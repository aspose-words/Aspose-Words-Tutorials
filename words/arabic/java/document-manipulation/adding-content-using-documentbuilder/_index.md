---
title: إضافة المحتوى باستخدام DocumentBuilder في Aspose.Words لـ Java
linktitle: إضافة المحتوى باستخدام DocumentBuilder
second_title: واجهة برمجة تطبيقات معالجة المستندات في Java Aspose.Words
description: إتقان إنشاء المستندات باستخدام Aspose.Words for Java. دليل خطوة بخطوة لإضافة النصوص والجداول والصور والمزيد. أنشئ مستندات Word مذهلة دون عناء.
weight: 26
url: /ar/java/document-manipulation/adding-content-using-documentbuilder/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# إضافة المحتوى باستخدام DocumentBuilder في Aspose.Words لـ Java


## مقدمة حول إضافة المحتوى باستخدام DocumentBuilder في Aspose.Words لـ Java

في هذا الدليل التفصيلي، سنستكشف كيفية استخدام Aspose.Words لـ DocumentBuilder في Java لإضافة أنواع مختلفة من المحتوى إلى مستند Word. سنتناول إدراج النصوص والجداول والقواعد الأفقية وحقول النماذج وHTML والارتباطات التشعبية وجدول المحتويات والصور المضمنة والعائمة والفقرات والمزيد. لنبدأ!

