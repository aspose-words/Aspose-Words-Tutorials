---
category: general
date: 2026-11-15
description: जावा में LoadOptions का उपयोग करके मार्कडाउन दस्तावेज़ को लोड करना सीखें,
  जिससे अंडरलाइन फ़ॉर्मेटिंग बनी रहे और आयात व्यवहार को नियंत्रित किया जा सके।
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- load markdown document
- LoadOptions
- import underline formatting
- Document class
- custom import behavior
language: hi
lastmod: 2026-11-15
og_description: LoadOptions के साथ जावा में मार्कडाउन दस्तावेज़ लोड करें। अंडरलाइन
  फ़ॉर्मेटिंग को संरक्षित रखें और केवल कुछ लाइनों के कोड में आयात व्यवहार को सूक्ष्म‑समायोजित
  करें।
og_image_alt: Screenshot of Java code loading a markdown document with custom LoadOptions
og_title: जावा में मार्कडाउन दस्तावेज़ लोड करें – कस्टम इम्पोर्ट विकल्प गाइड
schemas:
- author: GroupDocs
  dateModified: '2026-11-15'
  description: Learn how to load markdown document in Java using LoadOptions to preserve
    underline formatting and control import behavior.
  headline: How to load markdown document in Java with custom import options
  type: TechArticle
- description: Learn how to load markdown document in Java using LoadOptions to preserve
    underline formatting and control import behavior.
  name: How to load markdown document in Java with custom import options
  steps:
  - name: Why you need a `LoadOptions` instance
    text: '* **Predictable results** – Without explicit options the parser may drop
      or change formatting. * **Future‑proofing** – Adding new flags later (e.g.,
      handling tables or code blocks) is as simple as setting another property.'
  - name: When to enable this flag
    text: '* Your markdown contains emphasis that relies on underlining (common in
      technical documentation). * You are generating PDFs or HTML where visual fidelity
      matters.'
  - name: Verifying the load
    text: 'You can quickly confirm that the document loaded correctly:'
  - name: Pro tip
    text: 'Always log the effective `LoadOptions` before loading the file. This makes
      debugging easier when the document doesn’t look as expected:'
  type: HowTo
tags:
- Java
- Markdown
- File I/O
title: जावा में कस्टम इम्पोर्ट विकल्पों के साथ मार्कडाउन दस्तावेज़ कैसे लोड करें
url: /hi/java/document-loading-and-saving/how-to-load-markdown-document-in-java-with-custom-import-opt/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Java में कस्टम इम्पोर्ट विकल्पों के साथ मार्कडाउन दस्तावेज़ कैसे लोड करें

यदि आपको विशिष्ट फ़ॉर्मेटिंग को बनाए रखते हुए **मार्कडाउन दस्तावेज़ लोड** करने की आवश्यकता है, तो यह गाइड आपको एक संक्षिप्त, प्रोडक्शन‑रेडी समाधान दिखाता है। `LoadOptions` इंस्टेंस को कॉन्फ़िगर करके आप स्रोत फ़ाइल से अंडरलाइन स्टाइलिंग और अन्य फीचर्स को कैसे इम्पोर्ट किया जाए, इसे नियंत्रित कर सकते हैं।

यह ट्यूटोरियल वह सब कुछ कवर करता है जो आपको जानना आवश्यक है: आवश्यक इम्पोर्ट्स, चरण‑दर‑चरण कोड, प्रत्येक सेटिंग क्यों महत्वपूर्ण है, और सामान्य pitfalls से बचना। कोई बाहरी दस्तावेज़ आवश्यक नहीं—सिर्फ कॉपी, पेस्ट और रन करें।

## आवश्यकताएँ

* Java 17 या बाद का संस्करण स्थापित हो।
* वह लाइब्रेरी जो `Document` और `LoadOptions` प्रदान करती है (उदाहरण के लिए, **GroupDocs.Viewer** या **Aspose.Words** जैसी मार्कडाउन प्रोसेसिंग SDK)। यदि आप अलग पैकेज उपयोग करते हैं तो इम्पोर्ट स्टेटमेंट्स को समायोजित करें।
* `input.md` नामक मार्कडाउन फ़ाइल को ऐसी डायरेक्टरी में रखें जिसे आप अपने कोड से रेफ़र कर सकें।

## चरण 1: इम्पोर्ट व्यवहार को कस्टमाइज़ करने के लिए `LoadOptions` ऑब्जेक्ट बनाएं

```java
// Import the necessary classes from the SDK
import com.example.sdk.LoadOptions;
import com.example.sdk.Document;

// Step 1: Instantiate LoadOptions for fine‑grained control
LoadOptions loadOptions = new LoadOptions();
```

