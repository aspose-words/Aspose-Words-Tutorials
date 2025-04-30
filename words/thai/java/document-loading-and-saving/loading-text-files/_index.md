---
"description": "ปลดล็อกพลังของ Aspose.Words สำหรับ Java เรียนรู้การโหลดเอกสารข้อความ จัดการรายการ จัดการช่องว่าง และควบคุมทิศทางของข้อความ"
"linktitle": "การโหลดไฟล์ข้อความด้วย"
"second_title": "API การประมวลผลเอกสาร Java ของ Aspose.Words"
"title": "การโหลดไฟล์ข้อความด้วย Aspose.Words สำหรับ Java"
"url": "/th/java/document-loading-and-saving/loading-text-files/"
"weight": 13
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# การโหลดไฟล์ข้อความด้วย Aspose.Words สำหรับ Java


## บทนำสู่การโหลดไฟล์ข้อความด้วย Aspose.Words สำหรับ Java

ในคู่มือนี้ เราจะศึกษาวิธีการโหลดไฟล์ข้อความโดยใช้ Aspose.Words สำหรับ Java และจัดการไฟล์เหล่านั้นในรูปแบบเอกสาร Word เราจะครอบคลุมถึงประเด็นต่างๆ เช่น การตรวจจับรายการ การจัดการช่องว่าง และการควบคุมทิศทางของข้อความ

## ขั้นตอนที่ 1: การตรวจจับรายการ

หากต้องการโหลดเอกสารข้อความและตรวจจับรายการ คุณสามารถทำตามขั้นตอนเหล่านี้:

```java
// สร้างเอกสารข้อความธรรมดาในรูปแบบสตริงที่มีบางส่วนที่สามารถตีความได้ว่าเป็นรายการ
// เมื่อโหลดแล้ว สามรายการแรกจะถูกตรวจพบโดย Aspose.Words เสมอ
// และรายการวัตถุจะถูกสร้างขึ้นสำหรับพวกเขาหลังจากการโหลด
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
// รายการที่สี่ โดยมีช่องว่างระหว่างหมายเลขรายการและเนื้อหาของรายการ
// จะถูกตรวจพบเป็นรายการเท่านั้นหาก "DetectNumberingWithWhitespaces" ในอ็อบเจ็กต์ LoadOptions ถูกตั้งค่าเป็นจริง
// เพื่อหลีกเลี่ยงการตรวจพบย่อหน้าที่เริ่มต้นด้วยตัวเลขผิดพลาดว่าเป็นรายการ
TxtLoadOptions loadOptions = new TxtLoadOptions();
{
    loadOptions.setDetectNumberingWithWhitespaces(true);
}
// โหลดเอกสารในขณะที่ใช้ LoadOptions เป็นพารามิเตอร์และตรวจสอบผลลัพธ์
Document doc = new Document(new ByteArrayInputStream(TEXT_DOC.getBytes()), loadOptions);
doc.save("Your Directory Path" + "WorkingWithTxtLoadOptions.DetectNumberingWithWhitespaces.docx");
```

โค้ดนี้สาธิตวิธีการโหลดเอกสารข้อความที่มีรูปแบบรายการต่างๆ และใช้ `DetectNumberingWithWhitespaces` ตัวเลือกในการตรวจจับรายการอย่างถูกต้อง

## ขั้นตอนที่ 2: การจัดการตัวเลือกพื้นที่

หากต้องการควบคุมช่องว่างนำหน้าและต่อท้ายเมื่อโหลดเอกสารข้อความ คุณสามารถใช้โค้ดดังต่อไปนี้:

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

ในตัวอย่างนี้ เราโหลดเอกสารข้อความและตัดช่องว่างนำหน้าและต่อท้ายโดยใช้ `TxtLeadingSpacesOptions.TRIM` และ `TxtTrailingSpacesOptions-TRIM`.

## ขั้นตอนที่ 3: การควบคุมทิศทางข้อความ

หากต้องการระบุทิศทางข้อความเมื่อโหลดเอกสารข้อความ คุณสามารถใช้โค้ดดังต่อไปนี้:

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

รหัสนี้จะกำหนดทิศทางเอกสารให้ตรวจจับอัตโนมัติ (`DocumentDirection.AUTO`) และโหลดเอกสารข้อความที่มีข้อความภาษาฮีบรู คุณสามารถปรับทิศทางเอกสารได้ตามต้องการ

## โค้ดต้นฉบับสมบูรณ์สำหรับการโหลดไฟล์ข้อความด้วย Aspose.Words สำหรับ Java

