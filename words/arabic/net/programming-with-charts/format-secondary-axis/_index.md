---
title: تنسيق محور X الثانوي وتعيين وحدة العرض إلى الآلاف في مخططات Word الخطية باستخدام Aspose.Words for .NET
weight: 710
limit:
description: أنشئ مخططًا خطيًا في Word، أضف محور X ثانوي، عيّن وحدة عرضه إلى الآلاف، وطبق تنسيقًا رقميًا مخصصًا باستخدام Aspose.Words for .NET.
keywords: [secondary axis formatting, Aspose.Words for .NET, line chart axis units, display units thousands, custom numeric format axis, Word chart secondary X axis]
url: /net/programming-with-charts/format-secondary-axis/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: أنشئ مخططًا خطيًا في Word، أضف محور X ثانوي، عيّن وحدة عرضه إلى الآلاف،
    وطبق تنسيقًا رقميًا مخصصًا باستخدام Aspose.Words for .NET.
  headline: تنسيق محور X الثانوي وتعيين وحدة العرض إلى الآلاف في مخططات Word الخطية
    باستخدام Aspose.Words for .NET
  type: TechArticle
- description: أنشئ مخططًا خطيًا في Word، أضف محور X ثانوي، عيّن وحدة عرضه إلى الآلاف،
    وطبق تنسيقًا رقميًا مخصصًا باستخدام Aspose.Words for .NET.
  name: تنسيق محور X الثانوي وتعيين وحدة العرض إلى الآلاف في مخططات Word الخطية باستخدام
    Aspose.Words for .NET
  steps:
  - name: أنشئ كائن Document جديد و DocumentBuilder لبدء بناء ملف Word.
    text: أنشئ كائن Document جديد و DocumentBuilder لبدء بناء ملف Word.
  - name: أدرج مخططًا خطيًا بحجم 500×300 في المستند واحصل على كائن Chart.
    text: أدرج مخططًا خطيًا بحجم 500×300 في المستند واحصل على كائن Chart.
  - name: احذف سلسلة العرض التجريبية الافتراضية التي يضيفها Aspose.Words تلقائيًا.
    text: احذف سلسلة العرض التجريبية الافتراضية التي يضيفها Aspose.Words تلقائيًا.
  - name: عرّف مصفوفة من تسميات الفئات التي ستُستخدم لمحور X.
    text: عرّف مصفوفة من تسميات الفئات التي ستُستخدم لمحور X.
  - name: أضف سلسلة البيانات الأساسية المسماة \"Main Data\" باستخدام التسميات والقيم.
    text: أضف سلسلة البيانات الأساسية المسماة \"Main Data\" باستخدام التسميات والقيم.
  - name: أنشئ مجموعة سلسلة ثانوية من النوع Line وعيّنها إلى مجموعة المحور الثانوي.
    text: أنشئ مجموعة سلسلة ثانوية من النوع Line وعيّنها إلى مجموعة المحور الثانوي.
  - name: عيّن وحدة عرض محور X الثانوي إلى الآلاف بحيث تُعرض القيم بـ K.
    text: عيّن وحدة عرض محور X الثانوي إلى الآلاف بحيث تُعرض القيم بـ K.
  - name: طبق تنسيق رقمي مخصص \"#,##0.0\" على تسميات علامات محور X الثانوي.
    text: طبق تنسيق رقمي مخصص \"#,##0.0\" على تسميات علامات محور X الثانوي.
  - name: يمكنك إضافة سلسلة بيانات مساعدة إلى المجموعة الثانوية اختياريًا.
    text: يمكنك إضافة سلسلة بيانات مساعدة إلى المجموعة الثانوية اختياريًا.
  - name: احفظ المستند كملف .docx.
    text: احفظ المستند كملف .docx.
  type: HowTo
