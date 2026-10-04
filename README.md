
# I Pwned Metasploitable 2

How I got root:

1. nmap found vsftpd 2.3.4 on port 21
2. Used metasploit vsftpd_234_backdoor -> got root
3. Got hashes from /etc/shadow
4. Cracked msfadmin with john + rockyou
5. SSH login with legacy options
6. sudo su -> root

Proof: whoami = root

Tools: nmap, metasploit, john, ssh

Learned: Patch old services, strong passwords, no ALL in sudo.
