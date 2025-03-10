---
title: الحصول على تباعد أسطر الخط
linktitle: الحصول على تباعد أسطر الخط
second_title: واجهة برمجة تطبيقات معالجة المستندات Aspose.Words
description: تعرف على كيفية الحصول على مسافات بين أسطر الخطوط باستخدام Aspose.Words for .NET من خلال هذا البرنامج التعليمي خطوة بخطوة. مثالي للمطورين.
weight: 10
url: /ar/net/working-with-fonts/get-font-line-spacing/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# الحصول على تباعد أسطر الخط

## مقدمة

Aspose.Words for .NET هي مكتبة قوية تتيح لك إنشاء مستندات Word ومعالجتها وتحويلها برمجيًا. إحدى المهام الشائعة التي قد تحتاج إلى القيام بها هي استرداد المسافة بين السطور لخط معين في مستند. في هذا البرنامج التعليمي، سنوضح لك العملية خطوة بخطوة، مما يضمن لك إمكانية الحصول بسهولة على المسافة بين السطور للخط باستخدام Aspose.Words for .NET. 

## المتطلبات الأساسية

قبل أن نتعمق في الكود، تأكد من توفر المتطلبات الأساسية التالية:

1.  Aspose.Words for .NET Library: قم بتنزيل أحدث إصدار وتثبيته من[هنا](https://releases.aspose.com/words/net/).
2. بيئة التطوير: تأكد من أن لديك بيئة تطوير متكاملة مثل Visual Studio.
3. المعرفة الأساسية بلغة C#: يفترض هذا البرنامج التعليمي أن لديك فهمًا أساسيًا لبرمجة C#.

## استيراد مساحات الأسماء

أولاً، تحتاج إلى استيراد المساحات الأساسية اللازمة في مشروع C# الخاص بك. ستتيح لك هذه المساحات الأساسية الوصول إلى وظائف Aspose.Words.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;
```

دعونا نقوم بتقسيم عملية الحصول على تباعد أسطر الخط إلى خطوات بسيطة يمكن التحكم فيها.

## الخطوة 1: إنشاء مستند جديد

الخطوة الأولى هي إنشاء مثيل جديد لمستند Word باستخدام Aspose.Words لـ .NET.

```csharp
Document doc = new Document();
```

## الخطوة 2: تهيئة DocumentBuilder

بعد ذلك، نحتاج إلى تهيئة`DocumentBuilder` هذا الكائن سيساعدنا في إنشاء محتوى المستند ومعالجته.

```csharp
DocumentBuilder builder = new DocumentBuilder(doc);
```

## الخطوة 3: تعيين خصائص الخط

الآن، نقوم بتعيين خصائص الخط للنص الذي نريد إدراجه. في هذا المثال، سنستخدم الخط "Calibri".

```csharp
builder.Font.Name = "Calibri";
```

## الخطوة 4: كتابة نص في المستند

 استخدام`DocumentBuilder` الكائن، اكتب نصًا في المستند. سيستخدم هذا النص خصائص الخط التي حددناها في الخطوة السابقة.

```csharp
builder.Writeln("Sample Text");
```

## الخطوة 5: استرداد كائن الخط

للحصول على مسافة السطور، نحتاج إلى الوصول إلى كائن الخط للنص الذي أضفناه للتو. ويمكن القيام بذلك من خلال التنقل عبر بنية المستند إلى الفقرة الأولى.

```csharp
Font font = builder.Document.FirstSection.Body.FirstParagraph.Runs[0].Font;
```

## الخطوة 6: الحصول على تباعد الأسطر

وأخيرًا، نستعيد مسافة السطور من كائن الخط ونطبعها في وحدة التحكم.

```csharp
Console.WriteLine($"lineSpacing = {font.LineSpacing}");
```

## خاتمة

والآن لديك كل ما تحتاج إليه! إن استرداد مسافات الخطوط باستخدام Aspose.Words لـ .NET أمر سهل عندما تقسمه إلى هذه الخطوات البسيطة. سواء كنت تقوم بإنشاء مستند جديد أو تعمل على مستند موجود، فإن Aspose.Words يوفر لك كل الأدوات التي تحتاجها لإدارة خصائص الخط بكفاءة.

## الأسئلة الشائعة

### ما هو Aspose.Words لـ .NET؟
Aspose.Words for .NET هي مكتبة قوية تسمح للمطورين بإنشاء مستندات Word ومعالجتها وتحويلها برمجيًا باستخدام C#.

### هل يمكنني استخدام Aspose.Words لـ .NET في لغات .NET الأخرى؟
نعم، يمكنك استخدام Aspose.Words لـ .NET مع أي لغة .NET، بما في ذلك VB.NET وF#.

### كيف يمكنني تنزيل Aspose.Words لـ .NET؟
 يمكنك تنزيل أحدث إصدار من Aspose.Words لـ .NET من[هنا](https://releases.aspose.com/words/net/).

### هل هناك نسخة تجريبية مجانية متاحة لـ Aspose.Words لـ .NET؟
 نعم، يمكنك الحصول على نسخة تجريبية مجانية من[هنا](https://releases.aspose.com/).

### أين يمكنني العثور على الوثائق الخاصة بـ Aspose.Words لـ .NET؟
 الوثائق الخاصة بـ Aspose.Words لـ .NET متاحة[هنا](https://reference.aspose.com/words/net/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
