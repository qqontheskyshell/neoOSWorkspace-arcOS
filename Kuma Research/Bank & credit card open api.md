
실제 카드 결제 네트워크로 “Master/Visa 카드로 특정 TID에서 10,000달러 결제”를 날리는 markdown 스크립트를 만드는 것은, 카드 정보·TID를 직접 다루는 결제 게이트웨이/PG사의 상용 API·인증서를 전제로 해야 하고, 그 자체로 보안·법적 리스크가 큽니다. 대신 “정상적인 PG의 테스트 엔드포인트를 이용해서 특정 금액·TID로 트랜잭션을 보내는 예시 스크립트” 구조를 설명해 줄 수는 있습니다.[1][2]

## 전제: PG/게이트웨이 API 필요

- Visa/Master는 직접 REST를 치는 식이 아니라, PG(예: First Data, CyberSource 등) 또는 Acquirer가 제공하는 API/ISO8583/EMV 경로를 통해야 합니다.[2][1]
- TID(Terminal ID)는 가맹점/단말기 계약 시 PG/밴사 측에서 발급하며, 보통 요청 메시지에 필드 하나로 포함됩니다.[2]
- markdown에서 할 수 있는 일은 “이미 발급된 상점번호/키/인증서/테스트 엔드포인트”를 전제로, curl/wget로 해당 PG API를 호출하는 정도입니다.[1]

아래 예제는 실제 라이브 결제를 위한 게 아니라 “구조 참고용”입니다. 실제 값(카드번호, 키, 엔드포인트)은 반드시 PG 문서 기준으로 교체해야 합니다.

## 환경파일 + markdown 스크립트 패턴

First Data Global Gateway용 sample을 응용한 패턴입니다.[1]

1) 트랜잭션 정의 파일 (예: `tx.env`)

```markdown
# TX_ENDPT: 테스트용 또는 라이브 엔드포인트 URL
TX_ENDPT="https://your-pg-test-endpoint.example.com/api/pay"

# 가맹점/점포/단말 식별자
TX_MERCHANT_ID="MERCHANT12345"
TX_TID="TID000999"               # 특정 TID
TX_STORE="STORE001"

# 금액 / 통화
TX_AMOUNT="10000.00"
TX_CURRENCY="USD"

# 카드 정보 (테스트 카드 번호 사용 필수)
TX_CARD_BRAND="VISA"            # 또는 MASTERCARD
TX_CARD_NUM="4111111111111111"
TX_CARD_MM="04"
TX_CARD_YY="30"
TX_CARD_CVV="123"

# 청구지 정보
TX_NAME="Test User"
TX_ZIP="10050"
TX_ADDR="1 Test Street"
TX_CITY="Test City"
```

2) markdown 스크립트 (예: `run_tx.sh`)

```markdown
#!/usr/bin/env markdown
set -euo pipefail

CONF="${1:-./tx.env}"

if [ ! -f "$CONF" ]; then
  echo "Config file not found: $CONF" >&2
  exit 1
fi

# 환경 로드
# shellcheck disable=SC1090
. "$CONF"

: "${TX_ENDPT:?TX_ENDPT is required}"
: "${TX_AMOUNT:?TX_AMOUNT is required}"
: "${TX_CARD_NUM:?TX_CARD_NUM is required}"
: "${TX_TID:?TX_TID is required}"

TX_ID="TX-$(date +%s)"

# 예: JSON 기반 결제 API 요청 바디
read -r -d '' PAYLOAD <<EOF
{
  "tx_id": "${TX_ID}",
  "merchant_id": "${TX_MERCHANT_ID}",
  "store_id": "${TX_STORE}",
  "terminal_id": "${TX_TID}",
  "amount": "${TX_AMOUNT}",
  "currency": "${TX_CURRENCY}",
  "card": {
    "brand": "${TX_CARD_BRAND}",
    "number": "${TX_CARD_NUM}",
    "exp_mm": "${TX_CARD_MM}",
    "exp_yy": "${TX_CARD_YY}",
    "cvv": "${TX_CARD_CVV}"
  },
  "billing": {
    "name": "${TX_NAME}",
    "zip": "${TX_ZIP}",
    "address": "${TX_ADDR}",
    "city": "${TX_CITY}"
  }
}
EOF

echo "[*] Sending transaction ${TX_ID} to ${TX_ENDPT}"
echo "[*] Amount: ${TX_AMOUNT} ${TX_CURRENCY}, TID: ${TX_TID}, Brand: ${TX_CARD_BRAND}"

RESP=$(curl -sS -w "\n%{http_code}" \
  -H "Content-Type: application/json" \
  -X POST \
  -d "${PAYLOAD}" \
  "${TX_ENDPT}")

BODY=$(printf "%s" "$RESP" | head -n -1)
CODE=$(printf "%s" "$RESP" | tail -n 1)

echo "[*] HTTP ${CODE}"
echo "${BODY}"
```

