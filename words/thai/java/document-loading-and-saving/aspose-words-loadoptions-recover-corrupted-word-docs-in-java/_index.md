---
category: general
date: 2026-05-04
description: เรียนรู้วิธีที่ LoadOptions ของ Aspose.Words สามารถกู้คืนไฟล์ Word ที่เสียหาย,
  ใช้โหมดการกู้คืน, ซ่อมแซมไฟล์ docx ที่เสียหายและนับจำนวนหน้าของ Word ในบทเรียนเดียว
draft: false
keywords:
- aspose words loadoptions
- recover corrupted word
- use recovery mode
- repair corrupted docx
- get word page count
language: th
og_description: เชี่ยวชาญการใช้ Aspose.Words LoadOptions เพื่อกู้ไฟล์ Word ที่เสียหาย,
  เลือกโหมดการกู้ที่เหมาะสม, ซ่อมแซมไฟล์ docx ที่เสียและดึงจำนวนหน้ามาได้
og_title: aspose words loadoptions – กู้คืนเอกสาร Word ที่เสียหาย
tags:
- Aspose.Words
- Java
- Document Recovery
title: aspose words loadoptions – กู้คืนเอกสาร Word ที่เสียหายใน Java
url: /th/java/document-loading-and-saving/aspose-words-loadoptions-recover-corrupted-word-docs-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# aspose words loadoptions – กู้คืนไฟล์ Word ที่เสียหายใน Java

เคยลองเปิดไฟล์ Word แล้วไฟล์นั้นปฏิเสธการโหลดหรือไม่? เป็นความรู้สึกเจ็บปวดเมื่อไคลเอนต์ส่ง **docx ที่เสียหาย** มาให้คุณและคุณไม่รู้ว่าจะกู้คืนได้หรือไม่ ข่าวดีคือ? ด้วย **aspose words loadoptions** คุณสามารถบอก Aspose.Words ว่าจะทำอย่างไรเมื่อเอกสารถูกทำลาย ไม่ว่าจะโยนข้อยกเว้นหรือพยายามแก้ไขแบบเงียบ ๆ  

ในบทแนะนำนี้เราจะเดินผ่านการใช้ `LoadOptions` เพื่อ **กู้ไฟล์ Word ที่เสียหาย** สำรวจการตั้งค่า **use recovery mode** ดูวิธี **repair corrupted docx** อัตโนมัติ และสรุปด้วย **การดึงจำนวนหน้าของ Word** จากเอกสารที่กู้คืนแล้ว ไม่ต้องใช้เครื่องมือภายนอก เพียงแค่ Java และ Aspose.Words

## สิ่งที่คุณต้องมี

- **Aspose.Words for Java** (v24.12 หรือใหม่กว่า) – เวอร์ชันล่าสุดเพิ่มการตรวจสอบความปลอดภัยเพิ่มเติม
- **IDE สำหรับ Java** (IntelliJ IDEA, Eclipse หรือแม้แต่ข้อความธรรมดาพร้อม `javac`)
- **DOCX ที่เสียหาย** ที่คุณต้องการทดสอบ (เราจะเรียกมันว่า `Corrupted.docx`)
- **ความเข้าใจพื้นฐาน** ของไวยากรณ์ Java – ไม่ต้องซับซ้อน เพียง `public static void main` ธรรมดา

> **เคล็ดลับ:** เก็บสำเนาสำรองของไฟล์ต้นฉบับไว้; การพยายามกู้คืนอาจเขียนทับบางส่วนของไบนารีได้

## ขั้นตอนที่ 1: สร้าง LoadOptions – แกนหลักของการกู้คืน

สิ่งแรกที่คุณทำคือสร้างอ็อบเจกต์ `LoadOptions` อ็อบเจกต์นี้เป็นแผงควบคุมของคุณ; มันบอก Aspose.Words ว่าจะจัดการไฟล์อย่างไรเมื่อพบปัญหา

```java
// Step 1: Initialise LoadOptions
LoadOptions loadOptions = new LoadOptions();
```

ทำไมขั้นตอนนี้ถึงสำคัญ? เพราะหากไม่มี `LoadOptions` ไลบรารีจะใช้พฤติกรรมเริ่มต้น ซึ่งอาจมองข้ามข้อผิดพลาดแบบเงียบ ๆ หรือแย่กว่า คือคืนเอกสารที่โหลดบางส่วนแล้วทำให้แอปพังในภายหลัง การกำหนดค่าตัวเลือกอย่างชัดเจนทำให้คุณได้การจัดการข้อผิดพลาดที่กำหนดได้

## ขั้นตอนที่ 2: เลือกโหมดการกู้คืนที่เหมาะสม

Aspose.Words มีสองกลยุทธ์การกู้คืน:

| Mode | Behaviour |
|------|-----------|
| `RecoveryMode.STRICT` | Throws an exception if the document cannot be fully repaired. |
| `RecoveryMode.REPAIR` | Attempts to fix the file and continues loading, even if some content is lost. |

สำหรับสถานการณ์ **recover corrupted word** ที่คุณต้องการรู้ว่าการแก้ไขสำเร็จหรือไม่ `STRICT` เป็นตัวเลือกที่ปลอดภัยที่สุด หากคุณต้องการวิธีแบบพยายามเต็มที่ ให้สลับเป็น `REPAIR`

```java
// Step 2: Set the recovery mode
loadOptions.setRecoveryMode(RecoveryMode.STRICT);
// loadOptions.setRecoveryMode(RecoveryMode.REPAIR); // Uncomment to attempt automatic repair
```

> **ทำไมต้องเลือกอันใดอันหนึ่ง?**  
> *STRICT* ให้สัญญาณที่ชัดเจน—เอกสารใช้งานได้หรือคุณต้องแจ้งผู้ใช้ *REPAIR* เหมาะกับงานแบบ batch ที่คุณยอมรับการสูญเสียรูปภาพหรือส่วนอื่น ๆ บางส่วนได้

## ขั้นตอนที่ 3: โหลดเอกสารที่อาจเสียหาย

ต่อไปคุณเปิดไฟล์โดยส่ง `LoadOptions` ที่ตั้งค่าไว้ หากไฟล์อยู่เกินกว่าที่จะซ่อมและคุณเลือก `STRICT` จะมีข้อยกเว้นเกิดขึ้น; หากไม่เช่นนั้นคุณจะได้อ็อบเจกต์ `Document` พร้อมตรวจสอบ

```java
// Step 3: Load the document with the configured options
Document document = new Document("YOUR_DIRECTORY/Corrupted.docx", loadOptions);
```

สังเกตว่าเส้นทางไฟล์อาจเป็นแบบ absolute หรือ relative จากโฟลเดอร์รากของโปรเจกต์ `Document` คลาสทำหน้าที่เป็นตัวกลางของไฟล์ Word ทั้งหมด ทำให้คุณสามารถสอบถามข้อมูลเช่นจำนวนหน้า, ส่วนต่าง ๆ หรือแม้แก้ไขเนื้อหาหลังการกู้คืนได้ง่าย ๆ

## ขั้นตอนที่ 4: ตรวจสอบการโหลด – ดึงจำนวนหน้าของ Word

การตรวจสอบอย่างรวดเร็วคือการถาม Aspose.Words ว่าเอกสารมีจำนวนหน้าเท่าไหร่ หากจำนวนไม่เป็นศูนย์ คุณน่าจะ **repair corrupted docx** สำเร็จแล้ว

```java
// Step 4: Output the page count to confirm successful loading
System.out.println("Loaded successfully, page count = " + document.getPageCount());
```

ผลลัพธ์ที่คาดหวัง:

```
Loaded successfully, page count = 12
```

หากเอกสารถูกพิจารณาว่าอ่านไม่ได้ภายใต้ `STRICT` โค้ดจะโยนข้อยกเว้นก่อนถึงบรรทัดนี้ การตรวจสอบ `page count` จึงทำหน้าที่เป็นการยืนยันและเป็นข้อมูลที่มีประโยชน์สำหรับตรรกะต่อไป (เช่น การแบ่งหน้าในเว็บวิวเวอร์)

## ตัวอย่างทำงานเต็มรูปแบบ

ด้านล่างเป็นโปรแกรม Java ที่พร้อมรันครบทุกขั้นตอน คัดลอกและวางลงในไฟล์ชื่อ `RecoveryModeDemo.java` ปรับเส้นทางไฟล์ แล้วรัน `javac RecoveryModeDemo.java && java RecoveryModeDemo`

```java
import com.aspose.words.*;

public class RecoveryModeDemo {
    public static void main(String[] args) throws Exception {

        // Step 1: Create LoadOptions to control how the file is opened
        LoadOptions loadOptions = new LoadOptions();

        // Step 2: Choose strict recovery – an exception is thrown if the file cannot be repaired
        loadOptions.setRecoveryMode(RecoveryMode.STRICT);
        // loadOptions.setRecoveryMode(RecoveryMode.REPAIR); // alternative: attempt repair and continue

        // Step 3: Load the possibly‑corrupted document using the configured options
        Document document = new Document("YOUR_DIRECTORY/Corrupted.docx", loadOptions);

        // Step 4: Verify that the document was loaded (e.g., output its page count)
        System.out.println("Loaded successfully, page count = " + document.getPageCount());
    }
}
```

### ผลลัพธ์ที่คาดว่าจะได้

