---
category: general
date: 2026-07-16
description: กำหนดขนาดปุ่มโดยโปรแกรมในเอกสาร Word ด้วย Aspose.Words for Java. เรียนรู้วิธีแทรกปุ่ม
  ActiveX, ตั้งค่าตำแหน่งปุ่มและอื่น ๆ อีกมากมาย.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- set button size
- insert activex button
- programmatically add button
- set button location
- create word document button
language: th
lastmod: 2026-07-16
og_description: กำหนดขนาดปุ่มในเอกสาร Word ด้วย Java คู่มือขั้นตอนนี้แสดงวิธีแทรกปุ่ม
  ActiveX, ตั้งตำแหน่งปุ่ม, และเพิ่มปุ่มโดยโปรแกรม.
og_image_alt: Screenshot of a Word document where the button size has been set using
  Aspose.Words for Java
og_title: ตั้งขนาดปุ่มใน Word ด้วย Java – คู่มือ Aspose.Words เต็มรูปแบบ
schemas:
- author: Aspose
  dateModified: '2026-07-16'
  description: Set button size programmatically in a Word document using Aspose.Words
    for Java. Learn how to insert ActiveX button, set button location and more.
  headline: Set Button Size in Word with Java – Complete Aspose.Words Guide
  type: TechArticle
- description: Set button size programmatically in a Word document using Aspose.Words
    for Java. Learn how to insert ActiveX button, set button location and more.
  name: Set Button Size in Word with Java – Complete Aspose.Words Guide
  steps:
  - name: Expected Output Screenshot
    text: '![Word document showing the inserted button with the set button size](https://example.com/images/set-button-size.png
      "Screenshot of a Word file where the button size has been set using Aspose.Words
      for Java")'
  - name: “Can I set the button size using centimeters instead of points?”
    text: Word’s API only accepts points, but you can convert centimeters to points
      (`points = cm * 28.3465`). Write a small helper method if you prefer metric
      units.
  - name: “What if I need the button to appear on a specific page?”
    text: After inserting the button, you can move the cursor to a particular page
      using `builder.moveToPage(pageNumber)`. Insert the control right after the move,
      then set its location as shown above.
  - name: “Does this work with .doc (Word 97‑2003) files?”
    text: Yes—Aspose.Words automatically handles older formats. Just change the file
      extension in `doc.save("Demo.doc")`.
  type: HowTo
tags:
- Aspose.Words
- Java
- ActiveX
- Word automation
title: ตั้งขนาดปุ่มใน Word ด้วย Java – คู่มือ Aspose.Words ฉบับสมบูรณ์
url: /th/java/using-document-elements/set-button-size-in-word-with-java-complete-aspose-words-guid/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# ตั้งขนาดปุ่มใน Word ด้วย Java – คู่มือ Aspose.Words ฉบับสมบูรณ์

เคยสงสัยไหมว่า **การตั้งขนาดปุ่ม** ภายในไฟล์ Word โดยไม่ต้องเปิด UI ทำอย่างไร? คุณไม่ได้เป็นคนเดียวที่คิดเช่นนั้น เมื่อคุณต้องการสร้างเอกสารฟอร์มที่กรอกข้อมูลได้แบบอัตโนมัติ—เช่น แพ็คเกจต้อนรับพนักงานใหม่ที่มีปุ่ม “Submit”—การทำแบบโปรแกรมเมติกจะช่วยประหยัดเวลาการทำงานหลายชั่วโมง

ในบทแนะนำนี้ เราจะพาคุณผ่านขั้นตอนที่แม่นยำเพื่อ **แทรกปุ่ม ActiveX**, ปรับขนาด, กำหนดตำแหน่งให้ถูกต้อง, และสุดท้ายบันทึกไฟล์ เมื่อเสร็จคุณจะสามารถ **เพิ่มปุ่ม** ควบคุมต่าง ๆ ลงในเอกสาร Word ใด ๆ ได้โดยใช้ Aspose.Words for Java.

## ข้อกำหนดเบื้องต้น – สิ่งที่คุณต้องเตรียมก่อนเริ่ม

