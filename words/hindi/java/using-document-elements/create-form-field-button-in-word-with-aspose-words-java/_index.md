---
category: general
date: 2026-10-13
description: Aspose.Words for Java का उपयोग करके Word में फ़ॉर्म फ़ील्ड बटन बनाएं।
  कुछ आसान चरणों में कमांड बटन वर्ड फ़ॉर्म फ़ील्ड कैसे डालें और कमांड बटन कैप्शन कैसे
  सेट करें, सीखें।
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create form field button
- insert command button word
- set command button caption
language: hi
lastmod: 2026-10-13
og_description: Aspose.Words for Java का उपयोग करके Word में फ़ॉर्म फ़ील्ड बटन बनाएं।
  यह ट्यूटोरियल दिखाता है कि कमांड बटन वर्ड फ़ील्ड कैसे डालें और कमांड बटन कैप्शन
  को जल्दी से सेट करें।
og_image_alt: Screenshot of a Word document containing an inserted command button
  form field created with Aspose.Words Java
og_title: Word में फ़ॉर्म फ़ील्ड बटन बनाएं – Aspose.Words Java गाइड
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Create form field button in Word using Aspose.Words for Java. Learn
    how to insert command button word form fields and set command button caption in
    a few easy steps.
  headline: Create form field button in Word with Aspose.Words Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word automation
title: Aspose.Words Java के साथ Word में फ़ॉर्म फ़ील्ड बटन बनाएं
url: /hi/java/using-document-elements/create-form-field-button-in-word-with-aspose-words-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word में Aspose.Words Java के साथ फ़ॉर्म फ़ील्ड बटन बनाएं

यदि आपको Word दस्तावेज़ में **फ़ॉर्म फ़ील्ड बटन बनाना** है, तो यह गाइड Aspose.Words for Java का उपयोग करके पूरी प्रक्रिया को समझाता है। चाहे आप एक फ़ॉर्म टेम्पलेट बना रहे हों या रिपोर्ट में इंटरैक्टिव कंट्रोल जोड़ रहे हों, आप सीखेंगे कि कैसे **insert command button word** फ़ॉर्म फ़ील्ड डालें और **set command button caption** को न्यूनतम कोड के साथ सेट करें।

यह ट्यूटोरियल Maven सेटअप से लेकर पूरी तरह चलने योग्य उदाहरण तक सब कुछ कवर करता है, ताकि आप कोड को कॉपी‑पेस्ट कर सकें, चलाएँ, और एक `.docx` फ़ाइल देखें जिसमें एक क्लिक करने योग्य बटन हो, जो आगे की कस्टमाइज़ेशन के लिए तैयार है।

## आवश्यकताएँ

- Java 17 (या नया) आपके मशीन पर स्थापित और कॉन्फ़िगर किया हुआ।
- डिपेंडेंसी प्रबंधन के लिए Maven 3.6+।
- आपकी पसंद का IDE या टेक्स्ट एडिटर (जैसे, IntelliJ IDEA, VS Code)।
- एक वैध Aspose.Words for Java लाइसेंस (मुफ़्त ट्रायल मूल्यांकन के लिए काम करता है)।

## चरण 1: अपने Maven प्रोजेक्ट में Aspose.Words जोड़ें

`pom.xml` बनाएं (या मौजूदा को संपादित करें) और Aspose.Words डिपेंडेंसी शामिल करें:

```xml
<dependencies>
    <dependency>
        <groupId>com.aspose</groupId>
        <artifactId>aspose-words</artifactId>
        <version>24.9</version> <!-- Use the latest version available -->
    </dependency>
</dependencies>
```

> **Pro tip:** संस्करण संख्या को अद्यतन रखें। नए रिलीज़ नवीनतम Word फीचर्स के समर्थन को जोड़ते हैं और प्रदर्शन में सुधार करते हैं।

## चरण 2: एक खाली दस्तावेज़ और `DocumentBuilder` को इनिशियलाइज़ करें

