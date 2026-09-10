---
date: 2025-12-27
description: Aspose.Words for Java में LoadOptions कैसे सेट करें, जिसमें टेम्प फ़ोल्डर
  निर्दिष्ट करना, वर्ड संस्करण सेट करना, मेटाफाइल्स को PNG में बदलना, और लचीले दस्तावेज़
  प्रोसेसिंग के लिए शैप को गणित में बदलना शामिल है।
linktitle: Using Load Options
second_title: Aspose.Words Java Document Processing API
title: Aspose.Words for Java में LoadOptions कैसे सेट करें
url: /hi/java/document-loading-and-saving/using-load-options/
weight: 11
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for Java में LoadOptions कैसे सेट करें

इस ट्यूटोरियल में हम वास्तविक‑दुनिया के विभिन्न परिदृश्यों के लिए **LoadOptions कैसे सेट करें** इस पर चरण‑दर‑चरण चर्चा करेंगे। LoadOptions आपको दस्तावेज़ खोलने के तरीके पर सूक्ष्म नियंत्रण प्रदान करते हैं—चाहे आपको गंदे फ़ील्ड्स को अपडेट करना हो, एन्क्रिप्टेड फ़ाइलों के साथ काम करना हो, शैप्स को Office Math में बदलना हो, या लाइब्रेरी को अस्थायी डेटा कहाँ स्टोर करना है बताना हो। अंत तक आप अपने एप्लिकेशन की सटीक आवश्यकताओं के अनुसार लोडिंग व्यवहार को अनुकूलित कर पाएँगे।

## त्वरित उत्तर
- **LoadOptions क्या है?** वह कॉन्फ़िगरेशन ऑब्जेक्ट जो निर्धारित करता है कि Aspose.Words दस्तावेज़ को कैसे लोड करता है।  
- **क्या मैं लोडिंग के दौरान फ़ील्ड्स को अपडेट कर सकता हूँ?** हाँ—`setUpdateDirtyFields(true)` सेट करें।  
- **पासवर्ड‑सुरक्षित फ़ाइल को कैसे खोलें?** पासवर्ड को `LoadOptions` कंस्ट्रक्टर में पास करें।  
- **क्या अस्थायी फ़ोल्डर बदलना संभव है?** `setTempFolder("path")` उपयोग करें।  
- **कौन सा मेथड शैप्स को Office Math में बदलता है?** `setConvertShapeToOfficeMath(true)`।

## LoadOptions क्यों उपयोग करें?
LoadOptions आपको पोस्ट‑लोड प्रोसेसिंग चरणों से बचने, मेमोरी उपयोग कम करने, और यह सुनिश्चित करने में मदद करते हैं कि दस्तावेज़ ठीक उसी तरह व्याख्यायित हो जैसा आपको चाहिए। उदाहरण के लिए, लोड के दौरान मेटा‑फ़ाइल्स को PNG में बदलना बाद में रास्टराइज़ेशन समस्याओं को रोकता है, और MS Word संस्करण निर्दिष्ट करने से लेगेसी फ़ाइलों के साथ लेआउट फ़िडेलिटी बनी रहती है।

## पूर्वापेक्षाएँ
- Java 17 या बाद का संस्करण  
- Aspose.Words for Java (नवीनतम संस्करण)  
- प्रोडक्शन उपयोग के लिए वैध Aspose लाइसेंस  

## चरण‑दर‑चरण गाइड

### गंदे फ़ील्ड्स अपडेट करें

जब दस्तावेज़ में ऐसे फ़ील्ड्स हों जो संपादित किए गए हों लेकिन रिफ्रेश नहीं हुए हों, तो आप लोड के दौरान Aspose.Words को स्वचालित रूप से उन्हें अपडेट करने के लिए कह सकते हैं।

```java
LoadOptions loadOptions = new LoadOptions();
loadOptions.setUpdateDirtyFields(true);

Document doc = new Document("Your Directory Path" + "Dirty field.docx", loadOptions);
doc.save("Your Directory Path" + "WorkingWithLoadOptions.UpdateDirtyFields.docx");
```

*`setUpdateDirtyFields(true)` कॉल यह सुनिश्चित करता है कि कोई भी गंदा फ़ील्ड दस्तावेज़ खुलते ही पुनः गणना हो जाए।*

### एन्क्रिप्टेड दस्तावेज़ लोड करें

