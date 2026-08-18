---
category: general
date: 2026-07-03
description: إنشاء شكل مستطيل في جافا وتعلم كيفية إضافة ظل إلى الشكل، وتطبيق تأثير
  الظل، وضبط شفافية الشكل، وإنشاء مستند فارغ بسرعة.
draft: false
keywords:
- create rectangle shape
- add shadow to shape
- apply shadow effect
- set shape transparency
- create blank document
language: ar
og_description: إنشاء شكل مستطيل في جافا مع الظل والشفافية ومستند فارغ. اتبع هذا الدليل
  لإتقان التعامل مع الأشكال.
og_title: إنشاء شكل مستطيل في جافا – دليل برمجة كامل
schemas:
- author: Aspose
  dateModified: '2026-07-03'
  description: Create rectangle shape in Java and learn how to add shadow to shape,
    apply shadow effect, set shape transparency, and create blank document quickly.
  headline: Create rectangle shape in Java – Complete Step‑by‑Step Guide
  type: TechArticle
- description: Create rectangle shape in Java and learn how to add shadow to shape,
    apply shadow effect, set shape transparency, and create blank document quickly.
  name: Create rectangle shape in Java – Complete Step‑by‑Step Guide
  steps:
  - name: What if I want a different shadow color?
    text: 'Simply change the `setColor` call:'
  - name: Can I apply the same shadow to multiple shapes?
    text: 'Yes. Create one `ShadowEffect` instance, configure it, then reuse it:'
  - name: How do I change the shadow blur dynamically?
    text: Expose a UI slider that maps to `setBlurRadius`. Values between `2` and
      `12` are typical; larger numbers produce a “glow” rather than a crisp shadow.
  - name: What if I need the shape to float rather than be inline?
    text: 'Swap the wrap type:'
  type: HowTo
tags:
- Java
- Aspose.Words
- Document Automation
title: إنشاء شكل مستطيل في جافا – دليل خطوة بخطوة كامل
url: /ar/java/images-shapes/create-rectangle-shape-in-java-complete-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# إنشاء شكل مستطيل في Java – دليل كامل خطوة بخطوة

هل تساءلت يومًا كيف **تنشئ شكل مستطيل** في مستند Word باستخدام Java؟ لست وحدك—غالبًا ما يحتاج المطورون إلى طريقة سريعة لإضافة رسومات هندسية، ثم إعطائها ظلًا خفيفًا لتبدو التخطيط أكثر صقلًا. في هذا الدرس سنستعرض العملية بالكامل: من إنشاء **مستند فارغ** إلى **إضافة ظل إلى الشكل**، **تطبيق تأثير الظل**، وحتى **تعيين شفافية الشكل** للحصول على مظهر احترافي.

المقتطف البرمجي أدناه مثال كامل يمكنك نسخه‑ولصقه في مشروعك. لا حاجة إلى وثائق خارجية—فقط اتبع الخطوات، افهم “السبب”، وستتمكن من توليد مستطيلات ذات ظل في ثوانٍ.

## ما ستتعلمه

- كيفية **إنشاء شكل مستطيل** برمجيًا باستخدام Aspose.Words for Java.
- الاستدعاءات الدقيقة اللازمة **لإضافة ظل إلى الشكل** وتكوين خصائصه البصرية.
- طرق **تطبيق تأثير الظل** وتعديل معلمات مثل الإزاحة، نصف قطر الضبابية، واللون.
- تقنيات **تعيين شفافية الشكل** للحصول على مظهر أكثر نعومة.
- كيفية **إنشاء مستند فارغ**، إدراج الشكل، وحفظ النتيجة.

> **نصيحة محترف:** جميع هذه الإجراءات تُجرى على نسخة `Document` واحدة، مما يعني أنه يمكنك ربطها معًا دون القلق بشأن عمليات الإدخال/الإخراج الوسيطة.

## المتطلبات المسبقة

