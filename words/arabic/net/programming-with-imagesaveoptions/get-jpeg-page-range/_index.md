---
title: الحصول على نطاق الصفحات بتنسيق Jpeg
linktitle: الحصول على نطاق الصفحات بتنسيق Jpeg
second_title: واجهة برمجة تطبيقات معالجة المستندات Aspose.Words
description: قم بتحويل صفحات معينة من مستندات Word إلى تنسيق JPEG باستخدام إعدادات مخصصة باستخدام Aspose.Words for .NET. تعرف على كيفية ضبط السطوع والتباين والدقة خطوة بخطوة.
weight: 10
url: /ar/net/programming-with-imagesaveoptions/get-jpeg-page-range/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# الحصول على نطاق الصفحات بتنسيق Jpeg

## مقدمة

يمكن أن يكون تحويل مستندات Word إلى صور مفيدًا بشكل لا يصدق، سواء كنت تقوم بإنشاء صور مصغرة أو معاينة مستندات عبر الإنترنت أو مشاركة المحتوى بتنسيق أكثر سهولة في الوصول إليه. باستخدام Aspose.Words for .NET، يمكنك بسهولة تحويل صفحات معينة من مستندات Word إلى تنسيق JPEG مع تخصيص إعدادات مختلفة مثل السطوع والتباين والدقة. دعنا نتعمق في كيفية تحقيق ذلك خطوة بخطوة!

## المتطلبات الأساسية

قبل أن نبدأ، ستحتاج إلى بعض الأشياء:

-  Aspose.Words for .NET: تأكد من تثبيت Aspose.Words for .NET. يمكنك[تحميله هنا](https://releases.aspose.com/words/net/).
- بيئة التطوير: بيئة تطوير AC# مثل Visual Studio.
- مستند نموذجي: مستند Word للعمل عليه. يمكنك استخدام أي ملف .docx لهذا البرنامج التعليمي.
- المعرفة الأساسية بلغة C#: الإلمام ببرمجة C#.

بمجرد أن تكون هذه الأشياء جاهزة، فلنبدأ!

## استيراد مساحات الأسماء

لاستخدام Aspose.Words لـ .NET، ستحتاج إلى استيراد المساحات الأساسية اللازمة في بداية الكود الخاص بك. يضمن هذا إمكانية وصولك إلى جميع الفئات والطرق المطلوبة لمعالجة المستندات.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

## الخطوة 1: قم بتحميل مستندك

أولاً، نحتاج إلى تحميل مستند Word الذي نريد تحويله. لنفترض أن اسم المستند هو`Rendering.docx` ويقع في الدليل المحدد بواسطة العنصر النائب`YOUR DOCUMENT DIRECTORY`.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Rendering.docx");
```

 يقوم هذا الكود بتهيئة المسار إلى مستندك وتحميله في Aspose.Words`Document` هدف.

## الخطوة 2: إعداد ImageSaveOptions

 بعد ذلك، سنقوم بإعداد`ImageSaveOptions` لتحديد كيفية إنشاء ملف JPEG الذي نريده. ويتضمن ذلك ضبط نطاق الصفحة وسطوع الصورة والتباين والدقة.

```csharp
ImageSaveOptions options = new ImageSaveOptions(SaveFormat.Jpeg);
options.PageSet = new PageSet(0); // تحويل الصفحة الأولى فقط
options.ImageBrightness = 0.3f;   // ضبط السطوع
options.ImageContrast = 0.7f;     // ضبط التباين
options.HorizontalResolution = 72f; // تعيين الدقة
```

## الخطوة 3: حفظ المستند بصيغة JPEG

وأخيرًا، نحفظ المستند كملف JPEG باستخدام الإعدادات التي حددناها.

```csharp
doc.Save(dataDir + "WorkingWithImageSaveOptions.GetJpegPageRange.jpeg", options);
```

 هذا الكود يحفظ الصفحة الأولى من`Rendering.docx` كصورة JPEG مع إعدادات السطوع والتباين والدقة المحددة.

## خاتمة

والآن، لقد نجحت في تحويل صفحة معينة من مستند Word إلى صورة بتنسيق JPEG باستخدام إعدادات مخصصة باستخدام Aspose.Words for .NET. ويمكن تخصيص هذه العملية لتناسب احتياجات مختلفة، سواء كنت تقوم بإعداد صور لموقع ويب أو إنشاء معاينات للمستندات أو أكثر.

## الأسئلة الشائعة

### هل يمكنني تحويل صفحات متعددة في وقت واحد؟
 نعم، يمكنك تحديد نطاق من الصفحات باستخدام`PageSet` الممتلكات في`ImageSaveOptions`.

### كيف أضبط جودة الصورة؟
 يمكنك ضبط جودة JPEG باستخدام`JpegQuality` الممتلكات في`ImageSaveOptions`.

### هل يمكنني الحفظ بتنسيقات أخرى للصورة؟
 نعم، يدعم Aspose.Words تنسيقات الصور المختلفة مثل PNG وBMP وTIFF. قم بتغيير`SaveFormat` في`ImageSaveOptions` وفقاً لذلك.

### هل هناك طريقة لمعاينة الصورة قبل الحفظ؟
سوف تحتاج إلى تنفيذ آلية المعاينة بشكل منفصل، حيث أن Aspose.Words لا يوفر ميزة معاينة مضمنة.

### كيف يمكنني الحصول على ترخيص مؤقت لـ Aspose.Words؟
 يمكنك طلب[رخصة مؤقتة هنا](https://purchase.aspose.com/temporary-license/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
