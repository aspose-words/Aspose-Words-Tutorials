---
title: إضافة أرقام صفحات إلى تذييل مستند Word باستخدام Aspose.Words for .NET
weight: 210
limit:
description: أضف أرقام صفحات تُحدَّث تلقائيًا إلى التذييل الأساسي لمستند Word باستخدام Aspose.Words for .NET.
keywords: [Aspose.Words for .NET, add page numbers, word document footer, documentbuilder page numbers, automatic page numbering, c# aspose.words]
url: /net/working-with-headers-and-footers/add-page-numbers/
date: '2026-09-22'
lastmod: '2026-09-22'
schemas:
- author: Aspose
  dateModified: '2026-09-22'
  description: أضف أرقام صفحات تُحدَّث تلقائيًا إلى التذييل الأساسي لمستند Word باستخدام
    Aspose.Words for .NET.
  headline: إضافة أرقام صفحات إلى تذييل مستند Word باستخدام Aspose.Words for .NET
  type: TechArticle
- description: أضف أرقام صفحات تُحدَّث تلقائيًا إلى التذييل الأساسي لمستند Word باستخدام
    Aspose.Words for .NET.
  name: إضافة أرقام صفحات إلى تذييل مستند Word باستخدام Aspose.Words for .NET
  steps:
  - name: أنشئ كائن Document جديدًا و DocumentBuilder مرتبطًا به.
    text: أنشئ كائن Document جديدًا و DocumentBuilder مرتبطًا به.
  - name: انقل مؤشر الـ builder إلى التذييل الأساسي للقسم الأول.
    text: انقل مؤشر الـ builder إلى التذييل الأساسي للقسم الأول.
  - name: عيّن محاذاة الفقرة إلى الوسط حتى يُوسَّط نص التذييل.
    text: عيّن محاذاة الفقرة إلى الوسط حتى يُوسَّط نص التذييل.
  - name: اكتب العلامة "Page " وأدرج حقل PAGE الذي يعرض رقم الصفحة الحالي.
    text: اكتب العلامة "Page " وأدرج حقل PAGE الذي يعرض رقم الصفحة الحالي.
  - name: اكتب " of " وأدرج حقل NUMPAGES الذي يُظهر إجمالي عدد الصفحات.
    text: اكتب " of " وأدرج حقل NUMPAGES الذي يُظهر إجمالي عدد الصفحات.
  - name: احفظ المستند كملف .docx.
    text: احفظ المستند كملف .docx.
  type: HowTo
- questions:
  - answer: لا. `MoveToHeaderFooter(HeaderFooterType.FooterPrimary)` ينقل الـ builder
      فقط إلى التذييل الأساسي *للقسم الأول*، لذا تُدرج الحقول هناك فقط.
    question: إذا كان المستند يحتوي على أكثر من قسم، هل سيضيف هذا الكود أرقام الصفحات
      إلى تذييل كل قسم؟
  - answer: عيّن `builder.ParagraphFormat.Alignment` إلى قيمة `ParagraphAlignment`
      أخرى (مثلاً `ParagraphAlignment.Right`) قبل كتابة الحقول.
    question: كيف يمكنني تغيير محاذاة فقرة رقم الصفحة في التذييل؟
  - answer: '`InsertField` يأخذ رمز الحقل ونتيجة اختيارية؛ تمرير `null` يُخبر Aspose.Words
      بأن يترك Word يحسب النتيجة أثناء التشغيل.'
    question: ماذا يمثل الوسيط `null` في `InsertField("PAGE", null)`؟
  - answer: نعم—استبدل `HeaderFooterType.FooterPrimary` بـ `HeaderFooterType.HeaderPrimary`
      (أو نوع ترويسة آخر) قبل إدراج الحقول.
    question: هل يمكنني وضع حقول "Page X of Y" نفسها في الترويسة بدلاً من التذييل؟
  type: FAQPage
images:
- /net/working-with-headers-and-footers/add-page-numbers/og-image.png
og_title: إدراج أرقام صفحات تلقائية في تذييل Word
og_description: كود خطوة بخطوة لإضافة أرقام صفحات حية إلى تذييل Word باستخدام Aspose.Words for .NET.
og_image_alt: دليل يوضح كيفية إضافة أرقام صفحات تلقائية إلى تذييل مستند Word باستخدام Aspose.Words for .NET
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# إضافة أرقام صفحات إلى تذييل مستند Word باستخدام Aspose.Words
يوضح هذا البرنامج التعليمي كيفية استخدام Aspose.Words Document و DocumentBuilder لإدراج أرقام صفحات تُحدَّث تلقائيًا في التذييل الأساسي لمستند Word. من خلال إضافة أرقام الصفحات برمجيًا، تضمن ترقيمًا ثابتًا عبر الملف بأكمله دون تعديل يدوي. الكود المثال جاهز للتنفيذ في بيئة .NET.

---

{{< tutorial-widget sourcePath="words/net/working-with-headers-and-footers/add-page-numbers" >}}


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
   using System.Drawing;
   ```

4. Apply License (Optional):
   To use the full version, [apply a license](https://purchase.aspose.com/temporary-license/) or use a [free trial](https://releases.aspose.com/).

## Also See
[Aspose.Words for .NET Documentation](https://docs.aspose.com/words/net/)
[Aspose.Words for .NET References](https://reference.aspose.com/words/net/)

## Frequently asked questions

**Q: إذا كان المستند يحتوي على أكثر من قسم، هل سيضيف هذا الكود أرقام الصفحات إلى تذييل كل قسم؟**  
A: لا. `MoveToHeaderFooter(HeaderFooterType.FooterPrimary)` ينقل الـ builder فقط إلى التذييل الأساسي *للقسم الأول*، لذا تُدرج الحقول هناك فقط.

**Q: كيف يمكنني تغيير محاذاة فقرة رقم الصفحة في التذييل؟**  
A: عيّن `builder.ParagraphFormat.Alignment` إلى قيمة `ParagraphAlignment` أخرى (مثلاً `ParagraphAlignment.Right`) قبل كتابة الحقول.

**Q: ماذا يمثل الوسيط `null` في `InsertField("PAGE", null)`؟**  
A: `InsertField` يأخذ رمز الحقل ونتيجة اختيارية؛ تمرير `null` يُخبر Aspose.Words بأن يترك Word يحسب النتيجة أثناء التشغيل.

**Q: هل يمكنني وضع حقول "Page X of Y" نفسها في الترويسة بدلاً من التذييل؟**  
A: نعم—استبدل `HeaderFooterType.FooterPrimary` بـ `HeaderFooterType.HeaderPrimary` (أو نوع ترويسة آخر) قبل إدراج الحقول.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}