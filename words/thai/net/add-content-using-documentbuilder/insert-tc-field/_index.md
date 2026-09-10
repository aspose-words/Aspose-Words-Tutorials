---
title: เพิ่มฟิลด์ TC ลงในเอกสาร Word ด้วย Aspose.Words for .NET
weight: 310
limit:
description: เรียนรู้วิธีแทรกฟิลด์ TC ลงในเอกสาร Word ใหม่ด้วย Aspose.Words for .NET โดยใช้ DocumentBuilder
keywords: [Aspose.Words for .NET, insert TC field, DocumentBuilder TC field, Word document indexing, add TC field programmatically, TC field tutorial]
url: /net/add-content-using-documentbuilder/insert-tc-field/
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# เพิ่มฟิลด์ TC ลงในเอกสาร Word ด้วย Aspose.Words
ในบทแนะนำเชิงโต้ตอบนี้คุณจะได้เรียนรู้วิธีเพิ่มฟิลด์ TC—เครื่องหมายซ่อนที่ Word ใช้สำหรับการทำดัชนีและฟีเจอร์สารบัญ—โดยโปรแกรมลงในเอกสารที่สร้างใหม่โดยใช้ Aspose.Words for .NET โดยใช้ DocumentBuilder คุณสามารถวางฟิลด์ได้ตรงตำแหน่งที่ต้องการและจากนั้นบันทึกไฟล์เพื่อพร้อมสำหรับการประมวลผลต่อไป

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

**Q: ฟิลด์ "TC" ที่แทรกโดย `builder.InsertField(\"TC \\"Entry Text\" \\\\f t\")` ทำหน้าที่อะไรในเอกสาร Word จริงๆ?**
A: มันสร้างรายการในสารบัญด้วยข้อความที่มองเห็นได้ "Entry Text" และทำเครื่องหมายว่าเป็นรายการ TC (Table of Contents) ซึ่ง Word สามารถใช้ต่อมาเมื่อต้องสร้างสารบัญ

**Q: สวิตช์ `\\f t` ในสตริงฟิลด์ TC มีจุดประสงค์เพื่ออะไร?**
A: สวิตช์ `\\f t` บอก Word ให้ถือรายการนี้เป็นข้อความทั่วไป (ไม่ใช่หัวเรื่อง) และรวมไว้ในสารบัญเมื่อสร้าง TOC

**Q: ฉันสามารถแทรกฟิลด์ TC หลายรายการที่มีข้อความต่างกันโดยใช้อินสแตนซ์ `DocumentBuilder` เดียวกันได้หรือไม่?**
A: ได้; เพียงเรียก `builder.InsertField` อีกครั้งด้วยสตริงที่ต่างกัน เช่น `builder.InsertField(\"TC \\"Another Entry\" \\\\f t\")` และแต่ละครั้งจะใส่ฟิลด์ TC ใหม่ที่ตำแหน่งเคอร์เซอร์ปัจจุบัน

**Q: ถ้าฉันต้องการให้ข้อความรายการเป็นแบบไดนามิก (เช่น มาจากตัวแปร) ควรจัดรูปแบบการเรียก `InsertField` อย่างไร?**
A: สร้างสตริงฟิลด์ด้วยการแทรกสตริงหรือ `String.Format` ตัวอย่างเช่น: `string entry = \"Chapter 1\"; builder.InsertField($\"TC \\"{entry}\" \\\\f t\");`.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}