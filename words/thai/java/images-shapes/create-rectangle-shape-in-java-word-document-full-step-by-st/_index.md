---
category: general
date: 2026-05-26
description: สร้างรูปสี่เหลี่ยมในเอกสาร Word ด้วย Java และใช้เอฟเฟกต์เงา เรียนรู้วิธีเพิ่มเงาให้รูปทรง
  ตั้งค่าระยะเงา และบันทึกไฟล์
draft: false
keywords:
- create rectangle shape
- apply shadow effect
- create word document java
- add shape shadow
- set shadow distance
language: th
og_description: สร้างรูปสี่เหลี่ยมในเอกสาร Word ด้วย Java, ใช้เอฟเฟกต์เงา, เพิ่มเงารูป,
  และตั้งค่าระยะห่างของเงาด้วย Aspose.Words.
og_title: สร้างรูปสี่เหลี่ยมในเอกสาร Word ด้วย Java – คู่มือฉบับสมบูรณ์
schemas:
- author: Aspose
  dateModified: '2026-05-26'
  description: Create rectangle shape in a Java Word document and apply shadow effect.
    Learn how to add shape shadow, set shadow distance, and save the file.
  headline: Create Rectangle Shape in Java Word Document – Full Step‑by‑Step Guide
  type: TechArticle
- description: Create rectangle shape in a Java Word document and apply shadow effect.
    Learn how to add shape shadow, set shadow distance, and save the file.
  name: Create Rectangle Shape in Java Word Document – Full Step‑by‑Step Guide
  steps:
  - name: “Can I use a different shape?”
    text: Absolutely. Replace `ShapeType.RECTANGLE` with `ShapeType.OVAL`, `ShapeType.LINE`,
      or any other supported enum. The rest of the shadow code stays the same.
  - name: “What if I need multiple shadows?”
    text: Aspose.Words only supports a single shadow per shape. To simulate multiple
      shadows, duplicate the shape, offset each copy, and adjust the transparency.
  - name: “Is the shadow visible in LibreOffice?”
    text: Yes—Aspose.Words writes standard OOXML, which LibreOffice interprets correctly.
      The shadow may look slightly different due to rendering engines, but the effect
      persists.
  - name: “How do I change the shadow color to match my brand?”
    text: Just swap `java.awt.Color.GRAY` with any `java.awt.Color` you prefer, such
      as `new java.awt.Color(0, 120, 215)` for a corporate blue.
  type: HowTo
tags:
- Java
- Aspose.Words
- Word Automation
title: สร้างรูปสี่เหลี่ยมในเอกสาร Word ด้วย Java – คู่มือขั้นตอนเต็ม
url: /th/java/images-shapes/create-rectangle-shape-in-java-word-document-full-step-by-st/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# สร้างรูปสี่เหลี่ยมในเอกสาร Word ด้วย Java – คู่มือเต็มขั้นตอน

เคยต้องการ **create rectangle shape** ในเอกสาร Word ด้วย Java แต่ไม่แน่ใจว่าจะเริ่มอย่างไรหรือไม่? คุณไม่ได้อยู่คนเดียว—นักพัฒนาหลายคนเจออุปสรรคนี้เมื่อสร้างรายงานหรือใบแจ้งหนี้โดยอัตโนมัติ ในบทเรียนนี้เราจะอธิบายขั้นตอนการ **create rectangle shape**, การเพิ่มเงาที่ดูเรียบหรู, และการปรับระยะห่างของเงาให้ผลลัพธ์ดูเป็นมืออาชีพ

เราจะใช้ Aspose.Words for Java ซึ่งเป็นไลบรารีที่แข็งแรงที่ช่วยให้คุณจัดการไฟล์ Word ได้โดยไม่ต้องติดตั้ง Microsoft Office เมื่อคุณอ่านจบคู่มือนี้คุณจะสามารถสร้างโปรเจกต์ **create word document java** ที่ **add shape shadow**, **apply shadow effect**, และ **set shadow distance** ด้วยเพียงไม่กี่บรรทัดของโค้ด

