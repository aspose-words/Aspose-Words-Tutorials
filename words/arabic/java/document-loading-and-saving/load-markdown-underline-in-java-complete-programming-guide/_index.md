---
category: general
date: 2026-08-04
description: تحميل تسطير ماركداون في جافا والحفاظ على تنسيق الماركداون أثناء تحميله
  إلى المستند. اتبع هذا الدليل خطوة بخطوة.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- load markdown underline
- load markdown into document
- preserve markdown formatting
language: ar
lastmod: 2026-08-04
og_description: حمّل تنسيق الخط السفلي للماركداون في جافا واحفظ تنسيق الماركداون.
  تعلّم كيفية تحميل الماركداون إلى المستند مع دعم كامل للخط السفلي.
og_image_alt: Diagram showing load markdown underline process
og_title: تحميل تسطير ماركداون في جافا – دليل خطوة بخطوة
schemas:
- author: GroupDocs
  dateModified: '2026-08-04'
  description: Load markdown underline in Java and preserve markdown formatting while
    loading markdown into document. Follow this step‑by‑step tutorial.
  headline: Load markdown underline in Java – complete programming guide
  type: TechArticle
- description: Load markdown underline in Java and preserve markdown formatting while
    loading markdown into document. Follow this step‑by‑step tutorial.
  name: Load markdown underline in Java – complete programming guide
  steps:
  - name: Create `LoadOptions` for the document
    text: '`LoadOptions` lets you customize how the library parses the source file.
      Creating a fresh instance gives you a clean slate for later settings.'
  - name: Enable detection of underline formatting while loading
    text: By default the viewer may ignore underline tags because they are less common
      in Markdown. Enabling this flag tells the parser to keep underline spans intact.
  - name: Load the Markdown file using the configured options
    text: Now you can load the file. Pass the `loadOptions` object to the `Document`
      constructor so the parser respects the underline flag.
  - name: Verify that underline formatting is preserved
    text: A quick sanity check helps you confirm that **preserve markdown formatting**
      worked. The following snippet prints the text of each paragraph and marks underlined
      fragments with a tilde (`~`) for visibility.
  type: HowTo
tags:
- markdown
- Java
- document-processing
title: تحميل تسطير ماركداون في جافا – دليل برمجي كامل
url: /ar/java/document-loading-and-saving/load-markdown-underline-in-java-complete-programming-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# تحميل تسطير markdown في Java – دليل برمجة شامل

إذا كنت بحاجة إلى **تحميل تسطير markdown** أثناء تحويل ملف Markdown إلى كائن `Document`، يوضح لك هذا الدليل بالضبط كيفية القيام بذلك. ستتعلم أيضًا كيفية **تحميل markdown إلى المستند** دون فقدان أي تنسيق تسطير، مما يضمن الحفاظ الكامل على تنسيق Markdown الأصلي.

يغطي البرنامج التعليمي كل ما تحتاجه: المكتبات المطلوبة، كل خطوة من خطوات التكوين، وكيفية التحقق من أن تنسيق التسطير نجى من الاستيراد. في النهاية ستحصل على مقتطف شفرة قابل لإعادة الاستخدام يمكنك إدراجه في أي مشروع Java.

## المتطلبات المسبقة

قبل أن تبدأ، تأكد من أن لديك:

- Java 17 أو أحدث مثبتة (المثال يستخدم نظام الوحدات الحديث)
- أحدث إصدار من **GroupDocs.Viewer** (أو مكتبة متوافقة توفر `LoadOptions` و `Document`)
- ملف Markdown (`sample.md`) يحتوي على نص مسطر، مثل `<u>underlined</u>` أو صيغة GitHub‑flavored `__underlined__`
- بيئة تطوير متكاملة مثل IntelliJ IDEA أو VS Code، رغم أن أي محرر نصوص سيؤدي الغرض

هذه المتطلبات تضمن تشغيل الشفرة دون إعدادات إضافية.

## دليل تحميل تسطير markdown – خطوة بخطوة

