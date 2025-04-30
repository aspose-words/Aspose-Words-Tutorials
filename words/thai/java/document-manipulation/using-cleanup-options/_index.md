---
"description": "ปรับปรุงความชัดเจนของเอกสารด้วยตัวเลือก Aspose.Words สำหรับ Java Cleanup เรียนรู้วิธีลบย่อหน้าที่ว่างเปล่า ส่วนที่ไม่ได้ใช้ และอื่นๆ"
"linktitle": "การใช้ตัวเลือกการล้างข้อมูล"
"second_title": "API การประมวลผลเอกสาร Java ของ Aspose.Words"
"title": "การใช้ตัวเลือกการล้างข้อมูลใน Aspose.Words สำหรับ Java"
"url": "/th/java/document-manipulation/using-cleanup-options/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# การใช้ตัวเลือกการล้างข้อมูลใน Aspose.Words สำหรับ Java


## บทนำสู่การใช้ตัวเลือกการล้างข้อมูลใน Aspose.Words สำหรับ Java

ในบทช่วยสอนนี้ เราจะมาเรียนรู้วิธีใช้ตัวเลือกการล้างข้อมูลใน Aspose.Words สำหรับ Java เพื่อจัดการและล้างข้อมูลเอกสารระหว่างกระบวนการผสานจดหมาย ตัวเลือกการล้างข้อมูลช่วยให้คุณควบคุมด้านต่างๆ ของการล้างข้อมูลเอกสารได้ เช่น การลบย่อหน้าที่ว่างเปล่า ส่วนที่ไม่ได้ใช้ และอื่นๆ

## ข้อกำหนดเบื้องต้น

