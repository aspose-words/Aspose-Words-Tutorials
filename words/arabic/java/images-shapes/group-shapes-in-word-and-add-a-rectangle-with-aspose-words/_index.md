---
category: general
date: 2026-09-11
description: تجميع الأشكال في Word وإضافة شكل مستطيل باستخدام Aspose.Words for Java.
  تعلّم كيفية ضبط حجم الشكل، تجميع الكائنات، وحفظ المستند.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- group shapes in word
- add rectangle shape
- set shape size
- how to group shapes
- how to add rectangle
language: ar
lastmod: 2026-09-11
og_description: تجميع الأشكال في Word وإضافة شكل مستطيل باستخدام Aspose.Words for
  Java. يوضح هذا البرنامج التعليمي كيفية تعيين حجم الشكل، تجميع الأشكال، وتصدير المستند.
og_image_alt: Screenshot showing grouped shapes in a Word document
og_title: تجميع الأشكال في Word – إضافة مستطيل باستخدام Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-09-11'
  description: Group shapes in Word and add a rectangle shape using Aspose.Words for
    Java. Learn how to set shape size, group objects, and save the document.
  headline: Group shapes in Word and add a rectangle with Aspose.Words
  type: TechArticle
- description: Group shapes in Word and add a rectangle shape using Aspose.Words for
    Java. Learn how to set shape size, group objects, and save the document.
  name: Group shapes in Word and add a rectangle with Aspose.Words
  steps:
  - name: Prerequisites
    text: '* Java 17 or later installed. * Maven or Gradle to manage dependencies.
      * A valid Aspose.Words for Java license (or a free evaluation key). * An image
      file (`sample.png`) placed in a known directory (replace `YOUR_DIRECTORY` with
      your actual path).'
  - name: Add a group shape
    text: A group shape is a container that can hold other shapes. Think of it as
      a folder for drawing objects.
  - name: How to add rectangle
    text: The code above demonstrates **how to add rectangle** by creating a `Shape`
      instance with `ShapeType.RECTANGLE` and then appending it to the `GroupShape`.
      This pattern works for any other shape type (e.g., `ELLIPSE`, `POLYLINE`).
  type: HowTo
tags:
- Aspose.Words
- Java
- Word automation
title: تجميع الأشكال في Word وإضافة مستطيل باستخدام Aspose.Words
url: /ar/java/images-shapes/group-shapes-in-word-and-add-a-rectangle-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# تجميع الأشكال في Word وإضافة مستطيل باستخدام Aspose.Words

إذا كنت بحاجة إلى **تجميع الأشكال في Word** أثناء إضافة مستطيل برمجياً، فإن هذا الدليل يقدم لك حلاً كاملاً وجاهزاً للتنفيذ. ستتعرف بالضبط على كيفية إدراج شكل مجموعة، إضافة شكل مستطيل، ضبط حجم الشكل، وأخيراً حفظ المستند لتتمكن من عرض النتيجة فوراً.

العمل مع مستندات Word غالباً ما يعني ترتيب عدة كائنات—صور، مخططات، أو أشكال هندسية بسيطة—في وحدة منطقية واحدة. يجعل تجميع هذه الكائنات من السهل تحريكها أو تدويرها أو تنسيقها معاً. في هذا البرنامج التعليمي سنغطي أيضاً **كيفية إضافة مستطيل** وكيفية **ضبط حجم الشكل** للتحكم المثالي في التخطيط.

## ما ستتعلمه

* كيفية إنشاء مستند Word جديد باستخدام Aspose.Words for Java.  
* **كيفية تجميع الأشكال** بحيث تتصرف ككائن واحد.  
* **إضافة شكل مستطيل** إلى مجموعة وإدراج صورة في نفس المجموعة.  
* **ضبط حجم الشكل** لكل من المستطيل والصورة.  
* حفظ المستند وفتحه في Microsoft Word للتحقق من النتيجة.

### المتطلبات المسبقة

* Java 17 أو أحدث مثبتة.  
* Maven أو Gradle لإدارة الاعتمادات.  
* رخصة صالحة لـ Aspose.Words for Java (أو مفتاح تقييم مجاني).  
* ملف صورة (`sample.png`) موجود في دليل معروف (استبدل `YOUR_DIRECTORY` بالمسار الفعلي الخاص بك).

---

## كيفية تجميع الأشكال في Word باستخدام Aspose.Words

الخطوة الأولى هي إنشاء `Document` و`DocumentBuilder`. يوفر الـ builder واجهة برمجة تطبيقات مريحة لإدراج الأشكال والنص والعناصر الأخرى.

```java
import com.aspose.words.*;

public class GroupShapesExample {
    public static void main(String[] args) throws Exception {
        // Initialize the document and builder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

> **لماذا هذا مهم:** يعمل `DocumentBuilder` مباشرةً مع كائن `Document` الأساسي، مما يتيح لك إدراج الأشكال دون الحاجة إلى التعامل يدويًا مع مجموعات العقد منخفضة المستوى.

### إضافة شكل مجموعة

شكل المجموعة هو حاوية يمكنها احتواء أشكال أخرى. فكر فيه كملف للمُرسَّمات.

```java
        // Insert an empty group shape – this will hold the rectangle and the picture
        GroupShape group = builder.insertGroupShape();
