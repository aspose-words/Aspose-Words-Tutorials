---
category: general
date: 2026-08-07
description: كيفية تعديل الحاشية السفلية في جافا باستخدام Aspose.Words – إضافة شرطة
  مخصصة، تغيير خط الحاشية السفلية، وتعيين محاذاة الفقرة للحصول على مستندات مصقولة.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to edit footnote
- add custom dash
- change footnote line
- change footnote separator
- set paragraph alignment
language: ar
lastmod: 2026-08-07
og_description: كيفية تعديل الحاشية السفلية في جافا باستخدام Aspose.Words. تعلم إضافة
  شرطة مخصصة، تغيير خط الحاشية السفلية، وتعيين محاذاة الفقرة في بضع خطوات فقط.
og_image_alt: Java code editing footnote separator with a custom dash and centered
  alignment
og_title: كيفية تعديل الحاشية السفلية في جافا – إضافة شرطة، تغيير السطر، ضبط المحاذاة
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: How to edit footnote in Java with Aspose.Words – add custom dash, change
    footnote line, and set paragraph alignment for polished documents.
  headline: How to edit footnote in Java with Aspose.Words
  type: TechArticle
- description: How to edit footnote in Java with Aspose.Words – add custom dash, change
    footnote line, and set paragraph alignment for polished documents.
  name: How to edit footnote in Java with Aspose.Words
  steps:
  - name: '**Loading the document** – `new Document(...)` reads the DOCX file into
      memory, giving you access to all its nodes.'
    text: '**Loading the document** – `new Document(...)` reads the DOCX file into
      memory, giving you access to all its nodes.'
  - name: '**Fetching the separator** – `getFootnoteSeparator()` returns the special
      paragraph that Aspose.Words treats as the footnote line. This object is the
      only place you can safely modify the separator.'
    text: '**Fetching the separator** – `getFootnoteSeparator()` returns the special
      paragraph that Aspose.Words treats as the footnote line. This object is the
      only place you can safely modify the separator.'
  - name: '**Setting paragraph alignment** – `setAlignment(ParagraphAlignment.CENTER)`
      changes the line’s alignment. The keyword *set paragraph alignment* is applied
      directly to the separator, ensuring a centered dash.'
    text: '**Setting paragraph alignment** – `setAlignment(ParagraphAlignment.CENTER)`
      changes the line’s alignment. The keyword *set paragraph alignment* is applied
      directly to the separator, ensuring a centered dash.'
  - name: '**Adding a custom dash** – By clearing existing runs and adding a new `Run`
      with the em‑dash character (`—`), you achieve the *add custom dash* effect while
      also *change footnote line* to your desired style.'
    text: '**Adding a custom dash** – By clearing existing runs and adding a new `Run`
      with the em‑dash character (`—`), you achieve the *add custom dash* effect while
      also *change footnote line* to your desired style.'
  - name: '**Saving the document** – `doc.save(...)` writes the changes back to disk,
      producing an output file that reflects all modifications.'
    text: '**Saving the document** – `doc.save(...)` writes the changes back to disk,
      producing an output file that reflects all modifications.'
  type: HowTo
tags:
- Aspose.Words
- Java
- Footnotes
title: كيفية تعديل الحاشية السفلية في جافا باستخدام Aspose.Words
url: /ar/java/document-styling/how-to-edit-footnote-in-java-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# كيفية تعديل الحاشية السفلية في Java باستخدام Aspose.Words

إذا كنت بحاجة إلى **كيفية تعديل الحاشية السفلية** في مستند Word باستخدام Java، فإن هذا الدليل يوضح سير العمل الكامل. ستتعلم كيفية إضافة شرطة مخصصة، تغيير خط الحاشية السفلية، وتعيين محاذاة الفقرة بحيث يبدو فاصل الحاشية السفلية احترافيًا.

تعديل الحواشي السفلية هو طلب شائع عند إعداد العقود القانونية، الأوراق الأكاديمية، أو الكتيبات التسويقية. تغطي الخطوات أدناه كل ما تحتاجه—من تحميل المستند إلى حفظ الملف النهائي—دون الحاجة إلى أدوات إضافية.

## المتطلبات المسبقة

