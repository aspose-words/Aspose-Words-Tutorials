---
category: general
date: 2026-09-27
description: Aspose.Words का उपयोग करके जावा में ActiveX युक्त docx बनाएं। चरण‑दर‑चरण
  ActiveX कमांड बटन डालना सीखें।
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create docx containing activex
- insert activex command button
- Aspose.Words Java
- ActiveX control in Word
- generate Word document programmatically
language: hi
lastmod: 2026-09-27
og_description: Aspose.Words के साथ जावा में ActiveX वाला docx बनाएं। इस गाइड का पालन
  करके ActiveX कमांड बटन डालें और दस्तावेज़ को सहेजें।
og_image_alt: Screenshot of a Word document that contains an ActiveX command button
og_title: जावा में ActiveX युक्त docx बनाएं – पूर्ण मार्गदर्शिका
schemas:
- author: Aspose
  dateModified: '2026-09-27'
  description: Create docx containing ActiveX in Java using Aspose.Words. Learn to
    insert an ActiveX command button step‑by‑step.
  headline: How to create docx containing ActiveX with Java and Aspose.Words
  type: TechArticle
- description: Create docx containing ActiveX in Java using Aspose.Words. Learn to
    insert an ActiveX command button step‑by‑step.
  name: How to create docx containing ActiveX with Java and Aspose.Words
  steps:
  - name: The document should show a single page with a button labeled **Click Me**
      positioned near the top‑left corner.
    text: The document should show a single page with a button labeled **Click Me**
      positioned near the top‑left corner.
  - name: If the button does not appear, check that **ActiveX controls are enabled**
      in Word’s Trust Center (File → Options → Trust Center → Trust Center Settings
      → ActiveX Settings).
    text: If the button does not appear, check that **ActiveX controls are enabled**
      in Word’s Trust Center (File → Options → Trust Center → Trust Center Settings
      → ActiveX Settings).
  - name: The button is functional only on Windows versions of Word that support ActiveX.
      On macOS or web‑based Word, the control will be displayed as a static image.
    text: The button is functional only on Windows versions of Word that support ActiveX.
      On macOS or web‑based Word, the control will be displayed as a static image.
  type: HowTo
tags:
- docx
- activex
- java
- aspose-words
title: जावा और Aspose.Words के साथ ActiveX युक्त docx कैसे बनाएं
url: /hi/java/using-document-elements/how-to-create-docx-containing-activex-with-java-and-aspose-w/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Java और Aspose.Words के साथ ActiveX युक्त docx कैसे बनाएं

यदि आपको **ActiveX युक्त docx बनाना** है, तो यह गाइड आपको एक पूर्ण समाधान दिखाता है। आप सीखेंगे कि Aspose.Words for Java का उपयोग करके Word फ़ाइल में **ActiveX कमांड बटन** कैसे **डालें**, और फिर परिणाम को .docx के रूप में सहेजें जिसे Microsoft Word में खोला जा सकता है।

प्रोग्रामेटिक रूप से Word दस्तावेज़ बनाना आपको मैन्युअल संपादन से बचाता है और रिपोर्ट, अनुबंध, या फ़ॉर्म टेम्पलेट्स में स्थिरता सुनिश्चित करता है। नीचे दिए गए चरण प्रोजेक्ट सेटअप से लेकर सामान्य समस्याओं को संभालने तक सब कुछ कवर करते हैं, ताकि आप इस तकनीक को किसी भी Java एप्लिकेशन में एकीकृत कर सकें।

## आवश्यकताएँ

* Java Development Kit (JDK) 8 या उससे नया स्थापित हो।
* Maven 3.6+ (या कोई अन्य बिल्ड टूल जो आप पसंद करते हैं)।
* Aspose.Words for Java लाइसेंस फ़ाइल (नि:शुल्क मूल्यांकन परीक्षण के लिए काम करता है)।
* यदि आप ActiveX नियंत्रण को दृश्य रूप से सत्यापित करना चाहते हैं तो लक्ष्य मशीन पर Microsoft Word स्थापित हो।

