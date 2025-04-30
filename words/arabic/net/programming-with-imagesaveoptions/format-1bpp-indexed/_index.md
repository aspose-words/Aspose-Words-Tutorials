---
"description": "تعرّف على كيفية تحويل مستند Word إلى صورة مفهرسة بحجم 1Bpp باستخدام Aspose.Words لـ .NET. اتبع دليلنا خطوة بخطوة لتسهيل التحويل."
"linktitle": "تنسيق 1Bpp مفهرس"
"second_title": "واجهة برمجة تطبيقات معالجة المستندات Aspose.Words"
"title": "تنسيق 1Bpp مفهرس"
"url": "/ar/net/programming-with-imagesaveoptions/format-1bpp-indexed/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# تنسيق 1Bpp مفهرس

## مقدمة

هل تساءلت يومًا عن كيفية حفظ مستند وورد كصورة بالأبيض والأسود باستخدام بضعة أسطر برمجية فقط؟ حسنًا، أنت محظوظ! اليوم، سنستعرض حيلة بسيطة وسهلة باستخدام Aspose.Words for .NET، والتي تتيح لك تحويل مستنداتك إلى صور مفهرسة بحجم بت واحد لكل صفحة. هذا التنسيق مثالي لأنواع معينة من الأرشفة الرقمية، والطباعة، أو عند الحاجة إلى توفير مساحة. سنشرح كل خطوة بالتفصيل لتسهيل الأمر. هل أنت مستعد للبدء؟ هيا بنا!

## المتطلبات الأساسية

قبل أن نبدأ في العمل، هناك بعض الأشياء التي يجب أن تكون موجودة في مكانها:

- Aspose.Words لـ .NET: تأكد من تثبيت المكتبة. يمكنك [قم بتحميله هنا](https://releases.aspose.com/words/net/).
- بيئة تطوير .NET: يعد Visual Studio خيارًا جيدًا، ولكن يمكنك استخدام أي بيئة تشعر بالراحة معها.
- المعرفة الأساسية بلغة C#: لا تقلق، سنبقي الأمر بسيطًا، ولكن القليل من الألفة مع لغة C# سوف يساعدك.
- مستند Word: احصل على مستند Word نموذجي جاهز للتحويل.

## استيراد مساحات الأسماء

أولاً، علينا استيراد مساحات الأسماء اللازمة. هذا أمر بالغ الأهمية لأنه يسمح لنا بالوصول إلى الفئات والأساليب التي نحتاجها من Aspose.Words.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

## الخطوة 1: إعداد دليل المستندات الخاص بك

ستحتاج إلى تحديد مسار مجلد مستندك. هذا هو المكان الذي يُخزَّن فيه مستند Word، وهو المكان الذي ستُحفَظ فيه الصورة المُحوَّلة.

```csharp
// المسار إلى دليل المستندات الخاص بك
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## الخطوة 2: تحميل مستند Word

الآن، دعنا نحمل مستند Word إلى Aspose.Words `Document` هذا الكائن يمثل ملف Word الخاص بك ويسمح لك بالتعامل معه.

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

## الخطوة 3: تكوين خيارات حفظ الصورة

بعد ذلك، نحتاج إلى إعداد `ImageSaveOptions`هنا يأتي السحر. سنُهيئه لحفظ الصورة بتنسيق PNG مع وضع ألوان مُفهرسة بدقة 1Bpp.

```csharp
ImageSaveOptions saveOptions = new ImageSaveOptions(SaveFormat.Png)
{
    PageSet = new PageSet(1),
    ImageColorMode = ImageColorMode.BlackAndWhite,
    PixelFormat = ImagePixelFormat.Format1bppIndexed
};
```

- SaveFormat.Png: يشير هذا إلى أننا نريد حفظ المستند كصورة PNG.
- PageSet(1): يشير هذا إلى أننا نقوم بتحويل الصفحة الأولى فقط.
- ImageColorMode.BlackAndWhite: يؤدي هذا إلى تعيين الصورة إلى اللونين الأبيض والأسود.
- ImagePixelFormat.Format1bppIndexed: يؤدي هذا إلى تعيين تنسيق الصورة إلى 1Bpp مفهرسة.

## الخطوة 4: حفظ المستند كصورة

وأخيرًا، نقوم بحفظ المستند كصورة باستخدام `Save` طريقة `Document` هدف.

```csharp
doc.Save(dataDir + "WorkingWithImageSaveOptions.Format1BppIndexed.Png", saveOptions);
```

## خاتمة

وها قد انتهيت! ببضعة أسطر برمجية فقط، حوّلت مستند Word الخاص بك إلى صورة مفهرسة بحجم 1Bpp باستخدام Aspose.Words لـ .NET. هذه الطريقة مفيدة للغاية لإنشاء صور عالية التباين وموفرة للمساحة من مستنداتك. الآن، يمكنك دمج هذه الطريقة بسهولة في مشاريعك وسير عملك. برمجة ممتعة!

## الأسئلة الشائعة

### ما هي الصورة المفهرسة 1Bpp؟
الصورة المفهرسة 1Bpp (1 بت لكل بكسل) هي تنسيق صورة بالأبيض والأسود حيث يتم تمثيل كل بكسل ببت واحد، إما 0 أو 1. هذا التنسيق فعال للغاية من حيث المساحة.

### هل يمكنني تحويل صفحات متعددة من مستند Word مرة واحدة؟
نعم، يمكنك ذلك. عدّل `PageSet` الممتلكات في `ImageSaveOptions` لتضمين صفحات متعددة أو المستند بأكمله.

### هل أحتاج إلى ترخيص لاستخدام Aspose.Words لـ .NET؟
نعم، يتطلب Aspose.Words for .NET ترخيصًا للعمل بكامل وظائفه. يمكنك الحصول على [رخصة مؤقتة هنا](https://purchase.aspose.com/temporary-license/).

### ما هي تنسيقات الصور الأخرى التي يمكنني تحويل مستند Word إليها؟
يدعم Aspose.Words تنسيقات صور متنوعة، بما في ذلك JPEG وBMP وTIFF. ما عليك سوى تغيير `SaveFormat` في `ImageSaveOptions`.

### أين يمكنني العثور على مزيد من الوثائق حول Aspose.Words لـ .NET؟
يمكنك العثور على وثائق مفصلة على [صفحة توثيق Aspose.Words لـ .NET](https://reference.aspose.com/words/net/).



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}