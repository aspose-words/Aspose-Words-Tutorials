---
category: general
date: 2026-09-24
description: ตั้งค่าตำแหน่งปุ่มในเอกสาร Word ด้วย Java และ Aspose.Words. เรียนรู้วิธีแทรกปุ่ม,
  เพิ่มคอนโทรล ActiveX, และสร้างเอกสาร Word สไตล์ Java.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- set button position
- how to insert button
- add activex control
- add button to word
- create word document java
language: th
lastmod: 2026-09-24
og_description: ตั้งตำแหน่งปุ่มในเอกสาร Word ด้วย Java คู่มือนี้แสดงวิธีแทรกปุ่ม,
  เพิ่มการควบคุม ActiveX, และสร้างเอกสาร Word ด้วย Java โดยใช้ Aspose.Words.
og_image_alt: Screenshot of a Word document showing a CommandButton positioned at
  100 px left and 150 px top
og_title: ตั้งตำแหน่งปุ่มในเอกสาร Word ด้วย Java – คู่มือเต็ม
schemas:
- author: Aspose
  dateModified: '2026-09-24'
  description: Set button position in a Word document using Java and Aspose.Words.
    Learn how to insert button, add ActiveX control, and create Word document Java
    style.
  headline: How to set button position in a Word document with Java
  type: TechArticle
- description: Set button position in a Word document using Java and Aspose.Words.
    Learn how to insert button, add ActiveX control, and create Word document Java
    style.
  name: How to set button position in a Word document with Java
  steps:
  - name: Expected output
    text: '* A `.docx` file named **CommandButtonDemo.docx**. * Inside the document,
      a **CommandButton** labeled “Click Me” appears 100 px from the left margin and
      150 px from the top margin. * The button responds to clicks when the document
      is opened in Word (it will display a default ActiveX message unless y'
  - name: Adding multiple buttons
    text: If you need to **add button to Word** more than once, repeat steps 3‑5 with
      a new `Forms2OleControl` instance each time. Remember to adjust the `setTop`
      value so buttons don’t overlap.
  - name: Working without a license
    text: 'Aspose.Words adds a watermark when used without a license. For production
      code, purchase a license and apply it at the start of `main`:'
  - name: Compatibility with older Office versions
    text: 'ActiveX controls are supported in the `.doc` (Word 97‑2003) format. To
      create a legacy file, change the save format:'
  - name: Next steps
    text: '* Explore other `Forms2OleControl.ControlType` values (e.g., `CHECKBOX`,
      `TEXTBOX`) to build richer forms. * Combine the button with VBA macros for custom
      click handling. * Use Aspose.Words’ mail‑merge feature to generate personalized
      documents that already contain interactive controls.'
  type: HowTo
- questions:
  - answer: Yes. Aspose.Words is pure Java and runs on any JDK 8+ implementation,
      including OpenJDK.
    question: Does this work with OpenJDK?
  - answer: ActiveX button appearance is controlled by the host application (Word).
      You can attach VBA code to modify properties at runtime, but the static appearance
      is limited to the default style.
    question: Can I change the button’s font or color?
  - answer: 'Move the `DocumentBuilder` cursor into the cell before calling `insertForms2OleControl`.
      The control will inherit the cell’s layout, and you can still use `setLeft`/`setTop`
      for fine‑tuning. ## Conclusion You now know how to **set button position** in
      a Word document using Java, how to **how to inse'
    question: What if I need to place the button inside a table cell?
  type: FAQPage
tags:
- Aspose.Words
- Java
- ActiveX
- Word automation
- CommandButton
title: วิธีตั้งตำแหน่งปุ่มในเอกสาร Word ด้วย Java
url: /th/java/using-document-elements/how-to-set-button-position-in-a-word-document-with-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# วิธีตั้งตำแหน่งปุ่มในเอกสาร Word ด้วย Java

หากคุณต้องการ **set button position** ภายในไฟล์ Word คำแนะนำนี้จะแสดงวิธีแก้ไขที่สมบูรณ์และสามารถรันได้ ไม่ว่าคุณจะสร้างเทมเพลตที่ต้องการการโต้ตอบของผู้ใช้หรืออัตโนมัติฟอร์ม คุณจะได้เรียนรู้อย่างแม่นยำว่า **how to insert button** ด้วย Aspose.Words for Java และควบคุมตำแหน่งของมัน

