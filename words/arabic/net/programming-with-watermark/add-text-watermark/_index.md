---
title: إضافة علامة مائية نصية حمراء مائلة إلى مستندات Word باستخدام Aspose.Words for .NET
weight: 110
limit:
description: تطبيق علامة مائية نصية حمراء مائلة تلقائيًا على كل ملف Word يتم إنشاؤه في دفعة باستخدام Aspose.Words for .NET.
keywords: [Aspose.Words for .NET, text watermark, red diagonal watermark, batch document generation, DocumentBuilder watermark, automated report]
url: /net/programming-with-watermark/add-text-watermark/
date: '2026-09-29'
lastmod: '2026-09-29'
schemas:
- author: Aspose
  dateModified: '2026-09-29'
  description: تطبيق علامة مائية نصية حمراء مائلة تلقائيًا على كل ملف Word يتم إنشاؤه
    في دفعة باستخدام Aspose.Words for .NET.
  headline: إضافة علامة مائية نصية حمراء مائلة إلى مستندات Word باستخدام Aspose.Words
    for .NET
  type: TechArticle
- description: تطبيق علامة مائية نصية حمراء مائلة تلقائيًا على كل ملف Word يتم إنشاؤه
    في دفعة باستخدام Aspose.Words for .NET.
  name: إضافة علامة مائية نصية حمراء مائلة إلى مستندات Word باستخدام Aspose.Words
    for .NET
  steps:
  - name: أنشئ المجلد "GeneratedReports" حيث سيتم حفظ ملفات الإخراج.
    text: أنشئ المجلد "GeneratedReports" حيث سيتم حفظ ملفات الإخراج.
  - name: ابدأ حلقة ستولد ثلاثة مستندات منفصلة.
    text: ابدأ حلقة ستولد ثلاثة مستندات منفصلة.
  - name: أنشئ كائن مستند Word جديد فارغ.
    text: أنشئ كائن مستند Word جديد فارغ.
  - name: استخدم DocumentBuilder لكتابة سطر عنوان ووصف داخل المستند.
    text: استخدم DocumentBuilder لكتابة سطر عنوان ووصف داخل المستند.
  - name: حدد مظهر العلامة المائية، بما في ذلك الخط، الحجم، اللون، وتخطيط القطر.
    text: حدد مظهر العلامة المائية، بما في ذلك الخط، الحجم، اللون، وتخطيط القطر.
  - name: طبق العلامة المائية الحمراء المائلة المُكوَّنة بالنص "PROTECTED" على المستند.
    text: طبق العلامة المائية الحمراء المائلة المُكوَّنة بالنص "PROTECTED" على المستند.
  - name: احفظ المستند المموج بالعلامة المائية في مجلد "GeneratedReports" باسم ملف
      فريد.
    text: احفظ المستند المموج بالعلامة المائية في مجلد "GeneratedReports" باسم ملف
      فريد.
  - name: أغلق الحلقة بعد معالجة المستند الحالي.
    text: أغلق الحلقة بعد معالجة المستند الحالي.
  type: HowTo
- questions:
  - answer: يحدد IsSemitrasparent ما إذا كانت العلامة المائية تُعرض بعتامة جزئية؛
      تعيينه إلى **true** يجعل النص شبه شفاف بحيث يبقى المحتوى الأساسي أكثر قابلية
      للقراءة.
    question: ما الذي يتحكم فيه خيار **IsSemitrasparent** وما هو التأثير عند تعيينه
      إلى **true**؟
  - answer: نعم—قم بتعيين الخاصية **Layout** إلى **WatermarkLayout.Horizontal** في
      **TextWatermarkOptions** قبل استدعاء **document.Watermark.SetText**.
    question: هل يمكنني تغيير اتجاه العلامة المائية إلى أفقي بدلاً من مائل؟
  - answer: 'المقتطف ينشئ كائن **Document** جديد، لكن يمكنك فتح أي ملف موجود (مثال:
      `new Document("Existing.docx")`) ثم استدعاء **document.Watermark.SetText** لتطبيق
      نفس العلامة المائية.'
    question: هل سيضيف هذا الكود علامة مائية إلى ملف Word موجود، أم فقط إلى المستندات
      التي تم إنشاؤها حديثًا؟
  - answer: عيّن لونًا مخصصًا باستخدام **Color.FromArgb(red, green, blue)** إلى الخاصية
      **Color** في **TextWatermarkOptions**، على سبيل المثال، `Color = Color.FromArgb(128,
      0, 128)` للون الأرجواني.
    question: كيف يمكنني استخدام لون RGB مخصص للعلامة المائية بدلاً من **Color.Red**
      المحدد مسبقًا؟
  type: FAQPage
images:
- /net/programming-with-watermark/add-text-watermark/og-image.png
og_title: إضافة علامة مائية نصية حمراء مائلة إلى مستندات Word
og_description: شاهد كيفية تطبيق علامة مائية حمراء مائلة تلقائيًا على كل مستند Word في دفعة باستخدام Aspose.Words.
og_image_alt: دليل يوضح كيفية إضافة علامة مائية نصية حمراء مائلة إلى مستندات Word باستخدام Aspose.Words for .NET
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# إضافة علامة مائية نصية حمراء مائلة إلى مستندات Word باستخدام Aspose.Words
يوضح هذا البرنامج التعليمي كيفية دمج علامة مائية نصية حمراء مائلة تلقائيًا في كل مستند Word يتم إنشاؤه أثناء توليد تقارير دفعة. باستخدام فئتي Document و DocumentBuilder في Aspose.Words for .NET، يتم تطبيق العلامة المائية برمجيًا أثناء إنشاء الملفات، مما يضمن أن يحمل كل مستند نفس العلامة التجارية أو إشعار السرية دون جهد يدوي.

---

{{< tutorial-widget sourcePath="words/net/programming-with-watermark/add-text-watermark" >}}


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

**Q: ما الذي يتحكم فيه خيار **IsSemitrasparent** وما هو التأثير عند تعيينه إلى **true**؟**  
A: يحدد IsSemitrasparent ما إذا كانت العلامة المائية تُعرض بعتامة جزئية؛ تعيينه إلى **true** يجعل النص شبه شفاف بحيث يبقى المحتوى الأساسي أكثر قابلية للقراءة.

**Q: هل يمكنني تغيير اتجاه العلامة المائية إلى أفقي بدلاً من مائل؟**  
A: نعم—قم بتعيين الخاصية **Layout** إلى **WatermarkLayout.Horizontal** في **TextWatermarkOptions** قبل استدعاء **document.Watermark.SetText**.

**Q: هل سيضيف هذا الكود علامة مائية إلى ملف Word موجود، أم فقط إلى المستندات التي تم إنشاؤها حديثًا؟**  
A: المقتطف ينشئ كائن **Document** جديد، لكن يمكنك فتح أي ملف موجود (مثال: `new Document("Existing.docx")`) ثم استدعاء **document.Watermark.SetText** لتطبيق نفس العلامة المائية.

**Q: كيف يمكنني استخدام لون RGB مخصص للعلامة المائية بدلاً من **Color.Red** المحدد مسبقًا؟**  
A: عيّن لونًا مخصصًا باستخدام **Color.FromArgb(red, green, blue)** إلى الخاصية **Color** في **TextWatermarkOptions**، على سبيل المثال، `Color = Color.FromArgb(128, 0, 128)` للون الأرجواني.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}