---
category: general
date: 2026-09-05
description: تعرّف على كيفية إنشاء مجموعة أشكال في ملف docx، وإدراج زر أمر ActiveX،
  وتحميل Markdown إلى مستند Word باستخدام مثال كامل بلغة C#.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create group shape docx
- insert activex command button
- load markdown into word document
language: ar
lastmod: 2026-09-05
og_description: إنشاء مجموعة أشكال في ملف docx، وإدراج زر أمر ActiveX، وتحميل Markdown
  إلى مستند Word باستخدام C#. اتبع هذا الدليل خطوةً بخطوة.
og_image_alt: Screenshot of a Word document showing a grouped shape and an ActiveX
  button
og_title: إنشاء مجموعة أشكال docx وتضمين عناصر تحكم ActiveX – دليل C#
schemas:
- author: Aspose
  dateModified: '2026-09-05'
  description: Learn how to create group shape docx, insert ActiveX command button,
    and load Markdown into a Word document with a complete C# example.
  headline: How to create group shape docx and add interactive controls in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Document automation
title: كيفية إنشاء مجموعة أشكال في ملف docx وإضافة عناصر تحكم تفاعلية في C#
url: /ar/java/images-shapes/how-to-create-group-shape-docx-and-add-interactive-controls/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# كيفية إنشاء مجموعة أشكال docx وإضافة عناصر تحكم تفاعلية في C#

إذا كنت بحاجة إلى **إنشاء مجموعة أشكال docx** برمجيًا، فإن هذا الدليل يوضح لك بالضبط كيفية القيام بذلك. ستتعرف أيضًا على كيفية **إدراج زر أمر ActiveX** وعناصر التحكم و**تحميل Markdown إلى مستند Word** دون فقدان تنسيق التسطير. في نهاية الدرس ستحصل على ملف `.docx` كامل الوظائف يجمع بين الرسومات المتجهية، وعناصر واجهة المستخدم التفاعلية، ومحتوى مبني على Markdown.

هذا الدرس يفترض أن لديك بيئة تطوير C# أساسية ومكتبة Aspose.Words for .NET مثبتة. لا تحتاج إلى أدوات خارجية—كل شيء يعمل داخل تطبيق .NET قياسي من نوع console أو desktop.

## المتطلبات المسبقة

- .NET 6.0 SDK أو أحدث (الكود يعمل أيضًا مع .NET Framework 4.7+)
- Aspose.Words for .NET (حزمة NuGet `Aspose.Words`)
- شهادة X.509 صالحة (`.pfx`) إذا كنت تريد اختبار خطوة التوقيع
- ملف صورة (مثال: `logo.png`) وملف markdown (`sample.md`) موجودان في مجلد معروف

> **نصيحة احترافية:** احفظ جميع ملفات الإدخال في مجلد *resources* واحد لتبسيط المسارات النسبية.

## الخطوة 1: إعداد المشروع واستيراد المساحات الاسمية

أنشئ مشروع console جديد وأضف توجيهات `using` المطلوبة. يوضح هذا القسم أيضًا كيفية الإشارة إلى فئات Aspose.Words التي ستستخدمها لاحقًا.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Loading;
using Aspose.Words.Saving;
using Aspose.Words.Saving.XpsSaveOptions; // only needed for signing example
using Aspose.Words.Saving.Signature;

// Ensure the license is applied if you have one
// Aspose.Words.License license = new Aspose.Words.License();
// license.SetLicense("Aspose.Words.lic");
```

تمنحك عبارات `using` وصولًا مباشرًا إلى `Document`، `DocumentBuilder`، `GroupShape`، `Forms2OleControl`، وغيرها من الأنواع المستخدمة طوال الدرس.

## الخطوة 2: **إنشاء مجموعة أشكال docx** – إضافة شكل مجموعة مع عناصر فرعية

*مجموعة الشكل* تسمح لك بمعاملة عدة كائنات رسم كوحدة واحدة. هذا مفيد لتحريك أو تغيير حجم الرسومات المرتبطة معًا.

```csharp
// Initialize a new empty document
Document document = new Document();
DocumentBuilder builder = new DocumentBuilder(document);

// Insert a group shape container
GroupShape group = builder.InsertGroupShape();

// Add a rectangle (100 × 50 points) as the first child
Shape rect = builder.InsertShape(ShapeType.Rectangle, 100, 50);
group.AppendChild(rect);

// Add an ellipse (80 × 40 points) as the second child
Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 80, 40);
group.AppendChild(ellipse);

// Optional: set a fill color for visual distinction
rect.FillColor = System.Drawing.Color.LightBlue;
ellipse.FillColor = System.Drawing.Color.LightCoral;

