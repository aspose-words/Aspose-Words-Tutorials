---
category: general
date: 2026-06-27
description: Aspose.Words का उपयोग करके जावा में फ़ॉन्ट प्रतिस्थापन चेतावनियों को
  कैसे पकड़ें, सीखें। यह चरण‑दर‑चरण ट्यूटोरियल चेतावनी कॉलबैक और LoadOptions के उपयोग
  को भी कवर करता है।
draft: false
keywords:
- capture font substitution warnings
- Aspose.Words warning callback
- Java LoadOptions example
- font substitution handling
- document processing with Aspose
language: hi
og_description: Aspose.Words के साथ जावा में फ़ॉन्ट प्रतिस्थापन चेतावनियों को कैप्चर
  करें। इस गाइड का पालन करके चेतावनी कॉलबैक सेट करें, LoadOptions का उपयोग करें, और
  गायब फ़ॉन्ट्स को संभालें।
og_title: जावा में फ़ॉन्ट प्रतिस्थापन चेतावनियों को कैप्चर करें – Aspose.Words ट्यूटोरियल
schemas:
- author: Aspose
  dateModified: '2026-06-27'
  description: Learn how to capture font substitution warnings in Java using Aspose.Words.
    This step‑by‑step tutorial also covers warning callbacks and LoadOptions usage.
  headline: Capture Font Substitution Warnings in Java with Aspose.Words – Complete
    Guide
  type: TechArticle
- questions:
  - answer: Yes. The warning callback is format‑agnostic; it fires for any document
      type that Aspose.Words loads (DOC, DOCX, RTF, HTML, etc.). The only difference
      is the set of warnings that may appear.
    question: Does this work with PDF or other formats?
  - answer: Absolutely. Inside the `warning` method, inspect `info.getWarningType()`
      for other enum values such as `WarningType.IMAGE_RESOLUTION`. Then handle them
      accordingly.
    question: Can I capture other warning types, like *image resolution* warnings?
  - answer: 'Store each `info.getDescription()` in a `List<String>` inside the callback.
      After loading, you’ll have a collection you can log, send to a monitoring service,
      or use to trigger a font‑download routine. ## Conclusion You now know **how
      to capture font substitution warnings** in Java using Aspose.Word'
    question: What if I need the list of substituted fonts after the document loads?
  type: FAQPage
tags:
- Aspose.Words
- Java
- Document Conversion
title: Aspose.Words के साथ जावा में फ़ॉन्ट प्रतिस्थापन चेतावनियों को कैप्चर करें –
  पूर्ण गाइड
url: /hi/java/document-loading-and-saving/capture-font-substitution-warnings-in-java-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Java में Aspose.Words के साथ फ़ॉन्ट प्रतिस्थापन चेतावनियों को कैप्चर करें – पूर्ण गाइड

क्या आपको कभी **फ़ॉन्ट प्रतिस्थापन चेतावनियों** को कैप्चर करने की ज़रूरत पड़ी है जबकि आप एक DOCX लोड कर रहे हैं जिसमें विदेशी टाइपफ़ेस होते हैं? आप अकेले नहीं हैं। कई वास्तविक‑दुनिया प्रोजेक्ट्स में—जैसे स्वचालित रिपोर्ट जनरेटर्स या बैच दस्तावेज़ कनवर्टर्स—गायब फ़ॉन्ट्स चुपचाप प्रतिस्थापन को ट्रिगर करते हैं जो लेआउट की सटीकता को बिगाड़ सकते हैं।

सौभाग्य से, Aspose.Words आपको इन चेतावनियों को सुनने का साफ़ तरीका देता है। इस ट्यूटोरियल में हम **LoadOptions** को कॉन्फ़िगर करने, **Aspose.Words warning callback** को जोड़ने, और प्रत्येक *फ़ॉन्ट प्रतिस्थापन* नोटिस को कंसोल पर प्रिंट करने की प्रक्रिया को चरण‑दर‑चरण देखेंगे। अंत तक आप ठीक‑ठीक जान पाएँगे कि कब फ़ॉन्ट बदल दिया गया और प्रोग्रामेटिक रूप से कैसे प्रतिक्रिया दें।

> **आपको क्या मिलेगा:** एक पूरी तरह चलने योग्य Java स्निपेट, प्रत्येक भाग के *क्यों* का स्पष्टीकरण, और कस्टम फ़ॉन्ट डायरेक्टरी जैसे एज केस को संभालने के टिप्स।

## आवश्यकताएँ और आपको क्या चाहिए