```java
public void detectNumberingWithWhitespaces() throws Exception {
	// สร้างเอกสารข้อความธรรมดาในรูปแบบสตริงที่มีบางส่วนที่สามารถตีความได้ว่าเป็นรายการ
	// เมื่อโหลดแล้ว สามรายการแรกจะถูกตรวจพบโดย Aspose.Words เสมอ
	// และรายการวัตถุจะถูกสร้างขึ้นสำหรับพวกเขาหลังจากการโหลด
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
	// รายการที่สี่ โดยมีช่องว่างระหว่างหมายเลขรายการและเนื้อหาของรายการ
	// จะถูกตรวจพบเป็นรายการเท่านั้นหาก "DetectNumberingWithWhitespaces" ในอ็อบเจ็กต์ LoadOptions ถูกตั้งค่าเป็นจริง
	// เพื่อหลีกเลี่ยงการตรวจพบย่อหน้าที่เริ่มต้นด้วยตัวเลขผิดพลาดว่าเป็นรายการ
	TxtLoadOptions loadOptions = new TxtLoadOptions();
	{
		loadOptions.setDetectNumberingWithWhitespaces(true);
	}
	// โหลดเอกสารในขณะที่ใช้ LoadOptions เป็นพารามิเตอร์และตรวจสอบผลลัพธ์
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

## บทสรุป

ในคู่มือนี้ เราได้ศึกษาวิธีการโหลดไฟล์ข้อความโดยใช้ Aspose.Words สำหรับ Java การตรวจจับรายการ จัดการช่องว่าง และควบคุมทิศทางของข้อความ เทคนิคเหล่านี้ช่วยให้คุณสามารถจัดการเอกสารข้อความได้อย่างมีประสิทธิภาพในแอปพลิเคชัน Java ของคุณ

## คำถามที่พบบ่อย

### Aspose.Words สำหรับ Java คืออะไร?

Aspose.Words for Java เป็นไลบรารีประมวลผลเอกสารอันทรงพลังที่ช่วยให้นักพัฒนาสามารถสร้าง จัดการ และแปลงเอกสาร Word ในแอปพลิเคชัน Java ได้ด้วยโปรแกรม โดยมีคุณสมบัติมากมายสำหรับการทำงานกับข้อความ ตาราง รูปภาพ และองค์ประกอบเอกสารอื่นๆ

### ฉันจะเริ่มต้นใช้งาน Aspose.Words สำหรับ Java ได้อย่างไร?

หากต้องการเริ่มต้นใช้งาน Aspose.Words สำหรับ Java ให้ทำตามขั้นตอนเหล่านี้:
1. ดาวน์โหลดและติดตั้งไลบรารี Aspose.Words สำหรับ Java
2. ดูเอกสารประกอบได้ที่ [เอกสารอ้างอิง Aspose.Words สำหรับ Java API](https://reference.aspose.com/words/java/) สำหรับข้อมูลโดยละเอียดและตัวอย่าง
3. สำรวจโค้ดตัวอย่างและบทช่วยสอนเพื่อเรียนรู้วิธีใช้ไลบรารีอย่างมีประสิทธิภาพ

### ฉันจะโหลดเอกสารข้อความโดยใช้ Aspose.Words สำหรับ Java ได้อย่างไร

หากต้องการโหลดเอกสารข้อความโดยใช้ Aspose.Words สำหรับ Java คุณสามารถใช้ `TxtLoadOptions` ชั้นเรียนและ `Document` คลาส ตรวจสอบให้แน่ใจว่าคุณได้ระบุตัวเลือกที่เหมาะสมสำหรับการจัดการช่องว่างและทิศทางของข้อความตามต้องการ โปรดดูคำแนะนำทีละขั้นตอนในบทความนี้เพื่อดูตัวอย่างโดยละเอียด

### ฉันสามารถแปลงเอกสารข้อความที่โหลดเป็นรูปแบบอื่นได้หรือไม่

ใช่ Aspose.Words สำหรับ Java ช่วยให้คุณแปลงเอกสารข้อความที่โหลดเป็นรูปแบบต่างๆ รวมถึง DOCX, PDF และอื่นๆ คุณสามารถใช้ `Document` คลาสสำหรับทำการแปลง โปรดดูเอกสารสำหรับตัวอย่างการแปลงเฉพาะ

### ฉันจะจัดการช่องว่างในเอกสารข้อความที่โหลดได้อย่างไร

คุณสามารถควบคุมวิธีการจัดการช่องว่างนำหน้าและต่อท้ายในเอกสารข้อความที่โหลดได้โดยใช้ `TxtLoadOptions`. ตัวเลือกเช่น `TxtLeadingSpacesOptions` และ `TxtTrailingSpacesOptions` ช่วยให้คุณสามารถตัดแต่งหรือรักษาพื้นที่ได้ตามต้องการ ดูตัวอย่างในหัวข้อ "ตัวเลือกการจัดการพื้นที่" ในคู่มือนี้

### ความสำคัญของทิศทางข้อความใน Aspose.Words สำหรับ Java คืออะไร

ทิศทางของข้อความเป็นสิ่งสำคัญสำหรับเอกสารที่มีสคริปต์หรือภาษาผสม เช่น ภาษาฮีบรูหรืออาหรับ Aspose.Words สำหรับ Java มีตัวเลือกในการระบุทิศทางของข้อความ เพื่อให้แน่ใจว่าการแสดงผลและการจัดรูปแบบข้อความในภาษาเหล่านี้ถูกต้อง ส่วน "การควบคุมทิศทางของข้อความ" ในคู่มือนี้จะแสดงวิธีการตั้งค่าทิศทางของข้อความ

### ฉันสามารถหาทรัพยากรและการสนับสนุนเพิ่มเติมสำหรับ Aspose.Words สำหรับ Java ได้ที่ไหน

สำหรับทรัพยากร เอกสารประกอบ และการสนับสนุนเพิ่มเติม โปรดไปที่ [เอกสาร Aspose.Words สำหรับ Java](https://reference.aspose.com/words/java/)คุณยังสามารถเข้าร่วมฟอรัมชุมชน Aspose.Words หรือติดต่อฝ่ายสนับสนุน Aspose เพื่อขอความช่วยเหลือเกี่ยวกับปัญหาหรือคำถามเฉพาะได้

### Aspose.Words สำหรับ Java เหมาะกับโปรเจ็กต์เชิงพาณิชย์หรือไม่?

ใช่ Aspose.Words สำหรับ Java เหมาะสำหรับทั้งโครงการส่วนบุคคลและเชิงพาณิชย์ โดยมีตัวเลือกการออกใบอนุญาตเพื่อรองรับสถานการณ์การใช้งานต่างๆ อย่าลืมตรวจสอบเงื่อนไขการออกใบอนุญาตและราคาบนเว็บไซต์ Aspose เพื่อเลือกใบอนุญาตที่เหมาะสมสำหรับโครงการของคุณ


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}