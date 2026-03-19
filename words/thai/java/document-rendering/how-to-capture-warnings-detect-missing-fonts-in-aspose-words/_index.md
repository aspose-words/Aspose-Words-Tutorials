---
category: general
date: 2026-03-19
description: เรียนรู้วิธีจับคำเตือนใน Aspose.Words for Java และตรวจจับฟอนต์ที่หายไป
  คู่มือขั้นตอนนี้ยังแสดงวิธีจัดการกับฟอนต์ที่หายไปอย่างราบรื่น
draft: false
keywords:
- how to capture warnings
- detect missing fonts
- how to detect missing fonts
- handle missing fonts
language: th
og_description: วิธีดักจับคำเตือนใน Aspose.Words for Java, ตรวจจับฟอนต์ที่หายไป, และจัดการฟอนต์ที่หายไปพร้อมตัวอย่างโค้ดเต็มรูปแบบ.
og_title: วิธีดักจับคำเตือน – ตรวจจับฟอนต์ที่หายไปใน Aspose.Words
tags:
- Aspose.Words
- Java
- Font Substitution
- Document Processing
title: วิธีจับคำเตือน – ตรวจจับฟอนต์ที่หายไปใน Aspose.Words
url: /th/java/document-rendering/how-to-capture-warnings-detect-missing-fonts-in-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# วิธีจับคำเตือน – ตรวจจับฟอนต์ที่หายไปใน Aspose.Words

เคยสงสัย **วิธีจับคำเตือน** เมื่อเอกสาร Word โหลดและฟอนต์บางตัวไม่มีในเครื่องหรือไม่? คุณไม่ได้เป็นคนเดียว ในหลายโครงการจริง ฟอนต์ที่หายไปทำให้การจัดวางเปลี่ยนแปลงโดยไม่มีการแจ้งเตือน และวิธีเดียวที่จะรู้ว่าเกิดอะไรขึ้นคือการฟังสตรีมคำเตือนที่ Aspose.Words ส่งออก  

ในบทแนะนำนี้เราจะพาคุณผ่านตัวอย่างที่สมบูรณ์และพร้อมรันที่ **ตรวจจับฟอนต์ที่หายไป**, แสดงให้คุณ **วิธีตรวจจับฟอนต์ที่หายไป** ด้วยโปรแกรม, และยังให้เคล็ดลับสั้น ๆ เกี่ยวกับ **การจัดการฟอนต์ที่หายไป** เพื่อให้ผลลัพธ์ของคุณคาดเดาได้

> **หมายเหตุสั้น:** โค้ดทำงานกับ Aspose.Words 23.9 (หรือใหม่กว่า) และต้องการ Java 8+.

---

## สิ่งที่คุณต้องการ

- **Aspose.Words for Java** (การพึ่งพา Maven/Gradle หรือ JAR บน classpath)  
- ไฟล์ Word (`input.docx`) ที่อ้างอิงฟอนต์ที่ไม่ได้ติดตั้งในระบบของคุณ (เช่น “Comic Sans MS”)  
- IDE ของ Java หรือการตั้งค่า command line ง่าย ๆ ด้วย `javac`/`java`  

ไม่ต้องการไลบรารีอื่น—ทุกอย่างอื่นอยู่ภายในแพคเกจ Aspose.Words

---

## ขั้นตอนที่ 1 – ตั้งค่า LoadOptions เพื่อจับคำเตือน  

เพื่อเริ่มฟังคำเตือนคุณต้องสร้างอินสแตนซ์ของ `LoadOptions` วัตถุนี้บอกให้ตัวโหลดติดตามปัญหาที่พบ เช่น ฟอนต์ที่หายไป

```java
import com.aspose.words.*;

public class FontWarningDemo {
    public static void main(String[] args) throws Exception {

        // Step 1: Create LoadOptions that will store warning information
        LoadOptions loadOptions = new LoadOptions();

        // ... the rest of the code follows
```

**ทำไมเรื่องนี้ถึงสำคัญ:** หากไม่มี `LoadOptions` ตัวโหลดจะเปลี่ยนฟอนต์ที่หายไปเป็นฟอนต์ระบบเริ่มต้นโดยเงียบ ๆ และคุณจะไม่รู้ว่ามีการแทนที่เกิดขึ้น การเปิดใช้งานคำเตือนจะทำให้คุณเห็นภาพทั้งหมด

---

## ขั้นตอนที่ 2 – โหลดเอกสารโดยใช้ LoadOptions  

ตอนนี้เราจะโหลดเอกสารจริง ๆ `LoadOptions` ที่เราสร้างขึ้นจะถูกส่งไปยังคอนสตรัคเตอร์ ดังนั้นคำเตือนใด ๆ ที่เกิดขึ้นระหว่างการพาร์สจะถูกจับไว้

```java
        // Step 2: Load the document that may contain missing fonts
        Document document = new Document("YOUR_DIRECTORY/input.docx", loadOptions);
```

