---
date: 2026-01-03
description: เรียนรู้วิธีการแทนที่ข้อความด้วย HTML ในเอกสาร Word โดยใช้ Aspose.Words
  for Java คู่มือทีละขั้นตอนพร้อมตัวอย่างโค้ด เคล็ดลับการใช้ regex แทนที่ข้อความใน
  Java และอื่น ๆ อีกมาก.
linktitle: Finding and Replacing Text
second_title: Aspose.Words Java Document Processing API
title: แทนที่ข้อความด้วย HTML โดยใช้ Aspose.Words สำหรับ Java
url: /th/java/document-manipulation/finding-and-replacing-text/
weight: 15
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# แทนที่ข้อความด้วย HTML ใน Aspose.Words for Java

## แนะนำการค้นหาและแทนที่ข้อความใน Aspose.Words for Java

Aspose.Words for Java เป็น API Java ที่ทรงพลังซึ่งช่วยให้คุณจัดการเอกสาร Word ด้วยโปรแกรม หนึ่งในงานที่พบบ่อยที่สุดคือ **การแทนที่ข้อความด้วย HTML** ไม่ว่าคุณจะอัปเดตตัวแปรในเทมเพลต, แทรกเนื้อหาที่มีสไตล์, หรือทำการแปลงข้อความเป็นจำนวนมาก ในคู่มือนี้เราจะอธิบายวิธีการแทนที่ข้อความ, วิธีการใช้ regex replace text java, และแม้กระทั่งการแทนที่ข้อความในส่วนหัว—ทั้งหมดนี้โดยรักษาโค้ดให้สะอาดและมีประสิทธิภาพ

## คำตอบสั้น
- **วิธีหลักในการแทนที่ข้อความด้วย HTML คืออะไร?** ใช้ `FindReplaceOptions` พร้อม callback ที่กำหนดเองเช่น `ReplaceWithHtmlEvaluator`  
- **ฉันสามารถละเว้นฟิลด์ขณะแทนที่ได้หรือไม่?** ได้ – ตั้งค่า `options.setIgnoreFields(true)`  
- **ต้องมีลิขสิทธิ์สำหรับการใช้งานในผลิตภัณฑ์หรือไม่?** จำเป็นต้องมีลิขสิทธิ์ Aspose.Words ที่ถูกต้องสำหรับการใช้งานเชิงพาณิชย์  
- **รองรับเวอร์ชัน Java ใด?** Aspose.Words for Java ทำงานกับ Java 8 ขึ้นไป  
- **รองรับ regex replace text java หรือไม่?** แน่นอน – ส่งอ็อบเจกต์ `Pattern` ไปยังเมธอด `replace`

## “replace text with html” คืออะไร?

การแทนที่ข้อความด้วย HTML หมายถึงการสลับตัวแปรข้อความธรรมดาด้วยมาร์กอัป HTML ที่มีความหลากหลาย (ตาราง, รายการ, การจัดรูปแบบ) พร้อมกับคงโครงสร้างของเอกสาร Word ไว้ Aspose.Words จะทำการแยกวิเคราะห์ HTML แล้วแทรกอ็อบเจกต์ Word ที่สอดคล้องกัน ทำให้คุณควบคุมเลย์เอาต์ขั้นสุดท้ายได้อย่างเต็มที่

## ทำไมต้องใช้ Aspose.Words สำหรับงานนี้?

- **ความแม่นยำของ Word เต็มรูปแบบ** – ไลบรารีคงรูปแบบทั้งหมด, ส่วนหัว, ส่วนท้าย, และการเปลี่ยนแปลงที่ติดตามไว้  
- **รองรับ regex ในตัว** – เหมาะสำหรับรูปแบบการค้นหาที่ซับซ้อน (`regex replace text java`)  
- **การควบคุมระดับละเอียด** – ตัวเลือกเช่น `IgnoreFields`, `IgnoreDeleted`, และ `UseLegacyOrder` ช่วยให้คุณปรับการทำงานให้ตรงกับความต้องการของคุณ  
- **ข้ามแพลตฟอร์ม** – ทำงานบน OS ใดก็ได้ที่รัน Java

## ข้อกำหนดเบื้องต้น

