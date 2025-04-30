---
"description": "जावा के लिए Aspose.Words में लोड विकल्पों में महारत हासिल करें। दस्तावेज़ लोडिंग को कस्टमाइज़ करें, एन्क्रिप्शन को संभालें, आकृतियों को बदलें, Word संस्करण सेट करें, और कुशल जावा दस्तावेज़ प्रसंस्करण के लिए और भी बहुत कुछ करें।"
"linktitle": "लोड विकल्प का उपयोग करना"
"second_title": "Aspose.Words जावा दस्तावेज़ प्रसंस्करण एपीआई"
"title": "जावा के लिए Aspose.Words में लोड विकल्प का उपयोग करना"
"url": "/hi/java/document-loading-and-saving/using-load-options/"
"weight": 11
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# जावा के लिए Aspose.Words में लोड विकल्प का उपयोग करना


## जावा के लिए Aspose.Words में लोड विकल्पों के साथ कार्य करने का परिचय

इस ट्यूटोरियल में, हम जावा के लिए Aspose.Words में लोड विकल्पों के साथ काम करने का तरीका जानेंगे। लोड विकल्प आपको दस्तावेज़ों को लोड करने और संसाधित करने के तरीके को अनुकूलित करने की अनुमति देते हैं। हम गंदे फ़ील्ड को अपडेट करने, एन्क्रिप्ट किए गए दस्तावेज़ों को लोड करने, आकृतियों को Office Math में बदलने, MS Word संस्करण को सेट करने, एक अस्थायी फ़ोल्डर निर्दिष्ट करने, चेतावनियों को संभालने और मेटाफ़ाइल को PNG में बदलने सहित विभिन्न परिदृश्यों को कवर करेंगे। आइए चरण दर चरण आगे बढ़ते हैं।

## गंदे फ़ील्ड अपडेट करें

```java
LoadOptions loadOptions = new LoadOptions();
loadOptions.setUpdateDirtyFields(true);

Document doc = new Document("Your Directory Path" + "Dirty field.docx", loadOptions);
doc.save("Your Directory Path" + "WorkingWithLoadOptions.UpdateDirtyFields.docx");
```

यह कोड स्निपेट दर्शाता है कि दस्तावेज़ में गंदे फ़ील्ड को कैसे अपडेट किया जाए। `setUpdateDirtyFields(true)` विधि का उपयोग यह सुनिश्चित करने के लिए किया जाता है कि दस्तावेज़ लोड होने के दौरान गंदे फ़ील्ड अपडेट हो जाएं।

## एन्क्रिप्टेड दस्तावेज़ लोड करें

```java
@Test
public void loadEncryptedDocument() throws Exception {
    Document doc = new Document("Your Directory Path" + "Encrypted.docx", new LoadOptions("docPassword"));
    doc.save("Your Directory Path" + "WorkingWithLoadOptions.LoadAndSaveEncryptedOdt.odt", new OdtSaveOptions("newPassword"));
}
```

यहां, हम पासवर्ड का उपयोग करके एक एन्क्रिप्टेड दस्तावेज़ लोड करते हैं। `LoadOptions` कंस्ट्रक्टर दस्तावेज़ पासवर्ड स्वीकार करता है, और आप दस्तावेज़ को सहेजते समय एक नया पासवर्ड भी निर्दिष्ट कर सकते हैं `OdtSaveOptions`.

## आकृति को कार्यालय गणित में बदलें

```java
LoadOptions loadOptions = new LoadOptions();
loadOptions.setConvertShapeToOfficeMath(true);

Document doc = new Document("Your Directory Path" + "Office math.docx", loadOptions);
doc.save("Your Directory Path" + "WorkingWithLoadOptions.ConvertShapeToOfficeMath.docx");
```

यह कोड दर्शाता है कि दस्तावेज़ लोड करते समय आकृतियों को Office Math ऑब्जेक्ट में कैसे परिवर्तित किया जाए। `setConvertShapeToOfficeMath(true)` विधि इस रूपांतरण को सक्षम बनाती है.

## एमएस वर्ड संस्करण सेट करें

```java
@Test
public void setMsWordVersion() throws Exception {
    LoadOptions loadOptions = new LoadOptions();
    loadOptions.setMswVersion(MsWordVersion.WORD_2010);

    Document doc = new Document("Your Directory Path" + "Document.docx", loadOptions);
    doc.save("Your Directory Path" + "WorkingWithLoadOptions.SetMsWordVersion.docx");
}
```

