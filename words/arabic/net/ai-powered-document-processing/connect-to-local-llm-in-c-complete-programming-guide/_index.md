---
category: general
date: 2026-04-28
description: الاتصال بـ LLM المحلي من C# وتحفيز نموذج اللغة الكبير لتحميل مستند Word،
  استدعاء الـ LLM المحلي وإعادة كتابة النص تلقائيًا. يتضمن كود خطوة بخطوة.
draft: false
keywords:
- connect to local llm
- prompt large language model
- load word document
- call local llm
- rewrite text automatically
language: ar
og_description: اتصل بـ LLM المحلي من C# وتعرّف على كيفية توجيه نموذج اللغة الضخم،
  تحميل مستند Word، استدعاء الـ LLM المحلي وإعادة كتابة النص تلقائيًا في دقائق.
og_title: الاتصال بـ LLM المحلي في C# – دليل البرمجة الكامل
tags:
- Aspose.Words
- C#
- LLM
- AI Automation
title: الاتصال بـ LLM المحلي في C# – دليل برمجة شامل
url: /ar/net/ai-powered-document-processing/connect-to-local-llm-in-c-complete-programming-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# الاتصال بـ LLM المحلي في C# – دليل برمجي كامل

هل احتجت يومًا إلى **الاتصال بـ llm المحلي** من تطبيق .NET وتساءلت كيف تجعلها تتعامل مع ملف Word؟ لست وحدك. في هذا الدليل سنستعرض العملية بالكامل — الاتصال بـ llm المحلي، **تحفيز نموذج اللغة الكبيرة**، تحميل مستند Word، **استدعاء llm المحلي**، وأخيرًا **إعادة كتابة النص تلقائيًا**. في النهاية ستحصل على مثال قابل للتنفيذ يحول أي فقرة إلى نبرة رسمية دون الحاجة إلى مفاتيح API خارجية.

## ما يغطيه هذا الدرس

سنبدأ بتثبيت حزم NuGet الضرورية، ثم تشغيل نقطة نهاية LLM محلية بسيطة (فكر في Ollama على المنفذ 11434). بعد ذلك سنحمّل ملف `.docx` باستخدام Aspose.Words، نرسل فقرة إلى LLM، نستقبل نسخة معاد صياغتها، ونكتبها مرة أخرى في نفس المستند. ستشاهد أيضًا كيفية التعامل مع المشكلات الشائعة — فقرات فارغة، إلغاء الموارد بشكل غير متزامن، ومشكلات الترميز — بحيث يعمل الكود في بيئة الإنتاج وليس مجرد عرض توضيحي.

### المتطلبات المسبقة

- .NET 6.0 SDK أو أحدث (يمكنك أيضًا استخدام .NET 8 إذا رغبت)
- Visual Studio 2022 أو VS Code مع امتداد C#
- **Aspose.Words for .NET** (الإصدار التجريبي المجاني يعمل جيدًا)
- LLM مستضاف محليًا يدعم عقد `/api/generate` (مثل Ollama، LMStudio)
- إلمام أساسي بـ async/await في C#

> **نصيحة احترافية:** إذا لم تقم بتثبيت Ollama بعد، شغّل `ollama serve` واسحب نموذجًا باستخدام `ollama pull llama3`. ستكون نقطة النهاية HTTP الافتراضية `http://localhost:11434/api/generate`.

---

## الخطوة 1: تثبيت الحزم المطلوبة

أولاً، أضف حزم NuGet الخاصة بـ Aspose.Words و Aspose.Words.AI إلى مشروعك.

```bash
dotnet add package Aspose.Words
dotnet add package Aspose.Words.AI
```

هذه المكتبات تمنحنا القدرة على **تحميل مستند Word** وتغليفًا خفيفًا لـ **استدعاء llm المحلي** دون الحاجة إلى كتابة طلبات HTTP يدويًا.

---

## الخطوة 2: الاتصال بنقطة نهاية LLM المحلي

الاتصال بنموذج مستضاف محليًا بسيط مثل إنشاء كائن `LocalLargeLanguageModel`. يتوقع المُنشئ عنوان URL الكامل لنقطة توليد النص.

```csharp
using Aspose.Words.AI;
using Aspose.Words;
using System.Threading.Tasks;

// Create a client that talks to the LLM running on localhost
var localLlm = new LocalLargeLanguageModel("http://localhost:11434/api/generate");
```

لماذا نغلف النقطة النهاية في فئة؟ فئة `LocalLargeLanguageModel` تتعامل مع تسلسل JSON، وإعادة المحاولات، وتدفق الاستجابات نيابةً عنك — بحيث يمكنك التركيز على منطق التحفيز بدلاً من العبث بـ `HttpClient`.

---

## الخطوة 3: تحميل مستند Word المصدر

