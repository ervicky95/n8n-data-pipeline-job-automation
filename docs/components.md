# 🧩 Components

## 📌 Overview

This pipeline consists of multiple modular components, each responsible for a specific task.

---

## 🔹 Core Components

### 1. Trigger

- RSS Feed Trigger
- Entry point of pipeline

---

### 2. Storage

- Google Sheets (Input)
- Google Sheets (Post Data)

---

### 3. Processing

#### Data Cleaning
- JS Code Node
- Removes unwanted HTML

#### AI Processing
- OpenAI (Content generation)
- Gemini (categorization, enrichment)

---

### 4. Validation

- IF Nodes:
  - Content validation
  - Metadata validation
  - Category validation

---

### 5. Enrichment

- Title/Slug Generator
- Keyword Generator
- Category Analyzer
- Internal Linking Engine

---

### 6. Publishing

- WordPress Node
- HTTP API for:
  - Tags
  - Metadata update

---

### 7. Utility Components

- SplitOut (keyword splitting)
- Loop (tag creation)
- Merge (data aggregation)
- Code Node (custom logic)

---

## 🧠 Component Design

- Loosely coupled
- Reusable nodes
- API-driven interactions