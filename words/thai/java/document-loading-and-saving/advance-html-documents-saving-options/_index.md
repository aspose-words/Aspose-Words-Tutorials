---
date: 2025-12-19
description: เรียนรู้วิธีส่งออก HTML ด้วย Aspose.Words Java พร้อมครอบคลุมตัวเลือกขั้นสูงในการบันทึกไฟล์
  Word เป็น HTML และแปลง Word เป็น HTML อย่างมีประสิทธิภาพ
linktitle: Saving HTML Documents with
second_title: Aspose.Words Java Document Processing API
title: 'วิธีส่งออก HTML ด้วย Aspose.Words Java: ตัวเลือกขั้นสูง'
url: /th/java/document-loading-and-saving/advance-html-documents-saving-options/
weight: 16
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# วิธีส่งออก HTML ด้วย Aspose.Words Java: ตัวเลือกขั้นสูง

ในบทแนะนำนี้คุณจะได้ค้นพบ **วิธีส่งออก HTML** จากเอกสาร Word ด้วย Aspose.Words for Java ไม่ว่าคุณจะต้องการ **บันทึก Word เป็น HTML** เพื่อเผยแพร่บนเว็บหรือ **แปลง Word เป็น HTML** เพื่อการประมวลผลต่อไป ตัวเลือกการบันทึกขั้นสูงจะให้การควบคุมที่ละเอียดอ่อนต่อผลลัพธ์ เราจะเดินผ่านแต่ละตัวเลือกทีละขั้นตอน อธิบายเมื่อใดควรใช้ และแสดงสถานการณ์จริงที่การตั้งค่าเหล่านี้ทำให้เกิดความแตกต่าง

## คำตอบสั้น
- **คลาสหลักสำหรับการส่งออก HTML คืออะไร?** `HtmlSaveOptions`  
- **ฟอนต์สามารถฝังโดยตรงใน HTML ได้หรือไม่?** ใช่, ตั้งค่า `exportFontsAsBase64` เป็น `true`.  
- **ฉันจะเก็บข้อมูล round‑trip ของ Word ไว้ได้อย่างไร?** เปิดใช้งาน `exportRoundtripInformation`.  
- **รูปแบบใดดีที่สุดสำหรับกราฟิกเวกเตอร์?** ใช้ `convertMetafilesToSvg` สำหรับเอาต์พุต SVG.  
- **สามารถหลีกเลี่ยงการชนกันของชื่อคลาส CSS ได้หรือไม่?** ใช่, ใช้ `addCssClassNamePrefix`.

## 1. Introduction
Aspose.Words for Java เป็น API ที่แข็งแกร่งซึ่งช่วยให้นักพัฒนาสามารถจัดการเอกสาร Word ด้วยโปรแกรมได้ คู่มือนี้มุ่งเน้นที่ตัวเลือกการบันทึกเอกสาร HTML ขั้นสูงที่ให้คุณปรับกระบวนการแปลงให้ตรงกับความต้องการเว็บหรือการบูรณาการเฉพาะ

## 2. Export Roundtrip Information
การเก็บข้อมูล round‑trip ช่วยให้คุณสามารถแปลง HTML กลับเป็นเอกสาร Word ได้โดยไม่สูญเสียรายละเอียดการจัดรูปแบบหรือเลย์เอาต์

```java
public void exportRoundtripInformation() throws Exception {
    Document doc = new Document("Your Directory Path" + "Rendering.docx");
    HtmlSaveOptions saveOptions = new HtmlSaveOptions();
    saveOptions.setExportRoundtripInformation(true);
    doc.save("Your Directory Path" + "WorkingWithHtmlSaveOptions.ExportRoundtripInformation.html", saveOptions);
}
```

### เมื่อใช้
- เมื่อคุณต้องการไพรเมตการแปลงที่ย้อนกลับได้ (HTML → Word → HTML).  
- เหมาะสำหรับสถานการณ์การแก้ไขร่วมกันที่ต้องคงโครงสร้าง Word ดั้งเดิมไว้

## 3. Export Fonts as Base64
การฝังฟอนต์โดยตรงลงใน HTML จะกำจัดการพึ่งพาฟอนต์ภายนอกและรับประกันความแม่นยำของการแสดงผลในทุกเบราว์เซอร์

