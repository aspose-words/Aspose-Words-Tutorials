---
title: إعادة تحجيم المخطط بشكل متناسب عند تغيير حجم الصفحة في Word باستخدام Aspose.Words for .NET
weight: 210
limit:
description: تعلم كيفية إعادة تحجيم مخطط عمودي في Word تلقائيًا عند تحويل المستند إلى A4 باستخدام Aspose.Words for .NET.
keywords: [chart resizing, Aspose.Words for .NET, Word column chart, automatic chart scaling, A4 page size, resize chart in Word]
url: /net/programming-with-charts/resize-chart/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: تعلم كيفية إعادة تحجيم مخطط عمودي في Word تلقائيًا عند تحويل المستند
    إلى A4 باستخدام Aspose.Words for .NET.
  headline: إعادة تحجيم المخطط بشكل متناسب عند تغيير حجم الصفحة في Word باستخدام Aspose.Words
    for .NET
  type: TechArticle
- description: تعلم كيفية إعادة تحجيم مخطط عمودي في Word تلقائيًا عند تحويل المستند
    إلى A4 باستخدام Aspose.Words for .NET.
  name: إعادة تحجيم المخطط بشكل متناسب عند تغيير حجم الصفحة في Word باستخدام Aspose.Words
    for .NET
  steps:
  - name: أنشئ كائن Document جديد و DocumentBuilder لتعديله.
    text: أنشئ كائن Document جديد و DocumentBuilder لتعديله.
  - name: أدرج مخططًا عموديًا بحجم 432×252 نقطة واحصل على كائن Chart الخاص به.
    text: أدرج مخططًا عموديًا بحجم 432×252 نقطة واحصل على كائن Chart الخاص به.
  - name: عيّن نص عنوان المخطط إلى "Quarterly Revenue" واجعله مرئيًا.
    text: عيّن نص عنوان المخطط إلى "Quarterly Revenue" واجعله مرئيًا.
  - name: احفظ المستند إلى ملف يُظهر حجم المخطط الأصلي.
    text: احفظ المستند إلى ملف يُظهر حجم المخطط الأصلي.
  - name: غيّر حجم ورق المستند إلى A4 وقم بتحديث التخطيط.
    text: غيّر حجم ورق المستند إلى A4 وقم بتحديث التخطيط.
  - name: احسب عرضًا جديدًا للمخطط يساوي 80 % من عرض الصفحة مع الحفاظ على نسبة الأبعاد
      الأصلية.
    text: احسب عرضًا جديدًا للمخطط يساوي 80 % من عرض الصفحة مع الحفاظ على نسبة الأبعاد
      الأصلية.
  - name: إذا كان الشكل يحتوي على مخطط، طبّق العرض والارتفاع المحسوبين لإعادة تحجيمه.
    text: إذا كان الشكل يحتوي على مخطط، طبّق العرض والارتفاع المحسوبين لإعادة تحجيمه.
  - name: احفظ المستند بعد إعادة تحجيم المخطط ليعكس حجم الصفحة الجديد.
    text: احفظ المستند بعد إعادة تحجيم المخطط ليعكس حجم الصفحة الجديد.
  type: HowTo
