---
category: general
date: 2026-09-27
description: สร้างไฟล์ docx ที่มี ActiveX ใน Java ด้วย Aspose.Words เรียนรู้วิธีแทรกปุ่มคำสั่ง
  ActiveX ทีละขั้นตอน.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create docx containing activex
- insert activex command button
- Aspose.Words Java
- ActiveX control in Word
- generate Word document programmatically
language: th
lastmod: 2026-09-27
og_description: สร้างไฟล์ docx ที่มี ActiveX ใน Java ด้วย Aspose.Words. ทำตามคำแนะนำนี้เพื่อแทรกปุ่มคำสั่ง
  ActiveX และบันทึกเอกสาร.
og_image_alt: Screenshot of a Word document that contains an ActiveX command button
og_title: สร้างไฟล์ docx ที่มี ActiveX ใน Java – คู่มือฉบับเต็ม
schemas:
- author: Aspose
  dateModified: '2026-09-27'
  description: Create docx containing ActiveX in Java using Aspose.Words. Learn to
    insert an ActiveX command button step‑by‑step.
  headline: How to create docx containing ActiveX with Java and Aspose.Words
  type: TechArticle
- description: Create docx containing ActiveX in Java using Aspose.Words. Learn to
    insert an ActiveX command button step‑by‑step.
  name: How to create docx containing ActiveX with Java and Aspose.Words
  steps:
  - name: The document should show a single page with a button labeled **Click Me**
      positioned near the top‑left corner.
    text: The document should show a single page with a button labeled **Click Me**
      positioned near the top‑left corner.
  - name: If the button does not appear, check that **ActiveX controls are enabled**
      in Word’s Trust Center (File → Options → Trust Center → Trust Center Settings
      → ActiveX Settings).
    text: If the button does not appear, check that **ActiveX controls are enabled**
      in Word’s Trust Center (File → Options → Trust Center → Trust Center Settings
      → ActiveX Settings).
  - name: The button is functional only on Windows versions of Word that support ActiveX.
      On macOS or web‑based Word, the control will be displayed as a static image.
    text: The button is functional only on Windows versions of Word that support ActiveX.
      On macOS or web‑based Word, the control will be displayed as a static image.
  type: HowTo
tags:
- docx
- activex
- java
- aspose-words
title: วิธีสร้างไฟล์ docx ที่มี ActiveX ด้วย Java และ Aspose.Words
url: /th/java/using-document-elements/how-to-create-docx-containing-activex-with-java-and-aspose-w/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# วิธีสร้าง docx ที่มี ActiveX ด้วย Java และ Aspose.Words

หากคุณต้องการ **สร้าง docx ที่มี ActiveX** คู่มือนี้จะแสดงวิธีแก้ไขแบบครบวงจร คุณจะได้เรียนรู้วิธี **แทรกปุ่มคำสั่ง ActiveX** ลงในไฟล์ Word ด้วย Aspose.Words for Java แล้วบันทึกผลลัพธ์เป็นไฟล์ .docx ที่สามารถเปิดด้วย Microsoft Word ได้

การสร้างเอกสาร Word ด้วยโปรแกรมช่วยให้คุณหลีกเลี่ยงการแก้ไขด้วยมือและรับประกันความสอดคล้องของรายงาน, สัญญา หรือเทมเพลตฟอร์ม ขั้นตอนด้านล่างครอบคลุมทุกอย่างตั้งแต่การตั้งค่าโครงการจนถึงการจัดการกับปัญหาที่พบบ่อย เพื่อให้คุณสามารถผสานเทคนิคนี้เข้าไปในแอปพลิเคชัน Java ใดก็ได้

## ข้อกำหนดเบื้องต้น

ก่อนเริ่มทำงาน โปรดตรวจสอบว่าคุณมี:

