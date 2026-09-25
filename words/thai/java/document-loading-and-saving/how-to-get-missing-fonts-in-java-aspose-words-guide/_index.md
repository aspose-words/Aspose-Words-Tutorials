---
category: general
date: 2026-02-15
description: เรียนรู้วิธีดึงฟอนต์ที่หายไปเมื่อโหลดเอกสาร Word ใน Java ด้วย Aspose.Words
  รวมถึงการจัดการคอลแบ็กคำเตือนและการแทนที่ฟอนต์.
draft: false
keywords:
- how to get missing fonts
- Aspose.Words missing font
- font substitution warning
- Java LoadOptions warning callback
- document processing Java
language: th
og_description: วิธีรับฟอนต์ที่หายไปใน Java ด้วย Aspose.Words. ค้นพบการเรียกคืนคำเตือน,
  การจัดการการแทนที่ฟอนต์, และแนวทางปฏิบัติที่ดีที่สุดสำหรับการประมวลผลเอกสาร.
og_title: วิธีรับแบบอักษรที่หายไปใน Java – คู่มือ Aspose.Words
tags:
- Aspose.Words
- Java
- Font Management
title: วิธีรับฟอนต์ที่หายไปใน Java – คู่มือ Aspose.Words
url: /th/java/document-loading-and-saving/how-to-get-missing-fonts-in-java-aspose-words-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# วิธีการดึงฟอนต์ที่หายไปใน Java – คู่มือ Aspose.Words

เคยเปิดไฟล์ Word ใน Java แล้วเห็นการแทนที่ฟอนต์ที่แปลกประหลาดและสงสัย **วิธีการดึงฟอนต์ที่หายไป**หรือไม่? คุณไม่ใช่คนแรกที่เจอความประหลาดใจนี้ ในแอปพลิเคชันระดับองค์กรหลายแห่ง คำเตือนฟอนต์ที่หายไปอาจทำลายความแม่นยำของการแสดงผลในรายงาน สัญญา หรือสื่อการตลาด

ข่าวดีคืออะไร? Aspose.Words ให้วิธีที่สะอาดในการดักจับคำเตือนเหล่านั้นผ่าน callback เพื่อให้คุณสามารถบันทึก, แทนที่, หรือแม้กระทั่งแจ้งเตือนผู้ใช้ก่อนที่เอกสารจะถูกเรนเดอร์ ในบทแนะนำนี้เราจะเดินผ่านตัวอย่างที่สมบูรณ์และสามารถรันได้ซึ่งแสดง **วิธีการดึงฟอนต์ที่หายไป**, อธิบายว่าทำไม callback ถึงสำคัญ, และครอบคลุมเทคนิคกรณีขอบที่คุณอาจต้องใช้ในโครงการจริง

> **Pro tip:** หากคุณกำลังใช้ Aspose.Words 22.12 หรือใหม่กว่า API ที่แสดงด้านล่างทำงานได้ทันทีโดยไม่ต้องกำหนดค่าเพิ่มเติม

![Diagram illustrating how to get missing fonts using Aspose.Words warning callback](how-to-get-missing-fonts-diagram.png "แผนภาพวิธีการดึงฟอนต์ที่หายไป")

## สิ่งที่บทแนะนำนี้ครอบคลุม

- ตั้งค่า **Java LoadOptions warning callback** เพื่อดักจับคำเตือนการแทนที่ฟอนต์  
- กรองคำเตือนเพื่อให้คุณเห็นเฉพาะที่เกี่ยวกับฟอนต์ที่หายไป  
- พิมพ์รายงานที่ชัดเจนและอ่านง่ายว่าฟอนต์ใดถูกแทนที่และแทนด้วยอะไร  
- เคล็ดลับการจัดการเอกสารขนาดใหญ่, ปรับระดับคำเตือน, และผสานโซลูชันเข้ากับ pipeline การประมวลผลที่ใหญ่ขึ้น  

