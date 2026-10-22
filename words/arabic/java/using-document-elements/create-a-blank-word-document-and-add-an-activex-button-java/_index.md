---
category: general
date: 2026-10-16
description: إنشاء مستند Word فارغ باستخدام Java وتعلم كيفية إضافة زر ActiveX، وتعيين
  عنوانه، وضبط أبعاده باستخدام Aspose.Words.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- add activex button
- set button caption
- set button dimensions
language: ar
lastmod: 2026-10-16
og_description: إنشاء مستند Word فارغ باستخدام Java، ثم إضافة زر ActiveX، وتعيين تسميته،
  وتحديد أبعاده باستخدام Aspose.Words.
og_image_alt: Screenshot showing a blank Word document with an ActiveX button inserted
og_title: إنشاء مستند Word فارغ وتضمين زر ActiveX – دليل Java
schemas:
- author: Aspose
  dateModified: '2026-10-16'
  description: Create a blank Word document with Java and learn how to add an ActiveX
    button, set its caption, and adjust its dimensions using Aspose.Words.
  headline: Create a blank Word document and add an ActiveX button (Java)
  type: TechArticle
tags:
- Aspose.Words
- Java
- ActiveX
title: إنشاء مستند Word فارغ وإضافة زر ActiveX (Java)
url: /ar/java/using-document-elements/create-a-blank-word-document-and-add-an-activex-button-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# إنشاء مستند Word فارغ وإضافة زر ActiveX (Java)

إذا كنت بحاجة إلى **إنشاء مستند Word فارغ** برمجيًا، يوضح لك هذا الدليل كيفية القيام بذلك باستخدام Java و Aspose.Words. ستتعلم أيضًا كيفية **إضافة زر ActiveX**، **تعيين تسمية الزر**، و **تحديد أبعاد الزر** بحيث يظهر التحكم تمامًا كما تتوقع.

يغطي هذا البرنامج التعليمي:

* تهيئة ملف Word فارغ باستخدام Aspose.Words for Java.  
* إدراج عنصر تحكم ActiveX من نوع `CommandButton`.  
* ضبط تسمية الزر وحجمه.  
* حفظ الملف النهائي بامتداد `.docx`.

يجب أن تكون لديك معرفة أساسية بـ Java وإصدار حديث من مكتبة Aspose.Words for Java (الكود يعمل مع الإصدار 23.9 وما بعده). لا توجد تبعيات إضافية مطلوبة.

![Create a blank Word document with an ActiveX button](/images/activex-button-example.png){: .align-center alt="إنشاء مستند Word فارغ مع زر ActiveX"}

## إنشاء مستند Word فارغ باستخدام Aspose.Words

الخطوة الأولى هي إنشاء كائن `Document` فارغ. يمثل هذا الكائن ملف Word بالكامل في الذاكرة ويوفر فئة `DocumentBuilder` للتحرير.

```java
import com.aspose.words.*;

public class ActiveXButtonDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document
        Document doc = new Document();               // creates an empty .docx structure
        DocumentBuilder builder = new DocumentBuilder(doc);
        
        // The rest of the steps follow here...
```

**لماذا هذا مهم:**  
إنشاء مستند فارغ يمنحك لوحة رسم نظيفة، مما يجنب أي أنماط أو أقسام مخفية قد تتداخل مع حسابات التخطيط لاحقًا.

## إضافة زر ActiveX إلى المستند

تتيح لك Aspose.Words تضمين عناصر تحكم ActiveX القديمة عبر فئة `Forms2OleControl`. يقوم الكود التالي بإدراج عنصر تحكم `CommandButton` في موضع المؤشر الحالي.

```java
        // Step 2: Insert an ActiveX CommandButton control
        Forms2OleControl commandButton = builder.insertForms2OleControl();

        // Define the exact ActiveX class name (CommandButton)
        commandButton.setOleClassName("Forms.CommandButton.1");
```

**نصيحة:** قيمة `setOleClassName` `"Forms.CommandButton.1"` هي ProgID للزر القياسي في Microsoft Forms. استخدام ProgID مختلف (مثل `"Forms.CheckBox.1"`) سيؤدي إلى إدراج نوع تحكم مختلف.

## تعيين تسمية الزر

التسمية هي النص الذي يظهر على وجه الزر. يمكنك تغييرها في أي وقت قبل حفظ المستند.

```java
        // Step 3: Set the button's caption
        commandButton.setCaption("Click Me");
```

**لماذا تحتاج هذا:** المستخدمون لا يفهمون التحكم إلا عندما يكون هدفه واضحًا. تعيين تسمية ذات معنى يحسن من قابلية الاستخدام، خاصةً عندما يُفتح المستند في Word على نظام Windows.

## تعيين أبعاد الزر

يتم تحديد الموضع والحجم بالنقاط (نقطة واحدة = 1/72 بوصة). عدّل القيم لتناسب تخطيطك.

