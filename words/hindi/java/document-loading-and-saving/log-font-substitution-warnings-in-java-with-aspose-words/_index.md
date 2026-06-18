---
category: general
date: 2026-06-17
description: Aspose.Words का उपयोग करके जावा में फ़ॉन्ट प्रतिस्थापन चेतावनियों को
  लॉग करें – दस्तावेज़ लोड के दौरान गायब फ़ॉन्ट को पकड़ें और अपने आउटपुट को सुसंगत
  रखें।
draft: false
keywords:
- log font substitution warnings
- Aspose.Words Java
- font substitution
- warning callback
- LoadOptions
- document loading
language: hi
og_description: Aspose.Words के साथ जावा में फ़ॉन्ट प्रतिस्थापन चेतावनियों को लॉग
  करें। दस्तावेज़ लोड करते समय गायब फ़ॉन्ट अलर्ट को पकड़ना सीखें और अपने PDF को शुद्ध
  रखें।
og_title: जावा में फ़ॉन्ट प्रतिस्थापन चेतावनियों को लॉग करें – पूर्ण मार्गदर्शिका
schemas:
- author: Aspose
  dateModified: '2026-06-17'
  description: Log font substitution warnings in Java using Aspose.Words – capture
    missing fonts during document load and keep your output consistent.
  headline: Log Font Substitution Warnings in Java with Aspose.Words
  type: TechArticle
- description: Log font substitution warnings in Java using Aspose.Words – capture
    missing fonts during document load and keep your output consistent.
  name: Log Font Substitution Warnings in Java with Aspose.Words
  steps:
  - name: Prerequisites
    text: '- Java 8 or newer (the code works with Java 11+ as well). - Aspose.Words
      for Java library (version 23.10 or later is recommended). - A sample `.docx`
      that references a font not installed on your machine (e.g., `MissingFont.docx`).'
  - name: Logging to a File Instead of the Console
    text: 'If you prefer a persistent log, replace the `System.out.println` call with
      a `FileWriter`:'
  - name: Capturing Multiple Documents in a Loop
    text: 'When processing a folder of documents, you can reuse the same callback:'
  - name: Dealing with Embedded Fonts
    text: 'Aspose.Words can embed missing fonts if you enable it:'
  type: HowTo
tags:
- Java
- Aspose.Words
- Document Processing
title: Aspose.Words के साथ जावा में फ़ॉन्ट प्रतिस्थापन चेतावनियों को लॉग करें
url: /hi/java/document-loading-and-saving/log-font-substitution-warnings-in-java-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# जावा में फ़ॉन्ट प्रतिस्थापन चेतावनियों को लॉग करें – पूर्ण गाइड

क्या आपने कभी सोचा है कि **फ़ॉन्ट प्रतिस्थापन चेतावनियों** को कैसे लॉग किया जाए जब कोई Word दस्तावेज़ सर्वर पर उपलब्ध नहीं होने वाले फ़ॉन्ट को खींचता है? आप अकेले नहीं हैं जो गायब फ़ॉन्ट्स के कारण चुपचाप बदलने की समस्या से जूझ रहे हैं। अच्छी खबर? Aspose.Words for Java आपको दस्तावेज़ लोड होते ही उन प्रतिस्थापनों को पकड़ने का साफ़ तरीका देता है।

इस ट्यूटोरियल में हम एक व्यावहारिक उदाहरण के माध्यम से दिखाएंगे कि कैसे एक चेतावनी कॉलबैक रजिस्टर किया जाए, फ़ॉन्ट‑सबस्टीट्यूशन अलर्ट्स को फ़िल्टर किया जाए, और उन्हें कंसोल (या आपके पसंदीदा लॉगर) में लिखा जाए। अंत तक आपके पास एक पुन: उपयोग योग्य स्निपेट होगा जिसे आप किसी भी जावा प्रोजेक्ट में डाल सकते हैं जो **Aspose.Words Java** का उपयोग करता है।

## आप क्या सीखेंगे

- **LoadOptions** को कॉन्फ़िगर करके चेतावनियों को कैप्चर करना।
- एक **IWarningCallback** को लागू करना जो केवल **फ़ॉन्ट प्रतिस्थापन** इवेंट्स पर प्रतिक्रिया देता है।
- दस्तावेज़ को सुरक्षित रूप से लोड करना जबकि गायब फ़ॉन्ट्स का स्पष्ट ऑडिट ट्रेल रखना।
- समाधान को फ़ाइल‑आधारित लॉग या मॉनिटरिंग सिस्टम में विस्तारित करने के टिप्स।

