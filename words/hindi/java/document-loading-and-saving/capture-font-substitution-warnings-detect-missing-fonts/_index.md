---
category: general
date: 2026-04-04
description: Aspose.Words for Java का उपयोग करके Word दस्तावेज़ लोड करते समय फ़ॉन्ट
  प्रतिस्थापन चेतावनियों को पकड़ें और स्वचालित रूप से गायब फ़ॉन्ट्स का पता लगाएँ।
  इस चरण‑दर‑चरण मार्गदर्शिका का पालन करें।
draft: false
keywords:
- capture font substitution warnings
- detect missing fonts
language: hi
og_description: Aspose.Words for Java का उपयोग करके Word दस्तावेज़ लोड करते समय फ़ॉन्ट
  प्रतिस्थापन चेतावनियों को पकड़ें और कुछ आसान चरणों में गायब फ़ॉन्ट्स का पता लगाएँ।
og_title: फ़ॉन्ट प्रतिस्थापन चेतावनियों को कैप्चर करें – गायब फ़ॉन्ट्स का पता लगाएँ
tags:
- Aspose.Words
- Java
- Document Processing
title: फ़ॉन्ट प्रतिस्थापन चेतावनियों को कैप्चर करें – गायब फ़ॉन्ट्स का पता लगाएँ
url: /hi/java/document-loading-and-saving/capture-font-substitution-warnings-detect-missing-fonts/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# फ़ॉन्ट प्रतिस्थापन चेतावनियों को कैप्चर करें – लापता फ़ॉन्ट्स का पता लगाएँ

क्या आपको कभी Word फ़ाइल खोलते समय **फ़ॉन्ट प्रतिस्थापन चेतावनियों** को कैप्चर करने की ज़रूरत पड़ी है, केवल यह पता चलने पर कि एक महत्वपूर्ण टाइपफ़ेस गायब है? आप अकेले नहीं हैं। कई एंटरप्राइज़ वर्कफ़्लो में एक लापता फ़ॉन्ट एक पूरी तरह से फ़ॉर्मेटेड रिपोर्ट को गड़बड़ mess में बदल सकता है, और एकमात्र संकेत जो आपको मिलता है वह एक चुप्पी चेतावनी है जिसे अधिकांश डेवलपर्स कभी नहीं देखते।

अच्छी खबर यह है कि Aspose.Words for Java आपको लोडिंग प्रक्रिया में हुक करने देता है और **लापता फ़ॉन्ट्स का पता** लगाने में मदद करता है इससे पहले कि वे बाद में समस्या बनें। इस ट्यूटोरियल में हम एक पूर्ण, चलाने योग्य उदाहरण के माध्यम से चलेंगे जो प्रत्येक प्रतिस्थापन चेतावनी को सीधे कंसोल में प्रिंट करता है, ताकि आप तय कर सकें कि सही फ़ॉन्ट को एम्बेड करना है, उसे बदलना है, या उपयोगकर्ता को सूचित करना है।

इस गाइड के अंत तक आप जानेंगे कैसे:

* एक कस्टम वार्निंग कॉलबैक के साथ `LoadOptions` ऑब्जेक्ट सेट अप करें।
* कॉलबैक को फ़िल्टर करें ताकि वह केवल फ़ॉन्ट‑सबस्टीट्यूशन इवेंट्स पर प्रतिक्रिया दे।
* किसी भी `.docx` फ़ाइल को लोड करें और तुरंत चेतावनियों को देखें।
* समाधान को विस्तारित करें ताकि चेतावनियों को लॉग किया जा सके, एक्सेप्शन थ्रो किया जा सके, या यहाँ तक कि लापता फ़ॉन्ट्स को ऑटो‑इंस्टॉल किया जा सके।

कोई बाहरी दस्तावेज़ीकरण आवश्यक नहीं—सिर्फ कुछ पंक्तियों का Java कोड और Aspose.Words JAR।

## पूर्वापेक्षाएँ

डाइव करने से पहले, सुनिश्चित करें कि आपके पास है:

* Java 8 या उससे नया स्थापित हो (नवीनतम LTS संस्करण सबसे अच्छा काम करता है)।
* Aspose.Words for Java 23.11 या बाद का – आप Maven आर्टिफैक्ट या Aspose वेबसाइट से साधारण JAR प्राप्त कर सकते हैं।
* एक Word दस्तावेज़ जिसमें ऐसा फ़ॉन्ट रेफ़रेंस हो जो आपके विकास मशीन पर नहीं है (उदा., “MyFancyFont”)।  
* आपका पसंदीदा IDE या टेक्स्ट एडिटर – मैं IntelliJ IDEA उपयोग कर रहा हूँ, लेकिन Eclipse या VS Code भी ठीक रहेगा।

यदि इनमें से कोई भी परिचित नहीं लग रहा है, तो पहले उन्हें इंस्टॉल करें; ट्यूटोरियल का बाकी हिस्सा यह मानता है कि वे तैयार हैं।

---

## Aspose.Words का उपयोग करके फ़ॉन्ट प्रतिस्थापन चेतावनियों को कैप्चर करें

