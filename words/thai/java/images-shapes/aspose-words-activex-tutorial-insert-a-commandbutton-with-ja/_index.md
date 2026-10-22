---
category: general
date: 2026-08-07
description: บทแนะนำ Aspose.Words ActiveX แสดงวิธีเพิ่มควบคุม CommandButton ลงในเอกสาร
  Word ด้วย Java. เรียนรู้โค้ดเต็ม, การกำหนดค่า และขั้นตอนการบันทึก.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- aspose words activex tutorial
- aspose.words java
- activeX control java
- documentbuilder insert control
- forms2olecontrol usage
language: th
lastmod: 2026-08-07
og_description: บทแนะนำ Aspose.Words ActiveX อธิบายวิธีฝังควบคุม CommandButton ActiveX
  ลงในเอกสาร Word ด้วย Java ทำตามตัวอย่างเต็มเพื่อสร้าง กำหนดค่า และบันทึกเอกสาร
og_image_alt: Screenshot of a Word document with a CommandButton added via Aspose.Words
  ActiveX tutorial
og_title: บทแนะนำ Aspose.Words ActiveX – คู่มือขั้นตอนโดยขั้นตอนสำหรับ Java
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: Aspose.Words ActiveX tutorial shows how to add a CommandButton control
    to a Word document using Java. Learn the full code, configuration, and saving
    steps.
  headline: Aspose.Words ActiveX tutorial – insert a CommandButton with Java
  type: TechArticle
- description: Aspose.Words ActiveX tutorial shows how to add a CommandButton control
    to a Word document using Java. Learn the full code, configuration, and saving
    steps.
  name: Aspose.Words ActiveX tutorial – insert a CommandButton with Java
  steps:
  - name: Initialize a `Document` and `DocumentBuilder`.
    text: Initialize a `Document` and `DocumentBuilder`.
  - name: Insert a `Forms2OleControl` of type `COMMAND_BUTTON`.
    text: Insert a `Forms2OleControl` of type `COMMAND_BUTTON`.
  - name: Set the button’s name, caption, size, and position.
    text: Set the button’s name, caption, size, and position.
  - name: Save the document as a .docx file that contains the ActiveX control.
    text: Save the document as a .docx file that contains the ActiveX control.
  type: HowTo
tags:
- Aspose.Words
- Java
- ActiveX
title: บทเรียน Aspose.Words ActiveX – แทรกปุ่มคำสั่งด้วย Java
url: /th/java/images-shapes/aspose-words-activex-tutorial-insert-a-commandbutton-with-ja/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words ActiveX tutorial – insert a CommandButton with Java

หากคุณต้องการฝัง ActiveX control ลงในไฟล์ Word, **Aspose.Words ActiveX tutorial** นี้จะพาคุณผ่านขั้นตอนทั้งหมด คุณจะได้เห็นวิธีสร้างเอกสารเปล่า, แทรก CommandButton, ตั้งค่าคุณสมบัติต่าง ๆ และบันทึกผลลัพธ์—ทั้งหมดด้วยโค้ด Java ธรรมดา

ตัวอย่างใช้ Aspose.Words for Java API ซึ่งทำให้ไม่จำเป็นต้องมี Microsoft Office บนเซิร์ฟเวอร์ที่ทำการคอมไพล์ เมื่อจบคู่มือคุณจะสามารถสร้างไฟล์ .docx ที่มี CommandButton ทำงานเต็มรูปแบบพร้อมใช้งานในสภาพแวดล้อม Windows

## Prerequisites

ก่อนเริ่มทำงาน ให้ตรวจสอบว่าคุณมี:

- Java Development Kit (JDK) 8 หรือใหม่กว่า
- Maven หรือเครื่องมือ build อื่น ๆ เพื่อจัดการ dependencies
- ใบอนุญาต Aspose.Words for Java (หรือคีย์ประเมินผลชั่วคราว) เพื่อหลีกเลี่ยงลายน้ำการประเมิน
- ความคุ้นเคยพื้นฐานกับไวยากรณ์ Java และการเขียนโปรแกรมเชิงวัตถุ

> **Pro tip:** เพิ่ม dependency ของ Aspose.Words ในไฟล์ `pom.xml` ของคุณเพื่อให้ IDE สามารถ resolve คลาสได้อัตโนมัติ:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.10</version> <!-- Use the latest version -->
</dependency>
```

## Step 1: Create a new blank document and a `DocumentBuilder`

คลาส `Document` แทนไฟล์ Word ในหน่วยความจำ ส่วน `DocumentBuilder` ให้ API แบบ fluent สำหรับแก้ไขเอกสาร การสร้างอ็อบเจกต์ทั้งสองนี้เตรียมเอกสารสำหรับการแก้ไขต่อไป

```java
import com.aspose.words.*;

