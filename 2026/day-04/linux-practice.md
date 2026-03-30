# Linux Practice - Day 04

## 🔹 Process Checks

### Command:
ps aux | grep cron

### Output:
root        1531  0.0  0.0   9496  3024 ?        Ss   09:19   0:00 /usr/sbin/cron -f -P

### Command:
pgrep cron

### Output:
1531

---

## 🔹 Service Checks

### Command:
systemctl status cron

### Output:
● cron.service - Regular background program processing daemon
     Loaded: loaded (/lib/systemd/system/cron.service; enabled; vendor preset: enabled)
     Active: active (running) since Mon 2026-03-30 09:19:48 IST; 42min ago
       Docs: man:cron(8)
   Main PID: 1531 (cron)
      Tasks: 1 (limit: 18596)
     Memory: 696.0K
        CPU: 70ms
     CGroup: /system.slice/cron.service
             └─1531 /usr/sbin/cron -f -P

Mar 30 09:30:01 enovatepy241-Latitude-3430 CRON[16483]: pam_unix(cron:session): session closed for user root
Mar 30 09:35:01 enovatepy241-Latitude-3430 CRON[19301]: pam_unix(cron:session): session opened for user root(uid=0) by (uid=0)
Mar 30 09:35:01 enovatepy241-Latitude-3430 CRON[19302]: (root) CMD (command -v debian-sa1 > /dev/null && debian-sa1 1 1)
Mar 30 09:35:01 enovatepy241-Latitude-3430 CRON[19301]: pam_unix(cron:session): session closed for user root
Mar 30 09:45:01 enovatepy241-Latitude-3430 CRON[23384]: pam_unix(cron:session): session opened for user root(uid=0) by (uid=0)
Mar 30 09:45:01 enovatepy241-Latitude-3430 CRON[23385]: (root) CMD (command -v debian-sa1 > /dev/null && debian-sa1 1 1)
Mar 30 09:45:01 enovatepy241-Latitude-3430 CRON[23384]: pam_unix(cron:session): session closed for user root
Mar 30 09:55:01 enovatepy241-Latitude-3430 CRON[27421]: pam_unix(cron:session): session opened for user root(uid=0) by (uid=0)
Mar 30 09:55:01 enovatepy241-Latitude-3430 CRON[27422]: (root) CMD (command -v debian-sa1 > /dev/null && debian-sa1 1 1)
Mar 30 09:55:01 enovatepy241-Latitude-3430 CRON[27421]: pam_unix(cron:session): session closed for user root


---

### Command:
systemctl list-units --type=service | grep cron

### Output:
  cron.service                                          loaded active     running       Regular background program processing daemon


---

## 🔹 Log Checks

### Command:
journalctl -u cron --no-pager | tail -n 20

### Output:
Mar 29 13:19:35 enovatepy241-Latitude-3430 systemd[1]: Stopped Regular background program processing daemon.
-- Boot fb75bb02e2fd4b828f9328dc396004d0 --
Mar 30 09:19:48 enovatepy241-Latitude-3430 systemd[1]: Started Regular background program processing daemon.
Mar 30 09:19:48 enovatepy241-Latitude-3430 cron[1531]: (CRON) INFO (pidfile fd = 3)
Mar 30 09:19:48 enovatepy241-Latitude-3430 cron[1531]: (CRON) INFO (Running @reboot jobs)
Mar 30 09:25:01 enovatepy241-Latitude-3430 CRON[13968]: pam_unix(cron:session): session opened for user root(uid=0) by (uid=0)
Mar 30 09:25:01 enovatepy241-Latitude-3430 CRON[13969]: (root) CMD (command -v debian-sa1 > /dev/null && debian-sa1 1 1)
Mar 30 09:25:01 enovatepy241-Latitude-3430 CRON[13968]: pam_unix(cron:session): session closed for user root
Mar 30 09:30:01 enovatepy241-Latitude-3430 CRON[16483]: pam_unix(cron:session): session opened for user root(uid=0) by (uid=0)
Mar 30 09:30:01 enovatepy241-Latitude-3430 CRON[16485]: (root) CMD ([ -x /etc/init.d/anacron ] && if [ ! -d /run/systemd/system ]; then /usr/sbin/invoke-rc.d anacron start >/dev/null; fi)
Mar 30 09:30:01 enovatepy241-Latitude-3430 CRON[16483]: pam_unix(cron:session): session closed for user root
Mar 30 09:35:01 enovatepy241-Latitude-3430 CRON[19301]: pam_unix(cron:session): session opened for user root(uid=0) by (uid=0)
Mar 30 09:35:01 enovatepy241-Latitude-3430 CRON[19302]: (root) CMD (command -v debian-sa1 > /dev/null && debian-sa1 1 1)
Mar 30 09:35:01 enovatepy241-Latitude-3430 CRON[19301]: pam_unix(cron:session): session closed for user root
Mar 30 09:45:01 enovatepy241-Latitude-3430 CRON[23384]: pam_unix(cron:session): session opened for user root(uid=0) by (uid=0)
Mar 30 09:45:01 enovatepy241-Latitude-3430 CRON[23385]: (root) CMD (command -v debian-sa1 > /dev/null && debian-sa1 1 1)
Mar 30 09:45:01 enovatepy241-Latitude-3430 CRON[23384]: pam_unix(cron:session): session closed for user root
Mar 30 09:55:01 enovatepy241-Latitude-3430 CRON[27421]: pam_unix(cron:session): session opened for user root(uid=0) by (uid=0)
Mar 30 09:55:01 enovatepy241-Latitude-3430 CRON[27422]: (root) CMD (command -v debian-sa1 > /dev/null && debian-sa1 1 1)
Mar 30 09:55:01 enovatepy241-Latitude-3430 CRON[27421]: pam_unix(cron:session): session closed for user root




---

## 🔹 Mini Troubleshooting

### Problem:
Cron service not running

### Steps:
1. Check status:
   systemctl status cron

2. Start service:
   sudo systemctl start cron

3. Verify again:
   systemctl status cron

4. Check logs:
   journalctl -u cron

### Conclusion:
Cron service is running successfully and logs are visible