// Save the intermediate document so you can inspect the group
document.Save("Output/GroupShape.docx");
```

**لماذا مجموعة أشكال؟**  
تجعل التجميع المستطيل والبيضاوي متراصين عندما يقوم المستخدم بسحبهما في Word. كما يبسط العمليات اللاحقة مثل تطبيق حد مشترك أو تحريك الرسم بالكامل برمجيًا.

## الخطوة 3: إدراج عنصر تحكم محتوى نص عادي (نص نائب للمستخدم)

عناصر التحكم بالمحتوى تمنح المستخدمين مساحة منظمة لكتابة النص. يختفي النص النائب بمجرد بدء المستخدم بالكتابة.

```csharp
// Insert a plain‑text StructuredDocumentTag (SDT) after the group shape
StructuredDocumentTag sdt = builder.InsertStructuredDocumentTag(
    SdtType.PlainText, "MyTag");

// Set a friendly placeholder that appears in the UI
sdt.PlaceholderName = "Enter text here";

// Optionally, lock the content control to prevent deletion
sdt.LockContents = false;
sdt.LockContentControl = false;
```

خاصية `PlaceholderName` هي ما يعرضه Word كإشارة رمادية فاتحة. يمكن للمستخدمين استبدالها بنصهم الخاص، وتظل بنية XML الأساسية صحيحة.

## الخطوة 4: **إدراج زر أمر ActiveX** – إضافة واجهة مستخدم تفاعلية إلى المستند

لا تزال عناصر التحكم ActiveX مدعومة في ملفات Word الحديثة ويمكنها تشغيل ماكرو أو أتمتة خارجية. أدناه نضيف *زر أمر* ونحدد تسميته.

```csharp
// Insert an ActiveX Forms2OleControl at the current cursor position
Forms2OleControl commandBtn = builder.InsertForms2OleControl();

// Define the control type as a command button
commandBtn.ControlType = Forms2OleControl.ControlType.CommandButton;

// Set the visible caption
commandBtn.Caption = "Click Me";

// Position the button relative to the page (optional)
commandBtn.Left = 150;   // points from the left margin
commandBtn.Top = 300;    // points from the top margin
```

**متى تستخدم زر ActiveX؟**  
إذا كنت توزع المستند داخل بيئة مؤسسية تعتمد على ماكرو VBA، يمكن لزر ActiveX تشغيل ماكرو أو تطبيق خارجي. للتفاعلية القائمة على HTML فقط، فكر في استخدام *عناصر التحكم بالمحتوى* مع *Office.js* بدلاً من ذلك.

## الخطوة 5: إدراج صورة مخفية (مثل الشعار) للعلامة التجارية أو للوصول عبر السكريبت لاحقًا

الأشكال المخفية لا تُعرض في المستند المطبوع لكنها تبقى في XML، مما يتيح لك استرجاعها برمجيًا لاحقًا.

```csharp
// Insert an image from disk
Shape logo = builder.InsertImage("Resources/logo.png");

// Hide the image from the view/layout
logo.Hidden = true;

// You can still reference the image via its ShapeId if needed
string logoId = logo.Name;
```

## الخطوة 6: **تحميل markdown إلى مستند Word** مع الحفاظ على تنسيق التسطير

يمكن لـ Aspose.Words استيراد Markdown مباشرة. يضمن تمكين `ImportUnderlineFormatting` أن تصبح تسطيرات markdown (`<u>` أو `__text__`) أنماط تسطير في Word بدلاً من نص عادي.

```csharp
// Configure markdown load options
MarkdownLoadOptions mdOptions = new MarkdownLoadOptions
{
    ImportUnderlineFormatting = true
};

// Load the markdown file into a new Document instance
Document markdownDoc = new Document("Resources/sample.md", mdOptions);

// Append the markdown content to the main document after the previous elements
builder.MoveToDocumentEnd();
builder.InsertDocument(markdownDoc, ImportFormatMode.KeepSourceFormatting);
```

**حالة حافة:** إذا كان ملف markdown يحتوي على جداول، يتم تحويلها تلقائيًا إلى جداول Word. إذا كنت تحتاج إلى تنسيق جدول مخصص، استخدم `DocumentBuilder` بعد الإدراج.

## الخطوة 7: توقيع المستند باستخدام XAdES‑EPES (خطوة أمان اختيارية)

التوقيعات الرقمية تضمن سلامة المستند. الكود التالي يوقع ملف **إنشاء مجموعة أشكال docx** باستخدام ملف تعريف XAdES‑EPES.

```csharp
// Initialize the signature object for the current document
Signature signature = new Signature(document);

// Choose the XAdES‑EPES level
signature.XmlDsigLevel = XmlDsigLevel.XAdES_EPES;

// Sign using a .pfx certificate (replace path and password)
signature.Sign("Resources/cert.pfx", "password");

