---
category: general
date: 2026-03-19
description: Aspose.Words for Java में चेतावनियों को पकड़ना और लापता फ़ॉन्ट्स का पता
  लगाना सीखें। यह चरण‑दर‑चरण मार्गदर्शिका यह भी दिखाती है कि लापता फ़ॉन्ट्स को सहजता
  से कैसे संभालें।
draft: false
keywords:
- how to capture warnings
- detect missing fonts
- how to detect missing fonts
- handle missing fonts
language: hi
og_description: Aspose.Words for Java में चेतावनियों को कैसे पकड़ें, लापता फ़ॉन्ट्स
  का पता लगाएँ, और लापता फ़ॉन्ट्स को संभालें, एक पूर्ण कोड उदाहरण के साथ।
og_title: चेतावनियों को कैप्चर कैसे करें – Aspose.Words में लापता फ़ॉन्ट्स का पता
  लगाएँ
tags:
- Aspose.Words
- Java
- Font Substitution
- Document Processing
title: चेतावनियों को कैसे कैप्चर करें – Aspose.Words में लापता फ़ॉन्ट्स का पता लगाएँ
url: /hi/java/document-rendering/how-to-capture-warnings-detect-missing-fonts-in-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# चेतावनियों को कैप्चर कैसे करें – Aspose.Words में लापता फ़ॉन्ट्स का पता लगाएँ

क्या आपने कभी सोचा है **चेतावनियों को कैसे कैप्चर किया जाए** जब कोई Word दस्तावेज़ लोड होता है और कुछ फ़ॉन्ट्स मशीन पर उपलब्ध नहीं होते? आप अकेले नहीं हैं। कई वास्तविक‑दुनिया प्रोजेक्ट्स में, लापता फ़ॉन्ट्स चुपचाप लेआउट में बदलाव कर देते हैं, और यह जानने का एकमात्र तरीका है Aspose.Words द्वारा उत्पन्न चेतावनी स्ट्रीम को सुनना।  

इस ट्यूटोरियल में हम एक पूर्ण, तैयार‑चलाने‑योग्य उदाहरण के माध्यम से चलते हैं जो **लापता फ़ॉन्ट्स का पता लगाता है**, आपको **प्रोग्रामेटिक रूप से लापता फ़ॉन्ट्स का पता कैसे लगाएँ** दिखाता है, और यहाँ तक कि **लापता फ़ॉन्ट्स को संभालने** के लिए एक त्वरित टिप भी देता है ताकि आपका आउटपुट पूर्वानुमेय बना रहे।

> **त्वरित नोट:** यह कोड Aspose.Words 23.9 (या नया) के साथ काम करता है और Java 8+ की आवश्यकता होती है।

---

## आपको क्या चाहिए

- **Aspose.Words for Java** (Maven/Gradle डिपेंडेंसी या क्लासपाथ पर JAR)  
- एक Word फ़ाइल (`input.docx`) जो आपके सिस्टम पर स्थापित नहीं किए गए फ़ॉन्ट (जैसे “Comic Sans MS”) को संदर्भित करती है  
- एक Java IDE या साधारण `javac`/`java` कमांड‑लाइन सेटअप  

कोई अन्य लाइब्रेरी आवश्यक नहीं है—बाकी सब कुछ Aspose.Words पैकेज के भीतर रहता है।

---

## चरण 1 – चेतावनियों को कैप्चर करने के लिए LoadOptions सेट करें  

चेतावनियों को सुनना शुरू करने के लिए आपको एक `LoadOptions` इंस्टेंस बनाना होगा। यह ऑब्जेक्ट लोडर को बताता है कि वह किसी भी समस्या को ट्रैक करे, जैसे लापता फ़ॉन्ट्स।

```java
import com.aspose.words.*;

public class FontWarningDemo {
    public static void main(String[] args) throws Exception {

        // Step 1: Create LoadOptions that will store warning information
        LoadOptions loadOptions = new LoadOptions();

        // ... the rest of the code follows
```

**यह क्यों महत्वपूर्ण है:** `LoadOptions` के बिना लोडर चुपचाप लापता फ़ॉन्ट्स को डिफ़ॉल्ट सिस्टम फ़ॉन्ट से बदल देता है, और आपको कभी नहीं पता चलता कि प्रतिस्थापन हुआ। चेतावनियों को सक्षम करने से आपको पूरी दृश्यता मिलती है।

---

## चरण 2 – LoadOptions का उपयोग करके दस्तावेज़ लोड करें  

अब हम वास्तव में दस्तावेज़ लोड करते हैं। हमने अभी जो `LoadOptions` बनाया था, उसे कंस्ट्रक्टर में पास किया जाता है, इसलिए पार्सिंग के दौरान उत्पन्न कोई भी चेतावनी कैप्चर हो जाती है।

```java
        // Step 2: Load the document that may contain missing fonts
        Document document = new Document("YOUR_DIRECTORY/input.docx", loadOptions);
```

