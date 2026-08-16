---
category: general
date: 2026-06-17
description: บันทึกคำเตือนการแทนที่ฟอนต์ใน Java ด้วย Aspose.Words – ตรวจจับฟอนต์ที่หายไประหว่างการโหลดเอกสารและทำให้ผลลัพธ์ของคุณสอดคล้องกัน
draft: false
keywords:
- log font substitution warnings
- Aspose.Words Java
- font substitution
- warning callback
- LoadOptions
- document loading
language: th
og_description: บันทึกคำเตือนการแทนที่ฟอนต์ใน Java ด้วย Aspose.Words เรียนรู้วิธีจับการแจ้งเตือนฟอนต์ที่หายไประหว่างการโหลดเอกสารและทำให้ไฟล์
  PDF ของคุณคงความสมบูรณ์.
og_title: บันทึกคำเตือนการแทนที่ฟอนต์ใน Java – คู่มือฉบับสมบูรณ์
schemas:
- author: Aspose
  dateModified: '2026-06-17'
  description: Log font substitution warnings in Java using Aspose.Words – capture
    missing fonts during document load and keep your output consistent.
  headline: Log Font Substitution Warnings in Java with Aspose.Words
  type: TechArticle
- description: Log font substitution warnings in Java using Aspose.Words – capture
    missing fonts during document load and keep your output consistent.
  name: Log Font Substitution Warnings in Java with Aspose.Words
  steps:
  - name: Prerequisites
    text: '- Java 8 or newer (the code works with Java 11+ as well). - Aspose.Words
      for Java library (version 23.10 or later is recommended). - A sample `.docx`
      that references a font not installed on your machine (e.g., `MissingFont.docx`).'
  - name: Logging to a File Instead of the Console
    text: 'If you prefer a persistent log, replace the `System.out.println` call with
      a `FileWriter`:'
  - name: Capturing Multiple Documents in a Loop
    text: 'When processing a folder of documents, you can reuse the same callback:'
  - name: Dealing with Embedded Fonts
    text: 'Aspose.Words can embed missing fonts if you enable it:'
  type: HowTo
tags:
- Java
- Aspose.Words
- Document Processing
title: บันทึกคำเตือนการแทนที่ฟอนต์ใน Java ด้วย Aspose.Words
url: /th/java/document-loading-and-saving/log-font-substitution-warnings-in-java-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# บันทึกคำเตือนการแทนที่ฟอนต์ใน Java – คู่มือฉบับสมบูรณ์

เคยสงสัยไหมว่าจะแสดง **คำเตือนการแทนที่ฟอนต์** อย่างไรเมื่อเอกสาร Word ดึงฟอนต์ที่คุณไม่มีบนเซิร์ฟเวอร์? คุณไม่ได้เป็นคนเดียวที่สับสนกับฟอนต์ที่หายไปแล้วถูกแทนที่โดยเงียบ ๆ ข่าวดีคือ Aspose.Words for Java มีวิธีที่สะอาดตาในการดักจับการแทนที่เหล่านั้นในทันทีที่เอกสารถูกโหลด

ในบทแนะนำนี้เราจะทำตามตัวอย่างเชิงปฏิบัติที่แสดงอย่างชัดเจนว่าจะแนบ callback สำหรับคำเตือนอย่างไร, กรองเหตุการณ์การแทนที่ฟอนต์, และเขียนผลลัพธ์ลงคอนโซล (หรือ logger ใด ๆ ที่คุณต้องการ) เมื่อจบคุณจะได้ snippet ที่นำกลับไปใช้ใหม่ได้ในโปรเจกต์ Java ใด ๆ ที่ใช้ **Aspose.Words Java**

## สิ่งที่คุณจะได้เรียนรู้

- วิธีกำหนดค่า **LoadOptions** เพื่อจับคำเตือน
- วิธีสร้าง **IWarningCallback** ที่ตอบสนองต่อเหตุการณ์ **font substitution** เท่านั้น
- วิธีโหลดเอกสารอย่างปลอดภัยพร้อมบันทึกเส้นทางการตรวจสอบฟอนต์ที่หายไปอย่างชัดเจน
- เคล็ดลับในการขยายโซลูชันให้บันทึกเป็นไฟล์หรือส่งไปยังระบบมอนิเตอร์

