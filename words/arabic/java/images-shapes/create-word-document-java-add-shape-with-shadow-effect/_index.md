---
category: general
date: 2026-06-30
description: إنشاء مثال جافا لمستند وورد يوضح كيفية إضافة شكل إلى مستند وورد، وتعيين
  لون تعبئة الشكل، وتطبيق تأثير الظل على الشكل في بضع أسطر فقط.
draft: false
keywords:
- create word document java
- how to add shadow to shape
- add shape to word document
- set shape fill color
- apply shadow effect shape
language: ar
og_description: إنشاء برنامج تعليمي بلغة جافا لإنشاء مستند وورد يوضح كيفية إضافة شكل
  إلى مستند وورد، وتعيين لون تعبئة الشكل، وتطبيق تأثير الظل على الشكل.
og_title: إنشاء مستند Word باستخدام Java – إضافة شكل مع تأثير الظل
schemas:
- author: Aspose
  dateModified: '2026-06-30'
  description: Create word document java example that shows how to add shape to word
    document, set shape fill color, and apply shadow effect shape in just a few lines.
  headline: Create Word Document Java – Add Shape with Shadow Effect
  type: TechArticle
- description: Create word document java example that shows how to add shape to word
    document, set shape fill color, and apply shadow effect shape in just a few lines.
  name: Create Word Document Java – Add Shape with Shadow Effect
  steps:
  - name: Creates the shape object.
    text: Creates the shape object.
  - name: Positions it at the current cursor location (top‑left of the page by default).
    text: Positions it at the current cursor location (top‑left of the page by default).
  - name: Adds it to the document’s internal node collection.
    text: Adds it to the document’s internal node collection.
  type: HowTo
tags:
- Java
- Aspose.Words
- Word Automation
- Shapes
title: إنشاء مستند Word باستخدام Java – إضافة شكل مع تأثير الظل
url: /ar/java/images-shapes/create-word-document-java-add-shape-with-shadow-effect/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# إنشاء مستند Word باستخدام Java – إضافة شكل مع تأثير الظل

هل احتجت يومًا إلى **إنشاء مستند Word باستخدام Java** يُرسم مستطيلًا ويضيف له ظلًا خفيفًا؟ لست وحدك. سواءً كنت تُولّد تقارير، فواتير، أو منشورًا بسيطًا، فإن القدرة على **إضافة شكل إلى مستند Word** برمجيًا توفر ساعات من التعديل اليدوي.  

في هذا الدليل سنستعرض مثالًا كاملًا جاهزًا للتنفيذ لا يقتصر فقط على إنشاء ملف Word جديد، بل أيضًا **تعيين لون تعبئة الشكل**، **كيفية إضافة ظل إلى الشكل**، وأخيرًا **تطبيق تأثير الظل على الشكل** باستخدام Aspose.Words for Java. لا إطالة—فقط الخطوات الدقيقة التي يمكنك نسخها ولصقها في بيئة التطوير الخاصة بك.

> **نصيحة احترافية:** إذا كنت جديدًا على Aspose.Words، تأكد من وجود أحدث ملف JAR في مسار الفئات (classpath). الـ API الذي نستخدمه يعمل مع الإصدار 23.10 وما بعده.

## ما ستقوم بإنشائه

بنهاية هذا البرنامج التعليمي ستحصل على ملف `.docx` يحتوي على:

* مستند Word فارغ تم إنشاؤه من الصفر.
* مستطيل أصفر (150 × 80 نقطة) مُدرج في الصفحة الأولى.
* ظل رمادي ناعم مُزاح بضع نقاط، يمنح الشكل مظهرًا مرتفعًا.
* كل ذلك تم تحقيقه باستخدام عدد قليل من عبارات Java.

بدون قوالب خارجية، بدون XML معقد—كود Java نقي يمكن لأي شخص تشغيله.

---

## إنشاء مستند Word باستخدام Java – إدراج شكل

أول شيء نحتاجه هو كائن `Document` جديد و`DocumentBuilder`. فكر في الـ builder كقلم يتيح لنا الرسم داخل المستند.

```java
import com.aspose.words.*;

public class ShadowEffectDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document and a builder to add content.
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);
```

*لماذا هذا مهم:* `Document` يمثل الملف بأكمله، بينما `DocumentBuilder` يوفّر لنا طرقًا مريحة مثل `insertShape`. بدون الـ builder سيتعين علينا التعامل مع العقد منخفضة المستوى مباشرةً—مما يتطلب جهدًا أكبر بكثير.

## إضافة شكل إلى مستند Word – إدراج المستطيل

الآن نضيف فعليًا **شكلًا إلى مستند Word**. في حالتنا هو مستطيل، لكن يمكنك اختيار أي `ShapeType` تدعمه Aspose (بيضاوي، سهم، إلخ).

