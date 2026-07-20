---
category: general
date: 2026-07-20
description: DOCX फ़ाइलों में फुटनोट स्पेसिंग को आसानी से बदलें। सीखें कैसे स्पेसिंग
  सेट करें, फुटनोट सेपरेटर को समायोजित करें, और जावा के साथ पैराग्राफ की लाइन स्पेसिंग
  सेट करें।
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- change footnote spacing
- how to set spacing
- adjust footnote separator
- set paragraph line spacing
- change line spacing docx
language: hi
lastmod: 2026-07-20
og_description: DOCX फ़ाइलों में फुटनोट स्पेसिंग को जल्दी बदलें। यह गाइड दिखाता है
  कि कैसे स्पेसिंग सेट करें, फुटनोट सेपरेटर को समायोजित करें, और जावा में पैराग्राफ
  लाइन स्पेसिंग को कस्टमाइज़ करें।
og_image_alt: Screenshot showing Java code that changes footnote spacing in a DOCX
  document
og_title: DOCX में फुटनोट स्पेसिंग बदलें – चरण-दर-चरण मार्गदर्शिका
schemas:
- author: Aspose
  dateModified: '2026-07-20'
  description: Change footnote spacing in DOCX files easily. Learn how to set spacing,
    adjust footnote separator, and set paragraph line spacing with Java.
  headline: Change footnote spacing in DOCX – Complete Guide
  type: TechArticle
tags:
- footnote
- docx
- java
- spacing
title: DOCX में फुटनोट स्पेसिंग बदलें – पूर्ण गाइड
url: /hi/java/document-styling/change-footnote-spacing-in-docx-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# DOCX में फुटनोट स्पेसिंग बदलें – पूर्ण गाइड

क्या आपको कभी Word दस्तावेज़ में **फुटनोट स्पेसिंग बदलने** की ज़रूरत पड़ी है लेकिन शुरू करने के बारे में अनिश्चित रहे हैं? आप अकेले नहीं हैं। चाहे आप थीसिस को परिपूर्ण कर रहे हों या अनुबंध में थोड़ा बदलाव कर रहे हों, फुटनोट सेपरेटर को सही ढंग से सेट करना बड़ा अंतर ला सकता है।  

इस ट्यूटोरियल में हम **स्पेसिंग सेट करने** का तरीका, फुटनोट सेपरेटर को समायोजित करना, और **पैराग्राफ लाइन स्पेसिंग सेट** करने को Java‑आधारित लाइब्रेरीज़ का उपयोग करके समझेंगे। अंत तक आपके पास एक तैयार‑चलाने योग्य उदाहरण होगा जिसे आप किसी भी प्रोजेक्ट में जोड़ सकते हैं।

## आपको क्या चाहिए

- Java 17 या नया (कोड आधुनिक भाषा सुविधाओं का उपयोग करता है)
- निर्भरता प्रबंधन के लिए Maven या Gradle
- कम से कम एक फुटनोट वाला DOCX फ़ाइल (या आप इसे मैन्युअली बना सकते हैं)
- **Aspose.Words for Java** लाइब्रेरी (या कोई भी संगत API; हम उदाहरण में Aspose का उपयोग करेंगे)

बस इतना ही—कोई भारी फ्रेमवर्क नहीं, सिर्फ साधारण Java और एक लाइब्रेरी।

![DOCX में फुटनोट स्पेसिंग बदलने का उदाहरण](/images/footnote-spacing.png){alt="DOCX में फुटनोट स्पेसिंग बदलने का उदाहरण"}

## चरण 1: DOCX दस्तावेज़ लोड करें (फुटनोट स्पेसिंग बदलें)

सबसे पहले आपको Word फ़ाइल खोलनी होगी। इससे आपको एक `Document` ऑब्जेक्ट मिलता है जिसे आप संशोधित कर सकते हैं।

```java
import com.aspose.words.*;

public class FootnoteSpacingDemo {
    public static void main(String[] args) throws Exception {
        // Load the DOCX file – change the path to your own file
        Document doc = new Document("input.docx");
        
        // Continue with spacing adjustments...
        adjustFootnoteSeparator(doc);
        
        // Save the updated document
        doc.save("output.docx");
    }
}
```

*क्यों यह महत्वपूर्ण है*: दस्तावेज़ लोड करना **फुटनोट स्पेसिंग बदलने** का प्रवेश बिंदु है। `Document` इंस्टेंस के बिना आप फुटनोट सेपरेटर या किसी पैराग्राफ फ़ॉर्मेट तक नहीं पहुँच सकते।

