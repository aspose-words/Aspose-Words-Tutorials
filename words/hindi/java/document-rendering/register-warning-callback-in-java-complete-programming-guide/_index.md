---
category: general
date: 2026-05-23
description: जावा में चेतावनी कॉलबैक पंजीकृत करें ताकि गायब फ़ॉन्ट्स का पता लगाया
  जा सके और फ़ॉन्ट प्रतिस्थापन को संभाला जा सके। पूर्ण उदाहरण के साथ चरण‑दर‑चरण सीखें।
draft: false
keywords:
- register warning callback
- detect missing fonts
- Java font handling
- Aspose.Words warning callback
- font substitution detection
language: hi
og_description: जावा में चेतावनी कॉलबैक पंजीकृत करें ताकि गायब फ़ॉन्ट्स का पता लगाया
  जा सके। यह ट्यूटोरियल कोड, व्याख्याएँ और सर्वोत्तम प्रथाओं के साथ एक पूर्ण समाधान
  दिखाता है।
og_title: जावा में चेतावनी कॉलबैक पंजीकृत करें – पूर्ण मार्गदर्शिका
schemas:
- author: Aspose
  dateModified: '2026-05-23'
  description: Register warning callback in Java to detect missing fonts and handle
    font substitutions. Learn step‑by‑step with a full example.
  headline: Register Warning Callback in Java – Complete Programming Guide
  type: TechArticle
tags:
- Java
- Aspose.Words
- FontSettings
- DocumentProcessing
title: जावा में वार्निंग कॉलबैक रजिस्टर करें – पूर्ण प्रोग्रामिंग गाइड
url: /hi/java/document-rendering/register-warning-callback-in-java-complete-programming-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Java में Warning Callback पंजीकृत करें – पूर्ण प्रोग्रामिंग गाइड

क्या आपको कभी **register warning callback** Java में करना पड़ा लेकिन फ़ॉन्ट की कमी को पकड़ने का तरीका नहीं पता था? आप अकेले नहीं हैं। जब दस्तावेज़ कस्टम टाइपफ़ेस पर निर्भर होते हैं, तो चुप‑चाप फ़ॉन्ट प्रतिस्थापन लेआउट को बिगाड़ सकता है, और इन्हें पहचानने का भरोसेमंद तरीका केवल चेतावनियों को सुनना है। इस गाइड में हम एक व्यावहारिक समाधान पर चलेंगे जो न केवल **warning callback पंजीकृत करता है** बल्कि **missing fonts** को तब ही पहचान लेता है जब वे चुप‑चाप आपके आउटपुट को बिगाड़ने वाले हों।

वास्तव में—Aspose.Words for Java फ़ॉन्ट प्रबंधन के लिए एक साफ़ API देता है, फिर भी कई डेवलपर warning callback चरण को छोड़ देते हैं और अंत में ऐसे PDFs बनाते हैं जो मूल Word फ़ाइल से बिल्कुल अलग दिखते हैं। इस ट्यूटोरियल के अंत तक आपके पास चलाने योग्य स्निपेट होगा, प्रत्येक पंक्ति का महत्व समझेंगे, और अधिक जटिल परिदृश्यों के लिए इस दृष्टिकोण को कैसे विस्तारित करें, जानेंगे।

## आप क्या सीखेंगे

आने वाले कुछ सेक्शन में हम कवर करेंगे:

* `LoadOptions` बनाना और कस्टम फ़ॉन्ट हैंडलिंग सक्षम करना।  
* `FONT_SUBSTITUTION` इवेंट को पकड़ने के लिए **warning callback पंजीकृत** करना।  
* **missing fonts** का पता लगाना और डिबगिंग के लिए उपयोगी जानकारी लॉग करना।  
* एक पूर्ण, चलाने योग्य Java उदाहरण जो आप आज ही अपने IDE में पेस्ट कर सकते हैं।

Aspose.Words के अलावा कोई बाहरी लाइब्रेरी आवश्यक नहीं है, और कोड Java 8+ और Aspose.Words 23.9 (या बाद के संस्करण) के साथ काम करता है। यदि आपके पास पहले से ही `.docx` फ़ाइलें लोड करने वाला प्रोजेक्ट है, तो आपको केवल कुछ पंक्तियों को जोड़ना होगा—कोई बड़े‑पैमाने पर रीफ़ैक्टर नहीं।

