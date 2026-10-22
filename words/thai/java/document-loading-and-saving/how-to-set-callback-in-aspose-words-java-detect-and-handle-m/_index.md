---
category: general
date: 2026-06-20
description: วิธีตั้งค่า callback ใน Aspose.Words Java เพื่อตรวจจับฟอนต์ที่หายไปและปรับแต่งการโหลดเอกสาร
  เรียนรู้การจัดการคำเตือนการแทนที่ฟอนต์แบบขั้นตอนต่อขั้นตอน
draft: false
keywords:
- how to set callback
- detect missing fonts
- handle missing fonts
- customize document loading
language: th
og_description: วิธีตั้งค่า callback ใน Aspose.Words Java เพื่อตรวจจับแบบอักษรที่หายไป,
  จัดการการแทนที่, และปรับแต่งการโหลดเอกสาร. คู่มือเต็มพร้อมโค้ด.
og_title: วิธีตั้งค่า callback – ตรวจจับฟอนต์ที่หายไปใน Aspose.Words Java
schemas:
- author: Aspose
  dateModified: '2026-06-20'
  description: how to set callback in Aspose.Words Java to detect missing fonts and
    customize document loading. Learn step‑by‑step handling of font substitution warnings.
  headline: how to set callback in Aspose.Words Java – Detect and Handle Missing Fonts
  type: TechArticle
- description: how to set callback in Aspose.Words Java to detect missing fonts and
    customize document loading. Learn step‑by‑step handling of font substitution warnings.
  name: how to set callback in Aspose.Words Java – Detect and Handle Missing Fonts
  steps:
  - name: What if I want the program to stop loading when a font is missing?
    text: 'Throw an exception inside the `warning` method:'
  - name: Does this work for PDFs generated from DOCX?
    text: Absolutely. The callback fires during the **loading** phase, which is identical
      for all output formats (`save` to PDF, DOCX, HTML, etc.). As long as you load
      the source document with the same `LoadOptions`, you’ll catch missing fonts
      before they affect the final PDF.
  - name: Can I capture other warning types (e.g., image conversion)?
    text: Yes—`WarningInfo.getWarningType()` can be compared against other enums like
      `WarningType.IMAGE_CONVERSION`. Just add more `if` branches in the callback.
  - name: Is there a performance impact?
    text: Negligible. The callback runs synchronously during loading, and the extra
      checks are lightweight. If you’re loading thousands of documents, you might
      want to disable warnings in production by setting `loadOptions.setWarningCallback(null);`.
  - name: What’s Next?
    text: '- Explore **font substitution tables** for bulk mapping of many missing
      fonts. - Combine this callback with **document validation** to enforce style
      guides. - Try **custom warning callbacks** that write to a log file or a monitoring
      system instead of `System.out`.'
  type: HowTo
tags:
- Aspose.Words
- Java
- Document Processing
title: วิธีตั้งค่า callback ใน Aspose.Words Java – ตรวจจับและจัดการฟอนต์ที่หายไป
url: /th/java/document-loading-and-saving/how-to-set-callback-in-aspose-words-java-detect-and-handle-m/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# วิธีตั้งค่า callback ใน Aspose.Words Java – ตรวจจับและจัดการฟอนต์ที่หายไป

เคยสงสัย **วิธีตั้งค่า callback** ใน Aspose.Words Java เพื่อให้คุณสามารถตรวจจับฟอนต์ที่หายไปก่อนที่มันจะทำลาย PDF หรือ DOCX ของคุณหรือไม่? คุณไม่ได้เป็นคนเดียว คำเตือนฟอนต์ที่หายไปอาจทำให้การจัดวางเสียหายโดยไม่รู้สึก และหากไม่มี callback คำเตือนที่เหมาะสม คุณอาจไม่สังเกตจนกว่าเอกสารสุดท้ายจะดูผิดพลาด  

ในบทแนะนำนี้เราจะพาคุณผ่านตัวอย่างที่สมบูรณ์พร้อมรันที่ **ตรวจจับฟอนต์ที่หายไป**, **จัดการฟอนต์ที่หายไป** อย่างราบรื่น, และแสดงวิธี **ปรับแต่งการโหลดเอกสาร** ด้วย warning callback. เมื่อจบคุณจะมีคลาส Java ที่เป็นอิสระซึ่งสามารถนำไปใส่ในโปรเจกต์ใดก็ได้ — ไม่ต้องค้นหาเอกสารเพิ่มเติม