### पूर्वापेक्षाएँ

- Java 8 या नया (कोड Java 11+ के साथ भी काम करता है)।
- Aspose.Words for Java लाइब्रेरी (संस्करण 23.10 या बाद का अनुशंसित)।
- एक नमूना `.docx` जो आपके मशीन पर इंस्टॉल नहीं किए गए फ़ॉन्ट को रेफ़र करता है (जैसे, `MissingFont.docx`)।

कोई अतिरिक्त फ्रेमवर्क आवश्यक नहीं—सिर्फ साधारण जावा और Aspose.JARs।

---

## चरण 1: Aspose.Words Java के लिए LoadOptions कॉन्फ़िगर करें

किसी भी चेतावनी को इंटरसेप्ट करने से पहले, आपको एक **LoadOptions** इंस्टेंस चाहिए। यह ऑब्जेक्ट Aspose.Words को बताता है कि आने वाली फ़ाइल को पार्स करते समय कैसे व्यवहार करना है।

```java
// Step 1: Create LoadOptions to enable warning capture
LoadOptions loadOptions = new LoadOptions();
```

यह कदम क्यों महत्वपूर्ण है? बिना `LoadOptions` ऑब्जेक्ट के, लाइब्रेरी चुपचाप गायब फ़ॉन्ट्स को प्रतिस्थापित कर देती है और आप कभी भी इसका ट्रेस नहीं देखते। स्पष्ट रूप से एक बनाकर, आप एक कस्टम **warning callback** की राह खोलते हैं जो ठीक वही लॉग कर सकता है जिसकी आपको ज़रूरत है।

> **Pro tip:** यदि आप बैच में कई दस्तावेज़ लोड कर रहे हैं, तो अनावश्यक ऑब्जेक्ट निर्माण से बचने के लिए एक ही `LoadOptions` इंस्टेंस को पुन: उपयोग करें।

---

## चरण 2: फ़ॉन्ट प्रतिस्थापन के लिए एक Warning Callback लागू करें

Aspose.Words `IWarningCallback` इंटरफ़ेस के साथ आता है। इसे लागू करने से आप तय कर सकते हैं कि इंजन `WarningInfo` उठाने पर क्या करना है। हमारे मामले में, हम केवल `WarningType.FONT_SUBSTITUTION` पर प्रतिक्रिया देना चाहते हैं।

```java
// Step 2: Register a warning callback that logs only font‑substitution warnings
loadOptions.setWarningCallback(new IWarningCallback() {
    @Override
    public void warning(WarningInfo info) {
        // Filter for font‑substitution warnings only
        if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
            // Simple console output – replace with a logger if you prefer
            System.out.println("Font substitution: " + info.getMessage());
        }
    }
});
```

ध्यान देने योग्य कुछ बातें:

1. **फ़िल्टरिंग** – `if` स्टेटमेंट सुनिश्चित करता है कि हम असंबंधित चेतावनियों (जैसे लेआउट समस्याएँ) को अनदेखा कर दें और लॉग को साफ़ रखें।
2. **थ्रेड सुरक्षा** – कॉलबैक उसी थ्रेड पर चलता है जो दस्तावेज़ लोड करता है, इसलिए साधारण कंसोल आउटपुट के लिए अतिरिक्त सिंक्रोनाइज़ेशन की ज़रूरत नहीं है। यदि आप साझा लॉगर में लिखते हैं, तो सुनिश्चित करें कि वह थ्रेड‑सेफ़ है।
3. **विस्तारशीलता** – फ़ाइल में लिखना चाहते हैं? `System.out.println` को `java.util.logging.Logger` या किसी थर्ड‑पार्टी लॉगिंग फ्रेमवर्क से बदलें।

---

## चरण 3: कॉन्फ़िगर किए गए विकल्पों के साथ दस्तावेज़ लोड करें

अब जबकि कॉलबैक सेट है, अपना Word फ़ाइल लोड करें। जैसे ही Aspose.Words दस्तावेज़ को पार्स करता है, कोई भी गायब फ़ॉन्ट ऊपर परिभाषित कॉलबैक को ट्रिगर करेगा।

