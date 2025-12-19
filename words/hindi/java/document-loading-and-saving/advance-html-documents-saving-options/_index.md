---
date: 2025-12-19
description: Aspose.Words Java के साथ HTML निर्यात करना सीखें, जिसमें Word को HTML
  के रूप में सहेजने और Word को HTML में कुशलतापूर्वक बदलने के उन्नत विकल्प शामिल हैं।
linktitle: Saving HTML Documents with
second_title: Aspose.Words Java Document Processing API
title: 'Aspose.Words Java के साथ HTML निर्यात कैसे करें: उन्नत विकल्प'
url: /hi/java/document-loading-and-saving/advance-html-documents-saving-options/
weight: 16
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words Java के साथ HTML निर्यात कैसे करें: उन्नत विकल्प

इस ट्यूटोरियल में आप **HTML निर्यात** को Aspose.Words for Java का उपयोग करके Word दस्तावेज़ों से कैसे प्राप्त किया जाए, यह जानेंगे। चाहे आपको वेब प्रकाशन के लिए **Word को HTML के रूप में सहेजना** हो या डाउनस्ट्रीम प्रोसेसिंग के लिए **Word को HTML में बदलना** हो, उन्नत सहेजने के विकल्प आपको आउटपुट पर सूक्ष्म नियंत्रण प्रदान करते हैं। हम प्रत्येक विकल्प को चरण‑दर‑चरण देखेंगे, यह बताएँगे कि कब उपयोग करना है, और वास्तविक‑दुनिया के परिदृश्य दिखाएँगे जहाँ ये सेटिंग्स अंतर पैदा करती हैं।

## Quick Answers
- **HTML निर्यात के लिए मुख्य क्लास कौन सी है?** `HtmlSaveOptions`  
- **फ़ॉन्ट्स को सीधे HTML में एम्बेड किया जा सकता है?** हाँ, `exportFontsAsBase64` को `true` सेट करें।  
- **मैं Word‑विशिष्ट राउंड‑ट्रिप डेटा कैसे रखूँ?** `exportRoundtripInformation` को सक्षम करें।  
- **वेक्टर ग्राफ़िक्स के लिए कौन सा फ़ॉर्मेट सबसे अच्छा है?** SVG आउटपुट के लिए `convertMetafilesToSvg` का उपयोग करें।  
- **क्या CSS क्लास नाम टकराव से बचा जा सकता है?** हाँ, `addCssClassNamePrefix` का उपयोग करें।

## 1. Introduction
Aspose.Words for Java एक मजबूत API है जो डेवलपर्स को प्रोग्रामेटिक रूप से Word दस्तावेज़ों को नियंत्रित करने की अनुमति देता है। यह गाइड उन्नत HTML दस्तावेज़ सहेजने के विकल्पों पर केंद्रित है, जिससे आप रूपांतरण प्रक्रिया को विशिष्ट वेब या इंटीग्रेशन आवश्यकताओं के अनुसार अनुकूलित कर सकते हैं।

## 2. Export Roundtrip Information
राउंड‑ट्रिप जानकारी को संरक्षित करने से आप HTML को वापस Word दस्तावेज़ में बिना लेआउट या फ़ॉर्मेटिंग विवरण खोए परिवर्तित कर सकते हैं।

```java
public void exportRoundtripInformation() throws Exception {
    Document doc = new Document("Your Directory Path" + "Rendering.docx");
    HtmlSaveOptions saveOptions = new HtmlSaveOptions();
    saveOptions.setExportRoundtripInformation(true);
    doc.save("Your Directory Path" + "WorkingWithHtmlSaveOptions.ExportRoundtripInformation.html", saveOptions);
}
```

### When to use
- जब आपको एक उलट‑पुलट (HTML → Word → HTML) रूपांतरण पाइपलाइन चाहिए।  
- सहयोगी संपादन परिदृश्यों में आदर्श जहाँ मूल Word संरचना को बरकरार रखना आवश्यक है।

## 3. Export Fonts as Base64
फ़ॉन्ट्स को सीधे HTML में एम्बेड करने से बाहरी फ़ॉन्ट निर्भरताएँ समाप्त हो जाती हैं और विभिन्न ब्राउज़रों में दृश्य समानता सुनिश्चित होती है।

