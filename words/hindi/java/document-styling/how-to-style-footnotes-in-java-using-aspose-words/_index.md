---
category: general
date: 2026-10-07
description: जावा में फुटनोट को स्टाइल कैसे करें – फुटनोट सेपरेटर बदलना सीखें, फुटनोट
  सेपरेटर फॉर्मेटिंग संपादित करें, और स्टाइल किए गए फुटनोट के साथ दस्तावेज़ सहेजें।
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to style footnotes
- change footnote separator
- edit footnote separator
- format footnote separator
- access footnote separator
language: hi
lastmod: 2026-10-07
og_description: जावा में Aspose.Words के साथ फुटनोट को स्टाइल करने का तरीका। यह ट्यूटोरियल
  दिखाता है कि फुटनोट सेपरेटर को कैसे बदलें, फुटनोट सेपरेटर फॉर्मेटिंग को कैसे संपादित
  करें, और एक परिष्कृत दस्तावेज़ तैयार करें।
og_image_alt: Screenshot illustrating how to style footnotes in a Java Word processing
  example
og_title: जावा में फुटनोट्स को कैसे स्टाइल करें – पूर्ण प्रोग्रामिंग गाइड
schemas:
- author: Aspose
  dateModified: '2026-10-07'
  description: how to style footnotes in Java – learn to change footnote separator,
    edit footnote separator formatting, and save the document with styled footnotes.
  headline: how to style footnotes in Java using Aspose.Words
  type: TechArticle
- description: how to style footnotes in Java – learn to change footnote separator,
    edit footnote separator formatting, and save the document with styled footnotes.
  name: how to style footnotes in Java using Aspose.Words
  steps:
  - name: Load the source document.
    text: Load the source document.
  - name: Iterate through each footnote and **access footnote separator** runs.
    text: Iterate through each footnote and **access footnote separator** runs.
  - name: Apply the desired styling (bold, color, underline, etc.).
    text: Apply the desired styling (bold, color, underline, etc.).
  - name: Save the document with the updated footnote separator.
    text: Save the document with the updated footnote separator.
  type: HowTo
tags:
- Aspose.Words
- Java
- Word automation
title: Aspose.Words का उपयोग करके जावा में फुटनोट्स को कैसे स्टाइल करें
url: /hi/java/document-styling/how-to-style-footnotes-in-java-using-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Java में Aspose.Words का उपयोग करके फुटनोट्स को स्टाइल कैसे करें

यदि आपको Java का उपयोग करके Word दस्तावेज़ में फुटनोट्स को स्टाइल करने की आवश्यकता है, तो यह गाइड Aspose.Words के साथ **how to style footnotes** दिखाता है। आप सीखेंगे कि फुटनोट सेपरेटर को कैसे बदलें, फुटनोट सेपरेटर फ़ॉर्मेटिंग को कैसे संपादित करें, और कुछ स्पष्ट चरणों में संशोधित दस्तावेज़ को कैसे सहेजें।

फुटनोट्स के साथ काम करना अक्सर मुख्य पाठ और फुटनोट सूची के बीच दिखाई देने वाली सेपरेटर लाइन को समायोजित करने का मतलब होता है। इस ट्यूटोरियल के अंत तक आप **access footnote separator** रन को एक्सेस कर सकेंगे, बोल्ड या रंग स्टाइल लागू कर सकेंगे, और अपने IDE को छोड़े बिना फुटनोट्स की समग्र उपस्थिति को नियंत्रित कर सकेंगे।

## पूर्वापेक्षाएँ

शुरू करने से पहले सुनिश्चित करें कि आपके पास है:

* Java 17 या नया स्थापित हो।
* Maven 3.6+ (या Gradle) ताकि निर्भरताओं का प्रबंधन किया जा सके।
* एक वैध Aspose.Words for Java लाइसेंस (इस उदाहरण के लिए मुफ्त मूल्यांकन काम करता है)।
* एक स्रोत Word दस्तावेज़ जिसमें कम से कम एक फुटनोट हो (उदाहरण के लिए `Footnotes.docx`)।

ये आवश्यकताएँ सुनिश्चित करती हैं कि कोड आधुनिक Java रनटाइम पर सुचारू रूप से चले और आपको **how to style footnotes** तकनीक पर ध्यान केंद्रित करने दे, सेट‑अप समस्याओं से नहीं।

## फुटनोट्स को स्टाइल कैसे करें – समग्र दृष्टिकोण

प्रक्रिया चार तार्किक चरणों में विभाजित है:

1. स्रोत दस्तावेज़ लोड करें।
2. प्रत्येक फुटनोट पर इटररेट करें और **access footnote separator** रन को प्राप्त करें।
3. वांछित स्टाइल लागू करें (बोल्ड, रंग, अंडरलाइन, आदि)।
4. अपडेटेड फुटनोट सेपरेटर के साथ दस्तावेज़ सहेजें।