```java

public void exportFontsAsBase64() throws Exception {
    Document doc = new Document("Your Directory Path" + "Rendering.docx");
    HtmlSaveOptions saveOptions = new HtmlSaveOptions();
    saveOptions.setExportFontsAsBase64(true);
    doc.save("Your Directory Path" + "WorkingWithHtmlSaveOptions.ExportFontsAsBase64.html", saveOptions);
}
```

### เคล็ดลับระดับมืออาชีพ
ใช้ตัวเลือกนี้เมื่อสภาพแวดล้อมเป้าหมายเข้าถึงทรัพยากรภายนอกได้จำกัด (เช่น จดหมายข่าวอีเมล).

## 4. Export Resources
ควบคุมวิธีการส่งออก CSS และทรัพยากรฟอนต์ และระบุโฟลเดอร์หรือ URL alias ที่กำหนดเองสำหรับทรัพยากรเหล่านั้น

```java

public void exportResources() throws Exception {
    Document doc = new Document("Your Directory Path" + "Rendering.docx");
    HtmlSaveOptions saveOptions = new HtmlSaveOptions();
    saveOptions.setCssStyleSheetType(CssStyleSheetType.EXTERNAL);
    saveOptions.setExportFontResources(true);
    saveOptions.setResourceFolder("Your Directory Path" + "Resources");
    saveOptions.setResourceFolderAlias("http://example.com/resources");
    doc.save("Your Directory Path" + "WorkingWithHtmlSaveOptions.ExportResources.html", saveOptions);
}
```

### ทำไมจึงสำคัญ
การแยก CSS ไปเป็นไฟล์ภายนอกช่วยลดขนาด HTML และทำให้สามารถแคชได้เพื่อการโหลดหน้าเว็บที่เร็วขึ้น

## 5. Convert Metafiles to EMF or WMF
เมตาฟายล์ (เช่น EMF/WMF) จะถูกแปลงเป็นรูปแบบที่เบราว์เซอร์สามารถเรนเดอร์ได้อย่างเชื่อถือได้

```java

public void convertMetafilesToEmfOrWmf() throws Exception {

	string dataDir = "Your Document Directory";
    Document doc = new Document();
	DocumentBuilder builder = new DocumentBuilder(doc);

	builder.write("Here is an image as is: ");
	builder.insertHtml(
		"<img src=\"data:image/png;base64,\r\n                    iVBORw0KGgoAAAANSUhEUgAAAAoAAAAKCAYAAACNMs+9AAAABGdBTUEAALGP\r\n                    C/xhBQAAAAlwSFlzAAALEwAACxMBAJqcGAAAAAd0SU1FB9YGARc5KB0XV+IA\r\n                    AAAddEVYdENvbW1lbnQAQ3JlYXRlZCB3aXRoIFRoZSBHSU1Q72QlbgAAAF1J\r\n                    REFUGNO9zL0NglAAxPEfdLTs4BZM4DIO4C7OwQg2JoQ9LE1exdlYvBBeZ7jq\r\n                    ch9//q1uH4TLzw4d6+ErXMMcXuHWxId3KOETnnXXV6MJpcq2MLaI97CER3N0\r\n                    vr4MkhoXe0rZigAAAABJRU5ErkJggg==\" alt=\"Red dot\" />");

	HtmlSaveOptions saveOptions = new HtmlSaveOptions(); { saveOptions.setMetafileFormat(HtmlMetafileFormat.EMF_OR_WMF); }

	doc.save(dataDir + "WorkingWithHtmlSaveOptions.ConvertMetafilesToEmfOrWmf.html", saveOptions);
}
```

### กรณีใช้งาน
เลือก EMF/WMF เมื่อเบราว์เซอร์เป้าหมายรองรับรูปแบบเวกเตอร์เหล่านี้และคุณต้องการการสเกลโดยไม่มีการสูญเสีย

## 6. Convert Metafiles to SVG
SVG ให้ความสามารถในการสเกลที่ดีที่สุดและได้รับการสนับสนุนอย่างกว้างขวางในเบราว์เซอร์สมัยใหม่

