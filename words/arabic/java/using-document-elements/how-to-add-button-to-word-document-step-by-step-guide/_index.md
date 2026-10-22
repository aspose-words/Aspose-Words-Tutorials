---
category: general
date: 2026-07-20
description: كيفية إضافة زر إلى مستند Word باستخدام Aspose.Words. تعلّم إدراج زر Forms2OleControl
  باستخدام DocumentBuilder في دقائق.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to add button to word document
- Forms2OleControl
- DocumentBuilder
- insertForms2OleControl
- Word automation
language: ar
lastmod: 2026-07-20
og_description: كيفية إضافة زر إلى مستند Word باستخدام Aspose.Words. اتبع هذا الدليل
  العملي لتضمين زر CommandButton من Forms2OleControl باستخدام Java.
og_image_alt: Screenshot of a Word document with a clickable button added via Aspose.Words
  (how to add button to word document)
og_title: كيفية إضافة زر إلى مستند Word – دليل Aspose.Words الكامل
schemas:
- author: Aspose
  dateModified: '2026-07-20'
  description: How to add button to Word document using Aspose.Words. Learn to insert
    a Forms2OleControl button with DocumentBuilder in minutes.
  headline: How to Add Button to Word Document – Step‑by‑Step Guide
  type: TechArticle
- description: How to add button to Word document using Aspose.Words. Learn to insert
    a Forms2OleControl button with DocumentBuilder in minutes.
  name: How to Add Button to Word Document – Step‑by‑Step Guide
  steps:
  - name: '`Forms2OleControlType.COMMANDBUTTON` – tells Word we want a button.'
    text: '`Forms2OleControlType.COMMANDBUTTON` – tells Word we want a button.'
  - name: '`100` – width in points (≈1.39 inches).'
    text: '`100` – width in points (≈1.39 inches).'
  - name: '`30` – height in points (≈0.42 inches).'
    text: '`30` – height in points (≈0.42 inches).'
  type: HowTo
tags:
- Aspose.Words
- Java
- Office Automation
title: كيفية إضافة زر إلى مستند Word – دليل خطوة بخطوة
url: /ar/java/using-document-elements/how-to-add-button-to-word-document-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# كيفية إضافة زر إلى مستند Word – دليل Aspose.Words الكامل

هل تساءلت يومًا **كيفية إضافة زر إلى مستند Word** دون فتح واجهة المستخدم والنقر هنا وهناك؟ لست وحدك. يحتاج العديد من المطورين إلى تضمين عناصر تحكم تفاعلية برمجيًا — فكر في زر “إرسال” في قالب يُملأ لاحقًا من قبل المستخدم النهائي. الخبر السار؟ باستخدام Aspose.Words for Java يمكنك القيام بذلك في بضع أسطر.

في هذا الدرس سنستعرض الخطوات الدقيقة لإدراج `Forms2OleControl` من النوع **CommandButton** باستخدام `DocumentBuilder`. في النهاية ستحصل على ملف `.docx` جاهز للاستخدام يظهر زرًا قابلًا للنقر مكتوبًا عليه “Click Me”. لا غموض، فقط كود واضح وتفسير لكل سطر.

## ما ستتعلمه

- كيفية إنشاء مستند Word جديد من الصفر.  
- كيفية استخدام **DocumentBuilder** لوضع **Forms2OleControl**.  
- لماذا يجب ضبط تسمية الزر وحجمه كما نفعل.  
- كيفية حفظ النتيجة والتحقق منها.  
- المشكلات الشائعة (مثل المكتبات المفقودة، أنواع التحكم غير المدعومة) وكيفية تجنبها.  

**المتطلبات المسبقة** – تحتاج إلى Java 8+ (أو أحدث) ومكتبة Aspose.Words for Java (الإصدار 23.12 أو لاحق). سيجعل IDE مثل IntelliJ IDEA أو Eclipse الأمور أسهل، لكن أي محرر نصوص سيعمل.

---

## الخطوة 1: إعداد المشروع واستيراد التبعيات

