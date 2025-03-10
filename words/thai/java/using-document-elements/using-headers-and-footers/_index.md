---
title: การใช้ส่วนหัวและส่วนท้ายใน Aspose.Words สำหรับ Java
linktitle: การใช้ส่วนหัวและส่วนท้าย
second_title: API การประมวลผลเอกสาร Java ของ Aspose.Words
description: เรียนรู้วิธีใช้ส่วนหัวและส่วนท้ายใน Aspose.Words สำหรับ Java ทีละขั้นตอน สร้างเอกสารระดับมืออาชีพได้อย่างง่ายดาย
weight: 16
url: /th/java/using-document-elements/using-headers-and-footers/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# การใช้ส่วนหัวและส่วนท้ายใน Aspose.Words สำหรับ Java


ในคู่มือฉบับสมบูรณ์นี้ เราจะแนะนำคุณเกี่ยวกับกระบวนการใช้งานส่วนหัวและส่วนท้ายใน Aspose.Words สำหรับ Java ส่วนหัวและส่วนท้ายเป็นองค์ประกอบสำคัญในการจัดรูปแบบเอกสาร และ Aspose.Words มอบเครื่องมืออันทรงพลังเพื่อสร้างและปรับแต่งส่วนหัวและส่วนท้ายตามความต้องการของคุณ

ตอนนี้ มาเจาะลึกแต่ละขั้นตอนโดยละเอียดกัน

## 1. บทนำสู่ Aspose.Words

Aspose.Words เป็น Java API ที่ทรงพลังที่ช่วยให้คุณสร้าง จัดการ และแสดงผลเอกสาร Word ได้ด้วยโปรแกรม โดยมีคุณสมบัติมากมายสำหรับการจัดรูปแบบเอกสาร รวมถึงส่วนหัวและส่วนท้าย

