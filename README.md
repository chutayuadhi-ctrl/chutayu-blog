# chutayu-blog

> **ไฟล์นี้คืออะไร:** บล็อกส่วนตัวของ Chutayu Adhittayawong (First) — เว็บไซต์ Jekyll ที่ deploy ผ่าน GitHub Pages
> **เปิดอ่านเมื่อ:** จะเพิ่มโพสต์ใหม่ / แก้ธีม / debug การ build
> **แก้ไฟล์นี้:** แก้ตรงนี้ได้เลยเมื่อโครงสร้าง repo เปลี่ยน (เช่น เปลี่ยนธีม, ย้ายโฟลเดอร์)

เว็บไซต์จริง: https://chutayuadhi-ctrl.github.io/chutayu-blog/

ย้ายมาจาก Medium ([@24savagez](https://24savagez.medium.com)) เมื่อ 2026-09-11 — บทความเก่าย้ายมาครบพร้อมรูปประกอบต้นฉบับ ต้นทางเก็บสำรองไว้ที่ `03 - Research/Personal-Medium-Archive/` ในโปรเจกต์ ADA (ห้ามแก้ที่นั่น — เป็นสำเนาสำรอง)

## โครงสร้าง

```
_config.yml       ตั้งค่าเว็บไซต์ (ธีม minima, permalink, ฯลฯ)
_posts/            โพสต์ทั้งหมด — ไฟล์ .md ตามฟอร์แมต Jekyll YYYY-MM-DD-slug.md
assets/images/<slug>/   รูปประกอบของแต่ละโพสต์ (แยกโฟลเดอร์ตาม slug ของโพสต์นั้น)
index.md           หน้าแรก (แสดงรายการโพสต์อัตโนมัติผ่าน layout: home)
about.md           หน้า About
```

## วิธีเพิ่มโพสต์ใหม่ (สำหรับ agent/คนที่เขียนต่อ)

1. สร้างไฟล์ใหม่ใน `_posts/` ชื่อ `YYYY-MM-DD-slug-ภาษาอังกฤษ.md` (วันที่ในชื่อไฟล์ต้อง**ตรงกับ** `date:` ใน front matter — Jekyll ใช้ทั้งคู่กำหนด URL)
2. ใส่ front matter ขั้นต่ำ:
   ```yaml
   ---
   layout: post
   title: "ชื่อโพสต์"
   subtitle: "คำโปรยรอง (ถ้ามี — ลบบรรทัดนี้ทิ้งได้ถ้าไม่ใช้)"
   date: YYYY-MM-DD HH:MM:SS +0700
   author: Chutayu Adhittayawong
   ---
   ```
3. เขียนเนื้อหาเป็น Markdown ปกติต่อจาก front matter (`##` สำหรับหัวข้อย่อย)
4. ถ้ามีรูป: วางไฟล์รูปไว้ที่ `assets/images/<slug>/` แล้วอ้างอิงในเนื้อหาด้วย
   `![คำอธิบายรูป](/chutayu-blog/assets/images/<slug>/ชื่อไฟล์.png)`
   (ต้องขึ้นต้นด้วย `/chutayu-blog/` เพราะเว็บอยู่ใต้ path ย่อย — ดู `baseurl` ใน `_config.yml`)
5. Commit + push ขึ้น `main` — GitHub Pages build ให้อัตโนมัติ (ไม่ต้องรัน build เอง) รอ 1-2 นาทีแล้วเช็คที่เว็บจริง

## ทดสอบ local (ถ้ามี Ruby/Bundler)

```bash
bundle install
bundle exec jekyll serve
# เปิด http://localhost:4000/chutayu-blog/
```

ถ้าเครื่องไม่มี Ruby/Jekyll พร้อม ข้ามขั้นตอนนี้ได้ — push แล้วเช็คผลบน GitHub Pages จริงแทน (Settings → Pages จะบอกสถานะ build)

## Push / Deploy

Repo นี้ private key/token อยู่นอก repo เสมอ (ไม่มี credential ใดๆ อยู่ใน git history) — ใครจะ push ต้องมี access เป็นของตัวเอง (fine-grained PAT scope เฉพาะ repo นี้ หรือ SSH key ของบัญชี GitHub เจ้าของ)
