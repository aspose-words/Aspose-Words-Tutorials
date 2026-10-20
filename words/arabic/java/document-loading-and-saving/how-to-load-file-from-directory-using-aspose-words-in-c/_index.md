---
category: general
date: 2026-09-11
description: تحميل ملف من الدليل باستخدام Aspose.Words مع خيارات التحميل الافتراضية
  وتعلم كيفية تعيين ترميز المستند أو تخصيص خيارات التحميل في C#.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- load file from directory
- default load options
- set document encoding
- set load options
language: ar
lastmod: 2026-09-11
og_description: تحميل ملف من الدليل باستخدام Aspose.Words مع خيارات التحميل الافتراضية،
  تعيين ترميز المستند، وتخصيص خيارات التحميل لأي مستند Word.
og_image_alt: Diagram illustrating load file from directory process with Aspose.Words
og_title: تحميل ملف من الدليل باستخدام Aspose.Words – دليل C# الكامل
schemas:
- author: Aspose
  dateModified: '2026-09-11'
  description: Load file from directory with Aspose.Words using default load options
    and learn how to set document encoding or customize load options in C#.
  headline: How to load file from directory using Aspose.Words in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Document processing
title: كيفية تحميل ملف من الدليل باستخدام Aspose.Words في C#
url: /ar/java/document-loading-and-saving/how-to-load-file-from-directory-using-aspose-words-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# كيفية تحميل ملف من دليل باستخدام Aspose.Words في C#

إذا كنت بحاجة إلى **load file from directory** في سير عمل معالجة Word، فإن Aspose.Words يجعل ذلك بسيطًا. يوضح هذا الدليل كيفية استخدام **default load options**، **set document encoding**، و **set load options** لتناسب السيناريو الخاص بك.

غالبًا ما يواجه المطورون صعوبات في تحميل المستند عندما يكون ملف المصدر موجودًا في مجلد مخصص أو يستخدم ترميزًا غير UTF‑8. بحلول نهاية هذا الدرس ستتمكن من تحميل أي ملف `.docx` من أي دليل، التحكم في ترميزه، وتعديل سلوك التحميل دون كتابة شفرة إضافية.

## ما ستحققه

- تحميل مستند Word من دليل عشوائي باستخدام سطر واحد من الشفرة.  
- فهم ما توفره **default load options** ومتى تحتاج إلى تعديلها.  
- تطبيق **set document encoding** لتفسير مجموعات الأحرف القديمة مثل Big5 بشكل صحيح.  
- تخصيص **set load options** لضبط استخدام الذاكرة، معالجة كلمات المرور، والمزيد.  

### المتطلبات المسبقة

- .NET 6.0 أو أحدث (المثال يستهدف .NET 6، لكن أي نسخة .NET حديثة تعمل).  
- Aspose.Words for .NET 23.9 أو أحدث – أضف حزمة NuGet `Aspose.Words`.  
- إلمام أساسي بـ C# و Visual Studio أو بيئة التطوير المتكاملة التي تفضلها.

---

## كيفية تحميل ملف من دليل باستخدام Aspose.Words

جوهر العملية هو مُنشئ `Document` واحد يقبل مسار ملف ونسخة اختيارية من `LoadOptions`. عندما تتجاهل `LoadOptions`، يقوم Aspose.Words تلقائيًا بتطبيق **default load options**، والتي تكون كافية لمعظم المستندات الحديثة.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Loading;

class Program
{
    static void Main()
    {
        // Step 1: Define the absolute path to the .docx file you want to load.
        string filePath = @"C:\MyDocuments\big5.docx";

        // Step 2: Load the document using the default load options.
        Document doc = new Document(filePath, new LoadOptions());

        // Verify that the document loaded by outputting the page count.
        Console.WriteLine($"Document loaded. Page count: {doc.PageCount}");
    }
}
```

**لماذا هذا يعمل:**  
- يقوم مُنشئ `Document` بقراءة الملف الموجود في `filePath`.  
- تمرير `new LoadOptions()` يخبر Aspose.Words باستخدام **default load options**، التي تكتشف تنسيق الملف تلقائيًا، تختار الترميز المناسب، وتطبق فحوصات الأمان القياسية.  

تشغيل البرنامج يطبع عدد الصفحات، مؤكدًا أن عملية **load file from directory** نجحت.

---

## استخدام default load options

على الرغم من أنه يمكنك تخطي معامل `LoadOptions` تمامًا، فإن إنشاء كائن `LoadOptions` صراحةً يوضح النية ويجهزك للتخصيصات المستقبلية.

```csharp
// Create a LoadOptions instance with the default configuration.
LoadOptions loadOptions = new LoadOptions();

