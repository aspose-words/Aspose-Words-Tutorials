---
"date": "2025-03-28"
"description": "บทช่วยสอนเกี่ยวกับโค้ดสำหรับ Aspose.Words Java"
"title": "การบันทึกหน้าและรูปภาพที่กำหนดเองใน Java ด้วย Aspose.Words Callbacks"
"url": "/th/java/images-shapes/aspose-words-java-callback-custom-savings/"
"weight": 1
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}


# วิธีการใช้ Custom Page และการบันทึกภาพด้วย Aspose.Words Callbacks ใน Java

## การแนะนำ

ในภูมิทัศน์ดิจิทัลของปัจจุบัน การแปลงเอกสารเป็นรูปแบบต่างๆ เช่น HTML ถือเป็นสิ่งสำคัญสำหรับการเผยแพร่เนื้อหาอย่างราบรื่นบนแพลตฟอร์มต่างๆ อย่างไรก็ตาม การจัดการผลลัพธ์ เช่น การปรับแต่งชื่อไฟล์สำหรับหน้าหรือรูปภาพในระหว่างการแปลงอาจเป็นเรื่องท้าทาย บทช่วยสอนนี้ใช้ประโยชน์จาก Aspose.Words สำหรับ Java เพื่อแก้ปัญหานี้โดยใช้คอลแบ็กเพื่อปรับแต่งกระบวนการบันทึกหน้าและรูปภาพอย่างมีประสิทธิภาพ

### สิ่งที่คุณจะได้เรียนรู้
- การใช้งาน Page Saving Callback ใน Java ด้วย Aspose.Words
- การใช้การบันทึกการโทรกลับส่วนเอกสารเพื่อแบ่งเอกสารออกเป็นส่วนที่กำหนดเอง
- การปรับแต่งชื่อไฟล์สำหรับรูปภาพในระหว่างการแปลง HTML
- การจัดการสไตล์ชีต CSS ในระหว่างการแปลงเอกสาร

พร้อมที่จะเริ่มใช้งานหรือยัง เริ่มต้นด้วยการตั้งค่าสภาพแวดล้อมของคุณและสำรวจความสามารถอันทรงพลังของคอลแบ็ก Aspose.Words

## ข้อกำหนดเบื้องต้น

ก่อนที่เราจะเริ่ม ให้แน่ใจว่าคุณมีสิ่งต่อไปนี้:

### ห้องสมุดที่จำเป็น
- **Aspose.คำศัพท์สำหรับภาษา Java**:ไลบรารีที่มีประสิทธิภาพสำหรับการทำงานกับเอกสาร Word คุณต้องใช้เวอร์ชัน 25.3 ขึ้นไป
  
### ข้อกำหนดการตั้งค่าสภาพแวดล้อม
- Java Development Kit (JDK) ติดตั้งอยู่บนเครื่องของคุณ
- IDE เช่น IntelliJ IDEA หรือ Eclipse

### ข้อกำหนดเบื้องต้นของความรู้
- ความเข้าใจพื้นฐานเกี่ยวกับการเขียนโปรแกรม Java และการดำเนินการ I/O ไฟล์
- ความคุ้นเคยกับ Maven หรือ Gradle สำหรับการจัดการการอ้างอิง

## การตั้งค่า Aspose.Words

หากต้องการเริ่มใช้ Aspose.Words คุณต้องรวมไว้ในโปรเจ็กต์ของคุณ ดังต่อไปนี้:

### การพึ่งพา Maven
เพิ่มสิ่งต่อไปนี้ลงในของคุณ `pom.xml`-
```xml
<dependency>
  <groupId>com.aspose</groupId>
  <artifactId>aspose-words</artifactId>
  <version>25.3</version>
</dependency>
```

### การอ้างอิงของ Gradle
รวมสิ่งนี้ไว้ในของคุณ `build.gradle` ไฟล์:
```gradle
implementation 'com.aspose:aspose-words:25.3'
```

#### ขั้นตอนการรับใบอนุญาต

