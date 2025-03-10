---
title: การบันทึกเอกสารเป็น PDF ใน Aspose.Words สำหรับ Java
linktitle: การบันทึกเอกสารเป็น PDF
second_title: API การประมวลผลเอกสาร Java ของ Aspose.Words
description: เรียนรู้วิธีบันทึกเอกสาร Word เป็น PDF โดยใช้ Aspose.Words สำหรับ Java ปรับแต่งแบบอักษร คุณสมบัติ และคุณภาพของรูปภาพ คู่มือที่ครอบคลุมสำหรับการแปลง PDF
weight: 22
url: /th/java/document-loading-and-saving/saving-documents-as-pdf/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# การบันทึกเอกสารเป็น PDF ใน Aspose.Words สำหรับ Java


## บทนำสู่การบันทึกเอกสารเป็น PDF ใน Aspose.Words สำหรับ Java

ในคู่มือทีละขั้นตอนนี้ เราจะอธิบายวิธีการบันทึกเอกสารเป็น PDF โดยใช้ Aspose.Words สำหรับ Java เราจะครอบคลุมประเด็นต่างๆ ของการแปลง PDF และให้ตัวอย่างโค้ดเพื่อทำให้กระบวนการง่ายขึ้น

## ข้อกำหนดเบื้องต้น

ก่อนที่เราจะเริ่มต้น ให้แน่ใจว่าคุณมีข้อกำหนดเบื้องต้นดังต่อไปนี้:

- Java Development Kit (JDK) ติดตั้งอยู่บนระบบของคุณ
-  ไลบรารี Aspose.Words สำหรับ Java คุณสามารถดาวน์โหลดได้จาก[ที่นี่](https://releases.aspose.com/words/java/).

## การแปลงเอกสารเป็น PDF

หากต้องการแปลงเอกสาร Word เป็น PDF คุณสามารถใช้โค้ดสั้นๆ ดังต่อไปนี้:

```java
Document doc = new Document("input.docx");
PdfSaveOptions saveOptions = new PdfSaveOptions();
doc.save("output.pdf", saveOptions);
```

 แทนที่`"input.docx"` ด้วยเส้นทางไปยังเอกสาร Word ของคุณและ`"output.pdf"` ด้วยเส้นทางไฟล์ PDF เอาท์พุตตามต้องการ

## การควบคุมตัวเลือกการบันทึก PDF

 คุณสามารถควบคุมตัวเลือกการบันทึก PDF ต่างๆ ได้โดยใช้`PdfSaveOptions` คลาส ตัวอย่างเช่น คุณสามารถตั้งชื่อเรื่องการแสดงผลสำหรับเอกสาร PDF ได้ดังนี้:

```java
PdfSaveOptions saveOptions = new PdfSaveOptions();
saveOptions.setDisplayDocTitle(true);
doc.save("output.pdf", saveOptions);
```

## การฝังแบบอักษรใน PDF

หากต้องการฝังแบบอักษรใน PDF ที่สร้างขึ้น ให้ใช้โค้ดดังต่อไปนี้:

```java
PdfSaveOptions saveOptions = new PdfSaveOptions();
saveOptions.setEmbedFullFonts(true);
doc.save("output.pdf", saveOptions);
```

## การปรับแต่งคุณสมบัติของเอกสาร

คุณสามารถปรับแต่งคุณสมบัติเอกสารใน PDF ที่สร้างขึ้นได้ ตัวอย่างเช่น:

```java
PdfSaveOptions saveOptions = new PdfSaveOptions();
saveOptions.setCustomPropertiesExport(PdfCustomPropertiesExport.STANDARD);
doc.save("output.pdf", saveOptions);
```

## โครงสร้างเอกสารการส่งออก

 ในการส่งออกโครงสร้างเอกสาร ให้ตั้งค่า`exportDocumentStructure` ตัวเลือกที่จะ`true`-

```java
PdfSaveOptions saveOptions = new PdfSaveOptions();
saveOptions.setExportDocumentStructure(true);
doc.save("output.pdf", saveOptions);
```

## การบีบอัดภาพ

คุณสามารถควบคุมการบีบอัดภาพได้โดยใช้โค้ดต่อไปนี้:

```java
PdfSaveOptions saveOptions = new PdfSaveOptions();
saveOptions.setImageCompression(PdfImageCompression.JPEG);
doc.save("output.pdf", saveOptions);
```

## การอัปเดตคุณสมบัติที่พิมพ์ล่าสุด

หากต้องการอัปเดตคุณสมบัติ "พิมพ์ล่าสุด" ใน PDF ให้ใช้:

```java
PdfSaveOptions saveOptions = new PdfSaveOptions();
saveOptions.setUpdateLastPrintedProperty(true);
doc.save("output.pdf", saveOptions);
```

## การเรนเดอร์เอฟเฟกต์ DML 3D

สำหรับการเรนเดอร์เอฟเฟ็กต์ DML 3D ขั้นสูง ให้ตั้งค่าโหมดการเรนเดอร์:

```java
PdfSaveOptions saveOptions = new PdfSaveOptions();
saveOptions.setDml3DEffectsRenderingMode(Dml3DEffectsRenderingMode.ADVANCED);
doc.save("output.pdf", saveOptions);
```

## การแทรกภาพ

คุณสามารถเปิดใช้งานการแทรกภาพเพื่อปรับปรุงคุณภาพของภาพได้:

```java
PdfSaveOptions saveOptions = new PdfSaveOptions();
saveOptions.setInterpolateImages(true);
doc.save("output.pdf", saveOptions);
```

## บทสรุป

Aspose.Words สำหรับ Java มอบความสามารถที่ครอบคลุมสำหรับการแปลงเอกสาร Word เป็นรูปแบบ PDF พร้อมความยืดหยุ่นและตัวเลือกการปรับแต่ง คุณสามารถควบคุมด้านต่างๆ ของเอาต์พุต PDF ได้ เช่น แบบอักษร คุณสมบัติเอกสาร การบีบอัดรูปภาพ และอื่นๆ อีกมากมาย

## คำถามที่พบบ่อย

### ฉันจะแปลงเอกสาร Word เป็น PDF โดยใช้ Aspose.Words สำหรับ Java ได้อย่างไร

หากต้องการแปลงเอกสาร Word เป็น PDF ให้ใช้โค้ดดังต่อไปนี้:

```java
Document doc = new Document("input.docx");
PdfSaveOptions saveOptions = new PdfSaveOptions();
doc.save("output.pdf", saveOptions);
```

 แทนที่`"input.docx"` ด้วยเส้นทางไปยังเอกสาร Word ของคุณและ`"output.pdf"` ด้วยเส้นทางไฟล์ PDF เอาท์พุตตามต้องการ

### ฉันสามารถฝังแบบอักษรลงใน PDF ที่สร้างโดย Aspose.Words สำหรับ Java ได้หรือไม่

 ใช่ คุณสามารถฝังแบบอักษรใน PDF ได้โดยการตั้งค่า`setEmbedFullFonts` ตัวเลือกที่จะ`true` ใน`PdfSaveOptions`นี่คือตัวอย่าง:

```java
PdfSaveOptions saveOptions = new PdfSaveOptions();
saveOptions.setEmbedFullFonts(true);
doc.save("output.pdf", saveOptions);
```

### ฉันจะปรับแต่งคุณสมบัติเอกสารใน PDF ที่สร้างขึ้นได้อย่างไร

 คุณสามารถปรับแต่งคุณสมบัติเอกสารใน PDF ได้โดยใช้`setCustomPropertiesExport` ตัวเลือกใน`PdfSaveOptions`. ตัวอย่างเช่น:

```java
PdfSaveOptions saveOptions = new PdfSaveOptions();
saveOptions.setCustomPropertiesExport(PdfCustomPropertiesExport.STANDARD);
doc.save("output.pdf", saveOptions);
```

### จุดประสงค์ของการบีบอัดภาพใน Aspose.Words สำหรับ Java คืออะไร

 การบีบอัดภาพช่วยให้คุณควบคุมคุณภาพและขนาดของภาพใน PDF ที่สร้างขึ้นได้ คุณสามารถตั้งค่าโหมดการบีบอัดภาพได้โดยใช้`setImageCompression` ใน`PdfSaveOptions`.

### ฉันจะอัปเดตคุณสมบัติ "พิมพ์ล่าสุด" ใน PDF ได้อย่างไร

 คุณสามารถอัปเดตคุณสมบัติ "พิมพ์ล่าสุด" ใน PDF ได้โดยตั้งค่า`setUpdateLastPrintedProperty` ถึง`true` ใน`PdfSaveOptions`นี่จะแสดงวันที่พิมพ์ล่าสุดในข้อมูลเมตาของ PDF

### ฉันจะปรับปรุงคุณภาพของภาพเมื่อแปลงเป็น PDF ได้อย่างไร

 เพื่อปรับปรุงคุณภาพของภาพ ให้เปิดใช้งานการแทรกภาพโดยการตั้งค่า`setInterpolateImages` ถึง`true` ใน`PdfSaveOptions`จะทำให้ภาพใน PDF เรียบเนียนขึ้นและมีคุณภาพสูงขึ้น
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
