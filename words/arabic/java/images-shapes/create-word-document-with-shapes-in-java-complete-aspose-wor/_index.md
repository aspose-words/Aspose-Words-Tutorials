---
category: general
date: 2026-07-29
description: إنشاء مستند Word في Java باستخدام Aspose.Words. تعلم كيفية إدراج شكل
  مستطيل، تجميع الأشكال في Word، وحفظ المستند كملف docx بسرعة.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document
- insert rectangle shape
- group shapes in word
- save document as docx
- add shapes to word
language: ar
lastmod: 2026-07-29
og_description: إنشاء مستند Word في Java باستخدام Aspose.Words. إدراج شكل مستطيل،
  تجميع الأشكال في Word، وحفظ المستند كملف docx في دقائق.
og_image_alt: Screenshot showing how to create word document with grouped shapes using
  Java
og_title: إنشاء مستند Word مع أشكال – دليل Aspose.Words للغة Java
schemas:
- author: Aspose
  dateModified: '2026-07-29'
  description: Create word document in Java using Aspose.Words. Learn to insert rectangle
    shape, group shapes in Word, and save document as docx quickly.
  headline: Create Word Document with Shapes in Java – Complete Aspose.Words Guide
  type: TechArticle
- description: Create word document in Java using Aspose.Words. Learn to insert rectangle
    shape, group shapes in Word, and save document as docx quickly.
  name: Create Word Document with Shapes in Java – Complete Aspose.Words Guide
  steps:
  - name: '## Create Word Document with Shapes Using Aspose.Words'
    text: The first thing you need is an empty Word file to work with. Aspose.Words
      makes this a one‑liner.
  - name: '## Insert Rectangle Shape and Other Shapes'
    text: Now we’ll add a blue rectangle and a green ellipse. The rectangle demonstrates
      the **insert rectangle shape** keyword, while the ellipse shows that you can
      mix shape types freely.
  - name: '## Group Shapes in Word for Easy Manipulation'
    text: Having two separate objects is fine, but often you want to move them together.
      That’s where **group shapes in word** shines.
  - name: '## Save Document as DOCX and Verify Output'
    text: Finally, we persist the file. This step fulfills the **save document as
      docx** requirement.
  - name: '## Full Working Example and Common Pitfalls'
    text: Below is the complete, ready‑to‑run Java class. Copy‑paste it into your
      project, adjust the output folder, and hit *Run*.
  type: HowTo
tags:
- Aspose.Words
- Java
- Word Automation
title: إنشاء مستند Word مع أشكال في Java – دليل Aspose.Words الكامل
url: /ar/java/images-shapes/create-word-document-with-shapes-in-java-complete-aspose-wor/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# إنشاء مستند Word مع أشكال في Java – دليل Aspose.Words الكامل

هل تساءلت يومًا كيف **create word document** برمجيًا وتضيف إليه رسومات مخصصة؟ لست وحدك. سواء كنت تحتاج إلى إنشاء تقرير مع أقسام مميزة أو تصميم منشور بسرعة، فإن إتقان التعامل مع الأشكال في Word يمكن أن يوفر لك ساعات من العمل اليدوي.

في هذا الدرس سنستعرض الخطوات الدقيقة لـ **create word document** باستخدام Aspose.Words for Java، **insert rectangle shape**، **group shapes in Word**، وأخيرًا **save document as docx**. في النهاية ستحصل على مثال كامل قابل للتنفيذ يمكنك إدراجه في أي مشروع.

## ما ستحصل عليه

- ملف Word جديد يتم إنشاؤه بالكامل من كود Java.  
- شكلان مميزان (مستطيل وإهليلج) مضافان إلى الصفحة.  
- تلك الأشكال مجمعة معًا باستخدام واجهة برمجة التطبيقات **group shapes in word**، لتتصرف ككائن واحد.  
- الملف محفوظ على القرص كملف `.docx` قياسي يفتح في Microsoft Word دون أي مشاكل.  

بدون أدوات خارجية، بدون حيل XML معقدة — فقط Java نظيفة ومكتوبة بوضوح وAspose.Words.

---

## المتطلبات المسبقة

قبل أن نبدأ، تأكد من وجود ما يلي:

1. **Java Development Kit (JDK) 8 أو أحدث** – الكود يستهدف Java 8+.  
2. **Aspose.Words for Java** JAR (يمكنك الحصول على أحدث نسخة من مستودع Maven Central).  
3. بيئة تطوير متوسطة (IntelliJ IDEA، Eclipse، أو حتى محرر نصوص بسيط).  

