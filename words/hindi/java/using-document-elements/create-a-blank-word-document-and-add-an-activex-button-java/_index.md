---
category: general
date: 2026-10-16
description: Java का उपयोग करके एक खाली Word दस्तावेज़ बनाएं और Aspose.Words के साथ
  ActiveX बटन जोड़ना, उसका कैप्शन सेट करना, तथा उसके आयाम समायोजित करना सीखें।
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- add activex button
- set button caption
- set button dimensions
language: hi
lastmod: 2026-10-16
og_description: Java के साथ एक खाली Word दस्तावेज़ बनाएं, फिर एक ActiveX बटन जोड़ें,
  उसका कैप्शन सेट करें, और Aspose.Words का उपयोग करके उसके आयाम निर्धारित करें।
og_image_alt: Screenshot showing a blank Word document with an ActiveX button inserted
og_title: एक खाली Word दस्तावेज़ बनाएं और एक ActiveX बटन एम्बेड करें – Java गाइड
schemas:
- author: Aspose
  dateModified: '2026-10-16'
  description: Create a blank Word document with Java and learn how to add an ActiveX
    button, set its caption, and adjust its dimensions using Aspose.Words.
  headline: Create a blank Word document and add an ActiveX button (Java)
  type: TechArticle
tags:
- Aspose.Words
- Java
- ActiveX
title: एक खाली Word दस्तावेज़ बनाएं और एक ActiveX बटन जोड़ें (Java)
url: /hi/java/using-document-elements/create-a-blank-word-document-and-add-an-activex-button-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# एक खाली Word दस्तावेज़ बनाएं और ActiveX बटन जोड़ें (Java)

यदि आपको प्रोग्रामेटिक रूप से **create a blank Word document** बनाना है, तो यह गाइड आपको Java और Aspose.Words के साथ इसे करने का तरीका दिखाता है। आप यह भी सीखेंगे कि **add an ActiveX button**, **set button caption**, और **set button dimensions** कैसे सेट करें ताकि नियंत्रण बिल्कुल वही दिखे जैसा आप चाहते हैं।

यह ट्यूटोरियल कवर करता है:

* Aspose.Words for Java के साथ एक खाली Word फ़ाइल को इनिशियलाइज़ करना।  
* एक ActiveX `CommandButton` नियंत्रण सम्मिलित करना।  
* बटन की कैप्शन और आकार को कॉन्फ़िगर करना।  
* अंतिम `.docx` फ़ाइल को सहेजना।  

आपके पास बेसिक Java ज्ञान और Aspose.Words for Java लाइब्रेरी का हालिया संस्करण होना चाहिए (कोड 23.9 और बाद के संस्करणों के साथ काम करता है)। कोई अतिरिक्त डिपेंडेंसीज़ की आवश्यकता नहीं है।

![Create a blank Word document with an ActiveX button](/images/activex-button-example.png){: .align-center alt="ActiveX बटन के साथ एक खाली Word दस्तावेज़ बनाएं"}

## Aspose.Words के साथ एक खाली Word दस्तावेज़ बनाएं

पहला कदम एक खाली `Document` ऑब्जेक्ट को इंस्टैंशिएट करना है। यह ऑब्जेक्ट मेमोरी में पूरे Word फ़ाइल का प्रतिनिधित्व करता है और संपादन के लिए `DocumentBuilder` क्लास प्रदान करता है।

```java
import com.aspose.words.*;

public class ActiveXButtonDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document
        Document doc = new Document();               // creates an empty .docx structure
        DocumentBuilder builder = new DocumentBuilder(doc);
        
        // The rest of the steps follow here...
```

**यह क्यों महत्वपूर्ण है:**  
एक खाली दस्तावेज़ बनाकर आपको एक साफ़ कैनवास मिलता है, जिससे कोई भी छिपी हुई स्टाइल या सेक्शन नहीं रहता जो बाद में लेआउट गणनाओं में बाधा डाल सके।

## दस्तावेज़ में ActiveX बटन जोड़ें

