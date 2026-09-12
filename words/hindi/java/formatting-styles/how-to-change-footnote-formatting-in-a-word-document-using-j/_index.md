---
category: general
date: 2026-09-11
description: Aspose.Words के साथ जावा में फुटनोट फ़ॉर्मेटिंग कैसे बदलें, सीखें। यह
  गाइड बताता है कि फुटनोट को कैसे संपादित करें, फुटनोट शैली को अपडेट करें, और फुटनोट
  सेपरेटर को संशोधित करें।
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- change footnote formatting
- how to edit footnote
- update footnote style
- modify footnote separator
language: hi
lastmod: 2026-09-11
og_description: Aspose.Words के साथ जावा में फुटनोट फ़ॉर्मेटिंग बदलें। फुटनोट को संपादित
  करने, फुटनोट शैली को अपडेट करने और फुटनोट सेपरेटर को संशोधित करने के लिए इस पूर्ण
  गाइड का पालन करें।
og_image_alt: Screenshot showing change footnote formatting in a Java editor
og_title: जावा में फुटनोट फॉर्मेटिंग बदलें – चरण-दर-चरण गाइड
schemas:
- author: Aspose
  dateModified: '2026-09-11'
  description: Learn how to change footnote formatting in Java with Aspose.Words.
    This guide explains how to edit footnote, update footnote style, and modify footnote
    separator.
  headline: How to change footnote formatting in a Word document using Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- Footnote
- Document processing
title: जावा का उपयोग करके वर्ड दस्तावेज़ में फुटनोट फॉर्मेटिंग कैसे बदलें
url: /hi/java/formatting-styles/how-to-change-footnote-formatting-in-a-word-document-using-j/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word दस्तावेज़ में फुटनोट फ़ॉर्मेटिंग कैसे बदलें Java का उपयोग करके

यदि आपको Word दस्तावेज़ में **फुटनोट फ़ॉर्मेटिंग** बदलनी है, तो यह ट्यूटोरियल Aspose.Words for Java का उपयोग करके सटीक चरणों के माध्यम से आपका मार्गदर्शन करता है। चाहे आप एक प्रकाशन पाइपलाइन बना रहे हों या केवल प्रोग्रामेटिक रूप से **फुटनोट को कैसे संपादित करें** दिखावट की आवश्यकता हो, नीचे दिया गया समाधान फ़ाइल लोड करने से लेकर अपडेटेड संस्करण को सहेजने तक सब कुछ कवर करता है।

आप सीखेंगे कि **फुटनोट स्टाइल को अपडेट** कैसे करें, फुटनोट सेपरेटर को बोल्ड बनाएं, और यहाँ तक कि **फुटनोट सेपरेटर** की फ़ॉन्ट साइज या रंग जैसी प्रॉपर्टीज़ को **संशोधित** कैसे करें। यह गाइड मानता है कि आपके पास बुनियादी Java ज्ञान और एक कार्यशील Aspose.Words for Java लाइसेंस है।

## पूर्वापेक्षाएँ

* Java 17 या नया स्थापित हो।
* Aspose.Words for Java (संस्करण 23.12 या बाद का) आपके प्रोजेक्ट के क्लासपाथ में जोड़ा गया हो।
* एक Word दस्तावेज़ (`input.docx`) जिसमें कम से कम एक फुटनोट हो।
* कोड को कंपाइल और रन करने के लिए एक IDE या बिल्ड टूल (Maven/Gradle)।

यदि आप नहीं जानते कि Aspose.Words को Maven प्रोजेक्ट में कैसे जोड़ें, तो अपने `pom.xml` में निम्नलिखित डिपेंडेंसी शामिल करें:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.12</version>
</dependency>
```

## Aspose.Words for Java के साथ फुटनोट फ़ॉर्मेटिंग बदलें

समाधान का मूल एक छोटा Java प्रोग्राम है जो दस्तावेज़ को लोड करता है, फुटनोट सेपरेटर पैराग्राफ तक पहुँचता है, उसकी फ़ॉर्मेटिंग बदलता है, और परिणाम को सहेजता है। कोड पूरी तरह से स्व-निहित है, इसलिए आप इसे नई क्लास में कॉपी करके तुरंत चला सकते हैं।

```java
import com.aspose.words.*;

