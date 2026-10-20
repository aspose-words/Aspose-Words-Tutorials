---
category: general
date: 2026-09-11
description: تعلم كيفية تغيير تنسيق الحواشي السفلية في جافا باستخدام Aspose.Words.
  يوضح هذا الدليل كيفية تحرير الحاشية السفلية، وتحديث نمط الحاشية السفلية، وتعديل
  فاصل الحاشية السفلية.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- change footnote formatting
- how to edit footnote
- update footnote style
- modify footnote separator
language: ar
lastmod: 2026-09-11
og_description: غيّر تنسيق الحواشي في جافا باستخدام Aspose.Words. اتبع هذا الدليل
  الكامل لتعديل الحاشية، وتحديث نمط الحاشية، وتعديل فاصل الحاشية.
og_image_alt: Screenshot showing change footnote formatting in a Java editor
og_title: تغيير تنسيق الحواشي في جافا – دليل خطوة بخطوة
schemas:
- author: Aspose
  dateModified: '2026-09-11'
  description: Learn how to change footnote formatting in Java with Aspose.Words.
    This guide explains how to edit footnote, update footnote style, and modify footnote
    separator.
  headline: How to change footnote formatting in a Word document using Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- Footnote
- Document processing
title: كيفية تغيير تنسيق الحواشي السفلية في مستند Word باستخدام Java
url: /ar/java/formatting-styles/how-to-change-footnote-formatting-in-a-word-document-using-j/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# كيفية تغيير تنسيق الحاشية السفلية في مستند Word باستخدام Java

إذا كنت بحاجة إلى **تغيير تنسيق الحاشية السفلية** في مستند Word، فإن هذا الدليل يشرح لك الخطوات الدقيقة باستخدام Aspose.Words for Java. سواءً كنت تبني خط أنابيب للنشر أو تحتاج فقط إلى **كيفية تحرير مظهر الحاشية السفلية** برمجياً، فإن الحل أدناه يغطي كل شيء من تحميل الملف إلى حفظ النسخة المحدثة.

سوف تتعلم كيفية **تحديث نمط الحاشية السفلية**، وجعل فاصل الحاشية السفلية غامقًا، وحتى **تعديل خصائص فاصل الحاشية السفلية** مثل حجم الخط أو اللون. يفترض الدليل أن لديك معرفة أساسية بـ Java ورخصة صالحة لـ Aspose.Words for Java.

## المتطلبات المسبقة

قبل أن تبدأ، تأكد من أن لديك:

* Java 17 أو أحدث مثبت.
* Aspose.Words for Java (الإصدار 23.12 أو أحدث) مضاف إلى مسار الفئات (classpath) في مشروعك.
* مستند Word (`input.docx`) يحتوي على حاشية سفلية واحدة على الأقل.
* بيئة تطوير متكاملة (IDE) أو أداة بناء (Maven/Gradle) لتجميع وتشغيل الكود.

إذا لم تكن متأكدًا من كيفية إضافة Aspose.Words إلى مشروع Maven، فأدرج الاعتماد التالي في ملف `pom.xml` الخاص بك:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.12</version>
</dependency>
```

## تغيير تنسيق الحاشية السفلية باستخدام Aspose.Words for Java

جوهر الحل هو برنامج Java قصير يقوم بتحميل مستند، والوصول إلى فقرة فاصل الحاشية السفلية، وتغيير تنسيقها، ثم حفظ النتيجة. الكود مكتمل ذاتيًا، لذا يمكنك نسخه إلى فئة جديدة وتشغيله فورًا.

```java
import com.aspose.words.*;

