---
category: general
date: 2026-11-25
description: เพิ่มเงาให้กับรูปร่างในเอกสาร Word ด้วย Python เรียนรู้วิธีแทรกรูปสี่เหลี่ยมใน
  Word และใช้เงาโปร่งแสงด้วย Aspose.Words.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- add shadow to shape
- insert rectangle shape word
- how to create word document python
- Aspose.Words Python
- shape formatting Python
language: th
lastmod: 2026-11-25
og_description: เพิ่มเงาให้กับรูปทรงในเอกสาร Word ด้วย Python บทเรียนนี้แสดงวิธีแทรกรูปสี่เหลี่ยมใน
  Word และตั้งค่าเงาที่โปร่งแสง 30 % ด้วย Aspose.Words.
og_image_alt: Add shadow to shape example in a Word document created by Python
og_title: เพิ่มเงาให้รูปทรงในเอกสาร Word ด้วย Python – คู่มือขั้นตอนโดยละเอียด
schemas:
- author: Aspose
  dateModified: '2026-11-25'
  description: Add shadow to shape in a Word document with Python. Learn how to insert
    rectangle shape in Word and apply a transparent shadow using Aspose.Words.
  headline: How to add shadow to shape in a Word document using Python
  type: TechArticle
tags:
- Python
- Aspose.Words
- Word automation
title: วิธีเพิ่มเงาให้กับรูปทรงในเอกสาร Word ด้วย Python
url: /th/python/images-shapes/how-to-add-shadow-to-shape-in-a-word-document-using-python/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# วิธีเพิ่มเงาให้รูปทรงในเอกสาร Word ด้วย Python

หากคุณต้องการ **เพิ่มเงาให้รูปทรง** ในเอกสาร Word คำแนะนำนี้จะแสดงวิธีแก้ไขที่สมบูรณ์และสามารถรันได้ คุณจะได้เห็นวิธีสร้างไฟล์ Word, แทรกรูปสี่เหลี่ยม, และใช้เงาโปร่งแสง 30 % — ทั้งหมดด้วยไลบรารี Aspose.Words for Python.

ทำงานกับเอกสาร Word อย่างอัตโนมัติช่วยลดการจัดรูปแบบด้วยมือและทำให้คุณสร้างรายงาน, สัญญา, หรือโบรชัวร์การตลาดได้ในปริมาณมาก เมื่อจบบทเรียนนี้คุณจะสามารถตอบคำถาม “**วิธีสร้างเอกสาร Word ด้วย Python**” ด้วยตัวอย่างโค้ดที่พร้อมรันได้

## ข้อกำหนดเบื้องต้น

* Python 3.8 หรือใหม่กว่า ที่ติดตั้งแล้ว
* ใบอนุญาต Aspose.Words for Python ที่ใช้งานได้ (รุ่นทดลองฟรีใช้เพื่อการประเมินผล)
* แพ็กเกจ `aspose-words` ที่ติดตั้งผ่าน `pip install aspose-words`.
* โฟลเดอร์ที่สามารถบันทึกไฟล์ผลลัพธ์ได้ (แทนที่ `YOUR_DIRECTORY` ในโค้ด).

ไม่ต้องการการพึ่งพาเพิ่มเติม

## ขั้นตอนที่ 1: สร้างเอกสาร Word ใหม่

ขั้นตอนแรกคือการสร้างอ็อบเจ็กต์ `Document` ซึ่งอ็อบเจ็กต์นี้แทนไฟล์ .docx ทั้งหมดในหน่วยความจำ

```python
import aspose.words as aw

# Create an empty Word document
doc = aw.Document()
# DocumentBuilder provides a convenient API for adding content
builder = aw.DocumentBuilder(doc)
```

`DocumentBuilder` ทำงานคล้ายกับเคอร์เซอร์เสมือน เมื่อคุณเรียกใช้เมธอดของมัน ไลบรารีจะใส่องค์ประกอบที่สอดคล้องกันที่ตำแหน่งเคอร์เซอร์ปัจจุบัน

## ขั้นตอนที่ 2: แทรกรูปสี่เหลี่ยมใน Word

ต่อไปคุณ **แทรกรูปสี่เหลี่ยม** โดยใช้เมธอด `insert_shape` ของ builder เมธอดนี้ต้องการประเภทของรูปทรงและขนาดเป็นหน่วยพอยต์ (1 พอยต์ = 1/72 นิ้ว)

```python
# Insert a rectangle shape that is 100 points wide and 50 points tall
shape = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 100, 50)
```

คุณสามารถเปลี่ยนขนาดให้ตรงกับการออกแบบของคุณ รูปสี่เหลี่ยมจะเป็นส่วนหนึ่งของเลเยอร์การวาดของเอกสาร ซึ่งหมายความว่าคุณสามารถแก้ไขการเติมสี, เส้นขอบ หรือเงาในภายหลังได้

## ขั้นตอนที่ 3: เข้าถึงรูปแบบเงาของรูปทรง

