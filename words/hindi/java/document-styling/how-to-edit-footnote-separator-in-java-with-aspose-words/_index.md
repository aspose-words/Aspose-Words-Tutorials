---
category: general
date: 2026-10-04
description: Aspose.Words का उपयोग करके जावा में फुटनोट सेपरेटर को संपादित करें –
  जानें कैसे फुटनोट सेपरेटर बदलें और वर्ड दस्तावेज़ों में एक कस्टम सेपरेटर शब्द जोड़ें।
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- edit footnote separator
- change footnote separator
- custom separator word
language: hi
lastmod: 2026-10-04
og_description: Aspose.Words के साथ जावा में फुटनोट सेपरेटर को संपादित करें। यह ट्यूटोरियल
  दिखाता है कि फुटनोट सेपरेटर को कैसे बदलें और एक कस्टम सेपरेटर शब्द कैसे डालें।
og_image_alt: Screenshot of a Java IDE showing code that edits a footnote separator
  in a Word document
og_title: जावा में फुटनोट सेपरेटर संपादित करें – पूर्ण Aspose.Words गाइड
schemas:
- author: Aspose
  dateModified: '2026-10-04'
  description: Edit footnote separator in Java using Aspose.Words – learn how to change
    footnote separator and add a custom separator word to Word documents.
  headline: How to edit footnote separator in Java with Aspose.Words
  type: TechArticle
- description: Edit footnote separator in Java using Aspose.Words – learn how to change
    footnote separator and add a custom separator word to Word documents.
  name: How to edit footnote separator in Java with Aspose.Words
  steps:
  - name: '**`clearChildren()`** removes any existing runs, ensuring the separator
      contains only the text you provide.'
    text: '**`clearChildren()`** removes any existing runs, ensuring the separator
      contains only the text you provide.'
  - name: '**`new Run(document, "—")`** creates a text node with the desired separator.
      The `Run` object respects the document’s style, so the separator inherits the
      formatting of the original footnote separator.'
    text: '**`new Run(document, "—")`** creates a text node with the desired separator.
      The `Run` object respects the document’s style, so the separator inherits the
      formatting of the original footnote separator.'
  - name: '**`appendChild(customRun)`** inserts the new run into the separator paragraph.'
    text: '**`appendChild(customRun)`** inserts the new run into the separator paragraph.'
  type: HowTo
tags:
- Aspose.Words
- Java
- Footnotes
- Word processing
title: जावा में Aspose.Words के साथ फुटनोट सेपरेटर को कैसे संपादित करें
url: /hi/java/document-styling/how-to-edit-footnote-separator-in-java-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Java के साथ Aspose.Words में फुटनोट सेपरेटर को कैसे संपादित करें

यदि आपको Word दस्तावेज़ में **footnote separator** को संपादित करने की आवश्यकता है, तो यह गाइड आपको बिल्कुल बताता है कि इसे Java में कैसे किया जाए। चाहे आप **footnote separator** को डैश, स्टार, या किसी भी **custom separator word** में बदलना चाहते हों, नीचे दिए गए चरण सभी आवश्यक चीज़ें कवर करते हैं।

आप सीखेंगे कि कैसे `.docx` फ़ाइल को लोड किया जाए, विशेष सेपरेटर सेक्शन को प्राप्त किया जाए, उसकी सामग्री को संशोधित किया जाए, और परिणाम को सहेजा जाए। कोई बाहरी स्क्रिप्ट या मैनुअल एडिटिंग आवश्यक नहीं – सब कुछ Aspose.Words for Java लाइब्रेरी के साथ प्रोग्रामेटिकली किया जाता है।

## आवश्यकताएँ

- Java 17 या बाद का संस्करण स्थापित हो।
- निर्भरताओं को प्रबंधित करने के लिए Maven या Gradle (उदाहरण में Maven उपयोग किया गया है)।
- एक वैध Aspose.Words for Java लाइसेंस (या मुफ्त मूल्यांकन कुंजी)।
- एक Word दस्तावेज़ जिसमें पहले से फुटनोट्स मौजूद हों (सेपरेटर केवल तब मौजूद होता है जब फुटनोट्स हों)।

## अपने प्रोजेक्ट में Aspose.Words जोड़ें

यदि आप Maven का उपयोग करते हैं, तो अपने `pom.xml` में निम्नलिखित डिपेंडेंसी जोड़ें:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.11</version> <!-- Use the latest version -->
</dependency>
```

Gradle के लिए, जोड़ें:

```gradle
implementation 'com.aspose:aspose-words:24.11'
```

## चरण 1: फुटनोट्स वाले दस्तावेज़ को लोड करें

पहला चरण वह Word फ़ाइल खोलना है जिसे आप संशोधित करना चाहते हैं। Aspose.Words फ़ाइल को एक `Document` ऑब्जेक्ट में पढ़ता है, जो आपको दस्तावेज़ के सभी भागों, जिसमें फुटनोट सेपरेटर भी शामिल हैं, तक पूर्ण पहुँच देता है।

```java
import com.aspose.words.*;