تتكون العملية من ثلاث إجراءات أساسية: إنشاء كائن `LoadOptions`، تمكين اكتشاف التسطير، وأخيرًا تحميل ملف Markdown باستخدام تلك الخيارات. يتم شرح كل خطوة أدناه.

### الخطوة 1: إنشاء `LoadOptions` للمستند

`LoadOptions` يتيح لك تخصيص طريقة تحليل المكتبة للملف المصدر. إنشاء نسخة جديدة يمنحك قاعدة نظيفة للإعدادات اللاحقة.

```java
import com.groupdocs.viewer.options.LoadOptions;

// Step 1: Create load options for the document
LoadOptions loadOptions = new LoadOptions();
```

كائن `LoadOptions` هو نقطة الدخول لجميع التعديلات المتعلقة بالاستيراد. ستستخدمه في الخطوة التالية لتفعيل اكتشاف التسطير.

### الخطوة 2: تمكين اكتشاف تنسيق التسطير أثناء التحميل

افتراضيًا قد يتجاهل العارض وسوم التسطير لأنها أقل شيوعًا في Markdown. تمكين هذه العلامة يخبر المحلل بالحفاظ على نطاقات التسطير دون تعديل.

```java
// Step 2: Enable detection of underline formatting while loading
loadOptions.setImportUnderlineFormatting(true);
```

إعداد `setImportUnderlineFormatting(true)` يضمن أن أي وسم HTML `<u>` أو صيغة GitHub‑flavored للتسطير تُترجم إلى نموذج `Document` كتنسيق تسطير. هذا هو الإجراء الأساسي الذي يجعل **load markdown underline** يعمل كما هو متوقع.

### الخطوة 3: تحميل ملف Markdown باستخدام الخيارات المكوَّنة

الآن يمكنك تحميل الملف. مرّر كائن `loadOptions` إلى مُنشئ `Document` حتى يحترم المحلل علامة التسطير.

```java
import com.groupdocs.viewer.Document;

// Step 3: Load the Markdown file using the configured options
Document markdownDoc = new Document("YOUR_DIRECTORY/sample.md", loadOptions);
```

عند انتهاء المُنشئ، يحتوي `markdownDoc` على تمثيل كامل في الذاكرة لمصدر Markdown، مع تضمين تشغيلات التسطير.

### الخطوة 4: التحقق من حفظ تنسيق التسطير

فحص سريع يساعدك على التأكد من أن **preserve markdown formatting** نجح. المقتطف التالي يطبع نص كل فقرة ويضع علامة `~` على المقاطع المسطرة لتوضيحها.

```java
import com.groupdocs.viewer.contents.Page;
import com.groupdocs.viewer.contents.Paragraph;
import com.groupdocs.viewer.contents.TextFragment;

for (Page page : markdownDoc.getPages()) {
    for (Paragraph paragraph : page.getParagraphs()) {
        StringBuilder line = new StringBuilder();
        for (TextFragment fragment : paragraph.getTextFragments()) {
            if (fragment.isUnderline()) {
                line.append("~").append(fragment.getText()).append("~");
            } else {
                line.append(fragment.getText());
            }
        }
        System.out.println(line.toString());
    }
}
```

**الناتج المتوقع** (بافتراض أن `sample.md` يحتوي على `This is __underlined__ text`):

```
This is ~underlined~ text
```

تشير العلامات المائلة إلى أن نمط التسطير نجى من الاستيراد، مما يؤكد أن عملية **load markdown into document** حافظت على التنسيق الأصلي.

## المشكلات الشائعة وكيفية تجنّبها

