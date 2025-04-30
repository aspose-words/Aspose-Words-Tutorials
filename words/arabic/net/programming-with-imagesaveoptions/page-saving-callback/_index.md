---
"description": "تعلم كيفية حفظ كل صفحة من مستند Word كصورة PNG منفصلة باستخدام Aspose.Words لـ .NET مع دليلنا المفصل خطوة بخطوة."
"linktitle": "استدعاء حفظ الصفحة"
"second_title": "واجهة برمجة تطبيقات معالجة المستندات Aspose.Words"
"title": "استدعاء حفظ الصفحة"
"url": "/ar/net/programming-with-imagesaveoptions/page-saving-callback/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# استدعاء حفظ الصفحة

## مقدمة

أهلاً! هل شعرتَ يومًا بالحاجة إلى حفظ كل صفحة من مستند Word كصور منفصلة؟ ربما ترغب في تقسيم تقرير كبير إلى صور سهلة الفهم، أو ربما تحتاج إلى إنشاء صور مصغّرة للمعاينة. مهما كان سببك، فإن استخدام Aspose.Words لـ .NET يُسهّل هذه المهمة. في هذا الدليل، سنشرح لك عملية إعداد استدعاء حفظ الصفحات لحفظ كل صفحة من المستند كصورة PNG مستقلة. لنبدأ!

## المتطلبات الأساسية

قبل أن نبدأ، تأكد من أن لديك ما يلي:

1. Aspose.Words لـ .NET: إذا لم تقم بذلك بالفعل، فقم بتنزيله وتثبيته من [هنا](https://releases.aspose.com/words/net/).
2. Visual Studio: يجب أن يعمل أي إصدار، ولكنني سأستخدم Visual Studio 2019 لهذا الدليل.
3. المعرفة الأساسية بلغة C#: ستحتاج إلى فهم أساسي للغة C# للمتابعة.

## استيراد مساحات الأسماء

أولاً، علينا استيراد مساحات الأسماء اللازمة. هذا يُمكّننا من الوصول إلى الفئات والأساليب المطلوبة دون الحاجة إلى كتابة مساحة الأسماء كاملةً في كل مرة.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;
```

## الخطوة 1: إعداد دليل المستندات الخاص بك

حسنًا، لنبدأ بتحديد مسار مجلد المستندات. هذا هو المكان الذي يوجد فيه مستند Word المُدخل، وهو المكان الذي ستُحفظ فيه صور المخرجات.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## الخطوة 2: تحميل المستند الخاص بك

بعد ذلك، سنحمّل المستند الذي تريد معالجته. تأكد من وجود مستندك (Rendering.docx) في المجلد المحدد.

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

## الخطوة 3: تكوين خيارات حفظ الصورة

نحتاج إلى ضبط خيارات حفظ الصور. في هذه الحالة، سنحفظ الصفحات كملفات PNG.

```csharp
ImageSaveOptions imageSaveOptions = new ImageSaveOptions(SaveFormat.Png)
{
    PageSet = new PageSet(new PageRange(0, doc.PageCount - 1)),
    PageSavingCallback = new HandlePageSavingCallback()
};
```

هنا، `PageSet` يحدد نطاق الصفحات التي سيتم حفظها، و `PageSavingCallback` يشير إلى فئة الاستدعاء المخصصة لدينا.

## الخطوة 4: تنفيذ استدعاء حفظ الصفحة

الآن، دعنا ننفذ فئة الاستدعاء التي تتعامل مع كيفية حفظ كل صفحة.

```csharp
private class HandlePageSavingCallback : IPageSavingCallback
{
    public void PageSaving(PageSavingArgs args)
    {
        args.PageFileName = string.Format(dataDir + "Page_{0}.png", args.PageIndex);
    }
}
```

هذه الفئة تنفذ `IPageSavingCallback` الواجهة، وداخل `PageSaving` الطريقة هي أننا نقوم بتحديد نمط التسمية لكل صفحة محفوظة.

## الخطوة 5: حفظ المستند كصور

وأخيرًا، نقوم بحفظ المستند باستخدام الخيارات التي قمنا بتكوينها.

```csharp
doc.Save(dataDir + "WorkingWithImageSaveOptions.PageSavingCallback.png", imageSaveOptions);
```

## خاتمة

وها أنت ذا! لقد نجحت في إعداد استدعاء حفظ الصفحات لحفظ كل صفحة من مستند Word كصورة PNG منفصلة باستخدام Aspose.Words لـ .NET. هذه التقنية مفيدة للغاية لتطبيقات متنوعة، بدءًا من إنشاء معاينات الصفحات ووصولًا إلى إنشاء صور صفحات فردية للتقارير. 

برمجة سعيدة!

## الأسئلة الشائعة

### هل يمكنني حفظ الصفحات بتنسيقات أخرى غير PNG؟  
نعم، يمكنك حفظ الصفحات بتنسيقات مختلفة مثل JPEG وBMP وTIFF عن طريق تغيير `SaveFormat` في `ImageSaveOptions`.

### ماذا لو أردت حفظ صفحات محددة فقط؟  
يمكنك تحديد الصفحات التي تريد حفظها عن طريق تعديل `PageSet` المعلمة في `ImageSaveOptions`.

### هل من الممكن تخصيص جودة الصورة؟  
بالتأكيد! يمكنك تعيين خصائص مثل `ImageSaveOptions.JpegQuality` للتحكم في جودة الصور الناتجة.

### كيف يمكنني التعامل مع المستندات الكبيرة بكفاءة؟  
بالنسبة للمستندات الكبيرة، فكر في معالجة الصفحات على دفعات لإدارة استخدام الذاكرة بشكل فعال.

### أين يمكنني العثور على مزيد من المعلومات حول Aspose.Words لـ .NET؟  
تحقق من [التوثيق](https://reference.aspose.com/words/net/) للحصول على أدلة وأمثلة شاملة.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}