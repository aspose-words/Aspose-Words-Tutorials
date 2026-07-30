---
date: 2026-02-14
description: เรียนรู้วิธีการแสดงคณิตศาสตร์แบบอินไลน์, แทรกสมการคณิตศาสตร์และจัดการวัตถุ
  Office Math อย่างง่ายดายด้วย Aspose.Words for Java.
linktitle: Using Office Math Objects
second_title: Aspose.Words Java Document Processing API
title: แสดงคณิตศาสตร์แบบอินไลน์ด้วย Office Math ใน Aspose.Words สำหรับ Java
url: /th/java/document-conversion-and-export/using-office-math-objects/
weight: 13
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# แสดงสมการคณิตศาสตร์แบบอินไลน์ด้วย Office Math ใน Aspose.Words for Java

ในบทแนะนำที่ครอบคลุมนี้ คุณจะได้เรียนรู้วิธี **display math inline** โดยใช้วัตถุ Office Math ใน Aspose.Words for Java ไม่ว่าคุณจะต้อง **insert math equation** ลงในรายงานหรือปรับแต่งรูปแบบของสูตรที่ซับซ้อน คู่มือนี้จะพาคุณผ่านทุกขั้นตอน—from loading a Word document to saving the final result.

## คำตอบอย่างรวดเร็ว
- **What does “display math inline” mean?** สมการจะแสดงอยู่ในกระแสข้อความ ไม่ได้อยู่บนบรรทัดแยก  
- **Which class represents a math object?** `OfficeMath` ใน Aspose.Words API.  
- **Can I change the alignment?** ใช่, ใช้ `setJustification` กับ LEFT, CENTER หรือ RIGHT.  
- **Do I need a license for this feature?** จำเป็นต้องมีใบอนุญาต Aspose.Words for Java ที่ถูกต้องสำหรับการใช้งานในสภาพแวดล้อมการผลิต.  
- **What version is demonstrated?** โค้ดทำงานกับรุ่นล่าสุดของ Aspose.Words for Java (2026).

## “display math inline” คืออะไร?
การแสดงสมการแบบอินไลน์หมายถึงสมการถูกจัดเป็นส่วนหนึ่งของข้อความในย่อหน้า ทำให้สามารถตัดบรรทัดได้อย่างเป็นธรรมชาติร่วมกับคำรอบข้าง ซึ่งเป็นประโยชน์สำหรับสูตรสั้นที่ไม่ควรทำให้การอ่านขัดจังหวะ.

## ทำไมต้องใช้วัตถุ Office Math ใน Aspose.Words for Java?
- **Precise control** การควบคุมการจัดวางสมการ (inline vs. display).  
- **Programmatic manipulation** การจัดการสมการโดยโปรแกรมโดยไม่ต้องเปิด Word ด้วยตนเอง.  
- **Consistent rendering** การแสดงผลที่สอดคล้องกันบนหลายแพลตฟอร์ม เหมาะสำหรับการสร้างรายงานอัตโนมัติ.

## ข้อกำหนดเบื้องต้น
ก่อนที่เราจะเริ่ม ควรตรวจสอบว่าคุณมี:

- Aspose.Words for Java ที่ติดตั้งและอ้างอิงในโปรเจกต์ของคุณ  
- ไฟล์ Word ที่มีสมการ Office Math อยู่แล้ว (เช่น `OfficeMath.docx`)  
- ใบอนุญาตที่ถูกต้องหากคุณต้องการรันโค้ดนอกโหมดประเมินผล

## คู่มือแบบขั้นตอน

### โหลดเอกสาร
ขั้นแรก โหลดเอกสารที่มีสมการ Office Math ที่คุณต้องการทำงานด้วย:

```java
Document doc = new Document("Your Directory Path" + "OfficeMath.docx");
```

### เข้าถึงวัตถุ Office Math
ดึงโหนด Office Math ตัวแรกจากเอกสาร:

```java
OfficeMath officeMath = (OfficeMath) doc.getChild(NodeType.OFFICE_MATH, 0, true);
```

### ตั้งค่าชนิดการแสดงผล (Inline vs. Display)
ควบคุมว่สมการจะแสดงแบบอินไลน์กับข้อความรอบข้างหรือบนบรรทัดแยก สำหรับ **display math inline** ให้ใช้ค่า enum `INLINE`; หากต้องการบรรทัดแยกให้ใช้ `DISPLAY`:

```java
officeMath.setDisplayType(OfficeMathDisplayType.DISPLAY);
```

*หากคุณต้องการให้สมการอยู่ในรูปแบบอินไลน์ ให้เปลี่ยน `DISPLAY` เป็น `INLINE`.*

### ตั้งค่า Justification
ปรับการจัดตำแหน่งของสมการ ด้านล่างเราได้จัดตำแหน่งไปทางซ้าย แต่คุณสามารถเลือก `CENTER` หรือ `RIGHT` ได้เช่นกัน:

```java
officeMath.setJustification(OfficeMathJustification.LEFT);
```

### บันทึกเอกสารที่แก้ไขแล้ว
สุดท้าย เขียนการเปลี่ยนแปลงกลับไปยังไฟล์ใหม่:

```java
doc.save("Your Directory Path" + "ModifiedOfficeMath.docx");
```

## โค้ดต้นฉบับเต็มสำหรับการใช้วัตถุ Office Math ใน Aspose.Words for Java

```java
        Document doc = new Document("Your Directory Path" + "Office math.docx");
        OfficeMath officeMath = (OfficeMath) doc.getChild(NodeType.OFFICE_MATH, 0, true);
        // OfficeMath display type represents whether an equation is displayed inline with the text or displayed on its line.
        officeMath.setDisplayType(OfficeMathDisplayType.DISPLAY);
        officeMath.setJustification(OfficeMathJustification.LEFT);
        doc.save("Your Directory Path" + "WorkingWithOfficeMath.MathEquations.docx");
```

## ปัญหาที่พบบ่อยและการแก้ไข
- **Equation not found:** ตรวจสอบว่าเอกสารมีวัตถุ Office Math อยู่จริง; หากไม่มี `doc.getChild` จะคืนค่า `null`.  
- **Display type has no effect:** ยืนยันว่าคุณใช้รุ่นล่าสุดของ Aspose.Words; รุ่นเก่าอาจรองรับ `OfficeMathDisplayType` ไม่เต็มที่.  
- **License exception:** หากพบข้อผิดพลาดเกี่ยวกับใบอนุญาต ตรวจสอบให้แน่ใจว่าไฟล์ใบอนุญาตโหลดอย่างถูกต้องก่อนสร้างอินสแตนซ์ `Document`.

## คำถามที่พบบ่อย

**ถาม: ออบเจ็กต์ Office Math ใน Aspose.Words สำหรับ Java มีจุดประสงค์อะไร**
ตอบ: Office Math object ให้คุณแสดงและการจัดการสมการคณิตศาสตร์โดยโปรแกรม ให้คุณควบคุมและรูปแบบต่างๆ ได้

**ถาม: ฉันสามารถจัดแนวสมการ Office Math ให้แตกต่างออกไปภายในเอกสารของฉันได้หรือไม่**
ตอบ: ทำได้ ใช้เมธอด `setJustification` เพื่อจัดตำแหน่งด้านซ้าย ถูกต้องหรือกลาง

**ถาม: Aspose.Words สำหรับ Java เหมาะสำหรับการจัดการเอกสารทางคณิตศาสตร์ที่ซับซ้อนหรือไม่**
A: แน่นอน. รองรับการรองรับนี้ของสมการเทรลเลอร์, คุณสมบัติของชั้นลอย, ความสามารถในการรับรู้เรื่องราวต่างๆ มากมาย

**ถาม: ฉันจะเรียนรู้เพิ่มเติมเกี่ยวกับ Aspose.Words สำหรับ Java ได้อย่างไร**
ตอบ: สำหรับเอกสารและการเก็บรักษาอย่างครบถ้วนไม่จำเป็นต้องมีอีกต่อไป [Aspose.Words for Java Documentation](https://reference.aspose.com/words/java/)

**ถาม: ฉันจะดาวน์โหลด Aspose.Words สำหรับ Java ได้ที่ไหน** 
A: คุณสามารถดาวน์โหลด Aspose.Words for Java ได้จากเว็บไซต์: [Download Aspose.Words for Java](https://releases.aspose.com/words/java/).

---

**อัปเดตล่าสุด:** 2026-02-14  
**ทดสอบด้วย:** Aspose.Words for Java 24.12 (latest as of Feb 2026)  
**ผู้เขียน:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}