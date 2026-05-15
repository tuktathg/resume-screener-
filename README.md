# Resume Screener — AI-Powered

คัดกรอง Resume PDF อัตโนมัติด้วย Claude claude-sonnet-4-20250514

## Features
- อัปโหลด PDF หลายไฟล์พร้อมกัน (drag & drop)
- กำหนดเกณฑ์ด้วย Job Description + Required Keywords
- AI วิเคราะห์และให้คะแนน 0–100
- ดาวน์โหลด Resume ที่ผ่านเกณฑ์เป็น ZIP
- Export ผลลัพธ์เป็น CSV
- Static deploy — ไม่ต้องมี backend server

## Tech Stack
- Vanilla HTML/CSS/JS (ไม่มี framework)
- [PDF.js](https://mozilla.github.io/pdf.js/) — extract text จาก PDF
- [JSZip](https://stuk.github.io/jszip/) — pack ZIP download
- Anthropic Claude API — วิเคราะห์ resume

---

## Deploy บน Vercel (5 นาที)

### Option A: Vercel CLI (แนะนำ)
```bash
# 1. ติดตั้ง Vercel CLI
npm i -g vercel

# 2. เข้าโฟลเดอร์นี้
cd resume-screener

# 3. Deploy
vercel

# ตอบคำถาม:
# Set up and deploy? → Y
# Which scope? → เลือก account ของคุณ
# Link to existing project? → N
# Project name? → resume-screener (หรือชื่ออื่น)
# In which directory is your code located? → ./
# Want to override the settings? → N
```

### Option B: GitHub + Vercel Auto-Deploy
```bash
# 1. สร้าง repo ใหม่บน GitHub แล้วรัน:
git init
git add .
git commit -m "feat: initial resume screener"
git remote add origin https://github.com/YOUR_USERNAME/resume-screener.git
git push -u origin main

# 2. ไปที่ vercel.com → New Project → Import GitHub repo
# 3. เลือก repo → Deploy (ไม่ต้องตั้ง env vars อะไรทั้งนั้น)
```

---

## การใช้งาน

1. เปิด URL ที่ได้จาก Vercel
2. กรอก **Anthropic API Key** (ขึ้นต้นด้วย `sk-ant-`)
3. ตั้ง **Pass Score Threshold** (default 70%)
4. วาง **Job Description** ในช่องที่กำหนด
5. เพิ่ม **Keywords/Conditions** ที่ต้องการ (เช่น "Python", "5+ years", "MBA")
6. ลาก PDF หรือคลิกเลือกไฟล์
7. กด **เริ่มคัดกรอง Resume**
8. ดาวน์โหลด ZIP หรือ Export CSV

---

## ข้อจำกัดที่ต้องรู้

| รายการ | รายละเอียด |
|---|---|
| API Key | อยู่ใน browser — เห็นได้ใน DevTools ตามที่ตกลงกัน |
| PDF scanned | อ่านไม่ได้ — ต้องเป็น text-based PDF เท่านั้น |
| Persistent storage | ไม่มี — ปิด tab ข้อมูลหาย |
| Cost | ~$0.003–0.01 ต่อ resume (ขึ้นอยู่กับความยาว) |

---

## โครงสร้างไฟล์

```
resume-screener/
├── index.html      ← แอปทั้งหมดอยู่ที่นี่
├── vercel.json     ← Vercel deploy config
└── README.md       ← ไฟล์นี้
```
