---
category: general
date: 2026-11-22
description: जावा का उपयोग करके वर्ड दस्तावेज़ में मैक्रो बटन बनाएं। कमांड बटन डालना,
  बटन का टेक्स्ट सेट करना, और इंटरैक्टिव दस्तावेज़ों के लिए बटन से मैक्रो को लिंक
  करना सीखें।
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create macro button
- insert command button
- set button text
- link macro to button
- add interactive button
language: hi
lastmod: 2026-11-22
og_description: जावा का उपयोग करके वर्ड दस्तावेज़ में मैक्रो बटन बनाएं। यह ट्यूटोरियल
  दिखाता है कि कमांड बटन कैसे डालें, बटन का टेक्स्ट सेट करें, और पूर्ण इंटरैक्टिविटी
  के लिए मैक्रो को बटन से लिंक करें।
og_image_alt: Screenshot of a Word document showing a macro button created with Java
  code
og_title: जावा के साथ वर्ड दस्तावेज़ में मैक्रो बटन बनाएं – चरण‑दर‑चरण मार्गदर्शिका
schemas:
- author: Aspose
  dateModified: '2026-11-22'
  description: Create macro button in a Word document using Java. Learn to insert
    command button, set button text, and link macro to button for interactive documents.
  headline: How to create macro button in a Word document with Aspose.Words for Java
  type: TechArticle
- description: Create macro button in a Word document using Java. Learn to insert
    command button, set button text, and link macro to button for interactive documents.
  name: How to create macro button in a Word document with Aspose.Words for Java
  steps:
  - name: Insert command button into the document
    text: '`DocumentBuilder.insertForms2OleControl` creates an OLE control of the
      specified type. The `Forms2OleControlType.COMMAND_BUTTON` constant tells Aspose.Words
      to generate a command button that can host a macro.'
  - name: Set button text (caption)
    text: The caption is the visible label on the button. Use `setCaption` to define
      what the user sees.
  - name: Link macro to button
    text: A macro is identified by its name, for example `MyMacro`. The `setOnClick`
      method stores this name in the button’s `OnClick` event handler.
  - name: Add interactive button to a Word document
    text: After configuring the OLE control, you may want to position it, resize it,
      or add surrounding text. The `DocumentBuilder` continues to operate on the document,
      so you can insert paragraphs before or after the button.
  - name: Expected output
    text: 'Running the program generates `MacroButtonDemo.docm`. Opening the file
      in Microsoft Word shows:'
  type: HowTo
tags:
- Aspose.Words
- Java
- OLE controls
- Automation
title: Aspose.Words for Java का उपयोग करके Word दस्तावेज़ में मैक्रो बटन कैसे बनाएं
url: /hi/java/using-document-elements/how-to-create-macro-button-in-a-word-document-with-aspose-wo/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word दस्तावेज़ में Aspose.Words for Java के साथ मैक्रो बटन कैसे बनाएं

यदि आपको Word फ़ाइल में **मैक्रो बटन बनाना** है, तो यह गाइड आपको आवश्यक सटीक चरणों के माध्यम से ले जाएगा। आप सीखेंगे कि **कमांड बटन कैसे डालें**, **बटन का टेक्स्ट कैसे सेट करें**, और **मैक्रो को बटन से कैसे लिंक करें** ताकि दस्तावेज़ पूरी तरह इंटरैक्टिव बन सके।

डेवलपर्स अक्सर दस्तावेज़ के भीतर से VBA मैक्रो को ट्रिगर करने के लिए OLE कंट्रोल एम्बेड करते हैं। यह ट्यूटोरियल पूर्ण वर्कफ़्लो को कवर करता है, प्रोजेक्ट सेटअप से लेकर एक रन करने योग्य Java उदाहरण तक जो .docx फ़ाइल में **इंटरैक्टिव बटन** जोड़ता है। कोई बाहरी स्क्रिप्ट आवश्यक नहीं है—सब कुछ Java प्रक्रिया के भीतर चलता है।

## आवश्यकताएँ

