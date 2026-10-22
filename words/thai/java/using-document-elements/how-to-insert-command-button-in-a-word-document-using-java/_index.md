---
category: general
date: 2026-08-23
description: เรียนรู้วิธีแทรกปุ่มคำสั่งในเอกสาร Word ด้วย Java และ Aspose.Words คู่มือนี้จะแสดงวิธีเพิ่มฟอร์มคอนโทรล
  ตั้งชื่อปุ่ม และฝังปุ่ม ActiveX.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert command button
- add form control
- how to add button
- set button name
- add activex button
language: th
lastmod: 2026-08-23
og_description: แทรกปุ่มคำสั่งในเอกสาร Word ด้วย Java. ทำตามคำแนะนำนี้เพื่อเพิ่มการควบคุมฟอร์ม,
  ตั้งชื่อปุ่ม, และฝังปุ่ม ActiveX ด้วย Aspose.Words.
og_image_alt: Screenshot of a Word document showing an inserted ActiveX command button
og_title: แทรกปุ่มคำสั่งใน Word ด้วย Java – คู่มือขั้นตอนโดยละเอียด
schemas:
- author: Aspose
  dateModified: '2026-08-23'
  description: Learn how to insert command button in a Word document using Java and
    Aspose.Words. This guide shows how to add form control, set button name, and embed
    an ActiveX button.
  headline: How to insert command button in a Word document using Java
  type: TechArticle
- description: Learn how to insert command button in a Word document using Java and
    Aspose.Words. This guide shows how to add form control, set button name, and embed
    an ActiveX button.
  name: How to insert command button in a Word document using Java
  steps:
  - name: Open `CommandButtonDemo.docx` with Microsoft Word (2016 or later).
    text: Open `CommandButtonDemo.docx` with Microsoft Word (2016 or later).
  - name: The **Submit** button appears where the cursor was positioned during insertion.
    text: The **Submit** button appears where the cursor was positioned during insertion.
  - name: Right‑click the button and choose **Properties** to see that the **Name**
      field contains `btnSubmit`.
    text: Right‑click the button and choose **Properties** to see that the **Name**
      field contains `btnSubmit`.
  type: HowTo
tags:
- Aspose.Words
- Java
- Word automation
title: วิธีแทรกปุ่มคำสั่งในเอกสาร Word ด้วย Java
url: /th/java/using-document-elements/how-to-insert-command-button-in-a-word-document-using-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# วิธีแทรกปุ่มคำสั่งในเอกสาร Word ด้วย Java

หากคุณต้องการ **แทรกปุ่มคำสั่ง** ลงในไฟล์ Word, บทแนะนำนี้จะแสดงวิธีแก้ไขแบบครบวงจรด้วย Aspose.Words for Java คุณจะได้เห็นวิธีเพิ่มฟอร์มคอนโทรล, ตั้งค่าคำบรรยายของมัน, และกำหนดชื่อปุ่มโดยไม่ต้องออกจาก IDE

คู่มือครอบคลุมทุกอย่างที่คุณต้องการเพื่อสร้างไฟล์ `.docx` ที่มีปุ่ม ActiveX พร้อมใช้งานใน Microsoft Word ไม่ต้องใช้เครื่องมือเพิ่มเติมใด ๆ และตัวอย่างทำงานบน Java 8+

## สิ่งที่คุณจะได้เรียนรู้

* วิธีเพิ่มฟอร์มคอนโทรลประเภท **CommandButton** ลงในเอกสาร Word  
* ขั้นตอนที่แน่นอนในการ **ตั้งชื่อปุ่ม** และ **เพิ่มคุณสมบัติของปุ่ม activex**  
* วิธีบันทึกเอกสารเพื่อให้ปุ่มปรากฏอย่างถูกต้องเมื่อเปิดใน Word  

คุณควรมีสภาพแวดล้อมการพัฒนา Java เบื้องต้นและโครงการ Maven หรือ Gradle ที่สามารถนำเข้าไลบรารี Aspose.Words ได้

## ข้อกำหนดเบื้องต้น

| Requirement | Reason |
|-------------|--------|
| Java 8 หรือใหม่กว่า | Aspose.Words for Java ทำงานบน Java 8+ |
| เครื่องมือสร้าง Maven หรือ Gradle | ช่วยให้ง่ายต่อการเพิ่ม dependency ของ Aspose.Words |
| ใบอนุญาต Aspose.Words for Java (หรือทดลองใช้ฟรี) | จำเป็นสำหรับฟีเจอร์เต็ม; API ทำงานในโหมดประเมินผล |
| IDE เช่น IntelliJ IDEA หรือ Eclipse | ทำให้การแก้ไขและรันตัวอย่างง่ายขึ้น |

