---
date: 2025-12-27
description: เรียนรู้วิธีตั้งทิศทาง โหลดไฟล์ txt ตัดช่องว่าง และแปลง txt เป็น docx
  ด้วย Aspose.Words สำหรับ Java
linktitle: Loading Text Files with
second_title: Aspose.Words Java Document Processing API
title: วิธีตั้งทิศทางและโหลดไฟล์ข้อความด้วย Aspose.Words สำหรับ Java
url: /th/java/document-loading-and-saving/loading-text-files/
weight: 13
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# วิธีตั้งค่าทิศทางและโหลดไฟล์ข้อความด้วย Aspose.Words สำหรับ Java

## บทนำการโหลดไฟล์ข้อความด้วย Aspose.Words สำหรับ Java

ในคู่มือนี้ คุณจะได้ค้นพบ **วิธีตั้งค่าทิศทาง** เมื่อโหลดเอกสารข้อความธรรมดาและดูวิธีการปฏิบัติในการ **โหลด txt**, **ตัดช่องว่าง**, และ **แปลง txt เป็น docx** ด้วย Aspose.Words สำหรับ Java ไม่ว่าคุณจะสร้างบริการแปลงเอกสารหรือจำเป็นต้องควบคุมการตรวจจับรายการอย่างละเอียด คู่มือนี้จะพาคุณผ่านทุกขั้นตอนพร้อมคำอธิบายที่ชัดเจนและโค้ดที่พร้อมรัน

## คำตอบสั้น ๆ
- **ฉันจะตั้งค่าทิศทางข้อความสำหรับไฟล์ TXT ที่โหลดแล้วอย่างไร?** ใช้ `TxtLoadOptions.setDocumentDirection(DocumentDirection.AUTO)` หรือระบุ `LEFT_TO_RIGHT` / `RIGHT_TO_LEFT`
- **Aspose.Words สามารถตรวจจับรายการลำดับเลขในข้อความธรรมดาได้หรือไม่?** ได้ – เปิดใช้งาน `DetectNumberingWithWhitespaces` ใน `TxtLoadOptions`
- **ฉันจะตัดช่องว่างหน้าหลังได้อย่างไร?** ตั้งค่า `TxtLeadingSpacesOptions.TRIM` และ `TxtTrailingSpacesOptions.TRIM`
- **สามารถแปลงไฟล์ TXT เป็น DOCX ได้ในบรรทัดเดียวหรือไม่?** โหลด TXT ด้วย `TxtLoadOptions` แล้วเรียก `Document.save("output.docx")`
- **ต้องการเวอร์ชัน Java ใด?** Java 8+ เพียงพอสำหรับ Aspose.Words 24.x

## “วิธีตั้งค่าทิศทาง” ใน Aspose.Words คืออะไร?
เมื่อไฟล์ข้อความมีสคริปต์จากขวาไปซ้าย (เช่น ฮีบรูหรืออารบิก) ไลบรารีต้องรู้ลำดับการอ่าน `DocumentDirection` enum ช่วยให้คุณ **ตั้งค่าทิศทาง** ด้วยตนเองหรือให้ Aspose ตรวจจับอัตโนมัติ เพื่อให้การจัดวางและการฟอร์แมตแบบ bidi ถูกต้อง

## ทำไมต้องใช้ Aspose.Words สำหรับการโหลดไฟล์ TXT?
- **การตรวจจับรายการที่แม่นยำ** – รองรับรายการลำดับเลข, รายการหัวข้อ, และรายการที่คั่นด้วยช่องว่าง
- **การจัดการช่องว่างอย่างละเอียด** – ตัดหรือคงรักษาช่องว่างหน้าหลัง
- **การตรวจจับทิศทางข้อความอัตโนมัติ** – เหมาะสำหรับเอกสารหลายภาษา
- **การแปลงขั้นตอนเดียว** – โหลด `.txt` แล้วบันทึกเป็น `.docx`, `.pdf` หรือรูปแบบที่รองรับอื่น ๆ

## ข้อกำหนดเบื้องต้น
- Java 8 หรือใหม่กว่า
- ไลบรารี Aspose.Words สำหรับ Java (เพิ่ม dependency ของ Maven/Gradle หรือ JAR ลงในโปรเจค)
- ความรู้พื้นฐานเกี่ยวกับ Java I/O streams

## คู่มือแบบขั้นตอน

### ขั้นตอนที่ 1: การตรวจจับรายการ (วิธีโหลด txt)
เพื่อโหลดเอกสารข้อความและตรวจจับรายการโดยอัตโนมัติ ให้สร้างอินสแตนซ์ของ `TxtLoadOptions` แล้วเปิดใช้งานการตรวจจับรายการ โค้ดด้านล่างแสดงสไตล์รายการหลายแบบและเปิดใช้งานการนับเลขที่คำนึงถึงช่องว่าง

