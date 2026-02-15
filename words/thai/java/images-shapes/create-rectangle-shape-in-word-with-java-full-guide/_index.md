---
category: general
date: 2026-02-15
description: สร้างรูปสี่เหลี่ยมในเอกสาร Word ด้วย Java เรียนรู้วิธีเพิ่มเงาของรูป
  บันทึกเอกสาร Word และเพิ่มรูปสี่เหลี่ยมด้วย Aspose.Words.
draft: false
keywords:
- create rectangle shape
- save word document
- how to shadow shape
- add shape shadow
- add rectangle shape
language: th
og_description: สร้างรูปสี่เหลี่ยมในไฟล์ Word ด้วย Java คู่มือนี้แสดงวิธีเพิ่มเงาให้รูปทรง,
  บันทึกเอกสาร Word, และเพิ่มรูปสี่เหลี่ยมขั้นตอนโดยขั้นตอน.
og_title: สร้างรูปสี่เหลี่ยมผืนผ้า – บทแนะนำ Java Aspose.Words
tags:
- Aspose.Words
- Java
- Document Automation
title: สร้างรูปสี่เหลี่ยมใน Word ด้วย Java – คู่มือเต็ม
url: /th/java/images-shapes/create-rectangle-shape-in-word-with-java-full-guide/
---

lists, blockquotes, code placeholders.

Check for any missed bolds: we kept bold terms unchanged.

