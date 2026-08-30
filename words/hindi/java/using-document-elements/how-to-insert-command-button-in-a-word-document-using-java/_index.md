---
category: general
date: 2026-08-23
description: जावा और Aspose.Words का उपयोग करके वर्ड दस्तावेज़ में कमांड बटन कैसे
  डालें, सीखें। यह गाइड दिखाता है कि फ़ॉर्म कंट्रोल कैसे जोड़ें, बटन का नाम कैसे सेट
  करें, और ActiveX बटन को कैसे एम्बेड करें।
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert command button
- add form control
- how to add button
- set button name
- add activex button
language: hi
lastmod: 2026-08-23
og_description: जावा का उपयोग करके वर्ड दस्तावेज़ में कमांड बटन डालें। फ़ॉर्म कंट्रोल
  जोड़ने, बटन का नाम सेट करने और Aspose.Words के साथ एक ActiveX बटन एम्बेड करने के
  लिए इस गाइड का पालन करें।
og_image_alt: Screenshot of a Word document showing an inserted ActiveX command button
og_title: जावा के साथ वर्ड में कमांड बटन डालें – चरण-दर-चरण गाइड
schemas:
- author: Aspose
  dateModified: '2026-08-23'
  description: Learn how to insert command button in a Word document using Java and
    Aspose.Words. This guide shows how to add form control, set button name, and embed
    an ActiveX button.
  headline: How to insert command button in a Word document using Java
  type: TechArticle
- description: Learn how to insert command button in a Word document using Java and
    Aspose.Words. This guide shows how to add form control, set button name, and embed
    an ActiveX button.
  name: How to insert command button in a Word document using Java
  steps:
  - name: Open `CommandButtonDemo.docx` with Microsoft Word (2016 or later).
    text: Open `CommandButtonDemo.docx` with Microsoft Word (2016 or later).
  - name: The **Submit** button appears where the cursor was positioned during insertion.
    text: The **Submit** button appears where the cursor was positioned during insertion.
  - name: Right‑click the button and choose **Properties** to see that the **Name**
      field contains `btnSubmit`.
    text: Right‑click the button and choose **Properties** to see that the **Name**
      field contains `btnSubmit`.
  type: HowTo
tags:
- Aspose.Words
- Java
- Word automation
title: जावा का उपयोग करके वर्ड दस्तावेज़ में कमांड बटन कैसे सम्मिलित करें
url: /hi/java/using-document-elements/how-to-insert-command-button-in-a-word-document-using-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Java का उपयोग करके Word दस्तावेज़ में कमांड बटन कैसे डालें

यदि आपको Word फ़ाइल में **insert command button** डालने की आवश्यकता है, तो यह ट्यूटोरियल Aspose.Words for Java के साथ एक पूर्ण समाधान दिखाता है। आप देखेंगे कि फ़ॉर्म कंट्रोल कैसे जोड़ें, उसके कैप्शन को कॉन्फ़िगर करें, और बटन का नाम अपने IDE से बाहर निकले बिना सेट करें।

गाइड में वह सब कुछ शामिल है जो आपको एक `.docx` बनाने के लिए चाहिए जिसमें Microsoft Word में उपयोग के लिए तैयार ActiveX बटन हो। अतिरिक्त कोई टूलिंग आवश्यक नहीं है, और उदाहरण Java 8+ पर चलता है।

## आप क्या सीखेंगे

* Word दस्तावेज़ में प्रकार **CommandButton** का फ़ॉर्म कंट्रोल कैसे जोड़ें।  
* **set button name** और **add activex button** प्रॉपर्टीज़ के सटीक चरण।  
* दस्तावेज़ को इस तरह सहेजें कि Word में खोलने पर बटन सही ढंग से दिखाई दे।  

आपके पास एक बुनियादी Java विकास वातावरण और एक Maven या Gradle प्रोजेक्ट होना चाहिए जो Aspose.Words लाइब्रेरी को इम्पोर्ट कर सके।

## पूर्वापेक्षाएँ

| Requirement | Reason |
|-------------|--------|
| Java 8 or newer | Aspose.Words for Java Java 8+ पर चलता है। |
| Maven or Gradle build tool | Aspose.Words निर्भरता जोड़ने को सरल बनाता है। |
| Aspose.Words for Java license (or free trial) | पूर्ण फीचर सेट के लिए आवश्यक; API मूल्यांकन मोड में काम करता है। |
| An IDE such as IntelliJ IDEA or Eclipse | उदाहरण को संपादित करने और चलाने को आसान बनाता है। |

## चरण 1: अपने प्रोजेक्ट में Aspose.Words जोड़ें

