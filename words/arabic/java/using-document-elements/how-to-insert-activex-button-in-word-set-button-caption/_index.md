---
category: general
date: 2026-07-26
description: كيفية إدراج زر ActiveX في مستند Word باستخدام Aspose.Words – تعلم تعيين
  تسمية الزر، وموقعه، وحجمه في بضع سطور فقط.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to insert activex
- set button caption
language: ar
lastmod: 2026-07-26
og_description: كيفية إدراج زر ActiveX في مستند Word باستخدام Aspose.Words. اتبع هذا
  الدليل خطوة بخطوة لتعيين تسمية الزر، وموقعه، وحجمه.
og_image_alt: Screenshot of a Word document showing an inserted ActiveX CommandButton
  with a custom caption
og_title: كيفية إدراج زر ActiveX في Word – دليل سريع
schemas:
- author: Aspose
  dateModified: '2026-07-26'
  description: How to insert ActiveX button in a Word document using Aspose.Words
    – learn to set button caption, position, and size in just a few lines.
  headline: How to Insert ActiveX Button in Word – Set Button Caption
  type: TechArticle
tags:
- Aspose.Words
- Java
- ActiveX
- Word automation
- Document generation
title: كيفية إدراج زر ActiveX في Word – تعيين تسمية الزر
url: /ar/java/using-document-elements/how-to-insert-activex-button-in-word-set-button-caption/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# كيفية إدراج زر ActiveX في Word – تعيين تسمية الزر

هل تساءلت يومًا **كيفية إدراج ActiveX** في ملفات Word دون فتح الواجهة؟ لست وحدك. في العديد من التطبيقات المؤسسية تحتاج إلى زر قابل للنقر يشغّل ماكرو، والقيام بذلك برمجيًا يوفر ساعات. يوضح لك هذا الدليل بالضبط **كيفية إدراج ActiveX** CommandButton باستخدام Aspose.Words for Java، و—نعم—كيفية **تعيين تسمية الزر** حتى يعرف المستخدم ما الذي يجب النقر عليه.

سنستعرض العملية بالكامل: من إعداد المكتبة، إنشاء مستند جديد، إضافة الزر، تعديل حجمه وموقعه، إعطائه تسمية واضحة، وأخيرًا حفظ الملف. في النهاية ستحصل على ملف `.docx` قابل للتشغيل يفتح في Word مع زر ActiveX يعمل بالكامل جاهز لتفعيل الماكرو الخاص بك.

---

## ما ستتعلمه

- تثبيت وإضافة مرجع Aspose.Words في مشروع Java.  
- إنشاء `Document` و `DocumentBuilder` جديدين.  
- **Insert ActiveX** CommandButton control باستخدام سطر واحد من الشيفرة.  
- **Set button caption**، تعديل موقعه، وتعريف أبعاده.  
- حفظ المستند وفتحه في Word لرؤية النتيجة.

لا تحتاج إلى خبرة سابقة في ActiveX؛ فقط معرفة أساسية بـ Java ونسخة من Aspose.Words.

## المتطلبات المسبقة

- Java 8 أو أحدث مثبت على جهازك.  
- Maven أو Gradle لإدارة الاعتمادات (سنظهر مقتطف Maven).  
- نسخة مرخصة أو تجريبية من **Aspose.Words for Java** (الإصدار التجريبي المجاني يكفي لهذا العرض).  
- Microsoft Word (أي نسخة حديثة) لاختبار الملف المُولد.

## الخطوة 1: إعداد Aspose.Words في مشروعك

