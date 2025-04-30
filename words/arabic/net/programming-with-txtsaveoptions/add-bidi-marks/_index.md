---
"description": "تعرّف على كيفية إضافة علامات ثنائية الاتجاه (Bidi) في مستندات Word باستخدام Aspose.Words لـ .NET من خلال هذا الدليل. تأكد من اتجاه النص الصحيح للمحتوى متعدد اللغات."
"linktitle": "إضافة علامات Bidi في مستند Word"
"second_title": "واجهة برمجة تطبيقات معالجة المستندات Aspose.Words"
"title": "إضافة علامات Bidi في مستند Word"
"url": "/ar/net/programming-with-txtsaveoptions/add-bidi-marks/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# إضافة علامات Bidi في مستند Word

## مقدمة

في عالم معالجة المستندات، قد يكون التعامل مع النصوص ثنائية الاتجاه (Bidi) صعبًا بعض الشيء. وينطبق هذا بشكل خاص عند التعامل مع لغات ذات اتجاهات نصية مختلفة، مثل العربية أو العبرية. لحسن الحظ، يُسهّل Aspose.Words for .NET التعامل مع مثل هذه الحالات. في هذا البرنامج التعليمي، سنشرح كيفية إضافة علامات Bidi إلى مستند Word باستخدام Aspose.Words for .NET.

## المتطلبات الأساسية

قبل أن نتعمق في الكود، تأكد من أن لديك ما يلي:

1. Aspose.Words لـ .NET: يجب تثبيت Aspose.Words لـ .NET. يمكنك تنزيله من [صفحة تنزيلات Aspose](https://releases.aspose.com/words/net/).
2. .NET Framework أو .NET Core: تأكد من أن لديك بيئة .NET متوافقة تم إعدادها لتشغيل الأمثلة.
3. المعرفة الأساسية بلغة C#: الإلمام بلغة البرمجة C# والعمليات الأساسية في .NET.

## استيراد مساحات الأسماء

للبدء، عليك استيراد مساحات الأسماء اللازمة. إليك كيفية تضمينها في مشروعك:

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

دعونا نُقسّم عملية إضافة علامات بيدي إلى مستند وورد إلى خطوات واضحة. ستُرشدك كل خطوة خلال الكود وغرضه.

## الخطوة 1: إعداد مستندك

ابدأ بإنشاء مثيل جديد لـ `Document` الصف و `DocumentBuilder` لإضافة محتوى إلى المستند.

```csharp
// المسار إلى دليل المستندات الخاص بك
string dataDir = "YOUR DOCUMENTS DIRECTORY";

// إنشاء المستند وإضافة المحتوى
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

في هذه الخطوة، يمكنك تهيئة مستند Word جديد وإعداده `DocumentBuilder` لتسهيل إدراج المحتوى.

## الخطوة 2: إضافة محتوى إلى مستندك

بعد ذلك، أضف نصًا إلى مستندك. هنا، سنضيف نصًا بلغات مختلفة لتوضيح كيفية التعامل مع نص Bidi.

```csharp
builder.Writeln("Hello world!");
builder.ParagraphFormat.Bidi = true;
builder.Writeln("שלום עולם!");
builder.Writeln("مرحبا بالعالم!");
```

هنا، نضيف أولاً عبارة إنجليزية قياسية. ثم نُفعّل تنسيق النص ثنائي الاتجاه للنص اللاحق، المكتوب بالعبرية والعربية. يوضح هذا كيفية دمج النص ثنائي الاتجاه.

## الخطوة 3: تكوين خيارات الحفظ لعلامات Bidi

للتأكد من حفظ علامات Bidi بشكل صحيح في المستند، تحتاج إلى تكوين `TxtSaveOptions` وتمكين `AddBidiMarks` خيار.

```csharp
// إضافة علامات بيدي
TxtSaveOptions saveOptions = new TxtSaveOptions { AddBidiMarks = true };
doc.Save(dataDir + "WorkingWithTxtSaveOptions.AddBidiMarks.txt", saveOptions);
```

في هذه الخطوة، نقوم بإنشاء مثيل لـ `TxtSaveOptions` وضبط `AddBidiMarks` الممتلكات إلى `true`. ويضمن هذا تضمين علامات Bidi عند حفظ المستند كملف نصي.

## خاتمة

إضافة علامات ثنائية الاتجاه إلى مستندات Word خطوة أساسية عند التعامل مع محتوى متعدد اللغات يتضمن لغات ذات اتجاهات نصية مختلفة. مع Aspose.Words لـ .NET، هذه العملية سهلة وفعّالة. باتباع الخطوات الموضحة أعلاه، يمكنك ضمان تمثيل مستنداتك لنصوص ثنائية الاتجاه بشكل صحيح، مما يُحسّن سهولة القراءة والدقة.

## الأسئلة الشائعة

### ما هي علامات البيدي ولماذا هي مهمة؟
علامات بيدي هي أحرف خاصة تُستخدم للتحكم في اتجاه النص في المستندات. وهي ضرورية لعرض اللغات التي تُقرأ من اليمين إلى اليسار بشكل صحيح، مثل العربية والعبرية.

### هل يمكنني استخدام Aspose.Words لـ .NET للتعامل مع أنواع أخرى من مشكلات اتجاه النص؟
نعم، يوفر Aspose.Words for .NET دعمًا شاملاً لاحتياجات توجيه النص وتنسيقه المختلفة، بما في ذلك اللغات من اليمين إلى اليسار ومن اليسار إلى اليمين.

### هل من الممكن تطبيق تنسيق Bidi على أجزاء محددة من المستند فقط؟
نعم، يمكنك تطبيق تنسيق Bidi على فقرات أو أقسام محددة من مستندك حسب الحاجة.

### ما هي التنسيقات التي يمكنني حفظ المستند بها باستخدام علامات Bidi؟
في المثال المُقدّم، يُحفظ المستند كملف نصي. مع ذلك، يدعم Aspose.Words أيضًا حفظ المستندات بتنسيقات مختلفة مع الحفاظ على علامات Bidi.

### أين يمكنني العثور على مزيد من المعلومات حول Aspose.Words لـ .NET؟
يمكنك استكشاف المزيد حول Aspose.Words لـ .NET من خلال [وثائق Aspose](https://reference.aspose.com/words/net/) والوصول إلى [منتدى الدعم](https://forum.aspose.com/c/words/8) للحصول على مساعدة إضافية.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}