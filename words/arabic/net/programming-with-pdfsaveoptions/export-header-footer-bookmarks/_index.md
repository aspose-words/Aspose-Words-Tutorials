---
"description": "تعرف على كيفية تصدير إشارات مرجعية للرأس والتذييل من مستند Word إلى PDF باستخدام Aspose.Words for .NET من خلال دليلنا خطوة بخطوة."
"linktitle": "تصدير الإشارات المرجعية لرأس وتذييل مستند Word إلى مستند PDF"
"second_title": "واجهة برمجة تطبيقات معالجة المستندات Aspose.Words"
"title": "تصدير الإشارات المرجعية لرأس وتذييل مستند Word إلى مستند PDF"
"url": "/ar/net/programming-with-pdfsaveoptions/export-header-footer-bookmarks/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# تصدير الإشارات المرجعية لرأس وتذييل مستند Word إلى مستند PDF

## مقدمة

تحويل مستندات Word إلى PDF مهمة شائعة، خاصةً عند مشاركة المستندات أو أرشفتها مع الحفاظ على تنسيقها. أحيانًا، تحتوي هذه المستندات على إشارات مرجعية مهمة ضمن رؤوس وتذييلات الصفحات. في هذا البرنامج التعليمي، سنشرح عملية تصدير هذه الإشارات المرجعية من مستند Word إلى PDF باستخدام Aspose.Words لـ .NET.

## المتطلبات الأساسية

قبل أن نبدأ، تأكد من أن لديك ما يلي:

- Aspose.Words لـ .NET: يجب تثبيت Aspose.Words لـ .NET. يمكنك تنزيله من [هنا](https://releases.aspose.com/words/net/).
- بيئة التطوير: قم بإعداد بيئة التطوير الخاصة بك. يمكنك استخدام Visual Studio أو أي بيئة تطوير متكاملة أخرى متوافقة مع .NET.
- المعرفة الأساسية بلغة C#: مطلوب معرفة ببرمجة C# لمتابعة أمثلة التعليمات البرمجية.

## استيراد مساحات الأسماء

أولاً، عليك استيراد مساحات الأسماء اللازمة في مشروع C#. أضف هذه الأسطر في أعلى ملف الكود الخاص بك:

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

دعونا نقسم العملية إلى خطوات سهلة المتابعة.

## الخطوة 1: تهيئة المستند

الخطوة الأولى هي تحميل مستند Word. إليك الطريقة:

```csharp
// المسار إلى دليل المستندات.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Bookmarks in headers and footers.docx");
```

في هذه الخطوة، عليك ببساطة تحديد المسار إلى دليل المستند الخاص بك وتحميل مستند Word.

## الخطوة 2: تكوين خيارات حفظ PDF

بعد ذلك، ستحتاج إلى تكوين خيارات حفظ ملف PDF للتأكد من تصدير الإشارات المرجعية الموجودة في الرؤوس والتذييلات بشكل صحيح.

```csharp
PdfSaveOptions saveOptions = new PdfSaveOptions();
saveOptions.OutlineOptions.DefaultBookmarksOutlineLevel = 1;
saveOptions.HeaderFooterBookmarksExportMode = HeaderFooterBookmarksExportMode.First;
```

هنا، نقوم بإعداد `PdfSaveOptions`. ال `DefaultBookmarksOutlineLevel` تحدد الخاصية مستوى المخطط التفصيلي للإشارات المرجعية، و `HeaderFooterBookmarksExportMode` تضمن الخاصية أن يتم تصدير الظهور الأول فقط للإشارات المرجعية في الرؤوس والتذييلات.

## الخطوة 3: حفظ المستند بتنسيق PDF

وأخيرًا، احفظ مستندك بتنسيق PDF باستخدام الخيارات التي قمت بتكوينها.

```csharp
doc.Save(dataDir + "WorkingWithPdfSaveOptions.ExportHeaderFooterBookmarks.pdf", saveOptions);
```

في هذه الخطوة، ستقوم بحفظ المستند في المسار المحدد باستخدام الخيارات التي قمت بتكوينها.

## خاتمة

وهذا كل ما في الأمر! باتباع هذه الخطوات، يمكنك بسهولة تصدير الإشارات المرجعية من رؤوس وتذييلات مستند Word إلى ملف PDF باستخدام Aspose.Words لـ .NET. تضمن هذه الطريقة حفظ أدوات التنقل المهمة في مستندك بتنسيق PDF، مما يُسهّل على القراء التنقل عبره.

## الأسئلة الشائعة

### هل يمكنني تصدير كافة الإشارات المرجعية من مستند Word إلى PDF؟

نعم يمكنك ذلك. في `PdfSaveOptions`يمكنك تعديل الإعدادات لتشمل جميع الإشارات المرجعية إذا لزم الأمر.

### ماذا لو أردت تصدير الإشارات المرجعية من نص المستند أيضًا؟

يمكنك تكوين `OutlفيeOptions` in `PdfSaveOptions` لتضمين الإشارات المرجعية من نص المستند.

### هل من الممكن تخصيص مستويات الإشارات المرجعية في ملف PDF؟

بالتأكيد! يمكنك تخصيص `DefaultBookmarksOutlineLevel` خاصية لتعيين مستويات مختلفة للخطوط العريضة لإشاراتك المرجعية.

### كيف أتعامل مع المستندات التي لا تحتوي على إشارات مرجعية؟

إذا لم يكن مستندك يحتوي على إشارات مرجعية، فسيتم إنشاء ملف PDF بدون أي مخطط إشارات مرجعية. تأكد من احتواء مستندك على إشارات مرجعية إذا كنت بحاجة إليها في ملف PDF.

### هل يمكنني استخدام هذه الطريقة لأنواع أخرى من المستندات مثل DOCX أو RTF؟

نعم، يدعم Aspose.Words for .NET أنواعًا مختلفة من المستندات، بما في ذلك DOCX وRTF وغيرها.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}