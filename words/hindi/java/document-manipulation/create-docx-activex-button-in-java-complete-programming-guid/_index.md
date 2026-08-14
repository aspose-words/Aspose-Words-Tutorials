---
category: general
date: 2026-08-14
description: Aspose.Words के साथ जावा में docx ActiveX बटन बनाएं। जानिए कैसे प्रोग्रामेटिकली
  Word में फ़ॉर्म बटन जोड़ें और दस्तावेज़ को सहेजें।
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create docx ActiveX button
- add form button word
language: hi
lastmod: 2026-08-14
og_description: Aspose.Words का उपयोग करके जावा में docx ActiveX बटन बनाएं। यह गाइड
  आपको दिखाता है कि Word में फॉर्म बटन कैसे जोड़ें, उसे कॉन्फ़िगर करें, और फ़ाइल को
  सहेजें।
og_image_alt: Screenshot of a Word document containing an ActiveX CommandButton created
  with Java
og_title: जावा में docx ActiveX बटन बनाएं – चरण‑दर‑चरण ट्यूटोरियल
schemas:
- author: Aspose
  dateModified: '2026-08-14'
  description: Create docx ActiveX button in Java with Aspose.Words. Learn how to
    add a form button in Word programmatically and save the document.
  headline: Create docx ActiveX button in Java – complete programming guide
  type: TechArticle
- description: Create docx ActiveX button in Java with Aspose.Words. Learn how to
    add a form button in Word programmatically and save the document.
  name: Create docx ActiveX button in Java – complete programming guide
  steps:
  - name: Set up the project and import Aspose.Words
    text: 'Add the Aspose.Words dependency to your `pom.xml` if you use Maven:'
  - name: Create a new blank document
    text: Instantiate a `Document` object, which represents an empty Word file ready
      to receive content.
  - name: Initialize a DocumentBuilder
    text: '`DocumentBuilder` provides a fluent interface for inserting text, images,
      and controls. Attach it to the document you just created.'
  - name: Insert an ActiveX CommandButton control
    text: Use the `insertForms2OleControl` method to embed an ActiveX `CommandButton`.
      This method returns a `Forms2OleControl` instance that you can further configure.
  - name: Configure the button’s properties
    text: Set the control’s name, caption, and layout attributes. These values determine
      how the button appears in Word and how you can reference it later via VBA or
      automation scripts.
  - name: Save the document
    text: Finally, write the document to disk. Use the `.docx` extension to keep the
      file in the modern Office Open XML format.
  type: HowTo
tags:
- ActiveX
- Java
- Aspose.Words
- Word automation
title: जावा में docx ActiveX बटन बनाएं – पूर्ण प्रोग्रामिंग गाइड
url: /hi/java/document-manipulation/create-docx-activex-button-in-java-complete-programming-guid/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Java में docx ActiveX बटन बनाएं – पूर्ण प्रोग्रामिंग गाइड

यदि आपको Java में **docx ActiveX बटन बनाना** है, तो यह गाइड आपको पूरी प्रक्रिया से गुज़राएगा। आप देखेंगे कि Word में फ़ॉर्म बटन कैसे जोड़ें, उसकी प्रॉपर्टीज़ कैसे कॉन्फ़िगर करें, और तैयार‑से‑उपयोग .docx फ़ाइल कैसे बनाएं।

लेगेसी Word फ़ॉर्म्स को ऑटोमेट करने के दौरान ActiveX कंट्रोल्स के साथ काम करना एक सामान्य आवश्यकता है। इस ट्यूटोरियल में आप Aspose.Words for Java लाइब्रेरी का उपयोग करके **फ़ॉर्म बटन वर्ड** दस्तावेज़ों को जोड़ना सीखेंगे, ताकि आप मैन्युअल एडिटिंग के बिना इंटरैक्टिव कंट्रोल्स एम्बेड कर सकें।

## आपको क्या चाहिए