* ติดตั้ง Java Development Kit (JDK) 8 หรือใหม่กว่า
* Maven 3.6+ (หรือเครื่องมือสร้างอื่นที่คุณต้องการ)
* ไฟล์ใบอนุญาต Aspose.Words for Java (รุ่นทดลองฟรีใช้สำหรับการทดสอบ)
* ติดตั้ง Microsoft Word บนเครื่องเป้าหมายหากต้องการตรวจสอบการทำงานของ ActiveX อย่างเห็นภาพ

สิ่งเหล่านี้จำเป็นเพราะ Aspose.Words ให้ API สำหรับสร้างเอกสาร ส่วน Word จำเป็นสำหรับการแสดงผลควบคุม ActiveX

## ขั้นตอนที่ 1: ตั้งค่าโครงการ Maven

สร้างโครงการ Maven ใหม่หรือเพิ่มการอ้างอิง Aspose.Words ลงใน `pom.xml` ที่มีอยู่:

```xml
<project>
    <modelVersion>4.0.0</modelVersion>
    <groupId>com.example</groupId>
    <artifactId>activex-docx-demo</artifactId>
    <version>1.0.0</version>
    <properties>
        <maven.compiler.source>1.8</maven.compiler.source>
        <maven.compiler.target>1.8</maven.compiler.target>
    </properties>

    <dependencies>
        <!-- Aspose.Words for Java -->
        <dependency>
            <groupId>com.aspose</groupId>
            <artifactId>aspose-words</artifactId>
            <version>24.10</version> <!-- use the latest stable version -->
        </dependency>
    </dependencies>
</project>
```

> **เคล็ดลับ:** ควรรักษาเวอร์ชันของ Aspose.Words ให้ตรงกับบันทึกการปล่อยเวอร์ชันอย่างเป็นทางการเพื่อรับประโยชน์จากการแก้ไขบั๊กและคุณสมบัติ ActiveX ใหม่

## ขั้นตอนที่ 2: เขียนโค้ด Java ที่สร้างเอกสาร

สร้างคลาสชื่อ `ActiveXDocxCreator` โค้ดด้านล่างรวมการนำเข้า (import) ที่จำเป็นทั้งหมด, เมธอด `main`, และคอมเมนต์ละเอียดที่อธิบายการทำงานแต่ละขั้นตอน

```java
package com.example.activex;

import com.aspose.words.*;
import java.io.File;

/**
 * Demonstrates how to create a DOCX file that contains an ActiveX command button.
 * The resulting file can be opened in Microsoft Word where the button appears
 * on the first page.
 */
public class ActiveXDocxCreator {

    public static void main(String[] args) {
        // 1. Initialize a new empty document and a DocumentBuilder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2. Insert an ActiveX Forms2OleControl at the current cursor position.
        Forms2OleControl commandButton = builder.insertForms2OleControl();

        // 3. Configure the control to be a CommandButton and set its caption.
        commandButton.setControlType(Forms2OleControlType.COMMANDBUTTON);
        commandButton.setCaption("Click Me");

        // 4. Position the button on the page.
        //    The coordinates are measured in points (1 point = 1/72 inch).
        commandButton.setLeft(100); // 100 points from the left margin
        commandButton.setTop(150);  // 150 points from the top margin

        // 5. (Optional) Set the size of the button for better visibility.
        commandButton.setWidth(120);
        commandButton.setHeight(30);

        // 6. Save the document to the desired location.
        String outputPath = "output/ActiveXCommandButton.docx";
        try {
            // Ensure the output directory exists.
            new File("output").mkdirs();
            doc.save(outputPath);
            System.out.println("Document saved successfully to " + outputPath);
        } catch (Exception e) {
            System.err.println("Error while saving the document: " + e.getMessage());
        }
    }
}
```

### ทำไมแต่ละบรรทัดจึงสำคัญ

