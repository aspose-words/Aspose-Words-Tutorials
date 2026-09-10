---
date: 2025-12-27
description: เรียนรู้วิธีบันทึกหน้าเป็น JPEG และดึงรูปภาพจากเอกสาร Word ด้วย Aspose.Words
  for Java รวมถึงเคล็ดลับในการตั้งค่าความสว่างของภาพ ความละเอียด และการสร้างไฟล์ TIFF
  หลายหน้า.
linktitle: Saving Images from Documents
second_title: Aspose.Words Java Document Processing API
title: วิธีบันทึกหน้าเป็น JPEG และดึงรูปภาพจากเอกสารด้วย Aspose.Words สำหรับ Java
url: /th/java/document-loading-and-saving/saving-images-from-documents/
weight: 17
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# บันทึกหน้าเป็น JPEG และสกัดภาพจากเอกสารใน Aspose.Words for Java

ในบทแนะนำนี้คุณจะได้ค้นพบวิธี **save page as jpeg** จากเอกสาร Word และวิธี **extract images from Word** ด้วย Aspose.Words for Java เราจะพาไปผ่านสถานการณ์จริง เช่น การตั้งค่าความสว่างของภาพ, การปรับความละเอียดของภาพใน Java, และการสร้างไฟล์ TIFF หลายหน้า แต่ละขั้นตอนจะมีโค้ดตัวอย่างที่พร้อมรันเพื่อให้คุณคัดลอก วาง และดูผลลัพธ์ได้ทันที.

## คำตอบอย่างรวดเร็ว
- **Can I save a single page as JPEG?** ใช่ – ใช้ `ImageSaveOptions` กับ `setPageSet(new PageSet(pageIndex))`.
- **How do I change image brightness?** เรียก `options.setImageBrightness(floatValue)` (ช่วง 0‑1).
- **What if I need a multipage TIFF?** ตั้งค่า `PageSet` ที่ครอบคลุมหน้าที่ต้องการและเลือกวิธีการบีบอัด TIFF.
- **How can I control image resolution?** ใช้ `setResolution(floatDpi)` หรือ `setHorizontalResolution(floatDpi)`.
- **Do I need a license for production?** จำเป็นต้องมีใบอนุญาต Aspose.Words ที่ถูกต้องสำหรับการใช้งานที่ไม่ใช่รุ่นทดลอง.

## “save page as jpeg” คืออะไร
การบันทึกหน้าเป็น JPEG หมายถึงการแปลงหน้าหนึ่งของเอกสาร Word ให้เป็นไฟล์ภาพเรสเตอร์ (JPEG) ซึ่งเป็นประโยชน์สำหรับการสร้างตัวอย่างภาพ, การสร้างรูปย่อ, หรือการฝังหน้าของเอกสารในเว็บเพจที่การแสดงผล PDF ไม่เป็นไปได้จริง.

## ทำไมต้องสกัดภาพจากเอกสาร Word
กระบวนการทำงานหลายอย่างในธุรกิจต้องการดึงกราฟิกต้นฉบับ (โลโก้, แผนภาพ, รูปถ่าย) จากไฟล์ DOCX เพื่อการนำกลับมาใช้ใหม่, การเก็บถาวร, หรือการวิเคราะห์ Aspose.Words ทำให้การสกัดแต่ละภาพในรูปแบบดั้งเดิมโดยไม่สูญเสียคุณภาพเป็นเรื่องง่าย.

