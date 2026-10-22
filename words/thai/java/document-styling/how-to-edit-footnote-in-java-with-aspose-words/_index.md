---
category: general
date: 2026-08-07
description: วิธีแก้ไขเชิงอรรถใน Java ด้วย Aspose.Words – เพิ่มขีดแบบกำหนดเอง, เปลี่ยนเส้นเชิงอรรถ,
  และตั้งค่าการจัดแนวย่อหน้าเพื่อเอกสารที่ดูเรียบหรู.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to edit footnote
- add custom dash
- change footnote line
- change footnote separator
- set paragraph alignment
language: th
lastmod: 2026-08-07
og_description: วิธีแก้ไขเชิงอรรถใน Java ด้วย Aspose.Words เรียนรู้การเพิ่มขีดกำหนดเอง
  เปลี่ยนเส้นเชิงอรรถ และตั้งค่าการจัดแนวย่อหน้าในไม่กี่ขั้นตอน
og_image_alt: Java code editing footnote separator with a custom dash and centered
  alignment
og_title: วิธีแก้ไขเชิงอรรถใน Java – เพิ่มขีด, เปลี่ยนบรรทัด, ตั้งค่าการจัดแนว
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: How to edit footnote in Java with Aspose.Words – add custom dash, change
    footnote line, and set paragraph alignment for polished documents.
  headline: How to edit footnote in Java with Aspose.Words
  type: TechArticle
- description: How to edit footnote in Java with Aspose.Words – add custom dash, change
    footnote line, and set paragraph alignment for polished documents.
  name: How to edit footnote in Java with Aspose.Words
  steps:
  - name: '**Loading the document** – `new Document(...)` reads the DOCX file into
      memory, giving you access to all its nodes.'
    text: '**Loading the document** – `new Document(...)` reads the DOCX file into
      memory, giving you access to all its nodes.'
  - name: '**Fetching the separator** – `getFootnoteSeparator()` returns the special
      paragraph that Aspose.Words treats as the footnote line. This object is the
      only place you can safely modify the separator.'
    text: '**Fetching the separator** – `getFootnoteSeparator()` returns the special
      paragraph that Aspose.Words treats as the footnote line. This object is the
      only place you can safely modify the separator.'
  - name: '**Setting paragraph alignment** – `setAlignment(ParagraphAlignment.CENTER)`
      changes the line’s alignment. The keyword *set paragraph alignment* is applied
      directly to the separator, ensuring a centered dash.'
    text: '**Setting paragraph alignment** – `setAlignment(ParagraphAlignment.CENTER)`
      changes the line’s alignment. The keyword *set paragraph alignment* is applied
      directly to the separator, ensuring a centered dash.'
  - name: '**Adding a custom dash** – By clearing existing runs and adding a new `Run`
      with the em‑dash character (`—`), you achieve the *add custom dash* effect while
      also *change footnote line* to your desired style.'
    text: '**Adding a custom dash** – By clearing existing runs and adding a new `Run`
      with the em‑dash character (`—`), you achieve the *add custom dash* effect while
      also *change footnote line* to your desired style.'
  - name: '**Saving the document** – `doc.save(...)` writes the changes back to disk,
      producing an output file that reflects all modifications.'
    text: '**Saving the document** – `doc.save(...)` writes the changes back to disk,
      producing an output file that reflects all modifications.'
  type: HowTo
tags:
- Aspose.Words
- Java
- Footnotes
title: วิธีแก้ไขเชิงอรรถใน Java ด้วย Aspose.Words
url: /th/java/document-styling/how-to-edit-footnote-in-java-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# วิธีแก้ไขเชิงอรรถใน Java ด้วย Aspose.Words

หากคุณต้องการ **วิธีแก้ไขเชิงอรรถ** ในเอกสาร Word ด้วย Java คู่มือนี้จะแสดงขั้นตอนการทำงานทั้งหมด คุณจะได้เรียนรู้การเพิ่มขีดแบบกำหนดเอง, การเปลี่ยนเส้นเชิงอรรถ, และการตั้งค่าการจัดแนวย่อหน้าเพื่อให้เส้นแบ่งเชิงอรรถดูเป็นมืออาชีพ

การแก้ไขเชิงอรรถเป็นความต้องการทั่วไปเมื่อเตรียมสัญญากฎหมาย, งานวิจัยทางวิชาการ, หรือโบรชัวร์การตลาด ขั้นตอนด้านล่างครอบคลุมทุกอย่างที่คุณต้องการ—from การโหลดเอกสารจนถึงการบันทึกไฟล์สุดท้าย—โดยไม่ต้องใช้เครื่องมือเพิ่มเติม

## ข้อกำหนดเบื้องต้น

ก่อนเริ่มทำงาน โปรดตรวจสอบว่าคุณมี:

* Java 17 หรือใหม่กว่า
* Aspose.Words for Java (เวอร์ชันล่าสุด) ที่เพิ่มเข้าไปใน classpath ของโปรเจกต์
* ไฟล์ DOCX (`input.docx`) ที่มีเชิงอรรถอย่างน้อยหนึ่งรายการ

สิ่งเหล่านี้รับประกันว่าโค้ดจะทำงานโดยไม่มีข้อผิดพลาดในระหว่างรัน

## วิธีแก้ไขเส้นแบ่งและบรรทัดเชิงอรรถ

เส้นแบ่งเชิงอรรถคือย่อหน้าที่ปรากฏระหว่างข้อความหลักและรายการเชิงอรรถ การเปลี่ยนแปลงลักษณะของมันช่วยเพิ่มความอ่านง่ายและสอดคล้องกับแบรนด์ขององค์กร

```java
import com.aspose.words.*;

public class FootnoteSeparatorDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Load the document containing footnotes
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // Step 2: Get the footnote separator paragraph (the line before the footnote list)
        Paragraph separator = doc.getFootnoteSeparator();

        // Step 3: Center‑align the separator for better appearance
        separator.getParagraphFormat().setAlignment(ParagraphAlignment.CENTER);

        // Step 4: Replace the default separator line with a custom dash
        separator.getRuns().clear();                 // Remove existing runs
        separator.getRuns().add(new Run(doc, "—"));   // Add a custom dash character

        // Step 5: Save the modified document
        doc.save("YOUR_DIRECTORY/output.docx");
    }
}
```

### ทำไมแต่ละบรรทัดจึงสำคัญ

1. **การโหลดเอกสาร** – `new Document(...)` อ่านไฟล์ DOCX เข้าไปในหน่วยความจำ ทำให้คุณเข้าถึงโหนดทั้งหมดได้
2. **การดึงเส้นแบ่ง** – `getFootnoteSeparator()` คืนค่าย่อหน้าพิเศษที่ Aspose.Words ถือเป็นบรรทัดเชิงอรรถ วัตถุนี้เป็นที่เดียวที่คุณสามารถแก้ไขเส้นแบ่งได้อย่างปลอดภัย
3. **การตั้งค่าการจัดแนวย่อหน้า** – `setAlignment(ParagraphAlignment.CENTER)` เปลี่ยนการจัดแนวของบรรทัด คำหลัก *set paragraph alignment* จะถูกนำไปใช้โดยตรงกับเส้นแบ่ง เพื่อให้ได้ขีดที่อยู่กึ่งกลาง
4. **การเพิ่มขีดแบบกำหนดเอง** – โดยการลบ `Run` ที่มีอยู่และเพิ่ม `Run` ใหม่ที่มีอักขระ em‑dash (`—`) คุณจะได้ผลลัพธ์ *add custom dash* พร้อมกับ *change footnote line* ตามสไตล์ที่ต้องการ
5. **การบันทึกเอกสาร** – `doc.save(...)` เขียนการเปลี่ยนแปลงกลับไปยังดิสก์ สร้างไฟล์ผลลัพธ์ที่สะท้อนการแก้ไขทั้งหมด

## เพิ่มขีดแบบกำหนดเองให้กับเส้นแบ่งเชิงอรรถ

โค้ดใน **ขั้นตอน 4** แสดงเทคนิค *add custom dash* คุณสามารถเปลี่ยนอักขระ em‑dash เป็นสตริงใดก็ได้ เช่น `"***"` หรือ `"---"` เพื่อให้สอดคล้องกับภาษาภาพของเอกสาร

```java
separator.getRuns().clear();                     // Remove default line
separator.getRuns().add(new Run(doc, "***"));    // Insert three asterisks as a custom dash
```

การใช้ขีดแบบกำหนดเองเป็นประโยชน์เป็นพิเศษเมื่อเส้นบางแบบเริ่มต้นไม่ตรงกับแนวทางแบรนด์

## เปลี่ยนสไตล์บรรทัดเชิงอรรถ

หากคุณต้องการเส้นทึบแทนขีด สามารถใส่อักขระ Unicode แบบ box‑drawing หรืออักขระ underscore ที่ซ้ำกันได้

```java
separator.getRuns().clear();
separator.getRuns().add(new Run(doc, "_____")); // Five underscores create a solid line
```

ขั้นตอน *change footnote line* ทำงานเช่นเดียวกันไม่ว่าคุณจะเลือกอักขระใด เพราะย่อหน้าเส้นแบ่งเพียงแค่แสดงข้อความที่บรรจุไว้

## ตั้งค่าการจัดแนวย่อหน้าสำหรับเส้นแบ่งเชิงอรรถ

การดำเนินการ *set paragraph alignment* ไม่ได้จำกัดแค่การจัดกึ่งกลาง คุณสามารถจัดแนวซ้าย, ขวา, หรือจัดเต็มตามความต้องการของเลย์เอาต์