بعد ذلك، نجلب المستند إلى الذاكرة. يدعم Aspose.Words تقريبًا كل تنسيقات Word، لذا سيقوم `Document` بتحليل `input.docx` دون الحاجة إلى تثبيت Office.

```csharp
// Path to the source file – adjust as needed
string inputPath = Path.Combine(Environment.CurrentDirectory, "input.docx");

// Load the document; throws if the file is missing or corrupted
Document sourceDocument = new Document(inputPath);
```

إذا احتجت للعمل مع تدفق (مثلاً ملف تم رفعه عبر ASP.NET)، استبدل مسار الملف بـ `MemoryStream` ومرره إلى مُنشئ `Document`.

---

## الخطوة 4: استخراج نص الفقرة الحالية

سنستخدم `DocumentBuilder` للتنقل داخل المستند. في هذا المثال نعيد صياغة **الفقرة الأولى**، لكن يمكنك التكرار على `sourceDocument.GetChildNodes(NodeType.Paragraph, true)` لمعالجة عدة فقرات.

```csharp
// Builder gives us a cursor inside the document
DocumentBuilder docBuilder = new DocumentBuilder(sourceDocument);

// Grab the text of the paragraph where the builder is currently positioned
string originalParagraph = docBuilder.CurrentParagraph?.GetText() ?? string.Empty;

// Safety check – avoid sending empty strings to the LLM
if (string.IsNullOrWhiteSpace(originalParagraph))
{
    Console.WriteLine("No paragraph found at the current cursor position.");
    return;
}
```

عامل `?.` يمنع حدوث `NullReferenceException` إذا كان المستند فارغًا. هذه واحدة من **حالات الحافة** التي تُربك المبتدئين.

---

## الخطوة 5: تحفيز LLM لإعادة صياغة الفقرة

الآن نقوم فعليًا بـ **تحفيز نموذج اللغة الكبيرة**. النص التحفيزي هو إنجليزي بسيط؛ التغليف سيُرسله كـ JSON إلى النقطة النهاية المحلية.

```csharp
// Build a friendly instruction for the model
string prompt = $"Rewrite the following sentence in a more formal tone:\n{originalParagraph}";

// Await the model's response – this is an async call
string rewrittenParagraph = await localLlm.PromptAsync(prompt);
```

لماذا نصيغ الطلب بهذه الطريقة؟ تستجيب LLMs بشكل أفضل لتعليمات واضحة ومحددة المهمة. إضافة سطر جديد بعد النقطتين تفصل بين التعليمات والمحتوى، مما يقلل من احتمال أن يُعيد النموذج النص التحفيزي نفسه.

**الناتج المتوقع** – إذا كان `originalParagraph` هو `"Hey, what's up?"`، قد يُعيد LLM:

> “Good day, how may I assist you?”

يمكنك التحقق من النتيجة بطباعتها:

```csharp
Console.WriteLine("Original:  " + originalParagraph);
Console.WriteLine("Rewritten: " + rewrittenParagraph);
```

---

## الخطوة 6: إدراج النص المعاد صياغته مرة أخرى في المستند

مع النص الجديد في المتناول، نستبدل الفقرة القديمة. `DocumentBuilder.Writeln` يكتب سطرًا جديدًا ويحرك المؤشر للأمام، وهو مثالي للإضافة. إذا أردت *استبدال* الفقرة نفسها تمامًا، يمكنك استخدام `docBuilder.CurrentParagraph.RemoveAllChildren()` قبل الكتابة.

```csharp
// Option A – Append a new paragraph (keeps the original)
docBuilder.Writeln(rewrittenParagraph);

// Option B – Replace the existing paragraph (uncomment to use)
// docBuilder.CurrentParagraph.RemoveAllChildren();
// docBuilder.CurrentParagraph.AppendChild(new Run(docBuilder.Document, rewrittenParagraph));
```

تم عرض كلا النهجين لتختار ما يناسب سير عملك.

---

## الخطوة 7: حفظ المستند المحدث

أخيرًا، نحفظ التغييرات في ملف جديد. يختار Aspose.Words التنسيق تلقائيًا بناءً على امتداد الملف.

```csharp
string outputPath = Path.Combine(Environment.CurrentDirectory, "output.docx");
sourceDocument.Save(outputPath);

Console.WriteLine($"Document saved to {outputPath}");
```

افتح `output.docx` في Word، وسترى أن الفقرة الآن مكتوبة بنبرة رسمية.

---

## مثال كامل يعمل

فيما يلي **البرنامج الكامل المستقل**. انسخه إلى مشروع Console، استعد حزم NuGet، وشغّله — لا تحتاج إلى أي إعدادات إضافية سوى تشغيل LLM المحلي.

