---
date: 2025-12-27
description: Aspose.Words for Java का उपयोग करके पेज को JPEG के रूप में सहेजना और
  Word दस्तावेज़ों से छवियों को निकालना सीखें। इसमें इमेज की ब्राइटनेस, रिज़ॉल्यूशन
  सेट करने और मल्टीपेज TIFF बनाने के टिप्स शामिल हैं।
linktitle: Saving Images from Documents
second_title: Aspose.Words Java Document Processing API
title: Aspose.Words for Java के साथ पृष्ठ को JPEG के रूप में सहेजना और दस्तावेज़ों
  से छवियों को निकालना
url: /hi/java/document-loading-and-saving/saving-images-from-documents/
weight: 17
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Save page as JPEG और Aspose.Words for Java में दस्तावेज़ों से छवियों को निकालें

इस ट्यूटोरियल में आप सीखेंगे कि Aspose.Words for Java का उपयोग करके Word दस्तावेज़ से **save page as jpeg** कैसे किया जाता है और **extract images from Word** फ़ाइलों को कैसे निकाला जाता है। हम वास्तविक‑परिदृश्यों जैसे कि इमेज की ब्राइटनेस सेट करना, जावा में इमेज रेज़ोल्यूशन समायोजित करना, और मल्टीपेज TIFF बनाना, को कवर करेंगे। प्रत्येक चरण में तैयार‑कोड स्निपेट्स शामिल हैं ताकि आप उन्हें कॉपी, पेस्ट करके तुरंत परिणाम देख सकें।

## त्वरित उत्तर
- **क्या मैं एक पेज को JPEG के रूप में सहेज सकता हूँ?** हाँ – `ImageSaveOptions` के साथ `setPageSet(new PageSet(pageIndex))` का उपयोग करें।
- **इमेज की ब्राइटनेस कैसे बदलें?** `options.setImageBrightness(floatValue)` को कॉल करें (0‑1 रेंज)।
- **यदि मुझे मल्टीपेज TIFF चाहिए तो?** इच्छित पेजों को कवर करने वाला `PageSet` सेट करें और एक TIFF कम्प्रेशन मेथड चुनें।
- **इमेज रेज़ोल्यूशन कैसे नियंत्रित करें?** `setResolution(floatDpi)` या `setHorizontalResolution(floatDpi)` का उपयोग करें।
- **प्रोडक्शन के लिए लाइसेंस चाहिए?** गैर‑ट्रायल उपयोग के लिए एक वैध Aspose.Words लाइसेंस आवश्यक है।

## “save page as jpeg” क्या है?
एक पेज को JPEG के रूप में सहेजना का अर्थ है Word दस्तावेज़ के एक पेज को रास्टर इमेज फ़ाइल (JPEG) में बदलना। यह प्रीव्यू जनरेशन, थंबनेल निर्माण, या वेब पेजों में दस्तावेज़ पेज एम्बेड करने के लिए उपयोगी है जहाँ PDF रेंडरिंग व्यावहारिक नहीं है।

## Word दस्तावेज़ों से छवियों को निकालने का कारण?
कई व्यापार प्रक्रियाओं को मूल ग्राफिक्स (लोगो, डायग्राम, फ़ोटो) को DOCX फ़ाइल से निकालने की आवश्यकता होती है ताकि उन्हें पुन: उपयोग, अभिलेख या विश्लेषण किया जा सके। Aspose.Words प्रत्येक इमेज को उसके मूल फ़ॉर्मेट में बिना गुणवत्ता खोए निकालना आसान बनाता है।

