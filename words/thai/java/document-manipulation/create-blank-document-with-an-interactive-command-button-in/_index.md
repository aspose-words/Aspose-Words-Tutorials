---
category: general
date: 2026-09-18
description: สร้างเอกสารเปล่าใน Java และเพิ่มปุ่ม ActiveX เรียนรู้วิธีแทรกปุ่มคำสั่ง
  สร้างฟอร์มโต้ตอบ และบันทึกเอกสาร Word
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank document
- create interactive form
- add activex button
- how to insert command button
- create word document
language: th
lastmod: 2026-09-18
og_description: สร้างเอกสารเปล่าใน Java และฝังปุ่มคำสั่ง ActiveX ตามคำแนะนำขั้นตอนต่อขั้นตอนนี้เพื่อสร้างแบบฟอร์มโต้ตอบและบันทึกไฟล์
  Word.
og_image_alt: Screenshot of a Word document showing a clickable ActiveX command button
og_title: สร้างเอกสารเปล่าพร้อมปุ่มคำสั่งโต้ตอบใน Word
schemas:
- author: Aspose
  dateModified: '2026-09-18'
  description: Create blank document in Java and add an ActiveX button. Learn how
    to insert command button, build an interactive form, and save a Word document.
  headline: Create blank document with an interactive command button in Word using
    Java
  type: TechArticle
- description: Create blank document in Java and add an ActiveX button. Learn how
    to insert command button, build an interactive form, and save a Word document.
  name: Create blank document with an interactive command button in Word using Java
  steps:
  - name: 'Load the existing document: `Document doc = new Document("ExistingForm.docx");`'
    text: 'Load the existing document: `Document doc = new Document("ExistingForm.docx");`'
  - name: 'Move the builder to the desired location: `builder.moveToParagraph(5, 0);
      // 6th paragraph, first node`'
    text: 'Move the builder to the desired location: `builder.moveToParagraph(5, 0);
      // 6th paragraph, first node`'
  - name: Insert the button as shown in Step 3.
    text: Insert the button as shown in Step 3.
  - name: Adjust the button’s `Top`/`Left` based on the paragraph’s layout.
    text: Adjust the button’s `Top`/`Left` based on the paragraph’s layout.
  type: HowTo
tags:
- Aspose.Words
- Java
- ActiveX
- Word automation
title: สร้างเอกสารเปล่าพร้อมปุ่มคำสั่งโต้ตอบใน Word ด้วย Java
url: /th/java/document-manipulation/create-blank-document-with-an-interactive-command-button-in/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# สร้างเอกสารเปล่าพร้อมปุ่มคำสั่งแบบโต้ตอบใน Word ด้วย Java

หากคุณต้องการ **สร้างเอกสารเปล่า** ที่มีปุ่มคลิกได้ คู่มือนี้จะแสดงวิธีทำอย่างละเอียดด้วย Aspose.Words for Java คุณจะได้เรียนรู้การสร้างแบบฟอร์มโต้ตอบ, เพิ่มปุ่ม ActiveX, และสุดท้ายบันทึกไฟล์ Word—ทั้งหมดในไม่กี่ขั้นตอนสั้น ๆ

การฝังปุ่มคำสั่งทำให้ไฟล์ .docx ที่คงที่กลายเป็นแบบฟอร์มทำงานที่ผู้ใช้ปลายทางสามารถโต้ตอบได้โดยตรงใน Microsoft Word คู่มือนี้ยังครอบคลุม **วิธีแทรกปุ่มคำสั่ง**, การจัดการกับข้อผิดพลาดทั่วไป, และการขยายโซลูชันสำหรับแบบฟอร์มที่ซับซ้อนมากขึ้น.

## ข้อกำหนดเบื้องต้น

