---
title: إخفاء حد مساحة الرسم في مخطط عمودي باستخدام Aspose.Words for .NET
weight: 410
limit:
description: تعلم كيفية إخفاء حد مساحة الرسم للمخطط مع إبقاء خطوط المحاور مرئية في مخطط عمودي في Word باستخدام Aspose.Words for .NET.
keywords: [aspose.words for .net, hide plot border, column chart, chart formatting, word document chart, plot area border removal]
url: /net/programming-with-charts/hide-plot-border/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: تعلم كيفية إخفاء حد مساحة الرسم للمخطط مع إبقاء خطوط المحاور مرئية
    في مخطط عمودي في Word باستخدام Aspose.Words for .NET.
  headline: إخفاء حد مساحة الرسم في مخطط عمودي باستخدام Aspose.Words for .NET
  type: TechArticle
- description: تعلم كيفية إخفاء حد مساحة الرسم للمخطط مع إبقاء خطوط المحاور مرئية
    في مخطط عمودي في Word باستخدام Aspose.Words for .NET.
  name: إخفاء حد مساحة الرسم في مخطط عمودي باستخدام Aspose.Words for .NET
  steps:
  - name: أنشئ مستند Word فارغًا جديدًا وDocumentBuilder لتعديله.
    text: أنشئ مستند Word فارغًا جديدًا وDocumentBuilder لتعديله.
  - name: أدرج مخططًا عموديًا بحجم 432×252 في المستند واحصل على كائن Chart الخاص به.
    text: أدرج مخططًا عموديًا بحجم 432×252 في المستند واحصل على كائن Chart الخاص به.
  - name: امسح أي سلاسل موجودة، عرّف ثلاث تسميات فئات، وأضف سلسلة بقيم عينة إلى المخطط.
    text: امسح أي سلاسل موجودة، عرّف ثلاث تسميات فئات، وأضف سلسلة بقيم عينة إلى المخطط.
  - name: عيّن وزن حد مساحة الرسم إلى صفر، مما يزيل حدها مع إبقاء خطوط المحاور مرئية.
    text: عيّن وزن حد مساحة الرسم إلى صفر، مما يزيل حدها مع إبقاء خطوط المحاور مرئية.
  - name: احفظ المستند المعدل كملف .docx.
    text: احفظ المستند المعدل كملف .docx.
  type: HowTo
- questions:
  - answer: خاصية `Stroke` تنتمي إلى تنسيق الكائن `Chart` العام، الذي يرسم الحد المستطيل
      حول مساحة الرسم؛ خطوط المحاور هي كائنات `Axis` منفصلة ولا تتأثر بإعدادات `Stroke`
      للمخطط.
    question: لماذا يؤدي ضبط `columnChart.Format.Stroke.Weight = 0` إلى إزالة حد مساحة
      الرسم مع ترك خطوط المحاور مرئية؟
  - answer: لا، خاصية `Stroke` تتحكم في كامل حد مساحة الرسم كمتواسط واحد، لذا لا يمكن
      إخفاء حدود جزئية عبر Aspose.Words؛ سيتعين عليك إضافة أشكال مخصصة أو تعديل المخطط
      يدويًا.
    question: هل يمكنني إخفاء جانب واحد فقط من حد مساحة الرسم (مثل الجانب الأيسر)
      مع إبقاء الجوانب الثلاثة الأخرى مرئية؟
  - answer: نعم، خاصية `Stroke` مستقلة عن `ChartType`، لذا ضبط `Weight` إلى 0 يزيل
      حد مساحة الرسم للمخططات الخطية، الفطيرة، أو أي نوع مخطط مدعوم آخر.
    question: إذا غيرت نوع المخطط إلى خط أو فطيرة، هل سيظل `columnChart.Format.Stroke.Weight
      = 0` يزيل حد مساحة الرسم؟
  - answer: لا يلزم أي تحديث إضافي؛ مسح السلاسل وإضافة سلسلة جديدة يحدث المخطط داخليًا،
      و`wordDoc.Save(...)` يكتب الحالة الحالية إلى ملف .docx.
    question: بعد استدعاء `columnChart.Series.Clear()`، هل أحتاج إلى تحديث المخطط
      قبل حفظ المستند؟
  type: FAQPage
images:
- /net/programming-with-charts/hide-plot-border/og-image.png
og_title: إخفاء حد الرسم في مخطط عمودي في Word
og_description: أزل حد مساحة الرسم مع إبقاء خطوط المحاور مرئية في مخطط عمودي في Word باستخدام Aspose.Words for .NET.
og_image_alt: دليل يوضح مستند Word يحتوي على مخطط عمودي حيث تم إخفاء حد مساحة الرسم لكن خطوط المحاور تظل مرئية باستخدام Aspose.Words for .NET.
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# إخفاء حد مساحة الرسم في مخطط عمودي باستخدام Aspose.Words
في هذا البرنامج التعليمي ستتعلم كيفية إنشاء مستند Word، وإدراج مخطط عمودي، وتعبئته ببيانات عينة، ثم إخفاء حد مساحة الرسم للمخطط مع إبقاء خطوط المحاور مرئية. يوضح الكود خطوة بخطوة كل عملية وينتهي بحفظ المستند، حتى تتمكن من رؤية النتيجة فورًا.

---

{{< tutorial-widget sourcePath="words/net/programming-with-charts/hide-plot-border" >}}


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

**Q: لماذا يؤدي ضبط `columnChart.Format.Stroke.Weight = 0` إلى إزالة حد مساحة الرسم مع ترك خطوط المحاور مرئية؟**  
A: خاصية `Stroke` تنتمي إلى تنسيق الكائن `Chart` العام، الذي يرسم الحد المستطيل حول مساحة الرسم؛ خطوط المحاور هي كائنات `Axis` منفصلة ولا تتأثر بإعدادات `Stroke` للمخطط.

**Q: هل يمكنني إخفاء جانب واحد فقط من حد مساحة الرسم (مثل الجانب الأيسر) مع إبقاء الجوانب الثلاثة الأخرى مرئية؟**  
A: لا، خاصية `Stroke` تتحكم في كامل حد مساحة الرسم كمتواسط واحد، لذا لا يمكن إخفاء حدود جزئية عبر Aspose.Words؛ سيتعين عليك إضافة أشكال مخصصة أو تعديل المخطط يدويًا.

**Q: إذا غيرت نوع المخطط إلى خط أو فطيرة، هل سيظل `columnChart.Format.Stroke.Weight = 0` يزيل حد مساحة الرسم؟**  
A: نعم، خاصية `Stroke` مستقلة عن `ChartType`، لذا ضبط `Weight` إلى 0 يزيل حد مساحة الرسم للمخططات الخطية، الفطيرة، أو أي نوع مخطط مدعوم آخر.

**Q: بعد استدعاء `columnChart.Series.Clear()`، هل أحتاج إلى تحديث المخطط قبل حفظ المستند؟**  
A: لا يلزم أي تحديث إضافي؛ مسح السلاسل وإضافة سلسلة جديدة يحدث المخطط داخليًا، و`wordDoc.Save(...)` يكتب الحالة الحالية إلى ملف .docx.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}