---
date: 2025-12-29
description: เรียนรู้วิธีเข้ารหัสไฟล์ docx ด้วยรหัสผ่านโดยใช้ตัวเลือกการบันทึกของ
  Aspose.Words for Java ปกป้อง ปรับให้เหมาะสม และปรับแต่งไฟล์ OOXML ของคุณได้อย่างง่ายดาย.
linktitle: Saving Documents as OOXML Format
second_title: Aspose.Words Java Document Processing API
title: วิธีเข้ารหัสไฟล์ DOCX ด้วยรหัสผ่านโดยใช้ Aspose.Words สำหรับ Java
url: /th/java/document-loading-and-saving/saving-documents-as-ooxml-format/
weight: 20
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# วิธีการเข้ารหัส DOCX ด้วยรหัสผ่านโดยใช้ Aspose.Words for Java

ในคู่มือนี้คุณจะได้เรียนรู้ **วิธีการเข้ารหัส docx ด้วยรหัสผ่าน** ขณะบันทึกเอกสารในรูปแบบ OOXML ด้วย Aspose.Words for Java ไม่ว่าคุณจะต้องการปกป้องรายงานที่เป็นความลับหรือรักษาแบบร่างสัญญา ขั้นตอนต่อไปนี้จะแสดงให้คุณเห็นวิธีการตั้งค่าการป้องกันด้วยรหัสผ่านและปรับแต่งตัวเลือกการบันทึก OOXML อื่น ๆ อย่างละเอียด

## คำตอบอย่างรวดเร็ว
- **ฉันสามารถเข้ารหัสไฟล์ DOCX ด้วยรหัสผ่านได้หรือไม่?** ได้, ใช้ `OoxmlSaveOptions.setPassword()` ก่อนบันทึก  
- **คลาสใดควบคุมการตั้งค่าการบันทึก OOXML?** `OoxmlSaveOptions` (ส่วนหนึ่งของ Aspose.Words)  
- **ฉันต้องมีลิขสิทธิ์สำหรับการป้องกันด้วยรหัสผ่านหรือไม่?** จำเป็นต้องมีลิขสิทธิ์ Aspose.Words ที่ถูกต้องสำหรับการใช้งานในสภาพแวดล้อมการผลิต  
- **ฉันสามารถรวมการเข้ารหัสกับการตั้งค่าการปฏิบัติตามมาตรฐานได้หรือไม่?** แน่นอน – ตั้งค่า `setPassword` และ `setCompliance` บนอินสแตนซ์ `OoxmlSaveOptions` เดียวกัน  
- **ระดับการบีบอัดที่มีให้เลือกมีอะไรบ้าง?** `NORMAL`, `SUPER_FAST` และ `MAXIMUM` ผ่าน `CompressionLevel`

## “encrypt docx with password” คืออะไร?
การเข้ารหัสไฟล์ DOCX หมายความว่าข้อมูลภายในไฟล์จะถูกเก็บในรูปแบบที่เข้ารหัสและสามารถเปิดได้เฉพาะเมื่อป้อนรหัสผ่านที่ถูกต้องเท่านั้น การทำเช่นนี้ช่วยปกป้องข้อมูลที่สำคัญจากการเข้าถึงโดยไม่ได้รับอนุญาต ในขณะเดียวกันยังคงให้เครื่องมือ Word มาตรฐานเปิดไฟล์ได้เมื่อมีการใส่รหัสผ่าน

## ทำไมต้องใช้ Aspose.Words save options สำหรับการเข้ารหัส?
Aspose.Words มี **aspose words save options** ที่หลากหลาย ช่วยให้คุณควบคุมไม่เพียงแต่การเข้ารหัสเท่านั้น แต่รวมถึงระดับการปฏิบัติตามมาตรฐาน, การบีบอัด, และการจัดการอักขระควบคุมแบบเก่า—all จากโค้ด Java นี้ทำให้ไม่ต้องพึ่งพาการประมวลผลหลังการบันทึกหรือเครื่องมือของบุคคลที่สาม

## ข้อกำหนดเบื้องต้น
- Java Development Kit (JDK 8 หรือสูงกว่า)  
- ไลบรารี Aspose.Words for Java ที่เพิ่มเข้าไปในโปรเจกต์ของคุณ (Maven/Gradle หรือ JAR)  
- ลิขสิทธิ์ Aspose.Words ที่ถูกต้องสำหรับการผลิต (ไม่บังคับสำหรับการทดลอง)

## การบันทึกเอกสารพร้อมการเข้ารหัสด้วยรหัสผ่าน

คุณสามารถเข้ารหัสเอกสารของคุณด้วยรหัสผ่านขณะบันทึกในรูปแบบ OOXML ได้ ตามขั้นตอนต่อไปนี้:

```java
import com.aspose.words.Document;
import com.aspose.words.OoxmlSaveOptions;

// Load the document
Document doc = new Document("Document.docx");

// Create OoxmlSaveOptions and set the password
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions();
saveOptions.setPassword("password");

// Save the document with encryption
doc.save("EncryptedDoc.docx", saveOptions);
```

## การตั้งค่าการปฏิบัติตามมาตรฐาน OOXML

คุณสามารถระบุระดับการปฏิบัติตามมาตรฐาน OOXML เมื่อบันทึกเอกสาร ตัวอย่างเช่น ตั้งค่าเป็น ISO 29500:2008 (Strict) ตามนี้:

```java
import com.aspose.words.Document;
import com.aspose.words.OoxmlSaveOptions;
import com.aspose.words.MsWordVersion;
import com.aspose.words.OoxmlCompliance;

// Load the document
Document doc = new Document("Document.docx");

// Optimize for Word 2016
doc.getCompatibilityOptions().optimizeFor(MsWordVersion.WORD_2016);

// Create OoxmlSaveOptions and set the compliance level
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions();
saveOptions.setCompliance(OoxmlCompliance.ISO_29500_2008_STRICT);

// Save the document with compliance setting
doc.save("ComplianceDoc.docx", saveOptions);
```

## การอัปเดตคุณสมบัติ “Last Saved Time”

คุณสามารถเลือกให้ระบบอัปเดตคุณสมบัติ “Last Saved Time” ของเอกสารเมื่อบันทึกได้ ตามนี้:

```java
import com.aspose.words.Document;
import com.aspose.words.OoxmlSaveOptions;

// Load the document
Document doc = new Document("Document.docx");

// Create OoxmlSaveOptions and enable updating the Last Saved Time property
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions();
saveOptions.setUpdateLastSavedTimeProperty(true);

// Save the document with the updated property
doc.save("UpdatedLastSavedTime.docx", saveOptions);
```

## การคงอักขระควบคุมแบบเก่า

หากเอกสารของคุณมีอักขระควบคุมแบบเก่า คุณสามารถเลือกคงไว้ขณะบันทึกได้ ตามนี้:

```java
import com.aspose.words.Document;
import com.aspose.words.OoxmlSaveOptions;
import com.aspose.words.SaveFormat;

// Load a document with legacy control characters
Document doc = new Document("LegacyControlChars.doc");

// Create OoxmlSaveOptions with the FLAT_OPC format and enable keeping legacy control characters
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions();
saveOptions.setKeepLegacyControlChars(true);

// Save the document with legacy control characters
doc.save("LegacyControlCharsPreserved.docx", saveOptions);
```

## การตั้งค่าระดับการบีบอัด

คุณสามารถปรับระดับการบีบอัดเมื่อบันทึกเอกสาร ตัวอย่างเช่น ตั้งค่าเป็น **SUPER_FAST** เพื่อบีบอัดน้อยที่สุด ตามนี้:

```java
import com.aspose.words.Document;
import com.aspose.words.OoxmlSaveOptions;
import com.aspose.words.CompressionLevel;

// Load the document
Document doc = new Document("Document.docx");

// Create OoxmlSaveOptions and set the compression level
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions();
saveOptions.setCompressionLevel(CompressionLevel.SUPER_FAST);

// Save the document with the specified compression level
doc.save("FastCompressionDoc.docx", saveOptions);
```

เหล่านี้เป็นตัวเลือกและการตั้งค่าที่สำคัญบางส่วนที่คุณสามารถใช้เมื่อบันทึกเอกสารในรูปแบบ OOXML ด้วย Aspose.Words for Java อย่าลังเลที่จะสำรวจตัวเลือกเพิ่มเติมและปรับแต่งกระบวนการบันทึกเอกสารของคุณตามต้องการ

## โค้ดเต็มสำหรับการบันทึกเอกสารเป็นรูปแบบ OOXML ใน Aspose.Words for Java

