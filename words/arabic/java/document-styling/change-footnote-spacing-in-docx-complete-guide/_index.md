---
category: general
date: 2026-07-20
description: غيّر تباعد الحواشي في ملفات DOCX بسهولة. تعلّم كيفية ضبط التباعد، تعديل
  فاصل الحواشي، وتعيين تباعد أسطر الفقرة باستخدام Java.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- change footnote spacing
- how to set spacing
- adjust footnote separator
- set paragraph line spacing
- change line spacing docx
language: ar
lastmod: 2026-07-20
og_description: غيّر تباعد الحواشي في ملفات DOCX بسرعة. يوضح هذا الدليل كيفية ضبط
  التباعد، تعديل فاصل الحواشي، وتخصيص تباعد سطر الفقرة في جافا.
og_image_alt: Screenshot showing Java code that changes footnote spacing in a DOCX
  document
og_title: تغيير تباعد الحواشي في DOCX – دليل خطوة بخطوة
schemas:
- author: Aspose
  dateModified: '2026-07-20'
  description: Change footnote spacing in DOCX files easily. Learn how to set spacing,
    adjust footnote separator, and set paragraph line spacing with Java.
  headline: Change footnote spacing in DOCX – Complete Guide
  type: TechArticle
tags:
- footnote
- docx
- java
- spacing
title: تغيير تباعد الحواشي السفلية في DOCX – دليل شامل
url: /ar/java/document-styling/change-footnote-spacing-in-docx-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# تغيير تباعد الحواشي في DOCX – دليل كامل

هل احتجت يومًا إلى **تغيير تباعد الحواشي** في مستند Word لكن لم تكن متأكدًا من أين تبدأ؟ لست وحدك. سواء كنت تُنقّح رسالة ماجستير أو تُعدّل عقدًا، فإن ضبط فاصل الحواشي بشكل صحيح يمكن أن يُحدث فرقًا كبيرًا.  

في هذا الدرس سنستعرض **كيفية ضبط التباعد**، تعديل فاصل الحواشي، و**ضبط تباعد سطر الفقرة** باستخدام مكتبات مبنية على Java. في النهاية ستحصل على مثال جاهز للتنفيذ يمكنك إدراجه في أي مشروع.

## ما ستحتاجه

- Java 17 أو أحدث (الكود يستخدم ميزات اللغة الحديثة)
- Maven أو Gradle لإدارة الاعتمادات
- ملف DOCX يحتوي على حاشية واحدة على الأقل (أو يمكنك إنشاء واحد يدويًا)
- مكتبة **Aspose.Words for Java** (أو أي API متوافق؛ سنستخدم Aspose في المثال)

هذا كل شيء—بدون أطر عمل ثقيلة، فقط Java عادي ومكتبة واحدة.

![مثال على تغيير تباعد الحواشي في DOCX](/images/footnote-spacing.png){alt="مثال على تغيير تباعد الحواشي في DOCX"}

## الخطوة 1: تحميل مستند DOCX (تغيير تباعد الحواشي)

أول شيء عليك فعله هو فتح ملف Word. هذا يمنحك كائن `Document` يمكنك التلاعب به.

```java
import com.aspose.words.*;

public class FootnoteSpacingDemo {
    public static void main(String[] args) throws Exception {
        // Load the DOCX file – change the path to your own file
        Document doc = new Document("input.docx");
        
        // Continue with spacing adjustments...
        adjustFootnoteSeparator(doc);
        
        // Save the updated document
        doc.save("output.docx");
    }
}
```

*لماذا هذا مهم*: تحميل المستند هو نقطة الدخول لـ **تغيير تباعد الحواشي**. بدون كائن `Document` لا يمكنك الوصول إلى فاصل الحواشي أو أي تنسيقات الفقرات.

## الخطوة 2: استرجاع وضبط فاصل الحواشي (ضبط فاصل الحواشي)

فاصل الحواشي هو فقرة مخفية تقع بين النص الرئيسي وقائمة الحواشي. لتغيير تباعد أسطرها تحتاج إلى الحصول على تلك الفقرة وتعديل تنسيقها.

```java
private static void adjustFootnoteSeparator(Document doc) throws Exception {
    // Get the footnote separator (the first one is usually the default separator)
    FootnoteSeparator separator = doc.getFootnoteSeparator();
    
    // If the document has no separator (rare), create one
    if (separator == null) {
        separator = new FootnoteSeparator(doc);
        doc.getFootnotes().add(separator);
    }
    
    // Access the underlying paragraph and set line spacing
    Paragraph sepParagraph = separator.getSeparatorParagraph();
    ParagraphFormat fmt = sepParagraph.getParagraphFormat();
    
    // Set line spacing to 12 points – this is the core of "change footnote spacing"
    fmt.setLineSpacing(12.0);
    
    // Optional: also adjust spacing before/after if needed
    fmt.setSpaceBefore(0);
    fmt.setSpaceAfter(0);
}
```

### كيف يحل هذا المشكلة

- **استرجاع فاصل الحواشي** – هذا هو الجزء الذي تريد تعديله فعليًا، مما يفي بمتطلب *ضبط فاصل الحواشي*.
- **ضبط تباعد السطر** – `setLineSpacing(12.0)` يجيب مباشرةً على *كيفية ضبط التباعد* لتلك الفقرة المخفية.
- **معالجة الحالات الطرفية** – إذا كان المستند يفتقر إلى فاصل بطريقة ما، نقوم بإنشائه فورًا، مما يمنع حدوث `NullPointerException`.

## الخطوة 3: التحقق من التغيير والحفظ (ضبط تباعد سطر الفقرة)

