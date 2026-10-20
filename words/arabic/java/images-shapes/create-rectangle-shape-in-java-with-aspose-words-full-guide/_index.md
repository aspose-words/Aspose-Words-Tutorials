---
category: general
date: 2026-07-06
description: إنشاء شكل مستطيل في Java باستخدام Aspose.Words – تعلم كيفية إضافة ظل
  إلى الشكل، وضبط شفافية الشكل، وحفظ المستند كملف PDF.
draft: false
keywords:
- create rectangle shape
- add shadow to shape
- set shape transparency
- save document as pdf
- how to add shadow
language: ar
og_description: إنشاء شكل مستطيل في Java باستخدام Aspose.Words. يوضح هذا الدليل كيفية
  إضافة ظل إلى الشكل، ضبط شفافية الشكل، وحفظ المستند كملف PDF.
og_title: إنشاء شكل مستطيل في جافا – دليل Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-07-06'
  description: Create rectangle shape in Java using Aspose.Words – learn how to add
    shadow to shape, set shape transparency, and save document as PDF.
  headline: Create rectangle shape in Java with Aspose.Words – Full Guide
  type: TechArticle
- description: Create rectangle shape in Java using Aspose.Words – learn how to add
    shadow to shape, set shape transparency, and save document as PDF.
  name: Create rectangle shape in Java with Aspose.Words – Full Guide
  steps:
  - name: 1️⃣ What if I need a larger rectangle?
    text: Just change the width and height parameters in `insertShape`. Remember that
      72 pt = 1 in, so `400.0, 200.0` would give you a 5.5 × 2.8 inch rectangle.
  - name: 2️⃣ Can I use a different color for the shadow?
    text: Absolutely. The `ShadowFormat` class also exposes `setColor(java.awt.Color)`.
      For a subtle gray shadow, try `shadow.setColor(java.awt.Color.DARK_GRAY);`.
  - name: 3️⃣ Does `save document as pdf` work on all platforms?
    text: Yes. Aspose.Words for Java is platform‑agnostic; the same code runs on Windows,
      macOS, and Linux as long as you have a compatible JRE.
  - name: 4️⃣ How do I remove the shadow later?
    text: Call `rect.getShadowFormat().clear();` or set the `Visible` property to
      `false` (`shadow.setVisible(false);`).
  - name: 5️⃣ What about DPI and image quality?
    text: When saving to PDF, Aspose automatically uses 300 DPI for vector graphics
      like shapes, so you get crisp results regardless of zoom level.
  type: HowTo
tags:
- Aspose.Words
- Java
- PDF
- Shape
- Shadow
title: إنشاء شكل مستطيل في جافا باستخدام Aspose.Words – دليل كامل
url: /ar/java/images-shapes/create-rectangle-shape-in-java-with-aspose-words-full-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# إنشاء شكل مستطيل في Java باستخدام Aspose.Words – دليل كامل

هل تساءلت يومًا كيف **إنشاء شكل مستطيل** في Java دون التعامل مع واجهات برمجة رسومية منخفضة المستوى؟ لست وحدك. يحتاج العديد من المطورين إلى طريقة سريعة وموثوقة لإدراج مستطيل في مستند Word، وإعطائه ظلًا خفيفًا، وتعديل شفافيته، ثم تسليم النتيجة كملف PDF.  

في هذا الدرس سنستعرض ذلك خطوة بخطوة، مع كود كامل قابل للتنفيذ. في النهاية ستعرف **كيفية إضافة ظل** إلى شكل، وكيفية **ضبط شفافية الشكل**، وكيفية **حفظ المستند كملف PDF** باستخدام Aspose.Words for Java. لا إطالة، فقط إرشادات عملية يمكنك نسخها ولصقها في مشروعك اليوم.

## ما ستتعلمه

- الإعداد الأدنى المطلوب للعمل مع Aspose.Words في مشروع Java.  
- كيفية **إنشاء شكل مستطيل** برمجيًا.  
- الاستدعاءات الدقيقة اللازمة **لإضافة ظل إلى الشكل** وتعديل الضبابية، الإزاحة، والشفافية.  
- طرق **ضبط شفافية الشكل** بحيث يندمج المستطيل بشكل جميل مع المحتوى المحيط.  
- أبسط طريقة **لحفظ المستند كملف PDF** دون أي خطوات تحويل إضافية.  

إذا كنت مرتاحًا مع أساسيات Java وتملك بيئة بناء Maven أو Gradle، فأنت جاهز للبدء.

## المتطلبات المسبقة

- Java 8 أو أحدث.  
- Aspose.Words for Java 23.x (أو أحدث نسخة متوفرة عند القراءة).  
- بيئة تطوير متكاملة أو أداة بناء سطر أوامر (IntelliJ, Eclipse, Maven, Gradle—اختر ما يناسبك).  

