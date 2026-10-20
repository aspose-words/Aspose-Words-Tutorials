---
category: general
date: 2026-05-30
description: जावा में चेतावनी कॉलबैक पंजीकृत करें ताकि गायब फ़ॉन्ट्स को ट्रैक किया
  जा सके और Aspose.Words के साथ दस्तावेज़ लोडिंग को अनुकूलित किया जा सके। पूर्ण चरण‑दर‑चरण
  समाधान सीखें।
draft: false
keywords:
- register warning callback
- track missing fonts
- customize document loading
language: hi
og_description: जावा में चेतावनी कॉलबैक रजिस्टर करें ताकि गायब फ़ॉन्ट्स को ट्रैक किया
  जा सके और दस्तावेज़ लोडिंग को कस्टमाइज़ किया जा सके। कोड और व्याख्याओं के साथ पूर्ण
  गाइड।
og_title: जावा में चेतावनी कॉलबैक पंजीकृत करें – लापता फ़ॉन्ट्स को ट्रैक करें
schemas:
- author: Aspose
  dateModified: '2026-05-30'
  description: Register warning callback in Java to track missing fonts and customize
    document loading with Aspose.Words. Learn the full step‑by‑step solution.
  headline: Register warning callback in Java – Track missing fonts
  type: TechArticle
- description: Register warning callback in Java to track missing fonts and customize
    document loading with Aspose.Words. Learn the full step‑by‑step solution.
  name: Register warning callback in Java – Track missing fonts
  steps:
  - name: '**Get real‑time insight** – every `FONT_SUBSTITUTION` warning is delivered
      instantly.'
    text: '**Get real‑time insight** – every `FONT_SUBSTITUTION` warning is delivered
      instantly.'
  - name: '**Log or react** – you could log to a file, raise an alert, or even replace
      the font programmatically.'
    text: '**Log or react** – you could log to a file, raise an alert, or even replace
      the font programmatically.'
  - name: '**Maintain clean output** – knowing which fonts are missing lets you fix
      the source document before publishing.'
    text: '**Maintain clean output** – knowing which fonts are missing lets you fix
      the source document before publishing.'
  type: HowTo
- questions:
  - answer: It’s the interface Aspose.Words uses for all warning types, giving you
      a single entry point for many possible issues.
    question: Why `IWarningCallback`?
  - answer: Aspose.Words only allows one warning handler. If you need to log to both
      a file and the console, implement a composite callback that forwards the warning
      to multiple destinations.
    question: Multiple callbacks?
  type: FAQPage
tags:
- Aspose.Words
- Java
- Font handling
title: जावा में चेतावनी कॉलबैक पंजीकृत करें – गायब फ़ॉन्ट्स को ट्रैक करें
url: /hi/java/document-loading-and-saving/register-warning-callback-in-java-track-missing-fonts/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Java में warning callback रजिस्टर करें – गायब फ़ॉन्ट्स को ट्रैक करें

क्या आप कभी सोचते थे कि Aspose.Words for Java के साथ Word दस्तावेज़ लोड करते समय **गायब फ़ॉन्ट्स को कैसे ट्रैक करें**? शायद आपने उन चुपचाप फ़ॉन्ट प्रतिस्थापनों को देखा होगा और सोचा होगा, “मेरे लेआउट के साथ क्या हुआ?” अच्छी खबर यह है कि आपको अनुमान लगाने की ज़रूरत नहीं है। **warning callback रजिस्टर करके**, आप दस्तावेज़ पढ़े जाने के क्षण ही प्रत्येक फ़ॉन्ट प्रतिस्थापन इवेंट को पकड़ सकते हैं, और आप **document loading को कस्टमाइज़** भी कर सकते हैं ताकि यह आपके पाइपलाइन में फिट हो सके।

इस ट्यूटोरियल में हम एक वास्तविक‑दुनिया का उदाहरण देखेंगे जो बिल्कुल दिखाता है कि callback कैसे सेट‑अप करें, यह क्यों महत्वपूर्ण है, और आपके प्रोसेसिंग पाइपलाइन को साफ़ कैसे रखें। अंत तक आपके पास एक तैयार‑चलाने‑योग्य Java क्लास होगा जो हर missing‑font warning को प्रिंट करेगा और दस्तावेज़ की एक प्रोसेस्ड कॉपी सेव करेगा। कोई बाहरी रेफ़रेंस नहीं चाहिए—सिर्फ शुद्ध, चलने योग्य कोड।

