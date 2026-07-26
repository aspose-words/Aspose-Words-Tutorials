---
category: general
date: 2026-07-26
description: Aspose.Words का उपयोग करके Word दस्तावेज़ में ActiveX बटन कैसे डालें
  – कुछ ही पंक्तियों में बटन का कैप्शन, स्थिति और आकार सेट करना सीखें।
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to insert activex
- set button caption
language: hi
lastmod: 2026-07-26
og_description: Aspose.Words के साथ Word दस्तावेज़ में ActiveX बटन कैसे डालें। बटन
  का कैप्शन, स्थिति और आकार सेट करने के लिए इस चरण‑दर‑चरण ट्यूटोरियल का पालन करें।
og_image_alt: Screenshot of a Word document showing an inserted ActiveX CommandButton
  with a custom caption
og_title: वर्ड में ActiveX बटन कैसे डालें – त्वरित गाइड
schemas:
- author: Aspose
  dateModified: '2026-07-26'
  description: How to insert ActiveX button in a Word document using Aspose.Words
    – learn to set button caption, position, and size in just a few lines.
  headline: How to Insert ActiveX Button in Word – Set Button Caption
  type: TechArticle
tags:
- Aspose.Words
- Java
- ActiveX
- Word automation
- Document generation
title: Word में ActiveX बटन कैसे डालें – बटन कैप्शन सेट करें
url: /hi/java/using-document-elements/how-to-insert-activex-button-in-word-set-button-caption/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word में ActiveX बटन कैसे डालें – बटन कैप्शन सेट करें

क्या आपने कभी **how to insert ActiveX** कंट्रोल्स को Word फ़ाइल में UI खोले बिना डालने के बारे में सोचा है? आप अकेले नहीं हैं। कई एंटरप्राइज़ एप्लिकेशन्स में आपको एक क्लिक करने योग्य बटन चाहिए जो मैक्रो चलाए, और इसे प्रोग्रामेटिकली करने से कई घंटे बचते हैं। यह गाइड आपको बिल्कुल दिखाता है कि Aspose.Words for Java का उपयोग करके **how to insert ActiveX** CommandButton कैसे डालें, और—हाँ—**set button caption** कैसे सेट करें ताकि उपयोगकर्ता को पता चले कि क्या क्लिक करना है।

हम पूरी प्रक्रिया को चरण दर चरण देखेंगे: लाइब्रेरी सेटअप करने से, नया दस्तावेज़ बनाने, बटन डालने, उसके आकार और स्थान को समायोजित करने, एक उपयोगी कैप्शन देने, और अंत में फ़ाइल को सहेजने तक। अंत तक आपके पास एक चलाने योग्य `.docx` होगा जो Word में खुलेगा और उसमें एक पूरी तरह कार्यशील ActiveX बटन होगा जो आपके मैक्रो को ट्रिगर करने के लिए तैयार है।

---

## आप क्या सीखेंगे

- Java प्रोजेक्ट में Aspose.Words को इंस्टॉल और रेफ़रेंस करें।  
- एक नया `Document` और `DocumentBuilder` बनाएं।  
- **Insert ActiveX** CommandButton कंट्रोल को एक ही लाइन कोड से डालें।  
- **Set button caption**, उसकी पोजीशन समायोजित करें, और उसके डायमेंशन निर्धारित करें।  
- दस्तावेज़ को सहेजें और Word में खोलें ताकि परिणाम देखें।

ActiveX का कोई पूर्व अनुभव आवश्यक नहीं है; केवल बुनियादी Java ज्ञान और Aspose.Words की एक कॉपी चाहिए।

---

## पूर्वापेक्षाएँ

- आपके मशीन पर Java 8 या उससे नया संस्करण स्थापित हो।  
- निर्भरता प्रबंधन के लिए Maven या Gradle (हम Maven स्निपेट दिखाएंगे)।  
- **Aspose.Words for Java** की लाइसेंस्ड या इवैल्यूएशन कॉपी (इस डेमो के लिए फ्री ट्रायल ठीक काम करता है)।  
- Microsoft Word (कोई भी हालिया संस्करण) ताकि उत्पन्न फ़ाइल का परीक्षण किया जा सके।

---

## चरण 1: अपने प्रोजेक्ट में Aspose.Words सेट अप करें

सबसे पहले—Aspose.Words डिपेंडेंसी जोड़ें। यदि आप Maven उपयोग करते हैं, तो इसे अपने `pom.xml` में डालें:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.10</version> <!-- check for the latest version -->
</dependency>
```

Gradle उपयोगकर्ता जोड़ सकते हैं:

```gradle
implementation 'com.aspose:aspose-words:24.10'
```

`mvn clean install` (या `gradle build`) चलाने के बाद लाइब्रेरी आपके क्लासपाथ में होगी और आप कोड लिखने के लिए तैयार हैं।

---

## चरण 2: नया Document और Builder बनाएं

`Document` पूरे Word फ़ाइल को दर्शाता है, जबकि `DocumentBuilder` आपको इसे संपादित करने देता है। Builder को एक पेन की तरह समझें जो नई कैनवास पर ड्रॉ करता है।

```java
import com.aspose.words.*;

