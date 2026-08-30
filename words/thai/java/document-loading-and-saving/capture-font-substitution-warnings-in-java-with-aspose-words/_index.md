---
category: general
date: 2026-06-27
description: เรียนรู้วิธีดักจับคำเตือนการแทนที่ฟอนต์ใน Java ด้วย Aspose.Words บทเรียนทีละขั้นตอนนี้ยังครอบคลุมการใช้
  callback คำเตือนและการใช้ LoadOptions ด้วย
draft: false
keywords:
- capture font substitution warnings
- Aspose.Words warning callback
- Java LoadOptions example
- font substitution handling
- document processing with Aspose
language: th
og_description: บันทึกคำเตือนการแทนที่ฟอนต์ใน Java ด้วย Aspose.Words ปฏิบัติตามคำแนะนำนี้เพื่อกำหนดการเรียกคืนคำเตือน
  ใช้ LoadOptions และจัดการกับฟอนต์ที่หายไป
og_title: บันทึกคำเตือนการแทนที่ฟอนต์ใน Java – บทเรียน Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-06-27'
  description: Learn how to capture font substitution warnings in Java using Aspose.Words.
    This step‑by‑step tutorial also covers warning callbacks and LoadOptions usage.
  headline: Capture Font Substitution Warnings in Java with Aspose.Words – Complete
    Guide
  type: TechArticle
- questions:
  - answer: Yes. The warning callback is format‑agnostic; it fires for any document
      type that Aspose.Words loads (DOC, DOCX, RTF, HTML, etc.). The only difference
      is the set of warnings that may appear.
    question: Does this work with PDF or other formats?
  - answer: Absolutely. Inside the `warning` method, inspect `info.getWarningType()`
      for other enum values such as `WarningType.IMAGE_RESOLUTION`. Then handle them
      accordingly.
    question: Can I capture other warning types, like *image resolution* warnings?
  - answer: 'Store each `info.getDescription()` in a `List<String>` inside the callback.
      After loading, you’ll have a collection you can log, send to a monitoring service,
      or use to trigger a font‑download routine. ## Conclusion You now know **how
      to capture font substitution warnings** in Java using Aspose.Word'
    question: What if I need the list of substituted fonts after the document loads?
  type: FAQPage
tags:
- Aspose.Words
- Java
- Document Conversion
title: จับคำเตือนการแทนที่ฟอนต์ใน Java ด้วย Aspose.Words – คู่มือฉบับสมบูรณ์
url: /th/java/document-loading-and-saving/capture-font-substitution-warnings-in-java-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# จับคำเตือนการแทนที่ฟอนต์ใน Java ด้วย Aspose.Words – คู่มือฉบับสมบูรณ์

เคยต้อง **จับคำเตือนการแทนที่ฟอนต์** ขณะโหลดไฟล์ DOCX ที่ใช้ฟอนต์แปลกใหม่หรือไม่? คุณไม่ได้เป็นคนเดียว ในหลายโครงการจริง—เช่น ตัวสร้างรายงานอัตโนมัติหรือเครื่องแปลงเอกสารเป็นชุด—ฟอนต์ที่หายไปจะทำให้เกิดการแทนที่โดยเงียบ ๆ ซึ่งอาจทำให้การจัดวางหน้าตาเสียหายได้  

โชคดีที่ Aspose.Words มีวิธีที่สะอาดตาในการฟังคำเตือนเหล่านั้น ในบทแนะนำนี้เราจะพาคุณผ่านการกำหนดค่า **LoadOptions**, การเชื่อมต่อ **Aspose.Words warning callback**, และการพิมพ์ข้อความ *การแทนที่ฟอนต์* ทุกข้อความไปยังคอนโซล เมื่อจบคุณจะรู้ว่าเมื่อใดฟอนต์ถูกสลับและจะตอบสนองอย่างไรในระดับโค้ด

> **สิ่งที่คุณจะได้:** ตัวอย่างโค้ด Java ที่รันได้เต็มรูปแบบ, คำอธิบายว่า *ทำไม* แต่ละส่วนจึงสำคัญ, และเคล็ดลับการจัดการกรณีขอบเช่นโฟลเดอร์ฟอนต์แบบกำหนดเอง

## ข้อกำหนดเบื้องต้น & สิ่งที่คุณต้องมี

ก่อนที่เราจะลงลึก ให้ตรวจสอบว่าคุณมี:

- Java 8 หรือใหม่กว่า (โค้ดทำงานได้กับ Java 11+ ด้วย)
- JAR ของ Aspose.Words for Java รุ่นล่าสุด (ดาวน์โหลดจากเว็บไซต์ทางการหรือ Maven Central)
- ไฟล์ DOCX ที่อ้างอิงฟอนต์ที่ไม่ได้ติดตั้งบนเครื่องของคุณ (เช่น *font‑rich.docx* ที่พบในชุดตัวอย่างของ Aspose)
- IDE ที่ใช้งานได้ดี (IntelliJ IDEA, Eclipse หรือแม้แต่ VS Code พร้อมส่วนขยาย Java)

ไม่ต้องใช้ไลบรารีภายนอกนอกจาก Aspose.Words และตัวอย่างทำงานในเมธอด `main` ธรรมดา

## ขั้นตอนที่ 1: ตั้งค่า LoadOptions – จุดเริ่มต้นสำหรับการโหลดแบบกำหนดเอง

`LoadOptions` คือถุงกำหนดค่าของ Aspose.Words ที่บอกไลบรารีว่า *จะอ่านเอกสารอย่างไร* โดยค่าเริ่มต้นมันจะทำการแทนที่ฟอนต์ที่หายไปโดยเงียบ ๆ แต่คุณสามารถเปลี่ยนพฤติกรรมนั้นด้วย callback คำเตือนได้

```java
import com.aspose.words.*;

public class FontWarningDemo {
    public static void main(String[] args) throws Exception {

        // Step 1: Create LoadOptions to customize loading behavior
        LoadOptions loadOptions = new LoadOptions();
```

**ทำไมเรื่องนี้สำคัญ:** หากไม่มี `LoadOptions` เอกสารจะโหลดแบบเงียบและคุณจะไม่เห็นฟอนต์ที่หายไป การสร้างอินสแตนซ์ทำให้คุณได้ hook สำหรับระบบคำเตือน

## ขั้นตอนที่ 2: กำหนด Warning Callback เพื่อ *จับคำเตือนการแทนที่ฟอนต์*

Aspose.Words ส่งเหตุการณ์คำเตือนผ่านอินเทอร์เฟซ `IWarningCallback` Implement มันแบบอินไลน์ (หรือเป็นคลาสแยก) แล้วกรองเฉพาะ `WarningType.FONT_SUBSTITUTION`

```java
        // Step 2: Define a warning callback to capture font substitution warnings
        loadOptions.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) {
                // Only react to font substitution warnings
                if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                    System.out.println("Font substituted: " + info.getDescription());
                }
            }
        });
```

**คำอธิบาย:**  
- `info.getWarningType()` ให้ประเภทของคำเตือน  
- `WarningType.FONT_SUBSTITUTION` คือค่า enum ที่เราต้องการ  
- `info.getDescription()` มีข้อความที่คนอ่านได้ เช่น *“Font 'Comic Sans MS' not found, substituted with 'Arial'.”*  

โดยการพิมพ์ description คุณ **จับคำเตือนการแทนที่ฟอนต์** ได้แบบเรียลไทม์

## ขั้นตอนที่ 3: โหลดเอกสารโดยใช้ LoadOptions ที่กำหนดไว้

เมื่อ callback ถูกตั้งค่าแล้ว ให้โหลดไฟล์ DOCX ของคุณ คำเตือนจะถูกเรียกอัตโนมัติระหว่างการพาร์ส

```java
        // Step 3: Load the document using the configured LoadOptions
        Document document = new Document("YOUR_DIRECTORY/font-rich.docx", loadOptions);
```

แทนที่ `YOUR_DIRECTORY` ด้วยพาธจริงของไฟล์ทดสอบของคุณ เมื่อคอนสตรัคเตอร์ `Document` ทำงาน ฟอนต์ใดที่หายไปจะทำให้ callback ที่กำหนดไว้ก่อนหน้านี้ทำงานและคุณจะเห็นข้อความแทนที่บนคอนโซล

## ขั้นตอนที่ 4: ตรวจสอบเอกสารที่โหลดแล้ว (ไม่บังคับแต่แนะนำ)

หลังจากโหลดแล้ว คุณอาจต้องการยืนยันความสมบูรณ์ของเอกสาร—เช่น จำนวนหน้า, การสกัดข้อความ ฯลฯ ขั้นตอนนี้ไม่จำเป็นสำหรับการจับคำเตือน แต่ช่วยให้คุณเห็นผลของการแทนที่ได้ชัดเจนขึ้น

