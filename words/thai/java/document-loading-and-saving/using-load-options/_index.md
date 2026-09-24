---
date: 2025-12-27
description: เรียนรู้วิธีตั้งค่า LoadOptions ใน Aspose.Words สำหรับ Java รวมถึงวิธีระบุโฟลเดอร์ชั่วคราว
  ตั้งค่าเวอร์ชันของ Word แปลงไฟล์เมต้าเป็น PNG และแปลงรูปทรงเป็นคณิตศาสตร์เพื่อการประมวลผลเอกสารที่ยืดหยุ่น
linktitle: Using Load Options
second_title: Aspose.Words Java Document Processing API
title: วิธีตั้งค่า LoadOptions ใน Aspose.Words สำหรับ Java
url: /th/java/document-loading-and-saving/using-load-options/
weight: 11
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# วิธีตั้งค่า LoadOptions ใน Aspose.Words for Java

ในบทแนะนำนี้เราจะอธิบาย **วิธีตั้งค่า LoadOptions** สำหรับสถานการณ์ต่าง ๆ ที่พบในโลกจริงเมื่อทำงานกับ Aspose.Words for Java LoadOptions ให้คุณควบคุมการเปิดเอกสารได้อย่างละเอียด—ไม่ว่าจะเป็นการอัปเดตฟิลด์ที่เปลี่ยนแปลง, ทำงานกับไฟล์ที่เข้ารหัส, แปลงรูปทรงเป็น Office Math, หรือบอกไลบรารีให้เก็บข้อมูลชั่วคราวไว้ที่ไหน เมื่ออ่านจบคุณจะสามารถปรับพฤติกรรมการโหลดให้ตรงกับความต้องการของแอปพลิเคชันของคุณได้อย่างแม่นยำ

## คำตอบสั้น
- **LoadOptions คืออะไร?** วัตถุการกำหนดค่าที่มีผลต่อวิธีที่ Aspose.Words โหลดเอกสาร  
- **ฉันสามารถอัปเดตฟิลด์ขณะโหลดได้หรือไม่?** ได้—ตั้งค่า `setUpdateDirtyFields(true)`  
- **จะเปิดไฟล์ที่มีรหัสผ่านอย่างไร?** ส่งรหัสผ่านไปยังคอนสตรัคเตอร์ของ `LoadOptions`  
- **สามารถเปลี่ยนโฟลเดอร์ชั่วคราวได้หรือไม่?** ใช้ `setTempFolder("path")`  
- **เมธอดใดที่แปลงรูปทรงเป็น Office Math?** `setConvertShapeToOfficeMath(true)`

## ทำไมต้องใช้ LoadOptions?
LoadOptions ช่วยให้คุณหลีกเลี่ยงขั้นตอนการประมวลผลหลังการโหลด, ลดการใช้หน่วยความจำ, และทำให้เอกสารถูกตีความตามที่คุณต้องการ ตัวอย่างเช่น การแปลงเมตาไฟล์เป็น PNG ระหว่างการโหลดจะป้องกันปัญหาการเรสเตอร์ไลเซชันในภายหลัง, และการระบุเวอร์ชันของ MS Word จะช่วยรักษาความแม่นยำของเลย์เอาต์เมื่อทำงานกับไฟล์เก่า

## ข้อกำหนดเบื้องต้น
- Java 17 หรือใหม่กว่า  
- Aspose.Words for Java (เวอร์ชันล่าสุด)  
- ใบอนุญาต Aspose ที่ถูกต้องสำหรับการใช้งานในสภาพแวดล้อมการผลิต  

## คู่มือแบบขั้นตอน

### อัปเดตฟิลด์ที่เปลี่ยนแปลง

เมื่อเอกสารมีฟิลด์ที่ถูกแก้ไขแต่ยังไม่ได้รีเฟรช, คุณสามารถบอก Aspose.Words ให้ทำการอัปเดตโดยอัตโนมัติขณะโหลดได้

```java
LoadOptions loadOptions = new LoadOptions();
loadOptions.setUpdateDirtyFields(true);

Document doc = new Document("Your Directory Path" + "Dirty field.docx", loadOptions);
doc.save("Your Directory Path" + "WorkingWithLoadOptions.UpdateDirtyFields.docx");
```

*การเรียก `setUpdateDirtyFields(true)` จะทำให้ฟิลด์ที่เปลี่ยนแปลงทั้งหมดถูกคำนวณใหม่ทันทีที่เปิดเอกสาร*