بعد تعديل الفاصل، سترغب في التأكد من أن التغيير تم حفظه. فتح الملف المحفوظ في Word سيظهر التباعد الجديد، لكن يمكنك أيضًا التحقق منه برمجيًا.

```java
private static void verifySpacing(Document doc) throws Exception {
    FootnoteSeparator sep = doc.getFootnoteSeparator();
    double spacing = sep.getSeparatorParagraph().getParagraphFormat().getLineSpacing();
    System.out.println("Current footnote separator line spacing: " + spacing);
}
```

أضف استدعاءً لـ `verifySpacing(doc);` مباشرةً قبل `doc.save(...)` في الدالة `main`. عند تشغيل البرنامج يجب أن ترى:

```
Current footnote separator line spacing: 12.0
```

هذا يؤكد أن عملية **تغيير تباعد السطر في docx** نجحت.

## الأخطاء الشائعة والنصائح الاحترافية

- **خطأ**: استخدام `setLineSpacing` بقيمة تبدو كـ “12” ولكن تُفسَّر كـ “12 نقطة” مقابل “12 سطر”. Aspose تتوقع النقاط، لذا 12 تعني 12 pt. للتباعد المزدوج استخدم `24.0`.
- **نصيحة احترافية**: إذا كنت بحاجة إلى مظهر موحد عبر جميع أنواع الحواشي (الفاصل، فاصل الاستمرار، إلخ)، كرّر نفس الخطوات لـ `doc.getFootnoteContinuationSeparator()` و `doc.getFootnoteContinuationNotice()`.
- **خطأ**: نسيان استدعاء `save()` بعد التعديلات. المستند في الذاكرة يتغير، لكن الملف على القرص يبقى كما هو.
- **نصيحة احترافية**: اجمع بين تغييرات التباعد وتحديثات الأنماط (`ParagraphStyle`) للحصول على قسم حواشي مصقول بالكامل.

## مثال كامل يعمل (جميع الخطوات في ملف واحد)

```java
import com.aspose.words.*;

public class FootnoteSpacingDemo {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Load the DOCX document
        Document doc = new Document("input.docx");

        // 2️⃣ Adjust the footnote separator – this is where we "change footnote spacing"
        adjustFootnoteSeparator(doc);

        // 3️⃣ Verify the new line spacing (optional but handy for debugging)
        verifySpacing(doc);

        // 4️⃣ Save the result – now your footnotes have the desired spacing
        doc.save("output.docx");
        System.out.println("Footnote spacing updated and saved to output.docx");
    }

    private static void adjustFootnoteSeparator(Document doc) throws Exception {
        FootnoteSeparator separator = doc.getFootnoteSeparator();
        if (separator == null) {
            separator = new FootnoteSeparator(doc);
            doc.getFootnotes().add(separator);
        }
        Paragraph sepParagraph = separator.getSeparatorParagraph();
        ParagraphFormat fmt = sepParagraph.getParagraphFormat();

        // Core operation: "set paragraph line spacing" for the separator
        fmt.setLineSpacing(12.0);   // 12 pt line spacing
        fmt.setSpaceBefore(0);
        fmt.setSpaceAfter(0);
    }

    private static void verifySpacing(Document doc) throws Exception {
        FootnoteSeparator sep = doc.getFootnoteSeparator();
        double spacing = sep.getSeparatorParagraph().getParagraphFormat().getLineSpacing();
        System.out.println("Current footnote separator line spacing: " + spacing);
    }
}
```

انسخ الشيفرة أعلاه إلى فئة Java جديدة، أضف اعتماد Aspose.Words Maven، وشغّلها. سيصبح ملف `output.docx` الآن يحتوي على تباعد سطر فاصل الحواشي مضبوطًا إلى **12 pt**، مما يؤدي فعليًا إلى **تغيير تباعد الحواشي**.

### اعتماد Maven

أضف هذا المقتطف إلى ملف `pom.xml` الخاص بك:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version> <!-- Use the latest stable version -->
</dependency>
```

إذا كنت تفضل Gradle، فإن المكافئ هو:

```gradle
implementation 'com.aspose:aspose-words:24.9'
```

## الخلاصة

لقد تعلمت الآن كيفية **تغيير تباعد الحواشي** في ملف DOCX باستخدام Java. من خلال تحميل المستند، استرجاع **فاصل الحواشي**، وتطبيق **ضبط تباعد سطر الفقرة**، تحصل على تحكم دقيق في مظهر الحواشي.  

من هنا يمكنك استكشاف تعديلات ذات صلة، مثل تعديل نمط نص الحواشي، إضافة فواصل مخصصة، أو حتى أتمتة تحديثات جماعية عبر مستندات متعددة.  

هل لديك المزيد من الأسئلة حول **ضبط فاصل الحواشي** أو مهام أتمتة Word أخرى؟ اترك تعليقًا، وتمنياتنا لك بالبرمجة السعيدة!

## ماذا يجب أن تتعلم بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات التي تم توضيحها في هذا الدليل. كل مصدر يتضمن أمثلة شاملة من الشيفرة مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف أساليب تنفيذ بديلة في مشاريعك.

- [تغيير تباعد الفقرة الآسيوية والمسافات البادئة في مستند Word](/words/english/net/document-formatting/change-asian-paragraph-spacing-and-indents/)
- [تغيير تباعد الفقرة الآسيوية والمسافات البادئة](/words/german/net/document-formatting/change-asian-paragraph-spacing-and-indents/)
- [تغيير تباعد الفقرة الآسيوية والمسافات البادئة](/words/french/net/document-formatting/change-asian-paragraph-spacing-and-indents/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}