---
date: '2025-11-26'
description: เรียนรู้วิธีตั้งค่าสีพื้นหลังของหน้าโดยใช้ Aspose.Words for Java, เปลี่ยนสีหน้าในเอกสาร
  Word, รวมส่วนของเอกสาร, และนำเข้าส่วนจากเอกสารอย่างมีประสิทธิภาพ
keywords:
- Aspose.Words for Java
- Document initialization in Java
- Customize page backgrounds with Java
- Import nodes between documents using Java
language: th
title: ตั้งค่าสีพื้นหลังของหน้าโดยใช้ Aspose.Words for Java – คู่มือ
url: /java/content-management/aspose-words-java-document-manipulation-guide/
weight: 1
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# ตั้งค่าสีพื้นหลังของหน้าโดยใช้ Aspose.Words for Java

ในบทแนะนำนี้คุณจะได้เรียนรู้ **วิธีตั้งค่าสีพื้นหลังของหน้า** ด้วย Aspose.Words for Java และสำรวจงานที่เกี่ยวข้องเช่น **การเปลี่ยนสีหน้าในเอกสาร Word**, **การรวมส่วนของเอกสาร**, **การสร้างภาพพื้นหลังของเอกสาร**, และ **การนำเข้าส่วนจากเอกสาร** เมื่อเสร็จสิ้นคุณจะมีเวิร์กโฟลว์ที่พร้อมใช้งานในระดับผลิตเพื่อปรับแต่งลักษณะและโครงสร้างของไฟล์ Word อย่างเป็นโปรแกรม

## คำตอบอย่างรวดเร็ว
- **คลาสหลักที่ใช้ทำงานคืออะไร?** `com.aspose.words.Document`
- **เมธอดใดที่ตั้งค่าสีพื้นหลังแบบเดียวกัน?** `Document.setPageColor(Color)`
- **ฉันสามารถนำเข้าส่วนจากเอกสารอื่นได้หรือไม่?** ได้, ใช้ `Document.importNode(...)`
- **ต้องมีลิขสิทธิ์สำหรับการใช้งานในผลิตหรือไม่?** ต้องมี, ต้องซื้อใบอนุญาต Aspose.Words
- **รองรับบน Java 8+ หรือไม่?** แน่นอน – ทำงานกับ JDK สมัยใหม่ทั้งหมด

## “ตั้งค่าสีพื้นหลังของหน้า” คืออะไร?
การตั้งค่าสีพื้นหลังของหน้าเปลี่ยนแคนวาสภาพมองเห็นของทุกหน้าภายในเอกสาร Word ซึ่งมีประโยชน์สำหรับการสร้างแบรนด์, การเพิ่มความอ่านง่าย, หรือการสร้างแบบฟอร์มที่พิมพ์ออกมามีสีอ่อน

## ทำไมต้องเปลี่ยนสีหน้าในเอกสาร Word?
การเปลี่ยนสีหน้าสามารถ:
- ทำให้เอกสารถูกจัดให้สอดคล้องกับโทนสีขององค์กร  
- ลดความเมื่อยล้าของดวงตาสำหรับรายงานยาว  
- เน้นส่วนต่าง ๆ เมื่อพิมพ์บนกระดาษสี  

## ข้อกำหนดเบื้องต้น

ก่อนเริ่มทำงาน ตรวจสอบให้แน่ใจว่าคุณมี:

- **Aspose.Words for Java** เวอร์ชัน 25.3 หรือใหม่กว่า  
- **JDK** (Java 8 หรือใหม่กว่า) ที่ติดตั้งไว้  
- IDE เช่น **IntelliJ IDEA** หรือ **Eclipse**  
- ความรู้พื้นฐานของ Java และความคุ้นเคยกับ **Maven** หรือ **Gradle** สำหรับการจัดการ dependency  

## การตั้งค่า Aspose.Words

### Maven
เพิ่มโค้ดสแนปนี้ลงในไฟล์ `pom.xml` ของคุณ:

```xml
<dependency>
  <groupId>com.aspose</groupId>
  <artifactId>aspose-words</artifactId>
  <version>25.3</version>
</dependency>
```

### Gradle
ใส่โค้ดต่อไปนี้ในไฟล์ `build.gradle` ของคุณ:

```gradle
implementation 'com.aspose:aspose-words:25.3'
```

#### ขั้นตอนการรับลิขสิทธิ์
1. **ทดลองใช้ฟรี** – ทดลองใช้คุณสมบัติทั้งหมดเป็นเวลา 30 วัน  
2. **ลิขสิทธิ์ชั่วคราว** – ปลดล็อกฟังก์ชันเต็มระหว่างการประเมินผล  
3. **ซื้อ** – รับลิขสิทธิ์ถาวรสำหรับการใช้งานในผลิต

### การเริ่มต้นและตั้งค่าพื้นฐาน

นี่คือตัวอย่างโปรแกรม Java ขั้นต่ำที่สร้างเอกสารเปล่า:

```java
import com.aspose.words.Document;

public class DocumentSetup {
    public static void main(String[] args) throws Exception {
        // Initialize a new document
        Document doc = new Document();
        
        System.out.println("Document initialized successfully!");
    }
}
```

เมื่อไลบรารีพร้อมแล้ว เราจะไปสำรวจฟีเจอร์หลักต่อไป

## คู่มือการดำเนินการ

### ฟีเจอร์ 1: การเริ่มต้นเอกสาร

#### ภาพรวม
การสร้าง `GlossaryDocument` ภายในเอกสารหลักช่วยให้คุณจัดการพจนานุกรม, สไตล์, และส่วนกำหนดเองในคอนเทนเนอร์ที่แยกออกมาอย่างเป็นระเบียบ

```java
import com.aspose.words.Document;
import com.aspose.words.GlossaryDocument;

public class DocumentInitialization {
    public static void constructor() throws Exception {
        // Create a new document instance
        Document doc = new Document();

        // Initialize and set a GlossaryDocument to the main document
        GlossaryDocument glossaryDoc = new GlossaryDocument();
        doc.setGlossaryDocument(glossaryDoc);
    }
}
```

*เหตุผลที่สำคัญ:* แพทเทิร์นนี้เป็นพื้นฐานสำหรับ **การรวมส่วนของเอกสาร** ในภายหลัง, เพราะแต่ละส่วนสามารถรักษาสตไลล์ของตนเองได้แม้อยู่ในไฟล์เดียวกัน

### ฟีเจอร์ 2: ตั้งค่าสีพื้นหลังของหน้า

#### ภาพรวม
คุณสามารถใช้ `Document.setPageColor` เพื่อใส่สีโทนเดียวให้ทุกหน้า ซึ่งตรงกับคีย์เวิร์ดหลัก **set page background color**

```java
import com.aspose.words.Document;
import java.awt.Color;

public class SetPageBackgroundColor {
    public void setPageColor() throws Exception {
        // Create a new document and add text to it (omitted for brevity)
        Document doc = new Document();

        // Set the background color of all pages to light gray
        doc.setPageColor(Color.lightGray);

        // Save the document with a specified path
        String outputPath = "YOUR_OUTPUT_DIRECTORY/DocumentBase.SetPageColor.docx";
        doc.save(outputPath);
    }
}
```

**เคล็ดลับ:** หากต้องการ **เปลี่ยนสีหน้าในเอกสาร Word** อย่างรวดเร็ว เพียงเปลี่ยน `Color.lightGray` เป็นค่าคงที่ของ `java.awt.Color` ใดก็ได้ หรือค่า RGB ที่กำหนดเอง

### ฟีเจอร์ 3: นำเข้าส่วนจากเอกสาร (และการรวมส่วนของเอกสาร)

#### ภาพรวม
เมื่อคุณต้องการรวมเนื้อหาจากหลายแหล่ง คุณสามารถนำเข้าทั้งส่วน (หรือโหนดใด ๆ) จากเอกสารหนึ่งไปยังอีกเอกสารหนึ่ง นี่คือหัวใจของ **merge document sections** และ **import section from document**

```java
import com.aspose.words.Document;
import com.aspose.words.Section;

public class ImportNode {
    public void importNode() throws Exception {
        // Create source and destination documents
        Document srcDoc = new Document();
        Document dstDoc = new Document();

        // Add text to paragraphs in both documents
        srcDoc.getFirstSection().getBody()
            .getFirstParagraph()
            .appendChild(new com.aspose.words.Run(srcDoc, "Source document first paragraph text."));
        dstDoc.getFirstSection().getBody()
            .getFirstParagraph()
            .appendChild(new com.aspose.words.Run(dstDoc, "Destination document first paragraph text."));

        // Import section from source to destination document
        Section importedSection = (Section) dstDoc.importNode(srcDoc.getFirstSection(), true);
        
        // Append the imported section to the destination document
        dstDoc.appendChild(importedSection);
    }
}
```

**Pro tip:** หลังจากนำเข้าแล้ว ให้เรียก `dstDoc.updatePageLayout()` เพื่อให้การจัดหน้าและหัวกระดาษ/ท้ายกระดาษถูกคำนวณใหม่อย่างถูกต้อง

### ฟีเจอร์ 4: นำเข้าโหนดพร้อมโหมดฟอร์แมตแบบกำหนดเอง

#### ภาพรวม
บางครั้งแหล่งที่มและปลายทางใช้สไตล์ที่แตกต่างกัน `ImportFormatMode` ช่วยให้คุณเลือกว่าจะรักษาสตไลล์ของแหล่งที่มาหรือบังคับให้ใช้สไตล์ของปลายทาง

```java
import com.aspose.words.Document;
import com.aspose.words.Style;
import com.aspose.words.StyleType;
import com.aspose.words.ImportFormatMode;

public class ImportNodeCustom {
    public void importNodeCustom() throws Exception {
        // Create source and destination documents with different style configurations
        Document srcDoc = new Document();
        Style srcStyle = srcDoc.getStyles().add(StyleType.CHARACTER, "My style");
        srcStyle.getFont().setName("Courier New");

        Document dstDoc = new Document();
        Style dstStyle = dstDoc.getStyles().add(StyleType.CHARACTER, "My style");
        dstStyle.getFont().setName("Calibri");

        // Use importNode with specific format mode
        Section importedSection = (Section) dstDoc.importNode(srcDoc.getFirstSection(), true, ImportFormatMode.USE_DESTINATION_STYLES);
    }
}
```

