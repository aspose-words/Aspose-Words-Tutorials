---
category: general
date: 2026-01-11
description: Aspose.Words for Java का उपयोग करके फ़ॉन्ट प्रतिस्थापन चेतावनियों को
  कैसे कैप्चर करें, सीखें। यह चरण‑दर‑चरण ट्यूटोरियल LoadOptions और चेतावनी कॉलबैक्स
  को भी कवर करता है।
draft: false
keywords:
- capture font substitution warnings
- Aspose.Words font substitution
- Java warning callback
- LoadOptions usage
- document loading warnings
language: hi
og_description: Aspose.Words for Java के साथ फ़ॉन्ट प्रतिस्थापन चेतावनियों को कैप्चर
  करें। विश्वसनीय दस्तावेज़ लोडिंग के लिए LoadOptions और एक चेतावनी कॉलबैक सेट करने
  हेतु इस गाइड का पालन करें।
og_title: जावा में फ़ॉन्ट प्रतिस्थापन चेतावनियों को कैप्चर करें – पूर्ण ट्यूटोरियल
tags:
- Aspose.Words
- Java
- Document Processing
title: जावा में Aspose.Words के साथ फ़ॉन्ट प्रतिस्थापन चेतावनियों को कैप्चर करें –
  पूर्ण गाइड
url: /hi/java/document-loading-and-saving/capture-font-substitution-warnings-in-java-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# फ़ॉन्ट प्रतिस्थापन चेतावनियों को कैप्चर करें – पूर्ण जावा ट्यूटोरियल

क्या आपको कभी **capture font substitution warnings** की आवश्यकता पड़ी है जब आप किसी ऐसे Word दस्तावेज़ को खोलते हैं जिसमें फ़ॉन्ट अनुपलब्ध होते हैं? यह अक्सर समस्या बन जाता है, ख़ासकर जब आप PDFs जनरेट कर रहे हों या ऐसे सर्वर पर प्रिंट कर रहे हों जहाँ सभी टाइपफ़ेस इंस्टॉल नहीं होते। अच्छी खबर यह है कि Aspose.Words for Java इसे बहुत आसान बना देता है—बस एक `LoadOptions` ऑब्जेक्ट कॉन्फ़िगर करें और एक चेतावनी कॉलबैक जोड़ें। इस गाइड में आप देखेंगे कि इसे कैसे किया जाता है, क्यों महत्वपूर्ण है, और चेतावनी ट्रिगर होने पर क्या अपेक्षा करनी चाहिए।

हम संबंधित विषयों जैसे **Aspose.Words font substitution**, **Java warning callback**, और **LoadOptions usage** के सर्वोत्तम अभ्यासों को भी छुएँगे। अंत तक, आपके पास एक तैयार‑से‑चलाने वाला स्निपेट होगा जो हर मिसिंग‑फ़ॉन्ट इवेंट को लॉग करता है, ताकि आपका डाउनस्ट्रीम प्रोसेसिंग कभी आश्चर्यचकित न हो।

## Prerequisites

कोड में डुबने से पहले सुनिश्चित करें कि आपके पास है:

- Java 17 (या कोई भी हालिया JDK) स्थापित और कॉन्फ़िगर किया हुआ।
- Aspose.Words for Java 23.10 (या नया) आपके क्लासपाथ में।
- एक Word दस्तावेज़ जो ऐसे फ़ॉन्ट को रेफ़र करता है जो आपके स्थानीय सिस्टम में नहीं है (जैसे `DocWithMissingFont.docx`)।
- Java try/catch ब्लॉक्स की बेसिक समझ—कोई जटिलता नहीं।

यदि इनमें से कोई भी परिचित नहीं लग रहा है, तो एक क्षण रुकें और Maven Central से लाइब्रेरी इंस्टॉल करें:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.10</version>
</dependency>
```

अब बुनियादी सेटअप तैयार है, चलिए कोड की ओर बढ़ते हैं।

## Step 1: Set Up a Warning Callback to **Capture Font Substitution Warnings**

सबसे पहले आपको एक कॉलबैक चाहिए जो Aspose.Words को हर बार कॉल करे जब वह कोई मिसिंग फ़ॉन्ट पाए। यही वह जगह है जहाँ हम **capture font substitution warnings** करते हैं। कॉलबैक `IWarningCallback` इंटरफ़ेस को इम्प्लीमेंट करता है और `WarningType` की जाँच करता है।

```java
import com.aspose.words.*;

public class FontSubstitutionInfo {