* Java 17 या बाद का संस्करण (कोड पहले के संस्करणों के साथ भी कंपाइल होता है, लेकिन Java 17 की सलाह दी जाती है)।
* Aspose.Words for Java 23.10 या नया – Aspose वेबसाइट से JAR डाउनलोड करें या Maven डिपेंडेंसी जोड़ें।
* एक IDE (IntelliJ IDEA, Eclipse, या VS Code) या एक साधारण टेक्स्ट एडिटर और कमांड‑लाइन बिल्ड टूल्स।
* Java सिंटैक्स और ऑब्जेक्ट‑ओरिएंटेड प्रोग्रामिंग का बुनियादी ज्ञान।

## Aspose.Words के साथ docx ActiveX बटन कैसे बनाएं

निम्नलिखित चरण **docx ActiveX बटन** ऑब्जेक्ट्स बनाने और उन्हें Word दस्तावेज़ में एम्बेड करने के लिए आवश्यक सटीक क्रम दिखाते हैं।

### चरण 1: प्रोजेक्ट सेट अप करें और Aspose.Words इम्पोर्ट करें

`pom.xml` में Aspose.Words डिपेंडेंसी जोड़ें यदि आप Maven उपयोग करते हैं:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.10</version>
    <classifier>jdk17</classifier>
</dependency>
```

या, यदि आप Gradle पसंद करते हैं:

```gradle
implementation 'com.aspose:aspose-words:23.10:jdk17'
```

डिपेंडेंसी रेजॉल्व होने के बाद, अपने Java स्रोत फ़ाइल में आवश्यक क्लासेज़ इम्पोर्ट करें:

```java
import com.aspose.words.Document;
import com.aspose.words.DocumentBuilder;
import com.aspose.words.forms.Forms2OleControl;
import com.aspose.words.forms.Forms2OleControlType;
```

इन इम्पोर्ट्स से आपको `Document`, `DocumentBuilder`, और `Forms2OleControl` API तक पहुँच मिलती है, जिसका उपयोग ActiveX कंट्रोल्स इन्सर्ट करने के लिए किया जाता है।

### चरण 2: नया खाली दस्तावेज़ बनाएं

`Document` ऑब्जेक्ट को इंस्टैंशिएट करें, जो एक खाली Word फ़ाइल का प्रतिनिधित्व करता है, जो सामग्री प्राप्त करने के लिए तैयार है।

```java
// Step 2: Create a new blank document
Document document = new Document();
```

पहले दस्तावेज़ बनाना यह सुनिश्चित करता है कि बाद का बिल्डर एक साफ़ कैनवास पर काम करे।

### चरण 3: DocumentBuilder को इनिशियलाइज़ करें

`DocumentBuilder` टेक्स्ट, इमेज और कंट्रोल्स इन्सर्ट करने के लिए एक फ्लुएंट इंटरफ़ेस प्रदान करता है। इसे उस दस्तावेज़ से जोड़ें जो आपने अभी बनाया है।

```java
// Step 3: Initialize a DocumentBuilder to construct the document content
DocumentBuilder builder = new DocumentBuilder(document);
```

बिल्डर दस्तावेज़ के भीतर वर्तमान कर्सर पोज़िशन को ट्रैक करता है, इसलिए अगला इन्सर्शन ठीक उसी जगह पर होता है जहाँ आपको चाहिए।

### चरण 4: ActiveX CommandButton कंट्रोल इन्सर्ट करें

`insertForms2OleControl` मेथड का उपयोग करके ActiveX `CommandButton` एम्बेड करें। यह मेथड एक `Forms2OleControl` इंस्टेंस रिटर्न करता है जिसे आप आगे कॉन्फ़िगर कर सकते हैं।

```java
// Step 4: Insert an ActiveX CommandButton control into the document
Forms2OleControl commandButton = builder.insertForms2OleControl(
        Forms2OleControlType.COMMAND_BUTTON);
