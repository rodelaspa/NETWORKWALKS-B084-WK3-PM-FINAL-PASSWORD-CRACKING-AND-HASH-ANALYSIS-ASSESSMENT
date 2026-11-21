# 🔐 Password Cracking & Hash Analysis Assessment (`W3-PM1` & `W3-PM2`)
Executing Offline PDF Hash Extraction (`pdf2john.pl` & Networkwalks Hash Calculator) and Dictionary-Based Password Auditing (John the Ripper & Networkwalks Password Cracker) on Debian Linux within an authorized penetration testing scope.

---

## 📌 Project Overview
This repository documents the **Week 3 Practical Activities** (`W3-PM1` and `W3-PM2`) for the Networkwalks Cybersecurity & Ethical Hacking Internship (Batch **B084**).

Per the Week 3 Project Guide requirements, both essential modules were completed natively on **Debian Linux**:
1. **Essential Module 1 (`W3-PM1` – Password Cracking with JTR):** Extracting the `$pdf$` cryptographic hash from an encrypted PDF file (`My Locked PDF1.pdf`) using `/usr/share/john/pdf2john.pl`, saving the hash file (`hash1.txt`), and executing dictionary attacks using **John the Ripper (`john`)** on Debian Linux.
2. **Essential Module 2 (`W3-PM2` – Password Cracking with Networkwalks Tools):** Using the browser-based **Networkwalks Hash Calculator** and **Networkwalks Password Cracker** tools to extract `$pdf$` hashes, run wordlist dictionary attacks, and unlock protected files.

All activities were executed strictly within authorized educational boundaries using official Networkwalks lab files.

---

## 🎯 Objectives
The main objectives of this Week 3 engagement are to:
- **Cryptographic Foundations:**
  - Understand the core distinction between reversible **two-way encryption** and irreversible **one-way hashing**.
- **Module 1 (`W3-PM1` – Password Cracking with John the Ripper on Debian Linux):**
  - Install and verify John the Ripper (`john`) and `/usr/share/john/pdf2john.pl` on Debian Linux.
  - Extract the crackable `$pdf$` hash from `My Locked PDF1.pdf` and save it into `hash1.txt`.
  - Generate a dictionary wordlist (`wordlist.txt`) and execute `john` to display the recovered password (`password1`).
- **Module 2 (`W3-PM2` – Password Cracking with Networkwalks Tools):**
  - Parse `My Locked PDF1.pdf` locally in the browser using the **Networkwalks Hash Calculator** (`networkwalks.com/hash-calculator/`) to extract the `$pdf$` hash.
  - Execute a dictionary attack using the **Networkwalks Password Cracker** (`networkwalks.com/password-cracker/`).
- **Verification & Reporting:**
  - Unlock `My Locked PDF1.pdf` with the recovered password (`password1`), capture the completion flag, and document password hardening recommendations.

---

## 🛡️ Scope & Authorization
This assessment covers **Week 3 (`W3-PM1` & `W3-PM2`)** under strict rules of engagement:
- **Authorized Target File:** `My Locked PDF1.pdf` *(Official encrypted lab file provided by Networkwalks)*
- **Permitted Activities:** Offline hash extraction and authorized dictionary-based password strength auditing.
- **Prohibited Activities:** Unauthorized password cracking, credential stuffing, or attacking third-party files and systems without explicit written permission.

> **⚠️ Liability Disclaimer:** All materials and methodologies documented in this repository are strictly for educational and authorized research purposes. Unauthorized access or password cracking against systems or files without explicit written permission is illegal. Neither the author nor Networkwalks assumes liability for misuse of this knowledge.

---

## 🏗️ Assessment Architecture
The assessment demonstrates two end-to-end offline password auditing workflows executed from **Debian Linux**:
- **Local CLI Auditing (`W3-PM1`):** Uses `perl /usr/share/john/pdf2john.pl` and **John the Ripper (`john`)** in a unified Debian Linux terminal workflow to extract and crack the PDF password hash offline.
- **Browser-Based Auditing (`W3-PM2`):** Uses a web browser (Firefox ESR / Chromium) on Debian Linux to run the client-side **Networkwalks Hash Calculator** and **Networkwalks Password Cracker** tools without installing additional dependencies.

---

## ⚙️ Engagement & Environment Configuration

| 🧩 Component | ⚙️ Configuration |
| :--- | :--- |
| **👤 Pentester Name** | Rodel L. Aspa |
| **🎓 Program / Batch** | B084 – Networkwalks Cybersecurity Internship |
| **📅 Assessment Date** | *[DD Month YYYY]* |
| **📦 Modules Completed** | `W3-PM1` (Password Cracking with JTR), `W3-PM2` (Password Cracking with NW Tools) |
| **🐧 Assessment OS** | Debian Linux |
| **📄 Authorized Target File** | `My Locked PDF1.pdf` (`65.2 KB` – PDF Revision R4, Version V4, 128-bit) |
| **🧰 Core Tools (`W3-PM1`)** | `perl /usr/share/john/pdf2john.pl`, John the Ripper (`john`) |
| **🌐 Core Web Tools (`W3-PM2`)** | Networkwalks Hash Calculator, Networkwalks Password Cracker |

