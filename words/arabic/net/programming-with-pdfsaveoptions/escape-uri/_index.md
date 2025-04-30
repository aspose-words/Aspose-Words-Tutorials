---
"description": "تعرّف على كيفية تجاوز عناوين URI في ملفات PDF باستخدام Aspose.Words لـ .NET. يشرح هذا الدليل المُفصّل العملية خطوة بخطوة."
"linktitle": "الهروب من عنوان URI في مستند PDF"
"second_title": "واجهة برمجة تطبيقات معالجة المستندات Aspose.Words"
"title": "الهروب من عنوان URI في مستند PDF"
"url": "/ar/net/programming-with-pdfsaveoptions/escape-uri/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# الهروب من عنوان URI في مستند PDF

## مقدمة

أهلاً! هل تساءلت يومًا عن كيفية التعامل مع عناوين URI عند حفظ مستند Word كملف PDF باستخدام Aspose.Words لـ .NET؟ أنت في المكان الصحيح! اليوم، سنتعمق في كيفية تجاوز عناوين URI في مستندات PDF لضمان عملها بشكل صحيح عند تحويل مستندك. لنبدأ هذه الرحلة معًا، خطوة بخطوة، لنضمن لك استيعاب كل مفهوم على طول الطريق.

## المتطلبات الأساسية

قبل أن نبدأ، دعونا نتأكد من أن لديك كل ما تحتاجه:

1. Aspose.Words لـ .NET: تأكد من حصولك على أحدث إصدار. يمكنك تنزيله. [هنا](https://releases.aspose.com/words/net/).
2. بيئة التطوير: Visual Studio أو أي بيئة تطوير .NET أخرى.
3. المعرفة الأساسية بلغة C#: يفترض هذا البرنامج التعليمي أن لديك فهمًا أساسيًا لبرمجة C#.

## استيراد مساحات الأسماء

أولاً، عليك استيراد مساحات الأسماء اللازمة. هذا ضروري للوصول إلى وظائف Aspose.Words.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

حسنًا، لنُقسّم العملية إلى خطوات سهلة الفهم. اتبع الخطوات وستصبح محترفًا في فك تشفير عناوين URI في وقت قصير!

## الخطوة 1: إعداد دليل المستندات الخاص بك

قبل البدء في الكود، حدد مسار مجلد المستندات. هنا سيتم حفظ ملفاتك.

```csharp
// المسار إلى دليل المستندات.
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

يستبدل `"YOUR DOCUMENT DIRECTORY"` مع المسار الفعلي الذي تريد حفظ مستند PDF الخاص بك فيه.

## الخطوة 2: إنشاء مستند جديد

بعد ذلك، سننشئ مستندًا جديدًا باستخدام Aspose.Words. سيُستخدم هذا المستند كلوحة لإدراج الروابط التشعبية.

```csharp
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

هنا، `Document` هو مستند Word الجديد الخاص بك، و `DocumentBuilder` هي فئة مساعدة تعمل على تبسيط عملية إنشاء المستندات.

## الخطوة 3: إدراج ارتباط تشعبي

الآن، لنُدرج رابطًا تشعبيًا في المستند. سيكون هذا الرابط محور عملية حذف عنوان URI.

```csharp
builder.InsertHyperlink("Testlink", "https://www.google.com/search?q= aspose"، false)؛
```

في هذا الخط، `"Testlink"` هو نص العرض للارتباط التشعبي، و `"https://www.google.com/search?q= aspose"` هو عنوان URL. `false` تشير المعلمة إلى أنه لا ينبغي تنسيق الرابط كارتباط تشعبي (أي أنه لن يكون مسطرًا باللون الأزرق).

## الخطوة 4: حفظ المستند بتنسيق PDF

أخيرًا، احفظ المستند بصيغة PDF. هنا، يتولى Aspose.Words مهمة حذف عنوان URI في ملف PDF.

```csharp
doc.Save(dataDir + "WorkingWithPdfSaveOptions.EscapeUri.pdf");
```

يحفظ هذا السطر المستند في الدليل المحدد باسم الملف `WorkingWithPdfSaveOptions.EscapeUri.pdf`.

## خاتمة

وهذا كل ما في الأمر! لقد تعلمت للتو كيفية تجاوز عناوين URL عند حفظ مستند Word كملف PDF باستخدام Aspose.Words لـ .NET. تضمن هذه العملية بقاء روابطك التشعبية سليمة وتنسيقها الصحيح في ملف PDF الناتج. 

تذكر أن إتقان هذه التقنيات البسيطة والمهمة يُحسّن جودة مستنداتك ووظائفها بشكل كبير. برمجة ممتعة!

## الأسئلة الشائعة

### ما هو Aspose.Words لـ .NET؟

Aspose.Words for .NET هي مكتبة قوية تسمح للمطورين بإنشاء مستندات Word ومعالجتها وتحويلها في تطبيقات .NET.

### لماذا يعد الهروب من عنوان URI مهمًا في ملفات PDF؟

يضمن إفلات URI تفسير الأحرف الخاصة في عناوين URL بشكل صحيح، مما يمنع الروابط المعطلة ويضمن عملها كما هو مقصود.

### هل يمكنني استخدام أنواع أخرى من الروابط في Aspose.Words لـ .NET؟

بالتأكيد! يدعم Aspose.Words أنواعًا مختلفة من الروابط، بما في ذلك روابط المستندات الداخلية، والإشارات المرجعية، وعناوين URL الخارجية.

### كيف يمكنني الحصول على نسخة تجريبية مجانية من Aspose.Words لـ .NET؟

يمكنك الحصول على نسخة تجريبية مجانية [هنا](https://releases.aspose.com/).

### أين يمكنني العثور على المزيد من الوثائق التفصيلية حول Aspose.Words لـ .NET؟

يمكنك العثور على الوثائق التفصيلية [هنا](https://reference.aspose.com/words/net/).



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}