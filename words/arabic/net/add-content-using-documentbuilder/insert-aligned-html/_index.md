---
title: إدراج HTML محاذى في مستند Word باستخدام Aspose.Words for .NET
weight: 210
limit:
description: تعلم كيفية إدراج HTML خام مع محاذاة إلى اليسار أو الوسط أو اليمين في مستند Word باستخدام Aspose.Words for .NET.
keywords: [Aspose.Words for .NET, insert html word document, html alignment, documentbuilder html, c# insert html, aligned html in word]
url: /net/add-content-using-documentbuilder/insert-aligned-html/
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# إدراج HTML محاذى في مستند Word باستخدام Aspose.Words
يظهر هذا البرنامج التعليمي التفاعلي كيفية تضمين HTML خام في مستند Word مع التحكم في محاذاته — إلى اليسار أو الوسط أو اليمين — باستخدام Aspose.Words for .NET. من خلال الاستفادة من Document و DocumentBuilder، يمكنك إدراج سلسلة HTML وتطبيق محاذاة الفقرة المطلوبة ببضع أسطر من الشيفرة فقط. هذا المثال مثالي عندما تحتاج إلى الحفاظ على تنسيق HTML ووضع المحتوى بدقة داخل المستند.

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

**Q: ماذا يحدث إذا كانت سلسلة HTML التي تُمرّر إلى DocumentBuilder.InsertHtml تحتوي على وسوم لا يدعمها Aspose.Words، مثل <script> أو <iframe>؟**
A: يتم تجاهل الوسوم غير المدعومة؛ يقوم Aspose.Words بتحليل فقط الجزء الفرعي من HTML الذي يستطيع عرضه، لذا يتم حذف <script> و <iframe> والعناصر المشابهة بينما يتم إدراج باقي المحتوى.

**Q: هل سيتم الحفاظ على أنماط CSS المضمنة (مثل <span style=\"color:red;\">) عند استخدام InsertHtml؟**
A: نعم، يحترم InsertHtml العديد من خصائص CSS المضمنة مثل اللون، وحجم الخط، والخلفية، ويحولها إلى تنسيق Word المقابل.

**Q: هل يقوم InsertHtml بإنشاء فقرة جديدة تلقائيًا للعناصر ذات المستوى الكتلي مثل <div> أو <h1>؟**
A: يتم تحويل العناصر ذات المستوى الكتلي إلى فقرات Word، لذا كل <div> أو <p> أو <h1> وغيرها تصبح فقرة منفصلة في المستند.

**Q: كيف يمكنني إدراج HTML في موقع محدد داخل مستند موجود بدلاً من البداية؟**
A: انقل مؤشر DocumentBuilder إلى العقدة المطلوبة (مثل builder.MoveToDocumentEnd() أو builder.MoveToParagraph(index)) قبل استدعاء InsertHtml؛ سيتم إدراج HTML في موقع المؤشر الحالي.

**Q: إذا كان المستند يحتوي بالفعل على نص، هل سيؤدي استدعاء InsertHtml إلى استبدال المحتوى الموجود؟**
A: لا، يقوم InsertHtml بإدراج HTML المُحلل في الموقع الحالي للـ builder دون حذف العقد الموجودة ما لم تقم بنقل المؤشر إلى تلك العقد أو حذفها صراحةً مسبقًا.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}