* Java 17 หรือใหม่กว่า (โค้ดคอมไพล์ด้วย JDK 17+)
* Aspose.Words for Java 23.9 หรือใหม่กว่า – ไลบรารีให้ `Document`, `DocumentBuilder`, และ `Forms2OleControl`.
* IDE หรือเครื่องมือสร้าง (Maven/Gradle) ที่สามารถเพิ่ม dependency ของ Aspose.Words
* ความรู้พื้นฐานเกี่ยวกับไวยากรณ์ Java และแนวคิดเอกสาร Word

```xml
<!-- Maven dependency -->
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
</dependency>
```

## ขั้นตอนที่ 1: สร้างเอกสารเปล่า

การดำเนินการแรกคือการสร้างอ็อบเจ็กต์ `Document` ใหม่ ซึ่งอ็อบเจ็กต์นี้เป็นไฟล์ Word ว่างเปล่าที่พร้อมสำหรับการใส่เนื้อหา

```java
// Step 1: Create a new blank document
Document doc = new Document();
```

การสร้างเอกสารเปล่าให้คุณได้ผืนผ้าใบที่สะอาด ซึ่งจำเป็นเมื่อคุณต้องการ **สร้างเอกสาร Word** ด้วยโปรแกรมโดยไม่มีเทมเพลตที่มีอยู่ล่วงหน้า

## ขั้นตอนที่ 2: เริ่มต้น DocumentBuilder

`DocumentBuilder` เป็นคลาสหลักสำหรับการเพิ่มข้อความ, ตาราง, และคอนโทรลฟอร์ม มันทำงานบน `Document` ที่คุณเพิ่งสร้าง

```java
// Step 2: Initialize a DocumentBuilder to construct the document content
DocumentBuilder builder = new DocumentBuilder(doc);
```

Builder จะรักษาตำแหน่งการแทรกปัจจุบันไว้ ดังนั้นคำสั่งต่อมาจะส่งผลต่อตำแหน่งที่ถูกต้องในไฟล์

## ขั้นตอนที่ 3: แทรกคอนโทรลปุ่มคำสั่ง Forms2Ole

Aspose.Words เปิดเผยคลาส `Forms2OleControl` สำหรับคอนโทรล ActiveX เพื่อ **เพิ่มปุ่ม activex** คุณต้องขอประเภท `COMMANDBUTTON` จาก builder

```java
// Step 3: Insert a Forms2Ole command button control
Forms2OleControl commandButton = builder.insertForms2OleControl(OleControlType.COMMANDBUTTON);
```

เมธอด `insertForms2OleControl` จะใส่คอนโทรลที่ตำแหน่งเคอร์เซอร์ปัจจุบันของ builder เนื่องจากคอนโทรลเป็นอ็อบเจ็กต์ ActiveX จึงทำงานได้เฉพาะในเวอร์ชันเดสก์ท็อปของ Microsoft Word เท่านั้น ไม่ทำงานใน Word Online

## ขั้นตอนที่ 4: กำหนดลักษณะและตำแหน่งของปุ่ม

คุณสามารถตั้งค่าคำบรรยาย, ขนาด, และตำแหน่งของปุ่มโดยใช้ setter ของคอนโทรล ค่าตำแหน่งวัดเป็นจุด (1 point = 1/72 นิ้ว)

```java
// Step 4: Configure the button's appearance and position
commandButton.setCaption("Click Me");   // Text shown on the button
commandButton.setTop(100);              // Distance from the top edge of the page (points)
commandButton.setLeft(100);             // Distance from the left edge of the page (points)
commandButton.setWidth(120);            // Optional: set button width
commandButton.setHeight(30);            // Optional: set button height
```

*ทำไมต้องกำหนดคุณสมบัติเหล่านี้?* การตั้งค่า `Top` และ `Left` ทำให้ปุ่มปรากฏในตำแหน่งที่คุณคาดหวังบนหน้า, ส่วน `Caption` กำหนดป้ายที่ผู้ใช้มองเห็น หากคุณละเว้นความกว้าง/ความสูง Word จะกำหนดขนาดเริ่มต้นซึ่งอาจไม่ตรงกับการออกแบบของคุณ

