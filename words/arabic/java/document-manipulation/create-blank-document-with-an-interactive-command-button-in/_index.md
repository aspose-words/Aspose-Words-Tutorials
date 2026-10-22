---
category: general
date: 2026-09-18
description: إنشاء مستند فارغ في جافا وإضافة زر ActiveX. تعلم كيفية إدراج زر أمر،
  بناء نموذج تفاعلي، وحفظ مستند Word.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank document
- create interactive form
- add activex button
- how to insert command button
- create word document
language: ar
lastmod: 2026-09-18
og_description: إنشاء مستند فارغ في Java وتضمين زر أمر ActiveX. اتبع هذا الدليل خطوة
  بخطوة لبناء نموذج تفاعلي وحفظ ملف Word.
og_image_alt: Screenshot of a Word document showing a clickable ActiveX command button
og_title: إنشاء مستند فارغ مع زر أمر تفاعلي في Word
schemas:
- author: Aspose
  dateModified: '2026-09-18'
  description: Create blank document in Java and add an ActiveX button. Learn how
    to insert command button, build an interactive form, and save a Word document.
  headline: Create blank document with an interactive command button in Word using
    Java
  type: TechArticle
- description: Create blank document in Java and add an ActiveX button. Learn how
    to insert command button, build an interactive form, and save a Word document.
  name: Create blank document with an interactive command button in Word using Java
  steps:
  - name: 'Load the existing document: `Document doc = new Document("ExistingForm.docx");`'
    text: 'Load the existing document: `Document doc = new Document("ExistingForm.docx");`'
  - name: 'Move the builder to the desired location: `builder.moveToParagraph(5, 0);
      // 6th paragraph, first node`'
    text: 'Move the builder to the desired location: `builder.moveToParagraph(5, 0);
      // 6th paragraph, first node`'
  - name: Insert the button as shown in Step 3.
    text: Insert the button as shown in Step 3.
  - name: Adjust the button’s `Top`/`Left` based on the paragraph’s layout.
    text: Adjust the button’s `Top`/`Left` based on the paragraph’s layout.
  type: HowTo
tags:
- Aspose.Words
- Java
- ActiveX
- Word automation
title: إنشاء مستند فارغ مع زر أمر تفاعلي في Word باستخدام Java
url: /ar/java/document-manipulation/create-blank-document-with-an-interactive-command-button-in/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# إنشاء مستند فارغ مع زر أمر تفاعلي في Word باستخدام Java

إذا كنت بحاجة إلى **create blank document** يحتوي على زر قابل للنقر، فإن هذا الدليل يوضح لك بالضبط كيفية القيام بذلك باستخدام Aspose.Words for Java. ستتعلم كيفية بناء نموذج تفاعلي، إضافة زر ActiveX، وأخيرًا حفظ ملف Word — كل ذلك في بضع خطوات مختصرة.

إدراج زر أمر يحول ملف .docx ثابت إلى نموذج وظيفي يمكن للمستخدمين النهائيين التفاعل معه مباشرة داخل Microsoft Word. يغطي هذا البرنامج التعليمي أيضًا **how to insert command button**، ويتعامل مع المشكلات الشائعة، ويوسع الحل للنماذج الأكثر تعقيدًا.

## المتطلبات المسبقة

* Java 17 أو أحدث (الكود يُترجم باستخدام JDK 17+)
* Aspose.Words for Java 23.9 أو أحدث – المكتبة توفر `Document`، `DocumentBuilder`، و`Forms2OleControl`.
* بيئة تطوير متكاملة (IDE) أو أداة بناء (Maven/Gradle) يمكنها إضافة تبعية Aspose.Words.
* معرفة أساسية بصياغة Java ومفاهيم مستندات Word.

```xml
<!-- Maven dependency -->
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
</dependency>
```

## الخطوة 1: إنشاء مستند فارغ

العملية الأولى هي إنشاء كائن `Document` جديد. هذا الكائن يمثل ملف Word فارغ جاهز لإضافة المحتوى.

```java
// Step 1: Create a new blank document
Document doc = new Document();
```