### ข้อกำหนดเบื้องต้น

- Java 8 หรือใหม่กว่า (โค้ดทำงานได้กับ Java 11+ ด้วย)
- ไลบรารี Aspose.Words for Java (แนะนำเวอร์ชัน 23.10 หรือใหม่กว่า)
- ตัวอย่างไฟล์ `.docx` ที่อ้างอิงฟอนต์ที่ไม่ได้ติดตั้งบนเครื่องของคุณ (เช่น `MissingFont.docx`)

ไม่ต้องใช้เฟรมเวิร์กเพิ่มเติม—แค่ Java ธรรมดาและ Aspose.JARs

---

## ขั้นตอนที่ 1: กำหนดค่า LoadOptions สำหรับ Aspose.Words Java

ก่อนที่คุณจะดักจับคำเตือนใด ๆ คุณต้องมีอินสแตนซ์ของ **LoadOptions** วัตถุนี้บอก Aspose.Words ว่าจะทำงานอย่างไรขณะพาร์สไฟล์ที่เข้ามา

```java
// Step 1: Create LoadOptions to enable warning capture
LoadOptions loadOptions = new LoadOptions();
```

ทำไมขั้นตอนนี้ถึงสำคัญ? หากไม่มีอ็อบเจ็กต์ `LoadOptions` ไลบรารีจะทำการแทนที่ฟอนต์ที่หายไปโดยเงียบ ๆ และคุณจะไม่เห็นร่องรอยใด ๆ การสร้างอ็อบเจ็กต์อย่างชัดเจนจะเปิดประตูสู่ **warning callback** ที่กำหนดเองเพื่อบันทึกสิ่งที่คุณสนใจ

> **Pro tip:** หากคุณกำลังโหลดเอกสารหลายไฟล์เป็นชุด ให้ใช้ `LoadOptions` ตัวเดียวซ้ำเพื่อหลีกเลี่ยงการสร้างอ็อบเจ็กต์ที่ไม่จำเป็น

---

## ขั้นตอนที่ 2: สร้าง Warning Callback สำหรับการแทนที่ฟอนต์

Aspose.Words มีอินเทอร์เฟซ `IWarningCallback` ให้ใช้งาน การทำให้คลาสของคุณ implements อินเทอร์เฟซนี้จะทำให้คุณกำหนดพฤติกรรมเมื่อเอนจินส่ง `WarningInfo` ในกรณีของเราเราต้องการตอบสนองต่อ `WarningType.FONT_SUBstitution` เท่านั้น

```java
// Step 2: Register a warning callback that logs only font‑substitution warnings
loadOptions.setWarningCallback(new IWarningCallback() {
    @Override
    public void warning(WarningInfo info) {
        // Filter for font‑substitution warnings only
        if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
            // Simple console output – replace with a logger if you prefer
            System.out.println("Font substitution: " + info.getMessage());
        }
    }
});
```

ข้อควรจำบางประการ:

1. **Filtering** – คำสั่ง `if` ทำให้เราข้ามคำเตือนที่ไม่เกี่ยวข้อง (เช่นปัญหา layout) เพื่อให้บันทึกเป็นระเบียบ
2. **Thread safety** – Callback ทำงานบนเธรดเดียวกับการโหลดเอกสาร ดังนั้นสำหรับการพิมพ์ลงคอนโซลง่าย ๆ ไม่ต้องทำ synchronization เพิ่มเติม หากเขียนลง logger ที่ใช้ร่วมกันต้องแน่ใจว่าเป็น thread‑safe
3. **Extensibility** – ต้องการบันทึกลงไฟล์? แทนที่ `System.out.println` ด้วย `java.util.logging.Logger` หรือเฟรมเวิร์ก logging ของบุคคลที่สาม

---

## ขั้นตอนที่ 3: โหลดเอกสารด้วยตัวเลือกที่กำหนดไว้

เมื่อ callback พร้อมแล้ว ให้โหลดไฟล์ Word ของคุณ ณ ขณะที่ Aspose.Words พาร์สเอกสาร ฟอนต์ที่หายไปใด ๆ จะทำให้ callback ที่กำหนดไว้ข้างต้นทำงาน