```java

public void exportFontsAsBase64() throws Exception {
    Document doc = new Document("Your Directory Path" + "Rendering.docx");
    HtmlSaveOptions saveOptions = new HtmlSaveOptions();
    saveOptions.setExportFontsAsBase64(true);
    doc.save("Your Directory Path" + "WorkingWithHtmlSaveOptions.ExportFontsAsBase64.html", saveOptions);
}
```

### Pro tip
इस विकल्प का उपयोग तब करें जब लक्ष्य वातावरण में बाहरी संसाधनों तक सीमित पहुँच हो (जैसे ई‑मेल न्यूज़लेटर)।

## 4. Export Resources
CSS और फ़ॉन्ट संसाधनों को कैसे निकाला जाए, इसे नियंत्रित करें, और उन एसेट्स के लिए एक कस्टम फ़ोल्डर या URL उपनाम निर्दिष्ट करें।

```java

public void exportResources() throws Exception {
    Document doc = new Document("Your Directory Path" + "Rendering.docx");
    HtmlSaveOptions saveOptions = new HtmlSaveOptions();
    saveOptions.setCssStyleSheetType(CssStyleSheetType.EXTERNAL);
    saveOptions.setExportFontResources(true);
    saveOptions.setResourceFolder("Your Directory Path" + "Resources");
    saveOptions.setResourceFolderAlias("http://example.com/resources");
    doc.save("Your Directory Path" + "WorkingWithHtmlSaveOptions.ExportResources.html", saveOptions);
}
```

### Why it matters
CSS को एक बाहरी फ़ाइल में अलग करने से HTML का आकार घटता है और तेज़ पेज लोड के लिए कैशिंग संभव होती है।

## 5. Convert Metafiles to EMF or WMF
Metafiles (जैसे EMF/WMF) को ऐसे फ़ॉर्मेट में बदलें जिसे ब्राउज़र विश्वसनीय रूप से रेंडर कर सके।

```java

public void convertMetafilesToEmfOrWmf() throws Exception {

	string dataDir = "Your Document Directory";
    Document doc = new Document();
	DocumentBuilder builder = new DocumentBuilder(doc);

	builder.write("Here is an image as is: ");
	builder.insertHtml(
		"<img src=\"data:image/png;base64,\r\n                    iVBORw0KGgoAAAANSUhEUgAAAAoAAAAKCAYAAACNMs+9AAAABGdBTUEAALGP\r\n                    C/xhBQAAAAlwSFlzAAALEwAACxMBAJqcGAAAAAd0SU1FB9YGARc5KB0XV+IA\r\n                    AAAddEVYdENvbW1lbnQAQ3JlYXRlZCB3aXRoIFRoZSBHSU1Q72QlbgAAAF1J\r\n                    REFUGNO9zL0NglAAxPEfdLTs4BZM4DIO4C7OwQg2JoQ9LE1exdlYvBBeZ7jq\r\n                    ch9//q1uH4TLzw4d6+ErXMMcXuHWxId3KOETnnXXV6MJpcq2MLaI97CER3N0\r\n                    vr4MkhoXe0rZigAAAABJRU5ErkJggg==\" alt=\"Red dot\" />");

	HtmlSaveOptions saveOptions = new HtmlSaveOptions(); { saveOptions.setMetafileFormat(HtmlMetafileFormat.EMF_OR_WMF); }

	doc.save(dataDir + "WorkingWithHtmlSaveOptions.ConvertMetafilesToEmfOrWmf.html", saveOptions);
}
```

### Use case
EMF/WMF का चयन तब करें जब लक्ष्य ब्राउज़र इन वेक्टर फ़ॉर्मेट्स को सपोर्ट करता हो और आपको बिना गुणवत्ता हानि के स्केलिंग चाहिए।

## 6. Convert Metafiles to SVG
SVG सर्वोत्तम स्केलेबिलिटी प्रदान करता है और आधुनिक ब्राउज़रों में व्यापक रूप से समर्थित है।

