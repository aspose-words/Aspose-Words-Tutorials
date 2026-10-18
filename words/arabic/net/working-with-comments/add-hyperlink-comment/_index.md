---
title: إضافة تعليق ارتباط تشعبي وتصديره كتعليق توضيحي في PDF باستخدام Aspose.Words for .NET
weight: 110
limit:
description: تعلم كيفية إضافة تعليق ارتباط تشعبي في ملف Word وتصديره كتعليق توضيحي في PDF باستخدام Aspose.Words for .NET.
keywords: [Aspose.Words for .NET, add hyperlink comment, PDF annotation, export Word to PDF, comment with hyperlink, verify PDF output]
url: /net/working-with-comments/add-hyperlink-comment/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: تعلم كيفية إضافة تعليق ارتباط تشعبي في ملف Word وتصديره كتعليق توضيحي
    في PDF باستخدام Aspose.Words for .NET.
  headline: إضافة تعليق ارتباط تشعبي وتصديره كتعليق توضيحي في PDF باستخدام Aspose.Words
    for .NET
  type: TechArticle
- description: تعلم كيفية إضافة تعليق ارتباط تشعبي في ملف Word وتصديره كتعليق توضيحي
    في PDF باستخدام Aspose.Words for .NET.
  name: إضافة تعليق ارتباط تشعبي وتصديره كتعليق توضيحي في PDF باستخدام Aspose.Words
    for .NET
  steps:
  - name: أنشئ كائن Document جديد فارغ وDocumentBuilder للعمل معه.
    text: أنشئ كائن Document جديد فارغ وDocumentBuilder للعمل معه.
  - name: اكتب سطرًا من النص الظاهر الذي سيستضيف التعليق القادم.
    text: اكتب سطرًا من النص الظاهر الذي سيستضيف التعليق القادم.
  - name: أنشئ Comment من تأليف Jane Doe وأرفقه بالفقرة الأولى من المستند.
    text: أنشئ Comment من تأليف Jane Doe وأرفقه بالفقرة الأولى من المستند.
  - name: داخل التعليق، أضف فقرة وأدرج ارتباطًا تشعبيًا أزرقًا ومُسطّرًا إلى موقع
      Aspose.Words Library.
    text: داخل التعليق، أضف فقرة وأدرج ارتباطًا تشعبيًا أزرقًا ومُسطّرًا إلى موقع
      Aspose.Words Library.
  - name: قم بتكوين المستند لعرض التعليقات كتعليقات توضيحية في PDF وقم بتحديث التخطيط.
    text: قم بتكوين المستند لعرض التعليقات كتعليقات توضيحية في PDF وقم بتحديث التخطيط.
  - name: أنشئ مجلد "Output" في الدليل الحالي لتخزين ملف PDF المُولَّد.
    text: أنشئ مجلد "Output" في الدليل الحالي لتخزين ملف PDF المُولَّد.
  - name: احفظ المستند المُجهَّز كملف PDF باستخدام PdfSaveOptions.
    text: احفظ المستند المُجهَّز كملف PDF باستخدام PdfSaveOptions.
  - name: تحقق من وجود ملف PDF وأنه يحتوي على بيانات، ثم اعرض النتيجة في وحدة التحكم.
    text: تحقق من وجود ملف PDF وأنه يحتوي على بيانات، ثم اعرض النتيجة في وحدة التحكم.
  type: HowTo
