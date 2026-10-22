---
category: general
date: 2026-07-16
description: Aspose.Words for Java का उपयोग करके Word दस्तावेज़ में बटन का आकार प्रोग्रामेटिकली
  सेट करें। जानें कैसे ActiveX बटन डालें, बटन का स्थान सेट करें और अधिक।
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- set button size
- insert activex button
- programmatically add button
- set button location
- create word document button
language: hi
lastmod: 2026-07-16
og_description: जावा का उपयोग करके वर्ड दस्तावेज़ में बटन का आकार सेट करें। यह चरण‑दर‑चरण
  गाइड दिखाता है कि कैसे एक्टिवएक्स बटन डालें, बटन का स्थान सेट करें, और प्रोग्रामेटिक
  रूप से बटन जोड़ें।
og_image_alt: Screenshot of a Word document where the button size has been set using
  Aspose.Words for Java
og_title: Java के साथ Word में बटन का आकार सेट करें – पूर्ण Aspose.Words ट्यूटोरियल
schemas:
- author: Aspose
  dateModified: '2026-07-16'
  description: Set button size programmatically in a Word document using Aspose.Words
    for Java. Learn how to insert ActiveX button, set button location and more.
  headline: Set Button Size in Word with Java – Complete Aspose.Words Guide
  type: TechArticle
- description: Set button size programmatically in a Word document using Aspose.Words
    for Java. Learn how to insert ActiveX button, set button location and more.
  name: Set Button Size in Word with Java – Complete Aspose.Words Guide
  steps:
  - name: Expected Output Screenshot
    text: '![Word document showing the inserted button with the set button size](https://example.com/images/set-button-size.png
      "Screenshot of a Word file where the button size has been set using Aspose.Words
      for Java")'
  - name: “Can I set the button size using centimeters instead of points?”
    text: Word’s API only accepts points, but you can convert centimeters to points
      (`points = cm * 28.3465`). Write a small helper method if you prefer metric
      units.
  - name: “What if I need the button to appear on a specific page?”
    text: After inserting the button, you can move the cursor to a particular page
      using `builder.moveToPage(pageNumber)`. Insert the control right after the move,
      then set its location as shown above.
  - name: “Does this work with .doc (Word 97‑2003) files?”
    text: Yes—Aspose.Words automatically handles older formats. Just change the file
      extension in `doc.save("Demo.doc")`.
  type: HowTo
tags:
- Aspose.Words
- Java
- ActiveX
- Word automation
title: जावा के साथ वर्ड में बटन आकार सेट करें – पूर्ण Aspose.Words गाइड
url: /hi/java/using-document-elements/set-button-size-in-word-with-java-complete-aspose-words-guid/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Set Button Size in Word with Java – Complete Aspose.Words Guide

क्या आपने कभी सोचा है कि **बटन का आकार** Word फ़ाइल में UI खोले बिना कैसे सेट किया जाए? आप अकेले नहीं हैं। जब आपको ऑन‑द‑फ़्लाई फ़ॉर्म‑फ़िल्डेड डॉक्यूमेंट बनाना हो—जैसे कि “Submit” बटन वाला ऑनबोर्डिंग पैकेट—तो इसे प्रोग्रामेटिकली करना मैन्युअल काम में कई घंटे बचा सकता है।

इस ट्यूटोरियल में हम **ActiveX बटन डालना**, उसके आयाम सेट करना, सही जगह पर पोज़िशन करना, और अंत में फ़ाइल सेव करना के सटीक चरणों को देखेंगे। अंत तक आप **प्रोग्रामेटिकली बटन** कंट्रोल को किसी भी Word डॉक्यूमेंट में Aspose.Words for Java का उपयोग करके जोड़ पाएँगे।

## Prerequisites – What You Need Before You Start

- **Java Development Kit (JDK) 8+** – कोड किसी भी हालिया JDK पर चलता है।  
- **Aspose.Words for Java** लाइब्रेरी (आधिकारिक साइट से नवीनतम JAR डाउनलोड करें)।  
- आपका **IDE**—IntelliJ IDEA, Eclipse, या साधारण टेक्स्ट एडिटर—जो भी हो।  
- Java सिंटैक्स की बुनियादी समझ; Word‑ऑटोमेशन का गहरा ज्ञान आवश्यक नहीं।

> *Pro tip:* Aspose.Words JAR को अपने प्रोजेक्ट की classpath में रखें, नहीं तो `com.aspose.words.*` इम्पोर्ट करने पर `ClassNotFoundException` मिलेगा।

## Step 1: Create a New Word Document

सबसे पहले हम एक खाली डॉक्यूमेंट और एक `DocumentBuilder` बनाते हैं। बिल्डर को आप ऐसी पेन समझें जो फ़ाइल के अंदर कुछ भी ड्रॉ कर सके।