หากต้องการปลดล็อคคุณสมบัติทั้งหมด คุณต้องมีใบอนุญาต ขั้นตอนมีดังนี้:
1. **ทดลองใช้งานฟรี**:เริ่มต้นด้วยใบอนุญาตชั่วคราวเพื่อสำรวจฟังก์ชันการทำงานทั้งหมด
2. **ซื้อใบอนุญาต**:หากต้องการใช้ในระยะยาว ควรพิจารณาซื้อใบอนุญาตเชิงพาณิชย์

### การเริ่มต้นและการตั้งค่าเบื้องต้น
```java
License license = new License();
license.setLicense("path/to/your/license/file");
```

## คู่มือการใช้งาน

มาแบ่งการใช้งานออกเป็นคุณสมบัติหลักโดยใช้คอลแบ็ก Aspose.Words

### คุณสมบัติ 1: การบันทึกหน้าการโทรกลับ

คุณลักษณะนี้สาธิตการบันทึกแต่ละหน้าของเอกสารเป็นไฟล์ HTML แยกกันโดยมีชื่อไฟล์ที่กำหนดเอง

#### ภาพรวม
การปรับแต่งไฟล์เอาต์พุตสำหรับหน้าแต่ละหน้าช่วยให้จัดเก็บได้เป็นระเบียบและค้นหาได้ง่าย

#### ขั้นตอนการดำเนินการ

##### ขั้นตอนที่ 1: ดำเนินการตาม `IPageSavingCallback` อินเทอร์เฟซ
```java
import com.aspose.words.*;

public class CustomFileNamePageSavingCallback implements IPageSavingCallback {
    public void pageSaving(PageSavingArgs args) throws Exception {
        String outFileName = "YOUR_DOCUMENT_DIRECTORY/SavingCallback.PageFileNames.Page_" + args.getPageIndex() + ".html";
        args.setPageFileName(outFileName);

        try (FileOutputStream outputStream = new FileOutputStream(outFileName)) {
            args.setPageStream(outputStream);
        }

        assert !args.getKeepPageStreamOpen();
    }
}
```

- **คำอธิบายพารามิเตอร์**-
  - `PageSavingArgs`: มีข้อมูลเกี่ยวกับหน้าที่กำลังถูกบันทึก
  - `setPageFileName()`: กำหนดชื่อไฟล์ที่กำหนดเองสำหรับแต่ละหน้า HTML

#### เคล็ดลับการแก้ไขปัญหา
- ตรวจสอบให้แน่ใจว่าเส้นทางไดเร็กทอรีถูกต้องเพื่อหลีกเลี่ยง `FileNotFoundException`-
- ตรวจสอบว่าการอนุญาตไฟล์อนุญาตให้ดำเนินการเขียนได้

### คุณสมบัติ 2: การบันทึกส่วนเอกสารแบบเรียกกลับ

แบ่งเอกสารออกเป็นส่วนๆ เช่น หน้า คอลัมน์ หรือส่วน และบันทึกโดยใช้ชื่อไฟล์ที่กำหนดเอง

#### ภาพรวม
ฟีเจอร์นี้ช่วยจัดการโครงสร้างเอกสารที่ซับซ้อนโดยให้สามารถควบคุมไฟล์เอาต์พุตได้อย่างละเอียด

#### ขั้นตอนการดำเนินการ

##### ขั้นตอนที่ 1: ดำเนินการตาม `IDocumentPartSavingCallback` อินเทอร์เฟซ
```java
import com.aspose.words.*;
import org.apache.commons.io.FilenameUtils;
import java.io.FileOutputStream;
import java.text.MessageFormat;

public class SavedDocumentPartRename implements IDocumentPartSavingCallback {
    private int mCount = 0;
    private final String mOutFileName;
    private final int mDocumentSplitCriteria;

    public SavedDocumentPartRename(String outFileName, int documentSplitCriteria) {
        this.mOutFileName = outFileName;
        this.mDocumentSplitCriteria = documentSplitCriteria;
    }

    public void documentPartSaving(DocumentPartSavingArgs args) throws Exception {
        String partType = determinePartType();
        String partFileName = MessageFormat.format("{0} part {1}, of type {2}.{3}", 
                                                   mOutFileName, ++mCount, partType, FilenameUtils.getExtension(args.getDocumentPartFileName()));
        
        args.setDocumentPartFileName(partFileName);

        try (FileOutputStream outputStream = new FileOutputStream("YOUR_DOCUMENT_DIRECTORY" + partFileName)) {
            args.setDocumentPartStream(outputStream);
        }

        assert args.getDocumentPartStream() != null;
        assert !args.getKeepDocumentPartStreamOpen();
    }

    private String determinePartType() {
        switch (mDocumentSplitCriteria) {
            case DocumentSplitCriteria.PAGE_BREAK: return "Page";
            case DocumentSplitCriteria.COLUMN_BREAK: return "Column";
            case DocumentSplitCriteria.SECTION_BREAK: return "Section";
            case DocumentSplitCriteria.HEADING_PARAGRAPH: return "Paragraph from heading";
            default: return "";
        }
    }
}
```