यदि आप Maven का उपयोग करते हैं, तो `pom.xml` में निम्नलिखित निर्भरता जोड़ें:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version> <!-- Use the latest version -->
</dependency>
```

Gradle के लिए, इस पंक्ति को `build.gradle` में रखें:

```gradle
implementation 'com.aspose:aspose-words:24.9'
```

निर्भरता हल होने के बाद, आप अपने Java स्रोत फ़ाइल में लाइब्रेरी क्लासेस को इम्पोर्ट कर सकते हैं।

## चरण 2: कमांड बटन डालें – मुख्य कोड

`InsertCommandButtonDemo` नाम की नई Java क्लास बनाएं। नीचे दिया गया कोड **insert command button** डालने के लिए आवश्यक चारों कार्य करता है:

```java
import com.aspose.words.*;

public class InsertCommandButtonDemo {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Create a new blank document and a DocumentBuilder to edit it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Add form control – an ActiveX CommandButton – to the document
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMAND_BUTTON);

        // 3️⃣ Set button name and displayed caption (this answers the "set button name" need)
        commandButton.setName("btnSubmit");
        commandButton.setCaption("Submit");

        // 4️⃣ Save the document with the embedded button
        doc.save("CommandButtonDemo.docx");
    }
}
```

### प्रत्येक पंक्ति क्यों महत्वपूर्ण है

* **Document & DocumentBuilder** – वे Word फ़ाइल का इन‑मेमोरी प्रतिनिधित्व और उसकी सामग्री को संशोधित करने के लिए API प्रदान करते हैं।  
* **insertForms2OleControl** – यह मेथड प्रकार `COMMAND_BUTTON` का **adds form control** करता है। लौटाया गया `Forms2OleControl` ऑब्जेक्ट ActiveX कंट्रोल का प्रतिनिधित्व करता है।  
* **setName** – एक प्रोग्रामेटिक पहचानकर्ता (`btnSubmit`) असाइन करता है। Word मैक्रोज़ या VBA बाद में इस नाम को संदर्भित कर सकते हैं।  
* **setCaption** – बटन पर उपयोगकर्ता को दिखने वाला टेक्स्ट निर्धारित करता है, “बटन कैसे जोड़ें” प्रश्न का उत्तर देता है।  
* **save** – `.docx` को डिस्क पर लिखता है, एम्बेडेड ActiveX बटन को संरक्षित रखता है।  

प्रोग्राम चलाने से कार्य निर्देशिका में `CommandButtonDemo.docx` बनता है। Microsoft Word में फ़ाइल खोलने पर **Submit** लेबल वाला बटन दिखता है जिसे आप क्लिक कर सकते हैं (यह मूल्यांकन मोड में एक डिफ़ॉल्ट ActiveX डायलॉग प्रदर्शित करेगा)।

## चरण 3: Word में डाले गए बटन की जाँच करें

1. `CommandButtonDemo.docx` को Microsoft Word (2016 या बाद का) में खोलें।  
2. डालने के दौरान कर्सर जहाँ स्थित था, वहाँ **Submit** बटन दिखाई देता है।  
3. बटन पर राइट‑क्लिक करें और **Properties** चुनें ताकि देखें कि **Name** फ़ील्ड में `btnSubmit` है।  

यदि बटन नहीं दिखता, तो सुनिश्चित करें कि Word के Trust Center सेटिंग्स में **ActiveX controls** सक्षम हैं।

## चरण 4: बटन को कस्टमाइज़ करना (वैकल्पिक)

आप बटन का आकार, स्थिति समायोजित करके या VBA मैक्रो जोड़कर इसे और कस्टमाइज़ कर सकते हैं। `Forms2OleControl` क्लास अतिरिक्त प्रॉपर्टीज़ जैसे `setWidth`, `setHeight`, और `setLeft` को उजागर करता है। नीचे एक उदाहरण है जो बटन को बड़ा बनाता है:

```java
commandButton.setWidth(100);   // Width in points
commandButton.setHeight(30);   // Height in points
commandButton.setLeft(50);     // Horizontal offset from the left margin
```

इन पंक्तियों को `setCaption` कॉल के बाद रखा जा सकता है। ये **add activex button** कस्टमाइज़ेशन को बुनियादी डाली से आगे दिखाते हैं।

## सामान्य समस्याएँ और उन्हें कैसे टालें

| Symptom | Cause | Fix |
|---------|-------|-----|
| बटन Word में नहीं दिखता | कंट्रोल जोड़ने से पहले दस्तावेज़ सहेजा गया | `insertForms2OleControl` को `doc.save` से पहले कॉल किया गया है, यह सुनिश्चित करें। |
| बटन का कैप्शन खाली है | `setCaption` नहीं कॉल किया गया या खाली स्ट्रिंग के साथ कॉल किया गया | एक गैर‑खाली स्ट्रिंग प्रदान करें, जैसे `"Submit"`। |
| VBA बटन नहीं ढूँढ पा रहा है | `setName` मान और VBA कोड के बीच नाम का मेल नहीं है | नाम को सुसंगत रखें; `setName("btnSubmit")` उपयोग करें और VBA में `btnSubmit` को संदर्भित करें। |
| फ़ाइल खोलते समय सुरक्षा चेतावनी | Word की मैक्रो सुरक्षा ActiveX कंट्रोल्स को ब्लॉक करती है | Trust Center > Macro Settings समायोजित करें, या दस्तावेज़ को विश्वसनीय प्रमाणपत्र से साइन करें। |

## पूर्ण, चलाने योग्य उदाहरण

नीचे पूर्ण स्रोत फ़ाइल है, जिसे अपने IDE में कॉपी‑पेस्ट करने के लिए तैयार है। इसमें इम्पोर्ट स्टेटमेंट्स, एक्सेप्शन हैंडलिंग, और एक टिप्पणी ब्लॉक शामिल है जो प्रत्येक प्रमुख चरण को समझाता है।

```java
// InsertCommandButtonDemo.java
// Demonstrates how to insert an ActiveX CommandButton into a Word document using Aspose.Words for Java.

