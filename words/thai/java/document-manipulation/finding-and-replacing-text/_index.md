---
title: การค้นหาและแทนที่ข้อความใน Aspose.Words สำหรับ Java
linktitle: การค้นหาและการแทนที่ข้อความ
second_title: API การประมวลผลเอกสาร Java ของ Aspose.Words
description: เรียนรู้วิธีค้นหาและแทนที่ข้อความในเอกสาร Word ด้วย Aspose.Words สำหรับ Java คำแนะนำทีละขั้นตอนพร้อมตัวอย่างโค้ด พัฒนาทักษะการจัดการเอกสาร Java ของคุณ
weight: 15
url: /th/java/document-manipulation/finding-and-replacing-text/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# การค้นหาและแทนที่ข้อความใน Aspose.Words สำหรับ Java


## บทนำเกี่ยวกับการค้นหาและแทนที่ข้อความใน Aspose.Words สำหรับ Java

Aspose.Words for Java เป็น Java API ที่ทรงพลังซึ่งช่วยให้คุณสามารถทำงานกับเอกสาร Word ได้ด้วยการเขียนโปรแกรม หนึ่งในงานทั่วไปเมื่อจัดการกับเอกสาร Word คือการค้นหาและแทนที่ข้อความ ไม่ว่าคุณจะต้องอัปเดตตัวแทนในเทมเพลตหรือดำเนินการจัดการข้อความที่ซับซ้อนมากขึ้น Aspose.Words for Java ก็สามารถช่วยให้คุณบรรลุเป้าหมายได้อย่างมีประสิทธิภาพ

## ข้อกำหนดเบื้องต้น

ก่อนที่เราจะเจาะลึกรายละเอียดของการค้นหาและการแทนที่ข้อความ โปรดตรวจสอบให้แน่ใจว่าคุณมีข้อกำหนดเบื้องต้นต่อไปนี้:

- สภาพแวดล้อมการพัฒนา Java
- Aspose.Words สำหรับไลบรารี Java
- เอกสารตัวอย่าง Word ที่จะใช้งาน

 คุณสามารถดาวน์โหลดไลบรารี Aspose.Words สำหรับ Java ได้จาก[ที่นี่](https://releases.aspose.com/words/java/).

## การค้นหาและการแทนที่ข้อความธรรมดา

```java
// โหลดเอกสาร
Document doc = new Document("your-document.docx");

// สร้าง DocumentBuilder
DocumentBuilder builder = new DocumentBuilder(doc);

// ค้นหาและแทนที่ข้อความ
builder.getRange().replace("old-text", "new-text", new FindReplaceOptions());

// บันทึกเอกสารที่แก้ไข
doc.save("modified-document.docx");
```

 ในตัวอย่างนี้ เราโหลดเอกสาร Word สร้าง`DocumentBuilder` และใช้`replace` วิธีการค้นหาและแทนที่ “ข้อความเก่า” ด้วย “ข้อความใหม่” ภายในเอกสาร

## การใช้นิพจน์ทั่วไป

นิพจน์ทั่วไปให้ความสามารถในการจับคู่รูปแบบที่มีประสิทธิภาพสำหรับการค้นหาและแทนที่ข้อความ Aspose.Words สำหรับ Java รองรับนิพจน์ทั่วไปสำหรับการค้นหาและแทนที่ขั้นสูง

```java
// โหลดเอกสาร
Document doc = new Document("your-document.docx");

// สร้าง DocumentBuilder
DocumentBuilder builder = new DocumentBuilder(doc);

// ใช้นิพจน์ทั่วไปในการค้นหาและแทนที่ข้อความ
Pattern regex = Pattern.compile("your-pattern");
builder.getRange().replace(regex, "replacement-text", new FindReplaceOptions());

// บันทึกเอกสารที่แก้ไข
doc.save("modified-document.docx");
```

ในตัวอย่างนี้ เราใช้รูปแบบนิพจน์ปกติเพื่อค้นหาและแทนที่ข้อความภายในเอกสาร

## การละเว้นข้อความภายในฟิลด์

คุณสามารถกำหนดค่า Aspose.Words เพื่อละเว้นข้อความภายในฟิลด์เมื่อดำเนินการค้นหาและแทนที่

```java
// โหลดเอกสาร
Document doc = new Document("your-document.docx");

// สร้างอินสแตนซ์ FindReplaceOptions และตั้งค่า IgnoreFields เป็นจริง
FindReplaceOptions options = new FindReplaceOptions();
options.setIgnoreFields(true);

// ใช้ตัวเลือกเมื่อแทนที่ข้อความ
doc.getRange().replace("text-to-replace", "new-text", options);

// บันทึกเอกสารที่แก้ไข
doc.save("modified-document.docx");
```

สิ่งนี้มีประโยชน์เมื่อคุณต้องการให้ข้อความภายในฟิลด์ เช่น ฟิลด์ผสาน ไม่ถูกแทนที่

## การละเว้นข้อความภายในการลบแก้ไข

คุณสามารถกำหนดค่า Aspose.Words เพื่อละเว้นข้อความภายในการแก้ไขการลบในระหว่างการค้นหาและแทนที่

```java
// โหลดเอกสาร
Document doc = new Document("your-document.docx");

// สร้างอินสแตนซ์ FindReplaceOptions และตั้งค่า IgnoreDeleted เป็นจริง
FindReplaceOptions options = new FindReplaceOptions();
options.setIgnoreDeleted(true);

// ใช้ตัวเลือกเมื่อแทนที่ข้อความ
doc.getRange().replace("text-to-replace", "new-text", options);

// บันทึกเอกสารที่แก้ไข
doc.save("modified-document.docx");
```

สิ่งนี้ช่วยให้คุณสามารถยกเว้นข้อความที่ถูกทำเครื่องหมายสำหรับการลบออกจากการติดตามการเปลี่ยนแปลงจากการถูกแทนที่

## การละเว้นการแก้ไขข้อความภายในส่วนแทรก

คุณสามารถกำหนดค่า Aspose.Words เพื่อละเว้นข้อความภายในการแทรกการแก้ไขในระหว่างการค้นหาและแทนที่

```java
// โหลดเอกสาร
Document doc = new Document("your-document.docx");

// สร้างอินสแตนซ์ FindReplaceOptions และตั้งค่า IgnoreInserted เป็น true
FindReplaceOptions options = new FindReplaceOptions();
options.setIgnoreInserted(true);

// ใช้ตัวเลือกเมื่อแทนที่ข้อความ
doc.getRange().replace("text-to-replace", "new-text", options);

// บันทึกเอกสารที่แก้ไข
doc.save("modified-document.docx");
```

สิ่งนี้ช่วยให้คุณสามารถยกเว้นข้อความที่ถูกทำเครื่องหมายว่าแทรกไว้ในการติดตามการเปลี่ยนแปลงจากการถูกแทนที่

## การแทนที่ข้อความด้วย HTML

คุณสามารถใช้ Aspose.Words สำหรับ Java เพื่อแทนที่ข้อความด้วยเนื้อหา HTML ได้

```java
// โหลดเอกสาร
Document doc = new Document("your-document.docx");

// สร้างอินสแตนซ์ FindReplaceOptions ด้วยคอลแบ็กการแทนที่แบบกำหนดเอง
FindReplaceOptions options = new FindReplaceOptions();
options.setReplacingCallback(new ReplaceWithHtmlEvaluator(options));

// ใช้ตัวเลือกเมื่อแทนที่ข้อความ
doc.getRange().replace("text-to-replace", "new-html-content", options);

// บันทึกเอกสารที่แก้ไข
doc.save("modified-document.docx");
```

 ในตัวอย่างนี้ เราใช้แบบกำหนดเอง`ReplaceWithHtmlEvaluator` เพื่อแทนที่ข้อความด้วยเนื้อหา HTML

## การแทนที่ข้อความในส่วนหัวและส่วนท้าย

คุณสามารถค้นหาและแทนที่ข้อความภายในส่วนหัวและส่วนท้ายของเอกสาร Word ของคุณได้

```java
// โหลดเอกสาร
Document doc = new Document("your-document.docx");

// รับคอลเลกชันของส่วนหัวและส่วนท้าย
HeaderFooterCollection headersFooters = doc.getFirstSection().getHeadersFooters();

// เลือกประเภทส่วนหัวหรือส่วนท้ายที่คุณต้องการแทนที่ข้อความ (เช่น HeaderFooterType.FOOTER_PRIMARY)
HeaderFooter footer = headersFooters.getByHeaderFooterType(HeaderFooterType.FOOTER_PRIMARY);

// สร้างอินสแตนซ์ FindReplaceOptions และนำไปใช้กับช่วงของส่วนท้าย
FindReplaceOptions options = new FindReplaceOptions();
footer.getRange().replace("text-to-replace", "new-text", options);

// บันทึกเอกสารที่แก้ไข
doc.save("modified-document.docx");
```

สิ่งนี้ทำให้คุณสามารถแทนที่ข้อความโดยเฉพาะในส่วนหัวและส่วนท้ายได้

## แสดงการเปลี่ยนแปลงสำหรับคำสั่งซื้อส่วนหัวและส่วนท้าย

คุณสามารถใช้ Aspose.Words เพื่อแสดงการเปลี่ยนแปลงสำหรับคำสั่งซื้อส่วนหัวและส่วนท้ายในเอกสารของคุณได้

```java
// โหลดเอกสาร
Document doc = new Document("your-document.docx");

// รับส่วนแรก
Section firstPageSection = doc.getFirstSection();

//สร้างอินสแตนซ์ FindReplaceOptions และนำไปใช้กับช่วงของเอกสาร
FindReplaceOptions options = new FindReplaceOptions();
options.setReplacingCallback(new ReplaceLog());

// แทนที่ข้อความที่ส่งผลต่อคำสั่งซื้อส่วนหัวและส่วนท้าย
doc.getRange().replace(Pattern.compile("(header|footer)"), "", options);

// บันทึกเอกสารที่แก้ไข
doc.save("modified-document.docx");
```

สิ่งนี้ช่วยให้คุณมองเห็นการเปลี่ยนแปลงที่เกี่ยวข้องกับลำดับส่วนหัวและส่วนท้ายในเอกสารของคุณได้

## การแทนที่ข้อความด้วยฟิลด์

คุณสามารถแทนที่ข้อความด้วยฟิลด์โดยใช้ Aspose.Words สำหรับ Java

```java
// โหลดเอกสาร
Document doc = new Document("your-document.docx");

// สร้างอินสแตนซ์ FindReplaceOptions และตั้งค่าการเรียกกลับการแทนที่แบบกำหนดเองสำหรับฟิลด์
FindReplaceOptions options = new FindReplaceOptions();
options.setReplacingCallback(new ReplaceTextWithFieldHandler(FieldType.FIELD_MERGE_FIELD));

// ใช้ตัวเลือกเมื่อแทนที่ข้อความ
doc.getRange().replace(Pattern.compile("PlaceHolder(\\d+)"), "", options);

// บันทึกเอกสารที่แก้ไข
doc.save("modified-document.docx");
```

 ในตัวอย่างนี้ เราจะแทนที่ข้อความด้วยฟิลด์และระบุประเภทฟิลด์ (เช่น`FieldType.FIELD_MERGE_FIELD`-

## การแทนที่ด้วยผู้ประเมิน

คุณสามารถใช้ตัวประเมินแบบกำหนดเองเพื่อกำหนดข้อความแทนที่แบบไดนามิก

```java
// โหลดเอกสาร
Document doc = new Document("your-document.docx");

// สร้างอินสแตนซ์ FindReplaceOptions และตั้งค่าการโทรกลับการแทนที่แบบกำหนดเอง
FindReplaceOptions options = new FindReplaceOptions();
options.setReplacingCallback(new MyReplaceEvaluator());

// ใช้ตัวเลือกเมื่อแทนที่ข้อความ
doc.getRange().replace(Pattern.compile("[s|m]ad"), "", options);

// บันทึกเอกสารที่แก้ไข
doc.save("modified-document.docx");
```

ในตัวอย่างนี้ เราใช้เครื่องมือประเมินแบบกำหนดเอง (`MyReplaceEvaluator`) เพื่อแทนที่ข้อความ

## การแทนที่ด้วย Regex

Aspose.Words สำหรับ Java ช่วยให้คุณสามารถแทนที่ข้อความโดยใช้นิพจน์ทั่วไป

```java
// โหลดเอกสาร
Document doc = new Document("your-document.docx");

// ใช้นิพจน์ทั่วไปในการค้นหาและแทนที่ข้อความ
doc.getRange().replace(Pattern.compile("[s|m]ad"), "bad", new FindReplaceOptions());

// บันทึกเอกสารที่แก้ไข
doc.save("modified-document.docx");
```

ในตัวอย่างนี้ เราใช้รูปแบบนิพจน์ปกติเพื่อค้นหาและแทนที่ข้อความภายในเอกสาร

## การรับรู้และการทดแทนภายในรูปแบบการทดแทน

คุณสามารถจดจำและแทนที่ภายในรูปแบบการแทนที่ได้โดยใช้ Aspose.Words สำหรับ Java

```java
// โหลดเอกสาร
Document doc = new Document("your-document.docx");

// สร้างอินสแตนซ์ FindReplaceOptions โดยตั้งค่า UseSubstitutions เป็น true
FindReplaceOptions options = new FindReplaceOptions();
options.setUseSubstitutions(true);

// ใช้ตัวเลือกเมื่อแทนที่ข้อความด้วยรูปแบบ
doc.getRange().replace(Pattern.compile("([A-z]+) give money to ([A-z]+)"), "$2 take money from $1", options);

// บันทึกเอกสารที่แก้ไข
doc.save("modified-document.docx");
```

สิ่งนี้ช่วยให้คุณสามารถดำเนินการทดแทนภายในรูปแบบการทดแทนสำหรับการเปลี่ยนขั้นสูงเพิ่มเติมได้

## การแทนที่ด้วยสตริง

คุณสามารถแทนที่ข้อความด้วยสตริงง่ายๆ ได้โดยใช้ Aspose.Words สำหรับ Java

```java
// โหลดเอกสาร
Document doc = new Document("your-document.docx");

// แทนที่ข้อความด้วยสตริง
doc.getRange().replace("text-to-replace", "new-string", new FindReplaceOptions());

// บันทึกเอกสารที่แก้ไข
doc.save("modified-document.docx");
```

ในตัวอย่างนี้ เราจะแทนที่ "text-to-replace" ด้วย "new-string" ภายในเอกสาร

## การใช้คำสั่งแบบ Legacy

คุณสามารถใช้คำสั่งเดิมเมื่อดำเนินการค้นหาและแทนที่

```java
// โหลดเอกสาร
Document doc = new Document("your-document.docx");

// สร้างอินสแตนซ์ FindReplaceOptions และตั้งค่า UseLegacyOrder เป็นจริง
FindReplaceOptions options = new FindReplaceOptions();
options.setUseLegacyOrder(true);

// ใช้ตัวเลือกเมื่อแทนที่ข้อความ
doc.getRange().replace(Pattern.compile("\\[(.*?)\\]"), "", options);

// บันทึกเอกสารที่แก้ไข
doc.save("modified-document.docx");
```

สิ่งนี้ช่วยให้คุณใช้คำสั่งเดิมในการค้นหาและแทนที่ได้

## การแทนที่ข้อความในตาราง

คุณสามารถค้นหาและแทนที่ข้อความภายในตารางในเอกสาร Word ของคุณได้

```java
// โหลดเอกสาร
Document doc = new Document("your-document.docx");

// รับตารางที่เฉพาะเจาะจง (เช่น ตารางแรก)
Table table = (Table) doc.getChild(NodeType.TABLE, 0, true);

//ใช้ FindReplaceOptions เพื่อแทนที่ข้อความในตาราง
table.getRange().replace("old-text", "new-text", new FindReplaceOptions());

// บันทึกเอกสารที่แก้ไข
doc.save("modified-document.docx");
```

สิ่งนี้ทำให้คุณสามารถแทนที่ข้อความเฉพาะภายในตารางได้

## บทสรุป

Aspose.Words สำหรับ Java มีความสามารถที่ครอบคลุมสำหรับการค้นหาและแทนที่ข้อความในเอกสาร Word ไม่ว่าคุณจะต้องดำเนินการแทนที่ข้อความธรรมดาหรือการดำเนินการขั้นสูงโดยใช้นิพจน์ทั่วไป การจัดการฟิลด์ หรือตัวประเมินแบบกำหนดเอง Aspose.Words สำหรับ Java ก็มีให้คุณครบครัน อย่าลืมสำรวจเอกสารประกอบและตัวอย่างมากมายที่ Aspose จัดเตรียมไว้เพื่อใช้ประโยชน์จากศักยภาพทั้งหมดของไลบรารี Java ที่ทรงพลังนี้

## คำถามที่พบบ่อย

### ฉันจะดาวน์โหลด Aspose.Words สำหรับ Java ได้อย่างไร?

 คุณสามารถดาวน์โหลด Aspose.Words สำหรับ Java ได้จากเว็บไซต์โดยเข้าไปที่[ลิงค์นี้](https://releases.aspose.com/words/java/).

### ฉันสามารถใช้นิพจน์ทั่วไปเพื่อแทนที่ข้อความได้หรือไม่

ใช่ คุณสามารถใช้นิพจน์ทั่วไปเพื่อแทนที่ข้อความใน Aspose.Words สำหรับ Java ได้ วิธีนี้ทำให้คุณสามารถค้นหาและแทนที่ได้ในระดับขั้นสูงและยืดหยุ่นยิ่งขึ้น

### ฉันจะละเว้นข้อความภายในฟิลด์ในระหว่างการแทนที่ได้อย่างไร

หากต้องการละเว้นข้อความภายในฟิลด์ระหว่างการแทนที่ คุณสามารถตั้งค่า`IgnoreFields` ทรัพย์สินของ`FindReplaceOptions` ถึง`true`วิธีนี้จะช่วยให้แน่ใจว่าข้อความภายในฟิลด์ เช่น ฟิลด์ผสาน จะถูกแยกออกจากการแทนที่

### ฉันสามารถแทนที่ข้อความภายในส่วนหัวและส่วนท้ายได้หรือไม่

 ใช่ คุณสามารถแทนที่ข้อความภายในส่วนหัวและส่วนท้ายของเอกสาร Word ของคุณได้ เพียงเข้าถึงส่วนหัวหรือส่วนท้ายที่เหมาะสมแล้วใช้`replace` วิธีการตามที่ต้องการ`FindReplaceOptions`.

### ตัวเลือก UseLegacyOrder มีไว้ใช้งานอะไร

 การ`UseLegacyOrder` ตัวเลือกใน`FindReplaceOptions` ช่วยให้คุณสามารถใช้ลำดับแบบเดิมเมื่อดำเนินการค้นหาและแทนที่ ซึ่งอาจมีประโยชน์ในสถานการณ์บางสถานการณ์ที่ต้องการใช้ลำดับแบบเดิม
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
