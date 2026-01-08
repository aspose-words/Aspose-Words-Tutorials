---
date: 2026-01-01
description: تعلم كيفية إنشاء حقول النماذج وإضافة النصوص والجداول والصور والروابط
  التشعبية والمزيد باستخدام Aspose.Words for Java DocumentBuilder. دليل خطوة بخطوة
  للمطورين.
linktitle: Adding Content using DocumentBuilder
second_title: Aspose.Words Java Document Processing API
title: كيفية إنشاء حقول نموذج وإضافة محتوى باستخدام DocumentBuilder في Aspose.Words
  للغة Java
url: /ar/java/document-manipulation/adding-content-using-documentbuilder/
weight: 26
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# إضافة محتوى باستخدام DocumentBuilder في Aspose.Words للـ Java

## مقدمة حول إضافة محتوى باستخدام DocumentBuilder في Aspose.Words للـ Java

في هذا الدليل خطوة بخطوة، ستقوم **بإنشاء حقول نموذج** وإضافة مجموعة متنوعة من المحتوى—نص، جداول، خطوط أفقية، HTML، روابط تشعبية، صور، وأكثر—إلى مستند Word باستخدام Aspose.Words للـ Java. سواءً كنت تبني تقريرًا، قالب عقد، أو نموذجًا تفاعليًا، فإن فئة `DocumentBuilder` تمنحك تحكمًا دقيقًا في كل عنصر. هيا نبدأ!

## إجابات سريعة
- **كيف يمكنني إنشاء حقول نموذج؟** استخدم `insertTextInput`، `insertCheckBox`، أو `insertComboBox` على كائن `DocumentBuilder`.
- **ما الطريقة التي تضيف نصًا عاديًا؟** استدعِ `builder.write("Your text")` أو `builder.writeln("Your text")`.
- **هل يمكنني إدراج خط أفقي؟** نعم—`builder.insertHorizontalRule()` يضيف فاصلًا خطيًا.
- **كيف يمكنني تضمين HTML؟** استخدم `builder.insertHtml("<p>HTML content</p>")`.
- **كيف يمكنني إضافة صورة داخل النص؟** `builder.insertImage("path/to/image.png")` يضع الصورة داخل تدفق النص.

## ما هو DocumentBuilder ولماذا نستخدمه لإنشاء حقول نموذج؟

`DocumentBuilder` هو API سلس من Aspose.Words لإنشاء وتحرير مستندات Word برمجيًا. يقوم بتجريد بنية OpenXML منخفض المستوى، مما يسمح لك بالتركيز على *ما* تريد إضافته—مثل **حقول نموذج**—بدلاً من *كيف* تبدو XML. هذا يجعله مثاليًا لإنشاء نماذج ديناميكية، عقود، أو أي مستند يتطلب تفاعل المستخدم.

## المتطلبات المسبقة

