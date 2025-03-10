---
title: إنشاء رأس وتذييل الصفحة
linktitle: إنشاء رأس وتذييل الصفحة
second_title: واجهة برمجة تطبيقات معالجة المستندات Aspose.Words
description: تعرف على كيفية إضافة وتخصيص الرؤوس والتذييلات في مستندات Word باستخدام Aspose.Words for .NET. يضمن هذا الدليل التفصيلي تنسيق المستندات بشكل احترافي.
weight: 10
url: /ar/net/working-with-headers-and-footers/create-header-footer/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# إنشاء رأس وتذييل الصفحة

## مقدمة

إن إضافة رؤوس وتذييلات إلى مستنداتك يمكن أن يعزز من احترافيتها وقابليتها للقراءة. باستخدام Aspose.Words for .NET، يمكنك بسهولة إنشاء وتخصيص رؤوس وتذييلات لمستندات Word الخاصة بك. في هذا البرنامج التعليمي، سنرشدك خلال العملية خطوة بخطوة، لضمان قدرتك على تنفيذ هذه الميزات بسلاسة.

## المتطلبات الأساسية

قبل أن تبدأ، تأكد من أن لديك ما يلي:

-  Aspose.Words for .NET: تنزيل وتثبيت من[رابط التحميل](https://releases.aspose.com/words/net/).
- بيئة التطوير: مثل Visual Studio، لكتابة وتشغيل التعليمات البرمجية الخاصة بك.
- المعرفة الأساسية بلغة C#: فهم لغة C# وإطار عمل .NET.
- مستند نموذجي: مستند نموذجي لتطبيق الرؤوس والتذييلات، أو إنشاء مستند جديد كما هو موضح في البرنامج التعليمي.

## استيراد مساحات الأسماء

أولاً، يتعين عليك استيراد المساحات الأساسية اللازمة للوصول إلى فئات وطرق Aspose.Words.

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
using System;
```

## الخطوة 1: تحديد دليل المستندات

قم بتحديد الدليل الذي سيتم حفظ المستند فيه. يساعد هذا في إدارة المسار بشكل فعال.

```csharp
// المسار إلى دليل المستندات
string dataDir = "YOUR_DIRECTORY_OF_DOCUMENTS";
```

## الخطوة 2: إنشاء مستند جديد

 إنشاء مستند جديد و`DocumentBuilder`لتسهيل إضافة المحتوى.

```csharp
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## الخطوة 3: تكوين إعداد الصفحة

قم بإعداد إعدادات الصفحة، بما في ذلك ما إذا كانت الصفحة الأولى ستحتوي على رأس/تذييل مختلف.

```csharp
Section currentSection = builder.CurrentSection;
PageSetup pageSetup = currentSection.PageSetup;

pageSetup.DifferentFirstPageHeaderFooter = true;
pageSetup.HeaderDistance = 20;
```

## الخطوة 4: إضافة رأس الصفحة إلى الصفحة الأولى

انتقل إلى قسم الرأس للصفحة الأولى وقم بتكوين نص الرأس.

```csharp
builder.MoveToHeaderFooter(HeaderFooterType.HeaderFirst);
builder.ParagraphFormat.Alignment = ParagraphAlignment.Center;

builder.Font.Name = "Arial";
builder.Font.Bold = true;
builder.Font.Size = 14;

builder.Write("Aspose.Words Header/Footer Creation Primer - Title Page.");
```

## الخطوة 5: إضافة رأس رئيسي

انتقل إلى قسم الرأس الرئيسي وأدرج صورة ونصًا.

```csharp
builder.MoveToHeaderFooter(HeaderFooterType.HeaderPrimary);

// إدراج صورة في الرأس
builder.InsertImage(dataDir + "Graphics Interchange Format.gif", 
    RelativeHorizontalPosition.Page, 10, RelativeVerticalPosition.Page, 10, 50, 50, WrapType.Through);

builder.ParagraphFormat.Alignment = ParagraphAlignment.Right;
builder.Write("Aspose.Words Header/Footer Creation Primer.");
```

## الخطوة 6: إضافة تذييل أساسي

انتقل إلى قسم التذييل الأساسي وقم بإنشاء جدول لتنسيق محتوى التذييل.

```csharp
builder.MoveToHeaderFooter(HeaderFooterType.FooterPrimary);

builder.StartTable();
builder.CellFormat.ClearFormatting();
builder.InsertCell();
builder.CellFormat.PreferredWidth = PreferredWidth.FromPercent(100 / 3);

// إضافة ترقيم الصفحات
builder.Write("Page ");
builder.InsertField("PAGE", "");
builder.Write(" of ");
builder.InsertField("NUMPAGES", "");

builder.CurrentParagraph.ParagraphFormat.Alignment = ParagraphAlignment.Left;
builder.InsertCell();
builder.CellFormat.PreferredWidth = PreferredWidth.FromPercent(100 * 2 / 3);

builder.Write("(C) 2001 Aspose Pty Ltd. All rights reserved.");
builder.CurrentParagraph.ParagraphFormat.Alignment = ParagraphAlignment.Right;

builder.EndRow();
builder.EndTable();
```

## الخطوة 7: إضافة المحتوى وفواصل الصفحات

انتقل إلى نهاية المستند وأضف فاصلًا للصفحة وأنشئ قسمًا جديدًا بإعدادات صفحة مختلفة.

```csharp
builder.MoveToDocumentEnd();
builder.InsertBreak(BreakType.PageBreak);
builder.InsertBreak(BreakType.SectionBreakNewPage);

currentSection = builder.CurrentSection;
pageSetup = currentSection.PageSetup;
pageSetup.Orientation = Orientation.Landscape;
pageSetup.DifferentFirstPageHeaderFooter = false;

currentSection.HeadersFooters.LinkToPrevious(false);
CopyHeadersFootersFromPreviousSection(currentSection);

HeaderFooter primaryFooter = currentSection.HeadersFooters[HeaderFooterType.FooterPrimary];
Row row = primaryFooter.Tables[0].FirstRow;
row.FirstCell.CellFormat.PreferredWidth = PreferredWidth.FromPercent(100 / 3);
row.LastCell.CellFormat.PreferredWidth = PreferredWidth.FromPercent(100 * 2 / 3);

doc.Save(dataDir + "WorkingWithHeadersAndFooters.CreateHeaderFooter.docx");
```

## الخطوة 8: نسخ الرؤوس والتذييلات من القسم السابق

إذا كنت تريد إعادة استخدام الرؤوس والتذييلات من قسم سابق، فقم بنسخها وتطبيق التعديلات اللازمة.

```csharp
private static void CopyHeadersFootersFromPreviousSection(Section section)
{
    Section previousSection = (Section)section.PreviousSibling;
    if (previousSection == null) return;

    section.HeadersFooters.Clear();

    foreach (HeaderFooter headerFooter in previousSection.HeadersFooters)
    {
        section.HeadersFooters.Add(headerFooter.Clone(true));
    }
}
```

## خاتمة

باتباع هذه الخطوات، يمكنك إضافة وتخصيص الرؤوس والتذييلات في مستندات Word الخاصة بك بفعالية باستخدام Aspose.Words for .NET. وهذا يعزز مظهر مستندك واحترافيته، مما يجعله أكثر قابلية للقراءة وجاذبية.

## الأسئلة الشائعة

### ما هو Aspose.Words لـ .NET؟

Aspose.Words for .NET هي مكتبة تتيح للمطورين إنشاء مستندات Word وتحريرها وتحويلها برمجيًا داخل تطبيقات .NET.

### هل يمكنني إضافة صور إلى الرأس أو التذييل؟

 نعم، يمكنك بسهولة إضافة الصور إلى الرأس أو التذييل باستخدام`DocumentBuilder.InsertImage` طريقة.

### كيف أقوم بتعيين رؤوس وتذييلات مختلفة للصفحة الأولى؟

 يمكنك تعيين رؤوس وتذييلات مختلفة للصفحة الأولى باستخدام`DifferentFirstPageHeaderFooter` ممتلكات`PageSetup` فصل.

### أين يمكنني العثور على مزيد من الوثائق حول Aspose.Words؟

 يمكنك العثور على وثائق شاملة حول[صفحة توثيق واجهة برمجة التطبيقات Aspose.Words](https://reference.aspose.com/words/net/).

### هل يتوفر الدعم لـ Aspose.Words؟

 نعم، تقدم Aspose الدعم من خلال[منتدى الدعم](https://forum.aspose.com/c/words/8).

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
