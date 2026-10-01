---
category: general
date: 2026-01-11
description: สร้างเอกสาร Word ด้วย Java อย่างรวดเร็วโดยการเพิ่มรูปสี่เหลี่ยม ตั้งค่าสีเติม
  และใส่เงาให้รูปทรง เรียนรู้ขั้นตอนทีละขั้นตอน.
draft: false
keywords:
- create word document java
- add rectangle shape
- apply shadow to shape
- set shape fill color
- how to add shape
language: th
og_description: สร้างเอกสาร Word ด้วย Java โดยแทรกรูปสี่เหลี่ยม ตั้งค่าสีเติม และใช้เงา
  คู่มือเต็มพร้อมโค้ด
og_title: สร้างเอกสาร Word ด้วย Java – เพิ่มรูปสี่เหลี่ยมพร้อมเงา
tags:
- Aspose.Words
- Java
- Document Generation
title: สร้างเอกสาร Word ด้วย Java – เพิ่มรูปสี่เหลี่ยมพร้อมเงา
url: /th/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# สร้าง Word Document Java – เพิ่มรูปสี่เหลี่ยมผืนผ้าพร้อมเงา

เคยต้องการ **create word document java** แล้วอยากให้ดูเป็นมืออาชีพขึ้นบ้างหรือไม่? บางทีคุณอาจกำลังสร้างตัวสร้างรายงานและหน้าเอกสารธรรมดาไม่พอใช้ ข่าวดีคือ ด้วย Aspose.Words for Java คุณสามารถวางรูปสี่เหลี่ยมลงในเอกสาร เติมสีสันให้มัน และแม้กระทั่งใส่เงาแบบเบา ๆ ได้ เพียงไม่กี่บรรทัดโค้ด

ในบทแนะนำนี้เราจะพาคุณผ่านขั้นตอนทั้งหมด: วิธีเพิ่มรูปสี่เหลี่ยม ตั้งค่าสีเติม และใส่เงาให้รูป เพื่อให้ไฟล์ Word ของคุณดูเป็นมืออาชีพยิ่งขึ้น เมื่อเสร็จแล้วคุณจะได้ตัวอย่างที่สามารถคัดลอก‑วางไปใช้ในโปรเจกต์ของคุณได้ทันที

## สิ่งที่คุณต้องเตรียม

- **Java 17** (หรือ JDK เวอร์ชันล่าสุด) – โค้ดใช้คุณสมบัติมาตรฐานของภาษา
- **Aspose.Words for Java** library – แนะนำเวอร์ชัน 23.9 หรือใหม่กว่า
- IDE หรือโปรแกรมแก้ไขข้อความที่คุณชอบ – IntelliJ IDEA, Eclipse, VS Code … เลือกตามใจคุณ
- โฟลเดอร์ที่ต้องการบันทึกไฟล์ `ShadowShape.docx` ที่สร้างขึ้น

ไม่ต้องทำการตั้งค่าเพิ่มเติมใด ๆ เพียงแค่เพิ่มไฟล์ JAR ของ Aspose.Words ไปยัง classpath ของคุณก็พร้อมใช้งาน

## ขั้นตอนที่ 1: ตั้งค่าโปรเจกต์และนำเข้า Aspose.Words

เริ่มแรกให้สร้างโปรเจกต์ Maven (หรือ Gradle) ใหม่แล้วเพิ่ม dependency ของ Aspose.Words ตัวอย่าง `pom.xml` ขั้นต่ำสำหรับ Maven:

```xml
<dependencies>
    <dependency>
        <groupId>com.aspose</groupId>
        <artifactId>aspose-words</artifactId>
        <version>23.9</version>
        <classifier>jdk17</classifier>
    </dependency>
</dependencies>
```

หากคุณไม่ได้ใช้ Maven เพียงแค่วางไฟล์ JAR ลงในโฟลเดอร์ `libs` ของคุณและเพิ่มเข้าไปใน build path

> **เคล็ดลับ:** Aspose มีไลเซนส์ทดลองฟรีที่คุณสามารถฝังได้ด้วย `License license = new License(); license.setLicense("Aspose.Words.lic");` หากต้องการทดสอบอย่างรวดเร็วสามารถข้ามได้; ไลบรารีจะทำงานในโหมดประเมินผล

## ขั้นตอนที่ 2: สร้าง Document และ DocumentBuilder ใหม่

