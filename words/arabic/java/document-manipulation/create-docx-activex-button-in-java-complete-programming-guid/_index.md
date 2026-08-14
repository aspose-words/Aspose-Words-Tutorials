---
category: general
date: 2026-08-14
description: إنشاء زر ActiveX في ملف docx باستخدام Java وAspose.Words. تعلّم كيفية
  إضافة زر نموذج في Word برمجيًا وحفظ المستند.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create docx ActiveX button
- add form button word
language: ar
lastmod: 2026-08-14
og_description: إنشاء زر ActiveX في ملف docx باستخدام Java وAspose.Words. يوضح لك
  هذا الدليل كيفية إضافة زر نموذج في Word، وتكوينه، وحفظ الملف.
og_image_alt: Screenshot of a Word document containing an ActiveX CommandButton created
  with Java
og_title: إنشاء زر ActiveX لملف docx في Java – دليل خطوة بخطوة
schemas:
- author: Aspose
  dateModified: '2026-08-14'
  description: Create docx ActiveX button in Java with Aspose.Words. Learn how to
    add a form button in Word programmatically and save the document.
  headline: Create docx ActiveX button in Java – complete programming guide
  type: TechArticle
- description: Create docx ActiveX button in Java with Aspose.Words. Learn how to
    add a form button in Word programmatically and save the document.
  name: Create docx ActiveX button in Java – complete programming guide
  steps:
  - name: Set up the project and import Aspose.Words
    text: 'Add the Aspose.Words dependency to your `pom.xml` if you use Maven:'
  - name: Create a new blank document
    text: Instantiate a `Document` object, which represents an empty Word file ready
      to receive content.
  - name: Initialize a DocumentBuilder
    text: '`DocumentBuilder` provides a fluent interface for inserting text, images,
      and controls. Attach it to the document you just created.'
  - name: Insert an ActiveX CommandButton control
    text: Use the `insertForms2OleControl` method to embed an ActiveX `CommandButton`.
      This method returns a `Forms2OleControl` instance that you can further configure.
  - name: Configure the button’s properties
    text: Set the control’s name, caption, and layout attributes. These values determine
      how the button appears in Word and how you can reference it later via VBA or
      automation scripts.
  - name: Save the document
    text: Finally, write the document to disk. Use the `.docx` extension to keep the
      file in the modern Office Open XML format.
  type: HowTo
tags:
- ActiveX
- Java
- Aspose.Words
- Word automation
title: إنشاء زر ActiveX لملف docx في جافا – دليل برمجي كامل
url: /ar/java/document-manipulation/create-docx-activex-button-in-java-complete-programming-guid/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# إنشاء زر ActiveX في ملف docx باستخدام Java – دليل برمجة كامل

إذا كنت بحاجة إلى **إنشاء زر ActiveX في ملف docx** باستخدام Java، فإن هذا الدليل سيرشدك خلال العملية بالكامل. ستتعرف على كيفية إضافة زر نموذج في Word، وتكوين خصائصه، وإنتاج ملف .docx جاهز للاستخدام.

التعامل مع عناصر التحكم ActiveX هو متطلب شائع عند أتمتة نماذج Word القديمة. في هذا البرنامج التعليمي ستتعلم **إضافة زر نموذج إلى مستندات Word** باستخدام مكتبة Aspose.Words for Java، حتى تتمكن من تضمين عناصر تحكم تفاعلية دون تحرير يدوي.

## ما ستحتاجه

* Java 17 أو أحدث (الكود يُترجم مع الإصدارات السابقة، لكن يُنصح بـ Java 17).
* Aspose.Words for Java 23.10 أو أحدث – قم بتحميل ملف JAR من موقع Aspose أو أضف تبعية Maven.
* بيئة تطوير متكاملة (IntelliJ IDEA، Eclipse، أو VS Code) أو محرر نصوص بسيط وأدوات بناء سطر الأوامر.
* معرفة أساسية بصياغة Java وبرمجة الكائنات.

## كيفية إنشاء زر ActiveX في ملف docx باستخدام Aspose.Words

الخطوات التالية توضح التسلسل الدقيق المطلوب **لإنشاء زر ActiveX في ملف docx** وإدراجه في مستند Word.

### الخطوة 1: إعداد المشروع واستيراد Aspose.Words

