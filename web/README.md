# Web app ทายภาพ (YOLO Polygon)

รันโมเดลบนเบราว์เซอร์ของผู้ใช้ (client-side) ด้วย onnxruntime-web ไม่ต้องมี server ประมวลผล

```
web/
├── index.html      หน้าเว็บ
├── style.css       ตกแต่ง
├── app.js          โค้ดโหลดโมเดล + ทายภาพ
└── model/
    └── best.onnx   ได้จาก assignment/step7_export_onnx.py
```

## ลองในเครื่อง
ต้องเปิดผ่าน server (ดับเบิลคลิก index.html ตรงๆ จะโหลดโมเดลไม่ได้)
```
cd web
python -m http.server 8000
```
แล้วเปิด http://localhost:8000

## ขึ้นเว็บจริง
### GitHub + Vercel (แนะนำ)
1. สร้าง repo ใหม่บน GitHub แล้วอัปทั้งโฟลเดอร์ `web` (รวม `model/best.onnx` ~11 MB ไม่เกินลิมิต 100 MB ของ GitHub)
2. เข้า vercel.com → Add New Project → Import repo นั้น
3. Framework Preset = **Other**, Root Directory = โฟลเดอร์ `web` (ถ้า repo มีแค่ไฟล์เว็บก็ปล่อยว่าง) → Deploy
4. ได้ลิงก์ `https://ชื่อโปรเจกต์.vercel.app`

GitHub Pages ก็ได้: Settings → Pages → Deploy from branch → main

### Supabase
ใช้ Supabase Storage เก็บไฟล์โมเดลได้ (bucket แบบ Public)
1. Storage → New bucket → ติ๊ก Public → อัป `best.onnx`
2. คัดลอก Public URL แล้วแก้บรรทัดแรกๆ ใน `app.js`
   ```js
   const MODEL_URL = "https://xxxx.supabase.co/storage/v1/object/public/ชื่อbucket/best.onnx";
   ```
หมายเหตุ: Supabase Storage ไม่เหมาะกับการเปิดหน้า `index.html` โดยตรง (อาจแสดงเป็นข้อความโค้ด) จึงควรให้หน้าเว็บอยู่บน Vercel/GitHub Pages แล้วโหลดโมเดลจาก Supabase
