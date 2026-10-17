---
category: general
date: 2026-01-11
description: أنشئ مستند Word باستخدام Java بسرعة عن طريق إضافة شكل مستطيل، وضبط لون
  التعبئة، وتطبيق ظل على الشكل. تعلم خطوة بخطوة.
draft: false
keywords:
- create word document java
- add rectangle shape
- apply shadow to shape
- set shape fill color
- how to add shape
language: ar
og_description: إنشاء مستند Word باستخدام Java عن طريق إدراج شكل مستطيل، وتعيين لون
  التعبئة، وتطبيق ظل. دليل كامل مع الشيفرة.
og_title: إنشاء مستند Word باستخدام Java – إضافة شكل مستطيل مع الظل
tags:
- Aspose.Words
- Java
- Document Generation
title: إنشاء مستند Word باستخدام Java – إضافة شكل مستطيل مع تأثير الظل
url: /ar/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# إنشاء مستند Word باستخدام Java – إضافة شكل مستطيل مع تأثير الظل

هل احتجت يوماً إلى **create word document java** وجعل المستند يبدو أكثر احترافية؟ ربما تقوم بإنشاء مولد تقارير ولا يكفي أن يكون الصفحات عادية. الخبر السار؟ باستخدام Aspose.Words for Java يمكنك إضافة شكل مستطيل إلى المستند، إعطائه لونًا، وحتى إضافة ظل خفيف عليه—all in a handful of lines.

في هذا الدرس سنستعرض خطوة بخطوة كيفية إضافة شكل مستطيل، ضبط لون التعبئة، وتطبيق ظل على الشكل حتى يصبح ملف Word الخاص بك أكثر احترافية. في النهاية ستحصل على مثال جاهز للتنفيذ يمكنك نسخه‑لصقه في مشروعك.

## ما الذي ستحتاجه

- **Java 17** (أو أي JDK حديث) – الكود يستخدم ميزات اللغة القياسية.
- مكتبة **Aspose.Words for Java** – يفضَّل الإصدار 23.9 أو أحدث.
- بيئة تطوير أو محرر نصوص تختاره – IntelliJ IDEA، Eclipse، VS Code… إلخ.
- مجلد سيتم حفظ الملف `ShadowShape.docx` فيه.

لا حاجة لأي إعدادات إضافية؛ فقط أضف ملف JAR الخاص بـ Aspose.Words إلى مسار الـ classpath وستكون جاهزًا.

## الخطوة 1: إعداد المشروع واستيراد Aspose.Words

أولاً، أنشئ مشروع Maven (أو Gradle) وأضف تبعية Aspose.Words. إليك مقطع `pom.xml` بسيط لـ Maven:

```xml
<dependencies>
    <dependency>
        <groupId>com.aspose</groupId>
        <artifactId>aspose-words</artifactId>
        <version>23.9</version>
        <classifier>jdk17</classifier>
    </dependency>
</dependencies>
```

إذا لم تكن تستخدم Maven، فقط ضع ملف JAR في مجلد `libs` وأضفه إلى مسار البناء.

> **نصيحة احترافية:** Aspose توفر ترخيص تجريبي مجاني يمكنك تضمينه بـ `License license = new License(); license.setLicense("Aspose.Words.lic");`. يمكنك تخطيه للاختبارات السريعة؛ المكتبة تعمل في وضع التقييم.

## الخطوة 2: إنشاء مستند جديد وDocumentBuilder

الآن سنقوم فعليًا **create word document java**. فئة `Document` تمثل ملف .docx بالكامل، بينما يتيح لنا `DocumentBuilder` إدراج المحتوى.

```java
import com.aspose.words.*;

public class ShadowEffectDemo {
    public static void main(String[] args) throws Exception {
        // Initialize a blank Word document
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);
```

في هذه المرحلة لديك مستند فارغ جاهز لاستقبال الأشكال، الفقرات، أو أي شيء آخر تحتاجه.

## الخطوة 3: إدراج شكل مستطيل وضبط لون التعبئة

إضافة شكل بسيطة مثل استدعاء `insertShape`. سنستخدم تقنية **add rectangle shape**، والتي تُعد من الكلمات المفتاحية الثانوية *add rectangle shape*.

```java
        // Insert a rectangle shape – 200pt wide, 100pt tall
        Shape rectangle = builder.insertShape(ShapeType.RECTANGLE, 200, 100);

        // Set the fill color to a bright orange
        rectangle.setFillColor(java.awt.Color.ORANGE);
```

لماذا اللون البرتقالي؟ لأنه يبرز في خلفية بيضاء، لكن يمكنك استبداله بأي `java.awt.Color` تفضله. هذه الخطوة تغطي الكلمة المفتاحية الثانوية *set shape fill color*.

## الخطوة 4: ضبط مظهر الظل – تطبيق ظل على الشكل

الآن يأتي الجزء الممتع: إضافة ظل خفيف للمستطيل. توفر API الخاصة بـ Aspose كائن `ShadowFormat` يتحكم في جميع جوانب الظل.

```java
        // Get the shadow format object for the shape
        ShadowFormat shadow = rectangle.getShadowFormat();

        // Make the shadow visible
        shadow.setVisible(true);

        // Choose a neutral gray for the shadow color
        shadow.setColor(java.awt.Color.GRAY);

        // Blur radius – larger values produce a softer edge
        shadow.setBlur(5.0);

        // Offset determines how far the shadow is displaced
        shadow.setOffsetX(4.0);
        shadow.setOffsetY(4.0);

        // Transparency (0 = opaque, 1 = fully transparent)
        shadow.setTransparency(0.2);

        // Define the shadow style and type
        shadow.setStyle(ShadowStyle.OUTER);
        shadow.setType(ShadowType.PARALLEL);

        // Scale controls the overall size of the shadow relative to the shape
        shadow.setScale(1.0);
```

