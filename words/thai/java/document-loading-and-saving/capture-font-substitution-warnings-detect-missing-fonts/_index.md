---
category: general
date: 2026-04-04
description: บันทึกคำเตือนการแทนที่ฟอนต์ขณะโหลดเอกสาร Word ด้วย Aspose.Words for Java
  และตรวจจับฟอนต์ที่หายไปโดยอัตโนมัติ ทำตามคู่มือขั้นตอนต่อขั้นตอนนี้
draft: false
keywords:
- capture font substitution warnings
- detect missing fonts
language: th
og_description: บันทึกคำเตือนการแทนที่ฟอนต์ขณะโหลดเอกสาร Word ด้วย Aspose.Words for
  Java และตรวจจับฟอนต์ที่หายไปในไม่กี่ขั้นตอนง่าย ๆ.
og_title: บันทึกคำเตือนการแทนที่ฟอนต์ – ตรวจจับฟอนต์ที่หายไป
tags:
- Aspose.Words
- Java
- Document Processing
title: บันทึกคำเตือนการแทนที่ฟอนต์ – ตรวจจับฟอนต์ที่หายไป
url: /th/java/document-loading-and-saving/capture-font-substitution-warnings-detect-missing-fonts/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# บันทึกคำเตือนการแทนที่ฟอนต์ – ตรวจจับฟอนต์ที่หายไป

เคยต้องการ **บันทึกคำเตือนการแทนที่ฟอนต์** ขณะเปิดไฟล์ Word แล้วพบว่าฟอนต์สำคัญหายไปหรือไม่? คุณไม่ได้เป็นคนเดียว ในหลายกระบวนการทำงานขององค์กร ฟอนต์ที่หายไปสามารถทำให้รายงานที่จัดรูปแบบอย่างสมบูรณ์กลายเป็นข้อความยุ่งเหยิง และสัญญาณเดียวที่คุณได้รับคือคำเตือนเงียบที่นักพัฒนาส่วนใหญ่ไม่เคยเห็น

ข่าวดีคือ Aspose.Words for Java ให้คุณเชื่อมต่อกับกระบวนการโหลดและ **ตรวจจับฟอนต์ที่หายไป** ก่อนที่มันจะทำปัญหาในภายหลัง ในบทแนะนำนี้เราจะพาคุณผ่านตัวอย่างที่สมบูรณ์และสามารถรันได้ซึ่งพิมพ์คำเตือนการแทนที่ทุกอย่างตรงไปยังคอนโซล เพื่อให้คุณสามารถตัดสินใจว่าจะฝังฟอนต์ที่ถูกต้อง, แทนที่มัน, หรือแจ้งผู้ใช้

เมื่อจบคู่มือคุณจะรู้วิธี:

* ตั้งค่าอ็อบเจ็กต์ `LoadOptions` พร้อมกับ callback คำเตือนแบบกำหนดเอง
* กรอง callback ให้ตอบสนองต่อเหตุการณ์การแทนที่ฟอนต์เท่านั้น
* โหลดไฟล์ `.docx` ใดก็ได้และดูคำเตือนทันที
* ขยายโซลูชันเพื่อบันทึกคำเตือน, โยนข้อยกเว้น, หรือแม้กระทั่งติดตั้งฟอนต์ที่หายไปอัตโนมัติ

ไม่ต้องอ้างอิงเอกสารภายนอก—แค่บรรทัดโค้ด Java ไม่กี่บรรทัดและ Aspose.Words JAR

## ข้อกำหนดเบื้องต้น

ก่อนที่เราจะลงลึก โปรดตรวจสอบว่าคุณมี:

* Java 8 หรือใหม่กว่า (เวอร์ชัน LTS ล่าสุดทำงานได้ดีที่สุด)
* Aspose.Words for Java 23.11 หรือใหม่กว่า – คุณสามารถดึง Maven artifact หรือ JAR ธรรมดาจากเว็บไซต์ Aspose
* เอกสาร Word ที่อ้างอิงฟอนต์ที่คุณไม่มีในเครื่องพัฒนา (เช่น “MyFancyFont”)  
* IDE หรือโปรแกรมแก้ไขข้อความที่คุณชอบ – ฉันใช้ IntelliJ IDEA แต่ Eclipse หรือ VS Code ก็ใช้ได้ดี

หากรายการใดฟังดูไม่คุ้นเคย ให้หยุดและติดตั้งก่อน; ส่วนที่เหลือของบทแนะนำถือว่าพร้อมใช้งานแล้ว

---

## บันทึกคำเตือนการแทนที่ฟอนต์โดยใช้ Aspose.Words

