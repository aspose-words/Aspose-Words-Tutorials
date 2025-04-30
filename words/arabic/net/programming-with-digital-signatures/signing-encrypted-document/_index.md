---
"description": "تعرّف على كيفية توقيع مستندات Word مشفرة باستخدام Aspose.Words لـ .NET من خلال هذا الدليل المفصل خطوة بخطوة. مثالي للمطورين."
"linktitle": "توقيع مستند Word مشفر"
"second_title": "واجهة برمجة تطبيقات معالجة المستندات Aspose.Words"
"title": "توقيع مستند Word مشفر"
"url": "/ar/net/programming-with-digital-signatures/signing-encrypted-document/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# توقيع مستند Word مشفر

## مقدمة

هل تساءلت يومًا عن كيفية توقيع مستند وورد مشفّر؟ سنشرح اليوم هذه العملية باستخدام Aspose.Words لـ .NET. استعدوا لدرس تعليمي مفصل وجذاب وممتع!

## المتطلبات الأساسية

قبل الغوص في الكود، دعنا نتأكد من أن لديك كل ما تحتاجه:

1. Aspose.Words لـ .NET: التنزيل والتثبيت من [هنا](https://releases.aspose.com/words/net/).
2. Visual Studio: تأكد من تثبيته.
3. شهادة صالحة: ستحتاج إلى ملف شهادة .pfx.
4. المعرفة الأساسية بلغة C#: إن فهم الأساسيات سيجعل هذا البرنامج التعليمي أكثر سلاسة.

## استيراد مساحات الأسماء

أولاً، لنستورد مساحات الأسماء اللازمة. فهي ضرورية للوصول إلى وظائف Aspose.Words.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;
using Aspose.Words.DigitalSignatures;
```

الآن، دعونا نقسم العملية إلى خطوات بسيطة وقابلة للإدارة.

## الخطوة 1: إعداد مشروعك

أولاً، قم بإعداد مشروعك فيجوال ستوديو. افتح فيجوال ستوديو وأنشئ تطبيق وحدة تحكم C# جديد. سمّه بشيء وصفي مثل "SignEncryptedWordDoc".

## الخطوة 2: إضافة Aspose.Words إلى مشروعك

بعد ذلك، نحتاج إلى إضافة Aspose.Words إلى مشروعك. هناك عدة طرق للقيام بذلك، ولكن استخدام NuGet هو الأبسط. 

1. افتح وحدة تحكم مدير الحزم NuGet من الأدوات > مدير الحزم NuGet > وحدة تحكم مدير الحزم.
2. قم بتشغيل الأمر التالي:

```powershell
Install-Package Aspose.Words
```

## الخطوة 3: إعداد دليل المستندات

ستحتاج إلى مجلد لتخزين مستندات Word وشهاداتك. لنُنشئ واحدًا.

1. أنشئ مجلدًا على جهاز الكمبيوتر الخاص بك. للتبسيط، لنسمِّه "DocumentDirectory".
2. ضع مستند Word الخاص بك (على سبيل المثال، "Document.docx") وشهادة .pfx الخاصة بك (على سبيل المثال، "morzal.pfx") في هذا الدليل.

## الخطوة 4: كتابة الكود

الآن، لنبدأ في شرح الكود. افتح `Program.cs` الملف وابدأ بإعداد المسار إلى دليل المستند الخاص بك وتهيئة `SignOptions` مع كلمة مرور فك التشفير.

```csharp
// المسار إلى دليل المستندات.
string dataDir = "YOUR DOCUMENTS DIRECTORY";
SignOptions signOptions = new SignOptions { DecryptionPassword = "decryptionPassword" };
```

## الخطوة 5: تحميل الشهادة

بعد ذلك، قم بتحميل الشهادة الخاصة بك باستخدام `CertificateHolder` سيتطلب هذا المسار إلى ملف .pfx وكلمة مرور الشهادة.

```csharp
CertificateHolder certHolder = CertificateHolder.Create(dataDir + "morzal.pfx", "aw");
```

## الخطوة 6: توقيع الوثيقة

وأخيرا، استخدم `DigitalSignatureUtil.Sign` طريقة لتوقيع مستند Word المشفّر. تتطلب هذه الطريقة خيارات ملف الإدخال، وملف الإخراج، وحامل الشهادة، والتوقيع.

```csharp
DigitalSignatureUtil.Sign(
    dataDir + "Document.docx",
    dataDir + "DigitallySignedDocument.docx",
    certHolder,
    signOptions);
```

## الخطوة 7: تشغيل الكود

احفظ ملفك وشغّل المشروع. إذا تم إعداد كل شيء بشكل صحيح، فسترى مستندك الموقّع في الدليل المحدد.

## خاتمة

ها قد انتهيت! لقد وقّعت بنجاح مستند وورد مشفّر باستخدام Aspose.Words لـ .NET. مع هذه المكتبة الفعّالة، أصبح التوقيع الرقمي سهلاً للغاية، حتى للملفات المشفّرة. برمجة ممتعة!

## الأسئلة الشائعة

### هل يمكنني استخدام نوع مختلف من الشهادة؟
نعم، يدعم Aspose.Words أنواعًا مختلفة من الشهادات، طالما كانت بالتنسيق الصحيح.

### هل من الممكن التوقيع على عدة مستندات في وقت واحد؟
بالتأكيد! يمكنك تصفح مجموعة من المستندات وتوقيع كل منها برمجيًا.

### ماذا لو نسيت كلمة المرور الخاصة بفك التشفير؟
لسوء الحظ، بدون كلمة مرور فك التشفير، لن تتمكن من توقيع المستند.

### هل يمكنني إضافة توقيع مرئي إلى المستند؟
نعم، يسمح لك Aspose.Words بإضافة توقيعات رقمية مرئية أيضًا.

### هل هناك طريقة للتحقق من التوقيع؟
نعم يمكنك استخدام `DigitalSignatureUtil.Verify` طريقة التحقق من التوقيعات.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}