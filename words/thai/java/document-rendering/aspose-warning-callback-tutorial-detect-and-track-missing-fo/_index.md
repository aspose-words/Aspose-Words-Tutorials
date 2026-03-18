---
category: general
date: 2026-03-17
description: เรียนรู้บทแนะนำการใช้ callback คำเตือนของ Aspose เพื่อตรวจจับและติดตามฟอนต์ที่หายไปในเอกสาร
  Java พร้อมตัวอย่างที่สมบูรณ์และสามารถรันได้
draft: false
keywords:
- aspose warning callback tutorial
- detect missing fonts
- track missing fonts
language: th
og_description: เชี่ยวชาญบทเรียนการเรียกคืนคำเตือนของ Aspose เพื่อค้นหาและติดตามแบบอักษรที่หายไปในกระบวนการประมวลผลคำด้วย
  Java ของคุณ
og_title: บทแนะนำ callback คำเตือนของ aspose – ตรวจจับฟอนต์ที่หายไป
tags:
- Aspose.Words
- Java
- Font Substitution
- Document Processing
title: บทเรียนการเรียกคืนคำเตือนของ Aspose – การตรวจจับและติดตามฟอนต์ที่หายไป
url: /th/java/document-rendering/aspose-warning-callback-tutorial-detect-and-track-missing-fo/
---

Make sure to keep markdown formatting.

Let's produce translation.

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# aspose warning callback tutorial – ตรวจจับและติดตามฟอนต์ที่หายไป

เคยสงสัยหรือไม่ว่า **จะตรวจจับฟอนต์ที่หายไป** อย่างไรเมื่อทำการแปลงหรือแก้ไขไฟล์ Word ด้วย Aspose.Words? คุณไม่ได้เป็นคนเดียวที่มีคำถามนี้ ในหลายโครงการจริง ๆ ฟอนต์ที่หายไปอาจทำให้เลย์เอาต์ผิดพลาด และคุณต้องการวิธีที่เชื่อถือได้เพื่อ **ติดตามฟอนต์ที่หายไป** ก่อนที่มันจะสร้างปัญหาให้คุณในภายหลัง  

ข่าวดีคือ? **aspose warning callback tutorial** ให้คุณมีฮุคโปรแกรมเมติกที่สะอาดตาซึ่งพิมพ์คำเตือนการแทนที่ฟอนต์ในขณะที่เกิดขึ้น ในคู่มือนี้เราจะพาคุณผ่านการตั้งค่าคอลแบ็ก, การโหลดเอกสาร, และการดูคำเตือนทำงาน—ทั้งหมดใน Java  

เมื่ออ่านบทความนี้จนจบ คุณจะสามารถตรวจจับฟอนต์ที่หายไปโดยอัตโนมัติ, บันทึกไว้, และตัดสินใจว่าจะฝังฟอนต์ทดแทนหรือปรับไฟล์ต้นฉบับของคุณหรือไม่ ไม่ต้องใช้เครื่องมือภายนอกใด ๆ

## Prerequisites

- **Java 8+** (โค้ดนี้คอมไพล์ได้กับ JDK รุ่นล่าสุดใดก็ได้)
- **Aspose.Words for Java** เวอร์ชัน 23.10 หรือใหม่กว่า – ดาวน์โหลดจากพอร์ทัลของ Aspose หรือเพิ่มเป็น dependency ของ Maven
- ตัวอย่างไฟล์ DOCX ที่ตั้งใจอ้างอิงฟอนต์ที่คุณไม่ได้ติดตั้ง (เช่น “Comic Sans MS” บนเครื่อง Linux)

แค่นี้แหละ—ไม่ต้องใช้ไลบรารีเพิ่มเติม, ไม่ต้องทำขั้นตอนการสร้างที่ซับซ้อน

## Step 1: Register a Warning Callback – The Core of the aspose warning callback tutorial

สิ่งแรกที่บทเรียนสอนคือการแนบ listener สำหรับคำเตือน Aspose.Words จะสร้างอ็อบเจกต์ `WarningInfo` สำหรับทุกปัญหาที่พบ และแฟล็ก `WarningSource.FONT_SUBSTITUTION` จะบอกเราว่าเมื่อใดที่ฟอนต์กำลังถูกแทนที่

```java
import com.aspose.words.*;

public class FontDiagnostics {
    public static void main(String[] args) throws Exception {

        // Step 1: Register a warning callback to capture font substitution warnings.
        Document.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) {
                // We only care about font‑substitution events.
                if (info.getSource() == WarningSource.FONT_SUBSTITUTION) {
                    System.out.println("Font substitution warning:");
                    System.out.println("  Original:   " + info.getDescription());
                    System.out.println("  Substituted:" + info.getAdditionalInfo());
                }
            }
        });
```

