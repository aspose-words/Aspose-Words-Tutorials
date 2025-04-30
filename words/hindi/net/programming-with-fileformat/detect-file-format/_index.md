---
"description": "इस व्यापक, चरण-दर-चरण मार्गदर्शिका के साथ .NET के लिए Aspose.Words का उपयोग करके दस्तावेज़ फ़ाइल स्वरूपों का पता लगाना सीखें।"
"linktitle": "दस्तावेज़ फ़ाइल स्वरूप का पता लगाएँ"
"second_title": "Aspose.Words दस्तावेज़ प्रसंस्करण API"
"title": "दस्तावेज़ फ़ाइल स्वरूप का पता लगाएँ"
"url": "/hi/net/programming-with-fileformat/detect-file-format/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# दस्तावेज़ फ़ाइल स्वरूप का पता लगाएँ

## परिचय

आज की डिजिटल दुनिया में, विभिन्न दस्तावेज़ प्रारूपों को कुशलतापूर्वक प्रबंधित करना महत्वपूर्ण है। चाहे आप Word, PDF, HTML या अन्य प्रारूपों को संभाल रहे हों, इन फ़ाइलों को सही ढंग से पहचानना और संसाधित करना आपका बहुत समय और प्रयास बचा सकता है। इस ट्यूटोरियल में, हम .NET के लिए Aspose.Words का उपयोग करके दस्तावेज़ फ़ाइल प्रारूपों का पता लगाने का तरीका जानेंगे। यह मार्गदर्शिका आपको आवश्यक सभी चीज़ों से परिचित कराएगी, जिसमें पूर्वापेक्षाओं से लेकर विस्तृत चरण-दर-चरण मार्गदर्शिका तक शामिल है।

## आवश्यक शर्तें

इससे पहले कि हम कोड में उतरें, आइए सुनिश्चित करें कि आपके पास वह सब कुछ है जो आपको चाहिए:

- .NET के लिए Aspose.Words: आप इसे यहाँ से डाउनलोड कर सकते हैं [यहाँ](https://releases.aspose.com/words/net/)सुनिश्चित करें कि आपके पास वैध लाइसेंस है। यदि नहीं, तो आप एक वैध लाइसेंस प्राप्त कर सकते हैं। [अस्थायी लाइसेंस](https://purchase.aspose.com/temporary-license/).
- विजुअल स्टूडियो: कोई भी नवीनतम संस्करण ठीक काम करेगा।
- .NET फ्रेमवर्क: सुनिश्चित करें कि आपके पास सही संस्करण स्थापित है।

## नामस्थान आयात करें

आरंभ करने के लिए, आपको अपने प्रोजेक्ट में आवश्यक नामस्थान आयात करने होंगे:

```csharp
using Aspose.Words;
using Aspose.Words.FileFormats;
using Aspose.Words.FileFormats.Util;
using System;
using System.Collections.Generic;
using System.IO;
using System.Linq;
```

आइये इस उदाहरण को कई चरणों में विभाजित करें ताकि इसका अनुसरण करना आसान हो जाए।

## चरण 1: निर्देशिकाएँ सेट करें

सबसे पहले, हमें निर्देशिकाएं स्थापित करनी होंगी जहां फाइलों को उनके प्रारूप के आधार पर क्रमबद्ध किया जाएगा।

```csharp
// दस्तावेज़ निर्देशिका का पथ.
string dataDir = "YOUR DOCUMENT DIRECTORY";
string supportedDir = dataDir + "Supported";
string unknownDir = dataDir + "Unknown";
string encryptedDir = dataDir + "Encrypted";
string pre97Dir = dataDir + "Pre97";

// यदि निर्देशिकाएं पहले से मौजूद नहीं हैं तो उन्हें बनाएं।
if (!Directory.Exists(supportedDir))
    Directory.CreateDirectory(supportedDir);
if (!Directory.Exists(unknownDir))
    Directory.CreateDirectory(unknownDir);
if (!Directory.Exists(encryptedDir))
    Directory.CreateDirectory(encryptedDir);
if (!Directory.Exists(pre97Dir))
    Directory.CreateDirectory(pre97Dir);
```

## चरण 2: फ़ाइलों की सूची प्राप्त करें

इसके बाद, हम निर्देशिका से फ़ाइलों की एक सूची प्राप्त करेंगे, जिसमें कोई भी दूषित दस्तावेज़ शामिल नहीं होगा।

```csharp
IEnumerable<string> fileList = Directory.GetFiles(dataDir).Where(name => !name.EndsWith("Corrupted document.docx"));
```

## चरण 3: फ़ाइल स्वरूपों का पता लगाएं

अब, हम प्रत्येक फ़ाइल को दोहराते हैं और Aspose.Words का उपयोग करके उसके प्रारूप का पता लगाते हैं।

```csharp
foreach (string fileName in fileList)
{
    string nameOnly = Path.GetFileName(fileName);

    Console.Write(nameOnly);

    FileFormatInfo info = FileFormatUtil.DetectFileFormat(fileName);

    // दस्तावेज़ प्रकार प्रदर्शित करें
    switch (info.LoadFormat)
    {
        case LoadFormat.Doc:
            Console.WriteLine("\tMicrosoft Word 97-2003 document.");
            break;
        case LoadFormat.Dot:
            Console.WriteLine("\tMicrosoft Word 97-2003 template.");
            break;
        case LoadFormat.Docx:
            Console.WriteLine("\tOffice Open XML WordprocessingML Macro-Free Document.");
            break;
        case LoadFormat.Docm:
            Console.WriteLine("\tOffice Open XML WordprocessingML Macro-Enabled Document.");
            break;
        case LoadFormat.Dotx:
            Console.WriteLine("\tOffice Open XML WordprocessingML Macro-Free Template.");
            break;
        case LoadFormat.Dotm:
            Console.WriteLine("\tOffice Open XML WordprocessingML Macro-Enabled Template.");
            break;
        case LoadFormat.FlatOpc:
            Console.WriteLine("\tFlat OPC document.");
            break;
        case LoadFormat.Rtf:
            Console.WriteLine("\tRTF format.");
            break;
        case LoadFormat.WordML:
            Console.WriteLine("\tMicrosoft Word 2003 WordprocessingML format.");
            break;
        case LoadFormat.Html:
            Console.WriteLine("\tHTML format.");
            break;
        case LoadFormat.Mhtml:
            Console.WriteLine("\tMHTML (Web archive) format.");
            break;
        case LoadFormat.Odt:
            Console.WriteLine("\tOpenDocument Text.");
            break;
        case LoadFormat.Ott:
            Console.WriteLine("\tOpenDocument Text Template.");
            break;
        case LoadFormat.DocPreWord60:
            Console.WriteLine("\tMS Word 6 or Word 95 format.");
            break;
        case LoadFormat.Unknown:
            Console.WriteLine("\tUnknown format.");
            break;
    }

    if (info.IsEncrypted)
    {
        Console.WriteLine("\tAn encrypted document.");
        File.Copy(fileName, Path.Combine(encryptedDir, nameOnly), true);
    }
    else
    {
        switch (info.LoadFormat)
        {
            case LoadFormat.DocPreWord60:
                File.Copy(fileName, Path.Combine(pre97Dir, nameOnly), true);
                break;
            case LoadFormat.Unknown:
                File.Copy(fileName, Path.Combine(unknownDir, nameOnly), true);
                break;
            default:
                File.Copy(fileName, Path.Combine(supportedDir, nameOnly), true);
                break;
        }
    }
}
```

## निष्कर्ष

.NET के लिए Aspose.Words का उपयोग करके दस्तावेज़ फ़ाइल स्वरूपों का पता लगाना एक सीधी प्रक्रिया है। अपनी निर्देशिकाएँ सेट करके, अपनी फ़ाइलों की सूची प्राप्त करके, और फ़ाइल स्वरूपों का पता लगाने के लिए Aspose.Words का उपयोग करके, आप अपने दस्तावेज़ों को कुशलतापूर्वक व्यवस्थित और प्रबंधित कर सकते हैं। यह दृष्टिकोण न केवल समय बचाता है बल्कि यह भी सुनिश्चित करता है कि आप विभिन्न दस्तावेज़ स्वरूपों को सही ढंग से संभालें।

## अक्सर पूछे जाने वाले प्रश्न

### .NET के लिए Aspose.Words क्या है?
Aspose.Words for .NET, Word दस्तावेज़ों के साथ प्रोग्रामेटिक रूप से काम करने के लिए एक शक्तिशाली लाइब्रेरी है। यह डेवलपर्स को विभिन्न प्रारूपों में दस्तावेज़ बनाने, संशोधित करने और परिवर्तित करने की अनुमति देता है।

### क्या Aspose.Words एन्क्रिप्टेड दस्तावेज़ों का पता लगा सकता है?
हां, Aspose.Words यह पता लगा सकता है कि कोई दस्तावेज़ एन्क्रिप्टेड है या नहीं और आप ऐसे दस्तावेज़ों को तदनुसार संभाल सकते हैं।

### Aspose.Words किन प्रारूपों का पता लगा सकता है?
Aspose.Words DOC, DOCX, RTF, HTML, MHTML, ODT, और कई अन्य सहित प्रारूपों की एक विस्तृत श्रृंखला का पता लगा सकता है।

### मैं Aspose.Words के लिए अस्थायी लाइसेंस कैसे प्राप्त कर सकता हूं?
आप अस्थायी लाइसेंस प्राप्त कर सकते हैं [Aspose खरीद](https://purchase.aspose.com/temporary-license/) पृष्ठ.

### मैं Aspose.Words के लिए दस्तावेज़ कहां पा सकता हूं?
Aspose.Words के लिए दस्तावेज़ यहां पाया जा सकता है [यहाँ](https://reference.aspose.com/words/net/).



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}