إذا كان لديك كل ذلك، رائع—لنبدأ.

## تنفيذ خطوة بخطوة

فيما يلي نقسم العملية إلى خطوات صغيرة. كل خطوة تتضمن مقطع كود، شرحًا مختصرًا، ونصيحة قد لا تجدها في الوثائق الرسمية.

### ## إنشاء مستند Word مع أشكال باستخدام Aspose.Words

الخطوة الأولى هي الحصول على ملف Word فارغ للعمل معه. Aspose.Words يجعل ذلك سطرًا واحدًا.

```java
// Step 1: Initialise a blank document and a DocumentBuilder
Document doc = new Document();                 // Represents the Word file
DocumentBuilder builder = new DocumentBuilder(doc);
```

**Why this matters:**  
`Document` هو الحاوية لكل شيء—النص، الجداول، الصور، والأشكال. `DocumentBuilder` هو المساعد الودود الذي يتيح لك إضافة محتوى دون الحاجة للتعامل مع الكائنات منخفضة المستوى. فكر فيه كقلم يكتب مباشرة على الصفحة.

> **Pro tip:** إذا كنت تخطط للبدء من قالب (مثلاً، ترويسة شركة)، استبدل `new Document()` بـ `new Document("template.docx")`.

### ## إدراج مستطيل وشكل آخر

الآن سنضيف مستطيل أزرق وإهليلج أخضر. المستطيل يوضح كلمة **insert rectangle shape**، بينما يُظهر الإهليلج أنه يمكنك خلط أنواع الأشكال بحرية.

```java
// Step 2: Insert a rectangle shape (100x50 points) and set its appearance
Shape rect = builder.insertShape(ShapeType.RECTANGLE, 100, 50);
rect.setLeft(50);                               // X‑coordinate in points
rect.setTop(50);                                // Y‑coordinate in points
rect.getFill().setColor(java.awt.Color.BLUE);  // Fill color

// Step 3: Insert an ellipse shape (80x80 points) and configure it
Shape ellipse = builder.insertShape(ShapeType.ELLIPSE, 80, 80);
ellipse.setLeft(180);
ellipse.setTop(30);
ellipse.getFill().setColor(java.awt.Color.GREEN);
```

**What’s happening under the hood?**  
كل استدعاء لـ `insertShape` ينشئ كائن `Shape` ويضيفه تلقائيًا إلى الفقرة الحالية. طُرُق `setLeft`/`setTop` تحدد موضع الشكل بالنسبة لهامش الصفحة، مقاسة بالنقاط (1 pt = 1/72 in). بتعديل هذه القيم يمكنك وضع الأشكال في أي مكان تريده.

> **Common question:** *هل يمكنني إضافة صورة بدلاً من لون صلب؟*  
> بالتأكيد—ما عليك سوى استبدال لون التعبئة بصورة باستخدام `shape.getFill().setImage("path/to/image.png")`.

### ## تجميع الأشكال في Word لتسهيل التعامل

وجود كائنين منفصلين لا بأس به، لكن غالبًا ما تريد تحريكهما معًا. هنا يأتي دور **group shapes in word**.

```java
// Step 4: Create a GroupShape container and add the two shapes
GroupShape group = builder.insertGroupShape(); // Starts an empty group
group.appendChild(rect);
group.appendChild(ellipse);

// Step 5: Reposition the whole group as a single entity
group.setLeft(100);
group.setTop(150);
```

**Why group?**  
عند تجميع الأشكال، أي تحويل—نقل، تدوير، تغيير حجم—يُطبق على المجموعة بأكملها. هذا يحاكي السلوك الذي تحصل عليه عند اختيار عدة أشكال يدويًا في واجهة Word والنقر على *Group*. كما يبسط الكود لاحقًا لأنك تحتاج لتعديل كائن واحد فقط بدلاً من عدة كائنات.

> **Edge case:** إذا احتجت لاحقًا إلى فك التجميع، استدعِ `group.getParentNode().removeChild(group)` وأعد إدراج الأطفال بشكل فردي.

### ## حفظ المستند كـ DOCX والتحقق من النتيجة

أخيرًا، نقوم بحفظ الملف. هذه الخطوة تلبي متطلب **save document as docx**.

```java
// Step 6: Write the document to disk as a .docx file
String outputPath = "output/GroupShapeExample.docx";
doc.save(outputPath, SaveFormat.DOCX);
System.out.println("Document saved successfully to " + outputPath);
```

