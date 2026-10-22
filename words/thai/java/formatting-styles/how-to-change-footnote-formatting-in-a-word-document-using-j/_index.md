---
category: general
date: 2026-09-11
description: เรียนรู้วิธีเปลี่ยนรูปแบบเชิงอรรถใน Java ด้วย Aspose.Words คู่มือนี้อธิบายวิธีแก้ไขเชิงอรรถ,
  ปรับปรุงสไตล์ของเชิงอรรถ, และแก้ไขตัวคั่นของเชิงอรรถ.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- change footnote formatting
- how to edit footnote
- update footnote style
- modify footnote separator
language: th
lastmod: 2026-09-11
og_description: เปลี่ยนรูปแบบเชิงอรรถใน Java ด้วย Aspose.Words. ปฏิบัติตามคู่มือฉบับเต็มนี้เพื่อแก้ไขเชิงอรรถ,
  ปรับปรุงสไตล์เชิงอรรถ, และแก้ไขตัวคั่นเชิงอรรถ.
og_image_alt: Screenshot showing change footnote formatting in a Java editor
og_title: เปลี่ยนรูปแบบเชิงอรรถใน Java – คู่มือขั้นตอนต่อขั้นตอน
schemas:
- author: Aspose
  dateModified: '2026-09-11'
  description: Learn how to change footnote formatting in Java with Aspose.Words.
    This guide explains how to edit footnote, update footnote style, and modify footnote
    separator.
  headline: How to change footnote formatting in a Word document using Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- Footnote
- Document processing
title: วิธีเปลี่ยนรูปแบบเชิงอรรถในเอกสาร Word ด้วย Java
url: /th/java/formatting-styles/how-to-change-footnote-formatting-in-a-word-document-using-j/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# วิธีเปลี่ยนรูปแบบเชิงอรรถในเอกสาร Word ด้วย Java

หากคุณต้องการ **เปลี่ยนรูปแบบเชิงอรรถ** ในเอกสาร Word, บทแนะนำนี้จะพาคุณผ่านขั้นตอนที่แน่นอนโดยใช้ Aspose.Words for Java ไม่ว่าคุณจะกำลังสร้าง pipeline การเผยแพร่หรือเพียงต้องการ **วิธีแก้ไขเชิงอรรถ** อย่างโปรแกรม, โซลูชันด้านล่างครอบคลุมทุกอย่างตั้งแต่การโหลดไฟล์จนถึงการบันทึกเวอร์ชันที่อัปเดต

คุณจะได้เรียนรู้วิธี **อัปเดตรูปแบบเชิงอรรถ**, ทำให้ตัวคั่นเชิงอรรถเป็นตัวหนา, และแม้กระทั่ง **แก้ไขคุณสมบัติตัวคั่นเชิงอรรถ** เช่น ขนาดฟอนต์หรือสี คู่มือสมมติว่าคุณมีความรู้พื้นฐานของ Java และมีใบอนุญาต Aspose.Words for Java ที่ทำงานได้

## ข้อกำหนดเบื้องต้น

* Java 17 หรือใหม่กว่า ที่ติดตั้งไว้
* Aspose.Words for Java (เวอร์ชัน 23.12 หรือใหม่กว่า) ที่เพิ่มเข้าไปใน classpath ของโปรเจกต์
* เอกสาร Word (`input.docx`) ที่มีอย่างน้อยหนึ่งเชิงอรรถ
* IDE หรือเครื่องมือ build (Maven/Gradle) เพื่อคอมไพล์และรันโค้ด

หากคุณไม่แน่ใจว่าจะเพิ่ม Aspose.Words ไปยังโปรเจกต์ Maven อย่างไร, ให้ใส่ dependency ต่อไปนี้ใน `pom.xml` ของคุณ:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.12</version>
</dependency>
```

## เปลี่ยนรูปแบบเชิงอรรถด้วย Aspose.Words for Java

แกนหลักของโซลูชันคือโปรแกรม Java สั้น ๆ ที่โหลดเอกสาร, เข้าถึงย่อหน้าตัวคั่นเชิงอรรถ, เปลี่ยนรูปแบบของมัน, และบันทึกผลลัพธ์ โค้ดนี้เป็นอิสระเต็มรูปแบบ, ดังนั้นคุณสามารถคัดลอกไปยังคลาสใหม่และรันได้ทันที

```java
import com.aspose.words.*;

