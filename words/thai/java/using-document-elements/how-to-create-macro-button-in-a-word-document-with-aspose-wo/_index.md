---
category: general
date: 2026-11-22
description: สร้างปุ่มแมโครในเอกสาร Word ด้วย Java เรียนรู้วิธีแทรกปุ่มคำสั่ง ตั้งข้อความปุ่ม
  และเชื่อมโยงแมโครกับปุ่มเพื่อสร้างเอกสารแบบโต้ตอบ.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create macro button
- insert command button
- set button text
- link macro to button
- add interactive button
language: th
lastmod: 2026-11-22
og_description: สร้างปุ่มแมโครในเอกสาร Word ด้วย Java บทเรียนนี้แสดงวิธีแทรกปุ่มคำสั่ง
  ตั้งค่าข้อความปุ่ม และเชื่อมโยงแมโครกับปุ่มเพื่อความโต้ตอบเต็มรูปแบบ
og_image_alt: Screenshot of a Word document showing a macro button created with Java
  code
og_title: สร้างปุ่มแมโครในเอกสาร Word ด้วย Java – คู่มือแบบขั้นตอนต่อขั้นตอน
schemas:
- author: Aspose
  dateModified: '2026-11-22'
  description: Create macro button in a Word document using Java. Learn to insert
    command button, set button text, and link macro to button for interactive documents.
  headline: How to create macro button in a Word document with Aspose.Words for Java
  type: TechArticle
- description: Create macro button in a Word document using Java. Learn to insert
    command button, set button text, and link macro to button for interactive documents.
  name: How to create macro button in a Word document with Aspose.Words for Java
  steps:
  - name: Insert command button into the document
    text: '`DocumentBuilder.insertForms2OleControl` creates an OLE control of the
      specified type. The `Forms2OleControlType.COMMAND_BUTTON` constant tells Aspose.Words
      to generate a command button that can host a macro.'
  - name: Set button text (caption)
    text: The caption is the visible label on the button. Use `setCaption` to define
      what the user sees.
  - name: Link macro to button
    text: A macro is identified by its name, for example `MyMacro`. The `setOnClick`
      method stores this name in the button’s `OnClick` event handler.
  - name: Add interactive button to a Word document
    text: After configuring the OLE control, you may want to position it, resize it,
      or add surrounding text. The `DocumentBuilder` continues to operate on the document,
      so you can insert paragraphs before or after the button.
  - name: Expected output
    text: 'Running the program generates `MacroButtonDemo.docm`. Opening the file
      in Microsoft Word shows:'
  type: HowTo
tags:
- Aspose.Words
- Java
- OLE controls
- Automation
title: วิธีสร้างปุ่มแมโครในเอกสาร Word ด้วย Aspose.Words สำหรับ Java
url: /th/java/using-document-elements/how-to-create-macro-button-in-a-word-document-with-aspose-wo/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# วิธีสร้างปุ่มแมโครในไฟล์ Word ด้วย Aspose.Words for Java

หากคุณต้องการ **สร้างปุ่มแมโคร** ในไฟล์ Word คำแนะนำนี้จะพาคุณผ่านขั้นตอนที่จำเป็นอย่างละเอียด คุณจะได้เรียนรู้วิธี **แทรกปุ่มคำสั่ง**, **ตั้งข้อความบนปุ่ม**, และ **เชื่อมโยงแมโครกับปุ่ม** เพื่อทำให้เอกสารเป็นแบบโต้ตอบเต็มรูปแบบ

นักพัฒนามักฝังคอนโทรล OLE เพื่อเรียกใช้แมโคร VBA จากภายในเอกสาร บทเรียนนี้ครอบคลุมกระบวนการทำงานทั้งหมด ตั้งแต่การตั้งค่าโปรเจกต์จนถึงตัวอย่าง Java ที่ทำงานได้จริงซึ่งเพิ่ม **ปุ่มโต้ตอบ** ลงในไฟล์ .docx ไม่ต้องใช้สคริปต์ภายนอก—ทุกอย่างทำงานภายในกระบวนการ Java

## ข้อกำหนดเบื้องต้น

ก่อนเริ่มทำงาน ให้ตรวจสอบว่าคุณมี:

* JDK 17 หรือใหม่กว่า
* Maven 3.8+ (หรือ Gradle) สำหรับจัดการ dependencies
* Aspose.Words for Java 23.9 หรือใหม่กว่า – ไลบรารีนี้ให้ `DocumentBuilder` และ API คอนโทรล OLE
* ความคุ้นเคยพื้นฐานกับ Java และแมโคร VBA

หากขาดรายการใดรายการหนึ่ง ให้ติดตั้งก่อน; เนื้อหาต่อไปนี้สมมติว่ามีพร้อมใช้งานแล้ว

## วิธีสร้างปุ่มแมโครด้วย Aspose.Words for Java

แกนหลักของวิธีแก้ปัญหาประกอบด้วยสี่ขั้นตอน:

1. **แทรกคอนโทรลปุ่มคำสั่ง** OLE ลงในเอกสาร
2. **ตั้งข้อความบนปุ่ม** (caption) ที่ผู้ใช้จะเห็น
3. **เชื่อมโยงแมโครกับปุ่ม** เพื่อให้การคลิกทำงานตามรหัส VBA ที่ต้องการ
4. **บันทึกเอกสาร** พร้อมแมโครที่ฝังอยู่

แต่ละขั้นตอนจะอธิบายในส่วนของตนเองด้านล่าง

### ขั้นตอนที่ 1: แทรกปุ่มคำสั่งลงในเอกสาร

`DocumentBuilder.insertForms2OleControl` สร้างคอนโทรล OLE ตามประเภทที่ระบุ ค่าคงที่ `Forms2OleControlType.COMMAND_BUTTON` บอก Aspose.Words ให้สร้างปุ่มคำสั่งที่สามารถโฮสต์แมโครได้

```java
import com.aspose.words.*;

public class MacroButtonDemo {
    public static void main(String[] args) throws Exception {
        // Load a blank document or create a new one
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a command button OLE control
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMAND_BUTTON);
```

**เหตุผลที่สำคัญ:** คอนโทรล OLE ทำหน้าที่เป็นตัวบรรจุแมโคร หากไม่ได้แทรกคอนโทรลนี้ จะไม่มีองค์ประกอบที่ผู้ใช้สามารถคลิกได้

### ขั้นตอนที่ 2: ตั้งข้อความบนปุ่ม (caption)

caption คือป้ายชื่อที่มองเห็นได้บนปุ่ม ใช้ `setCaption` เพื่อกำหนดข้อความที่ผู้ใช้จะเห็น

```java
        // Set the button's caption – this is the text displayed on the button
        commandButton.setCaption("Run Report");
```

**เหตุผลที่สำคัญ:** ข้อความบนปุ่มที่ชัดเจนช่วยเพิ่มความใช้งานง่าย `setCaption` จะอัปเดตคุณสมบัติ `Caption` ของคอนโทรล OLE ซึ่ง Word จะเรนเดอร์เป็นป้ายปุ่ม

### ขั้นตอนที่ 3: เชื่อมโยงแมโครกับปุ่ม

แมโครจะถูกระบุด้วยชื่อของมัน เช่น `MyMacro` เมธอด `setOnClick` จะเก็บชื่อนี้ไว้ในตัวจัดการเหตุการณ์ `OnClick` ของปุ่ม

```java
        // Assign a macro to run when the button is clicked
        commandButton.setOnClick("MyMacro");
```

**เหตุผลที่สำคัญ:** การเชื่อมโยงแมโครทำให้เกิดพฤติกรรมโต้ตอบ เมื่อผู้ใช้คลิกปุ่มใน Word รหัส VBA ที่ระบุจะทำงาน

### ขั้นตอนที่ 4: เพิ่มปุ่มโต้ตอบลงในเอกสาร Word

หลังจากกำหนดค่าคอนโทรล OLE แล้ว คุณอาจต้องการกำหนดตำแหน่ง ปรับขนาด หรือเพิ่มข้อความรอบปุ่ม `DocumentBuilder` ยังคงทำงานกับเอกสารต่อไป คุณจึงสามารถแทรกย่อหน้าก่อนหรือหลังปุ่มได้

