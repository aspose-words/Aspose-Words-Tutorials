---
category: general
date: 2026-05-26
description: เปิดเอกสาร Word ที่เสียหายใน Java ด้วย Aspose.Words. เรียนรู้วิธีตั้งค่าโหมดการกู้คืนและกู้ไฟล์
  Word ที่เสียหายได้อย่างน่าเชื่อถือ.
draft: false
keywords:
- open corrupted word document
- set recovery mode
- how to recover corrupted word file
- Aspose.Words Java
- document recovery Java
language: th
og_description: เปิดเอกสาร Word ที่เสียหายใน Java ด้วย Aspose.Words คู่มือนี้แสดงวิธีตั้งค่าโหมดการกู้คืนและกู้คืนไฟล์
  Word ที่เสียหายอย่างมีประสิทธิภาพ
og_title: เปิดเอกสาร Word ที่เสียหาย – ตั้งค่าโหมดการกู้คืนใน Java
schemas:
- author: Aspose
  dateModified: '2026-05-26'
  description: Open corrupted word document in Java with Aspose.Words. Learn how to
    set recovery mode and recover corrupted Word files reliably.
  headline: Open Corrupted Word Document – Set Recovery Mode in Java
  type: TechArticle
- description: Open corrupted word document in Java with Aspose.Words. Learn how to
    set recovery mode and recover corrupted Word files reliably.
  name: Open Corrupted Word Document – Set Recovery Mode in Java
  steps:
  - name: Why each line matters
    text: '* **`LoadOptions loadOptions = new LoadOptions();`** – without this object
      Aspose.Words uses default recovery, which *rejects* corrupted files. Creating
      it gives you the hook to change that behavior. * **`setRecoveryMode(...)`**
      – this is the **set recovery mode** call that decides whether warnings '
  - name: 1. File Not Found
    text: 'If the path is wrong, `Document` throws a `FileNotFoundException`. Wrap
      the load in a try‑catch block and log a friendly message:'
  - name: 2. Irrecoverable Corruption
    text: Even with `RECOVER_WITH_WARNINGS`, some structures are beyond repair. In
      that case Aspose.Words still loads what it can, but you’ll see warnings like
      “Cannot read paragraph properties”. Pay attention to the console output; those
      warnings often point to missing sections that you may need to reconstru
  - name: 3. Large Files and Performance
    text: Recovery adds a small overhead because the library parses the file twice—once
      to detect issues, again to rebuild. For multi‑gigabyte documents, consider streaming
      the file or increasing the JVM heap (`-Xmx2g`) to avoid `OutOfMemoryError`.
  type: HowTo
tags:
- Aspose.Words
- Java
- Word
title: เปิดไฟล์ Word ที่เสียหาย – ตั้งค่าโหมดการกู้คืนใน Java
url: /th/java/document-loading-and-saving/open-corrupted-word-document-set-recovery-mode-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# เปิดไฟล์ Word ที่เสีย – ตั้งค่าโหมดการกู้คืนใน Java

เคยลองเปิดไฟล์ Word ที่เสียและเห็นโปรแกรมหยุดทำงานด้วยข้อยกเว้นหรือไม่? คุณไม่ได้เป็นคนเดียว—ไฟล์ .docx ที่เสียเหล่านั้นอาจทำให้ศีรษะปวด ข่าวดีคือ Aspose.Words for Java ให้คุณควบคุมได้ละเอียดเพื่อที่คุณจะสามารถ **เปิดไฟล์ Word ที่เสีย** โดยไม่ทำให้แอปพัง, และยังสามารถเลือกว่าจะให้แสดงคำเตือน, การกู้คืนแบบเงียบ, หรือการปฏิเสธอย่างเด็ดขาด

ในบทแนะนำนี้เราจะเดินผ่านกระบวนการทั้งหมด: ตั้งแต่การสร้าง `LoadOptions` ที่เหมาะสม, การเลือกค่าของ **set recovery mode** ที่เหมาะสม, และสุดท้ายยืนยันว่าเอกสารถูกโหลดสำเร็จแล้ว. เมื่อจบคุณจะรู้ **how to recover corrupted word file** ด้วยโปรแกรม, ไม่ต้องคัดลอก‑วางด้วยตนเอง

> **สิ่งที่คุณต้องการ**  
> * Java 8 หรือใหม่กว่า (API ทำงานกับ Java 11 ด้วยเช่นกัน)  
> * Aspose.Words for Java 23.9 (หรือเวอร์ชันล่าสุด)  
> * ไฟล์ .docx ที่เสียตัวอย่าง—เพียงเปลี่ยนชื่อไฟล์ที่ใช้งานได้ใด ๆ เพื่อจำลองการเสียหายหากคุณไม่มีไฟล์พร้อมใช้งาน  

Let’s dive in.

## เปิดไฟล์ Word ที่เสีย – ภาพรวมขั้นตอนโดยละเอียด

ต่อไปนี้คือกระบวนการระดับสูงที่เราจะดำเนินการ:

1. **Create `LoadOptions`** – วัตถุนี้บอก Aspose.Words ว่าจะทำอย่างไรเมื่อเจอปัญหา.  
2. **Set recovery mode** – เลือก `RECOVER_WITH_WARNINGS`, `RECOVER_WITHOUT_WARNINGS`, หรือ `REJECT_CORRUPTED`.  
3. **Load the document** โดยใช้ตัวเลือกที่กำหนดค่าไว้.  
4. **Verify** การโหลดสำเร็จ (เช่น พิมพ์จำนวนหน้า).  

แต่ละขั้นตอนจะอธิบายอย่างละเอียด พร้อมตัวอย่างโค้ดที่คุณสามารถคัดลอก‑วางโดยตรงลงใน IDE ของคุณ.

## ตั้งค่าโหมดการกู้คืนสำหรับสถานการณ์ต่าง ๆ

Aspose.Words กำหนดกลยุทธ์การกู้คืนสามแบบภายใน `LoadOptions.RecoveryMode`:

| โหมด | พฤติกรรม | เมื่อใช้ |
|------|-----------|----------|
| `RECOVER_WITH_WARNINGS` | พยายามโหลดเอกสาร แต่แสดงปัญหาใด ๆ เป็นคำเตือนในคอนโซล. | คุณต้องการดู *ว่า* สิ่งใดผิดพลาดโดยไม่หยุดการทำงาน. |
| `RECOVER_WITHOUT_WARNINGS` | แก้ไขโดยเงียบ ๆ สิ่งที่ทำได้และซ่อนคำเตือน. | สภาพแวดล้อมการผลิตที่ต้องการให้บันทึกสะอาด. |
| `REJECT_CORRUPTED` | ขว้างข้อยกเว้นทันทีที่ตรวจพบความเสียหาย. | กระบวนการตรวจสอบที่เข้มงวดซึ่งต้องล้มเหลวอย่างรวดเร็ว. |

การเลือกโหมดที่เหมาะสมนั้นเป็นหัวใจของการใช้ **set recovery mode** อย่างถูกต้อง. ในการดีบักส่วนใหญ่ `RECOVER_WITH_WARNINGS` เป็นจุดที่เหมาะที่สุดเพราะมันบอกคุณอย่างชัดเจนว่ามีส่วนใดบ้างที่ถูกซ่อมแซม.

## วิธีการกู้คืนไฟล์ Word ที่เสียโดยใช้ Aspose.Words

ต่อไปนี้เป็น **โปรแกรม Java ที่สมบูรณ์และสามารถรันได้** ที่แสดงกระบวนการทั้งหมด. คุณสามารถวางลงในไฟล์ `RecoveryModeDemo.java`, ปรับเส้นทาง, แล้วรันได้เลย.

```java
import com.aspose.words.*;

public class RecoveryModeDemo {
    public static void main(String[] args) throws Exception {
        // -------------------------------------------------
        // Step 1: Prepare LoadOptions – this controls recovery
        // -------------------------------------------------
        LoadOptions loadOptions = new LoadOptions();

        // -------------------------------------------------
        // Step 2: Choose the recovery behavior
        // -------------------------------------------------
        // Option A – show warnings (great for debugging)
        loadOptions.setRecoveryMode(LoadOptions.RecoveryMode.RECOVER_WITH_WARNINGS);

        // Uncomment ONE of the alternatives below if you need a different behavior:
        // loadOptions.setRecoveryMode(LoadOptions.RecoveryMode.RECOVER_WITHOUT_WARNINGS);
        // loadOptions.setRecoveryMode(LoadOptions.RecoveryMode.REJECT_CORRUPTED);

        // -------------------------------------------------
        // Step 3: Load the potentially corrupted document
        // -------------------------------------------------
        // Replace the placeholder with the actual path to your .docx file
        String corruptedPath = "C:/temp/corrupted.docx";
        Document doc = new Document(corruptedPath, loadOptions);

        // -------------------------------------------------
        // Step 4: Verify that the document is usable
        // -------------------------------------------------
        System.out.println("Document loaded successfully!");
        System.out.println("Page count = " + doc.getPageCount());

        // Bonus: you can now save the repaired file if you wish
        doc.save("C:/temp/recovered.docx");
        System.out.println("Recovered file saved as recovered.docx");
    }
}
```

### ทำไมแต่ละบรรทัดจึงสำคัญ