ต่อไปเราจะ **create word document java** จริง ๆ คลาส `Document` แทนไฟล์ .docx ทั้งหมด ส่วน `DocumentBuilder` ใช้สำหรับแทรกเนื้อหา

```java
import com.aspose.words.*;

public class ShadowEffectDemo {
    public static void main(String[] args) throws Exception {
        // Initialize a blank Word document
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);
```

ตอนนี้คุณมีเอกสารเปล่าที่พร้อมรับรูปทรง, ย่อหน้า หรือสิ่งอื่นใดที่ต้องการ

## ขั้นตอนที่ 3: แทรกรูปสี่เหลี่ยมและตั้งค่าสีเติม

การเพิ่มรูปทำได้ง่าย ๆ เพียงเรียก `insertShape` เราจะใช้เทคนิค **add rectangle shape** ซึ่งเป็นคีย์เวิร์ดรอง *add rectangle shape*

```java
        // Insert a rectangle shape – 200pt wide, 100pt tall
        Shape rectangle = builder.insertShape(ShapeType.RECTANGLE, 200, 100);

        // Set the fill color to a bright orange
        rectangle.setFillColor(java.awt.Color.ORANGE);
```

ทำไมถึงเลือกสีส้ม? สีส้มโดดเด่นบนพื้นขาว แต่คุณก็สามารถเปลี่ยนเป็น `java.awt.Color` ใดก็ได้ตามต้องการ ขั้นตอนนี้สอดคล้องกับคีย์เวิร์ดรอง *set shape fill color*

## ขั้นตอนที่ 4: ตั้งค่าลักษณะเงา – Apply Shadow to Shape

ต่อมาคือส่วนที่สนุก: ใส่เงาตกเบา ๆ ให้กับสี่เหลี่ยม Aspose API มีอ็อบเจ็กต์ `ShadowFormat` ที่ควบคุมทุกแง่มุมของเงา

```java
        // Get the shadow format object for the shape
        ShadowFormat shadow = rectangle.getShadowFormat();

        // Make the shadow visible
        shadow.setVisible(true);

        // Choose a neutral gray for the shadow color
        shadow.setColor(java.awt.Color.GRAY);

        // Blur radius – larger values produce a softer edge
        shadow.setBlur(5.0);

        // Offset determines how far the shadow is displaced
        shadow.setOffsetX(4.0);
        shadow.setOffsetY(4.0);

        // Transparency (0 = opaque, 1 = fully transparent)
        shadow.setTransparency(0.2);

        // Define the shadow style and type
        shadow.setStyle(ShadowStyle.OUTER);
        shadow.setType(ShadowType.PARALLEL);

        // Scale controls the overall size of the shadow relative to the shape
        shadow.setScale(1.0);
```

บล็อกโค้ดนี้ **apply shadow to shape** ตามที่คีย์เวิร์ดรองบ่งบอก คุณสามารถปรับ `blur`, `offsetX/Y` และ `transparency` ให้เหมาะกับสไตล์ของคุณ ตัวอย่างเช่น `offsetX` ที่ใหญ่ขึ้นจะทำให้เงาดูโดดเด่นมากขึ้น ส่วน `transparency` ที่สูงจะทำให้เงาเบาบางเหมือนกระซิบ

## ขั้นตอนที่ 5: บันทึกเอกสาร

สุดท้ายให้เขียนเอกสารลงดิสก์ เลือกโฟลเดอร์ที่คุณมีสิทธิ์เขียนและตั้งชื่อไฟล์ให้ชัดเจน

```java
        // Save the result – adjust the path as needed
        document.save("YOUR_DIRECTORY/ShadowShape.docx");
    }
}
```

เมื่อคุณเปิด `ShadowShape.docx` ด้วย Microsoft Word หรือ LibreOffice คุณจะเห็นสี่เหลี่ยมสีส้มสดใสพร้อมเงาสีเทานุ่ม ๆ ลอยอยู่ใต้รูป

![create word document java with rectangle shape](/images/shadow-rectangle.png "create word document java – rectangle with shadow")

*ข้อความ alt ของรูปรวมคีย์เวิร์ดหลักไว้แล้ว จึงสอดคล้องกับกฎ SEO*

## คำถามที่พบบ่อย & กรณีพิเศษ

### ถ้าต้องการรูปแบบอื่น?

