---
title: แทรก HTML ที่จัดแนวลงในเอกสาร Word ด้วย Aspose.Words for .NET
weight: 210
limit:
description: เรียนรู้วิธีแทรก HTML พร้อมการจัดแนวเฉพาะลงในเอกสาร Word ด้วย Aspose.Words for .NET
keywords: [insert aligned html, Aspose.Words for .NET, documentbuilder html insertion, html alignment in word, c# insert html word]
url: /net/add-content-using-documentbuilder/insert-aligned-html/
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# แทรก HTML ที่จัดแนวลงในเอกสาร Word ด้วย Aspose.Words
บทเรียนนี้แสดงวิธีใช้ DocumentBuilder ของ Aspose.Words for .NET เพื่อฝังมาร์กอัป HTML ลงในเอกสาร Word และควบคุมการจัดแนวของมัน คุณจะได้เห็นวิธีแทรก HTML, ตั้งค่าการจัดย่อหน้า (ซ้าย, กลาง หรือ ขวา) และจากนั้นบันทึกเอกสารที่ได้ ตัวอย่างนี้เหมาะสำหรับนักพัฒนาที่ต้องการรักษาการจัดรูปแบบแบบเว็บขณะสร้างไฟล์ Word อย่างอัตโนมัติ

---

{{< tutorial-widget sourcePath="words/net/add-content-using-documentbuilder/insert-aligned-html" >}}


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

**Q: สามารถใช้ InsertHtml เพื่อเพิ่ม HTML ลงในเอกสาร Word ที่มีอยู่แล้วแทนที่จะเป็นเอกสารใหม่ได้หรือไม่?**  
A: ได้. สร้าง Document จากไฟล์ที่มีอยู่, วางตำแหน่งเคอร์เซอร์ของ DocumentBuilder ที่ต้องการแทรก HTML (เช่นโดยใช้ builder.MoveToDocumentEnd()), แล้วเรียก builder.InsertHtml พร้อมมาร์กอัปของคุณ

**Q: คุณลักษณะ HTML ใดที่ InsertHtml เคารพสำหรับการจัดแนว?**  
A: InsertHtml ให้การสนับสนุนคุณลักษณะ "align" บนองค์ประกอบระดับบล็อกเช่น &lt;p&gt;, &lt;div&gt; และแท็กหัวเรื่อง, โดยนำการจัดย่อหน้าที่สอดคล้องกันไปใช้ในเอกสาร Word ที่ได้

**Q: จะเกิดอะไรขึ้นหากสตริง HTML มีแท็กหรือ CSS ที่ไม่รองรับ?**  
A: แท็กที่ไม่รองรับจะถูกละเลยและข้อความภายในของมันจะถูกแทรกเป็นข้อความธรรมดา; สไตล์ CSS แบบอินไลน์ที่ Aspose.Words ไม่รู้จักก็จะถูกละเลยเช่นกัน ดังนั้นจึงมีเพียงส่วนย่อยของ HTML ที่รองรับเท่านั้นที่จะแสดงผล

**Q: ฉันต้องปิด DocumentBuilder ก่อนบันทึกเอกสารหรือไม่?**  
A: ไม่จำเป็นต้องปิดโดยเฉพาะ; หลังจากแทรก HTML แล้วคุณสามารถเรียก doc.Save ด้วยชื่อไฟล์และรูปแบบที่ต้องการโดยตรง, และทรัพยากรของ builder จะถูกปล่อยโดยอัตโนมัติ

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}