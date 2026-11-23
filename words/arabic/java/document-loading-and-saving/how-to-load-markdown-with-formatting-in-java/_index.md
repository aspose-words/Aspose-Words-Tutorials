---
category: general
date: 2026-11-22
description: تعلم كيفية تحميل ملفات ماركداون مع التنسيق في جافا. يوضح لك هذا الدليل
  كيفية قراءة ملفات ماركداون مع التنسيق باستخدام LoadOptions و Document.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to load markdown
- read markdown with formatting
- Java markdown parsing
- LoadOptions import underline
- Document processing Java
language: ar
lastmod: 2026-11-22
og_description: كيفية تحميل ماركداون مع التنسيق في جافا. اتبع هذا الدليل الكامل لقراءة
  ماركداون مع التنسيق، والحفاظ على أنماط التسطير، والعمل مع كائنات Document.
og_image_alt: Java code snippet showing markdown loading with formatting enabled
og_title: كيفية تحميل ماركداون مع التنسيق في جافا – دليل خطوة بخطوة
schemas:
- author: GroupDocs
  dateModified: '2026-11-22'
  description: Learn how to load markdown with formatting in Java. This guide shows
    you how to read markdown with formatting using LoadOptions and Document.
  headline: How to load markdown with formatting in Java
  type: TechArticle
tags:
- markdown
- java
- document-processing
title: كيفية تحميل ماركداون مع التنسيق في جافا
url: /ar/java/document-loading-and-saving/how-to-load-markdown-with-formatting-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# كيفية تحميل markdown مع التنسيق في Java

إذا كنت بحاجة إلى **كيفية تحميل markdown** مع الحفاظ على أنماطه البصرية، فإن هذا الدليل يقدم لك حلاً جاهزًا للتنفيذ. ستشاهد بالضبط كيف **تقرا markdown مع التنسيق** مثل النص المسطر، بحيث يتطابق المستند المعروض مع المصدر الأصلي.

الدليل يغطي كل خطوة من تكوين المحمل إلى التحقق من بقاء التنسيق بعد الاستيراد. لا توجد أدوات خارجية مطلوبة بخلاف مكتبة GroupDocs.Viewer القياسية (أو أي API متوافق يوفر `LoadOptions` و `Document`). في النهاية يمكنك دمج تحميل markdown في أي خلفية Java، خدمة ويب، أو تطبيق سطح مكتب.

## المتطلبات المسبقة

قبل أن تبدأ، تأكد من أن لديك:

* Java 17 أو أحدث مثبت.
* Maven أو Gradle لإدارة الاعتمادات.
* الوصول إلى ملف JAR الخاص بـ GroupDocs.Viewer (أو ما يعادله) الذي يحتوي على `LoadOptions` و `Document`.
* ملف markdown تجريبي (`sample.md`) يتضمن تعليمات تسطير (مثلاً `<u>underlined text</u>` أو `_underlined_` حسب المحلل).

## الخطوة 1: إضافة الاعتماد المطلوب

إذا كنت تستخدم Maven، أضف ما يلي إلى ملف `pom.xml` الخاص بك. عدّل الإصدار إلى أحدث إصدار ثابت.

```xml
<dependency>
    <groupId>com.groupdocs</groupId>
    <artifactId>groupdocs-viewer</artifactId>
    <version>23.12</version>
</dependency>
```

يمكن لمستخدمي Gradle إضافة:

```groovy
implementation 'com.groupdocs:groupdocs-viewer:23.12'
```

إضافة المكتبة تجعل كلا من فئتي `LoadOptions` و `Document` متاحتين أثناء التجميع.

## الخطوة 2: تكوين LoadOptions لاستيراد تنسيق التسطير

كائن `LoadOptions` يخبر المحلل أي ميزات markdown يجب الحفاظ عليها. تمكين تنسيق التسطير يضمن ظهور النمط البصري في الـ `Document` الناتج.

