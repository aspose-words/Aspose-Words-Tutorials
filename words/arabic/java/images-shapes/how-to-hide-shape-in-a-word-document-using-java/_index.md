---
category: general
date: 2026-10-04
description: تعلم كيفية إخفاء الشكل في Word باستخدام Java. يوضح لك هذا الدليل خطوة
  بخطوة كيفية إخفاء الشكل في Word، وجعل الشكل غير مرئي في Word، وإخفاء الشكل في Microsoft
  Word برمجيًا.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to hide shape
- hide shape in word
- make shape invisible word
- hide shape microsoft word
language: ar
lastmod: 2026-10-04
og_description: كيفية إخفاء الشكل في Word باستخدام Java. اتبع هذا الدليل لإخفاء الشكل
  في Word، وجعل الشكل غير مرئي في Word، وإخفاء الشكل في Microsoft Word ببضع أسطر من
  الشيفرة.
og_image_alt: Screenshot showing a Word document with a hidden shape after applying
  the how to hide shape code
og_title: كيفية إخفاء الشكل في مستند Word باستخدام Java – دليل كامل
schemas:
- author: Aspose
  dateModified: '2026-10-04'
  description: Learn how to hide shape in Word with Java. This step‑by‑step guide
    shows you how to hide shape in Word, make shape invisible Word, and hide shape
    Microsoft Word programmatically.
  headline: How to hide shape in a Word document using Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- Microsoft Word
- Document Automation
title: كيفية إخفاء الشكل في مستند Word باستخدام Java
url: /ar/java/images-shapes/how-to-hide-shape-in-a-word-document-using-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# كيفية إخفاء الشكل في مستند Word باستخدام Java

إذا كنت بحاجة إلى إخفاء شكل في ملف Word، فإن هذا الدليل يوضح لك بالضبط **كيفية إخفاء الشكل** برمجيًا. سواءً كنت تولد تقارير، أو تنظف القوالب، أو تُعدّ مستندات للامتثال، يمكنك جعل الشكل غير مرئي دون إزالته من بنية الملف.

في الأقسام أدناه ستتعلم كيفية إخفاء الشكل في Word، وجعل الشكل غير مرئي في Word، وإخفاء الشكل في Microsoft Word باستخدام مكتبة Aspose.Words for Java. يفترض الدليل أن لديك معرفة أساسية بـ Java وبيئة تطوير Java تعمل.

## المتطلبات المسبقة

* مجموعة تطوير جافا (JDK) 8 أو أحدث  
* Maven أو Gradle لإدارة التبعيات  
* Aspose.Words for Java (الإصدار 23.9 أو أحدث) – أضف إحداثية Maven `com.aspose:aspose-words:23.9`  
* مستند Word (`input.docx`) يحتوي على شكل واحد على الأقل (مثل صورة، مربع نص، أو SmartArt)

## الخطوة 1: إعداد المشروع واستيراد Aspose.Words

أنشئ مشروع Maven جديد أو أضف تبعية Aspose.Words إلى مشروع موجود.

```xml
<!-- pom.xml snippet -->
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
    <classifier>jdk17</classifier> <!-- adjust classifier for your JDK -->
</dependency>
```

توفر المكتبة الفئات `Document` و `NodeType` و `Shape` المستخدمة في الخطوات التالية. استوردها في أعلى ملف مصدر Java الخاص بك:

```java
import com.aspose.words.Document;
import com.aspose.words.NodeType;
import com.aspose.words.Shape;
```

## الخطوة 2: تحميل مستند Word

تحميل المستند هو الخطوة الأولى في أي سير عمل لمعالجة Word. يقوم مُنشئ `Document` بقراءة الملف إلى الذاكرة، مع الحفاظ على جميع العقد، بما في ذلك الأشكال المخفية.

```java
// Load the source document
Document doc = new Document("YOUR_DIRECTORY/input.docx");
```

*لماذا هذا مهم*: تحميل الملف يُنشئ نموذج كائن المستند (DOM) الذي يتيح لك التنقل، والاستعلام، وتعديل العقد الفردية مثل الأشكال، الفقرات، أو الجداول.

## الخطوة 3: استرجاع الشكل المستهدف