```java

public void convertMetafilesToSvg() throws Exception {
	string dataDir = "Your Document Directory";
    Document doc = new Document();
	DocumentBuilder builder = new DocumentBuilder(doc);
	
	builder.write("Here is an SVG image: ");
	builder.insertHtml(
		"<svg height='210' width='500'>\r\n                <polygon points='100,10 40,198 190,78 10,78 160,198' \r\n                    style='fill:lime;stroke:purple;stroke-width:5;fill-rule:evenodd;' />\r\n            </svg> ");

	HtmlSaveOptions saveOptions = new HtmlSaveOptions(); { saveOptions.setMetafileFormat(HtmlMetafileFormat.SVG); }

	doc.save(dataDir + "WorkingWithHtmlSaveOptions.ConvertMetafilesToSvg.html", saveOptions);
}
```

### ประโยชน์
ไฟล์ SVG มีน้ำหนักเบาและทำให้เอกสารไม่ขึ้นกับความละเอียด เหมาะสำหรับการออกแบบเว็บที่ตอบสนอง

## 7. Add CSS Class Name Prefix
ป้องกันการชนกันของสไตล์โดยการเพิ่มคำนำหน้าต่อชื่อคลาส CSS ทั้งหมดที่สร้างขึ้น

```java

public void addCssClassNamePrefix() throws Exception {
    Document doc = new Document("Your Directory Path" + "Rendering.docx");
    HtmlSaveOptions saveOptions = new HtmlSaveOptions();
    saveOptions.setCssStyleSheetType(CssStyleSheetType.EXTERNAL);
    saveOptions.setCssClassNamePrefix("pfx_");
    doc.save("Your Directory Path" + "WorkingWithHtmlSaveOptions.AddCssClassNamePrefix.html", saveOptions);
}
```

### เคล็ดลับการใช้งานจริง
ใช้คำนำหน้าที่ไม่ซ้ำกัน (เช่น ชื่อโปรเจกต์ของคุณ) เมื่อฝัง HTML ลงในหน้าเดิมเพื่อหลีกเลี่ยงความขัดแย้งของ CSS

## 8. Export CID URLs for MHTML Resources
เมื่อบันทึกเป็น MHTML คุณสามารถส่งออกทรัพยากรโดยใช้ URL แบบ Content‑ID เพื่อความเข้ากันได้กับอีเมลที่ดียิ่งขึ้น

```java

public void exportCidUrlsForMhtmlResources() throws Exception {
	string dataDir = "Your Document Directory";
    Document doc = new Document(dataDir + "Content-ID.docx");

	HtmlSaveOptions saveOptions = new HtmlSaveOptions(SaveFormat.MHTML);
	{
		saveOptions.setPrettyFormat(true); saveOptions.setExportCidUrlsForMhtmlResources(true);
	}

	doc.save(dataDir + "WorkingWithHtmlSaveOptions.ExportCidUrlsForMhtmlResources.mhtml", saveOptions);
}
```

### เมื่อใช้
เหมาะสำหรับการสร้างไฟล์ HTML เดียวที่รวมทุกอย่างและสามารถแนบไปกับอีเมลได้

## 9. Resolve Font Names
รับรองว่า HTML อ้างอิงฟอนต์ที่ถูกต้อง เพื่อปรับปรุงความสอดคล้องข้ามแพลตฟอร์ม

```java

public void resolveFontNames() throws Exception {
    
	string dataDir = "Your Document Directory";
	Document doc = new Document(dataDir + "Missing font.docx");

	HtmlSaveOptions saveOptions = new HtmlSaveOptions(SaveFormat.HTML);
	{
		saveOptions.setPrettyFormat(true); saveOptions.setResolveFontNames(true);
	}

	doc.save(dataDir + "WorkingWithHtmlSaveOptions.ResolveFontNames.html", saveOptions);
}
```

### ทำไมจึงช่วยได้
หากเอกสารต้นฉบับใช้ฟอนต์ที่ไม่ได้ติดตั้งบนเครื่องของผู้ใช้ ตัวเลือกนี้จะเปลี่ยนเป็นฟอนต์ที่ปลอดภัยสำหรับเว็บ

## 10. Export Text Input Form Field as Text
เรนเดอร์ฟิลด์ฟอร์มเป็นข้อความธรรมดาแทนที่จะเป็นองค์ประกอบอินพุต HTML ที่โต้ตอบได้

