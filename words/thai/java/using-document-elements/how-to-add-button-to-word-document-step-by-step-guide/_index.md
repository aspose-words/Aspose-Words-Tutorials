---
category: general
date: 2026-07-20
description: วิธีเพิ่มปุ่มในเอกสาร Word ด้วย Aspose.Words เรียนรู้การแทรกปุ่ม Forms2OleControl
  ด้วย DocumentBuilder ภายในไม่กี่นาที
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to add button to word document
- Forms2OleControl
- DocumentBuilder
- insertForms2OleControl
- Word automation
language: th
lastmod: 2026-07-20
og_description: วิธีเพิ่มปุ่มลงในเอกสาร Word ด้วย Aspose.Words. ติดตามคู่มือเชิงปฏิบัตินี้เพื่อฝัง
  Forms2OleControl CommandButton ด้วย Java.
og_image_alt: Screenshot of a Word document with a clickable button added via Aspose.Words
  (how to add button to word document)
og_title: วิธีเพิ่มปุ่มในเอกสาร Word – บทเรียน Aspose.Words อย่างครบถ้วน
schemas:
- author: Aspose
  dateModified: '2026-07-20'
  description: How to add button to Word document using Aspose.Words. Learn to insert
    a Forms2OleControl button with DocumentBuilder in minutes.
  headline: How to Add Button to Word Document – Step‑by‑Step Guide
  type: TechArticle
- description: How to add button to Word document using Aspose.Words. Learn to insert
    a Forms2OleControl button with DocumentBuilder in minutes.
  name: How to Add Button to Word Document – Step‑by‑Step Guide
  steps:
  - name: '`Forms2OleControlType.COMMANDBUTTON` – tells Word we want a button.'
    text: '`Forms2OleControlType.COMMANDBUTTON` – tells Word we want a button.'
  - name: '`100` – width in points (≈1.39 inches).'
    text: '`100` – width in points (≈1.39 inches).'
  - name: '`30` – height in points (≈0.42 inches).'
    text: '`30` – height in points (≈0.42 inches).'
  type: HowTo
tags:
- Aspose.Words
- Java
- Office Automation
title: วิธีเพิ่มปุ่มในเอกสาร Word – คู่มือแบบขั้นตอนต่อขั้นตอน
url: /th/java/using-document-elements/how-to-add-button-to-word-document-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# วิธีเพิ่มปุ่มในเอกสาร Word – คำแนะนำเต็มของ Aspose.Words

เคยสงสัย **วิธีเพิ่มปุ่มในเอกสาร Word** โดยไม่ต้องเปิด UI และคลิกหลายครั้งหรือไม่? คุณไม่ได้เป็นคนเดียว นักพัฒนาจำนวนมากต้องการฝังคอนโทรลแบบโต้ตอบโดยโปรแกรม—เช่นปุ่ม “Submit” ในเทมเพลตที่ผู้ใช้ปลายทางจะกรอกในภายหลัง ข่าวดีคือ? ด้วย Aspose.Words for Java คุณทำได้ในไม่กี่บรรทัด

ในบทแนะนำนี้เราจะเดินผ่านขั้นตอนที่แม่นยำเพื่อแทรก `Forms2OleControl` ชนิด **CommandButton** โดยใช้ `DocumentBuilder` เมื่อเสร็จคุณจะได้ไฟล์ `.docx` ที่พร้อมใช้งานซึ่งแสดงปุ่มที่คลิกได้ที่มีข้อความ “Click Me” ไม่มีความลับ เพียงโค้ดที่ชัดเจนและเหตุผลเบื้องหลังแต่ละบรรทัด

## สิ่งที่คุณจะได้เรียนรู้

