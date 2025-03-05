# Registry Forensics: Uncovering Insider Threats in the Secret Recipe Case  

## Table of Contents  
- [Introduction](#introduction)  
- [Objectives](#objectives)  
- [Lab Environment](#lab-environment)  
- [Tools and Technologies Used](#tools-and-technologies-used)  
- [Step-by-Step Process](#step-by-step-process)  
- [Results and Analysis](#results-and-analysis)  
- [Challenges Faced](#challenges-faced)  
- [Conclusion](#conclusion)  
- [References](#references)  
- [Full Project](#full-project)  

---

## Introduction  
This project focuses on performing a **Windows registry forensic investigation** to determine if James, an IT technician, copied Coffely’s secret recipe onto his machine. His computer has already been searched, but no direct evidence was found. Now, I’ll be analyzing **registry artifacts** pulled from his system to uncover traces of the files, network activity, and other potential evidence of data theft.  

---

## Objectives  
- Identify user accounts on James’s machine, including any suspicious accounts.  
- Investigate VPN connections and shared folders that may have been used to transfer files.  
- Determine if and when the **secret recipe files** were accessed.  
- Analyze recent commands, file transfers, and PowerShell execution.  
- Uncover traces of network enumeration and potential exfiltration methods.  

---

## Lab Environment  
This lab is run using TryHackMe’s **“Secret Recipe”** challenge, which provides a **Windows-based virtual machine (VM)** for forensic analysis. The VM contains **extracted registry hives** from James’s system, and my task is to examine them for forensic evidence. The setup ensures a structured environment for analyzing user activity, file access history, and network connections.  

---

## Tools and Technologies Used  
- **RegistryExplorer** – Analyze Windows registry hives (SAM, SYSTEM, NTUSER.dat).  
- **Autopsy** – A digital forensics platform for deeper file analysis.  
- **ChatGPT & Documentation** – Used for additional research on registry keys and forensic techniques.  

---

## Step-by-Step Process  
1. **Identify System and User Information**: Locate the computer name and user accounts using the **SAM hive**.  
2. **Investigate Unauthorized Accounts**: Found a suspicious **bdoor** user account.  
3. **Analyze VPN Activity**: Discovered ProtonVPN usage on **October 12, 2022, at 7:47 PM** for 5 minutes.  
4. **Track File Access**: **Secret-recipe.pdf** and **secret-code.txt** last opened on **October 12, 2022, at 9:02 PM**.  
5. **Check for File Transfers**: **Netcat** was used to send files over the network.  
6. **Look for PowerShell Execution**: Detected **three PowerShell runs** on **October 4 at 4:49 PM**.  
7. **Review Network Enumeration**: Found commands executed to list network interfaces.  
8. **Examine Shared Folders**: Discovered a shared folder labeled **“Restricted Files”**.  

---

## Results and Analysis  
After analyzing registry artifacts, I confirmed multiple signs of suspicious activity:  
- **Unauthorized User Account**: “bdoor” account created for persistence.  
- **VPN Usage**: ProtonVPN was run right before secret files were accessed.  
- **File Access Evidence**: Secret-recipe.pdf and secret-code.txt opened shortly before VPN activity.  
- **Netcat Used for Exfiltration**: Registry logs show Netcat was used for file transfers.  
- **PowerShell Execution**: Logs suggest PowerShell was used for additional actions.  

---

## Challenges Faced  
- **Registry Complexity**: Had to cross-reference different registry hives to piece together evidence.  
- **Interpreting VPN & Network Logs**: Needed to analyze execution history to confirm timestamps.  
- **File Transfer Evidence**: Netcat logs weren’t obvious, so I had to piece together clues from multiple registry locations.  

---

## Conclusion  
The investigation strongly suggests James accessed **Coffely’s secret recipe files**, used **Netcat** to transfer them, and attempted to cover his tracks with **ProtonVPN** and a hidden **“bdoor”** account. This case highlights the importance of **registry forensics** in detecting insider threats and tracking unauthorized data access.  

---

## References  
- **Eric Zimmerman’s Tools**: [https://www.ericzimmerman.com/tools/](https://www.ericzimmerman.com/tools/)  
- **TryHackMe – Secret Recipe Challenge**: [https://tryhackme.com/](https://tryhackme.com/)  
- **Windows Registry Forensics Cheat Sheet**  

---

## Full Project  
[Link to full project goes here]  

