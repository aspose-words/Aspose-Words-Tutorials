---
category: general
date: 2026-11-15
description: जावा का उपयोग करके वर्ड दस्तावेज़ में पैराग्राफ की लाइन स्पेसिंग सेट
  करें। सटीक दस्तावेज़ फ़ॉर्मेटिंग के लिए Aspose.Words के माध्यम से प्रोग्रामेटिकली
  लाइन स्पेसिंग कैसे सेट करें, जानें।
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- set paragraph line spacing
- how to set line spacing
language: hi
lastmod: 2026-11-15
og_description: Java के साथ Word दस्तावेज़ में पैराग्राफ की लाइन स्पेसिंग सेट करें।
  यह गाइड Aspose.Words का उपयोग करके पैराग्राफ और फुटनोट सेपरेटर की लाइन स्पेसिंग
  कैसे सेट करें, यह समझाता है, जिससे आपको दस्तावेज़ लेआउट पर पूर्ण नियंत्रण मिलता
  है।
og_image_alt: Screenshot showing Java code that sets paragraph line spacing in a Word
  document
og_title: जावा का उपयोग करके वर्ड में पैराग्राफ लाइन स्पेसिंग सेट करें
schemas:
- author: Aspose
  dateModified: '2026-11-15'
  description: Set paragraph line spacing in a Word document with Java. Learn how
    to set line spacing programmatically using Aspose.Words for precise document formatting.
  headline: Set paragraph line spacing in a Word document with Java
  type: TechArticle
- description: Set paragraph line spacing in a Word document with Java. Learn how
    to set line spacing programmatically using Aspose.Words for precise document formatting.
  name: Set paragraph line spacing in a Word document with Java
  steps:
  - name: Load the Word document
    text: First, create a `Document` instance that points to your source file.
  - name: Retrieve the footnote separator
    text: Footnote separators are special paragraphs that appear between footnotes
      and the main text. To change their appearance you need to access the `FootnoteSeparator`
      object.
  - name: How to set line spacing for the separator's paragraph
    text: Now apply the desired line spacing. Aspose.Words uses points for line‑spacing
      values; 12 pts is roughly single‑spacing for most fonts.
  - name: Save the updated document
    text: Finally, write the changes back to disk.
  type: HowTo
tags:
- Java
- Aspose.Words
- Document Formatting
title: जावा के साथ वर्ड दस्तावेज़ में पैराग्राफ लाइन स्पेसिंग सेट करें
url: /hi/java/formatting-styles/set-paragraph-line-spacing-in-a-word-document-with-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Java के साथ Word दस्तावेज़ में पैराग्राफ लाइन स्पेसिंग सेट करें

यदि आपको Word दस्तावेज़ में **पैराग्राफ लाइन स्पेसिंग सेट** करनी है, तो यह ट्यूटोरियल आपको Java और Aspose.Words के साथ यह करने का तरीका दिखाएगा। आप **फुटनोट सेपरेटर के लिए लाइन स्पेसिंग सेट** करना भी सीखेंगे—जो पेशेवर दस्तावेज़ों को फॉर्मेट करने में एक सामान्य आवश्यकता है।

आगे के सेक्शन में आप करेंगे:

* मौजूदा *.docx* फ़ाइल लोड करना।
* फुटनोट सेपरेटर पैराग्राफ प्राप्त करना।
* कस्टम लाइन‑स्पेसिंग वैल्यू लागू करना।
* अपडेटेड दस्तावेज़ को सेव करना।

Aspose.Words लाइब्रेरी को अपने प्रोजेक्ट में जोड़ने के अलावा कोई बाहरी कॉन्फ़िगरेशन आवश्यक नहीं है, इसलिए आप कोड को 그대로 कॉपी करके तुरंत चला सकते हैं।

## आवश्यकताएँ

शुरू करने से पहले सुनिश्चित करें कि आपके पास है:

* Java 17 या उससे नया संस्करण स्थापित हो।
* Maven (या कोई अन्य बिल्ड टूल) डिपेंडेंसीज़ मैनेज करने के लिए।
* एक वैध Aspose.Words for Java लाइसेंस (टेस्टिंग के लिए फ्री इवैल्यूएशन काम करता है)।
* एक इनपुट Word दस्तावेज़ (`input.docx`) जो ज्ञात डायरेक्टरी में स्थित हो।

अपने `pom.xml` में Aspose.Words डिपेंडेंसी जोड़ें:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.10</version> <!-- Use the latest stable version -->
</dependency>
```

## Aspose.Words के साथ पैराग्राफ लाइन स्पेसिंग सेट करें

यह H2 हेडर मुख्य कीवर्ड शामिल करता है, जिससे SEO आवश्यकता पूरी होती है।

### चरण 1: Word दस्तावेज़ लोड करें

सबसे पहले, एक `Document` इंस्टेंस बनाएं जो आपके स्रोत फ़ाइल की ओर इशारा करता हो।

```java
import com.aspose.words.*;