قبل أن تبدأ، تأكد من تثبيت مكتبة Aspose.Words للـ Java في مشروعك. يمكنك تنزيلها من [here](https://releases.aspose.com/words/java/).

## إضافة نص (كيفية إضافة نص)

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a simple text paragraph
builder.write("This is a simple text paragraph.");

// Save the document
doc.save("path/to/your/document.docx");
```

## إضافة جداول

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Start a table
Table table = builder.startTable();

// Insert cells and content
builder.insertCell();
builder.write("Cell 1");

builder.insertCell();
builder.write("Cell 2");

// End the table
builder.endTable();

// Save the document
doc.save("path/to/your/document.docx");
```

## إضافة خط أفقي (إضافة خط أفقي)

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a horizontal rule
builder.insertHorizontalRule();

// Save the document
doc.save("path/to/your/document.docx");
```

## إضافة حقول نموذج (إنشاء حقول نموذج)

### حقل نموذج إدخال نص

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a text input form field
builder.insertTextInput("TextInput", TextFormFieldType.REGULAR, "", "Default text", 0);

// Save the document
doc.save("path/to/your/document.docx");
```

### حقل نموذج مربع اختيار

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a check box form field
builder.insertCheckBox("CheckBox", true, true, 0);

// Save the document
doc.save("path/to/your/document.docx");
```

### حقل نموذج قائمة منسدلة

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Define items for the combo box
String[] items = { "Option 1", "Option 2", "Option 3" };

// Insert a combo box form field
builder.insertComboBox("DropDown", items, 0);

// Save the document
doc.save("path/to/your/document.docx");
```

## إضافة HTML (إدراج كلمة html)

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert HTML content
builder.insertHtml("<p>This is an HTML paragraph.</p>");

// Save the document
doc.save("path/to/your/document.docx");
```

## إضافة روابط تشعبية (كيفية إضافة رابط تشعبي)

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a hyperlink
builder.write("Visit ");
builder.getFont().setColor(Color.BLUE);
builder.getFont().setUnderline(Underline.SINGLE);
builder.insertHyperlink("Aspose Website", "http://www.aspose.com", false);
builder.getFont().clearFormatting();
builder.write(" for more information.");

// Save the document
doc.save("path/to/your/document.docx");
```

## إضافة جدول محتويات

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a table of contents
builder.insertTableOfContents("\\o \"1-3\" \\h \\z \\u");

// Add document content
// ...

// Update the table of contents
doc.updateFields();

// Save the document
doc.save("path/to/your/document.docx");
```

## إضافة صور

### صورة داخلية (إدراج صورة داخلية)

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert an inline image
builder.insertImage("path/to/your/image.png");

// Save the document
doc.save("path/to/your/document.docx");
```

### صورة عائمة

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a floating image
builder.insertImage("path/to/your/image.png", RelativeHorizontalPosition.MARGIN, 100.0, RelativeVerticalPosition.MARGIN, 100.0, 200.0, 100.0, WrapType.SQUARE);

// Save the document
doc.save("path/to/your/document.docx");
```

## إضافة فقرات

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Set paragraph formatting
Font font = builder.getFont();
font.setSize(16.0);
font.setBold(true);
font.setColor(Color.BLUE);
font.setName("Arial");
font.setUnderline(Underline.DASH);

ParagraphFormat paragraphFormat = builder.getParagraphFormat();
paragraphFormat.setFirstLineIndent(8.0);
paragraphFormat.setAlignment(ParagraphAlignment.JUSTIFY);
paragraphFormat.setKeepTogether(true);

// Insert a paragraph
builder.writeln("This is a formatted paragraph.");

// Save the document
doc.save("path/to/your/document.docx");
```

## تحريك المؤشر (الخطوة 10)

يمكنك التحكم في موضع المؤشر داخل المستند باستخدام طرق مثل `moveToParagraph`، `moveToCell`، إلخ.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Move the cursor to a specific paragraph
builder.moveToParagraph(2, 0);

// Add content at the new cursor position
builder.writeln("This is the 3rd paragraph.");
```

هذه بعض العمليات الشائعة التي يمكنك تنفيذها باستخدام `DocumentBuilder` في Aspose.Words للـ Java. استكشف وثائق المكتبة للمزيد من الميزات المتقدمة وخيارات التخصيص. نتمنى لك إنشاء مستندات سعيد!

## الخلاصة

في هذا الدليل الشامل، أظهرنا كيفية **إنشاء حقول نموذج** وإضافة أنواع مختلفة من المحتوى—نص، جداول، خطوط أفقية، HTML، روابط تشعبية، جدول محتويات، صور، فقرات منسقة، وتنقل المؤشر—باستخدام `DocumentBuilder` في Aspose.Words للـ Java. الآن لديك أساس قوي لتوليد مستندات Word ديناميكية وتفاعلية برمجيًا.

## الأسئلة المتكررة

### س: ما هو Aspose.Words للـ Java؟

ج: Aspose.Words للـ Java هي مكتبة جافا تسمح للمطورين بإنشاء وتعديل ومعالجة مستندات Microsoft Word برمجيًا. توفر مجموعة واسعة من الميزات لإنشاء المستندات، التنسيق، وإدراج المحتوى.

### س: كيف يمكنني إضافة جدول محتويات إلى مستندى؟

ج: لإضافة جدول محتويات، استخدم `DocumentBuilder` لإدراج حقل TOC ثم استدعِ `doc.updateFields()` بعد إضافة المحتوى.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a table of contents field
builder.insertTableOfContents("\\o \"1-3\" \\h \\z \\u");

// Add document content
// ...

// Update the table of contents
doc.updateFields();
```

### س: كيف يمكنني إدراج صور في مستند باستخدام Aspose.Words للـ Java؟

ج: يمكنك إدراج الصور، سواءً داخلية أو عائمة، باستخدام `DocumentBuilder`.

#### صورة داخلية:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert an inline image
builder.insertImage("path/to/your/image.png");
```

#### صورة عائمة:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a floating image
builder.insertImage("path/to/your/image.png", RelativeHorizontalPosition.MARGIN, 100.0, RelativeVerticalPosition.MARGIN, 100.0, 200.0, 100.0, WrapType.SQUARE);
```

### س: هل يمكنني تنسيق النص والفقرات عند إضافة المحتوى؟

ج: نعم، يمكنك تنسيق النص والفقرات باستخدام `DocumentBuilder`. اضبط خصائص الخط، محاذاة الفقرة، المسافة البادئة، والمزيد قبل كتابة المحتوى.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Set font and paragraph formatting
Font font = builder.getFont();
font.setSize(16.0);
font.setBold(true);
font.setColor(Color.BLUE);
font.setName("Arial");
font.setUnderline(Underline.DASH);

ParagraphFormat paragraphFormat = builder.getParagraphFormat();
paragraphFormat.setFirstLineIndent(8.0);
paragraphFormat.setAlignment(ParagraphAlignment.JUSTIFY);
paragraphFormat.setKeepTogether(true);

// Insert a formatted paragraph
builder.writeln("This is a formatted paragraph.");
```

### س: كيف يمكنني تحريك المؤشر إلى موقع محدد داخل المستند؟

ج: استخدم طرقًا مثل `moveToParagraph`، `moveToCell`، إلخ، لتحديد موقع المؤشر قبل إدراج محتوى جديد.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Move the cursor to a specific paragraph
builder.moveToParagraph(2, 0);

// Add content at the new cursor position
builder.writeln("This is the 3rd paragraph.");
```

هذه الإجابات تغطي أكثر السيناريوهات شيوعًا عند العمل مع `DocumentBuilder` في Aspose.Words للـ Java. للحصول على تفاصيل أعمق، راجع [وثائق المكتبة](https://reference.aspose.com/words/java/) أو انضم إلى مجتمع Aspose.Words للحصول على الدعم.

---

**Last Updated:** 2026-01-01  
**Tested With:** Aspose.Words for Java 24.12  
**Author:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}