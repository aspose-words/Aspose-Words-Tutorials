---
category: general
date: 2026-10-20
description: إنشاء ملف DOCX فارغ برمجيًا وإدراج زر أمر باستخدام Java. تعلم الكود الكامل
  لإنشاء مستند Word لحفظه مع زر وتعيين تسمية زر الأمر.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank docx programmatically
- create word document code
- save word with button
- add command button word
- set command button caption
language: ar
lastmod: 2026-10-20
og_description: إنشاء ملف DOCX فارغ برمجيًا وإدراج زر أمر. اتبع هذا الدليل خطوة بخطوة
  بلغة Java لحفظ ملف Word مع الزر وتعيين تسمية زر الأمر.
og_image_alt: Screenshot of a blank DOCX file with an inserted command button created
  programmatically
og_title: إنشاء مستند DOCX فارغ برمجيًا – إضافة زر أمر
schemas:
- author: Aspose
  dateModified: '2026-10-20'
  description: Create a blank DOCX programmatically and embed a command button using
    Java. Learn the full create word document code to save Word with button and set
    command button caption.
  headline: Create a blank DOCX programmatically and add a command button
  type: TechArticle
- description: Create a blank DOCX programmatically and embed a command button using
    Java. Learn the full create word document code to save Word with button and set
    command button caption.
  name: Create a blank DOCX programmatically and add a command button
  steps:
  - name: Initialize a new blank document
    text: A blank document is the canvas on which you’ll place the command button.
      Aspose.Words provides the `Document` class for this purpose.
  - name: Set up a `DocumentBuilder`
    text: '`DocumentBuilder` is a helper that lets you insert content, including OLE
      controls, without dealing with low‑level node manipulation.'
  - name: Insert an OLE command button
    text: Word treats interactive controls as OLE (Object Linking and Embedding) objects.
      Aspose.Words exposes `Forms2OleControl` for this.
  - name: Configure the button – type, caption, and location
    text: You must define the control’s type (`COMMANDBUTTON`), set a user‑visible
      caption, and place it on the page.
  - name: Save the document with the embedded button
    text: Finally, write the file to disk. The resulting file can be opened in Microsoft
      Word, where the button will be fully functional.
  - name: Expected result
    text: 'When you open `CommandButton.docx` in Microsoft Word:'
  type: HowTo
tags:
- Java
- DOCX
- Aspose.Words
- Command button
- Automation
title: إنشاء مستند DOCX فارغ برمجيًا وإضافة زر أمر
url: /ar/java/document-manipulation/create-a-blank-docx-programmatically-and-add-a-command-butto/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# إنشاء مستند DOCX فارغ برمجياً وإضافة زر أمر

إذا كنت بحاجة إلى **إنشاء مستند DOCX فارغ برمجياً**، فإن هذا الدرس يوضح لك كيفية تضمين زر أمر مباشرةً في الملف. ستحصل على *كود إنشاء مستند Word* الكامل الذي يحفظ مستند Word مع زر، ويسمح لك **بتعيين تسمية زر الأمر**، ويعمل مع أحدث مكتبة Aspose.Words for Java.

إنشاء ضوابط تفاعلية داخل ملف DOCX مفيد عندما تريد توزيع قوالب تُشغّل ماكروهات، أو تُطلق برامج خارجية، أو ببساطة تُرشد المستخدمين بزر قابل للنقر “Click Me”. الخطوات أدناه تغطي كل شيء من تهيئة مستند فارغ إلى حفظ الملف النهائي على القرص.

## المتطلبات المسبقة

* Java 17 أو أحدث مثبت.
* Maven (أو أداة البناء المفضلة لديك) لإدارة التبعيات.
* Aspose.Words for Java 23.9 أو أحدث. أضف التبعية إلى ملف `pom.xml`:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
    <classifier>jdk17</classifier>
</dependency>
```

* IDE مثل IntelliJ IDEA أو VS Code (أي محرر يدعم Java يعمل).

## إنشاء مستند DOCX فارغ برمجياً – خطوة بخطوة

الأقسام التالية تقسم العملية إلى خطوات واضحة مرقمة. كل خطوة تشرح **لماذا** هي ضرورية، وليس فقط **ماذا** تكتب.

### الخطوة 1: تهيئة مستند فارغ جديد

المستند الفارغ هو القماش الذي ستضع عليه زر الأمر. توفر Aspose.Words الفئة `Document` لهذا الغرض.

```java
import com.aspose.words.Document;
import com.aspose.words.DocumentBuilder;