```java
        // Add a descriptive paragraph before the button
        builder.moveToDocumentStart();
        builder.writeln("Click the button below to generate the report:");

        // Move the cursor back to the button location (optional)
        builder.moveTo(commandButton.getNode());

        // Optionally, resize the button (width and height in points)
        commandButton.setWidth(120);
        commandButton.setHeight(30);

        // Save the document with the macro-enabled format
        doc.save("MacroButtonDemo.docm", SaveFormat.DOCM);
    }
}
```

**เหตุผลที่สำคัญ:** การบันทึกเป็น `.docm` จะคงรักษาโค้ดแมโครไว้ หากบันทึกเป็น `.docx` การอ้างอิงแมโครจะหายไป

## ตัวอย่างเต็มที่สามารถรันได้

ด้านล่างเป็นโปรแกรม Java ฉบับสมบูรณ์ รวมถึงการ import, การจัดการข้อยกเว้น, และคอมเมนต์อธิบายแต่ละขั้นตอน คัดลอกโค้ดไปยังโปรเจกต์ Maven ที่มี dependency ของ Aspose.Words แล้วรัน

```java
// Maven dependency (add to pom.xml):
// <dependency>
//   <groupId>com.aspose</groupId>
//   <artifactId>aspose-words</artifactId>
//   <version>23.9</version>
// </dependency>

import com.aspose.words.*;

public class MacroButtonDemo {
    public static void main(String[] args) throws Exception {
        // 1. Create a new empty document
        Document doc = new Document();

        // 2. Initialize DocumentBuilder to edit the document
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 3. Write an introductory paragraph
        builder.writeln("Press the button to execute the macro:");

        // 4. Insert the command button OLE control
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMAND_BUTTON);

        // 5. Set the visual caption of the button
        commandButton.setCaption("Run Report");

        // 6. Link the button to a VBA macro named MyMacro
        commandButton.setOnClick("MyMacro");

        // 7. Resize the button for better appearance
        commandButton.setWidth(120);   // points
        commandButton.setHeight(30);   // points

        // 8. Save the document as a macro‑enabled file
        doc.save("MacroButtonDemo.docm", SaveFormat.DOCM);
    }
}
```

### ผลลัพธ์ที่คาดหวัง

เมื่อรันโปรแกรมจะสร้างไฟล์ `MacroButtonDemo.docm` การเปิดไฟล์นี้ใน Microsoft Word จะเห็น:

* ย่อหน้าที่มีข้อความ *“Press the button to execute the macro:”*  
* ปุ่มที่มีป้าย **Run Report** อยู่ด้านล่างย่อหน้าโดยตรง  
* เมื่อคลิกปุ่ม Word จะพยายามรันแมโคร `MyMacro` (คุณต้องเพิ่มโค้ด VBA จริงลงในเอกสารด้วยตนเองหรือผ่านขั้นตอนอัตโนมัติอื่น)

หากแมโครไม่มีอยู่ Word จะแสดงคำเตือนด้านความปลอดภัย ซึ่งเป็นพฤติกรรมปกติของเอกสารที่เปิดใช้งานแมโคร

## ความแปรผันทั่วไปและกรณีขอบ

| สถานการณ์ | วิธีปรับโค้ด |
|----------|--------------|
| **เปลี่ยนข้อความบนปุ่ม** | เปลี่ยนสตริงที่ส่งให้ `setCaption` |
| **หลายปุ่ม** | เรียก `insertForms2OleControl` ซ้ำ ๆ พร้อม `setCaption` และ `setOnClick` ของแต่ละปุ่ม |
| **ชื่อแมโครแบบกำหนดเอง** | แทนที่ `"MyMacro"` ด้วยชื่อโปรซีเดอร์ VBA ที่ถูกต้อง เช่น `"ExportToExcel"` |
| **ข้อจำกัดขนาดปุ่ม** | ปรับค่า `setWidth` และ `setHeight`; Word จะใช้ค่าจุดที่คุณระบุ |
| **ฝังแมโครโดยโปรแกรม** | ใช้ `Document.getBuiltInDocumentProperties().add("Macros", …)` หรือขั้นตอนการฉีด VBA แยกต่างหาก; Aspose.Words ไม่เขียนโค้ด VBA เอง |

