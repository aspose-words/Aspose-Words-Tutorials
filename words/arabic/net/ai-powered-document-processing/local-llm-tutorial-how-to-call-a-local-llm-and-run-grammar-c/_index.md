---
category: general
date: 2026-06-24
description: دورة تعليمية حول LLM المحلي تُظهر لك كيفية استدعاء LLM محلي، تحميل مستند
  Word وإجراء فحص القواعد باستخدام فحص القواعد بالذكاء الاصطناعي في C#.
draft: false
keywords:
- local llm tutorial
- run grammar check
- ai grammar check
- call local llm
- load word document
language: ar
og_description: يشرح دليل LLM المحلي خطوة بخطوة كيفية استدعاء LLM محلي، تحميل مستند
  Word، وتشغيل فحص القواعد اللغوية بالذكاء الاصطناعي في C#.
og_title: دورة تعليمية للـ LLM المحلي – استدعاء LLM محلي وإجراء فحص القواعد
schemas:
- author: Aspose
  dateModified: '2026-06-24'
  description: Local LLM tutorial that shows you how to call a local LLM, load a Word
    document and run grammar check using AI grammar check in C#.
  headline: Local LLM Tutorial – How to Call a Local LLM and Run Grammar Check
  type: TechArticle
- description: Local LLM tutorial that shows you how to call a local LLM, load a Word
    document and run grammar check using AI grammar check in C#.
  name: Local LLM Tutorial – How to Call a Local LLM and Run Grammar Check
  steps:
  - name: How to Run
    text: 1. Open a terminal in the project folder. 2. Run `dotnet run`. 3. Watch
      the console print the corrected text.
  - name: Can I use a different LLM brand?
    text: Absolutely. As long as the server respects the OpenAI v1 API schema, just
      change `Endpoint` and pick the corresponding `AiModelType` enum value (e.g.,
      `AiModelType.Llama2`). The rest of the code stays identical.
  - name: What if my document is huge (10 MB+)?
    text: Large payloads can exceed the default request size of many servers. Split
      the document into sections and call `CheckGrammar` per section, then concatenate
      the results. This also reduces the chance of a timeout.
  - name: How do I write the corrected output back to a `.docx` file?
    text: 'The `Document` class usually provides a `Save(string path, string content)`
      method. After you get `result.CorrectedText`, call:'
  - name: Is the dummy API key a security risk?
    text: No. The key is ignored by self‑hosted endpoints, but some SDKs enforce a
      non‑null string. Using a placeholder like `"dummy"` satisfies the SDK without
      exposing any secrets.
  type: HowTo
tags:
- LLM
- C#
- GrammarCheck
- AI
title: دورة تعليمية للـ LLM المحلي – كيفية استدعاء LLM محلي وتشغيل فحص القواعد
url: /ar/net/ai-powered-document-processing/local-llm-tutorial-how-to-call-a-local-llm-and-run-grammar-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# دورة LLM محلية – استدعاء LLM محلي وتشغيل فحص القواعد

هل تساءلت يومًا كيف **تشغّل فحص القواعد** على ملف Word دون إرسال أي شيء إلى السحابة؟ في هذه **دورة LLM محلية** سنقوم بربط نموذج لغة كبير مستضاف ذاتيًا، تحميل ملف `.docx`، والسماح للذكاء الاصطناعي بتنظيم النص. لا مفاتيح API، لا حركة مرور خارجية—فقط جهازك الخاص يقوم بالمعالجة.

سنستعرض كل سطر من الشيفرة، نشرح لماذا كل جزء مهم، ونظهر لك كيفية التعامل مع المشكلات الشائعة (مثل الملفات المفقودة أو نقطة النهاية غير المتاحة). في النهاية ستحصل على تطبيق C# Console جاهز للتنفيذ يقوم بـ **ai grammar check** باستخدام نموذج مستضاف محليًا.

> **ما ستحصل عليه:** برنامج كامل قابل للتنفيذ، شرح واضح لكل خطوة، ونصائح لتوسيع الحل إلى مستندات أكبر أو مزودي LLM مختلفين.