```java
        // Optional: Output basic document info
        System.out.println("Document loaded successfully.");
        System.out.println("Page count: " + document.getPageCount());
```

หากฟอนต์ถูกแทนที่ การจัดวางอาจเลื่อนเล็กน้อย; การตรวจสอบจำนวนหน้าอาจเปิดเผยการเปลี่ยนแปลงเหล่านั้น

## ขั้นตอนที่ 5: ขั้นสูง – จัดการฟอนต์ที่ถูกแทนที่ด้วยโปรแกรม

บางครั้งคุณไม่ต้องการเพียงบันทึกคำเตือน—คุณอาจต้องฝังฟอนต์สำรองหรือปรับสไตล์ ด้านล่างเป็นแพทเทิร์นสั้น ๆ ที่คุณสามารถนำไปใช้ได้

```java
        // Advanced: Register a fallback font folder to reduce substitutions
        FontSettings fontSettings = new FontSettings();
        // Point to a folder that contains the missing fonts
        fontSettings.setFontsFolder("YOUR_DIRECTORY/custom-fonts", true);
        loadOptions.setFontSettings(fontSettings);
```

โดยการชี้ Aspose.Words ไปยังโฟลเดอร์ที่มีฟอนต์ต้นฉบับ คุณสามารถ *ป้องกัน* การแทนที่ได้ทั้งหมด หากโฟลเดอร์หายไป callback ยังจับเหตุการณ์และให้กลยุทธ์สำรอง

## ตัวอย่างทำงานเต็มรูปแบบ

รวมทุกอย่างเข้าด้วยกัน นี่คือโปรแกรมที่พร้อมรัน:

```java
import com.aspose.words.*;

public class FontWarningDemo {
    public static void main(String[] args) throws Exception {

        // Initialize LoadOptions
        LoadOptions loadOptions = new LoadOptions();

        // Set up warning callback to capture font substitution warnings
        loadOptions.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) {
                if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                    System.out.println("Font substituted: " + info.getDescription());
                }
            }
        });

        // OPTIONAL: Register a custom fonts folder to avoid substitution
        FontSettings fontSettings = new FontSettings();
        fontSettings.setFontsFolder("YOUR_DIRECTORY/custom-fonts", true);
        loadOptions.setFontSettings(fontSettings);

        // Load the document – warnings will be printed automatically
        Document doc = new Document("YOUR_DIRECTORY/font-rich.docx", loadOptions);

        // Verify basic info
        System.out.println("Document loaded successfully.");
        System.out.println("Page count: " + doc.getPageCount());
    }
}
```

**ผลลัพธ์ที่คาดว่าจะเห็นบนคอนโซล** (เมื่อพบฟอนต์ที่หายไป):

```
Font substituted: Font 'Pacifico' not found, substituted with 'Arial'.
Document loaded successfully.
Page count: 3
```

หากฟอนต์ทั้งหมดมีอยู่ callback จะเงียบ—ไม่มีอะไรพิมพ์ออกมา ซึ่งเป็นพฤติกรรมที่คาดหวัง

## ข้อผิดพลาดทั่วไป & เคล็ดลับระดับมืออาชีพ

| ข้อผิดพลาด | สาเหตุ | วิธีแก้ |
|------------|--------|--------|
| **Callback ไม่ทำงาน** | คุณลืมเชื่อม callback กับ `LoadOptions` **หรือ** ใช้คอนสตรัคเตอร์เริ่มต้นของ `Document` โดยไม่ส่ง `loadOptions` | ต้องเรียก `loadOptions.setWarningCallback(...)` **และ** ใช้ overload `new Document(path, loadOptions)` |
| **คำเตือนเยอะเกินไปทำให้ล็อกเกลือ** | เอกสารขนาดใหญ่ที่มีฟอนต์หายหลายตัวสร้างคำเตือนต่อการแทนที่หนึ่งครั้ง | กรองต่อโดยตรวจสอบ `info.getDescription()` สำหรับชื่อฟอนต์เฉพาะ, หรือเก็บคำเตือนใน List เพื่อประมวลผลภายหลัง |
| **ฟอนต์ที่แทนที่ทำให้เลย์เอาต์เปลี่ยน** | ฟอนต์สำรองอาจมีเมตริกต่างกัน (ขนาด, ระยะห่าง) | ให้โฟลเดอร์ฟอนต์แบบกำหนดเอง (ดูขั้นตอน 5) หรือปรับสไตล์ของเอกสารหลังโหลด |
| **รันบนเซิร์ฟเวอร์แบบ headless** | ฟอนต์สำรองเริ่มต้นอาจอ้างอิงฟอนต์ระบบที่ไม่ได้ติดตั้งบนเซิร์ฟเวอร์ | แพ็คฟอนต์ที่ต้องการกับแอปและชี้ `FontSettings` ไปยังโฟลเดอร์นั้น |

