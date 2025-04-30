---
"description": "เรียนรู้วิธีบันทึกเอกสาร HTML ด้วยเค้าโครงคงที่ใน Aspose.Words สำหรับ Java ปฏิบัติตามคำแนะนำทีละขั้นตอนของเราเพื่อการจัดรูปแบบเอกสารอย่างราบรื่น"
"linktitle": "การบันทึกเอกสาร HTML ด้วยเค้าโครงคงที่"
"second_title": "API การประมวลผลเอกสาร Java ของ Aspose.Words"
"title": "การบันทึกเอกสาร HTML ที่มีเค้าโครงคงที่ใน Aspose.Words สำหรับ Java"
"url": "/th/java/document-loading-and-saving/saving-html-documents-with-fixed-layout/"
"weight": 15
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# การบันทึกเอกสาร HTML ที่มีเค้าโครงคงที่ใน Aspose.Words สำหรับ Java


## บทนำสู่การบันทึกเอกสาร HTML ที่มีเค้าโครงคงที่ใน Aspose.Words สำหรับ Java

ในคู่มือฉบับสมบูรณ์นี้ เราจะแนะนำคุณเกี่ยวกับขั้นตอนการบันทึกเอกสาร HTML ด้วยเค้าโครงคงที่โดยใช้ Aspose.Words สำหรับ Java พร้อมด้วยคำแนะนำทีละขั้นตอนและตัวอย่างโค้ด คุณจะได้เรียนรู้วิธีการดำเนินการนี้ได้อย่างราบรื่น มาเริ่มกันเลย!

## ข้อกำหนดเบื้องต้น

ก่อนที่เราจะเริ่ม โปรดตรวจสอบให้แน่ใจว่าคุณมีข้อกำหนดเบื้องต้นดังต่อไปนี้:

- การตั้งค่าสภาพแวดล้อมการพัฒนา Java
- ติดตั้งและกำหนดค่าไลบรารี Aspose.Words สำหรับ Java แล้ว

## ขั้นตอนที่ 1: การโหลดเอกสาร

ขั้นแรก เราต้องโหลดเอกสารที่เราต้องการบันทึกในรูปแบบ HTML โดยสามารถทำได้ดังนี้:

```java
Document doc = new Document("Your Directory Path" + "YourDocument.docx");
```

แทนที่ `"YourDocument.docx"` พร้อมเส้นทางไปยังเอกสาร Word ของคุณ

## ขั้นตอนที่ 2: กำหนดค่าตัวเลือกการบันทึกแบบคงที่ HTML

เพื่อบันทึกเอกสารด้วยเค้าโครงคงที่ เราจำเป็นต้องกำหนดค่า `HtmlFixedSaveOptions` ชั้นเรียน เราจะตั้งค่า `useTargetMachineFonts` ทรัพย์สินที่จะ `true` เพื่อให้แน่ใจว่าแบบอักษรของเครื่องเป้าหมายถูกใช้ในผลลัพธ์ HTML:

```java
HtmlFixedSaveOptions saveOptions = new HtmlFixedSaveOptions();
saveOptions.setUseTargetMachineFonts(true);
```

## ขั้นตอนที่ 3: บันทึกเอกสารเป็น HTML

ต่อไปเรามาบันทึกเอกสารเป็น HTML ที่มีเค้าโครงคงที่โดยใช้ตัวเลือกที่กำหนดค่าไว้ก่อนหน้านี้:

```java
doc.save("Your Directory Path" + "FixedLayoutDocument.html", saveOptions);
```

แทนที่ `"FixedLayoutDocument.html"` พร้อมชื่อที่ต้องการให้กับไฟล์ HTML ของคุณ

## โค้ดต้นฉบับสมบูรณ์สำหรับการบันทึกเอกสาร HTML ที่มีเค้าโครงคงที่ใน Aspose.Words สำหรับ Java

```java
        Document doc = new Document("Your Directory Path" + "Bullet points with alternative font.docx");
        HtmlFixedSaveOptions saveOptions = new HtmlFixedSaveOptions();
        {
            saveOptions.setUseTargetMachineFonts(true);
        }
        doc.save("Your Directory Path" + "WorkingWithHtmlFixedSaveOptions.UseFontFromTargetMachine.html", saveOptions);
    }
```

## บทสรุป

ในบทช่วยสอนนี้ เราได้เรียนรู้วิธีการบันทึกเอกสาร HTML ด้วยเค้าโครงคงที่โดยใช้ Aspose.Words สำหรับ Java โดยทำตามขั้นตอนง่ายๆ เหล่านี้ คุณสามารถมั่นใจได้ว่าเอกสารของคุณมีโครงสร้างภาพที่สอดคล้องกันบนแพลตฟอร์มต่างๆ

## คำถามที่พบบ่อย

### ฉันจะตั้งค่า Aspose.Words สำหรับ Java ในโปรเจ็กต์ของฉันได้อย่างไร

การตั้งค่า Aspose.Words สำหรับ Java นั้นทำได้ง่าย คุณสามารถดาวน์โหลดไลบรารีได้จาก [ที่นี่](https://releases.aspose.com/words/java/) และปฏิบัติตามคำแนะนำในการติดตั้งที่ระบุไว้ในเอกสารประกอบ [ที่นี่](https://reference-aspose.com/words/java/).

### มีข้อกำหนดการออกใบอนุญาตสำหรับการใช้ Aspose.Words สำหรับ Java หรือไม่

ใช่ Aspose.Words สำหรับ Java ต้องมีใบอนุญาตที่ถูกต้องจึงจะใช้ในสภาพแวดล้อมการผลิตได้ คุณสามารถขอรับใบอนุญาตได้จากเว็บไซต์ Aspose สามารถดูรายละเอียดเพิ่มเติมได้ในเอกสารประกอบ

### ฉันสามารถปรับแต่งเอาต์พุต HTML เพิ่มเติมได้หรือไม่

แน่นอน! Aspose.Words สำหรับ Java มีตัวเลือกมากมายสำหรับการปรับแต่งเอาต์พุต HTML ให้ตรงตามความต้องการเฉพาะของคุณ คุณสามารถศึกษาเอกสารประกอบเพื่อดูข้อมูลโดยละเอียดเกี่ยวกับตัวเลือกการปรับแต่ง

### Aspose.Words สำหรับ Java สามารถใช้งานร่วมกับ Java เวอร์ชันต่างๆ ได้หรือไม่

ใช่ Aspose.Words สำหรับ Java เข้ากันได้กับ Java เวอร์ชันต่างๆ ตรวจสอบให้แน่ใจว่าคุณใช้ Aspose.Words สำหรับ Java เวอร์ชันที่เข้ากันได้ซึ่งตรงกับสภาพแวดล้อมการพัฒนา Java ของคุณ


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}