```

इस चरण पर .docx फ़ाइल में बटन के लिए एक प्लेसहोल्डर मौजूद है, लेकिन अभी तक इसमें कोई विज़ुअल कैप्शन या आकार नहीं है।

### चरण 5: बटन की प्रॉपर्टीज़ कॉन्फ़िगर करें

कंट्रोल का नाम, कैप्शन, और लेआउट एट्रिब्यूट सेट करें। ये मान निर्धारित करते हैं कि बटन Word में कैसे दिखेगा और आप बाद में VBA या ऑटोमेशन स्क्रिप्ट्स के माध्यम से उसे कैसे रेफ़र करेंगे।

```java
// Step 5: Configure the button's properties (name, caption, size, and position)
commandButton.setName("btnSubmit");          // internal name used by VBA
commandButton.setCaption("Submit");          // text shown on the button
commandButton.setTop(100);                  // distance from the top of the page (points)
commandButton.setLeft(150);                 // distance from the left margin (points)
commandButton.setWidth(80);                 // button width (points)
commandButton.setHeight(30);                // button height (points)
```

> **प्रो टिप:** Word पोज़िशन को पॉइंट्स में मापता है (1 pt ≈ 1/72 in)। बटन को आसपास की सामग्री के साथ संरेखित करने के लिए `setTop` और `setLeft` को समायोजित करें।

### चरण 6: दस्तावेज़ को सेव करें

अंत में, दस्तावेज़ को डिस्क पर लिखें। फ़ाइल को आधुनिक Office Open XML फॉर्मेट में रखने के लिए `.docx` एक्सटेंशन का उपयोग करें।

```java
// Step 6: Save the document containing the ActiveX button
String outputPath = "C:/temp/ActiveXButton.docx";
document.save(outputPath);
System.out.println("Document saved to " + outputPath);
```

जब आप परिणामी फ़ाइल को Microsoft Word में खोलेंगे, तो आप एक **Submit** बटन देखेंगे जो आपने निर्दिष्ट कोऑर्डिनेट्स पर स्थित है। Word में बटन पर क्लिक करने से कोई कार्रवाई नहीं होगी जब तक आप VBA कोड नहीं जोड़ते, लेकिन यह कंट्रोल फ़ॉर्म‑आधारित वर्कफ़्लोज़ के लिए पूरी तरह कार्यात्मक है।

## सामान्य प्रश्न और किनारे के मामले

| प्रश्न | उत्तर |
|----------|--------|
| **क्या मुझे कोई विशेष Word संस्करण चाहिए?** | ActiveX कंट्रोल्स Windows पर Microsoft Word के डेस्कटॉप संस्करण में समर्थित हैं। ये Mac के लिए Word या Word Online में उपलब्ध नहीं हैं। |
| **क्या मैं इसे `.doc` फ़ाइलों के साथ उपयोग कर सकता हूँ?** | हां। दस्तावेज़ को `.doc` एक्सटेंशन के साथ सेव करें (`document.save("ActiveXButton.doc")`)। वही API पुराने बाइनरी फ़ॉर्मेट के लिए भी काम करता है। |
| **अगर बटन नहीं दिखता तो क्या करें?** | सुनिश्चित करें कि **File → Options → Trust Center → Trust Center Settings → ActiveX Settings** ActiveX कंट्रोल्स की अनुमति देता है। साथ ही जाँचें कि दस्तावेज़ “Protected View” में नहीं खुला है। |
| **क्या मैं अन्य ActiveX कंट्रोल्स जोड़ सकता हूँ?** | बिल्कुल। `Forms2OleControlType.COMMAND_BUTTON` को `Forms2OleControlType.CHECK_BOX`, `RADIO_BUTTON` आदि से बदलें। |
| **क्या आकार की कोई सीमा है?** | कंट्रोल का आकार केवल पेज लेआउट द्वारा सीमित है। बहुत बड़े आयाम लेआउट ओवरफ़्लो का कारण बन सकते हैं। |

## पूर्ण, चलाने योग्य उदाहरण

नीचे एक पूर्ण Java क्लास दिया गया है जिसे आप कॉपी, कंपाइल और रन कर सकते हैं। इसमें सभी इम्पोर्ट्स, मुख्य मेथड, और स्पष्टता के लिए इनलाइन कमेंट्स शामिल हैं।

```java
package com.example.wordactive;

