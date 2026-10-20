---
category: general
date: 2026-06-05
description: Java में Aspose.Words का उपयोग करके गायब फ़ॉन्ट प्रतिस्थापन का पता लगाएँ।
  विश्वसनीय दस्तावेज़ प्रोसेसिंग के लिए LoadOptions, FontSettings और चेतावनी कॉलबैक
  को कैसे कॉन्फ़िगर करें, सीखें।
draft: false
keywords:
- detect missing font substitution
- Java Aspose.Words
- LoadOptions configuration
- FontSettings warning callback
- document loading Java
language: hi
og_description: Java में Aspose.Words के साथ गायब फ़ॉन्ट प्रतिस्थापन का पता लगाएँ।
  यह गाइड चरण‑दर‑चरण दिखाता है कि LoadOptions, FontSettings, और एक चेतावनी कॉलबैक
  कैसे सेट करें ताकि गायब फ़ॉन्ट को पकड़ा जा सके।
og_title: जावा में गायब फ़ॉन्ट प्रतिस्थापन का पता लगाएँ – पूर्ण Aspose.Words ट्यूटोरियल
schemas:
- author: Aspose
  dateModified: '2026-06-05'
  description: detect missing font substitution in Java using Aspose.Words. Learn
    how to configure LoadOptions, FontSettings, and warning callbacks for reliable
    document processing.
  headline: detect missing font substitution in Java – Complete Aspose.Words Guide
  type: TechArticle
- description: detect missing font substitution in Java using Aspose.Words. Learn
    how to configure LoadOptions, FontSettings, and warning callbacks for reliable
    document processing.
  name: detect missing font substitution in Java – Complete Aspose.Words Guide
  steps:
  - name: 4.1 Quick verification
    text: Run the program from your IDE or via `java -cp .;aspose-words-23.12.jar
      MissingFontDetector`. If the document references a font you don’t have, you’ll
      see the warning message printed. If the console stays silent, either the font
      exists on your machine or the document doesn’t request any missing font
  - name: 4.2 Logging instead of `System.out`
    text: 'In production code you probably want a logger:'
  - name: 4.3 Handling other warning types
    text: 'The callback receives *all* warnings, not just font issues. If you’d like
      to keep an eye on other problems (e.g., `UNKNOWN_STYLE`), add extra `if` branches.
      Here’s a quick example:'
  type: HowTo
tags:
- Aspose.Words
- Java
- Font handling
title: जावा में गायब फ़ॉन्ट प्रतिस्थापन का पता लगाएँ – पूर्ण Aspose.Words गाइड
url: /hi/java/document-loading-and-saving/detect-missing-font-substitution-in-java-complete-aspose-wor/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# जावा में मिसिंग फ़ॉन्ट सब्स्टिट्यूशन का पता लगाएँ – पूर्ण Aspose.Words गाइड

क्या आपने कभी सोचा है कि जावा में Word दस्तावेज़ लोड करते समय **मिसिंग फ़ॉन्ट सब्स्टिट्यूशन** का पता कैसे लगाया जाए? आप अकेले नहीं हैं। मिसिंग फ़ॉन्ट्स आपके PDFs या रेंडर किए गए पेजों को चुपचाप बिगाड़ सकते हैं, और उन्हें जल्दी पहचानना डिबगिंग में घंटों बचा सकता है। इस ट्यूटोरियल में हम एक व्यावहारिक समाधान पर चलते हैं जो न केवल दस्तावेज़ लोड करता है बल्कि आपको ठीक‑ठीक बताता है कि फ़ॉन्ट सब्स्टिट्यूशन कब हुआ।

हम `LoadOptions` बनाने से लेकर `WarningCallback` को जोड़ने तक सब कुछ कवर करेंगे, जो Aspose.Words द्वारा मिसिंग फ़ॉन्ट बदलने पर स्पष्ट संदेश प्रिंट करता है। अंत तक आपके पास एक पुन: उपयोग योग्य स्निपेट होगा जो किसी भी `.docx` फ़ाइल के साथ काम करता है, और आप समझेंगे कि *क्यों* प्रत्येक भाग महत्वपूर्ण है। कोई अतिरिक्त लाइब्रेरी नहीं, सिर्फ साधारण जावा और Aspose.Words।

## आप क्या सीखेंगे

