---
category: general
date: 2026-04-28
description: Aspose.Words for Java का उपयोग करके Word फ़ाइल में दस्तावेज़ चेतावनियों
  को इटरेट करें, गायब फ़ॉन्ट्स का पता लगाएँ, गायब फ़ॉन्ट नाम प्राप्त करें और गायब
  फ़ॉन्ट विवरण प्रिंट करें।
draft: false
keywords:
- iterate document warnings
- detect missing fonts
- load word document
- retrieve missing font
- print missing font
language: hi
og_description: दस्तावेज़ चेतावनियों को दोहराएँ ताकि गायब फ़ॉन्ट्स मिल सकें, गायब
  फ़ॉन्ट नाम प्राप्त करें, और पूर्ण जावा उदाहरण के साथ गायब फ़ॉन्ट विवरण प्रिंट करें।
og_title: 'दस्तावेज़ चेतावनियों को दोहराएँ: जावा में लापता फ़ॉन्ट्स का पता लगाएँ'
tags:
- Aspose.Words
- Java
- Document Processing
title: 'दस्तावेज़ चेतावनियों को दोहराएँ: जावा में लापता फ़ॉन्ट्स का पता लगाएँ'
url: /hi/java/document-operations/iterate-document-warnings-detect-missing-fonts-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# दस्तावेज़ चेतावनियों को इटररेट करें – जावा में लापता फ़ॉन्ट्स का पता लगाएँ

क्या आपको कभी Word फ़ाइल खोलते समय **iterate document warnings** करने की ज़रूरत पड़ी है और आप सोचते थे कि कौन से फ़ॉन्ट्स लापता हैं? आप अकेले नहीं हैं। लापता फ़ॉन्ट्स रिपोर्ट की रूपरेखा को बिगाड़ सकते हैं, और बिना उन्हें पहचानने के आप ऐसा दस्तावेज़ भेज सकते हैं जो मूल जैसा नहीं दिखेगा।  

इस ट्यूटोरियल में हम आपको दिखाएंगे कि कैसे **detect missing fonts** किया जाए Word दस्तावेज़ को लोड करके, उसकी चेतावनियों को इटररेट करके, लापता फ़ॉन्ट नामों को प्राप्त करके, और अंत में लापता फ़ॉन्ट जानकारी को प्रिंट करके—सभी Aspose.Words for Java के साथ।  

हम कोड की पहली पंक्ति से लेकर अपेक्षित कंसोल आउटपुट तक सब कुछ कवर करेंगे, ताकि आप अभी अपने प्रोजेक्ट में एक कार्यशील समाधान को कॉपी‑पेस्ट कर सकें। अतिरिक्त दस्तावेज़ों की आवश्यकता नहीं।

## आवश्यकताएँ

- Java 8 या उससे नया स्थापित हो।
- Aspose.Words for Java लाइब्रेरी (2026‑04‑28 तक का नवीनतम संस्करण)।
- एक Word फ़ाइल जिसमें संभवतः आपके मशीन पर स्थापित न किए गए फ़ॉन्ट्स हों (उदाहरण के लिए `doc-with-missing-font.docx`)।

यदि आपके पास ये सब है, तो बढ़िया—आप **load word document** करने और इटररेट करने के लिए तैयार हैं।

## चरण 1 – डिफ़ॉल्ट विकल्पों के साथ Word दस्तावेज़ लोड करें

**iterate document warnings** करने से पहले, फ़ाइल को मेमोरी में लोड करना आवश्यक है। Aspose.Words आपको यह एकल कंस्ट्रक्टर कॉल से करने देता है। डिफ़ॉल्ट `LoadOptions` आमतौर पर पर्याप्त होते हैं, लेकिन स्पष्टता के लिए हम स्पष्ट निर्माण दिखाएंगे।

```java
import com.aspose.words.*;

public class MissingFontDetector {
    public static void main(String[] args) throws Exception {

        // Step 1: Prepare load options (default settings are fine for this example)
        LoadOptions loadOptions = new LoadOptions();

        // Step 2: Load the document that may contain missing fonts
        Document document = new Document("YOUR_DIRECTORY/doc-with-missing-font.docx", loadOptions);
```

