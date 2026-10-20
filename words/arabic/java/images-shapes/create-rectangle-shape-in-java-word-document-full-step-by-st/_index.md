---
category: general
date: 2026-05-26
description: إنشاء شكل مستطيل في مستند Word باستخدام Java وتطبيق تأثير الظل. تعلم
  كيفية إضافة ظل للشكل، ضبط مسافة الظل، وحفظ الملف.
draft: false
keywords:
- create rectangle shape
- apply shadow effect
- create word document java
- add shape shadow
- set shadow distance
language: ar
og_description: إنشاء شكل مستطيل في مستند Word باستخدام Java، تطبيق تأثير الظل، إضافة
  ظل للشكل، وتعيين مسافة الظل باستخدام Aspose.Words.
og_title: إنشاء شكل مستطيل في مستند Word باستخدام Java – دليل كامل
schemas:
- author: Aspose
  dateModified: '2026-05-26'
  description: Create rectangle shape in a Java Word document and apply shadow effect.
    Learn how to add shape shadow, set shadow distance, and save the file.
  headline: Create Rectangle Shape in Java Word Document – Full Step‑by‑Step Guide
  type: TechArticle
- description: Create rectangle shape in a Java Word document and apply shadow effect.
    Learn how to add shape shadow, set shadow distance, and save the file.
  name: Create Rectangle Shape in Java Word Document – Full Step‑by‑Step Guide
  steps:
  - name: “Can I use a different shape?”
    text: Absolutely. Replace `ShapeType.RECTANGLE` with `ShapeType.OVAL`, `ShapeType.LINE`,
      or any other supported enum. The rest of the shadow code stays the same.
  - name: “What if I need multiple shadows?”
    text: Aspose.Words only supports a single shadow per shape. To simulate multiple
      shadows, duplicate the shape, offset each copy, and adjust the transparency.
  - name: “Is the shadow visible in LibreOffice?”
    text: Yes—Aspose.Words writes standard OOXML, which LibreOffice interprets correctly.
      The shadow may look slightly different due to rendering engines, but the effect
      persists.
  - name: “How do I change the shadow color to match my brand?”
    text: Just swap `java.awt.Color.GRAY` with any `java.awt.Color` you prefer, such
      as `new java.awt.Color(0, 120, 215)` for a corporate blue.
  type: HowTo
tags:
- Java
- Aspose.Words
- Word Automation
title: إنشاء شكل مستطيل في مستند Word باستخدام Java – دليل كامل خطوة بخطوة
url: /ar/java/images-shapes/create-rectangle-shape-in-java-word-document-full-step-by-st/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# إنشاء شكل مستطيل في مستند Word باستخدام Java – دليل خطوة‑بخطوة كامل

هل احتجت يوماً إلى **create rectangle shape** في مستند Word باستخدام Java لكن لم تكن متأكدًا من أين تبدأ؟ لست وحدك—العديد من المطورين يواجهون هذه المشكلة عند توليد التقارير أو الفواتير برمجيًا. في هذا الدرس سنستعرض بالضبط كيفية **create rectangle shape**، إضافة ظل مصقول، وضبط مسافة الظل بدقة لتظهر النتيجة بشكل احترافي.

سنستخدم Aspose.Words for Java، مكتبة قوية تتيح لك تعديل ملفات Word دون الحاجة إلى تثبيت Microsoft Office. بنهاية هذا الدليل ستكون قادرًا على إنشاء مشاريع **create word document java** التي **add shape shadow**، **apply shadow effect**، و**set shadow distance** ببضع أسطر من الشيفرة فقط.

---

## ما ستبنيه

- ملف `.docx` جديد يحتوي على مستطيل سينا.
- ظل إسقاط واقعي مُطمس، مائل، وشفاف جزئيًا.
- تحكم كامل في مسافة الظل عن الشكل.
- فئة Java جاهزة للتنفيذ يمكنك وضعها في أي مشروع Maven أو Gradle.

بدون أدوات خارجية، بدون خطوات يدوية في الواجهة—فقط شيفرة صافية.

---

## المتطلبات المسبقة

- Java 8 أو أحدث (الشيفرة تعمل على Java 11، Java 17، إلخ).
- مكتبة Aspose.Words for Java (متوفرة عبر Maven Central).
- بيئة تطوير أو محرر نصوص تفضله (IntelliJ IDEA، Eclipse، VS Code…).
- إلمام أساسي بصياغة Java.

