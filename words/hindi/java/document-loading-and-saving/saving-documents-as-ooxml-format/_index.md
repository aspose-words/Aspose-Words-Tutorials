---
title: Java के लिए Aspose.Words में OOXML प्रारूप में दस्तावेज़ों को सहेजना
linktitle: दस्तावेज़ों को OOXML प्रारूप में सहेजना
second_title: Aspose.Words जावा दस्तावेज़ प्रसंस्करण एपीआई
description: Java के लिए Aspose.Words के साथ OOXML फ़ॉर्मेट में दस्तावेज़ों को सहेजना सीखें। अपनी फ़ाइलों को सुरक्षित, अनुकूलित और आसानी से कस्टमाइज़ करें।
weight: 20
url: /hi/java/document-loading-and-saving/saving-documents-as-ooxml-format/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Java के लिए Aspose.Words में OOXML प्रारूप में दस्तावेज़ों को सहेजना


## Java के लिए Aspose.Words में OOXML प्रारूप में दस्तावेज़ों को सहेजने का परिचय

इस गाइड में, हम जावा के लिए Aspose.Words का उपयोग करके OOXML प्रारूप में दस्तावेज़ों को सहेजने का तरीका जानेंगे। OOXML (ऑफिस ओपन XML) एक फ़ाइल प्रारूप है जिसका उपयोग Microsoft Word और अन्य कार्यालय अनुप्रयोगों द्वारा किया जाता है। हम OOXML प्रारूप में दस्तावेज़ों को सहेजने के लिए विभिन्न विकल्पों और सेटिंग्स को कवर करेंगे।

## आवश्यक शर्तें

आरंभ करने से पहले, सुनिश्चित करें कि आपके प्रोजेक्ट में Aspose.Words for Java लाइब्रेरी स्थापित है।

## पासवर्ड एन्क्रिप्शन के साथ दस्तावेज़ सहेजना

आप अपने दस्तावेज़ को OOXML फ़ॉर्मेट में सहेजते समय पासवर्ड से एन्क्रिप्ट कर सकते हैं। आप यह कैसे कर सकते हैं, यहाँ बताया गया है:

```java
import com.aspose.words.Document;
import com.aspose.words.OoxmlSaveOptions;

// दस्तावेज़ लोड करें
Document doc = new Document("Document.docx");

// OoxmlSaveOptions बनाएं और पासवर्ड सेट करें
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions();
saveOptions.setPassword("password");

// दस्तावेज़ को एन्क्रिप्शन के साथ सहेजें
doc.save("EncryptedDoc.docx", saveOptions);
```

## OOXML अनुपालन सेट करना

आप दस्तावेज़ को सहेजते समय OOXML अनुपालन स्तर निर्दिष्ट कर सकते हैं। उदाहरण के लिए, आप इसे ISO 29500:2008 (सख्त) पर सेट कर सकते हैं। यहाँ बताया गया है कि कैसे:

```java
import com.aspose.words.Document;
import com.aspose.words.OoxmlSaveOptions;
import com.aspose.words.MsWordVersion;
import com.aspose.words.OoxmlCompliance;

// दस्तावेज़ लोड करें
Document doc = new Document("Document.docx");

// Word 2016 के लिए अनुकूलित करें
doc.getCompatibilityOptions().optimizeFor(MsWordVersion.WORD_2016);

// OoxmlSaveOptions बनाएं और अनुपालन स्तर निर्धारित करें
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions();
saveOptions.setCompliance(OoxmlCompliance.ISO_29500_2008_STRICT);

// अनुपालन सेटिंग के साथ दस्तावेज़ सहेजें
doc.save("ComplianceDoc.docx", saveOptions);
```

## अंतिम सहेजे गए समय की संपत्ति को अद्यतन करना

आप दस्तावेज़ को सहेजते समय उसके "अंतिम सहेजे गए समय" गुण को अपडेट करना चुन सकते हैं। यहाँ बताया गया है कि कैसे:

```java
import com.aspose.words.Document;
import com.aspose.words.OoxmlSaveOptions;

// दस्तावेज़ लोड करें
Document doc = new Document("Document.docx");

// OoxmlSaveOptions बनाएं और अंतिम सहेजे गए समय गुण को अद्यतन करने में सक्षम करें
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions();
saveOptions.setUpdateLastSavedTimeProperty(true);

// दस्तावेज़ को अपडेट की गई प्रॉपर्टी के साथ सहेजें
doc.save("UpdatedLastSavedTime.docx", saveOptions);
```

## विरासत नियंत्रण वर्णों को बनाए रखना

यदि आपके दस्तावेज़ में लीगेसी नियंत्रण वर्ण हैं, तो आप उन्हें सहेजते समय रखना चुन सकते हैं। यहाँ बताया गया है कि कैसे:

```java
import com.aspose.words.Document;
import com.aspose.words.OoxmlSaveOptions;
import com.aspose.words.SaveFormat;

//विरासत नियंत्रण वर्णों के साथ दस्तावेज़ लोड करें
Document doc = new Document("LegacyControlChars.doc");

// FLAT_OPC प्रारूप के साथ OoxmlSaveOptions बनाएं और विरासत नियंत्रण वर्णों को रखने में सक्षम करें
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions();
saveOptions.setKeepLegacyControlChars(true);

// दस्तावेज़ को लीगेसी नियंत्रण वर्णों के साथ सहेजें
doc.save("LegacyControlCharsPreserved.docx", saveOptions);
```

## संपीड़न स्तर सेट करना

आप दस्तावेज़ को सहेजते समय संपीड़न स्तर को समायोजित कर सकते हैं। उदाहरण के लिए, आप इसे न्यूनतम संपीड़न के लिए SUPER_FAST पर सेट कर सकते हैं। यहाँ बताया गया है कि कैसे:

```java
import com.aspose.words.Document;
import com.aspose.words.OoxmlSaveOptions;
import com.aspose.words.CompressionLevel;

// दस्तावेज़ लोड करें
Document doc = new Document("Document.docx");

// OoxmlSaveOptions बनाएं और संपीड़न स्तर सेट करें
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions();
saveOptions.setCompressionLevel(CompressionLevel.SUPER_FAST);

// दस्तावेज़ को निर्दिष्ट संपीड़न स्तर के साथ सहेजें
doc.save("FastCompressionDoc.docx", saveOptions);
```

ये कुछ मुख्य विकल्प और सेटिंग्स हैं जिनका उपयोग आप Aspose.Words for Java का उपयोग करके OOXML प्रारूप में दस्तावेज़ सहेजते समय कर सकते हैं। अधिक विकल्पों का पता लगाने और आवश्यकतानुसार अपने दस्तावेज़-सहेजने की प्रक्रिया को अनुकूलित करने के लिए स्वतंत्र महसूस करें।

## जावा के लिए Aspose.Words में OOXML प्रारूप के रूप में दस्तावेज़ों को सहेजने के लिए पूर्ण स्रोत कोड

