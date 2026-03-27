---
category: general
date: 2026-03-27
description: احفظ ملف docx كملف txt باستخدام Aspose.Words وحوّل مستند Word إلى LaTeX.
  تعلّم كيفية تصدير المعادلات، الحفاظ على النص العادي، والحصول على تنسيق LaTeX في
  دقائق.
draft: false
keywords:
- save docx as txt
- convert word to latex
- how to export equations
- save word plain text
- export equations to latex
language: ar
og_description: احفظ ملف docx كملف txt باستخدام Aspose.Words. يوضح هذا الدليل كيفية
  تحويل Word إلى LaTeX، وتصدير المعادلات، والحفاظ على مستندك كنص عادي.
og_title: حفظ ملف docx كملف txt – تصدير معادلات Word إلى LaTeX
tags:
- Aspose.Words
- C#
- LaTeX
- Document Conversion
title: حفظ ملف docx كملف txt – دليل كامل لتصدير معادلات Word إلى LaTeX
url: /ar/net/programming-with-txtsaveoptions/save-docx-as-txt-complete-guide-to-exporting-word-equations/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# حفظ ملف docx كـ txt – تصدير معادلات Word إلى LaTeX

هل احتجت يومًا إلى **حفظ ملف docx كـ txt** لكنك خفت من فقدان الرياضيات المتقدمة الموجودة داخل ملف Word؟ لست وحدك. في العديد من سير عمل البحث العلمي يكون الإصدار النصي البسيط للمستند أمرًا ضروريًا، ومع ذلك تريد أن تبقى المعادلات على شكل ترميز LaTeX نظيف.  

في هذا الدرس سنستعرض الخطوات الدقيقة **لتحويل Word إلى LaTeX** باستخدام Aspose.Words for .NET، بحيث يتم تصدير المعادلات بشكل صحيح بينما يتحول باقي المستند إلى نص عادي منظم. في النهاية ستعرف كيف **تصدّر المعادلات إلى LaTeX**، وتحافظ على باقي الملف كنص بسيط، وتتجنب المشكلات الشائعة التي تواجه المبتدئين.

## ما ستتعلمه

- كيفية تحميل ملف *.docx* يحتوي على Office Math.  
- ضبط `TxtSaveOptions` بشكل صحيح لجعل Aspose ينتج LaTeX لكل معادلة.  
- حفظ النتيجة كملف **save word plain text** يمكنك إدخاله في نظام التحكم بالإصدارات، خطوط أنابيب CI، أو أي أداة لاحقة.  
- الحالات الخاصة الشائعة—ماذا تفعل عندما يخلط المستند بين الصور والمعادلات، أو عندما تحتاج إلى الحفاظ على أحرف Unicode.  
- عينة كود كاملة جاهزة للتنفيذ يمكنك وضعها في تطبيق Console.

### المتطلبات المسبقة

- .NET 6.0 أو أحدث (الكود يعمل أيضًا مع .NET Framework 4.7+).  
- نسخة مرخصة من **Aspose.Words for .NET** (الإصدار التجريبي المجاني يكفي للاختبار).  
- Visual Studio 2022 أو أي بيئة تطوير تدعم تجميع مشاريع C#.  
- مستند Word (`input.docx`) يحتوي بالفعل على بعض كائنات Office Math.

> **نصيحة احترافية:** إذا لم تكن لديك رخصة بعد، يمكنك طلب مفتاح مؤقت من موقع Aspose—فقط استبدل العنصر النائب في الكود بمفتاحك قبل التشغيل.

## الخطوة 1 – تثبيت Aspose.Words عبر NuGet

أولًا: تحتاج إلى إضافة المكتبة إلى مشروعك. افتح **Package Manager Console** وشغّل الأمر التالي:

```powershell
Install-Package Aspose.Words
```

هذا السطر الواحد يجلب لك كل ما تحتاجه، بما في ذلك مساحة الاسم `Saving` التي توجد فيها `TxtSaveOptions`. لا ملفات DLL إضافية، ولا تبعيات أصلية—فقط كود مُدار بالكامل.

## الخطوة 2 – تحميل مستند Word المصدر

الآن نقرأ فعليًا الملف الذي يحتوي على المعادلات. فئة `Document` تمثل بنية *.docx* بالكامل، لذا يمكنك التعامل معها ككائن عالي المستوى.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;

// If you have a license file, load it here
// var license = new License();
// license.SetLicense("Aspose.Words.lic");