Aspose.Words รองรับค่า `ShapeType` มากมาย – ดาว, ลูกศร, คำอธิบาย ฯลฯ เพียงเปลี่ยน `ShapeType.RECTANGLE` เป็น `ShapeType.OVAL` หรือค่า enum อื่น ๆ ขั้นตอน **how to add shape** ยังคงใช้ได้เช่นเดิม

### จะใส่รูปลงในย่อหน้าที่เฉพาะเจาะจงได้อย่างไร?

แทนที่จะใส่รูปโดยตรงด้วย builder คุณสามารถสร้างรูปก่อน (`new Shape(document, ShapeType.RECTANGLE)`) แล้วเพิ่มลงใน `Paragraph` ด้วย `paragraph.appendChild(shape)` วิธีนี้ให้การควบคุมการจัดวางที่ละเอียดขึ้น

### สามารถใส่สีไล่ระดับ (gradient) แทนสีทึบได้หรือไม่?

ทำได้! ใช้ `rectangle.getFill().setFillType(FillType.GRADIENT)` แล้วกำหนด `LinearGradientFill` API ค่อนข้างยาวกว่าแต่เหมาะกับการออกแบบสมัยใหม่

### ความเข้ากันได้กับเวอร์ชัน Word เก่าเป็นอย่างไร?

Aspose.Words บันทึกเป็นฟอร์แมต .docx โดยค่าเริ่มต้น ซึ่งรองรับ Word 2007+ และ LibreOffice หากต้องการ .doc ให้เรียก `document.save("file.doc", SaveFormat.DOC)` การแสดงเงาอาจแตกต่างเล็กน้อย แต่รูปทรงจะยังคงอยู่

## ตัวอย่างทำงานเต็มรูปแบบ (Copy‑Paste Ready)

ด้านล่างเป็นโปรแกรมทั้งหมดพร้อมคอมไพล์และรัน แค่เปลี่ยน `YOUR_DIRECTORY` ให้เป็นพาธที่มีอยู่บนเครื่องของคุณ

```java
import com.aspose.words.*;

public class ShadowEffectDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new document and a builder
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Step 2: Insert a rectangle shape and set its fill color
        Shape rectangle = builder.insertShape(ShapeType.RECTANGLE, 200, 100);
        rectangle.setFillColor(java.awt.Color.ORANGE);

        // Step 3: Apply shadow to shape
        ShadowFormat shadow = rectangle.getShadowFormat();
        shadow.setVisible(true);
        shadow.setColor(java.awt.Color.GRAY);
        shadow.setBlur(5.0);
        shadow.setOffsetX(4.0);
        shadow.setOffsetY(4.0);
        shadow.setTransparency(0.2);
        shadow.setStyle(ShadowStyle.OUTER);
        shadow.setType(ShadowType.PARALLEL);
        shadow.setScale(1.0);

        // Step 4: Save the document
        document.save("YOUR_DIRECTORY/ShadowShape.docx");
    }
}
```

เมื่อรันโค้ดนี้จะได้ไฟล์ Word ที่มีสี่เหลี่ยมสีส้มพร้อมเงาสีเทานุ่ม ๆ – ตรงตามที่เราตั้งเป้าหมายเมื่อ **create word document java** พร้อมรูปทรงที่สไตล์ดี

## สรุป

ตอนนี้คุณมีสูตรครบวงจรสำหรับ **create word document java** ที่ *adds rectangle shape*, *sets shape fill color*, และ *applies shadow to shape* วิธีการตรงไปตรงมา API ใช้งานง่าย และคุณสามารถต่อยอดได้หลายรูปแบบ – รูปแบบอื่น ๆ, สีไล่ระดับ, หรือแม้แต่หลายเงาต่อรูปหนึ่ง

ต่อไปคุณอาจลองวางหลายรูปซ้อนกัน, ทดลองใช้ `ShadowStyle.ETCHED` เพื่อให้ได้ลุคที่แตกต่าง, หรือผสานกับการสร้างตารางเพื่อทำรายงานเต็มรูปแบบ ความเป็นไปได้จำกัดแค่จินตนาการของคุณ (และระดับไลเซนส์ของ Aspose)

หากคุณเจอปัญหาใดหรือมีไอเดียสำหรับการพัฒนาเพิ่มเติม แสดงความคิดเห็นด้านล่างได้เลย ขอให้สนุกกับการเขียนโค้ดและทำให้เอกสาร Word ของคุณดูน่าสนใจยิ่งขึ้น!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}