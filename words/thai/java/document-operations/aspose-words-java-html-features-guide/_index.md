---
"date": "2025-03-28"
"description": "เรียนรู้วิธีใช้ประโยชน์จาก Aspose.Words สำหรับ Java เพื่อควบคุมการประมวลผลเอกสาร รวมถึงการรองรับ VML การเข้ารหัส ตัวเลือกการนำเข้า HTML และอื่นๆ อีกมากมาย"
"title": "Aspose.Words สำหรับ Java พร้อมคุณลักษณะ HTML ที่ครอบคลุมและคู่มือการจัดการเอกสาร"
"url": "/th/java/document-operations/aspose-words-java-html-features-guide/"
"weight": 1
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}


# ฟีเจอร์ HTML ที่ครอบคลุมพร้อม Aspose.Words สำหรับ Java: คู่มือสำหรับนักพัฒนา

## การแนะนำ

การนำทางในโลกที่ซับซ้อนของการประมวลผลเอกสารอาจเป็นเรื่องท้าทาย โดยเฉพาะอย่างยิ่งเมื่อต้องจัดการกับฟีเจอร์ HTML ต่างๆ ไม่ว่าคุณจะจัดการกับการสนับสนุน Vector Markup Language (VML) เอกสารที่เข้ารหัส หรือลักษณะการนำเข้า HTML เฉพาะ **Aspose.คำศัพท์สำหรับภาษา Java** นำเสนอโซลูชันที่แข็งแกร่ง ในคู่มือนี้ เราจะสำรวจวิธีการนำฟังก์ชันเหล่านี้ไปใช้อย่างราบรื่นโดยใช้ Aspose.Words เพื่อเพิ่มประสิทธิภาพในการประมวลผลเอกสารของคุณ

**สิ่งที่คุณจะได้เรียนรู้:**
- วิธีโหลดเอกสาร HTML ด้วยการรองรับ VML
- เทคนิคในการจัดการ HTML แบบหน้าคงที่และคำเตือน
- วิธีการเข้ารหัสและโหลดเอกสาร HTML ที่ได้รับการป้องกันด้วยรหัสผ่าน
- การใช้ URI ฐานในตัวเลือกการโหลด HTML
- นำเข้าองค์ประกอบอินพุต HTML ในรูปแบบแท็กเอกสารที่มีโครงสร้างหรือฟิลด์ฟอร์ม
- การเพิกเฉย `<noscript>` องค์ประกอบในระหว่างการโหลด HTML
- การกำหนดค่าโหมดการนำเข้าบล็อกเพื่อควบคุมการรักษาโครงสร้าง HTML
- การสนับสนุน `@font-face` กฎสำหรับแบบอักษรที่กำหนดเอง

ด้วยข้อมูลเชิงลึกเหล่านี้ คุณจะพร้อมรับมือกับงานประมวลผล HTML ที่หลากหลาย มาเจาะลึกข้อกำหนดเบื้องต้นและการตั้งค่ากันก่อน!

## ข้อกำหนดเบื้องต้น

ก่อนที่เราจะเริ่มนำคุณลักษณะ HTML ต่างๆ มาใช้กับ Aspose.Words สำหรับ Java โปรดตรวจสอบให้แน่ใจว่าสภาพแวดล้อมของคุณได้รับการตั้งค่าอย่างถูกต้อง:

- **ห้องสมุดที่จำเป็น:** คุณต้องมีไลบรารี Aspose.Words เวอร์ชัน 25.3 ขึ้นไป
- **สภาพแวดล้อมการพัฒนา:** คู่มือนี้จะถือว่าคุณใช้ Maven หรือ Gradle ในการจัดการการอ้างอิง
- **ฐานความรู้:** ความเข้าใจพื้นฐานเกี่ยวกับ Java และความคุ้นเคยกับเอกสาร HTML จะเป็นประโยชน์

## การตั้งค่า Aspose.Words

หากต้องการเริ่มใช้งาน Aspose.Words ก่อนอื่นคุณต้องรวม Aspose.Words ไว้ในโปรเจ็กต์ของคุณ ด้านล่างนี้คือขั้นตอนในการตั้งค่าไลบรารีโดยใช้ Maven และ Gradle:

### เมเวน

เพิ่มการอ้างอิงต่อไปนี้ให้กับของคุณ `pom.xml` ไฟล์:

```xml
<dependency>
  <groupId>com.aspose</groupId>
  <artifactId>aspose-words</artifactId>
  <version>25.3</version>
</dependency>
```

### แกรเดิล

รวมสิ่งนี้ไว้ในของคุณ `build.gradle` ไฟล์:

```gradle
implementation 'com.aspose:aspose-words:25.3'
```

#### การขอใบอนุญาต

