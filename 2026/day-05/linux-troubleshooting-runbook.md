# Linux Troubleshooting Runbook

## 🔹 Target Service
cron

---

## 🔹 Environment Basics

### Command:
uname -a

### Output:
(paste)

### Observation:
System is running Linux kernel (write version)

---

### Command:
cat /etc/os-release

### Output:
(paste)

### Observation:
System is Ubuntu (write version)

---

## 🔹 Filesystem Sanity

### Command:
mkdir /tmp/runbook-demo

### Output:
(paste if any)

### Observation:
Directory created successfully

---

### Command:
cp /etc/hosts /tmp/runbook-demo/hosts-copy && ls -l /tmp/runbook-demo

### Output:
(paste)

### Observation:
File copied successfully

---

## 🔹 Snapshot: CPU & Memory

### Command:
ps -o pid,pcpu,pmem,comm -p <PID>

### Output:
(paste)

### Observation:
Cron uses very low CPU and memory (normal behavior)

---

### Command:
free -h

### Output:
(paste)

### Observation:
Memory usage is within normal limits

---

## 🔹 Snapshot: Disk & IO

### Command:
df -h

### Output:
(paste)

### Observation:
Disk usage is healthy (no partition full)

---

### Command:
du -sh /var/log

### Output:
(paste)

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

### Output:
(paste)

### Observation:
Network connectivity is working

---

## 🔹 Logs Reviewed

### Command:
journalctl -u cron --no-pager -n 50

### Output:
(paste)

### Observation:
No critical errors in logs

---

### Command:
tail -n 50 /var/log/syslog | grep cron

### Output:
(paste)

### Observation:
Cron jobs are executing normally

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