إذا كان المستند يحتوي على عدة أشكال، يمكنك تحديد شكل معين بواسطة الفهرس أو الاسم أو معايير أخرى. للعرض السريع، يجلب المثال الشكل الأول في تسلسل المستند، بما في ذلك الأشكال المتداخلة داخل الجداول أو المجموعات.

```java
// Retrieve the first shape (including descendants)
Shape shape = (Shape) doc.getChild(NodeType.SHAPE, 0, true);
```

*لماذا هذا مهم*: طريقة `getChild` مع القيمة `true` لعلامة `isDeep` تُجري استعراضًا كاملًا لشجرة العقد، مما يضمن التقاط الأشكال التي ليست أبناء مباشرة لجسم المستند.

## الخطوة 4: إخفاء الشكل

ضبط الخاصية `Hidden` إلى `true` يُخبر Microsoft Word باستبعاد الشكل من عرض التخطيط مع الحفاظ عليه في بنية المستند. لن يكون الشكل مرئيًا عند فتح الملف في Word، لكنه يظل متاحًا للمعالجة لاحقًا.

```java
// Hide the shape so it does not appear in the layout
shape.setHidden(true);
```

*لماذا هذا مهم*: إخفاء الشكل مفيد عندما تحتاج إلى الاحتفاظ بالشكل لتفعيل لاحق (مثل المحتوى الشرطي، الإصدارات) دون عرضه للمستخدم النهائي.

## الخطوة 5: حفظ المستند المعدل

بعد تغيير رؤية الشكل، احفظ المستند مرة أخرى على القرص. يمكنك استبدال الملف الأصلي أو إنشاء ملف جديد؛ المثال يكتب إلى `HiddenShape.docx`.

```java
// Save the document with the hidden shape
doc.save("YOUR_DIRECTORY/HiddenShape.docx");
```

عند فتح `HiddenShape.docx` في Microsoft Word، سيكون الشكل غير مرئي، ومع ذلك سيعكس تخطيط المستند حالته المخفية (بدون مساحة فارغة إضافية).

## مثال كامل قابل للتنفيذ

جمع جميع الخطوات معًا ينتج برنامجًا مستقلًا يمكنك تجميعه وتشغيله مباشرة.

```java
import com.aspose.words.Document;
import com.aspose.words.NodeType;
import com.aspose.words.Shape;

/**
 * Demonstrates how to hide shape in a Word document using Aspose.Words for Java.
 */
public class HideShapeExample {
    public static void main(String[] args) {
        // Verify that the input path is provided
        if (args.length != 1) {
            System.out.println("Usage: java HideShapeExample <input-docx-path>");
            return;
        }

        String inputPath = args[0];
        String outputPath = "HiddenShape.docx";

        try {
            // Step 1: Load the Word document
            Document doc = new Document(inputPath);

            // Step 2: Retrieve the first shape (including descendants)
            Shape shape = (Shape) doc.getChild(NodeType.SHAPE, 0, true);
            if (shape == null) {
                System.out.println("No shape found in the document.");
                return;
            }

            // Step 3: Hide the shape
            shape.setHidden(true);

            // Step 4: Save the modified document
            doc.save(outputPath);
            System.out.println("Shape hidden successfully. Output saved to " + outputPath);
        } catch (Exception e) {
            System.err.println("Error processing document: " + e.getMessage());
            e.printStackTrace();
        }
    }
}
```

**النتيجة المتوقعة**  
تشغيل البرنامج ينتج `HiddenShape.docx`. فتح هذا الملف في Microsoft Word يعرض المحتوى الأصلي لكن الشكل الموجود في `input.docx` لم يعد مرئيًا. لا يزال هيكل المستند يحتوي على عقدة الشكل، والتي يمكن إظهارها لاحقًا بتعيين `shape.setHidden(false)`.

## لماذا نُخفي الشكل بدلاً من حذفه؟

* **الحفاظ على البيانات الوصفية** – غالبًا ما تحمل الأشكال نصًا بديلًا أو روابط تشعبية أو بيانات مخصصة قد تحتاجها لاحقًا.  
* **العرض الشرطي** – في سيناريوهات دمج البريد أو توليد التقارير قد ترغب في إظهار الشكل فقط لمستلمين محددين.  
* **التحكم في الإصدارات** – إبقاء الشكل مخفيًا يتيح لك الحفاظ على قالب واحد مع تبديل الرؤية برمجيًا.

