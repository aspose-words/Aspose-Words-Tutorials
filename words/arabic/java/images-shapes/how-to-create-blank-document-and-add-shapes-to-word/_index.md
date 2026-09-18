---
category: general
date: 2026-09-18
description: إنشاء مستند فارغ وإدراج أشكال إلى Word باستخدام Aspose.Words – تعلّم
  كيفية إضافة شكل مثلث والمزيد.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank document
- add shapes to word
- how to insert triangle
- add triangle shape
- create word document
language: ar
lastmod: 2026-09-18
og_description: إنشاء مستند فارغ في Word باستخدام Aspose.Words وتعلم كيفية إدراج شكل
  مثلث، تجميع الأشكال، وغيرها من الرسومات. اتبع هذا الدليل الكامل.
og_image_alt: Screenshot of a Word document showing a grouped shape with a triangle
  inside
og_title: إنشاء مستند فارغ وإضافة أشكال إلى Word – دليل خطوة بخطوة
schemas:
- author: Aspose
  dateModified: '2026-09-18'
  description: Create blank document and insert shapes to Word with Aspose.Words –
    learn how to add a triangle shape and more.
  headline: How to create blank document and add shapes to Word
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word automation
- Shapes
title: كيفية إنشاء مستند فارغ وإضافة أشكال إلى Word
url: /ar/java/images-shapes/how-to-create-blank-document-and-add-shapes-to-word/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# كيفية إنشاء مستند فارغ وإضافة أشكال إلى Word

إذا كنت بحاجة إلى **إنشاء مستند فارغ** ثم إغنائه بالرسومات، يوضح لك هذا الدليل بالضبط كيفية القيام بذلك. سنستعرض إنشاء ملف Word من الصفر و **إضافة أشكال إلى Word**، بما في ذلك **كيفية إدراج شكل مثلث**، باستخدام Aspose.Words for Java.

سوف تنتهي من الدرس بملف *.docx* جاهز للاستخدام يحتوي على شكل مجموعة يحمل مثلثًا. تغطي الخطوات كل شيء من إعداد المشروع إلى حفظ **إنشاء مستند Word** النهائي. لا توجد أدوات خارجية مطلوبة بخلاف Aspose.Words.

## المتطلبات المسبقة

* Java 17 أو أحدث مثبت  
* Maven أو Gradle لإدارة التبعيات  
* ترخيص Aspose.Words for Java (التقييم المجاني يعمل لهذا العرض)

إذا كنت تفضل نظام بناء مختلف، قم بتعديل صياغة التبعيات وفقًا لذلك. يعمل الكود على أي منصة تدعم Java.

## إنشاء مستند فارغ باستخدام Aspose.Words

العملية الأولى هي **إنشاء مستند فارغ** في الذاكرة. توفر Aspose.Words فئة `Document` التي تمثل ملف Word بدون أي محتوى.

```java
import com.aspose.words.*;

public class ShapeDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document
        Document doc = new Document();               // create blank document
```

يقوم المُنشئ `new Document()` بإنشاء بنية *.docx* فارغة، يمكنك لاحقًا ملؤها بالفقرات أو الجداول أو الرسومات. بما أن المستند فارغ، لديك سيطرة كاملة على كل عنصر تضيفه.

## إضافة أشكال إلى Word – إدراج شكل مجموعة

يسمح لك شكل المجموعة بمعاملة عدة رسومات كوحدة واحدة. هذا مفيد عندما تريد نقل أو تغيير حجم عدة أشكال معًا.

```java
        // Step 2: Initialize a DocumentBuilder to construct content
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 3: Insert a group shape of size 300 × 300 points
        GroupShape group = builder.insertGroupShape(300.0, 300.0);
```

`DocumentBuilder` هو الـ API الأساسي لإضافة المحتوى. تُنشئ استدعاء `insertGroupShape` حاوية بحجم 300 × 300 نقطة (تقريبًا 4 × 4 بوصة). بعد هذا الاستدعاء يتم وضع المؤشر *داخل* المجموعة، جاهزًا لأشكال إضافية.

### لماذا نستخدم شكل مجموعة؟

تجميع الرسومات المرتبطة يحافظ على محاذاتها ويسهل تطبيق تنسيق موحد. إذا قررت لاحقًا نقل المثلث، فإن المجموعة بأكملها تتحرك معًا، مما يحافظ على التخطيط.

## كيفية إدراج شكل مثلث داخل المجموعة

الآن نتناول **كيفية إدراج مثلث**. المثلث هو أحد القيم المدمجة في `ShapeType`.

```java
        // Step 4: Move the cursor into the group's first paragraph
        builder.moveTo(group.getFirstParagraph());

        // Step 5: Insert a triangle shape of size 60 × 60 points inside the group
        builder.insertShape(ShapeType.TRIANGLE, 60.0, 60.0);
```

يضمن استدعاء `moveTo` أن نقطة إدراج الـ builder هي الفقرة الأولى في المجموعة. ثم يضيف `insertShape` مثلثًا بحجم 60 × 60 نقطة. بما أن المؤشر داخل المجموعة، يصبح المثلث عنصرًا فرعيًا لشكل المجموعة.

**نصائح لإضافة شكل مثلث**:

* الحجم يُقاس بالنقاط؛ 72 نقطة تساوي بوصة واحدة. عدّل الأبعاد لتناسب تخطيطك.  
* إذا كنت بحاجة إلى توجيه مختلف، استخدم `builder.getCurrentParagraph().getParagraphFormat().setAlignment()` لمحاذاة الشكل داخل المجموعة.  
* يرث المثلث تعبئة المجموعة وأنماط الخط ما لم تقم بتجاوزها باستخدام `shape.getFillColor()` أو `shape.getStrokeColor()`.

## حفظ المستند – إنشاء مستند Word

بعد إنشاء الرسومات، تقوم بحفظ الملف. هذه الخطوة تُنهي عملية **إنشاء مستند Word**.

```java
        // Step 6: Save the document with the extended group shape
        doc.save("ExtendedGroup.docx");               // create word document
    }
}
```

`doc.save` يكتب التمثيل الموجود في الذاكرة إلى القرص كملف Word قياسي. يمكنك فتح `ExtendedGroup.docx` في Microsoft Word أو LibreOffice أو أي عارض يدعم تنسيق OOXML. سيعرض الملف شكل مجموعة يحتوي على مثلث، تمامًا كما تم إنشاؤه بالكود.

## مثال كامل قابل للتنفيذ

بجمع جميع الأجزاء معًا، إليك البرنامج الكامل الذي يمكنك نسخه، تجميعه، وتشغيله:

```java
import com.aspose.words.*;

public class ShapeDemo {
    public static void main(String[] args) throws Exception {
        // 1. Create a new blank document
        Document doc = new Document();

        // 2. Prepare a builder for inserting content
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 3. Insert a group shape (300 × 300 points)
        GroupShape group = builder.insertGroupShape(300.0, 300.0);

        // 4. Position the cursor inside the group
        builder.moveTo(group.getFirstParagraph());

        // 5. Insert a triangle shape (60 × 60 points)
        builder.insertShape(ShapeType.TRIANGLE, 60.0, 60.0);

        // 6. Save the file – this creates the final Word document
        doc.save("ExtendedGroup.docx");
    }
}
```

### النتيجة المتوقعة

عند فتح `ExtendedGroup.docx`، سترى شكل مجموعة واحد يملأ وسط الصفحة. داخل تلك المجموعة، يظهر مثلث صغير في الموضع الافتراضي. يمكن تحديد المثلث وتحريكه كجزء من المجموعة، مما يؤكد أن **إضافة أشكال إلى Word** عملت كما هو مقصود.

## الأسئلة الشائعة والحالات الخاصة

| السؤال | الجواب |
|----------|--------|
| *هل يمكنني إضافة أكثر من شكل واحد داخل المجموعة؟* | نعم. بعد إدراج المثلث، احتفظ بالمؤشر داخل المجموعة واستدعِ `builder.insertShape` مرة أخرى بنوع `ShapeType` مختلف. |
| *ماذا لو أردت أن يكون المثلث أحمر؟* | احصل على كائن `Shape` الذي تُعيده `insertShape` واستدعِ `shape.getFillColor().setColor(Color.RED)`. |
| *هل يعمل هذا مع ملفات .doc القديمة؟* | يقوم Aspose.Words بالحفظ بالتنسيق الذي تحدده. استخدم `doc.save("file.doc", SaveFormat.DOC)` لإنشاء مستند Word قديم. |
| *كيف يمكنني تغيير حدود المجموعة؟* | استخدم `group.getStrokeColor().setColor(Color.BLUE)` و `group.setLineWeight(2.0)` لتخصيص الحدود. |
| *هل هناك طريقة لتدوير المثلث؟* | استدعِ `shape.getRotation()` لتعيين زاوية بالدرجات. |

## نصائح احترافية

* **إعادة استخدام الـ builder** – إنشاء `DocumentBuilder` جديد لكل شكل يضيف عبئًا. احتفظ بـ builder واحد لكل مستند.  
* **تحويل الوحدات** – إذا كنت تعمل بالمليمترات، حوّلها إلى نقاط (`points = mm * 2.83465`).  
* **الأداء** – للمستندات الكبيرة، استدعِ `doc.updatePageLayout()` مرة واحدة فقط بعد إضافة جميع الأشكال.

## الخلاصة

أنت الآن تعرف كيفية **إنشاء مستند فارغ**، **إضافة أشكال إلى Word**، وبشكل خاص **كيفية إدراج مثلث** باستخدام Aspose.Words for Java. يوضح المثال الكامل سير العمل بالكامل من ملف فارغ إلى **إنشاء مستند Word** محفوظ يحتوي على مثلث مجموعة.

من هنا يمكنك استكشاف قيم `ShapeType` إضافية، تطبيق تنسيقات مخصصة، أو دمج مجموعات متعددة لبناء مخططات معقدة. جرّب أحجامًا، ألوانًا، ومواقع مختلفة لتتقن أتمتة Word في Java.

--- 

*هل أنت مستعد لأتمتة تقريرك التالي؟ استنسخ المثال، عدّل الأبعاد، ودمج الكود في تطبيقك الخاص اليوم.*

## ما الذي يجب أن تتعلمه بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات الموضحة في هذا الدليل. كل مورد يتضمن أمثلة كود كاملة مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف أساليب تنفيذ بديلة في مشاريعك.

- [إنشاء شكل مجموعة في مستند Word باستخدام Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [إنشاء مستند Word فارغ مع شكل مستطيل بظل – دليل خطوة بخطوة](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [إنشاء شكل مستطيل في Word باستخدام Aspose.Words – دليل خطوة بخطوة](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}