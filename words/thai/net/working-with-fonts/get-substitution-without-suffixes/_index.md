---
"description": "เรียนรู้วิธีจัดการการแทนที่แบบอักษรโดยไม่ต้องใช้คำต่อท้ายใน Aspose.Words สำหรับ .NET ปฏิบัติตามคำแนะนำทีละขั้นตอนของเราเพื่อให้แน่ใจว่าเอกสารของคุณจะดูสมบูรณ์แบบทุกครั้ง"
"linktitle": "รับการทดแทนโดยไม่ต้องมีคำต่อท้าย"
"second_title": "API การประมวลผลเอกสาร Aspose.Words"
"title": "รับการทดแทนโดยไม่ต้องมีคำต่อท้าย"
"url": "/th/net/working-with-fonts/get-substitution-without-suffixes/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# รับการทดแทนโดยไม่ต้องมีคำต่อท้าย

## การแนะนำ

ยินดีต้อนรับสู่คู่มือฉบับสมบูรณ์เกี่ยวกับการจัดการการแทนที่แบบอักษรโดยใช้ Aspose.Words สำหรับ .NET หากคุณเคยประสบปัญหาแบบอักษรไม่ปรากฏอย่างถูกต้องในเอกสารของคุณ คุณมาถูกที่แล้ว บทช่วยสอนนี้จะแนะนำคุณทีละขั้นตอนในการจัดการการแทนที่แบบอักษรโดยไม่ต้องใช้คำต่อท้ายอย่างมีประสิทธิภาพ

## ข้อกำหนดเบื้องต้น

ก่อนจะเริ่มบทช่วยสอนนี้ ให้แน่ใจว่าคุณมีสิ่งต่อไปนี้:

- ความรู้พื้นฐานเกี่ยวกับ C#: ความเข้าใจในการเขียนโปรแกรม C# จะทำให้ปฏิบัติตามและนำขั้นตอนต่างๆ ไปใช้ได้ง่ายยิ่งขึ้น
- Aspose.Words สำหรับไลบรารี .NET: ดาวน์โหลดและติดตั้งไลบรารีจาก [ลิงค์ดาวน์โหลด](https://releases-aspose.com/words/net/).
- สภาพแวดล้อมการพัฒนา: ตั้งค่าสภาพแวดล้อมการพัฒนาเช่น Visual Studio เพื่อเขียนและรันโค้ดของคุณ
- เอกสารตัวอย่าง: เอกสารตัวอย่าง (เช่น `Rendering.docx`) ที่จะนำไปใช้ในระหว่างการสอนนี้

## นำเข้าเนมสเปซ

ก่อนอื่น เราต้องนำเข้าเนมสเปซที่จำเป็นเพื่อเข้าถึงคลาสและวิธีการที่ Aspose.Words จัดเตรียมไว้

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;
using System.Collections.Generic;
```

## ขั้นตอนที่ 1: กำหนดไดเรกทอรีเอกสาร

ในการเริ่มต้น ให้ระบุไดเรกทอรีที่เอกสารของคุณตั้งอยู่ ซึ่งจะช่วยให้ค้นหาเอกสารที่คุณต้องการดำเนินการได้

```csharp
// เส้นทางไปยังไดเรกทอรีเอกสารของคุณ
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## ขั้นตอนที่ 2: ตั้งค่าตัวจัดการคำเตือนการทดแทน

ขั้นต่อไป เราต้องตั้งค่าตัวจัดการคำเตือนที่จะแจ้งให้เราทราบทุกครั้งที่เกิดการแทนที่แบบอักษรระหว่างการประมวลผลเอกสาร ซึ่งถือเป็นสิ่งสำคัญสำหรับการตรวจจับและจัดการปัญหาด้านแบบอักษร

```csharp
DocumentSubstitutionWarnings substitutionWarningHandler = new DocumentSubstitutionWarnings();
Document doc = new Document(dataDir + "Rendering.docx");
doc.WarningCallback = substitutionWarningHandler;
```

## ขั้นตอนที่ 3: เพิ่มแหล่งที่มาของแบบอักษรที่กำหนดเอง

ในขั้นตอนนี้ เราจะเพิ่มแหล่งที่มาของแบบอักษรที่กำหนดเองเพื่อให้แน่ใจว่า Aspose.Words สามารถค้นหาและใช้แบบอักษรที่ถูกต้องได้ ซึ่งจะเป็นประโยชน์อย่างยิ่งหากคุณมีแบบอักษรเฉพาะที่เก็บไว้ในไดเร็กทอรีที่กำหนดเอง

```csharp
List<FontSourceBase> fontSources = new List<FontSourceBase>(FontSettings.DefaultInstance.GetFontsSources());

FolderFontSource folderFontSource = new FolderFontSource("C:\\MyFonts\\", true);
fontSources.Add(folderFontSource);

FontSourceBase[] updatedFontSources = fontSources.ToArray();
FontSettings.DefaultInstance.SetFontsSources(updatedFontSources);
```

ในโค้ดนี้:
- เราดึงแหล่งที่มาของแบบอักษรปัจจุบันและเพิ่มแบบอักษรใหม่ `FolderFontSource` ชี้ไปที่ไดเร็กทอรีแบบอักษรที่กำหนดเองของเรา (`C:\\MyFonts\\`-
- จากนั้นเราอัปเดตแหล่งที่มาของแบบอักษรด้วยรายการใหม่นี้

## ขั้นตอนที่ 4: บันทึกเอกสาร

สุดท้าย ให้บันทึกเอกสารหลังจากใช้การตั้งค่าการแทนที่แบบอักษรแล้ว สำหรับบทช่วยสอนนี้ เราจะบันทึกเป็น PDF

```csharp
doc.Save(dataDir + "WorkingWithFonts.GetSubstitutionWithoutSuffixes.pdf");
```

## ขั้นตอนที่ 5: สร้างคลาสตัวจัดการคำเตือน

เพื่อจัดการคำเตือนอย่างมีประสิทธิภาพ ให้สร้างคลาสแบบกำหนดเองที่ใช้งาน `IWarningCallback` อินเทอร์เฟซ คลาสนี้จะจับภาพและบันทึกคำเตือนการแทนที่แบบอักษรทั้งหมด

```csharp
public class DocumentSubstitutionWarnings : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        if (info.WarningType == WarningType.FontSubstitution)
            FontWarnings.Warning(info);
    }

    public WarningInfoCollection FontWarnings = new WarningInfoCollection();
}
```

ในชั้นเรียนนี้:
- การ `Warning` วิธีการนี้จะจับคำเตือนที่เกี่ยวข้องกับการแทนที่แบบอักษร
- การ `FontWarnings` คอลเลกชันจะจัดเก็บคำเตือนเหล่านี้ไว้สำหรับการตรวจสอบหรือการบันทึกเพิ่มเติม

## บทสรุป

ตอนนี้คุณเข้าใจกระบวนการจัดการการแทนที่แบบอักษรโดยไม่ต้องใช้คำต่อท้ายโดยใช้ Aspose.Words สำหรับ .NET เป็นอย่างดีแล้ว ความรู้ดังกล่าวจะช่วยให้มั่นใจได้ว่าเอกสารของคุณจะคงรูปลักษณ์ตามที่ต้องการไว้ โดยไม่คำนึงถึงแบบอักษรที่มีอยู่ในระบบ ทดลองใช้การตั้งค่าและแหล่งที่มาต่างๆ อย่างต่อเนื่องเพื่อใช้ประโยชน์จาก Aspose.Words อย่างเต็มที่

## คำถามที่พบบ่อย

### ฉันจะใช้แบบอักษรจากไดเร็กทอรีที่กำหนดเองหลาย ๆ แห่งได้อย่างไร

คุณสามารถเพิ่มหลายรายการได้ `FolderFontSource` กรณีตัวอย่างถึง `fontSources` รายการและอัปเดตแหล่งที่มาของแบบอักษรให้เหมาะสม

### ฉันสามารถดาวน์โหลด Aspose.Words สำหรับ .NET แบบทดลองใช้งานฟรีได้ที่ไหน

คุณสามารถดาวน์โหลดรุ่นทดลองใช้งานฟรีได้จาก [หน้าทดลองใช้งานฟรี Aspose](https://releases-aspose.com/).

### ฉันสามารถจัดการกับคำเตือนหลายประเภทโดยใช้ `IWarningCallback`-

ใช่ครับ `IWarningCallback` อินเทอร์เฟซช่วยให้คุณจัดการคำเตือนประเภทต่างๆ ไม่ใช่แค่การแทนที่แบบอักษรเท่านั้น

### ฉันจะได้รับการสนับสนุนสำหรับ Aspose.Words ได้จากที่ไหน

หากต้องการความช่วยเหลือ โปรดไปที่ [ฟอรั่มสนับสนุน Aspose.Words](https://forum-aspose.com/c/words/8).

### สามารถซื้อใบอนุญาตชั่วคราวได้หรือไม่?

ใช่ คุณสามารถขอใบอนุญาตชั่วคราวได้จาก [หน้าใบอนุญาตชั่วคราว](https://purchase-aspose.com/temporary-license/).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}