- **คำอธิบายพารามิเตอร์**-
  - `DocumentPartSavingArgs`: ประกอบด้วยข้อมูลเกี่ยวกับส่วนของเอกสารที่ถูกบันทึก
  - `setDocumentPartFileName()`: กำหนดชื่อไฟล์ที่กำหนดเองให้กับแต่ละส่วนของเอกสาร

#### เคล็ดลับการแก้ไขปัญหา
- ให้แน่ใจว่ามีการตั้งชื่อแบบสอดคล้องกันเพื่อหลีกเลี่ยงความสับสนในไฟล์เอาต์พุต
- จัดการข้อยกเว้นอย่างเหมาะสมเมื่อเขียนไฟล์

### คุณสมบัติที่ 3: การบันทึกภาพการโทรกลับ

ปรับแต่งชื่อไฟล์สำหรับรูปภาพที่สร้างในระหว่างการแปลง HTML เพื่อรักษาความเป็นระเบียบและความชัดเจน

#### ภาพรวม
คุณลักษณะนี้ช่วยให้แน่ใจว่ารูปภาพที่สร้างจากเอกสาร Word จะมีชื่อไฟล์ที่อธิบายรายละเอียด ทำให้จัดการได้ง่ายยิ่งขึ้น

#### ขั้นตอนการดำเนินการ

##### ขั้นตอนที่ 1: ดำเนินการตาม `IImageSavingCallback` อินเทอร์เฟซ
```java
import com.aspose.words.*;
import org.apache.commons.io.FilenameUtils;
import java.io.FileOutputStream;
import java.text.MessageFormat;

public static class SavedImageRename implements IImageSavingCallback {
    private int mCount = 0;
    private final String mOutFileName;

    public SavedImageRename(String outFileName) {
        this.mOutFileName = outFileName;
    }

    public void imageSaving(ImageSavingArgs args) throws Exception {
        String imageFileName = MessageFormat.format("{0} shape {1}, of type {2}.{3}", 
                                                    mOutFileName, ++mCount, args.getCurrentShape().getShapeType(), FilenameUtils.getExtension(args.getImageFileName()));
        
        args.setImageFileName(imageFileName);

        args.setImageStream(new FileOutputStream("YOUR_DOCUMENT_DIRECTORY" + imageFileName));

        assert args.getImageStream() != null;
        assert args.isImageAvailable();
        assert !args.getKeepImageStreamOpen();
    }
}
```

- **คำอธิบายพารามิเตอร์**-
  - `ImageSavingArgs`: ประกอบด้วยข้อมูลเกี่ยวกับภาพที่ถูกบันทึก
  - `setImageFileName()`: ตั้งค่าชื่อไฟล์แบบกำหนดเองให้กับภาพเอาต์พุตแต่ละภาพ

#### เคล็ดลับการแก้ไขปัญหา
- ตรวจสอบให้แน่ใจว่าเส้นทางไดเร็กทอรีถูกต้องเพื่อป้องกันข้อผิดพลาดระหว่างการดำเนินการไฟล์
- ยืนยันว่ามีการรวมสิ่งที่ต้องมีทั้งหมด เช่น Apache Commons IO ไว้ในโปรเจ็กต์ของคุณแล้ว

### คุณสมบัติที่ 4: การบันทึก CSS Callback

จัดการสไตล์ชีต CSS ได้อย่างมีประสิทธิภาพในระหว่างการแปลง HTML โดยการตั้งชื่อไฟล์และสตรีมแบบกำหนดเอง

