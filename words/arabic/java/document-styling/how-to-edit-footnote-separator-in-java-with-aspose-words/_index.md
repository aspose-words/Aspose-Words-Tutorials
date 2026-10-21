---
category: general
date: 2026-10-04
description: تحرير فاصل الحاشية السفلية في جافا باستخدام Aspose.Words – تعلم كيفية
  تغيير فاصل الحاشية السفلية وإضافة كلمة فاصل مخصصة إلى مستندات Word.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- edit footnote separator
- change footnote separator
- custom separator word
language: ar
lastmod: 2026-10-04
og_description: تحرير فاصل الحاشية في Java باستخدام Aspose.Words. يوضح هذا الدرس كيفية
  تغيير فاصل الحاشية وإدراج كلمة فاصل مخصصة.
og_image_alt: Screenshot of a Java IDE showing code that edits a footnote separator
  in a Word document
og_title: تحرير فاصل الحاشية السفلية في جافا – دليل Aspose.Words الكامل
schemas:
- author: Aspose
  dateModified: '2026-10-04'
  description: Edit footnote separator in Java using Aspose.Words – learn how to change
    footnote separator and add a custom separator word to Word documents.
  headline: How to edit footnote separator in Java with Aspose.Words
  type: TechArticle
- description: Edit footnote separator in Java using Aspose.Words – learn how to change
    footnote separator and add a custom separator word to Word documents.
  name: How to edit footnote separator in Java with Aspose.Words
  steps:
  - name: '**`clearChildren()`** removes any existing runs, ensuring the separator
      contains only the text you provide.'
    text: '**`clearChildren()`** removes any existing runs, ensuring the separator
      contains only the text you provide.'
  - name: '**`new Run(document, "—")`** creates a text node with the desired separator.
      The `Run` object respects the document’s style, so the separator inherits the
      formatting of the original footnote separator.'
    text: '**`new Run(document, "—")`** creates a text node with the desired separator.
      The `Run` object respects the document’s style, so the separator inherits the
      formatting of the original footnote separator.'
  - name: '**`appendChild(customRun)`** inserts the new run into the separator paragraph.'
    text: '**`appendChild(customRun)`** inserts the new run into the separator paragraph.'
  type: HowTo
tags:
- Aspose.Words
- Java
- Footnotes
- Word processing
title: كيفية تعديل فاصل الحاشية السفلية في جافا باستخدام Aspose.Words
url: /ar/java/document-styling/how-to-edit-footnote-separator-in-java-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# كيفية تعديل فاصل الحاشية السفلية في Java باستخدام Aspose.Words

إذا كنت بحاجة إلى **تعديل فاصل الحاشية السفلية** في مستند Word، يوضح لك هذا الدليل بالضبط كيفية القيام بذلك في Java. سواء كنت تريد **تغيير فاصل الحاشية السفلية** إلى شرطة، نجمة، أو أي **كلمة فاصل مخصصة**، فإن الخطوات أدناه تغطي كل ما تحتاجه.

ستتعلم كيفية تحميل ملف `.docx`، استرجاع قسم الفاصل الخاص، تعديل محتواه، وحفظ النتيجة. لا حاجة لسكربتات خارجية أو تعديل يدوي – كل شيء يتم برمجياً باستخدام مكتبة Aspose.Words for Java.

## المتطلبات المسبقة

قبل أن تبدأ، تأكد من وجود ما يلي:

- Java 17 أو أحدث مثبتة.
- Maven أو Gradle لإدارة الاعتمادات (المثال يستخدم Maven).
- رخصة صالحة لـ Aspose.Words for Java (أو مفتاح تقييم مجاني).
- مستند Word يحتوي بالفعل على حواشي سفلية (الفاصل موجود فقط عندما تكون هناك حواشي).

## إضافة Aspose.Words إلى مشروعك

إذا كنت تستخدم Maven، أضف الاعتماد التالي إلى ملف `pom.xml` الخاص بك:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.11</version> <!-- Use the latest version -->
</dependency>
```

لـ Gradle، أضف:

```gradle
implementation 'com.aspose:aspose-words:24.11'
```

## الخطوة 1: تحميل المستند الذي يحتوي على حواشي سفلية

الخطوة الأولى هي فتح ملف Word الذي تريد تعديله. تقوم Aspose.Words بقراءة الملف إلى كائن `Document`، مما يمنحك وصولاً كاملاً إلى جميع أجزاء المستند، بما في ذلك فواصل الحواشي السفلية.

```java
import com.aspose.words.*;

