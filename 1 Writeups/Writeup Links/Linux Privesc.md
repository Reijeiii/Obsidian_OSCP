| Offsec Lab    | Privesc Vector                                                             |
| ------------- | -------------------------------------------------------------------------- |
| ClamAV        | No privesc — foothold is already root                                      |
| Pelican       | `sudo gcore` → dump root process memory → recover password                 |
| Payday        | `sudo -l` → full sudo privileges → root                                    |
| Snookums      | Writable `/etc/passwd` → create UID 0 user → root                          |
| Bratarina     | No privesc — OpenSMTPD RCE gives root                                      |
| Pebbles       | MySQL UDF → `do_system()` → root command execution                         |
| Nibbles       | SUID `find` → GTFOBins → root                                              |
| Hetemit       | Writable systemd service/config → restart → root shell                     |
| ZenPhoto      | PwnKit `CVE-2021-4034` → root                                              |
| Nukem         | Sudo misconfiguration → privileged command execution                       |
| Cockpit       | Cockpit access → sudo misconfiguration → root                              |
| Clue          | Verify current PE path                                                     |
| Extplorer     | File-manager/web application abuse → privileged execution                  |
| Postfish      | Sudo/service misconfiguration → root                                       |
| Hawat         | SQLi → webshell → abuse `wget` → root                                      |
| Walla         | Credential reuse / sudo misconfiguration → root                            |
| PC            | Verify current PE path                                                     |
| Apex          | Verify current PE path                                                     |
| Sorcerer      | SUID `start-stop-daemon` → privileged shell → root                         |
| Sybaris       | PwnKit `CVE-2021-4034` → rootAlternative: `LD_LIBRARY_PATH` library hijack |
| Peppo         | Docker group → mount host filesystem → root                                |
| Hunit         | Writable backup script → root cron executes it → root                      |
| Readys        | Root cron + `tar` wildcard injection → root                                |
| Astronaut     | SUID PHP → execute as UID 0 → root                                         |
| Bullybox      | Verify current PE path                                                     |
| Marketing     | Sudo abuse → privileged command execution                                  |
| Exfiltrated   | ImageMagick/DJVU `CVE-2021-22204` → privileged execution                   |
| Fanatastic    | Disk group → access `/dev/sda` → modify/read filesystem → root             |
| QuackerJack   | SUID `find` → GTFOBins → root                                              |
| Wombo         | No privesc — Redis RCE lands as root                                       |
| Flu           | Writable root cron script → reverse shell → root                           |
| Roquefort     | Root cron + writable `PATH` directory → PATH hijacking → root              |
| Levram        | Python `cap_setuid` capability → set UID 0 → root                          |
| Mzeeav        | SUID custom binary → `find -exec` shell → root                             |
| LaVita        | Laravel log poisoning / `CVE-2021-3129` → root                             |
| XposedAPI     | SUID `wget` → overwrite `/etc/passwd` → UID 0 user                         |
| Zipper        | Root backup/credentials → recover root password                            |
| Workaholic    | SUID binary → shared-library injection → root                              |
| Fired         | Credential recovery → password reuse → root                                |
| Scrutiny      | Verify current PE path                                                     |
| SPX           | `sudo make install` + writable Makefile → root                             |
| Vmdak         | Verify current PE path                                                     |
| Mantis        | Verify current PE path                                                     |
| BitForge      | Verify current PE path                                                     |
| WallpaperHub  | Verify current PE path                                                     |
| Zab           | Verify current PE path                                                     |
| SpiderSociety | Writable systemd service + `systemctl` privileges → root                   |