public class ChangeFootnoteFormatting {
    public static void main(String[] args) throws Exception {
        // Step 1: Load the Word document
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // Step 2: Retrieve the footnote separator paragraph
        Paragraph footnoteSeparator = doc.getFootnoteSeparator();

        // Defensive check – the separator may be empty in some documents
        if (footnoteSeparator.getRuns().getCount() == 0) {
            // Create a new run so we have something to format
            Run run = new Run(doc);
            run.setText("\u2022"); // bullet character as placeholder
            footnoteSeparator.appendChild(run);
        }

        // Step 3: Change the first run's formatting – this is where we
        //          modify footnote separator appearance
        Run firstRun = footnoteSeparator.getRuns().get(0);
        Font font = firstRun.getFont();
        font.setBold(true);                // make the separator bold
        font.setItalic(true);              // optional: also italic
        font.setSize(10.0);                // set font size to 10 pt
        font.setColor(java.awt.Color.GRAY); // change color to a subtle gray

        // Step 4: Save the updated document
        doc.save("YOUR_DIRECTORY/output.docx");
    }
}
```

### ทำไมแต่ละขั้นตอนถึงสำคัญ

* **Loading the document** (`new Document`) สร้างการแสดงผลในหน่วยความจำที่ Aspose.Words สามารถจัดการได้.  
* **Retrieving the footnote separator** (`getFootnoteSeparator`) ให้คุณเข้าถึงย่อหน้าที่แยกเชิงอรรถจากข้อความหลักโดยตรง นี่คือองค์ประกอบที่คุณต้องกำหนดเป้าหมายเมื่อคุณต้องการ **change footnote formatting**.  
* **Formatting the run** (`setBold`, `setItalic`, `setSize`, `setColor`) แสดงวิธี **modify footnote separator** คุณสามารถเพิ่มคุณลักษณะฟอนต์เพิ่มเติมได้ที่นี่ เช่น การขีดเส้นใต้หรือไฮไลท์ เพื่อควบคุมลักษณะการแสดงผลอย่างเต็มที่.  
* **Saving the document** เขียนการเปลี่ยนแปลงกลับไปยังดิสก์, สร้างไฟล์ใหม่ (`output.docx`) ที่สะท้อนสไตล์เชิงอรรถที่อัปเดต.  

> **Pro tip:** หากเอกสารต้นฉบับของคุณใช้ตัวคั่นเชิงอรรถที่กำหนดเองซึ่งมีหลาย run (เช่น การผสมสัญลักษณ์), ให้วนลูปผ่าน `footnoteSeparator.getRuns()` และใช้การตั้งค่า `Font` เดียวกันกับแต่ละ run เพื่อให้สไตล์สอดคล้องกัน.

## วิธีแก้ไขตัวคั่นเชิงอรรถโดยโปรแกรม

บางครั้งคุณอาจต้องการแก้ไขไม่เพียงตัวคั่นเท่านั้น แต่ยังรวมถึงข้อความเชิงอรรถด้วย API เดียวกันสามารถใช้เข้าถึงแต่ละเชิงอรรถ, ปรับรูปแบบย่อหน้า, หรือเปลี่ยนสไตล์การนับเลขได้

```java
for (Footnote footnote : (Iterable<Footnote>) doc.getFootnotes()) {
    // Example: make all footnote text italic and 9 pt
    for (Paragraph para : (Iterable<Paragraph>) footnote.getParagraphs()) {
        para.getParagraphFormat().setStyleIdentifier(StyleIdentifier.FOOTNOTE_TEXT);
        para.getRuns().forEach(run -> {
            Font f = run.getFont();
            f.setItalic(true);
            f.setSize(9.0);
        });
    }
}
```

โค้ดส่วนข้างต้นแสดง **how to edit footnote** เนื้อหาเชิงอรรถหลังจากที่คุณได้ **changed footnote formatting** สำหรับตัวคั่นแล้ว โดยการวนลูปผ่าน `doc.getFootnotes()` คุณจะทำให้ทุกเชิงอรรถสืบทอดสไตล์เดียวกัน ซึ่งเป็นสิ่งสำคัญสำหรับเอกสารที่ดูเป็นมืออาชีพ

## อัปเดตสไตล์เชิงอรรถเพื่อให้ลักษณะเอกสารสอดคล้องกัน

หากคุณต้องการทำงานกับสไตล์แทนการจัดการ run แยกแต่ละอัน, Aspose.Words ให้คุณสร้างหรือแก้ไขอ็อบเจ็กต์ `Style` แล้วนำไปใช้กับเชิงอรรถและตัวคั่น วิธีนี้มีประโยชน์เมื่อคุณต้องการ **update footnote style** ในหลายเอกสาร

```java
// Create or retrieve a style named "MyFootnoteStyle"
Style footnoteStyle = doc.getStyles().add(StyleType.PARAGRAPH, "MyFootnoteStyle");
footnoteStyle.getFont().setBold(true);
footnoteStyle.getFont().setSize(10);
footnoteStyle.getFont().setColor(java.awt.Color.DARK_GRAY);

// Apply the style to the separator
footnoteSeparator.getParagraphFormat().setStyle(footnoteStyle);

