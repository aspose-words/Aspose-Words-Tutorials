---
category: general
date: 2026-10-07
description: إنشاء زر أمر ActiveX في Java وإضافة زر الأمر برمجيًا إلى مستندات Word.
  تعلّم كيفية ضبط موضع الزر من اليسار والأعلى.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create activex command button
- programmatically add command button
- how to set button left top
language: ar
lastmod: 2026-10-07
og_description: إنشاء زر أمر ActiveX في Java لتضمين عناصر تحكم تفاعلية في مستندات
  Word الخاصة بك. تعلم كيفية إضافة زر الأمر برمجياً، وتحديد موقعه، وتخصيص مظهره.
og_image_alt: Screenshot showing a created ActiveX command button in a Java‑generated
  Word document
og_title: إنشاء زر أمر ActiveX في Java – دليل خطوة بخطوة
schemas:
- author: Aspose
  dateModified: '2026-10-07'
  description: Create ActiveX command button in Java and programmatically add command
    button to Word docs. Learn how to set button left top positions.
  headline: How to create ActiveX command button in Java
  type: TechArticle
- description: Create ActiveX command button in Java and programmatically add command
    button to Word docs. Learn how to set button left top positions.
  name: How to create ActiveX command button in Java
  steps:
  - name: How to set button left top
    text: Positioning the button is where the secondary keyword **how to set button
      left top** becomes relevant. The `setLeft` and `setTop` methods accept values
      measured in points (1 point = 1/72 in).
  - name: Adding multiple buttons
    text: If you need several buttons, repeat **Step 2** and **Step 3** for each control.
      Remember to adjust `setLeft` and `setTop` so the buttons don’t overlap.
  - name: Changing button behavior
    text: 'ActiveX buttons can run VBA macros when clicked. To attach a macro, set
      the `setOnAction` property with the macro name:'
  - name: Compatibility notes
    text: '- The button works only in desktop versions of Word that support ActiveX
      (e.g., Word for Windows). It will appear as a static image in Word for Mac or
      online editors. - If you target a mixed environment, consider using a **content
      control** (`RichTextContentControl`) instead of an ActiveX control.'
  - name: Next steps
    text: '- Explore other ActiveX controls such as `Forms.TextBox.1` or `Forms.CheckBox.1`.
      - Combine multiple controls with a VBA module to implement full‑featured forms.
      - Replace ActiveX with content controls if you need cross‑platform compatibility.'
  type: HowTo
tags:
- ActiveX
- Java
- Aspose.Words
title: كيفية إنشاء زر أمر ActiveX في جافا
url: /ar/java/using-document-elements/how-to-create-activex-command-button-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# كيفية إنشاء زر أمر ActiveX في Java

إذا كنت بحاجة إلى **إنشاء زر أمر ActiveX** في مستند Word باستخدام Java، فإن هذا الدليل يوضح لك بالضبط كيفية القيام بذلك. سترى مثالًا كاملاً قابلاً للتنفيذ **يضيف زر أمر برمجيًا**، ويضعه باستخدام `setLeft` و `setTop`، ويحفظ النتيجة كملف `.docx`.

يتيح لك تضمين زر تفاعلي بناء نماذج، أتمتة سير العمل، أو جمع مدخلات المستخدم مباشرة داخل ملف Word. تغطي الخطوات أدناه كل شيء من إعداد المشروع إلى التحقق النهائي، بحيث يمكنك نسخ الشيفرة إلى مشروعك الخاص دون أن تفوت أي تفاصيل.

## المتطلبات المسبقة

- تثبيت JDK 17 أو أحدث  
- Maven 3.8+ (أو أداة البناء المفضلة لديك)  
- Aspose.Words for Java 23.9 أو أحدث – المكتبة التي توفر `DocumentBuilder` ودعم التحكمات OLE  
- إلمام أساسي بصياغة Java ومفاهيم البرمجة الكائنية  

إذا كنت تستخدم Maven، أضف الاعتماد إلى ملف `pom.xml` الخاص بك:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
    <classifier>jdk17</classifier>
