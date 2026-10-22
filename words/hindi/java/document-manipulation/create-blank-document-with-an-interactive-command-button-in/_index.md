---
category: general
date: 2026-09-18
description: जावा में एक खाली दस्तावेज़ बनाएं और उसमें एक ActiveX बटन जोड़ें। कमांड
  बटन कैसे डालें, इंटरैक्टिव फ़ॉर्म कैसे बनाएं, और वर्ड दस्तावेज़ को कैसे सहेजें,
  यह सीखें।
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank document
- create interactive form
- add activex button
- how to insert command button
- create word document
language: hi
lastmod: 2026-09-18
og_description: जावा में एक खाली दस्तावेज़ बनाएं और एक ActiveX कमांड बटन एम्बेड करें।
  इंटरैक्टिव फ़ॉर्म बनाने और वर्ड फ़ाइल को सहेजने के लिए इस चरण‑दर‑चरण गाइड का पालन
  करें।
og_image_alt: Screenshot of a Word document showing a clickable ActiveX command button
og_title: वर्ड में इंटरैक्टिव कमांड बटन के साथ खाली दस्तावेज़ बनाएं
schemas:
- author: Aspose
  dateModified: '2026-09-18'
  description: Create blank document in Java and add an ActiveX button. Learn how
    to insert command button, build an interactive form, and save a Word document.
  headline: Create blank document with an interactive command button in Word using
    Java
  type: TechArticle
- description: Create blank document in Java and add an ActiveX button. Learn how
    to insert command button, build an interactive form, and save a Word document.
  name: Create blank document with an interactive command button in Word using Java
  steps:
  - name: 'Load the existing document: `Document doc = new Document("ExistingForm.docx");`'
    text: 'Load the existing document: `Document doc = new Document("ExistingForm.docx");`'
  - name: 'Move the builder to the desired location: `builder.moveToParagraph(5, 0);
      // 6th paragraph, first node`'
    text: 'Move the builder to the desired location: `builder.moveToParagraph(5, 0);
      // 6th paragraph, first node`'
  - name: Insert the button as shown in Step 3.
    text: Insert the button as shown in Step 3.
  - name: Adjust the button’s `Top`/`Left` based on the paragraph’s layout.
    text: Adjust the button’s `Top`/`Left` based on the paragraph’s layout.
  type: HowTo
tags:
- Aspose.Words
- Java
- ActiveX
- Word automation
title: जावा का उपयोग करके वर्ड में इंटरैक्टिव कमांड बटन के साथ खाली दस्तावेज़ बनाएं
url: /hi/java/document-manipulation/create-blank-document-with-an-interactive-command-button-in/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Java का उपयोग करके Word में एक इंटरैक्टिव कमांड बटन के साथ खाली दस्तावेज़ बनाएं

यदि आपको **create blank document** बनाना है जो एक क्लिक करने योग्य बटन रखता हो, तो यह गाइड आपको Aspose.Words for Java के साथ इसे कैसे करना है, बिल्कुल दिखाएगा। आप एक इंटरैक्टिव फ़ॉर्म बनाना, एक ActiveX बटन जोड़ना, और अंत में Word फ़ाइल को सहेजना सीखेंगे—सभी कुछ संक्षिप्त चरणों में।

एक कमांड बटन एम्बेड करने से एक स्थैतिक .docx एक कार्यात्मक फ़ॉर्म बन जाता है, जिससे अंतिम उपयोगकर्ता सीधे Microsoft Word के भीतर इंटरैक्ट कर सकते हैं। यह ट्यूटोरियल **how to insert command button** को भी कवर करता है, सामान्य समस्याओं को संभालता है, और अधिक जटिल फ़ॉर्म के लिए समाधान को विस्तारित करता है।

## पूर्वापेक्षाएँ

* Java 17 या बाद का (कोड JDK 17+ के साथ संकलित होता है)
* Aspose.Words for Java 23.9 या नया – लाइब्रेरी `Document`, `DocumentBuilder`, और `Forms2OleControl` प्रदान करती है।
* एक IDE या बिल्ड टूल (Maven/Gradle) जो Aspose.Words डिपेंडेंसी जोड़ सके।
* Java सिंटैक्स और Word दस्तावेज़ अवधारणाओं का बुनियादी ज्ञान।

```xml
<!-- Maven dependency -->
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
</dependency>
```

## चरण 1: खाली दस्तावेज़ बनाएं

पहला ऑपरेशन एक नया `Document` ऑब्जेक्ट इंस्टैंशिएट करना है। यह ऑब्जेक्ट एक खाली Word फ़ाइल का प्रतिनिधित्व करता है जो सामग्री के लिए तैयार है।

```java
// Step 1: Create a new blank document
Document doc = new Document();
```

एक खाली दस्तावेज़ बनाना आपको एक साफ़ कैनवास देता है, जो तब आवश्यक होता है जब आप किसी भी पूर्व‑निर्मित टेम्पलेट के बिना प्रोग्रामेटिक रूप से **create word document** बनाना चाहते हैं।

