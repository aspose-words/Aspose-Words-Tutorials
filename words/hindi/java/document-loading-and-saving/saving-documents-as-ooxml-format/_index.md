---
date: 2025-12-29
description: Aspose.Words for Java के सहेजने विकल्पों का उपयोग करके पासवर्ड के साथ
  docx को एन्क्रिप्ट करना सीखें। अपने OOXML फ़ाइलों को आसानी से सुरक्षित, अनुकूलित
  और कस्टमाइज़ करें।
linktitle: Saving Documents as OOXML Format
second_title: Aspose.Words Java Document Processing API
title: Aspose.Words for Java का उपयोग करके पासवर्ड के साथ DOCX को एन्क्रिप्ट कैसे
  करें
url: /hi/java/document-loading-and-saving/saving-documents-as-ooxml-format/
weight: 20
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for Java का उपयोग करके पासवर्ड के साथ DOCX को एन्क्रिप्ट कैसे करें

इस गाइड में आप **DOCX को पासवर्ड से एन्क्रिप्ट करने** का तरीका जानेंगे, जबकि दस्तावेज़ों को OOXML फ़ॉर्मेट में Aspose.Words for Java का उपयोग करके सहेजा जाता है। चाहे आप गोपनीय रिपोर्ट की सुरक्षा करना चाहते हों या अनुबंध ड्राफ्ट को सुरक्षित रखना चाहते हों, नीचे दिए गए चरण आपको पासवर्ड प्रोटेक्शन लागू करने और अन्य OOXML सहेजने विकल्पों को सूक्ष्म‑तरीके से समायोजित करने का पूरा तरीका दिखाते हैं।

## त्वरित उत्तर
- **क्या मैं DOCX फ़ाइल को पासवर्ड से एन्क्रिप्ट कर सकता हूँ?** हाँ, सहेजने से पहले `OoxmlSaveOptions.setPassword()` का उपयोग करें।  
- **कौन सा क्लास OOXML सहेजने की सेटिंग्स को नियंत्रित करता है?** `OoxmlSaveOptions` (Aspose.Words का हिस्सा)।  
- **क्या पासवर्ड प्रोटेक्शन के लिए लाइसेंस की आवश्यकता है?** प्रोडक्शन उपयोग के लिए एक वैध Aspose.Words लाइसेंस आवश्यक है।  
- **क्या मैं एन्क्रिप्शन को कंप्लायंस सेटिंग्स के साथ संयोजित कर सकता हूँ?** बिल्कुल – उसी `OoxmlSaveOptions` इंस्टेंस पर `setPassword` और `setCompliance` दोनों सेट करें।  
- **कौन‑से कॉम्प्रेशन लेवल उपलब्ध हैं?** `NORMAL`, `SUPER_FAST`, और `MAXIMUM` `CompressionLevel` के माध्यम से।

## “encrypt docx with password” क्या है?
DOCX फ़ाइल को एन्क्रिप्ट करना मतलब है कि फ़ाइल की सामग्री एन्क्रिप्टेड रूप में संग्रहीत होती है और केवल सही पासवर्ड प्रदान करने पर ही खोली जा सकती है। यह संवेदनशील जानकारी को अनधिकृत पहुँच से बचाता है, जबकि पासवर्ड देने के बाद मानक Word टूल्स से फ़ाइल को खोलना संभव रहता है।

## एन्क्रिप्शन के लिए Aspose.Words सहेजने विकल्पों का उपयोग क्यों करें?
Aspose.Words एक समृद्ध **aspose words save options** सेट प्रदान करता है जो न केवल एन्क्रिप्शन, बल्कि कंप्लायंस लेवल, कॉम्प्रेशन, और लेगेसी कैरेक्टर हैंडलिंग को भी Java कोड से नियंत्रित करता है। इससे मैन्युअल पोस्ट‑प्रोसेसिंग या थर्ड‑पार्टी टूल्स की आवश्यकता समाप्त हो जाती है।

