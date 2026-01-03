---
date: 2026-01-03
description: เรียนรู้วิธีปรับเลขหน้าในขณะแทรกสารบัญโดยใช้ Aspose.Words for Java ปรับแต่งสไตล์ของสารบัญและสร้างเอกสารได้อย่างง่ายดาย.
linktitle: Generating Table of Contents
second_title: Aspose.Words Java Document Processing API
title: ปรับหมายเลขหน้าและสร้างสารบัญด้วย Aspose.Words สำหรับ Java
url: /th/java/document-manipulation/generating-table-of-contents/
weight: 21
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# ปรับหมายเลขหน้าและสร้างสารบัญใน Aspose.Words for Java

ในบทแนะนำนี้คุณจะได้เรียนรู้วิธี **ปรับหมายเลขหน้า** และ **แทรกสารบัญ** (TOC) ด้วย Aspose.Words for Java. สารบัญที่จัดโครงสร้างอย่างดีทำให้เอกสารยาวง่ายต่อการนำทาง, และการปรับการจัดตำแหน่งหมายเลขหน้าให้ตรงตามต้องการจะมอบประสบการณ์ระดับมืออาชีพให้ผู้อ่าน เราจะเดินผ่านการสร้างเอกสาร, ปรับสไตล์ของ TOC, และแก้ไข tab stop เพื่อให้หมายเลขหน้าตรงกับตำแหน่งที่ต้องการ

## คำตอบสั้น
- **“ปรับหมายเลขหน้า” หมายถึงอะไร?** การแก้ไข tab stop ที่จัดตำแหน่งหมายเลขหน้าในสารบัญ.  
- **ฉันสามารถแทรกสารบัญโดยอัตโนมัติได้หรือไม่?** ได้ – ใช้คลาส `FieldToc`.  
- **ต้องมีลิขสิทธิ์เพื่อรันโค้ดหรือไม่?** เวอร์ชันทดลองฟรีใช้ได้สำหรับการพัฒนา; ต้องมีลิขสิทธิ์สำหรับการใช้งานจริง.  
- **รองรับเวอร์ชันของ Aspose ใด?** ตัวอย่างทำงานกับรุ่นล่าสุดของ Aspose.Words for Java.  
- **สามารถปรับสไตล์ของ TOC ได้หรือไม่?** แน่นอน – คุณสามารถเปลี่ยนฟอนต์, ความหนา, และอื่น ๆ.

## TOC คืออะไรใน Aspose.Words?
TOC คือฟิลด์ที่สแกนเอกสารเพื่อค้นหา style ของหัวเรื่อง (เช่น Heading 1, Heading 2) แล้วสร้างรายการพร้อมหมายเลขหน้า Aspose.Words ให้คุณแทรกฟิลด์นี้โดยโปรแกรมและควบคุมลักษณะการแสดงผลได้อย่างเต็มที่

## ทำไมต้องปรับหมายเลขหน้าใน TOC?
การปรับ tab stop ให้คุณควบคุมตำแหน่งของหมายเลขหน้าได้อย่างแม่นยำ, ซึ่งสำคัญสำหรับ:

- รักษาเลย์เอาต์คอลัมน์ที่เรียบร้อย.  
- ปฏิบัติตามแนวทางสไตล์ขององค์กร.  
- ปรับปรุงความอ่านง่ายในเอกสารที่พิมพ์และดิจิทัล.

## ข้อกำหนดเบื้องต้น
- เพิ่ม Aspose.Words for Java ลงในโปรเจกต์ของคุณ (Maven/Gradle).  
- มีความคุ้นเคยพื้นฐานกับไวยากรณ์ Java.

## คู่มือขั้นตอนโดยละเอียด

### ขั้นตอนที่ 1: สร้างเอกสารใหม่
ก่อนอื่นให้สร้างอ็อบเจ็กต์ `Document` ว่างที่ใช้เก็บเนื้อหาและ TOC ของคุณ

```java
Document doc = new Document();
```

### ขั้นตอนที่ 2: ปรับสไตล์ของ TOC
คุณสามารถเปลี่ยนลักษณะของแต่ละระดับของ TOC ได้ ในตัวอย่างนี้เราทำให้รายการระดับแรกเป็นตัวหนา, ซึ่งเป็นคำขอการจัดรูปแบบที่พบบ่อย

```java
doc.getStyles().getByStyleIdentifier(StyleIdentifier.TOC_1).getFont().setBold(true);
```

### ขั้นตอนที่ 3: เพิ่มเนื้อหาในเอกสารของคุณ
แทรกหัวเรื่อง (เช่น `Heading1`, `Heading2`) และย่อหน้าปกติ. ฟิลด์ TOC จะดึงหัวเรื่องเหล่านี้มาอัตโนมัติ *(โค้ดถูกตัดเพื่อความกระชับ – เน้นที่การสร้าง TOC)*

### ขั้นตอนที่ 4: แทรกฟิลด์ TOC
วาง TOC ไว้ที่ตำแหน่งที่ต้องการ – ปกติจะอยู่ที่จุดเริ่มต้นของเอกสาร

