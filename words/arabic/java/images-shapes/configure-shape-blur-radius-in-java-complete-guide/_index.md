---
category: general
date: 2026-06-27
description: تعلم كيفية ضبط نصف قطر الضبابية للشكل باستخدام Aspose.Words for Java.
  يغطي هذا الدليل خطوة بخطوة أيضًا إعدادات الظل والشفافية وحفظ المستند.
draft: false
keywords:
- configure shape blur radius
- Aspose.Words shape shadow
- Java shadow format
- Word document shape manipulation
- set blur radius
language: ar
og_description: قم بتكوين نصف قطر الضبابية للشكل في مستند Word باستخدام Java. اتبع
  هذا الدليل التفصيلي لإتقان إعدادات ظل الشكل في Aspose.Words.
og_title: تكوين نصف قطر التشويش للشكل في جافا – دليل كامل
schemas:
- author: Aspose
  dateModified: '2026-06-27'
  description: Learn how to configure shape blur radius using Aspose.Words for Java.
    This step‑by‑step tutorial also covers shadow settings, transparency, and saving
    the document.
  headline: Configure Shape Blur Radius in Java – Complete Guide
  type: TechArticle
- description: Learn how to configure shape blur radius using Aspose.Words for Java.
    This step‑by‑step tutorial also covers shadow settings, transparency, and saving
    the document.
  name: Configure Shape Blur Radius in Java – Complete Guide
  steps:
  - name: Understanding the Numbers
    text: '- **Blur radius** (`setBlurRadius`) controls how fuzzy the shadow looks.
      A value of `0` gives a crisp edge, while `10` or higher yields a dreamy glow.
      - **DistanceX / DistanceY** shift the shadow relative to the shape. Positive
      X moves it right; positive Y moves it down. - **Transparency** makes the'
  - name: Targeting a Specific Shape by Name
    text: 'If your document contains many shapes, rely on the shape’s **name** (set
      in Word’s layout options) instead of index:'
  - name: Applying Different Blur Radii
    text: 'You might want a stronger blur for background graphics and a subtle one
      for icons. Loop through all shapes:'
  - name: Compatibility Notes
    text: '- **Units:** Aspose.Words uses points (1 pt = 1/72 inch). If you work with
      millimeters, convert accordingly. - **Version:** The API shown works with Aspose.Words
      for Java 24.9 and later. Older versions may use `setBlurRadius(double)` but
      lack some newer shadow properties.'
  type: HowTo
tags:
- Aspose.Words
- Java
- Document Automation
title: تكوين نصف قطر تشويش الشكل في جافا – دليل كامل
url: /ar/java/images-shapes/configure-shape-blur-radius-in-java-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# تكوين نصف قطر تمويه الشكل في Java – دليل شامل

هل احتجت يومًا إلى **تكوين نصف قطر تمويه الشكل** في مستند Word أثناء العمل بـ Java؟ لست وحدك الذي يحاول حل هذه المشكلة. سواء كنت تُنقّح تقريرًا مؤسسيًا أو تضيف لمسة بصرية خفيفة إلى منشور، فإن إتقان هذا الإعداد يمكن أن يجعل مستنداتك تبدو أكثر احترافية.

في هذا البرنامج التعليمي سنستعرض العملية بالكامل — من تحميل ملف `.docx` إلى تعديل تمويه الظل وأخيرًا حفظ النتيجة. سنتطرق أيضًا إلى مواضيع ذات صلة مثل **Aspose.Words shape shadow**، **Java shadow format**، و**Word document shape manipulation** العامة. بنهاية الدليل ستحصل على مقتطف شفرة جاهز للتنفيذ وفهم واضح لأهمية كل سطر.

## ما ستتعلمه

- كيفية تحميل مستند Word باستخدام Aspose.Words for Java.  
- كيفية العثور على أول كائن `Shape` داخل جسم المستند.  
- الخطوات الدقيقة **لتكوين نصف قطر تمويه الشكل** وخصائص الظل الأخرى مثل المسافة والشفافية.  
- كيفية حفظ التغييرات في ملف `.docx` جديد.  

لا تحتاج إلى مكتبات خارجية غير Aspose.Words، وتعمل الشفرة مع Java 8 فوق وأي نسخة حديثة من Aspose.Words for Java (مثلاً 24.9). إذا كنت مرتاحًا مع أساسيات Java، فستكون بخير.

---

## الخطوة 1: تحميل مستند Word

قبل أن تتمكن من تعديل أي شكل، تحتاج إلى تحميل المستند في الذاكرة. تجعلك Aspose.Words تقوم بذلك بسطر واحد.

```java
// Load the source .docx file
com.aspose.words.Document document = new com.aspose.words.Document("YOUR_DIRECTORY/input.docx");
```

