# Rules.md

Version: 1.0

---

# Core Principle

Data preservation is the highest priority.

Never lose information while merging contacts.

---

# General Rules

- Write clean, modular and readable code.
- Prefer explicit code over clever code.
- Every module should have a single responsibility.
- Avoid unnecessary abstractions.
- Keep functions short and testable.

---

# Merge Rules

Never overwrite information.

Always merge unique values.

Examples:

Emails:
A + B -> Union

Phone Numbers:
Normalize only for comparison.
Retain original formatting in stored contact.

Addresses:
Keep every unique address.

Organizations:
Keep every unique organization.

Events:
Keep every unique event.

Notes:
Append unique content.
AI may assist if necessary.

---

# Duplicate Detection

Current version:

- Phone number
- Normalised name, also without Roll number and branch or other informations

Normalization should ignore:

- +country code
- spaces
- hyphens
- brackets

The original phone number format must never be modified.

---

# Primary Contact

The surviving contact should be selected automatically.

Preference:

1. Richest metadata
2. Has photo
3. Most populated fields

The merged information is written into this contact.

Only after successful verification should duplicate contacts be deleted.

---

# AI Boundaries

AI should NOT:

- detect duplicates
- normalize phone numbers
- merge deterministic fields
- delete contacts
- update Google contacts

AI MAY:

- resolve conflicting names
- merge conflicting notes
- explain merge decisions

If deterministic logic can solve a problem,
AI must not be used.

---

# Error Handling

Never continue after a failed Google API update.

Always:

- show the error
- keep backups
- stop deletion

Deletion must only occur after a verified successful update.

---

# Logging

Log every important action.

Include:

- timestamp
- contact IDs
- merge result
- deleted contacts
- errors

---

# Backups

Always create backups before modifying contacts.

Backups should be sufficient to restore deleted contacts.

---

# Libraries

Preferred

- google-api-python-client
- google-auth
- google-auth-oauthlib
- phonenumbers
- pandas
- pydantic
- streamlit
- python-dotenv

Avoid

- Selenium
- Browser automation
- Web scraping
- Direct HTML parsing

Always use official Google APIs.

---

# Code Style

- Type hints everywhere.
- Dataclasses or Pydantic models preferred.
- Constants in config.py.
- No hardcoded credentials.
- Environment variables for secrets.

---

# Future Contributors

When adding features:

- Preserve backwards compatibility.
- Do not change merge behaviour without discussion.
- Keep merge logic deterministic whenever possible.
