---
"description": "عيّن مُعرّف مُزوّد التوقيع بأمان في مستندات Word باستخدام Aspose.Words لـ .NET. اتبع دليلنا المُفصّل، المُكوّن من 2000 كلمة، لتوقيع مستنداتك رقميًا."
"linktitle": "تعيين معرف موفر التوقيع في مستند Word"
"second_title": "واجهة برمجة تطبيقات معالجة المستندات Aspose.Words"
"title": "تعيين معرف موفر التوقيع في مستند Word"
"url": "/ar/net/programming-with-digital-signatures/set-signature-provider-id/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# تعيين معرف موفر التوقيع في مستند Word

## مقدمة

أهلاً! لديك إذن مستند وورد رائع يحتاج إلى توقيع رقمي، أليس كذلك؟ ولكن ليس أي توقيع، بل عليك تعيين مُعرّف مُحدد لمُزوّد التوقيع. سواء كنت تُعالج مستندات قانونية أو عقودًا أو أي أوراق رسمية، فإن إضافة توقيع رقمي آمن أمرٌ بالغ الأهمية. في هذا البرنامج التعليمي، سأشرح لك العملية الكاملة لتعيين مُعرّف مُزوّد التوقيع في مستند وورد باستخدام Aspose.Words لـ .NET. هل أنت مستعد؟ هيا بنا!

## المتطلبات الأساسية

قبل أن نبدأ، تأكد من أن لديك ما يلي:

1. Aspose.Words لمكتبة .NET: إذا لم تقم بذلك بالفعل، [قم بتحميله هنا](https://releases.aspose.com/words/net/).
2. بيئة التطوير: Visual Studio أو أي بيئة تطوير متكاملة متوافقة مع C#.
3. مستند Word: مستند يحتوي على سطر توقيع (`Signature line.docx`).
4. الشهادة الرقمية: أ `.pfx` ملف الشهادة (على سبيل المثال، `morzal.pfx`).
5. المعرفة الأساسية بلغة C#: فقط الأساسيات - لا تقلق، نحن هنا لمساعدتك!

الآن دعونا ننتقل إلى العمل!

## استيراد مساحات الأسماء

أولاً، تأكد من تضمين مساحات الأسماء اللازمة في مشروعك. هذا ضروري للوصول إلى مكتبة Aspose.Words والفئات ذات الصلة.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.DigitalSignatures;
```

حسنًا، دعنا نقسم هذا إلى خطوات بسيطة وسهلة الهضم.

## الخطوة 1: تحميل مستند Word الخاص بك

الخطوة الأولى هي تحميل مستند Word الذي يحتوي على سطر التوقيع. سيتم تعديل هذا المستند ليشمل التوقيع الرقمي مع مُعرّف مُزوّد التوقيع المُحدد.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Signature line.docx");
```

هنا، نحدد الدليل الذي يوجد فيه مستندك. استبدل `"YOUR DOCUMENT DIRECTORY"` مع المسار الفعلي للمستند الخاص بك.

## الخطوة 2: الوصول إلى خط التوقيع

بعد ذلك، علينا الوصول إلى سطر التوقيع داخل المستند. سطر التوقيع مُضمّن ككائن شكل في مستند Word.

```csharp
SignatureLine signatureLine = ((Shape)doc.FirstSection.Body.GetChild(NodeType.Shape, 0, true)).SignatureLine;
```

يحصل هذا السطر من التعليمات البرمجية على الشكل الأول في نص القسم الأول من المستند ويحوله إلى `SignatureLine` هدف.

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

لتوقيع المستند رقميًا، تحتاج إلى شهادة. إليك كيفية تحميل ملفك `.pfx` ملف:

```csharp
CertificateHolder certHolder = CertificateHolder.Create(dataDir + "morzal.pfx", "aw");
```

يستبدل `"aw"` مع كلمة المرور لملف الشهادة الخاص بك إذا كان لديه واحدة.

## الخطوة 5: توقيع الوثيقة

وأخيرًا، حان الوقت لتوقيع الوثيقة باستخدام `DigitalSignatureUtil.Sign` طريقة.

```csharp
DigitalSignatureUtil.Sign(dataDir + "Digitally signed.docx",
    dataDir + "SignDocuments.SetSignatureProviderId.docx", certHolder, signOptions);
```

يؤدي هذا إلى توقيع مستندك وحفظه كملف جديد، `Digitally signed.docx`.

## خاتمة

وها قد انتهيت! لقد نجحت في تعيين مُعرّف مُزوّد التوقيع في مستند Word باستخدام Aspose.Words لـ .NET. هذه العملية لا تُؤمّن مستنداتك فحسب، بل تضمن أيضًا توافقها مع معايير التوقيع الرقمي. الآن، جرّبها مع مستنداتك. هل لديك أي أسئلة؟ تفقّد الأسئلة الشائعة أدناه أو انقر على [منتدى دعم Aspose](https://forum.aspose.com/c/words/8).

## الأسئلة الشائعة

### ما هو معرف مزود التوقيع؟

يقوم معرف مزود التوقيع بتحديد هوية مزود التوقيع الرقمي بشكل فريد، مما يضمن الأصالة والأمان.

### هل يمكنني استخدام أي ملف .pfx للتوقيع؟

نعم، طالما أنها شهادة رقمية صالحة. تأكد من استخدام كلمة المرور الصحيحة إذا كانت محمية.

### كيف أحصل على ملف .pfx؟

يمكنك الحصول على ملف .pfx من هيئة إصدار الشهادات (CA) أو إنشاء ملف باستخدام أدوات مثل OpenSSL.

### هل يمكنني التوقيع على عدة مستندات في وقت واحد؟

نعم، يمكنك المرور عبر مستندات متعددة وتطبيق نفس عملية التوقيع على كل منها.

### ماذا لو لم يكن لدي سطر توقيع في مستندي؟

ستحتاج أولاً إلى إدراج سطر توقيع. يوفر Aspose.Words طرقًا لإضافة أسطر توقيع برمجيًا.



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}