إذا لم تضف اعتماد Maven من قبل، إليك المقتطف السريع:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.10</version> <!-- Use the latest stable version -->
</dependency>
```

الآن، لنبدأ.

---

## الخطوة 1: إنشاء شكل مستطيل في مستند Word

أول شيء نحتاجه هو مستند فارغ و`DocumentBuilder`. فكر في الـ builder كقلم يكتب داخل المستند. بمجرد حصولنا عليه، يمكننا **create rectangle shape** باستدعاء طريقة واحدة.

```java
import com.aspose.words.*;

public class ShadowEffectDemo {
    public static void main(String[] args) throws Exception {
        // Initialize a new empty document.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a rectangle shape of 150x80 points.
        Shape rectangleShape = builder.insertShape(ShapeType.RECTANGLE, 150, 80);
        // Make the shape visible by filling it with cyan.
        rectangleShape.setFillColor(java.awt.Color.CYAN);
```

> **لماذا هذا مهم:** طريقة `insertShape` لا تُنشئ الشكل الهندسي فقط بل تضيفه أيضًا إلى مجموعة الأشكال الداخلية للمستند، بحيث يمكنك البدء فورًا في تنسيقه.

---

## الخطوة 2: تطبيق تأثير الظل على الشكل

الآن بعد أن أصبح المستطيل موجودًا على الصفحة، سنقوم **apply shadow effect**. الظلال تُضيف عمقًا، تجعل الشكل يبدو كأنه مرتفع عن الصفحة—تحسين بسيط في واجهة المستخدم يمكن أن يعزز قابلية القراءة في التقارير.

```java
        // Retrieve the shadow format object.
        ShadowFormat shadowFormat = rectangleShape.getShadowFormat();

        // Enable the shadow and configure its appearance.
        shadowFormat.setVisible(true);          // Turn the shadow on.
        shadowFormat.setBlur(5.0);              // Soft blur radius.
        shadowFormat.setAngle(45.0);            // Direction of the shadow.
        shadowFormat.setColor(java.awt.Color.GRAY); // Shadow color.
        shadowFormat.setTransparency(0.3);     // 30% transparent.
```

> **نصيحة احترافية:** قيمة التمويه `5.0` تبدو طبيعية لمعظم المستندات المعروضة على الشاشات. إذا كنت تطبع، قد ترغب في قيمة أقل قليلًا لتجنب مظهر ضبابي.

---

## الخطوة 3: ضبط مسافة الظل – تحسين الموضع

الظلال ليست مجرد تمويه؛ فهي تحتاج أيضًا إلى الإزاحة الصحيحة. هنا نستخدم **set shadow distance**. مسافة `7.0` نقطة تُنشئ إزاحة معتدلة تُلاحظ ولكنها ليست مفرطة.

```java
        // Define how far the shadow sits from the shape.
        shadowFormat.setDistance(7.0); // Distance in points.
```

> **ماذا لو احتجت إزاحة أكبر؟** زد القيمة؛ قللها للحصول على مظهر أكثر إحكامًا. تذكر أن المسافة تعمل مع الزاوية لتحديد موضع الظل بدقة.

---

## الخطوة 4: حفظ المستند – تثبيت عملك

أخيرًا، نكتب المستند إلى القرص. غيّر المسار إلى المكان الذي تريد حفظ الملف فيه.

```java
        // Save the document with the rectangle and its shadow.
        doc.save("YOUR_DIRECTORY/shadow.docx");
    }
}
```

تشغيل الفئة يُنشئ ملف `shadow.docx`، وعند فتحه في Microsoft Word أو LibreOffice، سيظهر مستطيل سينا مع ظل رمادي ناعم مائل بزاوية 45° وإزاحة 7 نقاط.

---

## مثال كامل يعمل

فيما يلي الشيفرة الكاملة جاهزة للنسخ واللصق. تشمل جميع الاستيرادات، التعليقات، واستدعاء `save` النهائي.

```java
import com.aspose.words.*;

