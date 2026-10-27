---
category: general
date: 2026-08-07
description: Aspose.Words ActiveX ट्यूटोरियल दिखाता है कि जावा का उपयोग करके Word
  दस्तावेज़ में CommandButton नियंत्रण कैसे जोड़ें। पूर्ण कोड, कॉन्फ़िगरेशन और सहेजने
  के चरण सीखें।
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- aspose words activex tutorial
- aspose.words java
- activeX control java
- documentbuilder insert control
- forms2olecontrol usage
language: hi
lastmod: 2026-08-07
og_description: Aspose.Words ActiveX ट्यूटोरियल बताता है कि जावा का उपयोग करके Word
  दस्तावेज़ में CommandButton ActiveX नियंत्रण को कैसे एम्बेड किया जाए। दस्तावेज़
  को बनाने, कॉन्फ़िगर करने और सहेजने के लिए पूर्ण उदाहरण का पालन करें।
og_image_alt: Screenshot of a Word document with a CommandButton added via Aspose.Words
  ActiveX tutorial
og_title: Aspose.Words ActiveX ट्यूटोरियल – जावा चरण-दर-चरण मार्गदर्शिका
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: Aspose.Words ActiveX tutorial shows how to add a CommandButton control
    to a Word document using Java. Learn the full code, configuration, and saving
    steps.
  headline: Aspose.Words ActiveX tutorial – insert a CommandButton with Java
  type: TechArticle
- description: Aspose.Words ActiveX tutorial shows how to add a CommandButton control
    to a Word document using Java. Learn the full code, configuration, and saving
    steps.
  name: Aspose.Words ActiveX tutorial – insert a CommandButton with Java
  steps:
  - name: Initialize a `Document` and `DocumentBuilder`.
    text: Initialize a `Document` and `DocumentBuilder`.
  - name: Insert a `Forms2OleControl` of type `COMMAND_BUTTON`.
    text: Insert a `Forms2OleControl` of type `COMMAND_BUTTON`.
  - name: Set the button’s name, caption, size, and position.
    text: Set the button’s name, caption, size, and position.
  - name: Save the document as a .docx file that contains the ActiveX control.
    text: Save the document as a .docx file that contains the ActiveX control.
  type: HowTo
tags:
- Aspose.Words
- Java
- ActiveX
title: Aspose.Words ActiveX ट्यूटोरियल – जावा के साथ एक CommandButton सम्मिलित करें
url: /hi/java/images-shapes/aspose-words-activex-tutorial-insert-a-commandbutton-with-ja/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words ActiveX ट्यूटोरियल – Java के साथ CommandButton डालें

यदि आपको Word फ़ाइल में एक ActiveX कंट्रोल एम्बेड करना है, तो यह **Aspose.Words ActiveX ट्यूटोरियल** आपको पूरी प्रक्रिया के माध्यम से ले जाएगा। आप देखेंगे कि कैसे एक खाली दस्तावेज़ बनाएं, एक CommandButton डालें, उसकी प्रॉपर्टीज़ सेट करें, और परिणाम को सहेजें—सभी साधारण Java कोड के साथ।

उदाहरण Aspose.Words for Java API का उपयोग करता है, जो बिल्ड सर्वर पर Microsoft Office की आवश्यकता को समाप्त कर देता है। इस गाइड के अंत तक आप .docx फ़ाइलें जेनरेट कर पाएंगे जिनमें पूरी तरह कार्यशील CommandButton कंट्रोल्स हों, जो Windows वातावरण में उपयोग के लिए तैयार हों।

## पूर्वापेक्षाएँ

शुरू करने से पहले सुनिश्चित करें कि आपके पास है:

- Java Development Kit (JDK) 8 या उससे नया स्थापित हो।
- Maven या कोई अन्य बिल्ड टूल जो डिपेंडेंसीज़ को मैनेज करे।
- Aspose.Words for Java लाइसेंस (या एक अस्थायी इवैल्यूएशन की) ताकि इवैल्यूएशन वाटरमार्क न आएँ।
- Java सिंटैक्स और ऑब्जेक्ट‑ओरिएंटेड प्रोग्रामिंग की बुनियादी समझ।

> **Pro tip:** अपने `pom.xml` में Aspose.Words Maven डिपेंडेंसी जोड़ें ताकि IDE क्लासेस को ऑटोमैटिकली रिजॉल्व कर सके:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.10</version> <!-- Use the latest version -->
</dependency>
```

## चरण 1: एक नया खाली दस्तावेज़ और `DocumentBuilder` बनाएं

`Document` क्लास मेमोरी में Word फ़ाइल का प्रतिनिधित्व करती है, जबकि `DocumentBuilder` दस्तावेज़ को एडिट करने के लिए एक फ्लुएंट API प्रदान करता है। दोनों ऑब्जेक्ट्स को इनिशियलाइज़ करने से आगे के संशोधनों के लिए दस्तावेज़ तैयार हो जाता है।

```java
import com.aspose.words.*;

