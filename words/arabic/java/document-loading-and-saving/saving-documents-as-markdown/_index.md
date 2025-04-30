---
"description": "تعرّف على كيفية تحويل مستندات Word إلى Markdown باستخدام Aspose.Words لجافا. يغطي هذا الدليل خطوة بخطوة محاذاة الجداول، ومعالجة الصور، والمزيد."
"linktitle": "حفظ المستندات بتنسيق Markdown"
"second_title": "واجهة برمجة تطبيقات معالجة مستندات Java Aspose.Words"
"title": "حفظ المستندات بتنسيق Markdown في Aspose.Words لـ Java"
"url": "/ar/java/document-loading-and-saving/saving-documents-as-markdown/"
"weight": 18
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# حفظ المستندات بتنسيق Markdown في Aspose.Words لـ Java


## مقدمة لحفظ المستندات بتنسيق Markdown في Aspose.Words لـ Java

في هذا الدليل التفصيلي، سنوضح كيفية حفظ المستندات بتنسيق Markdown باستخدام Aspose.Words لجافا. Markdown هي لغة ترميز خفيفة تُستخدم عادةً لتنسيق المستندات النصية. باستخدام Aspose.Words لجافا، يمكنك بسهولة تحويل مستندات Word إلى تنسيق Markdown. سنغطي جوانب مختلفة من حفظ ملفات Markdown، بما في ذلك محاذاة محتوى الجدول ومعالجة الصور.

## المتطلبات الأساسية

قبل أن تبدأ، تأكد من أن لديك المتطلبات الأساسية التالية:

- تم تثبيت Java Development Kit (JDK) على نظامك.
- مكتبة Aspose.Words لجافا. يمكنك تنزيلها من [هنا](https://releases.aspose.com/words/java/).

## الخطوة 1: إنشاء مستند Word

لنبدأ بإنشاء مستند وورد، ثم سنحوّله إلى تنسيق Markdown. يمكنك تخصيص هذا المستند حسب احتياجاتك.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// إدراج جدول يحتوي على خليتين
builder.insertCell();
builder.getParagraphFormat().setAlignment(ParagraphAlignment.RIGHT);
builder.write("Cell1");

builder.insertCell();
builder.getParagraphFormat().setAlignment(ParagraphAlignment.CENTER);
builder.write("Cell2");

// حفظ المستند بتنسيق Markdown
MarkdownSaveOptions saveOptions = new MarkdownSaveOptions();
doc.save("output.md", saveOptions);
```

في هذا المثال، ننشئ جدولًا بسيطًا من خليتين ونضبط محاذاة الفقرات داخلهما. ثم نحفظ المستند بتنسيق Markdown باستخدام `MarkdownSaveOptions`.

## الخطوة 2: تخصيص محاذاة محتوى الجدول

يتيح لك Aspose.Words لجافا تخصيص محاذاة محتوى الجدول عند الحفظ بتنسيق Markdown. يمكنك محاذاة محتوى الجدول إلى اليسار أو اليمين أو الوسط، أو تحديده تلقائيًا بناءً على الفقرة الأولى في كل عمود.

فيما يلي كيفية تخصيص محاذاة محتوى الجدول:

```java
// ضبط محاذاة محتوى الجدول إلى اليسار
saveOptions.setTableContentAlignment(TableContentAlignment.LEFT);
doc.save("left_alignment.md", saveOptions);

// ضبط محاذاة محتوى الجدول إلى اليمين
saveOptions.setTableContentAlignment(TableContentAlignment.RIGHT);
doc.save("right_alignment.md", saveOptions);

// ضبط محاذاة محتوى الجدول إلى المركز
saveOptions.setTableContentAlignment(TableContentAlignment.CENTER);
doc.save("center_alignment.md", saveOptions);

// تعيين محاذاة محتوى الجدول إلى تلقائي (يتم تحديدها حسب الفقرة الأولى)
saveOptions.setTableContentAlignment(TableContentAlignment.AUTO);
doc.save("auto_alignment.md", saveOptions);
```

عن طريق تغيير `TableContentAlignment` باستخدام الخاصية، يمكنك التحكم في كيفية محاذاة المحتوى داخل الجداول عند التحويل إلى Markdown.

## الخطوة 3: التعامل مع الصور

لتضمين الصور في مستند Markdown، عليك تحديد المجلد الذي توجد فيه الصور. يتيح لك Aspose.Words لـ Java تعيين مجلد الصور في `MarkdownSaveOptions`.

إليك كيفية تعيين مجلد الصور وحفظ المستند بالصور:

```java
// تحميل مستند يحتوي على صور
Document doc = new Document("document_with_images.docx");

// تعيين مسار مجلد الصور
MarkdownSaveOptions saveOptions = new MarkdownSaveOptions();
saveOptions.setImagesFolder("images_folder/");

// حفظ المستند مع الصور
doc.save("document_with_images.md", saveOptions);
```

تأكد من الاستبدال `"document_with_images.docx"` مع المسار إلى مستند Word الذي يحتوي على الصور و `"images_folder/"` مع المسار الفعلي للمجلد الذي يتم تخزين صورك فيه.

## كود المصدر الكامل لحفظ المستندات بتنسيق Markdown في Aspose.Words لـ Java

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
	// يجعل جميع الفقرات داخل الجدول محاذية.
	MarkdownSaveOptions saveOptions = new MarkdownSaveOptions();
	{
		saveOptions.setTableContentAlignment(TableContentAlignment.LEFT);
	}
	doc.save("Your Directory Path" + "WorkingWithMarkdownSaveOptions.LeftTableContentAlignment.md", saveOptions);
	saveOptions.setTableContentAlignment(TableContentAlignment.RIGHT);
	doc.save("Your Directory Path" + "WorkingWithMarkdownSaveOptions.RightTableContentAlignment.md", saveOptions);
	saveOptions.setTableContentAlignment(TableContentAlignment.CENTER);
	doc.save("Your Directory Path" + "WorkingWithMarkdownSaveOptions.CenterTableContentAlignment.md", saveOptions);
	// سيتم أخذ المحاذاة في هذه الحالة من الفقرة الأولى في عمود الجدول المقابل.
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

## خاتمة

في هذا الدليل، استكشفنا كيفية حفظ المستندات بتنسيق Markdown باستخدام Aspose.Words لجافا. غطينا إنشاء مستند Word، وتخصيص محاذاة محتوى الجدول، ومعالجة الصور في ملفات Markdown. يمكنك الآن تحويل مستندات Word بكفاءة إلى تنسيق Markdown، مما يجعلها مناسبة لمختلف منصات النشر واحتياجات التوثيق.

## الأسئلة الشائعة

### كيف أقوم بتثبيت Aspose.Words لـ Java؟

يمكن تثبيت Aspose.Words لجافا عن طريق تضمين المكتبة في مشروع جافا. يمكنك تنزيل المكتبة من [هنا](https://releases.aspose.com/words/java/) واتبع تعليمات التثبيت الواردة في الوثائق.

### هل يمكنني تحويل مستندات Word المعقدة التي تحتوي على الجداول والصور إلى Markdown؟

نعم، يدعم Aspose.Words لجافا تحويل مستندات Word المعقدة، التي تحتوي على جداول وصور وعناصر تنسيق متنوعة، إلى تنسيق Markdown. يمكنك تخصيص مُخرجات Markdown حسب تعقيد مستندك.

### كيف يمكنني التعامل مع الصور في ملفات Markdown؟

لتضمين الصور في ملفات Markdown، اضبط مسار مجلد الصور باستخدام `setImagesFolder` الطريقة في `MarkdownSaveOptions`تأكد من تخزين ملفات الصور في المجلد المحدد، وسوف يقوم Aspose.Words for Java بمعالجة مراجع الصور وفقًا لذلك.

### هل هناك نسخة تجريبية من Aspose.Words لـ Java متاحة؟

نعم، يمكنك الحصول على نسخة تجريبية من Aspose.Words لجافا من موقع Aspose الإلكتروني. تتيح لك هذه النسخة التجريبية تقييم إمكانيات المكتبة قبل شراء الترخيص.

### أين يمكنني العثور على المزيد من الأمثلة والوثائق؟

لمزيد من الأمثلة والوثائق والمعلومات التفصيلية حول Aspose.Words for Java، يرجى زيارة [التوثيق](https://reference.aspose.com/words/java/).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}