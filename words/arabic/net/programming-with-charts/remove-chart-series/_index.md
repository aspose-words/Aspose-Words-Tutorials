---
title: إزالة سلسلة مخطط من مستند Word باستخدام Aspose.Words for .NET
weight: 510
limit:
description: تعلم كيفية حذف سلسلة بيانات محددة من مخطط عمودي في مستند Word باستخدام Aspose.Words for .NET.
keywords: [Aspose.Words for .NET, remove chart series, ChartSeriesCollection.RemoveAt, column chart manipulation, Word document chart editing, C# chart series removal]
url: /net/programming-with-charts/remove-chart-series/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: تعلم كيفية حذف سلسلة بيانات محددة من مخطط عمودي في مستند Word باستخدام
    Aspose.Words for .NET.
  headline: إزالة سلسلة مخطط من مستند Word باستخدام Aspose.Words for .NET
  type: TechArticle
- description: تعلم كيفية حذف سلسلة بيانات محددة من مخطط عمودي في مستند Word باستخدام
    Aspose.Words for .NET.
  name: إزالة سلسلة مخطط من مستند Word باستخدام Aspose.Words for .NET
  steps:
  - name: أنشئ مستند Word جديدًا وDocumentBuilder مرتبطًا به.
    text: أنشئ مستند Word جديدًا وDocumentBuilder مرتبطًا به.
  - name: أدرج مخططًا عموديًا بحجم 432×252 نقطة واحصل على كائن Chart لمزيد من المعالجة.
    text: أدرج مخططًا عموديًا بحجم 432×252 نقطة واحصل على كائن Chart لمزيد من المعالجة.
  - name: حدد الفهرس الصفري للسلسلة التي يجب إزالتها (السلسلة الثانية).
    text: حدد الفهرس الصفري للسلسلة التي يجب إزالتها (السلسلة الثانية).
  - name: إذا كان الفهرس صالحًا، استدعِ RemoveAt على مجموعة Series الخاصة بالمخطط
      لحذف تلك السلسلة.
    text: إذا كان الفهرس صالحًا، استدعِ RemoveAt على مجموعة Series الخاصة بالمخطط
      لحذف تلك السلسلة.
  - name: احفظ المستند المحدث إلى ملف .docx.
    text: احفظ المستند المحدث إلى ملف .docx.
  type: HowTo
- questions:
  - answer: سيفشل شرط `if` (`targetSeriesIdx < columnChart.Series.Count`)، وبالتالي
      لن يتم استدعاء `RemoveAt` ولن يتغير المخطط.
    question: ماذا يحدث إذا مررت فهرسًا يساوي عدد السلاسل في المخطط؟
  - answer: نعم، بعد `columnChart.Series.RemoveAt` يتم إعادة توليد وسيلة الإيضاح لتعكس
      السلاسل المتبقية، وبالتالي يختفي العنصر المُزال من وسيلة الإيضاح.
    question: هل يؤدي إزالة سلسلة إلى تحديث وسيلة إيضاح المخطط تلقائيًا؟
  - answer: تعمل الشيفرة مع أي نوع مخطط يدعم مجموعة `Series`؛ فقط غيّر `ChartType.Column`
      إلى النوع المطلوب عند إدراج المخطط.
    question: هل يمكنني استخدام نفس الشيفرة لحذف سلسلة من مخطط خطي أو مخطط دائري؟
  - answer: المخطط الذي لا يحتوي على أي سلسلة يظل `Shape` صالحًا وسيُحفظ، لكنه سيظهر
      فارغًا في المستند الناتج.
    question: إذا أزلت السلسلة الوحيدة في المخطط، هل سيظل المخطط يُحفظ بشكل صحيح؟
  type: FAQPage
images:
- /net/programming-with-charts/remove-chart-series/og-image.png
og_title: حذف سلسلة مخطط في مستند Word
og_description: دليل خطوة بخطوة لإزالة سلسلة بيانات من مخطط Word باستخدام Aspose.Words for .NET.
og_image_alt: دليل يوضح كيفية حذف سلسلة بيانات محددة من مخطط عمودي في مستند Word باستخدام Aspose.Words for .NET.
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# إزالة سلسلة مخطط من مستند Word باستخدام Aspose.Words
يُظهر هذا البرنامج التعليمي كيفية إنشاء مستند Word، إضافة مخطط عمودي باستخدام DocumentBuilder، ثم حذف سلسلة بيانات محددة من ذلك المخطط باستخدام طريقة ChartSeriesCollection.RemoveAt. في النهاية، ستحصل على مستند محفوظ مع إزالة السلسلة غير المرغوب فيها، مما يمنحك تحكمًا دقيقًا في محتوى المخطط مباشرةً من شفرة .NET.

---

{{< tutorial-widget sourcePath="words/net/programming-with-charts/remove-chart-series" >}}


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
   using Aspose.Words.Fields;
   using System.Drawing;
   ```

4. Apply License (Optional):
   To use the full version, [apply a license](https://purchase.aspose.com/temporary-license/) or use a [free trial](https://releases.aspose.com/).

## Also See
[Aspose.Words for .NET Documentation](https://docs.aspose.com/words/net/)
[Aspose.Words for .NET References](https://reference.aspose.com/words/net/)

## Frequently asked questions

**Q: ماذا يحدث إذا مررت فهرسًا يساوي عدد السلاسل في المخطط؟**  
A: سيفشل شرط `if` (`targetSeriesIdx < columnChart.Series.Count`)، وبالتالي لن يتم استدعاء `RemoveAt` ولن يتغير المخطط.

**Q: هل يؤدي إزالة سلسلة إلى تحديث وسيلة إيضاح المخطط تلقائيًا؟**  
A: نعم، بعد `columnChart.Series.RemoveAt` يتم إعادة توليد وسيلة الإيضاح لتعكس السلاسل المتبقية، وبالتالي يختفي العنصر المُزال من وسيلة الإيضاح.

**Q: هل يمكنني استخدام نفس الشيفرة لحذف سلسلة من مخطط خطي أو مخطط دائري؟**  
A: تعمل الشيفرة مع أي نوع مخطط يدعم مجموعة `Series`؛ فقط غيّر `ChartType.Column` إلى النوع المطلوب عند إدراج المخطط.

**Q: إذا أزلت السلسلة الوحيدة في المخطط، هل سيظل المخطط يُحفظ بشكل صحيح؟**  
A: المخطط الذي لا يحتوي على أي سلسلة يظل `Shape` صالحًا وسيُحفظ، لكنه سيظهر فارغًا في المستند الناتج.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}