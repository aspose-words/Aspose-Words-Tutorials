---
"description": "اكتشف كيفية استخدام Aspose.Words لـ .NET لاكتشاف الترقيم بالمسافات البيضاء في المستندات النصية العادية والتأكد من التعرف على القوائم الخاصة بك بشكل صحيح."
"linktitle": "اكتشاف الترقيم باستخدام المسافات البيضاء"
"second_title": "واجهة برمجة تطبيقات معالجة المستندات Aspose.Words"
"title": "اكتشاف الترقيم باستخدام المسافات البيضاء"
"url": "/ar/net/programming-with-txtloadoptions/detect-numbering-with-whitespaces/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# اكتشاف الترقيم باستخدام المسافات البيضاء

## مقدمة

Aspose.Words لعشاق .NET! اليوم، نتعمق في ميزة رائعة تُسهّل التعامل مع القوائم في مستندات النص العادي. هل سبق لك التعامل مع ملفات نصية حيث يُفترض أن تكون بعض أسطرها قوائم، لكنها لا تبدو سليمة عند تحميلها في مستند Word؟ حسنًا، لدينا حيلة رائعة: كشف الترقيم باستخدام المسافات البيضاء. سيرشدك هذا البرنامج التعليمي إلى كيفية استخدام `DetectNumberingWithWhitespaces` يمكنك استخدام الخيار الموجود في Aspose.Words لـ .NET للتأكد من التعرف على القوائم الخاصة بك بشكل صحيح، حتى عندما تكون هناك مسافة بيضاء بين الأرقام والنص.

## المتطلبات الأساسية

قبل أن نبدأ، تأكد من أن لديك ما يلي:

- Aspose.Words for .NET: يمكنك تنزيله من [إصدارات Aspose](https://releases.aspose.com/words/net/) صفحة.
- بيئة التطوير: Visual Studio أو أي بيئة تطوير متكاملة أخرى لـC#.
- تم تثبيت .NET Framework على جهازك.
- المعرفة الأساسية بلغة C#: فهم الأساسيات سوف يساعدك على متابعة الأمثلة.

## استيراد مساحات الأسماء

قبل البدء في الكود، تأكد من استيراد مساحات الأسماء اللازمة في مشروعك. إليك مقطع سريع للبدء:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Loading;
```

دعونا نقسم العملية إلى خطوات بسيطة وسهلة التنفيذ. كل خطوة سترشدك خلال الكود اللازم وتشرح ما يحدث.

## الخطوة 1: تحديد دليل المستندات الخاص بك

أولاً، لنُنشئ مسار مجلد المستندات. هذا هو المكان الذي ستُخزَّن فيه ملفات الإدخال والإخراج.

```csharp
// المسار إلى دليل المستندات الخاص بك
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## الخطوة 2: إنشاء مستند نص عادي

بعد ذلك، سننشئ مستندًا نصيًا عاديًا كسلسلة نصية. سيحتوي هذا المستند على أجزاء يمكن تفسيرها كقوائم.

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

لاكتشاف الترقيم باستخدام المسافات البيضاء، نحتاج إلى ضبط `DetectNumberingWithWhitespaces` خيار ل `true` في `TxtLoadOptions` هدف.

```csharp
TxtLoadOptions loadOptions = new TxtLoadOptions { DetectNumberingWithWhitespaces = true };
```

## الخطوة 4: تحميل المستند

الآن، دعنا نحمل المستند باستخدام `TxtLoadOptions` كمعامل. هذا يضمن اكتشاف القائمة الرابعة (مع المسافات البيضاء) بشكل صحيح.

```csharp
Document doc = new Document(new MemoryStream(Encoding.UTF8.GetBytes(textDoc)), loadOptions);
```

## الخطوة 5: حفظ المستند

أخيرًا، احفظ المستند في المجلد المُحدد. سيؤدي هذا إلى إخراج مستند Word بقوائم مُكتشفة بشكل صحيح.

```csharp
doc.Save(dataDir + "WorkingWithTxtLoadOptions.DetectNumberingWithWhitespaces.docx");
```

## خاتمة

وها أنت ذا! ببضعة أسطر برمجية فقط، أتقنتَ فنّ كشف الترقيم بالمسافات في مستندات النص العادي باستخدام Aspose.Words لـ .NET. تُعد هذه الميزة مفيدة للغاية عند التعامل مع تنسيقات نصية مختلفة وضمان تمثيل قوائمك بدقة في مستندات Word. لذا، في المرة القادمة التي تواجه فيها هذه القوائم المعقدة، ستعرف بالضبط ما يجب عليك فعله.

## الأسئلة الشائعة

### ما هو `DetectNumberingWithWhitespaces` في Aspose.Words لـ .NET؟
`DetectNumberingWithWhitespaces` هو خيار في `TxtLoadOptions` يتيح ذلك لـ Aspose.Words التعرف على القوائم حتى عندما تكون هناك مسافة بيضاء بين الترقيم ونص عنصر القائمة.

### هل يمكنني استخدام هذه الميزة لعناصر أخرى مثل النقاط والأقواس؟
نعم، يكتشف Aspose.Words تلقائيًا القوائم ذات الفواصل الشائعة مثل النقاط والأقواس. `DetectNumberingWithWhitespaces` يساعد بشكل خاص مع القوائم التي تحتوي على مسافات بيضاء.

### ماذا يحدث إذا لم أستخدم `DetectNumberingWithWhitespaces`؟
بدون هذا الخيار، قد لا يتم التعرف على القوائم التي تحتوي على مسافة بيضاء بين الترقيم والنص كقوائم، وقد تظهر العناصر كفقرات عادية.

### هل هذه الميزة متاحة في منتجات Aspose الأخرى؟
تم تصميم هذه الميزة المحددة خصيصًا لـ Aspose.Words for .NET، وهي مصممة للتعامل مع معالجة مستندات Word.

### كيف يمكنني الحصول على ترخيص مؤقت لـ Aspose.Words لـ .NET؟
يمكنك الحصول على ترخيص مؤقت من [ترخيص Aspose المؤقت](https://purchase.aspose.com/temporary-license/) صفحة.




{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}