समाधान का मुख्य भाग एक `LoadOptions` इंस्टेंस में रहता है। `IWarningCallback` असाइन करके हम लोड चरण के दौरान लाइब्रेरी द्वारा उत्पन्न प्रत्येक चेतावनी को इंटरसेप्ट कर सकते हैं।

```java
import com.aspose.words.*;

public class FontDiagnosticsTutorial {
    public static void main(String[] args) throws Exception {

        // Step 1️⃣: Create LoadOptions and set a warning callback.
        LoadOptions loadOptions = new LoadOptions();
        loadOptions.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) {
                // Capture only font substitution warnings.
                if (info.getWarningType() == WarningType.SUBSTITUTED_FONT) {
                    System.out.println("Font substitution: " + info.getDescription());
                }
            }
        });

        // Step 2️⃣: Load the document. The callback runs automatically.
        Document doc = new Document("YOUR_DIRECTORY/document-with-missing-font.docx", loadOptions);

        // Step 3️⃣: If you reach this line, the document is loaded.
        // Any missing‑font warnings have already been printed to the console.
        System.out.println("Document loaded successfully.");
    }
}
```

**यह क्यों काम करता है:**  
`LoadOptions` Aspose.Words को बताता है कि आने वाली फ़ाइल को कैसे ट्रीट करना है। `IWarningCallback` इंटरफ़ेस एक हुक है जो *हर* चेतावनी के लिए एक `WarningInfo` ऑब्जेक्ट प्राप्त करता है। `info.getWarningType()` की जाँच करके हम सब कुछ फ़िल्टर कर देते हैं सिवाय `SUBSTITUTED_FONT` के। `description` प्रॉपर्टी में एक मानव‑पठनीय संदेश होता है जैसे “Font 'MyFancyFont' was substituted with 'Arial'”।

### अपेक्षित कंसोल आउटपुट

यदि स्रोत दस्तावेज़ ऐसा फ़ॉन्ट रेफ़रेंस करता है जो स्थापित नहीं है, तो आप कुछ इस तरह देखेंगे:

```
Font substitution: Font 'MyFancyFont' was substituted with 'Arial'.
Document loaded successfully.
```

यदि दस्तावेज़ केवल उन फ़ॉन्ट्स का उपयोग करता है जो मशीन पर मौजूद हैं, तो कॉलबैक चुप रहता है और आपको केवल अंतिम “Document loaded successfully.” लाइन मिलती है।

## अपने दस्तावेज़ में लापता फ़ॉन्ट्स का पता लगाएँ

आप सोच सकते हैं, *“क्या एक प्रतिस्थापन चेतावनी लापता फ़ॉन्ट के समान है?”* अधिकांश मामलों में, हाँ—Aspose.Words लापता फ़ॉन्ट को एक फ़ॉलबैक से बदल देता है और इसे `SUBSTITUTED_FONT` के माध्यम से रिपोर्ट करता है। हालांकि, कुछ किनारे के मामलों में फ़ॉन्ट मौजूद होता है लेकिन सटीक स्टाइल (बोल्ड‑इटैलिक, विशिष्ट OpenType फीचर्स) नहीं होता, जिससे एक सूक्ष्म प्रतिस्थापन होता है।

पूरी तरह सुनिश्चित करने के लिए कि आपने हर गैप पकड़ लिया है, आप वार्निंग कॉलबैक को पोस्ट‑लोड निरीक्षण के साथ जोड़ सकते हैं:

```java
// After loading the document, iterate through all runs.
for (Paragraph para : (Iterable<Paragraph>) doc.getFirstSection().getBody().getChildNodes(NodeType.PARAGRAPH, true)) {
    for (Run run : (Iterable<Run>) para.getChildNodes(NodeType.RUN, true)) {
        Font font = run.getFont();
        if (font.getName().equalsIgnoreCase("MyFancyFont")) {
            System.out.println("Run still uses the missing font: " + font.getName());
        }
    }
}
```

**प्रो टिप:** यदि आप कोई रन पाते हैं जो अभी भी लापता फ़ॉन्ट को रेफ़रेंस कर रहा है, तो आप उन्हें तुरंत बदल सकते हैं:

```java
font.setName("Arial"); // fallback
```

इस तरह आप एक सुसंगत विज़ुअल परिणाम सुनिश्चित करते हैं, भले ही मूल चेतावनी दबा दी गई हो।

## सामान्य जाल और उन्हें कैसे टालें

