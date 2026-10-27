---
category: general
date: 2026-09-30
description: เรียนรู้วิธีสร้างรูปร่างสี่เหลี่ยม, ใส่เงาให้รูปร่าง, และบันทึกไฟล์ Word
  พร้อมรูปร่างโดยใช้ Aspose.Words สำหรับ Python.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create rectangle shape
- how to add shape
- apply shadow to shape
- set shadow blur
- save word with shape
language: th
lastmod: 2026-09-30
og_description: สร้างรูปสี่เหลี่ยมในเอกสาร Word อย่างรวดเร็ว บทเรียนนี้แสดงวิธีเพิ่มรูป,
  ใส่เงาให้รูป, ตั้งค่าความเบลอของเงา, และบันทึกไฟล์ Word พร้อมรูป
og_image_alt: Screenshot of a Word document showing a rectangle shape with a soft
  shadow
og_title: สร้างรูปสี่เหลี่ยมใน Word ด้วย Python – คู่มือแบบขั้นตอนต่อขั้นตอน
schemas:
- author: Aspose
  dateModified: '2026-09-30'
  description: Learn how to create rectangle shape, apply shadow to shape, and save
    Word with shape using Aspose.Words for Python.
  headline: How to create rectangle shape in a Word document using Python
  type: TechArticle
tags:
- Aspose.Words
- Python
- Word automation
- Shapes
title: วิธีสร้างรูปสี่เหลี่ยมในเอกสาร Word ด้วย Python
url: /th/python/images-shapes/how-to-create-rectangle-shape-in-a-word-document-using-pytho/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# วิธีสร้างรูปสี่เหลี่ยมผืนผ้าในเอกสาร Word ด้วย Python

หากคุณต้องการ **สร้างรูปสี่เหลี่ยมผืนผ้า** ในไฟล์ Word คำแนะนำนี้จะแสดงวิธีแก้ปัญหาที่สมบูรณ์และสามารถรันได้ คุณจะได้เห็นวิธีเพิ่มรูป, ใช้เอฟเฟกต์เงา, ปรับค่าความเบลอ, และสุดท้าย **บันทึก Word พร้อมรูป** เพื่อให้ผลลัพธ์สามารถเปิดใน Microsoft Word หรือโปรแกรมดูที่เข้ากันได้ใด ๆ

ตัวอย่างใช้ **Aspose.Words for Python via .NET** ซึ่งเป็นไลบรารีที่ช่วยให้คุณจัดการเอกสาร Word โดยไม่ต้องติดตั้ง Microsoft Office ไม่จำเป็นต้องมีประสบการณ์กับ API มาก่อน—แค่ความรู้พื้นฐานของ Python ก็พอ

## สิ่งที่คุณจะได้ทำ

- แทรกรูปสี่เหลี่ยมลงในส่วนแรกของเอกสารใหม่  
- ตั้งค่าเงานุ่มโดยกำหนดค่าความเบลอ, ระยะชิด, และสี  
- บันทึกเอกสารลงดิสก์และตรวจสอบผลลัพธ์ที่เห็นได้

## ข้อกำหนดเบื้องต้น

- Python 3.8 หรือใหม่กว่า  
- ติดตั้งแพคเกจ `aspose-words` (`pip install aspose-words`)  
- มีสิทธิ์เขียนในไดเรกทอรีที่ใช้เก็บผลลัพธ์

## สร้างรูปสี่เหลี่ยมและกำหนดลักษณะการแสดงผล

ขั้นตอนแรกคือสร้างเอกสารเปล่าและเพิ่มรูปสี่เหลี่ยมลงไป รูปนี้จะทำหน้าที่เป็นผืนผ้าใบสำหรับเอฟเฟกต์เงา

```python
import aspose.words as aw
from aspose.words.drawing import ShadowEffect

# Step 1: Create a new blank document
doc = aw.Document()

# Step 2: Add a rectangle shape to the first section
shape = doc.get_first_section().body.append_child(
    aw.drawing.Shape(doc, aw.drawing.ShapeType.RECTANGLE)
)

# Optional: Define the shape’s size and position (in points)
shape.width = aw.ConvertUtil.inch_to_point(2)   # 2 inches wide
shape.height = aw.ConvertUtil.inch_to_point(1)  # 1 inch tall
shape.left = aw.ConvertUtil.inch_to_point(1)    # 1 inch from the left margin
shape.top = aw.ConvertUtil.inch_to_point(1)     # 1 inch from the top margin
```

