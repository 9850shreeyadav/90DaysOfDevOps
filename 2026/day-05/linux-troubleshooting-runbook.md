# Linux Troubleshooting Runbook

## 🔹 Target Service
cron

---

## 🔹 Environment Basics

### Command:
uname -a

### Output:
Linux **************-Latitude-3430 6.17.0-19-generic #19~24.04.2-Ubuntu SMP PREEMPT_DYNAMIC Fri Mar  6 23:08:46 UTC 2 x86_64 x86_64 x86_64 GNU/Linux

### Observation:
System is running Linux kernel 6.17.0-19

---

### Command:
cat /etc/os-release

### Output:
PRETTY_NAME="Ubuntu 24.04.4 LTS"
NAME="Ubuntu"
VERSION_ID="24.04"
VERSION="24.04.4 LTS (Noble Numbat)"
VERSION_CODENAME=noble
ID=ubuntu
ID_LIKE=debian
HOME_URL="https://www.ubuntu.com/"
SUPPORT_URL="https://help.ubuntu.com/"
BUG_REPORT_URL="https://bugs.launchpad.net/ubuntu/"
PRIVACY_POLICY_URL="https://www.ubuntu.com/legal/terms-and-policies/privacy-policy"
UBUNTU_CODENAME=noble
LOGO=ubuntu-logo

### Observation:
System is Ubuntu 24.04.4 LTS

---

## 🔹 Filesystem Sanity

### Command:
mkdir 90dayofDevOps

### Observation:
Directory created successfully

---

### Command:
cp 90DayOfDevOps/90DaysOfDevOps/2026/day-02/linux-architecture-notes.md  90DayOfDevOps/90DaysOfDevOps/2026/day-05/ && ls -l 90DayOfDevOps/90DaysOfDevOps/2026/day-05/


### Output:
-rw-rw-r-- 1 judy judy 2279 Mar 31 22:48 linux-architecture-notes.md
-rw-rw-r-- 1 judy judy 2030 Mar 31 22:41 linux-troubleshooting-runbook.md
-rw-rw-r-- 1 judy judy 3591 Mar 13 15:56 README.md

### Observation:
File copied successfully

---

## 🔹 Snapshot: CPU & Memory

### Command:
ps -o pid,pcpu,pmem,comm -p 336836

### Output:
 PID    %CPU  %MEM COMMAND
 336836  0.0  0.0  bash

### Observation:
Cron uses very low CPU and memory (normal behavior)

---

### Command:
free -h

### Output:
               total        used        free      shared  buff/cache   available
Mem:            15Gi         9Gi       2.0Gi       2.5Gi       6.1Gi       5.4Gi
Swap:          2.0Gi       1.3Gi       668Mi


### Observation:
Memory usage is within normal limits

---

## 🔹 Snapshot: Disk & IO

### Command:
df -h

### Output:
Filesystem      Size  Used Avail Use% Mounted on
tmpfs           1.6G  4.0M  1.6G   1% /run
efivarfs        438K  174K  260K  41% /sys/firmware/efi/efivars
/dev/nvme0n1p3  460G  169G  268G  39% /
tmpfs           7.7G  165M  7.5G   3% /dev/shm
tmpfs           5.0M  8.0K  5.0M   1% /run/lock
/dev/nvme0n1p1  896M   39M  858M   5% /boot/efi
tmpfs           1.6G  1.4M  1.6G   1% /run/user/1001


### Observation:
Disk usage is healthy (no partition full)

---

### Command:
du -sh /var/log

### Output:
2.7G	/var/log

### Observation:
Log size is reasonable

---

## 🔹 Snapshot: Network

### Command:
ss -tulnp | grep cron

### Output:
(paste or empty)

### Observation:
Cron does not use network ports (expected behavior)

---

### Command:
ping -c 3 google.com
curl -i google.com

### Output:
PING google.com (2404:6800:4009:813::200e) 56 data bytes
64 bytes from bom12s08-in-x0e.1e100.net (2404:6800:4009:813::200e): icmp_seq=1 ttl=118 time=7.36 ms
64 bytes from bom12s08-in-x0e.1e100.net (2404:6800:4009:813::200e): icmp_seq=2 ttl=118 time=8.96 ms
64 bytes from bom12s08-in-x0e.1e100.net (2404:6800:4009:813::200e): icmp_seq=3 ttl=118 time=8.03 ms

--- google.com ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2002ms
rtt min/avg/max/mdev = 7.358/8.116/8.964/0.658 ms


HTTP/1.1 301 Moved Permanently
Location: http://www.google.com/
Content-Type: text/html; charset=UTF-8
Content-Security-Policy-Report-Only: object-src 'none';base-uri 'self';script-src 'nonce-HekKvv0NG7dlJp8ctTBAEg' 'strict-dynamic' 'report-sample' 'unsafe-eval' 'unsafe-inline' https: http:;report-uri https://csp.withgoogle.com/csp/gws/other-hp
Reporting-Endpoints: default="//www.google.com/httpservice/retry/jserror?ei=HATMaZa7At6Z4-EPm9D-kAY&cad=crash&error=Page%20Crash&jsel=1&bver=2410&dpf=vifyUilrA2AxXcBHQDG2265AgZC78vah5eDUTDtVui8"
Date: Tue, 31 Mar 2026 17:27:56 GMT
Expires: Thu, 30 Apr 2026 17:27:56 GMT
Cache-Control: public, max-age=2592000
Server: gws
Content-Length: 219
X-XSS-Protection: 0
X-Frame-Options: SAMEORIGIN

<HTML><HEAD><meta http-equiv="content-type" content="text/html;charset=utf-8">
<TITLE>301 Moved</TITLE></HEAD><BODY>
<H1>301 Moved</H1>
The document has moved
<A HREF="http://www.google.com/">here</A>.
</BODY></HTML>

### Observation:
Network connectivity is working
ping → Can I reach the server?
curl → Is the service working?
---

## 🔹 Logs Reviewed

### Command:
journalctl -u cron --no-pager -n 50

### Observation:
No critical errors in logs, lists 50 lines of normal logs

---

### Command:
tail -n 50 /var/log/syslog | grep cron

### Output:
(paste)

### Observation:
Filtered recent logs show cron job activity and execution details
---

## 🔹 Quick Findings

- Cron service is running normally
- No high CPU or memory usage
- No disk issues
- Logs show normal activity

---

## 🔹 If This Worsens (Next Steps)

1. Restart service:
   sudo systemctl restart cron

2. Increase logging and monitor:
   journalctl -u cron -f

3. Debug deeper:
   Check scheduled jobs using crontab -l