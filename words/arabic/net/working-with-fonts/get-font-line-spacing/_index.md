---
"description": "تعلّم كيفية ضبط مسافات أسطر الخطوط باستخدام Aspose.Words لـ .NET من خلال هذا البرنامج التعليمي خطوة بخطوة. مثالي للمطورين."
"linktitle": "الحصول على تباعد أسطر الخط"
"second_title": "واجهة برمجة تطبيقات معالجة المستندات Aspose.Words"
"title": "الحصول على تباعد أسطر الخط"
"url": "/ar/net/working-with-fonts/get-font-line-spacing/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# الحصول على تباعد أسطر الخط

## مقدمة

Aspose.Words for .NET هي مكتبة فعّالة تُمكّنك من إنشاء مستندات Word وتعديلها وتحويلها برمجيًا. من المهام الشائعة التي قد تحتاج إلى تنفيذها استعادة تباعد أسطر خط مُحدد في مستند. في هذا البرنامج التعليمي، سنشرح لك العملية خطوة بخطوة، مما يضمن لك سهولة الحصول على تباعد أسطر الخط باستخدام Aspose.Words for .NET. 

## المتطلبات الأساسية

قبل أن نتعمق في الكود، تأكد من أن لديك المتطلبات الأساسية التالية:

1. Aspose.Words for .NET Library: قم بتنزيل أحدث إصدار وتثبيته من [هنا](https://releases.aspose.com/words/net/).
2. بيئة التطوير: تأكد من أن لديك بيئة تطوير متكاملة مثل Visual Studio.
3. المعرفة الأساسية بلغة C#: يفترض هذا البرنامج التعليمي أن لديك فهمًا أساسيًا لبرمجة C#.

## استيراد مساحات الأسماء

أولاً، عليك استيراد مساحات الأسماء اللازمة في مشروع C#. ستتيح لك هذه المساحات الوصول إلى وظائف Aspose.Words.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;
```

دعونا نقسم عملية الحصول على مسافة بين أسطر الخط إلى خطوات بسيطة يمكن التحكم فيها.

## الخطوة 1: إنشاء مستند جديد

الخطوة الأولى هي إنشاء مثيل جديد لمستند Word باستخدام Aspose.Words لـ .NET.

```csharp
Document doc = new Document();
```

## الخطوة 2: تهيئة DocumentBuilder

بعد ذلك، نحتاج إلى تهيئة `DocumentBuilder` هذا الكائن سيساعدنا في إنشاء محتوى المستند ومعالجته.

```csharp
DocumentBuilder builder = new DocumentBuilder(doc);
```

## الخطوة 3: تعيين خصائص الخط

الآن، نضبط خصائص الخط للنص الذي نريد إدراجه. في هذا المثال، سنستخدم خط "Calibri".

```csharp
builder.Font.Name = "Calibri";
```

## الخطوة 4: كتابة نص إلى المستند

باستخدام `DocumentBuilder` كائن، اكتب نصًا في المستند. سيستخدم هذا النص خصائص الخط التي حددناها في الخطوة السابقة.

```csharp
builder.Writeln("Sample Text");
```

## الخطوة 5: استرداد كائن الخط

للحصول على تباعد الأسطر، علينا الوصول إلى عنصر الخط في النص الذي أضفناه. يمكن القيام بذلك بالانتقال عبر بنية المستند إلى الفقرة الأولى.

```csharp
Font font = builder.Document.FirstSection.Body.FirstParagraph.Runs[0].Font;
```

## الخطوة 6: الحصول على تباعد الأسطر

وأخيرًا، نسترد مسافة السطور من كائن الخط ونطبعها في وحدة التحكم.

```csharp
Console.WriteLine($"lineSpacing = {font.LineSpacing}");
```

## خاتمة

وهذا كل ما في الأمر! استعادة تباعد أسطر الخط باستخدام Aspose.Words لـ .NET أمرٌ سهلٌ للغاية، فقط اتبع هذه الخطوات البسيطة. سواءً كنت تُنشئ مستندًا جديدًا أو تعمل على مستند موجود، يوفر Aspose.Words جميع الأدوات اللازمة لإدارة خصائص الخط بكفاءة.

## الأسئلة الشائعة

### ما هو Aspose.Words لـ .NET؟
Aspose.Words for .NET هي مكتبة قوية تسمح للمطورين بإنشاء مستندات Word ومعالجتها وتحويلها برمجيًا باستخدام C#.

### هل يمكنني استخدام Aspose.Words لـ .NET في لغات .NET الأخرى؟
نعم، يمكنك استخدام Aspose.Words لـ .NET مع أي لغة .NET، بما في ذلك VB.NET وF#.

### كيف يمكنني تنزيل Aspose.Words لـ .NET؟
يمكنك تنزيل أحدث إصدار من Aspose.Words لـ .NET من [هنا](https://releases.aspose.com/words/net/).

### هل هناك نسخة تجريبية مجانية متاحة لـ Aspose.Words لـ .NET؟
نعم، يمكنك الحصول على نسخة تجريبية مجانية من [هنا](https://releases.aspose.com/).

### أين يمكنني العثور على الوثائق الخاصة بـ Aspose.Words لـ .NET؟
تتوفر وثائق Aspose.Words لـ .NET [هنا](https://reference.aspose.com/words/net/).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}