public class ActiveXDemo {
    public static void main(String[] args) throws Exception {
        // Create an empty Word document
        Document document = new Document();

        // DocumentBuilder lets you add text, tables, and controls
        DocumentBuilder builder = new DocumentBuilder(document);
```

**Why this matters:**  
`DocumentBuilder` จะติดตามตำแหน่งเคอร์เซอร์ปัจจุบัน ดังนั้นการแทรกใด ๆ ที่ตามมา—เช่นการเพิ่ม control—จะปรากฏตรงตำแหน่งที่คุณต้องการ

## Step 2: Insert a CommandButton ActiveX control

Aspose.Words เปิดเผย `Forms2OleControl` สำหรับอ็อบเจกต์ ActiveX วิธี `insertForms2OleControl` ต้องการประเภทของ control ซึ่งคุณระบุผ่าน enumeration `Forms2OleControlType`

```java
        // Insert a CommandButton ActiveX control at the current cursor location
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMAND_BUTTON);
```

**Explanation:**  
Control ที่แทรกเป็นอ็อบเจกต์แบบ COM ที่ Word จะเรนเดอร์เป็นปุ่มที่คลิกได้เมื่อเปิดเอกสารในสภาพแวดล้อม Windows

## Step 3: Configure the button’s properties

หลังจากแทรกแล้ว คุณสามารถปรับชื่อ, คำบรรยาย, ขนาดและตำแหน่งของปุ่มได้ คุณสมบัติเหล่านี้ส่งผลต่อการแสดงผลและพฤติกรรมของ control ภายใน Word

```java
        // Set the logical name used by VBA or external scripts
        commandButton.setName("cmdSubmit");

        // Text displayed on the button face
        commandButton.setCaption("Submit");

        // Position the button 100 points from the left margin and 150 points from the top
        commandButton.setLeft(100);
        commandButton.setTop(150);

        // Define the button’s dimensions (width × height) in points
        commandButton.setWidth(80);
        commandButton.setHeight(30);
```

**Why these settings are important:**  

- **Name** – ทำให้ VBA macro สามารถอ้างอิง control ได้ (`ActiveDocument.Forms("cmdSubmit")`)  
- **Caption** – กำหนดข้อความที่ผู้ใช้เห็นและคลิก  
- **Left / Top** – ควบคุมการวางตำแหน่งสัมพันธ์กับขอบกระดาษ  
- **Width / Height** – รับประกันขนาดภาพที่สม่ำเสมอบนหน้าจอความละเอียดต่าง ๆ  

## Step 4: Save the document

การเรียก `save` จะเขียนข้อมูลในหน่วยความจำลงไฟล์จริง คุณสามารถเลือกฟอร์แมตที่รองรับได้ทุกแบบ (`.docx`, `.doc`, `.pdf` ฯลฯ) สำหรับบทเรียนนี้เราจะเก็บเป็นฟอร์แมต Word ดั้งเดิม

```java
        // Persist the document with the embedded ActiveX control
        document.save("output/ActiveXDemo.docx");
    }
}
```

**Result:**  
การเปิดไฟล์ `ActiveXDemo.docx` ใน Microsoft Word จะแสดง CommandButton ที่มีข้อความ **Submit** อยู่ในพิกัดที่กำหนด การคลิกปุ่มจะทำพฤติกรรมเริ่มต้น (ไม่มีโค้ด VBA แนบมาโดยอัตโนมัติ)

## Full source code

เมื่อนำส่วนต่าง ๆ มารวมกัน โปรแกรมที่ทำงานได้เต็มรูปแบบจะมีลักษณะดังนี้:

```java
import com.aspose.words.*;
import com.aspose.words.forms.*;

