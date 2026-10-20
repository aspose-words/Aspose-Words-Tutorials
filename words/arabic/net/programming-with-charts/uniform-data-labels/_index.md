---
title: تعيين تسميات بيانات موحدة في مخطط عمودي باستخدام Aspose.Words for .NET
weight: 110
limit:
description: تعلم كيفية إنشاء مخطط عمودي في Word وتطبيق حجم خط ولون موحد لتسميات البيانات على جميع السلاسل باستخدام Aspose.Words for .NET.
keywords: [Aspose.Words for .NET, uniform data labels, chart data label formatting, column chart Word SDK, default data label style, Word document chart customization]
url: /net/programming-with-charts/uniform-data-labels/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: تعلم كيفية إنشاء مخطط عمودي في Word وتطبيق حجم خط ولون موحد لتسميات
    البيانات على جميع السلاسل باستخدام Aspose.Words for .NET.
  headline: تعيين تسميات بيانات موحدة في مخطط عمودي باستخدام Aspose.Words for .NET
  type: TechArticle
- description: تعلم كيفية إنشاء مخطط عمودي في Word وتطبيق حجم خط ولون موحد لتسميات
    البيانات على جميع السلاسل باستخدام Aspose.Words for .NET.
  name: تعيين تسميات بيانات موحدة في مخطط عمودي باستخدام Aspose.Words for .NET
  steps:
  - name: أنشئ مستند Word جديد فارغ وDocumentBuilder لتعديله.
    text: أنشئ مستند Word جديد فارغ وDocumentBuilder لتعديله.
  - name: أدرج مخططًا عموديًا بحجم 500×300 في المستند واحصل على كائن Chart الخاص به.
    text: أدرج مخططًا عموديًا بحجم 500×300 في المستند واحصل على كائن Chart الخاص به.
  - name: احذف سلسلة العينة الافتراضية التي يضيفها Aspose.Words إلى مخطط جديد.
    text: احذف سلسلة العينة الافتراضية التي يضيفها Aspose.Words إلى مخطط جديد.
  - name: حدد تسميات الفئات وأضف سلسلتين من البيانات (Item Alpha وItem Beta) مع قيمهما
      إلى المخطط.
    text: حدد تسميات الفئات وأضف سلسلتين من البيانات (Item Alpha وItem Beta) مع قيمهما
      إلى المخطط.
  - name: حدد حجم الخط واللون الأساسيين اللذين سيُطبقان على جميع تسميات البيانات.
    text: حدد حجم الخط واللون الأساسيين اللذين سيُطبقان على جميع تسميات البيانات.
  - name: فعّل تسميات البيانات لكل سلسلة، اعرض القيمة الرقمية، وطبق حجم الخط واللون
      المحددين مسبقًا.
    text: فعّل تسميات البيانات لكل سلسلة، اعرض القيمة الرقمية، وطبق حجم الخط واللون
      المحددين مسبقًا.
  - name: احفظ المستند كملف .docx.
    text: احفظ المستند كملف .docx.
  type: HowTo
