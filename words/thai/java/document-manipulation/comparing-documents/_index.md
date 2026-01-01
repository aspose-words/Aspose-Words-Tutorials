---
date: 2026-01-01
description: เรียนรู้วิธีเปรียบเทียบไฟล์ Word สองไฟล์โดยใช้ Aspose.Words for Java
  ซึ่งเป็นไลบรารี Java ที่ทรงพลังสำหรับการวิเคราะห์เอกสารและการควบคุมเวอร์ชัน
linktitle: Comparing Documents
second_title: Aspose.Words Java Document Processing API
title: วิธีเปรียบเทียบไฟล์ Word สองไฟล์ด้วย Aspose.Words สำหรับ Java
url: /th/java/document-manipulation/comparing-documents/
weight: 28
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# วิธีเปรียบเทียบไฟล์ Word สองไฟล์ด้วย Aspose.Words for Java

## บทนำการเปรียบเทียบเอกสาร

การเปรียบเทียบเอกสารหมายถึงการวิเคราะห์สองเอกสารและระบุความแตกต่าง ซึ่งอาจเป็นสิ่งสำคัญในหลายสถานการณ์ เช่น กฎหมาย, กฎระเบียบ, หรือการจัดการเนื้อหา **Aspose.Words for Java** ทำให้การเปรียบเทียบไฟล์ Word สองไฟล์เป็นเรื่องง่ายและให้มุมมองที่ชัดเจนว่ามีการเปลี่ยนแปลงอะไรบ้างระหว่างเวอร์ชัน

## คำตอบสั้น
- **เมธอด compare คืนค่าอะไร?** คอลเลกชันของ revision ที่แสดงถึงความแตกต่าง  
- **ฉันสามารถละเว้นการเปลี่ยนแปลงรูปแบบได้หรือไม่?** ได้, ใช้ `CompareOptions.setIgnoreFormatting(true)`  
- **สามารถเปรียบเทียบเฉพาะข้อความหลักได้หรือไม่?** ตั้งค่า `setIgnoreHeadersAndFooters(true)` เพื่อข้ามส่วนหัว/ส่วนท้าย  
- **ต้องใช้ Java เวอร์ชันใด?** รองรับ Java 8 ขึ้นไปทั้งหมด  
- **ต้องมีลิขสิทธิ์สำหรับการใช้งานในผลิตภัณฑ์หรือไม่?** ต้องมีลิขสิทธิ์ Aspose.Words for Java ที่ถูกต้องสำหรับโครงการเชิงพาณิชย์

## การตั้งค่าสภาพแวดล้อมของคุณ

