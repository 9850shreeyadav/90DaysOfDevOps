# Day 09 Challenge — Answer Template

## Summary
- Users created: tokyo, berlin, professor, nairobi
- Groups created: developers, admins, project-team

---

## Task 1 — Create Users

Commands

```
# create users with home directories and set passwords
sudo useradd -m tokyo
sudo passwd tokyo
sudo useradd -m berlin
sudo passwd berlin
sudo useradd -m professor
sudo passwd professor
```

Output

```
# cat /etc/passwd
tokyo:x:1001:1001::/home/tokyo:/bin/sh
berlin:x:1002:1002::/home/berlin:/bin/sh
professor:x:1003:1003::/home/professor:/bin/sh

# cd /home | ls -lrt
drwxr-x--- 2 tokyo     tokyo     4096 Jun 16 17:14 tokyo
drwxr-x--- 2 berlin    berlin    4096 Jun 16 17:15 berlin
drwxr-x--- 2 professor professor 4096 Jun 16 17:15 professor
```

## Task 2 — Create Groups

Commands

```
sudo groupadd developers
sudo groupadd admins
cat /etc/group
```

Output

```
developers:x:1004:
admin:x:1005
```

---

## Task 3 — Assign Users to Groups

Commands

```
sudo usermod -aG developers tokyo
sudo usermod -aG developers,admins berlin
sudo usermod -aG admins professor
```

Output

```
# groups tokyo    
tokyo : tokyo developers

# groups berlin
berlin : berlin developers admins

# groups professor
professor : professor admins
```

---

## Task 4 — Shared Directory (/opt/dev-project)

Commands

```
sudo mkdir -p /opt/dev-project
sudo chgrp developers /opt/dev-project
sudo chmod 775 /opt/dev-project

```

Output

```
# ls -ld /opt/dev-project
drwxrwxr-x 2 root developers 4096 Jun 16 17:35 .
```

---

## Task 5 — Team Workspace (/opt/team-workspace)

Commands

```
sudo useradd -m nairobi
sudo passwd nairobi
sudo groupadd project-team
sudo usermod -aG project-team nairobi
sudo usermod -aG project-team tokyo
sudo usermod -aG project-team tokyo
sudo chgrp project-team /opt/team-workspace
sudo chmod 775 /opt/team-workspace
```

Output

```
# ls -ld /opt/team-workspace
drwxrwxr-x 2 root project-team 4096 Jun 16 17:39 /opt/team-workspace/
```

---

## Commands Used (full history)

Copy-paste the exact commands you executed (in order):

    1  ls
    2  cd workspace/
    3  ls
    4  cd devuser/
    5  ls
    6  ls -a
    7  cd
    8  useradd -m tokyo
    9  passwd tokyo
    10  useradd -m berlin
    11  passwd berlin
    12  useradd -m professor
    13  passwd professor
    14  cd /usr/bin/bash
    15  cd /usr/bin/bash/
    16  cd /usr/bin
    17  ls
    18  cd ../
    19  ls
    20  cd
    21  cd /etc/passwd
    22  cd /home/
    23  ls
    24  cd 
    25  cd /etc/passwd
    26  cd /etc/passwd/
    27  cd /etc/
    28  ls
    29  cat passwd
    30  cd
    31  cd /home/
    32  ls
    33  ls -lrt
    34  cd
    35  ls
    36  clear
    37  ls -a
    38  sudo groupadd developers
    39  groupadd developers
    40  groupadd admin
    41  cat /etc/group
    42  usermod -aG developers tokyo
    43  usermod -aG developers,admin berlin
    44  usermod -aG admins professor
    45  usermod -aG admin professor
    46  groups
    47  id
    48  groups
    49  groups tokyo
    50  groups berlin
    51  groups professor
    52  sudo mkdir -p /opt/dev-project
    53  mkdir -p /opt/dev-project
    54  chgrp developers /opt/dev-project
    55  chmod 775 /opt/dev-project
    56  -u tokyo touch /opt/dev-project/tokyo-test.txt
    57  ls
    58  ls -lrt
    59  cd /opt/dev-project/
    60  ls
    61  ls -ld
    62  sudo -u tokyo touch /opt/dev-project/tokyo-test.txt
    63  sudo useradd -m nairobi
    64  sudo useradd -m nairobuseradd -m nairobii
    65  useradd -m nairobi
    66  passwd nairobi
    67  groupadd project-team
    68  usermod -aG project-team nairobi
    69  usermod -aG project-team tokyo
    70  chgrp project-team /opt/team-workspace
    71  chmod 775 /opt/team-workspace
    72  cd ../
    73  ls
    74  mkdir -p /opt/team-workspace
    75  chgrp project-team /opt/team-workspace
    76  chmod 775 /opt/chmod 775 /opt/team-workspace
    77  chmod 775 /opt/team-workspace
    78  ls -ld /opt/team-workspace/
    79  cd
    80  history