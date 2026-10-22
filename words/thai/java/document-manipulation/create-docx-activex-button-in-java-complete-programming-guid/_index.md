---
category: general
date: 2026-08-14
description: สร้างปุ่ม ActiveX ในไฟล์ docx ด้วย Java และ Aspose.Words. เรียนรู้วิธีเพิ่มปุ่มฟอร์มใน
  Word ด้วยโค้ดและบันทึกเอกสาร.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create docx ActiveX button
- add form button word
language: th
lastmod: 2026-08-14
og_description: สร้างปุ่ม ActiveX ในไฟล์ docx ด้วย Java โดยใช้ Aspose.Words คู่มือนี้จะแสดงวิธีเพิ่มปุ่มฟอร์มใน
  Word ตั้งค่าและบันทึกไฟล์
og_image_alt: Screenshot of a Word document containing an ActiveX CommandButton created
  with Java
og_title: สร้างปุ่ม ActiveX สำหรับไฟล์ docx ใน Java – คู่มือทีละขั้นตอน
schemas:
- author: Aspose
  dateModified: '2026-08-14'
  description: Create docx ActiveX button in Java with Aspose.Words. Learn how to
    add a form button in Word programmatically and save the document.
  headline: Create docx ActiveX button in Java – complete programming guide
  type: TechArticle
- description: Create docx ActiveX button in Java with Aspose.Words. Learn how to
    add a form button in Word programmatically and save the document.
  name: Create docx ActiveX button in Java – complete programming guide
  steps:
  - name: Set up the project and import Aspose.Words
    text: 'Add the Aspose.Words dependency to your `pom.xml` if you use Maven:'
  - name: Create a new blank document
    text: Instantiate a `Document` object, which represents an empty Word file ready
      to receive content.
  - name: Initialize a DocumentBuilder
    text: '`DocumentBuilder` provides a fluent interface for inserting text, images,
      and controls. Attach it to the document you just created.'
  - name: Insert an ActiveX CommandButton control
    text: Use the `insertForms2OleControl` method to embed an ActiveX `CommandButton`.
      This method returns a `Forms2OleControl` instance that you can further configure.
  - name: Configure the button’s properties
    text: Set the control’s name, caption, and layout attributes. These values determine
      how the button appears in Word and how you can reference it later via VBA or
      automation scripts.
  - name: Save the document
    text: Finally, write the document to disk. Use the `.docx` extension to keep the
      file in the modern Office Open XML format.
  type: HowTo
tags:
- ActiveX
- Java
- Aspose.Words
- Word automation
title: สร้างปุ่ม ActiveX สำหรับไฟล์ docx ใน Java – คู่มือการเขียนโปรแกรมฉบับสมบูรณ์
url: /th/java/document-manipulation/create-docx-activex-button-in-java-complete-programming-guid/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# สร้างปุ่ม ActiveX ในไฟล์ docx ด้วย Java – คู่มือการเขียนโปรแกรมครบถ้วน

หากคุณต้องการ **create docx ActiveX button** ใน Java คู่มือนี้จะพาคุณผ่านขั้นตอนทั้งหมด คุณจะได้เห็นวิธีเพิ่มปุ่มฟอร์มใน Word ตั้งค่าคุณสมบัติของมัน และสร้างไฟล์ .docx ที่พร้อมใช้งาน

การทำงานกับคอนโทรล ActiveX เป็นความต้องการทั่วไปเมื่อทำการอัตโนมัติฟอร์ม Word รุ่นเก่า ในบทเรียนนี้คุณจะได้เรียนรู้วิธี **add form button word** เอกสารโดยใช้ไลบรารี Aspose.Words for Java เพื่อให้คุณสามารถฝังคอนโทรลแบบโต้ตอบได้โดยไม่ต้องแก้ไขด้วยตนเอง

## สิ่งที่คุณต้องเตรียม

