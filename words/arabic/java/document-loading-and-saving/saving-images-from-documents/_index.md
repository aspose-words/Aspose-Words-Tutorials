---
title: حفظ الصور من المستندات في Aspose.Words لـ Java
linktitle: حفظ الصور من المستندات
second_title: واجهة برمجة تطبيقات معالجة المستندات في Java Aspose.Words
description: تعرف على كيفية حفظ الصور من المستندات باستخدام Aspose.Words for Java من خلال دليلنا الشامل خطوة بخطوة. يمكنك تخصيص التنسيقات والضغط والمزيد.
weight: 17
url: /ar/java/document-loading-and-saving/saving-images-from-documents/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# حفظ الصور من المستندات في Aspose.Words لـ Java


## مقدمة لحفظ الصور من المستندات في Aspose.Words لـ Java

في هذا البرنامج التعليمي، سنستكشف كيفية حفظ الصور من المستندات باستخدام Aspose.Words for Java. وسنغطي سيناريوهات مختلفة وخيارات التخصيص لحفظ الصور. يوفر هذا الدليل تعليمات خطوة بخطوة مع أمثلة لأكواد المصدر.

## المتطلبات الأساسية

 قبل أن تبدأ، تأكد من دمج مكتبة Aspose.Words for Java في مشروعك. يمكنك تنزيلها من[هنا](https://releases.aspose.com/words/java/).

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

## الخطوة 2: حفظ صفحة محددة بتنسيق TIFF متعدد الصفحات

لحفظ صفحة معينة بصيغة TIFF متعددة الصفحات، استخدم الكود التالي:

```java
Document doc = new Document("Your Directory Path" + "Rendering.docx");
ImageSaveOptions saveOptions = new ImageSaveOptions();
saveOptions.setPageSet(new PageSet(new PageRange(0, 1)));
saveOptions.setTiffCompression(TiffCompression.CCITT_4);
saveOptions.setResolution(160f);
doc.save("Your Directory Path" + "SpecificPageMultipage.tiff", saveOptions);
```

## الخطوة 3: حفظ الصور بتنسيق PNG مُفهرس بتنسيق 1 BPP

لحفظ الصور بتنسيق PNG مُفهرس بتنسيق 1 BPP، اتبع الخطوات التالية:

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
	// اضبط "PageSet" على "0" لتحويل الصفحة الأولى فقط من المستند.
	options.setPageSet(new PageSet(0));
	// تغيير سطوع الصورة وتباينها.
	// كلاهما على مقياس من 0 إلى 1 ويكونان عند 0.5 بشكل افتراضي.
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

لقد تعلمت كيفية حفظ الصور من المستندات باستخدام Aspose.Words for Java. توضح هذه الأمثلة خيارات التخصيص المتنوعة لحفظ الصور، بما في ذلك التنسيق والضغط واستخدام الاستدعاء. استكشف المزيد من الإمكانيات مع القدرات القوية لـ Aspose.Words for Java.

## الأسئلة الشائعة

### كيف يمكنني تغيير تنسيق الصورة عند الحفظ باستخدام Aspose.Words لـ Java؟

 يمكنك تغيير تنسيق الصورة عن طريق تحديد التنسيق المطلوب في`ImageSaveOptions` على سبيل المثال، لحفظ الملف بتنسيق PNG، استخدم`SaveFormat.PNG` كما هو موضح في الكود:

```java
ImageSaveOptions saveOptions = new ImageSaveOptions();
```

### هل يمكنني تخصيص إعدادات الضغط لصور TIFF؟

نعم، يمكنك تخصيص إعدادات ضغط صور TIFF. على سبيل المثال، لتعيين طريقة الضغط إلى CCITT_3، استخدم الكود التالي:

```java
saveOptions.setTiffCompression(TiffCompression.CCITT_3);
```

### كيف يمكنني حفظ صفحة محددة من مستند كصورة منفصلة؟

 لحفظ صفحة معينة كصورة، استخدم`setPageSet`الطريقة في`ImageSaveOptions` على سبيل المثال، لحفظ الصفحة الأولى فقط، اضبط`PageSet` ل`new PageSet(0)`.

```java
saveOptions.setPageSet(new PageSet(0)); // حفظ الصفحة الأولى كصورة
```

### كيف يمكنني تطبيق الإعدادات المخصصة على صور JPEG عند الحفظ؟

يمكنك تطبيق إعدادات مخصصة على صور JPEG باستخدام`ImageSaveOptions`. اضبط خصائص مثل السطوع والتباين والدقة. على سبيل المثال، لتغيير السطوع إلى 0.3 والتباين إلى 0.7، استخدم هذا الكود:

```java
options.setImageBrightness(0.3f);
options.setImageContrast(0.7f);
```

### كيف يمكنني استخدام معاودة الاتصال لتخصيص حفظ الصورة؟

 لاستخدام معاودة الاتصال لتخصيص حفظ الصورة، اضبط`PageSavingCallback` في`ImageSaveOptions` . إنشاء فئة تنفذ`IPageSavingCallback` الواجهة وتجاوزها`pageSaving` طريقة.

```java
imageSaveOptions.setPageSavingCallback(new HandlePageSavingCallback());
```

 ثم قم بإنشاء فئة تنفذ`IPageSavingCallback` واجهة وتخصيص اسم الملف وموقعه في`pageSaving` طريقة.

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