**เคล็ดลับมืออาชีพ:** หากคุณกำลังประมวลผลไฟล์หลายไฟล์เป็นชุด ให้ใช้อินสแตนซ์ `LoadOptions` เดียวกันซ้ำเพื่อหลีกเลี่ยงการสร้างอ็อบเจ็กต์ที่ไม่จำเป็น

---

## ขั้นตอนที่ 3 – วนลูปผ่านคำเตือนที่จับได้  

Aspose.Words เก็บคำเตือนแต่ละรายการเป็นอ็อบเจ็กต์ `WarningInfo` เราให้ความสนใจเฉพาะคำเตือนที่เกี่ยวกับฟอนต์เท่านั้น ดังนั้นเราจะกรองด้วย `FontSubstitutionWarningInfo`

```java
        // Step 3: Loop through all warnings generated while loading
        for (WarningInfo warning : document.getWarnings()) {
            // Step 3a: Keep only font substitution warnings
            if (warning instanceof FontSubstitutionWarningInfo) {
                FontSubstitutionWarningInfo fontWarning = (FontSubstitutionWarningInfo) warning;

                // Step 4: Output the requested and actual font names
                System.out.println("Requested: " + fontWarning.getRequestedFontName()
                        + " → Substituted: " + fontWarning.getActualFontName());
            }
        }
    }
}
```

**คำอธิบาย:**  
- `document.getWarnings()` คืนรายการของคำเตือนทั้งหมดที่เกิดขึ้นระหว่างการโหลด  
- `FontSubstitutionWarningInfo` มีข้อมูลสำคัญสองส่วน: **ฟอนต์ที่ร้องขอ** (ฟอนต์ที่ DOCX ต้องการ) และ **ฟอนต์ที่ใช้จริง** ที่ Aspose.Words ใช้แทน  
- โดยการพิมพ์ทั้งสองค่า คุณจะเห็นทันทีว่าฟอนต์ใดหายไปและมีการแทนที่อย่างไร

---

## ขั้นตอนที่ 4 – (ทางเลือก) จัดการฟอนต์ที่หายไปด้วยโปรแกรม  

การจับคำเตือนเป็นเพียงครึ่งหนึ่งของเรื่อง เมื่อคุณรู้ว่าฟอนต์หายไป คุณอาจต้องการ **จัดการฟอนต์ที่หายไป** โดยให้การแทนที่แบบกำหนดเองหรือบันทึกปัญหาเพื่อการตรวจสอบในภายหลัง

```java
                // Optional: Replace the missing font with a known fallback
                FontSettings fontSettings = new FontSettings();
                fontSettings.getSubstitutionSettings().getTableSubstitution()
                    .addSubstitutes(fontWarning.getRequestedFontName(), "Arial");
                document.setFontSettings(fontSettings);
```

**ทำไมต้องทำเช่นนี้?**  
- รับประกันการแสดงผลที่สม่ำเสมอระหว่างเครื่องต่าง ๆ  
- ป้องกันการเปลี่ยนแปลงการจัดวางที่ไม่คาดคิดใน PDF หรือรูปภาพที่สร้างต่อมา  

คุณยังสามารถเก็บรายละเอียดคำเตือนในฐานข้อมูล ส่งอีเมลไปยังทีมเนื้อหา หรือแม้กระทั่งยกเลิกกระบวนการหากฟอนต์สำคัญหายไป

---

## ตัวอย่างทำงานเต็มรูปแบบ  

ด้านล่างเป็นโปรแกรมที่สมบูรณ์และสามารถรันได้ เพียงแทนที่ `YOUR_DIRECTORY/input.docx` ด้วยพาธของไฟล์ทดสอบของคุณ เพิ่ม Aspose.Words JAR ไปยัง classpath แล้วรัน

```java
import com.aspose.words.*;

public class FontWarningDemo {
    public static void main(String[] args) throws Exception {

        // 1️⃣ Create LoadOptions to capture warnings
        LoadOptions loadOptions = new LoadOptions();

        // 2️⃣ Load the document that may contain missing fonts
        Document document = new Document("YOUR_DIRECTORY/input.docx", loadOptions);

        // 3️⃣ Iterate through all warnings
        for (WarningInfo warning : document.getWarnings()) {
            // 3a️⃣ Filter only font substitution warnings
            if (warning instanceof FontSubstitutionWarningInfo) {
                FontSubstitutionWarningInfo fontWarning = (FontSubstitutionWarningInfo) warning;

                // 4️⃣ Display the requested and actual font names
                System.out.println("Requested: " + fontWarning.getRequestedFontName()
                        + " → Substituted: " + fontWarning.getActualFontName());

                // 5️⃣ (Optional) Provide a custom fallback
                FontSettings fontSettings = new FontSettings();
                fontSettings.getSubstitutionSettings().getTableSubstitution()
                    .addSubstitutes(fontWarning.getRequestedFontName(), "Arial");
                document.setFontSettings(fontSettings);
            }
        }

        // 6️⃣ Save the document if you need to see the result with the fallback applied
        document.save("output.docx");
    }
}
```

