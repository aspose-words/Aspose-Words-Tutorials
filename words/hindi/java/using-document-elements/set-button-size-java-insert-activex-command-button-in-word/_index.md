---
category: general
date: 2026-07-29
description: 'सेट बटन साइज जावा ट्यूटोरियल: जावा और Aspose.Words का उपयोग करके वर्ड
  दस्तावेज़ में ActiveX कमांड बटन कैसे डालें, साथ ही बटन का आकार निर्धारित करना और
  खाली दस्तावेज़ बनाना सीखें।'
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- set button size java
- how to insert activex
- how to set button
- java create blank word
- insert command button word
language: hi
lastmod: 2026-07-29
og_description: सेट बटन साइज जावा गाइड दिखाता है कि जावा का उपयोग करके वर्ड फ़ाइल
  में एक ActiveX कमांड बटन कैसे डालें, उसका आकार समायोजित करें, और प्रोग्रामेटिक रूप
  से दस्तावेज़ को सहेजें।
og_image_alt: set button size java example showing a Word document with an ActiveX
  command button
og_title: बटन का आकार सेट करें जावा – जावा के साथ वर्ड में ActiveX कमांड बटन जोड़ें
schemas:
- author: Aspose
  dateModified: '2026-07-29'
  description: 'set button size java tutorial: learn how to insert ActiveX command
    button in a Word document using Java and Aspose.Words, plus sizing and blank document
    creation.'
  headline: set button size java – Insert ActiveX Command Button in Word
  type: TechArticle
- description: 'set button size java tutorial: learn how to insert ActiveX command
    button in a Word document using Java and Aspose.Words, plus sizing and blank document
    creation.'
  name: set button size java – Insert ActiveX Command Button in Word
  steps:
  - name: 1. Set Up the Project and Import Aspose.Words
    text: 'First, create a new Maven (or Gradle) project and add the Aspose.Words
      dependency shown above. Then, import the required classes in your Java source
      file:'
  - name: 2. java create blank word Document
    text: Now we actually **java create blank word** document. This is the foundation
      on which we’ll later **insert command button word**.
  - name: 3. Initialize DocumentBuilder and Insert the ActiveX Control
    text: 'The `DocumentBuilder` is a helper that lets us add content, paragraphs,
      tables, and, yes, ActiveX controls. Here’s where we answer **how to insert activex**:'
  - name: 4. How to Set Button Size Java – Adjust Width and Height
    text: 'Now comes the heart of the tutorial: **how to set button size java**. The
      control exposes several layout properties—`Left`, `Top`, `Width`, and `Height`.
      Setting them directly controls the button’s appearance on the page.'
  - name: 5. Save the Document
    text: 'Finally, persist the document to disk:'
  - name: What if the button doesn’t appear in Word?
    text: '- **Check the Word version.** ActiveX controls require the desktop version
      of Word; Word Online strips them out. - **Make sure the Aspose.Words license
      is applied** (if you’re using a paid edition). An unlicensed evaluation version
      may embed a watermark but still shows the control.'
  - name: Can I change the button’s font or color?
    text: Yes. After inserting the control, you can access its underlying OLE object
      and manipulate the VBA properties. That’s a more advanced topic—look into `commandButton.getOleObject().setProperty("ForeColor",
      0xFF0000)` for a red caption, for example.
  - name: How do I handle the button’s click event?
    text: ActiveX command buttons fire a VBA `Click` event. To make the button functional,
      you’ll need to embed a macro in the same document. Aspose.Words can add a macro
      module via the `Document.getMacros()` API, but the macro code itself must be
      written in VBA.
  - name: What about different button types?
    text: 'Aspose.Words supports many `Forms2OleControlType` values: `CHECKBOX`, `OPTIONBUTTON`,
      `LISTBOX`, etc. Swap the enum constant in the `insertForms2OleControl` call
      to experiment.'
  type: HowTo
tags:
- Java
- Aspose.Words
- ActiveX
- Word Automation
title: बटन का आकार सेट करें जावा – वर्ड में ActiveX कमांड बटन डालें
url: /hi/java/using-document-elements/set-button-size-java-insert-activex-command-button-in-word/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# बटन आकार सेट करें java – Word में ActiveX कमांड बटन डालें

