---
title: إنشاء جدول نص مائل في مستند Word باستخدام Aspose.Words for .NET
weight: 110
limit:
description: تعلم بناء جدول Word بأعمدة ذات عرض ثابت، نص مائل، ارتفاعات صفوف دقيقة، وخلايا مُعبأة باستخدام Aspose.Words for .NET.
keywords: [Aspose.Words for .NET, rotated text table, fixed column widths, vertical alignment Aspose.Words, set row height Word, populate table cells .NET]
url: /net/add-content-using-documentbuilder/create-rotated-text-table/
date: '2026-09-16'
lastmod: '2026-09-16'
schemas:
- author: Aspose
  dateModified: '2026-09-16'
  description: تعلم بناء جدول Word بأعمدة ذات عرض ثابت، نص مائل، ارتفاعات صفوف دقيقة،
    وخلايا مُعبأة باستخدام Aspose.Words for .NET.
  headline: إنشاء جدول نص مائل في مستند Word باستخدام Aspose.Words for .NET
  type: TechArticle
- description: تعلم بناء جدول Word بأعمدة ذات عرض ثابت، نص مائل، ارتفاعات صفوف دقيقة،
    وخلايا مُعبأة باستخدام Aspose.Words for .NET.
  name: إنشاء جدول نص مائل في مستند Word باستخدام Aspose.Words for .NET
  steps:
  - name: إنشاء كائن Document جديد وDocumentBuilder سيُستخدمان لبناء الجدول.
    text: إنشاء كائن Document جديد وDocumentBuilder سيُستخدمان لبناء الجدول.
  - name: ابدأ جدولًا جديدًا، أدخل الخلية الأولى، وثبت عرض الأعمدة بحيث لا يتم تعديلها
      تلقائيًا.
    text: ابدأ جدولًا جديدًا، أدخل الخلية الأولى، وثبت عرض الأعمدة بحيث لا يتم تعديلها
      تلقائيًا.
  - name: محاذاة المحتوى عموديًا في الخلية الحالية إلى الوسط، واكتب نص الخلية الأولى
      للصف الأول.
    text: محاذاة المحتوى عموديًا في الخلية الحالية إلى الوسط، واكتب نص الخلية الأولى
      للصف الأول.
  - name: أدرج الخلية الثانية للصف الأول واكتب نصها.
    text: أدرج الخلية الثانية للصف الأول واكتب نصها.
  - name: أغلق الصف الأول، مُكملًا تخطيطه.
    text: أغلق الصف الأول، مُكملًا تخطيطه.
  - name: ابدأ الخلية الأولى للصف الثاني، عيّن ارتفاع الصف إلى 100 نقطة بالضبط، دوّر
      النص إلى الأعلى، واكتب نص الخلية.
    text: ابدأ الخلية الأولى للصف الثاني، عيّن ارتفاع الصف إلى 100 نقطة بالضبط، دوّر
      النص إلى الأعلى، واكتب نص الخلية.
  - name: أدرج الخلية الثانية للصف الثاني، دوّر نصها إلى الأسفل، واكتب نص الخلية.
    text: أدرج الخلية الثانية للصف الثاني، دوّر نصها إلى الأسفل، واكتب نص الخلية.
  - name: أغلق الصف الثاني، مكملًا السطر الثاني للجدول.
    text: أغلق الصف الثاني، مكملًا السطر الثاني للجدول.
  - name: أنهِ بناء الجدول، مُغلقًا هيكله.
    text: أنهِ بناء الجدول، مُغلقًا هيكله.
  - name: احفظ المستند المكتمل كملف .docx.
    text: احفظ المستند المكتمل كملف .docx.
  type: HowTo
