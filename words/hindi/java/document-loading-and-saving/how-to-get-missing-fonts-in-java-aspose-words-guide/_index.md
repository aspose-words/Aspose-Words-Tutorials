---
category: general
date: 2026-02-15
description: Aspose.Words का उपयोग करके जावा में वर्ड दस्तावेज़ लोड करते समय लापता
  फ़ॉन्ट्स को प्राप्त करने के तरीके सीखें। इसमें चेतावनी कॉलबैक और फ़ॉन्ट‑प्रतिस्थापन
  संभालना शामिल है।
draft: false
keywords:
- how to get missing fonts
- Aspose.Words missing font
- font substitution warning
- Java LoadOptions warning callback
- document processing Java
language: hi
og_description: Aspose.Words के साथ Java में गायब फ़ॉन्ट कैसे प्राप्त करें। चेतावनी
  कॉलबैक, फ़ॉन्ट प्रतिस्थापन हैंडलिंग और दस्तावेज़ प्रोसेसिंग के लिए सर्वोत्तम प्रथाओं
  की खोज करें।
og_title: जावा में लापता फ़ॉन्ट्स कैसे प्राप्त करें – Aspose.Words गाइड
tags:
- Aspose.Words
- Java
- Font Management
title: जावा में लापता फ़ॉन्ट्स कैसे प्राप्त करें – Aspose.Words गाइड
url: /hi/java/document-loading-and-saving/how-to-get-missing-fonts-in-java-aspose-words-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# जावा में मिसिंग फ़ॉन्ट्स कैसे प्राप्त करें – Aspose.Words गाइड

क्या आपने कभी जावा में एक Word दस्तावेज़ खोला है और अजीब फ़ॉन्ट प्रतिस्थापन देख कर **मिसिंग फ़ॉन्ट्स कैसे प्राप्त करें** सोचते हैं? आप इस आश्चर्य के पहले नहीं हैं। कई एंटरप्राइज़ एप्लिकेशन्स में, मिसिंग फ़ॉन्ट चेतावनियां रिपोर्ट, अनुबंध, या मार्केटिंग सामग्री की दृश्य सटीकता को बिगाड़ सकती हैं।

अच्छी खबर? Aspose.Words आपको एक कॉलबैक के माध्यम से उन चेतावनियों को पकड़ने का साफ़ तरीका देता है, ताकि आप दस्तावेज़ रेंडर होने से पहले लॉग, प्रतिस्थापित या उपयोगकर्ताओं को सूचित कर सकें। इस ट्यूटोरियल में हम एक पूर्ण, चलाने योग्य उदाहरण के माध्यम से **मिसिंग फ़ॉन्ट्स कैसे प्राप्त करें** दिखाएंगे, समझाएंगे कि कॉलबैक क्यों महत्वपूर्ण है, और वास्तविक प्रोजेक्ट्स में आवश्यक कुछ एज‑केस ट्रिक्स को कवर करेंगे।

> **प्रो टिप:** यदि आप पहले से ही Aspose.Words 22.12 या उससे नया उपयोग कर रहे हैं, तो नीचे दिखाया गया API अतिरिक्त कॉन्फ़िगरेशन के बिना सीधे काम करता है।

---

![Aspose.Words चेतावनी कॉलबैक का उपयोग करके मिसिंग फ़ॉन्ट्स कैसे प्राप्त करें, यह दर्शाने वाला आरेख](how-to-get-missing-fonts-diagram.png "मिसिंग फ़ॉन्ट्स आरेख")

## इस ट्यूटोरियल में क्या कवर किया गया है

- फ़ॉन्ट‑सबस्टीट्यूशन चेतावनियों को कैप्चर करने के लिए **Java LoadOptions warning callback** सेट अप करना।  
- चेतावनियों को फ़िल्टर करना ताकि आप केवल मिसिंग फ़ॉन्ट्स से संबंधित वाले देखें।  
- कौन से फ़ॉन्ट्स को बदल दिया गया और किसके साथ बदला गया, इसका स्पष्ट, मानव‑पठनीय रिपोर्ट प्रिंट करना।  
- बड़े दस्तावेज़ों को संभालने, चेतावनी स्तर को कस्टमाइज़ करने, और समाधान को बड़े प्रोसेसिंग पाइपलाइन में एकीकृत करने के टिप्स।

