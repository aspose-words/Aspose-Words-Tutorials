---
"description": "แปลงเมตาไฟล์เป็น SVG ในเอกสาร Word โดยใช้ Aspose.Words สำหรับ .NET ด้วยคู่มือทีละขั้นตอนโดยละเอียดนี้ เหมาะสำหรับนักพัฒนาในทุกระดับ"
"linktitle": "แปลงไฟล์ Metafile เป็น SVG"
"second_title": "API การประมวลผลเอกสาร Aspose.Words"
"title": "แปลงไฟล์ Metafile เป็น SVG"
"url": "/th/net/programming-with-htmlsaveoptions/convert-metafiles-to-svg/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# แปลงไฟล์ Metafile เป็น SVG

## การแนะนำ

สวัสดีผู้ชื่นชอบการเขียนโค้ด! คุณเคยสงสัยไหมว่าจะแปลงไฟล์เมตาเป็น SVG ในเอกสาร Word ของคุณโดยใช้ Aspose.Words สำหรับ .NET ได้อย่างไร? รับรองว่าคุณจะต้องติดใจ! วันนี้เราจะมาเจาะลึกในโลกของ Aspose.Words ซึ่งเป็นไลบรารีอันทรงพลังที่ทำให้การจัดการเอกสารเป็นเรื่องง่าย เมื่ออ่านบทช่วยสอนนี้จบ คุณจะกลายเป็นผู้เชี่ยวชาญในการแปลงไฟล์เมตาเป็น SVG ทำให้เอกสาร Word ของคุณมีความหลากหลายและสวยงามมากขึ้น ดังนั้นมาเริ่มกันเลยดีกว่า

## ข้อกำหนดเบื้องต้น

ก่อนที่เราจะลงรายละเอียด เรามาตรวจสอบให้แน่ใจก่อนว่าเรามีทุกสิ่งที่จำเป็นสำหรับการเริ่มต้น:

1. Aspose.Words สำหรับ .NET: คุณสามารถดาวน์โหลดได้จาก [หน้าวางจำหน่าย Aspose](https://releases-aspose.com/words/net/).
2. .NET Framework: ตรวจสอบให้แน่ใจว่าคุณได้ติดตั้ง .NET Framework ไว้ในเครื่องของคุณแล้ว
3. สภาพแวดล้อมการพัฒนา: IDE ใดๆ เช่น Visual Studio ก็สามารถทำได้
4. ความรู้พื้นฐานเกี่ยวกับ C#: ความคุ้นเคยกับ C# เล็กน้อยจะเป็นประโยชน์ แต่ไม่ต้องกังวลหากคุณเป็นมือใหม่ เราจะอธิบายทุกอย่างอย่างละเอียด

## นำเข้าเนมสเปซ

ขั้นแรกเรามาทำการนำเข้ากันก่อน ในโปรเจ็กต์ C# ของคุณ คุณจะต้องนำเข้าเนมสเปซที่จำเป็น ซึ่งเป็นสิ่งสำคัญสำหรับการเข้าถึงฟังก์ชัน Aspose.Words

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

ตอนนี้เราได้กำหนดข้อกำหนดเบื้องต้นและเนมสเปซเรียบร้อยแล้ว มาดูคำแนะนำทีละขั้นตอนในการแปลงเมตาไฟล์เป็น SVG กัน

## ขั้นตอนที่ 1: เริ่มต้นใช้งาน Document และ DocumentBuilder

เอาล่ะ มาเริ่มต้นด้วยการสร้างเอกสาร Word ใหม่และเริ่มต้นใช้งาน `DocumentBuilder` วัตถุ ตัวสร้างนี้จะช่วยให้เราเพิ่มเนื้อหาลงในเอกสารของเรา

```csharp
// เส้นทางไปยังไดเร็กทอรีเอกสาร
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

ที่นี่ เราจะเริ่มต้นเอกสารใหม่และตัวสร้างเอกสาร `dataDir` ตัวแปรเก็บเส้นทางไปยังไดเร็กทอรีเอกสารที่คุณจะบันทึกไฟล์ของคุณ

## ขั้นตอนที่ 2: เพิ่มข้อความลงในเอกสาร

ต่อไปเรามาเพิ่มข้อความลงในเอกสารกัน เราจะใช้ `Write` วิธีการของ `DocumentBuilder` การแทรกข้อความ

```csharp
builder.Write("Here is an SVG image: ");
```

บรรทัดนี้จะเพิ่มข้อความ "นี่คือภาพ SVG: " ลงในเอกสารของคุณ ควรให้บริบทหรือคำอธิบายสำหรับภาพ SVG ที่คุณกำลังจะแทรกเข้าไป

## ขั้นตอนที่ 3: แทรกภาพ SVG

ตอนนี้มาถึงส่วนสนุก ๆ แล้ว! เราจะแทรกภาพ SVG ลงในเอกสารของเราโดยใช้ `InsertHtml` วิธี.

```csharp
builder.InsertHtml(
    @"<svg height='210' width='500'>
    <polygon points='100,10 40,198 190,78 10,78 160,198' 
    style='fill:lime;stroke:purple;stroke-width:5;fill-rule:evenodd;' />
</svg> ");
```

สไนปเป็ตนี้จะแทรกภาพ SVG ลงในเอกสาร รหัส SVG จะกำหนดรูปหลายเหลี่ยมธรรมดาที่มีจุด สี และรูปแบบที่กำหนดไว้ คุณสามารถปรับแต่งรหัส SVG ตามความต้องการของคุณได้

## ขั้นตอนที่ 4: กำหนด HtmlSaveOptions

เพื่อให้แน่ใจว่าเมตาไฟล์ของเราได้รับการบันทึกเป็น SVG เราจะกำหนด `HtmlSaveOptions` และตั้งค่า `MetafileFormat` ทรัพย์สินที่จะ `HtmlMetafileFormat-Svg`.

```csharp
HtmlSaveOptions saveOptions = new HtmlSaveOptions
{
    MetafileFormat = HtmlMetafileFormat.Svg
};
```

ซึ่งจะแจ้งให้ Aspose.Words บันทึกเมตาไฟล์ใดๆ ในเอกสารเป็น SVG เมื่อส่งออกเป็น HTML

## ขั้นตอนที่ 5: บันทึกเอกสาร

สุดท้ายนี้เรามาบันทึกเอกสารของเรากัน เราจะใช้ `Save` วิธีการของ `Document` คลาสและส่งผ่านเส้นทางไดเร็กทอรีและบันทึกตัวเลือก

```csharp
doc.Save(dataDir + "WorkingWithHtmlSaveOptions.ConvertMetafilesToSvg.html", saveOptions);
```

บรรทัดนี้จะบันทึกเอกสารไปยังไดเร็กทอรีที่ระบุโดยมีชื่อไฟล์ `WorkingWithHtmlSaveOptions.ConvertMetafilesToSvg.html`. การ `saveOptions` ตรวจสอบให้แน่ใจว่าเมตาไฟล์ถูกแปลงเป็น SVG

## บทสรุป

และแล้วคุณก็ทำได้! คุณได้แปลงไฟล์เมตาเป็น SVG ในเอกสาร Word สำเร็จแล้วโดยใช้ Aspose.Words สำหรับ .NET เจ๋งใช่ไหม? เพียงแค่เขียนโค้ดไม่กี่บรรทัด คุณก็ปรับปรุงเอกสาร Word ของคุณได้โดยการเพิ่มกราฟิกเวกเตอร์ที่ปรับขนาดได้ ทำให้เอกสารดูมีชีวิตชีวาและดึงดูดสายตามากขึ้น ดังนั้น ลองใช้ในโปรเจ็กต์ของคุณได้เลย ขอให้สนุกกับการเขียนโค้ด!

## คำถามที่พบบ่อย

### Aspose.Words สำหรับ .NET คืออะไร?
Aspose.Words สำหรับ .NET เป็นไลบรารีอันทรงพลังที่ช่วยให้คุณสร้าง แก้ไข และแปลงเอกสาร Word ด้วยโปรแกรมโดยใช้ C#

### ฉันสามารถใช้ Aspose.Words สำหรับ .NET กับ .NET Core ได้หรือไม่
ใช่ Aspose.Words สำหรับ .NET รองรับ .NET Core ทำให้มีความยืดหยุ่นสำหรับแอปพลิเคชัน .NET ที่แตกต่างกัน

### ฉันจะได้รับรุ่นทดลองใช้งาน Aspose.Words สำหรับ .NET ฟรีได้อย่างไร
คุณสามารถดาวน์โหลดรุ่นทดลองใช้งานฟรีได้จาก [หน้าวางจำหน่าย Aspose](https://releases-aspose.com/).

### สามารถแปลงไฟล์รูปภาพรูปแบบอื่นเป็น SVG โดยใช้ Aspose.Words ได้หรือไม่
ใช่ Aspose.Words รองรับการแปลงไฟล์รูปภาพต่างๆ รวมถึงเมตาไฟล์ เป็น SVG

### ฉันสามารถค้นหาเอกสารสำหรับ Aspose.Words สำหรับ .NET ได้ที่ไหน
คุณสามารถค้นหาเอกสารรายละเอียดได้ที่ [หน้าเอกสาร Aspose](https://reference-aspose.com/words/net/).



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}