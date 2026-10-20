---
category: general
date: 2026-03-19
description: تعلم كيفية تعيين الظل على شكل بسرعة، إضافة الظل إلى الشكل، تغيير الشفافية،
  تمويه الظل وتحديد المسافة باستخدام Aspose.Words for Java.
draft: false
keywords:
- how to set shadow
- add shadow to shape
- how to change transparency
- how to blur shadow
- how to set distance
language: ar
og_description: أتقن كيفية تعيين الظل على شكل في Aspose.Words. يوضح هذا الدليل كيفية
  إضافة الظل إلى الشكل، وتغيير الشفافية، وتمويه الظل، وتحديد المسافة.
og_title: كيفية ضبط الظل على شكل – دليل جافا خطوة بخطوة
tags:
- Aspose.Words
- Java
- ShapeShadow
title: كيفية تعيين الظل على شكل في Aspose.Words – دليل كامل
url: /ar/java/images-shapes/how-to-set-shadow-on-a-shape-in-aspose-words-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# كيفية إضافة ظل إلى شكل في Aspose.Words – دليل كامل

هل تساءلت يومًا **كيفية إضافة ظل** إلى شكل دون الغوص في وثائق API اللامتناهية؟ لست وحدك. يواجه العديد من المطورين صعوبة عندما يحتاجون إلى ظل خفيف لتخطيط، شعار، أو توضيح في مستند Word. الخبر السار؟ الأمر سهل جدًا مع Aspose.Words for Java، ويمكنك القيام به في بضع أسطر فقط.

في هذا الدرس سنستعرض العملية بالكامل: **إضافة ظل إلى الشكل**، تعديل **الشفافية**، تطبيق **تمويه**، وضبط **المسافة** والزاوية. في النهاية ستحصل على شكل مُنسق بالكامل يبدو أنيقًا، وستفهم لماذا كل خاصية مهمة.

---

## المتطلبات المسبقة

قبل أن نبدأ، تأكد من وجود ما يلي:

- Java 8 أو أحدث مثبتة.
- Aspose.Words for Java (أحدث نسخة؛ في وقت كتابة هذا الدليل v24.10).
- ملف `.docx` بسيط يحتوي على شكل واحد على الأقل (مثل مستطيل أو صورة) في الملف `input.docx`.
- بيئة التطوير المتكاملة المفضلة لديك (IntelliJ IDEA، Eclipse، VS Code… أيًا كان).

لا توجد مكتبات إضافية مطلوبة—Aspose.Words يأتي مع كل ما تحتاجه.

---

## كيفية إضافة ظل إلى شكل – خطوة بخطوة

نقسم الحل إلى خطوات صغيرة. كل خطوة تتضمن مقتطفًا قصيرًا من الشيفرة، شرحًا **لـ لماذا** نقوم بذلك، ونصيحة قد تكون مفيدة.

### 1. تحميل المستند المصدر

أولًا نحتاج إلى كائن `Document` يشير إلى الملف على القرص. فكر فيه كفتح ملف Word في الذاكرة.

```java
import com.aspose.words.*;

public class ShadowDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Load the source document
        Document doc = new Document("YOUR_DIRECTORY/input.docx");
```

*لماذا هذا مهم:* بدون مستند محمَّل لا شيء لتعديله. فئة `Document` هي نقطة الدخول لأي عملية في Aspose.Words.

> **نصيحة احترافية:** استخدم مسارًا مطلقًا أثناء التطوير لتجنب مفاجآت “الملف غير موجود”.

### 2. إضافة ظل إلى الشكل – استرجاع أول شكل

الآن نحدد الشكل الذي نريد تنسيقه. المحدد `NodeType.SHAPE` يتجول في شجرة العقد ويعيد أول `Shape` يصادفه.

```java
        // Step 2: Retrieve the first shape in the document
        Shape firstShape = (Shape) doc.getChild(NodeType.SHAPE, 0, true);
```

*لماذا هذا مهم:* الأشكال يمكن أن تكون صورًا، رسومات، أو SmartArt. الحصول على العقدة الصحيحة يضمن أننا لا نعدل عن طريق الخطأ فقرة أو جدول.

> **احذر:** إذا كان المستند لا يحتوي على أشكال، فستكون القيمة `firstShape` `null` وستتسبب الأسطر التالية في رمي `NullPointerException`. تأكد دائمًا من فحص `null` في الكود الإنتاجي.

### 3. كيفية تغيير شفافية الظل

الظل الكامل اللون يبدو ثقيلًا. ضبط خاصية `transparency` يتيح لك تقليلها إلى غشاء خفيف.

```java
        // Step 3: Obtain the shadow formatting object for the shape
        ShadowFormat shadowFormat = firstShape.getShadowFormat();

        // Step 4: Make the shadow 30 % transparent
        shadowFormat.setTransparency(0.3);
```

*لماذا هذا مهم:* الشفافية تتحكم في مقدار ما يظهر من المحتوى الأساسي من خلال الظل. القيمة `0.0` تعني أسود صلب؛ `0.3` تعطي تأثيرًا شفافًا خفيفًا.

> **خطأ شائع:** نسيان استدعاء `setTransparency` يترك القيمة الافتراضية (معتمة تمامًا)، مما قد يجعل الظل قاسيًا جدًا.

### 4. كيفية تمويه الظل

التمويه ينعّم الحواف، مما يجعل الظل يبدو أكثر طبيعية، خاصة على الشاشات عالية الدقة.

```java
        // Step 5: Apply a soft blur with a radius of 5 points
        shadowFormat.setBlurRadius(5.0);
```

