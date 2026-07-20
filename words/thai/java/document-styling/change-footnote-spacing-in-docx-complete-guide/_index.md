---
category: general
date: 2026-07-20
description: เปลี่ยนระยะห่างของเชิงอรรถในไฟล์ DOCX ได้อย่างง่ายดาย เรียนรู้วิธีตั้งค่าระยะห่าง
  ปรับตัวคั่นเชิงอรรถ และตั้งค่าระยะห่างบรรทัดของย่อหน้าด้วย Java.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- change footnote spacing
- how to set spacing
- adjust footnote separator
- set paragraph line spacing
- change line spacing docx
language: th
lastmod: 2026-07-20
og_description: เปลี่ยนระยะห่างของเชิงอรรถในไฟล์ DOCX อย่างรวดเร็ว คู่มือนี้แสดงวิธีตั้งค่าระยะห่าง
  ปรับตัวคั่นเชิงอรรถ และปรับแต่งระยะห่างบรรทัดของย่อหน้าใน Java.
og_image_alt: Screenshot showing Java code that changes footnote spacing in a DOCX
  document
og_title: เปลี่ยนระยะห่างของเชิงอรรถใน DOCX – คู่มือแบบทีละขั้นตอน
schemas:
- author: Aspose
  dateModified: '2026-07-20'
  description: Change footnote spacing in DOCX files easily. Learn how to set spacing,
    adjust footnote separator, and set paragraph line spacing with Java.
  headline: Change footnote spacing in DOCX – Complete Guide
  type: TechArticle
tags:
- footnote
- docx
- java
- spacing
title: เปลี่ยนระยะห่างของเชิงอรรถใน DOCX – คู่มือฉบับสมบูรณ์
url: /th/java/document-styling/change-footnote-spacing-in-docx-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# เปลี่ยนระยะห่างของเชิงอรรถใน DOCX – คู่มือฉบับสมบูรณ์

เคยต้องการ **เปลี่ยนระยะห่างของเชิงอรรถ** ในเอกสาร Word แต่ไม่แน่ใจว่าจะเริ่มจากตรงไหนหรือไม่? คุณไม่ได้อยู่คนเดียว ไม่ว่าคุณจะกำลังปรับแต่งวิทยานิพนธ์หรือแก้ไขสัญญา การทำให้ตัวคั่นเชิงอรรถพอดีอาจสร้างความแตกต่างอย่างมาก  

ในบทแนะนำนี้เราจะอธิบาย **วิธีตั้งค่าระยะห่าง**, ปรับตัวคั่นเชิงอรรถ, และ **ตั้งค่าระยะห่างบรรทัดของย่อหน้า** ด้วยไลบรารีที่ใช้ Java สุดท้ายคุณจะได้ตัวอย่างที่พร้อมรันซึ่งสามารถนำไปใช้ในโปรเจกต์ใดก็ได้

## สิ่งที่คุณต้องมี

- Java 17 หรือใหม่กว่า (โค้ดใช้คุณสมบัติของภาษาที่ทันสมัย)
- Maven หรือ Gradle สำหรับการจัดการ dependencies
- ไฟล์ DOCX ที่มีอย่างน้อยหนึ่งเชิงอรรถ (หรือคุณสามารถสร้างเองได้)
- ไลบรารี **Aspose.Words for Java** (หรือ API ที่เข้ากันได้; เราจะใช้ Aspose ในตัวอย่าง)

เท่านี้—ไม่มีเฟรมเวิร์กหนักๆ เพียงแค่ Java ธรรมดาและไลบรารีเดียว

![Change footnote spacing in DOCX example](/images/footnote-spacing.png){alt="ตัวอย่างการเปลี่ยนระยะห่างของเชิงอรรถใน DOCX"}

## ขั้นตอนที่ 1: โหลดเอกสาร DOCX (เปลี่ยนระยะห่างของเชิงอรรถ)

สิ่งแรกที่คุณต้องทำคือเปิดไฟล์ Word ซึ่งจะให้คุณได้อ็อบเจกต์ `Document` ที่สามารถจัดการได้

```java
import com.aspose.words.*;

public class FootnoteSpacingDemo {
    public static void main(String[] args) throws Exception {
        // Load the DOCX file – change the path to your own file
        Document doc = new Document("input.docx");
        
        // Continue with spacing adjustments...
        adjustFootnoteSeparator(doc);
        
        // Save the updated document
        doc.save("output.docx");
    }
}
```

*ทำไมสิ่งนี้ถึงสำคัญ*: การโหลดเอกสารเป็นจุดเริ่มต้นสำหรับ **การเปลี่ยนระยะห่างของเชิงอรรถ** หากไม่มีอินสแตนซ์ `Document` คุณจะไม่สามารถเข้าถึงตัวคั่นเชิงอรรถหรือรูปแบบของย่อหน้าใดๆ

