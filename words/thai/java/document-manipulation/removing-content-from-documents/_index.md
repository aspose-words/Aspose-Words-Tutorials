---
date: 2026-01-06
description: เรียนรู้วิธีลบส่วนท้ายจากเอกสาร Word ด้วย Aspose.Words for Java รวมถึงวิธีลบการแบ่งส่วน
  การแบ่งหน้า และอื่น ๆ อีกมากมาย
linktitle: Removing Content from Documents
second_title: Aspose.Words Java Document Processing API
title: วิธีลบส่วนท้ายจากเอกสาร Word ด้วย Aspose.Words สำหรับ Java
url: /th/java/document-manipulation/removing-content-from-documents/
weight: 16
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# วิธีการลบส่วนท้าย (footer) จากเอกสาร Word ด้วย Aspose.Words for Java

## แนะนำ Aspose.Words for Java

ในบทเรียนนี้คุณจะได้เรียนรู้ **วิธีลบส่วนท้ายจากไฟล์ Word** อย่างเป็นโปรแกรมด้วย Aspose.Words for Java ไม่ว่าคุณจะต้องทำความสะอาดรายงานที่สร้างอัตโนมัติ, กำจัดข้อมูลที่เป็นความลับ, หรือเพียงแค่ทำให้เทมเพลตดูเรียบร้อย คู่มือนี้จะพาคุณผ่านสถานการณ์การลบเนื้อหาที่พบบ่อยที่สุด—การแบ่งหน้า, การแบ่งส่วน, ส่วนท้าย, และสารบัญ. เริ่มกันเลย!

## คำตอบสั้น
- **ฉันสามารถลบส่วนท้ายโดยไม่กระทบเนื้อหาอื่นได้หรือไม่?** ได้, API ให้คุณเลือกโหนดส่วนท้ายเท่านั้น.
- **ต้องมีลิขสิทธิ์เพื่อรันตัวอย่างเหล่านี้หรือไม่?** เวอร์ชันทดลองฟรีใช้ได้สำหรับการพัฒนา; ต้องมีลิขสิทธิ์สำหรับการใช้งานจริง.
- **รองรับรูปแบบไฟล์ Word ใดบ้าง?** DOC, DOCX, DOCM, และรูปแบบที่อิง OOXML.
- **โค้ดนี้เข้ากันได้กับ Java 8 ขึ้นไปหรือไม่?** แน่นอน, ไลบรารีรองรับ Java ตั้งแต่เวอร์ชัน 8 เป็นต้นไป.
- **จะลบการแบ่งส่วนอย่างไร?** ดูส่วน “วิธีลบการแบ่งส่วน” ด้านล่าง.

## “remove footers from Word” คืออะไร?

การลบส่วนท้ายจากเอกสาร Word หมายถึงการลบโหนด `HeaderFooter` ที่ปรากฏที่ด้านล่างของแต่ละหน้า การทำเช่นนี้มักใช้เมื่อคุณต้องการเลย์เอาต์ที่มีแค่หัวเรื่องหรือเมื่อส่วนท้ายมีข้อมูลที่เป็นความลับและไม่ควรเผยแพร่.

## ทำไมต้องใช้ Aspose.Words for Java สำหรับงานนี้?

Aspose.Words มีโมเดลอ็อบเจกต์ระดับสูงที่ทำให้ซับซ้อนของรูปแบบไฟล์ DOCX ง่ายขึ้น คุณสามารถจัดการกับย่อหน้า, รัน, ส่วน, และส่วนท้ายได้ด้วยไม่กี่บรรทัดของโค้ด Java โดยไม่ต้องติดตั้ง Microsoft Word บนเซิร์ฟเวอร์.

## สิ่งที่ต้องเตรียม
- Java Development Kit (JDK) 8 หรือใหม่กว่า.
- ไลบรารี Aspose.Words for Java (ดาวน์โหลดจากเว็บไซต์ Aspose).
- ตัวอย่างไฟล์ Word (`Document.docx`) ที่วางไว้ในโฟลเดอร์ที่รู้จัก.