**لماذا هذا مهم:**  
إنشاء كائن `Document` يحلل الملف بالكامل، مما يمنحك الوصول إلى الأقسام والفقرات والجداول **والأشكال**. تخطي هذه الخطوة سيتركك بدون سياق لتطبيق نصف قطر التمويه.

> **نصيحة احترافية:** إذا كنت تتعامل مع ملفات كبيرة، فكر في استخدام `LoadOptions` لتدفق الأجزاء التي تحتاجها فقط. يمكن أن يقلل ذلك من استهلاك الذاكرة بشكل كبير.

---

## الخطوة 2: استرجاع الشكل المستهدف

يمكن أن تتواجد الأشكال في أي مكان — رؤوس، تذييلات، جداول، إلخ. للبساطة، سنأخذ أول شكل يُعثر عليه في جسم القسم الأول.

```java
// Navigate to the first shape in the document body
com.aspose.words.Shape shape = (com.aspose.words.Shape) document
        .getFirstSection()
        .getBody()
        .getChild(com.aspose.words.NodeType.SHAPE, 0, true);
```

**لماذا هذا مهم:**  
استدعاء `getChild` يتجول في شجرة العقد بعمق أول، ويعيد *أول* شكل يطابق `NodeType.SHAPE`. إذا كان مستندك يحتوي على أشكال متعددة، يمكنك تعديل الفهرس (`0`) أو التكرار عبر `document.getChildNodes(NodeType.SHAPE, true)`.

> **حالة حافة:** إذا لم يحتوي المستند على أي أشكال، فستكون قيمة `shape` `null` وسيتسبب السطر التالي في رفع `NullPointerException`. احرص دائمًا على التحقق من ذلك في الشيفرة الإنتاجية.

---

## الخطوة 3: تكوين ظل الشكل – ضبط نصف قطر التمويه

الآن يأتي العنصر الرئيسي: تعديل نصف قطر التمويه. هذا يقع داخل كائن `ShadowFormat` المرتبط بالشكل.

```java
// Access the shadow format of the shape
com.aspose.words.ShadowFormat shadow = shape.getShadowFormat();

// Set the blur radius (in points). Larger values produce a softer edge.
shadow.setBlurRadius(5.0);

// Optional: fine‑tune other shadow attributes
shadow.setDistanceX(3.0);          // Horizontal offset
shadow.setDistanceY(3.0);          // Vertical offset
shadow.setTransparency(0.3);      // 0 = fully opaque, 1 = fully transparent
```

### فهم الأرقام

- **نصف قطر التمويه** (`setBlurRadius`) يتحكم في مدى وضوح الظل. القيمة `0` تعطي حافة حادة، بينما `10` أو أعلى تنتج توهجًا ضبابيًا.  
- **DistanceX / DistanceY** يغيران موضع الظل بالنسبة للشكل. X الموجبة تحركه إلى اليمين؛ Y الموجبة تحركه إلى الأسفل.  
- **الشفافية** تجعل الظل شبه شفاف. مفيد عندما تريد تأثيرًا خفيفًا بدلاً من كتلة سوداء صلبة.

> **لماذا نضبط نصف قطر التمويه؟**  
> في العديد من القوالب المؤسسية، يضيف التمويه الخفيف عمقًا دون إزعاج القارئ. إنها تعديل بصري بسيط يمكنه تحسين جودة المظهر بشكل ملحوظ.

---

## الخطوة 4: حفظ المستند المعدل

اكتملت جميع العمليات الثقيلة؛ الآن احفظ التغييرات إلى القرص.

```java
// Persist the modified document
document.save("YOUR_DIRECTORY/output.docx");
```

**لماذا هذا مهم:**  
استدعاء `save` يكتب المستند بالكامل، بما في ذلك `ShadowFormat` المحدث. إذا كنت تحتاج فقط الشكل كصورة، يمكنك تصديره عبر `shape.getImageData().save(...)` بدلاً من ذلك.

---

## مثال كامل يعمل

فيما يلي البرنامج الكامل المستقل الذي يمكنك نسخه ولصقه في أي بيئة تطوير Java. تأكد من وجود ملف JAR الخاص بـ Aspose.Words for Java في مسار الـ classpath.

```java
import com.aspose.words.*;

public class ConfigureShapeBlurRadius {
    public static void main(String[] args) throws Exception {
        // 1. Load the document
        Document document = new Document("YOUR_DIRECTORY/input.docx");

        // 2. Get the first shape (add null‑check for safety)
        Shape shape = (Shape) document.getFirstSection()
                .getBody()
                .getChild(NodeType.SHAPE, 0, true);
        if (shape == null) {
            System.out.println("No shape found in the document.");
            return;
        }

        // 3. Configure shadow – focus on blur radius
        ShadowFormat shadow = shape.getShadowFormat();
        shadow.setBlurRadius(5.0);          // Soft blur
        shadow.setDistanceX(3.0);           // Horizontal offset
        shadow.setDistanceY(3.0);           // Vertical offset
        shadow.setTransparency(0.3);        // Slightly transparent

        // 4. Save the result
        document.save("YOUR_DIRECTORY/output.docx");
        System.out.println("Document saved with configured shape blur radius.");
    }
}
```