قبل أن نبدأ، تأكد من وجود ما يلي:

- Java 17 (أو أي JDK حديث) مثبت.
- مكتبة Aspose.Words for Java مضافة إلى مشروعك (إحداثيات Maven: `com.aspose:aspose-words:23.12`).
- بيئة تطوير Java أو محرر نصوص بسيط—لا شيء معقد، مجرد مكان لتجميع وتشغيل الكود.

إذا كان أيٌ من هذه غير متوفر، احصل على JDK من Oracle وأضف تبعية Aspose عبر Maven أو Gradle. بمجرد إعداده، ستكون جاهزًا للانطلاق.

## الخطوة 1: **إنشاء مستند فارغ** – القماش لكل شيء

أول شيء تحتاجه هو كائن `Document` فارغ. فكر فيه كصفحة بيضاء؛ بدونها لا مكان لوضع المستطيل.

```java
// Step 1: Create a new blank document
Document document = new Document();
```

لماذا نبدأ بمستند فارغ؟ لأن كل شكل يعيش داخل `Section`، و`Document` المُنشأ حديثًا يحتوي بالفعل على قسم افتراضي مع جسم جاهز لاستقبال العقد. تخطي هذه الخطوة يجبرك على إنشاء أقسام يدويًا لاحقًا، مما يضيف تعقيدًا غير ضروري.

## الخطوة 2: **إنشاء شكل مستطيل** وتحديد حجمه

الآن بعد أن لدينا القماش، لن **ننشئ شكل مستطيل**. فئة `Shape` تأخذ مرجع المستند و`ShapeType`. هنا نختار `RECTANGLE` ونحدد العرض/الارتفاع بالنقاط (1 pt ≈ 1/72 inch).

```java
// Step 2: Insert a rectangle shape and define its size and layout
Shape rectangleShape = new Shape(document, ShapeType.RECTANGLE);
rectangleShape.setWidth(200);   // 200 pt ≈ 2.78 inches
rectangleShape.setHeight(100);  // 100 pt ≈ 1.39 inches
rectangleShape.setWrapType(WrapType.INLINE);
```

لماذا نعيّن `WrapType.INLINE`؟ يجعل الالتفاف داخل السطر الشكل يتصرف كحرف في الفقرة، مما يضمن تحركه مع النص المحيط. إذا كنت تحتاج سلوكًا عائمًا، غيّر إلى `WrapType.SQUARE` أو `WrapType.TOP_BOTTOM`.

## الخطوة 3: **تطبيق تأثير الظل** – إعطاء المستطيل عمقًا

المستطيل المسطح يبدو… مسطحًا. إضافة ظل يجعله يبرز. سن **نطبق تأثير الظل** بإنشاء كائن `ShadowEffect`، ثم تعديل خصائصه البصرية.

```java
// Step 3: Create a shadow effect and configure its visual properties
ShadowEffect shadowEffect = new ShadowEffect();
shadowEffect.setColor(Color.getGray(0.5));   // medium gray
shadowEffect.setOffsetX(5);                  // horizontal offset (points)
shadowEffect.setOffsetY(5);                  // vertical offset (points)
shadowEffect.setBlurRadius(8);               // softness of the shadow
shadowEffect.setTransparency(0.3);           // 30 % transparent
```

نوضح ذلك قليلاً:

- **اللون** – `Color.getGray(0.5)` ينتج رمادي بنسبة 50 %، وهو محايد ويعمل على معظم الخلفيات.
- **OffsetX/Y** – القيم الموجبة تدفع الظل إلى اليمين والأسفل؛ القيم السالبة تحركه إلى اليسار/الأعلى.
- **BlurRadius** – القيم الأكبر تُنتج ظلًا أكثر نعومة وانتشارًا.
- **Transparency** – تتراوح بين `0` (معتم) إلى `1` (شفاف تمامًا). اخترنا `0.3` لتأثير خفيف.

