---
category: general
date: 2026-10-20
description: जावा का उपयोग करके प्रोग्रामेटिक रूप से एक खाली DOCX बनाएं और उसमें एक
  कमांड बटन एम्बेड करें। बटन के साथ वर्ड को सहेजने और कमांड बटन का कैप्शन सेट करने
  के लिए पूर्ण वर्ड दस्तावेज़ निर्माण कोड सीखें।
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank docx programmatically
- create word document code
- save word with button
- add command button word
- set command button caption
language: hi
lastmod: 2026-10-20
og_description: प्रोग्रामेटिक रूप से एक खाली DOCX बनाएं और उसमें एक कमांड बटन एम्बेड
  करें। बटन के साथ Word को सहेजने और कमांड बटन का कैप्शन सेट करने के लिए इस चरण‑दर‑चरण
  Java गाइड का पालन करें।
og_image_alt: Screenshot of a blank DOCX file with an inserted command button created
  programmatically
og_title: प्रोग्रामेटिक रूप से एक खाली DOCX बनाएं – एक कमांड बटन जोड़ें
schemas:
- author: Aspose
  dateModified: '2026-10-20'
  description: Create a blank DOCX programmatically and embed a command button using
    Java. Learn the full create word document code to save Word with button and set
    command button caption.
  headline: Create a blank DOCX programmatically and add a command button
  type: TechArticle
- description: Create a blank DOCX programmatically and embed a command button using
    Java. Learn the full create word document code to save Word with button and set
    command button caption.
  name: Create a blank DOCX programmatically and add a command button
  steps:
  - name: Initialize a new blank document
    text: A blank document is the canvas on which you’ll place the command button.
      Aspose.Words provides the `Document` class for this purpose.
  - name: Set up a `DocumentBuilder`
    text: '`DocumentBuilder` is a helper that lets you insert content, including OLE
      controls, without dealing with low‑level node manipulation.'
  - name: Insert an OLE command button
    text: Word treats interactive controls as OLE (Object Linking and Embedding) objects.
      Aspose.Words exposes `Forms2OleControl` for this.
  - name: Configure the button – type, caption, and location
    text: You must define the control’s type (`COMMANDBUTTON`), set a user‑visible
      caption, and place it on the page.
  - name: Save the document with the embedded button
    text: Finally, write the file to disk. The resulting file can be opened in Microsoft
      Word, where the button will be fully functional.
  - name: Expected result
    text: 'When you open `CommandButton.docx` in Microsoft Word:'
  type: HowTo
tags:
- Java
- DOCX
- Aspose.Words
- Command button
- Automation
title: प्रोग्रामेटिक रूप से एक खाली DOCX बनाएं और एक कमांड बटन जोड़ें
url: /hi/java/document-manipulation/create-a-blank-docx-programmatically-and-add-a-command-butto/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# प्रोग्रामेटिकली एक खाली DOCX बनाएं और कमांड बटन जोड़ें

यदि आपको **एक खाली DOCX प्रोग्रामेटिकली बनाना** है, तो यह ट्यूटोरियल आपको दिखाता है कि फ़ाइल में सीधे एक कमांड बटन कैसे एम्बेड किया जाए। आपको पूरी *create word document code* मिल जाएगी जो बटन के साथ एक Word दस्तावेज़ को सहेजती है, आपको **set command button caption** करने देती है, और नवीनतम Aspose.Words for Java लाइब्रेरी के साथ काम करती है।

DOCX फ़ाइल में इंटरैक्टिव कंट्रोल एम्बेड करना उपयोगी है जब आप ऐसे टेम्प्लेट वितरित करना चाहते हैं जो मैक्रो ट्रिगर करते हैं, बाहरी प्रोग्राम लॉन्च करते हैं, या सिर्फ़ उपयोगकर्ताओं को एक क्लिक करने योग्य “Click Me” बटन से मार्गदर्शन करते हैं। नीचे दिए गए चरण एक खाली दस्तावेज़ को इनिशियलाइज़ करने से लेकर अंतिम फ़ाइल को डिस्क पर सहेजने तक सब कुछ कवर करते हैं।