// Load the document with those options.
Document doc = new Document(@"C:\MyDocuments\sample.docx", loadOptions);
```

**نقاط رئيسية حول default load options**

| الميزة | السلوك الافتراضي |
|---------|------------------|
| **Format detection** | يكتشف تلقائيًا DOC، DOCX، ODT، RTF، HTML، والعديد من الصيغ الأخرى. |
| **Encoding** | يكتشف UTF‑8، UTF‑16، والترميزات القديمة الشائعة؛ ويعود إلى UTF‑8 إذا فشل. |
| **Password handling** | يرمي استثناء `IncorrectPasswordException` إذا كان الملف محميًا بكلمة مرور. |
| **Memory usage** | يقوم بتحميل المستند بالكامل في الذاكرة، وهو مثالي للملفات التي تقل عن 100 ميغابايت. |

إذا كان مستندك مُشفرًا باستخدام مجموعة أحرف قديمة (مثل Big5) وفشل الاكتشاف التلقائي، يجب عليك **set document encoding** يدويًا.

---

## تعيين set document encoding

عندما يحتوي ملف على خطوط أو نص مُشفر بصفحة ترميز قديمة، يمكنك إخبار Aspose.Words أي ترميز يستخدم عبر خاصية `LoadOptions.Encoding`. هذه هي الطريقة المعتادة لـ **set document encoding** للملفات التي لا يستطيع الكاشف الافتراضي حلها.

```csharp
using System.Text;

// Step 1: Create LoadOptions and specify the encoding.
LoadOptions loadOptions = new LoadOptions
{
    // Big5 is code page 950.
    Encoding = Encoding.GetEncoding(950)
};

// Step 2: Load the document from the target directory.
Document doc = new Document(@"C:\MyDocuments\big5.docx", loadOptions);

// Step 3: Verify that the special characters are preserved.
Console.WriteLine($"First paragraph text: {doc.FirstSection.Body.Paragraphs[0].GetText()}");
```

**لماذا تحتاج هذا:**  
- بدون تعيين `Encoding` صراحةً، قد يفسر Aspose.Words البايتات كـ UTF‑8، مما يؤدي إلى ظهور أحرف مشوهة.  
- من خلال توفير صفحة الترميز الصحيحة، يقرأ المكتبة النص تمامًا كما قصده المؤلف.

**نصيحة:** استخدم `Encoding.GetEncoding("big5")` أو رقم صفحة الترميز (`950`) للمستندات الصينية التقليدية (Big5).

---

## تخصيص load options (set load options)

بالإضافة إلى الترميز، تُظهر `LoadOptions` العديد من الخصائص التي تسمح لك بـ **set load options** للسيناريوهات المتقدمة:

```csharp
// Create a LoadOptions object with several custom settings.
LoadOptions loadOptions = new LoadOptions
{
    // Force the document to be treated as a DOCX file, even if the extension is wrong.
    LoadFormat = LoadFormat.Docx,

    // Limit memory usage for very large files (e.g., 200 MB+).
    LoadOptionsMemoryUsage = LoadOptionsMemoryUsage.LowMemory,

    // Provide a password if the file is encrypted.
    Password = "MySecretPassword"
};

