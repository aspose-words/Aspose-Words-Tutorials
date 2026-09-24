---
date: 2025-12-24
description: เรียนรู้วิธีแปลงไฟล์ Word เป็น RTF ด้วย Aspose.Words สำหรับ Java บทแนะนำขั้นตอนนี้จะแสดงการโหลดไฟล์
  DOCX การกำหนดค่าตัวเลือกการบันทึกเป็น RTF และการบันทึกเป็นข้อความรูปแบบ Rich Text.
linktitle: Saving Documents as RTF Format
second_title: Aspose.Words Java Document Processing API
title: แปลง Word เป็น RTF ด้วย Aspose.Words for Java บทเรียน
url: /th/java/document-loading-and-saving/saving-documents-as-rtf-format/
weight: 23
---

{{< blocks/products/pf/tutorial-page-section >}}

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

# แปลง Word เป็น RTF ด้วย Aspose.Words for Java

ในบทแนะนำนี้คุณจะได้เรียนรู้ **วิธีแปลง Word เป็น RTF** อย่างรวดเร็วและเชื่อถือได้โดยใช้ Aspose.Words for Java การแปลงไฟล์ DOCX ไปเป็นรูปแบบ Rich‑Text RTF เป็นความต้องการทั่วไปเมื่อคุณต้องการความเข้ากันได้กับโปรเซสเซอร์คำเก่า, ไคลเอนต์อีเมล, หรือระบบจัดเก็บเอกสาร เราจะเดินผ่านการโหลดเอกสาร Word ใน Java, ปรับแต่งตัวเลือกการบันทึก RTF (รวมถึงการบันทึกรูปภาพเป็น WMF), และสุดท้ายเขียนไฟล์ผลลัพธ์ออกมา

## คำตอบสั้น
- **“แปลง word เป็น rtf” หมายความว่าอะไร?** จะทำการแปลงไฟล์ DOCX/Word ให้เป็น Rich Text Format พร้อมคงรักษาข้อความ, สไตล์, และรูปภาพ (ถ้าต้องการ)  
- **ต้องมีลิขสิทธิ์หรือไม่?** เวอร์ชันทดลองฟรีใช้ได้สำหรับการพัฒนา; ต้องมีลิขสิทธิ์เชิงพาณิชย์สำหรับการใช้งานจริง  
- **รองรับเวอร์ชัน Java ใด?** Aspose.Words for Java รองรับ Java 8 ขึ้นไป  
- **สามารถคงรูปภาพไว้ได้หรือไม่?** ได้ – ใช้ตัวเลือก `saveImagesAsWmf` เพื่อฝังรูปภาพเป็น WMF ภายใน RTF  
- **การแปลงใช้เวลานานแค่ไหน?** ปกติภายในไม่กี่วินาทีสำหรับเอกสารมาตรฐาน; ไฟล์ขนาดใหญ่กว่าอาจใช้เวลาสองสามวินาที

## “แปลง word เป็น rtf” คืออะไร?
การแปลงเอกสาร Word ไปเป็น RTF จะสร้างไฟล์ที่เป็นอิสระต่อแพลตฟอร์มซึ่งเก็บข้อความ, การจัดรูปแบบ, และรูปภาพ (ถ้าต้องการ) ในรูปแบบมาร์กอัปแบบข้อความธรรมดา ทำให้เอกสารสามารถเปิดดูได้ในเกือบทุกโปรเซสเซอร์คำโดยไม่สูญเสียเลย์เอาต์

## ทำไมต้องใช้ Aspose.Words for Java เพื่อบันทึกเป็น rich text?
- **ความแม่นยำเต็มรูปแบบ** – ทุกคุณลักษณะของ Word (สไตล์, ตาราง, ส่วนหัว/ส่วนท้าย) จะถูกเก็บไว้ครบถ้วน  
- **ไม่ต้องใช้ Microsoft Office** – ทำงานได้บนเซิร์ฟเวอร์หรือคลาวด์ใดก็ได้  
- **การควบคุมละเอียด** – ตัวเลือกการบันทึกให้คุณกำหนดวิธีการเก็บรูปภาพ, การเข้ารหัสที่ใช้, และอื่น ๆ

