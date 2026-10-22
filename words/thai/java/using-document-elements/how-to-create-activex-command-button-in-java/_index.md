---
category: general
date: 2026-10-07
description: สร้างปุ่มคำสั่ง ActiveX ใน Java และเพิ่มปุ่มคำสั่งลงในเอกสาร Word อย่างโปรแกรมมิ่ง
  เรียนรู้วิธีตั้งตำแหน่งซ้ายบนของปุ่ม
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create activex command button
- programmatically add command button
- how to set button left top
language: th
lastmod: 2026-10-07
og_description: สร้างปุ่มคำสั่ง ActiveX ด้วย Java เพื่อฝังการควบคุมแบบโต้ตอบในเอกสาร
  Word ของคุณ เรียนรู้วิธีเพิ่มปุ่มคำสั่งโดยโปรแกรม ตั้งตำแหน่งของมัน และปรับแต่งลักษณะการแสดงผล
og_image_alt: Screenshot showing a created ActiveX command button in a Java‑generated
  Word document
og_title: สร้างปุ่มคำสั่ง ActiveX ใน Java – คู่มือขั้นตอนโดยละเอียด
schemas:
- author: Aspose
  dateModified: '2026-10-07'
  description: Create ActiveX command button in Java and programmatically add command
    button to Word docs. Learn how to set button left top positions.
  headline: How to create ActiveX command button in Java
  type: TechArticle
- description: Create ActiveX command button in Java and programmatically add command
    button to Word docs. Learn how to set button left top positions.
  name: How to create ActiveX command button in Java
  steps:
  - name: How to set button left top
    text: Positioning the button is where the secondary keyword **how to set button
      left top** becomes relevant. The `setLeft` and `setTop` methods accept values
      measured in points (1 point = 1/72 in).
  - name: Adding multiple buttons
    text: If you need several buttons, repeat **Step 2** and **Step 3** for each control.
      Remember to adjust `setLeft` and `setTop` so the buttons don’t overlap.
  - name: Changing button behavior
    text: 'ActiveX buttons can run VBA macros when clicked. To attach a macro, set
      the `setOnAction` property with the macro name:'
  - name: Compatibility notes
    text: '- The button works only in desktop versions of Word that support ActiveX
      (e.g., Word for Windows). It will appear as a static image in Word for Mac or
      online editors. - If you target a mixed environment, consider using a **content
      control** (`RichTextContentControl`) instead of an ActiveX control.'
  - name: Next steps
    text: '- Explore other ActiveX controls such as `Forms.TextBox.1` or `Forms.CheckBox.1`.
      - Combine multiple controls with a VBA module to implement full‑featured forms.
      - Replace ActiveX with content controls if you need cross‑platform compatibility.'
  type: HowTo
tags:
- ActiveX
- Java
- Aspose.Words
title: วิธีสร้างปุ่มคำสั่ง ActiveX ใน Java
url: /th/java/using-document-elements/how-to-create-activex-command-button-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# วิธีสร้างปุ่มคำสั่ง ActiveX ใน Java

หากคุณต้องการ **สร้างปุ่มคำสั่ง ActiveX** ในเอกสาร Word ด้วย Java คู่มือนี้จะแสดงให้คุณเห็นอย่างละเอียด คุณจะได้เห็นตัวอย่างที่สมบูรณ์และสามารถรันได้ที่ **เพิ่มปุ่มคำสั่งโดยโปรแกรม** ตั้งตำแหน่งด้วย `setLeft` และ `setTop` และบันทึกผลลัพธ์เป็นไฟล์ `.docx`

การฝังปุ่มเชิงโต้ตอบช่วยให้คุณสร้างฟอร์ม, ทำงานอัตโนมัติ, หรือเก็บข้อมูลผู้ใช้โดยตรงภายในไฟล์ Word ขั้นตอนต่อไปนี้ครอบคลุมทุกอย่างตั้งแต่การตั้งค่าโครงการจนถึงการตรวจสอบขั้นสุดท้าย เพื่อให้คุณสามารถคัดลอกโค้ดไปยังโครงการของคุณได้โดยไม่พลาดรายละเอียดใด ๆ

## ข้อกำหนดเบื้องต้น

- JDK 17 หรือใหม่กว่า ติดตั้งแล้ว  
- Maven 3.8+ (หรือเครื่องมือสร้างที่คุณต้องการ)  
- Aspose.Words for Java 23.9 หรือใหม่กว่า – ไลบรารีที่ให้ `DocumentBuilder` และการสนับสนุน OLE control  
- ความคุ้นเคยพื้นฐานกับไวยากรณ์ Java และแนวคิดเชิงวัตถุ  

หากคุณใช้ Maven ให้เพิ่ม dependency ลงในไฟล์ `pom.xml` ของคุณ:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
    <classifier>jdk17</classifier>
