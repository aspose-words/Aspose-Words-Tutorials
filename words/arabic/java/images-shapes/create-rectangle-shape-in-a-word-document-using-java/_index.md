---
category: general
date: 2026-11-15
description: إنشاء شكل مستطيل في Word باستخدام Java وتعلم كيفية إضافة الأشكال إلى
  Word، وتحديد أبعاد الشكل، وحفظ مستند Word بكفاءة.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create rectangle shape
- add shapes to word
- save word document
- set shape dimensions
- define shape size
language: ar
lastmod: 2026-11-15
og_description: إنشاء شكل مستطيل في مستند Word باستخدام Java. تعلم كيفية إضافة الأشكال
  إلى Word، وتحديد أبعاد الشكل، وحفظ مستند Word في دقائق.
og_image_alt: Screenshot showing a rectangle shape inside a group shape in a Word
  document
og_title: إنشاء شكل مستطيل في Word باستخدام Java – دليل خطوة بخطوة
schemas:
- author: Aspose
  dateModified: '2026-11-15'
  description: Create rectangle shape in Word with Java and learn how to add shapes
    to Word, set shape dimensions, and save Word document efficiently.
  headline: Create rectangle shape in a Word document using Java
  type: TechArticle
- description: Create rectangle shape in Word with Java and learn how to add shapes
    to Word, set shape dimensions, and save Word document efficiently.
  name: Create rectangle shape in a Word document using Java
  steps:
  - name: Prerequisites
    text: '* Java 17 or later (the code compiles with Java 8 as well). * Aspose.Words
      for Java 23.10 or newer – you can obtain it from Maven Central. * A basic understanding
      of Java syntax and object‑oriented concepts.'
  - name: Expected output
    text: '* A Word file named `RectangleShapeDemo.docx`. * Inside the first paragraph,
      a group shape containing a 100 pt × 50 pt rectangle. * No text is added, so
      the rectangle appears on a blank page.'
  - name: What’s next?
    text: '* Explore **add shapes to Word** by inserting circles, arrows, or text
      boxes. * Combine multiple shapes into a single `GroupShape` and apply transformations
      (rotate, flip). * Generate reports that embed charts as shapes, then **save
      Word document** as PDF for sharing.'
  type: HowTo
tags:
- Aspose.Words
- Java
- Word automation
title: إنشاء شكل مستطيل في مستند Word باستخدام Java
url: /ar/java/images-shapes/create-rectangle-shape-in-a-word-document-using-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# إنشاء شكل مستطيل في مستند Word باستخدام Java

إذا كنت بحاجة إلى **إنشاء شكل مستطيل** داخل ملف Word، يوضح لك هذا الدليل بالضبط كيفية القيام بذلك باستخدام Java. سترى كيفية **إضافة أشكال إلى Word**، والتحكم في **تحديد أبعاد الشكل**، وأخيرًا **حفظ مستند Word** دون مغادرة بيئة التطوير المتكاملة الخاصة بك.

في الأقسام التالية ستحصل على مثال كامل قابل للتنفيذ، شرح لكل سطر، ونصائح لتجنب المشكلات الشائعة مثل مشكلات الحجم وتوافق المستند. لا تحتاج إلى مراجع خارجية—فقط مكتبة Aspose.Words for Java.

## ما ستتعلمه

* كيفية تهيئة `Document` و `DocumentBuilder`.
* كيفية إدراج **group shape** ووضع مستطيل داخله.
* كيفية **تحديد حجم الشكل** باستخدام `setWidth` و `setHeight`.
* كيفية **حفظ مستند Word** بصيغة `.docx`.
* معالجة الحالات الطرفية لأحجام الصفحات المختلفة وإعدادات DPI.

### المتطلبات المسبقة

* Java 17 أو أحدث (الكود يُترجم أيضًا مع Java 8).
* Aspose.Words for Java 23.10 أو أحدث – يمكنك الحصول عليها من Maven Central.
* فهم أساسي لبنية Java ومفاهيم البرمجة الكائنية.

> **نصيحة احترافية:** إذا كنت تخطط لإضافة المزيد من الأشكال لاحقًا (مثل الدوائر أو مربعات النص)، احتفظ بها داخل نفس `GroupShape`. هذا يجعل تحريك أو تدوير أو تنسيق المجموعة بأكملها أسهل بكثير.

## الخطوة 1: تهيئة المستند والباني

الخطوة الأولى هي إنشاء ملف Word فارغ و`DocumentBuilder` يتيح لك كتابة المحتوى.  

```java
import com.aspose.words.*;

public class RectangleShapeDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document
        Document document = new Document();

        // Initialise a DocumentBuilder for the document
        DocumentBuilder builder = new DocumentBuilder(document);
```

