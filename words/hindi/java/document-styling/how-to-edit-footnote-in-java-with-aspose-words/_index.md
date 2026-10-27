---
category: general
date: 2026-08-07
description: Aspose.Words के साथ जावा में फुटनोट को कैसे संपादित करें – कस्टम डैश
  जोड़ें, फुटनोट लाइन बदलें, और परिष्कृत दस्तावेज़ों के लिए पैराग्राफ संरेखण सेट करें।
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to edit footnote
- add custom dash
- change footnote line
- change footnote separator
- set paragraph alignment
language: hi
lastmod: 2026-08-07
og_description: Aspose.Words के साथ जावा में फुटनोट को कैसे संपादित करें। कस्टम डैश
  जोड़ना, फुटनोट लाइन बदलना, और कुछ ही चरणों में पैराग्राफ संरेखण सेट करना सीखें।
og_image_alt: Java code editing footnote separator with a custom dash and centered
  alignment
og_title: Java में फुटनोट कैसे संपादित करें – डैश जोड़ें, लाइन बदलें, संरेखण सेट करें
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: How to edit footnote in Java with Aspose.Words – add custom dash, change
    footnote line, and set paragraph alignment for polished documents.
  headline: How to edit footnote in Java with Aspose.Words
  type: TechArticle
- description: How to edit footnote in Java with Aspose.Words – add custom dash, change
    footnote line, and set paragraph alignment for polished documents.
  name: How to edit footnote in Java with Aspose.Words
  steps:
  - name: '**Loading the document** – `new Document(...)` reads the DOCX file into
      memory, giving you access to all its nodes.'
    text: '**Loading the document** – `new Document(...)` reads the DOCX file into
      memory, giving you access to all its nodes.'
  - name: '**Fetching the separator** – `getFootnoteSeparator()` returns the special
      paragraph that Aspose.Words treats as the footnote line. This object is the
      only place you can safely modify the separator.'
    text: '**Fetching the separator** – `getFootnoteSeparator()` returns the special
      paragraph that Aspose.Words treats as the footnote line. This object is the
      only place you can safely modify the separator.'
  - name: '**Setting paragraph alignment** – `setAlignment(ParagraphAlignment.CENTER)`
      changes the line’s alignment. The keyword *set paragraph alignment* is applied
      directly to the separator, ensuring a centered dash.'
    text: '**Setting paragraph alignment** – `setAlignment(ParagraphAlignment.CENTER)`
      changes the line’s alignment. The keyword *set paragraph alignment* is applied
      directly to the separator, ensuring a centered dash.'
  - name: '**Adding a custom dash** – By clearing existing runs and adding a new `Run`
      with the em‑dash character (`—`), you achieve the *add custom dash* effect while
      also *change footnote line* to your desired style.'
    text: '**Adding a custom dash** – By clearing existing runs and adding a new `Run`
      with the em‑dash character (`—`), you achieve the *add custom dash* effect while
      also *change footnote line* to your desired style.'
  - name: '**Saving the document** – `doc.save(...)` writes the changes back to disk,
      producing an output file that reflects all modifications.'
    text: '**Saving the document** – `doc.save(...)` writes the changes back to disk,
      producing an output file that reflects all modifications.'
  type: HowTo
tags:
- Aspose.Words
- Java
- Footnotes
title: Aspose.Words के साथ जावा में फुटनोट कैसे संपादित करें
url: /hi/java/document-styling/how-to-edit-footnote-in-java-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Java में Aspose.Words के साथ फुटनोट कैसे संपादित करें

यदि आपको Java का उपयोग करके Word दस्तावेज़ में **how to edit footnote** करने की आवश्यकता है, तो यह गाइड पूरी कार्यप्रणाली दिखाता है। आप कस्टम डैश जोड़ना, फुटनोट लाइन बदलना, और पैराग्राफ एलाइमेंट सेट करना सीखेंगे ताकि फुटनोट सेपरेटर पेशेवर दिखे।

फुटनोट को संपादित करना कानूनी अनुबंधों, शैक्षणिक पत्रों, या मार्केटिंग ब्रोशर तैयार करते समय एक सामान्य आवश्यकता है। नीचे दिए गए चरण सभी चीज़ों को कवर करते हैं—दस्तावेज़ लोड करने से लेकर अंतिम फ़ाइल सहेजने तक—बिना अतिरिक्त टूल की आवश्यकता के।

## पूर्वापेक्षाएँ

शुरू करने से पहले सुनिश्चित करें कि आपके पास है:

* Java 17 या उससे नया स्थापित हो।
* Aspose.Words for Java (नवीनतम संस्करण) को अपने प्रोजेक्ट की classpath में जोड़ें।
* एक DOCX फ़ाइल (`input.docx`) जिसमें कम से कम एक फुटनोट हो।

