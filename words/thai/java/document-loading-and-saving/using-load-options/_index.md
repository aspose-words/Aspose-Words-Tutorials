---
title: การใช้ตัวเลือกโหลดใน Aspose.Words สำหรับ Java
linktitle: การใช้ตัวเลือกโหลด
second_title: API การประมวลผลเอกสาร Java ของ Aspose.Words
description: การเรียนรู้ตัวเลือกการโหลดใน Aspose.Words สำหรับ Java ปรับแต่งการโหลดเอกสาร จัดการการเข้ารหัส แปลงรูปร่าง ตั้งค่าเวอร์ชันของ Word และอื่นๆ เพื่อการประมวลผลเอกสาร Java ที่มีประสิทธิภาพ
weight: 11
url: /th/java/document-loading-and-saving/using-load-options/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# การใช้ตัวเลือกโหลดใน Aspose.Words สำหรับ Java


## บทนำสู่การทำงานกับตัวเลือกโหลดใน Aspose.Words สำหรับ Java

ในบทช่วยสอนนี้ เราจะมาสำรวจวิธีการทำงานกับตัวเลือกการโหลดใน Aspose.Words สำหรับ Java ตัวเลือกการโหลดช่วยให้คุณปรับแต่งวิธีการโหลดและประมวลผลเอกสารได้ เราจะครอบคลุมสถานการณ์ต่างๆ เช่น การอัปเดตฟิลด์ที่ไม่ปลอดภัย การโหลดเอกสารที่เข้ารหัส การแปลงรูปร่างเป็น Office Math การตั้งค่าเวอร์ชัน MS Word การระบุโฟลเดอร์ชั่วคราว การจัดการคำเตือน และการแปลงเมตาไฟล์เป็น PNG มาเจาะลึกทีละขั้นตอนกันเลย

## อัพเดทสนามสกปรก

```java
LoadOptions loadOptions = new LoadOptions();
loadOptions.setUpdateDirtyFields(true);

Document doc = new Document("Your Directory Path" + "Dirty field.docx", loadOptions);
doc.save("Your Directory Path" + "WorkingWithLoadOptions.UpdateDirtyFields.docx");
```

 ตัวอย่างโค้ดนี้แสดงวิธีการอัปเดตฟิลด์ที่ไม่ปลอดภัยในเอกสาร`setUpdateDirtyFields(true)` วิธีนี้ใช้เพื่อให้แน่ใจว่าฟิลด์ที่สกปรกได้รับการอัปเดตในระหว่างการโหลดเอกสาร

## โหลดเอกสารที่เข้ารหัส

```java
@Test
public void loadEncryptedDocument() throws Exception {
    Document doc = new Document("Your Directory Path" + "Encrypted.docx", new LoadOptions("docPassword"));
    doc.save("Your Directory Path" + "WorkingWithLoadOptions.LoadAndSaveEncryptedOdt.odt", new OdtSaveOptions("newPassword"));
}
```

 ที่นี่เราโหลดเอกสารที่เข้ารหัสโดยใช้รหัสผ่าน`LoadOptions` ผู้สร้างยอมรับรหัสผ่านเอกสาร และคุณยังสามารถระบุรหัสผ่านใหม่ได้เมื่อบันทึกเอกสารโดยใช้`OdtSaveOptions`.

## แปลงรูปร่างเป็น Office Math

```java
LoadOptions loadOptions = new LoadOptions();
loadOptions.setConvertShapeToOfficeMath(true);

Document doc = new Document("Your Directory Path" + "Office math.docx", loadOptions);
doc.save("Your Directory Path" + "WorkingWithLoadOptions.ConvertShapeToOfficeMath.docx");
```

 โค้ดนี้สาธิตวิธีการแปลงรูปร่างเป็นวัตถุ Office Math ในระหว่างการโหลดเอกสาร`setConvertShapeToOfficeMath(true)`วิธีการนี้เปิดใช้การแปลงนี้

## ตั้งค่าเวอร์ชัน MS Word