## การลบการแบ่งหน้า

การแบ่งหน้าควบคุมการจัดหน้า แต่บางครั้งต้องการลบออก โค้ดต่อไปนี้จะสแกนทุกย่อหน้า, ล้างแฟล็ก `PageBreakBefore`, และลบอักขระการแบ่งหน้าที่เป็นแบบชัดเจน.

```java
Document doc = new Document("Your Directory Path" + "Document.docx");
NodeCollection paragraphs = doc.getChildNodes(NodeType.PARAGRAPH, true);
for (Paragraph para : (Iterable<Paragraph>) paragraphs) {
    if (para.getParagraphFormat().getPageBreakBefore()) {
        para.getParagraphFormat().setPageBreakBefore(false);
    }
    for (Run run : para.getRuns()) {
        if (run.getText().contains(ControlChar.PAGE_BREAK)) {
            run.setText(run.getText().replace(ControlChar.PAGE_BREAK, ""));
        }
    }
}
doc.save("Your Directory Path" + "RemoveContent.RemovePageBreaks.docx");
```

*เคล็ดลับ:* ให้รันโค้ดนี้ก่อนลบส่วนท้ายหากต้องการเลย์เอาต์หน้าเดียว.

## วิธีลบการแบ่งส่วน

การแบ่งส่วนทำให้เอกสารถูกแยกเป็นส่วนอิสระแต่ละส่วนมีหัวเรื่อง, ส่วนท้าย, และการตั้งค่าหน้าเฉพาะ การรวมส่วนและ **ลบการแบ่งส่วน** ทำได้โดยวนลูปย้อนกลับ, นำเนื้อหาของแต่ละส่วนก่อนหน้ามาต่อหน้าสุดท้าย, แล้วลบส่วนที่ว่างเปล่าออก.

```java
for (int i = doc.getSections().getCount() - 2; i >= 0; i--) {
    doc.getLastSection().prependContent(doc.getSections().get(i));
    doc.getSections().get(i).remove();
}
```

วิธีนี้จะคงเนื้อหาทั้งหมดไว้ขณะกำจัดการแบ่งโครงสร้าง.

## การลบส่วนท้าย (เป้าหมายหลัก: remove footers from Word)

ส่วนท้ายมักมีหมายเลขหน้า, วันที่, หรือบันทึกที่เป็นความลับ โค้ดด้านล่างจะลบ **ประเภทส่วนท้ายทั้งหมด**—ส่วนแรก, ส่วนหลัก, และแม้กระทั่งส่วนของหน้าอื่น ๆ—จากทุกส่วน.

```java
Document doc = new Document("Your Directory Path" + "Header and footer types.docx");
for (Section section : doc.getSections()) {
    HeaderFooter footer = section.getHeadersFooters().getByHeaderFooterType(HeaderFooterType.FOOTER_FIRST);
    footer.remove();
    footer = section.getHeadersFooters().getByHeaderFooterType(HeaderFooterType.FOOTER_PRIMARY);
    footer.remove();
    footer = section.getHeadersFooters().getByHeaderFooterType(HeaderFooterType.FOOTER_EVEN);
    footer.remove();
}
doc.save("Your Directory Path" + "RemoveContent.RemoveFooters.docx");
```

หลังจากรันโค้ดนี้ เอกสารที่ได้จะ **ไม่มีส่วนท้าย** ทั้งหมด ทำให้บรรลุเป้าหมายหลักของ “remove footers from Word”.

## การลบสารบัญ

สารบัญ (TOC) ถูกเก็บเป็นฟิลด์ เพื่อจะลบให้ค้นหาฟิลด์ TOC ตามดัชนีและลบโหนดที่เกี่ยวข้อง.

```java
Document doc = new Document("Your Directory Path" + "Table of contents.docx");
removeTableOfContents(doc, 0);
doc.save("Your Directory Path" + "RemoveContent.RemoveToc.doc");
```

