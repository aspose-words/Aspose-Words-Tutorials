---
category: general
date: 2026-07-03
description: जावा में वार्निंग कॉलबैक रजिस्टर करें ताकि वर्ड दस्तावेज़ प्रोसेस करते
  समय गायब फ़ॉन्ट्स का पता लगाया जा सके। Aspose.Words की वार्निंग हैंडलिंग और फ़ॉन्ट
  प्रतिस्थापन का पता लगाना सीखें।
draft: false
keywords:
- register warning callback
- detect missing fonts
- font substitution warning
- Aspose.Words warning callback
- Java missing font detection
- document font handling
language: hi
og_description: जावा में चेतावनी कॉलबैक पंजीकृत करके गायब फ़ॉन्ट्स का पता लगाएँ। यह
  गाइड Aspose.Words के साथ फ़ॉन्ट प्रतिस्थापन चेतावनियों को कैप्चर करने का तरीका दिखाता
  है।
og_title: जावा में चेतावनी कॉलबैक पंजीकृत करें – लापता फ़ॉन्ट्स का पता लगाएँ
schemas:
- author: Aspose
  dateModified: '2026-07-03'
  description: Register warning callback in Java to detect missing fonts while processing
    Word docs. Learn Aspose.Words warning handling and font substitution detection.
  headline: Register warning callback in Java – Detect missing fonts easily
  type: TechArticle
