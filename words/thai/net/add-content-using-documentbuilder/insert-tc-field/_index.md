---
title: แทรกฟิลด์ TC ในเอกสาร Word โดยใช้ Aspose.Words for .NET
weight: 110
limit:
description: เรียนรู้วิธีแทรกฟิลด์ TC พร้อมข้อความที่กำหนดเองลงในเอกสาร Word โดยใช้ Aspose.Words for .NET.
keywords: [Aspose.Words for .NET, insert TC field, TC field Word, DocumentBuilder TC field, Word document index, table of contents field]
url: /net/add-content-using-documentbuilder/insert-tc-field/
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# แทรกฟิลด์ TC ในเอกสาร Word โดยใช้ Aspose.Words
บทเรียนนี้แสดงวิธีใช้ Aspose.Words for .NET เพื่อแทรกฟิลด์ TC (Table of Contents) ลงในเอกสาร Word ที่สร้างใหม่ โดยใช้ DocumentBuilder คุณสามารถเพิ่มฟิลด์ TC พร้อมข้อความรายการที่กำหนดเอง ซึ่งเป็นประโยชน์สำหรับการสร้างดัชนีที่ค้นหาได้สำหรับสารบัญ ตัวอย่างนี้ยังสาธิตการบันทึกเอกสารลงดิสก์.

---

{{< tutorial-widget sourcePath="words/net/add-content-using-documentbuilder/insert-tc-field" >}}


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

**Q: สวิตช์ \"\\f t\" ในโค้ดฟิลด์ TC มีความหมายว่าอะไร?**
A: สวิตช์ \"\\f t\" บอก Word ให้ถือรายการเป็นรายการตาราง ซึ่งทำให้มันปรากฏในสารบัญที่สร้างด้วยสวิตช์ \\f.

**Q: ฉันจะเปลี่ยนข้อความที่แสดงในฟิลด์ TC ได้อย่างไร?**
A: แทนที่ \"Entry Text\" ในการเรียก InsertField ด้วยสตริงใดก็ได้ที่คุณต้องการ เช่น builder.InsertField(\"TC \\\"Chapter 1\\\" \\f t\");

**Q: ฉันสามารถแทรกฟิลด์ TC หลายรายการในเอกสารเดียวกันได้หรือไม่?**
A: ได้; เพียงเรียก builder.InsertField ด้วยข้อความรายการที่ต่างกันในตำแหน่งที่ต้องการก่อนบันทึกเอกสาร.

**Q: โค้ดนี้ทำงานกับรูปแบบอื่นนอกจาก .docx เช่น .pdf หรือไม่?**
A: เอกสารถูกบันทึกเป็น .docx ในตัวอย่างนี้ แต่ Aspose.Words สามารถบันทึกเป็นรูปแบบอื่น (เช่น .pdf) ได้โดยการเปลี่ยนส่วนขยายไฟล์ใน doc.Save และตรวจสอบให้แน่ใจว่ารูปแบบผลลัพธ์ที่เหมาะสมได้รับการสนับสนุน.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}