---
category: general
date: 2026-10-13
description: สร้างปุ่มฟิลด์ฟอร์มใน Word ด้วย Aspose.Words for Java. เรียนรู้วิธีแทรกฟิลด์ฟอร์มปุ่มคำสั่งใน
  Word และตั้งค่าคำบรรยายของปุ่มคำสั่งในไม่กี่ขั้นตอนง่าย ๆ.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create form field button
- insert command button word
- set command button caption
language: th
lastmod: 2026-10-13
og_description: สร้างปุ่มฟิลด์ฟอร์มใน Word ด้วย Aspose.Words for Java. บทเรียนนี้แสดงวิธีแทรกฟิลด์คำสั่งปุ่มและตั้งค่าคำบรรยายของปุ่มอย่างรวดเร็ว.
og_image_alt: Screenshot of a Word document containing an inserted command button
  form field created with Aspose.Words Java
og_title: สร้างปุ่มฟิลด์ฟอร์มใน Word – คู่มือ Aspose.Words Java
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Create form field button in Word using Aspose.Words for Java. Learn
    how to insert command button word form fields and set command button caption in
    a few easy steps.
  headline: Create form field button in Word with Aspose.Words Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word automation
title: สร้างปุ่มฟิลด์ฟอร์มใน Word ด้วย Aspose.Words Java
url: /th/java/using-document-elements/create-form-field-button-in-word-with-aspose-words-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# สร้างปุ่มฟิลด์ฟอร์มใน Word ด้วย Aspose.Words Java

หากคุณต้องการ **create form field button** ในเอกสาร Word คำแนะนำนี้จะพาคุณผ่านกระบวนการทั้งหมดโดยใช้ Aspose.Words for Java ไม่ว่าคุณจะกำลังสร้างเทมเพลตฟอร์มกรอกข้อมูลหรือเพิ่มคอนโทรลแบบโต้ตอบในรายงาน คุณจะได้เรียนรู้วิธี **insert command button word** ฟิลด์ฟอร์มและ **set command button caption** ด้วยโค้ดเพียงเล็กน้อย

บทแนะนำนี้ครอบคลุมทุกอย่างตั้งแต่การตั้งค่า Maven จนถึงตัวอย่างที่สามารถรันได้เต็มรูปแบบ เพื่อให้คุณสามารถคัดลอก‑วางโค้ด, รันมัน, และดูไฟล์ `.docx` ที่มีปุ่มคลิกได้พร้อมสำหรับการปรับแต่งเพิ่มเติม

## ข้อกำหนดเบื้องต้น

- Java 17 (หรือใหม่กว่า) ที่ติดตั้งและกำหนดค่าไว้บนเครื่องของคุณ
- Maven 3.6+ สำหรับการจัดการ dependencies
- IDE หรือโปรแกรมแก้ไขข้อความตามที่คุณเลือก (เช่น IntelliJ IDEA, VS Code)
- ใบอนุญาต Aspose.Words for Java ที่ถูกต้อง (รุ่นทดลองใช้ฟรีสำหรับการประเมินผล)

## ขั้นตอนที่ 1: เพิ่ม Aspose.Words ไปยังโครงการ Maven ของคุณ

สร้างไฟล์ `pom.xml` (หรือแก้ไขไฟล์ที่มีอยู่) และเพิ่ม dependency ของ Aspose.Words:

```xml
<dependencies>
    <dependency>
        <groupId>com.aspose</groupId>
        <artifactId>aspose-words</artifactId>
        <version>24.9</version> <!-- Use the latest version available -->
    </dependency>
</dependencies>
```

> **Pro tip:** ควรอัปเดตหมายเลขเวอร์ชันให้เป็นปัจจุบัน รุ่นใหม่จะเพิ่มการสนับสนุนฟีเจอร์ Word ล่าสุดและปรับปรุงประสิทธิภาพ

## ขั้นตอนที่ 2: เริ่มต้นเอกสารเปล่าและ `DocumentBuilder`

คลาส `DocumentBuilder` ให้ API แบบ fluent สำหรับแก้ไขเอกสาร Word ในขั้นตอนนี้เราจะสร้าง `Document` ว่างเปล่าและผูก builder เข้ากับมัน

```java
import com.aspose.words.*;

public class InsertCommandButtonDemo {
    public static void main(String[] args) throws Exception {
        // Create a new blank document
        Document doc = new Document();

        // DocumentBuilder lets us add content programmatically
        DocumentBuilder builder = new DocumentBuilder(doc);
```

