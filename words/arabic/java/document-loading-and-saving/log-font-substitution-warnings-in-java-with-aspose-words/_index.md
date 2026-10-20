---
category: general
date: 2026-06-17
description: سجّل تحذيرات استبدال الخطوط في جافا باستخدام Aspose.Words – التقط الخطوط
  المفقودة أثناء تحميل المستند وحافظ على تناسق المخرجات.
draft: false
keywords:
- log font substitution warnings
- Aspose.Words Java
- font substitution
- warning callback
- LoadOptions
- document loading
language: ar
og_description: سجّل تحذيرات استبدال الخطوط في جافا باستخدام Aspose.Words. تعلّم كيفية
  التقاط تنبيهات الخطوط المفقودة أثناء تحميل المستند وحافظ على ملفات PDF الخاصة بك
  خالية من العيوب.
og_title: تسجيل تحذيرات استبدال الخطوط في جافا – دليل كامل
schemas:
- author: Aspose
  dateModified: '2026-06-17'
  description: Log font substitution warnings in Java using Aspose.Words – capture
    missing fonts during document load and keep your output consistent.
  headline: Log Font Substitution Warnings in Java with Aspose.Words
  type: TechArticle
- description: Log font substitution warnings in Java using Aspose.Words – capture
    missing fonts during document load and keep your output consistent.
  name: Log Font Substitution Warnings in Java with Aspose.Words
  steps:
  - name: Prerequisites
    text: '- Java 8 or newer (the code works with Java 11+ as well). - Aspose.Words
      for Java library (version 23.10 or later is recommended). - A sample `.docx`
      that references a font not installed on your machine (e.g., `MissingFont.docx`).'
  - name: Logging to a File Instead of the Console
    text: 'If you prefer a persistent log, replace the `System.out.println` call with
      a `FileWriter`:'
  - name: Capturing Multiple Documents in a Loop
    text: 'When processing a folder of documents, you can reuse the same callback:'
  - name: Dealing with Embedded Fonts
    text: 'Aspose.Words can embed missing fonts if you enable it:'
  type: HowTo
tags:
- Java
- Aspose.Words
- Document Processing
title: تسجيل تحذيرات استبدال الخطوط في جافا باستخدام Aspose.Words
url: /ar/java/document-loading-and-saving/log-font-substitution-warnings-in-java-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# تسجيل تحذيرات استبدال الخطوط في Java – دليل كامل

هل تساءلت يومًا كيف **تسجل تحذيرات استبدال الخطوط** عندما يقوم مستند Word بسحب خط غير موجود على الخادم؟ لست الوحيد الذي يحك رأسه بسبب الخطوط المفقودة التي يتم استبدالها بصمت. الخبر السار؟ Aspose.Words for Java توفر لك طريقة نظيفة لالتقاط تلك الاستبدالات في اللحظة التي يتم فيها تحميل المستند.

في هذا الدرس سنستعرض مثالًا عمليًا يوضح بالضبط كيفية تسجيل رد نداء تحذير، وتصفية تنبيهات استبدال الخطوط، وكتابتها إلى وحدة التحكم (أو أي مسجل تفضله). في النهاية ستحصل على مقتطف قابل لإعادة الاستخدام يمكنك إدراجه في أي مشروع Java يستخدم **Aspose.Words Java**.

## ما ستتعلمه

- كيفية تكوين **LoadOptions** لالتقاط التحذيرات.
- كيفية تنفيذ **IWarningCallback** الذي يتفاعل فقط مع أحداث **font substitution**.
- كيفية تحميل مستند بأمان مع الحفاظ على سجل تدقيق واضح للخطوط المفقودة.
- نصائح لتوسيع الحل إلى سجلات ملفية أو أنظمة مراقبة.

### المتطلبات المسبقة

- Java 8 أو أحدث (الكود يعمل مع Java 11+ أيضًا).
- مكتبة Aspose.Words for Java (الإصدار 23.10 أو أحدث يُنصح به).
- ملف `.docx` تجريبي يشير إلى خط غير مثبت على جهازك (مثال: `MissingFont.docx`).

لا توجد أطر إضافية مطلوبة—فقط Java عادي وملفات Aspose.JAR.

---

## الخطوة 1: تكوين LoadOptions لـ Aspose.Words Java

قبل أن تتمكن من اعتراض أي تحذير، تحتاج إلى كائن **LoadOptions**. هذا الكائن يخبر Aspose.Words كيف يتصرف أثناء تحليل الملف الوارد.

```java
// Step 1: Create LoadOptions to enable warning capture
LoadOptions loadOptions = new LoadOptions();
```

