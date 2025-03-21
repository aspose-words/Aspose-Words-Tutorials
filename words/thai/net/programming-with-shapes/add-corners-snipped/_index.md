---
title: เพิ่มมุมที่ถูกตัดออก
linktitle: เพิ่มมุมที่ถูกตัดออก
second_title: API การประมวลผลเอกสาร Aspose.Words
description: เรียนรู้วิธีการเพิ่มรูปร่างมุมตัดลงในเอกสาร Word ของคุณโดยใช้ Aspose.Words สำหรับ .NET คำแนะนำทีละขั้นตอนนี้จะช่วยให้คุณปรับปรุงเอกสารของคุณได้อย่างง่ายดาย
weight: 10
url: /th/net/programming-with-shapes/add-corners-snipped/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# เพิ่มมุมที่ถูกตัดออก

## การแนะนำ

การเพิ่มรูปร่างที่กำหนดเองลงในเอกสาร Word ของคุณนั้นเป็นวิธีที่สนุกและดึงดูดสายตาในการเน้นข้อมูลที่สำคัญหรือเพิ่มความสวยงามให้กับเนื้อหาของคุณ ในบทช่วยสอนนี้ เราจะเจาะลึกถึงวิธีการแทรกรูปร่าง "Corners Snipped" ลงในเอกสาร Word ของคุณโดยใช้ Aspose.Words สำหรับ .NET คู่มือนี้จะแนะนำคุณตลอดทุกขั้นตอน เพื่อให้แน่ใจว่าคุณสามารถเพิ่มรูปร่างเหล่านี้ได้อย่างง่ายดายและปรับแต่งเอกสารของคุณได้อย่างมืออาชีพ

## ข้อกำหนดเบื้องต้น

ก่อนที่เราจะเริ่มต้นใช้งานโค้ด เรามาตรวจสอบก่อนว่าคุณมีทุกสิ่งที่จำเป็นในการเริ่มต้น:

1.  Aspose.Words สำหรับ .NET: หากคุณยังไม่ได้ดาวน์โหลดเวอร์ชันล่าสุดจาก[หน้าวางจำหน่าย Aspose](https://releases.aspose.com/words/net/).
2. สภาพแวดล้อมการพัฒนา: ตั้งค่าสภาพแวดล้อมการพัฒนาของคุณ Visual Studio เป็นตัวเลือกยอดนิยม แต่คุณสามารถใช้ IDE ใดๆ ที่รองรับ .NET ได้
3.  ใบอนุญาต: หากคุณแค่ทดลอง คุณสามารถใช้[ทดลองใช้งานฟรี](https://releases.aspose.com/) หรือรับ[ใบอนุญาตชั่วคราว](https://purchase.aspose.com/temporary-license/) เพื่อปลดล็อคฟังก์ชั่นเต็มรูปแบบ
4. ความเข้าใจพื้นฐานเกี่ยวกับ C#: ความคุ้นเคยกับการเขียนโปรแกรม C# จะช่วยให้คุณทำตามตัวอย่างได้

## นำเข้าเนมสเปซ

ก่อนที่เราจะเริ่มทำงานกับ Aspose.Words สำหรับ .NET เราจะต้องนำเข้าเนมสเปซที่จำเป็นก่อน โดยเพิ่มสิ่งเหล่านี้ไว้ที่ด้านบนของไฟล์ C#:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
```

ตอนนี้เรามาแบ่งกระบวนการในการเพิ่มรูปทรง "Corners Snipped" ออกเป็นหลายขั้นตอน ปฏิบัติตามขั้นตอนเหล่านี้อย่างใกล้ชิดเพื่อให้แน่ใจว่าทุกอย่างทำงานได้อย่างราบรื่น

## ขั้นตอนที่ 1: เริ่มต้นใช้งาน Document และ DocumentBuilder

 สิ่งแรกที่เราต้องทำคือสร้างเอกสารใหม่และเริ่มต้นใช้งาน`DocumentBuilder` วัตถุ ตัวสร้างนี้จะช่วยให้เราเพิ่มเนื้อหาลงในเอกสารของเรา

```csharp
// เส้นทางไปยังไดเรกทอรีเอกสารของคุณ
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

 ในขั้นตอนนี้ เราได้ตั้งค่าเอกสารและตัวสร้างของเราแล้ว ลองนึกถึง`DocumentBuilder` เป็นปากกาแบบดิจิทัลของคุณ พร้อมสำหรับการเขียนและวาดลงในเอกสาร Word ของคุณ

## ขั้นตอนที่ 2: ใส่รูปทรงที่ตัดมุมแล้ว

 ต่อไปเราจะใช้`DocumentBuilder` การแทรกรูปทรง "Corners Snipped" รูปทรงประเภทนี้ถูกกำหนดไว้ล่วงหน้าใน Aspose.Words และสามารถแทรกได้ง่าย ๆ ด้วยโค้ดเพียงบรรทัดเดียว

```csharp
builder.InsertShape(ShapeType.TopCornersSnipped, 50, 50);
```

ที่นี่ เราจะระบุประเภทรูปร่างและขนาดของรูปร่าง (50x50) ลองนึกภาพว่าคุณกำลังติดสติกเกอร์มุมเล็กๆ ที่ตัดมาอย่างสมบูรณ์แบบบนเอกสารของคุณ 

## ขั้นตอนที่ 3: กำหนดตัวเลือกการบันทึกพร้อมการปฏิบัติตาม

ก่อนที่จะบันทึกเอกสารของเรา เราจำเป็นต้องกำหนดตัวเลือกการบันทึกเพื่อให้แน่ใจว่าเอกสารของเราเป็นไปตามมาตรฐานเฉพาะ เราจะใช้`OoxmlSaveOptions` ชั้นเรียนสำหรับสิ่งนี้

```csharp
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions(SaveFormat.Docx)
{
    Compliance = OoxmlCompliance.Iso29500_2008_Transitional
};
```

ตัวเลือกการบันทึกเหล่านี้ช่วยให้แน่ใจว่าเอกสารของเราปฏิบัติตามมาตรฐาน ISO/IEC 29500:2008 ซึ่งเป็นสิ่งสำคัญสำหรับความเข้ากันได้และอายุการใช้งานของเอกสาร

## ขั้นตอนที่ 4: บันทึกเอกสาร

ในที่สุด เราบันทึกเอกสารของเราไปยังไดเร็กทอรีที่ระบุโดยใช้ตัวเลือกบันทึกที่เรากำหนดไว้ก่อนหน้านี้

```csharp
doc.Save(dataDir + "WorkingWithShapes.AddCornersSnipped.docx", saveOptions);
```

และเพียงเท่านี้ เอกสารของคุณจะมีรูปร่าง "ตัดมุม" ที่กำหนดเอง ซึ่งบันทึกด้วยตัวเลือกการปฏิบัติตามข้อกำหนดที่จำเป็น

## บทสรุป

เท่านี้คุณก็ทำได้แล้ว! การเพิ่มรูปร่างที่กำหนดเองลงในเอกสาร Word ของคุณโดยใช้ Aspose.Words สำหรับ .NET นั้นทำได้ง่าย และสามารถเพิ่มความสวยงามให้กับเอกสารของคุณได้อย่างมาก ด้วยการทำตามขั้นตอนเหล่านี้ คุณสามารถแทรกรูปร่าง "Corners Snipped" ได้อย่างง่ายดาย และมั่นใจได้ว่าเอกสารของคุณจะตรงตามมาตรฐานที่กำหนด ขอให้สนุกกับการเขียนโค้ด!

## คำถามที่พบบ่อย

### ฉันสามารถกำหนดขนาดของรูปร่าง "Corners Snipped" ได้หรือไม่?
ใช่ คุณสามารถปรับขนาดได้โดยการเปลี่ยนขนาดใน`InsertShape` วิธี.

### สามารถเพิ่มรูปทรงอื่น ๆ ได้หรือไม่?
 แน่นอน! Aspose.Words รองรับรูปทรงต่างๆ เพียงเปลี่ยน`ShapeType` ให้เป็นรูปร่างตามที่คุณต้องการ

### ฉันต้องมีใบอนุญาตเพื่อใช้ Aspose.Words หรือไม่?
แม้ว่าคุณจะสามารถใช้รุ่นทดลองใช้งานฟรีหรือใบอนุญาตชั่วคราวได้ แต่จำเป็นต้องมีใบอนุญาตเต็มรูปแบบจึงจะใช้งานได้แบบไม่มีข้อจำกัด

### ฉันจะปรับแต่งรูปทรงเพิ่มเติมได้อย่างไร?
คุณสามารถใช้คุณสมบัติและวิธีการเพิ่มเติมที่ให้มาโดย Aspose.Words เพื่อปรับแต่งลักษณะที่ปรากฏและพฤติกรรมของรูปทรงได้

### Aspose.Words เข้ากันได้กับรูปแบบอื่นหรือไม่
ใช่ Aspose.Words รองรับรูปแบบเอกสารหลายรูปแบบ รวมถึง DOCX, PDF, HTML และอื่นๆ อีกมากมาย
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
