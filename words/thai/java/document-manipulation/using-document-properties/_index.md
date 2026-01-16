---
date: 2026-01-16
description: เรียนรู้วิธีแปลงนิ้วเป็นพอยต์, อ่านเมตาดาต้าเอกสารด้วย Java, เพิ่มคุณสมบัติเฉพาะด้วย
  Java, และตั้งค่าขอบหน้ากระดาษด้วย Java ด้วย Aspose.Words for Java.
linktitle: Using Document Properties
second_title: Aspose.Words Java Document Processing API
title: แปลงนิ้วเป็นพอยต์ – ใช้คุณสมบัติของเอกสารใน Aspose.Words สำหรับ Java
url: /th/java/document-manipulation/using-document-properties/
weight: 32
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# แปลงนิ้วเป็นพอยต์ – การใช้คุณสมบัติเอกสารใน Aspose.Words for Java

ในบทแนะนำนี้คุณจะได้เรียนรู้วิธี **แปลงนิ้วเป็นพอยต์** เมื่อกำหนดขอบกระดาษ, อ่านเมตาดาต้าเอกสารด้วย Java, เพิ่มคุณสมบัติแบบกำหนดเองด้วย Java, และทำงานกับคุณสมบัติเอกสารที่มีมาในตัวโดยใช้ Aspose.Words for Java. ไม่ว่าคุณจะสร้างรายงาน, ใบแจ้งหนี้, หรือเอกสารทางกฎหมาย, การเชี่ยวชาญเทคนิคเหล่านี้จะทำให้คุณควบคุมลักษณะการแสดงผลและเมตาดาต้าของไฟล์ Word ได้อย่างละเอียด.

## คำตอบอย่างรวดเร็ว
- **วิธีแปลงนิ้วเป็นพอยต์?** ใช้ `ConvertUtil.inchToPoint(value)` จาก Aspose.Words.
- **ฉันสามารถอ่านเมตาดาต้าเอกสารใน Java ได้หรือไม่?** ใช่ – เรียก `doc.getBuiltInDocumentProperties()` หรือ `doc.getCustomDocumentProperties()`.
- **วิธีเพิ่มคุณสมบัติแบบกำหนดเองใน Java?** ใช้ `doc.getCustomDocumentProperties().add(name, value)`.
- **เมธอดใดที่ตั้งค่าขอบกระดาษเป็นพอยต์?** `PageSetup.setTopMargin`, `setBottomMargin` เป็นต้น, รับค่าพอยต์.
- **การลิงก์ไปยังบุ๊กมาร์คได้รับการสนับสนุนหรือไม่?** ใช่ – ใช้ `addLinkToContent` บนคอลเลกชันคุณสมบัติแบบกำหนดเอง.

## แนะนำคุณสมบัติเอกสาร
คุณสมบัติเอกสารเป็นส่วนสำคัญของไฟล์ Word ใด ๆ. พวกมันเก็บข้อมูลเช่น ชื่อเรื่อง, ผู้เขียน, หัวข้อ, คำสำคัญ, และเมตาดาต้าแบบกำหนดเองใด ๆ ที่คุณต้องการสำหรับการประมวลผลต่อไป. ใน Aspose.Words for Java คุณสามารถจัดการคุณสมบัติเอกสารที่มีมาในตัวและแบบกำหนดเอง, และคุณยังสามารถควบคุมรายละเอียดการจัดวางเช่นขอบกระดาษโดยการแปลงหน่วยการวัด (เช่น **แปลงนิ้วเป็นพอยต์**).

## “แปลงนิ้วเป็นพอยต์” คืออะไร?
ใน Word การวัดการจัดวางจะแสดงเป็นพอยต์ (1 พอยต์ = 1/72 นิ้ว). การแปลงนิ้วเป็นพอยต์ทำให้คุณกำหนดขอบ, ระยะเยื้อง, และการเว้นระยะโดยใช้หน่วยอิมพีเรียลที่คุ้นเคยในขณะที่ API ทำงานกับพอยต์ภายใน.

