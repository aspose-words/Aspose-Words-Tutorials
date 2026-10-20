---
category: general
date: 2026-07-26
description: วิธีแทรกปุ่ม ActiveX ในเอกสาร Word ด้วย Aspose.Words – เรียนรู้การตั้งค่าคำบรรยายปุ่ม,
  ตำแหน่งและขนาด เพียงไม่กี่บรรทัด.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to insert activex
- set button caption
language: th
lastmod: 2026-07-26
og_description: วิธีแทรกปุ่ม ActiveX ในเอกสาร Word ด้วย Aspose.Words. ทำตามบทแนะนำแบบทีละขั้นตอนนี้เพื่อกำหนดคำบรรยายของปุ่ม,
  ตำแหน่งและขนาด.
og_image_alt: Screenshot of a Word document showing an inserted ActiveX CommandButton
  with a custom caption
og_title: วิธีแทรกปุ่ม ActiveX ใน Word – คู่มือสั้น
schemas:
- author: Aspose
  dateModified: '2026-07-26'
  description: How to insert ActiveX button in a Word document using Aspose.Words
    – learn to set button caption, position, and size in just a few lines.
  headline: How to Insert ActiveX Button in Word – Set Button Caption
  type: TechArticle
tags:
- Aspose.Words
- Java
- ActiveX
- Word automation
- Document generation
title: วิธีแทรกปุ่ม ActiveX ใน Word – ตั้งค่าข้อความปุ่ม
url: /th/java/using-document-elements/how-to-insert-activex-button-in-word-set-button-caption/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# วิธีแทรกปุ่ม ActiveX ใน Word – ตั้งค่าคำบรรยายปุ่ม

เคยสงสัย **how to insert ActiveX** คอนโทรลลงในไฟล์ Word โดยไม่ต้องเปิด UI ไหม? คุณไม่ได้เป็นคนเดียว ในแอปพลิเคชันระดับองค์กรหลายแห่งคุณต้องการปุ่มที่คลิกได้ซึ่งเรียกแมโครและการทำเช่นนี้โดยโปรแกรมช่วยประหยัดเวลาหลายชั่วโมง คู่มือนี้จะแสดงให้คุณเห็นอย่างชัดเจนว่า **how to insert ActiveX** CommandButton ด้วย Aspose.Words for Java และ—ใช่—วิธี **set button caption** เพื่อให้ผู้ใช้รู้ว่าจะต้องคลิกอะไร

เราจะเดินผ่านกระบวนการทั้งหมด: ตั้งค่าห้องสมุด, สร้างเอกสารใหม่, ใส่ปุ่ม, ปรับขนาดและตำแหน่ง, ให้คำบรรยายที่เป็นมิตร, และสุดท้ายบันทึกไฟล์ เมื่อเสร็จคุณจะได้ไฟล์ `.docx` ที่สามารถเปิดใน Word พร้อมปุ่ม ActiveX ที่ทำงานเต็มรูปแบบพร้อมเรียกแมโครของคุณ

---

## สิ่งที่คุณจะได้เรียนรู้

- ติดตั้งและอ้างอิง Aspose.Words ในโปรเจกต์ Java.  
- สร้าง `Document` และ `DocumentBuilder` ใหม่.  
- **Insert ActiveX** คอนโทรล CommandButton ด้วยบรรทัดโค้ดเดียว.  
- **Set button caption**, ปรับตำแหน่งและกำหนดขนาด.  
- บันทึกเอกสารและเปิดใน Word เพื่อดูผลลัพธ์.

ไม่จำเป็นต้องมีประสบการณ์กับ ActiveX มาก่อน; เพียงความรู้พื้นฐานของ Java และสำเนา Aspose.Words.

## ข้อกำหนดเบื้องต้น

- ติดตั้ง Java 8 หรือใหม่กว่าในเครื่องของคุณ.  
- Maven หรือ Gradle สำหรับการจัดการ dependencies (เราจะแสดงตัวอย่าง Maven).  
- สำเนา **Aspose.Words for Java** ที่มีลิขสิทธิ์หรือแบบประเมิน (รุ่นทดลองฟรีใช้งานได้สำหรับการสาธิตนี้).  
- Microsoft Word (เวอร์ชันล่าสุดใดก็ได้) เพื่อทดสอบไฟล์ที่สร้างขึ้น.

## ขั้นตอนที่ 1: ตั้งค่า Aspose.Words ในโปรเจกต์ของคุณ

สิ่งแรกที่ต้องทำ—เพิ่ม dependency ของ Aspose.Words หากคุณใช้ Maven ให้ใส่ส่วนนี้ลงใน `pom.xml` ของคุณ:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.10</version> <!-- check for the latest version -->
</dependency>
```

ผู้ใช้ Gradle สามารถเพิ่มได้:

```gradle
implementation 'com.aspose:aspose-words:24.10'
```

หลังจากรัน `mvn clean install` (หรือ `gradle build`) อย่างรวดเร็ว ไลบรารีจะอยู่ใน classpath ของคุณและคุณพร้อมเขียนโค้ดแล้ว.

## ขั้นตอนที่ 2: สร้าง Document และ Builder ใหม่

`Document` แทนไฟล์ Word ทั้งหมด, ส่วน `DocumentBuilder` ให้คุณแก้ไขมัน คิดว่า Builder เป็นปากกาที่วาดบนผืนผ้าใบใหม่.

```java
import com.aspose.words.*;