यदि आपका स्रोत फ़ाइल पासवर्ड‑सुरक्षित है, तो `LoadOptions` इंस्टेंस बनाते समय पासवर्ड प्रदान करें। आप अलग फ़ॉर्मेट में सहेजते समय नया पासव सेट कर सकते हैं।

```java
@Test
public void loadEncryptedDocument() throws Exception {
    Document doc = new Document("Your Directory Path" + "Encrypted.docx", new LoadOptions("docPassword"));
    doc.save("Your Directory Path" + "WorkingWithLoadOptions.LoadAndSaveEncryptedOdt.odt", new OdtSaveOptions("newPassword"));
}
```

### शैप को Office Math में बदलें

कुछ लेगेसी दस्तावेज़ समीकरणों को ड्रॉइंग शैप्स के रूप में स्टोर करते हैं। इस विकल्प को सक्षम करने से वे शैप्स मूल Office Math ऑब्जेक्ट्स में बदल जाते हैं, जिन्हें बाद में संपादित करना आसान होता है।

```java
LoadOptions loadOptions = new LoadOptions();
loadOptions.setConvertShapeToOfficeMath(true);

Document doc = new Document("Your Directory Path" + "Office math.docx", loadOptions);
doc.save("Your Directory Path" + "WorkingWithLoadOptions.ConvertShapeToOfficeMath.docx");
```

### MS Word संस्करण सेट करें

लक्ष्य Word संस्करण निर्दिष्ट करने से लाइब्रेरी को सही रेंडरिंग नियम चुनने में मदद मिलती है, विशेषकर पुराने फ़ाइल फ़ॉर्मेट्स के साथ काम करते समय।

```java
@Test
public void setMsWordVersion() throws Exception {
    LoadOptions loadOptions = new LoadOptions();
    loadOptions.setMswVersion(MsWordVersion.WORD_2010);

    Document doc = new Document("Your Directory Path" + "Document.docx", loadOptions);
    doc.save("Your Directory Path" + "WorkingWithLoadOptions.SetMsWordVersion.docx");
}
```

### अस्थायी फ़ोल्डर उपयोग करें

बड़े दस्तावेज़ इमेज़ निकालने जैसी प्रक्रियाओं के दौरान अस्थायी फ़ाइलें बना सकते हैं। आप इन फ़ाइलों को अपनी पसंद के फ़ोल्डर में निर्देशित कर सकते हैं, जो सैंडबॉक्सेड वातावरण में उपयोगी है।

```java
@Test
public void useTempFolder() throws Exception {
    LoadOptions loadOptions = new LoadOptions();
    loadOptions.setTempFolder("Your Directory Path");

    Document doc = new Document("Your Directory Path" + "Document.docx", loadOptions);
}
```

### चेतावनी कॉलबैक

लोडिंग के दौरान Aspose.Words चेतावनियाँ (जैसे असमर्थित फीचर) उत्पन्न कर सकता है। एक कॉलबैक लागू करने से आप इन घटनाओं को लॉग या प्रतिक्रिया दे सकते हैं।

```java
@Test
public void warningCallback() throws Exception {
    LoadOptions loadOptions = new LoadOptions();
    loadOptions.setWarningCallback(new DocumentLoadingWarningCallback());

    Document doc = new Document("Your Directory Path" + "Document.docx", loadOptions);
}

public static class DocumentLoadingWarningCallback implements IWarningCallback {
    public void warning(WarningInfo info) {
        // Handle warnings as they arise during document loading.
        System.out.println(MessageFormat.format("WARNING: {0}, source: {1}", info.getWarningType(), info.getSource()));
        System.out.println(MessageFormat.format("\tDescription: {0}", info.getDescription()));
    }
}
```

### मेटा‑फ़ाइल्स को PNG में बदलें

WMF जैसी मेटा‑फ़ाइल्स को लोड के दौरान PNG में रास्टराइज़ किया जा सकता है, जिससे विभिन्न प्लेटफ़ॉर्म पर रेंडरिंग सुसंगत रहती है।

```java
@Test
public void convertMetafilesToPng() throws Exception {
    LoadOptions loadOptions = new LoadOptions();
    loadOptions.setConvertMetafilesToPng(true);

    Document doc = new Document("Your Directory Path" + "WMF with image.docx", loadOptions);
}
```

