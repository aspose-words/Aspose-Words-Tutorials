---
title: ตั้งค่าตำแหน่งสัมพันธ์แนวนอนหรือแนวตั้ง
linktitle: ตั้งค่าตำแหน่งสัมพันธ์แนวนอนหรือแนวตั้ง
second_title: API การประมวลผลเอกสาร Aspose.Words
description: เรียนรู้วิธีการตั้งค่าตำแหน่งแนวนอนและแนวตั้งสัมพันธ์สำหรับตารางในเอกสาร Word โดยใช้ Aspose.Words สำหรับ .NET ด้วยคู่มือทีละขั้นตอนนี้
weight: 10
url: /th/net/programming-with-tables/set-relative-horizontal-or-vertical-position/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# ตั้งค่าตำแหน่งสัมพันธ์แนวนอนหรือแนวตั้ง

## การแนะนำ

เคยรู้สึกติดขัดกับการจัดวางตารางในเอกสาร Word อย่างไรให้ถูกต้องหรือไม่? ไม่ใช่คุณคนเดียวที่คิดเช่นนั้น ไม่ว่าคุณจะกำลังสร้างรายงานระดับมืออาชีพหรือโบรชัวร์ที่มีสไตล์ การจัดวางตารางให้ตรงกันก็สามารถสร้างความแตกต่างได้อย่างมาก นั่นคือจุดที่ Aspose.Words สำหรับ .NET มีประโยชน์ บทช่วยสอนนี้จะแนะนำคุณทีละขั้นตอนเกี่ยวกับวิธีตั้งค่าตำแหน่งแนวนอนหรือแนวตั้งสัมพันธ์กันสำหรับตารางในเอกสาร Word ของคุณ มาเริ่มกันเลย!

## ข้อกำหนดเบื้องต้น

ก่อนที่เราจะเริ่ม โปรดตรวจสอบให้แน่ใจว่าคุณมีสิ่งต่อไปนี้:

1.  Aspose.Words สำหรับ .NET: หากคุณยังไม่ได้ดาวน์โหลด คุณสามารถดาวน์โหลดได้[ที่นี่](https://releases.aspose.com/words/net/).
2. สภาพแวดล้อมการพัฒนา: Visual Studio หรือ IDE อื่น ๆ ที่เข้ากันได้กับ .NET
3. ความรู้พื้นฐานเกี่ยวกับ C#: บทช่วยสอนนี้ถือว่าคุณมีความคุ้นเคยกับพื้นฐานของการเขียนโปรแกรม C#

## นำเข้าเนมสเปซ

สิ่งแรกที่ต้องทำคือนำเข้าเนมสเปซที่จำเป็น ซึ่งถือเป็นสิ่งสำคัญสำหรับการเข้าถึงฟังก์ชันการทำงานของ Aspose.Words

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
```

## ขั้นตอนที่ 1: โหลดเอกสารของคุณ

ในการเริ่มต้น คุณจะต้องโหลดเอกสาร Word ของคุณลงในโปรแกรม โดยคุณสามารถทำได้ดังนี้:

```csharp
// เส้นทางไปยังไดเรกทอรีเอกสารของคุณ
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document(dataDir + "Table wrapped by text.docx");
```

โค้ดสั้นๆ นี้จะตั้งค่าเส้นทางไปยังไดเรกทอรีเอกสารของคุณและโหลดเอกสารเฉพาะที่คุณต้องการใช้งาน ตรวจสอบให้แน่ใจว่าเส้นทางเอกสารของคุณถูกต้องเพื่อหลีกเลี่ยงปัญหาในการโหลด

## ขั้นตอนที่ 2: เข้าถึงตาราง

ขั้นต่อไป เราต้องเข้าถึงตารางภายในเอกสาร โดยปกติ คุณจะต้องการทำงานกับตารางแรกในส่วนเนื้อหา

```csharp
Table table = doc.FirstSection.Body.Tables[0];
```

โค้ดบรรทัดนี้จะดึงตารางแรกจากเนื้อหาของเอกสาร หากเอกสารของคุณมีตารางหลายตาราง คุณสามารถปรับดัชนีให้เหมาะสมได้

## ขั้นตอนที่ 3: ตั้งค่าตำแหน่งแนวนอน

ตอนนี้เรามากำหนดตำแหน่งแนวนอนของตารางโดยสัมพันธ์กับองค์ประกอบเฉพาะ ในตัวอย่างนี้ เราจะกำหนดตำแหน่งตารางโดยสัมพันธ์กับคอลัมน์

```csharp
table.HorizontalAnchor = RelativeHorizontalPosition.Column;
```

 โดยการตั้งค่า`HorizontalAnchor` ถึง`RelativeHorizontalPosition.Column`คุณกำลังสั่งให้ตารางจัดแนวตัวเองในแนวนอนเทียบกับคอลัมน์ที่ตารางตั้งอยู่

## ขั้นตอนที่ 4: ตั้งค่าตำแหน่งแนวตั้ง

การวางตำแหน่งในแนวนอนนั้น คุณสามารถกำหนดตำแหน่งในแนวตั้งได้เช่นกัน โดยในที่นี้ เราจะวางตำแหน่งให้สัมพันธ์กับหน้ากระดาษ

```csharp
table.VerticalAnchor = RelativeVerticalPosition.Page;
```

 การตั้งค่า`VerticalAnchor` ถึง`RelativeVerticalPosition.Page` ช่วยให้แน่ใจว่าตารางจะเรียงตามแนวตั้งตามหน้า

## ขั้นตอนที่ 5: บันทึกเอกสารของคุณ

สุดท้าย ให้บันทึกการเปลี่ยนแปลงของคุณลงในเอกสารใหม่ นี่เป็นขั้นตอนสำคัญเพื่อให้แน่ใจว่าการเปลี่ยนแปลงของคุณได้รับการรักษาไว้

```csharp
doc.Save(dataDir + "WorkingWithTables.SetFloatingTablePosition.docx");
```

คำสั่งนี้จะบันทึกเอกสารที่แก้ไขด้วยชื่อใหม่ โดยรับประกันว่าคุณจะไม่เขียนทับไฟล์ต้นฉบับ

## บทสรุป

และแล้วคุณก็ทำได้! คุณได้กำหนดตำแหน่งแนวนอนและแนวตั้งที่สัมพันธ์กันสำหรับตารางในเอกสาร Word สำเร็จแล้วโดยใช้ Aspose.Words สำหรับ .NET ด้วยทักษะใหม่นี้ คุณสามารถปรับปรุงเค้าโครงและการอ่านเอกสารของคุณ ทำให้เอกสารดูเป็นมืออาชีพและสวยงามมากขึ้น ทดลองใช้ตำแหน่งต่างๆ ต่อไปและดูว่าตำแหน่งใดเหมาะกับความต้องการของคุณที่สุด

## คำถามที่พบบ่อย

### ฉันสามารถวางตำแหน่งตารางสัมพันธ์กับองค์ประกอบอื่นได้หรือไม่  
ใช่ Aspose.Words ช่วยให้คุณวางตำแหน่งตารางสัมพันธ์กับองค์ประกอบต่างๆ เช่น ระยะขอบ หน้า คอลัมน์ และอื่นๆ อีกมากมาย

### ฉันต้องมีใบอนุญาตเพื่อใช้ Aspose.Words สำหรับ .NET หรือไม่?  
 ใช่ คุณสามารถซื้อใบอนุญาตได้[ที่นี่](https://purchase.aspose.com/buy) หรือรับใบอนุญาตชั่วคราว[ที่นี่](https://purchase.aspose.com/temporary-license/).

### มี Aspose.Words สำหรับ .NET ให้ทดลองใช้งานฟรีหรือไม่  
 แน่นอน! คุณสามารถดาวน์โหลดรุ่นทดลองใช้งานฟรีได้[ที่นี่](https://releases.aspose.com/).

### ฉันสามารถใช้ Aspose.Words กับภาษาการเขียนโปรแกรมอื่นได้หรือไม่  
Aspose.Words ได้รับการออกแบบมาโดยเฉพาะสำหรับ .NET แต่ยังมีเวอร์ชันสำหรับ Java, Python และแพลตฟอร์มอื่นๆ อีกด้วย

### ฉันสามารถหาเอกสารรายละเอียดเพิ่มเติมได้ที่ไหน  
หากต้องการข้อมูลเชิงลึกเพิ่มเติม โปรดดูเอกสาร Aspose.Words[ที่นี่](https://reference.aspose.com/words/net/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