#### ภาพรวม
ฟีเจอร์นี้ช่วยให้คุณควบคุมวิธีการสร้างและตั้งชื่อไฟล์ CSS เพื่อให้แน่ใจถึงความสอดคล้องกันในเอกสารที่ส่งออกต่างๆ

#### ขั้นตอนการดำเนินการ

##### ขั้นตอนที่ 1: ดำเนินการตาม `ICssSavingCallback` อินเทอร์เฟซ
```java
import com.aspose.words.*;
import java.io.FileOutputStream;

public static class CustomCssSavingCallback implements ICssSavingCallback {
    private final String mCssTextFileName;
    private final boolean mIsExportNeeded;
    private final boolean mKeepCssStreamOpen;

    public CustomCssSavingCallback(String cssDocFilename, boolean isExportNeeded, boolean keepCssStreamOpen) {
        this.mCssTextFileName = cssDocFilename;
        this.mIsExportNeeded = isExportNeeded;
        this.mKeepCssStreamOpen = keepCssStreamOpen;
    }

    public void cssSaving(CssSavingArgs args) throws Exception {
        args.setCssStream(new FileOutputStream(mCssTextFileName));
        args.isExportNeeded(mIsExportNeeded);
        args.setKeepCssStreamOpen(mKeepCssStreamOpen);
    }
}
```

- **คำอธิบายพารามิเตอร์**-
  - `CssSavingArgs`: ประกอบด้วยข้อมูลเกี่ยวกับ CSS ที่ถูกบันทึก
  - `setCssStream()`: ตั้งค่าสตรีมแบบกำหนดเองให้กับไฟล์ CSS เอาท์พุต

#### เคล็ดลับการแก้ไขปัญหา
- ตรวจสอบว่าเส้นทางไฟล์ CSS ถูกระบุอย่างถูกต้องเพื่อหลีกเลี่ยงข้อผิดพลาดในการเขียน
- ให้แน่ใจว่ามีการกำหนดชื่อที่สอดคล้องกันเพื่อให้ระบุไฟล์ CSS ได้ง่าย

## การประยุกต์ใช้งานจริง

ต่อไปนี้เป็นกรณีการใช้งานจริงบางส่วนที่สามารถนำคุณลักษณะเหล่านี้ไปใช้:

1. **ระบบจัดการเอกสาร**:จัดระเบียบส่วนเอกสารและรูปภาพให้เป็นแบบอัตโนมัติเพื่อการค้นคืนและการจัดการที่ดีขึ้น
2. **การเผยแพร่ทางเว็บไซต์**:ปรับแต่งการส่งออก HTML ด้วยชื่อไฟล์ที่เฉพาะเจาะจงเพื่อรักษาโครงสร้างไดเร็กทอรีที่สะอาดบนเซิร์ฟเวอร์ของคุณ
3. **พอร์ทัลเนื้อหา**:ใช้การโทรกลับเพื่อให้แน่ใจว่ามีรูปแบบการตั้งชื่อที่สอดคล้องกันในเนื้อหาประเภทต่างๆ เพื่อเพิ่มประสิทธิภาพ SEO และประสบการณ์ของผู้ใช้

## การพิจารณาประสิทธิภาพ

เมื่อนำคุณลักษณะเหล่านี้ไปใช้ ควรพิจารณาเคล็ดลับประสิทธิภาพดังต่อไปนี้:

- **เพิ่มประสิทธิภาพการดำเนินการ I/O ไฟล์**:ลดขนาดการเปิดไฟล์ให้เหลือน้อยที่สุดโดยใช้ try-with-resources สำหรับการจัดการทรัพยากรอัตโนมัติ
- **การประมวลผลแบบแบตช์**จัดการเอกสารขนาดใหญ่เป็นชุดเล็กๆ เพื่อลดการใช้หน่วยความจำและปรับปรุงความเร็วในการประมวลผล
- **การจัดการทรัพยากร**:ตรวจสอบทรัพยากรระบบเพื่อป้องกันการคอขวดระหว่างกระบวนการแปลง

## บทสรุป