## पूर्वापेक्षाएँ
- Java Development Kit (JDK 8 या उससे ऊपर)  
- आपके प्रोजेक्ट में Aspose.Words for Java लाइब्रेरी (Maven/Gradle या JAR) जोड़ी गई हो  
- प्रोडक्शन के लिए वैध Aspose.Words लाइसेंस (इवैल्यूएशन के लिए वैकल्पिक)

## पासवर्ड एन्क्रिप्शन के साथ दस्तावेज़ सहेजना

आप OOXML फ़ॉर्मेट में सहेजते समय अपने दस्तावेज़ को पासवर्ड से एन्क्रिप्ट कर सकते हैं। नीचे इसका तरीका दिया गया है:

```java
import com.aspose.words.Document;
import com.aspose.words.OoxmlSaveOptions;

// Load the document
Document doc = new Document("Document.docx");

// Create OoxmlSaveOptions and set the password
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions();
saveOptions.setPassword("password");

// Save the document with encryption
doc.save("EncryptedDoc.docx", saveOptions);
```

## OOXML कंप्लायंस सेट करना

दस्तावेज़ सहेजते समय आप OOXML कंप्लायंस लेवल निर्दिष्ट कर सकते हैं। उदाहरण के तौर पर, इसे ISO 29500:2008 (Strict) पर सेट किया जा सकता है। तरीका इस प्रकार है:

```java
import com.aspose.words.Document;
import com.aspose.words.OoxmlSaveOptions;
import com.aspose.words.MsWordVersion;
import com.aspose.words.OoxmlCompliance;

// Load the document
Document doc = new Document("Document.docx");

// Optimize for Word 2016
doc.getCompatibilityOptions().optimizeFor(MsWordVersion.WORD_2016);

// Create OoxmlSaveOptions and set the compliance level
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions();
saveOptions.setCompliance(OoxmlCompliance.ISO_29500_2008_STRICT);

// Save the document with compliance setting
doc.save("ComplianceDoc.docx", saveOptions);
```

## “Last Saved Time” प्रॉपर्टी अपडेट करना

सहेजते समय आप दस्तावेज़ की “Last Saved Time” प्रॉपर्टी को अपडेट करने का विकल्प चुन सकते हैं। तरीका इस प्रकार है:

```java
import com.aspose.words.Document;
import com.aspose.words.OoxmlSaveOptions;

// Load the document
Document doc = new Document("Document.docx");

// Create OoxmlSaveOptions and enable updating the Last Saved Time property
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions();
saveOptions.setUpdateLastSavedTimeProperty(true);

// Save the document with the updated property
doc.save("UpdatedLastSavedTime.docx", saveOptions);
```

## लेगेसी कंट्रोल कैरेक्टर्स को बनाए रखना

यदि आपके दस्तावेज़ में लेगेसी कंट्रोल कैरेक्टर्स हैं, तो आप सहेजते समय उन्हें बनाए रखने का विकल्प चुन सकते हैं। तरीका इस प्रकार है:

```java
import com.aspose.words.Document;
import com.aspose.words.OoxmlSaveOptions;
import com.aspose.words.SaveFormat;

// Load a document with legacy control characters
Document doc = new Document("LegacyControlChars.doc");

// Create OoxmlSaveOptions with the FLAT_OPC format and enable keeping legacy control characters
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions();
saveOptions.setKeepLegacyControlChars(true);

// Save the document with legacy control characters
doc.save("LegacyControlCharsPreserved.docx", saveOptions);
```

## कॉम्प्रेशन लेवल सेट करना

दस्तावेज़ सहेजते समय आप कॉम्प्रेशन लेवल को समायोजित कर सकते हैं। उदाहरण के लिए, न्यूनतम कॉम्प्रेशन के लिए **SUPER_FAST** सेट किया जा सकता है। तरीका इस प्रकार है:

```java
import com.aspose.words.Document;
import com.aspose.words.OoxmlSaveOptions;
import com.aspose.words.CompressionLevel;

// Load the document
Document doc = new Document("Document.docx");

// Create OoxmlSaveOptions and set the compression level
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions();
saveOptions.setCompressionLevel(CompressionLevel.SUPER_FAST);

// Save the document with the specified compression level
doc.save("FastCompressionDoc.docx", saveOptions);
```

ये कुछ मुख्य विकल्प और सेटिंग्स हैं जिन्हें आप Aspose.Words for Java का उपयोग करके OOXML फ़ॉर्मेट में दस्तावेज़ सहेजते समय उपयोग कर सकते हैं। अधिक विकल्पों का अन्वेषण करें और अपनी आवश्यकता अनुसार दस्तावेज़‑सहेजने की प्रक्रिया को कस्टमाइज़ करें।

## OOXML फ़ॉर्मेट में दस्तावेज़ सहेजने के लिए पूर्ण स्रोत कोड (Aspose.Words for Java)

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

इस व्यापक गाइड में हमने **DOCX को पासवर्ड से एन्क्रिप्ट** करने और Aspose.Words for Java के माध्यम से विभिन्न OOXML सहेजने विकल्पों को सूक्ष्म‑तरीके से ट्यून करने का तरीका खोजा। चाहे आपको गोपनीय सामग्री की सुरक्षा करनी हो, कड़ी ISO कंप्लायंस पूरी करनी हो, लेगेसी कैरेक्टर्स को संरक्षित रखना हो, या कॉम्प्रेशन को नियंत्रित करना हो, लाइब्रेरी एक ही `OoxmlSaveOptions` API के माध्यम से विस्तृत नियंत्रण प्रदान करती है।

## अक्सर पूछे जाने वाले प्रश्न

**प्रश्न: पासवर्ड‑सुरक्षित दस्तावेज़ से पासवर्ड प्रोटेक्शन कैसे हटाएँ?**  
उत्तर: सही पासवर्ड के साथ दस्तावेज़ खोलें, फिर `setPassword` को कॉल किए बिना फिर से सहेजें। नई फ़ाइल अब अनप्रोटेक्टेड होगी।

**प्रश्न: OOXML फ़ॉर्मेट में दस्तावेज़ सहेजते समय कस्टम प्रॉपर्टीज़ सेट कर सकता हूँ?**  
उत्तर: हाँ। `Document` ऑब्जेक्ट पर `BuiltInDocumentProperties` या `CustomDocumentProperties` का उपयोग करके `save` कॉल करने से पहले सेट करें।

**प्रश्न: OOXML फ़ॉर्मेट में दस्तावेज़ सहेजते समय डिफ़ॉल्ट कॉम्प्रेशन लेवल क्या है?**  
उत्तर: डिफ़ॉल्ट `NORMAL` है। गति के लिए `SUPER_FAST` या छोटे फ़ाइल आकार के लिए `MAXIMUM` चुन सकते हैं।

**प्रश्न: क्या aspose words save options पुराने Word संस्करणों के साथ काम करते हैं?**  
उत्तर: हाँ। `MsWordVersion` और कंप्लायंस सेटिंग्स को समायोजित करके आप Word 2007‑2019 को टार्गेट कर सकते हैं और संगतता सुनिश्चित कर सकते हैं।

**प्रश्न: क्या एक ही ऑपरेशन में कई सहेजने विकल्पों को संयोजित किया जा सकता है?**  
उत्तर: बिल्कुल। एक `OoxmlSaveOptions` इंस्टेंस बनाएं, सभी वांछित प्रॉपर्टीज़ (पासवर्ड, कंप्लायंस, कॉम्प्रेशन आदि) सेट करें, और उसे `doc.save()` में पास करें।

---

**अंतिम अपडेट:** 2025-12-29  
**परीक्षित संस्करण:** Aspose.Words for Java 24.12  
**लेखक:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}