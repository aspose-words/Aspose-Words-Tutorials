---
category: general
date: 2026-11-22
description: जावा में फ़ॉर्मेटिंग के साथ मार्कडाउन लोड करना सीखें। यह गाइड आपको LoadOptions
  और Document का उपयोग करके फ़ॉर्मेटिंग के साथ मार्कडाउन पढ़ने का तरीका दिखाता है।
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to load markdown
- read markdown with formatting
- Java markdown parsing
- LoadOptions import underline
- Document processing Java
language: hi
lastmod: 2026-11-22
og_description: जावा में फ़ॉर्मेटिंग के साथ मार्कडाउन कैसे लोड करें। इस पूर्ण ट्यूटोरियल
  का पालन करें ताकि आप फ़ॉर्मेटिंग के साथ मार्कडाउन पढ़ सकें, अंडरलाइन स्टाइल को संरक्षित
  रखें, और डॉक्यूमेंट ऑब्जेक्ट्स के साथ काम कर सकें।
og_image_alt: Java code snippet showing markdown loading with formatting enabled
og_title: जावा में फ़ॉर्मेटिंग के साथ मार्कडाउन लोड करने का तरीका – चरण-दर-चरण गाइड
schemas:
- author: GroupDocs
  dateModified: '2026-11-22'
  description: Learn how to load markdown with formatting in Java. This guide shows
    you how to read markdown with formatting using LoadOptions and Document.
  headline: How to load markdown with formatting in Java
  type: TechArticle
tags:
- markdown
- java
- document-processing
title: जावा में फॉर्मेटिंग के साथ मार्कडाउन कैसे लोड करें
url: /hi/java/document-loading-and-saving/how-to-load-markdown-with-formatting-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Java में फ़ॉर्मेटिंग के साथ markdown लोड कैसे करें

यदि आपको **markdown लोड करने का तरीका** उसकी दृश्य शैली को बनाए रखते हुए चाहिए, तो यह ट्यूटोरियल आपको एक तैयार‑से‑चलाने योग्य समाधान देता है। आप बिल्कुल देखेंगे कि **फ़ॉर्मेटिंग के साथ markdown पढ़ना** कैसे किया जाता है, जैसे कि अंडरलाइन किया हुआ टेक्स्ट, ताकि रेंडर किया गया दस्तावेज़ मूल स्रोत से मेल खाए।

यह गाइड लोडर को कॉन्फ़िगर करने से लेकर यह सत्यापित करने तक के हर चरण को कवर करता है कि फ़ॉर्मेटिंग इम्पोर्ट के बाद बनी रही। मानक GroupDocs.Viewer लाइब्रेरी (या कोई भी संगत API जो `LoadOptions` और `Document` प्रदान करता है) के अलावा कोई बाहरी टूल आवश्यक नहीं है। अंत तक आप markdown लोडिंग को किसी भी Java बैकएंड, वेब सर्विस, या डेस्कटॉप ऐप में एकीकृत कर सकते हैं।

## आवश्यकताएँ

* Java 17 या उससे नया स्थापित हो।
* निर्भरता प्रबंधन के लिए Maven या Gradle।
* `LoadOptions` और `Document` शामिल करने वाले GroupDocs.Viewer (या समकक्ष) JAR तक पहुँच।
* `sample.md` नामक एक नमूना markdown फ़ाइल जिसमें अंडरलाइन मार्कअप हो (जैसे `<u>underlined text</u>` या `_underlined_` पार्सर के अनुसार)।

## चरण 1: आवश्यक निर्भरता जोड़ें

यदि आप Maven उपयोग करते हैं, तो अपने `pom.xml` में निम्न जोड़ें। संस्करण को नवीनतम स्थिर रिलीज़ के अनुसार समायोजित करें।

```xml
<dependency>
    <groupId>com.groupdocs</groupId>
    <artifactId>groupdocs-viewer</artifactId>
    <version>23.12</version>
</dependency>
```

Gradle उपयोगकर्ता इसे जोड़ सकते हैं:

```groovy
implementation 'com.groupdocs:groupdocs-viewer:23.12'
```

लाइब्रेरी को शामिल करने से `LoadOptions` और `Document` दोनों क्लासेस कंपाइल समय पर उपलब्ध हो जाते हैं।

## चरण 2: अंडरलाइन फ़ॉर्मेटिंग आयात करने के लिए LoadOptions कॉन्फ़िगर करें

`LoadOptions` ऑब्जेक्ट पार्सर को बताता है कि कौन-से markdown फ़ीचर को संरक्षित करना है। अंडरलाइन फ़ॉर्मेटिंग को सक्षम करने से यह सुनिश्चित होता है कि दृश्य शैली परिणामी `Document` में दिखाई दे।

