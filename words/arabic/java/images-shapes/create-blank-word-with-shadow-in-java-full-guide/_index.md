---
category: general
date: 2026-05-04
description: إنشاء مستند Word فارغ في Java وتعلم كيفية ضبط لون الظل والتمويه والإزاحة
  للأشكال – دليل سريع.
draft: false
keywords:
- create blank word
- set shadow color
- how to add shadow
- how to set blur
- how to set offset
language: ar
og_description: إنشاء مستند Word فارغ في Java وتعلم كيفية ضبط لون الظل، والضبابية،
  والإزاحة للأشكال. اتبع هذا الدرس خطوة بخطوة.
og_title: إنشاء كلمة فارغة مع ظل في جافا – دليل كامل
tags:
- Aspose.Words
- Java
- Document Automation
title: إنشاء كلمة فارغة مع ظل في جافا – دليل كامل
url: /ar/java/images-shapes/create-blank-word-with-shadow-in-java-full-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# إنشاء مستند Word فارغ مع ظل في Java – دليل كامل

هل احتجت يوماً إلى **إنشاء مستند Word فارغ** من الكود وجعله يبدو أكثر أناقة؟ لست وحدك. في العديد من مشاريع التقارير أو توليد القوالب، أول شيء تفعله هو إنشاء مستند Word فارغ، ثم إضافة شكل بظل لإضفاء لمسة احترافية.  

في هذا الدرس سنستعرض خطوة بخطوة كيفية إنشاء مستند Word فارغ باستخدام Aspose.Words for Java، **كيفية إضافة ظل** إلى شكل، وتفاصيل **تعيين لون الظل**، **كيفية ضبط الضبابية**، و**كيفية ضبط الإزاحة**. في النهاية ستحصل على ملف `.docx` جاهز يُظهر مستطيلاً بظل أحمر نصف شفاف ومُطمس بشكل جميل.

## ما ستحتاجه

- **Aspose.Words for Java** (أي نسخة حديثة؛ الكود يعمل مع 23.9+)
- JDK 8 أو أحدث
- بيئة تطوير متكاملة أو محرر نصوص بسيط مع طرفية
- معرفة أساسية بـ Java—لا شيء معقد، فقط القدرة على تشغيل دالة `main`

لا يلزم أي إعداد إضافي لـ Maven أو Gradle للعرض؛ فقط ضع ملف JAR الخاص بـ Aspose في مسار الـ classpath وستكون جاهزاً.

---

![create blank word document with shadow example](image-placeholder.png){: .center alt="مثال على إنشاء مستند Word فارغ مع ظل"}

## إنشاء مستند Word فارغ – تهيئة الـ Document

الخطوة الأولى هي إنشاء ملف Word جديد وفارغ تماماً. فكر فيه كقماش نظيف يمكنك لاحقاً رسم الأشكال أو الجداول أو النصوص عليه.

```java
import com.aspose.words.*;

public class ShadowDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank Word document
        Document document = new Document();

        // Step 2: Initialise a DocumentBuilder to add content
        DocumentBuilder builder = new DocumentBuilder(document);
```

> **لماذا هذا مهم:** `Document` يمثل الحزمة الكاملة للملف `.docx`. بإنشائه باستخدام المُنشئ الافتراضي فأنت فعلياً **تنشئ مستند Word فارغ** – لا محتوى، لا أقسام، فقط بنية الملف جاهزة لتملأها.

## كيفية إضافة ظل إلى شكل

الآن بعد أن أصبح لدينا مستند نظيف، لنُدخل مستطيلاً سيحمل الظل. هنا يبدأ السحر البصري.

```java
        // Step 3: Insert a rectangle shape that will receive a custom shadow
        Shape rectangleShape = builder.insertShape(ShapeType.RECTANGLE, 150, 80);
```

> **نصيحة محترف:** استدعاء `insertShape` يضيف الشكل تلقائياً إلى الفقرة الحالية، لذا لا تحتاج إلى إدارة الموضع يدوياً إلا إذا أردت وضعاً مطلقاً.

## تعيين لون الظل – لجعل الظل بارزاً

الظل بدون لون هو مجرد تمويه رمادي، قد يبدو مسطحاً. بتعيين لون الظل يمكنك مطابقة هوية العلامة أو ببساطة جعله يبرز.

```java
        // Step 4a: Make the shadow visible and set its color
        rectangleShape.getShadowFormat().setVisible(true);
        rectangleShape.getShadowFormat().setColor(java.awt.Color.RED); // set shadow color
```

> **ما يحدث:** `ShadowFormat` يتحكم في كل جانب بصري للظل. تمكين `setVisible(true)` يُفعّل التأثير، و`setColor` يتيح لك اختيار أي `java.awt.Color`. في مثالنا اخترنا اللون الأحمر لتوضيح **تعيين لون الظل** بوضوح.

## كيفية ضبط الضبابية لتأثير ناعم

الظل الحاد ذو الحواف الصلبة قد يبدو قاسياً. إضافة الضبابية تُنعّم الحواف، مما يمنح مظهراً أكثر طبيعية.

```java
        // Step 4b: Define how fuzzy the shadow should be
        rectangleShape.getShadowFormat().setBlur(5.0); // how to set blur
```