इस गाइड के अंत तक आप प्रश्न “**मिसिंग फ़ॉन्ट्स कैसे प्राप्त करें**?” का उत्तर तैयार‑चलाने योग्य कोड स्निपेट और अंतर्निहित मैकेनिक्स की ठोस समझ के साथ दे पाएंगे।

### पूर्वापेक्षाएँ

- Java 8 या उससे नया स्थापित हो।  
- Aspose.Words for Java लाइब्रेरी (आधिकारिक साइट से डाउनलोड करें या Maven/Gradle के माध्यम से जोड़ें)।  
- एक Word दस्तावेज़ जो आपके मशीन पर स्थापित नहीं फ़ॉन्ट को संदर्भित करता है (जैसे, `MissingFont.docx`)।  

यदि आप इनमें से कोई भी चीज़ नहीं रखते, तो अभी लाइब्रेरी प्राप्त करें—Maven में जोड़ना इतना सरल है:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version> <!-- replace with the latest version -->
</dependency>
```

---

## चरण 1: फ़ॉन्ट‑सबस्टीट्यूशन चेतावनियों के लिए एक संग्रह तैयार करें

डॉक्यूमेंट लोड करने से पहले हमें Aspose.Words द्वारा उत्पन्न किसी भी चेतावनी को संग्रहीत करने के लिए एक जगह चाहिए। `ArrayList<WarningInfo>` अच्छा काम करता है क्योंकि यह क्रम को बनाए रखता है और बाद में इटररेट करने की सुविधा देता है।

```java
import com.aspose.words.*;
import java.util.ArrayList;
import java.util.List;

