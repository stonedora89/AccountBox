# AccountBox
AccountBox account password

# KeyNest

> Local First Digital Asset Vault for Apple Ecosystem

Version: 1.0

---

# 1. Product Overview

## Product Name

**KeyNest**

## Vision

A local-first digital asset vault for individuals.

KeyNest is not a traditional password manager.

Instead, it is a secure personal repository for managing:

* Accounts
* Passwords
* API Keys
* MFA Recovery Codes
* Subscription Information
* Software Licenses
* Domain Registrations
* Cloud Platform Credentials

The primary goal is:

> Help users understand, organize, and securely manage their digital assets.

---

# 2. Design Principles

## Local First

All user data remains on the device.

No mandatory cloud storage.

No account registration.

No external server.

---

## Privacy First

Sensitive information is encrypted before storage.

No telemetry.

No analytics.

No tracking.

---

## Offline First

Application must function without internet access.

All core features available offline.

---

## Apple Native Experience

Built specifically for:

* iPhone
* Mac

Using Apple's native frameworks.

---

# 3. Target Users

## Phase 1

Personal use.

Typical assets include:

* ChatGPT
* Claude
* DeepSeek
* GitHub
* AWS
* Azure
* Google
* Apple ID
* Domain Providers
* Exam Platforms

---

## Phase 2

Professional users:

* Developers
* Security Engineers
* Consultants
* IT Administrators
* Power Users

---

# 4. MVP Scope

## Features Included

### Account Management

Create

Read

Update

Delete

Digital asset records.

---

### Search

Search by:

* Title
* URL
* Email
* Username
* Tags

---

### Tag Management

Default tags:

* AI
* Work
* Study
* Banking
* Cloud
* Subscription
* Development
* Personal

Custom tags supported.

---

### Security

* Master Password
* Face ID
* Touch ID
* Local Encryption

---

### Import / Export

Encrypted backup export.

Encrypted backup import.

---

# 5. Data Model

## VaultRecord

```swift
struct VaultRecord {

    var id: UUID

    var title: String

    var website: String

    var username: String

    var email: String

    var phone: String

    var password: String

    var apiKey: String

    var recoveryCode: String

    var notes: String

    var tags: [String]

    var createdAt: Date

    var updatedAt: Date
}
```

---

# 6. UI Structure

## Home Screen

Display all records.

Functions:

* Search
* Filter
* Sort

Display:

* Name
* Tag
* Last Updated Time

---

## Detail Screen

Fields:

* Title
* Website
* Username
* Email
* Phone
* Password
* API Key
* Recovery Code
* Notes
* Tags

Actions:

* Copy
* Edit
* Delete

---

## Add Record Screen

Allow manual creation.

Support quick paste parsing.

Example input:

```text
https://chatgpt.com
user@gmail.com
Password123
```

Expected result:

* Website detected
* Email detected
* Suggested title generated

---

## Settings Screen

Features:

* Face ID Toggle
* Export Vault
* Import Vault
* Change Master Password

---

# 7. Security Architecture

## Authentication

### First Launch

User creates:

* Master Password

Requirements:

* Minimum 12 characters

---

### Unlock Methods

Primary:

* Face ID

Fallback:

* Master Password

---

## Encryption

Framework:

```text
CryptoKit
```

Algorithm:

```text
AES-256-GCM
```

Encrypted Fields:

* Password
* API Key
* Recovery Code
* Notes

---

## Key Storage

Framework:

```text
Keychain
```

Store:

* Encryption Key

Never store:

* Plaintext Passwords

---

# 8. Backup Format

## File Extension

```text
.knvault
```

---

## Structure

```json
{
  "version": "1.0",
  "records": []
}
```

Entire file encrypted using AES-256-GCM.

---

# 9. Synchronization Strategy

## MVP

No real-time sync.

Supported:

* Export
* Import
* AirDrop Transfer

Workflow:

```text
Mac Export
↓
AirDrop
↓
iPhone Import
↓
Merge Records
```

---

## Merge Logic

Primary Key:

```text
UUID
```

Conflict Resolution:

```text
Latest updatedAt wins
```

---

# 10. Technical Stack

## UI

```text
SwiftUI
```

## Persistence

```text
SwiftData
```

## Encryption

```text
CryptoKit
```

## Authentication

```text
LocalAuthentication
```

## Secure Storage

```text
Keychain
```

---

# 11. Architecture

```text
Presentation Layer
│
├── SwiftUI Views
│
Application Layer
│
├── VaultService
├── SecurityService
├── BackupService
│
Persistence Layer
│
├── SwiftData
│
Security Layer
│
├── CryptoKit
├── Keychain
│
System Layer
│
├── FaceID
├── TouchID
```

---

# 12. Roadmap

## V1

Core Vault

* CRUD
* Search
* Tags
* Encryption
* Face ID
* Export
* Import

---

## V2

Security Features

* Password Generator
* Weak Password Detection
* Duplicate Password Detection
* Subscription Tracking
* API Key Management

---

## V3

AI Features

Natural Language Queries:

Examples:

```text
Which accounts use Gmail?

Which accounts do not have MFA enabled?

Which subscriptions expire next month?

Show all OpenAI-related accounts.
```

AI Features:

* Auto Categorization
* Smart Search
* Quick Record Creation

---

# 13. Development Plan

## Week 1

* Project Setup
* SwiftData Models
* Home Screen
* Add/Edit Screen

---

## Week 2

* CRUD Operations
* Search
* Tag Management

---

## Week 3

* CryptoKit Encryption
* Keychain Integration

---

## Week 4

* Face ID
* Master Password

---

## Week 5

* Backup Export
* Backup Import

---

## Week 6

* Mac Optimization
* UI Polish
* Testing

---

# Success Criteria

A user can:

1. Store all digital assets locally.
2. Protect data using Face ID and encryption.
3. Backup data securely.
4. Transfer data between Mac and iPhone manually.
5. Manage hundreds of accounts efficiently.

Without relying on any cloud service.
