---
category: general
date: 2026-07-20
description: Aspose.Words का उपयोग करके Word दस्तावेज़ में बटन कैसे जोड़ें। मिनटों
  में DocumentBuilder के साथ Forms2OleControl बटन डालना सीखें।
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to add button to word document
- Forms2OleControl
- DocumentBuilder
- insertForms2OleControl
- Word automation
language: hi
lastmod: 2026-07-20
og_description: Aspose.Words के साथ Word दस्तावेज़ में बटन कैसे जोड़ें। जावा का उपयोग
  करके Forms2OleControl CommandButton को एम्बेड करने के लिए इस व्यावहारिक गाइड का
  पालन करें।
og_image_alt: Screenshot of a Word document with a clickable button added via Aspose.Words
  (how to add button to word document)
og_title: Word दस्तावेज़ में बटन कैसे जोड़ें – पूर्ण Aspose.Words ट्यूटोरियल
schemas:
- author: Aspose
  dateModified: '2026-07-20'
  description: How to add button to Word document using Aspose.Words. Learn to insert
    a Forms2OleControl button with DocumentBuilder in minutes.
  headline: How to Add Button to Word Document – Step‑by‑Step Guide
  type: TechArticle
- description: How to add button to Word document using Aspose.Words. Learn to insert
    a Forms2OleControl button with DocumentBuilder in minutes.
  name: How to Add Button to Word Document – Step‑by‑Step Guide
  steps:
  - name: '`Forms2OleControlType.COMMANDBUTTON` – tells Word we want a button.'
    text: '`Forms2OleControlType.COMMANDBUTTON` – tells Word we want a button.'
  - name: '`100` – width in points (≈1.39 inches).'
    text: '`100` – width in points (≈1.39 inches).'
  - name: '`30` – height in points (≈0.42 inches).'
    text: '`30` – height in points (≈0.42 inches).'
  type: HowTo
tags:
- Aspose.Words
- Java
- Office Automation
title: वर्ड दस्तावेज़ में बटन कैसे जोड़ें – चरण-दर-चरण गाइड
url: /hi/java/using-document-elements/how-to-add-button-to-word-document-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word दस्तावेज़ में बटन कैसे जोड़ें – पूर्ण Aspose.Words ट्यूटोरियल

क्या आपने कभी **Word दस्तावेज़ में बटन कैसे जोड़ें** बिना UI खोले और क्लिक‑क्लिक किए सोचा है? आप अकेले नहीं हैं। कई डेवलपर्स को प्रोग्रामेटिक रूप से इंटरैक्टिव कंट्रोल्स एम्बेड करने की जरूरत पड़ती है—जैसे टेम्पलेट में “Submit” बटन, जिसे बाद में अंतिम उपयोगकर्ता भरता है। अच्छी खबर? Aspose.Words for Java के साथ आप इसे कुछ ही लाइनों में कर सकते हैं।

इस ट्यूटोरियल में हम `DocumentBuilder` का उपयोग करके **CommandButton** प्रकार का `Forms2OleControl` डालने के सटीक चरणों से गुजरेंगे। अंत में आपके पास एक तैयार `.docx` फ़ाइल होगी, जिसमें “Click Me” लेबल वाला क्लिक‑योग्य बटन होगा। कोई रहस्य नहीं, सिर्फ स्पष्ट कोड और प्रत्येक लाइन के पीछे की तर्कसंगति।

## आप क्या सीखेंगे

- शून्य से नया Word दस्तावेज़ कैसे बनाएं।
- **DocumentBuilder** का उपयोग करके **Forms2OleControl** कैसे रखें।
- बटन का कैप्शन सेट करना और आकार निर्धारित करना क्यों आवश्यक है।
- परिणाम को कैसे सहेजें और सत्यापित करें।
- सामान्य समस्याएँ (जैसे, लाइब्रेरी नहीं मिलना, असमर्थित कंट्रोल प्रकार) और उन्हें कैसे टालें।

**Prerequisites** – आपको Java 8+ (या नया) और Aspose.Words for Java लाइब्रेरी (version 23.12 या बाद का) चाहिए। IntelliJ IDEA या Eclipse जैसे IDE से काम आसान होगा, लेकिन कोई भी टेक्स्ट एडिटर चल जाएगा।

---

## Step 1: Set Up Your Project and Import Dependencies