โดยเมื่อจบคู่มือนี้คุณจะสามารถตอบคำถาม “**วิธีการดึงฟอนต์ที่หายไป**?” ด้วยโค้ดสแนปที่พร้อมรันและความเข้าใจเชิงกลไกที่มั่นคง

### ข้อกำหนดเบื้องต้น

- ติดตั้ง Java 8 หรือใหม่กว่า  
- ไลบรารี Aspose.Words for Java (ดาวน์โหลดจากเว็บไซต์อย่างเป็นทางการหรือเพิ่มผ่าน Maven/Gradle)  
- ไฟล์ Word ที่อ้างอิงฟอนต์ที่ไม่ได้ติดตั้งบนเครื่องของคุณ (เช่น `MissingFont.docx`)  

หากคุณขาดสิ่งใดสิ่งหนึ่งเหล่านี้ ให้ดาวน์โหลดไลบรารีทันที—การเพิ่มลงใน Maven ง่ายเพียง:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version> <!-- replace with the latest version -->
</dependency>
```

---

## ขั้นตอนที่ 1: เตรียมคอลเลกชันสำหรับคำเตือนการแทนที่ฟอนต์

ก่อนโหลดเอกสารเราต้องมีที่เก็บคำเตือนใด ๆ ที่ Aspose.Words ส่งออก `ArrayList<WarningInfo>` ทำงานได้ดีเพราะรักษาลำดับและให้เราสามารถวนลูปต่อไปได้

```java
import com.aspose.words.*;
import java.util.ArrayList;
import java.util.List;