## الخطوة 4: **إضافة الظل إلى الشكل** – ربط التأثير

إنشاء التأثير وحده غير كافٍ؛ يجب **إضافة الظل إلى الشكل** عن طريق إسناد كائن `ShadowEffect` إلى المستطيل.

```java
// Step 4: Apply the shadow effect to the rectangle shape
rectangleShape.setShadowEffect(shadowEffect);
```

خلف الكواليس، هذه الدعوة تُحدّث العلامة الداخلية OpenXML (`<w:shdw>`) التي يستخدمها Word لتصوير الظلال. إذا فحصت ملف `.docx` المحفوظ، ستجد عنصر `<w:effect>` مُملأ بالمعلمات التي عيّناها.

## الخطوة 5: **تعيين شفافية الشكل** – اختياري لكن مفيد غالبًا

أحيانًا تريد أن يكون المستطيل نفسه شبه شفاف، بحيث يظهر النص الخلفي من خلاله. فئة `Shape` تُتيح `setFillColor` و`setFillTransparency`. إليك مثال سريع يجعل المستطيل شفافًا بنسبة 40 %:

```java
// Optional: make the rectangle partially transparent
rectangleShape.setFillColor(Color.getWhite());
rectangleShape.setFillTransparency(0.4); // 40 % transparent
```

لماذا قد تقوم بذلك؟ تخيل علامة مائية أو ملاحظة مميزة حيث يجب أن يبقى المحتوى الأساسي مقروءًا. عدّل قيمة الشفافية لتناسب لغة التصميم الخاصة بك.

## الخطوة 6: إدراج الشكل في المستند

لقد بنينا المستطيل، أضفنا الظل، (واختياريًا) عيّنّا شفافيته. الخطوة الأخيرة هي **إضافة الشكل إلى القسم الأول من المستند**.

```java
// Step 5: Add the shape to the first section of the document
document.getFirstSection().getBody().appendChild(rectangleShape);
```

إضافة الشكل إلى الجسم يضعه في نهاية الفقرة الأولى. إذا كنت تحتاج نقطة إدراج محددة، استخرج `Paragraph` المستهدف واستخدم `insertBefore` أو `insertAfter`.

## الخطوة 7: حفظ المستند – شاهد النتيجة

كل هذا العمل يختتم بدعوة `save` واحدة. اختر مسارًا يناسب بيئتك.

```java
// Step 6: Save the document with the shadowed shape
document.save("YOUR_DIRECTORY/ShadowShape.docx");
```

افتح الملف الناتج `ShadowShape.docx` في Microsoft Word أو LibreOffice، وسترى مستطيلًا واضحًا مع ظل رمادي خفيف، شفافًا قليلًا إذا نفذت الخطوة الاختيارية. الشكل البصري يطابق المعلمات التي عرّفناها برمجيًا.

---

