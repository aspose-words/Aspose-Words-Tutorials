---
title: फ़ॉन्ट फ़ोल्डर डिफ़ॉल्ट इंस्टेंस सेट करें
linktitle: फ़ॉन्ट फ़ोल्डर डिफ़ॉल्ट इंस्टेंस सेट करें
second_title: Aspose.Words दस्तावेज़ प्रसंस्करण API
description: इस चरण-दर-चरण ट्यूटोरियल के साथ Aspose.Words for .NET में डिफ़ॉल्ट इंस्टेंस के लिए फ़ॉन्ट फ़ोल्डर सेट करना सीखें। अपने Word दस्तावेज़ों को आसानी से कस्टमाइज़ करें।
weight: 10
url: /hi/net/working-with-fonts/set-fonts-folders-default-instance/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# फ़ॉन्ट फ़ोल्डर डिफ़ॉल्ट इंस्टेंस सेट करें

## परिचय

नमस्ते, साथी कोडर! यदि आप .NET में Word दस्तावेज़ों के साथ काम कर रहे हैं, तो आप शायद अपने फ़ॉन्ट को सही तरीके से रखने के महत्व को जानते होंगे। आज, हम .NET के लिए Aspose.Words का उपयोग करके डिफ़ॉल्ट इंस्टेंस के लिए फ़ॉन्ट फ़ोल्डर सेट करने के तरीके के बारे में जानेंगे। कल्पना करें कि आपके सभी कस्टम फ़ॉन्ट आपकी उंगलियों पर हों, जिससे आपके दस्तावेज़ बिल्कुल वैसे ही दिखें जैसे आप उन्हें देखना चाहते हैं। बढ़िया लगता है, है न? चलिए शुरू करते हैं!

## आवश्यक शर्तें