*لماذا هذا مهم:* `Document` يمثل الملف بالكامل، بينما `DocumentBuilder` يوفر طرقًا عالية المستوى لإدراج النصوص والجداول و**الأشكال**. بدون الباني سيتعين عليك التعامل مع العقد منخفضة المستوى يدويًا.

## الخطوة 2: إدراج group shape لاحتواء أشكال متعددة

`**group shape**` يعمل كحاوية؛ يمكنك إضافة عدة أشكال ومعاملتها ككائن واحد لاحقًا (مثلًا، التحريك أو التدوير معًا).

```java
        // Step 2: Insert a group shape into the document
        GroupShape groupShape = builder.insertGroupShape();
```

*لماذا تستخدم group shape؟* إذا قررت لاحقًا إضافة أسهم أو دوائر أو تسميات حول المستطيل، فإن المجموعة تحافظ على كل شيء محاذيًا. كما أنها تبسط سير عمل **إضافة أشكال إلى Word** لأنك تحتاج إلى استدعاء واحد فقط لـ `appendChild` لكل شكل جديد.

## الخطوة 3: إنشاء شكل المستطيل

الآن نقوم بإنشاء المستطيل الفعلي الذي سيعيش داخل المجموعة. يحتاج مُنشئ `Shape` إلى الـ `Document` المالِك ونوع الشكل الذي تريده.

```java
        // Step 3: Create a rectangle shape that will live inside the group
        Shape rectangle = new Shape(document, ShapeType.RECTANGLE);
```

*لماذا مستطيل؟* `ShapeType.RECTANGLE` هو الأكثر شيوعًا لتسليط الضوء على الأقسام، إنشاء نُسخ احتياطية، أو رسم نماذج واجهة مستخدم بسيطة مباشرة داخل Word.

## الخطوة 4: تحديد حجم المستطيل

تحديد الأبعاد هو المكان الذي يصبح فيه **تحديد أبعاد الشكل** مهمًا. يمكنك استخدام أي وحدة قياس يدعمها Aspose.Words؛ الافتراضية هي النقاط (1 pt = 1/72 inch).

```java
        // Step 4: Define the rectangle's size (width = 100 pt, height = 50 pt)
        rectangle.setWidth(100);
        rectangle.setHeight(50);
```

> **ملاحظة:** إذا كنت تفضل المليمترات، استدعِ `rectangle.setWidth(ConversionUtil.inchesToPoints(1.39));` حيث `1.39 in ≈ 35 mm`. هذا يوضح مرونة **تحديد حجم الشكل**.

## الخطوة 5: إضافة المستطيل إلى group shape

إضافة المستطيل إلى المجموعة التي تم إنشاؤها مسبقًا يجعلها تظهر في المستند.

```java
        // Step 5: Add the rectangle to the group shape
        groupShape.appendChild(rectangle);
```

في هذه المرحلة يكون المستطيل موضعه في الزاوية العليا اليسرى للمجموعة. يمكنك تحريكه لاحقًا باستخدام `rectangle.setLeft(...)` و `rectangle.setTop(...)` إذا كنت تحتاج إلى وضعية دقيقة.

## الخطوة 6: (اختياري) حفظ المستند لرؤية النتيجة

أخيرًا، اكتب المستند إلى القرص. هذه هي خطوة **حفظ مستند Word** التي تنتج ملف `.docx` يمكنك فتحه في Microsoft Word أو LibreOffice أو Google Docs.

```java
        // Step 6: Save the document (optional but recommended for verification)
        document.save("output/RectangleShapeDemo.docx");
    }
}
```

تشغيل البرنامج ينشئ `RectangleShapeDemo.docx` يحتوي على مستطيل واحد داخل group shape. فتح الملف يظهر مستطيل أبيض بسيط—بالضبط بالحجم الذي حددته.

### النتيجة المتوقعة

* ملف Word باسم `RectangleShapeDemo.docx`.
* داخل الفقرة الأولى، group shape يحتوي على مستطيل بحجم 100 pt × 50 pt.
* لم يتم إضافة أي نص، لذا يظهر المستطيل على صفحة فارغة.

## الاختلافات الشائعة والحالات الطرفية

