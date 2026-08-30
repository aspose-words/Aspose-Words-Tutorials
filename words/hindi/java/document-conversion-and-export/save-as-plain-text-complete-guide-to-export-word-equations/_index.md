---
category: general
date: 2026-05-30
description: जाने कैसे प्लेन टेक्स्ट के रूप में सेव करें और समीकरणों को संरक्षित रखते
  हुए docx को txt में बदलें। चरण‑दर‑चरण जावा उदाहरण जिसमें वर्ड समीकरणों को निर्यात
  किया गया है।
draft: false
keywords:
- save as plain text
- convert docx to txt
- export word equations
- save word as txt
- convert word with equations
language: hi
og_description: 'सादा टेक्स्ट के रूप में सहेजें ट्यूटोरियल: docx को txt में बदलें,
  वर्ड समीकरण निर्यात करें, और Aspose.Words का उपयोग करके वर्ड को txt के रूप में सहेजें।'
og_title: सादा पाठ के रूप में सहेजें – जावा में वर्ड समीकरण निर्यात करें
schemas:
- author: Aspose
  dateModified: '2026-05-30'
  description: Learn how to save as plain text and convert docx to txt while preserving
    equations. Step‑by‑step Java example with export word equations.
  headline: save as plain text – Complete Guide to Export Word Equations
  type: TechArticle
- description: Learn how to save as plain text and convert docx to txt while preserving
    equations. Step‑by‑step Java example with export word equations.
  name: save as plain text – Complete Guide to Export Word Equations
  steps:
  - name: Expected Output
    text: 'Open `MathSample.txt` in any editor and you’ll see something like:'
  - name: What if the target system doesn’t support Unicode?
    text: 'If you need an ASCII‑only fallback, switch the export mode to `OfficeMathExportMode.TEXT`.
      The equations will be rendered as plain text approximations (e.g., “sum(i=1
      to n) i”). Just replace the line:'
  - name: Can I batch‑process a folder of DOCX files?
    text: Absolutely. Wrap the loading and saving logic inside a `File[] files = new
      File("inputFolder").listFiles();` loop. Remember to handle exceptions per file
      to avoid the whole batch stopping on a single corrupt document.
  - name: What about tables or images?
    text: '`TxtSaveOptions` strips non‑text elements by design. If you need a richer
      export (e.g., CSV for tables), consider `CsvSaveOptions` instead. Images are
      omitted because plain text cannot embed binary data.'
  type: HowTo
tags:
- Java
- Aspose.Words
- Document Conversion
title: सादा पाठ के रूप में सहेजें – वर्ड समीकरण निर्यात करने की संपूर्ण गाइड
url: /hi/java/document-conversion-and-export/save-as-plain-text-complete-guide-to-export-word-equations/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# सादे टेक्स्ट के रूप में सहेजें – समीकरणों के साथ DOCX को बदलने के लिए फुल‑स्टैक ट्यूटोरियल

क्या आपको कभी **सादे टेक्स्ट के रूप में सहेजने** की ज़रूरत पड़ी, लेकिन आपका Word फ़ाइल गणितीय फ़ॉर्मूले रखता है जो बिगड़ जाते हैं? आप अकेले नहीं हैं। चाहे आप शोध पत्रों को संग्रहित कर रहे हों, सर्च इंडेक्स को फ़ीड कर रहे हों, या सिर्फ़ एक अनुबंध का हल्का संस्करण चाहिए, चुनौती यह है कि OfficeMath ऑब्जेक्ट्स को रूपांतरण के बाद भी पढ़ने योग्य रखा जाए।

अधिकांश साधारण कन्वर्टर समीकरण के glyph को अपठनीय प्रतीकों के रूप में डंप कर देते हैं। इस गाइड में हम आपको दिखाएंगे कि **docx को txt में कैसे बदलें** जबकि समीकरणों को Unicode के रूप में संरक्षित रखें, यानी *Word समीकरणों को निर्यात* करने का एक साफ़, खोज योग्य फ़ॉर्मेट। अंत तक आपके पास एक तैयार‑चलाने‑योग्य Java स्निपेट होगा जो **शब्द को txt के रूप में सहेजता** है बिना गणित खोए।

## इस ट्यूटोरियल में क्या कवर किया गया है

- आवश्यक निर्भरताएँ (Aspose.Words for Java)  
- निर्यात मोड को नियंत्रित करने के लिए **TxtSaveOptions** सेट करना  
- एक पूर्ण, चलाने योग्य Java प्रोग्राम जो **समीकरणों के साथ शब्द को बदलता** है सुरक्षित रूप से  
- सामान्य समस्याएँ (फ़ॉन्ट मुद्दे, Unicode समर्थन की कमी) और उन्हें कैसे टालें  
- अगले कदम: लाइन ब्रेक को समायोजित करना, तालिकाओं को संभालना, और बैच प्रोसेसिंग  

कोई बाहरी दस्तावेज़ लिंक आवश्यक नहीं—सभी आवश्यक जानकारी यहाँ ही है।

## पूर्वापेक्षाएँ