public class CommandButtonDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document
        Document document = new Document();
```

*لماذا هذا مهم*: بدءًا بمستند `Document` فارغ يضمن عدم وجود تنسيق مخفي أو ضوابط موجودة تتداخل مع الزر الذي ستضيفه لاحقًا.

### الخطوة 2: إعداد `DocumentBuilder`

`DocumentBuilder` هو أداة مساعدة تتيح لك إدراج محتوى، بما في ذلك ضوابط OLE، دون الحاجة للتعامل مع تعديل العقد منخفض المستوى.

```java
        // Step 2: Initialize a DocumentBuilder for the document
        DocumentBuilder builder = new DocumentBuilder(document);
```

*لماذا هذا مهم*: يحتفظ الـ builder بموقع المؤشر الحالي، لذا سيتم وضع الزر بالضبط حيث تحدده.

### الخطوة 3: إدراج زر أمر OLE

يتعامل Word مع الضوابط التفاعلية ككائنات OLE (Object Linking and Embedding). تُظهر Aspose.Words الفئة `Forms2OleControl` لهذا الغرض.

```java
        // Step 3: Insert an OLE command button into the document
        com.aspose.words.forms.Forms2OleControl commandButton = builder.insertForms2OleControl();
```

*لماذا هذا مهم*: إدراج الضابط ينشئ عنصرًا نائبًا يمكنك تكوينه لاحقًا (النوع، التسمية، الموقع).

### الخطوة 4: تكوين الزر – النوع، التسمية، والموقع

يجب تعريف نوع الضابط (`COMMANDBUTTON`)، وتعيين تسمية مرئية للمستخدم، ووضعه على الصفحة.

```java
        // Step 4: Configure the command button's type, caption, and position
        commandButton.setOleControlType(com.aspose.words.forms.OleControlType.COMMANDBUTTON);
        commandButton.setCaption("Click Me");               // set command button caption
        commandButton.setLeft(100);                         // distance from the left margin (points)
        commandButton.setTop(200);                          // distance from the top margin (points)
```

*لماذا هذا مهم*:  
* **Type** يخبر Word أن الضابط يتصرف كزر قابل للنقر.  
* **Caption** هو النص الذي يراه المستخدم؛ تغييره هو الطريقة التي **تُعيّن بها تسمية زر الأمر**.  
* **Left** و **Top** يتحكمان في الموضع الدقيق، وهو أمر أساسي عندما **تضيف زر أمر إلى مستندات Word** التي تحتاج إلى تخطيط دقيق.

### الخطوة 5: حفظ المستند مع الزر المدمج

أخيرًا، اكتب الملف إلى القرص. يمكن فتح الملف الناتج في Microsoft Word، حيث سيكون الزر فعالًا بالكامل.

```java
        // Step 5: Save the document with the embedded command button
        String outputPath = "YOUR_DIRECTORY/CommandButton.docx";
        document.save(outputPath);
        System.out.println("Document saved to: " + outputPath);
    }
}
```

*لماذا هذا مهم*: هذه الخطوة **تحفظ Word مع زر** بحيث يبقى الضابط موجودًا عبر الأجهزة. يمكن توزيع الملف كقالب أو استخدامه في خطوط توليد التقارير الآلية.

## مثال كامل يعمل

انسخ الفئة الكاملة أدناه إلى ملف اسمه `CommandButtonDemo.java`، عدّل `YOUR_DIRECTORY` إلى مسار حقيقي، وشغّله باستخدام `mvn compile exec:java`.

```java
import com.aspose.words.Document;
import com.aspose.words.DocumentBuilder;
import com.aspose.words.forms.Forms2OleControl;
import com.aspose.words.forms.OleControlType;

