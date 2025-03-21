---
title: वर्टिकल एंकर
linktitle: वर्टिकल एंकर
second_title: Aspose.Words दस्तावेज़ प्रसंस्करण API
description: .NET के लिए Aspose.Words का उपयोग करके Word दस्तावेज़ों में टेक्स्टबॉक्स के लिए वर्टिकल एंकर पोजिशन सेट करना सीखें। आसान चरण-दर-चरण मार्गदर्शिका शामिल है।
weight: 10
url: /hi/net/programming-with-shapes/vertical-anchor/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# वर्टिकल एंकर

## परिचय

क्या आपको कभी यह नियंत्रित करने की ज़रूरत महसूस हुई है कि Word दस्तावेज़ में टेक्स्टबॉक्स के अंदर टेक्स्ट कहाँ दिखाई देता है? शायद आप चाहते हैं कि आपका टेक्स्ट टेक्स्टबॉक्स के ऊपर, बीच में या नीचे एंकर हो? अगर ऐसा है, तो आप सही जगह पर हैं! इस ट्यूटोरियल में, हम Word दस्तावेज़ों में टेक्स्टबॉक्स के वर्टिकल एंकर को सेट करने के लिए .NET के लिए Aspose.Words का उपयोग करने का तरीका जानेंगे। वर्टिकल एंकरिंग को जादू की छड़ी के रूप में सोचें जो आपके टेक्स्ट को उसके कंटेनर के भीतर ठीक उसी स्थान पर रखती है जहाँ आप चाहते हैं। शुरू करने के लिए तैयार हैं? चलिए शुरू करते हैं!

## आवश्यक शर्तें

इससे पहले कि हम ऊर्ध्वाधर एंकरिंग के मूल तत्वों पर चर्चा करें, आपको कुछ चीजों को व्यवस्थित करने की आवश्यकता होगी:

1.  Aspose.Words for .NET: सुनिश्चित करें कि आपके पास Aspose.Words for .NET लाइब्रेरी स्थापित है। यदि आपके पास अभी तक यह नहीं है, तो आप[यहाँ पर डाउनलोड करो](https://releases.aspose.com/words/net/).
2. विज़ुअल स्टूडियो: यह ट्यूटोरियल मानता है कि आप कोडिंग के लिए विज़ुअल स्टूडियो या किसी अन्य .NET IDE का उपयोग कर रहे हैं।
3. C# का बुनियादी ज्ञान: C# और .NET से परिचित होने से आपको आसानी से आगे बढ़ने में मदद मिलेगी।

## नामस्थान आयात करें

आरंभ करने के लिए, आपको अपने C# कोड में आवश्यक नामस्थान आयात करने होंगे। यह वह जगह है जहाँ आप अपने एप्लिकेशन को बताते हैं कि आपको कौन सी कक्षाएँ और विधियाँ उपयोग करनी हैं। इसे करने का तरीका यहाँ बताया गया है:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
```

ये नामस्थान वे कक्षाएं प्रदान करते हैं जिनकी आपको दस्तावेजों और आकृतियों के साथ काम करने के लिए आवश्यकता होगी।

## चरण 1: दस्तावेज़ को आरंभ करें

सबसे पहले, आपको एक नया वर्ड डॉक्यूमेंट बनाना होगा। इसे पेंटिंग शुरू करने से पहले अपने कैनवास को सेट करने के रूप में सोचें।

```csharp
// आपके दस्तावेज़ निर्देशिका का पथ
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

 यहाँ,`Document` आपका खाली कैनवास है, और`DocumentBuilder` यह आपका पेंटब्रश है, जो आपको आकृतियां और पाठ जोड़ने की अनुमति देता है।

## चरण 2: टेक्स्टबॉक्स आकार डालें

अब, चलिए अपने दस्तावेज़ में एक टेक्स्टबॉक्स जोड़ते हैं। यहीं पर आपका टेक्स्ट रहेगा। 

```csharp
Shape textBox = builder.InsertShape(ShapeType.TextBox, 200, 200);
```

 इस उदाहरण में,`ShapeType.TextBox` आपके इच्छित आकार को निर्दिष्ट करता है, और`200, 200` टेक्स्टबॉक्स की चौड़ाई और ऊंचाई बिंदुओं में हैं।

## चरण 3: वर्टिकल एंकर सेट करें

यहाँ जादू होता है! आप टेक्स्टबॉक्स के भीतर टेक्स्ट का वर्टिकल अलाइनमेंट सेट कर सकते हैं। यह निर्धारित करता है कि टेक्स्ट टेक्स्टबॉक्स के ऊपर, बीच में या नीचे एंकर किया गया है या नहीं।

```csharp
textBox.TextBox.VerticalAnchor = TextBoxAnchor.Bottom;
```

 इस मामले में,`TextBoxAnchor.Bottom`यह सुनिश्चित करता है कि टेक्स्ट टेक्स्टबॉक्स के निचले भाग में लंगर डाला जाएगा। यदि आप इसे केंद्र में रखना चाहते हैं या शीर्ष पर संरेखित करना चाहते हैं, तो आप इसका उपयोग करेंगे`TextBoxAnchor.Center` या`TextBoxAnchor.Top`, क्रमश।

## चरण 4: टेक्स्टबॉक्स में टेक्स्ट जोड़ें

अब आपके टेक्स्टबॉक्स में कुछ सामग्री जोड़ने का समय आ गया है। इसे अपने कैनवास को अंतिम रूप देने के रूप में सोचें।

```csharp
builder.MoveTo(textBox.FirstParagraph);
builder.Write("Textbox contents");
```

 यहाँ,`MoveTo` यह सुनिश्चित करता है कि पाठ को टेक्स्टबॉक्स में डाला गया है, और`Write` वास्तविक पाठ जोड़ता है.

## चरण 5: दस्तावेज़ सहेजें

अंतिम चरण है अपने दस्तावेज़ को सहेजना। यह आपकी तैयार पेंटिंग को फ्रेम में रखने जैसा है।

```csharp
doc.Save(dataDir + "WorkingWithShapes.VerticalAnchor.docx");
```

## निष्कर्ष

और अब यह हो गया! आपने अभी सीखा है कि Aspose.Words for .NET का उपयोग करके Word दस्तावेज़ में टेक्स्टबॉक्स के भीतर टेक्स्ट के वर्टिकल अलाइनमेंट को कैसे नियंत्रित किया जाए। चाहे आप टेक्स्ट को ऊपर, बीच में या नीचे एंकर कर रहे हों, यह सुविधा आपको अपने दस्तावेज़ के लेआउट पर सटीक नियंत्रण देती है। तो अगली बार जब आपको अपने दस्तावेज़ के टेक्स्ट प्लेसमेंट में बदलाव करने की आवश्यकता होगी, तो आपको पता होगा कि क्या करना है!

## अक्सर पूछे जाने वाले प्रश्न

### वर्ड दस्तावेज़ में वर्टिकल एंकरिंग क्या है?
वर्टिकल एंकरिंग यह नियंत्रित करती है कि टेक्स्ट को टेक्स्टबॉक्स में कहां रखा जाए, जैसे शीर्ष, मध्य या निचला संरेखण।

### क्या मैं टेक्स्टबॉक्स के अलावा अन्य आकृतियों का उपयोग कर सकता हूँ?
हां, आप अन्य आकृतियों के साथ वर्टिकल एंकरिंग का उपयोग कर सकते हैं, हालांकि टेक्स्टबॉक्स सबसे आम उपयोग मामला है।

### टेक्स्टबॉक्स बनाने के बाद मैं एंकर पॉइंट कैसे बदलूं?
 आप एंकर पॉइंट को सेट करके बदल सकते हैं`VerticalAnchor` टेक्स्टबॉक्स आकार ऑब्जेक्ट पर संपत्ति।

### क्या टेक्स्ट को टेक्स्ट बॉक्स के मध्य में रखना संभव है?
 बिलकुल! बस उपयोग करें`TextBoxAnchor.Center` टेक्स्ट को टेक्स्ट बॉक्स के भीतर लंबवत केन्द्रित करने के लिए।

### मैं Aspose.Words for .NET के बारे में अधिक जानकारी कहां पा सकता हूं?
 इसकी जाँच पड़ताल करो[Aspose.Words दस्तावेज़ीकरण](https://reference.aspose.com/words/net/) अधिक जानकारी और मार्गदर्शन के लिए.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
