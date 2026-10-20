---
category: general
date: 2026-08-04
description: जावा में मार्कडाउन अंडरलाइन लोड करें और मार्कडाउन को दस्तावेज़ में लोड
  करते समय उसकी फ़ॉर्मेटिंग को संरक्षित रखें। इस चरण‑दर‑चरण ट्यूटोरियल का पालन करें।
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- load markdown underline
- load markdown into document
- preserve markdown formatting
language: hi
lastmod: 2026-08-04
og_description: जावा में मार्कडाउन अंडरलाइन लोड करें और मार्कडाउन फ़ॉर्मेटिंग को संरक्षित
  रखें। जानें कि कैसे मार्कडाउन को दस्तावेज़ में पूर्ण अंडरलाइन समर्थन के साथ लोड
  किया जाए।
og_image_alt: Diagram showing load markdown underline process
og_title: Java में markdown अंडरलाइन लोड करें – चरण‑दर‑चरण गाइड
schemas:
- author: GroupDocs
  dateModified: '2026-08-04'
  description: Load markdown underline in Java and preserve markdown formatting while
    loading markdown into document. Follow this step‑by‑step tutorial.
  headline: Load markdown underline in Java – complete programming guide
  type: TechArticle
- description: Load markdown underline in Java and preserve markdown formatting while
    loading markdown into document. Follow this step‑by‑step tutorial.
  name: Load markdown underline in Java – complete programming guide
  steps:
  - name: Create `LoadOptions` for the document
    text: '`LoadOptions` lets you customize how the library parses the source file.
      Creating a fresh instance gives you a clean slate for later settings.'
  - name: Enable detection of underline formatting while loading
    text: By default the viewer may ignore underline tags because they are less common
      in Markdown. Enabling this flag tells the parser to keep underline spans intact.
  - name: Load the Markdown file using the configured options
    text: Now you can load the file. Pass the `loadOptions` object to the `Document`
      constructor so the parser respects the underline flag.
  - name: Verify that underline formatting is preserved
    text: A quick sanity check helps you confirm that **preserve markdown formatting**
      worked. The following snippet prints the text of each paragraph and marks underlined
      fragments with a tilde (`~`) for visibility.
  type: HowTo
tags:
- markdown
- Java
- document-processing
title: जावा में मार्कडाउन अंडरलाइन लोड करें – पूर्ण प्रोग्रामिंग गाइड
url: /hi/java/document-loading-and-saving/load-markdown-underline-in-java-complete-programming-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# जावा में मार्कडाउन अंडरलाइन लोड करें – पूर्ण प्रोग्रामिंग गाइड

यदि आपको मार्कडाउन फ़ाइल को `Document` ऑब्जेक्ट में परिवर्तित करते समय **load markdown underline** करने की आवश्यकता है, तो यह गाइड आपको बिल्कुल बताता है कि इसे कैसे करें। आप यह भी सीखेंगे कि **load markdown into document** कैसे करें बिना किसी अंडरलाइन स्टाइलिंग को खोए, जिससे मूल मार्कडाउन फ़ॉर्मेटिंग पूरी तरह संरक्षित रहे।

यह ट्यूटोरियल वह सब कवर करता है जो आपको जानना आवश्यक है: आवश्यक लाइब्रेरीज़, प्रत्येक कॉन्फ़िगरेशन स्टेप, और यह कैसे सत्यापित करें कि अंडरलाइन फ़ॉर्मेटिंग इम्पोर्ट के बाद भी बनी रही। अंत तक आपके पास एक पुन: उपयोग योग्य कोड स्निपेट होगा जिसे आप किसी भी जावा प्रोजेक्ट में डाल सकते हैं।

## पूर्वापेक्षाएँ

शुरू करने से पहले सुनिश्चित करें कि आपके पास है:

- Java 17 या बाद का संस्करण स्थापित हो (उदाहरण आधुनिक मॉड्यूल सिस्टम का उपयोग करता है)
- **GroupDocs.Viewer** का नवीनतम संस्करण (या कोई संगत लाइब्रेरी जो `LoadOptions` और `Document` प्रदान करती है)
- एक मार्कडाउन फ़ाइल (`sample.md`) जिसमें अंडरलाइन किया गया टेक्स्ट हो, उदाहरण के लिए `<u>underlined</u>` या GitHub‑flavored सिंटैक्स `__underlined__`
- IntelliJ IDEA या VS Code जैसे IDE, हालांकि कोई भी टेक्स्ट एडिटर काम करेगा

इन आवश्यकताओं से यह सुनिश्चित होता है कि कोड अतिरिक्त कॉन्फ़िगरेशन के बिना चल सके।

## Load markdown underline – चरण‑दर‑चरण गाइड

यह प्रक्रिया तीन मुख्य कार्यों में विभाजित है: `LoadOptions` इंस्टेंस बनाना, अंडरलाइन डिटेक्शन सक्षम करना, और अंत में उन विकल्पों के साथ मार्कडाउन फ़ाइल लोड करना। प्रत्येक चरण नीचे समझाया गया है।