## चरण 2: फुटनोट सेपरेटर प्राप्त करें और समायोजित करें (फुटनोट सेपरेटर समायोजित करें)

फुटनोट सेपरेटर एक छिपा हुआ पैराग्राफ है जो मुख्य टेक्स्ट और फुटनोट सूची के बीच स्थित होता है। इसकी लाइन स्पेसिंग बदलने के लिए आपको उस पैराग्राफ को प्राप्त करके उसके फ़ॉर्मेट को समायोजित करना होगा।

```java
private static void adjustFootnoteSeparator(Document doc) throws Exception {
    // Get the footnote separator (the first one is usually the default separator)
    FootnoteSeparator separator = doc.getFootnoteSeparator();
    
    // If the document has no separator (rare), create one
    if (separator == null) {
        separator = new FootnoteSeparator(doc);
        doc.getFootnotes().add(separator);
    }
    
    // Access the underlying paragraph and set line spacing
    Paragraph sepParagraph = separator.getSeparatorParagraph();
    ParagraphFormat fmt = sepParagraph.getParagraphFormat();
    
    // Set line spacing to 12 points – this is the core of "change footnote spacing"
    fmt.setLineSpacing(12.0);
    
    // Optional: also adjust spacing before/after if needed
    fmt.setSpaceBefore(0);
    fmt.setSpaceAfter(0);
}
```

### यह समस्या कैसे हल करता है

- **फुटनोट सेपरेटर प्राप्त करें** – यह वह भाग है जिसे आप वास्तव में संशोधित करना चाहते हैं, जिससे *फुटनोट सेपरेटर समायोजित करें* की आवश्यकता पूरी होती है।
- **लाइन स्पेसिंग सेट करें** – `setLineSpacing(12.0)` सीधे *स्पेसिंग कैसे सेट करें* का उत्तर देता है उस छिपे हुए पैराग्राफ के लिए।
- **एज केस हैंडलिंग** – यदि दस्तावेज़ में किसी कारण से सेपरेटर नहीं है, तो हम उसे तुरंत बनाते हैं, जिससे `NullPointerException` से बचा जा सके।

## चरण 3: परिवर्तन सत्यापित करें और सहेजें (पैराग्राफ लाइन स्पेसिंग सेट करें)

सेपरेटर को बदलने के बाद, आपको यह सुनिश्चित करना होगा कि परिवर्तन सहेजा गया है। सहेजी गई फ़ाइल को Word में खोलने पर नई स्पेसिंग दिखेगी, लेकिन आप इसे प्रोग्रामेटिक रूप से भी जांच सकते हैं।

```java
private static void verifySpacing(Document doc) throws Exception {
    FootnoteSeparator sep = doc.getFootnoteSeparator();
    double spacing = sep.getSeparatorParagraph().getParagraphFormat().getLineSpacing();
    System.out.println("Current footnote separator line spacing: " + spacing);
}
```

`main` में `doc.save(...)` से ठीक पहले `verifySpacing(doc);` कॉल जोड़ें। जब आप प्रोग्राम चलाएँगे तो आपको यह दिखना चाहिए:

```
Current footnote separator line spacing: 12.0
```

यह पुष्टि करता है कि **लाइन स्पेसिंग बदलें docx** ऑपरेशन सफल रहा।

## सामान्य गलतियाँ और प्रो टिप्स

- **गलती**: `setLineSpacing` को ऐसे मान के साथ उपयोग करना जो “12” जैसा दिखता है लेकिन “12 pts” बनाम “12 lines” के रूप में व्याख्यायित होता है। Aspose पॉइंट्स की अपेक्षा करता है, इसलिए 12 का मतलब 12 pt है। डबल‑स्पेसिंग के लिए `24.0` उपयोग करें।
- **प्रो टिप**: यदि आपको सभी फुटनोट प्रकारों (सेपरेटर, कंटिन्यूएशन सेपरेटर, आदि) में समान रूप चाहिए, तो `doc.getFootnoteContinuationSeparator()` और `doc.getFootnoteContinuationNotice()` के लिए भी वही चरण दोहराएँ।
- **गलती**: संशोधनों के बाद `save()` कॉल करना भूल जाना। मेमोरी में दस्तावेज़ बदलता है, लेकिन डिस्क पर फ़ाइल वही रहती है।
- **प्रो टिप**: स्पेसिंग परिवर्तन को स्टाइल अपडेट (`ParagraphStyle`) के साथ मिलाएँ ताकि फुटनोट सेक्शन पूरी तरह से परिपूर्ण हो।