```java
separator.getParagraphFormat().setAlignment(ParagraphAlignment.RIGHT); // Right‑align
```

การจัดแนวเส้นแบ่งไปทางขวาอาจมีประโยชน์สำหรับเอกสารที่ใช้เชิงอรรถจัดแนวขวา เช่น สิ่งพิมพ์สองภาษา

## ตัวอย่างเต็มที่สามารถรันได้

ด้านล่างเป็นโปรแกรมทั้งหมดที่รวมแนวคิดทั้งหมด—การโหลดเอกสาร, การแก้ไขเส้นแบ่งเชิงอรรถ, การเพิ่มขีดแบบกำหนดเอง, การเปลี่ยนสไตล์บรรทัด, และการตั้งค่าการจัดแนว

```java
import com.aspose.words.*;

public class FootnoteSeparatorDemo {
    public static void main(String[] args) throws Exception {
        // Load the source document
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // Retrieve the footnote separator paragraph
        Paragraph separator = doc.getFootnoteSeparator();

        // Set the desired alignment (center, left, right, or justify)
        separator.getParagraphFormat().setAlignment(ParagraphAlignment.CENTER);

        // Clear any existing content in the separator
        separator.getRuns().clear();

        // Add a custom dash – replace with any string to change footnote line
        separator.getRuns().add(new Run(doc, "—")); // Em‑dash as the custom dash

        // Save the updated document
        doc.save("YOUR_DIRECTORY/output.docx");
    }
}
```

**ผลลัพธ์ที่คาดหวัง:** ไฟล์ `output.docx` จะมี em‑dash กึ่งกลางแทนเส้นบางเดิม เชิงอรรถทั้งหมดยังคงอยู่ครบถ้วน และเลย์เอาต์ของเอกสารจะแสดงสไตล์เส้นแบ่งใหม่

## ข้อผิดพลาดทั่วไปและวิธีหลีกเลี่ยง

| Issue | Reason | Fix |
|-------|--------|-----|
| Separator not found | Document has no footnotes or uses a custom footnote style | Ensure the source DOCX contains at least one footnote before calling `getFootnoteSeparator()` |
| Custom dash not visible | Font does not support the chosen character | Use a Unicode character that is supported by the document’s default font, or embed a compatible font |
| Alignment appears unchanged | Paragraph format is overridden later in the code | Apply alignment **after** any other formatting calls that might reset it |

การแก้ไขปัญหาเหล่านี้จะช่วยป้องกันข้อผิดพลาดระหว่างรันและทำให้กระบวนการ *how to edit footnote* ทำงานอย่างมั่นคง

## ขั้นตอนต่อไป

ตอนนี้คุณรู้ **วิธีแก้ไขเชิงอรรถ** แล้ว สามารถสำรวจงานที่เกี่ยวข้องต่อไปได้:

* **เพิ่มสไตล์อ้างอิงเชิงอรรถแบบกำหนดเอง** – แก้ไขโหนด `FootnoteReference` เพื่อเปลี่ยนหมายเลขหรือสัญลักษณ์
* **แทรกเชิงอรรถใหม่โดยโปรแกรม** – ใช้ `DocumentBuilder.insertFootnote()` สำหรับเนื้อหาแบบไดนามิก
* **ใช้การจัดรูปแบบตามเงื่อนไข** – เปลี่ยนลักษณะเชิงอรรถตามสไตล์ย่อหน้าหรือความยาวของเนื้อหา

แต่ละส่วนขยายเหล่านี้สร้างบน API เดียวกันที่คุณใช้เพื่อ *add custom dash*, *change footnote line*, และ *set paragraph alignment*

---

*Happy coding! หากบทแนะนำนี้ช่วยให้คุณเชี่ยวชาญการแก้ไขเชิงอรรถ อย่าลืมแชร์ให้ทีมของคุณหรือส่ง pull request เพื่อปรับปรุงตัวอย่างต่อไป*

## คุณควรเรียนรู้อะไรต่อไป?

บทแนะนำต่อไปนี้ครอบคลุมหัวข้อที่เกี่ยวข้องอย่างใกล้ชิดและต่อยอดจากเทคนิคที่แสดงในคู่มือนี้ แต่ละแหล่งข้อมูลมีตัวอย่างโค้ดทำงานเต็มรูปแบบพร้อมคำอธิบายทีละขั้นตอน เพื่อช่วยคุณเชี่ยวชาญฟีเจอร์ API เพิ่มเติมและสำรวจแนวทางการทำงานอื่น ๆ ในโปรเจกต์ของคุณ

- [Set Footnote And End Note Position](/words/hindi/net/working-with-footnote-and-endnote/set-footnote-and-end-note-position/)
- [How to create form fields and add content using DocumentBuilder in Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [How to Set LoadOptions in Aspose.Words for Java](/words/english/java/document-loading-and-saving/using-load-options/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}