## ขั้นตอนที่ 1: เพิ่ม Aspose.Words ไปยังโครงการของคุณ

หากคุณใช้ Maven, เพิ่ม dependency ต่อไปนี้ใน `pom.xml`:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version> <!-- Use the latest version -->
</dependency>
```

สำหรับ Gradle, ใส่บรรทัดนี้ใน `build.gradle`:

```gradle
implementation 'com.aspose:aspose-words:24.9'
```

หลังจาก dependency ถูกดึงมาแล้ว, คุณสามารถนำเข้าคลาสของไลบรารีในไฟล์ซอร์ส Java ของคุณได้

## ขั้นตอนที่ 2: แทรกปุ่มคำสั่ง – โค้ดหลัก

สร้างคลาส Java ใหม่ชื่อ `InsertCommandButtonDemo` โค้ดด้านล่างทำการดำเนินการสี่ขั้นตอนที่จำเป็นสำหรับการ **แทรกปุ่มคำสั่ง**:

```java
import com.aspose.words.*;

public class InsertCommandButtonDemo {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Create a new blank document and a DocumentBuilder to edit it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Add form control – an ActiveX CommandButton – to the document
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMAND_BUTTON);

        // 3️⃣ Set button name and displayed caption (this answers the "set button name" need)
        commandButton.setName("btnSubmit");
        commandButton.setCaption("Submit");

        // 4️⃣ Save the document with the embedded button
        doc.save("CommandButtonDemo.docx");
    }
}
```

### ทำไมแต่ละบรรทัดจึงสำคัญ

* **Document & DocumentBuilder** – ให้การแสดงผลในหน่วยความจำของไฟล์ Word และ API สำหรับแก้ไขเนื้อหา  
* **insertForms2OleControl** – เมธอดนี้ **เพิ่มฟอร์มคอนโทรล** ประเภท `COMMAND_BUTTON` วัตถุ `Forms2OleControl` ที่คืนค่ามาแสดงถึงคอนโทรล ActiveX  
* **setName** – กำหนดตัวระบุโปรแกรม (`btnSubmit`) Word macro หรือ VBA สามารถอ้างอิงชื่อนี้ได้ในภายหลัง  
* **setCaption** – กำหนดข้อความที่ผู้ใช้เห็นบนปุ่ม, ตอบคำถาม “วิธีเพิ่มปุ่ม”  
* **save** – เขียนไฟล์ `.docx` ไปยังดิสก์, คงปุ่ม ActiveX ที่ฝังอยู่ไว้  

การรันโปรแกรมจะสร้างไฟล์ `CommandButtonDemo.docx` ในไดเรกทอรีทำงาน การเปิดไฟล์ใน Microsoft Word จะแสดงปุ่มที่มีข้อความ **Submit** ซึ่งสามารถคลิกได้ (จะแสดงไดอะล็อก ActiveX เริ่มต้นในโหมดประเมินผล)

## ขั้นตอนที่ 3: ตรวจสอบปุ่มที่แทรกใน Word

1. เปิด `CommandButtonDemo.docx` ด้วย Microsoft Word (2016 หรือใหม่กว่า)  
2. ปุ่ม **Submit** จะปรากฏตรงตำแหน่งที่เคอร์เซอร์อยู่ขณะแทรก  
3. คลิกขวาที่ปุ่มและเลือก **Properties** เพื่อดูว่าฟิลด์ **Name** มีค่า `btnSubmit`  

หากปุ่มไม่ปรากฏ, ตรวจสอบให้แน่ใจว่า **ActiveX controls** ถูกเปิดใช้งานในการตั้งค่า Trust Center ของ Word

## ขั้นตอนที่ 4: ปรับแต่งปุ่ม (ไม่บังคับ)

คุณสามารถปรับแต่งปุ่มเพิ่มเติมได้โดยเปลี่ยนขนาด, ตำแหน่ง, หรือเพิ่ม VBA macro คลาส `Forms2OleControl` มีคุณสมบัติเพิ่มเติมเช่น `setWidth`, `setHeight`, และ `setLeft` ตัวอย่างต่อไปนี้ทำให้ปุ่มใหญ่ขึ้น:

```java
commandButton.setWidth(100);   // Width in points
commandButton.setHeight(30);   // Height in points
commandButton.setLeft(50);     // Horizontal offset from the left margin
```

บรรทัดเหล่านี้สามารถวางหลังจากการเรียก `setCaption` ได้ มันแสดงการ **เพิ่มคุณสมบัติของปุ่ม activex** ที่เกินการแทรกพื้นฐาน

## ข้อผิดพลาดทั่วไปและวิธีหลีกเลี่ยง

| Symptom | Cause | Fix |
|---------|-------|-----|
| Button does not appear in Word | Document saved before the control was added | Ensure `insertForms2OleControl` is called before `doc.save`. |
| Button caption is empty | `setCaption` not called or called with an empty string | Provide a non‑empty string, e.g., `"Submit"`. |
| VBA cannot find the button | Name mismatch between VBA code and `setName` value | Keep the name consistent; use `setName("btnSubmit")` and reference `btnSubmit` in VBA. |
| Security warning on opening the file | Word’s macro security blocks ActiveX controls | Adjust Trust Center > Macro Settings, or sign the document with a trusted certificate. |

## ตัวอย่างเต็มที่สามารถรันได้

ด้านล่างเป็นไฟล์ซอร์สทั้งหมดพร้อมคัดลอก‑วางลงใน IDE ของคุณ รวมถึงคำสั่ง import, การจัดการข้อยกเว้น, และบล็อกคอมเมนต์ที่อธิบายแต่ละขั้นตอนสำคัญ

```java
// InsertCommandButtonDemo.java
// Demonstrates how to insert an ActiveX CommandButton into a Word document using Aspose.Words for Java.

