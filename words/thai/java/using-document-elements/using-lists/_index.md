---
"description": "เรียนรู้การใช้รายการใน Aspose.Words สำหรับ Java ด้วยบทช่วยสอนแบบทีละขั้นตอนนี้ จัดระเบียบและจัดรูปแบบเอกสารของคุณอย่างมีประสิทธิภาพ"
"linktitle": "การใช้รายการ"
"second_title": "API การประมวลผลเอกสาร Java ของ Aspose.Words"
"title": "การใช้รายการใน Aspose.Words สำหรับ Java"
"url": "/th/java/using-document-elements/using-lists/"
"weight": 18
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# การใช้รายการใน Aspose.Words สำหรับ Java


ในบทช่วยสอนที่ครอบคลุมนี้ เราจะมาสำรวจวิธีใช้รายการใน Aspose.Words for Java อย่างมีประสิทธิภาพ ซึ่งเป็น API ที่มีประสิทธิภาพสำหรับการทำงานกับเอกสาร Microsoft Word ในเชิงโปรแกรม รายการมีความจำเป็นสำหรับการจัดโครงสร้างและจัดระเบียบเนื้อหาในเอกสารของคุณ เราจะครอบคลุมประเด็นสำคัญสองประการของการทำงานกับรายการ ได้แก่ การเริ่มรายการใหม่ในแต่ละส่วนและการระบุระดับรายการ มาเจาะลึกกันเลย!

## บทนำสู่ Aspose.Words สำหรับ Java

ก่อนที่เราจะเริ่มทำงานกับรายการ เรามาทำความรู้จักกับ Aspose.Words สำหรับ Java กันก่อน API นี้มอบเครื่องมือสำหรับนักพัฒนาเพื่อสร้าง แก้ไข และจัดการเอกสาร Word ในสภาพแวดล้อม Java ซึ่งเป็นโซลูชันอเนกประสงค์สำหรับงานตั้งแต่การสร้างเอกสารง่ายๆ ไปจนถึงการจัดรูปแบบและการจัดการเนื้อหาที่ซับซ้อน

### การตั้งค่าสภาพแวดล้อมของคุณ

