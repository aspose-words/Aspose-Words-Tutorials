---
title: ขั้นสูงตัวเลือกการบันทึกเอกสาร HTML ด้วย Aspose.Words Java
linktitle: การบันทึกเอกสาร HTML ด้วย
second_title: API การประมวลผลเอกสาร Java ของ Aspose.Words
description: ในบทช่วยสอนนี้ เราได้กล่าวถึงตัวเลือกการบันทึกเอกสาร HTML ขั้นสูงต่างๆ ด้วย Aspose.Words สำหรับ Java ตัวเลือกเหล่านี้ช่วยให้คุณสามารถสร้าง HTML คุณภาพสูงได้
weight: 16
url: /th/java/document-loading-and-saving/advance-html-documents-saving-options/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# ขั้นสูงตัวเลือกการบันทึกเอกสาร HTML ด้วย Aspose.Words Java


ในบทช่วยสอนนี้ เราจะมาสำรวจตัวเลือกการบันทึกเอกสาร HTML ขั้นสูงที่ Aspose.Words สำหรับ Java นำเสนอ Aspose.Words เป็น Java API ที่ทรงพลังสำหรับการทำงานกับเอกสาร Word และมีคุณสมบัติมากมายสำหรับการจัดการและแปลงเอกสาร

## 1. บทนำ
Aspose.Words สำหรับ Java ช่วยให้คุณสามารถทำงานกับเอกสาร Word ได้ด้วยการเขียนโปรแกรม ในบทช่วยสอนนี้ เราจะเน้นที่ตัวเลือกการบันทึกเอกสาร HTML ขั้นสูง ซึ่งช่วยให้คุณควบคุมวิธีการแปลงเอกสาร Word เป็น HTML ได้

## 2. ข้อมูลการส่งออกไปกลับ
 การ`exportRoundtripInformation` วิธีการนี้ช่วยให้คุณสามารถส่งออกเอกสาร Word เป็นรูปแบบ HTML โดยที่ยังคงรักษาข้อมูลการเดินทางกลับไว้ ข้อมูลนี้อาจมีประโยชน์เมื่อคุณต้องการแปลง HTML กลับเป็นรูปแบบ Word โดยไม่สูญเสียรายละเอียดเฉพาะของเอกสารใดๆ

```java
public void exportRoundtripInformation() throws Exception {
    Document doc = new Document("Your Directory Path" + "Rendering.docx");
    HtmlSaveOptions saveOptions = new HtmlSaveOptions();
    saveOptions.setExportRoundtripInformation(true);
    doc.save("Your Directory Path" + "WorkingWithHtmlSaveOptions.ExportRoundtripInformation.html", saveOptions);
}
```

## 3. ส่งออกแบบอักษรเป็น Base64
 ด้วย`exportFontsAsBase64` วิธีการนี้ช่วยให้คุณส่งออกแบบอักษรที่ใช้ในเอกสารเป็นข้อมูลที่เข้ารหัส Base64 ในรูปแบบ HTML ได้ วิธีนี้จะช่วยให้การแสดง HTML ยังคงใช้แบบอักษรเดียวกันกับเอกสาร Word ต้นฉบับ

```java

public void exportFontsAsBase64() throws Exception {
    Document doc = new Document("Your Directory Path" + "Rendering.docx");
    HtmlSaveOptions saveOptions = new HtmlSaveOptions();
    saveOptions.setExportFontsAsBase64(true);
    doc.save("Your Directory Path" + "WorkingWithHtmlSaveOptions.ExportFontsAsBase64.html", saveOptions);
}
```

## 4. การส่งออกทรัพยากร
 การ`exportResources` วิธีการนี้ช่วยให้คุณระบุประเภทของสไตล์ชีต CSS และส่งออกทรัพยากรแบบอักษรได้ นอกจากนี้ คุณยังสามารถตั้งค่าโฟลเดอร์ทรัพยากรและนามแฝงสำหรับทรัพยากรใน HTML ได้อีกด้วย

