# 🏗️ Architecture Explanation

## 📌 Overview

This system is an **event-driven, AI-powered content automation pipeline** built using **n8n**, designed to ingest job-related content, process it using LLMs, enrich it with SEO metadata, and publish it to WordPress.

The architecture follows a **modular ETL + AI enrichment pattern**, ensuring scalability, fault tolerance, and maintainability.

---

## 🧱 Architecture Layers

### 1. Ingestion Layer

- **RSS Feed Trigger**
  - Polls: `https://sarkariujala.com/feed/`
  - Frequency: Every 10 minutes
  - Acts as the event source

---

### 2. Deduplication Layer

- **Google Sheets (Input Table)**
  - Stores processed URLs
  - Prevents duplicate ingestion
  - Uses lookup on URL field

---

### 3. Extraction Layer

- **HTTP Request Node**
  - Fetches raw HTML from article URL
  - Handles external web ingestion

---

### 4. Data Cleaning Layer

- **Custom JS Function (Code Node)**
  - Removes:
    - `<script>`, `<style>`
    - Ads, banners
    - WhatsApp/Telegram/social blocks
    - sarkariujala branding

  - Extracts:
    - Main content using regex-based selectors

  - Adds metadata:
    - `processedAt`
    - `contentLength`
    - `originalUrl`

---

### 5. Transformation Layer (AI Core)

#### Content Generation (LLM)
- Model: OpenAI GPT-4.1-mini
- Converts raw HTML → structured job notification (Markdown)

#### Content Formatting
- Converts Markdown → WordPress HTML
- Applies strict:
  - Heading structure
  - Table styling
  - SEO-friendly layout

---

### 6. Enrichment Layer

#### SEO Metadata
- Title
- Slug
- Meta description

#### Keyword Generation
- Focus keyword + supporting keywords
- Output:
  - Array
  - Comma-separated string

#### Category Mapping
- Uses Google Sheets reference
- Semantic matching via LLM

#### Internal Linking
- Pulls previous posts (last 10 days)
- Injects contextual links

---

### 7. Control & Validation Layer

- Content validation (length + structure)
- Title/meta validation
- Category validation
- WordPress publish validation

- Retry logic enabled on:
  - LLM nodes
  - HTTP requests

---

### 8. Publishing Layer

#### WordPress API

- Create post
- Assign:
  - Categories
  - Tags (dynamic creation)
- Upload:
  - Content
  - Featured image
  - Metadata (RankMath)

---

### 9. Storage & Logging Layer

- **Google Sheets (Post Data Table)**

Stores:
- Title
- URL
- Keywords
- Category IDs
- Tag IDs
- Post ID
- Status

---

## 🔄 Architecture Pattern

- Event-driven ingestion
- Stateless transformations
- API-based serving
- Persistent logging

---

## ⚙️ Design Principles

- Modular node-based design
- Idempotent processing (via deduplication)
- AI-first transformation
- Validation-driven pipeline
- External system integration (WordPress, Sheets)

---

## 📈 Scalability Improvements

- Replace Google Sheets → BigQuery / Snowflake
- Replace n8n → Airflow / Prefect
- Add queue → Kafka / PubSub
- Add monitoring → Prometheus + Grafana

---

## 🧠 Summary

This architecture combines:

- ETL pipeline design
- AI content processing
- SEO automation
- CMS integration

Making it a **real-world data engineering + AI system**.