// Step 1: Create a list that will hold warning information.
List<WarningInfo> fontWarnings = new ArrayList<>();
```

*Why this matters:* चेतावनी कॉलबैक एक ही फ़ाइल के लिए दर्जनों बार फायर हो सकता है—हर मिसिंग ग्लिफ़, हर एम्बेडेड इमेज समस्या आदि के लिए। उन्हें पहले इकट्ठा करके आप लोडिंग चरण को तेज़ रख सकते हैं और प्रोसेसिंग को नियंत्रित लूप में स्थगित कर सकते हैं।

## चरण 2: LoadOptions को एक Warning Callback के साथ कॉन्फ़िगर करें

Aspose.Words आपको `IWarningCallback` प्लग‑इन करने देता है। कॉलबैक के अंदर हम स्टेप 1 की सूची में हर `WarningInfo` जोड़ेंगे।

```java
// Step 2: Set up LoadOptions with a custom warning callback.
LoadOptions loadOptions = new LoadOptions();
loadOptions.setWarningCallback(new IWarningCallback() {
    @Override
    public void warning(WarningInfo info) {
        // Capture every warning; we'll filter later.
        fontWarnings.add(info);
    }
});
```

*Explanation:* `warning` मेथड दस्तावेज़ लोडिंग के दौरान **सिंक्रोनस** रूप से कॉल किया जाता है। `WarningInfo` को बस `fontWarnings` में पुश करके हम किसी भी भारी I/O (जैसे फ़ाइल में लॉगिंग) से बचते हैं जो लोड को धीमा कर सकता है। यह पैटर्न—पहले इकट्ठा करें‑फिर प्रोसेस करें—बड़ी संख्या में चेतावनियों को संभालने का अनुशंसित तरीका है।

## चरण 3: कॉन्फ़िगर किए गए Options के साथ दस्तावेज़ लोड करें

अब हम वास्तव में Word फ़ाइल पढ़ते हैं। यदि दस्तावेज़ में ऐसे फ़ॉन्ट हैं जो स्थापित नहीं हैं, तो Aspose.Words स्वचालित रूप से उन्हें प्रतिस्थापित करेगा और हमने अभी जो कॉलबैक सेट किया है, उसे फायर करेगा।

```java
// Step 3: Load the document with the warning‑aware LoadOptions.
String filePath = "YOUR_DIRECTORY/MissingFont.docx"; // adjust to your environment
Document doc = new Document(filePath, loadOptions);
```

*What happens under the hood?* Aspose.Words फ़ाइल की फ़ॉन्ट टेबल को पार्स करता है, उसे होस्ट OS पर उपलब्ध फ़ॉन्ट्स से तुलना करता है, और हर मिसिंग एंट्री के लिए `WarningInfo` बनाता है जिसमें `WarningSource.FontSubstitution` होता है। यही स्रोत हमें मिसिंग‑फ़ॉन्ट चेतावनियों को अलग करने की कुंजी देगा।

## चरण 4: केवल फ़ॉन्ट‑सबस्टीट्यूशन चेतावनियों को फ़िल्टर और प्रदर्शित करें

लोडिंग के बाद, `fontWarnings` में विभिन्न प्रकार के संदेश (जैसे, डिप्रिकेटेड फीचर्स, इमेज समस्याएँ) हो सकते हैं। हमें केवल मिसिंग फ़ॉन्ट्स की परवाह है, इसलिए हम सूची में लूप करके एक संक्षिप्त रिपोर्ट प्रिंट करेंगे।

```java
// Step 4: Output any font‑substitution warnings that were captured.
for (WarningInfo warning : fontWarnings) {
    if (warning.getSource() == WarningSource.FontSubstitution) {
        System.out.println("Substituted '" + warning.getDescription() + "' with '" +
                           warning.getAdditionalInfo() + "'");
    }
}
```

**उदाहरण आउटपुट**

```
Substituted 'Comic Sans MS' with 'Arial'
Substituted 'Times New Roman PS' with 'Times New Roman'
```

*Why this is useful:* `description` फ़ील्ड बताता है कि दस्तावेज़ ने कौन सा फ़ॉन्ट मांगा था, जबकि `additionalInfo` बताता है कि Aspose.Words ने वास्तव में क्या उपयोग किया। इस डेटा के साथ आप:

- उपयोगकर्ता को मिसिंग फ़ॉन्ट इंस्टॉल करने के लिए प्रॉम्प्ट कर सकते हैं।  
- प्रोग्रामेटिक रूप से एक सब्स्टीट्यूट फ़ॉन्ट को दस्तावेज़ में एम्बेड कर सकते हैं (`doc.getFontInfos().add(...)`)।  
- अनुपालन ऑडिट के लिए इस इवेंट को लॉग कर सकते हैं।

## एज केस और सामान्य वैरिएशन को संभालना

### 1. नॉन‑फ़ॉन्ट चेतावनियों को दबाना

यदि आप केवल फ़ॉन्ट‑संबंधित संदेश चाहते हैं, तो कॉलबैक को कड़ा कर सकते हैं:

```java
loadOptions.setWarningCallback(info -> {
    if (info.getSource() == WarningSource.FontSubstitution) {
        fontWarnings.add(info);
    }
});
```

यह बड़े बैच प्रोसेसिंग के दौरान मेमोरी उपयोग को कम करता है।

### 2. चेतावनी गंभीरता को समायोजित करना

Aspose.Words चेतावनियों को `WarningType` द्वारा वर्गीकृत करता है। मिसिंग फ़ॉन्ट्स के लिए आप आमतौर पर `WarningType.FontSubstitution` देखेंगे। यदि आप उन्हें एरर के रूप में ट्रीट करना चाहते हैं (जैसे, लोडिंग को रोकना), तो कॉलबैक के अंदर एक्सेप्शन थ्रो करें:

```java
loadOptions.setWarningCallback(info -> {
    if (info.getSource() == WarningSource.FontSubstitution) {
        throw new RuntimeException("Missing font detected: " + info.getDescription());
    }
});
```

### 3. फ़ाइलों के बजाय स्ट्रीम्स के साथ काम करना

कभी‑कभी दस्तावेज़ डेटाबेस या HTTP रिक्वेस्ट से आते हैं। वही तरीका `InputStream` के साथ काम करता है:

```java
InputStream docStream = new ByteArrayInputStream(bytesFromDb);
Document doc = new Document(docStream, loadOptions);
```

सिर्फ लोडिंग के बाद स्ट्रीम को बंद करना याद रखें।

### 4. कस्टम फ़ॉन्ट फ़ोल्डर का उपयोग करना

यदि आपके पास कॉर्पोरेट फ़ॉन्ट्स का संग्रह साझा ड्राइव पर है, तो Aspose.Words को उस फ़ोल्डर की ओर इशारा करें:

```java
loadOptions.setFontSettings(new FontSettings());
loadOptions.getFontSettings().setFontsFolder("C:/CorporateFonts", true);
```

अब लाइब्रेरी सिस्टम फ़ॉन्ट्स पर वापस गिरने से पहले *पहले* वहाँ देखेगी, जिससे मिसिंग‑फ़ॉन्ट चेतावनियों की संख्या में उल्लेखनीय कमी आएगी।

## पूर्ण कार्यशील उदाहरण

सब कुछ एक साथ मिलाते हुए, यहाँ एक स्व-निहित क्लास है जिसे आप किसी भी जावा प्रोजेक्ट में डाल सकते हैं:

```java
import com.aspose.words.*;
import java.util.ArrayList;
import java.util.List;