* JDK 17 या बाद का स्थापित हो।
* Maven 3.8+ (या Gradle) निर्भरता प्रबंधन के लिए।
* Aspose.Words for Java 23.9 या नया – लाइब्रेरी `DocumentBuilder` और OLE कंट्रोल API प्रदान करती है।
* Java और VBA मैक्रो की बुनियादी जानकारी।

यदि इनमें से कोई भी आइटम अनुपलब्ध है, तो पहले उसे स्थापित करें; ट्यूटोरियल का बाकी हिस्सा यह मानता है कि वे उपलब्ध हैं।

## Aspose.Words for Java के साथ मैक्रो बटन कैसे बनाएं

समाधान का मूल चार क्रियाओं में विभाजित है:

1. **Insert command button** OLE कंट्रोल को दस्तावेज़ में डालें।
2. **Set button text** (कैप्शन) जो उपयोगकर्ता देखता है।
3. **Link macro to button** ताकि क्लिक करने पर वांछित VBA रूटीन चले।
4. **Save the document** एम्बेडेड मैक्रो के साथ।

प्रत्येक क्रिया को नीचे अपने-अपने सेक्शन में समझाया गया है।

### चरण 1: दस्तावेज़ में कमांड बटन डालें

`DocumentBuilder.insertForms2OleControl` निर्दिष्ट प्रकार का OLE कंट्रोल बनाता है। `Forms2OleControlType.COMMAND_BUTTON` कॉन्स्टेंट Aspose.Words को बताता है कि वह एक कमांड बटन जनरेट करे जो मैक्रो होस्ट कर सके।

```java
import com.aspose.words.*;

public class MacroButtonDemo {
    public static void main(String[] args) throws Exception {
        // Load a blank document or create a new one
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a command button OLE control
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMAND_BUTTON);
```

**Why this matters:** OLE कंट्रोल मैक्रो के लिए कंटेनर के रूप में कार्य करता है। इसे डाले बिना, उपयोगकर्ता के क्लिक करने के लिए कोई दृश्य तत्व नहीं रहेगा।

### चरण 2: बटन टेक्स्ट (कैप्शन) सेट करें

कैप्शन बटन पर दिखाई देने वाला लेबल है। `setCaption` का उपयोग करके आप वह टेक्स्ट निर्धारित कर सकते हैं जो उपयोगकर्ता देखेगा।

```java
        // Set the button's caption – this is the text displayed on the button
        commandButton.setCaption("Run Report");
```

**Why this matters:** स्पष्ट बटन टेक्स्ट उपयोगिता को बढ़ाता है। `setCaption` मेथड OLE कंट्रोल की `Caption` प्रॉपर्टी को अपडेट करता है, जिसे Word बटन लेबल के रूप में रेंडर करता है।

### चरण 3: मैक्रो को बटन से लिंक करें

मैक्रो को उसके नाम से पहचाना जाता है, उदाहरण के लिए `MyMacro`। `setOnClick` मेथड इस नाम को बटन के `OnClick` इवेंट हैंडलर में संग्रहीत करता है।

```java
        // Assign a macro to run when the button is clicked
        commandButton.setOnClick("MyMacro");
```

**Why this matters:** मैक्रो को लिंक करने से इंटरैक्टिव व्यवहार बनता है। जब उपयोगकर्ता Word में बटन पर क्लिक करता है, तो संबंधित VBA रूटीन निष्पादित होती है।

### चरण 4: Word दस्तावेज़ में इंटरैक्टिव बटन जोड़ें

OLE कंट्रोल को कॉन्फ़िगर करने के बाद, आप इसे स्थित करना, आकार बदलना, या आसपास का टेक्स्ट जोड़ना चाह सकते हैं। `DocumentBuilder` दस्तावेज़ पर काम करना जारी रखता है, इसलिए आप बटन से पहले या बाद में पैराग्राफ डाल सकते हैं।

