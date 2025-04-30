---
"description": "حوّل صفحات محددة من مستندات Word إلى صيغة JPEG بإعدادات مخصصة باستخدام Aspose.Words لـ .NET. تعلّم كيفية ضبط السطوع والتباين والدقة خطوة بخطوة."
"linktitle": "الحصول على نطاق صفحات Jpeg"
"second_title": "واجهة برمجة تطبيقات معالجة المستندات Aspose.Words"
"title": "الحصول على نطاق صفحات Jpeg"
"url": "/ar/net/programming-with-imagesaveoptions/get-jpeg-page-range/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# الحصول على نطاق صفحات Jpeg

## مقدمة

تحويل مستندات Word إلى صور مفيد للغاية، سواءً كنت تنشئ صورًا مصغّرة، أو تعاين مستندات عبر الإنترنت، أو تشارك المحتوى بتنسيق أسهل. مع Aspose.Words لـ .NET، يمكنك بسهولة تحويل صفحات محددة من مستندات Word إلى صيغة JPEG مع تخصيص إعدادات متنوعة مثل السطوع والتباين والدقة. لنبدأ في شرح كيفية تحقيق ذلك خطوة بخطوة!

## المتطلبات الأساسية

قبل أن نبدأ، ستحتاج إلى بعض الأشياء في مكانها:

- Aspose.Words لـ .NET: تأكد من تثبيت Aspose.Words لـ .NET. يمكنك [قم بتحميله هنا](https://releases.aspose.com/words/net/).
- بيئة التطوير: بيئة تطوير AC# مثل Visual Studio.
- نموذج مستند: مستند وورد للعمل عليه. يمكنك استخدام أي ملف .docx لهذا البرنامج التعليمي.
- المعرفة الأساسية بلغة C#: الإلمام ببرمجة C#.

بمجرد أن تكون هذه الأشياء جاهزة، فلنبدأ!

## استيراد مساحات الأسماء

لاستخدام Aspose.Words لـ .NET، ستحتاج إلى استيراد مساحات الأسماء اللازمة في بداية الكود. هذا يضمن لك الوصول إلى جميع الفئات والأساليب اللازمة لمعالجة المستندات.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

## الخطوة 1: تحميل المستند الخاص بك

أولاً، علينا تحميل مستند Word الذي نريد تحويله. لنفترض أن اسم مستندنا `Rendering.docx` ويقع في الدليل المحدد بواسطة العنصر النائب `YOUR DOCUMENT DIRECTORY`.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Rendering.docx");
```

يقوم هذا الكود بتهيئة المسار إلى مستندك وتحميله في Aspose.Words `Document` هدف.

## الخطوة 2: إعداد ImageSaveOptions

بعد ذلك، سنقوم بإعداد `ImageSaveOptions` لتحديد كيفية إنشاء ملف JPEG. يتضمن ذلك ضبط نطاق الصفحات، وسطوع الصورة، وتباينها، ودقتها.

```csharp
ImageSaveOptions options = new ImageSaveOptions(SaveFormat.Jpeg);
options.PageSet = new PageSet(0); // تحويل الصفحة الأولى فقط
options.ImageBrightness = 0.3f;   // ضبط السطوع
options.ImageContrast = 0.7f;     // ضبط التباين
options.HorizontalResolution = 72f; // تعيين الدقة
```

## الخطوة 3: حفظ المستند بتنسيق JPEG

وأخيرًا، نحفظ المستند كملف JPEG باستخدام الإعدادات التي حددناها.

```csharp
doc.Save(dataDir + "WorkingWithImageSaveOptions.GetJpegPageRange.jpeg", options);
```

هذا الكود يحفظ الصفحة الأولى من `Rendering.docx` كصورة JPEG مع إعدادات السطوع والتباين والدقة المحددة.

## خاتمة

وها أنت ذا! لقد نجحت في تحويل صفحة محددة من مستند Word إلى صورة JPEG بإعدادات مخصصة باستخدام Aspose.Words لـ .NET. يمكن تخصيص هذه العملية لتناسب احتياجات متنوعة، سواء كنت تُحضّر صورًا لموقع ويب، أو تُنشئ معاينات للمستندات، أو غير ذلك.

## الأسئلة الشائعة

### هل يمكنني تحويل صفحات متعددة في وقت واحد؟
نعم، يمكنك تحديد نطاق من الصفحات باستخدام `PageSet` الممتلكات في `ImageSaveOptions`.

### كيف أضبط جودة الصورة؟
يمكنك ضبط جودة JPEG باستخدام `JpegQuality` الممتلكات في `ImageSaveOptions`.

### هل يمكنني الحفظ بتنسيقات صور أخرى؟
نعم، يدعم Aspose.Words تنسيقات صور متنوعة مثل PNG وBMP وTIFF. غيّر `SaveFormat` في `ImageSaveOptions` وفقاً لذلك.

### هل هناك طريقة لمعاينة الصورة قبل الحفظ؟
سوف تحتاج إلى تنفيذ آلية المعاينة بشكل منفصل، حيث أن Aspose.Words لا يوفر ميزة المعاينة المضمنة.

### كيف أحصل على ترخيص مؤقت لـ Aspose.Words؟
يمكنك طلب [رخصة مؤقتة هنا](https://purchase.aspose.com/temporary-license/).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}