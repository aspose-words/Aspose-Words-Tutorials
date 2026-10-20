---
category: general
date: 2026-03-04
description: كيفية تكوين نموذج اللغة الكبيرة (LLM) للذكاء الاصطناعي المستندات واستبدال
  النص في ملفات DOCX باستخدام الذكاء الاصطناعي – دليل خطوة بخطوة مع كود Java كامل.
draft: false
keywords:
- how to configure llm
- replace text in docx
- how to replace text
- how to use document ai
- replace phrase with ai
language: ar
og_description: How to configure LLM for Document AI and replace text in DOCX using
  AI – complete guide with runnable Java code.
og_title: كيفية تكوين نموذج اللغة الكبيرة – استبدال النص في ملف DOCX باستخدام الذكاء
  الاصطناعي
tags:
- LLM
- Document AI
- Java
- DOCX
title: How to Configure LLM – Replace Text in DOCX with AI
url: /ar/java/ai-machine-learning-integration/how-to-configure-llm-replace-text-in-docx-with-ai/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# كيفية تكوين LLM – استبدال النص في DOCX باستخدام الذكاء الاصطناعي

هل تساءلت يومًا **كيف يمكنك تكوين LLM** ليتمكن من تعديل ملف Word لك؟ لست وحدك. يواجه العديد من المطورين صعوبة عندما يحتاجون إلى استبدال عبارة داخل ملف `.docx` برمجيًا دون فتح Microsoft Word. الخبر السار؟ باستخدام LLM محلي وطبقة تغليف صغيرة تُسمى Document AI، يمكنك استبدال النص في ملف DOCX ببضع أسطر من Java فقط.

في هذا الدرس سنستعرض العملية بالكامل: من إعداد اتصال LLM، تحميل ملف DOCX، إلى استخدام **Document AI** لاستبدال العبارة المستهدفة. في النهاية ستحصل على مثال كامل، قابل للتنفيذ، يمكنك إدراجه في أي مشروع Maven أو Gradle. لا مفاتيح API خارجية، لا رسوم سحابة—فقط نموذجك الخاص المستمع على `http://localhost:8080/v1`.

> **فوز سريع:** إذا كان لديك LLM محلي (مثل Llama 3 أو Mistral) يُظهر نقطة نهاية متوافقة مع OpenAI، فإن الشيفرة أدناه تعمل مباشرةً.

---

![Diagram of how to configure LLM for Document AI](/images/configure-llm-diagram.png){: .center-image alt="how to configure llm diagram"}

## ما ستحتاجه

- **Java 17** (أو أي JDK حديث)  
- **LLM محلي** يُظهر نقطة نهاية على نمط OpenAI `/v1` (مثل Ollama، LMStudio)  
- مكتبة **Document AI Java** (افترض `com.example:document-ai:1.2.0` على Maven Central)  
- ملف DOCX تجريبي (`input.docx`) موجود في مجلد معروف  

إذا كان أحد هذه العناصر غير متوفر، يمكنك تشغيل Ollama بسرعة:

```bash
ollama serve &
ollama run llama3
```

سيبدأ ذلك خادمًا على `http://localhost:8080/v1` جاهزًا لاستقبال الطلبات.

---

## كيفية تكوين LLM لـ Document AI

أول شيء نفعله هو إخبار عميل `DocumentAi` بمكان العثور على النموذج وأي نموذج نريد استخدامه. هذه هي خطوة **كيفية تكوين LLM** التي تتجاهلها العديد من الدروس.

```java
// Step 1: Set up the LLM connection details
AiModelConfig modelConfig = new AiModelConfig();
modelConfig.setBaseUrl("http://localhost:8080/v1");   // Local server address
modelConfig.setApiKey("dummy");                       // Not needed for local models, but the client expects a value
modelConfig.setModelName("local-llm");                // Replace with your model's identifier
```

*لماذا هذا مهم:*  
كائن `AiModelConfig` يُجرد تفاصيل HTTP، مما يسمح لـ `DocumentAi` بالتركيز على المحتوى. إذا قررت الانتقال إلى مزود مستضاف، كل ما عليك تغييره هو `baseUrl` و `apiKey`—وبقية الشيفرة تبقى كما هي.

---

## تحميل وتحضير مستند DOCX

بعد ذلك نقوم بقراءة ملف Word إلى الذاكرة. تتعامل فئة `Document` مع كل من `.docx` و`.pdf` في الخلفية، لكننا هنا نهتم بـ DOCX فقط.

```java
// Step 2: Load the DOCX you want to edit
Path docPath = Paths.get("YOUR_DIRECTORY/input.docx");
Document inputDocument = new Document(docPath.toFile());
```

*نصيحة احترافية:* استخدم مسارًا مطلقًا أثناء عملية التصحيح لتجنب مفاجأة “الملف غير موجود”. بمجرد أن تتأكد من عمل الشيفرة، عد إلى مسار نسبي لزيادة القابلية للنقل.

---

## استبدال النص في DOCX باستخدام الذكاء الاصطناعي

الآن نصل إلى جوهر الدرس—**كيفية استبدال النص** في ملف DOCX بمساعدة الذكاء الاصطناعي. تُرسل طريقة `replaceText` محتويات المستند إلى LLM، تطلب منه إجراء الاستبدال، وتعيد النص المعدل.

```java
// Step 3: Initialise the Document AI client
DocumentAi documentAi = new DocumentAi(modelConfig);

// Step 4: Ask the LLM to replace the target phrase
String oldPhrase = "old phrase";
String newPhrase = "new phrase";

String revisedText = documentAi.replaceText(
        inputDocument,
        oldPhrase,
        newPhrase
);
```