Aspose.Words आपको `Forms2OleControl` क्लास के माध्यम से लेगेसी ActiveX कंट्रोल एम्बेड करने की सुविधा देता है। नीचे दिया गया कोड वर्तमान कर्सर पोजीशन पर एक `CommandButton` कंट्रोल इंसर्ट करता है।

```java
        // Step 2: Insert an ActiveX CommandButton control
        Forms2OleControl commandButton = builder.insertForms2OleControl();

        // Define the exact ActiveX class name (CommandButton)
        commandButton.setOleClassName("Forms.CommandButton.1");
```

**टिप:** `setOleClassName` वैल्यू `"Forms.CommandButton.1"` मानक Microsoft Forms बटन का ProgID है। अलग ProgID (जैसे `"Forms.CheckBox.1"`) उपयोग करने पर अलग कंट्रोल टाइप इंसर्ट होगा।

## बटन कैप्शन सेट करें

कैप्शन वह टेक्स्ट है जो बटन के फेस पर दिखता है। आप इसे दस्तावेज़ सहेजने से पहले किसी भी समय बदल सकते हैं।

```java
        // Step 3: Set the button's caption
        commandButton.setCaption("Click Me");
```

**आपको यह क्यों चाहिए:** उपयोगकर्ता तभी कंट्रोल को समझते हैं जब उसका उद्देश्य स्पष्ट हो। एक अर्थपूर्ण कैप्शन सेट करने से उपयोगिता में सुधार होता है, विशेषकर जब दस्तावेज़ Windows पर Word में खोला जाता है।

## बटन के आयाम सेट करें

पोजीशन और साइज पॉइंट्स में निर्दिष्ट होते हैं (1 पॉइंट = 1/72 इंच)। अपने लेआउट के अनुसार मान समायोजित करें।

```java
        // Step 4: Define button size and location
        commandButton.setLeft(100);    // distance from the left edge of the page
        commandButton.setTop(200);     // distance from the top edge of the page
        commandButton.setWidth(120);   // width of the button
        commandButton.setHeight(30);   // height of the button
```

**सामान्य वैरिएशन:**

| परिदृश्य | समायोजन |
|----------|------------|
| टच स्क्रीन के लिए बड़ा बटन | `setWidth` और `setHeight` को अनुपातिक रूप से बढ़ाएँ |
| पेज पर बटन को केंद्र में रखें | `left = (pageWidth - width) / 2` की गणना करें |
| कॉलम में कई बटन | प्रत्येक नए बटन के लिए `setTop` को इन्क्रिमेंट करें |

## ActiveX बटन वाला दस्तावेज़ सहेजें

अंत में, दस्तावेज़ को डिस्क पर लिखें। `.docx` फॉर्मेट Windows संस्करण के Microsoft Word के लिए ActiveX कंट्रोल को संरक्षित रखता है।

```java
        // Step 5: Save the document
        doc.save("ActiveXCommandButton.docx");
    }
}
```

**अपेक्षित परिणाम:** `ActiveXCommandButton.docx` को Word (Windows) में खोलने पर एक खाली पेज दिखेगा जिसमें **Click Me** लेबल वाला क्लिकेबल बटन बाएँ मार्जिन से 100 pt और शीर्ष मार्जिन से 200 pt की दूरी पर स्थित होगा।

## पूर्ण, चलाने योग्य उदाहरण

नीचे दिया गया पूरा क्लास अपने IDE में कॉपी करें, प्रोजेक्ट क्लासपाथ में Aspose.Words for Java JAR जोड़ें, और इसे चलाएँ।

```java
import com.aspose.words.*;

public class ActiveXButtonDemo {
    public static void main(String[] args) throws Exception {
        // Create a new blank document
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert an ActiveX CommandButton control
        Forms2OleControl commandButton = builder.insertForms2OleControl();
        commandButton.setOleClassName("Forms.CommandButton.1");

        // Set button caption
        commandButton.setCaption("Click Me");

        // Set button dimensions and position
        commandButton.setLeft(100);    // points from left edge
        commandButton.setTop(200);     // points from top edge
        commandButton.setWidth(120);   // width in points
        commandButton.setHeight(30);   // height in points

        // Save the document
        doc.save("ActiveXCommandButton.docx");
    }
}
```