```java

public void convertMetafilesToSvg() throws Exception {
	string dataDir = "Your Document Directory";
    Document doc = new Document();
	DocumentBuilder builder = new DocumentBuilder(doc);
	
	builder.write("Here is an SVG image: ");
	builder.insertHtml(
		"<svg height='210' width='500'>\r\n                <polygon points='100,10 40,198 190,78 10,78 160,198' \r\n                    style='fill:lime;stroke:purple;stroke-width:5;fill-rule:evenodd;' />\r\n            </svg> ");

	HtmlSaveOptions saveOptions = new HtmlSaveOptions(); { saveOptions.setMetafileFormat(HtmlMetafileFormat.SVG); }

	doc.save(dataDir + "WorkingWithHtmlSaveOptions.ConvertMetafilesToSvg.html", saveOptions);
}
```

### Benefit
SVG फ़ाइलें हल्की होती हैं और दस्तावेज़ को रिज़ॉल्यूशन‑इंडिपेंडेंट रखती हैं, जो रिस्पॉन्सिव वेब डिज़ाइन के लिए आदर्श है।

## 7. Add CSS Class Name Prefix
सभी उत्पन्न CSS क्लास नामों के पहले एक उपसर्ग जोड़कर शैली टकराव से बचें।

```java

public void addCssClassNamePrefix() throws Exception {
    Document doc = new Document("Your Directory Path" + "Rendering.docx");
    HtmlSaveOptions saveOptions = new HtmlSaveOptions();
    saveOptions.setCssStyleSheetType(CssStyleSheetType.EXTERNAL);
    saveOptions.setCssClassNamePrefix("pfx_");
    doc.save("Your Directory Path" + "WorkingWithHtmlSaveOptions.AddCssClassNamePrefix.html", saveOptions);
}
```

### Practical tip
जब आप HTML को मौजूदा पृष्ठों में एम्बेड करते हैं, तो एक विशिष्ट उपसर्ग (जैसे आपके प्रोजेक्ट का नाम) उपयोग करें ताकि CSS टकराव न हो।

## 8. Export CID URLs for MHTML Resources
MHTML के रूप में सहेजते समय आप संसाधनों को Content‑ID URLs के माध्यम से निर्यात कर सकते हैं, जिससे ई‑मेल संगतता बेहतर होती है।

```java

public void exportCidUrlsForMhtmlResources() throws Exception {
	string dataDir = "Your Document Directory";
    Document doc = new Document(dataDir + "Content-ID.docx");

	HtmlSaveOptions saveOptions = new HtmlSaveOptions(SaveFormat.MHTML);
	{
		saveOptions.setPrettyFormat(true); saveOptions.setExportCidUrlsForMhtmlResources(true);
	}

	doc.save(dataDir + "WorkingWithHtmlSaveOptions.ExportCidUrlsForMhtmlResources.mhtml", saveOptions);
}
```

### When to use
एकल, स्व‑समाहित HTML फ़ाइल बनाने के लिए आदर्श जिसे ई‑मेल में अटैच किया जा सके।

## 9. Resolve Font Names
सुनिश्चित करता है कि HTML सही फ़ॉन्ट परिवारों को संदर्भित करे, जिससे क्रॉस‑प्लेटफ़ॉर्म संगतता में सुधार होता है।

```java

public void resolveFontNames() throws Exception {
    
	string dataDir = "Your Document Directory";
	Document doc = new Document(dataDir + "Missing font.docx");

	HtmlSaveOptions saveOptions = new HtmlSaveOptions(SaveFormat.HTML);
	{
		saveOptions.setPrettyFormat(true); saveOptions.setResolveFontNames(true);
	}

	doc.save(dataDir + "WorkingWithHtmlSaveOptions.ResolveFontNames.html", saveOptions);
}
```

### Why it helps
यदि मूल दस्तावेज़ में ऐसे फ़ॉन्ट उपयोग किए गए हैं जो क्लाइंट मशीन पर स्थापित नहीं हैं, तो यह विकल्प उन्हें वेब‑सेफ़ विकल्पों से बदल देता है।

## 10. Export Text Input Form Field as Text
फ़ॉर्म फ़ील्ड को इंटरैक्टिव HTML इनपुट तत्वों के बजाय साधारण टेक्स्ट के रूप में रेंडर करें।