قبل تشغيل أي كود، يجب أن يعرف Maven (أو Gradle) من أين يجلب Aspose.Words. أضف هذا المقتطف إلى ملف `pom.xml` الخاص بك:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.12</version>
</dependency>
```

إذا كنت تفضّل Gradle، فالمكافئ هو:

```gradle
implementation 'com.aspose:aspose-words:23.12'
```

> **نصيحة احترافية:** استخدم أحدث إصدار؛ الإصدارات القديمة قد تفتقر إلى API الخاص بـ `Forms2OleControl`.

بمجرد حل التبعيات، ستكون جاهزًا لكتابة كود Java.

---

## الخطوة 2: إنشاء مستند جديد والحصول على DocumentBuilder

فئة `Document` تمثل حزمة `.docx` بالكامل، بينما `DocumentBuilder` هو الفرشاة التي تستخدمها لرسم المحتوى عليها. فكر في `DocumentBuilder` كـ “المؤشر” الذي يعرف أين يجب أن يذهب العنصر التالي.

```java
import com.aspose.words.*;

public class AddButtonExample {
    public static void main(String[] args) throws Exception {
        // Step 2: Create a new blank document
        Document doc = new Document();

        // Obtain a DocumentBuilder tied to the document
        DocumentBuilder builder = new DocumentBuilder(doc);
```

**لماذا هذا مهم:** إنشاء `Document` جديد يمنحك لوحة رسم نظيفة. يقوم الـ builder تلقائيًا بالإشارة إلى الفقرة الأولى، لذا لا تحتاج إلى إدارة الأقسام أو الصفحات يدويًا.

---

## الخطوة 3: إدراج Forms2OleControl من النوع CommandButton

الآن يأتي نجم العرض: `insertForms2OleControl`. هذه الطريقة تنشئ تحكم OLE (Object Linking and Embedding) يعامله Word كعنصر نموذج. سنمرّر ثلاثة معطيات:

1. `Forms2OleControlType.COMMANDBUTTON` – يُخبر Word أننا نريد زرًا.  
2. `100` – العرض بالنقاط (≈1.39 بوصة).  
3. `30` – الارتفاع بالنقاط (≈0.42 بوصة).  

```java
        // Step 3: Insert a CommandButton with specific dimensions
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON, 100, 30);
```

**كيف يعمل:** في الخلفية، يقوم Aspose.Words بإنشاء XML المناسب في الجزء `word/document.xml`، مشيرًا إلى كائن OLE. الأبعاد التي تزودها تُحترم من قبل محرك تخطيط Word، لذا يظهر الزر بالضبط حيث يقع مؤشر الـ builder.

---

## الخطوة 4: ضبط التسمية (النص) على الزر

زر بدون تسمية يسبب ارتباكًا — تخيّل زر مصعد صامت. طريقة `setCaption` تضبط النص الظاهر:

```java
        // Step 4: Define the button's label
        commandButton.setCaption("Click Me");
```

يمكنك تغيير التسمية إلى أي شيء: “Submit”، “Approve”، أو حتى سلسلة محلية. تُخزن التسمية في خصائص كائن OLE، لذا سيعرضها Word أصليًا.

---

## الخطوة 5: حفظ المستند والتحقق من النتيجة

أخيرًا، اكتب الملف إلى القرص. اختر مجلدًا لديك صلاحية كتابة فيه؛ وإلا ستواجه `IOException`.

```java
        // Step 5: Persist the document
        String outputPath = "output/button-demo.docx";
        doc.save(outputPath);
        System.out.println("Document saved to: " + outputPath);
    }
}
```

افتح `button-demo.docx` في Microsoft Word. يجب أن ترى زرًا مكتوبًا عليه **Click Me** موضعه في أعلى المستند. النقر عليه في Word سيُفعّل سلوك OLE الافتراضي (عادةً رسالة placeholder، ما لم تقم بربط ماكرو).

---

## الحالات الخاصة الشائعة وكيفية التعامل معها

| الحالة | لماذا يحدث | الحل |
|-----------|----------------|-----|
| **غياب نوع `Forms2OleControl`** | إصدارات Aspose.Words القديمة لم تُظهر هذا الـ enum. | قم بالترقية إلى 23.12+ أو أحدث. |
| **الزر يظهر كصورة** | إعدادات أمان Word تحظر عناصر OLE. | فعّل “Trust access to the VBA project object model” في مركز الثقة، أو استخدم ملف `.docm` يدعم الماكرو. |
| **الحجم غير صحيح** | خلط بين النقاط والبكسل. | تذكّر أن 1 نقطة = 1/72 بوصة. عدّل القيم وفقًا لذلك. |
| **حفظ يرفع `FileNotFoundException`** | المسار غير موجود. | تأكد من إنشاء الدليل (`output/`) قبل `doc.save`. استخدم `new File("output").mkdirs();`. |

---

## توسيع المثال: إضافة أزرار متعددة أو عناصر تحكم أخرى

إذا كنت بحاجة إلى أكثر من زر واحد، ببساطة حرّك مؤشر الـ builder باستخدام `builder.moveTo` أو `builder.writeln()` قبل استدعاء `insertForms2OleControl` مرة أخرى.

```java
        // Add a second button below the first
        builder.writeln(); // moves to a new paragraph
        Forms2OleControl secondButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON, 120, 35);
        secondButton.setCaption("Submit");