```java
// Step 3: Load the document with the warning‑aware LoadOptions
Document doc = new Document("YOUR_DIRECTORY/MissingFont.docx", loadOptions);
```

หากไฟล์ต้นทางอ้างอิงฟอนต์ที่ไม่ได้ติดตั้ง คุณจะเห็นผลลัพธ์คล้ายกับ:

```
Font substitution: Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
```

บรรทัดนั้นคือ **log font substitution warnings** ที่คุณกำลังมองหา ตอนนี้คุณสามารถดำเนินการต่อได้—อาจแจ้งผู้ใช้, สลับไปใช้ stylesheet สำรอง, หรือบันทึกเพื่อการปฏิบัติตามข้อกำหนด

---

## ขั้นตอนที่ 4: ดำเนินการต่อไปตามปกติ

หลังจากโหลดเสร็จ เอกสารจะทำงานเหมือนอ็อบเจ็กต์ `Document` ใด ๆ อย่าลังเลที่จะตรวจสอบ sections, ดึงข้อความ, หรือแปลงเป็น PDF การบันทึกคำเตือนเกิดขึ้นอัตโนมัติในขั้นตอนการโหลด จึงไม่ต้องเขียนโค้ดเพิ่มเติม

```java
// Example: Print the number of sections – just to prove the doc is usable
System.out.println("Document has " + doc.getSections().getCount() + " sections.");
```

คอนโซลจะโชว์ทั้งคำเตือนการแทนที่ฟอนต์ (ถ้ามี) **และ** จำนวน sections เพื่อยืนยันว่าเอกสารทำงานเต็มที่

---

## เคล็ดลับขั้นสูง & กรณีขอบ

### บันทึกลงไฟล์แทนคอนโซล

หากต้องการบันทึกแบบถาวร ให้เปลี่ยนการเรียก `System.out.println` เป็น `FileWriter`:

```java
private static final String LOG_PATH = "logs/font_substitutions.txt";

loadOptions.setWarningCallback(new IWarningCallback() {
    @Override
    public void warning(WarningInfo info) {
        if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
            try (FileWriter fw = new FileWriter(LOG_PATH, true)) {
                fw.write("Font substitution: " + info.getMessage() + System.lineSeparator());
            } catch (IOException e) {
                e.printStackTrace();
            }
        }
    }
});
```

อย่าลืมจัดการ `IOException` อย่างเหมาะสมในโค้ด production

### ดักจับหลายเอกสารในลูป

เมื่อประมวลผลโฟลเดอร์ของเอกสารหลายไฟล์ คุณสามารถใช้ callback เดียวซ้ำได้:

```java
File[] files = new File("input").listFiles((dir, name) -> name.endsWith(".docx"));
for (File f : files) {
    Document d = new Document(f.getAbsolutePath(), loadOptions);
    // Additional processing...
}
```

เนื่องจาก callback ถูกแนบกับ `loadOptions` ทุกการวนลูปจะบันทึกเหตุการณ์การแทนที่ฟอนต์โดยอัตโนมัติ

### จัดการกับฟอนต์ที่ฝังอยู่

Aspose.Words สามารถฝังฟอนต์ที่หายไปได้หากเปิดใช้งาน:

```java
loadOptions.setLoadFormat(LoadFormat.DOCX);
loadOptions.setEnableFontSubstitution(true); // default is true
```

แม้เปิดการฝังฟอนต์แล้ว callback ยังทำงานอยู่ ทำให้คุณมองเห็นว่าฟอนต์ใดถูกแทนที่

---

## ตัวอย่างทำงานเต็มรูปแบบ

ด้านล่างเป็นโปรแกรมที่พร้อมรัน คัดลอกไปยังคลาสชื่อ `FontSubstitutionDiagnostics.java` ปรับเส้นทางไฟล์ตามความต้องการแล้วรัน