public class ChangeFootnoteFormatting {
    public static void main(String[] args) throws Exception {
        // Step 1: Load the Word document
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // Step 2: Retrieve the footnote separator paragraph
        Paragraph footnoteSeparator = doc.getFootnoteSeparator();

        // Defensive check – the separator may be empty in some documents
        if (footnoteSeparator.getRuns().getCount() == 0) {
            // Create a new run so we have something to format
            Run run = new Run(doc);
            run.setText("\u2022"); // bullet character as placeholder
            footnoteSeparator.appendChild(run);
        }

        // Step 3: Change the first run's formatting – this is where we
        //          modify footnote separator appearance
        Run firstRun = footnoteSeparator.getRuns().get(0);
        Font font = firstRun.getFont();
        font.setBold(true);                // make the separator bold
        font.setItalic(true);              // optional: also italic
        font.setSize(10.0);                // set font size to 10 pt
        font.setColor(java.awt.Color.GRAY); // change color to a subtle gray

        // Step 4: Save the updated document
        doc.save("YOUR_DIRECTORY/output.docx");
    }
}
```

### لماذا كل خطوة مهمة

* **تحميل المستند** (`new Document`) ينشئ تمثيلًا في الذاكرة يمكن لـ Aspose.Words التلاعب به.  
* **استرجاع فاصل الحاشية السفلية** (`getFootnoteSeparator`) يمنحك وصولًا مباشرًا إلى الفقرة التي تفصل الحواشي عن النص الرئيسي. هذا هو العنصر الذي تحتاج إلى استهدافه عندما تريد **تغيير تنسيق الحاشية السفلية**.  
* **تنسيق المقطع** (`setBold`, `setItalic`, `setSize`, `setColor`) يوضح كيفية **تعديل خصائص فاصل الحاشية السفلية**. يمكنك إضافة أي سمات خط إضافية هنا، مثل التسطير أو التمييز، للتحكم الكامل في المظهر.  
* **حفظ المستند** يكتب التغييرات مرة أخرى إلى القرص، وينتج ملفًا جديدًا (`output.docx`) يعكس نمط الحاشية السفلية المحدث.

> **نصيحة احترافية:** إذا كان مستندك المصدر يستخدم فاصل حاشية سفلي مخصص يحتوي على عدة مقاطع (مثلاً، مزيج من الرموز)، قم بالتكرار عبر `footnoteSeparator.getRuns()` وطبق نفس إعدادات `Font` على كل مقطع للحصول على تنسيق متسق.

## كيفية تحرير فاصل الحاشية السفلية برمجياً

أحيانًا قد تحتاج إلى تحرير ليس فقط الفاصل بل أيضًا نص الحاشية السفلية نفسه. يمكن استخدام نفس الـ API للوصول إلى كل حاشية، وضبط تنسيق الفقرة الخاصة بها، أو تغيير نمط الترقيم.

```java
for (Footnote footnote : (Iterable<Footnote>) doc.getFootnotes()) {
    // Example: make all footnote text italic and 9 pt
    for (Paragraph para : (Iterable<Paragraph>) footnote.getParagraphs()) {
        para.getParagraphFormat().setStyleIdentifier(StyleIdentifier.FOOTNOTE_TEXT);
        para.getRuns().forEach(run -> {
            Font f = run.getFont();
            f.setItalic(true);
            f.setSize(9.0);
        });
    }
}
```

المقتطف أعلاه يوضح **كيفية تحرير محتوى الحاشية** بعد أن تكون قد **قمت بتغيير تنسيق الحاشية** للفاصل. من خلال التكرار على `doc.getFootnotes()`, تضمن أن كل حاشية ستحصل على نفس النمط، وهو أمر أساسي للحصول على مستند بمظهر احترافي.

## تحديث نمط الحاشية السفلية لمظهر مستند متسق

إذا كنت تفضل العمل بالأنماط بدلاً من المقاطع الفردية، يتيح لك Aspose.Words إنشاء أو تعديل كائن `Style` ثم تطبيقه على الحواشي والفاصل. هذا النهج مفيد عندما تحتاج إلى **تحديث نمط الحاشية السفلية** عبر العديد من المستندات.

```java
// Create or retrieve a style named "MyFootnoteStyle"
Style footnoteStyle = doc.getStyles().add(StyleType.PARAGRAPH, "MyFootnoteStyle");
footnoteStyle.getFont().setBold(true);
footnoteStyle.getFont().setSize(10);
footnoteStyle.getFont().setColor(java.awt.Color.DARK_GRAY);

// Apply the style to the separator
footnoteSeparator.getParagraphFormat().setStyle(footnoteStyle);

