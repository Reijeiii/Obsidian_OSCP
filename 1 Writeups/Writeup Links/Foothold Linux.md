| Offsec Lab    | Foothold                                                                                                                                                                 |
| ------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| ClamAV        | Sendmail + clamav-milter <0.91.2 unauthenticated RCE (insecure popen) → opens bind shell on port 31337, root directly                                                    |
| Pelican       | Exhibitor Web UI (Zookeeper admin, port 8080) unauthenticated RCE via "java.env" config field                                                                            |
| Payday        | CS-Cart 1.3.3, default creds admin:admin → authenticated RCE (upload .phtml disguised as image)                                                                          |
| Snookums      | Simple PHP Photo Gallery v0.8 — LFI/RFI in `image.php` `img` param → RCE                                                                                                 |
| Bratarina     | OpenSMTPD RCE exploit on port 25 → direct root shell, no privesc                                                                                                         |
| Pebbles       | ZoneMinder console v1.29.0 at `/zm` — SQLi via sqlmap `--os-shell` → root                                                                                                |
| Nibbles       | **Unusual port** 5437 PostgreSQL, default creds postgres:postgres → `COPY ... FROM PROGRAM` RCE                                                                          |
| Hetemit       | Flask app on port 50000, `/verify` endpoint `eval()`s user input → RCE                                                                                                   |
| ZenPhoto      | CUPS on port 23 is a rabbit hole; real vector is ZenPhoto 1.4.1.4 (hidden in `/test`) — `ajax_create_folder.php` unauthenticated RCE                                     |
| Nukem         | WordPress 5.5.1, "Simple File List" plugin arbitrary file upload → RCE                                                                                                   |
| Cockpit       | Custom login ("blaze") SQLi auth bypass (`' OR ''='`) → leaks base64-encoded creds                                                                                       |
| Clue          | **Unusual port** 8021 FreeSWITCH `mod_event_socket` (default no-auth) → command execution                                                                                |
| Extplorer     | eXtplorer file manager, default creds admin:admin → arbitrary file upload                                                                                                |
| Postfish      | **Unusual technique**: register a web account, then send yourself a "password reset" phishing email via raw SMTP to leak the password → SSH                              |
| Hawat         | **Unusual ports** (17445/30455/50080) — Nextcloud default creds leak a zip with hardcoded creds → SQLi in a Java "issue tracker" writes a PHP webshell, root directly    |
| Walla         | RaspAP (Wi-Fi router admin panel) on port 8091, default creds admin:secret → CVE-2020-24572 authenticated RCE. Decoy SSH ports (22/422/42042) and open telnet            |
| Apex          | OpenEMR + Responsive FileManager 9.13.4 path traversal leaks DB creds → crack admin hash → authenticated OpenEMR RCE                                                     |
| Sorcerer      | Web dir listing leaks an SSH key restricted to `scp` only (forced command) → bypass via `scp -O` to overwrite `authorized_keys`                                          |
| Sybaris       | Anonymous/writable FTP + Redis 5.0.9 → upload malicious Redis module via FTP, load it → RCE                                                                              |
| Peppo         | **Unusual port** 113 (ident) enumerated with `ident-user-enum` to get real username → weak SSH creds → rbash escape → docker group abuse                                 |
| Hunit         | Credentials for user `dademola` hidden in web page source → SSH                                                                                                          |
| Wombo         | NodeBB (8080) is a rabbit hole; real vector is unauthenticated Redis 5.0.9 RCE, root directly                                                                            |
| XposedAPI     | **Unusual port** 13337, custom "Remote Software Management API" — WAF bypass via `X-Forwarded-For` header, LFI leaks username → malicious ELF via `/update`+`/restart`   |
| Exfiltrated   | Subrion CMS 4.2.1, default creds admin:admin → CVE-2018-19422 authenticated arbitrary file upload                                                                        |
| QuackerJack   | rConfig 3.9.4 — CVE-2019-19509 unauthenticated user creation chained with SQLi → authenticated RCE                                                                       |
| Readys        | WordPress "site-editor" plugin LFI leaks `/etc/redis/redis.conf` password → Redis rogue-server RCE                                                                       |
| PC            | **Unusual**: port 8000 web app is literally an unauthenticated command-execution panel — paste a command, get a shell                                                    |
| Astronaut     | Grav CMS admin panel → authenticated RCE exploit                                                                                                                         |
| BullyBox      | Exposed `.git` repo (BoxBilling) → recovered source/creds → CVE-2022-3552 authenticated RCE                                                                              |
| Marketing     | Hidden `/old` directory leaks a subdomain hosting LimeSurvey 5.3.13 → authenticated RCE                                                                                  |
| Fanatastic    | Grafana v8.3.0 arbitrary file-read (`/public/plugins/.../../../../var/lib/grafana/grafana.db`) → leaks datasource creds                                                  |
| QuackerJack   | _(see above)_                                                                                                                                                            |
| Wombo         | _(see above)_                                                                                                                                                            |
| Flu           | Confluence 7.13.6, ports 8090/8091 → CVE-2022-26134 OGNL injection RCE                                                                                                   |
| Roquefort     | Gitea (port 3000) → unauthenticated RCE (exploit-db 49383)                                                                                                               |
| Levram        | Gerapy v0.9.7 web panel (port 8000), default creds admin:admin → CVE authenticated RCE                                                                                   |
| Mzeeav        | "Antivirus" file-upload panel — bypass magic-byte filter → PHP webshell                                                                                                  |
| LaVita        | Laravel 8.4.2 with debug mode enabled → RCE via phpggc deserialization gadget (needs log-file path)                                                                      |
| Zipper        | LFI via PHP filter chain leaks source → PHP zip-wrapper trick (`zip://...#`) to execute an uploaded webshell                                                             |
| Workaholic    | WordPress, "wp-advanced-search" plugin → CVE-2024-9796 unauthenticated SQL injection                                                                                     |
| Fired         | Openfire admin console (ports 9090/9091) → CVE-2023-32315 path traversal / auth bypass → RCE                                                                             |
| Scrutiny      | Hidden `teams.` vhost running TeamCity 2023.05.4 → CVE-2024-27198 auth bypass → create admin user → RCE                                                                  |
| SPX           | Exposed `php-spx` profiler (phpinfo leak of its auth key) → CVE-2024-42007 directory traversal → cracked creds → TinyFileManager webshell                                |
| Vmdak         | "Prison Management System" web app (port 9443) — SQLi + PHP file upload → foothold as www-data                                                                           |
| Mantis        | MantisBT bug tracker — CVE-2017-12419 rogue-MySQL-server arbitrary file read leaks DB creds → cracked admin hash → authenticated RCE via dot_tool/graph config injection |
| BitForge      | Exposed `.git` repo leaks MySQL creds → SOPlanning app creds from DB                                                                                                     |
| WallpaperHub  | Wallpaper-upload app (port 5000) — filename-based LFI → steals SQLite DB with creds → cracked hash → SSH                                                                 |
| Zab           | Mage AI dashboard (port 6789) has a built-in terminal — instant unauthenticated foothold as www-data                                                                     |
| SpiderSociety | **Unusual port** 2121 FTP — default-cred control panel leaks FTP creds → FTP reveals a hidden dotfile with SSH creds                                                     |





