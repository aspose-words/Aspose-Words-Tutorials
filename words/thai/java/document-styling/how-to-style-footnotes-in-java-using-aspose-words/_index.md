---
category: general
date: 2026-10-07
description: วิธีจัดรูปแบบเชิงอรรถใน Java – เรียนรู้การเปลี่ยนตัวคั่นเชิงอรรถ, แก้ไขการจัดรูปแบบตัวคั่นเชิงอรรถ,
  และบันทึกเอกสารพร้อมเชิงอรรถที่จัดรูปแบบแล้ว.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to style footnotes
- change footnote separator
- edit footnote separator
- format footnote separator
- access footnote separator
language: th
lastmod: 2026-10-07
og_description: วิธีจัดรูปแบบเชิงอรรถใน Java ด้วย Aspose.Words บทเรียนนี้จะแสดงวิธีเปลี่ยนตัวคั่นเชิงอรรถ
  แก้ไขการจัดรูปแบบตัวคั่นเชิงอรรถ และสร้างเอกสารที่เรียบหรู
og_image_alt: Screenshot illustrating how to style footnotes in a Java Word processing
  example
og_title: วิธีจัดรูปแบบเชิงอรรถใน Java – คู่มือการเขียนโปรแกรมครบถ้วน
schemas:
- author: Aspose
  dateModified: '2026-10-07'
  description: how to style footnotes in Java – learn to change footnote separator,
    edit footnote separator formatting, and save the document with styled footnotes.
  headline: how to style footnotes in Java using Aspose.Words
  type: TechArticle
- description: how to style footnotes in Java – learn to change footnote separator,
    edit footnote separator formatting, and save the document with styled footnotes.
  name: how to style footnotes in Java using Aspose.Words
  steps:
  - name: Load the source document.
    text: Load the source document.
  - name: Iterate through each footnote and **access footnote separator** runs.
    text: Iterate through each footnote and **access footnote separator** runs.
  - name: Apply the desired styling (bold, color, underline, etc.).
    text: Apply the desired styling (bold, color, underline, etc.).
  - name: Save the document with the updated footnote separator.
    text: Save the document with the updated footnote separator.
  type: HowTo
tags:
- Aspose.Words
- Java
- Word automation
title: วิธีจัดรูปแบบเชิงอรรถใน Java ด้วย Aspose.Words
url: /th/java/document-styling/how-to-style-footnotes-in-java-using-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# วิธีจัดรูปแบบเชิงอรรถใน Java ด้วย Aspose.Words

หากคุณต้องการจัดรูปแบบเชิงอรรถในเอกสาร Word ด้วย Java คำแนะนำนี้จะแสดง **วิธีจัดรูปแบบเชิงอรรถ** ด้วย Aspose.Words คุณจะได้เรียนรู้วิธีเปลี่ยนตัวคั่นเชิงอรรถ, แก้ไขการจัดรูปแบบตัวคั่นเชิงอรรถ, และบันทึกเอกสารที่แก้ไขแล้วในไม่กี่ขั้นตอนที่ชัดเจน

การทำงานกับเชิงอรรถมักหมายถึงการปรับเส้นตัวคั่นที่แสดงระหว่างข้อความหลักและรายการเชิงอรรถ เมื่อจบการสอนนี้คุณจะสามารถ **เข้าถึงตัวคั่นเชิงอรรถ** (footnote separator) runs, ใส่สไตล์แบบหนาหรือสี, และควบคุมลักษณะโดยรวมของเชิงอรรถได้โดยไม่ต้องออกจาก IDE

## ข้อกำหนดเบื้องต้น

ก่อนเริ่มทำงาน โปรดตรวจสอบว่าคุณมี:

* Java 17 หรือใหม่กว่า
* Maven 3.6+ (หรือ Gradle) เพื่อจัดการ dependencies
* ใบอนุญาต Aspose.Words for Java ที่ถูกต้อง (เวอร์ชันทดลองฟรีใช้ได้สำหรับตัวอย่างนี้)
* เอกสาร Word ต้นฉบับที่มีอย่างน้อยหนึ่งเชิงอรรถ (เช่น `Footnotes.docx`)

ข้อกำหนดเหล่านี้ทำให้โค้ดทำงานได้อย่างราบรื่นบน Java runtime รุ่นใหม่และช่วยให้คุณมุ่งเน้นที่ **วิธีจัดรูปแบบเชิงอรรถ** แทนปัญหาการตั้งค่า

## วิธีจัดรูปแบบเชิงอรรถ – แนวทางโดยรวม

กระบวนการประกอบด้วยสี่ขั้นตอนหลัก:

1. โหลดเอกสารต้นฉบับ
2. วนลูปแต่ละเชิงอรรถและ **เข้าถึงตัวคั่นเชิงอรรถ** runs
3. ใส่สไตล์ที่ต้องการ (หนา, สี, ขีดเส้นใต้ ฯลฯ)
4. บันทึกเอกสารพร้อมตัวคั่นเชิงอรรถที่อัปเดต

