---
title: إزالة رؤوس وتذييلات المصدر
linktitle: إزالة رؤوس وتذييلات المصدر
second_title: واجهة برمجة تطبيقات معالجة المستندات Aspose.Words
description: تعرف على كيفية إزالة الرؤوس والتذييلات في مستندات Word باستخدام Aspose.Words for .NET. قم بتبسيط إدارة المستندات لديك باستخدام دليلنا خطوة بخطوة.
weight: 10
url: /ar/net/join-and-append-documents/remove-source-headers-footers/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# إزالة رؤوس وتذييلات المصدر

## مقدمة

في هذا الدليل الشامل، سنتناول بالتفصيل كيفية إزالة الرؤوس والتذييلات بفعالية من مستند Word باستخدام Aspose.Words for .NET. تُستخدم الرؤوس والتذييلات عادةً لترقيم الصفحات أو عناوين المستندات أو غيرها من المحتويات المتكررة في مستندات Word. سواء كنت تقوم بدمج المستندات أو تنظيف التنسيق، فإن إتقان هذه العملية يمكن أن يبسط مهام إدارة المستندات الخاصة بك. دعنا نستكشف العملية خطوة بخطوة لتحقيق ذلك باستخدام Aspose.Words for .NET.

## المتطلبات الأساسية

قبل الغوص في البرنامج التعليمي، تأكد من إعداد المتطلبات الأساسية التالية:

1. بيئة التطوير: قم بتثبيت Visual Studio أو أي بيئة تطوير .NET أخرى.
2.  Aspose.Words for .NET: تأكد من تنزيل Aspose.Words for .NET وتثبيته. إذا لم يكن الأمر كذلك، فيمكنك الحصول عليه من[هنا](https://releases.aspose.com/words/net/).
3. المعرفة الأساسية: الإلمام ببرمجة C# وأساسيات إطار عمل .NET.

## استيراد مساحات الأسماء

قبل البدء في الترميز، تأكد من استيراد المساحات الأساسية اللازمة في ملف C# الخاص بك:

```csharp
using Aspose.Words;
```

## الخطوة 1: تحميل المستند المصدر

 أولاً، تحتاج إلى تحميل المستند المصدر الذي تريد إزالة الرؤوس والتذييلات منه. استبدل`"YOUR DOCUMENT DIRECTORY"` مع المسار الفعلي إلى دليل المستند الخاص بك حيث يوجد المستند المصدر.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document srcDoc = new Document(dataDir + "Document source.docx");
```

## الخطوة 2: إنشاء أو تحميل مستند الوجهة

 إذا لم تقم بالفعل بإنشاء مستند وجهة حيث تريد وضع المحتوى المعدل، فيمكنك إنشاء مستند جديد`Document` الكائن أو تحميل كائن موجود.

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

لمنع استمرار ظهور الرؤوس والتذييلات في المستند الوجهة (`dstDoc` ), تأكد من أن`LinkToPrevious` تم ضبط إعدادات الرؤوس والتذييلات على`false`.

```csharp
srcDoc.FirstSection.HeadersFooters.LinkToPrevious(false);
```

## الخطوة 5: إضافة المستند المعدّل إلى المستند الوجهة

أخيرًا، قم بإرفاق المحتوى المعدّل من المستند المصدر (`srcDoc`) إلى المستند الوجهة (`dstDoc`) مع الحفاظ على تنسيق المصدر.

```csharp
dstDoc.AppendDocument(srcDoc, ImportFormatMode.KeepSourceFormatting);
```

## الخطوة 6: احفظ المستند الناتج

احفظ المستند النهائي مع إزالة الرؤوس والتذييلات في الدليل المحدد.

```csharp
dstDoc.Save(dataDir + "JoinAndAppendDocuments.RemoveSourceHeadersFooters.docx");
```

## خاتمة

إن إزالة الرؤوس والتذييلات من مستند Word باستخدام Aspose.Words for .NET هي عملية بسيطة يمكنها تحسين مهام إدارة المستندات بشكل كبير. باتباع الخطوات الموضحة أعلاه، يمكنك تنظيف المستندات بكفاءة للحصول على مظهر أنيق واحترافي.

## الأسئلة الشائعة

### هل يمكنني إزالة الرؤوس والتذييلات من أقسام محددة فقط؟
نعم، يمكنك التكرار عبر الأقسام ومسح الرؤوس والتذييلات بشكل انتقائي حسب الحاجة.

### هل يدعم Aspose.Words for .NET إزالة الرؤوس والتذييلات من مستندات متعددة؟
بالتأكيد، يمكنك معالجة الرؤوس والتذييلات عبر مستندات متعددة باستخدام Aspose.Words لـ .NET.

###  ماذا يحدث إذا نسيت الضبط`LinkToPrevious` to `false`?
يمكن أن تستمر الرؤوس والتذييلات من المستند المصدر في المستند الوجهة.

### هل يمكنني إزالة الرؤوس والتذييلات برمجيًا دون التأثير على التنسيقات الأخرى؟
نعم، يسمح لك Aspose.Words for .NET بإزالة الرؤوس والتذييلات مع الحفاظ على باقي تنسيق المستند.

### أين يمكنني العثور على المزيد من الموارد والدعم لـ Aspose.Words لـ .NET؟
 قم بزيارة[توثيق Aspose.Words لـ .NET](https://reference.aspose.com/words/net/) للحصول على مراجع مفصلة وأمثلة لواجهة برمجة التطبيقات.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