* Java 17 أو أحدث مثبت.
* Aspose.Words for Java (الإصدار الأخير) مضاف إلى مسار الفئات (classpath) في مشروعك.
* ملف DOCX (`input.docx`) يحتوي على حاشية سفلية واحدة على الأقل.

هذه العناصر تضمن تشغيل الكود دون أخطاء وقت التشغيل.

## كيفية تعديل فاصل الحاشية السفلية والخط

فاصل الحاشية السفلية هو الفقرة التي تظهر بين النص الرئيسي وقائمة الحواشي السفلية. تغيير مظهره يحسن القابلية للقراءة ويتماشى مع هوية العلامة التجارية.

```java
import com.aspose.words.*;

public class FootnoteSeparatorDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Load the document containing footnotes
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // Step 2: Get the footnote separator paragraph (the line before the footnote list)
        Paragraph separator = doc.getFootnoteSeparator();

        // Step 3: Center‑align the separator for better appearance
        separator.getParagraphFormat().setAlignment(ParagraphAlignment.CENTER);

        // Step 4: Replace the default separator line with a custom dash
        separator.getRuns().clear();                 // Remove existing runs
        separator.getRuns().add(new Run(doc, "—"));   // Add a custom dash character

        // Step 5: Save the modified document
        doc.save("YOUR_DIRECTORY/output.docx");
    }
}
```

### لماذا كل سطر مهم

1. **تحميل المستند** – `new Document(...)` يقرأ ملف DOCX إلى الذاكرة، مما يمنحك الوصول إلى جميع عقده.
2. **جلب الفاصل** – `getFootnoteSeparator()` يُعيد الفقرة الخاصة التي تتعامل معها Aspose.Words كخط الحاشية السفلية. هذا الكائن هو المكان الوحيد الذي يمكنك تعديل الفاصل فيه بأمان.
3. **تعيين محاذاة الفقرة** – `setAlignment(ParagraphAlignment.CENTER)` يغيّر محاذاة الخط. كلمة المفتاح *set paragraph alignment* تُطبق مباشرة على الفاصل، مما يضمن شرطة متمركزة.
4. **إضافة شرطة مخصصة** – عن طريق مسح الـ runs الحالية وإضافة `Run` جديد بحرف الشرطة الطويلة (`—`)، تحقق تأثير *add custom dash* بينما تقوم أيضًا بـ *change footnote line* إلى النمط المطلوب.
5. **حفظ المستند** – `doc.save(...)` يكتب التغييرات إلى القرص، منتجًا ملف إخراج يعكس جميع التعديلات.

## إضافة شرطة مخصصة إلى فاصل الحاشية السفلية

الكود في **Step 4** يوضح تقنية *add custom dash*. يمكنك استبدال الشرطة الطويلة بأي سلسلة، مثل `"***"` أو `"---"`، لتتناسب مع اللغة البصرية لمستندك.

```java
separator.getRuns().clear();                     // Remove default line
separator.getRuns().add(new Run(doc, "***"));    // Insert three asterisks as a custom dash
```

استخدام شرطة مخصصة يكون مفيدًا بشكل خاص عندما لا تلبي الخط الرفيع الافتراضي إرشادات العلامة التجارية.

## تغيير نمط خط الحاشية السفلية

إذا كنت تفضّل خطًا صلبًا بدلاً من الشرطة، يمكنك إدراج حرف رسم صندوق Unicode أو شرطة سفلية متكررة.

```java
separator.getRuns().clear();
separator.getRuns().add(new Run(doc, "_____")); // Five underscores create a solid line
```

خطوة *change footnote line* تعمل بنفس الطريقة بغض النظر عن الحرف الذي تختاره، لأن فقرة الفاصل تقوم ببساطة بعرض النص الموجود فيها.

## تعيين محاذاة الفقرة لفاصل الحاشية السفلية

عملية *set paragraph alignment* لا تقتصر على المحاذاة المركزية. يمكنك المحاذاة إلى اليسار أو اليمين أو الضبط المتساوي وفقًا لاحتياجات التخطيط الخاصة بك.

```java
separator.getParagraphFormat().setAlignment(ParagraphAlignment.RIGHT); // Right‑align
```