อ็อบเจ็กต์การวาดทุกตัวจะเปิดเผยคุณสมบัติ `shadow_format` ที่ควบคุมลักษณะของเงา ดึงคุณสมบัตินี้เพื่อปรับความโปร่งแสง, การเลื่อน, ความเบลอ, และสี

```python
# Get the ShadowFormat object for the rectangle
shadow = shape.shadow_format
```

ในขั้นตอนนี้รูปทรงยังมีเงาเริ่มต้น (ไม่มีเงา) วัตถุ `ShadowFormat` จะเก็บพารามิเตอร์ทั้งหมดที่คุณต้องการเพื่อสร้างเอฟเฟกต์ที่สมจริง

## ขั้นตอนที่ 4: ทำให้เงาโปร่งแสง 30 %

ความโปร่งแสงจะระบุเป็นค่าระหว่าง `0` (ทึบเต็ม) ถึง `1` (โปร่งแสงเต็ม) การตั้งค่าเป็น `0.3` จะให้เงาโปร่งแสง 30 % ซึ่งมักเพียงพอที่จะเพิ่มความลึกโดยไม่ทำให้ข้อความดูอัดแน่นเกินไป

```python
# Apply a 30 % transparent shadow
shadow.transparency = 0.3
# Optional: adjust other shadow properties for a nicer look
shadow.visible = True               # Ensure the shadow is turned on
shadow.distance = 4                 # Distance of the shadow from the shape (points)
shadow.blur = 4                     # Amount of blur applied to the shadow
shadow.color = aw.Color.black       # Shadow color
```

คุณสมบัติเพิ่มเติมเหล่านี้ไม่จำเป็นต้องใช้ แต่ช่วยแสดงวิธีการปรับแต่งเอฟเฟกต์อย่างละเอียด ธง `visible` เป็นสิ่งสำคัญ; หากลืมตั้งค่า เงาจะไม่ปรากฏแม้ว่าการตั้งค่าอื่น ๆ จะถูกกำหนดไว้แล้ว

## ขั้นตอนที่ 5: บันทึกเอกสารเพื่อดูผลลัพธ์

สุดท้าย ให้บันทึกเอกสารลงดิสก์ การเปิดไฟล์ `.docx` ที่ได้ใน Microsoft Word หรือโปรแกรมดูไฟล์ที่รองรับจะแสดงรูปสี่เหลี่ยมพร้อมเงาโปร่งแสงที่ถูกนำไปใช้

```python
# Save the document to the desired location
output_path = r"YOUR_DIRECTORY/output.docx"
doc.save(output_path)
print(f"Document saved to {output_path}")
```

เมื่อคุณเปิด `output.docx` คุณจะเห็นรูปสี่เหลี่ยมธรรมดาพร้อมเงาสีเทาอ่อนที่เลื่อนไปด้านล่าง‑ขวา ความโปร่งแสง 30 % ของเงาทำให้รูปทรงดูเหมือนลอยขึ้นจากหน้า

![Add shadow to shape example](placeholder-image.png){: .align-center alt="ตัวอย่างการเพิ่มเงาให้รูปทรงในเอกสาร Word ที่สร้างด้วย Python"}

## สคริปต์เต็มที่สามารถรันได้

การรวมส่วนต่าง ๆ เข้าด้วยกันจะให้สคริปต์ที่ทำงานได้เองซึ่งคุณสามารถคัดลอก, วาง, และรันได้ทันที

```python
import aspose.words as aw

def create_word_with_shadow(output_path: str):
    """
    Creates a Word document that contains a rectangle shape
    with a 30 % transparent shadow.
    """
    # Step 1: Initialize document and builder
    doc = aw.Document()
    builder = aw.DocumentBuilder(doc)

    # Step 2: Insert rectangle shape
    shape = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 100, 50)

    # Step 3: Access shadow format
    shadow = shape.shadow_format

    # Step 4: Configure shadow properties
    shadow.visible = True
    shadow.transparency = 0.3
    shadow.distance = 4
    shadow.blur = 4
    shadow.color = aw.Color.black

    # Step 5: Save the document
    doc.save(output_path)
    print(f"Document saved to {output_path}")

if __name__ == "__main__":
    # Replace with a valid folder on your machine
    create_word_with_shadow(r"YOUR_DIRECTORY/output.docx")
```

**ผลลัพธ์ที่คาดหวัง:** การเปิด `output.docx` ที่สร้างขึ้นจะแสดงหน้าเดียวที่มีรูปสี่เหลี่ยมที่สร้างเงาอ่อนแสงและกึ่ง‑โปร่งแสง ไม่จำเป็นต้องจัดรูปแบบเพิ่มเติม

## ความแปรผันทั่วไปและกรณีขอบ

