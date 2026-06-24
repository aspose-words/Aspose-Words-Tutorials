---
category: general
date: 2026-06-20
description: احفظ مستند Word باستخدام Aspose.Words في Java مع إضافة شكل مستطيل وتطبيق
  ظل. تعلم كيفية إدراج الشكل خطوة بخطوة.
draft: false
keywords:
- save word document
- add rectangle shape
- apply shadow to shape
- how to add shadow
- how to insert shape
language: ar
og_description: احفظ مستند Word باستخدام Aspose.Words Java. يوضح هذا الدليل كيفية
  إضافة شكل مستطيل، وتطبيق ظل، وإدراجه في فقرة.
og_title: حفظ مستند Word – إضافة شكل مستطيل وظل في Java
schemas:
- author: Aspose
  dateModified: '2026-06-20'
  description: Save Word document using Aspose.Words in Java while adding a rectangle
    shape and applying a shadow. Learn how to insert shape step‑by‑step.
  headline: Save Word Document – Add Rectangle Shape & Shadow in Java
  type: TechArticle
- description: Save Word document using Aspose.Words in Java while adding a rectangle
    shape and applying a shadow. Learn how to insert shape step‑by‑step.
  name: Save Word Document – Add Rectangle Shape & Shadow in Java
  steps:
  - name: '**Compile** – `javac -cp "aspose-words-xx.jar" ShadowShapeDemo.java`'
    text: '**Compile** – `javac -cp "aspose-words-xx.jar" ShadowShapeDemo.java`'
  - name: '**Execute** – `java -cp ".;aspose-words-xx.jar" ShadowShapeDemo`'
    text: '**Execute** – `java -cp ".;aspose-words-xx.jar" ShadowShapeDemo`'
  - name: '**Open** `shadow.docx` in Microsoft Word or LibreOffice. You should see
      the rectangle with a soft black shadow anchored at the start of the first paragraph.'
    text: '**Open** `shadow.docx` in Microsoft Word or LibreOffice. You should see
      the rectangle with a soft black shadow anchored at the start of the first paragraph.'
  type: HowTo
- questions:
  - answer: Yes. Retrieve the target `Section` or `PageSetup` and insert the shape
      into a paragraph located on that page.
    question: Can I add the shape to a specific page?
  - answer: Absolutely. Aspose.Words abstracts the format, so the same code **saves
      a Word document** whether it’s `.doc` or `.docx`.
    question: Does this work with .doc files?
  - answer: 'Replace `ShapeType.RECTANGLE` with `ShapeType.ELLIPSE`. All shadow properties
      remain the same. --- ## Conclusion You now know how to **save a Word document**
      while **adding a rectangle shape**, **applying a shadow**, and **inserting the
      shape** into the first paragraph—all with a handful of clean Ja'
    question: What if I need a different shape, like an ellipse?
  type: FAQPage
tags:
- Aspose.Words
- Java
- Word Automation
title: حفظ مستند Word – إضافة شكل مستطيل وظل في Java
url: /ar/java/images-shapes/save-word-document-add-rectangle-shape-shadow-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# حفظ مستند Word – إضافة شكل مستطيل وظل في Java

هل تساءلت يوماً كيف **تحفظ مستند Word** بعد تعديل تخطيطه؟ لست وحدك—معظم المطورين يواجهون هذه المشكلة عندما يحتاجون إلى إثراء ملف DOCX برمجياً. الخبر السار هو أنه باستخدام Aspose.Words for Java يمكنك **حفظ مستند Word**، وإدراج شكل مستطيل في المكان الذي تريد، وحتى إعطاء هذا الشكل ظلًا خفيفًا.

في هذا الدرس سنستعرض العملية بالكامل: تحميل ملف موجود، **إضافة شكل مستطيل**، ضبط **الظل** الخاص به، إدراج الشكل في الفقرة الأولى، وأخيرًا **حفظ مستند Word**. في النهاية ستحصل على برنامج Java قابل للتنفيذ ينتج ملف `shadow.docx` مصقول—بدون الحاجة لتعديل يدوي.