---

## สิ่งที่คุณจะสร้าง

- ไฟล์ `.docx` ใหม่ที่มีสี่เหลี่ยมสีฟ้าไซอาน
- เงาตกที่ดูสมจริง มีการเบลอ มีมุม และมีความโปร่งแสงบางส่วน
- ควบคุมระยะห่างของเงาจากรูปได้เต็มที่
- คลาส Java ที่พร้อมรันที่คุณสามารถใส่ลงในโปรเจกต์ Maven หรือ Gradle ใดก็ได้

ไม่มีเครื่องมือภายนอก ไม่มีขั้นตอน UI แบบมือ—เพียงโค้ดเท่านั้น

---

## ข้อกำหนดเบื้องต้น

- Java 8 หรือใหม่กว่า (โค้ดทำงานบน Java 11, Java 17 เป็นต้น)
- ไลบรารี Aspose.Words for Java (สามารถดาวน์โหลดได้จาก Maven Central)
- IDE หรือโปรแกรมแก้ไขข้อความที่คุณชอบ (IntelliJ IDEA, Eclipse, VS Code…)
- ความคุ้นเคยพื้นฐานกับไวยากรณ์ Java

หากคุณยังไม่เคยเพิ่ม dependency ของ Maven มาก่อน นี่คือตัวอย่างสั้น ๆ:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.10</version> <!-- Use the latest stable version -->
</dependency>
```

ต่อไป เรามาเริ่มกันเลย

---

## ขั้นตอนที่ 1: สร้างรูปสี่เหลี่ยมในเอกสาร Word

สิ่งแรกที่เราต้องการคือเอกสารเปล่าและ `DocumentBuilder` คิดว่า builder เป็นเหมือนปากกาที่เขียนลงในเอกสาร เมื่อเรามีแล้ว เราสามารถ **create rectangle shape** ด้วยการเรียกเมธอดเดียว

```java
import com.aspose.words.*;

