---
"description": "เรียนรู้การใช้ Aspose.Words เพื่อแก้ไข Java อย่างมีประสิทธิภาพ คำแนะนำทีละขั้นตอนสำหรับนักพัฒนา เพิ่มประสิทธิภาพการจัดการเอกสารของคุณ"
"linktitle": "การใช้การแก้ไข"
"second_title": "API การประมวลผลเอกสาร Java ของ Aspose.Words"
"title": "การใช้การแก้ไขใน Aspose.Words สำหรับ Java"
"url": "/th/java/using-document-elements/using-revisions/"
"weight": 22
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# การใช้การแก้ไขใน Aspose.Words สำหรับ Java


หากคุณเป็นนักพัฒนา Java ที่ต้องการทำงานกับเอกสารและจำเป็นต้องนำการควบคุมการแก้ไขมาใช้ Aspose.Words for Java มีชุดเครื่องมืออันทรงพลังที่จะช่วยให้คุณจัดการการแก้ไขได้อย่างมีประสิทธิภาพ ในบทช่วยสอนนี้ เราจะแนะนำคุณเกี่ยวกับการใช้การแก้ไขใน Aspose.Words for Java ทีละขั้นตอน 

## 1. บทนำสู่ Aspose.Words สำหรับ Java

Aspose.Words สำหรับ Java เป็น Java API ที่มีประสิทธิภาพซึ่งช่วยให้คุณสร้าง แก้ไข และจัดการเอกสาร Word ได้โดยไม่ต้องใช้ Microsoft Word มีประโยชน์อย่างยิ่งเมื่อคุณจำเป็นต้องแก้ไขเอกสารของคุณ

## 2. การตั้งค่าสภาพแวดล้อมการพัฒนาของคุณ

ก่อนที่เราจะลงลึกถึงการใช้ Aspose.Words สำหรับ Java คุณต้องตั้งค่าสภาพแวดล้อมการพัฒนาของคุณก่อน ตรวจสอบให้แน่ใจว่าคุณมีเครื่องมือพัฒนา Java ที่จำเป็นและติดตั้งไลบรารี Aspose.Words สำหรับ Java แล้ว

## 3. การสร้างเอกสารใหม่

เริ่มต้นด้วยการสร้างเอกสาร Word ใหม่โดยใช้ Aspose.Words สำหรับ Java คุณสามารถทำได้ดังนี้:

```java
string outPath = "Your Output Directory";
Document doc = new Document();
Body body = doc.getFirstSection().getBody();
Paragraph para = body.getFirstParagraph();
```

## 4. การเพิ่มเนื้อหาลงในเอกสาร

ตอนนี้คุณมีเอกสารเปล่าแล้ว คุณสามารถเพิ่มเนื้อหาลงไปได้ ในตัวอย่างนี้ เราจะเพิ่มย่อหน้าสามย่อหน้า:

```java
para.appendChild(new Run(doc, "Paragraph 1. "));
body.appendParagraph("Paragraph 2. ");
body.appendParagraph("Paragraph 3. ");
```

## 5. การเริ่มต้นการติดตามการแก้ไข

หากต้องการติดตามการแก้ไขในเอกสารของคุณ คุณสามารถใช้โค้ดดังต่อไปนี้:

```java
doc.startTrackRevisions("John Doe", new Date());
```

## 6. การแก้ไข

มาแก้ไขกันโดยเพิ่มย่อหน้าอีกย่อหน้าหนึ่ง:

```java
para = body.appendParagraph("Paragraph 4. ");
```

## 7. การยอมรับและการปฏิเสธการแก้ไข

คุณสามารถยอมรับหรือปฏิเสธการแก้ไขในเอกสารของคุณได้โดยใช้ Aspose.Words สำหรับ Java การแก้ไขสามารถจัดการได้อย่างง่ายดายใน Microsoft Word หลังจากสร้างเอกสารแล้ว

## 8. การหยุดการติดตามการแก้ไข

หากต้องการหยุดการติดตามการแก้ไข ให้ใช้โค้ดดังต่อไปนี้:

```java
doc.stopTrackRevisions();
```

## 9. การบันทึกเอกสาร

สุดท้ายให้บันทึกเอกสารของคุณ:

```java
doc.save(outPath + "WorkingWithRevisions.AcceptRevisions.docx");
```

## 10. บทสรุป

ในบทช่วยสอนนี้ เราได้กล่าวถึงหลักพื้นฐานของการใช้การแก้ไขใน Aspose.Words สำหรับ Java แล้ว คุณได้เรียนรู้วิธีการสร้างเอกสาร เพิ่มเนื้อหา เริ่มและหยุดการติดตามการแก้ไข และบันทึกเอกสารของคุณแล้ว