**What to expect:**  
افتح الملف `GroupShapeExample.docx` في Microsoft Word. سترى مستطيلًا أزرق وإهليلجًا أخضر، مجمّعين معًا. اسحب المجموعة—كلا الشكلين يتحركان معًا، تمامًا كما هو متوقع من الواجهة.

> **Tip:** استخدم `SaveFormat.PDF` إذا كنت بحاجة إلى نسخة PDF؛ الكود نفسه يعمل دون تعديل.

### ## مثال كامل جاهز للعمل ومشكلات شائعة

فيما يلي الفئة الكاملة في Java جاهزة للتنفيذ. انسخ‑الصقها في مشروعك، عدل مسار المجلد الناتج، ثم اضغط *Run*.

```java
import com.aspose.words.*;

public class GroupShapeExample {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document and a DocumentBuilder to work with it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Insert the first rectangle shape and set its position and fill color
        Shape rect = builder.insertShape(ShapeType.RECTANGLE, 100, 50);
        rect.setLeft(50);
        rect.setTop(50);
        rect.getFill().setColor(java.awt.Color.BLUE);

        // Step 3: Insert a second ellipse shape and configure its position and fill color
        Shape ellipse = builder.insertShape(ShapeType.ELLIPSE, 80, 80);
        ellipse.setLeft(180);
        ellipse.setTop(30);
        ellipse.getFill().setColor(java.awt.Color.GREEN);

        // Step 4: Group the two shapes together using the new GroupShape API
        GroupShape group = builder.insertGroupShape();
        group.appendChild(rect);
        group.appendChild(ellipse);

        // Step 5: Optionally reposition the entire group as a single object
        group.setLeft(100);
        group.setTop(150);

        // Step 6: Save the document containing the grouped shapes
        String outPath = "output/GroupShapeExample.docx";
        doc.save(outPath, SaveFormat.DOCX);
        System.out.println("Document saved successfully to " + outPath);
    }
}
```

#### مشكلات شائعة وكيفية تجنّبها

| Issue | Why It Happens | Fix |
|-------|----------------|-----|
| **`NullPointerException` on `builder`** | نسيان إنشاء `DocumentBuilder` بعد إنشاء `Document`. | تأكد من تشغيل `new DocumentBuilder(doc)` قبل أي إدراج للأشكال. |
| **Shapes appear off‑page** | استخدام قيم بكسل بدلاً من نقاط، أو عدم مراعاة الهوامش. | تذكر أن Aspose.Words يتوقع القيم بالنقاط؛ 72 pt = 1 in. عدّل `setLeft`/`setTop` وفقًا لذلك. |
| **Group disappears after save** | إضافة الأشكال إلى المجموعة *بعد* حفظ المستند. | اجمع الأشكال دائمًا قبل استدعاء `doc.save()`. |
| **File not found on save** | دليل الإخراج غير موجود. | أنشئ الدليل برمجيًا (`new File("output").mkdirs();`) أو استخدم مسارًا موجودًا. |

---

## الخاتمة

لقد قمنا للتو بـ **create word document** من الصفر، **add shapes to word**، **insert rectangle shape**، **group shapes in word**، وأخيرًا **save document as docx**—كل ذلك بضع أسطر من Java. تكمن قوة Aspose.Words في نموذج الكائنات الواضح؛ يمكنك التعامل مع ملف Word كقماش، ورسم الأشكال عليه، ثم تصديره إلى أي صيغة تحتاجها.

هل تشعر بالمغامرة؟ جرّب استبدال المستطيل بنجمة، أضف نصًا داخل الأشكال باستخدام `Shape.getTextBox()`، أو جرّب التدوير (`shape.setRotationAngle(45)`). الواجهة غنية، والاحتمالات لا نهائية تقريبًا.

هل لديك أسئلة حول سيناريوهات أكثر تقدمًا—مثل ربط الأشكال بالإشارات المرجعية أو تصدير إلى PDF مع خطوط مدمجة؟ اترك تعليقًا أدناه، وسنغوص أعمق معًا. Happy coding!

## ما الذي ينبغي أن تتعلمه بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات التي تم توضيحها في هذا الدليل. كل مصدر يتضمن أمثلة كود كاملة مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف أساليب تنفيذ بديلة في مشاريعك الخاصة.

- [إنشاء مستند Word Java – إضافة مستطيل مع تأثير الظل](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [إنشاء مجموعة أشكال في مستند Word باستخدام Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [إنشاء مستطيل في Word باستخدام Aspose.Words – دليل خطوة بخطوة](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}