import com.aspose.words.*;

public class InsertCommandButtonDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document and a DocumentBuilder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Add a CommandButton form control (ActiveX) to the document.
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMAND_BUTTON);

        // Step 3: Configure the button – set its programmatic name and visible caption.
        commandButton.setName("btnSubmit");   // This answers the "set button name" requirement.
        commandButton.setCaption("Submit");   // This is the text the user sees.

        // Optional: Resize and reposition the button (demonstrates add activex button customization).
        commandButton.setWidth(100);
        commandButton.setHeight(30);
        commandButton.setLeft(50);

        // Step 4: Save the document. The button is now embedded and will appear in Word.
        doc.save("CommandButtonDemo.docx");
    }
}
```

**अपेक्षित परिणाम:** प्रोग्राम चलाने के बाद, `CommandButtonDemo.docx` में एक ही **Submit** बटन होता है। Word में फ़ाइल खोलने पर बटन ठीक उसी जगह दिखता है जहाँ `DocumentBuilder` कर्सर स्थित था।

## अगले कदम

* **Add more form controls** – पूर्ण Word फ़ॉर्म बनाने के लिए `Forms2OleControlType.CHECK_BOX`, `RADIO_BUTTON`, या `TEXT_BOX` का उपयोग करें।  
* **Combine with mail merge** – व्यक्तिगत इंटरैक्टिव फ़ॉर्म बनाने के लिए मेल‑मर्ज्ड दस्तावेज़ में बटन डालें।  
* **Attach VBA macros** – उन्नत ऑटोमेशन के लिए बटन के `Click` इवेंट पर प्रतिक्रिया देने वाला VBA प्रोग्रामेटिकली एम्बेड करें।  

ये विषय स्वाभाविक रूप से आपके द्वारा अभी सीखी गई **add form control** तकनीक को विस्तारित करते हैं।

---

### पुनरावलोकन

अब आप जानते हैं कि Java का उपयोग करके Word दस्तावेज़ में **insert command button** कैसे डालें, **add form control** कैसे करें, **set button name** कैसे सेट करें, और **add activex button** कस्टमाइज़ेशन कैसे करें। पूर्ण उदाहरण बॉक्स से बाहर चलाता है, और आप इसे किसी भी दस्तावेज़‑जनरेशन वर्कफ़्लो में अनुकूलित कर सकते हैं। कोडिंग का आनंद लें!

## अब आपको क्या सीखना चाहिए?

निम्नलिखित ट्यूटोरियल्स उन निकट संबंधित विषयों को कवर करते हैं जो इस गाइड में दिखाए गए तकनीकों पर आधारित हैं। प्रत्येक संसाधन में पूर्ण कार्यशील कोड उदाहरण और चरण‑दर‑चरण व्याख्याएँ शामिल हैं ताकि आप अतिरिक्त API सुविधाओं में निपुण हो सकें और अपने प्रोजेक्ट्स में वैकल्पिक कार्यान्वयन दृष्टिकोणों का अन्वेषण कर सकें।

- [Aspose.Words for Java में DocumentBuilder का उपयोग करके फ़ॉर्म फ़ील्ड बनाना और सामग्री जोड़ना कैसे करें](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Word दस्तावेज़ में कॉम्बो बॉक्स फ़ॉर्म फ़ील्ड डालें](/words/english/net/working-with-form-fields/insert-form-fields/)
- [Word दस्तावेज़ में चेक बॉक्स फ़ॉर्म फ़ील्ड डालें](/words/english/net/add-content-using-documentbuilder/insert-check-box-form-field/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}