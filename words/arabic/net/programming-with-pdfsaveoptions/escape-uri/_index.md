---
title: إزالة عنوان URI من مستند PDF
linktitle: إزالة عنوان URI من مستند PDF
second_title: واجهة برمجة تطبيقات معالجة المستندات Aspose.Words
description: تعرف على كيفية تجنب عناوين URI في ملفات PDF باستخدام Aspose.Words for .NET. يرشدك هذا الدليل التفصيلي خلال العملية خطوة بخطوة.
weight: 10
url: /ar/net/programming-with-pdfsaveoptions/escape-uri/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# إزالة عنوان URI من مستند PDF

## مقدمة

مرحبًا! هل تساءلت يومًا عن كيفية التعامل مع عناوين URI عند حفظ مستند Word بتنسيق PDF باستخدام Aspose.Words لـ .NET؟ أنت في المكان الصحيح! اليوم، سنخوض بعمق في كيفية إفلات عناوين URI في مستندات PDF لضمان عملها بشكل صحيح عند تحويل مستندك. فلنبدأ هذه الرحلة معًا، خطوة بخطوة، لضمان استيعابك لكل مفهوم على طول الطريق.

## المتطلبات الأساسية

قبل أن نبدأ، دعونا نتأكد من أن لديك كل ما تحتاجه:

1.  Aspose.Words for .NET: تأكد من حصولك على أحدث إصدار. يمكنك تنزيله[هنا](https://releases.aspose.com/words/net/).
2. بيئة التطوير: Visual Studio أو أي بيئة تطوير .NET أخرى.
3. المعرفة الأساسية بلغة C#: يفترض هذا البرنامج التعليمي أن لديك فهمًا أساسيًا لبرمجة C#.

## استيراد مساحات الأسماء

أولاً وقبل كل شيء، عليك استيراد مساحات الأسماء الضرورية. وهذا أمر بالغ الأهمية للوصول إلى وظائف Aspose.Words.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

حسنًا، دعنا نقسم العملية إلى خطوات سهلة الفهم. اتبع الخطوات التالية وستصبح محترفًا في الهروب من عناوين URI في وقت قصير!

## الخطوة 1: إعداد دليل المستندات الخاص بك

قبل التعمق في الكود، قم بإعداد المسار إلى دليل المستندات الخاص بك. هذا هو المكان الذي سيتم حفظ ملفاتك فيه.

```csharp
// المسار إلى دليل المستندات.
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

 يستبدل`"YOUR DOCUMENT DIRECTORY"` مع المسار الفعلي الذي تريد حفظ مستند PDF الخاص بك فيه.

## الخطوة 2: إنشاء مستند جديد

بعد ذلك، سننشئ مستندًا جديدًا باستخدام Aspose.Words. سيعمل هذا المستند كلوحة لإدراج الارتباطات التشعبية.

```csharp
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

 هنا،`Document` هذا هو مستند Word الجديد الخاص بك، و`DocumentBuilder` هي فئة مساعدة تعمل على تبسيط عملية إنشاء المستندات.

## الخطوة 3: إدراج ارتباط تشعبي

الآن، دعنا ندرج ارتباطًا تشعبيًا في المستند. سيكون هذا الارتباط التشعبي هو محور عملية الهروب من URI.

```csharp
builder.InsertHyperlink("Testlink", "https://www.google.com/search?q= aspose"، false)؛
```

 في هذا الخط،`"Testlink"` هو نص العرض للارتباط التشعبي، و`"https://www.google.com/search?q= aspose"` هو عنوان URL.`false` تشير المعلمة إلى أنه لا ينبغي تنسيق الرابط كارتباط تشعبي (أي أنه لن يكون مسطرًا باللون الأزرق).

## الخطوة 4: احفظ المستند بتنسيق PDF

أخيرًا، احفظ المستند بتنسيق PDF. هنا يتولى Aspose.Words مهمة تجنب عنوان URI في مخرجات PDF.

```csharp
doc.Save(dataDir + "WorkingWithPdfSaveOptions.EscapeUri.pdf");
```

 يحفظ هذا السطر المستند في الدليل المحدد باسم الملف`WorkingWithPdfSaveOptions.EscapeUri.pdf`.

## خاتمة

والآن، لقد تعلمت كيفية تجنب عناوين URI عند حفظ مستند Word بتنسيق PDF باستخدام Aspose.Words for .NET. تضمن هذه العملية أن تظل الروابط التشعبية الخاصة بك وظيفية ومنسقة بشكل صحيح في ملف PDF الناتج. 

تذكر أن إتقان هذه التقنيات الصغيرة ولكن المهمة يمكن أن يعزز بشكل كبير من جودة ووظائف مستنداتك. استمتع بالبرمجة!

## الأسئلة الشائعة

### ما هو Aspose.Words لـ .NET؟

Aspose.Words for .NET هي مكتبة قوية تسمح للمطورين بإنشاء مستندات Word ومعالجتها وتحويلها في تطبيقات .NET.

### لماذا يعد إفلات URI مهمًا في ملفات PDF؟

يضمن إفلات URI تفسير الأحرف الخاصة في عناوين URL بشكل صحيح، مما يمنع الروابط المعطلة ويضمن عملها كما هو مقصود.

### هل يمكنني استخدام أنواع أخرى من الروابط في Aspose.Words لـ .NET؟

بالتأكيد! يدعم Aspose.Words أنواعًا مختلفة من الروابط، بما في ذلك روابط المستندات الداخلية، والإشارات المرجعية، وعناوين URL الخارجية.

### كيف يمكنني الحصول على نسخة تجريبية مجانية من Aspose.Words لـ .NET؟

 يمكنك الحصول على نسخة تجريبية مجانية[هنا](https://releases.aspose.com/).

### أين يمكنني العثور على مزيد من الوثائق التفصيلية حول Aspose.Words لـ .NET؟

 يمكنك العثور على الوثائق التفصيلية[هنا](https://reference.aspose.com/words/net/).

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
