 Linux Privilege Escalation Lab (TryHackMe)

A hands-on security audit and privilege escalation exercise on a Linux target machine.  
This room explored **21 different attack vectors** used to gain elevated access through weak permissions, misconfigurations, and vulnerable services.
                                            ---------------------------------------------------------------
🎯 Objective

Identify privilege escalation paths and obtain root access by exploiting insecure system configurations.
                                           ---------------------------------------------------------------
 💥 Key Exploitation: MySQL UDF Injection

The most impactful finding was a **MySQL service running with root privileges**.

By abusing **User Defined Functions (UDF)**, system-level command execution was achieved.
                                            ---------------------------------------------------------------
  Methodology

- **Custom Shared Library**
  - Compiled malicious `.so` file using `gcc`
  - Used `-fPIC` for compatibility with MySQL memory space

- **Binary to BLOB Injection**
  - Converted exploit file into binary data (BLOB)
  - Inserted into temporary MySQL table

- **Restricted Directory Write**
  - Used `INTO DUMPFILE`
  - Dropped payload into:

```bash
/usr/lib/mysql/plugin/
                                            ---------------------------------------------------------------

Root Shell Access
Registered do_system() function
Modified /bin/bash SUID permissions
Spawned persistent root shell
                                            ---------------------------------------------------------------

 Attack Vectors Covered

 Services

MySQL UDF Exploitation
Shared Object Injection
SUID / SGID Abuse

Permissions
Writable /etc/passwd abuse
Writable /etc/shadow hijacking
Automation

Cron Job PATH Hijacking
Wildcard Expansion Abuse

 Sudo Misconfigurations

Shell Escape Sequences
LD_PRELOAD Exploitation
                                            ---------------------------------------------------------------

 Internal Escalation
Kernel Exploit Theory
DirtyCow
DirtyPipe
NFS Root Squashing Issues
                                            ---------------------------------------------------------------

📚 Lessons Learned
⚠️ Root Fallacy

Protecting user accounts is useless when background services run with excessive privileges.

 Debugging Matters

Using:

-g

during compilation helped troubleshoot library behavior and linking issues.
                                            ---------------------------------------------------------------

🔒 Security Recommendations

Enable secure_file_priv in MySQL
Restrict plugin directories
Apply Principle of Least Privilege (PoLP)
Audit cron jobs and writable paths
Remove unnecessary SUID binaries
🏁 Final Result

✔ Root access obtained
✔ 21 privilege escalation vectors reviewed
✔ Real-world Linux hardening lessons learned


## 📸 Screenshot

<img width="1898" height="886" alt="image" src="https://github.com/user-attachments/assets/45cefc97-eb23-448d-b3da-4b888b97591d" />
<img width="1368" height="801" alt="image" src="https://github.com/user-attachments/assets/a6415e3e-dbc1-4d29-a927-9f52ba7803b2" />


For educational and authorized lab environments only.
