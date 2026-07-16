# architecture.md

Version: 1.0

---

# Tech Stack

Backend
- Python 3.12+
- Google People API
- Google OAuth

Frontend
- Streamlit

Utilities
- pandas
- phonenumbers
- pydantic
- python-dotenv

AI
- OpenAI API (only for ambiguous fields)

---

# Project Structure

contact_merger/

├── app.py
├── config.py
├── auth.py
├── google_api.py
├── requirements.txt
│
├── engine/
│   ├── detector.py
│   ├── normalizer.py
│   ├── merger.py
│   ├── resolver.py
│   └── updater.py
│
├── models/
│   ├── contact.py
│   ├── duplicate_group.py
│   ├── merged_contact.py
│   └── merge_plan.py
│
├── ui/
│   ├── review.py
│   └── diff.py
│
├── backups/
├── logs/
├── docs/
│   ├── PRD.md
│   ├── architecture.md
│   ├── Rules.md
│   ├── phases.md
│   ├── design.md
│   └── memory.md
│
└── tests/

---

# High Level Flow

Google Contacts

↓

Download Contacts

↓

Normalize Data

↓

Find Duplicate Groups

↓

Build Merged Contact

↓

Generate Merge Plan

↓

User Review

↓

Update Primary Contact

↓

Verify Update

↓

Delete Duplicate Contacts

---

# Merge Philosophy

Duplicate Group

↓

Merged Contact (Memory Only)

↓

Merge Plan

↓

Google Update

No contact is modified until the user approves.

---

# Primary Contact Selection

The surviving contact is chosen automatically.

Preference order:

1. Richest metadata
2. Has photo
3. Most populated fields
4. Oldest Google contact (if available)

The merged information is written into this contact.

Remaining contacts are deleted after successful verification.

---

# AI Responsibilities

AI is NOT used for:

- duplicate detection
- phone normalization
- merging unique values
- deleting contacts

AI MAY be used for:

- conflicting names
- conflicting notes
- explaining merge decisions

---

# Backup Strategy

Before every merge:

- Export original contacts
- Save merge plan
- Save merge result
- Write merge log

Nothing is permanently deleted without backup.

---

# Future Extensions

- VCF support
- Outlook
- iCloud
- Batch merge
- Undo
- Similar-name detection
- Merge history
