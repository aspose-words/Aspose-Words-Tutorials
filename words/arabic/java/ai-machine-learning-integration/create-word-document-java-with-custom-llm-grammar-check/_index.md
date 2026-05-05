---
category: general
date: 2026-05-04
description: إنشاء مستند Word في Java باستخدام Aspose.Words وتعلم كيفية فحص القواعد
  النحوية باستخدام نموذج لغة كبير مخصص. دليل خطوة بخطوة لمطوري Java.
draft: false
keywords:
- create word document java
- how to create docx
- how to check grammar
- use custom llm
language: ar
og_description: إنشاء مستند Word باستخدام Java ومعرفة كيفية فحص القواعد النحوية باستخدام
  نموذج لغة مخصص. دليل Java كامل مع كود قابل للتنفيذ.
og_title: إنشاء مستند Word باستخدام Java مع فحص القواعد اللغوية المخصص للـ LLM
tags:
- Java
- Aspose.Words
- LLM
title: إنشاء مستند Word بلغة Java مع فحص القواعد اللغوية المخصص للـ LLM
url: /ar/java/ai-machine-learning-integration/create-word-document-java-with-custom-llm-grammar-check/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# إنشاء مستند Word باستخدام Java مع فحص القواعد المخصص LLM

هل تساءلت يومًا كيف يمكنك **إنشاء مستند word java** يراجع نفسه تلقائيًا؟ لست وحدك—العديد من المطورين يرغبون في خط أنابيب واحد ينتج ملف *.docx* مصقول دون الحاجة إلى أدوات متعددة. في هذا الدرس سنستعرض ذلك خطوة بخطوة، موضحين لك **كيفية إنشاء ملفات docx** باستخدام Aspose.Words، وربط خادم LLM محلي، وأخيرًا **كيفية فحص القواعد** تلقائيًا. بحلول النهاية ستحصل على برنامج Java مستقل يكتب، يتحقق، ويحفظ مستند Word—كل ذلك باستخدام **نقاط نهاية LLM مخصصة** تتحكم فيها.

## ما ستحتاجه

قبل أن نبدأ، تأكد من وجود ما يلي على جهازك:

| المتطلب | لماذا هو مهم |
|--------------|----------------|
| Java 17+ (أو أي JDK حديث) | ميزات لغة حديثة ودعم أفضل للوحدات |
| Aspose.Words for Java (أحدث نسخة) | المكتبة التي تتيح لك **إنشاء مستند word java** برمجيًا |
| خادم LLM محلي (مثل Ollama، LMStudio) يستمع على `http://localhost:11434/api/generate` | مطلوب لخطوة **استخدام LLM مخصص** التي تقوم بفحص القواعد |
| Maven أو Gradle (سنستخدم Maven في الأمثلة) | يبسط إدارة الاعتمادات |
| بيئة تطوير أو محرر نصوص (IntelliJ IDEA، VS Code، إلخ) | يجعل كتابة الكود وتصحيح الأخطاء أسهل |

إذا كان أي من هذه غير مألوف لك، لا تقلق—كل عنصر مجاني أو لديه نسخة مجتمع تعمل بشكل ممتاز لأغراض التعلم.

## الخطوة 1 – إعداد مشروع Maven الخاص بك

لـ **إنشاء مستند word java** بسرعة، ابدأ بملف Maven بسيط `pom.xml`. هذا الملف يجلب مكتبة Aspose.Words وأي عميل HTTP تفضله (سنستخدم Apache HttpClient).

```xml
<!-- pom.xml -->
<project xmlns="http://maven.apache.org/POM/4.0.0" 
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 
                             http://maven.apache.org/xsd/maven-4.0.0.xsd">
    <modelVersion>4.0.0</modelVersion>

    <groupId>com.example</groupId>
    <artifactId>word-llm-demo</artifactId>
    <version>1.0.0</version>
    <properties>
        <maven.compiler.source>17</maven.compiler.source>
        <maven.compiler.target>17</maven.compiler.target>
    </properties>

    <dependencies>
        <!-- Aspose.Words for Java -->
        <dependency>
            <groupId>com.aspose</groupId>
            <artifactId>aspose-words</artifactId>
            <version>24.9</version> <!-- replace with the latest -->
        </dependency>

        <!-- Apache HttpClient for calling the LLM endpoint -->
        <dependency>
            <groupId>org.apache.httpcomponents.client5</groupId>
            <artifactId>httpclient5</artifactId>
            <version>5.2</version>
        </dependency>
    </dependencies>
</project>
```

> **نصيحة احترافية:** إذا كنت تستخدم Gradle، فإن نفس الاعتمادات توضع تحت `implementation` في `build.gradle`.

الآن شغّل `mvn clean install` لجلب الـ jars. بمجرد نجاح البناء، ستكون جاهزًا لكتابة كود Java الذي **ينشئ مستندات word java**.

## الخطوة 2 – كتابة الفئة Java التي **تنشئ مستند word java**

فيما يلي الملف المصدر الكامل الجاهز للتنفيذ. يوضح التدفق الكامل: تهيئة مستند فارغ، ضبط نقطة نهاية LLM مخصصة، استدعاء فحص القواعد، وأخيرًا حفظ النتيجة.

