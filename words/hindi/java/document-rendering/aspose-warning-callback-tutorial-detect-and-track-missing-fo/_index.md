---
category: general
date: 2026-03-17
description: Aspose चेतावनी कॉलबैक ट्यूटोरियल सीखें ताकि जावा दस्तावेज़ों में लापता
  फ़ॉन्ट्स का पता लगाया जा सके और उनका ट्रैक रखा जा सके, एक पूर्ण, चलाने योग्य उदाहरण
  के साथ।
draft: false
keywords:
- aspose warning callback tutorial
- detect missing fonts
- track missing fonts
language: hi
og_description: Aspose चेतावनी कॉलबैक ट्यूटोरियल में महारत हासिल करें ताकि आप अपने
  जावा वर्ड प्रोसेसिंग वर्कफ़्लो में गायब फ़ॉन्ट्स का पता लगा सकें और उनका ट्रैक रख
  सकें।
og_title: Aspose चेतावनी कॉलबैक ट्यूटोरियल – लापता फ़ॉन्ट्स का पता लगाएँ
tags:
- Aspose.Words
- Java
- Font Substitution
- Document Processing
title: Aspose चेतावनी कॉलबैक ट्यूटोरियल – लापता फ़ॉन्ट्स का पता लगाएँ और ट्रैक करें
url: /hi/java/document-rendering/aspose-warning-callback-tutorial-detect-and-track-missing-fo/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# aspose warning callback tutorial – गायब फ़ॉन्ट्स का पता लगाएँ और ट्रैक करें

क्या आपने कभी सोचा है कि **गायब फ़ॉन्ट्स** का पता कैसे लगाया जाए जब आप Aspose.Words के साथ Word फ़ाइलें बदल रहे हों या संपादित कर रहे हों? आप अकेले नहीं हैं। कई वास्तविक‑दुनिया प्रोजेक्ट्स में, एक अनजाना फ़ॉन्ट लेआउट गड़बड़ियों का कारण बन सकता है, और आपको एक भरोसेमंद तरीका चाहिए **गायब फ़ॉन्ट्स को ट्रैक करने** का, इससे पहले कि वे बाद में समस्या बनें।  

अच्छी खबर? **aspose warning callback tutorial** आपको एक साफ़, प्रोग्रामेटिक हुक देता है जो उन फ़ॉन्ट‑सब्स्टिट्यूशन चेतावनियों को ठीक उसी समय प्रिंट करता है जब वे उत्पन्न होती हैं। इस गाइड में हम कॉलबैक सेटअप करना, दस्तावेज़ लोड करना, और चेतावनियों को कार्य में देखना—सभी Java में—परिचित करेंगे।

इस लेख के अंत तक आप स्वचालित रूप से गायब फ़ॉन्ट्स का पता लगा पाएँगे, उन्हें लॉग करेंगे, और यह तय करेंगे कि प्रतिस्थापन एम्बेड करना है या स्रोत फ़ाइलों को समायोजित करना है। कोई बाहरी टूल्स आवश्यक नहीं।

## Prerequisites

- **Java 8+** (कोड किसी भी हालिया JDK के साथ कम्पाइल होता है)
- **Aspose.Words for Java** संस्करण 23.10 या नया – Aspose पोर्टल से डाउनलोड करें या Maven डिपेंडेंसी जोड़ें।
- एक सैंपल DOCX जिसमें जानबूझकर ऐसा फ़ॉन्ट रेफ़रेंस हो जो आपके सिस्टम में इंस्टॉल न हो (जैसे, Linux बॉक्स पर “Comic Sans MS”)।

बस इतना ही—कोई अतिरिक्त लाइब्रेरी नहीं, कोई जटिल बिल्ड स्टेप नहीं।

## Step 1: Register a Warning Callback – The Core of the aspose warning callback tutorial

ट्यूटोरियल का पहला चरण है एक warning listener को अटैच करना। Aspose.Words हर समस्या के लिए एक `WarningInfo` ऑब्जेक्ट उठाता है, और `WarningSource.FONT_SUBSTITUTION` फ़्लैग हमें ठीक वही बताता है जब फ़ॉन्ट बदल रहा हो।

```java
import com.aspose.words.*;

public class FontDiagnostics {
    public static void main(String[] args) throws Exception {

        // Step 1: Register a warning callback to capture font substitution warnings.
        Document.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) {
                // We only care about font‑substitution events.
                if (info.getSource() == WarningSource.FONT_SUBSTITUTION) {
                    System.out.println("Font substitution warning:");
                    System.out.println("  Original:   " + info.getDescription());
                    System.out.println("  Substituted:" + info.getAdditionalInfo());
                }
            }
        });
```