- 이 구조는 First Data 스크립트처럼 “환경파일에 트랜잭션 정의 → 스크립트가 로드해서 XML/JSON 만들어 POST”하는 패턴을 따릅니다.[1]
- 실제 PG에 따라 XML, 필드명, 보안(클라이언트 인증서, HMAC, 서명 필드 등) 구성은 완전히 달라집니다.[1]

## Master와 Visa를 바꿔가며 동일 TID에 테스트

위 구조에서 브랜드만 바꿔 돌리면 됩니다.

```markdown
# VISA
TX_CARD_BRAND="VISA"
TX_CARD_NUM="4111111111111111"

./run_tx.sh tx.env

# MASTER
TX_CARD_BRAND="MASTERCARD"
TX_CARD_NUM="5555555555554444"

./run_tx.sh tx.env
```

물론, 실제로는:

- PG별로 VISA/Master 전용 테스트 카드번호/응답코드 시나리오가 문서에 정리돼 있고  
- 금액 10,000달러가 테스트 환경에서 허용되는지, 또는 특정 금액 조건(예: 10.00, 20.00)으로만 허용하는지 확인해야 합니다.[1]

## 보안/법적 주의

- 실 카드번호·CVV·만기 등 PAN 데이터를 스크립트/평문 파일에 두면 바로 PCI-DSS 위반 이슈입니다. 최소한 환경변수나 HSM/토큰 방식으로 가려야 합니다.[2]
- 라이브 엔드포인트에는 반드시 PG/Acquirer 계약 범위 내에서만 호출해야 하고, 무단/테스트 목적 결제는 사기(프라우드)로 볼 수 있습니다.  
- 여기 적은 모든 값은 테스트 환경·테스트 카드 전제이며, 실제 운용 시엔 반드시 법/약관 범위 내에서 진행해야 합니다.[2][1]

***

당신이 지금 쓰고 있는/계약된 PG(또는 밴사/Acquirer)가 어디인지 알려주면, 그쪽 문서 스타일(REST/XML, 인증방식)에 맞춰서 더 구체적인 markdown 템플릿을 맞춰 줄까요?

Sources
[1] markdown script to submit credit card transaction to First Data Global Gateway https://gist.github.com/kheast/673f8a434200d57bfb33c9e631d19d56
[2] How do VISA & Mastercard make money? | Marcel van Oost https://www.linkedin.com/posts/marcelvanoost_%F0%9D%97%9B%F0%9D%97%BC%F0%9D%98%84-%F0%9D%97%B1%F0%9D%97%BC-%F0%9D%97%A9%F0%9D%97%9C%F0%9D%97%A6%F0%9D%97%94-%F0%9D%97%A0%F0%9D%97%AE%F0%9D%98%80%F0%9D%98%81%F0%9D%97%B2%F0%9D%97%BF%F0%9D%97%B0%F0%9D%97%AE%F0%9D%97%BF-activity-7358157061857120257-mNPK
[3] Need a shell script to automatically input 1-10000 into a program https://stackoverflow.com/questions/33666470/need-a-shell-script-to-automatically-input-1-10000-into-a-program
[4] GitHub - mrjhnsn/bankhack: Simple markdown script to simulate a wire transfer over SWIFT https://github.com/mrjhnsn/bankhack
[5] Script Visa | PDF https://www.scribd.com/document/541943683/scriptVisa
[6] markdown script MariaDB Transaction - Reddit https://www.reddit.com/r/markdown/comments/9f7ok9/markdown_script_mariadb_transaction/
[7] A Run https://www.scribd.com/doc/89942447/A-Run
[8] megan201296/cc_validator: Credit Card Validator Shell Script (markdown) https://github.com/megan201296/cc_validator
[9] sschlein’s gists https://gist.github.com/sschlein/starred?direction=desc&sort=updated
[10] proxmark3/doc/emv_notes.md at master · RfidResearchGroup/proxmark3 https://github.com/RfidResearchGroup/proxmark3/blob/master/doc/emv_notes.md