## चरण 2: DocumentBuilder को इनिशियलाइज़ करें

`DocumentBuilder` टेक्स्ट, टेबल, और फ़ॉर्म कंट्रोल जोड़ने के लिए मुख्य क्लास है। यह आपके द्वारा अभी बनाए गए `Document` पर काम करता है।

```java
// Step 2: Initialize a DocumentBuilder to construct the document content
DocumentBuilder builder = new DocumentBuilder(doc);
```

बिल्डर वर्तमान इंसर्शन पॉइंट को बनाए रखता है, इसलिए बाद के कमांड फ़ाइल में सही स्थान को प्रभावित करेंगे।

## चरण 3: Forms2Ole कमांड बटन कंट्रोल डालें

Aspose.Words ActiveX कंट्रोल के लिए `Forms2OleControl` क्लास को एक्सपोज़ करता है। **add activex button** करने के लिए, आप बिल्डर से `COMMANDBUTTON` प्रकार का अनुरोध करते हैं।

```java
// Step 3: Insert a Forms2Ole command button control
Forms2OleControl commandButton = builder.insertForms2OleControl(OleControlType.COMMANDBUTTON);
```

`insertForms2OleControl` मेथड कंट्रोल को बिल्डर के वर्तमान कर्सर लोकेशन पर इन्सर्ट करता है। चूँकि यह कंट्रोल एक ActiveX ऑब्जेक्ट है, यह केवल Microsoft Word के डेस्कटॉप संस्करण में काम करता है, Word Online में नहीं।

## चरण 4: बटन की उपस्थिति और स्थिति कॉन्फ़िगर करें

आप कंट्रोल के सेटर्स का उपयोग करके बटन का कैप्शन, आकार, और स्थान सेट कर सकते हैं। पोज़िशन वैल्यू पॉइंट्स में मापी जाती हैं (1 पॉइंट = 1/72 इंच)。

```java
// Step 4: Configure the button's appearance and position
commandButton.setCaption("Click Me");   // Text shown on the button
commandButton.setTop(100);              // Distance from the top edge of the page (points)
commandButton.setLeft(100);             // Distance from the left edge of the page (points)
commandButton.setWidth(120);            // Optional: set button width
commandButton.setHeight(30);            // Optional: set button height
```

*Why configure these properties?* `Top` और `Left` सेट करने से बटन पेज पर वही जगह पर दिखाई देता है जहाँ आप चाहते हैं, जबकि `Caption` उपयोगकर्ता‑दिखाई देने वाला लेबल निर्धारित करता है। यदि आप width/height छोड़ देते हैं, तो Word डिफ़ॉल्ट डाइमेंशन असाइन करता है, जो आपके डिज़ाइन से मेल नहीं खा सकता।

### प्रो टिप

यदि आप कई कंट्रोल जोड़ने की योजना बनाते हैं, तो प्रत्येक इन्सर्शन से पहले `builder.moveToDocumentEnd()` कॉल करें ताकि ऑब्जेक्ट्स ओवरलैप न हों।

## चरण 5: एम्बेडेड कमांड बटन के साथ दस्तावेज़ सहेजें

अंत में, दस्तावेज़ को डिस्क पर लिखें। फ़ाइल एक्सटेंशन `.docx` (या पुराने Word संस्करणों के लिए `.doc`) होना चाहिए ताकि ActiveX कंट्रोल संरक्षित रहे।

```java
// Step 5: Save the document with the embedded command button
String outputPath = "C:/temp/CommandButton.docx";
doc.save(outputPath);
System.out.println("Document saved to: " + outputPath);
```

जब आप Microsoft Word में `CommandButton.docx` खोलते हैं, तो आपको **Click Me** लेबल वाला बटन दिखाई देगा। इसे क्लिक करने से डिफ़ॉल्ट ActiveX एक्शन ट्रिगर होगा (जो डिफ़ॉल्ट रूप से कुछ नहीं करता)। आप बाद में एक मैक्रो या VBA स्क्रिप्ट संलग्न करके कस्टम व्यवहार परिभाषित कर सकते हैं।

## मौजूदा फ़ॉर्म में कमांड बटन कैसे डालें (वैकल्पिक)

यदि आपके पास पहले से ही टेक्स्ट फ़ील्ड वाला फ़ॉर्म है और आप एक बटन सहित **create interactive form** बनाना चाहते हैं, तो इन अतिरिक्त चरणों का पालन करें:

1. मौजूदा दस्तावेज़ लोड करें: `Document doc = new Document("ExistingForm.docx");`
2. बिल्डर को इच्छित स्थान पर ले जाएँ: `builder.moveToParagraph(5, 0); // 6th paragraph, first node`
3. स्टेप 3 में दिखाए अनुसार बटन डालें।
4. पैराग्राफ की लेआउट के आधार पर बटन के `Top`/`Left` को समायोजित करें।