*ما الذي يحدث خلف الكواليس؟*  
يقوم `DocumentAi` بتحويل DOCX إلى نص عادي، ثم يُنشئ مطالبة مثل:

> “في المستند التالي، استبدل كل ظهور لعبارة ‘old phrase’ بعبارة ‘new phrase’ وأعد النص المحدث فقط.”

يعالج LLM الطلب ويعيد المحتوى المعدل. يعمل هذا النهج حتى عندما تمتد العبارة عبر عدة تشغيلات أو فقرات—وهو ما قد يفوّته استبدال السلاسل النصية البسيط.

---

## التحقق وإخراج النص المعدل

أخيرًا نطبع النص الذي عدّله الذكاء الاصطناعي إلى وحدة التحكم. في تطبيق واقعي قد تقوم بكتابة النتيجة إلى ملف DOCX جديد، لكن الطباعة تسمح بالتحقق السريع.

```java
// Step 5: Show the AI‑revised output
System.out.println("AI‑revised text:");
System.out.println("-----------------------------------");
System.out.println(revisedText);
```

**الناتج المتوقع** (بافتراض أن DOCX الأصلي يحتوي على “This is the old phrase we want to change.”):

```
AI‑revised text:
-----------------------------------
This is the new phrase we want to change.
```

إذا رأيت العبارة الجديدة تظهر، تهانينا—**لقد تعلمت الآن كيفية استخدام Document AI لاستبدال عبارة باستخدام الذكاء الاصطناعي**.

---

## مثال كامل يعمل

بدمج كل ما سبق، إليك فئة Java كاملة جاهزة للتنفيذ. يمكنك نسخها ولصقها في `src/main/java/com/example/ReplaceInDocx.java`.

```java
package com.example;

import com.example.documentai.AiModelConfig;
import com.example.documentai.DocumentAi;
import com.example.documentai.Document;

import java.nio.file.Path;
import java.nio.file.Paths;

/**
 * Demonstrates how to configure LLM, load a DOCX, and replace a phrase using Document AI.
 */
public class ReplaceInDocx {

    public static void main(String[] args) {
        // 1️⃣ Configure the local LLM connection
        AiModelConfig modelConfig = new AiModelConfig();
        modelConfig.setBaseUrl("http://localhost:8080/v1");
        modelConfig.setApiKey("dummy");               // Not required for local models
        modelConfig.setModelName("local-llm");        // Change if needed

        // 2️⃣ Load the DOCX you want to modify
        Path docPath = Paths.get("YOUR_DIRECTORY/input.docx");
        Document inputDocument = new Document(docPath.toFile());

        // 3️⃣ Create the Document AI client using the configuration
        DocumentAi documentAi = new DocumentAi(modelConfig);

        // 4️⃣ Replace the target phrase with the new phrase using the AI model
        String oldPhrase = "old phrase";
        String newPhrase = "new phrase";

        String revisedText = documentAi.replaceText(
                inputDocument,
                oldPhrase,
                newPhrase
        );

        // 5️⃣ Output the AI‑revised text
        System.out.println("AI‑revised text:");
        System.out.println("-----------------------------------");
        System.out.println(revisedText);
    }
}
```

### كيفية التشغيل

```bash
# Compile
mvn clean compile

# Execute
mvn exec:java -Dexec.mainClass="com.example.ReplaceInDocx"
```

تأكد من أن خادم LLM يعمل قبل تشغيل البرنامج؛ وإلا ستحصل على مهلة اتصال.

---

## الحالات الحدية والمشكلات الشائعة

| الحالة | ما يجب مراقبته | الحل المقترح |
|--------|----------------|--------------|
| **العبارة غير موجودة** | يُعيد LLM النص الأصلي دون تغيير. | تحقق من الإملاء وحساسية الأحرف؛ يمكنك إضافة `ignoreCase:true` إلى المطالبة إذا كان الغلاف يدعم ذلك. |
| **مستندات كبيرة (>5 MB)** | قد يتجاوز حجم المطالبة حد توكنات النموذج. | قسّم DOCX إلى أقسام، عالج كل قسم على حدة، ثم اجمع النتائج. |
| **LLM محلي يُعيد أخطاء** | غالبًا بسبب اسم نموذج غير متطابق. | تحقق من أن اسم النموذج في واجهة LLM (`ollama list`) يطابق ما تم تعيينه في `modelConfig.setModelName`. |
| **حروف Unicode مشوهة** | مشاكل ترميز عند قراءة DOCX. | تأكد من أن بيئة تشغيل Java تستخدم UTF‑8 (أضف `-Dfile.encoding=UTF-8` إلى وسائط JVM). |

---

## الخطوات التالية

الآن بعد أن عرفت **كيفية استبدال النص في DOCX** باستخدام الذكاء الاصطناعي، قد ترغب في استكشاف:

- **كيفية استخدام Document AI** لمهام أكثر تعقيدًا مثل استخراج الجداول أو الحفاظ على الأنماط.  
- **استبدال العبارة باستخدام AI** في ملفات PDF عبر تغيير معامل مُنشئ `Document`.  
- **المعالجة الدفعية**: حلقة تمر على مجلد من ملفات DOCX وتطبق نفس الاستبدال.  

كل هذه تبني على نفس أساس `AiModelConfig` و `DocumentAi`، لذا لن تحتاج إلى البدء من الصفر.

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}