## ข้อกำหนดเบื้องต้น
- Java Development Kit (JDK 8 หรือใหม่กว่า) ติดตั้งแล้ว.
- ไลบรารี Aspose.Words for Java เพิ่มเข้าในโปรเจกต์ของคุณ ดาวน์โหลดได้จาก [here](https://releases.aspose.com/words/java/).
- ตัวอย่างเอกสาร Word (เช่น `Rendering.docx`) วางไว้ในไดเรกทอรีที่ทราบ.

## ขั้นตอนที่ 1: บันทึกภาพเป็น TIFF พร้อมการควบคุม Threshold (สร้าง Multipage TIFF)
เพื่อสร้าง TIFF แบบสีเทาที่มีคอนทราสต์สูง คุณสามารถควบคุมค่า threshold ของการไบนารีได้ ซึ่งเป็นประโยชน์เมื่อคุณต้องการเวอร์ชันพิมพ์สีขาว-ดำของเอกสารของคุณ.

```java
Document doc = new Document("Your Directory Path" + "Rendering.docx");
ImageSaveOptions saveOptions = new ImageSaveOptions();
saveOptions.setTiffCompression(TiffCompression.CCITT_3);
saveOptions.setImageColorMode(ImageColorMode.GRAYSCALE);
saveOptions.setTiffBinarizationMethod(ImageBinarizationMethod.FLOYD_STEINBERG_DITHERING);
saveOptions.setThresholdForFloydSteinbergDithering((byte) 254);
doc.save("Your Directory Path" + "ThresholdControlledImage.tiff", saveOptions);
```

## ขั้นตอนที่ 2: บันทึกหน้าที่ระบุเป็น Multipage TIFF
หากคุณต้องการ TIFF ที่มีเพียงส่วนหนึ่งของหน้า (เช่น หน้า 1‑2) ให้กำหนดค่า `PageSet` นี่เป็นการสาธิต **create multipage tiff**.

```java
Document doc = new Document("Your Directory Path" + "Rendering.docx");
ImageSaveOptions saveOptions = new ImageSaveOptions();
saveOptions.setPageSet(new PageSet(new PageRange(0, 1)));
saveOptions.setTiffCompression(TiffCompression.CCITT_4);
saveOptions.setResolution(160f);
doc.save("Your Directory Path" + "SpecificPageMultipage.tiff", saveOptions);
```

## ขั้นตอนที่ 3: บันทึกภาพเป็น PNG แบบ Indexed 1 BPP
เมื่อคุณต้องการ PNG สีขาว-ดำที่มีขนาดเบามาก (1 บิตต่อพิกเซล) ให้ตั้งค่ารูปแบบพิกเซลให้สอดคล้อง นี่เป็นประโยชน์สำหรับการฝังกราฟิกง่าย ๆ ในสถานการณ์ที่แบนด์วิดท์ต่ำ.

```java
Document doc = new Document("Your Directory Path" + "Rendering.docx");
ImageSaveOptions saveOptions = new ImageSaveOptions();
saveOptions.setPageSet(new PageSet(1));
saveOptions.setImageColorMode(ImageColorMode.BLACK_AND_WHITE);
saveOptions.setPixelFormat(ImagePixelFormat.FORMAT_1_BPP_INDEXED);
doc.save("Your Directory Path" + "1BPPIndexed.png", saveOptions);
```

## ขั้นตอนที่ 4: บันทึกหน้าเป็น JPEG พร้อมการปรับแต่ง (ตั้งค่าความสว่างและความละเอียดของภาพ)
ที่นี่เราจะ **save page as jpeg** พร้อมการปรับความสว่าง, คอนทราสต์, และความละเอียด—เหมาะสำหรับการสร้างรูปย่อหรือภาพตัวอย่างที่พร้อมใช้งานบนเว็บ.

```java
Document doc = new Document("Your Directory Path" + "Rendering.docx");
ImageSaveOptions options = new ImageSaveOptions();
options.setPageSet(new PageSet(0));
options.setImageBrightness(0.3f);          // set image brightness (0‑1)
options.setImageContrast(0.7f);            // set image contrast (0‑1)
options.setHorizontalResolution(72f);      // set image resolution in DPI
doc.save("Your Directory Path" + "CustomizedJPEG.jpeg", options);
```

## ขั้นตอนที่ 5: ใช้ Page‑Saving Callback (การปรับแต่งขั้นสูง)
Callback จะทำให้คุณสามารถเปลี่ยนชื่อไฟล์ผลลัพธ์แต่ละไฟล์ได้แบบไดนามิก ซึ่งเป็นประโยชน์เมื่อส่งออกหลายหน้าพร้อมกัน.

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

## โค้ดต้นฉบับเต็มสำหรับทุกสถานการณ์
ด้านล่างเป็นคลาสเดียวที่มีทุกเมธอดที่แสดงข้างต้น คุณสามารถรันแต่ละการทดสอบแยกกันได้.

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

## ปัญหาทั่วไปและวิธีแก้
- **“Unable to locate the document file”** – ตรวจสอบว่าเส้นทางไฟล์ใช้ตัวคั่นที่ถูกต้อง (`/` หรือ `\\`) สำหรับระบบปฏิบัติการของคุณ.
- **Images appear blank** – ตรวจสอบว่าคุณตั้งค่า `ImageColorMode` ที่เหมาะสม (เช่น `GRAYSCALE` สำหรับ TIFF).
- **Out‑of‑memory errors on large documents** – ประมวลผลหน้าเป็นชุดโดยปรับช่วง `PageSet`.
- **JPEG quality looks poor** – เพิ่มความละเอียดด้วย `setHorizontalResolution` หรือ `setResolution`.

## คำถามที่พบบ่อย

**Q: How do I change the image format when saving with Aspose.Words for Java?**  
A: ตั้งค่าฟอร์แมตที่ต้องการใน `ImageSaveOptions` สำหรับ PNG คุณสามารถสร้างอินสแตนซ์ของ `ImageSaveOptions` แล้วกำหนด `SaveFormat.PNG` หากต้องการ.

```java
ImageSaveOptions saveOptions = new ImageSaveOptions();
```

**Q: Can I customize the compression settings for TIFF images?**  
A: ใช่. ใช้ `setTiffCompression` เพื่อเลือกอัลกอริทึมการบีบอัด เช่น `CCITT_3`.

```java
saveOptions.setTiffCompression(TiffCompression.CCITT_3);
```

**Q: How can I save a specific page from a document as a separate image?**  
A: ใช้เมธอด `setPageSet` พร้อมดัชนีหน้าหนึ่งหน้า.

```java
saveOptions.setPageSet(new PageSet(0)); // Save the first page as an image
```

**Q: How do I apply custom settings to JPEG images when saving?**  
A: ปรับคุณสมบัติเช่น ความสว่าง, คอนทราสต์, และความละเอียดผ่าน `ImageSaveOptions`.

```java
options.setImageBrightness(0.3f);
options.setImageContrast(0.7f);
```

**Q: How can I use a callback for customizing image saving?**  
A: สร้างการทำงานของ `IPageSavingCallback` แล้วกำหนดให้กับ `setPageSavingCallback`.

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

## สรุป
คุณมีชุดเครื่องมือครบถ้วนสำหรับ **saving page as jpeg**, การสกัดภาพ, การควบคุมความสว่างของภาพ, การตั้งค่าความละเอียดของภาพใน Java, และการสร้างไฟล์ TIFF หลายหน้าด้วย Aspose.Words for Java ทดลองใช้การตั้งค่า `ImageSaveOptions` ต่าง ๆ เพื่อให้ตรงกับความต้องการของโครงการของคุณ และสำรวจ API ของ Aspose.Words ที่กว้างขวางเพื่อความสามารถในการจัดการเอกสารเพิ่มเติม.

---

**อัปเดตล่าสุด:** 2025-12-27  
**ทดสอบด้วย:** Aspose.Words for Java 24.12 (latest at time of writing)  
**ผู้เขียน:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}