محاذاة الفاصل إلى اليمين يمكن أن تكون مفيدة للمستندات التي تستخدم حواشي سفلية محاذاة إلى اليمين، مثل المنشورات ثنائية اللغة.

## مثال كامل قابل للتنفيذ

فيما يلي البرنامج الكامل الذي يدمج جميع المفاهيم—تحميل مستند، تعديل فاصل الحاشية السفلية، إضافة شرطة مخصصة، تغيير نمط الخط، وتعيين المحاذاة.

```java
import com.aspose.words.*;

public class FootnoteSeparatorDemo {
    public static void main(String[] args) throws Exception {
        // Load the source document
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // Retrieve the footnote separator paragraph
        Paragraph separator = doc.getFootnoteSeparator();

        // Set the desired alignment (center, left, right, or justify)
        separator.getParagraphFormat().setAlignment(ParagraphAlignment.CENTER);

        // Clear any existing content in the separator
        separator.getRuns().clear();

        // Add a custom dash – replace with any string to change footnote line
        separator.getRuns().add(new Run(doc, "—")); // Em‑dash as the custom dash

        // Save the updated document
        doc.save("YOUR_DIRECTORY/output.docx");
    }
}
```

**الناتج المتوقع:** يحتوي ملف `output.docx` على شرطة طويلة متمركزة حيث كان الخط الرفيع الأصلي. جميع الحواشي السفلية تظل سليمة، وتظهر تخطيطات المستند النمط الجديد للفاصل.

## المشكلات الشائعة وكيفية تجنبها

| المشكلة | السبب | الحل |
|-------|--------|-----|
| لم يتم العثور على الفاصل | المستند لا يحتوي على حواشي سفلية أو يستخدم نمط حاشية مخصص | تأكد من أن ملف DOCX المصدر يحتوي على حاشية سفلية واحدة على الأقل قبل استدعاء `getFootnoteSeparator()` |
| الشرطة المخصصة غير مرئية | الخط لا يدعم الحرف المختار | استخدم حرف Unicode مدعوم من الخط الافتراضي للمستند، أو قم بدمج خط متوافق |
| المحاذاة تبدو غير متغيرة | تنسيق الفقرة يتم تجاوزه لاحقًا في الكود | طبق المحاذاة **بعد** أي استدعاءات تنسيق أخرى قد تعيد تعيينها |

معالجة هذه النقاط تمنع أخطاء وقت التشغيل وتضمن أن عملية *كيفية تعديل الحاشية السفلية* تعمل بشكل موثوق.

## الخطوات التالية

الآن بعد أن عرفت **كيفية تعديل الحاشية السفلية**، يمكنك استكشاف المهام ذات الصلة:

* **إضافة نمط مرجع حاشية سفلية مخصص** – تعديل عقد `FootnoteReference` لتغيير الترقيم أو الرموز.
* **إدراج حواشي سفلية جديدة برمجياً** – استخدم `DocumentBuilder.insertFootnote()` للمحتوى الديناميكي.
* **تطبيق تنسيق شرطي** – تغيير مظهر الحاشية السفلية بناءً على نمط الفقرة أو طول المحتوى.

كل من هذه الإضافات يبني على نفس سطح الـ API الذي استخدمته لـ *add custom dash*، *change footnote line*، و *set paragraph alignment*.

---

*برمجة سعيدة! إذا ساعدك هذا الدليل في إتقان تعديل الحواشي السفلية، فكر في مشاركته مع فريقك أو تقديم طلب سحب لتحسين المثال أكثر.*

## ماذا يجب أن تتعلم بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات الموضحة في هذا الدليل. كل مورد يتضمن أمثلة شفرة كاملة مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف أساليب تنفيذ بديلة في مشاريعك الخاصة.

- [تعيين موضع الحاشية السفلية وملاحظة النهاية](/words/hindi/net/working-with-footnote-and-endnote/set-footnote-and-end-note-position/)
- [كيفية إنشاء حقول نموذج وإضافة محتوى باستخدام DocumentBuilder في Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [كيفية تعيين LoadOptions في Aspose.Words for Java](/words/english/java/document-loading-and-saving/using-load-options/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}