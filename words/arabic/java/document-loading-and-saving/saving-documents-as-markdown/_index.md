---
date: 2025-12-22
description: تعلم كيفية تصدير ماركداون عن طريق تحويل مستندات Word إلى ماركداون باستخدام
  Aspose.Words for Java. يغطي هذا الدليل خطوة بخطوة محاذاة الجداول ومعالجة الصور والمزيد.
linktitle: Saving Documents as Markdown
second_title: Aspose.Words Java Document Processing API
title: كيفية تصدير Markdown باستخدام Aspose.Words للـ Java
url: /ar/java/document-loading-and-saving/saving-documents-as-markdown/
weight: 18
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# كيفية تصدير Markdown باستخدام Aspose.Words for Java

## مقدمة حول تصدير Markdown في Aspose.Words for Java

في هذا الدرس خطوة بخطوة، **ستتعلم كيفية تصدير markdown** من مستندات Word باستخدام Aspose.Words for Java. Markdown هي لغة توصيف خفيفة الوزن مثالية للتوثيق، مولدات المواقع الثابتة، والعديد من منصات النشر. بنهاية هذا الدليل ستكون قادرًا على **تحويل Word إلى markdown**، تخصيص محاذاة الجداول، و**معالجة الصور في markdown** بسهولة.

## إجابات سريعة
- **ما هي الفئة الأساسية للحفظ كـ Markdown؟** `MarkdownSaveOptions`
- **هل يمكن تضمين الصور تلقائيًا؟** نعم – قم بتعيين مجلد الصور عبر `setImagesFolder`.
- **كيف يمكن التحكم في محاذاة الجدول؟** استخدم `TableContentAlignment` (LEFT, RIGHT, CENTER, AUTO).
- **ما هي المتطلبات الدنيا؟** JDK 8+ ومكتبة Aspose.Words for Java.
- **هل تتوفر نسخة تجريبية؟** نعم، حمّلها من موقع Aspose.

## ما هو “كيفية تصدير markdown”؟
تصدير markdown يعني أخذ مستند Word غني بالنص (`.docx`) وإنتاج ملف نصي عادي `.md` يحافظ على العناوين والجداول والصور بصيغة Markdown.

## لماذا نستخدم Aspose.Words for Java لتحويل docx مع الصور؟
Aspose.Words يتعامل مع التخطيطات المعقدة، الصور المدمجة، وهياكل الجداول دون فقدان الدقة. كما يمنحك تحكمًا دقيقًا في مخرجات Markdown، مثل محاذاة الجداول وإدارة مجلد الصور.

## المتطلبات المسبقة