Aspose.Words ต้องมีใบอนุญาตจึงจะใช้งานได้เต็มรูปแบบ คุณสามารถรับรุ่นทดลองใช้งานฟรี ขอใบอนุญาตชั่วคราว หรือซื้อใบอนุญาตถาวร เยี่ยมชม [หน้าการซื้อ](https://purchase.aspose.com/buy) สำหรับรายละเอียดเพิ่มเติม

หากต้องการเริ่มต้น Aspose.Words ในโปรเจ็กต์ Java ของคุณ โปรดตรวจสอบให้แน่ใจว่าคุณได้ตั้งค่าใบอนุญาตอย่างถูกต้อง:

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

## คู่มือการใช้งาน

เราจะแบ่งการใช้งานออกเป็นส่วนๆ ตามคุณลักษณะที่เราต้องการใช้งาน

### รองรับ VML ในเอกสาร HTML

**ภาพรวม:**
การโหลดเอกสาร HTML ที่มีหรือไม่มีการสนับสนุน VML ช่วยให้สามารถเรนเดอร์กราฟิกเวกเตอร์ได้อย่างหลากหลาย คุณลักษณะนี้มีความสำคัญเมื่อต้องจัดการกับเอกสารที่มีองค์ประกอบกราฟิก เช่น แผนภูมิและรูปทรง

#### การดำเนินการทีละขั้นตอน:

1. **ตั้งค่าตัวเลือกการโหลด**
   
   ```java
   import com.aspose.words.Document;
   import com.aspose.words.HtmlLoadOptions;

   HtmlLoadOptions loadOptions = new HtmlLoadOptions();
   loadOptions.setSupportVml(true); // เปิดใช้งานการรองรับ VML
   ```

2. **โหลดเอกสาร**
   
   ```java
   Document doc = new Document("path/to/VML conditional.htm", loadOptions);
   ```

3. **ตรวจสอบประเภทภาพ**
   
   ตรวจสอบให้แน่ใจว่าประเภทภาพตรงตามความคาดหวังของคุณ:
   
   ```java
   import com.aspose.words.NodeType;
   import com.aspose.words.Shape;

   Shape imageShape = (Shape) doc.getChild(NodeType.SHAPE, 0, true);
   String expectedImageType = "JPG"; // ปรับตามตรรกะที่แท้จริง

   if (!imageShape.getImageData().getImageType().toString().equals(expectedImageType)) {
       throw new AssertionError("Unexpected image type loaded.");
   }
   ```

### โหลด HTML คงที่และจัดการคำเตือน

**ภาพรวม:**
การโหลดเอกสาร HTML แบบหน้าคงที่สามารถสร้างคำเตือนที่จำเป็นต้องจัดการเพื่อการประมวลผลที่แม่นยำ

#### การดำเนินการทีละขั้นตอน:

1. **กำหนดการเรียกกลับคำเตือน**
   
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

2. **กำหนดค่าตัวเลือกการโหลด**
   
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
การเข้ารหัสเอกสาร HTML ด้วยรหัสผ่านช่วยให้มั่นใจถึงการเข้าถึงที่ปลอดภัยซึ่งถือเป็นสิ่งสำคัญสำหรับข้อมูลที่ละเอียดอ่อน

#### การดำเนินการทีละขั้นตอน:

1. **เตรียมตัวเลือกลายเซ็นดิจิทัล**
   
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

### URI ฐานสำหรับตัวเลือกการโหลด HTML

**ภาพรวม:**
การระบุ URI ฐานช่วยแก้ไข URI ที่เกี่ยวข้อง โดยเฉพาะอย่างยิ่งเมื่อจัดการกับรูปภาพหรือทรัพยากรที่เชื่อมโยงอื่น

#### การดำเนินการทีละขั้นตอน:

1. **กำหนดค่าตัวเลือกการโหลดด้วย URI ฐาน**
   
   ```java
   HtmlLoadOptions loadOptions = new HtmlLoadOptions(LoadFormat.HTML, "", "path/to/imageDir");
   ```

2. **โหลดเอกสารและตรวจสอบภาพ**
   
   ```java
   import com.aspose.words.Document;
   import com.aspose.words.NodeType;

   Document doc = new Document("path/to/Missing image.html", loadOptions);
   Shape imageShape = (Shape) doc.getChildNodes(NodeType.SHAPE, true).get(0);

   if (!imageShape.isImage()) {
       throw new AssertionError("Expected an image shape.");
   }
   ```

### นำเข้า HTML เลือกเป็นแท็กเอกสารที่มีโครงสร้าง

**ภาพรวม:**
การนำเข้า `<select>` องค์ประกอบเป็นแท็กเอกสารที่มีโครงสร้างช่วยให้สามารถควบคุมและจัดรูปแบบภายในเอกสาร Word ได้ดีขึ้น

#### การดำเนินการทีละขั้นตอน:

1. **ตั้งค่าประเภทการควบคุมที่ต้องการ**
   
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

{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}