## आवश्यकताएँ

शुरू करने से पहले, सुनिश्चित करें कि आपके पास है:

* Java 17 या नया स्थापित हो।
* Maven (या आपका पसंदीदा बिल्ड टूल) निर्भरताओं को प्रबंधित करने के लिए।
* Aspose.Words for Java 23.9 या बाद का संस्करण। अपनी `pom.xml` में निर्भरता जोड़ें:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
    <classifier>jdk17</classifier>
</dependency>
```

* IntelliJ IDEA या VS Code जैसे IDE (कोई भी एडिटर जो Java सपोर्ट करता है) काम करता है।

## प्रोग्रामेटिकली एक खाली DOCX बनाना – चरण‑दर‑चरण

निम्नलिखित सेक्शन प्रक्रिया को स्पष्ट, क्रमांकित चरणों में विभाजित करते हैं। प्रत्येक चरण यह समझाता है कि यह **क्यों** आवश्यक है, न कि केवल **क्या** टाइप करना है।

### चरण 1: नया खाली दस्तावेज़ इनिशियलाइज़ करें

एक खाली दस्तावेज़ वह कैनवास है जिस पर आप कमांड बटन रखेंगे। इस उद्देश्य के लिए Aspose.Words `Document` क्लास प्रदान करता है।

```java
import com.aspose.words.Document;
import com.aspose.words.DocumentBuilder;

public class CommandButtonDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document
        Document document = new Document();
```

*यह क्यों महत्वपूर्ण है*: एक खाली `Document` से शुरू करने से यह सुनिश्चित होता है कि कोई छिपा हुआ फॉर्मेटिंग या मौजूदा कंट्रोल बटन को बाद में जोड़ते समय बाधा न बनें।

### चरण 2: एक `DocumentBuilder` सेट अप करें

`DocumentBuilder` एक सहायक है जो आपको कंटेंट, जिसमें OLE कंट्रोल भी शामिल हैं, को इन्सर्ट करने देता है, बिना लो‑लेवल नोड मैनिपुलेशन के।

```java
        // Step 2: Initialize a DocumentBuilder for the document
        DocumentBuilder builder = new DocumentBuilder(document);
```

*यह क्यों महत्वपूर्ण है*: बिल्डर वर्तमान कर्सर पोजीशन को बनाए रखता है, इसलिए बटन ठीक उसी जगह पर रखा जाएगा जहाँ आप निर्दिष्ट करेंगे।

### चरण 3: एक OLE कमांड बटन इन्सर्ट करें

Word इंटरैक्टिव कंट्रोल को OLE (Object Linking and Embedding) ऑब्जेक्ट के रूप में मानता है। इसके लिए Aspose.Words `Forms2OleControl` प्रदान करता है।

```java
        // Step 3: Insert an OLE command button into the document
        com.aspose.words.forms.Forms2OleControl commandButton = builder.insertForms2OleControl();
```

*यह क्यों महत्वपूर्ण है*: कंट्रोल को इन्सर्ट करने से एक प्लेसहोल्डर बनता है जिसे आप बाद में कॉन्फ़िगर कर सकते हैं (टाइप, कैप्शन, पोजीशन)।

### चरण 4: बटन को कॉन्फ़िगर करें – टाइप, कैप्शन, और लोकेशन

आपको कंट्रोल का टाइप (`COMMANDBUTTON`) निर्धारित करना होगा, उपयोगकर्ता‑दिखाई देने वाला कैप्शन सेट करना होगा, और इसे पेज पर रखना होगा।

```java
        // Step 4: Configure the command button's type, caption, and position
        commandButton.setOleControlType(com.aspose.words.forms.OleControlType.COMMANDBUTTON);
        commandButton.setCaption("Click Me");               // set command button caption
        commandButton.setLeft(100);                         // distance from the left margin (points)
        commandButton.setTop(200);                          // distance from the top margin (points)
