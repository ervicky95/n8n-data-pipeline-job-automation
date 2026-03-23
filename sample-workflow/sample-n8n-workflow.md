# 🔍 Sample Workflow (Sanitized Overview)

## 📌 Note

This is a **high-level representation** of the workflow.

⚠️ Full workflow JSON is NOT included to protect:
- Proprietary prompts
- Business logic
- API configurations

---

## 🔄 Workflow Logic Overview

### Step 1: Trigger
- RSS Feed Trigger (every 10 minutes)

---

### Step 2: Deduplication
- Check URL in Google Sheets
- Skip if already processed

---

### Step 3: Data Extraction
- HTTP Request to fetch article HTML

---

### Step 4: Data Cleaning
- Remove:
  - Scripts
  - Ads
  - Social links
- Extract main content

---

### Step 5: AI Processing

#### Content Generation
- Convert HTML → structured job post

#### Content Formatting
- Convert → WordPress HTML format

---

### Step 6: SEO Enrichment
- Title, slug, meta generation
- Keyword extraction

---

### Step 7: Categorization
- Map categories using:
  - Google Sheets reference
  - AI semantic matching

---

### Step 8: Tag Processing
- Generate tags from keywords
- Create if not exists

---

### Step 9: Publishing
- Create post via WordPress API
- Assign categories & tags

---

### Step 10: SEO Update
- Update RankMath metadata

---

### Step 11: Logging
- Store results in Google Sheets

---

## 🧠 Key Design Decisions

- Idempotent pipeline (deduplication)
- Modular processing layers
- AI-driven transformation
- API-first architecture
- Validation at each stage

---

## 🔐 Why JSON is Not Included

This workflow contains:
- Advanced prompt engineering
- Custom business logic
- API integrations

To prevent misuse, only a **sanitized architecture and explanation** are shared.

---

## 💼 Recruiter Note

Full workflow and implementation can be demonstrated during:
- Technical interviews
- Live walkthrough sessions