// Step 2: Load the source Word document that contains equations
Document document = new Document(@"C:\MyProjects\Docs\input.docx");

// Quick sanity check – make sure the document actually has Office Math
if (document.GetChildNodes(NodeType.OfficeMath, true).Count == 0)
{
    Console.WriteLine("Warning: No equations found. The output will be plain text only.");
}
```

**لماذا هذا مهم:** تحميل المستند مبكرًا يتيح لك فحص شجرة العقد. إذا تخطيت الفحص وكان الملف لا يحتوي على معادلات، ستحصل على ملف txt نظيف—but لن تعرف لماذا يكون إخراج LaTeX فارغًا.

## الخطوة 3 – تكوين TxtSaveOptions لتصدير LaTeX

توفر Aspose تحكمًا دقيقًا في طريقة تصيير Office Math. عبر ضبط `OfficeMathExportMode` إلى `LaTeX`، تتحول كل معادلة إلى ما يعادلها في LaTeX بدلاً من إزالتها أو تحويلها إلى صورة.

```csharp
// Step 3: Create text save options and set Office Math export mode to LaTeX
TxtSaveOptions txtSaveOptions = new TxtSaveOptions
{
    // This tells Aspose to emit LaTeX markup for each equation
    OfficeMathExportMode = OfficeMathExportMode.LaTeX,

    // Optional: preserve Unicode characters (useful for symbols like α, β, etc.)
    Encoding = Encoding.UTF8,

    // Optional: add a line break after each paragraph for readability
    AddBidiMarks = false
};
```

**لماذا هذا مهم:** وضع التصدير الافتراضي سيحذف المعادلات تمامًا. التحويل إلى `LaTeX` يحافظ على النية الرياضية، وهو ما تحتاجه عندما تُدخل الملف لاحقًا إلى مُترجم LaTeX أو معالج markdown يدعم صيغة `$…$`.

## الخطوة 4 – حفظ المستند كنص عادي

مع ضبط الخيارات، يصبح حفظ الملف سطرًا واحدًا. سيُنتج ملف `.txt` حيث تظهر كل معادلة ككود LaTeX محاط بحدود `$` (يمكنك تعديل ذلك لاحقًا إذا فضلت كتل `\[` … `\]`).

```csharp
// Step 4: Save the document as a plain‑text file; equations are exported as LaTeX markup
string outputPath = @"C:\MyProjects\Docs\output.txt";
document.Save(outputPath, txtSaveOptions);

Console.WriteLine($"Success! The file has been saved to {outputPath}");
```

### النتيجة المتوقعة

افتح `output.txt` في أي محرر وسترى شيئًا مشابهًا لـ:

```
This is a sample paragraph with an equation.

$E = mc^2$

Another paragraph follows the equation.

