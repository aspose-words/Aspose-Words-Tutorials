---
title: แทรกการแบ่งหน้าในเอกสาร Word ด้วย Aspose.Words for .NET
weight: 110
limit:
description: เรียนรู้วิธีเพิ่มการแบ่งหน้าในไฟล์ Word ด้วย Aspose.Words for .NET โดยใช้ Document และ DocumentBuilder.
keywords: [Aspose.Words for .NET, insert page break, documentbuilder page break, c# add page break, word document pagination]
url: /net/add-content-using-documentbuilder/insert-page-break/
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# แทรกการแบ่งหน้าในเอกสาร Word ด้วย Aspose.Words
ในบทแนะนำเชิงโต้ตอบนี้ คุณจะได้เรียนรู้วิธีการเพิ่มการแบ่งหน้าในเอกสาร Word อย่างโปรแกรมโดยใช้ Aspose.Words for .NET โดยการสร้างอ็อบเจ็กต์ Document และใช้ DocumentBuilder คุณสามารถควบคุมตำแหน่งที่หน้าต่างใหม่เริ่มต้นได้ ซึ่งเป็นสิ่งสำคัญสำหรับการจัดรูปแบบรายงาน ใบแจ้งหนี้ หรือเอกสารหลายส่วนใด ๆ ให้ทำตามตัวอย่างขั้นตอนต่อขั้นตอนเพื่อดูโค้ดทำงานและดูตัวอย่างไฟล์ที่ได้.

---

{{< tutorial-widget sourcePath="words/net/add-content-using-documentbuilder/insert-page-break" >}}


{{< /blocks/products/pf/tutorial-page-section >}}

{{< blocks/products/pf/tutorial-page-section >}}
## Installation Instructions
1. Download Aspose.Words for .NET:
   Get the latest version from the [Aspose Downloads page](https://releases.aspose.com/words/net/).

2. Install via NuGet:
   - Open your Visual Studio project.
   - Navigate to the NuGet Package Manager (Tools > NuGet Package Manager > Manage NuGet Packages for Solution).
   - Search for "Aspose.Words" and click Install.

3. Add Namespace References:
   Add the following namespace at the top of your code file:
   ```csharp
   using Aspose.Words;
   using Aspose.Words.Saving;
   using Aspose.Words.Drawing;
   ```

4. Apply License (Optional):
   To use the full version, [apply a license](https://purchase.aspose.com/temporary-license/) or use a [free trial](https://releases.aspose.com/).

## Also See
[Aspose.Words for .NET Documentation](https://docs.aspose.com/words/net/)
[Aspose.Words for .NET References](https://reference.aspose.com/words/net/)

## Frequently asked questions

**Q: ฉันสามารถใช้ InsertBreak เพื่อเพิ่มการขึ้นบรรทัดใหม่หรือการแบ่งส่วนแทนการแบ่งหน้าได้หรือไม่?**
A: ใช่, InsertBreak รองรับค่าใด ๆ ของ enum BreakType เช่น BreakType.LineBreak หรือ BreakType.SectionBreakContinuous เพื่อแทรกการแบ่งที่สอดคล้องกัน.

**Q: ฉันต้องเรียก InsertBreak ก่อนหรือหลังจากเขียนข้อความสำหรับหน้าที่ใหม่?**
A: ควรเรียก InsertBreak หลังจากเนื้อหาที่ต้องการบนหน้าปัจจุบัน; คำสั่ง Writeln ถัดไปจะเริ่มบนหน้าที่สร้างโดยการแบ่งนั้น.

**Q: จะเกิดอะไรขึ้นหากเส้นทาง dataDir ไม่ลงท้ายด้วยตัวคั่นไดเรกทอรี?**
A: หาก dataDir ไม่มีสแลชต่อท้าย ชื่อไฟล์จะถูกต่อเข้าด้วยกันโดยตรง (เช่น "C:\\DocsAddContentUsingDocumentBuilder.InsertBreak.docx") ซึ่งอาจทำให้เส้นทางไม่ถูกต้อง; ควรตรวจสอบให้เส้นทางลงท้ายด้วย "\\" หรือใช้ Path.Combine.

**Q: ฉันสามารถใช้อินสแตนซ์ DocumentBuilder เดียวกันเพื่อแทรกการแบ่งหลายครั้งทั่วทั้งเอกสารได้หรือไม่?**
A: ได้, DocumentBuilder เดียวกันสามารถใช้ซ้ำได้; ทุกครั้งที่เรียก InsertBreak จะทำการแทรกการแบ่งที่ตำแหน่งเคอร์เซอร์ปัจจุบันของ builder.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}