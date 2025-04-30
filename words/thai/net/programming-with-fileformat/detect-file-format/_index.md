---
"description": "เรียนรู้วิธีตรวจจับรูปแบบไฟล์เอกสารโดยใช้ Aspose.Words สำหรับ .NET ด้วยคู่มือทีละขั้นตอนที่ครอบคลุมนี้"
"linktitle": "ตรวจจับรูปแบบไฟล์เอกสาร"
"second_title": "API การประมวลผลเอกสาร Aspose.Words"
"title": "ตรวจจับรูปแบบไฟล์เอกสาร"
"url": "/th/net/programming-with-fileformat/detect-file-format/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# ตรวจจับรูปแบบไฟล์เอกสาร

## การแนะนำ

ในโลกดิจิทัลทุกวันนี้ การจัดการรูปแบบเอกสารต่างๆ อย่างมีประสิทธิภาพถือเป็นสิ่งสำคัญ ไม่ว่าคุณจะใช้ Word, PDF, HTML หรือรูปแบบอื่นๆ การตรวจจับและประมวลผลไฟล์เหล่านี้อย่างถูกต้องจะช่วยประหยัดเวลาและความพยายามของคุณได้มาก ในบทช่วยสอนนี้ เราจะมาสำรวจวิธีตรวจจับรูปแบบไฟล์เอกสารโดยใช้ Aspose.Words สำหรับ .NET คู่มือนี้จะแนะนำคุณเกี่ยวกับทุกสิ่งที่คุณจำเป็นต้องรู้ ตั้งแต่ข้อกำหนดเบื้องต้นไปจนถึงคำแนะนำทีละขั้นตอนโดยละเอียด

## ข้อกำหนดเบื้องต้น

ก่อนที่เราจะเจาะลึกโค้ด เรามาตรวจสอบกันก่อนว่าคุณมีทุกสิ่งที่คุณต้องการแล้ว:

- Aspose.Words สำหรับ .NET: คุณสามารถดาวน์โหลดได้จาก [ที่นี่](https://releases.aspose.com/words/net/). ตรวจสอบให้แน่ใจว่าคุณมีใบอนุญาตที่ถูกต้อง หากไม่มี คุณสามารถขอใบอนุญาตได้ [ใบอนุญาตชั่วคราว](https://purchase-aspose.com/temporary-license/).
- Visual Studio: เวอร์ชันล่าสุดใดๆ ก็ทำงานได้ดี
- .NET Framework: ตรวจสอบให้แน่ใจว่าคุณได้ติดตั้งเวอร์ชันที่ถูกต้อง

## นำเข้าเนมสเปซ

ในการเริ่มต้น คุณจะต้องนำเข้าเนมสเปซที่จำเป็นในโครงการของคุณ:

```csharp
using Aspose.Words;
using Aspose.Words.FileFormats;
using Aspose.Words.FileFormats.Util;
using System;
using System.Collections.Generic;
using System.IO;
using System.Linq;
```

ให้เราแบ่งตัวอย่างออกเป็นหลายขั้นตอนเพื่อให้สามารถปฏิบัติตามได้ง่ายขึ้น

## ขั้นตอนที่ 1: ตั้งค่าไดเรกทอรี

ขั้นแรก เราต้องตั้งค่าไดเร็กทอรีที่ไฟล์จะถูกเรียงลำดับตามรูปแบบ

```csharp
// เส้นทางไปยังไดเร็กทอรีเอกสาร
string dataDir = "YOUR DOCUMENT DIRECTORY";
string supportedDir = dataDir + "Supported";
string unknownDir = dataDir + "Unknown";
string encryptedDir = dataDir + "Encrypted";
string pre97Dir = dataDir + "Pre97";

// สร้างไดเร็กทอรีหากยังไม่มีอยู่
if (!Directory.Exists(supportedDir))
    Directory.CreateDirectory(supportedDir);
if (!Directory.Exists(unknownDir))
    Directory.CreateDirectory(unknownDir);
if (!Directory.Exists(encryptedDir))
    Directory.CreateDirectory(encryptedDir);
if (!Directory.Exists(pre97Dir))
    Directory.CreateDirectory(pre97Dir);
```

## ขั้นตอนที่ 2: รับรายการไฟล์

ต่อไปเราจะได้รับรายการไฟล์จากไดเร็กทอรี โดยไม่รวมเอกสารที่เสียหาย

```csharp
IEnumerable<string> fileList = Directory.GetFiles(dataDir).Where(name => !name.EndsWith("Corrupted document.docx"));
```

## ขั้นตอนที่ 3: ตรวจจับรูปแบบไฟล์

ขณะนี้ เราจะวนซ้ำผ่านไฟล์แต่ละไฟล์และตรวจจับรูปแบบของไฟล์โดยใช้ Aspose.Words

```csharp
foreach (string fileName in fileList)
{
    string nameOnly = Path.GetFileName(fileName);

    Console.Write(nameOnly);

    FileFormatInfo info = FileFormatUtil.DetectFileFormat(fileName);

    // แสดงประเภทเอกสาร
    switch (info.LoadFormat)
    {
        case LoadFormat.Doc:
            Console.WriteLine("\tMicrosoft Word 97-2003 document.");
            break;
        case LoadFormat.Dot:
            Console.WriteLine("\tMicrosoft Word 97-2003 template.");
            break;
        case LoadFormat.Docx:
            Console.WriteLine("\tOffice Open XML WordprocessingML Macro-Free Document.");
            break;
        case LoadFormat.Docm:
            Console.WriteLine("\tOffice Open XML WordprocessingML Macro-Enabled Document.");
            break;
        case LoadFormat.Dotx:
            Console.WriteLine("\tOffice Open XML WordprocessingML Macro-Free Template.");
            break;
        case LoadFormat.Dotm:
            Console.WriteLine("\tOffice Open XML WordprocessingML Macro-Enabled Template.");
            break;
        case LoadFormat.FlatOpc:
            Console.WriteLine("\tFlat OPC document.");
            break;
        case LoadFormat.Rtf:
            Console.WriteLine("\tRTF format.");
            break;
        case LoadFormat.WordML:
            Console.WriteLine("\tMicrosoft Word 2003 WordprocessingML format.");
            break;
        case LoadFormat.Html:
            Console.WriteLine("\tHTML format.");
            break;
        case LoadFormat.Mhtml:
            Console.WriteLine("\tMHTML (Web archive) format.");
            break;
        case LoadFormat.Odt:
            Console.WriteLine("\tOpenDocument Text.");
            break;
        case LoadFormat.Ott:
            Console.WriteLine("\tOpenDocument Text Template.");
            break;
        case LoadFormat.DocPreWord60:
            Console.WriteLine("\tMS Word 6 or Word 95 format.");
            break;
        case LoadFormat.Unknown:
            Console.WriteLine("\tUnknown format.");
            break;
    }

    if (info.IsEncrypted)
    {
        Console.WriteLine("\tAn encrypted document.");
        File.Copy(fileName, Path.Combine(encryptedDir, nameOnly), true);
    }
    else
    {
        switch (info.LoadFormat)
        {
            case LoadFormat.DocPreWord60:
                File.Copy(fileName, Path.Combine(pre97Dir, nameOnly), true);
                break;
            case LoadFormat.Unknown:
                File.Copy(fileName, Path.Combine(unknownDir, nameOnly), true);
                break;
            default:
                File.Copy(fileName, Path.Combine(supportedDir, nameOnly), true);
                break;
        }
    }
}
```

## บทสรุป

การตรวจจับรูปแบบไฟล์เอกสารโดยใช้ Aspose.Words สำหรับ .NET เป็นกระบวนการที่ตรงไปตรงมามาก คุณสามารถจัดระเบียบและจัดการเอกสารของคุณได้อย่างมีประสิทธิภาพโดยการตั้งค่าไดเร็กทอรีของคุณ รับรายการไฟล์ของคุณ และใช้ Aspose.Words เพื่อตรวจจับรูปแบบไฟล์ วิธีนี้ไม่เพียงแต่ประหยัดเวลา แต่ยังช่วยให้คุณจัดการรูปแบบเอกสารต่างๆ ได้อย่างถูกต้องอีกด้วย

## คำถามที่พบบ่อย

### Aspose.Words สำหรับ .NET คืออะไร?
Aspose.Words สำหรับ .NET เป็นไลบรารีที่มีประสิทธิภาพสำหรับการทำงานกับเอกสาร Word ด้วยโปรแกรม ช่วยให้นักพัฒนาสามารถสร้าง แก้ไข และแปลงเอกสารในรูปแบบต่างๆ ได้

### Aspose.Words สามารถตรวจจับเอกสารที่เข้ารหัสได้หรือไม่
ใช่ Aspose.Words สามารถตรวจจับได้ว่าเอกสารได้รับการเข้ารหัสหรือไม่ และคุณสามารถจัดการเอกสารดังกล่าวได้ตามความเหมาะสม

### Aspose.Words สามารถตรวจจับรูปแบบใดบ้าง?
Aspose.Words สามารถตรวจจับรูปแบบต่างๆ ได้มากมาย รวมถึง DOC, DOCX, RTF, HTML, MHTML, ODT และอื่นๆ อีกมากมาย

### ฉันจะได้รับใบอนุญาตชั่วคราวสำหรับ Aspose.Words ได้อย่างไร
คุณสามารถขอใบอนุญาตชั่วคราวได้จาก [การซื้อ Aspose](https://purchase.aspose.com/temporary-license/) หน้าหนังสือ.

### ฉันสามารถค้นหาเอกสารสำหรับ Aspose.Words ได้ที่ไหน
เอกสารประกอบสำหรับ Aspose.Words สามารถพบได้ [ที่นี่](https://reference-aspose.com/words/net/).



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}