```java
import com.groupdocs.viewer.options.LoadOptions;

/**
 * Creates a LoadOptions instance with underline import enabled.
 *
 * @return configured LoadOptions
 */
private static LoadOptions createLoadOptions() {
    LoadOptions loadOptions = new LoadOptions();
    // Preserve underline markup when the markdown is parsed.
    loadOptions.setImportUnderlineFormatting(true);
    return loadOptions;
}
```

**क्यों यह महत्वपूर्ण है:**  
`setImportUnderlineFormatting(true)` के बिना, पार्सर अंडरलाइन टैग हटाकर साधारण टेक्स्ट छोड़ देता है। फ़्लैग को सक्षम करने से शैली अपरिवर्तित रहती है, जो तब आवश्यक है जब डाउनस्ट्रीम कंज्यूमर (जैसे PDF जेनरेटर) दृश्य संकेतों पर निर्भर करता है।

## चरण 3: कॉन्फ़िगर किए गए विकल्पों का उपयोग करके markdown दस्तावेज़ लोड करें

अब आप markdown फ़ाइल पढ़ सकते हैं। `Document` कन्स्ट्रक्टर फ़ाइल पथ और आपने अभी तैयार किए `LoadOptions` को स्वीकार करता है।

```java
import com.groupdocs.viewer.Document;
import com.groupdocs.viewer.options.LoadOptions;

/**
 * Loads a markdown file while preserving formatting.
 *
 * @param markdownPath absolute or relative path to the .md file
 * @param options      LoadOptions with formatting flags
 * @return Document representing the parsed markdown
 */
private static Document loadMarkdown(String markdownPath, LoadOptions options) {
    return new Document(markdownPath, options);
}
```

**क्यों यह महत्वपूर्ण है:**  
`LoadOptions` को `Document` कन्स्ट्रक्टर में पास करने से यह सुनिश्चित होता है कि पार्सर पूरे इम्पोर्ट प्रक्रिया में अंडरलाइन फ़्लैग का सम्मान करे। परिणामी `Document` ऑब्जेक्ट को पूर्ण फ़ॉर्मेटिंग के साथ रेंडर, कन्वर्ट या निरीक्षण किया जा सकता है।

## चरण 4: सत्यापित करें कि अंडरलाइन फ़ॉर्मेटिंग बनी रही

अंडरलाइन मौजूद है या नहीं, यह पुष्टि करने का तेज़ तरीका है दस्तावेज़ को HTML में रेंडर करना और आउटपुट प्रिंट करना। यदि इम्पोर्ट सफल रहा तो HTML में `<u>` टैग मौजूद होंगे।

```java
import com.groupdocs.viewer.options.HtmlViewOptions;
import com.groupdocs.viewer.Viewer;

/**
 * Renders the loaded Document to HTML and prints the first page.
 *
 * @param doc Document loaded from markdown
 */
private static void renderAndPrint(Document doc) {
    // Create a Viewer instance for rendering.
    Viewer viewer = new Viewer(doc);
    // Render the first page as HTML.
    HtmlViewOptions viewOptions = HtmlViewOptions.forEmbeddedResources();
    viewer.view(viewOptions, 1);
    String html = viewOptions.getHtmlContent();

    System.out.println("Rendered HTML snippet:");
    System.out.println(html.substring(0, Math.min(html.length(), 500)));
}
```

पूरा प्रोग्राम चलाने पर एक HTML स्निपेट दिखना चाहिए जिसमें `<u>underlined text</u>` शामिल हो। यदि टैग गायब है, तो दोबारा जांचें कि फ़ाइल लोड करने से पहले `setImportUnderlineFormatting(true)` कॉल किया गया था।

## पूर्ण चलाने योग्य उदाहरण

सब कुछ मिलाकर, यहाँ एक स्व-निहित Java क्लास है जिसे आप कंपाइल और निष्पादित कर सकते हैं:

```java
import com.groupdocs.viewer.Document;
import com.groupdocs.viewer.Viewer;
import com.groupdocs.viewer.options.HtmlViewOptions;
import com.groupdocs.viewer.options.LoadOptions;

/**
 * Demonstrates how to load markdown with formatting in Java.
 * The program reads a markdown file, preserves underline markup,
 * renders the first page to HTML, and prints a snippet.
 */
public class MarkdownLoader {

    public static void main(String[] args) {
        // Path to the markdown file – adjust as needed.
        String markdownPath = "sample.md";

        // Step 1: create LoadOptions with underline support.
        LoadOptions options = createLoadOptions();

        // Step 2: load the markdown document.
        Document doc = loadMarkdown(markdownPath, options);

        // Step 3: render the document to HTML and verify formatting.
        renderAndPrint(doc);
    }

    private static LoadOptions createLoadOptions() {
        LoadOptions loadOptions = new LoadOptions();
        loadOptions.setImportUnderlineFormatting(true);
        return loadOptions;
    }

    private static Document loadMarkdown(String path, LoadOptions options) {
        return new Document(path, options);
    }

    private static void renderAndPrint(Document doc) {
        Viewer viewer = new Viewer(doc);
        HtmlViewOptions viewOptions = HtmlViewOptions.forEmbeddedResources();
        viewer.view(viewOptions, 1); // render first page
        String html = viewOptions.getHtmlContent();

        System.out.println("Rendered HTML snippet:");
        System.out.println(html.substring(0, Math.min(html.length(), 500)));
    }
}
```

