---
category: general
date: 2026-02-15
description: โหมดการกู้คืนช่วยให้คุณโหลดเอกสารพร้อมการกู้คืน ทำให้การกู้คืนเอกสาร
  Word ที่เสียหายและการแก้ไขข้อผิดพลาดการกู้คืนเอกสาร Word เป็นเรื่องง่าย.
draft: false
keywords:
- set recovery mode
- recover broken word document
- load document with recovery
- recover word document errors
language: th
og_description: การตั้งค่าโหมดการกู้คืนเป็นกุญแจสำคัญในการโหลดเอกสารพร้อมการกู้คืน
  ทำให้คุณสามารถกู้ข้อผิดพลาดของเอกสาร Word ที่เสียหายใน Java ได้
og_title: ตั้งโหมดการกู้คืน – กู้คืนเอกสาร Word ที่เสียหายอย่างรวดเร็ว
tags:
- Aspose.Words
- Java
- Document Recovery
title: ตั้งโหมดการกู้คืนเพื่อกู้ไฟล์ Word ที่เสียหาย
url: /th/java/document-loading-and-saving/set-recovery-mode-to-recover-broken-word-document/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# set recovery mode – วิธีกู้คืนไฟล์ Word ที่เสียหายด้วย Aspose.Words

เคยลองเปิดไฟล์ Word ที่ทันใดนั้นปฏิเสธการโหลดหรือไม่? คุณอาจกำลังมองไฟล์ *.docx* ที่เสียหายและสงสัยว่าต้องเริ่มจากศูนย์หรือไม่ ข่าวดีคือ **set recovery mode** ใน Aspose.Words ให้วิธีที่ราบรื่นในการ *load document with recovery* และรักษาส่วนใหญ่ของเนื้อหาไว้ครบถ้วน  

ในบทแนะนำนี้คุณจะได้เรียนรู้อย่างละเอียดว่า **set recovery mode** ทำอย่างไร, ทำไมตัวเลือก *RELAXED* มักเป็นตัวเลือกที่ดีที่สุดสำหรับไฟล์ที่เสียหาย, และวิธีจัดการกับ *recover word document errors* ที่อาจหลุดผ่านบ้าง ไม่ต้องใช้เครื่องมือภายนอก, เพียง Java ธรรมดาและโค้ดไม่กี่บรรทัด

> **สิ่งที่คุณจะได้:** ตัวอย่างที่สมบูรณ์และสามารถรันได้ ซึ่งโหลดไฟล์ Word ที่เสียหาย, ข้ามส่วนที่อ่านไม่ได้, และให้คุณได้อ็อบเจกต์ `Document` ที่พร้อมใช้งานสำหรับการประมวลผลต่อไป

---

## Prerequisites

ก่อนที่เราจะเริ่ม, โปรดตรวจสอบว่าคุณมี:

- **Aspose.Words for Java** (v24.9 หรือใหม่กว่า) ที่เพิ่มเข้าในโปรเจกต์ผ่าน Maven หรือ JAR แบบแมนนวล
- ไฟล์ **corrupted .docx** ที่คุณต้องการทดสอบ (เราจะเรียกมันว่า `Corrupted.docx`)
- ความรู้พื้นฐานของ Java – ไม่จำเป็นต้องเป็นผู้เชี่ยวชาญด้านการประมวลผล Word, แค่สบายกับเมธอด `main` เท่านั้น

