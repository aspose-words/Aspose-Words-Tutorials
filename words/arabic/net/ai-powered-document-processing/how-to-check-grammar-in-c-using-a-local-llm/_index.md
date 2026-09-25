---
category: general
date: 2026-02-21
description: كيفية فحص القواعد النحوية في C# عن طريق تحميل ملف DOCX، وإرسال نصه إلى
  نموذج لغة كبير محلي، ثم كتابة النسخة المصححة مرة أخرى. يتضمن ذلك كيفية استخدام النموذج
  اللغوي وقراءة نص مستند Word.
draft: false
keywords:
- how to check grammar
- how to use llm
- read word document text
- load docx in c#
language: ar
og_description: كيفية فحص القواعد النحوية في C# عن طريق تحميل ملف DOCX، وإرسال نصه
  إلى نموذج لغة محلي، ثم كتابة النسخة المصححة مرة أخرى. تعلم كيفية استخدام نموذج اللغة
  وقراءة نص مستند Word.
og_title: كيفية فحص القواعد النحوية في C# باستخدام نموذج لغة محلي
tags:
- C#
- LLM
- Aspose.Words
title: كيفية التحقق من القواعد النحوية في C# باستخدام نموذج لغة محلي
url: /ar/net/ai-powered-document-processing/how-to-check-grammar-in-c-using-a-local-llm/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# كيفية فحص القواعد النحوية في C# باستخدام نموذج لغة كبير محلي

هل تساءلت يومًا **كيف تفحص القواعد النحوية** في مستند Word دون مغادرة مشروع C# الخاص بك؟ لست وحدك—المطورون يتساءلون باستمرار، “هل يمكنني أتمتة التدقيق اللغوي باستخدام نفس الكود الذي يشغّل الدردشات الآلية؟” الجواب المختصر هو نعم. عن طريق تحميل ملف DOCX، استخراج نصه، وإرساله إلى نموذج لغة كبير مستضاف محليًا (LLM)، يمكنك الحصول على تصحيحات نحوية فورية وكتابة النتيجة المصقولة مباشرةً في الملف.

في هذا الدرس سنستعرض العملية بالكامل: قراءة ملف `.docx` باستخدام **load docx in c#**، استدعاء **how to use llm** لتصحيح القواعد، وأخيرًا حفظ المستند المنقح. في النهاية ستحصل على تطبيق console جاهز للتنفيذ يقوم بالضبط ما تحتاجه—بدون نسخ ولصق يدوي، بدون واجهات برمجة تطبيقات خارجية، فقط C# صافية ونقطة نهاية LLM محلية.

