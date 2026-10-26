---
category: general
date: 2026-10-26
description: تعلم كيفية إنشاء مستند Word برمجيًا، وإضافة شكل، وإخفاء كائن في Word
  باستخدام Aspose.Words for Java – دليل خطوة بخطوة.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document programmatically
- how to hide shape
- how to add shape
- hide object in word
language: ar
lastmod: 2026-10-26
og_description: إنشاء مستند Word برمجيًا، تعلم كيفية إضافة شكل وإخفاء كائن في Word
  باستخدام Aspose.Words for Java. مثال كامل وقابل للتنفيذ.
og_image_alt: Screenshot of a Word document created programmatically with a hidden
  ellipse shape
og_title: إنشاء مستند Word برمجيًا – إضافة وإخفاء الأشكال في Java
schemas:
- author: Aspose
  dateModified: '2026-10-26'
  description: Learn how to create Word document programmatically, add a shape, and
    hide object in Word using Aspose.Words for Java – step‑by‑step guide.
  headline: Create Word document programmatically and add a shape in Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word automation
title: إنشاء مستند Word برمجيًا وإضافة شكل في Java
url: /ar/java/images-shapes/create-word-document-programmatically-and-add-a-shape-in-jav/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# إنشاء مستند Word برمجيًا وإضافة شكل في Java

إذا كنت بحاجة إلى **إنشاء مستند Word برمجيًا**، فإن هذا الدليل يوضح لك بالضبط كيفية القيام بذلك، إضافة شكل، ثم إخفاء الكائن في Word. سواءً كنت تبني مولد تقارير أو نظام عقود آلي، ستحصل على حل كامل وجاهز للتنفيذ في بضع دقائق فقط.

سوف تتعلم كيفية:

* تهيئة مستند Word باستخدام Aspose.Words for Java.  
* إدراج إهليلج (أو أي شكل آخر) باستخدام تقنية **how to add shape**.  
* إخفاء ذلك الشكل بحيث لا يظهر أبدًا عند فتح الملف، مُجيبًا على سؤال **how to hide shape**.  

لا توجد أدوات خارجية مطلوبة بخلاف مكتبة Aspose.Words، ويعمل الكود مع Java 17 وما بعدها.

## المتطلبات المسبقة

قبل أن تبدأ، تأكد من أن لديك:

* مجموعة تطوير جافا (JDK) 17 أو أحدث مثبتة.  
* Maven أو Gradle لإدارة التبعيات (المثال يستخدم Maven).  
* ترخيص صالح لـ Aspose.Words for Java (التقييم المجاني يكفي للاختبار).  

إذا كنت جديدًا على Aspose.Words، راجع دليل البدء الرسمي، لكنك لن تحتاج إلى قراءته لتتبع هذا الدليل.

## تبعية Maven

أضف التبعية التالية إلى ملف `pom.xml` الخاص بك:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.10</version> <!-- Use the latest stable version -->
</dependency>
```

> **نصيحة احترافية:** حافظ على تحديث رقم الإصدار؛ الإصدارات الأحدث تحتوي على إصلاحات للأخطاء المتعلقة بمعالجة الأشكال.

## الخطوة 1: إنشاء مستند Word برمجيًا – تهيئة المستند

أول شيء تقوم به عندما **تنشئ مستند Word برمجيًا** هو إنشاء كائن `Document`. هذا الكائن يمثل ملف .docx بالكامل في الذاكرة.

```java
import com.aspose.words.*;

public class WordShapeDemo {
    public static void main(String[] args) throws Exception {
        // Initialize a new empty document
        Document doc = new Document();

        // Create a DocumentBuilder to add content
        DocumentBuilder builder = new DocumentBuilder(doc);
```

*لماذا هذه الخطوة مهمة*: فئة `Document` هي نقطة الدخول لجميع عمليات معالجة Word. بدونها لا يمكنك إضافة صفحات أو فقرات أو أشكال.

## الخطوة 2: كيفية إضافة شكل – إدراج إهليلج

الآن نتناول جزء **how to add shape** في الدليل. تدعم Aspose.Words العديد من أنواع الأشكال (Ellipse، Rectangle، TextBox، إلخ). أدناه نقوم بإدراج إهليلج بعرض وارتفاع 50 نقطة.

```java
        // Insert an ellipse shape of size 50x50 points
        Shape ellipse = builder.insertShape(ShapeType.ELLIPSE, 50.0, 50.0);

        // Position the shape (optional)
        ellipse.setLeft(100);
        ellipse.setTop(100);
```

طريقة `insertShape` تُعيد كائن `Shape` يمكنك تخصيصه أكثر—اللون، نمط الخط، الدوران، وأكثر. تُقاس الإحداثيات بالنقاط (1/72 بوصة).

*لماذا قد ترغب في إضافة شكل*: الأشكال مفيدة كعلامات مائية، عناصر زخرفية، أو عناصر نائبة تقوم بإخفائها أو استبدالها لاحقًا.

## الخطوة 3: كيفية إخفاء الشكل – جعل الكائن غير مرئي في Word

للإجابة على سؤال **how to hide shape**، ما عليك سوى ضبط خاصية `Hidden` للشكل على `true`. هذا يخبر Word بمعاملة الشكل ككائن مخفي، بحيث لا يُظهره أبدًا في عرض المستند أو الطباعة.

```java
        // Hide the shape so it does not appear in the rendered document
        ellipse.setHidden(true);
```

إذا كنت بحاجة إلى **إخفاء كائن في Word** لمستخدم أو شرط معين، يمكنك تبديل هذه الخاصية أثناء التشغيل بناءً على منطق عملك.

> **ملاحظة:** الأشكال المخفية لا تزال جزءًا من بنية XML للمستند. يمكن كشفها لاحقًا بتعيين `setHidden(false)`.

## الخطوة 4: حفظ المستند

بعد إضافة الشكل وإخفائه، اكتب المستند إلى القرص.

```java
        // Save the document as a .docx file
        doc.save("HiddenShapeDemo.docx");
        System.out.println("Document created successfully.");
    }
}
```

عند فتح `HiddenShapeDemo.docx` في Microsoft Word، ستظهر صفحة فارغة لأن الإهليلج مخفي. المستند يتصرف كأي ملف Word عادي بخلاف ذلك.

## مثال كامل يعمل

بجمع كل الأجزاء معًا، إليك البرنامج الكامل القابل للتنفيذ:

```java
import com.aspose.words.*;