แกนหลักของโซลูชันอยู่ในอินสแตนซ์ `LoadOptions` โดยการกำหนด `IWarningCallback` เราสามารถดักจับคำเตือนทุกอย่างที่ไลบรารีส่งออกในช่วงการโหลดได้

```java
import com.aspose.words.*;

public class FontDiagnosticsTutorial {
    public static void main(String[] args) throws Exception {

        // Step 1️⃣: Create LoadOptions and set a warning callback.
        LoadOptions loadOptions = new LoadOptions();
        loadOptions.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) {
                // Capture only font substitution warnings.
                if (info.getWarningType() == WarningType.SUBSTITUTED_FONT) {
                    System.out.println("Font substitution: " + info.getDescription());
                }
            }
        });

        // Step 2️⃣: Load the document. The callback runs automatically.
        Document doc = new Document("YOUR_DIRECTORY/document-with-missing-font.docx", loadOptions);

        // Step 3️⃣: If you reach this line, the document is loaded.
        // Any missing‑font warnings have already been printed to the console.
        System.out.println("Document loaded successfully.");
    }
}
```

**ทำไมวิธีนี้ถึงได้ผล:**  
`LoadOptions` บอก Aspose.Words ว่าจะจัดการไฟล์เข้ามาอย่างไร อินเทอร์เฟซ `IWarningCallback` เป็น hook ที่รับอ็อบเจ็กต์ `WarningInfo` สำหรับ *ทุก* คำเตือน โดยตรวจสอบ `info.getWarningType()` เราจะกรองทุกอย่างออกยกเว้น `SUBSTITUTED_FONT` คุณสมบัติ `description` มีข้อความที่คนอ่านเข้าใจได้ เช่น “Font 'MyFancyFont' was substituted with 'Arial'”

### ผลลัพธ์ที่คาดว่าจะเห็นในคอนโซล

หากเอกสารต้นทางอ้างอิงฟอนต์ที่ไม่ได้ติดตั้ง คุณจะเห็นอย่างนี้:

```
Font substitution: Font 'MyFancyFont' was substituted with 'Arial'.
Document loaded successfully.
```

หากเอกสารใช้ฟอนต์ที่มีอยู่บนเครื่อง callback จะเงียบและคุณจะเห็นเพียงบรรทัดสุดท้าย “Document loaded successfully.”

---

## ตรวจจับฟอนต์ที่หายไปในเอกสารของคุณ

คุณอาจสงสัยว่า *“คำเตือนการแทนที่เป็นเหมือนฟอนต์ที่หายไปหรือไม่?”* ในหลายกรณี คำตอบคือใช่—Aspose.Words แทนที่ฟอนต์ที่หายไปด้วยฟอนต์สำรองและรายงานผ่าน `SUBSTITUTED_FONT` อย่างไรก็ตาม มีกรณีขอบที่ฟอนต์มีอยู่แต่สไตล์ที่แน่นอน (เช่น bold‑italic, ฟีเจอร์ OpenType เฉพาะ) ไม่มี ทำให้เกิดการแทนที่อย่างละเอียดอ่อน

เพื่อให้แน่ใจว่าคุณจับทุกช่องว่างได้ คุณสามารถผสาน callback คำเตือนกับการตรวจสอบหลังการโหลดได้ดังนี้:

```java
// After loading the document, iterate through all runs.
for (Paragraph para : (Iterable<Paragraph>) doc.getFirstSection().getBody().getChildNodes(NodeType.PARAGRAPH, true)) {
    for (Run run : (Iterable<Run>) para.getChildNodes(NodeType.RUN, true)) {
        Font font = run.getFont();
        if (font.getName().equalsIgnoreCase("MyFancyFont")) {
            System.out.println("Run still uses the missing font: " + font.getName());
        }
    }
}
```

**เคล็ดลับ:** หากคุณพบ run ใดที่ยังอ้างอิงฟอนต์ที่หายไป คุณสามารถแทนที่ได้ทันที:

```java
font.setName("Arial"); // fallback
```

วิธีนี้จะทำให้ผลลัพธ์ภาพที่สอดคล้องกัน แม้คำเตือนเดิมจะถูกซ่อน

---

## ข้อผิดพลาดทั่วไป & วิธีหลีกเลี่ยง

