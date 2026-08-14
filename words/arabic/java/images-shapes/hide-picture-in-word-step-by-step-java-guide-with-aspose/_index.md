---
category: general
date: 2026-08-14
description: إخفاء الصورة في Word باستخدام Java. تعلّم كيفية إخفاء الصورة، إخفاء الصورة،
  ضبط الخاصية المخفية، وإخفاء الشكل في Word باستخدام Aspose.Words.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- hide picture in word
- how to hide picture
- how to hide image
- set hidden property
- hide shape in word
language: ar
lastmod: 2026-08-14
og_description: إخفاء الصورة في Word باستخدام Java و Aspose.Words. يوضح هذا الدرس
  كيفية تعيين خاصية الإخفاء على صورة، إخفاء الشكل في Word، وحفظ المستند في ثوانٍ.
og_image_alt: Screenshot of Java code hiding a picture in a Word document
og_title: إخفاء الصورة في Word – دليل Java خطوة بخطوة مع Aspose
schemas:
- author: Aspose
  dateModified: '2026-08-14'
  description: Hide picture in Word using Java. Learn how to hide picture, hide image,
    set hidden property, and hide shape in Word with Aspose.Words.
  headline: Hide picture in Word – step‑by‑step Java guide with Aspose
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word automation
title: إخفاء الصورة في Word – دليل Java خطوة بخطوة مع Aspose
url: /ar/java/images-shapes/hide-picture-in-word-step-by-step-java-guide-with-aspose/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# إخفاء الصورة في Word – دليل Java خطوة بخطوة باستخدام Aspose

إذا كنت بحاجة إلى **إخفاء الصورة في Word** برمجياً، يوضح هذا الدليل الحل الكامل. سترى كيف يتم تحديد موقع صورة، تطبيق علامة الإخفاء، وكتابة الملف المحدث مرة أخرى إلى القرص.

إخفاء رسم بياني هو طلب شائع عندما تقوم بإنشاء تقارير، أو إنشاء قوالب، أو إعداد مستندات للمراجعة الامتثالية. المثال أدناه يوضح **كيفية إخفاء الصورة** باستخدام Aspose.Words for Java، لكن نفس المفاهيم تنطبق على أي مكتبة معالجة Word تُظهر طريقة `setHidden` للشكل.

## ما ستحقه

* تحميل ملف `.docx` باستخدام Aspose.Words.
* العثور على أول شكل صورة في المستند.
* **تعيين خاصية الإخفاء** لهذا الشكل بحيث لا يظهر عند فتح الملف في Microsoft Word.
* حفظ المستند المعدل دون تعديل المحتوى الآخر.

المتطلب الوحيد هو بيئة تطوير Java (JDK 8 أو أحدث) ورخصة صالحة لـ Aspose.Words for Java. لا توجد إضافات Maven إضافية مطلوبة بخلاف المكتبة الأساسية.

## إخفاء الصورة في Word باستخدام Aspose.Words

الخطوة الأولى هي إنشاء كائن `Document` الذي يمثل ملف المصدر. تقوم Aspose.Words بقراءة حزمة Word بالكامل إلى الذاكرة، مما يجعل من السهل استعراض العقد مثل الأشكال، الفقرات، والجداول.

```java
// Step 1: Load the Word document
Document doc = new Document("YOUR_DIRECTORY/input.docx");
```

إنشاء نسخة `Document` يتحقق من صحة تنسيق الملف ويبني شجرة عقد داخلية. هذه الشجرة هي الأساس لجميع العمليات اللاحقة، بما في ذلك **كيفية إخفاء الصور**.

## كيفية إخفاء الصورة باستخدام خاصية الإخفاء set hidden

الصورة في ملف Word تُخزن كعقدة `Shape` بنوع `ShapeType.IMAGE`. توفر المكتبة طريقة `setHidden(boolean)` للتحكم في رؤية الشكل. يُفلتر الدفق التالي مجموعة العقد لتحديد أول شكل صورة.

```java
// Step 2: Locate the first picture shape in the document
Shape picture = (Shape) doc.getChildNodes(NodeType.SHAPE, true)
        .stream()
        .filter(node -> ((Shape) node).getShapeType() == ShapeType.IMAGE)
        .findFirst()
        .orElse(null);
```

استدعاء `getChildNodes` يتجول عبر شجرة المستند بالكامل (`true` يُفعّل البحث العميق). تعبير lambda يتحقق من `ShapeType` لكل عقدة. هذا النمط هو الطريقة الموصى بها لـ **كيفية إخفاء الصورة** عندما تحتاج إلى تحكم دقيق في اختيار العقد.

## كيفية إخفاء الصورة في مستند Word

بمجرد تحديد الشكل المستهدف، قم بتطبيق علامة الإخفاء. ضبط هذه الخاصية لا يزيل الصورة؛ بل يوجه Word إلى اعتبار الشكل مخفيًا أثناء العرض.