## المتطلبات الأساسية

 قبل أن تبدأ، تأكد من إعداد مكتبة Aspose.Words for Java في مشروعك. يمكنك تنزيلها من[هنا](https://releases.aspose.com/words/java/).

## إضافة نص

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// إدراج فقرة نصية بسيطة
builder.write("This is a simple text paragraph.");

// حفظ المستند
doc.save("path/to/your/document.docx");
```

## إضافة الجداول

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

//ابدأ جدولاً
Table table = builder.startTable();

// إدراج الخلايا والمحتوى
builder.insertCell();
builder.write("Cell 1");

builder.insertCell();
builder.write("Cell 2");

// انهاء الجدول
builder.endTable();

// حفظ المستند
doc.save("path/to/your/document.docx");
```

## إضافة قاعدة أفقية

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// إدراج خط أفقي
builder.insertHorizontalRule();

// حفظ المستند
doc.save("path/to/your/document.docx");
```

## إضافة حقول النموذج

### حقل نموذج إدخال النص

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// إدراج حقل نموذج إدخال النص
builder.insertTextInput("TextInput", TextFormFieldType.REGULAR, "", "Default text", 0);

// حفظ المستند
doc.save("path/to/your/document.docx");
```

### حقل نموذج مربع الاختيار

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// إدراج حقل نموذج مربع الاختيار
builder.insertCheckBox("CheckBox", true, true, 0);

// حفظ المستند
doc.save("path/to/your/document.docx");
```

### حقل نموذج المربع المنسدل

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// تحديد العناصر لمربع المجموعة
String[] items = { "Option 1", "Option 2", "Option 3" };

// إدراج حقل نموذج مربع المجموعة
builder.insertComboBox("DropDown", items, 0);

// حفظ المستند
doc.save("path/to/your/document.docx");
```

## إضافة HTML

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// إدراج محتوى HTML
builder.insertHtml("<p>This is an HTML paragraph.</p>");

// حفظ المستند
doc.save("path/to/your/document.docx");
```

## إضافة الارتباطات التشعبية

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// إدراج ارتباط تشعبي
builder.write("Visit ");
builder.getFont().setColor(Color.BLUE);
builder.getFont().setUnderline(Underline.SINGLE);
builder.insertHyperlink("Aspose Website", "http://www.aspose.com"، خطأ);
builder.getFont().clearFormatting();
builder.write(" for more information.");

// حفظ المستند
doc.save("path/to/your/document.docx");
```

## إضافة جدول المحتويات

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// إدراج جدول المحتويات
builder.insertTableOfContents("\\o \"1-3\" \\h \\z \\u");

// إضافة محتوى المستند
// ...

// تحديث جدول المحتويات
doc.updateFields();

// حفظ المستند
doc.save("path/to/your/document.docx");
```

## إضافة الصور

### صورة مضمنة

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// إدراج صورة مضمنة
builder.insertImage("path/to/your/image.png");

// حفظ المستند
doc.save("path/to/your/document.docx");
```

### الصورة العائمة

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// إدراج صورة عائمة
builder.insertImage("path/to/your/image.png", RelativeHorizontalPosition.MARGIN, 100.0, RelativeVerticalPosition.MARGIN, 100.0, 200.0, 100.0, WrapType.SQUARE);

// حفظ المستند
doc.save("path/to/your/document.docx");
```

## إضافة فقرات

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// تعيين تنسيق الفقرة
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

// إدراج فقرة
builder.writeln("This is a formatted paragraph.");

// حفظ المستند
doc.save("path/to/your/document.docx");
```

## الخطوة 10: تحريك المؤشر

 يمكنك التحكم في موضع المؤشر داخل المستند باستخدام طرق مختلفة مثل`moveToParagraph`, `moveToCell`، والمزيد. إليك مثال:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// نقل المؤشر إلى فقرة محددة
builder.moveToParagraph(2, 0);

// إضافة المحتوى في موضع المؤشر الجديد
builder.writeln("This is the 3rd paragraph.");
```

هذه بعض العمليات الشائعة التي يمكنك إجراؤها باستخدام Aspose.Words لـ DocumentBuilder في Java. استكشف وثائق المكتبة للحصول على ميزات أكثر تقدمًا وخيارات تخصيص. إنشاء مستندات سعيد!


## خاتمة

في هذا الدليل الشامل، استكشفنا قدرات Aspose.Words لـ DocumentBuilder في Java لإضافة أنواع مختلفة من المحتوى إلى مستندات Word. لقد قمنا بتغطية النصوص والجداول والقواعد الأفقية وحقول النماذج وHTML والارتباطات التشعبية وجدول المحتويات والصور والفقرات وحركة المؤشر.

## الأسئلة الشائعة

### س: ما هو Aspose.Words لـ Java؟

ج: Aspose.Words for Java عبارة عن مكتبة Java تتيح للمطورين إنشاء مستندات Microsoft Word وتعديلها ومعالجتها برمجيًا. وهي توفر مجموعة واسعة من الميزات لإنشاء المستندات وتنسيقها وإدراج المحتوى.

### س: كيف يمكنني إضافة جدول المحتويات إلى مستندي؟

أ: لإضافة جدول المحتويات، استخدم`DocumentBuilder` لإدراج حقل جدول المحتويات في مستندك. تأكد من تحديث الحقول في المستند بعد إضافة المحتوى لملء جدول المحتويات. فيما يلي مثال:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// إدراج حقل جدول المحتويات
builder.insertTableOfContents("\\o \"1-3\" \\h \\z \\u");

// إضافة محتوى المستند
// ...

// تحديث جدول المحتويات
doc.updateFields();
```

### س: كيف يمكنني إدراج الصور في مستند باستخدام Aspose.Words لـ Java؟

 أ: يمكنك إدراج الصور، سواء المضمنة أو العائمة، باستخدام`DocumentBuilder`وفيما يلي أمثلة لكلا الأمرين:

#### صورة مضمنة:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// إدراج صورة مضمنة
builder.insertImage("path/to/your/image.png");
```

#### الصورة العائمة:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// إدراج صورة عائمة
builder.insertImage("path/to/your/image.png", RelativeHorizontalPosition.MARGIN, 100.0, RelativeVerticalPosition.MARGIN, 100.0, 200.0, 100.0, WrapType.SQUARE);
```

### س: هل يمكنني تنسيق النص والفقرات عند إضافة المحتوى؟

 ج: نعم، يمكنك تنسيق النص والفقرات باستخدام`DocumentBuilder`يمكنك ضبط خصائص الخط ومحاذاة الفقرة والمسافة البادئة وغير ذلك. إليك مثال:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// تعيين تنسيق الخط والفقرة
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

// إدراج فقرة منسقة
builder.writeln("This is a formatted paragraph.");
```

### س: كيف يمكنني نقل المؤشر إلى مكان محدد داخل المستند؟

 أ: يمكنك التحكم في موضع المؤشر باستخدام طرق مثل`moveToParagraph`, `moveToCell`، والمزيد. إليك مثال:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// نقل المؤشر إلى فقرة محددة
builder.moveToParagraph(2, 0);

// إضافة المحتوى في موضع المؤشر الجديد
builder.writeln("This is the 3rd paragraph.");
```

هذه بعض الأسئلة والأجوبة الشائعة لمساعدتك في البدء باستخدام Aspose.Words لـ DocumentBuilder في Java. إذا كانت لديك أسئلة أخرى أو كنت بحاجة إلى مزيد من المساعدة، فراجع[توثيقات المكتبة](https://reference.aspose.com/words/java/) أو اطلب المساعدة من مجتمع Aspose.Words وموارد الدعم.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
