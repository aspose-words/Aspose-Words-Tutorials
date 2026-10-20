---
category: general
date: 2026-03-25
description: जावा में वर्ड दस्तावेज़ लोड करने और गायब फ़ॉन्ट्स को संभालने के लिए वार्निंग
  कॉलबैक ट्यूटोरियल। कस्टम वार्निंग कॉलबैक के साथ लोड वर्ड डॉक्यूमेंट जावा एप्रोच
  सीखें।
draft: false
keywords:
- warning callback tutorial
- load word document java
- handle missing fonts
language: hi
og_description: वॉर्निंग कॉलबैक ट्यूटोरियल दिखाता है कि जावा में वर्ड दस्तावेज़ को
  कैसे लोड किया जाए और कस्टम वॉर्निंग कॉलबैक के साथ लापता फ़ॉन्ट्स को कैसे संभाला
  जाए।
og_title: चेतावनी कॉलबैक ट्यूटोरियल – जावा में वर्ड दस्तावेज़ लोड करें
tags:
- java
- aspose-words
- document-processing
title: चेतावनी कॉलबैक ट्यूटोरियल – जावा में वर्ड दस्तावेज़ लोड करें
url: /hi/java/document-loading-and-saving/warning-callback-tutorial-load-word-document-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# चेतावनी कॉलबैक ट्यूटोरियल – जावा में वर्ड डॉक्यूमेंट लोड करें

क्या आपने कभी जावा में **.docx** फ़ाइल लोड करने की कोशिश की है और फिर फ़ॉन्ट की कमी के बारे में एक रहस्यमय चेतावनी देखी है? आप अकेले नहीं हैं। इस **warning callback tutorial** में, हम एक पूर्ण, तैयार‑चलाने योग्य उदाहरण के माध्यम से चलेंगे जो न केवल वर्ड डॉक्यूमेंट लोड करता है बल्कि फ़ॉन्ट‑सब्स्टिट्यूशन चेतावनियों को भी पकड़ता है ताकि आप प्रोग्रामेटिकली उनका उत्तर दे सकें।

यदि आप सोच रहे हैं कि **load word document java** शैली में फ़ॉन्ट की कमी की चेतावनियों (*handle missing fonts*) पर नजर रखते हुए कैसे लोड करें, तो आप सही जगह पर हैं। इस गाइड के अंत तक आपके पास एक पुन: उपयोग योग्य पैटर्न होगा जिसे आप किसी भी जावा प्रोजेक्ट में डाल सकते हैं जो Aspose.Words (या समान लाइब्रेरी) का उपयोग करता है और आप समझेंगे कि फ़ॉन्ट समस्याओं के बारे में सूचित रहने के लिए चेतावनी कॉलबैक सबसे साफ़ तरीका क्यों है।

---

## आप क्या सीखेंगे

- जावा में चेतावनी कॉलबैक को कॉन्फ़िगर करने के लिए आवश्यक सटीक कोड।  
- कैसे कॉलबैक फ़ॉन्ट‑सब्स्टिट्यूशन चेतावनियों को अन्य संदेश प्रकारों से अलग करता है।  
- गुम फ़ॉन्ट्स को लॉग करने, दबाने या तुरंत बदलने के तरीके।  
- अनुपलब्ध फ़ॉन्ट्स का संदर्भ देने वाले वर्ड डॉक्यूमेंट लोड करते समय सामान्य समस्याओं को हल करने के लिए टिप्स।

### आवश्यकताएँ

- आपके मशीन पर Java 17 (या नया) स्थापित हो।  
- Maven या Gradle जैसे बिल्ड टूल (हम Maven स्निपेट्स दिखाएंगे)।  
- Aspose.Words for Java लाइब्रेरी (टेस्टिंग के लिए मुफ्त ट्रायल काम करता है)।  
- एक नमूना **input.docx** जिसमें ऐसा फ़ॉन्ट उपयोग किया गया है जो आपके पास स्थापित नहीं है (चेतावनी ट्रिगर करने के लिए)।

