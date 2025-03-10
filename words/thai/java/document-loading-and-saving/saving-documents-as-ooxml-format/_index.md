---
title: การบันทึกเอกสารเป็นรูปแบบ OOXML ใน Aspose.Words สำหรับ Java
linktitle: การบันทึกเอกสารเป็นรูปแบบ OOXML
second_title: API การประมวลผลเอกสาร Java ของ Aspose.Words
description: เรียนรู้วิธีบันทึกเอกสารในรูปแบบ OOXML ด้วย Aspose.Words สำหรับ Java รักษาความปลอดภัย เพิ่มประสิทธิภาพ และปรับแต่งไฟล์ของคุณได้อย่างง่ายดาย
weight: 20
url: /th/java/document-loading-and-saving/saving-documents-as-ooxml-format/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# การบันทึกเอกสารเป็นรูปแบบ OOXML ใน Aspose.Words สำหรับ Java


## บทนำเกี่ยวกับการบันทึกเอกสารเป็นรูปแบบ OOXML ใน Aspose.Words สำหรับ Java

ในคู่มือนี้ เราจะอธิบายวิธีการบันทึกเอกสารในรูปแบบ OOXML โดยใช้ Aspose.Words สำหรับ Java OOXML (Office Open XML) เป็นรูปแบบไฟล์ที่ใช้โดย Microsoft Word และแอปพลิเคชัน Office อื่นๆ เราจะกล่าวถึงตัวเลือกและการตั้งค่าต่างๆ สำหรับการบันทึกเอกสารในรูปแบบ OOXML

## ข้อกำหนดเบื้องต้น

ก่อนที่เราจะเริ่มต้น ตรวจสอบให้แน่ใจว่าคุณได้ตั้งค่าไลบรารี Aspose.Words สำหรับ Java ในโปรเจ็กต์ของคุณแล้ว

## การบันทึกเอกสารด้วยการเข้ารหัสรหัสผ่าน

คุณสามารถเข้ารหัสเอกสารด้วยรหัสผ่านในขณะที่บันทึกเป็นรูปแบบ OOXML ได้ โดยทำได้ดังนี้:

```java
import com.aspose.words.Document;
import com.aspose.words.OoxmlSaveOptions;

// โหลดเอกสาร
Document doc = new Document("Document.docx");

// สร้าง OoxmlSaveOptions และตั้งรหัสผ่าน
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions();
saveOptions.setPassword("password");

// บันทึกเอกสารด้วยการเข้ารหัส
doc.save("EncryptedDoc.docx", saveOptions);
```

## การตั้งค่าการปฏิบัติตาม OOXML

คุณสามารถระบุระดับการปฏิบัติตาม OOXML ได้เมื่อบันทึกเอกสาร ตัวอย่างเช่น คุณสามารถตั้งค่าเป็น ISO 29500:2008 (เข้มงวด) ได้ ดังต่อไปนี้:

```java
import com.aspose.words.Document;
import com.aspose.words.OoxmlSaveOptions;
import com.aspose.words.MsWordVersion;
import com.aspose.words.OoxmlCompliance;

// โหลดเอกสาร
Document doc = new Document("Document.docx");

// เพิ่มประสิทธิภาพสำหรับ Word 2016
doc.getCompatibilityOptions().optimizeFor(MsWordVersion.WORD_2016);

// สร้าง OoxmlSaveOptions และกำหนดระดับการปฏิบัติตาม
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions();
saveOptions.setCompliance(OoxmlCompliance.ISO_29500_2008_STRICT);

// บันทึกเอกสารด้วยการตั้งค่าการปฏิบัติตาม
doc.save("ComplianceDoc.docx", saveOptions);
```

## การอัปเดตคุณสมบัติเวลาที่บันทึกล่าสุด

คุณสามารถเลือกอัปเดตคุณสมบัติ "เวลาที่บันทึกล่าสุด" ของเอกสารได้เมื่อบันทึก โดยทำดังนี้:

```java
import com.aspose.words.Document;
import com.aspose.words.OoxmlSaveOptions;

// โหลดเอกสาร
Document doc = new Document("Document.docx");

// สร้าง OoxmlSaveOptions และเปิดใช้งานการอัปเดตคุณสมบัติเวลาที่บันทึกล่าสุด
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions();
saveOptions.setUpdateLastSavedTimeProperty(true);

// บันทึกเอกสารด้วยคุณสมบัติที่อัปเดต
doc.save("UpdatedLastSavedTime.docx", saveOptions);
```

## การรักษาตัวละครควบคุมแบบเลกาซี

หากเอกสารของคุณมีอักขระควบคุมแบบเก่า คุณสามารถเลือกที่จะเก็บอักขระเหล่านี้ไว้ขณะบันทึกได้ ดังต่อไปนี้:

```java
import com.aspose.words.Document;
import com.aspose.words.OoxmlSaveOptions;
import com.aspose.words.SaveFormat;

//โหลดเอกสารด้วยอักขระควบคุมแบบเดิม
Document doc = new Document("LegacyControlChars.doc");

// สร้าง OoxmlSaveOptions ด้วยรูปแบบ FLAT_OPC และเปิดใช้งานการเก็บอักขระควบคุมแบบเดิม
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions();
saveOptions.setKeepLegacyControlChars(true);

// บันทึกเอกสารด้วยอักขระควบคุมแบบเดิม
doc.save("LegacyControlCharsPreserved.docx", saveOptions);
```

## การตั้งค่าระดับการบีบอัด

คุณสามารถปรับระดับการบีบอัดเมื่อบันทึกเอกสารได้ ตัวอย่างเช่น คุณสามารถตั้งค่าเป็น SUPER_FAST เพื่อการบีบอัดขั้นต่ำ ดังต่อไปนี้:

```java
import com.aspose.words.Document;
import com.aspose.words.OoxmlSaveOptions;
import com.aspose.words.CompressionLevel;

// โหลดเอกสาร
Document doc = new Document("Document.docx");

// สร้าง OoxmlSaveOptions และตั้งค่าระดับการบีบอัด
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions();
saveOptions.setCompressionLevel(CompressionLevel.SUPER_FAST);

// บันทึกเอกสารด้วยระดับการบีบอัดที่ระบุ
doc.save("FastCompressionDoc.docx", saveOptions);
```

เหล่านี้คือตัวเลือกและการตั้งค่าหลักบางส่วนที่คุณสามารถใช้เมื่อบันทึกเอกสารในรูปแบบ OOXML โดยใช้ Aspose.Words สำหรับ Java อย่าลังเลที่จะสำรวจตัวเลือกเพิ่มเติมและปรับแต่งกระบวนการบันทึกเอกสารของคุณตามต้องการ

## โค้ดต้นฉบับที่สมบูรณ์สำหรับการบันทึกเอกสารเป็นรูปแบบ OOXML ใน Aspose.Words สำหรับ Java

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

## บทสรุป

ในคู่มือฉบับสมบูรณ์นี้ เราได้อธิบายวิธีการบันทึกเอกสารในรูปแบบ OOXML โดยใช้ Aspose.Words สำหรับ Java ไม่ว่าคุณจะต้องเข้ารหัสเอกสารด้วยรหัสผ่าน ตรวจสอบให้แน่ใจว่าเป็นไปตามมาตรฐาน OOXML เฉพาะ อัปเดตคุณสมบัติของเอกสาร รักษาอักขระควบคุมแบบเดิม หรือปรับระดับการบีบอัด Aspose.Words ก็มีชุดเครื่องมืออเนกประสงค์ที่ตอบสนองความต้องการของคุณ

## คำถามที่พบบ่อย

### ฉันจะลบการป้องกันด้วยรหัสผ่านจากเอกสารที่ป้องกันด้วยรหัสผ่านได้อย่างไร

หากต้องการลบการป้องกันด้วยรหัสผ่านออกจากเอกสารที่ป้องกันด้วยรหัสผ่าน คุณสามารถเปิดเอกสารด้วยรหัสผ่านที่ถูกต้อง จากนั้นบันทึกโดยไม่ต้องระบุรหัสผ่านในตัวเลือกบันทึก การทำเช่นนี้จะบันทึกเอกสารโดยไม่ต้องป้องกันด้วยรหัสผ่าน

### ฉันสามารถตั้งค่าคุณสมบัติแบบกำหนดเองเมื่อบันทึกเอกสารในรูปแบบ OOXML ได้หรือไม่

 ใช่ คุณสามารถตั้งค่าคุณสมบัติแบบกำหนดเองสำหรับเอกสารก่อนบันทึกเป็นรูปแบบ OOXML ได้ ใช้`BuiltInDocumentProperties` และ`CustomDocumentProperties` คลาสที่จะตั้งค่าคุณสมบัติต่างๆ เช่น ผู้แต่ง ชื่อเรื่อง คำสำคัญ และคุณสมบัติแบบกำหนดเอง

### ระดับการบีบอัดเริ่มต้นเมื่อบันทึกเอกสารในรูปแบบ OOXML คืออะไร

 ระดับการบีบอัดเริ่มต้นเมื่อบันทึกเอกสารในรูปแบบ OOXML โดยใช้ Aspose.Words สำหรับ Java คือ`NORMAL` . คุณสามารถเปลี่ยนระดับการบีบอัดได้`SUPER_FAST` หรือ`MAXIMUM` ตามความจำเป็น.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