* Java 17 หรือใหม่กว่า (โค้ดสามารถคอมไพล์กับเวอร์ชันก่อนหน้าได้ แต่แนะนำให้ใช้ Java 17)
* Aspose.Words for Java 23.10 หรือใหม่กว่า – ดาวน์โหลด JAR จากเว็บไซต์ Aspose หรือเพิ่ม dependency ของ Maven
* IDE (IntelliJ IDEA, Eclipse หรือ VS Code) หรือเครื่องมือแก้ไขข้อความง่าย ๆ พร้อมเครื่องมือสร้างแบบ command‑line
* ความรู้พื้นฐานเกี่ยวกับไวยากรณ์ Java และการเขียนโปรแกรมเชิงวัตถุ

## วิธีสร้างปุ่ม ActiveX ในไฟล์ docx ด้วย Aspose.Words

ขั้นตอนต่อไปนี้แสดงลำดับที่แน่นอนที่จำเป็นสำหรับการ **create docx ActiveX button** วัตถุและฝังลงในเอกสาร Word

### ขั้นตอนที่ 1: ตั้งค่าโปรเจกต์และนำเข้า Aspose.Words

เพิ่ม dependency ของ Aspose.Words ลงในไฟล์ `pom.xml` ของคุณหากใช้ Maven:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.10</version>
    <classifier>jdk17</classifier>
</dependency>
```

หรือ หากคุณต้องการใช้ Gradle:

```gradle
implementation 'com.aspose:aspose-words:23.10:jdk17'
```

เมื่อ dependency ถูกดึงมาเรียบร้อยแล้ว ให้นำเข้าคลาสที่จำเป็นในไฟล์ซอร์ส Java ของคุณ:

```java
import com.aspose.words.Document;
import com.aspose.words.DocumentBuilder;
import com.aspose.words.forms.Forms2OleControl;
import com.aspose.words.forms.Forms2OleControlType;
```

การนำเข้าดังกล่าวทำให้คุณเข้าถึง `Document`, `DocumentBuilder` และ API `Forms2OleControl` ที่ใช้ในการแทรกคอนโทรล ActiveX

### ขั้นตอนที่ 2: สร้างเอกสารเปล่าใหม่

สร้างอ็อบเจกต์ `Document` ซึ่งเป็นไฟล์ Word ว่างเปล่าที่พร้อมรับเนื้อหา

```java
// Step 2: Create a new blank document
Document document = new Document();
```

การสร้างเอกสารก่อนทำให้ตัวสร้างต่อไปทำงานบนผืนผ้าใบที่สะอาด

### ขั้นตอนที่ 3: เริ่มต้น DocumentBuilder

`DocumentBuilder` ให้ส่วนต่อประสานแบบ fluent สำหรับการแทรกข้อความ, รูปภาพ, และคอนโทรล. ผูกมันเข้ากับเอกสารที่คุณสร้างไว้

```java
// Step 3: Initialize a DocumentBuilder to construct the document content
DocumentBuilder builder = new DocumentBuilder(document);
```

ตัวสร้างจะติดตามตำแหน่งเคอร์เซอร์ปัจจุบันภายในเอกสาร ทำให้การแทรกต่อไปเกิดขึ้นตรงตำแหน่งที่คุณต้องการ

### ขั้นตอนที่ 4: แทรกคอนโทรล ActiveX CommandButton

ใช้เมธอด `insertForms2OleControl` เพื่อฝัง ActiveX `CommandButton`. เมธอดนี้จะคืนค่าอินสแตนซ์ของ `Forms2OleControl` ที่คุณสามารถกำหนดค่าเพิ่มเติมได้

```java
// Step 4: Insert an ActiveX CommandButton control into the document
Forms2OleControl commandButton = builder.insertForms2OleControl(
        Forms2OleControlType.COMMAND_BUTTON);