## ขั้นตอนที่ 2: ดึงและปรับตัวคั่นเชิงอรรถ (ปรับตัวคั่นเชิงอรรถ)

ตัวคั่นเชิงอรรถคือย่อหน้าที่ซ่อนอยู่ระหว่างข้อความหลักและรายการเชิงอรรถ เพื่อเปลี่ยนระยะห่างบรรทัดของมันคุณต้องดึงย่อหน้านั้นและปรับรูปแบบของมัน

```java
private static void adjustFootnoteSeparator(Document doc) throws Exception {
    // Get the footnote separator (the first one is usually the default separator)
    FootnoteSeparator separator = doc.getFootnoteSeparator();
    
    // If the document has no separator (rare), create one
    if (separator == null) {
        separator = new FootnoteSeparator(doc);
        doc.getFootnotes().add(separator);
    }
    
    // Access the underlying paragraph and set line spacing
    Paragraph sepParagraph = separator.getSeparatorParagraph();
    ParagraphFormat fmt = sepParagraph.getParagraphFormat();
    
    // Set line spacing to 12 points – this is the core of "change footnote spacing"
    fmt.setLineSpacing(12.0);
    
    // Optional: also adjust spacing before/after if needed
    fmt.setSpaceBefore(0);
    fmt.setSpaceAfter(0);
}
```

### วิธีที่นี่แก้ปัญหา

- **ดึงตัวคั่นเชิงอรรถ** – นี่คือส่วนที่คุณต้องการแก้ไขจริงๆ ซึ่งสอดคล้องกับความต้องการ *ปรับตัวคั่นเชิงอรรถ*.
- **ตั้งค่าระยะห่างบรรทัด** – `setLineSpacing(12.0)` ตอบโดยตรงว่า *วิธีตั้งค่าระยะห่าง* สำหรับย่อหน้าที่ซ่อนนี้.
- **จัดการกรณีขอบ** – หากเอกสารไม่มีตัวคั่น เราจะสร้างขึ้นทันทีเพื่อป้องกัน `NullPointerException`.

## ขั้นตอนที่ 3: ตรวจสอบการเปลี่ยนแปลงและบันทึก (ตั้งค่าระยะห่างบรรทัดของย่อหน้า)

หลังจากที่คุณปรับตัวคั่นแล้ว คุณต้องการตรวจสอบว่าการเปลี่ยนแปลงนั้นถูกบันทึกไว้จริงหรือไม่ การเปิดไฟล์ที่บันทึกใน Word จะเห็นระยะห่างใหม่ แต่คุณยังสามารถตรวจสอบได้โดยโปรแกรม

```java
private static void verifySpacing(Document doc) throws Exception {
    FootnoteSeparator sep = doc.getFootnoteSeparator();
    double spacing = sep.getSeparatorParagraph().getParagraphFormat().getLineSpacing();
    System.out.println("Current footnote separator line spacing: " + spacing);
}
```

เพิ่มการเรียก `verifySpacing(doc);` ก่อน `doc.save(...)` ในฟังก์ชัน `main` เมื่อคุณรันโปรแกรมควรเห็น:

```
Current footnote separator line spacing: 12.0
```

ซึ่งยืนยันว่าการดำเนินการ **เปลี่ยนระยะห่างบรรทัดใน docx** สำเร็จ

## ข้อผิดพลาดทั่วไป & เคล็ดลับมืออาชีพ

- **ข้อผิดพลาด**: การใช้ `setLineSpacing` กับค่าที่ดูเหมือน “12” แต่ถูกตีความเป็น “12 pts” แทน “12 lines”. Aspose คาดหวังเป็นจุด (points) ดังนั้น 12 หมายถึง 12 pt. สำหรับการทำบรรทัดคู่ให้ใช้ `24.0`.
- **เคล็ดลับ**: หากต้องการลักษณะที่สอดคล้องกันในทุกประเภทของเชิงอรรถ (ตัวคั่น, ตัวคั่นต่อเนื่อง, เป็นต้น) ให้ทำซ้ำขั้นตอนเดียวกันสำหรับ `doc.getFootnoteContinuationSeparator()` และ `doc.getFootnoteContinuationNotice()`.
- **ข้อผิดพลาด**: ลืมเรียก `save()` หลังจากแก้ไข. เอกสารในหน่วยความจำอาจเปลี่ยนแปลง แต่ไฟล์บนดิสก์ยังคงเดิม.
- **เคล็ดลับ**: ผสานการเปลี่ยนแปลงระยะห่างกับการอัปเดตสไตล์ (`ParagraphStyle`) เพื่อให้ส่วนเชิงอรรถดูสมบูรณ์แบบ