### चरण 1: दस्तावेज़ के लिए `LoadOptions` बनाएं

`LoadOptions` आपको लाइब्रेरी को स्रोत फ़ाइल कैसे पार्स करनी है, इसे कस्टमाइज़ करने की अनुमति देता है। एक नई इंस्टेंस बनाकर आप बाद के सेटिंग्स के लिए एक साफ़ आधार प्राप्त करते हैं।

```java
import com.groupdocs.viewer.options.LoadOptions;

// Step 1: Create load options for the document
LoadOptions loadOptions = new LoadOptions();
```

`LoadOptions` ऑब्जेक्ट सभी इम्पोर्ट‑संबंधी ट्यूनिंग का एंट्री पॉइंट है। आप इसे अगले चरण में अंडरलाइन डिटेक्शन चालू करने के लिए उपयोग करेंगे।

### चरण 2: लोड करते समय अंडरलाइन फ़ॉर्मेटिंग का डिटेक्शन सक्षम करें

डिफ़ॉल्ट रूप से व्यूअर अंडरलाइन टैग्स को अनदेखा कर सकता है क्योंकि वे मार्कडाउन में कम सामान्य होते हैं। इस फ़्लैग को सक्षम करने से पार्सर अंडरलाइन स्पैन को बरकरार रखता है।

```java
// Step 2: Enable detection of underline formatting while loading
loadOptions.setImportUnderlineFormatting(true);
```

`setImportUnderlineFormatting(true)` सेट करने से कोई भी `<u>` HTML टैग या GitHub‑flavored अंडरलाइन सिंटैक्स `Document` मॉडल में अंडरलाइन स्टाइल के रूप में अनुवादित हो जाता है। यही मुख्य कार्रवाई है जो **load markdown underline** को अपेक्षित रूप से काम करने देती है।

### चरण 3: कॉन्फ़िगर किए गए विकल्पों के साथ मार्कडाउन फ़ाइल लोड करें

अब आप फ़ाइल लोड कर सकते हैं। `loadOptions` ऑब्जेक्ट को `Document` कंस्ट्रक्टर में पास करें ताकि पार्सर अंडरलाइन फ़्लैग का सम्मान करे।

```java
import com.groupdocs.viewer.Document;

// Step 3: Load the Markdown file using the configured options
Document markdownDoc = new Document("YOUR_DIRECTORY/sample.md", loadOptions);
```

जब कंस्ट्रक्टर समाप्त होता है, `markdownDoc` में मार्कडाउन स्रोत की पूरी इन‑मेमोरी प्रतिनिधित्व होती है, जिसमें अंडरलाइन रन भी शामिल होते हैं।

### चरण 4: सत्यापित करें कि अंडरलाइन फ़ॉर्मेटिंग बनी हुई है

एक त्वरित sanity check आपको यह पुष्टि करने में मदद करता है कि **preserve markdown formatting** काम किया। नीचे दिया गया स्निपेट प्रत्येक पैराग्राफ का टेक्स्ट प्रिंट करता है और दृश्यता के लिए अंडरलाइन भागों को टिल्डे (`~`) से चिह्नित करता है।

```java
import com.groupdocs.viewer.contents.Page;
import com.groupdocs.viewer.contents.Paragraph;
import com.groupdocs.viewer.contents.TextFragment;

for (Page page : markdownDoc.getPages()) {
    for (Paragraph paragraph : page.getParagraphs()) {
        StringBuilder line = new StringBuilder();
        for (TextFragment fragment : paragraph.getTextFragments()) {
            if (fragment.isUnderline()) {
                line.append("~").append(fragment.getText()).append("~");
            } else {
                line.append(fragment.getText());
            }
        }
        System.out.println(line.toString());
    }
}
```

**अपेक्षित आउटपुट** (मान लेते हैं `sample.md` में `This is __underlined__ text` है):

```
This is ~underlined~ text
```

टिल्डे यह दर्शाते हैं कि अंडरलाइन स्टाइल इम्पोर्ट के बाद भी जीवित रहा, जिससे यह पुष्टि होती है कि **load markdown into document** ऑपरेशन ने मूल फ़ॉर्मेटिंग को संरक्षित किया।

## सामान्य समस्याएँ और उनका समाधान

| लक्षण | कारण | समाधान |
|---|---|---|
| लोड करने के बाद अंडरलाइन गायब हो जाता है | `setImportUnderlineFormatting` डिफ़ॉल्ट `false` पर रह गया | `Document` बनाने से पहले `loadOptions.setImportUnderlineFormatting(true)` कॉल करना सुनिश्चित करें। |
| टेक्स्ट का केवल कुछ हिस्सा अंडरलाइन है | मिश्रित मार्कडाउन सिंटैक्स (जैसे HTML `<u>` को `__underline__` के साथ मिलाना) | लाइब्रेरी दोनों को सपोर्ट करती है; सुनिश्चित करें कि स्रोत फ़ाइल में एकसमान अंडरलाइन मार्कर उपयोग हो। |
| दस्तावेज़ लोड नहीं हो रहा | गलत फ़ाइल पाथ या लाइब्रेरी डिपेंडेंसीज़ गायब | पूर्ण पाथ उपयोग करें या `sample.md` को कार्य निर्देशिका के सापेक्ष रखें; व्यूअर JARs को क्लासपाथ में शामिल करें। |

