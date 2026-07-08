---
category: general
date: 2026-06-30
description: Aspose.Words Java में चेतावनियों के लिए LoadOptions को कॉन्फ़िगर करें।
  फ़ॉन्ट प्रतिस्थापन और अन्य लोड‑ऑप्शन चेतावनियों के लिए एक चेतावनी कॉलबैक सेट करना
  सीखें।
draft: false
keywords:
- configure loadoptions for warnings
- Aspose.Words font substitution
- Java warning callback
- document loading options
- handle font warnings
language: hi
og_description: Aspose.Words Java में चेतावनियों के लिए LoadOptions को कॉन्फ़िगर करें।
  यह गाइड दिखाता है कि कैसे फ़ॉन्ट‑सब्स्टिट्यूशन अलर्ट को एक चेतावनी कॉलबैक के साथ
  कैप्चर किया जाए।
og_title: चेतावनियों के लिए LoadOptions कॉन्फ़िगर करें – जावा ट्यूटोरियल
schemas:
- author: Aspose
  dateModified: '2026-06-30'
  description: Configure LoadOptions for warnings in Aspose.Words Java. Learn to set
    up a warning callback for font substitution and other load‑options warnings.
  headline: Configure LoadOptions for Warnings – Complete Java Guide
  type: TechArticle
tags:
- aspose-words
- java
- warnings
- font-substitution
title: चेतावनियों के लिए LoadOptions कॉन्फ़िगर करें – पूर्ण जावा गाइड
url: /hi/java/document-loading-and-saving/configure-loadoptions-for-warnings-complete-java-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# चेतावनियों के लिए LoadOptions को कॉन्फ़िगर करें – पूर्ण जावा गाइड

क्या आपको कभी Aspose.Words for Java के साथ Word दस्तावेज़ खोलते समय **चेतावनियों के लिए LoadOptions को कॉन्फ़िगर** करने की ज़रूरत पड़ी है? आप अकेले नहीं हैं। कई डेवलपर्स को यह समस्या आती है कि जब कोई फ़ॉन्ट गायब होता है तो वह चुपचाप बदल दिया जाता है, जिससे अंतिम PDF का स्वरूप ब्रांड से मेल नहीं खाता। अच्छी खबर? अपने `LoadOptions` में **Java warning callback** जोड़कर आप फ़ॉन्ट‑सब्स्टिट्यूशन की हर चेतावनी को तुरंत पकड़ सकते हैं।

इस ट्यूटोरियल में हम एक व्यावहारिक उदाहरण के माध्यम से चलेंगे, जो न केवल कॉलबैक सेटअप दिखाता है बल्कि *क्यों* प्रत्येक भाग महत्वपूर्ण है, यह भी समझाता है। अंत तक आप **फ़ॉन्ट चेतावनियों** को संभालने, उन्हें लॉग करने या यहाँ तक कि फ़ॉन्ट को ऑन‑द‑फ़्लाई बदलने में सक्षम हो जाएंगे—बिना किसी अनुमान के।

## आप क्या सीखेंगे

- एक पूरी तरह चलने वाला जावा प्रोग्राम जो हर फ़ॉन्ट‑सब्स्टिट्यूशन चेतावनी को प्रिंट करता है।  
- **Aspose.Words फ़ॉन्ट सब्स्टिट्यूशन** मैकेनिज़्म की समझ।  
- बड़े प्रोजेक्ट्स के लिए चेतावनी हैंडलिंग को कस्टमाइज़ करने के टिप्स।  
- **डॉक्यूमेंट लोडिंग विकल्पों** में अंतर्दृष्टि और कब उन्हें ट्यून करना चाहिए।

> **पूर्वापेक्षा:** Java 8+ और Aspose.Words for Java लाइब्रेरी (संस्करण 23.9 या बाद का)। अन्य कोई बाहरी निर्भरताएँ आवश्यक नहीं हैं।

---

## चरण 1: चेतावनियों के लिए LoadOptions को कॉन्फ़िगर करें

पहले आपको एक `LoadOptions` इंस्टेंस चाहिए जो यह जानता हो कि उसे चेतावनियाँ रिपोर्ट करनी हैं। `LoadOptions` को उस टूलबॉक्स की तरह सोचें जिसे आप Aspose.Words को फ़ाइल खोलने से पहले देते हैं।