- วิธีสร้างเอกสาร Word ใหม่ตั้งแต่ต้น
- วิธีใช้ **DocumentBuilder** เพื่อวาง **Forms2OleControl**
- เหตุผลที่คุณควรตั้งค่าคำบรรยายของปุ่มและขนาดตามที่เราแนะนำ
- วิธีบันทึกและตรวจสอบผลลัพธ์
- ข้อผิดพลาดทั่วไป (เช่น ไลบรารีหาย, ชนิดคอนโทรลที่ไม่รองรับ) และวิธีหลีกเลี่ยง

**Prerequisites** – คุณต้องมี Java 8+ (หรือใหม่กว่า) และไลบรารี Aspose.Words for Java (เวอร์ชัน 23.12 หรือใหม่กว่า) IDE อย่าง IntelliJ IDEA หรือ Eclipse จะทำให้การทำงานราบรื่นขึ้น แต่ใด ๆ ที่เป็นโปรแกรมแก้ไขข้อความก็ใช้ได้

---

## Step 1: Set Up Your Project and Import Dependencies

ก่อนที่โค้ดใดจะทำงาน Maven (หรือ Gradle) ต้องรู้ว่าจะดึง Aspose.Words จากที่ไหน เพิ่มส่วนนี้ลงใน `pom.xml` ของคุณ:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.12</version>
</dependency>
```

หากคุณชอบ Gradle ให้ใช้แบบเทียบเท่า:

```gradle
implementation 'com.aspose:aspose-words:23.12'
```

> **Pro tip:** ใช้รุ่นล่าสุด; รุ่นเก่าอาจไม่มี API `Forms2OleControl`

เมื่อการอ้างอิงสำเร็จ คุณก็พร้อมเขียนโค้ด Java แล้ว

## Step 2: Create a New Document and Obtain a DocumentBuilder

คลาส `Document` แทนส่วนทั้งหมดของแพ็กเกจ `.docx` ส่วน `DocumentBuilder` คือแปรงที่คุณใช้วาดเนื้อหาไปบนมัน คิดว่า `DocumentBuilder` เป็น “เคอร์เซอร์” ที่รู้ว่าจะวางองค์ประกอบต่อไปที่ไหน

```java
import com.aspose.words.*;