```

*यह क्यों महत्वपूर्ण है*:  
* **Type** Word को बताता है कि कंट्रोल एक क्लिक करने योग्य बटन की तरह व्यवहार करता है।  
* **Caption** वह टेक्स्ट है जो उपयोगकर्ता देखता है; इसे बदलना वही है जिससे आप **set command button caption** करते हैं।  
* **Left** और **Top** सटीक प्लेसमेंट को नियंत्रित करते हैं, जो तब आवश्यक है जब आप **add command button word** दस्तावेज़ बनाते हैं जिन्हें सटीक लेआउट चाहिए।

### चरण 5: एम्बेडेड बटन के साथ दस्तावेज़ को सहेजें

अंत में, फ़ाइल को डिस्क पर लिखें। परिणामी फ़ाइल को Microsoft Word में खोला जा सकता है, जहाँ बटन पूरी तरह कार्यशील होगा।

```java
        // Step 5: Save the document with the embedded command button
        String outputPath = "YOUR_DIRECTORY/CommandButton.docx";
        document.save(outputPath);
        System.out.println("Document saved to: " + outputPath);
    }
}
```

*यह क्यों महत्वपूर्ण है*: यह चरण **saves Word with button** करता है ताकि कंट्रोल मशीनों के बीच बना रहे। फ़ाइल को टेम्प्लेट के रूप में वितरित किया जा सकता है या स्वचालित रिपोर्ट जेनरेशन पाइपलाइन में उपयोग किया जा सकता है।

## पूर्ण कार्यशील उदाहरण

नीचे दिया गया पूरा क्लास `CommandButtonDemo.java` नाम की फ़ाइल में कॉपी करें, `YOUR_DIRECTORY` को वास्तविक पथ में बदलें, और इसे `mvn compile exec:java` के साथ चलाएँ।

```java
import com.aspose.words.Document;
import com.aspose.words.DocumentBuilder;
import com.aspose.words.forms.Forms2OleControl;
import com.aspose.words.forms.OleControlType;