```java
// Create a plaintext document in the form of a string with parts that may be interpreted as lists.
// Upon loading, the first three lists will always be detected by Aspose.Words,
// and List objects will be created for them after loading.
final String TEXT_DOC = "Full stop delimiters:\n" +
        "1. First list item 1\n" +
        "2. First list item 2\n" +
        "3. First list item 3\n\n" +
        "Right bracket delimiters:\n" +
        "1) Second list item 1\n" +
        "2) Second list item 2\n" +
        "3) Second list item 3\n\n" +
        "Bullet delimiters:\n" +
        "• Third list item 1\n" +
        "• Third list item 2\n" +
        "• Third list item 3\n\n" +
        "Whitespace delimiters:\n" +
        "1 Fourth list item 1\n" +
        "2 Fourth list item 2\n" +
        "3 Fourth list item 3";
// The fourth list, with whitespace in between the list number and list item contents,
// will only be detected as a list if "DetectNumberingWithWhitespaces" in a LoadOptions object is set to true,
// to avoid paragraphs that start with numbers being mistakenly detected as lists.
TxtLoadOptions loadOptions = new TxtLoadOptions();
{
    loadOptions.setDetectNumberingWithWhitespaces(true);
}
// Load the document while applying LoadOptions as a parameter and verify the result.
Document doc = new Document(new ByteArrayInputStream(TEXT_DOC.getBytes()), loadOptions);
doc.save("Your Directory Path" + "WorkingWithTxtLoadOptions.DetectNumberingWithWhitespaces.docx");
```

> **เคล็ดลับ:** หากคุณต้องการการตรวจจับรายการพื้นฐานเท่านั้น สามารถข้ามตัวเลือกช่องว่าง – Aspose จะยังคงรับรู้รูปแบบ `1.` และ `1)` มาตรฐานได้

### ขั้นตอนที่ 2: การจัดการตัวเลือกช่องว่าง (วิธีตัดช่องว่าง)
ช่องว่างหน้าหลังมักทำให้รูปแบบผิดพลาด ใช้ `TxtLeadingSpacesOptions` และ `TxtTrailingSpacesOptions` เพื่อควบคุมพฤติกรรมนี้

```java
@Test
public void handleSpacesOptions() throws Exception {
    final String TEXT_DOC = "      Line 1 \n" +
            "    Line 2   \n" +
            " Line 3       ";
    TxtLoadOptions loadOptions = new TxtLoadOptions();
    {
        loadOptions.setLeadingSpacesOptions(TxtLeadingSpacesOptions.TRIM);
        loadOptions.setTrailingSpacesOptions(TxtTrailingSpacesOptions.TRIM);
    }
    Document doc = new Document(new ByteArrayInputStream(TEXT_DOC.getBytes()), loadOptions);
    doc.save("Your Directory Path" + "WorkingWithTxtLoadOptions.HandleSpacesOptions.docx");
}
```

> **ทำไมถึงสำคัญ:** การตัดช่องว่างช่วยป้องกันการเยื้องที่ไม่ต้องการใน DOCX ที่ได้ ทำให้เอกสารดูเรียบร้อยโดยไม่ต้องทำการปรับแต่งด้วยมือหลังจากแปลง

### ขั้นตอนที่ 3: การควบคุมทิศทางข้อความ (วิธีตั้งค่าทิศทาง)
สำหรับภาษาที่อ่านจากขวาไปซ้าย ให้ตั้งค่าทิศทางของเอกสารก่อนการโหลด ตัวอย่างด้านล่างโหลดไฟล์ข้อความฮีบรูและพิมพ์ค่า bidi เพื่อตรวจสอบทิศทาง

```java
@Test
public void documentTextDirection() throws Exception {
    TxtLoadOptions loadOptions = new TxtLoadOptions();
    {
        loadOptions.setDocumentDirection(DocumentDirection.AUTO);
    }
    Document doc = new Document("Your Directory Path" + "Hebrew text.txt", loadOptions);
    Paragraph paragraph = doc.getFirstSection().getBody().getFirstParagraph();
    System.out.println(paragraph.getParagraphFormat().getBidi());
    doc.save("Your Directory Path" + "WorkingWithTxtLoadOptions.DocumentTextDirection.docx");
}
```

> **ข้อผิดพลาดทั่วไป:** ลืมตั้งค่า `DocumentDirection` จะทำให้ข้อความอารบิก/ฮีบรูแสดงผลเป็นอักษรผกผันหรือเรียงลำดับผิด