```java
// Step 1: Create LoadOptions and attach a warning callback.
LoadOptions loadOptions = new LoadOptions();
loadOptions.setWarningCallback(new IWarningCallback() {
    @Override
    public void warning(WarningInfo info) {
        // Only react to font‑substitution warnings.
        if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
            System.out.println("Font substitution detected: " + info.getDescription());
        }
    }
});
```

**यह क्यों महत्वपूर्ण है:**  
`LoadOptions` नियंत्रित करता है कि लाइब्रेरी दस्तावेज़ को कैसे पढ़ती है। एक `IWarningCallback` असाइन करके आप Aspose.Words को बताते हैं कि जब भी उसे कोई महत्वपूर्ण चीज़ मिले—जैसे गायब फ़ॉन्ट—तो आपका कोड चलाया जाए। बिना इस सेटिंग के, लाइब्रेरी चुपचाप फ़ॉन्ट बदल देगी और आपको पता नहीं चलेगा।

> **उपयोगी सुझाव:** यदि आप *सभी* चेतावनियों को पकड़ना चाहते हैं, तो `if` चेक को हटा दें। अभी हम फ़ॉन्ट समस्याओं पर ध्यान दे रहे हैं क्योंकि वे लेआउट में सबसे आम आश्चर्य होते हैं।

---

## चरण 2: कॉन्फ़िगर किए गए विकल्पों का उपयोग करके दस्तावेज़ लोड करें

अब जब कॉलबैक तैयार है, तो वही `LoadOptions` के साथ अपना `.docx` (या कोई भी समर्थित फ़ॉर्मेट) लोड करें। यही वह जगह है जहाँ **डॉक्यूमेंट लोडिंग विकल्प** वास्तव में प्रभावी होते हैं।

```java
// Step 2: Load the document with the warning‑aware LoadOptions.
Document document = new Document("YOUR_DIRECTORY/input.docx", loadOptions);
```

**परदे के पीछे:**  
जब Aspose.Words `input.docx` को पार्स करता है, तो वह फ़ॉन्ट टेबल स्कैन करता है। यदि दस्तावेज़ में कोई फ़ॉन्ट होस्ट मशीन पर इंस्टॉल नहीं है, तो इंजन `FONT_SUBSTITUTION` चेतावनी उठाता है, जो तुरंत हमारे द्वारा पहले परिभाषित कॉलबैक को ट्रिगर करता है।

---

## चरण 3: दस्तावेज़ सहेजें – चेतावनियाँ पहले ही प्रिंट हो चुकी हैं

सहेजना सीधा है, लेकिन यह वह क्षण है जहाँ आप सत्यापित कर सकते हैं कि कॉलबैक सही ढंग से फायर हुआ। सभी चेतावनियाँ लोड चरण के दौरान प्रिंट हो जाती हैं, इसलिए सेव ऑपरेशन केवल सफ़ाई है।

```java
// Step 3: Save the document. Any warnings were already printed in Step 1.
document.save("YOUR_DIRECTORY/output.docx");
```

**अपेक्षित कंसोल आउटपुट:**  

```
Font substitution detected: Font 'Calibri' is not installed. Substituted with 'Arial'.
Font substitution detected: Font 'Times New Roman' is not installed. Substituted with 'Liberation Serif'.
```

यदि कुछ नहीं दिखता, तो या तो दस्तावेज़ में केवल स्थापित फ़ॉन्ट ही थे, या कॉलबैक सही से जुड़ा नहीं था—चरण 1 को दोबारा जाँचें।

---

## चरण 4: कॉलबैक को **फ़ॉन्ट चेतावनियों** को सहजता से संभालने के लिए विस्तारित करें

डेमो के लिए कंसोल पर प्रिंट करना ठीक है, लेकिन प्रोडक्शन कोड अक्सर अधिक उन्नत हैंडलिंग चाहता है: फ़ाइल में लॉग करना, अलर्ट भेजना, या प्रोग्रामेटिक रूप से फ़ॉन्ट बदलना।

```java
loadOptions.setWarningCallback(new IWarningCallback() {
    @Override
    public void warning(WarningInfo info) {
        if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
            // Log to a file (simple example)
            try (FileWriter fw = new FileWriter("font-warnings.log", true)) {
                fw.write("WARN: " + info.getDescription() + System.lineSeparator());
            } catch (IOException e) {
                e.printStackTrace();
            }
            // Optionally replace the missing font with a fallback.
            FontSettings.getDefaultInstance().setSubstitutionSettings(
                new FontSubstitutionSettings() {{
                    getTableSubstitution().addSubstitutes("Calibri", "Arial");
                }}
            );
        }
    }
});
```