## สิ่งที่คุณต้องการ

- Java 8 หรือใหม่กว่า (โค้ดทำงานกับ Java 11+ ด้วย)  
- ไลบรารี Aspose.Words for Java (เวอร์ชัน 23.9 หรือใหม่กว่า)  
- ไฟล์ DOCX ที่อ้างอิงฟอนต์ที่คุณไม่ได้ติดตั้ง (เช่น ฟอนต์องค์กรที่กำหนดเอง)  

หากคุณยังไม่ได้เพิ่ม Aspose.Words เข้าไปในโปรเจกต์ Maven ของคุณ เพียงแค่ใส่:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
</dependency>
```

แค่นั้น—ไม่มีปลั๊กอินเพิ่มเติม ไม่มีการพึ่งพา native

---

## ขั้นตอนที่ 1: ทำความเข้าใจกลไก WarningCallback

The **warning callback** คือวิธีของ Aspose.Words ที่แจ้งเตือนคุณเมื่อมีสิ่งที่ไม่คาดคิดเกิดขึ้นขณะโหลดหรือบันทึกเอกสาร โดยการทำ implement `IWarningCallback` คุณจะได้ควบคุมอย่างเต็มที่ว่าข้อมูลใดจะถูกบันทึก, ถูกละเว้น, หรือแม้กระทั่งแปลงเป็น exception.

> **ทำไมเรื่องนี้ถึงสำคัญ:**  
> เมื่อฟอนต์หายไป Aspose จะใช้ฟอนต์สำรอง ผลลัพธ์ที่แสดงอาจแตกต่างอย่างมาก โดยเฉพาะกับ PDF ที่มีแบรนด์เป็นหลัก การดักจับ `WarningType.FONT_SUBSTITUTION` คุณสามารถบันทึกชื่อฟอนต์ที่แน่นอน, ตัดสินใจว่าจะยกเลิกหรือไม่, หรือแทนที่ด้วยฟอนต์กำหนดเองโดยโปรแกรม

---

## ขั้นตอนที่ 2: สร้างอินสแตนซ์ LoadOptions

`LoadOptions` คือจุดเริ่มต้นสำหรับการปรับแต่งการโหลดเอกสาร คุณจะผูก callback กับอ็อบเจกต์นี้ก่อนที่คุณจะโหลดไฟล์จริง

```java
// Step 2: Prepare LoadOptions
LoadOptions loadOptions = new LoadOptions();
```

ในขณะนี้ `loadOptions` เป็นเพียงคอนเทนเนอร์ธรรมดา—ยังไม่มีอะไรเกิดขึ้นเลย เวทมนตร์ที่แท้จริงจะเริ่มเมื่อเราติดตั้ง callback

---

## ขั้นตอนที่ 3: Implement และผูก Callback

ด้านล่างเป็นคลาสอนามัยแบบย่อที่ implements `IWarningCallback`. มันพิมพ์ข้อความเป็นมิตรไปยังคอนโซลทุกครั้งที่มีการแทนที่ฟอนต์

```java
// Step 3: Attach a warning callback to capture font substitution warnings
loadOptions.setWarningCallback(new IWarningCallback() {
    @Override
    public void warning(WarningInfo info) {
        // Detect missing fonts
        if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
            System.out.println("[Missing Font] " + info.getDescription());
            // Optional: you could throw an exception here to abort loading
            // throw new RuntimeException("Font missing: " + info.getDescription());
        }
    }
});
```

> **เคล็ดลับระดับมืออาชีพ:** หากคุณต้องการ **จัดการฟอนต์ที่หายไป** โดยให้การทดแทน คุณสามารถตั้งค่า `FontSettings` บน `LoadOptions` และแมปฟอนต์ที่หายไปไปยังฟอนต์สำรองที่รู้จักได้

---

## ขั้นตอนที่ 4: โหลดเอกสารด้วยตัวเลือกที่กำหนดเองของคุณ

เมื่อ callback ถูกเชื่อมต่อแล้ว ให้โหลดเอกสาร หากไฟล์อ้างอิงฟอนต์ที่คุณไม่มี คุณจะเห็นคำเตือนที่พิมพ์ออกมา

```java
// Step 4: Load the document using the configured LoadOptions
String docPath = "YOUR_DIRECTORY/doc-with-missing-font.docx";
Document document = new Document(docPath, loadOptions);
```

เมื่อคุณรันโปรแกรม คอนโซลอาจแสดง:

```
[Missing Font] Font substitution: The font "MyCustomFont" was not found. Substituted with "Arial".
```

บรรทัดนั้นพิสูจน์ว่าคุณได้ **ตรวจจับฟอนต์ที่หายไป** อย่างสำเร็จและตอนนี้คุณอยู่ในตำแหน่งที่สามารถ **จัดการฟอนต์ที่หายไป** ตามที่คุณต้องการ

---

## ขั้นตอนที่ 5: ตัวเลือก – แทนที่ฟอนต์ที่หายไปด้วยฟอนต์ที่รู้จัก

หากคุณต้องการแทนที่ฟอนต์ที่หายไปโดยอัตโนมัติด้วยฟอนต์เช่น `Times New Roman` คุณสามารถเพิ่มอ็อบเจกต์ `FontSettings` ได้:

```java
// Optional Step 5: Map missing fonts to a fallback
FontSettings fontSettings = new FontSettings();
fontSettings.setMissingFontNotification(new IWarningCallback() {
    @Override
    public void warning(WarningInfo info) {
        // This will be called for each missing font
        if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
            System.out.println("[Auto‑Replace] " + info.getDescription());
        }
    }
});
// Force substitution to Times New Roman
fontSettings.getSubstitutionSettings().getTableSubstitution().addSubstitutes("MyCustomFont", new String[]{"Times New Roman"});
loadOptions.setFontSettings(fontSettings);
```

ตอนนี้เอกสารโหลดแล้ว และการอ้างอิงใด ๆ ที่มี `MyCustomFont` จะถูกสลับเป็น `Times New Roman` อย่างเงียบ ๆ คอนโซลยังคงบอกคุณว่ามีอะไรถูกแทนที่ เพื่อให้คุณทราบ

---

## ตัวอย่างการทำงานเต็มรูปแบบ

ด้านล่างเป็นคลาส Java เดียวที่รวมทุกขั้นตอนข้างต้น คัดลอก‑วางลงใน IDE ของคุณ ปรับ `docPath` แล้วรัน

```java
import com.aspose.words.*;

