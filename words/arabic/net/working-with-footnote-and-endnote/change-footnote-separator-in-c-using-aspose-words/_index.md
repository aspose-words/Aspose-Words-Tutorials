---
category: general
date: 2026-08-04
description: تغيير فاصل الحاشية السفلية في C# باستخدام Aspose.Words – تعلّم كيفية
  تعديل فاصل الحاشية السفلية وتغيير فاصل الحاشية الختامية في مستندات Word.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- change footnote separator
- edit footnote separator
- how to change footnote separator
- change endnote separator
language: ar
lastmod: 2026-08-04
og_description: تغيير فاصل الحاشية السفلية في C# باستخدام Aspose.Words. يوضح لك هذا
  الدليل كيفية تعديل فاصل الحاشية السفلية، وتخصيص فاصل الحاشية الختامية، وحفظ المستند
  المحدث.
og_image_alt: Screenshot showing the changed footnote separator in a Word document
og_title: تغيير فاصل الحاشية السفلية في C# – دليل Aspose.Words الكامل
schemas:
- author: Aspose
  dateModified: '2026-08-04'
  description: Change footnote separator in C# using Aspose.Words – learn how to edit
    footnote separator and change endnote separator in Word documents.
  headline: Change footnote separator in C# using Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- C#
- Footnotes
- Document processing
title: تغيير فاصل الحاشية السفلية في C# باستخدام Aspose.Words
url: /ar/net/working-with-footnote-and-endnote/change-footnote-separator-in-c-using-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# تغيير فاصل الحاشية السفلية في C# باستخدام Aspose.Words

إذا كنت بحاجة إلى **تغيير فاصل الحاشية السفلية** في مستند Word، فإن هذا الدليل يوضح لك الخطوات الدقيقة باستخدام Aspose.Words لـ .NET. سواء كنت تريد استبدال الخط الافتراضي برمز، أو تطبيق نمط مختلف على فواصل الحواشي الختامية، فإن الشيفرة أدناه تغطي سير العمل بالكامل.

ستتعلم أيضًا كيفية **تحرير فاصل الحاشية السفلية** والعملية المرتبطة بـ **تغيير فاصل الحاشية الختامية**، بحيث يمكن للمستند نفسه أن يحتوي على تنسيق متسق لكل من الحواشي السفلية والختامية. لا تحتاج إلى أدوات خارجية—فقط بضع أسطر من C#.

## ما ستحققه

بنهاية هذا الدليل ستكون قادرًا على:

* تحميل ملف *.docx* موجود يحتوي على حواشي سفلية وحواشي ختامية.  
* الوصول إلى عقد الفاصل للحواشي السفلية، واستمرار الحواشي، والحواشي الختامية.  
* استبدال حرف الفاصل (مثلاً، تغيير الخط الافتراضي إلى نجمة).  
* حفظ المستند المعدل دون فقدان أي محتوى آخر.  

يفترض الدليل أن لديك فهمًا أساسيًا للغة C# وأنك قد قمت بتثبيت حزمة **Aspose.Words** عبر NuGet (الإصدار 24.9 أو أحدث).  

---

## المتطلبات المسبقة

| المتطلب | السبب |
|-------------|--------|
| .NET 6.0+ أو .NET Framework 4.7.2+ | وقت تشغيل مطلوب لـ Aspose.Words |
| مكتبة Aspose.Words لـ .NET | توفر واجهات `Document` و `FootnoteOptions` |
| ملف Word إدخالي (`input.docx`) يحتوي على حاشية سفلية أو ختامية واحدة على الأقل | يوضح عملية تغيير الفاصل |

يمكنك إضافة Aspose.Words إلى مشروعك باستخدام أمر CLI التالي:

```bash
dotnet add package Aspose.Words --version 24.9.0
```

---

## الخطوة 1: تحميل المستند الذي يحتوي على الحواشي

العملية الأولى هي قراءة الملف المصدر إلى كائن `Document`. يمثل هذا الكائن ملف Word بالكامل في الذاكرة ويمنحك إمكانية الوصول إلى جميع عقده.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Tables;

