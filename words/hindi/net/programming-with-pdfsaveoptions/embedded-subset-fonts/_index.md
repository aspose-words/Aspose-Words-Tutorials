---
title: पीडीएफ दस्तावेज़ में सबसेट फ़ॉन्ट एम्बेड करें
linktitle: पीडीएफ दस्तावेज़ में सबसेट फ़ॉन्ट एम्बेड करें
second_title: Aspose.Words दस्तावेज़ प्रसंस्करण API
description: .NET के लिए Aspose.Words का उपयोग करके केवल आवश्यक फ़ॉन्ट उपसमूह एम्बेड करके PDF फ़ाइल का आकार कम करें। अपने PDF को कुशलतापूर्वक अनुकूलित करने के लिए हमारे चरण-दर-चरण मार्गदर्शिका का पालन करें।
weight: 10
url: /hi/net/programming-with-pdfsaveoptions/embedded-subset-fonts/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# पीडीएफ दस्तावेज़ में सबसेट फ़ॉन्ट एम्बेड करें

## परिचय

क्या आपने कभी गौर किया है कि कुछ PDF फ़ाइलें दूसरों की तुलना में बहुत बड़ी होती हैं, भले ही उनमें समान सामग्री हो? इसका दोष अक्सर फ़ॉन्ट में होता है। PDF में फ़ॉन्ट एम्बेड करने से यह सुनिश्चित होता है कि यह किसी भी डिवाइस पर एक जैसा दिखता है, लेकिन यह फ़ाइल के आकार को भी बढ़ा सकता है। सौभाग्य से, .NET के लिए Aspose.Words केवल आवश्यक फ़ॉन्ट उपसमूह एम्बेड करने के लिए एक आसान सुविधा प्रदान करता है, जिससे आपकी PDFs छोटी और कुशल बनी रहती हैं। यह ट्यूटोरियल आपको प्रक्रिया के माध्यम से, चरण-दर-चरण मार्गदर्शन करेगा।

## आवश्यक शर्तें

आरंभ करने से पहले, सुनिश्चित करें कि आपके पास निम्नलिखित हैं:

-  .NET के लिए Aspose.Words: आप इसे डाउनलोड कर सकते हैं[यहाँ](https://releases.aspose.com/words/net/).
- .NET वातावरण: सुनिश्चित करें कि आपके पास एक कार्यशील .NET विकास वातावरण है।
- C# का बुनियादी ज्ञान: C# प्रोग्रामिंग से परिचित होने से आपको आगे बढ़ने में मदद मिलेगी।

## नामस्थान आयात करें

.NET के लिए Aspose.Words का उपयोग करने के लिए, आपको अपने प्रोजेक्ट में आवश्यक नेमस्पेस आयात करने की आवश्यकता है। इन्हें अपनी C# फ़ाइल के शीर्ष पर जोड़ें:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;
```

## चरण 1: दस्तावेज़ लोड करें

 सबसे पहले, हमें उस वर्ड डॉक्यूमेंट को लोड करना होगा जिसे हम पीडीएफ में बदलना चाहते हैं।`Document` Aspose.Words द्वारा प्रदान किया गया वर्ग.

```csharp
// दस्तावेज़ निर्देशिका का पथ.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Rendering.docx");
```

 यह कोड स्निपेट यहां स्थित दस्तावेज़ को लोड करता है`dataDir` . प्रतिस्थापित करना सुनिश्चित करें`"YOUR DOCUMENT DIRECTORY"` आपके दस्तावेज़ के वास्तविक पथ के साथ.

## चरण 2: पीडीएफ सेव विकल्प कॉन्फ़िगर करें

 इसके बाद, हम कॉन्फ़िगर करते हैं`PdfSaveOptions` यह सुनिश्चित करने के लिए कि केवल आवश्यक फ़ॉन्ट उपसमूह ही एम्बेड किए गए हैं।`EmbedFullFonts` को`false`, हम Aspose.Words को केवल दस्तावेज़ में उपयोग किए गए ग्लिफ़ को एम्बेड करने के लिए कहते हैं।

```csharp
// आउटपुट पीडीएफ में दस्तावेज़ के फ़ॉन्ट्स के उपसमूह शामिल होंगे।
// दस्तावेज़ में प्रयुक्त ग्लिफ़ को ही पीडीएफ फ़ॉन्ट में शामिल किया गया है।
PdfSaveOptions saveOptions = new PdfSaveOptions { EmbedFullFonts = false };
```

यह छोटा लेकिन महत्वपूर्ण कदम पीडीएफ फाइल के आकार को काफी कम करने में मदद करता है।

## चरण 3: दस्तावेज़ को PDF के रूप में सहेजें

 अंत में, हम दस्तावेज़ को PDF के रूप में सहेजते हैं`Save` विधि, कॉन्फ़िगर लागू करना`PdfSaveOptions`.

```csharp
doc.Save(dataDir + "WorkingWithPdfSaveOptions.EmbedSubsetFonts.pdf", saveOptions);
```

 यह कोड नाम के साथ एक पीडीएफ फाइल उत्पन्न करेगा`WorkingWithPdfSaveOptions.EmbedSubsetFonts.pdf` निर्दिष्ट निर्देशिका में, केवल आवश्यक फ़ॉन्ट उपसमूहों को एम्बेड किया जाएगा।

## निष्कर्ष

और अब यह हो गया! इन सरल चरणों का पालन करके, आप .NET के लिए Aspose.Words का उपयोग करके केवल आवश्यक फ़ॉन्ट उपसमूह एम्बेड करके अपनी PDF फ़ाइलों के आकार को कुशलतापूर्वक कम कर सकते हैं। यह न केवल स्टोरेज स्पेस बचाता है बल्कि तेज़ लोड समय और बेहतर प्रदर्शन भी सुनिश्चित करता है, खासकर व्यापक फ़ॉन्ट वाले दस्तावेज़ों के लिए।

## अक्सर पूछे जाने वाले प्रश्न

### मुझे पीडीएफ में केवल फ़ॉन्ट उपसमूह ही क्यों एम्बेड करना चाहिए?
केवल आवश्यक फ़ॉन्ट उपसमूहों को एम्बेड करने से दस्तावेज़ की उपस्थिति और पठनीयता से समझौता किए बिना पीडीएफ फ़ाइल का आकार काफी कम किया जा सकता है।

### यदि आवश्यक हो तो क्या मैं पूर्ण फ़ॉन्ट एम्बेड करने की सुविधा पुनः प्राप्त कर सकता हूँ?
 हाँ, आप कर सकते हैं। बस सेट करें`EmbedFullFonts`संपत्ति को`true` में`PdfSaveOptions`.

### क्या Aspose.Words for .NET अन्य PDF अनुकूलन सुविधाओं का समर्थन करता है?
बिल्कुल! Aspose.Words for .NET पीडीएफ को अनुकूलित करने के लिए कई विकल्प प्रदान करता है, जिसमें छवि संपीड़न और अप्रयुक्त वस्तुओं को हटाना शामिल है।

### .NET के लिए Aspose.Words का उपयोग करके किस प्रकार के फ़ॉन्ट को एम्बेड किया जा सकता है?
.NET के लिए Aspose.Words दस्तावेज़ में प्रयुक्त सभी ट्रूटाइप फ़ॉन्ट के लिए सबसेट एम्बेडिंग का समर्थन करता है।

### मैं कैसे सत्यापित कर सकता हूं कि मेरे पीडीएफ में कौन से फ़ॉन्ट एम्बेडेड हैं?
आप पीडीएफ को एडोब एक्रोबेट रीडर में खोल सकते हैं और एम्बेडेड फ़ॉन्ट्स को देखने के लिए फ़ॉन्ट्स टैब के अंतर्गत गुणों की जांच कर सकते हैं।

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