### โค้ดต้นฉบับเต็มสำหรับการโหลดไฟล์ข้อความด้วย Aspose.Words สำหรับ Java
ด้านล่างเป็นโค้ดเต็มพร้อมรันที่รวมการตรวจจับรายการ, การจัดการช่องว่าง, และการควบคุมทิศทาง คุณสามารถคัดลอกวางลงในคลาสเดียวและรันเมธอดทดสอบสามเมธอดแยกกัน

```java
public void detectNumberingWithWhitespaces() throws Exception {
	// Create a plaintext document in the form of a string with parts that may be interpreted as lists.
	// Upon loading, the first three lists will always be detected by Aspose.Words,
	// and List objects will be created for them after loading.
	final String TEXT_DOC = "Full stop delimiters:\n" +
			"1. First list item 1\n" +
			"2. First list item 2\n" +
			"3. First list item 3\n\n" +
			"Right bracket delimiters:\n" +
			"1) Second list item 1\n" +
			"2) Second list item 2\n" +
			"3) Second list item 3\n\n" +
			"Bullet delimiters:\n" +
			"• Third list item 1\n" +
			"• Third list item 2\n" +
			"• Third list item 3\n\n" +
			"Whitespace delimiters:\n" +
			"1 Fourth list item 1\n" +
			"2 Fourth list item 2\n" +
			"3 Fourth list item 3";
	// The fourth list, with whitespace inbetween the list number and list item contents,
	// will only be detected as a list if "DetectNumberingWithWhitespaces" in a LoadOptions object is set to true,
	// to avoid paragraphs that start with numbers being mistakenly detected as lists.
	TxtLoadOptions loadOptions = new TxtLoadOptions();
	{
		loadOptions.setDetectNumberingWithWhitespaces(true);
	}
	// Load the document while applying LoadOptions as a parameter and verify the result.
	Document doc = new Document(new ByteArrayInputStream(TEXT_DOC.getBytes()), loadOptions);
	doc.save("Your Directory Path" + "WorkingWithTxtLoadOptions.DetectNumberingWithWhitespaces.docx");
}
@Test
public void handleSpacesOptions() throws Exception {
	final String TEXT_DOC = "      Line 1 \n" +
			"    Line 2   \n" +
			" Line 3       ";
	TxtLoadOptions loadOptions = new TxtLoadOptions();
	{
		loadOptions.setLeadingSpacesOptions(TxtLeadingSpacesOptions.TRIM);
		loadOptions.setTrailingSpacesOptions(TxtTrailingSpacesOptions.TRIM);
	}
	Document doc = new Document(new ByteArrayInputStream(TEXT_DOC.getBytes()), loadOptions);
	doc.save("Your Directory Path" + "WorkingWithTxtLoadOptions.HandleSpacesOptions.docx");
}
@Test
public void documentTextDirection() throws Exception {
	TxtLoadOptions loadOptions = new TxtLoadOptions();
	{
		loadOptions.setDocumentDirection(DocumentDirection.AUTO);
	}
	Document doc = new Document("Your Directory Path" + "Hebrew text.txt", loadOptions);
	Paragraph paragraph = doc.getFirstSection().getBody().getFirstParagraph();
	System.out.println(paragraph.getParagraphFormat().getBidi());
	doc.save("Your Directory Path" + "WorkingWithTxtLoadOptions.DocumentTextDirection.docx");
	}
```

## ปัญหาทั่วไปและวิธีแก้
| ปัญหา | สาเหตุ | วิธีแก้ |
|-------|-------|-----|
| รายการไม่ถูกตรวจจับ | `DetectNumberingWithWhitespaces` ถูกตั้งค่าเป็น `false` สำหรับรายการที่คั่นด้วยช่องว่าง | เปิดใช้งาน `loadOptions.setDetectNumberingWithWhitespaces(true)` |
| มีการเยื้องเพิ่มหลังการโหลด | ช่องว่างหน้าถูกเก็บไว้ | ตั้งค่า `TxtLeadingSpacesOptions.TRIM` |
| ข้อความฮีบรูแสดงผลย้อนกลับ | ไม่ได้ตั้งค่า DocumentDirection หรือตั้งค่าเป็น `LEFT_TO_RIGHT` | ใช้ `DocumentDirection.AUTO` หรือ `RIGHT_TO_LEFT` |
| DOCX ผลลัพธ์ว่างเปล่า | สตรีมอินพุตไม่ได้รีเซ็ตก่อนการโหลดครั้งที่สอง | สร้าง `ByteArrayInputStream` ใหม่สำหรับแต่ละการเรียกโหลด |

## คำถามที่พบบ่อย