- **ถ้าไฟล์สามารถกู้คืนได้:** คอนโซลจะแสดงจำนวนหน้าและคุณสามารถดำเนินการต่อกับอ็อบเจกต์ `Document` ได้อย่างปลอดภัย
- **ถ้าไฟล์อยู่เกินกว่าที่จะซ่อม (โหมด STRICT):** จะเกิด `com.aspose.words.UnsupportedFileFormatException` (หรือคล้ายกัน) ซึ่งคุณสามารถจับและจัดการอย่างสุภาพได้

## คำถามที่พบบ่อย & กรณีขอบ

### ต้องการบันทึกรายละเอียดข้อผิดพลาดอย่างแม่นยำทำอย่างไร?

ห่อโค้ดการโหลดด้วยบล็อก `try‑catch` แล้วบันทึก `e.getMessage()` จะให้เหตุผลที่ชัดเจน—ไม่ว่าจะเป็นส่วนที่หายไป, ความสัมพันธ์ที่ขัดข้อง, หรือสตรีมที่เสียหาย

```java
try {
    Document doc = new Document("Corrupted.docx", loadOptions);
    System.out.println("Pages: " + doc.getPageCount());
} catch (Exception e) {
    System.err.println("Recovery failed: " + e.getMessage());
}
```

### สามารถกู้คืนเฉพาะส่วนบางอย่าง (เช่นข้อความแต่ไม่ใช่รูปภาพ) ได้หรือไม่?

Aspose.Words ไม่ได้เปิดให้กำหนดการกู้คืนแบบละเอียดระดับส่วนย่อย แต่หลังจากโหลดแล้วคุณสามารถวนลูป `NodeType` และละทิ้งโหนดที่เป็น `NodeType.SHAPE` (รูปภาพ) หากทำให้เกิดปัญหาในขั้นตอนต่อไป

### ทำงานกับไฟล์ `.doc` เก่าได้หรือไม่?

ได้. `LoadOptions` ทำงานกับฟอร์แมต Word ทุกประเภท (`.doc`, `.docx`, `.dot`, `.dotx`) โดยใช้ตรรกะการกู้คืนเดียวกัน

### ไลบรารีจัดการไฟล์ที่มีรหัสผ่านอย่างไร?

หากไฟล์ถูกเข้ารหัส `LoadOptions` จะไม่ข้ามรหัสผ่าน คุณต้องใส่รหัสผ่านผ่าน `loadOptions.setPassword("yourPassword")` โหมดการกู้คืนจะทำงานหลังจากถอดรหัสสำเร็จเท่านั้น

## เคล็ดลับสำหรับการใช้งานใน Production

- **บันทึกโหมดการกู้คืนที่เลือก** – ช่วยให้คุณตรวจสอบภายหลังว่าทำไมไฟล์ใดไฟล์หนึ่งถึงสำเร็จหรือไม่สำเร็จ
- **ห้ามเขียนทับไฟล์ต้นฉบับ** – บันทึกเอกสารที่กู้คืนไปยังตำแหน่งใหม่ (`document.save("Recovered.docx")`)
- **ผสานกับการตรวจสอบคุณภาพ** – หลังการกู้คืนให้รันการตรวจสอบการสะกดหรือโครงสร้างเพื่อให้แน่ใจว่าเอกสารถูกต้องตามกฎธุรกิจของคุณ
- **ประมวลผลแบบ batch** – เมื่อจัดการไฟล์หลายไฟล์ ให้วนลูปแต่ละไฟล์, จับข้อยกเว้นแยกกัน, และสรุปรายงานความสำเร็จ vs. ความล้มเหลว

## สรุป

คุณมีสูตรครบวงจรสำหรับการใช้ **aspose words loadoptions** เพื่อ **recover corrupted Word** เอกสาร, ตัดสินใจว่าจะ **use recovery mode** อย่างเคร่งครัดหรือยืดหยุ่น, **repair corrupted docx** ตามต้องการ, และสุดท้าย **get the word page count** ของไฟล์ที่กู้คืนแล้ว วิธีการนี้กำหนดได้, ผสานง่ายกับ pipeline ของ Java ที่มีอยู่แล้ว, และให้คุณควบคุมระดับความรุนแรงของไลบรารีเมื่อเจอไฟล์ไบนารีที่เสียหาย

พร้อมจะก้าวต่อ? ลองสลับ `RecoveryMode.STRICT` เป็น `REPAIR` ในงาน batch, หรือขยายตัวอย่างให้บันทึกไฟล์ที่ซ่อมแล้วไปยังโฟลเดอร์ปลอดภัย ความเป็นไปได้ไม่มีที่สิ้นสุด และด้วย Aspose.Words คุณพร้อมรับมือกับปัญหา Word ที่แสนซับซ้อนที่สุด

Happy coding, and may your documents always load cleanly!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}