इससे पहले कि हम विस्तृत विवरण में उतरें, आइए सुनिश्चित करें कि आपके पास वह सब कुछ है जो आपको चाहिए:
-  Aspose.Words for .NET: सुनिश्चित करें कि आपके पास लाइब्रेरी स्थापित है। यदि नहीं, तो आप कर सकते हैं[यहाँ पर डाउनलोड करो](https://releases.aspose.com/words/net/).
- विकास वातावरण: विजुअल स्टूडियो या कोई अन्य .NET संगत IDE.
- C# का बुनियादी ज्ञान: आपको C# प्रोग्रामिंग में सहज होना चाहिए।
- फ़ॉन्ट फ़ोल्डर: आपके कस्टम फ़ॉन्ट वाली निर्देशिका.

## नामस्थान आयात करें

सबसे पहले, आइए आवश्यक नेमस्पेस को आयात करें। यह फ़ॉन्ट फ़ोल्डर सेट करने के लिए आवश्यक क्लासेस और विधियों तक पहुँचने में मदद करता है।

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;
```

आइये इस प्रक्रिया को सरल एवं सुगम चरणों में विभाजित करें।

## चरण 1: डेटा निर्देशिका निर्धारित करें

हर महान यात्रा एक कदम से शुरू होती है, और हमारी यात्रा उस निर्देशिका को परिभाषित करने से शुरू होती है जहाँ आपका दस्तावेज़ संग्रहीत है। यह वह जगह है जहाँ Aspose.Words आपके Word दस्तावेज़ की तलाश करेगा।

```csharp
// आपके दस्तावेज़ निर्देशिका का पथ
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

 यहाँ, प्रतिस्थापित करें`"YOUR DOCUMENT DIRECTORY"` आपके दस्तावेज़ निर्देशिका के वास्तविक पथ के साथ। यह वह जगह है जहाँ आपका स्रोत दस्तावेज़ स्थित है और जहाँ आउटपुट सहेजा जाएगा।

## चरण 2: फ़ॉन्ट फ़ोल्डर सेट करें

 अब, आइए Aspose.Words को बताएं कि आपके कस्टम फ़ॉन्ट कहाँ मिलेंगे। यह फ़ॉन्ट फ़ोल्डर को सेट करके किया जाता है`FontSettings.DefaultInstance.SetFontsFolder` तरीका।

```csharp
FontSettings.DefaultInstance.SetFontsFolder("C:\\MyFonts\\", true);
```

 इस पंक्ति में,`"C:\\MyFonts\\"` आपके कस्टम फ़ॉन्ट फ़ोल्डर का पथ है। दूसरा पैरामीटर,`true`, यह इंगित करता है कि इस फ़ोल्डर में फ़ॉन्ट्स को पुनरावर्ती रूप से स्कैन किया जाना चाहिए।

## चरण 3: अपना दस्तावेज़ लोड करें

 फ़ॉन्ट फ़ोल्डर सेट होने के बाद, अगला चरण आपके वर्ड दस्तावेज़ को Aspose.Words में लोड करना है। यह काम Aspose.Words के ज़रिए किया जाता है।`Document` कक्षा।

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

 यहाँ,`dataDir + "Rendering.docx"` आपके Word दस्तावेज़ के पूर्ण पथ को संदर्भित करता है। सुनिश्चित करें कि आपका दस्तावेज़ निर्दिष्ट निर्देशिका में है।

## चरण 4: दस्तावेज़ सहेजें

अंतिम चरण फ़ॉन्ट फ़ोल्डर सेट करने के बाद अपने दस्तावेज़ को सहेजना है। यह सुनिश्चित करता है कि आपके कस्टम फ़ॉन्ट आउटपुट में सही तरीके से लागू किए गए हैं।

```csharp
doc.Save(dataDir + "WorkingWithFonts.SetFontsFoldersDefaultInstance.pdf");
```

यह लाइन आपके दस्तावेज़ को कस्टम फ़ॉन्ट के साथ PDF के रूप में सहेजती है। आउटपुट फ़ाइल आपके स्रोत दस्तावेज़ के समान निर्देशिका में स्थित होगी।

## निष्कर्ष

और अब यह हो गया! Aspose.Words for .NET में डिफ़ॉल्ट इंस्टेंस के लिए फ़ॉन्ट फ़ोल्डर सेट करना बहुत आसान है, जब आप इसे सरल चरणों में तोड़ते हैं। इस गाइड का पालन करके, आप यह सुनिश्चित कर सकते हैं कि आपके Word दस्तावेज़ बिल्कुल वैसे ही दिखें जैसे आप चाहते हैं, आपके सभी कस्टम फ़ॉन्ट्स के साथ। तो आगे बढ़ें, इसे आज़माएँ, और अपने दस्तावेज़ों को चमकाएँ!

## अक्सर पूछे जाने वाले प्रश्न

### क्या मैं एकाधिक फ़ॉन्ट फ़ोल्डर्स सेट कर सकता हूँ?
 हां, आप इसका उपयोग करके एकाधिक फ़ॉन्ट फ़ोल्डर सेट कर सकते हैं`SetFontsFolders` विधि जो फ़ोल्डर पथों की एक सरणी स्वीकार करती है।

### दस्तावेज़ों को सहेजने के लिए Aspose.Words किस फ़ाइल स्वरूपों का समर्थन करता है?
Aspose.Words DOCX, PDF, HTML, EPUB, आदि सहित विभिन्न प्रारूपों का समर्थन करता है।

### क्या Aspose.Words में ऑनलाइन फ़ॉन्ट का उपयोग करना संभव है?
नहीं, Aspose.Words वर्तमान में केवल स्थानीय फ़ॉन्ट फ़ाइलों का समर्थन करता है।

### मैं कैसे सुनिश्चित कर सकता हूं कि मेरे कस्टम फ़ॉन्ट सहेजे गए पीडीएफ में एम्बेडेड हैं?
 सेट करके`FontSettings` सही ढंग से और यह सुनिश्चित करते हुए कि फ़ॉन्ट उपलब्ध हैं, Aspose.Words उन्हें पीडीएफ आउटपुट में एम्बेड कर देगा।

### यदि कोई फ़ॉन्ट निर्दिष्ट फ़ोल्डर में नहीं मिलता है तो क्या होगा?
यदि निर्दिष्ट फ़ॉन्ट नहीं मिलता है तो Aspose.Words फ़ॉलबैक फ़ॉन्ट का उपयोग करेगा।
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