การสร้างเอกสารเป็นพื้นฐานสำหรับวัตถุ **create form field button** ในภายหลังของบทแนะนำ

## ขั้นตอนที่ 3: แทรกฟิลด์ฟอร์มปุ่มคำสั่ง

Aspose.Words เปิดเผยคลาส `Forms2OleControl` สำหรับคอนโทรลฟอร์ม OLE เพื่อ **insert command button word** ฟิลด์ฟอร์ม ให้เรียก `insertForms2OleControl` พร้อมค่าตัวแปร enum `COMMANDBUTTON`

```java
        // Insert a Command Button form field at the current cursor position
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON);
```

เมธอดนี้จะคืนค่าอินสแตนซ์ `Forms2OleControl` ที่เราสามารถกำหนดค่าก่อนบันทึกได้

## ขั้นตอนที่ 4: กำหนดขนาดและตำแหน่งของปุ่ม

ปุ่มคำสั่งต้องการขนาดและตำแหน่งที่ชัดเจนบนหน้า ปรับความกว้าง, ความสูง, และพิกัดให้เหมาะกับการจัดวางของคุณ

```java
        // Set the button's visual size (in points)
        commandButton.setWidth(120);   // 120 points ≈ 1.67 inches
        commandButton.setHeight(30);   // 30 points ≈ 0.42 inches

        // Position the button relative to the page margins
        commandButton.setLeft(50);   // 50 points from the left margin
        commandButton.setTop(100);   // 100 points from the top margin
```

การปรับค่าต่าง ๆ อย่างละเอียดจะทำให้ปุ่มปรากฏตรงตำแหน่งที่คุณต้องการในเอกสารขั้นสุดท้าย

## ขั้นตอนที่ 5: **Set command button caption**

ข้อความที่แสดงบนปุ่มถูกควบคุมโดยเมธอด `setCaption` นี่คือจุดที่เราจะ **set command button caption** เพื่อชี้นำผู้ใช้

```java
        // Define the text that appears on the button
        commandButton.setCaption("Click Me");
```

คุณสามารถเปลี่ยน `"Click Me"` เป็นป้ายกำกับใด ๆ ที่สอดคล้องกับวัตถุประสงค์ของฟอร์มของคุณ เช่น `"Submit"` หรือ `"Approve"`

## ขั้นตอนที่ 6: บันทึกเอกสาร

สุดท้ายให้เขียนเอกสารลงดิสก์ ไฟล์ที่ได้จะมีปุ่มเชิงโต้ตอบและสามารถเปิดได้ใน Microsoft Word หรือ LibreOffice

```java
        // Save the document with the embedded command button
        doc.save("CommandButtonDemo.docx");
    }
}
```

การรันโปรแกรมจะสร้างไฟล์ `CommandButtonDemo.docx` การเปิดไฟล์ใน Word จะแสดงปุ่มที่มีป้าย **Click Me** อยู่ห่างจากด้านซ้าย 50 pts และจากด้านบน 100 pts ของหน้า

### ผลลัพธ์ที่คาดหวัง

- ไฟล์ `.docx` ชื่อ `CommandButtonDemo.docx`
- เอกสารมีหน้าเดียวที่มีฟิลด์ฟอร์มปุ่มคำสั่ง
- ปุ่มจะแสดงข้อความที่คุณตั้งค่า (เช่น **Click Me**)

## ความหลากหลายและกรณีขอบที่พบบ่อย

| สถานการณ์ | วิธีปรับ |
|-----------|----------|
| **Multiple buttons** | เรียก `insertForms2OleControl` ซ้ำหลายครั้ง พร้อมปรับ `setLeft`/`setTop` สำหรับแต่ละปุ่มใหม่ |
| **Different caption per button** | ใช้ `setCaption` พร้อมสตริงที่ไม่ซ้ำกันหลังการแทรกแต่ละครั้ง |
| **Button inside a table cell** | ย้ายเคอร์เซอร์ไปยังเซลล์ที่ต้องการด้วย `builder.moveTo(cell.getFirstParagraph())` ก่อนแทรกคอนโทรล |
| **Legacy Word formats (.doc)** | บันทึกโดยใช้ `doc.save("Demo.doc", SaveFormat.DOC);` – ปุ่มคำสั่งจะถูกเก็บไว้ |
| **Read‑only forms** | หลังจากแทรกแล้ว ให้ตั้งค่า `commandButton.setEnabled(false);` เพื่อป้องกันการโต้ตอบของผู้ใช้ |

## เคล็ดลับสำหรับการใช้งานที่มั่นคง

