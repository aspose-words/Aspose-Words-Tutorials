---
date: 2026-01-09
description: เรียนรู้วิธีสร้างรายการหลายระดับ ใช้สไตล์ย่อหน้า ตั้งค่าการจัดแนวย่อหน้า
  และสร้างเอกสาร Word ด้วย Aspose.Words for Java คู่มือนี้ครอบคลุมเทคนิคการจัดรูปแบบสำหรับเอกสารระดับมืออาชีพ
linktitle: Formatting Documents
second_title: Aspose.Words Java Document Processing API
title: วิธีสร้างรายการหลายระดับและจัดรูปแบบเอกสารใน Aspose.Words สำหรับ Java
url: /th/java/document-manipulation/formatting-documents/
weight: 29
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# การจัดรูปแบบเอกสารใน Aspose.Words for Java

## บทนำสู่การจัดรูปแบบเอกสารใน Aspose.Words for Java

ในโลกของการประมวลผลเอกสารด้วย Java, Aspose.Words for Java เป็นเครื่องมือที่แข็งแกร่งและหลากหลาย ไม่ว่าคุณจะสร้างรายงาน, ทำใบแจ้งหนี้, หรือออกแบบเลย์เอาต์ที่ซับซ้อน, คุณมักจะต้อง **สร้างรายการหลายระดับ** และใช้สไตล์ย่อหน้าที่ซับซ้อน คู่มือฉบับครอบคลุมนี้จะอธิบายวิธีการจัดรูปแบบเอกสาร, สร้างเอกสาร Word ตั้งแต่ต้น, และปรับแต่งการจัดแนวย่อหน้า, การเยื้องซ้าย, และรายละเอียดการพิมพ์อื่น ๆ มาเริ่มกันทีละขั้นตอน

## คำตอบอย่างรวดเร็ว
- **ฉันจะสร้างรายการหลายระดับได้อย่างไร?** ใช้ `DocumentBuilder.getListFormat().applyNumberDefault()` และเพิ่มรายการตามลำดับ.  
- **ฉันสามารถตั้งค่าการจัดแนวย่อหน้าได้หรือไม่?** ได้, เรียก `ParagraphFormat.setAlignment(ParagraphAlignment.CENTER)` หรือการจัดแนวอื่น ๆ.  
- **เมธอดใดที่เพิ่มการเยื้องซ้าย?** ใช้ `ParagraphFormat.setLeftIndent(double)` เพื่อกำหนดระยะเยื้องด้านซ้าย.  
- **ฉันจะสร้างเอกสาร Word อย่างโปรแกรมได้อย่างไร?** สร้างอินสแตนซ์ `Document`, เพิ่มเนื้อหาด้วย `DocumentBuilder`, แล้วเรียก `save("MyDoc.docx")`.  
- **มีวิธีใดที่จะใช้สไตล์ย่อหน้าที่กำหนดเองหรือไม่?** ตั้งค่าตัวระบุสไตล์โดยใช้ `ParagraphFormat.setStyleIdentifier(StyleIdentifier.TITLE)`.

## การตั้งค่าสภาพแวดล้อมของคุณ