// Step 1: Create a list that will hold warning information.
List<WarningInfo> fontWarnings = new ArrayList<>();
```

*ทำไมเรื่องนี้ถึงสำคัญ:* Callback คำเตือนอาจถูกเรียกหลายสิบครั้งสำหรับไฟล์เดียว—คิดถึงแต่ละ glyph ที่หายไป, ปัญหารูปภาพที่ฝัง, ฯลฯ การเก็บรวบรวมไว้ก่อนทำให้ขั้นตอนการโหลดเร็วและการประมวลผลถูกเลื่อนไปยังลูปที่ควบคุมได้

---

## ขั้นตอนที่ 2: กำหนดค่า LoadOptions ด้วย Warning Callback

Aspose.Words ให้คุณต่อ `IWarningCallback` เข้าไป ภายใน callback เราจะเพิ่ม `WarningInfo` ทุกตัวลงในรายการจากขั้นตอนที่ 1

```java
// Step 2: Set up LoadOptions with a custom warning callback.
LoadOptions loadOptions = new LoadOptions();
loadOptions.setWarningCallback(new IWarningCallback() {
    @Override
    public void warning(WarningInfo info) {
        // Capture every warning; we'll filter later.
        fontWarnings.add(info);
    }
});
```

*คำอธิบาย:* วิธี `warning` ถูกเรียก **แบบซิงโครนัส** ระหว่างการโหลดเอกสาร โดยการผลัก `WarningInfo` เข้าไปใน `fontWarnings` เราจะหลีกเลี่ยง I/O หนัก ๆ (เช่นการบันทึกลงไฟล์) ที่อาจทำให้การโหลดช้า รูปแบบ “เก็บ‑แล้ว‑ประมวลผล” นี้เป็นวิธีที่แนะนำสำหรับการจัดการคำเตือนจำนวนมาก

---

## ขั้นตอนที่ 3: โหลดเอกสารโดยใช้ตัวเลือกที่กำหนดค่าไว้

ตอนนี้เราจริง ๆ แล้วอ่านไฟล์ Word หากเอกสารมีฟอนต์ที่ไม่ได้ติดตั้ง Aspose.Words จะทำการแทนที่โดยอัตโนมัติและเรียก callback คำเตือนที่เราติดตั้งไว้

```java
// Step 3: Load the document with the warning‑aware LoadOptions.
String filePath = "YOUR_DIRECTORY/MissingFont.docx"; // adjust to your environment
Document doc = new Document(filePath, loadOptions);
```

*อะไรเกิดขึ้นเบื้องหลัง?* Aspose.Words วิเคราะห์ตารางฟอนต์ของไฟล์, เปรียบเทียบกับฟอนต์ที่มีบน OS, และสำหรับแต่ละรายการที่หายไปจะสร้าง `WarningInfo` ที่มี `WarningSource.FontSubstitution` แหล่งนี้คือคีย์ที่เราจะใช้แยกคำเตือนฟอนต์ที่หายไป

---

## ขั้นตอนที่ 4: กรองและแสดงเฉพาะคำเตือนการแทนที่ฟอนต์

หลังจากโหลด `fontWarnings` อาจมีข้อความผสม (เช่นฟีเจอร์ที่เลิกใช้, ปัญหารูปภาพ) เราแค่สนใจฟอนต์ที่หายไป ดังนั้นเราจะวนลูปรายการและพิมพ์รายงานสั้น ๆ

```java
// Step 4: Output any font‑substitution warnings that were captured.
for (WarningInfo warning : fontWarnings) {
    if (warning.getSource() == WarningSource.FontSubstitution) {
        System.out.println("Substituted '" + warning.getDescription() + "' with '" +
                           warning.getAdditionalInfo() + "'");
    }
}
```

**ตัวอย่างผลลัพธ์**

```
Substituted 'Comic Sans MS' with 'Arial'
Substituted 'Times New Roman PS' with 'Times New Roman'
```

*ทำไมสิ่งนี้จึงมีประโยชน์:* ฟิลด์ `description` บอกว่าฟอนต์ใดที่เอกสารต้องการ, ส่วน `additionalInfo` บอกว่า Aspose.Words ใช้อะไรแทนที่ ด้วยข้อมูลนี้คุณสามารถ:

- แจ้งผู้ใช้ให้ติดตั้งฟอนต์ที่หายไป  
- ฝังฟอนต์ทดแทนลงในเอกสารโดยโปรแกรม (`doc.getFontInfos().add(...)`)  
- บันทึกเหตุการณ์เพื่อการตรวจสอบตามข้อกำหนด

---

## การจัดการกรณีขอบและความแปรผันทั่วไป

### 1. การยับยั้งคำเตือนที่ไม่เกี่ยวกับฟอนต์

หากคุณต้องการข้อความเฉพาะฟอนต์เท่านั้น สามารถทำให้ callback แคบลงได้:

```java
loadOptions.setWarningCallback(info -> {
    if (info.getSource() == WarningSource.FontSubstitution) {
        fontWarnings.add(info);
    }
});
```

วิธีนี้ช่วยลดการใช้หน่วยความจำเมื่อประมวลผลชุดข้อมูลขนาดใหญ่

### 2. การปรับระดับความรุนแรงของคำเตือน

Aspose.Words แบ่งคำเตือนตาม `WarningType` สำหรับฟอนต์ที่หายไปคุณมักจะเห็น `WarningType.FontSubstitution` หากต้องการถือเป็นข้อผิดพลาด (เช่นยกเลิกการโหลด) ให้โยน exception ภายใน callback:

```java
loadOptions.setWarningCallback(info -> {
    if (info.getSource() == WarningSource.FontSubstitution) {
        throw new RuntimeException("Missing font detected: " + info.getDescription());
    }
});
```

### 3. ทำงานกับ Stream แทนไฟล์

บางครั้งเอกสารมาจากฐานข้อมูลหรือ HTTP request วิธีเดียวกันทำงานกับ `InputStream` ได้:

```java
InputStream docStream = new ByteArrayInputStream(bytesFromDb);
Document doc = new Document(docStream, loadOptions);
```

จำไว้ว่าให้ปิด stream หลังโหลดเสร็จ

### 4. ใช้โฟลเดอร์ฟอนต์กำหนดเอง

หากคุณมีคอลเลกชันฟอนต์ของบริษัทเก็บไว้บนไดรฟ์แชร์ ให้ชี้ Aspose.Words ไปยังโฟลเดอร์นั้น:

```java
loadOptions.setFontSettings(new FontSettings());
loadOptions.getFontSettings().setFontsFolder("C:/CorporateFonts", true);
```

ตอนนี้ไลบรารีจะมองหาในโฟลเดอร์นั้น *ก่อน* จะย้อนกลับไปใช้ฟอนต์ของระบบ ลดจำนวนคำเตือนฟอนต์ที่หายไปอย่างมาก

---

## ตัวอย่างทำงานเต็มรูปแบบ

รวมทุกอย่างเข้าด้วยกัน นี่คือคลาสที่สามารถวางลงในโปรเจค Java ใดก็ได้:

```java
import com.aspose.words.*;
import java.util.ArrayList;
import java.util.List;

