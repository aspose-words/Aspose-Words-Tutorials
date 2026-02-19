---
category: general
date: 2026-02-18
description: สร้างตัวเลือกการโหลดใน Java เพื่อตรวจจับฟอนต์ที่หายไปและเรียนรู้วิธีโหลดไฟล์
  DOCX พร้อมคอลแบ็กคำเตือน
draft: false
keywords:
- create load options
- detect missing fonts
- how to load docx
- Aspose.Words warning callback
- Java document processing
language: th
og_description: สร้างตัวเลือกการโหลดใน Java เพื่อตรวจจับฟอนต์ที่หายไปและเรียนรู้วิธีการโหลดไฟล์
  DOCX พร้อมการเรียกกลับคำเตือน
og_title: สร้างตัวเลือกการโหลดใน Java – ตรวจจับฟอนต์ที่หายไปและวิธีโหลด DOCX
tags:
- java
- aspose-words
- document-processing
title: สร้างตัวเลือกการโหลดใน Java – ตรวจจับฟอนต์ที่หายไปและวิธีโหลด DOCX
url: /th/java/document-loading-and-saving/create-load-options-in-java-detect-missing-fonts-how-to-load/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# สร้าง Load Options ใน Java – ตรวจจับฟอนต์ที่หายไปและวิธีโหลด DOCX

เคยสงสัยไหมว่า **การสร้าง load options** ที่ไม่เพียงแค่อ่านไฟล์ DOCX แต่ยังบอกคุณเมื่อฟอนต์หายไป? คุณไม่ได้เป็นคนเดียว ฟอนต์ที่หายไปสามารถทำให้เอกสารที่จัดรูปแบบอย่างสมบูรณ์กลายเป็นข้อความที่อ่านไม่ออก และการจับได้ตั้งแต่แรกจะช่วยประหยัดเวลาการดีบักหลายชั่วโมง ในบทแนะนำนี้เราจะเดินผ่านขั้นตอนที่แน่นอนเพื่อ **ตรวจจับฟอนต์ที่หายไป** พร้อมแสดงให้คุณเห็น **วิธีโหลดไฟล์ DOCX** ด้วย callback คำเตือนที่กำหนดเอง

## สิ่งที่คุณจะได้เรียนรู้

- วิธีสร้าง `LoadOptions` และกำหนด warning handler  
- ทำไม warning callback ถึงสำคัญสำหรับการจับปัญหาการแทนที่ฟอนต์  
- โค้ดที่จำเป็นเพื่อ **โหลดไฟล์ DOCX** อย่างปลอดภัย พร้อมเคล็ดลับการใช้งานจริงสำหรับโปรเจกต์  
- การจัดการ edge‑case เช่น การจัดการกับประเภทคำเตือนอื่น ๆ หรือการโหลด PDF ด้วยวิธีเดียวกัน  

ไม่ต้องอ้างอิงเอกสารภายนอก—ทุกอย่างที่คุณต้องการอยู่ที่นี่

## ข้อกำหนดเบื้องต้น

- Java 17 หรือใหม่กว่า (API ทำงานบนเวอร์ชันเก่าได้ แต่ 17 เป็นจุดที่เหมาะที่สุด)  
- ไลบรารี Aspose.Words for Java ที่เพิ่มเข้าไปในโปรเจกต์ (`aspose-words-x.x.jar`)  
- ความเข้าใจพื้นฐานเกี่ยวกับการจัดการข้อยกเว้นใน Java  

ถ้าคุณมีสิ่งเหล่านี้แล้ว ไปต่อกันเลย

![Diagram showing the flow of creating load options, setting a warning callback, and loading a DOCX file](/images/create-load-options-diagram.png){: .center-image alt="Create Load Options flow diagram"}

## ขั้นตอนที่ 1: สร้าง Load Options (วิธีโหลด DOCX)

สิ่งแรกที่คุณต้องทำคือ **สร้าง load options** วัตถุนี้บอก Aspose.Words ว่าจะทำงานอย่างไรเมื่อเปิดไฟล์ คิดว่าเป็นชุดคำสั่งที่คุณส่งให้ไลบรารีก่อนที่มันจะเห็นไฟล์ DOCX

```java
// Step 1: Instantiate LoadOptions
LoadOptions loadOptions = new LoadOptions();
```