![local llm tutorial diagram](https://example.com/local-llm-tutorial-diagram.png "Diagram illustrating the flow of the local llm tutorial")

## المتطلبات المسبقة

قبل أن نبدأ، تأكد من وجود ما يلي:

- .NET 6.0 SDK أو أحدث (يمكنك تنزيله من موقع Microsoft)
- خادم LLM يعمل محليًا ويعرض نقطة نهاية متوافقة مع OpenAI (مثل Ollama، LM Studio، أو غلاف FastAPI مخصص)
- حزمة NuGet `AiGrammar` (أو أي مكتبة توفر الفئات `LocalLargeLanguageModel`، `Document`، و `AiModelType`)
- مستند Word تجريبي (`input.docx`) موجود في مجلد ستشير إليه لاحقًا

هذا كل شيء—لا حاجة لأي بيانات اعتماد سحابية إضافية.

## الخطوة 1: دورة LLM محلية – إعداد نقطة النهاية

أول شيء نحتاجه هو كائن **call local llm** يعرف إلى أين يرسل طلباته. فكر فيه كرقم الهاتف الذي تتصل به قبل أن تتحدث.

```csharp
using System;
using AiGrammar;   // Hypothetical library containing the LLM helpers

// Step 1: Configure a local large language model (LLM) endpoint
var llm = new LocalLargeLanguageModel
{
    Endpoint = "http://localhost:8000/v1",
    ApiKey = "dummy"   // Not required for self‑hosted models, but the property is mandatory
};
```

**لماذا هذا مهم:**  
معظم SDKs الخاصة بـ LLM تتوقع نقطة نهاية HTTP تتبع عقدة API الخاصة بـ OpenAI. بتوجيه `Endpoint` إلى `http://localhost:8000/v1` نخبر المكتبة بـ **call local llm** بدلاً من الاتصال بخوادم OpenAI. مفتاح API الوهمي هو مجرد عنصر نائب—بعض العملاء يرفضون قيمة `null`، لذا نعطيه قيمة غير ضارة.

> **نصيحة احترافية:** إذا شغّلت الـ LLM خلف وكيل عكسي، اضبط `Endpoint` على عنوان الوكيل ودع الوكيل يتعامل مع إنهاء TLS. هذا يبقي تطبيق الكونسول بسيطًا وآمنًا.

## الخطوة 2: تحميل مستند Word لفحص القواعد

الآن بعد أن أصبح النموذج قابلًا للوصول، نحتاج إلى **load word document** محتوى المستند إلى الذاكرة. فئة `Document` تج abstracts عملية تحليل `.docx` لنا.

```csharp
// Step 2: Load the document you want to check
var docPath = @"C:\Projects\GrammarDemo\YOUR_DIRECTORY\input.docx";
if (!System.IO.File.Exists(docPath))
{
    Console.Error.WriteLine($"Error: The file '{docPath}' does not exist.");
    return;
}

var doc = new Document(docPath);
```

**لماذا هذا مهم:**  
إرسال ملف `.docx` ثنائي مباشرة إلى LLM سيُربكه. أداة `Document` تستخرج النص الخام مع الحفاظ على فواصل الفقرات، مما يمنح **ai grammar check** مدخلًا نظيفًا للعمل معه. فحص الوجود يمنع حدوث `FileNotFoundException` مزعج قد يتسبب في تعطل التطبيق.

## الخطوة 3: تشغيل فحص القواعد باستخدام الـ LLM

هذا هو جوهر الدورة: نطلب من النموذج المحلي تدقيق النص. الطريقة `CheckGrammar` تخفي تفاصيل HTTP وتعيد كائن نتيجة.

```csharp
// Step 3: Run the grammar‑check operation using the LLM
var result = doc.CheckGrammar(
    llm,
    AiModelType.Gpt4   // You can swap this for any model supported by AiModelType
);
```

**لماذا هذا مهم:**  
`AiModelType.Gpt4` هو مجرد تسمية تخبر الخدمة البعيدة أي قالب مطالبة يستخدم. إذا كان لديك نموذج أصغر (مثل `Llama2`)، استبدله بذلك. المكتبة تسلسل نص المستند، ترسله إلى `http://localhost:8000/v1/completions`، وتُحلل المخرجات المصححة.

> **حالة حافة:** إذا انتهت مهلة الـ LLM، فإن `CheckGrammar` تُطلق استثناء `TimeoutException`. غلف الاستدعاء داخل كتلة `try/catch` إذا كنت تتوقع مستندات كبيرة أو خادمًا مشغولًا.

## الخطوة 4: إخراج النص المصحح

أخيرًا، نعرض النسخة المنقحة. في تطبيق حقيقي قد تكتبها مرة أخرى إلى ملف `.docx` جديد، لكن لهذه الدورة يكفي طباعة النص في الكونسول.

```csharp
// Step 4: Output the corrected text
Console.WriteLine("=== Corrected Text ===");
Console.WriteLine(result.CorrectedText);
```

**الناتج المتوقع** (بافتراض أن الملف الأصلي يحتوي على بعض الأخطاء المتعمدة):

```
=== Corrected Text ===
The quick brown fox jumps over the lazy dog. 
She doesn't like apples, but she loves oranges.
```

إذا لم يجد الـ LLM أي أخطاء، سيكون الناتج مطابقًا للمدخل، وهذا لا يزال إشارة مفيدة.

## مثال كامل يعمل

بجمع كل ما سبق، إليك البرنامج الكامل الذي يمكنك نسخه ولصقه في مشروع كونسول جديد:

```csharp
using System;
using AiGrammar;   // Replace with the actual namespace of your grammar library

namespace LocalLlmGrammarDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // Configure the local LLM endpoint
            var llm = new LocalLargeLanguageModel
            {
                Endpoint = "http://localhost:8000/v1",
                ApiKey = "dummy"
            };

            // Path to the Word document you want to check
            var docPath = @"C:\Projects\GrammarDemo\YOUR_DIRECTORY\input.docx";

            // Verify the file exists before proceeding
            if (!System.IO.File.Exists(docPath))
            {
                Console.Error.WriteLine($"Error: The file '{docPath}' does not exist.");
                return;
            }

            // Load the document (this also extracts plain text)
            var doc = new Document(docPath);

            // Perform the AI grammar check using the local LLM
            GrammarCheckResult result;
            try
            {
                result = doc.CheckGrammar(llm, AiModelType.Gpt4);
            }
            catch (Exception ex)
            {
                Console.Error.WriteLine($"Grammar check failed: {ex.Message}");
                return;
            }

            // Show the corrected text
            Console.WriteLine("=== Corrected Text ===");
            Console.WriteLine(result.CorrectedText);
        }
    }
}
```

### كيفية التشغيل

1. افتح الطرفية في مجلد المشروع.  
2. شغّل `dotnet run`.  
3. راقب الكونسول وهو يطبع النص المصحح.

هذا هو كل ما في **دورة LLM محلية** في أقل من 100 سطر من الشيفرة.

## الأسئلة المتكررة (FAQ)

### هل يمكنني استخدام علامة تجارية LLM مختلفة؟

بالطبع. طالما أن الخادم يلتزم بمخطط API الخاص بـ OpenAI v1، فقط غيّر `Endpoint` واختر قيمة تعداد `AiModelType` المقابلة (مثل `AiModelType.Llama2`). باقي الشيفرة يبقى كما هو.

### ماذا لو كان مستندي ضخمًا (أكثر من 10 ميغابايت)؟

الأحمال الكبيرة قد تتجاوز حجم الطلب الافتراضي للعديد من الخوادم. قسّم المستند إلى أقسام واستدعِ `CheckGrammar` لكل قسم، ثم اجمع النتائج. هذا يقلل أيضًا من احتمال حدوث مهلة.

### كيف أكتب النص المصحح مرة أخرى إلى ملف `.docx`؟

عادةً توفر فئة `Document` طريقة `Save(string path, string content)`. بعد حصولك على `result.CorrectedText`، استدعِ:

```csharp
doc.Save(@"C:\Projects\GrammarDemo\output_corrected.docx", result.CorrectedText);
```

تحقق من وثائق المكتبة للحصول على التوقيع الدقيق.

### هل مفتاح API الوهمي يمثل خطرًا أمنيًا؟

لا. المفتاح يتم تجاهله من قبل نقاط النهاية المستضافة ذاتيًا، لكن بعض SDKs تفرض وجود سلسلة غير فارغة. استخدام قيمة placeholder مثل `"dummy"` يُرضي الـ SDK دون كشف أي أسرار.

## الخطوات التالية والمواضيع ذات الصلة

- **Fine‑tune your local LLM** لتخصيص القواعد حسب المجال (مثل الكتابة القانونية أو الطبية).  
- **Run a batch job** لمعالجة مجلد كامل من ملفات Word—مفيد لسلاسل النشر.  
- استكشف **streaming responses** إذا أردت اقتراحات فورية أثناء كتابة المستخدم.  
- دمج هذا مع **spell‑checking libraries** للحصول على طبقة جودة مزدوجة.

كل فكرة من هذه الأفكار تبني على المفاهيم الأساسية التي غطيناها في **دورة LLM محلية**، لذا ستلاحظ تكرار الأنماط نفسها—**call local llm**، **load word document**، **run grammar check**، و **handle results**—في جميع الأمثلة.

---

*برمجة سعيدة! إذا واجهت أي مشكلة، اترك تعليقًا أدناه وسنساعدك في حلها.*


## ما الذي يجب أن تتعلمه بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات التي تم توضيحها في هذا الدليل. كل مورد يتضمن أمثلة شيفرة كاملة مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف نهج تنفيذ بديلة في مشاريعك.

- [Load With Encoding In Word Document](/words/english/net/programming-with-loadoptions/load-with-encoding/)
- [Load Encrypted In Word Document](/words/english/net/programming-with-loadoptions/load-encrypted-document/)
- [Recover Corrupted DOCX – Open & Load Word Document](/words/english/python-net/document-operations/recover-corrupted-docx-open-load-word-document/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}