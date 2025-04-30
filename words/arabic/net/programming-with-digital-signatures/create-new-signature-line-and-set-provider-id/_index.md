---
"description": "تعرّف على كيفية إنشاء سطر توقيع جديد وتعيين مُعرّف المُزوّد في مستندات Word باستخدام Aspose.Words لـ .NET. دليل خطوة بخطوة."
"linktitle": "إنشاء سطر توقيع جديد وتعيين معرف الموفر"
"second_title": "واجهة برمجة تطبيقات معالجة المستندات Aspose.Words"
"title": "إنشاء سطر توقيع جديد وتعيين معرف الموفر"
"url": "/ar/net/programming-with-digital-signatures/create-new-signature-line-and-set-provider-id/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# إنشاء سطر توقيع جديد وتعيين معرف الموفر

## مقدمة

أهلاً بكم يا عشاق التقنية! هل تساءلتم يوماً عن كيفية إضافة سطر توقيع في مستندات Word برمجياً؟ حسناً، سنتعمق اليوم في ذلك باستخدام Aspose.Words لـ .NET. سيشرح لكم هذا الدليل كل خطوة، مما يجعل إنشاء سطر توقيع جديد وتعيين معرف الموفر في مستندات Word في غاية السهولة. سواء كنتم تعملون على أتمتة معالجة المستندات أو ترغبون فقط في تبسيط سير عملكم، فهذا الدليل سيلبي جميع احتياجاتكم.

## المتطلبات الأساسية

قبل أن نبدأ في العمل، دعونا نتأكد من أننا حصلنا على كل ما نحتاجه:

1. Aspose.Words for .NET: إذا لم تقم بتنزيله بالفعل، فقم بتنزيله [هنا](https://releases.aspose.com/words/net/).
2. بيئة التطوير: Visual Studio أو أي بيئة تطوير C# أخرى.
3. .NET Framework: تأكد من تثبيت .NET Framework.
4. شهادة PFX: لتوقيع المستندات، ستحتاج إلى شهادة PFX. يمكنك الحصول عليها من جهة إصدار شهادات موثوقة.

## استيراد مساحات الأسماء

أولاً وقبل كل شيء، دعنا نستورد المساحات الأساسية اللازمة في مشروع C# الخاص بك:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Signing;
using System;
```

حسنًا، لنبدأ بالتفاصيل. إليك شرح مفصل لكل خطوة لإنشاء سطر توقيع جديد وتعيين معرف المزوّد.

## الخطوة 1: إنشاء مستند جديد

للبدء، علينا إنشاء مستند وورد جديد. سيكون هذا هو مساحة العمل لتوقيعنا.

```csharp
// المسار إلى دليل المستندات.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

في هذا المقطع، نقوم بتهيئة ملف جديد `Document` و أ `DocumentBuilder`. ال `DocumentBuilder` يساعدنا على إضافة عناصر إلى مستندنا.

## الخطوة 2: تحديد خيارات سطر التوقيع

بعد ذلك، نُحدد خيارات سطر التوقيع. يتضمن ذلك اسم المُوقّع، ولقبه، وبريده الإلكتروني، وتفاصيل أخرى.

```csharp
SignatureLineOptions signatureLineOptions = new SignatureLineOptions
{
    Signer = "vderyushev",
    SignerTitle = "QA",
    Email = "vderyushev@aspose.com",
    ShowDate = true,
    DefaultInstructions = false,
    Instructions = "Please sign here.",
    AllowComments = true
};
```

تعمل هذه الخيارات على تخصيص خط التوقيع، مما يجعله واضحًا واحترافيًا.

## الخطوة 3: إدراج سطر التوقيع

بعد ضبط خياراتنا، يمكننا الآن إدراج سطر التوقيع في المستند.

```csharp
SignatureLine signatureLine = builder.InsertSignatureLine(signatureLineOptions).SignatureLine;
signatureLine.ProviderId = Guid.Parse("CF5A7BB4-8F3C-4756-9DF6-BEF7F13259A2");
```

هنا، `InsertSignatureLine` تضيف الطريقة سطر التوقيع، ونقوم بتعيين معرف مزود فريد له.

## الخطوة 4: حفظ المستند

بعد إدخال سطر التوقيع، دعنا نحفظ المستند.

```csharp
doc.Save(dataDir + "SignDocuments.SignatureLineProviderId.docx");
```

يؤدي هذا إلى حفظ مستندك بسطر التوقيع المضاف حديثًا.

## الخطوة 5: إعداد خيارات التوقيع

الآن، علينا ضبط خيارات توقيع المستند. يتضمن ذلك مُعرِّف سطر التوقيع، ومُعرِّف المُزوِّد، والتعليقات، ووقت التوقيع.

```csharp
SignOptions signOptions = new SignOptions
{
    SignatureLineId = signatureLine.Id,
    ProviderId = signatureLine.ProviderId,
    Comments = "Document was signed by vderyushev",
    SignTime = DateTime.Now
};
```

تضمن هذه الخيارات توقيع المستند بالتفاصيل الصحيحة.

## الخطوة 6: إنشاء حامل الشهادة

لتوقيع الوثيقة، سنستخدم شهادة PFX. لنُنشئ حامل شهادة لها.

```csharp
CertificateHolder certHolder = CertificateHolder.Create(dataDir + "morzal.pfx", "aw");
```

تأكد من الاستبدال `"morzal.pfx"` مع ملف الشهادة الفعلي الخاص بك و `"aw"` مع كلمة المرور الخاصة بشهادتك.

## الخطوة 7: توقيع الوثيقة

وأخيرًا، نقوم بتوقيع المستند باستخدام أداة التوقيع الرقمي.

```csharp
DigitalSignatureUtil.Sign(dataDir + "SignDocuments.SignatureLineProviderId.docx", 
    dataDir + "SignDocuments.CreateNewSignatureLineAndSetProviderId.docx", certHolder, signOptions);
```

يؤدي هذا إلى توقيع المستند وحفظه كملف جديد.

## خاتمة

وها أنت ذا! لقد نجحت في إنشاء سطر توقيع جديد وتعيين مُعرّف المُزوّد في مستند Word باستخدام Aspose.Words لـ .NET. تُسهّل هذه المكتبة القوية إدارة مهام معالجة المستندات وأتمتتها بشكل كبير. جرّبها وشاهد كيف يُمكنها تبسيط سير عملك.

## الأسئلة الشائعة

### هل يمكنني تخصيص مظهر خط التوقيع؟
بالتأكيد! يمكنك تعديل خيارات مختلفة في `SignatureLineOptions` لتناسب احتياجاتك.

### ماذا لو لم يكن لدي شهادة PFX؟
ستحتاج إلى الحصول على شهادة من جهة إصدار شهادات موثوقة. فهي ضرورية للتوقيع الرقمي للمستندات.

### هل يمكنني إضافة أسطر توقيع متعددة إلى مستند؟
نعم، يمكنك إضافة عدد كبير من أسطر التوقيع حسب الحاجة عن طريق تكرار عملية الإدراج باستخدام خيارات مختلفة.

### هل Aspose.Words for .NET متوافق مع .NET Core؟
نعم، يدعم Aspose.Words for .NET .NET Core، مما يجعله متعدد الاستخدامات لبيئات التطوير المختلفة.

### ما مدى أمان التوقيعات الرقمية؟
تعتبر التوقيعات الرقمية التي تم إنشاؤها باستخدام Aspose.Words آمنة للغاية، بشرط استخدام شهادة صالحة وموثوقة.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}