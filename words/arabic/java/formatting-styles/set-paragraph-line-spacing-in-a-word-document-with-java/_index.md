---
category: general
date: 2026-11-15
description: ضبط تباعد أسطر الفقرة في مستند Word باستخدام Java. تعلم كيفية ضبط تباعد
  الأسطر برمجيًا باستخدام Aspose.Words لتنسيق المستند بدقة.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- set paragraph line spacing
- how to set line spacing
language: ar
lastmod: 2026-11-15
og_description: تعيين تباعد أسطر الفقرات في مستند Word باستخدام Java. يشرح هذا الدليل
  كيفية تعيين تباعد الأسطر للفقرات وفواصل الحواشي باستخدام Aspose.Words، مما يمنحك
  سيطرة كاملة على تخطيط المستند.
og_image_alt: Screenshot showing Java code that sets paragraph line spacing in a Word
  document
og_title: ضبط تباعد أسطر الفقرة في Word باستخدام Java
schemas:
- author: Aspose
  dateModified: '2026-11-15'
  description: Set paragraph line spacing in a Word document with Java. Learn how
    to set line spacing programmatically using Aspose.Words for precise document formatting.
  headline: Set paragraph line spacing in a Word document with Java
  type: TechArticle
- description: Set paragraph line spacing in a Word document with Java. Learn how
    to set line spacing programmatically using Aspose.Words for precise document formatting.
  name: Set paragraph line spacing in a Word document with Java
  steps:
  - name: Load the Word document
    text: First, create a `Document` instance that points to your source file.
  - name: Retrieve the footnote separator
    text: Footnote separators are special paragraphs that appear between footnotes
      and the main text. To change their appearance you need to access the `FootnoteSeparator`
      object.
  - name: How to set line spacing for the separator's paragraph
    text: Now apply the desired line spacing. Aspose.Words uses points for line‑spacing
      values; 12 pts is roughly single‑spacing for most fonts.
  - name: Save the updated document
    text: Finally, write the changes back to disk.
  type: HowTo
tags:
- Java
- Aspose.Words
- Document Formatting
title: تعيين تباعد أسطر الفقرة في مستند Word باستخدام Java
url: /ar/java/formatting-styles/set-paragraph-line-spacing-in-a-word-document-with-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# ضبط تباعد الأسطر للفقرة في مستند Word باستخدام Java

إذا كنت بحاجة إلى **ضبط تباعد الأسطر للفقرة** في مستند Word، يوضح لك هذا الدرس كيفية القيام بذلك باستخدام Java و Aspose.Words. ستتعلم أيضًا **كيفية ضبط تباعد الأسطر** لفواصل الحواشي — وهو طلب شائع عند تنسيق المستندات المهنية.

في الأقسام التالية سوف تقوم بـ:

* تحميل ملف *.docx* موجود.
* استرجاع فقرة فاصل الحاشية.
* تطبيق قيمة مخصصة لتباعد الأسطر.
* حفظ المستند المحدث.

لا يلزم أي إعداد خارجي بخلاف إضافة مكتبة Aspose.Words إلى مشروعك، لذا يمكنك نسخ الشيفرة كما هي وتشغيلها فورًا.

## المتطلبات المسبقة

قبل أن تبدأ، تأكد من وجود ما يلي:

* Java 17 أو أحدث مثبتة.
* Maven (أو أداة بناء أخرى) لإدارة الاعتمادات.
* رخصة صالحة لـ Aspose.Words for Java (التقييم المجاني يكفي للاختبار).
* مستند Word إدخالي (`input.docx`) موجود في دليل معروف.

أضف اعتماد Aspose.Words إلى ملف `pom.xml` الخاص بك:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.10</version> <!-- Use the latest stable version -->
</dependency>
```

## ضبط تباعد الأسطر للفقرة باستخدام Aspose.Words

هذا العنوان من المستوى H2 يحتوي على الكلمة المفتاحية الأساسية، لتلبية متطلبات تحسين محركات البحث.

### الخطوة 1: تحميل مستند Word

أولاً، أنشئ كائن `Document` يشير إلى ملف المصدر الخاص بك.

```java
import com.aspose.words.*;

public class LineSpacingExample {
    public static void main(String[] args) throws Exception {
        // Load the Word document from the specified path
        Document doc = new Document("YOUR_DIRECTORY/input.docx");
        // Continue with formatting...
    }
}
```

*لماذا هذا مهم*: تحميل المستند يمنحك نموذجًا في الذاكرة يمكنك تعديلَه دون لمس الملف الأصلي حتى تقوم بحفظه صراحةً.

### الخطوة 2: استرجاع فاصل الحاشية

فواصل الحواشي هي فقرات خاصة تظهر بين الحواشي والنص الرئيسي. لتغيير مظهرها تحتاج إلى الوصول إلى كائن `FootnoteSeparator`.

```java
// Retrieve the footnote separator that Aspose.Words represents internally
FootnoteSeparator separator = doc.getFootnoteSeparator();
```

*نصيحة*: إذا لم يحتوي مستندك على حواشي، فإن الفاصل لا يزال موجودًا كفقرة مخفية، لذا لن تُعيد الدالة القيمة `null` أبدًا.

### الخطوة 3: كيفية ضبط تباعد الأسطر لفقرة الفاصل

الآن طبّق تباعد الأسطر المطلوب. يستخدم Aspose.Words النقاط كوحدات لقيم تباعد الأسطر؛ 12 نقطة تقريبًا تعادل تباعدًا أحاديًا لمعظم الخطوط.

```java
// Set the line spacing to 12 points (single‑spacing)
separator.getParagraphFormat().setLineSpacing(12.0);
```

يمكنك أيضًا استخدام أوضاع تباعد أخرى:

| الوضع                     | استدعاء الطريقة                                      |
|--------------------------|------------------------------------------------------|
| **بالضبط** (نقاط ثابتة) | `setLineSpacingRule(LineSpacingRule.EXACTLY)`       |
| **متعدد** (مثلاً 1.5)    | `setLineSpacingRule(LineSpacingRule.MULTIPLE); setLineSpacing(1.5);` |

اختيار القاعدة الصحيحة يضمن أن يُظهر المستند بشكل متسق عبر Word و Google Docs وغيرها من عارضات المستندات.

### الخطوة 4: حفظ المستند المحدث

أخيرًا، اكتب التغييرات إلى القرص.

```java
// Save the modified document to a new file
doc.save("YOUR_DIRECTORY/output.docx");
System.out.println("Document saved with updated paragraph line spacing.");
```

عند فتح `output.docx` في Microsoft Word، سيظهر فاصل الحاشية بتباعد الأسطر الذي حددته.

## فهم كيفية ضبط تباعد الأسطر للفقرات العادية

نفس الـ API يعمل مع أي كائن `Paragraph`، ليس فقط فواصل الحواشي. إليك مثالًا سريعًا يضبط تباعد الفقرة الأولى في الجسم:

```java
// Access the first body paragraph
Paragraph firstPara = (Paragraph) doc.getFirstSection().getBody().getChild(NodeType.PARAGRAPH, 0, true);

