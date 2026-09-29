---
title: إدراج باركود DataMatrix في مستند Word باستخدام Aspose.Words for .NET
weight: 210
limit:
description: أضف باركود DataMatrix إلى مستند Word برمجيًا باستخدام Aspose.Words for .NET.
keywords: [Aspose.Words for .NET, datamatrix barcode, displaybarcode field, documentbuilder barcode, word document barcode, insert barcode .net]
url: /net/working-with-fields/insert-datamatrix-barcode/
date: '2026-09-29'
lastmod: '2026-09-29'
schemas:
- author: Aspose
  dateModified: '2026-09-29'
  description: أضف باركود DataMatrix إلى مستند Word برمجيًا باستخدام Aspose.Words
    for .NET.
  headline: إدراج باركود DataMatrix في مستند Word باستخدام Aspose.Words for .NET
  type: TechArticle
- description: أضف باركود DataMatrix إلى مستند Word برمجيًا باستخدام Aspose.Words
    for .NET.
  name: إدراج باركود DataMatrix في مستند Word باستخدام Aspose.Words for .NET
  steps:
  - name: أنشئ مستند Word فارغًا جديدًا وDocumentBuilder لتعديله.
    text: أنشئ مستند Word فارغًا جديدًا وDocumentBuilder لتعديله.
  - name: أدرج حقل DISPLAYBARCODE في موضع المؤشر الحالي، مما يضيف عنصرًا نائبًا للحقل
      إلى المستند.
    text: أدرج حقل DISPLAYBARCODE في موضع المؤشر الحالي، مما يضيف عنصرًا نائبًا للحقل
      إلى المستند.
  - name: عيّن BarcodeType الخاص بالحقل إلى DataMatrix وقدم سلسلة البيانات لتشفيرها.
    text: عيّن BarcodeType الخاص بالحقل إلى DataMatrix وقدم سلسلة البيانات لتشفيرها.
  - name: يمكنك اختيارياً تحديد ألوان الخلفية والواجهة للباركود.
    text: يمكنك اختيارياً تحديد ألوان الخلفية والواجهة للباركود.
  - name: استدعِ UpdateFields على المستند لعرض صورة الباركود داخل الحقل.
    text: استدعِ UpdateFields على المستند لعرض صورة الباركود داخل الحقل.
  - name: احفظ المستند كملف .docx.
    text: احفظ المستند كملف .docx.
  type: HowTo
- questions:
  - answer: سيتم إدراج الحقل، لكن `document.UpdateFields()` سيترك الباركود فارغًا
      وستطلق Aspose.Words استثناءً من نوع `FieldException` يشير إلى نوع باركود غير
      صالح.
    question: ماذا يحدث إذا قمت بتعيين قيمة غير مدعومة إلى `displayBarcodeField.BarcodeType`؟
  - answer: '`UpdateFields()` يعرض صور الباركود، لذا يمكنك إدراج عدة كائنات `FieldDisplayBarcode`
      واستدعاء `document.UpdateFields()` مرة واحدة في النهاية لعرضها جميعًا.'
    question: هل يجب علي استدعاء `document.UpdateFields()` بعد كل إدراج للباركود،
      أم يمكنني التحديث مرة واحدة بعد إضافة جميع الحقول؟
  - answer: 'كلتا الخاصيتين تتوقعان سلسلة RGB سداسية عشرية مسبوقة بـ `0x` (مثال: "0xFF0000"
      للون الأحمر)؛ أي تنسيق آخر سيتجاهل وسيتم استخدام الألوان الافتراضية.'
    question: ما هو التنسيق الذي يجب أن تكون عليه سلاسل الألوان لـ `BackgroundColor`
      و `ForegroundColor`؟
  - answer: نعم—ما عليك سوى تعيين `displayBarcodeField.BarcodeValue` إلى سلسلة جديدة
      واستدعاء `document.UpdateFields()` مرة أخرى لتحديث الصورة المعروضة.
    question: هل يمكنني تغيير محتوى الباركود بعد إدراج الحقل؟
  type: FAQPage
images:
- /net/working-with-fields/insert-datamatrix-barcode/og-image.png
og_title: إدراج باركود DataMatrix باستخدام Aspose.Words
og_description: تعلم كيفية إضافة باركود DataMatrix إلى ملف Word ببضع أسطر فقط من كود .NET.
og_image_alt: دليل يوضح كيفية إدراج وعرض باركود DataMatrix في مستند Word باستخدام Aspose.Words for .NET
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# إدراج باركود DataMatrix في مستند Word باستخدام Aspose.Words
مع Aspose.Words for .NET يمكنك إضافة باركود DataMatrix إلى مستند Word برمجيًا. يوضح هذا البرنامج التعليمي كيفية إنشاء مستند جديد، وإدراج حقل DISPLAYBARCODE، وتعيين نوعه إلى DataMatrix، وعرض صورة الباركود باستخدام فئتي Document وDocumentBuilder. اتبع الخطوات لإنشاء باركود قابل للطباعة مباشرة داخل ملف .docx الخاص بك.

---

{{< tutorial-widget sourcePath="words/net/working-with-fields/insert-datamatrix-barcode" >}}


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

**Q: ماذا يحدث إذا قمت بتعيين قيمة غير مدعومة إلى `displayBarcodeField.BarcodeType`؟**  
A: سيتم إدراج الحقل، لكن `document.UpdateFields()` سيترك الباركود فارغًا وستطلق Aspose.Words استثناءً من نوع `FieldException` يشير إلى نوع باركود غير صالح.

**Q: هل يجب علي استدعاء `document.UpdateFields()` بعد كل إدراج للباركود، أم يمكنني التحديث مرة واحدة بعد إضافة جميع الحقول؟**  
A: `UpdateFields()` يعرض صور الباركود، لذا يمكنك إدراج عدة كائنات `FieldDisplayBarcode` واستدعاء `document.UpdateFields()` مرة واحدة في النهاية لعرضها جميعًا.

**Q: ما هو التنسيق الذي يجب أن تكون عليه سلاسل الألوان لـ `BackgroundColor` و `ForegroundColor`؟**  
A: كلتا الخاصيتين تتوقعان سلسلة RGB سداسية عشرية مسبوقة بـ `0x` (مثال: "0xFF0000" للون الأحمر)؛ أي تنسيق آخر سيتجاهل وسيتم استخدام الألوان الافتراضية.

**Q: هل يمكنني تغيير محتوى الباركود بعد إدراج الحقل؟**  
A: نعم—ما عليك سوى تعيين `displayBarcodeField.BarcodeValue` إلى سلسلة جديدة واستدعاء `document.UpdateFields()` مرة أخرى لتحديث الصورة المعروضة.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}