- **Java Development Kit (JDK) 8+** – โค้ดสามารถทำงานได้บน JDK เวอร์ชันล่าสุดใดก็ได้
- **Aspose.Words for Java** library (ดาวน์โหลด JAR เวอร์ชันล่าสุดจากเว็บไซต์ทางการ).  
- **IDE** ที่คุณเลือก—IntelliJ IDEA, Eclipse หรือแม้แต่โปรแกรมแก้ไขข้อความธรรมดาก็ใช้ได้
- ความคุ้นเคยพื้นฐานกับไวยากรณ์ Java; ไม่จำเป็นต้องมีความรู้เชิงลึกเกี่ยวกับการอัตโนมัติของ Word

> *เคล็ดลับมืออาชีพ:* ให้แน่ใจว่า JAR ของ Aspose.Words อยู่ใน classpath ของโปรเจกต์ของคุณ มิฉะนั้นคุณจะเจอ `ClassNotFoundException` ทันทีที่พยายาม import `com.aspose.words.*`.

## ขั้นตอนที่ 1: สร้างเอกสาร Word ใหม่

สิ่งแรกที่เราทำคือสร้างเอกสารเปล่าและ `DocumentBuilder` คิดว่า builder เป็นเหมือนปากกาที่ให้เราวาดอะไรลงในไฟล์ได้

```java
import com.aspose.words.*;

public class InsertCommandButtonDemo {
    public static void main(String[] args) throws Exception {
        // Create an empty document.
        Document doc = new Document();

        // DocumentBuilder gives us a fluent API to add content.
        DocumentBuilder builder = new DocumentBuilder(doc);
```

> **ทำไมเรื่องนี้สำคัญ:** วัตถุ `Document` แทนไฟล์ .docx ทั้งหมด, ส่วน `DocumentBuilder` เป็นเครื่องมือหลักที่ให้เราสามารถแทรกย่อหน้า, ตาราง, และ—ใช่—คอนโทรล ActiveX

## ขั้นตอนที่ 2: แทรกปุ่ม ActiveX – ช่วง “Insert ActiveX Button”

ตอนนี้เราจริง ๆ **แทรกปุ่ม activex** ลงในเอกสาร Aspose.Words มีเมธอดที่สะดวก `insertForms2OleControl` ซึ่งจะคืนค่าเป็นอ็อบเจ็กต์ `Forms2OleControl`

```java
        // Insert an ActiveX CommandButton control.
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMAND_BUTTON);
        commandButton.setName("cmdSubmit");   // Programmatic name.
        commandButton.setCaption("Submit");   // Text shown on the button.
```

> *อะไรที่เกิดขึ้นเบื้องหลัง?* `Forms2OleControlType.COMMAND_BUTTON` บอก Word ว่าเราต้องการ CommandButton แบบคลาสสิก ซึ่งเป็นประเภทเดียวกับที่คุณลากจากแท็บ Developer ใน UI

## ขั้นตอนที่ 3: ตั้งขนาดและตำแหน่งปุ่ม – ตรรกะหลักของ “Set Button Size”

นี่คือจุดที่คีย์เวิร์ดหลักส่องแสง เราจะ **ตั้งขนาดปุ่ม** และ **ตั้งตำแหน่งปุ่ม** เพื่อให้คอนโทรลปรากฏตรงตำแหน่งที่ต้องการบนหน้า

```java
        // Position the button (distance from the left/top edges in points).
        commandButton.setLeft(100);   // 100 points from the left margin.
        commandButton.setTop(150);    // 150 points from the top margin.

        // Set the button's dimensions.
        commandButton.setWidth(80);   // Width = 80 points.
        commandButton.setHeight(30);  // Height = 30 points.
```

> **ทำไมคุณควรสนใจ:** จุด (point) เป็นหน่วยวัดพื้นฐานใน Word (1 point = 1/72 นิ้ว) การปรับ `setLeft`, `setTop`, `setWidth`, และ `setHeight` จะให้การควบคุมที่แม่นยำระดับพิกเซล—ไม่มีอีกแล้ว “ดูดีบนหน้าจอของฉันแต่พิมพ์ออกมาไม่ตรง”

> *ข้อผิดพลาดทั่วไป:* ลืมตั้งค่าความกว้างหรือความสูงจะทำให้ปุ่มอยู่ที่ขนาดเริ่มต้น ซึ่งอาจเล็กเกินกว่าจะคลิกได้ ควรกำหนดทั้งสองค่าเสมอ

