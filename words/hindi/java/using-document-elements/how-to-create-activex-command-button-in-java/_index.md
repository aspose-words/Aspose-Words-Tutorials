---
category: general
date: 2026-10-07
description: जावा में ActiveX कमांड बटन बनाएं और प्रोग्रामेटिकली वर्ड दस्तावेज़ों
  में कमांड बटन जोड़ें। बटन की बाएँ‑ऊपरी स्थिति सेट करना सीखें।
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create activex command button
- programmatically add command button
- how to set button left top
language: hi
lastmod: 2026-10-07
og_description: जावा में एक्टिवएक्स कमांड बटन बनाकर अपने वर्ड दस्तावेज़ों में इंटरैक्टिव
  कंट्रोल एम्बेड करें। जानें कि प्रोग्रामेटिकली कमांड बटन कैसे जोड़ें, उसकी स्थिति
  सेट करें, और उसकी उपस्थिति को कस्टमाइज़ करें।
og_image_alt: Screenshot showing a created ActiveX command button in a Java‑generated
  Word document
og_title: जावा में ActiveX कमांड बटन बनाएं – चरण-दर-चरण गाइड
schemas:
- author: Aspose
  dateModified: '2026-10-07'
  description: Create ActiveX command button in Java and programmatically add command
    button to Word docs. Learn how to set button left top positions.
  headline: How to create ActiveX command button in Java
  type: TechArticle
- description: Create ActiveX command button in Java and programmatically add command
    button to Word docs. Learn how to set button left top positions.
  name: How to create ActiveX command button in Java
  steps:
  - name: How to set button left top
    text: Positioning the button is where the secondary keyword **how to set button
      left top** becomes relevant. The `setLeft` and `setTop` methods accept values
      measured in points (1 point = 1/72 in).
  - name: Adding multiple buttons
    text: If you need several buttons, repeat **Step 2** and **Step 3** for each control.
      Remember to adjust `setLeft` and `setTop` so the buttons don’t overlap.
  - name: Changing button behavior
    text: 'ActiveX buttons can run VBA macros when clicked. To attach a macro, set
      the `setOnAction` property with the macro name:'
  - name: Compatibility notes
    text: '- The button works only in desktop versions of Word that support ActiveX
      (e.g., Word for Windows). It will appear as a static image in Word for Mac or
      online editors. - If you target a mixed environment, consider using a **content
      control** (`RichTextContentControl`) instead of an ActiveX control.'
  - name: Next steps
    text: '- Explore other ActiveX controls such as `Forms.TextBox.1` or `Forms.CheckBox.1`.
      - Combine multiple controls with a VBA module to implement full‑featured forms.
      - Replace ActiveX with content controls if you need cross‑platform compatibility.'
  type: HowTo
tags:
- ActiveX
- Java
- Aspose.Words
title: जावा में ActiveX कमांड बटन कैसे बनाएं
url: /hi/java/using-document-elements/how-to-create-activex-command-button-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Java में ActiveX command button कैसे बनाएं

यदि आपको Java का उपयोग करके Word दस्तावेज़ में **ActiveX command button** बनाना है, तो यह गाइड आपको बिल्कुल दिखाएगा कि कैसे करना है। आप एक पूर्ण, चलाने योग्य उदाहरण देखेंगे जिसमें **प्रोग्रामेटिकली कमांड बटन जोड़ा जाता है**, उसे `setLeft` और `setTop` से स्थित किया जाता है, और परिणाम को `.docx` फ़ाइल के रूप में सहेजा जाता है।

इंटरैक्टिव बटन एम्बेड करने से आप फ़ॉर्म बना सकते हैं, वर्कफ़्लो को ऑटोमेट कर सकते हैं, या सीधे Word फ़ाइल के भीतर उपयोगकर्ता इनपुट एकत्र कर सकते हैं। नीचे दिए गए चरण प्रोजेक्ट सेटअप से लेकर अंतिम सत्यापन तक सब कुछ कवर करते हैं, ताकि आप कोड को अपने प्रोजेक्ट में बिना किसी विवरण को छोड़े कॉपी कर सकें।

## आवश्यकताएँ

शुरू करने से पहले सुनिश्चित करें कि आपके पास हैं:

- JDK 17 या उससे नया स्थापित हो  
- Maven 3.8+ (या आपका पसंदीदा बिल्ड टूल)  
- Aspose.Words for Java 23.9 या बाद का – वह लाइब्रेरी जो `DocumentBuilder` और OLE नियंत्रण समर्थन प्रदान करती है  
- Java सिंटैक्स और ऑब्जेक्ट‑ओरिएंटेड अवधारणाओं की बुनियादी परिचितता  

यदि आप Maven का उपयोग कर रहे हैं, तो अपनी `pom.xml` में निम्न निर्भरता जोड़ें:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
    <classifier>jdk17</classifier>