**الناتج المتوقع:**  
تشغيل البرنامج ينتج ملف `output.docx` جديد حيث يحمل الشكل الأول ظلًا ناعمًا شبه شفاف بنصف قطر تمويه قدره `5` نقاط. افتح الملف في Word، حدد الشكل، وتحت **Shape Format → Shadow Effects → Shadow Options**، ستلاحظ القيم التي ضبطتها تظهر في الواجهة.

---

## التعامل مع أشكال متعددة وسيناريوهات متقدمة

### استهداف شكل محدد بالاسم

إذا كان مستندك يحتوي على العديد من الأشكال، اعتمد على **اسم** الشكل (المحدد في خيارات تخطيط Word) بدلاً من الفهرس:

```java
Shape target = (Shape) document.getChildNodes(NodeType.SHAPE, true)
        .stream()
        .filter(node -> ((Shape) node).getName().equals("MyLogo"))
        .findFirst()
        .orElse(null);
```

### تطبيق أنصاف أقطار تمويه مختلفة

قد ترغب في تمويه أقوى للرسومات الخلفية وتمويه أخف للأيقونات. قم بالتكرار عبر جميع الأشكال:

```java
for (Node node : document.getChildNodes(NodeType.SHAPE, true)) {
    Shape s = (Shape) node;
    ShadowFormat sf = s.getShadowFormat();
    sf.setBlurRadius(s.getName().contains("Background") ? 10.0 : 3.0);
}
```

### ملاحظات حول التوافق

- **الوحدات:** تستخدم Aspose.Words النقاط (1 pt = 1/72 بوصة). إذا كنت تعمل بالمليمترات، قم بالتحويل وفقًا لذلك.  
- **الإصدار:** API المعروضة تعمل مع Aspose.Words for Java 24.9 وما بعده. الإصدارات القديمة قد تستخدم `setBlurRadius(double)` لكنها تفتقر إلى بعض خصائص الظل الحديثة.

---

## الأخطاء الشائعة وكيفية تجنّبها

| المشكلة | السبب | الحل |
|---------|-------|------|
| `NullPointerException` على `shape` | المستند لا يحتوي على أشكال أو الفهرس خارج النطاق | أضف فحصًا للـ null قبل الوصول إلى `ShadowFormat`. |
| الظل غير ظاهر في Word | لون الظل افتراضيًا شفاف أو قيم المسافة تدفعه خارج الصفحة | عيّن `ShadowColor` مرئي (`shadow.setColor(Color.BLACK)`) واحافظ على قيم `DistanceX/Y` معتدلة. |
| نصف قطر التمويه لا يتغيّر | استخدام نسخة قديمة من Aspose.Words تتجاهل الخاصية | حدّث المكتبة إلى أحدث نسخة؛ الخاصية أضيفت في الإصدار 20.5. |
| بطء الأداء على مستندات ضخمة | حفظ المستند بالكامل بعد تعديل كل شكل | اجمع جميع التعديلات ثم استدعِ `save` مرة واحدة. |

---

## الخلاصة

أنت الآن تعرف **كيفية تكوين نصف قطر تمويه الشكل** في مستند Word باستخدام Java وAspose.Words. من تحميل الملف، إلى الحصول على الـ `Shape` المناسب، وتعديل `ShadowFormat`، ثم حفظ التغييرات — كل خطوة موضّحة مع نصائح عملية.  

هذه التقنية لا تقتصر على شكل واحد؛ يمكنك توسيعها لتشمل مستندًا كاملاً، تطبيق مستويات تمويه مختلفة، أو دمجها مع خصائص ظل أخرى مثل **shadow transparency Java**. الخطوات التالية المنطقية هي استكشاف **set blur radius** للصور، تجربة **Java shadow format** على المخططات، أو الغوص أعمق في **Word document shape manipulation** لإنشاء تقارير ديناميكية.

هل لديك سيناريو لم يُغطى هنا؟ اترك تعليقًا أو راجع وثائق Aspose.Words for Java للحصول على تأثيرات ظل متقدمة أخرى. Happy coding!

---

<img src="configure-shape-blur-radius.png" alt="Configure shape blur radius using Aspose.Words Java example" style="max-width:100%;">

---


## ماذا يجب أن تتعلم بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات الموضحة في هذا الدليل. كل مورد يتضمن أمثلة شفرة كاملة مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف أساليب تنفيذ بديلة في مشاريعك.

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Using Document Options and Settings in Aspose.Words for Java](/words/english/java/document-manipulation/using-document-options-and-settings/)
- [How to Convert Word to PDF Using Aspose.Words for Java](/words/english/java/document-converting/using-document-converting/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}