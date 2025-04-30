---
"description": "เรียนรู้วิธีจัดรูปแบบตารางและนำรูปแบบไปใช้โดยใช้ Aspose.Words สำหรับ Java คำแนะนำทีละขั้นตอนนี้ครอบคลุมถึงการตั้งค่าขอบ การแรเงาเซลล์ และการนำรูปแบบตารางไปใช้"
"linktitle": "การจัดรูปแบบตารางและสไตล์ของตาราง"
"second_title": "API การประมวลผลเอกสาร Java ของ Aspose.Words"
"title": "การจัดรูปแบบตารางและสไตล์ของตาราง"
"url": "/th/java/document-conversion-and-export/formatting-tables-and-table-styles/"
"weight": 17
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# การจัดรูปแบบตารางและสไตล์ของตาราง


## การแนะนำ

เมื่อเป็นเรื่องของการจัดรูปแบบเอกสาร ตารางมีบทบาทสำคัญในการจัดระเบียบและนำเสนอข้อมูลอย่างชัดเจน หากคุณใช้ Java และ Aspose.Words คุณจะมีเครื่องมืออันทรงพลังสำหรับการสร้างและจัดรูปแบบตารางในเอกสารของคุณ ไม่ว่าคุณจะออกแบบตารางธรรมดาหรือใช้สไตล์ขั้นสูง Aspose.Words สำหรับ Java ก็มีคุณสมบัติมากมายที่จะช่วยให้คุณได้รับผลลัพธ์ที่ดูเป็นมืออาชีพ

ในคู่มือนี้ เราจะแนะนำคุณเกี่ยวกับขั้นตอนการจัดรูปแบบตารางและการใช้รูปแบบตารางโดยใช้ Aspose.Words สำหรับ Java คุณจะได้เรียนรู้วิธีการตั้งค่าเส้นขอบตาราง การแรเงาเซลล์ และใช้รูปแบบตารางเพื่อปรับปรุงรูปลักษณ์ของเอกสารของคุณ เมื่ออ่านจบ คุณจะมีทักษะในการสร้างตารางที่มีรูปแบบที่ดีซึ่งจะทำให้ข้อมูลของคุณโดดเด่น

## ข้อกำหนดเบื้องต้น

ก่อนที่เราจะเริ่มต้น มีบางสิ่งที่คุณต้องมี:

1. Java Development Kit (JDK): ตรวจสอบให้แน่ใจว่าคุณได้ติดตั้ง JDK 8 หรือใหม่กว่าแล้ว Aspose.Words สำหรับ Java ต้องใช้ JDK ที่เข้ากันได้จึงจะทำงานได้อย่างถูกต้อง
2. สภาพแวดล้อมการพัฒนาแบบบูรณาการ (IDE): IDE เช่น IntelliJ IDEA หรือ Eclipse จะช่วยคุณจัดการโปรเจ็กต์ Java และปรับปรุงกระบวนการพัฒนาของคุณให้มีประสิทธิภาพยิ่งขึ้น
3. ไลบรารี Aspose.Words สำหรับ Java: ดาวน์โหลดเวอร์ชันล่าสุดของ Aspose.Words สำหรับ Java [ที่นี่](https://releases.aspose.com/words/java/) และรวมไว้ในโครงการของคุณ
4. โค้ดตัวอย่าง: เราจะใช้โค้ดตัวอย่างบางส่วน ดังนั้น โปรดแน่ใจว่าคุณมีความเข้าใจพื้นฐานเกี่ยวกับการเขียนโปรแกรม Java และวิธีการรวมไลบรารีเข้ากับโปรเจ็กต์ของคุณ

## แพ็คเกจนำเข้า

ในการใช้งาน Aspose.Words สำหรับ Java คุณจะต้องนำเข้าแพ็คเกจที่เกี่ยวข้องเข้าสู่โปรเจ็กต์ของคุณ แพ็คเกจเหล่านี้มีคลาสและวิธีการที่จำเป็นสำหรับการจัดการและจัดรูปแบบเอกสาร

```java
import com.aspose.words.*;
```

คำสั่งนำเข้านี้ทำให้คุณสามารถเข้าถึงคลาสที่จำเป็นทั้งหมดสำหรับการสร้างและการจัดรูปแบบตารางในเอกสารของคุณ

## ขั้นตอนที่ 1: การจัดรูปแบบตาราง

การจัดรูปแบบตารางใน Aspose.Words สำหรับ Java เกี่ยวข้องกับการตั้งค่าขอบ การแรเงาเซลล์ และการใช้ตัวเลือกการจัดรูปแบบต่างๆ คุณสามารถทำได้ดังนี้:

### โหลดเอกสาร

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

### สร้างและจัดรูปแบบตาราง

```java
Table table = builder.startTable();
builder.insertCell();

// กำหนดขอบเขตให้กับตารางทั้งหมด
table.setBorders(LineStyle.SINGLE, 2.0, Color.BLACK);
        
// ตั้งค่าการแรเงาเซลล์สำหรับเซลล์นี้
builder.getCellFormat().getShading().setBackgroundPatternColor(Color.RED);
builder.writeln("Cell #1");

builder.insertCell();
        
// ระบุการแรเงาเซลล์ที่แตกต่างกันสำหรับเซลล์ที่สอง
builder.getCellFormat().getShading().setBackgroundPatternColor(Color.GREEN);
builder.writeln("Cell #2");

builder.endRow();
```

### ปรับแต่งขอบเขตเซลล์

```java
// ล้างการจัดรูปแบบเซลล์จากการดำเนินการก่อนหน้า
builder.getCellFormat().clearFormatting();

builder.insertCell();

// สร้างเส้นขอบที่ใหญ่ขึ้นสำหรับเซลล์แรกของแถวนี้
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

### คำอธิบาย

ในตัวอย่างนี้:
- ตั้งค่าเส้นขอบ: เราตั้งค่าเส้นขอบของตารางทั้งหมดเป็นรูปแบบเส้นเดียวโดยมีความหนา 2.0 จุด
- การแรเงาเซลล์: เซลล์แรกแรเงาด้วยสีแดง และเซลล์ที่สองแรเงาด้วยสีเขียว วิธีนี้ช่วยให้แยกความแตกต่างระหว่างเซลล์ต่างๆ ได้อย่างชัดเจน
- ขอบเซลล์: สำหรับเซลล์ที่สาม เราสร้างขอบที่หนากว่าเพื่อเน้นให้แตกต่างจากเซลล์ที่เหลือ

## ขั้นตอนที่ 2: การใช้รูปแบบตาราง

สไตล์ตารางใน Aspose.Words สำหรับ Java ช่วยให้คุณสามารถใช้ตัวเลือกการจัดรูปแบบที่กำหนดไว้ล่วงหน้ากับตาราง ทำให้การสร้างรูปลักษณ์ที่สอดคล้องกันเป็นเรื่องง่ายขึ้น ต่อไปนี้เป็นวิธีการใช้สไตล์กับตารางของคุณ:

### สร้างเอกสารและตาราง

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

Table table = builder.startTable();
        
// เราจะต้องแทรกอย่างน้อยหนึ่งแถวก่อนการตั้งค่าการจัดรูปแบบตารางใดๆ
builder.insertCell();
```

### ใช้รูปแบบตาราง

```java
// ตั้งค่ารูปแบบตารางตามตัวระบุรูปแบบเฉพาะตัว
table.setStyleIdentifier(StyleIdentifier.MEDIUM_SHADING_1_ACCENT_1);
        
// ปรับใช้คุณลักษณะใดจึงจะถูกจัดรูปแบบตามรูปแบบ
table.setStyleOptions(TableStyleOptions.FIRST_COLUMN | TableStyleOptions.ROW_BANDS | TableStyleOptions.FIRST_ROW);
table.autoFit(AutoFitBehavior.AUTO_FIT_TO_CONTENTS);
```

### เพิ่มข้อมูลตาราง

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

### คำอธิบาย

ในตัวอย่างนี้:
- ตั้งค่ารูปแบบตาราง: เราใช้รูปแบบที่กำหนดไว้ล่วงหน้า (`MEDIUM_SHADING_1_ACCENT_1`) ลงในตาราง รูปแบบนี้รวมถึงการจัดรูปแบบสำหรับส่วนต่าง ๆ ของตาราง
- ตัวเลือกสไตล์: เราระบุว่าคอลัมน์แรก แถบแถว และแถวแรกจะต้องได้รับการจัดรูปแบบตามตัวเลือกสไตล์
- AutoFit: เราใช้ `AUTO_FIT_TO_CONTENTS` เพื่อให้แน่ใจว่าตารางปรับขนาดตามเนื้อหา

## บทสรุป

และแล้วคุณก็ทำได้! คุณได้จัดรูปแบบตารางและนำรูปแบบไปใช้สำเร็จแล้วโดยใช้ Aspose.Words สำหรับ Java ด้วยเทคนิคเหล่านี้ คุณสามารถสร้างตารางที่ไม่เพียงแต่ใช้งานได้จริงแต่ยังดูสวยงามอีกด้วย การจัดรูปแบบตารางอย่างมีประสิทธิภาพสามารถปรับปรุงการอ่านและรูปลักษณ์ที่เป็นมืออาชีพของเอกสารของคุณได้อย่างมาก

Aspose.Words สำหรับ Java เป็นเครื่องมือที่มีประสิทธิภาพซึ่งมีคุณสมบัติมากมายสำหรับการจัดการเอกสาร ด้วยการเชี่ยวชาญการจัดรูปแบบและสไตล์ของตาราง คุณจะเข้าใกล้การใช้ประโยชน์จากไลบรารีนี้อย่างเต็มประสิทธิภาพอีกขั้นหนึ่ง

## คำถามที่พบบ่อย

### 1. ฉันสามารถใช้รูปแบบตารางแบบกำหนดเองที่ไม่ได้รวมอยู่ในตัวเลือกเริ่มต้นได้หรือไม่

ใช่ คุณสามารถกำหนดและใช้รูปแบบที่กำหนดเองกับตารางของคุณได้โดยใช้ Aspose.Words สำหรับ Java ตรวจสอบ [เอกสารประกอบ](https://reference.aspose.com/words/java/) สำหรับรายละเอียดเพิ่มเติมเกี่ยวกับการสร้างสไตล์ที่กำหนดเอง

### 2. ฉันจะนำการจัดรูปแบบตามเงื่อนไขไปใช้กับตารางได้อย่างไร

Aspose.Words สำหรับ Java ช่วยให้คุณปรับรูปแบบตารางตามเงื่อนไขได้โดยอัตโนมัติ ซึ่งสามารถทำได้โดยตรวจสอบเกณฑ์เฉพาะในโค้ดของคุณแล้วจัดรูปแบบตามนั้น

### 3. ฉันสามารถจัดรูปแบบเซลล์ที่ผสานในตารางได้หรือไม่

ใช่ คุณสามารถจัดรูปแบบเซลล์ที่ผสานได้เช่นเดียวกับเซลล์ปกติ ตรวจสอบให้แน่ใจว่าคุณใช้การจัดรูปแบบหลังจากผสานเซลล์แล้ว เพื่อดูการเปลี่ยนแปลงที่เกิดขึ้น

### 4. สามารถปรับเค้าโครงตารางแบบไดนามิกได้หรือไม่

ใช่ คุณสามารถปรับเปลี่ยนเค้าโครงตารางได้แบบไดนามิกโดยการแก้ไขขนาดเซลล์ ความกว้างของตาราง และคุณสมบัติอื่นๆ ตามเนื้อหาหรือข้อมูลที่ผู้ใช้ป้อน

### 5. ฉันสามารถหาข้อมูลเพิ่มเติมเกี่ยวกับการจัดรูปแบบตารางได้จากที่ไหน

สำหรับตัวอย่างและตัวเลือกโดยละเอียดเพิ่มเติม โปรดไปที่ [เอกสารประกอบ API ของ Aspose.Words](https://reference-aspose.com/words/java/).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}