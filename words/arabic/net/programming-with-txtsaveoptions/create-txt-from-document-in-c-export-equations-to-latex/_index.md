---
category: general
date: 2026-06-02
description: إنشاء ملف txt من مستند في C# وحفظ نص Word العادي مع تصدير المعادلات بصيغة LaTeX باستخدام Aspose.Words –
  دليل خطوة بخطوة.
draft: false
keywords:
- create txt from document
- save word plain text
- export equations latex
language: ar
og_description: إنشاء ملف txt من مستند في C# وحفظ النص العادي للـ Word مع تصدير المعادلات
  بصيغة LaTeX باستخدام Aspose.Words – دليل كامل.
og_title: إنشاء ملف txt من مستند في C# – تصدير المعادلات إلى LaTeX
schemas:
- author: Aspose
  dateModified: '2026-06-02'
  description: Create txt from document in C# and save Word plain text while export
    equations latex using Aspose.Words – step‑by‑step guide.
  headline: Create txt from document in C# – Export equations to LaTeX
  type: TechArticle
- description: Create txt from document in C# and save Word plain text while export
    equations latex using Aspose.Words – step‑by‑step guide.
  name: Create txt from document in C# – Export equations to LaTeX
  steps:
  - name: What if I need **save word plain text** without any LaTeX conversion?
    text: Simply omit the `OfficeMathExportMode` line or set it to `OfficeMathExportMode.Text`.
      The equations will be rendered as plain Unicode characters (e.g., “x = (‑b ±
      √(b²‑4ac)) / 2a”).
  - name: Can I export to other formats (Markdown, HTML) while keeping LaTeX?
    text: Yes. Aspose.Words also supports `MarkdownSaveOptions` and `HtmlSaveOptions`
      with similar `OfficeMathExportMode` settings. Switch the options class, keep
      the `OfficeMathExportMode = OfficeMathExportMode.LaTeX`, and you’ll get LaTeX
      embedded in the target markup.
  - name: How do I handle large documents (hundreds of MB)?
    text: 'Use `LoadOptions` with `LoadFormat.Auto` and consider streaming the output:'
  type: HowTo
tags:
- Aspose.Words
- C#
- LaTeX
title: إنشاء ملف txt من مستند في C# – تصدير المعادلات إلى LaTeX
url: /ar/net/programming-with-txtsaveoptions/create-txt-from-document-in-c-export-equations-to-latex/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# إنشاء txt من مستند في C# – تصدير المعادلات إلى LaTeX

هل تساءلت يوماً كيف **إنشاء txt من مستند** دون فقدان الرياضيات التي قضيت ساعات في كتابتها؟ لست وحدك. في العديد من خطوط تقارير البيانات تحتاج إلى نسخة نصية عادية من ملف Word، ومع ذلك تريد أن تُظهر المعادلات بصيغة LaTeX حتى تتمكن الأدوات اللاحقة من معالجتها.  

في هذا الدرس سنستعرض الخطوات الدقيقة **لحفظ نص Word** مع **تصدير المعادلات إلى LaTeX** باستخدام مكتبة Aspose.Words القوية لـ .NET. في النهاية ستحصل على مقتطف جاهز للتنفيذ يمكنك وضعه في أي مشروع C#.

## ما ستتعلمه

- تثبيت وإضافة مرجع Aspose.Words إلى مشروع .NET.  
- تحميل ملف `.docx` يحتوي على كائنات OfficeMath.  
- ضبط `TxtSaveOptions` بحيث يُصدر LaTeX لكل معادلة.  
- كتابة ملف النص الناتج إلى القرص.  
- التحقق من ظهور المعادلات على شكل ترميز LaTeX داخل ملف `.txt`.

لا تحتاج إلى خبرة سابقة في Aspose؛ فقط إلمام أساسي بـ C# و Visual Studio يكفي.

---

## المتطلبات المسبقة

| المتطلب | لماذا هو مهم |
|-------------|----------------|
| .NET 6.0 أو أحدث | ميزات لغة حديثة وأداء أفضل |
| Visual Studio 2022 (أو VS Code) | تصحيح أخطاء سهل وإنشاء مشروع سريع |
| Aspose.Words for .NET (NuGet) | المكتبة التي تتعامل مع تحويل OfficeMath → LaTeX |
| مستند Word يحتوي على معادلات | لرؤية تصدير LaTeX عملياً |

إذا كان أي من هذه غير متوفر، توقف الآن وقم بتثبيته—وإلا لن يتم تجميع الكود.