क्या आपने कभी सोचा है **how to set button size java** के बारे में जब आप Word दस्तावेज़ों को ऑटोमेट कर रहे हों? शायद आप एक रिपोर्टिंग टूल बना रहे हैं जिसे .docx फ़ाइल के भीतर एक क्लिक करने योग्य “Submit” बटन चाहिए। इस ट्यूटोरियल में हम पूरी प्रक्रिया को समझेंगे—एक खाली Word दस्तावेज़ बनाना, ActiveX कमांड बटन डालना, और उसकी चौड़ाई व ऊँचाई को स्पष्ट रूप से सेट करना—सभी Java और Aspose.Words के साथ।

हम उन कई डेवलपर्स के लिए अक्सर उठने वाले “how to insert activex” सवाल का भी जवाब देंगे। अंत तक आपके पास एक चलाने योग्य प्रोग्राम होगा जो एक Word फ़ाइल उत्पन्न करेगा जिसमें बिल्कुल सही आकार का कमांड बटन होगा, जिसे आगे कस्टमाइज़ किया जा सकता है।

---

## What You’ll Need

शुरू करने से पहले सुनिश्चित करें कि आपके पास निम्नलिखित हैं:

- **Java Development Kit (JDK) 8 या नया** – कोड किसी भी हालिया JDK के साथ कंपाइल होता है।
- **Aspose.Words for Java** (जुलाई 2026 तक का नवीनतम संस्करण)। JAR को [Aspose वेबसाइट](https://products.aspose.com/words/java) से डाउनलोड करें या Maven के माध्यम से प्राप्त करें:
  ```xml
  <dependency>
      <groupId>com.aspose</groupId>
      <artifactId>aspose-words</artifactId>
      <version>23.10</version>
  </dependency>
  ```
- कोई भी IDE या साधारण टेक्स्ट एडिटर—IntelliJ IDEA, Eclipse, या VS Code चलेगा।
- वह फ़ोल्डर जहाँ आप उत्पन्न **CommandButton.docx** को सहेजना चाहते हैं।

बस इतना ही। कोई अतिरिक्त Office interop लाइब्रेरी नहीं, कोई COM ट्रिक नहीं, सिर्फ शुद्ध Java।

---

## Step‑by‑Step Implementation

हम समाधान को पाँच तार्किक चरणों में विभाजित करेंगे। प्रत्येक चरण का अपना H2 हेडर है; उनमें से एक में हमारा **primary keyword** है ताकि SEO संतुष्ट हो।

### 1. Set Up the Project and Import Aspose.Words

पहले, एक नया Maven (या Gradle) प्रोजेक्ट बनाएं और ऊपर दिखाए गए Aspose.Words डिपेंडेंसी को जोड़ें। फिर, अपने Java स्रोत फ़ाइल में आवश्यक क्लासेज़ को इम्पोर्ट करें:

```java
import com.aspose.words.*;
```

> **Pro tip:** यदि आप IDE का उपयोग कर रहे हैं, तो इसे क्लासेज़ को ऑटो‑इम्पोर्ट करने दें। इससे बहुत टाइपिंग बचती है और टाइपो से बचा जा सकता है।

### 2. java create blank word Document

अब हम वास्तव में **java create blank word** दस्तावेज़ बनाते हैं। यह वह आधार है जिस पर हम बाद में **insert command button word** डालेंगे।

```java
// Step 2: Create a new blank document
Document document = new Document();          // Starts with a clean, empty .docx
```

`Document` ऑब्जेक्ट मेमोरी में पूरे Word फ़ाइल का प्रतिनिधित्व करता है। इस बिंदु पर फ़ाइल में कोई पेज, कोई टेक्स्ट नहीं—सिर्फ एक साफ़ स्लेट।

### 3. Initialize DocumentBuilder and Insert the ActiveX Control

`DocumentBuilder` एक हेल्पर है जो हमें कंटेंट, पैराग्राफ, टेबल, और हाँ, ActiveX कंट्रोल जोड़ने देता है। यहाँ हम **how to insert activex** का उत्तर देते हैं:

```java
// Step 3: Initialize a DocumentBuilder to work with the document
DocumentBuilder builder = new DocumentBuilder(document);

// Insert an ActiveX command button (COMMANDBUTTON is a built‑in type)
Forms2OleControl commandButton = builder.insertForms2OleControl(
        Forms2OleControlType.COMMANDBUTTON);
```

`Forms2OleControl` Aspose का OLE ऑब्जेक्ट के चारों ओर रैपर है। `COMMANDBUTTON` निर्दिष्ट करके हम Word को क्लासिक ActiveX कमांड बटन एम्बेड करने के लिए कहते हैं।

### 4. How to Set Button Size Java – Adjust Width and Height

अब ट्यूटोरियल का मुख्य भाग: **how to set button size java**। कंट्रोल कई लेआउट प्रॉपर्टीज़—`Left`, `Top`, `Width`, और `Height`—को एक्सपोज़ करता है। इन्हें सीधे सेट करने से बटन की पेज पर उपस्थिति नियंत्रित होती है।

```java
// Step 4: Set button properties, including size
commandButton.setCaption("Click Me"); // Text shown on the button
commandButton.setLeft(100);           // Distance from the left margin (points)
commandButton.setTop(200);            // Distance from the top margin (points)
commandButton.setWidth(120);          // Width in points (≈1.67 inches)
commandButton.setHeight(30);          // Height in points (≈0.42 inches)
```

ये नंबर क्यों? Word में एक पॉइंट 1/72 इंच के बराबर होता है। इसलिए `120` पॉइंट की चौड़ाई लगभग 1.67 इंच बनती है—लेबल पढ़ने योग्य होने के लिए पर्याप्त बड़ी, लेकिन बहुत अधिक नहीं। अपने लेआउट के अनुसार मान बदलें; वही प्रॉपर्टीज़ आपके **how to set button** सवाल का भी उत्तर देती हैं।

> **Note:** यदि आपको अलग बटन प्रकार चाहिए (जैसे, चेकबॉक्स), तो `Forms2OleControlType.COMMANDBUTTON` को उपयुक्त enum वैल्यू से बदल दें।

### 5. Save the Document

अंत में, दस्तावेज़ को डिस्क पर सहेजें:

```java
// Step 5: Save the document with the embedded ActiveX control
document.save("YOUR_DIRECTORY/CommandButton.docx");
```

`YOUR_DIRECTORY` को अपने मशीन पर एक एब्सोल्यूट या रिलेटिव पाथ से बदलें। प्रोग्राम चलाने के बाद, उत्पन्न फ़ाइल को Microsoft Word में खोलें। आपको बाएँ से 100 pts और ऊपर से 200 pts की दूरी पर “Click Me” लेबल वाला बटन दिखाई देगा, जिसकी आकार बिल्कुल वही है जो हमने सेट किया था।

---

## Full Working Example

नीचे पूरा, तैयार‑चलाने‑योग्य Java क्लास दिया गया है। इसे `CommandButtonActiveX.java` में कॉपी‑पेस्ट करें, आउटपुट पाथ समायोजित करें, और **Run** दबाएँ।

```java
import com.aspose.words.*;

public class CommandButtonActiveX {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document (java create blank word)
        Document document = new Document();

        // Step 2: Initialize a DocumentBuilder to work with the document
        DocumentBuilder builder = new DocumentBuilder(document);

        // Step 3: Insert an ActiveX command button (how to insert activex)
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON);

        // Step 4: Set button properties – this is how to set button size java
        commandButton.setCaption("Click Me"); // Button text
        commandButton.setLeft(100);           // Left position (points)
        commandButton.setTop(200);            // Top position (points)
        commandButton.setWidth(120);          // Width (points)
        commandButton.setHeight(30);          // Height (points)

        // Step 5: Save the document (insert command button word)
        document.save("YOUR_DIRECTORY/CommandButton.docx");
    }
}
```

**Expected output:** `CommandButton.docx` को Word में खोलने पर एक सिंगल पेज दिखेगा जिसमें मध्य‑पेज के आसपास स्थित एक क्लिक‑योग्य “Click Me” बटन होगा। बटन के आयाम वही होंगे जो आपने सेट किए थे, जिससे यह पुष्टि होती है कि **set button size java** इच्छानुसार काम कर रहा है।

---

## Common Questions & Edge Cases

### What if the button doesn’t appear in Word?

- **Word संस्करण जांचें।** ActiveX कंट्रोल्स को डेस्कटॉप संस्करण के Word की आवश्यकता होती है; Word Online इन्हें हटा देता है।
- **सुनिश्चित करें कि Aspose.Words लाइसेंस लागू है** (यदि आप पेड एडिशन उपयोग कर रहे हैं)। अनलाइसेंस्ड एवाल्यूएशन संस्करण में वॉटरमार्क हो सकता है, लेकिन कंट्रोल अभी भी दिखेगा।

### Can I change the button’s font or color?

हां। कंट्रोल डालने के बाद आप उसके अंतर्निहित OLE ऑब्जेक्ट तक पहुंच सकते हैं और VBA प्रॉपर्टीज़ को बदल सकते हैं। यह अधिक उन्नत विषय है—उदाहरण के लिए `commandButton.getOleObject().setProperty("ForeColor", 0xFF0000)` का उपयोग करके कैप्शन को लाल रंग में बदलें।

### How do I handle the button’s click event?

ActiveX कमांड बटन VBA `Click` इवेंट फायर करता है। बटन को कार्यात्मक बनाने के लिए आपको उसी दस्तावेज़ में एक मैक्रो एम्बेड करना होगा। Aspose.Words `Document.getMacros()` API के माध्यम से मैक्रो मॉड्यूल जोड़ सकता है, लेकिन मैक्रो कोड स्वयं VBA में लिखा जाना चाहिए।

### What about different button types?

Aspose.Words कई `Forms2OleControlType` वैल्यूज़ सपोर्ट करता है: `CHECKBOX`, `OPTIONBUTTON`, `LISTBOX`, आदि। `insertForms2OleControl` कॉल में enum कॉन्स्टैंट को बदलकर आप विभिन्न प्रकार के कंट्रोल्स आज़मा सकते हैं।

---

## Pro Tips for Production‑Ready Code

1. **लेआउट वैल्यूज़ के लिए कॉन्स्टेंट्स उपयोग करें** – भविष्य में बदलाव आसान हो जाएगा।
2. **सेव पाथ को `Path` ऑब्जेक्ट में रैप करें** ताकि प्लेटफ़ॉर्म‑स्पेसिफ़िक सेपरेटर समस्याओं से बचा जा सके।
3. **Document को डिस्पोज़ करें** (या कई फ़ाइलों को लूप में प्रोसेस करते समय try‑with‑resources का उपयोग करें)।
4. **सेव करने से पहले आउटपुट फ़ोल्डर वैलिडेट करें** ताकि `FileNotFoundException` से बचा जा सके।

---

## Conclusion

आपने अभी **set button size java** सीख लिया है—एक खाली Word फ़ाइल बनाकर, ActiveX कमांड बटन डालकर, और उसकी डाइमेंशन को सटीक रूप से कॉन्फ़िगर करके—सिर्फ कुछ ही लाइनों के Java कोड से। यह **how to insert activex**, **how to set button**, **java create blank word**, और **insert command button word** को एक ही, स्व-समाहित उदाहरण में कवर करता है।

अगले कदम? बटन के कैप्शन को कस्टमाइज़ करें, क्लिक इवेंट के लिए मैक्रो जोड़ें, या एक ही पेज पर कई कंट्रोल्स एम्बेड करें। आप Aspose.Words के साथ परिणामी .docx को PDF में कनवर्ट करने का भी अन्वेषण कर सकते हैं, जिससे बटन एक स्थैतिक इमेज के रूप में संरक्षित रहेगा।

प्रयोग करने में संकोच न करें, और यदि कोई समस्या आती है तो नीचे टिप्पणी छोड़ें। Happy coding!

## What Should You Learn Next?

नीचे दिए गए ट्यूटोरियल्स उन विषयों को कवर करते हैं जो इस गाइड में दिखाए गए तकनीकों पर आधारित हैं। प्रत्येक संसाधन में पूर्ण कार्यशील कोड उदाहरण और चरण‑दर‑चरण व्याख्याएँ शामिल हैं, जिससे आप अतिरिक्त API फीचर्स में महारत हासिल कर सकते हैं और अपने प्रोजेक्ट्स में वैकल्पिक इम्प्लीमेंटेशन अप्रोचेज़ का अन्वेषण कर सकते हैं।

- [How to create form fields and add content using DocumentBuilder in Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [How to Load Word Documents with Aspose.Words Java: Comprehensive Guide](/words/english/java/document-operations/aspose-words-java-master-word-processing/)
- [How to save document as pdf with Aspose.Words for Java](/words/english/java/document-loading-and-saving/saving-documents-as-pdf/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}