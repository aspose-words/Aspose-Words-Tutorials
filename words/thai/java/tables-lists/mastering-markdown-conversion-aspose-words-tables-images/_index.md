---
"date": "2025-03-28"
"description": "เรียนรู้วิธีการแปลงเอกสาร Word ให้เป็น Markdown ที่มีโครงสร้างที่ดีโดยใช้ Aspose.Words สำหรับ Java โดยเน้นที่ตารางและรูปภาพ"
"title": "ฝึกฝนการแปลง Markdown ให้เชี่ยวชาญด้วย Aspose.Words&#58; ตารางและรูปภาพ"
"url": "/th/java/tables-lists/mastering-markdown-conversion-aspose-words-tables-images/"
"weight": 1
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}


# การแปลง Markdown อย่างเชี่ยวชาญด้วย Aspose.Words: คำแนะนำเกี่ยวกับตารางและรูปภาพ
## การแนะนำ
กำลังดิ้นรนที่จะแปลงเอกสาร Word ที่ซับซ้อนเป็นไฟล์ Markdown ที่สะอาดและมีโครงสร้างที่ดีหรือไม่ ไม่ว่าจะเป็นการจัดแนวเนื้อหาในตารางหรือการเปลี่ยนชื่อรูปภาพในระหว่างการแปลง เครื่องมือที่เหมาะสมสามารถสร้างความแตกต่างได้ คู่มือนี้จะช่วยคุณใช้ **Aspose.คำศัพท์สำหรับภาษา Java** เพื่อการแปลง Markdown ได้อย่างราบรื่น คุณจะได้เรียนรู้:
- การจัดตำแหน่งเนื้อหาตารางในมาร์กดาวน์
- การเปลี่ยนชื่อรูปภาพอย่างมีประสิทธิภาพในระหว่างการแปลงมาร์กดาวน์
- การระบุโฟลเดอร์และนามแฝงของภาพ
- การส่งออกการจัดรูปแบบขีดเส้นใต้และตารางเป็น HTML
การเปลี่ยนจาก Word ไปเป็น Markdown ไม่จำเป็นต้องยุ่งยาก เรามาดูกันว่า Aspose.Words Java ทำให้กระบวนการนี้ง่ายขึ้นอย่างไร
## ข้อกำหนดเบื้องต้น
ก่อนจะเริ่มใช้งานจริง ให้แน่ใจว่าคุณมีเครื่องมือที่จำเป็นแล้ว:
- **Aspose.คำศัพท์สำหรับภาษา Java**:ไลบรารีอันทรงพลังนี้ช่วยอำนวยความสะดวกในการประมวลผลและการแปลงเอกสาร
- **ชุดพัฒนา Java (JDK)**:ขอแนะนำเวอร์ชัน 8 ขึ้นไป
- **ไอดีอี**:สภาพแวดล้อมการพัฒนาแบบบูรณาการ เช่น IntelliJ IDEA หรือ Eclipse
คุณควรมีความเข้าใจพื้นฐานเกี่ยวกับการเขียนโปรแกรม Java รวมถึงการจัดการการอ้างอิงผ่าน Maven หรือ Gradle
## การตั้งค่า Aspose.Words
หากต้องการเริ่มใช้ Aspose.Words สำหรับ Java ให้รวมไว้ในโปรเจ็กต์ของคุณ ดังต่อไปนี้:
### การพึ่งพา Maven
เพิ่มการอ้างอิงต่อไปนี้ให้กับของคุณ `pom.xml` ไฟล์:
```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>25.3</version>
</dependency>
```
### การอ้างอิงของ Gradle
อีกวิธีหนึ่ง ให้รวมสิ่งนี้ไว้ในของคุณ `build.gradle` ไฟล์:
```gradle
implementation 'com.aspose:aspose-words:25.3'
```
### การขอใบอนุญาต
หากต้องการปลดล็อกความสามารถทั้งหมดของ Aspose.Words โปรดพิจารณาซื้อใบอนุญาต คุณสามารถเริ่มต้นด้วยการทดลองใช้ฟรีหรือขอใบอนุญาตชั่วคราวเพื่อทดสอบฟีเจอร์ต่างๆ โดยไม่มีข้อจำกัด
## คู่มือการใช้งาน
เรามาแยกรายละเอียดคุณลักษณะแต่ละอย่างและแนะนำคุณตลอดกระบวนการใช้งาน:
### จัดตำแหน่งเนื้อหาตารางในมาร์กดาวน์
การจัดวางเนื้อหาตารางให้ตรงกันจะช่วยให้ข้อมูลของคุณแสดงออกมาอย่างเรียบร้อยในรูปแบบมาร์กดาวน์ วิธีดำเนินการนี้โดยใช้ Aspose.Words มีดังนี้
#### ภาพรวม
คุณลักษณะนี้ช่วยให้คุณระบุการตั้งค่าการจัดตำแหน่งสำหรับเนื้อหาตารางเมื่อแปลงเอกสารเป็นมาร์กดาวน์
```java
import com.aspose.words.*;

DocumentBuilder builder = new DocumentBuilder();
builder.insertCell();
builder.getParagraphFormat().setAlignment(ParagraphAlignment.RIGHT);
builder.write("Cell1");
builder.insertCell();
builder.getParagraphFormat().setAlignment(ParagraphAlignment.CENTER);
builder.write("Cell2");

MarkdownSaveOptions saveOptions = new MarkdownSaveOptions();
saveOptions.setTableContentAlignment(TableContentAlignment.LEFT); // ตั้งค่าการจัดตำแหน่งที่ต้องการ

builder.getDocument().save("AlignedTableContents.md", saveOptions);
```
**คำอธิบาย**- 
- `DocumentBuilder` ใช้เพื่อสร้างและจัดการเอกสาร
- `setAlignment()` ตั้งค่าการจัดตำแหน่งย่อหน้าสำหรับแต่ละเซลล์
- `setTableContentAlignment()` ระบุว่าควรจัดตำแหน่งเนื้อหาตารางใน Markdown อย่างไร
### เปลี่ยนชื่อรูปภาพระหว่างการแปลงมาร์กดาวน์
การกำหนดชื่อไฟล์ภาพระหว่างการแปลงช่วยจัดระเบียบทรัพยากรได้อย่างมีประสิทธิภาพ:
#### ภาพรวม
ฟีเจอร์นี้ช่วยให้คุณเปลี่ยนชื่อรูปภาพแบบไดนามิก ช่วยให้จัดการไฟล์หลังการแปลงได้ง่ายยิ่งขึ้น
```java
import com.aspose.words.*;
import java.text.MessageFormat;
import org.apache.commons.io.FilenameUtils;

class ImageRenameFeature implements IImageSavingCallback {
    private int mCount = 0;
    private String mOutFileName;

    public ImageRenameFeature(String outFileName) {
        this.mOutFileName = outFileName;
    }

    @Override
    public void imageSaving(ImageSavingArgs args) throws Exception {
        String imageFileName = MessageFormat.format("{0} shape {1}, of type {2}.{3}",
                mOutFileName, ++mCount, args.getCurrentShape().getShapeType(), FilenameUtils.getExtension(args.getImageFileName()));
        args.setImageFileName(imageFileName);
        args.setKeepImageStreamOpen(false);
    }
}

Document doc = new Document("YOUR_DOCUMENT_PATH");
MarkdownSaveOptions saveOptions = new MarkdownSaveOptions();
saveOptions.setImageSavingCallback(new ImageRenameFeature("CustomImages"));
doc.save("RenamedImages.md", saveOptions);
```
**คำอธิบาย**- 
- ดำเนินการ `IImageSavingCallback` เพื่อปรับแต่งชื่อไฟล์ภาพ
- ใช้ `MessageFormat` และ `FilenameUtils` เพื่อการตั้งชื่อแบบมีโครงสร้าง
### ระบุโฟลเดอร์รูปภาพและนามแฝงในมาร์กดาวน์
จัดระเบียบรูปภาพของคุณโดยระบุโฟลเดอร์และนามแฝงเฉพาะระหว่างการแปลง:
#### ภาพรวม
คุณสมบัตินี้ช่วยให้แน่ใจว่ารูปภาพทั้งหมดได้รับการบันทึกไว้ในไดเร็กทอรีที่ระบุโดยมีชื่อ URI ที่เหมาะสม
```java
import com.aspose.words.*;
import java.nio.file.Paths;

DocumentBuilder builder = new DocumentBuilder();
builder.writeln("Some image below:");
builder.insertImage("YOUR_IMAGE_PATH" + "Logo.jpg");

String imagesFolder = Paths.get("YOUR_DOCUMENT_DIRECTORY", "ImagesDir").toString();
MarkdownSaveOptions saveOptions = new MarkdownSaveOptions();
saveOptions.setImagesFolder(imagesFolder);
saveOptions.setImagesFolderAlias("http://example.com/images);

builder.getDocument().save("ImageFolderSpecified.md", saveOptions);
```
**คำอธิบาย**- 
- `setImagesFolder()` ระบุว่าควรเก็บรูปภาพไว้ที่ไหน
- `setImagesFolderAlias()` กำหนด URI เพื่ออ้างอิงโฟลเดอร์รูปภาพ
### การส่งออกการจัดรูปแบบขีดเส้นใต้ในมาร์กดาวน์
รักษาความสำคัญของภาพโดยการส่งออกการจัดรูปแบบขีดเส้นใต้:
#### ภาพรวม
คุณสมบัตินี้จะแปลงเส้นใต้ในเอกสาร Word ให้เป็นไวยากรณ์ที่เป็นมิตรต่อ Markdown
```java
import com.aspose.words.*;

Document doc = new Document();
doc.getRange().getFont().setUnderline(Underline.SINGLE);
doc.getFirstSection().getBody().appendParagraph("Lorem ipsum. Dolor sit amet.");

MarkdownSaveOptions saveOptions = new MarkdownSaveOptions();
saveOptions.setExportUnderlineFormatting(true);

doc.save("UnderlineFormatted.md", saveOptions);
```
**คำอธิบาย**- 
- `setUnderline()` ใช้การจัดรูปแบบขีดเส้นใต้
- `setExportUnderlineFormatting()` ช่วยให้แน่ใจว่าเส้นขีดเส้นใต้จะถูกแปลเป็นรูปแบบ Markdown
### ส่งออกตารางเป็น HTML ในมาร์กดาวน์
รักษาโครงสร้างตารางที่ซับซ้อนโดยการส่งออกเป็น HTML แบบดิบ:
#### ภาพรวม
คุณลักษณะนี้ช่วยให้สามารถส่งออกตารางเป็น HTML ได้โดยตรง โดยยังคงโครงสร้างเดิมเอาไว้
```java
import com.aspose.words.*;

Document doc = new Document();
DocumentBuilder documentBuilder = new DocumentBuilder(doc);
documentBuilder.writeln("Sample table:");
documentBuilder.insertCell();
documentBuilder.getParagraphFormat().setAlignment(ParagraphAlignment.RIGHT);
documentBuilder.write("Cell1");
documentBuilder.insertCell();
documentBuilder.getParagraphFormat().setAlignment(ParagraphAlignment.CENTER);
documentBuilder.write("Cell2");

MarkdownSaveOptions saveOptions = new MarkdownSaveOptions();
saveOptions.setExportAsHtml(MarkdownExportAsHtml.TABLES);

doc.save("TableAsHtml.md", saveOptions);
```
**คำอธิบาย**- 
- ใช้ `setExportAsHtml()` เพื่อส่งออกตารางเป็น HTML ภายในไฟล์ Markdown
## การประยุกต์ใช้งานจริง
คุณสมบัติเหล่านี้สามารถนำไปประยุกต์ใช้ในสถานการณ์ต่างๆ ได้ดังนี้:
1. **การแปลงเอกสาร**:แปลงคู่มือทางเทคนิคให้เป็น Markdown ที่ใช้งานง่าย
2. **การสร้างเนื้อหาเว็บไซต์**:สร้างเนื้อหาสำหรับบล็อกหรือเว็บไซต์ด้วยข้อมูลและรูปภาพที่มีโครงสร้าง
3. **โครงการความร่วมมือ**:แบ่งปันเอกสารระหว่างทีมโดยใช้ระบบควบคุมเวอร์ชันเช่น Git
## การพิจารณาประสิทธิภาพ
เพื่อให้มั่นใจถึงประสิทธิภาพที่เหมาะสมที่สุด:
- **จัดการการใช้หน่วยความจำ**:ใช้ขนาดบัฟเฟอร์ที่เหมาะสมและจัดการทรัพยากรอย่างมีประสิทธิภาพในระหว่างการแปลง
- **เพิ่มประสิทธิภาพ I/O ไฟล์**:ลดการดำเนินการกับดิสก์ให้เหลือน้อยที่สุดโดยแบ่งการบันทึกภาพเป็นชุดหรือส่งออกตาราง
- **ใช้ประโยชน์จากมัลติเธรด**:หากใช้ได้ ให้ใช้การประมวลผลพร้อมกันสำหรับเอกสารขนาดใหญ่
## บทสรุป
การเชี่ยวชาญฟีเจอร์เหล่านี้ของ Aspose.Words สำหรับ Java จะช่วยให้คุณแปลงเอกสาร Word เป็น Markdown ได้อย่างแม่นยำและง่ายดาย ไม่ว่าจะเป็นการจัดแนวตาราง การเปลี่ยนชื่อรูปภาพ หรือการส่งออกการจัดรูปแบบ คู่มือนี้จะช่วยให้คุณมีทักษะที่จำเป็นสำหรับการแปลงเอกสารอย่างมีประสิทธิภาพ

{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}