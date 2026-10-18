---
title: تحديث بيانات سلاسل المخطط في مستند Word باستخدام Aspose.Words for .NET
weight: 610
limit:
description: تعلم تعديل نقاط بيانات سلاسل المخطط في مستند Word وتحديث المخطط باستخدام Aspose.Words for .NET.
keywords: [Aspose.Words for .NET, modify chart series, update chart data points, Word chart manipulation, C# chart editing, column chart in Word]
url: /net/programming-with-charts/modify-chart-series/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: تعلم تعديل نقاط بيانات سلاسل المخطط في مستند Word وتحديث المخطط باستخدام
    Aspose.Words for .NET.
  headline: تحديث بيانات سلاسل المخطط في مستند Word باستخدام Aspose.Words for .NET
  type: TechArticle
- description: تعلم تعديل نقاط بيانات سلاسل المخطط في مستند Word وتحديث المخطط باستخدام
    Aspose.Words for .NET.
  name: تحديث بيانات سلاسل المخطط في مستند Word باستخدام Aspose.Words for .NET
  steps:
  - name: أنشئ مستندًا جديدًا، وأدرج مخططًا عموديًا باستخدام DocumentBuilder، واحفظه
      كملف أولي.
    text: أنشئ مستندًا جديدًا، وأدرج مخططًا عموديًا باستخدام DocumentBuilder، واحفظه
      كملف أولي.
  - name: افتح الملف المحفوظ وحدد شكل المخطط للحصول على كائن Chart الموجود.
    text: افتح الملف المحفوظ وحدد شكل المخطط للحصول على كائن Chart الموجود.
  - name: امسح قيم السلسلة الأولى وأضف نقاطًا جديدة، ثم عدل السلسلة الثانية بإزالة
      نقطتها الأولى وإضافة نقطة جديدة.
    text: امسح قيم السلسلة الأولى وأضف نقاطًا جديدة، ثم عدل السلسلة الثانية بإزالة
      نقطتها الأولى وإضافة نقطة جديدة.
  - name: احفظ المستند المعدل في ملف جديد يحتوي على المخطط المحدث.
    text: احفظ المستند المعدل في ملف جديد يحتوي على المخطط المحدث.
  type: HowTo
- questions:
  - answer: استخدم `document.GetChildNodes(NodeType.Shape, true)` للحصول على جميع
      الأشكال، ثم قم بالترشيح باستخدام `s.HasChart` واختر الأول (أو الشكل الذي تحتاجه)
      – هذا يجنب اختيار الصور أو مربعات النص غير المتعلقة.
    question: كيف يمكنني تحديد موقع شكل المخطط بثقة في مستند قد يحتوي على أشكال أخرى؟
  - answer: '`ClearValues()` يزيل نقاط البيانات الموجودة؛ بدونها تُضاف النقاط الجديدة
      إلى القديمة، مما قد ينتج فئات مكررة أو إجماليات غير صحيحة.'
    question: لماذا يجب استدعاء `ClearValues()` قبل إضافة نقاط جديدة إلى سلسلة؟
  - answer: استخدم `FromString` عندما تكون فئات المحور X للمخطط نصية (مثلاً "Group
      A"), واستخدم `FromDouble` عندما يتوقع المحور قيمًا رقمية مثل التواريخ أو القياسات.
    question: متى يجب استخدام `ChartXValue.FromString` مقابل `ChartXValue.FromDouble`
      لقيم المحور X؟
  - answer: محاولة الوصول إلى سلسلة غير موجودة تُثير استثناء `ArgumentOutOfRangeException`؛
      تحقق دائمًا من `existingChart.Series.Count` قبل الإشارة إلى فهرس معين.
    question: ماذا يحدث إذا كان المخطط يحتوي على سلسلة واحدة فقط وحاولت الوصول إلى
      `existingChart.Series[1]`؟
  - answer: حفظ الـ `openedDoc` كافٍ لأنه هو نسخة المستند التي تحتوي على المخطط المعدل؛
      الـ `document` الأصلي استُخدم فقط لإنشاء الملف الأولي.
    question: هل يجب علي إعادة حفظ الـ `document` الأصلي بعد تعديل المخطط، أم أن حفظ
      الـ `openedDoc` كافٍ؟
  type: FAQPage
images:
- /net/programming-with-charts/modify-chart-series/og-image.png
og_title: تحرير بيانات سلاسل المخطط في Word
og_description: دليل خطوة بخطوة لتغيير قيم سلاسل المخطط في ملف Word باستخدام Aspose.Words for .NET.
og_image_alt: دليل يوضح مستند Word يحتوي على مخطط عمودي قبل وبعد تحديث بيانات سلاسله باستخدام Aspose.Words for .NET.
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# تحديث بيانات سلاسل المخطط في مستند Word باستخدام Aspose.Words
يوضح هذا البرنامج التعليمي كيفية إنشاء مستند Word يحتوي على مخطط عمودي، ثم إعادة فتح الملف، واسترجاع سلاسل المخطط الموجودة، وتعديل نقاط البيانات الخاصة بها، وحفظ المستند بحيث يعرض المخطط القيم الجديدة. اتبع الشيفرة خطوة بخطوة لترى مدى سهولة تعديل بيانات المخطط برمجيًا باستخدام Aspose.Words for .NET.

---

{{< tutorial-widget sourcePath="words/net/programming-with-charts/modify-chart-series" >}}


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

**Q: كيف يمكنني تحديد موقع شكل المخطط بثقة في مستند قد يحتوي على أشكال أخرى؟**  
A: استخدم `document.GetChildNodes(NodeType.Shape, true)` للحصول على جميع الأشكال، ثم قم بالترشيح باستخدام `s.HasChart` واختر الأول (أو الشكل الذي تحتاجه) – هذا يجنب اختيار الصور أو مربعات النص غير المتعلقة.

**Q: لماذا يجب استدعاء `ClearValues()` قبل إضافة نقاط جديدة إلى سلسلة؟**  
A: `ClearValues()` يزيل نقاط البيانات الموجودة؛ بدونها تُضاف النقاط الجديدة إلى القديمة، مما قد ينتج فئات مكررة أو إجماليات غير صحيحة.

**Q: متى يجب استخدام `ChartXValue.FromString` مقابل `ChartXValue.FromDouble` لقيم المحور X؟**  
A: استخدم `FromString` عندما تكون فئات المحور X للمخطط نصية (مثلاً "Group A"), واستخدم `FromDouble` عندما يتوقع المحور قيمًا رقمية مثل التواريخ أو القياسات.

**Q: ماذا يحدث إذا كان المخطط يحتوي على سلسلة واحدة فقط وحاولت الوصول إلى `existingChart.Series[1]`؟**  
A: محاولة الوصول إلى سلسلة غير موجودة تُثير استثناء `ArgumentOutOfRangeException`؛ تحقق دائمًا من `existingChart.Series.Count` قبل الإشارة إلى فهرس معين.

**Q: هل يجب علي إعادة حفظ الـ `document` الأصلي بعد تعديل المخطط، أم أن حفظ الـ `openedDoc` كافٍ؟**  
A: حفظ الـ `openedDoc` كافٍ لأنه هو نسخة المستند التي تحتوي على المخطط المعدل؛ الـ `document` الأصلي استُخدم فقط لإنشاء الملف الأولي.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}