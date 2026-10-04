---
category: general
date: 2026-10-04
description: วิธีสร้างเอกสารใน Python และเพิ่มเงาให้กับรูปทรงโดยใช้ Aspose.Words เรียนรู้การตั้งค่าสีเงา
  แทรกรูปสี่เหลี่ยม และปรับแต่งเงานอก
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to create document
- add shadow to shape
- set shadow color
- insert rectangle shape
- how to add shadow
language: th
lastmod: 2026-10-04
og_description: วิธีสร้างเอกสารใน Python และเพิ่มเงาให้กับรูปทรง คู่มือฉบับนี้จะแสดงวิธีตั้งค่าสีเงา
  แทรกรูปสี่เหลี่ยมผืนผ้า และใช้เงานอกด้วย Aspose.Words.
og_image_alt: Python code inserting a rectangle shape with a visible shadow into a
  Word document
og_title: วิธีสร้างเอกสารด้วยรูปสี่เหลี่ยมและเงาใน Python
schemas:
- author: Aspose
  dateModified: '2026-10-04'
  description: How to create document in Python and add shadow to shape using Aspose.Words.
    Learn to set shadow color, insert rectangle shape, and customize outer shadow.
  headline: How to create document with a rectangle shape and shadow in Python
  type: TechArticle
- description: How to create document in Python and add shadow to shape using Aspose.Words.
    Learn to set shadow color, insert rectangle shape, and customize outer shadow.
  name: How to create document with a rectangle shape and shadow in Python
  steps:
  - name: Why does the shadow sometimes appear invisible?
    text: The shadow is only rendered if `shadow.visible` is set to `True` **and**
      the shape’s `wrap_type` allows it to be displayed. An inline shape works reliably;
      floating shapes may require additional layout adjustments.
  - name: How can I change the shadow color to match a brand palette?
    text: 'Replace `aw.drawing.Color.black` with a custom RGB value:'
  - name: What if I need the shape to appear behind text?
    text: Set the wrap type to `WrapType.BEHIND` and adjust the `z_order_position`
      if necessary. Keep in mind that some viewers may render behind‑text shapes differently.
  - name: Can I apply the same shadow settings to multiple shapes?
    text: Yes. Create a helper function that configures the shadow and call it for
      each shape you insert. This promotes code reuse and ensures consistent styling.
  type: HowTo
tags:
- Aspose.Words
- Python
- Word automation
title: วิธีสร้างเอกสารที่มีรูปสี่เหลี่ยมและเงาใน Python
url: /th/python/images-shapes/how-to-create-document-with-a-rectangle-shape-and-shadow-in/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# วิธีสร้างเอกสารที่มีรูปสี่เหลี่ยมและเงาใน Python

หากคุณต้องการ **วิธีสร้างเอกสาร** ที่มีรูปสี่เหลี่ยมที่ออกแบบสวยงาม คู่มือนี้จะให้วิธีแก้ไขที่สมบูรณ์ คุณจะได้เรียนรู้วิธี **เพิ่มเงาให้กับรูปร่าง**, ตั้งค่าสีของเงา, และควบคุมการเยื้องและการเบลอ—all ด้วย Aspose.Words for Python. เมื่อจบบทเรียนแล้วคุณจะสามารถสร้างไฟล์ `.docx` ที่ดูเรียบหรูและพร้อมสำหรับการแจกจ่ายได้

ขั้นตอนต่อไปนี้ครอบคลุมทุกอย่างตั้งแต่การติดตั้งไลบรารีจนถึงการปรับแต่งลักษณะของเงา ไม่ต้องอ้างอิงเอกสารภายนอก; โค้ดพร้อมคัดลอก, รัน, และปรับใช้กับโปรเจกต์ของคุณเอง คุณยังจะได้เรียนรู้วิธี **แทรกรูปสี่เหลี่ยม**, เลือก **สไตล์เงานอก**, และจัดการกับปัญหาทั่วไปเช่นเงาที่ไม่มองเห็นหรือการตั้งค่า wrap ที่ไม่ถูกต้อง

## ข้อกำหนดเบื้องต้น

ก่อนเริ่มทำงาน, โปรดตรวจสอบว่าคุณมี:

