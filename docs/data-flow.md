# 🔀 Data Flow

## 📌 Overview

This document explains how data flows across the pipeline from ingestion to publishing.

---

## 🔄 Step-by-Step Flow

### Step 1: Trigger

RSS Feed Trigger emits:
- title
- link
- pubDate

---

### Step 2: Deduplication

- Check URL in Google Sheets
- If exists → STOP
- Else → continue

---

### Step 3: Fetch Content

HTTP Request:
- Input: URL
- Output: raw HTML

---

### Step 4: Clean Content

JS Function:
- Input: raw HTML
- Output:
  - cleanedHtml
  - metadata

---

### Step 5: AI Processing

#### Content Generator
Input:
- cleanedHtml

Output:
- structured markdown content

---

### Step 6: Formatting

- Convert to WordPress HTML
- Apply styling + structure

---

### Step 7: Metadata Generation

- Title, Slug, Meta
- Keywords (array + string)

---

### Step 8: Category Mapping

- Input:
  - Title
  - Meta
- Output:
  - category IDs

---

### Step 9: Tag Processing

- Split keywords
- Create tags if not exist
- Collect tag IDs

---

### Step 10: Internal Linking

- Fetch previous posts
- Inject links into content

---

### Step 11: Final Assembly

Prepare:
- Title
- Content
- Slug
- Category IDs
- Tag IDs
- Meta

---

### Step 12: Publish

WordPress API:
- Create post
- Update SEO metadata

---

### Step 13: Logging

Store in Google Sheets:
- Post ID
- Title
- Keywords
- Category
- Tags

---

## 🔁 Data Transformation Summary

| Stage | Input | Output |
|------|------|--------|
| Ingestion | RSS | URL |
| Extraction | URL | HTML |
| Cleaning | HTML | Cleaned content |
| AI | Content | Structured content |
| Enrichment | Content | SEO data |
| Publishing | Final data | WordPress post |

---

## 🧠 Summary

The pipeline ensures:

- Clean data flow
- Structured transformations
- Reliable publishing