* **`LoadOptions loadOptions = new LoadOptions();`** – หากไม่มีวัตถุนี้ Aspose.Words จะใช้การกู้คืนค่าเริ่มต้น ซึ่ง *ปฏิเสธ* ไฟล์ที่เสีย. การสร้างมันให้คุณมีจุดเชื่อมต่อเพื่อเปลี่ยนพฤติกรรมนั้น.  
* **`setRecoveryMode(...)`** – นี่คือการเรียก **set recovery mode** ที่กำหนดว่าคำเตือนจะแสดง, ซ่อน, หรือทำให้เกิดข้อยกเว้น.  
* **`new Document(path, loadOptions);`** – ตัวสร้างรับ `LoadOptions` ที่เราตั้งค่าไว้, ดังนั้นไลบรารีจะรู้ว่าจะจัดการไฟล์ที่เสียอย่างไรตั้งแต่แรก.  
* **`doc.getPageCount()`** – การตรวจสอบอย่างรวดเร็ว. หากเอกสารถูกโหลดและคืนค่าจำนวนหน้า, คุณได้ทำ **how to recover corrupted word file** สำเร็จแล้ว.  
* **`doc.save(...)`** – เป็นตัวเลือกแต่สะดวก; คุณสามารถบันทึกเวอร์ชันที่ซ่อมแซมกลับไปยังดิสก์เพื่อใช้ในภายหลัง.  

## การจัดการกรณีขอบที่พบบ่อย

### 1. ไม่พบไฟล์

หากเส้นทางผิด, `Document` จะขว้าง `FileNotFoundException`. ห่อการโหลดในบล็อก try‑catch และบันทึกข้อความที่เป็นมิตร:

```java
try {
    Document doc = new Document(corruptedPath, loadOptions);
    // proceed...
} catch (FileNotFoundException e) {
    System.err.println("The file was not found: " + corruptedPath);
}
```

### 2. ความเสียหายที่ไม่สามารถกู้คืนได้

แม้จะใช้ `RECOVER_WITH_WARNINGS`, โครงสร้างบางอย่างก็เกินกว่าจะซ่อมแซมได้. ในกรณีนั้น Aspose.Words ยังโหลดสิ่งที่ทำได้, แต่คุณจะเห็นคำเตือนเช่น “Cannot read paragraph properties”. ให้ใส่ใจผลลัพธ์ในคอนโซล; คำเตือนเหล่านั้นมักชี้ไปยังส่วนที่หายไปซึ่งคุณอาจต้องสร้างใหม่ด้วยตนเอง.

### 3. ไฟล์ขนาดใหญ่และประสิทธิภาพ

การกู้คืนเพิ่มภาระเล็กน้อยเนื่องจากไลบรารีต้องวิเคราะห์ไฟล์สองครั้ง—ครั้งแรกเพื่อตรวจจับปัญหา, ครั้งที่สองเพื่อสร้างใหม่. สำหรับเอกสารหลายกิกะไบต์, พิจารณา stream ไฟล์หรือเพิ่ม heap ของ JVM (`-Xmx2g`) เพื่อหลีกเลี่ยง `OutOfMemoryError`.

## เคล็ดลับระดับมืออาชีพ – ทำให้การกู้คืนมั่นคง

* **Log warnings to a file** – เปลี่ยนการส่งออก `System.err` ไปยัง logger เพื่อให้คุณมีบันทึกการตรวจสอบว่ามีอะไรถูกแก้ไข.  
* **Validate after recovery** – เรียก `doc.updatePageLayout();` แล้วตรวจสอบจำนวนหน้าใหม่; บางครั้งการจัดวางเปลี่ยนหลังจากซ่อมแซมส่วนที่เสีย.  
* **Automate batch recovery** – ห่อเดโมในลูปที่ประมวลผลโฟลเดอร์ของไฟล์ที่เสีย, ใช้ `LoadOptions` เดียวกันทุกครั้ง.  

## สรุป

ตอนนี้คุณรู้วิธี **how to recover corrupted word file** ด้วย Aspose.Words for Java อย่างแม่นยำ. ด้วยการสร้างอินสแตนซ์ `LoadOptions`, **set recovery mode** ให้เป็นกลยุทธ์ที่เหมาะกับสถานการณ์ของคุณ, และโหลดเอกสารด้วยตัวเลือกเหล่านั้น, คุณสามารถ **เปิดไฟล์ Word ที่เสีย** อย่างปลอดภัยโดยไม่ทำให้แอปพัง. ตัวอย่างโค้ดข้างต้นเป็นโซลูชันที่สมบูรณ์และพร้อมรันที่พิมพ์จำนวนหน้าและแม้แต่บันทึกสำเนาที่ทำความสะอาดแล้ว.

ต่อไปคุณจะทำอะไร? ลองสลับโหมดการกู้คืนเป็น `RECOVER_WITHOUT_WARNINGS` และเปรียบเทียบผลลัพธ์ในคอนโซล, หรือทดลองโหลดเอกสารที่เข้ารหัส (คุณจะต้องให้รหัสผ่านผ่าน

## บทแนะนำที่เกี่ยวข้อง

- [Aspose.Words Java: คู่มือครอบคลุมการประมวลผลเอกสาร Word](/words/english/java/document-operations/aspose-words-java-master-word-processing/)
- [วิธีแปลง Word เป็น PDF ด้วย Aspose.Words for Java](/words/english/java/document-converting/using-document-converting/)
- [วิธีเปรียบเทียบไฟล์ Word สองไฟล์ด้วย Aspose.Words for Java](/words/english/java/document-manipulation/comparing-documents/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}