> **لماذا الضبابية مهمة:** قيمة `setBlur` تُقاس بالنقاط. القيمة `5.0` تُنتج انتشاراً خفيفاً؛ زدها للحصول على ظل أكثر سحابة، أو قلّها للحصول على حافة أكثر حدة.

## كيفية ضبط الإزاحة – تموضع الظل

الإزاحات تحدد مكان سقوط الظل بالنسبة للشكل. فكر فيها كتحركات X و Y.

```java
        // Step 4c: Position the shadow horizontally and vertically
        rectangleShape.getShadowFormat().setOffsetX(8.0); // how to set offset (horizontal)
        rectangleShape.getShadowFormat().setOffsetY(8.0); // how to set offset (vertical)
```

> **شرح الإزاحة:** قيمة X الموجبة تحرك الظل إلى اليمين، وقيمة Y الموجبة تحركه إلى الأسفل. جرّب القيم السالبة إذا أردت أن يظهر الظل على الجانب المقابل.

## ضبط الشفافية بدقة

إذا رغبت في أن يكون الظل أقل بروزاً، عدّل شفافيته. هذه الخطوة ليست مطلباً رئيسياً لكنها تُكمل التحكم البصري.

```java
        // Optional: Make the shadow semi‑transparent (30 % transparent)
        rectangleShape.getShadowFormat().setTransparency(0.3);
```

## حفظ المستند – شاهد النتيجة

أخيراً، اكتب المستند إلى القرص. ستحصل على ملف `.docx` يمكنك فتحه في Word أو LibreOffice أو أي عارض يدعم الصيغة.

```java
        // Step 5: Save the document with the shaped shadow
        document.save("YOUR_DIRECTORY/ShadowShape.docx");
    }
}
```

> **ما يجب أن تراه:** افتح `ShadowShape.docx`. ستظهر صفحة واحدة تحتوي على مستطيل بحجم 150 × 80 pt مع ظل أحمر مُطمس قليلاً ومُزاح 8 pt إلى الأسفل واليمين. الظل شفاف بنسبة 30 %، لذا يبقى المستطيل واضحاً.

---

## أسئلة شائعة وحالات خاصة

### ماذا لو احتجت إلى شكل مختلف؟

استبدل `ShapeType.RECTANGLE` بأي قيمة أخرى من الـ enum (`ELLIPSE`, `CLOUD`, `CALLOUT`, إلخ). إعدادات الظل تعمل بنفس الطريقة على جميع الأشكال.

### هل يمكن تطبيق نفس الظل على عدة أشكال دون تكرار الكود؟

بالتأكيد. أنشئ دالة مساعدة:

```java
private static void applyShadow(Shape shape, java.awt.Color color,
                                double blur, double offsetX, double offsetY,
                                double transparency) {
    shape.getShadowFormat().setVisible(true);
    shape.getShadowFormat().setColor(color);
    shape.getShadowFormat().setBlur(blur);
    shape.getShadowFormat().setOffsetX(offsetX);
    shape.getShadowFormat().setOffsetY(offsetY);
    shape.getShadowFormat().setTransparency(transparency);
}
```

ثم استدعِ `applyShadow(rectangleShape, Color.RED, 5.0, 8.0, 8.0, 0.3);` لأي شكل.

### هل يعمل هذا مع إصدارات Aspose القديمة؟

واجهة `ShadowFormat` مستقرة منذ الإصدار 19.8، لذا يجب أن تكون بخير مع معظم الإصدارات الحديثة. إذا كنت تستخدم نسخة قديمة جداً، تحقق من Javadoc الخاص بـ `ShadowFormat` لتأكيد أسماء الطرق.

### كيف أصدّر إلى PDF مع الحفاظ على الظل؟

فقط استدعِ `document.save("output.pdf");` بعد إنشاء الشكل. Aspose.Words يرسم الظلال بشكل صحيح في PDF، مع الحفاظ على الضبابية والشفافية.

---

## ملخص – إنشاء مستند Word فارغ بظل مخصص

بدأنا بـ **إنشاء مستند Word فارغ** باستخدام `new Document()`، ثم أدخلنا مستطيلاً، **حددنا لون الظل**، تعلمنا **كيفية إضافة ظل**، ضبطنا **كيفية ضبط الضبابية**، وأخيراً عدّلنا **كيفية ضبط الإزاحة** لتحديد موضعه بدقة. الكود الكامل القابل للتنفيذ موجود في المقتطف أعلاه، والملف الناتج يُظهر التأثير بوضوح.

---

## ما التالي؟

- **جرب خصائص ظل أخرى** مثل `ShadowFormat.setStyle(ShadowStyle.OUTER)` للحصول على أنماط بصرية مختلفة.
- **اجمع عدة أشكال** كل منها بظل خاص لبناء مخططات معقدة.
- **أضف نصاً داخل الشكل** باستخدام `builder.insertHtml("<b>Hello</b>")` قبل إدراج الشكل، ثم طبّق نفس منطق الظل.
- **استكشف خيارات تنسيق أخرى** مثل نمط الخط، لون التعبئة، أو التعبئات المتدرجة—Aspose.Words يوفر API غني لهذه الأمور.

لا تتردد في تعديل نصف القطر الضبابي، الإزاحات، أو الألوان حتى يصبح الظل مناسباً تماماً للغة تصميم مستندك. برمجة سعيدة، ولتظل ملفات Word التي تُنشئها دائماً أكثر صقلاً!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}