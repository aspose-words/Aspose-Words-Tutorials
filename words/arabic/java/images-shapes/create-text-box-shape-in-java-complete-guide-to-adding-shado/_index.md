---
category: general
date: 2026-05-30
description: أنشئ شكل صندوق نص في جافا وتعلم كيفية إضافة الظل، وتعيين لون الظل، وتحديد
  مسافة الظل. اتبع هذا الدليل خطوةً بخطوة للحصول على مستند مصقول.
draft: false
keywords:
- create text box shape
- set shadow color
- how to add shadow
- set shadow distance
- add shadow textbox
language: ar
og_description: إنشاء شكل صندوق نص في Java ورؤية كيفية إضافة الظل، وتعيين لون الظل
  والمسافة فورًا. دليل عملي لـ Aspose.Words.
og_title: إنشاء شكل صندوق نص في جافا – دليل الظل الكامل
schemas:
- author: Aspose
  dateModified: '2026-05-30'
  description: Create text box shape in Java and learn how to add shadow, set shadow
    color, and set shadow distance. Follow this step‑by‑step tutorial for a polished
    document.
  headline: Create Text Box Shape in Java – Complete Guide to Adding Shadows
  type: TechArticle
- description: Create text box shape in Java and learn how to add shadow, set shadow
    color, and set shadow distance. Follow this step‑by‑step tutorial for a polished
    document.
  name: Create Text Box Shape in Java – Complete Guide to Adding Shadows
  steps:
  - name: Why These Values?
    text: '- **BlurRadius** of `4.0` gives a gentle feathered edge without looking
      fuzzy. - **Distance** of `5.0` offsets the shadow enough to be noticeable but
      not detached. - **Transparency** of `0.35` keeps the shadow from overwhelming
      the text. - **Color** `GRAY` works well on both light and dark backgroun'
  - name: 1️⃣ Can I apply a shadow to a shape that already contains images?
    text: Absolutely. The `ShadowFormat` works on any `Shape`, whether it’s a text
      box, picture, or auto‑shape. Just retrieve the shape’s `ShadowFormat` and set
      the desired properties.
  - name: 2️⃣ What if I need multiple shadows (e.g., inner and outer)?
    text: Aspose.Words currently supports a single drop shadow per shape. For more
      complex effects you might need to duplicate the shape, offset it, and adjust
      opacity manually.
  - name: 3️⃣ Does the shadow respect the document’s theme colors?
    text: When you use `Color.getThemeColor(ThemeColor.ACCENT_1)`, the shadow will
      follow the active theme. This is handy for corporate branding where you don’t
      want hard‑coded RGB values.
  - name: 4️⃣ How does **add shadow textbox** differ from adding a picture shadow?
    text: The API is identical; the only distinction is the shape type. A textbox
      is a `ShapeType.TEXT_BOX`, while a picture is `ShapeType.IMAGE`. Both expose
      `ShadowFormat`.
  - name: 5️⃣ I’m targeting PDF output—will the shadow survive the conversion?
    text: Yes. Aspose.Words renders shadows when saving to PDF, provided you’re using
      a recent version (23.12+). Just call `doc.save("output.pdf")` instead of DOCX.
  - name: Wrap‑Up
    text: We’ve just walked through a complete, end‑to‑end example that shows you
      how
  type: HowTo
tags:
- Java
- Aspose.Words
- Document Generation
title: إنشاء شكل صندوق نص في جافا – دليل شامل لإضافة الظلال
url: /ar/java/images-shapes/create-text-box-shape-in-java-complete-guide-to-adding-shado/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# إنشاء شكل صندوق نص في Java – دليل كامل لإضافة الظلال

هل تساءلت يومًا كيف **تنشئ شكل صندوق نص** في Java وتضيف له ظلًا أنيقًا؟ لست وحدك. سواء كنت تُنشئ تقارير، أو تصمم منشورات تسويقية، أو مجرد تجربة تنسيق المستندات، فإن صندوق النص المظلل يمكن أن يجعل مخرجاتك تبدو أكثر احترافية.

