---
category: general
date: 2026-10-04
description: แก้ไขตัวคั่นเชิงอรรถใน Java ด้วย Aspose.Words – เรียนรู้วิธีเปลี่ยนตัวคั่นเชิงอรรถและเพิ่มคำตัวคั่นแบบกำหนดเองในเอกสาร
  Word
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- edit footnote separator
- change footnote separator
- custom separator word
language: th
lastmod: 2026-10-04
og_description: แก้ไขตัวคั่นเชิงอรรถใน Java ด้วย Aspose.Words บทเรียนนี้แสดงวิธีเปลี่ยนตัวคั่นเชิงอรรถและแทรกคำตัวคั่นที่กำหนดเอง
og_image_alt: Screenshot of a Java IDE showing code that edits a footnote separator
  in a Word document
og_title: แก้ไขตัวคั่นเชิงอรรถใน Java – คู่มือ Aspose.Words ฉบับสมบูรณ์
schemas:
- author: Aspose
  dateModified: '2026-10-04'
  description: Edit footnote separator in Java using Aspose.Words – learn how to change
    footnote separator and add a custom separator word to Word documents.
  headline: How to edit footnote separator in Java with Aspose.Words
  type: TechArticle
- description: Edit footnote separator in Java using Aspose.Words – learn how to change
    footnote separator and add a custom separator word to Word documents.
  name: How to edit footnote separator in Java with Aspose.Words
  steps:
  - name: '**`clearChildren()`** removes any existing runs, ensuring the separator
      contains only the text you provide.'
    text: '**`clearChildren()`** removes any existing runs, ensuring the separator
      contains only the text you provide.'
  - name: '**`new Run(document, "—")`** creates a text node with the desired separator.
      The `Run` object respects the document’s style, so the separator inherits the
      formatting of the original footnote separator.'
    text: '**`new Run(document, "—")`** creates a text node with the desired separator.
      The `Run` object respects the document’s style, so the separator inherits the
      formatting of the original footnote separator.'
  - name: '**`appendChild(customRun)`** inserts the new run into the separator paragraph.'
    text: '**`appendChild(customRun)`** inserts the new run into the separator paragraph.'
  type: HowTo
tags:
- Aspose.Words
- Java
- Footnotes
- Word processing
title: วิธีแก้ไขตัวคั่นเชิงอรรถใน Java ด้วย Aspose.Words
url: /th/java/document-styling/how-to-edit-footnote-separator-in-java-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# วิธีแก้ไขตัวคั่นเชิงอรรถใน Java ด้วย Aspose.Words

หากคุณต้องการ **แก้ไขตัวคั่นเชิงอรรถ** ในเอกสาร Word คำแนะนำนี้จะแสดงให้คุณเห็นอย่างชัดเจนว่าจะทำอย่างไรใน Java ไม่ว่าคุณต้องการ **เปลี่ยนตัวคั่นเชิงอรรถ** เป็นเครื่องหมายขีด, ดาว, หรือ **คำตัวคั่นที่กำหนดเอง** ขั้นตอนต่อไปนี้ครอบคลุมทุกอย่างที่คุณต้องการ

คุณจะได้เรียนรู้วิธีโหลดไฟล์ `.docx` ดึงส่วนตัวคั่นพิเศษออกมา แก้ไขเนื้อหา และบันทึกผลลัพธ์ ไม่ต้องใช้สคริปต์ภายนอกหรือการแก้ไขด้วยมือ – ทุกอย่างทำโดยโปรแกรมด้วยไลบรารี Aspose.Words for Java

## ข้อกำหนดเบื้องต้น

- Java 17 หรือใหม่กว่า ติดตั้งแล้ว
- Maven หรือ Gradle เพื่อจัดการ dependencies (ตัวอย่างใช้ Maven)
- ใบอนุญาต Aspose.Words for Java ที่ถูกต้อง (หรือคีย์ทดลองใช้ฟรี)
- เอกสาร Word ที่มีเชิงอรรถอยู่แล้ว (ตัวคั่นจะมีเฉพาะเมื่อมีเชิงอรรถอยู่)