```java
import com.aspose.words.*;

public class InsertCommandButtonDemo {
    public static void main(String[] args) throws Exception {
        // Create an empty document.
        Document doc = new Document();

        // DocumentBuilder gives us a fluent API to add content.
        DocumentBuilder builder = new DocumentBuilder(doc);
```

> **Why this matters:** `Document` ऑब्जेक्ट पूरी .docx फ़ाइल को दर्शाता है, जबकि `DocumentBuilder` वह कार्यकर्ता है जो पैराग्राफ, टेबल, और—हां—ActiveX कंट्रोल्स डालने की सुविधा देता है।

## Step 2: Insert ActiveX Button – The “Insert ActiveX Button” Moment

अब हम वास्तव में **activex बटन** डॉक्यूमेंट में डालते हैं। Aspose.Words एक सुविधाजनक मेथड `insertForms2OleControl` प्रदान करता है जो `Forms2OleControl` ऑब्जेक्ट रिटर्न करता है।

```java
        // Insert an ActiveX CommandButton control.
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMAND_BUTTON);
        commandButton.setName("cmdSubmit");   // Programmatic name.
        commandButton.setCaption("Submit");   // Text shown on the button.
```

> *What’s happening under the hood?* `Forms2OleControlType.COMMAND_BUTTON` Word को बताता है कि हमें क्लासिक CommandButton चाहिए, वही जो आप UI के Developer टैब से ड्रॉप करते हैं।

## Step 3: Set Button Size and Location – The Core “Set Button Size” Logic

यहीं पर मुख्य कीवर्ड काम आता है। हम **बटन का आकार सेट** करेंगे और साथ ही **बटन का स्थान सेट** करेंगे ताकि कंट्रोल पेज पर ठीक उसी जगह दिखे जहाँ हम चाहते हैं।

```java
        // Position the button (distance from the left/top edges in points).
        commandButton.setLeft(100);   // 100 points from the left margin.
        commandButton.setTop(150);    // 150 points from the top margin.

        // Set the button's dimensions.
        commandButton.setWidth(80);   // Width = 80 points.
        commandButton.setHeight(30);  // Height = 30 points.
```

> **Why you should care:** पॉइंट्स Word में मूल माप इकाई है (1 पॉइंट = 1/72 इंच)। `setLeft`, `setTop`, `setWidth`, और `setHeight` को एडजस्ट करके आप पिक्सेल‑परफ़ेक्ट कंट्रोल प्राप्त कर सकते हैं—अब “स्क्रीन पर ठीक लगता है लेकिन प्रिंटर पर नहीं” जैसी समस्या नहीं रहेगी।

> *Common pitfall:* चौड़ाई या ऊँचाई में से कोई एक सेट न करने पर बटन डिफ़ॉल्ट आकार में रह जाता है, जो क्लिक करने के लिए बहुत छोटा हो सकता है। हमेशा दोनों को निर्दिष्ट करें।

## Step 4: Save the Document – “Create Word Document Button” Completed

अंत में हम फ़ाइल को डिस्क पर लिखते हैं। नाम से स्पष्ट है कि हम **Word डॉक्यूमेंट बटन** बना रहे हैं।

```java
        // Persist the document to the file system.
        doc.save("CommandButtonDemo.docx");
    }
}
```

जब आप `CommandButtonDemo.docx` को Microsoft Word में खोलेंगे, तो आपको बाएँ किनारे से 100 pt और ऊपर से 150 pt की दूरी पर **Submit** बटन दिखाई देगा, जिसका आकार 80 × 30 pt होगा। UI में इसे क्लिक करने पर डिफ़ॉल्ट ActiveX व्यवहार चलेगा (जिसे बाद में VBA से कनेक्ट किया जा सकता है)।

### Expected Output Screenshot

