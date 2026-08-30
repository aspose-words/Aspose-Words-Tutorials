---
category: general
date: 2026-06-24
description: วิธีจัดการคำเตือนเมื่อประมวลผลไฟล์ Word ด้วย Java เรียนรู้วิธีดักจับฟอนต์
  พิมพ์ข้อความฟอนต์ และจัดการฟอนต์ที่หายไปอย่างราบรื่น
draft: false
keywords:
- how to handle warnings
- how to capture fonts
- print font messages
- handle missing fonts
language: th
og_description: วิธีจัดการคำเตือนใน Aspose.Words for Java. คู่มือนี้แสดงวิธีดักจับฟอนต์
  พิมพ์ข้อความฟอนต์ และจัดการฟอนต์ที่หายไปอย่างมีประสิทธิภาพ.
og_title: วิธีจัดการคำเตือนใน Aspose.Words – บทเรียน Java ฉบับสมบูรณ์
schemas:
- author: Aspose
  dateModified: '2026-06-24'
  description: how to handle warnings when processing Word files in Java. Learn how
    to capture fonts, print font messages, and handle missing fonts smoothly.
  headline: how to handle warnings in Aspose.Words for Java – Full Guide
  type: TechArticle
- description: how to handle warnings when processing Word files in Java. Learn how
    to capture fonts, print font messages, and handle missing fonts smoothly.
  name: how to handle warnings in Aspose.Words for Java – Full Guide
  steps:
  - name: The document actually references a missing font.
    text: The document actually references a missing font.
  - name: The path to `input.docx` is correct.
    text: The path to `input.docx` is correct.
  - name: You’re using a recent version of Aspose.Words (older builds sometimes suppress
      certain warnings).
    text: You’re using a recent version of Aspose.Words (older builds sometimes suppress
      certain warnings).
  type: HowTo
tags:
- Aspose.Words
- Java
- Font Substitution
title: วิธีจัดการคำเตือนใน Aspose.Words for Java – คู่มือเต็ม
url: /th/java/document-rendering/how-to-handle-warnings-in-aspose-words-for-java-full-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# วิธีจัดการคำเตือนใน Aspose.Words for Java – คู่มือเต็ม

เคยสงสัย **วิธีจัดการคำเตือน** ที่ปรากฏขึ้นเมื่อคุณโหลดเอกสาร Word ด้วย Aspose.Words หรือไม่? บางครั้งคุณอาจเจอข้อความลึกลับเกี่ยวกับฟอนต์ที่หายไปและคิดว่า “เยี่ยม, PDF ของฉันดูเอียง—แล้วทำอย่างไรต่อ?” คุณไม่ได้อยู่คนเดียว ในหลายโครงการจริง คำเตือนการแทนที่ฟอนต์เป็นผู้กระทำลับที่ทำลายความแม่นยำของการจัดหน้า

ในบทแนะนำนี้ เราจะพาไปผ่านวิธีแก้ปัญหาที่ใช้งานได้จริง: การลงทะเบียน callback สำหรับคำเตือน, การตรวจจับการแจ้งเตือนที่เกี่ยวกับฟอนต์, และ **การพิมพ์ข้อความฟอนต์** เพื่อให้คุณตัดสินใจว่าจะฝังฟอนต์สำรองหรือจัดส่งไฟล์ฟอนต์แบบกำหนดเอง สิ้นสุดบทคุณจะรู้ **วิธีดึงฟอนต์**, การ **จัดการฟอนต์ที่หายไป** อย่างราบรื่น, และทำให้ pipeline การแปลงเอกสารของคุณมั่นคง

## สิ่งที่คุณจะได้เรียนรู้

- จุดประสงค์ของ callback คำเตือนใน Aspose.Words
- วิธีตรวจจับและกรองคำเตือน *การแทนที่ฟอนต์*
- วิธีการบันทึกหรือแสดง **ข้อความฟอนต์ที่พิมพ์** สำหรับการดีบัก
- กลยุทธ์สำหรับ **การจัดการฟอนต์ที่หายไป** ในสภาพแวดล้อมการผลิต
- ตัวอย่าง Java ที่สมบูรณ์พร้อมใช้งานที่คุณสามารถนำไปใส่ในโครงการ Maven หรือ Gradle ใดก็ได้

### ข้อกำหนดเบื้องต้น

- Java 8 หรือใหม่กว่า (โค้ดทำงานกับ JDK 11 ด้วย)
- ไลบรารี Aspose.Words for Java (ดาวน์โหลดจากเว็บไซต์ Aspose หรือเพิ่ม dependency ของ Maven/Gradle)
- ตัวอย่างไฟล์ `input.docx` ที่อ้างอิงฟอนต์ที่คุณไม่ได้ติดตั้งในเครื่อง (เหมาะสำหรับทดสอบ callback)