> **आपको क्या मिलेगा:**  
> • Aspose.Words का उपयोग करके पूर्ण Java प्रोग्राम  
> • प्रत्येक लाइन की चरण‑दर‑चरण व्याख्या  
> • एन्क्रिप्टेड फ़ाइलें या बड़े बैच जैसी एज केसों को संभालने के टिप्स  
> • किसी भी `.docx` फ़ाइल पर चलाने योग्य त्वरित sanity‑check  

## Prerequisites

शुरू करने से पहले सुनिश्चित करें कि आपके पास है:

- **Java 17** (या कोई भी हालिया JDK) इंस्टॉल और `JAVA_HOME` सेट।  
- **Aspose.Words for Java** JAR आपके classpath में। आप नवीनतम संस्करण Maven Central रिपॉज़िटरी से प्राप्त कर सकते हैं:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.12</version> <!-- replace with the newest -->
</dependency>
```

- एक सैंपल Word दस्तावेज़ (`input.docx`) जिसमें आपको संदेह है कि आपके मशीन पर फ़ॉन्ट इंस्टॉल नहीं हैं।  
- एक IDE या कमांड‑लाइन बिल्ड टूल (Maven/Gradle) जिससे आप सहज हों।

बस इतना ही। कोई अतिरिक्त फ़ॉन्ट्स नहीं, कोई अतिरिक्त सर्विस नहीं—सिर्फ साधारण Java और Aspose.Words।

## Why register a warning callback?

**warning callback** को अपने दस्तावेज़ लोडिंग प्रक्रिया के लिए एक सुरक्षा कैमरा समझें। जब Aspose.Words को कोई missing glyph मिलता है, तो यह exception नहीं फेंकता; बल्कि चुपचाप एक fallback फ़ॉन्ट से बदल देता है। यह चुपचाप प्रतिस्थापन आपके लेआउट को बिगाड़ सकता है, विशेषकर ब्रांड‑क्रिटिकल PDFs या इनवॉइस में। callback रजिस्टर करके आप:

1. **रियल‑टाइम इनसाइट** प्राप्त करें – हर `FONT_SUBSTITUTION` warning तुरंत डिलीवर होती है।  
2. **लॉग या रिएक्ट** करें – आप इसे फ़ाइल में लॉग कर सकते हैं, अलर्ट उठा सकते हैं, या प्रोग्रामेटिकली फ़ॉन्ट बदल सकते हैं।  
3. **आउटपुट को साफ़ रखें** – कौन से फ़ॉन्ट्स गायब हैं, यह जानकर आप स्रोत दस्तावेज़ को प्रकाशित करने से पहले ठीक कर सकते हैं।

संक्षेप में, callback एक छिपी समस्या को दृश्यमान बनाता है, जिससे आपका दस्तावेज़ पाइपलाइन बहुत अधिक भरोसेमंद बन जाता है।

## Step 1 – Create `LoadOptions` to customize how the document is loaded

सबसे पहले हम `LoadOptions` को instantiate करते हैं। यह ऑब्जेक्ट हर लोड‑टाइम ट्यूनिंग का गेटवे है, पासवर्ड हैंडलिंग से लेकर हमारे **register warning callback** फीचर तक।

```java
// Step 1: Prepare LoadOptions for custom loading behavior
LoadOptions loadOptions = new LoadOptions();
```

क्यों सीधे `new Document("file.docx")` कॉल करें? क्योंकि `LoadOptions` के बिना आप लोडिंग इवेंट्स में हुक करने का मौका खो देते हैं। `LoadOptions` वह एकमात्र जगह है जहाँ Aspose.Words आपको **document loading को कस्टमाइज़** करने देता है।

## Step 2 – Register a warning callback to track missing fonts

अब आता है शो का स्टार: हम **warning callback रजिस्टर करते हैं** जो `IWarningCallback` को इम्प्लीमेंट करता है। `warning` मेथड के अंदर हम `WarningType.FONT_SUBSTITUTION` को फ़िल्टर करते हैं और एक मददगार संदेश प्रिंट करते हैं।

```java
// Step 2: Register a warning handler that reports font substitution events
loadOptions.setFontSubstitutionWarningHandler(new IWarningCallback() {
    @Override
    public void warning(WarningInfo info) {
        // Only react to font substitution warnings
        if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
            System.out.println("Font substitution detected: " + info.getDescription());
        }
    }
});
```

ध्यान देने योग्य कुछ बातें:

- **क्यों `IWarningCallback`?** यह वह इंटरफ़ेस है जिसे Aspose.Words सभी warning प्रकारों के लिए उपयोग करता है, जिससे आपको कई संभावित समस्याओं के लिए एक ही एंट्री पॉइंट मिलता है।  
- **फ़िल्टरिंग महत्वपूर्ण है** – `if` चेक के बिना आपको missing images, deprecated features आदि की warnings भी मिलेंगी, जो आपके लॉग को गंदा कर देंगी।  
- **थ्रेड‑सेफ़्टी** – callback उसी थ्रेड पर चलता है जो दस्तावेज़ लोड करता है, इसलिए आप सुरक्षित रूप से साझा स्ट्रक्चर को अपडेट कर सकते हैं यदि बाद में परिणाम एकत्र करने की ज़रूरत हो।

यह स्निपेट **warning callback रजिस्टर करता है**, और इस बिंदु से हर missing‑font इवेंट `stdout` पर प्रिंट होगा। यही **track missing fonts** का मूल है।

## Step 3 – Load the document using the configured `LoadOptions`

Callback सेट होने के बाद, हम अंततः फ़ाइल लोड करते हैं। यदि दस्तावेज़ में कोई ऐसा फ़ॉन्ट रेफ़रेंस है जो आपके पास नहीं है, तो callback दस्तावेज़ ऑब्जेक्ट पूरी तरह निर्मित होने से पहले फायर हो जाता है।

```java
// Step 3: Load the document with our custom LoadOptions
Document document = new Document("YOUR_DIRECTORY/input.docx", loadOptions);
```

`YOUR_DIRECTORY` को अपने मशीन पर वास्तविक पाथ से बदलें। `Document` कंस्ट्रक्टर फ़ाइल पढ़ता है, पासवर्ड (यदि आपने `loadOptions` में सेट किया है) लागू करता है, और प्रत्येक missing फ़ॉन्ट के लिए warning callback ट्रिगर करता है। आपको ऐसा आउटपुट दिखेगा:

```
Font substitution detected: Font 'Calibri' was substituted with 'Arial'.
```

यह लाइन साबित करती है कि आपने सफलतापूर्वक **track missing fonts** कर लिया है।

## Step 4 – Continue processing the document (optional)

इस चरण में आप दस्तावेज़ को अपनी इच्छा अनुसार बदल सकते हैं—टेक्स्ट बदलें, इमेज़ इन्सर्ट करें, या प्रोग्रामेटिकली प्रतिस्थापित फ़ॉन्ट्स को स्वैप करें। callback ने पहले ही समस्या वाले फ़ॉन्ट्स की सूची दे दी है, इसलिए आप उदाहरण के तौर पर एक fallback फ़ॉन्ट एम्बेड कर सकते हैं:

```java
// Optional: Replace missing fonts with a known fallback (e.g., Liberation Sans)
FontSettings fontSettings = new FontSettings();
fontSettings.setSubstitutionSettings(new FontSubstitutionSettings());
fontSettings.getSubstitutionSettings().getDefaultFontSubstitutes()
    .add("Calibri", "Liberation Sans");
