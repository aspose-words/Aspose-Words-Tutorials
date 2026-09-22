---
date: 2025-12-27
description: تعلم كيفية حفظ الصفحة كملف JPEG واستخراج الصور من مستندات Word باستخدام
  Aspose.Words للغة Java. يتضمن نصائح لضبط سطوع الصورة، الدقة، وإنشاء ملفات TIFF متعددة
  الصفحات.
linktitle: Saving Images from Documents
second_title: Aspose.Words Java Document Processing API
title: كيفية حفظ الصفحة كـ JPEG واستخراج الصور من المستندات باستخدام Aspose.Words
  للـ Java
url: /ar/java/document-loading-and-saving/saving-images-from-documents/
weight: 17
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# حفظ الصفحة كـ JPEG واستخراج الصور من المستندات في Aspose.Words for Java

في هذا البرنامج التعليمي ستكتشف كيفية **حفظ الصفحة كـ jpeg** من مستند Word وكيفية **استخراج الصور من ملفات Word** باستخدام Aspose.Words for Java. سنستعرض سيناريوهات واقعية مثل ضبط سطوع الصورة، تعديل دقة الصورة في Java، وإنشاء ملف TIFF متعدد الصفحات. كل خطوة تتضمن مقتطفات شفرة جاهزة للتنفيذ لتتمكن من النسخ واللصق ورؤية النتائج فورًا.

## إجابات سريعة
- **هل يمكنني حفظ صفحة واحدة كـ JPEG؟** نعم – استخدم `ImageSaveOptions` مع `setPageSet(new PageSet(pageIndex))`.
- **كيف أغيّر سطوع الصورة؟** استدعِ `options.setImageBrightness(floatValue)` (نطاق 0‑1).
- **ماذا لو أردت TIFF متعدد الصفحات؟** عيّن `PageSet` يغطي الصفحات المطلوبة واختر طريقة ضغط TIFF.
- **كيف يمكنني التحكم في دقة الصورة؟** استخدم `setResolution(floatDpi)` أو `setHorizontalResolution(floatDpi)`.
- **هل أحتاج إلى ترخيص للاستخدام في الإنتاج؟** يلزم وجود ترخيص صالح لـ Aspose.Words للاستخدام غير التجريبي.

## ما هو “حفظ الصفحة كـ jpeg”؟
حفظ الصفحة كـ JPEG يعني تحويل صفحة واحدة من مستند Word إلى ملف صورة نقطية (JPEG). هذا مفيد لإنشاء معاينات، صور مصغرة، أو تضمين صفحات المستند في صفحات الويب عندما لا يكون عرض PDF عمليًا.

## لماذا استخراج الصور من مستندات Word؟
العديد من سير عمل الأعمال تتطلب استخراج الرسومات الأصلية (الشعارات، المخططات، الصور) من ملف DOCX لإعادة استخدامها، أرشفتها، أو تحليلها. تجعل Aspose.Words عملية استخراج كل صورة بصيغتها الأصلية دون فقدان الجودة سهلة وسريعة.