> **ما ستحتاجه**
> - .NET 6.0 أو أحدث (الكود يعمل أيضًا على .NET Framework، لكن .NET 6 هو الخيار المثالي)
> - مكتبة [Aspose.Words for .NET](https://products.aspose.com/words/net/) (الإصدار التجريبي المجاني يكفي للاختبار)
> - خادم LLM يعمل ويعرض نقطة نهاية بسيطة `CheckGrammar(string)` (مثل Ollama، LM Studio، أو غلاف FastAPI مخصص)
> - إلمام أساسي بـ async/await (اختياري لكن يُنصح به)

إذا كنت تتساءل **لماذا قد يهمك هذا**، فكر في الوقت الذي تقضيه في تصحيح الأخطاء يدويًا في التقارير المُولدة. أتمتة هذه الخطوة لا تُسرّع الأنابيب فقط بل تضمن التناسق عبر العشرات من المستندات. لنبدأ.

---

## نظرة عامة على فحص القواعد النحوية

قبل أن نتعمق، إليك خارطة طريق سريعة:

1. **إنشاء عميل** يتواصل مع نقطة نهاية LLM المحلية.  
2. **قراءة مستند Word** باستخدام Aspose.Words—هذه هي الطريقة الكلاسيكية لـ **read word document text** في C#.  
3. **إرسال النص الأصلي** إلى LLM واستلام نسخة مصححة.  
4. **استبدال المحتوى الأصلي** في المستند بالنص المصحح.  
5. **حفظ** الملف المحدث (اختياري لكن عادةً مطلوب).

كل خطوة مغلفة في دالة خاصة بها بحيث يمكنك إعادة استخدامها أو استبدالها لاحقًا. يظهر الكود الكامل في نهاية المقال.

---

## الخطوة 1: إعداد عميل LLM (How to Use LLM)

للحفاظ على النظافة، سنغلف استدعاء HTTP في فئة صغيرة. تفترض هذه الفئة أن خدمة LLM تقبل طلب POST مع حمولة JSON `{ "prompt": "..."} ` وتعيد `{ "response": "..." }`. عدّل التسلسل إذا كانت خدمتك تختلف.

```csharp
using System.Net.Http;
using System.Text;
using System.Text.Json;
using System.Threading.Tasks;

/// <summary>
/// Minimal client for a local LLM that offers a grammar‑checking endpoint.
/// </summary>
public class LocalLargeLanguageModel
{
    private readonly HttpClient _http;
    private readonly string _baseUrl;

    public LocalLargeLanguageModel(string baseUrl)
    {
        _baseUrl = baseUrl.TrimEnd('/');
        _http = new HttpClient();
    }

    /// <summary>
    /// Sends the input text to the LLM and returns the corrected version.
    /// </summary>
    public async Task<string> CheckGrammarAsync(string input)
    {
        var payload = new { prompt = $"Correct the grammar and punctuation:\n\n{input}" };
        var content = new StringContent(JsonSerializer.Serialize(payload), Encoding.UTF8, "application/json");

        // The endpoint is assumed to be /grammar
        var response = await _http.PostAsync($"{_baseUrl}/grammar", content);
        response.EnsureSuccessStatusCode();

        var json = await response.Content.ReadAsStringAsync();
        var result = JsonSerializer.Deserialize<Dictionary<string, string>>(json);
        return result != null && result.TryGetValue("response", out var corrected) ? corrected : input;
    }
}
```

**لماذا هذا مهم:**  
- **فصل المسؤوليات** – إذا قمت لاحقًا بالتبديل من Ollama إلى LM Studio، كل ما عليك تغييره هو عنوان URL أو تنسيق الحمولة.  
- **متوافق مع Async** – عمليات الإدخال/الإخراج الشبكية لن تحجب واجهة المستخدم أو العامل الخلفي.  
- **معالجة الأخطاء** – `EnsureSuccessStatusCode` يرمي استثناءً واضحًا إذا كان LLM غير متاح، وسنتعامل معه لاحقًا.

> **نصيحة احترافية:** إذا كان LLM يعمل على GPU، حافظ على حجم الطلب أقل من ~4 KB لتجنب ارتفاعات الكمون.

---

## الخطوة 2: تحميل DOCX واستخراج النص (Read Word Document Text)

تجعل Aspose.Words قراءة ملفات Word أمرًا سهلًا. تُعيد الدالة `Document.GetText()` النص المرئي بالكامل، مع الحفاظ على فواصل الأسطر. إذا كنت تحتاج إلى تنسيق أغنى (جداول، حواشي)، سيتوجب عليك استكشاف شجرة العقد، لكن لفحص القواعد النحوية فقط النص العادي يكفي.

```csharp
using Aspose.Words;

/// <summary>
/// Loads a .docx file and returns its raw textual content.
/// </summary>
public static string ReadDocumentText(string filePath)
{
    if (!File.Exists(filePath))
        throw new FileNotFoundException($"Document not found: {filePath}");

    var doc = new Document(filePath);
    return doc.GetText(); // Returns text with line breaks
}
```

**ملاحظة حول الحالات الحدية:**  
إذا كان المستند يحتوي على أحرف غير إنجليزية أو رموز خاصة، تأكد من أن نموذج LLM الذي تستخدمه يدعم Unicode. معظم النماذج الحديثة تدعم ذلك، لكن النماذج القديمة قد تقص أو تفسّرها بشكل خاطئ.

---

## الخطوة 3: استبدال المحتوى بالنص المصحح

لا توفر Aspose.Words طريقة سطر واحد “استبدال كامل النص”؛ لكن مسح شجرة العقد وإدراج فقرة واحدة يعمل بشكل جيد. هذا يضمن أيضًا إزالة أي علامات مخفية (مثل التغييرات المتتبعة).

```csharp
/// <summary>
/// Overwrites the document with the supplied corrected text.
/// </summary>
public static void WriteCorrectedText(string filePath, string correctedText)
{
    var doc = new Document(filePath);
    doc.RemoveAllChildren(); // Clears sections, paragraphs, tables, etc.

    var builder = new DocumentBuilder(doc);
    builder.Writeln(correctedText); // Writes as a single paragraph; you can split by "\n" if you want multiple paragraphs.

    doc.Save(filePath); // Overwrites the original file
}
```

**لماذا نزيل جميع الأطفال:**  
- يضمن بداية نظيفة، مما يمنع بقايا التنسيق من التدخل مع المحتوى الجديد.  
- يبسط الكود—لا حاجة للبحث عن عقد محددة لاستبدالها.

إذا كنت تفضّل الحفاظ على العناوين الأصلية، يمكنك تحليل شجرة العقد الأصلية، استبدال عقد `Run` فقط، لكن ذلك يضيف تعقيدًا خارج نطاق هذا الدرس.

---

## الخطوة 4: ربط كل شيء معًا – مثال كامل يعمل

فيما يلي البرنامج الكامل لتطبيق console. يوضح **how to check grammar** من البداية إلى النهاية، بما في ذلك معالجة الأخطاء الأساسية ومعاملات سطر الأوامر الاختيارية.

```csharp
using System;
using System.IO;
using System.Threading.Tasks;
using Aspose.Words;

// Ensure you have a license or are okay with the evaluation watermark.
class Program
{
    // Adjust these paths to match your environment.
    private const string InputPath = @"YOUR_DIRECTORY\input.docx";
    private const string OutputPath = @"YOUR_DIRECTORY\output.docx";
    private const string LlmEndpoint = "http://localhost:5000";

    static async Task Main(string[] args)
    {
        try
        {
            // 1️⃣ Create the LLM client.
            var llm = new LocalLargeLanguageModel(LlmEndpoint);

            // 2️⃣ Load the DOCX and read its text.
            Console.WriteLine("Reading document...");
            string originalText = ReadDocumentText(InputPath);

            // 3️⃣ Send text to the LLM for grammar correction.
            Console.WriteLine("Sending text to LLM for grammar check...");
            string correctedText = await llm.CheckGrammarAsync(originalText);

            // 4️⃣ Write the corrected text back into a new file.
            Console.WriteLine("Writing corrected text to new document...");
            // We copy the original file first so the original remains untouched.
            File.Copy(InputPath, OutputPath, overwrite: true);
            WriteCorrectedText(OutputPath, correctedText);

            Console.WriteLine($"✅ Grammar check complete! Updated file saved to: {OutputPath}");
        }
        catch (Exception ex)
        {
            Console.Error.WriteLine($"❌ An error occurred: {ex.Message}");
            // For real‑world apps, consider logging the stack trace.
        }
    }

    // --- Helper methods from earlier steps ---
    public static string ReadDocumentText(string filePath)
    {
        if (!File.Exists(filePath))
            throw new FileNotFoundException($"Document not found: {filePath}");

        var doc = new Document(filePath);
        return doc.GetText();
    }

    public static void WriteCorrectedText(string filePath, string correctedText)
    {
        var doc = new Document(filePath);
        doc.RemoveAllChildren();

        var builder = new DocumentBuilder(doc);
        // Preserve line breaks by splitting and writing each line.
        foreach (var line in correctedText.Split(new[] { "\r\n", "\n" }, StringSplitOptions.None))
        {
            builder.Writeln(line);
        }

        doc.Save(filePath);
    }
}
```

### النتيجة المتوقعة

عند تشغيل البرنامج (`dotnet run`)، سيظهر في وحدة التحكم شيء مشابه لـ:

```
Reading document...
Sending text to LLM for grammar check...
Writing corrected text to new document...
✅ Grammar check complete! Updated file saved to: YOUR_DIRECTORY\output.docx
```

افتح `output.docx` في Word—سترى نفس المحتوى لكن مع تصحيح علامات الترقيم، توافق الفاعل والفعل، وأي أخطاء إملائية واضحة تم إصلاحها بواسطة LLM.

---

## أسئلة شائعة وحالات حدية

### ماذا لو أعاد LLM قيمة `null` أو سلسلة فارغة؟

طريقة `CheckGrammarAsync` تعود إلى النص الأصلي إذا كان حقل `response` مفقودًا في الحمولة. هذا يمنع مسح المستند عن طريق الخطأ.

### ما الحد الأقصى لحجم المستند قبل انتهاء المهلة؟

معظم خوادم LLM المحلية تتعامل مع بضعة آلاف من الأحرف بسهولة. للملفات الأكبر (مثلاً 100 KB+)، يُفضَّل تجزئة النص إلى فقرات، إرسال كل جزء على حدة، ثم إعادة تجميع القطع المصححة. حجم التجزئة ~2 KB يُعد نقطة انطلاق جيدة.

### هل يتم الحفاظ على الصور أو الجداول أو الحواشي؟

لا. عند مسح جميع الأطفال نفقد أي عناصر غير نصية. إذا كنت بحاجة للحفاظ عليها، سيتوجب عليك استعراض شجرة العقد، استبدال عقد `Run` فقط (وهي أجزاء النص)، وترك العقد الأخرى دون تعديل. هذا سيناريو أكثر تقدماً—استكشف API الخاص بـ Aspose.Words لتعامل مع `NodeCollection`.

### هل يمكنني استخدام LLM سحابي بدلاً من المحلي؟

بالتأكيد. استبدل فقط عنوان URL وتنسيق الحمولة في `LocalLargeLanguageModel`. ضع في اعتبارك أن الخدمات السحابية غالبًا ما تفرض حدودًا على المعدل وتكلفة، بينما النموذج المحلي يعمل دون اتصال ومجاني بعد إعداد GPU/CPU الأولي.

---

## نصائح احترافية وأفضل الممارسات

- **احتفظ بالعميل في الذاكرة**: إعادة استخدام نفس كائن `HttpClient` يمنع

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}