```java
// Insert a TOC field at the desired location in your document.
FieldToc fieldToc = new FieldToc();
doc.getFirstSection().getBody().getFirstParagraph().appendChild(fieldToc);
```

### ขั้นตอนที่ 5: บันทึกเอกสาร
บันทึกเอกสารลงดิสก์ คุณสามารถเลือกฟอร์แมตที่รองรับได้เช่น DOCX, PDF, หรือ HTML

```java
doc.save("your_output_path_here");
```

## การปรับ Tab Stop ใน TOC (ปรับหมายเลขหน้า)
หาก tab stop เริ่มต้นไม่จัดตำแหน่งหมายเลขหน้าให้ตรงตามที่ต้องการ, คุณสามารถวนลูปผ่านย่อหน้าของ TOC ทั้งหมดและแก้ไขตำแหน่ง tab ได้

```java
Document doc = new Document("Table of contents.docx");

for (Paragraph para : (Iterable<Paragraph>) doc.getChildNodes(NodeType.PARAGRAPH, true))
{
    if (para.getParagraphFormat().getStyle().getStyleIdentifier() >= StyleIdentifier.TOC_1 &&
        para.getParagraphFormat().getStyle().getStyleIdentifier() <= StyleIdentifier.TOC_9)
    {
        // Get the first tab used in this paragraph, which aligns the page numbers.
        TabStop tab = para.getParagraphFormat().getTabStops().get(0);
        
        // Remove the old tab.
        para.getParagraphFormat().getTabStops().removeByPosition(tab.getPosition());
        
        // Insert a new tab at a modified position (e.g., 50 units to the left).
        para.getParagraphFormat().getTabStops().add(tab.getPosition() - 50.0, tab.getAlignment(), tab.getLeader());
    }
}

doc.save("output.docx");
```

ตอนนี้รายการ TOC จะแสดงหมายเลขหน้าในตำแหน่งที่คุณกำหนด, ทำให้เอกสารดูเป็นมืออาชีพยิ่งขึ้น

## ปัญหาที่พบบ่อย & เคล็ดลับ
- **หัวเรื่องหายจาก TOC:** ตรวจสอบว่าหัวเรื่องของคุณใช้สไตล์ในตัว (`Heading1`, `Heading2` ฯลฯ) หรือแมพสไตล์ที่กำหนดเองให้กับระดับ TOC.  
- **Tab stop ไม่ทำงาน:** ยืนยันว่าข้อความนั้นอยู่ในสไตล์ของ TOC (`TOC_1`‑`TOC_9`).  
- **ประสิทธิภาพกับเอกสารขนาดใหญ่:** เรียก `doc.updateFields()` หลังจากแทรก TOC เพื่ออัปเดตรายการทั้งหมดในครั้งเดียว.

## คำถามที่พบบ่อย

**ถาม: จะเปลี่ยนรูปแบบของรายการ TOC อย่างไร?**  
ตอบ: ใช้ `doc.getStyles().getByStyleIdentifier(StyleIdentifier.TOC_X)` โดยที่ *X* คือระดับ (1‑9) แล้วแก้ไขฟอนต์, สี, หรือการตั้งค่าพารากราฟ

**ถาม: จะเพิ่มระดับให้กับ TOC ได้อย่างไร?**  
ตอบ: ปรับสวิตช์ของ `FieldToc` เป็น `\o "1-3"` (ตัวอย่าง) เพื่อรวมระดับหัวเรื่องเพิ่มเติม, แล้วอัปเดตสไตล์ `TOC_X` ที่สอดคล้องกัน

**ถาม: สามารถเปลี่ยนตำแหน่ง tab stop สำหรับรายการ TOC เฉพาะได้หรือไม่?**  
ตอบ: ได้ – วนลูปผ่านย่อหน้าตามที่แสดงในส่วน “การปรับ Tab Stop” แล้วแก้ไขแต่ละ tab stop แยกกัน

**ถาม: สามารถสร้าง TOC ในไฟล์ PDF ได้หรือไม่?**  
ตอบ: แน่นอน. บันทึกเอกสารเป็น PDF (`doc.save("output.pdf")`) หลังจากสร้าง TOC; ฟิลด์จะถูกเรนเดอร์โดยอัตโนมัติ

**ถาม: จำเป็นต้องเรียก `updateFields()` ด้วยตนเองหรือไม่?**  
ตอบ: เมื่อแทรก `FieldToc` Aspose.Words จะอัปเดตฟิลด์เมื่อบันทึก, แต่การเรียก `doc.updateFields()` จะให้ผลลัพธ์ทันทีสำหรับการดีบัก

## สรุป
คุณได้เรียนรู้วิธี **ปรับหมายเลขหน้า**, **แทรกสารบัญ**, และ **ปรับสไตล์ของ TOC** ด้วย Aspose.Words for Java เทคนิคเหล่านี้ช่วยให้คุณสร้างเอกสารที่สะอาด, นำทางง่าย, และมีการจัดรูปแบบระดับมืออาชีพตามมาตรฐานการเผยแพร่ใด ๆ

---  

**อัปเดตล่าสุด:** 2026-01-03  
**ทดสอบกับ:** Aspose.Words for Java (รุ่นล่าสุด)  
**ผู้เขียน:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}