```java
package com.example.wordllmdemo;

import com.aspose.words.*;
import com.aspose.words.ai.*;

import java.io.IOException;
import java.nio.file.Files;
import java.nio.file.Path;

/**
 * Demonstrates how to create a Word document in Java and run a grammar‑check
 * using a self‑hosted LLM (e.g., Ollama). This example is fully self‑contained
 * and can be executed with a single `java -cp` command after Maven builds.
 */
public class SelfHostedLLMDemo {

    public static void main(String[] args) throws Exception {
        // -----------------------------------------------------------------
        // Step 2.1 – Create an empty Word document
        // -----------------------------------------------------------------
        Document document = new Document(); // this is the object that will become your .docx

        // Add a simple paragraph so the grammar engine has something to work with
        DocumentBuilder builder = new DocumentBuilder(document);
        builder.writeln("Ths sentence has a typo and a grammer error.");

        // -----------------------------------------------------------------
        // Step 2.2 – Configure the custom LLM endpoint (use custom llm)
        // -----------------------------------------------------------------
        AiEndpoint llmEndpoint = new AiEndpoint();
        llmEndpoint.setBaseUrl("http://localhost:11434/api/generate");
        llmEndpoint.setModel("llama3.1:8b"); // make sure this model is available locally

        // Initialise the Document AI engine with the endpoint we just set up
        DocumentAi documentAi = new DocumentAi(llmEndpoint);

        // -----------------------------------------------------------------
        // Step 2.3 – Run grammar checking (how to check grammar)
        // -----------------------------------------------------------------
        // AiModelType.CUSTOM tells the API to forward the request to our LLM
        documentAi.checkGrammar(document, AiModelType.CUSTOM);

        // -----------------------------------------------------------------
        // Step 2.4 – Save the corrected file
        // -----------------------------------------------------------------
        String outputPath = "output/GrammarChecked.docx";
        // Ensure the directory exists
        Files.createDirectories(Path.of("output"));
        document.save(outputPath);
        System.out.println("Document saved to " + outputPath);
    }
}
```

> **لماذا يعمل هذا:**  
> * `Document` هو الفئة الأساسية في Aspose.Words التي تمثل ملف *.docx* في الذاكرة.  
> * `AiEndpoint` يحدد لموديول AI في Aspose أين يرسل الطلب. بتوجيهه إلى `localhost:11434` نحن **نستخدم LLM مخصص** بدلاً من خدمة سحابية.  
> * `checkGrammar` مع `AiModelType.CUSTOM` يرسل نص المستند إلى الـ LLM، يستقبل النص المصحح، ويعيد كتابة عقد Word الداخلية.  
> * أخيرًا نستدعي `save` لكتابة الملف على القرص، لتحصل على ملف Word مصقول.

### النتيجة المتوقعة

بعد تشغيل `mvn exec:java -Dexec.mainClass="com.example.wordllmdemo.SelfHostedLLMDemo"` يجب أن ترى:

```
Document saved to output/GrammarChecked.docx
```

افتح الملف الناتج `GrammarChecked.docx` في Microsoft Word (أو LibreOffice). الجملة الأصلية *“Ths sentence has a typo and a grammer error.”* ستصبح الآن *“This sentence has a typo and a grammar error.”* – دليل على نجاح خطوة **كيفية فحص القواعد**.

## الخطوة 3 – كيفية إنشاء docx بمحتوى مختلف (اختياري)

إذا رغبت في توليد مستندات أغنى—جداول، صور، أو نص منسق—استمر في استخدام `DocumentBuilder`. إليك مقتطف سريع يوضح إضافة عنوان وجدول:

```java
// Adding a heading
builder.getParagraphFormat().setStyleIdentifier(StyleIdentifier.HEADING_1);
builder.writeln("Demo Report");

// Adding a 2x2 table
Table table = builder.startTable();
builder.insertCell();
builder.write("Item");
builder.insertCell();
builder.write("Quantity");
builder.endRow();

builder.insertCell();
builder.write("Apples");
builder.insertCell();
builder.write("42");
builder.endRow();
builder.endTable();
```

يمكنك وضع هذا الكود في أي مكان بين كتلة إنشاء المستند (الخطوة 2.1) واستدعاء فحص القواعد (الخطوة 2.3). سيستقبل الـ LLM النص الكامل، لذا يمكنه تصحيح أي جزء نصي طبيعي مع ترك الجداول دون تعديل.

## الخطوة 4 – التعامل مع مشاكل نقاط النهاية (استخدام LLM مخصص بأمان)

عند **استخدام LLM مخصص**، تظهر بعض المشكلات الشائعة:

| العَرَض | السبب المحتمل | الحل |
|---------|--------------|-----|
| خطأ `Connection refused` | خادم LLM غير مشغل أو المنفذ غير صحيح | شغّل Ollama (`ollama serve`) وتأكد من أن `http://localhost:11434/api/generate` يعمل باستخدام `curl`. |
| استجابة JSON تفتقد حقل `completion` | اسم النموذج غير متطابق | تأكد من أن النموذج المحدد (`llama3.1:8b`) مثبت (`ollama list`). |
| فحص القواعد يُعيد النص الأصلي دون تغيير | الطلب غير مفهوم للـ LLM | عدّل نظام النموذج |

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}