---

## الخطوة 1 – تثبيت Aspose.Words عبر NuGet

للبدء، افتح الحل (solution)، انقر بزر الماوس الأيمن على المشروع، واختر **Manage NuGet Packages**. ابحث عن **Aspose.Words** واضغط **Install**.  

أو، إذا كنت تفضّل سطر الأوامر، نفّذ:

```powershell
dotnet add package Aspose.Words
```

> **نصيحة احترافية:** استخدم أحدث نسخة مستقرة؛ حتى يونيو 2026 الإصدار هو **23.9.0**. هذا يضمن حصولك على أحدث تحسينات تصدير OfficeMath.

---

## الخطوة 2 – تحميل مستند Word المصدر

الآن نحتاج إلى كائن `Document` يمثل ملف `.docx` الذي تريد تحويله. المقتطف التالي يفترض أن الملف موجود في مجلد يُدعى `Input`.

```csharp
using Aspose.Words;

// Load the Word file (change the path as needed)
Document doc = new Document(@"Input\sample_with_equations.docx");

// Quick sanity check – how many OfficeMath objects do we have?
int equationCount = doc.GetChildNodes(NodeType.OfficeMath, true).Count;
Console.WriteLine($"Found {equationCount} equation(s) to export.");
```

استدعاء `GetChildNodes` اختياري لكنه مفيد؛ فهو يُخبرك ما إذا كان المستند يحتوي فعلياً على معادلات قبل أن تضيع الوقت في التصدير.

---

## الخطوة 3 – ضبط TxtSaveOptions لت **تصدير المعادلات بصيغة LaTeX**

هذا هو جوهر العملية. `TxtSaveOptions` يتيح لك تعديل طريقة توليد النص العادي. ضبط `OfficeMathExportMode` إلى `LaTeX` يخبر Aspose أن يستبدل كل كائن OfficeMath بتمثيله بصيغة LaTeX.

```csharp
using Aspose.Words.Saving;

// Step 3: Configure TXT save options to export OfficeMath as LaTeX
TxtSaveOptions txtOptions = new TxtSaveOptions
{
    // This flag converts every equation into LaTeX syntax.
    OfficeMathExportMode = OfficeMathExportMode.LaTeX,

    // Optional: Preserve line breaks exactly as they appear in Word.
    PreserveTableLayout = true
};
```

لماذا نحتاج `PreserveTableLayout`؟ إذا كان مستندك يخلط المعادلات داخل الجداول، فإن هذه العلامة تحافظ على المحاذاة البصرية عندما تعرض ملف `.txt` لاحقاً. ليست إلزامية، لكن معظم التقارير الواقعية تستفيد منها.

---

## الخطوة 4 – **حفظ نص Word** باستخدام الخيارات المكوَّنة

مع إعداد الخيارات، عملية الحفظ تصبح سطرًا واحدًا. سنكتب الناتج إلى مجلد `Output`.

```csharp
// Step 4: Save the document as a plain‑text file using the configured options
string outputPath = @"Output\exported.txt";
doc.Save(outputPath, txtOptions);

Console.WriteLine($"Document saved as plain text at: {outputPath}");
```

عند فتح `exported.txt`، ستلاحظ فقرات عادية متداخلة مع مقاطع LaTeX مثل `\int_{0}^{\infty} e^{-x} dx`. يبقى باقي المحتوى دون تعديل، مما يمنحك تجربة **إنشاء txt من مستند** حقيقية.

---

## الخطوة 5 – التحقق من النتيجة (ونصيحة سريعة للتصحيح)

افتح الملف المُولَّد في أي محرر نصوص. يجب أن ترى شيئًا مشابهًا لـ:

```
This is a sample report.

The quadratic formula is given by:
\[
x = \frac{-b \pm \sqrt{b^2 - 4ac}}{2a}
\]

Another paragraph follows...
```

إذا كانت مقاطع LaTeX مفقودة، تحقق من أن المستند المصدر يحتوي فعليًا على كائنات `OfficeMath` وأنك أدرجت النسخة الصحيحة من Aspose. كذلك، تأكد أن خاصية `OfficeMathExportMode` لم تُستبدل في مكان آخر من الكود.

---

## أسئلة شائعة وحالات خاصة

### ماذا لو أردت **حفظ نص Word** دون أي تحويل إلى LaTeX؟

ما عليك سوى حذف سطر `OfficeMathExportMode` أو ضبطه إلى `OfficeMathExportMode.Text`. ستُعرض المعادلات كحروف Unicode عادية (مثال: “x = (‑b ± √(b²‑4ac)) / 2a”).