```java
        // Add a descriptive paragraph before the button
        builder.moveToDocumentStart();
        builder.writeln("Click the button below to generate the report:");

        // Move the cursor back to the button location (optional)
        builder.moveTo(commandButton.getNode());

        // Optionally, resize the button (width and height in points)
        commandButton.setWidth(120);
        commandButton.setHeight(30);

        // Save the document with the macro-enabled format
        doc.save("MacroButtonDemo.docm", SaveFormat.DOCM);
    }
}
```

**Why this matters:** `.docm` के रूप में सहेजने से मैक्रो कोड संरक्षित रहता है। यदि आप इसे `.docx` के रूप में सहेजते हैं, तो मैक्रो रेफ़रेंस खो जाता है।

## पूर्ण रन करने योग्य उदाहरण

नीचे पूरा Java प्रोग्राम दिया गया है, जिसमें इम्पोर्ट्स, एक्सेप्शन हैंडलिंग, और प्रत्येक चरण को समझाने वाले कमेंट्स शामिल हैं। कोड को Aspose.Words डिपेंडेंसी वाले Maven प्रोजेक्ट में कॉपी करें और चलाएँ।

```java
// Maven dependency (add to pom.xml):
// <dependency>
//   <groupId>com.aspose</groupId>
//   <artifactId>aspose-words</artifactId>
//   <version>23.9</version>
// </dependency>

import com.aspose.words.*;

public class MacroButtonDemo {
    public static void main(String[] args) throws Exception {
        // 1. Create a new empty document
        Document doc = new Document();

        // 2. Initialize DocumentBuilder to edit the document
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 3. Write an introductory paragraph
        builder.writeln("Press the button to execute the macro:");

        // 4. Insert the command button OLE control
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMAND_BUTTON);

        // 5. Set the visual caption of the button
        commandButton.setCaption("Run Report");

        // 6. Link the button to a VBA macro named MyMacro
        commandButton.setOnClick("MyMacro");

        // 7. Resize the button for better appearance
        commandButton.setWidth(120);   // points
        commandButton.setHeight(30);   // points

        // 8. Save the document as a macro‑enabled file
        doc.save("MacroButtonDemo.docm", SaveFormat.DOCM);
    }
}
```

### अपेक्षित आउटपुट

प्रोग्राम चलाने से `MacroButtonDemo.docm` बनता है। Microsoft Word में फ़ाइल खोलने पर दिखता है:

* एक पैराग्राफ जिसमें लिखा हो *“Press the button to execute the macro:”*।
* एक बटन जिसका लेबल **Run Report** है, जो सीधे पैराग्राफ के नीचे स्थित है।
* जब आप बटन पर क्लिक करेंगे, तो Word मैक्रो `MyMacro` चलाने की कोशिश करेगा। (आपको वास्तविक VBA कोड दस्तावेज़ में मैन्युअल रूप से या किसी अन्य ऑटोमेशन स्टेप के माध्यम से जोड़ना होगा।)

यदि मैक्रो मौजूद नहीं है, तो Word एक सुरक्षा चेतावनी दिखाता है, जो मैक्रो‑सक्षम दस्तावेज़ों के लिए सामान्य व्यवहार है।

## सामान्य विविधताएँ और किनारे के मामलों

| परिदृश्य | कोड को कैसे अनुकूलित करें |
|----------|-----------------------|
| **विभिन्न बटन कैप्शन** | स्ट्रिंग को बदलें जो `setCaption` को पास की गई है। |
| **एकाधिक बटन** | बार-बार `insertForms2OleControl` को कॉल करें, प्रत्येक के अपने `setCaption` और `setOnClick` के साथ। |
| **कस्टम मैक्रो नाम** | `"MyMacro"` को किसी भी वैध VBA प्रोसिजर नाम से बदलें, जैसे `"ExportToExcel"`। |
| **बटन आकार प्रतिबंध** | `setWidth` और `setHeight` मानों को समायोजित करें; Word आपके द्वारा प्रदान किए गए पॉइंट्स का सम्मान करता है। |
| **प्रोग्रामेटिक रूप से मैक्रो एम्बेड करना** | `Document.getBuiltInDocumentProperties().add("Macros", …)` का उपयोग करें या एक अलग VBA इंजेक्शन स्टेप; Aspose.Words स्वयं VBA कोड नहीं लिखता। |

