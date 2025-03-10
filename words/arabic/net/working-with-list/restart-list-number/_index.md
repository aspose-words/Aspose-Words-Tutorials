---
title: رقم قائمة إعادة التشغيل
linktitle: رقم قائمة إعادة التشغيل
second_title: واجهة برمجة تطبيقات معالجة المستندات Aspose.Words
description: تعرف على كيفية إعادة تشغيل أرقام القائمة في مستندات Word باستخدام Aspose.Words for .NET. يغطي هذا الدليل المفصل الذي يبلغ طوله 2000 كلمة كل ما تحتاج إلى معرفته، من الإعداد إلى التخصيص المتقدم.
weight: 10
url: /ar/net/working-with-list/restart-list-number/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# رقم قائمة إعادة التشغيل

## مقدمة

هل تتطلع إلى إتقان فن التعامل مع القوائم في مستندات Word باستخدام Aspose.Words for .NET؟ حسنًا، أنت في المكان المناسب! في هذا البرنامج التعليمي، سنخوض بعمق في إعادة تشغيل أرقام القائمة، وهي ميزة رائعة ستنقل مهاراتك في أتمتة المستندات إلى المستوى التالي. استعد، ولنبدأ!

## المتطلبات الأساسية

قبل أن ننتقل إلى الكود، دعنا نتأكد من أن لديك كل ما تحتاجه:

1.  Aspose.Words for .NET: يجب أن يكون لديك Aspose.Words for .NET مثبتًا. إذا لم تقم بتثبيته بعد، فيمكنك[تحميله هنا](https://releases.aspose.com/words/net/).
2. بيئة التطوير: تأكد من أن لديك بيئة تطوير مناسبة مثل Visual Studio.
3. المعرفة الأساسية بلغة C#: إن الفهم الأساسي للغة C# سيساعدك على متابعة البرنامج التعليمي.

## استيراد مساحات الأسماء

أولاً وقبل كل شيء، دعنا نستورد مساحات الأسماء الضرورية. فهي ضرورية للوصول إلى ميزات Aspose.Words.

```csharp
using Aspose.Words;
using Aspose.Words.Lists;
using System.Drawing;
```

الآن، دعنا نقسم العملية إلى خطوات سهلة المتابعة. سنغطي كل شيء بدءًا من إنشاء قائمة وحتى إعادة ترقيمها.

## الخطوة 1: إعداد المستند والمنشئ

قبل أن تتمكن من البدء في معالجة القوائم، ستحتاج إلى مستند وبرنامج DocumentBuilder. برنامج DocumentBuilder هو أداة الانتقال إلى إضافة المحتوى إلى مستندك.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## الخطوة 2: إنشاء قائمتك الأولى وتخصيصها

بعد ذلك، سننشئ قائمة بناءً على قالب ونخصص مظهرها. في هذا المثال، نستخدم تنسيق الأرقام العربية مع الأقواس.

```csharp
List list1 = doc.Lists.Add(ListTemplate.NumberArabicParenthesis);
list1.ListLevels[0].Font.Color = Color.Red;
list1.ListLevels[0].Alignment = ListLevelAlignment.Right;
```

هنا، قمنا بتعيين لون الخط إلى اللون الأحمر ومحاذاة النص إلى اليمين.

## الخطوة 3: أضف العناصر إلى قائمتك الأولى

 بعد أن أصبحت قائمتك جاهزة، حان الوقت لإضافة بعض العناصر.`ListFormat.List` تساعد الخاصية في تطبيق تنسيق القائمة على النص.

```csharp
builder.Writeln("List 1 starts below:");
builder.ListFormat.List = list1;
builder.Writeln("Item 1");
builder.Writeln("Item 2");
builder.ListFormat.RemoveNumbers();
```

## الخطوة 4: إعادة تشغيل ترقيم القائمة

لإعادة استخدام القائمة وإعادة ترقيمها، يتعين عليك إنشاء نسخة من القائمة الأصلية. يتيح لك هذا تعديل القائمة الجديدة بشكل مستقل.

```csharp
List list2 = doc.Lists.AddCopy(list1);
list2.ListLevels[0].StartAt = 10;
```

في هذا المثال، تبدأ القائمة الجديدة بالرقم 10.

## الخطوة 5: إضافة العناصر إلى القائمة الجديدة

تمامًا كما في السابق، أضف عناصر إلى قائمتك الجديدة. يوضح هذا إعادة تشغيل القائمة عند العدد المحدد.

```csharp
builder.Writeln("List 2 starts below:");
builder.ListFormat.List = list2;
builder.Writeln("Item 1");
builder.Writeln("Item 2");
builder.ListFormat.RemoveNumbers();
```

## الخطوة 6: احفظ مستندك

وأخيرًا، قم بحفظ مستندك في الدليل المحدد.

```csharp
builder.Document.Save(dataDir + "WorkingWithList.RestartListNumber.docx");
```

## خاتمة

إن إعادة تشغيل أرقام القائمة في مستندات Word باستخدام Aspose.Words for .NET أمر بسيط ومفيد بشكل لا يصدق. سواء كنت تقوم بإنشاء تقارير أو إنشاء مستندات منظمة أو كنت تحتاج فقط إلى تحكم أفضل في قوائمك، فإن هذه التقنية ستلبي احتياجاتك.

## الأسئلة الشائعة

### هل يمكنني استخدام قوالب قائمة أخرى بالإضافة إلى NumberEnglishParenthesis؟

بالتأكيد! يوفر Aspose.Words قوالب قوائم متنوعة مثل النقاط والحروف والأرقام الرومانية والمزيد. يمكنك اختيار القالب الذي يناسب احتياجاتك بشكل أفضل.

### كيف يمكنني تغيير مستوى القائمة؟

 يمكنك تغيير مستوى القائمة عن طريق تعديل`ListLevels` الممتلكات. على سبيل المثال،`list1.ListLevels[1]` سوف يشير إلى المستوى الثاني من القائمة.

### هل يمكنني إعادة ترقيم أي رقم؟

 نعم، يمكنك تعيين الرقم الأولي إلى أي قيمة عددية صحيحة باستخدام`StartAt` خاصية مستوى القائمة.

### هل من الممكن الحصول على تنسيق مختلف لمستويات القائمة المختلفة؟

في الواقع! يمكن أن يكون لكل مستوى من مستويات القائمة إعدادات تنسيق خاصة به، مثل الخط والمحاذاة ونمط الترقيم.

### ماذا لو أردت الاستمرار في الترقيم من قائمة سابقة بدلاً من إعادة البدء؟

إذا كنت تريد الاستمرار في الترقيم، فلن تحتاج إلى إنشاء نسخة من القائمة. ما عليك سوى الاستمرار في إضافة العناصر إلى القائمة الأصلية.



{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
