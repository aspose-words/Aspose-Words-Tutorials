---
category: general
date: 2026-07-29
description: 'สอนการตั้งขนาดปุ่มใน Java: เรียนรู้วิธีแทรกปุ่มคำสั่ง ActiveX ในเอกสาร
  Word ด้วย Java และ Aspose.Words รวมถึงการกำหนดขนาดและการสร้างเอกสารเปล่า'
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- set button size java
- how to insert activex
- how to set button
- java create blank word
- insert command button word
language: th
lastmod: 2026-07-29
og_description: คู่มือการตั้งขนาดปุ่มใน Java แสดงวิธีแทรกปุ่มคำสั่ง ActiveX ลงในไฟล์
  Word ด้วย Java ปรับขนาดของปุ่ม และบันทึกเอกสารโดยอัตโนมัติ
og_image_alt: set button size java example showing a Word document with an ActiveX
  command button
og_title: ตั้งค่าขนาดปุ่ม Java – เพิ่มปุ่มคำสั่ง ActiveX ไปยัง Word ด้วย Java
schemas:
- author: Aspose
  dateModified: '2026-07-29'
  description: 'set button size java tutorial: learn how to insert ActiveX command
    button in a Word document using Java and Aspose.Words, plus sizing and blank document
    creation.'
  headline: set button size java – Insert ActiveX Command Button in Word
  type: TechArticle
- description: 'set button size java tutorial: learn how to insert ActiveX command
    button in a Word document using Java and Aspose.Words, plus sizing and blank document
    creation.'
  name: set button size java – Insert ActiveX Command Button in Word
  steps:
  - name: 1. Set Up the Project and Import Aspose.Words
    text: 'First, create a new Maven (or Gradle) project and add the Aspose.Words
      dependency shown above. Then, import the required classes in your Java source
      file:'
  - name: 2. java create blank word Document
    text: Now we actually **java create blank word** document. This is the foundation
      on which we’ll later **insert command button word**.
  - name: 3. Initialize DocumentBuilder and Insert the ActiveX Control
    text: 'The `DocumentBuilder` is a helper that lets us add content, paragraphs,
      tables, and, yes, ActiveX controls. Here’s where we answer **how to insert activex**:'
  - name: 4. How to Set Button Size Java – Adjust Width and Height
    text: 'Now comes the heart of the tutorial: **how to set button size java**. The
      control exposes several layout properties—`Left`, `Top`, `Width`, and `Height`.
      Setting them directly controls the button’s appearance on the page.'
  - name: 5. Save the Document
    text: 'Finally, persist the document to disk:'
  - name: What if the button doesn’t appear in Word?
    text: '- **Check the Word version.** ActiveX controls require the desktop version
      of Word; Word Online strips them out. - **Make sure the Aspose.Words license
      is applied** (if you’re using a paid edition). An unlicensed evaluation version
      may embed a watermark but still shows the control.'
  - name: Can I change the button’s font or color?
    text: Yes. After inserting the control, you can access its underlying OLE object
      and manipulate the VBA properties. That’s a more advanced topic—look into `commandButton.getOleObject().setProperty("ForeColor",
      0xFF0000)` for a red caption, for example.
  - name: How do I handle the button’s click event?
    text: ActiveX command buttons fire a VBA `Click` event. To make the button functional,
      you’ll need to embed a macro in the same document. Aspose.Words can add a macro
      module via the `Document.getMacros()` API, but the macro code itself must be
      written in VBA.
  - name: What about different button types?
    text: 'Aspose.Words supports many `Forms2OleControlType` values: `CHECKBOX`, `OPTIONBUTTON`,
      `LISTBOX`, etc. Swap the enum constant in the `insertForms2OleControl` call
      to experiment.'
  type: HowTo
tags:
- Java
- Aspose.Words
- ActiveX
- Word Automation
title: ตั้งขนาดปุ่มใน Java – แทรกปุ่มคำสั่ง ActiveX ใน Word
url: /th/java/using-document-elements/set-button-size-java-insert-activex-command-button-in-word/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# set button size java – แทรกปุ่มคำสั่ง ActiveX ใน Word