---

## ขั้นตอนที่ 1: ตั้งค่าโครงการของคุณและนำเข้า Aspose.Words

ก่อนที่คุณจะ **จัดการคำเตือน**, คุณต้องมีโครงการ Java ที่รู้จัก Aspose.Words หากคุณใช้ Maven ให้เพิ่มโค้ดส่วนนั้นลงในไฟล์ `pom.xml` ของคุณ:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.10</version> <!-- Use the latest stable version -->
</dependency>
```

สำหรับ Gradle, เวอร์ชันที่เทียบเท่าคือ:

```gradle
implementation 'com.aspose:aspose-words:23.10'
```

เมื่อ dependency ถูกแก้ไขแล้ว ให้นำเข้าคลาสที่จำเป็นในไฟล์ซอร์ส Java ของคุณ:

```java
import com.aspose.words.*;
```

> **เคล็ดลับ:** คอยอัปเดตไลบรารี Aspose ของคุณให้เป็นเวอร์ชันล่าสุด รุ่นใหม่มักปรับปรุงการจัดการคำเตือนและเพิ่มรายละเอียดของ `WarningInfo` ที่สมบูรณ์ยิ่งขึ้น

---

## ขั้นตอนที่ 2: โหลดเอกสาร Word และลงทะเบียน Warning Callback

ตอนนี้ไลบรารีอยู่ใน classpath แล้ว เราสามารถ **ดึงฟอนต์** ที่เอนจินสลับออกได้ คีย์คือ `Document.setWarningCallback` ซึ่งรับการทำงานใด ๆ ของ `IWarningCallback` ด้านล่างเป็นตัวอย่างสั้นแต่ครบถ้วนที่พิมพ์คำเตือนการแทนที่ฟอนต์ทุกรายการไปยังคอนโซล

```java
public class FontWarningDemo {

    public static void main(String[] args) throws Exception {
        // 1️⃣ Load the Word document (replace with your actual path)
        Document document = new Document("YOUR_DIRECTORY/input.docx");

        // 2️⃣ Register the warning callback – this is where we **handle warnings**
        document.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo warningInfo) {
                // Filter only font‑substitution warnings
                if (warningInfo.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                    // 3️⃣ **Print font messages** – you could also log to a file or monitoring system
                    System.out.println("Font substitution detected: " + warningInfo.getDescription());
                }
                // Optional: handle other warning types here
            }
        });

        // Trigger the warning processing by saving or converting the document
        // For demonstration, we’ll just save to PDF (you could save to any format)
        document.save("output.pdf");
    }
}
```

### ทำไมวิธีนี้ถึงได้ผล

- **`Document.setWarningCallback`** บอก Aspose.Words ให้เรียกโค้ดของคุณทุกครั้งที่พบสถานการณ์ที่ต้องการคำเตือน
- **`WarningInfo.getWarningType()`** ช่วยให้เราตรวจแยกประเภทต่าง ๆ (เช่น `FONT_SUBSTITUTION`, `DEPRECATED_FEATURE`) โดยโฟกัสที่ `FONT_SUBSTITUTION` เรา **จัดการฟอนต์ที่หายไป** โดยไม่ทำให้บันทึกรก
- บรรทัด `System.out.println` **พิมพ์ข้อความฟอนต์** แบบเรียลไทม์ ซึ่งมีคุณค่าสำหรับการพัฒนาหรือแก้ปัญหา pipeline การผลิต

---

## ขั้นตอนที่ 3: ทดสอบ Callback ด้วยฟอนต์ที่หายไป

เพื่อยืนยันว่า callback ของเราจริง ๆ **ดึงฟอนต์** ได้ ให้สร้างไฟล์ Word ที่ใช้ฟอนต์ที่ไม่ได้ติดตั้งบนเครื่องของคุณ—เช่น “Comic Sans MS” บนเซิร์ฟเวอร์ Linux ที่มีเพียง “DejaVu Sans” เมื่อคุณรันตัวอย่าง คุณควรเห็นผลลัพธ์คล้ายกับ:

```
Font substitution detected: Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
```

หากคุณไม่เห็นข้อความใด ๆ ให้ตรวจสอบสองครั้ง:

1. เอกสารจริง ๆ อ้างอิงฟอนต์ที่หายไป
2. เส้นทางไปยัง `input.docx` ถูกต้อง
3. คุณใช้เวอร์ชันล่าสุดของ Aspose.Words (บางรุ่นเก่าอาจซ่อนคำเตือนบางอย่าง)

---

## ขั้นตอนที่ 4: การจัดการขั้นสูง – ฝังฟอนต์สำรอง

การพิมพ์คำเตือนเป็นเรื่องดี แต่ในระบบการผลิตคุณอาจต้องการ **จัดการฟอนต์ที่หายไป** โดยอัตโนมัติ วิธีที่พบบ่อยคือการฝังฟอนต์สำรอง (เช่น “Liberation Sans”) ก่อนบันทึก ต่อไปนี้คือวิธีขยาย callback เพื่อแทนที่ฟอนต์ที่หายไปโดยโปรแกรม:

```java
document.setWarningCallback(new IWarningCallback() {
    @Override
    public void warning(WarningInfo warningInfo) {
        if (warningInfo.getWarningType() == WarningType.FONT_SUBSTITUTION) {
            String missingFont = warningInfo.getDescription()
                .replaceAll(".*'([^']+)'.*", "$1"); // extract the font name
            System.out.println("Missing font: " + missingFont);

            // Load a fallback font from resources or a known location
            FontSettings fontSettings = document.getFontSettings();
            fontSettings.setSubstitutionSettings(new FontSubstitutionSettings() {{
                getTableSubstitution().addSubstitutes(missingFont, new String[]{"Liberation Sans"});
            }});
        }
    }
});
```

**เกิดอะไรขึ้น?**

- เราแยกคำอธิบายคำเตือนเพื่อดึงชื่อฟอนต์ที่หายไป
- ด้วย `FontSettings` เราบอก Aspose.Words ให้แทนที่ *ทุก* การใช้ฟอนต์นั้นด้วย “Liberation Sans”
- ครั้งต่อไปที่เอกสารถูกเรนเดอร์หรือบันทึก ฟอนต์สำรองจะถูกนำไปใช้โดยเงียบ ๆ

> **คำเตือน:** การใช้การแทนที่อัตโนมัติมากเกินไปอาจปิดบังปัญหาการออกแบบที่แท้จริง ควรบันทึกการแทนที่ (เช่นที่เรา **พิมพ์ข้อความฟอนต์** แล้ว) และตรวจสอบผลลัพธ์ด้วยตนเองในขั้นตอน QA

---

## ขั้นตอนที่ 5: บันทึกแทนการพิมพ์ – ทำให้พร้อมใช้งานในการผลิต

ใน pipeline CI/CD คุณอาจไม่ต้องการแสดงผลบนคอนโซล ให้เปลี่ยน `System.out.println` เป็น logger ที่เหมาะสม (เช่น SLF4J) นี่คือตัวอย่างการปรับอย่างรวดเร็ว:

```java
import org.slf4j.Logger;
import org.slf4j.LoggerFactory;