บทแนะนำนี้ครอบคลุมทุกอย่างที่คุณต้องการเพื่อ **add ActiveX control** ในเอกสาร Word, อธิบายวิธี **add button to Word**, และสาธิตกระบวนการเต็มรูปแบบเพื่อ **create Word document Java** ไม่ต้องอ้างอิงภายนอก—เพียงคัดลอก, รัน, และตรวจสอบผลลัพธ์.

## ข้อกำหนดเบื้องต้น

* ติดตั้ง Java 17 (หรือ Java 8+ runtime ใดก็ได้).
* Maven หรือ Gradle เพื่อจัดการ dependencies.
* ใบอนุญาต Aspose.Words for Java (รุ่นทดลองฟรีใช้เพื่อการประเมิน).
* ความเข้าใจพื้นฐานของไวยากรณ์ Java.

> **Pro tip:** เก็บไฟล์ JAR ของ Aspose.Words ไว้ในโฟลเดอร์ `libs/` และเพิ่มลงใน classpath ของโปรเจกต์เพื่อหลีกเลี่ยงความขัดแย้งของเวอร์ชัน.

## ขั้นตอนที่ 1: ตั้งค่าโปรเจกต์ Maven

สร้างโปรเจกต์ Maven อย่างง่าย (หรือใช้ Gradle) และเพิ่ม dependency ของ Aspose.Words:

```xml
<!-- pom.xml -->
<project>
    <modelVersion>4.0.0</modelVersion>
    <groupId>com.example</groupId>
    <artifactId>word-button-demo</artifactId>
    <version>1.0.0</version>
    <dependencies>
        <dependency>
            <groupId>com.aspose</groupId>
            <artifactId>aspose-words</artifactId>
            <version>24.9</version> <!-- latest at time of writing -->
        </dependency>
    </dependencies>
</project>
```

การรัน `mvn clean compile` จะดาวน์โหลดไลบรารีและเตรียมเส้นทางการสร้าง.

## ขั้นตอนที่ 2: สร้างเอกสาร Word ใหม่

การดำเนินการแรกคือ **create Word document java** แบบสไตล์ คุณจะสร้างอ็อบเจ็กต์ `Document` และ `DocumentBuilder` ที่ช่วยให้คุณแก้ไขไฟล์ได้.

```java
import com.aspose.words.*;

public class CommandButtonDemo {
    public static void main(String[] args) throws Exception {
        // Initialize a blank document
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

คลาส `Document` แสดงถึงไฟล์ .docx ทั้งหมด, ส่วน `DocumentBuilder` ให้ API แบบ fluent สำหรับแทรกเนื้อหา.

## ขั้นตอนที่ 3: วิธีแทรกปุ่ม – add ActiveX control

Aspose.Words เปิดเผยคลาส `Forms2OleControl` สำหรับแทรก ActiveX control แบบเก่าเช่น CommandButton ขั้นตอนนี้แสดงวิธีที่แน่นอนว่า **how to insert button** ลงในเอกสาร.

```java
        // Insert a CommandButton ActiveX control
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControl.ControlType.COMMANDBUTTON);
```

เมธอด `insertForms2OleControl` จะคืนค่าอินสแตนซ์ `Forms2OleControl` ที่คุณสามารถกำหนดค่าได้ นี่คือแกนหลักของกระบวนการ **add ActiveX control**.

## ขั้นตอนที่ 4: ตั้งค่าตำแหน่งปุ่ม

ตอนนี้เราจริง ๆ แล้ว **set button position** เมธอด `setLeft` และ `setTop` ของคอนโทรลรับค่าหน่วยเป็น points (1 pt = 1/72 in). เพื่อให้ปุ่มสอดคล้องกับพิกัดหน้าจอทั่วไป คุณสามารถแปลงพิกเซลเป็น points (1 px ≈ 0.75 pt). ในตัวอย่างเราตั้งตำแหน่งปุ่ม 100 px จากขอบซ้ายและ 150 px จากขอบบน.

```java
        // Position the button on the page
        commandButton.setLeft(100 * 0.75);   // 75 pt ≈ 100 px
        commandButton.setTop(150 * 0.75);    // 112.5 pt ≈ 150 px
