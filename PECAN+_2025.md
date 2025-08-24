# PECAN+ 2025
This page has notes from PECAN+ CTF 2025.

## Further info
Further info, some of which was covered during the training day can be found in [Get Started](https://github.com/J33p3rs/GetStarted/blob/main/README.md)

## Handy Linux
| Command | What it does | Example |
|---|---|---|
| `ls` | Lists files and directories in the current (or specified) directory. | `ls filename` |
| `cd` | Changes the current working directory. | `cd ~/projects` |
| `mkdir` | Creates a new directory (use `-p` to create parent dirs as needed). | `mkdir projects/app/logs` |
| `cat` | Concatenates and prints file contents to standard output. | `cat notes.txt` |
| `cp` | Copies files or directories (use `-r` for directories). | `cp report.pdf backups/` |
| `mv` | Moves or renames files or directories. | `mv oldname.txt newname.txt` |
| `rm` | Removes files or directories (danger: permanent delete). | `rm obsolete.log` |
| `sudo` | Runs a command with elevated privileges (default: root). | `sudo systemctl restart nginx` |
| `man` | Opens the manual page for a command. | `man grep` |
| `-h` / `--help` | Shows built-in help/usage for many commands. | `ls --help` |
| `\|` (pipe) | Sends the output of the left command to the right command’s input. | `dmesg \| grep -i usb` |
| `grep` | Searches text for lines matching a pattern (regex supported). The `-i` flag makes `grep` perform a case-insensitive match, so a pattern like `error` will also find `Error`, `ERROR`, and `eRrOr`. | `grep -i "error" /var/log/syslog` |
| `strings` | Prints human-readable strings from binary files. | `strings /bin/ls` |
| `readelf` | Displays ELF binary information (headers, sections, symbols). | `readelf /bin/ls` |

## Things to check out (tools, links, and other random things)


| Name                | Link                                             | Description                                                                 |
|---------------------|--------------------------------------------------|-----------------------------------------------------------------------------|
| CrikeyCon          | [https://crikeycon.com](https://crikeycon.com)    | A community-led cybersecurity conference in South-East Queensland.         |
| B-Sides Brisbane   | [https://bsidesbrisbane.com](https://bsidesbrisbane.com) | A dynamic, inclusive cybersecurity conference in Brisbane.                 |
| TryHackMe          | [https://tryhackme.com](https://tryhackme.com)    | An online cybersecurity training platform with hands-on, browser-based labs. |
| OverTheWire        | [https://overthewire.org](https://overthewire.org) | Wargames platform for learning Linux, networking, and security basics.     |
| Hack The Box       | [https://www.hackthebox.com](https://www.hackthebox.com) | A cybersecurity training platform offering labs, CTFs, and certifications. |
| GitHub             | [https://github.com](https://github.com)         | A platform for hosting, sharing, and collaborating on code repositories.   |
| CyberChef          | [https://cyberchef.io](https://cyberchef.io)     | The "Cyber Swiss Army Knife" – a web app for encryption, encoding, decoding, and data analysis. |
| AperiSolve         | [https://www.aperisolve.com](https://www.aperisolve.com) | An online tool for analysing images and detecting hidden information.     |
| PentesterLab       | [https://pentesterlab.com](https://pentesterlab.com) | Hands-on web security and penetration testing exercises for all skill levels. |
| Burp Web Academy   | [https://portswigger.net/web-security](https://portswigger.net/web-security) | Free training from PortSwigger for learning web application security.     |
| A-Packets           | [https://apackets.com](https://apackets.com)     | A platform focused on packet analysis and network traffic investigation tools. |


## Writing Better Prompts: The **Role + Task + Detail** Approach

When writing prompts for AI or LLMs, it's helpful to follow a simple structure:

**Role + Task + Detail**

This makes your prompts **clear**, **specific**, and **easy for the AI to understand**.

---

### **1. Role**
Tell the AI **who it should act as**.  
This sets the context and improves the quality of the response.

**Example:**  
“You are a **cybersecurity teacher**.”

---

### **2. Task**
Explain **what you want it to do**.  
Be direct and specific.

**Example:**  
“**Explain three common cyber threats.**”

---

### **3. Detail**
Add **extra information, rules, or style** so the answer matches what you need.

**Example:**  
“**Use simple language for high school students and keep it under 100 words.**”

---

### **Putting It All Together**

**Prompt Example 1:**  
> You are a **cybersecurity teacher**. **Explain three common cyber threats** in **simple terms for high school students**.

**Prompt Example 2:**  
> You are an **ethical hacker**. **Write a short guide** showing **how to create a strong password**. **Use bullet points and keep it under 80 words.**

**Prompt Example 3:**  
> You are a **news reporter**. **Summarise the latest ransomware attack** in **one paragraph** that a **Year 10 student** can understand.

---

### **Quick Tip**
- The more **specific** you are, the **better the results**.
- Always include **who**, **what**, and **how** in your prompt.
