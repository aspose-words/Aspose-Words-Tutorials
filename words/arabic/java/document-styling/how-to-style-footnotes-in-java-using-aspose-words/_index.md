---
category: general
date: 2026-10-07
description: كيفية تنسيق الحواشي في جافا – تعلم كيفية تغيير فاصل الحاشية، تعديل تنسيق
  فاصل الحاشية، وحفظ المستند بالحواشي المنسقة.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to style footnotes
- change footnote separator
- edit footnote separator
- format footnote separator
- access footnote separator
language: ar
lastmod: 2026-10-07
og_description: كيفية تنسيق الحواشي في جافا باستخدام Aspose.Words. يوضح هذا الدرس
  كيفية تغيير فاصل الحواشي، تعديل تنسيق فاصل الحواشي، وإنتاج مستند مصقول.
og_image_alt: Screenshot illustrating how to style footnotes in a Java Word processing
  example
og_title: كيفية تنسيق الحواشي في جافا – دليل برمجي كامل
schemas:
- author: Aspose
  dateModified: '2026-10-07'
  description: how to style footnotes in Java – learn to change footnote separator,
    edit footnote separator formatting, and save the document with styled footnotes.
  headline: how to style footnotes in Java using Aspose.Words
  type: TechArticle
- description: how to style footnotes in Java – learn to change footnote separator,
    edit footnote separator formatting, and save the document with styled footnotes.
  name: how to style footnotes in Java using Aspose.Words
  steps:
  - name: Load the source document.
    text: Load the source document.
  - name: Iterate through each footnote and **access footnote separator** runs.
    text: Iterate through each footnote and **access footnote separator** runs.
  - name: Apply the desired styling (bold, color, underline, etc.).
    text: Apply the desired styling (bold, color, underline, etc.).
  - name: Save the document with the updated footnote separator.
    text: Save the document with the updated footnote separator.
  type: HowTo
tags:
- Aspose.Words
- Java
- Word automation
title: كيفية تنسيق الحواشي السفلية في جافا باستخدام Aspose.Words
url: /ar/java/document-styling/how-to-style-footnotes-in-java-using-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# كيفية تنسيق الحواشي في Java باستخدام Aspose.Words

إذا كنت بحاجة إلى تنسيق الحواشي في مستند Word باستخدام Java، فإن هذا الدليل يوضح لك **كيفية تنسيق الحواشي** باستخدام Aspose.Words. ستتعلم كيفية تغيير فاصل الحاشية، تعديل تنسيق فاصل الحاشية، وحفظ المستند المعدل في بضع خطوات واضحة.

التعامل مع الحواشي غالبًا ما يعني تعديل خط الفاصل الذي يظهر بين النص الرئيسي وقائمة الحواشي. بحلول نهاية هذا الدليل، ستكون قادرًا على **الوصول إلى تشغيلات فاصل الحاشية**، تطبيق تنسيق غامق أو لون، والتحكم في المظهر العام للحواشي دون مغادرة بيئة التطوير المتكاملة (IDE).

## المتطلبات المسبقة

* تثبيت Java 17 أو أحدث.
* Maven 3.6+ (أو Gradle) لإدارة التبعيات.
* ترخيص صالح لـ Aspose.Words for Java (التقييم المجاني يعمل لهذا المثال).
* مستند Word مصدر يحتوي على حاشية واحدة على الأقل (مثال: `Footnotes.docx`).

هذه المتطلبات تضمن تشغيل الكود بسلاسة على بيئات Java الحديثة وتتيح لك التركيز على تقنية **كيفية تنسيق الحواشي** بدلاً من مشكلات الإعداد.

## كيفية تنسيق الحواشي – النهج العام

تتكون العملية من أربع مراحل منطقية:

1. تحميل المستند المصدر.
2. التكرار عبر كل حاشية و **الوصول إلى تشغيلات فاصل الحاشية**.
3. تطبيق التنسيق المطلوب (غامق، لون، تسطير، إلخ).
4. حفظ المستند مع فاصل الحاشية المحدث.