```java
public void encryptDocxWithPassword() throws Exception
{
	Document doc = new Document("Your Directory Path" + "Document.docx");
	OoxmlSaveOptions saveOptions = new OoxmlSaveOptions(); { saveOptions.setPassword("password"); }
	doc.save("Your Directory Path" + "WorkingWithOoxmlSaveOptions.EncryptDocxWithPassword.docx", saveOptions);
}
@Test
public void ooxmlComplianceIso29500_2008_Strict() throws Exception
{
	Document doc = new Document("Your Directory Path" + "Document.docx");
	doc.getCompatibilityOptions().optimizeFor(MsWordVersion.WORD_2016);
	OoxmlSaveOptions saveOptions = new OoxmlSaveOptions(); { saveOptions.setCompliance(OoxmlCompliance.ISO_29500_2008_STRICT); }
	doc.save("Your Directory Path" + "WorkingWithOoxmlSaveOptions.OoxmlComplianceIso29500_2008_Strict.docx", saveOptions);
}
@Test
public void updateLastSavedTimeProperty() throws Exception
{
	Document doc = new Document("Your Directory Path" + "Document.docx");
	OoxmlSaveOptions saveOptions = new OoxmlSaveOptions(); { saveOptions.setUpdateLastSavedTimeProperty(true); }
	doc.save("Your Directory Path" + "WorkingWithOoxmlSaveOptions.UpdateLastSavedTimeProperty.docx", saveOptions);
}
@Test
public void keepLegacyControlChars() throws Exception
{
	Document doc = new Document("Your Directory Path" + "Legacy control character.doc");
	OoxmlSaveOptions saveOptions = new OoxmlSaveOptions(); { saveOptions.setKeepLegacyControlChars(true); }
	doc.save("Your Directory Path" + "WorkingWithOoxmlSaveOptions.KeepLegacyControlChars.docx", saveOptions);
}
@Test
public void setCompressionLevel() throws Exception
{
	Document doc = new Document("Your Directory Path" + "Document.docx");
	OoxmlSaveOptions saveOptions = new OoxmlSaveOptions(); { saveOptions.setCompressionLevel(CompressionLevel.SUPER_FAST); }
	doc.save("Your Directory Path" + "WorkingWithOoxmlSaveOptions.SetCompressionLevel.docx", saveOptions);
}
```

## निष्कर्ष

इस व्यापक गाइड में, हमने जावा के लिए Aspose.Words का उपयोग करके OOXML प्रारूप में दस्तावेज़ों को सहेजने का तरीका खोजा है। चाहे आपको अपने दस्तावेज़ों को पासवर्ड से एन्क्रिप्ट करना हो, विशिष्ट OOXML मानकों के अनुपालन को सुनिश्चित करना हो, दस्तावेज़ गुणों को अपडेट करना हो, विरासत नियंत्रण वर्णों को संरक्षित करना हो, या संपीड़न स्तरों को समायोजित करना हो, Aspose.Words आपकी आवश्यकताओं को पूरा करने के लिए उपकरणों का एक बहुमुखी सेट प्रदान करता है।

## अक्सर पूछे जाने वाले प्रश्न

### मैं पासवर्ड-संरक्षित दस्तावेज़ से पासवर्ड सुरक्षा कैसे हटाऊं?

पासवर्ड-संरक्षित दस्तावेज़ से पासवर्ड सुरक्षा हटाने के लिए, आप दस्तावेज़ को सही पासवर्ड के साथ खोल सकते हैं और फिर उसे सेव विकल्पों में पासवर्ड निर्दिष्ट किए बिना सेव कर सकते हैं। इससे दस्तावेज़ बिना पासवर्ड सुरक्षा के सेव हो जाएगा।

### क्या मैं किसी दस्तावेज़ को OOXML प्रारूप में सहेजते समय कस्टम गुण सेट कर सकता हूँ?

 हां, आप किसी दस्तावेज़ को OOXML फ़ॉर्मेट में सहेजने से पहले उसके लिए कस्टम गुण सेट कर सकते हैं।`BuiltInDocumentProperties` और`CustomDocumentProperties` विभिन्न गुण जैसे लेखक, शीर्षक, कीवर्ड और कस्टम गुण सेट करने के लिए कक्षाएं।

### किसी दस्तावेज़ को OOXML प्रारूप में सहेजते समय डिफ़ॉल्ट संपीड़न स्तर क्या है?

 Aspose.Words for Java का उपयोग करके OOXML प्रारूप में दस्तावेज़ सहेजते समय डिफ़ॉल्ट संपीड़न स्तर है`NORMAL` . आप संपीड़न स्तर को बदल सकते हैं`SUPER_FAST` या`MAXIMUM` जरुरत के अनुसार।
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