ตอนนี้คุณมีเครื่องมือที่จำเป็นในการจัดการการแก้ไขในแอปพลิเคชัน Java ของคุณอย่างมีประสิทธิภาพโดยใช้ Aspose.Words สำหรับ Java

## ซอร์สโค้ดที่สมบูรณ์
```java
string outPath = "Your Output Directory";
Document doc = new Document();
Body body = doc.getFirstSection().getBody();
Paragraph para = body.getFirstParagraph();
// เพิ่มข้อความในย่อหน้าแรก จากนั้นเพิ่มอีกสองย่อหน้า
para.appendChild(new Run(doc, "Paragraph 1. "));
body.appendParagraph("Paragraph 2. ");
body.appendParagraph("Paragraph 3. ");
// เรามีสามย่อหน้าซึ่งไม่มีย่อหน้าที่ลงทะเบียนเป็นการแก้ไขประเภทใด ๆ
// หากเราเพิ่ม/ลบเนื้อหาใดๆ ในเอกสารขณะติดตามการแก้ไข
// จะแสดงไว้ในเอกสารและสามารถยอมรับหรือปฏิเสธได้
doc.startTrackRevisions("John Doe", new Date());
// ย่อหน้านี้เป็นการแก้ไขและจะมีการตั้งค่าสถานะ "IsInsertRevision" ตามนั้น
para = body.appendParagraph("Paragraph 4. ");
Assert.assertTrue(para.isInsertRevision());
// รับคอลเลกชันย่อหน้าของเอกสารและลบย่อหน้า
ParagraphCollection paragraphs = body.getParagraphs();
Assert.assertEquals(4, paragraphs.getCount());
para = paragraphs.get(2);
para.remove();
// เนื่องจากเรากำลังติดตามการแก้ไข ย่อหน้ายังคงอยู่ในเอกสาร และจะมีการตั้งค่าเป็น "IsDeleteRevision"
// และจะแสดงเป็นการแก้ไขใน Microsoft Word จนกว่าเราจะยอมรับหรือปฏิเสธการแก้ไขทั้งหมด
Assert.assertEquals(4, paragraphs.getCount());
Assert.assertTrue(para.isDeleteRevision());
// ย่อหน้าการลบแก้ไขจะถูกลบออกเมื่อเรายอมรับการเปลี่ยนแปลง
doc.acceptAllRevisions();
Assert.assertEquals(3, paragraphs.getCount());
Assert.assertEquals(para.getRuns().getCount(), 0); //คือว่างเปล่า
// การหยุดการติดตามการแก้ไขจะทำให้ข้อความนี้ปรากฏเป็นข้อความปกติ
// การแก้ไขจะไม่นับเมื่อเอกสารมีการเปลี่ยนแปลง
doc.stopTrackRevisions();
// บันทึกเอกสาร
doc.save(outPath + "WorkingWithRevisions.AcceptRevisions.docx");
  
```

## คำถามที่พบบ่อย

### 1. ฉันสามารถใช้ Aspose.Words สำหรับ Java ร่วมกับภาษาการเขียนโปรแกรมอื่น ๆ ได้หรือไม่

ไม่ Aspose.Words สำหรับ Java ได้รับการออกแบบมาโดยเฉพาะสำหรับการพัฒนา Java

### 2. Aspose.Words สำหรับ Java สามารถใช้งานร่วมกับ Microsoft Word ทุกเวอร์ชันได้หรือไม่

ใช่ Aspose.Words สำหรับ Java ได้รับการออกแบบมาให้เข้ากันได้กับ Microsoft Word เวอร์ชันต่างๆ

### 3. ฉันสามารถติดตามการแก้ไขในเอกสาร Word ที่มีอยู่ได้หรือไม่

ใช่ คุณสามารถใช้ Aspose.Words สำหรับ Java เพื่อติดตามการแก้ไขในเอกสาร Word ที่มีอยู่ได้

### 4. มีข้อกำหนดการออกใบอนุญาตสำหรับการใช้ Aspose.Words สำหรับ Java หรือไม่

ใช่ คุณจะต้องได้รับใบอนุญาตเพื่อใช้ Aspose.Words สำหรับ Java ในโปรเจ็กต์ของคุณ คุณสามารถ [รับสิทธิ์เข้าถึงใบอนุญาตได้ที่นี่](https://purchase-aspose.com/buy).

### 5. ฉันสามารถค้นหาการสนับสนุนสำหรับ Aspose.Words สำหรับ Java ได้ที่ไหน

หากมีคำถามหรือปัญหาใดๆ คุณสามารถเยี่ยมชมได้ที่ [ฟอรัมสนับสนุน Aspose.Words สำหรับ Java](https://forum-aspose.com/).

เริ่มต้นใช้งาน Aspose.Words สำหรับ Java วันนี้ และปรับปรุงกระบวนการจัดการเอกสารของคุณให้มีประสิทธิภาพ



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}