# Forensic File Integrity & Encryption System (SecureRepair)

## Overview

This project is a forensic-grade file protection system designed to secure sensitive data and detect unauthorized modifications. It combines **AES-256 encryption** for confidentiality and **Merkle tree-based hashing** for fine-grained integrity verification.

---

## Key Features

*  AES-256 encryption for protecting files
*  Merkle tree-based hashing for integrity verification
*  Snapshot-based forensic analysis
*  Detects:

  * New files
  * Deleted files
  * Modified files
*  Identifies exact modified portions using chunk-level detection
*  Encrypted snapshot to prevent tampering

---

## System Workflow

### Before System Exposure (e.g., repair)

1. Encrypt all files
2. Generate snapshot using Merkle trees
3. Encrypt snapshot

### After System Access

1. Decrypt snapshot
2. Generate new snapshot
3. Compare with original
4. Produce forensic report

---

## Merkle Tree Concept

* Files are divided into chunks (default: 1KB)
* Each chunk is hashed using SHA-256
* Hashes are combined to form a Merkle root
* Any change in file → changes root → detected

---

## Tech Stack

* Python
* AES-256 (cryptography library)
* SHA-256 hashing
* JSON for snapshot storage
* File system operations

---

## Example Output

```
📊 FORENSIC REPORT

🆕 New Files:
  + hacker.enc

❌ Deleted Files:
  - file1.txt.enc

⚠️ Modified Files:
  * file.txt.enc
    Changed chunks: [0]
```

---

## How to Run

### 1. Install dependencies

```bash
pip install cryptography
```

### 2. Encrypt files & create snapshot

```bash
python enfi.py
```

### 3. Scan for tampering

```bash
python scan.py
```

---

## Key Insights

* Traditional hashing only detects if a file changed
* This system detects **which part of the file changed**
* Combines **confidentiality + integrity + forensic analysis**

---

## Highlights

* Chunk-level tamper detection
* Secure snapshot storage
* Practical real-world use case
* Inspired by blockchain (Merkle trees)

---

## Future Improvements

* GUI-based interface
* Real-time monitoring
* Cloud backup for snapshots
* Alert/notification system

---

## Author

**Chadive Revanth Sai Reddy**