## पूर्ण कार्यशील उदाहरण (सभी चरण एक फ़ाइल में)

```java
import com.aspose.words.*;

public class FootnoteSpacingDemo {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Load the DOCX document
        Document doc = new Document("input.docx");

        // 2️⃣ Adjust the footnote separator – this is where we "change footnote spacing"
        adjustFootnoteSeparator(doc);

        // 3️⃣ Verify the new line spacing (optional but handy for debugging)
        verifySpacing(doc);

        // 4️⃣ Save the result – now your footnotes have the desired spacing
        doc.save("output.docx");
        System.out.println("Footnote spacing updated and saved to output.docx");
    }

    private static void adjustFootnoteSeparator(Document doc) throws Exception {
        FootnoteSeparator separator = doc.getFootnoteSeparator();
        if (separator == null) {
            separator = new FootnoteSeparator(doc);
            doc.getFootnotes().add(separator);
        }
        Paragraph sepParagraph = separator.getSeparatorParagraph();
        ParagraphFormat fmt = sepParagraph.getParagraphFormat();

        // Core operation: "set paragraph line spacing" for the separator
        fmt.setLineSpacing(12.0);   // 12 pt line spacing
        fmt.setSpaceBefore(0);
        fmt.setSpaceAfter(0);
    }

    private static void verifySpacing(Document doc) throws Exception {
        FootnoteSeparator sep = doc.getFootnoteSeparator();
        double spacing = sep.getSeparatorParagraph().getParagraphFormat().getLineSpacing();
        System.out.println("Current footnote separator line spacing: " + spacing);
    }
}
```

ऊपर दिया गया कोड नई Java क्लास में कॉपी करें, Aspose.Words Maven निर्भरता जोड़ें, और इसे चलाएँ। आपका `output.docx` अब फुटनोट सेपरेटर की लाइन स्पेसिंग **12 pt** पर सेट होगा, प्रभावी रूप से **फुटनोट स्पेसिंग बदलते** हुए।

### Maven निर्भरता

यह स्निपेट अपने `pom.xml` में जोड़ें:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version> <!-- Use the latest stable version -->
</dependency>
```

यदि आप Gradle पसंद करते हैं, तो समकक्ष यह है:

```gradle
implementation 'com.aspose:aspose-words:24.9'
```

## निष्कर्ष

आपने अभी Java का उपयोग करके DOCX फ़ाइल में **फुटनोट स्पेसिंग बदलना** सीख लिया है। दस्तावेज़ लोड करके, **फुटनोट सेपरेटर** प्राप्त करके, और **पैराग्राफ लाइन स्पेसिंग सेट** करके, आप फुटनोट की उपस्थिति पर सटीक नियंत्रण प्राप्त करते हैं।  

अब आप संबंधित बदलावों की खोज कर सकते हैं, जैसे फुटनोट टेक्स्ट स्टाइल बदलना, कस्टम सेपरेटर जोड़ना, या कई दस्तावेज़ों में बल्क अपडेट को स्वचालित करना।  

**फुटनोट सेपरेटर समायोजित करें** या अन्य Word ऑटोमेशन कार्यों के बारे में और प्रश्न हैं? टिप्पणी छोड़ें, और कोडिंग का आनंद लें!

## अब आप क्या सीखें अगले?

निम्नलिखित ट्यूटोरियल्स उन निकट संबंधित विषयों को कवर करते हैं जो इस गाइड में दिखाए गए तकनीकों पर आधारित हैं। प्रत्येक संसाधन में पूर्ण कार्यशील कोड उदाहरण और चरण‑दर‑चरण व्याख्याएँ शामिल हैं जो आपको अतिरिक्त API सुविधाओं में महारत हासिल करने और अपने प्रोजेक्ट्स में वैकल्पिक कार्यान्वयन दृष्टिकोणों की खोज करने में मदद करती हैं।

- [Word दस्तावेज़ में एशियन पैराग्राफ स्पेसिंग और इंडेंट बदलें](/words/english/net/document-formatting/change-asian-paragraph-spacing-and-indents/)
- [एशियन पैराग्राफ स्पेसिंग और इंडेंट बदलें](/words/german/net/document-formatting/change-asian-paragraph-spacing-and-indents/)
- [एशियन पैराग्राफ स्पेसिंग और इंडेंट बदलें](/words/french/net/document-formatting/change-asian-paragraph-spacing-and-indents/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}