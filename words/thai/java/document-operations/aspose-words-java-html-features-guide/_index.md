---
date: '2026-02-06'
description: เรียนรู้วิธีโหลด HTML VML ด้วย Aspose.Words for Java, เข้ารหัสไฟล์ HTML
  Java, ตั้งค่า HTML base URI, และกำหนดค่าตัวเลือกการควบคุม HTML
keywords:
- Aspose.Words for Java
- HTML document processing
- document encryption
title: โหลด HTML VML ด้วย Aspose.Words for Java – คู่มือฉบับสมบูรณ์
url: /th/java/document-operations/aspose-words-java-html-features-guide/
weight: 1
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# คุณลักษณะ HTML อย่างครอบคลุมกับ Aspose.Words for Java: คู่มือสำหรับนักพัฒนา

## บทนำ

การสำรวจโลกที่ซับซ้อนของการประมวลผลเอกสารอาจทำให้รู้สึกท้าทาย โดยเฉพาะเมื่อจัดการกับคุณลักษณะ HTML ต่าง ๆ ไม่ว่าจะเป็นการสนับสนุน Vector Markup Language (VML) เอกสารที่เข้ารหัส หรือพฤติกรรมการนำเข้า HTML เฉพาะ **Aspose.Words for Java** มอบโซลูชันที่แข็งแกร่ง ในคู่มือนี้ คุณจะได้เรียนรู้ **how to load html vml** อย่างมีประสิทธิภาพและปลอดภัย พร้อมกับงานที่เกี่ยวข้องเช่น **encrypt html java**, **set html base uri**, และตัวเลือก **configure html control** 

**สิ่งที่คุณจะได้เรียนรู้:**
- วิธีโหลดเอกสาร HTML พร้อมการสนับสนุน VML
- เทคนิคการจัดการ HTML แบบหน้าเดียวและคำเตือน
- วิธีการเข้ารหัสและโหลดเอกสาร HTML ที่ป้องกันด้วยรหัสผ่าน
- การใช้ base URI ใน HTML Load Options
- การนำเข้าตัวอิลิเมนต์ input ของ HTML เป็น structured document tags หรือฟิลด์ฟอร์ม
- การละเว้นองค์ประกอบ `<noscript>` ระหว่างการโหลด HTML
- การกำหนดค่าโหมดการนำเข้าบล็อกเพื่อควบคุมการรักษาโครงสร้าง HTML
- การสนับสนุนกฎ `@font-face` สำหรับฟอนต์ที่กำหนดเอง

## คำตอบสั้น
- **วิธีหลักในการเปิดใช้งาน VML ขณะโหลด HTML คืออะไร?** ตั้งค่า `loadOptions.setSupportVml(true)`.
- **ฉันสามารถโหลดไฟล์ HTML ที่ป้องกันด้วยรหัสผ่านได้หรือไม่?** ใช่, ส่งรหัสผ่านไปยัง `HtmlLoadOptions`.
- **ฉันจะแก้ไขเส้นทางรูปภาพแบบ relative อย่างไร?** ใช้ `loadOptions.setBaseUri("your/base/uri")`.
- **สามารถนำเข้า `<select>` เป็นฟิลด์ฟอร์มได้หรือไม่?** ตั้งค่า `loadOptions.setHtmlControlType(HtmlControlType.StructuredDocumentTag)`.
- **คลาสใดที่จับคำเตือนระหว่างการโหลด?** Implement `IWarningCallback` และกำหนดให้กับ `loadOptions.setWarningCallback(...)`.

## ข้อกำหนดเบื้องต้น

ก่อนที่เราจะเริ่มดำเนินการคุณลักษณะ HTML ต่าง ๆ ด้วย Aspose.Words for Java ให้ตรวจสอบว่าสภาพแวดล้อมของคุณตั้งค่าอย่างถูกต้องแล้ว:

- **ไลบรารีที่จำเป็น:** คุณต้องใช้ไลบรารี Aspose.Words เวอร์ชัน 25.3 หรือใหม่กว่า
- **สภาพแวดล้อมการพัฒนา:** คู่มือนี้สมมติว่าคุณใช้ Maven หรือ Gradle สำหรับการจัดการ dependencies
- **พื้นฐานความรู้:** ความเข้าใจพื้นฐานของ Java และความคุ้นเคยกับเอกสาร HTML จะเป็นประโยชน์

