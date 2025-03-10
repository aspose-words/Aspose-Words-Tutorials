---
title: وحدة القياس
linktitle: وحدة القياس
second_title: واجهة برمجة تطبيقات معالجة المستندات Aspose.Words
description: تعرف على كيفية تكوين ميزة وحدة القياس في Aspose.Words لـ .NET للحفاظ على تنسيق المستند أثناء تحويل ODT.
weight: 10
url: /ar/net/programming-with-odtsaveoptions/measure-unit/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# وحدة القياس

## مقدمة

هل سبق لك أن اضطررت إلى تحويل مستندات Word إلى تنسيقات مختلفة ولكنك كنت بحاجة إلى وحدة قياس محددة لتخطيطك؟ سواء كنت تتعامل مع البوصات أو السنتيمترات أو النقاط، فإن التأكد من أن مستندك يحافظ على سلامته أثناء عملية التحويل أمر بالغ الأهمية. في هذا البرنامج التعليمي، سنشرح كيفية تكوين ميزة وحدة القياس في Aspose.Words لـ .NET. تضمن هذه الميزة القوية الحفاظ على تنسيق مستندك تمامًا كما تحتاج إليه عند التحويل إلى تنسيق ODT (نص المستند المفتوح).

## المتطلبات الأساسية

قبل الغوص في الكود، هناك بعض الأشياء التي ستحتاجها للبدء:

1. Aspose.Words for .NET: تأكد من تثبيت أحدث إصدار من Aspose.Words for .NET. إذا لم يكن لديك الإصدار بعد، فيمكنك تنزيله من[هنا](https://releases.aspose.com/words/net/).
2. بيئة التطوير: بيئة تطوير متكاملة مثل Visual Studio لكتابة وتنفيذ كود C#.
3. المعرفة الأساسية للغة C#: إن فهم أساسيات لغة C# سوف يساعدك على متابعة البرنامج التعليمي.
4. مستند Word: قم بإعداد مستند Word نموذجي يمكنك استخدامه للتحويل.

## استيراد مساحات الأسماء

قبل أن نبدأ في كتابة التعليمات البرمجية، دعنا نتأكد من استيراد مساحات الأسماء الضرورية. أضف هذه باستخدام التوجيهات في أعلى ملف التعليمات البرمجية الخاص بك:

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

## الخطوة 1: إعداد دليل المستندات الخاص بك

أولاً، عليك تحديد المسار إلى دليل المستند. هذا هو المكان الذي يوجد فيه مستند Word الخاص بك والذي سيتم حفظ الملف المحول فيه.

```csharp
// المسار إلى دليل المستندات الخاص بك
string dataDir = "YOUR DOCUMENTS DIRECTORY";
```

 يستبدل`"YOUR DOCUMENTS DIRECTORY"` مع المسار الفعلي إلى الدليل الخاص بك. وهذا يضمن أن الكود الخاص بك يعرف مكان العثور على مستند Word الخاص بك.

## الخطوة 2: تحميل مستند Word

 بعد ذلك، تحتاج إلى تحميل مستند Word الذي تريد تحويله. يتم ذلك باستخدام`Document` فئة من Aspose.Words.

```csharp
// تحميل مستند Word
Document doc = new Document(dataDir + "Document.docx");
```

تأكد من أن مستند Word الخاص بك، المسمى "Document.docx"، موجود في الدليل المحدد.

## الخطوة 3: تكوين وحدة القياس

 الآن، دعنا نحدد وحدة القياس لتحويل ODT. وهنا يحدث السحر. سنقوم بإعداد`OdtSaveOptions` استخدام البوصات كوحدة قياس.

```csharp
// تكوين خيارات النسخ الاحتياطي باستخدام ميزة "وحدة القياس"
OdtSaveOptions saveOptions = new OdtSaveOptions { MeasureUnit = OdtSaveMeasureUnit.Inches };
```

 في هذا المثال، نقوم بتعيين وحدة القياس إلى البوصات. يمكنك أيضًا اختيار وحدات أخرى مثل`OdtSaveMeasureUnit.Centimeters` أو`OdtSaveMeasureUnit.Points` اعتمادا على متطلباتك.

## الخطوة 4: تحويل المستند إلى ODT

 أخيرًا، سنقوم بتحويل مستند Word إلى تنسيق ODT باستخدام التنسيق الذي تم تكوينه`OdtSaveOptions`.

```csharp
// تحويل المستند إلى ODT
doc.Save(dataDir + "WorkingWithOdtSaveOptions.MeasureUnit.odt", saveOptions);
```

يحفظ هذا السطر من التعليمات البرمجية المستند المُحوّل في الدليل المحدد مع تطبيق وحدة القياس الجديدة.

## خاتمة

والآن، إليك ما تحتاج إليه! باتباع هذه الخطوات، يمكنك بسهولة تكوين ميزة وحدة القياس في Aspose.Words for .NET لضمان الحفاظ على تخطيط مستندك أثناء التحويل. سواء كنت تعمل بالبوصات أو السنتيمترات أو النقاط، فقد أظهر لك هذا البرنامج التعليمي كيفية التحكم في تنسيق مستندك بسهولة.

## الأسئلة الشائعة

### ما هو Aspose.Words لـ .NET؟
Aspose.Words for .NET هي مكتبة قوية للعمل مع مستندات Word برمجيًا. وهي تسمح للمطورين بإنشاء مستندات Word وتعديلها وتحويلها ومعالجتها دون الحاجة إلى Microsoft Word.

### هل يمكنني استخدام وحدات قياس أخرى غير البوصة؟
 نعم، يدعم Aspose.Words for .NET وحدات قياس أخرى مثل السنتيمترات والنقط. يمكنك تحديد الوحدة المطلوبة باستخدام`OdtSaveMeasureUnit` تعداد.

### هل هناك نسخة تجريبية مجانية متاحة لـ Aspose.Words لـ .NET؟
 نعم، يمكنك تنزيل نسخة تجريبية مجانية من Aspose.Words لـ .NET من[هنا](https://releases.aspose.com/).

### أين يمكنني العثور على وثائق Aspose.Words لـ .NET؟
 يمكنك الوصول إلى الوثائق الشاملة لـ Aspose.Words لـ .NET على[هذا الرابط](https://reference.aspose.com/words/net/).

### كيف يمكنني الحصول على الدعم لـ Aspose.Words لـ .NET؟
 للحصول على الدعم، يمكنك زيارة منتدى Aspose.Words على[هذا الرابط](https://forum.aspose.com/c/words/8).

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