### Q: Aspose.Words สำหรับ Java คืออะไร?
A: Aspose.Words สำหรับ Java เป็นไลบรารีการประมวลผลเอกสารที่ทรงพลัง ช่วยให้นักพัฒนาสร้าง, แก้ไข, และแปลงเอกสาร Word ผ่านโค้ด Java รองรับฟีเจอร์หลากหลาย ตั้งแต่การโหลดข้อความง่าย ๆ ไปจนถึงการจัดรูปแบบและการแปลงที่ซับซ้อน

### Q: จะเริ่มต้นใช้ Aspose.Words สำหรับ Java อย่างไร?
A: 1. ดาวน์โหลดและติดตั้งไลบรารี Aspose.Words สำหรับ Java 2. ดูเอกสารที่ [Aspose.Words for Java API Reference](https://reference.aspose.com/words/java/) เพื่อรับข้อมูลและตัวอย่างอย่างละเอียด 3. สำรวจโค้ดตัวอย่างและบทเรียนเพื่อเรียนรู้การใช้ไลบรารีอย่างมีประสิทธิภาพ

### Q: วิธีโหลดเอกสารข้อความโดยใช้ Aspose.Words สำหรับ Java คืออะไร?
A: ใช้คลาส `TxtLoadOptions` ร่วมกับคอนสตรัคเตอร์ของ `Document` ระบุอ็อปชันเช่นการตรวจจับรายการ, การจัดการช่องว่าง, หรือทิศทางข้อความตามที่แสดงในส่วนขั้นตอนด้านบน

### Q: สามารถแปลงเอกสารข้อความที่โหลดแล้วเป็นรูปแบบอื่นได้หรือไม่?
A: ได้ หลังจากโหลดไฟล์ TXT เข้าเป็นอ็อบเจ็กต์ `Document` แล้วเรียก `doc.save("output.pdf")`, `doc.save("output.docx")` หรือรูปแบบที่รองรับอื่น ๆ

### Q: วิธีจัดการช่องว่างในเอกสารข้อความที่โหลดคืออะไร?
A: ควบคุมช่องว่างหน้าหลังด้วย `TxtLeadingSpacesOptions` และ `TxtTrailingSpacesOptions` ตั้งค่าเป็น `TRIM` เพื่อลบช่องว่างที่ไม่ต้องการ หรือ `PRESERVE` หากต้องการคงช่องว่างเดิมไว้

### Q: ความสำคัญของทิศทางข้อความใน Aspose.Words สำหรับ Java คืออะไร?
A: ทิศทางข้อความทำให้สคริปต์จากขวาไปซ้าย (ฮีบรู, อารบิก ฯลฯ) แสดงผลถูกต้อง โดยการตั้งค่า `DocumentDirection` คุณจะมั่นใจว่าข้อความ bidi แสดงผลอย่างเหมาะสมในเอกสารที่สร้างขึ้น

### Q: จะหาแหล่งข้อมูลและการสนับสนุนเพิ่มเติมสำหรับ Aspose.Words สำหรับ Java ได้จากที่ไหน?
A: เยี่ยมชม [Aspose.Words for Java Documentation](https://reference.aspose.com/words/java/) เพื่อดู API reference, ตัวอย่างโค้ด, และคู่มือโดยละเอียด คุณยังสามารถเข้าร่วมฟอรั่มชุมชนของ Aspose หรือ ติดต่อฝ่ายสนับสนุนของ Aspose สำหรับคำถามเฉพาะได้

### Q: Aspose.Words สำหรับ Java เหมาะกับโครงการเชิงพาณิชย์หรือไม่?
A: ใช่ มีตัวเลือกการให้ลิขสิทธิ์ทั้งแบบส่วนบุคคลและเชิงพาณิชย์ ตรวจสอบเงื่อนไขการให้ลิขสิทธิ์บนเว็บไซต์ Aspose เพื่อเลือกแผนที่เหมาะสมกับโครงการของคุณ

## สรุป
คุณมีชุดเครื่องมือครบถ้วนเพื่อ **โหลดไฟล์ txt**, **ตรวจจับรายการ**, **ตัดช่องว่าง**, และ **ตั้งค่าทิศทาง** เมื่อแปลงข้อความธรรมดาเป็นเอกสาร Word ที่มีความสมบูรณ์ด้วย Aspose.Words สำหรับ Java นำรูปแบบเหล่านี้ไปใช้เพื่ออัตโนมัติกระบวนการทำงานกับเอกสาร, ปรับปรุงการรองรับหลายภาษา, และรับประกันผลลัพธ์ที่สะอาดและเป็นมืออาชีพทุกครั้ง

---

**อัปเดตล่าสุด:** 2025-12-27  
**ทดสอบด้วย:** Aspose.Words for Java 24.12  
**ผู้เขียน:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}