*(เมธอด `removeTableOfContents` เป็นส่วนหนึ่งของตัวอย่าง Aspose.Words และทำหน้าที่ลบโหนด TOC ที่ระบุ.)*

## ปัญหาทั่วไปและการแก้ไข

| อาการ | สาเหตุที่เป็นไปได้ | วิธีแก้ |
|-------|-------------------|----------|
| ส่วนท้ายยังคงปรากฏหลังรันโค้ด | เอกสารมีคู่ **header/footer** ที่ไม่ได้เข้าถึง (เช่น `FOOTER_FIRST` หาย) | วนลูปผ่านค่าทั้งหมดของ `HeaderFooterType` หรือเช็ค `null` ก่อนเรียก `remove()` |
| การจัดหน้าเปลี่ยนแปลงโดยไม่คาดคิดหลังลบการแบ่งส่วน | การตั้งค่าหน้าเฉพาะของส่วน (margin, orientation) หายไป | คัดลอกการตั้งค่าของส่วนไปยังส่วนเป้าหมายก่อนลบ |
| ไม่ลบ `ControlChar.PAGE_BREAK` | เอกสารใช้ **section breaks** แทนการแบ่งหน้าด้วยอักขระ | ใช้วิธี “วิธีลบการแบ่งส่วน” ก่อนเป็นอันดับแรก |

## คำถามที่พบบ่อย

**ถาม:** ฉันสามารถลบเฉพาะส่วนท้ายบางส่วนได้หรือไม่ (เช่น ส่วนท้ายหน้าแรกเท่านั้น)?  
**ตอบ:** ได้. ดึงส่วนท้ายตามประเภท (`FOOTER_FIRST`) แล้วเรียก `remove()` เฉพาะอินสแตนซ์นั้น.

**ถาม:** จะลบการแบ่งส่วนโดยไม่ต้องรวมเนื้อหาอย่างไร?  
**ตอบ:** สามารถลบโหนด `Section` โดยตรงได้หากไม่ต้องการเก็บเนื้อหา, แต่ต้องระวังว่าหัวเรื่อง/ส่วนท้ายที่แนบกับส่วนนั้นจะหายไปด้วย.

**ถาม:** สามารถตรวจจับว่าเอกสารมี TOC ก่อนจะลบได้หรือไม่?  
**ตอบ:** ใช้ `doc.getRange().getFields()` แล้วตรวจสอบฟิลด์ที่มีประเภท `FieldType.FIELD_TABLE_OF_CONTENTS`.

**ถาม:** Aspose.Words รองรับการลบส่วนท้ายจากไฟล์ Word ที่เข้ารหัสหรือไม่?  
**ตอบ:** รองรับ, เพียงเปิดเอกสารพร้อมรหัสผ่าน: `new Document(path, new LoadOptions(password))`.

**ถาม:** การลบส่วนท้ายจะส่งผลต่อการแบ่งหน้าในเอกสารหรือไม่?  
**ตอบ:** การลบส่วนท้ายไม่ทำให้หมายเลขหน้าต่างเปลี่ยนเว้นแต่ส่วนท้ายเองมีฟิลด์หมายเลขหน้า. หากต้องการจัดหมายเลขหน้าใหม่ ให้อัปเดตฟิลด์หมายเลขหน้าให้สอดคล้อง.

## สรุป

เราได้ครอบคลุมทุกอย่างที่คุณต้องการ **remove footers from Word** ด้วย Aspose.Words for Java รวมถึงงานที่เกี่ยวข้องเช่นการลบการแบ่งหน้า, **how to delete section breaks**, และการลบสารบัญ ด้วยการใช้สแนปช็อตเหล่านี้ คุณสามารถสร้างเอกสารที่สะอาดและเป็นมืออาชีพตามความต้องการของแอปพลิเคชันของคุณได้.

---

**อัปเดตล่าสุด:** 2026-01-06  
**ทดสอบกับ:** Aspose.Words for Java 24.12  
**ผู้เขียน:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
