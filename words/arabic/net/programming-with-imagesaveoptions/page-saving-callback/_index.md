---
title: استدعاء حفظ الصفحة
linktitle: استدعاء حفظ الصفحة
second_title: واجهة برمجة تطبيقات معالجة المستندات Aspose.Words
description: تعلم كيفية حفظ كل صفحة من مستند Word كصورة PNG منفصلة باستخدام Aspose.Words لـ .NET مع دليلنا المفصل خطوة بخطوة.
weight: 10
url: /ar/net/programming-with-imagesaveoptions/page-saving-callback/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# استدعاء حفظ الصفحة

## مقدمة

مرحبًا! هل شعرت يومًا بالحاجة إلى حفظ كل صفحة من مستند Word كصور منفصلة؟ ربما تريد تقسيم تقرير كبير إلى صور مرئية سهلة الفهم، أو ربما تحتاج إلى إنشاء صور مصغرة للمعاينة. أياً كان السبب، فإن استخدام Aspose.Words for .NET يجعل هذه المهمة سهلة للغاية. في هذا الدليل، سنرشدك خلال عملية إعداد معاودة الاتصال لحفظ الصفحة لحفظ كل صفحة من المستند كصورة PNG فردية. دعنا نتعمق في الأمر!

## المتطلبات الأساسية

قبل أن نبدأ، تأكد من أن لديك ما يلي:

1.  Aspose.Words for .NET: إذا لم تقم بتنزيله وتثبيته بالفعل، فقم بذلك من[هنا](https://releases.aspose.com/words/net/).
2. Visual Studio: يجب أن يعمل أي إصدار، ولكنني سأستخدم Visual Studio 2019 لهذا الدليل.
3. المعرفة الأساسية بلغة C#: ستحتاج إلى فهم أساسي للغة C# للمتابعة.

## استيراد مساحات الأسماء

أولاً، نحتاج إلى استيراد مساحات الأسماء اللازمة. يساعدنا هذا في الوصول إلى الفئات والطرق المطلوبة دون الحاجة إلى كتابة مساحة الأسماء بالكامل في كل مرة.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;
```

## الخطوة 1: إعداد دليل المستندات الخاص بك

حسنًا، لنبدأ بتحديد المسار إلى دليل المستندات. هذا هو المكان الذي يوجد فيه مستند Word المدخل وحيث سيتم حفظ الصور الناتجة.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## الخطوة 2: قم بتحميل مستندك

بعد ذلك، سنقوم بتحميل المستند الذي تريد معالجته. تأكد من أن المستند ("Rendering.docx") موجود في الدليل المحدد.

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

## الخطوة 3: تكوين خيارات حفظ الصورة

نحتاج إلى تكوين خيارات حفظ الصور. في هذه الحالة، نقوم بحفظ الصفحات كملفات PNG.

```csharp
ImageSaveOptions imageSaveOptions = new ImageSaveOptions(SaveFormat.Png)
{
    PageSet = new PageSet(new PageRange(0, doc.PageCount - 1)),
    PageSavingCallback = new HandlePageSavingCallback()
};
```

 هنا،`PageSet` يحدد نطاق الصفحات المراد حفظها، و`PageSavingCallback` يشير إلى فئة الاستدعاء المخصصة لدينا.

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

 هذه الفئة تنفذ`IPageSavingCallback` الواجهة، وداخل`PageSaving` الطريقة هي أننا نقوم بتحديد نمط التسمية لكل صفحة محفوظة.

## الخطوة 5: حفظ المستند كصور

وأخيرًا، نحفظ المستند باستخدام الخيارات التي قمنا بإعدادها.

```csharp
doc.Save(dataDir + "WorkingWithImageSaveOptions.PageSavingCallback.png", imageSaveOptions);
```

## خاتمة

والآن، لقد نجحت في إعداد استدعاء حفظ الصفحة لحفظ كل صفحة من مستند Word كصورة PNG منفصلة باستخدام Aspose.Words for .NET. هذه التقنية مفيدة بشكل لا يصدق للعديد من التطبيقات، بدءًا من إنشاء معاينات الصفحات إلى إنشاء صور صفحات فردية للتقارير. 

برمجة سعيدة!

## الأسئلة الشائعة

### هل يمكنني حفظ الصفحات بتنسيقات غير PNG؟  
 نعم، يمكنك حفظ الصفحات بتنسيقات مختلفة مثل JPEG وBMP وTIFF عن طريق تغيير`SaveFormat` في`ImageSaveOptions`.

### ماذا لو أردت حفظ صفحات محددة فقط؟  
 يمكنك تحديد الصفحات التي تريد حفظها عن طريق ضبط`PageSet` المعلمة في`ImageSaveOptions`.

### هل من الممكن تخصيص جودة الصورة؟  
 بالتأكيد! يمكنك تعيين خصائص مثل`ImageSaveOptions.JpegQuality` للتحكم في جودة الصور الناتجة.

### كيف يمكنني التعامل مع المستندات الكبيرة بكفاءة؟  
بالنسبة للمستندات الكبيرة، فكر في معالجة الصفحات على دفعات لإدارة استخدام الذاكرة بشكل فعال.

### أين يمكنني العثور على مزيد من المعلومات حول Aspose.Words لـ .NET؟  
 تحقق من[التوثيق](https://reference.aspose.com/words/net/) للحصول على أدلة وأمثلة شاملة.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