public class ActiveXDemo {
    public static void main(String[] args) throws Exception {
        // Create an empty Word document
        Document document = new Document();

        // DocumentBuilder lets you add text, tables, and controls
        DocumentBuilder builder = new DocumentBuilder(document);
```

**यह क्यों महत्वपूर्ण है:**  
`DocumentBuilder` वर्तमान कर्सर पोजीशन को ट्रैक करता है, इसलिए कोई भी बाद का इन्सर्ट ऑपरेशन—जैसे कंट्रोल जोड़ना—बिल्कुल वहीँ दिखाई देगा जहाँ आप चाहते हैं।

## चरण 2: एक CommandButton ActiveX कंट्रोल डालें

Aspose.Words `Forms2OleControl` को ActiveX ऑब्जेक्ट्स के लिए एक्सपोज़ करता है। `insertForms2OleControl` मेथड को कंट्रोल टाइप की आवश्यकता होती है, जिसे आप `Forms2OleControlType` एनेमरेशन के माध्यम से निर्दिष्ट करते हैं।

```java
        // Insert a CommandButton ActiveX control at the current cursor location
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMAND_BUTTON);
```

**व्याख्या:**  
डाला गया कंट्रोल एक COM‑आधारित ऑब्जेक्ट है जिसे Word Windows वातावरण में दस्तावेज़ खोलने पर क्लिक करने योग्य बटन के रूप में रेंडर करेगा।

## चरण 3: बटन की प्रॉपर्टीज़ कॉन्फ़िगर करें

इन्सर्शन के बाद, आप बटन का नाम, कैप्शन, आकार और पोजीशन समायोजित कर सकते हैं। ये प्रॉपर्टीज़ कंट्रोल के लुक और व्यवहार को Word के भीतर प्रभावित करती हैं।

```java
        // Set the logical name used by VBA or external scripts
        commandButton.setName("cmdSubmit");

        // Text displayed on the button face
        commandButton.setCaption("Submit");

        // Position the button 100 points from the left margin and 150 points from the top
        commandButton.setLeft(100);
        commandButton.setTop(150);

        // Define the button’s dimensions (width × height) in points
        commandButton.setWidth(80);
        commandButton.setHeight(30);
```

**इन सेटिंग्स का महत्व:**  

- **Name** – VBA मैक्रोज़ को कंट्रोल रेफ़रेंस करने की अनुमति देता है (`ActiveDocument.Forms("cmdSubmit")`)।
- **Caption** – वह दृश्यमान लेबल निर्धारित करता है जिस पर उपयोगकर्ता क्लिक करते हैं।
- **Left / Top** – पेज मार्जिन के सापेक्ष प्लेसमेंट को नियंत्रित करता है।
- **Width / Height** – विभिन्न स्क्रीन रिज़ॉल्यूशन पर एक सुसंगत विज़ुअल साइज सुनिश्चित करता है।

## चरण 4: दस्तावेज़ सहेजें

`save` कॉल इन‑मेमोरी प्रतिनिधित्व को एक फिजिकल फ़ाइल में लिखता है। आप कोई भी सपोर्टेड फ़ॉर्मेट (`.docx`, `.doc`, `.pdf`, आदि) चुन सकते हैं। इस ट्यूटोरियल के लिए हम मूल Word फ़ॉर्मेट रखेंगे।

```java
        // Persist the document with the embedded ActiveX control
        document.save("output/ActiveXDemo.docx");
    }
}
```

**परिणाम:**  
`ActiveXDemo.docx` को Microsoft Word में खोलने पर **Submit** लेबल वाला एक CommandButton निर्दिष्ट कॉर्डिनेट्स पर दिखेगा। बटन पर क्लिक करने से डिफ़ॉल्ट व्यवहार ट्रिगर होगा (डिफ़ॉल्ट रूप से कोई VBA कोड संलग्न नहीं है)।

## पूर्ण स्रोत कोड

सभी हिस्सों को मिलाकर, पूरा, रन करने योग्य प्रोग्राम इस प्रकार दिखता है:

```java
import com.aspose.words.*;
import com.aspose.words.forms.*;

