---
title: Java के लिए Aspose.Words में दस्तावेज़ों से छवियाँ सहेजना
linktitle: दस्तावेज़ों से छवियाँ सहेजना
second_title: Aspose.Words जावा दस्तावेज़ प्रसंस्करण एपीआई
description: हमारे विस्तृत चरण-दर-चरण गाइड के साथ Java के लिए Aspose.Words का उपयोग करके दस्तावेज़ों से छवियों को सहेजना सीखें। प्रारूप, संपीड़न और बहुत कुछ अनुकूलित करें।
weight: 17
url: /hi/java/document-loading-and-saving/saving-images-from-documents/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Java के लिए Aspose.Words में दस्तावेज़ों से छवियाँ सहेजना


## जावा के लिए Aspose.Words में दस्तावेज़ों से छवियाँ सहेजने का परिचय

इस ट्यूटोरियल में, हम सीखेंगे कि Aspose.Words for Java का उपयोग करके दस्तावेज़ों से छवियों को कैसे सहेजा जाए। हम छवि सहेजने के लिए विभिन्न परिदृश्यों और अनुकूलन विकल्पों को कवर करेंगे। यह गाइड स्रोत कोड उदाहरणों के साथ चरण-दर-चरण निर्देश प्रदान करता है।

## आवश्यक शर्तें

 शुरू करने से पहले, सुनिश्चित करें कि आपके प्रोजेक्ट में Aspose.Words for Java लाइब्रेरी एकीकृत है। आप इसे यहाँ से डाउनलोड कर सकते हैं[यहाँ](https://releases.aspose.com/words/java/).

## चरण 1: थ्रेशोल्ड नियंत्रण के साथ छवियों को TIFF के रूप में सहेजना

थ्रेसहोल्ड नियंत्रण के साथ छवियों को TIFF प्रारूप में सहेजने के लिए, इन चरणों का पालन करें:

```java
Document doc = new Document("Your Directory Path" + "Rendering.docx");
ImageSaveOptions saveOptions = new ImageSaveOptions();
saveOptions.setTiffCompression(TiffCompression.CCITT_3);
saveOptions.setImageColorMode(ImageColorMode.GRAYSCALE);
saveOptions.setTiffBinarizationMethod(ImageBinarizationMethod.FLOYD_STEINBERG_DITHERING);
saveOptions.setThresholdForFloydSteinbergDithering((byte) 254);
doc.save("Your Directory Path" + "ThresholdControlledImage.tiff", saveOptions);
```

## चरण 2: किसी विशिष्ट पृष्ठ को मल्टीपेज TIFF के रूप में सहेजना

किसी विशिष्ट पृष्ठ को बहुपृष्ठ TIFF के रूप में सहेजने के लिए, निम्नलिखित कोड का उपयोग करें:

```java
Document doc = new Document("Your Directory Path" + "Rendering.docx");
ImageSaveOptions saveOptions = new ImageSaveOptions();
saveOptions.setPageSet(new PageSet(new PageRange(0, 1)));
saveOptions.setTiffCompression(TiffCompression.CCITT_4);
saveOptions.setResolution(160f);
doc.save("Your Directory Path" + "SpecificPageMultipage.tiff", saveOptions);
```

## चरण 3: छवियों को 1 BPP अनुक्रमित PNG के रूप में सहेजना

छवियों को 1 BPP अनुक्रमित PNG के रूप में सहेजने के लिए, इन चरणों का पालन करें:

```java
Document doc = new Document("Your Directory Path" + "Rendering.docx");
ImageSaveOptions saveOptions = new ImageSaveOptions();
saveOptions.setPageSet(new PageSet(1));
saveOptions.setImageColorMode(ImageColorMode.BLACK_AND_WHITE);
saveOptions.setPixelFormat(ImagePixelFormat.FORMAT_1_BPP_INDEXED);
doc.save("Your Directory Path" + "1BPPIndexed.png", saveOptions);
```

## चरण 4: अनुकूलन के साथ पृष्ठ को JPEG के रूप में सहेजना

किसी विशिष्ट पृष्ठ को अनुकूलन विकल्पों के साथ JPEG के रूप में सहेजने के लिए, इस कोड का उपयोग करें:

```java
Document doc = new Document("Your Directory Path" + "Rendering.docx");
ImageSaveOptions options = new ImageSaveOptions();
options.setPageSet(new PageSet(0));
options.setImageBrightness(0.3f);
options.setImageContrast(0.7f);
options.setHorizontalResolution(72f);
doc.save("Your Directory Path" + "CustomizedJPEG.jpeg", options);
```

## चरण 5: पेज सेविंग कॉलबैक का उपयोग करना

आप पेज सेविंग को कस्टमाइज़ करने के लिए कॉलबैक का उपयोग कर सकते हैं। यहाँ एक उदाहरण दिया गया है:

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

## जावा के लिए Aspose.Words में दस्तावेज़ों से छवियों को सहेजने के लिए पूर्ण स्रोत कोड

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
	// किसी दस्तावेज़ के केवल प्रथम पृष्ठ को परिवर्तित करने के लिए "PageSet" को "0" पर सेट करें।
	options.setPageSet(new PageSet(0));
	// छवि की चमक और कंट्रास्ट बदलें.
	// दोनों 0-1 स्केल पर हैं और डिफ़ॉल्ट रूप से 0.5 पर हैं।
	options.setImageBrightness(0.3f);
	options.setImageContrast(0.7f);
	// क्षैतिज रिज़ोल्यूशन बदलें.
	// इन गुणों के लिए डिफ़ॉल्ट मान 96.0 है, जिसका रिज़ॉल्यूशन 96dpi है।
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

## निष्कर्ष

आपने सीखा है कि Java के लिए Aspose.Words का उपयोग करके दस्तावेज़ों से छवियों को कैसे सहेजा जाता है। ये उदाहरण छवि सहेजने के लिए विभिन्न अनुकूलन विकल्पों को प्रदर्शित करते हैं, जिसमें प्रारूप, संपीड़न और कॉलबैक उपयोग शामिल हैं। Java की शक्तिशाली क्षमताओं के लिए Aspose.Words के साथ और अधिक संभावनाओं का पता लगाएं।

## अक्सर पूछे जाने वाले प्रश्न

### मैं Aspose.Words for Java के साथ सहेजते समय छवि प्रारूप कैसे बदलूं?

 आप इच्छित प्रारूप निर्दिष्ट करके छवि प्रारूप बदल सकते हैं`ImageSaveOptions` उदाहरण के लिए, PNG के रूप में सहेजने के लिए, उपयोग करें`SaveFormat.PNG` जैसा कि कोड में दिखाया गया है:

```java
ImageSaveOptions saveOptions = new ImageSaveOptions();
```

### क्या मैं TIFF छवियों के लिए संपीड़न सेटिंग्स को अनुकूलित कर सकता हूँ?

हां, आप TIFF इमेज कम्प्रेशन सेटिंग को कस्टमाइज़ कर सकते हैं। उदाहरण के लिए, कम्प्रेशन विधि को CCITT_3 पर सेट करने के लिए, निम्न कोड का उपयोग करें:

```java
saveOptions.setTiffCompression(TiffCompression.CCITT_3);
```

### मैं किसी दस्तावेज़ से किसी विशिष्ट पृष्ठ को अलग छवि के रूप में कैसे सहेज सकता हूँ?

 किसी विशिष्ट पृष्ठ को छवि के रूप में सहेजने के लिए, का उपयोग करें`setPageSet`विधि में`ImageSaveOptions` उदाहरण के लिए, केवल पहला पेज सहेजने के लिए, सेट करें`PageSet` को`new PageSet(0)`.

```java
saveOptions.setPageSet(new PageSet(0)); // पहले पृष्ठ को छवि के रूप में सहेजें
```

### मैं JPEG छवियों को सहेजते समय उन पर कस्टम सेटिंग्स कैसे लागू करूँ?

आप JPEG छवियों पर कस्टम सेटिंग्स लागू कर सकते हैं`ImageSaveOptions`. चमक, कंट्रास्ट और रिज़ॉल्यूशन जैसे गुणों को समायोजित करें। उदाहरण के लिए, चमक को 0.3 और कंट्रास्ट को 0.7 में बदलने के लिए, इस कोड का उपयोग करें:

```java
options.setImageBrightness(0.3f);
options.setImageContrast(0.7f);
```

### मैं छवि सहेजने को अनुकूलित करने के लिए कॉलबैक का उपयोग कैसे कर सकता हूं?

 छवि सहेजने को अनुकूलित करने के लिए कॉलबैक का उपयोग करने के लिए, सेट करें`PageSavingCallback` में`ImageSaveOptions` एक ऐसा वर्ग बनाएं जो कार्यान्वित करता है`IPageSavingCallback` इंटरफ़ेस और ओवरराइड`pageSaving` तरीका।

```java
imageSaveOptions.setPageSavingCallback(new HandlePageSavingCallback());
```

 फिर, एक वर्ग बनाएं जो कार्यान्वित करता है`IPageSavingCallback` इंटरफ़ेस और फ़ाइल नाम और स्थान को अनुकूलित करें`pageSaving` तरीका।

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