هذا المقطع من الكود **apply shadow to shape** تمامًا كما توحي الكلمة المفتاحية الثانوية. يمكنك تعديل `blur`، `offsetX/Y`، و`transparency` لتناسب أسلوب التصميم الخاص بك. على سبيل المثال، قيمة `offsetX` أكبر تُنتج ظلًا أكثر دراماتيكية، بينما `transparency` أعلى يجعل الظل يهمس بدلاً من الصراخ.

## الخطوة 5: حفظ المستند

أخيرًا، نكتب المستند إلى القرص. اختر مجلدًا لديك صلاحية كتابة فيه، ومنح الملف اسمًا واضحًا.

```java
        // Save the result – adjust the path as needed
        document.save("YOUR_DIRECTORY/ShadowShape.docx");
    }
}
```

عند فتح `ShadowShape.docx` في Microsoft Word أو LibreOffice، ستظهر لك مستطيل برتقالي ساطع مع ظل رمادي ناعم يطفو تحته مباشرة.

![create word document java with rectangle shape](/images/shadow-rectangle.png "create word document java – rectangle with shadow")

*نص بديل الصورة يتضمن الكلمة المفتاحية الأساسية، مما يحقق شرط تحسين محركات البحث.*

## أسئلة شائعة وحالات خاصة

### ماذا لو احتجت إلى شكل مختلف؟

يدعم Aspose.Words عشرات القيم في `ShapeType` – نجوم، أسهم، تعليقات توضيحية، وما إلى ذلك. ما عليك سوى استبدال `ShapeType.RECTANGLE` بـ `ShapeType.OVAL` أو أي ثابت آخر. خطوات **how to add shape** تبقى نفسها.

### كيف أضيف الشكل إلى فقرة محددة؟

بدلاً من إدراج الشكل مباشرةً عبر الـ builder، يمكنك إنشاء الشكل أولًا (`new Shape(document, ShapeType.RECTANGLE)`) ثم إضافته إلى `Paragraph` عبر `paragraph.appendChild(shape)`. يمنحك ذلك تحكمًا أدق في التخطيط.

### هل يمكنني تطبيق تعبئة تدرجية بدلاً من لون صلب؟

نعم! استخدم `rectangle.getFill().setFillType(FillType.GRADIENT)` وعَرِّف `LinearGradientFill`. الـ API أكثر تفصيلاً، لكنه يعمل بشكل ممتاز لتصاميم حديثة.

### ماذا عن التوافق مع إصدارات Word القديمة؟

يحفظ Aspose.Words المستند بصيغة .docx افتراضيًا، وهي مدعومة من Word 2007+ وLibreOffice. إذا احتجت إلى .doc، استدعِ `document.save("file.doc", SaveFormat.DOC)`. قد يختلف عرض الظل قليلًا، لكن الشكل يبقى كما هو.

## مثال كامل جاهز للتنفيذ (نسخ‑لصق)

فيما يلي البرنامج الكامل، جاهز للترجمة والتنفيذ. استبدل `YOUR_DIRECTORY` بمسار فعلي على جهازك.

```java
import com.aspose.words.*;

public class ShadowEffectDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new document and a builder
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Step 2: Insert a rectangle shape and set its fill color
        Shape rectangle = builder.insertShape(ShapeType.RECTANGLE, 200, 100);
        rectangle.setFillColor(java.awt.Color.ORANGE);

        // Step 3: Apply shadow to shape
        ShadowFormat shadow = rectangle.getShadowFormat();
        shadow.setVisible(true);
        shadow.setColor(java.awt.Color.GRAY);
        shadow.setBlur(5.0);
        shadow.setOffsetX(4.0);
        shadow.setOffsetY(4.0);
        shadow.setTransparency(0.2);
        shadow.setStyle(ShadowStyle.OUTER);
        shadow.setType(ShadowType.PARALLEL);
        shadow.setScale(1.0);

        // Step 4: Save the document
        document.save("YOUR_DIRECTORY/ShadowShape.docx");
    }
}
```

تشغيل هذا الكود ينتج ملف Word يحتوي على المستطيل البرتقالي مع ظل رمادي ناعم – تمامًا ما سعى إليه الدرس عندما أردنا **create word document java** مع شكل مُصمم.

## الخلاصة

الآن لديك وصفة شاملة من البداية إلى النهاية لإنشاء **create word document java** يضيف *rectangle shape*، *sets shape fill color*، و*applies shadow to shape*. النهج بسيط، والـ API سهل الاستخدام، ويمكنك توسيعه بطرق لا حصر لها – أشكال مختلفة، تعبئات تدرجية، أو حتى ظلال متعددة لكل شكل.

ما الخطوة التالية؟ جرّب تراكب عدة أشكال، أو استكشف `ShadowStyle.ETCHED` للحصول على مظهر مختلف، أو اجمع ذلك مع توليد الجداول لبناء تقارير متكاملة. الإمكانيات محدودة فقط بخيالك (ورخصة Aspose التي تمتلكها).

إذا واجهت أي صعوبات أو لديك أفكار لتطوير إضافي، اترك تعليقًا أدناه. برمجة سعيدة، واستمتع بجعل مستندات Word أقل رتابة!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}