public class ActiveXButtonDemo {
    public static void main(String[] args) throws Exception {
        // Step 2: Initialize a blank document and a builder
        Document doc = new Document();                 // creates an empty .docx
        DocumentBuilder builder = new DocumentBuilder(doc);
```

खाली दस्तावेज़ से क्यों शुरू करें? यह सुनिश्चित करता है कि आप जोड़ने वाले प्रत्येक तत्व पर पूर्ण नियंत्रण रखें, और बाद में कोई छिपा हुआ फ़ॉर्मेटिंग आपको आश्चर्यचकित नहीं करेगा।

---

## चरण 3: ActiveX CommandButton कंट्रोल डालें

अब मुख्य भाग की बारी। Aspose.Words `insertForms2OleControl` प्रदान करता है जो आप द्वारा निर्दिष्ट किसी भी ActiveX कंट्रोल को रख सकता है। यहाँ हम **CommandButton** मांग रहे हैं।

```java
        // Step 3: Insert a CommandButton ActiveX control
        Forms2OleControl commandBtn = builder.insertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON);
```

यह मेथड एक `Forms2OleControl` ऑब्जेक्ट लौटाता है, जिससे आपको बटन की प्रॉपर्टीज़ तक प्रोग्रामेटिक एक्सेस मिलती है। यही वह जगह है जहाँ **how to insert activex** एक लाइन में हो जाता है—बिना लो‑लेवल COM API के साथ झंझट किए।

---

## चरण 4: बटन की पोजीशन, आकार, और कैप्शन सेट करें

पेज के मध्य में तैरता बटन बहुत उपयोगी नहीं होता। आपको इसे उपयोगकर्ताओं की अपेक्षा के अनुसार रखना होगा, उचित आकार देना होगा, और—सबसे महत्वपूर्ण—**set button caption** करना होगा ताकि उन्हें पता चले कि क्लिक करने से क्या होगा।

```java
        // Step 4a: Position the button (coordinates are in points)
        commandBtn.setLeft(100);   // distance from the left margin
        commandBtn.setTop(150);    // distance from the top margin

        // Step 4b: Define width and height
        commandBtn.setWidth(120);
        commandBtn.setHeight(30);

        // Step 4c: Set the button caption (the text that appears on the button)
        commandBtn.setCaption("Click Me");
```

**इन संख्याओं का कारण क्या है?** Word पॉइंट्स का उपयोग करता है (1 pt ≈ 1/72 इंच)। `100 pt` ≈ बाएँ से 1.4 इंच, `150 pt` ≈ ऊपर से 2.1 इंच—लगभग एक मानक A4 पेज के केंद्र में। अपने लेआउट के अनुसार इन्हें समायोजित करें।

कैप्शन सेट करना महत्वपूर्ण है; इसके बिना बटन एक खाली आयत जैसा दिखेगा। `setCaption` मेथड कोई भी स्ट्रिंग स्वीकार करता है, इसलिए आवश्यकता पड़ने पर आप बाद में इसे स्थानीयकृत कर सकते हैं।

---

## चरण 5: दस्तावेज़ सहेजें

अंत में, दस्तावेज़ को डिस्क पर लिखें। आप कोई भी फ़ोल्डर चुन सकते हैं; बस यह सुनिश्चित करें कि पाथ मौजूद हो।

```java
        // Step 5: Save the document to a .docx file
        String outputPath = "C:/Temp/ActiveXButton.docx";
        doc.save(outputPath);
        System.out.println("Document saved to " + outputPath);
    }
}
```

जब आप Word में `ActiveXButton.docx` खोलेंगे, तो आपको एक अच्छी तरह रखी गई बटन **“Click Me.”** लेबल के साथ दिखेगी। यदि आप इसे डबल‑क्लिक करेंगे, तो Word आपको मैक्रो सक्षम करने के लिए प्रॉम्प्ट करेगा (क्योंकि ActiveX कंट्रोल्स को मैक्रो‑एनेबल्ड माना जाता है)। वहां से आप बटन के `Click` इवेंट से एक VBA रूटीन बाइंड कर सकते हैं।

---

## ध्यान देने योग्य किनारे के मामले और टिप्स

- **Macro‑Enabled Format**: Word साधारण `.docx` फ़ाइलों में ActiveX कंट्रोल्स को निष्क्रिय कर देता है जब तक उपयोगकर्ता मैक्रो सक्षम नहीं करता। यदि आपको बटन को तुरंत काम करना है, तो `doc.save(outputPath, SaveFormat.DOCM);` का उपयोग करके `.docm` (मैक्रो‑एनेबल्ड) के रूप में सहेजने पर विचार करें।
- **Compatibility**: Word के पुराने संस्करण (pre‑2007) बाइनरी `.doc` फ़ॉर्मेट का उपयोग करते हैं। Aspose.Words इसे सहेज सकता है, लेकिन कंट्रोल की प्रॉपर्टीज़ थोड़ा अलग दिख सकती हैं।
- **Security Settings**: कुछ कॉरपोरेट वातावरण ActiveX को लॉक कर देते हैं। यदि आपका बटन नहीं दिख रहा है, तो Word के Trust Center → ActiveX Settings देखें।
- **Multiple Buttons**: एक से अधिक चाहिए? बस `insertForms2OleControl` कॉल को दोहराएँ और प्रत्येक बटन के `Left`/`Top` मान समायोजित करें। लौटाए गए ऑब्जेक्ट्स को ट्रैक रखें ताकि आप व्यक्तिगत कैप्शन सेट कर सकें।
- **Styling the Caption**: कैप्शन डिफ़ॉल्ट फ़ॉन्ट को विरासत में लेता है। इसे बदलने के लिए आपको अंतर्निहित XML को संपादित करना होगा या इन्सर्शन के बाद Word स्टाइल लागू करना होगा—यह त्वरित गाइड के दायरे से बाहर है, लेकिन Aspose.Words के `ParagraphFormat` API से किया जा सकता है।

---

## पूरा कार्यशील उदाहरण

नीचे पूरा, तैयार‑चलाने योग्य Java क्लास दिया गया है। इसे अपने IDE में कॉपी‑पेस्ट करें, आउटपुट पाथ समायोजित करें, और **Run** दबाएँ।

```java
import com.aspose.words.*;