$ \int_{0}^{\infty} e^{-x^2} dx = \frac{\sqrt{\pi}}{2} $
```

لاحظ كيف يبقى النص العادي كما هو، بينما تتحول المعادلات إلى سلاسل LaTeX صافية. يمكنك نسخها ولصقها مباشرةً في مستند LaTeX، أو دفتر Jupyter، أو أي أداة تُظهر الرياضيات.

## الخطوة 5 – التعامل مع الحالات الخاصة

### محتوى مختلط (صور + معادلات)

إذا كان ملف Word يحتوي أيضًا على صور، سيتجاهلها Aspose عند استخدام `TxtSaveOptions`. هذا عادةً يكفي لسير عمل **save word plain text**، لكن إذا احتجت الصور كعناصر نائبة يمكنك:

1. تصدير المستند إلى HTML أولًا (`HtmlSaveOptions`) لالتقاط الصور كوسوم `<img>`.  
2. تشغيل تمريرة ثانية باستخدام `TxtSaveOptions` للحصول على معادلات LaTeX.  
3. دمج النتيجتين يدويًا أو عبر سكربت صغير.

### رموز Unicode

بعض المعادلات تستخدم أحرف Unicode خاصة (مثل الحروف اليونانية). ضبط `Encoding = Encoding.UTF8` في `TxtSaveOptions` (كما هو موضح في الخطوة 3) يضمن بقاء هذه الرموز بعد التحويل.

### مستندات ضخمة

للملفات الكبيرة (> 100 MB)، فكر في تنفيذ عملية الحفظ بطريقة تدفقية:

```csharp
using (FileStream fs = new FileStream(outputPath, FileMode.Create, FileAccess.Write))
{
    document.Save(fs, txtSaveOptions);
}
```

التدفق يتجنب تحميل الإخراج بالكامل في الذاكرة، وهو ما قد ينقذك على عوامل بناء ذات ذاكرة محدودة.

## مثال عملي كامل

فيما يلي البرنامج الكامل الجاهز للنسخ واللصق الذي يجمع كل الخطوات. ما عليك سوى تعديل مسارات الملفات، وإذا كان لديك رخصة فأضف سطر الترخيص.

```csharp
using System;
using System.Text;
using Aspose.Words;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // -------------------------------------------------
        // OPTIONAL: Load your Aspose.Words license here
        // -------------------------------------------------
        // var license = new License();
        // license.SetLicense("Aspose.Words.lic");

        // -------------------------------------------------
        // Step 1: Load the source document
        // -------------------------------------------------
        string inputPath = @"C:\MyProjects\Docs\input.docx";
        Document doc = new Document(inputPath);

        // -------------------------------------------------
        // Step 2: Verify that the document contains equations
        // -------------------------------------------------
        int equationCount = doc.GetChildNodes(NodeType.OfficeMath, true).Count;
        if (equationCount == 0)
        {
            Console.WriteLine("No Office Math found – the output will be plain text only.");
        }

        // -------------------------------------------------
        // Step 3: Configure TxtSaveOptions for LaTeX export
        // -------------------------------------------------
        TxtSaveOptions options = new TxtSaveOptions
        {
            OfficeMathExportMode = OfficeMathExportMode.LaTeX,
            Encoding = Encoding.UTF8,
            AddBidiMarks = false
        };

        // -------------------------------------------------
        // Step 4: Save as .txt (plain text + LaTeX equations)
        // -------------------------------------------------
        string outputPath = @"C:\MyProjects\Docs\output.txt";
        doc.Save(outputPath, options);

        Console.WriteLine($"File saved successfully to: {outputPath}");
    }
}
```

شغّل البرنامج (`dotnet run` إذا كنت تستخدم مشروع Console) وتفقد `output.txt`. لقد قمت الآن **بحفظ ملف docx كـ txt** مع الحفاظ على كل معادلة كـ LaTeX—دون الحاجة إلى نسخ يدوي.

## الأسئلة المتكررة

**س: هل يمكنني تغيير الفاصل من `$…$` إلى `\(...\)`؟**  
ج: نعم. بعد الحفظ، نفّذ استبدالًا بسيطًا على الملف: `output = output.Replace("$", @"\(").Replace("$", @"\)");`—احرص فقط على عدم استبدال علامات `$` الأصلية التي قد تكون جزءًا من النص.

**س: هل يعمل هذا مع ملفات Word من 2007‑2019؟**  
ج: بالتأكيد. يدعم Aspose.Words الصيغ `.doc`، `.docx`، `.docm`، وحتى عائلة `.dotx` الأحدث. الكود نفسه يعمل على جميع الإصدارات.

**س: ماذا لو أردت الحفاظ على تنسيق الفقرات الأصلي (علامات التبويب، المسافات المتعددة)؟**  
ج: اضبط `txtSaveOptions.PreserveTableLayout = true;` و `txtSaveOptions.PreserveSpace = true;` للحفاظ على الفراغات كما هي.

## الخلاصة

غطّينا كل ما تحتاجه **لحفظ ملف docx كـ txt** مع **تصدير المعادلات إلى LaTeX** باستخدام Aspose.Words. الخطوات الأساسية هي تحميل المستند، ضبط `TxtSaveOptions` بـ `OfficeMathExportMode.LaTeX`، ثم حفظ النتيجة. بهذه الثلاثة أسطر من الكود يمكنك بثقة **تحويل Word إلى LaTeX**، والحفاظ على مستندك كـ **save word plain text**، وتفادي فقدان الرموز الرياضية.

هل أنت مستعد للتحدي التالي؟ جرّب ربط هذه العملية بمولد markdown لإنشاء ملف `.md` كامل يتضمن النص وLaTeX—مثالي لتوثيق مدعوم بـ Git أو مولّدات مواقع ثابتة. أو استكشف `PdfSaveOptions` من Aspose للحصول على نسخة PDF إلى جانب الملف النصي.

إذا واجهتك أي صعوبات، اترك تعليقًا أدناه. برمجة سعيدة، واستمتع ببساطة تحويل معادلات Word إلى LaTeX نظيف! 

![Illustration of saving a DOCX as TXT with LaTeX equations](placeholder-image.png "save docx as txt example")

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}