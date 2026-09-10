---
date: 2025-12-22
description: เรียนรู้วิธีการส่งออก markdown โดยการแปลงเอกสาร Word เป็น Markdown ด้วย
  Aspose.Words for Java คู่มือขั้นตอนนี้ครอบคลุมการจัดแนวตาราง การจัดการรูปภาพ และอื่น
  ๆ อีกมาก
linktitle: Saving Documents as Markdown
second_title: Aspose.Words Java Document Processing API
title: วิธีส่งออก Markdown ด้วย Aspose.Words สำหรับ Java
url: /th/java/document-loading-and-saving/saving-documents-as-markdown/
weight: 18
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# วิธีการส่งออก Markdown ด้วย Aspose.Words สำหรับ Java

## บทนำสู่การส่งออก Markdown ด้วย Aspose.Words สำหรับ Java

ในบทแนะนำแบบขั้นตอนนี้, **คุณจะได้เรียนรู้วิธีการส่งออก markdown** จากเอกสาร Word ด้วย Aspose.Words สำหรับ Java. Markdown เป็นภาษามาร์กอัปแบบเบาที่เหมาะสำหรับเอกสาร, ตัวสร้างเว็บไซต์แบบสแตติก, และหลายแพลตฟอร์มการเผยแพร่. เมื่อจบคู่มือคุณจะสามารถ **แปลง Word เป็น markdown**, ปรับแต่งการจัดแนวตาราง, และ **จัดการรูปภาพใน markdown** ได้อย่างง่ายดาย.

## คำตอบสั้น
- **คลาสหลักสำหรับบันทึกเป็น Markdown คืออะไร?** `MarkdownSaveOptions`
- **รูปภาพสามารถฝังอัตโนมัติได้หรือไม่?** ใช่ – ตั้งค่าโฟลเดอร์รูปภาพผ่าน `setImagesFolder`.
- **ฉันจะควบคุมการจัดแนวตารางได้อย่างไร?** ใช้ `TableContentAlignment` (LEFT, RIGHT, CENTER, AUTO).
- **ข้อกำหนดขั้นต่ำคืออะไร?** JDK 8+ และไลบรารี Aspose.Words สำหรับ Java.
- **มีเวอร์ชันทดลองหรือไม่?** มี, ดาวน์โหลดจากเว็บไซต์ Aspose.

## อะไรคือ “วิธีการส่งออก markdown”?
การส่งออก markdown หมายถึงการนำเอกสาร Word ที่มีรูปแบบข้อความเต็ม (`.docx`) มาผลิตไฟล์ข้อความธรรมดา `.md` ที่คงไว้ซึ่งหัวเรื่อง, ตาราง, และรูปภาพในไวยากรณ์ Markdown.

## ทำไมต้องใช้ Aspose.Words สำหรับ Java เพื่อแปลง docx พร้อมรูปภาพ?
Aspose.Words จัดการกับเลย์เอาต์ที่ซับซ้อน, รูปภาพฝัง, และโครงสร้างตารางโดยไม่สูญเสียความแม่นยำ. มันยังให้คุณควบคุมผลลัพธ์ Markdown อย่างละเอียด, เช่น การจัดแนวตารางและการจัดการโฟลเดอร์รูปภาพ.

## ข้อกำหนดเบื้องต้น

