---
category: general
date: 2026-09-24
description: Java और Aspose.Words का उपयोग करके Word दस्तावेज़ में बटन की स्थिति सेट
  करें। सीखें कैसे बटन डालें, ActiveX नियंत्रण जोड़ें, और Java शैली में Word दस्तावेज़
  बनाएं।
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- set button position
- how to insert button
- add activex control
- add button to word
- create word document java
language: hi
lastmod: 2026-09-24
og_description: जावा का उपयोग करके वर्ड दस्तावेज़ में बटन की स्थिति सेट करें। यह गाइड
  दिखाता है कि बटन कैसे डालें, ActiveX नियंत्रण कैसे जोड़ें, और Aspose.Words के साथ
  जावा में वर्ड दस्तावेज़ कैसे बनाएं।
og_image_alt: Screenshot of a Word document showing a CommandButton positioned at
  100 px left and 150 px top
og_title: जावा के साथ वर्ड दस्तावेज़ में बटन की स्थिति सेट करें – पूर्ण मार्गदर्शिका
schemas:
- author: Aspose
  dateModified: '2026-09-24'
  description: Set button position in a Word document using Java and Aspose.Words.
    Learn how to insert button, add ActiveX control, and create Word document Java
    style.
  headline: How to set button position in a Word document with Java
  type: TechArticle
- description: Set button position in a Word document using Java and Aspose.Words.
    Learn how to insert button, add ActiveX control, and create Word document Java
    style.
  name: How to set button position in a Word document with Java
  steps:
  - name: Expected output
    text: '* A `.docx` file named **CommandButtonDemo.docx**. * Inside the document,
      a **CommandButton** labeled “Click Me” appears 100 px from the left margin and
      150 px from the top margin. * The button responds to clicks when the document
      is opened in Word (it will display a default ActiveX message unless y'
  - name: Adding multiple buttons
    text: If you need to **add button to Word** more than once, repeat steps 3‑5 with
      a new `Forms2OleControl` instance each time. Remember to adjust the `setTop`
      value so buttons don’t overlap.
  - name: Working without a license
    text: 'Aspose.Words adds a watermark when used without a license. For production
      code, purchase a license and apply it at the start of `main`:'
  - name: Compatibility with older Office versions
    text: 'ActiveX controls are supported in the `.doc` (Word 97‑2003) format. To
      create a legacy file, change the save format:'
  - name: Next steps
    text: '* Explore other `Forms2OleControl.ControlType` values (e.g., `CHECKBOX`,
      `TEXTBOX`) to build richer forms. * Combine the button with VBA macros for custom
      click handling. * Use Aspose.Words’ mail‑merge feature to generate personalized
      documents that already contain interactive controls.'
  type: HowTo
- questions:
  - answer: Yes. Aspose.Words is pure Java and runs on any JDK 8+ implementation,
      including OpenJDK.
    question: Does this work with OpenJDK?
  - answer: ActiveX button appearance is controlled by the host application (Word).
      You can attach VBA code to modify properties at runtime, but the static appearance
      is limited to the default style.
    question: Can I change the button’s font or color?
  - answer: 'Move the `DocumentBuilder` cursor into the cell before calling `insertForms2OleControl`.
      The control will inherit the cell’s layout, and you can still use `setLeft`/`setTop`
      for fine‑tuning. ## Conclusion You now know how to **set button position** in
      a Word document using Java, how to **how to inse'
    question: What if I need to place the button inside a table cell?
  type: FAQPage
tags:
- Aspose.Words
- Java
- ActiveX
- Word automation
- CommandButton
title: जावा के साथ वर्ड दस्तावेज़ में बटन की स्थिति कैसे सेट करें
url: /hi/java/using-document-elements/how-to-set-button-position-in-a-word-document-with-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Java के साथ Word दस्तावेज़ में बटन की स्थिति कैसे सेट करें

यदि आपको Word फ़ाइल के भीतर **set button position** सेट करना है, तो यह गाइड आपको एक पूर्ण, चलाने योग्य समाधान दिखाता है। चाहे आप उपयोगकर्ता इंटरैक्शन की आवश्यकता वाले टेम्पलेट बना रहे हों या फ़ॉर्म को स्वचालित कर रहे हों, आप Aspose.Words for Java का उपयोग करके **how to insert button** कैसे डालें और उसकी स्थिति को नियंत्रित करना सीखेंगे।