## เพิ่ม Aspose.Words ไปยังโปรเจคของคุณ

หากคุณใช้ Maven ให้เพิ่ม dependency ต่อไปนี้ในไฟล์ `pom.xml` ของคุณ:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.11</version> <!-- Use the latest version -->
</dependency>
```

สำหรับ Gradle ให้เพิ่ม:

```gradle
implementation 'com.aspose:aspose-words:24.11'
```

## ขั้นตอน 1: โหลดเอกสารที่มีเชิงอรรถ

ขั้นตอนแรกคือการเปิดไฟล์ Word ที่คุณต้องการแก้ไข Aspose.Words จะอ่านไฟล์เข้าสู่วัตถุ `Document` ซึ่งให้คุณเข้าถึงทุกส่วนของเอกสารรวมถึงตัวคั่นเชิงอรรถ

```java
import com.aspose.words.*;

public class EditFootnoteSeparator {
    public static void main(String[] args) throws Exception {
        // Path to the source document
        String inputPath = "YOUR_DIRECTORY/docWithNotes.docx";

        // Load the document
        Document document = new Document(inputPath);
        
        // Continue with separator editing...
    }
}
```

**ทำไมเรื่องนี้ถึงสำคัญ:** การโหลดเอกสารจะสร้างการแสดงผลในหน่วยความจำ ทำให้คุณสามารถแก้ไขโหนดใด ๆ ได้อย่างปลอดภัยโดยไม่กระทบไฟล์ต้นฉบับจนกว่าคุณจะบันทึกอย่างชัดเจน

## ขั้นตอน 2: ดึงส่วนตัวคั่นเชิงอรรถ

Word เก็บตัวคั่นเชิงอรรถเป็นโหนด `Separator` พิเศษ Aspose.Words มีเมธอด `getFootnoteSeparator()` เพื่อดึงออกโดยตรง

```java
// Get the footnote separator (the line that appears between footnotes and the main text)
Separator footnoteSeparator = document.getFootnoteSeparator();

if (footnoteSeparator == null) {
    System.out.println("The document does not contain a footnote separator.");
    return;
}
```

**เคล็ดลับ:** โหนดตัวคั่นจะมีเฉพาะเมื่อเอกสารมีเชิงอรรถอย่างน้อยหนึ่งรายการ หากคุณพยายามแก้ไขเอกสารที่ไม่มีเชิงอรรถ `getFootnoteSeparator()` จะคืนค่า `null` ดังนั้นควรตรวจสอบเงื่อนไขนี้เสมอ

## ขั้นตอน 3: แทรกคำตัวคั่นที่กำหนดเอง

ตอนนี้คุณสามารถเปลี่ยนลักษณะของตัวคั่นได้ ในตัวอย่างนี้เราจะแทนบรรทัดเริ่มต้นด้วยเครื่องหมาย em dash (`—`). คุณสามารถแทรก **คำตัวคั่นที่กำหนดเอง** ใด ๆ เช่น `"NOTE:"` หรือ `"***"`

```java
// Access the first paragraph of the separator (there is usually only one)
Paragraph separatorParagraph = footnoteSeparator.getParagraphs().get(0);

// Clear any existing runs (text fragments) to avoid mixing old and new content
separatorParagraph.clearChildren();

