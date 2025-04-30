---
"description": "Aspose.Words के साथ Java में दस्तावेज़ स्वरूपों का पता लगाना सीखें। DOC, DOCX, और बहुत कुछ पहचानें। फ़ाइलों को कुशलतापूर्वक व्यवस्थित करें।"
"linktitle": "दस्तावेज़ प्रारूप का निर्धारण"
"second_title": "Aspose.Words जावा दस्तावेज़ प्रसंस्करण एपीआई"
"title": "Java के लिए Aspose.Words में दस्तावेज़ प्रारूप का निर्धारण"
"url": "/hi/java/document-loading-and-saving/determining-document-format/"
"weight": 25
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Java के लिए Aspose.Words में दस्तावेज़ प्रारूप का निर्धारण


## जावा के लिए Aspose.Words में दस्तावेज़ प्रारूप निर्धारित करने का परिचय

जावा में दस्तावेज़ प्रसंस्करण के साथ काम करते समय, यह निर्धारित करना महत्वपूर्ण है कि आप जिन फ़ाइलों से निपट रहे हैं उनका प्रारूप क्या है। Aspose.Words for Java दस्तावेज़ प्रारूपों की पहचान करने के लिए शक्तिशाली सुविधाएँ प्रदान करता है, और हम आपको प्रक्रिया के माध्यम से मार्गदर्शन करेंगे।

## आवश्यक शर्तें

शुरू करने से पहले, सुनिश्चित करें कि आपके पास निम्नलिखित पूर्वापेक्षाएँ हैं:

- [जावा के लिए Aspose.Words](https://releases.aspose.com/words/java/)
- आपके सिस्टम पर जावा डेवलपमेंट किट (JDK) स्थापित है
- जावा प्रोग्रामिंग का बुनियादी ज्ञान

## चरण 1: निर्देशिका सेटअप

सबसे पहले, हमें अपनी फ़ाइलों को प्रभावी ढंग से व्यवस्थित करने के लिए आवश्यक निर्देशिकाएँ सेट अप करनी होंगी। हम अलग-अलग दस्तावेज़ प्रकारों के लिए निर्देशिकाएँ बनाएंगे।

```java
File supportedDir = new File("Your Directory Path" + "Supported");
File unknownDir = new File("Your Directory Path" + "Unknown");
File encryptedDir = new File("Your Directory Path" + "Encrypted");
File pre97Dir = new File("Your Directory Path" + "Pre97");

// यदि निर्देशिकाएं पहले से मौजूद नहीं हैं तो उन्हें बनाएं।
if (!supportedDir.exists())
    supportedDir.mkdir();
if (!unknownDir.exists())
    unknownDir.mkdir();
if (!encryptedDir.exists())
    encryptedDir.mkdir();
if (!pre97Dir.exists())
    pre97Dir.mkdir();
```

हमने समर्थित, अज्ञात, एन्क्रिप्टेड और पूर्व-97 दस्तावेज़ प्रकारों के लिए निर्देशिकाएँ बनाई हैं।

## चरण 2: दस्तावेज़ प्रारूप का पता लगाना

अब, आइए हमारी निर्देशिकाओं में दस्तावेज़ों के प्रारूप का पता लगाएं। हम इसे प्राप्त करने के लिए जावा के लिए Aspose.Words का उपयोग करेंगे।

```java
Set<String> listFiles = Stream.of(new File("Your Directory Path").listFiles())
    .filter(file -> !file.getName().endsWith("Corrupted document.docx") && !Files.isDirectory(file.toPath()))
    .map(File::getPath)
    .collect(Collectors.toSet());

for (String fileName : listFiles) {
    String nameOnly = Paths.get(fileName).getFileName().toString();
    System.out.println(nameOnly);
    FileFormatInfo info = FileFormatUtil.detectFileFormat(fileName);

    // दस्तावेज़ प्रकार प्रदर्शित करें
    switch (info.getLoadFormat()) {
        case LoadFormat.DOC:
            System.out.println("\tMicrosoft Word 97-2003 document.");
            break;
        // आवश्यकतानुसार अन्य दस्तावेज़ प्रारूपों के लिए केस जोड़ें
    }

    // एन्क्रिप्टेड दस्तावेज़ों को संभालें
    if (info.isEncrypted()) {
        System.out.println("\tAn encrypted document.");
        FileUtils.copyFile(new File(fileName), new File(encryptedDir, nameOnly));
    } else {
        // अन्य दस्तावेज़ प्रकारों को संभालें
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

इस कोड स्निपेट में, हम फ़ाइलों को दोहराते हैं, उनके प्रारूपों का पता लगाते हैं, और उन्हें संबंधित निर्देशिकाओं में व्यवस्थित करते हैं।

## जावा के लिए Aspose.Words में दस्तावेज़ प्रारूप निर्धारित करने के लिए पूर्ण स्रोत कोड

```java
        File supportedDir = new File("Your Directory Path" + "Supported");
        File unknownDir = new File("Your Directory Path" + "Unknown");
        File encryptedDir = new File("Your Directory Path" + "Encrypted");
        File pre97Dir = new File("Your Directory Path" + "Pre97");
        // यदि निर्देशिकाएं पहले से मौजूद नहीं हैं तो उन्हें बनाएं।
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
            // दस्तावेज़ प्रकार प्रदर्शित करें
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

## निष्कर्ष

Aspose.Words for Java में दस्तावेज़ प्रारूप निर्धारित करना कुशल दस्तावेज़ प्रसंस्करण के लिए आवश्यक है। इस गाइड में बताए गए चरणों के साथ, आप दस्तावेज़ प्रकारों की पहचान कर सकते हैं और अपने Java अनुप्रयोगों में उन्हें तदनुसार संभाल सकते हैं।

## अक्सर पूछे जाने वाले प्रश्न

### मैं Java के लिए Aspose.Words कैसे स्थापित करूं?

आप Java के लिए Aspose.Words को यहाँ से डाउनलोड कर सकते हैं [यहाँ](https://releases.aspose.com/words/java/) और दिए गए स्थापना निर्देशों का पालन करें।

### समर्थित दस्तावेज़ प्रारूप क्या हैं?

Aspose.Words for Java विभिन्न दस्तावेज़ स्वरूपों का समर्थन करता है, जिसमें DOC, DOCX, RTF, HTML, और बहुत कुछ शामिल है। आप पूरी सूची के लिए दस्तावेज़ देख सकते हैं।

### मैं Java के लिए Aspose.Words का उपयोग करके एन्क्रिप्टेड दस्तावेज़ों का पता कैसे लगा सकता हूँ?

आप इसका उपयोग कर सकते हैं `FileFormatUtil.detectFileFormat()` एन्क्रिप्टेड दस्तावेजों का पता लगाने की विधि, जैसा कि इस गाइड में प्रदर्शित किया गया है।

### क्या पुराने दस्तावेज़ प्रारूपों के साथ काम करते समय कोई सीमाएँ हैं?

पुराने दस्तावेज़ प्रारूप, जैसे कि MS Word 6 या Word 95, में आधुनिक अनुप्रयोगों के साथ सुविधाओं और संगतता के संदर्भ में सीमाएँ हो सकती हैं। जब आवश्यक हो तो इन दस्तावेज़ों को अपग्रेड या परिवर्तित करने पर विचार करें।

### क्या मैं अपने जावा अनुप्रयोग में दस्तावेज़ प्रारूप पहचान को स्वचालित कर सकता हूँ?

हां, आप अपने जावा एप्लिकेशन में दिए गए कोड को एकीकृत करके दस्तावेज़ प्रारूप पहचान को स्वचालित कर सकते हैं। यह आपको उनके पहचाने गए प्रारूपों के आधार पर दस्तावेज़ों को संसाधित करने की अनुमति देता है।


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}