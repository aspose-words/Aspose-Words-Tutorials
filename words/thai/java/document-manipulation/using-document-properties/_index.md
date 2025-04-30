---
"description": "เพิ่มประสิทธิภาพการจัดการเอกสารด้วย Aspose.Words สำหรับ Java เรียนรู้การใช้งานคุณสมบัติของเอกสาร เพิ่มข้อมูลเมตาแบบกำหนดเอง และอื่นๆ อีกมากมายในบทช่วยสอนที่ครอบคลุมนี้"
"linktitle": "การใช้คุณสมบัติของเอกสาร"
"second_title": "API การประมวลผลเอกสาร Java ของ Aspose.Words"
"title": "การใช้คุณสมบัติเอกสารใน Aspose.Words สำหรับ Java"
"url": "/th/java/document-manipulation/using-document-properties/"
"weight": 32
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# การใช้คุณสมบัติเอกสารใน Aspose.Words สำหรับ Java


## บทนำเกี่ยวกับคุณสมบัติของเอกสาร

คุณสมบัติเอกสารเป็นส่วนสำคัญของเอกสารใดๆ ก็ตาม คุณสมบัติเหล่านี้ให้ข้อมูลเพิ่มเติมเกี่ยวกับเอกสารนั้นเอง เช่น ชื่อ ผู้แต่ง หัวเรื่อง คำสำคัญ และอื่นๆ ใน Aspose.Words สำหรับ Java คุณสามารถจัดการคุณสมบัติเอกสารทั้งแบบในตัวและแบบกำหนดเองได้

## การนับคุณสมบัติของเอกสาร

### คุณสมบัติในตัว

ในการดึงข้อมูลและทำงานกับคุณสมบัติเอกสารในตัว คุณสามารถใช้ชิ้นส่วนโค้ดดังต่อไปนี้:

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

โค้ดนี้จะแสดงชื่อเอกสารและคุณสมบัติในตัว รวมถึงคุณสมบัติเช่น "ชื่อเรื่อง" "ผู้เขียน" และ "คำสำคัญ"

### คุณสมบัติที่กำหนดเอง

ในการทำงานกับคุณสมบัติเอกสารที่กำหนดเอง คุณสามารถใช้ชิ้นส่วนโค้ดดังต่อไปนี้:

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

ตัวอย่างโค้ดนี้สาธิตวิธีการเพิ่มคุณสมบัติเอกสารแบบกำหนดเอง รวมถึงค่าบูลีน สตริง วันที่ หมายเลขการแก้ไข และค่าตัวเลข

## การลบคุณสมบัติเอกสาร

หากต้องการลบคุณสมบัติเอกสารเฉพาะ คุณสามารถใช้โค้ดดังต่อไปนี้:

```java
@Test
public void removeCustomDocumentProperties() throws Exception
{
    Document doc = new Document("Your Directory Path" + "Properties.docx");
    doc.getCustomDocumentProperties().remove("Authorized Date");
}
```

รหัสนี้จะลบคุณสมบัติที่กำหนดเอง "วันที่ได้รับอนุญาต" ออกจากเอกสาร

## การกำหนดค่าการเชื่อมโยงไปยังเนื้อหา