public class DetectMissingFontsDemo {
    public static void main(String[] args) {
        try {
            // 1️⃣ Create LoadOptions
            LoadOptions loadOptions = new LoadOptions();

            // 2️⃣ Attach warning callback (detect missing fonts)
            loadOptions.setWarningCallback(new IWarningCallback() {
                @Override
                public void warning(WarningInfo info) {
                    if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                        System.out.println("[Missing Font] " + info.getDescription());
                    }
                }
            });

            // 3️⃣ (Optional) Set up automatic font substitution
            FontSettings fontSettings = new FontSettings();
            fontSettings.getSubstitutionSettings()
                        .getTableSubstitution()
                        .addSubstitutes("MyCustomFont", new String[]{"Times New Roman"});
            loadOptions.setFontSettings(fontSettings);

            // 4️⃣ Load the document with custom loading behavior
            String docPath = "YOUR_DIRECTORY/doc-with-missing-font.docx";
            Document doc = new Document(docPath, loadOptions);

            // 5️⃣ Save to PDF to see the final result (optional)
            doc.save("output.pdf");
            System.out.println("Document loaded and saved successfully.");

        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}
```

**ผลลัพธ์ที่คาดหวัง**

```
[Missing Font] Font substitution: The font "MyCustomFont" was not found. Substituted with "Times New Roman".
Document loaded and saved successfully.
```

ตอนนี้คุณมีวิธีที่ทำซ้ำได้เพื่อ **ตรวจจับฟอนต์ที่หายไป**, **จัดการฟอนต์ที่หายไป**, และ **ปรับแต่งการโหลดเอกสาร** — ทั้งหมดโดยการเรียนรู้ **วิธีตั้งค่า callback** อย่างถูกต้อง

---

## คำถามที่พบบ่อย

### ถ้าฉันต้องการให้โปรแกรมหยุดโหลดเมื่อฟอนต์หายไป?

ให้โยน exception ภายในเมธอด `warning`:

```java
throw new RuntimeException("Critical: Missing font - " + info.getDescription());
```

บล็อก catch ที่ด้านล่างจะจับมัน และคุณสามารถตัดสินใจว่าจะบันทึกหรือแจ้งเตือนผู้ใช้อย่างไร

### วิธีนี้ทำงานกับ PDF ที่สร้างจาก DOCX หรือไม่?

แน่นอน Callback จะทำงานในช่วง **loading** ซึ่งเหมือนกันสำหรับทุกรูปแบบผลลัพธ์ (`save` เป็น PDF, DOCX, HTML, ฯลฯ) ตราบใดที่คุณโหลดเอกสารต้นฉบับด้วย `LoadOptions` เดียวกัน คุณจะดักจับฟอนต์ที่หายไปก่อนที่มันจะส่งผลต่อ PDF สุดท้าย

### ฉันสามารถดักจับประเภทคำเตือนอื่น ๆ (เช่น การแปลงภาพ) ได้หรือไม่?

ได้ — `WarningInfo.getWarningType()` สามารถเปรียบเทียบกับ enum อื่น ๆ เช่น `WarningType.IMAGE_CONVERSION` เพียงเพิ่มเงื่อนไข `if` เพิ่มเติมใน callback

### มีผลต่อประสิทธิภาพหรือไม่?

ไม่มีนัยสำคัญ Callback ทำงานแบบ synchronous ระหว่างการโหลด และการตรวจสอบเพิ่มเติมนั้นเบา หากคุณกำลังโหลดเอกสารหลายพันไฟล์ คุณอาจต้องการปิดการเตือนในสภาพการผลิตโดยตั้งค่า `loadOptions.setWarningCallback(null);`

---

## ภาพรวมโดยภาพ

![ตัวอย่างการตั้งค่า callback ใน Aspose.Words Java](https://example.com/images/callback-diagram.png "ตัวอย่างการตั้งค่า callback")

*แผนภาพแสดงกระบวนการ: `LoadOptions` → `IWarningCallback` → การโหลดเอกสาร → การจัดการการแทนที่ฟอนต์*

---

## สรุป

เราได้ครอบคลุม **วิธีตั้งค่า callback** ใน Aspose.Words Java, แสดงวิธี **ตรวจจับฟอนต์ที่หายไป**, แสดงวิธีปฏิบัติในการ **จัดการฟอนต์ที่หายไป**, และอธิบายวิธี **ปรับแต่งการโหลดเอกสาร** ด้วย `LoadOptions`.  

ด้วยความรู้นี้ คุณสามารถปกป้องสายงานเอกสารของคุณจากการสลับฟอนต์โดยเงียบ, รักษาแบรนด์ให้คงเดิม, และให้ผู้ใช้ได้รับข้อเสนอแนะที่ชัดเจนเมื่อเกิดปัญหา

### ต่อไปคืออะไร?

- สำรวจ **ตารางการแทนที่ฟอนต์** สำหรับการแมปหลายฟอนต์ที่หายไปเป็นกลุ่ม  
- ผสาน callback นี้กับ **การตรวจสอบเอกสาร** เพื่อบังคับใช้แนวทางสไตล์  
- ทดลอง **custom warning callbacks** ที่เขียนลงไฟล์บันทึกหรือระบบมอนิเตอร์แทน `System.out`  

อย่าลังเลที่จะทดลองและบอกให้เราทราบว่าคุณปรับแต่ง callback อย่างไรสำหรับโปรเจกต์ของคุณเอง ขอให้เขียนโค้ดอย่างสนุกสนาน!

---

## สิ่งที่คุณควรเรียนต่อไป

บทแนะนำต่อไปนี้ครอบคลุมหัวข้อที่เกี่ยวข้องอย่างใกล้ชิดซึ่งต่อยอดจากเทคนิคที่แสดงในคู่มือนี้ แต่ละแหล่งข้อมูลมีตัวอย่างโค้ดทำงานเต็มรูปแบบพร้อมคำอธิบายทีละขั้นตอน เพื่อช่วยให้คุณเชี่ยวชาญคุณสมบัติ API เพิ่มเติมและสำรวจวิธีการนำไปใช้แบบอื่นในโปรเจกต์ของคุณ

- [วิธีตั้งค่า LoadOptions ใน Aspose.Words สำหรับ Java](/words/english/java/document-loading-and-saving/using-load-options/)
- [วิธีตรวจจับฟอนต์ใน Aspose.Words – จัดการคำเตือนและการตั้งค่า](/words/english/net/working-with-fonts/how-to-detect-fonts-in-aspose-words-handle-warnings-settings/)
- [วิธีดักจับฟอนต์ใน Aspose.Words – คู่มือเต็ม](/words/english/net/working-with-fonts/how-to-capture-fonts-in-aspose-words-complete-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}