import com.aspose.words.*;

public class InsertCommandButtonDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document and a DocumentBuilder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Add a CommandButton form control (ActiveX) to the document.
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMAND_BUTTON);

        // Step 3: Configure the button – set its programmatic name and visible caption.
        commandButton.setName("btnSubmit");   // This answers the "set button name" requirement.
        commandButton.setCaption("Submit");   // This is the text the user sees.

        // Optional: Resize and reposition the button (demonstrates add activex button customization).
        commandButton.setWidth(100);
        commandButton.setHeight(30);
        commandButton.setLeft(50);

        // Step 4: Save the document. The button is now embedded and will appear in Word.
        doc.save("CommandButtonDemo.docx");
    }
}
```

**ผลลัพธ์ที่คาดหวัง:** หลังจากรันโปรแกรม, `CommandButtonDemo.docx` จะมีปุ่ม **Submit** เพียงปุ่มเดียว การเปิดไฟล์ใน Word จะเห็นปุ่มอยู่ตรงตำแหน่งที่เคอร์เซอร์ของ `DocumentBuilder` อยู่

## ขั้นตอนต่อไป

* **เพิ่มฟอร์มคอนโทรลอื่น** – ใช้ `Forms2OleControlType.CHECK_BOX`, `RADIO_BUTTON`, หรือ `TEXT_BOX` เพื่อสร้างฟอร์ม Word ที่สมบูรณ์  
* **ผสานกับ mail merge** – แทรกปุ่มลงในเอกสารที่ทำ mail‑merge เพื่อสร้างฟอร์มเชิงโต้ตอบส่วนบุคคล  
* **แนบ VBA macros** – ฝัง VBA ที่ตอบสนองต่อเหตุการณ์ `Click` ของปุ่มเพื่อทำออโตเมชันขั้นสูง  

หัวข้อเหล่านี้ต่อยอดจากเทคนิค **add form control** ที่คุณเพิ่งเรียนรู้

---

### สรุป

คุณได้เรียนรู้วิธี **แทรกปุ่มคำสั่ง** ลงในเอกสาร Word ด้วย Java, วิธี **เพิ่มฟอร์มคอนโทรล**, วิธี **ตั้งชื่อปุ่ม**, และวิธี **เพิ่มคุณสมบัติของปุ่ม activex** ตัวอย่างเต็มทำงานทันที, และคุณสามารถปรับใช้กับกระบวนการสร้างเอกสารใด ๆ ก็ได้ ขอให้สนุกกับการเขียนโค้ด!

## สิ่งที่คุณควรเรียนรู้ต่อไป

บทแนะนำต่อไปนี้ครอบคลุมหัวข้อที่เกี่ยวข้องอย่างใกล้ชิดและต่อยอดจากเทคนิคในคู่มือนี้ แต่ละแหล่งรวมโค้ดทำงานเต็มรูปแบบพร้อมคำอธิบายขั้นตอนเพื่อช่วยให้คุณเชี่ยวชาญฟีเจอร์ API เพิ่มเติมและสำรวจวิธีการทำงานทางเลือกในโครงการของคุณเอง

- [How to create form fields and add content using DocumentBuilder in Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Insert Combo Box Form Field in Word Document](/words/english/net/working-with-form-fields/insert-form-fields/)
- [Insert Check Box Form Field In Word Document](/words/english/net/add-content-using-documentbuilder/insert-check-box-form-field/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}