## ทำไมต้องจัดการเมตาดาต้าเอกสารใน Java?
การฝังเมตาดาต้าช่วยให้การค้นหา, การจัดประเภท, และการทำงานอัตโนมัตาง่ายขึ้น. ตัวอย่างเช่น คุณอาจแท็กสัญญาด้วยแฟล็ก “Authorized” หรือเก็บหมายเลขรุ่นสำหรับการตรวจสอบ. การอ่านและเขียนข้อมูลนี้โดยโปรแกรมทำให้มั่นใจความสอดคล้องในชุดเอกสารจำนวนมาก.

## ข้อกำหนดเบื้องต้น
- Java 17+ (หรือ JDK ที่เข้ากันได้)
- ไลบรารี Aspose.Words for Java ที่เพิ่มในโปรเจกต์ของคุณ (Maven/Gradle)
- ไฟล์ตัวอย่าง `.docx` (เช่น `Properties.docx`) ที่วางไว้ในไดเรกทอรีที่เข้าถึงได้

## คู่มือขั้นตอนโดยละเอียด

### การแสดงรายการคุณสมบัติเอกสารที่มีมาในตัว
ด้านล่างเป็นการทดสอบง่ายที่เปิดเอกสารและพิมพ์คุณสมบัติที่มีมาในตัวทั้งหมด เช่น ชื่อเรื่อง, ผู้เขียน, และคำสำคัญ.

```java
@Test
public void enumerateProperties() throws Exception
{
    Document doc = new Document("Your Directory Path" + "Properties.docx");
    System.out.println(MessageFormat.format("1. Document name: {0}", doc.getOriginalFileName()));
    System.out.println("2. Built-in Properties");
    for (DocumentProperty prop : doc.getBuiltInDocumentProperties())
        System.out.println(MessageFormat.format("{0} : {1}", prop.getName(), prop.getValue()));
}
```

> **เคล็ดลับ:** ใช้สคริปต์นี้เพื่อยืนยันว่าเมตาดาต้าของคุณถูกเขียนอย่างถูกต้องในขั้นตอนก่อนหน้า.

### การเพิ่มคุณสมบัติเอกสารแบบกำหนดเอง (add custom properties java)
คุณสมบัติแบบกำหนดเองทำให้คุณเก็บข้อมูลประเภทใดก็ได้ที่ต้องการ—boolean, string, date, number ฯลฯ.

```java
@Test
public void addCustomDocumentProperties() throws Exception
{
    Document doc = new Document("Your Directory Path" + "Properties.docx");
    CustomDocumentProperties customDocumentProperties = doc.getCustomDocumentProperties();

    if (customDocumentProperties.get("Authorized") != null) return;

    customDocumentProperties.add("Authorized", true);
    customDocumentProperties.add("Authorized By", "John Smith");
    customDocumentProperties.add("Authorized Date", new Date());
    customDocumentProperties.add("Authorized Revision", doc.getBuiltInDocumentProperties().getRevisionNumber());
    customDocumentProperties.add("Authorized Amount", 123.45);
}
```

> **เหตุผลที่สำคัญ:** การเพิ่มแฟล็กเช่น **Authorized** สามารถขับเคลื่อนกระบวนการอนุมัติต่อเนื่องโดยไม่ต้องแก้ไขเนื้อหาเอกสาร.

### การลบคุณสมบัติแบบกำหนดเอง
หากคุณสมบัติเชื่อมต่อไม่จำเป็นแล้ว, คุณสามารถลบออกได้อย่างสะอาด.

```java
@Test
public void removeCustomDocumentProperties() throws Exception
{
    Document doc = new Document("Your Directory Path" + "Properties.docx");
    doc.getCustomDocumentProperties().remove("Authorized Date");
}
```

### การกำหนดลิงก์ไปยังเนื้อหา (bookmark linking)
คุณสามารถสร้างบุ๊กมาร์คและจากนั้นเพิ่มคุณสมบัติแบบกำหนดเองที่ชี้ไปยังบุ๊กมาร์คนั้น, ทำให้สามารถอ้างอิงข้ามแบบไดนามิก.

