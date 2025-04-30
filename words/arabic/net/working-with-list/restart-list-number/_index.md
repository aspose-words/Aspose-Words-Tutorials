---
"description": "تعرّف على كيفية إعادة تشغيل أرقام القوائم في مستندات Word باستخدام Aspose.Words لـ .NET. يغطي هذا الدليل المفصل، المكون من 2000 كلمة، كل ما تحتاج لمعرفته، من الإعداد إلى التخصيص المتقدم."
"linktitle": "رقم قائمة إعادة التشغيل"
"second_title": "واجهة برمجة تطبيقات معالجة المستندات Aspose.Words"
"title": "رقم قائمة إعادة التشغيل"
"url": "/ar/net/working-with-list/restart-list-number/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# رقم قائمة إعادة التشغيل

## مقدمة

هل تتطلع إلى إتقان فن التعامل مع القوائم في مستندات Word باستخدام Aspose.Words لـ .NET؟ أنت في المكان المناسب! في هذا البرنامج التعليمي، سنتعمق في إعادة تشغيل أرقام القوائم، وهي ميزة رائعة سترفع مهاراتك في أتمتة المستندات إلى مستوى جديد. استعد، ولنبدأ!

## المتطلبات الأساسية

قبل أن ننتقل إلى الكود، دعنا نتأكد من أن لديك كل ما تحتاجه:

1. Aspose.Words لـ .NET: يجب تثبيت Aspose.Words لـ .NET. إذا لم تقم بتثبيته بعد، يمكنك [قم بتحميله هنا](https://releases.aspose.com/words/net/).
2. بيئة التطوير: تأكد من أن لديك بيئة تطوير مناسبة مثل Visual Studio.
3. المعرفة الأساسية بلغة C#: إن الفهم الأساسي للغة C# سيساعدك على متابعة البرنامج التعليمي.

## استيراد مساحات الأسماء

أولاً، لنستورد مساحات الأسماء اللازمة. فهي ضرورية للوصول إلى ميزات Aspose.Words.

```csharp
using Aspose.Words;
using Aspose.Words.Lists;
using System.Drawing;
```

الآن، لنُقسّم العملية إلى خطوات سهلة. سنغطي كل شيء، من إنشاء قائمة إلى إعادة ترقيمها.

## الخطوة 1: إعداد مستندك ومنشئه

قبل البدء بمعالجة القوائم، ستحتاج إلى مستند وأداة إنشاء المستندات. أداة إنشاء المستندات هي أداتك المفضلة لإضافة محتوى إلى مستندك.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## الخطوة 2: إنشاء قائمتك الأولى وتخصيصها

بعد ذلك، سننشئ قائمةً بناءً على قالب ونُخصّص مظهرها. في هذا المثال، نستخدم تنسيق الأرقام العربية مع الأقواس.

```csharp
List list1 = doc.Lists.Add(ListTemplate.NumberArabicParenthesis);
list1.ListLevels[0].Font.Color = Color.Red;
list1.ListLevels[0].Alignment = ListLevelAlignment.Right;
```

هنا، قمنا بتعيين لون الخط إلى اللون الأحمر ومحاذاة النص إلى اليمين.

## الخطوة 3: إضافة العناصر إلى قائمتك الأولى

بعد أن أصبحت قائمتك جاهزة، حان الوقت لإضافة بعض العناصر. `ListFormat.List` تساعد الخاصية في تطبيق تنسيق القائمة على النص.

```csharp
builder.Writeln("List 1 starts below:");
builder.ListFormat.List = list1;
builder.Writeln("Item 1");
builder.Writeln("Item 2");
builder.ListFormat.RemoveNumbers();
```

## الخطوة 4: إعادة تشغيل ترقيم القائمة

لإعادة استخدام القائمة وإعادة ترقيمها، عليك إنشاء نسخة منها. هذا يسمح لك بتعديل القائمة الجديدة بشكل مستقل.

```csharp
List list2 = doc.Lists.AddCopy(list1);
list2.ListLevels[0].StartAt = 10;
```

في هذا المثال، تبدأ القائمة الجديدة بالرقم 10.

## الخطوة 5: إضافة العناصر إلى القائمة الجديدة

كما في السابق، أضف عناصر إلى قائمتك الجديدة. هذا يُظهر إعادة تشغيل القائمة عند العدد المحدد.

```csharp
builder.Writeln("List 2 starts below:");
builder.ListFormat.List = list2;
builder.Writeln("Item 1");
builder.Writeln("Item 2");
builder.ListFormat.RemoveNumbers();
```

## الخطوة 6: احفظ مستندك

وأخيرًا، احفظ مستندك في الدليل المحدد.

```csharp
builder.Document.Save(dataDir + "WorkingWithList.RestartListNumber.docx");
```

## خاتمة

إعادة تشغيل أرقام القوائم في مستندات Word باستخدام Aspose.Words لـ .NET عملية سهلة ومفيدة للغاية. سواء كنت تُنشئ تقارير، أو مستندات مُهيكلة، أو تحتاج فقط إلى تحكم أفضل في قوائمك، فهذه التقنية تُلبي احتياجاتك.

## الأسئلة الشائعة

### هل يمكنني استخدام قوالب قائمة أخرى إلى جانب NumberEnglishParenthesis؟

بالتأكيد! يوفر Aspose.Words قوالب قوائم متنوعة، مثل النقاط والحروف والأرقام الرومانية وغيرها. يمكنك اختيار القالب الأنسب لاحتياجاتك.

### كيف يمكنني تغيير مستوى القائمة؟

يمكنك تغيير مستوى القائمة عن طريق تعديل `ListLevels` الممتلكات. على سبيل المثال، `list1.ListLevels[1]` سوف يشير إلى المستوى الثاني من القائمة.

### هل يمكنني إعادة الترقيم عند أي رقم؟

نعم، يمكنك تعيين الرقم الابتدائي إلى أي قيمة عددية صحيحة باستخدام `StartAt` خاصية مستوى القائمة.

### هل من الممكن الحصول على تنسيق مختلف لمستويات القائمة المختلفة؟

بالفعل! لكل مستوى قائمة إعدادات تنسيق خاصة به، مثل الخط والمحاذاة ونمط الترقيم.

### ماذا لو أردت الاستمرار في الترقيم من قائمة سابقة بدلاً من إعادة التشغيل؟

إذا أردتَ مواصلة الترقيم، فلا حاجة لإنشاء نسخة من القائمة. ما عليك سوى مواصلة إضافة العناصر إلى القائمة الأصلية.





{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}