- आपके मशीन पर Java 8 या नया स्थापित हो  
- निर्भरताओं के प्रबंधन के लिए Maven या Gradle (उदाहरण में हम Maven उपयोग करेंगे)  
- एक DOCX फ़ाइल जिसमें कम से कम एक OfficeMath ऑब्जेक्ट (समीकरण) हो  

यदि आपके पास ये सब है, तो चलिए शुरू करते हैं।

## चरण 1: Aspose.Words निर्भरता जोड़ें

सबसे पहले, Aspose.Words for Java लाइब्रेरी को प्राप्त करें। यह एक व्यावसायिक उत्पाद है, लेकिन वे विकास के लिए एक मुफ्त अस्थायी लाइसेंस प्रदान करते हैं।

```xml
<!-- pom.xml -->
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version>
</dependency>
```

> **प्रो टिप:** यदि आप Maven का उपयोग नहीं कर रहे हैं, तो `aspose-words-24.9.jar` को अपने क्लासपाथ पर रखें।

## चरण 2: स्रोत दस्तावेज़ लोड करें

अब हम **स्रोत दस्तावेज़ को लोड** करेंगे। `Document` क्लास किसी भी Word फ़ॉर्मेट को पढ़ता है, जिसमें एम्बेडेड समीकरणों वाला `.docx` भी शामिल है।

```java
import com.aspose.words.Document;
import com.aspose.words.SaveFormat;

public class DocxToTxtConverter {
    public static void main(String[] args) throws Exception {
        // Step 1: Load the source document
        Document document = new Document("YOUR_DIRECTORY/input.docx");
        // ... we'll add the save logic next
    }
}
```

ध्यान दें कि वेरिएबल नाम `document` शब्द फ़ाइल की अवधारणा को दर्शाता है, जिससे कोड स्वयं‑स्पष्टीकरण बन जाता है।

## चरण 3: समीकरण निर्यात के लिए TxtSaveOptions कॉन्फ़िगर करें

**export word equations** कार्यप्रवाह का दिल `TxtSaveOptions` में है। डिफ़ॉल्ट रूप से Aspose OfficeMath को हटा देता है, लेकिन हम इसे `OfficeMathExportMode.UNICODE` के साथ बदल सकते हैं।

```java
import com.aspose.words.TxtSaveOptions;
import com.aspose.words.OfficeMathExportMode;

// Inside main after loading the document
TxtSaveOptions txtSaveOptions = new TxtSaveOptions();
txtSaveOptions.setOfficeMathExportMode(OfficeMathExportMode.UNICODE);
```

मोड को `UNICODE` सेट करने से Aspose प्रत्येक समीकरण को उसके Unicode प्रतिनिधित्व (जैसे “∑”, “√”) में रेंडर करता है। यही कारण है कि सादे‑टेक्स्ट फ़ाइल अभी भी *पढ़ने योग्य* और टूल्स द्वारा खोज योग्य रहती है।

## चरण 4: दस्तावेज़ को सादे टेक्स्ट के रूप में सहेजें

अंत में, हम कॉन्फ़िगर किए गए विकल्पों के साथ **सादे टेक्स्ट के रूप में सहेजते** हैं। यही वह चरण है जहाँ मुख्य कीवर्ड वास्तव में चमकता है।

```java
// Step 4: Save the document as a plain‑text file with the configured options
document.save("YOUR_DIRECTORY/MathSample.txt", txtSaveOptions);
System.out.println("Conversion complete! File saved as plain text.");
```

वह एक‑लाइनर भारी काम कर देता है: यह एक `.txt` फ़ाइल लिखता है, समीकरणों को रखता है, और लाइन ब्रेक का सम्मान करता है। अब आपने सफलतापूर्वक **docx को txt में बदल दिया** है जबकि गणित को संरक्षित रखा।

## पूर्ण कार्यशील उदाहरण

सब कुछ मिलाकर, यहाँ पूरा प्रोग्राम है जिसे आप अपने IDE में कॉपी‑पेस्ट कर सकते हैं।

```java
import com.aspose.words.Document;
import com.aspose.words.TxtSaveOptions;
import com.aspose.words.OfficeMathExportMode;

public class DocxToTxtConverter {
    public static void main(String[] args) throws Exception {
        // Load the DOCX that contains equations
        Document document = new Document("YOUR_DIRECTORY/input.docx");

        // Prepare TXT save options: export OfficeMath as Unicode
        TxtSaveOptions txtSaveOptions = new TxtSaveOptions();
        txtSaveOptions.setOfficeMathExportMode(OfficeMathExportMode.UNICODE);

        // Save as plain text
        document.save("YOUR_DIRECTORY/MathSample.txt", txtSaveOptions);

        System.out.println("Conversion complete! File saved as plain text.");
    }
}
```

### अपेक्षित आउटपुट

`MathSample.txt` को किसी भी एडिटर में खोलें और आपको कुछ इस तरह दिखेगा:

```
This is a sample paragraph.
∑_{i=1}^{n} i = n(n+1)/2
Another line of text.
```

समीकरण एक उचित Unicode सम प्रतीक के रूप में प्रदर्शित होता है, यह साबित करता है कि **export word equations** फ़्लैग काम किया।