// Load the .docx file that contains footnotes and endnotes.
Document document = new Document(@"C:\Docs\input.docx");
```

**لماذا هذا مهم:** تحميل المستند هو نقطة الدخول لأي تعديل. إذا تعذر العثور على الملف، فإن Aspose.Words يطرح استثناء `FileNotFoundException`، لذا تأكد من صحة المسار قبل المتابعة.

---

## الخطوة 2: الوصول إلى عقد فاصل الحاشية السفلية والختامية

`Document.FootnoteOptions` يعرّف ثلاث عقد فاصل:

* `Separator` – الخط الذي يظهر بعد مجموعة الحواشي السفلية في الصفحة الأولى.  
* `ContinuationSeparator` – الخط المستخدم عندما تستمر الحواشي السفلية إلى الصفحة التالية.  
* `EndnoteSeparator` – الخط الذي يفصل النص الرئيسي عن قائمة الحواشي الختامية.

تسترجع هذه العقد ككائنات `Node` عامة، ثم تقوم بتحويلها إلى `Run` لتعديل النص.

```csharp
// Retrieve the three separator nodes.
Node footnoteSeparator = document.FootnoteOptions.Separator;
Node footnoteContinuation = document.FootnoteOptions.ContinuationSeparator;
Node endnoteSeparator = document.FootnoteOptions.EndnoteSeparator;
```

**لماذا هذا مهم:** هذه العقد هي الأماكن الوحيدة التي يتواجد فيها حرف الفاصل البصري. تعديل أي عقدة أخرى (مثل فقرة عادية) لن يؤثر على تنسيق الحاشية السفلية.

---

## الخطوة 3: تغيير حرف فاصل الحاشية السفلية

المطلب الأكثر شيوعًا هو استبدال الخط الافتراضي برمز مثل النجمة (`*`). بما أن الفاصل يُخزن كـ `Run`، يمكنك تعديل خاصية `Text` بأمان.

```csharp
// Change the primary footnote separator to an asterisk.
if (footnoteSeparator is Run footnoteRun)
{
    footnoteRun.Text = "*";
}

// Optionally, change the continuation separator as well.
if (footnoteContinuation is Run continuationRun)
{
    continuationRun.Text = "*";
}
```

**لماذا هذا مهم:** تعديل `Run.Text` مباشرةً يحدّث التمثيل البصري في المستند النهائي دون التأثير على محتوى الحاشية السفلية الآخر. يمكن استخدام نفس النمط لتطبيق أي سلسلة، بما فيها الرموز Unicode.

---

## الخطوة 4: تغيير فاصل الحاشية الختامية (اختياري)

إذا كنت بحاجة أيضًا إلى **تغيير فاصل الحاشية الختامية**، فإن العملية مماثلة لتغيير فاصل الحاشية السفلية. استبدل نص `endnoteSeparator` بالحرف الذي ترغب به.

```csharp
// Change the endnote separator to a dash.
if (endnoteSeparator is Run endnoteRun)
{
    endnoteRun.Text = "-";
}
```

**لماذا هذا مهم:** غالبًا ما تُصمم الحواشي الختامية بنمط مختلف عن الحواشي السفلية. توفير فاصل منفصل يتيح لك الحفاظ على التناسق البصري مع إرشادات تصميم المستند.

---

## الخطوة 5: حفظ المستند المعدل

بعد إتمام جميع التعديلات، احفظ التغييرات باستخدام `Document.Save`. يمكنك استبدال الملف الأصلي أو الكتابة إلى موقع جديد.

```csharp
// Save the updated document.
document.Save(@"C:\Docs\ModifiedSeparators.docx");
```

**لماذا هذا مهم:** `Save` يكتب التمثيل الموجود في الذاكرة إلى القرص، مع الحفاظ على جميع العناصر الأخرى (الأنماط، الصور، الجداول) دون تغيير.

---

## مثال كامل قابل للتنفيذ

بدمج جميع الأجزاء، إليك تطبيق console مستقل يوضح سير العمل بالكامل:

```csharp
using System;
using Aspose.Words;