* Python 3.8 หรือใหม่กว่า
* ใบอนุญาต Aspose.Words for Python ที่ใช้งานได้ (หรือคีย์ทดลองฟรี)
* ความคุ้นเคยพื้นฐานกับการเขียนสคริปต์ Python
* สิทธิ์เข้าถึงตำแหน่งไฟล์ระบบที่ไฟล์เอกสารที่สร้างจะถูกบันทึก

คุณสามารถติดตั้ง SDK ด้วย pip:

```bash
pip install aspose-words
```

## ขั้นตอนที่ 1: นำเข้าไลบรารีและสร้างเอกสารเปล่าใหม่

การสร้างเอกสารใหม่เป็นการกระทำแรกในทุกสถานการณ์การทำอัตโนมัติของ Word ตัวสร้าง `aw.Document()` จะให้ไฟล์เปล่าที่คุณสามารถเติมข้อความ, รูปภาพ, หรือรูปร่างได้

```python
import aspose.words as aw

# Create a new blank document
document = aw.Document()
builder = aw.DocumentBuilder(document)
```

อ็อบเจกต์ `DocumentBuilder` ทำให้การแทรกเนื้อหาง่ายขึ้น มันจะติดตามตำแหน่งเคอร์เซอร์ปัจจุบัน, ดังนั้นคุณสามารถเพิ่มองค์ประกอบต่อเนื่องกันโดยไม่ต้องจัดการส่วนต่าง ๆ ด้วยตนเอง

## ขั้นตอนที่ 2: แทรกรูปสี่เหลี่ยมขนาดที่ต้องการ

รูปสี่เหลี่ยมทำหน้าที่เป็นคอนเทนเนอร์สำหรับองค์ประกอบภาพ คุณสามารถกำหนดความกว้างและความสูงเป็นหน่วยพอยท์ (1 pt ≈ 1/72 in)

```python
# Insert a rectangle shape that is 150 pt wide and 80 pt tall
rectangle_shape = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 150, 80)
```

ในขณะนี้รูปยังไม่มีการจัดรูปแบบใด ๆ จึงปรากฏเป็นเส้นขอบธรรมดา ขั้นตอนต่อไปจะทำให้มันมีความลึกและสีสัน

## ขั้นตอนที่ 3: ตั้งค่ารูปร่างให้ไหลแบบ inline กับข้อความรอบข้าง

เมื่อรูปร่างเป็น **inline**, มันทำงานเหมือนอักขระในย่อหน้า ซึ่งทำให้สี่เหลี่ยมอยู่ในตำแหน่งที่คุณคาดหวังในเลย์เอาต์ของเอกสาร

```python
# Make the shape inline so it follows the text flow
rectangle_shape.wrap_type = aw.drawing.WrapType.INLINE
```

หากคุณต้องการให้รูปร่างลอยเหนือข้อความ, คุณสามารถใช้ `WrapType.SQUARE` หรือ `WrapType.TOP_BOTTOM`, แต่สำหรับรายงานส่วนใหญ่รูปร่างแบบ inline จะทำให้เลย์เอาต์คาดเดาได้ง่ายกว่า

## ขั้นตอนที่ 4: ทำให้เงาแสดงผลและเลือกสีของเงา

เงาที่ไม่มองเห็นจะไม่มีประโยชน์ด้านภาพ `visible` flag จะเปิดใช้งานเอฟเฟกต์, และคุณสมบัติ `color` จะกำหนดโทนสี การใช้สีดำให้ความลึกแบบคลาสสิกและละเอียดอ่อน

```python
# Enable the shadow and set its color to black
rectangle_shape.shadow.visible = True
rectangle_shape.shadow.color = aw.drawing.Color.black
```

คุณสามารถเปลี่ยน `aw.drawing.Color.black` เป็นสีอื่นได้, เช่น `aw.drawing.Color.gray` หรือค่ารหัส RGB ที่กำหนดเอง (`aw.drawing.Color.from_argb(255, 128, 128, 128)`)

## ขั้นตอนที่ 5: กำหนดการเยื้องและการเบลอของเงาเพื่อให้มีความลึก

การเยื้องควบคุมระยะที่เงาเลื่อนออกจากรูปร่าง, ส่วนรัศมีการเบลอจะทำให้ขอบเงานุ่มขึ้น ค่าเล็กให้เงาคมชัด; ค่ามากให้ลุคที่นุ่มนวลกว่า