public class ShadowEffectDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document and a DocumentBuilder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Insert a rectangle shape of the desired size.
        Shape rectangleShape = builder.insertShape(ShapeType.RECTANGLE, 150, 80);
        // Step 3: Apply a fill color to make the shape visible.
        rectangleShape.setFillColor(java.awt.Color.CYAN);

        // Step 4: Configure the shape's shadow effect.
        ShadowFormat shadowFormat = rectangleShape.getShadowFormat();
        shadowFormat.setVisible(true);          // Enable the shadow.
        shadowFormat.setBlur(5.0);              // Set the blur radius.
        shadowFormat.setDistance(7.0);          // Define how far the shadow is from the shape.
        shadowFormat.setAngle(45.0);            // Set the direction of the shadow.
        shadowFormat.setColor(java.awt.Color.GRAY); // Choose the shadow color.
        shadowFormat.setTransparency(0.3);      // Make the shadow partially transparent.

        // Step 5: Save the document with the shaped shadow.
        doc.save("YOUR_DIRECTORY/shadow.docx");
    }
}
```

**الناتج المتوقع:** افتح `shadow.docx` → سترى مستطيلًا سيناًا مركزيًا في الصفحة الأولى، يُسقط ظلًا رماديًا خفيفًا مائلًا قليلًا إلى أسفل‑يمين. تمويه الظل وشفافيته يجعلان المظهر كإضاءة طبيعية.

---

## أسئلة شائعة وحالات خاصة

### “هل يمكنني استخدام شكل مختلف؟”

بالطبع. استبدل `ShapeType.RECTANGLE` بـ `ShapeType.OVAL` أو `ShapeType.LINE` أو أي تعداد مدعوم آخر. يبقى باقي شيفرة الظل كما هو.

### “ماذا لو احتجت ظلالًا متعددة؟”

Aspose.Words يدعم ظلًا واحدًا فقط لكل شكل. لمحاكاة ظلال متعددة، قم بنسخ الشكل، إزاحة كل نسخة، وضبط الشفافية.

### “هل الظل مرئي في LibreOffice؟”

نعم—Aspose.Words يكتب OOXML قياسيًا، والذي تفسره LibreOffice بشكل صحيح. قد يختلف مظهر الظل قليلًا بسبب محركات العرض، لكن التأثير يبقى موجودًا.

### “كيف أغيّر لون الظل ليتطابق مع علامتي التجارية؟”

ما عليك سوى استبدال `java.awt.Color.GRAY` بأي `java.awt.Color` تفضله، مثل `new java.awt.Color(0, 120, 215)` للون أزرق مؤسسي.

---

## توضيح بصري

![create rectangle shape in Java Word document](https://example.com/images/rectangle-shadow.png)

*نص بديل:* **create rectangle shape** توضيح يُظهر مستطيلًا سيناًا مع ظل رمادي إسقاطي في مستند Word.

---

## ملخص وخطوات مستقبلية

غطّينا كيفية **create rectangle shape**، **apply shadow effect**، **add shape shadow**، و**set shadow distance** باستخدام Aspose.Words for Java. الشيفرة مستقلة، تعمل على أي JDK حديث، وتنتج ملف `.docx` مصقول جاهز للتوزيع.

هل تريد التعمق أكثر؟ جرّب:

- إضافة نص داخل المستطيل باستخدام `builder.moveTo(rectangleShape.getAbsolutePosition())`.
- إنشاء جدول من الأشكال لبناء مخطط.
- تصدير المستند إلى PDF (`doc.save("output.pdf", SaveFormat.PDF);`).

كل هذه الخطوات تبني على الأساسيات التي استعرضناها للتو، لذا ستشعر بالراحة في توسيع المثال.

---

## الخاتمة

إتقان مهام **create word document java** مثل تشكيل الأشكال وتظليلها يمنحك ميزة كبيرة عند أتمتة التقارير، العقود، أو المواد التسويقية. النهج المعروض هنا نظيف، قابل للصيانة،—والأهم—سهل التعديل لأي نمط بصري تحتاجه.

جرّب الشيفرة، عدّل التمويه، الزاوية، والمسافة، وشاهد مستنداتك تتحول من عادية إلى مصقولة. إذا واجهت أي عائق، اترك تعليقًا أدناه؛ أنا سعيد بالمساعدة.

برمجة سعيدة!

## دروس ذات صلة

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [How to create form fields and add content using DocumentBuilder in Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Create PDF from Word with Barcode Generation – Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-barcode-generation/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}