| Symptom | Cause | Fix |
|---|---|---|
| اختفاء التسطير بعد التحميل | `setImportUnderlineFormatting` ترك على القيمة الافتراضية `false` | تأكد من استدعاء `loadOptions.setImportUnderlineFormatting(true)` قبل إنشاء الـ `Document`. |
| جزء فقط من النص مسطر | خلط صيغ Markdown (مثل HTML `<u>` مع `__underline__`) | المكتبة تدعم كلا الصيغتين؛ تحقق من أن ملف المصدر يستخدم علامة تسطير موحدة. |
| فشل تحميل المستند | مسار الملف غير صحيح أو نقص في تبعيات المكتبة | استخدم مسارًا مطلقًا أو ضع `sample.md` نسبياً إلى دليل العمل؛ أدرج ملفات JAR الخاصة بالمشاهد على classpath. |

**نصيحة احترافية:** إذا كنت تحتاج أيضًا إلى الحفاظ على الأنماط الغامقة أو المائلة، فعّلها باستخدام `setImportBoldFormatting(true)` و `setImportItalicFormatting(true)` على التوالي. الجمع بين هذه العلامات يمنحك استيرادًا دقيقًا لمعظم أنماط Markdown الشائعة.

## مثال كامل قابل للتنفيذ

فيما يلي برنامج Java مستقل يجمع كل شيء معًا. انسخ الشفرة إلى ملف باسم `LoadMarkdownUnderlineDemo.java`، عدّل مسار الملف، وشغّله باستخدام `java LoadMarkdownUnderlineDemo`.

```java
import com.groupdocs.viewer.Document;
import com.groupdocs.viewer.contents.Page;
import com.groupdocs.viewer.contents.Paragraph;
import com.groupdocs.viewer.contents.TextFragment;
import com.groupdocs.viewer.options.LoadOptions;

public class LoadMarkdownUnderlineDemo {

    public static void main(String[] args) {
        // 1️⃣ Create load options
        LoadOptions loadOptions = new LoadOptions();

        // 2️⃣ Enable underline detection
        loadOptions.setImportUnderlineFormatting(true);

        // 3️⃣ Load the Markdown file
        Document markdownDoc = new Document("YOUR_DIRECTORY/sample.md", loadOptions);

        // 4️⃣ Print each paragraph, marking underlined text with ~
        for (Page page : markdownDoc.getPages()) {
            for (Paragraph paragraph : page.getParagraphs()) {
                StringBuilder line = new StringBuilder();
                for (TextFragment fragment : paragraph.getTextFragments()) {
                    if (fragment.isUnderline()) {
                        line.append("~").append(fragment.getText()).append("~");
                    } else {
                        line.append(fragment.getText());
                    }
                }
                System.out.println(line.toString());
            }
        }
    }
}
```

تشغيل البرنامج يطبع محتوى المستند مع علامات التسطير، مما يثبت أن ميزة **load markdown underline** تعمل وأنك تستطيع **preserve markdown formatting** طوال عملية الاستيراد.

## الخلاصة

أنت الآن تعرف كيف **load markdown underline** في Java، وكيف **load markdown into document** مع الحفاظ على التنسيق الأصلي، وكيف تتحقق من بقاء تنسيق التسطير سليمًا. يعمل هذا النهج مع أحدث إصدارات GroupDocs.Viewer ويمكن توسيعه لدعم ميزات Markdown إضافية مثل الغامق، المائل، والجداول.

بعد ذلك، استكشف المواضيع ذات الصلة مثل **preserve markdown formatting for tables**، **render Markdown to PDF**، أو **custom styling of imported Markdown elements**. عدّل علامات `LoadOptions` لتتناسب مع متطلبات التنسيق الدقيقة لتطبيقك، وستحصل على تحكم دقيق في كل خطوة استيراد. Happy coding!

## ما الذي يجب أن تتعلمه بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات الموضحة في هذا الدليل. كل مورد يتضمن أمثلة شفرة كاملة مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف أساليب تنفيذ بديلة في مشاريعك.

- [إتقان خيارات تحميل Markdown مع Aspose.Words for Java](/words/english/java/document-operations/master-markdown-load-options-aspose-words-java/)
- [إتقان خيارات تحميل Markdown Aspose Words Java](/words/german/java/document-operations/master-markdown-load-options-aspose-words-java/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}