## आवश्यकताएँ

* Java Development Kit (JDK) 8 या नया।  
* Aspose.Words for Java (आधिकारिक साइट से डाउनलोड करें या Maven डिपेंडेंसी जोड़ें)।  
* वह डायरेक्टरी जहाँ आपका Word दस्तावेज़ स्थित है, उसकी पहुँच।  
* Java लैम्ब्डा या अनाम क्लास की बेसिक समझ (स्पष्टीकरण के लिए हम अनाम क्लास उपयोग करेंगे)।

यदि इनमें से कोई भी परिचित नहीं लग रहा, तो घबराएँ नहीं—प्रत्येक चरण को साधारण अंग्रेज़ी में समझाया गया है, और कोड कमेंट्स में गैप भर दिया गया है।

---

## चरण 1: Load Options बनाएं और कस्टम फ़ॉन्ट हैंडलिंग सक्षम करें

फ़ॉन्ट‑संबंधी चेतावनियों को सुनने से पहले हमें एक `LoadOptions` इंस्टेंस चाहिए जो Aspose.Words को हमारे अपने `FontSettings` उपयोग करने को बताता है। `LoadOptions` को आप दस्तावेज़ लोडर को देने वाले “सेटिंग्स बैग” के रूप में सोच सकते हैं।

```java
// Step 1: Create load options and enable custom font handling
LoadOptions loadOptions = new LoadOptions();               // Holds loading configuration
loadOptions.setFontSettings(new FontSettings());           // Attach a fresh FontSettings object
```

**यह क्यों महत्वपूर्ण है:**  
`FontSettings` वह द्वार है जिसके माध्यम से लाइब्रेरी फ़ॉन्ट‑सेटिंग्स—जैसे सर्च पाथ, प्रतिस्थापन नियम, और सबसे महत्वपूर्ण, warning callbacks—को नियंत्रित करती है। एक समर्पित `FontSettings` ऑब्जेक्ट बनाकर आप यह तय कर सकते हैं कि मिसिंग फ़ॉन्ट को कैसे संभाला जाए, बजाय लाइब्रेरी के डिफ़ॉल्ट व्यवहार पर भरोसा करने के।

> **Pro tip:** यदि आपका एप्लिकेशन पहले से ही एक साझा `FontSettings` (जैसे PDF कन्वर्ज़न के लिए) प्रदान करता है, तो इसे यहाँ पुनः उपयोग करें ताकि पूरे पाइपलाइन में फ़ॉन्ट रिज़ॉल्यूशन सुसंगत रहे।

---

## चरण 2: Missing Fonts का पता लगाने के लिए Warning Callback पंजीकृत करें

अब ट्यूटोरियल का मुख्य भाग—हम **warning callback पंजीकृत** करते हैं उस `FontSettings` पर जिसे हमने अभी बनाया था। यह callback दस्तावेज़ लोडिंग के दौरान उत्पन्न प्रत्येक चेतावनी के लिए एक `WarningInfo` ऑब्जेक्ट प्राप्त करता है।

```java
// Step 2: Register a warning callback to be notified of font substitutions
loadOptions.getFontSettings().setWarningCallback(new IWarningCallback() {
    @Override
    public void warning(WarningInfo info) {
        // Filter only font substitution warnings
        if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
            // This is where we **detect missing fonts**
            System.out.println("Substituted: " + info.getDescription());
        }
    }
});
```

**लॉजिक की व्याख्या:**

* `setWarningCallback` हमारे कस्टम लिस्नर को अटैच करता है।  
* `warning(WarningInfo info)` के अंदर हम `info.getWarningType()` की जाँच करते हैं।  
* जब टाइप `WarningType.FONT_SUBSTITUTION` के बराबर होता है, तो लाइब्रेरी बता रही होती है कि वह मूल फ़ॉन्ट नहीं मिला और उसे किसी अन्य फ़ॉन्ट से बदलना पड़ा।  
* `info.getDescription()` में एक मानव‑पठनीय संदेश होता है, जैसे *“Font 'MyCustomFont' not found, substituted with 'Arial'.”*  

इस विवरण को प्रिंट करके हम **missing fonts** को लोड चरण में ही पहचान लेते हैं, जिससे आप लॉग, अलर्ट या यहाँ तक कि ऑपरेशन को रोक भी सकते हैं यदि प्रतिस्थापन अस्वीकार्य हो।