> **यह क्यों महत्वपूर्ण है:**  
> दस्तावेज़ को लोड करने से Aspose.Words फ़ाइल को स्कैन करता है ताकि कोई भी संसाधन जो वह हल नहीं कर सकता, जैसे कि स्थानीय रूप से स्थापित न किए गए फ़ॉन्ट्स, खोज सके। इन समस्याओं को **warnings** के रूप में संग्रहीत किया जाता है, जिन्हें हम अगले चरण में **iterate document warnings** करेंगे।

## चरण 2 – फ़ॉन्ट समस्याओं को खोजने के लिए दस्तावेज़ चेतावनियों को इटररेट करें

अब समाधान का मुख्य भाग आता है: हम लोड करते समय लाइब्रेरी द्वारा एकत्रित प्रत्येक चेतावनी पर लूप चलाते हैं। `WarningInfo` ऑब्जेक्ट्स हमें बताते हैं क्या गलत हुआ, और हम `FontSubstitutionWarning` को फ़िल्टर करके **detect missing fonts** कर सकते हैं।

```java
        // Step 3: Iterate over all warnings generated during loading
        for (WarningInfo warningInfo : document.getWarnings()) {
            // Step 4: Identify font substitution warnings
            if (warningInfo instanceof FontSubstitutionWarning) {
                FontSubstitutionWarning fontWarning = (FontSubstitutionWarning) warningInfo;

                // Step 5: Output the missing font name and the font that was used as a substitute
                System.out.println("Missing font: " + fontWarning.getMissingFontName());
                System.out.println("Substituted with: " + fontWarning.getSubstitutedFontName());
            }
        }
    }
}
```

> **प्रो टिप:** `instanceof` जाँच यह सुनिश्चित करती है कि हम केवल फ़ॉन्ट‑संबंधी चेतावनियों को संभालें, अन्य जैसे इमेज‑लोडिंग समस्याओं को अनदेखा करें। इससे लूप कुशल बनता है और आउटपुट उन फ़ॉन्ट्स पर केंद्रित रहता है जिनके लिए आपको वास्तव में **retrieve missing font** जानकारी चाहिए।

### अपेक्षित कंसोल आउटपुट

```
Missing font: Arial Black
Substituted with: Liberation Sans
Missing font: Calibri
Substituted with: Liberation Sans
```

यदि दस्तावेज़ में कोई लापता फ़ॉन्ट नहीं है, तो लूप चुपचाप समाप्त हो जाता है—कोई **print missing font** नहीं।

## चरण 3 – फिर क्यों न केवल अपवाद को पकड़ें?

आप सोच सकते हैं, “`new Document(...)` कॉल को try‑catch में लपेट कर अपवाद की तलाश क्यों नहीं की जाए?” उत्तर दो भागों में है:

1. **Granular Information:** अपवाद केवल यह बताते हैं कि कुछ विफल हुआ। चेतावनियाँ आपको सटीक फ़ॉन्ट नाम और वह फॉलबैक देती हैं जो Aspose.Words ने चुना।
2. **Non‑Fatal Issues:** लापता फ़ॉन्ट्स आमतौर पर गैर‑घातक होते हैं; दस्तावेज़ अभी भी लोड हो जाता है, लेकिन दृश्य सटीकता प्रभावित होती है। **iterating document warnings** करके आप फ़ाइल के बाकी हिस्से को प्रोसेस करने की क्षमता बनाए रखते हैं।

## चरण 4 – उदाहरण का विस्तार: लापता फ़ॉन्ट्स को सूची में एकत्र करना

कभी‑कभी आपको आगे की प्रोसेसिंग के लिए लापता फ़ॉन्ट्स चाहिए होते हैं—शायद उन्हें एम्बेड करने के लिए या UI के माध्यम से उपयोगकर्ता को चेतावनी देने के लिए। यहाँ एक त्वरित बदलाव है जो नामों को `Set<String>` में इकट्ठा करता है।