*لماذا هذا مهم:* نصف قطر التمويه `0` ينتج حافة حادة غير واقعية. زيادة نصف القطر تنشر الظل، محاكاةً لتشتت الضوء في العالم الحقيقي.

> **اختبار سريع:** غيّر `5.0` إلى `10.0` وأعد التشغيل—لاحظ كيف يصبح الظل أكثر نعومة.

### 5. كيفية ضبط المسافة والزاوية للظل

المسافة تحرك الظل بعيدًا عن الشكل، بينما الزاوية تحدد اتجاه مصدر الضوء.

```java
        // Step 6: Set the shadow offset distance to 4 points
        shadowFormat.setDistance(4.0);

        // Step 7: Define the shadow direction angle (45 degrees)
        shadowFormat.setAngle(45.0);
```

*لماذا هذا مهم:* المسافة `0` تثبت الظل مباشرة خلف الشكل، وغالبًا ما يبدو مسطحًا. زاوية `45°` تحاكي مصدر ضوء من أعلى اليسار، وهو اختيار شائع في التصميم.

> **حالة حافة:** الزوايا تُقاس باتجاه عقارب الساعة من المحور الأفقي. زاوية `180` تقلب الظل إلى الجانب المقابل.

### 6. حفظ المستند

أخيرًا، اكتب المستند المعدل إلى القرص. يمكنك استبدال الملف الأصلي أو إنشاء ملف جديد.

```java
        // Save the updated document
        doc.save("YOUR_DIRECTORY/output_with_shadow.docx");
    }
}
```

*لماذا هذا مهم:* الحفظ يثبت جميع إعدادات الظل التي قمت بتكوينها. افتح الملف الناتج في Word لترى التأثير.

---

## مثال كامل يعمل

نجمع كل ما سبق في برنامج جاهز للتنفيذ:

```java
import com.aspose.words.*;

public class ShadowDemo {
    public static void main(String[] args) throws Exception {
        // Load the source document
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // Retrieve the first shape (add null‑check for safety)
        Shape firstShape = (Shape) doc.getChild(NodeType.SHAPE, 0, true);
        if (firstShape == null) {
            System.out.println("No shapes found in the document.");
            return;
        }

        // Access the shadow format
        ShadowFormat shadowFormat = firstShape.getShadowFormat();

        // Make the shadow 30 % transparent
        shadowFormat.setTransparency(0.3);

        // Apply a soft blur with a radius of 5 points
        shadowFormat.setBlurRadius(5.0);

        // Set the shadow offset distance to 4 points
        shadowFormat.setDistance(4.0);

        // Define the shadow direction angle (45 degrees)
        shadowFormat.setAngle(45.0);

        // Save the modified document
        doc.save("YOUR_DIRECTORY/output_with_shadow.docx");

        System.out.println("Shadow applied successfully!");
    }
}
```

**النتيجة المتوقعة:** افتح `output_with_shadow.docx`. يجب أن يعرض الشكل الأول ظلًا ناعمًا بنسبة شفافية 30 %، مع تمويه طفيف، وإزاحة 4 نقطة بزاوية 45°. يبدو كما لو أن الشكل يطفو فوق الصفحة.

---

## الأسئلة المتكررة (FAQ)

### هل يمكنني إضافة ظل إلى عدة أشكال في آن واحد؟

بالتأكيد. استبدل استرجاع الشكل الفردي بحلقة:

```java
NodeCollection shapes = doc.getChildNodes(NodeType.SHAPE, true);
for (Node node : shapes) {
    Shape shape = (Shape) node;
    ShadowFormat sf = shape.getShadowFormat();
    // Apply the same settings or vary per shape
}
```

### ماذا لو أردت ظلًا ملونًا بدلاً من الأسود؟

`ShadowFormat` يوفر أيضًا طريقة `setColor(Color)`. للحصول على ظل أزرق عميق:

```java
shadowFormat.setColor(Color.fromArgb(0, 0, 255));
```

### هل يعمل هذا مع الصور داخل الشكل؟

نعم. Aspose.Words يتعامل مع الصور ككائنات `Shape` طالما تم إدراجها كـ “Picture” (ليس inline). تنطبق نفس خصائص الظل.

### هل يُقاس نصف قطر التمويه بالنقاط أم بالبكسل؟

يُقاس بالنقاط (1 pt = 1/72 in). هذا يحافظ على المظهر متسقًا عبر إعدادات DPI المختلفة.

---

## الخلاصة

غطّينا **كيفية إضافة ظل** إلى شكل من البداية إلى النهاية، وعرضنا **إضافة ظل إلى الشكل**، وشرحنا **كيفية تغيير الشفافية**، و**كيفية تمويه الظل**، وأخيرًا **كيفية ضبط المسافة** والزاوية. الشيفرة مختصرة، المفاهيم واضحة، والآن لديك نمط قابل لإعادة الاستخدام لتنسيق أي شكل في Aspose.Words for Java.

هل أنت مستعد للتحدي التالي؟ جرّب دمج إعدادات الظل هذه مع **تعبئات متدرجة**، أو جرب **ظلال متعددة** عن طريق استنساخ الشكل وإزاحة كل نسخة. السماء هي الحد، ومع الأدوات التي تعلمتها الآن، ستتمكن من إعطاء مستنداتك لمسة احترافية في وقت قصير.

إذا وجدت هذا الدليل مفيدًا، اترك تعليقًا، شارك تنويعاتك، أو استكشف دروسنا الأخرى حول **تنسيق الأشكال**، **تأثيرات النص**، و**تحويل المستندات**. برمجة سعيدة! 

![مثال على كيفية إضافة ظل إلى شكل](image.png)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}