أضف تبعية Aspose.Words إلى ملف `pom.xml` إذا كنت تستخدم Maven:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.10</version>
    <classifier>jdk17</classifier>
</dependency>
```

أو، إذا كنت تفضّل Gradle:

```gradle
implementation 'com.aspose:aspose-words:23.10:jdk17'
```

بعد حل التبعية، استورد الفئات المطلوبة في ملف مصدر Java الخاص بك:

```java
import com.aspose.words.Document;
import com.aspose.words.DocumentBuilder;
import com.aspose.words.forms.Forms2OleControl;
import com.aspose.words.forms.Forms2OleControlType;
```

تتيح لك هذه الاستيرادات الوصول إلى `Document` و `DocumentBuilder` وواجهة برمجة التطبيقات `Forms2OleControl` المستخدمة لإدراج عناصر تحكم ActiveX.

### الخطوة 2: إنشاء مستند فارغ جديد

أنشئ كائن `Document`، الذي يمثل ملف Word فارغ جاهز لتلقي المحتوى.

```java
// Step 2: Create a new blank document
Document document = new Document();
```

إنشاء المستند أولاً يضمن أن المُنشئ اللاحق يعمل على لوحة نظيفة.

### الخطوة 3: تهيئة DocumentBuilder

`DocumentBuilder` يوفر واجهة سلسة لإدراج النصوص، الصور، والعناصر التحكم. اربطه بالمستند الذي أنشأته للتو.

```java
// Step 3: Initialize a DocumentBuilder to construct the document content
DocumentBuilder builder = new DocumentBuilder(document);
```

المُنشئ يتتبع موضع المؤشر الحالي داخل المستند، لذا يتم الإدراج التالي بالضبط حيث تحتاجه.

### الخطوة 4: إدراج عنصر تحكم ActiveX CommandButton

استخدم طريقة `insertForms2OleControl` لتضمين ActiveX `CommandButton`. تُعيد هذه الطريقة كائن `Forms2OleControl` يمكنك تكوينه لاحقًا.

```java
// Step 4: Insert an ActiveX CommandButton control into the document
Forms2OleControl commandButton = builder.insertForms2OleControl(
        Forms2OleControlType.COMMAND_BUTTON);
```

في هذه المرحلة يحتوي ملف .docx على عنصر نائب للزر، لكنه لا يمتلك عنوانًا مرئيًا أو حجمًا بعد.

### الخطوة 5: تكوين خصائص الزر

حدد اسم العنصر، العنوان، وسمات التخطيط. تحدد هذه القيم كيفية ظهور الزر في Word وكيفية الإشارة إليه لاحقًا عبر VBA أو سكريبتات الأتمتة.

```java
// Step 5: Configure the button's properties (name, caption, size, and position)
commandButton.setName("btnSubmit");          // internal name used by VBA
commandButton.setCaption("Submit");          // text shown on the button
commandButton.setTop(100);                  // distance from the top of the page (points)
commandButton.setLeft(150);                 // distance from the left margin (points)
commandButton.setWidth(80);                 // button width (points)
commandButton.setHeight(30);                // button height (points)
```

> **نصيحة احترافية:** يقيس Word المواقع بالنقاط (1 pt ≈ 1/72 in). عدّل `setTop` و `setLeft` لمحاذاة الزر مع المحتوى المحيط.

### الخطوة 6: حفظ المستند

أخيرًا، احفظ المستند إلى القرص. استخدم امتداد `.docx` للحفاظ على الملف بصيغة Office Open XML الحديثة.

```java
// Step 6: Save the document containing the ActiveX button
String outputPath = "C:/temp/ActiveXButton.docx";
document.save(outputPath);
System.out.println("Document saved to " + outputPath);
```

عند فتح الملف الناتج في Microsoft Word، ستظهر زر **Submit** في الإحداثيات التي حددتها. النقر على الزر في Word لن يُنفّذ أي إجراء ما لم تُرفق كود VBA، لكن العنصر يعمل بالكامل في سير عمل يعتمد على النماذج.

## أسئلة شائعة وحالات خاصة

| السؤال | الإجابة |
|----------|--------|
| **هل أحتاج إلى نسخة خاصة من Word؟** | يتم دعم عناصر التحكم ActiveX في نسخة سطح المكتب من Microsoft Word على نظام Windows. وهي غير متوفرة في Word لنظام Mac أو Word Online. |
| **هل يمكنني استخدام ذلك مع ملفات `.doc`؟** | نعم. احفظ المستند بامتداد `.doc` (`document.save("ActiveXButton.doc")`). نفس API يعمل مع الصيغة الثنائية القديمة. |
| **ماذا إذا لم يظهر الزر؟** | تأكد من أن **File → Options → Trust Center → Trust Center Settings → ActiveX Settings** يسمح بعناصر التحكم ActiveX. كما تحقق من أن المستند ليس مفتوحًا في “Protected View”. |
| **هل يمكنني إضافة عناصر تحكم ActiveX أخرى؟** | بالتأكيد. استبدل `Forms2OleControlType.COMMAND_BUTTON` بـ `Forms2OleControlType.CHECK_BOX` أو `RADIO_BUTTON`، إلخ. |
| **هل هناك حد لحجم العنصر؟** | حجم العنصر محدود فقط بتخطيط الصفحة. الأبعاد الكبيرة جدًا قد تتسبب في تجاوز التخطيط. |

## مثال كامل قابل للتنفيذ

فيما يلي فئة Java كاملة يمكنك نسخها، تجميعها، وتشغيلها. تتضمن جميع الاستيرادات، الدالة main، وتعليقات داخلية للتوضيح.

```java
package com.example.wordactive;