```python
# Horizontal and vertical offset of 5 pt each
rectangle_shape.shadow.offset_x = 5
rectangle_shape.shadow.offset_y = 5

# Blur radius of 3 pt for a gentle feather
rectangle_shape.shadow.blur = 3
```

ลองปรับค่าต่าง ๆ เพื่อให้ตรงกับแนวทางการออกแบบของคุณ สำหรับเงาตกหนักอาจเพิ่มค่าเยื้องและเบลอพร้อมกัน

## ขั้นตอนที่ 6: เลือกสไตล์เงานอก

Aspose.Words มีสไตล์เงาหลายแบบ, เช่น `INNER`, `OUTER`, และ `PERSPECTIVE`. สไตล์ **outer** จะวางเงานอกเส้นขอบของรูปร่าง, เหมาะสำหรับลุคที่สะอาดและเป็นมืออาชีพ

```python
# Apply an outer shadow style
rectangle_shape.shadow.style = aw.drawing.ShadowStyle.OUTER
```

หากต้องการเอฟเฟกต์ที่โดดเด่นกว่า, ลอง `ShadowStyle.PERSPECTIVE`—มันจะเพิ่มการเอียงสามมิติ

## ขั้นตอนที่ 7: บันทึกเอกสารพร้อมเงาที่กำหนดรูปแบบ

การบันทึกจะสรุปไฟล์และเขียนรูปแบบทั้งหมดลงดิสก์ เลือกไดเรกทอรีที่คุณมีสิทธิ์เขียนและตั้งชื่อไฟล์ให้สื่อความหมาย

```python
# Save the document to the desired location
output_path = "output/ShapeWithShadow.docx"
document.save(output_path)
print(f"Document saved to {output_path}")
```

เมื่อรันสคริปต์จะได้ไฟล์ Word ที่มีสี่เหลี่ยมพร้อมเงาที่มองเห็นและมีสี เปิดไฟล์ใน Microsoft Word หรือ LibreOffice เพื่อยืนยันผลลัพธ์

## ตัวอย่างที่สามารถรันได้เต็มรูปแบบ

ด้านล่างเป็นสคริปต์เต็มที่รวมทุกขั้นตอนที่อธิบายไว้ คัดลอกโค้ดไปยังไฟล์ชื่อ `create_shadowed_shape.py` แล้วรันด้วย `python create_shadowed_shape.py`

```python
import aspose.words as aw
import os

def main():
    # Ensure the output directory exists
    output_dir = "output"
    os.makedirs(output_dir, exist_ok=True)

    # Step 1: Create a new blank document
    document = aw.Document()
    builder = aw.DocumentBuilder(document)

    # Step 2: Insert a rectangle shape of the desired size
    rectangle_shape = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 150, 80)

    # Step 3: Set the shape to be inline with the text flow
    rectangle_shape.wrap_type = aw.drawing.WrapType.INLINE

    # Step 4: Make the shadow visible and choose its color
    rectangle_shape.shadow.visible = True
    rectangle_shape.shadow.color = aw.drawing.Color.black

    # Step 5: Define the shadow's offset and blur to give it depth
    rectangle_shape.shadow.offset_x = 5   # horizontal offset in points
    rectangle_shape.shadow.offset_y = 5   # vertical offset in points
    rectangle_shape.shadow.blur = 3       # blur radius in points

    # Step 6: Choose an outer shadow style
    rectangle_shape.shadow.style = aw.drawing.ShadowStyle.OUTER

    # Step 7: Save the document with the shaped shadow
    output_path = os.path.join(output_dir, "ShapeWithShadow.docx")
    document.save(output_path)
    print(f"Document saved to {output_path}")

if __name__ == "__main__":
    main()
```

**ผลลัพธ์ที่คาดหวัง**

เมื่อคุณเปิด `ShapeWithShadow.docx`, จะเห็นสี่เหลี่ยมเดียวอยู่กึ่งกลางหน้า สี่เหลี่ยมมีเงาดำสีอ่อนที่เยื้องไปด้านล่าง‑ขวาและเบลอเล็กน้อยเพื่อสร้างความลึก เงาใช้สไตล์ outer จึงไม่ตัดกับภายในสี่เหลี่ยม

## คำถามทั่วไปและกรณีขอบ

### ทำไมเงาบางครั้งถึงไม่ปรากฏ?