यह तरीका आपको किसी भी प्री‑बिल्ट Word टेम्पलेट को ActiveX बटन के साथ समृद्ध करने देता है बिना पूरे फ़ाइल को फिर से बनाने के।

## किनारे के मामलों और समस्या निवारण

| स्थिति | क्या जांचें | सिफारिशी समाधान |
|-----------|---------------|-----------------|
| बटन Word में दिखाई नहीं देता | सुनिश्चित करें कि आपने फ़ाइल को Word के डेस्कटॉप संस्करण में खोला है (Word Online ActiveX को हटा देता है)। | फ़ाइल को Word 2016+ डेस्कटॉप में खोलें। |
| कैप्शन कट गया है | जाँचें कि बटन की चौड़ाई टेक्स्ट को समाहित करने के लिए पर्याप्त बड़ी है। | `setWidth` को बढ़ाएँ जब तक कैप्शन फिट न हो जाए। |
| सेव करते समय `IOException` फेंकता है | पुष्टि करें कि आउटपुट डायरेक्टरी मौजूद है और आपके पास लिखने की अनुमति है। | डायरेक्टरी बनाएं या प्रोग्राम को उन्नत अधिकारों के साथ चलाएँ। |
| एकाधिक बटन ओवरलैप होते हैं | बिल्डर का कर्सर पिछले इन्सर्शन के बाद नहीं चला हो सकता है। | प्रत्येक नए कंट्रोल को इन्सर्ट करने से पहले `builder.moveToDocumentEnd()` कॉल करें। |

## पूर्ण चलाने योग्य उदाहरण

नीचे एक पूर्ण, स्व-निहित Java प्रोग्राम है जिसे आप कॉपी, कंपाइल और रन कर सकते हैं। यह **create blank document**, **add activex button**, और **save word document** को एक ही प्रवाह में दर्शाता है।

```java
import com.aspose.words.*;

public class CommandButtonDemo {
    public static void main(String[] args) {
        try {
            // 1. Create a new blank document
            Document doc = new Document();

            // 2. Initialize DocumentBuilder
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 3. Insert an ActiveX command button
            Forms2OleControl commandButton = builder.insertForms2OleControl(OleControlType.COMMANDBUTTON);

            // 4. Configure button properties
            commandButton.setCaption("Click Me");
            commandButton.setTop(100);   // points from top
            commandButton.setLeft(100);  // points from left
            commandButton.setWidth(120);
            commandButton.setHeight(30);

            // 5. Save the document
            String outPath = "CommandButton.docx";
            doc.save(outPath);
            System.out.println("Document created: " + outPath);
        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}
```

**अपेक्षित आउटपुट**

```
Document created: CommandButton.docx
```

`CommandButton.docx` खोलने पर एक पेज दिखता है जिसमें **Click Me** लेबल वाला बटन शीर्ष और बाएँ किनारों से 100 pt की दूरी पर स्थित है।

## निष्कर्ष

अब आप जानते हैं कि कैसे **create blank document**, एक **ActiveX button** एम्बेड करें, और एक साधारण Word फ़ाइल को **interactive form** में बदलें। **how to insert command button** में महारत हासिल करके, आप इस पैटर्न को चेकबॉक्स, कॉम्बो बॉक्स, या कस्टम VBA‑ड्रिवेन लॉजिक जोड़ने के लिए विस्तारित कर सकते हैं।

अगला, इन संबंधित विषयों का अन्वेषण करने पर विचार करें:

* **Create interactive form** टेक्स्ट फ़ील्ड (`builder.insertField`)  
* **Add activex button** जो VBA मैक्रो चलाता है (`builder.insertOleObject`)  
* **Create word document** टेम्पलेट से `Document(docTemplatePath)` का उपयोग करके  
* परिणामी .docx को PDF में कन्वर्ट करना जबकि बटन को संरक्षित रखना (ध्यान दें: PDF बटन को एक स्थिर छवि के रूप में रेंडर करेगा)।

## अब आपको क्या सीखना चाहिए?

निम्नलिखित ट्यूटोरियल्स उन निकट संबंधित विषयों को कवर करते हैं जो इस गाइड में प्रदर्शित तकनीकों पर आधारित हैं। प्रत्येक संसाधन में पूर्ण कार्यशील कोड उदाहरण और चरण-दर-चरण व्याख्याएँ शामिल हैं जो आपको अतिरिक्त API फीचर्स में महारत हासिल करने और अपने प्रोजेक्ट्स में वैकल्पिक कार्यान्वयन दृष्टिकोणों का अन्वेषण करने में मदद करती हैं।

- [How to create form fields and add content using DocumentBuilder in Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Create Vba Project in Word Document](/words/english/net/working-with-vba-macros/create-vba-project/)
- [Create New Word Document](/words/english/net/add-content-using-documentbuilder/create-new-document/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}