| الحالة | كيفية تعديل الكود |
|-----------|-----------------------|
| **حجم صفحة مختلف** (مثل A4) | استدعِ `document.getFirstSection().getPageSetup().setPaperSize(PaperSize.A4);` قبل إدراج الشكل. |
| **DPI أعلى للطباعة** | اضرب العرض/الارتفاع في عامل DPI المطلوب، مثال `rectangle.setWidth(200 * 2);` للحصول على دقة مزدوجة. |
| **إضافة تسمية نصية داخل المستطيل** | أنشئ `Shape` من النوع `TEXT_BOX`، عيّن `setWidth`/`setHeight` لتطابق المستطيل، ثم أضفه إلى نفس `GroupShape`. |
| **تدوير المستطيل** | استخدم `rectangle.setRotationAngle(45);` لتدوير 45 درجة باتجاه عقارب الساعة. |
| **الحفظ كملف PDF بدلاً من DOCX** | استبدل `document.save("output.docx");` بـ `document.save("output.pdf");` – نفس الـ API يعمل مع PDF، مع الحفاظ على المستطيل. |

## نصائح احترافية لتنفيذ قوي

1. **إعادة استخدام الباني** – بعد إدراج group shape، يمكنك الاستمرار في إضافة فقرات أو جداول دون إنشاء مثيل باني جديد.
2. **تحرير الموارد** – رغم أن جامع القمامة في Java يتعامل مع معظم الكائنات، فإن استدعاء `document.close();` صراحةً (إذا كنت تستخدم تدفقات) يمنع تسرب مقبض الملف.
3. **التحقق من الأبعاد** – قبل استدعاء `setWidth`/`setHeight`، تأكد من أن القيم موجبة؛ القيم السالبة تُطلق `IllegalArgumentException`.
4. **توافق الإصدارات** – يعمل الكود مع Aspose.Words 23.x وما بعده. قد تتطلب الإصدارات السابقة `Shape.setSize(width, height)` بدلاً من المحددات المنفصلة.

## مثال كامل قابل للتنفيذ

```java
import com.aspose.words.*;

public class RectangleShapeDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document
        Document document = new Document();

        // Initialise a DocumentBuilder for the document
        DocumentBuilder builder = new DocumentBuilder(document);

        // Step 2: Insert a group shape into the document
        GroupShape groupShape = builder.insertGroupShape();

        // Step 3: Create a rectangle shape that will live inside the group
        Shape rectangle = new Shape(document, ShapeType.RECTANGLE);

        // Step 4: Define the rectangle's size (width = 100 pt, height = 50 pt)
        rectangle.setWidth(100);
        rectangle.setHeight(50);

        // Optional: set a light gray fill to make it visible in Word
        rectangle.getFillColor() .setRGB(200, 200, 200);

        // Step 5: Add the rectangle to the group shape
        groupShape.appendChild(rectangle);

        // Step 6: Save the document (you can also save as PDF)
        document.save("output/RectangleShapeDemo.docx");
    }
}
```

> **التحقق من النتيجة:** افتح `output/RectangleShapeDemo.docx` في Microsoft Word. يجب أن ترى مستطيلًا بالحجم المحدد في أعلى الصفحة الأولى. إذا ظهر المستطيل صغيرًا جدًا، عدل القيم الممررة إلى `setWidth` و `setHeight`.

## الخلاصة

أنت الآن تعرف كيفية **إنشاء شكل مستطيل** في ملف Word باستخدام Java، وكيفية **إضافة أشكال إلى Word** عبر `GroupShape`، وكيفية **تحديد أبعاد الشكل** و**تحديد حجم الشكل**، وأخيرًا كيفية **حفظ مستند Word** للتوزيع لاحقًا. النمط نفسه يعمل مع أنواع أخرى من الأشكال، مما يتيح لك بناء مخططات معقدة برمجيًا.

### ما التالي؟

* استكشف **إضافة أشكال إلى Word** عن طريق إدراج دوائر أو أسهم أو مربعات نص.
* اجمع عدة أشكال في `GroupShape` واحد وطبق التحولات (تدوير، انعكاس).
* أنشئ تقارير تُدمج فيها المخططات كأشكال، ثم **احفظ مستند Word** كملف PDF للمشاركة.

لا تتردد في تجربة الأبعاد والألوان والمواضع لتناسب سيناريوك الخاص. برمجة سعيدة!

## ما الذي يجب أن تتعلمه بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات الموضحة في هذا الدليل. كل مصدر يتضمن أمثلة شفرة كاملة تعمل مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف أساليب تنفيذ بديلة في مشاريعك.

- [إنشاء مستند Word Java – إضافة شكل مستطيل مع تأثير الظل](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [إنشاء شكل مستطيل في مستند Word Java – دليل خطوة بخطوة كامل](/words/english/java/images-shapes/create-rectangle-shape-in-java-word-document-full-step-by-st/)
- [إنشاء مستند Word Java – إخفاء الشكل وتعيين لون التعبئة](/words/english/java/images-shapes/create-word-document-java-hide-shape-and-set-fill-color/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}