## ขั้นตอนที่ 4: บันทึกเอกสาร – เสร็จสิ้น “Create Word Document Button”

สุดท้าย เราเขียนไฟล์ลงดิสก์ ชื่อบ่งบอกว่าเรากำลัง **สร้างปุ่มในเอกสาร Word** ภายในไฟล์ .docx

```java
        // Persist the document to the file system.
        doc.save("CommandButtonDemo.docx");
    }
}
```

เมื่อคุณเปิด `CommandButtonDemo.docx` ใน Microsoft Word คุณจะเห็นปุ่ม **Submit** ที่วางห่างจากขอบซ้าย 100 pt และจากขอบบน 150 pt มีขนาด 80 × 30 pt การคลิกที่มันใน UI จะทำให้เกิดพฤติกรรมเริ่มต้นของ ActiveX (ซึ่งคุณสามารถเชื่อมต่อกับ VBA ภายหลังได้หากต้องการ)

### ภาพหน้าจอผลลัพธ์ที่คาดหวัง

![เอกสาร Word แสดงปุ่มที่แทรกพร้อมขนาดปุ่มที่ตั้งค่า](https://example.com/images/set-button-size.png "ภาพหน้าจอของไฟล์ Word ที่ตั้งค่าขนาดปุ่มโดยใช้ Aspose.Words for Java")

*ข้อความแทนภาพ:* ตั้งขนาดปุ่มในเอกสาร Word ด้วย Java

## ขั้นตอนที่ 5 (ทางเลือก): เพิ่มคอนโทรลอื่นหรือปรับสไตล์ปุ่ม

หากคุณต้องการ **เพิ่มปุ่ม** คอนโทรลเพิ่มเติมนอกเหนือจากปุ่ม Submit เดียว เพียงทำซ้ำบล็อกการแทรกด้วยชื่อและคำบรรยายใหม่ คุณยังสามารถปรับฟอนต์, สีพื้นหลัง, หรือแม้กระทั่งผูกมักร VBA ภายหลังได้

```java
        // Example: Adding a Cancel button next to Submit.
        Forms2OleControl cancelBtn = builder.insertForms2OleControl(
                Forms2OleControlType.COMMAND_BUTTON);
        cancelBtn.setName("cmdCancel");
        cancelBtn.setCaption("Cancel");
        cancelBtn.setLeft(190);   // Position it 90 points to the right of Submit.
        cancelBtn.setTop(150);
        cancelBtn.setWidth(80);
        cancelBtn.setHeight(30);
```

> *เคล็ดลับ:* ให้ขนาดของปุ่มทั้งหมดสม่ำเสมอเพื่อให้ดูเป็นมืออาชีพ วิธีง่าย ๆ คือเก็บค่าความกว้าง/ความสูงในคอนสแตนท์

## คำถามทั่วไป & กรณีขอบ

### “ฉันสามารถตั้งขนาดปุ่มเป็นเซนติเมตรแทนจุดได้หรือไม่?”

API ของ Word ยอมรับเฉพาะหน่วยจุดเท่านั้น แต่คุณสามารถแปลงเซนติเมตรเป็นจุดได้ (`points = cm * 28.3465`). เขียนเมธอดช่วยเหลือเล็ก ๆ หากคุณต้องการใช้หน่วยเมตริก

### “ถ้าฉันต้องการให้ปุ่มปรากฏบนหน้าเฉพาะ?”

หลังจากแทรกปุ่มแล้ว คุณสามารถย้ายเคอร์เซอร์ไปยังหน้าที่ต้องการโดยใช้ `builder.moveToPage(pageNumber)`. แทรกคอนโทรลทันทีหลังจากการย้าย แล้วตั้งค่าตำแหน่งตามที่แสดงด้านบน

### “วิธีนี้ทำงานกับไฟล์ .doc (Word 97‑2003) หรือไม่?”

ใช่—Aspose.Words จะจัดการรูปแบบเก่าโดยอัตโนมัติ เพียงเปลี่ยนนามสกุลไฟล์ใน `doc.save("Demo.doc")`

## ตัวอย่างเต็มที่สามารถรันได้

ด้านล่างเป็นโปรแกรมทั้งหมดที่คุณสามารถคัดลอก‑วางลงในคลาส Java แล้วรันได้ทันที (สมมติว่า JAR ของ Aspose.Words อยู่ใน classpath)

```java
import com.aspose.words.*;

public class InsertCommandButtonDemo {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Create a blank document.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Insert the first ActiveX CommandButton.
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMAND_BUTTON);
        commandButton.setName("cmdSubmit");
        commandButton.setCaption("Submit");

        // 3️⃣ Set button location and size – the core set button size logic.
        commandButton.setLeft(100);
        commandButton.setTop(150);
        commandButton.setWidth(80);
        commandButton.setHeight(30);

        // 4️⃣ (Optional) Add a second button for illustration.
        Forms2OleControl cancelBtn = builder.insertForms2OleControl(
                Forms2OleControlType.COMMAND_BUTTON);
        cancelBtn.setName("cmdCancel");
        cancelBtn.setCaption("Cancel");
        cancelBtn.setLeft(190);
        cancelBtn.setTop(150);
        cancelBtn.setWidth(80);
        cancelBtn.setHeight(30);

        // 5️⃣ Save the document – you’ve now created a Word document button.
        doc.save("CommandButtonDemo.docx");
    }
}
```

รันโปรแกรม, เปิดไฟล์ `CommandButtonDemo.docx` ที่สร้างขึ้น, คุณจะเห็นสองปุ่มที่มีขนาดพอดีพร้อมใช้งาน

## สรุป – คุณได้เชี่ยวชาญการตั้งขนาดปุ่มใน Word แล้ว

เราเพิ่งอธิบายวิธีแก้ปัญหาแบบครบวงจรจากต้นจนจบสำหรับ **การตั้งขนาดปุ่ม** และ **การตั้งตำแหน่งปุ่ม** ด้วย Aspose.Words for Java โดยทำตามขั้นตอนเหล่านี้คุณสามารถ **แทรกปุ่ม activex**, **เพิ่มปุ่ม** คอนโทรลแบบโปรแกรมเมติก, และในที่สุด **สร้างปุ่มในเอกสาร Word** ที่ทำงานตามที่คุณต้องการ

ต่อไปทำอะไรดี? ลองฝังปุ่มลงในเซลล์ตาราง, หรือผูกมักร VBA ที่ตรวจสอบฟิลด์ฟอร์มก่อนส่ง การใช้รูปแบบเดียวกันนี้ทำงานกับคอนโทรล ActiveX อื่น ๆ เช่น เช็คบ็อกซ์หรือคอมโบบ็อกซ์—เพียงเปลี่ยน `Forms2OleControlType.COMMAND_BUTTON` เป็นค่า enum ที่เหมาะสม

หากคุณเจอปัญหาใด ๆ ฝากคอมเมนต์ด้านล่างได้เลย ขอให้สนุกกับการเขียนโค้ดและเพลิดเพลินกับพลังของการสร้างเอกสาร Word แบบอัตโนมัติ!

## คุณควรเรียนรู้อะไรต่อไป?

บทแนะนำต่อไปนี้ครอบคลุมหัวข้อที่เกี่ยวข้องอย่างใกล้ชิดและต่อยอดจากเทคนิคที่แสดงในคู่มือนี้ แต่ละแหล่งข้อมูลมีตัวอย่างโค้ดทำงานเต็มรูปแบบพร้อมคำอธิบายทีละขั้นตอน เพื่อช่วยให้คุณเชี่ยวชาญฟีเจอร์ API เพิ่มเติมและสำรวจแนวทางการใช้งานทางเลือกในโปรเจกต์ของคุณ

- [วิธีตั้งค่า LoadOptions ใน Aspose.Words for Java](/words/english/java/document-loading-and-saving/using-load-options/)
- [วิธีลบส่วนท้ายจากเอกสาร Word ด้วย Aspose.Words for Java](/words/english/java/document-manipulation/removing-content-from-documents/)
- [Aspose.Words Java&#58; คู่มือครบวงจรการประมวลผลเอกสาร Word](/words/english/java/document-operations/aspose-words-java-master-word-processing/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}