import com.aspose.words.Document;
import com.aspose.words.DocumentBuilder;
import com.aspose.words.forms.Forms2OleControl;
import com.aspose.words.forms.Forms2OleControlType;

public class ActiveXButtonDemo {
    public static void main(String[] args) {
        try {
            // Create a new blank document
            Document document = new Document();

            // Initialize DocumentBuilder
            DocumentBuilder builder = new DocumentBuilder(document);

            // Insert an ActiveX CommandButton control
            Forms2OleControl commandButton = builder.insertForms2OleControl(
                    Forms2OleControlType.COMMAND_BUTTON);

            // Configure button properties
            commandButton.setName("btnSubmit");
            commandButton.setCaption("Submit");
            commandButton.setTop(100);   // points from top
            commandButton.setLeft(150);  // points from left
            commandButton.setWidth(80);  // width in points
            commandButton.setHeight(30); // height in points

            // Save the document
            String outputPath = "ActiveXButton.docx";
            document.save(outputPath);
            System.out.println("Document saved successfully to " + outputPath);
        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}
```

**النتيجة المتوقعة:** بعد تشغيل البرنامج، يظهر `ActiveXButton.docx` في دليل العمل. عند فتحه في Microsoft Word يظهر زر **Submit** قابل للنقر موضعه بالقرب من أعلى‑يسار الصفحة الأولى.

## الخلاصة

أنت الآن تعرف كيف **إنشاء زر ActiveX في ملف docx** باستخدام Java ومكتبة Aspose.Words، ورأيت كيف **إضافة زر نموذج إلى مستندات Word** برمجيًا. الخطوات — إعداد المشروع، إنشاء مستند، إدراج العنصر، تكوين خصائصه، وحفظه — تغطي سير العمل بالكامل من البداية إلى النهاية.

بعد ذلك، قد ترغب في استكشاف:

* إضافة ماكرو VBA يستجيب للنقر على الزر.
* تضمين عناصر تحكم ActiveX أخرى مثل مربعات الاختيار أو قوائم الاختيار.
* أتمتة إنشاء نماذج متعددة الصفحات تحتوي على عدة عناصر تفاعلية.

لا تتردد في تجربة الأحجام، المواقع، والعناوين لتتناسب مع متطلبات تصميم النموذج الخاصة بك. برمجة سعيدة!

## ما الذي يجب أن تتعلمه بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات الموضحة في هذا الدليل. كل مورد يتضمن أمثلة شفرة كاملة مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف أساليب تنفيذ بديلة في مشاريعك.

- [كيفية إنشاء حقول نموذج وإضافة محتوى باستخدام DocumentBuilder في Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [كيفية تحميل HTML وحفظه كـ DOCX باستخدام Aspose.Words for Java](/words/english/java/document-loading-and-saving/loading-and-saving-html-documents/)
- [كيفية إنشاء مستندات PDF باستخدام Aspose.Words for Java | Document Processing API](/words/english/java/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}