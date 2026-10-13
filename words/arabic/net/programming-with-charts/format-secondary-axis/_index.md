---
title: تنسيق المحور Y الثانوي كعملة في مخطط Word باستخدام Aspose.Words for .NET
weight: 710
limit:
description: تعلم كيفية إضافة وتنسيق محور Y ثانوي كعملة في مخطط خطي داخل Word باستخدام Aspose.Words for .NET.
keywords: [Aspose.Words for .NET, format secondary axis, currency axis formatting, Word line chart secondary series, secondary Y axis .NET, chart axis number format]
url: /net/programming-with-charts/format-secondary-axis/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: تعلم كيفية إضافة وتنسيق محور Y ثانوي كعملة في مخطط خطي داخل Word باستخدام
    Aspose.Words for .NET.
  headline: تنسيق المحور Y الثانوي كعملة في مخطط Word باستخدام Aspose.Words for .NET
  type: TechArticle
- description: تعلم كيفية إضافة وتنسيق محور Y ثانوي كعملة في مخطط خطي داخل Word باستخدام
    Aspose.Words for .NET.
  name: تنسيق المحور Y الثانوي كعملة في مخطط Word باستخدام Aspose.Words for .NET
  steps:
  - name: أنشئ مستند Word جديد فارغ وDocumentBuilder لتعديله.
    text: أنشئ مستند Word جديد فارغ وDocumentBuilder لتعديله.
  - name: أدرج مخططًا خطيًا بحجم 450×250 نقطة في المستند واحصل على كائن Chart الخاص
      به.
    text: أدرج مخططًا خطيًا بحجم 450×250 نقطة في المستند واحصل على كائن Chart الخاص
      به.
  - name: احذف سلسلة العنصر النائب الافتراضية التي يضيفها Aspose إلى مخطط جديد.
    text: احذف سلسلة العنصر النائب الافتراضية التي يضيفها Aspose إلى مخطط جديد.
  - name: عرّف تسميات الأرباع وأضف سلسلة بيانات أساسية بقيم نموذجية إلى المخطط.
    text: عرّف تسميات الأرباع وأضف سلسلة بيانات أساسية بقيم نموذجية إلى المخطط.
  - name: أنشئ مجموعة سلاسل ثانوية من النوع Line وعيّنها إلى مجموعة المحور الثانوي.
    text: أنشئ مجموعة سلاسل ثانوية من النوع Line وعيّنها إلى مجموعة المحور الثانوي.
  - name: أخفِ المحور X الثانوي بحيث يكون المحور Y الثانوي هو الوحيد الظاهر.
    text: أخفِ المحور X الثانوي بحيث يكون المحور Y الثانوي هو الوحيد الظاهر.
  - name: اعرض عنوان المحور Y الثانوي وضع نصه إلى "Sales (USD)".
    text: اعرض عنوان المحور Y الثانوي وضع نصه إلى "Sales (USD)".
  - name: عيّن تنسيق الأرقام للمحور Y الثانوي إلى نمط عملة برقمين عشريين وافصل هذا
      التنسيق عن تنسيق المصدر.
    text: عيّن تنسيق الأرقام للمحور Y الثانوي إلى نمط عملة برقمين عشريين وافصل هذا
      التنسيق عن تنسيق المصدر.
  - name: أضف سلسلة مساعدة إلى المجموعة الثانوية، موفرًا بيانات سيتم رسمها مقابل المحور
      Y الثانوي.
    text: أضف سلسلة مساعدة إلى المجموعة الثانوية، موفرًا بيانات سيتم رسمها مقابل المحور
      Y الثانوي.
  - name: احفظ المستند النهائي في ملف باسم ProfitChart.docx في الدليل الحالي.
    text: احفظ المستند النهائي في ملف باسم ProfitChart.docx في الدليل الحالي.
  type: HowTo