प्रत्येक चरण सीधे कोड की एक पंक्ति से जुड़ा है, जिससे कार्यान्वयन को समझना और संशोधित करना आसान हो जाता है।

## चरण 1: Maven प्रोजेक्ट सेट अप करें

एक नया Maven प्रोजेक्ट बनाएं (या मौजूदा में जोड़ें) और Aspose.Words निर्भरता शामिल करें:

```xml
<!-- pom.xml -->
<dependencies>
    <dependency>
        <groupId>com.aspose</groupId>
        <artifactId>aspose-words</artifactId>
        <version>24.10</version> <!-- Use the latest version -->
    </dependency>
</dependencies>
```

> **Pro tip:** लाइब्रेरी संस्करण को अद्यतित रखें; नए रिलीज़ फुटनोट हैंडलिंग के लिए बग फिक्स जोड़ते हैं।

## चरण 2: फुटनोट्स वाले स्रोत दस्तावेज़ को लोड करें

```java
import com.aspose.words.*;

public class FootnoteStyler {
    public static void main(String[] args) throws Exception {
        // Load the Word file that has footnotes.
        Document doc = new Document("YOUR_DIRECTORY/Footnotes.docx");
```

`Document` ऑब्जेक्ट पूरे Word फ़ाइल का प्रतिनिधित्व करता है। इसे लोड करना **how to style footnotes** में पहला ठोस कदम है।

## चरण 3: प्रत्येक फुटनोट पर इटररेट करें और **access footnote separator**

```java
        // Iterate through all footnotes in the document.
        for (Footnote footnote : (Iterable<Footnote>) doc.getFootnotes()) {
            // The separator is a Run that appears between the main text and the footnote list.
            Run separator = footnote.getSeparator();

            // Guard against unexpected null values (rare but possible with corrupted files).
            if (separator != null) {
                // Apply desired styling to the separator run.
                separator.getFont().setBold(true);          // change footnote separator to bold
                separator.getFont().setColor(Color.BLUE);   // optional: set a custom color
                separator.getFont().setUnderline(Underline.SINGLE);
            }
        }
```

इस ब्लॉक में हम `footnote.getSeparator()` के माध्यम से **access footnote separator** रन प्राप्त करते हैं। `Run` ऑब्जेक्ट टेक्स्ट स्टाइलिंग पर पूर्ण नियंत्रण देता है, जिससे आप एक ही कोड लाइन से **change footnote separator** की उपस्थिति बदल सकते हैं।

### `Footnote.getSeparator()` क्यों उपयोग करें

* `Footnote.getSeparator()` वह रन लौटाता है जिसमें सेपरेटर लाइन होती है।  
* यह एकमात्र API एंट्री पॉइंट है जो आपको **edit footnote separator** सीधे करने देता है।  
* रन की `Font` प्रॉपर्टीज़ को संशोधित करने से सभी फुटनोट्स के लिए दृश्य सेपरेटर अपडेट हो जाता है जो समान स्टाइल साझा करते हैं।

## चरण 4: (वैकल्पिक) कंटिन्यूएशन सेपरेटर और नोटिस को स्टाइल करें

Word तीन प्रकार के सेपरेटर को अलग करता है:

| Type                     | API method                | Typical use case |
|--------------------------|---------------------------|------------------|
| प्राथमिक सेपरेटर        | `Footnote.getSeparator()` | मुख्य पाठ को पहले फुटनोट से अलग करना |
| कंटिन्यूएशन सेपरेटर   | `Footnote.getContinuationSeparator()` | बाद के फुटनोट पृष्ठों को अलग करना |
| कंटिन्यूएशन नोटिस      | `Footnote.getContinuationNotice()` | बाद के पृष्ठों पर “Continued…” टेक्स्ट दिखाना |

यदि आप कंटिन्यूएशन पृष्ठों के लिए **format footnote separator** भी लागू करना चाहते हैं, तो लूप के अंदर निम्न कोड जोड़ें:

```java
            // Continuation separator (optional)
            Run contSeparator = footnote.getContinuationSeparator();
            if (contSeparator != null) {
                contSeparator.getFont().setItalic(true);
                contSeparator.getFont().setSize(9);
            }

            // Continuation notice (optional)
            Run contNotice = footnote.getContinuationNotice();
            if (contNotice != null) {
                contNotice.getFont().setColor(Color.GRAY);
            }
```

ये स्निपेट्स दिखाते हैं कि कैसे **edit footnote separator** ऑब्जेक्ट्स को प्राथमिक लाइन से आगे तक संशोधित किया जा सकता है, जिससे आपको फुटनोट लेआउट पर पूर्ण नियंत्रण मिलता है।