| ข้อผิดพลาด | สาเหตุ | วิธีแก้ |
|------------|--------|--------|
| **ลืมตั้งค่า callback** | `LoadOptions` มีค่าเริ่มต้นเป็น callback ที่ไม่ทำอะไร ทำให้คำเตือนหายไป | ควรเรียก `loadOptions.setWarningCallback(...)` ก่อนทำการโหลดเสมอ |
| **ใช้ประเภทคำเตือนผิด** | `WarningType.SUBSTITUTED_FONT` เป็น enum เดียวที่บ่งบอกฟอนต์ที่หายไป | กรองเฉพาะ `WarningType.SUBSTITUTED_FONT` *เท่านั้น*; ประเภทอื่น (เช่น `UNKNOWN_FILE_FORMAT`) ไม่เกี่ยวข้อง |
| **กำหนดค่าไฟล์แบบฮาร์ดโค้ด** | ทำงานในเครื่องท้องถิ่นแต่ล้มเหลวใน pipeline CI/CD | ใช้เส้นทางแบบ relative หรือรับตำแหน่งไฟล์เป็นอาร์กิวเมนต์บรรทัดคำสั่ง |
| **ละเลยฟอนต์ Unicode** | ฟอนต์ที่หายไปบางตัวอาจส่งผลต่ออักขระบางชุดเท่านั้น | ทดสอบด้วยเอกสารที่มีชุดอักขระเต็มที่คุณคาดว่าจะสนับสนุน |
| **รันบนเซิร์ฟเวอร์ headless ที่ไม่มีการตั้งค่าฟอนต์** | เซิร์ฟเวอร์อาจไม่มีฟอนต์สำรองใด ๆ ทำให้เกิดการแทนที่ที่ไม่คาดคิด | ติดตั้งชุดฟอนต์พื้นฐาน (Arial, Times New Roman) บนเซิร์ฟเวอร์ |

---

## ขยายโซลูชัน

ตอนนี้คุณสามารถ **บันทึกคำเตือนการแทนที่ฟอนต์** แล้ว คุณอาจต้องการ:

* **บันทึกคำเตือนลงไฟล์** – แทนที่ `System.out.println` ด้วย logger เช่น SLF4J
* **โยนข้อยกเว้น** – มีประโยชน์ใน pipeline อัตโนมัติที่ฟอนต์ที่หายไปควรทำให้การสร้างล้มเหลว:

```java
if (info.getWarningType() == WarningType.SUBSTITUTED_FONT) {
    throw new RuntimeException("Missing font detected: " + info.getDescription());
}
```

* **ติดตั้งฟอนต์ที่หายไปอัตโนมัติ** – ดาวน์โหลดไฟล์ TTF/OTF ที่ต้องการขณะรันและเพิ่มเข้าไปใน `GraphicsEnvironment` ของ Java นั่นเป็นสถานการณ์ขั้นสูง แต่ทำได้เต็มที่

---

## Diagram (optional)

![Capture font substitution warnings flow diagram showing LoadOptions → WarningCallback → Console output](capture-font-substitution-warnings-diagram.png)

*Alt text:* “แผนภาพการไหลของการบันทึกคำเตือนการแทนที่ฟอนต์ แสดงวิธีที่ Aspose.Words ส่งคำเตือนฟอนต์ที่หายไปไปยัง callback ที่กำหนดเอง”

---

## สรุป

เราได้อธิบายวิธี **บันทึกคำเตือนการแทนที่ฟอนต์** และ **ตรวจจับฟอนต์ที่หายไป** ขณะโหลดเอกสาร Word ด้วย Aspose.Words for Java โดยการกำหนดอ็อบเจ็กต์ `LoadOptions` และทำการ implement `IWarningCallback` ขนาดเล็ก คุณจะได้มองเห็นกระบวนการ fallback ของฟอนต์อย่างเต็มที่ ทำให้สามารถบันทึก, แทนที่ หรือยกเลิกการทำงานเมื่อพบฟอนต์ที่หายไป

สรุปสั้น ๆ: ตั้งค่า callback, กรอง `SUBSTITUTED_FONT`, โหลดเอกสาร, แล้วจัดการผลลัพธ์ตามที่แอปพลิเคชันของคุณต้องการ จากนี้คุณสามารถขยายไปยังเฟรมเวิร์กการบันทึก, ตรวจสอบ CI, หรือแม้กระทั่งการจัดหาฟอนต์อัตโนมัติ

อยากทำต่อ? ลอง:

* **ฝังฟอนต์** ลงในเอกสารที่บันทึก (`doc.save(..., SaveOptions.createSaveOptions(SaveFormat.DOCX))` พร้อม `FontEmbeddingMode.EMBED_ALL`)
* **สร้าง PDF** หลังจากแก้ฟอนต์แล้ว เพื่อให้ผลลัพธ์สุดท้ายดูเหมือนต้นฉบับอย่างแม่นยำ
* **สแกนโฟลเดอร์ทั้งหมด** ของเอกสารเพื่อค้นหาฟอนต์ที่หายไปและสร้างรายงานสรุป

เท่านี้ก็พอสำหรับตอนนี้—ขอให้เขียนโค้ดสนุกและเอกสารของคุณแสดงผลด้วยฟอนต์ที่ถูกต้องเสมอ!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}