- कैसे **LoadOptions** को कस्टम **FontSettings** के साथ कॉन्फ़िगर किया जाए।  
- कैसे **IWarningCallback** को इम्प्लीमेंट किया जाए जो `FONT_SUBSTITUTION` चेतावनियों को कैप्चर करता है।  
- कैसे दस्तावेज़ लोड किया जाए जबकि मिसिंग फ़ॉन्ट्स की सुरक्षित निगरानी की जा सके।  
- अपेक्षित कंसोल आउटपुट और कोड को लॉगिंग फ्रेमवर्क के लिए कैसे अनुकूलित किया जाए।  

**Prerequisites**: Java 8+ स्थापित हो, क्लासपाथ में Aspose.Words for Java (v23.12 या नया) हो, और एक नमूना `.docx` फ़ाइल हो जिसमें ऐसा फ़ॉन्ट रेफ़रेंस हो जो आपके सिस्टम में स्थापित न हो। बस इतना ही—कोई अतिरिक्त बिल्ड टूल्स की आवश्यकता नहीं।

---

## चरण 1: प्रोजेक्ट सेट अप करें और Aspose.Words जोड़ें

कोड में डुबकी लगाने से पहले सुनिश्चित करें कि Aspose.Words उपलब्ध है। यदि आप Maven उपयोग करते हैं, तो अपने `pom.xml` में निम्नलिखित डिपेंडेंसी जोड़ें:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.12</version>
</dependency>
```

यदि आप Gradle पसंद करते हैं, तो समकक्ष यह है:

```gradle
implementation 'com.aspose:aspose-words:23.12'
```

एक बार लाइब्रेरी क्लासपाथ में हो जाने पर, आप **मिसिंग फ़ॉन्ट सब्स्टिट्यूशन** को एक ही मेथड कॉल में पता लगाने के लिए तैयार हैं।

---

## चरण 2: LoadOptions बनाएं और FontSettings संलग्न करें

समाधान का दिल `LoadOptions` इंस्टेंस तैयार करने में है जो फ़ॉन्ट समस्याओं की निगरानी कर सके। यहाँ कोड को लाइन‑बाय‑लाइन समझाया गया है।

```java
import com.aspose.words.*;

public class MissingFontDetector {

    public static void main(String[] args) throws Exception {
        // 1️⃣ Prepare load options – this object controls how the document is read.
        LoadOptions loadOptions = new LoadOptions();

        // 2️⃣ Create FontSettings – it holds font‑related configuration.
        FontSettings fontSettings = new FontSettings();

        // 3️⃣ Register a warning callback that will be invoked on font substitution.
        fontSettings.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) {
                // We only care about FONT_SUBSTITUTION warnings.
                if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                    System.out.println("⚠️ Font substitution detected: " + info.getMessage());
                }
            }
        });

        // 4️⃣ Attach the FontSettings to the LoadOptions.
        loadOptions.setFontSettings(fontSettings);