**ทำไมจึงสำคัญ:**  
การสร้างรูปสี่เหลี่ยมให้คุณมีอ็อบเจกต์ที่เป็นรูป (`shape`) ที่สามารถปรับสไตล์ได้ต่อไป การกำหนดขนาดอย่างชัดเจนทำให้รูปแสดงผลเหมือนกันบนทุกแพลตฟอร์ม

## วิธีเพิ่มรูปลงในเอกสาร Word

แม้โค้ดข้างต้นจะเพิ่มรูปสี่เหลี่ยมแล้ว คุณอาจต้องการเพิ่มรูปอื่น ๆ (เช่น วงกลม, ลูกศร) ในภายหลัง รูปแบบเดียวกันใช้ได้: เรียก `append_child` บน `body` ของเอกสารและส่งค่า `ShapeType` ที่ต้องการ

```python
# Example: Adding a second shape – an ellipse
ellipse = doc.get_first_section().body.append_child(
    aw.drawing.Shape(doc, aw.drawing.ShapeType.ELLIPSE)
)
ellipse.width = aw.ConvertUtil.inch_to_point(1.5)
ellipse.height = aw.ConvertUtil.inch_to_point(1)
ellipse.left = aw.ConvertUtil.inch_to_point(3.5)
ellipse.top = aw.ConvertUtil.inch_to_point(1)
```

**เคล็ดลับ:** ใช้ enumeration `ShapeType` เพื่อสำรวจรูปแบบที่รองรับทั้งหมด วิธีนี้ทำให้โค้ดอ่านง่ายและหลีกเลี่ยงการใช้ตัวเลขลับ

## ใช้เงากับรูปและตั้งค่าความเบลอของเงา

เงาช่วยเพิ่มความลึกและความน่าสนใจ `ShadowEffect` class ให้คุณควบคุมความเบลอ, ระยะชิด, และสี ด้านล่างเราจะใส่เงาดำนุ่มลงบนรูปสี่เหลี่ยม

```python
# Step 3: Configure a shadow effect for the rectangle
shadow = ShadowEffect()
shadow.blur = 5.0          # Sets the softness of the shadow edge
shadow.offset_x = 2.0      # Horizontal displacement from the shape
shadow.offset_y = 2.0      # Vertical displacement from the shape
shadow.color = aw.Color.black

# Step 4: Apply the shadow effect to the shape
shape.shadow = shadow
```

**ทำไมต้องตั้งค่าความเบลอ?**  
`blur` กำหนดว่ามีการกระจายของเงาแค่ไหน ค่าเล็ก (เช่น 1.0) ให้ขอบคมชัด, ส่วนค่ามากกว่า (เช่น 5.0) จะทำให้เงาไล่สีอย่างนุ่มนวล ซึ่งมักดูสวยงามกว่า

**กรณีพิเศษ:** หากตั้ง `blur` เป็น 0 เงาจะกลายเป็นเงาดำเต็มรูปแบบ บางโปรแกรมอาจแสดงผลเป็นขอบหยัก ดังนั้นควรเลือกค่ามากกว่า 0 เพื่อให้ได้ผลลัพธ์ที่เรียบเนียน

## บันทึก Word พร้อมรูป

การบันทึกเอกสารทำให้การเปลี่ยนแปลงทั้งหมดเสร็จสมบูรณ์ เมธอด `save` จะเขียนไฟล์ `.docx` ที่โปรแกรมประมวลผล Word สมัยใหม่ใด ๆ ก็เปิดได้

```python
# Step 5: Save the document to see the result
output_path = "output.docx"   # Adjust the path as needed
doc.save(output_path)
print(f"Document saved to {output_path}")
```

เมื่อคุณเปิด `output.docx` จะเห็นรูปสี่เหลี่ยมที่วางห่างจากมุมบน‑ซ้ายหนึ่งนิ้ว พร้อมเงาดำนุ่มที่เลื่อนสองพอยต์ไปทางขวาและลงด้านล่าง ความเบลอของเงาทำให้รูปดูเหมือนลอยขึ้นจากหน้า

**เคล็ดลับระดับมืออาชีพ:** หากต้องสร้างเอกสารหลายไฟล์ในลูป ให้ใช้ `Document` ตัวเดียวกันและล้าง `body` ระหว่างรอบเพื่อประหยัดหน่วยความจำ

## ความแตกต่างทั่วไปและการแก้ไขปัญหา