```java
@Test
public void configuringLinkToContent() throws Exception
{
    Document doc = new Document();
    DocumentBuilder builder = new DocumentBuilder(doc);
    builder.startBookmark("MyBookmark");
    builder.writeln("Text inside a bookmark.");
    builder.endBookmark("MyBookmark");

    CustomDocumentProperties customProperties = doc.getCustomDocumentProperties();

    // Add linked to content property.
    DocumentProperty customProperty = customProperties.addLinkToContent("Bookmark", "MyBookmark");
    customProperty = customProperties.get("Bookmark");
    boolean isLinkedToContent = customProperty.isLinkToContent();
    String linkSource = customProperty.getLinkSource();
    String customPropertyValue = customProperty.getValue().toString();
}
```

### การแปลงหน่วยการวัด (set page margins java)
นี่คือจุดที่คีย์เวิร์ดหลักโดดเด่น. เรากำหนดขอบในหน่วยนิ้ว, แล้ว **แปลงนิ้วเป็นพอยต์** ด้วย `ConvertUtil`.

```java
@Test
public void convertBetweenMeasurementUnits() throws Exception
{
    Document doc = new Document();
    DocumentBuilder builder = new DocumentBuilder(doc);
    PageSetup pageSetup = builder.getPageSetup();

    // Set margins in inches.
    pageSetup.setTopMargin(ConvertUtil.inchToPoint(1.0));
    pageSetup.setBottomMargin(ConvertUtil.inchToPoint(1.0));
    pageSetup.setLeftMargin(ConvertUtil.inchToPoint(1.5));
    pageSetup.setRightMargin(ConvertUtil.inchToPoint(1.5));
    pageSetup.setHeaderDistance(ConvertUtil.inchToPoint(0.2));
    pageSetup.setFooterDistance(ConvertUtil.inchToPoint(0.2));
}
```

> **หมายเหตุ:** `ConvertUtil` ยังมี `pointToInch`, `mmToPoint` ฯลฯ สำหรับการจัดการเลย์เอาต์ที่ยืดหยุ่น.

### การใช้อักขระควบคุม (read document metadata java)
อักขระควบคุมช่วยทำความสะอาดสตรีมข้อความ. ตัวอย่างนี้แทนที่ carriage‑return (`\r`) ด้วยลำดับการขึ้นบรรทัดของ Windows (`\r\n`).

```java
@Test
public void useControlCharacters()
{
    final String TEXT = "test\r";

    // Replace "\r" control character with "\r\n".
    String replace = TEXT.replace(ControlChar.CR, ControlChar.CR_LF);
}
```

## ปัญหาที่พบบ่อยและวิธีแก้

| ปัญหา | สาเหตุ | วิธีแก้ |
|-------|-------|-----|
| ขอบกระดาษดูผิดหลังการแปลง | ใช้หน่วยผิด (เช่น ซม. แทนนิ้ว) | ตรวจสอบว่าคุณเรียก `ConvertUtil.inchToPoint` สำหรับค่าหน่วยนิ้ว |
| คุณสมบัติแบบกำหนดเองไม่ปรากฏ | เพิ่มคุณสมบัติหลังจากบันทึกเอกสาร | เรียก `doc.save(...)` หลังจากเพิ่มคุณสมบัติ |
| ลิงก์บุ๊กมาร์คเสีย | ชื่อบุ๊กมาร์คพิมพ์ผิด | ตรวจสอบให้แน่ใจว่าชื่อบุ๊กมาร์คตรงกันอย่างแม่นยำใน `addLinkToContent` |

## คำถามที่พบบ่อย

### วิธีเข้าถึงคุณสมบัติเอกสารที่มีมาในตัว?
เพื่อเข้าถึงคุณสมบัติเอกสารที่มีมาในตัวใน Aspose.Words for Java, คุณสามารถใช้เมธอด `getBuiltInDocumentProperties` บนวัตถุ `Document`. เมธอดนี้จะคืนคอลเลกชันของคุณสมบัติที่มีมาในตัวที่คุณสามารถวนลูปได้.

### ฉันสามารถเพิ่มคุณสมบัติเอกสารแบบกำหนดเองให้กับเอกสารได้หรือไม่?
ได้, คุณสามารถเพิ่มคุณสมบัติเอกสารแบบกำหนดเองให้กับเอกสารโดยใช้คอลเลกชัน `CustomDocumentProperties`. คุณสามารถกำหนดคุณสมบัติแบบกำหนดเองด้วยประเภทข้อมูลต่าง ๆ รวมถึง string, boolean, date, และค่าตัวเลข.