## ข้อกำหนดเบื้องต้น
1. **ไลบรารี Aspose.Words for Java** – ดาวน์โหลดและเพิ่มไฟล์ JAR ไปยังโปรเจกต์ของคุณจาก [ที่นี่](https://releases.aspose.com/words/java/)  
2. **ไฟล์ Word ต้นฉบับ** – ตัวอย่างเช่น `Document.docx` ที่คุณต้องการบันทึกเป็น RTF  
3. **สภาพแวดล้อมการพัฒนา Java** – JDK 8+ และ IDE ที่คุณชื่นชอบ

## ขั้นตอนที่ 1: โหลดเอกสาร Word (load word document java)
ก่อนอื่นให้โหลดไฟล์ DOCX ที่มีอยู่เข้าไปในอ็อบเจ็กต์ `Document` ซึ่งเป็นพื้นฐานของการแปลงใด ๆ

```java
import com.aspose.words.Document;

// Load the source document (e.g., Document.docx)
Document doc = new Document("path/to/Document.docx");
```

> **เคล็ดลับ:** ใช้เส้นทางแบบ absolute หรือทรัพยากรใน class‑path เพื่อหลีกเลี่ยง `FileNotFoundException`

## ขั้นตอนที่ 2: กำหนดค่าตัวเลือกการบันทึก RTF (save images as wmf)
Aspose.Words มีคลาส `RtfSaveOptions` ให้ปรับแต่งผลลัพธ์ ในตัวอย่างนี้เราจะเปิด **บันทึกรูปภาพเป็น WMF** ซึ่งเป็นรูปแบบที่แนะนำสำหรับไฟล์ RTF

```java
import com.aspose.words.RtfSaveOptions;

// Create an instance of RtfSaveOptions
RtfSaveOptions saveOptions = new RtfSaveOptions();

// Set the option to save images as WMF
saveOptions.setSaveImagesAsWmf(true);
```

คุณยังสามารถปรับตั้งค่าอื่น ๆ เช่น `saveOptions.setEncoding(Charset.forName("UTF-8"))` หากต้องการการเข้ารหัสอักขระเฉพาะ

## ขั้นตอนที่ 3: บันทึกเอกสารเป็น RTF (save docx as rtf)
ตอนนี้ให้เขียนเอกสารออกโดยใช้ตัวเลือกที่กำหนดไว้ ขั้นตอนนี้ **บันทึก DOCX เป็น RTF** ทำให้ได้ไฟล์ rich‑text พร้อมแจกจ่าย

```java
// Save the document in RTF format

doc.save("path/to/output.rtf", saveOptions);
```

## โค้ดต้นฉบับทั้งหมดสำหรับการแปลง Word เป็น RTF
ด้านล่างเป็นเวอร์ชันย่อที่คุณสามารถคัดลอก‑วางลงในคลาส Java ได้ มันสาธิต **การบันทึกเป็น rich text** พร้อมตัวเลือกรูปภาพ WMF ในบล็อกเดียว

```java
Document doc = new Document("Your Directory Path" + "Document.docx");
RtfSaveOptions saveOptions = new RtfSaveOptions(); { saveOptions.setSaveImagesAsWmf(true); }
doc.save("Your Directory Path" + "WorkingWithRtfSaveOptions.SavingImagesAsWmf.rtf", saveOptions);
```

## ข้อผิดพลาดทั่วไปและการแก้ไขปัญหา
| ปัญหา | สาเหตุ | วิธีแก้ |
|-------|--------|-----|
| RTF ที่ได้เป็นไฟล์เปล่า | ไม่พบไฟล์ต้นฉบับหรือไม่โหลด | ตรวจสอบเส้นทางใน `new Document(...)` |
| รูปภาพหาย | `saveImagesAsWmf` ตั้งเป็น `false` | เปิด `saveOptions.setSaveImagesAsWmf(true)` |
| ตัวอักษรแสดงเป็นอักขระแปลก | การเข้ารหัสไม่ถูกต้อง | ตั้ง `saveOptions.setEncoding(Charset.forName("UTF-8"))` |

## คำถามที่พบบ่อย

**ถาม: ฉันจะเปลี่ยนตัวเลือกการบันทึก RTF อื่น ๆ ได้อย่างไร?**  
ตอบ: ใช้คลาส `RtfSaveOptions` – มีคุณสมบัติสำหรับการบีบอัด, ฟอนต์, และอื่น ๆ ดูเอกสาร API ของ Aspose.Words for Java เพื่อรายการเต็ม

**ถาม: สามารถบันทึกเอกสาร RTF ด้วยการเข้ารหัสอื่นได้หรือไม่?**  
ตอบ: ได้ เรียก `saveOptions.setEncoding(Charset.forName("UTF-8"))` (หรือ charset ที่รองรับ) ก่อนบันทึก

**ถาม: สามารถบันทึกเอกสาร RTF โดยไม่มีรูปภาพได้หรือไม่?**  
ตอบ: แน่นอน ตั้ง `saveOptions.setSaveImagesAsWmf(false)` เพื่อไม่รวมรูปภาพในผลลัพธ์

**ถาม: ควรจัดการข้อยกเว้นระหว่างการแปลงอย่างไร?**  
ตอบ: ห่อการโหลดและการบันทึกด้วยบล็อก `try‑catch` ที่จับ `Exception` บันทึกข้อผิดพลาดและอาจโยนข้อยกเว้นแบบกำหนดเองสำหรับแอปของคุณ

**ถาม: วิธีนี้ทำงานกับไฟล์ Word ที่มีการป้องกันด้วยรหัสผ่านหรือไม่?**  
ตอบ: โหลดเอกสารด้วยอ็อบเจ็กต์ `LoadOptions` ที่ใส่รหัสผ่านแล้วดำเนินการบันทึกตามขั้นตอนเดิม

## สรุป
คุณมีวิธีที่ครบถ้วนและพร้อมใช้งานในระดับผลิตภัณฑ์เพื่อ **แปลง Word เป็น RTF** ด้วย Aspose.Words for Java โดยการโหลด DOCX, กำหนด `RtfSaveOptions` (รวมถึง **บันทึกรูปภาพเป็น WMF**), และเรียก `doc.save(...)` คุณสามารถสร้างไฟล์ rich‑text คุณภาพสูงที่ทำงานได้ทุกที่ อย่าลืมสำรวจตัวเลือกการบันทึกเพิ่มเติมเพื่อปรับผลลัพธ์ให้ตรงกับความต้องการของคุณ

---

**อัปเดตล่าสุด:** 2025-12-24  
**ทดสอบกับ:** Aspose.Words for Java 24.12  
**ผู้เขียน:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}