Now produce final content.{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# สร้างรูปสี่เหลี่ยมใน Word ด้วย Java – คู่มือเต็ม

เคยต้องการ **create rectangle shape** ในไฟล์ Word แต่ไม่แน่ใจว่าจะเริ่มจากตรงไหนหรือไม่? คุณไม่ได้เป็นคนเดียว—นักพัฒนาจำนวนมากเจออุปสรรคนี้เมื่อต้องทำอัตโนมัติรายงานหรือใบแจ้งหนี้ ข่าวดีคือ? ด้วย Aspose.Words for Java คุณสามารถสร้างสี่เหลี่ยม, ใส่เงาที่สวยงาม, และบันทึกเอกสาร Word ได้ในไม่กี่บรรทัด.

ในบทเรียนนี้เราจะพาคุณผ่านทุกขั้นตอนที่ต้องการ: ตั้งแต่การเริ่มต้นเอกสารเปล่า, การกำหนดค่าเงา, จนถึงการบันทึกไฟล์ในที่สุด. เมื่อจบคุณจะรู้ **how to shadow shape** objects, วิธี **add shape shadow**, และวิธี **add rectangle shape** ไปยังเอกสาร Word ใด ๆ ที่คุณสร้าง. ไม่ต้องใช้เอกสารภายนอก—เพียงโค้ดที่สามารถรันได้.

## สิ่งที่ต้องเตรียม

- Java 8 หรือใหม่กว่า (API ทำงานกับ Java 11+ ด้วย)  
- ไลบรารี Aspose.Words for Java (เวอร์ชัน 23.9 หรือใหม่กว่า)  
- IDE เช่น IntelliJ IDEA หรือ Eclipse—ใช้ได้ทุกตัว  
- ความคุ้นเคยพื้นฐานกับไวยากรณ์ Java  

> **เคล็ดลับมืออาชีพ:** หากคุณใช้ Maven, เพิ่ม dependency ของ Aspose.Words ลงใน `pom.xml` ของคุณและให้ IDE จัดการส่วนที่เหลือ.

---

## ขั้นตอนที่ 1: เริ่มต้นเอกสารใหม่ – How to **create rectangle shape**  

สิ่งแรกที่ต้องทำคือคุณต้องมีผืนผ้าใบที่สะอาด. ใน Aspose.Words ผืนผ้าใบนั้นคืออ็อบเจ็กต์ `Document`.

```java
import com.aspose.words.*;

public class ShadowShapeExample {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document
        Document document = new Document();
```

`Document` class แสดงถึงไฟล์ .docx ทั้งหมด. คิดว่าเป็นสมุดบันทึกที่คุณจะ **add rectangle shape** และเงาของมันในภายหลัง.

## ขั้นตอนที่ 2: สร้างสี่เหลี่ยม – **Add rectangle shape**  

ตอนนี้เราจะสร้างสี่เหลี่ยมจริง ๆ. เราจะกำหนดขนาด, การจัดวาง, และสีเติม.

```java
        // Step 2: Create a rectangle shape and set its size and layout
        Shape rectangleShape = new Shape(document, ShapeType.RECTANGLE);
        rectangleShape.setWidth(200);
        rectangleShape.setHeight(100);
        rectangleShape.setWrapType(WrapType.INLINE);
        rectangleShape.setFillColor(java.awt.Color.LIGHT_GRAY);
```

ทำไมต้อง `INLINE` wrap? เพราะเราต้องการให้รูปร่างทำงานเหมือนย่อหน้า—เหมาะกับรายงานง่าย ๆ. คุณสามารถเปลี่ยนเป็น `TOPBOTTOM` หากต้องการให้ข้อความไหลรอบรูปร่างในภายหลัง.

## ขั้นตอนที่ 3: ใส่เงา – **How to shadow shape**  

สี่เหลี่ยมแบน ๆ ดูธรรมดา. การเพิ่มเงาจะให้ความลึกและทำให้เอกสารดูเรียบหรูขึ้น. นี่คือจุดที่เราตอบ “**how to shadow shape**” อย่างจริงจัง.

```java
        // Step 3: Configure the shape's shadow appearance
        rectangleShape.getShadowFormat().setVisible(true);
        rectangleShape.getShadowFormat().setColor(java.awt.Color.DARK_GRAY);
        rectangleShape.getShadowFormat().setBlurRadius(5.0);
        rectangleShape.getShadowFormat().setOffsetX(4.0);
        rectangleShape.getShadowFormat().setOffsetY(4.0);
        rectangleShape.getShadowFormat().setTransparency(0.3);
```

แต่ละคุณสมบัติมีหน้าที่เฉพาะ:

- `setVisible(true)` เปิดใช้งานเงา.  
- `setColor` เลือกสีเทาเข้มเพื่อเอฟเฟกต์อ่อนโยน.  
- `setBlurRadius` ควบคุมความนุ่มของขอบ.  
- `setOffsetX/Y` ย้ายเงาไปทางขวาและลง, จำลองแหล่งแสง.  
- `setTransparency` ทำให้เงาโปร่งแสงเล็กน้อย, เพื่อให้รูปร่างยังเป็นจุดเด่น.

> **หมายเหตุ:** หากคุณต้องการเงาสี, เพียงส่ง `java.awt.Color` ที่ต่างออกไปให้กับ `setColor`.

## ขั้นตอนที่ 4: แทรกรูปร่างลงในเอกสาร  

เมื่อสี่เหลี่ยมและเงาพร้อมแล้ว, เราจะใส่ลงในส่วนแรกของเอกสาร.

```java
        // Step 4: Add the shape to the first section of the document
        document.getFirstSection().getBody().appendChild(rectangleShape);
```

การเพิ่มลงใน body จะวางรูปร่างในตำแหน่งที่ย่อหน้าใหม่จะอยู่. หากคุณต้องการสี่เหลี่ยมที่ตำแหน่งเฉพาะ, สามารถใช้ `insertBefore` หรือจัดการคอลเลกชัน `Paragraph`.

## ขั้นตอนที่ 5: **Save Word document** – บันทึกงานของคุณ  

ขั้นตอนสุดท้ายคือการเขียนไฟล์ลงดิสก์. นี่คือช่วงเวลาที่คุณจริง ๆ **save Word document**.

```java
        // Step 5: Save the document with the shadowed shape
        document.save("YOUR_DIRECTORY/ShadowShape.docx");
    }
}
```

แทนที่ `YOUR_DIRECTORY` ด้วยพาธแบบ absolute หรือ relative บนเครื่องของคุณ. หลังจากรันโปรแกรม, เปิด `ShadowShape.docx` ใน Microsoft Word—คุณควรเห็นสี่เหลี่ยมสีเทาอ่อนพร้อมเงาสีเข้มอ่อน.

![แผนภาพแสดงสี่เหลี่ยมพร้อมเงาที่สร้างด้วย Aspose.Words](https://example.com/rectangle-shadow.png "สร้างสี่เหลี่ยมพร้อมเงา")

---

## คำถามทั่วไปและกรณีขอบ

### ถ้าต้องการหลายสี่เหลี่ยม?

เพียงทำซ้ำ **Step 2** และ **Step 3** ในลูป, ปรับ `setWidth`, `setHeight`, หรือ `setFillColor` ในแต่ละรอบ. อย่าลืมตั้งชื่อตัวแปรที่ไม่ซ้ำกันหรือเก็บไว้ในรายการ.

### สามารถส่งออกเป็น PDF แทน DOCX ได้หรือไม่?

ได้เลย. หลังจากเพิ่มรูปร่าง, เรียก `document.save("output.pdf")`. Aspose.Words จะจัดการการแปลง, รักษาเงาไว้.

### เกี่ยวกับเวอร์ชัน Word เก่าล่ะ?

ใช้ overload `document.save("file.doc", SaveFormat.DOC)`. API จะลดระดับฟีเจอร์โดยอัตโนมัติ, แต่ควรทราบว่าบางสไตล์เงาอาจดูแตกต่างเล็กน้อยในฟอร์แมตเก่า.

### จะเปลี่ยนทิศทางของเงาอย่างไร?

ปรับ `setOffsetX` และ `setOffsetY`. ค่า X บวกจะย้ายเงาไปทางขวา, ค่า X ลบจะไปซ้าย. ค่า Y บวกจะย้ายลง, ค่า Y ลบจะย้ายขึ้น. ทดลองเปลี่ยนตัวเลขเหล่านี้เพื่อจำลองแหล่งแสงจากมุมใดก็ได้.

## เคล็ดลับการทำงานกับรูปร่าง  

- **Group shapes**: หากต้องการป้ายกำกับข้างสี่เหลี่ยม, สร้าง `GroupShape` แล้วเพิ่มทั้งสี่เหลี่ยมและ `TextBox`.  
- **Z‑order matters**: ใช้ `shape.moveToFront()` หรือ `shape.moveToBack()` เพื่อควบคุมว่ารูปร่างใดอยู่บนสุด.  
- **Performance**: การเพิ่มรูปร่างหลายร้อยอาจช้า. จัดกลุ่มในส่วนเดียว, แล้วเรียก `document.updatePageLayout()` ครั้งเดียวที่ท้าย.

## สรุป  

เราได้อธิบายวิธี **create rectangle shape** ในเอกสาร Word ด้วย Java, วิธี **add shape shadow**, และวิธี **save Word document** พร้อมผลลัพธ์. โค้ดที่สมบูรณ์และรันได้อยู่ในส่วนโค้ดข้างบน, และตอนนี้คุณเข้าใจ “เหตุผล” ของแต่ละคุณสมบัติ—เพื่อให้คุณปรับสี, ความเบลอ, และการออฟเซ็ตให้เหมาะกับการออกแบบใด ๆ.

พร้อมสำหรับความท้าทายต่อไปหรือยัง? ลองผสานสี่เหลี่ยมกับแผนภูมิ, หรือส่งออกไฟล์เป็น PDF แล้วดูว่าเงาแสดงอย่างไร. คุณอาจสำรวจการ **add rectangle shape** ภายในตารางสำหรับการจัดรูปแบบรายงานที่สวยงาม.

ขอให้เขียนโค้ดอย่างสนุกสนาน, และเอกสารของคุณดูคมชัดเสมอเหมือนโค้ดของคุณ!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}