public class ActiveXButtonDemo {
    public static void main(String[] args) throws Exception {
        // Step 2: Initialize a blank document and a builder
        Document doc = new Document();                 // creates an empty .docx
        DocumentBuilder builder = new DocumentBuilder(doc);
```

ทำไมต้องเริ่มจากเอกสารเปล่า? มันรับประกันว่าคุณจะมีการควบคุมเต็มที่ต่อทุกองค์ประกอบที่เพิ่มเข้าไปและไม่มีการจัดรูปแบบที่ซ่อนอยู่ทำให้คุณประหลาดใจในภายหลัง.

## ขั้นตอนที่ 3: แทรกคอนโทรล ActiveX CommandButton

ต่อไปคือส่วนสำคัญของการแสดงผล Aspose.Words มีเมธอด `insertForms2OleControl` ที่สามารถวางคอนโทรล ActiveX ใด ๆ ที่คุณระบุได้ ที่นี่เราต้องการ **CommandButton**.

```java
        // Step 3: Insert a CommandButton ActiveX control
        Forms2OleControl commandBtn = builder.insertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON);
```

เมธอดนี้คืนค่าเป็นอ็อบเจ็กต์ `Forms2OleControl` ซึ่งให้คุณเข้าถึงคุณสมบัติของปุ่มได้แบบโปรแกรม นี่คือจุดที่ **how to insert activex** กลายเป็นบรรทัดเดียว—ไม่ต้องยุ่งกับ COM API ระดับต่ำ.

## ขั้นตอนที่ 4: กำหนดตำแหน่ง, ขนาด, และตั้งค่าคำบรรยายปุ่ม

ปุ่มที่ลอยอยู่กลางหน้าไม่ค่อยมีประโยชน์ คุณต้องการวางมันในตำแหน่งที่ผู้ใช้คาดหวัง ให้ขนาดที่เหมาะสม และ—ที่สำคัญที่สุด—**set button caption** เพื่อให้พวกเขารู้ว่าการคลิกจะทำอะไร.

```java
        // Step 4a: Position the button (coordinates are in points)
        commandBtn.setLeft(100);   // distance from the left margin
        commandBtn.setTop(150);    // distance from the top margin

        // Step 4b: Define width and height
        commandBtn.setWidth(120);
        commandBtn.setHeight(30);

        // Step 4c: Set the button caption (the text that appears on the button)
        commandBtn.setCaption("Click Me");
```

**ทำไมถึงใช้ตัวเลขเหล่านี้?** Word ใช้หน่วยจุด (1 pt ≈ 1/72 inch). `100 pt` ≈ 1.4 in จากด้านซ้าย, `150 pt` ≈ 2.1 in จากด้านบน—ประมาณกลางของหน้า A4 มาตรฐาน ปรับค่าเหล่านี้ให้เหมาะกับเลย์เอาต์ของคุณ.

การตั้งค่าคำบรรยายเป็นสิ่งสำคัญ; หากไม่มีมันปุ่มจะดูเหมือนสี่เหลี่ยมว่างเมธอด `setCaption` รับสตริงใดก็ได้ ดังนั้นคุณสามารถแปลเป็นภาษาท้องถิ่นในภายหลังได้หากต้องการ.

## ขั้นตอนที่ 5: บันทึกเอกสาร

สุดท้าย เขียนเอกสารลงดิสก์ คุณสามารถเลือกโฟลเดอร์ใดก็ได้; เพียงตรวจสอบให้แน่ใจว่าเส้นทางมีอยู่.

```java
        // Step 5: Save the document to a .docx file
        String outputPath = "C:/Temp/ActiveXButton.docx";
        doc.save(outputPath);
        System.out.println("Document saved to " + outputPath);
    }
}
```

เมื่อคุณเปิด `ActiveXButton.docx` ใน Word คุณจะเห็นปุ่มที่วางอย่างดีพร้อมป้าย **“Click Me.”** หากคุณดับเบิลคลิก Word จะขอให้คุณเปิดใช้งานแมโคร (เพราะคอนโทรล ActiveX ถือเป็นแมโคร) จากนั้นคุณสามารถผูกรูทีน VBA กับเหตุการณ์ `Click` ของปุ่มได้.

## กรณีขอบและเคล็ดลับที่คุณอาจพลาด

- **Macro‑Enabled Format**: Word ปิดการใช้งานคอนโทรล ActiveX ในไฟล์ `.docx` ธรรมดา เว้นแต่ผู้ใช้จะเปิดแมโคร หากคุณต้องการให้ปุ่มทำงานทันที ให้บันทึกเป็น `.docm` (macro‑enabled) ด้วยการใช้ `doc.save(outputPath, SaveFormat.DOCM);`.
- **Compatibility**: เวอร์ชัน Word เก่ากว่า (ก่อน 2007) ใช้รูปแบบไบนารี `.doc`. Aspose.Words สามารถบันทึกเป็นรูปแบบนั้นได้ แต่คุณสมบัติของคอนโทรลอาจแสดงผลแตกต่างเล็กน้อย.
- **Security Settings**: บางสภาพแวดล้อมองค์กรล็อก ActiveX หากปุ่มของคุณไม่แสดง ตรวจสอบ Trust Center ของ Word → การตั้งค่า ActiveX.
- **Multiple Buttons**: ต้องการมากกว่าหนึ่งปุ่ม? เพียงทำซ้ำการเรียก `insertForms2OleControl` และปรับค่า `Left`/`Top` ของแต่ละปุ่ม เก็บอ็อบเจ็กต์ที่คืนค่าไว้เพื่อสามารถตั้งค่าคำบรรยายแยกแต่ละปุ่มได้.
- **Styling the Caption**: คำบรรยายสืบทอดฟอนต์เริ่มต้น หากต้องการเปลี่ยนคุณต้องแก้ไข XML พื้นฐานหรือใช้สไตล์ Word หลังการแทรก—เกินขอบเขตของคู่มือนี้ แต่ทำได้ด้วย API `ParagraphFormat` ของ Aspose.Words.

## ตัวอย่างทำงานเต็มรูปแบบ

ด้านล่างเป็นคลาส Java ที่สมบูรณ์พร้อมรัน คัดลอกและวางลงใน IDE ของคุณ ปรับเส้นทางออก และกด **Run**.

```java
import com.aspose.words.*;