public class ChangeFootnoteFormatting {
    public static void main(String[] args) throws Exception {
        // Step 1: Load the Word document
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // Step 2: Retrieve the footnote separator paragraph
        Paragraph footnoteSeparator = doc.getFootnoteSeparator();

        // Defensive check – the separator may be empty in some documents
        if (footnoteSeparator.getRuns().getCount() == 0) {
            // Create a new run so we have something to format
            Run run = new Run(doc);
            run.setText("\u2022"); // bullet character as placeholder
            footnoteSeparator.appendChild(run);
        }

        // Step 3: Change the first run's formatting – this is where we
        //          modify footnote separator appearance
        Run firstRun = footnoteSeparator.getRuns().get(0);
        Font font = firstRun.getFont();
        font.setBold(true);                // make the separator bold
        font.setItalic(true);              // optional: also italic
        font.setSize(10.0);                // set font size to 10 pt
        font.setColor(java.awt.Color.GRAY); // change color to a subtle gray

        // Step 4: Save the updated document
        doc.save("YOUR_DIRECTORY/output.docx");
    }
}
```

### प्रत्येक चरण का महत्व

* **Loading the document** (`new Document`) एक इन‑मेमोरी प्रतिनिधित्व बनाता है जिसे Aspose.Words हेरफेर कर सकता है।  
* **Retrieving the footnote separator** (`getFootnoteSeparator`) आपको उस पैराग्राफ तक सीधी पहुँच देता है जो फुटनोट को मुख्य टेक्स्ट से अलग करता है। यह वह तत्व है जिसे आपको **फुटनोट फ़ॉर्मेटिंग** बदलते समय लक्षित करना चाहिए।  
* **Formatting the run** (`setBold`, `setItalic`, `setSize`, `setColor`) दर्शाता है कि **फुटनोट सेपरेटर** की प्रॉपर्टीज़ को कैसे **संशोधित** किया जाए। आप यहाँ कोई भी अतिरिक्त फ़ॉन्ट एट्रिब्यूट जोड़ सकते हैं, जैसे अंडरलाइन या हाइलाइट, ताकि दिखावट पर पूर्ण नियंत्रण हो सके।  
* **Saving the document** बदलावों को डिस्क पर लिखता है, एक नई फ़ाइल (`output.docx`) बनाता है जो अपडेटेड फुटनोट स्टाइल को दर्शाती है।

> **Pro tip:** यदि आपके स्रोत दस्तावेज़ में एक कस्टम फुटनोट सेपरेटर है जिसमें कई रन (जैसे, विभिन्न प्रतीकों का संयोजन) शामिल हैं, तो `footnoteSeparator.getRuns()` पर लूप करें और प्रत्येक रन पर समान `Font` सेटिंग्स लागू करें ताकि स्टाइलिंग सुसंगत रहे।

## प्रोग्रामेटिक रूप से फुटनोट सेपरेटर को संपादित करना

कभी‑कभी आपको न केवल सेपरेटर बल्कि फुटनोट टेक्स्ट स्वयं को भी संपादित करने की आवश्यकता हो सकती है। वही API प्रत्येक फुटनोट तक पहुँचने, उसके पैराग्राफ फ़ॉर्मेटिंग को समायोजित करने, या नंबरिंग स्टाइल बदलने के लिए उपयोग की जा सकती है।

```java
for (Footnote footnote : (Iterable<Footnote>) doc.getFootnotes()) {
    // Example: make all footnote text italic and 9 pt
    for (Paragraph para : (Iterable<Paragraph>) footnote.getParagraphs()) {
        para.getParagraphFormat().setStyleIdentifier(StyleIdentifier.FOOTNOTE_TEXT);
        para.getRuns().forEach(run -> {
            Font f = run.getFont();
            f.setItalic(true);
            f.setSize(9.0);
        });
    }
}
```

ऊपर दिया गया स्निपेट **फुटनोट को कैसे संपादित करें** दिखाता है, जब आपने पहले से **फुटनोट फ़ॉर्मेटिंग** सेपरेटर के लिए बदल दी है। `doc.getFootnotes()` पर इटरेट करके आप सुनिश्चित करते हैं कि प्रत्येक फुटनोट समान स्टाइल विरासत में प्राप्त करे, जो एक प्रोफेशनल‑लुकिंग दस्तावेज़ के लिए आवश्यक है।

## सुसंगत दस्तावेज़ उपस्थिति के लिए फुटनोट स्टाइल अपडेट करें

यदि आप व्यक्तिगत रन के बजाय स्टाइल के साथ काम करना पसंद करते हैं, तो Aspose.Words आपको एक `Style` ऑब्जेक्ट बनाने या संशोधित करने और फिर उसे फुटनोट और सेपरेटर दोनों पर लागू करने की अनुमति देता है। यह दृष्टिकोण तब उपयोगी होता है जब आपको कई दस्तावेज़ों में **फुटनोट स्टाइल को अपडेट** करने की आवश्यकता हो।

```java
// Create or retrieve a style named "MyFootnoteStyle"
Style footnoteStyle = doc.getStyles().add(StyleType.PARAGRAPH, "MyFootnoteStyle");
footnoteStyle.getFont().setBold(true);
footnoteStyle.getFont().setSize(10);
footnoteStyle.getFont().setColor(java.awt.Color.DARK_GRAY);

// Apply the style to the separator
footnoteSeparator.getParagraphFormat().setStyle(footnoteStyle);

