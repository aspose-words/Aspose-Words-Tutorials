---
category: general
date: 2026-09-14
description: تعلم كيفية إدراج العلامة، إضافة الأشكال، إنشاء مجموعة، وحفظ المستند بصيغة
  DOCX باستخدام Aspose.Words في C#.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to insert tag
- save document as docx
- how to create group
- how to add shapes
- how to save docx
language: ar
lastmod: 2026-09-14
og_description: كيفية إدراج علامة، إضافة أشكال، إنشاء مجموعة، وحفظ المستند كملف DOCX
  باستخدام Aspose.Words. اتبع الدليل خطوة بخطوة.
og_image_alt: Diagram showing how to insert tag inside a grouped shape before saving
  as DOCX
og_title: كيفية إدراج علامة وبناء شكل مجموعة في ملف DOCX باستخدام C#
schemas:
- author: Aspose
  dateModified: '2026-09-14'
  description: Learn how to insert tag, add shapes, create a group, and save document
    as DOCX using Aspose.Words in C#.
  headline: How to insert tag and create a group shape in a DOCX
  type: TechArticle
tags:
- Aspose.Words
- C#
- DOCX manipulation
title: كيفية إدراج علامة وإنشاء شكل مجموعة في ملف DOCX
url: /ar/net/programming-with-shapes/how-to-insert-tag-and-create-a-group-shape-in-a-docx/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# كيفية إدراج علامة وإنشاء شكل مجموعة في ملف DOCX

إذا كنت بحاجة إلى معرفة **كيفية إدراج علامة** أثناء بناء تخطيط معقد، يوضح لك هذا الدليل حلاً كاملاً وقابلاً للتنفيذ. سترى كيفية إضافة أشكال، إنشاء مجموعة، وأخيرًا **حفظ المستند كـ DOCX** باستخدام Aspose.Words for .NET.

غالبًا ما يتطلب توليد المستندات خلط علامات النص مع العناصر الرسومية. في هذا البرنامج التعليمي ستتعلم بالضبط **كيفية إدراج علامة**، وكيفية **إضافة أشكال**، وكيفية **إنشاء مجموعة**، والطريقة الصحيحة **لحفظ docx** حتى يمكن فتح الملف في Word دون فقدان الدقة.

## المتطلبات المسبقة

- .NET 6.0 أو أحدث (الكود يعمل أيضًا مع .NET Framework 4.7+)
- حزمة NuGet لـ Aspose.Words for .NET (`Install-Package Aspose.Words`)
- إلمام أساسي بصياغة C#
- بيئة تطوير متكاملة مثل Visual Studio أو VS Code

لا توجد مكتبات إضافية مطلوبة؛ المثال الكامل يعمل بإشارة NuGet واحدة.

## كيفية إنشاء مجموعة وإضافة أشكال

الخطوة المنطقية الأولى هي إنشاء **مجموعة** ستحتوي على عدة أشكال. يضمن التجميع بقاء الأشكال معًا عند تحريكها أو تدويرها لاحقًا.

```csharp
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

// 1️⃣ Create an empty document and a DocumentBuilder
Document document = new Document();
DocumentBuilder builder = new DocumentBuilder(document);

// 2️⃣ Build a GroupShape (200 × 200 points) and set its bounds
GroupShape groupShape = new GroupShape(document, 200, 200);
groupShape.Bounds = new RectangleF(50, 50, 200, 200);

// 3️⃣ Add a rectangle shape
groupShape.AppendChild(new Shape(document, ShapeType.Rectangle)
{
    Width = 80,
    Height = 80,
    Left = 0,
    Top = 0
});

// 4️⃣ Add an ellipse shape next to the rectangle
groupShape.AppendChild(new Shape(document, ShapeType.Ellipse)
{
    Width = 80,
    Height = 80,
    Left = 100,
    Top = 0
});
```

**لماذا هذا مهم:**  
`GroupShape` يعمل كحاوية. عندما تقوم لاحقًا بتحريك المجموعة، يتحرك كل من المستطيل والبيضاوي معًا، مع الحفاظ على مواضعهما النسبية. هذه هي الطريقة الموصى بها لإدارة عدة رسومات تنتمي إلى نفس الكتلة المنطقية.

## كيفية إدراج علامة داخل المستند