ट्यूटोरियल में वह सब कुछ शामिल है जो आपको Word दस्तावेज़ में **add ActiveX control** जोड़ने के लिए चाहिए, यह बताता है कि **add button to Word** कैसे करें, और **create Word document Java** शैली में पूरी प्रक्रिया को प्रदर्शित करता है। कोई बाहरी संदर्भ आवश्यक नहीं है—सिर्फ कॉपी करें, चलाएँ, और परिणाम सत्यापित करें।

## पूर्वापेक्षाएँ

* Java 17 (या कोई भी Java 8+ रनटाइम) स्थापित हो।
* निर्भरताओं को प्रबंधित करने के लिए Maven या Gradle।
* Aspose.Words for Java लाइसेंस (मुफ़्त ट्रायल मूल्यांकन के लिए काम करता है)।
* Java सिंटैक्स की बुनियादी समझ।

> **Pro tip:** अपने Aspose.Words JARs को `libs/` फ़ोल्डर में रखें और उन्हें अपने प्रोजेक्ट की क्लासपाथ में जोड़ें ताकि संस्करण संघर्ष से बचा जा सके।

## चरण 1: Maven प्रोजेक्ट सेट अप करें

एक साधारण Maven प्रोजेक्ट बनाएं (या Gradle उपयोग करें) और Aspose.Words निर्भरता जोड़ें:

```xml
<!-- pom.xml -->
<project>
    <modelVersion>4.0.0</modelVersion>
    <groupId>com.example</groupId>
    <artifactId>word-button-demo</artifactId>
    <version>1.0.0</version>
    <dependencies>
        <dependency>
            <groupId>com.aspose</groupId>
            <artifactId>aspose-words</artifactId>
            <version>24.9</version> <!-- latest at time of writing -->
        </dependency>
    </dependencies>
</project>
```

`mvn clean compile` चलाने से लाइब्रेरी डाउनलोड होती है और बिल्ड पाथ तैयार हो जाता है।

## चरण 2: नया Word दस्तावेज़ बनाएं

पहला ऑपरेशन **create Word document java** शैली में है। आप एक `Document` ऑब्जेक्ट और एक `DocumentBuilder` बनाते हैं जो आपको फ़ाइल को संपादित करने देता है।

```java
import com.aspose.words.*;

public class CommandButtonDemo {
    public static void main(String[] args) throws Exception {
        // Initialize a blank document
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

`Document` क्लास पूरे .docx फ़ाइल का प्रतिनिधित्व करता है, जबकि `DocumentBuilder` सामग्री डालने के लिए एक फ़्लुएंट API प्रदान करता है।

## चरण 3: बटन कैसे डालें – add ActiveX control

Aspose.Words `Forms2OleControl` क्लास को उजागर करता है जिससे आप CommandButton जैसे लेगेसी ActiveX कंट्रोल डाल सकते हैं। यह चरण दस्तावेज़ में **how to insert button** डालने का सटीक तरीका दिखाता है।

```java
        // Insert a CommandButton ActiveX control
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControl.ControlType.COMMANDBUTTON);
```

`insertForms2OleControl` मेथड एक `Forms2OleControl` इंस्टेंस लौटाता है जिसे आप कॉन्फ़िगर कर सकते हैं। यह **add ActiveX control** प्रक्रिया का मुख्य भाग है।

## चरण 4: बटन की स्थिति सेट करें

अब हम वास्तव में **set button position** करते हैं। कंट्रोल के `setLeft` और `setTop` मेथड पॉइंट्स में मान स्वीकार करते हैं (1 pt = 1/72 in)। बटन को सामान्य स्क्रीन कॉर्डिनेट्स के साथ संरेखित करने के लिए, आप पिक्सेल को पॉइंट्स में बदल सकते हैं (1 px ≈ 0.75 pt)। इस उदाहरण में हम बटन को बाएँ किनारे से 100 px और ऊपर से 150 px पर रखते हैं।

```java
        // Position the button on the page
        commandButton.setLeft(100 * 0.75);   // 75 pt ≈ 100 px
        commandButton.setTop(150 * 0.75);    // 112.5 pt ≈ 150 px