public class EditFootnoteSeparator {
    public static void main(String[] args) throws Exception {
        // Path to the source document
        String inputPath = "YOUR_DIRECTORY/docWithNotes.docx";

        // Load the document
        Document document = new Document(inputPath);
        
        // Continue with separator editing...
    }
}
```

**لماذا هذا مهم:** تحميل المستند ينشئ تمثيلاً في الذاكرة، بحيث يمكنك تعديل أي عقدة بأمان دون المساس بالملف الأصلي حتى تقوم بحفظه صراحةً.

## الخطوة 2: استرجاع قسم فاصل الحاشية السفلية

يقوم Word بتخزين فاصل الحاشية السفلية كعقدة `Separator` خاصة. توفر Aspose.Words الطريقة `getFootnoteSeparator()` للحصول عليها مباشرة.

```java
// Get the footnote separator (the line that appears between footnotes and the main text)
Separator footnoteSeparator = document.getFootnoteSeparator();

if (footnoteSeparator == null) {
    System.out.println("The document does not contain a footnote separator.");
    return;
}
```

**نصيحة احترافية:** عقدة الفاصل موجودة فقط إذا كان المستند يحتوي بالفعل على حاشية سفلية واحدة على الأقل. إذا حاولت تعديل مستند بدون حواشي، فإن `getFootnoteSeparator()` تُعيد `null`، لذا تحقق دائماً من هذه الحالة.

## الخطوة 3: إدراج كلمة فاصل مخصصة

الآن يمكنك تغيير مظهر الفاصل. في هذا المثال نستبدل الخط الافتراضي بشرطة طويلة (em dash `—`). يمكنك بدلاً من ذلك إدراج أي **كلمة فاصل مخصصة** مثل `"NOTE:"` أو `"***"`.

```java
// Access the first paragraph of the separator (there is usually only one)
Paragraph separatorParagraph = footnoteSeparator.getParagraphs().get(0);

// Clear any existing runs (text fragments) to avoid mixing old and new content
separatorParagraph.clearChildren();

// Append a new Run that contains the custom separator word
Run customRun = new Run(document, "—");   // Replace "—" with any text you need
separatorParagraph.appendChild(customRun);
```

### ما يفعله الكود

1. **`clearChildren()`** يزيل أي تشغيلات (runs) موجودة، مما يضمن أن الفاصل يحتوي فقط على النص الذي تقدمه.
2. **`new Run(document, "—")`** ينشئ عقدة نصية بالفاصل المطلوب. كائن `Run` يحترم نمط المستند، لذا يرث الفاصل تنسيق فاصل الحاشية السفلية الأصلي.
3. **`appendChild(customRun)`** يضيف التشغيل الجديد إلى الفقرة الفاصلة.

يمكنك أيضاً تطبيق تنسيق على الـ run، على سبيل المثال:

```java
customRun.getFont().setBold(true);
customRun.getFont().setSize(10);
customRun.getFont().setColor(Color.BLUE);
```

## الخطوة 4: حفظ المستند المعدل

بعد تعديل الفاصل، اكتب المستند مرة أخرى إلى القرص. اختر اسم ملف جديد للحفاظ على الملف الأصلي دون تعديل.

```java
// Path to the output document
String outputPath = "YOUR_DIRECTORY/ModifiedNotes.docx";

// Save the changes
document.save(outputPath);