ก่อนที่เราจะเริ่ม ตรวจสอบให้แน่ใจว่าคุณได้รวมไลบรารี Aspose.Words สำหรับ Java ไว้ในโปรเจ็กต์ของคุณแล้ว คุณสามารถดาวน์โหลดได้จาก [ที่นี่](https://releases-aspose.com/words/java/).

## ขั้นตอนที่ 1: การลบย่อหน้าว่าง

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// แทรกเขตข้อมูลผสาน
FieldMergeField mergeFieldOption1 = (FieldMergeField) builder.insertField("MERGEFIELD", "Option_1");
mergeFieldOption1.setFieldName("Option_1");
builder.write(" ? ");
FieldMergeField mergeFieldOption2 = (FieldMergeField) builder.insertField("MERGEFIELD", "Option_2");
mergeFieldOption2.setFieldName("Option_2");

// ตั้งค่าตัวเลือกการล้างข้อมูล
doc.getMailMerge().setCleanupOptions(MailMergeCleanupOptions.REMOVE_EMPTY_PARAGRAPHS);

// เปิดใช้งานการล้างย่อหน้าด้วยเครื่องหมายวรรคตอน
doc.getMailMerge().setCleanupParagraphsWithPunctuationMarks(true);

// ดำเนินการรวมจดหมาย
doc.getMailMerge().execute(new String[] { "Option_1", "Option_2" }, new Object[] { null, null });

// บันทึกเอกสาร
doc.save("WorkingWithCleanupOptions.CleanupParagraphsWithPunctuationMarks.docx");
```

ในตัวอย่างนี้ เราจะสร้างเอกสารใหม่ แทรกฟิลด์ผสาน และตั้งค่าตัวเลือกการล้างข้อมูลเพื่อลบย่อหน้าว่าง นอกจากนี้ เรายังเปิดใช้งานการลบย่อหน้าที่มีเครื่องหมายวรรคตอน หลังจากดำเนินการผสานจดหมายแล้ว เอกสารจะถูกบันทึกโดยใช้การล้างข้อมูลที่ระบุ

## ขั้นตอนที่ 2: การลบภูมิภาคที่ไม่รวมเข้าด้วยกัน

```java
Document doc = new Document("Your Directory Path" + "Mail merge destination - Northwind suppliers.docx");
DataSet data = new DataSet();

// ตั้งค่าตัวเลือกการล้างข้อมูลเพื่อลบพื้นที่ที่ไม่ได้ใช้
doc.getMailMerge().setCleanupOptions(MailMergeCleanupOptions.REMOVE_UNUSED_REGIONS);

// ดำเนินการผสานจดหมายกับภูมิภาค
doc.getMailMerge().executeWithRegions(data);

// บันทึกเอกสาร
doc.save("WorkingWithCleanupOptions.RemoveUnmergedRegions.docx");
```

ในตัวอย่างนี้ เราจะเปิดเอกสารที่มีอยู่แล้วโดยใช้พื้นที่ผสาน ตั้งค่าตัวเลือกการล้างข้อมูลเพื่อลบพื้นที่ที่ไม่ได้ใช้ จากนั้นจึงดำเนินการผสานจดหมายด้วยข้อมูลว่าง กระบวนการนี้จะลบพื้นที่ที่ไม่ได้ใช้จากเอกสารโดยอัตโนมัติ

## ขั้นตอนที่ 3: การลบช่องว่าง

```java
Document doc = new Document("Your Directory Path" + "Table with fields.docx");

// ตั้งค่าตัวเลือกการล้างข้อมูลเพื่อลบฟิลด์ว่าง
doc.getMailMerge().setCleanupOptions(MailMergeCleanupOptions.REMOVE_EMPTY_FIELDS);

// ดำเนินการรวมจดหมาย
doc.getMailMerge().execute(new String[] { "FullName", "Company", "Address", "Address2", "City" },
    new Object[] { "James Bond", "MI5 Headquarters", "Milbank", "", "London" });

// บันทึกเอกสาร
doc.save("WorkingWithCleanupOptions.RemoveEmptyFields.docx");
```

ในตัวอย่างนี้ เราจะเปิดเอกสารที่มีฟิลด์ผสาน ตั้งค่าตัวเลือกการล้างข้อมูลเพื่อลบฟิลด์ว่าง และดำเนินการผสานจดหมายด้วยข้อมูล หลังจากการผสานแล้ว ฟิลด์ว่างทั้งหมดจะถูกลบออกจากเอกสาร

## ขั้นตอนที่ 4: การลบฟิลด์ที่ไม่ได้ใช้

```java
Document doc = new Document("Your Directory Path" + "Table with fields.docx");

// ตั้งค่าตัวเลือกการล้างข้อมูลเพื่อลบฟิลด์ที่ไม่ได้ใช้
doc.getMailMerge().setCleanupOptions(MailMergeCleanupOptions.REMOVE_UNUSED_FIELDS);

// ดำเนินการรวมจดหมาย
doc.getMailMerge().execute(new String[] { "FullName", "Company", "Address", "Address2", "City" },
    new Object[] { "James Bond", "MI5 Headquarters", "Milbank", "", "London" });

// บันทึกเอกสาร
doc.save("WorkingWithCleanupOptions.RemoveUnusedFields.docx");
```

ในตัวอย่างนี้ เราจะเปิดเอกสารที่มีฟิลด์ผสาน ตั้งค่าตัวเลือกการล้างข้อมูลเพื่อลบฟิลด์ที่ไม่ได้ใช้ และดำเนินการผสานจดหมายด้วยข้อมูล หลังจากการผสานแล้ว ฟิลด์ที่ไม่ได้ใช้ใดๆ จะถูกลบออกจากเอกสาร

## ขั้นตอนที่ 5: การลบฟิลด์ที่มี

```java
Document doc = new Document("Your Directory Path" + "Table with fields.docx");

// ตั้งค่าตัวเลือกการล้างข้อมูลเพื่อลบฟิลด์ที่มีอยู่
doc.getMailMerge().setCleanupOptions(MailMergeCleanupOptions.REMOVE_CONTAINING_FIELDS);

// ดำเนินการรวมจดหมาย
doc.getMailMerge().execute(new String[] { "FullName", "Company", "Address", "Address2", "City" },
    new Object[] { "James Bond", "MI5 Headquarters", "Milbank", "", "London" });

// บันทึกเอกสาร
doc.save("WorkingWithCleanupOptions.RemoveContainingFields.docx");
```

ในตัวอย่างนี้ เราจะเปิดเอกสารที่มีฟิลด์ผสาน ตั้งค่าตัวเลือกการล้างข้อมูลเพื่อลบฟิลด์ที่บรรจุอยู่ และดำเนินการผสานจดหมายด้วยข้อมูล หลังจากการผสานแล้ว ฟิลด์ต่างๆ จะถูกลบออกจากเอกสาร

## ขั้นตอนที่ 6: ลบแถวตารางว่าง

```java
Document doc = new Document("Your Directory Path" + "Table with fields.docx");

// ตั้งค่าตัวเลือกการล้างข้อมูลเพื่อลบแถวตารางที่ว่างเปล่า
doc.getMailMerge().setCleanupOptions(MailMergeCleanupOptions.REMOVE_EMPTY_TABLE_ROWS);

// ดำเนินการรวมจดหมาย
doc.getMailMerge().execute(new String[] { "FullName", "Company", "Address", "Address2", "City" },
    new Object[] { "James Bond", "MI5 Headquarters", "Milbank", "", "London" });

// บันทึกเอกสาร
doc.save("WorkingWithCleanupOptions.RemoveEmptyTableRows.docx");
```

ในตัวอย่างนี้ เราจะเปิดเอกสารที่มีตารางและฟิลด์ผสาน ตั้งค่าตัวเลือกการล้างข้อมูลเพื่อลบแถวตารางว่าง และดำเนินการผสานจดหมายด้วยข้อมูล หลังจากการผสาน แถวตารางว่างทั้งหมดจะถูกลบออกจากเอกสาร

## บทสรุป

ในบทช่วยสอนนี้ คุณจะได้เรียนรู้วิธีใช้ตัวเลือกการล้างข้อมูลใน Aspose.Words สำหรับ Java เพื่อจัดการและล้างข้อมูลเอกสารระหว่างกระบวนการผสานจดหมาย ตัวเลือกเหล่านี้ให้การควบคุมแบบละเอียดสำหรับการล้างข้อมูลเอกสาร ช่วยให้คุณสร้างเอกสารที่สวยงามและปรับแต่งได้อย่างง่ายดาย

## คำถามที่พบบ่อย

### ตัวเลือกการล้างข้อมูลใน Aspose.Words สำหรับ Java คืออะไร

ตัวเลือกการล้างข้อมูลใน Aspose.Words สำหรับ Java คือการตั้งค่าที่ให้คุณควบคุมด้านต่างๆ ของการล้างข้อมูลเอกสารระหว่างกระบวนการผสานจดหมาย ตัวเลือกเหล่านี้ช่วยให้คุณลบองค์ประกอบที่ไม่จำเป็น เช่น ย่อหน้าที่ว่างเปล่า ส่วนที่ไม่ได้ใช้ และอื่นๆ เพื่อให้แน่ใจว่าเอกสารขั้นสุดท้ายของคุณมีโครงสร้างที่ดีและสวยงาม

### ฉันจะลบย่อหน้าว่างออกจากเอกสารได้อย่างไร

หากต้องการลบย่อหน้าว่างออกจากเอกสารของคุณโดยใช้ Aspose.Words สำหรับ Java คุณสามารถตั้งค่าได้ `MailMergeCleanupOptions.REMOVE_EMPTY_PARAGRAPHS` ตัวเลือกเป็นจริง การดำเนินการนี้จะลบย่อหน้าที่ไม่มีเนื้อหาโดยอัตโนมัติ ส่งผลให้เอกสารสะอาดขึ้น

### จุดประสงค์ของการ `REMOVE_UNUSED_REGIONS` ตัวเลือกการทำความสะอาด?

การ `MailMergeCleanupOptions.REMOVE_UNUSED_REGIONS` ตัวเลือกนี้ใช้เพื่อลบพื้นที่ในเอกสารที่ไม่มีข้อมูลที่สอดคล้องกันในระหว่างกระบวนการผสานจดหมาย ซึ่งช่วยให้เอกสารของคุณเป็นระเบียบเรียบร้อยโดยกำจัดพื้นที่ว่างที่ไม่ได้ใช้

### ฉันสามารถลบแถวตารางว่างออกจากเอกสารโดยใช้ Aspose.Words สำหรับ Java ได้หรือไม่

ใช่ คุณสามารถลบแถวตารางว่างออกจากเอกสารได้โดยตั้งค่า `MailMergeCleanupOptions.REMOVE_EMPTY_TABLE_ROWS` ตัวเลือกการล้างข้อมูลเป็นจริง การดำเนินการนี้จะลบแถวตารางใดๆ ที่ไม่มีข้อมูลโดยอัตโนมัติ ทำให้มั่นใจได้ว่าตารางในเอกสารของคุณจะมีโครงสร้างที่ดี

### จะเกิดอะไรขึ้นเมื่อฉันตั้งค่า `REMOVE_CONTAINING_FIELDS` ตัวเลือก?

การตั้งค่า `MailMergeCleanupOptions.REMOVE_CONTAINING_FIELDS` ตัวเลือกนี้จะลบฟิลด์ผสานทั้งหมด รวมถึงย่อหน้าที่มีฟิลด์ผสานนั้นออกจากเอกสารระหว่างกระบวนการผสานจดหมาย ตัวเลือกนี้มีประโยชน์เมื่อคุณต้องการลบฟิลด์ผสานและข้อความที่เกี่ยวข้อง

### ฉันจะลบเขตข้อมูลผสานที่ไม่ได้ใช้จากเอกสารของฉันได้อย่างไร

หากต้องการลบเขตข้อมูลผสานที่ไม่ได้ใช้จากเอกสาร คุณสามารถตั้งค่า `MailMergeCleanupOptions.REMOVE_UNUSED_FIELDS` ตัวเลือกเป็นจริง การดำเนินการนี้จะลบฟิลด์ผสานที่ไม่ได้ถูกเติมระหว่างการผสานจดหมายโดยอัตโนมัติ ส่งผลให้เอกสารสะอาดขึ้น

### ความแตกต่างระหว่าง `REMOVE_EMPTY_FIELDS` และ `REMOVE_UNUSED_FIELDS` ตัวเลือกการทำความสะอาด?

การ `REMOVE_EMPTY_FIELDS` ตัวเลือกนี้จะลบเขตข้อมูลผสานที่ไม่มีข้อมูลหรือว่างเปล่าระหว่างกระบวนการผสานจดหมาย ในทางกลับกัน `REMOVE_UNUSED_FIELDS` ตัวเลือกนี้จะลบฟิลด์ผสานที่ไม่ถูกเติมด้วยข้อมูลระหว่างการผสาน การเลือกระหว่างฟิลด์เหล่านี้ขึ้นอยู่กับว่าคุณต้องการลบฟิลด์ที่ไม่มีเนื้อหาหรือฟิลด์ที่ไม่ได้ใช้ในระหว่างการผสานโดยเฉพาะ

### ฉันสามารถเปิดใช้งานการลบย่อหน้าพร้อมเครื่องหมายวรรคตอนได้อย่างไร

หากต้องการเปิดใช้งานการลบย่อหน้าที่มีเครื่องหมายวรรคตอน คุณสามารถตั้งค่า `cleanupParagraphsWithPunctuationMarks` ตัวเลือกเป็นจริงและระบุเครื่องหมายวรรคตอนที่จะนำมาพิจารณาในการล้างข้อมูล วิธีนี้ช่วยให้คุณสร้างเอกสารที่ละเอียดขึ้นโดยลบย่อหน้าที่มีแต่เครื่องหมายวรรคตอนที่ไม่จำเป็นออกไป

### ฉันสามารถปรับแต่งตัวเลือกการล้างข้อมูลใน Aspose.Words สำหรับ Java ได้หรือไม่

ใช่ คุณสามารถปรับแต่งตัวเลือกการล้างข้อมูลตามความต้องการเฉพาะของคุณได้ คุณสามารถเลือกตัวเลือกการล้างข้อมูลที่จะใช้และกำหนดค่าให้สอดคล้องกับข้อกำหนดการล้างข้อมูลเอกสารของคุณ เพื่อให้แน่ใจว่าเอกสารขั้นสุดท้ายของคุณตรงตามมาตรฐานที่คุณต้องการ


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}