</dependency>
```

> **نصيحة احترافية:** استخدم أحدث نسخة من Aspose.Words للاستفادة من إصلاحات الأخطاء والميزات الجديدة في OLE.

## الخطوة 1: إنشاء مستند فارغ جديد و DocumentBuilder

الخطوة الأولى لـ **إنشاء زر أمر ActiveX** هي إنشاء كائن `Document` فارغ و `DocumentBuilder`. يوفر لك الـ builder واجهة برمجة تطبيقات سلسة لإدراج المحتوى، بما في ذلك عناصر التحكم OLE.

```java
import com.aspose.words.*;

public class ActiveXButtonDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new empty document and a DocumentBuilder to work with it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

`Document` يمثل ملف Word في الذاكرة، بينما يعمل `DocumentBuilder` كالمؤشر الذي يتيح لك وضع العناصر بدقة في المكان الذي تحتاجه.

## الخطوة 2: إدراج عنصر تحكم زر أمر OLE

يتم إدراج عناصر التحكم ActiveX ككائنات OLE. توفر Aspose.Words الفئة `Forms2OleControl` لهذا الغرض.

```java
        // Step 2: Insert an OLE command button control into the document
        Forms2OleControl commandButton = builder.insertForms2OleControl();
```

عند استدعاء `insertForms2OleControl()`، تقوم Aspose تلقائيًا بإنشاء شكل نائب سيستضيف زر ActiveX.

## الخطوة 3: ضبط خصائص الزر

الآن يمكنك **إضافة زر أمر برمجيًا** وتحديد تفاصيله مثل ProgID، التسمية، والحجم. أكثر ProgID شيوعًا لزر الأمر هو `"Forms.CommandButton.1"`.

```java
        // Step 3: Configure the button's properties (type, position, size, caption)
        commandButton.setProgId("Forms.CommandButton.1"); // ActiveX class identifier
        commandButton.setCaption("Click Me");            // Text shown on the button
        commandButton.setWidth(80);                      // Width in points
        commandButton.setHeight(30);                     // Height in points
```

### كيفية تعيين موضع الزر (اليسار والعلو)

تحديد موضع الزر هو المكان الذي يصبح فيه المصطلح الثانوي **how to set button left top** ذا صلة. تقبل طُرُق `setLeft` و `setTop` قيمًا مقاسة بالنقاط (نقطة واحدة = 1/72 بوصة).

```java
        // Position the button 100 points from the left margin and 150 points from the top
        commandButton.setLeft(100);   // Horizontal offset
        commandButton.setTop(150);    // Vertical offset
```

قم بتعديل هذه الأرقام لتناسب تخطيطك. على سبيل المثال، لتنسيق الزر مع خلية جدول، احسب إحداثيات الخلية ومرّرها إلى `setLeft`/`setTop`.

## الخطوة 4: حفظ المستند

أخيرًا، اكتب المستند إلى القرص. سيحتوي الملف على زر ActiveX جاهز للتفاعل عند فتحه في Microsoft Word.

```java
        // Step 4: Save the document containing the button
        doc.save("CommandButton.docx");
        System.out.println("Document saved successfully.");
    }
}
```

تشغيل طريقة `main` ينتج ملف `CommandButton.docx`. افتح الملف في Word، فعّل المحتوى إذا طُلب منك، وسترى زرًا قابلًا للنقر يحمل التسمية **Click Me** في الإحداثيات التي حددتها.

![إنشاء زر أمر ActiveX في Java](/images/activex-button-screenshot.png){.center width=600 alt="لقطة شاشة لإنشاء زر أمر ActiveX في Java تُظهر الزر داخل مستند Word"}

## الاختلافات الشائعة وحالات الحافة

### إضافة عدة أزرار

إذا كنت بحاجة إلى عدة أزرار، كرّر **الخطوة 2** و **الخطوة 3** لكل عنصر تحكم. تذكّر تعديل `setLeft` و `setTop` حتى لا تتداخل الأزرار.

### تغيير سلوك الزر

