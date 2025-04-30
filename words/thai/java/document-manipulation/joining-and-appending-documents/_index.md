---
"description": "เรียนรู้วิธีรวมและผนวกเอกสารอย่างง่ายดายโดยใช้ Aspose.Words สำหรับ Java รักษาการจัดรูปแบบ จัดการส่วนหัว ส่วนท้าย และอื่นๆ"
"linktitle": "การเข้าร่วมและการผนวกเอกสาร"
"second_title": "API การประมวลผลเอกสาร Java ของ Aspose.Words"
"title": "การเข้าร่วมและการผนวกเอกสารใน Aspose.Words สำหรับ Java"
"url": "/th/java/document-manipulation/joining-and-appending-documents/"
"weight": 30
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# การเข้าร่วมและการผนวกเอกสารใน Aspose.Words สำหรับ Java


## บทนำเกี่ยวกับการรวมและผนวกเอกสารใน Aspose.Words สำหรับ Java

ในบทช่วยสอนนี้ เราจะมาเรียนรู้วิธีการรวมและผนวกเอกสารโดยใช้ไลบรารี Aspose.Words สำหรับ Java คุณจะได้เรียนรู้วิธีการผสานเอกสารหลายฉบับเข้าด้วยกันอย่างราบรื่นในขณะที่ยังคงรักษารูปแบบและโครงสร้างเอาไว้

## ข้อกำหนดเบื้องต้น

ก่อนที่เราจะเริ่มต้น ตรวจสอบให้แน่ใจว่าคุณได้ตั้งค่า Aspose.Words สำหรับ Java API ไว้ในโปรเจ็กต์ Java ของคุณแล้ว

## ตัวเลือกการเข้าร่วมเอกสาร

### การผนวกแบบง่าย

```java
Document srcDoc = new Document("source.docx");
Document dstDoc = new Document("destination.docx");
dstDoc.appendDocument(srcDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING);
```

### ผนวกด้วยตัวเลือกรูปแบบการนำเข้า

```java
ImportFormatOptions options = new ImportFormatOptions();
options.setKeepSourceNumbering(true);
dstDoc.appendDocument(srcDoc, ImportFormatMode.USE_DESTINATION_STYLES, options);
```

### ผนวกเข้ากับเอกสารเปล่า

```java
Document srcDoc = new Document("source.docx");
Document dstDoc = new Document();
dstDoc.removeAllChildren();
dstDoc.appendDocument(srcDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING);
```

### ผนวกกับการแปลงหมายเลขหน้า

```java
Document srcDoc = new Document("source.docx");
Document dstDoc = new Document("destination.docx");
dstDoc.appendDocument(srcDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING);
convertNumPageFieldsToPageRef(dstDoc); // แปลงฟิลด์ NUMPAGES
dstDoc.updatePageLayout(); // อัปเดตเค้าโครงหน้าเพื่อการกำหนดหมายเลขที่ถูกต้อง
```

## การจัดการการตั้งค่าหน้าต่างๆ

เมื่อผนวกเอกสารที่มีการตั้งค่าหน้าต่างกัน:

```java
srcDoc.getFirstSection().getPageSetup().setSectionStart(SectionStart.CONTINUOUS);
srcDoc.getFirstSection().getPageSetup().setRestartPageNumbering(true);
// ตรวจสอบให้แน่ใจว่าการตั้งค่าหน้าตรงกับเอกสารปลายทาง
```

## การรวมเอกสารด้วยรูปแบบที่แตกต่างกัน

```java
dstDoc.appendDocument(srcDoc, ImportFormatMode.USE_DESTINATION_STYLES);
```

## พฤติกรรมสไตล์สมาร์ท

```java
ImportFormatOptions options = new ImportFormatOptions();
options.setSmartStyleBehavior(true);
builder.insertDocument(srcDoc, ImportFormatMode.USE_DESTINATION_STYLES, options);
```

## การแทรกเอกสารด้วย DocumentBuilder

```java
DocumentBuilder builder = new DocumentBuilder(dstDoc);
builder.insertDocument(srcDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING);
```

## การรักษาหมายเลขแหล่งที่มา

```java
ImportFormatOptions importFormatOptions = new ImportFormatOptions();
importFormatOptions.setKeepSourceNumbering(true);
dstDoc.appendDocument(srcDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING, importFormatOptions);
```

## การจัดการกล่องข้อความ

```java
ImportFormatOptions importFormatOptions = new ImportFormatOptions();
importFormatOptions.setIgnoreTextBoxes(false);
dstDoc.appendDocument(srcDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING, importFormatOptions);
```

## การจัดการส่วนหัวและส่วนท้าย

### การเชื่อมโยงส่วนหัวและส่วนท้าย

```java
srcDoc.getFirstSection().getHeadersFooters().linkToPrevious(true);
dstDoc.appendDocument(srcDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING);
```

### การยกเลิกการเชื่อมโยงส่วนหัวและส่วนท้าย

```java
srcDoc.getFirstSection().getHeadersFooters().linkToPrevious(false);
dstDoc.appendDocument(srcDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING);
```

## บทสรุป

Aspose.Words สำหรับ Java มอบเครื่องมือที่ยืดหยุ่นและทรงพลังสำหรับการเข้าร่วมและผนวกเอกสาร ไม่ว่าคุณจะต้องรักษาการจัดรูปแบบ จัดการการตั้งค่าหน้าต่างๆ หรือจัดการส่วนหัวและส่วนท้าย ทดลองใช้เทคนิคเหล่านี้เพื่อตอบสนองความต้องการในการประมวลผลเอกสารเฉพาะของคุณ

## คำถามที่พบบ่อย

### ฉันจะรวมเอกสารที่มีรูปแบบต่างๆ ได้อย่างราบรื่นอย่างไร

ในการรวมเอกสารที่มีรูปแบบที่แตกต่างกัน ให้ใช้ `ImportFormatMode.USE_DESTINATION_STYLES` เมื่อผนวก

### ฉันสามารถรักษาหมายเลขหน้าไว้เมื่อผนวกเอกสารได้หรือไม่

ใช่ คุณสามารถรักษาการกำหนดหมายเลขหน้าได้โดยใช้ `convertNumPageFieldsToPageRef` วิธีการและการอัปเดตเค้าโครงหน้า

### Smart Style Behavior คืออะไร?

Smart Style Behavior ช่วยรักษารูปแบบที่สม่ำเสมอเมื่อผนวกเอกสาร ใช้ร่วมกับ `ImportFormatOptions` เพื่อผลลัพธ์ที่ดียิ่งขึ้น

### ฉันจะจัดการกล่องข้อความเมื่อผนวกเอกสารได้อย่างไร

ชุด `importFormatOptions.setIgnoreTextBoxes(false)` เพื่อรวมกล่องข้อความระหว่างการผนวก

### หากฉันต้องการเชื่อมโยง/ยกเลิกการเชื่อมโยงส่วนหัวและส่วนท้ายระหว่างเอกสารจะทำอย่างไร

คุณสามารถเชื่อมโยงส่วนหัวและส่วนท้ายด้วย `linkToPrevious(true)` หรือยกเลิกการเชื่อมโยงกับ `linkToPrevious(false)` ตามความจำเป็น.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}