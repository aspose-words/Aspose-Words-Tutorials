---
"description": "चरण-दर-चरण मार्गदर्शिका में .NET के लिए Aspose.Words का उपयोग करके Word फ़ाइलों से ActiveX नियंत्रण गुण पढ़ना सीखें। अपने दस्तावेज़ स्वचालन कौशल को बढ़ाएँ।"
"linktitle": "वर्ड फ़ाइल से Active XControl गुण पढ़ें"
"second_title": "Aspose.Words दस्तावेज़ प्रसंस्करण API"
"title": "वर्ड फ़ाइल से Active XControl गुण पढ़ें"
"url": "/hi/net/working-with-oleobjects-and-activex/read-active-xcontrol-properties/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# वर्ड फ़ाइल से Active XControl गुण पढ़ें

## परिचय

आज के डिजिटल युग में, उत्पादकता बढ़ाने के लिए स्वचालन महत्वपूर्ण है। यदि आप ऐसे Word दस्तावेज़ों के साथ काम कर रहे हैं जिनमें ActiveX नियंत्रण हैं, तो आपको विभिन्न उद्देश्यों के लिए उनके गुणों को पढ़ने की आवश्यकता हो सकती है। ActiveX नियंत्रण, जैसे चेकबॉक्स और बटन, महत्वपूर्ण डेटा रख सकते हैं। .NET के लिए Aspose.Words का उपयोग करके, आप इस डेटा को कुशलतापूर्वक निकाल सकते हैं और प्रोग्रामेटिक रूप से हेरफेर कर सकते हैं।

## आवश्यक शर्तें

शुरू करने से पहले, सुनिश्चित करें कि आपके पास निम्नलिखित हैं:

1. .NET लाइब्रेरी के लिए Aspose.Words: आप इसे यहाँ से डाउनलोड कर सकते हैं [यहाँ](https://releases.aspose.com/words/net/).
2. विजुअल स्टूडियो या कोई भी C# IDE: अपना कोड लिखने और निष्पादित करने के लिए।
3. ActiveX नियंत्रणों वाला एक Word दस्तावेज़: उदाहरण के लिए, "ActiveX controls.docx".
4. C# का बुनियादी ज्ञान: आगे बढ़ने के लिए C# प्रोग्रामिंग से परिचित होना आवश्यक है।

## नामस्थान आयात करें

सबसे पहले, आइए .NET के लिए Aspose.Words के साथ काम करने के लिए आवश्यक नेमस्पेस आयात करें।

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Ole;
using System;
```

## चरण 1: वर्ड दस्तावेज़ लोड करें

आरंभ करने के लिए, आपको Word दस्तावेज़ को लोड करना होगा जिसमें ActiveX नियंत्रण शामिल हैं।

```csharp
// आपके दस्तावेज़ निर्देशिका का पथ
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "ActiveX controls.docx");
```

## चरण 2: गुण रखने के लिए स्ट्रिंग को आरंभ करें

इसके बाद, ActiveX नियंत्रणों के गुणों को संग्रहीत करने के लिए एक रिक्त स्ट्रिंग को आरंभीकृत करें।

```csharp
string properties = "";
```

## चरण 3: दस्तावेज़ में आकृतियों के माध्यम से पुनरावृति करें

हमें ActiveX नियंत्रणों को खोजने के लिए दस्तावेज़ में सभी आकृतियों को पुनरावृत्त करना होगा।

```csharp
foreach (Shape shape in doc.GetChildNodes(NodeType.Shape, true))
{
    if (shape.OleFormat is null) continue;
    
    OleControl oleControl = shape.OleFormat.OleControl;
    if (oleControl.IsForms2OleControl)
    {
        // ActiveX नियंत्रण को संसाधित करें
    }
}
```

## चरण 4: ActiveX नियंत्रणों से गुण निकालें

लूप के भीतर, जाँचें कि क्या नियंत्रण Forms2OleControl है। यदि ऐसा है, तो उसे कास्ट करें और गुण निकालें।

```csharp
Forms2OleControl checkBox = (Forms2OleControl) oleControl;
properties += "\nCaption: " + checkBox.Caption;
properties += "\nValue: " + checkBox.Value;
properties += "\nEnabled: " + checkBox.Enabled;
properties += "\nType: " + checkBox.Type;

if (checkBox.ChildNodes != null)
{
    properties += "\nChildNodes: " + checkBox.ChildNodes;
}

properties += "\n";
```

## चरण 5: कुल ActiveX नियंत्रणों की गणना करें

सभी आकृतियों को दोहराने के बाद, पाए गए ActiveX नियंत्रणों की कुल संख्या की गणना करें।

```csharp
properties += "\nTotal ActiveX Controls found: " + doc.GetChildNodes(NodeType.Shape, true).Count;
```

## चरण 6: गुण प्रदर्शित करें

अंत में, निकाले गए गुणों को कंसोल पर प्रिंट करें।

```csharp
Console.WriteLine("\n" + properties);
```

## निष्कर्ष

और अब यह हो गया! आपने सफलतापूर्वक सीख लिया है कि Aspose.Words for .NET का उपयोग करके Word दस्तावेज़ से ActiveX नियंत्रण गुण कैसे पढ़ें। इस ट्यूटोरियल में दस्तावेज़ लोड करना, आकृतियों के माध्यम से पुनरावृत्ति करना और ActiveX नियंत्रणों से गुण निकालना शामिल है। इन चरणों का पालन करके, आप अपने Word दस्तावेज़ों से महत्वपूर्ण डेटा के निष्कर्षण को स्वचालित कर सकते हैं, जिससे आपकी कार्यप्रवाह दक्षता बढ़ जाती है।

## अक्सर पूछे जाने वाले प्रश्न

### वर्ड दस्तावेज़ों में ActiveX नियंत्रण क्या हैं?
एक्टिवएक्स नियंत्रण, वर्ड दस्तावेजों में सन्निहित इंटरैक्टिव ऑब्जेक्ट होते हैं, जैसे चेकबॉक्स, बटन और टेक्स्ट फ़ील्ड, जिनका उपयोग फॉर्म बनाने और कार्यों को स्वचालित करने के लिए किया जाता है।

### क्या मैं .NET के लिए Aspose.Words का उपयोग करके ActiveX नियंत्रणों के गुणों को संशोधित कर सकता हूँ?
हां, .NET के लिए Aspose.Words आपको प्रोग्रामेटिक रूप से ActiveX नियंत्रणों के गुणों को संशोधित करने की अनुमति देता है।

### क्या .NET के लिए Aspose.Words का उपयोग निःशुल्क है?
Aspose.Words for .NET एक निःशुल्क परीक्षण प्रदान करता है, लेकिन आपको निरंतर उपयोग के लिए लाइसेंस खरीदना होगा। आप एक निःशुल्क परीक्षण प्राप्त कर सकते हैं [यहाँ](https://releases.aspose.com/).

### क्या मैं C# के अलावा अन्य .NET भाषाओं के साथ .NET के लिए Aspose.Words का उपयोग कर सकता हूँ?
हां, .NET के लिए Aspose.Words का उपयोग किसी भी .NET भाषा के साथ किया जा सकता है, जिसमें VB.NET और F# शामिल हैं।

### मैं .NET के लिए Aspose.Words पर अधिक दस्तावेज़ कहां पा सकता हूं?
आप विस्तृत दस्तावेज पा सकते हैं [यहाँ](https://reference.aspose.com/words/net/).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}