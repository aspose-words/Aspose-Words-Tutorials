---
date: 2025-11-28
description: เรียนรู้วิธีเปลี่ยนเส้นขอบของเซลล์และจัดรูปแบบตารางด้วย Aspose.Words
  for Java คู่มือแบบขั้นตอนนี้ครอบคลุมการตั้งค่าเส้นขอบ การใช้สไตล์คอลัมน์แรก การปรับขนาดอัตโนมัติของเนื้อหาตาราง
  และการใช้สไตล์ตาราง
linktitle: How to Change Cell Borders in Tables – Aspose.Words for Java
second_title: Aspose.Words Java Document Processing API
title: วิธีเปลี่ยนเส้นขอบเซลล์ในตาราง – Aspose.Words สำหรับ Java
url: /th/java/document-conversion-and-export/formatting-tables-and-table-styles/
weight: 17
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# วิธีการเปลี่ยนเส้นขอบของเซลล์ในตาราง – Aspose.Words for Java

## บทนำ

เมื่อพูดถึงการจัดรูปแบบเอกสาร ตารางมีบทบาทสำคัญ และ **การรู้วิธีเปลี่ยนเส้นขอบของเซลล์** เป็นสิ่งจำเป็นสำหรับการสร้างเลย์เอาต์ที่ชัดเจนและเป็นมืออาชีพ หากคุณกำลังพัฒนาโดยใช้ Java และ Aspose.Words คุณก็มีเครื่องมือที่ทรงพลังอยู่ในมือแล้ว ในบทแนะนำนี้เราจะพาคุณผ่านกระบวนการทั้งหมดของการจัดรูปแบบตาราง การเปลี่ยนเส้นขอบของเซลล์ การใช้ *first column style* และการใช้ *auto‑fit table contents* เพื่อให้เอกสารของคุณดูเรียบหรู

## คำตอบสั้น
- **คลาสหลักสำหรับสร้างตารางคืออะไร?** `DocumentBuilder` สร้างตารางและเซลล์โดยโปรแกรมมิ่ง  
- **จะเปลี่ยนความหนาของเส้นขอบเซลล์เดียวอย่างไร?** ใช้ `builder.getCellFormat().getBorders().getLeft().setLineWidth(value)`  
- **สามารถใช้สไตล์ตารางที่กำหนดไว้ล่วงหน้าได้หรือไม่?** ใช่ – เรียก `table.setStyleIdentifier(StyleIdentifier.YOUR_STYLE)`  
- **เมธอดใดที่ทำให้ตารางอัตโนมัติพอดีกับเนื้อหา?** `table.autoFit(AutoFitBehavior.AUTO_FIT_TO_CONTENTS)`  
- **ต้องมีลิขสิทธิ์สำหรับการใช้งานในผลิตภัณฑ์หรือไม่?** จำเป็นต้องมีลิขสิทธิ์ Aspose.Words ที่ถูกต้องสำหรับการใช้งานที่ไม่ใช่ trial  

## “การเปลี่ยนเส้นขอบของเซลล์” ใน Aspose.Words คืออะไร?

การเปลี่ยนเส้นขอบของเซลล์หมายถึงการปรับแต่งเส้นที่แยกเซลล์ออกจากกัน—สี ความกว้าง และรูปแบบเส้น Aspose.Words มี API ที่ครอบคลุมให้คุณปรับคุณสมบัติเหล่านี้ได้ระดับตาราง แถว หรือเซลล์เดี่ยว ให้คุณควบคุมรูปลักษณ์ของเอกสารได้อย่างละเอียด

## ทำไมต้องใช้ Aspose.Words for Java สำหรับการจัดสไตล์ตาราง?

- **รูปลักษณ์สม่ำเสมอบนทุกแพลตฟอร์ม** – โค้ดสไตล์เดียวทำงานได้บน Windows, Linux, และ macOS  
- **ไม่ต้องพึ่งพา Microsoft Word** – สร้างหรือแก้ไขเอกสารบนเซิร์ฟเวอร์ได้  
- **ไลบรารีสไตล์ที่หลากหลาย** – มีสไตล์ตารางในตัว (เช่น *first column style*) และความสามารถ auto‑fit อย่างเต็มรูปแบบ  

## ข้อกำหนดเบื้องต้น