في هذا الدرس سنستعرض العملية بالكامل — من إنشاء الشكل إلى ضبط الظل — حتى تتمكن من **إضافة صندوق نص بظل** بثقة. في النهاية ستعرف بالضبط **كيفية إضافة الظل**، وكيفية **تعيين لون الظل**، وكيفية **تعيين مسافة الظل** باستخدام Aspose.Words for Java.

## ما ستتعلمه

- الأدوات المطلوبة (Java 17+، Aspose.Words for Java، بيئة تطوير)
- كيفية **إنشاء شكل صندوق نص** باستخدام `DocumentBuilder`
- كيفية **تعيين لون الظل**، **تعيين مسافة الظل**، وتعديل الضبابية أو الشفافية
- مثال كامل قابل للتنفيذ يمكنك نسخه‑ولصقه
- نصائح لاستكشاف الأخطاء الشائعة وتوسيع التأثير

> **نصيحة احترافية:** إذا لم تقم بتثبيت Aspose.Words بعد، احصل على أحدث ملف JAR من مستودع Maven الرسمي — هذا الدرس يستهدف الإصدار 23.12، الذي يدعم جميع واجهات برمجة الظلال التي سنستخدمها.

---

![كود Java ينشئ شكل صندوق نص مع ظل](https://example.com/images/shadow-textbox-java.png "كود Java ينشئ شكل صندوق نص مع ظل")

*(نص بديل الصورة: “كود Java ينشئ شكل صندوق نص مع ظل” – يتضمن الكلمة المفتاحية الأساسية)*

## الخطوة 1: إعداد المشروع واستيراد الاعتمادات

قبل أن نتمكن من **إنشاء شكل صندوق نص**، نحتاج إلى مشروع Java يربط Aspose.Words. إذا كنت تستخدم Maven، أضف ما يلي إلى ملف `pom.xml` الخاص بك:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.12</version>
</dependency>
```

إذا كنت تفضّل Gradle، فإن ما يعادله هو:

```gradle
implementation 'com.aspose:aspose-words:23.12'
```

بمجرد أن تكون المكتبة على مسار الفئة (classpath)، استورد الفئات التي سنحتاجها:

```java
import com.aspose.words.*;
import java.awt.Color;
```

هذا كل شيء — بيئتك جاهزة لـ **إنشاء شكل صندوق نص** والبدء في تنسيقه.

## الخطوة 2: إنشاء مستند فارغ ومُنشئ (Builder)

القطعة الأولى من اللغز هي كائن `Document` جديد. فكر فيه كقماش نظيف. ثم نرفق `DocumentBuilder` لبدء إدراج المحتوى.

```java
// Step 2: Initialize a new document and builder
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

لاحظ أن التعليق يذكر “initialize”. في الكود اليومي قد ترى “create document”، لكننا سنقوم بـ **إنشاء شكل صندوق نص** لاحقًا، لذا حافظ على هذا التمييز واضحًا.

## الخطوة 3: **إنشاء شكل صندوق نص** وإدراج النص

الآن يأتي الإجراء الأساسي: نحن فعليًا **ننشئ شكل صندوق نص**. طريقة `insertShape` تأخذ `ShapeType`، العرض، والارتفاع. بعد وضع الشكل، يمكننا كتابة النص مباشرةً داخله.

```java
// Step 3: Insert a text box shape where the shadow will be applied
Shape textBox = builder.insertShape(ShapeType.TEXT_BOX, 300.0, 80.0);

// Write some placeholder text inside the box
builder.moveTo(textBox.getFirstParagraph());
builder.writeln("Shadowed TextBox Example");
```

بعض النقاط التي يجب ملاحظتها:

- `ShapeType.TEXT_BOX` يخبر Aspose أننا نريد حاوية يمكنها احتواء فقرات.
- الأبعاد (`300 × 80`) بوحدات النقاط؛ عدّلها لتناسب تخطيطك.
- بنقل مؤشر الـ builder إلى الفقرة الأولى داخل الشكل، نضمن ظهور النص *داخل* الصندوق.

## الخطوة 4: **كيفية إضافة الظل** – ضبط `ShadowFormat`

تُظهر Aspose.Words كائن `ShadowFormat` على كل شكل. هنا نجيب على سؤال **كيفية إضافة الظل**. يمكنك التحكم في الضبابية، المسافة، الشفافية، وبالطبع اللون.

```java
// Step 4: Access the shadow format and configure it
ShadowFormat shadow = textBox.getShadowFormat();

// Set a subtle blur radius
shadow.setBlurRadius(4.0);

// Define how far the shadow is offset from the shape
shadow.setDistance(5.0);               // This is the "set shadow distance" part

// Make the shadow semi‑transparent
shadow.setTransparency(0.35);

// Choose a color – here's where we **set shadow color**
shadow.setColor(Color.GRAY);
```

### لماذا هذه القيم؟

- **BlurRadius** بقيمة `4.0` يعطي حافة ناعمة دون أن تبدو ضبابية.
- **Distance** بقيمة `5.0` يبعد الظل بما يكفي ليكون ملحوظًا لكن ليس منفصلًا.
- **Transparency** بقيمة `0.35` تحافظ على عدم غمر الظل للنص.
- **Color** `GRAY` يعمل جيدًا على الخلفيات الفاتحة والداكنة؛ يمكنك استبداله بـ `Color.RED` أو أي قيمة RGB مخصصة.

لا تتردد في التجربة — تغيير `setShadowDistance` إلى رقم أكبر سيبعد الظل أكثر، بينما الضبابية الأصغر تجعل الظل يبدو أكثر حدة.

## الخطوة 5: حفظ المستند

بعد تنسيق الشكل، الخطوة الأخيرة هي كتابة الملف إلى القرص. تدعم Aspose.Words صيغًا متعددة؛ هنا سنستخدم DOCX لأقصى توافق.

```java
// Step 5: Persist the document
String outputPath = "output/ShadowedTextboxDemo.docx";
doc.save(outputPath);
System.out.println("Document saved to " + outputPath);
```

تشغيل البرنامج سيولد ملف Word يحتوي على صندوق نص مع ظل مُصمم بشكل جميل. افتحه في Microsoft Word أو LibreOffice أو أي عارض يدعم DOCX، وسترى التأثير فورًا.

## مثال كامل يعمل

بتجميع كل ما سبق، إليك فئة مستقلة يمكنك تجميعها وتشغيلها:

```java
import com.aspose.words.*;
import java.awt.Color;

public class ShadowEffectDemo {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Create a new blank document and a builder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Insert a text box shape (the core of our tutorial)
        Shape textBox = builder.insertShape(ShapeType.TEXT_BOX, 300.0, 80.0);
        builder.moveTo(textBox.getFirstParagraph());
        builder.writeln("Shadowed TextBox Example");

        // 3️⃣ Configure shadow – this answers "how to add shadow"
        ShadowFormat shadow = textBox.getShadowFormat();
        shadow.setBlurRadius(4.0);
        shadow.setDistance(5.0);               // set shadow distance
        shadow.setTransparency(0.35);
        shadow.setColor(Color.GRAY);           // set shadow color

        // 4️⃣ Save the result
        String out = "output/ShadowedTextboxDemo.docx";
        doc.save(out);
        System.out.println("Document saved to " + out);
    }
}
```

**الناتج المتوقع:** عند فتح `ShadowedTextboxDemo.docx`، ستظهر صندوق نص واحد مركزي في الصفحة الأولى، يحتوي على العبارة “Shadowed TextBox Example”. سيظهر ظل رمادي ناعم مائل إلى أسفل‑يمين، مما يعطي انطباع العمق.

---

## أسئلة شائعة وحالات خاصة

### 1️⃣ هل يمكنني تطبيق ظل على شكل يحتوي بالفعل على صور؟

بالطبع. يعمل `ShadowFormat` على أي `Shape`، سواء كان صندوق نص، صورة، أو شكل تلقائي. ما عليك سوى جلب `ShadowFormat` الخاص بالشكل وتعيين الخصائص المطلوبة.

### 2️⃣ ماذا لو أحتاج إلى ظلال متعددة (مثلاً داخلية وخارجية)؟

حاليًا تدعم Aspose.Words ظلًا واحدًا فقط لكل شكل. للحصول على تأثيرات أكثر تعقيدًا قد تحتاج إلى تكرار الشكل، إزاحته، وضبط الشفافية يدويًا.

### 3️⃣ هل يحترم الظل ألوان سمة المستند؟

عند استخدام `Color.getThemeColor(ThemeColor.ACCENT_1)`، سيتبع الظل السمة النشطة. هذا مفيد للعلامات التجارية حيث لا تريد قيم RGB ثابتة.

### 4️⃣ كيف يختلف **إضافة ظل لصندوق النص** عن إضافة ظل للصورة؟

الواجهة البرمجية هي نفسها؛ الفرق الوحيد هو نوع الشكل. صندوق النص هو `ShapeType.TEXT_BOX`، بينما الصورة هي `ShapeType.IMAGE`. كلاهما يتيح الوصول إلى `ShadowFormat`.

### 5️⃣ أستهدف إخراج PDF — هل سيبقى الظل بعد التحويل؟

نعم. تقوم Aspose.Words برسم الظلال عند الحفظ إلى PDF، بشرط استخدام نسخة حديثة (23.12+). ما عليك سوى استدعاء `doc.save("output.pdf")` بدلاً من DOCX.

---

## نصائح وحيل من الميدان

- **نصيحة احترافية:** فعّل `doc.getCompatibilityOptions().optimizeFor(CompatibilityOptions.OPTIMIZE_FOR_MS_WORD_2016);` إذا لاحظت اختلافات طفيفة في العرض بين Word وPDF.
- **احذر من:** ضبط `distance` إلى `0` سيجعل الظل يجلس مباشرة خلف الشكل، مما يبدو مسطحًا غالبًا. قيمة صغيرة غير صفرية هي الأفضل عادة.
- **ملاحظة الأداء:** إضافة الظل يضيف عبءً بسيطًا. إذا كنت تُولّد آلاف المستندات، اجمع إعدادات الظل فقط للأشكال القليلة التي تحتاجه.

---

## الخطوات التالية

الآن بعد أن عرفت كيفية **إنشاء شكل صندوق نص**، **تعيين لون الظل**، **تعيين مسافة الظل**، و**إضافة ظل لصندوق النص**، فكر في استكشاف المواضيع ذات الصلة:

- **إضافة تعبئة متدرجة** إلى صندوق النص لمظهر أغنى.
- **إدراج جداول** داخل صندوق نص مظلل للبيانات المنظمة.
- **تطبيق تأثيرات نص** (حد، توهج) جنبًا إلى جنب مع الظلال لتحقيق أقصى تأثير.
- **أتمتة المعالجة الدفعية** لعدة مستندات بنمط ظل موحد.

كل من هذه المواضيع يبني على الأساس الذي وضعناه، مما يتيح لك إنتاج مستندات مصقولة ومتسقة مع العلامة التجارية برمجيًا.

---

### الخلاصة

لقد استعرضنا مثالًا كاملاً من البداية إلى النهاية يوضح لك كيفية

## ماذا يجب أن تتعلمه بعد ذلك؟

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)
- [Create Blank Word Document with Shadowed Rectangle Shape – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}