แต่ละขั้นตอนสอดคล้องกับบรรทัดโค้ด ทำให้การนำไปใช้ง่ายต่อการติดตามและแก้ไข

## ขั้นตอนที่ 1: ตั้งค่าโปรเจกต์ Maven

สร้างโปรเจกต์ Maven ใหม่ (หรือเพิ่มในโปรเจกต์ที่มีอยู่) และเพิ่ม dependency ของ Aspose.Words:

```xml
<!-- pom.xml -->
<dependencies>
    <dependency>
        <groupId>com.aspose</groupId>
        <artifactId>aspose-words</artifactId>
        <version>24.10</version> <!-- Use the latest version -->
    </dependency>
</dependencies>
```

> **เคล็ดลับ:** ควรอัปเดตเวอร์ชันของไลบรารีให้เป็นรุ่นล่าสุด; รุ่นใหม่มักมีการแก้บั๊กสำหรับการจัดการเชิงอรรถ

## ขั้นตอนที่ 2: โหลดเอกสารต้นฉบับที่มีเชิงอรรถ

```java
import com.aspose.words.*;

public class FootnoteStyler {
    public static void main(String[] args) throws Exception {
        // Load the Word file that has footnotes.
        Document doc = new Document("YOUR_DIRECTORY/Footnotes.docx");
```

อ็อบเจกต์ `Document` แทนไฟล์ Word ทั้งหมด การโหลดเป็นการกระทำแรกที่เป็นรูปธรรมใน **วิธีจัดรูปแบบเชิงอรรถ**

## ขั้นตอนที่ 3: วนลูปแต่ละเชิงอรรถและ **เข้าถึงตัวคั่นเชิงอรรถ**

```java
        // Iterate through all footnotes in the document.
        for (Footnote footnote : (Iterable<Footnote>) doc.getFootnotes()) {
            // The separator is a Run that appears between the main text and the footnote list.
            Run separator = footnote.getSeparator();

            // Guard against unexpected null values (rare but possible with corrupted files).
            if (separator != null) {
                // Apply desired styling to the separator run.
                separator.getFont().setBold(true);          // change footnote separator to bold
                separator.getFont().setColor(Color.BLUE);   // optional: set a custom color
                separator.getFont().setUnderline(Underline.SINGLE);
            }
        }
```

ในบล็อกนี้เราจะ **เข้าถึงตัวคั่นเชิงอรรถ** runs ผ่าน `footnote.getSeparator()` อ็อบเจกต์ `Run` ให้การควบคุมเต็มรูปแบบต่อการจัดรูปแบบข้อความ ทำให้คุณสามารถ **เปลี่ยนลักษณะตัวคั่นเชิงอรรถ** ได้ด้วยบรรทัดโค้ดเดียว

### ทำไมต้องใช้ `Footnote.getSeparator()`

* `Footnote.getSeparator()` คืนค่า run ที่บรรจุเส้นตัวคั่น
* เป็นจุดเข้าถึง API เพียงจุดเดียวที่ให้คุณ **แก้ไขตัวคั่นเชิงอรรถ** โดยตรง
* การแก้ไขคุณสมบัติ `Font` ของ run จะอัปเดตเส้นตัวคั่นที่มองเห็นได้สำหรับทุกเชิงอรรถที่ใช้สไตล์เดียวกัน

## ขั้นตอนที่ 4: (ทางเลือก) จัดรูปแบบตัวคั่นต่อเนื่องและข้อความแจ้งต่อเนื่อง

Word แยกประเภทตัวคั่นออกเป็นสามแบบ:

| ประเภท                     | วิธีการ API                               | กรณีใช้งานทั่วไป |
|----------------------------|------------------------------------------|-------------------|
| ตัวคั่นหลัก (Primary separator)        | `Footnote.getSeparator()`                | แยกข้อความหลักจากเชิงอรรถแรก |
| ตัวคั่นต่อเนื่อง (Continuation separator)   | `Footnote.getContinuationSeparator()`    | แยกหน้าต่อเนื่องของเชิงอรรถ |
| ข้อความแจ้งต่อเนื่อง (Continuation notice)      | `Footnote.getContinuationNotice()`       | แสดงข้อความ “Continued…” ในหน้าถัดไป |

หากคุณต้องการ **จัดรูปแบบตัวคั่นเชิงอรรถ** สำหรับหน้าต่อเนื่อง ให้เพิ่มโค้ดต่อไปนี้ภายในลูป:

```java
            // Continuation separator (optional)
            Run contSeparator = footnote.getContinuationSeparator();
            if (contSeparator != null) {
                contSeparator.getFont().setItalic(true);
                contSeparator.getFont().setSize(9);
            }

            // Continuation notice (optional)
            Run contNotice = footnote.getContinuationNotice();
            if (contNotice != null) {
                contNotice.getFont().setColor(Color.GRAY);
            }
```

ส่วนโค้ดเหล่านี้แสดงวิธี **แก้ไขตัวคั่นเชิงอรรถ** นอกเหนือจากเส้นหลัก ให้คุณควบคุมการจัดวางเชิงอรรถได้อย่างเต็มที่