- description: Register warning callback in Java to detect missing fonts while processing
    Word docs. Learn Aspose.Words warning handling and font substitution detection.
  name: Register warning callback in Java – Detect missing fonts easily
  steps:
  - name: Why this matters
    text: '* **Visibility:** Without a callback, the substitution happens silently,
      and you might ship a document with the wrong appearance. * **Automation:** In
      batch pipelines you can log every missing‑font incident and later feed the list
      to a font‑installation script. * **Compliance:** Some industries (e.g'
  - name: Expected console output
    text: 'Assuming `input.docx` references the font *“Comic Sans MS”* which isn’t
      installed, you’ll see something like:'
  - name: Multiple missing fonts
    text: If a document references several unavailable fonts, the callback will fire
      once per font. You can aggregate the messages into a list if you need a summary
      report later.
  - name: Controlling substitution behavior
    text: 'Sometimes you *do* want to force a particular fallback font. Use `FontSettings`
      before loading the document:'
  - name: Performance considerations
    text: 'Registering a warning callback introduces a tiny overhead—only a few nanoseconds
      per warning. In high‑throughput services (e.g., converting thousands of docs
      per hour) the impact is negligible. However, if you’re processing millions,
      consider disabling warnings after you’ve verified the font set is '
  - name: Cross‑platform notes
    text: The callback works identically on Windows, macOS, and Linux. The only difference
      is the set of fonts available on each OS. If you run the same job on multiple
      agents, you might see different substitution messages. To keep results deterministic,
      ship a **custom font folder** and point Aspose.Words to
  type: HowTo
tags:
- Aspose.Words
- Java
- Fonts
title: जावा में चेतावनी कॉलबैक पंजीकृत करें – गायब फ़ॉन्ट्स को आसानी से पहचानें
url: /hi/java/document-loading-and-saving/register-warning-callback-in-java-detect-missing-fonts-easil/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Java में warning callback पंजीकृत करें – फ़ॉन्ट की कमी आसानी से पता करें

क्या आपने कभी सोचा है कि **warning callback पंजीकृत** कैसे करें ताकि आप Word दस्तावेज़ों को परिवर्तित या संपादित करते समय **फ़ॉन्ट की कमी का पता लगा सकें**? आप अकेले नहीं हैं। फ़ॉन्ट की कमी चुपचाप लेआउट को बिगाड़ सकती है, एक सुगठित रिपोर्ट को गड़बड़ में बदल देती है, और अधिकांश डेवलपर्स इसे तब तक नहीं समझ पाते जब तक अंतिम PDF में समस्या न दिखे।

इस ट्यूटोरियल में हम एक पूर्ण, तुरंत चलाने योग्य उदाहरण के माध्यम से आपको दिखाएंगे कि Aspose.Words for Java की warning सिस्टम में कैसे जुड़ें, उन परेशान करने वाले फ़ॉन्ट‑सब्स्टिट्यूशन अलर्ट को कैसे पकड़ें, और उन्हें लॉग करें या अपनी आवश्यकता अनुसार प्रतिक्रिया दें। कोई अस्पष्ट “डॉक्यूमेंट देखें” शॉर्टकट नहीं—सिर्फ शुद्ध, कॉपी‑पेस्ट कोड और प्रत्येक पंक्ति के पीछे की तर्कसंगतता।

## आवश्यकताएँ

* **Java 17** (या कोई भी नवीनतम JDK) स्थापित और `JAVA_HOME` सेट हो।  
* **Aspose.Words for Java** JAR (आधिकारिक साइट से डाउनलोड करें या Maven के माध्यम से प्राप्त करें)।  
* एक नमूना `.docx` फ़ाइल जिसमें ऐसा फ़ॉन्ट संदर्भित हो **जो आपके मशीन पर स्थापित नहीं है**—यह warning को ट्रिगर करेगा।  
* आपका पसंदीदा IDE या एक साधारण टेक्स्ट एडिटर और कमांड‑लाइन बिल्ड टूल्स।

बस इतना ही। कोई अतिरिक्त फ्रेमवर्क नहीं, कोई बाहरी सेवा नहीं। तैयार हैं? चलिए शुरू करते हैं।

## चरण 1: प्रोजेक्ट सेट अप करें और Aspose.Words जोड़ें

यदि आप Maven उपयोग कर रहे हैं, तो अपने `pom.xml` में निम्नलिखित dependency जोड़ें:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.10</version> <!-- use the latest stable version -->
</dependency>
```

Gradle के लिए, इसे `build.gradle` में डालें:

```groovy
implementation 'com.aspose:aspose-words:24.10'
```

यदि आप मैन्युअल तरीका पसंद करते हैं, तो बस `aspose-words-24.10.jar` को अपने classpath में रखें।  
**Pro tip:** JAR को अपने `src` फ़ोल्डर के बगल में रखें; इससे बाद में `javac` कमांड सरल हो जाता है।

## चरण 2: वह दस्तावेज़ लोड करें जिसमें फ़ॉन्ट की कमी हो सकती है

सबसे पहले आप स्रोत फ़ाइल की ओर इशारा करने वाला `Document` ऑब्जेक्ट बनाते हैं। यह कदम सरल है, लेकिन यही वह जगह है जहाँ लाइब्रेरी फ़ाइल को स्कैन करती है और *संभवतः* गायब फ़ॉन्ट खोजती है।

```java
import com.aspose.words.*;

public class FontWarningDemo {
    public static void main(String[] args) throws Exception {
        // Adjust the path to point at your test document
        String inputPath = "YOUR_DIRECTORY/input.docx";

        // Load the document – Aspose.Words will start parsing it now
        Document doc = new Document(inputPath);
```

यहाँ, `Document` सभी Aspose.Words ऑपरेशन्स का प्रवेश बिंदु है। जब कंस्ट्रक्टर चलता है, लाइब्रेरी दस्तावेज़ के XML को पार्स करती है, फ़ॉन्ट हल करती है, और यदि कोई फ़ॉन्ट उपलब्ध नहीं है, तो वह *एक warning* को कतारबद्ध करता है जिसे हम बाद में पकड़ सकते हैं।

## चरण 3: फ़ॉन्ट‑सब्स्टिट्यूशन अलर्ट पकड़ने के लिए warning callback पंजीकृत करें

अब मुख्य भाग: **warning callback पंजीकृत करें**। Aspose.Words आपको `IWarningCallback` इंटरफ़ेस का कार्यान्वयन प्लग‑इन करने देता है। हर बार जब इंजन किसी ऐसी स्थिति पर पहुँचता है जिसे फ़्लैग करना चाहिए—जैसे फ़ॉन्ट की कमी—तो वह आपके `warning` मेथड को कॉल करता है।

```java
        // Register the warning callback
        doc.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) {
                // We’re only interested in font substitution warnings
                if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                    System.out.println("⚠️ Font substituted: " + info.getDescription());
                }
            }
        });