> **Exception पकड़ने की बजाय यह क्यों?**  
> मिसिंग फ़ॉन्ट आमतौर पर एक्सेप्शन नहीं फेंकते; वे चेतावनियाँ उत्पन्न करते हैं। बिना callback के ये चेतावनियाँ नज़रअंदाज़ हो जाती हैं और आपको कभी पता नहीं चलता कि दस्तावेज़ की दृश्य गुणवत्ता प्रभावित हुई है।

### वैकल्पिक: लैम्ब्डा का उपयोग (Java 8+)

यदि आप अधिक संक्षिप्त सिंटैक्स पसंद करते हैं, तो वही callback लैम्ब्डा के साथ लिखा जा सकता है:

```java
loadOptions.getFontSettings().setWarningCallback(info -> {
    if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
        System.out.println("Substituted: " + info.getDescription());
    }
});
```

दोनों तरीकों से वही लक्ष्य प्राप्त होता है—अपनी कोडबेस के अनुसार जो भी शैली उपयुक्त हो, चुनें।

---

## चरण 3: कॉन्फ़िगर किए गए Options के साथ दस्तावेज़ लोड करें

Callback सेट होने के बाद अंतिम चरण है दस्तावेज़ को लोड करना। `Document` कन्स्ट्रक्टर पाथ और हमने तैयार किया हुआ `LoadOptions` दोनों लेता है।

```java
// Step 3: Load the document using the configured options
Document document = new Document("YOUR_DIRECTORY/input.docx", loadOptions);
```

**आंतरिक रूप से क्या होता है?**  
इस कॉल के दौरान Aspose.Words `.docx` फ़ाइल को पार्स करता है, प्रत्येक संदर्भित फ़ॉन्ट को रिज़ॉल्व करता है, और किसी भी मिसिंग टाइपफ़ेस के लिए हमारे warning callback को ट्रिगर करता है। यदि सब कुछ उपलब्ध है, तो कोई कंसोल आउटपुट नहीं दिखेगा; अन्यथा आपको इस तरह की लाइनों मिलेंगी:

```
Substituted: Font 'OpenSans-Regular' not found, substituted with 'Times New Roman'.
Substituted: Font 'CustomIconFont' not found, substituted with 'Arial'.
```

यह आउटपुट स्पष्ट प्रमाण है कि हमने **warning callback पंजीकृत** किया है और **missing fonts** का पता लगा रहे हैं।

---

## पूर्ण कार्यशील उदाहरण

नीचे पूरा, स्व-निहित Java प्रोग्राम दिया गया है जिसे आप `Main.java` फ़ाइल में कॉपी‑पेस्ट करके चला सकते हैं। सुनिश्चित करें कि Aspose.Words JAR आपके क्लासपाथ में हो।

```java
import com.aspose.words.*;

public class Main {
    public static void main(String[] args) {
        try {
            // 1️⃣ Create LoadOptions and enable custom font handling
            LoadOptions loadOptions = new LoadOptions();
            loadOptions.setFontSettings(new FontSettings());

            // 2️⃣ Register warning callback to detect missing fonts
            loadOptions.getFontSettings().setWarningCallback(new IWarningCallback() {
                @Override
                public void warning(WarningInfo info) {
                    if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                        System.out.println("Substituted: " + info.getDescription());
                    }
                }
            });

            // 3️⃣ Load the document using the configured options
            Document doc = new Document("YOUR_DIRECTORY/input.docx", loadOptions);

            // Optional: Save as PDF to verify visual fidelity
            doc.save("output.pdf");
            System.out.println("Document loaded and saved successfully.");
        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}
```

**अपेक्षित आउटपुट** (जब फ़ॉन्ट गायब हों):

```
Substituted: Font 'MyCustomFont' not found, substituted with 'Arial'.
Document loaded and saved successfully.
```

यदि सभी फ़ॉन्ट उपलब्ध हों, तो आपको केवल सफलता संदेश ही दिखेगा।

---

## एज केस और सामान्य जाल

