---
title: रिक्त स्थान विकल्प संभालें
linktitle: रिक्त स्थान विकल्प संभालें
second_title: Aspose.Words दस्तावेज़ प्रसंस्करण API
description: .NET के लिए Aspose.Words के साथ टेक्स्ट दस्तावेज़ों में अग्रणी और अनुगामी रिक्त स्थान को संभालना सीखें। यह ट्यूटोरियल टेक्स्ट फ़ॉर्मेटिंग को साफ़ करने के लिए एक गाइड प्रदान करता है।
weight: 10
url: /hi/net/programming-with-txtloadoptions/handle-spaces-options/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# रिक्त स्थान विकल्प संभालें

## परिचय

टेक्स्ट डॉक्यूमेंट में स्पेस को हैंडल करना कभी-कभी एक करतब की तरह लग सकता है। स्पेस वहां घुस सकते हैं जहां आप उन्हें नहीं चाहते हैं या जहां उनकी जरूरत है वहां अनुपस्थित हो सकते हैं। .NET के लिए Aspose.Words के साथ काम करते समय, आपके पास इन स्पेस को सटीक और कुशलता से प्रबंधित करने के लिए उपकरण होते हैं। इस ट्यूटोरियल में, हम Aspose.Words का उपयोग करके टेक्स्ट डॉक्यूमेंट में स्पेस को हैंडल करने के तरीके के बारे में जानेंगे, जिसमें लीडिंग और ट्रेलिंग स्पेस पर ध्यान केंद्रित किया जाएगा।

## आवश्यक शर्तें

आरंभ करने से पहले, सुनिश्चित करें कि आपके पास ये हैं:

-  .NET के लिए Aspose.Words: आपको अपने .NET वातावरण में इस लाइब्रेरी को स्थापित करना होगा। आप इसे यहाँ से प्राप्त कर सकते हैं[Aspose वेबसाइट](https://releases.aspose.com/words/net/).
- विज़ुअल स्टूडियो: कोडिंग के लिए एक एकीकृत विकास वातावरण (IDE)। विज़ुअल स्टूडियो .NET प्रोजेक्ट्स के साथ काम करना आसान बनाता है।
- C# का मूलभूत ज्ञान: C# प्रोग्रामिंग से परिचित होना उपयोगी होगा क्योंकि हम कुछ कोड लिखेंगे।

## नामस्थान आयात करें

अपने .NET प्रोजेक्ट में Aspose.Words के साथ काम करने के लिए, आपको सबसे पहले आवश्यक नेमस्पेस आयात करने होंगे। अपनी C# फ़ाइल के शीर्ष पर निम्नलिखित using निर्देश जोड़ें:

```csharp
using Aspose.Words;
using Aspose.Words.Loading;
using System.IO;
using System.Text;
```

इन नामस्थानों में दस्तावेजों को संभालने, विकल्प लोड करने और फ़ाइल स्ट्रीम के साथ काम करने की मुख्य कार्यक्षमता शामिल होती है।

## चरण 1: अपने दस्तावेज़ निर्देशिका का पथ निर्धारित करें

सबसे पहले, वह पथ निर्दिष्ट करें जहाँ आप अपना दस्तावेज़ सहेजना चाहते हैं। यह वह जगह है जहाँ Aspose.Words संशोधित फ़ाइल आउटपुट करेगा।

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

 प्रतिस्थापित करें`"YOUR DOCUMENT DIRECTORY"` वास्तविक पथ के साथ जहाँ आप अपने दस्तावेज़ों को संग्रहीत करना चाहते हैं। यह पथ महत्वपूर्ण है क्योंकि यह Aspose.Words को निर्देशित करता है कि आउटपुट फ़ाइल को कहाँ सहेजना है।

## चरण 2: एक नमूना टेक्स्ट दस्तावेज़ बनाएँ

इसके बाद, असंगत आरंभिक और अंतिम रिक्त स्थान वाला एक नमूना पाठ परिभाषित करें। यह वह पाठ है जिसे हम Aspose.Words का उपयोग करके संसाधित करेंगे।

```csharp
const string textDoc = "      Line 1 \n" +
                       "    Line 2   \n" +
                       " Line 3       ";
```

 यहाँ,`textDoc` एक स्ट्रिंग है जो प्रत्येक पंक्ति से पहले और बाद में अतिरिक्त रिक्त स्थान के साथ एक टेक्स्ट फ़ाइल का अनुकरण करती है। इससे हमें यह देखने में मदद मिलेगी कि Aspose.Words इन रिक्त स्थानों को कैसे संभालता है।

## चरण 3: हैंडलिंग स्पेस के लिए लोड विकल्प सेट करें

 यह नियंत्रित करने के लिए कि अग्रणी और अंतिम रिक्त स्थान कैसे प्रबंधित किए जाएं, आपको कॉन्फ़िगर करने की आवश्यकता है`TxtLoadOptions` ऑब्जेक्ट. यह ऑब्जेक्ट आपको यह निर्दिष्ट करने की अनुमति देता है कि टेक्स्ट फ़ाइल लोड करते समय रिक्त स्थान का कैसे उपयोग किया जाना चाहिए.

```csharp
TxtLoadOptions loadOptions = new TxtLoadOptions
{
    LeadingSpacesOptions = TxtLeadingSpacesOptions.Trim,
    TrailingSpacesOptions = TxtTrailingSpacesOptions.Trim
};
```

इस कॉन्फ़िगरेशन में:
- `LeadingSpacesOptions = TxtLeadingSpacesOptions.Trim`यह सुनिश्चित करता है कि पंक्ति के आरंभ में कोई रिक्त स्थान हटा दिया जाए।
- `TrailingSpacesOptions = TxtTrailingSpacesOptions.Trim` यह सुनिश्चित करता है कि पंक्ति के अंत में कोई रिक्त स्थान न हो।

यह सेटअप टेक्स्ट फ़ाइलों को प्रोसेस करने या सेव करने से पहले उन्हें साफ करने के लिए आवश्यक है।

## चरण 4: विकल्पों के साथ टेक्स्ट दस्तावेज़ लोड करें

 अब जबकि हमने अपने लोड विकल्पों को कॉन्फ़िगर कर लिया है, तो उनका उपयोग नमूना टेक्स्ट दस्तावेज़ को Aspose.Words में लोड करने के लिए करें`Document` वस्तु।

```csharp
Document doc = new Document(new MemoryStream(Encoding.UTF8.GetBytes(textDoc)), loadOptions);
```

 यहाँ, हम एक बना रहे हैं`MemoryStream` एन्कोडेड नमूना पाठ से और इसे पास करना`Document` कन्स्ट्रक्टर के साथ-साथ लोड विकल्प भी शामिल हैं। यह चरण टेक्स्ट को पढ़ता है और स्पेस-हैंडलिंग नियम लागू करता है।

## चरण 5: दस्तावेज़ सहेजें

अंत में, प्रोसेस किए गए दस्तावेज़ को अपनी निर्दिष्ट निर्देशिका में सेव करें। यह चरण साफ़ किए गए दस्तावेज़ को फ़ाइल में लिखता है।

```csharp
doc.Save(dataDir + "WorkingWithTxtLoadOptions.HandleSpacesOptions.docx");
```

 यह कोड साफ़ किए गए रिक्त स्थानों के साथ दस्तावेज़ को नामित फ़ाइल में सहेजता है`WorkingWithTxtLoadOptions.HandleSpacesOptions.docx` अपनी निर्दिष्ट निर्देशिका में.

## निष्कर्ष

टेक्स्ट प्रोसेसिंग लाइब्रेरी के साथ काम करते समय टेक्स्ट डॉक्यूमेंट में स्पेस को संभालना एक आम लेकिन महत्वपूर्ण काम है। .NET के लिए Aspose.Words के साथ, लीडिंग और ट्रेलिंग स्पेस को मैनेज करना बहुत आसान हो जाता है।`TxtLoadOptions` क्लास। इस ट्यूटोरियल में दिए गए चरणों का पालन करके, आप यह सुनिश्चित कर सकते हैं कि आपके दस्तावेज़ साफ़-सुथरे हैं और आपकी ज़रूरतों के हिसाब से फ़ॉर्मेट किए गए हैं। चाहे आप किसी रिपोर्ट के लिए टेक्स्ट तैयार कर रहे हों या डेटा साफ़ कर रहे हों, ये तकनीकें आपको अपने दस्तावेज़ के स्वरूप पर नियंत्रण बनाए रखने में मदद करेंगी।

## अक्सर पूछे जाने वाले प्रश्न

### मैं .NET के लिए Aspose.Words का उपयोग करके टेक्स्ट फ़ाइलों में रिक्त स्थान को कैसे संभाल सकता हूँ?  
 आप इसका उपयोग कर सकते हैं`TxtLoadOptions` क्लास का उपयोग यह निर्दिष्ट करने के लिए किया जाता है कि पाठ फ़ाइलों को लोड करते समय आरंभिक और अंतिम रिक्त स्थानों का प्रबंधन कैसे किया जाना चाहिए।

### क्या मैं अपने दस्तावेज़ में आरंभिक रिक्त स्थान रख सकता हूँ?  
 हां, आप कॉन्फ़िगर कर सकते हैं`TxtLoadOptions` सेटिंग करके अग्रणी स्थान बनाए रखना`LeadingSpacesOptions` को`TxtLeadingSpacesOptions.None`.

### यदि मैं अंतिम रिक्त स्थानों को नहीं काटूं तो क्या होगा?  
यदि अंतिम रिक्त स्थानों को नहीं काटा गया तो वे आपके दस्तावेज़ में पंक्तियों के अंत में बने रहेंगे, जिससे स्वरूपण या उपस्थिति प्रभावित हो सकती है।

### क्या मैं अन्य प्रकार के रिक्त स्थानों को संभालने के लिए Aspose.Words का उपयोग कर सकता हूँ?  
Aspose.Words मुख्य रूप से आगे और पीछे के रिक्त स्थान पर ध्यान केंद्रित करता है। अधिक जटिल रिक्त स्थान प्रबंधन के लिए, आपको अतिरिक्त प्रसंस्करण की आवश्यकता हो सकती है।

### मैं Aspose.Words for .NET के बारे में अधिक जानकारी कहां पा सकता हूं?  
 आप यहां जा सकते हैं[Aspose.Words दस्तावेज़ीकरण](https://reference.aspose.com/words/net/) अधिक विस्तृत जानकारी और संसाधनों के लिए.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