कोड चलाने से पहले, Maven (या Gradle) को बताना होगा कि Aspose.Words कहाँ से लाना है। अपने `pom.xml` में यह स्निपेट जोड़ें:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.12</version>
</dependency>
```

यदि आप Gradle पसंद करते हैं, तो समकक्ष यह है:

```gradle
implementation 'com.aspose:aspose-words:23.12'
```

> **Pro tip:** नवीनतम रिलीज़ उपयोग करें; पुराने संस्करणों में `Forms2OleControl` API नहीं हो सकता।

डिपेंडेंसी रिजॉल्व हो जाने के बाद, आप Java कोड लिखने के लिए तैयार हैं।

---

## Step 2: Create a New Document and Obtain a DocumentBuilder

`Document` क्लास पूरी `.docx` पैकेज को दर्शाती है, जबकि `DocumentBuilder` वह ब्रश है जिसका उपयोग आप उस पर कंटेंट पेंट करने के लिए करते हैं। `DocumentBuilder` को “कर्सर” समझें, जो जानता है अगला एलिमेंट कहाँ जाना चाहिए।

```java
import com.aspose.words.*;

public class AddButtonExample {
    public static void main(String[] args) throws Exception {
        // Step 2: Create a new blank document
        Document doc = new Document();

        // Obtain a DocumentBuilder tied to the document
        DocumentBuilder builder = new DocumentBuilder(doc);
```

**Why this matters:** नया `Document` इनिशियलाइज़ करने से आपके पास एक साफ़ कैनवास मिलता है। बिल्डर स्वचालित रूप से पहले पैराग्राफ पर पॉइंट करता है, इसलिए आपको सेक्शन या पेज को मैन्युअली मैनेज करने की जरूरत नहीं।

---

## Step 3: Insert a Forms2OleControl of Type CommandButton

अब मुख्य भाग: `insertForms2OleControl`। यह मेथड एक OLE (Object Linking and Embedding) कंट्रोल बनाता है, जिसे Word फॉर्म एलिमेंट के रूप में मानता है। हम तीन आर्ग्यूमेंट पास करेंगे:

1. `Forms2OleControlType.COMMANDBUTTON` – Word को बताता है कि हमें बटन चाहिए।
2. `100` – चौड़ाई पॉइंट्स में (≈1.39 इंच)।
3. `30` – ऊँचाई पॉइंट्स में (≈0.42 इंच)।

```java
        // Step 3: Insert a CommandButton with specific dimensions
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON, 100, 30);
```

**How it works:** अंदर से Aspose.Words `word/document.xml` भाग में उपयुक्त XML बनाता है, जो OLE ऑब्जेक्ट को रेफ़र करता है। आप जो डाइमेंशन देते हैं, वे Word के लेआउट इंजन द्वारा सम्मानित होते हैं, इसलिए बटन बिल्डर के कर्सर की स्थिति पर ठीक वैसा ही दिखता है।

---

## Step 4: Set the Caption (Text) on the Button

बिना लेबल वाला बटन भ्रमित करता है—जैसे मौन लिफ़्ट बटन। `setCaption` मेथड दृश्यमान टेक्स्ट सेट करता है:

```java
        // Step 4: Define the button's label
        commandButton.setCaption("Click Me");
```

आप कैप्शन को कुछ भी बदल सकते हैं: “Submit”, “Approve”, या कोई स्थानीयकृत स्ट्रिंग। कैप्शन OLE ऑब्जेक्ट की प्रॉपर्टीज़ में स्टोर होता है, इसलिए Word इसे नेटिव रूप से रेंडर करेगा।

---

## Step 5: Save the Document and Verify the Result

अंत में, फ़ाइल को डिस्क पर लिखें। ऐसा फ़ोल्डर चुनें जहाँ आपके पास लिखने की अनुमति हो; अन्यथा `IOException` आएगा।

```java
        // Step 5: Persist the document
        String outputPath = "output/button-demo.docx";
        doc.save(outputPath);
        System.out.println("Document saved to: " + outputPath);
    }
}
```

`button-demo.docx` को Microsoft Word में खोलें। आपको दस्तावेज़ के शीर्ष पर **Click Me** लेबल वाला बटन दिखेगा। Word में इस पर क्लिक करने से डिफ़ॉल्ट OLE व्यवहार (आमतौर पर एक प्लेसहोल्डर मैसेज) ट्रिगर होगा, जब तक आप कोई मैक्रो बाइंड नहीं करते।

---

## Common Edge Cases and How to Handle Them

| Situation | Why It Happens | Fix |
|-----------|----------------|-----|
| **Missing `Forms2OleControl` type** | पुराने Aspose.Words संस्करणों में यह enum उपलब्ध नहीं था। | 23.12+ या बाद के संस्करण में अपग्रेड करें। |
| **Button appears as a picture** | Word की सुरक्षा सेटिंग्स OLE कंट्रोल्स को ब्लॉक करती हैं। | Trust Center में “Trust access to the VBA project object model” को एनेबल करें, या `.docm` फ़ाइल का उपयोग करें। |
| **Incorrect size** | पॉइंट बनाम पिक्सेल का भ्रम। | याद रखें 1 point = 1/72 inch. संख्या को उसी अनुसार समायोजित करें। |
| **Saving throws `FileNotFoundException`** | पाथ मौजूद नहीं है। | `doc.save` से पहले सुनिश्चित करें कि डायरेक्टरी (`output/`) बनाई गई है। `new File("output").mkdirs();` का उपयोग करें। |

---

## Extending the Example: Adding Multiple Buttons or Other Controls

यदि आपको एक से अधिक बटन चाहिए, तो `builder.moveTo` या `builder.writeln()` से बिल्डर का कर्सर ले जाएँ, फिर फिर से `insertForms2OleControl` कॉल करें।

```java
        // Add a second button below the first
        builder.writeln(); // moves to a new paragraph
        Forms2OleControl secondButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON, 120, 35);
        secondButton.setCaption("Submit");
