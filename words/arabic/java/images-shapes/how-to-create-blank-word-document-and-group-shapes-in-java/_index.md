---
category: general
date: 2026-09-27
description: إنشاء مستند Word فارغ في Java وتجميع الأشكال باستخدام Aspose.Words. تعلم
  كيفية ضبط حجم الشكل، وضبط لون تعبئة الشكل، وإضافة عنصر فرعي إلى المجموعة.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- group shapes in word
- set shape size
- set shape fill color
- append child to group
language: ar
lastmod: 2026-09-27
og_description: إنشاء مستند Word فارغ في Java باستخدام Aspose.Words. يوضح هذا الدرس
  كيفية تجميع الأشكال في Word، وتحديد حجم الشكل، وتعيين لون تعبئة الشكل، وإضافة عنصر
  فرعي إلى المجموعة.
og_image_alt: Screenshot of a blank Word document with grouped shapes created using
  Java
og_title: إنشاء مستند Word فارغ وتجميع الأشكال في Java – دليل خطوة بخطوة
schemas:
- author: Aspose
  dateModified: '2026-09-27'
  description: Create a blank Word document in Java and group shapes using Aspose.Words.
    Learn to set shape size, set shape fill color, and append child to group.
  headline: How to create blank word document and group shapes in Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word automation
title: كيفية إنشاء مستند Word فارغ وتجمّع الأشكال في جافا
url: /ar/java/images-shapes/how-to-create-blank-word-document-and-group-shapes-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# كيفية إنشاء مستند Word فارغ وتجميع الأشكال في Java

إذا كنت بحاجة إلى **إنشاء مستند Word فارغ** برمجياً، يوضح لك هذا الدليل بالضبط كيفية القيام بذلك باستخدام Aspose.Words for Java. ستتعلم أيضًا **تجميع الأشكال في Word**، وتعيين حجم كل شكل، وتطبيق لون تعبئة، و**إلحاق عنصر فرعي بالمجموعة** بحيث تتصرف الكائنات كوحدة واحدة.

العمل مع ملفات Word من الكود يوفر عليك التنسيق اليدوي ويمكنك من إنشاء تقارير، عقود، أو كتيبات تسويقية تلقائيًا. بنهاية هذا الدرس ستحصل على برنامج Java قابل للتنفيذ ينتج ملف `.docx` يحتوي على مستطيل أزرق وصورة، كلاهما مجمّع معًا.

## المتطلبات المسبقة

قبل أن تبدأ، تأكد من وجود ما يلي:

- Java 17 (أو أي JDK حديث) مثبت.
- Maven أو Gradle لإدارة الاعتمادات.
- رخصة Aspose.Words for Java (التقييم المجاني يكفي للاختبار).
- ملف صورة تجريبي (مثال: `sample.jpg`) موجود في مجلد يمكنك الإشارة إليه من الكود.

> **نصيحة احترافية:** احفظ ملفات الصور في دليل `resources` وحمّلها باستخدام `ClassLoader.getResourceAsStream` لتجنب المسارات المطلقة الصريحة.

## الخطوة 1: إنشاء مستند Word فارغ وإضافة GroupShape

الخطوة الأولى هي إنشاء كائن `Document` جديد، والذي يمثل ملف Word فارغ، ثم إدراج `GroupShape`. ستعمل المجموعة كحاوية لأي أشكال تضيفها لاحقًا.

```java
import com.aspose.words.*;

public class GroupShapesDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document
        Document doc = new Document();                     // create blank word document
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a GroupShape that will act as a container for other shapes
        GroupShape group = builder.insertGroupShape();     // group shapes in word
```

*لماذا هذا مهم:* يسمح لك `GroupShape` بنقل، تدوير، أو تنسيق عدة أشكال معًا، وهو أمر أساسي لتصاميم معقدة مثل المخططات أو العلامات المائية.

## الخطوة 2: إدراج مستطيل و**تعيين حجم الشكل**

بعد ذلك، أنشئ مستطيلًا، حدد أبعاده، وأضفه إلى المجموعة. هذا يوضح عملية **تعيين حجم الشكل**.

```java
        // Step 2: Create a rectangle shape, configure its size, and add it to the group
        Shape rectangle = new Shape(doc, ShapeType.RECTANGLE);
        rectangle.setWidth(100.0);                         // set shape size – width 100 points
        rectangle.setHeight(50.0);                         // set shape size – height 50 points
        rectangle.setFillColor(java.awt.Color.BLUE);      // set shape fill color to blue
        group.appendChild(rectangle);                     // append child to group
```

*شرح:* تتحكم `setWidth` و `setHeight` في الحجم الدقيق للشكل بالنقاط (نقطة واحدة = 1/72 بوصة). عدّل هذه القيم لتناسب متطلبات تخطيطك.

## الخطوة 3: **تعيين لون تعبئة الشكل** للمستطيل