> **نصيحة احترافية:** Aspose يقدم ترخيصًا مؤقتًا مجانيًا للتقييم. احصل عليه من بوابة حسابك وضع ملف `license.xml` في مسار الـ classpath؛ وإلا ستظهر علامة مائية في ملف PDF.

---

## الخطوة 1: **إنشاء شكل مستطيل** باستخدام Aspose.Words

الأول الذي نحتاجه هو مستند `Document` فارغ و`DocumentBuilder`. الـ builder هو العامل الأساسي الذي يسمح لنا بإدراج الأشكال مباشرةً في تدفق المستند.

```java
import com.aspose.words.*;

public class RectangleShadowDemo {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Initialize a new empty Word document
        Document doc = new Document();

        // 2️⃣ Create a builder attached to the document
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 3️⃣ Insert a rectangle shape – 200 points wide, 100 points tall
        Shape rect = builder.insertShape(ShapeType.RECTANGLE, 200.0, 100.0);
        // Optional: give the rectangle a light gray fill so the shadow is visible
        rect.getFillColor().setColor(java.awt.Color.LIGHT_GRAY);
```

**لماذا هذا مهم:** `ShapeType.RECTANGLE` يخبر Aspose أننا نريد مستطيلًا مثاليًا. العرض والارتفاع يُعبَّران بالنقاط (1 pt ≈ 1/72 in)، مما يمنحك تحكمًا دقيقًا في الحجم النهائي.

---

## الخطوة 2: **إضافة ظل إلى الشكل**

الآن بعد أن لدينا مستطيلًا، لنمنحه ظلًا خفيفًا. كائن `ShadowFormat` يوفّر كل ما نحتاجه—نصف قطر الضبابية، إزاحة X/Y، وحتى الشفافية.

```java
        // 4️⃣ Configure the shadow effect
        ShadowFormat shadow = rect.getShadowFormat();
        shadow.setBlur(5.0);          // Softness of the shadow edge
        shadow.setOffsetX(3.0);       // Horizontal shift (points)
        shadow.setOffsetY(3.0);       // Vertical shift (points)
        shadow.setTransparency(0.3); // 30 % transparent – makes it look natural
```

**لماذا هذا مهم:** الظل بدون ضبابية يبدو كخط صلب، وهذا نادرًا ما يرغبه المصممون. استدعاء `setBlur` ينعم الحواف، بينما `setTransparency` يجعل الظل يتلاشى في الخلفية. عدّل هذه القيم لتتناسب مع إرشادات واجهة المستخدم الخاصة بك.

---

## الخطوة 3: **ضبط شفافية الشكل**

أحيانًا تحتاج المستطيل نفسه أن يكون شبه شفاف—ربما لتغطية شعار أو علامة مائية. Aspose يجعل ذلك سطرًا واحدًا.

```java
        // 5️⃣ Make the rectangle partially transparent (optional)
        rect.getFillFormat().setTransparency(0.2); // 20 % transparent fill
```

**لماذا هذا مهم:** الشفافية يمكن أن تكون منقذة عندما تقوم بطبقة الأشكال. لاحظ أن شفافية الظل مستقلة، لذا يمكنك الحصول على شكل خفيف مع ظل أغمق إذا كان ذلك يناسب تصميمك.

---

## الخطوة 4: **حفظ المستند كملف PDF**

تم إنجاز كل العمل البصري؛ الخطوة الأخيرة هي حفظ المستند. Aspose.Words يمكنه الكتابة مباشرةً إلى PDF، مما يلغي الحاجة إلى مكتبة تحويل منفصلة.

```java
        // 6️⃣ Persist the document as a PDF file
        String outPath = "output/RectangleWithShadow.pdf";
        doc.save(outPath, SaveFormat.PDF);
        System.out.println("PDF saved to: " + outPath);
    }
}
```

**لماذا هذا مهم:** بتحديد `SaveFormat.PDF`، تتولى المكتبة تضمين الخطوط، ضغط الصور، والامتثال لـ PDF/A في الخلفية. الملف الناتج جاهز للتوزيع، الطباعة، أو الأرشفة.

---

## مثال كامل يعمل

بتجميع كل ما سبق، إليك الفئة الكاملة الجاهزة للتنفيذ. انسخ‑الصق، عدل مسار المخرجات، وستحصل على PDF يحتوي على مستطيل يلقي ظلًا واقعيًا.