इन वस्तुओं से यह सुनिश्चित होता है कि कोड रनटाइम त्रुटियों के बिना चलेगा।

## फुटनोट सेपरेटर और लाइन को कैसे संपादित करें

फुटनोट सेपरेटर वह पैराग्राफ है जो मुख्य टेक्स्ट और फुटनोट सूची के बीच दिखाई देता है। इसकी उपस्थिति बदलने से पठनीयता में सुधार होता है और कॉर्पोरेट ब्रांडिंग से मेल खाता है।

```java
import com.aspose.words.*;

public class FootnoteSeparatorDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Load the document containing footnotes
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // Step 2: Get the footnote separator paragraph (the line before the footnote list)
        Paragraph separator = doc.getFootnoteSeparator();

        // Step 3: Center‑align the separator for better appearance
        separator.getParagraphFormat().setAlignment(ParagraphAlignment.CENTER);

        // Step 4: Replace the default separator line with a custom dash
        separator.getRuns().clear();                 // Remove existing runs
        separator.getRuns().add(new Run(doc, "—"));   // Add a custom dash character

        // Step 5: Save the modified document
        doc.save("YOUR_DIRECTORY/output.docx");
    }
}
```

### प्रत्येक पंक्ति क्यों महत्वपूर्ण है

1. **Loading the document** – `new Document(...)` DOCX फ़ाइल को मेमोरी में पढ़ता है, जिससे आपको उसके सभी नोड्स तक पहुंच मिलती है।
2. **Fetching the separator** – `getFootnoteSeparator()` वह विशेष पैराग्राफ लौटाता है जिसे Aspose.Words फुटनोट लाइन के रूप में मानता है। यह ऑब्जेक्ट वह एकमात्र जगह है जहाँ आप सुरक्षित रूप से सेपरेटर को संशोधित कर सकते हैं।
3. **Setting paragraph alignment** – `setAlignment(ParagraphAlignment.CENTER)` लाइन की एलाइमेंट बदलता है। *set paragraph alignment* कीवर्ड सीधे सेपरेटर पर लागू होता है, जिससे डैश केंद्रित रहता है।
4. **Adding a custom dash** – मौजूदा रन को साफ़ करके और `Run` में em‑dash कैरेक्टर (`—`) जोड़कर आप *add custom dash* प्रभाव प्राप्त करते हैं और साथ ही *change footnote line* को अपनी इच्छित शैली में बदलते हैं।
5. **Saving the document** – `doc.save(...)` बदलावों को डिस्क पर लिखता है, जिससे एक आउटपुट फ़ाइल बनती है जो सभी संशोधनों को दर्शाती है।

## फुटनोट सेपरेटर में कस्टम डैश जोड़ें

**Step 4** में दिखाया गया कोड *add custom dash* तकनीक को प्रदर्शित करता है। आप em‑dash को किसी भी स्ट्रिंग, जैसे `"***"` या `"---"` से बदल सकते हैं, ताकि यह आपके दस्तावेज़ की दृश्य भाषा से मेल खाए।

```java
separator.getRuns().clear();                     // Remove default line
separator.getRuns().add(new Run(doc, "***"));    // Insert three asterisks as a custom dash
```

डिफ़ॉल्ट पतली लाइन ब्रांडिंग गाइडलाइन को पूरा नहीं करती हो तो कस्टम डैश विशेष रूप से उपयोगी होता है।

## फुटनोट लाइन शैली बदलें

यदि आप डैश की बजाय ठोस लाइन पसंद करते हैं, तो आप Unicode बॉक्स‑ड्रॉइंग कैरेक्टर या दोहराए गए अंडरस्कोर डाल सकते हैं।

```java
separator.getRuns().clear();
separator.getRuns().add(new Run(doc, "_____")); // Five underscores create a solid line
```

*change footnote line* चरण वही रहता है चाहे आप कोई भी कैरेक्टर चुनें, क्योंकि सेपरेटर पैराग्राफ केवल वह टेक्स्ट रेंडर करता है जो उसमें होता है।

## फुटनोट सेपरेटर के लिए पैराग्राफ एलाइमेंट सेट करें

*set paragraph alignment* ऑपरेशन केवल सेंटर एलाइमेंट तक सीमित नहीं है। आप लेआउट की जरूरतों के अनुसार बाएँ, दाएँ या जस्टिफ़ाई कर सकते हैं।

```java
separator.getParagraphFormat().setAlignment(ParagraphAlignment.RIGHT); // Right‑align
```

सेपरेटर को दाएँ संरेखित करना उन दस्तावेज़ों में उपयोगी हो सकता है जो दाएँ‑संरेखित फुटनोट का उपयोग करते हैं, जैसे द्विभाषी प्रकाशन।

