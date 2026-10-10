---
category: general
date: 2026-10-10
description: ใช้เชิงอรรถสไตล์หัวเรื่องในเอกสาร Word ด้วย Aspose.Words for Java – คู่มือเต็มขั้นตอน.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- apply heading style footnotes
- footnote separator
- endnote separator
- Aspose.Words for Java
- style identifier
language: th
lastmod: 2026-10-10
og_description: ใช้เชิงอรรถสไตล์หัวเรื่องในเอกสาร Word ด้วย Aspose.Words for Java.
  เรียนรู้วิธีจัดรูปแบบตัวคั่นเชิงอรรถและบันทึกท้ายในเวลาไม่กี่นาที.
og_image_alt: Document after applying heading style footnotes to footnote and endnote
  separators
og_title: ใช้เชิงอรรถสไตล์หัวข้อกับ Aspose.Words for Java – คู่มือฉบับเต็ม
schemas:
- author: Aspose
  dateModified: '2026-10-10'
  description: Apply heading style footnotes in a Word document using Aspose.Words
    for Java – a complete step‑by‑step guide.
  headline: Apply heading style footnotes with Aspose.Words for Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word processing
- Document styling
title: ใช้เชิงอรรถแบบหัวเรื่องกับ Aspose.Words สำหรับ Java
url: /th/java/annotations-comments/apply-heading-style-footnotes-with-aspose-words-for-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# ใช้สไตล์หัวเรื่องในเชิงอรรถด้วย Aspose.Words for Java

หากคุณต้องการ **ใช้สไตล์หัวเรื่องในเชิงอรรถ** ในเอกสาร Word, บทแนะนำนี้จะแสดงวิธีทำอย่างละเอียดด้วย Aspose.Words for Java คุณจะได้เห็นตัวอย่างที่ทำงานได้เต็มรูปแบบซึ่งกำหนดสไตล์ให้กับตัวคั่นเชิงอรรถและตัวคั่นอันทโน้ตโดยใช้สไตล์หัวเรื่องที่มีมาให้

การกำหนดสไตล์ให้กับตัวคั่นเชิงอรรถและอันทโน้ตทำให้เอกสารอ่านง่ายขึ้นและให้การจัดรูปแบบที่สม่ำเสมอในงานเขียนขนาดใหญ่ คู่มือนี้ยังครอบคลุมข้อผิดพลาดทั่วไป เช่น การตรวจสอบให้ใช้ `StyleIdentifier` ที่ถูกต้องและการจัดการกับเอกสารที่มีตัวคั่นแบบกำหนดเองอยู่แล้ว

## สิ่งที่คุณจะได้เรียนรู้

* วิธีโหลดไฟล์ `.docx` ที่มีเชิงอรรถและอันทโน้ต  
* วิธีดึงพารากราฟ **ตัวคั่นเชิงอรรถ** และกำหนดสไตล์เป็น `HEADING_2`  
* วิธีดึงพารากราฟ **ตัวคั่นอันทโน้ต** และกำหนดสไตล์เป็น `HEADING_3`  
* วิธีบันทึกเอกสารที่แก้ไขแล้วและตรวจสอบการเปลี่ยนแปลง  

**ข้อกำหนดเบื้องต้น**

* Java 17 หรือใหม่กว่า  
* Aspose.Words for Java 23.12 (หรือเวอร์ชันล่าสุด)  
* ความคุ้นเคยพื้นฐานกับแนวคิดการประมวลผล Word (เชิงอรรถ, อันทโน้ต, สไตล์)

---

## ภาพรวมการใช้สไตล์หัวเรื่องในเชิงอรรถ

แนวคิดหลักคือการใช้เมธอด `Document.getFootnoteSeparator()` และ `Document.getEndnoteSeparator()` ของ Aspose.Words ทั้งสองเมธอดจะคืนค่าออบเจ็กต์ `Paragraph` ที่เป็นตัวคั่นซ่อนระหว่างข้อความหลักกับพื้นที่เชิงอรรถ/อันทโน้ต โดยการเปลี่ยน `ParagraphFormat` ของพารากราฟและกำหนด `StyleIdentifier` คุณจึงสามารถ **ใช้สไตล์หัวเรื่องในเชิงอรรถ** ได้โดยไม่ต้องแก้ไข UI ของ Word ด้วยตนเอง

---

## ขั้นตอนที่ 1: ตั้งค่าโปรเจกต์

สร้างโปรเจกต์ Maven (หรือ Gradle) แล้วเพิ่ม dependency ของ Aspose.Words for Java:

```xml
<!-- pom.xml -->
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.12</version>
</dependency>
```