```

**यह क्यों महत्वपूर्ण है**: `LoadOptions` Aspose.Words को बताता है कि आने वाली फ़ाइल को *कैसे* इंटरप्रेट करना है। एक कस्टमाइज़्ड `FontSettings` प्लग इन करके, हम लोडर को एक हुक (`IWarningCallback`) देते हैं जो **बिल्कुल तभी** फायर होता है जब कोई मिसिंग फ़ॉन्ट बदल दिया जाता है। इस कॉलबैक के बिना, Aspose.Words चुपचाप फ़ॉन्ट बदल देगा और आपको कभी पता नहीं चलेगा।

---

## चरण 3: कॉन्फ़िगर किए गए विकल्पों के साथ दस्तावेज़ लोड करें

अब जब चेतावनी प्रणाली स्थापित है, दस्तावेज़ लोड करना सीधा‑सरल हो जाता है।

```java
        // 5️⃣ Load the document using the prepared options.
        // Replace the path with the location of your test file.
        String docPath = "YOUR_DIRECTORY/docWithMissingFont.docx";
        Document doc = new Document(docPath, loadOptions);

        // Optional: do something with the document (e.g., save as PDF).
        // doc.save("output.pdf");
    }
}
```

जब `new Document(...)` कॉल चलता है, Aspose.Words फ़ाइल पढ़ता है, प्रत्येक फ़ॉन्ट रेफ़रेंस की जाँच करता है, और यदि सिस्टम पर मिलते‑जुलते फ़ॉन्ट नहीं मिलता, तो वह पहले परिभाषित `warning` मेथड को ट्रिगर करता है। कंसोल तुरंत इस तरह की लाइन दिखाएगा:

```
⚠️ Font substitution detected: Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
```

यह लाइन वही **मिसिंग फ़ॉन्ट सब्स्टिट्यूशन** आउटपुट है जिसकी आप तलाश कर रहे थे।

---

## चरण 4: परिणाम सत्यापित करें और कॉलबैक को ट्यून करें (एडवांस्ड)

### 4.1 त्वरित सत्यापन

अपने IDE से या `java -cp .;aspose-words-23.12.jar MissingFontDetector` कमांड से प्रोग्राम चलाएँ। यदि दस्तावेज़ में ऐसा फ़ॉन्ट रेफ़रेंस है जो आपके पास नहीं है, तो आपको चेतावनी संदेश प्रिंट होते दिखेंगे। यदि कंसोल शांत रहता है, तो या तो फ़ॉन्ट आपके मशीन पर मौजूद है या दस्तावेज़ में कोई मिसिंग फ़ॉन्ट नहीं है।

### 4.2 `System.out` के बजाय लॉगिंग

प्रोडक्शन कोड में आप संभवतः एक लॉगर चाहते हैं:

```java
import java.util.logging.Logger;

private static final Logger logger = Logger.getLogger(MissingFontDetector.class.getName());

fontSettings.setWarningCallback(info -> {
    if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
        logger.warning("Font substitution: " + info.getMessage());
    }
});
```

यह छोटा बदलाव **मिसिंग फ़ॉन्ट सब्स्टिट्यूशन** मैकेनिज़्म को मौजूदा लॉगिंग पाइपलाइन के साथ सुगमता से काम करने देता है।

### 4.3 अन्य चेतावनी प्रकारों को संभालना

कॉलबैक *सभी* चेतावनियों को प्राप्त करता है, न कि केवल फ़ॉन्ट समस्याओं को। यदि आप अन्य समस्याओं (जैसे `UNKNOWN_STYLE`) पर भी नज़र रखना चाहते हैं, तो अतिरिक्त `if` शाखाएँ जोड़ें। यहाँ एक त्वरित उदाहरण है:

```java
if (info.getWarningType() == WarningType.UNKNOWN_STYLE) {
    logger.info("Unknown style encountered: " + info.getMessage());
}
```

---

## चरण 5: सामान्य समस्याएँ और प्रो टिप्स

| समस्या | क्यों होता है | समाधान |
|--------|----------------|-----|
| **कोई चेतावनी नहीं दिखती** | फ़ॉन्ट वास्तव में OS पर मौजूद है, या दस्तावेज़ ऐसा फॉलबैक उपयोग करता है जिसे Aspose.Words “पाया गया” मानता है। | फ़ॉन्ट को अस्थायी रूप से सिस्टम से हटाएँ या स्रोत दस्तावेज़ में वास्तव में मिसिंग फ़ॉन्ट नाम उपयोग करें। |
| **कॉलबैक कभी नहीं बुलाया जाता** | `setWarningCallback` किसी *भिन्न* `FontSettings` इंस्टेंस पर कॉल किया गया था, जो `LoadOptions` से जुड़ा नहीं था। | कॉलबैक कॉन्फ़िगर करने के **बाद** `loadOptions.setFontSettings(fontSettings)` कॉल करना सुनिश्चित करें। |
| **परफ़ॉर्मेंस धीमा** | कई बड़े दस्तावेज़ों को कॉलबैक के साथ लोड करने से ओवरहेड बढ़ सकता है। | एक ही `FontSettings` इंस्टेंस को कैश करें और बैच प्रोसेसिंग में पुनः उपयोग करें। |
| **एकाधिक थ्रेड्स** | `FontSettings` डिफ़ॉल्ट रूप से थ्रेड‑सेफ़ नहीं है। | प्रत्येक थ्रेड के लिए अलग `FontSettings` बनाएँ या एक्सेस को सिंक्रनाइज़ करें। |

**Pro tip**: यदि आप वेब सर्विस के लिए PDFs जेनरेट कर रहे हैं, तो आप सभी सब्स्टिट्यूशन चेतावनियों को एक सूची में इकट्ठा करके API रिस्पॉन्स में लौटाना चाहेंगे, बजाय कंसोल पर प्रिंट करने के।

---

## पूर्ण कार्यशील उदाहरण (कॉपी‑पेस्ट तैयार)

```java
import com.aspose.words.*;

