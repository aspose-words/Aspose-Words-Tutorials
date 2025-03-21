---
title: रिक्त स्थानों के साथ क्रमांकन का पता लगाना
linktitle: रिक्त स्थानों के साथ क्रमांकन का पता लगाना
second_title: Aspose.Words दस्तावेज़ प्रसंस्करण API
description: जानें कि सादे टेक्स्ट दस्तावेज़ों में रिक्त स्थानों के साथ क्रमांकन का पता लगाने के लिए .NET के लिए Aspose.Words का उपयोग कैसे करें और सुनिश्चित करें कि आपकी सूचियाँ सही ढंग से पहचानी गई हैं।
weight: 10
url: /hi/net/programming-with-txtloadoptions/detect-numbering-with-whitespaces/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# रिक्त स्थानों के साथ क्रमांकन का पता लगाना

## परिचय

.NET के शौकीनों के लिए Aspose.Words! आज, हम एक आकर्षक सुविधा के बारे में बात करने जा रहे हैं जो सादे टेक्स्ट दस्तावेज़ों में सूचियों को संभालना आसान बना सकती है। क्या आपने कभी ऐसी टेक्स्ट फ़ाइलों से निपटा है जहाँ कुछ पंक्तियाँ सूचियाँ होनी चाहिए, लेकिन वे Word दस्तावेज़ में लोड होने पर बिल्कुल सही नहीं लगतीं? खैर, हमारे पास एक बढ़िया तरकीब है: रिक्त स्थानों के साथ नंबरिंग का पता लगाना। यह ट्यूटोरियल आपको बताएगा कि कैसे उपयोग करना है`DetectNumberingWithWhitespaces` Aspose.Words for .NET में विकल्प का उपयोग यह सुनिश्चित करने के लिए करें कि आपकी सूचियाँ सही ढंग से पहचानी जाएँ, भले ही संख्याओं और पाठ के बीच रिक्त स्थान हो।

## आवश्यक शर्तें

आरंभ करने से पहले, सुनिश्चित करें कि आपके पास निम्नलिखित हैं:

-  .NET के लिए Aspose.Words: आप इसे यहाँ से डाउनलोड कर सकते हैं[एस्पोज रिलीज](https://releases.aspose.com/words/net/) पृष्ठ.
- विकास वातावरण: विजुअल स्टूडियो या कोई अन्य C# IDE.
- आपके मशीन पर .NET फ्रेमवर्क स्थापित है।
- C# का बुनियादी ज्ञान: मूल बातें समझने से आपको उदाहरणों के साथ आगे बढ़ने में मदद मिलेगी।

## नामस्थान आयात करें

कोड में कूदने से पहले, सुनिश्चित करें कि आपके प्रोजेक्ट में आवश्यक नेमस्पेस आयातित हैं। आरंभ करने के लिए यहां एक त्वरित स्निपेट दिया गया है:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Loading;
```

आइए इस प्रक्रिया को सरल, प्रबंधनीय चरणों में विभाजित करें। प्रत्येक चरण आपको आवश्यक कोड के माध्यम से मार्गदर्शन करेगा और समझाएगा कि क्या हो रहा है।

## चरण 1: अपनी दस्तावेज़ निर्देशिका निर्धारित करें

सबसे पहले, आइए अपने डॉक्यूमेंट डायरेक्टरी का पथ सेट करें। यहीं पर आपकी इनपुट और आउटपुट फ़ाइलें संग्रहीत होंगी।

```csharp
// आपके दस्तावेज़ निर्देशिका का पथ
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## चरण 2: एक सादा पाठ दस्तावेज़ बनाएँ

इसके बाद, हम एक स्ट्रिंग के रूप में एक प्लेनटेक्स्ट दस्तावेज़ बनाएंगे। इस दस्तावेज़ में ऐसे भाग होंगे जिन्हें सूचियों के रूप में समझा जा सकता है।

```csharp
const string textDoc = "Full stop delimiters:\n" +
                       "1. First list item 1\n" +
                       "2. First list item 2\n" +
                       "3. First list item 3\n\n" +
                       "Right bracket delimiters:\n" +
                       "1) Second list item 1\n" +
                       "2) Second list item 2\n" +
                       "3) Second list item 3\n\n" +
                       "Bullet delimiters:\n" +
                       "• Third list item 1\n" +
                       "• Third list item 2\n" +
                       "• Third list item 3\n\n" +
                       "Whitespace delimiters:\n" +
                       "1 Fourth list item 1\n" +
                       "2 Fourth list item 2\n" +
                       "3 Fourth list item 3";
```

## चरण 3: लोडऑप्शन कॉन्फ़िगर करें

 रिक्त स्थानों के साथ क्रमांकन का पता लगाने के लिए, हमें सेट करने की आवश्यकता है`DetectNumberingWithWhitespaces` विकल्प`true` में एक`TxtLoadOptions` वस्तु।

```csharp
TxtLoadOptions loadOptions = new TxtLoadOptions { DetectNumberingWithWhitespaces = true };
```

## चरण 4: दस्तावेज़ लोड करें

 अब, आइए दस्तावेज़ को लोड करें`TxtLoadOptions` एक पैरामीटर के रूप में। यह सुनिश्चित करता है कि चौथी सूची (रिक्त स्थान के साथ) सही ढंग से पहचानी गई है।

```csharp
Document doc = new Document(new MemoryStream(Encoding.UTF8.GetBytes(textDoc)), loadOptions);
```

## चरण 5: दस्तावेज़ सहेजें

अंत में, दस्तावेज़ को अपनी निर्दिष्ट निर्देशिका में सहेजें। यह सही ढंग से पहचानी गई सूचियों के साथ एक वर्ड दस्तावेज़ आउटपुट करेगा।

```csharp
doc.Save(dataDir + "WorkingWithTxtLoadOptions.DetectNumberingWithWhitespaces.docx");
```

## निष्कर्ष

और अब यह हो गया! कोड की कुछ ही पंक्तियों के साथ, आपने .NET के लिए Aspose.Words का उपयोग करके प्लेनटेक्स्ट दस्तावेज़ों में रिक्त स्थानों के साथ नंबरिंग का पता लगाने की कला में महारत हासिल कर ली है। यह सुविधा विभिन्न टेक्स्ट प्रारूपों से निपटने और यह सुनिश्चित करने के लिए अविश्वसनीय रूप से उपयोगी हो सकती है कि आपकी सूचियाँ आपके Word दस्तावेज़ों में सटीक रूप से प्रस्तुत की गई हैं। इसलिए अगली बार जब आप उन मुश्किल सूचियों का सामना करेंगे, तो आपको पता होगा कि क्या करना है।

## अक्सर पूछे जाने वाले प्रश्न

###  क्या है`DetectNumberingWithWhitespaces` in Aspose.Words for .NET?
`DetectNumberingWithWhitespaces` में एक विकल्प है`TxtLoadOptions` जो Aspose.Words को सूचियों को पहचानने की अनुमति देता है, भले ही क्रमांकन और सूची आइटम पाठ के बीच रिक्त स्थान हो।

### क्या मैं इस सुविधा का उपयोग बुलेट और ब्रैकेट जैसे अन्य सीमांककों के लिए कर सकता हूँ?
 हां, Aspose.Words स्वचालित रूप से बुलेट और ब्रैकेट जैसे सामान्य डिलीमीटर वाली सूचियों का पता लगाता है।`DetectNumberingWithWhitespaces` विशेष रूप से रिक्त स्थान वाली सूचियों में मदद करता है।

###  यदि मैं इसका उपयोग नहीं करूँ तो क्या होगा?`DetectNumberingWithWhitespaces`?
इस विकल्प के बिना, क्रमांकन और पाठ के बीच रिक्त स्थान वाली सूचियों को सूचियों के रूप में नहीं पहचाना जा सकता है, और आइटम सादे पैराग्राफ के रूप में दिखाई दे सकते हैं।

### क्या यह सुविधा अन्य Aspose उत्पादों में उपलब्ध है?
यह विशिष्ट सुविधा .NET के लिए Aspose.Words के अनुरूप बनाई गई है, जिसे Word दस्तावेज़ प्रसंस्करण को संभालने के लिए डिज़ाइन किया गया है।

### मैं .NET के लिए Aspose.Words हेतु अस्थायी लाइसेंस कैसे प्राप्त कर सकता हूँ?
 आप अस्थायी लाइसेंस प्राप्त कर सकते हैं[Aspose अस्थायी लाइसेंस](https://purchase.aspose.com/temporary-license/) पृष्ठ.


{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