// Append a new Run that contains the custom separator word
Run customRun = new Run(document, "—");   // Replace "—" with any text you need
separatorParagraph.appendChild(customRun);
```

### สิ่งที่โค้ดทำ

1. **`clearChildren()`** ลบ Run ที่มีอยู่ทั้งหมด เพื่อให้ตัวคั่นมีเพียงข้อความที่คุณกำหนด
2. **`new Run(document, "—")`** สร้างโหนดข้อความที่เป็นตัวคั่นตามที่ต้องการ วัตถุ `Run` จะสืบทอดสไตล์ของเอกสาร ดังนั้นตัวคั่นจะรับการจัดรูปแบบจากตัวคั่นเชิงอรรถเดิม
3. **`appendChild(customRun)`** แทรก Run ใหม่เข้าไปในย่อหน้าตัวคั่น

คุณยังสามารถกำหนดรูปแบบให้กับ Run ได้ ตัวอย่างเช่น:

```java
customRun.getFont().setBold(true);
customRun.getFont().setSize(10);
customRun.getFont().setColor(Color.BLUE);
```

## ขั้นตอน 4: บันทึกเอกสารที่แก้ไขแล้ว

หลังจากแก้ไขตัวคั่นแล้ว ให้เขียนเอกสารกลับไปยังดิสก์ เลือกชื่อไฟล์ใหม่เพื่อไม่ให้ไฟล์ต้นฉบับถูกแก้ไข

```java
// Path to the output document
String outputPath = "YOUR_DIRECTORY/ModifiedNotes.docx";

// Save the changes
document.save(outputPath);

System.out.println("Footnote separator edited successfully. Saved to " + outputPath);
```

**การตรวจสอบผลลัพธ์:** เปิดไฟล์ `ModifiedNotes.docx` ด้วย Microsoft Word ตัวคั่นเชิงอรรถควรแสดงเครื่องหมายขีดที่กำหนดเอง (หรือคำใดก็ตามที่คุณเลือก) แทนบรรทัดเริ่มต้น

## การจัดการตัวคั่นเชิงอรรถหลายประเภท

Word รองรับตัวคั่นพิเศษสามประเภท:

| ประเภทตัวคั่น | เมธอด |
|----------------|----------------------------|
| ตัวคั่นเชิงอรรถ | `getFootnoteSeparator()` |
| ตัวคั่นต่อเนื่องของเชิงอรรถ | `getFootnoteContinuationSeparator()` |
| ตัวคั่นเชิงอรรถสำหรับหน้าหนึ่ง | `getFootnoteSeparatorForFirstPage()` |

หากคุณต้องการแก้ไขทั้งหมด ให้ทำซ้ำ **ขั้นตอน 2** และ **ขั้นตอน 3** สำหรับแต่ละเมธอด ตัวอย่าง:

```java
Separator continuation = document.getFootnoteContinuationSeparator();
if (continuation != null) {
    // Apply the same custom run or a different one
    Paragraph p = continuation.getParagraphs().get(0);
    p.clearChildren();
    p.appendChild(new Run(document, "*"));
}
```

## ข้อผิดพลาดทั่วไปและวิธีหลีกเลี่ยง

| ปัญหา | สาเหตุ | วิธีแก้ |
|-------|-------|-----|
| ไม่มีตัวคั่นปรากฏหลังการบันทึก | เอกสารไม่มีเชิงอรรถ → โหนดตัวคั่นเป็น `null` | เพิ่มเชิงอรรถอย่างน้อยหนึ่งรายการก่อนแก้ไข หรือสร้างเชิงอรรถปลอมโดยโปรแกรม |
| ตัวคั่นแสดงช่องว่างเพิ่ม | Run ที่มีอยู่ไม่ได้ถูกลบ | เรียก `clearChildren()` ก่อนเพิ่ม Run ใหม่ |
| รูปแบบแสดงผลแตกต่าง | Run สืบทอดสไตล์จากตัวคั่นเดิม | ตั้งค่าคุณสมบัติฟอนต์ของ `Run` อย่างชัดเจนหากต้องการลักษณะเฉพาะ |

## ตัวอย่างทำงานเต็มรูปแบบ

รวมส่วนต่าง ๆ เข้าด้วยกัน นี่คือตัวอย่างคลาส Java ที่สมบูรณ์ซึ่งคุณสามารถคัดลอก คอมไพล์ และรันได้:

```java
import com.aspose.words.*;
import java.awt.Color;