    // Custom callback that prints details of each font substitution warning
    private static class FontWarningCallback implements IWarningCallback {
        @Override
        public void warning(WarningInfo info) {
            // Only act on font‑substitution warnings
            if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                System.out.println("Font substitution warning:");
                System.out.println("  Original font: " + info.getSource());
                System.out.println("  Substituted by: " + info.getDescription());
            }
        }
    }

    public static void main(String[] args) throws Exception {
        // Code continues in the next steps...
    }
}
```

**Why this matters:** बिना कॉलबैक के, Aspose.Words चुपचाप मिसिंग फ़ॉन्ट को डिफ़ॉल्ट फ़ॉन्ट से बदल देता है, और आपको पता नहीं चलता कि विज़ुअल आउटपुट बदल गया है। चेतावनी को कैप्चर करके आप लॉग, अलर्ट या यहाँ तक कि लोड को एबोर्ट भी कर सकते हैं यदि वह फ़ॉन्ट महत्वपूर्ण हो।

## Step 2: Configure **LoadOptions** and Register the Callback

अब हम एक `LoadOptions` इंस्टेंस बनाते हैं और उसमें अपना `FontWarningCallback` अटैच करते हैं। यह कदम **LoadOptions usage** के लिए आवश्यक है और सुनिश्चित करता है कि हर डॉक्यूमेंट लोड एक ही चेतावनी फ़िल्टर से गुज़रे।

```java
public static void main(String[] args) throws Exception {
    // Step 2: Prepare LoadOptions and hook the warning callback
    LoadOptions loadOptions = new LoadOptions();
    loadOptions.setWarningCallback(new FontWarningCallback());

    // Continue to load the document in the next step...
}
```

**Tip:** आप एक ही `LoadOptions` ऑब्जेक्ट को कई दस्तावेज़ों के लिए री‑यूज़ कर सकते हैं, जिससे कुछ लाइनों की बायलरप्लेट बचती है और आपके एप्लिकेशन में लगातार **document loading warnings** हैंडलिंग सुनिश्चित होती है।

## Step 3: Load the Document and Observe the Output

कॉलबैक सेट होने के बाद, बस अपना Word फ़ाइल लोड करें। यदि दस्तावेज़ ऐसे फ़ॉन्ट को रेफ़र करता है जो इंस्टॉल नहीं है, तो कॉलबैक फायर होगा और कंसोल में विवरण प्रिंट करेगा।

```java
    // Step 3: Load the document using the configured LoadOptions
    Document doc = new Document("YOUR_DIRECTORY/DocWithMissingFont.docx", loadOptions);

    // Step 4: Confirm that the load completed
    System.out.println("Document loaded; check console for any font‑substitution warnings.");
}
```

### Expected Console Output

मान लीजिए `DocWithMissingFont.docx` में मिसिंग फ़ॉन्ट *“Comic Sans MS”* रेफ़र किया गया है, तो आपको कुछ इस तरह दिखेगा:

```
Font substitution warning:
  Original font: Comic Sans MS
  Substituted by: Arial
Document loaded; check console for any font‑substitution warnings.
```

यदि दस्तावेज़ में **कोई मिसिंग फ़ॉन्ट नहीं** है, तो कंसोल केवल अंतिम लाइन दिखाएगा, यह पुष्टि करते हुए कि आपका कॉलबैक कोई फ़ॉल्स पॉज़िटिव नहीं उत्पन्न कर रहा।

## Step 4: Handling Edge Cases and Common Pitfalls

### Multiple Missing Fonts

यदि दस्तावेज़ कई अनुपलब्ध फ़ॉन्ट्स उपयोग करता है, तो कॉलबैक प्रत्येक फ़ॉन्ट के लिए एक बार चलेगा। आपको कई संदेश मिलेंगे, प्रत्येक का अपना `source` और `description` होगा। अतिरिक्त कोड की आवश्यकता नहीं—सिर्फ यह सुनिश्चित करें कि आपका लॉगिंग सिस्टम तेज़ क्रमिक कॉल्स को संभाल सके।

### Suppressing Warnings

कभी‑कभी आप कुछ प्रतिस्थापनों को अनदेखा करना चाह सकते हैं (जैसे आप जानते हैं कि कोई विशेष फॉलबैक स्वीकार्य है)। कॉलबैक लॉजिक को इस तरह विस्तारित करें:

```java
if (info.getWarningType() == WarningType.FONT_SUBSTITUTION &&
    !info.getSource().equalsIgnoreCase("SomeFontYouAccept")) {
    // Log or act on the warning
}
```

### Thread Safety

Aspose.Words `LoadOptions` डिफ़ॉल्ट रूप से थ्रेड‑सेफ़ नहीं है। यदि आप समानांतर में दस्तावेज़ लोड कर रहे हैं, तो प्रत्येक थ्रेड के लिए अलग `LoadOptions` इंस्टेंस बनाएँ, या रेस कंडीशन से बचने के लिए कॉलबैक को सिंक्रनाइज़ करें।

## Step 5: Verifying the Substituted Font in the Resulting Document

लोड करने के बाद, आप यह पुष्टि करना चाह सकते हैं कि प्रतिस्थापन वास्तव में हुआ है या नहीं। API आपको सभी रन पर इटररेट करने और प्रभावी फ़ॉन्ट नाम जांचने की सुविधा देती है:

```java
for (Run run : (Iterable<Run>) doc.getFirstSection().getBody().getChildNodes(NodeType.RUN, true)) {
    System.out.println("Run text: \"" + run.getText() + "\" uses font: " + run.getFont().getName());
}
```

यह स्निपेट प्रत्येक टेक्स्ट रन को उसके अंतिम फ़ॉन्ट के साथ प्रिंट करता है। यह स्वचालित PDF कन्वर्ज़न पाइपलाइन बनाते समय एक उपयोगी sanity check है।

## Full Working Example

सब कुछ मिलाकर, यहाँ पूरा, तैयार‑से‑चलाने वाला प्रोग्राम है:

```java
import com.aspose.words.*;