### เคล็ดลับพิเศษ
หากคุณวางแผนเพิ่มหลายคอนโทรล ให้เรียก `builder.moveToDocumentEnd()` ก่อนการแทรกแต่ละครั้งเพื่อหลีกเลี่ยงการทับซ้อนของอ็อบเจ็กต์

## ขั้นตอนที่ 5: บันทึกเอกสารพร้อมปุ่มคำสั่งที่ฝังไว้

สุดท้าย เขียนเอกสารลงดิสก์ ส่วนขยายไฟล์ต้องเป็น `.docx` (หรือ `.doc` สำหรับเวอร์ชัน Word เก่า) เพื่อรักษาคอนโทรล ActiveX

```java
// Step 5: Save the document with the embedded command button
String outputPath = "C:/temp/CommandButton.docx";
doc.save(outputPath);
System.out.println("Document saved to: " + outputPath);
```

เมื่อคุณเปิด `CommandButton.docx` ใน Microsoft Word คุณจะเห็นปุ่มที่มีป้าย **Click Me** การคลิกจะเรียกการทำงานเริ่มต้นของ ActiveX (ซึ่งโดยค่าเริ่มต้นไม่มีการทำอะไร) คุณสามารถต่อมาแนบมาโครหรือสคริปต์ VBA เพื่อกำหนดพฤติกรรมแบบกำหนดเอง

## วิธีแทรกปุ่มคำสั่งลงในฟอร์มที่มีอยู่ (ทางเลือก)

หากคุณมีฟอร์มที่มีฟิลด์ข้อความอยู่แล้วและต้องการ **สร้างฟอร์มโต้ตอบ** ที่รวมปุ่มด้วย ให้ทำตามขั้นตอนเพิ่มเติมต่อไปนี้:

1. โหลดเอกสารที่มีอยู่: `Document doc = new Document("ExistingForm.docx");`
2. ย้าย builder ไปยังตำแหน่งที่ต้องการ: `builder.moveToParagraph(5, 0); // ย่อหน้า 6, โหนดแรก`
3. แทรกปุ่มตามที่แสดงในขั้นตอนที่ 3.
4. ปรับ `Top`/`Left` ของปุ่มตามการจัดวางของย่อหน้า.

วิธีนี้ทำให้คุณสามารถเพิ่มปุ่ม ActiveX ลงในเทมเพลต Word ที่สร้างไว้ล่วงหน้าโดยไม่ต้องสร้างไฟล์ใหม่ทั้งหมด

## กรณีขอบและการแก้ไขปัญหา

| สถานการณ์ | สิ่งที่ต้องตรวจสอบ | วิธีแก้แนะนำ |
|-----------|-------------------|-----------------|
| ปุ่มไม่ปรากฏใน Word | ตรวจสอบว่าคุณเปิดไฟล์ในเวอร์ชันเดสก์ท็อปของ Word (Word Online จะลบ ActiveX) | เปิดไฟล์ใน Word 2016+ เวอร์ชันเดสก์ท็อป |
| คำบรรยายถูกตัด | ตรวจสอบว่าความกว้างของปุ่มเพียงพอที่จะบรรจุข้อความ | เพิ่ม `setWidth` จนกว่าคำบรรยายจะพอดี |
| การบันทึกโยน `IOException` | ยืนยันว่าไดเรกทอรีปลายทางมีอยู่และคุณมีสิทธิ์เขียน | สร้างไดเรกทอรีหรือรันโปรแกรมด้วยสิทธิ์ระดับสูง |
| หลายปุ่มทับซ้อนกัน | เคอร์เซอร์ของ builder อาจไม่ได้ย้ายหลังจากการแทรกก่อนหน้า | เรียก `builder.moveToDocumentEnd()` ก่อนแทรกคอนโทรลใหม่แต่ละอัน |

## ตัวอย่างที่สามารถรันได้เต็มรูปแบบ