## คำถามที่พบบ่อย

**ถาม: วิธีนี้ทำงานกับ PDF หรือฟอร์แมตอื่นได้หรือไม่?**  
ตอบ: ได้. callback คำเตือนเป็นแบบไม่ขึ้นกับฟอร์แมต; มันทำงานกับทุกประเภทเอกสารที่ Aspose.Words โหลด (DOC, DOCX, RTF, HTML ฯลฯ) ความแตกต่างเดียวคือชุดคำเตือนที่อาจปรากฏ

**ถาม: ฉันสามารถจับประเภทคำเตือนอื่น ๆ เช่น คำเตือนความละเอียดของรูปภาพได้หรือไม่?**  
ตอบ: แน่นอน. ภายในเมธอด `warning` ตรวจสอบ `info.getWarningType()` สำหรับค่า enum อื่น ๆ เช่น `WarningType.IMAGE_RESOLUTION` แล้วจัดการตามต้องการ

**ถาม: ถ้าฉันต้องการรายการฟอนต์ที่ถูกแทนที่หลังโหลดเอกสารแล้วทำอย่างไร?**  
ตอบ: เก็บ `info.getDescription()` แต่ละรายการใน `List<String>` ภายใน callback หลังโหลดเสร็จคุณจะมีคอลเลกชันที่สามารถบันทึก, ส่งไปยังบริการมอนิเตอร์, หรือใช้เพื่อเรียกกระบวนการดาวน์โหลดฟอนต์ได้

## สรุป

คุณได้เรียนรู้ **วิธีจับคำเตือนการแทนที่ฟอนต์** ใน Java ด้วย Aspose.Words, ทำไมแต่ละส่วนจึงสำคัญ, และวิธีขยายโซลูชันสำหรับสถานการณ์จริง โดยใช้ `LoadOptions`, `Aspose.Words warning callback` และ `FontSettings` ตัวเลือกเสริม คุณจะได้มองเห็นฟอนต์ที่หายไปทั้งหมดและทำให้สายการแปลงเอกสารของคุณเชื่อถือได้มากขึ้น  

พร้อมก้าวต่อไปหรือยัง? ลองเปลี่ยน `System.out.println` เป็น logger อย่าง SLF4J, หรือผสานรายการคำเตือนเข้ากับ UI ที่แจ้งผู้ใช้ก่อนทำการแปลงเป็นชุด คุณยังสามารถสำรวจ **Aspose.Words warning callback** สำหรับประเภทคำเตือนอื่น ๆ เช่น *ฟีเจอร์ที่ไม่รองรับ* หรือ *การแจ้งเตือนรูปภาพความละเอียดสูง*  

ขอให้เขียนโค้ดสนุกและ PDF ของคุณไม่มีการสลับฟอนต์โดยไม่คาดคิดอีกต่อไป!  

![ภาพหน้าจอแสดงผลลัพธ์ของคอนโซลที่จับคำเตือนการแทนที่ฟอนต์](image-placeholder.png "จับคำเตือนการแทนที่ฟอนต์")

## คุณควรเรียนรู้อะไรต่อไป?

บทแนะนำต่อไปนี้ครอบคลุมหัวข้อที่เกี่ยวข้องอย่างใกล้ชิดและต่อยอดจากเทคนิคที่แสดงในคู่มือนี้ แต่ละแหล่งรวมตัวอย่างโค้ดทำงานเต็มรูปแบบพร้อมคำอธิบายทีละขั้นตอน เพื่อช่วยให้คุณเชี่ยวชาญฟีเจอร์ API เพิ่มเติมและสำรวจแนวทางการนำไปใช้ในโครงการของคุณเอง

- [Enable Font Substitution Warnings in Aspose.Words – Complete Guide](/words/english/net/working-with-fonts/enable-font-substitution-warnings-in-aspose-words-complete-g/)
- [How to Set LoadOptions in Aspose.Words for Java](/words/english/java/document-loading-and-saving/using-load-options/)
- [How to Create PDF Documents with Aspose.Words for Java | Document Processing API](/words/english/java/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}