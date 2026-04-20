---
date: '2026-02-06'
description: เรียนรู้วิธีตรวจสอบลายเซ็นดิจิทัล, ตรวจจับการเข้ารหัสไฟล์, และจัดการข้อยกเว้นโดยใช้
  Aspose.Words for Java.
keywords:
- Aspose.Words for Java
- FileCorruptedException handling
- file encoding detection
- digital signature verification
- extract images from documents
title: ตรวจสอบลายเซ็นดิจิทัลด้วย Aspose.Words สำหรับ Java
url: /th/java/document-operations/aspose-words-java-handling-exceptions-formats/
weight: 1
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# ตรวจสอบลายเซ็นดิจิทัลและจัดการข้อยกเว้นและรูปแบบด้วย Aspose.Words for Java

## บทนำ

คุณต้องการ **ตรวจสอบลายเซ็นดิจิทัล** บนเอกสาร Word พร้อมกับการจัดการไฟล์ที่เสียหาย, ตรวจจับการเข้ารหัส, หรือดึงภาพที่ฝังอยู่หรือไม่? ด้วย **Aspose.Words for Java** คุณสามารถแก้ไขทุกความท้าทายเหล่านี้ด้วย API ที่เรียบง่ายเดียวกัน บทเรียนนี้จะพาคุณผ่านการดักจับ `FileCorruptedException`, การตรวจจับการเข้ารหัสของไฟล์, การแมปประเภทสื่อ, การตรวจสอบการเข้ารหัส, การตรวจสอบลายเซ็นดิจิทัล, การบันทึกอัตโนมัติรูปแบบที่ตรวจพบ, และการดึงภาพออกจากไฟล์ Word

**คุณจะได้เรียนรู้**

- ดักจับและจัดการข้อยกเว้นการเสียหายของไฟล์ใน Java.  
- **detect file encoding java** สำหรับเอกสาร HTML หรือข้อความ.  
- **detect file format java** และแมปประเภทสื่อเป็นรูปแบบการบันทึกของ Aspose.  
- **detect document encryption** และทำงานกับไฟล์ที่เข้ารหัส.  
- **verify digital signature** บนเอกสาร Word.  
- **extract images from word** เอกสารเพื่อการนำกลับมาใช้ใหม่หรือการวิเคราะห์.

ให้แน่ใจว่าสภาพแวดล้อมการพัฒนาของคุณพร้อมก่อนที่เราจะลงลึกในโค้ด

## คำตอบอย่างรวดเร็ว
- **วิธีการตรวจสอบลายเซ็นดิจิทัล?** ใช้ `FileFormatUtil.detectFileFormat(...).hasDigitalSignature()`.  
- **ข้อยกเว้นใดที่บ่งชี้ว่าไฟล์เสียหาย?** `FileCorruptedException`.  
- **Aspose.Words สามารถตรวจจับการเข้ารหัส HTML ได้หรือไม่?** ใช่, ผ่าน `FileFormatUtil.detectFileFormat`.  
- **มีวิธีการบันทึกอัตโนมัติเอกสารที่มีนามสกุลไม่ทราบหรือไม่?** แปลงรูปแบบการโหลดที่ตรวจพบเป็นรูปแบบการบันทึกด้วย `FileFormatUtil.loadFormatToSaveFormat`.  
- **วิธีการดึงภาพจากไฟล์ Word?** วนลูปผ่านโหนด `Shape` และเรียก `shape.getImageData().save(...)`.

## ข้อกำหนดเบื้องต้น

- Java Development Kit (JDK) 8 หรือใหม่กว่า.  
- ความรู้พื้นฐานของ Java, โดยเฉพาะการจัดการข้อยกเว้น.  
- Maven หรือ Gradle สำหรับการจัดการ dependencies.

### ไลบรารีที่จำเป็นและการตั้งค่าสภาพแวดล้อม
Add Aspose.Words to your project:

```xml
<dependency>
  <groupId>com.aspose</groupId>
  <artifactId>aspose-words</artifactId>
  <version>25.3</version>
</dependency>
```

```gradle
implementation 'com.aspose:aspose-words:25.3'
```

### ขั้นตอนการรับใบอนุญาต
เริ่มต้นด้วยการทดลองใช้งานฟรีหรือขอใบอนุญาตชั่วคราวเพื่อเปิดใช้งานคุณสมบัติเต็มรูปแบบก่อนทำการซื้อ.