```

طريقة `insertGroupShape()` تنشئ عقدة `GroupShape` وتُعيدها لتتمكن من إلحاق أشكال فرعية لاحقاً.  

---

## إضافة شكل مستطيل إلى المجموعة

الآن سنقوم **بإضافة شكل مستطيل** إلى المجموعة التي أنشأناها مسبقاً. سيعمل المستطيل كخلفية أو إطار للصورة.

```java
        // Create a rectangle shape with a specific size
        Shape rectangle = new Shape(doc, ShapeType.RECTANGLE);
        rectangle.setWidth(100.0);   // width in points
        rectangle.setHeight(50.0);   // height in points
        rectangle.setFillColor(java.awt.Color.LIGHT_GRAY);
        rectangle.setStrokeColor(java.awt.Color.DARK_GRAY);
        rectangle.setStrokeWeight(1.0);
        // Append the rectangle to the group
        group.appendChild(rectangle);
```

> **نصيحة:** ضبط `FillColor` و`StrokeColor` يجعل المستطيل مرئياً في المستند النهائي. إذا حذفت هذه الخصائص، قد يظهر الشكل شفافاً.

### كيفية إضافة مستطيل

الكود أعلاه يوضح **كيفية إضافة مستطيل** بإنشاء مثيل `Shape` مع `ShapeType.RECTANGLE` ثم إلحاقه بـ `GroupShape`. هذا النمط يعمل مع أي نوع شكل آخر (مثل `ELLIPSE`، `POLYLINE`).

---

## ضبط حجم الشكل للمستطيل والصورة

ضبط الحجم بشكل صحيح يضمن أن المستطيل والصورة يتماشيان بدقة. هنا نُضبط أيضاً **حجم الشكل** للصورة التي سنُدرجها لاحقاً.

```java
        // Insert an image and set its size
        Shape picture = builder.insertImage("YOUR_DIRECTORY/sample.png");
        picture.setWidth(100.0);   // match rectangle width
        picture.setHeight(50.0);   // match rectangle height
        // Append the picture to the same group
        group.appendChild(picture);
```

الآن كلا من المستطيل والصورة يشتركان في نفس الأبعاد (100 × 50 نقطة). وبما أنهما ينتميان إلى نفس المجموعة، فإن تحريك أو تدوير المجموعة سيؤثر على الشكلين معاً.

> **لماذا مطابقة الأحجام؟** يضمن توافق الأبعاد أن الصورة تجلس داخل المستطيل بشكل أنيق، مما يُنتج تأثير “صورة مُؤطرة” نظيف.

---

## حفظ المستند وعرض النتيجة

أخيراً، نكتب المستند إلى القرص. عند فتح الملف في Microsoft Word ستظهر الأشكال المجمعة ككائن واحد قابل للتحديد.

```java
        // Save the document – the group will appear as one object in Word
        doc.save("YOUR_DIRECTORY/output.docx");
        System.out.println("Document saved successfully.");
    }
}
```

عند فتح `output.docx`، سترى مستطيلاً يحتوي على الصورة داخله. النقر على الشكل يحدد كلًا من المستطيل والصورة لأنهما **مجمّعان**.

![group shapes in word example](https://example.com/images/group-shapes-word.png "group shapes in word example")

*نص بديل للصورة:* *group shapes in word example* – مستند Word يُظهر مستطيلًا وصورةً مجمّعين معاً.

---

## أسئلة شائعة ومعالجة الحالات الخاصة

| السؤال | الجواب |
|----------|--------|
| **ماذا لو احتجت حجمًا مختلفًا للصورة؟** | عدّل `picture.setWidth()` و`picture.setHeight()` بعد الإدراج. يمكن للمستطيل الحفاظ على حجمه الأصلي، أو يمكنك أيضاً تعديل حجمه ليتطابق. |
| **هل يمكنني إضافة المزيد من الأشكال إلى نفس المجموعة؟** | نعم. استدعِ `group.appendChild(newShape)` لأي كائنات `Shape` إضافية. |
| **كيف أقوم بتدوير المجموعة بأكملها؟** | استخدم `group.setRotationAngle(double angleInRadians)`. سيُطبق الدوران على كل شكل فرعي. |
| **ماذا لو كان ملف الصورة مفقودًا؟** | `insertImage` يرمي استثناء `FileNotFoundException`. احيط الاستدعاء بكتلة try‑catch وقدّم شكلًا بديلًا كعنصر نائب. |
| **هل يمكن إلغاء التجميع لاحقًا؟** | استدعِ `group.removeAllChildren()` لفصل الأطفال، ثم أدرجهم مرة أخرى في المستند بشكل منفصل. |

---

## الخلاصة

الآن لديك مثال كامل وقابل للتنفيذ يوضح **كيفية تجميع الأشكال في Word**، **إضافة شكل مستطيل**، **ضبط حجم الشكل**، و**حفظ** المستند باستخدام Aspose.Words for Java. من خلال تجميع المستطيل والصورة، يمكنك تحريكهما أو تغيير حجمهما أو تدويرهما كوحدة واحدة—وهو بالضبط ما تتطلبه العديد من سيناريوهات أتمتة المستندات.

من هنا يمكنك استكشاف:

* إضافة صناديق نصية إلى نفس المجموعة (`how to add rectangle`‑style text).  
* تطبيق أنماط تعبئة مختلفة أو تدرجات (`set shape size` مع التنسيق).  
* استخدام التقنية نفسها لتجميع المخططات، الجداول، أو SmartArt (`how to group shapes` عبر أنواع كائنات أخرى).  

لا تتردد في تجربة أنواع أشكال أخرى، ألوان، وخيارات تخطيط. Happy coding!

## ماذا يجب أن تتعلم بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات الموضحة في هذا الدليل. كل مورد يتضمن أمثلة شاملة مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف أساليب تنفيذ بديلة في مشاريعك.

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [How to create form fields and add content using DocumentBuilder in Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [How to Convert Word to PDF Using Aspose.Words for Java](/words/english/java/document-converting/using-document-converting/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}