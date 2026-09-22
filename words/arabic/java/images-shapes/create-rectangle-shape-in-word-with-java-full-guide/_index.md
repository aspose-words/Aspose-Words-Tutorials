---
category: general
date: 2026-02-10
description: إنشاء شكل مستطيل في مستند Word باستخدام Aspose.Words للغة Java. تعلّم
  كيفية تعيين لون الظل، وكيفية إضافة الظل، وإنشاء مستند Word برمجيًا.
draft: false
keywords:
- create rectangle shape
- set shadow color
- create word document
- how to add shadow
- how to create shape
language: ar
og_description: إنشاء شكل مستطيل في مستند Word باستخدام Aspose.Words للغة Java. اتبع
  هذا الدليل خطوة بخطوة لتعيين لون الظل، إضافة الظل، وإنشاء مستند Word.
og_title: إنشاء شكل مستطيل في Word باستخدام Java – دليل كامل
tags:
- Aspose.Words
- Java
- Document Automation
title: إنشاء شكل مستطيل في Word باستخدام Java – دليل كامل
url: /ar/java/images-shapes/create-rectangle-shape-in-word-with-java-full-guide/
---

produce final content with all translations.

Be careful to preserve markdown formatting exactly.

Let's craft final answer.{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# إنشاء شكل مستطيل في Word باستخدام Java – دليل كامل

هل احتجت يومًا إلى **إنشاء شكل مستطيل** في مستند Word لكنك لم تكن متأكدًا من أين تبدأ؟ لست وحدك—فالعديد من المطورين يواجهون هذا التحدي عندما يحاولون رسم رسومات برمجيًا في Word للمرة الأولى. الخبر السار؟ مع Aspose.Words for Java يمكنك وضع مستطيل على صفحة، إضافة ظل جميل، وحفظ الملف في ثوانٍ. في هذا الدرس سنستعرض بالضبط **كيفية إضافة الظل**، **تعيين لون الظل**، و**إنشاء مستند Word** من الصفر.  

سنغطي كل ما تحتاجه: المكتبات المطلوبة، كل سطر من الشيفرة، لماذا بعض الإعدادات مهمة، وبعض الحيل التي قد لا تجدها في الوثائق الرسمية. في النهاية ستحصل على مثال جاهز للتنفيذ يُنشئ شكل مستطيل بظل رمادي ناعم، محفوظًا باسم *Shadow.docx*.

## المتطلبات المسبقة – ما تحتاجه قبل البدء

قبل أن نغوص في الشيفرة، تأكد من وجود ما يلي:

| المتطلب | السبب |
|-------------|--------|
| Java Development Kit (JDK) 8 أو أحدث | Aspose.Words يعمل على أي JDK حديث. |
| Maven أو Gradle (اختياري) | يبسط إضافة تبعية Aspose.Words. |
| ترخيص Aspose.Words for Java (أو نسخة تجريبية مجانية) | المكتبة تجارية؛ النسخة التجريبية تكفي للاختبار. |
| بيئة تطوير متكاملة (IntelliJ IDEA، Eclipse، VS Code، إلخ) | تساعدك على تشغيل وتصحيح المثال بسرعة. |

إذا كان لديك مشروع Java بالفعل، فقط أضف إحداثيات Maven:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version> <!-- Replace with the latest version -->
</dependency>
```

لا حاجة لإعدادات معقدة أكثر من ذلك—طريقة `public static void main` العادية تكفي.

![مثال على إنشاء شكل مستطيل](https://example.com/rectangle-shadow.png "إنشاء شكل مستطيل مع ظل في Word")

*نص بديل للصورة: مثال على إنشاء شكل مستطيل يظهر مستطيلًا سيناويًا مع ظل رمادي.*

## الخطوة 1 – إنشاء مستند Word جديد

أول شيء علينا القيام به هو إنشاء مستند فارغ. فكر فيه كفتح ملف Word جديد سترسم عليه لاحقًا.

```java
// Step 1: Initialize a blank Document object
Document document = new Document();
```

لماذا نبدأ بـ `Document` فارغ؟ لأن Aspose.Words يتعامل مع فئة `Document` كقماش لجميع العمليات اللاحقة—إضافة فقرات، جداول، أو أشكال. إذا تخطيت هذه الخطوة ستحصل على `NullPointerException` في اللحظة التي تحاول فيها إدراج أي شيء.

## الخطوة 2 – إعداد DocumentBuilder

`DocumentBuilder` هو القلم الودود الذي يكتب داخل الـ `Document`. إنه الطريقة الموصى بها لإضافة المحتوى لأنه يدير موضع المؤشر تلقائيًا.

```java
// Step 2: Create a DocumentBuilder tied to our document
DocumentBuilder builder = new DocumentBuilder(document);
```

قد تتساءل، “لماذا لا أتعامل مع المستند مباشرةً؟” الجواب: الـ builder يج abstracts التفاصيل منخفضة المستوى مثل معالجة الأقسام، مما يجعل الشيفرة أنظف وأقل عرضة للأخطاء.

## الخطوة 3 – إدراج شكل المستطيل

الآن يأتي الجزء الممتع—**كيفية إنشاء الشكل**. سنُدرج مستطيلًا بأبعاد 100 × 50 نقطة ونملأه باللون السيناوي حتى تتمكن من رؤيته بوضوح.

```java
// Step 3: Insert a rectangle shape of size 100x50 points
Shape rectangle = builder.insertShape(ShapeType.RECTANGLE, 100, 50);

