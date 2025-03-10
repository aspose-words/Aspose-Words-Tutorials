---
title: شطب
linktitle: شطب
second_title: واجهة برمجة تطبيقات معالجة المستندات Aspose.Words
description: تعرف على كيفية تطبيق تنسيق الشطب على النص باستخدام Aspose.Words for .NET من خلال دليلنا خطوة بخطوة. قم بتحسين مهاراتك في معالجة المستندات.
weight: 10
url: /ar/net/working-with-markdown/strikethrough/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# شطب

## مقدمة

مرحبًا بك في هذا الدليل التفصيلي حول كيفية تطبيق تنسيق الشطب على النص باستخدام Aspose.Words for .NET. إذا كنت تتطلع إلى تحسين مهارات معالجة المستندات وإضافة لمسة فريدة إلى نصك، فأنت في المكان المناسب. دعنا نتعمق في الأمر!

## المتطلبات الأساسية

قبل أن نبدأ، تأكد من أن لديك ما يلي:

-  Aspose.Words for .NET: قم بتنزيله[هنا](https://releases.aspose.com/words/net/).
- .NET Framework: تأكد من تثبيت .NET Framework على نظامك.
- بيئة التطوير: بيئة تطوير متكاملة مثل Visual Studio.
- المعرفة الأساسية بلغة C#: المعرفة ببرمجة C# ضرورية.

## استيراد مساحات الأسماء

للبدء، ستحتاج إلى استيراد مساحات الأسماء الضرورية. وهي ضرورية للوصول إلى مكتبة Aspose.Words وميزاتها.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;
```

## الخطوة 1: تهيئة DocumentBuilder

 ال`DocumentBuilder` class هي أداة قوية في Aspose.Words تسمح لك بإضافة محتوى إلى مستندك بسهولة.

```csharp
// تهيئة DocumentBuilder.
DocumentBuilder builder = new DocumentBuilder();
```

## الخطوة 2: تعيين خاصية الشطب

الآن، دعنا نطبق خاصية الشطب على النص الخاص بنا. يتضمن هذا ضبط`StrikeThrough` ممتلكات`Font` الاعتراض على`true`.

```csharp
// اجعل النص مشطوبا.
builder.Font.StrikeThrough = true;
```

## الخطوة 3: كتابة النص مع الشطب

 مع تعيين خاصية الشطب، يمكننا الآن إضافة النص الخاص بنا.`Writeln` ستضيف هذه الطريقة النص إلى المستند.

```csharp
// اكتب نصًا بخط مشطوب.
builder.Writeln("This text will be StrikeThrough");
```

## خاتمة

والآن، لقد نجحت في إضافة تنسيق الشطب إلى نصك باستخدام Aspose.Words for .NET. تفتح هذه المكتبة القوية عالمًا من الاحتمالات لمعالجة المستندات وتخصيصها. سواء كنت تقوم بإنشاء تقارير أو رسائل أو أي نوع آخر من المستندات، فإن إتقان هذه الميزات سيعزز بلا شك إنتاجيتك وجودة مخرجاتك.

## الأسئلة الشائعة

### ما هو Aspose.Words لـ .NET؟
Aspose.Words for .NET هي مكتبة معالجة مستندات قوية تتيح للمطورين إنشاء مستندات Word ومعالجتها وتحويلها برمجيًا.

### هل يمكنني استخدام Aspose.Words لـ .NET في مشروع تجاري؟
 نعم، يمكنك استخدام Aspose.Words لـ .NET في المشاريع التجارية. لمعرفة خيارات الشراء، تفضل بزيارة[صفحة الشراء](https://purchase.aspose.com/buy).

### هل هناك نسخة تجريبية مجانية متاحة لـ Aspose.Words لـ .NET؟
 نعم، يمكنك تنزيل نسخة تجريبية مجانية[هنا](https://releases.aspose.com/).

### كيف أحصل على الدعم لـ Aspose.Words لـ .NET؟
يمكنك الحصول على الدعم من مجتمع Aspose والخبراء في[منتدى الدعم](https://forum.aspose.com/c/words/8).

### هل يمكنني تطبيق خيارات تنسيق النص الأخرى باستخدام Aspose.Words لـ .NET؟
بالتأكيد! يدعم Aspose.Words for .NET مجموعة واسعة من خيارات تنسيق النص بما في ذلك النص الغامق والمائل والخط المسطر وغير ذلك الكثير.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
