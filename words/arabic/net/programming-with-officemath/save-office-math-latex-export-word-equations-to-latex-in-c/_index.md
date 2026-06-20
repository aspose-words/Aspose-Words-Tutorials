---
category: general
date: 2026-04-21
description: احفظ معادلات الرياضيات في أوفيس بصيغة LaTeX بسرعة باستخدام Aspose.Words
  – وتعلم أيضًا كيفية حفظ نص Word العادي وتصدير معادلات Word بصيغة LaTeX في خطوة واحدة.
draft: false
keywords:
- save office math latex
- save word plain text
- export word equations latex
- convert word math latex
- convert word equations mathml
language: ar
og_description: احفظ رياضيات أوفيس لايتكس فورًا؛ تعلم تصدير معادلات وورد لايتكس وتحويل
  رياضيات وورد لايتكس باستخدام Aspose.Words في C#.
og_title: حفظ Office Math LaTeX – تصدير معادلات Word إلى LaTeX
tags:
- Aspose.Words
- C#
- LaTeX
title: حفظ Office Math LaTeX – تصدير معادلات Word إلى LaTeX في C#
url: /ar/net/programming-with-officemath/save-office-math-latex-export-word-equations-to-latex-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# save office math latex – تصدير معادلات Word إلى LaTeX باستخدام Aspose.Words

هل احتجت يومًا إلى **save office math latex** من ملف `.docx` لكن لم تكن متأكدًا من أين تبدأ؟ لست وحدك، والخبر السار هو أن الحل بسيط إلى حد كبير. في هذا الدليل سنستعرض الخطوات الدقيقة لتصدير معادلات Word بصيغة latex (وحتى MathML) باستخدام Aspose.Words لـ .NET، مع إظهار كيفية **save word plain text** جنبًا إلى جنب مع الرياضيات.

سنتناول كل ما قد تتساءل عنه: لماذا قد تختار LaTeX على غيره من الصيغ، كيفية تكوين `TxtSaveOptions`، وما يجب فعله إذا احتجت إلى **convert word math latex** إلى تمثيل آخر. في النهاية ستحصل على مقتطف قابل للتنفيذ يأخذ مستند Word يحتوي على كائنات Office Math وينتج ملف `.txt` نظيف يحتوي على معادلات LaTeX (أو MathML). لا أدوات خارجية، لا نسخ يدوي—فقط كود C# نظيف يمكنك إدراجه في أي مشروع.

## المتطلبات المسبقة