> **ما ستحتاجه**  
> * Java 17 (أو أي JDK حديث)  
> * مكتبة Aspose.Words for Java (Maven/Gradle أو ملف JAR)  
> * ملف DOCX إدخالي (`input.docx`) في مجلد معروف  

إذا كان لديك هذه الأساسيات، لنبدأ.

---

## حفظ مستند Word – مثال Java كامل

فيما يلي الشيفرة المصدرية الكاملة الجاهزة للتنفيذ. انسخها إلى بيئة التطوير المتكاملة (IDE) الخاصة بك، عدل المسارات، ثم اضغط **Run**.

```java
import com.aspose.words.*;
import com.aspose.words.drawing.*;

public class ShadowShapeDemo {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Load the existing document
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // 2️⃣ Create a rectangle shape (the core of add rectangle shape step)
        Shape rectangle = new Shape(doc, ShapeType.RECTANGLE);
        rectangle.setWidth(100.0);
        rectangle.setHeight(50.0);

        // 3️⃣ Apply shadow to shape – how to add shadow in Aspose.Words
        rectangle.getShadow().setVisible(true);
        rectangle.getShadow().setColor(java.awt.Color.BLACK);
        rectangle.getShadow().setBlurRadius(5.0);
        rectangle.getShadow().setOffsetX(4.0);
        rectangle.getShadow().setOffsetY(4.0);
        rectangle.getShadow().setTransparency(0.3);

        // 4️⃣ Insert shape into the first paragraph – how to insert shape
        Paragraph firstPara = doc.getFirstSection().getBody().getParagraphs().get(0);
        firstPara.appendChild(rectangle);

        // 5️⃣ Save the modified document – the final save word document step
        doc.save("YOUR_DIRECTORY/shadow.docx");
        System.out.println("Document saved successfully as shadow.docx");
    }
}
```

**النتيجة المتوقعة:** بعد تشغيل البرنامج، افتح `shadow.docx`. سترى المحتوى الأصلي بالإضافة إلى مستطيل أسود بحجم 100 × 50 pt مع ظل ناعم في بداية الفقرة الأولى.

---

## إضافة شكل مستطيل إلى مستند Word

لماذا نستخدم شكلًا مستطيلًا أصلاً؟ فكر فيه كمرساة بصرية—مثالي للتعليقات، أو الحوامل، أو الرسومات البسيطة. في Aspose.Words، فئة `Shape` تمثل جميع كائنات الرسم، و`ShapeType.RECTANGLE` يمنحك صندوقًا نظيفًا دون أي تعقيدات إضافية.

**نقاط رئيسية عند إضافة شكل مستطيل**

- **الوحدات هي النقاط** (1 pt = 1/72 in). عدّل `setWidth`/`setHeight` لتناسب تخطيطك.  
- الشكل يعيش داخل شجرة العقد في المستند، لذا يمكنك إدراجه في أي مكان يُسمح فيه بوجود `Paragraph` أو `Run`.  
- يمكنك تنسيق المستطيل (التعبئة، لون الخط، إلخ) قبل تطبيق الظل.

> **نصيحة احترافية:** إذا كنت تحتاج تعبئة شفافة، استدعِ `rectangle.getFill().setTransparent(true);`.

---

## تطبيق الظل على الشكل

الظلال تضيف عمقًا. كائن `Shadow` المرتبط بـ `Shape` يوفّر خصائص تتطابق مباشرةً مع خيارات واجهة Word.

| الخاصية | ما يفعله | القيمة النموذجية |
|----------|--------------|---------------|
| `setVisible(true)` | يشغّل الظل | `true` |
| `setColor(Color.BLACK)` | لون الظل | `Color.BLACK` |
| `setBlurRadius(5.0)` | نعومة الحواف | `5.0` |
| `setOffsetX(4.0)` / `setOffsetY(4.0)` | الإزاحة الأفقية/العمودية | `4.0` لكل منهما |
| `setTransparency(0.3)` | الشفافية (0 = غير شفاف، 1 = غير مرئي) | `0.3` |

عندما تسأل **كيف تطبق ظلًا على شكل**، الجواب هو ببساطة تعديل هذه الخصائص الست. يمكنك التجربة—الإزاحات الأكبر تعطي إحساسًا بـ "الرفع"، بينما قيمة `blurRadius` أعلى تنتج مظهرًا أكثر انتشارًا.