public class ActiveXDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document and a DocumentBuilder
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Step 2: Insert a CommandButton ActiveX control
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMAND_BUTTON);

        // Step 3: Configure the button's properties
        commandButton.setName("cmdSubmit");
        commandButton.setCaption("Submit");
        commandButton.setLeft(100);
        commandButton.setTop(150);
        commandButton.setWidth(80);
        commandButton.setHeight(30);

        // Step 4: Save the document with the ActiveX control
        document.save("output/ActiveXDemo.docx");
    }
}
```

### Expected output

- ไฟล์ชื่อ **ActiveXDemo.docx** อยู่ในโฟลเดอร์ `output`  
- เมื่อเปิดใน Microsoft Word (Windows) เอกสารจะแสดงปุ่ม **Submit** ที่คลิกได้ตามตำแหน่งที่กำหนด  
- ปุ่มสามารถเลือก, ย้ายตำแหน่ง หรือเชื่อมโยงกับโค้ด VBA ผ่าน UI ของ Word (Developer → Properties)

## Handling common variations

| Scenario | Adjustment |
|----------|------------|
| **Save as .doc** (legacy format) | `document.save("ActiveXDemo.doc", SaveFormat.DOC);` |
| **Add an event handler** | Word ไม่เปิดเผยเหตุการณ์ ActiveX ผ่าน Aspose.Words คุณต้องเพิ่มโค้ด VBA ด้วยตนเองหลังจากสร้างเอกสาร |
| **Multiple controls** | ทำซ้ำบล็อก insert/configure พร้อมค่า `setName` และ `setCaption` ที่แตกต่างกัน |
| **Different control type (e.g., CheckBox)** | ใช้ `Forms2OleControlType.CHECKBOX` ในการเรียก `insertForms2OleControl` |
| **Non‑Windows platforms** | ActiveX control จะเรนเดอร์ได้เฉพาะบน Word ของ Windows สำหรับโซลูชันข้ามแพลตฟอร์ม ให้พิจารณาใช้ content controls (`StructuredDocumentTag`) |

## Best practices and pitfalls

- **License early** – ลงทะเบียนใบอนุญาต Aspose.Words ก่อนสร้าง `Document` เพื่อหลีกเลี่ยงข้อความแจ้งการประเมิน  
- **Coordinate system** – ตำแหน่งวัดเป็นจุด (1 pt = 1/72 in) หาก UI ของคุณออกแบบเป็นพิกเซลหรือเซนติเมตรต้องทำการแปลงค่า  
- **File paths** – ใช้เส้นทางแบบ absolute หรือ API `Paths` ของ Java เพื่อป้องกัน `FileNotFoundException` เมื่อโฟลเดอร์ปลายทางไม่มีอยู่  
- **Thread safety** – `Document` และ `DocumentBuilder` ไม่ปลอดภัยต่อหลายเธรด สร้างอินสแตนซ์แยกสำหรับแต่ละเธรดหากต้องการสร้างเอกสารแบบขนาน  
- **Testing** – ตรวจสอบเอกสารที่สร้างบนเวอร์ชัน Word ที่เป้าหมาย (เช่น Word 2016, Word 365) เนื่องจากบางเวอร์ชันอาจแสดง ActiveX control แตกต่างกัน  

## Conclusion

**Aspose.Words ActiveX tutorial** นี้แสดงวิธีเพิ่ม CommandButton control ลงในเอกสาร Word ด้วย Java คุณได้เรียนรู้วิธี:

1. เริ่มต้น `Document` และ `DocumentBuilder`  
2. แทรก `Forms2OleControl` ประเภท `COMMAND_BUTTON`  
3. ตั้งค่าชื่อ, คำบรรยาย, ขนาดและตำแหน่งของปุ่ม  
4. บันทึกเอกสารเป็นไฟล์ .docx ที่มี ActiveX control อยู่ภายใน  

ต่อจากนี้คุณสามารถสำรวจประเภท control เพิ่มเติม, ทำการแทรก VBA macro อัตโนมัติ, หรือผสาน ActiveX control กับคุณลักษณะอื่นของ Aspose.Words เช่น mail‑merge และ content controls ทดลองปรับแต่งเลย์เอาต์ต่าง ๆ และผสานเอกสารที่สร้างเข้ากับ pipeline การรายงานที่พัฒนาด้วย Java ของคุณ

---


## What Should You Learn Next?


บทเรียนต่อไปนี้ครอบคลุมหัวข้อที่เกี่ยวข้องอย่างใกล้ชิดและต่อยอดจากเทคนิคที่แสดงในคู่มือนี้ แต่ละแหล่งข้อมูลมาพร้อมตัวอย่างโค้ดทำงานเต็มรูปแบบพร้อมคำอธิบายทีละขั้นตอน เพื่อช่วยให้คุณเชี่ยวชาญฟีเจอร์ API เพิ่มเติมและสำรวจแนวทางการทำงานแบบต่าง ๆ ในโครงการของคุณ

- [Using OLE Objects and ActiveX Controls in Aspose.Words for Java](/words/english/java/using-document-elements/using-ole-objects-and-activex/)
- [How to create form fields and add content using DocumentBuilder in Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Convert Word to RTF with Aspose.Words for Java Tutorial](/words/english/java/document-loading-and-saving/saving-documents-as-rtf-format/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}