```java
        // Step 2: Insert a rectangle shape of size 150x80 points.
        Shape rectangle = builder.insertShape(ShapeType.RECTANGLE, 150, 80);
```

هذا السطر الواحد يقوم بثلاثة أشياء:

1. ينشئ كائن الشكل.
2. يضعه في موقع المؤشر الحالي (أعلى‑يسار الصفحة افتراضيًا).
3. يضيفه إلى مجموعة العقد الداخلية للمستند.

إذا تساءلت يومًا *كيف تضيف ظلًا إلى الشكل* بعد ذلك، استمر في القراءة—فسنصل إلى ذلك في القسم التالي.

## تعيين لون تعبئة الشكل – تخصيص المظهر

المستطيل الأبيض البسيط ليس مثيرًا، لذا لن **نعيّن لون تعبئة الشكل** إلى لون ساطع. سنستخدم فئة `java.awt.Color` في Java، التي تقبلها Aspose مباشرة.

```java
        // Step 3: Set the shape's fill color to yellow.
        rectangle.setFillColor(java.awt.Color.YELLOW);
```

لا تتردد في استبدال `YELLOW` بـ `RED` أو `GREEN` أو أي قيمة RGB مخصصة (`new Color(123, 45, 67)`). لون التعبئة هو السطح الذي ستراه قبل أن يظهر الظل.

## كيفية إضافة ظل إلى الشكل – ضبط إعدادات الظل

هنا يحدث السحر. Aspose.Words يوفّر كائن `ShadowEffect` يتيح لنا تعديل مظهر الظل بدقة.

```java
        // Step 4: Configure a custom shadow effect for the shape.
        ShadowEffect shadow = rectangle.getShadowEffect();
        shadow.setColor(java.awt.Color.GRAY);      // Shadow color
        shadow.setBlurRadius(5.0);                 // Softness of the shadow
        shadow.setOffsetX(4.0);                    // Horizontal offset
        shadow.setOffsetY(4.0);                    // Vertical offset
        shadow.setTransparency(0.3);               // Shadow opacity (0 = opaque, 1 = fully transparent)
```

**لماذا كل خاصية مهمة:**

| الخاصية | ما تقوم به | القيم النموذجية |
|----------|--------------|----------------|
| `setColor` | تحدد درجة لون الظل. اللون الرمادي يناسب معظم الحالات، لكن يمكنك اختيار لون جريء مثل `Color.BLUE`. | أي `java.awt.Color` |
| `setBlurRadius` | يتحكم في مدى نعومة حواف الظل. القيم الأكبر تعطي مظهرًا أكثر انتشارًا. | 0 – 10 (float) |
| `setOffsetX` / `setOffsetY` | تحرك الظل يمينًا/يسارًا وفوقًا/تحتًا. القيم الموجبة تدفع الظل إلى الأسفل‑واليمين. | -10 – 10 |
| `setTransparency` | يحدد الشفافية؛ 0 يعني صلب، 1 يعني غير مرئي. | 0.0 – 1.0 |

إذا كنت تتساءل **كيف تضيف ظلًا إلى الشكل** دون إفساد التخطيط، المفتاح هو الحفاظ على القيم المتزاحة معتدلة. القيم الكبيرة قد تجعل الظل ينساب إلى الصفحة التالية.

## تطبيق تأثير الظل على الشكل – حفظ المستند

بعد تنسيق الشكل وضبط الظل، كل ما علينا هو حفظ الملف.

```java
        // Step 5: Save the document with the shaped shadow.
        document.save("YOUR_DIRECTORY/ShadowShape.docx");
    }
}
```

استبدل `YOUR_DIRECTORY` بمسار مطلق أو نسبي موجود على جهازك. بعد تشغيل البرنامج، افتح `ShadowShape.docx` في Microsoft Word أو LibreOffice—سترى مستطيلًا أصفرًا يطفو فوق الصفحة بفضل الظل الرمادي الذي أضفناه.

---

## التحقق من النتيجة – ما الذي يجب ملاحظته

عند فتح الملف المُولَّد:

* يجب أن يكون المستطيل مركزيًا حيث بدأ المؤشر (أعلى‑يسار الصفحة افتراضيًا).
* لونه أصفر ساطع.
* ظل رمادي ناعم يُبعد 4 نقطة إلى اليمين والأسفل، مع شفافية تقريبية 30 ٪.

إذا كان الظل شديدًا جدًا، قلل قيمة `BlurRadius` أو زد قيمة `Transparency`. إذا لم يظهر الشكل، تحقق من استدعاء `setFillColor`—ربما اللون المختار يندمج مع خلفية الصفحة.

---

## المشكلات الشائعة وحالات الحافة