public class MissingFontDetector {

    public static void main(String[] args) {
        // 1️⃣ Prepare a collection for warnings.
        List<WarningInfo> fontWarnings = new ArrayList<>();

        // 2️⃣ Create LoadOptions with a warning callback.
        LoadOptions loadOptions = new LoadOptions();
        loadOptions.setWarningCallback(info -> fontWarnings.add(info));

        // (Optional) Point to a custom font folder.
        // FontSettings fontSettings = new FontSettings();
        // fontSettings.setFontsFolder("C:/CorporateFonts", true);
        // loadOptions.setFontSettings(fontSettings);

        // 3️⃣ Load the document.
        String docPath = "YOUR_DIRECTORY/MissingFont.docx";
        Document doc;
        try {
            doc = new Document(docPath, loadOptions);
        } catch (Exception e) {
            System.err.println("Failed to load document: " + e.getMessage());
            return;
        }

        // 4️⃣ Print missing‑font warnings.
        System.out.println("=== Missing Font Report ===");
        for (WarningInfo warning : fontWarnings) {
            if (warning.getSource() == WarningSource.FontSubstitution) {
                System.out.println("Substituted '" + warning.getDescription() + "' with '" +
                                   warning.getAdditionalInfo() + "'");
            }
        }
        System.out.println("=== End of Report ===");
    }
}
```

รันโปรแกรมนี้แล้วคุณจะเห็นรายการที่เป็นระเบียบของฟอนต์ทุกตัวที่ Aspose.Words ต้องแทนที่ ไม่มีไลบรารีเพิ่มเติม ไม่มีเวทมนตร์ที่ซ่อนอยู่—แค่ Java แท้ ๆ และพลังของ **Aspose.Words missing font** API

---

## สรุป

เราตอบคำถามหลัก **วิธีการดึงฟอนต์ที่หายไป** ในสภาพแวดล้อม Java ด้วย Aspose.Words โดยการผูก `LoadOptions` warning callback, เก็บ `WarningInfo` แล้วกรองตามแหล่ง `FontSubstitution` คุณจะได้มองเห็นปัญหาฟอนต์ก่อนการเรนเดอร์ใด ๆ วิธีนี้สามารถสเกลจากยูทิลิตี้ไฟล์เดียวจนถึงตัวประมวลผลชุดข้อมูลขนาดใหญ่ และยืดหยุ่นพอที่จะรองรับโฟลเดอร์ฟอนต์กำหนดเอง, การจัดการระดับความรุนแรง, หรืออินพุตแบบ stream

ขั้นตอนต่อไป? ลองฝังฟอนต์ที่แทนที่ลงในเอกสารโดยตรง (`doc.getFontInfos().add(...)`) เพื่อให้ไฟล์สุดท้ายเป็นอิสระจริง ๆ หรือผสานรายงานคำเตือนเข้ากับแดชบอร์ดการตรวจสอบ คุณอาจสนใจหัวข้อที่เกี่ยวข้องเช่น **document processing Java**, **Aspose.Words font substitution warning**, และ **Java LoadOptions warning callback** เพื่อเพิ่มพูนความเชี่ยวชาญของคุณ

ขอให้เขียนโค้ดสนุกและเอกสารของคุณแสดงผลด้วยฟอนต์ที่คุณคาดหวังเสมอ!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}