```

ในขั้นตอนนี้ไฟล์ .docx มีเพียงที่วางสำหรับปุ่มเท่านั้น แต่ยังไม่มีคำบรรยายหรือขนาดที่มองเห็นได้

### ขั้นตอนที่ 5: กำหนดคุณสมบัติของปุ่ม

ตั้งค่าชื่อของคอนโทรล, คำบรรยาย, และแอตทริบิวต์การจัดวาง ค่าเหล่านี้กำหนดว่าปุ่มจะแสดงอย่างไรใน Word และคุณจะอ้างอิงมันต่อไปได้อย่างไรผ่าน VBA หรือสคริปต์อัตโนมัติ

```java
// Step 5: Configure the button's properties (name, caption, size, and position)
commandButton.setName("btnSubmit");          // internal name used by VBA
commandButton.setCaption("Submit");          // text shown on the button
commandButton.setTop(100);                  // distance from the top of the page (points)
commandButton.setLeft(150);                 // distance from the left margin (points)
commandButton.setWidth(80);                 // button width (points)
commandButton.setHeight(30);                // button height (points)
```

> **เคล็ดลับ:** Word วัดตำแหน่งเป็นจุด (1 pt ≈ 1/72 in). ปรับ `setTop` และ `setLeft` เพื่อจัดตำแหน่งปุ่มให้สอดคล้องกับเนื้อหารอบข้าง

### ขั้นตอนที่ 6: บันทึกเอกสาร

สุดท้าย ให้เขียนเอกสารลงดิสก์ ใช้นามสกุล `.docx` เพื่อเก็บไฟล์ในรูปแบบ Office Open XML สมัยใหม่

```java
// Step 6: Save the document containing the ActiveX button
String outputPath = "C:/temp/ActiveXButton.docx";
document.save(outputPath);
System.out.println("Document saved to " + outputPath);
```

เมื่อคุณเปิดไฟล์ที่ได้ใน Microsoft Word คุณจะเห็นปุ่ม **Submit** ที่วางตามพิกัดที่ระบุ การคลิกปุ่มใน Word จะไม่ทำให้เกิดการทำงานใด ๆ เว้นแต่คุณจะแนบโค้ด VBA แต่คอนโทรลนี้ทำงานเต็มรูปแบบสำหรับกระบวนการทำงานแบบฟอร์ม

## คำถามทั่วไปและกรณีขอบ

| Question | Answer |
|----------|--------|
| **ฉันต้องการเวอร์ชัน Word พิเศษหรือไม่?** | คอนโทรล ActiveX รองรับในเวอร์ชันเดสก์ท็อปของ Microsoft Word บน Windows แต่ไม่สามารถใช้ได้ใน Word สำหรับ Mac หรือ Word Online |
| **ฉันสามารถใช้กับไฟล์ `.doc` ได้หรือไม่?** | ได้ครับ/ค่ะ บันทึกเอกสารด้วยนามสกุล `.doc` (`document.save("ActiveXButton.doc")`). API เดียวกันทำงานกับรูปแบบไบนารีเก่าได้เช่นกัน |
| **ถ้าปุ่มไม่แสดงขึ้นจะทำอย่างไร?** | ตรวจสอบให้แน่ใจว่า **File → Options → Trust Center → Trust Center Settings → ActiveX Settings** อนุญาตคอนโทรล ActiveX และตรวจสอบว่าเอกสารไม่ได้เปิดใน “Protected View” |
| **ฉันสามารถเพิ่มคอนโทรล ActiveX อื่นได้หรือไม่?** | ได้เลย แค่เปลี่ยน `Forms2OleControlType.COMMAND_BUTTON` เป็น `Forms2OleControlType.CHECK_BOX`, `RADIO_BUTTON` เป็นต้น |
| **มีขนาดจำกัดหรือไม่?** | ขนาดของคอนโทรลจำกัดโดยการจัดหน้าเท่านั้น มิติที่ใหญ่เกินไปอาจทำให้เกิดการล้นของเลย์เอาต์ |

## ตัวอย่างเต็มที่สามารถรันได้

ด้านล่างเป็นคลาส Java ที่สมบูรณ์ซึ่งคุณสามารถคัดลอก, คอมไพล์, และรันได้ รวมถึงการนำเข้าทั้งหมด, เมธอด main, และคอมเมนต์ในบรรทัดเพื่อความชัดเจน

```java
package com.example.wordactive;