- questions:
  - answer: '`InsertChart` ينشئ مخططًا يحتوي على سلسلة عينة افتراضية؛ مسحها يزيل هذا
      العنصر النائب بحيث يعرض المخطط فقط السلاسل التي تضيفها (`Item Alpha` و`Item
      Beta`).'
    question: لماذا أحتاج إلى استدعاء `chart.Series.Clear()` قبل إضافة سلسلتي الخاصة؟
  - answer: استبدل `Color.White` بأي قيمة من `System.Drawing.Color`، مثل `Color.Black`
      أو `Color.FromArgb(255, 30, 144, 255)`؛ يتم تطبيق اللون الجديد عبر `series.DataLabels.Font.Color`
      داخل الحلقة.
    question: كيف يمكنني تغيير لون تسمية البيانات إلى لون غير الأبيض؟
  - answer: ستُخفى تسميات البيانات، وبالتالي تصبح إعدادات الخط التي قمت بتطبيقها غير
      مرئية؛ يجب إبقاء `HasDataLabels` مضبوطًا على `true` لكي تظهر التسميات (وتنسيقها).
    question: ماذا يحدث إذا قمت بتعيين `series.HasDataLabels = false` بعد ضبط حجم
      الخط واللون؟
  - answer: نعم — كل `ChartSeries` يمتلك كائن `DataLabels` خاص به، لذا أي سلسلة تُضاف
      بعد الحلقة الأولية يجب أن تُعيّن لها `HasDataLabels` و`ShowValue` وخصائص الخط،
      إما عبر تكرار الحلقة مرة أخرى أو باستخراج التنسيق إلى طريقة مساعدة.
    question: هل أحتاج إلى تكرار الحلقة عبر السلاسل مرة أخرى إذا أضفت سلسلة أخرى لاحقًا
      في الشيفرة؟
  type: FAQPage
images:
- /net/programming-with-charts/uniform-data-labels/og-image.png
og_title: تطبيق تسميات بيانات موحدة على مخطط Word
og_description: قم بسرعة بإعطاء كل تسمية في المخطط نفس حجم الخط واللون باستخدام Aspose.Words for .NET.
og_image_alt: دليل يوضح مستند Word يحتوي على مخطط عمودي حيث تتشارك جميع تسميات البيانات نفس حجم الخط واللون، تم إنشاؤه باستخدام Aspose.Words for .NET.
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# تعيين تسميات بيانات موحدة في مخطط عمودي باستخدام Aspose.Words
يوضح هذا البرنامج التعليمي كيفية إنشاء مستند Word، وإدراج مخطط عمودي، وإضافة سلاسل بيانات مخصصة باستخدام Aspose.Words for .NET. ثم يوضح كيفية تحديد حجم الخط ولون التسمية الافتراضيين للبيانات بحيث تعرض كل سلسلة في المخطط تسميات متطابقة. من خلال تطبيق نمط واحد، تضمن مظهرًا بصريًا متسقًا عبر كامل المخطط.

---

{{< tutorial-widget sourcePath="words/net/programming-with-charts/uniform-data-labels" >}}


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

**Q: لماذا أحتاج إلى استدعاء `chart.Series.Clear()` قبل إضافة سلسلتي الخاصة؟**  
A: `InsertChart` ينشئ مخططًا يحتوي على سلسلة عينة افتراضية؛ مسحها يزيل هذا العنصر النائب بحيث يعرض المخطط فقط السلاسل التي تضيفها (`Item Alpha` و`Item Beta`).

**Q: كيف يمكنني تغيير لون تسمية البيانات إلى لون غير الأبيض؟**  
A: استبدل `Color.White` بأي قيمة من `System.Drawing.Color`، مثل `Color.Black` أو `Color.FromArgb(255, 30, 144, 255)`؛ يتم تطبيق اللون الجديد عبر `series.DataLabels.Font.Color` داخل الحلقة.

**Q: ماذا يحدث إذا قمت بتعيين `series.HasDataLabels = false` بعد ضبط حجم الخط واللون؟**  
A: ستُخفى تسميات البيانات، وبالتالي تصبح إعدادات الخط التي قمت بتطبيقها غير مرئية؛ يجب إبقاء `HasDataLabels` مضبوطًا على `true` لكي تظهر التسميات (وتنسيقها).

**Q: هل أحتاج إلى تكرار الحلقة عبر السلاسل مرة أخرى إذا أضفت سلسلة أخرى لاحقًا في الشيفرة؟**  
A: نعم — كل `ChartSeries` يمتلك كائن `DataLabels` خاص به، لذا أي سلسلة تُضاف بعد الحلقة الأولية يجب أن تُعيّن لها `HasDataLabels` و`ShowValue` وخصائص الخط، إما عبر تكرار الحلقة مرة أخرى أو باستخراج التنسيق إلى طريقة مساعدة.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}