public class CommandButtonDemo {
    public static void main(String[] args) throws Exception {
        // Create a new blank document
        Document document = new Document();

        // Initialize a DocumentBuilder for the document
        DocumentBuilder builder = new DocumentBuilder(document);

        // Insert an OLE command button into the document
        Forms2OleControl commandButton = builder.insertForms2OleControl();

        // Configure the command button
        commandButton.setOleControlType(OleControlType.COMMANDBUTTON);
        commandButton.setCaption("Click Me");   // set command button caption
        commandButton.setLeft(100);             // points from left margin
        commandButton.setTop(200);              // points from top margin

        // Save the document with the embedded command button
        String outputPath = "YOUR_DIRECTORY/CommandButton.docx";
        document.save(outputPath);
        System.out.println("Document saved to: " + outputPath);
    }
}
```

### अपेक्षित परिणाम

जब आप Microsoft Word में `CommandButton.docx` खोलते हैं:

* दस्तावेज़ पूरी तरह खाली है सिवाय एक बटन के जो **Click Me** लेबल वाला है।
* बटन पर क्लिक करने से डिफ़ॉल्ट Word व्यवहार दिखेगा (जब तक कोई मैक्रो संलग्न नहीं है, यह कुछ नहीं करता), जो पुष्टि करता है कि OLE कंट्रोल सही ढंग से एम्बेड किया गया था।

## सामान्य प्रश्न और किनारे के मामलों

| प्रश्न | उत्तर |
|----------|--------|
| **क्या मैं बटन का आकार बदल सकता हूँ?** | हाँ। आयाम को पॉइंट्स में समायोजित करने के लिए `commandButton.setWidth(double)` और `commandButton.setHeight(double)` का उपयोग करें। |
| **अगर मुझे बटन के साथ एक मैक्रो संलग्न चाहिए तो?** | बटन स्वयं केवल एक OLE कंट्रोल है। आपको दस्तावेज़ में मैन्युअल रूप से या Aspose.Words `Document` API के `addMacro` यूटिलिटीज़ के माध्यम से VBA मैक्रो जोड़ना होगा। |
| **क्या बटन LibreOffice में काम करेगा?** | LibreOffice सीमित OLE कंट्रोल्स को सपोर्ट करता है। बटन दिखाई देगा, लेकिन उसका क्लिक व्यवहार अलग हो सकता है। |
| **एकाधिक बटन कैसे जोड़ें?** | स्टेप 3‑4 को एक नए `Forms2OleControl` इंस्टेंस के साथ दोहराएँ। ओवरलैप से बचने के लिए प्रत्येक बटन के `setLeft`/`setTop` को समायोजित करें। |
| **क्या कोड .NET के साथ संगत है?** | एक ही लॉजिक लागू होता है, लेकिन आप `.NET` क्लासेस (`Document`, `DocumentBuilder`, `Forms2OleControl`) के लिए `Aspose.Words` का उपयोग करेंगे। |

## क्षेत्र से टिप्स

* **प्रो टिप:** बटन इन्सर्ट करने से पहले `builder.moveToDocumentEnd()` उपयोग करें यदि आप इसे दस्तावेज़ के बिल्कुल अंत में चाहते हैं, चाहे पहले की सामग्री कुछ भी हो।
* **सावधान रहें:** बहुत छोटे `Left`/`Top` मान बटन को प्रिंटेबल एरिया के बाहर रख सकते हैं, जिससे वह Word के लेआउट व्यू में अदृश्य हो जाता है।
* **परफॉर्मेंस नोट:** कई OLE कंट्रोल्स इन्सर्ट करने से फ़ाइल आकार बढ़ सकता है। यदि आपको केवल एक विज़ुअल संकेत चाहिए, तो साधारण `Shape` के साथ हाइपरलिंक उपयोग करने पर विचार करें।

## निष्कर्ष

अब आप जानते हैं कि **प्रोग्रामेटिकली एक खाली DOCX कैसे बनाएं** और Java का उपयोग करके एक पूरी तरह कार्यशील कमांड बटन एम्बेड करें। ट्यूटोरियल ने पूरे *create word document code* वर्कफ़्लो को कवर किया, यह दिखाया कि कैसे **save Word with button** किया जाता है, सही तरीके से **add command button word** तत्वों को जोड़ा जाता है, और यह समझाया कि कैसे **set command button caption** किया जाता है।

अब आप कर सकते हैं:

* अधिक OLE कंट्रोल्स (चेकबॉक्स, कॉम्बो बॉक्स) जोड़ें ताकि फॉर्म अधिक समृद्ध हो।
* बटन को कस्टम एक्शन करने के लिए VBA मैक्रो संलग्न करें।
* इस तकनीक को डॉक्यूमेंट मेल‑मर्ज के साथ मिलाकर डायनामिक, इंटरैक्टिव टेम्प्लेट बनाएं।

बटन स्टाइल, पोजीशन और अतिरिक्त कंट्रोल्स के साथ प्रयोग करने में संकोच न करें ताकि यह आपके विशिष्ट व्यावसायिक आवश्यकताओं से मेल खाए। कोडिंग का आनंद लें

## अब आपको क्या सीखना चाहिए?

निम्नलिखित ट्यूटोरियल्स उन निकट संबंधित विषयों को कवर करते हैं जो इस गाइड में दिखाए गए तकनीकों पर आधारित हैं। प्रत्येक संसाधन में पूर्ण कार्यशील कोड उदाहरण और चरण‑दर‑चरण व्याख्याएँ शामिल हैं जो आपको अतिरिक्त API फीचर्स में महारत हासिल करने और अपने प्रोजेक्ट्स में वैकल्पिक इम्प्लीमेंटेशन एप्रोच को एक्सप्लोर करने में मदद करती हैं।

- [कमांड बटन के साथ खाली Word दस्तावेज़ बनाएं – चरण‑दर‑चरण गाइड](/words/english/java/using-document-elements/create-blank-word-document-with-a-command-button-step-by-ste/)
- [Word में ActiveX बटन कैसे इन्सर्ट करें – बटन कैप्शन सेट करें](/words/english/java/using-document-elements/how-to-insert-activex-button-in-word-set-button-caption/)
- [Java के साथ खाली Word दस्तावेज़ बनाएं – पूर्ण Aspose.Words गाइड](/words/english/java/document-loading-and-saving/create-blank-word-document-with-java-full-aspose-words-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}