आप दस्तावेज़ लोड करने के लिए MS Word संस्करण निर्दिष्ट कर सकते हैं। इस उदाहरण में, हमने संस्करण को Microsoft Word 2010 पर सेट किया है `setMswVersion`.

## अस्थायी फ़ोल्डर का उपयोग करें

```java
@Test
public void useTempFolder() throws Exception {
    LoadOptions loadOptions = new LoadOptions();
    loadOptions.setTempFolder("Your Directory Path");

    Document doc = new Document("Your Directory Path" + "Document.docx", loadOptions);
}
```

अस्थायी फ़ोल्डर का उपयोग करके सेट करके `setTempFolder`, आप यह नियंत्रित कर सकते हैं कि दस्तावेज़ प्रसंस्करण के दौरान अस्थायी फ़ाइलें कहाँ संग्रहीत की जाएँ।

## चेतावनी कॉलबैक

```java
@Test
public void warningCallback() throws Exception {
    LoadOptions loadOptions = new LoadOptions();
    loadOptions.setWarningCallback(new DocumentLoadingWarningCallback());

    Document doc = new Document("Your Directory Path" + "Document.docx", loadOptions);
}

public static class DocumentLoadingWarningCallback implements IWarningCallback {
    public void warning(WarningInfo info) {
        // दस्तावेज़ लोड होने के दौरान आने वाली चेतावनियों को संभालें.
        System.out.println(MessageFormat.format("WARNING: {0}, source: {1}", info.getWarningType(), info.getSource()));
        System.out.println(MessageFormat.format("\tDescription: {0}", info.getDescription()));
    }
}
```

यह कोड प्रदर्शित करता है कि दस्तावेज़ लोड होने के दौरान चेतावनियों को संभालने के लिए चेतावनी कॉलबैक कैसे सेट किया जाए। चेतावनियाँ होने पर आप अपने एप्लिकेशन के व्यवहार को अनुकूलित कर सकते हैं।

## मेटाफ़ाइल्स को PNG में बदलें

```java
@Test
public void convertMetafilesToPng() throws Exception {
    LoadOptions loadOptions = new LoadOptions();
    loadOptions.setConvertMetafilesToPng(true);

    Document doc = new Document("Your Directory Path" + "WMF with image.docx", loadOptions);
}
```

दस्तावेज़ लोडिंग के दौरान मेटाफ़ाइल्स (जैसे, WMF) को PNG छवियों में परिवर्तित करने के लिए, आप इसका उपयोग कर सकते हैं `setConvertMetafilesToPng(true)` तरीका।

## जावा के लिए Aspose.Words में लोड विकल्पों के साथ काम करने के लिए पूर्ण स्रोत कोड

