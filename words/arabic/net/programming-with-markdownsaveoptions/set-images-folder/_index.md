---
"description": "حوّل مستندات Word إلى Markdown مع محاذاة الجداول بشكل صحيح باستخدام Aspose.Words لـ .NET. اتبع دليلنا المفصل للحصول على نتائج مثالية."
"linktitle": "تعيين مجلد الصور"
"second_title": "واجهة برمجة تطبيقات معالجة المستندات Aspose.Words"
"title": "تعيين مجلد الصور"
"url": "/ar/net/programming-with-markdownsaveoptions/set-images-folder/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# تعيين مجلد الصور

## مقدمة

هل رغبتَ يومًا في تصدير مستند Word إلى تنسيق Markdown مع ضمان محاذاة الجداول والمحتوى بشكل مثالي؟ يُعدّ Aspose.Words for .NET الحل الأمثل لهذه المهمة. في هذه المقالة، سنشرح لك عملية إعداد Aspose.Words، وإعداد مستندك، وتصديره إلى تنسيق Markdown مع محاذاة محتويات الجداول بشكل صحيح. سنُفصّل كل خطوة لتسهيل فهمها. لذا، هيا بنا ننطلق ونحوّل مستندات Word إلى ملفات Markdown مُحاذاة بشكل جميل!

## المتطلبات الأساسية

قبل أن نبدأ، تأكد من أن لديك ما يلي:

- Aspose.Words for .NET: يمكنك تنزيله [هنا](https://releases.aspose.com/words/net/).
- ترخيص صالح: احصل على نسخة تجريبية مجانية [هنا](https://releases.aspose.com/) أو رخصة مؤقتة [هنا](https://purchase.aspose.com/temporary-license/).
- Visual Studio: أو أي IDE آخر يدعم تطوير .NET.
- المعرفة الأساسية بلغة C#: فهم لغة البرمجة C#.

## استيراد مساحات الأسماء

للبدء، ستحتاج إلى استيراد مساحات الأسماء اللازمة في مشروع C# الخاص بك. ستتيح لك هذه المساحات الوصول إلى وظيفة Aspose.Words.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using System.IO;
```

## الخطوة 1: إعداد مشروعك

أولاً، قم بإعداد مشروع .NET الخاص بك في بيئة التطوير المتكاملة (IDE). أنشئ تطبيق وحدة تحكم جديدًا وأضف مرجعًا إلى Aspose.Words for .NET.

### 1.1 إنشاء مشروع جديد

افتح Visual Studio وأنشئ مشروع تطبيق وحدة تحكم جديدًا. سمّه "MarkdownExporter" أو ما شابه.

### 1.2 إضافة مرجع Aspose.Words

لإضافة Aspose.Words إلى مشروعك، يمكنك تنزيل ملف DLL من [موقع Aspose](https://releases.aspose.com/words/net/) وأضفه يدويًا، أو استخدم NuGet Package Manager:

```bash
Install-Package Aspose.Words
```

## الخطوة 2: اكتب الكود لتصديره بتنسيق Markdown

الآن، دعنا نكتب الكود لقراءة مستند Word وحفظه كملف Markdown مع محاذاة الجدول المناسبة.

### 2.1 تحديد المسار إلى مستندك

قم بتعيين المسار إلى مستند Word والمجلد الذي تريد حفظ الصور فيه.

```csharp
string dataDir = "YOUR_DOCUMENT_DIRECTORY";
```

### 2.2 تحميل المستند

قم بتحميل مستند Word الخاص بك باستخدام Aspose.Words.

```csharp
Document doc = new Document(dataDir + "Image bullet points.docx");
```

### 2.3 تكوين خيارات حفظ Markdown

تكوين `MarkdownSaveOptions` لتحديد المكان الذي يجب تخزين الصور فيه.

```csharp
MarkdownSaveOptions saveOptions = new MarkdownSaveOptions
{
    ImagesFolder = dataDir + "Images"
};
```

### 2.4 حفظ المستند بتنسيق Markdown

استخدم `MemoryStream` لحفظ المستند بتنسيق Markdown.

```csharp
using (MemoryStream stream = new MemoryStream())
{
    doc.Save(stream, saveOptions);
}
```

## خاتمة

تصدير مستند Word إلى Markdown مع محاذاة محتوى الجدول باستخدام Aspose.Words for .NET سهلٌ باتباع الخطوات التالية. باستخدام بضعة أسطر من التعليمات البرمجية، يمكنك أتمتة عملية التحويل وضمان تنسيق محتواك بشكل جيد. الآن، يمكنك بسهولة مشاركة مستنداتك بتنسيق Markdown، مع ضمان مظهرها الرائع وبنيتها المميزة.

## الأسئلة الشائعة

### هل يمكنني استخدام Aspose.Words لـ .NET مع لغات برمجة أخرى؟

نعم، يمكن استخدام Aspose.Words for .NET مع أي لغة متوافقة مع .NET مثل VB.NET وF# والمزيد.

### كيف أحصل على ترخيص مؤقت لـ Aspose.Words؟

يمكنك الحصول على ترخيص مؤقت [هنا](https://purchase.aspose.com/temporary-license/).

### ما هي أنواع المستندات التي يمكنني تحويلها إلى Markdown؟

يمكنك تحويل مستندات Word المختلفة بما في ذلك .doc، و.docx، و.rtf، والمزيد.

### هل هناك أي قيود في النسخة التجريبية من Aspose.Words؟

النسخة التجريبية بها بعض القيود، مثل وجود علامات مائية في ملفات الإخراج. يمكنك الحصول على نسخة تجريبية مجانية. [هنا](https://releases.aspose.com/).

### أين يمكنني العثور على المزيد من الأمثلة والوثائق لـ Aspose.Words؟

يمكنك العثور على وثائق وأمثلة مفصلة على [موقع Aspose](https://reference.aspose.com/words/net/).



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}