To restrict or disable access to the /usr/bin folder for TFTP while using bash or in a "make" environment, you must control what directories TFTP is allowed or denied to access. This is typically handled on Linux systems using the /etc/tftpaccess.ctl file.

Disabling /usr/bin for TFTP

- Create or edit the file /etc/tftpaccess.ctl.
- Add a line to explicitly deny access to /usr/bin:  
    text

deny:/usr/bin

-   
    
- You can also explicitly allow only the needed directories with an allow: line (e.g., for your TFTP root folder), ensuring everything else is inaccessible:  
    text

allow:/tftpboot

deny:/usr/bin

-   
    
- The rules in /etc/tftpaccess.ctl are absolute path based and evaluated sequentially. If both allow: and deny: match a path, denial takes precedence. For more complex scenarios, see the specific example order in IBM's TFTP documentation.[ibm](https://www.ibm.com/docs/en/aix/7.2.0?topic=t-tftp-command)​

Using Bash or Make

- If you are running TFTP as part of a build or automation script (using bash or make), these directory rules will still apply, as they are enforced on the server side.
- If compiling TFTP-related code, ensure the TFTP daemon you use respects the /etc/tftpaccess.ctl mechanism.

Summary Table

|   |   |   |
|---|---|---|
|Method|What to do|Example|
|Allow TFTP root only|allow:/tftpboot|allow:/tftpboot|
|Block system binaries|deny:/usr/bin|deny:/usr/bin|
|Config file location|/etc/tftpaccess.ctl|/etc/tftpaccess.ctl|

These access control rules are the safest and most direct way to disable or block certain folders like /usr/bin for TFTP services running on Linux systems.[ibm](https://www.ibm.com/docs/en/aix/7.2.0?topic=t-tftp-command)​

Add to follow-up

1. [https://stackoverflow.com/questions/61548818/how-to-override-usr-local-bin-missing-from-bash-profile](https://stackoverflow.com/questions/61548818/how-to-override-usr-local-bin-missing-from-bash-profile)
2. [https://www.aeronetworks.ca/2014/05/tftp-server-on-fedora-linux.html](https://www.aeronetworks.ca/2014/05/tftp-server-on-fedora-linux.html)
3. [https://stackoverflow.com/questions/48467015/kill-tftp-command-thats-running-in-subshell](https://stackoverflow.com/questions/48467015/kill-tftp-command-thats-running-in-subshell)
4. [https://www.ibm.com/docs/en/aix/7.2.0?topic=t-tftp-command](https://www.ibm.com/docs/en/aix/7.2.0?topic=t-tftp-command)
5. [http://wiki.r1soft.com/display/CDP3/Configuring+TFTP+Server+on+Linux](http://wiki.r1soft.com/display/CDP3/Configuring+TFTP+Server+on+Linux)
6. [https://openwrt.org/docs/guide-user/troubleshooting/tftpserver](https://openwrt.org/docs/guide-user/troubleshooting/tftpserver)
7. [https://www.reddit.com/r/debian/comments/1dx9mxc/command_not_found_but_i_can_see_it/](https://www.reddit.com/r/debian/comments/1dx9mxc/command_not_found_but_i_can_see_it/)
8. [https://docs.fogproject.org/en/latest/kb/troubleshooting/troubleshoot-tftp/](https://docs.fogproject.org/en/latest/kb/troubleshooting/troubleshoot-tftp/)
9. [https://e2e.ti.com/support/processors-group/processors/f/processors-forum/61432/tftp-on-ubuntu-10-04](https://e2e.ti.com/support/processors-group/processors/f/processors-forum/61432/tftp-on-ubuntu-10-04)
10. [https://www.unixfu.ch/start-a-tftp-server-on-your-mac/](https://www.unixfu.ch/start-a-tftp-server-on-your-mac/)