- **Validate dimensions**: ความกว้างที่ใหญ่เกินไปอาจทำให้ปุ่มล้นขอบหน้ากระดาษ
- **License enforcement**: หากไม่มีใบอนุญาตที่ถูกต้อง Aspose.Words จะใส่ลายน้ำในเอกสารที่สร้างขึ้น ให้ตั้งค่าใบอนุญาตตั้งแต่ต้นด้วย `License license = new License(); license.setLicense("Aspose.Words.lic");`
- **Testing**: เปิดไฟล์ที่สร้างขึ้นใน Word และสลับ **Design Mode** (Developer → Design Mode) เพื่อดูคุณสมบัติของปุ่ม

## สรุปโค้ดต้นฉบับทั้งหมด

```java
import com.aspose.words.*;

public class InsertCommandButtonDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document and a builder to edit it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Insert a Command Button form field
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON);

        // Step 3: Define the button's size and position on the page
        commandButton.setWidth(120);
        commandButton.setHeight(30);
        commandButton.setLeft(50);
        commandButton.setTop(100);

        // Step 4: Set the text that appears on the button
        commandButton.setCaption("Click Me");

        // Step 5: Save the document with the embedded command button
        doc.save("CommandButtonDemo.docx");
    }
}
```

คัดลอกโค้ดไปยังไฟล์ชื่อ `InsertCommandButtonDemo.java` คอมไพล์ด้วย Maven (`mvn compile`) และรัน (`mvn exec:java -Dexec.mainClass=InsertCommandButtonDemo`). เอกสารที่สร้างขึ้นจะอยู่ในโฟลเดอร์รากของโครงการของคุณ

## สรุป

ตอนนี้คุณรู้วิธี **create form field button** ใน Word ด้วย Aspose.Words for Java วิธี **insert command button word** ฟิลด์ฟอร์ม และวิธี **set command button caption** ด้วยโปรแกรม ตัวอย่างครบวงจรนี้ให้พื้นฐานที่มั่นคงสำหรับการสร้างเอกสาร Word ที่มีความโต้ตอบและหลากหลายมากขึ้น ไม่ว่าคุณจะต้องการปุ่มส่งเดียวหรือชุดคอนโทรลฟอร์มเต็มรูปแบบ

### ขั้นตอนต่อไปคืออะไร?

- สำรวจคอนโทรลฟอร์มอื่น ๆ เช่น เช็คบ็อกซ์ (`Forms2OleControlType.CHECKBOX`) และกล่องข้อความ (`Forms2OleControlType.TEXTBOX`)
- รวมฟิลด์ฟอร์มกับ mail‑merge เพื่อสร้างแบบสอบถามส่วนบุคคล
- ใช้ Aspose.Words `FormField` API เพื่ออ่านข้อมูลที่ผู้ใช้กรอกหลังจากเอกสารถูกเติมเต็ม

อย่าลังเลที่จะทดลองกับขนาด, ป้ายข้อความ, และตำแหน่งต่าง ๆ เมื่อคุณเชี่ยวชาญปุ่มคำสั่ง การเพิ่มฟอร์มเต็มรูปแบบลงในกระบวนการอัตโนมัติของ Word จะกลายเป็นงานที่ง่ายดาย ขอให้สนุกกับการเขียนโค้ด!

## คุณควรเรียนรู้อะไรต่อไป?

บทแนะนำต่อไปนี้ครอบคลุมหัวข้อที่เกี่ยวข้องอย่างใกล้ชิดซึ่งต่อยอดจากเทคนิคที่แสดงในคู่มือนี้ แต่ละแหล่งข้อมูลมีตัวอย่างโค้ดทำงานครบถ้วนพร้อมคำอธิบายทีละขั้นตอนเพื่อช่วยให้คุณเชี่ยวชาญฟีเจอร์ API เพิ่มเติมและสำรวจแนวทางการทำงานทางเลือกในโครงการของคุณ

- [วิธีสร้างฟิลด์ฟอร์มและเพิ่มเนื้อหาโดยใช้ DocumentBuilder ใน Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [เพิ่มฟิลด์ฟอร์ม Combo Box ไปยังเอกสาร Word ด้วย Aspose.Words for .NET](/words/english/net/add-content-using-documentbuilder/insert-combo-box/)
- [เพิ่มฟิลด์ฟอร์ม Check Box ไปยังเอกสาร Word ด้วย Aspose.Words for .NET](/words/english/net/add-content-using-documentbuilder/insert-check-box/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}