```

เนื่องจากตรรกะ **set button position** ถูกห่อหุ้มไว้ที่นี่ คุณสามารถใช้บรรทัดเหล่านี้ซ้ำได้เมื่อใดก็ตามที่ต้องการย้ายคอนโทรล ปรับตัวเลขให้ตรงกับความต้องการของการจัดวางของคุณ.

## ขั้นตอนที่ 5: กำหนดขนาดและคำบรรยาย

ปุ่มที่ไม่มีป้ายชื่อจะทำให้สับสน ใช้ `setWidth`, `setHeight`, และ `setCaption` เพื่อให้มีลักษณะที่มองเห็นได้.

```java
        // Define size and caption
        commandButton.setWidth(120 * 0.75);   // 90 pt width
        commandButton.setHeight(30 * 0.75);   // 22.5 pt height
        commandButton.setCaption("Click Me");
```

ขนาดยังคงใช้หน่วยเป็น points ดังนั้นเราจะแปลงจากพิกเซลเพื่อความสอดคล้อง.

## ขั้นตอนที่ 6: บันทึกเอกสาร – ทำให้กระบวนการ create Word document java สมบูรณ์

สุดท้าย ให้บันทึกไฟล์ลงดิสก์ พาธสามารถเป็นแบบ absolute หรือ relative จากโฟลเดอร์รากของโปรเจกต์.

```java
        // Save the document containing the CommandButton
        doc.save("output/CommandButtonDemo.docx");
    }
}
```

การรันโปรแกรมจะสร้างไฟล์ `CommandButtonDemo.docx` ภายในโฟลเดอร์ `output` การเปิดไฟล์ใน Microsoft Word จะแสดงปุ่มที่คลิกได้ซึ่งอยู่ในตำแหน่งที่คุณตั้งค่าไว้อย่างแม่นยำ.

### ผลลัพธ์ที่คาดหวัง

* ไฟล์ `.docx` ชื่อ **CommandButtonDemo.docx**.
* ภายในเอกสาร, **CommandButton** ที่มีป้าย “Click Me” ปรากฏที่ 100 px จากขอบซ้ายและ 150 px จากขอบบน.
* ปุ่มตอบสนองต่อการคลิกเมื่อเปิดเอกสารใน Word (มันจะแสดงข้อความ ActiveX เริ่มต้นหากคุณไม่ได้แนบโค้ด VBA ที่กำหนดเอง).

## ขั้นตอนที่ 7: ความแปรผันทั่วไปและกรณีขอบ

### การเพิ่มหลายปุ่ม

หากคุณต้องการ **add button to Word** มากกว่าหนึ่งครั้ง ให้ทำซ้ำขั้นตอนที่ 3‑5 พร้อมกับอินสแตนซ์ `Forms2OleControl` ใหม่ทุกครั้ง จำไว้ว่าต้องปรับค่า `setTop` เพื่อไม่ให้ปุ่มทับกัน.

```java
        Forms2OleControl secondButton = builder.insertForms2OleControl(
                Forms2OleControl.ControlType.COMMANDBUTTON);
        secondButton.setLeft(200 * 0.75);
        secondButton.setTop(250 * 0.75);
        secondButton.setWidth(120 * 0.75);
        secondButton.setHeight(30 * 0.75);
        secondButton.setCaption("Second");
```

### ทำงานโดยไม่มีใบอนุญาต

Aspose.Words จะเพิ่มลายน้ำเมื่อใช้โดยไม่มีใบอนุญาต สำหรับโค้ดในการผลิต ควรซื้อใบอนุญาตและนำไปใช้ที่จุดเริ่มต้นของ `main`:

```java
        License license = new License();
        license.setLicense("Aspose.Words.lic");
```

### ความเข้ากันได้กับเวอร์ชัน Office เก่า

ActiveX controls รองรับในรูปแบบ `.doc` (Word 97‑2003) เพื่อสร้างไฟล์แบบเก่า ให้เปลี่ยนรูปแบบการบันทึก:

```java
        doc.save("CommandButtonDemo.doc", SaveFormat.DOC);
```

## โค้ดเต็ม (สามารถรันได้)

```java
import com.aspose.words.*;

public class CommandButtonDemo {
    public static void main(String[] args) throws Exception {
        // Optional: apply a license if you have one
        // License license = new License();
        // license.setLicense("Aspose.Words.lic");

        // Step 1: Create a new blank document and a DocumentBuilder to edit it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Insert a CommandButton ActiveX control (how to insert button)
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControl.ControlType.COMMANDBUTTON);

