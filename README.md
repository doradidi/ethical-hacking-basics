# ethical-hacking-basics
 This repository covers the Ethical Hacking Basics assignment for my Cybersecurity course. It includes WHOIS and nslookup reconnaissance on example.com and an Nmap port scan on a local virtual machine to identify open ports and running services.
Ethical Hacking Basics — Submission
Tools Used

WHOIS (ICANN Lookup)
nslookup (Windows CMD)
Nmap 7.95


Task 1: Reconnaissance on example.com
WHOIS Results
Domain Name: EXAMPLE.COM
Registry Domain ID: 2336799_DOMAIN_COM-VRSN
Registrar: RESERVED-INTERNET ASSIGNED NUMBERS AUTHORITY
Registrar WHOIS Server: whois.iana.org
Created Date: 1995-08-14
Updated Date: 2023-08-14
Expiry Date: 2024-08-13
Name Server: A.IANA-SERVERS.NET
Name Server: B.IANA-SERVERS.NET
DNSSEC: signedDelegation
Status: clientDeleteProhibited
nslookup Results
# Default query
nslookup example.com

Server:  dns.google
Address: 8.8.8.8

Non-authoritative answer:
Name:    example.com
Address: 93.184.216.34

# MX Records
nslookup -type=MX example.com
No MX records found (example.com does not host email)

# NS Records
nslookup -type=NS example.com
example.com nameserver = a.iana-servers.net
example.com nameserver = b.iana-servers.net

# TXT Records
nslookup -type=TXT example.com
example.com text = "v=spf1 -all"
example.com text = "wgyf8z8cgvm2qmxpnbnldrcltvk4rdtk"

Task 2: Nmap Scan on Local Virtual Machine
Target: 192.168.56.101 (Metasploitable VM on VirtualBox)
# Command used:
nmap -A -p- 192.168.56.101

Starting Nmap 7.95 ( https://nmap.org )
Nmap scan report for 192.168.56.101
Host is up (0.0012s latency).

PORT     STATE  SERVICE     VERSION
21/tcp   open   ftp         vsftpd 2.3.4
22/tcp   open   ssh         OpenSSH 4.7p1
23/tcp   open   telnet      Linux telnetd
25/tcp   open   smtp        Postfix smtpd
80/tcp   open   http        Apache httpd 2.2.8
111/tcp  open   rpcbind     2 (RPC #100000)
139/tcp  open   netbios-ssn Samba smbd 3.X
445/tcp  open   netbios-ssn Samba smbd 3.X
3306/tcp open   mysql       MySQL 5.0.51a
5432/tcp open   postgresql  PostgreSQL 8.3.0
8180/tcp open   http        Apache Tomcat 5.5

OS details: Linux 2.6.X
Network Distance: 1 hop

Step-by-Step Process

Opened Command Prompt on Windows
Ran nslookup example.com and noted the IP address and DNS servers
Used ICANN WHOIS lookup at lookup.icann.org for domain registration details
Launched VirtualBox and started the Metasploitable VM
Found the VM's IP using ip a inside the VM terminal
Ran nmap -A -p- 192.168.56.101 from the host machine
Documented all open ports, services, and versions found


Findings Summary
Reconnaissance (example.com)
InfoResultIP Address93.184.216.34RegistrarIANAName Serversa.iana-servers.net, b.iana-servers.netMail ServerNoneDNSSECEnabled
Nmap Scan (Local VM)
PortServiceVersion21FTPvsftpd 2.3.422SSHOpenSSH 4.7p123TelnetLinux telnetd25SMTPPostfix80HTTPApache 2.2.83306MySQL5.0.51a5432PostgreSQL8.3.08180HTTPApache Tomcat 5.5

Conclusion
This assignment demonstrated basic ethical hacking reconnaissance techniques. Using WHOIS and nslookup, I was able to gather publicly available information about example.com including its IP address, name servers, and domain registration details. Using Nmap on a local virtual machine, I identified multiple open ports and running services, which in a real penetration test would represent potential attack surfaces. Tools like FTP (port 21), Telnet (port 23), and outdated software versions highlight the importance of regularly auditing and securing networked systems.
