---
title: إنشاء وتوقيع سطر توقيع جديد
linktitle: إنشاء وتوقيع سطر توقيع جديد
second_title: واجهة برمجة تطبيقات معالجة المستندات Aspose.Words
description: تعرف على كيفية إنشاء سطر توقيع وتوقيعه رقميًا في مستند Word باستخدام Aspose.Words for .NET من خلال هذا البرنامج التعليمي خطوة بخطوة. مثالي لأتمتة المستندات.
weight: 10
url: /ar/net/programming-with-digital-signatures/creating-and-signing-new-signature-line/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# إنشاء وتوقيع سطر توقيع جديد

## مقدمة

مرحبًا! حسنًا، لديك مستند Word وتحتاج إلى إضافة سطر توقيع ثم التوقيع عليه رقميًا. هل يبدو الأمر صعبًا؟ ليس كذلك على الإطلاق! بفضل Aspose.Words for .NET، يمكنك تحقيق ذلك بسلاسة من خلال بضعة أسطر فقط من التعليمات البرمجية. في هذا البرنامج التعليمي، سنرشدك خلال العملية بأكملها من إعداد البيئة الخاصة بك إلى حفظ المستند بتوقيع جديد لامع. هل أنت مستعد؟ لنبدأ!

## المتطلبات الأساسية

قبل أن ننتقل إلى الكود، دعنا نتأكد من أن لديك كل ما تحتاجه:
1.  Aspose.Words لـ .NET - يمكنك[تحميله هنا](https://releases.aspose.com/words/net/).
2. بيئة تطوير .NET - يوصى بشدة باستخدام Visual Studio.
3. مستند للتوقيع - قم بإنشاء مستند Word بسيط أو استخدم مستندًا موجودًا.
4.  ملف الشهادة - هذا ضروري للتوقيعات الرقمية. يمكنك استخدام`.pfx` ملف.
5. صور لسطر التوقيع - اختياريًا، ملف صورة للتوقيع.

## استيراد مساحات الأسماء

أولاً، نحتاج إلى استيراد مساحات الأسماء الضرورية. هذه الخطوة بالغة الأهمية لأنها تُعد البيئة المناسبة لاستخدام وظائف Aspose.Words.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Saving;
using Aspose.Words.Signing;
```

## الخطوة 1: إعداد دليل المستندات

يحتاج كل مشروع إلى بداية جيدة. دعنا نحدد المسار إلى دليل المستندات الخاص بك. هذا هو المكان الذي سيتم فيه حفظ مستنداتك واسترجاعها.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## الخطوة 2: إنشاء مستند جديد

الآن، لنقم بإنشاء مستند Word جديد باستخدام Aspose.Words. سيكون هذا هو القماش الذي سنضيف إليه سطر التوقيع.

```csharp
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## الخطوة 3: إدخال سطر التوقيع

 وهنا يحدث السحر. نقوم بإدراج سطر توقيع في مستندنا باستخدام`DocumentBuilder` فصل.

```csharp
SignatureLine signatureLine = builder.InsertSignatureLine(new SignatureLineOptions()).SignatureLine;
```

## الخطوة 4: حفظ المستند الذي يحتوي على سطر التوقيع

بمجرد وضع سطر التوقيع في مكانه، نحتاج إلى حفظ المستند. هذه خطوة وسيطة قبل الشروع في التوقيع عليه.

```csharp
doc.Save(dataDir + "SignDocuments.SignatureLine.docx");
```

## الخطوة 5: إعداد خيارات التوقيع

الآن، دعنا نحدد خيارات توقيع المستند. يتضمن ذلك تحديد معرف سطر التوقيع والصورة التي سيتم استخدامها.

```csharp
SignOptions signOptions = new SignOptions
{
    SignatureLineId = signatureLine.Id,
    SignatureLineImage = File.ReadAllBytes(dataDir + "Enhanced Windows MetaFile.emf")
};
```

## الخطوة 6: تحميل الشهادة

تتطلب التوقيعات الرقمية شهادة. هنا، نقوم بتحميل ملف الشهادة الذي سيتم استخدامه لتوقيع المستند.

```csharp
CertificateHolder certHolder = CertificateHolder.Create(dataDir + "morzal.pfx", "aw");
```

## الخطوة 7: توقيع الوثيقة

 هذه هي الخطوة النهائية، نستخدم`DigitalSignatureUtil`الصف لتوقيع المستند. يتم حفظ المستند الموقّع باسم جديد.

```csharp
DigitalSignatureUtil.Sign(dataDir + "SignDocuments.SignatureLine.docx",
    dataDir + "SignDocuments.NewSignatureLine.docx", certHolder, signOptions);
```

## خاتمة

والآن، لقد انتهيت! باتباع هذه الخطوات، تكون قد أنشأت بنجاح مستند Word جديدًا، وأضفت سطر توقيع، ووقعته رقميًا باستخدام Aspose.Words for .NET. إنها أداة قوية تجعل أتمتة المستندات سهلة للغاية. سواء كنت تتعامل مع عقود أو اتفاقيات أو أي مستندات رسمية، فإن هذه الطريقة تضمن توقيعها والمصادقة عليها بشكل آمن.

## الأسئلة الشائعة

### هل يمكنني استخدام تنسيقات صور أخرى لسطر التوقيع؟
نعم، يمكنك استخدام تنسيقات الصور المختلفة مثل PNG، JPG، BMP، وما إلى ذلك.

###  هل من الضروري استخدام`.pfx` file for the certificate?
 نعم، أ`.pfx` الملف هو تنسيق شائع لتخزين المعلومات التشفيرية بما في ذلك الشهادات والمفاتيح الخاصة.

### هل يمكنني إضافة أسطر توقيع متعددة في مستند واحد؟
بالتأكيد! يمكنك إدراج أسطر توقيع متعددة عن طريق تكرار خطوة الإدراج لكل توقيع.

### ماذا لو لم يكن لدي شهادة رقمية؟
سيتعين عليك الحصول على شهادة رقمية من هيئة تصديق موثوقة أو إنشاء شهادة باستخدام أدوات مثل OpenSSL.

### كيف يمكنني التحقق من التوقيع الرقمي في المستند؟
بإمكانك فتح المستند الموقّع في Word والانتقال إلى تفاصيل التوقيع للتحقق من صحة وسلامة التوقيع.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
