---
category: general
date: 2026-02-10
description: تعلم كيفية حفظ ملفات docx كملفات txt وتحويل docx إلى markdown مع تصدير
  المعادلات إلى LaTeX باستخدام Aspose.Words لـ .NET.
draft: false
keywords:
- save docx as txt
- convert docx to markdown
- convert word to txt
- save document as markdown
- export equations to latex
language: ar
og_description: احفظ ملف docx كملف txt وحوّل docx إلى markdown مع تصدير معادلات LaTeX
  في دليل C# واحد.
og_title: احفظ ملف docx كملف txt – تحويل docx إلى markdown
tags:
- Aspose.Words
- C#
- Document Conversion
title: حفظ ملف docx كملف txt – تحويل docx إلى markdown
url: /ar/net/programming-with-markdownsaveoptions/save-docx-as-txt-convert-docx-to-markdown/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# حفظ docx كـ txt – تحويل docx إلى markdown

هل احتجت يوماً إلى **save docx as txt** ولكنك أيضاً أردت نسخة Markdown مرتبة تحافظ على معادلاتك سليمة؟ لست وحدك. يواجه العديد من المطورين مشكلة عندما تقوم مُصدّرات Word المدمجة بإزالة OfficeMath، مما يتركك بنص عادي غير مفهوم.  

في هذا الدرس سنستعرض حلاً كاملاً وجاهزاً للتنفيذ يقوم **converts docx to markdown**، **saves the same source as plain‑text**، و **exports equations to LaTeX**. في النهاية ستحصل على ملفين — `output.md` و `output.txt` — يبدوان تماماً كوثيقة Word الأصلية، مع المعادلات.

> **ما ستحتاجه**  
> * .NET 6+ (أو .NET Framework 4.6+).  
> * Aspose.Words for .NET (الإصدار التجريبي المجاني يعمل جيداً للاختبار).  
> * ملف DOCX يحتوي على معادلة واحدة على الأقل (OfficeMath).  

![save docx as txt example](/images/save-docx-as-txt.png)

## الخطوة 1: تحميل ملف DOCX

أولاً وقبل كل شيء—قم بتحميل المستند المصدر إلى الذاكرة. فئة `Document` تمثل ملف Word وتمنحنا الوصول إلى كل عنصر، من الفقرات إلى المعادلات.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;

