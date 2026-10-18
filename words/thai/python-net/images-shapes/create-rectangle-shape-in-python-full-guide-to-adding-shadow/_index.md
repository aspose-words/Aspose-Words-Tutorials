---
category: general
date: 2026-05-04
description: เรียนรู้วิธีสร้างรูปสี่เหลี่ยม วิธีเพิ่มรูปที่มีเงา การเปลี่ยนสีเงา ตั้งค่าระยะเงา
  และบันทึกเอกสารเป็น PDF โดยใช้ Aspose.Words สำหรับ Python.
draft: false
keywords:
- create rectangle shape
- how to add shape
- change shadow color
- save document as pdf
- set shadow distance
language: th
og_description: สร้างรูปสี่เหลี่ยมผืนผ้าด้วย Aspose.Words สำหรับ Python เรียนรู้วิธีเพิ่มรูปทรง
  เปลี่ยนสีเงา ตั้งระยะห่างของเงา และบันทึกเอกสารเป็น PDF.
og_title: สร้างรูปสี่เหลี่ยม – เพิ่มเงา, เปลี่ยนสี & บันทึกเป็น PDF
tags:
- Aspose.Words
- Python
- PDF generation
title: สร้างรูปสี่เหลี่ยมใน Python – คู่มือเต็มเรื่องการเพิ่มเงาและบันทึกเป็น PDF
url: /th/python/images-shapes/create-rectangle-shape-in-python-full-guide-to-adding-shadow/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# สร้างรูปสี่เหลี่ยม – คำแนะนำฉบับเต็มสำหรับนักพัฒนา Python

เคยต้อง **สร้างรูปสี่เหลี่ยม** ในเอกสาร Word แล้วสงสัยว่าจะเพิ่มเงาที่ดูเป็นมืออาชีพได้อย่างไรหรือไม่? บางทีคุณอาจกำลังสร้างตัวสร้างรายงานและความสวยงามของภาพมีความสำคัญ—โดยเฉพาะเมื่อผลลัพธ์สุดท้ายเป็น PDF ข่าวดีคือ ด้วย Aspose.Words for Python คุณไม่เพียงแต่ **วิธีเพิ่มรูป** แต่ยังสามารถปรับคุณสมบัติของเงาทั้งหมด ตั้งแต่สีจนถึงระยะห่าง แล้ว **บันทึกเอกสารเป็น pdf** ในขั้นตอนเดียวอย่างราบรื่น

ในคู่มือนี้เราจะเดินผ่านกระบวนการทั้งหมดแบบทีละขั้นตอน คุณจะได้เห็นโค้ดที่สามารถคัดลอก‑วางได้ตรง ๆ เข้าใจ *ทำไม* แต่ละบรรทัดจึงสำคัญ และรับเคล็ดลับสำหรับจัดการกรณีขอบ (เช่นเงาโปร่งใสหรือ DPI ที่ไม่เป็นมาตรฐาน) เมื่อจบคุณจะสามารถ **สร้างรูปสี่เหลี่ยม**, ปรับแต่งเงา, และส่งออก PDF ที่คมชัดโดยไม่ต้องเสียแรง

## ข้อกำหนดเบื้องต้น

- Python 3.8+ ติดตั้งบนเครื่องของคุณ  
- Aspose.Words for Python ผ่าน `pip install aspose-words`  
- ความคุ้นเคยพื้นฐานกับ Python แบบเชิงวัตถุ (ไม่มีอะไรซับซ้อน)

หากคุณมี virtual environment ตั้งไว้แล้ว เพียงรันคำสั่งติดตั้งและพร้อมใช้งาน

## ขั้นตอนที่ 1: เริ่มต้น Document และ Builder

ก่อนที่คุณจะ **วิธีเพิ่มรูป** คุณต้องมีเอกสารเปล่าที่จะทำงาน `Document` คลาสแทนไฟล์ทั้งหมด และ `DocumentBuilder` คือแปรงวาดของคุณ

```python
import aspose.words as aw

# Step 1: Create a new document and a DocumentBuilder to edit it
document = aw.Document()
builder = aw.DocumentBuilder(document)
```

*ทำไมสิ่งนี้สำคัญ:* `Document` เก็บส่วน, หน้า, และทรัพยากรทั้งหมด `DocumentBuilder` ให้ API ที่ไหลลื่นเพื่อแทรกเนื้อหาได้ตรงตำแหน่งที่ต้องการ—คิดว่าเป็นเคอร์เซอร์ในโปรเซสเซอร์คำ

## ขั้นตอนที่ 2: แทรกรูปสี่เหลี่ยม

