---
title: إدراج مخطط عمودي مخصص في مستند Word باستخدام Aspose.Words for .NET
weight: 310
limit:
description: إنشاء ملف Word، وإدراج مخطط عمودي، واستبدال بياناته بمصفوفة مخصصة، وإضافة عنوان، ثم حفظه—كل ذلك باستخدام Aspose.Words for .NET.
keywords: [Aspose.Words for .NET, custom chart, column chart, Word document chart, populate chart from array, insert chart Aspose.Words]
url: /net/programming-with-charts/insert-custom-chart/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: إنشاء ملف Word، وإدراج مخطط عمودي، واستبدال بياناته بمصفوفة مخصصة،
    وإضافة عنوان، ثم حفظه—كل ذلك باستخدام Aspose.Words for .NET.
  headline: إدراج مخطط عمودي مخصص في مستند Word باستخدام Aspose.Words for .NET
  type: TechArticle
- description: إنشاء ملف Word، وإدراج مخطط عمودي، واستبدال بياناته بمصفوفة مخصصة،
    وإضافة عنوان، ثم حفظه—كل ذلك باستخدام Aspose.Words for .NET.
  name: إدراج مخطط عمودي مخصص في مستند Word باستخدام Aspose.Words for .NET
  steps:
  - name: إنشاء مستند Document جديد وDocumentBuilder مرتبط به.
    text: إنشاء مستند Document جديد وDocumentBuilder مرتبط به.
  - name: إدراج مخطط عمودي بحجم 432×252 نقطة في المستند والحصول على كائن Chart الخاص
      به.
    text: إدراج مخطط عمودي بحجم 432×252 نقطة في المستند والحصول على كائن Chart الخاص
      به.
  - name: إزالة السلسلة النموذجية التي تم إنشاؤها تلقائيًا من المخطط.
    text: إزالة السلسلة النموذجية التي تم إنشاؤها تلقائيًا من المخطط.
  - name: تحديد تسميات فئات المحور X وعناصر وسيلة الإيضاح لكل سلسلة.
    text: تحديد تسميات فئات المحور X وعناصر وسيلة الإيضاح لكل سلسلة.
  - name: إنشاء مصفوفة ثنائية الأبعاد حيث يحتوي كل صف على القيم الخاصة بسلسلة واحدة.
    text: إنشاء مصفوفة ثنائية الأبعاد حيث يحتوي كل صف على القيم الخاصة بسلسلة واحدة.
  - name: التكرار عبر كل سلسلة، استخراج قيم الصف الخاصة بها من المصفوفة، وإضافة السلسلة
      إلى المخطط مع عنصر وسيلة الإيضاح المقابل وتسميات المحور X.
    text: التكرار عبر كل سلسلة، استخراج قيم الصف الخاصة بها من المصفوفة، وإضافة السلسلة
      إلى المخطط مع عنصر وسيلة الإيضاح المقابل وتسميات المحور X.
  - name: تعيين نص عنوان المخطط إلى 'Half‑Yearly Revenue' وجعله مرئيًا.
    text: تعيين نص عنوان المخطط إلى 'Half‑Yearly Revenue' وجعله مرئيًا.
  - name: حفظ المستند الذي يحتوي على المخطط المخصص إلى ملف .docx.
    text: حفظ المستند الذي يحتوي على المخطط المخصص إلى ملف .docx.
  type: HowTo
