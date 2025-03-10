---
title: اكتشاف الترقيم باستخدام المسافات البيضاء
linktitle: اكتشاف الترقيم باستخدام المسافات البيضاء
second_title: واجهة برمجة تطبيقات معالجة المستندات Aspose.Words
description: اكتشف كيفية استخدام Aspose.Words لـ .NET لاكتشاف الترقيم بالمسافات البيضاء في المستندات النصية العادية والتأكد من التعرف على قوائمك بشكل صحيح.
weight: 10
url: /ar/net/programming-with-txtloadoptions/detect-numbering-with-whitespaces/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# اكتشاف الترقيم باستخدام المسافات البيضاء

## مقدمة

Aspose.Words لعشاق .NET! اليوم، نتعمق في ميزة رائعة يمكنها أن تجعل التعامل مع القوائم في مستندات النص العادي أمرًا سهلاً. هل سبق لك التعامل مع ملفات نصية حيث من المفترض أن تكون بعض الأسطر عبارة عن قوائم، لكنها لا تبدو صحيحة تمامًا عند تحميلها في مستند Word؟ حسنًا، لدينا خدعة رائعة في جعبتنا: اكتشاف الترقيم باستخدام المسافات البيضاء. سيرشدك هذا البرنامج التعليمي إلى كيفية استخدام Aspose.Words`DetectNumberingWithWhitespaces` خيار في Aspose.Words لـ .NET لضمان التعرف على القوائم الخاصة بك بشكل صحيح، حتى عندما تكون هناك مسافة بيضاء بين الأرقام والنص.

## المتطلبات الأساسية

قبل أن نبدأ، تأكد من أن لديك ما يلي:

-  Aspose.Words for .NET: يمكنك تنزيله من[إصدارات Aspose](https://releases.aspose.com/words/net/) صفحة.
- بيئة التطوير: Visual Studio أو أي C# IDE آخر.
- تم تثبيت .NET Framework على جهازك.
- المعرفة الأساسية بلغة C#: إن فهم الأساسيات سيساعدك على متابعة الأمثلة.

## استيراد مساحات الأسماء

قبل البدء في كتابة الكود، تأكد من استيراد المساحات الأساسية اللازمة في مشروعك. إليك مقتطف سريع لمساعدتك على البدء:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Loading;
```

دعنا نقسم العملية إلى خطوات بسيطة وسهلة الإدارة. سترشدك كل خطوة خلال التعليمات البرمجية اللازمة وتشرح ما يحدث.

## الخطوة 1: قم بتحديد دليل المستندات الخاص بك

أولاً وقبل كل شيء، دعنا نحدد المسار إلى دليل المستندات الخاص بك. هذا هو المكان الذي سيتم فيه تخزين ملفات الإدخال والإخراج الخاصة بك.

```csharp
// المسار إلى دليل المستند الخاص بك
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## الخطوة 2: إنشاء مستند نص عادي

بعد ذلك، سننشئ مستند نص عادي كسلسلة. سيحتوي هذا المستند على أجزاء يمكن تفسيرها كقوائم.

```csharp
const string textDoc = "Full stop delimiters:\n" +
                       "1. First list item 1\n" +
                       "2. First list item 2\n" +
                       "3. First list item 3\n\n" +
                       "Right bracket delimiters:\n" +
                       "1) Second list item 1\n" +
                       "2) Second list item 2\n" +
                       "3) Second list item 3\n\n" +
                       "Bullet delimiters:\n" +
                       "• Third list item 1\n" +
                       "• Third list item 2\n" +
                       "• Third list item 3\n\n" +
                       "Whitespace delimiters:\n" +
                       "1 Fourth list item 1\n" +
                       "2 Fourth list item 2\n" +
                       "3 Fourth list item 3";
```

## الخطوة 3: تكوين LoadOptions

 لاكتشاف الترقيم باستخدام المسافات البيضاء، نحتاج إلى ضبط`DetectNumberingWithWhitespaces` خيار ل`true` في`TxtLoadOptions` هدف.

```csharp
TxtLoadOptions loadOptions = new TxtLoadOptions { DetectNumberingWithWhitespaces = true };
```

## الخطوة 4: تحميل المستند

 الآن، دعنا نحمل المستند باستخدام`TxtLoadOptions` كمعلمة. وهذا يضمن اكتشاف القائمة الرابعة (مع المسافات البيضاء) بشكل صحيح.

```csharp
Document doc = new Document(new MemoryStream(Encoding.UTF8.GetBytes(textDoc)), loadOptions);
```

## الخطوة 5: احفظ المستند

أخيرًا، احفظ المستند في الدليل المحدد. سيؤدي هذا إلى إخراج مستند Word يحتوي على قوائم تم اكتشافها بشكل صحيح.

```csharp
doc.Save(dataDir + "WorkingWithTxtLoadOptions.DetectNumberingWithWhitespaces.docx");
```

## خاتمة

والآن، لقد أتقنت فن اكتشاف الترقيم باستخدام المسافات البيضاء في المستندات النصية العادية باستخدام Aspose.Words for .NET. يمكن أن تكون هذه الميزة مفيدة للغاية عند التعامل مع تنسيقات نصية مختلفة والتأكد من تمثيل قوائمك بدقة في مستندات Word. لذا في المرة القادمة التي تواجه فيها هذه القوائم الصعبة، ستعرف بالضبط ما يجب عليك فعله.

## الأسئلة الشائعة

###  ما هو`DetectNumberingWithWhitespaces` in Aspose.Words for .NET?
`DetectNumberingWithWhitespaces` هو خيار في`TxtLoadOptions` وهو ما يسمح لـ Aspose.Words بالتعرف على القوائم حتى عندما تكون هناك مسافة بيضاء بين الترقيم ونص عنصر القائمة.

### هل يمكنني استخدام هذه الميزة لفاصلات أخرى مثل النقاط والأقواس؟
 نعم، يكتشف Aspose.Words تلقائيًا القوائم التي تحتوي على فواصل مشتركة مثل النقاط والأقواس.`DetectNumberingWithWhitespaces` يساعد بشكل خاص مع القوائم التي تحتوي على مسافات بيضاء.

###  ماذا يحدث إذا لم أستخدم`DetectNumberingWithWhitespaces`?
بدون هذا الخيار، قد لا يتم التعرف على القوائم التي تحتوي على مسافات بيضاء بين الترقيم والنص كقوائم، وقد تظهر العناصر كفقرات عادية.

### هل هذه الميزة متوفرة في منتجات Aspose الأخرى؟
تم تصميم هذه الميزة المحددة خصيصًا لـ Aspose.Words لـ .NET، وهي مصممة للتعامل مع معالجة مستندات Word.

### كيف يمكنني الحصول على ترخيص مؤقت لـ Aspose.Words لـ .NET؟
 يمكنك الحصول على ترخيص مؤقت من[ترخيص Aspose المؤقت](https://purchase.aspose.com/temporary-license/) صفحة.


{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