**प्रो टिप:** यदि आप बैच में कई फ़ाइलें प्रोसेस कर रहे हैं, तो अनावश्यक ऑब्जेक्ट निर्माण से बचने के लिए वही `LoadOptions` इंस्टेंस पुनः उपयोग करें।

---

## चरण 3 – कैप्चर की गई चेतावनियों पर इटररेट करें  

Aspose.Words प्रत्येक चेतावनी को एक `WarningInfo` ऑब्जेक्ट के रूप में संग्रहीत करता है। हमें केवल फ़ॉन्ट‑संबंधित चेतावनियों की परवाह है, इसलिए हम `FontSubstitutionWarningInfo` के लिए फ़िल्टर करते हैं।

```java
        // Step 3: Loop through all warnings generated while loading
        for (WarningInfo warning : document.getWarnings()) {
            // Step 3a: Keep only font substitution warnings
            if (warning instanceof FontSubstitutionWarningInfo) {
                FontSubstitutionWarningInfo fontWarning = (FontSubstitutionWarningInfo) warning;

                // Step 4: Output the requested and actual font names
                System.out.println("Requested: " + fontWarning.getRequestedFontName()
                        + " → Substituted: " + fontWarning.getActualFontName());
            }
        }
    }
}
```

**व्याख्या:**  
- `document.getWarnings()` लोड के दौरान हुई हर चेतावनी की सूची लौटाता है।  
- `FontSubstitutionWarningInfo` दो महत्वपूर्ण डेटा रखता है: **अनुरोधित फ़ॉन्ट** (DOCX ने जो माँगा) और वह **वास्तविक फ़ॉन्ट** जिस पर Aspose.Words ने फॉलबैक किया।  
- दोनों को प्रिंट करके आप तुरंत देख सकते हैं कौन से फ़ॉन्ट्स लापता हैं और कौन सा प्रतिस्थापन हुआ।

---

## चरण 4 – (वैकल्पिक) लापता फ़ॉन्ट्स को प्रोग्रामेटिक रूप से संभालें  

चेतावनियों को कैप्चर करना केवल आधा काम है। एक बार जब आप जानते हैं कि फ़ॉन्ट लापता है, तो आप **लापता फ़ॉन्ट्स को संभालना** चाह सकते हैं, जैसे कस्टम प्रतिस्थापन देना या बाद में समीक्षा के लिए समस्या को लॉग करना।

```java
                // Optional: Replace the missing font with a known fallback
                FontSettings fontSettings = new FontSettings();
                fontSettings.getSubstitutionSettings().getTableSubstitution()
                    .addSubstitutes(fontWarning.getRequestedFontName(), "Arial");
                document.setFontSettings(fontSettings);
```

**ऐसा क्यों करें?**  
- मशीनों के बीच सुसंगत रेंडरिंग सुनिश्चित करता है।  
- बाद में उत्पन्न PDFs या इमेजेज़ में अप्रत्याशित लेआउट बदलावों को रोकता है।  

आप चेतावनी विवरण को डेटाबेस में स्टोर कर सकते हैं, कंटेंट टीम को ई‑मेल भेज सकते हैं, या यदि कोई महत्वपूर्ण फ़ॉन्ट लापता है तो प्रोसेस को रोक भी सकते हैं।

---

## पूर्ण कार्यशील उदाहरण  

नीचे पूरा, चलाने योग्य प्रोग्राम दिया गया है। बस `YOUR_DIRECTORY/input.docx` को अपने टेस्ट फ़ाइल के पाथ से बदलें, Aspose.Words JAR को क्लासपाथ में जोड़ें, और चलाएँ।

```java
import com.aspose.words.*;

public class FontWarningDemo {
    public static void main(String[] args) throws Exception {

        // 1️⃣ Create LoadOptions to capture warnings
        LoadOptions loadOptions = new LoadOptions();

        // 2️⃣ Load the document that may contain missing fonts
        Document document = new Document("YOUR_DIRECTORY/input.docx", loadOptions);

        // 3️⃣ Iterate through all warnings
        for (WarningInfo warning : document.getWarnings()) {
            // 3a️⃣ Filter only font substitution warnings
            if (warning instanceof FontSubstitutionWarningInfo) {
                FontSubstitutionWarningInfo fontWarning = (FontSubstitutionWarningInfo) warning;

                // 4️⃣ Display the requested and actual font names
                System.out.println("Requested: " + fontWarning.getRequestedFontName()
                        + " → Substituted: " + fontWarning.getActualFontName());

                // 5️⃣ (Optional) Provide a custom fallback
                FontSettings fontSettings = new FontSettings();
                fontSettings.getSubstitutionSettings().getTableSubstitution()
                    .addSubstitutes(fontWarning.getRequestedFontName(), "Arial");
                document.setFontSettings(fontSettings);
            }
        }

        // 6️⃣ Save the document if you need to see the result with the fallback applied
        document.save("output.docx");
    }
}
```