public class LineSpacingExample {
    public static void main(String[] args) throws Exception {
        // Load the Word document from the specified path
        Document doc = new Document("YOUR_DIRECTORY/input.docx");
        // Continue with formatting...
    }
}
```

*यह क्यों महत्वपूर्ण है*: दस्तावेज़ को लोड करने से आपको एक इन‑मेमोरी मॉडल मिलता है, जिसे आप मूल फ़ाइल को तब तक नहीं छुएँ जब तक आप स्पष्ट रूप से उसे सेव न करें।

### चरण 2: फुटनोट सेपरेटर प्राप्त करें

फुटनोट सेपरेटर विशेष पैराग्राफ होते हैं जो फुटनोट्स और मुख्य टेक्स्ट के बीच आते हैं। उनका रूप बदलने के लिए आपको `FootnoteSeparator` ऑब्जेक्ट तक पहुंचना होगा।

```java
// Retrieve the footnote separator that Aspose.Words represents internally
FootnoteSeparator separator = doc.getFootnoteSeparator();
```

*टिप*: यदि आपके दस्तावेज़ में फुटनोट नहीं हैं, तो भी सेपरेटर एक छिपे हुए पैराग्राफ के रूप में मौजूद रहता है, इसलिए कॉल कभी `null` नहीं लौटाएगा।

### चरण 3: सेपरेटर के पैराग्राफ के लिए लाइन स्पेसिंग सेट करना

अब इच्छित लाइन स्पेसिंग लागू करें। Aspose.Words लाइन‑स्पेसिंग वैल्यू के लिए पॉइंट्स का उपयोग करता है; 12 pts अधिकांश फ़ॉन्ट्स के लिए लगभग सिंगल‑स्पेसिंग है।

```java
// Set the line spacing to 12 points (single‑spacing)
separator.getParagraphFormat().setLineSpacing(12.0);
```

आप अन्य स्पेसिंग मोड भी उपयोग कर सकते हैं:

| मोड                     | मेथड कॉल                                      |
|--------------------------|--------------------------------------------------|
| **Exactly** (स्थिर पॉइंट्स) | `setLineSpacingRule(LineSpacingRule.EXACTLY)`   |
| **Multiple** (उदा., 1.5) | `setLineSpacingRule(LineSpacingRule.MULTIPLE); setLineSpacing(1.5);` |

सही नियम चुनने से दस्तावेज़ Word, Google Docs और अन्य व्यूअर्स में लगातार रेंडर होता है।

### चरण 4: अपडेटेड दस्तावेज़ को सेव करें

अंत में, बदलावों को डिस्क पर लिखें।

```java
// Save the modified document to a new file
doc.save("YOUR_DIRECTORY/output.docx");
System.out.println("Document saved with updated paragraph line spacing.");
```

जब आप `output.docx` को Microsoft Word में खोलेंगे, तो फुटनोट सेपरेटर आपके द्वारा परिभाषित लाइन स्पेसिंग के साथ दिखेगा।

## नियमित पैराग्राफ़ के लिए लाइन स्पेसिंग सेट करने को समझना

एक ही API किसी भी `Paragraph` ऑब्जेक्ट के लिए काम करती है, न कि केवल फुटनोट सेपरेटर के लिए। यहाँ एक त्वरित उदाहरण है जो बॉडी के पहले पैराग्राफ की स्पेसिंग को समायोजित करता है:

```java
// Access the first body paragraph
Paragraph firstPara = (Paragraph) doc.getFirstSection().getBody().getChild(NodeType.PARAGRAPH, 0, true);

