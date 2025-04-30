---
"description": "تعرّف على كيفية إزالة الرؤوس والتذييلات من مستندات Word باستخدام Aspose.Words لـ .NET. بسّط إدارة مستنداتك مع دليلنا المفصل."
"linktitle": "إزالة رؤوس وتذييلات المصدر"
"second_title": "واجهة برمجة تطبيقات معالجة المستندات Aspose.Words"
"title": "إزالة رؤوس وتذييلات المصدر"
"url": "/ar/net/join-and-append-documents/remove-source-headers-footers/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# إزالة رؤوس وتذييلات المصدر

## مقدمة

في هذا الدليل الشامل، سنتناول بالتفصيل كيفية إزالة الرؤوس والتذييلات بفعالية من مستندات Word باستخدام Aspose.Words لـ .NET. تُستخدم الرؤوس والتذييلات عادةً لترقيم الصفحات، أو عناوين المستندات، أو أي محتوى متكرر آخر في مستندات Word. سواء كنت تقوم بدمج المستندات أو تحسين التنسيق، فإن إتقان هذه العملية يُسهّل مهام إدارة المستندات لديك. لنستعرض العملية خطوة بخطوة لتحقيق ذلك باستخدام Aspose.Words لـ .NET.

## المتطلبات الأساسية

قبل الغوص في البرنامج التعليمي، تأكد من إعداد المتطلبات الأساسية التالية:

1. بيئة التطوير: قم بتثبيت Visual Studio أو أي بيئة تطوير .NET أخرى.
2. Aspose.Words for .NET: تأكد من تنزيل Aspose.Words for .NET وتثبيته. إذا لم يكن كذلك، يمكنك الحصول عليه من [هنا](https://releases.aspose.com/words/net/).
3. المعرفة الأساسية: الإلمام ببرمجة C# وأساسيات إطار عمل .NET.

## استيراد مساحات الأسماء

قبل البدء في الترميز، تأكد من استيراد المساحات الأساسية اللازمة في ملف C# الخاص بك:

```csharp
using Aspose.Words;
```

## الخطوة 1: تحميل المستند المصدر

أولاً، عليك تحميل المستند المصدر الذي تريد إزالة الرؤوس والتذييلات منه. استبدل `"YOUR DOCUMENT DIRECTORY"` مع المسار الفعلي إلى دليل المستند الخاص بك حيث يوجد المستند المصدر.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document srcDoc = new Document(dataDir + "Document source.docx");
```

## الخطوة 2: إنشاء أو تحميل مستند الوجهة

إذا لم تقم بالفعل بإنشاء مستند وجهة حيث تريد وضع المحتوى المعدل، فيمكنك إنشاء مستند جديد `Document` الكائن أو تحميل كائن موجود.

```csharp
Document dstDoc = new Document(dataDir + "Northwind traders.docx");
```

## الخطوة 3: مسح الرؤوس والتذييلات من الأقسام

قم بالتكرار خلال كل قسم في المستند المصدر (`srcDoc`) ومسح رؤوسها وتذييلاتها.

```csharp
foreach (Section section in srcDoc.Sections)
{
    section.ClearHeadersFooters();
}
```

## الخطوة 4: إدارة إعدادات LinkToPrevious

لمنع استمرار ظهور الرؤوس والتذييلات في المستند الوجهة (`dstDoc`), تأكد من أن `LinkToPrevious` تم ضبط إعدادات الرؤوس والتذييلات على `false`.

```csharp
srcDoc.FirstSection.HeadersFooters.LinkToPrevious(false);
```

## الخطوة 5: إضافة المستند المعدّل إلى المستند الوجهة

وأخيرًا، قم بإرفاق المحتوى المعدّل من المستند المصدر (`srcDoc`) إلى المستند الوجهة (`dstDoc`) مع الحفاظ على تنسيق المصدر.

```csharp
dstDoc.AppendDocument(srcDoc, ImportFormatMode.KeepSourceFormatting);
```

## الخطوة 6: حفظ المستند الناتج

احفظ المستند النهائي مع إزالة الرؤوس والتذييلات في الدليل المحدد.

```csharp
dstDoc.Save(dataDir + "JoinAndAppendDocuments.RemoveSourceHeadersFooters.docx");
```

## خاتمة

إزالة الرؤوس والتذييلات من مستندات Word باستخدام Aspose.Words لـ .NET عملية سهلة تُحسّن إدارة المستندات بشكل كبير. باتباع الخطوات الموضحة أعلاه، يمكنك تنظيف مستنداتك بكفاءة للحصول على مظهر أنيق واحترافي.

## الأسئلة الشائعة

### هل يمكنني إزالة الرؤوس والتذييلات من أقسام محددة فقط؟
نعم، يمكنك التكرار خلال الأقسام ومسح الرؤوس والتذييلات بشكل انتقائي حسب الحاجة.

### هل يدعم Aspose.Words for .NET إزالة الرؤوس والتذييلات عبر مستندات متعددة؟
بالتأكيد، يمكنك معالجة الرؤوس والتذييلات عبر مستندات متعددة باستخدام Aspose.Words لـ .NET.

### ماذا يحدث إذا نسيت الضبط `LinkToPrevious` ل `false`؟
يمكن أن تستمر الرؤوس والتذييلات من المستند المصدر في المستند الوجهة.

### هل يمكنني إزالة الرؤوس والتذييلات برمجيًا دون التأثير على التنسيقات الأخرى؟
نعم، يسمح لك Aspose.Words for .NET بإزالة الرؤوس والتذييلات مع الحفاظ على باقي تنسيق المستند.

### أين يمكنني العثور على المزيد من الموارد والدعم لـ Aspose.Words لـ .NET؟
قم بزيارة [وثائق Aspose.Words لـ .NET](https://reference.aspose.com/words/net/) للحصول على مراجع API التفصيلية والأمثلة.



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}