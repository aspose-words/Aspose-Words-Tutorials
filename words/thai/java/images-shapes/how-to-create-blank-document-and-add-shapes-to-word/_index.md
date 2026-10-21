---
category: general
date: 2026-09-18
description: สร้างเอกสารเปล่าและแทรกรูปทรงลงใน Word ด้วย Aspose.Words – เรียนรู้วิธีเพิ่มรูปสามเหลี่ยมและอื่น
  ๆ
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank document
- add shapes to word
- how to insert triangle
- add triangle shape
- create word document
language: th
lastmod: 2026-09-18
og_description: สร้างเอกสารเปล่าใน Word ด้วย Aspose.Words และเรียนรู้วิธีแทรกรูปสามเหลี่ยม,
  จัดกลุ่มรูปทรง, และกราฟิกอื่น ๆ ตามคู่มือฉบับสมบูรณ์นี้.
og_image_alt: Screenshot of a Word document showing a grouped shape with a triangle
  inside
og_title: สร้างเอกสารเปล่าและเพิ่มรูปทรงใน Word – คู่มือแบบขั้นตอนต่อขั้นตอน
schemas:
- author: Aspose
  dateModified: '2026-09-18'
  description: Create blank document and insert shapes to Word with Aspose.Words –
    learn how to add a triangle shape and more.
  headline: How to create blank document and add shapes to Word
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word automation
- Shapes
title: วิธีสร้างเอกสารเปล่าและเพิ่มรูปทรงใน Word
url: /th/java/images-shapes/how-to-create-blank-document-and-add-shapes-to-word/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# วิธีสร้างเอกสารเปล่าและเพิ่มรูปทรงใน Word

หากคุณต้องการ **สร้างเอกสารเปล่า** แล้วเพิ่มกราฟิกลงไป คู่มือนี้จะแสดงให้คุณเห็นขั้นตอนอย่างละเอียด เราจะเดินผ่านการสร้างไฟล์ Word ตั้งแต่เริ่มต้นและ **เพิ่มรูปทรงใน Word** รวมถึง **วิธีแทรกรูปสามเหลี่ยม** โดยใช้ Aspose.Words for Java.

คุณจะจบการสอนด้วยไฟล์ *.docx* ที่พร้อมใช้งานซึ่งมีรูปทรงที่จัดกลุ่มและบรรจุรูปสามเหลี่ยม ขั้นตอนครอบคลุมทุกอย่างตั้งแต่การตั้งค่าโครงการจนถึงการบันทึก **สร้างเอกสาร Word** ขั้นสุดท้าย ไม่จำเป็นต้องใช้เครื่องมือภายนอกใด ๆ นอกจาก Aspose.Words.

## ข้อกำหนดเบื้องต้น

* ติดตั้ง Java 17 หรือใหม่กว่า  
* Maven หรือ Gradle สำหรับการจัดการ dependencies  
* ใบอนุญาต Aspose.Words for Java (รุ่นประเมินฟรีสามารถใช้ได้สำหรับการสาธิตนี้)

หากคุณต้องการใช้ระบบ build อื่น ปรับไวยากรณ์ของ dependency ตามนั้น โค้ดจะทำงานบนแพลตฟอร์มใด ๆ ที่รองรับ Java

## สร้างเอกสารเปล่าด้วย Aspose.Words

การดำเนินการแรกคือ **สร้างเอกสารเปล่า** ในหน่วยความจำ Aspose.Words มีคลาส `Document` ที่เป็นตัวแทนของไฟล์ Word ที่ไม่มีเนื้อหาใด ๆ

```java
import com.aspose.words.*;

public class ShapeDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document
        Document doc = new Document();               // create blank document
```

`new Document()` constructor สร้างโครงสร้าง *.docx* ว่างเปล่า ซึ่งคุณสามารถเติมด้วยย่อหน้า ตาราง หรือกราฟิกในภายหลัง เนื่องจากเอกสารเป็นเปล่า คุณจึงมีการควบคุมเต็มที่ต่อทุกองค์ประกอบที่เพิ่มเข้าไป

## เพิ่มรูปทรงใน Word – การแทรกรูปทรงแบบกลุ่ม

รูปทรงแบบกลุ่มทำให้คุณจัดการกราฟิกหลายรายการเป็นหน่วยเดียว ซึ่งมีประโยชน์เมื่อคุณต้องการย้ายหรือปรับขนาดหลายรูปทรงพร้อมกัน

```java
        // Step 2: Initialize a DocumentBuilder to construct content
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 3: Insert a group shape of size 300 × 300 points
        GroupShape group = builder.insertGroupShape(300.0, 300.0);
```

