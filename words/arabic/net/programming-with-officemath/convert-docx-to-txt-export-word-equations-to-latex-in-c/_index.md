---
category: general
date: 2026-04-28
description: تحويل DOCX إلى TXT وتصدير معادلات Word إلى LaTeX باستخدام Aspose.Words.
  تعلّم كيفية حفظ Word كملف TXT ومعالجة كائنات الرياضيات في بضع خطوات.
draft: false
keywords:
- convert docx to txt
- convert word equations to latex
- convert word to plain text
- save word as txt
- export equations as latex
language: ar
og_description: حوّل ملفات DOCX إلى TXT وصدر معادلات Word إلى LaTeX باستخدام مقتطف
  C# بسيط. دليل كامل، كود، ونصائح.
og_title: تحويل DOCX إلى TXT – تصدير معادلات Word إلى LaTeX
tags:
- C#
- Aspose.Words
- Document Conversion
title: تحويل DOCX إلى TXT – تصدير معادلات Word إلى LaTeX في C#
url: /ar/net/programming-with-officemath/convert-docx-to-txt-export-word-equations-to-latex-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# تحويل DOCX إلى TXT – تصدير معادلات Word إلى LaTeX

هل احتجت يومًا إلى **convert docx to txt** لكنك كنت قلقًا من أن تتحول المعادلات في ملف Word إلى فوضى غير مقروءة؟ لست وحدك. في العديد من المشاريع الهندسية أو الأكاديمية، المستند الأصلي يكون بامتداد .docx، بينما الأدوات اللاحقة لا تفهم إلا النص العادي أو LaTeX. الخبر السار؟ باستخدام بضع أسطر من C# و Aspose.Words يمكنك **convert docx to txt** *و* الحفاظ على كل معادلة ككود LaTeX نظيف.

في هذا الدرس سنستعرض العملية بالكامل: تحميل ملف .docx، ضبط خيارات الحفظ بحيث تتحول كائنات Office Math إلى LaTeX، وأخيرًا كتابة النتيجة إلى ملف .txt. بنهاية الدرس ستعرف كيف **save word as txt**، **convert word to plain text**، و **export equations as latex** دون الحاجة للبحث في وثائق الـ API.

## ما ستتعلمه

- الاستدعاءات الدقيقة للـ API اللازمة لـ **convert docx to txt** مع الحفاظ على المعادلات.
- لماذا اختيار `OfficeMathExportMode.LaTeX` هو الطريقة الموصى بها لـ **convert word equations to latex**.
- كيفية التعامل مع الحالات الطرفية الشائعة مثل الخطوط المفقودة أو ميزات المعادلات غير المدعومة.
- برنامج C# كامل جاهز للتنفيذ يمكنك إدراجه في أي مشروع .NET.

### المتطلبات المسبقة

- .NET 6.0 أو أحدث (الكود يعمل أيضًا على .NET Framework 4.7+).
- ترخيص لـ Aspose.Words for .NET (الإصدار التجريبي المجاني يكفي للتقييم).
- مستند Word (`input.docx`) يحتوي على كائن Office Math واحد على الأقل.

إذا كان لديك هذه المتطلبات، هيا نبدأ.

## الخطوة 1: تثبيت Aspose.Words

قبل تشغيل أي كود تحتاج إلى المكتبة. افتح الطرفية في مجلد مشروعك ونفّذ:

```bash
dotnet add package Aspose.Words
```

## الخطوة 2: تحميل المستند المصدر

أول شيء نقوم به هو قراءة ملف .docx إلى كائن `Document`. هذا الكائن يمنحنا وصولًا كاملًا إلى بنية الملف، بما في ذلك مقاطع النص، الصور، وكائنات الرياضيات.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // Step 2: Load the source document
        Document doc = new Document(@"YOUR_DIRECTORY\input.docx");
```

> **لماذا هذا مهم:** تحميل المستند ينشئ تمثيلًا في الذاكرة، بحيث يمكننا لاحقًا تعديل طريقة كتابة كل عنصر. إذا لم يُعثر على الملف، ستطرح Aspose استثناء `FileNotFoundException`، وقد ترغب في التقاطه في كود الإنتاج.

## الخطوة 3: ضبط خيارات حفظ TXT للرياضيات بصيغة LaTeX

افتراضيًا، `Document.Save` يكتب نصًا عاديًا و**يتجاهل** أي Office Math. للحفاظ على تلك المعادلات، نضبط `OfficeMathExportMode` إلى `LaTeX`. هذا يخبر المُصدّر بترجمة كل معادلة إلى ما يعادلها في LaTeX.

```csharp
        // Step 3: Configure TXT save options to export Office Math as LaTeX
        TxtSaveOptions txtOptions = new TxtSaveOptions
        {
            OfficeMathExportMode = OfficeMathExportMode.LaTeX,
            // Optional: preserve line breaks as they appear in the original Word file
            PreserveTableLayout = true
        };
```

> **نصيحة احترافية:** إذا كنت تحتاج فقط إلى الأحرف Unicode الخام للمعادلة (مثلاً لعرض سريع)، يمكنك استخدام `OfficeMathExportMode.Text`. لكن لمعظم خطوط الأنابيب العلمية، يعتبر `LaTeX` المعيار الذهبي لأنه مفهوم عالميًا من قبل معالجات LaTeX.

## الخطوة 4: حفظ المستند كنص عادي

الآن نكتب المحتوى المُحوّل إلى ملف `.txt`. سيحتوي الملف على فقرات عادية، نقاط تعداد، وبفضل الخطوة السابقة—مقتطفات LaTeX لكل معادلة.

```csharp
        // Step 4: Save the document as plain‑text using the configured options
        doc.Save(@"YOUR_DIRECTORY\Math.txt", txtOptions);
    }
}
```

عند فتح `Math.txt` ستظهر لك شيء مشابه لـ:

```
In this report we derive the quadratic formula:
\[
x = \frac{-b \pm \sqrt{b^{2} - 4ac}}{2a}
\]

