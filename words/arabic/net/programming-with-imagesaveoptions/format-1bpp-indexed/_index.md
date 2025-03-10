---
title: تنسيق 1Bpp مفهرس
linktitle: تنسيق 1Bpp مفهرس
second_title: واجهة برمجة تطبيقات معالجة المستندات Aspose.Words
description: تعرف على كيفية تحويل مستند Word إلى صورة مفهرسة بحجم 1Bpp باستخدام Aspose.Words for .NET. اتبع دليلنا خطوة بخطوة للتحويل السهل.
weight: 10
url: /ar/net/programming-with-imagesaveoptions/format-1bpp-indexed/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# تنسيق 1Bpp مفهرس

## مقدمة

هل تساءلت يومًا عن كيفية حفظ مستند Word كصورة بالأبيض والأسود باستخدام بضعة أسطر فقط من التعليمات البرمجية؟ حسنًا، أنت محظوظ! اليوم، سنتعرف على خدعة صغيرة أنيقة باستخدام Aspose.Words for .NET والتي تتيح لك تحويل مستنداتك إلى صور مفهرسة بحجم 1Bpp. هذا التنسيق مثالي لأنواع معينة من الأرشفة الرقمية أو الطباعة أو عندما تحتاج إلى توفير مساحة. سنقوم بتقسيم كل خطوة لجعلها سهلة للغاية. هل أنت مستعد للبدء؟ دعنا نتعمق!

## المتطلبات الأساسية

قبل أن نبدأ في العمل، هناك بعض الأشياء التي يجب أن تكون موجودة في مكانها:

-  Aspose.Words for .NET: تأكد من تثبيت المكتبة. يمكنك[تحميله هنا](https://releases.aspose.com/words/net/).
- بيئة تطوير .NET: يعد Visual Studio خيارًا جيدًا، ولكن يمكنك استخدام أي بيئة تشعر بالراحة معها.
- المعرفة الأساسية بلغة C#: لا تقلق، سنبقي الأمر بسيطًا، ولكن القليل من الألفة مع لغة C# سوف يساعدك.
- مستند Word: احصل على مستند Word نموذجي جاهز للتحويل.

## استيراد مساحات الأسماء

أولاً وقبل كل شيء، نحتاج إلى استيراد مساحات الأسماء الضرورية. وهذا أمر بالغ الأهمية لأنه يسمح لنا بالوصول إلى الفئات والطرق التي نحتاجها من Aspose.Words.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

## الخطوة 1: إعداد دليل المستندات الخاص بك

سوف تحتاج إلى تحديد المسار إلى دليل المستند الخاص بك. هذا هو المكان الذي يتم فيه تخزين مستند Word الخاص بك وحيث سيتم حفظ الصورة المحولة.

```csharp
// المسار إلى دليل المستند الخاص بك
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## الخطوة 2: تحميل مستند Word

 الآن، دعنا نحمل مستند Word إلى Aspose.Words`Document` هذا الكائن يمثل ملف Word الخاص بك ويسمح لك بالتعامل معه.

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

## الخطوة 3: تكوين خيارات حفظ الصورة

 بعد ذلك، نحتاج إلى إعداد`ImageSaveOptions`وهنا يحدث السحر. سنقوم بتكوينه لحفظ الصورة بتنسيق PNG مع وضع الألوان المفهرسة بمعدل 1Bpp.

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

 وأخيرًا، نقوم بحفظ المستند كصورة باستخدام`Save` طريقة`Document` هدف.

```csharp
doc.Save(dataDir + "WorkingWithImageSaveOptions.Format1BppIndexed.Png", saveOptions);
```

## خاتمة

والآن، لقد انتهيت! فباستخدام بضعة أسطر من التعليمات البرمجية، قمت بتحويل مستند Word الخاص بك إلى صورة مفهرسة بحجم 1Bpp باستخدام Aspose.Words for .NET. هذه الطريقة مفيدة بشكل لا يصدق لإنشاء صور عالية التباين وموفرة للمساحة من مستنداتك. والآن، يمكنك دمج هذه الطريقة بسهولة في مشاريعك وسير العمل الخاصة بك. أتمنى لك برمجة سعيدة!

## الأسئلة الشائعة

### ما هي الصورة المفهرسة 1Bpp؟
الصورة المفهرسة بدقة 1Bpp (بت واحد لكل بكسل) هي تنسيق صورة بالأبيض والأسود حيث يتم تمثيل كل بكسل ببت واحد، إما 0 أو 1. هذا التنسيق فعال للغاية من حيث المساحة.

### هل يمكنني تحويل عدة صفحات من مستند Word مرة واحدة؟
 نعم يمكنك ذلك. قم بتعديل`PageSet` الممتلكات في`ImageSaveOptions` لتضمين صفحات متعددة أو المستند بأكمله.

### هل أحتاج إلى ترخيص لاستخدام Aspose.Words لـ .NET؟
 نعم، يتطلب Aspose.Words for .NET ترخيصًا للحصول على الوظائف الكاملة. يمكنك الحصول على ترخيص[رخصة مؤقتة هنا](https://purchase.aspose.com/temporary-license/).

### ما هي تنسيقات الصور الأخرى التي يمكنني تحويل مستند Word إليها؟
 يدعم Aspose.Words تنسيقات الصور المختلفة بما في ذلك JPEG وBMP وTIFF. ما عليك سوى تغيير`SaveFormat` في`ImageSaveOptions`.

### أين يمكنني العثور على مزيد من الوثائق حول Aspose.Words لـ .NET؟
 يمكنك العثور على وثائق مفصلة على[صفحة توثيق Aspose.Words لـ .NET](https://reference.aspose.com/words/net/).

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