public class CommandButtonDemo {
    public static void main(String[] args) throws Exception {
        // Create a new blank document
        Document document = new Document();

        // Initialize a DocumentBuilder for the document
        DocumentBuilder builder = new DocumentBuilder(document);

        // Insert an OLE command button into the document
        Forms2OleControl commandButton = builder.insertForms2OleControl();

        // Configure the command button
        commandButton.setOleControlType(OleControlType.COMMANDBUTTON);
        commandButton.setCaption("Click Me");   // set command button caption
        commandButton.setLeft(100);             // points from left margin
        commandButton.setTop(200);              // points from top margin

        // Save the document with the embedded command button
        String outputPath = "YOUR_DIRECTORY/CommandButton.docx";
        document.save(outputPath);
        System.out.println("Document saved to: " + outputPath);
    }
}
```

### النتيجة المتوقعة

عند فتح `CommandButton.docx` في Microsoft Word:

* المستند فارغ تمامًا باستثناء زر يحمل التسمية **Click Me**.
* النقر على الزر سيظهر السلوك الافتراضي لـ Word (لا يفعل شيئًا ما لم يتم إرفاق ماكرو)، مما يؤكد أن ضابط OLE تم تضمينه بشكل صحيح.

## أسئلة شائعة وحالات خاصة

| Question | Answer |
|----------|--------|
| **هل يمكنني تغيير حجم الزر؟** | نعم. استخدم `commandButton.setWidth(double)` و `commandButton.setHeight(double)` لضبط الأبعاد بالنقاط. |
| **ماذا لو احتجت إلى ماكرو مرفق بالزر؟** | الزر نفسه هو مجرد عنصر OLE. يجب إضافة ماكرو VBA إلى المستند يدويًا أو عبر أدوات `addMacro` في واجهة برمجة تطبيقات Aspose.Words `Document`. |
| **هل سيعمل الزر في LibreOffice؟** | يدعم LibreOffice عناصر OLE محدودة. يظهر الزر، لكن سلوك النقر قد يختلف. |
| **كيف يمكن إضافة أزرار متعددة؟** | كرّر الخطوتين 3‑4 باستخدام نسخة جديدة من `Forms2OleControl`. عدّل `setLeft`/`setTop` لكل زر لتجنب التداخل. |
| **هل الكود متوافق مع .NET؟** | تنطبق نفس المنطق، لكن ستستخدم فئات `Aspose.Words` للـ .NET (`Document`, `DocumentBuilder`, `Forms2OleControl`). |

## نصائح من الميدان

* **نصيحة احترافية:** استخدم `builder.moveToDocumentEnd()` قبل إدراج الزر إذا كنت تريد وضعه في نهاية المستند تمامًا، بغض النظر عن المحتوى السابق.  
* **احذر من:** قيم `Left`/`Top` الصغيرة جدًا قد تضع الزر خارج المنطقة القابلة للطباعة، مما يجعله غير مرئي في عرض تخطيط Word.  
* **ملاحظة أداء:** إدراج العديد من ضوابط OLE قد يزيد من حجم الملف. إذا كنت تحتاج فقط إلى إشارة بصرية، فكر في استخدام `Shape` عادي مع رابط تشعبي بدلاً من ذلك.

## الخلاصة

أنت الآن تعرف كيف **تنشئ مستند DOCX فارغ برمجياً** وتدمج زر أمر يعمل بالكامل باستخدام Java. يغطي الدرس سير عمل كامل لـ *كود إنشاء مستند Word*، ويظهر كيفية **حفظ Word مع زر**، ويُظهر الطريقة الصحيحة **لإضافة زر أمر إلى مستندات Word**، ويشرح كيفية **تعيين تسمية زر الأمر**.

من هنا يمكنك:

* إضافة المزيد من ضوابط OLE (مربعات اختيار، قوائم منسدلة) لنماذج أكثر غنى.  
* إرفاق ماكروهات VBA لجعل الزر ينفّذ إجراءات مخصصة.  
* دمج هذه التقنية مع دمج البريد في المستندات لإنشاء قوالب ديناميكية وتفاعلية.

لا تتردد في تجربة أنماط الأزرار، المواقع، والضوابط الإضافية لتتناسب مع متطلبات عملك الخاصة. برمجة سعيدة

## ما الذي ينبغي أن تتعلمه بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات التي تم توضيحها في هذا الدليل. كل مصدر يتضمن أمثلة كود كاملة تعمل مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف أساليب تنفيذ بديلة في مشاريعك.

- [إنشاء مستند Word فارغ مع زر أمر – دليل خطوة بخطوة](/words/english/java/using-document-elements/create-blank-word-document-with-a-command-button-step-by-ste/)
- [كيفية إدراج زر ActiveX في Word – تعيين تسمية الزر](/words/english/java/using-document-elements/how-to-insert-activex-button-in-word-set-button-caption/)
- [إنشاء مستند Word فارغ باستخدام Java – دليل Aspose.Words الكامل](/words/english/java/document-loading-and-saving/create-blank-word-document-with-java-full-aspose-words-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}