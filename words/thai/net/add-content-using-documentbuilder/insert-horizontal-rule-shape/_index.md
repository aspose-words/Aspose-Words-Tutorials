---
title: แทรกรูปร่างเส้นกั้นแนวนอนในเอกสาร Word ด้วย Aspose.Words for .NET
weight: 110
limit:
description: เรียนรู้วิธีเพิ่มรูปร่างเส้นกั้นแนวนอนในเอกสาร Word ด้วย Aspose.Words for .NET โดยใช้ DocumentBuilder.
keywords: [Aspose.Words for .NET, insert horizontal rule shape, documentbuilder horizontal line, create Word document .NET, horizontal rule shape tutorial]
url: /net/add-content-using-documentbuilder/insert-horizontal-rule-shape/
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# แทรกรูปร่างเส้นกั้นแนวนอนในเอกสาร Word ด้วย Aspose.Words
ในบทแนะนำนี้คุณจะได้เรียนรู้วิธีแทรกรูปร่างเส้นกั้นแนวนอนลงในเอกสาร Word อย่างโปรแกรมด้วย Aspose.Words for .NET โดยใช้คลาส Document และ DocumentBuilder เราจะสร้างเอกสารใหม่, เพิ่มย่อหน้าข้อความ, แล้ววางรูปร่างเส้นแนวนอนในตำแหน่งที่ต้องการ เส้นกั้นแนวนอนทำหน้าที่เป็นตัวแบ่งเชิงภาพที่อาจเป็นประโยชน์สำหรับการแบ่งส่วนหรือการเน้นเชิงภาพ.

---

{{< tutorial-widget sourcePath="words/net/add-content-using-documentbuilder/insert-horizontal-rule-shape" >}}


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

**Q: บรรทัด `builder.InsertHorizontalRule()` จะวางเส้นไว้ที่ตำแหน่งใดในเอกสารอย่างแม่นยำ?**
A: `InsertHorizontalRule` แทรกรูปร่างเส้นกั้นแนวนอนที่ตำแหน่งเคอร์เซอร์ปัจจุบันของ `DocumentBuilder`; หากต้องการให้เป็นบรรทัดแยก ให้เรียก `builder.Writeln()` ก่อนทำการแทรก.

**Q: ฉันสามารถเปลี่ยนความหนา, สี หรือความกว้างของเส้นกั้นแนวนอนที่แทรกได้หรือไม่?**
A: `InsertHorizontalRule` เพิ่มเส้นกั้นที่มีสไตล์เริ่มต้นและไม่ได้เปิดเผยตัวเลือกการจัดรูปแบบ; หากต้องการปรับแต่งคุณต้องแทรก `Shape` ด้วยตนเอง (เช่น `builder.InsertShape(ShapeType.HorizontalLine)`) แล้วตั้งค่าคุณสมบัติ `LineFormat` ของมัน.

**Q: เป็นไปได้หรือไม่ที่จะเพิ่มเส้นกั้นแนวนอนมากกว่าหนึ่งเส้นในเอกสารเดียวกัน?**
A: ได้—เพียงเรียก `builder.InsertHorizontalRule()` ทุกครั้งที่ต้องการเส้นกั้นใหม่; แต่ละครั้งจะสร้างรูปร่างแยกที่ตำแหน่งปัจจุบันของ builder.

**Q: เส้นกั้นแนวนอนจะปรากฏเมื่อเปิดไฟล์ .docx ที่บันทึกไว้ใน Microsoft Word หรือไม่?**
A: แน่นอน; เส้นกั้นถูกบันทึกเป็นรูปร่างภายในไฟล์ .docx ดังนั้น Word จะแสดงมันตรงตามที่ปรากฏในเอกสารที่สร้างขึ้น.

**Q: จะเกิดอะไรขึ้นหากโฟลเดอร์ `dataDir` ไม่มีอยู่ก่อนเรียก `doc.Save(...)`?**
A: `doc.Save` จะโยน `DirectoryNotFoundException`; ตรวจสอบให้แน่ใจว่าไดเรกทอรีเป้าหมายมีอยู่หรือสร้างมันโดยโปรแกรมก่อนทำการบันทึก.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}