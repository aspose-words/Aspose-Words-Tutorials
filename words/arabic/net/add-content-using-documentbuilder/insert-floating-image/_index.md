---
title: إدراج صورة عائمة في مستند Word
linktitle: إدراج صورة عائمة في مستند Word
second_title: واجهة برمجة تطبيقات معالجة المستندات Aspose.Words
description: تعرف على كيفية إدراج صورة عائمة في مستند Word باستخدام Aspose.Words for .NET من خلال هذا الدليل التفصيلي خطوة بخطوة. مثالي لتحسين مستنداتك.
weight: 10
url: /ar/net/add-content-using-documentbuilder/insert-floating-image/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# إدراج صورة عائمة في مستند Word

## مقدمة

تخيل إنشاء تقرير أو اقتراح مذهل حيث يتم وضع الصور بشكل مثالي لتكملة النص الخاص بك. مع Aspose.Words for .NET، يمكنك تحقيق ذلك دون عناء. توفر هذه المكتبة ميزات قوية لمعالجة المستندات، مما يجعلها حلاً مناسبًا للمطورين. في هذا البرنامج التعليمي، سنركز على إدراج صورة عائمة باستخدام فئة DocumentBuilder. سواء كنت مطورًا متمرسًا أو مبتدئًا، سيرشدك هذا الدليل خلال كل خطوة.

## المتطلبات الأساسية

قبل أن نبدأ، دعنا نتأكد من أن لديك كل ما تحتاجه للبدء:

1.  Aspose.Words لـ .NET: يمكنك تنزيل المكتبة من[صفحة إصدارات Aspose](https://releases.aspose.com/words/net/).
2. Visual Studio: أي إصدار يدعم تطوير .NET.
3. المعرفة الأساسية بلغة C#: إن فهم أساسيات برمجة C# سيكون مفيدًا.
4. ملف الصورة: ملف الصورة الذي تريد إدراجه، مثل شعار أو صورة.

## استيراد مساحات الأسماء

لاستخدام Aspose.Words في مشروعك، تحتاج إلى استيراد المساحات الأساسية اللازمة. يتم ذلك عن طريق إضافة الأسطر التالية في أعلى ملف C# الخاص بك:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
```

مع توفر هذه المتطلبات الأساسية ومساحات الأسماء، أصبحنا جاهزين لبدء البرنامج التعليمي الخاص بنا.

دعنا نقسم عملية إدراج صورة عائمة في مستند Word إلى خطوات يمكن إدارتها. سيتم شرح كل خطوة بالتفصيل لضمان قدرتك على المتابعة دون أي عوائق.

## الخطوة 1: إعداد مشروعك

أولاً، قم بإنشاء مشروع C# جديد في Visual Studio. يمكنك اختيار تطبيق وحدة التحكم لتبسيط الأمر.

1. افتح Visual Studio وأنشئ مشروعًا جديدًا.
2. حدد "تطبيق وحدة التحكم (.NET Core)" ثم انقر فوق "التالي".
3. قم بتسمية مشروعك واختر مكانًا لحفظه. انقر فوق "إنشاء".
4. قم بتثبيت Aspose.Words لـ .NET عبر NuGet Package Manager. انقر بزر الماوس الأيمن على مشروعك في مستكشف الحلول، وحدد "إدارة حزم NuGet"، وابحث عن "Aspose.Words". قم بتثبيت أحدث إصدار.

## الخطوة 2: تهيئة المستند وDocumentBuilder

الآن بعد أن تم إعداد مشروعك، دعنا نقوم بتهيئة كائنات Document وDocumentBuilder.

1.  إنشاء مثيل جديد من`Document` فصل:

```csharp
Document doc = new Document();
```

2. تهيئة كائن DocumentBuilder:

```csharp
DocumentBuilder builder = new DocumentBuilder(doc);
```

 ال`Document` يمثل الكائن مستند Word، و`DocumentBuilder` يساعد في إضافة المحتوى إليه.

## الخطوة 3: تحديد مسار الصورة

بعد ذلك، حدد المسار إلى ملف الصورة. تأكد من إمكانية الوصول إلى صورتك من دليل المشروع.

قم بتحديد دليل الصورة واسم ملف الصورة:

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
string imagePath = dataDir + "Transparent background logo.png";
```

 يستبدل`"YOUR DOCUMENT DIRECTORY"` مع المسار الفعلي الذي يتم تخزين صورتك فيه.

## الخطوة 4: إدراج الصورة العائمة

بعد إعداد كل شيء، دعنا نقوم بإدراج الصورة العائمة في المستند.

 استخدم`InsertImage` طريقة`DocumentBuilder` الفئة لإدراج الصورة:

```csharp
builder.InsertImage(imagePath,
   RelativeHorizontalPosition.Margin,
   100,
   RelativeVerticalPosition.Margin,
   100,
   200,
   100,
   WrapType.Square);
```

إليك ما يعنيه كل معلمة:
- `imagePath`:المسار إلى ملف الصورة الخاص بك.
- `RelativeHorizontalPosition.Margin`:الموضع الأفقي بالنسبة إلى الهامش.
- `100`:الإزاحة الأفقية من الهامش (بالنقاط).
- `RelativeVerticalPosition.Margin`:الموضع الرأسي بالنسبة إلى الهامش.
- `100`:الإزاحة الرأسية من الهامش (بالنقاط).
- `200`:عرض الصورة (بالنقاط).
- `100`:ارتفاع الصورة (بالنقاط).
- `WrapType.Square`:نمط التفاف النص حول الصورة.

## الخطوة 5: احفظ المستند

وأخيرًا، قم بحفظ المستند في الموقع المطلوب.

1. حدد مسار ملف الإخراج:

```csharp
string outputPath = dataDir + "AddContentUsingDocumentBuilder.InsertFloatingImage.docx";
```

2. حفظ المستند:

```csharp
doc.Save(outputPath);
```

الآن أصبح مستند Word الخاص بك الذي يحتوي على الصورة العائمة جاهزًا!

## خاتمة

إن إدراج صورة عائمة في مستند Word باستخدام Aspose.Words for .NET هي عملية بسيطة عندما يتم تقسيمها إلى خطوات يمكن إدارتها. باتباع هذا الدليل، يمكنك إضافة صور ذات مظهر احترافي إلى مستنداتك، مما يعزز جاذبيتها البصرية. يوفر Aspose.Words واجهة برمجة تطبيقات قوية تجعل معالجة المستندات سهلة، سواء كنت تعمل على التقارير أو المقترحات أو أي نوع آخر من المستندات.

## الأسئلة الشائعة

### هل يمكنني إدراج صور متعددة باستخدام Aspose.Words لـ .NET؟

 نعم، يمكنك إدراج صور متعددة عن طريق تكرار`InsertImage` طريقة لكل صورة مع المعلمات المطلوبة.

### كيف يمكنني تغيير موضع الصورة؟

 يمكنك تعديل`RelativeHorizontalPosition`, `RelativeVerticalPosition`، ومعلمات الإزاحة لتحديد موضع الصورة حسب الحاجة.

### ما هي أنواع التغليف الأخرى المتوفرة للصور؟

 يدعم Aspose.Words أنواعًا مختلفة من الالتفاف مثل`Inline`, `TopBottom`, `Tight`, `Through`، والمزيد. يمكنك اختيار الخيار الذي يناسب تخطيط مستندك بشكل أفضل.

### هل يمكنني استخدام تنسيقات مختلفة للصور؟

نعم، يدعم Aspose.Words مجموعة واسعة من تنسيقات الصور بما في ذلك JPEG، PNG، BMP، وGIF.

### كيف يمكنني الحصول على نسخة تجريبية مجانية من Aspose.Words لـ .NET؟

 يمكنك الحصول على نسخة تجريبية مجانية من[صفحة النسخة التجريبية المجانية من Aspose](https://releases.aspose.com/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
