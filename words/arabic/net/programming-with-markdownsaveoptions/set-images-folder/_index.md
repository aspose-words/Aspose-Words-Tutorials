---
title: تعيين مجلد الصور
linktitle: تعيين مجلد الصور
second_title: واجهة برمجة تطبيقات معالجة المستندات Aspose.Words
description: قم بتحويل مستندات Word إلى Markdown مع محاذاة الجدول بشكل صحيح باستخدام Aspose.Words for .NET. اتبع دليلنا المفصل للحصول على نتائج مثالية.
weight: 10
url: /ar/net/programming-with-markdownsaveoptions/set-images-folder/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# تعيين مجلد الصور

## مقدمة

هل سبق لك أن أردت تصدير مستند Word الخاص بك إلى تنسيق Markdown مع ضمان محاذاة الجداول والمحتوى بشكل مثالي؟ يعد Aspose.Words for .NET الحل الأمثل لهذه المهمة. في هذه المقالة، سنوضح لك عملية إعداد Aspose.Words، وإعداد مستندك، وتصديره إلى تنسيق Markdown مع محاذاة محتويات الجدول بشكل صحيح. وسنوضح كل خطوة لتسهيل اتباعها وفهمها. لذا، دعنا نتعمق في تحويل مستندات Word الخاصة بك إلى ملفات Markdown محاذية بشكل جميل!

## المتطلبات الأساسية

قبل أن نبدأ، تأكد من أن لديك ما يلي:

-  Aspose.Words for .NET: يمكنك تنزيله[هنا](https://releases.aspose.com/words/net/).
-  ترخيص صالح: احصل على نسخة تجريبية مجانية[هنا](https://releases.aspose.com/) أو رخصة مؤقتة[هنا](https://purchase.aspose.com/temporary-license/).
- Visual Studio: أو أي IDE آخر يدعم تطوير .NET.
- المعرفة الأساسية بلغة C#: فهم لغة البرمجة C#.

## استيراد مساحات الأسماء

للبدء، ستحتاج إلى استيراد المساحات الأساسية اللازمة في مشروع C# الخاص بك. ستتيح لك هذه المساحات الأساسية الوصول إلى وظيفة Aspose.Words.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using System.IO;
```

## الخطوة 1: إعداد مشروعك

أولاً وقبل كل شيء، قم بإعداد مشروع .NET الخاص بك في بيئة التطوير المتكاملة الخاصة بك. قم بإنشاء تطبيق وحدة تحكم جديد وأضف مرجعًا إلى Aspose.Words لـ .NET.

### 1.1 إنشاء مشروع جديد

افتح Visual Studio وأنشئ مشروع تطبيق وحدة تحكم جديدًا. أطلق عليه اسم "MarkdownExporter" أو اسمًا مشابهًا.

### 1.2 إضافة مرجع Aspose.Words

 لإضافة Aspose.Words إلى مشروعك، يمكنك تنزيل DLL من[موقع اسبوس](https://releases.aspose.com/words/net/) وأضفها يدويًا، أو استخدم NuGet Package Manager:

```bash
Install-Package Aspose.Words
```

## الخطوة 2: اكتب الكود المراد تصديره بصيغة Markdown

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

 تكوين`MarkdownSaveOptions` لتحديد المكان الذي يجب تخزين الصور فيه.

```csharp
MarkdownSaveOptions saveOptions = new MarkdownSaveOptions
{
    ImagesFolder = dataDir + "Images"
};
```

### 2.4 حفظ المستند بتنسيق Markdown

 استخدم`MemoryStream` لحفظ المستند بتنسيق Markdown.

```csharp
using (MemoryStream stream = new MemoryStream())
{
    doc.Save(stream, saveOptions);
}
```

## خاتمة

إن تصدير مستند Word إلى تنسيق Markdown مع محاذاة محتوى الجدول باستخدام Aspose.Words for .NET أمر سهل عندما تتبع الخطوات التالية. باستخدام بضعة أسطر من التعليمات البرمجية، يمكنك أتمتة عملية التحويل والتأكد من تنسيق المحتوى بشكل جيد. الآن، يمكنك بسهولة مشاركة مستنداتك بتنسيق Markdown، مع العلم أنها ستبدو رائعة وستحافظ على بنيتها.

## الأسئلة الشائعة

### هل يمكنني استخدام Aspose.Words لـ .NET مع لغات برمجة أخرى؟

نعم، يمكن استخدام Aspose.Words for .NET مع أي لغة متوافقة مع .NET مثل VB.NET وF# والمزيد.

### كيف يمكنني الحصول على ترخيص مؤقت لـ Aspose.Words؟

يمكنك الحصول على ترخيص مؤقت[هنا](https://purchase.aspose.com/temporary-license/).

### ما هي أنواع المستندات التي يمكنني تحويلها إلى Markdown؟

يمكنك تحويل مستندات Word المختلفة بما في ذلك .doc، و.docx، و.rtf، والمزيد.

### هل هناك أي قيود في النسخة التجريبية من Aspose.Words؟

تحتوي النسخة التجريبية على بعض القيود مثل العلامات المائية في ملفات الإخراج. يمكنك الحصول على نسخة تجريبية مجانية[هنا](https://releases.aspose.com/).

### أين يمكنني العثور على المزيد من الأمثلة والوثائق لـ Aspose.Words؟

 يمكنك العثور على وثائق وأمثلة مفصلة على[موقع اسبوس](https://reference.aspose.com/words/net/).

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