public class WordShapeDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a document programmatically
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: How to add shape – insert an ellipse (50x50 points)
        Shape ellipse = builder.insertShape(ShapeType.ELLIPSE, 50.0, 50.0);
        ellipse.setLeft(100);
        ellipse.setTop(100);

        // Step 3: How to hide shape – hide the ellipse so it never appears
        ellipse.setHidden(true);

        // Step 4: Save the file
        doc.save("HiddenShapeDemo.docx");
        System.out.println("Document created successfully.");
    }
}
```

**الناتج المتوقع**

```
Document created successfully.
```

فتح `HiddenShapeDemo.docx` يُظهر صفحة فارغة؛ الإهليلج المخفي لا يُظهر، مما يؤكد نجاح عملية **hide object in Word**.

## حالات خاصة وتنوعات

| الحالة | ما الذي يجب تغييره | السبب |
|-----------|----------------|-----|
| إخفاء مستطيل بدلاً من إهليلج | استخدم `ShapeType.RECTANGLE` في `insertShape` | عنصر نائب بصري مختلف |
| إخفاء عدة أشكال مرة واحدة | التكرار عبر `doc.getChildNodes(NodeType.SHAPE, true)` وتعيين `setHidden(true)` | مفيد للمعالجة الجماعية |
| إظهار الشكل فقط في عرض الطباعة | اضبط `shape.setVisible(false)` و `shape.setPrint(true)` | Word يميز بين رؤية الشاشة والطباعة |
| استخدام وحدة قياس مختلفة | استدعِ `builder.getDocument().getCompatibilityOptions().setMeasureUnit(MeasureUnit.INCHES)` | يتماشى مع متطلبات التخطيط الخاصة بك |

## الأخطاء الشائعة

* **نسيان استدعاء `setHidden(true)`** – سيظهر الشكل كالمعتاد.  
* **حفظ المستند قبل إخفاء الشكل** – الترتيب مهم؛ إخفِ أولًا، ثم احفظ.  
* **استخدام إصدار قديم من Aspose.Words** – الإصدارات القديمة قد تفتقر إلى واجهة `setHidden`.  

اختبر دائمًا الملف المُولد في نسخة Microsoft Word المستهدفة لضمان سلوك الحالة المخفية كما هو متوقع.

## الخلاصة

في هذا الدليل تعلمت كيفية **إنشاء مستند Word برمجيًا**، **إضافة شكل**، و**إخفاء كائن في Word** باستخدام Aspose.Words for Java. المثال الكامل يوضح الخطوات الدقيقة، من تهيئة المستند إلى حفظ ملف لا يظهر فيه الشكل أبدًا.

من هنا يمكنك:

* تجربة أنواع أشكال أخرى (`ShapeType.LINE`, `ShapeType.TEXT_BOX`).  
* دمج الأشكال المخفية مع العلامات المرجعية لإنشاء قوالب ديناميكية.  
* استكشاف خصائص `setVisible` و `setPrint` لمزيد من التحكم الدقيق في رؤية الكائن.

برمجة سعيدة، واستمتع بأتمتة مستندات Word الخاصة بك!

## ما الذي يجب أن تتعلمه بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات الموضحة في هذا الدليل. كل مورد يتضمن أمثلة شفرة كاملة مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف أساليب تنفيذ بديلة في مشاريعك.

- [كيفية إنشاء مستند Word فارغ باستخدام Aspose.Words for Java](/words/english/java/document-manipulation/how-to-create-blank-word-document-with-aspose-words-for-java/)
- [كيفية إخفاء شكل في مستند Word باستخدام Java](/words/english/java/images-shapes/how-to-hide-shape-in-a-word-document-using-java/)
- [إنشاء مستند Word Java – إضافة شكل مستطيل مع تأثير الظل](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}