`DocumentBuilder` เป็น API หลักสำหรับการเพิ่มเนื้อหา การเรียก `insertGroupShape` จะสร้างคอนเทนเนอร์ขนาด 300 × 300 points (ประมาณ 4 × 4 นิ้ว) หลังจากการเรียกนี้เคอร์เซอร์จะอยู่ *ภายใน* กลุ่ม พร้อมสำหรับการเพิ่มรูปทรงเพิ่มเติม

### ทำไมต้องใช้รูปทรงแบบกลุ่ม?

การจัดกลุ่มทำให้กราฟิกที่เกี่ยวข้องจัดเรียงกันและง่ายต่อการใช้รูปแบบเดียวกัน หากคุณต้องการย้ายรูปสามเหลี่ยมในภายหลัง ทั้งกลุ่มจะย้ายพร้อมกัน ทำให้การจัดวางคงที่

## วิธีแทรกรูปสามเหลี่ยมภายในกลุ่ม

ตอนนี้เราจะอธิบาย **วิธีแทรกรูปสามเหลี่ยม** รูปสามเหลี่ยมเป็นหนึ่งในค่า `ShapeType` ที่มีมาให้ในตัว

```java
        // Step 4: Move the cursor into the group's first paragraph
        builder.moveTo(group.getFirstParagraph());

        // Step 5: Insert a triangle shape of size 60 × 60 points inside the group
        builder.insertShape(ShapeType.TRIANGLE, 60.0, 60.0);
```

การเรียก `moveTo` ทำให้ตำแหน่งแทรกของ builder อยู่ที่ย่อหน้าแรกของกลุ่ม `insertShape` จากนั้นจะเพิ่มรูปสามเหลี่ยมขนาด 60 × 60 points เนื่องจากเคอร์เซอร์อยู่ภายในกลุ่ม รูปสามเหลี่ยมจึงเป็นลูกของรูปทรงกลุ่ม

**เคล็ดลับการเพิ่มรูปสามเหลี่ยม**:

* ขนาดวัดเป็น points; 72 points เท่ากับหนึ่งนิ้ว ปรับมิติให้เหมาะกับการจัดวางของคุณ  
* หากต้องการทิศทางอื่น ใช้ `builder.getCurrentParagraph().getParagraphFormat().setAlignment()` เพื่อจัดแนวรูปทรงภายในกลุ่ม  
* รูปสามเหลี่ยมจะสืบทอดสีเติมและสไตล์เส้นของกลุ่ม เว้นแต่คุณจะกำหนดค่าใหม่ด้วย `shape.getFillColor()` หรือ `shape.getStrokeColor()`

## บันทึกเอกสาร – สร้างเอกสาร Word

หลังจากสร้างกราฟิกแล้ว คุณจะบันทึกไฟล์ ขั้นตอนนี้สรุปการดำเนินการ **สร้างเอกสาร Word**

```java
        // Step 6: Save the document with the extended group shape
        doc.save("ExtendedGroup.docx");               // create word document
    }
}
```

`doc.save` เขียนข้อมูลในหน่วยความจำลงดิสก์เป็นเอกสาร Word มาตรฐาน คุณสามารถเปิด `ExtendedGroup.docx` ด้วย Microsoft Word, LibreOffice หรือโปรแกรมดูไฟล์ใด ๆ ที่รองรับรูปแบบ OOXML ไฟล์จะแสดงรูปทรงที่จัดกลุ่มซึ่งมีรูปสามเหลี่ยม ตามที่โค้ดสร้างขึ้น

## ตัวอย่างที่สามารถรันได้เต็มรูปแบบ

เมื่อรวมส่วนต่าง ๆ เข้าด้วยกัน นี่คือโปรแกรมเต็มที่คุณสามารถคัดลอก, คอมไพล์, และรันได้:

```java
import com.aspose.words.*;

public class ShapeDemo {
    public static void main(String[] args) throws Exception {
        // 1. Create a new blank document
        Document doc = new Document();

        // 2. Prepare a builder for inserting content
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 3. Insert a group shape (300 × 300 points)
        GroupShape group = builder.insertGroupShape(300.0, 300.0);

        // 4. Position the cursor inside the group
        builder.moveTo(group.getFirstParagraph());

        // 5. Insert a triangle shape (60 × 60 points)
        builder.insertShape(ShapeType.TRIANGLE, 60.0, 60.0);

        // 6. Save the file – this creates the final Word document
        doc.save("ExtendedGroup.docx");
    }
}
```

### ผลลัพธ์ที่คาดหวัง