document.setFontSettings(fontSettings);
```

यदि आपका उद्देश्य केवल **track missing fonts** है तो आप इस ब्लॉक को स्किप कर सकते हैं। मुख्य बात यह है कि अब आपके पास वह जानकारी है जिससे आप सूचित निर्णय ले सकें।

## Step 5 – Save the processed document

अंत में, दस्तावेज़ को सहेजें। आप मूल फ़ाइल को ओवरराइट कर सकते हैं, नई लोकेशन पर सेव कर सकते हैं, या PDF में एक्सपोर्ट कर सकते हैं—बिना उस warning डेटा को खोए जो आपने पहले कैप्चर किया था।

```java
// Step 5: Save the processed document
document.save("YOUR_DIRECTORY/processed.docx");
System.out.println("Document saved successfully.");
```

पूरे क्लास को चलाने पर हर missing फ़ॉन्ट के लिए कंसोल आउटपुट मिलेगा और उसी फ़ोल्डर में `processed.docx` नाम की नई फ़ाइल बन जाएगी।

## Complete Working Example

नीचे पूर्ण Java क्लास दिया गया है जिसे आप अपने IDE में कॉपी‑पेस्ट कर सकते हैं। इसमें हमने अब तक चर्चा किए सभी हिस्से शामिल हैं, साथ ही एक छोटा `main` मेथड रैपर भी।

```java
import com.aspose.words.*;

