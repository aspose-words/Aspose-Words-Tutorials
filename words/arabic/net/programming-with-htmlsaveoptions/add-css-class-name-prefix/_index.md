---
"description": "تعرّف على كيفية إضافة بادئة اسم فئة CSS عند حفظ مستندات Word بتنسيق HTML باستخدام Aspose.Words لـ .NET. يتضمن دليلًا خطوة بخطوة، ومقاطع برمجية، وأسئلة شائعة."
"linktitle": "إضافة بادئة اسم فئة CSS"
"second_title": "واجهة برمجة تطبيقات معالجة المستندات Aspose.Words"
"title": "إضافة بادئة اسم فئة CSS"
"url": "/ar/net/programming-with-htmlsaveoptions/add-css-class-name-prefix/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# إضافة بادئة اسم فئة CSS

## مقدمة

أهلاً بك! إذا كنت تتعمق في عالم Aspose.Words لـ .NET، فأنت على موعد مع متعة لا تُنسى. سنستكشف اليوم كيفية إضافة بادئة اسم فئة CSS عند حفظ مستند Word بتنسيق HTML باستخدام Aspose.Words لـ .NET. هذه الميزة مفيدة للغاية لتجنب تعارض أسماء الفئات في ملفات HTML.

## المتطلبات الأساسية

قبل أن نبدأ، تأكد من أن لديك ما يلي:

- Aspose.Words لـ .NET: إذا لم تقم بتثبيته بعد، [قم بتحميله هنا](https://releases.aspose.com/words/net/).
- بيئة التطوير: Visual Studio أو أي بيئة تطوير متكاملة أخرى لـC#.
- مستند Word: سنستخدم مستندًا باسم `Rendering.docx`ضعه في دليل المشروع الخاص بك.

## استيراد مساحات الأسماء

أولاً، تأكد من استيراد مساحات الأسماء اللازمة إلى مشروع C#. أضفها في أعلى ملف الكود الخاص بك:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;
```

الآن، دعونا ننتقل إلى الدليل خطوة بخطوة!

## الخطوة 1: إعداد مشروعك

قبل أن نتمكن من البدء في إضافة بادئة اسم فئة CSS، دعنا نقوم بإعداد مشروعنا.

### الخطوة 1.1: إنشاء مشروع جديد

شغّل برنامج Visual Studio وأنشئ مشروع تطبيق وحدة تحكم جديدًا. سمّه اسمًا جذابًا مثل `AsposeCssPrefixExample`.

### الخطوة 1.2: إضافة Aspose.Words لـ .NET

إذا لم تقم بذلك بالفعل، فأضف Aspose.Words for .NET إلى مشروعك عبر NuGet. ما عليك سوى فتح وحدة تحكم إدارة الحزم NuGet وتشغيل الأمر التالي:

```bash
Install-Package Aspose.Words
```

رائع! الآن نحن جاهزون لبدء البرمجة.

## الخطوة 2: تحميل المستند الخاص بك

أول شيء يتعين علينا القيام به هو تحميل مستند Word الذي نريد تحويله إلى HTML.

### الخطوة 2.1: تحديد مسار المستند

حدّد مسار مجلد مستندك. في هذا الدرس، لنفترض أن مستندك موجود في مجلد باسم `Documents` ضمن دليل المشروع الخاص بك.

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

إنشاء مثيل `HtmlSaveOptions` الكائن وتعيين نوع ورقة أنماط CSS إلى `External`.

```csharp
HtmlSaveOptions saveOptions = new HtmlSaveOptions
{
    CssStyleSheetType = CssStyleSheetType.External
};
```

### الخطوة 3.2: تعيين بادئة اسم فئة CSS

الآن، دعونا نضع `CssClassNamePrefix` الخاصية إلى البادئة المطلوبة. في هذا المثال، سنستخدم `"pfx_"`.

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

بعد تشغيل مشروعك، انتقل إلى `Documents` المجلد. يجب أن تجد ملف HTML باسم `WorkingWithHtmlSaveOptions.AddCssClassNamePrefix.html`. افتح هذا الملف في محرر نصوص أو متصفح للتحقق من أن فئات CSS تحتوي على البادئة `pfx_`.

## خاتمة

وهذا كل شيء! باتباع هذه الخطوات، تكون قد أضفت بنجاح بادئة اسم فئة CSS إلى مُخرجات HTML باستخدام Aspose.Words لـ .NET. هذه الميزة البسيطة والفعّالة تُساعدك على الحفاظ على أنماط واضحة وخالية من التعارضات في مستندات HTML.

## الأسئلة الشائعة

### هل يمكنني استخدام بادئة مختلفة لكل عملية حفظ؟
نعم، يمكنك تخصيص البادئة في كل مرة تحفظ فيها مستندًا عن طريق تغيير `CssClassNamePrefix` ملكية.

### هل تدعم هذه الطريقة CSS المضمنة؟
ال `CssClassNamePrefix` تعمل الخاصية مع CSS خارجي. أما بالنسبة لـ CSS المضمن، فستحتاج إلى نهج مختلف.

### كيف يمكنني تضمين خيارات حفظ HTML الأخرى؟
يمكنك تكوين خصائص مختلفة لـ `HtmlSaveOptions` لتخصيص مخرجات HTML الخاصة بك. تحقق من [التوثيق](https://reference.aspose.com/words/net/) لمزيد من التفاصيل.

### هل من الممكن حفظ HTML في مجرى؟
بالتأكيد! يمكنك حفظ المستند في مجرى عن طريق تمرير كائن المجرى إلى `Save` طريقة.

### كيف يمكنني الحصول على الدعم إذا واجهت مشاكل؟
يمكنك الحصول على الدعم من [منتدى Aspose](https://forum.aspose.com/c/words/8).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}