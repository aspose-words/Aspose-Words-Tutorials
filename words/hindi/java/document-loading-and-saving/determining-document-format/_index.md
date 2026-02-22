---
date: 2026-02-22
description: Aspose.Words के साथ जावा में दस्तावेज़ फ़ॉर्मेट का पता लगाना सीखें और
  फ़ॉर्मेट के आधार पर फ़ाइलों को स्वचालित रूप से स्थानांतरित करें। DOC, DOCX और अन्य
  की पहचान करें।
linktitle: Determining Document Format
second_title: Aspose.Words Java Document Processing API
title: Aspose.Words for Java का उपयोग करके जावा में दस्तावेज़ फ़ॉर्मेट का पता लगाएँ
url: /hi/java/document-loading-and-saving/determining-document-format/
weight: 25
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for Java का उपयोग करके Java में दस्तावेज़ फ़ॉर्मेट का पता लगाएँ

जब आपको बैच में फ़ाइलों के लिए **detect document format java** करने की आवश्यकता होती है, तो उन्हें स्वचालित रूप से सही फ़ोल्डरों में व्यवस्थित करने की क्षमता मैन्युअल काम के कई घंटे बचा सकती है। इस ट्यूटोरियल में हम दिखाएंगे कि Aspose.Words for Java कैसे Word, RTF, HTML, ODT और कई अन्य फ़ॉर्मेट को आसानी से पहचानता है, और फिर **move files by format** करके व्यवस्थित डायरेक्टरीज़ में रखता है।

## Quick Answers
- **What does “detect document format java” mean?** यह प्रक्रिया Java कोड का उपयोग करके फ़ाइल के Word प्रोसेसिंग फ़ॉर्मेट (DOC, DOCX, RTF आदि) को प्रोग्रामेटिक रूप से पहचानने की है।  
- **Which library provides this capability?** Aspose.Words for Java `FileFormatUtil.detectFileFormat` API प्रदान करता है।  
- **Can the utility also handle encrypted files?** हाँ – `FileFormatInfo.isEncrypted()` फ़्लैग बताता है कि दस्तावेज़ पासवर्ड‑सुरक्षित है या नहीं।  
- **Do I need a license for production use?** प्रोडक्शन में गैर‑इवैल्यूएशन डिप्लॉयमेंट के लिए एक कमर्शियल Aspose.Words लाइसेंस आवश्यक है।  
- **Is it possible to move files automatically after detection?** बिल्कुल – detection परिणाम को `FileUtils.copyFile` के साथ मिलाकर फ़ाइलों को कस्टम फ़ोल्डरों में सॉर्ट किया जा सकता है।

## What is detect document format java?
`detect document format java` का अर्थ है Java कोड का उपयोग करके फ़ाइल के बाइनरी हेडर को जांचना और यह निर्धारित करना कि वह किस Word प्रोसेसिंग फ़ॉर्मेट (जैसे DOC, DOCX, ODT) से संबंधित है। Aspose.Words फ़ाइल को पूरी तरह लोड किए बिना पढ़ता है, जिससे यह ऑपरेशन तेज़ और मेमोरी‑कुशल बनता है।

## Why move files by format?
दस्तावेज़ों को उनके मूल फ़ॉर्मेट के अनुसार व्यवस्थित करने से डाउनस्ट्रीम प्रोसेसिंग आसान हो जाती है:

- **Batch conversions** सभी DOCX फ़ाइलों को एक फ़ोल्डर में रखने पर सरल हो जाती हैं।  
- **Legacy support**: आप प्री‑97 Word फ़ाइलों को विशेष हैंडलिंग के लिए अलग कर सकते हैं।  
- **Security**: एन्क्रिप्टेड दस्तावेज़ों को स्वचालित रूप से क्वारंटाइन किया जा सकता है।  

## Prerequisites

शुरू करने से पहले सुनिश्चित करें कि आपके पास है:

- [Aspose.Words for Java](https://releases.aspose.com/words/java/) (नवीनतम संस्करण डाउनलोड करें)  
- Java Development Kit (JDK) 8 या उससे ऊपर स्थापित हो  
- Java I/O और स्ट्रीम्स की बुनियादी समझ  

## Step 1: Set up directories for each format

हम पहले एक साफ़ फ़ोल्डर संरचना बनाते हैं जहाँ पहचान की गई फ़ाइलें स्थानांतरित की जाएँगी। यह वर्कफ़्लो को व्यवस्थित रखता है और बाद में नई फ़ॉर्मेट श्रेणियों को जोड़ना आसान बनाता है।

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

> **Pro tip:** प्रोडक्शन कोड में हार्ड‑कोडेड पाथ्स से बचने के लिए एब्सोल्यूट पाथ्स का उपयोग करें या बेस डायरेक्टरी को प्रॉपर्टीज़ फ़ाइल के माध्यम से कॉन्फ़िगर करें।

## Step 2: Detect the document format and move files

**detect document format java** का मुख्य भाग नीचे दिए गए लूप में स्थित है। यह प्रत्येक फ़ाइल को स्कैन करता है, उसका प्रकार निर्धारित करता है, और उपयुक्त फ़ोल्डर में कॉपी करता है।

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

`switch` ब्लॉक को आप अपनी आवश्यक सभी फ़ॉर्मेट को कवर करने के लिए विस्तारित कर सकते हैं। प्रत्येक केस एक मित्रवत संदेश प्रिंट करता है और फिर फ़ाइल को संबंधित फ़ोल्डर में ले जाता है।

## Complete source code for detecting document format java

नीचे पूरा, तैयार‑से‑चलाने वाला उदाहरण दिया गया है जो डायरेक्टरी सेटअप और डिटेक्शन लॉजिक को मिलाता है। इसे एक Java क्लास में कॉपी करें, बेस पाथ को समायोजित करें, और मिश्रित दस्तावेज़ों वाले फ़ोल्डर पर चलाएँ।

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

## Common issues and troubleshooting

| Issue | Why it happens | How to fix |
|-------|----------------|------------|
| **`FileFormatUtil.detectFileFormat` returns `UNKNOWN`** | फ़ाइल भ्रष्ट है या गैर‑Word फ़ॉर्मेट उपयोग में है। | फ़ाइल एक्सटेंशन की जाँच करें, या फ़ाइल को *Unknown* फ़ोल्डर में ले जाने के लिए एक फॉलबैक जोड़ें (नमूने में पहले से मौजूद)। |
| **Encrypted files throw an exception** | API एन्क्रिप्शन जांचने से पहले कंटेंट पढ़ने की कोशिश करता है। | किसी भी अन्य ऑपरेशन से पहले हमेशा `info.isEncrypted()` को कॉल करें। |
| **Directory creation fails on Linux** | अपर्याप्त अनुमतियाँ या पैरेंट फ़ोल्डर मौजूद नहीं है। | सुनिश्चित करें कि Java प्रोसेस के पास लिखने की अनुमति है और बेस पाथ मौजूद है। |

## Frequently Asked Questions

**Q: How do I install Aspose.Words for Java?**  
A: आप Aspose.Words for Java को [here](https://releases.aspose.com/words/java/) से डाउनलोड कर सकते हैं और प्रदान किए गए इंस्टॉलेशन निर्देशों का पालन कर सकते हैं।

**Q: What document formats are supported for detection?**  
A: Aspose.Words DOC, DOCX, DOT, DOTX, DOCM, DOTM, RTF, HTML, MHTML, ODT, OTT, FLAT_OPC, WORD_ML, और प्री‑97 फ़ॉर्मेट सहित कई अन्य फ़ॉर्मेट का पता लगा सकता है।

**Q: Can this code handle password‑protected documents?**  
A: हाँ। `FileFormatInfo.isEncrypted()` फ़्लैग एन्क्रिप्टेड फ़ाइलों की पहचान करता है, जिससे आप उन्हें खोलें बिना सुरक्षित फ़ोल्डर में ले जा सकते हैं।

**Q: Is there a performance impact when scanning large folders?**  
A: डिटेक्शन केवल फ़ाइल हेडर पढ़ता है, इसलिए हजारों फ़ाइलें भी तेज़ी से प्रोसेस हो जाती हैं। बहुत बड़े बैच के लिए पैरेलल स्ट्रीम्स पर विचार करें।

**Q: How can I extend the script to convert unsupported formats?**  
A: डिटेक्शन के बाद, आप `Document.save` को इच्छित आउटपुट फ़ॉर्मेट के साथ कॉल करके किसी भी समर्थित स्रोत प्रकार को कन्वर्ट कर सकते हैं।

## Conclusion

Aspose.Words के साथ **detect document format java** का उपयोग करके आप Word‑संबंधित फ़ाइलों को स्वचालित रूप से सॉर्ट, क्वारंटाइन या कन्वर्ट करने का भरोसेमंद तरीका प्राप्त करते हैं। नमूना कोड दिखाता है कि कैसे एक साफ़ फ़ोल्डर हाइरार्की बनाएं, प्रत्येक फ़ाइल का फ़ॉर्मेट पहचानें, और उसे उसी अनुसार ले जाएँ—जिससे आपका समय बचता है और मैन्युअल त्रुटियों में कमी आती है।

---

**Last Updated:** 2026-02-22  
**Tested With:** Aspose.Words for Java 24.12 (latest)  
**Author:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}