**เมื่อใดควรใช้:** เลือก `USE_DESTINATION_STYLES` หากต้องการลุคที่สอดคล้องกันทั่วทั้งเอกสารที่ **merged document sections** จากหลายแบรนด์

### ฟีเจอร์ 5: สร้างภาพพื้นหลังของเอกสาร (ตั้งค่า Shape พื้นหลัง)

#### ภาพรวม
นอกเหนือจากสีทึบ คุณสามารถฝัง Shape หรือภาพเป็นพื้นหลังของหน้า ตัวอย่างนี้เพิ่ม Shape รูปดาวสีแดง, แต่คุณสามารถเปลี่ยนเป็นรูปภาพใดก็ได้เพื่อ **create document background image**

```java
import com.aspose.words.Document;
import com.aspose.words.Shape;

public class SetBackgroundShape {
    public void setBackgroundShape() throws Exception {
        // Create a new document
        Document doc = new Document();

        // Add a shape to the background of each page
        Shape shape = new Shape(doc, com.aspose.words.ShapeType.STAR);
        shape.setWidth(200);
        shape.setHeight(100);
        shape.getFill().setColor(Color.RED);
        
        // Set the shape as the background for all pages (code omitted for brevity)

        doc.save("YOUR_OUTPUT_DIRECTORY/DocumentWithBackgroundShape.docx");
    }
}
```

**วิธีใช้ภาพ:** แทนที่การสร้าง `Shape` ด้วย `ShapeType.IMAGE` แล้วโหลดสตรีมของภาพ การทำเช่นนี้จะเปลี่ยน Shape ให้กลายเป็น **document background image** ที่ทำซ้ำบนทุกหน้า

## ปัญหาทั่วไปและวิธีแก้

| ปัญหา | วิธีแก้ |
|-------|----------|
| **สีพื้นหลังไม่แสดง** | ตรวจสอบให้แน่ใจว่าเรียก `doc.setPageColor(...)` **ก่อน** บันทึกเอกสาร |
| **ส่วนที่นำเข้าสูญเสียรูปแบบ** | ใช้ `ImportFormatMode.USE_DESTINATION_STYLES` เพื่อบังคับใช้สไตล์ปลายทาง |
| **Shape ไม่แสดงบนทุกหน้า** | แทรก Shape ลงใน **header/footer** ของแต่ละ Section, หรือทำการคัดลอกสำหรับทุก Section |
| **เกิดข้อยกเว้นลิขสิทธิ์** | ตรวจสอบว่าเรียก `License.setLicense("Aspose.Words.Java.lic")` ตั้งแต่ต้นแอป |
| **ค่าสีแสดงผลต่างกัน** | `java.awt.Color` ใช้ sRGB; ตรวจสอบค่า RGB ที่ต้องการอีกครั้ง |

## คำถามที่พบบ่อย

**ถาม: ฉันสามารถตั้งค่าสีพื้นหลังที่แตกต่างกันสำหรับแต่ละ Section ได้หรือไม่?**  
ตอบ: ได้ หลังจากสร้าง `Section` ใหม่ ให้เรียก `section.getPageSetup().setPageColor(Color)` สำหรับ Section นั้น

**ถาม: สามารถใช้ Gradient แทนสีทึบได้หรือไม่?**  
ตอบ: Aspose.Words ไม่รองรับการเติมแบบ Gradient โดยตรง, แต่คุณสามารถแทรกรูปภาพเต็มหน้าแบบ Gradient แล้วตั้งเป็น Shape พื้นหลังได้

**ถาม: จะรวมเอกสารขนาดใหญ่โดยไม่ให้หน่วยความจำเต็มได้อย่างไร?**  
ตอบ: ใช้ `Document.appendDocument(otherDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING)` ในโหมดสตรีมมิ่ง และเรียก `doc.updatePageLayout()` หลังการรวมแต่ละครั้ง

**ถาม: API ทำงานกับไฟล์ .docx ที่สร้างโดย Microsoft Word 2019 หรือไม่?**  
ตอบ: แน่นอน Aspose.Words รองรับมาตรฐาน OOXML ของ Word เวอร์ชันใหม่ทั้งหมด

**ถาม: วิธีที่ดีที่สุดในการเปลี่ยนพื้นหลังของไฟล์ .doc ที่มีอยู่โดยโปรแกรมคืออะไร?**  
ตอบ: โหลดเอกสารด้วย `new Document("file.doc")`, เรียก `setPageColor`, แล้วบันทึกกลับเป็น `.doc` หรือ `.docx`

---

**อัปเดตล่าสุด:** 2025-11-26  
**ทดสอบกับ:** Aspose.Words for Java 25.3  
**ผู้เขียน:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}