```java
// Step 3: Load the document with the warning‑aware LoadOptions
Document doc = new Document("YOUR_DIRECTORY/MissingFont.docx", loadOptions);
```

यदि स्रोत फ़ाइल में ऐसा फ़ॉन्ट रेफ़र किया गया है जो इंस्टॉल नहीं है, तो आपको इस तरह का आउटपुट दिखेगा:

```
Font substitution: Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
```

यह लाइन वही **log font substitution warnings** है जिसकी आप तलाश कर रहे थे। अब आप इस पर कार्रवाई कर सकते हैं—शायद उपयोगकर्ता को अलर्ट करें, फॉलबैक स्टाइलशीट पर स्विच करें, या सिर्फ अनुपालन के लिए रिकॉर्ड रखें।

---

## चरण 4: सामान्य प्रोसेसिंग जारी रखें

लोड करने के बाद, दस्तावेज़ किसी भी अन्य `Document` ऑब्जेक्ट की तरह व्यवहार करता है। सेक्शन जांचें, टेक्स्ट एक्सट्रैक्ट करें, या PDF में कन्वर्ट करें। चेतावनी लॉगिंग लोड स्टेप के दौरान स्वचालित रूप से हो जाता है, इसलिए अतिरिक्त कोड की ज़रूरत नहीं।

```java
// Example: Print the number of sections – just to prove the doc is usable
System.out.println("Document has " + doc.getSections().getCount() + " sections.");
```

कंसोल अब फ़ॉन्ट‑सबस्टीट्यूशन चेतावनी (यदि कोई हो) **और** सेक्शन काउंट दोनों दिखाएगा, यह पुष्टि करते हुए कि दस्तावेज़ पूरी तरह कार्यात्मक है।

---

## उन्नत टिप्स और एज केस

### कंसोल के बजाय फ़ाइल में लॉग करना

यदि आप स्थायी लॉग चाहते हैं, तो `System.out.println` को `FileWriter` से बदलें:

```java
private static final String LOG_PATH = "logs/font_substitutions.txt";

loadOptions.setWarningCallback(new IWarningCallback() {
    @Override
    public void warning(WarningInfo info) {
        if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
            try (FileWriter fw = new FileWriter(LOG_PATH, true)) {
                fw.write("Font substitution: " + info.getMessage() + System.lineSeparator());
            } catch (IOException e) {
                e.printStackTrace();
            }
        }
    }
});
```

प्रोडक्शन कोड में `IOException` को सही ढंग से हैंडल करना याद रखें।

### लूप में कई दस्तावेज़ प्रोसेस करना

फ़ोल्डर के दस्तावेज़ों को प्रोसेस करते समय, आप वही कॉलबैक पुन: उपयोग कर सकते हैं:

```java
File[] files = new File("input").listFiles((dir, name) -> name.endsWith(".docx"));
for (File f : files) {
    Document d = new Document(f.getAbsolutePath(), loadOptions);
    // Additional processing...
}
```

चूंकि कॉलबैक `loadOptions` से जुड़ा है, प्रत्येक इटरेशन स्वचालित रूप से किसी भी फ़ॉन्ट‑सबस्टीट्यूशन इवेंट को लॉग करेगा।

### एम्बेडेड फ़ॉन्ट्स से निपटना

Aspose.Words को एम्बेडेड फ़ॉन्ट्स सक्षम करने पर भी उपयोग किया जा सकता है:

```java
loadOptions.setLoadFormat(LoadFormat.DOCX);
loadOptions.setEnableFontSubstitution(true); // default is true
```

भले ही एम्बेडिंग चालू हो, चेतावनी कॉलबैक अभी भी फायर होता है, जिससे आपको यह पता चलता है कि क्या प्रतिस्थापित किया गया।

---

## पूर्ण कार्यशील उदाहरण

नीचे पूरा, तैयार‑चलाने‑योग्य प्रोग्राम दिया गया है। इसे `FontSubstitutionDiagnostics.java` नामक क्लास में कॉपी करें, फ़ाइल पाथ समायोजित करें, और चलाएँ।

