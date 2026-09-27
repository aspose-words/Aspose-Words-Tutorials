---
category: general
date: 2026-09-27
description: إنشاء ملف docx يحتوي على ActiveX في Java باستخدام Aspose.Words. تعلم
  كيفية إدراج زر أمر ActiveX خطوةً بخطوة.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create docx containing activex
- insert activex command button
- Aspose.Words Java
- ActiveX control in Word
- generate Word document programmatically
language: ar
lastmod: 2026-09-27
og_description: إنشاء ملف docx يحتوي على ActiveX في Java باستخدام Aspose.Words. اتبع
  هذا الدليل لإدراج زر أمر ActiveX وحفظ المستند.
og_image_alt: Screenshot of a Word document that contains an ActiveX command button
og_title: إنشاء ملف docx يحتوي على ActiveX في Java – دليل كامل
schemas:
- author: Aspose
  dateModified: '2026-09-27'
  description: Create docx containing ActiveX in Java using Aspose.Words. Learn to
    insert an ActiveX command button step‑by‑step.
  headline: How to create docx containing ActiveX with Java and Aspose.Words
  type: TechArticle
- description: Create docx containing ActiveX in Java using Aspose.Words. Learn to
    insert an ActiveX command button step‑by‑step.
  name: How to create docx containing ActiveX with Java and Aspose.Words
  steps:
  - name: The document should show a single page with a button labeled **Click Me**
      positioned near the top‑left corner.
    text: The document should show a single page with a button labeled **Click Me**
      positioned near the top‑left corner.
  - name: If the button does not appear, check that **ActiveX controls are enabled**
      in Word’s Trust Center (File → Options → Trust Center → Trust Center Settings
      → ActiveX Settings).
    text: If the button does not appear, check that **ActiveX controls are enabled**
      in Word’s Trust Center (File → Options → Trust Center → Trust Center Settings
      → ActiveX Settings).
  - name: The button is functional only on Windows versions of Word that support ActiveX.
      On macOS or web‑based Word, the control will be displayed as a static image.
    text: The button is functional only on Windows versions of Word that support ActiveX.
      On macOS or web‑based Word, the control will be displayed as a static image.
  type: HowTo
tags:
- docx
- activex
- java
- aspose-words
title: كيفية إنشاء ملف docx يحتوي على ActiveX باستخدام Java و Aspose.Words
url: /ar/java/using-document-elements/how-to-create-docx-containing-activex-with-java-and-aspose-w/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# كيفية إنشاء ملف docx يحتوي على ActiveX باستخدام Java و Aspose.Words

إذا كنت بحاجة إلى **إنشاء docx يحتوي على ActiveX**، فإن هذا الدليل يوضح لك حلًا كاملاً. ستتعلم كيفية **إدراج زر أمر ActiveX** في ملف Word باستخدام Aspose.Words for Java، ثم حفظ النتيجة كملف .docx يمكن فتحه في Microsoft Word.

إنشاء مستند Word برمجيًا يوفر عليك التحرير اليدوي ويضمن التناسق عبر التقارير أو العقود أو نماذج القوالب. تغطي الخطوات أدناه كل شيء من إعداد المشروع إلى التعامل مع المشكلات الشائعة، بحيث يمكنك دمج التقنية في أي تطبيق Java.

## المتطلبات المسبقة

قبل أن تبدأ، تأكد من وجود ما يلي:

* مجموعة تطوير جافا (JDK) 8 أو أحدث مثبتة.
* Maven 3.6+ (أو أي أداة بناء أخرى تفضلها).
* ملف ترخيص Aspose.Words for Java (التقييم المجاني يكفي للاختبار).
* Microsoft Word مثبت على الجهاز المستهدف إذا كنت تريد التحقق بصريًا من عنصر التحكم ActiveX.

هذه العناصر ضرورية لأن Aspose.Words يوفر الـ API الذي ينشئ المستند، بينما Word مطلوب لعرض عنصر التحكم ActiveX.

## الخطوة 1: إعداد مشروع Maven

أنشئ مشروع Maven جديد أو أضف تبعية Aspose.Words إلى ملف `pom.xml` الموجود:

```xml
<project>
    <modelVersion>4.0.0</modelVersion>
    <groupId>com.example</groupId>
    <artifactId>activex-docx-demo</artifactId>
    <version>1.0.0</version>
    <properties>
        <maven.compiler.source>1.8</maven.compiler.source>
        <maven.compiler.target>1.8</maven.compiler.target>
    </properties>

    <dependencies>
        <!-- Aspose.Words for Java -->
        <dependency>
            <groupId>com.aspose</groupId>
            <artifactId>aspose-words</artifactId>
            <version>24.10</version> <!-- use the latest stable version -->
        </dependency>
    </dependencies>
</project>
```

> **نصيحة احترافية:** حافظ على توافق نسخة Aspose.Words مع ملاحظات الإصدار الرسمية للاستفادة من إصلاحات الأخطاء والميزات الجديدة لـ ActiveX.

## الخطوة 2: كتابة كود Java الذي ينشئ المستند

أنشئ فئة باسم `ActiveXDocxCreator`. يتضمن الكود أدناه جميع الاستيرادات المطلوبة، وطريقة `main`، وتعليقات تفصيلية تشرح كل عملية.

```java
package com.example.activex;

import com.aspose.words.*;
import java.io.File;

/**
 * Demonstrates how to create a DOCX file that contains an ActiveX command button.
 * The resulting file can be opened in Microsoft Word where the button appears
 * on the first page.
 */
public class ActiveXDocxCreator {

    public static void main(String[] args) {
        // 1. Initialize a new empty document and a DocumentBuilder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2. Insert an ActiveX Forms2OleControl at the current cursor position.
        Forms2OleControl commandButton = builder.insertForms2OleControl();

        // 3. Configure the control to be a CommandButton and set its caption.
        commandButton.setControlType(Forms2OleControlType.COMMANDBUTTON);
        commandButton.setCaption("Click Me");

        // 4. Position the button on the page.
        //    The coordinates are measured in points (1 point = 1/72 inch).
        commandButton.setLeft(100); // 100 points from the left margin
        commandButton.setTop(150);  // 150 points from the top margin

        // 5. (Optional) Set the size of the button for better visibility.
        commandButton.setWidth(120);
        commandButton.setHeight(30);

        // 6. Save the document to the desired location.
        String outputPath = "output/ActiveXCommandButton.docx";
        try {
            // Ensure the output directory exists.
            new File("output").mkdirs();
            doc.save(outputPath);
            System.out.println("Document saved successfully to " + outputPath);
        } catch (Exception e) {
            System.err.println("Error while saving the document: " + e.getMessage());
        }
    }
}
```

### لماذا كل سطر مهم

* `Document` هو الحاوية لجميع محتويات Word. إنشاء نسخة جديدة يمنحك لوحة رسم نظيفة.
* `DocumentBuilder` يوفر API سلس لإدراج العناصر؛ يتتبع تلقائيًا نقطة الإدراج.
* `insertForms2OleControl()` ينشئ عنصرًا نائبًا عامًّا للتحكم OLE. تتعامل Aspose.Words معه كحاوية ActiveX.
* `setControlType(Forms2OleControlType.COMMANDBUTTON)` يخبر Word بأن العنصر النائب يجب أن يُعرض كزر أمر.
* `setCaption("Click Me")` يحدد النص المعروض على الزر.
* `setLeft` و `setTop` يضعان الزر نسبة إلى هوامش الصفحة. عدل هذه القيم لتناسب تخطيطك.
* `setWidth` و `setHeight` اختياريان لكنهما يحسنان مظهر الزر، خاصةً عندما يكون الحجم الافتراضي صغيرًا جدًا.
* `doc.save` يكتب البنية الموجودة في الذاكرة إلى ملف .docx فعلي يمكن لـ Word فتحه.

## الخطوة 3: التحقق من المستند المُولد

افتح `output/ActiveXCommandButton.docx` في Microsoft Word:

1. يجب أن يظهر المستند صفحة واحدة تحتوي على زر مُعنون **Click Me** موضعه بالقرب من الزاوية العليا اليسرى.
2. إذا لم يظهر الزر، تحقق من أن **التحكمات ActiveX مفعلة** في مركز الثقة الخاص بـ Word (File → Options → Trust Center → Trust Center Settings → ActiveX Settings).
3. الزر يعمل فقط على إصدارات Word لنظام Windows التي تدعم ActiveX. على macOS أو Word المستند إلى الويب، سيُعرض التحكم كصورة ثابتة.

## الخطوة 4: التعامل مع الحالات الشائعة