## 2. การตั้งค่าสภาพแวดล้อม Java ของคุณ

 ก่อนเริ่มใช้ Aspose.Words โปรดแน่ใจว่าคุณได้ตั้งค่าสภาพแวดล้อมการพัฒนา Java ของคุณอย่างถูกต้องแล้ว คุณสามารถดูคำแนะนำในการตั้งค่าที่จำเป็นได้ที่หน้าเอกสาร Aspose.Words:[เอกสาร Java ของ Aspose.Words](https://reference.aspose.com/words/java/).

## 3. การสร้างเอกสารใหม่

หากต้องการทำงานกับส่วนหัวและส่วนท้าย คุณต้องสร้างเอกสารใหม่โดยใช้ Aspose.Words โค้ดต่อไปนี้จะสาธิตวิธีการดำเนินการดังกล่าว:

```java
// โค้ด Java สำหรับการสร้างเอกสารใหม่
string dataDir = "Your Document Directory";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## 4. ทำความเข้าใจเกี่ยวกับการตั้งค่าหน้า

 การตั้งค่าหน้ากระดาษเป็นสิ่งสำคัญสำหรับการควบคุมเค้าโครงของเอกสารของคุณ คุณสามารถระบุคุณสมบัติต่างๆ ที่เกี่ยวข้องกับส่วนหัวและส่วนท้ายได้โดยใช้`PageSetup` ชั้นเรียน ตัวอย่างเช่น:

```java
// การตั้งค่าคุณสมบัติของหน้า
Section currentSection = builder.getCurrentSection();
PageSetup pageSetup = currentSection.getPageSetup();
pageSetup.setDifferentFirstPageHeaderFooter(true);
pageSetup.setHeaderDistance(20.0);
```

## 5. ส่วนหัว/ส่วนท้ายหน้าแรกที่แตกต่างกัน

Aspose.Words ช่วยให้คุณสามารถมีส่วนหัวและส่วนท้ายที่แตกต่างกันสำหรับหน้าแรกของเอกสารของคุณ ใช้`pageSetup.setDifferentFirstPageHeaderFooter(true);` เพื่อเปิดใช้งานคุณสมบัตินี้

## 6. การทำงานกับส่วนหัว

### 6.1. การเพิ่มข้อความลงในส่วนหัว

 คุณสามารถเพิ่มข้อความลงในส่วนหัวได้โดยใช้`DocumentBuilder`นี่คือตัวอย่าง:

```java
// การเพิ่มข้อความลงในส่วนหัวหน้าแรก
builder.moveToHeaderFooter(HeaderFooterType.HEADER_FIRST);
builder.getParagraphFormat().setAlignment(ParagraphAlignment.CENTER);
builder.getFont().setName("Arial");
builder.getFont().setBold(true);
builder.getFont().setSize(14.0);
builder.write("Aspose.Words Header/Footer Creation Primer - Title Page.");
```

### 6.2. การแทรกภาพลงในส่วนหัว

 หากต้องการแทรกภาพลงในส่วนหัว คุณสามารถใช้`insertImage` วิธีการ นี่คือตัวอย่าง:

```java
// การแทรกภาพลงในส่วนหัว
builder.insertImage(getImagesDir() + "Graphics Interchange Format.gif", RelativeHorizontalPosition.PAGE, 10.0,
    RelativeVerticalPosition.PAGE, 10.0, 50.0, 50.0, WrapType.THROUGH);
```

### 6.3. การปรับแต่งสไตล์ส่วนหัว

คุณสามารถปรับแต่งรูปแบบส่วนหัวได้โดยการตั้งค่าคุณสมบัติต่างๆ เช่น แบบอักษร การจัดตำแหน่ง และอื่นๆ ดังที่แสดงในตัวอย่างด้านบน

## 7. การทำงานกับส่วนท้าย

### 7.1. การเพิ่มข้อความลงในส่วนท้าย

 คล้ายกับส่วนหัว คุณสามารถเพิ่มข้อความลงในส่วนท้ายได้โดยใช้`DocumentBuilder`นี่คือตัวอย่าง:

```java
// การเพิ่มข้อความลงในส่วนท้ายหลัก
builder.moveToHeaderFooter(HeaderFooterType.FOOTER_PRIMARY);
// แทรกข้อความและฟิลด์ตามต้องการ
```

### 7.2. การแทรกภาพลงในส่วนท้าย

 หากต้องการแทรกภาพลงในส่วนท้าย ให้ใช้`insertImage` วิธีการเช่นเดียวกับในส่วนหัว

### 7.3. การปรับแต่งสไตล์ส่วนท้าย

 ปรับแต่งรูปแบบส่วนท้ายโดยใช้`DocumentBuilder`คล้ายกับการปรับแต่งส่วนหัว

## 8. การกำหนดหมายเลขหน้า

 คุณสามารถใส่หมายเลขหน้าในส่วนหัวและส่วนท้ายได้โดยใช้ฟิลด์เช่น`PAGE` และ`NUMPAGES`ฟิลด์เหล่านี้จะอัปเดตโดยอัตโนมัติเมื่อคุณเพิ่มหรือลบหน้า

## 9. ข้อมูลลิขสิทธิ์ในส่วนท้าย

หากต้องการเพิ่มข้อมูลลิขสิทธิ์ลงในส่วนท้ายของเอกสาร คุณสามารถใช้ตารางที่มีเซลล์ 2 เซลล์ โดยจัดตำแหน่งเซลล์หนึ่งชิดซ้ายและอีกเซลล์หนึ่งชิดขวา ดังที่แสดงในตัวอย่างโค้ด

## 10. การทำงานกับหลายส่วน

Aspose.Words ช่วยให้คุณสามารถทำงานกับหลายส่วนภายในเอกสารได้ คุณสามารถตั้งค่าหน้ากระดาษและส่วนหัว/ส่วนท้ายที่แตกต่างกันสำหรับแต่ละส่วนได้

## 11. การวางแนวภูมิทัศน์

คุณสามารถเปลี่ยนทิศทางของส่วนที่เจาะจงให้เป็นโหมดแนวนอนได้หากจำเป็น

## 12. การคัดลอกส่วนหัว/ส่วนท้ายจากส่วนก่อนหน้า

การคัดลอกส่วนหัวและส่วนท้ายจากส่วนก่อนหน้าสามารถประหยัดเวลาในการสร้างเอกสารที่ซับซ้อน

## 13. การบันทึกเอกสารของคุณ

หลังจากสร้างและปรับแต่งเอกสารของคุณแล้วอย่าลืมบันทึกโดยใช้`doc.save()` วิธี.

## ซอร์สโค้ดที่สมบูรณ์
```java
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
        Section currentSection = builder.getCurrentSection();
        PageSetup pageSetup = currentSection.getPageSetup();
        // ระบุว่าเราต้องการให้ส่วนหัว/ส่วนท้ายของหน้าแรกแตกต่างจากหน้าอื่นๆ หรือไม่
        // คุณยังสามารถใช้คุณสมบัติ PageSetup.OddAndEvenPagesHeaderFooter เพื่อระบุ
        // ส่วนหัว/ส่วนท้ายที่แตกต่างกันสำหรับหน้าคี่และหน้าคู่
        pageSetup.setDifferentFirstPageHeaderFooter(true);
        pageSetup.setHeaderDistance(20.0);
        builder.moveToHeaderFooter(HeaderFooterType.HEADER_FIRST);
        builder.getParagraphFormat().setAlignment(ParagraphAlignment.CENTER);
        builder.getFont().setName("Arial");
        builder.getFont().setBold(true);
        builder.getFont().setSize(14.0);
        builder.write("Aspose.Words Header/Footer Creation Primer - Title Page.");
        pageSetup.setHeaderDistance(20.0);
        builder.moveToHeaderFooter(HeaderFooterType.HEADER_PRIMARY);
        // แทรกภาพที่มีตำแหน่งไว้ที่มุมบน/ซ้ายของส่วนหัว
        // ระยะห่างจากขอบบน/ซ้ายของหน้าตั้งไว้ที่ 10 จุด
        builder.insertImage(getImagesDir() + "Graphics Interchange Format.gif", RelativeHorizontalPosition.PAGE, 10.0,
            RelativeVerticalPosition.PAGE, 10.0, 50.0, 50.0, WrapType.THROUGH);
        builder.getParagraphFormat().setAlignment(ParagraphAlignment.RIGHT);
        builder.write("Aspose.Words Header/Footer Creation Primer.");
        builder.moveToHeaderFooter(HeaderFooterType.FOOTER_PRIMARY);
        // เราใช้ตารางที่มีสองเซลล์เพื่อสร้างข้อความส่วนหนึ่งในบรรทัด (พร้อมการใส่หมายเลขหน้า)
        // ให้จัดชิดซ้าย และข้อความส่วนอื่น (มีลิขสิทธิ์) ให้จัดชิดขวา
        builder.startTable();
        builder.getCellFormat().clearFormatting();
        builder.insertCell();
        builder.getCellFormat().setPreferredWidth(PreferredWidth.fromPercent(100 / 3));
        // จะใช้ฟิลด์ PAGE และ NUMPAGES เพื่อคำนวณหมายเลขหน้าปัจจุบันและหน้าต่างๆ โดยอัตโนมัติ
        builder.write("Page ");
        builder.insertField("PAGE", "");
        builder.write(" of ");
        builder.insertField("NUMPAGES", "");
        builder.getCurrentParagraph().getParagraphFormat().setAlignment(ParagraphAlignment.LEFT);
        builder.insertCell();
        builder.getCellFormat().setPreferredWidth(PreferredWidth.fromPercent(100 * 2 / 3));
        builder.write("(C) 2001 Aspose Pty Ltd. All rights reserved.");
        builder.getCurrentParagraph().getParagraphFormat().setAlignment(ParagraphAlignment.RIGHT);
        builder.endRow();
        builder.endTable();
        builder.moveToDocumentEnd();
        // สร้างการแบ่งหน้าเพื่อสร้างหน้าที่สองซึ่งจะเห็นส่วนหัว/ส่วนท้ายหลัก
        builder.insertBreak(BreakType.PAGE_BREAK);
        builder.insertBreak(BreakType.SECTION_BREAK_NEW_PAGE);
        currentSection = builder.getCurrentSection();
        pageSetup = currentSection.getPageSetup();
        pageSetup.setOrientation(Orientation.LANDSCAPE);
        // ส่วนนี้ไม่จำเป็นต้องมีส่วนหัว/ส่วนท้ายหน้าแรกที่แตกต่างกัน เราต้องการเพียงหน้าชื่อเรื่องหนึ่งหน้าในเอกสาร
        //และส่วนหัว/ส่วนท้ายของหน้านี้ได้รับการกำหนดไว้แล้วในส่วนก่อนหน้า
        pageSetup.setDifferentFirstPageHeaderFooter(false);
        // ส่วนนี้แสดงส่วนหัว/ส่วนท้ายจากส่วนก่อนหน้า
        // โดยค่าเริ่มต้นให้เรียก currentSection.HeadersFooters.LinkToPrevious(false) เพื่อยกเลิกความกว้างของหน้านี้
        // แตกต่างกันสำหรับส่วนใหม่ ดังนั้นเราจึงต้องกำหนดความกว้างของเซลล์ต่างกันสำหรับตารางส่วนท้าย
        currentSection.getHeadersFooters().linkToPrevious(false);
        // หากเราต้องการใช้ชุดส่วนหัว/ส่วนท้ายที่มีอยู่แล้วสำหรับส่วนนี้
        // แต่ด้วยการปรับเปลี่ยนเล็กน้อย การคัดลอกส่วนหัว/ส่วนท้ายอาจเป็นประโยชน์
        // จากส่วนก่อนหน้าและปรับใช้การแก้ไขที่จำเป็นในส่วนที่เราต้องการ
        copyHeadersFootersFromPreviousSection(currentSection);
        HeaderFooter primaryFooter = currentSection.getHeadersFooters().getByHeaderFooterType(HeaderFooterType.FOOTER_PRIMARY);
        Row row = primaryFooter.getTables().get(0).getFirstRow();
        row.getFirstCell().getCellFormat().setPreferredWidth(PreferredWidth.fromPercent(100 / 3));
        row.getLastCell().getCellFormat().setPreferredWidth(PreferredWidth.fromPercent(100 * 2 / 3));
        doc.save("Your Directory Path" + "WorkingWithHeadersAndFooters.CreateHeaderFooter.docx");
```	
ซอร์สโค้ดของวิธี copyHeadersFootersFromPreviousSection
```java
    /// <สรุป>
    /// โคลนและคัดลอกส่วนหัว/ส่วนท้ายจากส่วนก่อนหน้าไปยังส่วนที่ระบุ
    /// </สรุป>
    private void copyHeadersFootersFromPreviousSection(Section section)
    {
        Section previousSection = (Section)section.getPreviousSibling();
        if (previousSection == null)
            return;
        section.getHeadersFooters().clear();
        for (HeaderFooter headerFooter : (Iterable<HeaderFooter>) previousSection.getHeadersFooters())
            section.getHeadersFooters().add(headerFooter.deepClone(true));
	}
```

## บทสรุป

ในบทช่วยสอนนี้ เราได้กล่าวถึงหลักพื้นฐานของการทำงานกับส่วนหัวและส่วนท้ายใน Aspose.Words สำหรับ Java แล้ว คุณได้เรียนรู้วิธีการสร้าง ปรับแต่ง และกำหนดรูปแบบส่วนหัวและส่วนท้าย ตลอดจนเทคนิคการจัดรูปแบบเอกสารที่สำคัญอื่นๆ

 สำหรับรายละเอียดเพิ่มเติมและคุณลักษณะขั้นสูง โปรดดูที่[เอกสาร Java ของ Aspose.Words](https://reference.aspose.com/words/java/).

## คำถามที่พบบ่อย

### 1. ฉันจะเพิ่มหมายเลขหน้าลงในส่วนท้ายของเอกสารได้อย่างไร
 คุณสามารถเพิ่มหมายเลขหน้าได้โดยการแทรก`PAGE` ใส่ฟิลด์ลงในส่วนท้ายโดยใช้ Aspose.Words

### 2. Aspose.Words เข้ากันได้กับสภาพแวดล้อมการพัฒนา Java หรือไม่
ใช่ Aspose.Words รองรับการพัฒนา Java โปรดแน่ใจว่าคุณมีการตั้งค่าที่จำเป็น

### 3. ฉันสามารถปรับแต่งแบบอักษรและรูปแบบของส่วนหัวและส่วนท้ายได้หรือไม่
แน่นอน คุณสามารถปรับแต่งแบบอักษร การจัดตำแหน่ง และรูปแบบอื่น ๆ เพื่อให้ส่วนหัวและส่วนท้ายของคุณดูน่าสนใจได้

### 4. เป็นไปได้ไหมที่จะมีส่วนหัวที่ต่างกันสำหรับหน้าคี่และหน้าคู่?
 ใช่คุณสามารถใช้`PageSetup.OddAndEvenPagesHeaderFooter` เพื่อระบุส่วนหัวที่แตกต่างกันสำหรับหน้าคี่และหน้าคู่

### 5. ฉันจะเริ่มต้นใช้งาน Aspose.Words สำหรับ Java ได้อย่างไร
 ในการเริ่มต้น ให้ไปที่[เอกสาร Java ของ Aspose.Words](https://reference.aspose.com/words/java/) เพื่อคำแนะนำที่ครอบคลุมเกี่ยวกับการใช้ API
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
