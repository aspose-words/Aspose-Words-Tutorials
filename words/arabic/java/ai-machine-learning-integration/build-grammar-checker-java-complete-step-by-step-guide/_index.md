---
category: general
date: 2026-05-23
description: أنشئ مدقق قواعد اللغة بجافا مع موفر نموذج مخصص. تعلّم كيفية تحميل مستند
  وورد بجافا وتعيين موفر النموذج المخصص في بضع خطوات فقط.
draft: false
keywords:
- build grammar checker java
- load word document java
- set custom model provider
- AI grammar validation java
- custom LLM integration java
language: ar
og_description: إنشاء مدقق قواعد اللغة في جافا باستخدام نموذج لغوي محلي. يوضح هذا
  الدليل كيفية تحميل مستند وورد في جافا وتعيين مزود نموذج مخصص للفحوصات المدفوعة بالذكاء
  الاصطناعي.
og_title: إنشاء مدقق القواعد النحوية Java – دليل كامل
schemas:
- author: Aspose
  dateModified: '2026-05-23'
  description: Build grammar checker java with a custom model provider. Learn how
    to load word document java and set custom model provider in just a few steps.
  headline: Build Grammar Checker Java – Complete Step‑by‑Step Guide
  type: TechArticle
tags:
- Java
- Grammar Checker
- AI
- Document Processing
title: بناء مدقق القواعد النحوية بلغة جافا – دليل كامل خطوة بخطوة
url: /ar/java/ai-machine-learning-integration/build-grammar-checker-java-complete-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# بناء مدقق قواعد اللغة Java – دليل خطوة‑بخطوة كامل

هل تساءلت يوماً كيف **تبني مدقق قواعد اللغة Java** يعمل محليًا دون إرسال نصك إلى واجهة برمجة تطبيقات طرف ثالث؟ لست وحدك. في العديد من المؤسسات لا يمكن للبيانات مغادرة الموقع، لذا فإن نموذج اللغة المستضاف ذاتيًا هو الطريق الوحيد القابل للتنفيذ. يوضح هذا الدرس بالضبط كيفية تحميل مستند Word، وربط موفر نموذج LLM مخصص، وتشغيل فحص قواعد اللغة المدعوم بالذكاء الاصطناعي—كل ذلك باستخدام Java النقي.

سنستعرض كل سطر، نشرح لماذا كل جزء مهم، ونقدم لك مثالًا جاهزًا للتنفيذ يمكنك إدراجه في مشروعك اليوم. بنهاية الدرس ستحصل على مدقق قواعد لغة يعمل يمكنك توسيعه لتغطية أدلة الأسلوب، المصطلحات المتخصصة، أو حتى الدعم متعدد اللغات.

---

## ما ستتعلمه

- **Load Word document java** – قراءة ملفات `.docx` باستخدام Aspose.Words (أو أي مكتبة متوافقة).
- **Set custom model provider** – تنفيذ `ITextGenerationProvider` لتوصيل نموذج LLM مستضاف محليًا.
- **Build grammar checker java** – ربط كل المكونات معًا باستخدام `DocumentGrammarChecker` ومعالجة النتائج.
- نصائح إضافية حول معالجة المستندات الكبيرة، تخصيص المطالبات، وحل المشكلات الشائعة.

> **المتطلبات المسبقة**  
> • Java 17 أو أحدث (يستخدم الكود كلمة المفتاح الحديثة `var` للتقليل).  
> • Maven أو Gradle لإدارة الاعتمادات.  
> • نموذج LLM يعمل محليًا ويعرض نقطة نهاية HTTP بسيطة (مثل Ollama، Llama.cpp، أو خادم خاص متوافق مع OpenAI).  

إذا كنت مرتاحًا مع أساسيات صياغة Java، فأنت جاهز للبدء.

---