System.out.println("Footnote separator edited successfully. Saved to " + outputPath);
```

**التحقق من النتيجة:** افتح `ModifiedNotes.docx` في Microsoft Word. يجب الآن أن يظهر فاصل الحاشية السفلية بالشرطة المخصصة (أو أي كلمة اخترتها) بدلاً من الخط الافتراضي.

## التعامل مع فواصل حواشي متعددة

يدعم Word ثلاثة أنواع خاصة من الفواصل:

| نوع الفاصل | الطريقة |
|----------------|----------------------------|
| فاصل الحاشية السفلية | `getFootnoteSeparator()` |
| فاصل استمرار الحاشية السفلية | `getFootnoteContinuationSeparator()` |
| فاصل الحاشية السفلية للصفحة الأولى | `getFootnoteSeparatorForFirstPage()` |

إذا كنت بحاجة إلى تعديل جميعها، كرّر **الخطوة 2** و **الخطوة 3** لكل طريقة. مثال:

```java
Separator continuation = document.getFootnoteContinuationSeparator();
if (continuation != null) {
    // Apply the same custom run or a different one
    Paragraph p = continuation.getParagraphs().get(0);
    p.clearChildren();
    p.appendChild(new Run(document, "*"));
}
```

## الأخطاء الشائعة وكيفية تجنّبها

| المشكلة | السبب | الحل |
|-------|-------|-----|
| لا يظهر فاصل بعد الحفظ | المستند لا يحتوي على حواشي → عقدة الفاصل هي `null` | أضف حاشية سفلية واحدة على الأقل قبل التعديل، أو أنشئ حاشية وهمية برمجياً. |
| الفاصل يظهر به مسافات إضافية | لم يتم مسح التشغيلات الموجودة | استدعِ `clearChildren()` قبل إلحاق الـ run الجديد. |
| التنسيق يبدو مختلفاً | الـ Run يرث النمط من الفاصل الأصلي | عيّن خصائص الخط صراحةً على الـ `Run` إذا كنت تحتاج مظهرًا محددًا. |

## مثال كامل يعمل

بجمع كل الأجزاء معاً، إليك فئة Java مستقلة يمكنك نسخها، تجميعها، وتشغيلها:

```java
import com.aspose.words.*;
import java.awt.Color;

public class EditFootnoteSeparator {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Load the document
        String inputPath = "YOUR_DIRECTORY/docWithNotes.docx";
        Document doc = new Document(inputPath);

        // 2️⃣ Retrieve the footnote separator
        Separator footnoteSeparator = doc.getFootnoteSeparator();
        if (footnoteSeparator == null) {
            System.out.println("Document has no footnote separator.");
            return;
        }

        // 3️⃣ Replace the separator with a custom word (e.g., an em dash)
        Paragraph para = footnoteSeparator.getParagraphs().get(0);
        para.clearChildren();                       // Remove old runs
        Run customRun = new Run(doc, "—");          // Change "—" to any word you need
        customRun.getFont().setBold(true);         // Optional styling
        customRun.getFont().setSize(9);
        customRun.getFont().setColor(Color.DARK_GRAY);
        para.appendChild(customRun);

        // 4️⃣ Save the modified document
        String outputPath = "YOUR_DIRECTORY/ModifiedNotes.docx";
        doc.save(outputPath);

        System.out.println("Footnote separator edited successfully.");
    }
}
```

شغّل البرنامج، ثم افتح `ModifiedNotes.docx` لتأكيد أن الفاصل قد تم تحديثه.

## الخلاصة

أنت الآن تعرف كيفية **تعديل فاصل الحاشية السفلية** في مستند Word باستخدام Java و Aspose.Words. غطى الدليل تحميل المستند، استرجاع عقدة الفاصل الخاصة، إدراج **كلمة فاصل مخصصة**، وحفظ النتيجة. باتباع هذه الخطوات يمكنك أيضاً **تغيير فاصل الحاشية السفلية** لأقسام الاستمرار أو حواشي الصفحة الأولى.

التالي، قد ترغب في استكشاف:

- إضافة فواصل مختلفة لحواشي الصفحة الأولى (`getFootnoteSeparatorForFirstPage()`).
- إنشاء حواشي برمجياً عندما لا توجد أي حواشي.
- استخدام Aspose.Words لتنسيق نص الحاشية (الخطوط، الألوان، المسافات البادئة).

لا تتردد في تجربة أحرف أو كلمات أخرى لتتناسب مع هوية مستندك. Happy coding!

## ما الذي يجب أن تتعلمه بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات التي تم توضيحها في هذا الدليل. كل مورد يتضمن أمثلة كود كاملة مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف طرق تنفيذ بديلة في مشاريعك.

- [إدراج فاصل نمط المستند في Word](/words/english/net/programming-with-styles-and-themes/insert-style-separator/)
- [الحصول على فاصل نمط الفقرة في مستند Word](/words/english/net/document-formatting/get-paragraph-style-separator/)
- [كيفية تحميل مستندات Word باستخدام Aspose.Words Java: دليل شامل](/words/english/java/document-operations/aspose-words-java-master-word-processing/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}