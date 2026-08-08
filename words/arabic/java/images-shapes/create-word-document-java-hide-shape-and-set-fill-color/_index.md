---
category: general
date: 2026-08-07
description: 'إنشاء مستند Word باستخدام Java و Aspose.Words: إدراج إهليلج، تعيين لون
  تعبئة الشكل، وإخفاء الشكل في Word باستخدام مثال مختصر.'
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document java
- how to hide shape
- how to insert shape
- hide shape in word
- set shape fill color
language: ar
lastmod: 2026-08-07
og_description: إنشاء مستند Word باستخدام Java و Aspose.Words. تعلم كيفية إدراج شكل،
  تعيين لون تعبئته، وإخفاء الشكل في Word—كل ذلك في مثال واحد قابل للتنفيذ.
og_image_alt: Screenshot showing a hidden ellipse shape in a Word document created
  with Java
og_title: إنشاء مستند Word باستخدام Java – إخفاء الشكل وتعيين لون التعبئة
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: 'Create word document java with Aspose.Words: insert an ellipse, set
    shape fill color, and hide shape in Word using a concise example.'
  headline: Create word document java – hide shape and set fill color
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word automation
- Shape handling
title: إنشاء مستند Word باستخدام Java – إخفاء الشكل وتعيين لون التعبئة
url: /ar/java/images-shapes/create-word-document-java-hide-shape-and-set-fill-color/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# إنشاء مستند Word باستخدام Java – إخفاء الشكل وتعيين لون التعبئة

إذا كنت بحاجة إلى **إنشاء مستند Word باستخدام Java** مع معالجة الأشكال برمجياً، فإن هذا الدليل يوضح لك الطريقة. ستتعلم كيفية إدراج شكل، تعيين لون تعبئته، وإخفاء الشكل في Word باستخدام Aspose.Words for Java.

يغطي الدليل كل خطوة بدءاً من تهيئة كائن `Document` وحتى التحقق من أن الشكل غير مرئي عند فتح الملف. لا تحتاج إلى موارد خارجية بخلاف مكتبة Aspose.Words، ويتم توفير الشيفرة المصدرية الكاملة لتتمكن من تشغيلها فوراً.

**المتطلبات المسبقة**

- Java 8 أو أحدث
- Maven أو Gradle لإدارة التبعيات (أو ملف JAR الخاص بـ Aspose.Words على مسار الـ classpath)
- إلمام أساسي بصياغة Java
- بيئة تطوير متكاملة (IDE) أو محرر نصوص لتطوير Java

يوضح الدليل أيضاً **كيفية إخفاء الشكل** في ملف Word، **كيفية إدراج الشكل** بأبعاد دقيقة، و**تعيين لون تعبئة الشكل** للتنسيق البصري.

---

![إنشاء مستند Word باستخدام Java – معاينة الشكل المخفي](image-placeholder.png){.align-center width=600 alt="إنشاء مستند Word باستخدام Java – معاينة الشكل المخفي"}

## إنشاء مستند Word باستخدام Java – تهيئة المستند والباني

الخطوة الأولى هي إنشاء مستند Word فارغ و`DocumentBuilder` يتيح لك إضافة المحتوى. تهيئة هذه الكائنات تخصّص البُنى الداخلية التي تحتاجها Aspose.Words لتتبع الصفحات والفقرات والأشكال.

```java
import com.aspose.words.*;

public class ShapeVisibilityDemo {
    public static void main(String[] args) throws Exception {
        // Create an empty document
        Document doc = new Document();

        // DocumentBuilder provides methods to insert elements
        DocumentBuilder builder = new DocumentBuilder(doc);
```

*لماذا هذا مهم:* بدون `DocumentBuilder` لا يمكنك إدراج أشكال أو نصوص أو كائنات أخرى. يعمل الباني على نسخة الـ `Document` الموجودة في الذاكرة، مما يضمن أن جميع التغييرات تُلتقط قبل الحفظ.

## كيفية إدراج شكل باستخدام Aspose.Words

تدعم Aspose.Words العديد من الأشكال الهندسية. هنا نقوم بإدراج إهليلج بعرض 150 pt وارتفاع 100 pt. تُعيد الدالة `insertShape` كائن `Shape` يمكنك تعديل خصائصه لاحقاً.

```java
        // Insert an ellipse shape (width: 150pt, height: 100pt)
        Shape ellipse = builder.insertShape(ShapeType.ELLIPSE, 150, 100);
```

*لماذا هذا مهم:* استخدام `insertShape` يضمن أن الشكل مُثبت بشكل صحيح داخل تدفق المستند. يتيح لك الـ `Shape` المسترجع تعديل خصائص مثل لون التعبئة، نمط الخط، والرؤية.

## تعيين لون تعبئة الشكل في Word

