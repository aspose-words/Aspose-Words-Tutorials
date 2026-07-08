---
category: general
date: 2026-07-03
description: สร้างรูปสี่เหลี่ยมใน Java และเรียนรู้วิธีเพิ่มเงาให้กับรูปทรง, ใช้เอฟเฟกต์เงา,
  ตั้งค่าความโปร่งใสของรูปทรง, และสร้างเอกสารเปล่าอย่างรวดเร็ว.
draft: false
keywords:
- create rectangle shape
- add shadow to shape
- apply shadow effect
- set shape transparency
- create blank document
language: th
og_description: สร้างรูปสี่เหลี่ยมใน Java พร้อมเงา ความโปร่งใส และเอกสารเปล่า. ทำตามคู่มือนี้เพื่อเชี่ยวชาญการจัดการรูปทรง.
og_title: สร้างรูปสี่เหลี่ยมผืนผ้าใน Java – บทเรียนการเขียนโปรแกรมเต็มรูปแบบ
schemas:
- author: Aspose
  dateModified: '2026-07-03'
  description: Create rectangle shape in Java and learn how to add shadow to shape,
    apply shadow effect, set shape transparency, and create blank document quickly.
  headline: Create rectangle shape in Java – Complete Step‑by‑Step Guide
  type: TechArticle
- description: Create rectangle shape in Java and learn how to add shadow to shape,
    apply shadow effect, set shape transparency, and create blank document quickly.
  name: Create rectangle shape in Java – Complete Step‑by‑Step Guide
  steps:
  - name: What if I want a different shadow color?
    text: 'Simply change the `setColor` call:'
  - name: Can I apply the same shadow to multiple shapes?
    text: 'Yes. Create one `ShadowEffect` instance, configure it, then reuse it:'
  - name: How do I change the shadow blur dynamically?
    text: Expose a UI slider that maps to `setBlurRadius`. Values between `2` and
      `12` are typical; larger numbers produce a “glow” rather than a crisp shadow.
  - name: What if I need the shape to float rather than be inline?
    text: 'Swap the wrap type:'
  type: HowTo
tags:
- Java
- Aspose.Words
- Document Automation
title: สร้างรูปสี่เหลี่ยมใน Java – คู่มือแบบครบถ้วนขั้นตอนต่อขั้นตอน
url: /th/java/images-shapes/create-rectangle-shape-in-java-complete-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# สร้างรูปสี่เหลี่ยมใน Java – คู่มือขั้นตอนเต็ม

เคยสงสัยไหมว่า **จะสร้างรูปสี่เหลี่ยม** ในเอกสาร Word ด้วย Java อย่างไร? คุณไม่ได้เป็นคนเดียว—นักพัฒนามักต้องการวิธีรวดเร็วในการเพิ่มกราฟิกเชิงเรขาคณิต แล้วใส่เงาเล็กน้อยเพื่อให้เลย์เอาต์ดูเรียบหรูยิ่งขึ้น ในบทเรียนนี้เราจะเดินผ่านกระบวนการทั้งหมด: ตั้งแต่การ **สร้างเอกสารเปล่า** ไปจนถึง **เพิ่มเงาให้รูป**, **ใช้เอฟเฟกต์เงา**, และแม้กระทั่ง **ตั้งค่าความโปร่งใสของรูป** เพื่อให้ได้ลุคระดับมืออาชีพ

โค้ดสแนปด้านล่างเป็นตัวอย่างที่ทำงานได้เต็มรูปแบบที่คุณสามารถคัดลอก‑วางลงในโปรเจกต์ของคุณได้ ไม่ต้องอ้างอิงเอกสารภายนอก—เพียงทำตามขั้นตอน เข้าใจ “ทำไม” แล้วคุณก็จะสร้างสี่เหลี่ยมที่มีเงาในไม่กี่วินาที

## สิ่งที่คุณจะได้เรียน