public class EditFootnoteSeparator {
    public static void main(String[] args) throws Exception {
        // Path to the source document
        String inputPath = "YOUR_DIRECTORY/docWithNotes.docx";

        // Load the document
        Document document = new Document(inputPath);
        
        // Continue with separator editing...
    }
}
```

**यह क्यों महत्वपूर्ण है:** दस्तावेज़ को लोड करने से एक इन‑मेमोरी प्रतिनिधित्व बनता है, इसलिए आप मूल फ़ाइल को तब तक नहीं छूते जब तक आप स्पष्ट रूप से इसे सहेज नहीं लेते, आप सुरक्षित रूप से किसी भी नोड को संशोधित कर सकते हैं।

## चरण 2: फुटनोट सेपरेटर सेक्शन प्राप्त करें

Word फुटनोट सेपरेटर को एक विशेष `Separator` नोड के रूप में संग्रहीत करता है। Aspose.Words सीधे इसे प्राप्त करने के लिए `getFootnoteSeparator()` मेथड प्रदान करता है।

```java
// Get the footnote separator (the line that appears between footnotes and the main text)
Separator footnoteSeparator = document.getFootnoteSeparator();

if (footnoteSeparator == null) {
    System.out.println("The document does not contain a footnote separator.");
    return;
}
```

**प्रो टिप:** सेपरेटर नोड केवल तभी मौजूद होता है जब दस्तावेज़ में कम से कम एक फुटनोट हो। यदि आप बिना फुटनोट्स के दस्तावेज़ को संपादित करने की कोशिश करते हैं, तो `getFootnoteSeparator()` `null` लौटाता है, इसलिए हमेशा इस स्थिति की जाँच करें।

## चरण 3: एक कस्टम सेपरेटर शब्द डालें

अब आप सेपरेटर की उपस्थिति बदल सकते हैं। इस उदाहरण में हम डिफ़ॉल्ट लाइन को एक एम डैश (`—`) से बदलते हैं। आप इसके बजाय कोई भी **custom separator word** जैसे `"NOTE:"` या `"***"` डाल सकते हैं।

```java
// Access the first paragraph of the separator (there is usually only one)
Paragraph separatorParagraph = footnoteSeparator.getParagraphs().get(0);

// Clear any existing runs (text fragments) to avoid mixing old and new content
separatorParagraph.clearChildren();

// Append a new Run that contains the custom separator word
Run customRun = new Run(document, "—");   // Replace "—" with any text you need
separatorParagraph.appendChild(customRun);
```

### कोड क्या करता है

1. **`clearChildren()`** मौजूदा सभी रन को हटा देता है, यह सुनिश्चित करता है कि सेपरेटर में केवल वह टेक्स्ट हो जो आप प्रदान करते हैं।
2. **`new Run(document, "—")`** वांछित सेपरेटर के साथ एक टेक्स्ट नोड बनाता है। `Run` ऑब्जेक्ट दस्तावेज़ की शैली का सम्मान करता है, इसलिए सेपरेटर मूल फुटनोट सेपरेटर की फ़ॉर्मेटिंग को विरासत में लेता है।
3. **`appendChild(customRun)`** नए रन को सेपरेटर पैराग्राफ में जोड़ता है।

आप रन पर फ़ॉर्मेटिंग भी लागू कर सकते हैं, उदाहरण के लिए:

```java
customRun.getFont().setBold(true);
customRun.getFont().setSize(10);
customRun.getFont().setColor(Color.BLUE);
```

## चरण 4: संशोधित दस्तावेज़ को सहेजें

सेपरेटर को संपादित करने के बाद, दस्तावेज़ को डिस्क पर वापस लिखें। मूल फ़ाइल को अपरिवर्तित रखने के लिए एक नया फ़ाइल नाम चुनें।

```java
// Path to the output document
String outputPath = "YOUR_DIRECTORY/ModifiedNotes.docx";

// Save the changes
document.save(outputPath);