</dependency>
```

> **Pro tip:** नवीनतम Aspose.Words संस्करण का उपयोग करें ताकि बग फिक्स और नई OLE सुविधाओं का लाभ मिल सके।

## चरण 1: नया खाली दस्तावेज़ और DocumentBuilder बनाएं

**ActiveX command button** बनाने का पहला चरण एक खाली `Document` और एक `DocumentBuilder` का इंस्टैंस बनाना है। बिल्डर आपको सामग्री सम्मिलित करने के लिए एक फ़्लुएंट API देता है, जिसमें OLE नियंत्रण भी शामिल हैं।

```java
import com.aspose.words.*;

public class ActiveXButtonDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new empty document and a DocumentBuilder to work with it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

`Document` मेमोरी में Word फ़ाइल का प्रतिनिधित्व करता है, जबकि `DocumentBuilder` एक कर्सर की तरह काम करता है जो आपको तत्वों को ठीक उसी जगह रखने की अनुमति देता है जहाँ आप चाहते हैं।

## चरण 2: OLE कमांड बटन नियंत्रण सम्मिलित करें

ActiveX नियंत्रण OLE ऑब्जेक्ट के रूप में सम्मिलित किए जाते हैं। इस उद्देश्य के लिए Aspose.Words `Forms2OleControl` क्लास प्रदान करता है।

```java
        // Step 2: Insert an OLE command button control into the document
        Forms2OleControl commandButton = builder.insertForms2OleControl();
```

जब आप `insertForms2OleControl()` को कॉल करते हैं, तो Aspose स्वचालित रूप से एक प्लेसहोल्डर शेप बनाता है जो ActiveX बटन को होस्ट करेगा।

## चरण 3: बटन की विशेषताएँ कॉन्फ़िगर करें

अब आप **प्रोग्रामेटिकली कमांड बटन** की विवरण जैसे ProgID, कैप्शन और आकार जोड़ते हैं। कमांड बटन के लिए सबसे आम ProgID `"Forms.CommandButton.1"` है।

```java
        // Step 3: Configure the button's properties (type, position, size, caption)
        commandButton.setProgId("Forms.CommandButton.1"); // ActiveX class identifier
        commandButton.setCaption("Click Me");            // Text shown on the button
        commandButton.setWidth(80);                      // Width in points
        commandButton.setHeight(30);                     // Height in points
```

### बटन की बाएँ‑ऊपर स्थिति कैसे सेट करें

बटन को स्थित करना वह जगह है जहाँ द्वितीयक कीवर्ड **how to set button left top** प्रासंगिक बन जाता है। `setLeft` और `setTop` मेथड पॉइंट्स में मान स्वीकार करते हैं (1 पॉइंट = 1/72 इंच)।

```java
        // Position the button 100 points from the left margin and 150 points from the top
        commandButton.setLeft(100);   // Horizontal offset
        commandButton.setTop(150);    // Vertical offset
```

इन संख्याओं को अपने लेआउट के अनुसार समायोजित करें। उदाहरण के लिए, बटन को टेबल सेल के साथ संरेखित करने के लिए, सेल के निर्देशांक की गणना करें और उन्हें `setLeft`/`setTop` को पास करें।

## चरण 4: दस्तावेज़ को सहेजें

अंत में, दस्तावेज़ को डिस्क पर लिखें। फ़ाइल में ActiveX बटन होगा जो Microsoft Word में खोलने पर इंटरैक्शन के लिए तैयार रहेगा।

```java
        // Step 4: Save the document containing the button
        doc.save("CommandButton.docx");
        System.out.println("Document saved successfully.");
    }
}
```

`main` मेथड चलाने पर `CommandButton.docx` बनता है। फ़ाइल को Word में खोलें, यदि प्रॉम्प्ट हो तो कंटेंट सक्षम करें, और आप **Click Me** लेबल वाला क्लिक करने योग्य बटन निर्दिष्ट निर्देशांक पर देखेंगे।

![Java में ActiveX command button बनाना](/images/activex-button-screenshot.png){.center width=600 alt="Java में ActiveX command button बनाना screenshot showing the button inside the Word document"}

## सामान्य विविधताएँ और किनारी मामलों

### कई बटन जोड़ना

यदि आपको कई बटन चाहिए, तो प्रत्येक नियंत्रण के लिए **चरण 2** और **चरण 3** दोहराएँ। बटनों के ओवरलैप न होने के लिए `setLeft` और `setTop` को समायोजित करना याद रखें।

### बटन व्यवहार बदलना

ActiveX बटन क्लिक पर VBA मैक्रो चला सकते हैं। मैक्रो संलग्न करने के लिए, `setOnAction` प्रॉपर्टी को मैक्रो नाम के साथ सेट करें:

```java
commandButton.setOnAction("MyMacro");
```

सुनिश्चित करें कि लक्ष्य दस्तावेज़ में संबंधित VBA मॉड्यूल मौजूद है; अन्यथा Word त्रुटि दिखाएगा।

