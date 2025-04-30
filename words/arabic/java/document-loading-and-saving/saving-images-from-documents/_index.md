---
"description": "تعرّف على كيفية حفظ الصور من المستندات باستخدام Aspose.Words لجافا من خلال دليلنا الشامل خطوة بخطوة. خصّص التنسيقات، وضغط الملفات، والمزيد."
"linktitle": "حفظ الصور من المستندات"
"second_title": "واجهة برمجة تطبيقات معالجة مستندات Java Aspose.Words"
"title": "حفظ الصور من المستندات في Aspose.Words لـ Java"
"url": "/ar/java/document-loading-and-saving/saving-images-from-documents/"
"weight": 17
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# حفظ الصور من المستندات في Aspose.Words لـ Java


## مقدمة لحفظ الصور من المستندات في Aspose.Words لـ Java

في هذا البرنامج التعليمي، سنستكشف كيفية حفظ الصور من المستندات باستخدام Aspose.Words لجافا. سنغطي سيناريوهات وخيارات تخصيص متنوعة لحفظ الصور. يقدم هذا الدليل تعليمات خطوة بخطوة مع أمثلة من الكود المصدري.

## المتطلبات الأساسية

قبل البدء، تأكد من دمج مكتبة Aspose.Words لجافا في مشروعك. يمكنك تنزيلها من [هنا](https://releases.aspose.com/words/java/).

## الخطوة 1: حفظ الصور بتنسيق TIFF باستخدام التحكم في العتبة

لحفظ الصور بتنسيق TIFF مع التحكم في العتبة، اتبع الخطوات التالية:

```java
Document doc = new Document("Your Directory Path" + "Rendering.docx");
ImageSaveOptions saveOptions = new ImageSaveOptions();
saveOptions.setTiffCompression(TiffCompression.CCITT_3);
saveOptions.setImageColorMode(ImageColorMode.GRAYSCALE);
saveOptions.setTiffBinarizationMethod(ImageBinarizationMethod.FLOYD_STEINBERG_DITHERING);
saveOptions.setThresholdForFloydSteinbergDithering((byte) 254);
doc.save("Your Directory Path" + "ThresholdControlledImage.tiff", saveOptions);
```

## الخطوة 2: حفظ صفحة محددة كملف TIFF متعدد الصفحات

لحفظ صفحة معينة كملف TIFF متعدد الصفحات، استخدم الكود التالي:

```java
Document doc = new Document("Your Directory Path" + "Rendering.docx");
ImageSaveOptions saveOptions = new ImageSaveOptions();
saveOptions.setPageSet(new PageSet(new PageRange(0, 1)));
saveOptions.setTiffCompression(TiffCompression.CCITT_4);
saveOptions.setResolution(160f);
doc.save("Your Directory Path" + "SpecificPageMultipage.tiff", saveOptions);
```

## الخطوة 3: حفظ الصور بتنسيق PNG مُفهرس بتنسيق 1 BPP

لحفظ الصور بتنسيق PNG المفهرس بتنسيق 1 BPP، اتبع الخطوات التالية:

```java
Document doc = new Document("Your Directory Path" + "Rendering.docx");
ImageSaveOptions saveOptions = new ImageSaveOptions();
saveOptions.setPageSet(new PageSet(1));
saveOptions.setImageColorMode(ImageColorMode.BLACK_AND_WHITE);
saveOptions.setPixelFormat(ImagePixelFormat.FORMAT_1_BPP_INDEXED);
doc.save("Your Directory Path" + "1BPPIndexed.png", saveOptions);
```

## الخطوة 4: حفظ الصفحة بتنسيق JPEG مع التخصيص

لحفظ صفحة معينة بصيغة JPEG مع خيارات التخصيص، استخدم هذا الكود:

```java
Document doc = new Document("Your Directory Path" + "Rendering.docx");
ImageSaveOptions options = new ImageSaveOptions();
options.setPageSet(new PageSet(0));
options.setImageBrightness(0.3f);
options.setImageContrast(0.7f);
options.setHorizontalResolution(72f);
doc.save("Your Directory Path" + "CustomizedJPEG.jpeg", options);
```

## الخطوة 5: استخدام استدعاء حفظ الصفحة

يمكنك استخدام معاودة الاتصال لتخصيص حفظ الصفحة. إليك مثال:

```java
Document doc = new Document("Your Directory Path" + "Rendering.docx");
ImageSaveOptions imageSaveOptions = new ImageSaveOptions();
imageSaveOptions.setPageSet(new PageSet(new PageRange(0, doc.getPageCount() - 1)));
imageSaveOptions.setPageSavingCallback(new HandlePageSavingCallback());
doc.save("Your Directory Path" + "PageSavingCallback.png", imageSaveOptions);
```

```java
private static class HandlePageSavingCallback implements IPageSavingCallback {
    public void pageSaving(PageSavingArgs args) {
        args.setPageFileName(MessageFormat.format("Your Directory Path" + "Page_{0}.png", args.getPageIndex()));
    }
}
```

## الكود المصدري الكامل لحفظ الصور من المستندات في Aspose.Words لـ Java

```java
public void exposeThresholdControlForTiffBinarization() throws Exception
{
	Document doc = new Document("Your Directory Path" + "Rendering.docx");
	ImageSaveOptions saveOptions = new ImageSaveOptions();
	{
		saveOptions.setTiffCompression(TiffCompression.CCITT_3);
		saveOptions.setImageColorMode(ImageColorMode.GRAYSCALE);
		saveOptions.setTiffBinarizationMethod(ImageBinarizationMethod.FLOYD_STEINBERG_DITHERING);
		saveOptions.setThresholdForFloydSteinbergDithering((byte) 254);
	}
	doc.save("Your Directory Path" + "WorkingWithImageSaveOptions.ExposeThresholdControlForTiffBinarization.tiff", saveOptions);
}
@Test
public void getTiffPageRange() throws Exception
{
	Document doc = new Document("Your Directory Path" + "Rendering.docx");
	doc.save("Your Directory Path" + "WorkingWithImageSaveOptions.MultipageTiff.tiff");
	ImageSaveOptions saveOptions = new ImageSaveOptions();
	{
		saveOptions.setPageSet(new PageSet(new PageRange(0, 1))); saveOptions.setTiffCompression(TiffCompression.CCITT_4); saveOptions.setResolution(160f);
	}
	doc.save("Your Directory Path" + "WorkingWithImageSaveOptions.GetTiffPageRange.tiff", saveOptions);
}
@Test
public void format1BppIndexed() throws Exception
{
	Document doc = new Document("Your Directory Path" + "Rendering.docx");
	ImageSaveOptions saveOptions = new ImageSaveOptions();
	{
		saveOptions.setPageSet(new PageSet(1));
		saveOptions.setImageColorMode(ImageColorMode.BLACK_AND_WHITE);
		saveOptions.setPixelFormat(ImagePixelFormat.FORMAT_1_BPP_INDEXED);
	}
	doc.save("Your Directory Path" + "WorkingWithImageSaveOptions.Format1BppIndexed.Png", saveOptions);
}
@Test
public void getJpegPageRange() throws Exception
{
	Document doc = new Document("Your Directory Path" + "Rendering.docx");
	ImageSaveOptions options = new ImageSaveOptions();
	// قم بضبط "PageSet" على "0" لتحويل الصفحة الأولى فقط من المستند.
	options.setPageSet(new PageSet(0));
	// تغيير سطوع الصورة وتباينها.
	// كلاهما على مقياس من 0 إلى 1 وهما 0.5 بشكل افتراضي.
	options.setImageBrightness(0.3f);
	options.setImageContrast(0.7f);
	// تغيير الدقة الأفقية.
	// القيمة الافتراضية لهذه الخصائص هي 96.0، لدقة 96 نقطة في البوصة.
	options.setHorizontalResolution(72f);
	doc.save("Your Directory Path" + "WorkingWithImageSaveOptions.GetJpegPageRange.jpeg", options);
}
@Test
public static void pageSavingCallback() throws Exception
{
	Document doc = new Document("Your Directory Path" + "Rendering.docx");
	ImageSaveOptions imageSaveOptions = new ImageSaveOptions();
	{
		imageSaveOptions.setPageSet(new PageSet(new PageRange(0, doc.getPageCount() - 1)));
		imageSaveOptions.setPageSavingCallback(new HandlePageSavingCallback());
	}
	doc.save("Your Directory Path" + "WorkingWithImageSaveOptions.PageSavingCallback.png", imageSaveOptions);
}
private static class HandlePageSavingCallback implements IPageSavingCallback
{
	public void pageSaving(PageSavingArgs args)
	{
		args.setPageFileName(MessageFormat.format("Your Directory Path" + "Page_{0}.png", args.getPageIndex()));
	}
```

## خاتمة

لقد تعلمتَ كيفية حفظ الصور من المستندات باستخدام Aspose.Words لجافا. توضح هذه الأمثلة خيارات التخصيص المتنوعة لحفظ الصور، بما في ذلك التنسيق والضغط واستخدام الاستدعاء العكسي. استكشف المزيد من الإمكانيات مع إمكانيات Aspose.Words القوية لجافا.

## الأسئلة الشائعة

### كيف يمكنني تغيير تنسيق الصورة عند الحفظ باستخدام Aspose.Words لـ Java؟

يمكنك تغيير تنسيق الصورة عن طريق تحديد التنسيق المطلوب في `ImageSaveOptions`على سبيل المثال، لحفظ الصورة بتنسيق PNG، استخدم `SaveFormat.PNG` كما هو موضح في الكود:

```java
ImageSaveOptions saveOptions = new ImageSaveOptions();
```

### هل يمكنني تخصيص إعدادات الضغط لصور TIFF؟

نعم، يمكنك تخصيص إعدادات ضغط صور TIFF. على سبيل المثال، لتعيين طريقة الضغط إلى CCITT_3، استخدم الكود التالي:

```java
saveOptions.setTiffCompression(TiffCompression.CCITT_3);
```

### كيف يمكنني حفظ صفحة محددة من مستند كصورة منفصلة؟

لحفظ صفحة معينة كصورة، استخدم `setPageSet` الطريقة في `ImageSaveOptions`على سبيل المثال، لحفظ الصفحة الأولى فقط، اضبط `PageSet` ل `new PageSet(0)`.

```java
saveOptions.setPageSet(new PageSet(0)); // حفظ الصفحة الأولى كصورة
```

### كيف يمكنني تطبيق الإعدادات المخصصة على صور JPEG عند الحفظ؟

يمكنك تطبيق الإعدادات المخصصة على صور JPEG باستخدام `ImageSaveOptions`اضبط خصائص مثل السطوع والتباين والدقة. على سبيل المثال، لتغيير السطوع إلى 0.3 والتباين إلى 0.7، استخدم هذا الكود:

```java
options.setImageBrightness(0.3f);
options.setImageContrast(0.7f);
```

### كيف يمكنني استخدام معاودة الاتصال لتخصيص حفظ الصورة؟

لاستخدام معاودة الاتصال لتخصيص حفظ الصورة، اضبط `PageSavفيgCallback` in `ImageSaveOptions`. قم بإنشاء فئة تنفذ `IPageSavingCallback` الواجهة وتجاوزها `pageSaving` طريقة.

```java
imageSaveOptions.setPageSavingCallback(new HandlePageSavingCallback());
```

ثم قم بإنشاء فئة تنفذ `IPageSavingCallback` واجهة وتخصيص اسم الملف وموقعه في `pageSaving` طريقة.

```java
private static class HandlePageSavingCallback implements IPageSavingCallback {
    public void pageSaving(PageSavingArgs args) {
        args.setPageFileName(MessageFormat.format("Your Directory Path" + "Page_{0}.png", args.getPageIndex()));
    }
}
```


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}