// Load the source .docx
Document doc = new Document(@"C:\MyDocs\input.docx");
```

*لماذا هذا مهم*: تحميل الملف مرة واحدة يجنب عمليات I/O المتكررة عندما نقوم لاحقاً بالتصدير إلى صيغتين مختلفتين. كما يضمن أن أي موارد مدمجة (صور، خطوط) تظل مرتبطة بنفس نسخة `Document`.

## الخطوة 2: إعداد خيارات حفظ Markdown – convert docx to markdown

Markdown هي لغة ترميز نصية بسيطة، لكن بشكل افتراضي تقوم Aspose.Words بتحويل المعادلات إلى صور. نغير ذلك باستخدام الخاصية `OfficeMathExportMode`.

```csharp
// Configure Markdown export – export equations as LaTeX
MarkdownSaveOptions mdOptions = new MarkdownSaveOptions
{
    OfficeMathExportMode = OfficeMathExportMode.LaTeX
};
```

*نصيحة احترافية*: إذا احتجت المعادلات كـ MathML بدلاً من ذلك، فقط استبدل `LaTeX` بـ `MathML`. نفس الخيار يعمل مع صيغ أخرى مثل HTML.

## الخطوة 3: تصدير المستند كـ Markdown – save document as markdown

الآن نقوم فعلياً بكتابة ملف Markdown. طريقة `Save` تلتقط الخيارات التي عرّفناها للتو.

```csharp
// Save as Markdown (.md)
doc.Save(@"C:\MyDocs\output.md", mdOptions);
```

**النتيجة المتوقعة** – افتح `output.md` في أي محرر وسترى عناوين Markdown عادية، قوائم نقطية، ولكل معادلة شيء مثل:

```
$$
\int_{a}^{b} f(x)\,dx
$$
```

هذا هو الجزء الخاص بـ *export equations to latex* يقوم بعمله.

## الخطوة 4: إعداد خيارات حفظ النص العادي – convert word to txt

تصدير النص العادي مشابه، لكننا نستخدم `TxtSaveOptions`. مرة أخرى نخبر Aspose بتحويل OfficeMath إلى LaTeX حتى لا تُفقد المعادلات.

```csharp
// Configure TXT export – keep equations as LaTeX
TxtSaveOptions txtOptions = new TxtSaveOptions
{
    OfficeMathExportMode = OfficeMathExportMode.LaTeX
};
```

لماذا لا نستخدم فقط `doc.Save("output.txt")`؟ بدون الخيارات ستُحذف المعادلات، مما يترك فجوة في ملاحظاتك التقنية. الخيارات الصريحة تجعل التحويل **convert word to txt** مع الحفاظ على الرياضيات.

## الخطوة 5: حفظ docx كـ txt – convert word to txt

مع إعداد الخيارات، نكتب ملف النص العادي.

```csharp
// Save as plain‑text (.txt)
doc.Save(@"C:\MyDocs\output.txt", txtOptions);
```

افتح `output.txt` وسترى نسخة نظيفة ومُقسمة إلى أسطر من المستند الأصلي. تظهر المعادلات كـ LaTeX داخل السطر، مثال:

```
\int_{a}^{b} f(x)\,dx
```

هذا مثالي للبحث السريع باستخدام grep أو لتغذية نماذج الذكاء الاصطناعي التي تفهم صsyntax LaTeX.

## الخطوة 6: التحقق من النتيجة ومعالجة الحالات الخاصة

### فحص سريع للمنطقية

```csharp
Console.WriteLine(File.ReadAllText(@"C:\MyDocs\output.md"));
Console.WriteLine("-----");
Console.WriteLine(File.ReadAllText(@"C:\MyDocs\output.txt"));
```

إذا كان كلا الملفين يحتويان على العناوين المتوقعة، النقاط النقطية، وكتل LaTeX، فقد نجحت في **save docx as txt** و **convert docx to markdown**.

### الأخطاء الشائعة وكيفية تجنّبها

| المشكلة | سبب حدوثها | الحل |
|-------|----------------|-----|
| المعادلات تظهر كـ `?` | استخدام نسخة أقدم من Aspose.Words لا تدعم `OfficeMathExportMode` | الترقي إلى أحدث حزمة NuGet |
| الصور مفقودة في Markdown | `MarkdownSaveOptions` الافتراضية تدمج الصور كـ base64؛ المستندات الكبيرة قد تتجاوز حدود الحجم | تعيين `ExportImagesAsBase64 = false` وتوفير مجلد صور مخصص |
| التفاف النص يبدو غريباً في TXT | `TxtSaveOptions` الافتراضية تقص السطر عند 80 حرفاً | ضبط `TxtSaveOptions.MaxCharactersPerLine` ليتناسب مع احتياجاتك |
| حروف UTF‑8 مشوشة | ترميز النظام الافتراضي هو ANSI | تعيين `txtOptions.Encoding = Encoding.UTF8` |

### نصيحة إضافية: التحويل الجماعي

إذا كان لديك مجلد يحتوي على ملفات DOCX، غلف المنطق السابق داخل حلقة `foreach`. يمكن إعادة استخدام نفس نسخة `Document`، لكن تذكر استدعاء `doc = new Document(path)` داخل الحلقة لإعادة ضبط الحالة.

```csharp
string[] files = Directory.GetFiles(@"C:\MyDocs\Batch", "*.docx");
foreach (var file in files)
{
    Document batchDoc = new Document(file);
    string baseName = Path.GetFileNameWithoutExtension(file);
    batchDoc.Save($@"C:\MyDocs\Batch\{baseName}.md", mdOptions);
    batchDoc.Save($@"C:\MyDocs\Batch\{baseName}.txt", txtOptions);
}
```

هذه طريقة مفيدة لـ **convert word to txt** على نطاق واسع مع الحصول على نسخة Markdown.

## الخاتمة

لقد غطينا كل ما تحتاجه لـ **save docx as txt**، **convert docx to markdown**، و **export equations to LaTeX** في سير عمل واحد ومتكامل. من خلال تحميل المستند مرة واحدة، وتكوين `MarkdownSaveOptions` و `TxtSaveOptions` باستخدام `OfficeMathExportMode.LaTeX`، واستدعاء `Save` مرتين، ستحصل على ملفين نظيفين وقابلين للبحث يحتفظان بالدقة الرياضية للوثيقة الأصلية.

الخطوات التالية؟ جرّب استبدال تصدير LaTeX بـ MathML، جرب معالجة الصور المخصصة، أو دمج هذه الخطوات في مهمة CI/CD تُنشئ الوثائق تلقائياً من مواصفات Word. النمط نفسه يعمل مع صيغ أخرى أيضاً—HTML، PDF، وحتى EPUB—وبذلك يمكنك توسيع نهج **save document as markdown** لأي مخرج تحتاجه.

برمجة سعيدة، وتذكر: المستند المحوَّل جيداً هو نصف المعركة التي فُزت بها. إذا واجهت أي مشكلة، اترك تعليقاً أدناه—دعنا نحلها معاً!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}