**Pro tip:** हमेशा उत्पन्न `.docm` को ऐसे मशीन पर टेस्ट करें जहाँ मैक्रो सुरक्षा *Enable all macros* पर सेट हो विकास के लिए। प्रोडक्शन में, सुरक्षा प्रॉम्प्ट से बचने के लिए मैक्रो को विश्वसनीय प्रमाणपत्र से साइन करें।

## समस्या निवारण चेकलिस्ट

* **Button does not appear** – सुनिश्चित करें कि दस्तावेज़ `.docm` के रूप में सहेजा गया है और OLE कंट्रोल्स को सपोर्ट करने वाले Word संस्करण में खोला गया है।
* **Macro does not run** – सुनिश्चित करें कि मैक्रो नाम बिल्कुल मेल खाता है, केस सहित, और मैक्रो दस्तावेज़ के VBA प्रोजेक्ट में मौजूद है।
* **Button caption is truncated** – लंबा टेक्स्ट फिट करने के लिए `setWidth` का उपयोग करके बटन की चौड़ाई बढ़ाएँ।
* **Unexpected layout shift** – कंट्रोल डालने से पहले कर्सर को सटीक रूप से स्थित करने के लिए `builder.moveTo` का उपयोग करें।

## निष्कर्ष

अब आप जानते हैं कि Java का उपयोग करके Word दस्तावेज़ में **मैक्रो बटन कैसे बनाएं**, **कमांड बटन डालें**, **बटन टेक्स्ट सेट करें**, और **मैक्रो को बटन से लिंक करें** ताकि पूरी इंटरैक्टिविटी मिल सके। पूर्ण उदाहरण प्रत्येक आवश्यक API कॉल को दर्शाता है, बताता है कि प्रत्येक चरण क्यों महत्वपूर्ण है, और सामान्य विविधताओं के लिए मार्गदर्शन प्रदान करता है।

अगला, आप निम्नलिखित का अन्वेषण कर सकते हैं:

* **Add interactive button** को नई दस्तावेज़ के बजाय मौजूदा टेम्पलेट्स में जोड़ें।
* Open XML SDK या किसी द्वितीयक ऑटोमेशन टूल का उपयोग करके **Programmatically inject VBA code**।
* समृद्ध फॉर्म बनाने के लिए **Combine multiple OLE controls** (चेकबॉक्स, लिस्ट बॉक्स) को मिलाएँ।

विभिन्न कैप्शन, मैक्रो नाम, और बटन आकारों के साथ प्रयोग करें ताकि आपके विशिष्ट उपयोग केस में फिट हो सके। कोडिंग का आनंद लें!

## अब आप क्या सीखें?

निम्नलिखित ट्यूटोरियल्स उन निकट संबंधित विषयों को कवर करते हैं जो इस गाइड में दिखाए गए तकनीकों पर आधारित हैं। प्रत्येक संसाधन में पूर्ण कार्यशील कोड उदाहरण और चरण-दर-चरण व्याख्याएँ शामिल हैं, जो आपको अतिरिक्त API फीचर्स में महारत हासिल करने और अपने प्रोजेक्ट्स में वैकल्पिक इम्प्लीमेंटेशन एप्रोच को खोजने में मदद करेंगे।

- [Java का उपयोग करके Word दस्तावेज़ में कमांड बटन कैसे डालें](/words/english/java/using-document-elements/how-to-insert-command-button-in-a-word-document-using-java/)
- [Java के साथ Word दस्तावेज़ में बटन की स्थिति कैसे सेट करें](/words/english/java/using-document-elements/how-to-set-button-position-in-a-word-document-with-java/)
- [Word में ActiveX बटन कैसे डालें – बटन कैप्शन सेट करें](/words/english/java/using-document-elements/how-to-insert-activex-button-in-word-set-button-caption/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}