import com.aspose.words.Document;
import com.aspose.words.DocumentBuilder;
import com.aspose.words.forms.Forms2OleControl;
import com.aspose.words.forms.Forms2OleControlType;

public class ActiveXButtonDemo {
    public static void main(String[] args) {
        try {
            // Create a new blank document
            Document document = new Document();

            // Initialize DocumentBuilder
            DocumentBuilder builder = new DocumentBuilder(document);

            // Insert an ActiveX CommandButton control
            Forms2OleControl commandButton = builder.insertForms2OleControl(
                    Forms2OleControlType.COMMAND_BUTTON);

            // Configure button properties
            commandButton.setName("btnSubmit");
            commandButton.setCaption("Submit");
            commandButton.setTop(100);   // points from top
            commandButton.setLeft(150);  // points from left
            commandButton.setWidth(80);  // width in points
            commandButton.setHeight(30); // height in points

            // Save the document
            String outputPath = "ActiveXButton.docx";
            document.save(outputPath);
            System.out.println("Document saved successfully to " + outputPath);
        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}
```

**ผลลัพธ์ที่คาดหวัง:** หลังจากรันโปรแกรม `ActiveXButton.docx` จะปรากฏในไดเรกทอรีทำงาน การเปิดไฟล์ใน Microsoft Word จะเห็นปุ่ม **Submit** ที่คลิกได้ซึ่งอยู่ใกล้ด้านบน‑ซ้ายของหน้าแรก

## สรุป

ตอนนี้คุณรู้วิธี **create docx ActiveX button** วัตถุใน Java ด้วย Aspose.Words แล้ว และคุณได้เห็นวิธี **add form button word** เอกสารโดยอัตโนมัติ ขั้นตอนต่าง ๆ — ตั้งค่าโปรเจกต์, สร้างเอกสาร, แทรกคอนโทรล, กำหนดคุณสมบัติ, และบันทึก — ครอบคลุมกระบวนการทำงานทั้งหมดตั้งแต่ต้นจนจบ

ต่อไปคุณอาจสำรวจ:

* เพิ่มแมโคร VBA ที่ตอบสนองต่อการคลิกปุ่ม
* ฝังคอนโทรล ActiveX อื่น ๆ เช่น เช็คบ็อกซ์หรือลิสต์บ็อกซ์
* อัตโนมัติการสร้างฟอร์มหลายหน้าโดยมีองค์ประกอบโต้ตอบหลายรายการ

คุณสามารถทดลองปรับขนาด, ตำแหน่ง, และคำบรรยายเพื่อให้ตรงกับความต้องการออกแบบฟอร์มของคุณได้อย่างอิสระ ขอให้สนุกกับการเขียนโค้ด!

## สิ่งที่คุณควรเรียนต่อไป

บทเรียนต่อไปนี้ครอบคลุมหัวข้อที่เกี่ยวข้องอย่างใกล้ชิดและต่อยอดจากเทคนิคที่แสดงในคู่มือนี้ แต่ละแหล่งข้อมูลมีตัวอย่างโค้ดทำงานครบถ้วนพร้อมคำอธิบายทีละขั้นตอน เพื่อช่วยคุณเชี่ยวชาญฟีเจอร์ API เพิ่มเติมและสำรวจวิธีการทำงานทางเลือกในโปรเจกต์ของคุณ

- [วิธีสร้างฟิลด์ฟอร์มและเพิ่มเนื้อหาโดยใช้ DocumentBuilder ใน Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [วิธีโหลด HTML และบันทึกเป็น DOCX ด้วย Aspose.Words for Java](/words/english/java/document-loading-and-saving/loading-and-saving-html-documents/)
- [วิธีสร้างเอกสาร PDF ด้วย Aspose.Words for Java | Document Processing API](/words/english/java/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}