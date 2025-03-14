---
title: ตัวเลือกการจัดการช่องว่าง
linktitle: ตัวเลือกการจัดการช่องว่าง
second_title: API การประมวลผลเอกสาร Aspose.Words
description: เรียนรู้วิธีการจัดการช่องว่างด้านหน้าและด้านหลังในเอกสารข้อความด้วย Aspose.Words สำหรับ .NET บทช่วยสอนนี้ให้คำแนะนำในการทำความสะอาดการจัดรูปแบบข้อความ
weight: 10
url: /th/net/programming-with-txtloadoptions/handle-spaces-options/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# ตัวเลือกการจัดการช่องว่าง

## การแนะนำ

การจัดการช่องว่างในเอกสารข้อความบางครั้งอาจดูเหมือนเป็นงานที่ต้องจัดการหลายอย่าง ช่องว่างอาจแทรกซึมเข้ามาในตำแหน่งที่คุณไม่ต้องการหรือหายไปในตำแหน่งที่จำเป็น เมื่อใช้งาน Aspose.Words สำหรับ .NET คุณจะมีเครื่องมือในการจัดการช่องว่างเหล่านี้ได้อย่างแม่นยำและมีประสิทธิภาพ ในบทช่วยสอนนี้ เราจะเจาะลึกถึงวิธีจัดการช่องว่างในเอกสารข้อความโดยใช้ Aspose.Words โดยเน้นที่ช่องว่างด้านหน้าและด้านหลัง

## ข้อกำหนดเบื้องต้น

ก่อนที่เราจะเริ่ม โปรดตรวจสอบให้แน่ใจว่าคุณมี:

-  Aspose.Words สำหรับ .NET: คุณจะต้องติดตั้งไลบรารีนี้ในสภาพแวดล้อม .NET ของคุณ คุณสามารถรับได้จาก[เว็บไซต์อาโพส](https://releases.aspose.com/words/net/).
- Visual Studio: สภาพแวดล้อมการพัฒนาแบบบูรณาการ (IDE) สำหรับการเขียนโค้ด Visual Studio ช่วยให้ทำงานกับโปรเจ็กต์ .NET ได้ง่ายขึ้น
- ความรู้พื้นฐานเกี่ยวกับ C#: ความคุ้นเคยกับการเขียนโปรแกรม C# จะเป็นประโยชน์เนื่องจากเราจะเขียนโค้ดบางส่วน

## นำเข้าเนมสเปซ

ในการใช้งาน Aspose.Words ในโปรเจ็กต์ .NET ของคุณ ก่อนอื่นคุณต้องนำเข้าเนมสเปซที่จำเป็น เพิ่มคำสั่ง using ต่อไปนี้ที่ส่วนบนของไฟล์ C#:

```csharp
using Aspose.Words;
using Aspose.Words.Loading;
using System.IO;
using System.Text;
```

เนมสเปซเหล่านี้รวมฟังก์ชันหลักสำหรับการจัดการเอกสาร ตัวเลือกการโหลด และการทำงานกับสตรีมไฟล์

## ขั้นตอนที่ 1: กำหนดเส้นทางไปยังไดเรกทอรีเอกสารของคุณ

ขั้นแรก ให้ระบุเส้นทางที่คุณต้องการบันทึกเอกสาร นี่คือจุดที่ Aspose.Words จะส่งออกไฟล์ที่แก้ไข

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

 แทนที่`"YOUR DOCUMENT DIRECTORY"` ด้วยเส้นทางจริงที่คุณต้องการเก็บเอกสารของคุณ เส้นทางนี้มีความสำคัญเนื่องจากจะกำหนด Aspose.Words ว่าจะบันทึกไฟล์เอาต์พุตไปที่ใด

## ขั้นตอนที่ 2: สร้างเอกสารข้อความตัวอย่าง

ต่อไป ให้กำหนดข้อความตัวอย่างที่มีช่องว่างนำหน้าและต่อท้ายที่ไม่สอดคล้องกัน นี่คือข้อความที่เราจะประมวลผลโดยใช้ Aspose.Words

```csharp
const string textDoc = "      Line 1 \n" +
                       "    Line 2   \n" +
                       " Line 3       ";
```

 ที่นี่,`textDoc` เป็นสตริงที่จำลองไฟล์ข้อความที่มีช่องว่างพิเศษก่อนและหลังแต่ละบรรทัด ซึ่งจะช่วยให้เราเห็นว่า Aspose.Words จัดการกับช่องว่างเหล่านี้อย่างไร

## ขั้นตอนที่ 3: ตั้งค่าตัวเลือกการโหลดสำหรับการจัดการพื้นที่

 หากต้องการควบคุมวิธีการจัดการช่องว่างด้านหน้าและด้านหลัง คุณจำเป็นต้องกำหนดค่า`TxtLoadOptions` วัตถุ วัตถุนี้ช่วยให้คุณระบุได้ว่าจะต้องจัดการช่องว่างอย่างไรเมื่อโหลดไฟล์ข้อความ

```csharp
TxtLoadOptions loadOptions = new TxtLoadOptions
{
    LeadingSpacesOptions = TxtLeadingSpacesOptions.Trim,
    TrailingSpacesOptions = TxtTrailingSpacesOptions.Trim
};
```

ในการกำหนดค่านี้:
- `LeadingSpacesOptions = TxtLeadingSpacesOptions.Trim`รับประกันว่าช่องว่างใดๆ ในตอนต้นบรรทัดจะถูกลบออก
- `TrailingSpacesOptions = TxtTrailingSpacesOptions.Trim` รับประกันว่าช่องว่างใดๆ ที่อยู่ตอนท้ายบรรทัดจะถูกลบออก

การตั้งค่านี้มีความจำเป็นสำหรับการทำความสะอาดไฟล์ข้อความก่อนที่จะประมวลผลหรือบันทึก

## ขั้นตอนที่ 4: โหลดเอกสารข้อความพร้อมตัวเลือก

 ตอนนี้เราได้กำหนดค่าตัวเลือกการโหลดแล้ว ใช้ตัวเลือกเหล่านี้เพื่อโหลดเอกสารข้อความตัวอย่างลงใน Aspose.Words`Document` วัตถุ.

```csharp
Document doc = new Document(new MemoryStream(Encoding.UTF8.GetBytes(textDoc)), loadOptions);
```

 ที่นี่เราจะสร้าง`MemoryStream` จากตัวอย่างข้อความเข้ารหัสและส่งไปยัง`Document` constructor พร้อมกับตัวเลือกการโหลดของเรา ขั้นตอนนี้จะอ่านข้อความและใช้กฎการจัดการพื้นที่

## ขั้นตอนที่ 5: บันทึกเอกสาร

สุดท้าย ให้บันทึกเอกสารที่ประมวลผลแล้วลงในไดเร็กทอรีที่คุณระบุ ขั้นตอนนี้จะเขียนเอกสารที่ทำความสะอาดแล้วลงในไฟล์

```csharp
doc.Save(dataDir + "WorkingWithTxtLoadOptions.HandleSpacesOptions.docx");
```

 รหัสนี้จะบันทึกเอกสารพร้อมช่องว่างที่ทำความสะอาดแล้วลงในไฟล์ที่ชื่อ`WorkingWithTxtLoadOptions.HandleSpacesOptions.docx` ในไดเร็กทอรีที่คุณกำหนด

## บทสรุป

การจัดการช่องว่างในเอกสารข้อความเป็นงานทั่วไปแต่มีความสำคัญเมื่อทำงานกับไลบรารีการประมวลผลข้อความ ด้วย Aspose.Words สำหรับ .NET การจัดการช่องว่างด้านหน้าและด้านหลังจะกลายเป็นเรื่องง่ายดายด้วย`TxtLoadOptions` ชั้นเรียน โดยทำตามขั้นตอนในบทช่วยสอนนี้ คุณสามารถมั่นใจได้ว่าเอกสารของคุณสะอาดและมีการจัดรูปแบบตามความต้องการของคุณ ไม่ว่าคุณจะกำลังเตรียมข้อความสำหรับรายงานหรือทำความสะอาดข้อมูล เทคนิคเหล่านี้จะช่วยให้คุณควบคุมลักษณะที่ปรากฏของเอกสารได้

## คำถามที่พบบ่อย

### ฉันจะจัดการช่องว่างในไฟล์ข้อความโดยใช้ Aspose.Words สำหรับ .NET ได้อย่างไร  
 คุณสามารถใช้`TxtLoadOptions` คลาสเพื่อระบุว่าควรจัดการช่องว่างนำหน้าและต่อท้ายอย่างไรเมื่อโหลดไฟล์ข้อความ

### ฉันสามารถเว้นวรรคนำหน้าในเอกสารของฉันได้ไหม  
 ใช่ คุณสามารถกำหนดค่าได้`TxtLoadOptions` เพื่อรักษาพื้นที่นำหน้าด้วยการตั้งค่า`LeadingSpacesOptions` ถึง`TxtLeadingSpacesOptions.None`.

### จะเกิดอะไรขึ้นถ้าฉันไม่ตัดช่องว่างท้ายข้อความ?  
หากไม่ตัดช่องว่างท้ายบรรทัด ช่องว่างเหล่านั้นจะยังคงอยู่ที่ท้ายบรรทัดในเอกสารของคุณ ซึ่งอาจส่งผลต่อการจัดรูปแบบหรือรูปลักษณ์

### ฉันสามารถใช้ Aspose.Words เพื่อจัดการช่องว่างประเภทอื่นได้หรือไม่  
Aspose.Words มุ่งเน้นที่ช่องว่างนำหน้าและต่อท้ายเป็นหลัก หากต้องการจัดการช่องว่างที่ซับซ้อนกว่านี้ คุณอาจต้องใช้การประมวลผลเพิ่มเติม

### ฉันสามารถหาข้อมูลเพิ่มเติมเกี่ยวกับ Aspose.Words สำหรับ .NET ได้จากที่ไหน  
 คุณสามารถเยี่ยมชม[เอกสารประกอบ Aspose.Words](https://reference.aspose.com/words/net/) สำหรับข้อมูลและทรัพยากรโดยละเอียดเพิ่มเติม
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