เมื่อคุณเปิด `ExtendedGroup.docx` คุณจะเห็นรูปทรงกลุ่มเดียวที่อยู่ตรงกลางหน้า ภายในกลุ่มนั้นจะมีรูปสามเหลี่ยมขนาดเล็กปรากฏที่ตำแหน่งเริ่มต้น รูปสามเหลี่ยมสามารถเลือกและย้ายได้เป็นส่วนหนึ่งของกลุ่ม ยืนยันว่า **เพิ่มรูปทรงใน Word** ทำงานตามที่ตั้งใจ

## คำถามทั่วไปและกรณีขอบ

| Question | Answer |
|----------|--------|
| *ฉันสามารถเพิ่มรูปทรงมากกว่าหนึ่งรูปภายในกลุ่มได้หรือไม่?* | ได้. หลังจากแทรกรูปสามเหลี่ยม ให้คงเคอร์เซอร์อยู่ภายในกลุ่มและเรียก `builder.insertShape` อีกครั้งด้วย `ShapeType` ที่แตกต่าง |
| *ถ้าต้องการให้รูปสามเหลี่ยมเป็นสีแดงจะทำอย่างไร?* | ดึง `Shape` ที่คืนค่าจาก `insertShape` แล้วเรียก `shape.getFillColor().setColor(Color.RED)` |
| *วิธีนี้ทำงานกับไฟล์ .doc เก่าได้หรือไม่?* | Aspose.Words จะบันทึกในรูปแบบที่คุณระบุ ใช้ `doc.save("file.doc", SaveFormat.DOC)` เพื่อสร้างเอกสาร Word รุ่นเก่า |
| *ฉันจะเปลี่ยนเส้นขอบของกลุ่มได้อย่างไร?* | ใช้ `group.getStrokeColor().setColor(Color.BLUE)` และ `group.setLineWeight(2.0)` เพื่อปรับแต่งเส้นขอบ |
| *มีวิธีใดบ้างที่จะหมุนรูปสามเหลี่ยม?* | เรียก `shape.getRotation()` เพื่อกำหนดมุมเป็นหน่วยองศา |

## เคล็ดลับระดับมืออาชีพ

* **ใช้ builder ซ้ำ** – การสร้าง `DocumentBuilder` ใหม่สำหรับแต่ละรูปทรงเพิ่มภาระงาน เก็บ builder ตัวเดียวต่อเอกสาร  
* **การแปลงหน่วย** – หากทำงานกับมิลลิเมตร ให้แปลงเป็น points (`points = mm * 2.83465`)  
* **ประสิทธิภาพ** – สำหรับเอกสารขนาดใหญ่ ให้เรียก `doc.updatePageLayout()` เพียงครั้งเดียวหลังจากเพิ่มรูปทรงทั้งหมด

## สรุป

ตอนนี้คุณรู้วิธี **สร้างเอกสารเปล่า**, **เพิ่มรูปทรงใน Word**, และโดยเฉพาะ **วิธีแทรกรูปสามเหลี่ยม** ด้วย Aspose.Words for Java ตัวอย่างเต็มแสดงกระบวนการทำงานทั้งหมดตั้งแต่ไฟล์ว่างจนถึงการบันทึก **สร้างเอกสาร Word** ที่มีรูปสามเหลี่ยมจัดกลุ่ม

จากนี้คุณสามารถสำรวจค่า `ShapeType` เพิ่มเติม, ใช้สไตล์ที่กำหนดเอง, หรือรวมหลายกลุ่มเพื่อสร้างแผนภาพซับซ้อน ทดลองกับขนาด สี และตำแหน่งต่าง ๆ เพื่อเชี่ยวชาญการอัตโนมัติ Word ด้วย Java

--- 

*พร้อมที่จะอัตโนมัติรายงานต่อไปของคุณหรือยัง? คัดลอกตัวอย่าง ปรับขนาดตามต้องการ และรวมโค้ดเข้ากับแอปพลิเคชันของคุณวันนี้.*

## สิ่งที่คุณควรเรียนต่อไป

บทเรียนต่อไปนี้ครอบคลุมหัวข้อที่เกี่ยวข้องอย่างใกล้ชิดและต่อยอดจากเทคนิคที่แสดงในคู่มือนี้ แต่ละแหล่งข้อมูลมีตัวอย่างโค้ดทำงานครบถ้วนพร้อมคำอธิบายทีละขั้นตอน เพื่อช่วยให้คุณเชี่ยวชาญฟีเจอร์ API เพิ่มเติมและสำรวจวิธีการทำงานแบบอื่นในโครงการของคุณ

- [สร้างรูปทรงแบบกลุ่มในเอกสาร Word ด้วย Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [สร้างเอกสาร Word เปล่าพร้อมรูปสี่เหลี่ยมเงา – คู่มือขั้นตอนโดยละเอียด](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [สร้างรูปสี่เหลี่ยมใน Word ด้วย Aspose.Words – คู่มือขั้นตอนโดยละเอียด](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}