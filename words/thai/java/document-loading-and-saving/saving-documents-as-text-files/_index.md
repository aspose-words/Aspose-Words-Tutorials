---
date: 2025-12-24
description: เรียนรู้วิธีสร้างไฟล์ข้อความธรรมดาจากเอกสาร Word ด้วย Aspose.Words สำหรับ
  Java คู่มือนี้แสดงวิธีแปลง Word เป็น txt, ใช้การเยื้องด้วยแท็บ, และบันทึก Word เป็น
  txt.
linktitle: Saving Documents as Text Files
second_title: Aspose.Words Java Document Processing API
title: วิธีสร้างไฟล์ข้อความธรรมดาด้วย Aspose.Words สำหรับ Java
url: /th/java/document-loading-and-saving/saving-documents-as-text-files/
weight: 24
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# วิธีสร้างไฟล์ข้อความธรรมดาด้วย Aspose.Words for Java

## แนะนำการบันทึกเอกสารเป็นไฟล์ข้อความใน Aspose.Words for Java

ในบทแนะนำนี้ คุณจะได้เรียนรู้ **วิธีสร้างไฟล์ข้อความธรรมดา** จากเอกสาร Word โดยใช้ไลบรารี Aspose.Words for Java ไม่ว่าคุณจะต้องการ **แปลง word เป็น txt**, ทำการสร้างรายงานอัตโนมัติ, หรือเพียงแค่ดึงข้อความดิบเพื่อประมวลผลต่อไป คู่มือนี้จะพาคุณผ่านขั้นตอนทั้งหมด—from การสร้างเอกสารจนถึงการปรับแต่งตัวเลือกการบันทึก เช่น **ใช้การเยื้องด้วยแท็บ** หรือเพิ่มเครื่องหมาย bidi. มาเริ่มกันเลย!

## คำตอบสั้น ๆ
- **คลาสหลักที่ใช้สร้างเอกสารคืออะไร?** `Document` จาก Aspose.Words.  
- **ตัวเลือกใดที่เพิ่มเครื่องหมาย bidi สำหรับภาษาขวา‑ซ้าย?** `TxtSaveOptions.setAddBidiMarks(true)`.  
- **จะเยื้องรายการด้วยแท็บได้อย่างไร?** ตั้งค่า `ListIndentation.Character` เป็น `'\t'`.  
- **ต้องใช้ลิขสิทธิ์สำหรับการพัฒนาหรือไม่?** รุ่นทดลองฟรีใช้ได้สำหรับการทดสอบ; ต้องมีลิขสิทธิ์สำหรับการใช้งานจริง.  
- **สามารถบันทึกไฟล์ด้วยชื่อและพาธที่กำหนดเองได้หรือไม่?** ได้—ส่งพาธเต็มให้กับ `doc.save()`.

## ข้อกำหนดเบื้องต้น

ก่อนเริ่มทำงาน โปรดตรวจสอบว่าคุณมีสิ่งต่อไปนี้พร้อมใช้งาน:

- Java Development Kit (JDK) ติดตั้งบนระบบของคุณ  
- ไลบรารี Aspose.Words for Java รวมอยู่ในโปรเจกต์ของคุณ สามารถดาวน์โหลดได้จาก [ที่นี่](https://releases.aspose.com/words/java/)  
- ความรู้พื้นฐานด้านการเขียนโปรแกรม Java

## ขั้นตอนที่ 1: สร้าง Document

เพื่อ **บันทึก word เป็น txt** เราต้องมีอินสแตนซ์ `Document` ก่อน ตัวอย่างโค้ด Java ง่าย ๆ ด้านล่างนี้สร้างเอกสารและเขียนข้อความหลายภาษาลงไป:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
builder.writeln("Hello world!");
builder.getParagraphFormat().setBidi(true);
builder.writeln("שלום עולם!");
builder.writeln("مرحبا بالعالم!");
```

ในโค้ดนี้ เราสร้างเอกสารใหม่, เพิ่มข้อความภาษาอังกฤษ, ฮีบรู, และอาหรับ, และเปิดการจัดรูปแบบขวา‑ซ้ายสำหรับย่อหน้าภาษาฮีบรู

## ขั้นตอนที่ 2: กำหนดตัวเลือกการบันทึกเป็นข้อความ

ต่อไปเราจะตั้งค่าการบันทึกเอกสารเป็นไฟล์ข้อความธรรมดา Aspose.Words มีคลาส `TxtSaveOptions` ที่ให้คุณควบคุมทุกอย่างตั้งแต่เครื่องหมาย bidi จนถึงการเยื้องรายการ

### ตัวอย่างที่ 1: เพิ่มเครื่องหมาย Bidi (วิธีบันทึก txt พร้อมรองรับ RTL อย่างถูกต้อง)

```java
TxtSaveOptions saveOptions = new TxtSaveOptions();
saveOptions.setAddBidiMarks(true);
doc.save("output.txt", saveOptions);
```

การตั้งค่า `AddBidiMarks` เป็น `true` จะทำให้ตัวอักษรขวา‑ซ้ายแสดงอย่างถูกต้องใน **ไฟล์ข้อความธรรมดา** ที่ได้

### ตัวอย่างที่ 2: ใช้ตัวอักษรแท็บสำหรับการเยื้องรายการ (use tab indentation)

```java
TxtSaveOptions saveOptions = new TxtSaveOptions();
saveOptions.getListIndentation().setCount(1);
saveOptions.getListIndentation().setCharacter('\t');
doc.save("output.txt", saveOptions);
```

ที่นี่เราบอก Aspose.Words ให้ใส่ตัวอักษรแท็บ (`'\t'`) ไว้หน้าระดับรายการแต่ละระดับ ทำให้ผลลัพธ์ข้อความอ่านง่ายขึ้น

## ขั้นตอนที่ 3: บันทึก Document เป็นข้อความ

เมื่อกำหนดตัวเลือกการบันทึกเรียบร้อยแล้ว คุณสามารถบันทึกเอกสารเป็น **ไฟล์ข้อความธรรมดา** ได้ดังนี้:

```java
doc.save("output.txt", saveOptions);
```

เปลี่ยน `"output.txt"` เป็นพาธเต็มที่คุณต้องการให้ไฟล์ถูกเก็บไว้

## โค้ดเต็มสำหรับการบันทึก Document เป็นไฟล์ข้อความใน Aspose.Words for Java

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
        // Create a list with three levels of indentation.
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
        // Create a list with three levels of indentation.
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

## ปัญหาที่พบบ่อยและวิธีแก้ไข

| ปัญหา | วิธีแก้ไข |
|-------|-----------|
| **ตัวอักษร bidi แสดงเป็นข้อความเสีย** | ตรวจสอบให้แน่ใจว่าเปิด `setAddBidiMarks(true)` แล้วเปิดไฟล์ผลลัพธ์ด้วยการเข้ารหัส UTF‑8 |
| **การเยื้องรายการแสดงไม่ถูกต้อง** | ตรวจสอบค่าของ `ListIndentation.Count` และ `Character` ให้เป็นค่าที่ต้องการ (แท็บ `'\t'` หรือช่องว่าง `' '` ) |
| **ไฟล์ไม่ถูกสร้าง** | ตรวจสอบว่าพาธไดเรกทอรีมีอยู่และแอปพลิเคชันมีสิทธิ์เขียน |

## คำถามที่พบบ่อย

### วิธีเพิ่มเครื่องหมาย bidi ให้กับผลลัพธ์ข้อความ?

```java
TxtSaveOptions saveOptions = new TxtSaveOptions();
saveOptions.setAddBidiMarks(true);
```

### สามารถกำหนดอักขระสำหรับการเยื้องรายการได้หรือไม่?

```java
TxtSaveOptions saveOptions = new TxtSaveOptions();
saveOptions.getListIndentation().setCount(1);
saveOptions.getListIndentation().setCharacter('\t');
```

### Aspose.Words for Java รองรับการจัดการข้อความหลายภาษาไหม?

ใช่, Aspose.Words for Java รองรับภาษาต่าง ๆ และการเข้ารหัสอักขระหลากหลาย ทำให้เหมาะสำหรับการดึงและบันทึกเนื้อหาหลายภาษาเป็นไฟล์ข้อความธรรมดา

### จะเข้าถึงเอกสารและแหล่งข้อมูลเพิ่มเติมของ Aspose.Words for Java ได้จากที่ไหน?

คุณสามารถดูเอกสารและแหล่งข้อมูลอย่างครบถ้วนได้ที่หน้า Aspose.Words for Java Documentation: [Aspose.Words for Java Documentation](https://reference.aspose.com/words/java/)

### สามารถดาวน์โหลด Aspose.Words for Java ได้จากที่ไหน?

ดาวน์โหลดไลบรารีได้จากเว็บไซต์อย่างเป็นทางการ: [Download Aspose.Words for Java](https://releases.aspose.com/words/java/)

### ถ้าต้องการ **แปลง word เป็น txt** เป็นกระบวนการแบบแบตช์ทำอย่างไร?

ให้ใส่โค้ดตัวอย่างข้างต้นในลูปที่โหลดไฟล์ `.docx` แต่ละไฟล์, ตั้งค่า `TxtSaveOptions` เดียวกัน, แล้วบันทึกเป็น `.txt` ตรวจสอบให้แน่ใจว่าปล่อย `Document` แต่ละออบเจ็กต์หลังการใช้งานเพื่อจัดการทรัพยากร

### API รองรับการบันทึกโดยตรงไปยังสตรีมแทนไฟล์หรือไม่?

ใช่, คุณสามารถส่ง `OutputStream` ให้กับ `doc.save(outputStream, saveOptions)` เพื่อประมวลผลในหน่วยความจำหรือเมื่อผสานกับบริการเว็บ

---

**อัปเดตล่าสุด:** 2025-12-24  
**ทดสอบด้วย:** Aspose.Words for Java 24.12 (ล่าสุด)  
**ผู้เขียน:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}