```java

public void exportTextInputFormFieldAsText() throws Exception {
    
	string dataDir = "Your Document Directory";
	Document doc = new Document(dataDir + "Rendering.docx");

	String imagesDir = Path.combine(dataDir, "Images");

	// The folder specified needs to exist and should be empty.
	if (Directory.exists(imagesDir))
		Directory.delete(imagesDir, true);

	Directory.createDirectory(imagesDir);

	// Set an option to export form fields as plain text, not as HTML input elements.
	HtmlSaveOptions saveOptions = new HtmlSaveOptions(SaveFormat.HTML);
	{
		saveOptions.setExportTextInputFormFieldAsText(true); saveOptions.setImagesFolder(imagesDir);
	}

	doc.save(dataDir + "WorkingWithHtmlSaveOptions.ExportTextInputFormFieldAsText.html", saveOptions);
}
```

### Use case
जब आपको फ़ॉर्म का केवल‑पढ़ने योग्य प्रतिनिधित्व चाहिए, जैसे अभिलेखीय या प्रिंटिंग उद्देश्यों के लिए।

## Common Pitfalls & Troubleshooting
| Issue | Typical Cause | Fix |
|-------|---------------|-----|
| आउटपुट में फ़ॉन्ट्स गायब | `exportFontsAsBase64` सक्षम नहीं है | `setExportFontsAsBase64(true)` सेट करें |
| एम्बेड करने के बाद CSS टूटना | `EXTERNAL` का उपयोग किया लेकिन CSS फ़ाइल प्रदान नहीं की | निर्दिष्ट `resourceFolderAlias` पर CSS फ़ाइल को डिप्लॉय करें |
| बड़ी HTML आकार | कई इमेज को Base64 में एम्बेड किया गया | `setExportFontResources(true)` के माध्यम से बाहरी इमेज संसाधनों पर स्विच करें और `resourceFolder` कॉन्फ़िगर करें |
| पुराने ब्राउज़र में SVG नहीं रेंडर हो रहा | ब्राउज़र में SVG सपोर्ट नहीं है | EMF/WMF के साथ fallback PNG प्रदान करें |

## Frequently Asked Questions

**Q: क्या मैं फ़ॉन्ट्स को Base64 के रूप में एम्बेड कर सकता हूँ और साथ ही बाहरी CSS रख सकता हूँ?**  
A: हाँ। `exportFontsAsBase64(true)` सेट करें जबकि `CssStyleSheetType.EXTERNAL` को रखकर फ़ॉन्ट डेटा को शैली नियमों से अलग रखें।

**Q: मौजूदा HTML को वापस Word दस्तावेज़ में कैसे बदलूँ?**  
A: `Document doc = new Document("input.html");` से HTML लोड करें और फिर `doc.save("output.docx");` करें। प्रारंभिक निर्यात के दौरान `exportRoundtripInformation` का उपयोग करके राउंड‑ट्रिप डेटा संरक्षित रखें।

**Q: SVG रूपांतरण के उपयोग से प्रदर्शन पर असर पड़ता है क्या?**  
A: बड़े Metafiles को SVG में बदलने से प्रोसेसिंग समय बढ़ सकता है, लेकिन परिणामी HTML आमतौर पर छोटा होता है और ब्राउज़र में तेज़ रेंडर होता है।

**Q: क्या ये विकल्प Aspose.Words for .NET के साथ भी काम करते हैं?**  
A: समान अवधारणाएँ .NET API में भी मौजूद हैं, हालांकि मेथड नाम थोड़ा अलग हो सकते हैं (जैसे `HtmlSaveOptions` दोनों प्लेटफ़ॉर्म पर साझा है)।

**Q: ई‑मेल‑फ्रेंडली HTML के लिए कौन सा विकल्प चुनूँ?**  
A: सभी संसाधनों को सीधे ई‑मेल बॉडी में एम्बेड करने के लिए `SaveFormat.MHTML` के साथ `exportCidUrlsForMhtmlResources` का उपयोग करें।

---

**Last Updated:** 2025-12-19  
**Tested With:** Aspose.Words for Java 24.12  
**Author:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}