เงาจะถูกเรนเดอร์ก็ต่อเมื่อ `shadow.visible` ถูกตั้งค่าเป็น `True` **และ** `wrap_type` ของรูปร่างอนุญาตให้แสดงผล รูปร่างแบบ inline ทำงานได้อย่างเชื่อถือได้; รูปร่างลอยอาจต้องปรับการจัดเลย์เอาต์เพิ่มเติม

### จะเปลี่ยนสีเงาให้ตรงกับพาเลตของแบรนด์ได้อย่างไร?

เปลี่ยน `aw.drawing.Color.black` เป็นค่ารหัส RGB ที่กำหนดเอง:

```python
rectangle_shape.shadow.color = aw.drawing.Color.from_argb(255, 0, 120, 215)  # corporate blue
```

### ถ้าต้องการให้รูปร่างอยู่ด้านหลังข้อความจะทำอย่างไร?

ตั้ง `wrap_type` เป็น `WrapType.BEHIND` และปรับ `z_order_position` หากจำเป็น ควรจำไว้ว่าโปรแกรมแสดงผลบางตัวอาจแสดงรูปร่างที่อยู่ด้านหลังข้อความแตกต่างกัน

### สามารถใช้การตั้งค่าเงาเดียวกันกับหลายรูปร่างได้หรือไม่?

ได้. สร้างฟังก์ชันช่วยเหลือที่กำหนดค่าเงาและเรียกใช้สำหรับแต่ละรูปร่างที่คุณแทรก วิธีนี้ช่วยให้โค้ดใช้ซ้ำและทำให้สไตล์สอดคล้องกัน

```python
def apply_shadow(shape, color=aw.drawing.Color.black, offset=5, blur=3):
    shape.shadow.visible = True
    shape.shadow.color = color
    shape.shadow.offset_x = offset
    shape.shadow.offset_y = offset
    shape.shadow.blur = blur
    shape.shadow.style = aw.drawing.ShadowStyle.OUTER
```

## สรุป

คุณได้เรียนรู้ **วิธีสร้างเอกสาร** ที่มีรูปสี่เหลี่ยมพร้อมเงาที่กำหนดเองด้วย Aspose.Words for Python แล้ว บทเรียนได้ครอบคลุมการแทรกรูปสี่เหลี่ยม, ทำให้รูปร่างเป็น inline, เปิดใช้งานเงา, ตั้งค่าสี, การเยื้อง, การเบลอ, สไตล์, และสุดท้ายการบันทึกไฟล์

จากนี้คุณสามารถสำรวจหัวข้อที่เกี่ยวข้องเช่น **add shadow to shape** สำหรับรูปแบบอื่น ๆ, **set shadow color** แบบไดนามิกตามข้อมูล, หรือ **how to add shadow** ให้กับรูปภาพและกล่องข้อความ ทดลองปรับขนาด, สี, และสไตล์เงาต่าง ๆ เพื่อให้สอดคล้องกับแนวทางแบรนด์หรือระบบออกแบบของคุณ

พร้อมที่จะทำอัตโนมัติเพิ่มเติมในเอกสาร Word หรือยัง? ลองเพิ่มตาราง, ส่วนหัว, หรือเนื้อหาแบบไดนามิกต่อไป—แต่ละขั้นตอนต่อยอดจากหลักการเดียวกันที่แสดงในที่นี้ ขอให้สนุกกับการเขียนโค้ด!

## สิ่งที่คุณควรเรียนต่อไป

บทแนะนำต่อไปนี้ครอบคลุมหัวข้อที่เกี่ยวข้องอย่างใกล้ชิดและต่อยอดจากเทคนิคที่แสดงในคู่มือนี้ แต่ละแหล่งรวมตัวอย่างโค้ดทำงานเต็มรูปแบบพร้อมคำอธิบายขั้นตอนเพื่อช่วยคุณเชี่ยวชาญฟีเจอร์ API เพิ่มเติมและสำรวจแนวทางการทำงานอื่น ๆ ในโปรเจกต์ของคุณ

- [Create rectangle shape, add shadow & save PDF](/words/english/net/programming-with-shapes/create-rectangle-shape-add-shadow-save-pdf/)
- [Create Blank Word Document with Shadowed Rectangle Shape – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [How to Manage Document Variables with Aspose.Words in Python&#58; A Complete Guide](/words/english/python-net/document-properties-metadata/aspose-words-python-manage-document-variables/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}