ทำไมไม่เรียก `new Document("file.docx")` ตรง ๆ? เพราะหากไม่มี `LoadOptions` คุณจะสูญเสียความสามารถในการตอบสนองต่อคำเตือน—เช่นฟอนต์ที่หายไป—จนกว่าเอกสารจะโหลดเสร็จแล้ว ซึ่งอาจช้าเกินไปสำหรับบาง workflow

## ขั้นตอนที่ 2: ตั้งค่า Warning Callback เพื่อตรวจจับฟอนต์ที่หายไป

ต่อไปเราจะผูก callback ที่จะถูกเรียกทุกครั้งที่ Aspose.Words พบสถานการณ์ที่ต้องการเตือนคุณ ในกรณีนี้เราต้องการตรวจจับ `WarningType.FONT_SUBSTITUTION`

```java
// Step 2: Register a warning callback
loadOptions.setWarningCallback(new IWarningCallback() {
    @Override
    public void warning(WarningInfo info) {
        // React only to font substitution warnings
        if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
            System.out.println("Missing font detected: " + info.getDescription());
        }
    }
});
```

ข้อควรจำบางประการ:

- **ทำไมต้องใช้ callback?** มันทำงาน *ระหว่าง* กระบวนการโหลด ให้คุณมีโอกาสบันทึกหรือแม้กระทั่งยกเลิกการทำงานก่อนที่เอกสารจะถูกสร้างเต็มรูปแบบ  
- **ทำไมต้องตรวจสอบ `WarningType.FONT_SUBSTITUTION`?** นี่คือค่า enum ที่ Aspose.Words ใช้สำหรับสถานการณ์ฟอนต์ที่หายไป ประเภทคำเตือนอื่น ๆ (เช่น `TABLE_STRUCTURE`) สามารถกรองได้ในลักษณะเดียวกันหากคุณต้องการ  
- **เคล็ดลับด้านประสิทธิภาพ:** Callback มีน้ำหนักเบา; หลีกเลี่ยง I/O หนัก ๆ ภายในมัน หากต้องเขียนไฟล์ให้จัดคิวข้อความและ flush หลังจากโหลดเสร็จ  

## ขั้นตอนที่ 3: โหลดไฟล์ DOCX ด้วย Options ที่กำหนดไว้

เมื่อ options และ callback พร้อมแล้ว คุณก็สามารถโหลดไฟล์ DOCX ได้ นี่คือส่วนที่ตอบ **วิธีโหลด docx** พร้อมเคารพคำเตือนที่คุณตั้งค่าไว้

```java
// Step 3: Load the document using the configured LoadOptions
try {
    Document document = new Document("YOUR_DIRECTORY/input.docx", loadOptions);
    System.out.println("Document loaded successfully.");
} catch (Exception e) {
    System.err.println("Failed to load document: " + e.getMessage());
}
```

**อะไรเกิดขึ้นเบื้องหลัง?** ขณะสตรีมไฟล์เข้ามา Aspose.Words ตรวจสอบแต่ละการอ้างอิงฟอนต์ หากฟอนต์ที่อ้างอิงไม่ได้ติดตั้ง จะเรียก warning callback ที่เรากำหนดไว้ก่อนหน้า คุณจะเห็นผลลัพธ์เช่น:

```
Missing font detected: Font 'Calibri' is not installed. Substituted with 'Arial'.
Document loaded successfully.
```

การตอบสนองทันทีนี้มีค่ามากเมื่อคุณต้องประมวลผลไฟล์จำนวนมากบนเซิร์ฟเวอร์

## ตัวอย่างทำงานเต็มรูปแบบ

รวมทุกอย่างเข้าด้วยกัน นี่คือโปรแกรมที่สามารถคัดลอก‑วางลงใน IDE ของคุณได้

```java
import com.aspose.words.*;

public class DetectMissingFonts {
    public static void main(String[] args) {
        // 1️⃣ Create LoadOptions
        LoadOptions loadOptions = new LoadOptions();

        // 2️⃣ Register warning callback to detect missing fonts
        loadOptions.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) {
                if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                    System.out.println("Missing font: " + info.getDescription());
                }
            }
        });

        // 3️⃣ Load the DOCX using the configured options
        try {
            Document doc = new Document("YOUR_DIRECTORY/input.docx", loadOptions);
            System.out.println("DOCX loaded – you can now work with it.");
        } catch (Exception ex) {
            System.err.println("Error loading DOCX: " + ex.getMessage());
        }
    }
}
```