**Pro tip:** यदि आपको बोल्ड या इटैलिक स्टाइल भी रखना है, तो क्रमशः `setImportBoldFormatting(true)` और `setImportItalicFormatting(true)` सक्षम करें। इन फ़्लैग्स को मिलाकर आप अधिकांश सामान्य मार्कडाउन स्टाइल्स का पूर्णतः सटीक इम्पोर्ट प्राप्त कर सकते हैं।

## पूर्ण चलाने योग्य उदाहरण

नीचे एक स्व-निहित जावा प्रोग्राम है जो सब कुछ एक साथ जोड़ता है। कोड को `LoadMarkdownUnderlineDemo.java` नामक फ़ाइल में कॉपी करें, फ़ाइल पाथ समायोजित करें, और `java LoadMarkdownUnderlineDemo` के साथ चलाएँ।

```java
import com.groupdocs.viewer.Document;
import com.groupdocs.viewer.contents.Page;
import com.groupdocs.viewer.contents.Paragraph;
import com.groupdocs.viewer.contents.TextFragment;
import com.groupdocs.viewer.options.LoadOptions;

public class LoadMarkdownUnderlineDemo {

    public static void main(String[] args) {
        // 1️⃣ Create load options
        LoadOptions loadOptions = new LoadOptions();

        // 2️⃣ Enable underline detection
        loadOptions.setImportUnderlineFormatting(true);

        // 3️⃣ Load the Markdown file
        Document markdownDoc = new Document("YOUR_DIRECTORY/sample.md", loadOptions);

        // 4️⃣ Print each paragraph, marking underlined text with ~
        for (Page page : markdownDoc.getPages()) {
            for (Paragraph paragraph : page.getParagraphs()) {
                StringBuilder line = new StringBuilder();
                for (TextFragment fragment : paragraph.getTextFragments()) {
                    if (fragment.isUnderline()) {
                        line.append("~").append(fragment.getText()).append("~");
                    } else {
                        line.append(fragment.getText());
                    }
                }
                System.out.println(line.toString());
            }
        }
    }
}
```

प्रोग्राम चलाने पर दस्तावेज़ की सामग्री अंडरलाइन मार्कर के साथ प्रिंट होगी, जिससे यह सिद्ध होता है कि **load markdown underline** फीचर काम करता है और आप **preserve markdown formatting** को इम्पोर्ट पाइपलाइन के दौरान बनाए रख सकते हैं।

## निष्कर्ष

अब आप जानते हैं कि जावा में **load markdown underline** कैसे किया जाता है, **load markdown into document** करते समय मूल स्टाइलिंग को कैसे बरकरार रखा जाता है, और अंडरलाइन फ़ॉर्मेटिंग के intact रहने की पुष्टि कैसे की जाती है। यह तरीका नवीनतम GroupDocs.Viewer रिलीज़ के साथ काम करता है और इसे बोल्ड, इटैलिक और टेबल्स जैसे अतिरिक्त मार्कडाउन फीचर्स को सपोर्ट करने के लिए विस्तारित किया जा सकता है।

अगला, संबंधित विषयों का अन्वेषण करें जैसे **preserve markdown formatting for tables**, **render Markdown to PDF**, या **custom styling of imported Markdown elements**। अपने एप्लिकेशन की सटीक फ़ॉर्मेटिंग आवश्यकताओं के अनुसार `LoadOptions` फ़्लैग्स को समायोजित करें, और आपके पास प्रत्येक इम्पोर्ट चरण पर सूक्ष्म नियंत्रण होगा। Happy coding!

## आपको आगे क्या सीखना चाहिए?

निम्नलिखित ट्यूटोरियल्स उन विषयों को कवर करते हैं जो इस गाइड में प्रदर्शित तकनीकों पर आधारित हैं। प्रत्येक संसाधन में पूर्ण कार्यशील कोड उदाहरण और चरण‑दर‑चरण व्याख्याएँ शामिल हैं, जो आपको अतिरिक्त API फीचर्स में महारत हासिल करने और अपने प्रोजेक्ट्स में वैकल्पिक इम्प्लीमेंटेशन अप्रोचेज़ को एक्सप्लोर करने में मदद करेंगे।

- [Aspose.Words for Java के साथ Markdown लोड विकल्पों में महारत हासिल करें](/words/english/java/document-operations/master-markdown-load-options-aspose-words-java/)
- [Aspose Words Java के साथ Markdown लोड विकल्पों में महारत](/words/german/java/document-operations/master-markdown-load-options-aspose-words-java/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}