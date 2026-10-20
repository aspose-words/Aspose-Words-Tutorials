---
title: إضافة سلسلة بيانات مسماة إلى مخطط هيستوجرام في Word باستخدام Aspose.Words for .NET
weight: 610
limit:
description: تعلم كيفية تضمين مخطط هيستوجرام في مستند Word وإضافة سلسلة بيانات مسماة باستخدام Aspose.Words for .NET.
keywords: [Aspose.Words for .NET, add named series chart, histogram chart in Word, ChartSeriesCollection Add overload, DocumentBuilder chart example, named data series Word]
url: /net/programming-with-charts/add-named-series/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: تعلم كيفية تضمين مخطط هيستوجرام في مستند Word وإضافة سلسلة بيانات مسماة
    باستخدام Aspose.Words for .NET.
  headline: إضافة سلسلة بيانات مسماة إلى مخطط هيستوجرام في Word باستخدام Aspose.Words
    for .NET
  type: TechArticle
- description: تعلم كيفية تضمين مخطط هيستوجرام في مستند Word وإضافة سلسلة بيانات مسماة
    باستخدام Aspose.Words for .NET.
  name: إضافة سلسلة بيانات مسماة إلى مخطط هيستوجرام في Word باستخدام Aspose.Words
    for .NET
  steps:
  - name: إنشاء مستند Word فارغ جديد و DocumentBuilder لتحريره.
    text: إنشاء مستند Word فارغ جديد و DocumentBuilder لتحريره.
  - name: إدراج شكل مخطط هيستوجرام بحجم 500×300 في المستند والحصول على كائن Chart
      الخاص به.
    text: إدراج شكل مخطط هيستوجرام بحجم 500×300 في المستند والحصول على كائن Chart
      الخاص به.
  - name: إزالة سلسلة العنصر النائب الافتراضية التي يضيفها Aspose.Words إلى المخططات
      الجديدة.
    text: إزالة سلسلة العنصر النائب الافتراضية التي يضيفها Aspose.Words إلى المخططات
      الجديدة.
  - name: إضافة سلسلة مسماة تُدعى "Demo Series" مع نقاط البيانات المحددة إلى مخطط
      الهيستوجرام.
    text: إضافة سلسلة مسماة تُدعى "Demo Series" مع نقاط البيانات المحددة إلى مخطط
      الهيستوجرام.
  - name: حفظ المستند إلى ملف .docx يحتوي على سلسلة المخطط المعنونة.
    text: حفظ المستند إلى ملف .docx يحتوي على سلسلة المخطط المعنونة.
  type: HowTo
- questions:
  - answer: '`InsertChart` ينشئ سلسلة عنصر نائب افتراضية؛ مسحها يزيل تلك السلسلة الفارغة
      بحيث يعرض المخطط فقط البيانات التي تضيفها باستخدام `Series.Add`.'
    question: لماذا أحتاج إلى استدعاء `histogramChart.Series.Clear()` قبل إضافة سلسلتي
      الخاصة؟
  - answer: نعم، استدعِ `histogramChart.Series.Add` عدة مرات، كل مرة باسم مميز وقيم
      `double[]`؛ ستُدرج كل سلسلة في وسيلة إيضاح المخطط بالاسم المقدم.
    question: هل يمكنني إضافة أكثر من سلسلة واحدة باستخدام نفس التحميل الزائد، وهل
      ستظهر كل منها مع تسمية خاصة بها؟
  - answer: التحميل الزائد يتوقع `double[]`؛ إذا كان لديك `int[]` أو مصفوفات عددية
      أخرى، قم بالتحويل أو التحويل إلى `double[]` قبل تمريره.
    question: هل الوسيط `double[]` هو النوع الوحيد المقبول لنقاط البيانات؟
  - answer: السلسلة التي تُمرّر كأول وسيط (مثلاً "Demo Series") تُستخدم كعنوان السلسلة
      وتُعرض في وسيلة إيضاح المخطط بشكل افتراضي.
    question: هل سيظهر اسم السلسلة الذي أزوده في المخطط تلقائيًا؟
  type: FAQPage
images:
- /net/programming-with-charts/add-named-series/og-image.png
og_title: إضافة سلسلة مسماة إلى مخطط هيستوجرام في Word
og_description: قم بتسمية سلسلة المخطط بسرعة في Word باستخدام Aspose.Words وشاهدها تُعرض فورًا.
og_image_alt: لقطة شاشة تُظهر مستند Word يحتوي على مخطط هيستوجرام يتضمن سلسلة بيانات معنونة تم إنشاؤها باستخدام Aspose.Words for .NET
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# إضافة سلسلة بيانات مسماة إلى مخطط هيستوجرام في Word باستخدام Aspose.Words
يوضح هذا البرنامج التعليمي كيفية إنشاء مستند Word باستخدام Aspose.Words for .NET، وإدراج مخطط هيستوجرام، وإضافة سلسلة بيانات معنونة باستخدام التحميل الزائد ChartSeriesCollection.Add الذي يقبل اسمًا وقيمًا. من خلال تسمية السلسلة يمكنك التعرف بوضوح على كل مجموعة بيانات داخل المخطط، مما يجعل المخرجات البصرية أسهل للقراءة والتفسير.

---

{{< tutorial-widget sourcePath="words/net/programming-with-charts/add-named-series" >}}


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

**Q: لماذا أحتاج إلى استدعاء `histogramChart.Series.Clear()` قبل إضافة سلسلتي الخاصة؟**  
A: `InsertChart` ينشئ سلسلة عنصر نائب افتراضية؛ مسحها يزيل تلك السلسلة الفارغة بحيث يعرض المخطط فقط البيانات التي تضيفها باستخدام `Series.Add`.

**Q: هل يمكنني إضافة أكثر من سلسلة واحدة باستخدام نفس التحميل الزائد، وهل ستظهر كل منها مع تسمية خاصة بها؟**  
A: نعم، استدعِ `histogramChart.Series.Add` عدة مرات، كل مرة باسم مميز وقيم `double[]`؛ ستُدرج كل سلسلة في وسيلة إيضاح المخطط بالاسم المقدم.

**Q: هل الوسيط `double[]` هو النوع الوحيد المقبول لنقاط البيانات؟**  
A: التحميل الزائد يتوقع `double[]`؛ إذا كان لديك `int[]` أو مصفوفات عددية أخرى، قم بالتحويل أو التحويل إلى `double[]` قبل تمريره.

**Q: هل سيظهر اسم السلسلة الذي أزوده في المخطط تلقائيًا؟**  
A: السلسلة التي تُمرّر كأول وسيط (مثلاً "Demo Series") تُستخدم كعنوان السلسلة وتُعرض في وسيلة إيضاح المخطط بشكل افتراضي.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}