> **เคล็ดลับ:** ใช้เวอร์ชันล่าสุดเพื่อรับประโยชน์จากการแก้บั๊กที่เกี่ยวกับ enumeration `StyleIdentifier`

---

## ขั้นตอนที่ 2: โหลดเอกสารต้นฉบับ

```java
import com.aspose.words.*;

public class ApplyHeadingStyleFootnotes {
    public static void main(String[] args) throws Exception {
        // Load a Word document that already contains footnotes and endnotes.
        Document document = new Document("YOUR_DIRECTORY/Footnotes.docx");
        // From here we will manipulate the footnote and endnote separators.
```

*คอนสตรัคเตอร์ `Document` จะอ่านไฟล์เข้าหน่วยความจำ ทำให้คุณสามารถเข้าถึงได้โดยโปรแกรมเต็มรูปแบบ*  

---

## ขั้นตอนที่ 3: กำหนดสไตล์ให้กับตัวคั่นเชิงอรรถ

```java
        // Retrieve the hidden paragraph that separates footnotes from the main text.
        Paragraph footnoteSeparator = document.getFootnoteSeparator();

        // Apply the built‑in Heading 2 style to this separator.
        footnoteSeparator.getParagraphFormat()
                         .setStyleIdentifier(StyleIdentifier.HEADING_2);
```

ทำไมต้องใช้ `HEADING_2`? สไตล์หัวเรื่องสืบทอดขนาดฟอนต์, สีและระยะห่าง ซึ่งทำให้ตัวคั่นดูโดดเด่นในเชิงภาพขณะยังคงสอดคล้องกับลำดับชั้นสไตล์ของเอกสาร

---

## ขั้นตอนที่ 4: กำหนดสไตล์ให้กับตัวคั่นอันทโน้ต

```java
        // Retrieve the hidden paragraph that separates endnotes.
        Paragraph endnoteSeparator = document.getEndnoteSeparator();

        // Apply the built‑in Heading 3 style to this separator.
        endnoteSeparator.getParagraphFormat()
                        .setStyleIdentifier(StyleIdentifier.HEADING_3);
```

การใช้ `HEADING_3` ทำให้ความหนาของสไตล์ต่ำกว่าตัวคั่นเชิงอรรถ ซึ่งสอดคล้องกับแนวปฏิบัติการจัดรูปแบบเชิงวิชาการทั่วไป

---

## ขั้นตอนที่ 5: บันทึกเอกสารที่แก้ไขแล้ว

```java
        // Persist the changes to a new file.
        document.save("YOUR_DIRECTORY/FootnoteStyled.docx");
        System.out.println("Document saved with styled footnote and endnote separators.");
    }
}
```

หลังจากรันโปรแกรมแล้ว ให้เปิดไฟล์ `FootnoteStyled.docx` ใน Microsoft Word คุณจะสังเกตว่า:

* ตัวคั่นเชิงอรรถแสดงด้วยรูปแบบของ **Heading 2** (ฟอนต์ใหญ่กว่า, ตัวหนาตามค่าเริ่มต้น)  
* ตัวคั่นอันทโน้ตแสดงด้วย **Heading 3** (ขนาดเล็กลงเล็กน้อย, ยังเป็นตัวหนา)  

การเปลี่ยนแปลงเหล่านี้จะถูกนำไปใช้โดยอัตโนมัติกับทุกเชิงอรรถและอันทโน้ตในเอกสาร แม้จะมีการเพิ่มรายการใหม่ในภายหลังก็ตาม

---

## คำถามทั่วไปและกรณีขอบ

| คำถาม | คำตอบ |
|----------|--------|
| **ถ้าเอกสารมีสไตล์กำหนดเองสำหรับตัวคั่นแล้วจะทำอย่างไร?** | การเขียนทับ `StyleIdentifier` จะแทนที่สไตล์เดิม หากต้องการคงรูปแบบที่กำหนดเองไว้ ให้ทำการโคลนสไตล์เดิม, ปรับแก้ แล้วกำหนดตัวระบุของคลอนนั้นให้กับพารากราฟ |
| **ฉันสามารถใช้สไตล์กำหนดเองแทนหัวเรื่องที่มีมาให้ได้หรือไม่?** | ใช่. สร้างสไตล์กำหนดเองด้วย `document.getStyles().add(StyleIdentifier.CUSTOM)`, ตั้งค่าคุณลักษณะต่าง ๆ แล้วกำหนดตัวระบุของสไตล์นั้นให้กับพารากราฟตัวคั่น |
| **โค้ดนี้ทำงานกับไฟล์ `.doc` (แบบไบนารี) ได้หรือไม่?** | ทำได้แน่นอน. Aspose.Words จัดการรูปแบบไฟล์ให้เป็นนามธรรม ดังนั้นโค้ดเดียวกันทำงานได้กับไฟล์ `.doc` และ `.docx` |
| **มีผลต่อประสิทธิภาพเมื่อทำงานกับเอกสารขนาดใหญ่หรือไม่?** | ผลกระทบต่ำมาก เนื่องจากการดำเนินการเป็น O(1) เพียงเป้าหมายที่พารากราฟซ่อนหนึ่งเดียว แม้เอกสาร 500 หน้า ก็ประมวลผลได้ในระดับมิลลิวินาที |