**ผลลัพธ์ที่คาดหวัง**

```
Missing font: Font 'Times New Roman' is not installed. Substituted with 'Arial'.
DOCX loaded – you can now work with it.
```

หากไฟล์ไม่มีฟอนต์ที่หายไป callback จะเงียบและบรรทัด “DOCX loaded” จะปรากฏขึ้น

## เคล็ดลับระดับมืออาชีพ & Edge Cases

| สถานการณ์ | วิธีทำ |
|-----------|------------|
| **ฟอนต์หายหลายตัว** | Callback จะถูกเรียกสำหรับแต่ละฟอนต์ ดังนั้นคุณจะได้บรรทัดหนึ่งต่อฟอนต์ หากต้องการสรุปให้รวบรวมเป็น `List<String>` |
| **ต้องการจับคำเตือนอื่น ๆ ด้วย** | เพิ่มเงื่อนไข `else if` สำหรับ `WarningType.TABLE_STRUCTURE`, `WarningType.UNKNOWN_FILE_FORMAT` เป็นต้น |
| **โหลดไฟล์ DOCX ขนาดใหญ่** | ใช้ `LoadOptions.setLoadFormat(LoadFormat.DOCX)` เพื่อบอกรูปแบบและเร่งการตรวจจับ |
| **ทำงานในเว็บเซอร์วิส** | อย่าใช้ `System.out.println`; ให้ฉีด logger (`SLF4J`, `Log4j`) เข้าไปใน callback แทน |
| **ฟอนต์ถูกติดตั้งระหว่างรันไทม์** | หลังจากตรวจพบฟอนต์ที่หายไป คุณสามารถโหลดฟอนต์โดยโปรแกรมผ่าน `GraphicsEnvironment.registerFont(...)` แล้วโหลดเอกสารใหม่ |

## ทำไมวิธีนี้ดีกว่าวิธี “Try‑Catch เท่านั้น”

นักพัฒนาหลายคนเพียงแค่ห่อ `new Document(...)` ด้วย try‑catch หวังว่าข้อยกเว้นจะบอกฟอนต์ที่หายไป แต่ Aspose.Words ถือการแทนที่ฟอนต์เป็น *คำเตือน* ไม่ใช่ข้อผิดพลาด ดังนั้นจึงไม่มี exception เกิดขึ้น การ **สร้าง load options** แล้วผูก warning callback ทำให้คุณได้ข้อมูลเชิงกำหนดเวลาที่แน่นอนเกี่ยวกับปัญหาฟอนต์โดยไม่เสียประสิทธิภาพ

## ขั้นตอนต่อไป

- **ตรวจจับฟอนต์ที่หายไปใน PDF** – รูปแบบ `LoadOptions` เดียวกันทำงานกับ PDF เพียงเปลี่ยนเส้นทางไฟล์และรูปแบบการโหลด  
- **อัตโนมัติการติดตั้งฟอนต์** – ผสาน callback กับสคริปต์ที่ดึงฟอนต์ที่หายไปจากคลังร่วม  
- **สำรวจประเภทคำเตือนอื่น ๆ** – Aspose.Words สามารถแจ้งคุณเกี่ยวกับแท็กที่ล้าสมัย ตารางซับซ้อน ฯลฯ  

ลองปรับใช้: เปลี่ยนคอนสตรัคเตอร์ `Document` เป็นสตรีม (`new Document(InputStream, loadOptions)`) หากคุณทำงานกับข้อมูลในหน่วยความจำ หรือเชื่อมต่อหลาย callback ด้วย pattern composite สำหรับ pipeline การประมวลผลขนาดใหญ่

---

### TL;DR

เราได้แสดงวิธี **สร้าง load options** ใน Java ตั้งค่า callback ที่ **ตรวจจับฟอนต์ที่หายไป** และสุดท้าย **โหลดไฟล์ DOCX** อย่างปลอดภัย ด้วยเพียงสามขั้นตอนสั้น ๆ คุณจะได้แพทเทิร์นที่นำกลับมาใช้ได้ในโปรเจกต์ Aspose.Words ใด ๆ

มีคำถามเกี่ยวกับรูปแบบไฟล์อื่นหรืออยากให้ช่วยปรับ callback ให้เหมาะกับสภาพแวดล้อมของคุณ? แสดงความคิดเห็นด้านล่าง แล้วขอให้สนุกกับการเขียนโค้ด!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}