หากคุณขาดสิ่งใดสิ่งหนึ่ง, ดาวน์โหลด JAR ล่าสุดของ Aspose.Words จาก [official site](https://products.aspose.com/words/java) แล้วเพิ่มเข้าใน classpath ของคุณ แค่นั้นเอง – ไม่ต้องมีการพึ่งพาไลบรารีเพิ่มเติม

---

## Step 1: Understand the Recovery Modes

Aspose.Words มีสองกลยุทธ์การกู้คืน:

| โหมด | พฤติกรรม | เมื่อควรใช้ |
|------|----------|------------|
| **RELAXED** | ข้ามส่วนที่อ่านไม่ออก, เก็บส่วนที่เหลือไว้ | ไฟล์ที่เสียหายส่วนใหญ่ – คุณต้องการ **recover broken word document** โดยไม่มีข้อยกเว้น |
| **STRICT** | โยนข้อยกเว้นเมื่อเกิดข้อผิดพลาดใด ๆ | เมื่อคุณต้องการรับประกันการโหลดที่สมบูรณ์แบบ ปราศจากข้อผิดพลาด (หายากสำหรับแหล่งที่เสียหาย) |

> **Pro tip:** *RELAXED* เป็นค่าเริ่มต้นสำหรับสถานการณ์ “แค่ได้อะไรกลับมาบ้าง”, ส่วน *STRICT* มีประโยชน์ใน pipeline อัตโนมัติที่ต้องหยุดกระบวนการเมื่อเกิดความล้มเหลว

---

## Step 2: Create a `LoadOptions` Object and **set recovery mode**

นี่คือจุดที่คีย์เวิร์ดหลักปรากฏในโค้ด เราตั้งค่า **set recovery mode** บนอินสแตนซ์ `LoadOptions` ก่อนทำการโหลดไฟล์

```java
import com.aspose.words.*;

public class RecoverWordDocument {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Create LoadOptions and choose a recovery mode.
        // RELAXED will skip unreadable parts, while STRICT throws an exception.
        LoadOptions loadOptions = new LoadOptions();
        loadOptions.setRecoveryMode(LoadOptions.RecoveryMode.RELAXED); // <-- set recovery mode

        // 2️⃣ Load the potentially corrupted document using the configured options.
        Document doc = new Document("YOUR_DIRECTORY/Corrupted.docx", loadOptions);

        // 3️⃣ Verify that the document loaded and optionally save a cleaned copy.
        System.out.println("Document loaded successfully. Page count: " + doc.getPageCount());
        doc.save("Recovered.docx");
    }
}
```

**ทำไมเรื่องนี้ถึงสำคัญ:** การเรียก `setRecoveryMode` จะบอก Aspose.Words ว่าจะพยายามกู้ไฟล์อย่างเข้มข้นแค่ไหน หากไม่เรียกนี้ ไลบรารีจะใช้ค่าเริ่มต้นเป็น *STRICT*, ซึ่งจะยุติการทำงานเมื่อเจอปัญหาแรก – ทำให้วัตถุประสงค์ของ workflow **recover broken word document** สูญเปล่า

---

## Step 3: Verify the Load – Did We Really **recover broken word document**?

หลังจากโหลดแล้ว, คุณสามารถตรวจสอบอ็อบเจกต์ `Document` ได้:

```java
// Check if any sections were dropped
int sections = doc.getSections().getCount();
System.out.println("Sections recovered: " + sections);
```

หากคอนโซลแสดงจำนวน section ที่สมเหตุสมผล, คุณได้ทำการ *load document with recovery* สำเร็จแล้ว ในการปฏิบัติจริง คุณจะสังเกตว่าเนื้อหาส่วนใหญ่, ตารางและรูปภาพยังคงอยู่, ส่วนที่เสียหายจะหายไปโดยอัตโนมัติ

---

## Step 4: Handle Remaining **recover word document errors** Gracefully

แม้ในโหมด *RELAXED* ยังมีกรณีขอบที่อาจทำให้เกิดคำเตือนได้ ห่อการโหลดด้วย `try‑catch` เพื่อให้แอปของคุณยังคงทำงานต่อได้:

```java
try {
    Document doc = new Document("Corrupted.docx", loadOptions);
    // Continue processing...
} catch (Exception ex) {
    System.err.println("Recovery failed: " + ex.getMessage());
    // Optionally fallback to a backup copy or notify the user.
}
```

**เหตุการณ์นี้จะเกิดขึ้นเมื่อใด?** หากไฟล์เสียหายจนแม้แต่ parser แบบ relaxed ไม่สามารถระบุตำแหน่งโครงสร้างเอกสารที่ถูกต้องได้, Aspose.Words จะยังคงโยนข้อยกเว้น ในกรณีเช่นนั้น คุณอาจต้องขอให้ผู้ใช้จัดหาไฟล์สำเนาอื่น

---

## Step 5: Save the Recovered File (Optional)

นักพัฒนาส่วนใหญ่ต้องการเวอร์ชันที่สะอาดเพื่อส่งต่อให้ระบบ downstream คำสั่ง `save` ด้านล่างจะเขียนไฟล์ `.docx` ใหม่ที่ไม่มีส่วนที่เสียหายเหลืออยู่

```java
doc.save("Recovered.docx");
System.out.println("Recovered file saved as Recovered.docx");
```

ตอนนี้คุณมี **recover broken word document** ที่สามารถเปิดได้ใน Microsoft Word, Google Docs หรือโปรแกรมดูไฟล์อื่น ๆ – ไม่มีหน้าต่างข้อผิดพลาด

---

## Visual Overview (Image)

![แผนภาพแสดงกระบวนการ set recovery mode – จากไฟล์ที่เสียหายไปยังเอกสารที่กู้คืน](https://example.com/images/recovery-flow.png "แผนภาพกระบวนการ set recovery mode")

*ข้อความ alt มีคีย์เวิร์ดหลักอย่างชัดเจน, ช่วยทั้งเครื่องมือค้นหาและโปรแกรมอ่านหน้าจอ*

---

## Common Questions & Edge Cases

| คำถาม | คำตอบ |
|----------|--------|
| *ถ้าฉันต้องการเก็บส่วนที่เสียหายไว้เพื่อการวิเคราะห์ทางนิติวิทยาศาสตร์ล่ะ?* | ใช้ `LoadOptions.setRecoverMode(LoadOptions.RecoveryMode.STRICT)` และจับข้อยกเว้น ข้อความของข้อยกเว้นจะมีรายละเอียดเกี่ยวกับส่วนที่เป็นปัญหา |
| *ฉันสามารถสลับระหว่าง RELAXED และ STRICT ระหว่างการทำงานได้หรือไม่?* | ได้เลย—เพียงสร้างอินสแตนซ์ `LoadOptions` ใหม่พร้อมโหมดที่ต้องการก่อนการโหลดแต่ละครั้ง |
| *วิธีนี้ทำงานกับไฟล์ .doc เก่าได้หรือไม่?* | ใช่. `LoadOptions` เดียวกันใช้ได้กับรูปแบบ `.doc` และ `.docx` |
| *มีผลกระทบต่อประสิทธิภาพหรือไม่?* | น้อยมาก. ภาระการพาร์สเพิ่มเติมเป็นเรื่องเล็กน้อยเมื่อเทียบกับค่าใช้จ่ายของการโหลดเอกสารเต็มรูปแบบ |

---

## Full Working Example (Copy‑Paste Ready)

```java
import com.aspose.words.*;

public class RecoverWordDocument {
    public static void main(String[] args) {
        try {
            // Step 1 – configure recovery mode
            LoadOptions loadOptions = new LoadOptions();
            loadOptions.setRecoveryMode(LoadOptions.RecoveryMode.RELAXED); // set recovery mode

            // Step 2 – load the corrupted file
            Document doc = new Document("Corrupted.docx", loadOptions);

            // Step 3 – optional verification
            System.out.println("Loaded! Pages: " + doc.getPageCount());

            // Step 4 – save a clean copy
            doc.save("Recovered.docx");
            System.out.println("Saved recovered document as Recovered.docx");
        } catch (Exception e) {
            System.err.println("Failed to recover document: " + e.getMessage());
        }
    }
}
```

เรียกโปรแกรม, ชี้ไปที่ไฟล์ที่เสียของคุณ, แล้วดูผลลัพธ์ หากทุกอย่างทำงานราบรื่น คุณจะเห็นจำนวนหน้าแสดงบนคอนโซลและไฟล์ `Recovered.docx` ใหม่ปรากฏข้างไฟล์ต้นฉบับ

---

## Conclusion

เราได้ครอบคลุมทุกสิ่งที่คุณต้องการเพื่อ **set recovery mode** ใน Aspose.Words, ตั้งแต่การเลือก `RecoveryMode` ที่เหมาะสมจนถึงการจัดการกับ *recover word document errors* ที่อาจยังคงปรากฏอยู่ ด้วยการทำตามขั้นตอนข้างต้น คุณสามารถ **load document with recovery** อย่างเชื่อถือได้, เก็บส่วนที่ดีของไฟล์ที่เสียและสร้างเวอร์ชันที่สะอาดพร้อมใช้ในกระบวนการต่อไปได้

พร้อมรับความท้าทายต่อไปหรือยัง? ลองผสาน **set recovery mode** กับ API **document cleaning** ของ Aspose.Words — การลบพารากราฟที่ซ่อนอยู่, การแก้ลิงก์ที่เสีย, หรือแม้กระทั่งการแปลงไฟล์ที่กู้คืนเป็น PDF ในขั้นตอนเดียว ความเป็นไปได้ไม่มีที่สิ้นสุด, และตอนนี้คุณมีพื้นฐานที่มั่นคงสำหรับการจัดการไฟล์ Word ที่เสียหายโดยตรง

Happy coding, and may your documents stay healthy!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}