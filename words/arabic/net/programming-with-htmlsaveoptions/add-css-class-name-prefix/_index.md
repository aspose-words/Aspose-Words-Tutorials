---
title: إضافة بادئة اسم فئة CSS
linktitle: إضافة بادئة اسم فئة CSS
second_title: واجهة برمجة تطبيقات معالجة المستندات Aspose.Words
description: تعرف على كيفية إضافة بادئة اسم فئة CSS عند حفظ مستندات Word بتنسيق HTML باستخدام Aspose.Words for .NET. دليل خطوة بخطوة، ومقاطع من التعليمات البرمجية، والأسئلة الشائعة المضمنة.
weight: 10
url: /ar/net/programming-with-htmlsaveoptions/add-css-class-name-prefix/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# إضافة بادئة اسم فئة CSS

## مقدمة

مرحبًا بك! إذا كنت تتعمق في عالم Aspose.Words for .NET، فأنت على موعد مع متعة لا تُنسى. اليوم، سنستكشف كيفية إضافة بادئة اسم فئة CSS عند حفظ مستند Word بتنسيق HTML باستخدام Aspose.Words for .NET. هذه الميزة مفيدة للغاية عندما تريد تجنب تعارضات اسم الفئة في ملفات HTML.

## المتطلبات الأساسية

قبل أن نبدأ، تأكد من أن لديك ما يلي:

-  Aspose.Words لـ .NET: إذا لم تقم بتثبيته بعد،[تحميله هنا](https://releases.aspose.com/words/net/).
- بيئة التطوير: Visual Studio أو أي C# IDE آخر.
-  مستند Word: سنستخدم مستندًا باسم`Rendering.docx`ضعه في دليل المشروع الخاص بك.

## استيراد مساحات الأسماء

أولاً، تأكد من استيراد مساحات الأسماء الضرورية إلى مشروع C# الخاص بك. أضف هذه المساحات في أعلى ملف التعليمات البرمجية الخاص بك:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;
```

الآن، دعونا ننتقل إلى الدليل خطوة بخطوة!

## الخطوة 1: إعداد مشروعك

قبل أن نتمكن من البدء في إضافة بادئة اسم فئة CSS، دعنا نقوم بإعداد مشروعنا.

### الخطوة 1.1: إنشاء مشروع جديد

 قم بتشغيل Visual Studio الخاص بك وقم بإنشاء مشروع تطبيق وحدة تحكم جديد. قم بتسميته بشيء جذاب مثل`AsposeCssPrefixExample`.

### الخطوة 1.2: إضافة Aspose.Words إلى .NET

إذا لم تكن قد قمت بذلك بالفعل، فأضف Aspose.Words for .NET إلى مشروعك عبر NuGet. ما عليك سوى فتح وحدة تحكم إدارة الحزم NuGet وتشغيل:

```bash
Install-Package Aspose.Words
```

رائع! الآن أصبحنا جاهزين لبدء البرمجة.

## الخطوة 2: قم بتحميل مستندك

أول شيء يتعين علينا فعله هو تحميل مستند Word الذي نريد تحويله إلى HTML.

### الخطوة 2.1: تحديد مسار المستند

 قم بإعداد المسار إلى دليل المستند الخاص بك. من أجل هذا البرنامج التعليمي، دعنا نفترض أن المستند الخاص بك موجود في مجلد باسم`Documents` ضمن دليل المشروع الخاص بك.

```csharp
string dataDir = @"C:\YourProject\Documents\";
```

### الخطوة 2.2: تحميل المستند

الآن، دعنا نحمل المستند باستخدام Aspose.Words:

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

## الخطوة 3: تكوين خيارات حفظ HTML

بعد ذلك، نحتاج إلى تكوين خيارات حفظ HTML لتشمل بادئة اسم فئة CSS.

### الخطوة 3.1: إنشاء خيارات حفظ HTML

 إنشاء مثيل`HtmlSaveOptions` الكائن وتعيين نوع ورقة نمط CSS إلى`External`.

```csharp
HtmlSaveOptions saveOptions = new HtmlSaveOptions
{
    CssStyleSheetType = CssStyleSheetType.External
};
```

### الخطوة 3.2: تعيين بادئة اسم فئة CSS

 الآن، دعونا نضع`CssClassNamePrefix` الخاصية إلى البادئة المطلوبة. في هذا المثال، سنستخدم`"pfx_"`.

```csharp
saveOptions.CssClassNamePrefix = "pfx_";
```

## الخطوة 4: حفظ المستند بصيغة HTML

وأخيرًا، دعنا نحفظ المستند كملف HTML باستخدام خياراتنا التي قمنا بتكوينها.


حدد مسار ملف HTML الناتج واحفظ المستند.

```csharp
doc.Save(dataDir + "WorkingWithHtmlSaveOptions.AddCssClassNamePrefix.html", saveOptions);
```

## الخطوة 5: التحقق من الناتج

 بعد تشغيل مشروعك، انتقل إلى`Documents` المجلد. يجب أن تجد ملف HTML باسم`WorkingWithHtmlSaveOptions.AddCssClassNamePrefix.html` افتح هذا الملف في محرر نصوص أو متصفح للتحقق من أن فئات CSS تحتوي على البادئة`pfx_`.

## خاتمة

والآن، لقد انتهيت! باتباع هذه الخطوات، تكون قد نجحت في إضافة بادئة اسم فئة CSS إلى مخرجات HTML باستخدام Aspose.Words for .NET. يمكن أن تساعدك هذه الميزة البسيطة والقوية في الحفاظ على أنماط نظيفة وخالية من التعارضات في مستندات HTML.

## الأسئلة الشائعة

### هل يمكنني استخدام بادئة مختلفة لكل عملية حفظ؟
 نعم، يمكنك تخصيص البادئة في كل مرة تحفظ فيها مستندًا عن طريق تغيير`CssClassNamePrefix` ملكية.

### هل تدعم هذه الطريقة CSS المضمنة؟
 ال`CssClassNamePrefix`تعمل الخاصية مع CSS خارجي. بالنسبة لـ CSS المضمن، ستحتاج إلى نهج مختلف.

### كيف يمكنني تضمين خيارات حفظ HTML الأخرى؟
 يمكنك تكوين خصائص مختلفة لـ`HtmlSaveOptions` لتخصيص مخرجات HTML الخاصة بك. تحقق من[التوثيق](https://reference.aspose.com/words/net/) لمزيد من التفاصيل.

### هل من الممكن حفظ HTML في تيار؟
 بالتأكيد! يمكنك حفظ المستند في مجرى عن طريق تمرير كائن المجرى إلى`Save` طريقة.

### كيف يمكنني الحصول على الدعم إذا واجهت مشاكل؟
 يمكنك الحصول على الدعم من[منتدى اسبوس](https://forum.aspose.com/c/words/8).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
