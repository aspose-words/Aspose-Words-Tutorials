---
category: general
date: 2026-11-15
description: تحرير مستند Word برمجيًا لإدراج زر أمر. تعلّم كيفية إضافة زر، تعيين اسم
  زر الأمر، وإنشاء زر نموذج في Word خلال دقائق.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- edit word document programmatically
- how to add button
- insert command button word
- create form button word
- set command button name
language: ar
lastmod: 2026-11-15
og_description: تحرير مستند Word برمجياً وإدراج زر أمر. يوضح هذا الدليل كيفية إضافة
  زر، تعيين اسم زر الأمر، وإنشاء زر نموذج Word بسرعة.
og_image_alt: Screenshot of a Word document edited programmatically with a command
  button
og_title: تحرير مستند Word برمجيًا – إضافة زر أمر
schemas:
- author: Aspose
  dateModified: '2026-11-15'
  description: Edit Word document programmatically to insert a command button. Learn
    how to add button, set command button name, and create form button Word in minutes.
  headline: Edit Word document programmatically and add a command button
  type: TechArticle
- description: Edit Word document programmatically to insert a command button. Learn
    how to add button, set command button name, and create form button Word in minutes.
  name: Edit Word document programmatically and add a command button
  steps:
  - name: Expected output
    text: 'When you open the saved file:'
  - name: How to add button to a specific paragraph?
    text: '```java builder.moveToParagraph(2, true); // moves to third paragraph (0‑based
      index) Forms2OleControl btn = builder.insertForms2OleControl(); btn.setName("btnThirdParagraph");
      btn.setCaption("Click Me"); ```'
  - name: How to insert a button inside a table cell?
    text: '```java Table table = builder.startTable(); builder.insertCell(); builder.insertCell();
      builder.endTable();'
  - name: What if I need a larger button?
    text: '```java cmdBtn.setWidth(100); // width in points cmdBtn.setHeight(30);
      // height in points ```'
  - name: How to **insert command button word** using a different language (e.g.,
      C#)?
    text: 'The same logic applies; replace Java syntax with C# equivalents:'
  type: HowTo
tags:
- Word automation
- Aspose.Words
- Java
title: تحرير مستند Word برمجيًا وإضافة زر أمر
url: /ar/java/document-manipulation/edit-word-document-programmatically-and-add-a-command-button/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# تحرير مستند Word برمجيًا وإضافة زر أمر

إذا كنت بحاجة إلى **تحرير مستند Word برمجيًا**، فإن أسرع طريقة هي استخدام Aspose.Words API. يوضح لك هذا الدرس بالضبط **كيفية إضافة زر** التحكم، وتكوين التسمية التوضيحية له، و**تعيين اسم زر الأمر** بحيث يمكن للمستند أن يعمل كنموذج بسيط. في النهاية ستحصل على ملف *.docx* قابل للتحرير بالكامل يحتوي على زر أمر فعال جاهز للمعالجة اللاحقة.

سوف تتعلم كيفية **إدراج كلمة زر الأمر**، **إنشاء كلمة زر النموذج**، وإدارة خصائص الزر دون فتح Word يدويًا. المتطلب الوحيد هو بيئة تطوير Java أساسية ومكتبة Aspose.Words for Java.

## المتطلبات المسبقة

- Java 17 أو أحدث (الكود يعمل مع Java 8+ أيضًا)
- Aspose.Words for Java (قم بالتنزيل من [Aspose.Words for Java](https://products.aspose.com/words/java/))
- مستند Word موجود (`input.docx`) تريد تعديله
- الإلمام بـ Maven أو Gradle لإضافة تبعية Aspose.Words

```xml
<!-- Maven dependency -->
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.12</version>
</dependency>
```

## الخطوة 1: تحميل مستند Word

العملية الأولى عند **تحرير مستند Word برمجيًا** هي تحميل الملف المصدر إلى كائن `Document`. هذا الكائن يمثل ملف Word بالكامل في الذاكرة، مما يتيح لك تعديل محتوياته.

```java
import com.aspose.words.*;

public class WordButtonDemo {
    public static void main(String[] args) throws Exception {
        // Load the existing Word file
        Document doc = new Document("YOUR_DIRECTORY/input.docx");
```

> **لماذا هذا مهم:** تحميل المستند ينشئ بنية شبيهة بـ DOM يمكن لـ Aspose.Words استعراضها وتعديلها. تخطي هذه الخطوة سيتركك بدون هدف لإدراج الزر.

## الخطوة 2: إنشاء `DocumentBuilder` لتحرير المستند

`DocumentBuilder` يعمل كالمؤشر داخل ملف Word. يسمح لك بإدراج نصوص، صور، وعناصر تحكم النموذج في الموضع الحالي.

```java
        // Initialize a builder positioned at the start of the document
        DocumentBuilder builder = new DocumentBuilder(doc);
```

> **نصيحة:** إذا كنت بحاجة إلى الزر في فقرة محددة، حرك الـ builder أولاً باستخدام `builder.moveToParagraph(index, true);`.

## الخطوة 3: إدراج Forms2OleControl (زر أمر)

الآن نجيب على السؤال الأساسي **كيفية إضافة زر** في ملف Word. طريقة `insertForms2OleControl()` تنشئ زر أمر *Forms2.0* قديم، وهو أكثر عناصر التحكم توافقًا عبر إصدارات Word.

```java
        // Insert the command button at the builder's current cursor location
        Forms2OleControl cmdBtn = builder.insertForms2OleControl();
```

> **حالة خاصة:** عنصر التحكم Forms2.0 يظهر فقط في *وضع التصميم* في Word. إذا كنت بحاجة إلى زر ActiveX أحدث، فكر في استخدام `insertOleControl()` بدلاً منه، لكن العنصر القديم يعمل في معظم سيناريوهات الأتمتة.

## الخطوة 4: تكوين خصائص الزر

بعد إدراج العنصر، يمكنك **تعيين اسم زر الأمر** و**إدراج كلمة زر الأمر** (التسمية) لجعله سهل الاستخدام.

```java
        // Set the internal name used by automation scripts
        cmdBtn.setName("cmdSubmit");

        // Set the text that appears on the button
        cmdBtn.setCaption("Submit");
```

> **لماذا هذه الخصائص؟**  
> - `setName` يمنح الزر معرفًا يمكن لـ VBA أو الأدوات الخارجية الإشارة إليه.  
> - `setCaption` هو التسمية الظاهرة، وهو فعليًا **إنشاء كلمة زر النموذج** التي ينقر عليها المستخدمون النهائيون.

يمكنك أيضًا تعديل الحجم، الموضع، أو إضافة ماكرو عبر الوصول إلى كائن OLE الأساسي، لكن هذه المواضيع خارج نطاق هذا الدليل السريع.

## الخطوة 5: حفظ المستند المعدل

أخيرًا، احفظ التغييرات في ملف جديد. هذه الخطوة **تنشئ كلمة زر النموذج** في المستند الناتج.

```java
        // Save the updated document
        doc.save("YOUR_DIRECTORY/output.docx");
    }
}
```

> **النتيجة:** عند فتح `output.docx` في Microsoft Word، ستظهر زرًا بعنوان “Submit”. عندما تحول Word إلى *وضع التصميم* (Developer → Design Mode)، يمكنك النقر المزدوج على الزر لإرفاق ماكرو أو استخدامه كعنصر نائب في نموذج.

### النتيجة المتوقعة

عند فتح الملف المحفوظ:

- يتم استبدال موضع الإدراج بالزر.
- الزر يعرض التسمية **Submit**.
- الاسم الداخلي للزر هو **cmdSubmit**، ويمكنك الإشارة إليه في VBA أو سكريبتات الأتمتة الخارجية.

## الأسئلة الشائعة والاختلافات

### كيف تضيف زر إلى فقرة محددة؟

```java
builder.moveToParagraph(2, true); // moves to third paragraph (0‑based index)
Forms2OleControl btn = builder.insertForms2OleControl();
btn.setName("btnThirdParagraph");
btn.setCaption("Click Me");
```

### كيف تُدرج زرًا داخل خلية جدول؟

```java
Table table = builder.startTable();
builder.insertCell();
builder.insertCell();
builder.endTable();

builder.moveToCell(0, 0, 0, 0, true); // first row, first cell
Forms2OleControl cellBtn = builder.insertForms2OleControl();
cellBtn.setCaption("Cell Button");
```

### ماذا لو احتجت زرًا أكبر؟

```java
cmdBtn.setWidth(100);   // width in points
cmdBtn.setHeight(30);   // height in points
```

### كيف **تُدخل كلمة زر الأمر** باستخدام لغة مختلفة (مثل C#)؟

تنطبق نفس المنطق؛ استبدل بنية Java بما يعادلها في C#:

```csharp
Document doc = new Document("input.docx");
DocumentBuilder builder = new DocumentBuilder(doc);
Forms2OleControl btn = builder.InsertForms2OleControl();
btn.Name = "cmdSubmit";
btn.Caption = "Submit";
doc.Save("output.docx");
```

## نصائح احترافية ومخاطر

- **نصيحة احترافية:** دائمًا استدعِ `builder.moveToDocumentEnd()` قبل إدراج زر إذا كنت تريد وضعه في نهاية المستند تمامًا.  
- **احذر من:** حفظ الملف في نفس الملف المفتوح قد يفسد المستند إذا حدث استثناء. استخدم مسار إخراج منفصل كما هو موضح.  
- **التوافق:** زر Forms2.0 القديم يعمل في Word 2007‑2021. بالنسبة لـ Word على الويب، فكر في استخدام عناصر التحكم بالمحتوى بدلاً منه.  
- **الأداء:** تحميل مستندات كبيرة جدًا (>100 MB) قد يستهلك ذاكرة كبيرة. استخدم `Document.load(InputStream, LoadOptions)` مع `LoadOptions.setLoadFormat(LoadFormat.DOCX)` لتقليل استهلاك الموارد.

## مثال كامل يعمل

فيما يلي البرنامج الكامل الجاهز للتنفيذ بلغة Java. انسخه في فئة باسم `WordButtonDemo.java`، عدل مسارات الملفات، وشغّل `mvn compile exec:java`.

```java
import com.aspose.words.*;

public class WordButtonDemo {
    public static void main(String[] args) throws Exception {
        // 1. Load the source document
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // 2. Create a builder positioned at the start
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 3. Insert a command button (Forms2OleControl)
        Forms2OleControl cmdBtn = builder.insertForms2OleControl();

        // 4. Set button properties – this is where we **set command button name**
        cmdBtn.setName("cmdSubmit");   // internal identifier
        cmdBtn.setCaption("Submit");   // visible text (creates form button word)

        // 5. Save the edited document
        doc.save("YOUR_DIRECTORY/output.docx");
    }
}
```

شغّل البرنامج وافتح `output.docx` للتحقق من ظهور الزر كما هو متوقع.

## الخلاصة

أنت الآن تعرف كيف **تحرّر مستند Word برمجيًا** لت **إدراج كلمة زر الأمر**، **إنشاء كلمة زر النموذج**، و**تعيين اسم زر الأمر** باستخدام Aspose.Words for Java. هذه الطريقة تلغي التحرير اليدوي، تمكّن من معالجة النماذج دفعةً واحدة، وتندمج بسلاسة مع سير العمل الآلي.

بعد ذلك، قد ترغب في استكشاف:

- إضافة ماكرو VBA إلى الزر (`cmdBtn.getOleFormat().setMacroName("MyMacro")`)  
- استخدام **عناصر التحكم بالمحتوى** لتجارب نماذج أغنى (`builder.insertCheckBox()` إلخ)  
- أتمتة الإدراج الجماعي عبر مستندات متعددة باستخدام حلقة  

لا تتردد في تجربة حجم الزر، موضعه، ومعالجة الأحداث لتناسب السيناريو الخاص بك. برمجة سعيدة!

## ما الذي يجب أن تتعلمه بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات الموضحة في هذا الدليل. كل مورد يتضمن أمثلة كود كاملة مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف أساليب تنفيذ بديلة في مشاريعك.

- [كيفية إضافة زر أمر برمجيًا في مستند Word](/words/english/net/working-with-oleobjects-and-activex/how-to-add-a-command-button-programmatically-in-a-word-docum/)
- [إنشاء مستند Word برمجيًا وإضافة زر ActiveX](/words/english/net/working-with-oleobjects-and-activex/create-word-document-programmatically-and-add-activex-button/)
- [إضافة زر أمر إلى مستند Word باستخدام Aspose.Words – دليل كامل](/words/english/net/working-with-oleobjects-and-activex/add-command-button-to-word-document-with-aspose-words-comple/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}