إنشاء مستند فارغ يمنحك لوحة نظيفة، وهو أمر أساسي عندما تريد **create word document** برمجيًا دون أي قالب مسبق.

## الخطوة 2: تهيئة DocumentBuilder

`DocumentBuilder` هو الفئة الأساسية لإضافة النصوص والجداول وعناصر التحكم في النماذج. يعمل على الـ `Document` الذي أنشأته للتو.

```java
// Step 2: Initialize a DocumentBuilder to construct the document content
DocumentBuilder builder = new DocumentBuilder(doc);
```

يحافظ الـ builder على نقطة الإدراج الحالية، لذا تؤثر الأوامر اللاحقة على الموقع الصحيح في الملف.

## الخطوة 3: إدراج عنصر تحكم زر أمر Forms2Ole

تُظهر Aspose.Words الفئة `Forms2OleControl` للتحكم في عناصر ActiveX. لإضافة **activex button**، تطلب نوع `COMMANDBUTTON` من الـ builder.

```java
// Step 3: Insert a Forms2Ole command button control
Forms2OleControl commandButton = builder.insertForms2OleControl(OleControlType.COMMANDBUTTON);
```

طريقة `insertForms2OleControl` تُدرج العنصر في موقع المؤشر الحالي للـ builder. نظرًا لأن العنصر هو كائن ActiveX، فهو يعمل فقط في نسخة سطح المكتب من Microsoft Word، وليس في Word Online.

## الخطوة 4: ضبط مظهر الزر وموقعه

يمكنك تعيين تسمية الزر، حجمه، وموقعه باستخدام الدوال setter الخاصة بالعنصر. قيم الموقع تُقاس بالنقاط (نقطة واحدة = 1/72 بوصة).

```java
// Step 4: Configure the button's appearance and position
commandButton.setCaption("Click Me");   // Text shown on the button
commandButton.setTop(100);              // Distance from the top edge of the page (points)
commandButton.setLeft(100);             // Distance from the left edge of the page (points)
commandButton.setWidth(120);            // Optional: set button width
commandButton.setHeight(30);            // Optional: set button height
```

*لماذا ضبط هذه الخصائص؟* ضبط `Top` و `Left` يضمن ظهور الزر في المكان المتوقع على الصفحة، بينما `Caption` يحدد النص الظاهر للمستخدم. إذا تخطيت ضبط العرض/الارتفاع، سيُعيّن Word أبعادًا افتراضية قد لا تتطابق مع التصميم الخاص بك.

### نصيحة احترافية
إذا كنت تخطط لإضافة عدة عناصر تحكم، استدعِ `builder.moveToDocumentEnd()` قبل كل إدراج لتجنب تداخل الكائنات.

## الخطوة 5: حفظ المستند مع زر الأمر المدمج

أخيرًا، احفظ المستند على القرص. يجب أن يكون امتداد الملف `.docx` (أو `.doc` لإصدارات Word القديمة) للحفاظ على عنصر التحكم ActiveX.

```java
// Step 5: Save the document with the embedded command button
String outputPath = "C:/temp/CommandButton.docx";
doc.save(outputPath);
System.out.println("Document saved to: " + outputPath);
```

عند فتح `CommandButton.docx` في Microsoft Word، سترى زرًا مُسمى **Click Me**. النقر عليه سيُطلق الإجراء الافتراضي لـ ActiveX (الذي لا يفعل شيئًا بشكل افتراضي). يمكنك لاحقًا إرفاق ماكرو أو سكريبت VBA لتحديد سلوك مخصص.

## كيفية إدراج زر أمر في نموذج موجود (اختياري)

إذا كان لديك بالفعل نموذج يحتوي على حقول نص وتريد **create interactive form** يتضمن زرًا، اتبع الخطوات الإضافية التالية:

1. تحميل المستند الموجود: `Document doc = new Document("ExistingForm.docx");`
2. نقل الـ builder إلى الموقع المطلوب: `builder.moveToParagraph(5, 0); // الفقرة السادسة، أول عقدة`
3. إدراج الزر كما هو موضح في الخطوة 3.
4. ضبط `Top`/`Left` للزر بناءً على تخطيط الفقرة.