1. **Java Development Kit (JDK) 8+** – ตรวจสอบให้ `java` อยู่ใน PATH ของคุณ  
2. **IDE** – IntelliJ IDEA, Eclipse หรือเครื่องมือแก้ไขใด ๆ ที่คุณชอบ  
3. **Aspose.Words for Java** – ดาวน์โหลด JAR ล่าสุดจาก [official site](https://releases.aspose.com/words/java/)  
4. **ความรู้พื้นฐาน Java** – คุณควรคุ้นเคยกับการสร้างโปรเจกต์ Maven/Gradle และการเพิ่ม JAR ภายนอก  

## นำเข้าแพ็กเกจ

เพื่อเริ่มทำงานกับตารางคุณต้องนำเข้าคลาสหลักของ Aspose.Words:

```java
import com.aspose.words.*;
```

การนำเข้าครั้งเดียวนี้ทำให้คุณเข้าถึง `Document`, `DocumentBuilder`, `Table`, `StyleIdentifier` และยูทิลิตี้อื่น ๆ อีกมากมาย

## วิธีการเปลี่ยนเส้นขอบของเซลล์

ต่อไปเราจะสร้างตารางง่าย ๆ เปลี่ยนเส้นขอบโดยรวม แล้วปรับเส้นขอบของเซลล์แต่ละเซลล์

### ขั้นตอนที่ 1: โหลดเอกสารใหม่

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

### ขั้นตอนที่ 2: สร้างตารางและตั้งค่าเส้นขอบทั่วโลก

```java
Table table = builder.startTable();
builder.insertCell();

// Set the borders for the entire table.
table.setBorders(LineStyle.SINGLE, 2.0, Color.BLACK);
        
// Set the cell shading for this cell.
builder.getCellFormat().getShading().setBackgroundPatternColor(Color.RED);
builder.writeln("Cell #1");

builder.insertCell();
        
// Specify a different cell shading for the second cell.
builder.getCellFormat().getShading().setBackgroundPatternColor(Color.GREEN);
builder.writeln("Cell #2");

builder.endRow();
```

### ขั้นตอนที่ 3: เปลี่ยนเส้นขอบของเซลล์เดียว

```java
// Clear the cell formatting from previous operations.
builder.getCellFormat().clearFormatting();

builder.insertCell();

// Create larger borders for the first cell of this row.
builder.getCellFormat().getBorders().getLeft().setLineWidth(4.0);
builder.getCellFormat().getBorders().getRight().setLineWidth(4.0);
builder.getCellFormat().getBorders().getTop().setLineWidth(4.0);
builder.getCellFormat().getBorders().getBottom().setLineWidth(4.0);
builder.writeln("Cell #3");

builder.insertCell();
builder.getCellFormat().clearFormatting();
builder.writeln("Cell #4");
        
doc.save("FormatTableAndCellWithDifferentBorders.docx");
```

#### สิ่งที่โค้ดทำ
- **เส้นขอบทั่วโลก** – `table.setBorders` ให้ตารางทั้งหมดเป็นเส้นสีดำ 2‑point  
- **การเติมสีเซลล์** – แสดงวิธีการใส่สีให้เซลล์เดี่ยว (สีแดงและสีเขียว)  
- **เส้นขอบเซลล์แบบกำหนดเอง** – เซลล์ที่สามได้รับเส้นขอบ 4‑point ทุกด้าน ทำให้โดดเด่น  

## การใช้สไตล์ตาราง (รวมถึง First Column Style)

สไตล์ตารางช่วยให้คุณใช้รูปลักษณ์สม่ำเสมอด้วยการเรียกครั้งเดียว เราจะสาธิตวิธีเปิดใช้งาน *first column style* และทำให้ตารางอัตโนมัติพอดีกับเนื้อหา

### ขั้นตอนที่ 4: สร้างเอกสารใหม่สำหรับการจัดสไตล์

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

Table table = builder.startTable();
        
// We must insert at least one row first before setting any table formatting.
builder.insertCell();
```

### ขั้นตอนที่ 5: ใช้สไตล์ที่กำหนดไว้ล่วงหน้าและเปิดใช้งาน First Column Formatting

```java
// Set the table style based on a unique style identifier.
table.setStyleIdentifier(StyleIdentifier.MEDIUM_SHADING_1_ACCENT_1);
        
// Apply which features should be formatted by the style.
table.setStyleOptions(TableStyleOptions.FIRST_COLUMN | TableStyleOptions.ROW_BANDS | TableStyleOptions.FIRST_ROW);

// Auto‑fit the table so columns shrink or expand to fit the content.
table.autoFit(AutoFitBehavior.AUTO_FIT_TO_CONTENTS);
```

### ขั้นตอนที่ 6: เติมข้อมูลลงในตาราง

```java
builder.writeln("Item");
builder.getCellFormat().setRightPadding(40.0);
builder.insertCell();
builder.writeln("Quantity (kg)");
builder.endRow();

builder.insertCell();
builder.writeln("Apples");
builder.insertCell();
builder.writeln("20");
builder.endRow();

builder.insertCell();
builder.writeln("Bananas");
builder.insertCell();
builder.writeln("40");
builder.endRow();

builder.insertCell();
builder.writeln("Carrots");
builder.insertCell();
builder.writeln("50");
builder.endRow();

doc.save("BuildTableWithStyle.docx");
```

#### ทำไมสิ่งนี้สำคัญ
- **Style identifier** – `MEDIUM_SHADING_1_ACCENT_1` ให้ตารางดูเรียบและมีเงาอย่างเป็นระเบียบ  
- **First column style** – การเน้นคอลัมน์แรกช่วยเพิ่มความอ่านง่าย โดยเฉพาะในรายงาน  
- **Row bands** – การสลับสีแถวทำให้ตารางขนาดใหญ่ดูสบายตา  
- **Auto‑fit** – ทำให้ความกว้างของตารางปรับตามเนื้อหา ป้องกันข้อความถูกตัด  

## ปัญหาทั่วไปและการแก้ไข

| Issue | Typical Cause | Quick Fix |
|-------|----------------|-----------|
| Borders not appearing | Using `clearFormatting()` after setting borders | Set borders **after** clearing formatting, or re‑apply them. |
| Shading ignored on merged cells | Shading applied before merging | Apply shading **after** merging the cells. |
| Table width exceeds page margins | No auto‑fit applied | Call `table.autoFit(AutoFitBehavior.AUTO_FIT_TO_CONTENTS)` or set a fixed width. |
| Style not applied | Wrong `StyleIdentifier` value | Verify the identifier exists in the version of Aspose.Words you’re using. |

## คำถามที่พบบ่อย

**Q: สามารถใช้สไตล์ตารางที่กำหนดเองที่ไม่ได้รวมอยู่ในตัวเลือกเริ่มต้นได้หรือไม่?**  
A: ใช่ คุณสามารถสร้างและใช้สไตล์ที่กำหนดเองโดยโปรแกรมมิ่ง ดูรายละเอียดใน [Aspose.Words documentation](https://reference.aspose.com/words/java/)  

**Q: จะทำอย่างไรให้มีการจัดรูปแบบตามเงื่อนไขกับเซลล์?**  
A: ใช้ตรรกะ Java ปกติเพื่อตรวจสอบค่าของเซลล์ แล้วเรียกเมธอดจัดรูปแบบที่เหมาะสม (เช่น เปลี่ยนสีพื้นหลังหากค่ามากกว่าขีดจำกัด)  

**Q: สามารถจัดรูปแบบเซลล์ที่รวมกันได้เหมือนเซลล์ปกติหรือไม่?**  
A: แน่นอน หลังจากรวมเซลล์แล้ว ให้ใช้ API `CellFormat` เดียวกันสำหรับการเติมสีหรือเส้นขอบ  

**Q: ถ้าต้องการให้ตารางปรับขนาดตามข้อมูลที่ผู้ใช้ป้อน จะทำอย่างไร?**  
A: ปรับความกว้างของคอลัมน์หรือเรียก `autoFit` อีกครั้งหลังจากแทรกข้อมูลใหม่เพื่อคำนวณเลย์เอาต์ใหม่  

**Q: จะหา ตัวอย่างเพิ่มเติมเกี่ยวกับการจัดสไตล์ตารางได้จากที่ไหน?**  
A: ตัวอย่างครบถ้วนอยู่ใน [Aspose.Words API documentation](https://reference.aspose.com/words/java/)  

## สรุป

ตอนนี้คุณมีเครื่องมือครบชุดสำหรับ **การเปลี่ยนเส้นขอบของเซลล์** การใช้ *first column style* และ **การทำให้ตารางอัตโนมัติพอดีกับเนื้อหา** ด้วย Aspose.Words for Java การเชี่ยวชาญเทคนิคเหล่านี้จะช่วยให้คุณสร้างเอกสารที่เต็มไปด้วยข้อมูลและสวยงาม—เหมาะสำหรับรายงาน ใบแจ้งหนี้ และผลลัพธ์ทางธุรกิจที่สำคัญอื่น ๆ

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}

---

**Last Updated:** 2025-11-28  
**Tested With:** Aspose.Words for Java 24.12 (latest at time of writing)  
**Author:** Aspose