**เคล็ดลับ:** ทดสอบไฟล์ `.docm` ที่สร้างบนเครื่องที่ตั้งค่าความปลอดภัยของแมโครเป็น *Enable all macros* สำหรับการพัฒนา ในการใช้งานจริง ควรลงนามแมโครด้วยใบรับรองที่เชื่อถือได้เพื่อหลีกเลี่ยงการแจ้งเตือนด้านความปลอดภัย

## รายการตรวจสอบการแก้ไขปัญหา

* **ปุ่มไม่ปรากฏ** – ตรวจสอบว่าไฟล์บันทึกเป็น `.docm` และเปิดด้วย Word เวอร์ชันที่รองรับคอนโทรล OLE  
* **แมโครไม่ทำงาน** – ตรวจสอบว่าชื่อแมโครตรงกันอย่างแม่นยำ (รวมถึงตัวพิมพ์ใหญ่‑เล็ก) และแมโครมีอยู่ในโปรเจกต์ VBA ของเอกสาร  
* **ข้อความบนปุ่มถูกตัด** – เพิ่มความกว้างของปุ่มด้วย `setWidth` เพื่อรองรับข้อความยาวขึ้น  
* **เลย์เอาต์เปลี่ยนแปลงโดยไม่คาดคิด** – ใช้ `builder.moveTo` เพื่อตำแหน่งเคอร์เซอร์อย่างแม่นยำก่อนแทรกคอนโทรล  

## สรุป

คุณได้เรียนรู้วิธี **สร้างปุ่มแมโคร** ในเอกสาร Word ด้วย Java, **แทรกปุ่มคำสั่ง**, **ตั้งข้อความบนปุ่ม**, และ **เชื่อมโยงแมโครกับปุ่ม** เพื่อให้เอกสารมีความโต้ตอบเต็มรูปแบบ ตัวอย่างเต็มที่ให้เห็นการเรียก API ทุกขั้นตอน อธิบายเหตุผลของแต่ละขั้นตอน และให้คำแนะนำสำหรับความแปรผันทั่วไป

ต่อไปคุณอาจสำรวจ:

* **เพิ่มปุ่มโต้ตอบ** ลงในเทมเพลตที่มีอยู่แทนการสร้างเอกสารใหม่  
* **ฉีดโค้ด VBA อย่างโปรแกรม** ด้วย Open XML SDK หรือเครื่องมืออัตโนมัติอื่น  
* **รวมคอนโทรล OLE หลายตัว** (เช่น เช็คบ็อกซ์, ลิสต์บ็อกซ์) เพื่อสร้างฟอร์มที่ซับซ้อน

ลองปรับเปลี่ยน caption, ชื่อแมโคร, และขนาดปุ่มให้เหมาะกับกรณีการใช้งานของคุณเอง ขอให้สนุกกับการเขียนโค้ด!

## คุณควรเรียนรู้อะไรต่อไป?

บทเรียนต่อไปนี้ครอบคลุมหัวข้อที่เกี่ยวข้องอย่างใกล้ชิดและต่อยอดจากเทคนิคที่แสดงในคู่มือนี้ แต่ละแหล่งข้อมูลมีตัวอย่างโค้ดทำงานเต็มรูปแบบพร้อมคำอธิบายทีละขั้นตอน เพื่อช่วยให้คุณเชี่ยวชาญฟีเจอร์ API เพิ่มเติมและสำรวจวิธีการทำงานแบบอื่นในโปรเจกต์ของคุณ

- [วิธีแทรกปุ่มคำสั่งในไฟล์ Word ด้วย Java](/words/english/java/using-document-elements/how-to-insert-command-button-in-a-word-document-using-java/)
- [วิธีตั้งตำแหน่งปุ่มในไฟล์ Word ด้วย Java](/words/english/java/using-document-elements/how-to-set-button-position-in-a-word-document-with-java/)
- [วิธีแทรกปุ่ม ActiveX ใน Word – ตั้ง Caption ของปุ่ม](/words/english/java/using-document-elements/how-to-insert-activex-button-in-word-set-button-caption/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}