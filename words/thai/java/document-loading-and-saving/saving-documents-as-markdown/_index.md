---
title: การบันทึกเอกสารเป็น Markdown ใน Aspose.Words สำหรับ Java
linktitle: การบันทึกเอกสารเป็นมาร์กดาวน์
second_title: API การประมวลผลเอกสาร Java ของ Aspose.Words
description: เรียนรู้วิธีแปลงเอกสาร Word เป็น Markdown ด้วย Aspose.Words สำหรับ Java คำแนะนำทีละขั้นตอนนี้ครอบคลุมถึงการจัดตำแหน่งตาราง การจัดการรูปภาพ และอื่นๆ อีกมากมาย
weight: 18
url: /th/java/document-loading-and-saving/saving-documents-as-markdown/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# การบันทึกเอกสารเป็น Markdown ใน Aspose.Words สำหรับ Java


## บทนำสู่การบันทึกเอกสารเป็น Markdown ใน Aspose.Words สำหรับ Java

ในคู่มือทีละขั้นตอนนี้ เราจะสาธิตวิธีการบันทึกเอกสารเป็น Markdown โดยใช้ Aspose.Words สำหรับ Java Markdown เป็นภาษามาร์กอัปน้ำหนักเบาที่มักใช้ในการจัดรูปแบบเอกสารข้อความ ด้วย Aspose.Words สำหรับ Java คุณสามารถแปลงเอกสาร Word ของคุณเป็นรูปแบบ Markdown ได้อย่างง่ายดาย เราจะครอบคลุมด้านต่างๆ ของการบันทึกไฟล์ Markdown รวมถึงการจัดตำแหน่งเนื้อหาตารางและการจัดการรูปภาพ

## ข้อกำหนดเบื้องต้น

ก่อนที่คุณจะเริ่มต้น โปรดตรวจสอบให้แน่ใจว่าคุณมีข้อกำหนดเบื้องต้นดังต่อไปนี้:

- Java Development Kit (JDK) ติดตั้งอยู่บนระบบของคุณ
-  ไลบรารี Aspose.Words สำหรับ Java คุณสามารถดาวน์โหลดได้จาก[ที่นี่](https://releases.aspose.com/words/java/).

## ขั้นตอนที่ 1: การสร้างเอกสาร Word

เริ่มต้นด้วยการสร้างเอกสาร Word ที่จะแปลงเป็นรูปแบบ Markdown ในภายหลัง คุณสามารถปรับแต่งเอกสารนี้ตามความต้องการของคุณได้

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// แทรกตารางด้วยสองเซลล์
builder.insertCell();
builder.getParagraphFormat().setAlignment(ParagraphAlignment.RIGHT);
builder.write("Cell1");

builder.insertCell();
builder.getParagraphFormat().setAlignment(ParagraphAlignment.CENTER);
builder.write("Cell2");

// บันทึกเอกสารเป็น Markdown
MarkdownSaveOptions saveOptions = new MarkdownSaveOptions();
doc.save("output.md", saveOptions);
```

 ในตัวอย่างนี้ เราสร้างตารางง่ายๆ ที่มีเซลล์สองเซลล์ และกำหนดการจัดตำแหน่งของย่อหน้าภายในเซลล์เหล่านี้ จากนั้น บันทึกเอกสารเป็นมาร์กดาวน์โดยใช้`MarkdownSaveOptions`.

## ขั้นตอนที่ 2: ปรับแต่งการจัดตำแหน่งเนื้อหาตาราง

Aspose.Words สำหรับ Java ช่วยให้คุณปรับแต่งการจัดวางเนื้อหาในตารางได้เมื่อบันทึกเป็น Markdown คุณสามารถจัดวางเนื้อหาในตารางให้ชิดซ้าย ชิดขวา กึ่งกลาง หรือให้กำหนดโดยอัตโนมัติตามย่อหน้าแรกในแต่ละคอลัมน์ของตาราง

วิธีปรับแต่งการจัดเรียงเนื้อหาตารางมีดังนี้:

```java
// ตั้งค่าการจัดตำแหน่งเนื้อหาตารางไปทางซ้าย
saveOptions.setTableContentAlignment(TableContentAlignment.LEFT);
doc.save("left_alignment.md", saveOptions);

// ตั้งค่าการจัดตำแหน่งเนื้อหาตารางให้ชิดขวา
saveOptions.setTableContentAlignment(TableContentAlignment.RIGHT);
doc.save("right_alignment.md", saveOptions);

// ตั้งค่าการจัดตำแหน่งเนื้อหาตารางให้อยู่กึ่งกลาง
saveOptions.setTableContentAlignment(TableContentAlignment.CENTER);
doc.save("center_alignment.md", saveOptions);

//ตั้งค่าการจัดตำแหน่งเนื้อหาตารางเป็นอัตโนมัติ (กำหนดโดยย่อหน้าแรก)
saveOptions.setTableContentAlignment(TableContentAlignment.AUTO);
doc.save("auto_alignment.md", saveOptions);
```

 โดยการเปลี่ยนแปลง`TableContentAlignment` คุณสมบัติ คุณสามารถควบคุมวิธีการจัดเรียงเนื้อหาภายในตารางเมื่อแปลงเป็น Markdown ได้

## ขั้นตอนที่ 3: การจัดการรูปภาพ

 หากต้องการรวมรูปภาพในเอกสาร Markdown ของคุณ คุณต้องระบุโฟลเดอร์ที่รูปภาพนั้นอยู่ Aspose.Words สำหรับ Java ช่วยให้คุณตั้งค่าโฟลเดอร์รูปภาพใน`MarkdownSaveOptions`.

วิธีตั้งค่าโฟลเดอร์รูปภาพและบันทึกเอกสารที่มีรูปภาพดังนี้:

```java
// โหลดเอกสารที่มีรูปภาพ
Document doc = new Document("document_with_images.docx");

// ตั้งค่าเส้นทางโฟลเดอร์รูปภาพ
MarkdownSaveOptions saveOptions = new MarkdownSaveOptions();
saveOptions.setImagesFolder("images_folder/");

// บันทึกเอกสารด้วยรูปภาพ
doc.save("document_with_images.md", saveOptions);
```

 อย่าลืมเปลี่ยน`"document_with_images.docx"` โดยมีเส้นทางไปยังเอกสาร Word ของคุณที่มีรูปภาพและ`"images_folder/"` พร้อมเส้นทางจริงไปยังโฟลเดอร์ที่เก็บรูปภาพของคุณ

## โค้ดต้นฉบับที่สมบูรณ์สำหรับการบันทึกเอกสารเป็น Markdown ใน Aspose.Words สำหรับ Java

```java
public void autoTableContentAlignment() throws Exception
{
	Document doc = new Document();
	DocumentBuilder builder = new DocumentBuilder(doc);
	builder.insertCell();
	builder.getParagraphFormat().setAlignment(ParagraphAlignment.RIGHT);
	builder.write("Cell1");
	builder.insertCell();
	builder.getParagraphFormat().setAlignment(ParagraphAlignment.CENTER);
	builder.write("Cell2");
	// จัดตำแหน่งย่อหน้าทั้งหมดภายในตารางให้ตรงกัน
	MarkdownSaveOptions saveOptions = new MarkdownSaveOptions();
	{
		saveOptions.setTableContentAlignment(TableContentAlignment.LEFT);
	}
	doc.save("Your Directory Path" + "WorkingWithMarkdownSaveOptions.LeftTableContentAlignment.md", saveOptions);
	saveOptions.setTableContentAlignment(TableContentAlignment.RIGHT);
	doc.save("Your Directory Path" + "WorkingWithMarkdownSaveOptions.RightTableContentAlignment.md", saveOptions);
	saveOptions.setTableContentAlignment(TableContentAlignment.CENTER);
	doc.save("Your Directory Path" + "WorkingWithMarkdownSaveOptions.CenterTableContentAlignment.md", saveOptions);
	// การจัดตำแหน่งในกรณีนี้จะนำมาจากย่อหน้าแรกในคอลัมน์ตารางที่สอดคล้องกัน
	saveOptions.setTableContentAlignment(TableContentAlignment.AUTO);
	doc.save("Your Directory Path" + "WorkingWithMarkdownSaveOptions.AutoTableContentAlignment.md", saveOptions);
}
@Test
public void setImagesFolder() throws Exception
{
	Document doc = new Document("Your Directory Path" + "Image bullet points.docx");
	MarkdownSaveOptions saveOptions = new MarkdownSaveOptions(); { saveOptions.setImagesFolder("Your Directory Path" + "Images"); }
	try(ByteArrayOutputStream stream = new ByteArrayOutputStream())
	{
		doc.save(stream, saveOptions);
	}
}
```

## บทสรุป

ในคู่มือนี้ เราได้ศึกษาวิธีการบันทึกเอกสารเป็น Markdown โดยใช้ Aspose.Words สำหรับ Java เราได้ครอบคลุมถึงการสร้างเอกสาร Word การปรับแต่งการจัดแนวเนื้อหาตาราง และการจัดการรูปภาพในไฟล์ Markdown ขณะนี้ คุณสามารถแปลงเอกสาร Word เป็นรูปแบบ Markdown ได้อย่างมีประสิทธิภาพ ทำให้เหมาะสำหรับแพลตฟอร์มการเผยแพร่และความต้องการด้านเอกสารต่างๆ

## คำถามที่พบบ่อย

### ฉันจะติดตั้ง Aspose.Words สำหรับ Java ได้อย่างไร?

 สามารถติดตั้ง Aspose.Words สำหรับ Java ได้โดยรวมไลบรารีไว้ในโปรเจ็กต์ Java ของคุณ คุณสามารถดาวน์โหลดไลบรารีได้จาก[ที่นี่](https://releases.aspose.com/words/java/) และปฏิบัติตามคำแนะนำในการติดตั้งที่ระบุไว้ในเอกสาร

### ฉันสามารถแปลงเอกสาร Word ที่ซับซ้อนพร้อมตารางและรูปภาพเป็น Markdown ได้หรือไม่

ใช่ Aspose.Words สำหรับ Java รองรับการแปลงเอกสาร Word ที่ซับซ้อนพร้อมตาราง รูปภาพ และองค์ประกอบการจัดรูปแบบต่างๆ ให้เป็น Markdown คุณสามารถปรับแต่งผลลัพธ์ Markdown ให้เหมาะกับความซับซ้อนของเอกสารของคุณได้

### ฉันจะจัดการรูปภาพในไฟล์ Markdown ได้อย่างไร?

 หากต้องการรวมรูปภาพในไฟล์ Markdown ให้ตั้งค่าเส้นทางโฟลเดอร์รูปภาพโดยใช้`setImagesFolder`วิธีการใน`MarkdownSaveOptions`ตรวจสอบให้แน่ใจว่าไฟล์รูปภาพถูกเก็บไว้ในโฟลเดอร์ที่ระบุ และ Aspose.Words สำหรับ Java จะจัดการการอ้างอิงรูปภาพตามนั้น

### มี Aspose.Words เวอร์ชันทดลองใช้งานสำหรับ Java หรือไม่

ใช่ คุณสามารถรับ Aspose.Words รุ่นทดลองใช้สำหรับ Java ได้จากเว็บไซต์ Aspose รุ่นทดลองใช้ช่วยให้คุณประเมินความสามารถของไลบรารีได้ก่อนซื้อใบอนุญาต

### ฉันสามารถหาตัวอย่างและเอกสารเพิ่มเติมได้ที่ไหน

 สำหรับตัวอย่าง เอกสาร และข้อมูลโดยละเอียดเพิ่มเติมเกี่ยวกับ Aspose.Words สำหรับ Java โปรดไปที่[เอกสารประกอบ](https://reference.aspose.com/words/java/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