### โหลดเอกสารที่เข้ารหัส

หากไฟล์ต้นทางของคุณมีการป้องกันด้วยรหัสผ่าน, ให้ระบุรหัสผ่านเมื่อสร้างอินสแตนซ์ `LoadOptions` คุณยังสามารถตั้งรหัสผ่านใหม่เมื่อบันทึกเป็นรูปแบบอื่นได้อีกด้วย

```java
@Test
public void loadEncryptedDocument() throws Exception {
    Document doc = new Document("Your Directory Path" + "Encrypted.docx", new LoadOptions("docPassword"));
    doc.save("Your Directory Path" + "WorkingWithLoadOptions.LoadAndSaveEncryptedOdt.odt", new OdtSaveOptions("newPassword"));
}
```

### แปลงรูปทรงเป็น Office Math

เอกสารเก่าบางไฟล์เก็บสมการเป็นรูปทรงวาด การเปิดใช้งานตัวเลือกนี้จะทำให้รูปทรงเหล่านั้นแปลงเป็นวัตถุ Office Math ที่เป็นเนทีฟ ซึ่งแก้ไขได้ง่ายขึ้นในภายหลัง

```java
LoadOptions loadOptions = new LoadOptions();
loadOptions.setConvertShapeToOfficeMath(true);

Document doc = new Document("Your Directory Path" + "Office math.docx", loadOptions);
doc.save("Your Directory Path" + "WorkingWithLoadOptions.ConvertShapeToOfficeMath.docx");
```

### ระบุเวอร์ชันของ MS Word

การกำหนดเวอร์ชัน Word ที่ต้องการช่วยไลบรารีเลือกกฎการเรนเดอร์ที่เหมาะสม, โดยเฉพาะเมื่อทำงานกับรูปแบบไฟล์เก่า

```java
@Test
public void setMsWordVersion() throws Exception {
    LoadOptions loadOptions = new LoadOptions();
    loadOptions.setMswVersion(MsWordVersion.WORD_2010);

    Document doc = new Document("Your Directory Path" + "Document.docx", loadOptions);
    doc.save("Your Directory Path" + "WorkingWithLoadOptions.SetMsWordVersion.docx");
}
```

### ใช้โฟลเดอร์ชั่วคราว

เอกสารขนาดใหญ่บางไฟล์อาจสร้างไฟล์ชั่วคราว (เช่น การสกัดภาพ) คุณสามารถกำหนดโฟลเดอร์เหล่านี้ให้เป็นตำแหน่งที่คุณเลือกได้ ซึ่งเป็นประโยชน์ในสภาพแวดล้อมที่แยกกัน (sandbox)

```java
@Test
public void useTempFolder() throws Exception {
    LoadOptions loadOptions = new LoadOptions();
    loadOptions.setTempFolder("Your Directory Path");

    Document doc = new Document("Your Directory Path" + "Document.docx", loadOptions);
}
```

### คอลแบ็กเตือนภัย

ขณะโหลด, Aspose.Words อาจส่งคำเตือน (เช่น ฟีเจอร์ที่ไม่รองรับ) การทำคอลแบ็กช่วยให้คุณบันทึกหรือจัดการกับเหตุการณ์เหล่านี้ได้

```java
@Test
public void warningCallback() throws Exception {
    LoadOptions loadOptions = new LoadOptions();
    loadOptions.setWarningCallback(new DocumentLoadingWarningCallback());

    Document doc = new Document("Your Directory Path" + "Document.docx", loadOptions);
}

public static class DocumentLoadingWarningCallback implements IWarningCallback {
    public void warning(WarningInfo info) {
        // Handle warnings as they arise during document loading.
        System.out.println(MessageFormat.format("WARNING: {0}, source: {1}", info.getWarningType(), info.getSource()));
        System.out.println(MessageFormat.format("\tDescription: {0}", info.getDescription()));
    }
}
```

### แปลงเมตาไฟล์เป็น PNG

เมตาไฟล์เช่น WMF สามารถแปลงเป็น PNG ระหว่างการโหลด เพื่อให้การแสดงผลสอดคล้องกันบนทุกแพลตฟอร์ม

```java
@Test
public void convertMetafilesToPng() throws Exception {
    LoadOptions loadOptions = new LoadOptions();
    loadOptions.setConvertMetafilesToPng(true);

    Document doc = new Document("Your Directory Path" + "WMF with image.docx", loadOptions);
}
```

