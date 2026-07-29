---
category: general
date: 2026-07-29
description: 'دروس ضبط حجم الزر في جافا: تعلم كيفية إدراج زر أمر ActiveX في مستند
  Word باستخدام جافا و Aspose.Words، بالإضافة إلى ضبط الحجم وإنشاء مستند فارغ.'
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- set button size java
- how to insert activex
- how to set button
- java create blank word
- insert command button word
language: ar
lastmod: 2026-07-29
og_description: دليل ضبط حجم الزر في جافا يوضح كيفية إدراج زر أمر ActiveX في ملف Word
  باستخدام جافا، وضبط حجمه، وحفظ المستند برمجياً.
og_image_alt: set button size java example showing a Word document with an ActiveX
  command button
og_title: تحديد حجم الزر في جافا – إضافة زر أمر ActiveX إلى Word باستخدام جافا
schemas:
- author: Aspose
  dateModified: '2026-07-29'
  description: 'set button size java tutorial: learn how to insert ActiveX command
    button in a Word document using Java and Aspose.Words, plus sizing and blank document
    creation.'
  headline: set button size java – Insert ActiveX Command Button in Word
  type: TechArticle
- description: 'set button size java tutorial: learn how to insert ActiveX command
    button in a Word document using Java and Aspose.Words, plus sizing and blank document
    creation.'
  name: set button size java – Insert ActiveX Command Button in Word
  steps:
  - name: 1. Set Up the Project and Import Aspose.Words
    text: 'First, create a new Maven (or Gradle) project and add the Aspose.Words
      dependency shown above. Then, import the required classes in your Java source
      file:'
  - name: 2. java create blank word Document
    text: Now we actually **java create blank word** document. This is the foundation
      on which we’ll later **insert command button word**.
  - name: 3. Initialize DocumentBuilder and Insert the ActiveX Control
    text: 'The `DocumentBuilder` is a helper that lets us add content, paragraphs,
      tables, and, yes, ActiveX controls. Here’s where we answer **how to insert activex**:'
  - name: 4. How to Set Button Size Java – Adjust Width and Height
    text: 'Now comes the heart of the tutorial: **how to set button size java**. The
      control exposes several layout properties—`Left`, `Top`, `Width`, and `Height`.
      Setting them directly controls the button’s appearance on the page.'
  - name: 5. Save the Document
    text: 'Finally, persist the document to disk:'
  - name: What if the button doesn’t appear in Word?
    text: '- **Check the Word version.** ActiveX controls require the desktop version
      of Word; Word Online strips them out. - **Make sure the Aspose.Words license
      is applied** (if you’re using a paid edition). An unlicensed evaluation version
      may embed a watermark but still shows the control.'
  - name: Can I change the button’s font or color?
    text: Yes. After inserting the control, you can access its underlying OLE object
      and manipulate the VBA properties. That’s a more advanced topic—look into `commandButton.getOleObject().setProperty("ForeColor",
      0xFF0000)` for a red caption, for example.
  - name: How do I handle the button’s click event?
    text: ActiveX command buttons fire a VBA `Click` event. To make the button functional,
      you’ll need to embed a macro in the same document. Aspose.Words can add a macro
      module via the `Document.getMacros()` API, but the macro code itself must be
      written in VBA.
  - name: What about different button types?
    text: 'Aspose.Words supports many `Forms2OleControlType` values: `CHECKBOX`, `OPTIONBUTTON`,
      `LISTBOX`, etc. Swap the enum constant in the `insertForms2OleControl` call
      to experiment.'
  type: HowTo
tags:
- Java
- Aspose.Words
- ActiveX
- Word Automation
title: تحديد حجم الزر في جافا – إدراج زر أمر ActiveX في Word
url: /ar/java/using-document-elements/set-button-size-java-insert-activex-command-button-in-word/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# تحديد حجم الزر جافا – إدراج زر أمر ActiveX في Word

هل تساءلت يومًا **كيف تحدد حجم الزر جافا** عندما تقوم بأتمتة مستندات Word؟ ربما تبني أداة تقارير تحتاج إلى زر “إرسال” قابل للنقر داخل ملف .docx. في هذا الدرس سنستعرض العملية بالكامل — إنشاء مستند Word فارغ، إدراج زر أمر ActiveX، وتحديد عرضه وارتفاعه بدقة — كل ذلك باستخدام Java و Aspose.Words.

سنجيب أيضًا على سؤال **كيف يتم إدراج activex** المتكرر بين المطورين. في النهاية ستحصل على برنامج قابل للتنفيذ ينتج ملف Word يحتوي على زر أمر بالحجم المثالي، جاهز لمزيد من التخصيص.

---

## ما الذي ستحتاجه

قبل أن نبدأ، تأكد من توفر ما يلي:

- **مجموعة تطوير جافا (JDK) 8 أو أحدث** – الكود يُترجم مع أي JDK حديث.
- **Aspose.Words for Java** (أحدث إصدار حتى يوليو 2026). احصل على ملف JAR من [موقع Aspose](https://products.aspose.com/words/java) أو عبر Maven:
  ```xml
  <dependency>
      <groupId>com.aspose</groupId>
      <artifactId>aspose-words</artifactId>
      <version>23.10</version>
  </dependency>
  ```
- بيئة تطوير متكاملة أو محرر نصوص بسيط — IntelliJ IDEA، Eclipse، أو VS Code يكفي.
- مجلد تريد حفظ ملف **CommandButton.docx** المُولد فيه.

هذا كل شيء. لا مكتبات إضافية للتعامل مع Office، ولا حيل COM، فقط Java صافية.

---

## تنفيذ خطوة بخطوة

سنقسم الحل إلى خمس خطوات منطقية. كل خطوة لها عنوان H2 مخصص؛ إحداها تحتوي على **الكلمة المفتاحية الأساسية** لتلبية متطلبات SEO.

### 1. إعداد المشروع واستيراد Aspose.Words

أولًا، أنشئ مشروع Maven (أو Gradle) جديد وأضف تبعية Aspose.Words كما هو موضح أعلاه. ثم استورد الفئات المطلوبة في ملف Java الخاص بك:

```java
import com.aspose.words.*;
```

> **نصيحة محترف:** إذا كنت تستخدم IDE، دعها تستورد الفئات تلقائيًا. هذا يوفر الكثير من الكتابة ويمنع الأخطاء المطبعية.

### 2. java create blank word Document

الآن سنقوم فعليًا **بإنشاء مستند Word فارغ باستخدام جافا**. هذا هو الأساس الذي سنُدرج عليه لاحقًا **زر الأمر في Word**.

```java
// Step 2: Create a new blank document
Document document = new Document();          // Starts with a clean, empty .docx
```

كائن `Document` يمثل ملف Word بالكامل في الذاكرة. في هذه المرحلة لا توجد صفحات ولا نص — مجرد صفحة بيضاء.

### 3. تهيئة DocumentBuilder وإدراج عنصر التحكم ActiveX

`DocumentBuilder` هو أداة مساعدة تسمح لنا بإضافة محتوى، فقرات، جداول، ونعم، عناصر تحكم ActiveX. هنا نجيب على سؤال **كيف يتم إدراج activex**:

```java
// Step 3: Initialize a DocumentBuilder to work with the document
DocumentBuilder builder = new DocumentBuilder(document);

// Insert an ActiveX command button (COMMANDBUTTON is a built‑in type)
Forms2OleControl commandButton = builder.insertForms2OleControl(
        Forms2OleControlType.COMMANDBUTTON);
```

`Forms2OleControl` هو الغلاف الذي تقدمه Aspose حول كائن OLE. بتحديد `COMMANDBUTTON` نخبر Word بدمج زر أمر ActiveX كلاسيكي.

### 4. كيف تحدد حجم الزر جافا – تعديل العرض والارتفاع

الآن يأتي جوهر الدرس: **كيف تحدد حجم الزر جافا**. العنصر يُظهر عدة خصائص تخطيطية — `Left`، `Top`، `Width`، و `Height`. ضبطها مباشرة يتحكم في مظهر الزر على الصفحة.

```java
// Step 4: Set button properties, including size
commandButton.setCaption("Click Me"); // Text shown on the button
commandButton.setLeft(100);           // Distance from the left margin (points)
commandButton.setTop(200);            // Distance from the top margin (points)
commandButton.setWidth(120);          // Width in points (≈1.67 inches)
commandButton.setHeight(30);          // Height in points (≈0.42 inches)
```

لماذا هذه القيم؟ في Word، النقطة الواحدة تساوي 1/72 من البوصة. لذا عرض `120` نقطة يساوي تقريبًا 1.67 بوصة — حجم كافٍ لتسمية قابلة للقراءة، دون أن يكون مبالغًا فيه. عدّل القيم لتناسب تخطيطك؛ نفس الخصائص تجيب أيضًا على سؤال **كيف تحدد الزر** إذا كان لديك.

> **ملاحظة:** إذا كنت بحاجة إلى نوع زر مختلف (مثل مربع اختيار)، استبدل `Forms2OleControlType.COMMANDBUTTON` بالقيمة المناسبة من الـ enum.

### 5. حفظ المستند

أخيرًا، احفظ المستند على القرص:

```java
// Step 5: Save the document with the embedded ActiveX control
document.save("YOUR_DIRECTORY/CommandButton.docx");
```

استبدل `YOUR_DIRECTORY` بمسار مطلق أو نسبي على جهازك. بعد تشغيل البرنامج، افتح الملف المُولد في Microsoft Word. سترى زرًا مكتوبًا عليه “Click Me” موضعًا على بعد 100 نقطة من اليسار و200 نقطة من الأعلى، بحجم يطابق ما حددناه.

---

## مثال كامل يعمل

فيما يلي الفئة Java الكاملة الجاهزة للتنفيذ. انسخها إلى `CommandButtonActiveX.java`، عدّل مسار الإخراج، ثم اضغط **Run**.

```java
import com.aspose.words.*;

public class CommandButtonActiveX {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document (java create blank word)
        Document document = new Document();

        // Step 2: Initialize a DocumentBuilder to work with the document
        DocumentBuilder builder = new DocumentBuilder(document);

        // Step 3: Insert an ActiveX command button (how to insert activex)
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON);

        // Step 4: Set button properties – this is how to set button size java
        commandButton.setCaption("Click Me"); // Button text
        commandButton.setLeft(100);           // Left position (points)
        commandButton.setTop(200);            // Top position (points)
        commandButton.setWidth(120);          // Width (points)
        commandButton.setHeight(30);          // Height (points)

        // Step 5: Save the document (insert command button word)
        document.save("YOUR_DIRECTORY/CommandButton.docx");
    }
}
```

**الناتج المتوقع:** عند فتح `CommandButton.docx` في Word سيظهر صفحة واحدة تحتوي على زر “Click Me” قابل للنقر موضعه تقريبًا في منتصف الصفحة. أبعاد الزر تتطابق مع القيم التي ضبطتها، مما يؤكد أن **تحديد حجم الزر جافا** يعمل كما هو متوقع.

---

## أسئلة شائعة وحالات خاصة

### ماذا لو لم يظهر الزر في Word؟

- **تحقق من نسخة Word.** تتطلب عناصر تحكم ActiveX نسخة Word المكتبية؛ Word Online يزيلها.
- **تأكد من تطبيق ترخيص Aspose.Words** (إذا كنت تستخدم نسخة مدفوعة). قد تُظهر النسخة التجريبية غير المرخصة علامة مائية لكنها لا تزال تعرض العنصر.

### هل يمكنني تغيير خط الزر أو لونه؟

نعم. بعد إدراج العنصر، يمكنك الوصول إلى كائن OLE الأساسي وتعديل خصائص VBA. هذا موضوع متقدم — ألقِ نظرة على `commandButton.getOleObject().setProperty("ForeColor", 0xFF0000)` لتغيير التسمية إلى اللون الأحمر، على سبيل المثال.

### كيف أتعامل مع حدث النقر على الزر؟

أزرار ActiveX تُطلق حدث VBA `Click`. لجعل الزر فعالًا، ستحتاج إلى تضمين ماكرو في نفس المستند. يمكن لـ Aspose.Words إضافة وحدة ماكرو عبر API `Document.getMacros()`، لكن كود الماكرو نفسه يجب أن يُكتب بلغة VBA.

### ماذا عن أنواع أزرار مختلفة؟

يدعم Aspose.Words العديد من القيم في `Forms2OleControlType`: `CHECKBOX`، `OPTIONBUTTON`، `LISTBOX`، وغيرها. استبدل الثابت في استدعاء `insertForms2OleControl` لتجربة نوع آخر.

---

## نصائح احترافية لكود جاهز للإنتاج

1. **استخدم ثوابت لقيم التخطيط** – يجعل تعديلها لاحقًا أسهل.
2. **غلف مسار الحفظ في كائن `Path`** لتجنب الفواصل الخاصة بالمنصات.
3. **حرّر كائن Document** (أو استخدم try‑with‑resources) إذا كنت تعالج ملفات متعددة في حلقة.
4. **تحقق من وجود مجلد الإخراج** قبل استدعاء `save` لتجنب `FileNotFoundException`.

---

## الخلاصة

لقد تعلمت الآن **تحديد حجم الزر جافا** عبر إنشاء ملف Word فارغ، إدراج زر أمر ActiveX، وتكوين أبعاده بدقة — كل ذلك ببضع أسطر من كود Java. يغطي هذا جوهر **كيف يتم إدراج activex**، **كيف تحدد الزر**، **إنشاء مستند Word فارغ بجافا**، و **إدراج زر أمر في Word** في مثال واحد متكامل.

ما الخطوة التالية؟ جرّب تخصيص تسمية الزر، إضافة ماكرو للرد على النقرات، أو دمج عدة عناصر تحكم في نفس الصفحة. يمكنك أيضًا استكشاف تحويل ملف .docx الناتج إلى PDF باستخدام Aspose.Words، مع الحفاظ على الزر كصورة ثابتة.

لا تتردد في التجربة، وإذا واجهت أي مشكلة، اترك تعليقًا أدناه. برمجة سعيدة!

## ما الذي ينبغي أن تتعلمه بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات التي تم توضيحها في هذا الدليل. كل مصدر يتضمن أمثلة كود كاملة مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف أساليب تنفيذ بديلة في مشاريعك.

- [How to create form fields and add content using DocumentBuilder in Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [How to Load Word Documents with Aspose.Words Java: Comprehensive Guide](/words/english/java/document-operations/aspose-words-java-master-word-processing/)
- [How to save document as pdf with Aspose.Words for Java](/words/english/java/document-loading-and-saving/saving-documents-as-pdf/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}