</dependency>
```

> **เคล็ดลับ:** ใช้เวอร์ชันล่าสุดของ Aspose.Words เพื่อรับประโยชน์จากการแก้ไขบั๊กและคุณสมบัติ OLE ใหม่

## ขั้นตอนที่ 1: สร้างเอกสารเปล่าใหม่และ DocumentBuilder

ขั้นตอนแรกในการ **สร้างปุ่มคำสั่ง ActiveX** คือการสร้างอินสแตนซ์ของ `Document` ว่างและ `DocumentBuilder` ตัวสร้างนี้ให้ API ที่ไหลลื่นสำหรับแทรกเนื้อหา รวมถึง OLE control

```java
import com.aspose.words.*;

public class ActiveXButtonDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new empty document and a DocumentBuilder to work with it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

`Document` แทนไฟล์ Word ในหน่วยความจำ ในขณะที่ `DocumentBuilder` ทำหน้าที่เป็นเคอร์เซอร์ที่ให้คุณวางองค์ประกอบได้อย่างแม่นยำตามที่ต้องการ

## ขั้นตอนที่ 2: แทรก OLE command button control

ActiveX control จะถูกแทรกเป็น OLE object Aspose.Words มีคลาส `Forms2OleControl` สำหรับจุดประสงค์นี้

```java
        // Step 2: Insert an OLE command button control into the document
        Forms2OleControl commandButton = builder.insertForms2OleControl();
```

เมื่อคุณเรียก `insertForms2OleControl()` Aspose จะสร้างรูปทรง placeholder โดยอัตโนมัติที่ใช้เป็นโฮสต์สำหรับปุ่ม ActiveX

## ขั้นตอนที่ 3: กำหนดคุณสมบัติของปุ่ม

ตอนนี้คุณ **เพิ่มปุ่มคำสั่งโดยโปรแกรม** รายละเอียดเช่น ProgID, caption, และขนาด ProgID ที่พบบ่อยที่สุดสำหรับปุ่มคำสั่งคือ `"Forms.CommandButton.1"`

```java
        // Step 3: Configure the button's properties (type, position, size, caption)
        commandButton.setProgId("Forms.CommandButton.1"); // ActiveX class identifier
        commandButton.setCaption("Click Me");            // Text shown on the button
        commandButton.setWidth(80);                      // Width in points
        commandButton.setHeight(30);                     // Height in points
```

### วิธีตั้งค่าตำแหน่งซ้ายบนของปุ่ม

การกำหนดตำแหน่งของปุ่มคือจุดที่คีย์เวิร์ดรอง **how to set button left top** มีความสำคัญ วิธี `setLeft` และ `setTop` รับค่าที่วัดเป็นจุด (1 point = 1/72 in).

```java
        // Position the button 100 points from the left margin and 150 points from the top
        commandButton.setLeft(100);   // Horizontal offset
        commandButton.setTop(150);    // Vertical offset
```

ปรับตัวเลขเหล่านี้ให้เข้ากับการจัดวางของคุณ ตัวอย่างเช่น เพื่อจัดตำแหน่งปุ่มให้ตรงกับเซลล์ตาราง ให้คำนวณพิกัดของเซลล์และส่งค่าไปยัง `setLeft`/`setTop`

## ขั้นตอนที่ 4: บันทึกเอกสาร

สุดท้าย เขียนเอกสารลงดิสก์ ไฟล์จะมีปุ่ม ActiveX พร้อมใช้งานเมื่อเปิดใน Microsoft Word

```java
        // Step 4: Save the document containing the button
        doc.save("CommandButton.docx");
        System.out.println("Document saved successfully.");
    }
}
```

การเรียกใช้เมธอด `main` จะสร้างไฟล์ `CommandButton.docx` เปิดไฟล์ใน Word หากมีการแจ้งให้เปิดใช้งานเนื้อหา ให้ทำเช่นนั้น แล้วคุณจะเห็นปุ่มที่คลิกได้ที่มีป้าย **Click Me** อยู่ในตำแหน่งที่คุณระบุ

![สร้างปุ่มคำสั่ง ActiveX ใน Java](/images/activex-button-screenshot.png){.center width=600 alt="ภาพหน้าจอการสร้างปุ่มคำสั่ง ActiveX ใน Java แสดงปุ่มภายในเอกสาร Word"}

## ความแปรผันทั่วไปและกรณีขอบ

### การเพิ่มหลายปุ่ม

หากคุณต้องการหลายปุ่ม ให้ทำซ้ำ **ขั้นตอน 2** และ **ขั้นตอน 3** สำหรับแต่ละคอนโทรล อย่าลืมปรับ `setLeft` และ `setTop` เพื่อไม่ให้ปุ่มทับกัน

### การเปลี่ยนพฤติกรรมของปุ่ม

ปุ่ม ActiveX สามารถเรียกใช้ VBA macro เมื่อคลิกได้ เพื่อแนบ macro ให้ตั้งค่า property `setOnAction` ด้วยชื่อ macro:

```java
commandButton.setOnAction("MyMacro");
```

ตรวจสอบให้แน่ใจว่าเอกสารเป้าหมายมีโมดูล VBA ที่สอดคล้องกัน; หากไม่เช่นนั้น Word จะแสดงข้อผิดพลาด

### หมายเหตุเรื่องความเข้ากันได้

- ปุ่มทำงานได้เฉพาะในเวอร์ชันเดสก์ท็อปของ Word ที่สนับสนุน ActiveX (เช่น Word for Windows) จะปรากฏเป็นภาพคงที่ใน Word for Mac หรือในโปรแกรมแก้ไขออนไลน์  
- หากคุณมุ่งเป้าไปยังสภาพแวดล้อมแบบผสม ควรพิจารณาใช้ **content control** (`RichTextContentControl`) แทน ActiveX control  

## โค้ดต้นฉบับเต็มสำหรับอ้างอิง

ด้านล่างเป็นตัวอย่างครบถ้วนและอิสระที่คุณสามารถคัดลอกไปยังโครงการ Maven ใหม่และรันได้ทันที

```java
import com.aspose.words.*;

public class ActiveXButtonDemo {
    public static void main(String[] args) throws Exception {
        // Create a new empty document and a DocumentBuilder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert an OLE command button control
        Forms2OleControl commandButton = builder.insertForms2OleControl();

        // Configure the button
        commandButton.setProgId("Forms.CommandButton.1");
        commandButton.setCaption("Click Me");
        commandButton.setWidth(80);
        commandButton.setHeight(30);

        // How to set button left top – position the control
        commandButton.setLeft(100);   // Horizontal offset in points
        commandButton.setTop(150);    // Vertical offset in points

        // Save the resulting document
        doc.save("CommandButton.docx");
        System.out.println("Document saved successfully.");
    }
}
```

**ผลลัพธ์ที่คาดหวัง:** หลังจากรัน คุณจะพบไฟล์ `CommandButton.docx` ในไดเรกทอรีทำงานของโครงการของคุณ การเปิดไฟล์ใน Microsoft Word จะแสดงปุ่มที่ตำแหน่งที่ระบุพร้อม caption “Click Me”.

## สรุป

ตอนนี้คุณรู้วิธี **สร้างปุ่มคำสั่ง ActiveX** ใน Java, **เพิ่มปุ่มคำสั่งโดยโปรแกรม** ลงในเอกสาร Word, และควบคุมการจัดวางอย่างแม่นยำด้วยวิธี **how to set button left top** เทคนิคนี้เปิดประตูสู่ฟอร์ม Word เชิงโต้ตอบที่สามารถเรียกใช้ macro, เปิดแอปพลิเคชันภายนอก, หรือเก็บข้อมูลผู้ใช้โดยตรงภายในเอกสาร

### ขั้นตอนต่อไป

- สำรวจ ActiveX control อื่น ๆ เช่น `Forms.TextBox.1` หรือ `Forms.CheckBox.1`  
- รวมหลายคอนโทรลกับโมดูล VBA เพื่อสร้างฟอร์มที่ครบถ้วน  
- แทนที่ ActiveX ด้วย content control หากคุณต้องการความเข้ากันได้ข้ามแพลตฟอร์ม  

อย่าลังเลที่จะทดลองปรับขนาด, caption, และตำแหน่งให้ตรงกับการออกแบบ UI ของคุณ หากพบปัญหา ให้ตรวจสอบอีกครั้งว่าเวอร์ชัน Aspose.Words ที่คุณใช้สนับสนุน OLE control หรือไม่ และตรวจสอบการตั้งค่าความปลอดภัยของ Word ว่าอนุญาตให้ทำงานกับ ActiveX หรือไม่ ขอให้สนุกกับการเขียนโค้ด!

## คุณควรเรียนรู้อะไรต่อไป?

บทแนะนำต่อไปนี้ครอบคลุมหัวข้อที่เกี่ยวข้องอย่างใกล้ชิดซึ่งต่อยอดจากเทคนิคที่แสดงในคู่มือนี้ แต่ละแหล่งข้อมูลมีตัวอย่างโค้ดทำงานเต็มรูปแบบพร้อมคำอธิบายทีละขั้นตอนเพื่อช่วยให้คุณเชี่ยวชาญฟีเจอร์ API เพิ่มเติมและสำรวจแนวทางการทำงานทางเลือกในโครงการของคุณ

- [ฝัง OLE Objects และ ActiveX Controls ในเอกสาร Word](/words/english/python-net/document-structure-and-content-manipulation/document-ole-objects-active-x/)
- [วิธีสร้างฟิลด์ฟอร์มและเพิ่มเนื้อหาโดยใช้ DocumentBuilder ใน Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [สร้างรูปสี่เหลี่ยมใน Word ด้วย Java – คู่มือเต็ม](/words/english/java/images-shapes/create-rectangle-shape-in-word-with-java-full-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}