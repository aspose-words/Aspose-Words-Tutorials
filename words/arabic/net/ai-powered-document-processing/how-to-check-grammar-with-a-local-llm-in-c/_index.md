---
category: general
date: 2026-03-19
description: تعلم كيفية فحص القواعد النحوية في Word باستخدام نموذج LLM محلي، وتسجيل
  النموذج، وحفظ المستندات المصححة—كل ذلك في دليل C# واحد.
draft: false
keywords:
- how to check grammar
- set up local llm
- check grammar in word
- how to register llm
- how to save corrected
language: ar
og_description: كيفية فحص القواعد في Word باستخدام نموذج لغة كبير محلي، وتسجيل النموذج،
  وحفظ المستندات المصححة—دليل خطوة بخطوة.
og_title: كيفية التحقق من القواعد النحوية باستخدام نموذج لغة محلي في C#
tags:
- Aspose.Words
- AI
- C#
title: كيفية التحقق من القواعد النحوية باستخدام نموذج لغة محلي في C#
url: /ar/net/ai-powered-document-processing/how-to-check-grammar-with-a-local-llm-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# كيفية فحص القواعد النحوية باستخدام نموذج LLM محلي في C#

هل تساءلت يومًا **كيف تتحقق من القواعد النحوية** في مستند Word دون إرسال نصك إلى السحابة؟ لست وحدك. يرغب العديد من المطورين في خصوصية نموذج مستضاف ذاتيًا مع الاستمرار في الحصول على اقتراحات مدعومة بالذكاء الاصطناعي. في هذا الدليل سنستعرض كيفية تسجيل نموذج LLM مخصص، وتكوين Aspose.Words لاستخدامه، وأخيرًا **كيفية حفظ الملفات المصححة** — كل ذلك بلغة C# بسيطة.

سنغطي أيضًا تفاصيل **إعداد LLM محلي**، ونوضح لك **كيفية تسجيل نقاط النهاية للـ llm**، ونظهر الخطوات الدقيقة **للتحقق من القواعد النحوية في مستندات word**. في النهاية ستحصل على مثال قابل للتنفيذ يمكنك إدراجه في أي مشروع .NET.

## المتطلبات المسبقة

- .NET 6+ SDK (الكود يعمل على .NET Core و .NET Framework)
- Visual Studio 2022 أو VS Code مع امتدادات C#
- Aspose.Words for .NET (الإصدار 24.12 أو أحدث) – يمكنك الحصول عليه من NuGet
- نموذج LLM يعمل محليًا ويتوافق مع API المتوافقة مع OpenAI (مثال: Ollama على المنفذ 11434)

> **نصيحة احترافية:** إذا كنت تستخدم Ollama، فإن الأمر `ollama serve` سيُنشئ نقطة النهاية `http://localhost:11434/api/generate` تلقائيًا.

## الخطوة 1 – كيفية تسجيل llm: إضافة النموذج المخصص إلى Aspose.Words

أول شيء نحتاجه هو إخبار Aspose.Words عن **llm المحلي** الخاص بنا. يتم ذلك مرة واحدة عند بدء تشغيل التطبيق.

```csharp
using Aspose.Words;
using Aspose.Words.AI;

// Register a custom LLM endpoint – no API key required for local servers
AiEngine.RegisterModel(
    modelName: "local-llm",                         // identifier we’ll reference later
    endpoint: new Uri("http://localhost:11434/api/generate"),
    apiKey: null,                                   // local server doesn’t need a key
    provider: AiProvider.Custom);
```

**لماذا هذا مهم:** من خلال تسجيل النموذج، تمنح Aspose.Words مقبضًا مسمى (`"local-llm"`). لاحقًا، عندما نستدعي `CheckGrammar`, تعرف المكتبة بالضبط أي نقطة نهاية يجب استهدافها. تخطي هذه الخطوة يجبر المكتبة على الرجوع إلى خدمة السحابة المدمجة، مما يفسد هدف الـ LLM الخاص.

## الخطوة 2 – تحميل مستند Word الذي تريد تحليله

الآن نقوم بتحميل الملف إلى الذاكرة. يمكنك الإشارة إلى أي ملف `.docx` أو `.doc` أو حتى `.rtf`.

```csharp
// Replace YOUR_DIRECTORY with the actual folder path on your machine
Document sourceDocument = new Document("YOUR_DIRECTORY/input.docx");

// Quick sanity check – print the number of paragraphs we just loaded
Console.WriteLine($"Loaded document with {sourceDocument.GetChildNodes(NodeType.Paragraph, true).Count} paragraphs.");
```

**ما الذي يحدث:** `Document` هو نموذج الكائن الأساسي في Aspose.Words. يقوم بتحليل الملف وبناء شجرة من العقد (فقرات، جداول، صور، إلخ). يتيح ذلك لمحرك الذكاء الاصطناعي استهداف نطاقات نصية محددة لتحليل القواعد النحوية.

## الخطوة 3 – تكوين خيارات فحص القواعد النحوية (إعداد llm محلي)

هنا نربط النموذج المسجل مسبقًا بعملية فحص القواعد النحوية.

```csharp
AiGrammarCheckOptions grammarOptions = new AiGrammarCheckOptions
{
    Model = "local-llm",               // references the name we used in RegisterModel
    // Optional: you can tweak temperature, maxTokens, etc. if your LLM supports them
    // Temperature = 0.7,
    // MaxTokens = 512
};
```

**لماذا نعرض هذه الخيارات:** نماذج LLM المختلفة لها سلوك مختلف. من خلال إتاحة `Model`, يسمح لك Aspose.Words بالتبديل بين نموذج محلي ونموذج سحابي دون تغيير أي كود آخر. هذه المرونة أساسية عند **إعداد llm محلي** للبيئات التي تتطلب الامتثال أو السيناريوهات غير المتصلة.