### संगतता नोट्स

- बटन केवल उन डेस्कटॉप Word संस्करणों में काम करता है जो ActiveX का समर्थन करते हैं (जैसे, Windows के लिए Word)। यह Word for Mac या ऑनलाइन संपादकों में स्थिर छवि के रूप में दिखेगा।  
- यदि आप मिश्रित वातावरण को लक्षित कर रहे हैं, तो ActiveX नियंत्रण के बजाय **content control** (`RichTextContentControl`) का उपयोग करने पर विचार करें।

## संदर्भ के लिए पूर्ण स्रोत कोड

नीचे वह संपूर्ण, स्व-निहित उदाहरण है जिसे आप नई Maven प्रोजेक्ट में कॉपी करके तुरंत चला सकते हैं।

```java
import com.aspose.words.*;

public class ActiveXButtonDemo {
    public static void main(String[] args) throws Exception {
        // Create a new empty document and a DocumentBuilder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert an OLE command button control
        Forms2OleControl commandButton = builder.insertForms2OleControl();

        // Configure the button
        commandButton.setProgId("Forms.CommandButton.1");
        commandButton.setCaption("Click Me");
        commandButton.setWidth(80);
        commandButton.setHeight(30);

        // How to set button left top – position the control
        commandButton.setLeft(100);   // Horizontal offset in points
        commandButton.setTop(150);    // Vertical offset in points

        // Save the resulting document
        doc.save("CommandButton.docx");
        System.out.println("Document saved successfully.");
    }
}
```

**अपेक्षित आउटपुट:** निष्पादन के बाद, आपको अपने प्रोजेक्ट की कार्य निर्देशिका में `CommandButton.docx` मिलेगा। Microsoft Word में फ़ाइल खोलने पर निर्दिष्ट स्थान पर “Click Me” कैप्शन वाला बटन दिखेगा।

## निष्कर्ष

अब आप जानते हैं कि Java में **ActiveX command button** कैसे बनाएं, **प्रोग्रामेटिकली कमांड बटन** को Word दस्तावेज़ में कैसे जोड़ें, और **बटन की बाएँ‑ऊपर स्थिति कैसे सेट करें** मेथड्स का उपयोग करके लेआउट को सटीक रूप से नियंत्रित करें। यह तकनीक समृद्ध, इंटरैक्टिव Word फ़ॉर्म बनाने का द्वार खोलती है जो मैक्रो ट्रिगर कर सकते हैं, बाहरी एप्लिकेशन लॉन्च कर सकते हैं, या सीधे दस्तावेज़ के भीतर उपयोगकर्ता इनपुट एकत्र कर सकते हैं।

### अगले कदम

- `Forms.TextBox.1` या `Forms.CheckBox.1` जैसे अन्य ActiveX नियंत्रणों का अन्वेषण करें।  
- कई नियंत्रणों को VBA मॉड्यूल के साथ मिलाकर पूर्ण‑विशेषताओं वाले फ़ॉर्म लागू करें।  
- यदि आपको क्रॉस‑प्लेटफ़ॉर्म संगतता चाहिए तो ActiveX को content controls से बदलें।  

आकार, कैप्शन और स्थिति को अपने UI डिज़ाइन के अनुसार मिलाने के लिए प्रयोग करने में संकोच न करें। यदि आपको समस्याएँ आती हैं, तो दोबारा जांचें कि आप जिस Aspose.Words संस्करण का उपयोग कर रहे हैं वह OLE नियंत्रणों का समर्थन करता है, और सुनिश्चित करें कि Word की सुरक्षा सेटिंग्स ActiveX निष्पादन की अनुमति देती हैं। Happy coding!

## अब आप क्या सीखें?

निम्नलिखित ट्यूटोरियल्स उन विषयों को कवर करते हैं जो इस गाइड में प्रदर्शित तकनीकों पर आधारित हैं। प्रत्येक संसाधन में पूर्ण कार्यशील कोड उदाहरण और चरण‑दर‑चरण व्याख्याएँ शामिल हैं, जिससे आप अतिरिक्त API सुविधाओं में निपुण हो सकें और अपने प्रोजेक्ट में वैकल्पिक कार्यान्वयन दृष्टिकोणों का अन्वेषण कर सकें।

- [Word दस्तावेज़ों में OLE ऑब्जेक्ट्स और ActiveX नियंत्रण एम्बेड करना](/words/english/python-net/document-structure-and-content-manipulation/document-ole-objects-active-x/)
- [Aspose.Words for Java में DocumentBuilder का उपयोग करके फ़ॉर्म फ़ील्ड बनाना और सामग्री जोड़ना](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Java के साथ Word में आयताकार आकार बनाना – पूर्ण गाइड](/words/english/java/images-shapes/create-rectangle-shape-in-word-with-java-full-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}