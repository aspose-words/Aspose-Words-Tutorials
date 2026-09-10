---
title: แทรก HTML ที่จัดแนวลงในเอกสาร Word ด้วย Aspose.Words for .NET
weight: 210
limit:
description: เรียนรู้วิธีแทรก HTML ดิบพร้อมการจัดแนวซ้าย, กลาง หรือขวา ลงในเอกสาร Word ด้วย Aspose.Words for .NET
keywords: [Aspose.Words for .NET, insert html word document, html alignment, documentbuilder html, c# insert html, aligned html in word]
url: /net/add-content-using-documentbuilder/insert-aligned-html/
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# แทรก HTML ที่จัดแนวลงในเอกสาร Word ด้วย Aspose.Words
บทแนะนำเชิงโต้ตอบนี้แสดงวิธีฝัง HTML ดิบลงในเอกสาร Word พร้อมควบคุมการจัดแนว—ซ้าย, กลาง หรือขวา—โดยใช้ Aspose.Words for .NET โดยใช้ Document และ DocumentBuilder คุณสามารถแทรกสตริง HTML และกำหนดการจัดแนวย่อหน้าที่ต้องการได้ด้วยเพียงไม่กี่บรรทัดของโค้ด ตัวอย่างนี้เหมาะอย่างยิ่งเมื่อคุณต้องการรักษาการจัดรูปแบบของ HTML และวางเนื้อหาอย่างแม่นยำในเอกสารของคุณ

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

**Q: จะเกิดอะไรขึ้นหากสตริง HTML ที่ส่งให้ DocumentBuilder.InsertHtml มีแท็กที่ Aspose.Words ไม่รองรับ เช่น <script> หรือ <iframe>?**
A: แท็กที่ไม่รองรับจะถูกละเลย; Aspose.Words จะพาร์สเฉพาะส่วนย่อยของ HTML ที่สามารถแสดงผลได้ ดังนั้น <script>, <iframe> และองค์ประกอบที่คล้ายกันจะถูกลบออกในขณะที่ส่วนที่เหลือของเนื้อหาจะถูกแทรก

**Q: สไตล์ CSS แบบอินไลน์ (เช่น <span style=\"color:red;\">) จะถูกเก็บรักษาไว้เมื่อใช้ InsertHtml หรือไม่?**
A: ใช่, InsertHtml รองรับคุณสมบัติ CSS แบบอินไลน์หลายอย่าง เช่น color, font‑size, และ background โดยจะแปลงเป็นการจัดรูปแบบของ Word ที่สอดคล้องกัน

**Q: InsertHtml จะสร้างย่อหน้าใหม่โดยอัตโนมัติสำหรับองค์ประกอบระดับบล็อก เช่น <div> หรือ <h1> หรือไม่?**
A: องค์ประกอบระดับบล็อกจะถูกแมปเป็นย่อหน้าใน Word ดังนั้นแต่ละ <div>, <p>, <h1> เป็นต้น จะกลายเป็นย่อหน้าแยกกันในเอกสาร

**Q: ฉันจะใส่ HTML ที่ตำแหน่งเฉพาะในเอกสารที่มีอยู่แทนที่จะใส่ที่จุดเริ่มต้นได้อย่างไร?**
A: ย้ายเคอร์เซอร์ของ DocumentBuilder ไปยังโหนดที่ต้องการ (เช่น builder.MoveToDocumentEnd() หรือ builder.MoveToParagraph(index)) ก่อนเรียก InsertHtml; HTML จะถูกแทรกที่ตำแหน่งเคอร์เซอร์ปัจจุบัน

**Q: หากเอกสารมีข้อความอยู่แล้ว การเรียก InsertHtml จะเขียนทับเนื้อหาที่มีอยู่หรือไม่?**
A: ไม่, InsertHtml จะใส่ HTML ที่พาร์สแล้วที่ตำแหน่งปัจจุบันของ builder โดยไม่ลบโหนดที่มีอยู่ เว้นแต่คุณจะย้ายเคอร์เซอร์เข้าไปหรือทำการลบโหนดเหล่านั้นก่อนหน้าโดยเจตนา

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}