System.out.println("Footnote separator edited successfully. Saved to " + outputPath);
```

**परिणाम सत्यापन:** Microsoft Word में `ModifiedNotes.docx` खोलें। फुटनोट सेपरेटर अब डिफ़ॉल्ट लाइन के बजाय कस्टम डैश (या जो भी शब्द आपने चुना है) दिखाना चाहिए।

## कई फुटनोट सेपरेटर को संभालना

Word तीन विशेष सेपरेटर प्रकारों का समर्थन करता है:

| सेपरेटर प्रकार | मेथड |
|----------------|----------------------------|
| Footnote separator | `getFootnoteSeparator()` |
| Footnote continuation separator | `getFootnoteContinuationSeparator()` |
| Footnote separator for the first page | `getFootnoteSeparatorForFirstPage()` |

यदि आपको सभी को संपादित करने की आवश्यकता है, तो प्रत्येक मेथड के लिए **Step 2** और **Step 3** दोहराएँ। उदाहरण:

```java
Separator continuation = document.getFootnoteContinuationSeparator();
if (continuation != null) {
    // Apply the same custom run or a different one
    Paragraph p = continuation.getParagraphs().get(0);
    p.clearChildren();
    p.appendChild(new Run(document, "*"));
}
```

## सामान्य समस्याएँ और उन्हें कैसे टालें

| समस्या | कारण | समाधान |
|-------|-------|-----|
| सहेजने के बाद कोई सेपरेटर नहीं दिखता | दस्तावेज़ में फुटनोट नहीं थे → सेपरेटर नोड `null` है | संपादन से पहले कम से कम एक फुटनोट जोड़ें, या प्रोग्रामेटिकली एक डमी फुटनोट बनाएं। |
| सेपरेटर में अतिरिक्त स्पेस दिखते हैं | मौजूदा रन साफ़ नहीं किए गए थे | नया रन जोड़ने से पहले `clearChildren()` कॉल करें। |
| फ़ॉर्मेटिंग अलग दिखती है | रन मूल सेपरेटर की शैली विरासत में लेता है | यदि आपको विशिष्ट रूप चाहिए तो `Run` पर फ़ॉन्ट प्रॉपर्टीज़ स्पष्ट रूप से सेट करें। |

## पूर्ण कार्यशील उदाहरण

सभी भागों को मिलाकर, यहाँ एक स्वतंत्र Java क्लास है जिसे आप कॉपी, कंपाइल और रन कर सकते हैं:

```java
import com.aspose.words.*;
import java.awt.Color;

public class EditFootnoteSeparator {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Load the document
        String inputPath = "YOUR_DIRECTORY/docWithNotes.docx";
        Document doc = new Document(inputPath);

        // 2️⃣ Retrieve the footnote separator
        Separator footnoteSeparator = doc.getFootnoteSeparator();
        if (footnoteSeparator == null) {
            System.out.println("Document has no footnote separator.");
            return;
        }

        // 3️⃣ Replace the separator with a custom word (e.g., an em dash)
        Paragraph para = footnoteSeparator.getParagraphs().get(0);
        para.clearChildren();                       // Remove old runs
        Run customRun = new Run(doc, "—");          // Change "—" to any word you need
        customRun.getFont().setBold(true);         // Optional styling
        customRun.getFont().setSize(9);
        customRun.getFont().setColor(Color.DARK_GRAY);
        para.appendChild(customRun);

        // 4️⃣ Save the modified document
        String outputPath = "YOUR_DIRECTORY/ModifiedNotes.docx";
        doc.save(outputPath);

        System.out.println("Footnote separator edited successfully.");
    }
}
```

प्रोग्राम चलाएँ, फिर `ModifiedNotes.docx` खोलें यह पुष्टि करने के लिए कि सेपरेटर अपडेट हो गया है।

## निष्कर्ष

अब आप जानते हैं कि Java और Aspose.Words का उपयोग करके Word दस्तावेज़ में **footnote separator** को कैसे **संपादित** किया जाता है। ट्यूटोरियल ने दस्तावेज़ लोड करने, विशेष सेपरेटर नोड प्राप्त करने, एक **custom separator word** डालने, और परिणाम सहेजने को कवर किया। इन चरणों का पालन करके आप निरंतरता सेक्शन या प्रथम‑पृष्ठ फुटनोट्स के लिए भी **footnote separator** को **बदल** सकते हैं।

अगले चरणों में आप देख सकते हैं:

- प्रथम‑पृष्ठ फुटनोट्स के लिए विभिन्न सेपरेटर जोड़ना (`getFootnoteSeparatorForFirstPage()`)।
- जब कोई फुटनोट न हो तो प्रोग्रामेटिकली फुटनोट बनाना।
- Aspose.Words का उपयोग करके फुटनोट टेक्स्ट को स्टाइल करना (फ़ॉन्ट, रंग, इंडेंटेशन)।

अपने दस्तावेज़ की ब्रांडिंग से मेल खाने के लिए अन्य अक्षर या शब्दों के साथ प्रयोग करने में संकोच न करें। कोडिंग का आनंद लें!

## आगे आप क्या सीखें?

निम्नलिखित ट्यूटोरियल्स उन निकट-संबंधित विषयों को कवर करते हैं जो इस गाइड में प्रदर्शित तकनीकों पर आधारित हैं। प्रत्येक संसाधन में पूर्ण कार्यशील कोड उदाहरण और चरण‑दर‑चरण व्याख्याएँ शामिल हैं जो आपको अतिरिक्त API सुविधाओं में महारत हासिल करने और अपने प्रोजेक्ट्स में वैकल्पिक कार्यान्वयन दृष्टिकोणों का अन्वेषण करने में मदद करती हैं।

- [Word में दस्तावेज़ शैली सेपरेटर डालें](/words/english/net/programming-with-styles-and-themes/insert-style-separator/)
- [Word दस्तावेज़ में पैराग्राफ शैली सेपरेटर प्राप्त करें](/words/english/net/document-formatting/get-paragraph-style-separator/)
- [Aspose.Words Java के साथ Word दस्तावेज़ लोड करने की पूरी गाइड](/words/english/java/document-operations/aspose-words-java-master-word-processing/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}