| المشكلة | السبب | الحل |
|-------|-------|-----|
| **اختفاء الظل** | تم ضبط `Transparency` إلى `1.0` (شفافية كاملة). | استخدم قيمة أقل، مثل `0.3`. |
| **عدم ظهور الشكل** | لون التعبئة يطابق خلفية الصفحة (غالبًا أبيض). | اختر لونًا متباينًا باستخدام `setFillColor`. |
| **قص الظل عند حافة الصفحة** | الإزاحات تدفع الظل خارج منطقة الطباعة. | قلل `OffsetX`/`OffsetY` أو وسّع هوامش الصفحة عبر `PageSetup`. |
| **خطأ تجميع: لا يمكن العثور على الرمز ShadowEffect** | استخدام نسخة أقدم من Aspose.Words لا تدعم الظل. | حدّث إلى Aspose.Words 23.10+ (الـ API أضيف `ShadowEffect` في 22.12). |

---

## الخطوات التالية – ما بعد الأساسيات

الآن بعد أن عرفت كيف **تنشئ مستند Word باستخدام Java**، **تضيف شكلًا إلى مستند Word**، **تعيّن لون تعبئة الشكل**، **تضيف ظلًا إلى الشكل**، وت **طبق تأثير الظل على الشكل**، قد تتساءل ماذا يمكنك أن تفعل بعد ذلك. إليك بعض الأفكار:

* **ألوان ديناميكية** – استخرج قيم RGB من قاعدة بيانات لتلوين الأشكال حسب الحالة.
* **ظلال متعددة** – استنسخ الشكل وأضف إعدادات `ShadowEffect` مختلفة لكل نسخة.
* **نص داخل الأشكال** – استخدم `Shape.getTextFrame()` لإدراج تسمية أو توضيح.
* **تصدير إلى PDF** – استدعِ `document.save("output.pdf", SaveFormat.PDF)` للحصول على نسخة جاهزة للطباعة بنفس الجودة البصرية.

كل هذه الأفكار تبني على النمط الأساسي الذي عرضناه: إنشاء مستند، إدراج شكل، تنسيقه، ثم حفظه.

---

## مثال كامل جاهز للتنفيذ (انسخه‑ألصقه)

```java
import com.aspose.words.*;
import java.awt.Color;

public class ShadowEffectDemo {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Create a new blank document and a builder.
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // 2️⃣ Insert a rectangle shape (150 × 80 pts).
        Shape rectangle = builder.insertShape(ShapeType.RECTANGLE, 150, 80);

        // 3️⃣ Set the shape's fill color to yellow.
        rectangle.setFillColor(Color.YELLOW);

        // 4️⃣ Configure the shadow effect.
        ShadowEffect shadow = rectangle.getShadowEffect();
        shadow.setColor(Color.GRAY);        // Shadow color
        shadow.setBlurRadius(5.0);          // Softness
        shadow.setOffsetX(4.0);             // Horizontal offset
        shadow.setOffsetY(4.0);             // Vertical offset
        shadow.setTransparency(0.3);        // 30 % transparent

        // 5️⃣ Save the document.
        document.save("ShadowShape.docx");
    }
}
```

تشغيل الفئة ينتج ملف `ShadowShape.docx` في دليل العمل الحالي. افتحه، وسترى النتيجة الدقيقة التي تم وصفها سابقًا.

---

## الخلاصة

لقد أظهرنا لك كيفية **إنشاء مستند Word باستخدام Java** من الصفر، **إضافة شكل إلى مستند Word**، **تعيين لون تعبئة الشكل**، **كيفية إضافة ظل إلى الشكل**، وأخيرًا **تطبيق تأثير الظل على الشكل**—كل ذلك عبر مثال كود مختصر وسهل الفهم.  

النهج بسيط عن قصد حتى يمكنك تعديله لسيناريوهات أكثر تعقيدًا—سواءً كنت تحتاج إلى أشكال متعددة، ألوان مختلفة، أو ظلال بأسلوب أكثر ديناميكية. تذكّر مراقبة توافق نسخة الـ API، ولا تتردد في تعديل معلمات الظل لتتناسب مع لغة التصميم الخاصة بك.

هل جربت تعديلًا مختلفًا؟ ربما وضعت صورة خلف المستطيل أو أضفت جدولًا داخل الشكل. اترك تعليقًا أدناه؛ أحب أن أسمع كيف يطوّر المطورون هذه الأمثلة. برمجة سعيدة


## ماذا يجب أن تتعلم بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات التي تم توضيحها في هذا الدليل. كل مورد يتضمن أمثلة كود كاملة مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف أساليب تنفيذ بديلة في مشاريعك.

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [How to Create PDF Documents with Aspose.Words for Java | Document Processing API](/words/english/java/)
- [Aspose.Words Java: Comprehensive Guide to Word Document Processing](/words/english/java/document-operations/aspose-words-java-master-word-processing/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}