- สภาพแวดล้อมการพัฒนา Java (JDK 8+)  
- ไลบรารี Aspose.Words for Java – ดาวน์โหลดได้จาก [here](https://releases.aspose.com/words/java/)  
- เอกสาร Word ตัวอย่าง (`.docx`) เพื่อทดลอง

## การค้นหาและแทนที่ข้อความง่าย ๆ

```java
// Load the document
Document doc = new Document("your-document.docx");

// Create a DocumentBuilder
DocumentBuilder builder = new DocumentBuilder(doc);

// Find and replace text
builder.getRange().replace("old-text", "new-text", new FindReplaceOptions());

// Save the modified document
doc.save("modified-document.docx");
```

ตัวอย่างพื้นฐานนี้แสดง **วิธีการแทนที่ข้อความ** ด้วยเมธอด `replace` ซึ่งเป็นพื้นฐานสำหรับสถานการณ์ที่ซับซ้อนยิ่งขึ้น

## การใช้ Regular Expressions (regex replace text java)

```java
// Load the document
Document doc = new Document("your-document.docx");

// Create a DocumentBuilder
DocumentBuilder builder = new DocumentBuilder(doc);

// Use regular expressions for finding and replacing text
Pattern regex = Pattern.compile("your-pattern");
builder.getRange().replace(regex, "replacement-text", new FindReplaceOptions());

// Save the modified document
doc.save("modified-document.docx");
```

Regular expressions ให้คุณจับคู่รูปแบบได้อย่างทรงพลัง เหมาะสำหรับตัวแปรแบบไดนามิกหรือขอบเขตคำที่ซับซ้อน

## การละเว้นข้อความภายในฟิลด์ (aspose words replace text)

```java
// Load the document
Document doc = new Document("your-document.docx");

// Create a FindReplaceOptions instance and set IgnoreFields to true
FindReplaceOptions options = new FindReplaceOptions();
options.setIgnoreFields(true);

// Use options when replacing text
doc.getRange().replace("text-to-replace", "new-text", options);

// Save the modified document
doc.save("modified-document.docx");
```

ตั้งค่า `IgnoreFields` เพื่อให้ฟิลด์เช่น merge fields, หมายเลขหน้า หรือโค้ดฟิลด์อื่น ๆ ไม่ถูกแก้ไขขณะคุณแทนที่เนื้อหาที่อยู่รอบข้าง

## การละเว้นข้อความภายในการลบ Revision

```java
// Load the document
Document doc = new Document("your-document.docx");

// Create a FindReplaceOptions instance and set IgnoreDeleted to true
FindReplaceOptions options = new FindReplaceOptions();
options.setIgnoreDeleted(true);

// Use options when replacing text
doc.getRange().replace("text-to-replace", "new-text", options);

// Save the modified document
doc.save("modified-document.docx");
```

ช่วยป้องกันไม่ให้ข้อความที่ถูกทำเครื่องหมายว่าลบ (tracked changes) ถูกเปลี่ยนแปลง

## การละเว้นข้อความภายในการแทรก Revision

```java
// Load the document
Document doc = new Document("your-document.docx");

// Create a FindReplaceOptions instance and set IgnoreInserted to true
FindReplaceOptions options = new FindReplaceOptions();
options.setIgnoreInserted(true);

// Use options when replacing text
doc.getRange().replace("text-to-replace", "new-text", options);

// Save the modified document
doc.save("modified-document.docx");
```

มีประโยชน์เมื่อคุณต้องการคงข้อความที่เพิ่งแทรกไว้ในระหว่างการแทนที่จำนวนมาก

## การแทนที่ข้อความด้วย HTML

```java
// Load the document
Document doc = new Document("your-document.docx");

// Create a FindReplaceOptions instance with a custom replacing callback
FindReplaceOptions options = new FindReplaceOptions();
options.setReplacingCallback(new ReplaceWithHtmlEvaluator(options));

// Use options when replacing text
doc.getRange().replace("text-to-replace", "new-html-content", options);

// Save the modified document
doc.save("modified-document.docx");
```

ที่นี่เราจะ **แทนที่ข้อความด้วย HTML** โดยให้ evaluator ที่กำหนดเองทำการแยกวิเคราะห์สตริง HTML และแทรกโหนด Word ที่เหมาะสม

## การแทนที่ข้อความในส่วนหัวและส่วนท้าย (replace text in headers)

```java
// Load the document
Document doc = new Document("your-document.docx");

// Get the collection of headers and footers
HeaderFooterCollection headersFooters = doc.getFirstSection().getHeadersFooters();

// Choose the header or footer type you want to replace text in (e.g., HeaderFooterType.FOOTER_PRIMARY)
HeaderFooter footer = headersFooters.getByHeaderFooterType(HeaderFooterType.FOOTER_PRIMARY);

// Create a FindReplaceOptions instance and apply it to the footer's range
FindReplaceOptions options = new FindReplaceOptions();
footer.getRange().replace("text-to-replace", "new-text", options);

// Save the modified document
doc.save("modified-document.docx");
```

การแทนที่ที่เจาะจงในส่วนหัวหรือส่วนท้ายช่วยให้การสร้างแบรนด์ของเอกสารของคุณคงที่

## การแสดงการเปลี่ยนแปลงสำหรับลำดับส่วนหัวและส่วนท้าย

```java
// Load the document
Document doc = new Document("your-document.docx");

// Get the first section
Section firstPageSection = doc.getFirstSection();

// Create a FindReplaceOptions instance and apply it to the document's range
FindReplaceOptions options = new FindReplaceOptions();
options.setReplacingCallback(new ReplaceLog());

// Replace text that affects header and footer orders
doc.getRange().replace(Pattern.compile("(header|footer)"), "", options);

// Save the modified document
doc.save("modified-document.docx");
```

ตัวอย่างนี้บันทึกการเปลี่ยนแปลง ช่วยให้คุณตรวจสอบการแก้ไขลำดับส่วนหัว/ส่วนท้ายได้

## การแทนที่ข้อความด้วยฟิลด์

```java
// Load the document
Document doc = new Document("your-document.docx");

// Create a FindReplaceOptions instance and set a custom replacing callback for fields
FindReplaceOptions options = new FindReplaceOptions();
options.setReplacingCallback(new ReplaceTextWithFieldHandler(FieldType.FIELD_MERGE_FIELD));

// Use options when replacing text
doc.getRange().replace(Pattern.compile("PlaceHolder(\\d+)"), "", options);

// Save the modified document
doc.save("modified-document.docx");
```

การแทรกฟิลด์ (เช่น merge fields) ทำให้คุณสร้างเอกสารแบบไดนามิกที่สามารถเติมข้อมูลในภายหลังได้

## การแทนที่ด้วย Evaluator

```java
// Load the document
Document doc = new Document("your-document.docx");

// Create a FindReplaceOptions instance and set a custom replacing callback
FindReplaceOptions options = new FindReplaceOptions();
options.setReplacingCallback(new MyReplaceEvaluator());

// Use options when replacing text
doc.getRange().replace(Pattern.compile("[s|m]ad"), "", options);

// Save the modified document
doc.save("modified-document.docx");
```

Evaluator ที่กำหนดเองให้คุณควบคุมข้อความที่แทนที่ได้อย่างเต็มที่ผ่านโปรแกรม

## การแทนที่ด้วย Regex (regex replace text java)

```java
// Load the document
Document doc = new Document("your-document.docx");

// Use regular expressions for finding and replacing text
doc.getRange().replace(Pattern.compile("[s|m]ad"), "bad", new FindReplaceOptions());

// Save the modified document
doc.save("modified-document.docx");
```

วิธีสั้น ๆ เพื่อทำการแทนที่ตามรูปแบบทั่วทั้งเอกสาร

## การรับรู้และการแทนที่ภายในรูปแบบการแทนที่

```java
// Load the document
Document doc = new Document("your-document.docx");

// Create a FindReplaceOptions instance with UseSubstitutions set to true
FindReplaceOptions options = new FindReplaceOptions();
options.setUseSubstitutions(true);

// Use options when replacing text with a pattern
doc.getRange().replace(Pattern.compile("([A-z]+) give money to ([A-z]+)"), "$2 take money from $1", options);

// Save the modified document
doc.save("modified-document.docx");
```

เปิดใช้งาน `UseSubstitutions` เพื่ออ้างอิงกลุ่มจับ (capture groups) โดยตรงในสตริงการแทนที่

## การแทนที่ด้วยสตริง (replace text word java)

```java
// Load the document
Document doc = new Document("your-document.docx");

// Replace text with a string
doc.getRange().replace("text-to-replace", "new-string", new FindReplaceOptions());

// Save the modified document
doc.save("modified-document.docx");
```

รูปแบบการแทนที่ที่ง่ายที่สุด – เหมาะสำหรับตัวแปรคงที่

## การใช้ Legacy Order

```java
// Load the document
Document doc = new Document("your-document.docx");

// Create a FindReplaceOptions instance and set UseLegacyOrder to true
FindReplaceOptions options = new FindReplaceOptions();
options.setUseLegacyOrder(true);

// Use options when replacing text
doc.getRange().replace(Pattern.compile("\\[(.*?)\\]"), "", options);

// Save the modified document
doc.save("modified-document.docx");
```

Legacy order อาจจำเป็นเมื่อทำงานกับเอกสารเก่าที่พึ่งพาการเดินทางตามลำดับเดิม

## การแทนที่ข้อความในตาราง

```java
// Load the document
Document doc = new Document("your-document.docx");

// Get a specific table (e.g., the first table)
Table table = (Table) doc.getChild(NodeType.TABLE, 0, true);

// Use FindReplaceOptions for replacing text in the table
table.getRange().replace("old-text", "new-text", new FindReplaceOptions());

// Save the modified document
doc.save("modified-document.docx");
```

การแทนที่ที่เจาะจงภายในตารางช่วยป้องกันการเปลี่ยนแปลงที่ไม่ต้องการในส่วนอื่นของเอกสาร

## ปัญหาทั่วไปและวิธีแก้

- **HTML ไม่แสดงผลอย่างถูกต้อง** – ตรวจสอบให้แน่ใจว่า HTML ของคุณมีโครงสร้างที่ถูกต้องและรวมแท็กที่จำเป็น (เช่น `<p>`, `<table>`)  
- **Regex ไม่ตรง** – อย่าลืม escape ตัวอักษรพิเศษและใช้ `Pattern.CASE_INSENSITIVE` หากจำเป็น  
- **ฟิลด์ถูกแทนที่โดยไม่ได้ตั้งใจ** – ตั้งค่า `options.setIgnoreFields(true)` เพื่อปกป้องฟิลด์เหล่านั้น  
- **ประสิทธิภาพบนเอกสารขนาดใหญ่** – ใช้ `UseLegacyOrder` หรือประมวลผลส่วนย่อยแยกกันเพื่อลดการใช้หน่วยความจำ

## คำถามที่พบบ่อย

**Q: ฉันจะดาวน์โหลด Aspose.Words for Java ได้จากที่ไหน?**  
A: คุณสามารถดาวน์โหลด Aspose.Words for Java จากเว็บไซต์โดยไปที่ [this link](https://releases.aspose.com/words/java/)  

**Q: ฉันสามารถใช้ regular expressions สำหรับการแทนที่ข้อความได้หรือไม่?**  
A: ได้ คุณสามารถใช้ regular expressions สำหรับการแทนที่ข้อความใน Aspose.Words for Java ซึ่งช่วยให้คุณทำการค้นหาและแทนที่ที่ซับซ้อนและยืดหยุ่นมากขึ้น  

**Q: ฉันจะละเว้นข้อความภายในฟิลด์ระหว่างการแทนที่ได้อย่างไร?**  
A: ตั้งค่า property `IgnoreFields` ของ `FindReplaceOptions` เป็น `true` ซึ่งจะทำให้ฟิลด์เช่น merge fields ไม่ถูกแทนที่  

**Q: สามารถแทนที่ข้อความภายในส่วนหัวและส่วนท้ายได้หรือไม่?**  
A: แน่นอน เข้าถึงส่วนหัวหรือส่วนท้ายที่ต้องการผ่าน `HeaderFooterCollection` แล้วใช้เมธอด `replace` พร้อมตัวเลือกที่เหมาะสม  

**Q: ตัวเลือก `UseLegacyOrder` ทำหน้าที่อะไร?**  
A: `UseLegacyOrder` บังคับให้เครื่องมือค้นหา/แทนที่เดินทางผ่านโหนดตามลำดับเดิมที่ใช้ในเวอร์ชันเก่าของ Aspose.Words ซึ่งอาจเป็นประโยชน์สำหรับความเข้ากันได้กับเอกสาร legacy  

---

**Last Updated:** 2026-01-03  
**Tested With:** Aspose.Words for Java 24.12  
**Author:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}