> **خطأ شائع:** نسيان `setVisible(true)` يترك الشكل بدون ظل حتى لو ضبطت الخصائص الأخرى.

---

## كيفية إدراج الشكل في فقرة

إدراج الشكل ليس سحراً؛ إنه مجرد تعديل عقد. طريقة `appendChild` تضع الشكل في نهاية عقد الفقرة. إذا أردت الشكل قبل النص، استخدم `insertBefore` بدلاً من ذلك.

```java
Paragraph para = doc.getFirstSection().getBody().getParagraphs().get(0);
para.insertBefore(rectangle, para.getFirstChild());
```

هذا التغيير الصغير يجيب على سؤال **كيف تُدرج الشكل** في المكان المطلوب—قبل أي `Run` موجود، بعد عنوان، أو حتى داخل خلية جدول (فقط احصل على عقدة `Cell` المناسبة أولاً).

---

## تشغيل الشيفرة والتحقق من النتيجة

1. **تجميع** – `javac -cp "aspose-words-xx.jar" ShadowShapeDemo.java`  
2. **تنفيذ** – `java -cp ".;aspose-words-xx.jar" ShadowShapeDemo`  
3. **فتح** `shadow.docx` في Microsoft Word أو LibreOffice. يجب أن ترى المستطيل مع ظل أسود ناعم مثبتًا في بداية الفقرة الأولى.

إذا لم يظهر الشكل، تحقق من التالي:

- مسار ملف الإدخال صحيح.  
- تستخدم نسخة حديثة من Aspose.Words (تم تعديل الـ API قليلًا قبل الإصدار 20.12).  
- المستند يحتوي على فقرة واحدة على الأقل (إلا سيؤدي `getParagraphs().get(0)` إلى استثناء `IndexOutOfBoundsException`).

---

## الأسئلة المتكررة (FAQ)

**س: هل يمكنني إضافة الشكل إلى صفحة محددة؟**  
ج: نعم. احصل على الـ `Section` أو `PageSetup` المستهدف وأدرج الشكل في فقرة موجودة في تلك الصفحة.

**س: هل يعمل هذا مع ملفات .doc؟**  
ج: بالتأكيد. Aspose.Words ي abstracts الصيغة، لذا نفس الشيفرة **تحفظ مستند Word** سواء كان `.doc` أو `.docx`.

**س: ماذا لو أردت شكلًا مختلفًا، مثل بيضاوي؟**  
ج: استبدل `ShapeType.RECTANGLE` بـ `ShapeType.ELLIPSE`. جميع خصائص الظل تبقى كما هي.

---

## الخلاصة

الآن تعرف كيف **تحفظ مستند Word** بينما **تضيف شكل مستطيل**، **تطبق ظلًا**، وت **درج الشكل** في الفقرة الأولى—كل ذلك بضع أسطر Java نظيفة. هذا النمط قابل للتوسيع: غير نوع الشكل، عدّل إعدادات الظل، أو ضع الشكل في جداول وترويسات. الإمكانيات واسعة بقدر احتياجات أتمتة المستندات لديك.

هل أنت مستعد للتحدي التالي؟ جرّب تراكب أشكال متعددة، إضافة نص داخل المستطيل، أو إنشاء تقرير كامل يحتوي على مخططات وعلامات مائية. كل هذه المهام تبني على الأساسيات التي غطيناها هنا—وبالتالي أنت بالفعل خطوة أمام الآخرين.

برمجة سعيدة، ولتكن أتمتة Word خالية من الأخطاء!

## ماذا يجب أن تتعلم بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات التي تم توضيحها في هذا الدليل. كل مصدر يتضمن أمثلة شيفرة كاملة مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف أساليب تنفيذ بديلة في مشاريعك.

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [How to save document as pdf with Aspose.Words for Java](/words/english/java/document-loading-and-saving/saving-documents-as-pdf/)
- [How to save word as pcl with Aspose.Words for Java](/words/english/java/document-loading-and-saving/saving-documents-as-pcl-format/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}