ในบทช่วยสอนนี้ คุณจะได้เรียนรู้วิธีการใช้งานการบันทึกหน้าและรูปภาพแบบกำหนดเองด้วยคอลแบ็ก Aspose.Words ใน Java การใช้ประโยชน์จากฟีเจอร์อันทรงพลังเหล่านี้จะช่วยให้คุณปรับปรุงการจัดการเอกสารและปรับปรุงการแปลง HTML ในแอปพลิเคชันของคุณได้ 

### ขั้นตอนต่อไป
- สำรวจฟังก์ชัน Aspose.Words เพิ่มเติมเพื่อขยายความสามารถในการประมวลผลเอกสารของคุณเพิ่มเติม
- ทดลองใช้การกำหนดค่าการโทรกลับที่แตกต่างกันเพื่อให้เหมาะกับความต้องการเฉพาะของคุณ

### การเรียกร้องให้ดำเนินการ
ลองใช้โซลูชันนี้วันนี้และสัมผัสกับประโยชน์ของการส่งออกเอกสารที่กำหนดเองได้โดยตรง!

## ส่วนคำถามที่พบบ่อย

1. **Aspose.Words สำหรับ Java คืออะไร?**
   - ไลบรารีที่ช่วยให้นักพัฒนาสามารถทำงานกับเอกสาร Word ในแอปพลิเคชัน Java พร้อมด้วยฟีเจอร์เช่นการแปลง การแก้ไข และการเรนเดอร์

2. **ฉันจะจัดการเอกสารขนาดใหญ่อย่างมีประสิทธิภาพด้วย Aspose.Words ได้อย่างไร**
   - ใช้การประมวลผลแบบแบตช์และเพิ่มประสิทธิภาพการดำเนินการ I/O ของไฟล์เพื่อจัดการการใช้หน่วยความจำอย่างมีประสิทธิภาพ

3. **ฉันสามารถปรับแต่งชื่อไฟล์สำหรับองค์ประกอบเอกสารอื่นๆ นอกเหนือจากหน้าและรูปภาพได้หรือไม่**
   - ใช่ คุณสามารถใช้การโทรกลับเพื่อปรับแต่งชื่อไฟล์สำหรับส่วนต่าง ๆ ของเอกสาร รวมถึงส่วนและคอลัมน์

4. **ปัญหาทั่วไปที่มักเกิดขึ้นเมื่อตั้งค่า Aspose.Words ในโครงการ Maven มีอะไรบ้าง**
   - ให้แน่ใจว่าคุณ `pom.xml` รวมถึงเวอร์ชันการอ้างอิงที่ถูกต้องและการตั้งค่าที่เก็บข้อมูลของคุณอนุญาตให้เข้าถึงไลบรารีของ Aspose

5. **ฉันจะจัดการไฟล์ CSS ในระหว่างการแปลง HTML ด้วย Aspose.Words ได้อย่างไร**
   - การดำเนินการตาม `ICssSavingCallback` อินเทอร์เฟซสำหรับปรับแต่งวิธีการตั้งชื่อและจัดเก็บไฟล์ CSS ในระหว่างการแปลงเอกสาร

## ทรัพยากร

- **เอกสารประกอบ**- [เอกสารอ้างอิง Aspose.Words Java](https://reference.aspose.com/words/java/)
- **ดาวน์โหลด**- [Aspose.Words สำหรับการเปิดตัว Java](https://releases.aspose.com/words/java/)
- **ซื้อ**- [ซื้อใบอนุญาต Aspose](https://purchase.aspose.com/buy)
- **ทดลองใช้งานฟรี**- [Aspose.Words ทดลองใช้งานฟรี](https://releases.aspose.com/words/java/)
- **ใบอนุญาตชั่วคราว**- [รับใบอนุญาตชั่วคราว](https://purchase.aspose.com/temporary-license/)
- **สนับสนุน**- [ฟอรั่ม Aspose](https://forum.aspose.com/c/words/10)

หากทำตามคำแนะนำนี้ คุณจะสามารถนำคุณลักษณะการบันทึกเอกสารแบบกำหนดเองไปใช้ในแอปพลิเคชัน Java ได้อย่างมีประสิทธิภาพโดยใช้คอลแบ็ก Aspose.Words ขอให้สนุกกับการเขียนโค้ด!

{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}