* `Document` คือคอนเทนเนอร์สำหรับเนื้อหา Word ทั้งหมด การสร้างอินสแตนซ์ใหม่ให้คุณได้ผืนผ้าใบที่สะอาด
* `DocumentBuilder` ให้ API แบบ fluent สำหรับแทรกองค์ประกอบ; มันจะติดตามตำแหน่งการแทรกโดยอัตโนมัติ
* `insertForms2OleControl()` สร้างตัวแทน OLE ควบคุมทั่วไป Aspose.Words จะถือว่าเป็นคอนเทนเนอร์ ActiveX
* `setControlType(Forms2OleControlType.COMMANDBUTTON)` บอก Word ว่าตัวแทนควรแสดงเป็น CommandButton
* `setCaption("Click Me")` กำหนดข้อความที่แสดงบนปุ่ม
* `setLeft` และ `setTop` วางปุ่มตามระยะจากขอบกระดาษ ปรับค่าเหล่านี้ให้เหมาะกับการจัดวางของคุณ
* `setWidth` และ `setHeight` เป็นค่าตัวเลือก แต่ช่วยปรับปรุงลักษณะของปุ่ม โดยเฉพาะเมื่อขนาดเริ่มต้นเล็กเกินไป
* `doc.save` เขียนโครงสร้างในหน่วยความจำเป็นไฟล์ .docx จริงที่ Word สามารถเปิดได้

## ขั้นตอนที่ 3: ตรวจสอบเอกสารที่สร้าง

เปิด `output/ActiveXCommandButton.docx` ด้วย Microsoft Word:

1. เอกสารควรแสดงหน้าเดียวพร้อมปุ่มที่มีป้าย **Click Me** อยู่ใกล้มุมบน‑ซ้าย
2. หากปุ่มไม่ปรากฏ ให้ตรวจสอบว่า **เปิดใช้งานควบคุม ActiveX** ใน Trust Center ของ Word (File → Options → Trust Center → Trust Center Settings → ActiveX Settings)
3. ปุ่มทำงานได้เฉพาะบน Word เวอร์ชัน Windows ที่รองรับ ActiveX เท่านั้น บน macOS หรือ Word แบบเว็บ ควบคุมจะถูกแสดงเป็นภาพคงที่

## ขั้นตอนที่ 4: จัดการกับกรณีขอบที่พบบ่อย

| สถานการณ์ | เหตุผล | การดำเนินการแนะนำ |
|-----------|--------|--------------------|
| ปุ่มหายไปหลังจากเปิดไฟล์ | การตั้งค่าความปลอดภัยของ Word บล็อก ActiveX | เปิดใช้งาน “Run all controls without restrictions” สำหรับตำแหน่งที่เชื่อถือ |
| ไม่สามารถเปิด .docx ที่สร้างได้ | เวอร์ชัน Aspose.Words ไม่เข้ากัน | อัปเกรดเป็นรุ่นล่าสุดของ Aspose.Words; รุ่นเก่าอาจไม่ฝังส่วน OLE ที่จำเป็นอย่างถูกต้อง |
| ต้องการให้ปุ่มเรียกใช้แมโคร | ActiveX เพียงอย่างเดียวไม่มีโค้ดแมโคร | รวมควบคุม ActiveX กับแมโคร VBA ที่จัดการเหตุการณ์ `Click`. ใช้เมธอด `DocumentBuilder.insertOleObject` เพื่อฝังเทมเพลตที่เปิดใช้งานแมโคร |
| การจัดวางผิดพลาดบนขนาดหน้ากระดาษต่างกัน | พิกัดเป็นจุดแบบคงที่ | ใช้ `builder.getPageSetup().setPageWidth` และ `setPageHeight` เพื่อทำให้ขนาดหน้ากระดาษเป็นมาตรฐานก่อนวางควบคุม |

## ขั้นตอนที่ 5: ขยายโซลูชัน

คุณสามารถแทรกควบคุม ActiveX อื่นได้โดยการเปลี่ยนค่า enum `ControlType`:

```java
commandButton.setControlType(Forms2OleControlType.CHECKBOX); // inserts a checkbox
```