```java
@Test
public void setMsWordVersion() throws Exception {
    LoadOptions loadOptions = new LoadOptions();
    loadOptions.setMswVersion(MsWordVersion.WORD_2010);

    Document doc = new Document("Your Directory Path" + "Document.docx", loadOptions);
    doc.save("Your Directory Path" + "WorkingWithLoadOptions.SetMsWordVersion.docx");
}
```

 คุณสามารถระบุเวอร์ชัน MS Word สำหรับการโหลดเอกสารได้ ในตัวอย่างนี้ เราตั้งค่าเวอร์ชันเป็น Microsoft Word 2010 โดยใช้`setMswVersion`.

## ใช้โฟลเดอร์ชั่วคราว

```java
@Test
public void useTempFolder() throws Exception {
    LoadOptions loadOptions = new LoadOptions();
    loadOptions.setTempFolder("Your Directory Path");

    Document doc = new Document("Your Directory Path" + "Document.docx", loadOptions);
}
```

 โดยการตั้งค่าโฟลเดอร์ชั่วคราวโดยใช้`setTempFolder`คุณสามารถควบคุมได้ว่าจะจัดเก็บไฟล์ชั่วคราวไว้ที่ไหนในระหว่างการประมวลผลเอกสาร

## คำเตือนการโทรกลับ

```java
@Test
public void warningCallback() throws Exception {
    LoadOptions loadOptions = new LoadOptions();
    loadOptions.setWarningCallback(new DocumentLoadingWarningCallback());

    Document doc = new Document("Your Directory Path" + "Document.docx", loadOptions);
}

public static class DocumentLoadingWarningCallback implements IWarningCallback {
    public void warning(WarningInfo info) {
        // จัดการคำเตือนเมื่อเกิดขึ้นในระหว่างการโหลดเอกสาร
        System.out.println(MessageFormat.format("WARNING: {0}, source: {1}", info.getWarningType(), info.getSource()));
        System.out.println(MessageFormat.format("\tDescription: {0}", info.getDescription()));
    }
}
```

โค้ดนี้สาธิตวิธีการตั้งค่าการเรียกกลับคำเตือนเพื่อจัดการคำเตือนระหว่างการโหลดเอกสาร คุณสามารถปรับแต่งพฤติกรรมของแอปพลิเคชันของคุณเมื่อเกิดคำเตือนได้

## แปลงไฟล์ Metafile เป็น PNG

```java
@Test
public void convertMetafilesToPng() throws Exception {
    LoadOptions loadOptions = new LoadOptions();
    loadOptions.setConvertMetafilesToPng(true);

    Document doc = new Document("Your Directory Path" + "WMF with image.docx", loadOptions);
}
```

 หากต้องการแปลงไฟล์เมตา (เช่น WMF) เป็นภาพ PNG ในระหว่างการโหลดเอกสาร คุณสามารถใช้`setConvertMetafilesToPng(true)` วิธี.

## โค้ดต้นฉบับที่สมบูรณ์สำหรับการทำงานกับตัวเลือกโหลดใน Aspose.Words สำหรับ Java