تتيح لك هذه الطريقة إثراء أي قالب Word مُسبق الإنشاء بزر ActiveX دون الحاجة إلى إعادة إنشاء الملف بالكامل.

## الحالات الخاصة واستكشاف الأخطاء وإصلاحها

| الحالة | ما الذي يجب التحقق منه | الإصلاح الموصى به |
|-----------|---------------------------|-------------------|
| الزر لا يظهر في Word | تأكد من فتح الملف في نسخة سطح المكتب من Word (Word Online يزيل ActiveX). | افتح الملف في Word 2016+ نسخة سطح المكتب. |
| التسمية مقطوعة | تحقق من أن عرض الزر كافٍ لاحتواء النص. | زد قيمة `setWidth` حتى تتناسب التسمية. |
| عملية الحفظ تُطلق استثناء `IOException` | تأكد من وجود دليل الإخراج وأن لديك صلاحيات كتابة. | أنشئ الدليل أو شغّل البرنامج بصلاحيات مرتفعة. |
| تداخل أزرار متعددة | قد لا يكون مؤشر الـ builder قد تحرك بعد الإدراج السابق. | استدعِ `builder.moveToDocumentEnd()` قبل إدراج كل عنصر تحكم جديد. |

## مثال كامل قابل للتنفيذ

فيما يلي برنامج Java كامل ومستقل يمكنك نسخه، تجميعه، وتشغيله. يوضح **create blank document**، **add activex button**، و**save word document** في تدفق واحد.

```java
import com.aspose.words.*;

public class CommandButtonDemo {
    public static void main(String[] args) {
        try {
            // 1. Create a new blank document
            Document doc = new Document();

            // 2. Initialize DocumentBuilder
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 3. Insert an ActiveX command button
            Forms2OleControl commandButton = builder.insertForms2OleControl(OleControlType.COMMANDBUTTON);

            // 4. Configure button properties
            commandButton.setCaption("Click Me");
            commandButton.setTop(100);   // points from top
            commandButton.setLeft(100);  // points from left
            commandButton.setWidth(120);
            commandButton.setHeight(30);

            // 5. Save the document
            String outPath = "CommandButton.docx";
            doc.save(outPath);
            System.out.println("Document created: " + outPath);
        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}
```

**الناتج المتوقع**

```
Document created: CommandButton.docx
```

فتح `CommandButton.docx` يُظهر صفحة واحدة بها زر مُسمى **Click Me** موضعه 100 pt من الحافة العليا واليسرى.

## الخلاصة

أنت الآن تعرف كيف **create blank document**، وتدمج **ActiveX button**، وتحول ملف Word عادي إلى **interactive form**. من خلال إتقان **how to insert command button**، يمكنك توسيع هذا النمط لإضافة مربعات اختيار، قوائم منسدلة، أو حتى منطق مخصص يُدار عبر VBA.

بعد ذلك، فكر في استكشاف المواضيع ذات الصلة التالية:

* **Create interactive form** مع حقول نص (`builder.insertField`)  
* **Add activex button** الذي يُشغّل ماكرو VBA (`builder.insertOleObject`)  
* **Create word document** من قالب باستخدام `Document(docTemplatePath)`  
* تحويل الـ .docx الناتج إلى PDF مع الحفاظ على الزر (ملاحظة: سيُظهر PDF الزر كصورة ثابتة).

لا تتردد في تجربة حجم الزر، موقعه، وتسميةه لتتناسب مع تصميم واجهة المستخدم الخاص بك. برمجة سعيدة!

## ما الذي يجب أن تتعلمه بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات التي تم توضيحها في هذا الدليل. كل مورد يتضمن أمثلة كود كاملة مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف أساليب تنفيذ بديلة في مشاريعك.

- [كيفية إنشاء حقول نموذج وإضافة محتوى باستخدام DocumentBuilder في Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [إنشاء مشروع VBA في مستند Word](/words/english/net/working-with-vba-macros/create-vba-project/)
- [إنشاء مستند Word جديد](/words/english/net/add-content-using-documentbuilder/create-new-document/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}