| สถานการณ์ | วิธีปรับโค้ด |
|-----------|--------------|
| **ประเภทรูปทรงที่แตกต่าง** (เช่น วงรี) | เปลี่ยน `aw.drawing.ShapeType.RECTANGLE` เป็น `aw.drawing.ShapeType.ELLIPSE`. |
| **สีเงาที่กำหนดเอง** | ตั้งค่า `shadow.color = aw.Color.from_argb(255, 128, 0, 0)` เพื่อให้ได้เงาสีแดงอมน้ำตาล. |
| **หลายรูปทรง** | เรียก `builder.insert_shape` ซ้ำหลายครั้ง; แต่ละครั้งจะคืนอ็อบเจ็กต์ `Shape` แยกต่างหากที่คุณสามารถกำหนดสไตล์ได้อย่างอิสระ. |
| **บันทึกเป็น PDF** | แทนที่ `doc.save(output_path)` ด้วย `doc.save(output_path.replace('.docx', '.pdf'))` และใช้ส่วนขยาย `.pdf`. |
| **รันโดยไม่มีใบอนุญาต** | รุ่นทดลองฟรีจะเพิ่มลายน้ำในหน้าแรก รับใบอนุญาตเพื่อเอาลายน้ำออกสำหรับการใช้งานในผลิตภัณฑ์. |

การแปรผันเหล่านี้แสดงให้เห็นว่ารูปแบบเดียวกัน — สร้างเอกสาร, แทรกรูปทรง, ปรับ `shadow_format`, บันทึก — ครอบคลุมสถานการณ์อัตโนมัติจำนวนมาก

## เคล็ดลับและแนวทางปฏิบัติที่ดีที่สุด

* **ใช้ builder ซ้ำ**: เก็บอินสแตนซ์ `DocumentBuilder` เพียงหนึ่งตัวสำหรับทั้งเอกสารเพื่อหลีกเลี่ยงการสร้างอ็อบเจ็กต์ที่ไม่จำเป็น.
* **ปล่อยทรัพยากร**: ในบริการที่ทำงานต่อเนื่องเป็นเวลานาน ให้เรียก `doc.dispose()` หลังบันทึกเพื่อคืนหน่วยความจำเนทีฟ.
* **ตรวจสอบผลลัพธ์**: ใช้ `doc.validate(aw.ValidationType.FULL_VALIDATION)` ก่อนบันทึกหากต้องการยืนยันว่าตรงตามมาตรฐาน Open XML.
* **ความเข้ากันได้ของเวอร์ชัน**: โค้ดทำงานกับ Aspose.Words for Python ≥ 22.9. ตรวจสอบให้แน่ใจว่าแพ็กเกจของคุณเป็นเวอร์ชันล่าสุดด้วย `pip install --upgrade aspose-words`.

## สรุป

ตอนนี้คุณรู้วิธี **เพิ่มเงาให้รูปทรง** ในเอกสาร Word ด้วย Python แล้ว โดยทำตามห้าขั้นตอน — สร้างเอกสาร, **แทรกรูปสี่เหลี่ยมใน Word**, ตั้งค่าเงา, และบันทึก — คุณสามารถทำอัตโนมัติการสร้างเอกสารที่ดูเป็นมืออาชีพสำหรับรายงาน, ใบแจ้งหนี้, หรือสื่อการตลาด  

ต่อจากนี้คุณอาจสำรวจตัวเลือกการจัดรูปแบบอื่น ๆ เช่น การเติมสีไล่ระดับ, การล้อมข้อความ, หรือการแปลงเอกสารเป็น PDF แต่ละหัวข้อเหล่านี้อิงจาก `DocumentBuilder` และแนวคิดการจัดรูปแบบรูปทรงที่แนะนำในบทเรียนนี้  

ขอให้สนุกกับการเขียนโค้ด และเพลิดเพลินกับความลึกของภาพที่เงาแบบง่ายสามารถเพิ่มให้กับเอกสาร Word ที่คุณสร้างอัตโนมัติ!

## คุณควรเรียนรู้อะไรต่อไป?

บทเรียนต่อไปนี้ครอบคลุมหัวข้อที่เกี่ยวข้องอย่างใกล้ชิดและต่อยอดจากเทคนิคที่แสดงในคู่มือนี้ แต่ละแหล่งข้อมูลมีตัวอย่างโค้ดที่ทำงานครบถ้วนพร้อมคำอธิบายทีละขั้นตอน เพื่อช่วยคุณเชี่ยวชาญฟีเจอร์ API เพิ่มเติมและสำรวจแนวทางการนำไปใช้แบบอื่นในโครงการของคุณ

- [วิธีสร้างรูปสี่เหลี่ยมในเอกสาร Word ด้วย Python](/words/english/python-net/images-shapes/how-to-create-rectangle-shape-in-a-word-document-using-pytho/)
- [เพิ่มเงาให้รูปทรงใน Python – บทแนะนำ Aspose.Words อย่างครบถ้วน](/words/english/python-net/images-shapes/add-shadow-to-shape-in-python-complete-aspose-words-tutorial/)
- [สร้างเอกสาร Word เปล่าและเพิ่มเงาให้รูปทรง – คู่มือ Python ฉบับเต็ม](/words/english/python-net/images-shapes/create-blank-word-document-and-add-shadow-to-shape-full-pyth/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}