الآن بعد أن أصبحت المجموعة جاهزة، يمكنك **إدراج علامة** (StructuredDocumentTag، والمعروفة أيضًا باسم SDT) مباشرةً بعد المجموعة. يمكن للعلامة أن تحتوي نصًا عاديًا، نصًا غنيًا، أو حتى محتوى متكرر.

```csharp
// 5️⃣ Insert the group at the current builder position
builder.InsertNode(groupShape);

// 6️⃣ Insert a plain‑text StructuredDocumentTag (SDT) and write content
builder.InsertStructuredDocumentTag(StructuredDocumentTagType.PlainText, "MyTag");
builder.Writeln("Content inside the SDT");
```

**لماذا يجب عليك استخدام StructuredDocumentTag:**  
توفر الـ SDT علامة دلالية يمكن لـ Word التعرف عليها للتحكم بالمحتوى، ربط البيانات، أو سيناريوهات تعبئة النماذج. باستخدام `InsertStructuredDocumentTag` تقوم بشكل صريح **بإدراج علامة** بطريقة تبقى صالحة بعد التعديل اللاحق في Microsoft Word.

## كيفية حفظ docx والتحقق من النتيجة

الخطوة الأخيرة هي حفظ المستند. يوضح الكود أدناه الطريقة الصحيحة **لحفظ المستند كـ docx** ومكان العثور على ملف الإخراج.

```csharp
// 7️⃣ Save the document to the file system
string outputPath = Path.Combine(Environment.GetFolderPath(Environment.SpecialFolder.Desktop), "GroupAndSDT.docx");
document.Save(outputPath);
Console.WriteLine($"Document saved to: {outputPath}");
```

عند فتح *GroupAndSDT.docx* في Word، يجب أن ترى رسمًا تجميعيًا لمستطيل‑بيضاوي يليه عنصر تحكم محتوى نصي عادي بعنوان **MyTag** يحتوي على السطر “Content inside the SDT”.

### النتيجة المتوقعة

- مجموعة بحجم 200 × 200 نقطة موضوعة عند (50, 50) على الصفحة.
- داخل المجموعة: مستطيل أزرق على اليسار وبيضاوي على اليمين (الألوان الافتراضية).
- مباشرةً أسفل المجموعة: عنصر تحكم محتوى معنون بـ **MyTag** يحتوي على النص “Content inside the SDT”.

## مثال كامل وقابل للتنفيذ

فيما يلي البرنامج الكامل الذي يمكنك نسخه ولصقه في تطبيق كونسول. يتضمن جميع توجيهات `using` الضرورية، معالجة الأخطاء، وتعليقات تشرح كل خطوة.

```csharp
using System;
using System.Drawing;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace AsposeWordsGroupAndTag
{
    class Program
    {
        static void Main()
        {
            // Create a new empty document and a DocumentBuilder to work with it
            Document document = new Document();
            DocumentBuilder builder = new DocumentBuilder(document);

            // Build a GroupShape (200x200) and define its bounds
            GroupShape groupShape = new GroupShape(document, 200, 200);
            groupShape.Bounds = new RectangleF(50, 50, 200, 200);

            // Add a rectangle to the group
            groupShape.AppendChild(new Shape(document, ShapeType.Rectangle)
            {
                Width = 80,
                Height = 80,
                Left = 0,
                Top = 0
            });

            // Add an ellipse to the group
            groupShape.AppendChild(new Shape(document, ShapeType.Ellipse)
            {
                Width = 80,
                Height = 80,
                Left = 100,
                Top = 0
            });

            // Insert the group into the document at the current builder position
            builder.InsertNode(groupShape);

            // Insert a plain‑text StructuredDocumentTag (SDT) and write some content inside it
            builder.InsertStructuredDocumentTag(StructuredDocumentTagType.PlainText, "MyTag");
            builder.Writeln("Content inside the SDT");

            // Save the resulting document
            string outputPath = Path.Combine(
                Environment.GetFolderPath(Environment.SpecialFolder.Desktop),
                "GroupAndSDT.docx");

            document.Save(outputPath);
            Console.WriteLine($"Document saved successfully to {outputPath}");
        }
    }
}
```

شغّل البرنامج، انتقل إلى سطح المكتب الخاص بك، وانقر مزدوجًا على *GroupAndSDT.docx* للتحقق من ظهور المجموعة والعلامة كما هو موصوف.