**आप इसे क्यों करेंगे:**  
एक लॉग फ़ाइल आपको पोस्ट‑मॉर्टेम अंतर्दृष्टि देती है, विशेषकर जब आप दस्तावेज़ों की बैच प्रोसेसिंग कर रहे हों। वैकल्पिक सब्स्टिट्यूशन ब्लॉक दिखाता है कि कैसे **चेतावनियों के लिए LoadOptions को कॉन्फ़िगर** किया जाए *और* कॉर्पोरेट फ़ॉन्ट नीति लागू की जाए।

---

## उन्नत: अन्य **Aspose.Words फ़ॉन्ट सब्स्टिट्यूशन** परिदृश्यों को नियंत्रित करना

चेतावनी कॉलबैक केवल गायब फ़ॉन्ट तक सीमित नहीं है। आप भी पकड़ सकते हैं:

- **असमर्थित यूनिकोड अक्षर** (`WarningType.UNSUPPORTED_CHAR`)।  
- **जटिल स्क्रिप्ट समस्याएँ** (`WarningType.COMPLEX_SCRIPT`)।

सिर्फ `if` स्टेटमेंट को विस्तारित करें:

```java
if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
    // handle fonts
} else if (info.getWarningType() == WarningType.UNSUPPORTED_CHAR) {
    System.out.println("Unsupported character: " + info.getDescription());
}
```

यह आपके समाधान को बहुभाषी दस्तावेज़ों के लिए मजबूत बनाता है, जो वैश्विक एप्लिकेशनों में आम एज केस है।

---

## पूर्ण कार्यशील उदाहरण

नीचे पूरा, तैयार‑चलाने‑योग्य प्रोग्राम दिया गया है। इसे किसी भी जावा IDE में पेस्ट करें, `YOUR_DIRECTORY` प्लेसहोल्डर को बदलें, और *Run* दबाएँ।

```java
import com.aspose.words.*;

import java.io.FileWriter;
import java.io.IOException;

public class FontSubstitutionDemo {
    public static void main(String[] args) throws Exception {

        // Step 1: Configure LoadOptions for warnings.
        LoadOptions loadOptions = new LoadOptions();
        loadOptions.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) {
                if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                    System.out.println("Font substitution: " + info.getDescription());

                    // Optional: Log to a file.
                    try (FileWriter fw = new FileWriter("font-warnings.log", true)) {
                        fw.write("WARN: " + info.getDescription() + System.lineSeparator());
                    } catch (IOException e) {
                        e.printStackTrace();
                    }

                    // Optional: Force a specific fallback font.
                    FontSettings.getDefaultInstance().setSubstitutionSettings(
                        new FontSubstitutionSettings() {{
                            getTableSubstitution().addSubstitutes("Calibri", "Arial");
                        }}
                    );
                }
            }
        });

        // Step 2: Load the document using the configured LoadOptions.
        Document document = new Document("YOUR_DIRECTORY/input.docx", loadOptions);

        // Step 3: Save the document. Warnings have already been printed.
        document.save("YOUR_DIRECTORY/output.docx");
    }
}
```

### अपेक्षित परिणाम

- कंसोल पर कोई भी फ़ॉन्ट‑सब्स्टिट्यूशन चेतावनी प्रिंट होगी।  
- यदि आप वैकल्पिक लॉगिंग रखी है, तो `font-warnings.log` में टाइम‑स्टैम्पेड सूची होगी।  
- `output.docx` सब्स्टिट्यूटेड फ़ॉन्ट के साथ सहेजा जाएगा, जो आपके द्वारा परिभाषित फॉलबैक से मेल खाता है।

---

## सामान्य बाधाएँ और उन्हें कैसे टालें