- questions:
  - answer: بعد تثبيت عرض الأعمدة، عيّن عرضًا لكل خلية باستخدام `builder.CellFormat.Width
      = <valueInPoints>;` قبل إدراج الخلية التالية؛ سيحافظ الجدول على تلك العروض الدقيقة.
    question: كيف يمكنني تعيين عرض أعمدة محدد بعد استدعاء `table.AutoFit(AutoFitBehavior.FixedColumnWidths)`؟
  - answer: '`builder.CellFormat.VerticalAlignment` هو إعداد على مستوى الخلية، لذا
      عليك تعيينه مرة أخرى للخلايا في الصف الثاني (مثال: `builder.CellFormat.VerticalAlignment
      = CellVerticalAlignment.Center;`) قبل كتابة محتواها.'
    question: لماذا تؤثر المحاذاة العمودية فقط على الصف الأول ولا تؤثر على الصف الثاني؟
  - answer: نعم—عيّن `builder.RowFormat.Height` و`builder.RowFormat.HeightRule = HeightRule.Exactly`
      قبل كل استدعاء لـ `builder.EndRow();`؛ يمكن للصف التالي أن يكون له قيمة ارتفاع
      مختلفة.
    question: هل يمكنني إعطاء كل صف ارتفاعًا دقيقًا مختلفًا، وإذا كان الجواب نعم،
      كيف؟
  - answer: أعد تعيين التوجيه بتعيين `builder.CellFormat.Orientation = TextOrientation.Horizontal;`
      قبل الكتابة إلى الخلية التالية.
    question: كيف أُعيد توجيه النص إلى الوضع الافتراضي بعد استخدام `TextOrientation.Upward`
      أو `Downward`؟
  type: FAQPage
images:
- /net/add-content-using-documentbuilder/create-rotated-text-table/og-image.png
og_title: إنشاء جدول نص مائل في Word باستخدام Aspose.Words
og_description: كود خطوة بخطوة لبناء جدول بعرض ثابت مع نص مائل عموديًا وارتفاعات صفوف دقيقة.
og_image_alt: لقطة شاشة تُظهر مستند Word يحتوي على جدول بأعمدة ذات عرض ثابت، نص مائل في الخلايا، وارتفاعات صفوف محددة، تم إنشاؤه باستخدام Aspose.Words for .NET
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# إنشاء جدول نص مائل في مستند Word باستخدام Aspose.Words
يوضح هذا البرنامج التعليمي كيفية إنشاء مستند Word وإضافة جدول تكون أعمدته ذات عرض ثابت، وصفوفه ذات ارتفاعات دقيقة، والنص داخل الخلايا مائل عموديًا. ستتعلم ضبط المحاذاة العمودية، تطبيق توجيه النص، ملء كل خلية بالمحتوى، وأخيرًا حفظ المستند — كل ذلك باستخدام Aspose.Words for .NET.

---

{{< tutorial-widget sourcePath="words/net/add-content-using-documentbuilder/create-rotated-text-table" >}}


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
   ```

4. Apply License (Optional):
   To use the full version, [apply a license](https://purchase.aspose.com/temporary-license/) or use a [free trial](https://releases.aspose.com/).

## Also See
[Aspose.Words for .NET Documentation](https://docs.aspose.com/words/net/)
[Aspose.Words for .NET References](https://reference.aspose.com/words/net/)

## Frequently asked questions

**Q: كيف يمكنني تعيين عرض أعمدة محدد بعد استدعاء `table.AutoFit(AutoFitBehavior.FixedColumnWidths)`؟**  
A: بعد تثبيت عرض الأعمدة، عيّن عرضًا لكل خلية باستخدام `builder.CellFormat.Width = <valueInPoints>;` قبل إدراج الخلية التالية؛ سيحافظ الجدول على تلك العروض الدقيقة.

**Q: لماذا تؤثر المحاذاة العمودية فقط على الصف الأول ولا تؤثر على الصف الثاني؟**  
A: `builder.CellFormat.VerticalAlignment` هو إعداد على مستوى الخلية، لذا عليك تعيينه مرة أخرى للخلايا في الصف الثاني (مثال: `builder.CellFormat.VerticalAlignment = CellVerticalAlignment.Center;`) قبل كتابة محتواها.

**Q: هل يمكنني إعطاء كل صف ارتفاعًا دقيقًا مختلفًا، وإذا كان الجواب نعم، كيف؟**  
A: نعم—عيّن `builder.RowFormat.Height` و`builder.RowFormat.HeightRule = HeightRule.Exactly` قبل كل استدعاء لـ `builder.EndRow();`؛ يمكن للصف التالي أن يكون له قيمة ارتفاع مختلفة.

**Q: كيف أُعيد توجيه النص إلى الوضع الافتراضي بعد استخدام `TextOrientation.Upward` أو `Downward`؟**  
A: أعد تعيين التوجيه بتعيين `builder.CellFormat.Orientation = TextOrientation.Horizontal;` قبل الكتابة إلى الخلية التالية.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}