يتم تعيين خلفية المستطيل إلى اللون الأزرق باستخدام `setFillColor`. يمكنك استخدام أي ثابت من `java.awt.Color` أو إنشاء لون RGB مخصص.

```java
        // The fill color was already applied in the previous step.
        // If you need a different color later, just call setFillColor again:
        // rectangle.setFillColor(new java.awt.Color(255, 165, 0)); // orange
```

*لماذا هو مفيد:* تساعد ألوان التعبئة على تمييز الكائنات بصريًا، خاصةً عندما تقوم لاحقًا بتصدير المستند إلى PDF أو طباعته.

## الخطوة 4: إدراج صورة و**إلحاق عنصر فرعي بالمجموعة**

الآن أضف صورة إلى نفس `GroupShape`. تُدرج الصورة عبر `DocumentBuilder.insertImage`، ثم تُلحق بالمجموعة بحيث تتحرك مع المستطيل.

```java
        // Step 4: Insert an image and add it to the same group
        Shape picture = builder.insertImage("YOUR_DIRECTORY/sample.jpg");
        group.appendChild(picture);                       // append child to group
```

*حالة خاصة:* إذا كان مسار الصورة غير صحيح، ستطرح Aspose.Words استثناء `FileNotFoundException`. استخدم مسارًا نسبيًا أو حمّل الصورة من الموارد لتجنب هذه المشكلة.

## الخطوة 5: **حفظ المستند مع الأشكال المجمعة**

أخيرًا، اكتب المستند إلى القرص. سيحتوي الملف الناتج على المستطيل والصورة المجمعة معًا.

```java
        // Step 5: Save the document with the grouped shapes
        doc.save("YOUR_DIRECTORY/GroupShape.docx");       // creates the blank word document with grouped shapes
    }
}
```

### النتيجة المتوقعة

- يظهر ملف باسم `GroupShape.docx` في الدليل المحدد.
- عند فتح الملف في Microsoft Word، ستظهر صفحة فارغة تحتوي على مستطيل أزرق والصورة المختارة، كلاهما محددان ككائن واحد (يمكنك نقلهما أو تغيير حجمهما معًا).

![إنشاء مستند Word فارغ مع الأشكال المجمعة](/images/grouped-shapes.png "إنشاء مستند Word فارغ مع الأشكال المجمعة")

*توضح اللقطة أعلاه الأشكال المجمعة النهائية داخل مستند Word الذي تم إنشاؤه حديثًا.*

## الاختلافات الشائعة والنصائح الإضافية

| الحالة | كيفية التعامل معها |
|-----------|-----------------|
| **صور متعددة** | أدخل كل صورة باستخدام `builder.insertImage` واستدعِ `group.appendChild(picture)` لكل واحدة. |
| **أنواع أشكال مختلفة** | استخدم `ShapeType.OVAL`، `ShapeType.LINE`، إلخ، عند إنشاء كائن `Shape`. |
| **تغيير موضع المجموعة** | بعد إضافة جميع العناصر الفرعية، اضبط `group.setLeft(x)` و `group.setTop(y)` لتحريك المجموعة بأكملها. |
| **تصدير إلى PDF** | استدعِ `doc.save("output.pdf")` بعد التجميع؛ سيحافظ ملف PDF على التجميع. |
| **تطبيق الرخصة** | إذا شغلت النسخة التجريبية، سيظهر علامة مائية. قم بتثبيت رخصة صالحة لإزالتها. |

## الخلاصة

أنت الآن تعرف كيف **تنشئ مستند Word فارغ**، وتدرج **GroupShape**، و**تحدد حجم الشكل**، و**تحدد لون تعبئة الشكل**، و**تلحق عنصرًا فرعيًا بالمجموعة** باستخدام Aspose.Words for Java. يتيح لك هذا النمط بناء تخطيطات برمجية معقدة يمكن تعديلها لاحقًا في Word أو تصديرها إلى صيغ أخرى.

بعد ذلك، استكشف كيفية **تجميع الأشكال في Word** مع صناديق النص، وإضافة روابط تشعبية إلى الأشكال، أو أتمتة إنشاء تقارير متعددة الصفحات. المبادئ نفسها تنطبق—فقط أنشئ أشكالًا إضافية، واضبط خصائصها، وألحقها بنفس المجموعة.

برمجة سعيدة!

## ما الذي ينبغي أن تتعلمه بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات التي تم توضيحها في هذا الدليل. كل مصدر يتضمن أمثلة شفرة كاملة مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف أساليب تنفيذ بديلة في مشاريعك الخاصة.

- [إنشاء شكل مستطيل في Word باستخدام Java – دليل كامل](/words/english/java/images-shapes/create-rectangle-shape-in-word-with-java-full-guide/)
- [إنشاء مستند Word Java – إضافة شكل مستطيل مع تأثير الظل](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [إنشاء شكل مجموعة في مستند Word باستخدام Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}