| समस्या | क्यों होता है | समाधान |
|---------|----------------|-----|
| **कोई चेतावनी नहीं दिखती** | कॉलबैक जुड़ा नहीं था, या दस्तावेज़ में केवल स्थापित फ़ॉन्ट ही उपयोग किए गए हैं। | सुनिश्चित करें कि `loadOptions.setWarningCallback(...)` को दस्तावेज़ लोड करने से *पहले* कॉल किया गया है। |
| `input.docx` पर **FileNotFoundException** | पथ गलत है या फ़ाइल प्रोजेक्ट में शामिल नहीं है। | एक पूर्ण पथ उपयोग करें या फ़ाइल को प्रोजेक्ट के resources फ़ोल्डर में रखें। |
| हजारों दस्तावेज़ प्रोसेस करते समय **प्रदर्शन में गिरावट** | हर चेतावनी पर डिस्क पर अत्यधिक लॉगिंग। | लॉग को बफ़र करें और बैच में लिखें, या केवल महत्वपूर्ण चेतावनियों तक लॉगिंग सीमित रखें। |
| **अनपेक्षित फ़ॉन्ट सब्स्टिट्यूशन** बावजूद फ़ॉलबैक | सब्स्टिट्यूशन टेबल पर्याप्त जल्दी लागू नहीं हुई। | सब्स्टिट्यूशन सेटिंग्स को दस्तावेज़ लोड करने से **पहले** सेट करें, या `FontSettings.setSubstitutionSettings` को ग्लोबली उपयोग करें। |

---

## अगले कदम

अब जब आप **चेतावनियों के लिए LoadOptions को कॉन्फ़िगर** करने में निपुण हो गए हैं, तो इन आगे के विषयों पर विचार करें:

- **बैच प्रोसेसिंग**: दस्तावेज़ों की डायरेक्टरी पर लूप चलाएँ, सभी फ़ॉन्ट चेतावनियों को एक ही रिपोर्ट में एकत्रित करें।  
- **कस्टम फ़ॉन्ट प्रोवाइडर**: स्थानीय OS के बजाय नेटवर्क शेयर या एम्बेडेड रिसोर्सेज़ से फ़ॉन्ट लोड करें।  
- **Log4j** जैसे लॉगिंग फ्रेमवर्क के साथ इंटीग्रेशन करके एंटरप्राइज़‑ग्रेड ट्रेसबिलिटी प्राप्त करें।  
- अन्य **डॉक्यूमेंट लोडिंग विकल्प** जैसे `LoadFormat` डिटेक्शन या पासवर्ड‑हैंडलिंग (संरक्षित फ़ाइलों के लिए) का अन्वेषण करें।

इन सभी में वही पैटर्न दोहराया जाता है—`LoadOptions` ऑब्जेक्ट बनाएं, उपयुक्त कॉलबैक संलग्न करें, और Aspose.Words को भारी काम करने दें।

---

## निष्कर्ष

हमने Aspose.Words for Java में **चेतावनियों के लिए LoadOptions को कॉन्फ़िगर** करने, **Java warning कॉलबैक** सेट करने, और इस जानकारी का उपयोग करके **फ़ॉन्ट चेतावनियों** को बुद्धिमानी से संभालने का गहरा अध्ययन किया। कोड संक्षिप्त है, अवधारणाएँ स्पष्ट हैं, और अब आपके पास चेतावनियों को अन्य परिदृश्यों जैसे असमर्थित अक्षर या जटिल स्क्रिप्ट्स में विस्तारित करने की ठोस नींव है।

इसे आज़माएँ, सब्स्टिट्यूशन टेबल को अपने ब्रांड फ़ॉन्ट के अनुसार ट्यून करें, और उन चुपचाप फ़ॉन्ट स्वैप्स को गायब होते देखें। कोडिंग का आनंद लें!

![LoadOptions को चेतावनियों के लिए कॉन्फ़िगर करने, दस्तावेज़ लोड करने, फ़ॉन्ट सब्स्टिट्यूशन इवेंट्स को कैप्चर करने और आउटपुट सहेजने की प्रवाह चित्र](configure-loadoptions-for-warnings-diagram.png "LoadOptions को चेतावनियों के लिए कॉन्फ़िगर करने का प्रवाह")

## आगे आप क्या सीखें?

नीचे दिए गए ट्यूटोरियल्स इस गाइड में प्रदर्शित तकनीकों पर आधारित हैं और अतिरिक्त API फीचर्स एवं वैकल्पिक कार्यान्वयन दृष्टिकोणों को समझने में मदद करेंगे।

- [जावा में Aspose.Words के साथ फ़ॉन्ट सब्स्टिट्यूशन चेतावनियों को कैप्चर करें – पूर्ण गाइड](/words/english/java/document-loading-and-saving/capture-font-substitution-warnings-in-java-with-aspose-words/)
- [Aspose.Words for Java में LoadOptions कैसे सेट करें](/words/english/java/document-loading-and-saving/using-load-options/)
- [Aspose.Words for Java में RTF लोड विकल्प कॉन्फ़िगर करके RTF दस्तावेज़ कैसे लोड करें](/words/english/java/document-loading-and-saving/configuring-rtf-load-options/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}