| जाल | क्यों होता है | समाधान |
|---------|----------------|-----|
| **कॉलबैक सेट करना भूलना** | `LoadOptions` डिफ़ॉल्ट रूप से कोई‑ऑप कॉलबैक रखता है, इसलिए चेतावनियाँ गायब हो जाती हैं। | लोड करने से पहले हमेशा `loadOptions.setWarningCallback(...)` कॉल करें। |
| **गलत वार्निंग टाइप का उपयोग करना** | `WarningType.SUBSTITUTED_FONT` एकमात्र enum है जो लापता फ़ॉन्ट्स को संकेत देता है। | `WarningType.SUBSTITUTED_FONT` पर *सटीक* फ़िल्टर करें; अन्य प्रकार (जैसे `UNKNOWN_FILE_FORMAT`) असंबंधित हैं। |
| **फ़ाइल पाथ को हार्ड‑कोड करना** | स्थानीय रूप से काम करता है लेकिन CI/CD पाइपलाइन पर टूट जाता है। | रिलेटिव पाथ उपयोग करें या फ़ाइल लोकेशन को कमांड‑लाइन आर्ग्यूमेंट के रूप में पास करें। |
| **Unicode फ़ॉन्ट्स को अनदेखा करना** | कुछ लापता फ़ॉन्ट्स केवल कुछ विशेष अक्षरों के लिए समस्या बनते हैं। | उस दस्तावेज़ के साथ टेस्ट करें जिसमें वह पूरा कैरेक्टर सेट हो जिसे आप सपोर्ट करने की उम्मीद करते हैं। |
| **फ़ॉन्ट कॉन्फ़िग के बिना हेडलेस सर्वर पर चलाना** | सर्वर में कोई फ़ॉलबैक फ़ॉन्ट नहीं हो सकता, जिससे अप्रत्याशित प्रतिस्थापन होते हैं। | सर्वर पर सामान्य फ़ॉन्ट्स (Arial, Times New Roman) का न्यूनतम सेट इंस्टॉल करें। |

## समाधान का विस्तार

अब जब आप **फ़ॉन्ट प्रतिस्थापन चेतावनियों को कैप्चर** कर सकते हैं, तो आप चाह सकते हैं:

* **फ़ाइल में चेतावनियों को लॉग करें** – `System.out.println` को SLF4J जैसे लॉगर से बदलें।
* **एक एक्सेप्शन थ्रो करें** – स्वचालित पाइपलाइन में उपयोगी जहाँ लापता फ़ॉन्ट बिल्ड को फेल कर देना चाहिए:

```java
if (info.getWarningType() == WarningType.SUBSTITUTED_FONT) {
    throw new RuntimeException("Missing font detected: " + info.getDescription());
}
```

* **लापता फ़ॉन्ट्स को ऑटो‑इंस्टॉल करें** – रनटाइम पर आवश्यक TTF/OTF डाउनलोड करें और उसे Java `GraphicsEnvironment` में जोड़ें। यह एक अधिक उन्नत परिदृश्य है, लेकिन पूरी तरह संभव है।

## डायग्राम (वैकल्पिक)

![फ़ॉन्ट प्रतिस्थापन चेतावनियों के प्रवाह डायग्राम जिसमें LoadOptions → WarningCallback → कंसोल आउटपुट दिखाया गया है](capture-font-substitution-warnings-diagram.png)

*Alt text:* “फ़ॉन्ट प्रतिस्थापन चेतावनियों का प्रवाह डायग्राम जो दर्शाता है कि Aspose.Words लापता‑फ़ॉन्ट चेतावनियों को एक कस्टम कॉलबैक तक कैसे रूट करता है।”

## निष्कर्ष

हमने अभी-अभी बताया कि Aspose.Words for Java के साथ Word दस्तावेज़ लोड करते समय **फ़ॉन्ट प्रतिस्थापन चेतावनियों को कैप्चर** और **लापता फ़ॉन्ट्स का पता** कैसे लगाया जाता है। `LoadOptions` ऑब्जेक्ट को कॉन्फ़िगर करके और एक छोटा `IWarningCallback` लागू करके, आप फ़ॉन्ट‑फ़ॉलबैक प्रक्रिया में पूरी दृश्यता प्राप्त करते हैं, जिससे आप लापता टाइपफ़ेस पर लॉग, बदल या एबॉर्ट कर सकते हैं।

सारांश में: कॉलबैक सेट करें, `SUBSTITUTED_FONT` पर फ़िल्टर करें, दस्तावेज़ लोड करें, और आउटपुट को अपनी एप्लिकेशन की आवश्यकता अनुसार हैंडल करें। यहाँ से आप लॉगिंग फ्रेमवर्क, CI चेक्स, या यहाँ तक कि ऑटोमेटेड फ़ॉन्ट प्रोविज़निंग तक विस्तार कर सकते हैं।

और आगे बढ़ना चाहते हैं? कोशिश करें:

* **फ़ॉन्ट्स को एम्बेड करना** सीधे सहेजे गए दस्तावेज़ में (`doc.save(..., SaveOptions.createSaveOptions(SaveFormat.DOCX))` के साथ `FontEmbeddingMode.EMBED_ALL`)।
* **फ़ॉन्ट्स को ठीक करने के बाद PDF बनाना**, जिससे अंतिम आउटपुट बिल्कुल इच्छित जैसा दिखे।
* **दस्तावेज़ों के पूरे फ़ोल्डर को स्कैन करना** लापता फ़ॉन्ट्स के लिए और एक सारांश रिपोर्ट बनाना।

अभी के लिए बस इतना ही—हैप्पी कोडिंग, और आपकी दस्तावेज़ हमेशा सही टाइपफ़ेस के साथ रेंडर हों!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}