> **Pro tip:** यदि आपके पास अभी तक Aspose.Words नहीं है, तो नीचे दिखाया गया डिपेंडेंसी जोड़ें और Maven को इसे आपके लिए डाउनलोड करने दें—कोई मैन्युअल JAR जुग्लिंग आवश्यक नहीं।

---

## चरण 1: अपना प्रोजेक्ट सेट अप करें और आवश्यक क्लासेस इम्पोर्ट करें

सबसे पहले, हमें सही Maven कोऑर्डिनेट्स चाहिए। इसे अपने `pom.xml` में जोड़ें:

```xml
<!-- Maven dependency for Aspose.Words -->
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version> <!-- Use the latest stable version -->
</dependency>
```

अब एक नई जावा क्लास बनाएं, उदाहरण के लिए `WordLoader.java`, और आवश्यक टाइप्स इम्पोर्ट करें:

```java
import com.aspose.words.Document;
import com.aspose.words.LoadOptions;
import com.aspose.words.IWarningCallback;
import com.aspose.words.WarningInfo;
import com.aspose.words.WarningType;
```

ये इम्पोर्ट्स हमें `LoadOptions`, `IWarningCallback` इंटरफ़ेस, और `WarningInfo` ऑब्जेक्ट तक पहुँच देते हैं जो हमें बताता है कि *क्या* गलत हुआ।

---

## चरण 2: चेतावनी कॉलबैक परिभाषित करें – ट्यूटोरियल का दिल

यह **warning callback tutorial** फ़ॉन्ट‑सब्स्टिट्यूशन इवेंट्स को इंटरसेप्ट करने पर निर्भर करता है। यहाँ एक संक्षिप्त लेकिन पूरी तरह कार्यात्मक इम्प्लीमेंटेशन है:

```java
// Step 2: Create a warning callback that prints font substitution messages
class FontSubstitutionCallback implements IWarningCallback {
    @Override
    public void warning(WarningInfo info) {
        // Only react to font‑substitution warnings
        if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
            System.out.println("⚠️ Font substituted: " + info.getDescription());
        }
    }
}
```

**यह क्यों महत्वपूर्ण है:**  
- `IWarningCallback` *हर* बार तब बुलाया जाता है जब Aspose.Words ऐसी स्थिति का सामना करता है जिसे वह उल्लेखनीय मानता है।  
- `info.getWarningType()` की जाँच करके, हम असंबंधित चेतावनियों (जैसे डिप्रिकेटेड फीचर्स) को फ़िल्टर करते हैं और केवल **handle missing fonts** परिदृश्य पर ध्यान केंद्रित करते हैं।  
- विवरण को लॉग करने से आपको मूल फ़ॉन्ट नाम और उपयोग किए गए फॉलबैक मिलते हैं, जो डाउनस्ट्रीम लेआउट जांचों के लिए महत्वपूर्ण है।

---

## चरण 3: कॉलबैक को LoadOptions में जोड़ें

अब हम अपने कॉलबैक को `LoadOptions` इंस्टेंस से जोड़ते हैं। यही वह बिंदु है जहाँ **load word document java** प्रक्रिया हमारे कस्टम हैंडलर से अवगत होती है।

```java
// Step 3: Prepare LoadOptions with the custom warning callback
LoadOptions loadOptions = new LoadOptions();
loadOptions.setWarningCallback(new FontSubstitutionCallback());
```

आप यहाँ अन्य विकल्प भी सेट कर सकते हैं—जैसे एन्क्रिप्टेड फ़ाइलों के लिए `setPassword` या यदि आपको किसी विशेष फ़ॉर्मेट को मजबूर करना है तो `setLoadFormat`। कॉलबैक इन सेटिंग्स से स्वतंत्र रूप से काम करता है।

---

## चरण 4: डॉक्यूमेंट लोड करें और कॉलबैक को कार्रवाई में देखें