- **Aspose.Words for .NET** (v23.10 أو أحدث). حزمة NuGet هي `Aspose.Words`.
- بيئة تطوير .NET (Visual Studio، Rider، أو VS Code مع امتداد C#).
- ملف Word (`.docx`) يحتوي على معادلة واحدة على الأقل تم إنشاؤها باستخدام محرر Office Math.
- إلمام أساسي بصياغة C#—لا شيء معقد، فقط عبارات `using` المعتادة.

إذا كنت قد تحققت من هذه المتطلبات، رائع—لنبدأ.

## الخطوة 1 – إعداد خيارات **save office math latex**

أول شيء تحتاج إلى فعله هو إخبار Aspose.Words كيف تريد عرض المحتوى الرياضي. تحتوي فئة `TxtSaveOptions` على خاصية `OfficeMathExportMode` التي تقبل ثلاث قيم: `LaTeX`، `MathML`، أو `Text`. لهدفنا الأساسي سنختار `LaTeX`.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;

// Configure TXT save options to export equations as LaTeX
TxtSaveOptions txtOptions = new TxtSaveOptions
{
    // This line makes the library output LaTeX for every Office Math object
    OfficeMathExportMode = OfficeMathExportMode.LaTeX
    // You could also use OfficeMathExportMode.MathML or .Text here
};
```

**لماذا هذا مهم:** عندما تضبط `OfficeMathExportMode` إلى `LaTeX`، يتم تحويل كل معادلة إلى مصدر LaTeX الأصلي. يمكن تجميع هذا المصدر لاحقًا بأي محرك LaTeX، مما يمنحك تنسيقًا مثاليًا دون الحاجة إلى إعادة كتابة الصيغ.

> **نصيحة احترافية:** إذا احتجت يومًا إلى **convert word equations mathml**، فقط غير قيمة التعداد إلى `OfficeMathExportMode.MathML`. باقي الكود يبقى كما هو.

## الخطوة 2 – تحميل مستند Word (سيناريو **save word plain text**)

بعد ذلك، نقوم بتحميل ملف `.docx` المصدر. هذه الخطوة متماثلة سواء كنت مهتمًا فقط باستخراج النص العادي أو تريد أيضًا المعادلات بصيغة LaTeX.

```csharp
// Load the document that contains Office Math objects
Document doc = new Document(@"C:\MyDocs\input.docx");

// Optional: verify that the document actually has equations
bool hasMath = doc.GetChildNodes(NodeType.OfficeMath, true).Count > 0;
if (!hasMath)
{
    Console.WriteLine("Warning: No Office Math objects found in the document.");
}
```

**ما الذي يحدث هنا؟** يقوم مُنشئ `Document` بقراءة الملف إلى الذاكرة. الفحص السريع باستخدام `GetChildNodes` يساعدك على اكتشاف حالة شائعة—محاولة تصدير LaTeX من ملف لا يحتوي على معادلات. إنها حماية صغيرة توفر عليك مخرجات فارغة محيرة لاحقًا.

## الخطوة 3 – **save office math latex** إلى ملف نصي عادي

الآن نكتب الملف أخيرًا. طريقة `Save` تحترم `TxtSaveOptions` التي قمنا بتكوينها سابقًا، لذا سيحتوي ملف `.txt` الناتج على كل من النص العادي ومقاطع LaTeX لكل معادلة.

```csharp
// Define the output path
string outputPath = @"C:\MyDocs\Equations.txt";

// Save the document as plain text, with LaTeX equations embedded
doc.Save(outputPath, txtOptions);

Console.WriteLine($"Document saved successfully to {outputPath}");
```

عند فتح `Equations.txt` سترى شيئًا مثل:

```
This is a sample paragraph.

\begin{equation}
E = mc^2
\end{equation}

Another paragraph follows.
```

يتم تغليف كتل LaTeX تلقائيًا بـ `\begin{equation}` … `\end{equation}`، مما يجعلها جاهزة للإدراج في أي مستند LaTeX.

## الخطوة 4 – بديل: **convert word equations mathml** بدلاً من LaTeX

إذا كانت سلسلة الأدوات اللاحقة تفضل MathML (مثلاً، صفحة ويب تعرض المعادلات باستخدام MathJax)، فقط غيّر وضع التصدير إلى:

```csharp
txtOptions.OfficeMathExportMode = OfficeMathExportMode.MathML;
doc.Save(@"C:\MyDocs\EquationsMathML.txt", txtOptions);
```

سيحتوي الناتج الآن على وسوم MathML على نمط XML، مثل:

```xml
<math xmlns="http://www.w3.org/1998/Math/MathML">
  <mi>E</mi>
  <mo>=</mo>
  <mi>m</mi>
  <msup><mi>c</mi><mn>2</mn></msup>
</math>
```

هذه هي الطريقة السريعة لـ **convert word equations mathml** دون كتابة محلل مخصص.

## الخطوة 5 – إضافي: **save word plain text** مع إبقاء المعادلات منفصلة

أحيانًا تريد نسخة نصية نظيفة من المستند *بدون* أي LaTeX أو MathML مدمجة. يمكنك تحقيق ذلك بتغيير وضع التصدير إلى `Text` وتشغيل عملية حفظ ثانية:

```csharp
// Export pure plain text (no math markup)
txtOptions.OfficeMathExportMode = OfficeMathExportMode.Text;
doc.Save(@"C:\MyDocs\PlainDocument.txt", txtOptions);
```

الآن لديك ثلاثة ملفات جنبًا إلى جنب:

| File                         | المحتوى                                 |
|------------------------------|----------------------------------------|
| `Equations.txt`              | نص عادي **+** معادلات LaTeX            |
| `EquationsMathML.txt`        | نص عادي **+** معادلات MathML           |
| `PlainDocument.txt`          | نص صافي، تم إزالة المعادلات            |

هذا النمط مفيد عندما تحتاج إلى إدخال النص العادي في فهرس بحث مع الحفاظ على الرياضيات الأصلية للنشر الأكاديمي.

## مثال كامل يعمل (جاهز للنسخ واللصق)

فيما يلي البرنامج الكامل الذي يمكنك تجميعه وتشغيله كما هو. يوضح **save office math latex**، **export word equations latex**، **convert word math latex**، و **save word plain text**—كل ذلك في سكريبت منظم واحد.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // 1️⃣ Configure TXT save options for LaTeX export
        TxtSaveOptions txtOptions = new TxtSaveOptions
        {
            OfficeMathExportMode = OfficeMathExportMode.LaTeX
        };

        // 2️⃣ Load the source Word document
        string inputPath = @"C:\MyDocs\input.docx";
        Document doc = new Document(inputPath);

        // Quick sanity check for equations
        if (doc.GetChildNodes(NodeType.OfficeMath, true).Count == 0)
        {
            Console.WriteLine("No equations found – proceeding with plain‑text export only.");
        }

        // 3️⃣ Save with LaTeX equations embedded
        string latexPath = @"C:\MyDocs\Equations.txt";
        doc.Save(latexPath, txtOptions);
        Console.WriteLine($"LaTeX export saved to {latexPath}");

        // 4️⃣ Switch to MathML and save (optional)
        txtOptions.OfficeMathExportMode = OfficeMathExportMode.MathML;
        string mathmlPath = @"C:\MyDocs\EquationsMathML.txt";
        doc.Save(mathmlPath, txtOptions);
        Console.WriteLine($"MathML export saved to {mathmlPath}");

        // 5️⃣ Finally, pure plain‑text export (no math markup)
        txtOptions.OfficeMathExportMode = OfficeMathExportMode.Text;
        string plainPath = @"C:\MyDocs\PlainDocument.txt";
        doc.Save(plainPath, txtOptions);
        Console.WriteLine($"Plain‑text export saved to {plainPath}");
    }
}
```

**النتيجة المتوقعة:** بعد التشغيل، ستجد ثلاثة ملفات نصية في `C:\MyDocs`. افتح `Equations.txt` وسترى كتل LaTeX؛ `EquationsMathML.txt` سيحتوي على MathML؛ `PlainDocument.txt` سيكون خاليًا من أي علامات معادلات.

## أسئلة شائعة وحالات حدية

- **ماذا لو كنت أحتاج فقط إلى LaTeX لمجموعة فرعية من المعادلات؟**  
  استخدم API عقدة `OfficeMath` للتكرار على كل معادلة، صدّرها يدويًا باستخدام `MathConverter`، واستبدل نص العنصر النائب حيث تريد. هذه الطريقة تمنحك تحكمًا دقيقًا لكن تضيف بضع أسطر إضافية من الكود.

- **هل يعمل هذا مع .NET Core / .NET 5+؟**  
  بالتأكيد. Aspose.Words متعدد المنصات، لذا يعمل نفس الكود على Windows وLinux وmacOS طالما أن نسخة runtime تتطابق مع متطلبات المكتبة.

- **هل يمكنني تغيير غلاف LaTeX (`\begin{equation}`) إلى شيء آخر؟**  
  نعم. اضبط `txtOptions.OfficeMathExportMode = OfficeMathExportMode.LaTeX` ثم عدل `txtOptions.MathExportSettings` (متاح في الإصدارات الأحدث) لتخصيص الفواصل.

- **هل هناك مخاوف بشأن الأداء مع المستندات الضخمة؟**  
  تقوم المكتبة ببث الإخراج، لذا يبقى استهلاك الذاكرة معتدلًا. ومع ذلك

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}