## सामान्य प्रश्न एवं किनारे के मामले

### यदि लक्ष्य प्रणाली Unicode का समर्थन नहीं करती तो क्या करें?

यदि आपको केवल ASCII‑only फॉलबैक चाहिए, तो निर्यात मोड को `OfficeMathExportMode.TEXT` में बदलें। समीकरण साधारण टेक्स्ट अनुमान (जैसे “sum(i=1 to n) i”) के रूप में रेंडर होंगे। बस इस पंक्ति को बदलें:

```java
txtSaveOptions.setOfficeMathExportMode(OfficeMathExportMode.TEXT);
```

### क्या मैं DOCX फ़ाइलों के फ़ोल्डर को बैच‑प्रोसेस कर सकता हूँ?

बिल्कुल। लोडिंग और सेविंग लॉजिक को `File[] files = new File("inputFolder").listFiles();` लूप के अंदर रखें। प्रत्येक फ़ाइल के लिए अपवादों को संभालें ताकि एक ही खराब दस्तावेज़ पर पूरी बैच रुक न जाए।

### तालिकाएँ या छवियों के बारे में क्या?

`TxtSaveOptions` डिज़ाइन के अनुसार गैर‑टेक्स्ट तत्वों को हटा देता है। यदि आपको richer निर्यात चाहिए (जैसे तालिकाओं के लिए CSV), तो `CsvSaveOptions` पर विचार करें। छवियों को छोड़ दिया जाता है क्योंकि सादे टेक्स्ट बाइनरी डेटा एम्बेड नहीं कर सकता।

## विश्वसनीय रूपांतरणों के लिए प्रो टिप्स

- **लाइसेंस पहले से**: Aspose 30 दिन बाद बिना लाइसेंस के चलाने पर चेतावनी देगा। `License license = new License(); license.setLicense("Aspose.Words.lic");` को `main` की शुरुआत में जोड़ें।  
- **UTF‑8 एन्कोडिंग**: लाइब्रेरी डिफ़ॉल्ट रूप से UTF‑8 लिखती है। यदि आपको अलग कोड पेज चाहिए, तो `txtSaveOptions.setEncoding(Encoding.getEncoding("windows-1252"));` सेट करें।  
- **लाइन एंडिंग्स**: Windows‑स्टाइल CRLF के लिए `txtSaveOptions.setSaveFormat(SaveFormat.TEXT);` कॉल करें (डिफ़ॉल्ट पहले से ही प्लेटफ़ॉर्म‑विशिष्ट लाइन एंडिंग्स उपयोग करता है)।

## दृश्य अवलोकन

![save as plain text workflow diagram](placeholder.png){alt="सादे टेक्स्ट के रूप में सहेजने की कार्यप्रवाह दिखाता है, जिसमें लोड, विकल्प कॉन्फ़िगर, और सहेजना चरण शामिल हैं"}

यह चित्र उन तीन‑चरणीय पाइपलाइन को दर्शाता है जिसे हमने अभी कोड किया: लोड → कॉन्फ़िगर → सहेजें।

## निष्कर्ष

अब आप जानते हैं कि **सादे टेक्स्ट के रूप में सहेजें** कैसे करें जबकि **docx को txt में बदलें** और हर समीकरण को बरकरार रखें। मुख्य बात थी `TxtSaveOptions` को `OfficeMathExportMode.UNICODE` के साथ कॉन्फ़िगर करना, जिससे आप **export word equations** को एक साफ़, खोज योग्य फ़ॉर्मेट में प्राप्त कर सकते हैं। इस बुनियाद के साथ आप आसानी से **शब्द को txt के रूप में सहेज** सकते हैं, फ़ोल्डर को बैच‑प्रोसेस कर सकते हैं, या विभिन्न वातावरणों के लिए निर्यात मोड को समायोजित कर सकते हैं।

अगला क्या? एक कमांड‑लाइन इंटरफ़ेस जोड़ें ताकि उपयोगकर्ता टूल को किसी भी फ़ोल्डर की ओर इंगित कर सकें, या तालिकाओं को CSV फ़ाइलों में निकालने के लिए `CsvSaveOptions` के साथ प्रयोग करें। **समीकरणों के साथ शब्द को बदलने** की संभावनाएँ अनंत हैं, और अब आपके पास एक ठोस, उद्धरण‑योग्य प्रारंभिक बिंदु है।

हैप्पी कोडिंग, और आपकी सादे‑टेक्स्ट रूपांतरणें हमेशा लोसलेस रहें!

## आप आगे क्या सीखें?

- [Save Document as TXT – Quick Guide to Exporting Word Math](/words/english/java/document-conversion-and-export/save-document-as-txt-quick-guide-to-exporting-word-math/)
- [Convert docx to markdown – Export Math Equations to LaTeX with Aspose.Words](/words/english/java/document-conversion-and-export/convert-docx-to-markdown-export-math-equations-to-latex-with/)
- [How to Export LaTeX from Word: Convert DOCX to Markdown & Save as PDF](/words/english/java/document-conversion-and-export/how-to-export-latex-from-word-convert-docx-to-markdown-save/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}