**ทำไมเรื่องนี้ถึงสำคัญ:** หากไม่มีคอลแบ็ก Aspose จะทำการแทนที่ฟอนต์ที่หายไปโดยเงียบ ๆ และคุณจะไม่รู้ว่าตัวอักษรใดอาจดูผิดพลาด การบันทึกคำเตือนทำให้คุณ **ตรวจจับฟอนต์ที่หายไป** ตั้งแต่เนิ่น ๆ และตัดสินใจว่าจะฝังฟอนต์ที่ถูกต้องหรือไม่

> **Pro tip:** หากต้องการเก็บคำเตือนเพื่อรายงานในภายหลัง ให้เก็บไว้ใน `List<WarningInfo>` แทนการพิมพ์ออกโดยตรง

## Step 2: Load the Document – Where missing fonts might hide

ตอนนี้เราจะโหลดไฟล์ DOCX ที่อาจอ้างอิงฟอนต์ที่ไม่มีในเครื่อง การโหลดนี้จะกระตุ้นคอลแบ็กคำเตือนหากมีฟอนต์ใดหายไป

```java
        // Step 2: Load a document that may contain missing fonts.
        Document document = new Document("YOUR_DIRECTORY/input.docx");
```

**อะไรกำลังเกิดขึ้นเบื้องหลัง?** Aspose จะวิเคราะห์คำนิยามสไตล์ของเอกสาร, สแกนแต่ละ run ของข้อความ, และตรวจสอบคลังฟอนต์ของระบบ เมื่อไม่พบฟอนต์ที่ตรงกันอย่างเต็มที่ ระบบจะใช้ฟอนต์ทดแทนและส่งสัญญาณคำเตือนที่เราได้เชื่อมต่อไว้

## Step 3: Save the Document – Flushing the warnings

สุดท้าย เราจะบันทึกเอกสาร การบันทึกนี้ยังทำการประเมินฟอนต์อีกครั้ง ดังนั้นคำเตือนใดที่ไม่ได้ถูกส่งในขั้นตอนการโหลดจะปรากฏในขั้นตอนนี้

```java
        // Step 3: Save the document; any font substitution warnings will be printed by the callback.
        document.save("YOUR_DIRECTORY/output.docx");
    }
}
```

เมื่อคุณรันโปรแกรม คุณจะเห็นผลลัพธ์บนคอนโซลคล้ายกับ:

```
Font substitution warning:
  Original:   Font "Comic Sans MS" not found.
  Substituted: Using "Arial" as fallback.
```

ผลลัพธ์นี้พิสูจน์ว่า **aspose warning callback tutorial** ทำงานได้สำเร็จ และคุณได้ **ตรวจจับฟอนต์ที่หายไป** อย่างสำเร็จและกำลัง **ติดตามฟอนต์ที่หายไป** ผ่านบันทึก

## How to Detect Missing Fonts in a Word Document – Beyond the Basics

วิธีคอลแบ็กเหมาะสำหรับการรันครั้งเดียว แต่บางครั้งคุณอาจต้องการยูทิลิตี้ที่ใช้ซ้ำได้ นี่คือตัวห่อ (wrapper) สั้น ๆ ที่คุณสามารถใส่ลงในโปรเจคใดก็ได้:

```java
public class FontMissingChecker {
    private final List<String> missingFonts = new ArrayList<>();

    public FontMissingChecker() {
        Document.setWarningCallback((WarningInfo info) -> {
            if (info.getSource() == WarningSource.FONT_SUBSTITUTION) {
                missingFonts.add(info.getDescription());
            }
        });
    }

    public List<String> check(String path) throws Exception {
        new Document(path); // triggers warnings
        return missingFonts;
    }
}
```

เรียกใช้งานแบบนี้:

```java
FontMissingChecker checker = new FontMissingChecker();
List<String> fonts = checker.check("input.docx");
if (!fonts.isEmpty()) {
    System.out.println("Missing fonts detected:");
    fonts.forEach(System.out::println);
}
```

ตอนนี้คุณมีเมธอด **detect missing fonts** ที่สามารถคืนค่าเป็นรายการเพื่อส่งต่อไปยัง pipeline CI หรือ UI ได้แล้ว

## Tracking Missing Fonts with Aspose.Words – Reporting for Teams

ในทีมขนาดใหญ่ คุณอาจต้องการสร้างรายงาน CSV ของฟอนต์ที่หายไปทั้งหมดในหลายเอกสาร ผสานยูทิลิตี้ข้างต้นกับการวนลูปไฟล์อย่างง่าย:

```java
import java.nio.file.*;
import java.io.*;

public class BulkFontReporter {
    public static void main(String[] args) throws Exception {
        Path folder = Paths.get("YOUR_DIRECTORY");
        try (BufferedWriter writer = Files.newBufferedWriter(folder.resolve("missing-fonts-report.csv"))) {
            writer.write("Document,Missing Font\n");
            Files.list(folder)
                 .filter(p -> p.toString().endsWith(".docx"))
                 .forEach(p -> {
                     try {
                         FontMissingChecker checker = new FontMissingChecker();
                         List<String> missing = checker.check(p.toString());
                         for (String msg : missing) {
                             // Extract font name from description
                             String font = msg.replaceAll("Font \"(.*?)\".*", "$1");
                             writer.write(p.getFileName() + "," + font + "\n");
                         }
                     } catch (Exception e) {
                         // In a real app, log the error
                     }
                 });
        }
        System.out.println("Report generated at missing-fonts-report.csv");
    }
}
```

การรันสคริปต์นี้จะให้ไฟล์ CSV **track missing fonts** ที่นักพัฒนาทุกคนสามารถดูได้ก่อนทำการคอมมิตเอกสารเข้าสู่ production

## Common Pitfalls & How to Avoid Them

| Pitfall | Why it Happens | Fix |
|---------|----------------|-----|
| **Callback not firing** | คุณลืมตั้งค่าคอลแบ็ก **ก่อน** โหลดเอกสาร | วาง `Document.setWarningCallback` ไว้ที่ส่วนบนสุดของ `main` |
| **Only first warning appears** | Aspose แคชคำเตือนต่ออินสแตนซ์ `Document` | ใช้อ็อบเจกต์ `Document` ใหม่สำหรับแต่ละไฟล์ หรือรีเซ็ตคอลแบ็กระหว่างการรัน |
| **Wrong font name in log** | คำอธิบายมีข้อความเพิ่มเติม (“Font … not found”) | ใช้ regex เพื่อตัดข้อความตามตัวอย่างใน CSV |
| **Performance hit on large batches** | คอลแบ็กทำงานบนทุก run ของข้อความ ทำให้ใช้ทรัพยากรสูง | จำกัดการตรวจสอบเป็นขั้นตอน pre‑flight; ข้ามการบันทึกหากต้องการเพียงการตรวจจับ |

## Expected Results & Verification

1. **Console output** – ควรเห็นอย่างน้อยหนึ่งบรรทัด “Font substitution warning” สำหรับแต่ละฟอนต์ที่หายไป  
2. **CSV report** – หลังสคริปต์ทำงานเสร็จ เปิด `missing-fonts-report.csv` และตรวจสอบว่าแต่ละแถวแสดงชื่อเอกสารและฟอนต์ที่หายไปอย่างแม่นยำ  
3. **Saved document** – ไฟล์ DOCX ที่บันทึกออกมาจะใช้ฟอนต์ทดแทนในการแสดงผล แต่เลย์เอาต์อาจแตกต่างจากต้นฉบับ

หากขั้นตอนใดไม่เป็นไปตามที่อธิบายไว้ ตรวจสอบให้แน่ใจว่า JAR ของ Aspose.Words อยู่ใน classpath และ `input.docx` จริง ๆ แล้วอ้างอิงฟอนต์ที่ไม่มีในระบบปฏิบัติการของคุณ

## Conclusion

คุณเพิ่งทำ **aspose warning callback tutorial** เสร็จสิ้น ซึ่งแสดงวิธี **ตรวจจับฟอนต์ที่หายไป** และ **ติดตามฟอนต์ที่หายไป** ในแอปพลิเคชัน Java โดยการลงทะเบียน listener สำหรับคำเตือน, โหลดเอกสาร, และอาจส่งออกผลลัพธ์ คุณจะได้มองเห็นปัญหาที่เกี่ยวกับฟอนต์อย่างเต็มที่ก่อนที่มันจะปรากฏใน production  

ต่อไปคุณอาจสำรวจ:

- ฝังฟอนต์ที่หายไปโดยตรงด้วย `LoadOptions.setFontSubstitution`  
- ใช้คลาส `FontSettings` เพื่อแมปฟอนต์ที่หายไปไปยังฟอนต์ทดแทนเฉพาะ  
- ผสานรายงาน CSV เข้ากับ pipeline CI/CD เพื่อให้การ build ล้มเหลวเมื่อพบฟอนต์ที่ไม่ได้บันทึกไว้  

ลองใช้งาน ปรับคอลแบ็กให้สอดคล้องกับเฟรมเวิร์กการบันทึกของคุณ แล้วคุณจะเห็นกระบวนการทำงานกับเอกสารของคุณแข็งแกร่งขึ้นอย่างมาก Happy coding!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}