- Java 8 या उससे नया स्थापित हो (कोड Java 11+ के साथ भी काम करता है)।
- सबसे नया Aspose.Words for Java JAR (आधिकारिक साइट या Maven Central से डाउनलोड करें)।
- एक DOCX फ़ाइल जिसमें ऐसे फ़ॉन्ट्स का उल्लेख हो जो आपके मशीन पर स्थापित नहीं हैं (उदाहरण के लिए, *font‑rich.docx* जिसे आप Aspose डेमो सेट में पा सकते हैं)।
- एक उपयुक्त IDE (IntelliJ IDEA, Eclipse, या यहाँ तक कि Java एक्सटेंशन के साथ VS Code)।

Aspose.Words के अलावा कोई बाहरी लाइब्रेरी आवश्यक नहीं है, और उदाहरण एक साधारण `main` मेथड में चलता है।

## चरण 1: LoadOptions सेट करें – कस्टम लोडिंग के लिए प्रवेश बिंदु

`LoadOptions` Aspose.Words का कॉन्फ़िगरेशन बैग है जो लाइब्रेरी को बताता है *कैसे* दस्तावेज़ पढ़ना है। डिफ़ॉल्ट रूप से यह गायब फ़ॉन्ट्स को चुपचाप प्रतिस्थापित करता है, लेकिन आप एक warning callback के साथ इस व्यवहार को बदल सकते हैं।

```java
import com.aspose.words.*;

public class FontWarningDemo {
    public static void main(String[] args) throws Exception {

        // Step 1: Create LoadOptions to customize loading behavior
        LoadOptions loadOptions = new LoadOptions();
```

**क्यों महत्वपूर्ण है:** बिना `LoadOptions` के, दस्तावेज़ चुपचाप लोड होता है और आपको गायब फ़ॉन्ट्स की जानकारी नहीं मिलती। एक इंस्टेंस बनाकर आप warning सिस्टम के लिए एक हुक प्राप्त करते हैं।

## चरण 2: एक Warning Callback परिभाषित करें ताकि *फ़ॉन्ट प्रतिस्थापन चेतावनियों* को कैप्चर किया जा सके

Aspose.Words `IWarningCallback` इंटरफ़ेस के माध्यम से चेतावनी इवेंट्स भेजता है। इसे इनलाइन (या अलग क्लास में) इम्प्लीमेंट करें और `WarningType.FONT_SUBstitution` के लिए फ़िल्टर करें।

```java
        // Step 2: Define a warning callback to capture font substitution warnings
        loadOptions.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) {
                // Only react to font substitution warnings
                if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                    System.out.println("Font substituted: " + info.getDescription());
                }
            }
        });
```

**व्याख्या:**  
- `info.getWarningType()` आपको चेतावनी की श्रेणी बताता है।  
- `WarningType.FONT_SUBSTITUTION` वह enum मान है जिसमें हमें रुचि है।  
- `info.getDescription()` में मानव‑पठनीय संदेश होता है, उदाहरण के लिए *“Font 'Comic Sans MS' not found, substituted with 'Arial'.”*  

विवरण को प्रिंट करके आप **फ़ॉन्ट प्रतिस्थापन चेतावनियों** को वास्तविक समय में कैप्चर करते हैं।

## चरण 3: कॉन्फ़िगर किए गए LoadOptions का उपयोग करके दस्तावेज़ लोड करें

अब जब callback सेट हो गया है, अपना DOCX लोड करें। पार्सिंग के दौरान warning callback स्वतः चलती है।

```java
        // Step 3: Load the document using the configured LoadOptions
        Document document = new Document("YOUR_DIRECTORY/font-rich.docx", loadOptions);
```

`YOUR_DIRECTORY` को अपने टेस्ट फ़ाइल के वास्तविक पाथ से बदलें। जब `Document` कंस्ट्रक्टर चलता है, कोई भी गायब फ़ॉन्ट पहले परिभाषित callback को ट्रिगर करता है, और आप कंसोल पर प्रतिस्थापन संदेश देखेंगे।

## चरण 4: लोड किए गए दस्तावेज़ की जाँच करें (वैकल्पिक लेकिन उपयोगी)

लोडिंग के बाद, आप दस्तावेज़ की अखंडता—पेज काउंट, टेक्स्ट एक्सट्रैक्शन आदि—की पुष्टि करना चाह सकते हैं। यह चरण चेतावनियों को कैप्चर करने के लिए आवश्यक नहीं है, लेकिन प्रतिस्थापन के प्रभाव को देखने में मदद करता है।

```java
        // Optional: Output basic document info
        System.out.println("Document loaded successfully.");
        System.out.println("Page count: " + document.getPageCount());
```

