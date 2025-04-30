---
"description": "เรียนรู้วิธีการสร้างและปรับแต่งสารบัญ (TOC) โดยใช้ Aspose.Words สำหรับ Java สร้างเอกสารที่เป็นระเบียบและเป็นมืออาชีพได้อย่างง่ายดาย"
"linktitle": "การสร้างสารบัญ"
"second_title": "API การประมวลผลเอกสาร Java ของ Aspose.Words"
"title": "การสร้างสารบัญใน Aspose.Words สำหรับ Java"
"url": "/th/java/document-manipulation/generating-table-of-contents/"
"weight": 21
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# การสร้างสารบัญใน Aspose.Words สำหรับ Java


## บทนำสู่การสร้างสารบัญใน Aspose.Words สำหรับ Java

ในบทช่วยสอนนี้ เราจะแนะนำคุณเกี่ยวกับขั้นตอนการสร้างสารบัญ (TOC) โดยใช้ Aspose.Words สำหรับ Java สารบัญเป็นฟีเจอร์สำคัญในการสร้างเอกสารที่เป็นระเบียบ เราจะครอบคลุมถึงวิธีการปรับแต่งรูปลักษณ์และเค้าโครงของสารบัญ

## ข้อกำหนดเบื้องต้น

ก่อนที่คุณจะเริ่มต้น ตรวจสอบให้แน่ใจว่าคุณได้ติดตั้งและตั้งค่า Aspose.Words สำหรับ Java ในโปรเจ็กต์ Java ของคุณแล้ว

## ขั้นตอนที่ 1: สร้างเอกสารใหม่

ก่อนอื่นให้สร้างเอกสารใหม่เพื่อใช้งาน

```java
Document doc = new Document();
```

## ขั้นตอนที่ 2: ปรับแต่งรูปแบบ TOC

หากต้องการปรับแต่งลักษณะของ TOC คุณสามารถปรับเปลี่ยนรูปแบบที่เกี่ยวข้องได้ ในตัวอย่างนี้ เราจะทำให้รายการ TOC ระดับแรกเป็นตัวหนา

```java
doc.getStyles().getByStyleIdentifier(StyleIdentifier.TOC_1).getFont().setBold(true);
```

## ขั้นตอนที่ 3: เพิ่มเนื้อหาลงในเอกสารของคุณ

คุณสามารถเพิ่มเนื้อหาลงในเอกสารได้ เนื้อหานี้จะถูกใช้เพื่อสร้าง TOC

## ขั้นตอนที่ 4: สร้าง TOC

หากต้องการสร้าง TOC ให้แทรกฟิลด์ TOC ในตำแหน่งที่ต้องการในเอกสารของคุณ ฟิลด์นี้จะถูกเติมโดยอัตโนมัติตามหัวเรื่องและรูปแบบในเอกสารของคุณ

```java
// แทรกช่อง TOC ในตำแหน่งที่ต้องการในเอกสารของคุณ
FieldToc fieldToc = new FieldToc();
doc.getFirstSection().getBody().getFirstParagraph().appendChild(fieldToc);
```

## ขั้นตอนที่ 5: บันทึกเอกสาร

สุดท้ายให้บันทึกเอกสารพร้อมกับ TOC

```java
doc.save("your_output_path_here");
```

## การปรับแต่งแท็บหยุดใน TOC

คุณสามารถปรับแต่งแท็บหยุดใน TOC ของคุณเพื่อควบคุมเค้าโครงของหมายเลขหน้าได้ ต่อไปนี้คือวิธีเปลี่ยนแท็บหยุด:

```java
Document doc = new Document("Table of contents.docx");

for (Paragraph para : (Iterable<Paragraph>) doc.getChildNodes(NodeType.PARAGRAPH, true))
{
    if (para.getParagraphFormat().getStyle().getStyleIdentifier() >= StyleIdentifier.TOC_1 &&
        para.getParagraphFormat().getStyle().getStyleIdentifier() <= StyleIdentifier.TOC_9)
    {
        // รับแท็บแรกที่ใช้ในย่อหน้านี้ ซึ่งจะจัดตำแหน่งหมายเลขหน้า
        TabStop tab = para.getParagraphFormat().getTabStops().get(0);
        
        // ถอดแถบเก่าออก
        para.getParagraphFormat().getTabStops().removeByPosition(tab.getPosition());
        
        // แทรกแท็บใหม่ในตำแหน่งที่แก้ไข (เช่น 50 หน่วยทางด้านซ้าย)
        para.getParagraphFormat().getTabStops().add(tab.getPosition() - 50.0, tab.getAlignment(), tab.getLeader());
    }
}

doc.save("output.docx");
```

ขณะนี้คุณมีสารบัญที่กำหนดเองในเอกสารของคุณพร้อมแท็บหยุดที่ได้รับการปรับแต่งสำหรับการจัดตำแหน่งหมายเลขหน้าแล้ว


## บทสรุป

ในบทช่วยสอนนี้ เราได้ศึกษาวิธีการสร้างสารบัญ (TOC) โดยใช้ Aspose.Words สำหรับ Java ซึ่งเป็นไลบรารีที่มีประสิทธิภาพสำหรับการทำงานกับเอกสาร Word สารบัญที่มีโครงสร้างที่ดีถือเป็นสิ่งสำคัญสำหรับการจัดระเบียบและการนำทางเอกสารยาวๆ และ Aspose.Words มอบเครื่องมือสำหรับการสร้างและปรับแต่งสารบัญได้อย่างง่ายดาย

## คำถามที่พบบ่อย

### ฉันจะเปลี่ยนการจัดรูปแบบของรายการ TOC ได้อย่างไร?

คุณสามารถปรับเปลี่ยนรูปแบบที่เกี่ยวข้องกับระดับ TOC ได้โดยใช้ `doc.getStyles().getByStyleIdentifier(StyleIdentifier.TOC_X)`โดยที่ X คือระดับ TOC

### ฉันจะเพิ่มระดับเพิ่มเติมให้กับ TOC ของฉันได้อย่างไร

หากต้องการรวมระดับเพิ่มเติมใน TOC คุณสามารถปรับเปลี่ยนช่อง TOC และระบุจำนวนระดับที่ต้องการได้

### ฉันสามารถเปลี่ยนตำแหน่งแท็บสต็อปสำหรับรายการ TOC เฉพาะได้หรือไม่

ใช่ ตามที่แสดงในตัวอย่างโค้ดด้านบน คุณสามารถเปลี่ยนตำแหน่งแท็บสต็อปสำหรับรายการ TOC เฉพาะได้ โดยการวนซ้ำผ่านย่อหน้าและแก้ไขแท็บสต็อปตามนั้น


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}