كل مرحلة تتطابق مباشرةً مع سطر من الكود، مما يجعل التنفيذ سهل المتابعة والتعديل.

## الخطوة 1: إعداد مشروع Maven

أنشئ مشروع Maven جديد (أو أضفه إلى مشروع موجود) وضمّن تبعية Aspose.Words:

```xml
<!-- pom.xml -->
<dependencies>
    <dependency>
        <groupId>com.aspose</groupId>
        <artifactId>aspose-words</artifactId>
        <version>24.10</version> <!-- Use the latest version -->
    </dependency>
</dependencies>
```

> **نصيحة احترافية:** حافظ على تحديث نسخة المكتبة؛ الإصدارات الأحدث تضيف إصلاحات للأخطاء المتعلقة بمعالجة الحواشي.

## الخطوة 2: تحميل المستند المصدر الذي يحتوي على الحواشي

```java
import com.aspose.words.*;

public class FootnoteStyler {
    public static void main(String[] args) throws Exception {
        // Load the Word file that has footnotes.
        Document doc = new Document("YOUR_DIRECTORY/Footnotes.docx");
```

كائن `Document` يمثل ملف Word بالكامل. تحميله هو الإجراء الأول الملموس في **كيفية تنسيق الحواشي**.

## الخطوة 3: التكرار عبر كل حاشية و **الوصول إلى فاصل الحاشية**

```java
        // Iterate through all footnotes in the document.
        for (Footnote footnote : (Iterable<Footnote>) doc.getFootnotes()) {
            // The separator is a Run that appears between the main text and the footnote list.
            Run separator = footnote.getSeparator();

            // Guard against unexpected null values (rare but possible with corrupted files).
            if (separator != null) {
                // Apply desired styling to the separator run.
                separator.getFont().setBold(true);          // change footnote separator to bold
                separator.getFont().setColor(Color.BLUE);   // optional: set a custom color
                separator.getFont().setUnderline(Underline.SINGLE);
            }
        }
```

في هذا الجزء نـ **نصل إلى تشغيلات فاصل الحاشية** عبر `footnote.getSeparator()`. كائن `Run` يمنحك تحكمًا كاملاً في تنسيق النص، مما يتيح لك **تغيير مظهر فاصل الحاشية** بسطر واحد من الكود.

### لماذا نستخدم `Footnote.getSeparator()`

* `Footnote.getSeparator()` يُعيد التشغيل الذي يحتوي على خط الفاصل.  
* هو نقطة الدخول الوحيدة في الـ API التي تسمح لك **بتعديل فاصل الحاشية** مباشرة.  
* تعديل خصائص `Font` للتشغيل يحدّث الفاصل البصري لجميع الحواشي التي تشترك في نفس النمط.

## الخطوة 4: (اختياري) تنسيق فاصل الاستمرار والإشعار

Word يتميّز بثلاثة أنواع من الفواصل:

| النوع                     | طريقة API                | حالة الاستخدام النموذجية |
|--------------------------|---------------------------|------------------|
| Primary separator        | `Footnote.getSeparator()` | فصل النص الرئيسي عن أول حاشية |
| Continuation separator   | `Footnote.getContinuationSeparator()` | فصل صفحات الحواشي اللاحقة |
| Continuation notice      | `Footnote.getContinuationNotice()` | إظهار نص “Continued…” في الصفحات اللاحقة |

إذا كنت ترغب أيضًا في **تنسيق فاصل الحاشية** لصفحات الاستمرار، أضف الشيفرة التالية داخل الحلقة:

```java
            // Continuation separator (optional)
            Run contSeparator = footnote.getContinuationSeparator();
            if (contSeparator != null) {
                contSeparator.getFont().setItalic(true);
                contSeparator.getFont().setSize(9);
            }

            // Continuation notice (optional)
            Run contNotice = footnote.getContinuationNotice();
            if (contNotice != null) {
                contNotice.getFont().setColor(Color.GRAY);
            }
```

تظهر هذه المقاطع كيف يمكنك **تعديل كائنات فاصل الحاشية** بما يتجاوز الخط الأساسي، مما يمنحك تحكمًا كاملاً في تخطيط الحواشي.