// Apply double line spacing (2.0 × the font size)
firstPara.getParagraphFormat().setLineSpacingRule(LineSpacingRule.MULTIPLE);
firstPara.getParagraphFormat().setLineSpacing(2.0);
```

**لماذا قد تحتاج هذا**: التقارير، العقود، والأوراق الأكاديمية غالبًا ما تتطلب نمط تباعد أسطر محدد (مثل التباعد المزدوج للمسودات). استخدام طريقة `setLineSpacing` نفسها يضمن التخطيط الدقيق الذي تتوقعه.

## الأخطاء الشائعة وكيفية تجنّبها

| المشكلة                                 | السبب                                      | الحل |
|----------------------------------------|--------------------------------------------|------|
| تباعد الأسطر لا يتغيّر                  | ترك `LineSpacingRule` على القيمة الافتراضية (AUTO) | عيّن القاعدة صراحةً باستخدام `setLineSpacingRule`. |
| ظهور أسطر فارغة إضافية بعد الفاصل       | يحتوي الفاصل على عوائد سطر مخفية            | قص نص الفاصل بـ `separator.getText().trim();` قبل ضبط التباعد. |
| فساد المستند بعد الحفظ                  | استخدام نسخة قديمة من Aspose.Words          | حدّث إلى أحدث نسخة (مثلاً 24.10) التي تحتوي على إصلاحات للأخطاء المتعلقة بالحفظ. |

## نصيحة احترافية: معالجة دفعة من المستندات

إذا كنت بحاجة لتحديث العشرات من الملفات، غلف المنطق في طريقة مساعدة وكرّرها على مجلد:

```java
public static void updateSpacing(Path inputPath, Path outputPath) throws Exception {
    Document doc = new Document(inputPath.toString());
    FootnoteSeparator sep = doc.getFootnoteSeparator();
    sep.getParagraphFormat().setLineSpacing(12.0);
    doc.save(outputPath.toString());
}
```

تشغيل هذه الطريقة داخل حلقة يوفر لك ساعات من التحرير اليدوي.

## النتيجة المتوقعة

بعد تشغيل البرنامج الكامل، سيقوم `output.docx` بـ:

* الاحتفاظ بالمحتوى الأصلي دون تغيير باستثناء تباعد الأسطر.
* عرض فاصل الحاشية بتباعد أحادي (12 نقطة).
* الحفاظ على جميع التنسيقات الأخرى (الأنماط، الصور، الجداول).

افتح الملف في Word وتأكد من أن خط الفاصل أصبح أكثر ضيقًا (أو أوسع، حسب القيمة التي ضبطتها).

## الخلاصة

أنت الآن تعرف كيف **تضبط تباعد الأسطر للفقرة** في مستند Word باستخدام Java، وتفهم أيضًا **كيفية ضبط تباعد الأسطر** لكل من فواصل الحواشي والفقرات العادية. المثال الكامل القابل للتنفيذ يوضح تحميل المستند، تعديل خصائص تباعد الأسطر، وحفظ النتيجة — كل ذلك عبر عدد قليل من استدعاءات الـ API الواضحة.

**الخطوات التالية** التي قد تستكشفها:

* **كيفية ضبط تباعد الأسطر** للجداول وعناصر القوائم.
* تطبيق قواعد تباعد مختلفة للعناوين مقارنةً بنص الجسم.
* استخدام كائن `Style` لفرض التباعد عبر المستند بأكمله.

جرّب القيم، اجمعها مع خيارات تنسيق أخرى، وستحصل على تحكم كامل في تخطيط المستند في أي تطبيق Java. Happy coding!

## ما الذي يجب أن تتعلمه بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات التي تم توضيحها في هذا الدليل. كل مورد يتضمن أمثلة شيفرة كاملة مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف أساليب تنفيذ بديلة في مشاريعك الخاصة.

- [كيفية ضبط الخيارات في Aspose.Words for Java – دليل كامل](/words/english/java/document-loading-and-saving/how-to-set-options-in-aspose-words-for-java-complete-guide/)
- [كيفية ضبط LoadOptions في Aspose.Words for Java](/words/english/java/document-loading-and-saving/using-load-options/)
- [تغيير تباعد الفقرات الآسيوية والمسافات البادئة في مستند Word](/words/english/net/document-formatting/change-asian-paragraph-spacing-and-indents/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}