- مجموعة تطوير جافا (JDK) مثبتة على نظامك.
- مكتبة Aspose.Words for Java. يمكنك تحميلها من [هنا](https://releases.aspose.com/words/java/).

## الخطوة 1: إنشاء مستند Word بسيط

أولاً، سننشئ مستندًا صغيرًا يحتوي على جدول. سيمكننا ذلك من توضيح **تخصيص محاذاة الجدول** لاحقًا.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a table with two cells
builder.insertCell();
builder.getParagraphFormat().setAlignment(ParagraphAlignment.RIGHT);
builder.write("Cell1");

builder.insertCell();
builder.getParagraphFormat().setAlignment(ParagraphAlignment.CENTER);
builder.write("Cell2");

// Save the document as Markdown
MarkdownSaveOptions saveOptions = new MarkdownSaveOptions();
doc.save("output.md", saveOptions);
```

في المقتطف أعلاه نقوم بـ:

1. إنشاء كائن `Document` جديد.
2. استخدام `DocumentBuilder` لإدراج جدول بخليةين.
3. تطبيق محاذاة الفقرة **يمين** و**وسط** داخل كل خلية.
4. حفظ الملف كـ Markdown باستخدام `MarkdownSaveOptions`.

## الخطوة 2: تخصيص محاذاة محتوى الجدول

Aspose.Words يتيح لك تحديد كيفية عرض خلايا الجدول في Markdown النهائي. يمكنك فرض محاذاة إلى اليسار أو اليمين أو الوسط، أو ترك المكتبة تقرر تلقائيًا بناءً على الفقرة الأولى في كل عمود.

```java
// Set the table content alignment to left
saveOptions.setTableContentAlignment(TableContentAlignment.LEFT);
doc.save("left_alignment.md", saveOptions);

// Set the table content alignment to right
saveOptions.setTableContentAlignment(TableContentAlignment.RIGHT);
doc.save("right_alignment.md", saveOptions);

// Set the table content alignment to center
saveOptions.setTableContentAlignment(TableContentAlignment.CENTER);
doc.save("center_alignment.md", saveOptions);

// Set the table content alignment to auto (determined by first paragraph)
saveOptions.setTableContentAlignment(TableContentAlignment.AUTO);
doc.save("auto_alignment.md", saveOptions);
```

عن طريق تبديل خاصية `TableContentAlignment` يمكنك التحكم في **تخصيص محاذاة الجدول** لمخرجات Markdown.

## الخطوة 3: معالجة الصور عند التصدير إلى markdown

عند احتواء المستند على صور، ستحتاج إلى ظهور هذه الصور بشكل صحيح في ملف `.md` المُولد. عيّن المجلد الذي يجب على Aspose.Words تفريغ الصور المستخرجة فيه.

```java
// Load a document containing images
Document doc = new Document("document_with_images.docx");

// Set the images folder path
MarkdownSaveOptions saveOptions = new MarkdownSaveOptions();
saveOptions.setImagesFolder("images_folder/");

// Save the document with images
doc.save("document_with_images.md", saveOptions);
```

استبدل `"document_with_images.docx"` بمسار ملف المصدر الخاص بك و`"images_folder/"` بالموقع الذي ترغب في تخزين الصور فيه. سيحتوي Markdown الناتج على روابط صور تشير إلى هذا المجلد، مما يتيح لك **معالجة الصور في markdown** بسلاسة.

## الكود الكامل لحفظ المستندات كـ Markdown في Aspose.Words for Java

```java
public void autoTableContentAlignment() throws Exception
{
	Document doc = new Document();
	DocumentBuilder builder = new DocumentBuilder(doc);
	builder.insertCell();
	builder.getParagraphFormat().setAlignment(ParagraphAlignment.RIGHT);
	builder.write("Cell1");
	builder.insertCell();
	builder.getParagraphFormat().setAlignment(ParagraphAlignment.CENTER);
	builder.write("Cell2");
	// Makes all paragraphs inside the table to be aligned.
	MarkdownSaveOptions saveOptions = new MarkdownSaveOptions();
	{
		saveOptions.setTableContentAlignment(TableContentAlignment.LEFT);
	}
	doc.save("Your Directory Path" + "WorkingWithMarkdownSaveOptions.LeftTableContentAlignment.md", saveOptions);
	saveOptions.setTableContentAlignment(TableContentAlignment.RIGHT);
	doc.save("Your Directory Path" + "WorkingWithMarkdownSaveOptions.RightTableContentAlignment.md", saveOptions);
	saveOptions.setTableContentAlignment(TableContentAlignment.CENTER);
	doc.save("Your Directory Path" + "WorkingWithMarkdownSaveOptions.CenterTableContentAlignment.md", saveOptions);
	// The alignment in this case will be taken from the first paragraph in corresponding table column.
	saveOptions.setTableContentAlignment(TableContentAlignment.AUTO);
	doc.save("Your Directory Path" + "WorkingWithMarkdownSaveOptions.AutoTableContentAlignment.md", saveOptions);
}
@Test
public void setImagesFolder() throws Exception
{
	Document doc = new Document("Your Directory Path" + "Image bullet points.docx");
	MarkdownSaveOptions saveOptions = new MarkdownSaveOptions(); { saveOptions.setImagesFolder("Your Directory Path" + "Images"); }
	try(ByteArrayOutputStream stream = new ByteArrayOutputStream())
	{
		doc.save(stream, saveOptions);
	}
}
```

## المشكلات الشائعة والحلول

| المشكلة | الحل |
|-------|----------|
| الصور لا تظهر في ملف `.md` | تأكد من أن `setImagesFolder` يشير إلى دليل قابل للكتابة وأن المجلد مُشار إليه بشكل صحيح في Markdown المُولد. |
| محاذاة الجدول غير صحيحة | استخدم `TableContentAlignment.AUTO` للسماح لـ Aspose.Words باستخلاص أفضل محاذاة بناءً على الفقرة الأولى في كل عمود. |
| ملف الإخراج فارغ | تأكد من أن كائن `Document` يحتوي فعليًا على محتوى قبل استدعاء `save`. |

## الأسئلة المتكررة

**س: كيف يمكنني تثبيت Aspose.Words for Java؟**  
ج: يمكن تثبيت Aspose.Words for Java عن طريق إضافة المكتبة إلى مشروع Java الخاص بك. يمكنك تحميل المكتبة من [هنا](https://releases.aspose.com/words/java/) واتباع تعليمات التثبيت الواردة في الوثائق.

**س: هل يمكنني تحويل مستندات Word معقدة تحتوي على جداول وصور إلى Markdown؟**  
ج: نعم، يدعم Aspose.Words for Java تحويل مستندات Word المعقدة التي تحتوي على جداول وصور وعناصر تنسيق متعددة إلى Markdown. يمكنك تخصيص مخرجات Markdown وفقًا لتعقيد المستند.

**س: كيف يمكنني معالجة الصور في ملفات Markdown؟**  
ج: عيّن مسار مجلد الصور باستخدام طريقة `setImagesFolder` في `MarkdownSaveOptions`. تأكد من تخزين ملفات الصور في المجلد المحدد؛ سيقوم Aspose.Words بإنشاء روابط صور Markdown المناسبة.

**س: هل تتوفر نسخة تجريبية من Aspose.Words for Java؟**  
ج: نعم، يمكنك الحصول على نسخة تجريبية من Aspose.Words for Java من موقع Aspose. تتيح لك النسخة التجريبية تقييم قدرات المكتبة قبل شراء الترخيص.

**س: أين يمكنني العثور على مزيد من الأمثلة والوثائق؟**  
ج: لمزيد من الأمثلة والوثائق والمعلومات التفصيلية حول Aspose.Words for Java، يرجى زيارة [الوثائق](https://reference.aspose.com/words/java/).

---

**آخر تحديث:** 2025-12-22  
**تم الاختبار باستخدام:** Aspose.Words for Java 24.12 (أحدث نسخة وقت الكتابة)  
**المؤلف:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}