```

चूँकि **set button position** लॉजिक यहाँ संलग्न है, आप इन लाइनों को तब पुनः उपयोग कर सकते हैं जब भी आपको कंट्रोल को स्थानांतरित करना हो। अपने लेआउट आवश्यकताओं के अनुसार संख्याओं को समायोजित करें।

## चरण 5: आकार और कैप्शन निर्धारित करें

बिना लेबल वाला बटन भ्रमित करने वाला होता है। `setWidth`, `setHeight`, और `setCaption` का उपयोग करके इसे एक दृश्यमान रूप दें।

```java
        // Define size and caption
        commandButton.setWidth(120 * 0.75);   // 90 pt width
        commandButton.setHeight(30 * 0.75);   // 22.5 pt height
        commandButton.setCaption("Click Me");
```

आकार भी पॉइंट्स में व्यक्त किया जाता है, इसलिए हम स्थिरता के लिए पिक्सेल से बदलते हैं।

## चरण 6: दस्तावेज़ सहेजें – create Word document java प्रवाह को पूरा करें

अंत में, फ़ाइल को डिस्क पर सहेजें। पाथ पूर्ण (absolute) या प्रोजेक्ट रूट के सापेक्ष हो सकता है।

```java
        // Save the document containing the CommandButton
        doc.save("output/CommandButtonDemo.docx");
    }
}
```

प्रोग्राम चलाने से `output` फ़ोल्डर के भीतर `CommandButtonDemo.docx` बनता है। Microsoft Word में फ़ाइल खोलने पर एक क्लिक करने योग्य बटन दिखता है जो ठीक उसी स्थान पर स्थित है जहाँ आपने इसे सेट किया था।

### अपेक्षित आउटपुट

* `.docx` फ़ाइल जिसका नाम **CommandButtonDemo.docx** है।
* दस्तावेज़ के भीतर, **CommandButton** लेबल “Click Me” के साथ बाएँ मार्जिन से 100 px और ऊपर से 150 px पर दिखाई देता है।
* जब दस्तावेज़ Word में खोला जाता है तो बटन क्लिक पर प्रतिक्रिया देता है (यदि आप कस्टम VBA कोड नहीं जोड़ते तो यह डिफ़ॉल्ट ActiveX संदेश दिखाएगा)।

## चरण 7: सामान्य विविधताएँ और किनारे के मामले

### कई बटन जोड़ना

यदि आपको **add button to Word** एक से अधिक बार करना है, तो प्रत्येक बार एक नया `Forms2OleControl` इंस्टेंस के साथ चरण 3‑5 दोहराएँ। बटनों के ओवरलैप न होने के लिए `setTop` मान को समायोजित करना याद रखें।

```java
        Forms2OleControl secondButton = builder.insertForms2OleControl(
                Forms2OleControl.ControlType.COMMANDBUTTON);
        secondButton.setLeft(200 * 0.75);
        secondButton.setTop(250 * 0.75);
        secondButton.setWidth(120 * 0.75);
        secondButton.setHeight(30 * 0.75);
        secondButton.setCaption("Second");
```

### बिना लाइसेंस के काम करना

Aspose.Words बिना लाइसेंस के उपयोग करने पर वॉटरमार्क जोड़ता है। प्रोडक्शन कोड के लिए, लाइसेंस खरीदें और इसे `main` की शुरुआत में लागू करें:

```java
        License license = new License();
        license.setLicense("Aspose.Words.lic");
```

### पुराने Office संस्करणों के साथ संगतता

ActiveX कंट्रोल `.doc` (Word 97‑2003) फ़ॉर्मेट में समर्थित हैं। लेगेसी फ़ाइल बनाने के लिए, सहेजने का फ़ॉर्मेट बदलें:

```java
        doc.save("CommandButtonDemo.doc", SaveFormat.DOC);
```

## पूर्ण स्रोत कोड (चलाने योग्य)

```java
import com.aspose.words.*;

public class CommandButtonDemo {
    public static void main(String[] args) throws Exception {
        // Optional: apply a license if you have one
        // License license = new License();
        // license.setLicense("Aspose.Words.lic");

        // Step 1: Create a new blank document and a DocumentBuilder to edit it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Insert a CommandButton ActiveX control (how to insert button)
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControl.ControlType.COMMANDBUTTON);

        // Step 3: Position the button on the page (set button position)
        commandButton.setLeft(100 * 0.75);   // distance from the left edge (points)
        commandButton.setTop(150 * 0.75);    // distance from the top edge (points)