```java
public void updateDirtyFields() throws Exception {
	LoadOptions loadOptions = new LoadOptions();
	{
		loadOptions.setUpdateDirtyFields(true);
	}
	Document doc = new Document("Your Directory Path" + "Dirty field.docx", loadOptions);
	doc.save("Your Directory Path" + "WorkingWithLoadOptions.UpdateDirtyFields.docx");
}
@Test
public void loadEncryptedDocument() throws Exception {
	Document doc = new Document("Your Directory Path" + "Encrypted.docx", new LoadOptions("docPassword"));
	doc.save("Your Directory Path" + "WorkingWithLoadOptions.LoadAndSaveEncryptedOdt.odt", new OdtSaveOptions("newPassword"));
}
@Test
public void convertShapeToOfficeMath() throws Exception {
	LoadOptions loadOptions = new LoadOptions();
	{
		loadOptions.setConvertShapeToOfficeMath(true);
	}
	Document doc = new Document("Your Directory Path" + "Office math.docx", loadOptions);
	doc.save("Your Directory Path" + "WorkingWithLoadOptions.ConvertShapeToOfficeMath.docx");
}
@Test
public void setMsWordVersion() throws Exception {
	// एक नया LoadOptions ऑब्जेक्ट बनाएं, जो डिफ़ॉल्ट रूप से MS Word 2019 विनिर्देश के अनुसार दस्तावेज़ लोड करेगा
	// और लोडिंग संस्करण को Microsoft Word 2010 में बदलें।
	LoadOptions loadOptions = new LoadOptions();
	{
		loadOptions.setMswVersion(MsWordVersion.WORD_2010);
	}
	Document doc = new Document("Your Directory Path" + "Document.docx", loadOptions);
	doc.save("Your Directory Path" + "WorkingWithLoadOptions.SetMsWordVersion.docx");
}
@Test
public void useTempFolder() throws Exception {
	LoadOptions loadOptions = new LoadOptions();
	{
		loadOptions.setTempFolder("Your Directory Path");
	}
	Document doc = new Document("Your Directory Path" + "Document.docx", loadOptions);
}
@Test
public void warningCallback() throws Exception {
	LoadOptions loadOptions = new LoadOptions();
	{
		loadOptions.setWarningCallback(new DocumentLoadingWarningCallback());
	}
	Document doc = new Document("Your Directory Path" + "Document.docx", loadOptions);
}
public static class DocumentLoadingWarningCallback implements IWarningCallback {
	public void warning(WarningInfo info) {
		// दस्तावेज़ लोड होने के दौरान आने वाली चेतावनियों और उनके विवरण को प्रिंट करता है।
		System.out.println(MessageFormat.format("WARNING: {0}, source: {1}", info.getWarningType(), info.getSource()));
		System.out.println(MessageFormat.format("\tDescription: {0}", info.getDescription()));
	}
}
@Test
public void convertMetafilesToPng() throws Exception {
	LoadOptions loadOptions = new LoadOptions();
	{
		loadOptions.setConvertMetafilesToPng(true);
	}
	Document doc = new Document("Your Directory Path" + "WMF with image.docx", loadOptions);
}
@Test
public void loadChm() throws Exception {
	LoadOptions loadOptions = new LoadOptions();
	{
		loadOptions.setEncoding(Charset.forName("windows-1251"));
	}
	Document doc = new Document("Your Directory Path" + "HTML help.chm", loadOptions);
}
```

## निष्कर्ष

इस ट्यूटोरियल में, हमने Aspose.Words for Java में लोड ऑप्शन के साथ काम करने के विभिन्न पहलुओं पर गहन चर्चा की है। लोड ऑप्शन दस्तावेज़ों को लोड करने और संसाधित करने के तरीके को अनुकूलित करने में महत्वपूर्ण भूमिका निभाते हैं, जिससे आप अपने दस्तावेज़ प्रसंस्करण को अपनी विशिष्ट आवश्यकताओं के अनुसार अनुकूलित कर सकते हैं। आइए इस गाइड में शामिल मुख्य बिंदुओं को फिर से देखें:

## अक्सर पूछे जाने वाले प्रश्न

### दस्तावेज़ लोड करते समय मैं चेतावनियों को कैसे संभाल सकता हूँ?

आप एक चेतावनी कॉलबैक सेट कर सकते हैं जैसा कि चित्र में दिखाया गया है `warningCallback()` उपरोक्त विधि का उपयोग करें। `DocumentLoadingWarningCallback` अपने एप्लिकेशन की आवश्यकताओं के अनुसार चेतावनियों को संभालने के लिए क्लास का उपयोग करें।

### क्या मैं दस्तावेज़ लोड करते समय आकृतियों को Office Math ऑब्जेक्ट में परिवर्तित कर सकता हूँ?

हां, आप इसका उपयोग करके आकृतियों को Office Math ऑब्जेक्ट में परिवर्तित कर सकते हैं `loadOptions.setConvertShapeToOfficeMath(true)`.

### मैं दस्तावेज़ लोड करने के लिए एमएस वर्ड संस्करण कैसे निर्दिष्ट करूं?

उपयोग `loadOptions.setMswVersion(MsWordVersion.WORD_2010)` दस्तावेज़ लोड करने के लिए एमएस वर्ड संस्करण निर्दिष्ट करने के लिए.

### इसका उद्देश्य क्या है? `setTempFolder` लोड विकल्प में विधि?

The `setTempFolder` विधि आपको उस फ़ोल्डर को निर्दिष्ट करने की अनुमति देती है जहां दस्तावेज़ प्रसंस्करण के दौरान अस्थायी फ़ाइलें संग्रहीत की जाती हैं।


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}