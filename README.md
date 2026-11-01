# YOLO Assignment : Rectangle & Polygon

เทรน YOLO 2 แบบ ทายวัตถุ 4 คลาส : **Dog, Person, Cat, Bunny**

| แบบ | โมเดล | val mAP50 | val mAP50-95 |
|---|---|---|---|
| Rectangle (กรอบ) | YOLO11n | 0.735 | 0.366 |
| Polygon (mask) | YOLO11n-seg | 0.775 | 0.588 |

## โครงสร้าง
```
assignment/
├── yolo_assignment.ipynb   เตรียมข้อมูล → เทรน → ผลการเทรน → test → predict → export
├── yolo_app.ipynb          โปรแกรม tkinter เลือกรูปแล้วทาย
└── runs/
    ├── rectangle/          ผลการเทรน + weights/best.pt
    ├── polygon/            ผลการเทรน + weights/best.pt
    ├── rectangle_test/     ผลบน test set
    ├── polygon_test/       ผลบน test set
    ├── predict_rectangle/  ผล predict
    └── predict_polygon/    ผล predict
web/                        เว็บแอปทายภาพด้วย Polygon model (onnxruntime-web, client-side)
```

## ลิงก์
- Web app : _(ใส่ลิงก์ Vercel)_
- Dataset : _(ใส่ลิงก์ OneDrive / Google Drive)_
- วิดีโอ : _(ใส่ลิงก์)_