![Word document showing the inserted button with the set button size](https://example.com/images/set-button-size.png "Screenshot of a Word file where the button size has been set using Aspose.Words for Java")

*Alt text:* set button size in a Word document using Java

## Step 5 (Optional): Add More Controls or Style the Button

यदि आपको एक ही Submit बटन से अधिक **प्रोग्रामेटिकली बटन** कंट्रोल जोड़ने हैं, तो बस नया नाम और कैप्शन के साथ इन्सर्शन ब्लॉक दोहराएँ। आप फ़ॉन्ट, बैकग्राउंड कलर बदल सकते हैं, या बाद में VBA मैक्रो बाइंड कर सकते हैं।

```java
        // Example: Adding a Cancel button next to Submit.
        Forms2OleControl cancelBtn = builder.insertForms2OleControl(
                Forms2OleControlType.COMMAND_BUTTON);
        cancelBtn.setName("cmdCancel");
        cancelBtn.setCaption("Cancel");
        cancelBtn.setLeft(190);   // Position it 90 points to the right of Submit.
        cancelBtn.setTop(150);
        cancelBtn.setWidth(80);
        cancelBtn.setHeight(30);
```

> *Tip:* प्रोफेशनल लुक के लिए सभी बटन के आयाम समान रखें। एक तेज़ तरीका है कि चौड़ाई/ऊँचाई को कॉन्स्टैंट्स में स्टोर करें।

## Common Questions & Edge Cases

### “Can I set the button size using centimeters instead of points?”
Word की API केवल पॉइंट्स को स्वीकार करती है, लेकिन आप सेंटीमीटर को पॉइंट्स में बदल सकते हैं (`points = cm * 28.3465`)। यदि आप मीट्रिक यूनिट पसंद करते हैं तो एक छोटा हेल्पर मेथड लिखें।

### “What if I need the button to appear on a specific page?”
बटन डालने के बाद आप `builder.moveToPage(pageNumber)` से कर्सर को इच्छित पेज पर ले जा सकते हैं। फिर कंट्रोल को इन्सर्ट करें और ऊपर दिखाए अनुसार लोकेशन सेट करें।

### “Does this work with .doc (Word 97‑2003) files?”
हां—Aspose.Words स्वतः पुराने फ़ॉर्मेट को हैंडल करता है। सिर्फ फ़ाइल एक्सटेंशन को `doc.save("Demo.doc")` में बदल दें।

## Full, Runnable Example

नीचे पूरा प्रोग्राम दिया गया है जिसे आप किसी भी Java क्लास में कॉपी‑पेस्ट करके तुरंत चला सकते हैं (मान लीजिए Aspose.Words JAR क्लासपाथ में है)।

```java
import com.aspose.words.*;

public class InsertCommandButtonDemo {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Create a blank document.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Insert the first ActiveX CommandButton.
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMAND_BUTTON);
        commandButton.setName("cmdSubmit");
        commandButton.setCaption("Submit");

        // 3️⃣ Set button location and size – the core set button size logic.
        commandButton.setLeft(100);
        commandButton.setTop(150);
        commandButton.setWidth(80);
        commandButton.setHeight(30);

        // 4️⃣ (Optional) Add a second button for illustration.
        Forms2OleControl cancelBtn = builder.insertForms2OleControl(
                Forms2OleControlType.COMMAND_BUTTON);
        cancelBtn.setName("cmdCancel");
        cancelBtn.setCaption("Cancel");
        cancelBtn.setLeft(190);
        cancelBtn.setTop(150);
        cancelBtn.setWidth(80);
        cancelBtn.setHeight(30);

        // 5️⃣ Save the document – you’ve now created a Word document button.
        doc.save("CommandButtonDemo.docx");
    }
}
```

प्रोग्राम चलाएँ, जनरेटेड `CommandButtonDemo.docx` खोलें, और दो ठीक‑से‑आकार के बटन देखेंगे जो इंटरैक्शन के लिए तैयार हैं।

## Conclusion – You’ve Mastered Setting Button Size in Word

हमने **बटन का आकार सेट** और **बटन का स्थान सेट** करने के लिए Aspose.Words for Java का उपयोग करके एक पूर्ण, एंड‑टू‑एंड समाधान देखा। इन चरणों को फॉलो करके आप **activex बटन डालना**, **प्रोग्रामेटिकली बटन** कंट्रोल जोड़ना, और अंततः **Word डॉक्यूमेंट बटन** बनाना सीख गए हैं।

अब क्या करें? बटन को टेबल सेल के अंदर एम्बेड करने की कोशिश करें, या VBA मैक्रो जोड़ें जो फॉर्म फ़ील्ड्स को वैलिडेट करे। वही पैटर्न चेक बॉक्स या कॉम्बो बॉक्स जैसे अन्य ActiveX कंट्रोल्स के लिए भी काम करता है—बस `Forms2OleControlType.COMMAND_BUTTON` को उपयुक्त enum वैल्यू से बदल दें।

यदि कोई समस्या आती है, तो नीचे कमेंट करें। Happy coding, और स्वचालित Word डॉक्यूमेंट निर्माण की शक्ति का आनंद लें!


## What Should You Learn Next?


The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [How to Set LoadOptions in Aspose.Words for Java](/words/english/java/document-loading-and-saving/using-load-options/)
- [How to remove footers from Word documents using Aspose.Words for Java](/words/english/java/document-manipulation/removing-content-from-documents/)
- [Aspose.Words Java&#58; Comprehensive Guide to Word Document Processing](/words/english/java/document-operations/aspose-words-java-master-word-processing/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}