```java
        // Step 4: Define button size and location
        commandButton.setLeft(100);    // distance from the left edge of the page
        commandButton.setTop(200);     // distance from the top edge of the page
        commandButton.setWidth(120);   // width of the button
        commandButton.setHeight(30);   // height of the button
```

**الاختلافات الشائعة:**

| السيناريو | التعديل |
|----------|----------|
| زر أكبر لشاشات اللمس | زيادة `setWidth` و `setHeight` بنسب متناسبة |
| زر مركزي في الصفحة | حساب `left = (pageWidth - width) / 2` |
| عدة أزرار في عمود | زيادة `setTop` لكل زر جديد |

## حفظ المستند الذي يحتوي على زر ActiveX

أخيرًا، اكتب المستند إلى القرص. يحافظ تنسيق `.docx` على عنصر التحكم ActiveX لإصدارات Windows من Microsoft Word.

```java
        // Step 5: Save the document
        doc.save("ActiveXCommandButton.docx");
    }
}
```

**النتيجة المتوقعة:** فتح `ActiveXCommandButton.docx` في Word (Windows) يعرض صفحة فارغة مع زر قابل للنقر يحمل التسمية **Click Me** موضعه 100 pt من الهامش الأيسر و200 pt من الهامش العلوي.

## مثال كامل قابل للتنفيذ

انسخ الفئة الكاملة أدناه إلى بيئة التطوير المتكاملة (IDE) الخاصة بك، أضف ملف JAR الخاص بـ Aspose.Words for Java إلى مسار الفئة (classpath) للمشروع، ثم شغّله.

```java
import com.aspose.words.*;

public class ActiveXButtonDemo {
    public static void main(String[] args) throws Exception {
        // Create a new blank document
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert an ActiveX CommandButton control
        Forms2OleControl commandButton = builder.insertForms2OleControl();
        commandButton.setOleClassName("Forms.CommandButton.1");

        // Set button caption
        commandButton.setCaption("Click Me");

        // Set button dimensions and position
        commandButton.setLeft(100);    // points from left edge
        commandButton.setTop(200);     // points from top edge
        commandButton.setWidth(120);   // width in points
        commandButton.setHeight(30);   // height in points

        // Save the document
        doc.save("ActiveXCommandButton.docx");
    }
}
```

تشغيل البرنامج ينتج ملف `ActiveXCommandButton.docx` في دليل العمل. افتحه باستخدام Microsoft Word (Windows) للتحقق من أن الزر يظهر تمامًا كما تم تكوينه.

## لماذا يُنصح بهذه الطريقة

* **البساطة:** يتم استخدام واجهة برمجة التطبيقات الأساسية لـ Aspose.Words فقط؛ لا حاجة إلى COM interop أو مكتبات إضافية.  
* **القابلية للنقل:** يعمل الكود على أي منصة تدعم Java، رغم أن عنصر التحكم ActiveX نفسه يعمل فقط على إصدارات Word لنظام Windows.  
* **قابلية الصيانة:** جميع الخصائص (التسمية، الأبعاد، الموضع) تُضبط عبر طرق واضحة ذات توثيق ذاتي، مما يجعل التعديلات المستقبلية سهلة.

## المشكلات الشائعة وكيفية تجنّبها

| المشكلة | الحل |
|---------|------|
| الزر لا يظهر في Word على macOS أو Linux | عناصر التحكم ActiveX مخصصة لنظام Windows فقط. استخدم عنصر تحكم مختلف (مثل content control) للمستندات متعددة المنصات. |
| التسمية مقطوعة | تأكد من أن عرض الزر كافٍ للنص؛ زد `setWidth` أو استخدم تسمية أقصر. |
| الزر يتداخل مع محتوى آخر | عدّل قيم `setTop` و `setLeft`، أو أدخل فقرة جديدة قبل التحكم لمنحه مساحة خاصة. |

## الخطوات التالية

الآن بعد أن أصبحت قادرًا على **إنشاء مستند Word فارغ**، **إضافة زر ActiveX**، **تعيين تسمية الزر**، و **تحديد أبعاد الزر**، يمكنك استكشاف:

* إضافة كود معالجة الأحداث عبر ماكرو VBA (يتطلب تضمين وحدة ماكرو).  
* إدراج عدة عناصر تحكم في تخطيط جدولي لإنشاء مستندات شبيهة بالنماذج.  
* استخدام واجهات **FormField** في Aspose.Words لحلول نماذج متعددة المنصات.

جرّب أحجامًا، مواضع، وتسمية مختلفة لتناسب تصميم مستندك الخاص. برمجة سعيدة!

## ماذا يجب أن تتعلمه بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات التي تم توضيحها في هذا الدليل. كل مصدر يتضمن أمثلة شاملة مع شروح خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف أساليب تنفيذ بديلة في مشاريعك.

- [إنشاء مستند Word باستخدام Java – إضافة شكل مستطيل مع تأثير الظل](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [كيفية إنشاء حقول نموذج وإضافة محتوى باستخدام DocumentBuilder في Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [إضافة علامة مائية إلى مستند باستخدام Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-watermarks-to-documents/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}