public class MissingFontDetector {

    public static void main(String[] args) {
        // 1️⃣ Prepare a collection for warnings.
        List<WarningInfo> fontWarnings = new ArrayList<>();

        // 2️⃣ Create LoadOptions with a warning callback.
        LoadOptions loadOptions = new LoadOptions();
        loadOptions.setWarningCallback(info -> fontWarnings.add(info));

        // (Optional) Point to a custom font folder.
        // FontSettings fontSettings = new FontSettings();
        // fontSettings.setFontsFolder("C:/CorporateFonts", true);
        // loadOptions.setFontSettings(fontSettings);

        // 3️⃣ Load the document.
        String docPath = "YOUR_DIRECTORY/MissingFont.docx";
        Document doc;
        try {
            doc = new Document(docPath, loadOptions);
        } catch (Exception e) {
            System.err.println("Failed to load document: " + e.getMessage());
            return;
        }

        // 4️⃣ Print missing‑font warnings.
        System.out.println("=== Missing Font Report ===");
        for (WarningInfo warning : fontWarnings) {
            if (warning.getSource() == WarningSource.FontSubstitution) {
                System.out.println("Substituted '" + warning.getDescription() + "' with '" +
                                   warning.getAdditionalInfo() + "'");
            }
        }
        System.out.println("=== End of Report ===");
    }
}
```

इस प्रोग्राम को चलाएँ, और आपको Aspose.Words द्वारा बदले गए हर फ़ॉन्ट की एक साफ़ सूची दिखेगी। कोई अतिरिक्त लाइब्रेरी नहीं, कोई छिपा जादू नहीं—सिर्फ शुद्ध जावा और **Aspose.Words मिसिंग फ़ॉन्ट** API की शक्ति।

## निष्कर्ष

हमने जावा वातावरण में Aspose.Words का उपयोग करके **मिसिंग फ़ॉन्ट्स कैसे प्राप्त करें** का मुख्य प्रश्न उत्तर दिया। `LoadOptions` चेतावनी कॉलबैक को अटैच करके, `WarningInfo` ऑब्जेक्ट्स को इकट्ठा करके, और `FontSubstitution` स्रोतों के लिए फ़िल्टर करके, आप रेंडरिंग से पहले फ़ॉन्ट‑संबंधी समस्याओं की पूरी दृश्यता प्राप्त करते हैं। यह दृष्टिकोण सिंगल‑फ़ाइल यूटिलिटीज़ से लेकर बड़े बैच प्रोसेसर तक स्केलेबल है, और कस्टम फ़ॉन्ट फ़ोल्डर, गंभीरता हैंडलिंग, या स्ट्रीम‑आधारित इनपुट को समायोजित करने के लिए पर्याप्त लचीला है।

अगले कदम? प्रतिस्थापित फ़ॉन्ट्स को सीधे दस्तावेज़ में एम्बेड करने की कोशिश करें (`doc.getFontInfos().add(...)`) ताकि अंतिम फ़ाइल वास्तव में सेल्फ‑कंटेन्ड हो, या चेतावनी रिपोर्ट को मॉनिटरिंग डैशबोर्ड में इंटीग्रेट करें। आप **डॉक्यूमेंट प्रोसेसिंग जावा**, **Aspose.Words फ़ॉन्ट सब्स्टीट्यूशन चेतावनी**, और **जावा LoadOptions चेतावनी कॉलबैक** जैसे संबंधित विषयों को भी एक्सप्लोर कर सकते हैं ताकि अपनी विशेषज्ञता को गहरा कर सकें।

हैप्पी कोडिंग, और आपके दस्तावेज़ हमेशा वही फ़ॉन्ट्स रेंडर करें जिसकी आप उम्मीद करते हैं!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}