```java
import com.aspose.words.*;

import java.io.FileWriter;
import java.io.IOException;

/**
 * Demonstrates how to log font substitution warnings using Aspose.Words for Java.
 */
public class FontSubstitutionDiagnostics {

    // Optional: path to a persistent log file
    private static final String LOG_FILE = "font_substitution_log.txt";

    public static void main(String[] args) throws Exception {
        // 1️⃣ Create LoadOptions to capture warnings
        LoadOptions loadOptions = new LoadOptions();

        // 2️⃣ Register a warning callback that logs only font‑substitution warnings
        loadOptions.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) {
                if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                    String message = "Font substitution: " + info.getMessage();
                    // Log to console
                    System.out.println(message);
                    // Also append to a file (optional)
                    try (FileWriter fw = new FileWriter(LOG_FILE, true)) {
                        fw.write(message + System.lineSeparator());
                    } catch (IOException e) {
                        // In a real app, use a proper logging framework
                        e.printStackTrace();
                    }
                }
            }
        });

        // 3️⃣ Load the document with the configured LoadOptions
        Document doc = new Document("YOUR_DIRECTORY/MissingFont.docx", loadOptions);

        // 4️⃣ Continue normal processing – e.g., print section count
        System.out.println("Document has " + doc.getSections().getCount() + " sections.");
    }
}
```

**अपेक्षित आउटपुट** (मान लेते हैं स्रोत डॉक में एक गायब फ़ॉन्ट है):

```
Font substitution: Font 'Times New Roman' was not found. Substituted with 'Arial'.
Document has 3 sections.
```

कंसोल और `font_substitution_log.txt` दोनों में चेतावनी होगी, जिससे आपको एक विश्वसनीय ऑडिट ट्रेल मिल जाएगा।

---

## निष्कर्ष

हमने आपको दिखाया कि कैसे **जावा में फ़ॉन्ट प्रतिस्थापन चेतावनियों** को Aspose.Words का उपयोग करके लॉग किया जाए। `LoadOptions` को कॉन्फ़िगर करके, `IWarningCallback` को वायर करके, और दस्तावेज़ लोड करके, आप उन सभी गायब‑फ़ॉन्ट इवेंट्स पर पूरी दृश्यता प्राप्त करते हैं जो अन्यथा अनदेखी रह सकते थे। अब आप:

- चेतावनियों को केंद्रीय लॉगिंग सर्विस में रूट कर सकते हैं।
- क्वालिटी‑कंट्रोल पाइपलाइन के लिए अलर्ट ट्रिगर कर सकते हैं।
- इस तकनीक को अन्य **document loading** रणनीतियों, जैसे PDF कन्वर्ज़न या मेल‑मर्ज, के साथ संयोजित कर सकते हैं।

बिना झिझक प्रयोग करें—कंसोल लॉगर को SLF4J से बदलें, टाइमस्टैम्प जोड़ें, या अलर्ट को मॉनिटरिंग डैशबोर्ड पर पुश करें। मूल पैटर्न वही रहता है, और अब आपके पास किसी भी जावा‑आधारित दस्तावेज़ वर्कफ़्लो में मजबूत फ़ॉन्ट‑हैंडलिंग के लिए एक ठोस आधार है।

क्या आपके पास कोई ट्विस्ट है जिसे आप साझा करना चाहते हैं? शायद आपने इसे Spring Boot या क्लाउड फ़ंक्शन के साथ इंटीग्रेट किया है। नीचे कमेंट करें, और बातचीत जारी रखें। Happy coding!

## अगला क्या सीखें?

निम्नलिखित ट्यूटोरियल्स उन विषयों को कवर करते हैं जो इस गाइड में दिखाए गए तकनीकों पर आधारित हैं। प्रत्येक संसाधन में पूर्ण कार्यशील कोड उदाहरण और चरण‑दर‑चरण व्याख्याएँ शामिल हैं, जिससे आप अतिरिक्त API फीचर्स में महारत हासिल कर सकें और अपने प्रोजेक्ट्स में वैकल्पिक इम्प्लीमेंटेशन एप्रोचेज़ का अन्वेषण कर सकें।

- [Capture Font Substitution Warnings in Java with Aspose.Words – Complete Guide](/words/english/java/document-loading-and-saving/capture-font-substitution-warnings-in-java-with-aspose-words/)
- [Using Document Options and Settings in Aspose.Words for Java](/words/english/java/document-manipulation/using-document-options-and-settings/)
- [Enable Font Substitution Warnings in Aspose.Words – Complete Guide](/words/english/net/working-with-fonts/enable-font-substitution-warnings-in-aspose-words-complete-g/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}