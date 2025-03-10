---
title: สร้างตารางจาก Datatable
linktitle: สร้างตารางจาก Datatable
second_title: API การประมวลผลเอกสาร Java ของ Aspose.Words
description: เรียนรู้วิธีสร้างตารางจาก DataTable โดยใช้ Aspose.Words สำหรับ Java สร้างเอกสาร Word แบบมืออาชีพด้วยตารางที่จัดรูปแบบได้อย่างง่ายดาย
weight: 11
url: /th/java/table-processing/generate-table-from-datatable/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# สร้างตารางจาก Datatable

## การแนะนำ

การสร้างตารางแบบไดนามิกจากแหล่งข้อมูลเป็นงานทั่วไปในแอปพลิเคชันจำนวนมาก ไม่ว่าคุณจะสร้างรายงาน ใบแจ้งหนี้ หรือสรุปข้อมูล การสามารถเพิ่มข้อมูลลงในตารางด้วยโปรแกรมสามารถประหยัดเวลาและความพยายามของคุณได้มาก ในบทช่วยสอนนี้ เราจะมาสำรวจวิธีสร้างตารางจาก DataTable โดยใช้ Aspose.Words สำหรับ Java เราจะแบ่งกระบวนการออกเป็นขั้นตอนที่จัดการได้ เพื่อให้แน่ใจว่าคุณจะเข้าใจแต่ละส่วนได้อย่างชัดเจน

## ข้อกำหนดเบื้องต้น

ก่อนจะเจาะลึกโค้ด เรามาตรวจสอบก่อนว่าคุณมีทุกสิ่งที่จำเป็นในการเริ่มต้น:

1.  Java Development Kit (JDK): ตรวจสอบให้แน่ใจว่าคุณได้ติดตั้ง JDK ไว้ในเครื่องของคุณแล้ว คุณสามารถดาวน์โหลดได้จาก[เว็บไซต์ออราเคิล](https://www.oracle.com/java/technologies/javase-jdk11-downloads.html).
   
2.  Aspose.Words สำหรับ Java: คุณจะต้องมีไลบรารี Aspose.Words คุณสามารถดาวน์โหลดเวอร์ชันล่าสุดได้จาก[หน้าเผยแพร่ของ Aspose](https://releases.aspose.com/words/java/).

3. IDE: สภาพแวดล้อมการพัฒนาแบบบูรณาการ (IDE) เช่น IntelliJ IDEA หรือ Eclipse จะทำให้การเขียนโค้ดง่ายขึ้น

4. ความรู้พื้นฐานเกี่ยวกับ Java: ความคุ้นเคยกับแนวคิดการเขียนโปรแกรม Java จะช่วยให้คุณเข้าใจชิ้นส่วนโค้ดได้ดีขึ้น

5. ข้อมูลตัวอย่าง: สำหรับบทช่วยสอนนี้ เราจะใช้ไฟล์ XML ชื่อ "List of people.xml" เพื่อจำลองแหล่งข้อมูล คุณสามารถสร้างไฟล์นี้ด้วยข้อมูลตัวอย่างสำหรับการทดสอบได้

## ขั้นตอนที่ 1: สร้างเอกสารใหม่

ขั้นแรก เราต้องสร้างเอกสารใหม่ซึ่งจะเป็นที่อยู่ของตาราง นี่คือพื้นที่สำหรับงานของเรา

```java
Document doc = new Document();
```

 ที่นี่เราจะสร้างตัวอย่างใหม่`Document` วัตถุ นี่จะเป็นเอกสารการทำงานของเราซึ่งเราจะสร้างตาราง

## ขั้นตอนที่ 2: เริ่มต้น DocumentBuilder

 ต่อไปเราจะใช้`DocumentBuilder` คลาสที่ช่วยให้เราจัดการเอกสารได้ง่ายขึ้น

```java
DocumentBuilder builder = new DocumentBuilder(doc);
```

 การ`DocumentBuilder` วัตถุมีวิธีการแทรกตาราง ข้อความ และองค์ประกอบอื่น ๆ ลงในเอกสาร

## ขั้นตอนที่ 3: ตั้งค่าทิศทางหน้า

เนื่องจากเราคาดว่าตารางของเราจะมีความกว้าง เราจึงจะตั้งค่าการวางแนวหน้าเป็นแนวนอน

```java
doc.getFirstSection().getPageSetup().setOrientation(Orientation.LANDSCAPE);
```

ขั้นตอนนี้มีความสำคัญเนื่องจากช่วยให้แน่ใจว่าตารางของเราพอดีกับหน้าโดยไม่ถูกตัดออก

## ขั้นตอนที่ 4: โหลดข้อมูลจาก XML

 ตอนนี้เราต้องโหลดข้อมูลจากไฟล์ XML ลงใน`DataTable`นี่คือที่มาของข้อมูลของเรา

```java
DataSet ds = new DataSet();
ds.readXml(getMyDir() + "List of people.xml");
DataTable dataTable = ds.getTables().get(0);
```

 ที่นี่ เราอ่านไฟล์ XML และดึงตารางแรกจากชุดข้อมูล`DataTable` จะเก็บข้อมูลที่เราต้องการแสดงในเอกสารของเรา

## ขั้นตอนที่ 5: นำเข้าตารางจาก DataTable

ตอนนี้มาถึงส่วนที่น่าตื่นเต้น: การนำเข้าข้อมูลของเราเข้าสู่เอกสารเป็นตาราง

```java
Table table = importTableFromDataTable(builder, dataTable, true);
```

 เราเรียกวิธีการนี้ว่า`importTableFromDataTable` , ผ่านการ`DocumentBuilder` , ของเรา`DataTable`และค่าบูลีนเพื่อระบุว่าจะรวมส่วนหัวคอลัมน์หรือไม่

## ขั้นตอนที่ 6: จัดแต่งโต๊ะ

เมื่อเรามีโต๊ะแล้ว เราก็สามารถจัดแต่งบางอย่างเพื่อให้ดูดีได้

```java
table.setStyleIdentifier(StyleIdentifier.MEDIUM_LIST_2_ACCENT_1);
table.setStyleOptions(TableStyleOptions.FIRST_ROW | TableStyleOptions.ROW_BANDS | TableStyleOptions.LAST_COLUMN);
```

โค้ดนี้ใช้รูปแบบที่กำหนดไว้ล่วงหน้ากับตาราง เพื่อเพิ่มความสวยงามและความสามารถในการอ่าน

## ขั้นตอนที่ 7: ลบเซลล์ที่ไม่ต้องการ

หากคุณมีคอลัมน์ใดๆ ที่คุณไม่ต้องการให้แสดง เช่น คอลัมน์รูปภาพ คุณสามารถลบออกได้อย่างง่ายดาย

```java
table.getFirstRow().getLastCell().removeAllChildren();
```

ขั้นตอนนี้จะช่วยให้แน่ใจว่าตารางของเราแสดงเฉพาะข้อมูลที่เกี่ยวข้องเท่านั้น

## ขั้นตอนที่ 8: บันทึกเอกสาร

สุดท้ายเราบันทึกเอกสารของเราโดยใช้ตารางที่สร้างขึ้น

```java
doc.save(getArtifactsDir() + "WorkingWithTables.BuildTableFromDataTable.docx");
```

บรรทัดนี้จะบันทึกเอกสารในไดเร็กทอรีที่ระบุ ทำให้คุณสามารถตรวจสอบผลลัพธ์ได้

## วิธีการ importTableFromDataTable

 มาดูกันให้ละเอียดยิ่งขึ้น`importTableFromDataTable` วิธีการนี้รับผิดชอบในการสร้างโครงสร้างตารางและเติมข้อมูลลงไป

### ขั้นตอนที่ 1: เริ่มต้นตาราง

ขั้นแรก เราต้องเริ่มตารางใหม่ในเอกสาร

```java
Table table = builder.startTable();
```

นี่จะเป็นการเริ่มต้นตารางใหม่ในเอกสารของเรา

### ขั้นตอนที่ 2: เพิ่มหัวข้อคอลัมน์

 หากเราต้องการรวมส่วนหัวคอลัมน์ เราจะตรวจสอบ`importColumnHeadings` ธง.

```java
if (importColumnHeadings) {
    // จัดเก็บรูปแบบดั้งเดิม
    boolean boldValue = builder.getFont().getBold();
    int paragraphAlignmentValue = builder.getParagraphFormat().getAlignment();

    // ตั้งค่าการจัดรูปแบบหัวเรื่อง
    builder.getFont().setBold(true);
    builder.getParagraphFormat().setAlignment(ParagraphAlignment.CENTER);

    // แทรกชื่อคอลัมน์
    for (DataColumn column : dataTable.getColumns()) {
        builder.insertCell();
        builder.writeln(column.getColumnName());
    }

    builder.endRow();

    // คืนค่ารูปแบบดั้งเดิม
    builder.getFont().setBold(boldValue);
    builder.getParagraphFormat().setAlignment(paragraphAlignmentValue);
}
```

 บล็อกโค้ดนี้จะจัดรูปแบบแถวหัวเรื่องและแทรกชื่อของคอลัมน์จาก`DataTable`.

### ขั้นตอนที่ 3: เติมข้อมูลลงในตาราง

 ตอนนี้เราวนรอบแต่ละแถวของ`DataTable` การแทรกข้อมูลลงในตาราง

```java
for (DataRow dataRow : (Iterable<DataRow>) dataTable.getRows()) {
    for (Object item : dataRow.getItemArray()) {
        builder.insertCell();
        switch (item.getClass().getName()) {
            case "DateTime":
                Date dateTime = (Date) item;
                SimpleDateFormat simpleDateFormat = new SimpleDateFormat("MMMM d, yyyy");
                builder.write(simpleDateFormat.format(dateTime));
                break;
            default:
                builder.write(item.toString());
                break;
        }
    }
    builder.endRow();
}
```

ในส่วนนี้เราจะจัดการกับประเภทข้อมูลต่างๆ การจัดรูปแบบวันที่อย่างเหมาะสมและการแทรกข้อมูลอื่นๆ เป็นข้อความ

### ขั้นตอนที่ 4: จบตาราง

ในที่สุดเราก็เสร็จสิ้นตารางเมื่อแทรกข้อมูลทั้งหมดเรียบร้อยแล้ว

```java
builder.endTable();
```

 บรรทัดนี้แสดงจุดสิ้นสุดของตารางของเรา ช่วยให้`DocumentBuilder` เพื่อให้ทราบว่าเราทำส่วนนี้เสร็จแล้ว

## บทสรุป

และแล้วคุณก็ทำได้! คุณได้เรียนรู้วิธีการสร้างตารางจาก DataTable โดยใช้ Aspose.Words สำหรับ Java สำเร็จแล้ว โดยทำตามขั้นตอนเหล่านี้ คุณก็สามารถสร้างตารางแบบไดนามิกในเอกสารของคุณได้อย่างง่ายดายโดยอิงจากแหล่งข้อมูลต่างๆ ไม่ว่าคุณจะกำลังสร้างรายงานหรือใบแจ้งหนี้ วิธีนี้จะช่วยปรับปรุงเวิร์กโฟลว์ของคุณและปรับปรุงกระบวนการสร้างเอกสารของคุณ

## คำถามที่พบบ่อย

### Aspose.Words สำหรับ Java คืออะไร?
Aspose.Words สำหรับ Java เป็นไลบรารีอันทรงพลังสำหรับการสร้าง จัดการ และแปลงเอกสาร Word ด้วยโปรแกรม

### ฉันสามารถใช้ Aspose.Words ได้ฟรีหรือไม่?
 ใช่ Aspose นำเสนอเวอร์ชันทดลองใช้งานฟรี คุณสามารถดาวน์โหลดได้จาก[ที่นี่](https://releases.aspose.com/).

### ฉันจะกำหนดรูปแบบตารางใน Aspose.Words ได้อย่างไร?
คุณสามารถใช้รูปแบบได้โดยใช้ตัวระบุรูปแบบที่กำหนดไว้ล่วงหน้าและตัวเลือกที่มีให้โดยไลบรารี

### ฉันสามารถแทรกประเภทข้อมูลใดลงในตารางได้บ้าง?
คุณสามารถแทรกประเภทข้อมูลต่างๆ ได้ เช่น ข้อความ ตัวเลข และวันที่ ซึ่งสามารถจัดรูปแบบได้ตามความเหมาะสม

### ฉันจะได้รับการสนับสนุนสำหรับ Aspose.Words ได้จากที่ไหน
 คุณสามารถค้นหาการสนับสนุนและถามคำถามได้ที่[ฟอรั่ม Aspose](https://forum.aspose.com/c/words/8/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