## ขั้นตอนที่ 5: บันทึกเอกสารที่แก้ไขแล้ว

```java
        // Save the document with the styled footnote separators.
        doc.save("YOUR_DIRECTORY/FootnotesStyled.docx");
    }
}
```

การบันทึกไฟล์จะเขียนการเปลี่ยนแปลงสไตล์ทั้งหมดลงดิสก์ ทำให้กระบวนการ **วิธีจัดรูปแบบเชิงอรรถ** เสร็จสมบูรณ์

## ตัวอย่างเต็มที่สามารถรันได้

รวมทุกส่วนเข้าด้วยกันจะได้โปรแกรมอิสระที่คุณสามารถคัดลอก, คอมไพล์, และรันได้:

```java
import com.aspose.words.*;
import java.awt.Color;

/**
 * Demonstrates how to style footnotes in a Word document using Aspose.Words for Java.
 * The example loads a document, makes the footnote separator bold and blue,
 * optionally styles continuation elements, and saves the result.
 */
public class FootnoteStyler {
    public static void main(String[] args) throws Exception {
        // 1. Load the source document.
        Document doc = new Document("YOUR_DIRECTORY/Footnotes.docx");

        // 2. Iterate through each footnote.
        for (Footnote footnote : (Iterable<Footnote>) doc.getFootnotes()) {
            // 3a. Access and style the primary separator.
            Run separator = footnote.getSeparator();
            if (separator != null) {
                separator.getFont().setBold(true);          // change footnote separator
                separator.getFont().setColor(Color.BLUE);   // set a custom color
                separator.getFont().setUnderline(Underline.SINGLE);
            }

            // 3b. (Optional) Style continuation separator.
            Run contSeparator = footnote.getContinuationSeparator();
            if (contSeparator != null) {
                contSeparator.getFont().setItalic(true);
                contSeparator.getFont().setSize(9);
            }

            // 3c. (Optional) Style continuation notice.
            Run contNotice = footnote.getContinuationNotice();
            if (contNotice != null) {
                contNotice.getFont().setColor(Color.GRAY);
            }
        }

        // 4. Save the modified document.
        doc.save("YOUR_DIRECTORY/FootnotesStyled.docx");
    }
}
```

**ผลลัพธ์ที่คาดหวัง:** เปิดไฟล์ `FootnotesStyled.docx` ด้วย Microsoft Word เส้นตัวคั่นระหว่างข้อความหลักและรายการเชิงอรรถจะปรากฏเป็นแบบหนา, สีน้ำเงิน, และขีดเส้นใต้ หากเอกสารมีเชิงอรรถที่ขยายหลายหน้า ตัวคั่นต่อเนื่องจะเป็นแบบเอียงและขนาดเล็กกว่า ส่วนข้อความแจ้งต่อเนื่องจะเป็นสีเทา

## คำถามที่พบบ่อยและการจัดการกรณีขอบ

| คำถาม | คำตอบ |
|----------|--------|
| *ถ้าเชิงอรรถไม่มีตัวคั่นล่ะ?* | `Footnote.getSeparator()` จะคืนค่า `null`. โค้ดตรวจสอบ `null` ก่อนใส่สไตล์ เพื่อป้องกัน `NullPointerException`. |
| *ฉันสามารถใส่สไตล์ต่างกันให้กับเชิงอรรถแรกเท่านั้นได้ไหม?* | ทำได้. เพิ่มตัวนับภายในลูปและใส่การจัดรูปแบบตามเงื่อนไขเมื่อ `index == 0`. |
| *วิธีนี้ทำงานกับไฟล์ .doc ได้หรือไม่?* | Aspose.Words รองรับทั้ง `.doc` และ `.docx`. โหลดพาธที่เหมาะสมและเรียก API เดียวกัน. |
| *ฉันจะคืนสไตล์เดิมได้อย่างไร?* | เก็บค่า `Font` ดั้งเดิมไว้ก่อนทำการเปลี่ยนแปลง |

## สิ่งที่คุณควรเรียนต่อไป

บทแนะนำต่อไปนี้ครอบคลุมหัวข้อที่เกี่ยวข้องอย่างใกล้ชิดและต่อยอดจากเทคนิคในคู่มือนี้ แต่ละแหล่งรวมตัวอย่างโค้ดทำงานเต็มรูปแบบพร้อมคำอธิบายทีละขั้นตอน เพื่อช่วยให้คุณเชี่ยวชาญฟีเจอร์ API เพิ่มเติมและสำรวจวิธีการทำงานทางเลือกในโปรเจกต์ของคุณ

- [How to save document as pdf with Aspose.Words for Java](/words/english/java/document-loading-and-saving/saving-documents-as-pdf/)
- [How to Change Cell Borders in Tables – Aspose.Words for Java](/words/english/java/document-conversion-and-export/formatting-tables-and-table-styles/)
- [How to Add Watermark – Document Conversion and Export with Aspose.Words for Java](/words/english/java/document-conversion-and-export/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}