        // Step 3: Position the button on the page (set button position)
        commandButton.setLeft(100 * 0.75);   // distance from the left edge (points)
        commandButton.setTop(150 * 0.75);    // distance from the top edge (points)

        // Step 4: Define the button's size and caption
        commandButton.setWidth(120 * 0.75);   // width in points
        commandButton.setHeight(30 * 0.75);   // height in points
        commandButton.setCaption("Click Me");

        // Step 5: Save the document containing the CommandButton (create word document java)
        doc.save("output/CommandButtonDemo.docx");
    }
}
```

บันทึกไฟล์เป็น `src/main/java/CommandButtonDemo.java`, รัน `mvn exec:java -Dexec.mainClass=CommandButtonDemo`, แล้วเปิดเอกสารที่สร้างขึ้นเพื่อดูผลลัพธ์.

## คำถามที่พบบ่อย

**Q: Does this work with OpenJDK?**  
A: ใช่ Aspose.Words เป็น Java แท้และทำงานบนการทำงานของ JDK 8+ ใดก็ได้ รวมถึง OpenJDK ด้วย.

**Q: Can I change the button’s font or color?**  
A: ลักษณะของปุ่ม ActiveX ถูกควบคุมโดยแอปพลิเคชันโฮสต์ (Word) คุณสามารถแนบโค้ด VBA เพื่อแก้ไขคุณสมบัติในขณะรันได้ แต่ลักษณะคงที่จะจำกัดอยู่ที่สไตล์เริ่มต้น.

**Q: What if I need to place the button inside a table cell?**  
A: ย้ายเคอร์เซอร์ของ `DocumentBuilder` ไปยังเซลล์ก่อนเรียก `insertForms2OleControl` คอนโทรลจะสืบทอดการจัดวางของเซลล์และคุณยังสามารถใช้ `setLeft`/`setTop` เพื่อปรับแต่งละเอียดได้.

## สรุป

ตอนนี้คุณรู้วิธี **set button position** ในเอกสาร Word ด้วย Java วิธี **how to insert button** วิธี **add ActiveX control** และวิธี **add button to Word** พร้อมปฏิบัติตามแนวทางที่ดีที่สุดสำหรับโปรเจกต์ **create Word document java** ตัวอย่างเต็มแสดงกระบวนการทั้งหมด—from การตั้งค่าโปรเจกต์จนถึงไฟล์ `.docx` ที่บันทึกไว้ซึ่งมี CommandButton ทำงาน.

### ขั้นตอนต่อไป

* สำรวจค่า `Forms2OleControl.ControlType` อื่น ๆ (เช่น `CHECKBOX`, `TEXTBOX`) เพื่อสร้างฟอร์มที่หลากหลายยิ่งขึ้น.
* ผสานปุ่มกับแมโคร VBA เพื่อจัดการการคลิกแบบกำหนดเอง.
* ใช้ฟีเจอร์ mail‑merge ของ Aspose.Words เพื่อสร้างเอกสารส่วนบุคคลที่มีคอนโทรลโต้ตอบอยู่แล้ว.

ขอให้สนุกกับการเขียนโค้ดและเพลิดเพลินกับการอัตโนมัติเอกสาร Word ด้วย Java!

## สิ่งที่คุณควรเรียนต่อไป

บทแนะนำต่อไปนี้ครอบคลุมหัวข้อที่เกี่ยวข้องอย่างใกล้ชิดซึ่งต่อยอดจากเทคนิคที่แสดงในคู่มือนี้ แต่ละแหล่งข้อมูลรวมตัวอย่างโค้ดทำงานเต็มรูปแบบพร้อมคำอธิบายทีละขั้นตอนเพื่อช่วยคุณเชี่ยวชาญฟีเจอร์ API เพิ่มเติมและสำรวจแนวทางการนำไปใช้ทางเลือกในโปรเจกต์ของคุณ.

- [วิธีสร้างฟิลด์ฟอร์มและเพิ่มเนื้อหาโดยใช้ DocumentBuilder ใน Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [เพิ่มฟิลด์ฟอร์ม Combo Box ไปยังเอกสาร Word ด้วย Aspose.Words for .NET](/words/english/net/add-content-using-documentbuilder/insert-combo-box/)
- [วิธีโหลดเอกสาร Word ด้วย Aspose.Words Java: คู่มือฉบับสมบูรณ์](/words/english/java/document-operations/aspose-words-java-master-word-processing/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}