**ผลลัพธ์ที่คาดหวัง** (เมื่อ “Comic Sans MS” หายไป):

```
Requested: Comic Sans MS → Substituted: Arial
```

หลังจากรหัส fallback ทางเลือกทำงาน ไฟล์ `output.docx` ที่บันทึกจะใช้ **Arial** ทุกที่ที่มีการอ้างอิง “Comic Sans MS” เดิม

---

## คำถามทั่วไป & กรณีขอบ  

| Question | Answer |
|----------|--------|
| *ถ้าเอกสารมีฟอนต์ที่หายไปหลายตัวล่ะ?* | ลูปจะส่งคำเตือนสำหรับแต่ละฟอนต์ คุณสามารถเก็บไว้ใน `Map<String, String>` เพื่อประมวลผลเป็นชุด |
| *วิธีนี้ทำงานกับ PDF ที่สร้างจากเอกสารหรือไม่?* | แน่นอน การแทนที่ฟอนต์เกิดขึ้นในขั้นตอนการโหลด ดังนั้นการส่งออกต่อม (PDF, HTML, image) จะใช้ฟอนต์ที่ได้แก้ไขแล้ว |
| *ฉันสามารถปิดการแสดงคำเตือนแทนการจับได้หรือไม่?* | ได้—ตั้งค่า `loadOptions.setWarningCallback(null);` แต่คุณจะสูญเสียการมองเห็นฟอนต์ที่หายไป |
| *รายการคำเตือนจะถูกล้างหลังจากบันทึกหรือไม่?* | คอลเลกชันคำเตือนเป็นของอินสแตนซ์ `Document` หลังจากเรียก `document.save()` รายการจะคงเดิมจนกว่าจะสร้าง `Document` ใหม่ |
| *ฟอนต์ที่กำหนดเองฝังใน DOCX จะเป็นอย่างไร?* | ฟอนต์ที่ฝังจะถือว่าใช้งานได้; Aspose.Words จะใช้ฟอนต์เหล่านั้นแม้ว่าจะไม่ได้ติดตั้งบนระบบโฮสต์ |

---

## เคล็ดลับระดับมืออาชีพสำหรับการใช้งานจริง  

- **Cache FontSettings:** หากคุณประมวลผลหลายร้อยไฟล์ สร้าง `FontSettings` เดียวที่มีการ fallback ที่คุณต้องการและใช้ซ้ำเพื่อหลีกเลี่ยงภาระ  
- **Log Structured Data:** แทนการใช้ `System.out` ธรรมดา ให้เขียนคำเตือนลงในล็อก JSON—ทำให้การวิเคราะห์ต่อเนื่อง (เช่น “ฟอนต์ที่หายไปมากที่สุด”) ง่ายดาย  
- **Validate Early:** รัน “dry‑load” อย่างรวดเร็วด้วย `LoadOptions` ก่อนการประมวลผลหนัก; ยกเลิกเร็วหากฟอนต์สำคัญหายไป  
- **Thread Safety:** อ็อบเจ็กต์ `Document` ไม่ปลอดภัยต่อการทำงานหลายเธรด เก็บการประมวลผลของแต่ละไฟล์ในเธรดของตนเองหรือใช้ `LoadOptions` แบบ thread‑local  

---

## สรุป  

ตอนนี้คุณรู้แล้วว่า **วิธีจับคำเตือน** ใน Aspose.Words สำหรับ Java, **ตรวจจับฟอนต์ที่หายไป**, และ **จัดการฟอนต์ที่หายไป** ด้วยกลยุทธ์ fallback ที่สะอาด ด้วยการใช้ `LoadOptions` และการวนลูป `document.getWarnings()` คุณจะได้ข้อมูลครบถ้วนเกี่ยวกับเหตุการณ์การแทนที่ฟอนต์ ทำให้เอกสารที่สร้างออกมาดูตรงตามที่ต้องการในทุกสภาพแวดล้อม  

พร้อมสำหรับขั้นตอนต่อไปหรือยัง? ลองขยายรูปแบบนี้เพื่อ **ตรวจจับรูปภาพที่หายไป**, **ติดตามฟีเจอร์ที่ไม่รองรับ**, หรือแม้กระทั่ง **ฝังฟอนต์ที่หายไปอัตโนมัติ** ลงในไฟล์ผลลัพธ์ วิธีการจับคำเตือนเดียวกันนี้ทำงานกับหลายสถานการณ์การประมวลผลเอกสาร ทำให้โค้ดของคุณทนทานและพร้อมสำหรับอนาคต  

ขอให้เขียนโค้ดอย่างสนุกสนาน และขอให้เอกสารของคุณแสดงผลอย่างสวยงามเสมอ!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}