- questions:
  - answer: نعم. تغيير `docBuilder.PageSetup.PaperSize` لا يضبط الأشكال الموجودة تلقائيًا،
      لذا عليك إعادة حساب وتعيين `chartContainer.Width` و `Height` بنفسك كما هو موضح.
    question: هل أحتاج إلى إعادة تحجيم المخطط يدويًا بعد تغيير حجم ورق المستند؟
  - answer: يقوم بتخزين `originalAspectRatio = chartContainer.Height / chartContainer.Width`
      ثم يحسب `newChartHeight = newChartWidth * originalAspectRatio` بعد تحديد العرض
      الجديد.
    question: كيف يحافظ الكود على نسبة العرض إلى الارتفاع الأصلية للمخطط عند إعادة
      التحجيم؟
  - answer: '`UpdatePageLayout()` يجبر محرك التخطيط على إعادة تقييم أبعاد الصفحة،
      مما يضمن أن `docBuilder.PageSetup.PageWidth` يعكس العرض الجديد للـ A4 قبل إعادة
      حساب حجم المخطط.'
    question: لماذا يتم استدعاء `myDoc.UpdatePageLayout()` بعد ضبط حجم الورق إلى A4؟
  - answer: حارس `if (chartContainer.HasChart)` يمنع الكود من تعيين `Width` و `Height`
      عندما لا يكون هناك مخطط، مما يتجنب استثناءً أثناء التشغيل.
    question: ماذا يحدث إذا كان الشكل المُدرج لا يحتوي فعليًا على مخطط؟
  - answer: بالطبع—استبدل المضاعف `0.8` بأي نسبة تفضلها؛ سيستمر باقي منطق إعادة التحجيم
      في الحفاظ على نسبة الأبعاد الأصلية.
    question: هل يمكنني تغيير معامل التحجيم بنسبة 80 % إلى قيمة أخرى؟
  type: FAQPage
images:
- /net/programming-with-charts/resize-chart/og-image.png
og_title: إعادة تحجيم مخطط Word عند التحويل إلى A4
og_description: حافظ على تناسب مخططك بإعادة تحجيمه تلقائيًا بعد تحويل المستند إلى A4.
og_image_alt: لقطة شاشة تُظهر مخططًا عموديًا تم إعادة تحجيمه تلقائيًا ليتناسب مع مستند Word بحجم A4 باستخدام Aspose.Words for .NET
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# إعادة تحجيم المخطط بشكل متناسب عند تغيير حجم الصفحة في Word باستخدام Aspose.Words
يوضح هذا البرنامج التعليمي كيفية إدراج مخطط عمودي في مستند Word، وتغيير حجم صفحة المستند إلى A4، وجعل المخطط يعيد تحجيمه تلقائيًا بحيث يبقى متناسبًا مع عرض الصفحة الجديد. باتباع الخطوات، ستلاحظ أن المخطط يضبط أبعاده دون تعديل يدوي، مما يضمن تخطيطًا ثابتًا عبر تنسيقات الصفحات المختلفة.

---

{{< tutorial-widget sourcePath="words/net/programming-with-charts/resize-chart" >}}


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

**Q: هل أحتاج إلى إعادة تحجيم المخطط يدويًا بعد تغيير حجم ورق المستند؟**  
A: نعم. تغيير `docBuilder.PageSetup.PaperSize` لا يضبط الأشكال الموجودة تلقائيًا، لذا عليك إعادة حساب وتعيين `chartContainer.Width` و `Height` بنفسك كما هو موضح.

**Q: كيف يحافظ الكود على نسبة العرض إلى الارتفاع الأصلية للمخطط عند إعادة التحجيم؟**  
A: يقوم بتخزين `originalAspectRatio = chartContainer.Height / chartContainer.Width` ثم يحسب `newChartHeight = newChartWidth * originalAspectRatio` بعد تحديد العرض الجديد.

**Q: لماذا يتم استدعاء `myDoc.UpdatePageLayout()` بعد ضبط حجم الورق إلى A4؟**  
A: `UpdatePageLayout()` يجبر محرك التخطيط على إعادة تقييم أبعاد الصفحة، مما يضمن أن `docBuilder.PageSetup.PageWidth` يعكس العرض الجديد للـ A4 قبل إعادة حساب حجم المخطط.

**Q: ماذا يحدث إذا كان الشكل المُدرج لا يحتوي فعليًا على مخطط؟**  
A: حارس `if (chartContainer.HasChart)` يمنع الكود من تعيين `Width` و `Height` عندما لا يكون هناك مخطط، مما يتجنب استثناءً أثناء التشغيل.

**Q: هل يمكنني تغيير معامل التحجيم بنسبة 80 % إلى قيمة أخرى؟**  
A: بالطبع—استبدل المضاعف `0.8` بأي نسبة تفضلها؛ سيستمر باقي منطق إعادة التحجيم في الحفاظ على نسبة الأبعاد الأصلية.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}