---
title: إدراج ASKField بدون منشئ المستندات
linktitle: إدراج ASKField بدون منشئ المستندات
second_title: واجهة برمجة تطبيقات معالجة المستندات Aspose.Words
description: تعرف على كيفية إدراج حقل ASK دون استخدام Document Builder في Aspose.Words for .NET. اتبع هذا الدليل لتحسين مستندات Word الخاصة بك بشكل ديناميكي.
weight: 10
url: /ar/net/working-with-fields/insert-askfield-with-out-document-builder/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# إدراج ASKField بدون منشئ المستندات

## مقدمة

هل تبحث عن إتقان أتمتة المستندات باستخدام Aspose.Words for .NET؟ لقد أتيت إلى المكان الصحيح! اليوم، سنوضح لك كيفية إدراج حقل ASK دون استخدام Document Builder. هذه ميزة رائعة عندما تريد أن يطلب مستندك من المستخدمين إدخال بيانات معينة، مما يجعل مستندات Word أكثر تفاعلية وديناميكية. لذا، دعنا نتعمق في جعل مستنداتك أكثر ذكاءً!

## المتطلبات الأساسية

قبل أن نبدأ في تعلم بعض الأكواد البرمجية، دعونا نتأكد من إعداد كل شيء:

1.  Aspose.Words for .NET: تأكد من تثبيت هذه المكتبة. إذا لم يكن الأمر كذلك، فيمكنك تنزيلها من[هنا](https://releases.aspose.com/words/net/).
2. بيئة التطوير: بيئة تطوير متكاملة مناسبة مثل Visual Studio.
3. .NET Framework: تأكد من تثبيت .NET Framework.

رائع! الآن بعد أن أصبح كل شيء جاهزًا، فلنبدأ باستيراد المساحات الأساسية اللازمة.

## استيراد مساحات الأسماء

أولاً وقبل كل شيء، نحتاج إلى استيراد مساحة اسم Aspose.Words للوصول إلى كافة ميزات Aspose.Words لـ .NET. إليك كيفية القيام بذلك:

```csharp
using Aspose.Words;
using Aspose.Words.Fields;
```

## الخطوة 1: إنشاء مستند جديد

قبل أن نتمكن من إدراج حقل ASK، نحتاج إلى مستند للعمل عليه. إليك كيفية إنشاء مستند جديد:

```csharp
// المسار إلى دليل المستندات.
string dataDir = "YOUR DOCUMENTS DIRECTORY";

// إنشاء المستندات.
Document doc = new Document();
```

يؤدي مقتطف التعليمات البرمجية هذا إلى إنشاء مستند Word جديد حيث سنضيف حقل ASK الخاص بنا.

## الخطوة 2: الوصول إلى عقدة الفقرة

في مستند Word، يتم تنظيم المحتوى في عقد. نحتاج إلى الوصول إلى عقدة الفقرة الأولى حيث سنقوم بإدراج حقل ASK:

```csharp
Paragraph para = (Paragraph)doc.GetChild(NodeType.Paragraph, 0, true);
```

يسترجع هذا السطر من التعليمات البرمجية الفقرة الأولى في المستند، جاهزة لإدراج حقل ASK.

## الخطوة 3: أدخل حقل ASK

الآن، لننتقل إلى الحدث الرئيسي - إدخال حقل ASK. سيطالب هذا الحقل المستخدم بإدخال بيانات عند فتح المستند.

```csharp
// أدخل حقل ASK.
FieldAsk field = (FieldAsk)para.AppendField(FieldType.FieldAsk, false);
```

هنا نضيف حقل ASK إلى الفقرة. الأمر بسيط، أليس كذلك؟

## الخطوة 4: تكوين حقل ASK

نحتاج إلى تعيين بعض الخصائص لتحديد كيفية عمل حقل ASK. دعنا نحدد اسم الإشارة المرجعية ونص المطالبة والاستجابة الافتراضية وسلوك دمج البريد:

```csharp
field.BookmarkName = "Test1";
field.PromptText = "Please enter your response:";
field.DefaultResponse = "Default response";
field.PromptOnceOnMailMerge = true;
```

- BookmarkName: معرف فريد لحقل ASK.
- PromptText: النص الذي يطالب المستخدم بالإدخال.
- DefaultResponse: الاستجابة المعبأة مسبقًا والتي يمكن للمستخدم تغييرها.
- PromptOnceOnMailMerge: يحدد ما إذا كانت المطالبة تظهر مرة واحدة فقط أثناء دمج البريد.

## الخطوة 5: تحديث الحقل

بعد تكوين حقل ASK، نحتاج إلى تحديثه للتأكد من تطبيق كافة الإعدادات بشكل صحيح:

```csharp
field.Update();
```

يتأكد هذا الأمر من أن حقل ASK جاهز ومُعد بشكل صحيح في المستند.

## الخطوة 6: حفظ المستند

وأخيرًا، دعنا نحفظ المستند في الدليل المحدد:

```csharp
doc.Save(dataDir + "InsertionChampASKSansDocumentBuilder.docx");
```

يحفظ هذا السطر المستند الذي يحتوي على حقل ASK المُدرج. وها أنت ذا – لقد أصبح مستندك الآن مزودًا بحقل ASK ديناميكي!

## خاتمة

تهانينا! لقد قمت للتو بإضافة حقل ASK إلى مستند Word باستخدام Aspose.Words for .NET بدون Document Builder. يمكن لهذه الميزة أن تعزز بشكل كبير تفاعل المستخدم مع مستنداتك، مما يجعلها أكثر مرونة وسهولة في الاستخدام. استمر في تجربة حقول وخصائص مختلفة لإطلاق العنان للإمكانات الكاملة لـ Aspose.Words. أتمنى لك برمجة سعيدة!

## الأسئلة الشائعة

### ما هو حقل ASK في Aspose.Words؟
حقل ASK في Aspose.Words هو حقل يطالب المستخدم بإدخال معين عند فتح المستند، مما يسمح بإدخال البيانات بشكل ديناميكي.

### هل يمكنني استخدام حقول ASK متعددة في مستند واحد؟
نعم، يمكنك إدراج حقول ASK متعددة في مستند، بحيث يحتوي كل منها على مطالبات واستجابات فريدة.

###  ما هو الغرض من ذلك؟`PromptOnceOnMailMerge` property?
 ال`PromptOnceOnMailMerge` تحدد الخاصية ما إذا كان موجه ASK يظهر مرة واحدة فقط أثناء عملية دمج البريد أو في كل مرة.

### هل أحتاج إلى تحديث حقل ASK بعد تعيين خصائصه؟
نعم، يؤدي تحديث الحقل ASK إلى ضمان تطبيق جميع الخصائص بشكل صحيح وعمل الحقل كما هو متوقع.

### هل يمكنني تخصيص نص المطالبة والاستجابة الافتراضية؟
بالتأكيد! يمكنك تعيين نص مخصص واستجابات افتراضية لتخصيص حقل ASK وفقًا لاحتياجاتك المحددة.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
