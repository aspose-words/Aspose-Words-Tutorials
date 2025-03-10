---
title: حفظ المستندات بتنسيق Markdown في Aspose.Words لـ Java
linktitle: حفظ المستندات بتنسيق Markdown
second_title: واجهة برمجة تطبيقات معالجة المستندات في Java Aspose.Words
description: تعرف على كيفية تحويل مستندات Word إلى Markdown باستخدام Aspose.Words for Java. يغطي هذا الدليل خطوة بخطوة محاذاة الجدول ومعالجة الصور والمزيد.
weight: 18
url: /ar/java/document-loading-and-saving/saving-documents-as-markdown/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# حفظ المستندات بتنسيق Markdown في Aspose.Words لـ Java


## مقدمة لحفظ المستندات بتنسيق Markdown في Aspose.Words للغة Java

في هذا الدليل التفصيلي، سنوضح لك كيفية حفظ المستندات بتنسيق Markdown باستخدام Aspose.Words for Java. Markdown هي لغة ترميز خفيفة الوزن تُستخدم عادةً لتنسيق المستندات النصية. باستخدام Aspose.Words for Java، يمكنك بسهولة تحويل مستندات Word إلى تنسيق Markdown. سنغطي جوانب مختلفة لحفظ ملفات Markdown، بما في ذلك محاذاة محتوى الجدول والتعامل مع الصور.

## المتطلبات الأساسية

قبل أن تبدأ، تأكد من أن لديك المتطلبات الأساسية التالية:

- تم تثبيت Java Development Kit (JDK) على نظامك.
-  مكتبة Aspose.Words للغة Java. يمكنك تنزيلها من[هنا](https://releases.aspose.com/words/java/).

## الخطوة 1: إنشاء مستند Word

لنبدأ بإنشاء مستند Word الذي سنقوم بتحويله لاحقًا إلى تنسيق Markdown. يمكنك تخصيص هذا المستند وفقًا لمتطلباتك.

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

 في هذا المثال، نقوم بإنشاء جدول بسيط يحتوي على خليتين ونحدد محاذاة الفقرات داخل هذه الخلايا. ثم نحفظ المستند بتنسيق Markdown باستخدام`MarkdownSaveOptions`.

## الخطوة 2: تخصيص محاذاة محتوى الجدول

يتيح لك Aspose.Words for Java تخصيص محاذاة محتوى الجدول عند الحفظ بتنسيق Markdown. يمكنك محاذاة محتوى الجدول إلى اليسار أو اليمين أو المنتصف أو تحديده تلقائيًا استنادًا إلى الفقرة الأولى في كل عمود في الجدول.

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

//ضبط محاذاة محتوى الجدول إلى تلقائي (يتم تحديده من خلال الفقرة الأولى)
saveOptions.setTableContentAlignment(TableContentAlignment.AUTO);
doc.save("auto_alignment.md", saveOptions);
```

 عن طريق تغيير`TableContentAlignment` باستخدام الخاصية، يمكنك التحكم في كيفية محاذاة المحتوى داخل الجداول عند التحويل إلى Markdown.

## الخطوة 3: التعامل مع الصور

 لتضمين الصور في مستند Markdown الخاص بك، تحتاج إلى تحديد المجلد الذي توجد به الصور. يتيح لك Aspose.Words for Java تعيين مجلد الصور في`MarkdownSaveOptions`.

إليك كيفية تعيين مجلد الصور وحفظ المستند بالصور:

```java
// تحميل مستند يحتوي على صور
Document doc = new Document("document_with_images.docx");

// تعيين مسار مجلد الصور
MarkdownSaveOptions saveOptions = new MarkdownSaveOptions();
saveOptions.setImagesFolder("images_folder/");

// حفظ المستند بالصور
doc.save("document_with_images.md", saveOptions);
```

 تأكد من الاستبدال`"document_with_images.docx"` مع المسار إلى مستند Word الخاص بك الذي يحتوي على الصور و`"images_folder/"` مع المسار الفعلي للمجلد الذي يتم تخزين صورك فيه.

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

في هذا الدليل، استكشفنا كيفية حفظ المستندات بتنسيق Markdown باستخدام Aspose.Words for Java. لقد تناولنا إنشاء مستند Word وتخصيص محاذاة محتوى الجدول ومعالجة الصور في ملفات Markdown. يمكنك الآن تحويل مستندات Word بكفاءة إلى تنسيق Markdown، مما يجعلها مناسبة لمنصات النشر المختلفة واحتياجات التوثيق.

## الأسئلة الشائعة

### كيف أقوم بتثبيت Aspose.Words لـ Java؟

 يمكن تثبيت Aspose.Words for Java عن طريق تضمين المكتبة في مشروع Java الخاص بك. يمكنك تنزيل المكتبة من[هنا](https://releases.aspose.com/words/java/) واتبع تعليمات التثبيت الواردة في الوثائق.

### هل يمكنني تحويل مستندات Word المعقدة التي تحتوي على الجداول والصور إلى Markdown؟

نعم، يدعم Aspose.Words for Java تحويل مستندات Word المعقدة التي تحتوي على جداول وصور وعناصر تنسيق مختلفة إلى Markdown. يمكنك تخصيص إخراج Markdown وفقًا لتعقيد مستندك.

### كيف يمكنني التعامل مع الصور في ملفات Markdown؟

 لتضمين الصور في ملفات Markdown، اضبط مسار مجلد الصور باستخدام`setImagesFolder`الطريقة في`MarkdownSaveOptions`تأكد من تخزين ملفات الصور في المجلد المحدد، وسيقوم Aspose.Words for Java بمعالجة مراجع الصور وفقًا لذلك.

### هل هناك نسخة تجريبية من Aspose.Words متاحة لـ Java؟

نعم، يمكنك الحصول على نسخة تجريبية من Aspose.Words for Java من موقع Aspose على الويب. تتيح لك النسخة التجريبية تقييم قدرات المكتبة قبل شراء الترخيص.

### أين يمكنني العثور على المزيد من الأمثلة والوثائق؟

 لمزيد من الأمثلة والوثائق والمعلومات التفصيلية حول Aspose.Words for Java، يرجى زيارة[التوثيق](https://reference.aspose.com/words/java/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