यदि फ़ॉन्ट प्रतिस्थापित हुआ है, तो लेआउट थोड़ा बदल सकता है; पेज काउंट की जाँच से ऐसे बदलाव स्पष्ट हो सकते हैं।

## चरण 5: उन्नत – प्रोग्रामेटिक रूप से प्रतिस्थापित फ़ॉन्ट्स को संभालना

कभी‑कभी आप केवल चेतावनी को लॉग नहीं करना चाहते—आपको fallback फ़ॉन्ट एम्बेड करना या स्टाइल समायोजित करना पड़ सकता है। नीचे एक तेज़ पैटर्न दिया गया है जिसे आप अपना सकते हैं।

```java
        // Advanced: Register a fallback font folder to reduce substitutions
        FontSettings fontSettings = new FontSettings();
        // Point to a folder that contains the missing fonts
        fontSettings.setFontsFolder("YOUR_DIRECTORY/custom-fonts", true);
        loadOptions.setFontSettings(fontSettings);
```

Aspose.Words को उस फ़ोल्डर की ओर इंगित करके जिसमें मूल फ़ॉन्ट्स हों, आप पूरी तरह से प्रतिस्थापन को *रोक* सकते हैं। यदि फ़ोल्डर मौजूद नहीं है, तो warning callback अभी भी इवेंट को कैप्चर करता है, जिससे आपके पास एक fallback रणनीति रहती है।

## पूर्ण कार्यशील उदाहरण

सब कुछ मिलाकर, यहाँ पूरा, तैयार‑चलाने‑योग्य प्रोग्राम है:

```java
import com.aspose.words.*;

public class FontWarningDemo {
    public static void main(String[] args) throws Exception {

        // Initialize LoadOptions
        LoadOptions loadOptions = new LoadOptions();

        // Set up warning callback to capture font substitution warnings
        loadOptions.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) {
                if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                    System.out.println("Font substituted: " + info.getDescription());
                }
            }
        });

        // OPTIONAL: Register a custom fonts folder to avoid substitution
        FontSettings fontSettings = new FontSettings();
        fontSettings.setFontsFolder("YOUR_DIRECTORY/custom-fonts", true);
        loadOptions.setFontSettings(fontSettings);

        // Load the document – warnings will be printed automatically
        Document doc = new Document("YOUR_DIRECTORY/font-rich.docx", loadOptions);

        // Verify basic info
        System.out.println("Document loaded successfully.");
        System.out.println("Page count: " + doc.getPageCount());
    }
}
```

**अपेक्षित कंसोल आउटपुट** (जब कोई फ़ॉन्ट गायब हो):

```
Font substituted: Font 'Pacifico' not found, substituted with 'Arial'.
Document loaded successfully.
Page count: 3
```

यदि सभी फ़ॉन्ट्स मौजूद हैं, तो callback चुप रहता है—कुछ भी प्रिंट नहीं होता, जो बिल्कुल अपेक्षित है।

## सामान्य समस्याएँ और प्रो टिप्स

| समस्या | क्यों होता है | समाधान |
|---------|----------------|-----|
| **Callback कभी नहीं चलता** | आपने `LoadOptions` में callback को जोड़ना भूल गए **या** `Document` के डिफ़ॉल्ट कंस्ट्रक्टर का उपयोग किया बिना `loadOptions` पास किए। | हमेशा `loadOptions.setWarningCallback(...)` को कॉल करें **और** `new Document(path, loadOptions)` ओवरलोड का उपयोग करें। |
| **बहुत सारी चेतावनियाँ लॉग को भर देती हैं** | बड़े दस्तावेज़ जिनमें कई गायब फ़ॉन्ट्स होते हैं, प्रत्येक प्रतिस्थापन पर एक चेतावनी उत्पन्न करते हैं। | `info.getDescription()` में विशिष्ट फ़ॉन्ट नामों की जाँच करके आगे फ़िल्टर करें, या बाद में प्रोसेसिंग के लिए चेतावनियों को सूची में एकत्रित करें। |
| **प्रतिस्थापित फ़ॉन्ट्स लेआउट को प्रभावित करते हैं** | फ़ॉलबैक फ़ॉन्ट के मेट्रिक (आकार, स्पेसिंग) अलग हो सकते हैं। | एक कस्टम फ़ॉन्ट्स फ़ोल्डर प्रदान करें (देखें चरण 5) या लोडिंग के बाद दस्तावेज़ की शैली को समायोजित करें। |
| **हेडलेस सर्वर पर चलाना** | डिफ़ॉल्ट फ़ॉन्ट फ़ॉलबैक सर्वर पर स्थापित नहीं होने वाले सिस्टम फ़ॉन्ट्स पर निर्भर हो सकता है। | आवश्यक फ़ॉन्ट्स को अपने एप्लिकेशन के साथ वितरित करें और `FontSettings` को उस फ़ोल्डर की ओर इंगित करें। |

