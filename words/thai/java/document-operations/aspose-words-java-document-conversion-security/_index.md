---
"date": "2025-03-28"
"description": "เรียนรู้วิธีการแปลงเอกสารและรักษาความปลอดภัยโดยใช้ Aspose.Words สำหรับ Java แปลงเป็น ODT ตรวจสอบให้แน่ใจว่าเป็นไปตามโครงร่าง และเข้ารหัสเอกสารได้อย่างง่ายดาย"
"title": "การแปลงเอกสาร Java และความปลอดภัยสำหรับไฟล์ ODT ของ Aspose.Words"
"url": "/th/java/document-operations/aspose-words-java-document-conversion-security/"
"weight": 1
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}


# เรียนรู้การแปลงเอกสารและการรักษาความปลอดภัยด้วย Aspose.Words Java

## การแนะนำ

ในแวดวงการจัดการเอกสาร การแปลงและรักษาความปลอดภัยเอกสารอย่างมีประสิทธิภาพถือเป็นสิ่งสำคัญสำหรับนักพัฒนาและธุรกิจ ไม่ว่าจะเป็นการรับรองความเข้ากันได้กับเวอร์ชันเก่าของโครงร่างหรือการปกป้องข้อมูลที่ละเอียดอ่อนผ่านการเข้ารหัส งานเหล่านี้อาจดูยุ่งยากหากไม่มีเครื่องมือที่เหมาะสม บทช่วยสอนนี้เน้นที่การใช้ **Aspose.คำศัพท์สำหรับภาษา Java** เพื่อปรับปรุงการส่งออกเอกสารเป็นรูปแบบ OpenDocument Text (ODT) พร้อมทั้งยังคงปฏิบัติตามโครงร่างและใช้มาตรการรักษาความปลอดภัยที่แข็งแกร่ง

ในคู่มือนี้ คุณจะได้เรียนรู้วิธีการ:
- ส่งออกเอกสารที่เป็นไปตามข้อกำหนด ODT 1.1
- ใช้หน่วยการวัดที่แตกต่างกันในเอกสาร ODT
- เข้ารหัสไฟล์ ODT/OTT ด้วยรหัสผ่านโดยใช้ Aspose.Words สำหรับ Java

มาเริ่มกันเลย!

## ข้อกำหนดเบื้องต้น

ก่อนที่เราจะเริ่ม ให้แน่ใจว่าคุณได้ตั้งค่าสิ่งต่อไปนี้แล้ว:

### ห้องสมุดที่จำเป็น
คุณจะต้อง **Aspose.คำศัพท์สำหรับภาษา Java** เวอร์ชัน 25.3 ขึ้นไป ต่อไปนี้เป็นวิธีรวมไว้ในโปรเจ็กต์ของคุณโดยใช้ Maven หรือ Gradle:

#### เมเวน:
```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>25.3</version>
</dependency>
```

#### เกรเดิ้ล:
```gradle
implementation 'com.aspose:aspose-words:25.3'
```

### การตั้งค่าสภาพแวดล้อม
ตรวจสอบให้แน่ใจว่าคุณได้ติดตั้ง Java บนเครื่องของคุณและมี IDE หรือตัวแก้ไขข้อความที่กำหนดค่าสำหรับการพัฒนา Java

### ข้อกำหนดเบื้องต้นของความรู้
ขอแนะนำให้มีความเข้าใจพื้นฐานเกี่ยวกับการเขียนโปรแกรม Java เพื่อปฏิบัติตามบทช่วยสอนนี้ได้อย่างมีประสิทธิผล

## การตั้งค่า Aspose.Words

หากต้องการเริ่มใช้ Aspose.Words ขั้นแรกต้องแน่ใจว่าได้ผสานรวมเข้ากับโปรเจ็กต์ของคุณอย่างถูกต้อง ขั้นตอนมีดังนี้:

1. **การขอใบอนุญาต**:คุณสามารถรับใบอนุญาตทดลองใช้งานฟรีได้จาก [อาโปเซ่](https://purchase.aspose.com/temporary-license/) เพื่อทดสอบคุณสมบัติทั้งหมดโดยไม่มีข้อจำกัด
   
2. **การเริ่มต้นขั้นพื้นฐาน**-
   ```java
   import com.aspose.words.Document;

   public class AsposeSetup {
       public static void main(String[] args) throws Exception {
           // โหลดเอกสารจากดิสก์
           Document doc = new Document("path/to/your/document.docx");
           
           // บันทึกเป็นรูปแบบ ODT เพื่อเป็นตัวอย่างการใช้งาน
           doc.save("output/path/OdtSaveOptions.odt", com.aspose.words.SaveFormat.ODT);
       }
   }
   ```

## คู่มือการใช้งาน

### การส่งออกเอกสารไปยัง ODT Schema 1.1

คุณลักษณะนี้ช่วยให้คุณมั่นใจได้ว่าเอกสารที่ส่งออกเป็นไปตามรูปแบบ ODT 1.1 ซึ่งจำเป็นสำหรับความเข้ากันได้กับแอปพลิเคชันบางตัว

#### ภาพรวม
ตัวอย่างโค้ดสาธิตวิธีการส่งออกเอกสารในขณะที่กำหนดข้อกำหนดโครงร่างและหน่วยการวัดเฉพาะ

#### การดำเนินการแบบทีละขั้นตอน

**3.1 กำหนดค่าตัวเลือกการส่งออก**
```java
import com.aspose.words.Document;
import com.aspose.words.OdtSaveOptions;

// โหลดเอกสาร Word ต้นฉบับของคุณ
Document document = new Document("YOUR_DOCUMENT_DIRECTORY/Rendering.docx");

// เริ่มต้นตัวเลือกการบันทึก ODT และกำหนดค่าการปฏิบัติตามโครงร่าง
OdtSaveOptions saveOptions = new OdtSaveOptions();
saveOptions.setMeasureUnit(OdtSaveMeasureUnit.CENTIMETERS);
saveOptions.isStrictSchema11(true); // ตั้งค่าเป็นจริงเพื่อให้สอดคล้องกับ ODT 1.1

// บันทึกเอกสารด้วยการตั้งค่าเหล่านี้
document.save("YOUR_OUTPUT_DIRECTORY/OdtSaveOptions.Odt11Schema.odt", saveOptions);
```

**3.2 ตรวจสอบการตั้งค่าการส่งออก**
หลังจากบันทึกแล้ว โปรดตรวจสอบให้แน่ใจว่าการตั้งค่าเอกสารของคุณถูกต้อง:
```java
import com.aspose.words.MeasurementUnits;

Document loadedDoc = new Document("YOUR_OUTPUT_DIRECTORY/OdtSaveOptions.Odt11Schema.odt");
MeasurementUnits mu = loadedDoc.getLayoutOptions().getRevisionOptions().getMeasurementUnit();

assert mu == MeasurementUnits.CENTIMETERS;
```

### การใช้หน่วยการวัดที่แตกต่างกัน
ในบางกรณี คุณอาจจำเป็นต้องส่งออกเอกสารที่มีหน่วยการวัดที่แตกต่างกันเนื่องจากเหตุผลด้านรูปแบบหรือภูมิภาค

#### ภาพรวม
คุณลักษณะนี้ช่วยให้สามารถระบุหน่วยการวัดในเอกสาร ODT ได้ ซึ่งจะทำให้มีความยืดหยุ่นระหว่างระบบเมตริกและระบบอิมพีเรียล

**3.3 ตั้งค่าหน่วยการวัด**
```java
OdtSaveOptions saveOptions = new OdtSaveOptions();
// เลือกหน่วยที่คุณต้องการ: เซนติเมตร หรือ นิ้ว
saveOptions.setMeasureUnit(OdtSaveMeasureUnit.CENTIMETERS);

document.save("YOUR_OUTPUT_DIRECTORY/OdtSaveOptions.Measurements.odt", saveOptions);
```

**3.4 ตรวจสอบหน่วยการวัดในรูปแบบ**
เพื่อให้แน่ใจว่าได้ใช้การวัดที่ถูกต้อง ให้ตรวจสอบเนื้อหาใน styles.xml:
```java
if (saveOptions.getMeasureUnit() == OdtSaveMeasureUnit.CENTIMETERS) {
    assert TestUtil.docPackageFileContainsString(
        "<style:paragraph-properties fo:orphans=\"2\" fo:widows=\"2\" style:tab-stop-distance=\"1.27cm\" />",
        "YOUR_OUTPUT_DIRECTORY/OdtSaveOptions.Measurements.odt", "styles.xml");
}
```

### การเข้ารหัสเอกสาร ODT/OTT
ความปลอดภัยถือเป็นสิ่งสำคัญที่สุดเมื่อต้องจัดการเอกสารสำคัญ ฟีเจอร์นี้สาธิตวิธีการเข้ารหัสเอกสารโดยใช้ Aspose.Words

#### ภาพรวม
เข้ารหัสเอกสารของคุณด้วยรหัสผ่าน เพื่อให้มั่นใจว่าเฉพาะผู้ใช้ที่ได้รับอนุญาตเท่านั้นที่จะเข้าถึงเนื้อหาได้

**3.5 เข้ารหัสเอกสาร**
```java
import com.aspose.words.Document;
import com.aspose.words.OdtSaveOptions;

Document doc = new Document();
doc.getRange().appendText("Hello world!");

OdtSaveOptions saveOptions = new OdtSaveOptions(com.aspose.words.SaveFormat.ODT);
saveOptions.setPassword("@sposeEncrypted_1145");

// บันทึกเอกสารด้วยการเข้ารหัส
doc.save("YOUR_OUTPUT_DIRECTORY/OdtSaveOptions.Encrypt.odt", saveOptions);
```

**3.6 ตรวจสอบการเข้ารหัส**
ตรวจสอบให้แน่ใจว่าเอกสารของคุณได้รับการเข้ารหัส:
```java
import com.aspose.words.FileFormatUtil;
import com.aspose.words.LoadOptions;

FileFormatInfo docInfo = FileFormatUtil.detectFileFormat("YOUR_OUTPUT_DIRECTORY/OdtSaveOptions.Encrypt.odt");
assert docInfo.isEncrypted();

// โหลดเอกสารโดยใช้รหัสผ่านที่ถูกต้อง
Document loadedDoc = new Document(
    "YOUR_OUTPUT_DIRECTORY/OdtSaveOptions.Encrypt.odt",
    new LoadOptions("@sposeEncrypted_1145")
);

assert loadedDoc.getText().trim() == "Hello world!";
```

## การประยุกต์ใช้งานจริง
ต่อไปนี้คือกรณีการใช้งานจริงสำหรับฟีเจอร์เหล่านี้:
1. **การปฏิบัติตามข้อกำหนดทางธุรกิจ**:การส่งออกเอกสารไปยัง ODT 1.1 ช่วยรับประกันความเข้ากันได้กับระบบเดิมในอุตสาหกรรมต่างๆ
2. **ความเป็นสากล**การใช้หน่วยการวัดที่แตกต่างกันทำให้สามารถแบ่งปันเอกสารได้อย่างราบรื่นระหว่างภูมิภาคต่างๆ ที่มีมาตรฐานการวัดที่หลากหลาย
3. **การคุ้มครองข้อมูล**การเข้ารหัสรายงานหรือสัญญาที่ละเอียดอ่อนจะป้องกันการเข้าถึงโดยไม่ได้รับอนุญาต ซึ่งเป็นสิ่งสำคัญสำหรับภาคกฎหมายและการเงิน

## การพิจารณาประสิทธิภาพ
การเพิ่มประสิทธิภาพการทำงานเมื่อใช้ Aspose.Words:
- ลดการใช้รูปภาพความละเอียดสูงในเอกสาร
- รักษาโครงสร้างเอกสารให้เรียบง่ายเพื่อลดเวลาในการประมวลผล
- อัปเดตเป็น Aspose.Words เวอร์ชันล่าสุดสำหรับ Java เป็นประจำเพื่อรับประโยชน์จากการปรับปรุงประสิทธิภาพ

## บทสรุป
ในบทช่วยสอนนี้ คุณจะได้เรียนรู้วิธีการส่งออกและเข้ารหัสเอกสาร ODT อย่างมีประสิทธิภาพโดยใช้ **Aspose.คำศัพท์สำหรับภาษา Java**เทคนิคเหล่านี้ช่วยให้มั่นใจได้ว่าเข้ากันได้กับรูปแบบต่างๆ และเพิ่มความปลอดภัยให้กับเอกสารด้วยการเข้ารหัส หากต้องการสำรวจความสามารถของ Aspose เพิ่มเติม โปรดพิจารณาศึกษาเอกสารประกอบที่ครอบคลุมและทดลองใช้คุณสมบัติเพิ่มเติม

พร้อมที่จะนำโซลูชันเหล่านี้ไปใช้ในโครงการของคุณหรือยัง ไปที่ [เอกสารประกอบ Aspose.Words](https://reference.aspose.com/words/java/) สำหรับข้อมูลเชิงลึกเพิ่มเติม!

## ส่วนคำถามที่พบบ่อย
**ถาม: ฉันจะมั่นใจได้อย่างไรว่าเข้ากันได้กับเวอร์ชัน ODT รุ่นเก่ากว่า**
ก. การใช้ `OdtSaveOptions.isStrictSchema11(true)` เพื่อให้เป็นไปตามข้อกำหนด ODT 1.1

**ถาม: ฉันสามารถสลับระหว่างหน่วยเมตริกและอิมพีเรียลได้อย่างง่ายดายหรือไม่?**
A: ใช่ ตั้งหน่วยการวัดเป็น `OdtSaveOptions.setMeasureUnit()` ไปอย่างใดอย่างหนึ่ง `CENTIMETERS` หรือ `INCHES`-

**ถาม: จะเกิดอะไรขึ้นหากเอกสารของฉันไม่ได้เข้ารหัสตามที่คาดหวัง?**
ก: ตรวจสอบให้แน่ใจว่าคุณได้ตั้งรหัสผ่านโดยใช้ `saveOptions.setPassword()`. ตรวจสอบการเข้ารหัสด้วย `FileFormatUtil-detectFileFormat()`.

**ถาม: ฉันจะแก้ไขปัญหาในการโหลดเอกสารเข้ารหัสได้อย่างไร**
ก: ตรวจสอบให้แน่ใจว่าใช้รหัสผ่านที่ถูกต้องเมื่อโหลดเอกสาร

{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}