| स्थिति | ध्यान देने योग्य बात | सुझाया गया समाधान |
|-----------|-------------------|---------------|
| **एकाधिक मिसिंग फ़ॉन्ट** | Callback कई बार फायर हो सकता है, जिससे लॉग भर सकते हैं। | संदेशों को एग्रीगेट करें या बाद में विश्लेषण के लिए फ़ाइल में लिखें। |
| **परफ़ॉर्मेंस प्रभाव** | अत्यधिक लॉगिंग बड़े बैच लोड्स को धीमा कर सकती है। | चेतावनियों को गंभीरता के आधार पर फ़िल्टर करें या प्रोडक्शन में कंसोल आउटपुट बंद रखें। |
| **कस्टम फ़ॉन्ट डायरेक्टरी** | `FontSettings` डिफ़ॉल्ट रूप से केवल सिस्टम फ़ॉन्ट देखता है। | `fontSettings.setFontsFolder("path/to/custom/fonts", true);` को callback पंजीकृत करने से पहले कॉल करें। |
| **चुप‑चाप प्रतिस्थापन** | कुछ फ़ॉन्ट समान माने जाने पर बिना चेतावनी के बदल सकते हैं। | `fontSettings.setSubstitutionSettings(new FontSubstitutionSettings());` सेट करें और प्रतिस्थापन नियमों को फाइन‑ट्यून करें। |

इन परिदृश्यों की पूर्वानुमान करके आप अपने एप्लिकेशन को मजबूत और लॉग को अर्थपूर्ण रख सकते हैं।

---

## समाधान का विस्तार

अब जब आप **warning callback पंजीकृत** करना और **missing fonts** का पता लगाना जानते हैं, तो आप चाहेंगे:

* **लोडिंग रोकना** जब कोई महत्वपूर्ण फ़ॉन्ट गायब हो (callback के अंदर एक्सेप्शन थ्रो करें)।  
* **मिसिंग फ़ॉन्ट नाम** को `Set<String>` में इकट्ठा करके दस्तावेज़ लोड होने के बाद सारांश रिपोर्ट बनाएं।  
* **मॉनिटरिंग सिस्टम** (जैसे Slack या Azure Monitor) के साथ इंटीग्रेट करें—callback से अलर्ट भेजें।  

इन सभी एक्सटेंशन का आधार वही callback पैटर्न है जिसे हमने प्रदर्शित किया है।

---

## निष्कर्ष

हमने एक पूर्ण, प्रोडक्शन‑रेडी उदाहरण के माध्यम से दिखाया कि कैसे **Java में warning callback पंजीकृत** किया जाए, जिससे **missing fonts** को दस्तावेज़ लोड होते ही पहचान सकें। मुख्य बिंदु:

* कस्टम `FontSettings` के साथ `LoadOptions` बनाएं।  
* `IWarningCallback` अटैच करें जो `FONT_SUBSTITUTION` चेतावनियों को फ़िल्टर करे।  
* उन विकल्पों के साथ दस्तावेज़ लोड करें और किसी भी मिसिंग‑फ़ॉन्ट इवेंट पर प्रतिक्रिया दें।

इस ज्ञान के साथ आप अपने दस्तावेज़‑प्रोसेसिंग पाइपलाइन को सुरक्षित रख सकते हैं, दृश्य सटीकता सुनिश्चित कर सकते हैं, और अंतिम उपयोगकर्ता को स्पष्ट डायग्नोस्टिक प्रदान कर सकते हैं।  

अगला कदम तैयार है? फ़ॉन्ट फ़ोल्डर जोड़ें, विभिन्न प्रतिस्थापन नीतियों के साथ प्रयोग करें, या callback को अपने मौजूदा लॉगिंग फ्रेमवर्क में जोड़ें। संभावनाएँ उतनी ही विस्तृत हैं जितनी आपकी फ़ॉन्ट लाइब्रेरी।

Happy coding, and may your PDFs always render exactly as intended!

## संबंधित ट्यूटोरियल

- [Capture Font Substitution Warnings in Java with Aspose.Words – Complete Guide](/words/english/java/document-loading-and-saving/capture-font-substitution-warnings-in-java-with-aspose-words/)
- [Warning Callback In Word Document](/words/english/net/programming-with-loadoptions/warning-callback/)
- [How to Load DOCX and Detect Missing Fonts – Complete C# Guide](/words/english/net/working-with-fonts/how-to-load-docx-and-detect-missing-fonts-complete-c-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}