public class ShadowEffectDemo {
    public static void main(String[] args) throws Exception {
        // Initialize a new empty document.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a rectangle shape of 150x80 points.
        Shape rectangleShape = builder.insertShape(ShapeType.RECTANGLE, 150, 80);
        // Make the shape visible by filling it with cyan.
        rectangleShape.setFillColor(java.awt.Color.CYAN);
```

> **ทำไมเรื่องนี้สำคัญ:** เมธอด `insertShape` ไม่เพียงสร้างรูปทรงเรขาคณิตเท่านั้น แต่ยังเพิ่มรูปลงในคอลเลกชันภายในของเอกสาร ทำให้คุณสามารถเริ่มจัดสไตล์ได้ทันที

---

## ขั้นตอนที่ 2: เพิ่มเอฟเฟกต์เงาให้กับรูป

เมื่อสี่เหลี่ยมอยู่บนหน้าแล้ว เราจะ **apply shadow effect** เงาช่วยเพิ่มความลึก ทำให้รูปดูเหมือนลอยขึ้นจากหน้า—การปรับ UI ที่ละเอียดอ่อนซึ่งสามารถเพิ่มความอ่านง่ายในรายงาน

```java
        // Retrieve the shadow format object.
        ShadowFormat shadowFormat = rectangleShape.getShadowFormat();

        // Enable the shadow and configure its appearance.
        shadowFormat.setVisible(true);          // Turn the shadow on.
        shadowFormat.setBlur(5.0);              // Soft blur radius.
        shadowFormat.setAngle(45.0);            // Direction of the shadow.
        shadowFormat.setColor(java.awt.Color.GRAY); // Shadow color.
        shadowFormat.setTransparency(0.3);     // 30% transparent.
```

> **เคล็ดลับ:** ค่าเบลอ `5.0` ดูเป็นธรรมชาติสำหรับเอกสารที่แสดงบนหน้าจอส่วนใหญ่ หากคุณพิมพ์อาจต้องการค่าต่ำกว่านี้เล็กน้อยเพื่อหลีกเลี่ยงลักษณะเบลอ

---

## ขั้นตอนที่ 3: ตั้งค่าระยะห่างของเงา – ปรับตำแหน่งอย่างละเอียด

เงาไม่ได้เกี่ยวกับการเบลอเท่านั้น; ยังต้องการการเลื่อนตำแหน่งที่เหมาะสม นี่คือจุดที่เราจะ **set shadow distance** ระยะ `7.0` จุดให้การเลื่อนที่พอเหมาะ สังเกตได้แต่ไม่เกินไป

```java
        // Define how far the shadow sits from the shape.
        shadowFormat.setDistance(7.0); // Distance in points.
```

> **ถ้าต้องการเลื่อนมากขึ้น?** เพิ่มค่าดังกล่าว; ลดค่าหากต้องการลุคที่กระชับ จำไว้ว่า ระยะห่างทำงานร่วมกับมุมเพื่อกำหนดตำแหน่งเงาอย่างถูกต้อง

---

## ขั้นตอนที่ 4: บันทึกเอกสาร – เก็บงานของคุณ

สุดท้าย เราจะเขียนเอกสารลงดิสก์ เปลี่ยนเส้นทางให้เป็นตำแหน่งที่คุณต้องการให้ไฟล์อยู่

```java
        // Save the document with the rectangle and its shadow.
        doc.save("YOUR_DIRECTORY/shadow.docx");
    }
}
```

การรันคลาสจะสร้างไฟล์ `shadow.docx` ซึ่งเมื่อเปิดใน Microsoft Word หรือ LibreOffice จะเห็นสี่เหลี่ยมสีไซอานพร้อมเงาสีเทานุ่มที่มีมุม 45° และเลื่อนออกไป 7 จุด

---

## ตัวอย่างทำงานเต็มรูปแบบ

ด้านล่างเป็นโค้ดที่พร้อมคัดลอก‑วางครบถ้วน รวมถึงการ import ทั้งหมด, คอมเมนต์, และการเรียก `save` สุดท้าย

```java
import com.aspose.words.*;