public class FontSubstitutionInfo {

    private static class FontWarningCallback implements IWarningCallback {
        @Override
        public void warning(WarningInfo info) {
            if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                System.out.println("Font substitution warning:");
                System.out.println("  Original font: " + info.getSource());
                System.out.println("  Substituted by: " + info.getDescription());
            }
        }
    }

    public static void main(String[] args) throws Exception {
        // Prepare LoadOptions and register the warning callback
        LoadOptions loadOptions = new LoadOptions();
        loadOptions.setWarningCallback(new FontWarningCallback());

        // Load the document (replace with your actual path)
        Document doc = new Document("YOUR_DIRECTORY/DocWithMissingFont.docx", loadOptions);

        // Optional: verify effective fonts in the document
        for (Run run : (Iterable<Run>) doc.getFirstSection().getBody().getChildNodes(NodeType.RUN, true)) {
            System.out.println("Run text: \"" + run.getText() + "\" uses font: " + run.getFont().getName());
        }

        System.out.println("Document loaded; check console for any font‑substitution warnings.");
    }
}
```

इसे `FontSubstitutionInfo.java` के रूप में सेव करें, `javac` से कंपाइल करें, और `java FontSubstitutionInfo` चलाएँ। आपको चेतावनी संदेश (यदि कोई हों) के बाद रन और उनके अंतिम फ़ॉन्ट की सूची दिखेगी।

## Visual Aid

![फ़ॉन्ट प्रतिस्थापन चेतावनियों को दिखाते हुए कंसोल आउटपुट का स्क्रीनशॉट](/images/font-substitution-warning.png "फ़ॉन्ट प्रतिस्थापन चेतावनियों का उदाहरण")

*Alt text:* **capture font substitution warnings** – दस्तावेज़ में मिसिंग फ़ॉन्ट्स लोड करने के बाद कंसोल आउटपुट।

## Conclusion

अब आप जानते हैं कि Aspose.Words for Java का उपयोग करके **capture font substitution warnings** कैसे किया जाता है। `LoadOptions` ऑब्जेक्ट को कॉन्फ़िगर करके और एक कस्टम `IWarningCallback` प्रदान करके आप किसी भी मिसिंग‑फ़ॉन्ट इवेंट पर पूरी दृश्यता प्राप्त कर सकते हैं, जो अन्यथा चुपचाप आपके दस्तावेज़ की उपस्थिति को बदल सकता है। यह तकनीक सीधे **Aspose.Words font substitution** हैंडलिंग में इंटीग्रेट होती है, विश्वसनीय **document loading warnings** सुनिश्चित करती है, और आपको अपने बिज़नेस नियमों के अनुसार लॉग, अलर्ट या एबोर्ट करने की लचीलापन देती है।

### What’s Next?

- अन्य चेतावनी प्रकारों (जैसे `DEPRECATED_FEATURE`) के लिए **Java warning callback** पैटर्न एक्सप्लोर करें।
- इस एप्रोच को **PDF conversion** के साथ मिलाकर सुनिश्चित करें कि प्रतिस्थापित फ़ॉन्ट लेआउट को नहीं तोड़ते।
- **LoadOptions usage** में गहराई से जाएँ—`Password`, `Encoding`, और `ResourceLoadingCallback` के साथ प्रयोग करें ताकि अधिक उन्नत परिदृश्य संभाल सकें।

कॉलबैक को अपनी जरूरतों के अनुसार ट्यून करें, चेतावनियों को लॉगिंग फ्रेमवर्क पर रूट करें, या यदि कोई महत्वपूर्ण फ़ॉन्ट मिसिंग हो तो कस्टम एक्सेप्शन थ्रो करें। संभावनाएँ असीमित हैं, और अब आपके पास एक ठोस आधार है जिसपर आप निर्माण कर सकते हैं।

Happy coding, and may your documents always render just the way you expect!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}