- questions:
  - answer: لا – إعدادات `AxisX` تتبع `ChartSeriesGroup`، لذا يمكنك تعيين `secondaryGroup.AxisX.DisplayUnit.Unit`
      و `secondaryGroup.AxisX.NumberFormat.FormatCode` قبل أو بعد إضافة السلاسل؛ سيُطبق
      التكوين على محور المجموعة في كلتا الحالتين.
    question: هل يجب علي إضافة السلسلة الثانوية قبل تعيين وحدة العرض وتنسيق الرقم
      على محور X الثانوي؟
  - answer: نعم – عيّن أي قيمة من `AxisBuiltInUnit`، على سبيل المثال `secondaryGroup.AxisX.DisplayUnit.Unit
      = AxisBuiltInUnit.Millions;` لعرض قيم المحور بالملايين بدلاً من الآلاف.
    question: هل يمكنني استخدام وحدة مدمجة مختلفة، مثل الملايين، لمحور X الثانوي؟
  - answer: لا – يتم تطبيق رمز التنسيق فقط على المحور الذي تعدّله (`secondaryGroup.AxisX.NumberFormat.FormatCode`)،
      لذا يظل محور X الأساسي بتنسيقه الافتراضي.
    question: هل سيؤثر التنسيق المخصص \"#,##0.0\" على تسميات محور X الأساسي؟
  - answer: سيحتوي المخطط على سلسلة العرض التجريبية الافتراضية بالإضافة إلى السلاسل
      التي تضيفها، مما قد يؤدي إلى خطوط إضافية وفئات غير متطابقة؛ مسح المجموعة يضمن
      ظهور البيانات التي تريدها فقط.
    question: ماذا يحدث إذا نسيت مسح سلسلة العرض التجريبية باستخدام `lineChart.Series.Clear();`؟
  type: FAQPage
images:
- /net/programming-with-charts/format-secondary-axis/og-image.png
og_title: تنسيق محور X الثانوي وتعيين الوحدات إلى الآلاف
og_description: أضف محور X ثانوي إلى مخطط خطي في Word وقم بتنسيق تساميه بالآلاف باستخدام نمط مخصص.
og_image_alt: دليل يوضح كيفية إضافة محور X ثانوي إلى مخطط خطي في Word وتنسيق تساميه لعرض الوحدات بالآلاف باستخدام Aspose.Words for .NET
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# تنسيق محور X الثانوي وتعيين وحدة العرض إلى الآلاف في مخططات Word الخطية باستخدام Aspose.Words
يُرشدك هذا البرنامج التعليمي إلى إنشاء مستند Word يحتوي على مخطط خطي، وإضافة محور X ثانوي، وتكوين ذلك المحور لعرض القيم بالآلاف. ستتعلم أيضًا كيفية تطبيق تنسيق رقمي مخصص على تسميات المحور الثانوي، مما يمنحك تحكمًا دقيقًا في طريقة عرض البيانات. اتبع الخطوات لتحسين قابلية قراءة المخططات متعددة المحاور في تقارير Word الخاصة بك.

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

**Q: هل يجب علي إضافة السلسلة الثانوية قبل تعيين وحدة العرض وتنسيق الرقم على محور X الثانوي؟**  
A: لا – إعدادات `AxisX` تتبع `ChartSeriesGroup`، لذا يمكنك تعيين `secondaryGroup.AxisX.DisplayUnit.Unit` و `secondaryGroup.AxisX.NumberFormat.FormatCode` قبل أو بعد إضافة السلاسل؛ سيُطبق التكوين على محور المجموعة في كلتا الحالتين.

**Q: هل يمكنني استخدام وحدة مدمجة مختلفة، مثل الملايين، لمحور X الثانوي؟**  
A: نعم – عيّن أي قيمة من `AxisBuiltInUnit`، على سبيل المثال `secondaryGroup.AxisX.DisplayUnit.Unit = AxisBuiltInUnit.Millions;` لعرض قيم المحور بالملايين بدلاً من الآلاف.

**Q: هل سيؤثر التنسيق المخصص \"#,##0.0\" على تسميات محور X الأساسي؟**  
A: لا – يتم تطبيق رمز التنسيق فقط على المحور الذي تعدّله (`secondaryGroup.AxisX.NumberFormat.FormatCode`)، لذا يظل محور X الأساسي بتنسيقه الافتراضي.

**Q: ماذا يحدث إذا نسيت مسح سلسلة العرض التجريبية باستخدام `lineChart.Series.Clear();`؟**  
A: سيحتوي المخطط على سلسلة العرض التجريبية الافتراضية بالإضافة إلى السلاسل التي تضيفها، مما قد يؤدي إلى خطوط إضافية وفئات غير متطابقة؛ مسح المجموعة يضمن ظهور البيانات التي تريدها فقط.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}