इन वस्तुओं की आवश्यकता इसलिए है क्योंकि Aspose.Words वह API प्रदान करता है जो दस्तावेज़ बनाता है, जबकि Word को ActiveX नियंत्रण को रेंडर करने के लिए आवश्यक है।

## चरण 1: Maven प्रोजेक्ट सेटअप करें

एक नया Maven प्रोजेक्ट बनाएं या मौजूदा `pom.xml` में Aspose.Words निर्भरता जोड़ें:

```xml
<project>
    <modelVersion>4.0.0</modelVersion>
    <groupId>com.example</groupId>
    <artifactId>activex-docx-demo</artifactId>
    <version>1.0.0</version>
    <properties>
        <maven.compiler.source>1.8</maven.compiler.source>
        <maven.compiler.target>1.8</maven.compiler.target>
    </properties>

    <dependencies>
        <!-- Aspose.Words for Java -->
        <dependency>
            <groupId>com.aspose</groupId>
            <artifactId>aspose-words</artifactId>
            <version>24.10</version> <!-- use the latest stable version -->
        </dependency>
    </dependencies>
</project>
```

> **Pro tip:** बग फिक्स और नए ActiveX फीचर्स का लाभ उठाने के लिए Aspose.Words संस्करण को आधिकारिक रिलीज़ नोट्स के साथ सिंक में रखें।

## चरण 2: वह Java कोड लिखें जो दस्तावेज़ बनाता है

`ActiveXDocxCreator` नाम की एक क्लास बनाएं। नीचे दिया गया कोड सभी आवश्यक इम्पोर्ट्स, एक `main` मेथड, और विस्तृत टिप्पणियों को शामिल करता है जो प्रत्येक ऑपरेशन को समझाती हैं।

```java
package com.example.activex;

import com.aspose.words.*;
import java.io.File;

/**
 * Demonstrates how to create a DOCX file that contains an ActiveX command button.
 * The resulting file can be opened in Microsoft Word where the button appears
 * on the first page.
 */
public class ActiveXDocxCreator {

    public static void main(String[] args) {
        // 1. Initialize a new empty document and a DocumentBuilder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2. Insert an ActiveX Forms2OleControl at the current cursor position.
        Forms2OleControl commandButton = builder.insertForms2OleControl();

        // 3. Configure the control to be a CommandButton and set its caption.
        commandButton.setControlType(Forms2OleControlType.COMMANDBUTTON);
        commandButton.setCaption("Click Me");

        // 4. Position the button on the page.
        //    The coordinates are measured in points (1 point = 1/72 inch).
        commandButton.setLeft(100); // 100 points from the left margin
        commandButton.setTop(150);  // 150 points from the top margin

        // 5. (Optional) Set the size of the button for better visibility.
        commandButton.setWidth(120);
        commandButton.setHeight(30);

        // 6. Save the document to the desired location.
        String outputPath = "output/ActiveXCommandButton.docx";
        try {
            // Ensure the output directory exists.
            new File("output").mkdirs();
            doc.save(outputPath);
            System.out.println("Document saved successfully to " + outputPath);
        } catch (Exception e) {
            System.err.println("Error while saving the document: " + e.getMessage());
        }
    }
}
```

### प्रत्येक पंक्ति क्यों महत्वपूर्ण है