## पूर्वापेक्षाएँ
- Java Development Kit (JDK 8 या बाद का) स्थापित हो।
- Aspose.Words for Java लाइब्रेरी को अपने प्रोजेक्ट में जोड़ें। इसे [here](https://releases.aspose.com/words/java/) से डाउनलोड करें।
- एक सैंपल Word दस्तावेज़ (जैसे `Rendering.docx`) को ज्ञात डायरेक्टरी में रखें।

## चरण 1: थ्रेशहोल्ड कंट्रोल के साथ TIFF के रूप में इमेज सहेजें (मल्टीपेज TIFF बनाएं)
उच्च‑कॉन्ट्रास्ट, ग्रेस्केल TIFF बनाने के लिए आप बाइनराइज़ेशन थ्रेशहोल्ड को नियंत्रित कर सकते हैं। यह तब उपयोगी होता है जब आपको अपने दस्तावेज़ का प्रिंटेबल, ब्लैक‑एंड‑व्हाइट संस्करण चाहिए।

```java
Document doc = new Document("Your Directory Path" + "Rendering.docx");
ImageSaveOptions saveOptions = new ImageSaveOptions();
saveOptions.setTiffCompression(TiffCompression.CCITT_3);
saveOptions.setImageColorMode(ImageColorMode.GRAYSCALE);
saveOptions.setTiffBinarizationMethod(ImageBinarizationMethod.FLOYD_STEINBERG_DITHERING);
saveOptions.setThresholdForFloydSteinbergDithering((byte) 254);
doc.save("Your Directory Path" + "ThresholdControlledImage.tiff", saveOptions);
```

## चरण 2: विशिष्ट पेज को मल्टीपेज TIFF के रूप में सहेजें
यदि आपको केवल कुछ पेजों (जैसे, पेज 1‑2) वाला TIFF चाहिए, तो `PageSet` कॉन्फ़िगर करें। यह **create multipage tiff** को दर्शाता है।

```java
Document doc = new Document("Your Directory Path" + "Rendering.docx");
ImageSaveOptions saveOptions = new ImageSaveOptions();
saveOptions.setPageSet(new PageSet(new PageRange(0, 1)));
saveOptions.setTiffCompression(TiffCompression.CCITT_4);
saveOptions.setResolution(160f);
doc.save("Your Directory Path" + "SpecificPageMultipage.tiff", saveOptions);
```

## चरण 3: इमेज को 1 BPP Indexed PNG के रूप में सहेजें
जब आपको अल्ट्रा‑लाइटवेट ब्लैक‑एंड‑व्हाइट PNG (1 बिट प्रति पिक्सेल) चाहिए, तो पिक्सेल फ़ॉर्मेट को उसी अनुसार सेट करें। यह कम‑बैंडविड्थ स्थितियों में सरल ग्राफिक्स एम्बेड करने के लिए उपयोगी है।

```java
Document doc = new Document("Your Directory Path" + "Rendering.docx");
ImageSaveOptions saveOptions = new ImageSaveOptions();
saveOptions.setPageSet(new PageSet(1));
saveOptions.setImageColorMode(ImageColorMode.BLACK_AND_WHITE);
saveOptions.setPixelFormat(ImagePixelFormat.FORMAT_1_BPP_INDEXED);
doc.save("Your Directory Path" + "1BPPIndexed.png", saveOptions);
```

## चरण 4: कस्टमाइज़ेशन के साथ पेज को JPEG के रूप में सहेजें (इमेज ब्राइटनेस और रेज़ोल्यूशन सेट करें)
यहाँ हम **save page as jpeg** करते हुए ब्राइटनेस, कॉन्ट्रास्ट और रेज़ोल्यूशन को समायोजित करते हैं—थंबनेल या वेब‑रेडी प्रीव्यू बनाने के लिए उपयुक्त।

```java
Document doc = new Document("Your Directory Path" + "Rendering.docx");
ImageSaveOptions options = new ImageSaveOptions();
options.setPageSet(new PageSet(0));
options.setImageBrightness(0.3f);          // set image brightness (0‑1)
options.setImageContrast(0.7f);            // set image contrast (0‑1)
options.setHorizontalResolution(72f);      // set image resolution in DPI
doc.save("Your Directory Path" + "CustomizedJPEG.jpeg", options);
```

## चरण 5: पेज‑सेविंग कॉलबैक का उपयोग (उन्नत कस्टमाइज़ेशन)
एक कॉलबैक आपको प्रत्येक आउटपुट फ़ाइल का नाम डायनामिक रूप से बदलने देता है, जो कई पेजों को एक साथ एक्सपोर्ट करने पर उपयोगी होता है।

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

## सभी परिदृश्यों के लिए पूर्ण स्रोत कोड
नीचे एक सिंगल क्लास है जिसमें ऊपर दिखाए गए सभी मेथड्स शामिल हैं। आप प्रत्येक टेस्ट को अलग‑अलग चलाकर देख सकते हैं।

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

## सामान्य समस्याएँ और समाधान
- **“Unable to locate the document file”** – अपने OS के लिए सही सेपरेटर (`/` या `\\`) का उपयोग करके फ़ाइल पाथ की जाँच करें।
- **Images appear blank** – सुनिश्चित करें कि आपने उपयुक्त `ImageColorMode` सेट किया है (जैसे TIFF के लिए `GRAYSCALE`)।
- **Out‑of‑memory errors on large documents** – `PageSet` रेंज को समायोजित करके पेजों को बैच में प्रोसेस करें।
- **JPEG quality looks poor** – `setHorizontalResolution` या `setResolution` के साथ रेज़ोल्यूशन बढ़ाएँ।

## अक्सर पूछे जाने वाले प्रश्न

**Q: Aspose.Words for Java के साथ सहेजते समय इमेज फ़ॉर्मेट कैसे बदलें?**  
A: `ImageSaveOptions` में वांछित फ़ॉर्मेट सेट करें। PNG के लिए, आप बस `ImageSaveOptions` का इंस्टैंस बनाकर `SaveFormat.PNG` असाइन कर सकते हैं यदि आवश्यक हो।

```java
ImageSaveOptions saveOptions = new ImageSaveOptions();
```

**Q: TIFF इमेजेज़ के लिए कम्प्रेशन सेटिंग्स को कस्टमाइज़ कर सकते हैं?**  
A: हाँ। `setTiffCompression` का उपयोग करके `CCITT_3` जैसे कम्प्रेशन एल्गोरिद्म को चुनें।

```java
saveOptions.setTiffCompression(TiffCompression.CCITT_3);
```

**Q: दस्तावेज़ से एक विशिष्ट पेज को अलग इमेज के रूप में कैसे सहेजें?**  
A: एकल पेज इंडेक्स के साथ `setPageSet` मेथड का उपयोग करें।

```java
saveOptions.setPageSet(new PageSet(0)); // Save the first page as an image
```

**Q: JPEG इमेजेज़ को सहेजते समय कस्टम सेटिंग्स कैसे लागू करें?**  
A: `ImageSaveOptions` के माध्यम से ब्राइटनेस, कॉन्ट्रास्ट और रेज़ोल्यूशन जैसी प्रॉपर्टीज़ को समायोजित करें।

```java
options.setImageBrightness(0.3f);
options.setImageContrast(0.7f);
```

**Q: इमेज सेविंग को कस्टमाइज़ करने के लिए कॉलबैक कैसे उपयोग करें?**  
A: `IPageSavingCallback` को इम्प्लीमेंट करें और `setPageSavingCallback` के साथ असाइन करें।

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

## निष्कर्ष
अब आपके पास **saving page as jpeg**, इमेज एक्सट्रैक्ट करने, इमेज ब्राइटनेस नियंत्रित करने, जावा में इमेज रेज़ोल्यूशन सेट करने, और Aspose.Words for Java के साथ मल्टीपेज TIFF फ़ाइलें बनाने के लिए एक पूर्ण टूलबॉक्स है। विभिन्न `ImageSaveOptions` सेटिंग्स के साथ प्रयोग करें ताकि आपके प्रोजेक्ट की जरूरतों को पूरा किया जा सके, और अधिक डॉक्यूमेंट मैनिपुलेशन क्षमताओं के लिए व्यापक Aspose.Words API को एक्सप्लोर करें।

---

**Last Updated:** 2025-12-27  
**Tested With:** Aspose.Words for Java 24.12 (latest at time of writing)  
**Author:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}