// Apply a solid fill color to make the shape visible
rectangle.setFillColor(java.awt.Color.CYAN);
```

بعض الملاحظات:

* `ShapeType.RECTANGLE` يُخبر Aspose أننا نريد مستطيلًا؛ يمكنك استبداله بـ `OVAL` أو `LINE` وغيرها.
* الأبعاد مُعبر عنها بالنقاط (1 pt ≈ 1/72 in). عدّلها لتناسب تخطيطك.
* بدون لون تعبئة سيكون الشكل غير مرئي على صفحة بيضاء—ولهذا نستخدم السيناوي.

## الخطوة 4 – إضافة ظل و**تعيين لون الظل**

هنا نجيب على جزء **كيفية إضافة الظل** من اللغز. كائن `ShadowFormat` يتحكم في كل جانب بصري للظل، من اللون إلى نصف قطر الضبابية.

```java
// Step 4: Enable the shape's shadow and configure its appearance
rectangle.getShadowFormat().setVisible(true);                     // Turn the shadow on
rectangle.getShadowFormat().setColor(java.awt.Color.GRAY);      // **set shadow color** to gray
rectangle.getShadowFormat().setBlurRadius(5.0);                  // Soft blur for realism
rectangle.getShadowFormat().setOffsetX(4.0);                     // Horizontal offset
rectangle.getShadowFormat().setOffsetY(4.0);                     // Vertical offset
rectangle.getShadowFormat().setTransparency(0.3);               // 30 % transparent
```

لماذا هذه القيم بالتحديد؟

* **الظهور** – بدون `setVisible(true)` تُهمل باقي الإعدادات.
* **اللون** – الرمادي خيار محايد يعمل على الخلفيات الفاتحة والداكنة. يمكنك استبدال `java.awt.Color.GRAY` بأي `java.awt.Color` تفضله.
* **نصف قطر الضبابية** – القيمة `5.0` تعطي ظلًا ناعمًا؛ القيم الأكبر تجعل الظل أكثر انتشارًا.
* **OffsetX/Y** – الإزاحات تحرك الظل إلى اليمين والأسفل، محاكاةً لمصدر ضوء من أعلى اليسار.
* **الشفافية** – الظل شبه الشفاف يندمج بشكل أفضل مع الصفحة، خاصة عند الطباعة.

إذا أردت مظهرًا أكثر حدة، اجعل نصف قطر الضبابية `0` وزد الإزاحة. التجربة مُشجَّعة—الظلال بصرية جدًا، والإعدادات المثالية تعتمد على تصميم مستندك.

## الخطوة 5 – حفظ المستند

أخيرًا، نحفظ كل شيء في ملف `.docx`. يمكنك اختيار أي مسار تريده؛ فقط تأكد من وجود المجلد.

```java
// Step 5: Save the document with the shaped shadow to a file
document.save("YOUR_DIRECTORY/Shadow.docx");
```

عند فتح *Shadow.docx* في Microsoft Word، سترى مستطيلًا سيناويًا مع ظل رمادي خفيف يطفو 4 نقطة إلى اليمين والأسفل. هذه هي عملية **إنشاء مستند Word** الكاملة.

### النتيجة المتوقعة

| العنصر | المظهر |
|---------|------------|
| مستطيل | تعبئة سيناوية، حجم 100 × 50 pt |
| ظل | رمادي، 30 % شفاف، تمويه 5 pt، إزاحة (4, 4) |
| ملف | `Shadow.docx` مخزن في المسار الذي قدمته |

إذا لم يظهر الشكل، تحقق مرة أخرى من أن لون التعبئة ليس هو نفسه لون خلفية الصفحة وأن الظل مُعين كـ visible.

## نصائح احترافية ومخاطر شائعة

* **نصيحة احترافية:** استخدم `rectangle.setStrokeColor(java.awt.Color.BLACK);` إذا أردت حدًا حول الشكل. يجعل المستطيل يبرز أكثر على الصفحة المطبوعة.
* **احذر من:** حفظ الملف في مجلد للقراءة فقط سيؤدي إلى رمي `IOException`. اختر موقعًا قابلًا للكتابة أو عدّل أذونات الملف.
* **حالة حافة:** إذا كنت تحتاج تعبئة شفافة (بدون لون)، استدعِ `rectangle.setFillColor(java.awt.Color.WHITE); rectangle.setFillOpacity(0.0);`. سيظل الشكل يُسقط ظلًا، وهو مفيد للرسومات على نمط العلامة المائية.
* **ملاحظة أداء:** إضافة مئات الأشكال داخل حلقة قد يزيد من استهلاك الذاكرة. استدعِ `document.save` مرة واحدة فقط بعد إضافة جميع الأشكال.

## مثال كامل يعمل

فيما يلي البرنامج الكامل الذي يمكنك نسخه ولصقه في فئة Java تسمى `ShadowDemo`. يَتَجَمَّع ويعمل كما هو (بشرط وجود ملف JAR الخاص بـ Aspose.Words في مسار الـ classpath).

```java
import com.aspose.words.*;

