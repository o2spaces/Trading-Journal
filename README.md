# 📊 Pro Trading Dashboard — คู่มือติดตั้ง

## ไฟล์ที่ได้รับ
- `trading-dashboard.html` — แอพหลัก (เปิดในเบราว์เซอร์ได้เลย)
- `google-apps-script.gs` — Backend สำหรับ Google Sheets

---

## ขั้นตอนเชื่อมต่อ Google Sheets

### 1. สร้าง Google Sheet ใหม่
- ไปที่ [sheets.google.com](https://sheets.google.com)
- สร้าง Spreadsheet ใหม่ ตั้งชื่อว่า **"Trade Journal"**

### 2. เปิด Apps Script
- ใน Google Sheet → คลิก **Extensions** → **Apps Script**
- ลบโค้ดเดิมทิ้งหมด

### 3. วาง Script
- เปิดไฟล์ `google-apps-script.gs`
- คัดลอกโค้ดทั้งหมด → วางใน Apps Script Editor
- กด **Save** (Ctrl+S)

### 4. Deploy เป็น Web App
1. กด **Deploy** → **New Deployment**
2. คลิกไอคอน ⚙️ → เลือก **Web App**
3. ตั้งค่า:
   - **Description:** Trading Dashboard API
   - **Execute as:** Me
   - **Who has access:** Anyone
4. กด **Deploy**
5. อนุญาต Permission ที่ขอ
6. **Copy URL** ที่ได้ (จะขึ้นต้นด้วย `https://script.google.com/macros/s/...`)

### 5. เชื่อมต่อกับ Dashboard
1. เปิด `trading-dashboard.html` ในเบราว์เซอร์
2. กดปุ่ม **"+ Add Data / Settings"**
3. คลิก **Account Settings**
4. วาง URL ที่ copy มาในช่อง **Google Apps Script Web App URL**
5. ใส่ **Initial Balance** (ยอดเงินเริ่มต้น เช่น 10000)
6. กด **Save Settings & Reload Data**

---

## วิธีใช้งาน

### บันทึกการเทรด
1. กดปุ่ม **"+ Add Data / Settings"**
2. กรอกข้อมูล:
   - **Entry/Exit Time** — เวลาเปิด/ปิดเทรด
   - **Asset** — คู่เงิน/สินทรัพย์
   - **Direction** — Buy หรือ Sell
   - **Result** — TP / SL / BE / Open
   - **System** — ระบบเทรดที่ใช้
   - **Risk Amount** — จำนวนเงินที่เสี่ยง
   - **Reward Ratio** — อัตราส่วน Risk:Reward
   - Net PnL จะคำนวณอัตโนมัติ ✨
3. กด **Save Trade**

### ดู Dashboard
- **Current Balance** — ยอดเงินปัจจุบัน
- **Net PnL** — กำไร/ขาดทุนสุทธิ
- **Win Rate** — อัตราชนะ
- **Max Drawdown** — Drawdown สูงสุด
- **Profit Factor** — Gross Profit ÷ Gross Loss
- **Expectancy** — ผลตอบแทนเฉลี่ยต่อเทรด
- **Equity Curve** — กราฟ Balance ตามเวลา
- **Monthly PnL** — กำไร/ขาดทุนรายเดือน
- **Win Rate by** Asset / System / Session / Setup

---

## Demo Mode
ถ้ายังไม่เชื่อมต่อ Google Sheets แอพจะแสดงข้อมูลตัวอย่าง 50 เทรด
พร้อมใช้งานได้ทันที — เทรดที่บันทึกจะอยู่ในหน่วยความจำชั่วคราว

---

## หมายเหตุ
- ข้อมูลใน Google Sheets จะถูกจัดรูปแบบอัตโนมัติ (สีเขียว/แดง)
- แอพรองรับทั้ง Desktop และ Mobile
- ไม่ต้องมี Server — ทำงานได้บน Browser โดยตรง