ในบางกรณี คุณอาจต้องการสร้างลิงก์ภายในเอกสารของคุณ โดยคุณสามารถทำได้ดังนี้:

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

    // เพิ่มคุณสมบัติที่เชื่อมโยงกับเนื้อหา
    DocumentProperty customProperty = customProperties.addLinkToContent("Bookmark", "MyBookmark");
    customProperty = customProperties.get("Bookmark");
    boolean isLinkedToContent = customProperty.isLinkToContent();
    String linkSource = customProperty.getLinkSource();
    String customPropertyValue = customProperty.getValue().toString();
}
```

ตัวอย่างโค้ดนี้สาธิตวิธีการสร้างบุ๊กมาร์กในเอกสารของคุณ และเพิ่มคุณสมบัติเอกสารแบบกำหนดเองที่ลิงก์ไปยังบุ๊กมาร์กนั้น

## การแปลงระหว่างหน่วยการวัด

ใน Aspose.Words สำหรับ Java คุณสามารถแปลงหน่วยการวัดได้อย่างง่ายดาย นี่คือตัวอย่างวิธีการดำเนินการ:

```java
@Test
public void convertBetweenMeasurementUnits() throws Exception
{
    Document doc = new Document();
    DocumentBuilder builder = new DocumentBuilder(doc);
    PageSetup pageSetup = builder.getPageSetup();

    // ตั้งค่าระยะขอบเป็นนิ้ว
    pageSetup.setTopMargin(ConvertUtil.inchToPoint(1.0));
    pageSetup.setBottomMargin(ConvertUtil.inchToPoint(1.0));
    pageSetup.setLeftMargin(ConvertUtil.inchToPoint(1.5));
    pageSetup.setRightMargin(ConvertUtil.inchToPoint(1.5));
    pageSetup.setHeaderDistance(ConvertUtil.inchToPoint(0.2));
    pageSetup.setFooterDistance(ConvertUtil.inchToPoint(0.2));
}
```

โค้ดสั้นๆ นี้จะตั้งค่าระยะขอบและระยะห่างเป็นนิ้วโดยการแปลงเป็นจุด

## การใช้ตัวอักษรควบคุม

อักขระควบคุมอาจมีประโยชน์เมื่อต้องจัดการกับข้อความ ต่อไปนี้เป็นวิธีการแทนที่อักขระควบคุมในข้อความของคุณ:

```java
@Test
public void useControlCharacters()
{
    final String TEXT = "test\r";

    // เปลี่ยนอักขระควบคุม "\r" เป็น "\r\n"
    String replace = TEXT.replace(ControlChar.CR, ControlChar.CR_LF);
}
```

ในตัวอย่างนี้ เราจะแทนที่คำสั่งส่งกลับรถ (`\r`) โดยมีการส่งกลับรถตามด้วยฟีดข้อมูลบรรทัด (`\r\n`-

## บทสรุป

คุณสมบัติเอกสารมีบทบาทสำคัญในการจัดการและจัดระเบียบเอกสารของคุณอย่างมีประสิทธิภาพใน Aspose.Words สำหรับ Java ไม่ว่าจะใช้งานกับคุณสมบัติในตัว คุณสมบัติที่กำหนดเอง หรือการใช้ตัวควบคุม คุณก็มีเครื่องมือต่างๆ มากมายที่จะช่วยเสริมความสามารถในการจัดการเอกสารของคุณ

## คำถามที่พบบ่อย

### ฉันจะเข้าถึงคุณสมบัติเอกสารในตัวได้อย่างไร

หากต้องการเข้าถึงคุณสมบัติเอกสารในตัวใน Aspose.Words สำหรับ Java คุณสามารถใช้ `getBuiltInDocumentProperties` วิธีการบน `Document` วัตถุ วิธีการนี้ส่งคืนคอลเลกชันของคุณสมบัติในตัวที่คุณสามารถวนซ้ำได้

### ฉันสามารถเพิ่มคุณสมบัติเอกสารแบบกำหนดเองลงในเอกสารได้หรือไม่

ใช่ คุณสามารถเพิ่มคุณสมบัติเอกสารที่กำหนดเองลงในเอกสารได้โดยใช้ `CustomDocumentProperties` คอลเลกชัน คุณสามารถกำหนดคุณสมบัติที่กำหนดเองได้ด้วยประเภทข้อมูลต่าง ๆ รวมถึงสตริง บูลีน วันที่ และค่าตัวเลข

### ฉันจะลบคุณสมบัติเอกสารที่กำหนดเองที่เจาะจงได้อย่างไร

หากต้องการลบคุณสมบัติเอกสารที่กำหนดเองโดยเฉพาะ คุณสามารถใช้ `remove` วิธีการบน `CustomDocumentProperties` คอลเลกชันโดยส่งชื่อของคุณสมบัติที่คุณต้องการลบเป็นพารามิเตอร์

### จุดประสงค์ของการลิงก์ไปยังเนื้อหาภายในเอกสารคืออะไร

การลิงก์ไปยังเนื้อหาภายในเอกสารช่วยให้คุณสร้างการอ้างอิงแบบไดนามิกไปยังส่วนต่างๆ ของเอกสารได้ ซึ่งอาจมีประโยชน์ในการสร้างเอกสารแบบโต้ตอบหรือการอ้างอิงแบบไขว้ระหว่างส่วนต่างๆ

### ฉันจะแปลงหน่วยการวัดต่างๆ ใน Aspose.Words สำหรับ Java ได้อย่างไร

คุณสามารถแปลงระหว่างหน่วยการวัดที่แตกต่างกันใน Aspose.Words สำหรับ Java ได้โดยใช้ `ConvertUtil` คลาสนี้มีวิธีการในการแปลงหน่วย เช่น นิ้วเป็นจุด จุดเป็นเซนติเมตร และอื่นๆ อีกมากมาย


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}