## अक्सर पूछे जाने वाले प्रश्न

**Q: क्या यह PDF या अन्य फ़ॉर्मैट्स के साथ काम करता है?**  
A: हाँ। warning callback फ़ॉर्मैट‑अज्ञेय है; यह Aspose.Words द्वारा लोड किए गए किसी भी दस्तावेज़ प्रकार (DOC, DOCX, RTF, HTML आदि) के लिए चलती है। केवल यह अंतर है कि कौन‑सी चेतावनियाँ दिखाई दे सकती हैं।

**Q: क्या मैं *image resolution* जैसी अन्य चेतावनी प्रकारों को भी कैप्चर कर सकता हूँ?**  
A: बिल्कुल। `warning` मेथड के अंदर, `info.getWarningType()` को जांचें ताकि `WarningType.IMAGE_RESOLUTION` जैसे अन्य enum मान मिल सकें। फिर उन्हें उपयुक्त रूप से हैंडल करें।

**Q: यदि दस्तावेज़ लोड होने के बाद मुझे प्रतिस्थापित फ़ॉन्ट्स की सूची चाहिए तो क्या करें?**  
A: callback के भीतर प्रत्येक `info.getDescription()` को एक `List<String>` में स्टोर करें। लोडिंग के बाद आपके पास एक कलेक्शन होगा जिसे आप लॉग कर सकते हैं, मॉनिटरिंग सर्विस को भेज सकते हैं, या फ़ॉन्ट‑डाउनलोड रूटीन को ट्रिगर करने के लिए उपयोग कर सकते हैं।

## निष्कर्ष

आप अब जानते हैं **Java में Aspose.Words का उपयोग करके फ़ॉन्ट प्रतिस्थापन चेतावनियों को कैसे कैप्चर करें**, प्रत्येक भाग क्यों महत्वपूर्ण है, और वास्तविक‑दुनिया के परिदृश्यों के लिए समाधान को कैसे विस्तारित करें। `LoadOptions`, `Aspose.Words warning callback` और वैकल्पिक `FontSettings` का उपयोग करके आप गायब फ़ॉन्ट्स पर पूरी दृश्यता प्राप्त करते हैं और अपने दस्तावेज़ कन्वर्ज़न पाइपलाइन को भरोसेमंद बना सकते हैं।

अगले कदम के लिए तैयार हैं? `System.out.println` को SLF4J जैसे लॉगर से बदलें, या warning सूची को एक UI में एकीकृत करें जो बैच कन्वर्ज़न समाप्त करने से पहले उपयोगकर्ताओं को चेतावनी दे। आप **Aspose.Words warning callback** को अन्य चेतावनी प्रकारों, जैसे *unsupported features* या *high‑resolution image* अलर्ट्स के लिए भी एक्सप्लोर कर सकते हैं।

कोडिंग का आनंद लें, और आपके PDFs फिर कभी अनपेक्षित फ़ॉन्ट स्वैप से परेशान न हों!

![Screenshot showing console output of captured font substitution warnings](image-placeholder.png "capture font substitution warnings")

## आगे आप क्या सीखें

निम्नलिखित ट्यूटोरियल्स उन विषयों को कवर करते हैं जो इस गाइड में दिखाए गए तकनीकों पर आधारित हैं। प्रत्येक संसाधन में पूर्ण कार्यशील कोड उदाहरण और चरण‑दर‑चरण स्पष्टीकरण शामिल हैं, जिससे आप अतिरिक्त API फीचर्स में निपुण हो सकें और अपने प्रोजेक्ट्स में वैकल्पिक इम्प्लीमेंटेशन एप्रोच को एक्सप्लोर कर सकें।

- [Aspose.Words में फ़ॉन्ट प्रतिस्थापन चेतावनियों को सक्षम करें – पूर्ण गाइड](/words/english/net/working-with-fonts/enable-font-substitution-warnings-in-aspose-words-complete-g/)
- [Aspose.Words for Java में LoadOptions कैसे सेट करें](/words/english/java/document-loading-and-saving/using-load-options/)
- [Aspose.Words for Java के साथ PDF दस्तावेज़ कैसे बनाएं | Document Processing API](/words/english/java/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}