import com.aspose.words.Document;
import com.aspose.words.DocumentBuilder;
import com.aspose.words.forms.Forms2OleControl;
import com.aspose.words.forms.Forms2OleControlType;

public class ActiveXButtonDemo {
    public static void main(String[] args) {
        try {
            // Create a new blank document
            Document document = new Document();

            // Initialize DocumentBuilder
            DocumentBuilder builder = new DocumentBuilder(document);

            // Insert an ActiveX CommandButton control
            Forms2OleControl commandButton = builder.insertForms2OleControl(
                    Forms2OleControlType.COMMAND_BUTTON);

            // Configure button properties
            commandButton.setName("btnSubmit");
            commandButton.setCaption("Submit");
            commandButton.setTop(100);   // points from top
            commandButton.setLeft(150);  // points from left
            commandButton.setWidth(80);  // width in points
            commandButton.setHeight(30); // height in points

            // Save the document
            String outputPath = "ActiveXButton.docx";
            document.save(outputPath);
            System.out.println("Document saved successfully to " + outputPath);
        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}
```

**अपेक्षित परिणाम:** प्रोग्राम चलाने के बाद, `ActiveXButton.docx` कार्य निर्देशिका में दिखाई देगा। इसे Microsoft Word में खोलने पर पहली पृष्ठ के शीर्ष‑बाएँ हिस्से के पास स्थित एक क्लिक करने योग्य **Submit** बटन दिखेगा।

## निष्कर्ष

अब आप जानते हैं कि Aspose.Words का उपयोग करके Java में **docx ActiveX बटन** ऑब्जेक्ट्स कैसे बनाते हैं, और आपने देखा कि प्रोग्रामेटिक रूप से **फ़ॉर्म बटन वर्ड** दस्तावेज़ कैसे जोड़ते हैं। चरण—प्रोजेक्ट सेट अप करना, दस्तावेज़ बनाना, कंट्रोल इन्सर्ट करना, उसकी प्रॉपर्टीज़ कॉन्फ़िगर करना, और सेव करना—शुरू से अंत तक पूरे वर्कफ़्लो को कवर करते हैं।

आगे, आप निम्नलिखित का अन्वेषण कर सकते हैं:

* बटन क्लिक पर प्रतिक्रिया देने वाले VBA मैक्रो जोड़ना।
* चेक बॉक्स या लिस्ट बॉक्स जैसे अन्य ActiveX कंट्रोल्स एम्बेड करना।
* कई इंटरैक्टिव एलिमेंट्स वाले मल्टी‑पेज फ़ॉर्म्स के जनरेशन को ऑटोमेट करना।

अपने विशिष्ट फ़ॉर्म डिज़ाइन आवश्यकताओं के अनुसार आकार, पोज़िशन, और कैप्शन के साथ प्रयोग करने में संकोच न करें। कोडिंग का आनंद लें!

## आगे आप क्या सीखें?

निम्नलिखित ट्यूटोरियल्स उन निकट संबंधित विषयों को कवर करते हैं जो इस गाइड में दिखाए गए तकनीकों पर आधारित हैं। प्रत्येक संसाधन में पूर्ण कार्यशील कोड उदाहरण और चरण‑दर‑चरण व्याख्याएँ शामिल हैं, जो आपको अतिरिक्त API फीचर्स में महारत हासिल करने और अपने प्रोजेक्ट्स में वैकल्पिक इम्प्लीमेंटेशन अप्रोचेज़ का अन्वेषण करने में मदद करती हैं।

- [Aspose.Words for Java में DocumentBuilder का उपयोग करके फ़ॉर्म फ़ील्ड्स बनाना और कंटेंट जोड़ना](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Aspose.Words for Java का उपयोग करके HTML लोड करना और DOCX के रूप में सेव करना](/words/english/java/document-loading-and-saving/loading-and-saving-html-documents/)
- [Aspose.Words for Java के साथ PDF दस्तावेज़ बनाना | Document Processing API](/words/english/java/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}