- questions:
  - answer: سيحتفظ المخطط بسلسلة العنصر النائب الافتراضية التي يضيفها Aspose.Words،
      وبالتالي ستظهر "Main Series" المخصصة لديك إلى جانب نقاط بيانات غير مرغوب فيها.
    question: ماذا يحدث إذا حذفت استدعاء `lineChart.Series.Clear()`؟
  - answer: عيّن `secondarySeriesGroup.AxisX.Hidden = false;` (أو ببساطة احذف السطر
      الذي يضبطه إلى `true`).
    question: كيف يمكنني عرض المحور X الثانوي بدلاً من إخفائه؟
  - answer: نعم – غيّر سلسلة التنسيق، مثلاً `secondarySeriesGroup.AxisY.NumberFormat.FormatCode
      = \"\\\"€\\\"#,##0.00\";` لليورو أو عدّل النمط ليتناسب مع إعدادات اللغة الخاصة
      بك.
    question: هل يمكنني استخدام رمز عملة مختلف أو تنسيق مختلف للمحور Y الثانوي؟
  - answer: عند كون `IsLinkedToSource` صحيحًا، يرث المحور تنسيق الرقم من مصدر البيانات
      الأساسي، متجاوزًا أي `FormatCode` مخصص؛ ضبطه على false يجبر المخطط على استخدام
      التنسيق الذي تحدده.
    question: لماذا يجب تعيين `IsLinkedToSource = false` عند تطبيق تنسيق رقم مخصص؟
  - answer: نعم، عيّن `secondarySeriesGroup.AxisY.Position = AxisPosition.Left;` (أو
      `Right` للإعداد الافتراضي) للتحكم في الجانب الذي يُرسم عليه المحور.
    question: هل يمكن نقل المحور Y الثانوي إلى الجانب الأيسر من المخطط؟
  type: FAQPage
images:
- /net/programming-with-charts/format-secondary-axis/og-image.png
og_title: تنسيق المحور الثانوي للمخطط كعملة
og_description: تعلم إضافة محور Y ثانوي إلى مخطط خطي في Word وتنسيقه كعملة برقمين عشريين.
og_image_alt: لقطة شاشة تُظهر مخططًا خطيًا في Word مع محور Y ثانوي مُنسق كعملة باستخدام Aspose.Words for .NET
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# تنسيق المحور Y الثانوي كعملة في مخطط Word باستخدام Aspose.Words
في هذا البرنامج التعليمي ستتعرف على كيفية إنشاء مستند Word، وإدراج مخطط خطي، وإضافة محور Y ثانوي، وتنسيق ذلك المحور كعملة برقمين عشريين، وربط سلسلة بيانات ثانوية به باستخدام Aspose.Words for .NET. يتيح تنسيق المحور الثانوي كعملة عرض البيانات المالية بوضوح جنبًا إلى جنب مع السلسلة الأساسية. اتبع التعليمات البرمجية خطوة بخطوة لتشاهد المخطط يُعرض مباشرةً في المستند المُنشأ.

---

{{< tutorial-widget sourcePath="words/net/programming-with-charts/format-secondary-axis" >}}


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

**Q: ماذا يحدث إذا حذفت استدعاء `lineChart.Series.Clear()`؟**  
A: سيحتفظ المخطط بسلسلة العنصر النائب الافتراضية التي يضيفها Aspose.Words، وبالتالي ستظهر "Main Series" المخصصة لديك إلى جانب نقاط بيانات غير مرغوب فيها.

**Q: كيف يمكنني عرض المحور X الثانوي بدلاً من إخفائه؟**  
A: عيّن `secondarySeriesGroup.AxisX.Hidden = false;` (أو ببساطة احذف السطر الذي يضبطه إلى `true`).

**Q: هل يمكنني استخدام رمز عملة مختلف أو تنسيق مختلف للمحور Y الثانوي؟**  
A: نعم – غيّر سلسلة التنسيق، مثلاً `secondarySeriesGroup.AxisY.NumberFormat.FormatCode = \"\\\"€\\\"#,##0.00\";` لليورو أو عدّل النمط ليتناسب مع إعدادات اللغة الخاصة بك.

**Q: لماذا يجب تعيين `IsLinkedToSource = false` عند تطبيق تنسيق رقم مخصص؟**  
A: عند كون `IsLinkedToSource` صحيحًا، يرث المحور تنسيق الرقم من مصدر البيانات الأساسي، متجاوزًا أي `FormatCode` مخصص؛ ضبطه على false يجبر المخطط على استخدام التنسيق الذي تحدده.

**Q: هل يمكن نقل المحور Y الثانوي إلى الجانب الأيسر من المخطط؟**  
A: نعم، عيّن `secondarySeriesGroup.AxisY.Position = AxisPosition.Left;` (أو `Right` للإعداد الافتراضي) للتحكم في الجانب الذي يُرسم عليه المحور.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}