```

يمكنك أيضًا إدراج **CheckBox** أو **ComboBox** أو **ListBox** عن طريق استبدال `Forms2OleControlType.COMMANDBUTTON` بالقيمة المناسبة من الـ enum (`CHECKBOX`، `COMBOBOX`، إلخ). تُطبق نفس معايير العرض/الارتفاع.

---

## كيف يتناسب هذا مع سير عمل أتمتة Word الأكبر

- **إنشاء القوالب:** بناء قالب عقد يتضمن زر “Approve” للموافقة اللاحقة.  
- **التقارير:** توليد تقرير يومي يحتوي على زر “Refresh Data” يُفعّل ماكرو.  
- **توزيع النماذج:** إرسال استبيان مع عناصر تحكم تفاعلية مُعبأة مسبقًا.  

جميع هذه السيناريوهات تستفيد من نهج **أتمتة Word** الذي عرضناه. من خلال تضمين عناصر التحكم برمجيًا، تلغي الحاجة إلى التحرير اليدوي وتقلل الأخطاء البشرية.

---

## الكود الكامل (جاهز للنسخ واللصق)

```java
import com.aspose.words.*;

public class AddButtonExample {
    public static void main(String[] args) throws Exception {
        // Create a new blank document
        Document doc = new Document();

        // Obtain a DocumentBuilder for the document
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a CommandButton (width: 100pt, height: 30pt)
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON, 100, 30);

        // Set the button caption
        commandButton.setCaption("Click Me");

        // Optionally add a second button
        builder.writeln(); // new paragraph
        Forms2OleControl secondButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON, 120, 35);
        secondButton.setCaption("Submit");

        // Save the document
        String outputPath = "output/button-demo.docx";
        new java.io.File("output").mkdirs(); // ensure directory exists
        doc.save(outputPath);
        System.out.println("Document saved to: " + outputPath);
    }
}
```

**الناتج المتوقع:** عند فتح `output/button-demo.docx` في Microsoft Word، سترى زرين — “Click Me” و “Submit” — مكدسين عموديًا في أعلى الملف.

---

## الخلاصة

أجبنا على **كيفية إضافة زر إلى مستند Word** باستخدام Aspose.Words for Java، خطوة بخطوة. بدءًا من `Document` فارغ، استخدمنا **DocumentBuilder** لإدراج `Forms2OleControl` من النوع **CommandButton**، ضبطنا تسمية صديقة، وحفظنا النتيجة. النمط قابل للتوسع لإضافة عدة عناصر تحكم ويتكامل بسلاسة مع خطوط أنابيب **أتمتة Word** الأوسع.

هل أنت مستعد للتحدي التالي؟ جرّب استبدال الزر بـ **CheckBox**، أو اربط ماكروًا ليتفاعل عندما ينقر المستخدم الزر في ملف `.docm`. النمط نفسه يُطبق — فقط غيّر الـ enum وعدّل التسمية.

إذا واجهت أي صعوبات، تحقق مرة أخرى من نسخة المكتبة وصلاحيات المجلد الهدف. لا تتردد في ترك تعليق أدناه بأسئلتك أو مشاركة حالتك الخاصة. برمجة سعيدة!

## ما الذي يجب أن تتعلمه بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات التي تم توضيحها في هذا الدليل. كل مورد يتضمن أمثلة كود كاملة مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف نهج تنفيذ بديلة في مشاريعك.

- [How to create form fields and add content using DocumentBuilder in Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Insert Inline Image in Word Document using Aspose.Words](/words/english/net/add-content-using-document-builder/insert-inline-image/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}