public class ActiveXDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document and a DocumentBuilder
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Step 2: Insert a CommandButton ActiveX control
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMAND_BUTTON);

        // Step 3: Configure the button's properties
        commandButton.setName("cmdSubmit");
        commandButton.setCaption("Submit");
        commandButton.setLeft(100);
        commandButton.setTop(150);
        commandButton.setWidth(80);
        commandButton.setHeight(30);

        // Step 4: Save the document with the ActiveX control
        document.save("output/ActiveXDemo.docx");
    }
}
```

### अपेक्षित आउटपुट

- `output` फ़ोल्डर में **ActiveXDemo.docx** नाम की फ़ाइल।
- जब Microsoft Word (Windows) में खोला जाए, तो दस्तावेज़ में परिभाषित पोजीशन पर क्लिक करने योग्य **Submit** बटन दिखेगा।
- बटन को चयनित, मूव किया जा सकता है, या Word UI (Developer → Properties) के माध्यम से VBA कोड से लिंक किया जा सकता है।

## सामान्य वैरिएशन्स को संभालना

| Scenario | Adjustment |
|----------|------------|
| **Save as .doc** (legacy format) | `document.save("ActiveXDemo.doc", SaveFormat.DOC);` |
| **Add an event handler** | Word Aspose.Words के माध्यम से ActiveX इवेंट्स को एक्सपोज़ नहीं करता। दस्तावेज़ जेनरेट होने के बाद आपको VBA कोड मैन्युअली जोड़ना होगा। |
| **Multiple controls** | विभिन्न `setName` और `setCaption` मानों के साथ इन्सर्ट/कॉन्फ़िगर ब्लॉक को दोहराएँ। |
| **Different control type (e.g., CheckBox)** | `insertForms2OleControl` कॉल में `Forms2OleControlType.CHECKBOX` का उपयोग करें। |
| **Non‑Windows platforms** | ActiveX कंट्रोल्स केवल Windows Word पर रेंडर होते हैं। क्रॉस‑प्लेटफ़ॉर्म समाधान के लिए कंटेंट कंट्रोल्स (`StructuredDocumentTag`) पर विचार करें। |

## सर्वोत्तम प्रैक्टिसेज़ और संभावित समस्याएँ

- **License early** – `Document` बनाने से पहले अपना Aspose.Words लाइसेंस रजिस्टर करें ताकि इवैल्यूएशन प्रॉम्प्ट न आएँ।
- **Coordinate system** – पोजीशन पॉइंट्स में मापी जाती है (1 pt = 1/72 in)। यदि आपका UI डिज़ाइन पिक्सेल या सेंटीमीटर में है तो उन्हें कन्वर्ट करें।
- **File paths** – आउटपुट डायरेक्टरी न होने पर `FileNotFoundException` से बचने के लिए एब्सोल्यूट पाथ या Java के `Paths` API का उपयोग करें।
- **Thread safety** – `Document` और `DocumentBuilder` थ्रेड‑सेफ़ नहीं हैं। यदि आप समानांतर में दस्तावेज़ जेनरेट कर रहे हैं तो प्रत्येक थ्रेड के लिए अलग इंस्टेंस बनाएँ।
- **Testing** – जेनरेटेड दस्तावेज़ को लक्ष्य Word संस्करण (जैसे Word 2016, Word 365) पर वेरिफ़ाई करें क्योंकि पुराने संस्करणों में ActiveX कंट्रोल्स अलग दिख सकते हैं।

## निष्कर्ष

यह **Aspose.Words ActiveX ट्यूटोरियल** दर्शाता है कि कैसे Java का उपयोग करके प्रोग्रामेटिकली एक CommandButton कंट्रोल को Word दस्तावेज़ में जोड़ा जाए। आपने सीखा:

1. `Document` और `DocumentBuilder` को इनिशियलाइज़ करना।
2. `Forms2OleControl` टाइप `COMMAND_BUTTON` को इन्सर्ट करना।
3. बटन का नाम, कैप्शन, आकार और पोजीशन सेट करना।
4. ActiveX कंट्रोल वाले .docx फ़ाइल को सहेजना।

अब आप अतिरिक्त कंट्रोल टाइप्स का अन्वेषण कर सकते हैं, VBA मैक्रो इंजेक्शन को ऑटोमेट कर सकते हैं, या ActiveX कंट्रोल्स को Aspose.Words की अन्य सुविधाओं जैसे मेल‑मर्ज और कंटेंट कंट्रोल्स के साथ संयोजित कर सकते हैं। विभिन्न लेआउट्स के साथ प्रयोग करें और जेनरेटेड दस्तावेज़ों को अपने बड़े Java‑आधारित रिपोर्टिंग पाइपलाइन में इंटीग्रेट करें।

---


## अगला आप क्या सीखें?

निम्नलिखित ट्यूटोरियल्स उन विषयों को कवर करते हैं जो इस गाइड में प्रदर्शित तकनीकों पर आधारित हैं। प्रत्येक संसाधन में पूर्ण कार्यशील कोड उदाहरण और चरण‑दर‑चरण व्याख्याएँ शामिल हैं, जिससे आप अतिरिक्त API फीचर्स में महारत हासिल कर सकें और अपने प्रोजेक्ट्स में वैकल्पिक इम्प्लीमेंटेशन अप्रोचेज़ का अन्वेषण कर सकें।

- [Using OLE Objects and ActiveX Controls in Aspose.Words for Java](/words/english/java/using-document-elements/using-ole-objects-and-activex/)
- [How to create form fields and add content using DocumentBuilder in Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Convert Word to RTF with Aspose.Words for Java Tutorial](/words/english/java/document-loading-and-saving/saving-documents-as-rtf-format/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}