namespace FootnoteSeparatorDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Load the source document.
            string inputPath = @"C:\Docs\input.docx";
            Document doc = new Document(inputPath);

            // 2️⃣ Access separator nodes.
            Node footnoteSep = doc.FootnoteOptions.Separator;
            Node footnoteCont = doc.FootnoteOptions.ContinuationSeparator;
            Node endnoteSep = doc.FootnoteOptions.EndnoteSeparator;

            // 3️⃣ Change footnote separator to an asterisk.
            if (footnoteSep is Run footnoteRun)
                footnoteRun.Text = "*";

            // Optional: also change the continuation separator.
            if (footnoteCont is Run contRun)
                contRun.Text = "*";

            // 4️⃣ Change endnote separator to a dash.
            if (endnoteSep is Run endnoteRun)
                endnoteRun.Text = "-";

            // 5️⃣ Save the result.
            string outputPath = @"C:\Docs\ModifiedSeparators.docx";
            doc.Save(outputPath);

            Console.WriteLine("Document saved to " + outputPath);
        }
    }
}
```

**النتيجة المتوقعة:** افتح *ModifiedSeparators.docx* في Microsoft Word. سيظهر الآن خط فاصل الحاشية السفلية في أسفل الصفحة الأولى لحواشي السفلية كنجمة واحدة (`*`). إذا كان المستند يحتوي على حواشي ختامية، فإن الخط الفاصل بين النص الرئيسي وقائمة الحواشي الختامية سيظهر كشرطة (`-`). جميع المحتويات الأخرى (نص، صور، جداول) تبقى دون تعديل.

---

## أسئلة شائعة ومعالجة الحالات الخاصة

| السؤال | الجواب |
|----------|--------|
| **ماذا لو لم يحتوي المستند على حواشي سفلية؟** | `FootnoteOptions.Separator` لا يزال يُعيد عقدة `Run`، لكن نصها قد يكون فارغًا. يتحقق الكود بأمان من نوع العقدة قبل تعديلها. |
| **هل يمكنني استخدام سلسلة متعددة الأحرف (مثلاً "***")؟** | نعم. خاصية `Run.Text` تقبل أي سلسلة، بما فيها الأحرف Unicode. |
| **هل سيؤثر تغيير الفاصل على ترقيم الحواشي السفلية الموجود؟** | لا. الفاصل مستقل عن نظام الترقيم. |
| **هل يجب إغلاق كائن `Document`؟** | `Document` يطبق `IDisposable` ضمنيًا عبر `Node`. في تطبيق console قصير العمر هذا اختياري، لكن في الخدمات طويلة التشغيل يمكنك وضعه داخل كتلة `using`. |
| **كيف يعمل هذا مع .NET Core مقابل .NET Framework؟** | الواجهة البرمجية (API) متطابقة عبر جميع أوقات التشغيل؛ فقط نسخة الإطار المستهدف هي التي تهم (يجب أن تكون مدعومة من حزمة Aspose.Words). |

**نصيحة احترافية:** إذا كنت بحاجة لتطبيق فواصل مختلفة لأقسام متعددة، يمكنك التجول عبر `doc.GetChildNodes(NodeType.Footnote, true)` وتعديل خاصية `Separator` لكل حاشية على حدة. هذا أكثر تقدمًا لكنه مفيد للمستندات المعقدة.

---

## الخلاصة

أنت الآن تعرف كيف **تغيير فاصل الحاشية السفلية** و**تغيير فاصل الحاشية الختامية** في ملف Word باستخدام Aspose.Words للـ C#. غطى الدليل تحميل المستند، الوصول إلى عقد الفاصل ذات الصلة، تعديل نصها، وحفظ النتيجة—كل ذلك في برنامج واحد متكامل.

من هنا يمكنك استكشاف مواضيع ذات صلة مثل **تحرير نمط فاصل الحاشية السفلية**، تخصيص ترقيم الحواشي، أو تطبيق تنسيق شرطي بناءً على تخطيط الصفحة. النمط نفسه (استرجاع عقدة، تحويلها إلى `Run`، تعديل `Text`) يعمل في العديد من سيناريوهات معالجة Word.

برمجة سعيدة، ولا تتردد في تجربة رموز مختلفة أو حتى إدراج صور كفواصل للحصول على تخطيط مستند فريد حقًا!

## ما الذي يجب أن تتعلمه بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات التي تم توضيحها في هذا الدليل. كل مورد يتضمن أمثلة شيفرة كاملة مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف أساليب تنفيذ بديلة في مشاريعك.

- [معالجة الكلمات مع الحواشي السفلية والختامية](/words/english/net/working-with-footnote-and-endnote/)
- [الحصول على فاصل نمط الفقرة في مستند Word](/words/english/net/document-formatting/get-paragraph-style-separator/)
- [إدراج فاصل نمط المستند في Word](/words/english/net/programming-with-styles-and-themes/insert-style-separator/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}