## Aspose.Words for Java में Load Options के साथ काम करने के लिए पूर्ण स्रोत कोड

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
	// Create a new LoadOptions object, which will load documents according to MS Word 2019 specification by default
	// and change the loading version to Microsoft Word 2010.
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
		// Prints warnings and their details as they arise during document loading.
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

## सामान्य उपयोग केस और टिप्स

- **बैच कन्वर्ज़न पाइपलाइन** – `setTempFolder` को शेड्यूल्ड जॉब के साथ मिलाकर सैकड़ों फ़ाइलों को प्रोसेस करें बिना सिस्टम टेम्प डायरेक्टरी भरें।  
- **लेगेसी दस्तावेज़ माइग्रेशन** – `setMswVersion` को `setConvertShapeToOfficeMath` के साथ उपयोग करके पुराने इंजीनियरिंग दस्तावेज़ों को आधुनिक फ़ॉर्मेट में लाएँ और समीकरणों को संरक्षित रखें।  
- **सुरक्षित दस्तावेज़ हैंडलिंग** – `loadEncryptedDocument` को `OdtSaveOptions` के साथ जोड़कर फ़ाइलों को नए पासवर्ड के साथ पुनः‑एन्क्रिप्ट करें और अलग फ़ॉर्मेट में सहेजें।  

## अक्सर पूछे जाने वाले प्रश्न

**प्रश्न: दस्तावेज़ लोडिंग के दौरान चेतावनियों को कैसे संभालें?**  
उत्तर: एक कस्टम `IWarningCallback` लागू करें (जैसा कि *चेतावनी कॉलबैक* उदाहरण में दिखाया गया है) और इसे `loadOptions.setWarningCallback(...)` के माध्यम से रजिस्टर करें। यह आपको चेतावनी की गंभीरता के आधार पर लॉग, अनदेखा या एबॉर्ट करने की अनुमति देता है।

**प्रश्न: क्या लोडिंग के दौरान शैप्स को Office Math ऑब्जेक्ट्स में बदल सकता हूँ?**  
उत्तर: हाँ—`Document` बनाने से पहले `loadOptions.setConvertShapeToOfficeMath(true)` कॉल करें। लाइब्रेरी स्वचालित रूप से संगत शैप्स को मूल Office Math ऑब्जेक्ट्स में बदल देगी।

**प्रश्न: दस्तावेज़ लोडिंग के लिए MS Word संस्करण कैसे निर्दिष्ट करें?**  
उत्तर: `loadOptions.setMswVersion(MsWordVersion.WORD_2010)` (या कोई अन्य enum मान) उपयोग करके Aspose.Words को बताएं कि किस Word संस्करण के रेंडरिंग नियम लागू करने हैं।

**प्रश्न: LoadOptions में `setTempFolder` मेथड का उद्देश्य क्या है?**  
उत्तर: यह लोडिंग के दौरान उत्पन्न सभी अस्थायी फ़ाइलों (जैसे निकाली गई इमेज़) को आपके द्वारा नियंत्रित फ़ोल्डर की ओर निर्देशित करता है, जो सीमित सिस्टम टेम्प डायरेक्टरी वाले वातावरण में आवश्यक है।

**प्रश्न: क्या लोड के दौरान WMF जैसी मेटा‑फ़ाइल्स को PNG में बदलना संभव है?**  
उत्तर: बिल्कुल—`loadOptions.setConvertMetafilesToPng(true)` सक्षम करें। इससे रास्टर इमेज़ PNG के रूप में संग्रहीत होते हैं, जिससे आधुनिक व्यूअर्स के साथ संगतता बेहतर होती है।

## निष्कर्ष

हमने Aspose.Words for Java में **LoadOptions कैसे सेट करें** की आवश्यक तकनीकों को कवर किया—गंदे फ़ील्ड्स अपडेट करने से लेकर एन्क्रिप्टेड फ़ाइलों को संभालने, शैप्स को बदलने, Word संस्करण निर्दिष्ट करने, अस्थायी स्टोरेज निर्देशित करने और अधिक। इन विकल्पों का उपयोग करके आप मजबूत, उच्च‑प्रदर्शन दस्तावेज़ प्रोसेसिंग पाइपलाइन बना सकते हैं जो विभिन्न इनपुट परिदृश्यों के अनुरूप हों।

---

**अंतिम अपडेट:** 2025-12-27  
**परीक्षित संस्करण:** Aspose.Words for Java 24.11  
**लेखक:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}