public class ShadowDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document
        Document document = new Document();

        // Step 2: Initialize a DocumentBuilder to construct the document content
        DocumentBuilder builder = new DocumentBuilder(document);

        // Step 3: Insert a rectangle shape of size 100x50 points
        Shape rectangle = builder.insertShape(ShapeType.RECTANGLE, 100, 50);
        // Apply a solid fill color to make the shape visible
        rectangle.setFillColor(java.awt.Color.CYAN);

        // Step 4: Enable the shape's shadow and configure its appearance
        rectangle.getShadowFormat().setVisible(true);
        rectangle.getShadowFormat().setColor(java.awt.Color.GRAY); // set shadow color
        rectangle.getShadowFormat().setBlurRadius(5.0);
        rectangle.getShadowFormat().setOffsetX(4.0);
        rectangle.getShadowFormat().setOffsetY(4.0);
        rectangle.getShadowFormat().setTransparency(0.3);

        // Step 5: Save the document with the shaped shadow to a file
        document.save("YOUR_DIRECTORY/Shadow.docx");
    }
}
```

شغّل البرنامج، افتح ملف *Shadow.docx* الناتج، وسترى المستطيل مع ظله تمامًا كما هو موصوف.

## ماذا لو كنت بحاجة إلى مزيد من الأشكال؟

قد تتساءل، “هل يمكنني **إنشاء شكل مستطيل** عدة مرات أو استخدام أشكال أخرى؟” بالتأكيد. فقط كرّر كود الإدراج وعدّل الإحداثيات باستخدام `builder.moveTo` أو `builder.insertParagraph`. يمكن إعادة استخدام إعدادات الظل نفسها عن طريق استخراجها إلى طريقة مساعدة:

```java
private static void applyStandardShadow(Shape shape) {
    shape.getShadowFormat().setVisible(true);
    shape.getShadowFormat().setColor(java.awt.Color.GRAY);
    shape.getShadowFormat().setBlurRadius(5.0);
    shape.getShadowFormat().setOffsetX(4.0);
    shape.getShadowFormat().setOffsetY(4.0);
    shape.getShadowFormat().setTransparency(0.3);
}
```

استدعِ `applyStandardShadow(rectangle);` بعد كل إدراج شكل للحفاظ على مبدأ DRY (Don’t Repeat Yourself).

## الخطوات التالية – ما بعد الأساسيات

الآن بعد أن عرفت **كيفية إضافة الظل**، فكر في استكشاف المواضيع ذات الصلة:

* **كيفية تعيين لون الظل** لتشغيل النصوص – يمنح العناوين ارتقاءً طفيفًا.
* **إنشاء مستند Word** مع جداول وصور – دمج الأشكال مع محتويات أخرى.
* **كيفية إنشاء شكل** رسوم متحركة باستخدام الأدوات المدمجة في Word

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}