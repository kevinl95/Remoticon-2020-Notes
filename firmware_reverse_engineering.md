# Introduction to Firmware Reverse Engineering
Instructor: Asmita Jha
IoT Security Consultant
asmita@payatu.com
aj_0x00

## Introduction
- Ascher Opler in 1967 coined term
- OS based and bare metal firmware
- OS has a stack of Hardware -> OS -> Application
- Bare metal is Hardware -> Application

## Why Firmware Reverse Engineering?
- The firmware is the core business logic
- It's core IP for a company
- Firmware is low hanging fruit for an attacker- could give you access to communication layer, management layer, user applications, etc.

## Possible Attack Scenarios
- Filesystem
- Custom binaries
- Hardcoded sensitive information like keys
- Config files
- Certificates
- Fuzzing
- Backdoor the device

## Introduction to tools for firmware static and dynamic analysis
- Identify if the device is OS based or bare metal
- Identify if the firmware is encrypted
- If encrypted, workaround or decrypt. Find previous non-encrypted releases (which may contain the encryption algorithm), hardware attacks like side channel techniques to extract the key
- If bare metal/RTOS/proprietary you will need to identify the controller, find a datasheet, identify the architecture, build a memory map, use Ghidra or IDA Pro or radare2 to reverse the binary, perform real time analysis using debuggers, and if the hardware is not present perform emulation

## Static Analysis
- Extract firmware files
- Look for interesting strings
- Hexdump - analyze the supposed file header
- Identfy the instruction set if there is no information available on the chip
- Hex editors like hexdump, or Bless
- Binwalk (ReFirmLabs). Can scan for common file signatures, the architecture, determine if files are encrypted, and more
- Ghidra (open source, on GitHub)/IDA Pro (Hex-Rays). Turns assembly into pseudo c-code.
- Firmwalker (Craigsmith.net). Searches for password files, SSL files, SSH related files, web servers, important binaries, IP addresses, URLS, and emails! Very cool tool, excited to try this one.
- FACT Tool (FKIE CAD). Nice GUI for static analysis
- EXPLIoT Firmware Auditor (expliot.io). Graphically analyzes firmware and shows you the location of config files, extracts entropy graph, and more.

## Dynamic Analysis
- Emulation
- Fuzzing
- Hardware and software based debugging
- Use a disassembler 
- gdb-multiarch
- Avatar2 (avatartwo on github). Hardware emulation tool
- Firmadyne (Firmadyne on github).
- Unicorn (unicorn-engine.org). Qemu-derived tool that does CPU emulation. 
- Qiling (qilingframework on github). Unicorn-derived tool that adds high-level system emulation. 
- Fuzzing tools like Radamsa, booFuzz. Checking for input sanitization

## Examples of attacks due to vulnerabilities in the firmware

### Example 1
CVE-2019-15530
Command injection on a D-Link router, DIR-823G
HNDAP API function is not sanitizing input, and will call system() with whatever the user has in the request body

### Example 2
CVE-2020-8614
Remote code execution on a router (Askey AP4000W TDC_V1.01.003)
Insecure FTP server with hardcoded credentials
Uses wget to get new firmware from Askey's website
Credentials ahd read/write rights to most directories on the manufacturer's FTP serer
Could load and modify firmware images, add a backdoor
No firmware signature validation in the update mechanism

### Example 3
CVE-2020-8423
Buffer overflow in httpd binary in a TP-Link router

### Example 4
CVE-2017-10721
Telnet Enabled in Shekar Endoscope (a camera for looking inside difficult to reach areas)
Attacker found that the camera's default SSID allowed them to connect with default credentials
Brute force telnet username/password