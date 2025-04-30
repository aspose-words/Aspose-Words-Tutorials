---
"description": "تعلّم كيفية تطبيق تنسيق الشطب على النص باستخدام Aspose.Words لـ .NET من خلال دليلنا المفصل. طوّر مهاراتك في معالجة المستندات."
"linktitle": "شطب"
"second_title": "واجهة برمجة تطبيقات معالجة المستندات Aspose.Words"
"title": "شطب"
"url": "/ar/net/working-with-markdown/strikethrough/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# شطب

## مقدمة

مرحبًا بكم في هذا الدليل المفصل حول كيفية تطبيق تنسيق الشطب على النص باستخدام Aspose.Words لـ .NET. إذا كنت ترغب في تحسين مهاراتك في معالجة المستندات وإضافة لمسة مميزة إلى نصك، فأنت في المكان المناسب. هيا بنا!

## المتطلبات الأساسية

قبل أن نبدأ، تأكد من أن لديك ما يلي:

- Aspose.Words لـ .NET: تنزيله [هنا](https://releases.aspose.com/words/net/).
- .NET Framework: تأكد من تثبيت .NET Framework على نظامك.
- بيئة التطوير: بيئة تطوير متكاملة مثل Visual Studio.
- المعرفة الأساسية بلغة C#: المعرفة ببرمجة C# ضرورية.

## استيراد مساحات الأسماء

للبدء، ستحتاج إلى استيراد مساحات الأسماء اللازمة. هذه ضرورية للوصول إلى مكتبة Aspose.Words وميزاتها.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;
```

## الخطوة 1: تهيئة DocumentBuilder

ال `DocumentBuilder` تعتبر الفئة أداة قوية في Aspose.Words تسمح لك بإضافة محتوى إلى مستندك بسهولة.

```csharp
// تهيئة DocumentBuilder.
DocumentBuilder builder = new DocumentBuilder();
```

## الخطوة 2: تعيين خاصية الشطب

الآن، لنطبّق خاصية الشطب على نصنا. يتضمن هذا ضبط `StrikeThrough` ممتلكات `Font` الاعتراض على `true`.

```csharp
// اجعل النص مشطوبًا.
builder.Font.StrikeThrough = true;
```

## الخطوة 3: كتابة النص مع الشطب

مع ضبط خاصية الشطب، يمكننا الآن إضافة النص الخاص بنا. `Writeln` ستضيف هذه الطريقة النص إلى المستند.

```csharp
// اكتب نصًا مع الشطب.
builder.Writeln("This text will be StrikeThrough");
```

## خاتمة

ها قد انتهيت! لقد نجحت في إضافة تنسيق الشطب إلى نصك باستخدام Aspose.Words لـ .NET. تفتح هذه المكتبة القوية آفاقًا واسعة لمعالجة المستندات وتخصيصها. سواء كنت تُنشئ تقارير أو رسائل أو أي نوع آخر من المستندات، فإن إتقان هذه الميزات سيعزز بلا شك إنتاجيتك وجودة مخرجاتك.

## الأسئلة الشائعة

### ما هو Aspose.Words لـ .NET؟
Aspose.Words for .NET هي مكتبة معالجة مستندات قوية تسمح للمطورين بإنشاء مستندات Word ومعالجتها وتحويلها برمجيًا.

### هل يمكنني استخدام Aspose.Words لـ .NET في مشروع تجاري؟
نعم، يمكنك استخدام Aspose.Words لـ .NET في المشاريع التجارية. للاطلاع على خيارات الشراء، تفضل بزيارة [صفحة الشراء](https://purchase.aspose.com/buy).

### هل هناك نسخة تجريبية مجانية متاحة لـ Aspose.Words لـ .NET؟
نعم، يمكنك تنزيل نسخة تجريبية مجانية [هنا](https://releases.aspose.com/).

### كيف أحصل على الدعم لـ Aspose.Words لـ .NET؟
يمكنك الحصول على الدعم من مجتمع Aspose والخبراء في [منتدى الدعم](https://forum.aspose.com/c/words/8).

### هل يمكنني تطبيق خيارات تنسيق النص الأخرى باستخدام Aspose.Words لـ .NET؟
بالتأكيد! يدعم Aspose.Words for .NET مجموعة واسعة من خيارات تنسيق النصوص، بما في ذلك الغامق والمائل والتسطير وغيرها.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}