أولًا، أضف تبعية Aspose.Words. إذا كنت تستخدم Maven، ضع هذا في ملف `pom.xml` الخاص بك:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.10</version> <!-- check for the latest version -->
</dependency>
```

يمكن لمستخدمي Gradle إضافة:

```gradle
implementation 'com.aspose:aspose-words:24.10'
```

بعد تشغيل سريع `mvn clean install` (أو `gradle build`) ستكون المكتبة على مسار الفئة الخاص بك وستكون جاهزًا للبرمجة.

## الخطوة 2: إنشاء مستند جديد وBuilder

`Document` يمثل ملف Word بالكامل، بينما `DocumentBuilder` يتيح لك تحريره. فكر في الـ Builder كقلم يرسم على لوحة جديدة.

```java
import com.aspose.words.*;

public class ActiveXButtonDemo {
    public static void main(String[] args) throws Exception {
        // Step 2: Initialize a blank document and a builder
        Document doc = new Document();                 // creates an empty .docx
        DocumentBuilder builder = new DocumentBuilder(doc);
```

لماذا نبدأ بمستند فارغ؟ يضمن لك التحكم الكامل في كل عنصر تضيفه، ولا توجد تنسيقات مخفية قد تفاجئك لاحقًا.

## الخطوة 3: إدراج عنصر التحكم ActiveX CommandButton

الآن نأتي إلى نجمة العرض. Aspose.Words يوفر الدالة `insertForms2OleControl` التي يمكنها وضع أي عنصر تحكم ActiveX تحدده. هنا نطلب **CommandButton**.

```java
        // Step 3: Insert a CommandButton ActiveX control
        Forms2OleControl commandBtn = builder.insertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON);
```

تُعيد الطريقة كائن `Forms2OleControl`، مما يمنحك وصولًا برمجيًا إلى خصائص الزر. هنا يصبح **how to insert activex** سطرًا واحدًا—دون الحاجة للتعامل مع واجهات COM منخفضة المستوى.

## الخطوة 4: تحديد الموقع، الحجم، وتعيين تسمية الزر

زر يطفو في وسط الصفحة ليس مفيدًا كثيرًا. تريد وضعه حيث يتوقعه المستخدمون، إعطائه حجمًا معقولًا، والأهم من ذلك—**set button caption** حتى يعرفوا ما سيحدث عند النقر.

```java
        // Step 4a: Position the button (coordinates are in points)
        commandBtn.setLeft(100);   // distance from the left margin
        commandBtn.setTop(150);    // distance from the top margin

        // Step 4b: Define width and height
        commandBtn.setWidth(120);
        commandBtn.setHeight(30);