الشكل بدون تعبئة يبدو شفافاً. تعيين لون تعبئة يجعل الشكل بارزاً عندما يكون مرئياً. يستخدم المثال `java.awt.Color.GREEN` لتوضيح **تعيين لون تعبئة الشكل**.

```java
        // Apply a green fill to the ellipse
        ellipse.setFillColor(java.awt.Color.GREEN);
```

*لماذا هذا مهم:* يتم تخزين لون التعبئة في تعريف XML الخاص بالشكل. تغييره أثناء التشغيل يتيح لك إنشاء مستندات بألوان مخصصة للعلامة التجارية أو لتسليط الضوء على مناطق مهمة.

## كيفية إخفاء الشكل في Word

أحياناً تحتاج إلى شكل يساهم في التخطيط أو يعمل كعنصر نائب لكنه لا يجب أن يظهر للمستخدم النهائي. تستدعي الدالة `setHidden(true)` لتطبيق **كيفية إخفاء الشكل** وتلبي متطلبات **إخفاء الشكل في Word**.

```java
        // Hide the shape so it will not be visible when the document is opened
        ellipse.setHidden(true);
```

*لماذا هذا مهم:* الأشكال المخفية لا تزال جزءاً من نموذج كائنات المستند، ما يعني أنه يمكن الإشارة إليها لاحقاً (مثلاً للعلامات المرجعية أو المعالجة البرمجية) دون إرباك التخطيط البصري.

## حفظ المستند والتحقق من النتائج

بعد ضبط الشكل، احفظ الملف على القرص. يمكن فتح ملف `.docx` المحفوظ في Microsoft Word؛ سيكون الإهليلج غير مرئي، لكن وجوده يمكن تأكيده بفحص XML للمستند أو باستخدام Aspose.Words لاستعراض الأشكال.

```java
        // Save the document to the desired location
        doc.save("YOUR_DIRECTORY/ShapeVisibilityDemo.docx");
    }
}
```

*النتيجة المتوقعة:* عند فتح `ShapeVisibilityDemo.docx` ستظهر صفحة عادية بدون رسومات مرئية. إذا فحصت المستند باستخدام عارض ZIP وفتحت `word/document.xml`، ستجد عنصر `<w:shape>` يحتوي على `hidden="true"` و`<v:fillcolor>` بقيمة `#00FF00`.

---

## اختلافات شائعة وحالات حافة

- **أنواع أشكال مختلفة:** استبدل `ShapeType.ELLIPSE` بـ `ShapeType.RECTANGLE` أو `ShapeType.CLOUD` أو أي قيمة enum مدعومة أخرى للحصول على الشكل المطلوب.
- **الرؤية الشرطية:** يمكنك تبديل `ellipse.setHidden(false)` بناءً على منطق وقت التشغيل، مما يتيح توليد مستندات ديناميكية.
- **تعبئات معقدة:** بدلاً من لون صلب، استخدم `ellipse.getFill().setTextureImage(...)` لتعبئات بنقوش. لا يزال أسلوب `setHidden` يتحكم في الرؤية.
- **أشكال متعددة:** أنشئ مصفوفة أو قائمة من كائنات `Shape`، واضبط كل واحدة بشكل مستقل، وأخفِ فقط تلك التي تفي بمعايير معينة.

*نصيحة احترافية:* عند توليد مستندات كبيرة، أعد استخدام نسخة واحدة من `DocumentBuilder` بدلاً من إنشاء واحدة جديدة لكل شكل. هذا يقلل من استهلاك الذاكرة ويحسن الأداء.

---

## الخلاصة

أصبحت الآن تعرف كيفية **إنشاء مستند Word باستخدام Java** الذي يدرج إهليلج، **تعيين لون تعبئة الشكل**، و**إخفاء الشكل في Word** باستخدام Aspose.Words. المثال الكامل القابل للتنفيذ يوضح كل استدعاء API، يشرح سبب ضرورة كل خطوة، ويظهر النتيجة المتوقعة.

بعد ذلك، استكشف مواضيع ذات صلة مثل **كيفية إدراج شكل** مع التفاف النص، إضافة روابط تشعبية إلى الأشكال، وتصدير المستند إلى PDF مع الحفاظ على العناصر المخفية. جرّب ألواناً، أحجاماً، وعلامات رؤية مختلفة لتخصيص أتمتة Word وفق احتياجات مشروعك.

هل أنت مستعد لأتمتة مزيد من ميزات Word؟ اطلع على وثائق Aspose.Words for Java حول [working with shapes](https://docs.aspose.com/words/java/working-with-shapes/) وابدأ في بناء مستندات غنية تُنشأ برمجياً اليوم.

## ما الذي يجب أن تتعلمه بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات الموضحة في هذا الدليل. كل مصدر يتضمن أمثلة شيفرة كاملة مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف أساليب تنفيذ بديلة في مشاريعك.

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}