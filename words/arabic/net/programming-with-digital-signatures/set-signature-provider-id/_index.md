---
title: تعيين معرف موفر التوقيع في مستند Word
linktitle: تعيين معرف موفر التوقيع في مستند Word
second_title: واجهة برمجة تطبيقات معالجة المستندات Aspose.Words
description: قم بتعيين معرف موفر التوقيع بشكل آمن في مستندات Word باستخدام Aspose.Words for .NET. اتبع دليلنا المفصل المكون من 2000 كلمة للتوقيع رقميًا على مستنداتك.
weight: 10
url: /ar/net/programming-with-digital-signatures/set-signature-provider-id/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# تعيين معرف موفر التوقيع في مستند Word

## مقدمة

مرحبًا! إذًا، لديك مستند Word مذهل يحتاج إلى توقيع رقمي، أليس كذلك؟ ولكن ليس أي توقيع فحسب، بل تحتاج إلى تعيين معرف موفر توقيع محدد. سواء كنت تتعامل مع مستندات قانونية أو عقود أو أي مستندات ورقية، فإن إضافة توقيع رقمي آمن أمر بالغ الأهمية. في هذا البرنامج التعليمي، سأقوم بإرشادك خلال العملية الكاملة لتعيين معرف موفر التوقيع في مستند Word باستخدام Aspose.Words for .NET. هل أنت مستعد؟ لنبدأ!

## المتطلبات الأساسية

قبل أن نبدأ، تأكد من أن لديك ما يلي:

1. Aspose.Words لمكتبة .NET: إذا لم تقم بذلك بالفعل،[تحميله هنا](https://releases.aspose.com/words/net/).
2. بيئة التطوير: Visual Studio أو أي بيئة تطوير متكاملة متوافقة مع C#.
3. مستند Word: مستند يحتوي على سطر توقيع (`Signature line.docx`).
4.  الشهادة الرقمية: أ`.pfx` ملف الشهادة (على سبيل المثال،`morzal.pfx`).
5. المعرفة الأساسية بلغة C#: فقط الأساسيات - لا تقلق، نحن هنا لمساعدتك!

الآن دعونا ننتقل إلى العمل!

## استيراد مساحات الأسماء

أولاً وقبل كل شيء، تأكد من تضمين مساحات الأسماء الضرورية في مشروعك. يعد هذا ضروريًا للوصول إلى مكتبة Aspose.Words والفئات ذات الصلة.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.DigitalSignatures;
```

حسنًا، دعونا نقسم هذا إلى خطوات بسيطة وسهلة الهضم.

## الخطوة 1: قم بتحميل مستند Word الخاص بك

الخطوة الأولى هي تحميل مستند Word الذي يحتوي على سطر التوقيع. سيتم تعديل هذا المستند ليشمل التوقيع الرقمي مع معرف موفر التوقيع المحدد.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Signature line.docx");
```

 هنا، نحدد الدليل الذي يوجد به مستندك. استبدل`"YOUR DOCUMENT DIRECTORY"` مع المسار الفعلي للمستند الخاص بك.

## الخطوة 2: الوصول إلى خط التوقيع

بعد ذلك، نحتاج إلى الوصول إلى سطر التوقيع داخل المستند. يتم تضمين سطر التوقيع ككائن شكل في مستند Word.

```csharp
SignatureLine signatureLine = ((Shape)doc.FirstSection.Body.GetChild(NodeType.Shape, 0, true)).SignatureLine;
```

 يحصل هذا السطر من التعليمات البرمجية على الشكل الأول في نص القسم الأول من المستند وينقله إلى`SignatureLine` هدف.

## الخطوة 3: إعداد خيارات الإشارة

الآن، نقوم بإنشاء خيارات التوقيع، والتي تتضمن معرف المزود ومعرف سطر التوقيع من سطر التوقيع الذي تم الوصول إليه.

```csharp
SignOptions signOptions = new SignOptions
{
    ProviderId = signatureLine.ProviderId,
    SignatureLineId = signatureLine.Id
};
```

سيتم استخدام هذه الخيارات عند توقيع المستند للتأكد من تعيين معرف موفر التوقيع الصحيح.

## الخطوة 4: تحميل الشهادة

 لتوقيع المستند رقميًا، تحتاج إلى شهادة. إليك كيفية تحميل`.pfx` ملف:

```csharp
CertificateHolder certHolder = CertificateHolder.Create(dataDir + "morzal.pfx", "aw");
```

 يستبدل`"aw"` مع كلمة المرور لملف الشهادة الخاص بك إذا كان لديه واحدة.

## الخطوة 5: توقيع الوثيقة

 وأخيرًا، حان الوقت لتوقيع الوثيقة باستخدام`DigitalSignatureUtil.Sign` طريقة.

```csharp
DigitalSignatureUtil.Sign(dataDir + "Digitally signed.docx",
    dataDir + "SignDocuments.SetSignatureProviderId.docx", certHolder, signOptions);
```

 يؤدي هذا إلى توقيع مستندك وحفظه كملف جديد،`Digitally signed.docx`.

## خاتمة

والآن، لقد نجحت في تعيين معرف موفر التوقيع في مستند Word باستخدام Aspose.Words لـ .NET. لا تعمل هذه العملية على تأمين مستنداتك فحسب، بل تضمن أيضًا توافقها مع معايير التوقيع الرقمي. الآن، امض قدمًا وجربها مع مستنداتك. هل لديك أي أسئلة؟ راجع الأسئلة الشائعة أدناه أو انقر فوق[منتدى دعم Aspose](https://forum.aspose.com/c/words/8).

## الأسئلة الشائعة

### ما هو معرف مزود التوقيع؟

يحدد معرف مزود التوقيع بشكل فريد مزود التوقيع الرقمي، مما يضمن الأصالة والأمان.

### هل يمكنني استخدام أي ملف .pfx للتوقيع؟

نعم، طالما أنها شهادة رقمية صالحة. تأكد من استخدام كلمة المرور الصحيحة إذا كانت محمية.

### كيف أحصل على ملف .pfx؟

يمكنك الحصول على ملف .pfx من هيئة إصدار الشهادات (CA) أو إنشاء ملف باستخدام أدوات مثل OpenSSL.

### هل يمكنني التوقيع على مستندات متعددة في وقت واحد؟

نعم، يمكنك المرور عبر مستندات متعددة وتطبيق نفس عملية التوقيع على كل منها.

### ماذا لو لم يكن لدي سطر توقيع في مستندي؟

سوف تحتاج إلى إدراج سطر توقيع أولاً. يوفر Aspose.Words طرقًا لإضافة أسطر توقيع برمجيًا.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