```java
public void encryptDocxWithPassword() throws Exception
{
	Document doc = new Document("Your Directory Path" + "Document.docx");
	OoxmlSaveOptions saveOptions = new OoxmlSaveOptions(); { saveOptions.setPassword("password"); }
	doc.save("Your Directory Path" + "WorkingWithOoxmlSaveOptions.EncryptDocxWithPassword.docx", saveOptions);
}
@Test
public void ooxmlComplianceIso29500_2008_Strict() throws Exception
{
	Document doc = new Document("Your Directory Path" + "Document.docx");
	doc.getCompatibilityOptions().optimizeFor(MsWordVersion.WORD_2016);
	OoxmlSaveOptions saveOptions = new OoxmlSaveOptions(); { saveOptions.setCompliance(OoxmlCompliance.ISO_29500_2008_STRICT); }
	doc.save("Your Directory Path" + "WorkingWithOoxmlSaveOptions.OoxmlComplianceIso29500_2008_Strict.docx", saveOptions);
}
@Test
public void updateLastSavedTimeProperty() throws Exception
{
	Document doc = new Document("Your Directory Path" + "Document.docx");
	OoxmlSaveOptions saveOptions = new OoxmlSaveOptions(); { saveOptions.setUpdateLastSavedTimeProperty(true); }
	doc.save("Your Directory Path" + "WorkingWithOoxmlSaveOptions.UpdateLastSavedTimeProperty.docx", saveOptions);
}
@Test
public void keepLegacyControlChars() throws Exception
{
	Document doc = new Document("Your Directory Path" + "Legacy control character.doc");
	OoxmlSaveOptions saveOptions = new OoxmlSaveOptions(); { saveOptions.setKeepLegacyControlChars(true); }
	doc.save("Your Directory Path" + "WorkingWithOoxmlSaveOptions.KeepLegacyControlChars.docx", saveOptions);
}
@Test
public void setCompressionLevel() throws Exception
{
	Document doc = new Document("Your Directory Path" + "Document.docx");
	OoxmlSaveOptions saveOptions = new OoxmlSaveOptions(); { saveOptions.setCompressionLevel(CompressionLevel.SUPER_FAST); }
	doc.save("Your Directory Path" + "WorkingWithOoxmlSaveOptions.SetCompressionLevel.docx", saveOptions);
}
```

## สรุป

ในคู่มือฉบับครอบคลุมนี้ เราได้สำรวจ **วิธีการเข้ารหัส docx ด้วยรหัสผ่าน** และการปรับแต่งตัวเลือกการบันทึก OOXML ต่าง ๆ ด้วย Aspose.Words for Java ไม่ว่าคุณจะต้องการปกป้องเนื้อหาที่เป็นความลับ, ปฏิบัติตามมาตรฐาน ISO อย่างเคร่งครัด, รักษาอักขระควบคุมแบบเก่า, หรือควบคุมการบีบอัด ไลบรารีนี้ให้คุณควบคุมได้อย่างละเอียดผ่าน API `OoxmlSaveOptions` เดียวกัน

## คำถามที่พบบ่อย

**ถาม: ฉันจะลบการป้องกันด้วยรหัสผ่านจากเอกสารที่มีการป้องกันอย่างไร?**  
ตอบ: เปิดเอกสารด้วยรหัสผ่านที่ถูกต้องแล้วบันทึกใหม่โดยไม่เรียก `setPassword` ไฟล์ใหม่จะไม่มีการป้องกัน

**ถาม: ฉันสามารถตั้งค่าคุณสมบัติเฉพาะเมื่อบันทึกเอกสารในรูปแบบ OOXML ได้หรือไม่?**  
ตอบ: ได้ ใช้ `BuiltInDocumentProperties` หรือ `CustomDocumentProperties` บนวัตถุ `Document` ก่อนเรียก `save`

**ถาม: ระดับการบีบอัดเริ่มต้นเมื่อบันทึกเอกสารในรูปแบบ OOXML คืออะไร?**  
ตอบ: ค่าเริ่มต้นคือ `NORMAL` คุณสามารถสลับเป็น `SUPER_FAST` เพื่อความเร็วหรือ `MAXIMUM` เพื่อขนาดไฟล์ที่เล็กลง

**ถาม: ตัวเลือกการบันทึก aspose words ทำงานกับเวอร์ชัน Word เก่าได้หรือไม่?**  
ตอบ: ได้ โดยการปรับ `MsWordVersion` และการตั้งค่าการปฏิบัติตามมาตรฐาน คุณสามารถกำหนดเป้าหมายเป็น Word 2007‑2019 และรับประกันความเข้ากันได้

**ถาม: สามารถรวมหลายตัวเลือกการบันทึกในหนึ่งการดำเนินการได้หรือไม่?**  
ตอบ: แน่นอน สร้างอินสแตนซ์ `OoxmlSaveOptions` ตัวเดียว ตั้งค่าทุกคุณสมบัติที่ต้องการ (รหัสผ่าน, การปฏิบัติตาม, การบีบอัด ฯลฯ) แล้วส่งให้ `doc.save()`

---

**อัปเดตล่าสุด:** 2025-12-29  
**ทดสอบด้วย:** Aspose.Words for Java 24.12  
**ผู้เขียน:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}