// ...

private static final Logger logger = LoggerFactory.getLogger(FontWarningDemo.class);

// Inside the callback:
logger.warn("Font substitution: {}", warningInfo.getDescription());
```

ตอนนี้คำเตือนของคุณจะรวมกับเครื่องมือรวมบันทึกที่มีอยู่ (ELK, Splunk ฯลฯ) ทำให้ง่ายขึ้นในการ **จัดการฟอนต์ที่หายไป** ในหลายงาน

---

## ขั้นตอนที่ 6: ข้อผิดพลาดทั่วไป & วิธีหลีกเลี่ยง

| ข้อผิดพลาด | สาเหตุ | วิธีแก้ |
|------------|--------|--------|
| ไม่มีคำเตือนปรากฏ | ฟอนต์มีอยู่ในระบบ หรือเอกสารใช้ฟอนต์ฝังอยู่ | ตรวจสอบว่าเอกสารทดสอบอ้างอิงฟอนต์ที่ไม่มีจริงหรือไม่ |
| Callback ไม่ทำงาน | `setWarningCallback` ถูกเรียก **หลังจาก** โหลดเอกสารแล้ว | ลงทะเบียน callback **ก่อน** การดำเนินการใด ๆ ที่อาจทำให้เกิดคำเตือน (เช่น ก่อน `Document.save`) |
| คำเตือนหลายรายการทำให้บันทึกแออัด | เอกสารขนาดใหญ่ทำให้เกิดการแทนที่หลายครั้ง | เพิ่มกลไกจำกัดความถี่หรือรวมข้อความก่อนบันทึก |
| การแทนที่ไม่ทำงาน | `FontSettings` ไม่ได้เชื่อมกับอินสแตนซ์ของเอกสาร | ตรวจสอบว่าคุณตั้งค่า `FontSettings` บน `Document` ตัวเดียวกับที่บันทึก |

---

## ขั้นตอนที่ 7: ตัวอย่างเต็มพร้อมรัน

ด้านล่างเป็นโปรแกรมเต็มรูปแบบพร้อมคัดลอกและวาง รวมการนำเข้า, callback, การบันทึก, และกลยุทธ์ฟอนต์สำรอง

```java
import com.aspose.words.*;
import org.slf4j.Logger;
import org.slf4j.LoggerFactory;