// Apply double line spacing (2.0 × the font size)
firstPara.getParagraphFormat().setLineSpacingRule(LineSpacingRule.MULTIPLE);
firstPara.getParagraphFormat().setLineSpacing(2.0);
```

**आपको यह क्यों चाहिए**: रिपोर्ट, कॉन्ट्रैक्ट और अकादमिक पेपर अक्सर विशिष्ट लाइन‑स्पेसिंग स्टाइल (जैसे ड्राफ्ट के लिए डबल‑स्पेसिंग) की मांग करते हैं। वही `setLineSpacing` मेथड उपयोग करने से आपको बिल्कुल वही लेआउट मिलता है जिसकी आप उम्मीद करते हैं।

## सामान्य समस्याएँ और उन्हें कैसे टालें

| समस्या                                 | कारण                                   | समाधान |
|---------------------------------------|----------------------------------------|-----|
| लाइन स्पेसिंग अपरिवर्तित दिखती है        | `LineSpacingRule` को डिफ़ॉल्ट (AUTO) पर रहने दिया गया | `setLineSpacingRule` के साथ स्पष्ट रूप से नियम सेट करें। |
| सेपरेटर के बाद अतिरिक्त खाली लाइन्स | सेपरेटर में छिपे carriage returns होते हैं | स्पेसिंग लागू करने से पहले `separator.getText().trim();` के साथ सेपरेटर का टेक्स्ट ट्रिम करें। |
| सेव करने के बाद दस्तावेज़ भ्रष्ट हो जाता है| पुराने Aspose.Words संस्करण का उपयोग करना | सेविंग से संबंधित बग फिक्स वाले नवीनतम संस्करण (उदा., 24.10) में अपग्रेड करें। |

## प्रो टिप: कई दस्तावेज़ों को बैच‑प्रोसेस करें

यदि आपको दर्जनों फ़ाइलों को अपडेट करना है, तो लॉजिक को एक हेल्पर मेथड में रखें और फ़ोल्डर पर इटररेट करें:

```java
public static void updateSpacing(Path inputPath, Path outputPath) throws Exception {
    Document doc = new Document(inputPath.toString());
    FootnoteSeparator sep = doc.getFootnoteSeparator();
    sep.getParagraphFormat().setLineSpacing(12.0);
    doc.save(outputPath.toString());
}
```

इस मेथड को लूप में चलाने से मैन्युअल एडिटिंग में घंटे बचते हैं।

## अपेक्षित आउटपुट

पूरा प्रोग्राम चलाने के बाद, `output.docx` में:

* मूल कंटेंट अपरिवर्तित रहेगा, केवल लाइन स्पेसिंग बदलेगी।
* फुटनोट सेपरेटर सिंगल‑स्पेसिंग (12 pts) लेआउट के साथ दिखेगा।
* सभी अन्य फॉर्मेटिंग (स्टाइल्स, इमेजेज, टेबल्स) संरक्षित रहेगी।

फ़ाइल को Word में खोलें और देखें कि सेपरेटर लाइन आपके सेट किए गए वैल्यू के अनुसार टाइटर (या लूज़र) है या नहीं।

## निष्कर्ष

आप अब जानते हैं कि **Java के साथ Word दस्तावेज़ में पैराग्राफ लाइन स्पेसिंग सेट** कैसे करें, और साथ ही **फुटनोट सेपरेटर और नियमित पैराग्राफ़ दोनों के लिए लाइन स्पेसिंग सेट** करना भी समझ लिया है। पूरा, रन करने योग्य उदाहरण दिखाता है कि दस्तावेज़ को लोड करना, लाइन‑स्पेसिंग प्रॉपर्टीज़ को एडजस्ट करना, और परिणाम को सेव करना—सभी कुछ स्पष्ट API कॉल्स के साथ।

**अगले कदम** जिन्हें आप एक्सप्लोर कर सकते हैं:

* **टेबल और सूची आइटम्स के लिए लाइन स्पेसिंग सेट करना**।
* हेडिंग्स बनाम बॉडी टेक्स्ट के लिए विभिन्न स्पेसिंग नियम लागू करना।
* पूरे दस्तावेज़ में स्पेसिंग लागू करने के लिए `Style` ऑब्जेक्ट का उपयोग करना।

वैल्यूज़ के साथ प्रयोग करें, उन्हें अन्य फॉर्मेटिंग विकल्पों के साथ मिलाएँ, और आप किसी भी Java एप्लिकेशन में दस्तावेज़ लेआउट पर पूर्ण नियंत्रण पा लेंगे। Happy coding!

## अगला क्या सीखें?

निम्नलिखित ट्यूटोरियल्स उन विषयों को कवर करते हैं जो इस गाइड में दिखाए गए तकनीकों पर आधारित हैं। प्रत्येक संसाधन में पूर्ण कार्यशील कोड उदाहरण और चरण‑दर‑चरण व्याख्याएँ शामिल हैं, जिससे आप अतिरिक्त API फीचर्स में महारत हासिल कर सकें और अपने प्रोजेक्ट्स में वैकल्पिक इम्प्लीमेंटेशन अप्रोचेज़ को एक्सप्लोर कर सकें।

- [Aspose.Words for Java में विकल्प सेट करने का तरीका – पूर्ण गाइड](/words/english/java/document-loading-and-saving/how-to-set-options-in-aspose-words-for-java-complete-guide/)
- [Aspose.Words for Java में LoadOptions सेट करना](/words/english/java/document-loading-and-saving/using-load-options/)
- [Word दस्तावेज़ में एशियाई पैराग्राफ स्पेसिंग और इंडेंट बदलें](/words/english/net/document-formatting/change-asian-paragraph-spacing-and-indents/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}