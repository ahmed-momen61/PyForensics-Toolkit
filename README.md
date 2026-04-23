# 🔍 PyForensics Toolkit

![Python](https://img.shields.io/badge/Python-3.x-blue?style=for-the-badge&logo=python)
![Category](https://img.shields.io/badge/Category-Digital%20Forensics%20(DFIR)-darkred?style=for-the-badge)
![Status](https://img.shields.io/badge/Status-Completed-success?style=for-the-badge)

## 📌 Repository Overview
This repository contains a collection of custom Python scripts developed for digital forensic investigations (specifically tailored for coursework KH5036CMD). These lightweight utilities are designed to automate the extraction and analysis of critical artifacts from raw disk images and Windows environments without the immediate need for heavy commercial forensic suites.

Currently, the toolkit includes two primary utilities:
1. **MBR Partition Table Analyzer** (`mbr_analyzer.py`)
2. **Windows Registry Forensic Artifact Extractor** (`forensic_extractor.py`)

---

## 🛠️ Tool 1: MBR Partition Table Analyzer
A specialized utility designed to parse the Master Boot Record (MBR) of a raw disk image. It verifies the disk structure and automatically identifies the correct starting sector of target partitions for mounting and analysis.

### ✨ Features
* **MBR Parsing:** Reads the first 512 bytes of the disk image to locate the partition table.
* **Partition Enumeration:** Iterates through the four primary partition entries.
* **Binary Data Decoding:** Utilizes the `struct` library (`<B 3x B 3x I I`) to unpack binary data into human-readable fields:
  * **Status:** Identifies Bootable vs. Non-Bootable partitions.
  * **Type:** Extracts the file system type code (e.g., `0x7` for NTFS).
  * **Start Sector & Size:** Calculates exact LBA offsets and capacity.
* **Target Highlighting:** Automatically flags Partition 2 (Start: 206848) for specific coursework task requirements.

### 🚀 Usage
1. Place `mbr_analyzer.py` in the same directory as your forensic disk image (Default target: `CW Image.dd`).
2. Run the script:
   ```bash
   python mbr_analyzer.py