| الحالة | السبب | الإجراء الموصى به |
|-----------|--------|--------------------|
| الزر مفقود بعد فتح الملف | إعدادات أمان Word تحظر ActiveX | فعّل “Run all controls without restrictions” للمواقع الموثوقة. |
| لا يمكن فتح ملف .docx المُولد | نسخة Aspose.Words غير متوافقة | حدّث إلى أحدث إصدار من Aspose.Words؛ الإصدارات القديمة قد لا تدمج أجزاء OLE المطلوبة بشكل صحيح. |
| تحتاج الزر إلى تنفيذ ماكرو | ActiveX وحده لا يحتوي على كود ماكرو | اجمع بين عنصر التحكم ActiveX وماكرو VBA يتعامل مع حدث `Click`. استخدم طريقة `DocumentBuilder.insertOleObject` لدمج قالب يدعم الماكرو. |
| التخطيط غير متناسق على أحجام صفحات مختلفة | الإحداثيات نقاط مطلقة | استخدم `builder.getPageSetup().setPageWidth` و `setPageHeight` لتوحيد حجم الصفحة قبل وضع التحكم. |

## الخطوة 5: توسيع الحل

يمكنك إدراج عناصر تحكم ActiveX أخرى بتغيير تعداد `ControlType`:

```java
commandButton.setControlType(Forms2OleControlType.CHECKBOX); // inserts a checkbox
```

يدعم Aspose.Words أيضًا إدراج **صناديق نصية ActiveX**، **قوائم**، و **قوائم منسدلة**. تُطبق طرق التموضع نفسها (`setLeft`, `setTop`, `setWidth`, `setHeight`).

إذا احتجت إلى وضع عدة عناصر تحكم، استدعِ `builder.insertForms2OleControl()` بشكل متكرر واضبط إحداثيات كل عنصر وفقًا لذلك.

## ملف المصدر الكامل

فيما يلي ملف `ActiveXDocxCreator.java` كامل جاهز للنسخ واللصق:

```java
package com.example.activex;

import com.aspose.words.*;
import java.io.File;

public class ActiveXDocxCreator {
    public static void main(String[] args) {
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        Forms2OleControl commandButton = builder.insertForms2OleControl();
        commandButton.setControlType(Forms2OleControlType.COMMANDBUTTON);
        commandButton.setCaption("Click Me");
        commandButton.setLeft(100);
        commandButton.setTop(150);
        commandButton.setWidth(120);
        commandButton.setHeight(30);

        String outputPath = "output/ActiveXCommandButton.docx";
        try {
            new File("output").mkdirs();
            doc.save(outputPath);
            System.out.println("Document saved successfully to " + outputPath);
        } catch (Exception e) {
            System.err.println("Error while saving the document: " + e.getMessage());
        }
    }
}
```

تشغيل هذا البرنامج ينتج **docx يحتوي على ActiveX** يمكنك توزيعه على المستخدمين النهائيين الذين يحتاجون إلى نماذج تفاعلية.

## الخلاصة

أنت الآن تعرف كيف **تنشئ docx يحتوي على ActiveX** باستخدام Java و Aspose.Words، وكيف **تدرج زر أمر ActiveX** برمجيًا. غطى الدليل إعداد المشروع، الشيفرة الكاملة، خطوات التحقق، واستراتيجيات التعامل مع المشكلات الشائعة.

من هنا يمكنك استكشاف:

* إضافة ماكرو VBA للاستجابة لنقر الزر.
* دمج عناصر تحكم ActiveX أخرى مثل مربعات الاختيار أو القوائم المنسدلة.
* أتمتة إنشاء نماذج متعددة الصفحات ببيانات ديناميكية.

جرّب إحداثيات، أحجام، وأنواع تحكم مختلفة لتتناسب مع تخطيط مستندك المحدد. برمجة سعيدة!

## ما الذي يجب أن تتعلمه بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات التي تم توضيحها في هذا الدليل. كل مصدر يتضمن أمثلة شيفرة كاملة مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف نهج تنفيذ بديلة في مشاريعك.

- [Using OLE Objects and ActiveX Controls in Aspose.Words for Java](/words/english/java/using-document-elements/using-ole-objects-and-activex/)
- [How to create form fields and add content using DocumentBuilder in Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Create rectangle shape in Word with Aspose.Words – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}