```csharp
using Aspose.Words.AI;
using Aspose.Words;
using System;
using System.IO;
using System.Threading.Tasks;

class Program
{
    static async Task Main()
    {
        // -------------------------------------------------
        // Step 1: Connect to the locally hosted LLM endpoint
        // -------------------------------------------------
        var localLlm = new LocalLargeLanguageModel("http://localhost:11434/api/generate");

        // -------------------------------------------------
        // Step 2: Load the source Word document
        // -------------------------------------------------
        string inputPath = Path.Combine(Environment.CurrentDirectory, "input.docx");
        Document sourceDocument = new Document(inputPath);

        // -------------------------------------------------
        // Step 3: Retrieve the text of the current paragraph
        // -------------------------------------------------
        DocumentBuilder docBuilder = new DocumentBuilder(sourceDocument);
        string originalParagraph = docBuilder.CurrentParagraph?.GetText() ?? string.Empty;

        if (string.IsNullOrWhiteSpace(originalParagraph))
        {
            Console.WriteLine("No paragraph found at the current cursor position.");
            return;
        }

        // -------------------------------------------------
        // Step 4: Ask the LLM to rewrite the paragraph in a formal tone
        // -------------------------------------------------
        string prompt = $"Rewrite the following sentence in a more formal tone:\n{originalParagraph}";
        string rewrittenParagraph = await localLlm.PromptAsync(prompt);

        // -------------------------------------------------
        // Step 5: Insert the rewritten text back into the document
        // -------------------------------------------------
        docBuilder.Writeln(rewrittenParagraph);

        // -------------------------------------------------
        // Step 6: Save the updated document
        // -------------------------------------------------
        string outputPath = Path.Combine(Environment.CurrentDirectory, "output.docx");
        sourceDocument.Save(outputPath);

        Console.WriteLine("Original paragraph:");
        Console.WriteLine(originalParagraph);
        Console.WriteLine("\nRewritten paragraph:");
        Console.WriteLine(rewrittenParagraph);
        Console.WriteLine($"\nDocument saved to {outputPath}");
    }
}
```

### ما تتوقعه عند تشغيله

1. يطبع الكونسول الفقرة الأصلية والفقرة المعاد صياغتها.  
2. يظهر `output.docx` بجوار `input.docx`.  
3. عند فتح الملف، ستجد الفقرة الرسمية الجديدة مضافة بعد الأصل (أو مستبدلة إذا استخدمت الكود البديل).

---

## التعامل مع حالات الحافة الشائعة

| الحالة | الحل |
|-----------|----------|
| **فقرة فارغة أو تحتوي على مسافات فقط** | تحقق من `string.IsNullOrWhiteSpace` قبل التحفيز (انظر الخطوة 3). |
| **LLM يُعيد خطأ أو سلسلة فارغة** | غلف `PromptAsync` بـ `try/catch` وارجع إلى النص الأصلي كبديل. |
| **ضرورة إعادة صياغة فقرات متعددة** | كرّر عبر `sourceDocument.GetChildNodes(NodeType.Paragraph, true)` وطبق منطق التحفيز نفسه. |
| **المستندات الكبيرة تُسبب تأخيرًا** | اجمع الفقرات وأرسلها في طلب واحد (حدّ التحفيز حتى 4 KB لكل استدعاء). |
| **حروف غير ASCII تظهر مشوهة** | تأكد من أن نقطة النهاية للـ LLM تستخدم UTF‑8 (معظم النماذج الحديثة تفعل ذلك). |

---

## الخطوات التالية والمواضيع ذات الصلة

- **تحفيز نموذج اللغة الكبيرة** بتعليمات أكثر تفصيلاً (مثل أدلة الأسلوب، حدود الطول).  
- استخدم **استدعاء llm المحلي** في Web API لتوفير أتمتة المستندات كخدمة.  
- استكشف **تحميل مستند Word** عبر تدفقات متوازية لسيناريوهات عالية الإنتاجية.  
- دمج هذا النهج مع **إعادة كتابة النص تلقائيًا** لتوليد رسائل بريد جماعية أو توحيد تقارير.

للتعمق أكثر، راجع توثيق Aspose حول **دمج المستندات** ومرجع Ollama API للحصول على معلمات العينة المخصصة.

---

## الخلاصة

لقد أظهرنا لك كيفية **الاتصال بـ llm المحلي** من C#، **تحفيز نموذج اللغة الكبيرة**، **تحميل مستند Word**، **استدعاء llm المحلي**، و**إعادة كتابة النص تلقائيًا** — كل ذلك في تطبيق Console واحد قابل للتنفيذ. النمط قابل للتوسيع: غيّر التحفيز، كرّر على الفقرات، أو قدّم المنطق عبر نقطة نهاية ASP.NET. الفكرة الأساسية هي أن نماذج الذكاء الاصطناعي المحلية يمكن دمجها بعمق مع مكتبات معالجة المستندات التقليدية، لتوفر أتمتة قوية دون مغادرة بيئتك الموثوقة داخل المؤسسة.

هل لديك أسئلة حول الـ threading،

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}