// Apply the same style to every footnote paragraph
for (Footnote fn : (Iterable<Footnote>) doc.getFootnotes()) {
    for (Paragraph p : (Iterable<Paragraph>) fn.getParagraphs()) {
        p.getParagraphFormat().setStyle(footnoteStyle);
    }
}
```

การใช้สไตล์เฉพาะทำให้การบำรุงรักษาในอนาคตง่ายขึ้น — เปลี่ยนสไตล์เพียงครั้งเดียว, แล้วทุกเชิงอรรถและตัวคั่นจะอัปเดตโดยอัตโนมัติ เทคนิคนี้เป็นวิธีที่แนะนำในการ **update footnote style** ในเวิร์กโฟลว์การเผยแพร่ขนาดใหญ่

## แก้ไขตัวคั่นเชิงอรรถให้สอดคล้องกับแบรนด์ของคุณ

แนวทางแบรนด์บางครั้งกำหนดให้ตัวคั่นเชิงอรรถใช้อักขระเฉพาะ (เช่น ดาว) หรือเส้นที่กำหนดเอง Aspose.Words อนุญาตให้คุณแทนที่เนื้อหาตัวคั่นเริ่มต้นโดยสมบูรณ์

```java
// Remove existing runs
footnoteSeparator.getRuns().clear();

// Insert a custom separator line
Run customRun = new Run(doc);
customRun.setText("--- Custom Separator ---");
Font customFont = customRun.getFont();
customFont.setBold(true);
customFont.setSize(8);
customFont.setColor(java.awt.Color.BLUE);
footnoteSeparator.appendChild(customRun);
```

โค้ดข้างต้น **modifies footnote separator** โดยลบ run ที่มีอยู่ทั้งหมดและแทรก run ใหม่พร้อมข้อความและรูปแบบที่ต้องการ คุณยังสามารถใช้อักขระ Unicode เช่น `\u2022` (bullet) หรือ `\u2014` (em dash) เพื่อให้ได้ผลลัพธ์ภาพที่ตรงกับแบรนด์ของคุณ

## ผลลัพธ์ที่คาดหวัง

หลังจากรันโปรแกรม:

* ตัวคั่นเชิงอรรถใน `output.docx` ปรากฏเป็น **bold**, **italic**, ขนาด 10 pt, และสีเทา (หรือสีใดก็ได้ที่คุณตั้งค่า).
* ย่อหน้าเชิงอรรถทั้งหมดใช้สไตล์ที่คุณกำหนด, ทำให้ลักษณะโดยรวมของเอกสารสอดคล้องกัน.
* หากคุณได้แทนที่ข้อความตัวคั่น, เส้นกำหนดเองใหม่จะแสดงตรงตำแหน่งที่เส้นเดิมเคยอยู่.

เปิดไฟล์ที่ได้ใน Microsoft Word หรือ LibreOffice Writer เพื่อยืนยันการเปลี่ยนแปลง คุณควรเห็นตัวคั่นที่อัปเดตอยู่เหนือเชิงอรรถแรก, และข้อความเชิงอรรถควรสะท้อนการแก้ไขสไตล์ที่คุณได้ทำ.

## ปัญหาที่พบบ่อยและวิธีหลีกเลี่ยง

| ปัญหา | สาเหตุ | วิธีแก้ |
|-------|--------|--------|
| `footnoteSeparator.getRuns().getCount() == 0` throws an exception | เอกสารบางไฟล์มีย่อตัวย่อหน้าตัวคั่นที่ว่างเปล่า | เพิ่มการตรวจสอบเชิงป้องกันและสร้าง run หากไม่มี (ดูตัวอย่างโค้ด). |
| Font changes are not visible | เอกสารใช้ธีมที่เขียนทับการจัดรูปแบบโดยตรง | ตั้งค่า `font.setThemeFont(null)` หรือใช้สไตล์กำหนดเองแทนการจัดรูปแบบโดยตรง. |
| Saved file does not reflect changes | ไฟล์ต้นฉบับยังเปิดอยู่ใน Word ทำให้ล็อคเส้นทางเอาต์พุต | ปิดไฟล์ที่เปิดอยู่ทั้งหมดก่อนรันโปรแกรม, หรือ

## คุณควรเรียนรู้อะไรต่อไป?

บทแนะนำต่อไปนี้ครอบคลุมหัวข้อที่เกี่ยวข้องอย่างใกล้ชิดซึ่งต่อยอดจากเทคนิคที่แสดงในคู่มือนี้ แต่ละแหล่งข้อมูลรวมตัวอย่างโค้ดที่ทำงานได้ครบถ้วนพร้อมคำอธิบายทีละขั้นตอน เพื่อช่วยคุณเชี่ยวชาญคุณลักษณะ API เพิ่มเติมและสำรวจแนวทางการนำไปใช้ทางเลือกในโปรเจกต์ของคุณ

- [การประมวลผลคำด้วยเชิงอรรถและอ้างอิงท้ายหน้า](/words/english/net/working-with-footnote-and-endnote/)
- [ตั้งตำแหน่งเชิงอรรถและอ้างอิงท้ายหน้า](/words/english/net/working-with-footnote-and-endnote/set-footnote-and-end-note-position/)
- [วิธีแสดงข้อมูลเวอร์ชันของ Aspose.Words ใน Java: คู่มือฉบับสมบูรณ์](/words/english/java/getting-started/aspose-words-java-version-info/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}