```java

public void exportTextInputFormFieldAsText() throws Exception {
    
	string dataDir = "Your Document Directory";
	Document doc = new Document(dataDir + "Rendering.docx");

	String imagesDir = Path.combine(dataDir, "Images");

	// The folder specified needs to exist and should be empty.
	if (Directory.exists(imagesDir))
		Directory.delete(imagesDir, true);

	Directory.createDirectory(imagesDir);

	// Set an option to export form fields as plain text, not as HTML input elements.
	HtmlSaveOptions saveOptions = new HtmlSaveOptions(SaveFormat.HTML);
	{
		saveOptions.setExportTextInputFormFieldAsText(true); saveOptions.setImagesFolder(imagesDir);
	}

	doc.save(dataDir + "WorkingWithHtmlSaveOptions.ExportTextInputFormFieldAsText.html", saveOptions);
}
```

### กรณีใช้งาน
เมื่อคุณต้องการการแสดงฟอร์มแบบอ่านอย่างเดียวเพื่อการเก็บถาวรหรือการพิมพ์

## ปัญหาทั่วไป & การแก้ไขข้อผิดพลาด
| ปัญหา | สาเหตุทั่วไป | วิธีแก้ |
|-------|---------------|----------|
| ฟอนต์หายในผลลัพธ์ | `exportFontsAsBase64` ไม่ได้เปิดใช้งาน | ตั้งค่า `setExportFontsAsBase64(true)` |
| CSS เสียหลังจากฝัง | ใช้ `EXTERNAL` โดยไม่ได้ให้ไฟล์ CSS | ตรวจสอบให้แน่ใจว่าไฟล์ CSS ถูกวางที่ `resourceFolderAlias` ที่ระบุ |
| ขนาด HTML ใหญ่ | ฝังรูปภาพหลายรูปเป็น Base64 | เปลี่ยนไปใช้ทรัพยากรรูปภาพภายนอกโดยใช้ `setExportFontResources(true)` และกำหนดค่า `resourceFolder` |
| SVG ไม่แสดงผลในเบราว์เซอร์เก่า | เบราว์เซอร์ไม่มีการสนับสนุน SVG | ให้ PNG สำรองโดยการส่งออกเป็น EMF/WMF ด้วย |

## คำถามที่พบบ่อย

**Q: ฉันสามารถฝังฟอนต์เป็น Base64 และยังคงใช้ CSS ภายนอกได้หรือไม่?**  
A: ใช่. ตั้งค่า `exportFontsAsBase64(true)` พร้อมกับคง `CssStyleSheetType.EXTERNAL` เพื่อแยกข้อมูลฟอนต์จากกฎสไตล์.

**Q: ฉันจะแปลง HTML ที่มีอยู่กลับเป็นเอกสาร Word ได้อย่างไร?**  
A: โหลด HTML ด้วย `Document doc = new Document("input.html");` แล้วใช้ `doc.save("output.docx");`. เก็บข้อมูล round‑trip ด้วยการใช้ `exportRoundtripInformation` ในการส่งออกครั้งแรก.

**Q: การแปลงเป็น SVG มีผลต่อประสิทธิภาพหรือไม่?**  
A: การแปลงเมตาฟายล์ขนาดใหญ่เป็น SVG อาจเพิ่มเวลาในการประมวลผล, แต่ HTML ที่ได้มักจะมีขนาดเล็กลงและแสดงผลเร็วขึ้นในเบราว์เซอร์.

**Q: ตัวเลือกเหล่านี้ทำงานกับ Aspose.Words for .NET ด้วยหรือไม่?**  
A: แนวคิดเดียวกันมีใน API ของ .NET แม้ว่าชื่อเมธอดอาจแตกต่างกันเล็กน้อย (เช่น `HtmlSaveOptions` ใช้ร่วมกันระหว่างแพลตฟอร์ม).

**Q: ควรเลือกตัวเลือกใดสำหรับ HTML ที่เหมาะกับอีเมล?**  
A: ใช้ `SaveFormat.MHTML` พร้อม `exportCidUrlsForMhtmlResources` เพื่อฝังทรัพยากรทั้งหมดโดยตรงในเนื้อหาอีเมล.

**อัปเดตล่าสุด:** 2025-12-19  
**ทดสอบกับ:** Aspose.Words for Java 24.12  
**ผู้เขียน:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}