- questions:
  - answer: '`Chart.Series.Add` يتوقع أن يكون طول مصفوفة القيم مساويًا لعدد تسميات
      المحور X، ويجب إضافة سلسلة واحدة بالضبط لكل **عنصر وسيلة إيضاح**؛ أي عدم تطابق
      سيسبب رمي `ArgumentException` أثناء التشغيل.'
    question: ماذا لو لم تتطابق الصفوف أو الأعمدة في `dataMatrix` مع أطوال `legendEntries`
      أو `xLabels`؟
  - answer: نعم—استبدل `ChartType.Column` في `docBuilder.InsertChart` بأي `ChartType`
      آخر (مثلاً `ChartType.Line`) وستقوم استدعاءات `Series.Add` اللاحقة بتعبئة المخطط
      الجديد بنفس الطريقة.
    question: هل يمكنني استخدام نوع مخطط مختلف، مثل مخطط خطي، مع نفس منطق تعبئة البيانات؟
  - answer: قم بضبط خصائص `Width` و `Height` لكائن `Shape` الذي تُعيده `InsertChart`
      (مثلاً، `chartContainer.Width = 500; chartContainer.Height = 300;`).
    question: كيف يمكنني تغيير حجم المخطط بعد إدراجه؟
  - answer: قم بتعيين `chartObj.Series[i].HasDataLabel = true;` لكل سلسلة بعد إضافتها،
      أو قم بالتكرار عبر `chartObj.Series` وتفعيل `HasDataLabel` لعرض القيم على المخطط.
    question: هل هناك طريقة سريعة لعرض تسميات البيانات على كل عمود في المخطط؟
  type: FAQPage
images:
- /net/programming-with-charts/insert-custom-chart/og-image.png
og_title: إضافة مخطط عمودي مخصص إلى مستند Word
og_description: استبدال البيانات الافتراضية للمخطط بمصفوفتك الخاصة وتعيين عنوان في ثوانٍ.
og_image_alt: لقطة شاشة تُظهر مستند Word يحتوي على مخطط عمودي مخصص تم إنشاؤه باستخدام Aspose.Words for .NET
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# إدراج مخطط عمودي مخصص في مستند Word باستخدام Aspose.Words
يُرشدك هذا البرنامج التعليمي إلى إنشاء مستند Word، وإدراج مخطط عمودي، ومسح بياناته الافتراضية، وتعبئة المخطط بقيم مخصصة من مصفوفة ثنائية الأبعاد—حيث يتم ربط كل صف بسلسلة وكل عمود بفئة. ستتعرف أيضًا على كيفية إضافة عنوان للمخطط قبل حفظ الملف. اتبع الخطوات لإنشاء مخطط مخصص بالكامل مباشرةً في ملف Word الخاص بك.

---

{{< tutorial-widget sourcePath="words/net/programming-with-charts/insert-custom-chart" >}}


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

**Q: ماذا لو لم تتطابق الصفوف أو الأعمدة في `dataMatrix` مع أطوال `legendEntries` أو `xLabels`؟**  
A: `Chart.Series.Add` يتوقع أن يكون طول مصفوفة القيم مساويًا لعدد تسميات المحور X، ويجب إضافة سلسلة واحدة بالضبط لكل **عنصر وسيلة إيضاح**؛ أي عدم تطابق سيسبب رمي `ArgumentException` أثناء التشغيل.

**Q: هل يمكنني استخدام نوع مخطط مختلف، مثل مخطط خطي، مع نفس منطق تعبئة البيانات؟**  
A: نعم—استبدل `ChartType.Column` في `docBuilder.InsertChart` بأي `ChartType` آخر (مثلاً `ChartType.Line`) وستقوم استدعاءات `Series.Add` اللاحقة بتعبئة المخطط الجديد بنفس الطريقة.

**Q: كيف يمكنني تغيير حجم المخطط بعد إدراجه؟**  
A: قم بضبط خصائص `Width` و `Height` لكائن `Shape` الذي تُعيده `InsertChart` (مثلاً، `chartContainer.Width = 500; chartContainer.Height = 300;`).

**Q: هل هناك طريقة سريعة لعرض تسميات البيانات على كل عمود في المخطط؟**  
A: قم بتعيين `chartObj.Series[i].HasDataLabel = true;` لكل سلسلة بعد إضافتها، أو قم بالتكرار عبر `chartObj.Series` وتفعيل `HasDataLabel` لعرض القيم على المخطط.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}