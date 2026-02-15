---
category: general
date: 2026-02-15
description: إنشاء شكل مستطيل في مستند Word باستخدام Java. تعلم كيفية إضافة ظل للشكل،
  حفظ مستند Word، وإضافة شكل مستطيل باستخدام Aspose.Words.
draft: false
keywords:
- create rectangle shape
- save word document
- how to shadow shape
- add shape shadow
- add rectangle shape
language: ar
og_description: إنشاء شكل مستطيل في ملف Word باستخدام Java. يوضح هذا الدليل كيفية
  إضافة ظل للشكل، حفظ مستند Word، وإضافة شكل مستطيل خطوة بخطوة.
og_title: إنشاء شكل مستطيل – دليل Aspose.Words لجافا
tags:
- Aspose.Words
- Java
- Document Automation
title: إنشاء شكل مستطيل في Word باستخدام Java – دليل كامل
url: /ar/java/images-shapes/create-rectangle-shape-in-word-with-java-full-guide/
---

with all translations.

Be careful with markdown formatting.

Let's craft Arabic translations.

We'll keep bold phrases unchanged.

Proceed to write final content.{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# إنشاء شكل مستطيل في Word باستخدام Java – دليل كامل

هل احتجت يوماً إلى **create rectangle shape** في ملف Word لكن لم تكن متأكدًا من أين تبدأ؟ لست وحدك—العديد من المطورين يواجهون هذه المشكلة عند أتمتة التقارير أو الفواتير. الخبر السار؟ باستخدام Aspose.Words for Java يمكنك إنشاء مستطيل، إضافة ظل جميل، وحفظ مستند Word ببضع أسطر فقط.

في هذا الدرس سنستعرض كل ما تحتاجه: من تهيئة مستند فارغ، إلى ضبط الظل، وحتى حفظ الملف. في النهاية ستعرف **how to shadow shape**، وكيفية **add shape shadow**، وكيفية **add rectangle shape** لأي مستند Word تقوم بإنشائه. لا حاجة لأي مستندات خارجية—فقط كود جاهز للتنفيذ.

## المتطلبات المسبقة

- Java 8 أو أحدث (تعمل الواجهة البرمجية أيضًا مع Java 11+).  
- مكتبة Aspose.Words for Java (الإصدار 23.9 أو أحدث).  
- بيئة تطوير متكاملة مثل IntelliJ IDEA أو Eclipse—أي منها يناسبك.  
- إلمام أساسي بصياغة Java.

> **نصيحة احترافية:** إذا كنت تستخدم Maven، أضف تبعية Aspose.Words إلى ملف `pom.xml` ودع IDE يتولى الباقي.

---

## الخطوة 1: تهيئة مستند جديد – How to **create rectangle shape**  

أولاً وقبل كل شيء: تحتاج إلى لوحة نظيفة. في Aspose.Words تكون هذه اللوحة كائن `Document`.

```java
import com.aspose.words.*;

public class ShadowShapeExample {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document
        Document document = new Document();
```

فئة `Document` تمثل ملف .docx بالكامل. فكر فيها كدفتر ملاحظات ستضيف إليه لاحقًا **add rectangle shape** وظله.

## الخطوة 2: بناء المستطيل – **Add rectangle shape**  

الآن نقوم فعليًا بإنشاء المستطيل. سنحدد حجمه، تخطيطه، ولون التعبئة.

```java
        // Step 2: Create a rectangle shape and set its size and layout
        Shape rectangleShape = new Shape(document, ShapeType.RECTANGLE);
        rectangleShape.setWidth(200);
        rectangleShape.setHeight(100);
        rectangleShape.setWrapType(WrapType.INLINE);
        rectangleShape.setFillColor(java.awt.Color.LIGHT_GRAY);
```

لماذا نستخدم التغليف `INLINE`؟ لأننا نريد أن يتصرف الشكل كفقرة—مثالي للتقارير البسيطة. يمكنك تغييره إلى `TOPBOTTOM` إذا احتجت إلى تدفق النص حول الشكل لاحقًا.

## الخطوة 3: تطبيق الظل – **How to shadow shape**  

المستطيل المسطح يبدو باهتًا قليلًا. إضافة الظل تمنحه عمقًا وتُحسّن مظهر المستند. هنا نجيب على سؤال “**how to shadow shape**” عمليًا.

```java
        // Step 3: Configure the shape's shadow appearance
        rectangleShape.getShadowFormat().setVisible(true);
        rectangleShape.getShadowFormat().setColor(java.awt.Color.DARK_GRAY);
        rectangleShape.getShadowFormat().setBlurRadius(5.0);
        rectangleShape.getShadowFormat().setOffsetX(4.0);
        rectangleShape.getShadowFormat().setOffsetY(4.0);
        rectangleShape.getShadowFormat().setTransparency(0.3);
```

كل خاصية تقوم بوظيفة معينة:

- `setVisible(true)` يُفعّل الظل.  
- `setColor` يختار لونًا رماديًا داكنًا لتأثير خفيف.  
- `setBlurRadius` يتحكم في مدى نعومة الحواف.  
- `setOffsetX/Y` يحرك الظل إلى اليمين وإلى الأسفل، محاكياً مصدر الضوء.  
- `setTransparency` يجعل الظل شبه شفاف، بحيث يبقى الشكل هو البطل.

> **ملاحظة:** إذا احتجت ظلًا ملونًا، ما عليك سوى تمرير قيمة `java.awt.Color` مختلفة إلى `setColor`.

## الخطوة 4: إدراج الشكل في المستند  

بعد أن أصبح المستطيل وظله جاهزين، نضعه في القسم الأول من المستند.

```java
        // Step 4: Add the shape to the first section of the document
        document.getFirstSection().getBody().appendChild(rectangleShape);
```

الإضافة إلى الـ body تضع الشكل حيث ستظهر فقرة جديدة. إذا أردت وضع المستطيل في موقع محدد، يمكنك استخدام `insertBefore` أو تعديل مجموعة `Paragraph`.

## الخطوة 5: **Save Word document** – احفظ عملك  

الخطوة الأخيرة هي كتابة الملف إلى القرص. هذه هي اللحظة التي تقوم فيها فعليًا **save Word document**.

```java
        // Step 5: Save the document with the shadowed shape
        document.save("YOUR_DIRECTORY/ShadowShape.docx");
    }
}
```

استبدل `YOUR_DIRECTORY` بمسار مطلق أو نسبي على جهازك. بعد تشغيل البرنامج، افتح `ShadowShape.docx` في Microsoft Word—سترى مستطيلًا رماديًا فاتحًا مع ظل داكن ناعم.

![مخطط يوضح شكل مستطيل مع ظل تم إنشاؤه باستخدام Aspose.Words](https://example.com/rectangle-shadow.png "إنشاء شكل مستطيل مع ظل")

---

## الأسئلة الشائعة والحالات الخاصة  

### ماذا لو احتجت إلى عدة مستطيلات؟

ما عليك سوى تكرار **Step 2** و **Step 3** داخل حلقة، مع تعديل `setWidth`، `setHeight` أو `setFillColor` في كل تكرار. تذكر إعطاء كل شكل اسم متغير فريد أو تخزينها في قائمة.

### هل يمكنني التصدير إلى PDF بدلاً من DOCX؟

بالتأكيد. بعد إضافة الشكل، استدعِ `document.save("output.pdf")`. ستتعامل Aspose.Words مع التحويل مع الحفاظ على الظل.

### ماذا عن إصدارات Word القديمة؟

استخدم النسخة الزائدة `document.save("file.doc", SaveFormat.DOC)`. تقوم الواجهة البرمجية تلقائيًا بخفض الميزات، لكن لاحظ أن بعض أنماط الظل قد تبدو مختلفة قليلًا في الصيغ القديمة.

### كيف يمكنني تغيير اتجاه الظل؟

عدّل `setOffsetX` و `setOffsetY`. القيمة الموجبة لـ X تحرك الظل إلى اليمين، والسالبة إلى اليسار. القيمة الموجبة لـ Y تحركه إلى الأسفل، والسالبة إلى الأعلى. جرّب هذه القيم لمحاكاة مصدر ضوء من أي زاوية.

## نصائح للعمل مع الأشكال  

- **Group shapes**: إذا احتجت تسمية بجوار المستطيل، أنشئ `GroupShape` وأضف كلًا من المستطيل و`TextBox`.  
- **Z‑order matters**: استخدم `shape.moveToFront()` أو `shape.moveToBack()` للتحكم في أي شكل يظهر في الأعلى.  
- **Performance**: إضافة مئات الأشكال قد تكون بطيئة. اجمعها في قسم واحد، ثم استدعِ `document.updatePageLayout()` مرة واحدة في النهاية.

## ملخص  

غطّينا كيفية **create rectangle shape** في مستند Word باستخدام Java، وكيفية **add shape shadow**، وكيفية **save Word document** بالنتيجة. الكود الكامل القابل للتنفيذ موجود في المقاطع أعلاه، والآن تفهم “السبب” وراء كل خاصية—لتتمكن من تعديل الألوان، والطمس، والإزاحات لتناسب أي تصميم.

هل أنت جاهز للتحدي التالي؟ جرّب دمج المستطيل مع مخطط، أو صدّر الملف كـ PDF وشاهد كيف يُظهر الظل. يمكنك أيضًا استكشاف **add rectangle shape** داخل الجداول لتصاميم تقارير أكثر أناقة.

برمجة سعيدة، ولتظل مستنداتك دائمًا حادة مثل شفرتك!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}