```java
// Step 3: Hide the picture if it was found
if (picture != null) {
    picture.setHidden(true);
}
```

استدعاء `setHidden(true)` يطابق مباشرةً السمة XML الأساسية `w:hidden="true"`. يحترم Word هذه السمة في كل من المحررات المكتبية وعبر الإنترنت، مما يضمن بقاء الصورة غير مرئية لجميع المشاهدين.

## إخفاء الشكل في Word – اعتبارات إضافية

بينما يُخفي المثال الصورة الأولى فقط، يمكنك توسيع المنطق لمعالجة أشكال متعددة:

```java
// Hide all picture shapes
for (Node node : doc.getChildNodes(NodeType.SHAPE, true)) {
    Shape shape = (Shape) node;
    if (shape.getShapeType() == ShapeType.IMAGE) {
        shape.setHidden(true);
    }
}
```

* **الأداء** – استعراض شجرة العقد هو O(n)؛ بالنسبة للمستندات الكبيرة جدًا، فكر في تضييق البحث إلى أقسام محددة.
* **التوافق** – علامة الإخفاء تعمل مع Word 2007+ (`.docx`) وملفات Word 97‑2003 (`.doc`).
* **تبديل الرؤية** – لجعل صورة مخفية مرئية مرة أخرى، استدعِ `shape.setHidden(false)`.

هذه النصائح تساعدك على إتقان سيناريوهات **إخفاء الشكل في Word** خارج الحالة الأساسية.

## حفظ المستند المعدل

بعد تحديث علامة الإخفاء، اكتب المستند مرة أخرى إلى التخزين. تقوم Aspose.Words تلقائيًا بالحفاظ على جميع أجزاء المستند الأخرى، مثل الأنماط، رؤوس الصفحات، وتذييلات الصفحات.

```java
// Step 4: Save the modified document
doc.save("YOUR_DIRECTORY/output.docx");
```

طريقة `save` تدعم مجموعة واسعة من الصيغ (PDF، HTML، ODT). في هذا الدليل نحافظ على المخرجات كملف Word لتوضيح تأثير إخفاء الصورة مباشرة.

## مثال كامل قابل للتنفيذ

جمع جميع الخطوات معًا ينتج برنامجًا مستقلًا يمكنك تجميعه وتشغيله فورًا.

```java
import com.aspose.words.*;

public class HidePictureExample {
    public static void main(String[] args) throws Exception {
        // Load the Word document
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // Locate the first picture shape in the document
        Shape picture = (Shape) doc.getChildNodes(NodeType.SHAPE, true)
                .stream()
                .filter(node -> ((Shape) node).getShapeType() == ShapeType.IMAGE)
                .findFirst()
                .orElse(null);

        // Hide the picture if it was found
        if (picture != null) {
            picture.setHidden(true);
        }

        // Save the modified document
        doc.save("YOUR_DIRECTORY/output.docx");
    }
}
```

**النتيجة المتوقعة:** افتح `output.docx` في Microsoft Word. الصورة الأصلية لن تُعرض، لكن باقي المستند (النص، الجداول، الرسومات الأخرى) يظل دون تغيير. إذا فحصت XML (`document.xml`) ستلاحظ السمة `w:hidden="true"` على عنصر `<w:pict>` الذي يت对应 إلى الصورة المخفية.

## الخلاصة

أنت الآن تعرف كيف **إخفاء الصورة في Word** باستخدام Java، Aspose.Words، وخاصية `setHidden`. غطى الدليل كيفية تحديد شكل الصورة، تطبيق علامة الإخفاء، وحفظ التغييرات. مع هذه الأساسيات يمكنك أيضًا **إخفاء الشكل في Word**، معالجة صور متعددة، أو تبديل الرؤية بناءً على قواعد العمل.

**الخطوات التالية**

* استكشف **كيفية إخفاء الصورة** بشكل شرطي بناءً على البيانات الوصفية (مثل دور المستخدم).
* اجمع هذه التقنية مع دمج البريد لإنشاء مستندات مخصصة ومراعية للخصوصية.
* راجع مرجع Aspose.Words API للتعامل المتقدم مع الأشكال، مثل تغيير الدوران أو تطبيق العلامات المائية.

لا تتردد في تجربة تنويعات، مثل إخفاء المخططات أو كائنات SmartArt، ومشاركة نتائجك مع مجتمع المطورين. برمجة سعيدة!

## ما الذي يجب أن تتعلمه بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات الموضحة في هذا الدليل. كل مورد يتضمن أمثلة كود كاملة مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف أساليب تنفيذ بديلة في مشاريعك.

- [إخفاء محور المخطط في مستند Word](/words/english/net/programming-with-charts/hide-chart-axis/)
- [إظهار/إخفاء المحتوى المعلم في مستند Word](/words/english/net/programming-with-bookmarks/show-hide-bookmarked-content/)
- [إدراج صورة مدمجة في مستند Word باستخدام Aspose.Words](/words/english/net/add-content-using-document-builder/insert-inline-image/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}