`LoadOptions` वह केंद्रीय क्लास है जो **Document class** को स्रोत फ़ाइल की व्याख्या कैसे करनी है, बताती है। एक इंस्टेंस बनाकर आप दर्जनों फ़्लैग्स तक पहुंच प्राप्त करते हैं—इनमें से एक अंडरलाइन फ़ॉर्मेटिंग को इम्पोर्ट करने की क्षमता है।

### आपको `LoadOptions` इंस्टेंस की क्यों आवश्यकता है

* **Predictable results** – स्पष्ट विकल्पों के बिना पार्सर फ़ॉर्मेटिंग को हटा या बदल सकता है।
* **Future‑proofing** – बाद में नए फ़्लैग्स जोड़ना (जैसे, टेबल्स या कोड ब्लॉक्स को संभालना) बस एक और प्रॉपर्टी सेट करने जितना सरल है।

## चरण 2: अंडरलाइन फ़ॉर्मेटिंग के इम्पोर्ट को सक्षम करें

```java
// Step 2: Turn on underline import
loadOptions.setImportUnderlineFormatting(true);
```

`setImportUnderlineFormatting(true)` कॉल **import underline formatting** फ़्लैग को सक्रिय करती है। जब यह फ़्लैग `true` हो, तो मूल मार्कडाउन में अंडरलाइन किया गया कोई भी टेक्स्ट परिणामी `Document` ऑब्जेक्ट में वही शैली बनाए रखेगा।

### इस फ़्लैग को कब सक्षम करें

* आपके मार्कडाउन में अंडरलाइन पर निर्भर इम्पेर्सिस मौजूद है (तकनीकी दस्तावेज़ीकरण में सामान्य)।
* आप PDF या HTML बना रहे हैं जहाँ विज़ुअल फ़िडेलिटी महत्वपूर्ण है।

यदि आप इस चरण को छोड़ देते हैं, तो अंडरलाइन किया गया टेक्स्ट साधारण टेक्स्ट के रूप में दिखेगा, जिससे विज़ुअल संकेतों पर निर्भर पाठकों को भ्रम हो सकता है।

## चरण 3: कॉन्फ़िगर किए गए `LoadOptions` का उपयोग करके मार्कडाउन फ़ाइल लोड करें

```java
// Step 3: Load the markdown document with the custom options
Document markdownDoc = new Document("YOUR_DIRECTORY/input.md", loadOptions);
```

`loadOptions` इंस्टेंस को `Document` कंस्ट्रक्टर में पास करने से **Document class** को `input.md` पढ़ते समय कस्टम इम्पोर्ट नियम लागू करने का निर्देश मिलता है।

### लोड की पुष्टि

आप जल्दी से पुष्टि कर सकते हैं कि दस्तावेज़ सही ढंग से लोड हुआ है:

```java
System.out.println("Document loaded. Page count: " + markdownDoc.getPageCount());
```

यदि फ़ाइल मौजूद नहीं है या पाथ गलत है, तो कंस्ट्रक्टर एक सूचनात्मक एक्सेप्शन फेंकेगा, जिससे आप त्रुटि को सहजता से संभाल सकेंगे।

## पूर्ण, चलाने योग्य उदाहरण

नीचे एक पूर्ण प्रोग्राम दिया गया है जिसे आप जैसा है वैसा ही कंपाइल और रन कर सकते हैं (पैकेज नाम को अपने SDK के अनुसार बदलें)।

```java
import com.example.sdk.LoadOptions;
import com.example.sdk.Document;

public class LoadMarkdownExample {
    public static void main(String[] args) {
        // 1️⃣ Create LoadOptions to customize import behavior
        LoadOptions loadOptions = new LoadOptions();

        // 2️⃣ Enable importing of underline formatting from the source
        loadOptions.setImportUnderlineFormatting(true);

        // 3️⃣ Load the markdown document using the configured options
        try {
            Document markdownDoc = new Document("YOUR_DIRECTORY/input.md", loadOptions);
            System.out.println("Markdown document loaded successfully.");
            System.out.println("Page count: " + markdownDoc.getPageCount());
        } catch (Exception e) {
            System.err.println("Failed to load markdown document: " + e.getMessage());
        }
    }
}
```

**अपेक्षित आउटपुट (मान लेते हैं कि फ़ाइल मौजूद है और कम से कम एक पेज की सामग्री रखती है):**

```
Markdown document loaded successfully.
Page count: 1
```

यदि फ़ाइल नहीं मिलती, तो आपको इस प्रकार का एरर मैसेज दिखेगा:

```
Failed to load markdown document: File not found: YOUR_DIRECTORY/input.md
```

## किनारे के मामलों और सर्वोत्तम‑प्रैक्टिस टिप्स

