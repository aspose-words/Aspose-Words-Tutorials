---
title: تخصيص خطوط شبكة المحور X في مخطط عمودي باستخدام Aspose.Words for .NET
weight: 610
limit:
description: تعلم إضافة وتخصيص لون خطوط الشبكة الرئيسية للمحور X في مخطط عمودي Word باستخدام Aspose.Words for .NET.
keywords: [Aspose.Words for .NET, column chart, customize x axis gridlines, word chart gridlines, primary x axis gridlines, chart formatting .NET]
url: /net/programming-with-charts/customize-x-axis-gridlines/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: تعلم إضافة وتخصيص لون خطوط الشبكة الرئيسية للمحور X في مخطط عمودي Word
    باستخدام Aspose.Words for .NET.
  headline: تخصيص خطوط شبكة المحور X في مخطط عمودي باستخدام Aspose.Words for .NET
  type: TechArticle
- description: تعلم إضافة وتخصيص لون خطوط الشبكة الرئيسية للمحور X في مخطط عمودي Word
    باستخدام Aspose.Words for .NET.
  name: تخصيص خطوط شبكة المحور X في مخطط عمودي باستخدام Aspose.Words for .NET
  steps:
  - name: أنشئ مستند Word جديدًا وDocumentBuilder لتعديله.
    text: أنشئ مستند Word جديدًا وDocumentBuilder لتعديله.
  - name: أدرج مخططًا عموديًا بحجم 432×252 في المستند واحصل على كائن Chart الخاص به.
    text: أدرج مخططًا عموديًا بحجم 432×252 في المستند واحصل على كائن Chart الخاص به.
  - name: أزل السلسلة الافتراضية وأضف سلسلة مخصصة تحتوي على ثلاث مجموعات وقيم.
    text: أزل السلسلة الافتراضية وأضف سلسلة مخصصة تحتوي على ثلاث مجموعات وقيم.
  - name: احصل على مرجع إلى المحور الأفقي (X) الأساسي للمخطط.
    text: احصل على مرجع إلى المحور الأفقي (X) الأساسي للمخطط.
  - name: فعّل عرض خطوط الشبكة الرئيسية على المحور X الأساسي.
    text: فعّل عرض خطوط الشبكة الرئيسية على المحور X الأساسي.
  - name: عيّن لون خطوط الشبكة إلى الأزرق وسمكها إلى نقطتين.
    text: عيّن لون خطوط الشبكة إلى الأزرق وسمكها إلى نقطتين.
  - name: احفظ المستند كملف .docx.
    text: احفظ المستند كملف .docx.
  type: HowTo
- questions:
  - answer: 'عيّن خاصية المحور نفسها إلى false: `horizontalAxis.HasMajorGridlines
      = false;` لتبديل رؤية خطوط الشبكة الرئيسية للمحور X.'
    question: كيف يمكنني إخفاء خطوط الشبكة الرئيسية مرة أخرى بعد تمكينها؟
  - answer: لا، إعدادات `Format.Stroke` تنطبق فقط على المحور الذي تقوم بتعديله؛ لتنسيق
      خطوط شبكة المحور Y يجب تعديل `chart.AxisY.Format.Stroke` بشكل منفصل.
    question: هل سيؤثر تغيير `horizontalAxis.Format.Stroke.Color` أيضًا على خطوط شبكة
      المحور Y؟
  - answer: استخدم `horizontalAxis.Format.Stroke.Weight` وعيّن قيمة مزدوجة (مثلاً
      `0.5`) لجعل خطوط الشبكة أرق.
    question: أي خاصية تتحكم في سمك خطوط الشبكة الرئيسية للمحور X؟
  - answer: نعم، عيّن `horizontalAxis.Format.Stroke.DashStyle` إلى قيمة من تعداد `DashStyle`
      مثل `DashStyle.Dash` أو `DashStyle.Dot`.
    question: هل يمكنني تغيير نمط الخط المتقطع لخطوط الشبكة الرئيسية للمحور X؟
  type: FAQPage
images:
- /net/programming-with-charts/customize-x-axis-gridlines/og-image.png
og_title: تنسيق خطوط شبكة المحور X في مخطط عمودي Word
og_description: فعّل وقم بتخصيص لون خطوط شبكة المحور X الأساسي لمخطط Word باستخدام Aspose.Words for .NET.
og_image_alt: دليل يوضح مستند Word يحتوي على مخطط عمودي حيث يتم تمييز خطوط الشبكة الرئيسية للمحور X الأساسي بلون مخصص باستخدام Aspose.Words for .NET.
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# تخصيص خطوط شبكة المحور X في مخطط عمودي باستخدام Aspose.Words
في هذا البرنامج التعليمي ستتعلم كيفية إنشاء مستند Word، وإدراج مخطط عمودي، واستبدال بياناته الافتراضية، ثم تمكين خطوط الشبكة الرئيسية على المحور X الأساسي. ستتعرف أيضًا على كيفية تغيير لون خط خطوط الشبكة ليتطابق مع تصميمك. اتبع الشيفرة خطوة بخطوة للحصول على تحكم دقيق في رؤية وتنسيق خطوط شبكة المحور X.

---

{{< tutorial-widget sourcePath="words/net/programming-with-charts/customize-x-axis-gridlines" >}}


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

**Q: كيف يمكنني إخفاء خطوط الشبكة الرئيسية مرة أخرى بعد تمكينها؟**  
A: عيّن خاصية المحور نفسها إلى false: `horizontalAxis.HasMajorGridlines = false;` لتبديل رؤية خطوط الشبكة الرئيسية للمحور X.

**Q: هل سيؤثر تغيير `horizontalAxis.Format.Stroke.Color` أيضًا على خطوط شبكة المحور Y؟**  
A: لا، إعدادات `Format.Stroke` تنطبق فقط على المحور الذي تقوم بتعديله؛ لتنسيق خطوط شبكة المحور Y يجب تعديل `chart.AxisY.Format.Stroke` بشكل منفصل.

**Q: أي خاصية تتحكم في سمك خطوط الشبكة الرئيسية للمحور X؟**  
A: استخدم `horizontalAxis.Format.Stroke.Weight` وعيّن قيمة مزدوجة (مثلاً `0.5`) لجعل خطوط الشبكة أرق.

**Q: هل يمكنني تغيير نمط الخط المتقطع لخطوط الشبكة الرئيسية للمحور X؟**  
A: نعم، عيّن `horizontalAxis.Format.Stroke.DashStyle` إلى قيمة من تعداد `DashStyle` مثل `DashStyle.Dash` أو `DashStyle.Dot`.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}