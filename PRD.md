# Contact Merge Engine (CME)

Version: 1.0
Status: Draft

---

# Overview

Contact Merge Engine (CME) is a desktop application that intelligently detects duplicate contacts in a user's Google Contacts account and safely merges them without losing information.

Unlike existing contact cleaners, CME focuses on **information preservation** rather than simply removing duplicates.

The application builds a merged representation of duplicate contacts by combining all unique information and allows the user to review every merge before any changes are made.

No contact is modified or deleted without explicit user approval.

---

# Problem Statement

Many users accumulate duplicate contacts over time because of:

- Importing contacts from multiple devices
- SIM card imports
- WhatsApp sync
- Gmail synchronization
- Manual contact creation
- CSV / VCF imports

Current solutions often:

- delete contacts
- overwrite information
- choose one contact over another
- lose emails, notes, addresses or metadata

Users therefore avoid automatic cleaning because they fear losing information.

---

# Vision

Build the safest contact merging tool possible.

The application should preserve every piece of useful information while making duplicate cleanup almost effortless.

---

# Target Users

Primary Users

- People with hundreds or thousands of contacts
- Students
- Professionals
- Recruiters
- Business users

Secondary Users

- IT administrators
- Phone repair shops
- Data migration professionals

---

# Goals

The application should:

✓ Detect duplicate contacts

✓ Preserve every unique piece of information

✓ Never silently delete data

✓ Allow user review before merge

✓ Maintain backups

✓ Be deterministic whenever possible

✓ Use AI only when human judgement is required

---

# Non Goals

The application is NOT intended to:

- Replace Google Contacts
- Synchronize contacts across platforms
- Edit contacts manually
- Become a CRM
- Automatically merge without review

---

# Supported Platforms

Initial Release

- Windows
- macOS
- Linux

---

# Contact Sources

Initial Release

Google Contacts

Future

- VCF files
- CSV
- Outlook
- iCloud

---

# Duplicate Detection

Initial Release

Duplicate detection based on:

- Phone number

Future versions may support:

- Email
- Similar names
- Organization
- Address
- Multiple confidence levels

---

# Merge Philosophy

The system should **never throw away information**.

Instead of selecting one contact and deleting another, the application should create a merged representation by combining every unique field.

Example

Contact A

Phone
Email A

Contact B

Phone
Email B
Company

Merged Contact

Phone
Email A
Email B
Company

---

# Review Workflow

For every duplicate group

1. Detect duplicates

2. Build merged contact

3. Show side-by-side comparison

4. Allow user to review

5. User approves

6. Update one existing contact

7. Delete remaining duplicate contacts

---

# Safety Principles

The application must:

- Never delete before successful update
- Verify update before deletion
- Keep automatic backups
- Allow merge preview
- Generate merge logs

---

# AI Usage

AI should only assist with fields that cannot be resolved deterministically.

Examples:

- Choosing between conflicting names
- Merging free-text notes
- Explaining merge decisions

AI must never:

- Delete contacts
- Override deterministic rules
- Make irreversible changes automatically

---

# Future Features

- Undo merge
- Batch approvals
- Duplicate confidence score
- Similar-name detection
- Smart note merging
- Merge history
- Contact statistics
- Dark mode
- Export merge reports
- Backup restoration
- Keyboard shortcuts

---

# Success Criteria

The project is considered successful if:

- No information is lost during merges.
- Users can review every merge.
- Duplicate cleanup becomes significantly faster than manual editing.
- The application remains safe even for users with thousands of contacts.

---

# Guiding Principle

"Preserve information first. Automate second."

Every design decision should prioritize data preservation and user trust over aggressive automation.