## चरण 5: संशोधित दस्तावेज़ सहेजें

```java
        // Save the document with the styled footnote separators.
        doc.save("YOUR_DIRECTORY/FootnotesStyled.docx");
    }
}
```

फ़ाइल को सहेजने से सभी स्टाइलिंग परिवर्तन डिस्क पर लिखे जाते हैं, जिससे **how to style footnotes** वर्कफ़्लो पूरा हो जाता है।

## पूर्ण, चलाने योग्य उदाहरण

सभी हिस्सों को मिलाकर एक स्व-निहित प्रोग्राम बनता है जिसे आप कॉपी, कंपाइल और रन कर सकते हैं:

```java
import com.aspose.words.*;
import java.awt.Color;

/**
 * Demonstrates how to style footnotes in a Word document using Aspose.Words for Java.
 * The example loads a document, makes the footnote separator bold and blue,
 * optionally styles continuation elements, and saves the result.
 */
public class FootnoteStyler {
    public static void main(String[] args) throws Exception {
        // 1. Load the source document.
        Document doc = new Document("YOUR_DIRECTORY/Footnotes.docx");

        // 2. Iterate through each footnote.
        for (Footnote footnote : (Iterable<Footnote>) doc.getFootnotes()) {
            // 3a. Access and style the primary separator.
            Run separator = footnote.getSeparator();
            if (separator != null) {
                separator.getFont().setBold(true);          // change footnote separator
                separator.getFont().setColor(Color.BLUE);   // set a custom color
                separator.getFont().setUnderline(Underline.SINGLE);
            }

            // 3b. (Optional) Style continuation separator.
            Run contSeparator = footnote.getContinuationSeparator();
            if (contSeparator != null) {
                contSeparator.getFont().setItalic(true);
                contSeparator.getFont().setSize(9);
            }

            // 3c. (Optional) Style continuation notice.
            Run contNotice = footnote.getContinuationNotice();
            if (contNotice != null) {
                contNotice.getFont().setColor(Color.GRAY);
            }
        }

        // 4. Save the modified document.
        doc.save("YOUR_DIRECTORY/FootnotesStyled.docx");
    }
}
```

**Expected output:** `FootnotesStyled.docx` को Microsoft Word में खोलें। मुख्य पाठ और फुटनोट सूची के बीच की सेपरेटर लाइन बोल्ड, नीली और अंडरलाइन दिखेगी। यदि दस्तावेज़ में कई पृष्ठों में फैले फुटनोट्स हैं, तो कंटिन्यूएशन सेपरेटर इटैलिक और छोटा होगा, जबकि कंटिन्यूएशन नोटिस ग्रे रंग में दिखाई देगा।

## सामान्य प्रश्न और एज‑केस हैंडलिंग

| Question | Answer |
|----------|--------|
| *यदि किसी फुटनोट में सेपरेटर नहीं है तो क्या होगा?* | `Footnote.getSeparator()` `null` लौटाता है। कोड स्टाइल लागू करने से पहले `null` की जाँच करता है, जिससे `NullPointerException` से बचा जा सके। |
| *क्या मैं केवल पहले फुटनोट पर अलग स्टाइल लागू कर सकता हूँ?* | हाँ। लूप के अंदर एक काउंटर जोड़ें और जब `index == 0` हो तो कंडीशनल फ़ॉर्मेटिंग लागू करें। |
| *क्या यह .doc फ़ाइलों के साथ काम करता है?* | Aspose.Words `.doc` और `.docx` दोनों का समर्थन करता है। उचित पाथ लोड करें और वही API कॉल्स लागू होंगी। |
| *मैं मूल स्टाइल में कैसे वापस जाऊँ?* | मूल `Font` को स्टोर करें |

## अगला आप क्या सीखें?

निम्नलिखित ट्यूटोरियल्स इस गाइड में दिखाए गए तकनीकों पर आधारित निकट-संबंधित विषयों को कवर करते हैं। प्रत्येक संसाधन में पूर्ण कार्यशील कोड उदाहरण और चरण‑दर‑चरण व्याख्याएँ शामिल हैं, जो आपको अतिरिक्त API फीचर्स में महारत हासिल करने और अपने प्रोजेक्ट्स में वैकल्पिक कार्यान्वयन दृष्टिकोणों का अन्वेषण करने में मदद करेंगे।

- [How to save document as pdf with Aspose.Words for Java](/words/english/java/document-loading-and-saving/saving-documents-as-pdf/)
- [How to Change Cell Borders in Tables – Aspose.Words for Java](/words/english/java/document-conversion-and-export/formatting-tables-and-table-styles/)
- [How to Add Watermark – Document Conversion and Export with Aspose.Words for Java](/words/english/java/document-conversion-and-export/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}