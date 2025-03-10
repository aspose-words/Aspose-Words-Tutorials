---
title: إزالة جدول المحتويات في مستند Word
linktitle: إزالة جدول المحتويات في مستند Word
second_title: واجهة برمجة تطبيقات معالجة المستندات Aspose.Words
description: تعرف على كيفية إزالة جدول المحتويات (TOC) في مستندات Word باستخدام Aspose.Words لـ .NET باستخدام هذا البرنامج التعليمي السهل المتابعة.
weight: 10
url: /ar/net/remove-content/remove-table-of-contents/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# إزالة جدول المحتويات في مستند Word

## مقدمة

هل سئمت من التعامل مع جدول محتويات غير مرغوب فيه في مستندات Word؟ لقد مررنا جميعًا بهذه التجربة - في بعض الأحيان لا يكون جدول المحتويات ضروريًا. لحسن الحظ، يسهل عليك Aspose.Words for .NET إزالة جدول المحتويات برمجيًا. في هذا البرنامج التعليمي، سأرشدك خلال العملية خطوة بخطوة، حتى تتمكن من إتقانها في وقت قصير. دعنا ننتقل مباشرة!

## المتطلبات الأساسية

قبل أن نبدأ، دعونا نتأكد من أن لديك كل ما تحتاجه:

1.  مكتبة Aspose.Words لـ .NET: إذا لم تقم بذلك بالفعل، فقم بتنزيل مكتبة Aspose.Words لـ .NET وتثبيتها من[إصدارات Aspose](https://releases.aspose.com/words/net/).
2. بيئة التطوير: ستعمل بيئة التطوير المتكاملة مثل Visual Studio على تسهيل عملية البرمجة.
3. .NET Framework: تأكد من تثبيت .NET Framework.
4. مستند Word: هل لديك مستند Word (.docx) يحتوي على جدول المحتويات الذي تريد إزالته.

## استيراد مساحات الأسماء

أولاً وقبل كل شيء، دعنا نستورد مساحات الأسماء الضرورية. سيؤدي هذا إلى إعداد البيئة لاستخدام Aspose.Words.

```csharp
using System;
using System.Linq;
using Aspose.Words;
using Aspose.Words.Fields;
```

الآن، دعونا نقوم بتقسيم عملية إزالة جدول المحتويات من مستند Word إلى خطوات واضحة وقابلة للإدارة.

## الخطوة 1: إعداد دليل المستندات الخاص بك

قبل أن نتمكن من التعامل مع مستندك، نحتاج إلى تحديد مكانه. هذا هو مسار دليل المستند الخاص بك.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

 يستبدل`"YOUR DOCUMENT DIRECTORY"` مع المسار إلى مجلد المستندات الخاص بك. هذا هو المكان الذي يوجد فيه ملف Word الخاص بك.

## الخطوة 2: تحميل المستند

بعد ذلك، نحتاج إلى تحميل مستند Word إلى تطبيقنا. يجعل Aspose.Words هذه العملية بسيطة للغاية.

```csharp
Document doc = new Document(dataDir + "your-document.docx");
```

 يستبدل`"your-document.docx"` مع اسم الملف الخاص بك. يقوم هذا السطر من التعليمات البرمجية بتحميل مستندك حتى نتمكن من البدء في العمل عليه.

## الخطوة 3: تحديد حقل جدول المحتويات وإزالته

وهنا يحدث السحر. سنحدد موقع حقل جدول المحتويات ونقوم بإزالته.

```csharp
doc.Range.Fields.Where(f => f.Type == FieldType.FieldTOC).ToList()
    .ForEach(f => f.Remove());
```

وهذا ما يحدث:
- `doc.Range.Fields`:هذا يتيح لك الوصول إلى كافة الحقول الموجودة في المستند.
- `.Where(f => f.Type == FieldType.FieldTOC)`:يؤدي هذا إلى تصفية الحقول للعثور فقط على تلك التي تعتبر جداول محتويات.
- `.ToList().ForEach(f => f.Remove())`:يؤدي هذا إلى تحويل الحقول المفلترة إلى قائمة وإزالة كل حقل منها.

## الخطوة 4: حفظ المستند المعدل

أخيرًا، نحتاج إلى حفظ التغييرات التي أجريناها. يمكنك حفظ المستند باسم جديد للحفاظ على الملف الأصلي.

```csharp
doc.Save(dataDir + "modified-document.docx", SaveFormat.Docx);
```

 يحفظ هذا السطر مستندك بالتغييرات التي أجريتها. استبدل`"modified-document.docx"` مع اسم الملف المطلوب.

## خاتمة

والآن، لقد انتهيت! إن إزالة جدول المحتويات من مستند Word باستخدام Aspose.Words for .NET أمر سهل بمجرد تقسيمه إلى هذه الخطوات البسيطة. لا تساعد هذه المكتبة القوية في إزالة جداول المحتويات فحسب، بل يمكنها أيضًا التعامل مع عدد لا يحصى من عمليات معالجة المستندات الأخرى. لذا، انطلق وجربها!

## الأسئلة الشائعة

### ما هو Aspose.Words لـ .NET؟

Aspose.Words for .NET هي مكتبة .NET قوية لمعالجة المستندات، مما يسمح للمطورين بإنشاء مستندات Word وتعديلها وتحويلها برمجيًا.

### هل يمكنني استخدام Aspose.Words مجانًا؟

 نعم، يمكنك استخدام Aspose.Words مع[نسخة تجريبية مجانية](https://releases.aspose.com/) أو الحصول على[رخصة مؤقتة](https://purchase.aspose.com/temporary-license/).

### هل من الممكن إزالة الحقول الأخرى باستخدام Aspose.Words؟

بالتأكيد! يمكنك إزالة أي حقل عن طريق تحديد نوعه في شرط الفلتر.

### هل أحتاج إلى Visual Studio لاستخدام Aspose.Words؟

على الرغم من أن Visual Studio يوصى به بشدة لسهولة التطوير، إلا أنه يمكنك استخدام أي IDE يدعم .NET.

### أين يمكنني العثور على مزيد من المعلومات حول Aspose.Words؟

 لمزيد من التفاصيل حول الوثائق، قم بزيارة[توثيق واجهة برمجة التطبيقات Aspose.Words لـ .NET](https://reference.aspose.com/words/net/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