public class FontWarningDemo {

    private static final Logger logger = LoggerFactory.getLogger(FontWarningDemo.class);

    public static void main(String[] args) throws Exception {
        // Load the document – adjust the path as needed
        Document document = new Document("YOUR_DIRECTORY/input.docx");

        // Register warning callback to capture and log font substitution warnings
        document.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo warningInfo) {
                if (warningInfo.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                    // Extract missing font name (optional, for advanced handling)
                    String missingFont = warningInfo.getDescription()
                        .replaceAll(".*'([^']+)'.*", "$1");

                    // Log the warning – this **prints font messages** in your log files
                    logger.warn("Font substitution detected: {}", warningInfo.getDescription());

                    // OPTIONAL: automatically substitute with a known fallback
                    FontSettings fontSettings = document.getFontSettings();
                    fontSettings.setSubstitutionSettings(new FontSubstitutionSettings() {{
                        getTableSubstitution().addSubstitutes(missingFont, new String[]{"Liberation Sans"});
                    }});
                }
            }
        });

        // Save to PDF (or any other format). This triggers the warning processing.
        document.save("output.pdf");
        logger.info("Document conversion completed. Check logs for any font substitution warnings.");
    }
}
```

**ผลลัพธ์ที่คาดว่าจะเห็นในคอนโซล/บันทึก** (สมมติว่า “Comic Sans MS” หายไป):

```
WARN  FontWarningDemo - Font substitution detected: Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
INFO  FontWarningDemo - Document conversion completed. Check logs for any font substitution warnings.
```

ไฟล์ `output.pdf` ที่ได้จะใช้ “Liberation Sans” ทุกที่ที่มีการอ้างอิง “Comic Sans MS” ด้วยการแทนที่อัตโนมัติที่เราเพิ่ม

---

## สรุป

เราได้อธิบาย **วิธีจัดการคำเตือน** ใน Aspose.Words for Java ตั้งแต่ต้นจนจบ โดยการลงทะเบียน warning callback, กรองการแจ้งเตือน **การแทนที่ฟอนต์**, และ **พิมพ์ข้อความฟอนต์**, คุณจะได้มองเห็นสถานการณ์ฟอนต์ที่หายไปอย่างครบถ้วน การเพิ่มฟอนต์สำรองผ่าน `FontSettings` ทำให้คุณ **จัดการฟอนต์ที่หายไป** โดยไม่ต้องทำด้วยตนเอง ในขณะที่กรอบบันทึกที่เหมาะสมทำให้โซลูชันพร้อมใช้งานในการผลิต

ขั้นตอนต่อไป? ลองผสานวิธีนี้กับ Aspose.PDF เพื่อตรวจสอบว่าฟอนต์ที่ฝังอยู่ยังคงอยู่หลังการแปลง หรือสำรวจประเภทคำเตือนอื่น ๆ (เช่น `DEPRECATED_FEATURE`) เพื่อทำให้โค้ดของคุณพร้อมสำหรับอนาคต และหากคุณสนใจ **วิธีดึงฟอนต์** จาก bucket ที่เก็บข้อมูลระยะไกล

## สิ่งที่คุณควรเรียนต่อไป?

บทแนะนำต่อไปนี้ครอบคลุมหัวข้อที่เกี่ยวข้องอย่างใกล้ชิดและต่อยอดจากเทคนิคในคู่มือนี้ แต่ละแหล่งข้อมูลมีตัวอย่างโค้ดทำงานเต็มรูปแบบพร้อมคำอธิบายทีละขั้นตอน เพื่อช่วยคุณเชี่ยวชาญฟีเจอร์ API เพิ่มเติมและสำรวจแนวทางการทำงานทางเลือกในโครงการของคุณ

- [ดักจับคำเตือนการแทนที่ฟอนต์ใน Java ด้วย Aspose.Words – คู่มือเต็ม](/words/english/java/document-loading-and-saving/capture-font-substitution-warnings-in-java-with-aspose-words/)
- [วิธีตรวจจับฟอนต์ใน Aspose.Words – จัดการคำเตือนและการตั้งค่า](/words/english/net/working-with-fonts/how-to-detect-fonts-in-aspose-words-handle-warnings-settings/)
- [วิธีดึงฟอนต์ใน Aspose.Words – คู่มือเต็ม](/words/english/net/working-with-fonts/how-to-capture-fonts-in-aspose-words-complete-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}