## مخطط سير العمل
![مخطط يوضح سير عمل بناء مدقق قواعد اللغة Java – تحميل مستند Word، تمرير النص إلى موفر نموذج مخصص، وتقرير مشاكل القواعد](https://example.com/diagram-build-grammar-checker-java.png)

---

## الخطوة 1 – تحميل مستند Word Java

الشيء الأول الذي تحتاجه هو كائن `Document` يمثل ملف `.docx` الذي تريد تحليله. أدناه نستخدم **Aspose.Words for Java**، مكتبة شائعة يمكنها قراءة وتعديل وحفظ ملفات Word دون الحاجة إلى تثبيت Microsoft Office.

```java
// Import statements
import com.aspose.words.Document;
import com.aspose.words.License;

// Load the document you want to check
var docPath = "YOUR_DIRECTORY/input.docx";
Document doc = new Document(docPath);
System.out.println("Document loaded: " + docPath);
```

**لماذا هذا مهم:**  
- `Document` يج abstracts تنسيق الملف، مما يمنحك وصولًا سهلًا إلى الفقرات والجداول وحتى البيانات الوصفية المخفية.  
- بتحميل المستند مبكرًا، يمكنك لاحقًا استخراج النص الخام أو العمل على عقد محددة (مثل محتوى النص فقط، متجاهلًا رؤوس الأقسام).  

**حالة حافة:** إذا كان الملف ضخمًا (أكبر من 100 ميغابايت)، فكر في تدفق المحتوى أو استخدام `doc.getPageCount()` لمعالجة الصفحات واحدةً تلو الأخرى والحفاظ على استهلاك الذاكرة منخفضًا.

---

## الخطوة 2 – تنفيذ موفر نموذج مخصص

`ITextGenerationProvider` هو العقد الذي يتوقعه محرك القواعد لأي نموذج ذكاء اصطناعي. تنفيذ هذا العقد يتيح لك **تعيين موفر نموذج مخصص** وتوجيه المدقق إلى نموذج LLM الخاص بك.

```java
import com.example.ai.ITextGenerationProvider;
import java.net.http.*;
import java.net.URI;
import java.time.Duration;

// Step 2: Implement a local LLM provider that conforms to ITextGenerationProvider
class MyLocalProvider implements ITextGenerationProvider {
    private final HttpClient client = HttpClient.newBuilder()
            .connectTimeout(Duration.ofSeconds(10))
            .build();

    private final String endpoint = "http://localhost:11434/api/generate";

    @Override
    public String generate(String prompt) {
        // Build a minimal JSON payload – most LLM APIs accept this shape
        String json = "{\"model\":\"my-llm\",\"prompt\":\"" + prompt + "\"}";

        HttpRequest request = HttpRequest.newBuilder()
                .uri(URI.create(endpoint))
                .header("Content-Type", "application/json")
                .POST(HttpRequest.BodyPublishers.ofString(json))
                .build();

        try {
            HttpResponse<String> response = client.send(request, HttpResponse.BodyHandlers.ofString());
            // Assume the API returns {"response":"..."} – adjust parsing as needed
            return parseResponse(response.body());
        } catch (Exception e) {
            // In production you’d have richer error handling
            throw new RuntimeException("LLM call failed", e);
        }
    }

    private String parseResponse(String body) {
        // Very naive extraction – replace with a proper JSON parser like Jackson
        int start = body.indexOf("\"response\":\"") + 12;
        int end = body.indexOf("\"", start);
        return body.substring(start, end);
    }
}
```

**لماذا هذا مهم:**  
- الموفر يج abstracts منطق **تعيين موفر نموذج مخصص**، مما يجعل باقي النظام غير معتمد على موقع النموذج.  
- استخدام `java.net.http.HttpClient` يقلل من الاعتمادات؛ يمكنك استبداله بـ Apache HttpClient إذا فضلت ذلك.  

**نصيحة احترافية:** خزن استجابة النموذج مؤقتًا للمطالبات المتطابقة داخل تشغيل واحد. هذا يسرّع الفحص للجمل المتكررة (مثل النصوص النموذجية).

---

## الخطوة 3 – تكوين خيارات الذكاء الاصطناعي مع موفرك

الآن نخبر محرك القواعد باستخدام الموفر الذي أنشأناه للتو. `AiOptions` يحمل إعدادات النموذج، درجة الحرارة، وغيرها من المعاملات.

```java
import com.example.ai.AiOptions;

// Step 3: Configure AI options to use the custom provider
AiOptions aiOptions = new AiOptions();
aiOptions.setModelProvider(new MyLocalProvider());
// Optional: tweak temperature for more deterministic output
aiOptions.setTemperature(0.2);
```

**لماذا هذا مهم:**  
- `AiOptions` يركز جميع إعدادات الذكاء الاصطناعي في مكان واحد، بحيث يمكنك تجربة موفرين مختلفين (OpenAI، Azure، أو موفرك الخاص) دون تعديل كود المدقق.  
- درجة حرارة منخفضة تجعل اقتراحات القواعد قابلة للتكرار، وهو أمر حاسم لخطوط أنابيب CI.

---

## الخطوة 4 – إنشاء كائن مدقق القواعد

مع وجود المستند وإعدادات الذكاء الاصطناعي جاهزة، نقوم بإنشاء كائن المدقق.

```java
import com.example.ai.DocumentGrammarChecker;

// Step 4: Create a grammar checker with the configured AI options
DocumentGrammarChecker grammarChecker = new DocumentGrammarChecker(aiOptions);
```

**لماذا هذا مهم:**  
- المدقق يجمع منطق تجوال المستند مع توليد مطالبات الذكاء الاصطناعي.  
- كما يتعامل مع تجميع قطع النص لتظل ضمن حدود الرموز المسموح بها لمعظم نماذج LLM.

---

## الخطوة 5 – تشغيل فحص القواعد

الآن نصل إلى جوهر عملية **بناء مدقق قواعد اللغة Java**: تمرير المستند المحمل إلى المدقق وجمع المشكلات.

```java
import com.example.ai.GrammarIssue;
import java.util.List;

// Step 5: Run the grammar check on the loaded document
List<GrammarIssue> grammarIssues = grammarChecker.checkGrammar(doc);
System.out.println("Found " + grammarIssues.size() + " potential issues.");
```

**لماذا هذا مهم:**  
- `checkGrammar` يعيد قائمة من كائنات `GrammarIssue`، كل منها يحتوي على رسالة، موقع، وشدة.  
- يمكنك لاحقًا تصفية النتائج حسب الشدة أو تصديرها إلى تنسيق تقرير (CSV، JSON، إلخ).

---

## الخطوة 6 – عرض النتائج

أخيرًا، نقوم بالتكرار على المشكلات وطباعة النتائج. في تطبيق واقعي قد تقوم بتمييز ملف Word أو إرسال النتائج إلى لوحة تحكم.

```java
// Step 6: Output each identified grammar issue
for (GrammarIssue issue : grammarIssues) {
    System.out.println("Location: " + issue.getLocation());
    System.out.println("Message : " + issue.getMessage());
    System.out.println("---");
}
```

**نموذج الإخراج** (افترض جملة بسيطة تفتقد أداة تعريف):

```
Location: Paragraph 3, Run 2
Message : Consider adding an article before "sunrise" – "the sunrise" sounds more natural.
---
Location: Table 1, Cell (2,1)
Message : "Their" should be "They're" in this context.
---
```

---

## مثال كامل يعمل

فيما يلي البرنامج الكامل جاهز للنسخ واللصق. استبدل مسارات الملفات ونقطة نهاية LLM بالقيم الخاصة بك.

```java
// File: GrammarCheckerDemo.java
import com.aspose.words.Document;
import com.example.ai.*;

import java.net.http.*;
import java.net.URI;
import java.time.Duration;
import java.util.List;

public class GrammarCheckerDemo {

    // ---- Custom provider ----------------------------------------------------
    static class MyLocalProvider implements ITextGenerationProvider {
        private final HttpClient client = HttpClient.newBuilder()
                .connectTimeout(Duration.ofSeconds(10))
                .build();

        private final String endpoint = "http://localhost:11434/api/generate";

        @Override
        public String generate(String prompt) {
            String json = "{\"model\":\"my-llm\",\"prompt\":\"" + prompt + "\"}";
            HttpRequest request = HttpRequest.newBuilder()
                    .uri(URI.create(endpoint))
                    .header("Content-Type", "application/json")
                    .POST(HttpRequest.BodyPublishers.ofString(json))
                    .build();

            try {
                HttpResponse<String> response = client.send(request, HttpResponse.BodyHandlers.ofString());
                return parseResponse(response.body());
            } catch (Exception e) {
                throw new RuntimeException("LLM call failed", e);
            }
        }

        private String parseResponse(String body) {
            int start = body.indexOf("\"response\":\"") + 12;
            int end = body.indexOf("\"", start);
            return body.substring(start, end);
        }
    }

    // ---- Main ---------------------------------------------------------------
    public static void main(String[] args) {
        // 1️⃣ Load the Word document (load word document java)
        String docPath = "YOUR_DIRECTORY/input.docx";
        Document doc = new Document(docPath);
        System.out.println("✅ Document loaded: " + docPath);

        // 2️⃣ Configure AI with the custom provider (set custom model provider)
        AiOptions aiOptions = new AiOptions();
        aiOptions.setModelProvider(new MyLocalProvider());
        aiOptions.setTemperature(0.2);

        // 3️⃣ Initialise the grammar checker
        DocumentGrammarChecker grammarChecker = new DocumentGrammarChecker(aiOptions);

        // 4️⃣ Run the check
        List<GrammarIssue> issues = grammarChecker.checkGrammar(doc);
        System.out.println("🔍 Found " + issues.size() + " potential grammar issues.");

        // 5️⃣ Print results
        for (GrammarIssue issue : issues) {
            System.out.println("\nLocation: " + issue.getLocation());
            System.out.println("Message : " + issue.getMessage());
        }
    }
}
```

**تشغيل العرض التجريبي**

```bash
# Assuming Maven
mvn compile exec:java -Dexec.mainClass=GrammarCheckerDemo
```

سترى مخرجات الكونسول مشابهة للنموذج المعروض سابقًا.

---

## أسئلة شائعة ومشكلات محتملة

| السؤال | الجواب |
|----------|--------|
| *ماذا لو أعاد نموذج LLM الخاص بي JSON بحقل اسم مختلف؟* | عدّل `parseResponse` ليتطابق مع الحمولة الفعلية، أو استخدم مكتبة JSON مناسبة مثل Jackson لزيادة المتانة. |
| *هل يمكنني فحص ملفات PDF بدلاً من DOCX؟* | نعم – استخرج النص باستخدام Apache PDFBox، ومرّر السلسلة الخام إلى `grammarChecker.checkGrammar` (ستحتاج إلى غلاف يقبل نصًا عاديًا). |
| *كيف أحدّ من استهلاك الرموز لـ | |

---

## دروس ذات صلة

- [كيفية ضبط الاتجاه وتحميل ملفات النص باستخدام Aspose.Words for Java](/words/english/java/document-loading-and-saving/loading-text-files/)
- [كيفية تحميل مستندات RTF بترميز UTF-8 في Java باستخدام Aspose.Words](/words/english/java/document-operations/load-rtf-with-utf8-java-asposewords/)
- [Aspose.Words Java&#58; دليل شامل لمعالجة مستندات Word](/words/english/java/document-operations/aspose-words-java-master-word-processing/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}