## المتطلبات المسبقة
- مجموعة تطوير جافا (JDK 8 أو أحدث) مثبتة.
- مكتبة Aspose.Words for Java مضافة إلى مشروعك. حمّلها من [هنا](https://releases.aspose.com/words/java/).
- مستند Word تجريبي (مثلاً `Rendering.docx`) موجود في دليل معروف.

## الخطوة 1: حفظ الصور كـ TIFF مع التحكم في العتبة (إنشاء TIFF متعدد الصفحات)
لإنشاء TIFF عالي التباين وتدرج رمادي يمكنك التحكم في عتبة التثليث. هذا مفيد عندما تحتاج نسخة مطبوعة بالأبيض والأسود من مستندك.

```java
Document doc = new Document("Your Directory Path" + "Rendering.docx");
ImageSaveOptions saveOptions = new ImageSaveOptions();
saveOptions.setTiffCompression(TiffCompression.CCITT_3);
saveOptions.setImageColorMode(ImageColorMode.GRAYSCALE);
saveOptions.setTiffBinarizationMethod(ImageBinarizationMethod.FLOYD_STEINBERG_DITHERING);
saveOptions.setThresholdForFloydSteinbergDithering((byte) 254);
doc.save("Your Directory Path" + "ThresholdControlledImage.tiff", saveOptions);
```

## الخطوة 2: حفظ صفحة محددة كـ TIFF متعدد الصفحات
إذا كنت تحتاج TIFF يحتوي فقط على مجموعة فرعية من الصفحات (مثلاً الصفحات 1‑2)، قم بتكوين `PageSet`. هذا يوضح **إنشاء TIFF متعدد الصفحات**.

```java
Document doc = new Document("Your Directory Path" + "Rendering.docx");
ImageSaveOptions saveOptions = new ImageSaveOptions();
saveOptions.setPageSet(new PageSet(new PageRange(0, 1)));
saveOptions.setTiffCompression(TiffCompression.CCITT_4);
saveOptions.setResolution(160f);
doc.save("Your Directory Path" + "SpecificPageMultipage.tiff", saveOptions);
```

## الخطوة 3: حفظ الصور كـ PNG مفهرس بدقة 1 BPP
عند الحاجة إلى PNG أبيض وأسود خفيف الوزن (بت واحد لكل بكسل)، اضبط تنسيق البكسل وفقًا لذلك. هذا مفيد لتضمين رسومات بسيطة في بيئات ذات عرض نطاق منخفض.

```java
Document doc = new Document("Your Directory Path" + "Rendering.docx");
ImageSaveOptions saveOptions = new ImageSaveOptions();
saveOptions.setPageSet(new PageSet(1));
saveOptions.setImageColorMode(ImageColorMode.BLACK_AND_WHITE);
saveOptions.setPixelFormat(ImagePixelFormat.FORMAT_1_BPP_INDEXED);
doc.save("Your Directory Path" + "1BPPIndexed.png", saveOptions);
```

## الخطوة 4: حفظ صفحة كـ JPEG مع تخصيص (ضبط سطوع الصورة والدقة)
هنا نقوم **بحفظ الصفحة كـ jpeg** مع تعديل السطوع، التباين، والدقة — مثالي لإنشاء صور مصغرة أو معاينات جاهزة للويب.

```java
Document doc = new Document("Your Directory Path" + "Rendering.docx");
ImageSaveOptions options = new ImageSaveOptions();
options.setPageSet(new PageSet(0));
options.setImageBrightness(0.3f);          // set image brightness (0‑1)
options.setImageContrast(0.7f);            // set image contrast (0‑1)
options.setHorizontalResolution(72f);      // set image resolution in DPI
doc.save("Your Directory Path" + "CustomizedJPEG.jpeg", options);
```

## الخطوة 5: استخدام رد نداء حفظ الصفحة (تخصيص متقدم)
يتيح رد النداء إعادة تسمية كل ملف ناتج ديناميكيًا، وهو مفيد عند تصدير العديد من الصفحات دفعة واحدة.

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

## الشيفرة المصدرية الكاملة لجميع السيناريوهات
فيما يلي فئة واحدة تحتوي على كل طريقة تم توضيحها أعلاه. يمكنك تشغيل كل اختبار على حدة.

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
	// Set the "PageSet" to "0" to convert only the first page of a document.
	options.setPageSet(new PageSet(0));
	// Change the image's brightness and contrast.
	// Both are on a 0-1 scale and are at 0.5 by default.
	options.setImageBrightness(0.3f);
	options.setImageContrast(0.7f);
	// Change the horizontal resolution.
	// The default value for these properties is 96.0, for a resolution of 96dpi.
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

## المشكلات الشائعة والحلول
- **“غير قادر على العثور على ملف المستند”** – تأكد من أن مسار الملف يستخدم الفاصل الصحيح (`/` أو `\\`) لنظام التشغيل لديك.
- **الصور تظهر فارغة** – تأكد من ضبط `ImageColorMode` المناسب (مثلاً `GRAYSCALE` للـ TIFF).
- **أخطاء نفاد الذاكرة في المستندات الكبيرة** – عالج الصفحات على دفعات عبر تعديل نطاق `PageSet`.
- **جودة JPEG سيئة** – زد الدقة باستخدام `setHorizontalResolution` أو `setResolution`.

## الأسئلة المتكررة

**س: كيف أغيّر تنسيق الصورة عند الحفظ باستخدام Aspose.Words for Java؟**  
ج: اضبط التنسيق المطلوب في `ImageSaveOptions`. بالنسبة لـ PNG، يمكنك ببساطة إنشاء `ImageSaveOptions` وتعيين `SaveFormat.PNG` إذا لزم الأمر.

```java
ImageSaveOptions saveOptions = new ImageSaveOptions();
```

**س: هل يمكنني تخصيص إعدادات الضغط لصور TIFF؟**  
ج: نعم. استخدم `setTiffCompression` لاختيار خوارزمية ضغط مثل `CCITT_3`.

```java
saveOptions.setTiffCompression(TiffCompression.CCITT_3);
```

**س: كيف يمكنني حفظ صفحة محددة من المستند كصورة منفصلة؟**  
ج: استخدم طريقة `setPageSet` مع فهرس صفحة واحدة.

```java
saveOptions.setPageSet(new PageSet(0)); // Save the first page as an image
```

**س: كيف أطبّق إعدادات مخصصة على صور JPEG عند الحفظ؟**  
ج: عدّل الخصائص مثل السطوع، التباين، والدقة عبر `ImageSaveOptions`.

```java
options.setImageBrightness(0.3f);
options.setImageContrast(0.7f);
```

**س: كيف يمكنني استخدام رد نداء لتخصيص حفظ الصور؟**  
ج: نفّذ `IPageSavingCallback` وعيّنها باستخدام `setPageSavingCallback`.

```java
imageSaveOptions.setPageSavingCallback(new HandlePageSavingCallback());
```

```java
private static class HandlePageSavingCallback implements IPageSavingCallback {
    public void pageSaving(PageSavingArgs args) {
        args.setPageFileName(MessageFormat.format("Your Directory Path" + "Page_{0}.png", args.getPageIndex()));
    }
}
```

## الخلاصة
الآن لديك مجموعة أدوات كاملة لـ **حفظ الصفحة كـ jpeg**، استخراج الصور، التحكم في سطوع الصورة، ضبط دقة الصورة في Java، وإنشاء ملفات TIFF متعددة الصفحات باستخدام Aspose.Words for Java. جرّب إعدادات `ImageSaveOptions` المختلفة لتتناسب مع احتياجات مشروعك، واستكشف API أوسع لـ Aspose.Words لمزيد من إمكانيات معالجة المستندات.

---

**آخر تحديث:** 2025-12-27  
**تم الاختبار مع:** Aspose.Words for Java 24.12 (أحدث نسخة وقت الكتابة)  
**المؤلف:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}