```java
import com.aspose.words.*;

import java.io.FileWriter;
import java.io.IOException;

/**
 * Demonstrates how to log font substitution warnings using Aspose.Words for Java.
 */
public class FontSubstitutionDiagnostics {

    // Optional: path to a persistent log file
    private static final String LOG_FILE = "font_substitution_log.txt";

    public static void main(String[] args) throws Exception {
        // 1️⃣ Create LoadOptions to capture warnings
        LoadOptions loadOptions = new LoadOptions();

        // 2️⃣ Register a warning callback that logs only font‑substitution warnings
        loadOptions.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) {
                if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                    String message = "Font substitution: " + info.getMessage();
                    // Log to console
                    System.out.println(message);
                    // Also append to a file (optional)
                    try (FileWriter fw = new FileWriter(LOG_FILE, true)) {
                        fw.write(message + System.lineSeparator());
                    } catch (IOException e) {
                        // In a real app, use a proper logging framework
                        e.printStackTrace();
                    }
                }
            }
        });

        // 3️⃣ Load the document with the configured LoadOptions
        Document doc = new Document("YOUR_DIRECTORY/MissingFont.docx", loadOptions);

        // 4️⃣ Continue normal processing – e.g., print section count
        System.out.println("Document has " + doc.getSections().getCount() + " sections.");
    }
}
```

**ผลลัพธ์ที่คาดหวัง** (สมมติว่าเอกสารต้นทางอ้างอิงฟอนต์ที่หายไป):

```
Font substitution: Font 'Times New Roman' was not found. Substituted with 'Arial'.
Document has 3 sections.
```

ทั้งคอนโซลและไฟล์ `font_substitution_log.txt` จะมีคำเตือนนี้ ทำให้คุณมี audit trail ที่เชื่อถือได้

---

## สรุป

เราได้แสดงวิธี **บันทึกคำเตือนการแทนที่ฟอนต์** ใน Java ด้วย Aspose.Words โดยกำหนด `LoadOptions`, เชื่อมต่อ `IWarningCallback`, และโหลดเอกสาร คุณจะได้มองเห็นเหตุการณ์ฟอนต์ที่หายไปทั้งหมดที่อาจมองไม่เห็นได้จากก่อนหน้า จากนี้คุณสามารถ:

- ส่งคำเตือนไปยังบริการ logging กลาง
- สร้างการแจ้งเตือนสำหรับ pipeline ควบคุมคุณภาพ
- ผสานเทคนิคนี้กับกลยุทธ์ **document loading** อื่น ๆ เช่น การแปลงเป็น PDF หรือ mail‑merge

ลองปรับเปลี่ยนได้ตามใจ—สลับ logger จากคอนโซลเป็น SLF4J, เพิ่ม timestamp, หรือส่งการแจ้งเตือนไปยัง dashboard การทำงานหลักยังคงเหมือนเดิม และตอนนี้คุณมีพื้นฐานที่มั่นคงสำหรับการจัดการฟอนต์อย่างแข็งแรงใน workflow เอกสารที่ใช้ Java

มีวิธีพิเศษที่อยากแชร์ไหม? บางทีคุณอาจรวมโค้ดนี้กับ Spring Boot หรือฟังก์ชันคลาวด์ ฝากคอมเมนต์ด้านล่าง แล้วเราจะต่อสนทนากันต่อไป ขอให้โค้ดสนุก!

## สิ่งที่คุณควรเรียนต่อไป

บทแนะนำต่อไปนี้ครอบคลุมหัวข้อที่เกี่ยวข้องอย่างใกล้ชิดและต่อยอดจากเทคนิคที่แสดงในคู่มือนี้ แต่ละแหล่งรวมตัวอย่างโค้ดทำงานเต็มรูปแบบพร้อมคำอธิบายขั้นตอนเพื่อช่วยให้คุณเชี่ยวชาญฟีเจอร์ API เพิ่มเติมและสำรวจแนวทางการทำงานทางเลือกในโปรเจกต์ของคุณ

- [Capture Font Substitution Warnings in Java with Aspose.Words – Complete Guide](/words/english/java/document-loading-and-saving/capture-font-substitution-warnings-in-java-with-aspose-words/)
- [Using Document Options and Settings in Aspose.Words for Java](/words/english/java/document-manipulation/using-document-options-and-settings/)
- [Enable Font Substitution Warnings in Aspose.Words – Complete Guide](/words/english/net/working-with-fonts/enable-font-substitution-warnings-in-aspose-words-complete-g/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}