Aspose.Words ยังรองรับการแทรก **กล่องข้อความ ActiveX**, **list box**, และ **combo box** วิธีการกำหนดตำแหน่งเดียวกัน (`setLeft`, `setTop`, `setWidth`, `setHeight`) ใช้ได้เช่นกัน

หากต้องการวางหลายควบคุม ให้เรียก `builder.insertForms2OleControl()` ซ้ำหลายครั้งและปรับพิกัดของแต่ละควบคุมตามความต้องการ

## ไฟล์ซอร์สเต็ม

ด้านล่างเป็นไฟล์ `ActiveXDocxCreator.java` ทั้งหมดพร้อมคัดลอกและวาง:

```java
package com.example.activex;

import com.aspose.words.*;
import java.io.File;

public class ActiveXDocxCreator {
    public static void main(String[] args) {
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        Forms2OleControl commandButton = builder.insertForms2OleControl();
        commandButton.setControlType(Forms2OleControlType.COMMANDBUTTON);
        commandButton.setCaption("Click Me");
        commandButton.setLeft(100);
        commandButton.setTop(150);
        commandButton.setWidth(120);
        commandButton.setHeight(30);

        String outputPath = "output/ActiveXCommandButton.docx";
        try {
            new File("output").mkdirs();
            doc.save(outputPath);
            System.out.println("Document saved successfully to " + outputPath);
        } catch (Exception e) {
            System.err.println("Error while saving the document: " + e.getMessage());
        }
    }
}
```

การรันโปรแกรมนี้จะสร้าง **docx ที่มี ActiveX** ที่คุณสามารถแจกจ่ายให้ผู้ใช้ปลายทางที่ต้องการแบบฟอร์มแบบโต้ตอบได้

## สรุป

คุณตอนนี้รู้วิธี **สร้าง docx ที่มี ActiveX** ด้วย Java และ Aspose.Words และวิธี **แทรกปุ่มคำสั่ง ActiveX** อย่างอัตโนมัติ คู่มือนี้ได้ครอบคลุมการตั้งค่าโครงการ, โค้ดเต็ม, ขั้นตอนการตรวจสอบ, และกลยุทธ์การจัดการกับปัญหาทั่วไป

ต่อจากนี้คุณอาจสำรวจ:

* เพิ่มแมโคร VBA เพื่อตอบสนองต่อการคลิกปุ่ม
* ฝังควบคุม ActiveX อื่น เช่น เช็คบ็อกซ์หรือคอมโบบ็อกซ์
* อัตโนมัติการสร้างแบบฟอร์มหลายหน้าโดยใช้ข้อมูลแบบไดนามิก

ทดลองใช้พิกัด, ขนาด, และประเภทควบคุมที่ต่างกันเพื่อให้เข้ากับการจัดวางเอกสารของคุณเอง ขอให้สนุกกับการเขียนโค้ด!

## สิ่งที่คุณควรเรียนต่อ

บทแนะนำต่อไปนี้ครอบคลุมหัวข้อที่เกี่ยวข้องอย่างใกล้ชิดและต่อยอดจากเทคนิคที่แสดงในคู่มือนี้ แต่ละแหล่งรวมตัวอย่างโค้ดทำงานเต็มรูปแบบพร้อมคำอธิบายขั้นตอนเพื่อช่วยคุณเชี่ยวชาญฟีเจอร์ API เพิ่มเติมและสำรวจแนวทางการทำงานแบบอื่นในโครงการของคุณ

- [การใช้ OLE Objects และ ActiveX Controls ใน Aspose.Words for Java](/words/english/java/using-document-elements/using-ole-objects-and-activex/)
- [วิธีสร้างฟิลด์ฟอร์มและเพิ่มเนื้อหาโดยใช้ DocumentBuilder ใน Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [สร้างรูปสี่เหลี่ยมใน Word ด้วย Aspose.Words – คู่มือขั้นตอนโดยละเอียด](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}