// Load the document using the customized options.
Document doc = new Document(@"C:\MyDocuments\protected.docx", loadOptions);
```

**شرح الخصائص المختارة**

| الخاصية | الغرض |
|----------|---------|
| `LoadFormat` | يفرض تنسيقًا محددًا، متجاوزًا الاكتشاف التلقائي. مفيد عندما تكون امتدادات الملفات مضللة. |
| `LoadOptionsMemoryUsage` | يختار استراتيجية توفير الذاكرة (`LowMemory`) للمستندات الضخمة. |
| `Password` | يوفر كلمة مرور للملفات المشفرة، لتجنب استثناء. |
| `ValidateDocumentStructure` | عند `true`، يتحقق المحمل من بنية XML الداخلية ويرمي استثناءً إذا كانت تالفة. |

يمكنك دمج أي من هذه مع **set document encoding** للتعامل مع أكثر خطوط الاستيراد تطلبًا.

---

## مثال كامل قابل للتنفيذ

فيما يلي برنامج مستقل يوضح جميع المفاهيم في تدفق واحد:

```csharp
using System;
using System.Text;
using Aspose.Words;
using Aspose.Words.Loading;

class LoadFileDemo
{
    static void Main()
    {
        // ------------------------------------------------------------------
        // 1️⃣ Define the directory and file name.
        // ------------------------------------------------------------------
        string directory = @"C:\MyDocuments";
        string fileName   = "big5.docx";               // Change as needed.
        string fullPath   = System.IO.Path.Combine(directory, fileName);

        // ------------------------------------------------------------------
        // 2️⃣ Create LoadOptions with explicit encoding (Big5) and low‑memory mode.
        // ------------------------------------------------------------------
        LoadOptions loadOptions = new LoadOptions
        {
            Encoding = Encoding.GetEncoding(950), // Big5 code page.
            LoadOptionsMemoryUsage = LoadOptionsMemoryUsage.LowMemory
        };

        // ------------------------------------------------------------------
        // 3️⃣ Load the document from the directory using the custom options.
        // ------------------------------------------------------------------
        Document doc = new Document(fullPath, loadOptions);

        // ------------------------------------------------------------------
        // 4️⃣ Verify the load succeeded.
        // ------------------------------------------------------------------
        Console.WriteLine($"Document loaded from \"{fullPath}\"");
        Console.WriteLine($"Page count: {doc.PageCount}");
        Console.WriteLine($"First paragraph: {doc.FirstSection.Body.Paragraphs[0].GetText().Trim()}");

        // ------------------------------------------------------------------
        // 5️⃣ (Optional) Save as PDF to confirm visual fidelity.
        // ------------------------------------------------------------------
        string pdfPath = System.IO.Path.ChangeExtension(fullPath, ".pdf");
        doc.Save(pdfPath);
        Console.WriteLine($"Saved PDF version to \"{pdfPath}\"");
    }
}
```

**مخرجات وحدة التحكم المتوقعة**

```
Document loaded from "C:\MyDocuments\big5.docx"
Page count: 3
First paragraph: 這是一個測試文件
Saved PDF version to "C:\MyDocuments\big5.pdf"
```

تشغيل البرنامج يوضح كيفية **load file from directory**، **set document encoding**، و **set load options** في سير عمل واحد واضح.

---

## الأخطاء الشائعة وكيفية تجنبها

| العَرَض | السبب المحتمل | الحل |
|---------|--------------|-----|
| أحرف صينية مشوهة | عدم تعيين الترميز أو صفحة الترميز الخاطئة | **Set document encoding** إلى `Encoding.GetEncoding(950)` لـ Big5. |
| `IncorrectPasswordException` رغم أن الملف غير محمي بكلمة مرور | المحمل اكتشف الملف الثنائي على أنه مشفر | حدد `LoadFormat` صراحةً إلى النوع الصحيح (مثال: `LoadFormat.Docx`). |
| Out

## ما الذي يجب أن تتعلمه بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات الموضحة في هذا الدليل. كل مورد يتضمن أمثلة شفرة كاملة مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف أساليب تنفيذ بديلة في مشاريعك.

- [استعادة ملف docx التالف باستخدام Aspose.Words – تعيين وضع الاسترداد وخيارات التحميل](/words/english/net/programming-with-loadoptions/recover-damaged-docx-with-aspose-words-set-recovery-mode-and/)
- [كيفية تحميل مستندات RTF مع تكوين خيارات تحميل RTF في Aspose.Words للـ Java](/words/english/java/document-loading-and-saving/configuring-rtf-load-options/)
- [إتقان خيارات تحميل Markdown مع Aspose.Words للـ Java](/words/english/java/document-operations/master-markdown-load-options-aspose-words-java/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}