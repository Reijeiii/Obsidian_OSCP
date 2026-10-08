### **Got Creds?**
Found creds but they don't work? Take a step back and check your enumeration? Port 22 ssh is open? -> Try creds there

# Webapps
- Enumerate version of applications. Check for exploits
- Cant catch shell? Change the port to something found in autorecon. In offesc labs the port are restricted
- There have been labs where nmap doesn't find vulns for example in SMBs. Try this nmap script `sudo nmap -sVC -vvv $IP --script vuln`
- CMS but no version info? Check the source code CAREFULLY
- Check nmap for CMS running for example RaspAP `WWW-Authenticate: Basic realm="RaspAP"` 
- Webapp Enum didn't find anything expect git endpoint 301. I could use Git-dumper to it but didn't think about it because 301 http response with gobuster
- use msfvenom if rev shell oneliners dont work
- run other nmap scans. Sometimes autorecon misses stuff
- run gobuster instead of Feroxbuster. Feroxbuster works 95% of times
- Got password but cant login? Maybe it is encrypted or base64 encoded? Try decoding it
- use username:username to login
# Privesc Linux
- Don't overthink to solution. It is not complicated so don't make it complicated
- Google for Kernel and OS version exploits. Did a room where Linpeas/Learnpeass/LinEnum/Linux-Exploit-Suggester did not found any exploits for kernel but google did
- check /etc/passwd for users and use the name as password: patrick:patrick
- use old password with root user
- custom SUID / executable / script? Check what it does [[Unknown binaries  - executables - jobs]]
- API in 127.0.0.1 port? use curl to it on target machine or port forward
- https://github.com/0x6b6679/CVE-2026-31431

# Privesc Win
- API in 127.0.0.1 port? use curl to it on target machine
- netstat -ano
- manually check everything
# AD
- check netstat -ano. Need to port forward something like jenkins? Check [[AD7]]
- stuck with lateral movement? Check rustscan on next machine. Maybe there is http server that you need to exploit
- got local admin user? Check post-exploitation steps like powershell history, secrets dump, mimikatz
- pass-the-ticket, golden ticket, silver ticket