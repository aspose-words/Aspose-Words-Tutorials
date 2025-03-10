---
title: توقيع مستند Word مشفر
linktitle: توقيع مستند Word مشفر
second_title: واجهة برمجة تطبيقات معالجة المستندات Aspose.Words
description: تعرف على كيفية توقيع مستندات Word المشفرة باستخدام Aspose.Words for .NET من خلال هذا الدليل المفصل خطوة بخطوة. مثالي للمطورين.
weight: 10
url: /ar/net/programming-with-digital-signatures/signing-encrypted-document/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# توقيع مستند Word مشفر

## مقدمة

هل تساءلت يومًا عن كيفية التوقيع على مستند Word مشفر؟ اليوم، سنشرح هذه العملية باستخدام Aspose.Words for .NET. استعد لدروس تعليمية مفصلة وجذابة وممتعة!

## المتطلبات الأساسية

قبل الغوص في الكود، دعنا نتأكد من أن لديك كل ما تحتاجه:

1.  Aspose.Words for .NET: تنزيل وتثبيت من[هنا](https://releases.aspose.com/words/net/).
2. Visual Studio: تأكد من تثبيته.
3. شهادة صالحة: ستحتاج إلى ملف شهادة .pfx.
4. المعرفة الأساسية بلغة C#: إن فهم الأساسيات سيجعل هذا البرنامج التعليمي أكثر سلاسة.

## استيراد مساحات الأسماء

أولاً، دعنا نستورد مساحات الأسماء الضرورية. فهي ضرورية للوصول إلى وظائف Aspose.Words.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;
using Aspose.Words.DigitalSignatures;
```

الآن، دعونا نقوم بتقسيم العملية إلى خطوات بسيطة وقابلة للإدارة.

## الخطوة 1: إعداد مشروعك

أولاً، قم بإعداد مشروع Visual Studio. افتح Visual Studio وقم بإنشاء تطبيق وحدة تحكم C# جديد. قم بتسميته بشيء وصفي مثل "SignEncryptedWordDoc".

## الخطوة 2: إضافة Aspose.Words إلى مشروعك

بعد ذلك، نحتاج إلى إضافة Aspose.Words إلى مشروعك. هناك عدة طرق للقيام بذلك، ولكن استخدام NuGet هو الأبسط. 

1. افتح وحدة تحكم مدير الحزم NuGet من الأدوات > مدير الحزم NuGet > وحدة تحكم مدير الحزم.
2. قم بتشغيل الأمر التالي:

```powershell
Install-Package Aspose.Words
```

## الخطوة 3: إعداد دليل المستندات

ستحتاج إلى دليل لتخزين مستندات Word والشهادات الخاصة بك. دعنا ننشئ واحدًا.

1. قم بإنشاء دليل على جهاز الكمبيوتر الخاص بك. من أجل التبسيط، دعنا نسميه "DocumentDirectory".
2. ضع مستند Word الخاص بك (على سبيل المثال، "Document.docx") وشهادة .pfx الخاصة بك (على سبيل المثال، "morzal.pfx") في هذا الدليل.

## الخطوة 4: كتابة الكود

 الآن، دعنا نتعمق في الكود. افتح`Program.cs` الملف وابدأ بإعداد المسار إلى دليل المستند الخاص بك وتهيئة`SignOptions` مع كلمة مرور فك التشفير.

```csharp
// المسار إلى دليل المستندات.
string dataDir = "YOUR DOCUMENTS DIRECTORY";
SignOptions signOptions = new SignOptions { DecryptionPassword = "decryptionPassword" };
```

## الخطوة 5: تحميل الشهادة

 بعد ذلك، قم بتحميل شهادتك باستخدام`CertificateHolder`سيتطلب هذا المسار إلى ملف .pfx وكلمة مرور الشهادة.

```csharp
CertificateHolder certHolder = CertificateHolder.Create(dataDir + "morzal.pfx", "aw");
```

## الخطوة 6: توقيع الوثيقة

 وأخيرا، استخدم`DigitalSignatureUtil.Sign` طريقة لتوقيع مستند Word المشفر. تتطلب هذه الطريقة ملف الإدخال وملف الإخراج وحامل الشهادة وخيارات التوقيع.

```csharp
DigitalSignatureUtil.Sign(
    dataDir + "Document.docx",
    dataDir + "DigitallySignedDocument.docx",
    certHolder,
    signOptions);
```

## الخطوة 7: تشغيل الكود

احفظ ملفك وشغّل المشروع. إذا تم إعداد كل شيء بشكل صحيح، فيجب أن ترى المستند الموقّع في الدليل المحدد.

## خاتمة

والآن، لقد نجحت في التوقيع على مستند Word مشفر باستخدام Aspose.Words for .NET. وبفضل هذه المكتبة القوية، أصبح التوقيع الرقمي سهلاً للغاية، حتى بالنسبة للملفات المشفرة. أتمنى لك برمجة ممتعة!

## الأسئلة الشائعة

### هل يمكنني استخدام نوع مختلف من الشهادة؟
نعم، يدعم Aspose.Words أنواعًا مختلفة من الشهادات، طالما كانت بالتنسيق الصحيح.

### هل من الممكن التوقيع على عدة مستندات في وقت واحد؟
بالتأكيد! يمكنك التنقل بين مجموعة من المستندات وتوقيع كل منها برمجيًا.

### ماذا لو نسيت كلمة المرور الخاصة بفك التشفير؟
لسوء الحظ، بدون كلمة مرور فك التشفير، لن تتمكن من توقيع المستند.

### هل يمكنني إضافة توقيع مرئي إلى المستند؟
نعم، يسمح لك Aspose.Words بإضافة التوقيعات الرقمية المرئية أيضًا.

### هل هناك طريقة للتحقق من التوقيع؟
 نعم يمكنك استخدام`DigitalSignatureUtil.Verify` طريقة التحقق من التوقيعات.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
