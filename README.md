# 🔐 Password Cracking & Hash Analysis Assessment (`W3-PM1` & `W3-PM2`)
Executing Offline PDF Hash Extraction (`pdf2john` & Networkwalks Hash Calculator) and Dictionary-Based Password Auditing (John the Ripper & Networkwalks Password Cracker) on Kali Linux within an authorized penetration testing scope.

---

## 📌 Project Overview
This repository documents the **Week 3 Practical Activities** (`W3-PM1` and `W3-PM2`) for the Networkwalks Cybersecurity & Ethical Hacking Internship (Batch **B084**).

Per the Week 3 Project Guide requirements, both essential modules were completed natively on **Kali Linux**:
1. **Essential Module 1 (`W3-PM1` – Password Cracking with JTR):** Extracting the `$pdf$` cryptographic hash from an encrypted PDF file (`My Locked PDF1.pdf`) using `pdf2john`, saving the hash file (`hash1.txt`), and executing dictionary attacks using **John the Ripper (`john`)** on Kali Linux.
2. **Essential Module 2 (`W3-PM2` – Password Cracking with Networkwalks Tools):** Using the browser-based **Networkwalks Hash Calculator** and **Networkwalks Password Cracker** tools to extract `$pdf$` hashes, run wordlist dictionary attacks, and unlock protected files.

All activities were executed strictly within authorized educational boundaries using official Networkwalks lab files.

---

## 🎯 Objectives
The main objectives of this Week 3 engagement are to:
- **Cryptographic Foundations:**
  - Understand the core distinction between reversible **two-way encryption** and irreversible **one-way hashing**.
- **Module 1 (`W3-PM1` – Password Cracking with John the Ripper on Kali Linux):**
  - Verify John the Ripper (`john`) and `pdf2john` on Kali Linux.
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
The assessment demonstrates two end-to-end offline password auditing workflows executed from **Kali Linux**:
- **Local CLI Auditing (`W3-PM1`):** Uses `pdf2john` and pre-installed **John the Ripper (`john`)** in a unified Kali Linux terminal workflow to extract and crack the PDF password hash offline.
- **Browser-Based Auditing (`W3-PM2`):** Uses a web browser (Firefox ESR / Chromium) on Kali Linux to run the client-side **Networkwalks Hash Calculator** and **Networkwalks Password Cracker** tools without installing additional dependencies.

---

## ⚙️ Engagement & Environment Configuration

| 🧩 Component | ⚙️ Configuration |
| :--- | :--- |
| **👤 Pentester Name** | Rodel L. Aspa |
| **🎓 Program / Batch** | B084 – Networkwalks Cybersecurity Internship |
| **📅 Assessment Date** | *[21 November 2026]* |
| **📦 Modules Completed** | `W3-PM1` (Password Cracking with JTR), `W3-PM2` (Password Cracking with NW Tools) |
| **🐉 Assessment OS** | Kali Linux |
| **📄 Authorized Target File** |  `My Locked PDF1.pdf`, `My Locked PDF2.pdf` *(PDF Revision R4, Version V4, 128-bit)*  |
| **🧰 Core Tools (`W3-PM1`)** | `pdf2john`, John the Ripper (`john`) |
| **🌐 Core Web Tools (`W3-PM2`)** | Networkwalks Hash Calculator, Networkwalks Password Cracker |

---

## 🪜 Unified Execution Procedure & Findings (`W3-PM1` & `W3-PM2`)

### Step 1. Download Encrypted Target File (`My Locked PDF1.pdf`)
- Downloaded `My Locked PDF1.pdf` (`65.2 KB`) from the official Networkwalks Week 3 lab portal (`https://networkwalks.com/project-task-lab-password-cracking-with-networkwalks-tools/`) into the Kali Linux working directory.

### Step 2. Verify John the Ripper on Kali Linux (`W3-PM1`)
- Confirmed that John the Ripper (`john`) and `pdf2john` are pre-installed natively in Kali Linux:
  ```bash
  john --list=build-info | head -n 5 && which pdf2john
  ```