**यह क्यों महत्वपूर्ण है:** कॉलबैक के बिना, Aspose चुपचाप गायब फ़ॉन्ट्स को बदल देता है, और आपको कभी नहीं पता चलता कि कौन‑से glyphs गलत दिख सकते हैं। चेतावनी को लॉग करके आप **गायब फ़ॉन्ट्स** का जल्दी पता लगा सकते हैं और सही फ़ॉन्ट एम्बेड करने का निर्णय ले सकते हैं।

> **Pro tip:** यदि आपको बाद में रिपोर्टिंग के लिए चेतावनियों को इकट्ठा करना है, तो सीधे प्रिंट करने के बजाय उन्हें `List<WarningInfo>` में स्टोर करें।

## Step 2: Load the Document – Where missing fonts might hide

अब हम उस DOCX को लोड करते हैं जिसमें संभवतः ऐसे फ़ॉन्ट्स रेफ़रेंस हैं जो मशीन पर मौजूद नहीं हैं। लोडिंग प्रक्रिया चेतावनी कॉलबैक को ट्रिगर करती है यदि कोई फ़ॉन्ट गायब हो।

```java
        // Step 2: Load a document that may contain missing fonts.
        Document document = new Document("YOUR_DIRECTORY/input.docx");
```

**पर्दे के पीछे क्या हो रहा है?** Aspose दस्तावेज़ की स्टाइल डिफ़िनिशन्स को पार्स करता है, प्रत्येक टेक्स्ट रन को स्कैन करता है, और सिस्टम के फ़ॉन्ट रिपॉज़िटरी की जाँच करता है। जब वह सटीक मैच नहीं ढूँढ पाता, तो वह एक सब्स्टिट्यूट पर फ़ॉल्बैक करता है और वही चेतावनी फायर करता है जिसे हमने अभी हुक किया है।

## Step 3: Save the Document – Flushing the warnings

अंत में, हम दस्तावेज़ को सेव करते हैं। सेव ऑपरेशन भी फ़ॉन्ट्स को फिर से‑इवैल्यूएट करता है, इसलिए लोड के दौरान नहीं निकली कोई चेतावनी अब दिखाई देगी।

```java
        // Step 3: Save the document; any font substitution warnings will be printed by the callback.
        document.save("YOUR_DIRECTORY/output.docx");
    }
}
```

जब आप प्रोग्राम चलाएँगे, तो आपको कंसोल आउटपुट कुछ इस तरह दिखेगा:

```
Font substitution warning:
  Original:   Font "Comic Sans MS" not found.
  Substituted: Using "Arial" as fallback.
```

यह आउटपुट साबित करता है कि **aspose warning callback tutorial** काम कर रहा है, और आपने सफलतापूर्वक **गायब फ़ॉन्ट्स का पता लगाया** और अब **गायब फ़ॉन्ट्स को ट्रैक** कर रहे हैं लॉग के माध्यम से।

## How to Detect Missing Fonts in a Word Document – Beyond the Basics

कॉलबैक तरीका एक‑बार के रन के लिए बढ़िया है, लेकिन कभी‑कभी आपको एक पुन: उपयोग योग्य यूटिलिटी चाहिए होती है। यहाँ एक छोटा रैपर है जिसे आप किसी भी प्रोजेक्ट में डाल सकते हैं:

```java
public class FontMissingChecker {
    private final List<String> missingFonts = new ArrayList<>();

    public FontMissingChecker() {
        Document.setWarningCallback((WarningInfo info) -> {
            if (info.getSource() == WarningSource.FONT_SUBSTITUTION) {
                missingFonts.add(info.getDescription());
            }
        });
    }

    public List<String> check(String path) throws Exception {
        new Document(path); // triggers warnings
        return missingFonts;
    }
}
```

इसे इस तरह कॉल करें:

```java
FontMissingChecker checker = new FontMissingChecker();
List<String> fonts = checker.check("input.docx");
if (!fonts.isEmpty()) {
    System.out.println("Missing fonts detected:");
    fonts.forEach(System.out::println);
}
```

अब आपके पास एक पुन: उपयोग योग्य **detect missing fonts** मेथड है जो एक लिस्ट रिटर्न करता है, जिसे आप CI पाइपलाइन या UI में फीड कर सकते हैं।

## Tracking Missing Fonts with Aspose.Words – Reporting for Teams

बड़ी टीम में, आप कई दस्तावेज़ों में सभी गायब फ़ॉन्ट्स की CSV रिपोर्ट बनाना चाह सकते हैं। पिछले यूटिलिटी को सरल फ़ाइल इटरेशन के साथ मिलाएँ:

```java
import java.nio.file.*;
import java.io.*;

public class BulkFontReporter {
    public static void main(String[] args) throws Exception {
        Path folder = Paths.get("YOUR_DIRECTORY");
        try (BufferedWriter writer = Files.newBufferedWriter(folder.resolve("missing-fonts-report.csv"))) {
            writer.write("Document,Missing Font\n");
            Files.list(folder)
                 .filter(p -> p.toString().endsWith(".docx"))
                 .forEach(p -> {
                     try {
                         FontMissingChecker checker = new FontMissingChecker();
                         List<String> missing = checker.check(p.toString());
                         for (String msg : missing) {
                             // Extract font name from description
                             String font = msg.replaceAll("Font \"(.*?)\".*", "$1");
                             writer.write(p.getFileName() + "," + font + "\n");
                         }
                     } catch (Exception e) {
                         // In a real app, log the error
                     }
                 });
        }
        System.out.println("Report generated at missing-fonts-report.csv");
    }
}
```

इस स्क्रिप्ट को चलाने पर आपको एक **track missing fonts** CSV मिलेगा, जिसे हर डेवलपर प्रोडक्शन में डॉक्यूमेंट कमिट करने से पहले देख सकता है।

## Common Pitfalls & How to Avoid Them

| Pitfall | Why it Happens | Fix |
|---------|----------------|-----|
| **Callback not firing** | आपने कॉलबैक को **डॉक्यूमेंट लोड करने से पहले** सेट करना भूल गए। | `Document.setWarningCallback` को `main` के सबसे ऊपर रखें। |
| **Only first warning appears** | Aspose प्रत्येक `Document` इंस्टेंस के लिए चेतावनियों को कैश करता है। | प्रत्येक फ़ाइल के लिए नया `Document` ऑब्जेक्ट उपयोग करें, या रन के बीच कॉलबैक रीसेट करें। |
| **Wrong font name in log** | विवरण में अतिरिक्त टेक्स्ट (“Font … not found”) शामिल होता है। | CSV उदाहरण में दिखाए अनुसार regex से स्ट्रिप करें। |
| **Performance hit on large batches** | कॉलबैक हर टेक्स्ट रन पर चलता है, जो महँगा हो सकता है। | प्री‑फ़्लाइट स्टेप तक चेक को सीमित रखें; यदि केवल डिटेक्शन चाहिए तो सेविंग को स्किप करें। |

## Expected Results & Verification

1. **Console output** – प्रत्येक गायब फ़ॉन्ट के लिए कम से कम एक “Font substitution warning” लाइन दिखनी चाहिए।  
2. **CSV report** – बैच स्क्रिप्ट समाप्त होने के बाद `missing-fonts-report.csv` खोलें और सुनिश्चित करें कि प्रत्येक पंक्ति में डॉक्यूमेंट नाम और सटीक गायब फ़ॉन्ट लिस्टेड है।  
3. **Saved document** – आउटपुट DOCX फॉलबैक फ़ॉन्ट्स का उपयोग करके रेंडर होगा, लेकिन विज़ुअल लेआउट मूल से अलग हो सकता है।

यदि इन चरणों में से कोई भी वर्णित अनुसार काम नहीं करता, तो जाँचें कि Aspose.Words JAR आपके क्लासपाथ में है और `input.docx` वास्तव में ऐसे फ़ॉन्ट को रेफ़रेंस करता है जो आपके OS में मौजूद नहीं है।

## Conclusion

आपने अभी-अभी एक **aspose warning callback tutorial** पूरा किया जिससे आप **गायब फ़ॉन्ट्स का पता लगा** और **गायब फ़ॉन्ट्स को ट्रैक** कर सकते हैं Java एप्लिकेशन में। एक warning listener रजिस्टर करके, डॉक्यूमेंट लोड करके, और वैकल्पिक रूप से निष्कर्षों को एक्सपोर्ट करके, आप प्रोडक्शन में फ़ॉन्ट‑संबंधी समस्याओं के सामने आने से पहले पूरी दृश्यता प्राप्त करते हैं।

अगला, आप एक्सप्लोर कर सकते हैं:

- `LoadOptions.setFontSubstitution` के साथ गायब फ़ॉन्ट को सीधे एम्बेड करना।
- `FontSettings` क्लास का उपयोग करके गायब फ़ॉन्ट्स को विशिष्ट सब्स्टिट्यूट्स से मैप करना।
- CSV रिपोर्ट को CI/CD पाइपलाइन में इंटीग्रेट करना ताकि अनडॉक्युमेंटेड फ़ॉन्ट्स मिलने पर बिल्ड फेल हो जाए।

इसे आज़माएँ, कॉलबैक को अपने लॉगिंग फ्रेमवर्क के अनुसार ट्यून करें, और देखें कि आपका डॉक्यूमेंट वर्कफ़्लो कितना अधिक मजबूत हो जाता है। Happy coding!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}