* `Document` सभी Word सामग्री का कंटेनर है। नया इंस्टेंस बनाने से आपको एक साफ़ कैनवास मिलता है।
* `DocumentBuilder` तत्वों को डालने के लिए एक फ्लुएंट API प्रदान करता है; यह स्वचालित रूप से इन्सर्शन पॉइंट को ट्रैक करता है।
* `insertForms2OleControl()` एक सामान्य OLE कंट्रोल प्लेसहोल्डर बनाता है। Aspose.Words इसे ActiveX कंटेनर के रूप में मानता है।
* `setControlType(Forms2OleControlType.COMMANDBUTTON)` Word को बताता है कि प्लेसहोल्डर को CommandButton के रूप में रेंडर करना चाहिए।
* `setCaption("Click Me")` बटन पर प्रदर्शित होने वाला टेक्स्ट निर्धारित करता है।
* `setLeft` और `setTop` बटन को पेज मार्जिन के सापेक्ष स्थित करते हैं। अपने लेआउट के अनुसार इन मानों को समायोजित करें।
* `setWidth` और `setHeight` वैकल्पिक हैं लेकिन बटन की उपस्थिति को बेहतर बनाते हैं, विशेषकर जब डिफ़ॉल्ट आकार बहुत छोटा हो।
* `doc.save` इन‑मेमोरी संरचना को एक भौतिक .docx फ़ाइल में लिखता है जिसे Word खोल सकता है।

## चरण 3: उत्पन्न दस्तावेज़ को सत्यापित करें

`output/ActiveXCommandButton.docx` को Microsoft Word में खोलें:

1. दस्तावेज़ में एक ही पेज दिखना चाहिए जिसमें बटन **Click Me** लेबल के साथ शीर्ष‑बाएँ कोने के पास स्थित हो।
2. यदि बटन नहीं दिखता है, तो Word के Trust Center में **ActiveX controls are enabled** है या नहीं, जांचें (File → Options → Trust Center → Trust Center Settings → ActiveX Settings)।
3. बटन केवल Windows संस्करण के Word में कार्यात्मक है जो ActiveX का समर्थन करता है। macOS या वेब‑आधारित Word में, नियंत्रण एक स्थिर छवि के रूप में दिखेगा।

## चरण 4: सामान्य किनारी मामलों को संभालना

| स्थिति | कारण | सिफारिशित कार्रवाई |
|-----------|--------|--------------------|
| फ़ाइल खोलने के बाद बटन गायब है | Word की सुरक्षा सेटिंग्स ActiveX को ब्लॉक करती हैं | विश्वसनीय स्थानों के लिए “Run all controls without restrictions” सक्षम करें। |
| उत्पन्न .docx नहीं खुल रहा है | Aspose.Words संस्करण असंगत है | नवीनतम Aspose.Words रिलीज़ में अपग्रेड करें; पुराने संस्करण आवश्यक OLE भागों को सही ढंग से एम्बेड नहीं कर सकते। |
| आपको बटन को मैक्रो चलाने की आवश्यकता है | केवल ActiveX में मैक्रो कोड नहीं होता | ActiveX कंट्रोल को एक VBA मैक्रो के साथ संयोजित करें जो `Click` इवेंट को संभालता है। `DocumentBuilder.insertOleObject` मेथड का उपयोग करके मैक्रो‑सक्षम टेम्पलेट एम्बेड करें। |
| विभिन्न पेज आकारों पर लेआउट बिगड़ रहा है | निर्देशांक निरपेक्ष पॉइंट्स हैं | कंट्रोल को स्थित करने से पहले `builder.getPageSetup().setPageWidth` और `setPageHeight` का उपयोग करके पेज आकार को मानकीकृत करें। |

## चरण 5: समाधान का विस्तार करना

`ControlType` enum बदलकर आप अन्य ActiveX कंट्रोल डाल सकते हैं:

```java
commandButton.setControlType(Forms2OleControlType.CHECKBOX); // inserts a checkbox
```

Aspose.Words **ActiveX टेक्स्ट बॉक्स**, **list boxes**, और **combo boxes** डालने का भी समर्थन करता है। वही पोजिशनिंग मेथड्स (`setLeft`, `setTop`, `setWidth`, `setHeight`) लागू होते हैं।