- questions:
  - answer: المعامل الثالث في `InsertHyperlink` يحدد ما إذا كان يجب معالجة الرابط
      كحقل؛ ضبطه على `false` يُدرج ارتباطًا تشعبيًا عاديًا يعمل في التعليق التوضيحي
      PDF دون الحاجة إلى رمز حقل.
    question: ماذا يتحكم فيه الوسيط الثالث (`false`) في `InsertHyperlink`؟
  - answer: قم بتعيين `myDocument.LayoutOptions.CommentDisplayMode` إلى `CommentDisplayMode.ShowInBalloons`
      قبل استدعاء `Save`؛ سيحتوي ملف PDF بعد ذلك على التعليق كتعليق Word عادي بدلاً
      من كتعليق توضيحي.
    question: كيف يمكنني جعل التعليق يظهر كفقاعة في مستند Word بدلاً من كتعليق توضيحي
      في PDF؟
  - answer: نعم—كل `Comment` تضيفه إلى فقرة يمكن أن يحتوي على استدعاء `InsertHyperlink`
      خاص به، وسيتم الحفاظ على جميع الروابط التشعبية كتعليقات توضيحية منفصلة في PDF
      عند حفظ المستند.
    question: إذا أضفت أكثر من تعليق، هل سيعمل كل ارتباط تشعبي في ملف PDF المُصدَّر؟
  - answer: افتح ملف PDF المُولَّد، وابحث عن التعليق التوضيحي (عادةً ما يُظهر كأيقونة
      ملاحظة)، انقر عليه لعرض نص التعليق، ثم انقر على الرابط الأزرق المُسطّر؛ يجب
      أن يفتح عنوان URL المستهدف في متصفح الويب.
    question: كيف يمكنني التحقق من أن الارتباط التشعبي داخل التعليق يعمل فعليًا بعد
      إنشاء ملف PDF؟
  type: FAQPage
images:
- /net/working-with-comments/add-hyperlink-comment/og-image.png
og_title: إدراج تعليق ارتباط تشعبي وتصديره إلى PDF
og_description: تعلم كيفية تضمين رابط قابل للنقر في تعليق Word وتحويله إلى تعليق توضيحي في PDF.
og_image_alt: دليل يوضح كيفية إضافة تعليق يحتوي على ارتباط تشعبي قابل للنقر إلى مستند Word وتصديره كتعليق توضيحي في PDF باستخدام Aspose.Words for .NET
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# إضافة تعليق ارتباط تشعبي وتصديره كتعليق توضيحي في PDF باستخدام Aspose.Words
في هذا البرنامج التعليمي ستتعرف على كيفية إنشاء مستند Word، وإدراج تعليق يحتوي على ارتباط تشعبي قابل للنقر إلى موقع ويب خارجي، وتكوين ذلك التعليق ليظهر كتعليق توضيحي في PDF، وتصدير المستند إلى PDF، والتحقق من ملف PDF الناتج. يتيح لك الكود خطوة بخطوة إضافة تعليقات غنية ومفعلة بالروابط والحفاظ عليها عند التحويل إلى PDF، مما يسهل مشاركة ملاحظات تفاعلية مع القراء.

---

{{< tutorial-widget sourcePath="words/net/working-with-comments/add-hyperlink-comment" >}}


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

**Q: ماذا يتحكم فيه الوسيط الثالث (`false`) في `InsertHyperlink`؟**  
A: المعامل الثالث في `InsertHyperlink` يحدد ما إذا كان يجب معالجة الرابط كحقل؛ ضبطه على `false` يُدرج ارتباطًا تشعبيًا عاديًا يعمل في التعليق التوضيحي PDF دون الحاجة إلى رمز حقل.

**Q: كيف يمكنني جعل التعليق يظهر كفقاعة في مستند Word بدلاً من كتعليق توضيحي في PDF؟**  
A: قم بتعيين `myDocument.LayoutOptions.CommentDisplayMode` إلى `CommentDisplayMode.ShowInBalloons` قبل استدعاء `Save`؛ سيحتوي ملف PDF بعد ذلك على التعليق كتعليق Word عادي بدلاً من كتعليق توضيحي.

**Q: إذا أضفت أكثر من تعليق، هل سيعمل كل ارتباط تشعبي في ملف PDF المُصدَّر؟**  
A: نعم—كل `Comment` تضيفه إلى فقرة يمكن أن يحتوي على استدعاء `InsertHyperlink` خاص به، وسيتم الحفاظ على جميع الروابط التشعبية كتعليقات توضيحية منفصلة في PDF عند حفظ المستند.

**Q: كيف يمكنني التحقق من أن الارتباط التشعبي داخل التعليق يعمل فعليًا بعد إنشاء ملف PDF؟**  
A: افتح ملف PDF المُولَّد، وابحث عن التعليق التوضيحي (عادةً ما يُظهر كأيقونة ملاحظة)، انقر عليه لعرض نص التعليق، ثم انقر على الرابط الأزرق المُسطّر؛ يجب أن يفتح عنوان URL المستهدف في متصفح الويب.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}