```java
public void updateDirtyFields() throws Exception {
	LoadOptions loadOptions = new LoadOptions();
	{
		loadOptions.setUpdateDirtyFields(true);
	}
	Document doc = new Document("Your Directory Path" + "Dirty field.docx", loadOptions);
	doc.save("Your Directory Path" + "WorkingWithLoadOptions.UpdateDirtyFields.docx");
}
@Test
public void loadEncryptedDocument() throws Exception {
	Document doc = new Document("Your Directory Path" + "Encrypted.docx", new LoadOptions("docPassword"));
	doc.save("Your Directory Path" + "WorkingWithLoadOptions.LoadAndSaveEncryptedOdt.odt", new OdtSaveOptions("newPassword"));
}
@Test
public void convertShapeToOfficeMath() throws Exception {
	LoadOptions loadOptions = new LoadOptions();
	{
		loadOptions.setConvertShapeToOfficeMath(true);
	}
	Document doc = new Document("Your Directory Path" + "Office math.docx", loadOptions);
	doc.save("Your Directory Path" + "WorkingWithLoadOptions.ConvertShapeToOfficeMath.docx");
}
@Test
public void setMsWordVersion() throws Exception {
	// สร้างวัตถุ LoadOptions ใหม่ซึ่งจะโหลดเอกสารตามข้อกำหนดของ MS Word 2019 ตามค่าเริ่มต้น
	// และเปลี่ยนเวอร์ชันโหลดเป็น Microsoft Word 2010
	LoadOptions loadOptions = new LoadOptions();
	{
		loadOptions.setMswVersion(MsWordVersion.WORD_2010);
	}
	Document doc = new Document("Your Directory Path" + "Document.docx", loadOptions);
	doc.save("Your Directory Path" + "WorkingWithLoadOptions.SetMsWordVersion.docx");
}
@Test
public void useTempFolder() throws Exception {
	LoadOptions loadOptions = new LoadOptions();
	{
		loadOptions.setTempFolder("Your Directory Path");
	}
	Document doc = new Document("Your Directory Path" + "Document.docx", loadOptions);
}
@Test
public void warningCallback() throws Exception {
	LoadOptions loadOptions = new LoadOptions();
	{
		loadOptions.setWarningCallback(new DocumentLoadingWarningCallback());
	}
	Document doc = new Document("Your Directory Path" + "Document.docx", loadOptions);
}
public static class DocumentLoadingWarningCallback implements IWarningCallback {
	public void warning(WarningInfo info) {
		//พิมพ์คำเตือนและรายละเอียดที่เกิดขึ้นในระหว่างการโหลดเอกสาร
		System.out.println(MessageFormat.format("WARNING: {0}, source: {1}", info.getWarningType(), info.getSource()));
		System.out.println(MessageFormat.format("\tDescription: {0}", info.getDescription()));
	}
}
@Test
public void convertMetafilesToPng() throws Exception {
	LoadOptions loadOptions = new LoadOptions();
	{
		loadOptions.setConvertMetafilesToPng(true);
	}
	Document doc = new Document("Your Directory Path" + "WMF with image.docx", loadOptions);
}
@Test
public void loadChm() throws Exception {
	LoadOptions loadOptions = new LoadOptions();
	{
		loadOptions.setEncoding(Charset.forName("windows-1251"));
	}
	Document doc = new Document("Your Directory Path" + "HTML help.chm", loadOptions);
}
```

## บทสรุป

ในบทช่วยสอนนี้ เราได้เจาะลึกถึงแง่มุมต่างๆ ของการทำงานกับตัวเลือกการโหลดใน Aspose.Words สำหรับ Java ตัวเลือกการโหลดมีบทบาทสำคัญในการปรับแต่งวิธีการโหลดและประมวลผลเอกสาร ช่วยให้คุณปรับแต่งการประมวลผลเอกสารให้เหมาะกับความต้องการเฉพาะของคุณได้ มาสรุปประเด็นสำคัญที่ครอบคลุมในคู่มือนี้กัน:

## คำถามที่พบบ่อย

### ฉันจะจัดการคำเตือนในระหว่างการโหลดเอกสารได้อย่างไร

 คุณสามารถตั้งค่าการโทรกลับคำเตือนดังที่แสดงใน`warningCallback()` วิธีการข้างต้น ปรับแต่ง`DocumentLoadingWarningCallback` คลาสที่จะจัดการคำเตือนตามความต้องการของแอปพลิเคชันของคุณ

### ฉันสามารถแปลงรูปร่างเป็นวัตถุ Office Math เมื่อโหลดเอกสารได้หรือไม่

 ใช่ คุณสามารถแปลงรูปร่างเป็นวัตถุ Office Math ได้โดยใช้`loadOptions.setConvertShapeToOfficeMath(true)`.

### ฉันจะระบุเวอร์ชัน MS Word สำหรับการโหลดเอกสารได้อย่างไร

 ใช้`loadOptions.setMswVersion(MsWordVersion.WORD_2010)` เพื่อระบุเวอร์ชัน MS Word สำหรับการโหลดเอกสาร

###  จุดประสงค์ของการ`setTempFolder` method in Load Options?

 การ`setTempFolder`วิธีการนี้ช่วยให้คุณระบุโฟลเดอร์ที่เก็บไฟล์ชั่วคราวในระหว่างการประมวลผลเอกสาร
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