## โค้ดเต็มสำหรับการทำงานกับ LoadOptions ใน Aspose.Words for Java

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
	// Create a new LoadOptions object, which will load documents according to MS Word 2019 specification by default
	// and change the loading version to Microsoft Word 2010.
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
		// Prints warnings and their details as they arise during document loading.
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

## กรณีการใช้งานทั่วไป & เคล็ดลับ

- **สายงานแปลงไฟล์เป็นชุด** – ผสาน `setTempFolder` กับงานที่กำหนดเวลาเพื่อประมวลผลหลายร้อยไฟล์โดยไม่ทำให้โฟลเดอร์ temp ของระบบเต็ม  
- **การย้ายเอกสารเก่า** – ใช้ `setMswVersion` ร่วมกับ `setConvertShapeToOfficeMath` เพื่อย้ายเอกสารวิศวกรรมเก่าไปยังรูปแบบสมัยใหม่พร้อมรักษาสมการไว้  
- **การจัดการเอกสารอย่างปลอดภัย** – ผสาน `loadEncryptedDocument` กับ `OdtSaveOptions` เพื่อเข้ารหัสไฟล์ใหม่ด้วยรหัสผ่านใหม่ในรูปแบบอื่น  

## คำถามที่พบบ่อย

**ถาม: จะจัดการคำเตือนระหว่างการโหลดเอกสารอย่างไร?**  
ตอบ: สร้างคลาสที่ implements `IWarningCallback` (ตามตัวอย่าง *คอลแบ็กเตือนภัย*) แล้วลงทะเบียนผ่าน `loadOptions.setWarningCallback(...)` ซึ่งทำให้คุณสามารถบันทึก, เพิกเฉย, หรือยกเลิกการทำงานตามระดับความรุนแรงของคำเตือนได้

**ถาม: สามารถแปลงรูปทรงเป็น Office Math objects ขณะโหลดเอกสารได้หรือไม่?**  
ตอบ: ได้—เรียก `loadOptions.setConvertShapeToOfficeMath(true)` ก่อนสร้าง `Document` ไลบรารีจะเปลี่ยนรูปทรงที่เข้ากันได้เป็นวัตถุ Office Math โดยอัตโนมัติ

**ถาม: จะระบุเวอร์ชันของ MS Word สำหรับการโหลดเอกสารอย่างไร?**  
ตอบ: ใช้ `loadOptions.setMswVersion(MsWordVersion.WORD_2010)` (หรือค่า enum ใดก็ได้) เพื่อบอก Aspose.Words ว่าจะใช้กฎการเรนเดอร์ของเวอร์ชัน Word ใด

**ถาม: จุดประสงค์ของเมธอด `setTempFolder` ใน LoadOptions คืออะไร?**  
ตอบ: มันกำหนดตำแหน่งโฟลเดอร์ที่ไฟล์ชั่วคราวทั้งหมดที่สร้างระหว่างการโหลด (เช่น ภาพที่สกัดออก) จะถูกเก็บไว้ ซึ่งสำคัญสำหรับสภาพแวดล้อมที่มีการจำกัดโฟลเดอร์ temp ของระบบ

**ถาม: สามารถแปลงเมตาไฟล์อย่าง WMF เป็น PNG ระหว่างการโหลดได้หรือไม่?**  
ตอบ: แน่นอน—เปิดใช้งานด้วย `loadOptions.setConvertMetafilesToPng(true)` ซึ่งทำให้ภาพเรสเตอร์ถูกเก็บเป็น PNG, เพิ่มความเข้ากันได้กับโปรแกรมดูสมัยใหม่

## สรุป

เราได้ครอบคลุมเทคนิคสำคัญสำหรับ **วิธีตั้งค่า LoadOptions** ใน Aspose.Words for Java ตั้งแต่การอัปเดตฟิลด์ที่เปลี่ยนแปลง, การจัดการไฟล์ที่เข้ารหัส, การแปลงรูปทรง, การระบุเวอร์ชัน Word, การกำหนดที่จัดเก็บไฟล์ชั่วคราว, และอื่น ๆ ด้วยการใช้ตัวเลือกเหล่านี้ คุณสามารถสร้างสายงานประมวลผลเอกสารที่แข็งแรง, มีประสิทธิภาพสูง, และปรับตัวได้กับสถานการณ์อินพุตที่หลากหลาย

---

**อัปเดตล่าสุด:** 2025-12-27  
**ทดสอบกับ:** Aspose.Words for Java 24.11  
**ผู้เขียน:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}