## الاختلافات الشائعة وحالات الحافة

| الحالة | التعديل الموصى به |
|-----------|------------------------|
| عدة أشكال، وتحتاج إلى شكل محدد | استخدم `doc.getChild(NodeType.SHAPE, index, true)` مع الفهرس المناسب، أو قم بالتكرار عبر `doc.getChildNodes(NodeType.SHAPE, true)` وتطابق على `shape.getName()` أو `shape.getAlternativeText()`. |
| الشكل داخل GroupShape | البحث العميق (`true`) يصل بالفعل داخل المجموعات، لكن قد تحتاج إلى تحويل إلى `GroupShape` أولاً إذا كنت تخطط لإخفاء عضو واحد فقط من المجموعة. |
| تريد إخفاء جميع الأشكال | قم بالتكرار على جميع عقد الشكل واستدعِ `setHidden(true)` داخل الحلقة. |
| التوافق مع إصدارات Word القديمة | علمة `Hidden` مدعومة منذ Word 2000. الصيغ القديمة (`.doc`) تحترمها أيضًا، لكن اختبر على الإصدار المستهدف إذا واجهت تغييرات غير متوقعة في التخطيط. |

**نصيحة احترافية:** بعد إخفاء الشكل، يمكنك استدعاء `doc.updatePageLayout()` إذا كنت بحاجة إلى إعادة حساب تخطيط الصفحة قبل الحفظ. هذا نادرًا ما يكون مطلوبًا لأن Word يعيد تدفق المحتوى تلقائيًا عند الفتح، لكنه قد يكون مفيدًا لتوليد معاينة على الخادم.

## اختبار النتيجة برمجيًا

إذا أردت التأكد من أن الشكل مخفي دون فتح Word، يمكنك الاستعلام عن الخاصية بعد الحفظ:

```java
Document checkDoc = new Document(outputPath);
Shape hiddenShape = (Shape) checkDoc.getChild(NodeType.SHAPE, 0, true);
System.out.println("Shape hidden flag: " + hiddenShape.isHidden()); // prints true
```

## الخطوات التالية

الآن بعد أن عرفت كيفية إخفاء الشكل في Word، فكر في هذه المواضيع ذات الصلة:

* **إخفاء الشكل في Word بناءً على شروط مخصصة** – اجمع علم `Hidden` مع حقول دمج البريد لتبديل الرؤية حسب المستلم.  
* **جعل الشكل غير مرئي في Word باستخدام VBA** – لأتمتة على الجهاز، يمكن ضبط الخاصية نفسها عبر VBA (`Shape.Visible = msoFalse`).  
* **إخفاء الشكل في Microsoft Word على نطاق واسع** – عالج مجلدًا من المستندات بحلقة تطبق نفس الكود على كل ملف.  

استكشاف هذه الإضافات سيعزز سيطرتك على أتمتة مستندات Word ويجعل ملفاتك المُولدة نظيفة ومهنية.

--- 

*هذا الدليل يتبع دليل أسلوب وثائق مطوري Google، يستخدم صيغة الفعل النشط، منظور المخاطب الثاني، ويوفر حلًا كاملًا وجديرًا بالاستشهاد لكل من محركات البحث ومساعدي الذكاء الاصطناعي.*

## ماذا يجب أن تتعلم بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات الموضحة في هذا الدليل. كل مورد يتضمن أمثلة شفرة كاملة مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف أساليب تنفيذ بديلة في مشاريعك.

- [إنشاء شكل مستطيل في Word باستخدام Java – دليل كامل](/words/english/java/images-shapes/create-rectangle-shape-in-word-with-java-full-guide/)
- [إضافة ظل إلى الشكل في Word – دليل Aspose.Words الكامل](/words/english/java/images-shapes/add-shadow-to-shape-in-word-complete-aspose-words-guide/)
- [إنشاء مستند Word بـ Java – إضافة شكل مستطيل مع تأثير الظل](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}