![إنشاء شكل مستطيل بظل في مستند Word](https://example.com/images/rectangle-shadow.png "إنشاء شكل مستطيل بظل")

*نص بديل للصورة:* **إنشاء شكل مستطيل بظل** – تمثيل بصري للنتيجة النهائية.

## أسئلة شائعة وحالات خاصة

### ماذا لو أردت لون ظل مختلف؟

ما عليك سوى تغيير استدعاء `setColor`:

```java
shadowEffect.setColor(Color.getRed()); // bright red shadow
```

تذكّر أن الظلال الزاهية جدًا قد تبدو غير احترافية؛ النغمات الهادئة عادةً ما تكون الأفضل.

### هل يمكنني تطبيق نفس الظل على عدة أشكال؟

نعم. أنشئ كائن `ShadowEffect` واحد، اضبطه، ثم أعد استخدامه:

```java
Shape circle = new Shape(document, ShapeType.OVAL);
circle.setShadowEffect(shadowEffect); // same effect as rectangle
```

تجنّب تعديل `ShadowEffect` بعد ربطه بأشكال أخرى، إلا إذا كنت تنوي تحديثها جميعًا.

### كيف أغيّر ضبابية الظل بصورة ديناميكية؟

وفر شريط تمرير UI يربط إلى `setBlurRadius`. القيم بين `2` و `12` شائعة؛ القيم الأكبر تنتج “توهج” بدلًا من ظل حاد.

### ماذا لو احتجت الشكل أن يكون عائمًا بدلاً من أن يكون داخل السطر؟

بدّل نوع الالتفاف:

```java
rectangleShape.setWrapType(WrapType.SQUARE);
rectangleShape.setRelativeHorizontalPosition(RelativeHorizontalPosition.PAGE);
rectangleShape.setHorizontalAlignment(HorizontalAlignment.CENTER);
```

الأشكال العائمة تمنحك حرية تخطيط أكبر لكنها تتطلب منطق تموضع إضافي.

## مثال عملي كامل

فيما يلي البرنامج الكامل جاهز للنسخ‑واللصق والذي يدمج جميع الخطوات التي ناقشناها. شغّله كتطبيق Java عادي.

```java
import com.aspose.words.*;

public class ShadowRectangleDemo {
    public static void main(String[] args) throws Exception {
        // 1. Create a blank document
        Document document = new Document();

        // 2. Build the rectangle shape
        Shape rectangleShape = new Shape(document, ShapeType.RECTANGLE);
        rectangleShape.setWidth(200);
        rectangleShape.setHeight(100);
        rectangleShape.setWrapType(WrapType.INLINE);

        // 3. Configure shadow effect
        ShadowEffect shadowEffect = new ShadowEffect();
        shadowEffect.setColor(Color.getGray(0.5));
        shadowEffect.setOffsetX(5);
        shadowEffect.setOffsetY(5);
        shadowEffect.setBlurRadius(8);
        shadowEffect.setTransparency(0.3);

        // 4. Apply shadow to the rectangle
        rectangleShape.setShadowEffect(shadowEffect);

        // 5. (Optional) Make rectangle semi‑transparent
        rectangleShape.setFillColor(Color.getWhite());
        rectangleShape.setFillTransparency(0.4);

        // 6. Insert shape into the document
        document.getFirstSection().getBody().appendChild(rectangleShape);

        // 7. Save the file
        document.save("ShadowShape.docx");
    }
}
```

**الناتج المتوقع:** عند فتح `ShadowShape.docx`، ستلاحظ مستطيلًا أبيض، 200 × 100 pt، مركّزًا في الفقرة الأولى، مع ظل رمادي متوسط الإزاحة بمقدار 5 pt، وضبابية نصف قطرها 8، وشفافية 30 %. المستطيل نفسه شفاف بنسبة 40 %، مما يسمح لأي نص أساسي بالظهور من خلاله.

## الخلاصة

لقد تعلمنا الآن **إنشاء شكل مستطيل** من الصفر، **إضافة ظل إلى الشكل**، **تطبيق تأثير الظل**، وحتى **تعيين شفافية الشكل**—كل ذلك مع **إنشاء مستند فارغ** كأساس. النهج بسيط، يعتمد على API السلس لـ Aspose.Words، ويمكن توسيعه إلى دوائر، نجوم، أو مضلعات مخصصة.

ما الخطوة التالية في خارطة طريقك؟ جرّب استبدال `ShapeType.RECTANGLE` بـ `ShapeType.OVAL` لتوليد دوائر ذات ظل، أو جرب تعبئات تدرجية لتجربة إبداعية أخرى.

## ماذا يجب أن تتعلمه بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات التي تم توضيحها في هذا الدليل. كل مورد يتضمن أمثلة كود كاملة مع شروحات خطوة‑بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف أساليب تنفيذ بديلة في مشاريعك.

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Create Blank Word Document with Shadowed Rectangle Shape – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}