## الخطوة 4 – تشغيل فحص القواعد النحوية المدفوع بالذكاء الاصطناعي (التحقق من القواعد النحوية في word)

مع ربط كل شيء, فحص القواعد النحوية الفعلي هو سطر واحد فقط.

```csharp
// This mutates sourceDocument in place, inserting suggestions and corrections
sourceDocument.CheckGrammar(grammarOptions);
Console.WriteLine("Grammar check completed.");
```

**تحت الغطاء:** يقوم Aspose.Words باستخراج كل جملة, وإرسالها إلى نقطة نهاية LLM, ويتلقى حمولة JSON مع التعديلات المقترحة, ثم يطبق تلك التعديلات على شجرة المستند. العملية تُنفّذ بشكل متزامن هنا للتبسيط; يمكنك أيضًا استدعاء النسخة غير المتزامنة `CheckGrammarAsync` إذا كنت تفضّل I/O غير محجوب.

## الخطوة 5 – كيفية حفظ المستندات المصححة

بعد أن يقوم الذكاء الاصطناعي بعمله السحري, ستحتاج إلى حفظ التغييرات.

```csharp
// Save the corrected file – you can change the format to PDF, HTML, etc.
sourceDocument.Save("YOUR_DIRECTORY/checked.docx");
Console.WriteLine("Corrected document saved as checked.docx");
```

**ما المتوقع:** افتح `checked.docx` في Word وسترى مشكلات القواعد النحوية مميزة (أو مصححة تلقائيًا, حسب إعدادات `AiGrammarCheckOptions`). إذا قمت بتمكين التتبع, سترى أيضًا علامات المراجعة.

## مثال كامل يعمل

بجمع كل شيء معًا, إليك تطبيق console جاهز للتنفيذ:

```csharp
// Program.cs
using System;
using Aspose.Words;
using Aspose.Words.AI;

class Program
{
    static void Main()
    {
        // 1️⃣ Register the local LLM
        AiEngine.RegisterModel(
            modelName: "local-llm",
            endpoint: new Uri("http://localhost:11434/api/generate"),
            apiKey: null,
            provider: AiProvider.Custom);

        // 2️⃣ Load the source document
        string inputPath = "YOUR_DIRECTORY/input.docx";
        Document sourceDocument = new Document(inputPath);
        Console.WriteLine($"Loaded: {inputPath}");

        // 3️⃣ Set up grammar‑check options (using the local model)
        AiGrammarCheckOptions grammarOptions = new AiGrammarCheckOptions
        {
            Model = "local-llm"
        };

        // 4️⃣ Perform the AI‑driven grammar check
        sourceDocument.CheckGrammar(grammarOptions);
        Console.WriteLine("Grammar analysis finished.");

        // 5️⃣ Save the corrected document
        string outputPath = "YOUR_DIRECTORY/checked.docx";
        sourceDocument.Save(outputPath);
        Console.WriteLine($"Corrected file saved to: {outputPath}");
    }
}
```

**المخرجات المتوقعة في وحدة التحكم:**

```
Loaded: YOUR_DIRECTORY/input.docx
Grammar analysis finished.
Corrected file saved to: YOUR_DIRECTORY/checked.docx
```

افتح `checked.docx` وسترى تحسينات القواعد النحوية مطبقة تلقائيًا.

## أسئلة شائعة وحالات خاصة

| السؤال | الجواب |
|----------|--------|
| *ماذا لو كان الـ LLM الخاص بي يحتاج إلى مفتاح API؟* | مرّر المفتاح إلى `apiKey` في `RegisterModel`. يعمل نفس الكود لكل من الخدمات التي تتطلب مفتاحًا وتلك التي لا تحتاجه. |
| *هل يمكنني استخدام تنسيق ملف مختلف؟* | بالتأكيد. `Document.Save` يدعم `.pdf`، `.html`، `.txt`، إلخ. فقط غيّر الامتداد. |
| *ماذا لو أعاد الـ LLM خطأً؟* | غلف `CheckGrammar` بكتلة try/catch؛ افحص `AiException` للحصول على التفاصيل. غالبًا ما يكون السبب مهلة—فكر في زيادة `grammarOptions.Timeout`. |
| *هل العملية آمنة من حيث الخيوط (thread‑safe)؟* | خطوة التسجيل عامة ويجب تنفيذها مرة واحدة عند بدء التشغيل. استدعاءات `CheckGrammar` اللاحقة آمنة للتنفيذ المتوازي طالما أن كل واحدة تستخدم نسخة `Document` الخاصة بها. |

## الخطوات التالية

الآن بعد أن عرفت **كيفية فحص القواعد النحوية** باستخدام **llm محلي**, قد ترغب في استكشاف:

- **المعالجة الدفعية**: التكرار عبر مجلد من المستندات وتشغيل نفس خط الأنابيب.
- **المطالبات المخصصة**: تعديل حمولة الطلب عن طريق ضبط `grammarOptions.PromptTemplate` لفحوصات خاصة بنمط معين.
- **التكامل مع ASP.NET Core**: إتاحة نقطة نهاية API تقبل ملفات `.docx` المرفوعة, تشغل فحص القواعد النحوية, وتعيد الملف المصحح.

هذه الإضافات تتيح لك بناء منصة “القواعد النحوية كخدمة” كاملة الميزات دون مغادرة بيئتك.

---

*برمجة سعيدة! إذا واجهت أي مشاكل, اترك تعليقًا أدناه—أنا سعيد بمساعدتك على ضبط الإعداد.*

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}