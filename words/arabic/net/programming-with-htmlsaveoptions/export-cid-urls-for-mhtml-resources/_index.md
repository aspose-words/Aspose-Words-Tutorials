---
"description": "تعرّف على كيفية تصدير عناوين URL الخاصة بـ Cid لموارد MHTML باستخدام Aspose.Words لـ .NET في هذا البرنامج التعليمي خطوة بخطوة. مثالي للمطورين من جميع المستويات."
"linktitle": "تصدير عناوين URL الخاصة بـ CID لموارد MHTML"
"second_title": "واجهة برمجة تطبيقات معالجة المستندات Aspose.Words"
"title": "تصدير عناوين URL الخاصة بـ CID لموارد MHTML"
"url": "/ar/net/programming-with-htmlsaveoptions/export-cid-urls-for-mhtml-resources/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# تصدير عناوين URL الخاصة بـ CID لموارد MHTML

## مقدمة

هل أنت مستعد لإتقان فن تصدير عناوين URL الخاصة بـ Cid لموارد MHTML باستخدام Aspose.Words لـ .NET؟ سواء كنت مطورًا محترفًا أو مبتدئًا، سيرشدك هذا الدليل الشامل خلال كل خطوة. بنهاية هذه المقالة، ستكتسب فهمًا واضحًا لكيفية التعامل بكفاءة مع موارد MHTML في مستندات Word. هيا بنا!

## المتطلبات الأساسية

قبل أن نبدأ، دعونا نتأكد من أن لديك كل ما تحتاجه:

- Aspose.Words لـ .NET: تأكد من تثبيت أحدث إصدار من Aspose.Words لـ .NET. إذا لم يكن لديك، يمكنك تنزيله من [هنا](https://releases.aspose.com/words/net/).
- بيئة التطوير: بيئة تطوير مثل Visual Studio.
- المعرفة الأساسية بلغة C#: على الرغم من أنني سأرشدك خلال كل خطوة، إلا أن الفهم الأساسي للغة C# سيكون مفيدًا.

## استيراد مساحات الأسماء

أولاً، لنستورد مساحات الأسماء اللازمة. هذه الخطوة تُمهّد الطريق لدرسنا التعليمي:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;
```

الآن، لنُقسّم العملية إلى خطوات بسيطة وسهلة التنفيذ. ستتضمن كل خطوة شرحًا مُفصّلًا لضمان سهولة متابعتها.

## الخطوة 1: إعداد مشروعك

### الخطوة 1.1: إنشاء مشروع جديد
افتح Visual Studio وأنشئ مشروع C# جديدًا. اختر قالب تطبيق وحدة التحكم لتبسيط الأمور.

### الخطوة 1.2: إضافة Aspose.Words إلى مرجع .NET
لاستخدام Aspose.Words لـ .NET، عليك إضافة مرجع إلى مكتبة Aspose.Words. يمكنك القيام بذلك عبر مدير حزم NuGet:

1. انقر بزر الماوس الأيمن على مشروعك في مستكشف الحلول.
2. حدد "إدارة حزم NuGet".
3. ابحث عن "Aspose.Words" وقم بتثبيته.

## الخطوة 2: تحميل مستند Word

### الخطوة 2.1: تحديد دليل المستندات
حدد مسار مجلد مستندك. هذا هو المكان الذي يوجد فيه مستند Word.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

يستبدل `"YOUR DOCUMENT DIRECTORY"` مع المسار الفعلي إلى الدليل الخاص بك.

### الخطوة 2.2: تحميل المستند
قم بتحميل مستند Word الخاص بك إلى المشروع.

```csharp
Document doc = new Document(dataDir + "Content-ID.docx");
```

## الخطوة 3: تكوين خيارات حفظ HTML

إنشاء مثيل لـ `HtmlSaveOptions` لتخصيص كيفية حفظ مستندك بتنسيق MHTML.

```csharp
HtmlSaveOptions saveOptions = new HtmlSaveOptions(SaveFormat.Mhtml)
{
    PrettyFormat = true,
    ExportCidUrlsForMhtmlResources = true
};
```

- `SaveFormat.Mhtml` يحدد أن تنسيق الإخراج هو MHTML.
- `PrettyFormat = true` يضمن تنسيق الإخراج بشكل أنيق.
- `ExportCidUrlsForMhtmlResources = true` يتيح تصدير عناوين URL الخاصة بـ Cid لموارد MHTML.

### الخطوة 4: حفظ المستند بتنسيق MHTML

الخطوة 4.1: حفظ المستند
احفظ مستندك كملف MHTML باستخدام الخيارات التي قمت بتكوينها.

```csharp
doc.Save(dataDir + "WorkingWithHtmlSaveOptions.ExportCidUrlsForMhtmlResources.mhtml", saveOptions);
```

## خاتمة

تهانينا! لقد نجحت في تصدير عناوين URL الخاصة بـ Cid لموارد MHTML باستخدام Aspose.Words لـ .NET. شرح لك هذا البرنامج التعليمي خطوات إعداد مشروعك، وتحميل مستند Word، وتكوين خيارات حفظ HTML، وحفظ المستند بتنسيق MHTML. يمكنك الآن تطبيق هذه الخطوات على مشاريعك وتحسين إدارة مستنداتك.

## الأسئلة الشائعة

### ما هو الغرض من تصدير عناوين URL الخاصة بـ Cid لموارد MHTML؟
يضمن تصدير عناوين URL الخاصة بـ Cid لموارد MHTML الإشارة بشكل صحيح إلى الموارد المضمنة في ملف MHTML الخاص بك، مما يؤدي إلى تحسين قابلية نقل المستندات وسلامتها.

### هل يمكنني تخصيص تنسيق الإخراج بشكل أكبر؟
نعم، يوفر Aspose.Words لـ .NET خيارات تخصيص شاملة لحفظ المستندات. راجع [التوثيق](https://reference.aspose.com/words/net/) لمزيد من التفاصيل.

### هل أحتاج إلى ترخيص لاستخدام Aspose.Words لـ .NET؟
نعم، تحتاج إلى ترخيص لاستخدام Aspose.Words لـ .NET. يمكنك الحصول على نسخة تجريبية مجانية. [هنا](https://releases.aspose.com/) أو شراء ترخيص [هنا](https://purchase.aspose.com/buy).

### هل يمكنني أتمتة هذه العملية لمستندات متعددة؟
بالتأكيد! يمكنك إنشاء نص برمجي لأتمتة عملية معالجة مستندات متعددة، مستفيدًا من قوة Aspose.Words لـ .NET للتعامل بكفاءة مع عمليات الدفعات.

### أين يمكنني الحصول على الدعم إذا واجهت مشاكل؟
إذا كنت بحاجة إلى الدعم، قم بزيارة منتدى دعم Aspose [هنا](https://forum.aspose.com/c/words/8) للحصول على المساعدة من المجتمع ومطوري Aspose.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}