        // Step 4c: Set the button caption (the text that appears on the button)
        commandBtn.setCaption("Click Me");
```

**لماذا هذه القيم؟** يستخدم Word النقاط (1 pt ≈ 1/72 inch). `100 pt` ≈ 1.4 إنش من اليسار، `150 pt` ≈ 2.1 إنش من الأعلى—تقريبًا مركز صفحة A4 القياسية. عدّلها لتناسب تخطيطك.

تعيين التسمية أمر حاسم؛ بدونها يبدو الزر كإطار فارغ. طريقة `setCaption` تقبل أي سلسلة نصية، لذا يمكنك ترجمتها لاحقًا إذا لزم الأمر.

## الخطوة 5: حفظ المستند

أخيرًا، احفظ المستند على القرص. يمكنك اختيار أي مجلد تريده؛ فقط تأكد من وجود المسار.

```java
        // Step 5: Save the document to a .docx file
        String outputPath = "C:/Temp/ActiveXButton.docx";
        doc.save(outputPath);
        System.out.println("Document saved to " + outputPath);
    }
}
```

عند فتح `ActiveXButton.docx` في Word، سترى زرًا موضوعًا بشكل جيد مُسمى **“Click Me.”** إذا نقرت عليه مرتين، سيطلب Word تمكين الماكرو (نظرًا لأن عناصر تحكم ActiveX تُعتبر ماكرو-مفعلة). من هناك يمكنك ربط روتين VBA بحدث `Click` للزر.

## حالات خاصة ونصائح قد تغفل عنها

- **تنسيق ماكرو‑مفعّل**: يقوم Word بتعطيل عناصر تحكم ActiveX في ملفات `.docx` العادية ما لم يُفعّل المستخدم الماكرو. إذا كنت بحاجة إلى أن يعمل الزر مباشرةً، فكر في حفظه كـ `.docm` (ماكرو‑مفعّل) باستخدام `doc.save(outputPath, SaveFormat.DOCM);`.
- **التوافق**: الإصدارات القديمة من Word (قبل 2007) تستخدم تنسيق `.doc` الثنائي. يمكن لـ Aspose.Words حفظه بهذا التنسيق، لكن قد تُظهر خصائص العنصر بشكل مختلف قليلًا.
- **إعدادات الأمان**: بعض بيئات الشركات تقفل ActiveX. إذا لم يظهر الزر، تحقق من مركز الثقة في Word → إعدادات ActiveX.
- **أزرار متعددة**: هل تريد أكثر من زر؟ فقط كرّر استدعاء `insertForms2OleControl` وعدّل قيم `Left`/`Top` لكل زر. احتفظ بالكائنات المرجعة لتتمكن من تعيين تسمية منفصلة لكل زر.
- **تنسيق التسمية**: التسمية ترث الخط الافتراضي. لتغييرها، تحتاج إلى تعديل XML الأساسي أو تطبيق نمط Word بعد الإدراج—خارج نطاق هذا الدليل السريع، لكن يمكن تحقيقه باستخدام API `ParagraphFormat` في Aspose.Words.

## مثال كامل يعمل

فيما يلي الفئة الكاملة الجاهزة للتنفيذ في Java. انسخها والصقها في بيئة التطوير IDE الخاصة بك، عدّل مسار الإخراج، واضغط **Run**.

```java
import com.aspose.words.*;

public class ActiveXButtonDemo {
    public static void main(String[] args) throws Exception {
        // Create a new blank document
        Document doc = new Document();

        // Obtain a DocumentBuilder to edit the document
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert an ActiveX CommandButton control
        Forms2OleControl commandBtn = builder.insertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON);

        // Position the button (points from the left/top margins)
        commandBtn.setLeft(100);
        commandBtn.setTop(150);

        // Set size (width × height in points)
        commandBtn.setWidth(120);
        commandBtn.setHeight(30);

        // Set the button caption – this is the visible text
        commandBtn.setCaption("Click Me");

        // Save the document; you may also use SaveFormat.DOCM for macro‑enabled files
        String outputPath = "C:/Temp/ActiveXButton.docx";
        doc.save(outputPath);
        System.out.println("Document saved to " + outputPath);
    }
}
```

**الناتج المتوقع**: بعد التنفيذ، يطبع الطرفية موقع الحفظ. فتح الملف المُولد في Word يظهر زرًا موضوعًا تقريبًا في وسط الصفحة، مُسمى “Click Me”. النقر عليه سيُطلق حدث النقر القياسي لـ ActiveX (ستحتاج إلى إرفاق ماكرو VBA للرد).

## الخلاصة

أنت الآن تعرف **how to insert ActiveX** CommandButton في مستند Word برمجيًا باستخدام Aspose.Words، ورأيت بالضبط كيفية **set button caption**، وتحديد موقع وحجم العنصر. هذه الطريقة تُزيل العمل اليدوي على الواجهة، وتندمج بسلاسة في مولدات التقارير الآلية، وتمنحك تحكمًا كاملاً في الـ 

## ماذا يجب أن تتعلم بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات التي تم توضيحها في هذا الدليل. كل مصدر يتضمن أمثلة شيفرة كاملة مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف أساليب تنفيذ بديلة في مشاريعك.

- [Insert Shapes in Word Documents Using Aspose.Words for .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Insert Inline Image in Word Document using Aspose.Words](/words/english/net/add-content-using-document-builder/insert-inline-image/)
- [Insert an Image into Word Document Header | Aspose.Words for .NET](/words/english/net/header-footer-formatting/insert-image/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}