public class AddButtonExample {
    public static void main(String[] args) throws Exception {
        // Step 2: Create a new blank document
        Document doc = new Document();

        // Obtain a DocumentBuilder tied to the document
        DocumentBuilder builder = new DocumentBuilder(doc);
```

**Why this matters:** การสร้าง `Document` ใหม่ให้คุณมีผืนผ้าเปล่าสะอาด Builder จะชี้ไปที่ย่อหน้าแรกโดยอัตโนมัติ ดังนั้นคุณไม่ต้องจัดการส่วนหรือหน้าเอง

## Step 3: Insert a Forms2OleControl of Type CommandButton

ตอนนี้มาถึงจุดเด่นของการแสดง: `insertForms2OleControl` เมธอดนี้สร้างคอนโทรล OLE (Object Linking and Embedding) ที่ Word ถือเป็นองค์ประกอบฟอร์ม เราจะส่งอาร์กิวเมนต์สามค่า:

1. `Forms2OleControlType.COMMANDBUTTON` – บอก Word ว่าเราต้องการปุ่ม
2. `100` – ความกว้างเป็นพอยต์ (≈1.39 นิ้ว)
3. `30` – ความสูงเป็นพอยต์ (≈0.42 นิ้ว)

```java
        // Step 3: Insert a CommandButton with specific dimensions
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON, 100, 30);
```

**How it works:** ภายใต้พื้นฐาน Aspose.Words จะสร้าง XML ที่เหมาะสมในส่วน `word/document.xml` พร้อมอ้างอิงถึงอ็อบเจ็กต์ OLE ขนาดที่คุณระบุจะถูกเคลียร์โดยเอนจินการจัดวางของ Word ดังนั้นปุ่มจะแสดงตรงตำแหน่งที่เคอร์เซอร์ของ Builder อยู่

## Step 4: Set the Caption (Text) on the Button

ปุ่มที่ไม่มีป้ายกำกับจะทำให้สับสน—ลองนึกถึงปุ่มลิฟต์ที่เงียบ `setCaption` เมธอดนี้ตั้งข้อความที่มองเห็นได้:

```java
        // Step 4: Define the button's label
        commandButton.setCaption("Click Me");
```

คุณสามารถเปลี่ยนป้ายกำกับเป็นอะไรก็ได้: “Submit”, “Approve” หรือแม้แต่สตริงที่แปลเป็นภาษาอื่น ป้ายกำกับจะถูกเก็บในคุณสมบัติของอ็อบเจ็กต์ OLE ดังนั้น Word จะเรนเดอร์มันตามธรรมชาติ

## Step 5: Save the Document and Verify the Result

สุดท้ายให้เขียนไฟล์ลงดิสก์ เลือกโฟลเดอร์ที่คุณมีสิทธิ์เขียน มิฉะนั้นคุณจะเจอ `IOException`

```java
        // Step 5: Persist the document
        String outputPath = "output/button-demo.docx";
        doc.save(outputPath);
        System.out.println("Document saved to: " + outputPath);
    }
}
```

เปิด `button-demo.docx` ใน Microsoft Word คุณควรเห็นปุ่มที่มีข้อความ **Click Me** อยู่ที่ด้านบนของเอกสาร การคลิกมันใน Word จะเรียกพฤติกรรม OLE เริ่มต้น (โดยปกติจะแสดงข้อความตัวอย่าง เว้นแต่คุณจะผูกมาโคร)

## Common Edge Cases and How to Handle Them

| สถานการณ์ | สาเหตุ | วิธีแก้ |
|-----------|--------|----------|
| **Missing `Forms2OleControl` type** | เวอร์ชันเก่าของ Aspose.Words ไม่ได้เปิดเผย enum นี้ | อัปเกรดเป็นเวอร์ชัน 23.12 ขึ้นไปหรือใหม่กว่า |
| **Button appears as a picture** | การตั้งค่าความปลอดภัยของ Word ปิดกั้น OLE control | เปิดใช้งาน “Trust access to the VBA project object model” ใน Trust Center หรือใช้ไฟล์ `.docm` ที่เปิดใช้งานมาโคร |
| **Incorrect size** | สับสนระหว่างพอยต์กับพิกเซล | จำไว้ว่า 1 พอยต์ = 1/72 นิ้ว ปรับตัวเลขให้เหมาะสม |
| **Saving throws `FileNotFoundException`** | เส้นทางไม่มีอยู่ | ตรวจสอบให้แน่ใจว่าไดเรกทอรี (`output/`) ถูกสร้างก่อน `doc.save`. ใช้ `new File("output").mkdirs();` |

---

## Extending the Example: Adding Multiple Buttons or Other Controls

หากคุณต้องการปุ่มมากกว่าหนึ่งปุ่ม เพียงย้ายเคอร์เซอร์ของ Builder ด้วย `builder.moveTo` หรือ `builder.writeln()` ก่อนเรียก `insertForms2OleControl` อีกครั้ง

```java
        // Add a second button below the first
        builder.writeln(); // moves to a new paragraph
        Forms2OleControl secondButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON, 120, 35);
        secondButton.setCaption("Submit");
```

คุณยังสามารถแทรก **CheckBox**, **ComboBox**, หรือ **ListBox** ได้โดยเปลี่ยน `Forms2OleControlType.COMMANDBUTTON` เป็นค่า enum ที่เหมาะสม (`CHECKBOX`, `COMBOBOX` เป็นต้น) พารามิเตอร์ความกว้าง/ความสูงยังคงใช้ได้เช่นเดิม

## How This Fits Into Larger Word Automation Workflows

- **Template Generation:** สร้างเทมเพลตสัญญาที่รวมปุ่ม “Approve” เพื่อการอนุมัติต่อไป
- **Reporting:** สร้างรายงานประจำวันพร้อมปุ่ม “Refresh Data” ที่เรียกใช้มาโคร
- **Form Distribution:** ส่งแบบสอบถามที่มีคอนโทรลแบบโต้ตอบที่กรอกล่วงหน้า

ทุกสถานการณ์เหล่านี้ได้รับประโยชน์จากแนวทาง **Word automation** ที่เราแสดง โดยการฝังคอนโทรลด้วยโปรแกรม คุณจะลดการแก้ไขด้วยมือและลดข้อผิดพลาดของมนุษย์

---

## Full Source Code (Copy‑Paste Ready)

```java
import com.aspose.words.*;