public class ActiveXButtonDemo {
    public static void main(String[] args) throws Exception {
        // Create a new blank document
        Document doc = new Document();

        // Obtain a DocumentBuilder to edit the document
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert an ActiveX CommandButton control
        Forms2OleControl commandBtn = builder.insertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON);

        // Position the button (points from the left/top margins)
        commandBtn.setLeft(100);
        commandBtn.setTop(150);

        // Set size (width × height in points)
        commandBtn.setWidth(120);
        commandBtn.setHeight(30);

        // Set the button caption – this is the visible text
        commandBtn.setCaption("Click Me");

        // Save the document; you may also use SaveFormat.DOCM for macro‑enabled files
        String outputPath = "C:/Temp/ActiveXButton.docx";
        doc.save(outputPath);
        System.out.println("Document saved to " + outputPath);
    }
}
```

**ผลลัพธ์ที่คาดหวัง**: หลังจากรัน คอนโซลจะแสดงตำแหน่งการบันทึก การเปิดไฟล์ที่สร้างใน Word จะเห็นปุ่มที่วางประมาณกลางหน้า พร้อมป้าย “Click Me”. การคลิกจะเรียกเหตุการณ์คลิกของ ActiveX มาตรฐาน (คุณต้องผูกแมโคร VBA เพื่อทำการตอบสนอง).

## สรุป

ตอนนี้คุณรู้แล้วว่า **how to insert ActiveX** คอนโทรล CommandButton ลงในเอกสาร Word ด้วยโปรแกรมโดยใช้ Aspose.Words และคุณได้เห็นวิธี **set button caption**, การกำหนดตำแหน่งและขนาดของคอนโทรลอย่างชัดเจน วิธีนี้ช่วยขจัดงาน UI แบบแมนนวล ผสานรวมอย่างสะอาดกับเครื่องมือสร้างรายงานอัตโนมัติ และให้คุณควบคุมทั้งหมด

## คุณควรเรียนรู้อะไรต่อไป?

บทแนะนำต่อไปนี้ครอบคลุมหัวข้อที่เกี่ยวข้องอย่างใกล้ชิดและต่อยอดจากเทคนิคที่แสดงในคู่มือนี้ แต่ละแหล่งรวมตัวอย่างโค้ดทำงานเต็มรูปแบบพร้อมคำอธิบายทีละขั้นตอน เพื่อช่วยคุณเชี่ยวชาญฟีเจอร์ API เพิ่มเติมและสำรวจวิธีการทำงานทางเลือกในโปรเจกต์ของคุณ.

- [แทรกรูปร่างในเอกสาร Word ด้วย Aspose.Words for .NET](/words/english/net/working-with-shapes/insert-shape/)
- [แทรกภาพอินไลน์ในเอกสาร Word ด้วย Aspose.Words](/words/english/net/add-content-using-document-builder/insert-inline-image/)
- [แทรกภาพลงในส่วนหัวของเอกสาร Word | Aspose.Words for .NET](/words/english/net/header-footer-formatting/insert-image/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}