- วิธี **สร้างรูปสี่เหลี่ยม** อย่างโปรแกรมเมติกด้วย Aspose.Words for Java
- คำเรียกที่จำเป็นสำหรับ **เพิ่มเงาให้รูป** และกำหนดคุณสมบัติการแสดงผล
- วิธี **ใช้เอฟเฟกต์เงา** และปรับพารามิเตอร์เช่น offset, blur radius, และสี
- เทคนิค **ตั้งค่าความโปร่งใสของรูป** เพื่อให้ดูอ่อนโยนยิ่งขึ้น
- วิธี **สร้างเอกสารเปล่า**, แทรกรูป, และบันทึกผลลัพธ์

> **เคล็ดลับมืออาชีพ:** การกระทำทั้งหมดนี้ทำบนอินสแตนซ์ `Document` ตัวเดียว ซึ่งหมายความว่าคุณสามารถต่อเชื่อมขั้นตอนต่าง ๆ เข้าด้วยกันได้โดยไม่ต้องกังวลเรื่องการอ่าน‑เขียนไฟล์ระหว่างขั้นตอน

## ข้อกำหนดเบื้องต้น

ก่อนที่เราจะลงลึก โปรดตรวจสอบว่าคุณมี:

- Java 17 (หรือ JDK เวอร์ชันใหม่) ติดตั้งอยู่
- ไลบรารี Aspose.Words for Java เพิ่มเข้าในโปรเจกต์ (Maven coordinates: `com.aspose:aspose-words:23.12`)
- IDE สำหรับ Java หรือข้อความแก้ไขธรรมดา—ไม่ต้องมีอะไรพิเศษ เพียงที่สามารถคอมไพล์และรันได้

หากขาดส่วนใดส่วนหนึ่ง ให้ดาวน์โหลด JDK จาก Oracle แล้วดึง Aspose dependency ผ่าน Maven หรือ Gradle เมื่อพร้อมแล้ว คุณก็พร้อมเริ่มทำงาน

## ขั้นตอนที่ 1: **สร้างเอกสารเปล่า** – พื้นฐานสำหรับทุกอย่าง

สิ่งแรกที่ต้องมีคืออ็อบเจ็กต์ `Document` ว่างเปล่า คิดว่าเป็นแผ่นกระดาษใหม่; หากไม่มีคุณก็ไม่มีที่ใส่สี่เหลี่ยมของคุณ

```java
// Step 1: Create a new blank document
Document document = new Document();
```

ทำไมต้องเริ่มจากเอกสารเปล่า? เพราะทุกรูปอยู่ภายใน `Section` และ `Document` ที่สร้างใหม่มาพร้อมกับ `Section` เริ่มต้นที่มี `body` พร้อมรับโหนดต่าง ๆ การข้ามขั้นตอนนี้จะทำให้คุณต้องสร้าง `Section` ด้วยตนเองในภายหลัง ซึ่งเพิ่มความซับซ้อนโดยไม่จำเป็น

## ขั้นตอนที่ 2: **สร้างรูปสี่เหลี่ยม** และกำหนดขนาด

เมื่อเรามีแคนวาสแล้ว มา **สร้างรูปสี่เหลี่ยม** กัน `Shape` class รับอ้างอิงเอกสารและ `ShapeType` ที่นี่เราเลือก `RECTANGLE` และตั้งค่าความกว้าง/ความสูงเป็นพอยต์ (1 pt ≈ 1/72 inch)

```java
// Step 2: Insert a rectangle shape and define its size and layout
Shape rectangleShape = new Shape(document, ShapeType.RECTANGLE);
rectangleShape.setWidth(200);   // 200 pt ≈ 2.78 inches
rectangleShape.setHeight(100);  // 100 pt ≈ 1.39 inches
rectangleShape.setWrapType(WrapType.INLINE);
```