सब कुछ जोड़ने के बाद, डॉक्यूमेंट लोड करना एक ही लाइन है:

```java
// Step 4: Load the .docx file using the configured LoadOptions
Document document = new Document("YOUR_DIRECTORY/input.docx", loadOptions);
```

जब फ़ाइल में कोई गुम फ़ॉन्ट रेफ़रेंस होता है, तो आपको इस प्रकार का आउटपुट दिखेगा:

```
⚠️ Font substituted: Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
```

यदि डॉक्यूमेंट के सभी फ़ॉन्ट मौजूद हैं, तो कॉलबैक चुप रहेगा—बिल्कुल वही जो आप **handle missing fonts** को सुगमता से संभालते समय अपेक्षित करेंगे।

---

## चरण 5: परिणाम सत्यापित करें और वैकल्पिक पोस्ट‑प्रोसेसिंग

लोड करने के बाद, आप यह पुष्टि करना चाह सकते हैं कि डॉक्यूमेंट उपयोग योग्य है, संभवतः इसे PDF में बदलकर या सादा टेक्स्ट निकालकर:

```java
// Optional: Save as PDF to verify visual fidelity
document.save("output.pdf");

// Or extract plain text to a console for quick inspection
System.out.println(document.getText());
```

दोनों क्रियाएँ पहले हुए सब्स्टिट्यूशन का सम्मान करेंगी, इसलिए आप अंतिम आउटपुट पर गुम फ़ॉन्ट के वास्तविक प्रभाव को देख सकते हैं।

---

## किनारे के मामलों और सामान्य समस्याएँ

| Situation | What Happens | How to Handle |
|-----------|--------------|---------------|
| **एकाधिक गुम फ़ॉन्ट्स** | कॉलबैक प्रत्येक गुम फ़ॉन्ट के लिए एक बार चलता है। | कॉलबैक को हल्का रखें; `warning()` के अंदर भारी I/O से बचें। |
| **कस्टम फ़ॉन्ट डायरेक्टरी** | यदि फ़ॉन्ट डिफ़ॉल्ट सर्च पाथ में नहीं है तो भी Aspose.Words सब्स्टिट्यूशन रिपोर्ट करता है। | `loadOptions.setFontSettings(FontSettings.getDefaultInstance())` का उपयोग करें और `FontSettings.getDefaultInstance().setFontsFolder("path", true)` के माध्यम से अपना फ़ॉन्ट फ़ोल्डर जोड़ें। |
| **परफ़ॉर्मेंस‑क्रिटिकल एप्लिकेशन** | अत्यधिक लॉगिंग बैच प्रोसेसिंग को धीमा कर सकती है। | `WARN` स्तर वाले लॉगर पर स्विच करें और प्रोडक्शन में कंसोल प्रिंटिंग को निष्क्रिय करें। |
| **गैर‑फ़ॉन्ट चेतावनियाँ** | कॉलबैक कई प्रकार की चेतावनियाँ प्राप्त करता है (जैसे `DEPRECATED_FEATURE`)। | जैसा दिखाया गया है, `WarningType` द्वारा फ़िल्टर करें; आप डायग्नोस्टिक रिपोर्ट के लिए अन्य चेतावनियों को भी एकत्र कर सकते हैं। |

---

## पूर्ण कार्यशील उदाहरण

नीचे पूर्ण, स्वतंत्र प्रोग्राम है जिसे आप अपने IDE में कॉपी‑पेस्ट कर सकते हैं। इसमें सभी इम्पोर्ट्स, कॉलबैक क्लास, और एक सरल `main` मेथड शामिल है।

