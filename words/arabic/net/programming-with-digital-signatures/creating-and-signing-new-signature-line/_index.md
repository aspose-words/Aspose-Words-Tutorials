---
"description": "تعلّم كيفية إنشاء سطر توقيع رقميًا في مستند Word باستخدام Aspose.Words لـ .NET من خلال هذا البرنامج التعليمي خطوة بخطوة. مثالي لأتمتة المستندات."
"linktitle": "إنشاء وتوقيع سطر توقيع جديد"
"second_title": "واجهة برمجة تطبيقات معالجة المستندات Aspose.Words"
"title": "إنشاء وتوقيع سطر توقيع جديد"
"url": "/ar/net/programming-with-digital-signatures/creating-and-signing-new-signature-line/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# إنشاء وتوقيع سطر توقيع جديد

## مقدمة

أهلاً! لديك مستند وورد وتحتاج إلى إضافة سطر توقيع ثم توقيعه رقمياً. هل يبدو الأمر صعباً؟ كلا! بفضل Aspose.Words لـ .NET، يمكنك تحقيق ذلك بسهولة ببضعة أسطر برمجية فقط. في هذا البرنامج التعليمي، سنشرح لك العملية كاملةً، من إعداد بيئة العمل إلى حفظ المستند بتوقيع جديد لامع. هل أنت مستعد؟ هيا بنا!

## المتطلبات الأساسية

قبل أن ننتقل إلى الكود، دعنا نتأكد من أن لديك كل ما تحتاجه:
1. Aspose.Words لـ .NET - يمكنك [قم بتحميله هنا](https://releases.aspose.com/words/net/).
2. بيئة تطوير .NET - يوصى بشدة باستخدام Visual Studio.
3. مستند للتوقيع - قم بإنشاء مستند Word بسيط أو استخدم مستندًا موجودًا.
4. ملف الشهادة - هذا ضروري للتوقيعات الرقمية. يمكنك استخدام `.pfx` ملف.
5. صور لسطر التوقيع - اختياريًا، ملف صورة للتوقيع.

## استيراد مساحات الأسماء

أولاً، علينا استيراد مساحات الأسماء اللازمة. هذه الخطوة بالغة الأهمية لأنها تُهيئ البيئة المناسبة لاستخدام وظائف Aspose.Words.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Saving;
using Aspose.Words.Signing;
```

## الخطوة 1: إعداد دليل المستندات

كل مشروع يحتاج إلى بداية جيدة. لنُنشئ مسارًا لمجلد مستنداتك. هنا سيتم حفظ مستنداتك واسترجاعها.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## الخطوة 2: إنشاء مستند جديد

الآن، لنُنشئ مستند وورد جديدًا باستخدام Aspose.Words. ستكون هذه هي لوحة الرسم التي سنضيف إليها سطر التوقيع.

```csharp
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## الخطوة 3: إدخال سطر التوقيع

وهنا يأتي دور السحر. نُدخل سطر توقيع في مستندنا باستخدام `DocumentBuilder` فصل.

```csharp
SignatureLine signatureLine = builder.InsertSignatureLine(new SignatureLineOptions()).SignatureLine;
```

## الخطوة 4: حفظ المستند مع سطر التوقيع

بعد وضع سطر التوقيع، علينا حفظ المستند. هذه خطوة تمهيدية قبل التوقيع.

```csharp
doc.Save(dataDir + "SignDocuments.SignatureLine.docx");
```

## الخطوة 5: إعداد خيارات التوقيع

الآن، لنُعِدّ خيارات توقيع المستند. يتضمن ذلك تحديد مُعرِّف سطر التوقيع والصورة المُراد استخدامها.

```csharp
SignOptions signOptions = new SignOptions
{
    SignatureLineId = signatureLine.Id,
    SignatureLineImage = File.ReadAllBytes(dataDir + "Enhanced Windows MetaFile.emf")
};
```

## الخطوة 6: تحميل الشهادة

تتطلب التوقيعات الرقمية شهادة. هنا، نقوم بتحميل ملف الشهادة الذي سيُستخدم لتوقيع المستند.

```csharp
CertificateHolder certHolder = CertificateHolder.Create(dataDir + "morzal.pfx", "aw");
```

## الخطوة 7: توقيع الوثيقة

هذه هي الخطوة الأخيرة. نستخدم `DigitalSignatureUtil` لتوقيع المستند. يُحفظ المستند المُوقّع باسم جديد.

```csharp
DigitalSignatureUtil.Sign(dataDir + "SignDocuments.SignatureLine.docx",
    dataDir + "SignDocuments.NewSignatureLine.docx", certHolder, signOptions);
```

## خاتمة

وهكذا تكون قد انتهيت! بهذه الخطوات، أنشأتَ بنجاح مستند Word جديدًا، وأضفتَ سطر توقيع، ووقّعتَه رقميًا باستخدام Aspose.Words لـ .NET. إنها أداة فعّالة تُسهّل أتمتة المستندات. سواءً كنتَ تتعامل مع عقود أو اتفاقيات أو أي مستندات رسمية، تضمن هذه الطريقة توقيعها ومصادقتها بشكل آمن.

## الأسئلة الشائعة

### هل يمكنني استخدام تنسيقات صور أخرى لسطر التوقيع؟
نعم، يمكنك استخدام تنسيقات الصور المختلفة مثل PNG، JPG، BMP، وما إلى ذلك.

### هل من الضروري استخدام `.pfx` ملف للحصول على الشهادة؟
نعم، أ `.pfx` الملف هو تنسيق شائع لتخزين المعلومات التشفيرية بما في ذلك الشهادات والمفاتيح الخاصة.

### هل يمكنني إضافة أسطر توقيع متعددة في مستند واحد؟
بالتأكيد! يمكنك إدراج عدة أسطر توقيع بتكرار خطوة الإدراج لكل توقيع.

### ماذا لو لم يكن لدي شهادة رقمية؟
سيتعين عليك الحصول على شهادة رقمية من هيئة إصدار شهادات موثوقة أو إنشاء شهادة باستخدام أدوات مثل OpenSSL.

### كيف يمكنني التحقق من التوقيع الرقمي في المستند؟
بإمكانك فتح المستند الموقع في Word والانتقال إلى تفاصيل التوقيع للتحقق من صحة وسلامة التوقيع.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}