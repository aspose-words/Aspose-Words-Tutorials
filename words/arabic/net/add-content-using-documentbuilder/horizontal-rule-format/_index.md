---
title: تنسيق الخط الأفقي في مستند Word
linktitle: تنسيق الخط الأفقي في مستند Word
second_title: واجهة برمجة تطبيقات معالجة المستندات Aspose.Words
description: تعرف على كيفية إدراج قواعد أفقية قابلة للتخصيص في مستندات Word باستخدام Aspose.Words for .NET. قم بتعزيز أتمتة المستندات لديك.
weight: 10
url: /ar/net/add-content-using-documentbuilder/horizontal-rule-format/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# تنسيق الخط الأفقي في مستند Word

## مقدمة

في عالم تطوير .NET، قد يكون التعامل مع مستندات Word وتنسيقها برمجيًا مهمة شاقة. لحسن الحظ، يوفر Aspose.Words for .NET حلاً قويًا، مما يمكّن المطورين من أتمتة إنشاء المستندات وتحريرها وإدارتها بسهولة. تتعمق هذه المقالة في إحدى الميزات الأساسية: إدراج قواعد أفقية في مستندات Word. سواء كنت مطورًا متمرسًا أو بدأت للتو في استخدام Aspose.Words، فإن إتقان هذه الإمكانية سيعزز عملية إنشاء المستندات لديك.

## المتطلبات الأساسية

قبل الغوص في تنفيذ القواعد الأفقية باستخدام Aspose.Words لـ .NET، تأكد من توفر المتطلبات الأساسية التالية:

- Visual Studio: تثبيت Visual Studio IDE لتطوير .NET.
- Aspose.Words for .NET: قم بتنزيل Aspose.Words for .NET وتثبيته من[هنا](https://releases.aspose.com/words/net/).
- المعرفة الأساسية بلغة C#: الإلمام بأساسيات لغة البرمجة C#.
-  فئة DocumentBuilder: فهم`DocumentBuilder` فئة في Aspose.Words لمعالجة المستندات.

## استيراد مساحات الأسماء

للبدء، قم باستيراد المساحات الأساسية اللازمة في مشروع C# الخاص بك:

```csharp
using Aspose.Words;
using System.Drawing;
```

توفر هذه المساحات الاسمية إمكانية الوصول إلى فئات Aspose.Words للتعامل مع المستندات وفئات .NET القياسية للتعامل مع الألوان.

دعونا نقوم بتقسيم عملية إضافة قاعدة أفقية في مستند Word باستخدام Aspose.Words لـ .NET إلى خطوات شاملة:

## الخطوة 1: تهيئة DocumentBuilder وتعيين الدليل

 أولاً، قم بتهيئة`DocumentBuilder` الكائن وتعيين مسار الدليل الذي سيتم حفظ المستند فيه.

```csharp
string dataDir = "YOUR_DOCUMENT_DIRECTORY_PATH";
DocumentBuilder builder = new DocumentBuilder();
```

## الخطوة 2: إدراج خط أفقي

 استخدم`InsertHorizontalRule()` طريقة`DocumentBuilder` فئة لإضافة قاعدة أفقية.

```csharp
Shape shape = builder.InsertHorizontalRule();
```

## الخطوة 3: تخصيص تنسيق القاعدة الأفقية

 الوصول إلى`HorizontalRuleFormat` خاصية الشكل المدرج لتخصيص مظهر المسطرة الأفقية.

```csharp
HorizontalRuleFormat horizontalRuleFormat = shape.HorizontalRuleFormat;
horizontalRuleFormat.Alignment = HorizontalRuleAlignment.Center;
horizontalRuleFormat.WidthPercent = 70;
horizontalRuleFormat.Height = 3;
horizontalRuleFormat.Color = Color.Blue;
horizontalRuleFormat.NoShade = true;
```

- المحاذاة: تحدد محاذاة القاعدة الأفقية (`HorizontalRuleAlignment.Center` في هذا المثال).
- WidthPercent: يحدد عرض الخط الأفقي كنسبة مئوية من عرض الصفحة (70% في هذا المثال).
- الارتفاع: يحدد ارتفاع المسطرة الأفقية بالنقاط (3 نقاط في هذا المثال).
- اللون: يحدد لون الخط الأفقي (`Color.Blue` في هذا المثال).
- NoShade: يحدد ما إذا كان يجب أن تحتوي القاعدة الأفقية على ظل (`true` في هذا المثال).

## الخطوة 4: حفظ المستند

 أخيرًا، احفظ المستند المعدّل باستخدام`Save` طريقة`Document` هدف.

```csharp
builder.Document.Save(dataDir + "AddContentUsingDocumentBuilder.HorizontalRuleFormat.docx");
```

## خاتمة

إن إتقان إدراج القواعد الأفقية في مستندات Word باستخدام Aspose.Words for .NET يعزز من قدرات أتمتة المستندات. ومن خلال الاستفادة من مرونة وقوة Aspose.Words، يمكن للمطورين تبسيط عمليات إنشاء المستندات وتنسيقها بكفاءة.

## الأسئلة الشائعة

### ما هو Aspose.Words لـ .NET؟
Aspose.Words for .NET عبارة عن مكتبة قوية للعمل مع مستندات Word برمجيًا في تطبيقات .NET.

### كيف يمكنني تنزيل Aspose.Words لـ .NET؟
 يمكنك تنزيل Aspose.Words لـ .NET من[هنا](https://releases.aspose.com/words/net/).

### هل يمكنني تخصيص مظهر القواعد الأفقية في Aspose.Words؟
نعم، يمكنك تخصيص جوانب مختلفة مثل المحاذاة والعرض والارتفاع واللون والتظليل للقواعد الأفقية باستخدام Aspose.Words.

### هل Aspose.Words مناسب لمعالجة المستندات على مستوى المؤسسة؟
نعم، يتم استخدام Aspose.Words على نطاق واسع في بيئات المؤسسات نظرًا لقدراته القوية في معالجة المستندات.

### أين يمكنني الحصول على الدعم لـ Aspose.Words لـ .NET؟
 للحصول على الدعم والمشاركة المجتمعية، قم بزيارة[منتدى Aspose.Words](https://forum.aspose.com/c/words/8).

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