## การตั้งค่า Aspose.Words

Initialize the library and apply your license:

```java
import com.aspose.words.License;

License license = new License();
license.setLicense("Aspose.Words.lic");
```

ตอนนี้คุณพร้อมใช้ API เต็มรูปแบบโดยไม่มีข้อจำกัดการประเมินผล.

## คู่มือการใช้งาน

### วิธีจัดการ FileCorruptedException ใน Java

**ภาพรวม**  
การจัดการอินพุตที่เสียหายอย่างราบรื่นช่วยป้องกันแอปพลิเคชันของคุณจากการหยุดทำงาน.

```java
import com.aspose.words.Document;
import com.aspose.words.FileCorruptedException;

try {
    Document doc = new Document("YOUR_DOCUMENT_DIRECTORY/Corrupted document.docx");
} catch (FileCorruptedException e) {
    System.out.println(e.getMessage());
}
```

บล็อก catch จะบันทึกข้อผิดพลาด, ให้คุณมีโอกาสแจ้งผู้ใช้หรือลองใหม่ด้วยไฟล์อื่น.

### วิธีตรวจจับการเข้ารหัสไฟล์ใน Java

**ภาพรวม**  
การตรวจจับการเข้ารหัสของไฟล์ HTML อย่างถูกต้องทำให้ตัวอักษรแสดงผลตามที่ต้องการ.

```java
import com.aspose.words.FileFormatInfo;
import com.aspose.words.LoadFormat;

FileFormatInfo info = FileFormatUtil.detectFileFormat("YOUR_DOCUMENT_DIRECTORY/Document.html");
System.out.println("Load Format: " + LoadFormat.toString(info.getLoadFormat()));
System.out.println("Encoding: " + (info.getEncoding() != null ? info.getEncoding().name() : "None"));
```

โค้ดสั้นนี้จะแสดงทั้งรูปแบบการโหลดที่ตรวจพบและการเข้ารหัสของอักขระ.

### วิธีตรวจจับรูปแบบไฟล์ใน Java

**ภาพรวม**  
การแมป MIME type (media type) ไปยังรูปแบบภายในของ Aspose ทำให้การจัดการประเภทเนื้อหาง่ายขึ้น.

```java
import com.aspose.words.FileFormatUtil;

FileFormatInfo info = FileFormatUtil.contentTypeToSaveFormat("image/jpeg");
System.out.println("Save Format: " + info.getLoadFormat());
```

การแปลงนี้มีประโยชน์เมื่อคุณรับไฟล์ผ่าน HTTP และต้องตัดสินใจว่าจะประมวลผลอย่างไร.

### วิธีตรวจจับการเข้ารหัสเอกสาร

**ภาพรวม**  
การรู้ว่าเอกสารถูกเข้ารหัสหรือไม่ทำให้คุณตัดสินใจได้ว่าจะขอรหัสผ่านหรือไม่.

```java
import com.aspose.words.Document;
import com.aspose.words.OdtSaveOptions;

Document doc = new Document();
OdtSaveOptions saveOptions = new OdtSaveOptions(com.aspose.words.SaveFormat.ODT);
saveOptions.setPassword("MyPassword");
doc.save("YOUR_OUTPUT_DIRECTORY/File.DetectDocumentEncryption.odt", saveOptions);

FileFormatInfo info = FileFormatUtil.detectFileFormat("YOUR_OUTPUT_DIRECTORY/File.DetectDocumentEncryption.odt");
System.out.println("Is Encrypted: " + info.isEncrypted());
```

โค้ดนี้สร้างไฟล์ ODT ที่เข้ารหัสก่อน, จากนั้นตรวจสอบสถานะการเข้ารหัสของมัน.

### วิธีตรวจสอบลายเซ็นดิจิทัล

**ภาพรวม**  
การตรวจสอบลายเซ็นดิจิทัลยืนยันความแท้และความสมบูรณ์ของเอกสาร.

```java
import com.aspose.words.FileFormatInfo;
import org.bouncycastle.cert.jcajce.JcaCertStore;

FileFormatInfo info = FileFormatUtil.detectFileFormat("YOUR_DOCUMENT_DIRECTORY/Document.docx");
System.out.println("Has Digital Signature: " + info.hasDigitalSignature());
```