// Apply the same style to every footnote paragraph
for (Footnote fn : (Iterable<Footnote>) doc.getFootnotes()) {
    for (Paragraph p : (Iterable<Paragraph>) fn.getParagraphs()) {
        p.getParagraphFormat().setStyle(footnoteStyle);
    }
}
```

एक समर्पित स्टाइल का उपयोग भविष्य में रखरखाव को आसान बनाता है—स्टाइल को एक बार बदलें, और सभी फुटनोट और सेपरेटर स्वचालित रूप से अपडेट हो जाते हैं। यह तकनीक बड़े‑पैमाने पर प्रकाशन वर्कफ़्लो में **फुटनोट स्टाइल को अपडेट** करने का अनुशंसित तरीका है।

## अपने ब्रांडिंग के अनुसार फुटनोट सेपरेटर को संशोधित करें

ब्रांड गाइडलाइन कभी‑कभी यह निर्धारित करती हैं कि फुटनोट सेपरेटर को एक विशिष्ट कैरेक्टर (जैसे, एस्टेरिस्क) या कस्टम लाइन का उपयोग करना चाहिए। Aspose.Words आपको डिफ़ॉल्ट सेपरेटर कंटेंट को पूरी तरह से बदलने की सुविधा देता है।

```java
// Remove existing runs
footnoteSeparator.getRuns().clear();

// Insert a custom separator line
Run customRun = new Run(doc);
customRun.setText("--- Custom Separator ---");
Font customFont = customRun.getFont();
customFont.setBold(true);
customFont.setSize(8);
customFont.setColor(java.awt.Color.BLUE);
footnoteSeparator.appendChild(customRun);
```

ऊपर दिया गया कोड **फुटनोट सेपरेटर** को मौजूदा सभी रन को साफ़ करके और इच्छित टेक्स्ट व फ़ॉर्मेटिंग के साथ एक नया रन डालकर **संशोधित** करता है। आप यूनिकोड कैरेक्टर्स जैसे `\u2022` (बुलेट) या `\u2014` (एम डैश) का उपयोग भी कर सकते हैं ताकि आपके ब्रांड द्वारा आवश्यक सटीक विज़ुअल इफ़ेक्ट प्राप्त हो सके।

## अपेक्षित परिणाम

प्रोग्राम चलाने के बाद:

* `output.docx` में फुटनोट सेपरेटर **बोल्ड**, **इटैलिक**, 10 pt, और ग्रे (या आपके द्वारा सेट किया गया कोई भी रंग) दिखता है।  
* सभी फुटनोट पैराग्राफ आपके द्वारा परिभाषित स्टाइल को अपनाते हैं, जिससे दस्तावेज़ में एक समान लुक सुनिश्चित होता है।  
* यदि आपने सेपरेटर टेक्स्ट को बदल दिया है, तो नई कस्टम लाइन ठीक उसी जगह दिखाई देती है जहाँ मूल लाइन थी।

परिणामी फ़ाइल को Microsoft Word या LibreOffice Writer में खोलें और बदलावों की पुष्टि करें। आपको पहला फुटनोट के ठीक ऊपर अपडेटेड सेपरेटर दिखना चाहिए, और फुटनोट टेक्स्ट में आपके द्वारा लागू किए गए किसी भी स्टाइल संशोधन को प्रतिबिंबित करना चाहिए।

## सामान्य समस्याएँ और उन्हें कैसे टालें

| Issue | Why it happens | Fix |
|-------|----------------|-----|
| `footnoteSeparator.getRuns().getCount() == 0` throws an exception | Some documents have an empty separator paragraph. | Add a defensive check and create a run if none exist (see the code example). |
| Font changes are not visible | The document uses a theme that overrides direct formatting. | Set `font.setThemeFont(null)` or apply a custom style instead of direct formatting. |
| Saved file does not reflect changes | The original file is still open in Word, locking the output path. | Close any instances of the file before running the program, or |

## आगे आप क्या सीखें?

निम्नलिखित ट्यूटोरियल्स उन विषयों को कवर करते हैं जो इस गाइड में प्रदर्शित तकनीकों पर आधारित हैं। प्रत्येक संसाधन में पूर्ण कार्यशील कोड उदाहरण और चरण‑दर‑चरण व्याख्याएँ शामिल हैं, जो आपको अतिरिक्त API फीचर्स में महारत हासिल करने और अपने प्रोजेक्ट्स में वैकल्पिक इम्प्लीमेंटेशन अप्रोचेज़ का अन्वेषण करने में मदद करेंगे।

- [फ़ुटनोट और एंडनोट के साथ शब्द प्रोसेसिंग](/words/english/net/working-with-footnote-and-endnote/)
- [फ़ुटनोट और एंडनोट पोज़ीशन सेट करें](/words/english/net/working-with-footnote-and-endnote/set-footnote-and-end-note-position/)
- [Java में Aspose.Words संस्करण जानकारी कैसे प्रदर्शित करें: एक व्यापक गाइड](/words/english/java/getting-started/aspose-words-java-version-info/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}