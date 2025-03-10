---
title: دمج أفقي
linktitle: دمج أفقي
second_title: واجهة برمجة تطبيقات معالجة المستندات Aspose.Words
description: تعرف على كيفية دمج الخلايا أفقياً في مستند Word باستخدام Aspose.Words لـ .NET من خلال هذا البرنامج التعليمي المفصل خطوة بخطوة.
weight: 10
url: /ar/net/programming-with-tables/horizontal-merge/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# دمج أفقي

## مقدمة

مرحبًا! هل أنت مستعد للغوص في عالم Aspose.Words لـ .NET؟ اليوم، سنتناول ميزة مفيدة للغاية: الدمج الأفقي في الجداول. قد يبدو هذا الأمر تقنيًا بعض الشيء، ولكن لا تقلق، فأنا سأساعدك. بحلول نهاية هذا البرنامج التعليمي، ستصبح محترفًا في دمج الخلايا في مستندات Word برمجيًا. لذا، فلنبدأ!

## المتطلبات الأساسية

قبل أن ننتقل إلى التفاصيل الدقيقة، هناك بعض الأشياء التي ستحتاج إلى وضعها في مكانها:

1. مكتبة Aspose.Words for .NET: إذا لم تقم بتنزيل مكتبة Aspose.Words for .NET بالفعل، يمكنك الحصول عليها[هنا](https://releases.aspose.com/words/net/).
2. بيئة التطوير: تأكد من إعداد بيئة تطوير مناسبة، مثل Visual Studio.
3. المعرفة الأساسية بلغة C#: سيكون من المفيد الحصول على فهم أساسي لبرمجة C#.

بمجرد الانتهاء من هذه الأمور، ستكون جاهزًا للبدء!

## استيراد مساحات الأسماء

قبل الخوض في الكود، دعنا نتأكد من استيراد مساحات الأسماء اللازمة. في مشروع C# الخاص بك، تأكد من تضمين:

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
```

حسنًا، دعنا نتناول عملية دمج خلايا الجدول أفقيًا في مستند Word باستخدام Aspose.Words لـ .NET.

## الخطوة 1: إعداد مستندك

 أولاً وقبل كل شيء، نحتاج إلى إنشاء مستند Word جديد وتهيئة`DocumentBuilder`:

```csharp
// المسار إلى دليل المستند الخاص بك
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

 يقوم مقتطف التعليمات البرمجية هذا بإعداد مستند جديد وإعداده`DocumentBuilder` من أجل العمل.

## الخطوة 2: إدخال الخلية الأولى

بعد ذلك نبدأ بإدخال الخلية الأولى ووضع علامة عليها للدمج الأفقي:

```csharp
builder.InsertCell();
builder.CellFormat.HorizontalMerge = CellMerge.First;
builder.Write("Text in merged cells.");
```

 هنا نقوم بإدخال خلية جديدة وتعيينها`HorizontalMerge`الممتلكات ل`CellMerge.First`، مما يشير إلى أن هذه الخلية هي بداية لتسلسل الخلايا المندمجة.

## الخطوة 3: إدراج الخلية المدمجة

الآن نقوم بإدخال الخلية التي سيتم دمجها مع الخلية السابقة:

```csharp
builder.InsertCell();
builder.CellFormat.HorizontalMerge = CellMerge.Previous;
builder.EndRow();
```

 تم تعيين هذه الخلية للاندماج مع الخلية السابقة باستخدام`CellMerge.Previous` لاحظ كيف ننهي الصف بـ`builder.EndRow()`.

## الخطوة 4: إدراج الخلايا غير المدمجة

لتوضيح الفرق، دعنا نقوم بإدراج زوج من الخلايا غير المدمجة:

```csharp
builder.InsertCell();
builder.CellFormat.HorizontalMerge = CellMerge.None;
builder.Write("Text in one cell.");
builder.InsertCell();
builder.Write("Text in another cell.");
builder.EndRow();
```

هنا، نقوم بإدراج خليتين دون دمج أفقي. يوضح هذا كيفية تصرف الخلايا عندما لا تكون جزءًا من تسلسل مدمج.

## الخطوة 5: الانتهاء من الجدول

وأخيرا ننهي الجدول ونحفظ المستند:

```csharp
builder.EndTable();
doc.Save(dataDir + "WorkingWithTables.HorizontalMerge.docx");
```

يكمل مقتطف التعليمات البرمجية هذا الجدول ويحفظ المستند في الدليل المحدد.

## خاتمة

والآن، لقد أتقنت فن دمج الخلايا أفقيًا في مستند Word باستخدام Aspose.Words for .NET. باتباع هذه الخطوات، يمكنك إنشاء هياكل جداول معقدة بسهولة. استمر في التجريب واستكشاف إمكانيات Aspose.Words لجعل مستنداتك ديناميكية ومرنة حسب حاجتك. استمتع بالبرمجة!

## الأسئلة الشائعة

### ما هو Aspose.Words لـ .NET؟
Aspose.Words for .NET عبارة عن مكتبة قوية تسمح للمطورين بإنشاء مستندات Word وتحريرها ومعالجتها برمجيًا في تطبيقات .NET.

### هل يمكنني دمج الخلايا عموديا باستخدام Aspose.Words لـ .NET؟
 نعم، يمكنك أيضًا دمج الخلايا عموديًا باستخدام`CellFormat.VerticalMerge` ملكية.

### هل استخدام Aspose.Words لـ .NET مجاني؟
 يقدم Aspose.Words for .NET نسخة تجريبية مجانية، ولكن للحصول على الوظائف الكاملة، ستحتاج إلى شراء ترخيص. يمكنك الحصول على ترخيص مؤقت[هنا](https://purchase.aspose.com/temporary-license/).

### كيف يمكنني معرفة المزيد عن Aspose.Words لـ .NET؟
 يمكنك استكشاف الوثائق التفصيلية[هنا](https://reference.aspose.com/words/net/).

### أين يمكنني الحصول على الدعم لـ Aspose.Words لـ .NET؟
 لأي استفسارات أو مشاكل، يمكنك زيارة منتدى دعم Aspose[هنا](https://forum.aspose.com/c/words/8).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
