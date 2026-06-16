# NTL Culture Day 2026 - GitHub Pages Version

ชุดนี้เป็นเวอร์ชันสำหรับ GitHub Pages โดยตัด Netlify Functions ออกแล้ว

## ใช้ไฟล์อะไรบ้าง

- `index.html` = หน้า Register
- `checkin.html` = หน้า Check-in
- `dashboard.html` = ปิดใช้งาน Dashboard แล้ว ให้ดู Summary ใน Google Sheet แทน
- `.nojekyll` = กัน GitHub Pages ประมวลผลผ่าน Jekyll

## ไม่ต้องใช้แล้ว

ลบไฟล์/โฟลเดอร์เหล่านี้ออกจาก repo ได้เลย

- `netlify.toml`
- `netlify/functions/register.js`
- `netlify/functions/checkin.js`
- `netlify/functions/dashboard.js`

## Backend URL

ไฟล์ HTML เรียก Apps Script Web App ตรงที่ URL นี้:

https://script.google.com/macros/s/AKfycbzKrf43i_0owWSfNZqns-STAkTf7QHa25-CtgrShLAHex8RPaU95xxHQwhCWSSi21QuaQ/exec

ถ้า Apps Script มีการสร้าง Deployment ใหม่และ URL เปลี่ยน ให้แก้ค่า `APPS_SCRIPT_URL` ใน `index.html` และ `checkin.html`

## Apps Script

ใน Code.gs ต้องยังรองรับ action:

- `register`
- `checkin`

และควร Deploy แบบ:

- Execute as: Me
- Who has access: Anyone

## GitHub Pages

1. สร้าง repository
2. อัปโหลดไฟล์ในโฟลเดอร์นี้ขึ้น repo
3. ไปที่ Settings > Pages
4. Source: Deploy from a branch
5. Branch: main / root
6. เปิด URL GitHub Pages ที่ได้

ตัวอย่าง URL:

- `https://<username>.github.io/<repo>/index.html`
- `https://<username>.github.io/<repo>/checkin.html`

## หมายเหตุ

ถ้าเปิดบน GitHub Pages แล้วขึ้น error ประมาณ `Failed to fetch` หรือ CORS ให้ใช้ทางเลือกใดทางเลือกหนึ่ง:

1. ย้ายหน้าเว็บไปไว้ใน Apps Script Web App โดยตรง
2. ใช้ Cloudflare Worker เป็น proxy แทน Netlify Function
3. กลับไปใช้ hosting ที่มี serverless proxy