| Situation | What to watch for | Recommended approach |
|-----------|-------------------|----------------------|
| **फ़ाइल पाथ में स्पेस हैं** | `new Document("C:/My Docs/input.md", ...)` कुछ OS पर टूट सकता है। | `java.nio.file.Paths` का उपयोग करके पाथ सुरक्षित रूप से बनाएं: `Paths.get("C:", "My Docs", "input.md").toString()` |
| **बड़ी मार्कडाउन फ़ाइलें** | बहुत बड़ी फ़ाइलों को लोड करने से मेमोरी की खपत बढ़ सकती है। | यदि SDK इसे सपोर्ट करता है तो स्ट्रीमिंग विकल्प सक्षम करें, या JVM हीप (`-Xmx`) बढ़ाएँ। |
| **अंडरलाइन सपोर्ट गायब है** | कुछ SDK संस्करण अंडरलाइन फ़्लैग को अनदेखा करते हैं। | `setImportUnderlineFormatting` को लागू करने वाले संस्करण का उपयोग कर रहे हैं, यह सुनिश्चित करें। रिलीज़ नोट्स देखें। |
| **एकाधिक इम्पोर्ट फ़्लैग्स की आवश्यकता** | आपको टेबल्स, कोड ब्लॉक्स आदि को भी संरक्षित करने की आवश्यकता हो सकती है। | `loadOptions` पर अतिरिक्त सेटर्स चेन करें, उदाहरण के लिए `loadOptions.setImportTables(true);` |

### प्रो टिप

फ़ाइल लोड करने से पहले हमेशा प्रभावी `LoadOptions` को लॉग करें। इससे डिबगिंग आसान हो जाती है जब दस्तावेज़ अपेक्षित रूप में नहीं दिखता:

```java
System.out.println("Import underline formatting: " + loadOptions.isImportUnderlineFormatting());
```

## विज़ुअल ओवरव्यू

![कस्टम LoadOptions के साथ मार्कडाउन दस्तावेज़ लोड करने वाले जावा कोड का स्क्रीनशॉट](load-markdown.png)

*Alt text: कस्टम LoadOptions के साथ मार्कडाउन दस्तावेज़ लोड करने वाले जावा कोड का स्क्रीनशॉट.*

## निष्कर्ष

अब आप जानते हैं कि Java में **मार्कडाउन दस्तावेज़ लोड** कैसे करें जबकि अंडरलाइन स्टाइलिंग को संरक्षित रखें और `LoadOptions` के माध्यम से **कस्टम इम्पोर्ट व्यवहार** लागू करें। तीन‑चरणीय पैटर्न—`LoadOptions` बनाएं, वांछित फ़्लैग्स को सक्षम करें, और विकल्पों को `Document` कंस्ट्रक्टर में पास करें—अन्य कई इम्पोर्ट सेटिंग्स पर भी लागू होता है।

अब आप अतिरिक्त फ़्लैग्स जैसे `setImportTables` का अन्वेषण कर सकते हैं, लोड किए गए `Document` को PDF कनवर्टर के साथ जोड़ सकते हैं, या दस्तावेज़ को वेब व्यूअर में एम्बेड कर सकते हैं। यही तरीका SDK द्वारा समर्थित अन्य फ़ाइल प्रकारों के लिए भी काम करता है, जिससे यह पैटर्न आपके Java टूलकिट में एक बहुमुखी उपकरण बन जाता है।

--- 

*अगले कदम:*  

* सीखें कि **लोड किए गए Document को PDF** या HTML में कैसे एक्सपोर्ट करें।  
* `LoadOptions` प्रॉपर्टीज़ की पूरी सूची का अन्वेषण करें ताकि मार्कडाउन पार्सिंग को फाइन‑ट्यून किया जा सके।  
* प्रोडक्शन‑ग्रेड एप्लिकेशन के लिए एरर हैंडलिंग और लॉगिंग को इंटीग्रेट करें।

## अब आपको क्या सीखना चाहिए?

निम्नलिखित ट्यूटोरियल्स उन निकट संबंधित विषयों को कवर करते हैं जो इस गाइड में प्रदर्शित तकनीकों पर आधारित हैं। प्रत्येक संसाधन में पूर्ण कार्यशील कोड उदाहरण और चरण‑दर‑चरण व्याख्याएँ शामिल हैं, जो आपको अतिरिक्त API फीचर्स में महारत हासिल करने और अपने प्रोजेक्ट्स में वैकल्पिक इम्प्लीमेंटेशन अप्रोच को एक्सप्लोर करने में मदद करती हैं।

- [Java में मार्कडाउन अंडरलाइन लोड करना – पूर्ण प्रोग्रामिंग गाइड](/words/english/java/document-loading-and-saving/load-markdown-underline-in-java-complete-programming-guide/)
- [Java में मार्कडाउन कैसे लोड करें – पूर्ण गाइड](/words/english/java/document-loading-and-saving/how-to-load-markdown-in-java-complete-guide/)
- [Aspose.Words के साथ Java में मार्कडाउन फ़ाइल को पढ़ना और लोड करना](/words/english/java/document-loading-and-saving/how-to-read-markdown-file-java-with-aspose-words/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}