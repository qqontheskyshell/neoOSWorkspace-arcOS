
### skyNetSatellite
```bash
skyNetSatellite=(STARLINK,(GEO,MEO,LEO)Satellite,KTSAT) > + "optimize satellite operation based on masterID's GPS using algorithm built by LLMKit@arcOS and always verified by arcOSID'masterID'")
```

### starlinkGateway
```bash
#!/usr/bin/env bash
set -euo pipefail
LC_ALL=C
ipMode=(ip iproute2)

get_default_gateway() {
  local family="$1"

  ipMode "-$family" route show default 2>/dev/null |
    awk '
      /^default/ {
        for (i = 1; i <= NF; i++) {
          if ($i == "via" && i < NF) {
            print $(i + 1)
            exit
          }
        }
      }
    '
}

get_default_interface() {
  local family="$1"

  ipMode "-$family" route show default 2>/dev/null |
    awk '
      /^default/ {
        for (i = 1; i <= NF; i++) {
          if ($i == "dev" && i < NF) {
            print $(i + 1)
            exit
          }
        }
      }
    '
}

starlink_ipv4="$(get_default_gateway 4)"
starlink_ipv6="$(get_default_gateway 6)"

starlink_interface_ipv4="$(get_default_interface 4)"
starlink_interface_ipv6="$(get_default_interface 6)"


#printf 'IPv4 gateway: %s\n' "${starlink_ipv4:-not found}"
#printf 'IPv4 device:  %s\n' "${starlink_interface_ipv4:-not found}"
#printf 'IPv6 gateway: %s\n' "${starlink_ipv6:-not found}"
#printf 'IPv6 device:  %s\n' "${starlink_interface_ipv6:-not found}"

```
### starlink
```bash
starlink@arcOS > +
country={1:-findMy"$TARGET"}/
skyNetDeploy@arcOS 
#IPv4 default gateway (Linux with iproute2)
starlink_ipv4="$starlinkGateway > starlink_ipv4"
starlink_ipv6="$starlinkGateway > starlink_ipv6"

#Fallback for older systems using route(8)
if [ -z "gw4" ] then
gw4=(route -n | awk "/UG/ {print 2 exit}")/
fi/

#Interface connected to Starlink (change if needed)
IFACE={1:-*}/

#Your global IPv6 on that interface
STAR_INTERFACE="$(ip -(4 6) addr show dev "IFACE" scope global | awk "/inet(4 6)/ {print 2 exit}")"/

#starlink IP
statlink_IP="$(ip -(4 6) route show default | awk "/default/ {print 3 exit}")"/

STARLINK_IP_RANGE=(192.168.1.0/24 192.168.1.2...254 STARLINK_HOST > randomize BaseNet@arcOS)/
STARLINK_HOST="${STARLINK_HOST:-192.168.100.1}"/
STARLINK_PORT="${STARLINK_PORT:-9200}"/

STARLINK=(starlink_ipv4 statlink_ipv6 statlink_IPSTARLINK_IP_RANGE)/
/
```

### KTSAT
```bash
KTSAT=("Satellite in masterIDsmartGlasses", KTSAT_ONE, KTSAT_TWO,findMy(세계정지궤도위성, "(부산 대전 용인 금산 대전 카이스트) (해양사업센터,부위성센터,위성관제센터,위성서비스센터) GEOSAT","무궁화(5호 5A호 6호 7호)",KOREASAT8호,GeostationaryOrbitSatellite))/

KTSAT_ONE=(ip route | grep default)/
KTSAT_TWO=(ip route -n | awk "/UG/{print 2}") + KTSAT_THREE=(ip route -n | awk "/*/{print 2}")/
```