---

## 🪜 Unified Execution Procedure & Findings (`W3-PM1` & `W3-PM2`)

### Step 1. Download Encrypted Target File (`My Locked PDF1.pdf`)
- Downloaded `My Locked PDF1.pdf` (`65.2 KB`) from the official Networkwalks Week 3 lab portal (`https://networkwalks.com/project-task-lab-password-cracking-with-networkwalks-tools/`) into the Debian Linux working directory.

### Step 2. Install & Verify John the Ripper on Debian Linux (`W3-PM1`)
- Installed the `john` package via `apt` and verified both John the Ripper and `/usr/share/john/pdf2john.pl`:
  ```bash
  sudo apt update && sudo apt install -y john
  john --list=build-info | head -n 5 && ls -l /usr/share/john/pdf2john.pl
  ```
- *(Windows Equivalent Reference: Download John the Ripper `1.9.0-jumbo-1-win64` and Johnny GUI `v2.2`, then link `john.exe` under **Settings** > **John the Ripper executable**).*

> *(Upload your JTR version/setup screenshot to GitHub and replace the `src` link below)*
<img alt="Step 2 - JTR Verification" src="screenshots/01-jtr-version.png" />

### Step 3. Extract PDF Hash via CLI (`pdf2john.pl` -> `hash1.txt`) (`W3-PM1`)
- Extracted the crackable `$pdf$` hash string from `My Locked PDF1.pdf` using Perl and saved it into `hash1.txt` without extra wrapper characters (`b'...'`):
  ```bash
  perl /usr/share/john/pdf2john.pl "My Locked PDF1.pdf" > hash1.txt && cat hash1.txt
  ```
- **Extracted Hash Format:** `$pdf$4*4*128*-1060*1*16*55d1a5c14175da449753199e44971d32*32*...`

> *(Upload your `pdf2john.pl` hash extraction screenshot to GitHub and replace the `src` link below)*
<img alt="Step 3 - PDF2John Hash Extraction" src="screenshots/02-pdf2john-hash.png" />

### Step 4. Execute Dictionary Attack via John the Ripper (`W3-PM1`)
- Created a targeted dictionary wordlist (`wordlist.txt`), ran John the Ripper against `hash1.txt`, and displayed the cracked plaintext password (equivalent to clicking **Open password file** > **Start new attack** in Johnny GUI):
  ```bash
  printf "123456\npassword\nadmin\nletmein\nqwerty\npassword1\n" > wordlist.txt
  john --wordlist=wordlist.txt hash1.txt && john --show hash1.txt
  ```
- **Cracked Password (`W3-PM1`):** `password1`

> *(Upload your JTR cracked output screenshot to GitHub and replace the `src` link below)*
<img alt="Step 4 - JTR Cracked Password" src="screenshots/03-jtr-cracked.png" />

### Step 5. Extract PDF Hash via Networkwalks Hash Calculator (`W3-PM2`)
- Opened `https://networkwalks.com/hash-calculator/` in the browser, selected the **PDF** tab, and uploaded `My Locked PDF1.pdf`.
- Verified the locally parsed `pdf2john` / Hashcat-compatible hash starting with `$pdf$4*4*128...` and clicked **Copy** to copy the full hash string.

> *(Upload your Networkwalks Hash Calculator screenshot to GitHub and replace the `src` link below)*
<img alt="Step 5 - Networkwalks Hash Calculator" src="screenshots/04-nw-hash-calculator.png" />

### Step 6. Execute Dictionary Attack via Networkwalks Password Cracker (`W3-PM2`)
- Opened `https://networkwalks.com/password-cracker/` in the browser, pasted the copied `$pdf$` hash into the **PDF HASH (`$PDF$...`)** field, kept the active built-in wordlist (`100 words`), and clicked **START CRACKING**.
- **Attack Progress:** `Tried: 91 / 100` (`[+] MATCH password1`)
- **Cracked Password (`W3-PM2`):** `password1`

> *(Upload your Networkwalks Password Cracker screenshot to GitHub and replace the `src` link below)*
<img alt="Step 6 - Networkwalks Password Cracker" src="screenshots/05-nw-password-cracker.png" />

### Step 7. Unlock Encrypted PDF & Capture Completion Flag (`W3-PM1` & `W3-PM2`)
- Opened `My Locked PDF1.pdf` in the Debian PDF viewer (or decrypted via `qpdf --password=password1 --decrypt "My Locked PDF1.pdf" unlocked.pdf`) and entered the recovered password (`password1`).
- Confirmed full document decryption and captured the completion message:
  > *"Congratulations! You have captured your 1st flag."*

> *(Upload your unlocked PDF flag screenshot to GitHub and replace the `src` link below)*
<img alt="Step 7 - Unlocked PDF Flag" src="screenshots/06-unlocked-pdf-flag.png" />

---

