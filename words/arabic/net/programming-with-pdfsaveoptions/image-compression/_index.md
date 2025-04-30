---
"description": "تعرّف على كيفية ضغط الصور في مستندات PDF باستخدام Aspose.Words لـ .NET. اتبع هذا الدليل لتحسين حجم الملف وجودته."
"linktitle": "ضغط الصور في مستند PDF"
"second_title": "واجهة برمجة تطبيقات معالجة المستندات Aspose.Words"
"title": "ضغط الصور في مستند PDF"
"url": "/ar/net/programming-with-pdfsaveoptions/image-compression/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# ضغط الصور في مستند PDF

## مقدمة

في عصرنا الرقمي، تُعدّ إدارة حجم المستندات أمرًا بالغ الأهمية لتحسين الأداء وكفاءة التخزين. سواء كنت تتعامل مع تقارير ضخمة أو عروض تقديمية معقدة، فإن تقليل حجم الملف دون المساس بالجودة أمرٌ أساسي. يُعد ضغط الصور في مستندات PDF تقنيةً أساسيةً لتحقيق هذا الهدف. إذا كنت تستخدم Aspose.Words لـ .NET، فأنت محظوظ! سيرشدك هذا البرنامج التعليمي خلال عملية ضغط الصور في مستندات PDF باستخدام Aspose.Words لـ .NET. سنستكشف خيارات الضغط المختلفة وكيفية تطبيقها بفعالية لضمان تحسين جودة وحجم ملفات PDF.

## المتطلبات الأساسية

قبل الغوص في البرنامج التعليمي، تأكد من أن لديك المتطلبات الأساسية التالية:

1. Aspose.Words لـ .NET: يجب تثبيت Aspose.Words لـ .NET. يمكنك تنزيله من [موقع Aspose](https://releases.aspose.com/words/net/).

2. المعرفة الأساسية بلغة C#: ستساعدك المعرفة ببرمجة C# على فهم أمثلة التعليمات البرمجية المقدمة في هذا البرنامج التعليمي.

3. بيئة التطوير: تأكد من إعداد بيئة تطوير .NET، مثل Visual Studio.

4. مستند نموذجي: قم بإعداد مستند Word نموذجي (على سبيل المثال، "Rendering.docx") جاهزًا لاختبار ضغط الصورة.

5. ترخيص Aspose: إذا كنت تستخدم إصدارًا مرخصًا من Aspose.Words لـ .NET، فتأكد من إعداد الترخيص بشكل صحيح. إذا كنت بحاجة إلى ترخيص مؤقت، يمكنك الحصول عليه من [صفحة الترخيص المؤقت لـ Aspose](https://purchase.aspose.com/temporary-license/).

## استيراد مساحات الأسماء

للبدء بضغط الصور في مستندات PDF باستخدام Aspose.Words لـ .NET، عليك استيراد مساحات الأسماء اللازمة. إليك الطريقة:

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

توفر هذه المساحات الاسمية إمكانية الوصول إلى الوظائف الأساسية اللازمة لمعالجة مستندات Word وحفظها بتنسيق PDF مع خيارات مختلفة.

## الخطوة 1: إعداد دليل المستندات الخاص بك

قبل البدء بالبرمجة، حدد مسار مجلد المستندات. سيساعدك هذا على تحديد موقع ملفاتك وحفظها بسهولة.

```csharp
// المسار إلى دليل المستندات.
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

يستبدل `"YOUR DOCUMENT DIRECTORY"` مع المسار الذي يتم تخزين مستند العينة الخاص بك فيه.

## الخطوة 2: تحميل مستند Word

بعد ذلك، قم بتحميل مستند Word الخاص بك إلى `Aspose.Words.Document` هذا سيسمح لك بالعمل مع المستند برمجيًا.

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

هنا، `"Rendering.docx"` هو اسم مستند Word النموذجي. تأكد من وجود هذا الملف في الدليل المحدد.

## الخطوة 3: تكوين ضغط الصورة الأساسي

إنشاء `PdfSaveOptions` لتكوين خيارات حفظ ملف PDF، بما في ذلك ضغط الصور. اضبط `ImageCompression` الممتلكات إلى `PdfImageCompression.Jpeg` لاستخدام ضغط JPEG للصور.

```csharp
PdfSaveOptions saveOptions = new PdfSaveOptions
{
	// ضغط الصور باستخدام JPEG
    ImageCompression = PdfImageCompression.Jpeg,
	// اختياري: الحفاظ على حقول النموذج في ملف PDF
    PreserveFormFields = true
};
```

## الخطوة 4: حفظ المستند باستخدام الضغط الأساسي

احفظ مستند Word كملف PDF باستخدام خيارات ضغط الصور المُعدّة. سيؤدي هذا إلى تطبيق ضغط JPEG على الصور في ملف PDF.

```csharp
doc.Save(dataDir + "WorkingWithPdfSaveOptions.PdfImageCompression.pdf", saveOptions);
```

في هذا المثال، تم تسمية ملف PDF الناتج `"WorkingWithPdfSaveOptions.PdfImageCompression.pdf"`. قم بتعديل اسم الملف حسب الحاجة.

## الخطوة 5: تكوين الضغط المتقدم مع التوافق مع PDF/A

لتحسين الضغط، خاصةً إذا كنت بحاجة إلى الامتثال لمعايير PDF/A، يمكنك تكوين خيارات إضافية. اضبط `Compliance` الممتلكات إلى `PdfCompliance.PdfA2u` وضبط `JpegQuality` ملكية.

```csharp
PdfSaveOptions saveOptionsA2U = new PdfSaveOptions
{
	// ضبط التوافق مع PDF/A-2u
    Compliance = PdfCompliance.PdfA2u,
	// استخدم ضغط JPEG
    ImageCompression = PdfImageCompression.Jpeg,
	// ضبط جودة JPEG للتحكم في مستوى الضغط
    JpegQuality = 100 
};
```

## الخطوة 6: حفظ المستند باستخدام الضغط المتقدم

احفظ مستند Word كملف PDF باستخدام إعدادات الضغط المتقدمة. يضمن هذا الإعداد توافق ملف PDF مع معايير PDF/A واستخدام ضغط JPEG عالي الجودة.

```csharp
doc.Save(dataDir + "WorkingWithPdfSaveOptions.PdfImageCompression_A2u.pdf", saveOptionsA2U);
```

هنا، يتم تسمية ملف PDF الناتج `"WorkingWithPdfSaveOptions.PdfImageCompression_A2u.pdf"`. قم بتعديل اسم الملف وفقًا لتفضيلاتك.

## خاتمة

يُعدّ تقليل حجم مستندات PDF عن طريق ضغط الصور خطوةً أساسيةً لتحسين أداء المستندات وتخزينها. مع Aspose.Words لـ .NET، تتوفر لك أدوات فعّالة للتحكم في ضغط الصور بفعالية. باتباع الخطوات الموضحة في هذا البرنامج التعليمي، يمكنك ضمان جودة عالية وضغط مُحكم لمستندات PDF الخاصة بك. سواءً كنت تحتاج إلى ضغط أساسي أو متقدم، يوفر Aspose.Words المرونة اللازمة لتلبية احتياجاتك.


## الأسئلة الشائعة

### ما هو ضغط الصور في ملفات PDF؟
يؤدي ضغط الصور إلى تقليل حجم ملفات مستندات PDF عن طريق تقليل جودة الصور، مما يساعد في تحسين التخزين والأداء.

### كيف يتعامل Aspose.Words for .NET مع ضغط الصور؟
يوفر Aspose.Words لـ .NET `PdfSaveOptions` الفئة، التي تسمح لك بتعيين خيارات ضغط الصور المختلفة، بما في ذلك ضغط JPEG.

### هل يمكنني استخدام Aspose.Words لـ .NET للامتثال لمعايير PDF/A؟
نعم، يدعم Aspose.Words التوافق مع تنسيق PDF/A، مما يسمح لك بحفظ المستندات بتنسيقات تلبي معايير الأرشفة والحفظ على المدى الطويل.

### ما هو تأثير جودة JPEG على حجم ملف PDF؟
تؤدي إعدادات جودة JPEG الأعلى إلى الحصول على جودة صورة أفضل ولكن أحجام ملفات أكبر، بينما تؤدي إعدادات الجودة المنخفضة إلى تقليل حجم الملف ولكن قد تؤثر على وضوح الصورة.

### أين يمكنني العثور على مزيد من المعلومات حول Aspose.Words لـ .NET؟
يمكنك استكشاف المزيد حول Aspose.Words for .NET على موقعهم [التوثيق](https://reference.aspose.com/words/net/)، [يدعم](https://forum.aspose.com/c/words/8)، و [تحميل](https://releases.aspose.com/words/net/) الصفحات.

### نموذج كود المصدر لضغط الصور باستخدام Aspose.Words لـ .NET

```csharp

// المسار إلى دليل المستندات.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Rendering.docx");

PdfSaveOptions saveOptions = new PdfSaveOptions
{
	ImageCompression = PdfImageCompression.Jpeg, PreserveFormFields = true
};

doc.Save(dataDir + "WorkingWithPdfSaveOptions.PdfImageCompression.pdf", saveOptions);

PdfSaveOptions saveOptionsA2U = new PdfSaveOptions
{
	Compliance = PdfCompliance.PdfA2u,
	ImageCompression = PdfImageCompression.Jpeg,
	JpegQuality = 100, // استخدم ضغط JPEG بجودة 50% لتقليل حجم الملف.
};



doc.Save(dataDir + "WorkingWithPdfSaveOptions.PdfImageCompression_A2u.pdf", saveOptionsA2U);
	
```


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}