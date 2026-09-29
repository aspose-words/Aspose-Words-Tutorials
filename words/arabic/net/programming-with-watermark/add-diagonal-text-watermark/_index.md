---
title: إنشاء علامة مائية نصية قطرية بخط مخصص في مستند Word باستخدام Aspose.Words for .NET
weight: 210
limit:
description: شفرة خطوة بخطوة لإضافة علامة مائية نصية قطرية بخط مخصص إلى ملف Word .docx باستخدام Aspose.Words for .NET.
keywords: [Aspose.Words for .NET, diagonal text watermark, custom font watermark, Word document watermark, Document.Watermark.SetText, C# watermark API]
url: /net/programming-with-watermark/add-diagonal-text-watermark/
date: '2026-09-29'
lastmod: '2026-09-29'
schemas:
- author: Aspose
  dateModified: '2026-09-29'
  description: شفرة خطوة بخطوة لإضافة علامة مائية نصية قطرية بخط مخصص إلى ملف Word
    .docx باستخدام Aspose.Words for .NET.
  headline: إنشاء علامة مائية نصية قطرية بخط مخصص في مستند Word باستخدام Aspose.Words
    for .NET
  type: TechArticle
- description: شفرة خطوة بخطوة لإضافة علامة مائية نصية قطرية بخط مخصص إلى ملف Word
    .docx باستخدام Aspose.Words for .NET.
  name: إنشاء علامة مائية نصية قطرية بخط مخصص في مستند Word باستخدام Aspose.Words
    for .NET
  steps:
  - name: أنشئ مثيلاً جديداً فارغاً لمستند Word باسم `document`.
    text: أنشئ مثيلاً جديداً فارغاً لمستند Word باسم `document`.
  - name: قم بتكوين `watermarkSettings` باستخدام خط Arial بحجم 48 نقطة ولون رمادي،
      وتخطيط قطري، وعرض غير شفاف.
    text: قم بتكوين `watermarkSettings` باستخدام خط Arial بحجم 48 نقطة ولون رمادي،
      وتخطيط قطري، وعرض غير شفاف.
  - name: طبق العلامة المائية النصية \"Private\" على `document` باستخدام الإعدادات
      المحددة مسبقاً.
    text: طبق العلامة المائية النصية \"Private\" على `document` باستخدام الإعدادات
      المحددة مسبقاً.
  - name: حدد مسار الملف الذي سيتم حفظ المستند المائي عليه.
    text: حدد مسار الملف الذي سيتم حفظ المستند المائي عليه.
  - name: احفظ الـ `document` المعدل إلى المسار المحدد كملف .docx.
    text: احفظ الـ `document` المعدل إلى المسار المحدد كملف .docx.
  type: HowTo
- questions:
  - answer: '`IsSemitrasparent` يحدد ما إذا كانت العلامة المائية تُعرض بشفافية جزئية؛
      ضبطه على `false` يجعل العلامة مائية غير شفافة تماماً، بينما `true` يطبق تأثير
      نصف شفاف افتراضي.'
    question: ما الذي يتحكم فيه علم **IsSemitrasparent** في `TextWatermarkOptions`؟
  - answer: نعم—قم بتعيين خاصية `Layout` إلى `WatermarkLayout.Horizontal` (أو قيمة
      تعداد أخرى) قبل استدعاء `document.Watermark.SetText`.
    question: هل يمكنني تغيير اتجاه العلامة المائية إلى أفقي بدلاً من القطري؟
  - answer: سيتراجع Word إلى الخط الافتراضي للعلامة المائية، لذا سيظهر النص لكن قد
      يختلف مظهره عن النمط المقصود.
    question: ماذا يحدث إذا لم يكن الخط المحدد في `FontFamily` (مثلاً \"Arial\") مثبتاً
      على الجهاز المستهدف؟
  - answer: حمّل الملف الموجود باستخدام `Document document = new Document(\"Existing.docx\");`
      ثم قم بتكوين `TextWatermarkOptions` واستدعِ `document.Watermark.SetText` كما
      هو موضح.
    question: هل يمكن إضافة علامة مائية إلى ملف `.docx` موجود بدلاً من إنشاء ملف جديد؟
  type: FAQPage
images:
- /net/programming-with-watermark/add-diagonal-text-watermark/og-image.png
og_title: إضافة علامة مائية نصية قطرية بخط مخصص
og_description: تعلم كيفية تضمين علامة مائية نصية مائلة بخطك الخاص داخل ملف Word خلال دقائق.
og_image_alt: دليل يوضح كيفية إضافة علامة مائية نصية قطرية بخط مخصص إلى مستند Word باستخدام Aspose.Words for .NET
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# إنشاء علامة مائية نصية قطرية بخط مخصص في مستند Word باستخدام Aspose.Words
يأخذك هذا البرنامج التعليمي خطوة بخطوة عبر إنشاء مستند Word جديد، وتكوين علامة مائية نصية قطرية باستخدام إعدادات الخط التي تختارها، وتطبيقها عبر واجهة برمجة التطبيقات Document.Watermark.SetText، ثم حفظ النتيجة كملف .docx. في النهاية ستحصل على مستند مائي بشكل احترافي يُظهر علامتك التجارية أو ملكيتك. الشيفرة التفصيلية جاهزة للنسخ إلى أي مشروع .NET.

---

{{< tutorial-widget sourcePath="words/net/programming-with-watermark/add-diagonal-text-watermark" >}}


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

**Q: ما الذي يتحكم فيه علم **IsSemitrasparent** في `TextWatermarkOptions`؟**  
A: `IsSemitrasparent` يحدد ما إذا كانت العلامة المائية تُعرض بشفافية جزئية؛ ضبطه على `false` يجعل العلامة مائية غير شفافة تماماً، بينما `true` يطبق تأثير نصف شفاف افتراضي.

**Q: هل يمكنني تغيير اتجاه العلامة المائية إلى أفقي بدلاً من القطري؟**  
A: نعم—قم بتعيين خاصية `Layout` إلى `WatermarkLayout.Horizontal` (أو قيمة تعداد أخرى) قبل استدعاء `document.Watermark.SetText`.

**Q: ماذا يحدث إذا لم يكن الخط المحدد في `FontFamily` (مثلاً \"Arial\") مثبتاً على الجهاز المستهدف؟**  
A: سيتراجع Word إلى الخط الافتراضي للعلامة المائية، لذا سيظهر النص لكن قد يختلف مظهره عن النمط المقصود.

**Q: هل يمكن إضافة علامة مائية إلى ملف `.docx` موجود بدلاً من إنشاء ملف جديد؟**  
A: حمّل الملف الموجود باستخدام `Document document = new Document(\"Existing.docx\");` ثم قم بتكوين `TextWatermarkOptions` واستدعِ `document.Watermark.SetText` كما هو موضح.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}