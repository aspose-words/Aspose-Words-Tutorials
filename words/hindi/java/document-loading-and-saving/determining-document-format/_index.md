---
date: 2025-12-20
description: जावा में Aspose.Words के साथ फ़ाइलों को प्रकार के अनुसार व्यवस्थित करना
  और दस्तावेज़ फ़ॉर्मेट का पता लगाना सीखें। DOC, DOCX, RTF और अधिक का समर्थन करता
  है।
linktitle: Determining Document Format
second_title: Aspose.Words Java Document Processing API
title: Aspose.Words for Java का उपयोग करके फ़ाइलों को प्रकार के अनुसार व्यवस्थित करें
url: /hi/java/document-loading-and-saving/determining-document-format/
weight: 25
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for Java का उपयोग करके फ़ाइलों को प्रकार के अनुसार व्यवस्थित करें

जब आपको Java एप्लिकेशन में **फ़ाइलों को प्रकार के अनुसार व्यवस्थित** करने की आवश्यकता होती है, तो पहला कदम प्रत्येक दस्तावेज़ के फ़ॉर्मेट को विश्वसनीय रूप से निर्धारित करना होता है। Aspose.Words for Java इसे सरल बनाता है, जिससे आप DOC, DOCX, RTF, HTML, ODT और कई अन्य फ़ॉर्मेट – यहाँ तक कि एन्क्रिप्टेड या अज्ञात फ़ाइलें – का पता लगा सकते हैं। इस गाइड में हम फ़ोल्डर सेटअप, फ़ाइल फ़ॉर्मेट का पता लगाने, और फ़ाइलों को स्वचालित रूप से सॉर्ट करने की प्रक्रिया को चरण-दर-चरण देखेंगे।

## त्वरित उत्तर
- **“फ़ाइलों को प्रकार के अनुसार व्यवस्थित” का क्या अर्थ है?** इसका मतलब है कि दस्तावेज़ों को उनके पहचाने गए फ़ॉर्मेट (जैसे DOCX, PDF, RTF) के आधार पर स्वचालित रूप से फ़ोल्डरों में ले जाना।  
- **Java में फ़ाइल फ़ॉर्मेट का पता लगाने के लिए कौन सी लाइब्रेरी मदद करती है?** Aspose.Words for Java `FileFormatUtil.detectFileFormat()` प्रदान करता है।  
- **क्या API अज्ञात फ़ाइल प्रकारों की पहचान कर सकता है?** हाँ – यह असमर्थित या अपरिचित फ़ाइलों के लिए `LoadFormat.UNKNOWN` लौटाता है।  
- **क्या एन्क्रिप्टेड दस्तावेज़ की पहचान समर्थित है?** बिल्कुल; `FileFormatInfo.isEncrypted()` फ़्लैग आपको बताता है कि फ़ाइल पासवर्ड‑सुरक्षित है या नहीं।  
- **क्या उत्पादन उपयोग के लिए लाइसेंस आवश्यक है?** व्यावसायिक डिप्लॉयमेंट के लिए एक वैध Aspose.Words लाइसेंस आवश्यक है।

## परिचय: Aspose.Words for Java के साथ फ़ाइलों को प्रकार के अनुसार व्यवस्थित करें

Java में दस्तावेज़ प्रोसेसिंग के साथ काम करते समय, आप जिन फ़ाइलों को संभाल रहे हैं उनके फ़ॉर्मेट को निर्धारित करना अत्यंत महत्वपूर्ण है। Aspose.Words for Java **detect file format java** के लिए शक्तिशाली सुविधाएँ प्रदान करता है, और हम आपको फ़ाइलों को कुशलता से व्यवस्थित करने की प्रक्रिया के माध्यम से ले जाएंगे।

## आवश्यकताएँ

शुरू करने से पहले सुनिश्चित करें कि आपके पास निम्नलिखित आवश्यकताएँ हैं:

- [Aspose.Words for Java](https://releases.aspose.com/words/java/)
- आपके सिस्टम पर स्थापित Java Development Kit (JDK)
- Java प्रोग्रामिंग का बुनियादी ज्ञान

## चरण 1: डायरेक्टरी सेटअप

सबसे पहले, हमें अपनी फ़ाइलों को प्रभावी ढंग से व्यवस्थित करने के लिए आवश्यक डायरेक्टरी सेटअप करनी होगी। हम विभिन्न दस्तावेज़ प्रकारों के लिए फ़ोल्डर बनाएँगे।

```java
File supportedDir = new File("Your Directory Path" + "Supported");
File unknownDir = new File("Your Directory Path" + "Unknown");
File encryptedDir = new File("Your Directory Path" + "Encrypted");
File pre97Dir = new File("Your Directory Path" + "Pre97");

// Create the directories if they do not already exist.
if (!supportedDir.exists())
    supportedDir.mkdir();
if (!unknownDir.exists())
    unknownDir.mkdir();
if (!encryptedDir.exists())
    encryptedDir.mkdir();
if (!pre97Dir.exists())
    pre97Dir.mkdir();
```

हमने समर्थित, अज्ञात, एन्क्रिप्टेड, और प्री‑97 दस्तावेज़ प्रकारों के लिए डायरेक्टरी बनाई हैं।

## चरण 2: दस्तावेज़ फ़ॉर्मेट का पता लगाना

अब, आइए हमारे डायरेक्टरी में मौजूद दस्तावेज़ों का फ़ॉर्मेट पता लगाएँ। हम यह करने के लिए Aspose.Words for Java का उपयोग करेंगे।

```java
Set<String> listFiles = Stream.of(new File("Your Directory Path").listFiles())
    .filter(file -> !file.getName().endsWith("Corrupted document.docx") && !Files.isDirectory(file.toPath()))
    .map(File::getPath)
    .collect(Collectors.toSet());

for (String fileName : listFiles) {
    String nameOnly = Paths.get(fileName).getFileName().toString();
    System.out.println(nameOnly);
    FileFormatInfo info = FileFormatUtil.detectFileFormat(fileName);

    // Display the document type
    switch (info.getLoadFormat()) {
        case LoadFormat.DOC:
            System.out.println("\tMicrosoft Word 97-2003 document.");
            break;
        // Add cases for other document formats as needed
    }

    // Handle encrypted documents
    if (info.isEncrypted()) {
        System.out.println("\tAn encrypted document.");
        FileUtils.copyFile(new File(fileName), new File(encryptedDir, nameOnly));
    } else {
        // Handle other document types
        switch (info.getLoadFormat()) {
            case LoadFormat.DOC_PRE_WORD_60:
                FileUtils.copyFile(new File(fileName), new File(pre97Dir, nameOnly));
                break;
            case LoadFormat.UNKNOWN:
                FileUtils.copyFile(new File(fileName), new File(unknownDir, nameOnly));
                break;
            default:
                FileUtils.copyFile(new File(fileName), new File(supportedDir, nameOnly));
                break;
        }
    }
}
```

इस स्निपेट में हम फ़ाइलों के माध्यम से इटररेट करते हैं, **detect file format java**, और उन्हें उपयुक्त फ़ोल्डरों में व्यवस्थित करते हैं।

## Aspose.Words for Java में दस्तावेज़ फ़ॉर्मेट निर्धारित करने के लिए पूर्ण स्रोत कोड

```java
        File supportedDir = new File("Your Directory Path" + "Supported");
        File unknownDir = new File("Your Directory Path" + "Unknown");
        File encryptedDir = new File("Your Directory Path" + "Encrypted");
        File pre97Dir = new File("Your Directory Path" + "Pre97");
        // Create the directories if they do not already exist.
        if (supportedDir.exists() == false)
            supportedDir.mkdir();
        if (unknownDir.exists() == false)
            unknownDir.mkdir();
        if (encryptedDir.exists() == false)
            encryptedDir.mkdir();
        if (pre97Dir.exists() == false)
            pre97Dir.mkdir();
        Set<String> listFiles = Stream.of(new File("Your Directory Path").listFiles())
                .filter(file -> !file.getName().endsWith("Corrupted document.docx") && !Files.isDirectory(file.toPath()))
                .map(File::getPath)
                .collect(Collectors.toSet());
        for (String fileName : listFiles) {
            String nameOnly = Paths.get(fileName).getFileName().toString();
            System.out.println(nameOnly);
            FileFormatInfo info = FileFormatUtil.detectFileFormat(fileName);
            // Display the document type
            switch (info.getLoadFormat()) {
                case LoadFormat.DOC:
                    System.out.println("\tMicrosoft Word 97-2003 document.");
                    break;
                case LoadFormat.DOT:
                    System.out.println("\tMicrosoft Word 97-2003 template.");
                    break;
                case LoadFormat.DOCX:
                    System.out.println("\tOffice Open XML WordprocessingML Macro-Free Document.");
                    break;
                case LoadFormat.DOCM:
                    System.out.println("\tOffice Open XML WordprocessingML Macro-Enabled Document.");
                    break;
                case LoadFormat.DOTX:
                    System.out.println("\tOffice Open XML WordprocessingML Macro-Free Template.");
                    break;
                case LoadFormat.DOTM:
                    System.out.println("\tOffice Open XML WordprocessingML Macro-Enabled Template.");
                    break;
                case LoadFormat.FLAT_OPC:
                    System.out.println("\tFlat OPC document.");
                    break;
                case LoadFormat.RTF:
                    System.out.println("\tRTF format.");
                    break;
                case LoadFormat.WORD_ML:
                    System.out.println("\tMicrosoft Word 2003 WordprocessingML format.");
                    break;
                case LoadFormat.HTML:
                    System.out.println("\tHTML format.");
                    break;
                case LoadFormat.MHTML:
                    System.out.println("\tMHTML (Web archive) format.");
                    break;
                case LoadFormat.ODT:
                    System.out.println("\tOpenDocument Text.");
                    break;
                case LoadFormat.OTT:
                    System.out.println("\tOpenDocument Text Template.");
                    break;
                case LoadFormat.DOC_PRE_WORD_60:
                    System.out.println("\tMS Word 6 or Word 95 format.");
                    break;
                case LoadFormat.UNKNOWN:
                    System.out.println("\tUnknown format.");
                    break;
            }
            if (info.isEncrypted()) {
                System.out.println("\tAn encrypted document.");
                FileUtils.copyFile(new File(fileName), new File(encryptedDir, nameOnly));
            } else {
                switch (info.getLoadFormat()) {
                    case LoadFormat.DOC_PRE_WORD_60:
                        FileUtils.copyFile(new File(fileName), new File(pre97Dir, nameOnly));
                        break;
                    case LoadFormat.UNKNOWN:
                        FileUtils.copyFile(new File(fileName), new File(unknownDir, nameOnly));
                        break;
                    default:
                        FileUtils.copyFile(new File(fileName), new File(supportedDir, nameOnly));
                        break;
                }
            }
        }

```

## फ़ाइल फ़ॉर्मेट Java कैसे पता करें

`FileFormatUtil.detectFileFormat()` मेथड फ़ाइल हेडर की जाँच करता है और एक `FileFormatInfo` ऑब्जेक्ट लौटाता है। यह ऑब्जेक्ट आपको **load format**, फ़ाइल एन्क्रिप्टेड है या नहीं, और अन्य उपयोगी मेटाडेटा बताता है। इस जानकारी का उपयोग करके आप प्रोग्रामेटिक रूप से **अज्ञात फ़ाइल प्रकारों की पहचान** कर सकते हैं और प्रत्येक फ़ाइल को कैसे प्रोसेस करना है, इसका निर्णय ले सकते हैं।

## अज्ञात फ़ाइल प्रकारों की पहचान

जब API `LoadFormat.UNKNOWN` लौटाता है, तो फ़ाइल या तो भ्रष्ट है या ऐसा फ़ॉर्मेट उपयोग कर रही है जिसे Aspose.Words समर्थन नहीं करता। हमारे नमूना कोड में हम उन फ़ाइलों को **Unknown** फ़ोल्डर में ले जाते हैं ताकि आप बाद में उनका निरीक्षण कर सकें।

## सामान्य समस्याएँ और समाधान

| समस्या | कारण | समाधान |
|-------|--------|-----|
| फ़ाइलें हमेशा *Supported* फ़ोल्डर में रखी जाती हैं | `FileFormatUtil` हेडर पढ़ नहीं सका (उदा., फ़ाइल खाली है) | सुनिश्चित करें कि आप सही फ़ाइल पाथ पास कर रहे हैं और फ़ाइल शून्य‑बाइट नहीं है। |
| एन्क्रिप्टेड फ़ाइलें अपवाद फेंकती हैं | एन्क्रिप्शन को संभाले बिना पढ़ने का प्रयास | कोड में दिखाए अनुसार आगे की प्रोसेसिंग से पहले `info.isEncrypted()` जाँच का उपयोग करें। |
| Pre‑97 Word दस्तावेज़ पहचान नहीं हो रहे | पुराने फ़ॉर्मेट को `DOC_PRE_WORD_60` केस की आवश्यकता होती है | `case LoadFormat.DOC_PRE_WORD_60` ब्लॉक को रखें ताकि वे *Pre97* फ़ोल्डर में रूट हों। |

## अक्सर पूछे जाने वाले प्रश्न

### मैं Aspose.Words for Java कैसे इंस्टॉल करूँ?

आप Aspose.Words for Java को [यहाँ](https://releases.aspose.com/words/java/) से डाउनलोड कर सकते हैं और प्रदान किए गए इंस्टॉलेशन निर्देशों का पालन कर सकते हैं।

### समर्थित दस्तावेज़ फ़ॉर्मेट कौन‑से हैं?

Aspose.Words for Java विभिन्न दस्तावेज़ फ़ॉर्मेट का समर्थन करता है, जिसमें DOC, DOCX, RTF, HTML, ODT और कई अन्य शामिल हैं। पूर्ण सूची के लिए आधिकारिक दस्तावेज़ देखें।

### मैं Aspose.Words for Java का उपयोग करके एन्क्रिप्टेड दस्तावेज़ कैसे पहचानूँ?

`FileFormatUtil.detectFileFormat()` मेथड का उपयोग करें; लौटाए गए `FileFormatInfo.isEncrypted()` फ़्लैग एन्क्रिप्शन को दर्शाता है, जैसा कि इस गाइड में दिखाया गया है।

### पुराने दस्तावेज़ फ़ॉर्मेट के साथ काम करने में कोई सीमाएँ हैं क्या?

MS Word 6 या Word 95 जैसे पुराने फ़ॉर्मेट में आधुनिक सुविधाएँ नहीं हो सकतीं और संगतता समस्याएँ उत्पन्न हो सकती हैं। संभव हो तो उन्हें नए फ़ॉर्मेट में परिवर्तित करने पर विचार करें।

### क्या मैं अपने Java एप्लिकेशन में दस्तावेज़ फ़ॉर्मेट पहचान को स्वचालित कर सकता हूँ?

हाँ, प्रदान किया गया कोड अपने एप्लिकेशन की प्रोसेसिंग पाइपलाइन में एम्बेड करें। इससे पता लगाए गए फ़ॉर्मेट के आधार पर स्वचालित सॉर्टिंग और हैंडलिंग संभव हो जाएगी।

---

**Last Updated:** 2025-12-20  
**Tested With:** Aspose.Words for Java 24.12 (latest)  
**Author:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}