## ตัวอย่างทำงานเต็มรูปแบบ (ทุกขั้นตอนในไฟล์เดียว)

```java
import com.aspose.words.*;

public class FootnoteSpacingDemo {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Load the DOCX document
        Document doc = new Document("input.docx");

        // 2️⃣ Adjust the footnote separator – this is where we "change footnote spacing"
        adjustFootnoteSeparator(doc);

        // 3️⃣ Verify the new line spacing (optional but handy for debugging)
        verifySpacing(doc);

        // 4️⃣ Save the result – now your footnotes have the desired spacing
        doc.save("output.docx");
        System.out.println("Footnote spacing updated and saved to output.docx");
    }

    private static void adjustFootnoteSeparator(Document doc) throws Exception {
        FootnoteSeparator separator = doc.getFootnoteSeparator();
        if (separator == null) {
            separator = new FootnoteSeparator(doc);
            doc.getFootnotes().add(separator);
        }
        Paragraph sepParagraph = separator.getSeparatorParagraph();
        ParagraphFormat fmt = sepParagraph.getParagraphFormat();

        // Core operation: "set paragraph line spacing" for the separator
        fmt.setLineSpacing(12.0);   // 12 pt line spacing
        fmt.setSpaceBefore(0);
        fmt.setSpaceAfter(0);
    }

    private static void verifySpacing(Document doc) throws Exception {
        FootnoteSeparator sep = doc.getFootnoteSeparator();
        double spacing = sep.getSeparatorParagraph().getParagraphFormat().getLineSpacing();
        System.out.println("Current footnote separator line spacing: " + spacing);
    }
}
```

คัดลอกโค้ดด้านบนไปยังคลาส Java ใหม่, เพิ่ม dependency ของ Aspose.Words ใน Maven, แล้วรันมัน `output.docx` ของคุณจะมีระยะห่างบรรทัดของตัวคั่นเชิงอรรถตั้งเป็น **12 pt** ซึ่งทำให้ **เปลี่ยนระยะห่างของเชิงอรรถ** อย่างมีประสิทธิภาพ

### Dependency ของ Maven

เพิ่มโค้ดส่วนนี้ลงใน `pom.xml` ของคุณ:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version> <!-- Use the latest stable version -->
</dependency>
```

หากคุณต้องการใช้ Gradle, สิ่งที่เทียบเท่าคือ:

```gradle
implementation 'com.aspose:aspose-words:24.9'
```

## สรุป

คุณเพิ่งเรียนรู้วิธี **เปลี่ยนระยะห่างของเชิงอรรถ** ในไฟล์ DOCX ด้วย Java โดยการโหลดเอกสาร, ดึง **ตัวคั่นเชิงอรรถ**, และใช้ **ตั้งค่าระยะห่างบรรทัดของย่อหน้า**, คุณจะได้การควบคุมที่แม่นยำต่อการแสดงผลของเชิงอรรถ  

จากนี้คุณสามารถสำรวจการปรับแต่งที่เกี่ยวข้อง เช่น การแก้ไขสไตล์ข้อความเชิงอรรถ, การเพิ่มตัวคั่นแบบกำหนดเอง, หรือแม้กระทั่งการทำอัตโนมัติการอัปเดตหลายไฟล์พร้อมกัน  

มีคำถามเพิ่มเติมเกี่ยวกับ **ปรับตัวคั่นเชิงอรรถ** หรืองานอัตโนมัติของ Word อื่นๆ? แสดงความคิดเห็นได้เลย, ขอให้สนุกกับการเขียนโค้ด!

## คุณควรเรียนรู้อะไรต่อไป?

บทแนะนำต่อไปนี้ครอบคลุมหัวข้อที่เกี่ยวข้องอย่างใกล้ชิดซึ่งต่อยอดจากเทคนิคที่แสดงในคู่มือนี้ แต่ละแหล่งข้อมูลมีตัวอย่างโค้ดทำงานเต็มรูปแบบพร้อมคำอธิบายทีละขั้นตอน เพื่อช่วยคุณเชี่ยวชาญฟีเจอร์ API เพิ่มเติมและสำรวจแนวทางการนำไปใช้แบบอื่นในโปรเจกต์ของคุณ

- [เปลี่ยนระยะห่างและการเยื้องของย่อหน้าแบบเอเชียนในเอกสาร Word](/words/english/net/document-formatting/change-asian-paragraph-spacing-and-indents/)
- [เปลี่ยนระยะห่างและการเยื้องของย่อหน้าแบบเอเชียน](/words/german/net/document-formatting/change-asian-paragraph-spacing-and-indents/)
- [เปลี่ยนระยะห่างและการเยื้องของย่อหน้าแบบเอเชียน](/words/french/net/document-formatting/change-asian-paragraph-spacing-and-indents/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}