- Java Development Kit (JDK) ที่ติดตั้งบนระบบของคุณ.
- ไลบรารี Aspose.Words สำหรับ Java. คุณสามารถดาวน์โหลดได้จาก [here](https://releases.aspose.com/words/java/).

## ขั้นตอนที่ 1: สร้างเอกสาร Word อย่างง่าย

แรกเริ่มเราจะสร้างเอกสารขนาดเล็กที่มีตาราง. นี้จะทำให้เราสามารถสาธิต **การปรับแต่งการจัดแนวตาราง** ได้ในภายหลัง.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a table with two cells
builder.insertCell();
builder.getParagraphFormat().setAlignment(ParagraphAlignment.RIGHT);
builder.write("Cell1");

builder.insertCell();
builder.getParagraphFormat().setAlignment(ParagraphAlignment.CENTER);
builder.write("Cell2");

// Save the document as Markdown
MarkdownSaveOptions saveOptions = new MarkdownSaveOptions();
doc.save("output.md", saveOptions);
```

ในโค้ดข้างต้นเรา:

1. สร้าง `Document` ใหม่.
2. ใช้ `DocumentBuilder` เพื่อแทรกตารางสองเซลล์.
3. ใช้การจัดแนวย่อหน้า **ขวา** และ **ศูนย์กลาง** ภายในแต่ละเซลล์.
4. บันทึกไฟล์เป็น Markdown ด้วย `MarkdownSaveOptions`.

## ขั้นตอนที่ 2: ปรับแต่งการจัดแนวเนื้อหาในตาราง

Aspose.Words ให้คุณกำหนดวิธีที่เซลล์ตารางจะถูกแสดงใน Markdown สุดท้าย. คุณสามารถบังคับให้จัดแนวซ้าย, ขวา, ศูนย์กลาง, หรือให้ไลบรารีตัดสินใจอัตโนมัติตามย่อหน้าแรกของแต่ละคอลัมน์.

```java
// Set the table content alignment to left
saveOptions.setTableContentAlignment(TableContentAlignment.LEFT);
doc.save("left_alignment.md", saveOptions);

// Set the table content alignment to right
saveOptions.setTableContentAlignment(TableContentAlignment.RIGHT);
doc.save("right_alignment.md", saveOptions);

// Set the table content alignment to center
saveOptions.setTableContentAlignment(TableContentAlignment.CENTER);
doc.save("center_alignment.md", saveOptions);

// Set the table content alignment to auto (determined by first paragraph)
saveOptions.setTableContentAlignment(TableContentAlignment.AUTO);
doc.save("auto_alignment.md", saveOptions);
```

โดยการสลับคุณสมบัติ `TableContentAlignment` คุณจะควบคุม **การปรับแต่งการจัดแนวตาราง** สำหรับผลลัพธ์ Markdown.

## ขั้นตอนที่ 3: จัดการรูปภาพเมื่อส่งออกเป็น markdown

เมื่อเอกสารมีรูปภาพ, คุณต้องการให้รูปเหล่านั้นปรากฏอย่างถูกต้องในไฟล์ `.md` ที่สร้างขึ้น. ตั้งค่าโฟลเดอร์ที่ Aspose.Words จะบันทึกรูปภาพที่สกัดออกมา.

```java
// Load a document containing images
Document doc = new Document("document_with_images.docx");

// Set the images folder path
MarkdownSaveOptions saveOptions = new MarkdownSaveOptions();
saveOptions.setImagesFolder("images_folder/");

// Save the document with images
doc.save("document_with_images.md", saveOptions);
```

เปลี่ยน `"document_with_images.docx"` ให้เป็นพาธไปยังไฟล์ต้นฉบับของคุณและ `"images_folder/"` ให้เป็นตำแหน่งที่คุณต้องการเก็บรูปภาพ. Markdown ที่ได้จะมีลิงก์รูปภาพที่ชี้ไปยังโฟลเดอร์นี้, ทำให้คุณ **จัดการรูปภาพใน markdown** ได้อย่างราบรื่น.

## โค้ดต้นฉบับเต็มสำหรับการบันทึกเอกสารเป็น Markdown ด้วย Aspose.Words สำหรับ Java

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
	// Makes all paragraphs inside the table to be aligned.
	MarkdownSaveOptions saveOptions = new MarkdownSaveOptions();
	{
		saveOptions.setTableContentAlignment(TableContentAlignment.LEFT);
	}
	doc.save("Your Directory Path" + "WorkingWithMarkdownSaveOptions.LeftTableContentAlignment.md", saveOptions);
	saveOptions.setTableContentAlignment(TableContentAlignment.RIGHT);
	doc.save("Your Directory Path" + "WorkingWithMarkdownSaveOptions.RightTableContentAlignment.md", saveOptions);
	saveOptions.setTableContentAlignment(TableContentAlignment.CENTER);
	doc.save("Your Directory Path" + "WorkingWithMarkdownSaveOptions.CenterTableContentAlignment.md", saveOptions);
	// The alignment in this case will be taken from the first paragraph in corresponding table column.
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

## ปัญหาที่พบบ่อยและวิธีแก้

| Issue | Solution |
|-------|----------|
| Images not appearing in the `.md` file | Verify that `setImagesFolder` points to a writable directory and that the folder is referenced correctly in the generated Markdown. |
| Table alignment looks off | Use `TableContentAlignment.AUTO` to let Aspose.Words infer the best alignment based on the first paragraph of each column. |
| Output file is empty | Ensure the `Document` object actually contains content before calling `save`. |

## คำถามที่พบบ่อย

**Q: How do I install Aspose.Words for Java?**  
A: Aspose.Words for Java can be installed by including the library in your Java project. You can download the library from [here](https://releases.aspose.com/words/java/) and follow the installation instructions provided in the documentation.

**Q: Can I convert complex Word documents with tables and images to Markdown?**  
A: Yes, Aspose.Words for Java supports the conversion of complex Word documents with tables, images, and various formatting elements to Markdown. You can customize the Markdown output according to your document’s complexity.

**Q: How can I handle images in Markdown files?**  
A: Set the images folder path using the `setImagesFolder` method in `MarkdownSaveOptions`. Ensure that the image files are stored in the specified folder; Aspose.Words will generate the appropriate Markdown image links.

**Q: Is there a trial version of Aspose.Words for Java available?**  
A: Yes, you can obtain a trial version of Aspose.Words for Java from the Aspose website. The trial version allows you to evaluate the library’s capabilities before purchasing a license.

**Q: Where can I find more examples and documentation?**  
A: For more examples, documentation, and detailed information on Aspose.Words for Java, please visit the [documentation](https://reference.aspose.com/words/java/).

---

**Last Updated:** 2025-12-22  
**Tested With:** Aspose.Words for Java 24.12 (latest at time of writing)  
**Author:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}