```

### यह क्यों महत्वपूर्ण है

* **Visibility (दृश्यता):** बिना callback के, सब्स्टिट्यूशन चुपचाप हो जाता है, और आप गलत रूप वाला दस्तावेज़ शिप कर सकते हैं।  
* **Automation (स्वचालन):** बैच पाइपलाइन में आप हर फ़ॉन्ट‑की‑कमी घटना को लॉग कर सकते हैं और बाद में सूची को फ़ॉन्ट‑इंस्टॉलेशन स्क्रिप्ट को दे सकते हैं।  
* **Compliance (अनुपालन):** कुछ उद्योग (जैसे कानूनी) को यह प्रमाण चाहिए कि मूल फ़ॉन्ट उपयोग किए गए थे या सही तरीके से सब्स्टिट्यूट किए गए थे।

ध्यान दें कि हम `WarningType.FONT_SUBSTITUTION` पर फ़िल्टर करते हैं। Aspose.Words कई प्रकार की warnings उत्पन्न करता है—लेआउट ओवरफ़्लो, अप्रचलित फीचर आदि—पर हमें केवल उन warnings की परवाह है जो बताती हैं कि फ़ॉन्ट गायब था। इससे कंसोल साफ़ रहता है और **फ़ॉन्ट की कमी का पता लगाने** लक्ष्य पर ध्यान केंद्रित रहता है।

## चरण 4: दस्तावेज़ को सहेजें और callback को ट्रिगर होने दें

जब आप अंत में `save` कॉल करते हैं, तो इंजन सभी लाज़ी लोडिंग पूरी करता है और सहेजने के दौरान पाए गए प्रत्येक गायब फ़ॉन्ट के लिए warning callback को ट्रिगर करता है।

```java
        // Save the document – this is where the warning callback gets invoked
        String outputPath = "YOUR_DIRECTORY/output.docx";
        doc.save(outputPath);

        System.out.println("✅ Document saved to " + outputPath);
    }
}
```

### अपेक्षित कंसोल आउटपुट

मान लीजिए `input.docx` में फ़ॉन्ट *“Comic Sans MS”* संदर्भित है जो स्थापित नहीं है, तो आपको कुछ इस तरह दिखेगा:

```
⚠️ Font substituted: Font 'Comic Sans MS' is not available. Substituted with 'Arial'.
✅ Document saved to YOUR_DIRECTORY/output.docx
```

यदि स्रोत दस्तावेज़ में केवल स्थापित फ़ॉन्ट ही हैं, तो warning लाइन कभी नहीं दिखेगी—जिसका अर्थ है कि **फ़ॉन्ट की कमी का पता लगाना** चुपचाप सफल रहा।

![रजिस्टर warning callback के कार्य को दर्शाते हुए कंसोल आउटपुट और फ़ॉन्ट की कमी का पता लगाना](register-warning-callback-output.png)

*छवि वैकल्पिक पाठ: रजिस्टर warning callback आउटपुट जो फ़ॉन्ट की कमी को दर्शाता है*

## चरण 5: किनारे के मामलों को संभालना और सर्वोत्तम‑प्रैक्टिस टिप्स

### कई गायब फ़ॉन्ट

यदि किसी दस्तावेज़ में कई अनुपलब्ध फ़ॉन्ट संदर्भित हैं, तो callback प्रत्येक फ़ॉन्ट के लिए एक बार फायर होगा। यदि आपको बाद में सारांश रिपोर्ट चाहिए, तो आप संदेशों को एक सूची में एकत्र कर सकते हैं।

```java
List<String> missingFonts = new ArrayList<>();
doc.setWarningCallback(info -> {
    if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
        missingFonts.add(info.getDescription());
    }
});
// After saving
if (!missingFonts.isEmpty()) {
    System.out.println("Missing fonts detected:");
    missingFonts.forEach(System.out::println);
}
```

### सब्स्टिट्यूशन व्यवहार को नियंत्रित करना

कभी-कभी आप *वास्तव में* किसी विशेष फॉलबैक फ़ॉन्ट को मजबूर करना चाहते हैं। दस्तावेज़ लोड करने से पहले `FontSettings` का उपयोग करें:

```java
FontSettings settings = new FontSettings();
settings.setSubstitutionSettings(new FontSubstitutionSettings()
        .addSubstitutes("Comic Sans MS", "Times New Roman"));
doc.setFontSettings(settings);
```

अब भी callback फायर होगा, लेकिन आपको ठीक-ठीक पता होगा कि कौन सा फ़ॉन्ट उपयोग किया जाएगा।

### प्रदर्शन संबंधी विचार

warning callback पंजीकृत करने से एक छोटा ओवरहेड जुड़ता है—प्रति warning केवल कुछ नैनोसेकंड। उच्च‑थ्रूपुट सेवाओं में (जैसे, प्रति घंटे हजारों दस्तावेज़ बदलना) इसका प्रभाव नगण्य है। हालांकि, यदि आप लाखों प्रोसेस कर रहे हैं, तो फ़ॉन्ट सेट की पूर्णता की पुष्टि के बाद warnings को निष्क्रिय करने पर विचार करें:

```java
doc.setWarningCallback(null); // turn off after initial scan
```

### क्रॉस‑प्लेटफ़ॉर्म नोट्स

callback Windows, macOS, और Linux पर समान रूप से काम करता है। केवल अंतर प्रत्येक OS पर उपलब्ध फ़ॉन्ट सेट में है। यदि आप एक ही जॉब कई एजेंट्स पर चलाते हैं, तो आपको अलग‑अलग सब्स्टिट्यूशन संदेश मिल सकते हैं। परिणामों को निर्धारित रखने के लिए, एक **कस्टम फ़ॉन्ट फ़ोल्डर** प्रदान करें और Aspose.Words को `FontSettings.setFontsFolder("path/to/fonts", true);` के माध्यम से उस पर इंगित करें।

## पूर्ण, चलाने योग्य उदाहरण

नीचे पूरा Java क्लास दिया गया है जिसे आप `src/main/java/FontWarningDemo.java` में कॉपी‑पेस्ट कर सकते हैं। इसमें सभी इम्पोर्ट्स, एरर हैंडलिंग, और टिप्पणी शामिल हैं जो इसे तुरंत चलाने के लिए आवश्यक हैं।

```java
import com.aspose.words.*;
import java.util.ArrayList;
import java.util.List;