## 💻 Complete All-in-One Debian Terminal Reference (`W3-PM1`)
```bash
# 1. Install John the Ripper (includes pdf2john.pl) if not already installed
sudo apt update && sudo apt install -y john

# 2. Verify John the Ripper and locate pdf2john.pl on Debian
john --list=build-info | head -n 5 && ls -l /usr/share/john/pdf2john.pl

# 3. Extract the PDF hash into hash1.txt and verify its contents
perl /usr/share/john/pdf2john.pl "My Locked PDF1.pdf" > hash1.txt && cat hash1.txt

# 4. Prepare a wordlist and run the dictionary attack, then show the cracked password
printf "123456\npassword\nadmin\nletmein\nqwerty\npassword1\n" > wordlist.txt
john --wordlist=wordlist.txt hash1.txt && john --show hash1.txt

# 5. Print the clean standalone $pdf$ hash string without the filename prefix (for W3-PM2)
perl /usr/share/john/pdf2john.pl "My Locked PDF1.pdf" | cut -d':' -f2
```

---

## 🔎 Audit Summary & Risk Analysis

> **Note:** The observations below represent findings from authorized offline password strength auditing on `My Locked PDF1.pdf`.

| ⚠️ Finding | 🧾 Evidence | 🎯 Potential Impact | 🚦 Risk Level |
| :--- | :--- | :--- | :--- |
| **Weak Dictionary-Based PDF Password** | Both JTR (`W3-PM1`) and NW Password Cracker (`W3-PM2`) recovered `password1` in seconds | Anyone obtaining the encrypted PDF can trivially unlock and read confidential contents | **Critical** |
| **Extractable 128-Bit PDF Hash Verifier** | `pdf2john.pl` & NW Hash Calculator extracted `$pdf$4*4*128` hash | Enables high-speed offline brute-force and dictionary attacks without lockout limits | **Medium** |

### Key Cryptographic Takeaways
- **Encryption vs. Hashing:** Encryption is a reversible **two-way** function requiring a key for decryption, whereas hashing is a **one-way** mathematical function that produces a unique message digest.
- **How Offline Cracking Works:** Tools like John the Ripper and the Networkwalks Password Cracker do not "decrypt" hashes—they compute hashes for candidate words in a wordlist and compare them against the target digest until a match is found.

---

## 🛡️ Password Hardening Recommendations
- **Enforce Strong Password Complexity & Length:** Require passphrases of at least **12–16+ characters** mixing uppercase, lowercase, numbers, and special symbols to resist dictionary and brute-force attacks.
- **Eliminate Common & Leaked Passwords:** Prohibit common dictionary words (`password1`, `123456`, `qwertyuiop`) and screen passwords against known breach lists.
- **Use Modern Document Encryption:** Protect sensitive PDFs and archives using **AES-256** encryption rather than legacy 128-bit revisions.
- **Implement Unique Credentials:** Never reuse passwords across sensitive documents or accounts; use a dedicated password manager to generate and store random passphrases.

---

## 📦 Week 3 Deliverables Checklist
- [x] **Essential Module 1 (`W3-PM1`):** Completed all steps on Debian Linux—installed/verified JTR, extracted `$pdf$` hash into `hash1.txt`, cracked `password1`, and unlocked `My Locked PDF1.pdf`.
- [x] **Essential Module 2 (`W3-PM2`):** Completed all steps—extracted `$pdf$` hash via Networkwalks Hash Calculator, cracked `password1` via Networkwalks Password Cracker, unlocked the PDF, and captured the 1st flag.

---

## 🐞 Problems Encountered & Solutions

### Problem 1. `pdf2john` Command & `rockyou.txt` Not Pre-Configured on Standard Debian Linux
Unlike Kali Linux, standard Debian Linux does not place `pdf2john` directly in `/usr/bin/` or ship with `/usr/share/wordlists/rockyou.txt` pre-installed.

**Solution:**
Installed `john` via `apt`, invoked the helper script directly via `perl /usr/share/john/pdf2john.pl`, and generated a clean local `wordlist.txt` file for immediate dictionary verification:
```bash
sudo apt install -y john
perl /usr/share/john/pdf2john.pl "My Locked PDF1.pdf" > hash1.txt
printf "123456\npassword\nadmin\nletmein\nqwerty\npassword1\n" > wordlist.txt
john --wordlist=wordlist.txt hash1.txt
```

### Problem 2. Formatting & Filename Prefix in `pdf2john.pl` Output
When running `perl /usr/share/john/pdf2john.pl "My Locked PDF1.pdf" > hash1.txt`, the output prepends the filename (`My Locked PDF1.pdf:$pdf$...`) to the hash line, whereas pasting into browser-based tools requires a standalone `$pdf$...` string without prefixes or `b'...'` wrappers.

**Solution:**
Used `cut -d':' -f2` when extracting a standalone `$pdf$` hash string for browser tools while keeping the standard `pdf2john.pl` output format in `hash1.txt` for John the Ripper:
```bash
# Clean hash string starting with $pdf$
perl /usr/share/john/pdf2john.pl "My Locked PDF1.pdf" | cut -d':' -f2
```