**अपेक्षित आउटपुट** (जब “Comic Sans MS” लापता हो):

```
Requested: Comic Sans MS → Substituted: Arial
```

वैकल्पिक फ़ॉलबैक कोड चलने के बाद, सहेजा गया `output.docx` जहाँ‑जहाँ “Comic Sans MS” मूल रूप से संदर्भित था, वहाँ **Arial** का उपयोग करेगा।

---

## सामान्य प्रश्न एवं किनारी स्थितियाँ  

| प्रश्न | उत्तर |
|----------|--------|
| *यदि दस्तावेज़ में कई लापता फ़ॉन्ट्स हों तो क्या होगा?* | लूप प्रत्येक लापता फ़ॉन्ट के लिए एक चेतावनी उत्पन्न करेगा। आप उन्हें बैच प्रोसेसिंग के लिए `Map<String, String>` में एकत्र कर सकते हैं। |
| *क्या यह PDFs के लिए भी काम करता है जो दस्तावेज़ से जेनरेट हुए हैं?* | बिल्कुल। फ़ॉन्ट प्रतिस्थापन लोड चरण में ही होता है, इसलिए बाद में किया गया कोई भी एक्सपोर्ट (PDF, HTML, इमेज) हल किए गए फ़ॉन्ट्स का उपयोग करता है। |
| *क्या मैं चेतावनियों को कैप्चर करने के बजाय दबा सकता हूँ?* | हाँ—`loadOptions.setWarningCallback(null);` सेट करें, लेकिन आप लापता फ़ॉन्ट्स की दृश्यता खो देंगे। |
| *क्या चेतावनी सूची सहेजने के बाद साफ़ हो जाती है?* | चेतावनी संग्रह `Document` इंस्टेंस से जुड़ा होता है। `document.save()` कॉल करने के बाद भी सूची अपरिवर्तित रहती है, जब तक आप नया `Document` नहीं बनाते। |
| *DOCX में एम्बेडेड कस्टम फ़ॉन्ट्स के बारे में क्या?* | एम्बेडेड फ़ॉन्ट्स को उपलब्ध माना जाता है; Aspose.Words उन्हें उपयोग करेगा भले ही वे होस्ट सिस्टम पर स्थापित न हों। |

---

## प्रोडक्शन उपयोग के लिए प्रो टिप्स  

- **फ़ॉन्ट सेटिंग्स को कैश करें:** यदि आप सैकड़ों फ़ाइलें प्रोसेस करते हैं, तो एक ही `FontSettings` बनाकर अपने पसंदीदा फ़ॉलबैक सेट करें और पुनः उपयोग करें ताकि ओवरहेड कम हो।  
- **संरचित डेटा लॉग करें:** साधारण `System.out` के बजाय चेतावनियों को JSON लॉग में लिखें—इससे डाउनस्ट्रीम एनालिटिक्स (जैसे “सबसे अधिक लापता फ़ॉन्ट्स”) आसान हो जाता है।  
- **जल्दी वैलिडेट करें:** भारी प्रोसेसिंग से पहले `LoadOptions` के साथ एक त्वरित “ड्राई‑लोड” चलाएँ; यदि महत्वपूर्ण फ़ॉन्ट लापता है तो तुरंत एबॉर्ट करें।  
- **थ्रेड सुरक्षा:** `Document` ऑब्जेक्ट थ्रेड‑सेफ़ नहीं होते। प्रत्येक फ़ाइल की प्रोसेसिंग को अपने थ्रेड में रखें या थ्रेड‑लोकल `LoadOptions` उपयोग करें।  

---

## निष्कर्ष  

अब आप **Aspose.Words for Java में चेतावनियों को कैप्चर करना**, **लापता फ़ॉन्ट्स का पता लगाना**, और **लापता फ़ॉन्ट्स को एक साफ़ फ़ॉलबैक रणनीति के साथ संभालना** जानते हैं। `LoadOptions` और `document.getWarnings()` का उपयोग करके आप फ़ॉन्ट प्रतिस्थापन घटनाओं की पूरी जानकारी प्राप्त कर सकते हैं, जिससे आपके जेनरेटेड दस्तावेज़ सभी वातावरणों में इच्छित रूप से दिखें।  

अगला कदम उठाने के लिए तैयार हैं? इस पैटर्न को **लापता इमेजेज़ का पता लगाने**, **असमर्थित फीचर्स को ट्रैक करने**, या यहाँ तक कि **लापता फ़ॉन्ट्स को आउटपुट फ़ाइल में ऑटो‑एम्बेड करने** के लिए विस्तारित करें। वही चेतावनी‑कैप्चर दृष्टिकोण कई अन्य दस्तावेज़‑प्रोसेसिंग परिदृश्यों में काम करता है, जिससे आपका कोड मजबूत और भविष्य‑सुरक्षित बनता है।  

हैप्पी कोडिंग, और आपके दस्तावेज़ हमेशा सुंदर रूप से रेंडर हों!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}