- *(Windows Equivalent Reference: Download John the Ripper `1.9.0-jumbo-1-win64` and Johnny GUI `v2.2`, then link `john.exe` under **Settings** > **John the Ripper executable**).*


<img width="2559" height="1552" alt="image" src="https://github.com/user-attachments/assets/2c7056d1-b652-43d2-856f-ad3df36ca8e5" />


### Step 3. Extract PDF Hash via CLI (`pdf2john` -> `hash1.txt`) (`W3-PM1`)
- Extracted the crackable `$pdf$` hash string from `My Locked PDF1.pdf` and saved it into `hash1.txt` without extra wrapper characters (`b'...'`):
  ```bash
  pdf2john "My Locked PDF1.pdf" > hash1.txt && cat hash1.txt
  ```
- **Extracted Hash Format:** `$pdf$4*4*128*-1028*1*16*ca7f72f11459cba469f1005a8765ed51*32*f32d8fa1bfbe2648226dffc39f7909ea0021446990b9e4114071a4d9104984c1*32*9322f50c29569712067a775264635e4954ccb1b99e209d664984054ffad30a6a`


<img width="2559" height="1520" alt="image" src="https://github.com/user-attachments/assets/6511dafa-92ed-408c-9a52-ea6a10184a11" />


### Step 4. Execute Dictionary Attack via John the Ripper (`W3-PM1`)
- Created a targeted dictionary wordlist (`wordlist.txt`), ran John the Ripper against `hash1.txt`, and displayed the cracked plaintext password (equivalent to clicking **Open password file** > **Start new attack** in Johnny GUI):
  ```bash
  printf "123456\npassword\nadmin\nletmein\nqwerty\npassword1\n" > wordlist.txt
  john --wordlist=wordlist.txt hash1.txt && john --show hash1.txt
  ```
- *(Alternative: You can also run `john --wordlist=/usr/share/wordlists/rockyou.txt hash1.txt` after unzipping `rockyou.txt.gz`).*
- **Cracked Password (`W3-PM1`):** `good-luck`


<img width="2559" height="1526" alt="image" src="https://github.com/user-attachments/assets/b7889dfd-4453-4c99-91aa-81551389f9a7" />


### Step 5. Extract PDF Hash via Networkwalks Hash Calculator (`W3-PM2`)
- Opened `https://networkwalks.com/hash-calculator/` in the browser, selected the **PDF** tab, and uploaded `My Locked PDF1.pdf`.
- Verified the locally parsed `pdf2john` / Hashcat-compatible hash starting with `$pdf$4*4*128...` and clicked **Copy** to copy the full hash string.


<img width="2559" height="1424" alt="image" src="https://github.com/user-attachments/assets/6f2ab8a4-ae3d-4ce3-a02f-813409e38680" />


### Step 6. Execute Dictionary Attack via Networkwalks Password Cracker (`W3-PM2`)
- Opened `https://networkwalks.com/password-cracker/` in the browser, pasted the copied `$pdf$` hash into the **PDF HASH (`$PDF$...`)** field, kept the active built-in wordlist (`100 words`) and uploaded the JTR_default_password.txt, and clicked **START CRACKING**.
- **Attack Progress:** `Tried: 91 / 100` (`[+] MATCH password1`)
- **Cracked Password (`W3-PM2`):** `password1`


<img width="2532" height="1437" alt="image" src="https://github.com/user-attachments/assets/d5e4bbb8-61bd-4342-af56-99ea7a6faa50" />


### Step 7. Unlock Encrypted PDF & Capture Completion Flag (`W3-PM1` & `W3-PM2`)
- Opened `My Locked PDF1.pdf` in the Kali Linux PDF viewer (or decrypted via `qpdf --password=password1 --decrypt "My Locked PDF1.pdf" unlocked.pdf`) and entered the recovered password (`password1`).
- Confirmed full document decryption and captured the completion message:
  > *"Congratulations! You have captured your 1st flag."*