**अपेक्षित आउटपुट (संक्षिप्त रूप में):**

```
Rendered HTML snippet:
<div class="page">
  <p>This is a <u>underlined text</u> example from the markdown file.</p>
  …
```

यदि `<u>` टैग दिखाई देता है, तो markdown फ़ॉर्मेटिंग के साथ लोड हुआ है।

## सामान्य विविधताएँ और किनारे के मामले

| स्थिति                                 | क्या बदलें                                                    |
|----------------------------------------|--------------------------------------------------------------|
| **विभिन्न markdown एक्सटेंशन**        | `loadOptions.setImportBoldFormatting(true)` का उपयोग **bold** के लिए करें। |
| **बड़ी फ़ाइलें (> 10 MB)**            | `FileInputStream` से फ़ाइल को स्ट्रीम करें और स्ट्रीम को `Document` को पास करें। |
| **PDF आउटपुट चाहिए**                 | लोड करने के बाद, `PdfViewOptions` को `Viewer` के साथ उपयोग करके एक PDF बनाएं जो अंडरलाइन स्टाइल को बनाए रखे। |
| **सर्वलेट कंटेनर में चलाना**           | `Document` को अनुरोध स्कोप में संग्रहीत करें और तुरंत HTML में रेंडर करें। |

**प्रो टिप:** प्रत्येक लोड ऑपरेशन के लिए हमेशा एक नया `LoadOptions` इंस्टेंस बनाएं। थ्रेड्स के बीच एक ही ऑब्जेक्ट को पुन: उपयोग करने से अप्रत्याशित स्टेट लीकेज हो सकता है।

## निष्कर्ष

अब आप **Java में फ़ॉर्मेटिंग के साथ markdown लोड करने का तरीका** और `LoadOptions` का उपयोग करके **फ़ॉर्मेटिंग के साथ markdown पढ़ने का तरीका** जानते हैं। पूर्ण उदाहरण कॉन्फ़िगरेशन, लोडिंग और सत्यापन दिखाता है, ताकि आप इस पैटर्न को किसी भी Java प्रोजेक्ट में एम्बेड कर सकें जो markdown फ़ाइलों को प्रोसेस करता है।

अगला, संबंधित विषयों का अन्वेषण करें जैसे **छवियों के साथ markdown पढ़ना**, **markdown को PDF में बदलना**, या **अन्य शैली आयातों को कस्टमाइज़ करना** (bold, italic, strikethrough)। इन सभी एक्सटेंशन में वही पैटर्न अपनाया जाता है: `LoadOptions` फ़्लैग्स को समायोजित करें, `Document` लोड करें, और इच्छित फ़ॉर्मेट में रेंडर करें।

कोडिंग का आनंद लें!

## अब आपको क्या सीखना चाहिए?

निम्नलिखित ट्यूटोरियल्स उन निकटतम संबंधित विषयों को कवर करते हैं जो इस गाइड में दिखाए गए तकनीकों पर आधारित हैं। प्रत्येक संसाधन में पूर्ण कार्यशील कोड उदाहरण और चरण-दर-चरण व्याख्याएँ शामिल हैं जो आपको अतिरिक्त API फीचर्स में निपुण बनने और अपने प्रोजेक्ट्स में वैकल्पिक कार्यान्वयन दृष्टिकोणों का अन्वेषण करने में मदद करती हैं।

- [Java में कस्टम इम्पोर्ट विकल्पों के साथ markdown दस्तावेज़ लोड करने का तरीका](/words/english/java/document-loading-and-saving/how-to-load-markdown-document-in-java-with-custom-import-opt/)
- [Aspose.Words के साथ Java में Markdown फ़ाइल पढ़ने और लोड करने का तरीका](/words/english/java/document-loading-and-saving/how-to-read-markdown-file-java-with-aspose-words/)
- [Java में Markdown लोड करने का तरीका – पूर्ण गाइड](/words/english/java/document-loading-and-saving/how-to-load-markdown-in-java-complete-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}