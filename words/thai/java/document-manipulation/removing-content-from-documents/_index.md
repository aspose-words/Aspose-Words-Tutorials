---
title: การลบเนื้อหาออกจากเอกสารใน Aspose.Words สำหรับ Java
linktitle: การลบเนื้อหาออกจากเอกสาร
second_title: API การประมวลผลเอกสาร Java ของ Aspose.Words
description: เรียนรู้วิธีลบเนื้อหาออกจากเอกสาร Word ใน Java โดยใช้ Aspose.Words สำหรับ Java ลบการแบ่งหน้า การแบ่งส่วน และอื่นๆ เพิ่มประสิทธิภาพการประมวลผลเอกสารของคุณ
weight: 16
url: /th/java/document-manipulation/removing-content-from-documents/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# การลบเนื้อหาออกจากเอกสารใน Aspose.Words สำหรับ Java


## บทนำสู่ Aspose.Words สำหรับ Java

ก่อนที่เราจะเจาะลึกเทคนิคการลบ เรามาทำความรู้จัก Aspose.Words สำหรับ Java กันก่อน Aspose.Words เป็น Java API ที่ให้คุณสมบัติมากมายสำหรับการทำงานกับเอกสาร Word คุณสามารถสร้าง แก้ไข แปลง และจัดการเอกสาร Word ได้อย่างราบรื่นโดยใช้ไลบรารีนี้

## การลบตัวแบ่งหน้า

การแบ่งหน้ามักใช้เพื่อควบคุมเค้าโครงของเอกสาร อย่างไรก็ตาม อาจมีบางกรณีที่คุณจำเป็นต้องลบการแบ่งหน้าออก นี่คือวิธีลบการแบ่งหน้าโดยใช้ Aspose.Words สำหรับ Java:

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

โค้ดชิ้นนี้จะวนซ้ำผ่านย่อหน้าต่างๆ ในเอกสาร ตรวจสอบการแบ่งหน้าและลบการแบ่งหน้าออก

## การลบตัวแบ่งส่วน

การแบ่งส่วนจะแบ่งเอกสารออกเป็นส่วนต่างๆ ที่มีการจัดรูปแบบที่แตกต่างกัน หากต้องการลบการแบ่งส่วน ให้ทำตามขั้นตอนเหล่านี้:

```java
for (int i = doc.getSections().getCount() - 2; i >= 0; i--) {
    doc.getLastSection().prependContent(doc.getSections().get(i));
    doc.getSections().get(i).remove();
}
```

โค้ดนี้จะวนซ้ำผ่านส่วนต่างๆ ในลำดับย้อนกลับ โดยรวมเนื้อหาของส่วนปัจจุบันเข้ากับส่วนสุดท้าย แล้วจึงลบส่วนที่คัดลอกมา

## การลบส่วนท้าย

ส่วนท้ายในเอกสาร Word มักมีหมายเลขหน้า วันที่ หรือข้อมูลอื่นๆ หากคุณต้องการลบส่วนท้ายเหล่านี้ คุณสามารถใช้โค้ดต่อไปนี้:

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

โค้ดนี้จะลบส่วนท้ายทุกประเภท (ส่วนแรก ส่วนหลัก และส่วนคู่) จากแต่ละส่วนในเอกสาร

## การลบสารบัญ

ฟิลด์สารบัญ (TOC) จะสร้างตารางแบบไดนามิกที่แสดงหัวข้อและหมายเลขหน้า หากต้องการลบ TOC คุณสามารถใช้โค้ดต่อไปนี้:

```java
Document doc = new Document("Your Directory Path" + "Table of contents.docx");
removeTableOfContents(doc, 0);
doc.save("Your Directory Path" + "RemoveContent.RemoveToc.doc");
```

 โค้ดนี้กำหนดวิธีการ`removeTableOfContents` ที่ลบ TOC ที่ระบุออกจากเอกสาร


## บทสรุป

ในบทความนี้ เราได้ศึกษาวิธีการลบเนื้อหาประเภทต่างๆ ออกจากเอกสาร Word โดยใช้ Aspose.Words สำหรับ Java ไม่ว่าจะเป็นการแบ่งหน้า การแบ่งส่วน ส่วนท้าย หรือสารบัญ Aspose.Words ก็มีเครื่องมือต่างๆ ที่ช่วยจัดการเอกสารของคุณได้อย่างมีประสิทธิภาพ

## คำถามที่พบบ่อย

### ฉันจะลบตัวแบ่งหน้าที่เฉพาะเจาะจงได้อย่างไร

หากต้องการลบตัวแบ่งหน้าที่เฉพาะเจาะจง ให้ทำซ้ำผ่านย่อหน้าต่างๆ ในเอกสารของคุณ และล้างแอตทริบิวต์ตัวแบ่งหน้าสำหรับย่อหน้าที่ต้องการ

### ฉันสามารถลบส่วนหัวและส่วนท้ายออกได้หรือไม่

ใช่ คุณสามารถลบทั้งส่วนหัวและส่วนท้ายออกจากเอกสารของคุณได้โดยทำตามแนวทางเดียวกันตามที่แสดงในบทความสำหรับส่วนท้าย

### Aspose.Words สำหรับ Java เข้ากันได้กับรูปแบบเอกสาร Word ล่าสุดหรือไม่

ใช่ Aspose.Words สำหรับ Java รองรับรูปแบบเอกสาร Word ล่าสุด ช่วยให้มั่นใจได้ว่าจะเข้ากันได้กับเอกสารสมัยใหม่

### Aspose.Words สำหรับ Java มีฟีเจอร์จัดการเอกสารอื่น ๆ อะไรอีกบ้าง?

Aspose.Words สำหรับ Java มีคุณสมบัติมากมาย เช่น การสร้างเอกสาร การแก้ไข การแปลง และอื่นๆ คุณสามารถสำรวจเอกสารประกอบเพื่อดูข้อมูลโดยละเอียด
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