public class EditFootnoteSeparator {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Load the document
        String inputPath = "YOUR_DIRECTORY/docWithNotes.docx";
        Document doc = new Document(inputPath);

        // 2️⃣ Retrieve the footnote separator
        Separator footnoteSeparator = doc.getFootnoteSeparator();
        if (footnoteSeparator == null) {
            System.out.println("Document has no footnote separator.");
            return;
        }

        // 3️⃣ Replace the separator with a custom word (e.g., an em dash)
        Paragraph para = footnoteSeparator.getParagraphs().get(0);
        para.clearChildren();                       // Remove old runs
        Run customRun = new Run(doc, "—");          // Change "—" to any word you need
        customRun.getFont().setBold(true);         // Optional styling
        customRun.getFont().setSize(9);
        customRun.getFont().setColor(Color.DARK_GRAY);
        para.appendChild(customRun);

        // 4️⃣ Save the modified document
        String outputPath = "YOUR_DIRECTORY/ModifiedNotes.docx";
        doc.save(outputPath);

        System.out.println("Footnote separator edited successfully.");
    }
}
```

รันโปรแกรมแล้วเปิดไฟล์ `ModifiedNotes.docx` เพื่อยืนยันว่าตัวคั่นได้รับการอัปเดตแล้ว

## สรุป

ตอนนี้คุณรู้วิธี **แก้ไขตัวคั่นเชิงอรรถ** ในเอกสาร Word ด้วย Java และ Aspose.Words แล้ว คำแนะนำนี้ครอบคลุมการโหลดเอกสาร การดึงโหนดตัวคั่นพิเศษ การแทรก **คำตัวคั่นที่กำหนดเอง** และการบันทึกผลลัพธ์ โดยทำตามขั้นตอนเหล่านี้คุณยังสามารถ **เปลี่ยนตัวคั่นเชิงอรรถ** สำหรับส่วนต่อเนื่องหรือเชิงอรรถหน้าแรกได้

ต่อไปคุณอาจสนใจสำรวจ:

- การเพิ่มตัวคั่นที่แตกต่างสำหรับเชิงอรรถหน้าแรก (`getFootnoteSeparatorForFirstPage()`).
- การสร้างเชิงอรรถโดยโปรแกรมเมื่อไม่มีเชิงอรรถใด ๆ.
- การใช้ Aspose.Words เพื่อจัดรูปแบบข้อความเชิงอรรถ (ฟอนต์, สี, การเยื้อง).

อย่าลังเลที่จะทดลองใช้ตัวอักษรหรือคำอื่น ๆ เพื่อให้สอดคล้องกับแบรนด์ของเอกสารของคุณ ขอให้สนุกกับการเขียนโค้ด!

## คุณควรเรียนรู้อะไรต่อไป?

บทแนะนำต่อไปนี้ครอบคลุมหัวข้อที่เกี่ยวข้องอย่างใกล้ชิดซึ่งต่อยอดจากเทคนิคที่แสดงในคู่มือนี้ แต่ละแหล่งข้อมูลมีตัวอย่างโค้ดทำงานเต็มรูปแบบพร้อมคำอธิบายทีละขั้นตอน เพื่อช่วยให้คุณเชี่ยวชาญฟีเจอร์ API เพิ่มเติมและสำรวจแนวทางการดำเนินการอื่น ๆ ในโปรเจคของคุณ

- [แทรกตัวคั่นสไตล์เอกสารใน Word](/words/english/net/programming-with-styles-and-themes/insert-style-separator/)
- [รับตัวคั่นสไตล์ย่อหน้าในเอกสาร Word](/words/english/net/document-formatting/get-paragraph-style-separator/)
- [วิธีโหลดเอกสาร Word ด้วย Aspose.Words Java: คู่มือฉบับสมบูรณ์](/words/english/java/document-operations/aspose-words-java-master-word-processing/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}