หาก `hasDigitalSignature()` คืนค่า `true`, เอกสารนั้นมีลายเซ็นที่ถูกต้อง.

### การบันทึกเอกสารเป็นรูปแบบที่ตรวจพบ

**ภาพรวม**  
การบันทึกเอกสารโดยอัตโนมัติในรูปแบบดั้งเดิมของมันช่วยทำให้กระบวนการประมวลผลแบบชุดเป็นไปอย่างราบรื่น.

```java
import com.aspose.words.Document;
import java.io.FileInputStream;

FileInputStream docStream = new FileInputStream("YOUR_DOCUMENT_DIRECTORY/Word document with missing file extension");
FileFormatInfo info = FileFormatUtil.detectFileFormat(docStream);
Document doc = new Document(docStream);

int saveFormat = FileFormatUtil.loadFormatToSaveFormat(info.getLoadFormat());
doc.save("YOUR_OUTPUT_DIRECTORY/Detected_Format.docx", saveFormat);
```

แม้ไม่มีนามสกุลไฟล์, Aspose.Words สามารถกำหนดรูปแบบที่ถูกต้องและบันทึกได้อย่างเหมาะสม.

### วิธีดึงภาพจาก Word

**ภาพรวม**  
การดึงภาพที่ฝังอยู่ทำให้สามารถนำกลับมาใช้ใหม่ในหน้าเว็บ, แกลเลอรี, หรือโครงการวิเคราะห์ข้อมูล.

```java
import com.aspose.words.Document;
import com.aspose.words.NodeCollection;
import com.aspose.words.Shape;

Document doc = new Document("YOUR_DOCUMENT_DIRECTORY/Images.docx");
NodeCollection shapes = doc.getChildNodes(com.aspose.words.NodeType.SHAPE, true);

int imageIndex = 0;
for (Shape shape : (Iterable<Shape>) shapes) {
    if (shape.hasImage()) {
        String imageFileName = "ExtractedImage_" + imageIndex + "." + 
                FileFormatUtil.imageTypeToExtension(shape.getImageData().getImageType());
        shape.getImageData().save("YOUR_OUTPUT_DIRECTORY/" + imageFileName);
        imageIndex++;
    }
}
```

แต่ละภาพจะถูกบันทึกด้วยชื่อไฟล์ตามลำดับและนามสกุลไฟล์ที่ถูกต้อง.

## การประยุกต์ใช้งานจริง

1. **บริการตรวจสอบเอกสาร** – ตรวจจับความเสียหาย, การเข้ารหัส, และลายเซ็นก่อนรับไฟล์จากพันธมิตร.  
2. **ระบบจัดการเนื้อหา (CMS)** – ตรวจจับประเภทสื่อและการเข้ารหัสอัตโนมัติเพื่อทำให้การอัปโหลดเป็นไปอย่างราบรื่น.  
3. **เครื่องมือด้านกฎหมายและการปฏิบัติตาม** – ตรวจสอบลายเซ็นดิจิทัลเพื่อให้แน่ใจว่าเอกสารไม่ได้ถูกดัดแปลง.  
4. **สายงานการดึงข้อมูล** – ดึงภาพจากสัญญา, รายงาน, หรือสื่อการตลาดเพื่อการจัดเก็บ.  
5. **การรายงานอัตโนมัติ** – บันทึกรายงานที่สร้างขึ้นในรูปแบบที่สร้างขึ้นเดิม แม้ไม่มีนามสกุลไฟล์.

## ข้อควรพิจารณาด้านประสิทธิภาพ

- ใช้การจัดการข้อยกเว้นที่เจาะจงเพื่อหลีกเลี่ยงภาระการ try/catch ที่ไม่จำเป็น.  
- แคชผลลัพธ์ `FileFormatInfo` สำหรับประเภทไฟล์ที่ประมวลผลบ่อย.  
- ปล่อยออบเจกต์ `Document` อย่างทันท่วงทีเพื่อคืนหน่วยความจำเมื่อจัดการไฟล์ขนาดใหญ่.

## ส่วนคำถามที่พบบ่อย