The end.
```

هل لاحظت delimiters `\[` … `\]`؟ هذه هي كتل الرياضيات في LaTeX التي تم توليدها تلقائيًا.

## الخطوة 5: التحقق من الناتج (اختياري لكن موصى به)

من السهل أن تغفل عن مشكلة تحويل دقيقة، خاصةً عندما تحتوي المعادلات على رموز مخصصة. فحص سريع هو تمرير ملف `.txt` المُولد إلى مُصرّف LaTeX (مثل `pdflatex`) ورؤية ما إذا كان يُترجم بدون أخطاء.

```bash
pdflatex -interaction=nonstopmode Math.txt
```

إذا نجح التجميع، فقد نجحت فعليًا في **convert word equations to latex** و **convert docx to txt** في خطوة واحدة. إذا واجهت أخطاء، ابحث عن رسائل حول أوامر غير معرفة—هذه عادةً ما تشير إلى ميزة معادلة لا يمكن لـ Aspose.Words ترجمتها (مثل بعض صيغ المصفوفات). في مثل هذه الحالات، يمكنك الرجوع إلى `OfficeMathExportMode.MathML` ثم تحويل MathML إلى LaTeX بأداة أخرى.

## المشكلات الشائعة وكيفية تجنبها

| المشكلة | لماذا يحدث | الحل |
|-------|----------------|-----|
| الخطوط المفقودة | Aspose.Words يحتاج الخط لتصوير الرموز بشكل صحيح. | ثبّت الخط المفقود على الجهاز أو أدمجه في ملف .docx. |
| عدم تصدير المعادلات المعقدة | بعض ميزات Office Math الحديثة لم تُطابق بعد إلى LaTeX. | استخدم `OfficeMathExportMode.MathML` ثم حوّل باستخدام مكتبة MathML‑to‑LaTeX. |
| سطور فارغة إضافية | حافظة النص العادي تحتفظ بفواصل الفقرات، مما قد يضيف مسافات بيضاء. | اضبط `txtOptions.AddBidiMarks = false` أو عالج الملف ببرنامج بسيط. |

## مثال كامل جاهز للتنفيذ (نسخ‑لصق)

فيما يلي البرنامج الكامل، جاهز للترجمة. استبدل `YOUR_DIRECTORY` بالمجلد الذي يحتوي على `input.docx`.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;

namespace DocxToTxtWithLatex
{
    class Program
    {
        static void Main()
        {
            try
            {
                // Load the source document
                Document doc = new Document(@"C:\Docs\input.docx");

                // Configure save options: export equations as LaTeX
                TxtSaveOptions txtOptions = new TxtSaveOptions
                {
                    OfficeMathExportMode = OfficeMathExportMode.LaTeX,
                    PreserveTableLayout = true,
                    AddBidiMarks = false
                };

                // Save as plain‑text
                string outputPath = @"C:\Docs\Math.txt";
                doc.Save(outputPath, txtOptions);

                Console.WriteLine($"Successfully converted DOCX to TXT. Output at: {outputPath}");
            }
            catch (Exception ex)
            {
                Console.Error.WriteLine($"Conversion failed: {ex.Message}");
            }
        }
    }
}
```

تشغيل هذا البرنامج سيقوم **save word as txt** مع تحويل كل كتلة Office Math إلى LaTeX، مما يمنحك ملف نص عادي نظيف وقابل للبحث.

## الخطوات التالية والمواضيع ذات الصلة

- **تحويل دفعي:** غلف المنطق أعلاه داخل حلقة `foreach` لمعالجة مجلد كامل من ملفات .docx.
- **دمج مع توليد PDF:** بعد الحصول على مقتطفات LaTeX، مررها إلى خط أنابيب PDF (مثل `PdfSharp` + `MiKTeX`) لإنتاج تقارير PDF.
- **تصدير المعادلات كـ latex** لتنسيقات أخرى: يدعم Aspose.Words أيضًا `SaveFormat.Markdown`، الذي يمكنه تضمين LaTeX تلقائيًا.
- **تحسين الأداء:** للمستندات الضخمة، أعد استخدام نفس كائن `TxtSaveOptions` وعطّل الميزات غير الضرورية مثل `AddBidiMarks`.

---

### مثال صورة (اختياري)

إذا كنت تفضّل إشارة بصرية، إليك لقطة شاشة لملف الإخراج في Notepad++.  

![مخرجات تحويل docx إلى txt تظهر معادلات LaTeX](convert-docx-to-txt-output.png)

*(نص بديل: “convert docx to txt output showing LaTeX equations” – يفي بمتطلبات الكلمة المفتاحية الأساسية.)*

## الخلاصة

لقد عرضنا طريقة موثوقة لـ **convert docx to txt** مع الحفاظ على كل معادلة كـ LaTeX نظيف. المفتاح هو علم `OfficeMathExportMode.LaTeX`، الذي يحول تنسيق الرياضيات الخاص بـ Word إلى شيء يفهمه أي محرك LaTeX. باستخدام عينة الكود الكاملة أعلاه يمكنك **save word as txt**، **convert word to plain text**، و **export equations as latex** في تشغيل واحد متكامل.

لا تتردد في التجربة—غيّر امتداد الإخراج إلى `.md` للـ Markdown، أو دمج المقتطف في خط أنابيب معالجة مستندات أكبر. إذا صادفت أي شذوذ، اترك تعليقًا أدناه؛ سأكون سعيدًا بالمساعدة في حل المشكلات.

برمجة سعيدة!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}