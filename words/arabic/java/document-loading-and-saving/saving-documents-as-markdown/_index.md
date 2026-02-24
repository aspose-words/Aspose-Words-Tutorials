---
date: 2026-02-24
description: تعلم كيفية تحويل ملفات Word إلى Markdown باستخدام Aspose.Words للغة Java.
  يغطي هذا الدليل محاذاة الجداول، ومعالجة الصور، وكيفية حفظ المستند كملف Markdown.
linktitle: Saving Documents as Markdown
second_title: Aspose.Words Java Document Processing API
title: تحويل Word إلى Markdown باستخدام Aspose.Words للـ Java
url: /ar/java/document-loading-and-saving/saving-documents-as-markdown/
weight: 18
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# تحويل Word إلى Markdown باستخدام Aspose.Words for Java

## مقدمة حول تحويل Word إلى Markdown باستخدام Aspose.Words for Java

في هذا الدليل خطوة بخطوة ستتعلم **كيفية تحويل Word إلى Markdown** باستخدام واجهة برمجة التطبيقات القوية Aspose.Words for Java. Markdown هي لغة توصيف خفيفة الوزن يعتمد عليها العديد من المطورين ومنصات المحتوى لإنشاء وثائق نظيفة وقابلة للقراءة. بحلول نهاية هذا الدليل ستتمكن من أخذ أي ملف `.docx`، مع الحفاظ على الجداول، الصور، والتنسيق، وتصديره كملف `.md` جاهز لمولدات المواقع الثابتة، ملفات README على GitHub، أو أي سير عمل يدعم Markdown.

## إجابات سريعة
- **ما المكتبة التي أحتاجها؟** Aspose.Words for Java (`aspose-words.jar`).
- **هل يمكنني تخصيص محاذاة الجداول؟** نعم – استخدم `TableContentAlignment` في `MarkdownSaveOptions`.
- **كيف يتم التعامل مع الصور؟** حدد مجلد الصور باستخدام `setImagesFolder()`؛ المكتبة تنشئ روابط نسبية.
- **هل أحتاج إلى ترخيص للإنتاج؟** الترخيص التجاري مطلوب للاستخدام غير التجريبي.
- **هل هذا متوافق مع Java 17؟** نعم، المكتبة تدعم Java 8 فوق.

## ما هو تحويل Word إلى Markdown؟

تحويل Word إلى Markdown يعني أخذ التنسيق الغني لمستند Microsoft Word وتحويله إلى صيغة نصية بسيطة باستخدام بناء جملة Markdown. تحتفظ هذه العملية بالعناوين، القوائم، الجداول، وإشارات الصور مع إزالة التنسيق الثنائي، مما يجعل المحتوى قابلًا للنقل وصديقًا لأنظمة التحكم في الإصدارات.

## لماذا نستخدم Aspose.Words for Java لحفظ المستند كـ markdown؟

* **دقة كاملة** – الجداول، الصور، والتصاميم المعقدة تُحفظ كما هي.
* **تحكم دقيق** – يمكنك تخصيص محاذاة الجداول، مسارات الصور، وأكثر.
* **بدون تبعيات خارجية** – المكتبة تعمل مباشرة دون الحاجة إلى تثبيت Office.
* **متعددة المنصات** – تعمل على Windows، Linux، و macOS مع أي بيئة تشغيل Java.

## المتطلبات المسبقة

قبل البدء، تأكد من وجود ما يلي:

- مجموعة تطوير جافا (JDK) مثبتة على نظامك.
- مكتبة Aspose.Words for Java. يمكنك تنزيلها من [هنا](https://releases.aspose.com/words/java/).

## دليل خطوة بخطوة

### الخطوة 1: إنشاء مستند Word سيتم تحويله

أولاً، نقوم بإنشاء مستند Word بسيط يحتوي على جدول بخليةين. يوضح هذا المثال كيف يتم احترام محاذاة الفقرات داخل خلايا الجدول عندما نقوم لاحقًا **بحفظ المستند كـ markdown**.

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

### الخطوة 2: تخصيص محاذاة محتوى الجدول

تتيح لك Aspose.Words for Java التحكم في كيفية محاذاة خلايا الجدول في الـ markdown المُولد. استخدم الخاصية `TableContentAlignment` لتحديد **تخصيص محاذاة الجدول** إلى اليسار، اليمين، الوسط، أو ترك المكتبة تقرر تلقائيًا بناءً على الفقرة الأولى في كل عمود.

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

من خلال تبديل هذا الإعداد يمكنك **تصدير جداول Word إلى markdown** بالمحاذاة الدقيقة التي تحتاجها لمحركات العرض اللاحقة.

### الخطوة 3: معالجة الصور أثناء التحويل

عندما يحتوي مستند Word المصدر على صور، يجب إخبار Aspose.Words بمكان وضع ملفات الصور المصدرة. طريقة `setImagesFolder` في `MarkdownSaveOptions` تحدد المجلد الذي سيحمل موارد الصور، وسيحتوي الـ markdown على روابط نسبية لتلك الملفات.

```java
// Load a document containing images
Document doc = new Document("document_with_images.docx");

// Set the images folder path
MarkdownSaveOptions saveOptions = new MarkdownSaveOptions();
saveOptions.setImagesFolder("images_folder/");

// Save the document with images
doc.save("document_with_images.md", saveOptions);
```

استبدل `"document_with_images.docx"` بمسار ملف المصدر الخاص بك و`"images_folder/"` بالمجلد المطلوب إخراج الصور إليه.

### الكود الكامل لجميع السيناريوهات

فيما يلي مثال موحد يوضح كيفية **محاذاة الجداول تلقائيًا**، **تخصيص المحاذاة**، و**تحديد مجلد الصور** في طريقة واحدة. هذا المقتطف يعكس الكود الأصلي في الدرس ويعمل دون تعديل.

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

| المشكلة | السبب | الحل |
|-------|--------|-----|
| الصور تظهر كروابط مكسورة | `setImagesFolder` غير محدد أو مسار المجلد غير صحيح | تحقق من صحة مسار المجلد وتأكد من أن المجلد قابل للكتابة |
| محاذاة الجدول غير صحيحة | قيمة `TableContentAlignment` خاطئة | استخدم `TableContentAlignment.AUTO` لترك الفقرة الأولى تقرر، أو اضبطها صراحةً إلى LEFT/RIGHT/CENTER |
| ملف الإخراج فارغ | خيارات الحفظ لم تُمرر إلى `doc.save()` | تأكد من تمرير كائن `MarkdownSaveOptions` إلى طريقة `save` |
| ميزات Word غير مدعومة (مثل SmartArt) | لا يمكن للـ markdown تمثيل بعض الكائنات المعقدة | حوّل تلك العناصر إلى صور قبل الحفظ، أو بسط المستند المصدر |

## الأسئلة المتكررة

**س: كيف أقوم بتثبيت Aspose.Words for Java؟**  
ج: يمكن تثبيت Aspose.Words for Java عن طريق إضافة المكتبة إلى مشروع Java الخاص بك. يمكنك تنزيل المكتبة من [هنا](https://releases.aspose.com/words/java/) واتباع تعليمات التثبيت الواردة في الوثائق.

**س: هل يمكنني تحويل مستندات Word معقدة تحتوي على جداول وصور إلى Markdown؟**  
ج: نعم، تدعم Aspose.Words for Java تحويل مستندات Word المعقدة التي تحتوي على جداول، صور، وعناصر تنسيق متعددة إلى Markdown. يمكنك تخصيص ناتج الـ Markdown وفقًا لتعقيد المستند.

**س: كيف يمكنني معالجة الصور في ملفات Markdown؟**  
ج: لتضمين الصور في ملفات Markdown، حدد مسار مجلد الصور باستخدام طريقة `setImagesFolder` في `MarkdownSaveOptions`. تأكد من أن ملفات الصور مخزنة في المجلد المحدد، وستتعامل Aspose.Words for Java مع إشارات الصور تلقائيًا.

**س: هل هناك نسخة تجريبية من Aspose.Words for Java متاحة؟**  
ج: نعم، يمكنك الحصول على نسخة تجريبية من Aspose.Words for Java من موقع Aspose. تسمح النسخة التجريبية بتقييم قدرات المكتبة قبل شراء الترخيص.

**س: أين يمكنني العثور على المزيد من الأمثلة والوثائق؟**  
ج: للمزيد من الأمثلة والوثائق والمعلومات التفصيلية حول Aspose.Words for Java، يرجى زيارة [الوثائق](https://reference.aspose.com/words/java/).

## الخلاصة

في هذا الدليل غطينا كل ما تحتاجه **لتحويل Word إلى Markdown** باستخدام Aspose.Words for Java: إنشاء مستند المصدر، **تخصيص محاذاة الجداول**، ومعالجة الصور عبر تكوين المجلد المناسب. باستخدام هذه التقنيات يمكنك تصدير محتوى Word إلى Markdown بثقة للمدونات، مواقع الوثائق، أو أي منصة تتعامل مع Markdown.

---

**آخر تحديث:** 2026-02-24  
**تم الاختبار مع:** Aspose.Words for Java 24.12 (أحدث نسخة وقت الكتابة)  
**المؤلف:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}