ทำไมต้องตั้งค่า `WrapType.INLINE`? การห่อแบบอินไลน์ทำให้รูปทำงานเหมือนอักขระในย่อหน้า ทำให้มันเคลื่อนที่พร้อมกับข้อความรอบข้าง หากต้องการพฤติกรรมลอย ให้เปลี่ยนเป็น `WrapType.SQUARE` หรือ `WrapType.TOP_BOTTOM`

## ขั้นตอนที่ 3: **ใช้เอฟเฟกต์เงา** – ให้สี่เหลี่ยมมีมิติ

สี่เหลี่ยมแบน ๆ ดู… แบน ๆ การเพิ่มเงาจะทำให้มันโดดเด่น เราจะ **ใช้เอฟเฟกต์เงา** โดยสร้างอินสแตนซ์ `ShadowEffect` แล้วปรับคุณสมบัติการแสดงผล

```java
// Step 3: Create a shadow effect and configure its visual properties
ShadowEffect shadowEffect = new ShadowEffect();
shadowEffect.setColor(Color.getGray(0.5));   // medium gray
shadowEffect.setOffsetX(5);                  // horizontal offset (points)
shadowEffect.setOffsetY(5);                  // vertical offset (points)
shadowEffect.setBlurRadius(8);               // softness of the shadow
shadowEffect.setTransparency(0.3);           // 30 % transparent
```

มาดูรายละเอียดกัน:

- **Color** – `Color.getGray(0.5)` ให้สีเทา 50 % ซึ่งเป็นสีกลางที่ทำงานได้กับพื้นหลังส่วนใหญ่
- **OffsetX/Y** – ค่าบวกผลักเงาไปทางขวาและลง; ค่าลบจะย้ายไปซ้าย/ขึ้น
- **BlurRadius** – ค่ามากกว่าจะทำให้เงานุ่มและกระจายมากขึ้น
- **Transparency** – อยู่ในช่วง `0` (ทึบ) ถึง `1` (โปร่งใสเต็ม) ที่นี่เราเลือก `0.3` เพื่อให้เอฟเฟกต์อ่อนโยน

## ขั้นตอนที่ 4: **เพิ่มเงาให้รูป** – ผูกเอฟเฟกต์เข้ากับรูป

การสร้างเอฟเฟกต์อย่างเดียวไม่พอ; เราต้อง **เพิ่มเงาให้รูป** โดยกำหนดอ็อบเจ็กต์ `ShadowEffect` ให้กับสี่เหลี่ยม

```java
// Step 4: Apply the shadow effect to the rectangle shape
rectangleShape.setShadowEffect(shadowEffect);
```

เบื้องหลังการเรียกนี้จะอัปเดต markup ของ OpenXML (`<w:shdw>`) ที่ Word ใช้ในการเรนเดอร์เงา หากคุณเปิดไฟล์ `.docx` ที่บันทึกไว้ คุณจะเห็น `<w:effect>` ที่มีพารามิเตอร์ที่เราตั้งไว้

## ขั้นตอนที่ 5: **ตั้งค่าความโปร่งใสของรูป** – ไม่บังคับแต่มักเป็นประโยชน์

บางครั้งคุณอาจต้องการให้สี่เหลี่ยมเองกึ่ง‑โปร่งใส เพื่อให้ข้อความพื้นหลังมองเห็นได้ `Shape` class มีเมธอด `setFillColor` และ `setFillTransparency` ตัวอย่างสั้น ๆ ที่ทำให้สี่เหลี่ยมโปร่งใส 40 % มีดังนี้:

```java
// Optional: make the rectangle partially transparent
rectangleShape.setFillColor(Color.getWhite());
rectangleShape.setFillTransparency(0.4); // 40 % transparent
```

ทำไมต้องทำเช่นนี้? ลองนึกถึงลายน้ำหรือการเน้นที่ต้องให้เนื้อหาภายหลังยังอ่านได้ ปรับค่าความโปร่งใสให้เหมาะกับสไตล์การออกแบบของคุณ