เคยสงสัย **how to set button size java** เมื่อคุณทำการอัตโนมัติเอกสาร Word หรือไม่? บางทีคุณอาจกำลังสร้างเครื่องมือรายงานที่ต้องการปุ่ม “Submit” ที่คลิกได้ภายในไฟล์ .docx. ในบทแนะนำนี้เราจะอธิบายขั้นตอนทั้งหมด—การสร้างเอกสาร Word เปล่า, การแทรกปุ่มคำสั่ง ActiveX, และการตั้งค่าความกว้างและความสูงของปุ่มอย่างชัดเจน—ทั้งหมดด้วย Java และ Aspose.Words.

เรายังจะตอบคำถามที่ค้างคา “how to insert activex” ที่หลายคนถามบ่อย. เมื่อเสร็จสิ้นคุณจะได้โปรแกรมที่รันได้ซึ่งสร้างไฟล์ Word ที่มีปุ่มคำสั่งขนาดพอดี พร้อมสำหรับการปรับแต่งต่อไป.

---

## สิ่งที่คุณต้องการ

- **Java Development Kit (JDK) 8 หรือใหม่กว่า** – โค้ดจะคอมไพล์ได้กับ JDK เวอร์ชันล่าสุดใดก็ได้.
- **Aspose.Words for Java** (เวอร์ชันล่าสุด ณ กรกฎาคม 2026). ดาวน์โหลด JAR จาก [Aspose website](https://products.aspose.com/words/java) หรือผ่าน Maven:
  ```xml
  <dependency>
      <groupId>com.aspose</groupId>
      <artifactId>aspose-words</artifactId>
      <version>23.10</version>
  </dependency>
  ```
- IDE หรือเครื่องมือแก้ไขข้อความง่าย—IntelliJ IDEA, Eclipse, หรือ VS Code ก็เพียงพอ.
- โฟลเดอร์ที่คุณต้องการให้ไฟล์ **CommandButton.docx** ที่สร้างขึ้นถูกเก็บไว้.

แค่นั้นเอง. ไม่ต้องใช้ไลบรารี Office interop เพิ่มเติม, ไม่ต้องใช้เทคนิค COM, เพียงแค่ Java ธรรมดา.

---

## การดำเนินการแบบขั้นตอน

เราจะแบ่งวิธีแก้เป็นห้าขั้นตอนที่เป็นตรรกะ. แต่ละขั้นมีหัวข้อ H2 ของตนเอง; หนึ่งในนั้นจะมี **primary keyword** ของเราเพื่อให้ SEO ครบถ้วน.

### 1. ตั้งค่าโปรเจกต์และนำเข้า Aspose.Words

เริ่มต้นด้วยการสร้างโปรเจกต์ Maven (หรือ Gradle) ใหม่และเพิ่ม dependency ของ Aspose.Words ตามที่แสดงด้านบน. จากนั้นให้ import คลาสที่จำเป็นในไฟล์ Java ของคุณ:

```java
import com.aspose.words.*;
```

> **Pro tip:** หากคุณใช้ IDE ให้ให้มันทำการ auto‑import คลาสให้เอง. จะช่วยลดการพิมพ์และป้องกันข้อผิดพลาดได้มาก.

### 2. java create blank word Document

ตอนนี้เราจะ **java create blank word** document จริง ๆ. นี่คือพื้นฐานที่เราจะใช้ต่อไปเพื่อ **insert command button word**.

```java
// Step 2: Create a new blank document
Document document = new Document();          // Starts with a clean, empty .docx
```

อ็อบเจกต์ `Document` แทนไฟล์ Word ทั้งหมดในหน่วยความจำ. ณ จุดนี้ไฟล์ยังไม่มีหน้า, ไม่มีข้อความ—เป็นเพียงแผ่นเปล่า.

### 3. เริ่มต้น DocumentBuilder และแทรก ActiveX Control

`DocumentBuilder` เป็นตัวช่วยที่ให้เราสามารถเพิ่มเนื้อหา, ย่อหน้า, ตาราง, และแน่นอนว่า ActiveX controls. ที่นี่เราจะตอบ **how to insert activex**:

```java
// Step 3: Initialize a DocumentBuilder to work with the document
DocumentBuilder builder = new DocumentBuilder(document);

// Insert an ActiveX command button (COMMANDBUTTON is a built‑in type)
Forms2OleControl commandButton = builder.insertForms2OleControl(
        Forms2OleControlType.COMMANDBUTTON);
```

`Forms2OleControl` เป็น wrapper ของ Aspose สำหรับอ็อบเจกต์ OLE. โดยระบุ `COMMANDBUTTON` เราบอก Word ให้ฝังปุ่มคำสั่ง ActiveX แบบคลาสสิก.

### 4. How to Set Button Size Java – ปรับความกว้างและความสูง

ตอนนี้มาถึงหัวใจของบทแนะนำ: **how to set button size java**. คอนโทรลนี้เปิดเผยคุณสมบัติ layout หลายอย่าง—`Left`, `Top`, `Width`, และ `Height`. การตั้งค่าเหล่านี้โดยตรงจะควบคุมลักษณะของปุ่มบนหน้า.

```java
// Step 4: Set button properties, including size
commandButton.setCaption("Click Me"); // Text shown on the button
commandButton.setLeft(100);           // Distance from the left margin (points)
commandButton.setTop(200);            // Distance from the top margin (points)
commandButton.setWidth(120);          // Width in points (≈1.67 inches)
commandButton.setHeight(30);          // Height in points (≈0.42 inches)
```

ทำไมต้องเป็นตัวเลขเหล่านี้? ใน Word หนึ่ง point เท่ากับ 1/72 นิ้ว. ดังนั้นความกว้าง `120` points จะเท่ากับประมาณ 1.67 นิ้ว—พอสำหรับป้ายที่อ่านง่าย, แต่ไม่ใหญ่เกินไป. ปรับค่าตามการออกแบบของคุณ; คุณสมบัติเหล่านี้ยังตอบคำถาม **how to set button** ที่คุณอาจมีอีกด้วย.

> **Note:** หากต้องการประเภทปุ่มอื่น (เช่น checkbox) ให้เปลี่ยน `Forms2OleControlType.COMMANDBUTTON` เป็นค่า enum ที่เหมาะสม.

### 5. บันทึกเอกสาร

สุดท้ายให้บันทึกเอกสารลงดิสก์:

```java
// Step 5: Save the document with the embedded ActiveX control
document.save("YOUR_DIRECTORY/CommandButton.docx");
```

แทนที่ `YOUR_DIRECTORY` ด้วยพาธแบบ absolute หรือ relative บนเครื่องของคุณ. หลังจากรันโปรแกรม, เปิดไฟล์ที่สร้างขึ้นใน Microsoft Word. คุณจะเห็นปุ่มที่มีข้อความ “Click Me” อยู่ที่ตำแหน่ง 100 pts จากซ้ายและ 200 pts จากบน, ขนาดตรงตามที่ตั้งค่าไว้.

---

## ตัวอย่างการทำงานเต็มรูปแบบ

ด้านล่างเป็นคลาส Java ที่พร้อมรันเต็มรูปแบบ. คัดลอก‑วางลงในไฟล์ `CommandButtonActiveX.java`, ปรับพาธเอาต์พุต, แล้วกด **Run**.

```java
import com.aspose.words.*;

public class CommandButtonActiveX {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document (java create blank word)
        Document document = new Document();

        // Step 2: Initialize a DocumentBuilder to work with the document
        DocumentBuilder builder = new DocumentBuilder(document);

        // Step 3: Insert an ActiveX command button (how to insert activex)
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON);

        // Step 4: Set button properties – this is how to set button size java
        commandButton.setCaption("Click Me"); // Button text
        commandButton.setLeft(100);           // Left position (points)
        commandButton.setTop(200);            // Top position (points)
        commandButton.setWidth(120);          // Width (points)
        commandButton.setHeight(30);          // Height (points)

        // Step 5: Save the document (insert command button word)
        document.save("YOUR_DIRECTORY/CommandButton.docx");
    }
}
```

**Expected output:** การเปิด `CommandButton.docx` ใน Word จะแสดงหน้าเดียวที่มีปุ่ม “Click Me” คลิกได้ อยู่ประมาณกึ่งกลางหน้า. มิติของปุ่มตรงกับค่าที่คุณตั้งไว้, ยืนยันว่า **set button size java** ทำงานตามที่คาดหวัง.

---

## คำถามทั่วไปและกรณีขอบ

### ถ้าปุ่มไม่ปรากฏใน Word?

- **Check the Word version.** ActiveX controls ต้องการเวอร์ชันเดสก์ท็อปของ Word; Word Online จะลบออก.
- **Make sure the Aspose.Words license is applied** (หากคุณใช้รุ่นที่ต้องชำระเงิน). เวอร์ชัน evaluation ที่ไม่มีลิขสิทธิ์อาจใส่ลายน้ำแต่ยังแสดงคอนโทรลได้.

### สามารถเปลี่ยนฟอนต์หรือสีของปุ่มได้หรือไม่?

ได้. หลังจากแทรกคอนโทรลแล้ว, คุณสามารถเข้าถึง OLE object ภายในและจัดการคุณสมบัติ VBA. นี่เป็นหัวข้อระดับสูง—ลองดู `commandButton.getOleObject().setProperty("ForeColor", 0xFF0000)` เพื่อให้ป้ายเป็นสีแดงเป็นตัวอย่าง.

### จะจัดการเหตุการณ์คลิกของปุ่มอย่างไร?

ActiveX command button จะส่งเหตุการณ์ VBA `Click`. เพื่อให้ปุ่มทำงานได้, คุณต้องฝัง macro ในเอกสารเดียวกัน. Aspose.Words สามารถเพิ่มโมดูล macro ผ่าน API `Document.getMacros()`, แต่โค้ด macro ต้องเขียนด้วย VBA เอง.

### มีประเภทปุ่มอื่น ๆ หรือไม่?

Aspose.Words รองรับค่า `Forms2OleControlType` มากมาย: `CHECKBOX`, `OPTIONBUTTON`, `LISTBOX` เป็นต้น. เพียงสลับค่า enum ในการเรียก `insertForms2OleControl` เพื่อทดลอง.

---

## เคล็ดลับสำหรับโค้ดพร้อมใช้งานใน Production

1. **Use constants for layout values** – ทำให้การปรับค่าในอนาคตง่ายขึ้น.
2. **Wrap the save path in a `Path` object** เพื่อหลีกเลี่ยงตัวคั่นที่แตกต่างตามแพลตฟอร์ม.
3. **Dispose of the Document** (หรือใช้ try‑with‑resources) หากคุณประมวลผลไฟล์หลายไฟล์ในลูป.
4. **Validate the output folder** ก่อนเรียก `save` เพื่อหลีกเลี่ยง `FileNotFoundException`.

---

## สรุป

คุณเพิ่งเรียนรู้ **set button size java** โดยการสร้างไฟล์ Word เปล่า, แทรกปุ่มคำสั่ง ActiveX, และกำหนดมิติอย่างแม่นยำ—ทั้งหมดด้วยไม่กี่บรรทัดของโค้ด Java. สิ่งนี้ครอบคลุมหัวใจของ **how to insert activex**, **how to set button**, **java create blank word**, และ **insert command button word** ในตัวอย่างเดียวที่ครบถ้วน.

ขั้นตอนต่อไป? ลองปรับข้อความบนปุ่ม, เพิ่ม macro เพื่อตอบสนองการคลิก, หรือฝังคอนโทรลหลายตัวบนหน้าเดียว. คุณอาจสำรวจการแปลง .docx ที่ได้เป็น PDF ด้วย Aspose.Words, โดยคงปุ่มเป็นภาพคงที่.

ลองทดลองดูได้เลย, หากเจออุปสรรคใด ๆ คอมเมนต์ไว้ด้านล่าง. Happy coding!

## สิ่งที่คุณควรเรียนต่อไป?

บทแนะนำต่อไปนี้ครอบคลุมหัวข้อที่เกี่ยวข้องอย่างใกล้ชิดและต่อยอดจากเทคนิคที่แสดงในคู่มือนี้. แต่ละแหล่งรวมตัวอย่างโค้ดทำงานเต็มรูปแบบพร้อมคำอธิบายขั้นตอนเพื่อช่วยคุณเชี่ยวชาญฟีเจอร์ API เพิ่มเติมและสำรวจแนวทางการทำงานแบบต่าง ๆ ในโปรเจกต์ของคุณ.

- [How to create form fields and add content using DocumentBuilder in Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [How to Load Word Documents with Aspose.Words Java: Comprehensive Guide](/words/english/java/document-operations/aspose-words-java-master-word-processing/)
- [How to save document as pdf with Aspose.Words for Java](/words/english/java/document-loading-and-saving/saving-documents-as-pdf/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}