## الخطوة 5: حفظ المستند المعدل

```java
        // Save the document with the styled footnote separators.
        doc.save("YOUR_DIRECTORY/FootnotesStyled.docx");
    }
}
```

حفظ الملف يكتب جميع تغييرات التنسيق إلى القرص، مكملًا سير عمل **كيفية تنسيق الحواشي**.

## مثال كامل قابل للتنفيذ

جمع جميع الأجزاء معًا ينتج برنامجًا مستقلًا يمكنك نسخه، تجميعه، وتشغيله:

```java
import com.aspose.words.*;
import java.awt.Color;

/**
 * Demonstrates how to style footnotes in a Word document using Aspose.Words for Java.
 * The example loads a document, makes the footnote separator bold and blue,
 * optionally styles continuation elements, and saves the result.
 */
public class FootnoteStyler {
    public static void main(String[] args) throws Exception {
        // 1. Load the source document.
        Document doc = new Document("YOUR_DIRECTORY/Footnotes.docx");

        // 2. Iterate through each footnote.
        for (Footnote footnote : (Iterable<Footnote>) doc.getFootnotes()) {
            // 3a. Access and style the primary separator.
            Run separator = footnote.getSeparator();
            if (separator != null) {
                separator.getFont().setBold(true);          // change footnote separator
                separator.getFont().setColor(Color.BLUE);   // set a custom color
                separator.getFont().setUnderline(Underline.SINGLE);
            }

            // 3b. (Optional) Style continuation separator.
            Run contSeparator = footnote.getContinuationSeparator();
            if (contSeparator != null) {
                contSeparator.getFont().setItalic(true);
                contSeparator.getFont().setSize(9);
            }

            // 3c. (Optional) Style continuation notice.
            Run contNotice = footnote.getContinuationNotice();
            if (contNotice != null) {
                contNotice.getFont().setColor(Color.GRAY);
            }
        }

        // 4. Save the modified document.
        doc.save("YOUR_DIRECTORY/FootnotesStyled.docx");
    }
}
```

**الناتج المتوقع:** افتح `FootnotesStyled.docx` في Microsoft Word. يظهر خط الفاصل بين النص الرئيسي وقائمة الحواشي غامقًا، أزرق، ومُسطَّرًا. إذا كان المستند يحتوي على حواشي تمتد عبر صفحات متعددة، فسيكون فاصل الاستمرار مائلًا وأصغر، بينما سيظهر إشعار الاستمرار باللون الرمادي.

## أسئلة شائعة ومعالجة الحالات الخاصة

| السؤال | الجواب |
|----------|--------|
| *ماذا لو لم تحتوي الحاشية على فاصل؟* | `Footnote.getSeparator()` يُعيد `null`. يتحقق الكود من `null` قبل تطبيق التنسيق، مما يمنع حدوث `NullPointerException`. |
| *هل يمكنني تطبيق نمط مختلف فقط على أول حاشية؟* | نعم. أضف عدادًا داخل الحلقة وطبق تنسيقًا شرطيًا عندما يكون `index == 0`. |
| *هل يعمل هذا مع ملفات .doc؟* | Aspose.Words يدعم كل من `.doc` و `.docx`. حمّل المسار المناسب وتُطبق نفس استدعاءات API. |
| *كيف أستعيد النمط الأصلي؟* | احفظ الـ `Font` الأصلي |

## ما الذي يجب أن تتعلمه بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات الموضحة في هذا الدليل. كل مورد يتضمن أمثلة شفرة كاملة مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف أساليب تنفيذ بديلة في مشاريعك.

- [كيفية حفظ المستند كملف pdf باستخدام Aspose.Words for Java](/words/english/java/document-loading-and-saving/saving-documents-as-pdf/)
- [كيفية تغيير حدود الخلايا في الجداول – Aspose.Words for Java](/words/english/java/document-conversion-and-export/formatting-tables-and-table-styles/)
- [كيفية إضافة علامة مائية – تحويل المستند وتصديره باستخدام Aspose.Words for Java](/words/english/java/document-conversion-and-export/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}