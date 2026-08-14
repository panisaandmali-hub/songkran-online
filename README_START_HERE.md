# ซอร์สโค้ดเต็ม — สงกรานต์ออนไลน์

ชุดนี้เป็นโค้ดเวอร์ชันล่าสุดของเว็บไซต์ **สงกรานต์ออนไลน์ สุขสันต์วันปีใหม่ไทย** โดยรวมหน้า React, CSS, API สำหรับคำอวยพร, MySQL/Drizzle schema, ชุดทดสอบ, ไฟล์ตั้งค่า และ HTML หน้าเดียวสำหรับนำไปใช้ต่อ

## เลือกวิธีใช้งาน

| สิ่งที่ต้องการ | ใช้ไฟล์หรือโฟลเดอร์ | ความสามารถ |
|---|---|---|
| ต้องการคัดลอกไปวางและเปิดหน้าเว็บอย่างรวดเร็ว | `songkran-online-standalone.html` | หน้าเว็บ, สวิตช์ TH/EN, modal, animation และรูปภาพทั้งหมด โดยไม่ต้องติดตั้ง Node.js |
| ต้องการแก้เว็บไซต์ด้วย React และเก็บคำอวยพรจริง | `songkran-online/` | React + Vite + Express + tRPC + MySQL/Drizzle ครบชุด |

> ไฟล์ HTML เดี่ยวเป็นเว็บไซต์แบบ static จึงไม่มีฐานข้อมูลสำหรับบันทึกคำอวยพรจริง ส่วนการส่งคำอวยพรจริงอยู่ในโฟลเดอร์ `songkran-online/`

## วิธีเร็วที่สุด: ใช้ HTML ไฟล์เดียว

เปิด `songkran-online-standalone.html` ในโปรแกรมแก้โค้ด แล้วคัดลอกทั้งหมดไปวางในไฟล์ `index.html` ของเว็บไซต์คุณ จากนั้นอัปโหลดขึ้นโฮสต์แบบ static เช่น GitHub Pages, Netlify หรือโฮสต์ที่ใช้อยู่

ไฟล์นี้ใช้ URL รูปภาพสาธารณะแล้ว จึงไม่ต้องคัดลอกรูปภาพแยกต่างหาก อย่างไรก็ตาม ฟอนต์ Chakra Petch และ Noto Sans Thai โหลดจาก Google Fonts จึงต้องเชื่อมต่ออินเทอร์เน็ตขณะเปิดหน้าเว็บครั้งแรก

## วิธีใช้โครงการ React ฉบับเต็ม

ต้องมี Node.js 22 ขึ้นไป, pnpm 10 และ MySQL ที่พร้อมใช้งาน ก่อนเริ่มให้เปิด Terminal ในโฟลเดอร์ `songkran-online/` แล้วรันคำสั่งต่อไปนี้

```bash
pnpm install
pnpm test
pnpm run dev
```

เมื่อต้องการสร้างไฟล์สำหรับนำขึ้นโฮสต์ ให้รัน:

```bash
pnpm build
pnpm start
```

## ตั้งค่าฐานข้อมูลสำหรับคำอวยพรจริง

ระบบส่งคำอวยพรใช้ MySQL และตาราง `songkranWishes` ตามไฟล์ `drizzle/schema.ts` ก่อนเริ่มใช้งานจริง ให้สร้างไฟล์ `.env` ในโฟลเดอร์ `songkran-online/` และกำหนดอย่างน้อยดังนี้

```env
DATABASE_URL=mysql://USERNAME:PASSWORD@HOST:3306/DATABASE_NAME
JWT_SECRET=เปลี่ยนเป็นข้อความสุ่มที่ยาวและเก็บเป็นความลับ
NODE_ENV=development
```

จากนั้นสร้างตารางด้วย migration ที่อยู่ในโฟลเดอร์ `drizzle/` ตามการตั้งค่า MySQL ของคุณ ห้ามนำไฟล์ `.env` หรือรหัสผ่านฐานข้อมูลขึ้น Git หรือส่งต่อให้ผู้อื่น

## ไฟล์สำคัญสำหรับการแก้เนื้อหา

| ไฟล์ | แก้สิ่งใด |
|---|---|
| `client/src/pages/Home.tsx` | ข้อความภาษาไทย/อังกฤษ, กิจกรรม, ประวัติ และกติกา 10 ข้อ |
| `client/src/index.css` | สี, เลย์เอาต์, responsive และ animation หลัก |
| `client/src/rule-illustrations.css` | สีหัวข้อและพื้นหลังของส่วนข้อปฏิบัติ |
| `songkran-online-standalone.html` | เว็บ HTML ไฟล์เดียวสำหรับคัดลอกใช้โดยไม่พึ่ง React |
| `server/routers.ts` และ `server/db.ts` | API อ่าน/ส่งคำอวยพร |
| `drizzle/schema.ts` | โครงสร้างตารางฐานข้อมูล |

รายละเอียดรายชื่อไฟล์ครบถ้วนอยู่ใน `songkran-online/SOURCE_MANIFEST.md`

## สิ่งที่ตั้งใจไม่รวมไว้ใน ZIP

ชุดซอร์สนี้ไม่รวม `node_modules/`, `dist/`, `.git/`, `.manus-logs/`, coverage, log และไฟล์ `.env*` เพราะติดตั้งใหม่ได้หรืออาจมีข้อมูลลับ เมื่อแตก ZIP ให้รัน `pnpm install` เพื่อดาวน์โหลด dependencies ใหม่