ด้านล่างเป็นโปรแกรม Java ที่สมบูรณ์และเป็นอิสระที่คุณสามารถคัดลอก, คอมไพล์, และรันได้ มันสาธิต **สร้างเอกสารเปล่า**, **เพิ่มปุ่ม activex**, และ **บันทึกเอกสาร Word** ในขั้นตอนเดียว

```java
import com.aspose.words.*;

public class CommandButtonDemo {
    public static void main(String[] args) {
        try {
            // 1. Create a new blank document
            Document doc = new Document();

            // 2. Initialize DocumentBuilder
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 3. Insert an ActiveX command button
            Forms2OleControl commandButton = builder.insertForms2OleControl(OleControlType.COMMANDBUTTON);

            // 4. Configure button properties
            commandButton.setCaption("Click Me");
            commandButton.setTop(100);   // points from top
            commandButton.setLeft(100);  // points from left
            commandButton.setWidth(120);
            commandButton.setHeight(30);

            // 5. Save the document
            String outPath = "CommandButton.docx";
            doc.save(outPath);
            System.out.println("Document created: " + outPath);
        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}
```

**ผลลัพธ์ที่คาดหวัง**

```
Document created: CommandButton.docx
```

การเปิด `CommandButton.docx` จะเห็นหน้าเดียวที่มีปุ่มที่มีป้าย **Click Me** อยู่ห่างจากขอบบนและซ้าย 100 pt

## สรุป

ตอนนี้คุณรู้วิธี **สร้างเอกสารเปล่า**, ฝัง **ปุ่ม ActiveX**, และเปลี่ยนไฟล์ Word ธรรมดาให้เป็น **แบบฟอร์มโต้ตอบ** ด้วยการเชี่ยวชาญ **วิธีแทรกปุ่มคำสั่ง** คุณสามารถขยายรูปแบบนี้เพื่อเพิ่มเช็คบ็อกซ์, คอมโบบ็อกซ์, หรือแม้กระทั่งตรรกะที่ขับเคลื่อนด้วย VBA แบบกำหนดเอง

ต่อไป, พิจารณาการสำรวจหัวข้อที่เกี่ยวข้องต่อไปนี้:

* **สร้างแบบฟอร์มโต้ตอบ** ด้วยฟิลด์ข้อความ (`builder.insertField`)  
* **เพิ่มปุ่ม activex** ที่รันมาโคร VBA (`builder.insertOleObject`)  
* **สร้างเอกสาร Word** จากเทมเพลตโดยใช้ `Document(docTemplatePath)`  
* แปลง .docx ที่ได้เป็น PDF พร้อมคงปุ่มไว้ (หมายเหตุ: PDF จะเรนเดอร์ปุ่มเป็นภาพคงที่)

คุณสามารถทดลองปรับขนาดปุ่ม, ตำแหน่ง, และคำบรรยายให้ตรงกับการออกแบบ UI ของคุณได้อย่างอิสระ ขอให้สนุกกับการเขียนโค้ด!

## สิ่งที่คุณควรเรียนต่อไป?

บทแนะนำต่อไปนี้ครอบคลุมหัวข้อที่เกี่ยวข้องอย่างใกล้ชิดซึ่งต่อยอดจากเทคนิคที่แสดงในคู่มือนี้ แต่ละแหล่งข้อมูลมีตัวอย่างโค้ดทำงานเต็มรูปแบบพร้อมคำอธิบายทีละขั้นตอนเพื่อช่วยให้คุณเชี่ยวชาญฟีเจอร์ API เพิ่มเติมและสำรวจแนวทางการนำไปใช้แบบอื่นในโครงการของคุณ

- [วิธีสร้างฟิลด์ฟอร์มและเพิ่มเนื้อหาโดยใช้ DocumentBuilder ใน Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [สร้างโครงการ Vba ในเอกสาร Word](/words/english/net/working-with-vba-macros/create-vba-project/)
- [สร้างเอกสาร Word ใหม่](/words/english/net/add-content-using-documentbuilder/create-new-document/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}