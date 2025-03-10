---
title: दस्तावेज़ पाठ दिशा
linktitle: दस्तावेज़ पाठ दिशा
second_title: Aspose.Words दस्तावेज़ प्रसंस्करण API
description: इस चरण-दर-चरण मार्गदर्शिका के साथ .NET के लिए Aspose.Words का उपयोग करके Word में दस्तावेज़ टेक्स्ट दिशा सेट करना सीखें। दाएँ से बाएँ भाषाओं को संभालने के लिए बिल्कुल सही।
weight: 10
url: /hi/net/programming-with-txtloadoptions/document-text-direction/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# दस्तावेज़ पाठ दिशा

## परिचय

Word दस्तावेज़ों के साथ काम करते समय, विशेष रूप से वे जिनमें कई भाषाएँ या विशेष स्वरूपण की आवश्यकताएँ होती हैं, पाठ की दिशा निर्धारित करना महत्वपूर्ण हो सकता है। उदाहरण के लिए, हिब्रू या अरबी जैसी दाएँ-से-बाएँ भाषाओं के साथ काम करते समय, आपको पाठ की दिशा को तदनुसार समायोजित करने की आवश्यकता हो सकती है। इस गाइड में, हम .NET के लिए Aspose.Words का उपयोग करके दस्तावेज़ पाठ की दिशा निर्धारित करने का तरीका बताएंगे। 

## आवश्यक शर्तें

इससे पहले कि हम कोड में उतरें, सुनिश्चित करें कि आपके पास निम्नलिखित हैं:

-  Aspose.Words for .NET लाइब्रेरी: सुनिश्चित करें कि आपके पास Aspose.Words for .NET इंस्टॉल है। आप इसे यहाँ से डाउनलोड कर सकते हैं[Aspose वेबसाइट](https://releases.aspose.com/words/net/).
- विजुअल स्टूडियो: C# कोड लिखने और निष्पादित करने के लिए एक विकास वातावरण।
- C# का बुनियादी ज्ञान: C# प्रोग्रामिंग से परिचित होना लाभदायक होगा क्योंकि हम कुछ कोड लिखेंगे।

## नामस्थान आयात करें

आरंभ करने के लिए, आपको अपने प्रोजेक्ट में Aspose.Words के साथ काम करने के लिए आवश्यक नामस्थान आयात करने होंगे। आप इसे इस प्रकार कर सकते हैं:

```csharp
using Aspose.Words;
using Aspose.Words.Loading;
```

ये नामस्थान Word दस्तावेज़ों में परिवर्तन करने के लिए आवश्यक कक्षाओं और विधियों तक पहुंच प्रदान करते हैं।

## चरण 1: अपने दस्तावेज़ निर्देशिका का पथ निर्धारित करें

सबसे पहले, अपने दस्तावेज़ को उस स्थान तक ले जाने के लिए पथ सेट करें जहाँ वह स्थित है। फ़ाइलों को सही तरीके से लोड करने और सहेजने के लिए यह महत्वपूर्ण है।

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

 प्रतिस्थापित करें`"YOUR DOCUMENT DIRECTORY"` उस वास्तविक पथ के साथ जहां आपका दस्तावेज़ संग्रहीत है.

## चरण 2: दस्तावेज़ दिशा सेटिंग के साथ TxtLoadOptions बनाएँ

 इसके बाद, आपको इसका एक उदाहरण बनाना होगा`TxtLoadOptions` और इसे सेट करें`DocumentDirection` प्रॉपर्टी। यह Aspose.Words को बताता है कि दस्तावेज़ में टेक्स्ट की दिशा को कैसे संभालना है।

```csharp
TxtLoadOptions loadOptions = new TxtLoadOptions { DocumentDirection = DocumentDirection.Auto };
```

 इस उदाहरण में, हम उपयोग करते हैं`DocumentDirection.Auto` Aspose.Words को सामग्री के आधार पर स्वचालित रूप से दिशा निर्धारित करने की अनुमति देना।

## चरण 3: दस्तावेज़ लोड करें

 अब, दस्तावेज़ को लोड करें`Document` वर्ग और पहले से परिभाषित`loadOptions`.

```csharp
Document doc = new Document(dataDir + "Hebrew text.txt", loadOptions);
```

 यहाँ,`"Hebrew text.txt"` यह आपकी टेक्स्ट फ़ाइल का नाम है। सुनिश्चित करें कि यह फ़ाइल आपकी निर्दिष्ट निर्देशिका में मौजूद है।

## चरण 4: पैराग्राफ़ के द्विदिश स्वरूपण तक पहुँचें और जाँचें

यह पुष्टि करने के लिए कि पाठ दिशा सही ढंग से सेट की गई है, दस्तावेज़ के पहले पैराग्राफ तक पहुँचें और उसके द्विदिश स्वरूपण की जाँच करें।

```csharp
Paragraph paragraph = doc.FirstSection.Body.FirstParagraph;
Console.WriteLine(paragraph.ParagraphFormat.Bidi);
```

यह चरण डिबगिंग और यह सत्यापित करने के लिए उपयोगी है कि दस्तावेज़ की पाठ दिशा अपेक्षा के अनुसार लागू की गई है।

## चरण 5: दस्तावेज़ को नई सेटिंग्स के साथ सहेजें

अंत में, परिवर्तनों को लागू करने और बनाए रखने के लिए दस्तावेज़ को सहेजें।

```csharp
doc.Save(dataDir + "WorkingWithTxtLoadOptions.DocumentTextDirection.docx");
```

 यहाँ,`"WorkingWithTxtLoadOptions.DocumentTextDirection.docx"` आउटपुट फ़ाइल का नाम है। ऐसा नाम चुनना सुनिश्चित करें जो आपके द्वारा किए गए परिवर्तनों को दर्शाता हो।

## निष्कर्ष

Word दस्तावेज़ों में टेक्स्ट दिशा सेट करना Aspose.Words for .NET के साथ एक सीधी प्रक्रिया है। इन चरणों का पालन करके, आप आसानी से कॉन्फ़िगर कर सकते हैं कि आपका दस्तावेज़ दाएँ-से-बाएँ या बाएँ-से-दाएँ टेक्स्ट को कैसे संभालता है। चाहे आप बहुभाषी दस्तावेज़ों के साथ काम कर रहे हों या आपको विशिष्ट भाषाओं के लिए टेक्स्ट दिशा को फ़ॉर्मेट करने की आवश्यकता हो, Aspose.Words आपकी ज़रूरतों को पूरा करने के लिए एक मज़बूत समाधान प्रदान करता है।

## अक्सर पूछे जाने वाले प्रश्न

###  क्या है?`DocumentDirection` property used for?

`DocumentDirection` संपत्ति में`TxtLoadOptions` दस्तावेज़ के लिए पाठ की दिशा निर्धारित करता है। इसे इस प्रकार सेट किया जा सकता है`DocumentDirection.Auto`, `DocumentDirection.LeftToRight` , या`DocumentDirection.RightToLeft`.

### क्या मैं संपूर्ण दस्तावेज़ के बजाय विशिष्ट पैराग्राफ़ के लिए पाठ दिशा निर्धारित कर सकता हूँ?

 हां, आप इसका उपयोग करके विशिष्ट पैराग्राफ के लिए पाठ की दिशा निर्धारित कर सकते हैं`ParagraphFormat.Bidi` संपत्ति, लेकिन`TxtLoadOptions.DocumentDirection` प्रॉपर्टी संपूर्ण दस्तावेज़ के लिए डिफ़ॉल्ट दिशा निर्धारित करती है।

###  लोड करने के लिए कौन से फ़ाइल प्रारूप समर्थित हैं`TxtLoadOptions`?

`TxtLoadOptions` मुख्य रूप से टेक्स्ट फाइल (.txt) लोड करने के लिए उपयोग किया जाता है। अन्य फ़ाइल स्वरूपों के लिए, अलग-अलग क्लास का उपयोग करें जैसे`DocLoadOptions` या`DocxLoadOptions`.

### मैं मिश्रित पाठ निर्देशों वाले दस्तावेज़ों को कैसे संभाल सकता हूँ?

 मिश्रित पाठ निर्देशों वाले दस्तावेज़ों के लिए, आपको प्रति-पैराग्राफ के आधार पर फ़ॉर्मेटिंग को संभालने की आवश्यकता हो सकती है।`ParagraphFormat.Bidi` प्रत्येक पैराग्राफ की दिशा को आवश्यकतानुसार समायोजित करने के लिए संपत्ति का उपयोग करें।

### मैं Aspose.Words for .NET के बारे में अधिक जानकारी कहां पा सकता हूं?

 अधिक जानकारी के लिए देखें[.NET दस्तावेज़ीकरण के लिए Aspose.Words](https://reference.aspose.com/words/net/) . आप अतिरिक्त संसाधनों का भी पता लगा सकते हैं जैसे[लिंक को डाउनलोड करें](https://releases.aspose.com/words/net/), [खरीदना](https://purchase.aspose.com/buy), [मुफ्त परीक्षण](https://releases.aspose.com/), [अस्थायी लाइसेंस](https://purchase.aspose.com/temporary-license/) , और[सहायता](https://forum.aspose.com/c/words/8).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