// Apply the same style to every footnote paragraph
for (Footnote fn : (Iterable<Footnote>) doc.getFootnotes()) {
    for (Paragraph p : (Iterable<Paragraph>) fn.getParagraphs()) {
        p.getParagraphFormat().setStyle(footnoteStyle);
    }
}
```

استخدام نمط مخصص يجعل الصيانة المستقبلية أسهل—قم بتغيير النمط مرة واحدة، وسيتم تحديث كل حاشية وفاصل تلقائيًا. هذه التقنية هي الطريقة الموصى بها **لتحديث نمط الحاشية السفلية** في سير عمل النشر على نطاق واسع.

## تعديل فاصل الحاشية السفلية ليتماشى مع علامتك التجارية

في بعض الأحيان تحدد إرشادات العلامة التجارية أن يستخدم فاصل الحاشية السفلية حرفًا محددًا (مثل النجمة) أو خطًا مخصصًا. يتيح لك Aspose.Words استبدال محتوى الفاصل الافتراضي بالكامل.

```java
// Remove existing runs
footnoteSeparator.getRuns().clear();

// Insert a custom separator line
Run customRun = new Run(doc);
customRun.setText("--- Custom Separator ---");
Font customFont = customRun.getFont();
customFont.setBold(true);
customFont.setSize(8);
customFont.setColor(java.awt.Color.BLUE);
footnoteSeparator.appendChild(customRun);
```

الكود أعلاه **يعدل فاصل الحاشية السفلية** عن طريق مسح أي مقاطع موجودة وإدراج مقطع جديد بالنص والتنسيق المطلوب. يمكنك أيضًا استخدام أحرف Unicode مثل `\u2022` (نقطة) أو `\u2014` (شرطة طويلة) لتحقيق التأثير البصري الدقيق المطلوب من قبل علامتك التجارية.

## النتيجة المتوقعة

بعد تشغيل البرنامج:

* فاصل الحاشية السفلية في `output.docx` يظهر **غامقًا**، **مائلًا**، بحجم 10 نقطة، ولون رمادي (أو أي لون قمت بتعيينه).  
* جميع فقرات الحواشي تتبنى النمط الذي حددته، مما يضمن مظهرًا موحدًا عبر المستند بأكمله.  
* إذا قمت باستبدال نص الفاصل، فإن الخط المخصص الجديد يظهر بالضبط حيث كان الخط الأصلي موجودًا.

افتح الملف الناتج في Microsoft Word أو LibreOffice Writer للتحقق من التغييرات. يجب أن ترى الفاصل المحدث مباشرةً فوق أول حاشية سفلية، ويجب أن يعكس نص الحاشية أي تعديلات نمط قمت بتطبيقها.

## المشكلات الشائعة وكيفية تجنبها

| المشكلة | سبب حدوثها | الحل |
|-------|----------------|-----|
| `footnoteSeparator.getRuns().getCount() == 0` يثير استثناء | بعض المستندات تحتوي على فقرة فاصل فارغة. | أضف فحصًا وقائيًا وأنشئ مقطعًا إذا لم يكن موجودًا (انظر مثال الكود). |
| تغييرات الخط غير مرئية | المستند يستخدم سمة تتجاوز التنسيق المباشر. | قم بتعيين `font.setThemeFont(null)` أو استخدم نمطًا مخصصًا بدلاً من التنسيق المباشر. |
| الملف المحفوظ لا يعكس التغييرات | الملف الأصلي لا يزال مفتوحًا في Word، مما يمنع كتابة المسار الوجهة. | أغلق أي نسخة من الملف قبل تشغيل البرنامج، أو |

## ماذا يجب أن تتعلم بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات الموضحة في هذا الدليل. كل مصدر يتضمن أمثلة كود كاملة مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف أساليب تنفيذ بديلة في مشاريعك.

- [معالجة الكلمات مع الحواشي السفلية والحواشي الختامية](/words/english/net/working-with-footnote-and-endnote/)
- [تعيين موضع الحاشية السفلية والحاشية الختامية](/words/english/net/working-with-footnote-and-endnote/set-footnote-and-end-note-position/)
- [كيفية عرض معلومات إصدار Aspose.Words في Java: دليل شامل](/words/english/java/getting-started/aspose-words-java-version-info/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}