### هل يمكنني التصدير إلى صيغ أخرى (Markdown، HTML) مع الحفاظ على LaTeX؟

نعم. تدعم Aspose.Words أيضًا `MarkdownSaveOptions` و `HtmlSaveOptions` مع إعدادات `OfficeMathExportMode` المماثلة. استبدل فئة الخيارات، حافظ على `OfficeMathExportMode = OfficeMathExportMode.LaTeX`، وستحصل على LaTeX مدمج داخل الترميز المستهدف.

### كيف أتعامل مع مستندات ضخمة (مئات الـ MB)؟

استخدم `LoadOptions` مع `LoadFormat.Auto` وفكّر في تدفق (stream) الإخراج:

```csharp
using (FileStream fs = new FileStream(outputPath, FileMode.Create))
{
    doc.Save(fs, txtOptions);
}
```

التدفق يقلل من ضغط الذاكرة ويسرّع عملية **إنشاء txt من مستند**.

---

## مثال كامل جاهز للتنفيذ (انسخ‑الصق)

فيما يلي البرنامج الكامل الذي يمكنك تجميعه وتشغيله فورًا. يجمع جميع الخطوات السابقة في طريقة `Main` واحدة.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // 1️⃣ Load the source Word document
        string inputPath = @"Input\sample_with_equations.docx";
        Document doc = new Document(inputPath);

        // 2️⃣ Optional sanity check – count equations
        int eqCount = doc.GetChildNodes(NodeType.OfficeMath, true).Count;
        Console.WriteLine($"Found {eqCount} equation(s).");

        // 3️⃣ Configure TxtSaveOptions to export equations as LaTeX
        TxtSaveOptions txtOptions = new TxtSaveOptions
        {
            OfficeMathExportMode = OfficeMathExportMode.LaTeX,
            PreserveTableLayout = true
        };

        // 4️⃣ Save as plain‑text file
        string outputPath = @"Output\exported.txt";
        doc.Save(outputPath, txtOptions);

        Console.WriteLine($"✅ Finished! Plain‑text saved to: {outputPath}");
    }
}
```

**المخرجات المتوقعة على وحدة التحكم:**

```
Found 3 equation(s).
✅ Finished! Plain‑text saved to: Output\exported.txt
```

افتح `exported.txt` وسترى مقاطع LaTeX متداخلة مع النص العادي—تمامًا ما طلبته متطلبات **إنشاء txt من مستند**.

---

## الخلاصة

لقد استعرضنا كيفية **إنشاء txt من مستند** في C# مع **حفظ نص Word** و**تصدير المعادلات إلى LaTeX** باستخدام Aspose.Words. الفكرة الأساسية؟ بضع أسطر من الإعداد (`TxtSaveOptions`) تفتح إمكانية الحفاظ على الدقة الرياضية حتى في ملف `.txt` مبسط.

من هنا يمكنك:

- ربط ملف `.txt` المُولد بمولد مواقع ثابتة يدعم LaTeX.  
- إرساله إلى خط أنابيب نشر علمي يتوقع ترميز LaTeX الخام.  
- توسيع الكود لمعالجة دفعات من ملفات Word تلقائيًا.

أياً كان الخطوة التالية، لديك الآن أساس قوي يمكن الاعتماد عليه. هل لديك أسئلة أخرى؟ اترك تعليقًا، وتمنياتنا لك ببرمجة سعيدة!  

![مثال إنشاء txt من مستند](/images/create-txt-from-document.png "لقطة شاشة تُظهر txt المُصدَّر مع معادلات LaTeX – إنشاء txt من مستند")

---


## ما الذي يجب أن تتعلمه بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات التي تم توضيحها في هذا الدليل. كل مورد يتضمن أمثلة شفرة كاملة مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف أساليب تنفيذ بديلة في مشاريعك.

- [Save Document as Txt – Export Word Math to LaTeX in C#](/words/english/net/programming-with-officemath/save-document-as-txt-export-word-math-to-latex-in-c/)
- [Save docx as txt – Export Word Math to LaTeX with C#](/words/english/net/programming-with-officemath/save-docx-as-txt-export-word-math-to-latex-with-c/)
- [Save Document as TXT – Complete C# Guide to Convert DOCX to Plain Text](/words/english/net/programming-with-txtsaveoptions/save-document-as-txt-complete-c-guide-to-convert-docx-to-pla/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}