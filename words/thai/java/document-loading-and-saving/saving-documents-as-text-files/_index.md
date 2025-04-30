---
"description": "เรียนรู้วิธีบันทึกเอกสารเป็นไฟล์ข้อความใน Aspose.Words สำหรับ Java ปฏิบัติตามคำแนะนำทีละขั้นตอนของเราพร้อมตัวอย่างโค้ด Java"
"linktitle": "การบันทึกเอกสารเป็นไฟล์ข้อความ"
"second_title": "API การประมวลผลเอกสาร Java ของ Aspose.Words"
"title": "การบันทึกเอกสารเป็นไฟล์ข้อความใน Aspose.Words สำหรับ Java"
"url": "/th/java/document-loading-and-saving/saving-documents-as-text-files/"
"weight": 24
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# การบันทึกเอกสารเป็นไฟล์ข้อความใน Aspose.Words สำหรับ Java


## บทนำสู่การบันทึกเอกสารเป็นไฟล์ข้อความใน Aspose.Words สำหรับ Java

ในบทช่วยสอนนี้ เราจะมาเรียนรู้วิธีบันทึกเอกสารเป็นไฟล์ข้อความโดยใช้ไลบรารี Aspose.Words สำหรับ Java Aspose.Words เป็น Java API ที่ทรงพลังสำหรับการทำงานกับเอกสาร Word และมีตัวเลือกต่างๆ สำหรับการบันทึกเอกสารในรูปแบบต่างๆ รวมถึงข้อความธรรมดา เราจะอธิบายขั้นตอนต่างๆ เพื่อให้บรรลุเป้าหมายนี้ และให้ตัวอย่างโค้ด Java ไปด้วย

## ข้อกำหนดเบื้องต้น

ก่อนที่เราจะเริ่ม โปรดตรวจสอบให้แน่ใจว่าคุณมีข้อกำหนดเบื้องต้นดังต่อไปนี้:

- Java Development Kit (JDK) ติดตั้งอยู่บนระบบของคุณ
- ไลบรารี Aspose.Words สำหรับ Java รวมอยู่ในโปรเจ็กต์ของคุณ คุณสามารถดาวน์โหลดได้จาก [ที่นี่](https://releases-aspose.com/words/java/).
- ความรู้พื้นฐานเกี่ยวกับการเขียนโปรแกรมภาษา Java

## ขั้นตอนที่ 1: สร้างเอกสาร

หากต้องการบันทึกเอกสารเป็นไฟล์ข้อความ เราต้องสร้างเอกสารโดยใช้ Aspose.Words ก่อน นี่คือตัวอย่างโค้ด Java ง่ายๆ ในการสร้างเอกสารที่มีเนื้อหาบางส่วน:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
builder.writeln("Hello world!");
builder.getParagraphFormat().setBidi(true);
builder.writeln("שלום עולם!");
builder.writeln("مرحبا بالعالم!");
```

ในโค้ดนี้ เราจะสร้างเอกสารใหม่และเพิ่มข้อความลงไป รวมถึงข้อความในภาษาต่างๆ ด้วย

## ขั้นตอนที่ 2: กำหนดตัวเลือกการบันทึกข้อความ

ขั้นต่อไป เราต้องกำหนดตัวเลือกการบันทึกข้อความที่ระบุวิธีการบันทึกเอกสารเป็นไฟล์ข้อความ เราสามารถกำหนดค่าการตั้งค่าต่างๆ เช่น การเพิ่มเครื่องหมายบิดิ การย่อหน้ารายการ และอื่นๆ ลองดูตัวอย่างสองตัวอย่าง:

### ตัวอย่างที่ 1: การเพิ่มเครื่องหมายบิดิ

```java
TxtSaveOptions saveOptions = new TxtSaveOptions();
saveOptions.setAddBidiMarks(true);
doc.save("output.txt", saveOptions);
```

ในตัวอย่างนี้ เราสร้าง `TxtSaveOptions` วัตถุและตั้งค่า `AddBidiMarks` ทรัพย์สินที่จะ `true` เพื่อรวมเครื่องหมายบิดิลงในผลลัพธ์ข้อความ

### ตัวอย่างที่ 2: การใช้แท็บอักขระสำหรับการเยื้องรายการ

```java
TxtSaveOptions saveOptions = new TxtSaveOptions();
saveOptions.getListIndentation().setCount(1);
saveOptions.getListIndentation().setCharacter('\t');
doc.save("output.txt", saveOptions);
```

ที่นี่ เราจะกำหนดค่าตัวเลือกการบันทึกเพื่อใช้แท็บสำหรับการเยื้องรายการด้วยการนับเป็น 1

## ขั้นตอนที่ 3: บันทึกเอกสารเป็นข้อความ

ตอนนี้เราได้กำหนดตัวเลือกการบันทึกข้อความแล้ว เราสามารถบันทึกเอกสารเป็นไฟล์ข้อความได้ โค้ดต่อไปนี้จะสาธิตวิธีการดำเนินการดังกล่าว:

```java
doc.save("output.txt", saveOptions);
```

แทนที่ `"output.txt"` พร้อมเส้นทางไฟล์ที่ต้องการบันทึกไฟล์ข้อความ

## โค้ดต้นฉบับสมบูรณ์สำหรับการบันทึกเอกสารเป็นไฟล์ข้อความใน Aspose.Words สำหรับ Java

```java
    public void addBidiMarks() throws Exception
    {        
		Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
        builder.writeln("Hello world!");
        builder.getParagraphFormat().setBidi(true);
        builder.writeln("שלום עולם!");
        builder.writeln("مرحبا بالعالم!");
        TxtSaveOptions saveOptions = new TxtSaveOptions(); { saveOptions.setAddBidiMarks(true); }
        doc.save("Your Directory Path" + "WorkingWithTxtSaveOptions.AddBidiMarks.txt", saveOptions);
    }
    @Test
    public void useTabCharacterPerLevelForListIndentation() throws Exception
    {
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
        // สร้างรายการที่มีการเยื้อง 3 ระดับ
        builder.getListFormat().applyNumberDefault();
        builder.writeln("Item 1");
        builder.getListFormat().listIndent();
        builder.writeln("Item 2");
        builder.getListFormat().listIndent(); 
        builder.write("Item 3");
        TxtSaveOptions saveOptions = new TxtSaveOptions();
        saveOptions.getListIndentation().setCount(1);
        saveOptions.getListIndentation().setCharacter('\t');
        doc.save("Your Directory Path" + "WorkingWithTxtSaveOptions.UseTabCharacterPerLevelForListIndentation.txt", saveOptions);
    }
    @Test
    public void useSpaceCharacterPerLevelForListIndentation() throws Exception
    {
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
        // สร้างรายการที่มีการเยื้อง 3 ระดับ
        builder.getListFormat().applyNumberDefault();
        builder.writeln("Item 1");
        builder.getListFormat().listIndent();
        builder.writeln("Item 2");
        builder.getListFormat().listIndent(); 
        builder.write("Item 3");
        TxtSaveOptions saveOptions = new TxtSaveOptions();
        saveOptions.getListIndentation().setCount(3);
        saveOptions.getListIndentation().setCharacter(' ');
        doc.save("Your Directory Path" + "WorkingWithTxtSaveOptions.UseSpaceCharacterPerLevelForListIndentation.txt", saveOptions);
	}
```

## บทสรุป

ในบทช่วยสอนนี้ เราได้เรียนรู้วิธีการบันทึกเอกสารเป็นไฟล์ข้อความใน Aspose.Words สำหรับ Java เราได้กล่าวถึงขั้นตอนในการสร้างเอกสาร การกำหนดตัวเลือกบันทึกข้อความ และบันทึกเอกสารในรูปแบบข้อความ Aspose.Words ให้ความยืดหยุ่นอย่างมากในการบันทึกเอกสาร ช่วยให้คุณปรับแต่งผลลัพธ์ให้ตรงตามความต้องการเฉพาะของคุณได้

## คำถามที่พบบ่อย

### ฉันจะเพิ่มเครื่องหมายบิดิลงในข้อความเอาท์พุตได้อย่างไร

หากต้องการเพิ่มเครื่องหมายบิดิลงในข้อความเอาต์พุต ให้ตั้งค่า `AddBidiMarks` ทรัพย์สินของ `TxtSaveOptions` ถึง `true`. ตัวอย่างเช่น:

```java
TxtSaveOptions saveOptions = new TxtSaveOptions();
saveOptions.setAddBidiMarks(true);
```

### ฉันสามารถปรับแต่งอักขระการเยื้องรายการได้หรือไม่

ใช่ คุณสามารถปรับแต่งอักขระการเยื้องรายการได้โดยการกำหนดค่า `ListIndentation` ทรัพย์สินของ `TxtSaveOptions`ตัวอย่างเช่น หากต้องการใช้อักขระแท็บสำหรับการเยื้องรายการ คุณสามารถดำเนินการดังต่อไปนี้:

```java
TxtSaveOptions saveOptions = new TxtSaveOptions();
saveOptions.getListIndentation().setCount(1);
saveOptions.getListIndentation().setCharacter('\t');
```

### Aspose.Words สำหรับ Java เหมาะกับการจัดการข้อความหลายภาษาหรือไม่

ใช่ Aspose.Words สำหรับ Java เหมาะสำหรับการจัดการข้อความหลายภาษา รองรับภาษาต่างๆ และการเข้ารหัสอักขระ ทำให้เป็นตัวเลือกที่หลากหลายสำหรับการทำงานกับเอกสารในภาษาต่างๆ

### ฉันจะเข้าถึงเอกสารและทรัพยากรเพิ่มเติมสำหรับ Aspose.Words สำหรับ Java ได้อย่างไร

คุณสามารถค้นหาเอกสารและทรัพยากรที่ครอบคลุมสำหรับ Aspose.Words สำหรับ Java ได้ที่เว็บไซต์เอกสาร Aspose: [เอกสาร Aspose.Words สำหรับ Java](https://reference-aspose.com/words/java/).

### ฉันสามารถดาวน์โหลด Aspose.Words สำหรับ Java ได้ที่ไหน

คุณสามารถดาวน์โหลดไลบรารี Aspose.Words สำหรับ Java ได้จากเว็บไซต์ Aspose: [ดาวน์โหลด Aspose.Words สำหรับ Java](https://releases-aspose.com/words/java/).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}