## पूर्ण, चलाने योग्य उदाहरण

नीचे पूरा प्रोग्राम दिया गया है जो सभी अवधारणाओं को सम्मिलित करता है—दस्तावेज़ लोड करना, फुटनोट सेपरेटर संपादित करना, कस्टम डैश जोड़ना, लाइन शैली बदलना, और एलाइमेंट सेट करना।

```java
import com.aspose.words.*;

public class FootnoteSeparatorDemo {
    public static void main(String[] args) throws Exception {
        // Load the source document
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // Retrieve the footnote separator paragraph
        Paragraph separator = doc.getFootnoteSeparator();

        // Set the desired alignment (center, left, right, or justify)
        separator.getParagraphFormat().setAlignment(ParagraphAlignment.CENTER);

        // Clear any existing content in the separator
        separator.getRuns().clear();

        // Add a custom dash – replace with any string to change footnote line
        separator.getRuns().add(new Run(doc, "—")); // Em‑dash as the custom dash

        // Save the updated document
        doc.save("YOUR_DIRECTORY/output.docx");
    }
}
```

**Expected output:** `output.docx` फ़ाइल में मूल पतली लाइन की जगह एक केंद्रित em‑dash होगा। सभी फुटनोट अपरिवर्तित रहेंगे, और दस्तावेज़ का लेआउट नई सेपरेटर शैली को दर्शाएगा।

## सामान्य समस्याएँ और उन्हें कैसे टालें

| समस्या | कारण | समाधान |
|-------|--------|-----|
| Separator not found | Document में फुटनोट नहीं हैं या कस्टम फुटनोट शैली उपयोग में है | `getFootnoteSeparator()` कॉल करने से पहले सुनिश्चित करें कि स्रोत DOCX में कम से कम एक फुटनोट हो |
| Custom dash not visible | फ़ॉन्ट चयनित कैरेक्टर को सपोर्ट नहीं करता | ऐसा Unicode कैरेक्टर उपयोग करें जो दस्तावेज़ के डिफ़ॉल्ट फ़ॉन्ट द्वारा समर्थित हो, या संगत फ़ॉन्ट एम्बेड करें |
| Alignment appears unchanged | पैराग्राफ फ़ॉर्मेट बाद में कोड में ओवरराइड हो रहा है | किसी भी अन्य फ़ॉर्मेटिंग कॉल के बाद **alignment** लागू करें जो इसे रीसेट कर सकती हैं |

इन बिंदुओं को संबोधित करने से रनटाइम त्रुटियों से बचाव होता है और *how to edit footnote* प्रक्रिया विश्वसनीय रूप से काम करती है।

## अगले कदम

अब जब आप **how to edit footnote** तत्वों को जानते हैं, तो आप संबंधित कार्यों का अन्वेषण कर सकते हैं:

* **Add custom footnote reference style** – `FootnoteReference` नोड्स को संशोधित करके नंबरिंग या प्रतीक बदलें।
* **Programmatically insert new footnotes** – डायनामिक कंटेंट के लिए `DocumentBuilder.insertFootnote()` का उपयोग करें।
* **Apply conditional formatting** – पैराग्राफ शैली या कंटेंट लंबाई के आधार पर फुटनोट की उपस्थिति बदलें।

इनमें से प्रत्येक विस्तार वही API सतह पर आधारित है जिसका आपने *add custom dash*, *change footnote line*, और *set paragraph alignment* के लिए उपयोग किया था।

---

*हैप्पी कोडिंग! यदि ट्यूटोरियल ने आपको फुटनोट संपादन में महारत हासिल करने में मदद की, तो इसे अपनी टीम के साथ साझा करने या उदाहरण को और बेहतर बनाने के लिए एक पुल रिक्वेस्ट योगदान करने पर विचार करें।*


## What Should You Learn Next?

निम्नलिखित ट्यूटोरियल्स उन विषयों को कवर करते हैं जो इस गाइड में प्रदर्शित तकनीकों पर आधारित हैं। प्रत्येक संसाधन में पूर्ण कार्यशील कोड उदाहरण और चरण‑दर‑चरण व्याख्याएँ शामिल हैं, जो आपको अतिरिक्त API फीचर सीखने और अपने प्रोजेक्ट में वैकल्पिक कार्यान्वयन दृष्टिकोणों का अन्वेषण करने में मदद करेंगे।

- [फुटनोट और एंड नोट पोजीशन सेट करें](/words/hindi/net/working-with-footnote-and-endnote/set-footnote-and-end-note-position/)
- [Aspose.Words for Java में DocumentBuilder का उपयोग करके फ़ॉर्म फ़ील्ड बनाना और कंटेंट जोड़ना](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Aspose.Words for Java में LoadOptions सेट करना](/words/english/java/document-loading-and-saving/using-load-options/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}