```java

public void exportResources() throws Exception {
    Document doc = new Document("Your Directory Path" + "Rendering.docx");
    HtmlSaveOptions saveOptions = new HtmlSaveOptions();
    saveOptions.setCssStyleSheetType(CssStyleSheetType.EXTERNAL);
    saveOptions.setExportFontResources(true);
    saveOptions.setResourceFolder("Your Directory Path" + "Resources");
    saveOptions.setResourceFolderAlias("http://example.com/resources);
    doc.save("Your Directory Path" + "WorkingWithHtmlSaveOptions.ExportResources.html", saveOptions);
}
```

## 5. แปลง Metafile เป็น EMF หรือ WMF
 การ`convertMetafilesToEmfOrWmf`วิธีการนี้ช่วยให้คุณแปลงเมตาไฟล์ในเอกสารให้เป็นรูปแบบ EMF หรือ WMF ช่วยให้มั่นใจถึงความเข้ากันได้และการแสดงผลใน HTML ราบรื่น

```java

public void convertMetafilesToEmfOrWmf() throws Exception {

	string dataDir = "Your Document Directory";
    Document doc = new Document();
	DocumentBuilder builder = new DocumentBuilder(doc);

	builder.write("Here is an image as is: ");
	builder.insertHtml(
		"<img src=\"data:image/png;base64,\r\n                    iVBORw0KGgoAAAANSUhEUgAAAAoAAAAKCAYAAACNMs+9AAAABGdBTUEAALGP\r\n                    C/xhBQAAAAlwSFlzAAALEwAACxMBAJqcGAAAAAd0SU1FB9YGARc5KB0XV+IA\r\n                    AAAddEVYdENvbW1lbnQAQ3JlYXRlZCB3aXRoIFRoZSBHSU1Q72QlbgAAAF1J\r\n                    REFUGNO9zL0NglAAxPEfdLTs4BZM4DIO4C7OwQg2JoQ9LE1exdlYvBBeZ7jq\r\n                    ch9//q1uH4TLzw4d6+ErXMMcXuHWxId3KOETnnXXV6MJpcq2MLaI97CER3N0\r\n vr4MkhoXe0rZigAAAABJRU5ErkJggg==\" alt=\"จุดสีแดง\" />");

	HtmlSaveOptions saveOptions = new HtmlSaveOptions(); { saveOptions.setMetafileFormat(HtmlMetafileFormat.EMF_OR_WMF); }

	doc.save(dataDir + "WorkingWithHtmlSaveOptions.ConvertMetafilesToEmfOrWmf.html", saveOptions);
}
```

## 6. แปลงไฟล์ Metafile เป็น SVG
 ใช้`convertMetafilesToSvg` วิธีการแปลงไฟล์เมตาเป็นรูปแบบ SVG ซึ่งรูปแบบนี้เหมาะสำหรับการแสดงกราฟิกแบบเวกเตอร์ในเอกสาร HTML

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

## 7. เพิ่มคำนำหน้าชื่อคลาส CSS
 ด้วย`addCssClassNamePrefix` คุณสามารถเพิ่มคำนำหน้าให้กับชื่อคลาส CSS ใน HTML ที่ส่งออกได้ ซึ่งจะช่วยป้องกันความขัดแย้งกับรูปแบบที่มีอยู่

```java

public void addCssClassNamePrefix() throws Exception {
    Document doc = new Document("Your Directory Path" + "Rendering.docx");
    HtmlSaveOptions saveOptions = new HtmlSaveOptions();
    saveOptions.setCssStyleSheetType(CssStyleSheetType.EXTERNAL);
    saveOptions.setCssClassNamePrefix("pfx_");
    doc.save("Your Directory Path" + "WorkingWithHtmlSaveOptions.AddCssClassNamePrefix.html", saveOptions);
}
```

## 8. ส่งออก URL CID สำหรับทรัพยากร MHTML
 การ`exportCidUrlsForMhtmlResources` วิธีนี้ใช้เมื่อบันทึกเอกสารในรูปแบบ MHTML ช่วยให้สามารถส่งออก URL Content-ID สำหรับทรัพยากรได้

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

## 9. แก้ไขชื่อแบบอักษร
 การ`resolveFontNames` วิธีการนี้ช่วยแก้ไขชื่อแบบอักษรเมื่อบันทึกเอกสารในรูปแบบ HTML ช่วยให้มั่นใจว่าการแสดงผลจะสอดคล้องกันในแพลตฟอร์มต่างๆ

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

