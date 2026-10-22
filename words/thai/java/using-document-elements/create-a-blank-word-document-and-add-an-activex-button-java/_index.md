---
category: general
date: 2026-10-16
description: สร้างเอกสาร Word เปล่าด้วย Java และเรียนรู้วิธีเพิ่มปุ่ม ActiveX ตั้งค่าข้อความบนปุ่ม
  และปรับขนาดของปุ่มโดยใช้ Aspose.Words.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- add activex button
- set button caption
- set button dimensions
language: th
lastmod: 2026-10-16
og_description: สร้างเอกสาร Word ว่างด้วย Java จากนั้นเพิ่มปุ่ม ActiveX ตั้งค่าคำบรรยายและกำหนดขนาดโดยใช้
  Aspose.Words.
og_image_alt: Screenshot showing a blank Word document with an ActiveX button inserted
og_title: สร้างเอกสาร Word ว่างและฝังปุ่ม ActiveX – คู่มือ Java
schemas:
- author: Aspose
  dateModified: '2026-10-16'
  description: Create a blank Word document with Java and learn how to add an ActiveX
    button, set its caption, and adjust its dimensions using Aspose.Words.
  headline: Create a blank Word document and add an ActiveX button (Java)
  type: TechArticle
tags:
- Aspose.Words
- Java
- ActiveX
title: สร้างเอกสาร Word ว่างและเพิ่มปุ่ม ActiveX (Java)
url: /th/java/using-document-elements/create-a-blank-word-document-and-add-an-activex-button-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# สร้างเอกสาร Word เปล่าและเพิ่มปุ่ม ActiveX (Java)

หากคุณต้องการ **สร้างเอกสาร Word เปล่า** อย่างอัตโนมัติ คู่มือนี้จะแสดงวิธีทำด้วย Java และ Aspose.Words คุณยังจะได้เรียนรู้วิธี **เพิ่มปุ่ม ActiveX**, **ตั้งค่าคำบรรยายของปุ่ม**, และ **กำหนดขนาดของปุ่ม** เพื่อให้ควบคุมแสดงผลตามที่คุณคาดหวัง

บทเรียนนี้ครอบคลุม:

* การเริ่มต้นไฟล์ Word ว่างด้วย Aspose.Words for Java.  
* การแทรกควบคุม ActiveX `CommandButton`.  
* การกำหนดคำบรรยายและขนาดของปุ่ม.  
* การบันทึกไฟล์ `.docx` สุดท้าย.

คุณควรมีความรู้พื้นฐานเกี่ยวกับ Java และไลบรารี Aspose.Words for Java เวอร์ชันล่าสุด (โค้ดทำงานกับ 23.9 ขึ้นไป) ไม่จำเป็นต้องมีการพึ่งพาเพิ่มเติมใด ๆ

![Create a blank Word document with an ActiveX button](/images/activex-button-example.png){: .align-center alt="สร้างเอกสาร Word เปล่าพร้อมปุ่ม ActiveX"}

## สร้างเอกสาร Word เปล่าด้วย Aspose.Words

ขั้นตอนแรกคือการสร้างอ็อบเจ็กต์ `Document` ว่าง ซึ่งอ็อบเจ็กต์นี้แทนไฟล์ Word ทั้งหมดในหน่วยความจำและให้คลาส `DocumentBuilder` สำหรับการแก้ไข

```java
import com.aspose.words.*;

public class ActiveXButtonDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document
        Document doc = new Document();               // creates an empty .docx structure
        DocumentBuilder builder = new DocumentBuilder(doc);
        
        // The rest of the steps follow here...
```

**ทำไมเรื่องนี้ถึงสำคัญ:**  
การสร้างเอกสารเปล่าให้คุณมีผืนผ้าแคนวาสที่สะอาด ปราศจากสไตล์หรือส่วนที่ซ่อนอยู่ซึ่งอาจรบกวนการคำนวณเลย์เอาต์ในภายหลัง

## เพิ่มปุ่ม ActiveX ลงในเอกสาร