لماذا هذه الخطوة حاسمة؟ بدون كائن `LoadOptions`، تقوم المكتبة باستبدال الخطوط المفقودة بصمت ولن ترى أي أثر. بإنشاءه صراحةً، تفتح الباب أمام **رد نداء تحذير** مخصص يمكنه تسجيل ما يهمك بالضبط.

> **نصيحة احترافية:** إذا كنت تقوم بتحميل العديد من المستندات دفعة واحدة، أعد استخدام كائن `LoadOptions` واحد لتجنب إنشاء كائنات غير ضرورية.

---

## الخطوة 2: تنفيذ رد نداء تحذير لاستبدال الخطوط

تأتي Aspose.Words مع واجهة `IWarningCallback`. تنفيذها يتيح لك تحديد ما يجب فعله عندما يرفع المحرك `WarningInfo`. في حالتنا، نريد فقط التفاعل مع `WarningType.FONT_SUBSTITUTION`.

```java
// Step 2: Register a warning callback that logs only font‑substitution warnings
loadOptions.setWarningCallback(new IWarningCallback() {
    @Override
    public void warning(WarningInfo info) {
        // Filter for font‑substitution warnings only
        if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
            // Simple console output – replace with a logger if you prefer
            System.out.println("Font substitution: " + info.getMessage());
        }
    }
});
```

بعض النقاط التي يجب ملاحظتها:

1. **التصفية** – جملة `if` تضمن أننا نتجاهل التحذيرات غير المتعلقة (مثل مشاكل التخطيط) ونحافظ على نظافة السجل.
2. **سلامة الخيوط** – رد النداء يعمل على نفس الخيط الذي يحمل المستند، لذا لا تحتاج إلى مزامنة إضافية لإخراج بسيط إلى وحدة التحكم. إذا كتبت إلى مسجل مشترك، تأكد من أنه آمن للخيوط.
3. **قابلية التوسيع** – هل تريد الكتابة إلى ملف؟ استبدل `System.out.println` بـ `java.util.logging.Logger` أو إطار تسجيل تابع لجهة خارجية.

---

## الخطوة 3: تحميل المستند باستخدام الخيارات المكوَّنة

الآن بعد أن تم إعداد رد النداء، قم بتحميل ملف Word الخاص بك. في اللحظة التي يقوم فيها Aspose.Words بتحليل المستند، سيؤدي أي خط مفقود إلى تشغيل رد النداء المحدد أعلاه.

```java
// Step 3: Load the document with the warning‑aware LoadOptions
Document doc = new Document("YOUR_DIRECTORY/MissingFont.docx", loadOptions);
```

إذا كان الملف المصدر يشير إلى خط غير مثبت، سترى مخرجات مشابهة لـ:

```
Font substitution: Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
```

ذلك السطر هو **تحذيرات استبدال الخطوط المسجلة** التي كنت تبحث عنها. يمكنك الآن اتخاذ إجراء بناءً عليه—ربما تنبه المستخدم، أو تبدل إلى ورقة أنماط احتياطية، أو ببساطة تحتفظ بسجل للامتثال.

---

## الخطوة 4: متابعة المعالجة العادية

بعد التحميل، يتصرف المستند كأي كائن `Document` آخر. لا تتردد في فحص الأقسام، استخراج النص، أو التحويل إلى PDF. يتم تسجيل التحذيرات تلقائيًا أثناء خطوة التحميل، لذا لا تحتاج إلى كود إضافي.

```java
// Example: Print the number of sections – just to prove the doc is usable
System.out.println("Document has " + doc.getSections().getCount() + " sections.");
```

ستظهر وحدة التحكم الآن كلًا من تحذير استبدال الخط (إن وجد) **والعدد** الأقسام، مما يؤكد أن المستند يعمل بشكل كامل.

---

## نصائح متقدمة وحالات حافة

### تسجيل إلى ملف بدلاً من وحدة التحكم

إذا كنت تفضل سجلًا دائمًا، استبدل استدعاء `System.out.println` بـ `FileWriter`:

```java
private static final String LOG_PATH = "logs/font_substitutions.txt";

loadOptions.setWarningCallback(new IWarningCallback() {
    @Override
    public void warning(WarningInfo info) {
        if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
            try (FileWriter fw = new FileWriter(LOG_PATH, true)) {
                fw.write("Font substitution: " + info.getMessage() + System.lineSeparator());
            } catch (IOException e) {
                e.printStackTrace();
            }
        }
    }
});
```

تذكر معالجة `IOException` بشكل صحيح في كود الإنتاج.

### التقاط مستندات متعددة في حلقة

عند معالجة مجلد من المستندات، يمكنك إعادة استخدام نفس رد النداء:

```java
File[] files = new File("input").listFiles((dir, name) -> name.endsWith(".docx"));
for (File f : files) {
    Document d = new Document(f.getAbsolutePath(), loadOptions);
    // Additional processing...
}
```

نظرًا لأن رد النداء مرتبط بـ `loadOptions`، فإن كل تكرار يسجل تلقائيًا أي أحداث استبدال الخط.

### التعامل مع الخطوط المدمجة

يمكن لـ Aspose.Words تضمين الخطوط المفقودة إذا قمت بتمكين ذلك:

```java
loadOptions.setLoadFormat(LoadFormat.DOCX);
loadOptions.setEnableFontSubstitution(true); // default is true
```

حتى مع تمكين التضمين، لا يزال رد النداء للتنبيه يعمل، مما يمنحك رؤية لما تم استبداله.

---

## مثال كامل يعمل

فيما يلي البرنامج الكامل الجاهز للتنفيذ. انسخه في فئة تسمى `FontSubstitutionDiagnostics.java`، عدل مسار الملف، ثم نفذ.

```java
import com.aspose.words.*;

import java.io.FileWriter;
import java.io.IOException;

/**
 * Demonstrates how to log font substitution warnings using Aspose.Words for Java.
 */
public class FontSubstitutionDiagnostics {

    // Optional: path to a persistent log file
    private static final String LOG_FILE = "font_substitution_log.txt";

    public static void main(String[] args) throws Exception {
        // 1️⃣ Create LoadOptions to capture warnings
        LoadOptions loadOptions = new LoadOptions();

        // 2️⃣ Register a warning callback that logs only font‑substitution warnings
        loadOptions.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) {
                if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                    String message = "Font substitution: " + info.getMessage();
                    // Log to console
                    System.out.println(message);
                    // Also append to a file (optional)
                    try (FileWriter fw = new FileWriter(LOG_FILE, true)) {
                        fw.write(message + System.lineSeparator());
                    } catch (IOException e) {
                        // In a real app, use a proper logging framework
                        e.printStackTrace();
                    }
                }
            }
        });

        // 3️⃣ Load the document with the configured LoadOptions
        Document doc = new Document("YOUR_DIRECTORY/MissingFont.docx", loadOptions);

        // 4️⃣ Continue normal processing – e.g., print section count
        System.out.println("Document has " + doc.getSections().getCount() + " sections.");
    }
}
```

**المخرجات المتوقعة** (بافتراض أن المستند المصدر يشير إلى خط مفقود):

```
Font substitution: Font 'Times New Roman' was not found. Substituted with 'Arial'.
Document has 3 sections.
```

ستحتوي كل من وحدة التحكم وملف `font_substitution_log.txt` على التحذير، مما يمنحك سجل تدقيق موثوق.

---

## الخلاصة

لقد أوضحنا لك الآن كيفية **تسجيل تحذيرات استبدال الخطوط** في Java باستخدام Aspose.Words. من خلال تكوين `LoadOptions`، وربط `IWarningCallback`، وتحميل المستند، تحصل على رؤية كاملة لأي أحداث خطوط مفقودة قد تمر دون ملاحظة. من هنا يمكنك:

- توجيه التحذيرات إلى خدمة تسجيل مركزية.
- إطلاق تنبيهات لخطوط أنابيب مراقبة الجودة.
- دمج هذه التقنية مع استراتيجيات **تحميل المستندات** أخرى، مثل تحويل PDF أو دمج البريد.

لا تتردد في التجربة—استبدل مسجل وحدة التحكم بـ SLF4J، أضف طوابع زمنية، أو حتى ادفع التنبيهات إلى لوحة مراقبة. يبقى النمط الأساسي هو نفسه، والآن لديك أساس قوي للتعامل مع الخطوط في أي سير عمل مستندات مبني على Java.

هل لديك تعديل ترغب في مشاركته؟ ربما قمت بدمج هذا مع Spring Boot أو وظيفة سحابية. اترك تعليقًا أدناه، ولنستمر في النقاش. ترميز سعيد!

## ماذا يجب أن تتعلم بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات الموضحة في هذا الدليل. كل مورد يتضمن أمثلة كود كاملة مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف أساليب تنفيذ بديلة في مشاريعك.

- [Capture Font Substitution Warnings in Java with Aspose.Words – Complete Guide](/words/english/java/document-loading-and-saving/capture-font-substitution-warnings-in-java-with-aspose-words/)
- [Using Document Options and Settings in Aspose.Words for Java](/words/english/java/document-manipulation/using-document-options-and-settings/)
- [Enable Font Substitution Warnings in Aspose.Words – Complete Guide](/words/english/net/working-with-fonts/enable-font-substitution-warnings-in-aspose-words-complete-g/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}