يمكن لأزرار ActiveX تشغيل ماكرو VBA عند النقر. لإرفاق ماكرو، اضبط خاصية `setOnAction` باسم الماكرو:

```java
commandButton.setOnAction("MyMacro");
```

تأكد من أن المستند الهدف يحتوي على وحدة VBA المقابلة؛ وإلا سيظهر خطأ في Word.

### ملاحظات التوافق

- يعمل الزر فقط في إصدارات Word المكتبية التي تدعم ActiveX (مثل Word لنظام Windows). سيظهر كصورة ثابتة في Word لنظام Mac أو المحررات عبر الإنترنت.  
- إذا كنت تستهدف بيئة مختلطة، فكر في استخدام **عنصر تحكم المحتوى** (`RichTextContentControl`) بدلاً من عنصر تحكم ActiveX.

## الكود الكامل للمصدر للرجوع إليه

فيما يلي المثال الكامل المستقل الذي يمكنك نسخه إلى مشروع Maven جديد وتشغيله فورًا.

```java
import com.aspose.words.*;

public class ActiveXButtonDemo {
    public static void main(String[] args) throws Exception {
        // Create a new empty document and a DocumentBuilder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert an OLE command button control
        Forms2OleControl commandButton = builder.insertForms2OleControl();

        // Configure the button
        commandButton.setProgId("Forms.CommandButton.1");
        commandButton.setCaption("Click Me");
        commandButton.setWidth(80);
        commandButton.setHeight(30);

        // How to set button left top – position the control
        commandButton.setLeft(100);   // Horizontal offset in points
        commandButton.setTop(150);    // Vertical offset in points

        // Save the resulting document
        doc.save("CommandButton.docx");
        System.out.println("Document saved successfully.");
    }
}
```

**الناتج المتوقع:** بعد التنفيذ، ستجد ملف `CommandButton.docx` في دليل عمل مشروعك. فتح الملف في Microsoft Word يُظهر زرًا في الموقع المحدد مع التسمية “Click Me”.

## الخلاصة

أنت الآن تعرف كيف **تنشئ زر أمر ActiveX** في Java، **تضيف زر أمر برمجيًا** إلى مستند Word، وتتحكم بدقة في تخطيطه باستخدام طرق **how to set button left top**. تفتح هذه التقنية الباب أمام نماذج Word غنية وتفاعلية يمكنها تشغيل ماكروهات، إطلاق تطبيقات خارجية، أو جمع مدخلات المستخدم مباشرة داخل المستند.

### الخطوات التالية

- استكشف عناصر تحكم ActiveX أخرى مثل `Forms.TextBox.1` أو `Forms.CheckBox.1`.  
- اجمع عدة عناصر تحكم مع وحدة VBA لتنفيذ نماذج كاملة المميزات.  
- استبدل ActiveX بعناصر تحكم المحتوى إذا كنت تحتاج إلى توافق عبر المنصات.  

لا تتردد في تجربة الحجم، التسمية، والموضع لتتناسب مع تصميم واجهة المستخدم الخاص بك. إذا واجهت أي مشاكل، تحقق مرة أخرى من أن نسخة Aspose.Words التي تستخدمها تدعم عناصر التحكم OLE، وتأكد من أن إعدادات أمان Word تسمح بتنفيذ ActiveX. برمجة سعيدة!

## ما الذي يجب أن تتعلمه بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات الموضحة في هذا الدليل. كل مورد يتضمن أمثلة شيفرة كاملة مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف أساليب تنفيذ بديلة في مشاريعك الخاصة.

- [إدراج كائنات OLE وعناصر التحكم ActiveX في مستندات Word](/words/english/python-net/document-structure-and-content-manipulation/document-ole-objects-active-x/)
- [كيفية إنشاء حقول نموذج وإضافة محتوى باستخدام DocumentBuilder في Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [إنشاء شكل مستطيل في Word باستخدام Java – دليل كامل](/words/english/java/images-shapes/create-rectangle-shape-in-word-with-java-full-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}