/**
 * Demonstrates how to register a warning callback in Aspose.Words for Java
 * to detect missing fonts during document processing.
 */
public class FontWarningDemo {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Paths – adjust to your environment
        String inputPath = "YOUR_DIRECTORY/input.docx";
        String outputPath = "YOUR_DIRECTORY/output.docx";

        // 2️⃣ Load the document (parsing begins here)
        Document doc = new Document(inputPath);

        // 3️⃣ Optional: set a custom font folder if you ship fonts with your app
        // FontSettings fs = new FontSettings();
        // fs.setFontsFolder("fonts", true);
        // doc.setFontSettings(fs);

        // 4️⃣ Register the warning callback to catch missing‑font warnings
        List<String> missingFonts = new ArrayList<>();
        doc.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) {
                if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                    // Log to console
                    System.out.println("⚠️ Font substituted: " + info.getDescription());
                    // Collect for later reporting
                    missingFonts.add(info.getDescription());
                }
            }
        });

        // 5️⃣ Save the document – triggers the callback
        doc.save(outputPath);
        System.out.println("✅ Document saved to " + outputPath);

        // 6️⃣ Post‑save reporting (if any fonts were missing)
        if (!missingFonts.isEmpty()) {
            System.out.println("\nSummary of missing fonts:");
            missingFonts.forEach(System.out::println);
        } else {
            System.out.println("\nNo missing fonts detected.");
        }
    }
}
```

कम्पाइल और चलाएँ:

```bash
javac -cp "aspose-words-24.10.jar" FontWarningDemo.java
java -cp ".:aspose-words-24.10.jar" FontWarningDemo
```

आपको warning लाइनों (यदि हों) के बाद सफलता संदेश दिखना चाहिए।

## निष्कर्ष

आपने अभी **Java में warning callback पंजीकृत करना** सीख लिया है ताकि Aspose.Words के साथ काम करते समय **फ़ॉन्ट की कमी का पता लगा सकें**। लाइब्रेरी की warning सिस्टम में प्लग‑इन करके आप फ़ॉन्ट‑सब्स्टिट्यूशन घटनाओं की पूरी दृश्यता प्राप्त करते हैं, उन्हें अनुपालन के लिए लॉग कर सकते हैं, और आवश्यकता पड़ने पर प्रोग्रामेटिक रूप से फ़ॉन्ट बदल भी सकते हैं।

अब आप आगे खोज सकते हैं:

* **Detect missing fonts** को लूप या parallel streams का उपयोग करके फ़ाइलों के बैच में खोजें।  
* उत्पादन‑स्तर की रिपोर्टों के लिए callback को लॉगिंग फ्रेमवर्क (SLF4J, Log4j) के साथ एकीकृत करें।  
* `FontSettings` का उपयोग करके कॉर्पोरेट फ़ॉन्ट पैलेट लागू करें और अनचाहे फॉलबैक से बचें।

इसे आज़माएँ—इनपुट दस्तावेज़ बदलें, विभिन्न फ़ॉन्ट‑की‑कमी परिदृश्य आज़माएँ, और देखें कि callback कैसे व्यवहार करता है। यदि आपको कोई अजीब समस्या मिले, तो नीचे टिप्पणी छोड़ें; कोडिंग का आनंद लें!

## आगे आप क्या सीखें?

निम्नलिखित ट्यूटोरियल्स उन निकट संबंधित विषयों को कवर करते हैं जो इस गाइड में दिखाए गए तकनीकों पर आधारित हैं। प्रत्येक संसाधन में पूर्ण कार्यशील कोड उदाहरण और चरण‑दर‑चरण व्याख्याएँ शामिल हैं जो आपको अतिरिक्त API फीचर्स में महारत हासिल करने और अपने प्रोजेक्ट्स में वैकल्पिक कार्यान्वयन दृष्टिकोणों का अन्वेषण करने में मदद करती हैं।

- [Capture Font Substitution Warnings in Java with Aspose.Words – Complete Guide](/words/english/java/document-loading-and-saving/capture-font-substitution-warnings-in-java-with-aspose-words/)
- [Warning Callback In Word Document](/words/english/net/programming-with-loadoptions/warning-callback/)
- [Aspose Words Java Callback Custom Savings](/words/hindi/java/images-shapes/aspose-words-java-callback-custom-savings/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}