Aspose.Words ให้คุณฝังควบคุม ActiveX แบบเก่าผ่านคลาส `Forms2OleControl` โค้ดต่อไปนี้จะแทรกควบคุม `CommandButton` ที่ตำแหน่งเคอร์เซอร์ปัจจุบัน

```java
        // Step 2: Insert an ActiveX CommandButton control
        Forms2OleControl commandButton = builder.insertForms2OleControl();

        // Define the exact ActiveX class name (CommandButton)
        commandButton.setOleClassName("Forms.CommandButton.1");
```

**เคล็ดลับ:** ค่าของ `setOleClassName` `"Forms.CommandButton.1"` คือ ProgID ของปุ่ม Microsoft Forms มาตรฐาน การใช้ ProgID อื่น (เช่น `"Forms.CheckBox.1"`) จะทำให้แทรกประเภทควบคุมที่แตกต่างกัน

## ตั้งค่าคำบรรยายของปุ่ม

คำบรรยายคือข้อความที่ปรากฏบนปุ่ม คุณสามารถเปลี่ยนได้ตลอดเวลา ก่อนบันทึกเอกสาร

```java
        // Step 3: Set the button's caption
        commandButton.setCaption("Click Me");
```

**ทำไมคุณถึงต้องการสิ่งนี้:** ผู้ใช้จะเข้าใจควบคุมได้เมื่อวัตถุประสงค์ของมันชัดเจน การตั้งค่าคำบรรยายที่มีความหมายช่วยปรับปรุงการใช้งาน โดยเฉพาะเมื่อเอกสารถูกเปิดใน Word บน Windows

## กำหนดขนาดของปุ่ม

ตำแหน่งและขนาดระบุเป็นจุด (1 point = 1/72 นิ้ว) ปรับค่าตามการออกแบบของคุณ

```java
        // Step 4: Define button size and location
        commandButton.setLeft(100);    // distance from the left edge of the page
        commandButton.setTop(200);     // distance from the top edge of the page
        commandButton.setWidth(120);   // width of the button
        commandButton.setHeight(30);   // height of the button
```

**การปรับแต่งทั่วไป:**

| สถานการณ์ | การปรับแต่ง |
|----------|------------|
| ปุ่มขนาดใหญ่สำหรับหน้าจอสัมผัส | เพิ่ม `setWidth` และ `setHeight` อย่างสัดส่วน |
| ปุ่มอยู่กึ่งกลางหน้า | คำนวณ `left = (pageWidth - width) / 2` |
| หลายปุ่มในคอลัมน์ | เพิ่มค่า `setTop` สำหรับแต่ละปุ่มใหม่ |

## บันทึกเอกสารที่มีปุ่ม ActiveX

สุดท้ายให้เขียนเอกสารลงดิสก์ ฟอร์แมต `.docx` จะรักษาควบคุม ActiveX ไว้สำหรับเวอร์ชัน Windows ของ Microsoft Word

```java
        // Step 5: Save the document
        doc.save("ActiveXCommandButton.docx");
    }
}
```

**ผลลัพธ์ที่คาดหวัง:** การเปิด `ActiveXCommandButton.docx` ใน Word (Windows) จะแสดงหน้าว่างพร้อมปุ่มที่คลิกได้ที่มีคำว่า **Click Me** อยู่ห่างจากขอบซ้าย 100 pt และจากขอบบน 200 pt

## ตัวอย่างเต็มที่สามารถรันได้

คัดลอกคลาสทั้งหมดด้านล่างนี้ไปยัง IDE ของคุณ เพิ่ม JAR ของ Aspose.Words for Java ไปยัง classpath ของโปรเจค แล้วรัน

```java
import com.aspose.words.*;

public class ActiveXButtonDemo {
    public static void main(String[] args) throws Exception {
        // Create a new blank document
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert an ActiveX CommandButton control
        Forms2OleControl commandButton = builder.insertForms2OleControl();
        commandButton.setOleClassName("Forms.CommandButton.1");

        // Set button caption
        commandButton.setCaption("Click Me");

        // Set button dimensions and position
        commandButton.setLeft(100);    // points from left edge
        commandButton.setTop(200);     // points from top edge
        commandButton.setWidth(120);   // width in points
        commandButton.setHeight(30);   // height in points

        // Save the document
        doc.save("ActiveXCommandButton.docx");
    }
}
```

