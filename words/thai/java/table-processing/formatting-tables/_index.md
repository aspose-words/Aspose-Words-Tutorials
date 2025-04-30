---
"description": "เรียนรู้ศิลปะของการจัดรูปแบบตารางในเอกสารโดยใช้ Aspose.Words สำหรับ Java สำรวจคำแนะนำทีละขั้นตอนและตัวอย่างโค้ดต้นฉบับสำหรับการจัดรูปแบบตารางที่แม่นยำ"
"linktitle": "การจัดรูปแบบตารางในเอกสาร"
"second_title": "API การประมวลผลเอกสาร Java ของ Aspose.Words"
"title": "การจัดรูปแบบตารางในเอกสาร"
"url": "/th/java/table-processing/formatting-tables/"
"weight": 13
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# การจัดรูปแบบตารางในเอกสาร

## การแนะนำ

คุณพร้อมที่จะเริ่มสร้างตารางในเอกสาร Word ได้อย่างง่ายดายโดยใช้ Aspose.Words สำหรับ Java หรือไม่ ตารางมีความจำเป็นสำหรับการจัดระเบียบข้อมูล และด้วยไลบรารีอันทรงพลังนี้ คุณสามารถสร้าง เติมข้อมูล และแม้แต่ซ้อนตารางในเอกสาร Word ของคุณได้ด้วยโปรแกรม ในคู่มือทีละขั้นตอนนี้ เราจะสำรวจวิธีการสร้างตาราง รวมเซลล์ และเพิ่มตารางซ้อน

## ข้อกำหนดเบื้องต้น

ก่อนที่คุณจะเริ่มเขียนโค้ด ให้แน่ใจว่าคุณมีสิ่งต่อไปนี้:

- Java Development Kit (JDK) ติดตั้งอยู่บนระบบของคุณ
- Aspose.Words สำหรับไลบรารี Java [ดาวน์โหลดได้ที่นี่](https://releases-aspose.com/words/java/).
- ความเข้าใจพื้นฐานเกี่ยวกับการเขียนโปรแกรมภาษา Java
- IDE เช่น IntelliJ IDEA, Eclipse หรืออื่นๆ ที่คุณคุ้นเคย
- เอ [ใบอนุญาตชั่วคราว](https://purchase.aspose.com/temporary-license/) เพื่อปลดล็อคความสามารถทั้งหมดของ Aspose.Words

## แพ็คเกจนำเข้า

ในการใช้ Aspose.Words สำหรับ Java คุณจำเป็นต้องนำเข้าคลาสและแพ็กเกจที่จำเป็น เพิ่มการนำเข้าเหล่านี้ไว้ที่ด้านบนของไฟล์ Java ของคุณ:

```java
import com.aspose.words.*;
```

มาแบ่งขั้นตอนออกเป็นขั้นตอนเล็กๆ น้อยๆ เพื่อให้ปฏิบัติตามได้ง่ายยิ่งขึ้น

## ขั้นตอนที่ 1: สร้างเอกสารและตาราง

สิ่งแรกที่คุณต้องการคืออะไร? เอกสารสำหรับใช้งาน!

เริ่มต้นด้วยการสร้างเอกสาร Word ใหม่และตาราง จากนั้นผนวกตารางเข้ากับเนื้อหาของเอกสาร

```java
Document doc = new Document();
Table table = new Table(doc);
doc.getFirstSection().getBody().appendChild(table);
```

- `Document`: หมายถึงเอกสาร Word
- `Table`: สร้างตารางเปล่า
- `appendChild`: เพิ่มตารางลงในเนื้อหาของเอกสาร

## ขั้นตอนที่ 2: เพิ่มแถวและเซลล์ลงในตาราง

ตารางที่ไม่มีแถวและเซลล์? นั่นก็เหมือนกับรถยนต์ที่ไม่มีล้อ! มาแก้ไขกันเถอะ

```java
Row firstRow = new Row(doc);
table.appendChild(firstRow);

Cell firstCell = new Cell(doc);
firstRow.appendChild(firstCell);
```

- `Row`: หมายถึงแถวในตาราง
- `Cell`: แสดงถึงเซลล์ในแถว
- `appendChild`: เพิ่มแถวและเซลล์ลงในตาราง

## ขั้นตอนที่ 3: เพิ่มข้อความลงในเซลล์

ถึงเวลาเพิ่มบุคลิกให้กับโต๊ะของเราแล้ว!

```java
Paragraph paragraph = new Paragraph(doc);
firstCell.appendChild(paragraph);

Run run = new Run(doc, "Hello world!");
paragraph.appendChild(run);
```

- `Paragraph`: เพิ่มย่อหน้าลงในเซลล์
- `Run`: เพิ่มข้อความลงในย่อหน้า

## ขั้นตอนที่ 4: รวมเซลล์ในตาราง

ต้องการรวมเซลล์เพื่อสร้างส่วนหัวหรือช่วงหรือไม่ ง่ายมาก!

```java
DocumentBuilder builder = new DocumentBuilder(doc);

builder.insertCell();
builder.getCellFormat().setHorizontalMerge(CellMerge.FIRST);
builder.write("Text in merged cells.");

builder.insertCell();
builder.getCellFormat().setHorizontalMerge(CellMerge.PREVIOUS);
builder.endRow();
```

- `DocumentBuilder`: ทำให้การจัดทำเอกสารเป็นเรื่องง่าย
- `setHorizontalMerge`: รวมเซลล์ในแนวนอน
- `write`เพิ่มเนื้อหาให้กับเซลล์ที่ผสานกัน

## ขั้นตอนที่ 5: เพิ่มตารางแบบซ้อนกัน

พร้อมที่จะเลเวลอัพหรือยัง มาเพิ่มตารางภายในตารางกันเถอะ

```java
builder.moveTo(table.getRows().get(0).getCells().get(0).getFirstParagraph());

builder.startTable();
builder.insertCell();
builder.write("Hello world!");
builder.endTable();
```

- `moveTo`: เลื่อนเคอร์เซอร์ไปยังตำแหน่งที่ระบุในเอกสาร
- `startTable`: เริ่มต้นสร้างตารางแบบซ้อนกัน
- `endTable`: สิ้นสุดตารางที่ซ้อนกัน

## บทสรุป

ขอแสดงความยินดี! คุณได้เรียนรู้วิธีการสร้าง เติมข้อมูล และกำหนดรูปแบบตารางโดยใช้ Aspose.Words สำหรับ Java แล้ว ตั้งแต่การเพิ่มข้อความไปจนถึงการผสานเซลล์และการซ้อนตาราง ตอนนี้คุณมีเครื่องมือสำหรับจัดโครงสร้างข้อมูลอย่างมีประสิทธิภาพในเอกสาร Word แล้ว

## คำถามที่พบบ่อย

### สามารถเพิ่มไฮเปอร์ลิงก์ไปยังเซลล์ตารางได้หรือไม่

ใช่ คุณสามารถเพิ่มไฮเปอร์ลิงก์ไปยังเซลล์ตารางใน Aspose.Words สำหรับ Java ได้ โดยทำได้ดังนี้:

```java
builder.moveTo(table.getRows().get(0).getCells().get(0).getFirstParagraph());

// แทรกไฮเปอร์ลิงก์และเน้นให้โดดเด่นด้วยการจัดรูปแบบแบบกำหนดเอง
// ไฮเปอร์ลิงก์จะเป็นข้อความที่คลิกได้ซึ่งจะนำเราไปยังตำแหน่งที่ระบุไว้ใน URL
builder.getFont().setColor(Color.BLUE);
builder.getFont().setUnderline(Underline.SINGLE);
builder.insertHyperlink("Google website", "https://www.google.com", เท็จ);
```

### ฉันสามารถใช้ Aspose.Words สำหรับ Java ได้ฟรีหรือไม่?  
ใช้ได้แบบมีข้อจำกัดหรือรับได้ [ทดลองใช้งานฟรี](https://releases.aspose.com/) เพื่อสำรวจศักยภาพเต็มที่ของมัน

### ฉันจะผสานเซลล์ในแนวตั้งในตารางได้อย่างไร  
ใช้ `setVerticalMerge` วิธีการของ `CellFormat` คลาสที่คล้ายกับการผสานแนวนอน

### ฉันสามารถเพิ่มรูปภาพลงในเซลล์ตารางได้หรือไม่  
ใช่คุณสามารถใช้ `DocumentBuilder` การแทรกภาพลงในเซลล์ตาราง

### ฉันสามารถหาทรัพยากรเพิ่มเติมเกี่ยวกับ Aspose.Words สำหรับ Java ได้ที่ไหน  
ตรวจสอบ [เอกสารประกอบ](https://reference.aspose.com/words/java/) หรือว่า [ฟอรั่มสนับสนุน](https://forum.aspose.com/c/words/8/) เพื่อดูคำแนะนำโดยละเอียด


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}