```

आप **CheckBox**, **ComboBox**, या **ListBox** भी डाल सकते हैं, बस `Forms2OleControlType.COMMANDBUTTON` को उपयुक्त enum वैल्यू (`CHECKBOX`, `COMBOBOX` आदि) से बदलें। चौड़ाई/ऊँचाई पैरामीटर वही रहेंगे।

---

## How This Fits Into Larger Word Automation Workflows

- **Template Generation:** ऐसा कॉन्ट्रैक्ट टेम्प्लेट बनाएं जिसमें “Approve” बटन शामिल हो, जिसे बाद में स्वीकृति के लिए उपयोग किया जाएगा।
- **Reporting:** दैनिक रिपोर्ट में “Refresh Data” बटन जोड़ें, जो मैक्रो ट्रिगर करता है।
- **Form Distribution:** इंटरैक्टिव कंट्रोल्स प्री‑पॉप्युलेटेड प्रश्नावली भेजें।

इन सभी परिदृश्यों को हमने दिखाए गए **Word automation** तरीके से लाभ मिलता है। कंट्रोल्स को प्रोग्रामेटिक रूप से एम्बेड करके आप मैन्युअल एडिटिंग को खत्म कर सकते हैं और मानवीय त्रुटियों को कम कर सकते हैं।

---

## Full Source Code (Copy‑Paste Ready)

```java
import com.aspose.words.*;

public class AddButtonExample {
    public static void main(String[] args) throws Exception {
        // Create a new blank document
        Document doc = new Document();

        // Obtain a DocumentBuilder for the document
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a CommandButton (width: 100pt, height: 30pt)
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON, 100, 30);

        // Set the button caption
        commandButton.setCaption("Click Me");

        // Optionally add a second button
        builder.writeln(); // new paragraph
        Forms2OleControl secondButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON, 120, 35);
        secondButton.setCaption("Submit");

        // Save the document
        String outputPath = "output/button-demo.docx";
        new java.io.File("output").mkdirs(); // ensure directory exists
        doc.save(outputPath);
        System.out.println("Document saved to: " + outputPath);
    }
}
```

**Expected output:** जब आप `output/button-demo.docx` को Microsoft Word में खोलेंगे, तो आपको दो बटन—“Click Me” और “Submit”—ऊपर से नीचे क्रम में दिखेंगे।

---

## Conclusion

हमने **Word दस्तावेज़ में बटन कैसे जोड़ें** को Aspose.Words for Java की मदद से चरण‑दर‑चरण समझाया। एक खाली `Document` से शुरू करके, हमने **DocumentBuilder** का उपयोग करके **CommandButton** प्रकार का `Forms2OleControl` डाला, एक दोस्ताना कैप्शन सेट किया, और परिणाम सहेजा। यह तरीका कई कंट्रोल्स के लिए स्केलेबल है और व्यापक **Word automation** पाइपलाइन में सहजता से फिट होता है।

अगली चुनौती के लिए तैयार हैं? बटन को **CheckBox** से बदलें, या `.docm` फ़ाइल में मैक्रो बाइंड करके बटन क्लिक पर प्रतिक्रिया दें। वही पैटर्न लागू होता है—सिर्फ enum बदलें और कैप्शन समायोजित करें।

यदि कोई समस्या आती है, तो लाइब्रेरी संस्करण और आउटपुट फ़ोल्डर की अनुमतियों की दोबारा जाँच करें। नीचे कमेंट करके प्रश्न पूछें या अपना उपयोग‑केस शेयर करें। Happy coding!

## What Should You Learn Next?

नीचे दिए गए ट्यूटोरियल्स उन विषयों को कवर करते हैं जो इस गाइड में दिखाए गए तकनीकों पर आधारित हैं। प्रत्येक संसाधन में पूर्ण कार्यशील कोड उदाहरण और चरण‑दर‑चरण व्याख्याएँ शामिल हैं, जिससे आप अतिरिक्त API फीचर्स में महारत हासिल कर सकें और अपने प्रोजेक्ट्स में वैकल्पिक इम्प्लीमेंटेशन अप्रोचेज़ को एक्सप्लोर कर सकें।

- [How to create form fields and add content using DocumentBuilder in Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Insert Inline Image in Word Document using Aspose.Words](/words/english/net/add-content-using-document-builder/insert-inline-image/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}