| สถานการณ์ | สิ่งที่ต้องเปลี่ยน | เหตุผล |
|-----------|----------------|--------|
| สีเงาต่างกัน | `shadow.color = aw.Color.red` | ใช้สีแบรนด์หรือเน้นรูปที่สำคัญ |
| ระยะชิดเงาใหญ่ขึ้น | เพิ่มค่า `shadow.offset_x`/`offset_y` | เน้นความลึกสำหรับ mock‑up UI |
| ไม่ต้องการเงาเลย | ลบบรรทัด `shape.shadow = shadow` | เหมาะกับรายงานแบบมินิมัล |
| ส่งออกเป็น PDF แทน DOCX | `doc.save("output.pdf")` | PDF เหมาะสำหรับการแจกจ่ายแบบอ่าน‑อย่างเดียว |

หากรูปไม่ปรากฏ ตรวจสอบว่าคุณได้เพิ่มรูปลงในส่วนที่ถูกต้อง (`get_first_section()`) และบันทึกเอกสารหลังจากทำการแก้ไขแล้ว

## ตัวอย่างเต็มที่สามารถรันได้

```python
import aspose.words as aw
from aspose.words.drawing import ShadowEffect

# Create a new blank document
doc = aw.Document()

# Add a rectangle shape
shape = doc.get_first_section().body.append_child(
    aw.drawing.Shape(doc, aw.drawing.ShapeType.RECTANGLE)
)
shape.width = aw.ConvertUtil.inch_to_point(2)
shape.height = aw.ConvertUtil.inch_to_point(1)
shape.left = aw.ConvertUtil.inch_to_point(1)
shape.top = aw.ConvertUtil.inch_to_point(1)

# Configure and apply a shadow
shadow = ShadowEffect()
shadow.blur = 5.0
shadow.offset_x = 2.0
shadow.offset_y = 2.0
shadow.color = aw.Color.black
shape.shadow = shadow

# Save the document
output_path = "output.docx"
doc.save(output_path)
print(f"Document saved to {output_path}")
```

การรันสคริปต์จะสร้าง `output.docx` ที่มีรูปสี่เหลี่ยมพร้อมเงานุ่ม เปิดไฟล์ใน Microsoft Word เพื่อตรวจสอบว่าเอฟเฟกต์ตรงตามที่อธิบายไว้

## สรุป

ตอนนี้คุณรู้วิธี **สร้างรูปสี่เหลี่ยมผืนผ้า**, **เพิ่มรูป** ลงในเอกสาร Word, **ใช้เงากับรูป**, **ตั้งค่าความเบลอของเงา**, และสุดท้าย **บันทึก Word พร้อมรูป** ด้วย Aspose.Words for Python รูปแบบเดียวกันสามารถขยายไปยังรูปแบบอื่น ๆ, สี, และเอฟเฟกต์อื่น ๆ ให้คุณควบคุมกราฟิกในเอกสารได้เต็มที่โดยไม่ต้องพึ่งพาการอัตโนมัติของ Office

**ขั้นตอนต่อไป**

- ทดลองใช้ `Shape.fill` เพื่อเพิ่มพื้นหลังแบบไล่สีหรือรูปภาพ  
- ใช้วัตถุ `Paragraph` เพื่อวางข้อความภายในรูปสี่เหลี่ยม  
- รวมหลายรูปเพื่อสร้างไดอะแกรมซับซ้อน แล้วส่งออกเป็น PDF เพื่อแจกจ่าย  

คุณสามารถปรับโค้ดให้เข้ากับการรายงานหรือการเทมเพลตของคุณเองได้ และแบ่งปันผลลัพธ์ในคอมเมนต์!

## สิ่งที่คุณควรเรียนต่อไป

บทแนะนำต่อไปนี้ครอบคลุมหัวข้อที่เกี่ยวข้องอย่างใกล้ชิดและต่อยอดจากเทคนิคในคู่มือนี้ แต่ละแหล่งรวมโค้ดทำงานเต็มรูปแบบพร้อมคำอธิบายทีละขั้นตอน เพื่อช่วยคุณเชี่ยวชาญฟีเจอร์ API เพิ่มเติมและสำรวจแนวทางการทำงานอื่น ๆ ในโปรเจกต์ของคุณ

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Create rectangle shape, add shadow & save PDF](/words/english/net/programming-with-shapes/create-rectangle-shape-add-shadow-save-pdf/)
- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}