`DocumentBuilder` क्लास Word दस्तावेज़ को संपादित करने के लिए एक फ़्लुएंट API प्रदान करती है। इस चरण में हम एक खाली `Document` बनाते हैं और उस पर एक बिल्डर संलग्न करते हैं।

```java
import com.aspose.words.*;

public class InsertCommandButtonDemo {
    public static void main(String[] args) throws Exception {
        // Create a new blank document
        Document doc = new Document();

        // DocumentBuilder lets us add content programmatically
        DocumentBuilder builder = new DocumentBuilder(doc);
```

दस्तावेज़ बनाना बाद में ट्यूटोरियल में **फ़ॉर्म फ़ील्ड बटन बनाने** के ऑब्जेक्ट्स के लिए आधार है।

## चरण 3: एक कमांड बटन फ़ॉर्म फ़ील्ड डालें

Aspose.Words OLE फ़ॉर्म कंट्रोल्स के लिए `Forms2OleControl` क्लास प्रदान करता है। **insert command button word** फ़ॉर्म फ़ील्ड डालने के लिए, `COMMANDBUTTON` enum वैल्यू के साथ `insertForms2OleControl` कॉल करें।

```java
        // Insert a Command Button form field at the current cursor position
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON);
```

यह मेथड एक `Forms2OleControl` इंस्टेंस लौटाता है जिसे हम सहेजने से पहले कॉन्फ़िगर कर सकते हैं।

## चरण 4: बटन का आकार और स्थिति निर्धारित करें

एक कमांड बटन को पृष्ठ पर स्पष्ट आयाम और स्थान की आवश्यकता होती है। अपने लेआउट के अनुसार चौड़ाई, ऊँचाई और निर्देशांक समायोजित करें।

```java
        // Set the button's visual size (in points)
        commandButton.setWidth(120);   // 120 points ≈ 1.67 inches
        commandButton.setHeight(30);   // 30 points ≈ 0.42 inches

        // Position the button relative to the page margins
        commandButton.setLeft(50);   // 50 points from the left margin
        commandButton.setTop(100);   // 100 points from the top margin
```

इन मानों को सूक्ष्म‑समायोजित करने से बटन अंतिम दस्तावेज़ में ठीक उसी जगह दिखाई देगा जहाँ आप चाहते हैं।

## चरण 5: **Set command button caption**

बटन पर दिखने वाला टेक्स्ट `setCaption` मेथड द्वारा नियंत्रित होता है। यहाँ हम उपयोगकर्ता को मार्गदर्शन देने के लिए **set command button caption** सेट करते हैं।

```java
        // Define the text that appears on the button
        commandButton.setCaption("Click Me");
```

आप `"Click Me"` को किसी भी लेबल से बदल सकते हैं जो आपके फ़ॉर्म के उद्देश्य से मेल खाता हो, जैसे `"Submit"` या `"Approve"`।

## चरण 6: दस्तावेज़ सहेजें

अंत में, दस्तावेज़ को डिस्क पर लिखें। परिणामी फ़ाइल में इंटरैक्टिव बटन होगा और इसे Microsoft Word या LibreOffice में खोला जा सकता है।

```java
        // Save the document with the embedded command button
        doc.save("CommandButtonDemo.docx");
    }
}
```

प्रोग्राम चलाने पर `CommandButtonDemo.docx` बनता है। इसे Word में खोलने पर एक बटन दिखता है जिसका लेबल **Click Me** है, जो पृष्ठ के बाएँ से 50 pts और ऊपर से 100 pts की दूरी पर स्थित है।

### अपेक्षित आउटपुट

- `CommandButtonDemo.docx` नाम की एक `.docx` फ़ाइल।
- दस्तावेज़ में एक पृष्ठ है जिसमें एक कमांड बटन फ़ॉर्म फ़ील्ड है।
- बटन वह कैप्शन दिखाता है जो आपने सेट किया है (उदा., **Click Me**)।

## सामान्य विविधताएँ और किनारी मामले

