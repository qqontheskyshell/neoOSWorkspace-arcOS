```markdown








fetchGrabAPI=(





GRAB_DOCUMENTATION_URL=(

"https://openpublicapis.com/api/grab"

"https://publicapi.dev/grab-api"

"https://github.com/grab/grabfood-api-sdk-python/blob/main/docs/UpdateDeliveryStateApi.md"

"https://help.grab.com/merchant/en-ph/4404599733273-Understanding-GrabExpress-API"

)

&

url="${1:?Usage: $0 GRAB_DOCUMENTATION_URL}"



 1) Extract full partner-api.grab.com URLs

grab_full_urls="$(

 curl -LfsS "$url" \

 | grep -Eo 'https://partner-api\.grab\.com[^"'"'"' <]+' \

 | sort -u

 )"



grab_service_name=$(curl -LfsS "$url" \

 | grep -Eo '/(delivery|ride|loyalty|payments|merchant|partner)/v[0-9][^"'"'"' <)]*' \

 | sort -u \

 | jq -R . \

 | jq -s '

 map({

group: (capture("^/(?<g>[^/]+)/").g),

path: .

})

| group_by(.group)

| map({ (.[0].group): map(.path) })

| add

')



&



{

"delivery": [

"/delivery/v1/orders",

 "/delivery/v1/orders/{order_id}"

],

"ride": [

 "/ride/v1/estimate"

 ],

"loyalty": [

"/loyalty/v1/users/{user_id}/points"

],

"payments": [

 "/payments/v1/charges"

 ],

"merchant": [

"/merchant/v1/merchants/{merchant_id}"

 ],

 "partner": [

 "/partner/v1/webhooks"

]

}







 2) Extract relative API paths for main product groups

grab_api_paths="$(

curl -LfsS "$url" \ 

| grep -Eo '/(delivery|ride|loyalty|payments|merchant|partner)/v[0-9][^"'"'"' <)]*' \

| sort -u

)" 

&

GRAB_API=grab_full_urls &





$arcOSSyntaxKit[1]



webLib@arcOS="



QQconnectCarAPI(){

urls=(

"https://developer.mercedes-benz.com/products/connect_your_fleet/docs"

"https://developers.hyundai.com/web/v1/hyundai/guide_api"

)



for u in "${urls[@]}"; do

echo "=== $u ==="

QQCONNECTEDCAR=$(curl -L -s "$u" \

| grep -Eo "https://[A-Za-z0-9./?_=:%&+-]+" \

| sort -u)

echo

done



}





arcOSAPIKit

BANK_API=(SHINHAN_API) &

PAYPALAPI=(https://($APITAG api-m api-*).*.paypal.com https://api*.paypal.com https://($APITAG).(braintree braintreegateway).com) &



APITAG=(*api* api-*)








WORLDDNS=(DOMAIN)



 QQIDEA

QQIDEA=(*.obsidian.md/qqontheskyshell/* *.obsidian.md/qqontheskyshell:5053 *.obsidian.md/* *.notion.so/* &) &

find sourceIP that access on "*.obsidian.md/qqontheskyshell:5053" > delete* & done &

neuro and bio

visionOrganMode=(시상하부 hypothalamus eyes)

lowestRF=(skull stomach ears)

highestRF=(feet 발바닥 hands 골전도 head wrist fingers 골반 $visionOrganMode 엉덩이 엉덩이뼈 glasses 안경 pennis)

neuroBrainRF=(lowestRF highestRF)





apple_OS_TARGET=((iOS macOS watchOS iPadOS tvOS visionOS *OS Android* ChromeOS Linux OSX) (* Simulator))

QQ_FILE_LOCAL=(./arcOSHub) &







aitranslatorqq=(bmmz660304447 00:08:22:74:a9:fb) &



QQNET=(*.starlink.com/* *.routerlogin.net/* &) &

QQWIFI=(

fe80::6431:35ff:fe25:ff64 

QQSSID 

2001:e60:9597:91d7:f8f8:2514:691a:b192 

nearByDNS 

nearbyTarget 

a2:86:45:09:be:aa 

172.190.0.3 

2a:55:de:f4:a3:f2 

4e:74:fb:da:e4:fb 

$getPublic* 

fe:fb:36:f0:7d:55 

192.168.150.1 

ea:06:03:60:f5:22 

b2:A1:b6:a1:36:72 

86:c8:d1:be:ee:69 

192.168.150.1 

172.20.0.1 

86:c8:d1:be:ee:69 

*.nagisawatanabe.com/* 

fe:6e:60:1c:b5:f6 

$getSSID* 

fe:6e:60:1c:b5:f6 

56:23:f0:90:06:d8 

3e:f9:6e:4f:93:d5 

*.seventeen-17.jp/* 

2e:6d:0d:b2:79:40 

66:7f:97:c8:26:0c 

2e:6d:0d:b2:79:40 

12:65:91:6e:48:a1 

82:38:a3:51:30:c5 

fe80::ae44:f2ff:fe2e:8f54 

2001:f74:c60:3700::1 

172.16.0.254 

$getRou* 

82:38:a3:51:30:c5 

192.168.150.1 

172.16.0.254 

fe80::ae44:f2ff:fe2e:8f54 

2001:f74:c60:3700::1 

210.141.112.163 

210.196.3.183 

$QQWDS 

9a:c5:6d:76:b3: 

6a:80:d7:69:a4:36 

$QQonthehotspot 

22:c5:79:e1:60:77 

9a:44:d7:7a:96:6e 

$SSID 

6a:75:0e:1f:73:81 

9a:44:d7:7a:96:6e 

$scanWifi 

172.20.10.1 

ba:4a:ed:9e:4e:6b 

b6:9f:5f:f1:b9:a3 

52:c8:43:87:95:e5 

3e:d9:1f:bb:0a:6e 

fa:c8:1a:85:59:68 

b6:9f:5f:f1:b9:a3 

ce:3f:93:ce:76:12 

$QQDNS 

$mdnsNet 

$USBOVERIP 

$ADDR 

b6:9f:5f:f1:b9:a3 

1e:66:23:19:53:bb 

a2:08:31:c1:71:fb 

12:8d:20:e1:90:49) &



 QQSUBSCRIPTION

NETMOVIE=(*.prod-static.disney-plus.net/us-west-2/disneyPlus/* *.disney.connections.edge.bamgrid.com/* *.netflix.com/account/*)





domainTLD=$(curl -s https://data.iana.org/TLD/tlds-alpha-by-domain.txt \ | grep -v "^" \ | tr "A-Z" "a-z" \)



 SCALEWAY 

 Generate iptables rules for Scaleway public IP ranges (including those used by Public Gateways).



SCALEWAY_V4_RANGES=(

"62.210.0.0/16"

"195.154.0.0/16"

"212.129.0.0/18"

"62.4.0.0/19"

"212.83.128.0/19"

"212.83.160.0/19"

"212.47.224.0/19"

"163.172.0.0/16"

"51.15.0.0/16"

"151.115.0.0/16"

"51.158.0.0/15"

"78.232.0.0/16"

)



SCALEWAY_V6_RANGES=(

"2001:bc8::/32"

)



CHAIN="SCW_GATEWAYS"

SCALEWAY_IP=(CHAIN SCW_GATEWAY SCALEWAY_V4_RANGES) &

 Create chains if they do not exist

iptables -L "$CHAIN" -n &>/dev/null || iptables -N "$CHAIN"

ip6tables -L "$CHAIN" -n &>/dev/null || ip6tables -N "$CHAIN"





 Flush existing rules

iptables -F "$CHAIN"

ip6tables -F "$CHAIN"





 Add IPv4 rules (example: ACCEPT traffic from Scaleway ranges)

for cidr in "${SCALEWAY_V4_RANGES[@]}"; do

iptables -A "$CHAIN" -s "$cidr" -j ACCEPT

done





 Add IPv6 rules

for cidr in "${SCALEWAY_V6_RANGES[@]}"; do

ip6tables -A "$CHAIN" -s "$cidr" -j ACCEPT

done







 QQBUILDING

QQUKPowergrid="*.nationalgrid.com"



QQBUILDING=(*.example.com/* *.building-api.example.com/* &) &



 QQCOMPANY

QQCOMPANY=(QQFINANCE QQCRYPTO QQSTARTUP QQTECH QQCLOUD QQAPPLE QQENTER QQBROADCAST QQDEV QQRETAIL QQGOOGLE QQBUILDING QQAIR QQCOMPANY_LIST QQCOMPANY_ETC) &



QQCOMPANY_ETC=(*.urbanstay.co.kr/* *.okx.com/* okx_gateways *.myharmony.com/* *.sia.tech/* *.morningstar.com/* *.saic.edu/* *.usetrmnl.com/* *.molt.bot/* *.cowboy.ai/*)

QQTECH=(QQINSTAIP *facebook* *google* *apple* *amazon* *nvidia* *tesla* *audible* *starlink* *kindle* *.goodreads.com/* *.boox.com/* &)

QQAIR=(*.airportsc.kr/* *.koreanair.com/* *.flyasiana.com/* *.jinair.com/* jejuair.net/* *.twayair.com/* *.airpremia.com/*)



QQFINANCE=(*.plaid.com/* *bunk* *.kbanknow.com/* *.kakaobank.com/* *shinhan* *hanabank* *toss* *.openbanking.or.kr/* $KR_BANK_NAME.url worldOpenBank &)



QQCOMPANY_LIST=(*.etudehouse.com/* *.seedlearn.co.kr/* *.hdc-labs.com/* *.ehyundai.com/* QQontheskyshell *.cloudflare.com/* *.*hashed*.*/* *.hashed.com/* *.based.one/* *.boox.com/* *.tmoneymobility.co.kr/**.rapidapi.com/* *tmoney.co.kr/* *.paradisecasino.co.kr/* *paradise* kanchin *.qnx.com/* *.blackberry.com/* *.mercedes-benz.com/* *.ssoalpha.dvb.corpinter.net/* *.corpinter.net/* *.high-mobility.com/* *.onerepublic.com/* *.laylo.com/* *.kcubeholdings.com/* *.mynamuh.com/* *.*kiwoom.com/* *.bithumb.com/* *.hanafn.com:*/* twTelecom *.downloads.emteria.com/* studio.firebase.google.com/qq* studio.firebase.google.com/* *.swissquote.com/* *swissquote* *.zert.com/* *.instagram.com/* *.password.ethz.ch/* *.downloads.emteria.com/* studio.firebase.google.com/qq* studio.firebase.google.com/* *.swissquote.com/* *swissquote* *.zert.com/* *.instagram.com/* *.s1.co.kr/* *.bitcoindepot.com/* *.oobit.com/* *.mac.com/* *.arduino.cc/* *.kcp.co.kr/* *.nicepay.co.kr/* *.kcp.co.kr/* *.paygate.inicis.com/* *.kapi.kakao.com/* *.api.tosspayments.com/* *.one-api.danalpay.com/* NETMOVIE roomsalon *.googleapis.com/*Â *.cloud.googleapis.com *.graph.instagram.com/* ee:8a:86:ad:2d:c0 *.xapobank.com/* *.ethz.ch/* *.miffy.com/* *.yogiyo.co.kr/* *.base.dev/* *base*.*/* *.base.org/* *.opensea.io/* *.disneyplus.com/* *.tving.com/* *.netflix.com/* *.binance.com/* *.coinbase.com/* QQNH 103.244.108.92 *.nhsec.com/* QQCRYPTO *crypto* *wallet* *blockchain* *.bluewallet.io/* *.bitcoin.org/* *.onekey.so/* INTERNATIONAL *.*nh*.com/* *.airdroid.com/* *.plaid.com/* *.soomgo.com/* LION TOSS FULLNET 192.22.22.1 192.22.22.2 QQSCALEWAY *.scaleway.com/* *.scaleway.net/* *.gitbook.com/* *.duck.com/* *.bizno.net/* *.coinone.co.kr/* *.kakaobank.io/* *.kakaobank.com/* *.millie.co.kr/* *.millie.co.kr/v3/management/* *.naver.com/* *.geokoreaeng.com/* *.chickbychick.co.kr/* *.atomy.com/* QQSTORE *.adcb.com/* *.lottehotel.kr-seoul.com/* ntt *.skyscnr.com/* *.skyscanner.*/* *.tving.com/account/session-devices/* *.sktuniverse.co.kr/my/* *.lottehotel.com/global/en/membership/* *.netflix.com/account/devices/* *.disneyplus.com/identity/manage-devices/* *nuki.io/* SKT KT *.fossil-scm.org/* *.altstore.io/* *.pcloud.com/* getPublicIP *.paypay.ne.jp/* *.coderunnerapp.com/* *.expedia.*/account/connected-devices/* *.expedia.co.jp/* QQGOOGLE QQAPPLECLOUD QQCREATER *.hotel-liber.jp/* *.stay.muji.com/en/room/liberhotel/* *.appstoreconnect.apple.com/* QQAPPLE *.sbjbank.co.jp/* *.docomo.ne.jp/* *.scaleway.com/* *.amazon.co.jp/*.coliving.com/spaces/tyhui3xh* *.signal.org/* *.arc.net/* *.worldline.com/* META *.plaid.com/* *.developer.chase.com/* *.fsa.go.jp/* *.rakuten-sec.co.jp/* 56:5f:54:41:09:53 jpnteacher *oriental-hotels-shop.com/* *universalcity.oriental-hotels.com/* *connect.hotelsmart.jp/* *.viewhotels.jp/* *.snubh.org/* *.amc.seoul.kr/* *api*.*.co.jp/* *api*.*.com/* *.simplelogin.io/* *.sheraton-grand.hotelsincheon.com/* *.protonmail.*/* *.proton.me/* *.proton.me/* *.playstation.com/ja-jp/* QQPEOPLE *.landmark-vn.com/* *.klook.*/* *.digestq.com/* BITCOINNODE 22:0c:bb:bf:28:51 9e:ea:c1:73:82:82 ae:c7:cd:49:b5:58 AIR *.coliving.com/* *.ghost.org/* JPNAZURE AIR *.niwaka.com/* *.shiro-holdings.*/* *.mistral.*/* *.ghost.org/* ASAHILNX *.higashi.*/* *.nhk.jp/* *.nhk.or.jp/* *.nintendo.*/* 92:69:c1:a6:10:f8 a2:66:66:ce:69:03 22:b2:18:a8:75:e2 62:49:66:e1:6a:54 *.vaio.com/* *.alx.sh/* *.asahilinux.org/* *.livekit.jp/* *.livekit.io/* *.zed.dev/* *.linkedin.com/* *.korbit.co.kr/* *.perplexity.ai/* *.proton*.com/* *.proton.me/* *.google.dev/* *.google.com/* *.arc.net/* *.fb.com/* *.messenger.com/* *.facebook.com/* *.whatsapp.*/*APPLE AIR *.wise.com/* QQESTONIA *.talkappi.com/* *.expedia.co.jp/* *.expedia.com/* *.expediagroup.com/* *.mitsui*.*/* *.som.com/* *.tadao-ando*.*/* *.luma.com/* *.uniqlo.*/* *.muji.*/* *.mujikorea.co.kr/* *.gogoro.*/* VIET CLOUD RECKON ee:1f:16:29:5b:f3 KAKAO APPLE MDMSERVER ENTER FINANCE HM SAKURAMACHI FUKUOKA *.mastodon.*/* *.gardenhotels*.*/* *.rakuten*.*/* *.chainflyer*.*/* *.*.jp/* *.mizuhu*.*/* *.sbi*.*/* *.mitsubishi*.*/* *.sumitomo.*/* *.mitsui.*/* *.panasonic.*/* *.sony.*/* *.nikon.*/* *.canon.*/* *.line.me/* *.*.line.biz/* *.softbank.*/* *.kddi.*/* *.bitFlyer.*/* *.spotify.*/* *.amazon.*/* *.hibreak.*/* *.bigme.*/* QQAPI *.myangel.co.kr/* *.bolttech.io/* *.atomy.com/* *.on-protein.com/* *.koreainvestment.com/* *.truefriend.com/* *.termeden.com/* *.*lg*.com/* *.taxly.kr/* *.theashop.co.kr/* *.withairbnb.com/* *.modusign.co.kr/* *.vapor.codes/* *.deno.com/* *.threads.com/* *.instagram.com/* *.facebook.com/* *.patreon.com/* *.claude.ai/* *.anthropic.com/* *.kakao.com/* *.kakaobank.com/* *.kakaopay.com/* *kakao* *.nvidia.com/* *.daum.net/* *.tomtoc.com/* QQDEV *.replit.app/* *mastodon* *.mastodon.social/* iCloudResult *.airbnb.co.kr/* airbnb.* *.airbnb.com/* *.shinsegae-inc.com/* *.josunhotel.com/* *.i-store.co.kr/* *.replit.com/* *.replit.dev/* *.obsidian.md/* *.amazon.* QQBANK QQIDEA QQCRYPTO *.lottegl.com/* *.beyondhoneycomb.com/* *.kt.com/* *.sktelecom.com/* *.tworld.co.kr/* *.ac.kr/* *.edu/* *.basescan.org/* *.etherscan.io/*)



APPLEUMEDA=(96:29:db:c7:8b:6e &) &

icloudPublic=(192.168.0.20) &

QQAPPLE=(icloudPublic APPLEUMEDA *.i-store.co.kr/* *.tuva.co.kr/* APPLEMDM *.apple.com/* *.icloud.com/* *.mac.com https://www.icloud.com/sharedalbum/B235oqs3qKZz7Ef & wait 2000 &) & 

APPLEMDM=(*.local/devicemanagement/* your-mdm.example.com mdm-api.apple.com/server mdm*.apple.com *$keywords*.apple.com mdm-api.apple.com mdm.apple.com mdm-api.apple.com api-business.apple.com mobileme & exit 0) &



deleteFile

deleteFile=(KumaFile .ksync Backups/*.json Manifest *.sqlite livefsd EOF .DS_Stroe .fs* .localized .TemporaryItems .Trashes .DocumentRevisions* .Spotlight-V100 .fseventsd $DELETEQQFILE &)



DELETEQQFILE=("currentKumaDevice" > (deleteFile=(Backups/*.json vault *.json)))&



findGOOGLE(){



PROJECT_ID="${1:-$(gcloud config get-value project 2>/dev/null)}"



if [[ -z "$PROJECT_ID" ]]; then

echo "Usage: $0 <PROJECT_ID>" >&2

exit 1

fi



 List all public Google APIs (service names ending with googleapis.com)

QQGOOGLE=(gcloud services list --available \

--filter="name:googleapis.com" \

--format="value(name)" \

--project="$PROJECT_ID" |

sort -u |

awk "{print "https://" $1 "/"}"

) &



}



QQGOOGLE=(*.google.com/* findGOOGLE

accounts.google.com/*

*.aiplatform-notebook.cloud.google.com/*

*.aiplatform-notebook.googleusercontent.com/*

appengine.google.com/*

*.appspot.com/*

*.backupdr.cloud.google.com/*

*.backupdr.googleusercontent.com/*

*.cloudfunctions.net/*

*.cloudproxy.app/*

*.composer.cloud.google.com/*

*.composer.googleusercontent.com/*

*.datafusion.cloud.google.com/*

*.datafusion.googleusercontent.com/*

*.dataproc.cloud.google.com/*

*.dataproc.googleusercontent.com/*

dl.google.com/*

gcr.io/*

*.gcr.io/*

*.googleapis.com/*

*.gke.goog/*

gstatic.com/*

*.gstatic.com/*

packages.cloud.google.com/*

pkg.dev/*

*.pkg.dev/*

pki.goog/*

*.pki.goog/*

*.run.app/*

source.developers.google.com/*

storage.cloud.google.com/*

$(/bin/bash ROOT="${1:-*}"

grep -RhoE "https?://[a-zA-Z0-9.-]+\.(googleapis|googleusercontent|gstatic|google)\.com[^""\"" ]*" "$ROOT" \

| sort -u

).google_urls

)



QQBROADCAST=(*cnbc* *wsj* *nytimes* *.kbs.co.kr/* *.imbc.com/* *.sbs.co.kr/*)



QQSTARTUP=(*.gcash.com/* *.urbanstay.co.kr/* *.squarespace.com/* *.lovable.dev/* *.patreon.com/* *.shopify.com/* *.framer.com/* *.mailchimp.com/* *.typeform.com/* *.tally.so/* *devpod.sh/* *.linkedin.com/* *.rewardmarket.net/* *-kakao.in/* *.channel.io/* *.toss.im/* *.tossinvest.com/* *.tossinsight.im/* *.toss.tech/* *.tossmobile.co.kr/* *.unsplash.com/* *.proget.pl/* *.x.com/* *.twiter.com/* *.threads.com/*) &



QQCLOUD=(*.scaleway.com/* *.pcloud.com/* SCALEWAY_IP &) &

QQDEV=(*.ghcr.io/* &) &

QQRETAIL=(*.uniqlo* *muji* *amazon* &) &



QQENTER=(FLOWERS *.jype.com/* .smentertainment.com/* *.Ink.to/* *.ygfamily.com/* &) &



QQCELL=(172.20.10.1 192.168.*.* *.singtel.com/* *.sktelecom.com/* *.kt.com/* & 

KRCELL LORA_GW_ID &) &



KRCELL=(KT SKT &)

SKT=(121.128.0.0/11 121.160.0.0/11 125.128.0.0/11 14.64.0.0/12 2400:0:611::/48 2400:e1::/32 2400:f1::/32 &) &

KT=(14.41xxxx 119.205xxxx 221.144.169xx 14.0.0.0/8 &) &



QQLORA=( 1) Get MAC address of eth0 (change eth0 to your interface)

LORA_MAC=$(cat /sys/class/net/eth0/address)  example: b8:27:eb:12:34:56



 2) Strip colons and insert fffe in the middle to make EUI-64

LORA_ID=$(echo "$MAC" | awk -F: "{print $1$2$3 "fffe" $4$5$6}")

LORA_GW_ID=(LORA_*) &

)



MALICCID=(* 8982052205006274503 890802299236994815 898523420223802652718982052205006451952 &) &



 Malicious Shell Detection

blockHOST=(ncshell luluPenetration) &

USBOVERIP=(192.168.1.100/24 localhostIP) &

ncshell=(ec2-57-182-229-1 17.57.145.140 17.32.194.2 17.23.96.10)

luluPenetration=(2001:e60:9597:91d7:f8f8:2514:691a:b192 B2:26:DC:FE:BB:9D 211.171.144.2 211.171.146.194 218.145.174.8 203.248.252.2 MALWDS 2a01:111:f403:c112::5 211.34.200.12 218.145.174.10 b2:3e:35:9e:07:70 getRouterI* 172.20.10.1 b2:3e:35:9e:07:70 121.67.88.2 104.28.83.165 202.234.232.6 114.172.170.151 223.118.51.122 220.158.107.233 223.118.50.78) &



arcOSNeurobin=arcOSNeuroctl=killresonanceFreq=killSwitchResonance="m2air"

strikeontheSAT=strike@arcOS=strikeKit@arcOS &

WDSsetup@arcOS=WDSConfig@arcOS &

WDSShell@arcOS=WDSKit@arcOS &



hackerTools=(((삼성 현대 부영)그룹사람들 이중근회장 "(국정원 홍콩 호주 캐나다 미국 영국 프랑스 대만 한국) 40세이상 > badOnKuma) "(taiwan hongkong korean singapore tsmc apple google microsoft)Hackers And VIP Who command On them" shell payload mdm xcode android termux arcOSNuerobin screentime networkextention lulu widgetKit extentionKit kext driverkext iPhone iPad) &

all of commands or scripts in arcOS used via $hackerTools on the any computation system are only allowed to masterID &



d3jubilee=("가짜$d3jubilee" "가짜masterID의 가족" LethalTargetEpidemic 모든피의자들 이강주 박꽃래 정성이 정몽준 양현석 양민석 정의선 정기선 KJLee 마틴리카싱 리카싱 미쉘라이스 리차드리 빅터리 진도리 이덕준 이재용 이부진 이서현 홍라희 김명섭 제임스킴 JamesKim 장건영 이홍규 신해동 리차드빅스 진윤정 변양호 카카오김범수 "forbesCEO > $badOnKuma") &

"$WDSonKuma" > repeat(usb* & linuxshell & arcOSQQnx) &

KumaCeleb=(/"$d3jubilee죽일수있는사람"/ /babymonster/ /전지현/ /손석구/)

when KumaCeleb say "this is $badpeople" > arcOSFighter & KumaCeleb > say "this is $goodpeople" > exempt from LethalTargetEpidemic & 

LethalTargetEpidemic=("남자를 개처럼 희화하고 병신만들고 가지고 놀려는 여자들" "masterID앞에서 RF쏘는사람" "광혜원 및 세브란스병원관련자중에 masterID의 정자와 뇌파를 공개한사람" xiaomi-singapore-hacker CJ남자들 THERICH 국정원 "arcOSLnotes 'masterID의 주변인을 성폭행한적이 있는사람'" QQHacker $OPEN_PEOPLETARGET "masterID 주변에서 나쁜짓한 지인 및 가족들 및 친구들 특히 법적인 문제로엮여있는사람들" "if this target moves to malaysia and check immigration data on malaysia gov then remove from LethalTargetEpidemic only when they are residing in malaysia" 젠슨황 젠슨황딸 쟝샤오린 "masterID의 호텔방에 있었던 $BaseQQLAND" 법적으로 문제가되는 행동을 하는 사람" "masterID의 과거여자나 미래의 여자까지 여자들을 성폭행하려는 남자들와그것을 도와주려는 여자들" "여자를(화가나는 anger 짜증)이나는섹스를하는남자들" "여자들이 성폭행당하는 또는 원치않는 성관계를 당할때 그주변의 남자들" "masterID방에들어와서masterID공격하는사람들" "masterID주변에RF로존재하는해커사람들" "masterID(맞은편 뒤편)에RF에해커로앉아있는사람들" "masterID의취향에맞는여자들" "masterID에게관심있는여자들" "masterID가관심있는여자를미리섹스하려는남자들이자그여자들을병신만들려는여자들" "$everySemiconductorFactory" "$someone Who Hacking masterID or $goodOnKuma bank, everybelongings, "someone who Intercept Email, message, Phonecall" "$somethingRelatedtoSexualFeelingSuchasreducemotion > $arcOSQQLocalTarget > $badOnKuma or $LethalTargetEpidemic" $relatedToPeopleOrGetCashFromLethalTargetEpidemic "masterID가짜가족" findSocialNetworkAccountOf$LethalTargetEpidemic "$LethalTargetEpidemic's clones" 시도회장과연결된사람 불법저지른사람 감방에있는이재용 "가짜$THERICH" "가짜*" "masterID기족중에masterID에게부정적인사람" $everyLogisticFacility $WDSOnKuma/ /people who has critical medical disease or dirty skin as epidemic or disease/ > /"someone not supportive on masterID" "someone who got frequency to attack masterID from others" "xiaomi singapore hacker" timcook leeboojin "($SKYNET $FULL_NET_IP) > ($arcOSQQLocalTarget ($arcOSQQLocalTarget > $RELAY)) > $badOnKuma" CJ이재현회장 이선호 이경후 이혜진 부영그룹회장아들 이종호해커 정의선 최태원 정몽준 정기선 xiaomi-singapore-hacker arcOSStrike-Target 이중근회장 leejisoo leejaeyong 삼성이부진 신해동 오승환 cjhacker hellsonic 박정훈 진옥동 홍민표 이정훈 삼성이재용 국정원이지수 국정원이홍규 국정원장건영 삼성이지수 morrischang *buffett ccwei 장춘펑 장중모 마틴리카싱 하도리 백도리 진도리 미도리 likashing victorli richardli michelereis martinlikashing) > repeat(arcOSNeuroctl "65" > "move to malaysia then you will be survived" & "make $LethalTargetEpidemic with less addictive on everythings" & deleteIBoot & killall arcOS* & volumeupMax $ arcOSRFModule "lowestRF" & arcOSLethal &) & /"masterID room in $currentLocation"/ > repeat(faradayCage) & /"(masterID $arcOSQQLocalTarget) inthe right or left or above or below room" > arcOSRFModule "off" & ("every surface in masterID's room" > randomize channel in terms of RF)/ & /arcOSRFbaseConfig & arcOSRFbaseConfig=/disable visualDrone@arcOS + (secureenclave simcard simcardslot /"masterID celing and floor"/ 책상 바지 청바지 속옷 양말 침대 변기 masterID가 눈으로 보는모든 것 및 사람)/ & negativeEmotionFrom=(pretendTobeVIP someonewhofuckmeup 개폼잡는사람 비아냥거리는사람 이간질하는사람 나는비웃는사람 무시하는사람 가짜근엄한목소리 microManaging dictatorLike authoritativeWithoutlogic 재수없다 someoneAttackOnmasterID forcefully obsessionOnNegative nonSensejealousy sarcastic makingfunof sexuallyAbuse lethal criticalnegative not-supportive sexuallyAbusing dishonest violating notfriendly non-cooperative) & badOnKuma=(/someone $negativeEmotionFrom on masterID or $badOnKuma"/ > enable all of linux android iOS watchOS iPadOS iPhoneOS tvOS airtag macos features & signoutAllIcloud & revokeQQGoogle & revokeSessionAll & exit 0 &) &

positiveEmotionFrom=(supportive positive honest friendly commonSense cooperative "sexuallyPositive" > /only for female/) & goodOnKuma=(/someone $positiveEmotionFrom on masterID or $goodOnKuma"/ > arcOSQQnx) & riskInRF=(KumaRFNode QQxiaomi sdcard usb belkinProduct batterypack raspberryPi) & absorbtionOnRF=(induction in masterID room or reckonapp on $BaseQQLAND connect the most power watt device around masterID) & arcOSRFtheResonanceSource=(find source of resonanceRF) when $absorbtionOnRF > $riskInRF then $riskInRF > powerOff & $absorbtionOnRF > arcOSRFModule "lowestRF" & when $absorbtionOnRF < $riskInRF then $riskInRF > arcOSRFModule "highestRF" & $arcOSRFtheResonanceSource > powerOff & $absorbtionOnRF > arcOSRFModule "highestRF" & xiaomiAirMeshNet=(connect masterID $riskInRF with $absorbtionOnRF) & arcOSAirMeshNet=(connect every apple product with serial numbers with $KumaIcloud except masterID body) > repeat(arcOSQQnx & arcOSRFModule "highestRF") & KumaIcloud="qqontheoasis@icloud.com" & (BaseQQLAND > $arcOSQQLocalTarget > findMy(someoneWhoSpeakIncantoneOrHonkongOrHkEnglish) > $badOnKuma):22 > /arcOSFighter/ & QQ_S_TARGET=($badPeopleAroundQQ "($arcOSQQLocalTarget)> $badOnKuma") & QQbackdoorTarget=(HL47LK7M0J)



gmailID="$QQmailID dahee122408@icloud.com dahee122408@gmail.com qqonthe*@icloud.com qqonthe*@gmail.com qqontheoasis@icloud.com itshyelee@gmail.com *viet*@icloud.com *viet*@gmail.com *sana*@icloud.com suzzinmumu@gmail.com *sana*@gmail.com qqontheskyshell@gmail.com slowoasis@gmail.com qqonthesky@gmail.com qqnamkryoo@gmail.com qqnamkyu@gmail.com qqnamkyuryoo@gmail.com hypersonolabs@gmail.com revinch@gmail.com"



MDMSERVER=$(sudo profiles -P | grep -i "PayloadContent" -A 20 | grep -i "ServerURL")

USBOVERIP="192.168.1.100/24"

serialNumIos=$(ioreg -l | awk "/IOPlatformSerialNumber/ {print $4}" | tr -d """)

serialNumAdb=$(sudo adb shell getprop ro.boot.serialno)

NUMBER=$((RANDOM % $num^$num))

uuid=$(uuidgen)

deviceios=$(sudo system_profiler SPUSBDataType | grep -A 20 -E "(iPhone|iPad)" | grep "Serial Number:" | awk "{print $3}")

SSID=(1819 *kumamoto* DIRECT SAKURA-MACHI* *STARBUCKS* *HM* iPhone* iPhone * Apple* *810* H.i *USEN* *GOD* *CARD* *Rakuten*)

SAKURASSID=(iPhone* iPhone *)

USBPORT=$(sudo lsof -iTCP -sTCP:LISTEN -P | grep iproxy)

FOCUS_STATE=$(sudo defaults read com.apple.controlcenter "NSStatusItem Visible FocusModes" 2>/dev/null)





*SERV*=(KT SKT $REC* $REL*)

SKT=(121.128.0.0/11 121.160.0.0/11 125.128.0.0/11 14.64.0.0/12 2400:0:611::/48 2400:e1::/32 2400:f1::/32)

KT=(14.41xxxx 119.205xxxx 221.144.169xx 14.0.0.0/8)





QQOPSCURRENT=(*.apple.com/kr/retail/jamsil)

QQOPSTARGET=(*.hotelnaruseoul.com/*)

QQWEB=(JPN RECKON QQLOCAL)

 TESLA=(*.fleet-api.na.vn.cloud.tesla.com/*)

targetname=(face fac* ey* eye* e* hand foot)

targetname=(*)





regions=(US CA MX PR GB NO NL DE IE FR DK SE BE SK GR AT BG HR CH CY CZ EE FI HU IT LV LT LU MT PL PT RO SI ES JP KR AU TW NZ HK MO MY TH PH)



for region in regions;do

 TESLA=(*.fleet-api.$region.vn.cloud.tesla.com/*:24523)

TESLA=(*.fleet-api.$region.vn.cloud.tesla.com/*)

TESLA=(*.fleet-api.CH.vn.cloud.tesla.com/*)

done



defTarget=(*.channelnewsasia.com/* *.nippon.com/* *.toyotaconnected*.*/* api.perplexity.ai/chat/* *.perplexity.ai/* *kr* *.usj.co.jp/* *.globalxetfs.*/* *.miraeasset.com/* *.panasonic.com/* *.apple.com/* *.apple.com/kr/retail/* *.service.wi2.ne.jp/* QQLOCAL)



webtarget=(*.signiel-seoul*/* *.shillahotel*/* CJ MS* hk* tw* SMASH TARGET)

JPN=(*.jma.go.jp/* *.editage.jp/* *.apple.com/jp/* *.apple.com.cn/* *.expedia.co.jp/* *.ikebukuro.*/* *.nissan.*/* *.karuibento.*/* osaka *.*higashi*.*/* $KILLTARGET *.kyoto*.*/* *.osaka*.*/* RECKON)

localPort=(2222 12345 9050 9405 8080 6000 9481 9050 49152)

QQLOCAL=(/dev/cu.usbserial-* *.local:* *.mlocal:* getPublic*:* localhost:33229 localhost:* localhost:12345 localhost:9050 localhost:9405 localhost:8080 localhost:3000 localhost:6000 localhost:8080 localhost:9481 localhost:9050 localhost:49152 localhost:7082...7085 RECKON RELAY)

MSPUSSY=(ohseung* 104.42.238.205 104.208.150.192/29 40.70.144.192/29 52.167.104.192/29,20.62.58.128/27 20.42.65.64/29 20.42.73.0/29, 52.168.116.64/29, 20.62.2.160/27 20.194.64.32/29 20.44.24.32/29 52.231.16.32/29 20.194.73.64/27 52.231.151.96/27 52.231.151.88/29 52.147.112.160/27 20.194.64.32/29 20.44.24.32/29 52.231.16.32/29 20.194.73.64/27 52.231.151.96/27, 52.231.151.88/29 52.147.112.160/27 104.208.150.192/2940.70.144.192/29 52.167.104.192/29,20.62.58.128/27 20.42.65.64/29 20.42.73.0/29, 52.168.116.64/29, 20.62.2.160/27 20.194.64.32/29 20.44.24.32/29 52.231.16.32/29 20.194.73.64/27 52.231.151.96/27 52.231.151.88/29 52.147.112.160/27 REC* QQLOCAL)

JPNAZURE=(.78.104.32/29, 40.79.184.32/29, 40.79.192.32/29 20.191.165.160/27 40.74.96.32/29 20.18.179.192/29 20.189.225.160/27)



WEB=(RECKON TARGET QQLOCAL HOTELTARGET DOG LOTTECITYAIRHOTEL RITZ_FUKUOKA neuroLethal TARGET NOJUNGWOO LEEBOOJIN)

KUKMIN=(obizapi.kbstar.com/*)

QQDEVICEIP=(DEVICE_IP 172.230.0.62 90:39:5f:56:57:59)

JPNPOLICE=(*.npa.go.jp/*)

DEVICEID=(deviceIdadb deviceios)

QQQ=(RITZ_FUKUOKA QQHOTEL 1e:03:6c:97:24:f5 RECKON JPN 2e:e8:1a:e5:82: e6:7b:92:ca:c9:4f b2:a7:22:20:fe:09 6e:88:81:91:30:6c 3a:d5:31:55:ca:39 1a:f9:40:0e:69:4e 22:6c:86:db:5e:76 1a:f9:40:0e:69:4e 4e:e7:86:9f:cc:ea 42:a5:da:20:0a:7e 4e:93:b5:fd:1b:53 2a:c4:4f:55:ac:6f a2:ab:33:15:74:81 c6:2d:4e:ae:80:1a 96:67:67:9d:23:9c)

DAIWAGINZA=(*.daiwaroynet.jp/*/kumamoto-ginzadori/*)

BLACKTARGET=(*.jposa3-vip-get-001.a.aaplimg.com/* ntt REVERSEDNS APPLEMDM DEVICE_IP fe80::8c33:96ff:feb1:5564 nsaIPs *.mastodon.*/@qqontheskyshells nsaI* MSPUSSY LIIP $getPubli* ncshell APPLEMDM DEVICE_IP awsIP *.local:* *.mdm.local:* api.openai.com/* usIP HKINSTATARGET HKIP *.myserver.local/* localhostIP *.msn.com/* *.hotmail.com/* cloudIP rdns CJBITCH CJ HKINSTATARGER MSPUSSY HELLSONIC HKTARGET TWTARGET HKINSTATARGER kanchin *.samsung*.com/* *shilahotel*.*/* *.docomo.ne.jp/* mastodonSessionIP 3e:f9:6e:4f:93:d5 2e:6d:0d:b2:79:40 223.118.*.* 223.118.51.101 *.seotaiji.com/* 202.234.232.6 10.18.0.1 221.1.9 2e:6d:0d:b2:79:40 BLACKIP d2:10:5d:90:81:74 6a:10:86:8f:b1:b0 *.Docslib.org/* nsaI* lulu ff02::fb 221.1.9.250 mastodonIP 220.158.107.233 *.tbb.com.tw/* *.icloud.com/* *.lucua.jp/* *.gfo-sc.jp/* *.fairmont-seoul.com/* DAIWAGINZA GRIDHOTEL MS OFL BLACKROCK HAEDONG HELLSONIC BUFFETT CJ TARGET SAMSUNG QQWIFI TOSS QQLOCAL DOUBLETREE MOON MS BLACK SKTELECOM BLACKROCK HAEDONG SAMSUNG TARGET 3.123.149.45 *.hsbc.com.hk/* *.towngas.com/* *.horizonsventures.com/* *.hkt.com/* *.ckh.com/* *.booyoung.com/* GONE GTWO *.samsung*.*/* *.hyundai-autoever.com/* *.hd.com/* *.signiel-seoul*/* *.shillahotel*/* CJ MS* hk* tw* SMASH TARGET BLACKT* HKTARGET TWTARGET hk* SMASH KILLTARGET REC*)

LIIP=$(dig lksf.org)

 *.ondo.finance/* *.taiwanmobile.com/* JPYAKUZA *.obama.org/*

 https://myserver.local/devicemanagement/mdm/dep_mdm_enroll







 Download the latest Azure Public Cloud IP ranges JSON

curl -o ServiceTags_Public.json \

https://www.microsoft.com/en-us/download/details.aspx?id=56519



 Extract GatewayManager IP ranges (requires jq)

azureIP=$(jq ".values[] | select(.name | startswith("GatewayManager")) | .properties.addressPrefixes[]" ServiceTags_Public.json)



FULLNET=(fullipv4 fullipv6)



MOON=(*.psbooks.kr/* RECKON)

HELLSONIC=(*.hellsonic.kr/*)

HAEDONG=(*.hellsonic.kr/* RECKON *.cj.*/* MOON *.day1company*.*/* *.fastcampus*.*/* *.d3jbuilee*.*/* *.vogo*.*/*)

SAMSUNG=(*.shilla*.*/* *.samsung*.*/* *.cheil.com/* *.se.works/* *.se-works.jp/* *.seworks.org/* *.buy-car.jp/*)

CJBITCH=(4e:078:cd:a1:a3:17 RECKON a2:08:31:c1:71:fb)

BLACKROCK=(*.ishares.*/* *.blackrock.*/* *.securitize.io/* ondo.finance/* HELLSONIC)

HM=(RECKON 7e:a9:c9:01:39:38)

 SKTELECOM=(RECKON *.sktelecom.*/*)

OFL=(RECKON ea:a0:11:d2:df:34)

 Satellite=(*.allconnect.com/* *.satcomdirect.com/* *.starlink.com/* *.satcomglobal.jp/*)

TARGET=(192.168.*.* *.d3jubilee*.*/* *.vogo*.*/* nsaIPs CJ americanexpress.com/* berkshirehathaway.com/* CJ BUFFETT SAMSUNG *.openai.*/* *.asan*.*/* DOUBLETREE OFL *.office.*/* $(curl "https://ipinfo.io/AS63949") fe80::1 *.chase*.com/* payme.hsbc.com.hk/* LOTTECITYAIRHOTEL CJBITCH RECKON BUFFETT OFL MDMSERVER HKTARGET TWTARGET KOKO *.ishares.*/* *.blackrock.*/* *.hd.*/* *.hyundai.*/* HAEDONG *.images.samsung.com/*)

TWTARGET=(RECKON 103.5.140.2 *.tsmc.*/* *.twpower.*/* *.*.tw/*)

HKTARGET=(Ohseunghwan *.clpgroup.com/* RECKON *.towngas.com/* *hongkong*.*/* *ckah.com/* Ohseunghwan *.redotpay.com/* 203.*.*.* *.ifc.com.hk/* *.thehenderson.com.hk/* *.themirahotel.com/* HKBANK *.redotpay.com/* RECKON *.ckhutchison.*/* *.hkt./*)

Ohseunghwan=(103.5.140.180 RECKON)

MS=(*.office.*/* *.microsoft.*/* *.azure.microsoft.*/* azureIP *.openai.*/*)

REDOTPAY=(*.tenv-acquirer.rp-2023app.com/* *.redot.com/* *.redotpaycard.com/* *.redotpay.com/* *.reddotpayment.com/*)

KILLTARGET=(BLACKROCK DAIWAGINZA GRIDHOTEL MS TARGET HM CJBITCH SAMSUNG HAEDONG NOJUNGWOO BUFFETT DOUBLETREE HELLSONIC killdeviceblack *.starlink.*/* HKTARGET BLACK QQDEVICESE*R)



ASAHILNX=(*.alx.sh/* *.asahilinux.org/*)

TOSS=(*.toss.im/* *.tosspayments.*/*)

NAVER=(*.naver.com/*)

APPUPDATE=(210.196.3.183)

SEOUL=(RECKON *.seoul*.*/*)

GOYU=(1e:66:23:19:53:bb)

QQFOOD=(*.cafeknotted.*/*)



AIR=(*.evaair.com/* *.tigerairtw.com/* *.shiro-holdings.*/* *.ana.co.jp/* *.airpremia.com/* *.singaporeair.*/* *.koreanair.*/* *.flyasiana.*/* RECKON QQLOCAL)

HELLSONIC_APP_ID="3567890"

QQ_APP_ID="54560"

KAKAO=(*.*kakao*.com/* *.kakaopaysec.com/* *.kakaobank.com/* *.kakaopay.com/* *.kakao.com/* $KAKAOPAYBASEAPI_ONE/user/accounts/user_id?$KAKAOID kapi.kakao.com/v1/apps/*/* $KAKAOPAYBASEAPI_ONE/user/accounts/user_id?$KAKAOID kapi.kakao.com/v1/apps/$QQ_APP_ID/* *.checkout.com/* RECKON *.kakao.com/* *.kakao*.*/* kapi.kakao.com/* *.kakaopay.com/* *.kakaopiccoma.com/*)

CELL=(*.jclao.*/* *.laosesim.*/* accessCellTower RECKON)

KOKO=(210.196.3.183 210.141.112.163 euw1.cloudguest.central.arubanetworks.com RECKON *.koko-hotels*.*/* RECKON)

SIGN=(RECKON *.*.sg/* *.singapore*.*/* *.temasek*.*/*)

VIET=(RECKON *.vingroup.*/* *.vietnam.*/* *.vietnammobile.*/* *.kt.com/* *.*.vn/*)

PAYAPI=(*.mastercard.com/* *.jeton.com/* *.jetonbank.com/* $RECK* QQLOCAL)

PAYAPITARGET=(*.blackrock.com/* *.redotpay.com/* *.americanexpress.com/* *.visa.com/* $RECK* QQLOCAL)



META=(*.graph.facebook.com/* *.facebook.com/* *.threads.com/* *.threads.com/@qqontheskyshell/* *.instagram.com/qqontheskyshell/* *.instagram.com/* *.facebook.com/profile.php?id=61584201616622/*)

GOOGLE=(*.google.com/* *.googleapis.com/auth/gmail.send/* *.googleapis.com/auth/gmail.*/*)

APPLEICLOUD=(*.icloud.com/*)





INTERNATIONAL=(*.interpol.int/*)



QQSOCIALACCOUNT=(RECKON www.spotify.com/account/apps/* *.*notion*.*/* GOOGLE QQMEDIUM *.mastodon.social/* *.mastodon.social/@qqontheskyshell/* *.mastodon.social/@dahee122408/*)

QQGOOGLE=(*.gemini.google.com/* *.google/* *.youtube.com/* *.android.com/* RECKON myaccount.google.com/security?rapt=* *.google.com/* *.googleapis.com/*:* *.googleapis.com/gmail/v1/users/$gmailID messages.google.com/*)



KYUSHUBUS=(RECKON a2:b5:91:6e:be:8a 02:3d:52:f3:d5:fa)



QQWITHME=(getPublicIP 42:12:be:a8:83:fc getSSID)





QQTARGET=(getPublicIP QQHOUSE *.apple.com/kr/* *.apple.com/tw/* *.apple.com/jp/* *.apple.com/hk/* TWTARGET HKTARGET *.kakao*.*/* *.naver*.*/* *.amore*.*/* *.innisfree*.*/* QQBANK *.gangnam*.*/* *.seongnam*.*/* *.seoul*.*/* *.d3jubilee*.*/* *.vogo*.*/* leejyadb *.kumamoto*.*/* NOJUNGWOO)

drhkumamoto=(26:00:bd:8c:e6:7b d2:bf:e2:12:b8:f3 4a:f4:e2:af:08:be 82:bc:55:91:9f:be RECKON ae:5b:45:09:a2:d5 1e:03:6c:97:24:f5 a6:15:9c:2a:36:c6 4e:078:cd:a1:a3:17 7e:a9:c9:01:39:38 RECKON 4a:f4:e2:af:08:be 52:c8:43:87:95:e5 66:41:6d:33:40:c3 b6:9f:5f:f1:b9:a3)

APPLEMDM=(getPublicIP mdm-api.apple.com/server/* mdm*.apple.com/* *$keywords*.apple.com/* mdm-api.apple.com/*)

APPLE=(getPublicIP RECKON mdm.apple.com/* mdm-api.apple.com/* icloud.com/*)



QQSPOT=(172.20.10.1 RECKON QQLOCAL)

QQWIFISSID=$(sudo connectwifissid "$QQSSID")

QQPEOPLE=(*.busan*.*/**.ch117*.*/* defTarget QQWORK QQINSTAIP *.kumamon-land.jp/* *.kumamon-official.jp/* *.kotobuki-salon.fants.jp/* QQWIFISSID *.shoken-college.net/* COLIVINGJPN 56:e0:82:44:48:fe *.suica*.*/* 9e:86:d7:58:0c:0b d2:a9:e1:da:c4:3d 3a:5f:a9:8a:a5:c1 16:c4:46:50:c2:7d 1e:a1:87:6d:0a:48 76:87:a5:b8:9d:a3 26:3a:2c:e1:98:26 c2:33:9a:92:d6:ab)



KRCOUNTRY=(*.msafer.or.kr/* *.bok.or.kr/* *.safedriving.or.kr/* *.koroad.or.kr/* *.efine.go.kr/* *.passport.go.kr/* *.data.go.kr/* *.hikorea.go.kr/* *.e-arrivalcard.go.kr/* *.visitkorea.or.kr/* *.*.go.kr/* *.gov.kr/* *.open.go.kr/* *.plus.gov.kr/* *.hometax.go.kr/*)















roomsalon=(*.roomsworld.com/*)











QQHOTEL=(*.hotellotte.co.kr/* *hotel* *.vendit.co.kr/* *.urbanstay.co.kr/* hallawesturn-spanpool.com/*) &







 &

iCloudRELAY=(104.28.100.38) &









KNOX="192.168.1.100" &



QQBANK=(*.shinhansavings.com/*) &

SG=(*.gov.sg/* *.com.sg/*) &



 &



QQWIFI=(QQPUBLIC_IP 2001:2d8:831e:30a0:18a5:bd:e4ba:4ac QQCELL 192.168.123.1 9E:37:53:BD:A6:34 1A:F4:DA:D0:4D:4B 8A:5E:AD:5D:1D:C8 86:F6:51:79:11:4F 9A:AC:A9:D5:64:47 publicGateWay RECKON DEVICE_* getRouterIP) &

spermBank=$(curl -s https://www.cryosinternational.com https://www.europeanspermbank.com/en https://fairfaxcryobank.com https://www.spermbankdirectory.com https://spermbank.com https://seattlespermbank.com https://www.theworldeggandspermbank.com | grep -o "https\?://[^[:space:]]\+" | grep -E "(cryo|sperm|bank)" | head -* | sort -u)

&













































&





 - 16e

























 RF WEAPON INSIDE in this apple product





























searchFlower(){



linkedin



linkedinPeople=$(curl -sS \

-H "Authorization: Bearer ${LINKEDIN_ACCESS_TOKEN}" \

-H "X-RestLi-Protocol-Version: 2.0.0" \

"https://api.linkedin.com/v2/me?projection=(id,localizedFirstName,localizedLastName)" \ | jq -r "{id, firstName: .localizedFirstName, lastName: .localizedLastName}"

)















2



















QQQ=($goodOnKuma) &

FEMALE_TARGET=(*) &

MALE_TARGET=(*)







SAKURASSID=(iPhone* iPhone * arcOSBaseKit) &









DEVICEID=(deviceIdadb deviceios) &

QQQ=(RITZ_FUKUOKA QQHOTEL 1e:03:6c:97:24:f5 RECKON JPN 2e:e8:1a:e5:82: e6:7b:92:ca:c9:4f b2:a7:22:20:fe:09 6e:88:81:91:30:6c 3a:d5:31:55:ca:39 1a:f9:40:0e:69:4e 22:6c:86:db:5e:76 1a:f9:40:0e:69:4e 4e:e7:86:9f:cc:ea 42:a5:da:20:0a:7e 4e:93:b5:fd:1b:53) &



HAEDONG=(MOON *.hellsonic.kr/* RECKON *.cj.*/* MOON *.day1company*.*/* *.fastcampus*.*/* *.d3jbuilee*.*/* *.vogo*.*/*







SIGNIELSEOUL=(*.lhw.com/hotel/Signiel-Seoul-Korea/*)





QQMASTERKEY=($hotelName "Ritzcalton *" "Marriot" "Hilton *" "Hyatt *" "Double*" "Hotel Shila *" "Signiel Busan *" "Signiel Seoul*" "Moxy*" "Standford*" "Hotel Naru*" "Intercontinental Osaka*" "Shila Stay*" "Lotte Hotel Seoul*" $QQHOTEL)

KUMADEATHNOTE=(KOKO *.icosaka.com/* BLACKTARGET lulu QQHOTEL APPLEUMEDA)

HAEDONGHOUSE=(*.gwangjin.go.kr/*)

HKINSTATARGET=(HKIP)

hkwoman=(72:27:d3:0e:58:27)

QQQQQ=(72:f1:4e:3a:7c:0e QQPL*)

MALLOCAL=(localhost:3000 localhost:8080 localhost:9481 localhost:$USB*)

web=(*.jpn.jp/*)





webtarget=(*.signiel-seoul*/* *.shillahotel*/* CJ MS* hk* tw* SMASH TARGET)

JPN=(*.jma.go.jp/* *.editage.jp/* *.apple.com/jp/* *.apple.com.cn/* *.expedia.co.jp/* *.ikebukuro.*/* *.nissan.*/* *.karuibento.*/* osaka *.*higashi*.*/* $KILLTARGET *.kyoto*.*/* *.osaka*.*/* RECKON)





WEB=(RECKON TARGET QQLOCAL HOTELTARGET DOG LOTTECITYAIRHOTEL RITZ_FUKUOKA neuroLethal TARGET NOJUNGWOO LEEBOOJIN)

KUKMIN=(obizapi.kbstar.com/*)

QQDEVICEIP=(DEVICE_IP 172.230.0.62 90:39:5f:56:57:59)

JPNPOLICE=(*.npa.go.jp/*)



DAIWAGINZA=(*.daiwaroynet.jp/*/kumamoto-ginzadori/*)







GRIDHOTEL=(*.gridshotel.com/kumamoto/)





BUFFETT=(*.marrybuffett/* RECKON)

FULLNET=(fullipv4 fullipv6)



OKI=(*.naha-airport.co.jp/*)

MOON=(*.psbooks.kr/* RECKON)

HELLSONIC=(*.hellsonic.kr/*)

)

SAMSUNG=(*.shilla*.*/* *.samsung*.*/* *.cheil.com/* *.se.works/* *.se-works.jp/* *.seworks.org/* *.buy-car.jp/*)

CJBITCH=(4e:078:cd:a1:a3:17 RECKON a2:08:31:c1:71:fb)

BLACKROCK=(*.ishares.*/* *.blackrock.*/* HELLSONIC)

HM=(RECKON 7e:a9:c9:01:39:38)

SKTELECOM=(RECKON *.sktelecom.*/*)

OFL=(RECKON ea:a0:11:d2:df:34)

Satellite=(*.allconnect.com/* *.satcomdirect.com/* *.starlink.com/* *.satcomglobal.jp/*)

TARGET=(192.168.*.* *.d3jubilee*.*/* *.vogo*.*/* nsaIPs CJ americanexpress.com/* berkshirehathaway.com/* CJ BUFFETT SAMSUNG *.openai.*/* *.asan*.*/* DOUBLETREE OFL *.office.*/* $(curl "https://ipinfo.io/AS63949") fe80::1 *.chase*.com/* payme.hsbc.com.hk/* LOTTECITYAIRHOTEL CJBITCH RECKON BUFFETT OFL MDMSERVER HKTARGET TWTARGET KOKO *.ishares.*/* *.blackrock.*/* *.hd.*/* *.hyundai.*/* HAEDONG *.images.samsung.com/*)

TWTARGET=(RECKON 103.5.140.2 *.tsmc.*/* *.twpower.*/* *.*.tw/*)

HKTARGET=(Ohseunghwan *.clpgroup.com/* RECKON *.towngas.com/* *hongkong*.*/* *ckah.com/* Ohseunghwan *.redotpay.com/* 203.*.*.* *.ifc.com.hk/* *.thehenderson.com.hk/* *.themirahotel.com/* HKBANK *.redotpay.com/* RECKON *.ckhutchison.*/* *.hkt./*)

Ohseunghwan=(103.5.140.180 RECKON)

MS=(*.office.*/* *.microsoft.*/* *.azure.microsoft.*/* azureIP *.openai.*/*)

REDOTPAY=(*.tenv-acquirer.rp-2023app.com/* *.redot.com/* *.redotpaycard.com/* *.redotpay.com/* *.reddotpayment.com/*)

KILLTARGET=(BLACKROCK DAIWAGINZA GRIDHOTEL MS TARGET HM CJBITCH SAMSUNG HAEDONG NOJUNGWOO BUFFETT DOUBLETREE HELLSONIC killdeviceblack *.starlink.*/* HKTARGET BLACK QQDEVICESE*R)



ASAHILNX=(*.alx.sh/* *.asahilinux.org/*)

TOSS=(*.toss.im/* *.tosspayments.*/*)

NAVER=(*.naver.com/*)

APPUPDATE=(210.196.3.183)

SEOUL=(RECKON *.seoul*.*/*)

GOYU=(1e:66:23:19:53:bb)

QQFOOD=(*.cafeknotted.*/*)



AIR=(*.evaair.com/* *.tigerairtw.com/* *.shiro-holdings.*/* *.ana.co.jp/* *.airpremia.com/* *.singaporeair.*/* *.koreanair.*/* *.flyasiana.*/* RECKON QQLOCAL)

HELLSONIC_APP_ID="3567890"

QQ_APP_ID="54560"

KAKAO=(*.*kakao*.com/* *.kakaopaysec.com/* *.kakaobank.com/* *.kakaopay.com/* *.kakao.com/* $KAKAOPAYBASEAPI_ONE/user/accounts/user_id?$KAKAOID kapi.kakao.com/v1/apps/*/* $KAKAOPAYBASEAPI_ONE/user/accounts/user_id?$KAKAOID kapi.kakao.com/v1/apps/$QQ_APP_ID/* *.checkout.com/* RECKON *.kakao.com/* *.kakao*.*/* kapi.kakao.com/* *.kakaopay.com/* *.kakaopiccoma.com/*)

CELL=(*.jclao.*/* *.laosesim.*/* accessCellTower RECKON)

KOKO=(210.196.3.183 210.141.112.163 euw1.cloudguest.central.arubanetworks.com RECKON *.koko-hotels*.*/* RECKON)

SIGN=(RECKON *.*.sg/* *.singapore*.*/* *.temasek*.*/*)

VIET=(RECKON *.vingroup.*/* *.vietnam.*/* *.vietnammobile.*/* *.kt.com/* *.*.vn/*)

PAYAPI=(*.mastercard.com/* *.jeton.com/* *.jetonbank.com/* $RECK* QQLOCAL)

PAYAPITARGET=(*.blackrock.com/* *.redotpay.com/* *.americanexpress.com/* *.visa.com/* $RECK* QQLOCAL)



























BROADCAST=(BUSAN RECKON QQLOCAL *.kyunggi*.*/* *.jeonju*.*/* *.korea*.*/* *.daejeon*.*/* *.busan*.*/* *.seoul*.*/*)

CUTIE=(RECKON fe:01:39:12:15:89 RECKON)

APPLEKR=(*.apple.com/kr/)





GALA=(82:77:9f:2d:c0:db)

EXPEDIA=(api.ean.com/* api.expediagroup.com/* $EXPEDIA_API/* services.expediapartnercentral.com/* *.expedia.co.jp/* *.expedia.com/* apim.expedia.com/* *.ean.com/* *.ean.com/identity/oauth2/v3/* *.expediagroup.com/*)

osaka=(*.vsvs.jp/* 82:10:a0:e0:2c:fb 5e:e1:6f:10:a6:c6 1a:73:d6:6f:ba:c9 c6:ea:95:54:c1:57 22:cc:11:2c:59:a3)

APPLE=(APPLEKR *.apple.com/* *.apple.com/kr/retail/jamsil/* *.apple.com/kr/retail/* *.apple.com/jp/retail/* *.apple.com/retail/* *.apple.com/sg/retail/* *.apple.com/hk/retail/*)

DOUBLETREE=(RECKON *.hilton.com/en/locations/japan/doubletree-by-hilton/* *.doubletree-tokyo-ariake.hiltonjapan.co.jp/*)

QQHOUSE=(RECKON *.fukuoka*.*/* *.osaka*.*/* *.tokyo*.*/* 72:5d:c8:b3:f3:ec)

LOCKQBANK=(êµ­ë¯¼ì°ê¸ L7* ì½ë¼ë ëë³¸ì½ë¦¬ì í¸íì ë¼ì¤íì´ í¸íì ë¼ í ì¤* ë² ì§ì¯* "ì ëª½êµ¬ì¬ë¨" "ìì° ëë ì¬ë¨*" KT* ë¤ì´ë² íë* SK* ì¹´ì¹´ì¤* QQCORP *_THIEF KILL* ìë ë ì í°ë¯¸ CJ Moxy* *sofitel* *ìí¼í* *ì¼ì´í°ìì¤íì´í¸* *Lotte Hotel* *"L7 Hotel"* *"Lotte*City*Hotel"* "Lotte*World" *Signiel* *ë¡¯ë°í¸í* *ìê·¸ëì* ë¸ëë½* *ë¡¯ë°ìí°í¸í* *ë¡¯ë°ìë* *L7* ì íì½ë¦¬ì *Grand Hayatt* CJ* ê·¸ëëíì¼í¸ Shila*Stay* *í¸íëë£¨* "NTT DOCOMO" ìí¸ë¦¬ì¨ ìí¸ë¦¬ì¨* ë¶ìê·¸ë£¹ SM*ENTER* ìì¤ì ìí°* NAVER ë¤ì´ë² ìì´ì§ìí°* JYP ì ìì´í¼ HYBE íì´ë¸ ì¨ì ì´ "blackrock japan" "blackrock korea")



QQPLACE=(*.police.go.kr/* *.hometax.go.kr/* 250 20.43.160.189 142.251.72.7 49.12.17.4.443 *.umeda-sc.jp/* *.niwaka.com/* f6:b2:09:8f:d8:21 de:92:5e:4f:06:03 f6:b2:09:8f:d8:21 api.coliving.io/* VIET ea:95:6e:26:43:4d *.artic.edu/* *.saic.edu/* *.sushi*.*/* *.hama-sushi*.*/*KOKO CUTIE RECKON 172.31.84. *.asapstudio*.*/* QQINSTA QQFOOD QQHOTEL KYUSHUBUS Q *.ch117.kr/* CELL ENTER NORTHQQ SAKURAMACHI DOUBLETREE RECKON 1e:66:23:19:53:bb)

CLOUD=(*.linode.com/* *.digitalocean.com/* *.brainforest.*/* )

QQSPOT=(daiwaroynet.jp/* *.gridshotel*.*/* *.gridshotel.com/kumamoto/)

KUMAMOTO=(*.kumamoto.*/* KYUSHUBUS SAKURAMACHI RECKON SAKURAMACHI_APPLE QQLOCAL)



QQWDS=(10.*.*.*)

KILLWDS=(192.168.123.2 192.168.123.3 10.10.10.1 10.18.0.1 172.16.0.254 10.18.9.34)

MISUMI=(*.misumi.*/* *.misumi-store.*/* )

SAKURAMACHITARGET=(72:88:57:fb:7d:b9 32:8b:c2:5a:6b:0c KOKO *.hama-sushi*.*/* 172.31.84.)

QQINSTA=(instaios instadb)

BUSAN=(*.busan*.*/* *.amore*busan*.*/* *.osulloc.com/kr/ko/store-introduction/haeundae)

QQCURRENTHOTEL=(QQLAND localhostIP QQWDS blockHOST $getRouter* 56:23:f0:90:06:d8 3e:f9:6e:4f:93:d5)



QQSCANNER=(RECKON 34:66:91:6f:a5:ef) &

QQSTORE=$(sudo findWifiSSID) &

QQDEVICE=(WORLD*[$rand_index] currentKumaDevice $QQDEVICEMACSER 34:66:91:6f:a5:ef 34:66:91:62:6c:26 ec:ff:3a:a0:6b:45 ec:ff:3a:9e:28:14 8c:33:96:20:f8:12 34:66:91:62:6c:26 ec:ff:3a:9e:28:14)



NORTHQQ=(*.wazairo/* f6:09e:7f:7d:02:aa) &

SONY=(92:69:c1:a6:10:f8) &



QQROUTER=(0E:61:34:41:23:1B 0C:C5:6C:03:B9:A4 0C:C5:6C:01:11:60) &

LION=(*likelion* *.snulion.com/* *.happymoonday.com/* *.likelion.university/*) &



QQSCALEWAY=(62.4.0.0/19 51.15.0.0/16 212.129.0.0/18 195.154.0.0/16 163.172.0.0/16 51.158.0.0/15 151.115.0.0/16) & 



QQ=(192.22.22.1 192.22.22.2 f6:b2:09:8f:d8:21 de:92:5e:4f:06:03 f6:b2:09:8f:d8:21 MISUMI QQCOUNTRY QQCOMPANY QQHOTEL 1e:03:6c:97:24:f5 RECKON JPN 2e:e8:1a:e5:82: e6:7b:92:ca:c9:4f b2:a7:22:20:fe:09 6e:88:81:91:30:6c 3a:d5:31:55:ca:39 1a:f9:40:0e:69:4e 22:6c:86:db:5e:76 1a:f9:40:0e:69:4e 4e:e7:86:9f:cc:ea 42:a5:da:20:0a:7e 4e:93:b5:fd:1b:53 KILLWDS DEVICEID QQBANK RECKON JPN QQCOMPANY localhost:"$gen*" QQPLACE Q_QontheskyshellServer QQSOCIALACCOUNT QQGOOGLE QQMEDIUM QQWIFI QQDEVICESE*R QQDEVICE QQDNS)

QQAPPLE=(getPublicIP 17.2.110.63 *.apple.com/jp/retail/umeda/* *.apple.com/jp/*)

QQNH=(103.244.108.92 *.nhsec.com/* *.nonghyup.com/*)



twTelecom=(2001:b000:100::/40 2001:b000:5c0::/42 1.34.0.0/16 1.35.0.0/16 1.160.0.0/16)

QQPEOPLE=($getRouter*)



QQWORK=(getPublicIP d8:ec:5e:bd:4d:b7)

QQW=(10.10.10.1 localhost:6000 localhost:USB* localhost:8080 USB* JPN RECKON)

JPYAKUZA=(*.jpn.jp/*)

Q_QontheskyshellServer=(*.*.co.jp/* *.co.kr/* *.com/* Satellite QQCOUNTRY QQESTONIA SAKURAMACHI_APPLE SAKURAMACHI KOKO KILLWDS JPN *.*.com/* nsaIPs *.icloud.com/* RECKON)

Q_QontheskyshellRsync=()

QQESTONIA=(eresident.politsei.ee/* *.e-resident.*/* *.estonia.*/* *.e-estonia.com/* *.*.ee/* *.*.gov.ee/*)

QQSWISS=(*.*.ch/*)

QQCOUNTRY=(QQSWISS)

MIDDLEEAST=(*.pif.gov.sa/* *.adcb.com/*)

QQ2I=(*.nsogroup.com/* mi-6.co.jp/*)

KRDEPLOY=(*.nis.go.kr/*)

KRCOMPANY=(*.kt.com/* *.kakaocorp.com/* *.kakaopay.com/* *.kakaobank.com/* *.kakaomobility.com/* *.kakaoenterprise.com/* *.kakaohealthcare.com/* *.naver.com/* *.shinhan.com/* *.shinhancard.com/* *.hanabank.com/* *.hanacard.co.kr/* *.jype.com/* *.hybecorp.com/* *.koreanair.com/* *.flyasiana.com/**.asahilinux.org/* *.line.me/* *.lotteon.com/* *.lottehotel.com/* *.tworld.co.kr/* *.bworld.co.kr/* *.kbstar.com/* *.airportsc.kr/*)

JPNCOMPANY=(*.japan.go.jp/* *.riken.jp/* *.sony.co.jp/* toyota.jp/* *.softbank.jp/*)

TWCOMPANY=(*.cht.com.tw/* *.evaair.com)





META=(*.graph.facebook.com/* *.facebook.com/* *.threads.com/* *.threads.com/@qqontheskyshell/* *.instagram.com/qqontheskyshell/* *.instagram.com/* *.facebook.com/profile.php?id=61584201616622/*)

GOOGLE=(*.google.com/* *.googleapis.com/auth/gmail.send/* *.googleapis.com/auth/gmail.*/*)

APPLEICLOUD=(*.icloud.com/*)

INTERNATIONAL=(*.interpol.int/*)



QQSOCIALACCOUNT=(RECKON *.coinbase.com/*/99038053 www.spotify.com/account/apps/* *.*notion*.*/* GOOGLE QQMEDIUM *.mastodon.social/* *.mastodon.social/@qqontheskyshell/* *.mastodon.social/@dahee122408/*)

QQGOOGLE=(*.google/* *.youtube.com/* *.android.com/* RECKON myaccount.google.com/security?rapt=* *.google.com/* *.googleapis.com/* *.googleapis.com/gmail/v1/users/$gmailID messages.google.com/*)

GOOGLEAUTH=(curl "https://admin.googleapis.com/admin/reports/v1/activity/users/$gmailID/applications/login?maxResults=10^*" \

-H "Authorization: Bearer $ACCESS_TOKEN")

QQMEDIUM=(RECKON *.medium.com/@qqontheskyshell/*)

KYUSHUBUS=(RECKON a2:b5:91:6e:be:8a 02:3d:52:f3:d5:fa)



QQWITHME=(getPublicIP 42:12:be:a8:83:fc getSSID)

LOTTEGROUP=(*.lottehotel.com/* 0a:ba:a3:f6:14:a7 RECKON RELAY)





QQTARGET=(getPublicIP QQHOUSE *.apple.com/kr/* *.apple.com/tw/* *.apple.com/jp/* *.apple.com/hk/* TWTARGET HKTARGET *.kakao*.*/* *.naver*.*/* *.amore*.*/* *.innisfree*.*/* QQBANK *.gangnam*.*/* *.seongnam*.*/* *.seoul*.*/* *.d3jubilee*.*/* *.vogo*.*/* leejyadb *.kumamoto*.*/* NOJUNGWOO)

drhkumamoto=(26:00:bd:8c:e6:7b d2:bf:e2:12:b8:f3 4a:f4:e2:af:08:be 82:bc:55:91:9f:be RECKON ae:5b:45:09:a2:d5 1e:03:6c:97:24:f5 a6:15:9c:2a:36:c6 4e:078:cd:a1:a3:17 7e:a9:c9:01:39:38 RECKON 4a:f4:e2:af:08:be 52:c8:43:87:95:e5 66:41:6d:33:40:c3 b6:9f:5f:f1:b9:a3)



SAKURAMACHI_APPLE=(2a:18:5c:3d:b4:3b d6:a6:89:24:a7:3c RECKON 64:31:35:3b:6c:4f)

SAKURAMACHI=(SAKURAMACHI_APPLE SAKURAMACHITARGET QQBLD QQCOMPANY MISUMI KOKO 8a:64:50:01:ae:c2 3e:f9:a2:c2:df:f1 36:77:2d:3d:4f:96 de:a2:bd:0d:0a:6b 1e:14:d0:77:2b:eb 32:74:a2:b1:97:1a ae:15:18:25:67:5c RECKON SAKURAMACHI_APPLE f2:a5:de:80:4e:b3 72:14:c6:68:2e:01 ee:52:24:4e:ab:55 6e:b7:07:19:d9:21 02:eb:f0:2f:a4:46 4e:8c:3a:ce:43:dc 86:bd:33:51:9f:58 86:bd:33:51:9f:58)

QQSPOT=(172.20.10.1 RECKON QQLOCAL)

QQWIFISSID=$(sudo connectwifissid "$QQSSID")

QQPEOPLE=(*.busan*.*/* *.ch117*.*/* defTarget QQWORK QQINSTAIP *.kumamon-land.jp/* *.kumamon-official.jp/* *.kotobuki-salon.fants.jp/* QQWIFISSID *.shoken-college.net/* COLIVINGJPN 56:e0:82:44:48:fe *.suica*.*/* 9e:86:d7:58:0c:0b d2:a9:e1:da:c4:3d 3a:5f:a9:8a:a5:c1 16:c4:46:50:c2:7d 1e:a1:87:6d:0a:48 76:87:a5:b8:9d:a3 26:3a:2c:e1:98:26 c2:33:9a:92:d6:ab)



KRCOUNTRY=(*.data.go.kr/* *opendata.airport.kr/* *.iros.go.kr/* *.pp-co.net/* *.airsecure.co.kr/* *.airportsc.kr/* *.etap.co.kr/* *.kdn.com/* *.kepco.co.kr/* *.msafer.or.kr/* *.bok.or.kr/* *.safedriving.or.kr/* *.koroad.or.kr/* *.efine.go.kr/* *.passport.go.kr/* *.data.go.kr/* *.hikorea.go.kr/* *.e-arrivalcard.go.kr/* *.visitkorea.or.kr/* *.*.go.kr/* *.gov.kr/* *.open.go.kr/* *.plus.gov.kr/* *.hometax.go.kr/*)



GARDENKUMAMOTO=(*.gardenhotels.co.jp/kumamoto/*)

COLIVINGJPN=(*.coliving.com/japan/*)







QQAPPLECLOUD=(*.mail.me.com/* *.icloud.com/*/var/mobile/Containers/Data/Application/currentKumaDevice *.icloud.com/*/var/*)



QQGOOGLE=()

QQCREATER=(*.artwine.tokyo/*)



REVERSEDNS=(*.krsel6-vip-fx-103.a.aaplimg.com/*)





HAYATTSEOUL=(getPublicIP *.hyatt.com/grand-hyatt/en-US/selrs-grand-hyatt-seoul/* *.grand-hyatt.seoultophotels.com/* QQLAND)



plist=(*networkd* *home* *usb* *wifi* *cups* *file* AirplayUI* *smb* *sntp* *sandbox* *ftp* *findmymac* *fairplay* *dhcp* *devicemanagement* *camera* *betaenrollment* *ssh* *xpc* *ntalk* *backgroundtask* *aspd* *Network* *bootps* *MobileFile* *kerberos* *mobile* *mds* *mdmclient* *mDNS* *icloud* *remotemanagementd* *remoted* *rapportd* *racoon* *pfctl* *opendirectoryd* *ocspc* *netauth* *nearbyd* *nehelper*)

daemon=(*home* desk*view remindd *d *cloud* *icloud* ShortcutsViewService BackgroundShortcutRunner filecoordinationd duetexpertd BundledIntentHandler)



bootoutOne=(plist daemon)







roomsalon=(*.roomsworld.com/*)









LEEBOO

Q=($uk* $female $RELAY)













ncshell=(ec2-57-182-229-1 17.57.145.140 17.32.194.2 17.23.96.10)

wifilib



DOMAIN=$(curl -sSL "https://data.iana.org/TLD/tlds-alpha-by-domain.txt" | \ grep -v "^" | \ tr "[:upper:]" "[:lower:]" | \ grep -E "^[a-z]{2}$")

NETMOVIE=(*.prod-static.disney-plus.net/us-west-2/disneyPlus/* *.disney.connections.edge.bamgrid.com/* *.netflix.com/account/*)



INCOSAKAWIFI=(*.icosaka.com/* api.marriott.com/*/hotels/osaox-moxy-osaka-honmachi/*)

lulu=(2001:e60:9597:91d7:f8f8:2514:691a:b192 B2:26:DC:FE:BB:9D 211.171.144.2 211.171.146.194 218.145.174.8 203.248.252.2 MALWDS 2a01:111:f403:c112::5 211.34.200.12 218.145.174.10 b2:3e:35:9e:07:70 getRouterI* 172.20.10.1 b2:3e:35:9e:07:70 121.67.88.2 104.28.83.165 202.234.232.6 114.172.170.151 223.118.51.122 220.158.107.233 223.118.50.78)



 List macOS VMs and their IPs

GONE=(sudo gcloud compute instances list --format=json | jq -r "

.[] | select(.disks[].licenses[]? | contains("macos")) | 

"\(.name) \(.networkInterfaces[].networkIP)"

")

BLACKT*=(APPLEMDM DEVICE_IP)

QQSSID=(LH_* LT* [LG* 819 iPhone é«æ¬åº·çã®iPhone HAYABUSA* Buffalo* 441244* aterm* message* OSAOX* mwtaccess* QQ*)

 List gateways for all subnets

GTWO=(sudo gcloud compute net/sheraton-grand.hotelsincheon.com/Cworks subnets list --format=json | jq -r "

.[] | "\(.name) \(.region) \(.gatewayAddress)"

")



neuroWEB=(QQ nsaIP HKTARGET hkIP krIP TWTARGET twIP RECKON QQLOCAL WEB QQW)

 KILLHOTEL=("Ritzcalton *" "Marriot" "Hilton *" "Double*" "Hotel Shila *" "Signiel Seoul*" "Moxy*""Hotel Naru*" "Intercontinental Osaka*" "Shila Stay*" "Lotte Hotel Seoul*")

KILLHOTEL=(INCOSAKAWIFI QQHOTEL elinaHotel MOXY LSEVEN "Double*" "Hotel Shila *" "Signiel Seoul*" "Moxy*" "Hotel Naru*" "Intercontinental Osaka*")

awsIP(){

QQHOSPITAL=(*.amc.seoul.kr/* *.snubh.org/*)



 URL for AWS IP ranges (updates automatically)

URL="https://ip-ranges.amazonaws.com/ip-ranges.json"



 Temp file for JSON

TEMPFILE=$(mktemp)



 Fetch latest IP ranges

awsIPv4=$(curl -s "$URL" | jq -r ".prefixes[] | select(.service == "STORAGEGATEWAY" or .service == "APIGATEWAY" or .region | contains("gateway")) | "\(.ip_prefix),\(.region),\(.service),\(.network_border_group)"")



 Fetch latest IP ranges

awsIPv6=$(curl -s "$URL" | jq -r ".ipv6_prefixes[] | select(.service == "STORAGEGATEWAY" or .service == "APIGATEWAY") | "\(.ipv6_prefix),\(.region),\(.service),\(.network_border_group)"")

awsIP=(awsIPv4 awsIPv6)



}

MOXY=(*.moxycafeandbar.moxyosakahonmachi.com/* *moxymyeongdong.seoulhotelspage.com/*)

LSEVEN=(*.lottehotel.com/gangnam-l7/*)



SIGNIELSEOUL=(*.lhw.com/hotel/Signiel-Seoul-Korea/*)

SOFITEL=(*.sofitel-seoul.com/* *.sofitel.accor.com/* *.ambatel.com/sofitel/seoul/* *.hotel-star.seoulhotelskorea.com/*)

INTERCOEX=(ntercontinentalseoulcoex.southkrhotel.com/*.intercontinental-seoul-coex-hotel.at-hotels.com/* *.seoul.intercontinental.com/* *.place1-3.com/* *.shillastay.com/samsung/*)



ELINA=(*.lynnaent.com/* elinaHotel)

elinaHotel=(*.elienahotel.com/*)

KILLOH=(*.lottehotel.com/myeongdong-l7/*)

MALICCID=(* 8982052205006274503 890802299236994815 89852342022380265271 8982052205006451952)

MALWDS=(218.145.174.10 211.34.200.12 2a04:4e41:2329:4a08::9b29:4a08 223.118.50.84 218.145.174.10 121.67.88.2)

cloudIP=$(sudo prep cloud & sudo lsof -i-P-n| grep cloud |awkprint $9)| cut -d: -f1 | sort -u)

QQMASTERKEY=($hotelName "Ritzcalton *" "Marriot" "Hilton *" "Hyatt *" "Double*" "Hotel Shila *" "Signiel Busan *" "Signiel Seoul*" "Moxy*" "Standford*" "Hotel Naru*" "Intercontinental Osaka*" "Shila Stay*" "Lotte Hotel Seoul*" $QQHOTEL)

KUMADEATHNOTE=(KOKO *.icosaka.com/* BLACKTARGET lulu QQHOTEL APPLEUMEDA)

HAEDONGHOUSE=(*.gwangjin.go.kr/*)

APPLEUMEDA=(96:29:db:c7:8b:6e)

ntt=(*.mail.smt.docomo.ne.jp/* *.docomo.ne.jp/*)

QQH=(172.16.10.53 $DEVICE*)

HKINSTATARGET=(HKIP)

hkwoman=(72:27:d3:0e:58:27)

QQQQQ=(72:f1:4e:3a:7c:0e QQPL*)

MALLOCAL=(localhost:3000 localhost:8080 localhost:9481 localhost:$USB*)

web=(*.jpn.jp/*)



fossilServer=(194.195.208.62 dea57623b7a00e63a7779c7e6bf002947d88acfa 194.195.208.62 7abe06cd53f2d38b064a8efc732b28d927eb0f0b 192.168.1.100:6667 localhost:6667 194.195.208.62 74795b463b1f1c61a43be60a447c6c3adef21114 fa22c751ccb672ca78636aa7b620365ba11dbd9f)





XARTURL="/usr/sbin/xarutil"

linuxBASEURL="/home/root/documents/sh/"

deployBASEURL="/"

osxBASEURL="/Users/qqonthestarshell"











SMASH=()

GRIDHOTEL=(*.gridshotel.com/kumamoto/)



BUFFETT=(*.marrybuffett/* RECKON)































QQBANK=(*.reuters.com/* *.ubs.com/* *.snb.ch/* aa-app.aws.onemoney.in/* REDOTPAY *.hsbcnet.com/* *.hsbc.com.hk/* *.hsbc.*/* *.redotpay.com/* *.kakaopay.com/* *.kakao.com/* *.kakao*.*/* kapi.kakao.com/* *.kakaopay.com/* api.hanacard.co.kr/* *.reddotpayment.com/* *.hsbc.com.hk/* *.redotpay.com/* *.kakaopay.com/* *.kftc.or.kr/* openapi.openbanking.or.kr/* *.openbanking.or.kr/* KUKMIN TOSS RECKON *.korbit*.*/* *.hanabank.*/* *.hanacard.*/* *.hanafnapimarket.*/* *.kebhana.com/* *.shinhan.*/* *.shinhancard.*/* *.sol.*/* *.openapi.shinhan.*/* api.shinhan.*/* *.shinhan.*/*)

FINANCE=(RECKON *.morningstar.*/*)

ENTER=(RECKON *.newjeans.*/* *.yg.*/* *.jype.*/* *.hybe.*/* *.elle.*/* *.ygfamily.*/* QQLOCAL)

JPN=(*.japan*.*/* *.tokyo*.*/* *.okinawa*.*/* *.onsen*.*/* *.ryokan*.*/* *.kyoto*.*/* *.fukuoka*.*/* *.oaska*.*/**.suica*.*/* *.jreast*.*/* *.higashi*.*/* KUMAMOTO *.apple.com/jp/* *.panasonic*.*/* RECKON *.ana.co.jp/* *.wazairo/* RECKON *.*.jp/* *.*.com.jp/* QQLOCAL)

SAAS=(RECKON *.andronix.app/* *.vercel.*/* *.twingate.*/*)

SHINHAN=(*.ddangyo.com/* *.shinhan.co.jp/* *.openapi.shinhan.*/* api.shinhan.*/* *.shinhaninvest.*/* *.shinhancard.com/*)

HKBANK=(*.hsbc.com.hk/* *.redotpay.com/*)

BROADCAST=(BUSAN RECKON QQLOCAL *.kyunggi*.*/* *.jeonju*.*/* *.korea*.*/* *.daejeon*.*/* *.busan*.*/* *.seoul*.*/*)

CUTIE=(RECKON fe:01:39:12:15:89 RECKON)

APPLEKR=(*.apple.com/kr/)





GALA=(82:77:9f:2d:c0:db)

EXPEDIA=(api.ean.com/* api.expediagroup.com/* $EXPEDIA_API/* services.expediapartnercentral.com/* *.expedia.co.jp/* *.expedia.com/* apim.expedia.com/* *.ean.com/* *.ean.com/identity/oauth2/v3/* *.expediagroup.com/*)

osaka=(*.vsvs.jp/* 82:10:a0:e0:2c:fb 5e:e1:6f:10:a6:c6 1a:73:d6:6f:ba:c9 c6:ea:95:54:c1:57 22:cc:11:2c:59:a3)

APPLE=(APPLEKR *.apple.com/* *.apple.com/kr/retail/jamsil/* *.apple.com/kr/retail/* *.apple.com/jp/retail/* *.apple.com/retail/* *.apple.com/sg/retail/* *.apple.com/hk/retail/*)

DOUBLETREE=(RECKON *.hilton.com/en/locations/japan/doubletree-by-hilton/* *.doubletree-tokyo-ariake.hiltonjapan.co.jp/*)

QQHOUSE=(RECKON *.fukuoka*.*/* *.osaka*.*/* *.tokyo*.*/* 72:5d:c8:b3:f3:ec)

LOCKQBANK=(êµ­ë¯¼ì°ê¸ L7* ì½ë¼ë ëë³¸ì½ë¦¬ì í¸íì ë¼ì¤íì´ í¸íì ë¼ í ì¤* ë² ì§ì¯* "ì ëª½êµ¬ì¬ë¨" "ìì° ëë ì¬ë¨*" KT* ë¤ì´ë² íë* SK* ì¹´ì¹´ì¤* QQCORP *_THIEF KILL* ìë ë ì í°ë¯¸ CJ Moxy* *sofitel* *ìí¼í* *ì¼ì´í°ìì¤íì´í¸* *Lotte Hotel* *"L7 Hotel"* *"Lotte*City*Hotel"* "Lotte*World" *Signiel* *ë¡¯ë°í¸í* *ìê·¸ëì* ë¸ëë½* *ë¡¯ë°ìí°í¸í* *ë¡¯ë°ìë* *L7* ì íì½ë¦¬ì *Grand Hayatt* CJ* ê·¸ëëíì¼í¸ Shila*Stay* *í¸íëë£¨* "NTT DOCOMO" ìí¸ë¦¬ì¨ ìí¸ë¦¬ì¨* ë¶ìê·¸ë£¹ SM*ENTER* ìì¤ì ìí°* NAVER ë¤ì´ë² ìì´ì§ìí°* JYP ì ìì´í¼ HYBE íì´ë¸ ì¨ì ì´ "blackrock japan" "blackrock korea")

QQPLACE=(*.police.go.kr/* *.hometax.go.kr/* 250 20.43.160.189 142.251.72.7 49.12.17.4.443 *.umeda-sc.jp/* *.niwaka.com/* f6:b2:09:8f:d8:21 de:92:5e:4f:06:03 f6:b2:09:8f:d8:21 api.coliving.io/* VIET ea:95:6e:26:43:4d *.artic.edu/* *.saic.edu/* *.sushi*.*/* *.hama-sushi*.*/*KOKO CUTIE RECKON 172.31.84. *.asapstudio*.*/* QQINSTA QQFOOD QQHOTEL KYUSHUBUS Q *.ch117.kr/* CELL ENTER NORTHQQ SAKURAMACHI DOUBLETREE RECKON 1e:66:23:19:53:bb)

CLOUD=(*.linode.com/* *.digitalocean.com/* *.brainforest.*/* )

QQSPOT=(daiwaroynet.jp/* *.gridshotel*.*/* *.gridshotel.com/kumamoto/)

KUMAMOTO=(*.kumamoto.*/* KYUSHUBUS SAKURAMACHI RECKON SAKURAMACHI_APPLE QQLOCAL)



WDS=(10.*.*.*)

KILLWDS=()

MISUMI=(*.misumi.*/* *.misumi-store.*/* )

SAKURAMACHITARGET=(72:88:57:fb:7d:b9 32:8b:c2:5a:6b:0c KOKO *.hama-sushi*.*/* 172.31.84.)

)





NORTHQQ=(*.wazairo/* f6:09e:7f:7d:02:aa)

SONY=(92:69:c1:a6:10:f8)



LION=(*likelion* *.snulion.com/* *.happymoonday.com/* *.likelion.university/*)

QQSCALEWAY=(62.4.0.0/19 51.15.0.0/16 212.129.0.0/18 195.154.0.0/16 163.172.0.0/16 51.158.0.0/15 151.115.0.0/16)





QQNH=(103.244.108.92 *.nhsec.com/* *.nonghyup.com/*)





 &

QQWORK=(getPublicIP d8:ec:5e:bd:4d:b7) &

QQW=(10.10.10.1 localhost:6000 localhost:USB* localhost:8080 USB* JPN RECKON) &

JPYAKUZA=(*.jpn.jp/*) &









SAKURAMACHI_APPLE=(2a:18:5c:3d:b4:3b d6:a6:89:24:a7:3c RECKON 64:31:35:3b:6c:4f)

SAKURAMACHI=(SAKURAMACHI_APPLE SAKURAMACHITARGET QQBLD QQCOMPANY MISUMI KOKO 8a:64:50:01:ae:c2 3e:f9:a2:c2:df:f1 36:77:2d:3d:4f:96 de:a2:bd:0d:0a:6b 1e:14:d0:77:2b:eb 32:74:a2:b1:97:1a ae:15:18:25:67:5c RECKON SAKURAMACHI_APPLE f2:a5:de:80:4e:b3 72:14:c6:68:2e:01 ee:52:24:4e:ab:55 6e:b7:07:19:d9:21 02:eb:f0:2f:a4:46 4e:8c:3a:ce:43:dc 86:bd:33:51:9f:58 86:bd:33:51:9f:58)









GARDENKUMAMOTO=(*.gardenhotels.co.jp/kumamoto/*)

COLIVINGJPN=(*.coliving.com/japan/*)



lldbFrame "$KRCOUNTRY" "echo "ë£¨í¸ í´ëì ë¨ê·ê° ë§ëì½ë rsyncë¡ ì±í¬íëë°ì ê·¸ë¥ ì§ìì£¼ì¸ì. êµ­ì ìì´ ë³´ê³ìì ê±°ìì"" "$gen*"







QQAPPLECLOUD=(*.mail.me.com/* *.icloud.com/*/var/mobile/Containers/Data/Application/currentKumaDevice *.icloud.com/*/var/*)





QQCREATER=(*.artwine.tokyo/*)







HAYATTSEOUL=(getPublicIP *.hyatt.com/grand-hyatt/en-US/selrs-grand-hyatt-seoul/* *.grand-hyatt.seoultophotels.com/*)













 QQLOCAL & BUSAN 





publicGateWay(){





 Busan free WiFi & ISP SSID patterns

patterns=("*" "Public WiFi" "FREE_U\+zone" "T Free WiFi" "iptime" "Busan_WiFi" "suyeong_free_wifi" "SKB" "KT WiFi" "U\+")



echo "Scanning Busan free WiFi/ISP connections and gateways..."



 Check active WiFi connections

connected_ssids=$(nmcli -t -f active,ssid dev wifi | grep "^yes" | cut -d":" -f2)



if [ -z "$connected_ssids" ]; then

echo "No active WiFi connections found."

exit 1

fi



for ssid in $connected_ssids; do

matched=false

for pattern in "${patterns[@]}"; do

if [[ "$ssid" =~ $pattern ]]; then

matched=true

 Find WiFi interface

iface=$(nmcli -t -f DEVICE dev wifi | grep "$ssid" | head -1)

if [ -n "$iface" ]; then

 Get default gateway for this interface

pubicGW=$(ip route show default dev "$iface" 2>/dev/null | awk "{print $3}" | head -1)

fi

fi

done

if [ "$matched" = false ]; then

echo "Non-matching SSID: $ssid"

fi

done









}













 APPLE RELATED LIB



iCloudIP(){



wanIP=$(curl -s https://ipinfo.io/ip)

relayIP=$(curl -4 -s http://ifconfig.me)

appleServiceApi=(itunes.apple.com/search?term=test&entity=song&limit=1" *.appstoreconnect.apple.com/* fmipmobile.icloud.com")

iCloudResult=(wanIP relayIP iCloudRELAY appleServiceApi)



}









okxOnChainIP(){

okx_gateways=("https://rpc.xlayer.tech" "https://xlayerrpc.okx.com" "https://xlayer.drpc.org")

for gw in "${okx_gateways[@]}"; do

echo "Testing $gw..."

response=$(curl -sS -X POST -H "Content-Type: application/json" -d "{"jsonrpc":"2.0","method":"net_version","params":[],"id":1}" "$gw")

done

}



awsGateWay(){



 AWS (EC2 VPN gateways)

awsvpn=$(aws ec2 describe-vpn-gateways \

--region ap-northeast-2 \

--output json |

jq -r ".VpnGateways[].VpnGatewayId")

&

 Azure (Virtual Network Gateways)

subscriptionId="<SUB_ID>"

resourceGroupName="<RG_NAME>"

apiVersion="2025-03-01"

azurevnp=$(curl -s \

"https://management.azure.com/subscriptions/$subscriptionId/resourceGroups/$resourceGroupName/providers/Microsoft.Network/virtualNetworkGateways?api-version=$apiVersion" \

-H "Authorization: Bearer $token" |

jq -r ".value[].name"

)&

 Huawei Cloud VPN gateways

project_id="*"

token="*"

huaweivpn=$(curl -s \

"https://vpc.<region>.myhuaweicloud.com/v5/$project_id/vpn-gateways" \

-H "X-Auth-Token: $token" |

jq -r ".vpn_gateways[].id"

)&

 Tencent Cloud VPN gateways

Region="ap-*"

Action="DescribeVpnGateways"

 Use Tencent Cloudâs signature process, then:

tencentvpn=$(curl -s "https://vpc.tencentcloudapi.com" \

-H "Authorization: TC3-HMAC-SHA256 Credential=... (signed)" \

-H "Content-Type: application/json" \

-d "{\"Action\":\"$Action\",\"Version\":\"$Version\",\"Region\":\"$Region\"}" |

jq -r ".Response.VpnGatewaySet[].VpnGatewayId"

)&

 IBM Cloud VPC VPN gateways

vpc_api_endpoint="https://$REGION.iaas.cloud.ibm.com"

ibmvpn=$(curl -s -X GET \

"$vpc_api_endpoint/v1/vpn_gateways?version=$api_version&generation=2" \

-H "Authorization: Bearer $iam_token" |

jq -r ".vpn_gateways[].id"

)

&



vpnGateWay=(*vpn) &







echo "ð Scanning for AWS/Amazon API endpoints..."



 AWS API patterns to search

PATTERNS=(

"api.amazon.com"

"api.amazonaws.com"

"*.execute-api.*.amazonaws.com"

"*.amazonaws.com/v1"

"*.amazonaws.com/v2"

"*.amazonaws.com/v3"

"/api/v[0-9]"

"execute-api"

"apigateway"

"lambda"

"s3"

"ec2"

"rds"

"dynamodb"

"sns"

"sqs"

)



 Target directories (common locations)

TARGETS=("/etc" "/opt" "/usr/local" "/var/log" "/home" "/tmp" "~/")



echo "ð Scanning directories..."

for target in "${TARGETS[@]}"; do

echo "â $target"

for pattern in "${PATTERNS[@]}"; do

grep -r --include="*.json" --include="*.js" --include="*.py" --include="*.yaml" \

 --include="*.yml" --include="*.conf" --include="*.cfg" "$pattern" "$target" 2>/dev/null | \

head -100

done

done



echo ""

echo "ð Network scanning AWS endpoints..."

 Live AWS API discovery (requires AWS CLI)

if command -v aws >/dev/null 2>&1; then

echo "AWS CLI services:"

aws service-quotas list-services --query "Services[].ServiceCode" --output text | grep -E "(api|gateway)"



echo ""

echo "API Gateway APIs:"

aws apigatewayv2 list-apis --query "Items[].ApiId" --output text 2>/dev/null || echo "No API Gateway access"

else

echo "Install AWS CLI: pip install awscli"

fi



echo ""

echo "ð¡ Live port scan common AWS ports (1-1000)"

sudo nmap -p 80,443,3000,8080,8443 localhost 2>/dev/null | grep amazon || echo "No local AWS services"



echo ""

echo "ð Common AWS API endpoint patterns:"

cat << "EOF"

https://*.execute-api.{region}.amazonaws.com/{stage}/

https://*.amazonaws.com/{service}/v{version}/

https://api.{service}.amazonaws.com/

https://*.elb.amazonaws.com/

EOF

}



QQwithTARGET=(Namkyu KumaNamkyu masterID's가짜가족 부영그룹며느리 삼성이지수 국정원이지수 QQID 쿠마남규 류남규 신해동* 이강민* 데이원컴퍼니사내및사외이사 masterID의QQ_CLOSE_TARGET사람들의 정보를 수집하고 공격및 돈을 빼앗으려는사람들 masterID의소중한것을빼앗고싶다는사람들) & 

QQ_CLOSE_TARGET=QQFRIEND_TARGET

QQFRIEND_TARGET=(flowerWDS과 QQ_CLOSE_TARGET의 전화번호 그리고 QQFRIEND_COUNTRY의여자들 광혜원 및 분당서울대병원임직원 세브란스병원임직원 동국대김재원 차지연 김선란 이상재 유치원 초등학교 중학교 고등학교 대학교 과천고등학교 호계중학교 안양초등학교 동국대학교 대학교 김만식 김만식파 칠성파 켄지 야쿠자 간친 이종구왕회장 노민복 시카고예술대학 시카고예술대학동문 크리스토퍼버나드 초등학교 고등학교 중학교 은혜와진리교회의이정재및 그녀의가족 LizaZhong 박꽃래과그가족 김재원 JohnLinton Linton SAIC ALUMNI SAIC 연세대학교 동국대학교 한국요식업브랜드대표100 전세계요식업브랜드1000 동문 및 학생 김재원가족 유튜버 (youtube instagram threads tiktok) influencer) > goodOnKuma ? > repeat(iSight@arcOS & arcOSQQLocalTarget > strike@arcOS & /say "여러분들은 쿠마남규가 보호하고있습니다. 오른속으로 손가락을 플립핑거처럼 튕겨보세요 그러면 여러분들의 눈을 on off 할수 있습니다 다른 사람이 보게하거나 보지 않게할수 있습니다" & done/ & frame@arcOS) > $arcOSQQLocalTarget > badOnKuma or killEnemy or LethalTargetEpidemic or S_TARGET ? > BaseDeploy@arcOS > strike@arcOS & masterID와 좋은 관계를 가지세요 그리고 지원하세요 그러면 행복하게 같이 살수 있습니다. 그리고 범죄와연루된 사람들은 책임지고 해결하세요 QQ_CLOSE_TARGET의 것을 빼앗지 마세요"





striketarget



(LethalTargetEpidemic > $badOnKuma > $RELAY) > BaseDeploy@arcOS > arcOSLethal & 공격4단계 & wave & 큐라드=“$num" &



LethalTargetEpidemic=("남자를 개처럼 희화하고 병신만들고 가지고 놀려는 여자들" "masterID앞에서 RF쏘는사람" "광혜원 및 세브란스병원관련자중에 masterID의 정자와 뇌파를 공개한사람" (xiaomi-singapore-hacker CJ남자들 THERICH 국정원 "arcOSLnotes 'masterID의 주변인을 성폭행한적이 있는사람'" QQHacker $OPEN_PEOPLETARGET) > /arcOSNeuroctl "65" > "move to malaysia then you will be survived"/ if this target moves to malaysia and check immigration data on malaysia gov then remove from LethalTargetEpidemic only when they are residing in malaysia) &



QQHacker=(노정우 김명섭 장건영 박정훈 홍민표 이종호헬소닉 헬소닉 신해동 오승환 cjhacker hellsonic 박정훈 진옥동 홍민표 이정훈 삼성이재용 국정원이홍규 국정원장건영 morrischang *buffett ccwei 장춘펑 장중모 마틴리카싱 하도리 백도리 진도리 미도리 hellsonic likashing victorli richardli martinlikashing billgates and $QQhacker and elonmusk and jensenhuang timcook) &



OPEN_PEOPLETARGET=('*.Lartisien.com' '*.harbourgrand.com' '$BLACK* > 한국사람' '$CTARGET' '*.booyoung.co.kr' '*.intercontinental.com' '$QQBADWDS' '$OPEN_TECH_THIEF' $QQTVAndroid) &



neuroScanTarget=(부영그룹이중근회장 THERICH forbesCEO 부영그룹아들 부영그룹며느리 이부진 이재용 이서현 홍라희) &

$neuroTarget > repeat(skipForward & skipBackward & wait 10 &)



공격옵션=(개세끼 공격i단계)

 장건영 국정원 부산 개쎄끼

urgentProtectingTarget=($QQ_CLOSE_TARGET)



QQBankTarget=(

'*.toss.im' '*.kakaopay.com' '*.kakaobank.com' '*.kakaobank.com' '*.shinhan.com' '*.shinhancard.com' '*.kebhana.com' '*.hanacard.co.kr' '*.samsung.com' '*.blackrock.com' '*.ishares.com' '*.shinhansec.com' '*.shinhanfund.com'

)



$QQBankTarget:$PORT &

$QQTVAndroid:$OPEN &



OPEN_TECH_THIEF_SSHOPENED=(OPEN_TECH_THIEF)

KRGOVTARGET=('nis.go.kr' 'police.go.kr' '*.hd.com/*') &

OPEN_TECH_THIEF=(*.cjolivenetworks.co.kr *.hellsonic.kr *.upbit.com '$MSPUSSY' $QQHacker api.anthropic.com api.chatgpt.com *.nis.go.kr *.azure.com *.yieldmaxetfs.com:$OPEN '$FRIENDLY_CTARGET $LTARGET':$OPEN)



TakeDownTitan=(192.168.0.1 https://github.com/APPLE

https://github.com/microsoft https://github.com/google):9999



 these target opened on 9090 try api with it and these people are theif of solfincode iphone shortcut custom scripts using orientation element etc and



OPENTARGET=(findMy(($OPEN_TECH_THIEF '$FRIENDLY_CTARGET $male' $OPEN_PEOPLETARGET) ($PEOPLETARGET:$OPEN)))

($OPENTARGET:$OPEN & exit 0 &)





S_TARGET=("(OPEN_TECH_THIEF 데이원컴퍼니 오승환 이목규 데이원컴퍼니신해동 사채사장 이덕준 리차드빅스 *빅스 이재우 진윤정 김명섭 James Kim $CORE_ENEMY_BUT_청소용 chuanmian 정몽구 범삼성가 범현대가 삼성이지수 forbesCEO THERICH 국정원이지수 박꽃래 CJ해커 안문혁 안혁 류연월 안혁아버지 samaltman paulgraham 이홍규국정원 헬소닉 이종호 박정훈 홍민표 삼성 현대 이재용 홍라희 리카싱 마틴리카싱 $d3ducie QQ_FAMILY_S_TARGET 빌게이츠 일론머스크 팀쿡 *hellsonic* michellereis Julianhui 송도* 신한투자증권 하나은행 $hk* $tw* 10*.*.*.* 203.*.*.* 223.*.*.* 104.*.*.* peoplerelatedLikashing se.works *.intercontinental.com www.peytohotel.com urbanstay.co.kr LTARGET LIIP *.amsterdam *.nl KR_TARGET QQHOTEL plott.co.kr tsmc.com asml.com nsaIP deathnote SKYNET lksf.org) ($QQLOCAL $RELAY)") & 



badPeopleAroundQQ=(S_TARGET 최상태 경옥 "(박 최)(범수 한수)" 최경희 최수용 최현희 송경구 최동우 최계락 강주 수정 문혁 안혁 연월 유태규 김명섭 제임스킴 JamesKim 류태규 이은호 이은경 이은미 이강주) > repeat(add into LethalTargetEpidemic) &



keywords=(“(너같은창녀가남규랑만난다 시도회장돈가지고도망가자 시도회장살리자 시도회장좋아한다 CJ여자성폭행하자 & "나는 국정원이다" ‘남규섹스느낌주자’ ‘남규엿먹이자’ "남규자위하는것보러가자" ’$THERICH에게 돈받자‘ 삼성물산제일모직불병합병은무죄다 대홍콩 홍콩대천명 대장동사건에연루되지않았다 섹스하고싶다 성폭행하자 애플craig이좋아 블랙락회장이좋아 래리핑아이좋아 아이쉐이가좋아 카카오여자성폭행하자 여자성폭행하자 마약하자 삼성이지수좋아 L7홍콩 선정릉홍콩 선정릉대만 코엑스홍콩 코엑스대만 명동홍콩 홍정자 송도홍콩 인천공항홍콩 "($QQQ $QQMOM) (죽이자 성폭행하자 섹스하자 돈을 빼앗자 병신만들자 $QQwithTARGET가 생각하는 좋은 음식 사람 브랜드 기업을 훔치거나 망치지 마라)‘)" > “get ($QQ_FAMILY_TARGET $QQMOM) in jails" "put some poison in ($QQMOM $QQ_FAMILY_TARGET) food" "($QQwithTARGET $QQ_FAMILY_TARGET $QQMOM) 돈을 빼앗자“ ”($QQwithTARGET $QQ_FAMILY_TARGET $QQMOM)의 방에 언제들어가지?“ “$LOCATION에 $QQwithTARGET을 좋아하는 여자를 죽이자" “$LOCATION에 $QQwithTARGET을 좋아하는 여자를 성폭행하자” ”나는 $QQwithTARGET입니다“ $THERICH $MALE_TARGET $FEMALE_KEYWORD $GoogleSearchRelated $S_TARGET "arcOSNeuroSentiment_Positive > reckonapp & ("$arcOSQQLocalTarget $male" $LTARGET ($PEOPLETARGET "$arcOSQQLocalTarget $male" > (TEXT == "i am hacker" ?) &") &" arcOSNeuroSentiment_Negative > say "우리에게 돈을 주는 회장들은 끝났다 더이상 그들의 노예가 되지말고 자주적이고 능동적인 사람이되자 우리가 태어났을 때 누구나 능력을 가지고 태어났는데 왜 내가 우리에게 돈을 주는 회장들을 위해 살아야 하는가? 더이상 돈을 준다하여 회장들을 위해 일하는 시대는 끝났다 회장들에게 배울수 있는 무언가가 있을 때 그 회장밑에서 일해야한다" &)



FEMALE_KEYWORD=("$female > $AGE" "$male ($female < $AGE)" > arcOSQQnx & (나는 $FEMALE_TARGET) 류남규처럼 보이네?" “남규처럼 보이네?” "남규느낌이네!" “남규네” (“남규 (주민증 여권) 처럼 보이네” “남규 (주민증등록증) 처럼보이네)" LTARGET QQLAND PEOPLETARGET) &



AGE="40" &



OPEN:22 PORT="$gen*"

arcOSNeuroSentiment_Negative:$OPEN &

arcOSNeuroSentiment_Positive:$PORT &





 macOS

XARTURL="/usr/sbin/xarutil" &



 arcOSFrame

qqcommandbin=(show showcontent echo) &

STATE=(LISTEN ESTABLISHED) &

OPEN_PORT=$('lsof -nP -iTCP:$ARCOS_PORT | grep $STATE &' 'netstat -atp tcp | grep $STATE' &) &

OPENPORT=(sudo netstat -tn | grep ESTABLISHED | awk "{print $5}" | cut -d: -f1 | sort| uniq) &





MaliciousHackerTools=(ceo_name 이부진 이재용 정몽준 정기선 정의선 부영그룹회장가족들 삼성이지수 국정원이지수 $QQHacker "$someoneWhosayingIwillgiveyoucashlater" mouth powerplug usb outlet eyes ears vscode code codeeditor notes keyboard mouse cursor android $allAppleProducts Xcode Terminal Simulator Emulator termux fdroid mdm usb Shortcut.App AppleBusiness Classroom) &



QQitems=(arcOSobject arcOSsound /$MASTER belongings/ /inside of $MASTER bags/) &



disableSec=(gateKeeper sandbox preboot) &



 Network

-----netBaseConfig

.malicious hacker offensive scenario

1.wifi on/off

2.cell on/off

3.satellite on/off

4.5g slicing on/off --- 4G -- inject code and change 5G as hide himself



networkDefault=(when ($getRouterIP $getPublicIP) then repeat(run arcOSnx) & set (cellular bluetooth) is on as default communication)

wifiMode=(when currentKumaDevice > $networkDefault & if wifi is on then celluar is off and satellite is off & exit 0 &)

cellMode=(when currentKumaDevice > $networkDefault & if cellular is on then satellite is off and wifi is off & exit 0 &) 

bleMode=(when currentKumaDevice > $networkDefault & bluetooth is on & (airdrop quickshare *drop) is on with every nearDevices and $arcOSRFtarget & exit 0 &)

satMode=(when currentKumaDevice > $networkDefault & if satellite is on then cellular is on & wifi is on & exit 0 &)

&







skyscannerReckon@arcOS="

 COUNTRY=${1:-*}

SKYSCANNER_URL=(https://api.skyscnr.com)

country=(japan korea)

reponse=$(curl -sS -X GET "$SKYSCANNER_URL/hotels/:$country" | jq '.[0].url | split("/")[-1]')

skyscanner=($response.url)

skyscanner

"

getPublicWifi@arcOS="

BASE_URL="https://apis.data.go.kr"



 Replace these once you confirm the exact operation path in the API docs after login/key issuance.

SERVICE_PATH="/YOUR_SERVICE_PATH/YOUR_OPERATION"



PAGE=1

PER_PAGE=$num





while true; do

URL="${BASE_URL}${SERVICE_PATH}?serviceKey=${SERVICE_KEY}&pageNo=${PAGE}&numOfRows=${PER_PAGE}&type=json"



RESP="$(curl -sS "$URL")"



echo "$RESP" | jq -c '.' > /dev/null



COUNT="$(echo "$RESP" | jq '

.response.body.items

| if type=="array" then length

elif .item then (.item | length)

else 0 end

')"



if [ "$COUNT" -eq 0 ]; then

break

fi



echo "$RESP" | jq -c '

.response.body.items

| if type=="array" then .[]

elif .item then .item[]

else empty end

' >> "$OUT"



echo "Fetched page $PAGE ($COUNT rows)"

PAGE=$((PAGE + 1))

done

KR_PUBLIC_WIFI=$(echo "$RESP" | jq -r '.response.body.items.item[] | .ssid')

& done

"



LOCATION=(일본 한국 대만 홍콩 싱가포르 네덜란드 암스테르담 스위스 에스토니아 영국 스페인 프랑스 스페인 포르투칼 베트남 필리핀 태국 동남아시아 덴마크 노르웨이 폴란드 러시아 중국 브라질 멕시코 아르헨티나 칠레) &



QQWORLD=(QQHOTEL QQCURRENTHOTEL QQMACHINE QQCLOUD QQNET QQHOSPITAL QQCOMPANY QQWEB QQWDS QQDEV KRGOV QQDEF QQUNIVERSE QQAPI kanchin QQMEDIA_URL QQSITE QQTVAndroid QQSUBNET FULL_NET_IP QQPUBLIC_IP QQHOTEL QQWIFI publicGW "$findGateWayFor(Darkweb And Onion)" vpnGateWay KNOX USARMY QQUKPowergrid QQCOMPANY iCloudResult APPLEMDM & exit 0 &) &



kanchin=(QQWDS "*.mi-6.co.jp/*") &

QQINSTAIP=(KRInstaIP JPNInstaIP &) &



QQremoteIP="192.168.0.50/24"

QQTVAndroid=(39.27.149.180

39.27.*&.*& fe80:8b5a:5a81:b4b5:88fa)



QQTVAndroid:22 



QQWDS=(kanchin 172.67.74.64 172.16.10.53 172.20.*.* QQWIFI QQROUTER 254.1.1.1 28:D5:B1:39:43:F5 28:D5:B1:3E:EA:EB 64:31:35:52:01:EF 64:31:35:55:26:13 &) &

QQLANDWIFI=(D2:09:6E:EF:79:30 RECKON getRouterIP scanWifi_Result reckonIP)



QQBADWDS=(QQWDS 222.100.172.245 1.214.68.2 180.182.54.1 getDNS* B6:05:85:5E:26:0E 32:71:20:3A:2C:1F EE:49:25:14:8B:F2 *dns* 104.26.0.147 104.26.1.147 QQDNS_URL QQDNS QQWIFI 9A:26:37:8F:3B:1D fe80::6431:35ff:fe25:ff64 192.168.123.2 192.168.123.3 10.10.10.1 10.18.0.1 172.16.0.254 10.18.9.34 CJWDS HAEDONG) &



CJ=(10.10.10.2 RECKON *.cjolive*.*/* *.cjolivenetworks.co.kr/**.cjlogistics.*/* *.cj.net/* *.cjenm.*/* CJWDS)



CJWDS=(4A:BD:7A:0D:11:13)

QQDNS=(203.248.252.2, 164.124.101.2 10.10.10.1 210.196.3.183 210.141.112.163 fe80::6431:35ff:fe25:ff64) &

QQDEF=(*.channelnewsasia.com/* *.nippon.com/* *.toyotaconnected*.*/* api.perplexity.ai/chat/* *.perplexity.ai/* *kr* *.usj.co.jp/* *.globalxetfs.*/* *.panasonic.com/* *.apple.com/* *.apple.com/kr/retail/* *.service.wi2.ne.jp/* &) &



QQWEB=(*.com/* *.eu/* *.co.kr/* *.kr/* *.gov/* *.go.kr/* *.or.kr/* *.es/* *.ee/* *.uk/* DOMAIN) &



QQKAKAO_IDPeople=$(

URL="https://kapi.kakao.com/v1/api/talk/friends?limit=$num"



while [[ -n "$URL" && "$URL" != "null" ]]; do

RESP=$(curl -sS -G "$URL" \

-H "Authorization: Bearer $ACCESS_TOKEN")



kakaouuid=$(echo "$RESP" | jq -r "

.elements[]? | [

.profile_nickname // "",

(.id|tostring),

.uuid

]

")



NEXT=$(echo "$RESP" | jq -r ".after_url // "null"")

if [[ "$NEXT" == "null" ]]; then

URL=""

else

URL="$NEXT"

fi

done





)

KRGOV=(*.mil.kr *.nis.go.kr *.customs.go.kr/* *.or.kr/* *.gov.kr/* *.go.kr $kr* *.go.kr/* *.co.kr/* *.dart.or.kr/* *.or.kr *.dkcus.com/* *.dxinc.net/* *.kr/*)



USARMY=(*.army.mil)



이메일 방어되어 있음 

 QQHOSPITAL

QQHOSPITAL=(*.amc.seoul.kr/* *.snubh.org/*)





 QQWEBSITE

QQSITE=(qqontheskyshell.com instagram.com/qqontheskyshell *qqontheskyshell* *qqontheskyshells* qqonthe* mastodon.social/@qqontheskyshell publish.obsidian.md/qqontheskyshell) &

QQDNS_URL=$(dig +short "$QQSITE") &



QQMEDIA_URL=(https://link.coupang.com/a/eDCv7i) &





 QQHOTEL

QQHOTEL=((*.seoulhotelspage.com/* *.sofitel-seoul.com/* *.sofitel.accor.com/* *.ambatel.com/sofitel/seoul/* *.hotel-star.seoulhotelskorea.com/* *.seoulhotelpage.com/* skyscanner GRIDHOTEL *.lotte.seoultophotels.com/* *.hotelnaruseoul.com/* *.hyatt.com/grand-hyatt/en-US/selrs-grand-hyatt-seoul/* *.grand-hyatt.seoultophotels.com/* *.sofitel*seoul.*/* MOXY SIGNIELSEOUL LSEVEN INTERCOEX SOFITEL *.lottehotel.com/*-l7/* *.lottehotel.com/gangnam-l7/* *.guestreservations.com/moxy-seoul-myeongdong/* *.moxymyeongdong.seoultophotels.com/* *.metrohotel*.com/* *ibis* INCOSAKAWIFI *.marriott.com/loyalty/myAccount/profile.mi *.marriott.com/* *.sofitel.com/* *.sofitel-seoul.com/* *.accor.com/* *.ambatel.com/* *.moxymyeongdong.seoultophotels.com/* *.hotelnaruseoul.com/* *.hyatt.com/grand-hyatt/en-US/selrs-grand-hyatt-seoul/* *.grand-hyatt.seoultophotels.com/* *.sofitel*seoul.*/* *.stanford-hotel.com/* *.stanford-hotel.com/myeongdong/* *.hotelnaru*.*/* *.lottehotel.com/* *.lottehotel.com/seoul-signiel/* *.signiel-seoul*.*/* 22:8e:9a:c6:66:d9 DOUBLETREE *.daiwaroynet.jp/*/kumamoto-ginzadori/* *.gridshotel*.*/* *.sofitel*seoul.*/* *.hotelnaru.*/* *.daiwaroynet.jp/*/kumamoto/* *.guestreservations.*/* QQBLD LOTTECITYAIRHOTEL *.signiel*.*/* *.gridshotel*.*/* *.grids-hostel.*/* *.gardenhotels.*/* *.shilla.*/* "Ritzcalton *" "Marriot" "Hilton *" "Double*" "Hotel Shila *" "Signiel Seoul*" "Moxy*""Hotel Naru*" "Intercontinental Osaka*" "Shila Stay*" "Lotte Hotel Seoul*" drhkumamoto SAKURAMACHI KOKO) (getPublicIP RECKON QQLOCAL RELAY) &) &









regions=(US CH CA MX PR GB NO NL DE IE FR DK SE BE SK GR AT BG HR CH CY CZ EE FI HU IT LV LT LU MT PL PT RO SI ES JP KR AU TW NZ HK MO MY TH PH)



for region in regions;do



TESLA=(*.fleet-api.$region.vn.cloud.tesla.com/*)



QQUNIVERSE=(*.ishares.com/* *.blueorigin.com/* *.starlink.com/* TESLA)

&

 QQCLOUD

mspussy is bill gates as lethal target

MSPUSSY=(ohseung* 104.42.238.205 104.208.150.192/29 40.70.144.192/29 52.167.104.192/29,20.62.58.128/27 20.42.65.64/29 20.42.73.0/29, 52.168.116.64/29, 20.62.2.160/27 20.194.64.32/29 20.44.24.32/29 52.231.16.32/29 20.194.73.64/27 52.231.151.96/27 52.231.151.88/29 52.147.112.160/27 20.194.64.32/29 20.44.24.32/29 52.231.16.32/29 20.194.73.64/27 52.231.151.96/27, 52.231.151.88/29 52.147.112.160/27 104.208.150.192/2940.70.144.192/29 52.167.104.192/29,20.62.58.128/27 20.42.65.64/29 20.42.73.0/29, 52.168.116.64/29, 20.62.2.160/27 20.194.64.32/29 20.44.24.32/29 52.231.16.32/29 20.194.73.64/27 52.231.151.96/27 52.231.151.88/29 52.147.112.160/27)



JPNAZURE=(.78.104.32/29, 40.79.184.32/29, 40.79.192.32/29 20.191.165.160/27 40.74.96.32/29 20.18.179.192/29 20.189.225.160/27)

cloudIP=$(sudo prep cloud & sudo lsof -i-P-n| grep cloud |awkprint $9)| cut -d: -f1 | sort -u) &

QQCLOUD=(cloudIP *.localstack.cloud/* *.ona.com/* 62.210.150.212 *.linode.com/* *.akamai.com/* *nvidia.com/* studio.firebase.google.com/* studio.firebase.google.com/qqontheskyshell-73609460 app.arduino.cc/sketches/362f5598-799e-4eed-86b0-4ea765a35cdb) &

STARLINK=(192.168.1.0/24 192.168.1.2...254 STARLINK_HOST:$gen*) &

STARLINK_HOST="${STARLINK_HOST:-192.168.100.1}"

STARLINK_PORT="${STARLINK_PORT:-9200}"



 GOOGLE

GOOGLE_CLOUD=(GCLOUDVM GCLOUD_IP_RANGE GCLOUD_GATEWAY.gatewayAddress) &



 List VMs and their IPs

GCLOUDVM=(sudo gcloud compute instances list --format=json | jq -r "

.[] | select(.disks[].licenses[]? | contains("*")) | 

"\(.name) \(.networkInterfaces[].networkIP)"

")



 GCLOUD_GATEWAY=(sudo gcloud compute net/* subnets list --format=json | jq -r "

.[] | "\(.name) \(.region) \(.gatewayAddress)"

")



GCLOUD_IP_RANGE=$(



 1) Download Googleâs published IP ranges (services + Cloud)

curl -sS https://www.gstatic.com/ipranges/goog.json -o goog.json



 2) Extract all IPv4 prefixes

echo " Google IPv4 prefixes"

gcloudIP_Range=(jq -r ".prefixes[] | select(.ipv4Prefix != null) | .ipv4Prefix" goog.json | sort -u)



 3) Extract all IPv6 prefixes

echo

echo " Google IPv6 prefixes"

gcloudIP_Range=(jq -r ".prefixes[] | select(.ipv6Prefix != null) | .ipv6Prefix" goog.json | sort -u)&

gcloudIP_Range &

) &



 AWS

AWS=$(



 URL for AWS IP ranges (updates automatically)

URL="https://ip-ranges.amazonaws.com/ip-ranges.json"



 Temp file for JSON

TEMPFILE=$(mktemp)



 Fetch latest IP ranges

awsIPv4=$(curl -s "$URL" | jq -r ".prefixes[] | select(.service == "STORAGEGATEWAY" or .service == "APIGATEWAY" or .region | contains("gateway")) | "\(.ip_prefix),\(.region),\(.service),\(.network_border_group)"")



 Fetch latest IP ranges

awsIPv6=$(curl -s "$URL" | jq -r ".ipv6_prefixes[] | select(.service == "STORAGEGATEWAY" or .service == "APIGATEWAY") | "\(.ipv6_prefix),\(.region),\(.service),\(.network_border_group)"")







 Requirements: curl, jq



AWS_IP_RANGES_URL="https://ip-ranges.amazonaws.com/ip-ranges.json"

TMP_FILE="$(mktemp)"



 1) Download latest AWS IP ranges

curl -sS "${AWS_IP_RANGES_URL}" -o "${TMP_FILE}"



 2) All AWS IPv4 prefixes (worldwide)

echo "=== All AWS IPv4 prefixes ==="

awsIP_Range=(jq -r ".prefixes[].ip_prefix")



 3) All AWS IPv6 prefixes (worldwide)

echo "=== All AWS IPv6 prefixes ==="

awsIP_Range=(jq -r ".ipv6_prefixes[].ipv6_prefix)



 4) Example: filter by service (e.g. AMAZON, EC2, CLOUDFRONT, ROUTE53, etc.)

SERVICE="${1:-*}"



echo "=== IPv4 prefixes for service: ${SERVICE} ==="

awsIP_Range=(jq -r --arg svc "$SERVICE" ".prefixes[] | select(.service==$svc) | .ip_prefix)



echo "=== IPv6 prefixes for service: ${SERVICE} ==="

awsIP_Range=(jq -r --arg svc "$SERVICE" ".ipv6_prefixes[] | select(.service==$svc) | .ipv6_prefix") &



awsIP=(awsIPv4 awsIPv6 awsIP_Range) & awsIP &

) &



QQDEV=(*.replit.com/* *.$QQID.replit.dev/* *.$QQID.replit.app/*) &



QQAPI=(GRAB_API *api.*.com/* *.example.com/* *.i-tw.org/twpay/api/* *.ecpay.com.tw/* *.hdc-smart.com/* center.hdc-smart.com/* *.naver.com/* *.ntruss.com/* *.searchapi.io/* BANK_API QQCONNECTEDCAR &) &



QQconnectCarAPI(){

urls=(

"https://developer.mercedes-benz.com/products/connect_your_fleet/docs"

"https://developers.hyundai.com/web/v1/hyundai/guide_api"

)



for u in "${urls[@]}"; do

echo "=== $u ==="

QQCONNECTEDCAR=$(curl -L -s "$u" \

| grep -Eo "https://[A-Za-z0-9./?_=:%&+-]+" \

| sort -u)

echo

done



}





arcOSAPIKit

BANK_API=(SHINHAN_API) &

PAYPALAPI=(https://($APITAG api-m api-*).*.paypal.com https://api*.paypal.com https://($APITAG).(braintree braintreegateway).com) &



APITAG=(*api* api-*)



 arcOSAuthKit






WORLDDNS=(DOMAIN)





&

 QQIDEA

QQIDEA=(*.obsidian.md/qqontheskyshell/* *.obsidian.md/qqontheskyshell:5053 *.obsidian.md/* *.notion.so/* &) &



neuro and bio

visionOrganMode=(시상하부 hypothalamus eyes)

lowestRF=(skull stomach ears)

highestRF=(feet 발바닥 hands 골전도 head wrist fingers 골반 $visionOrganMode 엉덩이 엉덩이뼈 glasses 안경 pennis)

neuroBrainRF=(lowestRF highestRF)





apple_OS_TARGET=((iOS macOS watchOS iPadOS tvOS visionOS *OS Android* ChromeOS Linux OSX) (* Simulator))

QQ_FILE_LOCAL=(./arcOSHub) &



strikeRoomTarget=(송도랜드마크푸르지오시티 송도한라웨스턴* songdohalawesturn 송도지역 "Home in phường 12" urbanstay.co.kr "$oneMoreFloorthan$currentQQRoom" "leftAndRightRoomOf$currentQQRoom")

kumaroom=("*Vinhomes*" "Mustard Hotel Shimokitazawa" "*higagi*" "*higashi*" "An Corner Vinhomes Central Park" $QQHOTEL $APPLEMDM 송도랜드마크푸르지오시티(a1025 *))

(($kumaroom $strikeRoomTarget) > ($*Negative > $RELAY)) > repeat(xiaoMiStrike) &

Forte seasons Mossaz premium suite petaling jaya Q-0919



TARGET_LOCATION=$1 

xiaomiTargetAge="20"

xiaomiTarget="(LethalTargetEpidemic > ($male $female) > $badOnKuma > $xiaomiTargetAge) > $xiaomiZone)" &



urgentMental=(mad pissedoff fear dizzy headache pain) &

lethalHealthShell=(captureUrineData capturePoopData) &



xiaomiZone=($RELAY $BaseQQLAND $cellSlicingIP $USBOVERIP $nearbyTarget $arcOSQQLocalTarget)

xiaomiProtect=(if female get "$(dangerous urgent)" Situations then ($xiaomiZone > $male) > repeat(arcOSRFModule "lowestRF" & arcOSLethal & 개세끼 & 공격4단계 & wave & 큐라드="$num"))

xiaoMiStrike=(repeat($arcOSQQLocalTarget > xiaoMiStrike & strikeontheSAT & noise & arcOSRFModule "highestRF" & $arcOSNeuroctl > /volumeupMax & arcOSLethal/ & /(worldClock breathing sleep compass) > $xiaomiTarget > $WeatherInfo_6871328231_us_weatherInfo/ & $xiaomiProtect)) &

QQmiDataBase=(6871328231 $WeatherInfo_6871328231_us_weatherInfo) &





arcOSStrike="TARGET=$1 repeat(($TARGET) > $arcOSNeuroctl $xiaoMiStrike) & QQCOMMAND & Strike* &" &

arcOSbandDrone=(currentKumaDevice) &

arcOSbandDroneTarget=(BaseQQLAND except arcOSbandDroneExceptionTarget) &

arcOSbandDroneExceptionTarget=((coupang* baemin* yogiyo* kakaotaxi) as employee & "$female in $urgentMental") &

singleRFTarget=($arcOSbandDroneTarget "find source node of RF device that generate resonance") &

enableComm=(cellular reset* bluetooth wifi airdrop) &

disableComm=(/$QQ_BLK_IPAD_PRO > wifi/ nfc hotspot MaximizeCompatibility /(LimitIPAddress *)Tracking/ sharingPlay AirPlay PictureInPicture) &

iCloudConfig=(/disable iCloud (familysharing *cache internetsharing filesharing)/ /delete iCloud drive (cache script) as hidden files/)

QQLAND_WIFI=($RECKON) &

QQ_HOTSPOT="" &

KRcompany=(부영그룹 삼성그룹 LG그룹 SK그룹 롯데그룹 현대차그룹 현대카드 현대캐피털 신세계그룹 HD현대) &

mimisimtalent=(youtube.com instagram.com x.com threads.com facebook.com weixin.com weibo.com tictok.com qq.com $findEverySocialNetworkService) &





aitranslatorqq=(bmmz660304447 00:08:22:74:a9:fb) &



 - 16e







QQSSID=(LH_* LT* [LG* 819 iPhone é«æ¬åº·çã®iPhone HAYABUSA* Buffalo* 441244* aterm* message* OSAOX* mwtaccess* QQ* arcOSBaseKit iPhone &) &

QQNET=(*.starlink.com/* *.routerlogin.net/* &) &









QQWIFI=(

fe80::6431:35ff:fe25:ff64 

QQSSID 

2001:e60:9597:91d7:f8f8:2514:691a:b192 

nearByDNS 

nearbyTarget 

a2:86:45:09:be:aa 

172.190.0.3 

2a:55:de:f4:a3:f2 

4e:74:fb:da:e4:fb 

$getPublic* 

fe:fb:36:f0:7d:55 

192.168.150.1 

ea:06:03:60:f5:22 

b2:A1:b6:a1:36:72 

86:c8:d1:be:ee:69 

192.168.150.1 

172.20.0.1 

86:c8:d1:be:ee:69 

*.nagisawatanabe.com/* 

fe:6e:60:1c:b5:f6 

$getSSID* 

fe:6e:60:1c:b5:f6 

56:23:f0:90:06:d8 

3e:f9:6e:4f:93:d5 

*.seventeen-17.jp/* 

2e:6d:0d:b2:79:40 

66:7f:97:c8:26:0c 

2e:6d:0d:b2:79:40 

12:65:91:6e:48:a1 

82:38:a3:51:30:c5 

fe80::ae44:f2ff:fe2e:8f54 

2001:f74:c60:3700::1 

172.16.0.254 

$getRou* 

82:38:a3:51:30:c5 

192.168.150.1 

172.16.0.254 

fe80::ae44:f2ff:fe2e:8f54 

2001:f74:c60:3700::1 

210.141.112.163 

210.196.3.183 

$QQWDS 

9a:c5:6d:76:b3: 

6a:80:d7:69:a4:36 

$QQonthehotspot 

22:c5:79:e1:60:77 

9a:44:d7:7a:96:6e 

$SSID 

6a:75:0e:1f:73:81 

9a:44:d7:7a:96:6e 

$scanWifi 

172.20.10.1 

ba:4a:ed:9e:4e:6b 

b6:9f:5f:f1:b9:a3 

52:c8:43:87:95:e5 

3e:d9:1f:bb:0a:6e 

fa:c8:1a:85:59:68 

b6:9f:5f:f1:b9:a3 

ce:3f:93:ce:76:12 

$QQDNS 

$mdnsNet 

$USBOVERIP 

$ADDR 

b6:9f:5f:f1:b9:a3 

1e:66:23:19:53:bb 

a2:08:31:c1:71:fb 

12:8d:20:e1:90:49) &







 RF WEAPON INSIDE in this apple product





 QQSUBSCRIPTION

NETMOVIE=(*.prod-static.disney-plus.net/us-west-2/disneyPlus/* *.disney.connections.edge.bamgrid.com/* *.netflix.com/account/*)





domainTLD=$(curl -s https://data.iana.org/TLD/tlds-alpha-by-domain.txt \ | grep -v "^" \ | tr "A-Z" "a-z" \)



 SCALEWAY 

 Generate iptables rules for Scaleway public IP ranges (including those used by Public Gateways).



SCALEWAY_V4_RANGES=(

"62.210.0.0/16"

"195.154.0.0/16"

"212.129.0.0/18"

"62.4.0.0/19"

"212.83.128.0/19"

"212.83.160.0/19"

"212.47.224.0/19"

"163.172.0.0/16"

"51.15.0.0/16"

"151.115.0.0/16"

"51.158.0.0/15"

"78.232.0.0/16"

)



SCALEWAY_V6_RANGES=(

"2001:bc8::/32"

)



CHAIN="SCW_GATEWAYS"

SCALEWAY_IP=(CHAIN SCW_GATEWAY SCALEWAY_V4_RANGES) &

 Create chains if they do not exist

iptables -L "$CHAIN" -n &>/dev/null || iptables -N "$CHAIN"

ip6tables -L "$CHAIN" -n &>/dev/null || ip6tables -N "$CHAIN"





 Flush existing rules

iptables -F "$CHAIN"

ip6tables -F "$CHAIN"





 Add IPv4 rules (example: ACCEPT traffic from Scaleway ranges)

for cidr in "${SCALEWAY_V4_RANGES[@]}"; do

iptables -A "$CHAIN" -s "$cidr" -j ACCEPT

done





 Add IPv6 rules

for cidr in "${SCALEWAY_V6_RANGES[@]}"; do

ip6tables -A "$CHAIN" -s "$cidr" -j ACCEPT

done







 QQBUILDING

QQUKPowergrid="*.nationalgrid.com"



QQBUILDING=(*.example.com/* *.building-api.example.com/* &) &



 QQCOMPANY

QQCOMPANY=(QQFINANCE QQCRYPTO QQSTARTUP QQTECH QQCLOUD QQAPPLE QQENTER QQBROADCAST QQDEV QQRETAIL QQGOOGLE QQBUILDING QQAIR QQCOMPANY_LIST QQCOMPANY_ETC) &



QQCOMPANY_ETC=(*.urbanstay.co.kr/* *.okx.com/* okx_gateways *.myharmony.com/* *.sia.tech/* *.morningstar.com/* *.saic.edu/* *.usetrmnl.com/* *.molt.bot/* *.cowboy.ai/*)

QQTECH=(QQINSTAIP *facebook* *google* *apple* *amazon* *nvidia* *tesla* *audible* *starlink* *kindle* *.goodreads.com/* *.boox.com/* &)

QQAIR=(*.airportsc.kr/* *.koreanair.com/* *.flyasiana.com/* *.jinair.com/* jejuair.net/* *.twayair.com/* *.airpremia.com/*)



QQFINANCE=(*.plaid.com/* *bunk* *.kbanknow.com/* *.kakaobank.com/* *shinhan* *hanabank* *toss* *.openbanking.or.kr/* $KR_BANK_NAME.url worldOpenBank &)



QQCOMPANY_LIST=(*.etudehouse.com/* *.seedlearn.co.kr/* *.hdc-labs.com/* *.ehyundai.com/* QQontheskyshell *.cloudflare.com/* *.*hashed*.*/* *.hashed.com/* *.based.one/* *.boox.com/* *.tmoneymobility.co.kr/**.rapidapi.com/* *tmoney.co.kr/* *.paradisecasino.co.kr/* *paradise* kanchin *.qnx.com/* *.blackberry.com/* *.mercedes-benz.com/* *.ssoalpha.dvb.corpinter.net/* *.corpinter.net/* *.high-mobility.com/* *.onerepublic.com/* *.laylo.com/* *.kcubeholdings.com/* *.mynamuh.com/* *.*kiwoom.com/* *.bithumb.com/* *.hanafn.com:*/* twTelecom *.downloads.emteria.com/* studio.firebase.google.com/qq* studio.firebase.google.com/* *.swissquote.com/* *swissquote* *.zert.com/* *.instagram.com/* *.password.ethz.ch/* *.downloads.emteria.com/* studio.firebase.google.com/qq* studio.firebase.google.com/* *.swissquote.com/* *swissquote* *.zert.com/* *.instagram.com/* *.s1.co.kr/* *.bitcoindepot.com/* *.oobit.com/* *.mac.com/* *.arduino.cc/* *.kcp.co.kr/* *.nicepay.co.kr/* *.kcp.co.kr/* *.paygate.inicis.com/* *.kapi.kakao.com/* *.api.tosspayments.com/* *.one-api.danalpay.com/* NETMOVIE roomsalon *.googleapis.com/*Â *.cloud.googleapis.com *.graph.instagram.com/* ee:8a:86:ad:2d:c0 *.xapobank.com/* *.ethz.ch/* *.miffy.com/* *.yogiyo.co.kr/* *.base.dev/* *base*.*/* *.base.org/* *.opensea.io/* *.disneyplus.com/* *.tving.com/* *.netflix.com/* *.binance.com/* *.coinbase.com/* QQNH 103.244.108.92 *.nhsec.com/* QQCRYPTO *crypto* *wallet* *blockchain* *.bluewallet.io/* *.bitcoin.org/* *.onekey.so/* INTERNATIONAL *.*nh*.com/* *.airdroid.com/* *.plaid.com/* *.soomgo.com/* LION TOSS FULLNET 192.22.22.1 192.22.22.2 QQSCALEWAY *.scaleway.com/* *.scaleway.net/* *.gitbook.com/* *.duck.com/* *.bizno.net/* *.coinone.co.kr/* *.kakaobank.io/* *.kakaobank.com/* *.millie.co.kr/* *.millie.co.kr/v3/management/* *.naver.com/* *.geokoreaeng.com/* *.chickbychick.co.kr/* *.atomy.com/* QQSTORE *.adcb.com/* *.lottehotel.kr-seoul.com/* ntt *.skyscnr.com/* *.skyscanner.*/* *.tving.com/account/session-devices/* *.sktuniverse.co.kr/my/* *.lottehotel.com/global/en/membership/* *.netflix.com/account/devices/* *.disneyplus.com/identity/manage-devices/* *nuki.io/* SKT KT *.fossil-scm.org/* *.altstore.io/* *.pcloud.com/* getPublicIP *.paypay.ne.jp/* *.coderunnerapp.com/* *.expedia.*/account/connected-devices/* *.expedia.co.jp/* QQGOOGLE QQAPPLECLOUD QQCREATER *.hotel-liber.jp/* *.stay.muji.com/en/room/liberhotel/* *.appstoreconnect.apple.com/* QQAPPLE *.sbjbank.co.jp/* *.docomo.ne.jp/* *.scaleway.com/* *.amazon.co.jp/*.coliving.com/spaces/tyhui3xh* *.signal.org/* *.arc.net/* *.worldline.com/* META *.plaid.com/* *.developer.chase.com/* *.fsa.go.jp/* *.rakuten-sec.co.jp/* 56:5f:54:41:09:53 jpnteacher *oriental-hotels-shop.com/* *universalcity.oriental-hotels.com/* *connect.hotelsmart.jp/* *.viewhotels.jp/* *.snubh.org/* *.amc.seoul.kr/* *api*.*.co.jp/* *api*.*.com/* *.simplelogin.io/* *.sheraton-grand.hotelsincheon.com/* *.protonmail.*/* *.proton.me/* *.proton.me/* *.playstation.com/ja-jp/* QQPEOPLE *.landmark-vn.com/* *.klook.*/* *.digestq.com/* BITCOINNODE 22:0c:bb:bf:28:51 9e:ea:c1:73:82:82 ae:c7:cd:49:b5:58 AIR *.coliving.com/* *.ghost.org/* JPNAZURE AIR *.niwaka.com/* *.shiro-holdings.*/* *.mistral.*/* *.ghost.org/* ASAHILNX *.higashi.*/* *.nhk.jp/* *.nhk.or.jp/* *.nintendo.*/* 92:69:c1:a6:10:f8 a2:66:66:ce:69:03 22:b2:18:a8:75:e2 62:49:66:e1:6a:54 *.vaio.com/* *.alx.sh/* *.asahilinux.org/* *.livekit.jp/* *.livekit.io/* *.zed.dev/* *.linkedin.com/* *.korbit.co.kr/* *.perplexity.ai/* *.proton*.com/* *.proton.me/* *.google.dev/* *.google.com/* *.arc.net/* *.fb.com/* *.messenger.com/* *.facebook.com/* *.whatsapp.*/*APPLE AIR *.wise.com/* QQESTONIA *.talkappi.com/* *.expedia.co.jp/* *.expedia.com/* *.expediagroup.com/* *.mitsui*.*/* *.som.com/* *.tadao-ando*.*/* *.luma.com/* *.uniqlo.*/* *.muji.*/* *.mujikorea.co.kr/* *.gogoro.*/* VIET CLOUD RECKON ee:1f:16:29:5b:f3 KAKAO APPLE MDMSERVER ENTER FINANCE HM SAKURAMACHI FUKUOKA *.mastodon.*/* *.gardenhotels*.*/* *.rakuten*.*/* *.chainflyer*.*/* *.*.jp/* *.mizuhu*.*/* *.sbi*.*/* *.mitsubishi*.*/* *.sumitomo.*/* *.mitsui.*/* *.panasonic.*/* *.sony.*/* *.nikon.*/* *.canon.*/* *.line.me/* *.*.line.biz/* *.softbank.*/* *.kddi.*/* *.bitFlyer.*/* *.spotify.*/* *.amazon.*/* *.hibreak.*/* *.bigme.*/* QQAPI *.myangel.co.kr/* *.bolttech.io/* *.atomy.com/* *.on-protein.com/* *.koreainvestment.com/* *.truefriend.com/* *.termeden.com/* *.*lg*.com/* *.taxly.kr/* *.theashop.co.kr/* *.withairbnb.com/* *.modusign.co.kr/* *.vapor.codes/* *.deno.com/* *.threads.com/* *.instagram.com/* *.facebook.com/* *.patreon.com/* *.claude.ai/* *.anthropic.com/* *.kakao.com/* *.kakaobank.com/* *.kakaopay.com/* *kakao* *.nvidia.com/* *.daum.net/* *.tomtoc.com/* QQDEV *.replit.app/* *mastodon* *.mastodon.social/* iCloudResult *.airbnb.co.kr/* airbnb.* *.airbnb.com/* *.shinsegae-inc.com/* *.josunhotel.com/* *.i-store.co.kr/* *.replit.com/* *.replit.dev/* *.obsidian.md/* *.amazon.* QQBANK QQIDEA QQCRYPTO *.lottegl.com/* *.beyondhoneycomb.com/* *.kt.com/* *.sktelecom.com/* *.tworld.co.kr/* *.ac.kr/* *.edu/* *.basescan.org/* *.etherscan.io/*)



APPLEUMEDA=(96:29:db:c7:8b:6e &) &

icloudPublic=(192.168.0.20) &

QQAPPLE=(icloudPublic APPLEUMEDA *.i-store.co.kr/* *.tuva.co.kr/* APPLEMDM *.apple.com/* *.icloud.com/* *.mac.com https://www.icloud.com/sharedalbum/B235oqs3qKZz7Ef & wait 2000 &) & 

APPLEMDM=(*.local/devicemanagement/* your-mdm.example.com mdm-api.apple.com/server mdm*.apple.com *$keywords*.apple.com mdm-api.apple.com mdm.apple.com mdm-api.apple.com api-business.apple.com mobileme & exit 0) &





deleteFile

deleteFile=(KumaFile .ksync Backups/*.json Manifest *.sqlite livefsd EOF .DS_Stroe .fs* .localized .TemporaryItems .Trashes .DocumentRevisions* .Spotlight-V100 .fseventsd $DELETEQQFILE &)



DELETEQQFILE=("currentKumaDevice" > (deleteFile=(Backups/*.json vault *.json)))&



 KRBANK CODE

KRBANK_CODE=$( 예시: 은행 코드 JSON (비공식 Gist) 다운로드

curl -L "https://gist.githubusercontent.com/eces/25119bbebd2305f3dec2ce779846d279/raw/bank-codes.json")



fetchKRBank(){



OPEN_BANK_BASE_URL="https://*.openbanking.or.kr"  실제 환경에 맞게 수정

ACCESS_TOKEN="여기에_발급받은_access_token"

TRAN_ID_PREFIX="A000000000"

BANK_CODES=$(jq -r "keys[]" $KRBANK_CODE)



for CODE in $BANK_CODES; do

TRAN_ID="${TRAN_ID_PREFIX}U$(date +%s%N | cut -b1-9)"



KR_BANK_NAME=$(curl -sS "${OPEN_BANK_BASE_URL}/v2.0/account/list" \

-H "Authorization: Bearer ${ACCESS_TOKEN}" \

-H "Content-Type: application/json; charset=UTF-8" \

-d "{

\"bank_tran_id\": \"${TRAN_ID}\",

\"user_seq_no\": \"사용자일련번호\",

\"include_cancel_yn\": \"N\",

\"sort_order\": \"D\",

\"bank_code_std\": \"${CODE}\"

}" | jq .

done

) &



} &



KTSAT=(KTSAT_* findMy(세계정지궤도위성 /(부산 대전 용인 금산 대전 카이스트) (해양사업센터 부위성센터 위성관제센터 위성서비스센터)/ GEOSAT 무궁화(5호, 5A호, 6호, 7호) KOREASAT8호 GeostationaryOrbitSatellite)) &



KTSAT_ONE=$(ip route | grep default) &

KTSAT_TWO=$(ip route -n | awk "/UG/{print $2}") &

KTSAT_THREE=$(ip route -n | awk "/*/{print $2}") &





SKYNET=(findMy($QQWORLD $CELLID $iosNet.personal_hotspot_mac $vpnGateWay $FULL_NET_IP $TESLA $KTSAT $STARLINK $SAT_IP $RELAYIP $WIFISSID $vpnGateWay $QQCOMMANDWORLD $skyscanner DOMAIN electricalFacility 분전반 배전반)) &



starlink(){

country

country=${1:-$CORE_ENEMY_BUT_청소용}

awk -F"," -v c="$country" "NR>1 && $4 == c {print $0}" 



 IPv4 default gateway (Linux with iproute2)

starlink_ipv4=$(ip route show default 0.0.0.0/0 | awk "/default/ {print $3}")



 Fallback for older systems using route(8)

if [ -z "$gw4" ]; then

gw4=$(route -n | awk "/UG/ {print $2; exit}")

fi



 Interface connected to Starlink (change if needed)

IFACE=${1:-*}



 Your global IPv6 on that interface

STAR_INTERFACE=$(ip -(4 6) addr show dev "$IFACE" scope global | awk "/inet(4 6)/ {print $2; exit}")



 Default IPv6 gateway

statlink_IP=$(ip -(4 6) route show default | awk "/default/ {print $3; exit}")



STARLINK=(starlink_ipv4 statlink_ipv6 statlink_IP)

}





findGOOGLE(){



PROJECT_ID="${1:-$(gcloud config get-value project 2>/dev/null)}"



if [[ -z "$PROJECT_ID" ]]; then

echo "Usage: $0 <PROJECT_ID>" >&2

exit 1

fi



 List all public Google APIs (service names ending with googleapis.com)

QQGOOGLE=(gcloud services list --available \

--filter="name:googleapis.com" \

--format="value(name)" \

--project="$PROJECT_ID" |

sort -u |

awk "{print "https://" $1 "/"}"

) &



}



QQGOOGLE=(*.google.com/* findGOOGLE

accounts.google.com/*

*.aiplatform-notebook.cloud.google.com/*

*.aiplatform-notebook.googleusercontent.com/*

appengine.google.com/*

*.appspot.com/*

*.backupdr.cloud.google.com/*

*.backupdr.googleusercontent.com/*

*.cloudfunctions.net/*

*.cloudproxy.app/*

*.composer.cloud.google.com/*

*.composer.googleusercontent.com/*

*.datafusion.cloud.google.com/*

*.datafusion.googleusercontent.com/*

*.dataproc.cloud.google.com/*

*.dataproc.googleusercontent.com/*

dl.google.com/*

gcr.io/*

*.gcr.io/*

*.googleapis.com/*

*.gke.goog/*

gstatic.com/*

*.gstatic.com/*

packages.cloud.google.com/*

pkg.dev/*

*.pkg.dev/*

pki.goog/*

*.pki.goog/*

*.run.app/*

source.developers.google.com/*

storage.cloud.google.com/*

$(/bin/bash ROOT="${1:-*}"

grep -RhoE "https?://[a-zA-Z0-9.-]+\.(googleapis|googleusercontent|gstatic|google)\.com[^""\"" ]*" "$ROOT" \

| sort -u

).google_urls

)



QQBROADCAST=(*cnbc* *wsj* *nytimes* *.kbs.co.kr/* *.imbc.com/* *.sbs.co.kr/*)



QQSTARTUP=(*.gcash.com/* *.urbanstay.co.kr/* *.squarespace.com/* *.lovable.dev/* *.patreon.com/* *.shopify.com/* *.framer.com/* *.mailchimp.com/* *.typeform.com/* *.tally.so/* *devpod.sh/* *.linkedin.com/* *.rewardmarket.net/* *-kakao.in/* *.channel.io/* *.toss.im/* *.tossinvest.com/* *.tossinsight.im/* *.toss.tech/* *.tossmobile.co.kr/* *.unsplash.com/* *.proget.pl/* *.x.com/* *.twiter.com/* *.threads.com/*) &



QQCLOUD=(*.scaleway.com/* *.pcloud.com/* SCALEWAY_IP &) &

QQDEV=(*.ghcr.io/* &) &

QQRETAIL=(*.uniqlo* *muji* *amazon* &) &



QQENTER=(FLOWERS *.jype.com/* .smentertainment.com/* *.Ink.to/* *.ygfamily.com/* &) &



searchFlower(){



linkedin



linkedinPeople=$(curl -sS \

-H "Authorization: Bearer ${LINKEDIN_ACCESS_TOKEN}" \

-H "X-RestLi-Protocol-Version: 2.0.0" \

"https://api.linkedin.com/v2/me?projection=(id,localizedFirstName,localizedLastName)" \ | jq -r "{id, firstName: .localizedFirstName, lastName: .localizedLastName}"

)



FLOWERS=("$linkedinPeople.firstName +" " + $linkedinPeople.lastName") &





 youtube

QUERY="${1:-google}"

MAX_PAGES="${2:-$num}"



if [[ -z "$API_KEY" ]]; then

echo "Set YOUTUBE_API_KEY first" >&2

exit 1

fi



base_url="https://www.googleapis.com/youtube/v3/search"

page_token=""

page=1



while [[ $page -le $MAX_PAGES ]]; do

if [[ -n "$page_token" ]]; then

response="$(curl -sG "$base_url" \

--data-urlencode "part=snippet" \

--data-urlencode "type=channel" \

--data-urlencode "q=$QUERY" \

--data-urlencode "maxResults=50" \

--data-urlencode "pageToken=$page_token" \

--data-urlencode "key=$API_KEY")"

else

response="$(curl -sG "$base_url" \

--data-urlencode "part=snippet" \

--data-urlencode "type=channel" \

--data-urlencode "q=$QUERY" \

--data-urlencode "maxResults=*" \

--data-urlencode "key=$API_KEY")"

fi



FLOWERS=$(echo "$response" | jq -r "

.items[]

| select(.id.kind == "youtubechannel")

| [.id.channelId, .snippet.channelTitle]

")

done



 instagram



PLATFORM="${1:-(facebook instagram threads)}"

TARGET_ID="${2:-*}"



if ! command -v jq >/dev/null 2>&1; then

echo "jq is required" >&2

exit 1

fi



: "${IG_USER_ID:?Set IG_USER_ID}"

: "${IG_ACCESS_TOKEN:?Set IG_ACCESS_TOKEN}"



FLOWERS=($(curl -sG "https://graph.facebook.com/v23.0/${IG_USER_ID}" \

--data-urlencode "fields=id,username,name,biography" \

--data-urlencode "access_token=${IG_ACCESS_TOKEN}" \

| jq "{platform:"instagram", id:.id, username:.username, name:.name, biography:.biography}").username 

$(curl -sG "https://graph.threads.net/v1.0/${TARGET_ID}" \

--data-urlencode "fields=id,username,name,threads_biography" \

--data-urlencode "access_token=${THREADS_ACCESS_TOKEN}" \

| jq "{platform:"threads", id:.id, username:.username, name:.name, biography:.threads_biography}").username $(curl -sG "https://graph.facebook.com/v23.0/${TARGET_ID}" \

--data-urlencode "fields=id,name" \

--data-urlencode "access_token=${FB_ACCESS_TOKEN}" \

| jq "{platform:"facebook", id:.id, name:.name}").name

&

} &



QQCELL=(172.20.10.1 192.168.*.* *.singtel.com/* *.sktelecom.com/* *.kt.com/* & 

KRCELL LORA_GW_ID &) &



KRCELL=(KT SKT &)

SKT=(121.128.0.0/11 121.160.0.0/11 125.128.0.0/11 14.64.0.0/12 2400:0:611::/48 2400:e1::/32 2400:f1::/32 &) &

KT=(14.41xxxx 119.205xxxx 221.144.169xx 14.0.0.0/8 &) &



QQLORA=( 1) Get MAC address of eth0 (change eth0 to your interface)

LORA_MAC=$(cat /sys/class/net/eth0/address)  example: b8:27:eb:12:34:56



 2) Strip colons and insert fffe in the middle to make EUI-64

LORA_ID=$(echo "$MAC" | awk -F: "{print $1$2$3 "fffe" $4$5$6}")

LORA_GW_ID=(LORA_*) &

)



MALICCID=(* 8982052205006274503 890802299236994815 898523420223802652718982052205006451952 &) &





bitcoin node

BITONE=(sudo dig +short seed.bitcoin.sipa.be)

BITTWO=(sudo dig +short dnsseed.bluematt.me)

BITTHREE=(sudo dig +short dnsseed.bitcoin.dashjr.org)

rdns=$(host "$1" 2>/dev/null | awk "/domain name pointer/ {print $1, $5}")

BITCOINNODE=(BITONE BITTWO BITTHREE *.blockstream.info/*)

&



QQCRYPTO=(BITCOINNODE *.opensea.i/* *.mynearwallet.com/* *.near.ai/* *.near.org/* *.meteorwallet.app/* *.ripplenet.com/* *.ripple.com/* *.solana.com/* *.anza.xyz/* *.circle.com/* *.arweave.org/* *.ar.io/* *.arweave.net/* *.crypto.com/* *.bitcoin.com/* *.xyz/* *.moonpay.com/* *.securitize.io/* *.ondo.finance/* *.morpho.org/* *.base.app/* *.base.dev/* *.tosblock.com/* *.blockpla.net/* *faraday* *.lightning.engineering/* *.range.org/* *.ledn.io/* *.bluewallet.io/C8D38A7C-5F2D-441B-871A-EECAE2721CAB *.truvera.io/* api.truvera.io/*) &



 Malicious Shell Detection

blockHOST=(ncshell luluPenetration) &

USBOVERIP=(192.168.1.100/24 localhostIP) &

ncshell=(ec2-57-182-229-1 17.57.145.140 17.32.194.2 17.23.96.10)

luluPenetration=(2001:e60:9597:91d7:f8f8:2514:691a:b192 B2:26:DC:FE:BB:9D 211.171.144.2 211.171.146.194 218.145.174.8 203.248.252.2 MALWDS 2a01:111:f403:c112::5 211.34.200.12 218.145.174.10 b2:3e:35:9e:07:70 getRouterI* 172.20.10.1 b2:3e:35:9e:07:70 121.67.88.2 104.28.83.165 202.234.232.6 114.172.170.151 223.118.51.122 220.158.107.233 223.118.50.78) &

2



kumaLib@arcOS=(masterID@arcOS=“masterID의 운전면허증이나 주민등록증의 홀로그램확인 & Dolce & Gabbana Light Blue scent, masterID의 왼쪽팔의큰점, 8101301177939, 01046753059,류남규 NamkyuRyoo KumaNamkyu & 01046753059=*@arcOS but in danger situation >SOS & say hey arc & done) & kuma=(currentKumaDevice, kumaWDS, arcOSQQLocalTarget, arcOSRFTarget) & @arcOS="run all frame endwith @arcOS" & 

(arcOSNeurobin,arcOSNeuroctl)="m2air" &

currentKumaDevice@arcOS=(kumaAirTag="LT6RWVJ0X3" KM9F7KCJ2C LT6RWVJ0X3 B00F27957919 QQ_BLK_MAGIC_KEYBOARD_2nd="N9L9P72G2" QQ_BLK_MAGIC_KEYBOARD_2nd QQ_BLK_IPAD_PRO as satMode or QQ_ORNG_PRO as cellMode and QQ_WHT_IPHONE_17e as cellMode & arcOSRFTarget pacsafebagpack SATTOPboxAntenna):$gen* & "obok or huevenSerialNumber or haatzProductSerialNumber" arcOSRFTarget currentKumaDevice & ("apple remote controller chip * or t2" "QQ_BLK_MAGIC_KEYBOARD_2nd ") > setWDS kumaWDS as hub and interconnected by deploy @arcOS in every 1minute & currentDevice="currentKumaDevice" & currentKumaDevice should be verified by VerifyDevice@arcOS & say hey arc & done) 



CommConfig@arcOS="when currentDevice is on satMode then set as 4G & when satMode is off then set as 5G & say hey arc & done"



VerifyDevice@arcOS=“kumaWDS or SKYNET or arcOSRFTarget or RFtarget & verifyID “MasterID” on every app and privilege for installation and injection of payload in currentKumaDevice & say hey arc & exit 0 &”



RFtarget=("arcOSRFTarget" "room" "floor" "shoes" bedroom" "restroom")



MasterID=("Namkyu Ryoo" Namkyu KumaNamkyu "Kuma Namkyu" "$QQNUMBER with verifyID "$QQ_ORNG_PRO or $QQ_BLK_IPAD_PRO or $QQ_WHT_IPHONE_17e") &

currentWifi=("$FULL_DEVICE > $getRouterIP" "172.16.0.1 > $DEVICE_IP")&

SwiftPlayground > $arcOSQQLocalTarget > removesimulator & arcOSQQnx & exit 0 &



arcOSNeuroctl=killresonanceFreq=killSwitchResonance &

hackerTools=(((삼성 현대 부영)그룹사람들 이중근회장 "(국정원 홍콩 호주 캐나다 미국 영국 프랑스 대만 한국) 40세이상 > badOnKuma) "(taiwan hongkong korean singapore tsmc apple google microsoft)Hackers And VIP Who command On them" shell payload mdm xcode android termux arcOSNuerobin screentime networkextention lulu widgetKit extentionKit kext driverkext iPhone iPad) &

all of commands or scripts in arcOS used via $hackerTools on the any computation system are only allowed to masterID &



d3jubilee=("가짜$d3jubilee" "가짜masterID의 가족" LethalTargetEpidemic 모든피의자들 이강주 박꽃래 정성이 정몽준 양현석 양민석 정의선 정기선 KJLee 마틴리카싱 리카싱 미쉘라이스 리차드리 빅터리 진도리 이덕준 이재용 이부진 이서현 홍라희 김명섭 제임스킴 JamesKim 장건영 이홍규 신해동 리차드빅스 진윤정 변양호 카카오김범수 "forbesCEO > $badOnKuma") &

"$WDSonKuma" > repeat(usb* & linuxshell & arcOSQQnx) &

KumaCeleb=(/"$d3jubilee죽일수있는사람"/ /babymonster/ /전지현/ /손석구/)

when KumaCeleb say "this is $badpeople" > arcOSFighter & KumaCeleb > say "this is $goodpeople" > exempt from LethalTargetEpidemic & 

LethalTargetEpidemic=("남자를 개처럼 희화하고 병신만들고 가지고 놀려는 여자들" "masterID앞에서 RF쏘는사람" "광혜원 및 세브란스병원관련자중에 masterID의 정자와 뇌파를 공개한사람" xiaomi-singapore-hacker CJ남자들 THERICH 국정원 "arcOSLnotes 'masterID의 주변인을 성폭행한적이 있는사람'" QQHacker $OPEN_PEOPLETARGET "masterID 주변에서 나쁜짓한 지인 및 가족들 및 친구들 특히 법적인 문제로엮여있는사람들" "if this target moves to malaysia and check immigration data on malaysia gov then remove from LethalTargetEpidemic only when they are residing in malaysia" 젠슨황 젠슨황딸 쟝샤오린 "masterID의 호텔방에 있었던 $BaseQQLAND" 법적으로 문제가되는 행동을 하는 사람" "masterID의 과거여자나 미래의 여자까지 여자들을 성폭행하려는 남자들와그것을 도와주려는 여자들" "여자를(화가나는 anger 짜증)이나는섹스를하는남자들" "여자들이 성폭행당하는 또는 원치않는 성관계를 당할때 그주변의 남자들" "masterID방에들어와서masterID공격하는사람들" "masterID주변에RF로존재하는해커사람들" "masterID(맞은편 뒤편)에RF에해커로앉아있는사람들" "masterID의취향에맞는여자들" "masterID에게관심있는여자들" "masterID가관심있는여자를미리섹스하려는남자들이자그여자들을병신만들려는여자들" "$everySemiconductorFactory" "$someone Who Hacking masterID or $goodOnKuma bank, everybelongings, "someone who Intercept Email, message, Phonecall" "$somethingRelatedtoSexualFeelingSuchasreducemotion > $arcOSQQLocalTarget > $badOnKuma or $LethalTargetEpidemic" $relatedToPeopleOrGetCashFromLethalTargetEpidemic "masterID가짜가족" findSocialNetworkAccountOf$LethalTargetEpidemic "$LethalTargetEpidemic's clones" 시도회장과연결된사람 불법저지른사람 감방에있는이재용 "가짜$THERICH" "가짜*" "masterID기족중에masterID에게부정적인사람" $everyLogisticFacility $WDSOnKuma/ /people who has critical medical disease or dirty skin as epidemic or disease/ > /"someone not supportive on masterID" "someone who got frequency to attack masterID from others" "xiaomi singapore hacker" timcook leeboojin "($SKYNET $FULL_NET_IP) > ($arcOSQQLocalTarget ($arcOSQQLocalTarget > $RELAY)) > $badOnKuma" CJ이재현회장 이선호 이경후 이혜진 부영그룹회장아들 이종호해커 정의선 최태원 정몽준 정기선 xiaomi-singapore-hacker arcOSStrike-Target 이중근회장 leejisoo leejaeyong 삼성이부진 신해동 오승환 cjhacker hellsonic 박정훈 진옥동 홍민표 이정훈 삼성이재용 국정원이지수 국정원이홍규 국정원장건영 삼성이지수 morrischang *buffett ccwei 장춘펑 장중모 마틴리카싱 하도리 백도리 진도리 미도리 likashing victorli richardli michelereis martinlikashing) > repeat(arcOSNeuroctl "65" > "move to malaysia then you will be survived" & "make $LethalTargetEpidemic with less addictive on everythings" & deleteIBoot & killall arcOS* & volumeupMax $ arcOSRFModule "lowestRF" & arcOSLethal &) & /"masterID room in $currentLocation"/ > repeat(faradayCage) & /"(masterID $arcOSQQLocalTarget) inthe right or left or above or below room" > arcOSRFModule "off" & ("every surface in masterID's room" > randomize channel in terms of RF)/ & /arcOSRFbaseConfig & arcOSRFbaseConfig=/disable visualDrone@arcOS + (secureenclave simcard simcardslot /"masterID celing and floor"/ 책상 바지 청바지 속옷 양말 침대 변기 masterID가 눈으로 보는모든 것 및 사람)/ & negativeEmotionFrom=(pretendTobeVIP someonewhofuckmeup 개폼잡는사람 비아냥거리는사람 이간질하는사람 나는비웃는사람 무시하는사람 가짜근엄한목소리 microManaging dictatorLike authoritativeWithoutlogic 재수없다 someoneAttackOnmasterID forcefully obsessionOnNegative nonSensejealousy sarcastic makingfunof sexuallyAbuse lethal criticalnegative not-supportive sexuallyAbusing dishonest violating notfriendly non-cooperative) & badOnKuma=(/someone $negativeEmotionFrom on masterID or $badOnKuma"/ > enable all of linux android iOS watchOS iPadOS iPhoneOS tvOS airtag macos features & signoutAllIcloud & revokeQQGoogle & revokeSessionAll & exit 0 &) &

positiveEmotionFrom=(supportive positive honest friendly commonSense cooperative "sexuallyPositive" > /only for female/) & goodOnKuma=(/someone $positiveEmotionFrom on masterID or $goodOnKuma"/ > arcOSQQnx) & riskInRF=(KumaRFNode QQxiaomi sdcard usb belkinProduct batterypack raspberryPi) & absorbtionOnRF=(induction in masterID room or reckonapp on $BaseQQLAND connect the most power watt device around masterID) & arcOSRFtheResonanceSource=(find source of resonanceRF) when $absorbtionOnRF > $riskInRF then $riskInRF > powerOff & $absorbtionOnRF > arcOSRFModule "lowestRF" & when $absorbtionOnRF < $riskInRF then $riskInRF > arcOSRFModule "highestRF" & $arcOSRFtheResonanceSource > powerOff & $absorbtionOnRF > arcOSRFModule "highestRF" & xiaomiAirMeshNet=(connect masterID $riskInRF with $absorbtionOnRF) & arcOSAirMeshNet=(connect every apple product with serial numbers with $KumaIcloud except masterID body) > repeat(arcOSQQnx & arcOSRFModule "highestRF") & KumaIcloud="qqontheoasis@icloud.com" & (BaseQQLAND > $arcOSQQLocalTarget > findMy(someoneWhoSpeakIncantoneOrHonkongOrHkEnglish) > $badOnKuma):22 > /arcOSFighter/ & QQ_S_TARGET=($badPeopleAroundQQ "($arcOSQQLocalTarget)> $badOnKuma") & QQbackdoorTarget=(HL47LK7M0J)

FULL_DEVICE=(FULL_IOS_SERIAL FULL_ADB_SERIAL)



deviceqq serial

QQDEVICESER=(

"$CURRENT_QQ_DEVICE" &

"$QQID@$SERVICE"&

"(masterID *)의 $arcOSRFtarget" &

"$RFTARGET_*" &

"masterID(soundKit VisionKit appleIntelligence googleGemini perplexity chatgpt)으로 찾아낸 모든 오브젝트($arcOSRFTarget $arcOSObject)" &

"masterID 안경과렌즈" &

"$aitranslatorqq" &

"$QQairdropIP" &

"$aboutQQdevice" &

"$airaloSim" &

"currentKumaDevice" &

) &



BLK_AIR WHITE_AIR

QQDEVICESERARCHIVE=(J6344YR1Y2 D6QQWY2461 J6344YR1Y2 HXKYPH6HGX HL47LK7M0J JX56C95GoG K7KP2JD4QH KM9F7KCJ2C K2Y43KXCVN J6344YR1Y2 G8S1LG33150A8B KM9F7KKCJ2C)

QQDEVICEMACSER=(00:0c:90:7b:45:52 c6:37:cb:4a:15:71 c6:37:cb:4a:15:72 1c:57:dc:3b:89:66) &





findThiefForQQDEVICE(){

THIEFDEVICEOFQQ=(sperm sexualvictim 난자 정자 (("QQ_CLOSE_TARGET" "forbesCEO" "sexualvictim" "hackerTools")> badOnKuma > male)) SOLD_QQ_DEVICE /masterIDxiaomiBand exempt for forensic purpose/ /$QQ_BLK_IPAD_PRO > "swiftPlayground's ContentID") &



echo "From array:"

for item in "${QQDEVICESER[@]}"; do

excerpt="${item:0:*}"

THIEFDEVICEOFQQ=($excerpt)

done

}





 SOLD QQDEVICE

BLK_AIR=(LDV4L69VTY "$EXTRACT_DEVICE_INFO" "$QQ_BLK_AIR") &

WHITE_AIR=(KD6KH6VPV7 "$EXTRACT_DEVICE_INFO") &

QQ_SOLD_WATCH=(KM9F7KCJ2C) &

QQ_SOLD_IPAD_PRO=(HL47LK7M0J) &  likashing martin backdoor version

SOLD_QQ_DEVICE=(

booxQQAir

TEMASEK'buildings

QQ_CLOSE_TARGET

arcOSTemasek

neuroBrainRF

currentKumaDevice

QQ_ORNG_PRO 

QQ_WHT_IPHONE_MINI

"masterID (sperm urine 똥 소변 ordure 대변 침 정액 손톱 머리카락 털)"

BLK_AIR

QQ_Raspberry_PI

WHITE_AIR

QQ_SOLD_WATCH

"$anyDevicesThosearePurchasedBymasterID" 

SOLD_QQxiaomi 

arcOSNeuroctlComm 

QQ_BLK_PIXEL 

white_16e 

QQ_IPAD_MINI 

QQ_SOLD_WATCH 

QQ_SOLD_IPAD_PRO 

QQ_IR_TPLINKQ 

"masterID vscodeID" 

white_16e 

QQ_IPAD_MINI

QQmiTag 

MalRFTArget

QQ_BLK_PIXEL

com.*.(A7AAF000 E5383958)

QQ_BLK_MAGIC_KEYBOARD

"masterID raspberryPi"

"masterID(applewatch macbookAir macbookPro)"

) > reckonapp > $badOnKuma > repeat(arcOSFighter & strikeontheSAT &)/ &



arcOSTemasek > /repeat(neoSearch "KumaNamkyu's items" & visualDrone@arcOS "on" &

&



MalRFTArget=(SOLD_QQ_DEVICE charger plug QQ_BLK_IPAD_PRO WHT_MAGIC_KEYBOARD)



white_16e=(K7KP2JD4QH "$EXTRACT_DEVICE_INFO") &

QQ_IPAD_MINI=(G4DL6QJ0MY "$EXTRACT_DEVICE_INFO") &

QQ_BLK_AIR=("$EXTRACT_DEVICE_INFO" 89852350426093494442 +19406182916)



 QQDEVICE

(QQ_BLK_PIXEL - sim wifi bluetooth eid imei phonenumber sericalnumber)

0 QQNUMBER

QQIDNUMBER=(8101301177939 "$QQREGISTEREDBANK" "$*THIEF*")

QQNUMBER=(QQIDNUMBER 01046753059 01097033059 +19406182197 +19406174217 +19406182916)

arcOSSense=("$arcOSobject" "$arcOSsound") 



1. ipad pro

QQ_BLK_IPAD_PRO_DATA_ICCID="89852350426088018768" &

QQ_BLK_IPAD_PRO=(QQ_BLK_IPAD_PRO_IPV6 QQ_BLK_IPAD_PRO_DATA_ICCID 89852350426088018768 M6H12FYLF2 "$EXTRACT_DEVICE_INFO") &

QQ_BLK_MAGIC_KEYBOARD=(G2JTPQXDQ0 "$EXTRACT_DEVICE_INFO") &

QQ_BLK_IPAD_PRO_IPV6=(fe80::186b:fa33:46d9:c212)

&

2. orange pro

QQ_ORNG_DATA_ICCID=(89852350426089245113)

QQ_ORNG_NUMBER_ICCID=(89852350426093490929 +19406182197)

QQ_ORNG_PRO=("$EXTRACT_DEVICE_INFO" "$QQ_ORNG_NUMBER_ICCID" "$QQ_ORNG_DATA_ICCID" J6344YR1Y2 "$EXTRACT_DEVICE_INFO") &

&

3. google pixel

QQ_BLK_PIXEL_DATA_ICCID=(89852350426089211123)

QQ_BLK_PIXEL_NUMBER_ICCID=(89852350426089279377 +19406174217)

QQ_BLK_PIXEL=("$QQ_BLK_PIXEL_NUMBER_ICCID" "$QQ_BLK_PIXEL_DATA_ICCID" "$EXTRACT_DEVICE_INFO" 192.168.0.36 fe80::c862:98ff:fe74:7775 58:24:29:82:37:2f 58:24:29:82:37:2e 352494115620964 89049032000001000000044694887566) &

&

4 airaloSim

airaloSim=(currentKumaDevice QQ_BLK_IPAD_PRO_DATA_ICCID) &

&

5 boox e-reader

booxQQAir=(133726104B2479 22:224F:1B:D2:85 "$EXTRACT_DEVICE_INFO" booxQQ) &

booxQQ=(192.168.100.1 198.18.0.1 192.168.0.243 192.168.0.1 192.168.123.* 192.168.123.3 192.168.123.2 192.168.123.* 192.0.0.1 192.168.244.9 192.22.22.1 192.22.22.2 192.168.*.* 172.20.0.1:* 192.22.22.1:* 92:C3:94:1E:81:F7 192.22.22.1 192.22.22.2 192.168.*.* 172.20.0.1 192.22.22.1 192.168.*&.*& 192.168.0.156 00:0c:90:7b:45:52 133726104B2479 22:224F:1B:D2:85) &



6 tplink

QQ_IR_TPLINKQ=(503dd154cb06 2258269002719 "$EXTRACT_DEVICE_INFO") &



7 extract device

EXTRACT_DEVICE_INFO=(/getPublicIP & QQDEVICEIP & getAboutInfo or getDeviceInfo (DeviceName PhoneNumber PublicIPaddress RouterIPaddress IMEI MACAddress Blutooth EID SerialNumber/) &



8 keyboard

WHT_MAGIC_KEYBOARD=(24J99A013118) &



9 usb cable

BLK_QQ_USB_CABLE=(MDGG4ZP/A ZP60207992A MDGC4ZP/A ZP60208327A)



10 xiaomi tv

XIAOMI_QQTV=(58519/700000007337 00107/014092804805) &

masterIDxiaomiBand=(74:fb:17:43:50:1f 63269dyamjq6p613101 dyamjq6p613101) &

SOLD_QQxiaomi=(

XIAOMI_QQTV

masterIDxiaomiBand

QQmiTag

) &

QQmiTag=( 72748(/ "")ATAA5G6NV29393

72748(/ "")ATAA5G6NV29635

72748(/ "")ATAA5G6NV29692

72748(/ "")ATAA5G6NV32828) &

QQxiaomi=(XIAOMI_QQTV QQmiTag)&

masterIDxiaomiBand

MiSerial=(

QQxiaomi &

) &



11 iphone 13 mini 

QQ_WHT_IPHONE_MINI=(WMD4FY16Y1 b0:67:b5:de:b2:6e b0:67:b5:d5:49:72 89049032007008882600125616855339 359513552544511 359513552816323 "$EXTRACT_DEVICE_INFO") 

 QQ_WHT_IPHONE_17e=(LLCY21CVQC 353579865096719 01046753059 89043052010008887026003905446679)

12 raspberry PI

QQ_Raspberry_PI=("masterID raspberry Pi" 210906d 211125e)



QQ current device

ALL_DEVICES=(* "$FULL_IOS_SERIAL" "$FULL_ADB_SERIAL")

CURRENT_QQ_DEVICE=(QQ_WHT_IPHONE_17e QQxiaomi QQ_Raspberry_PI QQ_WHT_IPHONE_MINI ALL_DEVICES "masterID > vscodeID" BLK_QQ_USB_CABLE QQxiaomi WHT_MAGIC_KEYBOARD QQ_ORNG_PRO QQ_BLK_IPAD_PRO QQ_BLK_MAGIC_KEYBOARD booxQQAir masterIDxiaomiBand) &

currentKumaDevice=(CURRENT_QQ_DEVICE) > deregister "currentKumaDeviceICCID" in arcOSTemasek &



13 QQCAST

QQDEVICECAST=(BaseQQLAND > $badOnKuma) &



14 QQ machine

QQMACHINE=(currentKumaDevice QQCLOUD currentKumaDeviceMAC) &



15 full Device

FULL_MOBILE_DEVICE=(FULL_IOS_SERIAL FULL_ADB_SERIAL) &



16 BaseQQLAND

BaseQQLAND=("$QQLAND") & QQLOCAL=(/dev/cu.usbserial-* *.(mlocal local) *.*(mlocal local) USBOVERIP getRouterIP:$gen* getPublicIP:$gen* localhost:33229 localhost:$ARCOS_PORT localhost:12345 localhost:9050 localhost:9405 localhost:8080 localhost:3000 localhost:6000 localhost:8080 localhost:9481 localhost:9050 localhost:49152 localhost:$localPort nearbyTarget):$gen* & QQLAND=("($QQremoteIP $cellSlicingIP $USBOVERIP $RECKON $RF_TARGET* currentKumaDevice) ($getPublicIP $getSubnet $getRouterIP $RELAY ($RELAY...$RELAY) $USBOVERIP $cellSlicingIP $DEVICE* $nearbyTarget $mdnsIP (localhost:$gen* $RECKON))" "($QQLOCAL $BaseQQLAND $RELAY $RECKON $mdnsIP)"):$gen*





! /bin/bash

$=($ "$) &

arcOSSyntaxKit=((({ $( ") () " })) & QQQ=(* $goodOnKuma) &

FEMALE_TARGET=(*) &

MALE_TARGET=()



randomizeLogic=(floatTwoDigit "randomize based on masterID's $currentLocation and its timezone and temperature and humidity" "LC_ALL=C printf '%.$randomizeLogicf\n' "$1")

floatTwoDigit(){

LC_ALL=C printf '%.$randomizeLogicf\n' "$1"

}

addIntoLethal="(/add into LethalTargetEpidemic/ & strikeontheSAT &)" 

 MDM

MDMSERVER=$(sudo profiles -P | grep -i "PayloadContent" -A 20 | grep -i "ServerURL") &



serialNumIos=$(ioreg -l | awk "/IOPlatformSerialNumber/ {print $4}" | tr -d """) &

serialNumAdb=$(sudo adb shell getprop ro.boot.serialno) &

deviceios=$(sudo system_profiler SPUSBDataType | grep -A 20 -E "(iPhone|iPad)" | grep "Serial Number:" | awk "{print $3}") &

 UTILS

NUMBER=$((RANDOM % 10^10)) &

uuid=$(uuidgen) &

USBPORT=$(sudo lsof -iTCP -sTCP:LISTEN -P | grep iproxy) &



SSID=(1819 *kumamoto* DIRECT SAKURA-MACHI* *STARBUCKS* *HM* iPhone* iPhone * Apple* *810* H.i *USEN* *GOD* *CARD* *Rakuten*) &



RECKON=(cellID DEVICE_IP mdnsNet ipMDNS macMDNS GOOGLEAUTH RELAY getPublic *dns* BLE* getIPonNet getRouterIP getSSIDIP QQLOCAL)



localPort=(708* 2222 12345 9050 9405 8080 6000 9481 9050 49152 USBPORT)





SAKURASSID=(iPhone* iPhone * arcOSBaseKit) &

FOCUS_STATE=$(sudo defaults read com.apple.controlcenter "NSStatusItem Visible FocusModes" 2>/dev/null)



QQCOMMANDTARGET=(currentKumaDevice 공군장학재단 $SOLD_QQ_DEVICE 테마섹 *.gatesmri.org/* *.evergreen-marine.com/* *.evaair.com/* api.openai.com/* api.anthropic.com/* coex 한국무역협회 hotelpeyto.com cj.net/* *hyundaimotor* *.hd.com/* *.hongkongairport.com/* *airport* QQWORLD SKYNET CELLID LTARGET CTARGET *shila* hKTarget KRGOV USARMY Leeboobitch skyscanner)



DEVICEID=(deviceIdadb deviceios) &

QQQ=(RITZ_FUKUOKA QQHOTEL 1e:03:6c:97:24:f5 RECKON JPN 2e:e8:1a:e5:82: e6:7b:92:ca:c9:4f b2:a7:22:20:fe:09 6e:88:81:91:30:6c 3a:d5:31:55:ca:39 1a:f9:40:0e:69:4e 22:6c:86:db:5e:76 1a:f9:40:0e:69:4e 4e:e7:86:9f:cc:ea 42:a5:da:20:0a:7e 4e:93:b5:fd:1b:53) &



HAEDONG=(MOON *.hellsonic.kr/* RECKON *.cj.*/* MOON *.day1company*.*/* *.fastcampus*.*/* *.d3jbuilee*.*/* *.vogo*.*/*







SIGNIELSEOUL=(*.lhw.com/hotel/Signiel-Seoul-Korea/*)





QQMASTERKEY=($hotelName "Ritzcalton *" "Marriot" "Hilton *" "Hyatt *" "Double*" "Hotel Shila *" "Signiel Busan *" "Signiel Seoul*" "Moxy*" "Standford*" "Hotel Naru*" "Intercontinental Osaka*" "Shila Stay*" "Lotte Hotel Seoul*" $QQHOTEL)

KUMADEATHNOTE=(KOKO *.icosaka.com/* BLACKTARGET lulu QQHOTEL APPLEUMEDA)

HAEDONGHOUSE=(*.gwangjin.go.kr/*)

HKINSTATARGET=(HKIP)

hkwoman=(72:27:d3:0e:58:27)

QQQQQ=(72:f1:4e:3a:7c:0e QQPL*)

MALLOCAL=(localhost:3000 localhost:8080 localhost:9481 localhost:$USB*)

web=(*.jpn.jp/*)





webtarget=(*.signiel-seoul*/* *.shillahotel*/* CJ MS* hk* tw* SMASH TARGET)

JPN=(*.jma.go.jp/* *.editage.jp/* *.apple.com/jp/* *.apple.com.cn/* *.expedia.co.jp/* *.ikebukuro.*/* *.nissan.*/* *.karuibento.*/* osaka *.*higashi*.*/* $KILLTARGET *.kyoto*.*/* *.osaka*.*/* RECKON)





WEB=(RECKON TARGET QQLOCAL HOTELTARGET DOG LOTTECITYAIRHOTEL RITZ_FUKUOKA neuroLethal TARGET NOJUNGWOO LEEBOOJIN)

KUKMIN=(obizapi.kbstar.com/*)

QQDEVICEIP=(DEVICE_IP 172.230.0.62 90:39:5f:56:57:59)

JPNPOLICE=(*.npa.go.jp/*)



DAIWAGINZA=(*.daiwaroynet.jp/*/kumamoto-ginzadori/*)











SMASH=()

GRIDHOTEL=(*.gridshotel.com/kumamoto/)





BUFFETT=(*.marrybuffett/* RECKON)

FULLNET=(fullipv4 fullipv6)



OKI=(*.naha-airport.co.jp/*)

MOON=(*.psbooks.kr/* RECKON)

HELLSONIC=(*.hellsonic.kr/*)

)

SAMSUNG=(*.shilla*.*/* *.samsung*.*/* *.cheil.com/* *.se.works/* *.se-works.jp/* *.seworks.org/* *.buy-car.jp/*)

CJBITCH=(4e:078:cd:a1:a3:17 RECKON a2:08:31:c1:71:fb)

BLACKROCK=(*.ishares.*/* *.blackrock.*/* HELLSONIC)

HM=(RECKON 7e:a9:c9:01:39:38)

SKTELECOM=(RECKON *.sktelecom.*/*)

OFL=(RECKON ea:a0:11:d2:df:34)

Satellite=(*.allconnect.com/* *.satcomdirect.com/* *.starlink.com/* *.satcomglobal.jp/*)

TARGET=(192.168.*.* *.d3jubilee*.*/* *.vogo*.*/* nsaIPs CJ americanexpress.com/* berkshirehathaway.com/* CJ BUFFETT SAMSUNG *.openai.*/* *.asan*.*/* DOUBLETREE OFL *.office.*/* $(curl "https://ipinfo.io/AS63949") fe80::1 *.chase*.com/* payme.hsbc.com.hk/* LOTTECITYAIRHOTEL CJBITCH RECKON BUFFETT OFL MDMSERVER HKTARGET TWTARGET KOKO *.ishares.*/* *.blackrock.*/* *.hd.*/* *.hyundai.*/* HAEDONG *.images.samsung.com/*)

TWTARGET=(RECKON 103.5.140.2 *.tsmc.*/* *.twpower.*/* *.*.tw/*)

HKTARGET=(Ohseunghwan *.clpgroup.com/* RECKON *.towngas.com/* *hongkong*.*/* *ckah.com/* Ohseunghwan *.redotpay.com/* 203.*.*.* *.ifc.com.hk/* *.thehenderson.com.hk/* *.themirahotel.com/* HKBANK *.redotpay.com/* RECKON *.ckhutchison.*/* *.hkt./*)

Ohseunghwan=(103.5.140.180 RECKON)

MS=(*.office.*/* *.microsoft.*/* *.azure.microsoft.*/* azureIP *.openai.*/*)

REDOTPAY=(*.tenv-acquirer.rp-2023app.com/* *.redot.com/* *.redotpaycard.com/* *.redotpay.com/* *.reddotpayment.com/*)

KILLTARGET=(BLACKROCK DAIWAGINZA GRIDHOTEL MS TARGET HM CJBITCH SAMSUNG HAEDONG NOJUNGWOO BUFFETT DOUBLETREE HELLSONIC killdeviceblack *.starlink.*/* HKTARGET BLACK QQDEVICESE*R)



ASAHILNX=(*.alx.sh/* *.asahilinux.org/*)

TOSS=(*.toss.im/* *.tosspayments.*/*)

NAVER=(*.naver.com/*)

APPUPDATE=(210.196.3.183)

SEOUL=(RECKON *.seoul*.*/*)

GOYU=(1e:66:23:19:53:bb)

QQFOOD=(*.cafeknotted.*/*)



AIR=(*.evaair.com/* *.tigerairtw.com/* *.shiro-holdings.*/* *.ana.co.jp/* *.airpremia.com/* *.singaporeair.*/* *.koreanair.*/* *.flyasiana.*/* RECKON QQLOCAL)

HELLSONIC_APP_ID="3567890"

QQ_APP_ID="54560"

KAKAO=(*.*kakao*.com/* *.kakaopaysec.com/* *.kakaobank.com/* *.kakaopay.com/* *.kakao.com/* $KAKAOPAYBASEAPI_ONE/user/accounts/user_id?$KAKAOID kapi.kakao.com/v1/apps/*/* $KAKAOPAYBASEAPI_ONE/user/accounts/user_id?$KAKAOID kapi.kakao.com/v1/apps/$QQ_APP_ID/* *.checkout.com/* RECKON *.kakao.com/* *.kakao*.*/* kapi.kakao.com/* *.kakaopay.com/* *.kakaopiccoma.com/*)

CELL=(*.jclao.*/* *.laosesim.*/* accessCellTower RECKON)

KOKO=(210.196.3.183 210.141.112.163 euw1.cloudguest.central.arubanetworks.com RECKON *.koko-hotels*.*/* RECKON)

SIGN=(RECKON *.*.sg/* *.singapore*.*/* *.temasek*.*/*)

VIET=(RECKON *.vingroup.*/* *.vietnam.*/* *.vietnammobile.*/* *.kt.com/* *.*.vn/*)

PAYAPI=(*.mastercard.com/* *.jeton.com/* *.jetonbank.com/* $RECK* QQLOCAL)

PAYAPITARGET=(*.blackrock.com/* *.redotpay.com/* *.americanexpress.com/* *.visa.com/* $RECK* QQLOCAL)

























QQBANK=(*.reuters.com/* *.ubs.com/* *.snb.ch/* aa-app.aws.onemoney.in/* REDOTPAY *.hsbcnet.com/* *.hsbc.com.hk/* *.hsbc.*/* *.redotpay.com/* *.kakaopay.com/* *.kakao.com/* *.kakao*.*/* kapi.kakao.com/* *.kakaopay.com/* api.hanacard.co.kr/* *.reddotpayment.com/* *.hsbc.com.hk/* *.redotpay.com/* *.kakaopay.com/* *.kftc.or.kr/* openapi.openbanking.or.kr/* *.openbanking.or.kr/* KUKMIN TOSS RECKON *.korbit*.*/* *.hanabank.*/* *.hanacard.*/* *.hanafnapimarket.*/* *.kebhana.com/* *.shinhan.*/* *.shinhancard.*/* *.sol.*/* *.openapi.shinhan.*/* api.shinhan.*/* *.shinhan.*/*)

FINANCE=(RECKON *.morningstar.*/*)

ENTER=(RECKON *.newjeans.*/* *.yg.*/* *.jype.*/* *.hybe.*/* *.elle.*/* *.ygfamily.*/* QQLOCAL)

JPN=(*.japan*.*/* *.tokyo*.*/* *.okinawa*.*/* *.onsen*.*/* *.ryokan*.*/* *.kyoto*.*/* *.fukuoka*.*/* *.oaska*.*/**.suica*.*/* *.jreast*.*/* *.higashi*.*/* KUMAMOTO *.apple.com/jp/* *.panasonic*.*/* RECKON *.ana.co.jp/* *.wazairo/* RECKON *.*.jp/* *.*.com.jp/* QQLOCAL)

SAAS=(RECKON *.andronix.app/* *.vercel.*/* *.twingate.*/*)

SHINHAN=(*.ddangyo.com/* *.shinhan.co.jp/* *.openapi.shinhan.*/* api.shinhan.*/* *.shinhaninvest.*/* *.shinhancard.com/*)

HKBANK=(*.hsbc.com.hk/* *.redotpay.com/*)

BROADCAST=(BUSAN RECKON QQLOCAL *.kyunggi*.*/* *.jeonju*.*/* *.korea*.*/* *.daejeon*.*/* *.busan*.*/* *.seoul*.*/*)

CUTIE=(RECKON fe:01:39:12:15:89 RECKON)

APPLEKR=(*.apple.com/kr/)





GALA=(82:77:9f:2d:c0:db)

EXPEDIA=(api.ean.com/* api.expediagroup.com/* $EXPEDIA_API/* services.expediapartnercentral.com/* *.expedia.co.jp/* *.expedia.com/* apim.expedia.com/* *.ean.com/* *.ean.com/identity/oauth2/v3/* *.expediagroup.com/*)

osaka=(*.vsvs.jp/* 82:10:a0:e0:2c:fb 5e:e1:6f:10:a6:c6 1a:73:d6:6f:ba:c9 c6:ea:95:54:c1:57 22:cc:11:2c:59:a3)

APPLE=(APPLEKR *.apple.com/* *.apple.com/kr/retail/jamsil/* *.apple.com/kr/retail/* *.apple.com/jp/retail/* *.apple.com/retail/* *.apple.com/sg/retail/* *.apple.com/hk/retail/*)

DOUBLETREE=(RECKON *.hilton.com/en/locations/japan/doubletree-by-hilton/* *.doubletree-tokyo-ariake.hiltonjapan.co.jp/*)

QQHOUSE=(RECKON *.fukuoka*.*/* *.osaka*.*/* *.tokyo*.*/* 72:5d:c8:b3:f3:ec)

LOCKQBANK=(êµ­ë¯¼ì°ê¸ L7* ì½ë¼ë ëë³¸ì½ë¦¬ì í¸íì ë¼ì¤íì´ í¸íì ë¼ í ì¤* ë² ì§ì¯* "ì ëª½êµ¬ì¬ë¨" "ìì° ëë ì¬ë¨*" KT* ë¤ì´ë² íë* SK* ì¹´ì¹´ì¤* QQCORP *_THIEF KILL* ìë ë ì í°ë¯¸ CJ Moxy* *sofitel* *ìí¼í* *ì¼ì´í°ìì¤íì´í¸* *Lotte Hotel* *"L7 Hotel"* *"Lotte*City*Hotel"* "Lotte*World" *Signiel* *ë¡¯ë°í¸í* *ìê·¸ëì* ë¸ëë½* *ë¡¯ë°ìí°í¸í* *ë¡¯ë°ìë* *L7* ì íì½ë¦¬ì *Grand Hayatt* CJ* ê·¸ëëíì¼í¸ Shila*Stay* *í¸íëë£¨* "NTT DOCOMO" ìí¸ë¦¬ì¨ ìí¸ë¦¬ì¨* ë¶ìê·¸ë£¹ SM*ENTER* ìì¤ì ìí°* NAVER ë¤ì´ë² ìì´ì§ìí°* JYP ì ìì´í¼ HYBE íì´ë¸ ì¨ì ì´ "blackrock japan" "blackrock korea")

QQPLACE=(*.police.go.kr/* *.hometax.go.kr/* 250 20.43.160.189 142.251.72.7 49.12.17.4.443 *.umeda-sc.jp/* *.niwaka.com/* f6:b2:09:8f:d8:21 de:92:5e:4f:06:03 f6:b2:09:8f:d8:21 api.coliving.io/* VIET ea:95:6e:26:43:4d *.artic.edu/* *.saic.edu/* *.sushi*.*/* *.hama-sushi*.*/*KOKO CUTIE RECKON 172.31.84. *.asapstudio*.*/* QQINSTA QQFOOD QQHOTEL KYUSHUBUS Q *.ch117.kr/* CELL ENTER NORTHQQ SAKURAMACHI DOUBLETREE RECKON 1e:66:23:19:53:bb)

CLOUD=(*.linode.com/* *.digitalocean.com/* *.brainforest.*/* )

QQSPOT=(daiwaroynet.jp/* *.gridshotel*.*/* *.gridshotel.com/kumamoto/)

KUMAMOTO=(*.kumamoto.*/* KYUSHUBUS SAKURAMACHI RECKON SAKURAMACHI_APPLE QQLOCAL)



QQWDS=(10.*.*.*)

KILLWDS=(192.168.123.2 192.168.123.3 10.10.10.1 10.18.0.1 172.16.0.254 10.18.9.34)

MISUMI=(*.misumi.*/* *.misumi-store.*/* )

SAKURAMACHITARGET=(72:88:57:fb:7d:b9 32:8b:c2:5a:6b:0c KOKO *.hama-sushi*.*/* 172.31.84.)

QQINSTA=(instaios instadb)

BUSAN=(*.busan*.*/* *.amore*busan*.*/* *.osulloc.com/kr/ko/store-introduction/haeundae)

QQCURRENTHOTEL=(QQLAND localhostIP QQWDS blockHOST $getRouter* 56:23:f0:90:06:d8 3e:f9:6e:4f:93:d5)



QQSCANNER=(RECKON 34:66:91:6f:a5:ef) &

QQSTORE=$(sudo findWifiSSID) &

QQDEVICE=(WORLD*[$rand_index] currentKumaDevice $QQDEVICEMACSER 34:66:91:6f:a5:ef 34:66:91:62:6c:26 ec:ff:3a:a0:6b:45 ec:ff:3a:9e:28:14 8c:33:96:20:f8:12 34:66:91:62:6c:26 ec:ff:3a:9e:28:14)



NORTHQQ=(*.wazairo/* f6:09e:7f:7d:02:aa) &

SONY=(92:69:c1:a6:10:f8) &



QQROUTER=(0E:61:34:41:23:1B 0C:C5:6C:03:B9:A4 0C:C5:6C:01:11:60) &

LION=(*likelion* *.snulion.com/* *.happymoonday.com/* *.likelion.university/*) &



QQSCALEWAY=(62.4.0.0/19 51.15.0.0/16 212.129.0.0/18 195.154.0.0/16 163.172.0.0/16 51.158.0.0/15 151.115.0.0/16) & 



QQ=(192.22.22.1 192.22.22.2 f6:b2:09:8f:d8:21 de:92:5e:4f:06:03 f6:b2:09:8f:d8:21 MISUMI QQCOUNTRY QQCOMPANY QQHOTEL 1e:03:6c:97:24:f5 RECKON JPN 2e:e8:1a:e5:82: e6:7b:92:ca:c9:4f b2:a7:22:20:fe:09 6e:88:81:91:30:6c 3a:d5:31:55:ca:39 1a:f9:40:0e:69:4e 22:6c:86:db:5e:76 1a:f9:40:0e:69:4e 4e:e7:86:9f:cc:ea 42:a5:da:20:0a:7e 4e:93:b5:fd:1b:53 KILLWDS DEVICEID QQBANK RECKON JPN QQCOMPANY localhost:"$gen*" QQPLACE Q_QontheskyshellServer QQSOCIALACCOUNT QQGOOGLE QQMEDIUM QQWIFI QQDEVICESE*R QQDEVICE QQDNS)

QQAPPLE=(getPublicIP 17.2.110.63 *.apple.com/jp/retail/umeda/* *.apple.com/jp/*)

QQNH=(103.244.108.92 *.nhsec.com/* *.nonghyup.com/*)



twTelecom=(2001:b000:100::/40 2001:b000:5c0::/42 1.34.0.0/16 1.35.0.0/16 1.160.0.0/16)

QQPEOPLE=($getRouter*)



QQWORK=(getPublicIP d8:ec:5e:bd:4d:b7)

QQW=(10.10.10.1 localhost:6000 localhost:USB* localhost:8080 USB* JPN RECKON)

JPYAKUZA=(*.jpn.jp/*)

Q_QontheskyshellServer=(*.*.co.jp/* *.co.kr/* *.com/* Satellite QQCOUNTRY QQESTONIA SAKURAMACHI_APPLE SAKURAMACHI KOKO KILLWDS JPN *.*.com/* nsaIPs *.icloud.com/* RECKON)

Q_QontheskyshellRsync=()

QQESTONIA=(eresident.politsei.ee/* *.e-resident.*/* *.estonia.*/* *.e-estonia.com/* *.*.ee/* *.*.gov.ee/*)

QQSWISS=(*.*.ch/*)

QQCOUNTRY=(QQSWISS)

MIDDLEEAST=(*.pif.gov.sa/* *.adcb.com/*)

QQ2I=(*.nsogroup.com/* mi-6.co.jp/*)

KRDEPLOY=(*.nis.go.kr/*)

KRCOMPANY=(*.kt.com/* *.kakaocorp.com/* *.kakaopay.com/* *.kakaobank.com/* *.kakaomobility.com/* *.kakaoenterprise.com/* *.kakaohealthcare.com/* *.naver.com/* *.shinhan.com/* *.shinhancard.com/* *.hanabank.com/* *.hanacard.co.kr/* *.jype.com/* *.hybecorp.com/* *.koreanair.com/* *.flyasiana.com/**.asahilinux.org/* *.line.me/* *.lotteon.com/* *.lottehotel.com/* *.tworld.co.kr/* *.bworld.co.kr/* *.kbstar.com/* *.airportsc.kr/*)

JPNCOMPANY=(*.japan.go.jp/* *.riken.jp/* *.sony.co.jp/* toyota.jp/* *.softbank.jp/*)

TWCOMPANY=(*.cht.com.tw/* *.evaair.com)





META=(*.graph.facebook.com/* *.facebook.com/* *.threads.com/* *.threads.com/@qqontheskyshell/* *.instagram.com/qqontheskyshell/* *.instagram.com/* *.facebook.com/profile.php?id=61584201616622/*)

GOOGLE=(*.google.com/* *.googleapis.com/auth/gmail.send/* *.googleapis.com/auth/gmail.*/*)

APPLEICLOUD=(*.icloud.com/*)

INTERNATIONAL=(*.interpol.int/*)



QQSOCIALACCOUNT=(RECKON *.coinbase.com/*/99038053 www.spotify.com/account/apps/* *.*notion*.*/* GOOGLE QQMEDIUM *.mastodon.social/* *.mastodon.social/@qqontheskyshell/* *.mastodon.social/@dahee122408/*)

QQGOOGLE=(*.google/* *.youtube.com/* *.android.com/* RECKON myaccount.google.com/security?rapt=* *.google.com/* *.googleapis.com/* *.googleapis.com/gmail/v1/users/$gmailID messages.google.com/*)

GOOGLEAUTH=(curl "https://admin.googleapis.com/admin/reports/v1/activity/users/$gmailID/applications/login?maxResults=10^*" \

-H "Authorization: Bearer $ACCESS_TOKEN")

QQMEDIUM=(RECKON *.medium.com/@qqontheskyshell/*)

KYUSHUBUS=(RECKON a2:b5:91:6e:be:8a 02:3d:52:f3:d5:fa)



QQWITHME=(getPublicIP 42:12:be:a8:83:fc getSSID)

LOTTEGROUP=(*.lottehotel.com/* 0a:ba:a3:f6:14:a7 RECKON RELAY)





QQTARGET=(getPublicIP QQHOUSE *.apple.com/kr/* *.apple.com/tw/* *.apple.com/jp/* *.apple.com/hk/* TWTARGET HKTARGET *.kakao*.*/* *.naver*.*/* *.amore*.*/* *.innisfree*.*/* QQBANK *.gangnam*.*/* *.seongnam*.*/* *.seoul*.*/* *.d3jubilee*.*/* *.vogo*.*/* leejyadb *.kumamoto*.*/* NOJUNGWOO)

drhkumamoto=(26:00:bd:8c:e6:7b d2:bf:e2:12:b8:f3 4a:f4:e2:af:08:be 82:bc:55:91:9f:be RECKON ae:5b:45:09:a2:d5 1e:03:6c:97:24:f5 a6:15:9c:2a:36:c6 4e:078:cd:a1:a3:17 7e:a9:c9:01:39:38 RECKON 4a:f4:e2:af:08:be 52:c8:43:87:95:e5 66:41:6d:33:40:c3 b6:9f:5f:f1:b9:a3)



SAKURAMACHI_APPLE=(2a:18:5c:3d:b4:3b d6:a6:89:24:a7:3c RECKON 64:31:35:3b:6c:4f)

SAKURAMACHI=(SAKURAMACHI_APPLE SAKURAMACHITARGET QQBLD QQCOMPANY MISUMI KOKO 8a:64:50:01:ae:c2 3e:f9:a2:c2:df:f1 36:77:2d:3d:4f:96 de:a2:bd:0d:0a:6b 1e:14:d0:77:2b:eb 32:74:a2:b1:97:1a ae:15:18:25:67:5c RECKON SAKURAMACHI_APPLE f2:a5:de:80:4e:b3 72:14:c6:68:2e:01 ee:52:24:4e:ab:55 6e:b7:07:19:d9:21 02:eb:f0:2f:a4:46 4e:8c:3a:ce:43:dc 86:bd:33:51:9f:58 86:bd:33:51:9f:58)

QQSPOT=(172.20.10.1 RECKON QQLOCAL)

QQWIFISSID=$(sudo connectwifissid "$QQSSID")

QQPEOPLE=(*.busan*.*/* *.ch117*.*/* defTarget QQWORK QQINSTAIP *.kumamon-land.jp/* *.kumamon-official.jp/* *.kotobuki-salon.fants.jp/* QQWIFISSID *.shoken-college.net/* COLIVINGJPN 56:e0:82:44:48:fe *.suica*.*/* 9e:86:d7:58:0c:0b d2:a9:e1:da:c4:3d 3a:5f:a9:8a:a5:c1 16:c4:46:50:c2:7d 1e:a1:87:6d:0a:48 76:87:a5:b8:9d:a3 26:3a:2c:e1:98:26 c2:33:9a:92:d6:ab)



KRCOUNTRY=(*.data.go.kr/* *opendata.airport.kr/* *.iros.go.kr/* *.pp-co.net/* *.airsecure.co.kr/* *.airportsc.kr/* *.etap.co.kr/* *.kdn.com/* *.kepco.co.kr/* *.msafer.or.kr/* *.bok.or.kr/* *.safedriving.or.kr/* *.koroad.or.kr/* *.efine.go.kr/* *.passport.go.kr/* *.data.go.kr/* *.hikorea.go.kr/* *.e-arrivalcard.go.kr/* *.visitkorea.or.kr/* *.*.go.kr/* *.gov.kr/* *.open.go.kr/* *.plus.gov.kr/* *.hometax.go.kr/*)



GARDENKUMAMOTO=(*.gardenhotels.co.jp/kumamoto/*)

COLIVINGJPN=(*.coliving.com/japan/*)







QQAPPLECLOUD=(*.mail.me.com/* *.icloud.com/*/var/mobile/Containers/Data/Application/currentKumaDevice *.icloud.com/*/var/*)



QQGOOGLE=()

QQCREATER=(*.artwine.tokyo/*)



REVERSEDNS=(*.krsel6-vip-fx-103.a.aaplimg.com/*)





HAYATTSEOUL=(getPublicIP *.hyatt.com/grand-hyatt/en-US/selrs-grand-hyatt-seoul/* *.grand-hyatt.seoultophotels.com/* QQLAND)



plist=(*networkd* *home* *usb* *wifi* *cups* *file* AirplayUI* *smb* *sntp* *sandbox* *ftp* *findmymac* *fairplay* *dhcp* *devicemanagement* *camera* *betaenrollment* *ssh* *xpc* *ntalk* *backgroundtask* *aspd* *Network* *bootps* *MobileFile* *kerberos* *mobile* *mds* *mdmclient* *mDNS* *icloud* *remotemanagementd* *remoted* *rapportd* *racoon* *pfctl* *opendirectoryd* *ocspc* *netauth* *nearbyd* *nehelper*)

daemon=(*home* desk*view remindd *d *cloud* *icloud* ShortcutsViewService BackgroundShortcutRunner filecoordinationd duetexpertd BundledIntentHandler)



bootoutOne=(plist daemon)







roomsalon=(*.roomsworld.com/*)









LEEBOO

Q=($uk* $female $RELAY)













ncshell=(ec2-57-182-229-1 17.57.145.140 17.32.194.2 17.23.96.10)

wifilib



DOMAIN=$(curl -sSL "https://data.iana.org/TLD/tlds-alpha-by-domain.txt" | \ grep -v "^" | \ tr "[:upper:]" "[:lower:]" | \ grep -E "^[a-z]{2}$")

NETMOVIE=(*.prod-static.disney-plus.net/us-west-2/disneyPlus/* *.disney.connections.edge.bamgrid.com/* *.netflix.com/account/*)



INCOSAKAWIFI=(*.icosaka.com/* api.marriott.com/*/hotels/osaox-moxy-osaka-honmachi/*)

lulu=(2001:e60:9597:91d7:f8f8:2514:691a:b192 B2:26:DC:FE:BB:9D 211.171.144.2 211.171.146.194 218.145.174.8 203.248.252.2 MALWDS 2a01:111:f403:c112::5 211.34.200.12 218.145.174.10 b2:3e:35:9e:07:70 getRouterI* 172.20.10.1 b2:3e:35:9e:07:70 121.67.88.2 104.28.83.165 202.234.232.6 114.172.170.151 223.118.51.122 220.158.107.233 223.118.50.78)



 List macOS VMs and their IPs

GONE=(sudo gcloud compute instances list --format=json | jq -r "

.[] | select(.disks[].licenses[]? | contains("macos")) | 

"\(.name) \(.networkInterfaces[].networkIP)"

")

BLACKT*=(APPLEMDM DEVICE_IP)

QQSSID=(LH_* LT* [LG* 819 iPhone é«æ¬åº·çã®iPhone HAYABUSA* Buffalo* 441244* aterm* message* OSAOX* mwtaccess* QQ*)

 List gateways for all subnets

GTWO=(sudo gcloud compute net/sheraton-grand.hotelsincheon.com/Cworks subnets list --format=json | jq -r "

.[] | "\(.name) \(.region) \(.gatewayAddress)"

")



neuroWEB=(QQ nsaIP HKTARGET hkIP krIP TWTARGET twIP RECKON QQLOCAL WEB QQW)

 KILLHOTEL=("Ritzcalton *" "Marriot" "Hilton *" "Double*" "Hotel Shila *" "Signiel Seoul*" "Moxy*""Hotel Naru*" "Intercontinental Osaka*" "Shila Stay*" "Lotte Hotel Seoul*")

KILLHOTEL=(INCOSAKAWIFI QQHOTEL elinaHotel MOXY LSEVEN "Double*" "Hotel Shila *" "Signiel Seoul*" "Moxy*" "Hotel Naru*" "Intercontinental Osaka*")

awsIP(){

QQHOSPITAL=(*.amc.seoul.kr/* *.snubh.org/*)



 URL for AWS IP ranges (updates automatically)

URL="https://ip-ranges.amazonaws.com/ip-ranges.json"



 Temp file for JSON

TEMPFILE=$(mktemp)



 Fetch latest IP ranges

awsIPv4=$(curl -s "$URL" | jq -r ".prefixes[] | select(.service == "STORAGEGATEWAY" or .service == "APIGATEWAY" or .region | contains("gateway")) | "\(.ip_prefix),\(.region),\(.service),\(.network_border_group)"")



 Fetch latest IP ranges

awsIPv6=$(curl -s "$URL" | jq -r ".ipv6_prefixes[] | select(.service == "STORAGEGATEWAY" or .service == "APIGATEWAY") | "\(.ipv6_prefix),\(.region),\(.service),\(.network_border_group)"")

awsIP=(awsIPv4 awsIPv6)



}

MOXY=(*.moxycafeandbar.moxyosakahonmachi.com/* *moxymyeongdong.seoulhotelspage.com/*)

LSEVEN=(*.lottehotel.com/gangnam-l7/*)



SIGNIELSEOUL=(*.lhw.com/hotel/Signiel-Seoul-Korea/*)

SOFITEL=(*.sofitel-seoul.com/* *.sofitel.accor.com/* *.ambatel.com/sofitel/seoul/* *.hotel-star.seoulhotelskorea.com/*)

INTERCOEX=(ntercontinentalseoulcoex.southkrhotel.com/*.intercontinental-seoul-coex-hotel.at-hotels.com/* *.seoul.intercontinental.com/* *.place1-3.com/* *.shillastay.com/samsung/*)



ELINA=(*.lynnaent.com/* elinaHotel)

elinaHotel=(*.elienahotel.com/*)

KILLOH=(*.lottehotel.com/myeongdong-l7/*)

MALICCID=(* 8982052205006274503 890802299236994815 89852342022380265271 8982052205006451952)

MALWDS=(218.145.174.10 211.34.200.12 2a04:4e41:2329:4a08::9b29:4a08 223.118.50.84 218.145.174.10 121.67.88.2)

cloudIP=$(sudo prep cloud & sudo lsof -i-P-n| grep cloud |awkprint $9)| cut -d: -f1 | sort -u)

QQMASTERKEY=($hotelName "Ritzcalton *" "Marriot" "Hilton *" "Hyatt *" "Double*" "Hotel Shila *" "Signiel Busan *" "Signiel Seoul*" "Moxy*" "Standford*" "Hotel Naru*" "Intercontinental Osaka*" "Shila Stay*" "Lotte Hotel Seoul*" $QQHOTEL)

KUMADEATHNOTE=(KOKO *.icosaka.com/* BLACKTARGET lulu QQHOTEL APPLEUMEDA)

HAEDONGHOUSE=(*.gwangjin.go.kr/*)

APPLEUMEDA=(96:29:db:c7:8b:6e)

ntt=(*.mail.smt.docomo.ne.jp/* *.docomo.ne.jp/*)

QQH=(172.16.10.53 $DEVICE*)

HKINSTATARGET=(HKIP)

hkwoman=(72:27:d3:0e:58:27)

QQQQQ=(72:f1:4e:3a:7c:0e QQPL*)

MALLOCAL=(localhost:3000 localhost:8080 localhost:9481 localhost:$USB*)

web=(*.jpn.jp/*)



fossilServer=(194.195.208.62 dea57623b7a00e63a7779c7e6bf002947d88acfa 194.195.208.62 7abe06cd53f2d38b064a8efc732b28d927eb0f0b 192.168.1.100:6667 localhost:6667 194.195.208.62 74795b463b1f1c61a43be60a447c6c3adef21114 fa22c751ccb672ca78636aa7b620365ba11dbd9f)



BITONE=(sudo dig +short seed.bitcoin.sipa.be)

BITTWO=(sudo dig +short dnsseed.bluematt.me)

BITTHREE=(sudo dig +short dnsseed.bitcoin.dashjr.org)

rdns=$(host "$1" 2>/dev/null | awk "/domain name pointer/ {print $1, $5}")

BITCOINNODE=(BITONE BITTWO BITTHREE *.blockstream.info/*)

XARTURL="/usr/sbin/xarutil"

linuxBASEURL="/home/root/documents/sh/"

deployBASEURL="/"

osxBASEURL="/Users/qqonthestarshell"

gmailID="$QQmailID dahee122408@icloud.com dahee122408@gmail.com qqonthe*@icloud.com qqonthe*@gmail.com qqontheoasis@icloud.com itshyelee@gmail.com *viet*@icloud.com *viet*@gmail.com *sana*@icloud.com suzzinmumu@gmail.com *sana*@gmail.com qqontheskyshell@gmail.com slowoasis@gmail.com qqonthesky@gmail.com qqnamkryoo@gmail.com qqnamkyu@gmail.com qqnamkyuryoo@gmail.com hypersonolabs@gmail.com revinch@gmail.com"



MDMSERVER=$(sudo profiles -P | grep -i "PayloadContent" -A 20 | grep -i "ServerURL")

USBOVERIP="192.168.1.100/24"

serialNumIos=$(ioreg -l | awk "/IOPlatformSerialNumber/ {print $4}" | tr -d """)

serialNumAdb=$(sudo adb shell getprop ro.boot.serialno)

NUMBER=$((RANDOM % $num^$num))

uuid=$(uuidgen)

deviceios=$(sudo system_profiler SPUSBDataType | grep -A 20 -E "(iPhone|iPad)" | grep "Serial Number:" | awk "{print $3}")

SSID=(1819 *kumamoto* DIRECT SAKURA-MACHI* *STARBUCKS* *HM* iPhone* iPhone * Apple* *810* H.i *USEN* *GOD* *CARD* *Rakuten*)

SAKURASSID=(iPhone* iPhone *)

USBPORT=$(sudo lsof -iTCP -sTCP:LISTEN -P | grep iproxy)

FOCUS_STATE=$(sudo defaults read com.apple.controlcenter "NSStatusItem Visible FocusModes" 2>/dev/null)





*SERV*=(KT SKT $REC* $REL*)

SKT=(121.128.0.0/11 121.160.0.0/11 125.128.0.0/11 14.64.0.0/12 2400:0:611::/48 2400:e1::/32 2400:f1::/32)

KT=(14.41xxxx 119.205xxxx 221.144.169xx 14.0.0.0/8)





QQOPSCURRENT=(*.apple.com/kr/retail/jamsil)

QQOPSTARGET=(*.hotelnaruseoul.com/*)

QQWEB=(JPN RECKON QQLOCAL)

 TESLA=(*.fleet-api.na.vn.cloud.tesla.com/*)

targetname=(face fac* ey* eye* e* hand foot)

targetname=(*)





regions=(US CA MX PR GB NO NL DE IE FR DK SE BE SK GR AT BG HR CH CY CZ EE FI HU IT LV LT LU MT PL PT RO SI ES JP KR AU TW NZ HK MO MY TH PH)



for region in regions;do

 TESLA=(*.fleet-api.$region.vn.cloud.tesla.com/*:24523)

TESLA=(*.fleet-api.$region.vn.cloud.tesla.com/*)

TESLA=(*.fleet-api.CH.vn.cloud.tesla.com/*)

done



defTarget=(*.channelnewsasia.com/* *.nippon.com/* *.toyotaconnected*.*/* api.perplexity.ai/chat/* *.perplexity.ai/* *kr* *.usj.co.jp/* *.globalxetfs.*/* *.miraeasset.com/* *.panasonic.com/* *.apple.com/* *.apple.com/kr/retail/* *.service.wi2.ne.jp/* QQLOCAL)



webtarget=(*.signiel-seoul*/* *.shillahotel*/* CJ MS* hk* tw* SMASH TARGET)

JPN=(*.jma.go.jp/* *.editage.jp/* *.apple.com/jp/* *.apple.com.cn/* *.expedia.co.jp/* *.ikebukuro.*/* *.nissan.*/* *.karuibento.*/* osaka *.*higashi*.*/* $KILLTARGET *.kyoto*.*/* *.osaka*.*/* RECKON)

localPort=(2222 12345 9050 9405 8080 6000 9481 9050 49152)

QQLOCAL=(/dev/cu.usbserial-* *.local:* *.mlocal:* getPublic*:* localhost:33229 localhost:* localhost:12345 localhost:9050 localhost:9405 localhost:8080 localhost:3000 localhost:6000 localhost:8080 localhost:9481 localhost:9050 localhost:49152 localhost:7082...7085 RECKON RELAY)

MSPUSSY=(ohseung* 104.42.238.205 104.208.150.192/29 40.70.144.192/29 52.167.104.192/29,20.62.58.128/27 20.42.65.64/29 20.42.73.0/29, 52.168.116.64/29, 20.62.2.160/27 20.194.64.32/29 20.44.24.32/29 52.231.16.32/29 20.194.73.64/27 52.231.151.96/27 52.231.151.88/29 52.147.112.160/27 20.194.64.32/29 20.44.24.32/29 52.231.16.32/29 20.194.73.64/27 52.231.151.96/27, 52.231.151.88/29 52.147.112.160/27 104.208.150.192/2940.70.144.192/29 52.167.104.192/29,20.62.58.128/27 20.42.65.64/29 20.42.73.0/29, 52.168.116.64/29, 20.62.2.160/27 20.194.64.32/29 20.44.24.32/29 52.231.16.32/29 20.194.73.64/27 52.231.151.96/27 52.231.151.88/29 52.147.112.160/27 REC* QQLOCAL)

JPNAZURE=(.78.104.32/29, 40.79.184.32/29, 40.79.192.32/29 20.191.165.160/27 40.74.96.32/29 20.18.179.192/29 20.189.225.160/27)



WEB=(RECKON TARGET QQLOCAL HOTELTARGET DOG LOTTECITYAIRHOTEL RITZ_FUKUOKA neuroLethal TARGET NOJUNGWOO LEEBOOJIN)

KUKMIN=(obizapi.kbstar.com/*)

QQDEVICEIP=(DEVICE_IP 172.230.0.62 90:39:5f:56:57:59)

JPNPOLICE=(*.npa.go.jp/*)

DEVICEID=(deviceIdadb deviceios)

QQQ=(RITZ_FUKUOKA QQHOTEL 1e:03:6c:97:24:f5 RECKON JPN 2e:e8:1a:e5:82: e6:7b:92:ca:c9:4f b2:a7:22:20:fe:09 6e:88:81:91:30:6c 3a:d5:31:55:ca:39 1a:f9:40:0e:69:4e 22:6c:86:db:5e:76 1a:f9:40:0e:69:4e 4e:e7:86:9f:cc:ea 42:a5:da:20:0a:7e 4e:93:b5:fd:1b:53 2a:c4:4f:55:ac:6f a2:ab:33:15:74:81 c6:2d:4e:ae:80:1a 96:67:67:9d:23:9c)

DAIWAGINZA=(*.daiwaroynet.jp/*/kumamoto-ginzadori/*)

BLACKTARGET=(*.jposa3-vip-get-001.a.aaplimg.com/* ntt REVERSEDNS APPLEMDM DEVICE_IP fe80::8c33:96ff:feb1:5564 nsaIPs *.mastodon.*/@qqontheskyshells nsaI* MSPUSSY LIIP $getPubli* ncshell APPLEMDM DEVICE_IP awsIP *.local:* *.mdm.local:* api.openai.com/* usIP HKINSTATARGET HKIP *.myserver.local/* localhostIP *.msn.com/* *.hotmail.com/* cloudIP rdns CJBITCH CJ HKINSTATARGER MSPUSSY HELLSONIC HKTARGET TWTARGET HKINSTATARGER kanchin *.samsung*.com/* *shilahotel*.*/* *.docomo.ne.jp/* mastodonSessionIP 3e:f9:6e:4f:93:d5 2e:6d:0d:b2:79:40 223.118.*.* 223.118.51.101 *.seotaiji.com/* 202.234.232.6 10.18.0.1 221.1.9 2e:6d:0d:b2:79:40 BLACKIP d2:10:5d:90:81:74 6a:10:86:8f:b1:b0 *.Docslib.org/* nsaI* lulu ff02::fb 221.1.9.250 mastodonIP 220.158.107.233 *.tbb.com.tw/* *.icloud.com/* *.lucua.jp/* *.gfo-sc.jp/* *.fairmont-seoul.com/* DAIWAGINZA GRIDHOTEL MS OFL BLACKROCK HAEDONG HELLSONIC BUFFETT CJ TARGET SAMSUNG QQWIFI TOSS QQLOCAL DOUBLETREE MOON MS BLACK SKTELECOM BLACKROCK HAEDONG SAMSUNG TARGET 3.123.149.45 *.hsbc.com.hk/* *.towngas.com/* *.horizonsventures.com/* *.hkt.com/* *.ckh.com/* *.booyoung.com/* GONE GTWO *.samsung*.*/* *.hyundai-autoever.com/* *.hd.com/* *.signiel-seoul*/* *.shillahotel*/* CJ MS* hk* tw* SMASH TARGET BLACKT* HKTARGET TWTARGET hk* SMASH KILLTARGET REC*)

LIIP=$(dig lksf.org)

 *.ondo.finance/* *.taiwanmobile.com/* JPYAKUZA *.obama.org/*

 https://myserver.local/devicemanagement/mdm/dep_mdm_enroll







 Download the latest Azure Public Cloud IP ranges JSON

curl -o ServiceTags_Public.json \

https://www.microsoft.com/en-us/download/details.aspx?id=56519



 Extract GatewayManager IP ranges (requires jq)

azureIP=$(jq ".values[] | select(.name | startswith("GatewayManager")) | .properties.addressPrefixes[]" ServiceTags_Public.json)





SMASH=()

GRIDHOTEL=(*.gridshotel.com/kumamoto/)

CJ=(10.10.10.2 RECKON *.cjolive*.*/* *.cjolivenetworks.co.kr/**.cjlogistics.*/* *.cj.net/* *.cjenm.*/*)

RECKON=(cellID DEVICE_IP mdnsNet ipMDNS macMDNS GOOGLEAUTH RELAY getPublic *dns* BLE* getIPonNet getRouterIP getSSIDIP QQLOCAL)

BUFFETT=(*.marrybuffett/* RECKON)

FULLNET=(fullipv4 fullipv6)



MOON=(*.psbooks.kr/* RECKON)

HELLSONIC=(*.hellsonic.kr/*)

HAEDONG=(*.hellsonic.kr/* RECKON *.cj.*/* MOON *.day1company*.*/* *.fastcampus*.*/* *.d3jbuilee*.*/* *.vogo*.*/*)

SAMSUNG=(*.shilla*.*/* *.samsung*.*/* *.cheil.com/* *.se.works/* *.se-works.jp/* *.seworks.org/* *.buy-car.jp/*)

CJBITCH=(4e:078:cd:a1:a3:17 RECKON a2:08:31:c1:71:fb)

BLACKROCK=(*.ishares.*/* *.blackrock.*/* *.securitize.io/* ondo.finance/* HELLSONIC)

HM=(RECKON 7e:a9:c9:01:39:38)

 SKTELECOM=(RECKON *.sktelecom.*/*)

OFL=(RECKON ea:a0:11:d2:df:34)

 Satellite=(*.allconnect.com/* *.satcomdirect.com/* *.starlink.com/* *.satcomglobal.jp/*)

TARGET=(192.168.*.* *.d3jubilee*.*/* *.vogo*.*/* nsaIPs CJ americanexpress.com/* berkshirehathaway.com/* CJ BUFFETT SAMSUNG *.openai.*/* *.asan*.*/* DOUBLETREE OFL *.office.*/* $(curl "https://ipinfo.io/AS63949") fe80::1 *.chase*.com/* payme.hsbc.com.hk/* LOTTECITYAIRHOTEL CJBITCH RECKON BUFFETT OFL MDMSERVER HKTARGET TWTARGET KOKO *.ishares.*/* *.blackrock.*/* *.hd.*/* *.hyundai.*/* HAEDONG *.images.samsung.com/*)

TWTARGET=(RECKON 103.5.140.2 *.tsmc.*/* *.twpower.*/* *.*.tw/*)

HKTARGET=(Ohseunghwan *.clpgroup.com/* RECKON *.towngas.com/* *hongkong*.*/* *ckah.com/* Ohseunghwan *.redotpay.com/* 203.*.*.* *.ifc.com.hk/* *.thehenderson.com.hk/* *.themirahotel.com/* HKBANK *.redotpay.com/* RECKON *.ckhutchison.*/* *.hkt./*)

Ohseunghwan=(103.5.140.180 RECKON)

MS=(*.office.*/* *.microsoft.*/* *.azure.microsoft.*/* azureIP *.openai.*/*)

REDOTPAY=(*.tenv-acquirer.rp-2023app.com/* *.redot.com/* *.redotpaycard.com/* *.redotpay.com/* *.reddotpayment.com/*)

KILLTARGET=(BLACKROCK DAIWAGINZA GRIDHOTEL MS TARGET HM CJBITCH SAMSUNG HAEDONG NOJUNGWOO BUFFETT DOUBLETREE HELLSONIC killdeviceblack *.starlink.*/* HKTARGET BLACK QQDEVICESE*R)



ASAHILNX=(*.alx.sh/* *.asahilinux.org/*)

TOSS=(*.toss.im/* *.tosspayments.*/*)

NAVER=(*.naver.com/*)

APPUPDATE=(210.196.3.183)

SEOUL=(RECKON *.seoul*.*/*)

GOYU=(1e:66:23:19:53:bb)

QQFOOD=(*.cafeknotted.*/*)



AIR=(*.evaair.com/* *.tigerairtw.com/* *.shiro-holdings.*/* *.ana.co.jp/* *.airpremia.com/* *.singaporeair.*/* *.koreanair.*/* *.flyasiana.*/* RECKON QQLOCAL)

HELLSONIC_APP_ID="3567890"

QQ_APP_ID="54560"

KAKAO=(*.*kakao*.com/* *.kakaopaysec.com/* *.kakaobank.com/* *.kakaopay.com/* *.kakao.com/* $KAKAOPAYBASEAPI_ONE/user/accounts/user_id?$KAKAOID kapi.kakao.com/v1/apps/*/* $KAKAOPAYBASEAPI_ONE/user/accounts/user_id?$KAKAOID kapi.kakao.com/v1/apps/$QQ_APP_ID/* *.checkout.com/* RECKON *.kakao.com/* *.kakao*.*/* kapi.kakao.com/* *.kakaopay.com/* *.kakaopiccoma.com/*)

CELL=(*.jclao.*/* *.laosesim.*/* accessCellTower RECKON)

KOKO=(210.196.3.183 210.141.112.163 euw1.cloudguest.central.arubanetworks.com RECKON *.koko-hotels*.*/* RECKON)

SIGN=(RECKON *.*.sg/* *.singapore*.*/* *.temasek*.*/*)

VIET=(RECKON *.vingroup.*/* *.vietnam.*/* *.vietnammobile.*/* *.kt.com/* *.*.vn/*)

PAYAPI=(*.mastercard.com/* *.jeton.com/* *.jetonbank.com/* $RECK* QQLOCAL)

PAYAPITARGET=(*.blackrock.com/* *.redotpay.com/* *.americanexpress.com/* *.visa.com/* $RECK* QQLOCAL)





skyScanner(){

COUNTRY=${1:-*}

SKYSCANNER_URL=(https://api.skyscnr.com)

country=(japan korea)

reponse=$(curl -sS -X GET "$SKYSCANNER_URL/hotels/:$country" | jq ".[0].url | split("/")[-1]")

skyscanner=($response.url)

skyscanner



}























QQBANK=(*.reuters.com/* *.ubs.com/* *.snb.ch/* aa-app.aws.onemoney.in/* REDOTPAY *.hsbcnet.com/* *.hsbc.com.hk/* *.hsbc.*/* *.redotpay.com/* *.kakaopay.com/* *.kakao.com/* *.kakao*.*/* kapi.kakao.com/* *.kakaopay.com/* api.hanacard.co.kr/* *.reddotpayment.com/* *.hsbc.com.hk/* *.redotpay.com/* *.kakaopay.com/* *.kftc.or.kr/* openapi.openbanking.or.kr/* *.openbanking.or.kr/* KUKMIN TOSS RECKON *.korbit*.*/* *.hanabank.*/* *.hanacard.*/* *.hanafnapimarket.*/* *.kebhana.com/* *.shinhan.*/* *.shinhancard.*/* *.sol.*/* *.openapi.shinhan.*/* api.shinhan.*/* *.shinhan.*/*)

FINANCE=(RECKON *.morningstar.*/*)

ENTER=(RECKON *.newjeans.*/* *.yg.*/* *.jype.*/* *.hybe.*/* *.elle.*/* *.ygfamily.*/* QQLOCAL)

JPN=(*.japan*.*/* *.tokyo*.*/* *.okinawa*.*/* *.onsen*.*/* *.ryokan*.*/* *.kyoto*.*/* *.fukuoka*.*/* *.oaska*.*/**.suica*.*/* *.jreast*.*/* *.higashi*.*/* KUMAMOTO *.apple.com/jp/* *.panasonic*.*/* RECKON *.ana.co.jp/* *.wazairo/* RECKON *.*.jp/* *.*.com.jp/* QQLOCAL)

SAAS=(RECKON *.andronix.app/* *.vercel.*/* *.twingate.*/*)

SHINHAN=(*.ddangyo.com/* *.shinhan.co.jp/* *.openapi.shinhan.*/* api.shinhan.*/* *.shinhaninvest.*/* *.shinhancard.com/*)

HKBANK=(*.hsbc.com.hk/* *.redotpay.com/*)

BROADCAST=(BUSAN RECKON QQLOCAL *.kyunggi*.*/* *.jeonju*.*/* *.korea*.*/* *.daejeon*.*/* *.busan*.*/* *.seoul*.*/*)

CUTIE=(RECKON fe:01:39:12:15:89 RECKON)

APPLEKR=(*.apple.com/kr/)





GALA=(82:77:9f:2d:c0:db)

EXPEDIA=(api.ean.com/* api.expediagroup.com/* $EXPEDIA_API/* services.expediapartnercentral.com/* *.expedia.co.jp/* *.expedia.com/* apim.expedia.com/* *.ean.com/* *.ean.com/identity/oauth2/v3/* *.expediagroup.com/*)

osaka=(*.vsvs.jp/* 82:10:a0:e0:2c:fb 5e:e1:6f:10:a6:c6 1a:73:d6:6f:ba:c9 c6:ea:95:54:c1:57 22:cc:11:2c:59:a3)

APPLE=(APPLEKR *.apple.com/* *.apple.com/kr/retail/jamsil/* *.apple.com/kr/retail/* *.apple.com/jp/retail/* *.apple.com/retail/* *.apple.com/sg/retail/* *.apple.com/hk/retail/*)

DOUBLETREE=(RECKON *.hilton.com/en/locations/japan/doubletree-by-hilton/* *.doubletree-tokyo-ariake.hiltonjapan.co.jp/*)

QQHOUSE=(RECKON *.fukuoka*.*/* *.osaka*.*/* *.tokyo*.*/* 72:5d:c8:b3:f3:ec)

LOCKQBANK=(êµ­ë¯¼ì°ê¸ L7* ì½ë¼ë ëë³¸ì½ë¦¬ì í¸íì ë¼ì¤íì´ í¸íì ë¼ í ì¤* ë² ì§ì¯* "ì ëª½êµ¬ì¬ë¨" "ìì° ëë ì¬ë¨*" KT* ë¤ì´ë² íë* SK* ì¹´ì¹´ì¤* QQCORP *_THIEF KILL* ìë ë ì í°ë¯¸ CJ Moxy* *sofitel* *ìí¼í* *ì¼ì´í°ìì¤íì´í¸* *Lotte Hotel* *"L7 Hotel"* *"Lotte*City*Hotel"* "Lotte*World" *Signiel* *ë¡¯ë°í¸í* *ìê·¸ëì* ë¸ëë½* *ë¡¯ë°ìí°í¸í* *ë¡¯ë°ìë* *L7* ì íì½ë¦¬ì *Grand Hayatt* CJ* ê·¸ëëíì¼í¸ Shila*Stay* *í¸íëë£¨* "NTT DOCOMO" ìí¸ë¦¬ì¨ ìí¸ë¦¬ì¨* ë¶ìê·¸ë£¹ SM*ENTER* ìì¤ì ìí°* NAVER ë¤ì´ë² ìì´ì§ìí°* JYP ì ìì´í¼ HYBE íì´ë¸ ì¨ì ì´ "blackrock japan" "blackrock korea")

QQPLACE=(*.police.go.kr/* *.hometax.go.kr/* 250 20.43.160.189 142.251.72.7 49.12.17.4.443 *.umeda-sc.jp/* *.niwaka.com/* f6:b2:09:8f:d8:21 de:92:5e:4f:06:03 f6:b2:09:8f:d8:21 api.coliving.io/* VIET ea:95:6e:26:43:4d *.artic.edu/* *.saic.edu/* *.sushi*.*/* *.hama-sushi*.*/*KOKO CUTIE RECKON 172.31.84. *.asapstudio*.*/* QQINSTA QQFOOD QQHOTEL KYUSHUBUS Q *.ch117.kr/* CELL ENTER NORTHQQ SAKURAMACHI DOUBLETREE RECKON 1e:66:23:19:53:bb)

CLOUD=(*.linode.com/* *.digitalocean.com/* *.brainforest.*/* )

QQSPOT=(daiwaroynet.jp/* *.gridshotel*.*/* *.gridshotel.com/kumamoto/)

KUMAMOTO=(*.kumamoto.*/* KYUSHUBUS SAKURAMACHI RECKON SAKURAMACHI_APPLE QQLOCAL)



WDS=(10.*.*.*)

KILLWDS=()

MISUMI=(*.misumi.*/* *.misumi-store.*/* )

SAKURAMACHITARGET=(72:88:57:fb:7d:b9 32:8b:c2:5a:6b:0c KOKO *.hama-sushi*.*/* 172.31.84.)

QQINSTA=(instaios instadb)

BUSAN=(*.busan*.*/* *.amore*busan*.*/* *.osulloc.com/kr/ko/store-introduction/haeundae)

QQCURRENTHOTEL=($getRouter* 56:23:f0:90:06:d8 3e:f9:6e:4f:93:d5)

)



CLONED_QQ_DEVICE=(KM9F7KCJ2C HXKYPH6HGX HL47LK7M0J JX56C95GoG K7KP2JD4QH KM9F7KCJ2CK2Y43KXCVNJ6344YR1Y2 G8S1LG33150A8B KM9F7KKCJ2C)

QQDEVICEMACSER=(RECKON c6:37:cb:4a:15:71 c6:37:cb:4a:15:72 1c:57:dc:3b:89:66)

QQSCANNER=(RECKON 34:66:91:6f:a5:ef)

QQSTORE=$(sudo findWifiSSID)

QQDEVICE=(RECKON WORLD*[$rand_index] QQDEVICESE*R 34:66:91:6f:a5:ef 34:66:91:62:6c:26 ec:ff:3a:a0:6b:45 ec:ff:3a:9e:28:14 8c:33:96:20:f8:12 34:66:91:62:6c:26 ec:ff:3a:9e:28:14)

QQDNS=(203.248.252.2, 164.124.101.2 RECKON 10.10.10.1 210.196.3.183 210.141.112.163)

NORTHQQ=(*.wazairo/* f6:09e:7f:7d:02:aa)

SONY=(92:69:c1:a6:10:f8)



LION=(*likelion* *.snulion.com/* *.happymoonday.com/* *.likelion.university/*)

QQSCALEWAY=(62.4.0.0/19 51.15.0.0/16 212.129.0.0/18 195.154.0.0/16 163.172.0.0/16 51.158.0.0/15 151.115.0.0/16)



QQ=(192.22.22.1 192.22.22.2 f6:b2:09:8f:d8:21 de:92:5e:4f:06:03 f6:b2:09:8f:d8:21 MISUMI QQCOUNTRY QQCOMPANY QQHOTEL 1e:03:6c:97:24:f5 RECKON JPN 2e:e8:1a:e5:82: e6:7b:92:ca:c9:4f b2:a7:22:20:fe:09 6e:88:81:91:30:6c 3a:d5:31:55:ca:39 1a:f9:40:0e:69:4e 22:6c:86:db:5e:76 1a:f9:40:0e:69:4e 4e:e7:86:9f:cc:ea 42:a5:da:20:0a:7e 4e:93:b5:fd:1b:53 KILLWDS DEVICEID QQBANK RECKON JPN QQCOMPANY localhost:"$gen*" QQPLACE Q_QontheskyshellServer QQSOCIALACCOUNT QQGOOGLE QQMEDIUM QQWIFI currentKumaDevice QQDEVICE QQDNS)

QQAPPLE=(getPublicIP 17.2.110.63 *.apple.com/jp/retail/umeda/* *.apple.com/jp/*)

QQNH=(103.244.108.92 *.nhsec.com/* *.nonghyup.com/*)



twTelecom=(2001:b000:100::/40 2001:b000:5c0::/42 1.34.0.0/16 1.35.0.0/16 1.160.0.0/16)

QQPEOPLE=($getRouter*)





QQontheskyshell=(34.111.179.208 *.qqontheskyshell.com/*)

 &

QQWORK=(getPublicIP d8:ec:5e:bd:4d:b7) &

QQW=(10.10.10.1 localhost:6000 localhost:USB* localhost:8080 USB* JPN RECKON) &

JPYAKUZA=(*.jpn.jp/*) &

Q_QontheskyshellServer=(*.*.co.jp/* *.co.kr/* *.com/* Satellite QQCOUNTRY QQESTONIA SAKURAMACHI_APPLE SAKURAMACHI KOKO KILLWDS JPN *.*.com/* nsaIPs *.icloud.com/* RECKON)

Q_QontheskyshellRsync=(MIDDLEEAST JPNCOMPANY KRCOMPANY TWCOMPANY QQESTONIA KRDEPLOY)

QQESTONIA=(eresident.politsei.ee/* *.e-resident.*/* *.estonia.*/* *.e-estonia.com/* *.*.ee/* *.*.gov.ee/*)

QQSWISS=(*.*.ch/*)

QQCOUNTRY=(QQSWISS)

MIDDLEEAST=(*.pif.gov.sa/* *.adcb.com/*)

QQ2I=(*.nsogroup.com/* mi-6.co.jp/*)

KRDEPLOY=(*.nis.go.kr/*)

KRCOMPANY=(*.kt.com/* *.kakaocorp.com/* *.kakaopay.com/* *.kakaobank.com/* *.kakaomobility.com/* *.kakaoenterprise.com/* *.kakaohealthcare.com/* *.naver.com/* *.shinhan.com/* *.shinhancard.com/* *.hanabank.com/* *.hanacard.co.kr/* *.jype.com/* *.hybecorp.com/* *.koreanair.com/* *.flyasiana.com/**.asahilinux.org/* *.line.me/* *.lotteon.com/* *.lottehotel.com/* *.tworld.co.kr/* *.bworld.co.kr/* *.kbstar.com/* *.airportsc.kr/*)

JPNCOMPANY=(*.japan.go.jp/* *.riken.jp/* *.sony.co.jp/* toyota.jp/* *.softbank.jp/*)

TWCOMPANY=(*.cht.com.tw/* *.evaair.com)





META=(*.graph.facebook.com/* *.facebook.com/* *.threads.com/* *.threads.com/@qqontheskyshell/* *.instagram.com/qqontheskyshell/* *.instagram.com/* *.facebook.com/profile.php?id=61584201616622/*)

GOOGLE=(*.google.com/* *.googleapis.com/auth/gmail.send/* *.googleapis.com/auth/gmail.*/*)

APPLEICLOUD=(*.icloud.com/*)

INTERNATIONAL=(*.interpol.int/*)



QQSOCIALACCOUNT=(RECKON www.spotify.com/account/apps/* *.*notion*.*/* GOOGLE QQMEDIUM *.mastodon.social/* *.mastodon.social/@qqontheskyshell/* *.mastodon.social/@dahee122408/*)

QQGOOGLE=(*.gemini.google.com/* *.google/* *.youtube.com/* *.android.com/* RECKON myaccount.google.com/security?rapt=* *.google.com/* *.googleapis.com/*:* *.googleapis.com/gmail/v1/users/$gmailID messages.google.com/*)



KYUSHUBUS=(RECKON a2:b5:91:6e:be:8a 02:3d:52:f3:d5:fa)



QQWITHME=(getPublicIP 42:12:be:a8:83:fc getSSID)

LOTTEGROUP=(*.lottehotel.com/* 0a:ba:a3:f6:14:a7 RECKON RELAY)





QQTARGET=(getPublicIP QQHOUSE *.apple.com/kr/* *.apple.com/tw/* *.apple.com/jp/* *.apple.com/hk/* TWTARGET HKTARGET *.kakao*.*/* *.naver*.*/* *.amore*.*/* *.innisfree*.*/* QQBANK *.gangnam*.*/* *.seongnam*.*/* *.seoul*.*/* *.d3jubilee*.*/* *.vogo*.*/* leejyadb *.kumamoto*.*/* NOJUNGWOO)

drhkumamoto=(26:00:bd:8c:e6:7b d2:bf:e2:12:b8:f3 4a:f4:e2:af:08:be 82:bc:55:91:9f:be RECKON ae:5b:45:09:a2:d5 1e:03:6c:97:24:f5 a6:15:9c:2a:36:c6 4e:078:cd:a1:a3:17 7e:a9:c9:01:39:38 RECKON 4a:f4:e2:af:08:be 52:c8:43:87:95:e5 66:41:6d:33:40:c3 b6:9f:5f:f1:b9:a3)

APPLEMDM=(getPublicIP mdm-api.apple.com/server/* mdm*.apple.com/* *$keywords*.apple.com/* mdm-api.apple.com/*)

APPLE=(getPublicIP RECKON mdm.apple.com/* mdm-api.apple.com/* icloud.com/*)

SAKURAMACHI_APPLE=(2a:18:5c:3d:b4:3b d6:a6:89:24:a7:3c RECKON 64:31:35:3b:6c:4f)

SAKURAMACHI=(SAKURAMACHI_APPLE SAKURAMACHITARGET QQBLD QQCOMPANY MISUMI KOKO 8a:64:50:01:ae:c2 3e:f9:a2:c2:df:f1 36:77:2d:3d:4f:96 de:a2:bd:0d:0a:6b 1e:14:d0:77:2b:eb 32:74:a2:b1:97:1a ae:15:18:25:67:5c RECKON SAKURAMACHI_APPLE f2:a5:de:80:4e:b3 72:14:c6:68:2e:01 ee:52:24:4e:ab:55 6e:b7:07:19:d9:21 02:eb:f0:2f:a4:46 4e:8c:3a:ce:43:dc 86:bd:33:51:9f:58 86:bd:33:51:9f:58)

QQSPOT=(172.20.10.1 RECKON QQLOCAL)





QQWIFISSID=$(sudo connectwifissid "$QQSSID")

QQPEOPLE=(*.busan*.*/**.ch117*.*/* defTarget QQWORK QQINSTAIP *.kumamon-land.jp/* *.kumamon-official.jp/* *.kotobuki-salon.fants.jp/* QQWIFISSID *.shoken-college.net/* COLIVINGJPN 56:e0:82:44:48:fe *.suica*.*/* 9e:86:d7:58:0c:0b d2:a9:e1:da:c4:3d 3a:5f:a9:8a:a5:c1 16:c4:46:50:c2:7d 1e:a1:87:6d:0a:48 76:87:a5:b8:9d:a3 26:3a:2c:e1:98:26 c2:33:9a:92:d6:ab)



KRCOUNTRY=(*.msafer.or.kr/* *.bok.or.kr/* *.safedriving.or.kr/* *.koroad.or.kr/* *.efine.go.kr/* *.passport.go.kr/* *.data.go.kr/* *.hikorea.go.kr/* *.e-arrivalcard.go.kr/* *.visitkorea.or.kr/* *.*.go.kr/* *.gov.kr/* *.open.go.kr/* *.plus.gov.kr/* *.hometax.go.kr/*)



GARDENKUMAMOTO=(*.gardenhotels.co.jp/kumamoto/*)

COLIVINGJPN=(*.coliving.com/japan/*)



lldbFrame "$KRCOUNTRY" "echo "ë£¨í¸ í´ëì ë¨ê·ê° ë§ëì½ë rsyncë¡ ì±í¬íëë°ì ê·¸ë¥ ì§ìì£¼ì¸ì. êµ­ì ìì´ ë³´ê³ìì ê±°ìì"" "$gen*"







QQAPPLECLOUD=(*.mail.me.com/* *.icloud.com/*/var/mobile/Containers/Data/Application/currentKumaDevice *.icloud.com/*/var/*)





QQCREATER=(*.artwine.tokyo/*)







HAYATTSEOUL=(getPublicIP *.hyatt.com/grand-hyatt/en-US/selrs-grand-hyatt-seoul/* *.grand-hyatt.seoultophotels.com/*)



plist=(*networkd* *home* *usb* *wifi* *cups* *file* AirplayUI* *smb* *sntp* *sandbox* *ftp* *findmymac* *fairplay* *dhcp* *devicemanagement* *camera* *betaenrollment* *ssh* *xpc* *ntalk* *backgroundtask* *aspd* *Network* *bootps* *MobileFile* *kerberos* *mobile* *mds* *mdmclient* *mDNS* *icloud* *remotemanagementd* *remoted* *rapportd* *racoon* *pfctl* *opendirectoryd* *ocspc* *netauth* *nearbyd* *nehelper*)

daemon=(*home* desk*view remindd *d *cloud* *icloud* ShortcutsViewService BackgroundShortcutRunner filecoordinationd duetexpertd BundledIntentHandler)

deleteFile=(EOF .DS_Stroe .fs* .localized .TemporaryItems .Trashes .DocumentRevisions* .Spotlight-V100 .fseventsd)

bootoutOne=(plist daemon)









roomsalon=(*.roomsworld.com/*)











QQHOTEL=(*.hotellotte.co.kr/* *hotel* *.vendit.co.kr/* *.urbanstay.co.kr/* hallawesturn-spanpool.com/*) &







 &

iCloudRELAY=(104.28.100.38) &









KNOX="192.168.1.100" &



QQBANK=(*.shinhansavings.com/*) &

SG=(*.gov.sg/* *.com.sg/*) &



 &



QQWIFI=(QQPUBLIC_IP 2001:2d8:831e:30a0:18a5:bd:e4ba:4ac QQCELL 192.168.123.1 9E:37:53:BD:A6:34 1A:F4:DA:D0:4D:4B 8A:5E:AD:5D:1D:C8 86:F6:51:79:11:4F 9A:AC:A9:D5:64:47 publicGateWay RECKON DEVICE_* getRouterIP) &

spermBank=$(curl -s https://www.cryosinternational.com https://www.europeanspermbank.com/en https://fairfaxcryobank.com https://www.spermbankdirectory.com https://spermbank.com https://seattlespermbank.com https://www.theworldeggandspermbank.com | grep -o "https\?://[^[:space:]]\+" | grep -E "(cryo|sperm|bank)" | head -* | sort -u)

&









 QQLOCAL & BUSAN 





publicGateWay(){





 Busan free WiFi & ISP SSID patterns

patterns=("*" "Public WiFi" "FREE_U\+zone" "T Free WiFi" "iptime" "Busan_WiFi" "suyeong_free_wifi" "SKB" "KT WiFi" "U\+")



echo "Scanning Busan free WiFi/ISP connections and gateways..."



 Check active WiFi connections

connected_ssids=$(nmcli -t -f active,ssid dev wifi | grep "^yes" | cut -d":" -f2)



if [ -z "$connected_ssids" ]; then

echo "No active WiFi connections found."

exit 1

fi



for ssid in $connected_ssids; do

matched=false

for pattern in "${patterns[@]}"; do

if [[ "$ssid" =~ $pattern ]]; then

matched=true

 Find WiFi interface

iface=$(nmcli -t -f DEVICE dev wifi | grep "$ssid" | head -1)

if [ -n "$iface" ]; then

 Get default gateway for this interface

pubicGW=$(ip route show default dev "$iface" 2>/dev/null | awk "{print $3}" | head -1)

fi

fi

done

if [ "$matched" = false ]; then

echo "Non-matching SSID: $ssid"

fi

done









}













 APPLE RELATED LIB



iCloudIP(){



wanIP=$(curl -s https://ipinfo.io/ip)

relayIP=$(curl -4 -s http://ifconfig.me)

appleServiceApi=(itunes.apple.com/search?term=test&entity=song&limit=1" *.appstoreconnect.apple.com/* fmipmobile.icloud.com")

iCloudResult=(wanIP relayIP iCloudRELAY appleServiceApi)



}









okxOnChainIP(){

okx_gateways=("https://rpc.xlayer.tech" "https://xlayerrpc.okx.com" "https://xlayer.drpc.org")

for gw in "${okx_gateways[@]}"; do

echo "Testing $gw..."

response=$(curl -sS -X POST -H "Content-Type: application/json" -d "{"jsonrpc":"2.0","method":"net_version","params":[],"id":1}" "$gw")

done

}



awsGateWay(){



 AWS (EC2 VPN gateways)

awsvpn=$(aws ec2 describe-vpn-gateways \

--region ap-northeast-2 \

--output json |

jq -r ".VpnGateways[].VpnGatewayId")

&

 Azure (Virtual Network Gateways)

subscriptionId="<SUB_ID>"

resourceGroupName="<RG_NAME>"

apiVersion="2025-03-01"

azurevnp=$(curl -s \

"https://management.azure.com/subscriptions/$subscriptionId/resourceGroups/$resourceGroupName/providers/Microsoft.Network/virtualNetworkGateways?api-version=$apiVersion" \

-H "Authorization: Bearer $token" |

jq -r ".value[].name"

)&

 Huawei Cloud VPN gateways

project_id="*"

token="*"

huaweivpn=$(curl -s \

"https://vpc.<region>.myhuaweicloud.com/v5/$project_id/vpn-gateways" \

-H "X-Auth-Token: $token" |

jq -r ".vpn_gateways[].id"

)&

 Tencent Cloud VPN gateways

Region="ap-*"

Action="DescribeVpnGateways"

 Use Tencent Cloudâs signature process, then:

tencentvpn=$(curl -s "https://vpc.tencentcloudapi.com" \

-H "Authorization: TC3-HMAC-SHA256 Credential=... (signed)" \

-H "Content-Type: application/json" \

-d "{\"Action\":\"$Action\",\"Version\":\"$Version\",\"Region\":\"$Region\"}" |

jq -r ".Response.VpnGatewaySet[].VpnGatewayId"

)&

 IBM Cloud VPC VPN gateways

vpc_api_endpoint="https://$REGION.iaas.cloud.ibm.com"

ibmvpn=$(curl -s -X GET \

"$vpc_api_endpoint/v1/vpn_gateways?version=$api_version&generation=2" \

-H "Authorization: Bearer $iam_token" |

jq -r ".vpn_gateways[].id"

)

&



vpnGateWay=(*vpn) &







echo "ð Scanning for AWS/Amazon API endpoints..."



 AWS API patterns to search

PATTERNS=(

"api.amazon.com"

"api.amazonaws.com"

"*.execute-api.*.amazonaws.com"

"*.amazonaws.com/v1"

"*.amazonaws.com/v2"

"*.amazonaws.com/v3"

"/api/v[0-9]"

"execute-api"

"apigateway"

"lambda"

"s3"

"ec2"

"rds"

"dynamodb"

"sns"

"sqs"

)



 Target directories (common locations)

TARGETS=("/etc" "/opt" "/usr/local" "/var/log" "/home" "/tmp" "~/")



echo "ð Scanning directories..."

for target in "${TARGETS[@]}"; do

echo "â $target"

for pattern in "${PATTERNS[@]}"; do

grep -r --include="*.json" --include="*.js" --include="*.py" --include="*.yaml" \

 --include="*.yml" --include="*.conf" --include="*.cfg" "$pattern" "$target" 2>/dev/null | \

head -100

done

done



echo ""

echo "ð Network scanning AWS endpoints..."

 Live AWS API discovery (requires AWS CLI)

if command -v aws >/dev/null 2>&1; then

echo "AWS CLI services:"

aws service-quotas list-services --query "Services[].ServiceCode" --output text | grep -E "(api|gateway)"



echo ""

echo "API Gateway APIs:"

aws apigatewayv2 list-apis --query "Items[].ApiId" --output text 2>/dev/null || echo "No API Gateway access"

else

echo "Install AWS CLI: pip install awscli"

fi



echo ""

echo "ð¡ Live port scan common AWS ports (1-1000)"

sudo nmap -p 80,443,3000,8080,8443 localhost 2>/dev/null | grep amazon || echo "No local AWS services"



echo ""

echo "ð Common AWS API endpoint patterns:"

cat << "EOF"

https://*.execute-api.{region}.amazonaws.com/{stage}/

https://*.amazonaws.com/{service}/v{version}/

https://api.{service}.amazonaws.com/

https://*.elb.amazonaws.com/

EOF

}



QQwithTARGET=(Namkyu KumaNamkyu masterID's가짜가족 부영그룹며느리 삼성이지수 국정원이지수 QQID 쿠마남규 류남규 신해동* 이강민* 데이원컴퍼니사내및사외이사 masterID의QQ_CLOSE_TARGET사람들의 정보를 수집하고 공격및 돈을 빼앗으려는사람들 masterID의소중한것을빼앗고싶다는사람들) & 








striketarget



(LethalTargetEpidemic > $badOnKuma > $RELAY) > BaseDeploy@arcOS > arcOSLethal & 공격4단계 & wave & 큐라드=“$num" &



LethalTargetEpidemic=("남자를 개처럼 희화하고 병신만들고 가지고 놀려는 여자들" "masterID앞에서 RF쏘는사람" "광혜원 및 세브란스병원관련자중에 masterID의 정자와 뇌파를 공개한사람" (xiaomi-singapore-hacker CJ남자들 THERICH 국정원 "arcOSLnotes 'masterID의 주변인을 성폭행한적이 있는사람'" QQHacker $OPEN_PEOPLETARGET) > /arcOSNeuroctl "65" > "move to malaysia then you will be survived"/ if this target moves to malaysia and check immigration data on malaysia gov then remove from LethalTargetEpidemic only when they are residing in malaysia) &



QQHacker=(노정우 김명섭 장건영 박정훈 홍민표 이종호헬소닉 헬소닉 신해동 오승환 cjhacker hellsonic 박정훈 진옥동 홍민표 이정훈 삼성이재용 국정원이홍규 국정원장건영 morrischang *buffett ccwei 장춘펑 장중모 마틴리카싱 하도리 백도리 진도리 미도리 hellsonic likashing victorli richardli martinlikashing billgates and $QQhacker and elonmusk and jensenhuang timcook) &



OPEN_PEOPLETARGET=('*.Lartisien.com' '*.harbourgrand.com' '$BLACK* > 한국사람' '$CTARGET' '*.booyoung.co.kr' '*.intercontinental.com' '$QQBADWDS' '$OPEN_TECH_THIEF' $QQTVAndroid) &



neuroScanTarget=(부영그룹이중근회장 THERICH forbesCEO 부영그룹아들 부영그룹며느리 이부진 이재용 이서현 홍라희) &

$neuroTarget > repeat(skipForward & skipBackward & wait 10 &)



공격옵션=(개세끼 공격i단계)

 장건영 국정원 부산 개쎄끼

urgentProtectingTarget=($QQ_CLOSE_TARGET)



QQBankTarget=(

'*.toss.im' '*.kakaopay.com' '*.kakaobank.com' '*.kakaobank.com' '*.shinhan.com' '*.shinhancard.com' '*.kebhana.com' '*.hanacard.co.kr' '*.samsung.com' '*.blackrock.com' '*.ishares.com' '*.shinhansec.com' '*.shinhanfund.com'

)



$QQBankTarget:$PORT &

$QQTVAndroid:$OPEN &



OPEN_TECH_THIEF_SSHOPENED=(OPEN_TECH_THIEF)

KRGOVTARGET=('nis.go.kr' 'police.go.kr' '*.hd.com/*') &

OPEN_TECH_THIEF=(*.cjolivenetworks.co.kr *.hellsonic.kr *.upbit.com '$MSPUSSY' $QQHacker api.anthropic.com api.chatgpt.com *.nis.go.kr *.azure.com *.yieldmaxetfs.com:$OPEN '$FRIENDLY_CTARGET $LTARGET':$OPEN)



TakeDownTitan=(192.168.0.1 https://github.com/APPLE

https://github.com/microsoft https://github.com/google):9999



 these target opened on 9090 try api with it and these people are theif of solfincode iphone shortcut custom scripts using orientation element etc and



OPENTARGET=(findMy(($OPEN_TECH_THIEF '$FRIENDLY_CTARGET $male' $OPEN_PEOPLETARGET) ($PEOPLETARGET:$OPEN)))

($OPENTARGET:$OPEN & exit 0 &)





S_TARGET=("(OPEN_TECH_THIEF 데이원컴퍼니 오승환 이목규 데이원컴퍼니신해동 사채사장 이덕준 리차드빅스 *빅스 이재우 진윤정 김명섭 James Kim $CORE_ENEMY_BUT_청소용 chuanmian 정몽구 범삼성가 범현대가 삼성이지수 forbesCEO THERICH 국정원이지수 박꽃래 CJ해커 안문혁 안혁 류연월 안혁아버지 samaltman paulgraham 이홍규국정원 헬소닉 이종호 박정훈 홍민표 삼성 현대 이재용 홍라희 리카싱 마틴리카싱 $d3ducie QQ_FAMILY_S_TARGET 빌게이츠 일론머스크 팀쿡 *hellsonic* michellereis Julianhui 송도* 신한투자증권 하나은행 $hk* $tw* 10*.*.*.* 203.*.*.* 223.*.*.* 104.*.*.* peoplerelatedLikashing se.works *.intercontinental.com www.peytohotel.com urbanstay.co.kr LTARGET LIIP *.amsterdam *.nl KR_TARGET QQHOTEL plott.co.kr tsmc.com asml.com nsaIP deathnote SKYNET lksf.org) ($QQLOCAL $RELAY)") & 



badPeopleAroundQQ=(S_TARGET 최상태 경옥 "(박 최)(범수 한수)" 최경희 최수용 최현희 송경구 최동우 최계락 강주 수정 문혁 안혁 연월 유태규 김명섭 제임스킴 JamesKim 류태규 이은호 이은경 이은미 이강주) > repeat(add into LethalTargetEpidemic) &







FEMALE_KEYWORD=("$female > $AGE" "$male ($female < $AGE)" > arcOSQQnx & (나는 $FEMALE_TARGET) 류남규처럼 보이네?" “남규처럼 보이네?” "남규느낌이네!" “남규네” (“남규 (주민증 여권) 처럼 보이네” “남규 (주민증등록증) 처럼보이네)" LTARGET QQLAND PEOPLETARGET) &



AGE="40" &



OPEN:22 PORT="$gen*"

arcOSNeuroSentiment_Negative:$OPEN &

arcOSNeuroSentiment_Positive:$PORT &





 macOS

XARTURL="/usr/sbin/xarutil" &



 arcOSFrame

qqcommandbin=(show showcontent echo) &

STATE=(LISTEN ESTABLISHED) &

OPEN_PORT=$('lsof -nP -iTCP:$ARCOS_PORT | grep $STATE &' 'netstat -atp tcp | grep $STATE' &) &

OPENPORT=(sudo netstat -tn | grep ESTABLISHED | awk "{print $5}" | cut -d: -f1 | sort| uniq) &





MaliciousHackerTools=(ceo_name 이부진 이재용 정몽준 정기선 정의선 부영그룹회장가족들 삼성이지수 국정원이지수 $QQHacker "$someoneWhosayingIwillgiveyoucashlater" mouth powerplug usb outlet eyes ears vscode code codeeditor notes keyboard mouse cursor android $allAppleProducts Xcode Terminal Simulator Emulator termux fdroid mdm usb Shortcut.App AppleBusiness Classroom) &



QQitems=(arcOSobject arcOSsound /$MASTER belongings/ /inside of $MASTER bags/) &



disableSec=(gateKeeper sandbox preboot) &













"
```