การรันโปรแกรมจะสร้างไฟล์ `ActiveXCommandButton.docx` ในไดเรกทอรีทำงาน เปิดด้วย Microsoft Word (Windows) เพื่อตรวจสอบว่าปุ่มปรากฏตามที่กำหนดไว้

## ทำไมวิธีนี้ถึงแนะนำ

* **ความเรียบง่าย:** ใช้เฉพาะ API หลักของ Aspose.Words; ไม่ต้องใช้ COM interop หรือไลบรารีเพิ่มเติม  
* **ความพกพา:** โค้ดทำงานบนแพลตฟอร์มใดก็ได้ที่รองรับ Java แม้ว่าปุ่ม ActiveX จะทำงานได้เฉพาะบน Word เวอร์ชัน Windows  
* **การบำรุงรักษา:** ทุกคุณสมบัติ (คำบรรยาย, ขนาด, ตำแหน่ง) ถูกตั้งค่าผ่านเมธอดที่ชัดเจนและอธิบายตัวเอง ทำให้การปรับเปลี่ยนในอนาคตทำได้ง่าย

## ข้อผิดพลาดทั่วไปและวิธีหลีกเลี่ยง

| ข้อผิดพลาด | วิธีแก้ |
|------------|----------|
| ปุ่มไม่ปรากฏใน Word บน macOS หรือ Linux | ActiveX ควบคุมทำงานได้เฉพาะ Windows ใช้ควบคุมอื่น (เช่น content control) สำหรับเอกสารข้ามแพลตฟอร์ม |
| คำบรรยายถูกตัด | ตรวจสอบให้ความกว้างของปุ่มเพียงพอสำหรับข้อความ; เพิ่ม `setWidth` หรือใช้คำบรรยายสั้นลง |
| ปุ่มทับกับเนื้อหาอื่น | ปรับค่า `setTop` และ `setLeft` หรือแทรกย่อหน้าใหม่ก่อนควบคุมเพื่อให้มีพื้นที่ของตน |

## ขั้นตอนต่อไป

ตอนนี้คุณสามารถ **สร้างเอกสาร Word เปล่า**, **เพิ่มปุ่ม ActiveX**, **ตั้งค่าคำบรรยายของปุ่ม**, และ **กำหนดขนาดของปุ่ม** แล้ว คุณอาจสำรวจต่อไป:

* เพิ่มโค้ดจัดการเหตุการณ์ผ่าน VBA macro (ต้องฝังโมดูล macro)  
* แทรกหลายควบคุมในรูปแบบตารางสำหรับเอกสารแบบฟอร์ม  
* ใช้ Aspose.Words **FormField** API สำหรับโซลูชันฟอร์มข้ามแพลตฟอร์ม

ลองทดลองกับขนาด, ตำแหน่ง, และคำบรรยายที่แตกต่างเพื่อให้ตรงกับการออกแบบเอกสารของคุณเอง ขอให้สนุกกับการเขียนโค้ด!

## สิ่งที่คุณควรเรียนต่อไป

บทเรียนต่อไปนี้ครอบคลุมหัวข้อที่เกี่ยวข้องอย่างใกล้ชิดและต่อยอดจากเทคนิคที่แสดงในคู่มือนี้ แต่ละแหล่งข้อมูลมีตัวอย่างโค้ดทำงานเต็มรูปแบบพร้อมคำอธิบายขั้นตอนเพื่อช่วยคุณเชี่ยวชาญฟีเจอร์ API เพิ่มเติมและสำรวจวิธีการทำงานแบบอื่นในโปรเจคของคุณ

- [สร้างเอกสาร Word ด้วย Java – เพิ่มรูปสี่เหลี่ยมผืนผ้าพร้อมเงา](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [วิธีสร้างฟิลด์ฟอร์มและเพิ่มเนื้อหาโดยใช้ DocumentBuilder ใน Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [เพิ่มลายน้ำในเอกสารโดยใช้ Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-watermarks-to-documents/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}