## ขั้นตอนที่ 6: แทรกรูปลงในเอกสาร

เราสร้างสี่เหลี่ยม, ใส่เงา, และ (ถ้าต้องการ) ตั้งค่าความโปร่งใสแล้ว ขั้นตอนสุดท้ายคือ **เพิ่มรูปลงใน Section แรกของเอกสาร**

```java
// Step 5: Add the shape to the first section of the document
document.getFirstSection().getBody().appendChild(rectangleShape);
```

การต่อรูปเข้ากับ `body` จะวางไว้ที่ตอนท้ายของย่อหน้าแรก หากต้องการตำแหน่งเฉพาะ ให้ดึง `Paragraph` เป้าหมายและใช้ `insertBefore` หรือ `insertAfter`

## ขั้นตอนที่ 7: บันทึกเอกสาร – ดูผลลัพธ์

ทุกอย่างสรุปด้วยการเรียก `save` เพียงครั้งเดียว เลือกพาธที่เหมาะกับสภาพแวดล้อมของคุณ

```java
// Step 6: Save the document with the shadowed shape
document.save("YOUR_DIRECTORY/ShadowShape.docx");
```

เปิดไฟล์ `ShadowShape.docx` ที่ได้ใน Microsoft Word หรือ LibreOffice คุณจะเห็นสี่เหลี่ยมคมชัดพร้อมเงาเทาอ่อน ๆ และอาจมีความโปร่งใสตามขั้นตอนเสริมที่ทำไว้ การแสดงผลตรงกับพารามิเตอร์ที่กำหนดในโค้ด

---

