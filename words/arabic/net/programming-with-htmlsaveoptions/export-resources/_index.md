---
title: تصدير الموارد
linktitle: تصدير الموارد
second_title: واجهة برمجة تطبيقات معالجة المستندات Aspose.Words
description: تعرف على كيفية تصدير الموارد مثل CSS والخطوط مع حفظ مستندات Word بتنسيق HTML باستخدام Aspose.Words for .NET. اتبع دليلنا خطوة بخطوة.
weight: 10
url: /ar/net/programming-with-htmlsaveoptions/export-resources/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# تصدير الموارد

## مقدمة

مرحبًا بكم، أيها المتحمسون للتكنولوجيا! إذا كنت في حاجة إلى تحويل مستندات Word إلى HTML، فأنت في المكان المناسب. اليوم، نغوص في عالم Aspose.Words الرائع لـ .NET. تجعل هذه المكتبة القوية العمل مع مستندات Word برمجيًا أمرًا سهلاً. في هذا البرنامج التعليمي، سنستعرض الخطوات اللازمة لتصدير الموارد، مثل الخطوط وCSS، عند حفظ مستند Word بتنسيق HTML باستخدام Aspose.Words لـ .NET. استعد لرحلة ممتعة ومفيدة!

## المتطلبات الأساسية

قبل أن نتعمق في الكود، دعنا نتأكد من أنك حصلت على كل ما تحتاجه للبدء. إليك قائمة مرجعية سريعة:

1.  Visual Studio: تأكد من تثبيت Visual Studio على جهازك. يمكنك تنزيله من[موقع فيجوال ستوديو](https://visualstudio.microsoft.com/).
2.  Aspose.Words for .NET: ستحتاج إلى مكتبة Aspose.Words for .NET. إذا لم تكن قد حصلت عليها بعد، فاحصل على نسخة تجريبية مجانية من[إصدارات Aspose](https://releases.aspose.com/words/net/) أو اشتريه من[متجر اسبوس](https://purchase.aspose.com/buy).
3. المعرفة الأساسية بلغة C#: إن الفهم الأساسي للغة C# سيساعدك على متابعة أمثلة التعليمات البرمجية.

هل فهمت كل ذلك؟ رائع! دعنا ننتقل إلى استيراد المساحات الأساسية اللازمة.

## استيراد مساحات الأسماء

لاستخدام Aspose.Words لـ .NET، تحتاج إلى تضمين المساحات ذات الصلة في مشروعك. إليك كيفية القيام بذلك:

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

تُعد هذه المساحات الأساسية ضرورية للوصول إلى فئات وطرق Aspose.Words التي سنستخدمها في البرنامج التعليمي الخاص بنا.

دعنا نوضح عملية تصدير الموارد عند حفظ مستند Word بتنسيق HTML. سنتناولها خطوة بخطوة، حتى يسهل متابعتها.

## الخطوة 1: إعداد دليل المستندات الخاص بك

أولاً وقبل كل شيء، عليك تحديد المسار إلى دليل المستندات. هذا هو المكان الذي يوجد فيه مستند Word الخاص بك والمكان الذي سيتم حفظ ملف HTML فيه.

```csharp
// المسار إلى دليل المستندات.
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

 يستبدل`"YOUR DOCUMENT DIRECTORY"` مع المسار الفعلي إلى الدليل الخاص بك.

## الخطوة 2: تحميل مستند Word

 بعد ذلك، دعنا نحمل مستند Word الذي تريد تحويله إلى HTML. في هذا البرنامج التعليمي، سنستخدم مستندًا باسم`Rendering.docx`.

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

يقوم هذا السطر من التعليمات البرمجية بتحميل المستند من الدليل المحدد.

## الخطوة 3: تكوين خيارات حفظ HTML

لتصدير الموارد مثل CSS والخطوط، تحتاج إلى تكوين`HtmlSaveOptions`. هذه الخطوة ضرورية لضمان أن يكون مخرج HTML الخاص بك منظمًا بشكل جيد ويتضمن الموارد اللازمة.

```csharp
HtmlSaveOptions saveOptions = new HtmlSaveOptions
{
    CssStyleSheetType = CssStyleSheetType.External,
    ExportFontResources = true,
    ResourceFolder = dataDir + "Resources",
    ResourceFolderAlias = "http://"مثال.com/resources"
};
```

دعونا نلقي نظرة على ما يفعله كل خيار:
- `CssStyleSheetType = CssStyleSheetType.External`:يحدد هذا الخيار أنه يجب حفظ أنماط CSS في ورقة أنماط خارجية.
- `ExportFontResources = true`:هذا يمكّن من تصدير موارد الخط.
- `ResourceFolder = dataDir + "Resources"`:يحدد المجلد المحلي الذي سيتم حفظ الموارد فيه (مثل الخطوط وملفات CSS).
- `ResourceFolderAlias = "http://example.com/resources"`:تعيين اسم مستعار لمجلد الموارد، والذي سيتم استخدامه في ملف HTML.

## الخطوة 4: حفظ المستند بصيغة HTML

بعد تكوين خيارات الحفظ، تكون الخطوة الأخيرة هي حفظ المستند كملف HTML. وإليك كيفية القيام بذلك:

```csharp
doc.Save(dataDir + "WorkingWithHtmlSaveOptions.ExportResources.html", saveOptions);
```

يحفظ هذا السطر من التعليمات البرمجية المستند بتنسيق HTML، إلى جانب الموارد المصدرة.

## خاتمة

والآن، لقد نجحت في تصدير الموارد أثناء حفظ مستند Word بتنسيق HTML باستخدام Aspose.Words for .NET. وبفضل هذه المكتبة القوية، أصبح التعامل مع مستندات Word برمجيًا أمرًا سهلاً للغاية. سواء كنت تعمل على تطبيق ويب أو تحتاج فقط إلى تحويل المستندات للاستخدام دون اتصال بالإنترنت، فإن Aspose.Words يوفر لك كل ما تحتاجه.

## الأسئلة الشائعة

### هل يمكنني تصدير الصور مع الخطوط وCSS؟
 نعم، يمكنك ذلك! يدعم Aspose.Words for .NET أيضًا تصدير الصور. فقط تأكد من تكوين`HtmlSaveOptions` وفقاً لذلك.

### هل هناك طريقة لتضمين CSS بدلاً من استخدام ورقة أنماط خارجية؟
 بالتأكيد. يمكنك ضبط`CssStyleSheetType` ل`CssStyleSheetType.Embedded` إذا كنت تفضل الأنماط المضمنة.

### كيف يمكنني تخصيص اسم ملف HTML الناتج؟
 يمكنك تحديد أي اسم ملف تريده في`doc.Save` الطريقة. على سبيل المثال،`doc.Save(dataDir + "CustomFileName.html", saveOptions);`.

### هل يدعم Aspose.Words تنسيقات أخرى إلى جانب HTML؟
 نعم، فهو يدعم تنسيقات مختلفة بما في ذلك PDF وDOCX وTXT والمزيد. تحقق من[التوثيق](https://reference.aspose.com/words/net/) للحصول على القائمة الكاملة.

### أين يمكنني الحصول على المزيد من الدعم والموارد؟
لمزيد من المساعدة، قم بزيارة[منتدى دعم Aspose.Words](https://forum.aspose.com/c/words/8) يمكنك أيضًا العثور على وثائق وأمثلة مفصلة على[موقع اسبوس](https://reference.aspose.com/words/net/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