        // Step 4: Define the button's size and caption
        commandButton.setWidth(120 * 0.75);   // width in points
        commandButton.setHeight(30 * 0.75);   // height in points
        commandButton.setCaption("Click Me");

        // Step 5: Save the document containing the CommandButton (create word document java)
        doc.save("output/CommandButtonDemo.docx");
    }
}
```

फ़ाइल को `src/main/java/CommandButtonDemo.java` के रूप में सहेजें, `mvn exec:java -Dexec.mainClass=CommandButtonDemo` चलाएँ, और परिणाम देखने के लिए उत्पन्न दस्तावेज़ खोलें।

## अक्सर पूछे जाने वाले प्रश्न

**Q: क्या यह OpenJDK के साथ काम करता है?**  
A: हाँ। Aspose.Words शुद्ध Java है और किसी भी JDK 8+ इम्प्लीमेंटेशन पर चलता है, जिसमें OpenJDK भी शामिल है।

**Q: क्या मैं बटन का फ़ॉन्ट या रंग बदल सकता हूँ?**  
A: ActiveX बटन की उपस्थिति होस्ट एप्लिकेशन (Word) द्वारा नियंत्रित होती है। आप रनटाइम पर प्रॉपर्टीज़ बदलने के लिए VBA कोड संलग्न कर सकते हैं, लेकिन स्थिर उपस्थिति डिफ़ॉल्ट शैली तक सीमित है।

**Q: यदि मुझे बटन को टेबल सेल के अंदर रखना हो तो क्या करें?**  
A: `insertForms2OleControl` कॉल करने से पहले `DocumentBuilder` कर्सर को सेल में ले जाएँ। कंट्रोल सेल की लेआउट को विरासत में लेगा, और आप अभी भी सूक्ष्म समायोजन के लिए `setLeft`/`setTop` का उपयोग कर सकते हैं।

## निष्कर्ष

अब आप जानते हैं कि Java का उपयोग करके Word दस्तावेज़ में **set button position** कैसे करें, **how to insert button** कैसे डालें, **add ActiveX control** कैसे जोड़ें, और **add button to Word** कैसे करें, साथ ही **create Word document java** प्रोजेक्ट्स के लिए सर्वोत्तम प्रथाओं का पालन करें। पूर्ण उदाहरण पूरे वर्कफ़्लो को दर्शाता है—प्रोजेक्ट सेटअप से लेकर एक सहेजी गई `.docx` फ़ाइल जिसमें कार्यात्मक CommandButton है।

### अगले कदम

* `Forms2OleControl.ControlType` के अन्य मानों (जैसे, `CHECKBOX`, `TEXTBOX`) का अन्वेषण करें ताकि अधिक समृद्ध फ़ॉर्म बना सकें।
* कस्टम क्लिक हैंडलिंग के लिए बटन को VBA मैक्रो के साथ संयोजित करें।
* Aspose.Words की mail‑merge सुविधा का उपयोग करके व्यक्तिगत दस्तावेज़ बनाएं जिनमें पहले से इंटरैक्टिव कंट्रोल हों।

कोडिंग का आनंद लें, और Java के साथ Word दस्तावेज़ों को स्वचालित करने का मज़ा उठाएँ!

## अब आप क्या सीखें?

निम्नलिखित ट्यूटोरियल्स उन निकट संबंधित विषयों को कवर करते हैं जो इस गाइड में दिखाए गए तकनीकों पर आधारित हैं। प्रत्येक संसाधन में पूर्ण कार्यशील कोड उदाहरण और चरण-दर-चरण व्याख्याएँ शामिल हैं जो आपको अतिरिक्त API फीचर्स में निपुण बनने और अपने प्रोजेक्ट्स में वैकल्पिक कार्यान्वयन दृष्टिकोणों की खोज करने में मदद करेंगे।

- [Aspose.Words for Java में DocumentBuilder का उपयोग करके फ़ॉर्म फ़ील्ड बनाना और सामग्री जोड़ना कैसे करें](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Aspose.Words for .NET के साथ Word दस्तावेज़ में कॉम्बो बॉक्स फ़ॉर्म फ़ील्ड जोड़ें](/words/english/net/add-content-using-documentbuilder/insert-combo-box/)
- [Aspose.Words Java के साथ Word दस्तावेज़ लोड करना कैसे करें: व्यापक गाइड](/words/english/java/document-operations/aspose-words-java-master-word-processing/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}