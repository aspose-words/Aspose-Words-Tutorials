---
"description": "تعرّف على كيفية إدراج جدول محتويات في Word باستخدام Aspose.Words لـ .NET. اتبع دليلنا خطوة بخطوة لتصفح المستندات بسلاسة."
"linktitle": "إدراج جدول المحتويات في مستند Word"
"second_title": "واجهة برمجة تطبيقات معالجة المستندات Aspose.Words"
"title": "إدراج جدول المحتويات في مستند Word"
"url": "/ar/net/add-content-using-documentbuilder/insert-table-of-contents/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# إدراج جدول المحتويات في مستند Word

## مقدمة
في هذا البرنامج التعليمي، ستتعلم كيفية إضافة جدول محتويات (TOC) بكفاءة إلى مستندات Word باستخدام Aspose.Words لـ .NET. تُعد هذه الميزة أساسية لتنظيم المستندات الطويلة والتنقل بينها، وتحسين سهولة القراءة، وتوفير نظرة عامة سريعة على أقسام المستند.

## المتطلبات الأساسية

قبل أن تبدأ، تأكد من أن لديك ما يلي:

- فهم أساسي لـ C# وإطار عمل .NET.
- تم تثبيت Visual Studio على جهازك.
- مكتبة Aspose.Words لـ .NET. إذا لم تُثبّتها بعد، يُمكنك تنزيلها من [هنا](https://releases.aspose.com/words/net/).

## استيراد مساحات الأسماء

للبدء، قم باستيراد المساحات الأساسية اللازمة في مشروع C# الخاص بك:

```csharp
using Aspose.Words;
using Aspose.Words.Builder;
using Aspose.Words.Fields;
using Aspose.Words.Tables;
```

دعونا نقسم العملية إلى خطوات واضحة:

## الخطوة 1: تهيئة مستند Aspose.Words وDocumentBuilder

أولاً، قم بتشغيل Aspose.Words جديد `Document` كائن و `DocumentBuilder` للعمل مع:

```csharp
// تهيئة المستند وDocumentBuilder
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## الخطوة 2: إدراج جدول المحتويات

الآن، أدخل جدول المحتويات باستخدام `InsertTableOfContents` طريقة:

```csharp
// إدراج جدول المحتويات
builder.InsertTableOfContents("\\o \"1-3\" \\h \\z \\u");
```

## الخطوة 3: بدء محتوى المستند على صفحة جديدة

لضمان التنسيق الصحيح، ابدأ بمحتوى المستند الفعلي على صفحة جديدة:

```csharp
// إدراج فاصل الصفحة
builder.InsertBreak(BreakType.PageBreak);
```

## الخطوة 4: هيكلة مستندك بالعناوين

قم بتنظيم محتوى مستندك باستخدام أنماط العناوين المناسبة:

```csharp
// تعيين أنماط العناوين
builder.ParagraphFormat.StyleIdentifier = StyleIdentifier.Heading1;
builder.Writeln("Heading 1");

builder.ParagraphFormat.StyleIdentifier = StyleIdentifier.Heading2;
builder.Writeln("Heading 1.1");
builder.Writeln("Heading 1.2");

builder.ParagraphFormat.StyleIdentifier = StyleIdentifier.Heading1;
builder.Writeln("Heading 2");
builder.Writeln("Heading 3");

builder.ParagraphFormat.StyleIdentifier = StyleIdentifier.Heading2;
builder.Writeln("Heading 3.1");

builder.ParagraphFormat.StyleIdentifier = StyleIdentifier.Heading3;
builder.Writeln("Heading 3.1.1");
builder.Writeln("Heading 3.1.2");
builder.Writeln("Heading 3.1.3");

builder.ParagraphFormat.StyleIdentifier = StyleIdentifier.Heading2;
builder.Writeln("Heading 3.2");
builder.Writeln("Heading 3.3");
```

## الخطوة 5: تحديث جدول المحتويات وتعبئته

تحديث جدول المحتويات ليعكس بنية المستند:

```csharp
// تحديث حقول جدول المحتويات
doc.UpdateFields();
```

## الخطوة 6: حفظ المستند

وأخيرًا، احفظ مستندك في الدليل المحدد:

```csharp
// حفظ المستند
string dataDir = "YOUR_DOCUMENT_DIRECTORY_PATH";
doc.Save(dataDir + "InsertTableOfContentsUsingAsposeWords.docx");
```

## خاتمة

إضافة جدول محتويات باستخدام Aspose.Words لـ .NET أمرٌ سهلٌ ويُحسّن سهولة استخدام مستنداتك بشكل ملحوظ. باتباع هذه الخطوات، يمكنك تنظيم المستندات المعقدة والتنقل بينها بكفاءة.

## الأسئلة الشائعة

### هل يمكنني تخصيص مظهر جدول المحتويات؟
نعم، يمكنك تخصيص مظهر وسلوك جدول المحتويات باستخدام Aspose.Words لواجهات برمجة التطبيقات .NET.

### هل يدعم Aspose.Words تحديث الحقول تلقائيًا؟
نعم، يسمح لك Aspose.Words بتحديث الحقول مثل جدول المحتويات بشكل ديناميكي استنادًا إلى تغييرات المستند.

### هل يمكنني إنشاء جداول محتويات متعددة في مستند واحد؟
يدعم Aspose.Words إنشاء جداول محتويات متعددة بإعدادات مختلفة ضمن مستند واحد.

### هل Aspose.Words متوافق مع الإصدارات المختلفة من Microsoft Word؟
نعم، يضمن Aspose.Words التوافق مع الإصدارات المختلفة من تنسيقات Microsoft Word.

### أين يمكنني العثور على مزيد من المساعدة والدعم لـ Aspose.Words؟
لمزيد من المساعدة، قم بزيارة [منتدى Aspose.Words](https://forum.aspose.com/c/words/8) أو تحقق من [الوثائق الرسمية](https://reference.aspose.com/words/net/).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}