public class ActiveXButtonDemo {
    public static void main(String[] args) throws Exception {
        // Create a new blank document
        Document doc = new Document();

        // Obtain a DocumentBuilder to edit the document
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert an ActiveX CommandButton control
        Forms2OleControl commandBtn = builder.insertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON);

        // Position the button (points from the left/top margins)
        commandBtn.setLeft(100);
        commandBtn.setTop(150);

        // Set size (width × height in points)
        commandBtn.setWidth(120);
        commandBtn.setHeight(30);

        // Set the button caption – this is the visible text
        commandBtn.setCaption("Click Me");

        // Save the document; you may also use SaveFormat.DOCM for macro‑enabled files
        String outputPath = "C:/Temp/ActiveXButton.docx";
        doc.save(outputPath);
        System.out.println("Document saved to " + outputPath);
    }
}
```

**अपेक्षित आउटपुट**: चलाने के बाद, कंसोल में सहेजने का स्थान प्रिंट होगा। उत्पन्न फ़ाइल को Word में खोलने पर पेज के मध्य में लगभग स्थित बटन दिखेगा, लेबल “Click Me”. इसे क्लिक करने से मानक ActiveX क्लिक इवेंट ट्रिगर होगा (प्रतिक्रिया देने के लिए आपको एक VBA मैक्रो संलग्न करना होगा)।

---

## निष्कर्ष

अब आप जानते हैं कि Aspose.Words के साथ प्रोग्रामेटिकली Word दस्तावेज़ में **how to insert ActiveX** CommandButton कंट्रोल कैसे डालें, और आपने ठीक‑ठीक देखा है कि **set button caption**, पोजीशन और आकार कैसे सेट करें। यह तरीका मैन्युअल UI कार्य को समाप्त करता है, स्वचालित रिपोर्ट जेनरेटर में साफ़ इंटीग्रेशन देता है, और आपको पूरी नियंत्रण देता है।

## अगले में आपको क्या सीखना चाहिए?

निम्नलिखित ट्यूटोरियल्स उन निकट संबंधित विषयों को कवर करते हैं जो इस गाइड में दिखाए गए तकनीकों पर आधारित हैं। प्रत्येक संसाधन में पूर्ण कार्यशील कोड उदाहरण और चरण‑दर‑चरण व्याख्याएँ शामिल हैं ताकि आप अतिरिक्त API फीचर्स में निपुण हो सकें और अपने प्रोजेक्ट्स में वैकल्पिक इम्प्लीमेंटेशन अप्रोच का पता लगा सकें।

- [Aspose.Words for .NET का उपयोग करके Word दस्तावेज़ में शैप्स डालें](/words/english/net/working-with-shapes/insert-shape/)
- [Aspose.Words का उपयोग करके Word दस्तावेज़ में इनलाइन इमेज डालें](/words/english/net/add-content-using-document-builder/insert-inline-image/)
- [Word दस्तावेज़ हेडर में इमेज डालें | Aspose.Words for .NET](/words/english/net/header-footer-formatting/insert-image/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}