## การตั้งค่า Aspose.Words

เพื่อเริ่มใช้งาน Aspose.Words คุณต้องเพิ่มไลบรารีนี้ในโปรเจกต์ของคุณ ด้านล่างเป็นขั้นตอนการตั้งค่าไลบรารีโดยใช้ Maven และ Gradle:

### Maven

เพิ่ม dependency ต่อไปนี้ในไฟล์ `pom.xml` ของคุณ:

```xml
<dependency>
  <groupId>com.aspose</groupId>
  <artifactId>aspose-words</artifactId>
  <version>25.3</version>
</dependency>
```

### Gradle

ใส่โค้ดนี้ในไฟล์ `build.gradle` ของคุณ:

```gradle
implementation 'com.aspose:aspose-words:25.3'
```

#### การรับใบอนุญาต

Aspose.Words ต้องการใบอนุญาตเพื่อใช้งานเต็มรูปแบบ คุณสามารถรับทดลองใช้งานฟรี ขอใบอนุญาตชั่วคราว หรือซื้อใบอนุญาตถาวรได้ เยี่ยมชม [purchase page](https://purchase.aspose.com/buy) เพื่อดูรายละเอียดเพิ่มเติม.

เพื่อเริ่มต้น Aspose.Words ในโปรเจกต์ Java ของคุณ ให้แน่ใจว่าคุณได้ตั้งค่าใบอนุญาตอย่างถูกต้อง:

```java
import com.aspose.words.License;

public class InitializeAspose {
    public static void main(String[] args) throws Exception {
        License license = new License();
        license.setLicense("path/to/your/license/file.lic");
        
        System.out.println("Aspose.Words is ready to use!");
    }
}
```

## คู่มือการดำเนินการ

เราจะแบ่งการดำเนินการออกเป็นส่วน ๆ ตามคุณลักษณะที่ต้องการทำ.

### วิธีโหลด html vml ด้วย Aspose.Words

**ภาพรวม:**  
การโหลดเอกสาร HTML พร้อมการสนับสนุน VML ช่วยให้เราสามารถเรนเดอร์กราฟิกเวกเตอร์เช่นแผนภูมิและรูปร่างได้อย่างหลากหลาย นี่เป็นขั้นตอนสำคัญสำหรับคีย์เวิร์ดหลัก **load html vml**.

#### ขั้นตอนทีละขั้นตอน

1. **ตั้งค่า Load Options**

```java
import com.aspose.words.Document;
import com.aspose.words.HtmlLoadOptions;

HtmlLoadOptions loadOptions = new HtmlLoadOptions();
loadOptions.setSupportVml(true); // Enable VML support
```

2. **โหลดเอกสาร**

```java
Document doc = new Document("path/to/VML conditional.htm", loadOptions);
```

3. **ตรวจสอบประเภทของรูปภาพ**

```java
import com.aspose.words.NodeType;
import com.aspose.words.Shape;

Shape imageShape = (Shape) doc.getChild(NodeType.SHAPE, 0, true);
String expectedImageType = "JPG"; // Adjust based on actual logic

if (!imageShape.getImageData().getImageType().toString().equals(expectedImageType)) {
    throw new AssertionError("Unexpected image type loaded.");
}
```

### โหลด HTML แบบ Fixed และจัดการคำเตือน

**ภาพรวม:**  
การโหลดเอกสาร HTML แบบหน้าเดียวอาจทำให้เกิดคำเตือนที่ต้องจัดการเพื่อการประมวลผลที่แม่นยำ.

#### ขั้นตอนทีละขั้นตอน

1. **กำหนด Warning Callback**

```java
import com.aspose.words.IWarningCallback;
import com.aspose.words.WarningInfo;
import java.util.ArrayList;

private static class ListDocumentWarnings implements IWarningCallback {
    private final ArrayList<WarningInfo> mWarnings = new ArrayList<>();

    public void warning(WarningInfo info) { 
        mWarnings.add(info); 
    }

    public ArrayList<WarningInfo> warnings() { return mWarnings; }
}
```

2. **กำหนดค่า Load Options**

```java
HtmlLoadOptions loadOptions = new HtmlLoadOptions();
ListDocumentWarnings warningCallback = new ListDocumentWarnings();
loadOptions.setWarningCallback(warningCallback);
```

3. **โหลดเอกสารและตรวจสอบคำเตือน**

```java
Document doc = new Document("path/to/HtmlFixed.html", loadOptions);

if (warningCallback.warnings().size() != 1) {
    throw new AssertionError("Unexpected number of warnings.");
}
```

### เข้ารหัสเอกสาร HTML

**ภาพรวม:**  
การเข้ารหัสเอกสาร HTML ด้วยรหัสผ่านช่วยให้การเข้าถึงปลอดภัย ซึ่งจำเป็นสำหรับข้อมูลที่สำคัญ—นี่คือการตอบสนองต่อสถานการณ์ **encrypt html java**.

#### ขั้นตอนทีละขั้นตอน

1. **เตรียมตัวเลือก Digital Signature**

```java
import com.aspose.words.CertificateHolder;
import com.aspose.words.DigitalSignatureUtil;
import com.aspose.words.SignOptions;

CertificateHolder certificateHolder = CertificateHolder.create("path/to/morzal.pfx", "aw");
SignOptions signOptions = new SignOptions();
signOptions.setComments("Comment");
signOptions.setSignTime(new Date());
signOptions.setDecryptionPassword("docPassword");
```

2. **ลงนามและเข้ารหัสเอกสาร**

```java
String inputFileName = "path/to/Encrypted.docx";
String outputFileName = "path/to/output/directory/HtmlLoadOptions.EncryptedHtml.html";

DigitalSignatureUtil.sign(inputFileName, outputFileName, certificateHolder, signOptions);
```

3. **โหลดเอกสารที่เข้ารหัส**

```java
import com.aspose.words.Document;

HtmlLoadOptions loadOptions = new HtmlLoadOptions("docPassword");
Document doc = new Document(outputFileName, loadOptions);

if (!doc.getText().trim().equals("Test encrypted document.")) {
    throw new AssertionError("Unexpected document text.");
}
```

### Base URI สำหรับ HTML Load Options

**ภาพรวม:**  
การระบุ **set html base uri** ช่วยให้สามารถแก้ไข URI แบบ relative ได้ โดยเฉพาะเมื่อทำงานกับรูปภาพหรือทรัพยากรที่เชื่อมโยงอื่น ๆ.

#### ขั้นตอนทีละขั้นตอน

1. **กำหนดค่า Load Options พร้อม Base URI**

```java
HtmlLoadOptions loadOptions = new HtmlLoadOptions(LoadFormat.HTML, "", "path/to/imageDir");
```

2. **โหลดเอกสารและตรวจสอบรูปภาพ**

```java
import com.aspose.words.Document;
import com.aspose.words.NodeType;

Document doc = new Document("path/to/Missing image.html", loadOptions);
Shape imageShape = (Shape) doc.getChildNodes(NodeType.SHAPE, true).get(0);

if (!imageShape.isImage()) {
    throw new AssertionError("Expected an image shape.");
}
```

### นำเข้า HTML Select เป็น Structured Document Tag

**ภาพรวม:**  
เพื่อ **configure html control** คุณสามารถนำเข้าองค์ประกอบ `<select>` เป็น Structured Document Tags ซึ่งให้การควบคุมที่ละเอียดขึ้นสำหรับฟิลด์ฟอร์มภายในเอกสาร Word.

#### ขั้นตอนทีละขั้นตอน

1. **ตั้งค่า Preferred Control Type**

```java
import com.aspose.words.HtmlLoadOptions;
import com.aspose.words.ControlType;

HtmlLoadOptions loadOptions = new HtmlLoadOptions();
loadOptions.setHtmlControlType(HtmlControlType.StructuredDocumentTag);
```

2. **โหลดเอกสารและตรวจสอบโครงสร้าง**

```java
import com.aspose.words.Document;
import com.aspose.words.NodeType;
import com.aspose.words.StructuredDocumentTag;

Document doc = new Document("path/to/Input HTML with select element.html", loadOptions);
StructuredDocumentTag sdt = (StructuredDocumentTag)doc.getChild(NodeType.STRUCTURED_DOCUMENT_TAG, 0, true);

if (!sdt.getTagName().equals("Select")) {
    throw new AssertionError("Expected a Structured Document Tag with tag name 'Select'.");
}
```

## ปัญหาที่พบบ่อยและวิธีแก้

| ปัญหา | สาเหตุ | วิธีแก้ |
|-------|--------|-----|
| กราฟิก VML ไม่แสดง | แฟล็ก `supportVml` ถูกปล่อยเป็นค่าเริ่มต้น (`false`) | ตรวจสอบให้แน่ใจว่าได้ตั้งค่า `loadOptions.setSupportVml(true)` ก่อนทำการโหลด |
| รูปภาพหายหลังจากโหลด | ไม่สามารถแก้ไขเส้นทางแบบ relative ได้ | ใช้ **set html base uri** (`loadOptions.setBaseUri(...)`) เพื่อชี้ไปยังโฟลเดอร์ที่ถูกต้อง |
| HTML ที่ป้องกันด้วยรหัสผ่านทำให้เกิดข้อยกเว้น | ไม่ได้ส่งรหัสผ่าน | ส่งรหัสผ่านไปยัง `new HtmlLoadOptions("yourPassword")` |
| ฟอร์มคอนโทรลแสดงเป็นข้อความธรรมดา | `HtmlControlType` ไม่ถูกต้อง | ตั้งค่า `loadOptions.setHtmlControlType(HtmlControlType.StructuredDocumentTag)` หรือ `FormField` ตามต้องการ |
| คำเตือนที่ไม่คาดคิด | องค์ประกอบ HTML ที่ไม่ได้จัดการ | Implement `IWarningCallback` เพื่อจับและตรวจสอบคำเตือน |

## คำถามที่พบบ่อย

**Q: สามารถโหลดไฟล์ HTML ที่มีทั้ง VML และกราฟิก SVG สมัยใหม่ได้หรือไม่?**  
A: ได้. เปิดใช้งาน VML ด้วย `setSupportVml(true)`; SVG จะถูกจัดการโดยอัตโนมัติโดย Aspose.Words.

**Q: จะเข้ารหัสเอกสาร HTML โดยไม่ใช้ใบรับรองดิจิทัลอย่างไร?**  
A: ใช้คอนสตรัคเตอร์ `HtmlLoadOptions` ที่รับพารามิเตอร์รหัสผ่านและบันทึกเอกสารด้วย `Document.save(..., SaveFormat.HTML)` หลังจากตั้งค่ารหัสผ่านแล้ว.

**Q: จะเกิดอะไรขึ้นหาก base URI ชี้ไปยังโฟลเดอร์ที่ไม่มีอยู่?**  
A: Aspose.Words จะโยน `FileNotFoundException` สำหรับทรัพยากรที่หายไป. ตรวจสอบเส้นทางก่อนทำการโหลด.

**Q: สามารถเปลี่ยนประเภทคอนโทรลเริ่มต้นสำหรับองค์ประกอบฟอร์ม HTML ทั้งหมดได้หรือไม่?**  
A: ได้. ใช้ `loadOptions.setHtmlControlType(HtmlControlType.StructuredDocumentTag)` เพื่อใช้ทั่วทั้งโปรเจกต์.

**Q: การเรียกใช้ warning callbacks ปลอดภัยต่อการทำงานหลายเธรดหรือไม่?**  
A: การทำงานของ callback ควรเป็น thread‑safe หากคุณวางแผนโหลดเอกสารพร้อมกัน. ใช้คอลเลกชันที่ synchronized หรือ thread‑local storage.

**อัปเดตล่าสุด:** 2026-02-06  
**ทดสอบด้วย:** Aspose.Words for Java 25.3  
**ผู้เขียน:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}