---

## โค้ดเต็ม (สามารถรันได้)

```java
import com.aspose.words.*;

public class ApplyHeadingStyleFootnotes {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Load the source document containing footnotes and endnotes.
        Document document = new Document("YOUR_DIRECTORY/Footnotes.docx");

        // 2️⃣ Retrieve the footnote separator and apply Heading 2.
        Paragraph footnoteSeparator = document.getFootnoteSeparator();
        footnoteSeparator.getParagraphFormat()
                         .setStyleIdentifier(StyleIdentifier.HEADING_2);

        // 3️⃣ Retrieve the endnote separator and apply Heading 3.
        Paragraph endnoteSeparator = document.getEndnoteSeparator();
        endnoteSeparator.getParagraphFormat()
                        .setStyleIdentifier(StyleIdentifier.HEADING_3);

        // 4️⃣ Save the modified document.
        document.save("YOUR_DIRECTORY/FootnoteStyled.docx");
        System.out.println("Document saved with styled footnote and endnote separators.");
    }
}
```

**ผลลัพธ์ที่คาดหวัง** (คอนโซล):

```
Document saved with styled footnote and endnote separators.
```

เปิดไฟล์ที่บันทึกไว้เพื่อดูตัวคั่นที่ได้รับการกำหนดสไตล์

---

## สรุป

คุณได้เรียนรู้วิธี **ใช้สไตล์หัวเรื่องในเชิงอรรถ** ในเอกสาร Word ด้วย Aspose.Words for Java โดยการดึงพารากราฟ **ตัวคั่นเชิงอรรถ** และ **ตัวคั่นอันทโน้ต** แล้วกำหนดค่า `StyleIdentifier` ที่เหมาะสม ทำให้ได้รูปแบบที่สม่ำเสมอและเป็นมืออาชีพด้วยเพียงไม่กี่บรรทัดโค้ด

ขั้นตอนต่อไปที่คุณอาจพิจารณา:

* ทดลองใช้สไตล์กำหนดเองแทนหัวเรื่องที่มีมาให้  
* ทำอัตโนมัติการเปลี่ยนสไตล์ในชุดเอกสารหลายไฟล์โดยใช้แนวทางเดียวกันนี้  
* ผสานเทคนิคนี้กับ API ของ `Document` อื่น ๆ เช่น `getFootnoteOptions()` เพื่อปรับแต่งการจัดลำดับเลขเชิงอรรถให้ละเอียดขึ้น  

ปรับใช้โค้ดตามความต้องการของกระบวนการเผยแพร่ของคุณและขอให้เขียนโค้ดอย่างสนุกสนาน!

## คุณควรเรียนรู้อะไรต่อไป?

บทแนะนำต่อไปนี้ครอบคลุมหัวข้อที่เกี่ยวข้องอย่างใกล้ชิดและต่อยอดจากเทคนิคที่แสดงในคู่มือนี้ แต่ละแหล่งข้อมูลมีตัวอย่างโค้ดทำงานครบถ้วนพร้อมคำอธิบายขั้นตอนเพื่อช่วยให้คุณเชี่ยวชาญฟีเจอร์ API เพิ่มเติมและสำรวจวิธีการทำงานแบบอื่นในโครงการของคุณ

- [การใช้เชิงอรรถและอันทโน้ตใน Aspose.Words for Java](/words/english/java/using-document-elements/using-footnotes-and-endnotes/)
- [บันทึก Word เป็น PDF ด้วย Aspose.Words – คู่มือ Java ขั้นตอนโดยขั้นตอน](/words/english/java/document-conversion-and-export/save-word-as-pdf-with-aspose-words-step-by-step-java-guide/)
- [ส่งออก Word เป็น Markdown – คู่มือ Java ด้วย Aspose.Words](/words/english/java/document-conversion-and-export/export-word-to-markdown-java-guide-using-aspose-words/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}