## 10. ส่งออกฟอร์มป้อนข้อความเป็นข้อความ
 การ`exportTextInputFormFieldAsText`วิธีการส่งออกฟอร์มฟิลด์เป็นข้อความธรรมดาใน HTML ทำให้สามารถอ่านและแก้ไขได้ง่าย

```java

public void exportTextInputFormFieldAsText() throws Exception {
    
	string dataDir = "Your Document Directory";
	Document doc = new Document(dataDir + "Rendering.docx");

	String imagesDir = Path.combine(dataDir, "Images");

	// โฟลเดอร์ที่ระบุจำเป็นต้องมีอยู่และควรจะว่างเปล่า
	if (Directory.exists(imagesDir))
		Directory.delete(imagesDir, true);

	Directory.createDirectory(imagesDir);

	// ตั้งค่าตัวเลือกในการส่งออกฟิลด์ฟอร์มเป็นข้อความธรรมดา ไม่ใช่องค์ประกอบอินพุต HTML
	HtmlSaveOptions saveOptions = new HtmlSaveOptions(SaveFormat.HTML);
	{
		saveOptions.setExportTextInputFormFieldAsText(true); saveOptions.setImagesFolder(imagesDir);
	}

	doc.save(dataDir + "WorkingWithHtmlSaveOptions.ExportTextInputFormFieldAsText.html", saveOptions);
}
```

## บทสรุป
ในบทช่วยสอนนี้ เราได้สำรวจตัวเลือกการบันทึกเอกสาร HTML ขั้นสูงที่ Aspose.Words สำหรับ Java จัดเตรียมไว้ ตัวเลือกเหล่านี้ช่วยให้คุณควบคุมกระบวนการแปลงได้อย่างละเอียด ช่วยให้คุณสร้างเอกสาร HTML ที่คล้ายกับเอกสาร Word ต้นฉบับได้อย่างใกล้ชิด

## คำถามที่พบบ่อย
ต่อไปนี้คือคำถามที่พบบ่อยเกี่ยวกับการทำงานกับ Aspose.Words สำหรับ Java และตัวเลือกการบันทึกเอกสาร HTML:

### คำถามที่ 1: ฉันจะแปลง HTML กลับเป็นรูปแบบ Word โดยใช้ Aspose.Words สำหรับ Java ได้อย่างไร
 หากต้องการแปลง HTML กลับเป็นรูปแบบ Word คุณสามารถใช้ API ของ Aspose.Words`load` วิธีการโหลดเอกสาร HTML และบันทึกเป็นรูปแบบ Word

### คำถามที่ 2: ฉันสามารถปรับแต่งรูปแบบ CSS เมื่อส่งออกเป็น HTML ได้หรือไม่
ใช่ คุณสามารถปรับแต่งรูปแบบ CSS ได้โดยการแก้ไขแผ่นสไตล์ที่ใช้ใน HTML หรือโดยใช้`addCssClassNamePrefix` วิธีการเพิ่มคำนำหน้าให้กับชื่อคลาส CSS

### คำถามที่ 3: มีวิธีเพิ่มประสิทธิภาพผลลัพธ์ HTML สำหรับการแสดงผลบนเว็บหรือไม่
ใช่ คุณสามารถเพิ่มประสิทธิภาพการแสดงผล HTML สำหรับการแสดงผลบนเว็บได้โดยการกำหนดค่าตัวเลือกเช่นการส่งออกแบบอักษรเป็น Base64 และการแปลงเมตาไฟล์เป็น SVG

### คำถามที่ 4: มีข้อจำกัดใด ๆ ในการแปลงเอกสาร Word ที่ซับซ้อนเป็น HTML หรือไม่
แม้ว่า Aspose.Words สำหรับ Java จะมีความสามารถในการแปลงไฟล์อันทรงพลัง แต่เอกสาร Word ที่ซับซ้อนซึ่งมีเค้าโครงที่ซับซ้อนอาจต้องมีการประมวลผลเพิ่มเติมหลังการประมวลผลเพื่อให้ได้ผลลัพธ์ HTML ตามต้องการ

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
