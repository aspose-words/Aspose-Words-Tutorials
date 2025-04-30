---
"description": "تعرّف على كيفية إدراج صورة عائمة في مستند وورد باستخدام Aspose.Words لـ .NET من خلال هذا الدليل المفصل خطوة بخطوة. مثالي لتحسين مستنداتك."
"linktitle": "إدراج صورة عائمة في مستند Word"
"second_title": "واجهة برمجة تطبيقات معالجة المستندات Aspose.Words"
"title": "إدراج صورة عائمة في مستند Word"
"url": "/ar/net/add-content-using-documentbuilder/insert-floating-image/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# إدراج صورة عائمة في مستند Word

## مقدمة

تخيل إنشاء تقرير أو مقترح رائع، حيث تُوضع الصور بشكل مثالي لتُكمل نصك. مع Aspose.Words لـ .NET، يمكنك تحقيق ذلك بسهولة. تُوفر هذه المكتبة ميزات فعّالة لمعالجة المستندات، مما يجعلها الحل الأمثل للمطورين. في هذا البرنامج التعليمي، سنركز على إدراج صورة عائمة باستخدام فئة DocumentBuilder. سواء كنت مطورًا متمرسًا أو مبتدئًا، سيرشدك هذا الدليل خلال كل خطوة.

## المتطلبات الأساسية

قبل أن نبدأ، دعنا نتأكد من أن لديك كل ما تحتاجه للبدء:

1. Aspose.Words لـ .NET: يمكنك تنزيل المكتبة من [صفحة إصدارات Aspose](https://releases.aspose.com/words/net/).
2. Visual Studio: أي إصدار يدعم تطوير .NET.
3. المعرفة الأساسية بلغة C#: إن فهم أساسيات برمجة C# سيكون مفيدًا.
4. ملف الصورة: ملف الصورة الذي تريد إدراجه، مثل شعار أو صورة.

## استيراد مساحات الأسماء

لاستخدام Aspose.Words في مشروعك، عليك استيراد مساحات الأسماء اللازمة. يتم ذلك بإضافة الأسطر التالية في أعلى ملف C#:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
```

مع وضع هذه المتطلبات الأساسية ومساحات الأسماء في مكانها الصحيح، أصبحنا جاهزين لبدء البرنامج التعليمي الخاص بنا.

دعونا نُقسّم عملية إدراج صورة عائمة في مستند وورد إلى خطوات سهلة. سيتم شرح كل خطوة بالتفصيل لضمان سهولة متابعتها.

## الخطوة 1: إعداد مشروعك

أولاً، أنشئ مشروع C# جديدًا في Visual Studio. يمكنك اختيار تطبيق وحدة التحكم لتسهيل الأمر.

1. افتح Visual Studio وقم بإنشاء مشروع جديد.
2. حدد "تطبيق وحدة التحكم (.NET Core)" ثم انقر فوق "التالي".
3. سمِّ مشروعك واختر مكانًا لحفظه. انقر على "إنشاء".
4. ثبّت Aspose.Words لـ .NET عبر مدير حزم NuGet. انقر بزر الماوس الأيمن على مشروعك في مستكشف الحلول، ثم اختر "إدارة حزم NuGet"، وابحث عن "Aspose.Words". ثبّت أحدث إصدار.

## الخطوة 2: تهيئة المستند وDocumentBuilder

الآن بعد إعداد مشروعك، دعنا نقوم بتهيئة كائنات Document وDocumentBuilder.

1. إنشاء مثيل جديد من `Document` فصل:

```csharp
Document doc = new Document();
```

2. تهيئة كائن DocumentBuilder:

```csharp
DocumentBuilder builder = new DocumentBuilder(doc);
```

ال `Document` يمثل الكائن مستند Word، و `DocumentBuilder` يساعد في إضافة المحتوى إليه.

## الخطوة 3: تحديد مسار الصورة

بعد ذلك، حدد مسار ملف صورتك. تأكد من إمكانية الوصول إلى صورتك من دليل مشروعك.

قم بتحديد دليل الصورة واسم ملف الصورة:

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
string imagePath = dataDir + "Transparent background logo.png";
```

يستبدل `"YOUR DOCUMENT DIRECTORY"` مع المسار الفعلي الذي يتم تخزين صورتك فيه.

## الخطوة 4: إدراج الصورة العائمة

بعد إعداد كل شيء، دعنا نقوم بإدراج الصورة العائمة في المستند.

استخدم `InsertImage` طريقة `DocumentBuilder` الفئة لإدراج الصورة:

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
- `imagePath`:المسار إلى ملف صورتك.
- `RelativeHorizontalPosition.Margin`:الموضع الأفقي بالنسبة إلى الهامش.
- `100`:الإزاحة الأفقية من الهامش (بالنقاط).
- `RelativeVerticalPosition.Margin`:الموضع الرأسي بالنسبة للهامش.
- `100`:الإزاحة الرأسية من الهامش (بالنقاط).
- `200`:عرض الصورة (بالنقاط).
- `100`:ارتفاع الصورة (بالنقاط).
- `WrapType.Square`:نمط التفاف النص حول الصورة.

## الخطوة 5: حفظ المستند

وأخيرًا، احفظ المستند في الموقع المطلوب.

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

إدراج صورة عائمة في مستند وورد باستخدام Aspose.Words لـ .NET عملية سهلة وبسيطة، مقسمة إلى خطوات سهلة. باتباع هذا الدليل، يمكنك إضافة صور احترافية إلى مستنداتك، مما يُحسّن من جاذبيتها البصرية. يوفر Aspose.Words واجهة برمجة تطبيقات قوية تُسهّل التعامل مع المستندات، سواءً كنت تعمل على تقارير أو مقترحات أو أي نوع آخر من المستندات.

## الأسئلة الشائعة

### هل يمكنني إدراج صور متعددة باستخدام Aspose.Words لـ .NET؟

نعم، يمكنك إدراج صور متعددة عن طريق تكرار `InsertImage` طريقة لكل صورة مع المعلمات المطلوبة.

### كيف يمكنني تغيير موضع الصورة؟

يمكنك تعديل `RelativeHorizontalPosition`، `RelativeVerticalPosition`، ومعلمات الإزاحة لتحديد موضع الصورة حسب الحاجة.

### ما هي أنواع التغليف الأخرى المتوفرة للصور؟

يدعم Aspose.Words أنواعًا مختلفة من الالتفاف مثل `Inline`، `TopBottom`، `Tight`، `Through`والمزيد. يمكنك اختيار ما يناسب تخطيط مستندك.

### هل يمكنني استخدام تنسيقات صور مختلفة؟

نعم، يدعم Aspose.Words مجموعة واسعة من تنسيقات الصور بما في ذلك JPEG وPNG وBMP وGIF.

### كيف يمكنني الحصول على نسخة تجريبية مجانية من Aspose.Words لـ .NET؟

يمكنك الحصول على نسخة تجريبية مجانية من [صفحة التجربة المجانية لـ Aspose](https://releases.aspose.com/).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}