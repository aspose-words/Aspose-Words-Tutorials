---
title: تصدير عناوين URL الخاصة بـ CID لموارد Mhtml
linktitle: تصدير عناوين URL الخاصة بـ CID لموارد Mhtml
second_title: واجهة برمجة تطبيقات معالجة المستندات Aspose.Words
description: تعرف على كيفية تصدير عناوين URL الخاصة بـ Cid لموارد MHTML باستخدام Aspose.Words for .NET في هذا البرنامج التعليمي خطوة بخطوة. مثالي للمطورين من جميع المستويات.
weight: 10
url: /ar/net/programming-with-htmlsaveoptions/export-cid-urls-for-mhtml-resources/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# تصدير عناوين URL الخاصة بـ CID لموارد Mhtml

## مقدمة

هل أنت مستعد لإتقان فن تصدير عناوين URL الخاصة بـ Cid لموارد MHTML باستخدام Aspose.Words لـ .NET؟ سواء كنت مطورًا متمرسًا أو مبتدئًا، فسيرشدك هذا الدليل الشامل خلال كل خطوة. بحلول نهاية هذه المقالة، ستكون لديك فكرة واضحة تمامًا عن كيفية التعامل بكفاءة مع موارد MHTML في مستندات Word الخاصة بك. دعنا نتعمق!

## المتطلبات الأساسية

قبل أن نبدأ، دعونا نتأكد من أن لديك كل ما تحتاجه:

-  Aspose.Words for .NET: تأكد من تثبيت أحدث إصدار من Aspose.Words for .NET. إذا لم يكن لديك الإصدار، فيمكنك تنزيله من[هنا](https://releases.aspose.com/words/net/).
- بيئة التطوير: بيئة تطوير مثل Visual Studio.
- المعرفة الأساسية بلغة C#: على الرغم من أنني سأرشدك خلال كل خطوة، إلا أن الفهم الأساسي للغة C# سيكون مفيدًا.

## استيراد مساحات الأسماء

أولاً وقبل كل شيء، دعنا نستورد مساحات الأسماء الضرورية. هذه الخطوة تمهد الطريق لبرنامجنا التعليمي:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;
```

الآن، دعنا نقسم العملية إلى خطوات بسيطة وسهلة الإدارة. ستتضمن كل خطوة شرحًا تفصيليًا لضمان قدرتك على متابعتها دون عناء.

## الخطوة 1: إعداد مشروعك

### الخطوة 1.1: إنشاء مشروع جديد
افتح Visual Studio وأنشئ مشروع C# جديدًا. اختر قالب تطبيق وحدة التحكم لتبسيط الأمور.

### الخطوة 1.2: إضافة Aspose.Words إلى مرجع .NET
لاستخدام Aspose.Words لـ .NET، تحتاج إلى إضافة مرجع إلى مكتبة Aspose.Words. يمكنك القيام بذلك عبر NuGet Package Manager:

1. انقر بزر الماوس الأيمن على مشروعك في مستكشف الحلول.
2. حدد "إدارة حزم NuGet".
3. ابحث عن "Aspose.Words" وقم بتثبيته.

## الخطوة 2: تحميل مستند Word

### الخطوة 2.1: تحديد دليل المستندات
قم بتحديد المسار إلى دليل المستندات الخاص بك. هذا هو المكان الذي يوجد فيه مستند Word الخاص بك.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

 يستبدل`"YOUR DOCUMENT DIRECTORY"` مع المسار الفعلي إلى الدليل الخاص بك.

### الخطوة 2.2: تحميل المستند
قم بتحميل مستند Word الخاص بك إلى المشروع.

```csharp
Document doc = new Document(dataDir + "Content-ID.docx");
```

## الخطوة 3: تكوين خيارات حفظ HTML

 إنشاء مثيل لـ`HtmlSaveOptions` لتخصيص كيفية حفظ مستندك بتنسيق MHTML.

```csharp
HtmlSaveOptions saveOptions = new HtmlSaveOptions(SaveFormat.Mhtml)
{
    PrettyFormat = true,
    ExportCidUrlsForMhtmlResources = true
};
```

- `SaveFormat.Mhtml` يحدد أن تنسيق الإخراج هو MHTML.
- `PrettyFormat = true` يتأكد من تنسيق الإخراج بشكل أنيق.
- `ExportCidUrlsForMhtmlResources = true` يتيح تصدير عناوين URL الخاصة بـ Cid لموارد MHTML.

### الخطوة 4: حفظ المستند بصيغة MHTML

الخطوة 4.1: حفظ المستند
احفظ مستندك كملف MHTML باستخدام الخيارات التي قمت بتكوينها.

```csharp
doc.Save(dataDir + "WorkingWithHtmlSaveOptions.ExportCidUrlsForMhtmlResources.mhtml", saveOptions);
```

## خاتمة

تهانينا! لقد نجحت في تصدير عناوين URL الخاصة بـ Cid لموارد MHTML باستخدام Aspose.Words for .NET. لقد شرح لك هذا البرنامج التعليمي كيفية إعداد مشروعك وتحميل مستند Word وتكوين خيارات الحفظ بتنسيق HTML وحفظ المستند بتنسيق MHTML. يمكنك الآن تطبيق هذه الخطوات على مشاريعك الخاصة وتحسين مهام إدارة المستندات.

## الأسئلة الشائعة

### ما هو الغرض من تصدير عناوين URL الخاصة بـ Cid لموارد MHTML؟
يضمن تصدير عناوين URL الخاصة بـ Cid لموارد MHTML الإشارة بشكل صحيح إلى الموارد المضمنة في ملف MHTML، مما يؤدي إلى تحسين قابلية نقل المستندات وسلامتها.

### هل يمكنني تخصيص تنسيق الإخراج بشكل أكبر؟
 نعم، يوفر Aspose.Words for .NET خيارات تخصيص شاملة لحفظ المستندات. راجع[التوثيق](https://reference.aspose.com/words/net/) لمزيد من التفاصيل.

### هل أحتاج إلى ترخيص لاستخدام Aspose.Words لـ .NET؟
 نعم، تحتاج إلى ترخيص لاستخدام Aspose.Words لـ .NET. يمكنك الحصول على نسخة تجريبية مجانية[هنا](https://releases.aspose.com/) أو شراء ترخيص[هنا](https://purchase.aspose.com/buy).

### هل يمكنني أتمتة هذه العملية لمستندات متعددة؟
بالتأكيد! يمكنك إنشاء برنامج نصي لأتمتة العملية الخاصة بمستندات متعددة، والاستفادة من قوة Aspose.Words for .NET للتعامل مع عمليات الدفعات بكفاءة.

### أين يمكنني الحصول على الدعم إذا واجهت مشاكل؟
إذا كنت بحاجة إلى الدعم، قم بزيارة منتدى دعم Aspose[هنا](https://forum.aspose.com/c/words/8) للحصول على المساعدة من المجتمع ومطوري Aspose.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