ก่อนที่เราจะลงลึกไปในการเปรียบเทียบเอกสาร, โปรดตรวจสอบว่าคุณได้ติดตั้ง Aspose.Words for Java แล้ว คุณสามารถดาวน์โหลดไลบรารีได้จากหน้า [Aspose.Words for Java releases](https://releases.aspose.com/words/java/) หลังจากดาวน์โหลดแล้วให้เพิ่มเข้าไปในโปรเจกต์ Java ของคุณ

## การเปรียบเทียบพื้นฐานของไฟล์ Word สองไฟล์

มาเริ่มต้นด้วยพื้นฐานของการเปรียบเทียบไฟล์ Word สองไฟล์กัน เราจะใช้เอกสารสองไฟล์คือ `docA` และ `docB` แล้วทำการเปรียบเทียบ

```java
Document docA = new Document("Your Directory Path" + "Document.docx");
Document docB = docA.deepClone();
docA.compare(docB, "user", new Date());
System.out.println(docA.getRevisions().getCount() == 0 ? "Documents are equal" : "Documents are not equal");
```

ในโค้ดส่วนนี้เราจะโหลดไฟล์เดียวกันสองครั้ง, ทำการคล cloning, แล้วเรียก `compare` เมธอดจะสร้างเครื่องหมาย revision ที่บ่งบอกถึงความแตกต่างใด ๆ ระหว่างไฟล์ Word สองไฟล์

## การปรับแต่งการเปรียบเทียบด้วยตัวเลือก

Aspose.Words for Java มีตัวเลือกมากมายสำหรับการปรับแต่งการเปรียบเทียบเอกสาร เรามาดูบางส่วนกัน

### วิธีละเว้นรูปแบบเมื่อคุณเปรียบเทียบไฟล์ Word สองไฟล์

เพื่อละเว้นความแตกต่างของรูปแบบ, ใช้ตัวเลือก `setIgnoreFormatting`

```java
CompareOptions options = new CompareOptions();
options.setIgnoreFormatting(true);
docA.compare(docB, "user", new Date(), options);
```

### วิธียกเว้นส่วนหัวและส่วนท้ายขณะเปรียบเทียบไฟล์ Word สองไฟล์

เพื่อยกเว้นส่วนหัวและส่วนท้ายจากการเปรียบเทียบ, ตั้งค่า `setIgnoreHeadersAndFooters`

```java
CompareOptions options = new CompareOptions();
options.setIgnoreHeadersAndFooters(true);
docA.compare(docB, "user", new Date(), options);
```

### วิธีละเว้นองค์ประกอบเฉพาะเมื่อเปรียบเทียบไฟล์ Word สองไฟล์

คุณสามารถละเว้นองค์ประกอบต่าง ๆ เช่น ตาราง, ฟิลด์, คอมเมนต์, กล่องข้อความ ฯลฯ ได้โดยใช้ตัวเลือกที่กำหนด

```java
CompareOptions options = new CompareOptions();
options.setIgnoreTables(true);
options.setIgnoreFields(true);
options.setIgnoreComments(true);
options.setIgnoreTextboxes(true);
docA.compare(docB, "user", new Date(), options);
```

### วิธีตั้งค่าเป้าหมายการเปรียบเทียบสำหรับไฟล์ Word สองไฟล์

ในบางกรณีคุณอาจต้องการระบุเป้าหมายการเปรียบเทียบ, คล้ายกับตัวเลือก “Show changes in” ของ Microsoft Word

```java
CompareOptions options = new CompareOptions();
options.setIgnoreFormatting(true);
options.setTarget(ComparisonTargetType.NEW);
docA.compare(docB, "user", new Date(), options);
```

### วิธีควบคุมความละเอียดของการเปรียบเทียบไฟล์ Word สองไฟล์

คุณสามารถควบคุมความละเอียดของการเปรียบเทียบได้ ตั้งแต่ระดับอักขระจนถึงระดับคำ

```java
DocumentBuilder builderA = new DocumentBuilder(new Document());
DocumentBuilder builderB = new DocumentBuilder(new Document());
builderA.writeln("This is A simple word");
builderB.writeln("This is B simple words");
CompareOptions compareOptions = new CompareOptions();
compareOptions.setGranularity(Granularity.CHAR_LEVEL);
builderA.getDocument().compare(builderB.getDocument(), "author", new Date(), compareOptions);
```

## กรณีการใช้งานทั่วไปสำหรับการเปรียบเทียบไฟล์ Word สองไฟล์

- **การตรวจสอบสัญญากฎหมาย:** ตรวจจับข้อกำหนดที่เพิ่ม, ลบ, หรือแก้ไขได้อย่างรวดเร็ว  
- **การปฏิบัติตามกฎระเบียบ:** ทำให้เอกสารนโยบายคงที่ระหว่างการแก้ไขหลายครั้ง  
- **การเผยแพร่เนื้อหา:** ตรวจจับการเปลี่ยนแปลงเชิงบรรณาธิการก่อนเผยแพร่สำเนาสุดท้าย  
- **การควบคุมเวอร์ชันในระบบจัดการเอกสาร:** ทำให้การติดตามการเปลี่ยนแปลงอัตโนมัติโดยไม่ต้องตรวจสอบด้วยตนเอง  

## เคล็ดลับการแก้ไขปัญหา

- **Revision ไม่แสดง:** ตรวจสอบให้แน่ใจว่าคุณเรียก `docA.updatePageLayout()` หลังการเปรียบเทียบหากต้องการให้เลย์เอาต์ภาพอัปเดต  
- **ประสิทธิภาพกับไฟล์ขนาดใหญ่:** ใช้ `compare` กับเอกสารที่ทำการคล cloning เพื่อหลีกเลี่ยงการโหลดไฟล์เดียวกันหลายครั้ง  
- **การเปลี่ยนแปลงในตารางหายไป:** ตรวจสอบให้ `setIgnoreTables(false)` (ค่าเริ่มต้น) เพื่อให้ความแตกต่างของตารางถูกจับได้  

## สรุป

การเปรียบเทียบไฟล์ Word สองไฟล์ด้วย Aspose.Words for Java เป็นความสามารถที่ทรงพลังและสามารถนำไปใช้ในหลายสถานการณ์การประมวลผลเอกสาร ด้วยตัวเลือกการปรับแต่งที่หลากหลาย คุณสามารถปรับกระบวนการเปรียบเทียบให้ตรงกับความต้องการของคุณ ทำให้เป็นเครื่องมือที่มีคุณค่าในชุดพัฒนา Java ของคุณ

## คำถามที่พบบ่อย

### วิธีการติดตั้ง Aspose.Words for Java?

เพื่อทำการติดตั้ง Aspose.Words for Java, ดาวน์โหลดไลบรารีจากหน้า [Aspose.Words for Java releases](https://releases.aspose.com/words/java/) แล้วเพิ่มเข้าไปใน dependencies ของโปรเจกต์ Java ของคุณ

### ฉันสามารถเปรียบเทียบเอกสารที่มีรูปแบบซับซ้อนได้ด้วย Aspose.Words for Java หรือไม่?

ได้, Aspose.Words for Java มีตัวเลือกสำหรับการเปรียบเทียบเอกสารที่มีรูปแบบซับซ้อน คุณสามารถปรับแต่งการเปรียบเทียบให้ตรงกับความต้องการของคุณได้

### Aspose.Words for Java เหมาะกับระบบจัดการเอกสารหรือไม่?

แน่นอน, ฟีเจอร์การเปรียบเทียบเอกสารของ Aspose.Words for Java เหมาะอย่างยิ่งสำหรับระบบจัดการเอกสารที่ต้องการการควบคุมเวอร์ชันและการติดตามการเปลี่ยนแปลง

### มีข้อจำกัดใดในการเปรียบเทียบเอกสารใน Aspose.Words for Java หรือไม่?

แม้ว่า Aspose.Words for Java จะมีความสามารถในการเปรียบเทียบเอกสารอย่างครอบคลุม, คุณควรตรวจสอบเอกสารอ้างอิงเพื่อให้แน่ใจว่าตรงกับความต้องการเฉพาะของคุณ

### จะเข้าถึงแหล่งข้อมูลและเอกสารเพิ่มเติมสำหรับ Aspose.Words for Java ได้อย่างไร?

สำหรับแหล่งข้อมูลเพิ่มเติมและเอกสารเชิงลึกเกี่ยวกับ Aspose.Words for Java, เยี่ยมชมหน้า [Aspose.Words for Java documentation](https://reference.aspose.com/words/java/)

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}

---

**อัปเดตล่าสุด:** 2026-01-01  
**ทดสอบด้วย:** Aspose.Words for Java รุ่นเสถียรล่าสุด  
**ผู้เขียน:** Aspose  

---