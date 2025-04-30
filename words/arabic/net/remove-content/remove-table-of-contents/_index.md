---
"description": "تعرف على كيفية إزالة جدول المحتويات (TOC) في مستندات Word باستخدام Aspose.Words لـ .NET باستخدام هذا البرنامج التعليمي السهل المتابعة."
"linktitle": "إزالة جدول المحتويات في مستند Word"
"second_title": "واجهة برمجة تطبيقات معالجة المستندات Aspose.Words"
"title": "إزالة جدول المحتويات في مستند Word"
"url": "/ar/net/remove-content/remove-table-of-contents/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# إزالة جدول المحتويات في مستند Word

## مقدمة

هل سئمت من التعامل مع جدول محتويات (TOC) غير مرغوب فيه في مستندات Word؟ جميعنا مررنا بهذه التجربة - أحيانًا لا يكون جدول المحتويات ضروريًا. لحسن حظك، يُسهّل Aspose.Words for .NET إزالة جدول المحتويات برمجيًا. في هذا البرنامج التعليمي، سأرشدك خطوة بخطوة خلال العملية، لتتمكن من إتقانها في وقت قصير. هيا بنا!

## المتطلبات الأساسية

قبل أن نبدأ، دعونا نتأكد من أن لديك كل ما تحتاجه:

1. مكتبة Aspose.Words لـ .NET: إذا لم تقم بذلك بالفعل، فقم بتنزيل مكتبة Aspose.Words لـ .NET وتثبيتها من [إصدارات Aspose](https://releases.aspose.com/words/net/).
2. بيئة التطوير: ستعمل بيئة التطوير المتكاملة مثل Visual Studio على جعل عملية الترميز أسهل.
3. .NET Framework: تأكد من تثبيت .NET Framework.
4. مستند Word: لديك مستند Word (.docx) يحتوي على جدول المحتويات الذي تريد إزالته.

## استيراد مساحات الأسماء

أولاً، لنستورد مساحات الأسماء اللازمة. هذا يُهيئ بيئة استخدام Aspose.Words.

```csharp
using System;
using System.Linq;
using Aspose.Words;
using Aspose.Words.Fields;
```

الآن، دعونا نقوم بتقسيم عملية إزالة جدول المحتويات من مستند Word إلى خطوات واضحة وقابلة للإدارة.

## الخطوة 1: إعداد دليل المستندات الخاص بك

قبل أن نتمكن من التعامل مع مستندك، علينا تحديد مكانه. هذا هو مسار دليل مستندك.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

يستبدل `"YOUR DOCUMENT DIRECTORY"` مع المسار إلى مجلد المستندات. هذا هو مكان ملف Word الخاص بك.

## الخطوة 2: تحميل المستند

بعد ذلك، علينا تحميل مستند Word إلى تطبيقنا. يُسهّل Aspose.Words هذه العملية بشكل كبير.

```csharp
Document doc = new Document(dataDir + "your-document.docx");
```

يستبدل `"your-document.docx"` مع اسم ملفك. هذا السطر من التعليمات البرمجية يُحمّل مستندك حتى نتمكن من بدء العمل عليه.

## الخطوة 3: تحديد حقل جدول المحتويات وإزالته

هنا تبدأ العملية السحرية. سنحدد موقع حقل جدول المحتويات ونزيله.

```csharp
doc.Range.Fields.Where(f => f.Type == FieldType.FieldTOC).ToList()
    .ForEach(f => f.Remove());
```

وإليك ما يحدث:
- `doc.Range.Fields`:يؤدي هذا إلى الوصول إلى كافة الحقول الموجودة في المستند.
- `.Where(f => f.Type == FieldType.FieldTOC)`:يؤدي هذا إلى تصفية الحقول للعثور فقط على تلك التي تعتبر جداول محتويات.
- `.ToList().ForEach(f => f.Remove())`:يؤدي هذا إلى تحويل الحقول المفلترة إلى قائمة وإزالة كل حقل منها.

## الخطوة 4: حفظ المستند المعدّل

أخيرًا، علينا حفظ التغييرات. يمكنك حفظ المستند باسم جديد للحفاظ على الملف الأصلي.

```csharp
doc.Save(dataDir + "modified-document.docx", SaveFormat.Docx);
```

يحفظ هذا السطر مستندك بالتغييرات التي أجريتها. استبدل `"modified-document.docx"` مع اسم الملف المطلوب.

## خاتمة

ها قد انتهيت! إزالة جدول محتويات من مستند وورد باستخدام Aspose.Words لـ .NET أمرٌ سهلٌ بمجرد اتباع هذه الخطوات البسيطة. هذه المكتبة القوية لا تساعد فقط في إزالة جداول المحتويات، بل يمكنها أيضًا التعامل مع العديد من عمليات معالجة المستندات الأخرى. لذا، جرّبها!

## الأسئلة الشائعة

### ما هو Aspose.Words لـ .NET؟

Aspose.Words for .NET هي مكتبة .NET قوية للتعامل مع المستندات، مما يسمح للمطورين بإنشاء مستندات Word وتعديلها وتحويلها برمجيًا.

### هل يمكنني استخدام Aspose.Words مجانًا؟

نعم، يمكنك استخدام Aspose.Words مع [نسخة تجريبية مجانية](https://releases.aspose.com/) أو احصل على [رخصة مؤقتة](https://purchase.aspose.com/temporary-license/).

### هل من الممكن إزالة الحقول الأخرى باستخدام Aspose.Words؟

بالتأكيد! يمكنك إزالة أي حقل بتحديد نوعه في خانة التصفية.

### هل أحتاج إلى Visual Studio لاستخدام Aspose.Words؟

على الرغم من أن Visual Studio يوصى به بشدة لسهولة التطوير، إلا أنه يمكنك استخدام أي IDE يدعم .NET.

### أين يمكنني العثور على مزيد من المعلومات حول Aspose.Words؟

لمزيد من التفاصيل حول الوثائق، قم بزيارة [توثيقات واجهة برمجة تطبيقات Aspose.Words لـ .NET](https://reference.aspose.com/words/net/).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}