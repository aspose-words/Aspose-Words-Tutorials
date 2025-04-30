---
"description": "تعلّم كيفية تصدير موارد مثل CSS والخطوط مع حفظ مستندات Word بتنسيق HTML باستخدام Aspose.Words لـ .NET. اتبع دليلنا خطوة بخطوة."
"linktitle": "تصدير الموارد"
"second_title": "واجهة برمجة تطبيقات معالجة المستندات Aspose.Words"
"title": "تصدير الموارد"
"url": "/ar/net/programming-with-htmlsaveoptions/export-resources/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# تصدير الموارد

## مقدمة

أهلاً بكم، أيها المتحمسون للتكنولوجيا! إذا كنتم بحاجة لتحويل مستندات Word إلى HTML، فأنتم في المكان المناسب. اليوم، نغوص في عالم Aspose.Words الرائع لـ .NET. هذه المكتبة القوية تُسهّل العمل مع مستندات Word برمجياً. في هذا البرنامج التعليمي، سنشرح خطوات تصدير الموارد، مثل الخطوط وCSS، عند حفظ مستند Word بتنسيق HTML باستخدام Aspose.Words لـ .NET. استعدوا لرحلة ممتعة ومفيدة!

## المتطلبات الأساسية

قبل أن نتعمق في شرح الكود، لنتأكد من حصولك على كل ما تحتاجه للبدء. إليك قائمة مرجعية سريعة:

1. فيجوال ستوديو: تأكد من تثبيت فيجوال ستوديو على جهازك. يمكنك تنزيله من [موقع ويب Visual Studio](https://visualstudio.microsoft.com/).
2. Aspose.Words لـ .NET: ستحتاج إلى مكتبة Aspose.Words لـ .NET. إذا لم تكن لديك بعد، فاحصل على نسخة تجريبية مجانية من [إصدارات Aspose](https://releases.aspose.com/words/net/) أو شرائه من [متجر أسبوس](https://purchase.aspose.com/buy).
3. المعرفة الأساسية بلغة C#: إن الفهم الأساسي للغة C# سيساعدك على متابعة أمثلة التعليمات البرمجية.

هل فهمت كل ذلك؟ رائع! لننتقل إلى استيراد مساحات الأسماء اللازمة.

## استيراد مساحات الأسماء

لاستخدام Aspose.Words لـ .NET، عليك تضمين مساحات الأسماء ذات الصلة في مشروعك. إليك كيفية القيام بذلك:

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

تُعد هذه المساحات الأساسية ضرورية للوصول إلى فئات وطرق Aspose.Words التي سنستخدمها في البرنامج التعليمي الخاص بنا.

دعونا نشرح عملية تصدير الموارد عند حفظ مستند وورد بصيغة HTML. سنشرحها خطوة بخطوة ليسهل متابعتها.

## الخطوة 1: إعداد دليل المستندات الخاص بك

أولاً، عليك تحديد مسار مجلد المستندات. هذا هو المكان الذي يوجد فيه مستند Word، وهو المكان الذي سيتم حفظ ملف HTML فيه.

```csharp
// المسار إلى دليل المستندات.
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

يستبدل `"YOUR DOCUMENT DIRECTORY"` مع المسار الفعلي إلى الدليل الخاص بك.

## الخطوة 2: تحميل مستند Word

بعد ذلك، لنحمّل مستند Word الذي نريد تحويله إلى HTML. في هذا البرنامج التعليمي، سنستخدم مستندًا باسم `Rendering.docx`.

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

يقوم هذا السطر من التعليمات البرمجية بتحميل المستند من الدليل المحدد.

## الخطوة 3: تكوين خيارات حفظ HTML

لتصدير الموارد مثل CSS والخطوط، تحتاج إلى تكوين `HtmlSaveOptions`. هذه الخطوة ضرورية لضمان أن يكون مخرجات HTML الخاصة بك منظمة بشكل جيد وتتضمن الموارد الضرورية.

```csharp
HtmlSaveOptions saveOptions = new HtmlSaveOptions
{
    CssStyleSheetType = CssStyleSheetType.External,
    ExportFontResources = true,
    ResourceFolder = dataDir + "Resources",
    ResourceFolderAlias = "http://example.com/resources"
};
```

دعونا نوضح ما يفعله كل خيار:
- `CssStyleSheetType = CssStyleSheetType.External`:يحدد هذا الخيار أنه يجب حفظ أنماط CSS في ورقة أنماط خارجية.
- `ExportFontResources = true`:هذا يمكّن من تصدير موارد الخط.
- `ResourceFolder = dataDir + "Resources"`:يحدد المجلد المحلي الذي سيتم حفظ الموارد فيه (مثل الخطوط وملفات CSS).
- `ResourceFolderAlias = "http://example.com/resources"`:تعيين اسم مستعار لمجلد الموارد، والذي سيتم استخدامه في ملف HTML.

## الخطوة 4: حفظ المستند بصيغة HTML

بعد ضبط خيارات الحفظ، الخطوة الأخيرة هي حفظ المستند كملف HTML. إليك الطريقة:

```csharp
doc.Save(dataDir + "WorkingWithHtmlSaveOptions.ExportResources.html", saveOptions);
```

يحفظ هذا السطر من التعليمات البرمجية المستند بتنسيق HTML، إلى جانب الموارد المصدرة.

## خاتمة

ها قد انتهيت! لقد نجحت في تصدير الموارد مع حفظ مستند وورد بصيغة HTML باستخدام Aspose.Words لـ .NET. مع هذه المكتبة القوية، أصبح التعامل مع مستندات وورد برمجيًا في غاية السهولة. سواء كنت تعمل على تطبيق ويب أو تحتاج فقط إلى تحويل مستندات للاستخدام دون اتصال بالإنترنت، فإن Aspose.Words يلبي احتياجاتك.

## الأسئلة الشائعة

### هل يمكنني تصدير الصور مع الخطوط و CSS؟
نعم، يمكنك ذلك! يدعم Aspose.Words لـ .NET تصدير الصور أيضًا. فقط تأكد من تكوين `HtmlSaveOptions` وفقاً لذلك.

### هل هناك طريقة لتضمين CSS بدلاً من استخدام ورقة أنماط خارجية؟
بالتأكيد. يمكنك ضبط `CssStyleSheetType` ل `CssStyleSheetType.Embedded` إذا كنت تفضل الأنماط المضمنة.

### كيف يمكنني تخصيص اسم ملف HTML الناتج؟
يمكنك تحديد أي اسم ملف تريده في `doc.Save` الطريقة. على سبيل المثال، `doc.Save(dataDir + "CustomFileName.html", saveOptions);`.

### هل يدعم Aspose.Words تنسيقات أخرى إلى جانب HTML؟
نعم، يدعم صيغًا متنوعة، بما في ذلك PDF وDOCX وTXT وغيرها. اطلع على [التوثيق](https://reference.aspose.com/words/net/) للحصول على القائمة الكاملة.

### أين يمكنني الحصول على المزيد من الدعم والموارد؟
لمزيد من المساعدة، قم بزيارة [منتدى دعم Aspose.Words](https://forum.aspose.com/c/words/8)يمكنك أيضًا العثور على وثائق وأمثلة مفصلة على [موقع Aspose](https://reference.aspose.com/words/net/).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}