// Save the signed document
document.Save("Output/SignedGroupShape.docx");
```

> **ملاحظة أمان:** احفظ كلمة مرور الشهادة بعيدًا عن التحكم في المصدر. استخدم متغيرات البيئة أو مخزن آمن في بيئة الإنتاج.

## مثال كامل قابل للتنفيذ

دمج جميع الخطوات معًا ينتج برنامجًا واحدًا مكتملًا. احفظ الملف باسم `Program.cs` وشغله من سطر الأوامر.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Loading;
using Aspose.Words.Saving.Signature;

class Program
{
    static void Main()
    {
        // 1️⃣ Create the document and group shape
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
        GroupShape group = builder.InsertGroupShape();
        group.AppendChild(builder.InsertShape(ShapeType.Rectangle, 100, 50));
        group.AppendChild(builder.InsertShape(ShapeType.Ellipse, 80, 40));

        // 2️⃣ Add a plain‑text content control
        StructuredDocumentTag sdt = builder.InsertStructuredDocumentTag(
            SdtType.PlainText, "MyTag");
        sdt.PlaceholderName = "Enter text here";

        // 3️⃣ Insert an ActiveX command button
        Forms2OleControl btn = builder.InsertForms2OleControl();
        btn.ControlType = Forms2OleControl.ControlType.CommandButton;
        btn.Caption = "Click Me";

        // 4️⃣ Insert a hidden logo image
        Shape logo = builder.InsertImage("Resources/logo.png");
        logo.Hidden = true;

        // 5️⃣ Load markdown while keeping underline formatting
        MarkdownLoadOptions mdOpts = new MarkdownLoadOptions
        {
            ImportUnderlineFormatting = true
        };
        Document mdDoc = new Document("Resources/sample.md", mdOpts);
        builder.MoveToDocumentEnd();
        builder.InsertDocument(mdDoc, ImportFormatMode.KeepSourceFormatting);

        // 6️⃣ Sign the document (optional)
        Signature sig = new Signature(doc);
        sig.XmlDsigLevel = XmlDsigLevel.XAdES_EPES;
        sig.Sign("Resources/cert.pfx", "password");

        // Save the final file
        doc.Save("Output/CompleteGroupShape.docx");
        Console.WriteLine("Document created successfully.");
    }
}
```

تشغيل البرنامج يولد `CompleteGroupShape.docx` يحتوي على:

- مستطيل + بيضاوي مجمّع (نواة **إنشاء مجموعة أشكال docx**)
- عنصر تحكم محتوى نص عادي مع نص نائب
- **زر أمر ActiveX** مسمى “Click Me”
- صورة شعار مخفية
- محتوى Markdown مع الحفاظ على التسطير
- توقيع رقمي XAdES‑EPES (إذا تم توفير الشهادة)

## أسئلة شائعة واستكشاف الأخطاء وإصلاحها

| السؤال | الجواب |
|---|---|
| **هل سيعمل زر ActiveX على Word لنظام macOS؟** | Word على macOS لا يدعم عناصر التحكم ActiveX. سيظهر الزر كصورة ثابتة. استخدم عناصر التحكم بالمحتوى مع Office.js للتفاعلية عبر المنصات. |
| **ماذا لو كان ملف markdown يحتوي على CSS مخصص؟** | Aspose.Words يتجاهل CSS؛ يتم معالجة فقط صsyntax markdown القياسي. حوّل العناصر ذات الأنماط CSS إلى أنماط Word يدويًا بعد الاستيراد. |
| **هل يمكنني إضافة المزيد من الأشكال إلى نفس المجموعة لاحقًا؟** | نعم. استرجع `GroupShape` بالاسم أو الفهرس، ثم استدعِ `AppendChild(newShape)`. تذكر إعادة حفظ المستند بعد التعديلات. |
| **كيف أغيّر خوارزمية التوقيع؟** | عيّن `signature.SignatureAlgorithm` قبل استدعاء `Sign`. الافتراضي هو SHA‑256، وهو يلبي معظم متطلبات الامتثال. |
| **هل الصورة المخفية مرئية في واجهة Word؟** | لا، لكنها يمكن عرضها بتفعيل *إظهار النص المخفي* في خيارات Word. هذا مفيد لتخزين بيانات تعريفية دون إغراق التخطيط. |

## الخطوات التالية

الآن بعد أن أصبحت قادرًا على **إنشاء مجموعة أشكال docx**، **إدراج زر أمر ActiveX**، و**تحميل markdown إلى مستند Word**، يمكنك استكشاف:

- **دمج ماكرو VBA** يتفاعل مع نقرة زر ActiveX.
- **تطبيق أنماط مخصصة** على الفقرات التي يولدها Markdown.
- **إنشاء ملفات PDF** من نفس المستند باستخدام `doc.Save("output.pdf", SaveFormat.Pdf)`.
- **أتمتة معالجة دفعات** من ملفات markdown متعددة إلى تقرير موحد واحد.

تتيح لك هذه الإضافات بناء خطوط أنابيب مستندات مؤتمتة بالكامل تجمع بين الرسومات الغنية، وعناصر التحكم التفاعلية، وتأليف المحتوى المستند إلى Markdown—كل ذلك من C#.

---

*برمجة سعيدة! إذا وجدت هذا الدرس مفيدًا

## ما الذي يجب أن تتعلمه بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات الموضحة في هذا الدليل. كل مورد يتضمن أمثلة شفرة كاملة مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف أساليب تنفيذ بديلة في مشاريعك.

- [إنشاء مجموعة أشكال في مستند Word باستخدام Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [إنشاء شكل مستطيل في Word باستخدام C# – دليل خطوة بخطوة](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [إنشاء markdown من Word – دليل C# كامل](/words/english/java/document-conversion-and-export/create-markdown-from-word-complete-c-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}