```java
        // Collect missing fonts for later use
        Set<String> missingFonts = new HashSet<>();

        for (WarningInfo warningInfo : document.getWarnings()) {
            if (warningInfo instanceof FontSubstitutionWarning) {
                FontSubstitutionWarning fontWarning = (FontSubstitutionWarning) warningInfo;
                missingFonts.add(fontWarning.getMissingFontName());

                // Still print for immediate feedback
                System.out.println("Missing font: " + fontWarning.getMissingFontName());
                System.out.println("Substituted with: " + fontWarning.getSubstitutedFontName());
            }
        }

        // Example of using the collected data
        System.out.println("Total missing fonts: " + missingFonts.size());
```

अब आपके पास प्रोग्रामेटिक रूप से **retrieve missing font** डेटा प्राप्त करने का साफ़ तरीका है, जिसे आप रिपोर्टिंग मॉड्यूल या फ़ॉन्ट‑इंस्टॉलेशन विज़ार्ड में फीड कर सकते हैं।

## चरण 5 – वास्तविक‑विश्व विचार

- **Multiple Substitutions:** एक लापता फ़ॉन्ट को दस्तावेज़ के विभिन्न हिस्सों में विभिन्न फ़ॉन्ट्स द्वारा प्रतिस्थापित किया जा सकता है। चेतावनी सूची में प्रत्येक घटना शामिल होगी, इसलिए आप डुप्लिकेट लापता‑फ़ॉन्ट प्रविष्टियों को देख सकते हैं।
- **Performance:** बहुत बड़े दस्तावेज़ लोड करने से हजारों चेतावनियाँ उत्पन्न हो सकती हैं। यदि आप केवल फ़ॉन्ट्स की परवाह करते हैं, तो जैसा दिखाया गया है, जल्दी फ़िल्टर करें ताकि लूप तेज़ रहे।
- **Cross‑Platform Fonts:** Linux पर, डिफ़ॉल्ट प्रतिस्थापन फ़ॉन्ट अक्सर *Liberation Sans* होता है। Windows पर, यह *Arial* हो सकता है। फॉलबैक को जानने से आप तय कर सकते हैं कि क्या आपको अपने एप्लिकेशन के साथ कस्टम फ़ॉन्ट्स शिप करने की आवश्यकता है।

## चरण 6 – दृश्य सहायता

नीचे कंसोल आउटपुट का स्क्रीनशॉट दिया गया है (alt टेक्स्ट में SEO के लिए मुख्य कीवर्ड शामिल है)।

![इटररेट दस्तावेज़ चेतावनियों का कंसोल आउटपुट जिसमें लापता फ़ॉन्ट्स और उनके प्रतिस्थापन दिखाए गए हैं](/images/iterate-document-warnings.png)

*Alt text:* *इटररेट दस्तावेज़ चेतावनियों का उदाहरण जिसमें लापता फ़ॉन्ट नाम और प्रतिस्थापन विवरण दिखाए गए हैं।*

## निष्कर्ष

आपने अभी-अभी Aspose.Words for Java में **iterate document warnings**, **detect missing fonts**, **load word document** को सुरक्षित रूप से, **retrieve missing font** जानकारी, और कंसोल में **print missing font** विवरण कैसे किया जाए, सीख लिया है। पूरा कोड स्निपेट जैसा है वैसा ही चलता है, और आप इसे फ़ाइल में लॉग करने, UI डायलॉग दिखाने, या लापता फ़ॉन्ट्स को स्वचालित रूप से एम्बेड करने के लिए अनुकूलित कर सकते हैं।

अगले चरण में, आप यह देखना चाह सकते हैं कि कैसे **load word document** को कस्टम फ़ॉन्ट स्रोतों (जैसे, कॉरपोरेट फ़ॉन्ट्स के फ़ोल्डर को जोड़ना) के साथ किया जाए या लापता फ़ॉन्ट्स को सीधे फ़ाइल में एम्बेड करके विभिन्न मशीनों पर लेआउट को सुरक्षित रखा जाए। दोनों विषय यहाँ कवर किए गए सामग्री पर स्वाभाविक रूप से आधारित हैं।

कोडिंग का आनंद लें, और आपके PDFs हमेशा वही दिखें जैसा आप चाहते हैं!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}