ตอนนี้เราจะ **วิธีเพิ่มรูป** จริง ๆ วิธี `insert_shape` ต้องการประเภทรูปและขนาด (หน่วยเป็น points) ที่นี่เราเลือกสี่เหลี่ยม 200 × 100 pt และเติมสีฟ้าอ่อน

```python
# Step 2: Insert a rectangle shape and give it a light‑blue fill
rectangle_shape = builder.insert_shape(
    aw.drawing.ShapeType.RECTANGLE,  # shape type
    200,                            # width in points
    100)                            # height in points
rectangle_shape.fill_color = aw.Color.light_blue
```

*เคล็ดลับ:* หากต้องการให้รูปจัดตำแหน่งกับข้อความที่มีอยู่ ใช้ `builder.move_to` ก่อนแทรก หรือปรับคุณสมบัติ `left`/`top` หลังสร้าง

## ขั้นตอนที่ 3: เปิดใช้งานเงา

รูปที่ไม่มีเงาดูแบนราบ เพื่อ **ตั้งระยะห่างของเงา** และทำให้เอฟเฟกต์มองเห็นได้ ให้ดึง `shadow format` แล้วเปิดใช้งาน

```python
# Step 3: Access the shape's shadow format and make the shadow visible
rectangle_shadow = rectangle_shape.shadow_format
rectangle_shadow.visible = True
```

*ทำไมต้องทำขั้นตอนนี้:* `ShadowFormat` เป็นอ็อบเจ็กต์แยก; การสลับ `visible` เป็นสิ่งแรกที่ต้องทำ มิฉะนั้นคุณสมบัติเพิ่มเติมของเงาจะถูกละเลย

## ขั้นตอนที่ 4: ปรับสไตล์เงา – สี, เบลอ, ระยะ, ทิศทาง

นี่คือจุดที่เวทมนต์เกิดขึ้น เราจะ **เปลี่ยนสีเงา**, ปรับรัศมีเบลอ, ตั้งระยะห่างของเงาจากสี่เหลี่ยม, และหมุน 45°

```python
# Step 4: Configure the appearance of the shadow
rectangle_shadow.style = aw.drawing.ShadowStyle.OUTER   # outer shadow
rectangle_shadow.blur_radius = 10.0                    # blur amount (pixels)
rectangle_shadow.distance = 5.0                        # distance from the shape
rectangle_shadow.direction = 45.0                     # angle in degrees
rectangle_shadow.color = aw.Color.gray                 # shadow colour
```

*คำอธิบายของแต่ละคุณสมบัติ:*

| Property | สิ่งที่ทำ | ค่าโดยทั่วไป |
|----------|----------|--------------|
| `style` | กำหนดว่าเงาเป็น *inner* หรือ *outer* | `OUTER` (ใช้บ่อยที่สุด) |
| `blur_radius` | ควบคุมความนุ่ม; ค่ามาก = ขอบฟุ้ง | 0–20 px เป็นค่าปกติ |
| `distance` | ระยะที่เงาถูกย้ายจากรูป | 0–10 pt สำหรับเงาเบา, >10 สำหรับเงาเด่น |
| `direction` | มุมของแหล่งแสง, วัดตามเข็มนาฬิกาจากแกน x | 0‑360° |
| `color` | สีของเงา | ใด ๆ `aw.Color` (เช่น `gray`, `dark_red`) |

*กรณีขอบ:* หากตั้ง `distance` เป็น `0` เงาจะอยู่ใต้รูปโดยตรง ทำให้สีเติมของรูปถูกซ่อน ควรตั้งค่าให้มากกว่า `0` เพื่อให้เห็นการย้ายตำแหน่ง

## ขั้นตอนที่ 5: บันทึกเอกสารเป็น PDF

สุดท้าย เรา **บันทึกเอกสารเป็น pdf** Aspose.Words จะทำการแรสเตอร์ไลซ์เงาโดยอัตโนมัติ ทำให้ PDF มีลักษณะเหมือนมุมมองใน Word

```python
# Step 5: Save the document as a PDF with the shadowed shape
output_path = "YOUR_DIRECTORY/ShadowedShape.pdf"
document.save(output_path)
print(f"PDF saved to {output_path}")
```

*ทำไมต้องเป็น PDF?* PDF รักษาเลย์เอาต์ข้ามแพลตฟอร์ม ทำให้เหมาะกับรายงาน, ใบแจ้งหนี้, หรือเอกสารที่ต้องพิมพ์

---