```java
import com.aspose.words.*;

public class RectangleShadowDemo {
    public static void main(String[] args) throws Exception {
        // Initialize document and builder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert rectangle shape (200×100 points)
        Shape rect = builder.insertShape(ShapeType.RECTANGLE, 200.0, 100.0);
        rect.getFillColor().setColor(java.awt.Color.LIGHT_GRAY);

        // Add shadow effect
        ShadowFormat shadow = rect.getShadowFormat();
        shadow.setBlur(5.0);
        shadow.setOffsetX(3.0);
        shadow.setOffsetY(3.0);
        shadow.setTransparency(0.3);

        // Optional: make the rectangle itself partially transparent
        rect.getFillFormat().setTransparency(0.2);

        // Save as PDF
        String outPath = "output/RectangleWithShadow.pdf";
        doc.save(outPath, SaveFormat.PDF);
        System.out.println("PDF saved to: " + outPath);
    }
}
```

**الناتج المتوقع:** عند فتح `RectangleWithShadow.pdf`، سترى مستطيلًا رماديًا فاتحًا مركَّزًا في الصفحة الأولى، مرفوعًا برفق عن الصفحة بظل ناعم شبه شفاف. الشكل نفسه شفاف بنسبة 20 %، مما يسمح لأي نص أساسي (إذا أضفته) بالظهور من خلاله.

---

## أسئلة شائعة وحالات حافة

### 1️⃣ ماذا لو احتجت إلى مستطيل أكبر؟

فقط غيّر قيم العرض والارتفاع في `insertShape`. تذكّر أن 72 pt = 1 in، لذا `400.0, 200.0` سيعطيك مستطيلًا بحجم 5.5 × 2.8 إنش.

### 2️⃣ هل يمكنني استخدام لون مختلف للظل؟

بالطبع. فئة `ShadowFormat` تتيح أيضًا `setColor(java.awt.Color)`. للحصول على ظل رمادي خفيف، جرّب `shadow.setColor(java.awt.Color.DARK_GRAY);`.

### 3️⃣ هل يعمل `save document as pdf` على جميع المنصات؟

نعم. Aspose.Words for Java مستقل عن المنصة؛ نفس الكود يعمل على Windows، macOS، وLinux طالما لديك JRE متوافق.

### 4️⃣ كيف يمكنني إزالة الظل لاحقًا؟

استدعِ `rect.getShadowFormat().clear();` أو عيّن خاصية `Visible` إلى `false` (`shadow.setVisible(false);`).

### 5️⃣ ماذا عن DPI وجودة الصورة؟

عند الحفظ إلى PDF، يستخدم Aspose تلقائيًا 300 DPI للرسومات المتجهة مثل الأشكال، لذا ستحصل على نتائج واضحة بغض النظر عن مستوى التكبير.

---

## نصائح احترافية وأفضل الممارسات

- **Batch processing:** إذا كنت بحاجة إلى توليد العشرات من ملفات PDF، أعد استخدام نسخة واحدة من `Document` وامسح أقسامها فقط بين كل جولة لتقليل ضغط الـ GC.  
- **Licensing:** ضع `License license = new License(); license.setLicense("license.xml");` في بداية `main` لتجنب علامة التقييم المائية.  
- **Performance:** رسم الظل رخيص للأشكال البسيطة، لكن المسارات المعقدة قد تبطئ توليد PDF. قم بالتحليل إذا كنت تعالج دفعات كبيرة.  
- **Testing:** استخدم `Document.save(..., SaveFormat.DOCX)` أولًا للتحقق من ظهور الشكل بشكل صحيح في Word قبل التحويل إلى PDF.

---

## الخلاصة

أنت الآن تعرف كيف **إنشاء شكل مستطيل** في Java باستخدام Aspose.Words، **إضافة ظل إلى الشكل**، **ضبط شفافية الشكل**، وأخيرًا **حفظ المستند كملف PDF**. الكود مستقل، يعمل مع أحدث مكتبة Aspose، ويظهر الاستدعاءات الأساسية للـ API التي ستحتاجها في معظم سيناريوهات أتمتة المستندات.

هل أنت مستعد للتحدي التالي؟ جرّب استبدال المستطيل ببيضاوي، جرب تعبئات متدرجة، أو استكشف كيفية **إضافة ظل** إلى إطارات النص. نفس المبادئ تنطبق، وواجهة Aspose API تجعل الأمر سهلًا كقطعة من الكعك.

برمجة سعيدة، ولا تتردد في ترك تعليق إذا واجهت أي صعوبة!

## ما الذي يجب أن تتعلمه بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات الموضحة في هذا الدليل. كل مصدر يتضمن أمثلة كود كاملة مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف نهج تنفيذ بديلة في مشاريعك الخاصة.

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [How to save document as pdf with Aspose.Words for Java](/words/english/java/document-loading-and-saving/saving-documents-as-pdf/)
- [How to create form fields and add content using DocumentBuilder in Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}