यदि आपको कई कंट्रोल रखने हैं, तो `builder.insertForms2OleControl()` को बार‑बार कॉल करें और प्रत्येक कंट्रोल के निर्देशांक को तदनुसार समायोजित करें।

## पूरा स्रोत फ़ाइल

नीचे पूरा `ActiveXDocxCreator.java` फ़ाइल दिया गया है, जिसे कॉपी‑एंड‑पेस्ट के लिए तैयार है:

```java
package com.example.activex;

import com.aspose.words.*;
import java.io.File;

public class ActiveXDocxCreator {
    public static void main(String[] args) {
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        Forms2OleControl commandButton = builder.insertForms2OleControl();
        commandButton.setControlType(Forms2OleControlType.COMMANDBUTTON);
        commandButton.setCaption("Click Me");
        commandButton.setLeft(100);
        commandButton.setTop(150);
        commandButton.setWidth(120);
        commandButton.setHeight(30);

        String outputPath = "output/ActiveXCommandButton.docx";
        try {
            new File("output").mkdirs();
            doc.save(outputPath);
            System.out.println("Document saved successfully to " + outputPath);
        } catch (Exception e) {
            System.err.println("Error while saving the document: " + e.getMessage());
        }
    }
}
```

इस प्रोग्राम को चलाने से एक **ActiveX युक्त docx** बनता है जिसे आप उन अंतिम उपयोगकर्ताओं को वितरित कर सकते हैं जिन्हें इंटरैक्टिव फ़ॉर्म की आवश्यकता है।

## निष्कर्ष

अब आप जानते हैं कि Java और Aspose.Words का उपयोग करके **ActiveX युक्त docx** कैसे **बनाएं**, और प्रोग्रामेटिक रूप से **ActiveX कमांड बटन** कैसे **डालें**। इस ट्यूटोरियल में प्रोजेक्ट सेटअप, पूरा स्रोत कोड, सत्यापन चरण, और सामान्य समस्याओं से निपटने की रणनीतियों को कवर किया गया है।

अब आप आगे खोज सकते हैं:

* बटन क्लिक पर प्रतिक्रिया देने के लिए VBA मैक्रो जोड़ना।
* चेकबॉक्स या कॉम्बो बॉक्स जैसे अन्य ActiveX कंट्रोल एम्बेड करना।
* डायनामिक डेटा के साथ मल्टी‑पेज फ़ॉर्म की जनरेशन को ऑटोमेट करना।

विभिन्न निर्देशांक, आकार, और कंट्रोल प्रकारों के साथ प्रयोग करें ताकि आपका दस्तावेज़ लेआउट अनुकूल हो। कोडिंग का आनंद लें!

## आप को आगे क्या सीखना चाहिए?

निम्नलिखित ट्यूटोरियल्स उन निकट-संबंधित विषयों को कवर करते हैं जो इस गाइड में दिखाए गए तकनीकों पर आधारित हैं। प्रत्येक संसाधन में पूर्ण कार्यशील कोड उदाहरण और चरण‑दर‑चरण व्याख्याएँ शामिल हैं जो आपको अतिरिक्त API फीचर्स में महारत हासिल करने और अपने प्रोजेक्ट्स में वैकल्पिक कार्यान्वयन दृष्टिकोणों का अन्वेषण करने में मदद करती हैं।

- [Aspose.Words for Java में OLE ऑब्जेक्ट्स और ActiveX कंट्रोल्स का उपयोग]( /words/english/java/using-document-elements/using-ole-objects-and-activex/ )
- [Aspose.Words for Java में DocumentBuilder का उपयोग करके फ़ॉर्म फ़ील्ड बनाना और कंटेंट जोड़ना]( /words/english/java/document-manipulation/adding-content-using-documentbuilder/ )
- [Aspose.Words के साथ Word में आयताकार आकार बनाना – चरण‑दर‑चरण गाइड]( /words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/ )

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}