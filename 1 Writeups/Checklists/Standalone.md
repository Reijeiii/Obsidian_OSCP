## Initial Recon

- [ ]  Rustscan
- [ ]  Run AutoRecon
### Web Enumeration

- [ ]  Directory bruteforce on web root (feroxbuster. If large output run gobuster for better visual of targets)
- [ ]  Directory bruteforce on every newly found subdirectory
- [ ]  Subdomain enumeration (if domain-based)
- [ ]  If new subdomains/vhosts found — repeat directory & file bruteforce
- [ ]  File extension bruteforce (php, txt, bak, zip, old, config, etc.)
- [ ]  Check `/robots.txt'
- [ ] php site? Check phpinfo to reveal anything interesting
- [ ]  Check `/sitemap.xml` / `/sitemap`
- [ ]  View page source on EVERY PAGE
- [ ]  Check all JS files for hardcoded API keys, endpoints, dev comments
- [ ]  Check HTTP response headers (Server, X-Powered-By)
- [ ]  Check error pages (404/500) for stack traces / tech leaks
- [ ]  Check for exposed installer pages (`/install.php`, `/setup`, `/install`)
- [ ]  Fingerprint CMS (WhatWeb, Wappalyzer, manual check)
- [ ]  Check for file upload functionality anywhere in the app
- [ ]  Try default/known creds on any admin panels found (Tomcat manager, phpMyAdmin, Jenkins, etc.)
- [ ]  Check every port and run service specific enumeration steps (Check ports & services from notes)
- [ ] check for apis to curl
- [ ] check siteurls for LFI, RFI
- [ ] check http request with burp for CMDi
- [ ] check for SQLi
### Exploit Research

- [ ]  Note exact version numbers for every identified service (not just major version)
- [ ]  Search ExploitDB for version-specific PoCs
- [ ]  Google/searchsploit for CVEs matching exact versions

### Credential Tracking

- [ ]  Cross-reference/reuse creds across every discovered service (SSH, SMB, web login, DB, etc.)
- [ ]  Password spray confirmed usernames across all services

### Mindset / Process

- [ ]  Take notes as you go, not after — save source of every finding
- [ ]  Time-box each avenue (~20–30 min); don't rabbit-hole
- [ ]  If blocked/stuck, verify tooling before assuming target issue
- [ ]  Revert target machine if service gets into a bad state (e.g. DB connection lockout)

## Linux PrivEsc
- [ ] `sudo -l`
- [ ] Run Linpeas, learnpeass, LSE, Exploit-suggester, LinEnum. Blast all of them and Save output and slowly go over it
- [ ] manually crawl /home/, /opt/ and /var/www/html
- [ ] Check listening ports too in case you need to port forward or curl them internally
- [ ] run credshunter to check for credentials

## Windows privesc
- [ ] Run whoami /all for easy wins
- [ ] Check PowerUp.ps1, privesccheck.ps1 then WinPEAS -- Save the automated output and slowly go over it
- [ ] go through C:\Users, C:\, C:\Program Files
- [ ] run Credshunter to search for creds
- [ ] Check listening ports in case you need to port forward or curl them internally
- [ ] If stuck, enumerate manually