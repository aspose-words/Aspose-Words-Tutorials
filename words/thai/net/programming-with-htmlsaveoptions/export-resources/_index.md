---
"description": "เรียนรู้วิธีการส่งออกทรัพยากร เช่น CSS และแบบอักษร ในขณะที่บันทึกเอกสาร Word เป็น HTML โดยใช้ Aspose.Words สำหรับ .NET ปฏิบัติตามคำแนะนำทีละขั้นตอนของเรา"
"linktitle": "การส่งออกทรัพยากร"
"second_title": "API การประมวลผลเอกสาร Aspose.Words"
"title": "การส่งออกทรัพยากร"
"url": "/th/net/programming-with-htmlsaveoptions/export-resources/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# การส่งออกทรัพยากร

## การแนะนำ

สวัสดีเพื่อนนักเทคโนโลยี! หากคุณเคยพบว่าตัวเองจำเป็นต้องแปลงเอกสาร Word เป็น HTML คุณมาถูกที่แล้ว วันนี้ เราจะพาคุณดำดิ่งสู่โลกอันแสนมหัศจรรย์ของ Aspose.Words สำหรับ .NET ไลบรารีอันทรงพลังนี้ทำให้การทำงานกับเอกสาร Word ด้วยโปรแกรมเป็นเรื่องง่าย ในบทช่วยสอนนี้ เราจะแนะนำขั้นตอนในการส่งออกทรัพยากร เช่น ฟอนต์และ CSS เมื่อบันทึกเอกสาร Word เป็น HTML โดยใช้ Aspose.Words สำหรับ .NET เตรียมตัวให้พร้อมสำหรับประสบการณ์ที่สนุกสนานและเต็มไปด้วยข้อมูล!

## ข้อกำหนดเบื้องต้น

ก่อนที่เราจะเจาะลึกโค้ด เรามาตรวจสอบกันก่อนว่าคุณได้เตรียมทุกอย่างที่จำเป็นเพื่อเริ่มต้นใช้งานแล้ว นี่คือรายการตรวจสอบโดยย่อ:

1. Visual Studio: ตรวจสอบให้แน่ใจว่าคุณได้ติดตั้ง Visual Studio ไว้ในเครื่องของคุณแล้ว คุณสามารถดาวน์โหลดได้จาก [เว็บไซต์ Visual Studio](https://visualstudio-microsoft.com/).
2. Aspose.Words สำหรับ .NET: คุณจะต้องมีไลบรารี Aspose.Words สำหรับ .NET หากคุณยังไม่มี ให้ดาวน์โหลดรุ่นทดลองใช้งานฟรีจาก [การเปิดตัว Aspose](https://releases.aspose.com/words/net/) หรือซื้อได้จาก [ร้านอาโพส](https://purchase-aspose.com/buy).
3. ความรู้พื้นฐานเกี่ยวกับ C#: ความเข้าใจพื้นฐานเกี่ยวกับ C# จะช่วยให้คุณติดตามตัวอย่างโค้ดได้

เข้าใจแล้วใช่ไหม เยี่ยมเลย! มาทำการนำเข้าเนมสเปซที่จำเป็นกันเลย

## นำเข้าเนมสเปซ

หากต้องการใช้ Aspose.Words สำหรับ .NET คุณจะต้องรวมเนมสเปซที่เกี่ยวข้องไว้ในโปรเจ็กต์ของคุณ โดยทำได้ดังนี้:

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

เนมสเปซเหล่านี้มีความสำคัญต่อการเข้าถึงคลาสและวิธีการ Aspose.Words ที่เราจะใช้ในบทช่วยสอนของเรา

มาดูขั้นตอนการส่งออกทรัพยากรเมื่อบันทึกเอกสาร Word เป็น HTML กันทีละขั้นตอนเพื่อให้ทำตามได้ง่าย

## ขั้นตอนที่ 1: ตั้งค่าไดเรกทอรีเอกสารของคุณ

ขั้นแรก คุณต้องระบุเส้นทางไปยังไดเร็กทอรีเอกสารของคุณ นี่คือตำแหน่งที่เอกสาร Word ของคุณอยู่และตำแหน่งที่จะบันทึกไฟล์ HTML

```csharp
// เส้นทางไปยังไดเร็กทอรีเอกสาร
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

แทนที่ `"YOUR DOCUMENT DIRECTORY"` พร้อมเส้นทางจริงไปยังไดเร็กทอรีของคุณ

## ขั้นตอนที่ 2: โหลดเอกสาร Word

ต่อไปเรามาโหลดเอกสาร Word ที่คุณต้องการแปลงเป็น HTML กัน สำหรับบทช่วยสอนนี้ เราจะใช้เอกสารชื่อ `Rendering-docx`.

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

บรรทัดโค้ดนี้โหลดเอกสารจากไดเร็กทอรีที่ระบุ

## ขั้นตอนที่ 3: กำหนดค่าตัวเลือกการบันทึก HTML

หากต้องการส่งออกทรัพยากรเช่น CSS และแบบอักษร คุณจำเป็นต้องกำหนดค่า `HtmlSaveOptions`ขั้นตอนนี้มีความสำคัญอย่างยิ่งในการทำให้แน่ใจว่าผลลัพธ์ HTML ของคุณมีโครงสร้างที่ดีและมีทรัพยากรที่จำเป็น

```csharp
HtmlSaveOptions saveOptions = new HtmlSaveOptions
{
    CssStyleSheetType = CssStyleSheetType.External,
    ExportFontResources = true,
    ResourceFolder = dataDir + "Resources",
    ResourceFolderAlias = "http://example.com/resources"
};
```

มาดูกันว่าแต่ละตัวเลือกทำหน้าที่อะไรบ้าง:
- `CssStyleSheetType = CssStyleSheetType.External`ตัวเลือกนี้ระบุว่าควรบันทึกสไตล์ CSS ไว้ในสไตล์ชีทภายนอก
- `ExportFontResources = true`:นี่จะช่วยให้สามารถส่งออกทรัพยากรแบบอักษรได้
- `ResourceFolder = dataDir + "Resources"`: ระบุโฟลเดอร์ในเครื่องที่จะบันทึกทรัพยากร (เช่น แบบอักษรและไฟล์ CSS)
- `ResourceFolderAlias = "http://example.com/resources"`: ตั้งค่านามแฝงสำหรับโฟลเดอร์ทรัพยากรซึ่งจะใช้ในไฟล์ HTML

## ขั้นตอนที่ 4: บันทึกเอกสารเป็น HTML

เมื่อกำหนดค่าตัวเลือกการบันทึกแล้ว ขั้นตอนสุดท้ายคือการบันทึกเอกสารเป็นไฟล์ HTML โดยทำดังนี้:

```csharp
doc.Save(dataDir + "WorkingWithHtmlSaveOptions.ExportResources.html", saveOptions);
```

บรรทัดโค้ดนี้จะบันทึกเอกสารในรูปแบบ HTML ร่วมกับทรัพยากรที่ส่งออก

## บทสรุป

และแล้วคุณก็ทำได้! คุณได้ส่งออกทรัพยากรสำเร็จแล้วในขณะที่บันทึกเอกสาร Word เป็น HTML โดยใช้ Aspose.Words สำหรับ .NET ด้วยไลบรารีอันทรงพลังนี้ การจัดการเอกสาร Word ด้วยโปรแกรมจะกลายเป็นเรื่องง่ายดาย ไม่ว่าคุณจะทำงานบนแอปพลิเคชันเว็บหรือเพียงแค่ต้องการแปลงเอกสารสำหรับการใช้งานออฟไลน์ Aspose.Words จะช่วยคุณได้

## คำถามที่พบบ่อย

### ฉันสามารถส่งออกรูปภาพพร้อมกับแบบอักษรและ CSS ได้หรือไม่
ใช่ คุณทำได้! Aspose.Words สำหรับ .NET รองรับการส่งออกรูปภาพเช่นกัน เพียงตรวจสอบให้แน่ใจว่าได้กำหนดค่า `HtmlSaveOptions` ตามนั้นครับ

### มีวิธีฝัง CSS แทนการใช้สไตล์ชีตภายนอกหรือไม่
แน่นอน คุณสามารถตั้งค่าได้ `CssStyleSheetType` ถึง `CssStyleSheetType.Embedded` หากคุณชอบสไตล์แบบฝัง

### ฉันจะกำหนดชื่อไฟล์ HTML เอาท์พุตได้อย่างไร
คุณสามารถระบุชื่อไฟล์ใด ๆ ที่คุณต้องการใน `doc.Save` วิธีการ เช่น `doc-Save(dataDir + "CustomFileName.html", saveOptions);`.

### Aspose.Words รองรับรูปแบบอื่นนอกเหนือจาก HTML หรือไม่?
ใช่ รองรับรูปแบบต่างๆ เช่น PDF, DOCX, TXT และอื่นๆ ลองดู [เอกสารประกอบ](https://reference.aspose.com/words/net/) สำหรับรายการทั้งหมด

### ฉันจะได้รับการสนับสนุนและทรัพยากรเพิ่มเติมได้ที่ไหน
หากต้องการความช่วยเหลือเพิ่มเติม โปรดไปที่ [ฟอรั่มสนับสนุน Aspose.Words](https://forum.aspose.com/c/words/8)คุณยังสามารถค้นหาเอกสารรายละเอียดและตัวอย่างได้ที่ [เว็บไซต์อาโพส](https://reference-aspose.com/words/net/).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}