**Q1: ฉันจะจัดการกับรูปแบบไฟล์ที่ไม่รองรับใน Aspose.Words อย่างไร?**  
A1: ใช้ `FileFormatUtil` เพื่อตรวจจับรูปแบบที่รองรับก่อน; สำหรับประเภทที่ไม่รองรับ ให้ใช้ตัวแยกวิเคราะห์แบบกำหนดเองหรือปฏิเสธไฟล์นั้น.

**Q2: Aspose.Words สามารถประมวลผลเอกสารขนาดใหญ่ได้อย่างมีประสิทธิภาพหรือไม่?**  
A2: ได้, แต่ควรปรับการตั้งค่า heap ของ JVM และพิจารณาใช้ streaming APIs สำหรับไฟล์ที่ใหญ่มาก.

**Q3: ข้อผิดพลาดทั่วไปเมื่อทำการตรวจจับลายเซ็นดิจิทัลคืออะไร?**  
A3: ตรวจสอบให้แน่ใจว่าห่วงโซ่ใบรับรองการลงนามได้รับความเชื่อถือและไลบรารี BouncyCastle ที่จำเป็นอยู่ใน classpath.

**Q4: ฉันจะรวม Aspose.Words เข้าในโครงการ Maven ที่มีอยู่ได้อย่างไร?**  
A4: เพิ่ม dependency ของ Maven ที่แสดงไว้ก่อนหน้า, วางไฟล์ใบอนุญาตของคุณใน classpath, และสร้างโครงการใหม่อีกครั้ง.

**Q5: มีขีดจำกัดใดในการทำงานของการดึงภาพหรือไม่?**  
A5: การดึงภาพทำได้เร็วสำหรับเอกสารทั่วไป; ไฟล์ที่มีภาพจำนวนมากอาจต้องปรับการตั้งค่าหน่วยความจำเพิ่มเติม.

## คำถามที่พบบ่อย

**Q: Aspose.Words รองรับไฟล์ Word ที่ป้องกันด้วยรหัสผ่าน (เข้ารหัส) หรือไม่?**  
A: ใช่. โหลดเอกสารด้วยรหัสผ่านที่เหมาะสมหรือใช้ `LoadOptions` เพื่อระบุพารามิเตอร์การถอดรหัส.

**Q: ฉันสามารถตรวจสอบลายเซ็นดิจิทัลโดยไม่ต้องโหลดเอกสารทั้งหมดได้หรือไม่?**  
A: วิธี `FileFormatUtil.detectFileFormat` จะอ่านเฉพาะข้อมูลส่วนหัวที่จำเป็นสำหรับการตรวจจับลายเซ็น ทำให้เป็นกระบวนการที่เบา.

**Q: มีวิธีการประมวลผลหลายไฟล์พร้อมกันเพื่อการตรวจจับการเข้ารหัสหรือไม่?**  
A: วนลูปผ่านไฟล์, เรียก `detectFileFormat` สำหรับแต่ละไฟล์, และบันทึก `info.isEncrypted()` – วิธีนี้สามารถขยายได้ดี.

**Q: Aspose.Words สามารถดึงภาพในรูปแบบใดได้บ้าง?**  
A: รองรับ PNG, JPEG, BMP, GIF, TIFF, และ EMF ผ่าน `shape.getImageData().getImageType()`.

**Q: ฉันต้องมีใบอนุญาตแยกต่างหากสำหรับแต่ละผลิตภัณฑ์ของ Aspose หรือไม่?**  
A: ใช่, ไลบรารี Aspose แต่ละตัว (Words, PDF, Cells ฯลฯ) ต้องการไฟล์ใบอนุญาตของตนเอง.

## แหล่งข้อมูล

- **Documentation:** [Aspose.Words Java Documentation](https://reference.aspose.com/words/java/)  
- **Download:** [Aspose.Words Java Releases](https://releases.aspose.com/words/java/)  
- **Purchase:** [Buy Aspose.Words](https://purchase.aspose.com/buy)  
- **Free Trial:** [Get a Free Trial of Aspose.Words](https://releases.aspose.com/words/java/)  
- **Temporary License:** [Request a Temporary License](https://purchase.aspose.com/temporary-license/)  
- **Support:** [Aspose Forum for Words](https://forum.aspose.com/c/words/10)

**อัปเดตล่าสุด:** 2026-02-06  
**ทดสอบด้วย:** Aspose.Words 25.3 for Java  
**ผู้เขียน:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}