public class ShadowEffectDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document and a DocumentBuilder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Insert a rectangle shape of the desired size.
        Shape rectangleShape = builder.insertShape(ShapeType.RECTANGLE, 150, 80);
        // Step 3: Apply a fill color to make the shape visible.
        rectangleShape.setFillColor(java.awt.Color.CYAN);

        // Step 4: Configure the shape's shadow effect.
        ShadowFormat shadowFormat = rectangleShape.getShadowFormat();
        shadowFormat.setVisible(true);          // Enable the shadow.
        shadowFormat.setBlur(5.0);              // Set the blur radius.
        shadowFormat.setDistance(7.0);          // Define how far the shadow is from the shape.
        shadowFormat.setAngle(45.0);            // Set the direction of the shadow.
        shadowFormat.setColor(java.awt.Color.GRAY); // Choose the shadow color.
        shadowFormat.setTransparency(0.3);      // Make the shadow partially transparent.

        // Step 5: Save the document with the shaped shadow.
        doc.save("YOUR_DIRECTORY/shadow.docx");
    }
}
```

**ผลลัพธ์ที่คาดหวัง:** เปิด `shadow.docx` → คุณจะเห็นสี่เหลี่ยมสีไซอานอยู่กึ่งกลางหน้าแรก, ปล่อยเงาสีเทานุ่มที่เลื่อนเล็กน้อยไปด้านล่าง‑ขวา การเบลอและความโปร่งแสงของเงาทำให้ดูเหมือนแสงธรรมชาติ

---

## คำถามทั่วไป & กรณีขอบ

### “ฉันสามารถใช้รูปแบบอื่นได้หรือไม่?”

แน่นอน. แทนที่ `ShapeType.RECTANGLE` ด้วย `ShapeType.OVAL`, `ShapeType.LINE`, หรือ enum ที่รองรับอื่น ๆ ส่วนของโค้ดเงาจะคงเดิม

### “ถ้าต้องการหลายเงา?”

Aspose.Words รองรับเงาเพียงหนึ่งเงาต่อรูปเท่านั้น เพื่อจำลองหลายเงา ให้ทำสำเนารูป, เลื่อนตำแหน่งแต่ละสำเนา, และปรับความโปร่งแสง

### “เงาแสดงผลใน LibreOffice หรือไม่?”

ใช่—Aspose.Words เขียนเป็น OOXML มาตรฐาน ซึ่ง LibreOffice สามารถตีความได้อย่างถูกต้อง เงาอาจดูแตกต่างเล็กน้อยเนื่องจากเครื่องยนต์การเรนเดอร์ แต่เอฟเฟกต์ยังคงอยู่

### “ฉันจะเปลี่ยนสีเงาให้ตรงกับแบรนด์ของฉันได้อย่างไร?”

เพียงเปลี่ยน `java.awt.Color.GRAY` เป็น `java.awt.Color` ใดก็ได้ที่คุณต้องการ เช่น `new java.awt.Color(0, 120, 215)` สำหรับสีน้ำเงินขององค์กร

---

## ภาพประกอบ

![สร้างรูปสี่เหลี่ยมในเอกสาร Word ด้วย Java](https://example.com/images/rectangle-shadow.png)

*ข้อความแทนภาพ:* **create rectangle shape** แสดงภาพสี่เหลี่ยมสีไซอานพร้อมเงาตกสีเทาในเอกสาร Word.

---

## สรุป & ขั้นตอนต่อไป

เราได้อธิบายวิธี **create rectangle shape**, **apply shadow effect**, **add shape shadow**, และ **set shadow distance** ด้วย Aspose.Words for Java โค้ดเป็นอิสระ สามารถทำงานบน JDK สมัยใหม่ใดก็ได้ และสร้างไฟล์ `.docx` ที่เรียบหรูพร้อมสำหรับการแจกจ่าย

ต้องการทำต่อ? ลอง:

- เพิ่มข้อความภายในสี่เหลี่ยมด้วย `builder.moveTo(rectangleShape.getAbsolutePosition())`.
- สร้างตารางของรูปเพื่อสร้างแผนภาพ.
- ส่งออกเอกสารเป็น PDF (`doc.save("output.pdf", SaveFormat.PDF);`).

แต่ละข้อเหล่านี้อิงจากพื้นฐานเดียวกันที่เราได้สำรวจไว้ ทำให้คุณรู้สึกสบายใจในการขยายตัวอย่าง

---

## ความคิดสุดท้าย

การเชี่ยวชาญงาน **create word document java** เช่น การสร้างรูปและการใส่เงา จะให้คุณได้เปรียบอย่างมากเมื่อทำอัตโนมัติรายงาน, สัญญา, หรือสื่อการตลาด วิธีการที่แสดงในนี้เป็นระเบียบ, ดูแลรักษาได้ง่าย, และ—ที่สำคัญที่สุด—ปรับแต่งได้ง่ายสำหรับสไตล์ภาพใด ๆ ที่คุณต้องการ

ลองใช้โค้ดนี้, ปรับค่าเบลอ, มุม, และระยะห่าง, แล้วดูเอกสารของคุณเปลี่ยนจากธรรมดาเป็นเรียบหรู หากคุณเจอปัญหาใด ๆ ฝากคอมเมนต์ด้านล่าง; ฉันยินดีช่วยเหลือ

ขอให้เขียนโค้ดอย่างสนุก!

---

## บทเรียนที่เกี่ยวข้อง

- [สร้างเอกสาร Word ด้วย Java – เพิ่มรูปสี่เหลี่ยมพร้อมเอฟเฟกต์เงา](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [วิธีสร้างฟิลด์ฟอร์มและเพิ่มเนื้อหาโดยใช้ DocumentBuilder ใน Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [สร้าง PDF จาก Word พร้อมการสร้างบาร์โค้ด – Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-barcode-generation/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}