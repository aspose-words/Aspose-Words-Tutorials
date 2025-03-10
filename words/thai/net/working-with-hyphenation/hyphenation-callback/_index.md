---
title: การโทรกลับการแบ่งคำ
linktitle: การโทรกลับการแบ่งคำ
second_title: API การประมวลผลเอกสาร Aspose.Words
description: เรียนรู้การใช้งานคอลแบ็กการแบ่งคำใน Aspose.Words สำหรับ .NET เพื่อปรับปรุงการจัดรูปแบบเอกสารด้วยคู่มือทีละขั้นตอนที่ครอบคลุมนี้
weight: 10
url: /th/net/working-with-hyphenation/hyphenation-callback/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# การโทรกลับการแบ่งคำ


## การแนะนำ

สวัสดี! คุณเคยพบว่าตัวเองติดอยู่ในความซับซ้อนของการจัดรูปแบบข้อความหรือไม่ โดยเฉพาะอย่างยิ่งเมื่อต้องจัดการกับภาษาที่ต้องใช้การแบ่งคำ คุณไม่ได้เป็นคนเดียว การใช้การแบ่งคำเป็นสิ่งสำคัญสำหรับการจัดรูปแบบข้อความที่เหมาะสม แต่ก็อาจทำให้ปวดหัวได้ แต่คุณรู้ไหมว่า Aspose.Words สำหรับ .NET ช่วยคุณได้ ไลบรารีอันทรงพลังนี้ช่วยให้คุณจัดการการจัดรูปแบบข้อความได้อย่างราบรื่น รวมถึงการจัดการการแบ่งคำผ่านกลไกการเรียกกลับ คุณสนใจหรือไม่ มาเจาะลึกรายละเอียดว่าคุณสามารถใช้งานการเรียกกลับการแบ่งคำโดยใช้ Aspose.Words สำหรับ .NET ได้อย่างไร

## ข้อกำหนดเบื้องต้น

ก่อนที่เราจะเริ่มลงมือเขียนโค้ด เรามาตรวจสอบกันก่อนว่าคุณมีทุกสิ่งที่คุณต้องการแล้ว:

1. Aspose.Words สำหรับ .NET: ตรวจสอบว่าคุณมีไลบรารี คุณสามารถ[ดาวน์โหลดได้ที่นี่](https://releases.aspose.com/words/net/).
2. IDE: สภาพแวดล้อมการพัฒนาเช่น Visual Studio
3. ความรู้พื้นฐานเกี่ยวกับ C#: ความเข้าใจเกี่ยวกับ C# และ .NET framework
4. พจนานุกรมการแบ่งคำ: พจนานุกรมการแบ่งคำสำหรับภาษาที่คุณวางแผนจะใช้
5.  ใบอนุญาต Aspose: ใบอนุญาต Aspose ที่ถูกต้อง คุณสามารถรับได้[ใบอนุญาตชั่วคราว](https://purchase.aspose.com/temporary-license/) หากคุณไม่มี

## นำเข้าเนมสเปซ

ขั้นแรกเลย เรามาทำการนำเข้าเนมสเปซที่จำเป็นกันก่อน วิธีนี้จะช่วยให้โค้ดของเราเข้าถึงคลาสและเมธอดทั้งหมดที่เราต้องการจาก Aspose.Words ได้

```csharp
using Aspose.Words;
using System;
using System.IO;
```

## ขั้นตอนที่ 1: ลงทะเบียนการโทรกลับการแบ่งคำ

ในการเริ่มต้น เราต้องลงทะเบียนคอลแบ็กการแบ่งคำของเรา นี่คือจุดที่เราแจ้งให้ Aspose.Words ใช้ตรรกะการแบ่งคำแบบกำหนดเองของเรา

```csharp
try
{
    // ลงทะเบียนการโทรกลับการแบ่งคำ
    Hyphenation.Callback = new CustomHyphenationCallback();
}
catch (Exception e)
{
    Console.WriteLine($"Error registering hyphenation callback: {e.Message}");
}
```

 ที่นี่ เรากำลังสร้างอินสแตนซ์ของคอลแบ็กที่กำหนดเองและกำหนดให้กับ`Hyphenation.Callback`.

## ขั้นตอนที่ 2: กำหนดเส้นทางเอกสาร

ขั้นต่อไป เราต้องกำหนดไดเรกทอรีที่เก็บเอกสารของเรา ซึ่งเป็นสิ่งสำคัญมาก เนื่องจากเราจะโหลดและบันทึกเอกสารจากเส้นทางนี้

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

 แทนที่`"YOUR DOCUMENT DIRECTORY"` พร้อมเส้นทางจริงไปยังเอกสารของคุณ

## ขั้นตอนที่ 3: โหลดเอกสาร

ตอนนี้มาโหลดเอกสารที่ต้องการการแบ่งคำกัน

```csharp
Document document = new Document(dataDir + "German text.docx");
```

ที่นี่ เรากำลังโหลดเอกสารข้อความภาษาเยอรมัน คุณสามารถแทนที่`"German text.docx"` ด้วยชื่อไฟล์เอกสารของคุณ

## ขั้นตอนที่ 4: บันทึกเอกสาร

หลังจากโหลดเอกสารแล้ว เราจะบันทึกเอกสารลงในไฟล์ใหม่ โดยใช้การเรียกกลับการแบ่งคำในกระบวนการนี้

```csharp
document.Save(dataDir + "TreatmentByCesureWithRecall.pdf");
```

บรรทัดนี้จะบันทึกเอกสารเป็น PDF โดยใช้การแบ่งคำ

## ขั้นตอนที่ 5: จัดการข้อยกเว้นพจนานุกรมการแบ่งคำที่ขาดหายไป

บางครั้งคุณอาจพบปัญหาที่พจนานุกรมการแบ่งคำหายไป มาจัดการกัน

```csharp
catch (Exception e) when (e.Message.StartsWith("Missing hyphenation dictionary"))
{
    Console.WriteLine(e.Message);
}
finally
{
    Hyphenation.Callback = null;
}
```

ในบล็อคนี้ เราจับข้อยกเว้นเฉพาะที่เกี่ยวข้องกับพจนานุกรมที่หายไปและพิมพ์ข้อความ

## ขั้นตอนที่ 6: นำคลาสการโทรกลับการแบ่งคำแบบกำหนดเองมาใช้

 ตอนนี้เรามาลองใช้งานกัน`CustomHyphenationCallback` คลาสซึ่งจัดการการร้องขอสำหรับพจนานุกรมการแบ่งคำ

```csharp
public class CustomHyphenationCallback : IHyphenationCallback
{
    public void RequestDictionary(string language)
    {
        string dictionaryFolder = MyDir;
        string dictionaryFullFileName;
        switch (language)
        {
            case "en-US":
                dictionaryFullFileName = Path.Combine(dictionaryFolder, "hyph_en_US.dic");
                break;
            case "de-CH":
                dictionaryFullFileName = Path.Combine(dictionaryFolder, "hyph_de_CH.dic");
                break;
            default:
                throw new Exception($"Missing hyphenation dictionary for {language}.");
        }
        // ลงทะเบียนพจนานุกรมสำหรับภาษาที่ร้องขอ
        Hyphenation.RegisterDictionary(language, dictionaryFullFileName);
    }
}
```

 ในชั้นเรียนนี้`RequestDictionary` เรียกใช้เมธอดนี้ทุกครั้งที่จำเป็นต้องใช้พจนานุกรมการแบ่งคำ โดยจะตรวจสอบภาษาและลงทะเบียนพจนานุกรมที่เหมาะสม

## บทสรุป

และแล้วคุณก็รู้แล้ว! คุณเพิ่งเรียนรู้วิธีใช้ฟังก์ชันการเรียกกลับแบบแบ่งคำใน Aspose.Words สำหรับ .NET เมื่อทำตามขั้นตอนเหล่านี้แล้ว คุณจะมั่นใจได้ว่าเอกสารของคุณมีการจัดรูปแบบที่สวยงามไม่ว่าจะใช้ภาษาใดก็ตาม ไม่ว่าคุณจะใช้ภาษาอังกฤษ เยอรมัน หรือภาษาอื่นใดก็ตาม วิธีนี้จะช่วยให้คุณจัดการการใช้การแบ่งคำได้อย่างง่ายดาย

## คำถามที่พบบ่อย

### Aspose.Words สำหรับ .NET คืออะไร?
Aspose.Words for .NET เป็นไลบรารีการจัดการเอกสารอันทรงพลังที่ช่วยให้นักพัฒนาสามารถสร้าง แก้ไข และแปลงเอกสารด้วยโปรแกรมได้

### เหตุใดการใช้เครื่องหมายยัติภังค์จึงมีความสำคัญในการจัดรูปแบบเอกสาร?
การใช้เครื่องหมายแบ่งคำช่วยปรับปรุงเค้าโครงข้อความโดยแบ่งคำในตำแหน่งที่เหมาะสม ทำให้เอกสารอ่านง่ายและน่ามองมากขึ้น

### ฉันสามารถใช้ Aspose.Words ได้ฟรีหรือไม่?
 Aspose.Words เสนอให้ทดลองใช้งานฟรี คุณสามารถรับมันได้[ที่นี่](https://releases.aspose.com/).

### ฉันจะได้รับพจนานุกรมการแบ่งคำได้อย่างไร
คุณสามารถดาวน์โหลดพจนานุกรมการแบ่งคำจากแหล่งข้อมูลออนไลน์ต่างๆ หรือสร้างพจนานุกรมของคุณเองหากจำเป็น

### จะเกิดอะไรขึ้นถ้าพจนานุกรมการแบ่งคำขาดหายไป?
 ถ้าพจนานุกรมหายไป`RequestDictionary`วิธีการนี้จะส่งข้อยกเว้นซึ่งคุณสามารถจัดการเพื่อแจ้งให้ผู้ใช้ทราบหรือให้ทางเลือกสำรองได้
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