ก่อนที่เราจะลงลึกในรายละเอียดของการจัดรูปแบบเอกสาร, การตั้งค่าสภาพแวดล้อมของคุณเป็นสิ่งสำคัญ ตรวจสอบให้แน่ใจว่าคุณได้ติดตั้งและกำหนดค่า Aspose.Words for Java อย่างถูกต้องในโปรเจกต์ของคุณ คุณสามารถดาวน์โหลดได้จาก [ที่นี่](https://releases.aspose.com/words/java/).

## การสร้างเอกสารง่าย ๆ

มาเริ่มต้นด้วยการ **สร้างเอกสาร Word** ด้วย Aspose.Words for Java โค้ดตัวอย่าง Java ด้านล่างแสดงวิธีสร้างเอกสารและเพิ่มข้อความบางส่วนเข้าไป:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
builder.writeln("Hello, Aspose.Words for Java!");
doc.save("MyDocument.docx");
```

## การปรับช่องว่างระหว่างข้อความเอเชียและละติน

Aspose.Words for Java มีฟีเจอร์ที่ทรงพลังสำหรับจัดการช่องว่างของข้อความ คุณสามารถปรับช่องว่างระหว่างข้อความเอเชียและละตินโดยอัตโนมัติตามตัวอย่างด้านล่าง:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
ParagraphFormat paragraphFormat = builder.getParagraphFormat();
paragraphFormat.setAddSpaceBetweenFarEastAndAlpha(true);
paragraphFormat.setAddSpaceBetweenFarEastAndDigit(true);
builder.writeln("Automatically adjust space between Asian and Latin text");
builder.writeln("Automatically adjust space between Asian text and numbers");
doc.save("SpaceBetweenAsianAndLatinText.docx");
```

## การทำงานกับการพิมพ์แบบเอเชีย

เพื่อควบคุมการตั้งค่าการพิมพ์แบบเอเชีย, พิจารณาโค้ดตัวอย่างต่อไปนี้:

```java
Document doc = new Document("AsianTypography.docx");
ParagraphFormat format = doc.getFirstSection().getBody().getParagraphs().get(0).getParagraphFormat();
format.setFarEastLineBreakControl(false);
format.setWordWrap(true);
format.setHangingPunctuation(false);
doc.save("AsianTypographyLineBreakGroup.docx");
```

## การจัดรูปแบบย่อหน้า

Aspose.Words for Java ช่วยให้คุณ **ตั้งค่าการจัดแนวย่อหน้า**, **ตั้งค่าการเยื้องซ้าย**, และจัดรูปแบบย่อหน้าได้อย่างง่ายดาย ดูตัวอย่างนี้:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
ParagraphFormat paragraphFormat = builder.getParagraphFormat();
paragraphFormat.setAlignment(ParagraphAlignment.CENTER);
paragraphFormat.setLeftIndent(50.0);
paragraphFormat.setRightIndent(50.0);
paragraphFormat.setSpaceAfter(25.0);
builder.writeln("I'm a very nice formatted paragraph. I'm intended to demonstrate how the left and right indents affect word wrapping.");
builder.writeln("I'm another nice formatted paragraph. I'm intended to demonstrate how the space after paragraph looks like.");
doc.save("ParagraphFormatting.docx");
```

## การจัดรูปแบบรายการหลายระดับ

การสร้างโครงสร้าง **รายการหลายระดับ** เป็นความต้องการทั่วไปในการจัดรูปแบบเอกสาร Aspose.Words for Java ทำให้กระบวนการนี้ง่ายขึ้น:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
builder.getListFormat().applyNumberDefault();
builder.writeln("Item 1");
// Add more items here...
doc.save("MultilevelListFormatting.docx");
```

## การใช้สไตล์ย่อหน้า

Aspose.Words for Java ทำให้คุณสามารถ **ใช้สไตล์ย่อหน้า** ได้อย่างไม่มีความยุ่งยาก:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
builder.getParagraphFormat().setStyleIdentifier(StyleIdentifier.TITLE);
builder.write("Hello, Styled Paragraph!");
doc.save("ApplyParagraphStyle.docx");
```

## การเพิ่มเส้นขอบและเงาให้กับย่อหน้า

เพิ่มความสวยงามให้กับเอกสารของคุณโดยการเพิ่มเส้นขอบและเงา:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
BorderCollection borders = builder.getParagraphFormat().getBorders();
// Customize borders here...
Shading shading = builder.getParagraphFormat().getShading();
// Customize shading here...
builder.write("I'm a formatted paragraph with double border and nice shading.");
doc.save("ApplyBordersAndShadingToParagraph.docx");
```

## การเปลี่ยนช่องว่างและการเยื้องของย่อหน้าเอเชีย

ปรับแต่งช่องว่างและการเยื้องของย่อหน้าสำหรับข้อความเอเชียอย่างละเอียด:

```java
Document doc = new Document("AsianTypography.docx");
ParagraphFormat format = doc.getFirstSection().getBody().getFirstParagraph().getParagraphFormat();
format.setCharacterUnitLeftIndent(10.0);
format.setCharacterUnitRightIndent(10.0);
format.setCharacterUnitFirstLineIndent(20.0);
format.setLineUnitBefore(5.0);
format.setLineUnitAfter(10.0);
doc.save("ChangeAsianParagraphSpacingAndIndents.docx");
```

## การจัดตำแหน่งตามกริด

เพิ่มประสิทธิภาพการจัดวางเมื่อทำงานกับอักขระเอเชียโดยจัดตำแหน่งตามกริด:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
Paragraph par = doc.getFirstSection().getBody().getFirstParagraph();
par.getParagraphFormat().setSnapToGrid(true);
builder.writeln("Lorem ipsum dolor sit amet, consectetur adipiscing elit...");
par.getRuns().get(0).getFont().setSnapToGrid(true);
doc.save("SnapToGrid.docx");
```

## การตรวจจับตัวคั่นสไตล์ย่อหน้า

หากคุณต้องการค้นหาตัวคั่นสไตล์ในเอกสารของคุณ, คุณสามารถใช้โค้ดต่อไปนี้:

```java
Document doc = new Document("Document.docx");
for (Paragraph paragraph : (Iterable<Paragraph>) doc.getChildNodes(NodeType.PARAGRAPH, true))
{
    if (paragraph.getBreakIsStyleSeparator())
    {
        System.out.println("Separator Found!");
    }
}
```

## สรุป

ในบทความนี้, เราได้สำรวจแง่มุมต่าง ๆ ของการจัดรูปแบบเอกสารใน Aspose.Words for Java รวมถึงวิธี **สร้างรายการหลายระดับ**, **ใช้สไตล์ย่อหน้า**, **ตั้งค่าการจัดแนวย่อหน้า**, และ **ตั้งค่าการเยื้องซ้าย** ด้วยความเข้าใจเหล่านี้, คุณสามารถสร้างเอกสาร Word ที่ดูเป็นมืออาชีพสำหรับแอปพลิเคชัน Java ของคุณ อย่าลืมอ้างอิงที่ [เอกสาร Aspose.Words for Java](https://reference.aspose.com/words/java/) เพื่อรับคำแนะนำเชิงลึกเพิ่มเติม.

## คำถามที่พบบ่อย

**ถาม: ฉันจะดาวน์โหลด Aspose.Words for Java ได้อย่างไร?**  
ตอบ: คุณสามารถดาวน์โหลด Aspose.Words for Java ได้จาก [ลิงก์นี้](https://releases.aspose.com/words/java/).

**ถาม: Aspose.Words for Java เหมาะสำหรับการสร้างเอกสารที่ซับซ้อนหรือไม่?**  
ตอบ: แน่นอน! Aspose.Words for Java มีความสามารถที่ครอบคลุมสำหรับการสร้างและจัดรูปแบบเอกสารที่ซับซ้อนได้อย่างง่ายดาย.

**ถาม: ฉันสามารถใช้สไตล์ที่กำหนดเองกับย่อหน้าโดยใช้ Aspose.Words for Java ได้หรือไม่?**  
ตอบ: ได้, คุณสามารถใช้สไตล์ที่กำหนดเองกับย่อหน้าเพื่อให้เอกสารของคุณมีลักษณะและความรู้สึกที่เป็นเอกลักษณ์.

**ถาม: Aspose.Words for Java รองรับรายการหลายระดับหรือไม่?**  
ตอบ: ใช่, Aspose.Words for Java มีการสนับสนุนที่ยอดเยี่ยมสำหรับการสร้างและจัดรูปแบบรายการหลายระดับ.

**ถาม: ฉันจะปรับช่องว่างของย่อหน้าสำหรับข้อความเอเชียอย่างไร?**  
ตอบ: คุณสามารถปรับแต่งช่องว่างของย่อหน้าสำหรับข้อความเอเชียโดยการปรับการตั้งค่าที่เกี่ยวข้องใน Aspose.Words for Java.

**ถาม: วิธีที่ง่ายที่สุดในการสร้างเอกสาร Word อย่างโปรแกรมคืออะไร?**  
ตอบ: สร้างอินสแตนซ์ `Document`, ใช้ `DocumentBuilder` เพื่อเพิ่มเนื้อหา, แล้วเรียก `save("YourFile.docx")`.

**ถาม: มีเคล็ดลับด้านประสิทธิภาพสำหรับเอกสารขนาดใหญ่หรือไม่?**  
ตอบ: ใช้ API แบบสตรีมและทำลายออบเจ็กต์ที่ไม่ได้ใช้โดยเร็วเพื่อรักษาการใช้หน่วยความจำให้ต่ำ.

**อัปเดตล่าสุด:** 2026-01-09  
**ทดสอบด้วย:** Aspose.Words for Java 24.12 (รุ่นล่าสุด)  
**ผู้เขียน:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}