public class AddButtonExample {
    public static void main(String[] args) throws Exception {
        // Create a new blank document
        Document doc = new Document();

        // Obtain a DocumentBuilder for the document
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a CommandButton (width: 100pt, height: 30pt)
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON, 100, 30);

        // Set the button caption
        commandButton.setCaption("Click Me");

        // Optionally add a second button
        builder.writeln(); // new paragraph
        Forms2OleControl secondButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON, 120, 35);
        secondButton.setCaption("Submit");

        // Save the document
        String outputPath = "output/button-demo.docx";
        new java.io.File("output").mkdirs(); // ensure directory exists
        doc.save(outputPath);
        System.out.println("Document saved to: " + outputPath);
    }
}
```

**Expected output:** เมื่อคุณเปิด `output/button-demo.docx` ใน Microsoft Word คุณจะเห็นสองปุ่ม—“Click Me” และ “Submit”—เรียงกันในแนวตั้งที่ด้านบนของไฟล์

---

## Conclusion

เราได้ตอบ **วิธีเพิ่มปุ่มในเอกสาร Word** ด้วย Aspose.Words for Java อย่างเป็นขั้นตอน ตั้งแต่เริ่มจาก `Document` เปล่า เราใช้ **DocumentBuilder** เพื่อแทรก `Forms2OleControl` ชนิด **CommandButton** ตั้งป้ายกำกับที่เป็นมิตรและบันทึกผลลัพธ์ วิธีนี้สามารถขยายเป็นหลายคอนโทรลและรวมเข้ากับกระบวนการ **Word automation** ที่กว้างขึ้นได้อย่างราบรื่น

พร้อมรับความท้าทายต่อไปหรือยัง? ลองเปลี่ยนปุ่มเป็น **CheckBox** หรือผูกมาโครให้ทำงานเมื่อผู้ใช้คลิกปุ่มในไฟล์ `.docm` แค่เปลี่ยน enum และปรับป้ายกำกับก็พอ

หากเจอปัญหาใด ๆ ตรวจสอบเวอร์ชันของไลบรารีและสิทธิ์ของโฟลเดอร์ปลายทาง อย่าลังเลที่จะคอมเมนต์ด้านล่างด้วยคำถามหรือแชร์กรณีการใช้งานของคุณเอง โค้ดดิ้งอย่างสนุกสนาน!

## What Should You Learn Next?

บทแนะนำต่อไปนี้ครอบคลุมหัวข้อที่เกี่ยวข้องอย่างใกล้ชิดและต่อยอดจากเทคนิคที่แสดงในคู่มือนี้ แต่ละแหล่งรวมตัวอย่างโค้ดทำงานเต็มรูปแบบพร้อมคำอธิบายขั้นตอนเพื่อช่วยคุณเชี่ยวชาญฟีเจอร์ API เพิ่มเติมและสำรวจแนวทางการทำงานทางเลือกในโปรเจกต์ของคุณ

- [วิธีสร้างฟิลด์ฟอร์มและเพิ่มเนื้อหาโดยใช้ DocumentBuilder ใน Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [แทรกรูปภาพแบบ Inline ในเอกสาร Word โดยใช้ Aspose.Words](/words/english/net/add-content-using-document-builder/insert-inline-image/)
- [สร้าง Group Shape ในเอกสาร Word ด้วย Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}