public class MissingFontDetector {
    public static void main(String[] args) throws Exception {
        // Prepare load options
        LoadOptions loadOptions = new LoadOptions();

        // Configure font settings with a warning callback
        FontSettings fontSettings = new FontSettings();
        fontSettings.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) {
                if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                    System.out.println("⚠️ Font substitution detected: " + info.getMessage());
                }
            }
        });

        // Attach font settings to load options
        loadOptions.setFontSettings(fontSettings);

        // Path to the document that contains a missing font
        String docPath = "YOUR_DIRECTORY/docWithMissingFont.docx";

        // Load the document – this triggers the callback if needed
        Document doc = new Document(docPath, loadOptions);

        // Optional: save as PDF to verify visual output
        // doc.save("output.pdf");

        System.out.println("Document loaded successfully.");
    }
}
```

**अपेक्षित कंसोल आउटपुट** (मान लेते हैं फ़ाइल में मिसिंग फ़ॉन्ट रेफ़रेंस है):

```
⚠️ Font substitution detected: Font 'Papyrus' was not found. Substituted with 'Times New Roman'.
Document loaded successfully.
```

यदि कोई मिसिंग फ़ॉन्ट नहीं है, तो आपको केवल अंतिम “Document loaded successfully.” लाइन दिखाई देगी।

---

## निष्कर्ष

हमने अभी-अभी दिखाया कि जावा में Aspose.Words का उपयोग करके **मिसिंग फ़ॉन्ट सब्स्टिट्यूशन** कैसे पता लगाया जाए। `LoadOptions` को कॉन्फ़िगर करके, `FontSettings` इंस्टेंस बनाकर, और `IWarningCallback` को वायर करके, आप लाइब्रेरी द्वारा बैकग्राउंड में किए जाने वाले प्रत्येक फ़ॉन्ट बदलने की पूरी दृश्यता प्राप्त करते हैं। यह तरीका न केवल चुपचाप रेंडरिंग गड़बड़ियों को रोकता है बल्कि लॉगिंग, अलर्टिंग, या यहाँ तक कि फ़ॉलबैक फ़ॉन्ट्स को ऑटो‑एम्बेड करने के लिए हुक भी प्रदान करता है।

अब आप कर सकते हैं:

- कॉलबैक को विस्तारित करके चेतावनियों को एक सूची में इकट्ठा करें और API रिस्पॉन्स में लौटाएँ।  
- इस तकनीक को **LoadOptions कॉन्फ़िगरेशन** के साथ अन्य परिदृश्यों (जैसे कस्टम रिसोर्स लोडिंग) के लिए संयोजित करें।  
- व्यापक **Java Aspose.Words** इकोसिस्टम का अन्वेषण करें: PDF में कन्वर्ट करना, टेक्स्ट एक्सट्रैक्ट करना, या मेल मर्ज करना।

इसे आज़माएँ, लॉगर को ट्यून करें, और अपने एप्लिकेशन को तब आवाज़ उठाने दें जब कोई फ़ॉन्ट गायब हो। Happy coding!

## आगे आप क्या सीखें?

निम्नलिखित ट्यूटोरियल्स उन विषयों को कवर करते हैं जो इस गाइड में प्रदर्शित तकनीकों पर आधारित हैं। प्रत्येक संसाधन में पूर्ण कार्यशील कोड उदाहरण और चरण‑दर‑चरण व्याख्याएँ शामिल हैं, जिससे आप अतिरिक्त API फीचर्स में निपुण हो सकें और अपने प्रोजेक्ट्स में वैकल्पिक इम्प्लीमेंटेशन एप्रोच को एक्सप्लोर कर सकें।

- [Capture Font Substitution Warnings in Java with Aspose.Words – Complete Guide](/words/english/java/document-loading-and-saving/capture-font-substitution-warnings-in-java-with-aspose-words/)
- [Using Document Options and Settings in Aspose.Words for Java](/words/english/java/document-manipulation/using-document-options-and-settings/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}