```java
import com.aspose.words.*;

public class WordLoader {
    // Custom warning callback – only cares about font substitution
    static class FontSubstitutionCallback implements IWarningCallback {
        @Override
        public void warning(WarningInfo info) {
            if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                System.out.println("⚠️ Font substituted: " + info.getDescription());
            }
        }
    }

    public static void main(String[] args) {
        try {
            // 1️⃣ Prepare LoadOptions with our callback
            LoadOptions loadOptions = new LoadOptions();
            loadOptions.setWarningCallback(new FontSubstitutionCallback());

            // 2️⃣ Load the document – this triggers the callback if needed
            Document doc = new Document("YOUR_DIRECTORY/input.docx", loadOptions);

            // 3️⃣ Optional verification – save as PDF and print text
            doc.save("output.pdf");                     // visual check
            System.out.println("--- Extracted Text ---");
            System.out.println(doc.getText());          // quick sanity check
        } catch (Exception e) {
            // In real apps, use proper logging instead of printStackTrace
            e.printStackTrace();
        }
    }
}
```

**अपेक्षित कंसोल आउटपुट** (जब गुम फ़ॉन्ट पता चलता है):

```
⚠️ Font substituted: Font 'Times New Roman' was not found. Substituted with 'Liberation Serif'.
--- Extracted Text ---
[Document text appears here...]
```

यदि कोई गुम फ़ॉन्ट नहीं है, तो आप केवल निकाले गए टेक्स्ट हेडर देखेंगे।

---

## दृश्य अवलोकन

![warning callback tutorial आरेख जो LoadOptions → IWarningCallback → कंसोल आउटपुट के प्रवाह को दर्शाता है](/images/warning-callback-tutorial.png "warning callback tutorial आरेख")

*यह आरेख दर्शाता है कि कैसे चेतावनी कॉलबैक डॉक्यूमेंट लोड प्रक्रिया के दौरान फ़ॉन्ट‑सब्स्टिट्यूशन इवेंट्स को इंटरसेप्ट करता है।*

---

## पुनरावलोकन और अगले कदम

हमने अभी एक **warning callback tutorial** पूरा किया है जो आपको दिखाता है कि **load word document java** शैली में **handle missing fonts** को सुगमता से कैसे किया जाए। मुख्य बिंदु हैं:

1. `IWarningCallback` को इम्प्लीमेंट करें और `WarningType.FONT_SUBSTITUTION` के लिए फ़िल्टर करें।  
2. डॉक्यूमेंट लोड करने से पहले कॉलबैक को `LoadOptions` से जोड़ें।  
3. सेव या टेक्स्ट निकालकर परिणाम की पुष्टि करें, और वैकल्पिक रूप से फ़ॉन्ट‑सर्च पाथ को फाइन‑ट्यून करें।

अब आप निम्नलिखित का अन्वेषण कर सकते हैं:

- **कस्टम फ़ॉन्ट सब्स्टिट्यूशन**: प्रोग्रामेटिकली गुम फ़ॉन्ट को अपनी पसंद के फ़ॉन्ट से बदलें।  
- **बैच प्रोसेसिंग**: डॉक्यूमेंट्स के फ़ोल्डर पर लूप चलाएँ, सभी सब्स्टिट्यूशन चेतावनियों को CSV रिपोर्ट में एकत्र करें।  
- **लॉगिंग फ्रेमवर्क्स के साथ इंटीग्रेशन**: प्रोडक्शन‑ग्रेड डायग्नोस्टिक्स के लिए चेतावनियों को Log4j या SLF4J में पाइप करें।

इन विचारों को आज़माएँ, और आप जल्दी ही देखेंगे कि वास्तविक दुनिया के डॉक्यूमेंट पाइपलाइनों में एक सही जगह पर रखी गई चेतावनी कॉलबैक कितनी शक्तिशाली हो सकती है।

---

### प्रश्न हैं?

नीचे टिप्पणी छोड़ने या GitHub पर मुझे पिंग करने में संकोच न करें। कोडिंग का आनंद लें, और आपके डॉक्यूमेंट हमेशा उन फ़ॉन्ट्स के साथ रेंडर हों जो आप अपेक्षा करते हैं!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}