![สร้างรูปสี่เหลี่ยมพร้อมเงาในเอกสาร Word](https://example.com/images/rectangle-shadow.png "สร้างรูปสี่เหลี่ยมพร้อมเงา")

*ข้อความแทนภาพ:* **สร้างรูปสี่เหลี่ยมพร้อมเงา** – การแสดงผลสุดท้ายของตัวอย่าง

## คำถามที่พบบ่อย & กรณีขอบเขตพิเศษ

### ถ้าต้องการสีเงาที่ต่างออกไป?

เพียงเปลี่ยนการเรียก `setColor`:

```java
shadowEffect.setColor(Color.getRed()); // bright red shadow
```

จำไว้ว่าเงาที่สีสดใสเกินไปอาจดูไม่เป็นมืออาชีพ; โทนสีอ่อนมักให้ผลลัพธ์ดีที่สุด

### สามารถใช้เงาเดียวกันกับหลายรูปได้หรือไม่?

ทำได้ สร้างอินสแตนซ์ `ShadowEffect` หนึ่งตัว ตั้งค่าแล้วนำไปใช้ซ้ำ:

```java
Shape circle = new Shape(document, ShapeType.OVAL);
circle.setShadowEffect(shadowEffect); // same effect as rectangle
```

แค่หลีกเลี่ยงการแก้ไข `ShadowEffect` หลังจากที่ได้ผูกกับรูปอื่น ๆ แล้ว เว้นแต่คุณต้องการอัปเดตทั้งหมดพร้อมกัน

### จะเปลี่ยนค่า blur ของเงาแบบไดนามิกได้อย่างไร?

สร้าง UI slider ที่แมปค่าไปยัง `setBlurRadius` ค่าโดยทั่วไปอยู่ระหว่าง `2` ถึง `12`; ค่ามากกว่าจะให้ลักษณะ “แสงสว่าง” มากกว่าเงาแบบคม

### ถ้าต้องการให้รูปลอยแทนการเป็นอินไลน์?

สลับประเภทการห่อ:

```java
rectangleShape.setWrapType(WrapType.SQUARE);
rectangleShape.setRelativeHorizontalPosition(RelativeHorizontalPosition.PAGE);
rectangleShape.setHorizontalAlignment(HorizontalAlignment.CENTER);
```

รูปแบบลอยให้อิสระในการจัดวางมากขึ้น แต่ต้องเขียนตรรกะการตำแหน่งเพิ่มเติม

## ตัวอย่างทำงานเต็มรูปแบบ

ด้านล่างเป็นโปรแกรมที่พร้อมคัดลอก‑วางครบทุกขั้นตอนที่อธิบายไว้ รันเป็นแอปพลิเคชัน Java ธรรมดา

```java
import com.aspose.words.*;

public class ShadowRectangleDemo {
    public static void main(String[] args) throws Exception {
        // 1. Create a blank document
        Document document = new Document();

        // 2. Build the rectangle shape
        Shape rectangleShape = new Shape(document, ShapeType.RECTANGLE);
        rectangleShape.setWidth(200);
        rectangleShape.setHeight(100);
        rectangleShape.setWrapType(WrapType.INLINE);

        // 3. Configure shadow effect
        ShadowEffect shadowEffect = new ShadowEffect();
        shadowEffect.setColor(Color.getGray(0.5));
        shadowEffect.setOffsetX(5);
        shadowEffect.setOffsetY(5);
        shadowEffect.setBlurRadius(8);
        shadowEffect.setTransparency(0.3);

        // 4. Apply shadow to the rectangle
        rectangleShape.setShadowEffect(shadowEffect);

        // 5. (Optional) Make rectangle semi‑transparent
        rectangleShape.setFillColor(Color.getWhite());
        rectangleShape.setFillTransparency(0.4);

        // 6. Insert shape into the document
        document.getFirstSection().getBody().appendChild(rectangleShape);

        // 7. Save the file
        document.save("ShadowShape.docx");
    }
}
```

**ผลลัพธ์ที่คาดหวัง:** เมื่อเปิด `ShadowShape.docx` คุณจะเห็นสี่เหลี่ยมสีขาว ขนาด 200 × 100 pt อยู่กึ่งกลางย่อหน้าแรก มีเงาเทากลางสีเทา offset 5 pt, blur radius 8, ความโปร่งใส 30 % สี่เหลี่ยมเองโปร่งใส 40 % ทำให้ข้อความพื้นหลังมองเห็นได้บ้าง

## สรุป

เราได้ **สร้างรูปสี่เหลี่ยม** ตั้งแต่ต้น, **เพิ่มเงาให้รูป**, **ใช้เอฟเฟกต์เงา**, และแม้กระทั่ง **ตั้งค่าความโปร่งใสของรูป** — ทั้งหมดนี้ทำบน **เอกสารเปล่า** เป็นฐาน วิธีการตรงไปตรงมา ใช้ API ของ Aspose.Words ที่เป็น fluent และสามารถต่อขยายเป็นวงกลม, ดาว, หรือรูปหลายเหลี่ยมที่กำหนดเองได้

ต่อไปคุณอยากทำอะไร? ลองเปลี่ยน `ShapeType.RECTANGLE` เป็น `ShapeType.OVAL` เพื่อสร้างวงกลมที่มีเงา หรือทดลองเติมสีไล่ระดับ (gradient) สำหรับรูปแบบใหม่

## คุณควรเรียนต่ออะไรต่อไป?

บทเรียนต่อไปนี้ครอบคลุมหัวข้อที่เกี่ยวข้องอย่างใกล้ชิดและต่อยอดจากเทคนิคที่แสดงในคู่มือนี้ แต่ละแหล่งรวมโค้ดทำงานเต็มรูปแบบพร้อมคำอธิบายขั้นตอนเพื่อช่วยให้คุณเชี่ยวชาญฟีเจอร์ API เพิ่มเติมและสำรวจแนวทางการทำงานอื่น ๆ ในโปรเจกต์ของคุณ

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Create Blank Word Document with Shadowed Rectangle Shape – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}