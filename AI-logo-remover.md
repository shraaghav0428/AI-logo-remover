# 🧠 Claude Project: PDF Logo Replacer App

## 📌 Project Overview
Build a web application that allows users to upload PDF files, automatically detect and remove existing logos and specific text (e.g., "property of XYZ"), and replace them with a user-uploaded logo in the exact same positions across all pages.

---

## 🎯 Core Objective
Enable seamless batch processing of PDFs where:
- Existing logos and ownership text are removed
- A new user-defined logo is inserted in the same positions
- The final processed PDFs are downloadable

---

## ⚙️ Functional Requirements

### 📂 File Upload Rules
- Users can upload:
  - Minimum: 1 file
  - Maximum: 3 files
- File type: **PDF only**
- File size constraints:
  - Max per file: **10 MB**
  - Max total upload: **30 MB**

---

### 🖼️ Logo Upload Rules
- Only **1 logo** can be uploaded at a time
- Allowed formats:
  - PNG
  - JPG
  - JPEG
- Logo should be stored temporarily and applied to all uploaded PDFs
- User can replace/change logo before processing

---

### 🔍 PDF Processing Logic

#### Step 1: Parse PDF
- Iterate through **each page** of the uploaded PDF
- Extract:
  - Images (potential logos)
  - Text content

#### Step 2: Identify Removable Elements
- Detect:
  - Logos (via image detection / heuristics / bounding boxes)
  - Text patterns like:
    - "property of XYZ"
    - "owned by"
    - watermark-like text
- Use:
  - OCR (if needed)
  - Pattern matching (regex for text)
  - Image similarity / positioning heuristics

#### Step 3: Remove Existing Elements
- Remove detected:
  - Logos (images)
  - Ownership text
- Maintain layout integrity

#### Step 4: Insert New Logo
- Place uploaded logo:
  - At **exact same coordinates** where original logos were found
  - Maintain:
    - Size ratio
    - Alignment
- If multiple logos exist → replace all instances

---

### 📦 Output Handling
- After processing:
  - If **1 file** → direct download as PDF
  - If **2–3 files** → bundle into **ZIP file**
- Show **Download CTA only after processing is complete**

---

### 🔁 Session Flow
- After download:
  - Reset state
  - Allow fresh uploads
  - Logo can be reused or changed

---

## 🧱 Suggested Tech Stack

### Frontend
- React (with TypeScript)
- MUI (Material UI)
- Responsive design (mobile-first)

### Backend
- Node.js (Express / Fastify)
- PDF Processing Libraries:
  - pdf-lib
  - pdfjs
  - sharp (image processing)
- OCR (if needed):
  - Tesseract.js

---

## 🧠 Key Challenges & Considerations
- Accurate logo detection (varied formats, placements)
- Handling scanned PDFs vs digital PDFs
- Maintaining layout integrity after removal
- Performance with large PDFs (optimize processing time)
- Edge cases:
  - No logo found
  - Multiple different logos
  - Overlapping text/images

---

## 🎨 UI/UX Requirements

### Design Principles
- Clean, minimal, white background UI
- Strong, clear CTA buttons
- Simple 3-step flow:
  1. Upload PDFs
  2. Upload Logo
  3. Process & Download

### Key Components
- File upload drag & drop
- Logo upload preview
- File list with size indicators
- Progress/loading state
- Download button (appears post-processing)

### Responsiveness
- Fully mobile responsive
- Touch-friendly interactions

---

## 🔐 Validation Rules

- Prevent upload if:
  - File type is not PDF
  - File size exceeds limits
  - More than 3 files uploaded
- Prevent processing if:
  - No logo uploaded
- Show clear error messages

---

## 🚀 Future Enhancements (Optional)
- Manual adjustment of logo placement
- Preview before download
- Bulk processing (more than 3 files)
- Save logo templates
- AI-based smarter logo detection

---

## ✅ Success Criteria
- Accurate detection and replacement of logos
- Seamless multi-file processing
- Fast processing time (<10–15 seconds per file ideally)
- Clean, intuitive user experience

---

## 🧩 Claude Instructions

When generating code or suggestions:
- Prioritize clean architecture
- Focus on modular components
- Optimize for performance and scalability
- Keep UI simple and production-ready
- Suggest libraries where needed
- Avoid overengineering — keep MVP lean