```java
import com.groupdocs.viewer.options.LoadOptions;

/**
 * Creates a LoadOptions instance with underline import enabled.
 *
 * @return configured LoadOptions
 */
private static LoadOptions createLoadOptions() {
    LoadOptions loadOptions = new LoadOptions();
    // Preserve underline markup when the markdown is parsed.
    loadOptions.setImportUnderlineFormatting(true);
    return loadOptions;
}
```

**لماذا هذا مهم:**  
بدون `setImportUnderlineFormatting(true)`، يقوم المحلل بإزالة وسوم التسطير، تاركًا النص عاديًا. تمكين العلامة يحافظ على النمط كما هو، وهو أمر أساسي عندما يعتمد المستهلك اللاحق (مثل مولد PDF) على الإشارات البصرية.

## الخطوة 3: تحميل مستند markdown باستخدام الخيارات المكوّنة

الآن يمكنك قراءة ملف markdown. يُقبل مُنشئ `Document` مسار الملف و`LoadOptions` التي أعددتها للتو.

```java
import com.groupdocs.viewer.Document;
import com.groupdocs.viewer.options.LoadOptions;

/**
 * Loads a markdown file while preserving formatting.
 *
 * @param markdownPath absolute or relative path to the .md file
 * @param options      LoadOptions with formatting flags
 * @return Document representing the parsed markdown
 */
private static Document loadMarkdown(String markdownPath, LoadOptions options) {
    return new Document(markdownPath, options);
}
```

**لماذا هذا مهم:**  
تمرير `LoadOptions` إلى مُنشئ `Document` يضمن أن المحلل يحترم علامة التسطير طوال عملية الاستيراد بالكامل. يمكن بعد ذلك عرض كائن `Document` أو تحويله أو فحصه مع الحفاظ على كامل التنسيق.

## الخطوة 4: التحقق من بقاء تنسيق التسطير

طريقة سريعة لتأكيد وجود التسطير هي تحويل المستند إلى HTML وطباعة الناتج. سيحتوي HTML على وسوم `<u>` إذا نجح الاستيراد.

```java
import com.groupdocs.viewer.options.HtmlViewOptions;
import com.groupdocs.viewer.Viewer;

/**
 * Renders the loaded Document to HTML and prints the first page.
 *
 * @param doc Document loaded from markdown
 */
private static void renderAndPrint(Document doc) {
    // Create a Viewer instance for rendering.
    Viewer viewer = new Viewer(doc);
    // Render the first page as HTML.
    HtmlViewOptions viewOptions = HtmlViewOptions.forEmbeddedResources();
    viewer.view(viewOptions, 1);
    String html = viewOptions.getHtmlContent();

    System.out.println("Rendered HTML snippet:");
    System.out.println(html.substring(0, Math.min(html.length(), 500)));
}
```

تشغيل البرنامج الكامل يجب أن يعرض مقطع HTML يتضمن `<u>underlined text</u>`. إذا كان الوسم مفقودًا، تحقق مرة أخرى من استدعاء `setImportUnderlineFormatting(true)` قبل تحميل الملف.

## مثال كامل قابل للتنفيذ

بجمع كل شيء معًا، إليك فئة Java مستقلة يمكنك تجميعها وتنفيذها:

```java
import com.groupdocs.viewer.Document;
import com.groupdocs.viewer.Viewer;
import com.groupdocs.viewer.options.HtmlViewOptions;
import com.groupdocs.viewer.options.LoadOptions;

/**
 * Demonstrates how to load markdown with formatting in Java.
 * The program reads a markdown file, preserves underline markup,
 * renders the first page to HTML, and prints a snippet.
 */
public class MarkdownLoader {

    public static void main(String[] args) {
        // Path to the markdown file – adjust as needed.
        String markdownPath = "sample.md";

        // Step 1: create LoadOptions with underline support.
        LoadOptions options = createLoadOptions();

        // Step 2: load the markdown document.
        Document doc = loadMarkdown(markdownPath, options);

        // Step 3: render the document to HTML and verify formatting.
        renderAndPrint(doc);
    }

    private static LoadOptions createLoadOptions() {
        LoadOptions loadOptions = new LoadOptions();
        loadOptions.setImportUnderlineFormatting(true);
        return loadOptions;
    }

    private static Document loadMarkdown(String path, LoadOptions options) {
        return new Document(path, options);
    }

    private static void renderAndPrint(Document doc) {
        Viewer viewer = new Viewer(doc);
        HtmlViewOptions viewOptions = HtmlViewOptions.forEmbeddedResources();
        viewer.view(viewOptions, 1); // render first page
        String html = viewOptions.getHtmlContent();

        System.out.println("Rendered HTML snippet:");
        System.out.println(html.substring(0, Math.min(html.length(), 500)));
    }
}
```

**الناتج المتوقع (مقتطع للوضوح):**

```
Rendered HTML snippet:
<div class="page">
  <p>This is a <u>underlined text</u> example from the markdown file.</p>
  …
```

إذا ظهر وسوم `<u>`، فقد تم تحميل markdown مع الحفاظ على التنسيق.

## تنوعات شائعة وحالات حافة

| الحالة                                 | ما الذي يجب تغييره                                            |
|----------------------------------------|--------------------------------------------------------------|
| **امتدادات markdown المختلفة**          | استخدم `loadOptions.setImportBoldFormatting(true)` لتطبيق **الخط العريض**. |
| **ملفات كبيرة (> 10 MB)**              | قم ببث الملف باستخدام `FileInputStream` ومرّر الدفق إلى `Document`. |
| **الحاجة إلى إخراج PDF**                | بعد التحميل، استخدم `PdfViewOptions` مع `Viewer` لإنشاء PDF يحافظ على أنماط التسطير. |
| **التشغيل في حاوية servlet**           | احفظ الـ `Document` في نطاق الطلب وقم بعرضه كـ HTML مباشرة. |

**نصيحة احترافية:** دائمًا أنشئ نسخة جديدة من `LoadOptions` لكل عملية تحميل. إعادة استخدام نفس الكائن عبر الخيوط قد يؤدي إلى تسرب حالة غير متوقع.

## الخلاصة

أنت الآن تعرف **كيفية تحميل markdown مع التنسيق في Java** وكيفية **قراءة markdown مع التنسيق** باستخدام `LoadOptions`. المثال الكامل يوضح التكوين، التحميل، والتحقق، بحيث يمكنك دمج هذا النمط في أي مشروع Java يعالج ملفات markdown.

بعد ذلك، استكشف المواضيع ذات الصلة مثل **قراءة markdown مع الصور**، **تحويل markdown إلى PDF**، أو **تخصيص استيراد أنماط أخرى** (عريض، مائل، شطب). كل من هذه الإضافات يتبع نفس النمط: عدّل علامات `LoadOptions`، حمّل الـ `Document`، واعرضه بالتنسيق المطلوب.

برمجة سعيدة!

## ما الذي يجب أن تتعلمه بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات الموضحة في هذا الدليل. كل مصدر يتضمن أمثلة شفرة كاملة مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف نهج تنفيذ بديلة في مشاريعك الخاصة.

- [كيفية تحميل مستند markdown في Java مع خيارات استيراد مخصصة](/words/english/java/document-loading-and-saving/how-to-load-markdown-document-in-java-with-custom-import-opt/)
- [كيفية قراءة وتحميل ملف Markdown في Java باستخدام Aspose.Words](/words/english/java/document-loading-and-saving/how-to-read-markdown-file-java-with-aspose-words/)
- [كيفية تحميل Markdown في Java – دليل كامل](/words/english/java/document-loading-and-saving/how-to-load-markdown-in-java-complete-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}