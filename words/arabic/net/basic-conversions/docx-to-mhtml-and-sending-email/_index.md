---
"description": "تعرّف على كيفية تحويل DOCX إلى MHTML وإرسال رسائل البريد الإلكتروني باستخدام Aspose.Words لـ .NET في هذا الدليل المُفصّل. عزّز إنتاجيتك بأتمتة سهلة."
"linktitle": "تحويل Docx إلى Mhtml وإرسال البريد الإلكتروني"
"second_title": "واجهة برمجة تطبيقات معالجة المستندات Aspose.Words"
"title": "تحويل Docx إلى Mhtml وإرسال البريد الإلكتروني"
"url": "/ar/net/basic-conversions/docx-to-mhtml-and-sending-email/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# تحويل Docx إلى Mhtml وإرسال البريد الإلكتروني

## مقدمة

في عصرنا الرقمي، أصبح تحويل المستندات من صيغة إلى أخرى وإرسالها عبر البريد الإلكتروني أمرًا شائعًا. ستشرح هذه المقالة عملية تحويل ملف DOCX إلى صيغة MHTML ثم إرساله عبر البريد الإلكتروني باستخدام Aspose.Words لـ .NET. سنشرح كل خطوة في دليل مفصل وسهل المتابعة، لضمان فهمك للعملية من البداية إلى النهاية. هيا بنا!

## المتطلبات الأساسية

قبل أن نبدأ، تأكد من توفر المتطلبات الأساسية التالية:

1. Aspose.Words لـ .NET: قم بتنزيل وتثبيت مكتبة Aspose.Words لـ .NET من [صفحة إصدارات Aspose](https://releases.aspose.com/words/net/).
2. Aspose.Email لـ .NET: قم بتنزيل وتثبيت مكتبة Aspose.Email لـ .NET من [صفحة إصدارات Aspose](https://releases.aspose.com/email/net/).
3. .NET Framework: تأكد من تثبيت .NET Framework على جهازك.
4. خادم SMTP: تحتاج إلى الوصول إلى خادم SMTP لإرسال رسائل البريد الإلكتروني.

## استيراد مساحات الأسماء

لاستخدام Aspose.Words وAspose.Email في مشروعك، عليك استيراد مساحات الأسماء اللازمة. أضف توجيهات الاستخدام التالية في أعلى ملف C#:

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using Aspose.Email;
using Aspose.Email.Mime;
using Aspose.Email.Clients.Smtp;
```

دعونا نقسم العملية إلى خطوات متعددة للتأكد من فهمك لكل جزء بوضوح.

## الخطوة 1: تحميل مستند DOCX

أولاً، عليك تحميل مستند DOCX الذي تريد تحويله. استخدم `Document` استخدم الفئة من Aspose.Words لتحميل ملف DOCX الخاص بك.

```csharp
// المسار إلى دليل المستندات.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Document.docx");
```

## الخطوة 2: حفظ المستند بتنسيق MHTML

بعد ذلك، احفظ المستند المُحمَّل كملف MHTML. يتم ذلك باستخدام `Save` طريقة `Document` فصل.

```csharp
Stream stream = new MemoryStream();
doc.Save(stream, SaveFormat.Mhtml);

// قم بإرجاع البث إلى البداية حتى يتمكن Aspose.Email من قراءته.
stream.Position = 0;
```

## الخطوة 3: إنشاء رسالة بريد إلكتروني

الآن، أنشئ رسالة بريد إلكتروني من دفق MHTML باستخدام Aspose.Email. ستستخدم `MailMessage` صف لهذا الغرض.

```csharp
// إنشاء رسالة بريد إلكتروني MIME لـ Aspose.Email من الدفق.
MailMessage message = MailMessage.Load(stream, new MhtmlLoadOptions());
message.From = "your_from@email.com";
message.To = "your_to@email.com";
message.Subject = "Aspose.Words + Aspose.Email MHTML Test Message";
```

## الخطوة 4: إرسال البريد الإلكتروني

أخيرًا، أرسل البريد الإلكتروني باستخدام عميل SMTP. قم بتكوين عميل SMTP باستخدام تفاصيل خادم SMTP الخاص بك، ثم استخدم `Send` طريقة إرسال الرسالة.

```csharp
// أرسل الرسالة باستخدام Aspose.Email.
SmtpClient client = new SmtpClient();
client.Host = "your_smtp.com";
client.Send(message);
```

## خاتمة

تهانينا! لقد نجحت في تحويل مستند DOCX إلى MHTML وإرساله عبر البريد الإلكتروني باستخدام Aspose.Words for .NET. تتضمن هذه العملية تحميل المستند، وتحويله إلى MHTML، وإنشاء رسالة بريد إلكتروني، وإرسالها باستخدام عميل SMTP. بهذه الخطوات، يمكنك أتمتة تحويل المستندات وإرسالها عبر البريد الإلكتروني بسهولة في تطبيقاتك.

## الأسئلة الشائعة

### هل يمكنني استخدام هذه الطريقة لتحويل تنسيقات المستندات الأخرى؟
نعم، يدعم Aspose.Words تنسيقات مختلفة، ويمكنك تحويل المستندات مثل DOC، وDOCX، وRTF، والمزيد إلى MHTML.

### كيف يمكنني إضافة المرفقات إلى البريد الإلكتروني؟
يمكنك استخدام `Attachments` ممتلكات `MailMessage` فئة لإضافة المرفقات إلى بريدك الإلكتروني.

### هل Aspose.Words متوافق مع .NET Core؟
نعم، Aspose.Words متوافق مع .NET Core. يمكنك استخدامه في تطبيقات .NET Core أيضًا.

### هل أحتاج إلى ترخيص لـ Aspose.Words و Aspose.Email؟
نعم، كلتا المكتبتين تتطلبان ترخيصًا. يمكنك الحصول على ترخيص مؤقت من [صفحة شراء Aspose](https://purchase.aspose.com/temporary-license/) لأغراض التقييم.

### أين يمكنني العثور على مزيد من الوثائق؟
يمكنك العثور على وثائق مفصلة لـ Aspose.Words [هنا](https://reference.aspose.com/words/net/) وللبريد الإلكتروني Aspose.Email [هنا](https://reference.aspose.com/email/net/).



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}