public class FontDiagnostic {
    public static void main(String[] args) throws Exception {
        // Step 1: Create LoadOptions to customize how the document is loaded
        LoadOptions loadOptions = new LoadOptions();

        // Step 2: Register a warning handler that reports font substitution events
        loadOptions.setFontSubstitutionWarningHandler(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) {
                if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                    System.out.println("Font substitution detected: " + info.getDescription());
                }
            }
        });

        // Step 3: Load the document using the configured LoadOptions
        Document document = new Document("YOUR_DIRECTORY/input.docx", loadOptions);

        // Optional Step 4: Replace missing fonts with a fallback (if desired)
        // FontSettings fontSettings = new FontSettings();
        // fontSettings.getSubstitutionSettings().getDefaultFontSubstitutes()
        //     .add("Calibri", "Liberation Sans");
        // document.setFontSettings(fontSettings);

        // Step 5: Save the processed document
        document.save("YOUR_DIRECTORY/processed.docx");
        System.out.println("Document saved successfully.");
    }
}
```

### Expected Output

जब आप प्रोग्राम को ऐसे दस्तावेज़ के खिलाफ चलाते हैं जिसमें आपके सिस्टम पर इंस्टॉल नहीं किया गया फ़ॉन्ट है, तो आपको कुछ इस तरह दिखेगा:

```
Font substitution detected: Font 'Times New Roman' was substituted with 'Arial'.
Font substitution detected: Font 'Cambria Math' was substituted with 'Arial Unicode MS'.
Document saved successfully.
```

यदि दस्तावेज़ में **कोई missing फ़ॉन्ट नहीं** है, तो कंसोल तब तक शांत रहेगा जब तक अंतिम “Document saved successfully.” लाइन नहीं आ जाती—बिल्कुल वही जो आप एक अच्छी तरह से व्यवहार करने वाले **register warning callback** इम्प्लीमेंटेशन से उम्मीद करेंगे।

## Pro Tips & Common Pitfalls

- **Multiple callbacks?** Aspose.Words केवल एक warning हैंडलर की अनुमति देता है। यदि आपको फ़ाइल और कंसोल दोनों में लॉग करना है, तो एक composite callback इम्प्लीमेंट करें जो warning को कई डेस्टिनेशन्स पर फॉरवर्ड करे।  
- **Large batches** – सैकड़ों फ़ाइलों को प्रोसेस करते समय, एक ही `LoadOptions` इंस्टेंस को पुनः उपयोग करने पर विचार करें; फ़ाइल‑दर‑फ़ाइल बनाना अनावश्यक ओवरहेड जोड़ता है।  
- **Encrypted docs** – लोड करने से पहले `LoadOptions` पर पासवर्ड सेट करें, अन्यथा `IncorrectPasswordException` आएगा और callback कभी फायर नहीं होगा।  
- **Performance** – callback सिंक्रोनस चलता है। यदि आप रिमोट सर्विस पर लॉग कर रहे हैं, तो संदेशों को बफ़र करें और लोड पूरा होने के बाद फ्लश करें ताकि I/O बॉटलनेक न बनें।  
- **Font fallback** – आप एक कस्टम `FontSource` कलेक्शन भी प्रदान कर सकते हैं यदि आपके पास प्रोप्राइटरी फ़ॉन्ट्स हैं जिन्हें आप Aspose.Words को सिस्टम फ़ॉन्ट्स से पहले विचार करने देना चाहते हैं।

## Conclusion

आपने अभी सीखा कि **Java में warning callback कैसे रजिस्टर करें**, प्रभावी रूप से **गायब फ़ॉन्ट्स को ट्रैक करें**, और Aspose.Words के साथ **document loading को कस्टमाइज़ करें**। यह समाधान स्व‑संकुलित है, एक ही `main` मेथड के साथ चलता है, और आपको उन सभी फ़ॉन्ट प्रतिस्थापनों की तुरंत दृश्यता देता है जो अन्यथा अनदेखी रह जातीं।

अगले कदम? callback को विस्तारित करके warnings को CSV फ़ाइल में लिखें, या एक बैच प्रोसेसर बनाएं जो स्वचालित रूप से missing फ़ॉन्ट्स को एम्बेड करे। आप `IMAGE_SUBSTITUTION` या `DEPRECATED_FEATURE` जैसे अन्य warning प्रकारों को भी एक्सप्लोर कर सकते हैं—एक ही पैटर्न लागू होता है।

Happy coding, और आपके दस्तावेज़ हमेशा वैसा ही रेंडर हों जैसा आपने इरादा किया था!

![Register warning callback diagram](register-warning-callback.png "Register warning callback flow")


## What Should You Learn Next?

- [Word दस्तावेज़ में Warning Callback](/words/english/net/programming-with-loadoptions/warning-callback/)
- [Aspose.Words Java में Theme Colors & Fonts को कस्टमाइज़ करना: एक व्यापक गाइड](/words/english/java/formatting-styles/customize-theme-colors-fonts-aspose-words-java/)
- [Aspose.Words Java का उपयोग करके Word दस्तावेज़ में परिवर्तन ट्रैक करना: दस्तावेज़ संशोधनों की पूर्ण गाइड](/words/english/java/document-comparison-tracking/aspose-words-java-track-changes-revisions/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}