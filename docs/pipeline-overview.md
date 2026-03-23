# 🔄 Pipeline Overview

## 📌 Definition

This pipeline is an **automated ETL + AI enrichment system** that transforms raw web content into structured, SEO-optimized WordPress posts.

---

## ⚙️ Pipeline Stages

### 1. Extract (Ingestion)

- RSS Feed Trigger
- Fetch new job articles every 10 minutes

---

### 2. Deduplication

- Check URL in Google Sheets
- Skip already processed records

---

### 3. Data Extraction

- HTTP request to fetch raw HTML

---

### 4. Data Cleaning

- Remove unwanted HTML elements
- Extract main content
- Validate minimum content length

---

### 5. Transformation (AI Processing)

#### Step 1: Content Generation
- Convert raw HTML → job notification format

#### Step 2: Formatting
- Convert content → WordPress HTML

---

### 6. Enrichment

- Generate:
  - Title
  - Slug
  - Meta
- Generate keywords
- Map categories
- Add internal links

---

### 7. Publishing (Load)

- Create WordPress post
- Assign:
  - Categories
  - Tags
- Upload SEO metadata

---

### 8. Logging

- Store processed data in Google Sheets

---

## 🔁 Pipeline Type

- Event-driven
- Micro-batch processing
- API-integrated ETL

---

## 📊 Input → Output

**Input:**
- RSS Feed URL

**Output:**
- Published WordPress blog post
- SEO metadata
- Structured content

---

## 🧠 Summary

Pipeline Flow:

RSS → Clean → AI Transform → Enrich → Publish → Log