ในการเริ่มต้น ตรวจสอบให้แน่ใจว่าคุณได้ติดตั้งและตั้งค่า Aspose.Words สำหรับ Java ในสภาพแวดล้อมการพัฒนาของคุณแล้ว คุณสามารถดาวน์โหลดได้ [ที่นี่](https://releases-aspose.com/words/java/). 

## การเริ่มต้นรายการใหม่ในแต่ละส่วน

ในหลายสถานการณ์ คุณอาจต้องเริ่มรายการใหม่ในแต่ละส่วนของเอกสาร ซึ่งอาจมีประโยชน์ในการสร้างเอกสารที่มีโครงสร้างที่มีหลายส่วน เช่น รายงาน คู่มือ หรือเอกสารวิชาการ

นี่คือคำแนะนำทีละขั้นตอนเกี่ยวกับวิธีการบรรลุสิ่งนี้โดยใช้ Aspose.Words สำหรับ Java:

### เริ่มต้นเอกสารของคุณ: 
เริ่มต้นโดยการสร้างวัตถุเอกสารใหม่

```java
Document doc = new Document();
```

### เพิ่มรายการหมายเลข: 
เพิ่มรายการที่มีหมายเลขลงในเอกสารของคุณ เราจะใช้รูปแบบหมายเลขเริ่มต้น

```java
doc.getLists().add(ListTemplate.NUMBER_DEFAULT);
```

### กำหนดค่าการตั้งค่ารายการ: 
\เปิดใช้งานรายการเพื่อเริ่มใหม่ในแต่ละส่วน

```java
List list = doc.getLists().get(0);
list.isRestartAtEachSection(true);
```

### การตั้งค่า DocumentBuilder: 
สร้าง DocumentBuilder เพื่อเพิ่มเนื้อหาลงในเอกสารของคุณ

```java
DocumentBuilder builder = new DocumentBuilder(doc);
builder.getListFormat().setList(list);
```

### เพิ่มรายการ: 
ใช้ลูปเพื่อเพิ่มรายการลงในเอกสารของคุณ เราจะแทรกตัวแบ่งส่วนหลังรายการที่ 15

```java
for (int i = 1; i < 45; i++) {
    builder.writeln(MessageFormat.format("List Item {0}", i));
    if (i == 15)
        builder.insertBreak(BreakType.SECTION_BREAK_NEW_PAGE);
}
```

### บันทึกเอกสารของคุณ: 
บันทึกเอกสารด้วยตัวเลือกที่ต้องการ

```java
OoxmlSaveOptions options = new OoxmlSaveOptions();
options.setCompliance(OoxmlCompliance.ISO_29500_2008_TRANSITIONAL);
doc.save(outPath + "RestartListAtEachSection.docx", options);
```

โดยทำตามขั้นตอนเหล่านี้ คุณสามารถสร้างเอกสารที่มีรายการที่เริ่มต้นใหม่ที่แต่ละส่วน โดยรักษาโครงสร้างเนื้อหาให้ชัดเจนและเป็นระเบียบ

## การระบุระดับรายการ

Aspose.Words สำหรับ Java ช่วยให้คุณระบุระดับรายการได้ ซึ่งมีประโยชน์อย่างยิ่งเมื่อคุณต้องการรูปแบบรายการที่แตกต่างกันภายในเอกสารของคุณ มาลองดูวิธีการดำเนินการนี้กัน:

### เริ่มต้นเอกสารของคุณ: 
สร้างวัตถุเอกสารใหม่

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

### สร้างรายการแบบหมายเลข: 
ใช้เทมเพลตรายการหมายเลขจาก Microsoft Word

```java
builder.getListFormat().setList(doc.getLists().add(ListTemplate.NUMBER_ARABIC_DOT));
```

### ระบุระดับรายการ: 
ทำซ้ำผ่านระดับรายการที่แตกต่างกันและเพิ่มเนื้อหา

```java
for (int i = 0; i < 9; i++) {
    builder.getListFormat().setListLevelNumber(i);
    builder.writeln("Level " + i);
}
```

### สร้างรายการแบบมีหัวข้อย่อย: 
ตอนนี้เรามาสร้างรายการแบบมีหัวข้อย่อยกัน

```java
builder.getListFormat().setList(doc.getLists().add(ListTemplate.BULLET_DIAMONDS));
```

### ระบุระดับรายการหัวข้อย่อย: 
คล้ายกับรายการหมายเลข ระบุระดับและเพิ่มเนื้อหา

```java
for (int i = 0; i < 9; i++) {
    builder.getListFormat().setListLevelNumber(i);
    builder.writeln("Level " + i);
}
```

### การจัดรูปแบบรายการหยุด: 
หากต้องการหยุดการจัดรูปแบบรายการ ให้ตั้งค่ารายการเป็นค่าว่าง

```java
builder.getListFormat().setList(null);
```

### บันทึกเอกสารของคุณ: 
บันทึกเอกสาร

```java
builder.getDocument().save(outPath + "SpecifyListLevel.docx");
```

โดยทำตามขั้นตอนเหล่านี้ คุณสามารถสร้างเอกสารที่มีระดับรายการที่กำหนดเองได้ ซึ่งจะทำให้คุณสามารถควบคุมการจัดรูปแบบของรายการในเอกสารของคุณได้

## ซอร์สโค้ดที่สมบูรณ์
```java
	string outPath = "Your Output Directory";
 public void restartListAtEachSection() throws Exception
    {
        Document doc = new Document();
        doc.getLists().add(ListTemplate.NUMBER_DEFAULT);
        List list = doc.getLists().get(0);
        list.isRestartAtEachSection(true);
        DocumentBuilder builder = new DocumentBuilder(doc);
        builder.getListFormat().setList(list);
        for (int i = 1; i < 45; i++)
        {
            builder.writeln(MessageFormat.format("List Item {0}", i));
            if (i == 15)
                builder.insertBreak(BreakType.SECTION_BREAK_NEW_PAGE);
        }
        // IsRestartAtEachSection จะถูกเขียนเฉพาะเมื่อความสอดคล้องสูงกว่า OoxmlComplianceCore.Ecma376
        OoxmlSaveOptions options = new OoxmlSaveOptions(); { options.setCompliance(OoxmlCompliance.ISO_29500_2008_TRANSITIONAL); }
        doc.save(outPath + "WorkingWithList.RestartListAtEachSection.docx", options);
    }
    @Test
    public void specifyListLevel() throws Exception
    {
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
        // สร้างรายการที่มีหมายเลขโดยอิงจากเทมเพลตรายการ Microsoft Word หนึ่งรายการ
        // และนำมาใช้กับย่อหน้าปัจจุบันของตัวสร้างเอกสาร
        builder.getListFormat().setList(doc.getLists().add(ListTemplate.NUMBER_ARABIC_DOT));
        // รายการนี้มีทั้งหมด 9 ระดับ มาลองเล่นให้ครบทุกระดับกันเลย
        for (int i = 0; i < 9; i++)
        {
            builder.getListFormat().setListLevelNumber(i);
            builder.writeln("Level " + i);
        }
        // สร้างรายการแบบมีหัวข้อย่อยโดยอิงจากเทมเพลตรายการของ Microsoft Word
        // และนำมาใช้กับย่อหน้าปัจจุบันของตัวสร้างเอกสาร
        builder.getListFormat().setList(doc.getLists().add(ListTemplate.BULLET_DIAMONDS));
        for (int i = 0; i < 9; i++)
        {
            builder.getListFormat().setListLevelNumber(i);
            builder.writeln("Level " + i);
        }
        // นี่เป็นวิธีหยุดการจัดรูปแบบรายการ
        builder.getListFormat().setList(null);
        builder.getDocument().save(outPath + "WorkingWithList.SpecifyListLevel.docx");
    }
    @Test
    public void restartListNumber() throws Exception
    {
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
        // สร้างรายการโดยอิงจากเทมเพลต
        List list1 = doc.getLists().add(ListTemplate.NUMBER_ARABIC_PARENTHESIS);
        list1.getListLevels().get(0).getFont().setColor(Color.RED);
        list1.getListLevels().get(0).setAlignment(ListLevelAlignment.RIGHT);
        builder.writeln("List 1 starts below:");
        builder.getListFormat().setList(list1);
        builder.writeln("Item 1");
        builder.writeln("Item 2");
        builder.getListFormat().removeNumbers();
        // หากต้องการนำรายการแรกมาใช้ซ้ำ เราจะต้องเริ่มการนับหมายเลขใหม่โดยสร้างสำเนาของการจัดรูปแบบรายการต้นฉบับ
        List list2 = doc.getLists().addCopy(list1);
        // เราปรับเปลี่ยนรายการใหม่ได้ทุกวิถีทาง รวมถึงการกำหนดหมายเลขเริ่มต้นใหม่
        list2.getListLevels().get(0).setStartAt(10);
        builder.writeln("List 2 starts below:");
        builder.getListFormat().setList(list2);
        builder.writeln("Item 1");
        builder.writeln("Item 2");
        builder.getListFormat().removeNumbers();
        builder.getDocument().save(outPath + "WorkingWithList.RestartListNumber.docx");
	}
```

## บทสรุป

ขอแสดงความยินดี! คุณได้เรียนรู้วิธีการทำงานกับรายการใน Aspose.Words สำหรับ Java อย่างมีประสิทธิภาพแล้ว รายการมีความสำคัญต่อการจัดระเบียบและนำเสนอเนื้อหาในเอกสารของคุณ ไม่ว่าคุณจะต้องเริ่มรายการใหม่ในแต่ละส่วนหรือระบุระดับรายการ Aspose.Words สำหรับ Java ก็มีเครื่องมือที่คุณต้องการเพื่อสร้างเอกสารที่ดูเป็นมืออาชีพ

ตอนนี้คุณสามารถใช้ฟีเจอร์เหล่านี้ได้อย่างมั่นใจเพื่อเพิ่มประสิทธิภาพการสร้างและจัดรูปแบบเอกสารของคุณ หากคุณมีคำถามหรือต้องการความช่วยเหลือเพิ่มเติม โปรดอย่าลังเลที่จะติดต่อ [ฟอรั่มชุมชน Aspose](https://forum.aspose.com/) เพื่อรองรับ

## คำถามที่พบบ่อย

### ฉันจะติดตั้ง Aspose.Words สำหรับ Java ได้อย่างไร?
คุณสามารถดาวน์โหลด Aspose.Words สำหรับ Java ได้จาก [ที่นี่](https://releases.aspose.com/words/java/) และปฏิบัติตามคำแนะนำในการติดตั้งที่อยู่ในเอกสาร

### ฉันสามารถปรับแต่งรูปแบบการนับหมายเลขของรายการได้หรือไม่
ใช่ Aspose.Words สำหรับ Java มีตัวเลือกมากมายสำหรับการปรับแต่งรูปแบบการนับรายการ คุณสามารถดูรายละเอียดเพิ่มเติมได้ในเอกสารประกอบ API

### Aspose.Words สำหรับ Java เข้ากันได้กับมาตรฐานเอกสาร Word ล่าสุดหรือไม่
ใช่ คุณสามารถกำหนดค่า Aspose.Words สำหรับ Java เพื่อให้เป็นไปตามมาตรฐานเอกสาร Word ต่างๆ รวมถึง ISO 29500

### ฉันสามารถสร้างเอกสารที่ซับซ้อนด้วยตารางและรูปภาพโดยใช้ Aspose.Words สำหรับ Java ได้หรือไม่
แน่นอน! Aspose.Words สำหรับ Java รองรับการจัดรูปแบบเอกสารขั้นสูง รวมถึงตาราง รูปภาพ และอื่นๆ อีกมากมาย ตรวจสอบเอกสารเพื่อดูตัวอย่าง

### ฉันสามารถรับใบอนุญาตชั่วคราวสำหรับ Aspose.Words สำหรับ Java ได้จากที่ใด
คุณสามารถขอใบอนุญาตชั่วคราวได้ [ที่นี่](https://purchase-aspose.com/temporary-license/).



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}