### ฉันจะลบคุณสมบัติเอกสารแบบกำหนดเองเฉพาะได้อย่างไร?
เพื่อที่จะลบคุณสมบัติเอกสารแบบกำหนดเองเฉพาะ, คุณสามารถใช้เมธอด `remove` บนคอลเลกชัน `CustomDocumentProperties`, โดยส่งชื่อของคุณสมบัติที่ต้องการลบเป็นพารามิเตอร์.

### จุดประสงค์ของการลิงก์ไปยังเนื้อหาในเอกสารคืออะไร?
การลิงก์ไปยังเนื้อหาในเอกสารทำให้คุณสร้างการอ้างอิงแบบไดนามิกไปยังส่วนเฉพาะของเอกสาร. สิ่งนี้มีประโยชน์สำหรับการสร้างเอกสารแบบโต้ตอบหรือการอ้างอิงข้ามระหว่างส่วนต่าง ๆ.

### ฉันจะเปลี่ยนหน่วยการวัดต่าง ๆ ใน Aspose.Words for Java ได้อย่างไร?
คุณสามารถแปลงหน่วยการวัดต่าง ๆ ใน Aspose.Words for Java ได้โดยใช้คลาส `ConvertUtil`. มันมีเมธอดสำหรับแปลงหน่วยเช่น นิ้วเป็นพอยต์, พอยต์เป็นเซนติเมตร, และอื่น ๆ.

## คำถามที่พบบ่อย

**ถาม: ฉันจะอ่านเมตาดาต้าเอกสาร Java โดยไม่โหลดไฟล์ทั้งหมดได้อย่างไร?**  
**ตอบ:** ใช้ `DocumentInfo` เพื่อดึงคุณสมบัติหลักโดยไม่ต้องโหลดเนื้อหาเอกสารเต็มรูปแบบ.

**ถาม: ฉันสามารถตั้งค่าขอบกระดาษ Java แบบโปรแกรมสำหรับเอกสารที่มีอยู่ได้หรือไม่?**  
**ตอบ:** ใช่—เปิดเอกสาร, แก้ไขขอบ `PageSetup` (แปลงนิ้วเป็นพอยต์หากจำเป็น), แล้วบันทึก.

**ถาม: สามารถส่งออกคุณสมบัติแบบกำหนดเองไปยังเมตาดาต้า PDF ได้หรือไม่?**  
**ตอบ:** เมื่อบันทึกเป็น PDF, Aspose.Words จะทำการแมพคุณสมบัติเอกสารแบบกำหนดเองไปยังเมตาดาต้า PDF แบบกำหนดเองโดยอัตโนมัติ.

**ถาม: อักขระควบคุมมีผลต่อการแปลงเป็น PDF หรือไม่?**  
**ตอบ:** พวกมันจะถูกเก็บไว้ระหว่างการแปลง; อย่างไรก็ตามคุณอาจต้องทำให้การขึ้นบรรทัดเป็นมาตรฐานเพื่อความสอดคล้อง.

**ถาม: เวอร์ชันของ Aspose.Words ที่ต้องการสำหรับ `ConvertUtil` คืออะไร?**  
**ตอบ:** `ConvertUtil` มีตั้งแต่ Aspose.Words 16.5; เวอร์ชันล่าสุดใด ๆ ก็รองรับ.

## สรุป

โดยการเชี่ยวชาญ **การแปลงนิ้วเป็นพอยต์**, การอ่านเมตาดาต้าเอกสาร Java, และการเพิ่มคุณสมบัติแบบกำหนดเอง Java, คุณจะได้ควบคุมทั้งการจัดวางภาพและข้อมูลที่ซ่อนอยู่ของไฟล์ Word อย่างเต็มที่. ความสามารถเหล่านี้ทำให้คุณสร้างระบบอัตโนมัติการจัดการเอกสาร, บังคับใช้การปฏิบัติตาม, และสร้างรายงานที่มีการจัดรูปแบบอย่างละเอียด—all with Aspose.Words for Java.

---

**อัปเดตล่าสุด:** 2026-01-16  
**ทดสอบด้วย:** Aspose.Words for Java 24.11  
**ผู้เขียน:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}