## أسئلة شائعة وحالات خاصة

| السؤال | الإجابة |
|----------|--------|
| **هل يمكنني إضافة أكثر من شكلين إلى المجموعة؟** | نعم. استدعِ `groupShape.AppendChild(new Shape(...))` لكل شكل إضافي قبل إدراج المجموعة. |
| **ماذا لو احتجت إلى علامة نص غني بدلاً من نص عادي؟** | استخدم `StructuredDocumentTagType.RichText` في `InsertStructuredDocumentTag`. |
| **كيف يمكنني تغيير لون المستطيل أو البيضاوي؟** | عيّن خاصية `FillColor` لكل كائن `Shape`، مثال: `shape.FillColor = Color.LightBlue;`. |
| **هل يمكن تدوير المجموعة بأكملها؟** | عيّن `groupShape.Rotation = 45;` (درجة) قبل إدراج العقدة. |
| **هل يجب استدعاء `Dispose()` على أي كائنات؟** | تدير Aspose.Words معظم الموارد داخليًا؛ إلغاء تخصيص `Document` اختياري في تطبيق كونسول قصير العمر. |

## أفضل الممارسات لحفظ ملفات DOCX

- **استخدم دائمًا مسارًا مطلقًا** (أو مسارًا نسبيًا معرفًا جيدًا) عند استدعاء `document.Save`. هذا يتجنب خطأ “الملف غير موجود” الذي قد يحدث مع أدلة عمل غير واضحة.
- **فضّل التحميلات الزائدة `Save` التي تقبل تدفقًا** إذا كنت بحاجة لإرسال المستند عبر HTTP أو تخزينه في قاعدة بيانات.
- **عيّن `CompatibilityOptions`** إذا كان عليك استهداف إصدارات أقدم من Word (مثل Word 2003). في معظم السيناريوهات الحديثة الإعدادات الافتراضية تعمل بشكل جيد.

## الخطوات التالية

الآن بعد أن عرفت **كيفية إدراج علامة**، وكيفية **إضافة أشكال**، وكيفية **إنشاء مجموعة**، وكيفية **حفظ docx**، يمكنك استكشاف سيناريوهات أكثر تقدمًا:

- دمج مجموعات متعددة لبناء مخططات معقدة.
- استخدم `StructuredDocumentTag` لربط البيانات في قوالب Word.
- تصدير نفس المستند إلى PDF (`document.Save("output.pdf")`) مع الحفاظ على الرسومات المجمعة.
- أتمتة تعبئة النماذج عن طريق ضبط محتوى الـ SDT برمجيًا (`builder.MoveToDocumentEnd(); builder.Write("New value");`).

جرّب قيم `ShapeType` مختلفة (مثل `ShapeType.Polygon`، `ShapeType.Line`) لترى كيف تتصرف داخل `GroupShape`. النمط نفسه يعمل للجداول، الصور، أو أي عقدة أخرى تريد إبقائها معًا.

---

**الملخص:** يوضح هذا الدليل **كيفية إدراج علامة** داخل شكل مجموعة، وكيفية **إضافة أشكال**، وكيفية **إنشاء مجموعة**، والطريقة الصحيحة **لحفظ المستند كـ docx** باستخدام Aspose.Words for .NET. لديك الآن أساس قوي لبناء ملفات DOCX غنية وتفاعلية برمجيًا.

## ماذا يجب أن تتعلم بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات الموضحة في هذا الدليل. كل مورد يتضمن أمثلة شفرة كاملة مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف أساليب تنفيذ بديلة في مشاريعك.

- [كيفية حفظ Markdown من DOCX – دليل خطوة بخطوة](/words/english/net/programming-with-markdownsaveoptions/how-to-save-markdown-from-docx-step-by-step-guide/)
- [كيفية استعادة DOCX – دليل كامل باستخدام Aspose.Words](/words/english/net/programming-with-loadoptions/how-to-recover-docx-complete-guide-using-aspose-words/)
- [كيفية فحص القواعد النحوية في DOCX باستخدام Aspose.Words – استخدم gpt-4 turbo](/words/english/net/ai-powered-document-processing/how-to-check-grammar-in-docx-with-aspose-words-use-gpt-4-tur/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}