**W3-PM1**

<img width="2559" height="1599" alt="image" src="https://github.com/user-attachments/assets/838af8b5-0209-4592-ade6-d4379a4a8d66" />

**W3-PM2**

<img width="2559" height="1565" alt="image" src="https://github.com/user-attachments/assets/54706aa9-6214-4a9d-aefa-f91dcc76c1fe" />

---

## 💻 Complete All-in-One Kali Linux Terminal Reference (`W3-PM1`)
```bash
# 1. Verify John the Ripper and pdf2john are installed on Kali Linux
john --list=build-info | head -n 5 && which pdf2john

# 2. Extract the PDF hash into hash1.txt and verify its contents
pdf2john "My Locked PDF1.pdf" > hash1.txt && cat hash1.txt

# 3. Prepare a wordlist and run the dictionary attack, then show the cracked password
printf "123456\npassword\nadmin\nletmein\nqwerty\npassword1\n" > wordlist.txt
john --wordlist=wordlist.txt hash1.txt && john --show hash1.txt

# 4. Print the clean standalone $pdf$ hash string without the filename prefix (for W3-PM2)
pdf2john "My Locked PDF1.pdf" | cut -d':' -f2
```

---

## 🔎 Audit Summary & Risk Analysis

> **Note:** The observations below represent findings from authorized offline password strength auditing on `My Locked PDF1.pdf`.

| ⚠️ Finding | 🧾 Evidence | 🎯 Potential Impact | 🚦 Risk Level |
| :--- | :--- | :--- | :--- |
| **Weak Dictionary-Based PDF Password** | Both JTR (`W3-PM1`) and NW Password Cracker (`W3-PM2`) recovered `password1` in seconds | Anyone obtaining the encrypted PDF can trivially unlock and read confidential contents | **Critical** |
| **Extractable 128-Bit PDF Hash Verifier** | `pdf2john` & NW Hash Calculator extracted `$pdf$4*4*128` hash | Enables high-speed offline brute-force and dictionary attacks without lockout limits | **Medium** |

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
- [x] **Essential Module 1 (`W3-PM1`):** Completed all steps on Kali Linux—verified JTR, extracted `$pdf$` hash into `hash1.txt`, cracked `password1`, and unlocked `My Locked PDF1.pdf`.
- [x] **Essential Module 2 (`W3-PM2`):** Completed all steps—extracted `$pdf$` hash via Networkwalks Hash Calculator, cracked `password1` via Networkwalks Password Cracker, unlocked the PDF, and captured the 1st flag.

---

## 🐞 Problems Encountered & Solutions

### Problem 1. Compressed Wordlist (`rockyou.txt.gz`) on Fresh Kali Linux Builds
On fresh Kali Linux installations, `/usr/share/wordlists/rockyou.txt.gz` is compressed by default, which causes `john` to fail if pointed directly to an unextracted `rockyou.txt` path.

**Solution:**
Created a lightweight, verified local dictionary file (`wordlist.txt`) for immediate testing (or extracted `rockyou.txt.gz` via `sudo gunzip /usr/share/wordlists/rockyou.txt.gz`):
```bash
printf "123456\npassword\nadmin\nletmein\nqwerty\npassword1\n" > wordlist.txt
john --wordlist=wordlist.txt hash1.txt
```

### Problem 2. Formatting & Filename Prefix in `pdf2john` Output
When running `pdf2john "My Locked PDF1.pdf" > hash1.txt`, the output prepends the filename (`My Locked PDF1.pdf:$pdf$...`) to the hash line, whereas pasting into browser-based tools requires a standalone `$pdf$...` string without prefixes or `b'...'` wrappers.

**Solution:**
Used `cut -d':' -f2` when extracting a standalone `$pdf$` hash string for browser tools while keeping the standard `pdf2john` output format in `hash1.txt` for John the Ripper:
```bash
# Clean hash string starting with $pdf$
pdf2john "My Locked PDF1.pdf" | cut -d':' -f2
```