![สร้างรูปสี่เหลี่ยมพร้อมเงา](https://example.com/images/rectangle-shadow.png){: .align-center alt="ตัวอย่างการสร้างรูปสี่เหลี่ยมพร้อมเงา"}

*ภาพด้านบนแสดงผลลัพธ์ PDF สุดท้าย – สี่เหลี่ยมสีฟ้าอ่อนพร้อมเงาเทาอ่อนด้านนอก ตามที่เราตั้งค่าไว้*

## คำถามที่พบบ่อย & รูปแบบต่าง ๆ

### ถ้าต้องการเงา **โปร่งใส** จะทำอย่างไร?

ตั้งค่าแชนแนลอัลฟาในสีเงา:

```python
transparent_gray = aw.Color.from_argb(128, 0, 0, 0)  # 50% opacity black
rectangle_shadow.color = transparent_gray
```

### สามารถใช้เงาเดียวกันกับหลายรูปได้หรือไม่?

ได้. ดึง `ShadowFormat` จากรูปหนึ่งแล้วกำหนดให้รูปอื่น:

```python
another_shape = builder.insert_shape(aw.drawing.ShapeType.ELLIPSE, 150, 150)
another_shape.shadow_format = rectangle_shadow.clone()
```

### จะเปลี่ยนเงาสำหรับ **รูปแบบอื่น** ได้อย่างไร?

รูปทุกประเภทใช้คุณสมบัติ `ShadowFormat` เดียวกัน จึงสามารถใช้บล็อกการตั้งค่าเดียวกัน—เพียงเปลี่ยน `ShapeType.RECTANGLE` เป็น `ShapeType.OVAL`, `ShapeType.TRIANGLE` เป็นต้น

### แล้ว **PDF ความละเอียดสูง** สำหรับการพิมพ์ล่ะ?

ระบุ `PdfSaveOptions` พร้อม DPI ที่สูงกว่า:

```python
options = aw.saving.PdfSaveOptions()
options.image_resolution = 300  # 300 DPI for print quality
document.save(output_path, options)
```

## สรุป

เราได้ครอบคลุมทุกอย่างที่คุณต้องการเพื่อ **สร้างรูปสี่เหลี่ยม**, **วิธีเพิ่มรูป**, ปรับ **สีเงา**, **ตั้งระยะห่างของเงา**, และสุดท้าย **บันทึกเอกสารเป็น pdf** สคริปต์ที่สมบูรณ์และพร้อมรันมีดังนี้:

```python
import aspose.words as aw

# Initialise document
document = aw.Document()
builder = aw.DocumentBuilder(document)

# Insert rectangle shape
rectangle_shape = builder.insert_shape(
    aw.drawing.ShapeType.RECTANGLE, 200, 100)
rectangle_shape.fill_color = aw.Color.light_blue

# Enable and style shadow
rectangle_shadow = rectangle_shape.shadow_format
rectangle_shadow.visible = True
rectangle_shadow.style = aw.drawing.ShadowStyle.OUTER
rectangle_shadow.blur_radius = 10.0
rectangle_shadow.distance = 5.0
rectangle_shadow.direction = 45.0
rectangle_shadow.color = aw.Color.gray

# Save as PDF
output_path = "YOUR_DIRECTORY/ShadowedShape.pdf"
document.save(output_path)
print(f"PDF saved to {output_path}")
```

รันสคริปต์, เปิดไฟล์ `ShadowedShape.pdf` ที่ได้, คุณจะเห็นสี่เหลี่ยมคมชัดพร้อมเงาเทาอ่อน—ตรงกับที่คาดหวังจากรายงานที่จัดรูปแบบอย่างมืออาชีพ

## ขั้นตอนต่อไปคืออะไร?

- **สำรวจรูปแบบอื่น** (`ShapeType.OVAL`, `ShapeType.LINE`) เพื่อเพิ่มความหลากให้เอกสารของคุณ  
- **รวมเงาหลายชั้น** โดยการวางซ้อนรูป; คุณสามารถสร้างเอฟเฟกต์ “glow” ด้วยการใช้ inner shadow สีสว่าง  
- **ทำงานอัตโนมัติเป็นชุด**: วนลูปข้อมูลหลายแถว, สร้างรูปต่อแถว, แล้วรวมทั้งหมดเป็น PDF เดียว  
- **เชื่อมต่อกับไลบรารี Aspose อื่น** (เช่น Aspose.Slides) หากต้องการส่งออกภาพเดียวกันไปยัง PowerPoint

ลองทดลองเปลี่ยน `blur_radius`, เล่นกับ `direction`, หรือสลับ `gray` เป็นสีที่สอดคล้องกับแบรนด์ของคุณ API มีความยืดหยุ่นพอที่การปรับเล็กน้อยจะเปลี่ยนผลลัพธ์อย่างมาก

มีคำถามหรือกรณีที่ท้าทาย? แสดงความคิดเห็นด้านล่างหรือเข้าร่วมฟอรั่มชุมชน Aspose. Happy coding, และสนุกกับสี่เหลี่ยมที่มีเงาสวยงาม!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}