प्रोग्राम चलाने पर कार्य निर्देशिका में `ActiveXCommandButton.docx` बन जाएगा। इसे Microsoft Word (Windows) में खोलें और देखें कि बटन ठीक उसी तरह कॉन्फ़िगर किया गया है जैसा आपने सेट किया था।

## इस दृष्टिकोण की सिफ़ारिश क्यों की जाती है

* **सरलता:** केवल कोर Aspose.Words API का उपयोग किया गया है; कोई COM इंटरऑप या अतिरिक्त लाइब्रेरी की आवश्यकता नहीं।  
* **पोर्टेबिलिटी:** कोड किसी भी प्लेटफ़ॉर्म पर चल सकता है जो Java सपोर्ट करता है, हालांकि ActiveX कंट्रोल स्वयं केवल Windows संस्करण के Word में काम करता है।  
* **मेंटेनेबिलिटी:** सभी प्रॉपर्टीज़ (कैप्शन, आयाम, पोजीशन) स्पष्ट, स्व-डॉक्यूमेंटेड मेथड्स के माध्यम से सेट की गई हैं, जिससे भविष्य में बदलाव आसान होते हैं।

## सामान्य समस्याएँ और उनका समाधान

| समस्या | समाधान |
|---------|------------|
| बटन macOS या Linux पर Word में नहीं दिखता | ActiveX कंट्रोल केवल Windows के लिए होते हैं। क्रॉस‑प्लेटफ़ॉर्म दस्तावेज़ों के लिए कोई अन्य कंट्रोल (जैसे कंटेंट कंट्रोल) उपयोग करें। |
| कैप्शन कट रहा है | बटन की चौड़ाई को टेक्स्ट के लिए पर्याप्त बनाएं; `setWidth` बढ़ाएँ या छोटा कैप्शन उपयोग करें। |
| बटन अन्य सामग्री के ऊपर ओवरलैप हो रहा है | `setTop` और `setLeft` मान समायोजित करें, या कंट्रोल से पहले एक नया पैराग्राफ इंसर्ट करके उसे अपना स्पेस दें। |

## अगले कदम

अब जब आप **एक खाली Word दस्तावेज़ बना सकते हैं**, **ActiveX बटन जोड़ सकते हैं**, **बटन कैप्शन सेट कर सकते हैं**, और **बटन आयाम सेट कर सकते हैं**, तो आप आगे कर सकते हैं:

* VBA मैक्रो के माध्यम से इवेंट‑हैंडलिंग कोड जोड़ना (एक मैक्रो मॉड्यूल एम्बेड करना आवश्यक)।  
* फॉर्म‑जैसे दस्तावेज़ों के लिए टेबल लेआउट में कई कंट्रोल इंसर्ट करना।  
* क्रॉस‑प्लेटफ़ॉर्म फ़ॉर्म समाधान के लिए Aspose.Words के **FormField** API का उपयोग करना।

विभिन्न आकार, पोजीशन और कैप्शन के साथ प्रयोग करें ताकि आपका दस्तावेज़ डिज़ाइन पूरी तरह फिट हो। Happy coding!

## आप अगला क्या सीखें?

निम्नलिखित ट्यूटोरियल्स उन विषयों को कवर करते हैं जो इस गाइड में दिखाए गए तकनीकों पर आधारित हैं। प्रत्येक रिसोर्स में पूर्ण कार्यशील कोड उदाहरण और चरण‑दर‑चरण व्याख्याएँ शामिल हैं, जिससे आप अतिरिक्त API फीचर्स में महारत हासिल कर सकें और अपने प्रोजेक्ट्स में वैकल्पिक इम्प्लीमेंटेशन अप्रोचेज़ का अन्वेषण कर सकें।

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [How to create form fields and add content using DocumentBuilder in Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Add a watermark to a document using Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-watermarks-to-documents/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}