| स्थिति | कैसे अनुकूलित करें |
|-----------|--------------|
| **एकाधिक बटन** | `insertForms2OleControl` को बार‑बार कॉल करें, प्रत्येक नए बटन के लिए `setLeft`/`setTop` को समायोजित करें। |
| **प्रत्येक बटन के लिए अलग कैप्शन** | प्रत्येक इन्सर्शन के बाद एक अद्वितीय स्ट्रिंग के साथ `setCaption` का उपयोग करें। |
| **टेबल सेल के अंदर बटन** | कंट्रोल डालने से पहले `builder.moveTo(cell.getFirstParagraph())` के साथ कर्सर को इच्छित सेल में ले जाएँ। |
| **पुराने Word फ़ॉर्मेट (.doc)** | `doc.save("Demo.doc", SaveFormat.DOC);` का उपयोग करके सहेजें – कमांड बटन संरक्षित रहता है। |
| **केवल‑पढ़ने योग्य फ़ॉर्म** | इन्सर्शन के बाद, उपयोगकर्ता इंटरैक्शन को रोकने के लिए `commandButton.setEnabled(false);` सेट करें। |

## मजबूत कार्यान्वयन के लिए टिप्स

- **Validate dimensions**: अत्यधिक बड़ी चौड़ाइयाँ बटन को पृष्ठ मार्जिन से बाहर निकलने का कारण बन सकती हैं।
- **License enforcement**: वैध लाइसेंस के बिना, Aspose.Words उत्पन्न दस्तावेज़ में वॉटरमार्क जोड़ता है। अपना लाइसेंस जल्दी लागू करें `License license = new License(); license.setLicense("Aspose.Words.lic");` के साथ।
- **Testing**: उत्पन्न फ़ाइल को Word में खोलें और बटन की प्रॉपर्टीज़ देखने के लिए **Design Mode** (Developer → Design Mode) टॉगल करें।

## पूर्ण स्रोत कोड पुनरावलोकन

```java
import com.aspose.words.*;

public class InsertCommandButtonDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document and a builder to edit it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Insert a Command Button form field
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON);

        // Step 3: Define the button's size and position on the page
        commandButton.setWidth(120);
        commandButton.setHeight(30);
        commandButton.setLeft(50);
        commandButton.setTop(100);

        // Step 4: Set the text that appears on the button
        commandButton.setCaption("Click Me");

        // Step 5: Save the document with the embedded command button
        doc.save("CommandButtonDemo.docx");
    }
}
```

कोड को `InsertCommandButtonDemo.java` नामक फ़ाइल में कॉपी करें, Maven (`mvn compile`) से कंपाइल करें, और चलाएँ (`mvn exec:java -Dexec.mainClass=InsertCommandButtonDemo`)। उत्पन्न दस्तावेज़ आपके प्रोजेक्ट की रूट फ़ोल्डर में दिखाई देगा।

## निष्कर्ष

अब आप जानते हैं कि Aspose.Words for Java का उपयोग करके Word में **फ़ॉर्म फ़ील्ड बटन कैसे बनाएं**, **insert command button word** फ़ॉर्म फ़ील्ड कैसे डालें, और प्रोग्रामेटिकली **set command button caption** कैसे सेट करें। यह एंड‑टू‑एंड उदाहरण आपको अधिक समृद्ध, इंटरैक्टिव Word दस्तावेज़ बनाने के लिए एक ठोस आधार देता है—चाहे आपको एकल सबमिट बटन चाहिए या फ़ॉर्म कंट्रोल्स का पूरा सेट।

### आगे क्या?

- [Aspose.Words for Java में DocumentBuilder का उपयोग करके फ़ॉर्म फ़ील्ड बनाना और सामग्री जोड़ना कैसे करें](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [.NET के लिए Aspose.Words के साथ Word दस्तावेज़ में कॉम्बो बॉक्स फ़ॉर्म फ़ील्ड जोड़ें](/words/english/net/add-content-using-documentbuilder/insert-combo-box/)
- [.NET के लिए Aspose.Words के साथ Word दस्तावेज़ में चेक बॉक्स फ़ॉर्म फ़ील्ड जोड़ें](/words/english/net/add-content-using-documentbuilder/insert-check-box/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}