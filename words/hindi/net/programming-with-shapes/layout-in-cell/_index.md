---
title: सेल में लेआउट
linktitle: सेल में लेआउट
second_title: Aspose.Words दस्तावेज़ प्रसंस्करण API
description: इस विस्तृत गाइड के साथ .NET के लिए Aspose.Words का उपयोग करके सेल में लेआउट सेट करना सीखें। Word दस्तावेज़ों को कस्टमाइज़ करने के इच्छुक डेवलपर्स के लिए बिल्कुल सही।
weight: 10
url: /hi/net/programming-with-shapes/layout-in-cell/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# सेल में लेआउट

## परिचय

यदि आप कभी भी Word दस्तावेज़ों में अपने टेबल सेल के लेआउट को प्रोग्रामेटिक रूप से ठीक करना चाहते हैं, तो आप सही जगह पर हैं। आज, हम .NET के लिए Aspose.Words का उपयोग करके सेल में लेआउट सेट करने के तरीके के बारे में जानेंगे। हम एक व्यावहारिक उदाहरण के माध्यम से चलेंगे, इसे चरण-दर-चरण तोड़ेंगे ताकि आप आसानी से इसका पालन कर सकें।

## आवश्यक शर्तें

इससे पहले कि हम कोड में आगे बढ़ें, आइए सुनिश्चित करें कि आपके पास वह सब कुछ है जो आपको चाहिए:

1.  Aspose.Words for .NET: सुनिश्चित करें कि आपके पास Aspose.Words for .NET लाइब्रेरी स्थापित है। यदि आपके पास नहीं है, तो आप यह कर सकते हैं[यहाँ पर डाउनलोड करो](https://releases.aspose.com/words/net/).
2. विकास पर्यावरण: आपको .NET के साथ एक विकास पर्यावरण की आवश्यकता होगी। यदि आप अनुशंसाओं की तलाश कर रहे हैं तो Visual Studio एक बढ़िया विकल्प है।
3. C# का बुनियादी ज्ञान: यद्यपि मैं प्रत्येक चरण की व्याख्या करूंगा, C# की बुनियादी समझ आपको अधिक आसानी से अनुसरण करने में मदद करेगी।
4.  दस्तावेज़ निर्देशिका: एक निर्देशिका पथ तैयार करें जहाँ आप अपने दस्तावेज़ सहेजेंगे। हम इसे इस प्रकार संदर्भित करेंगे`YOUR DOCUMENT DIRECTORY`.

## नामस्थान आयात करें

आरंभ करने के लिए, सुनिश्चित करें कि आप अपने प्रोजेक्ट में आवश्यक नामस्थान आयात कर रहे हैं:

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Tables;
```

आइये इस प्रक्रिया को प्रबंधनीय चरणों में विभाजित करें।

## चरण 1: नया दस्तावेज़ बनाएँ

 सबसे पहले, हम एक नया वर्ड दस्तावेज़ बनाएंगे और एक आरंभीकरण करेंगे`DocumentBuilder` हमें अपनी विषय-वस्तु के निर्माण में सहायता करने के लिए प्रेरित करें।

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## चरण 2: तालिका प्रारंभ करें और पंक्ति प्रारूप सेट करें

हम एक तालिका का निर्माण शुरू करेंगे और पंक्तियों के लिए ऊंचाई और ऊंचाई नियम निर्दिष्ट करेंगे।

```csharp
builder.StartTable();
builder.RowFormat.Height = 100;
builder.RowFormat.HeightRule = HeightRule.Exactly;
```

## चरण 3: कक्ष सम्मिलित करें और सामग्री भरें

इसके बाद, हम टेबल में सेल डालने के लिए लूप करते हैं। हर 7 सेल के लिए, हम एक नई सेल बनाने के लिए पंक्ति को समाप्त करेंगे।

```csharp
for (int i = 0; i < 31; i++)
{
    if (i != 0 && i % 7 == 0) builder.EndRow();
    builder.InsertCell();
    builder.Write("Cell contents");
}
builder.EndTable();
```

## चरण 4: वॉटरमार्क आकार जोड़ें

 अब, चलिए अपने डॉक्यूमेंट में वॉटरमार्क जोड़ते हैं।`Shape` ऑब्जेक्ट और उसके गुण सेट करें.

```csharp
Shape watermark = new Shape(doc, ShapeType.TextPlainText)
{
    RelativeHorizontalPosition = RelativeHorizontalPosition.Page,
    RelativeVerticalPosition = RelativeVerticalPosition.Page,
    IsLayoutInCell = true, // यदि आकृति को किसी सेल में रखा जाएगा तो उसे तालिका सेल के बाहर प्रदर्शित करें।
    Width = 300,
    Height = 70,
    HorizontalAlignment = HorizontalAlignment.Center,
    VerticalAlignment = VerticalAlignment.Center,
    Rotation = -40
};
```

## चरण 5: वॉटरमार्क उपस्थिति को अनुकूलित करें

हम वॉटरमार्क के रंग और पाठ गुणधर्म निर्धारित करके उसके स्वरूप को और भी अनुकूलित करेंगे।

```csharp
watermark.FillColor = Color.Gray;
watermark.StrokeColor = Color.Gray;
watermark.TextPath.Text = "watermarkText";
watermark.TextPath.FontFamily = "Arial";
watermark.Name = $"WaterMark_{Guid.NewGuid()}";
watermark.WrapType = WrapType.None;
```

## चरण 6: दस्तावेज़ में वॉटरमार्क डालें

हम दस्तावेज़ में अंतिम रन ढूंढेंगे और उस स्थान पर वॉटरमार्क डालेंगे।

```csharp
Run run = doc.GetChildNodes(NodeType.Run, true)[doc.GetChildNodes(NodeType.Run, true).Count - 1] as Run;
builder.MoveTo(run);
builder.InsertNode(watermark);
```

## चरण 7: Word 2010 के लिए दस्तावेज़ को अनुकूलित करें

संगतता सुनिश्चित करने के लिए, हम दस्तावेज़ को Word 2010 के लिए अनुकूलित करेंगे।

```csharp
doc.CompatibilityOptions.OptimizeFor(MsWordVersion.Word2010);
```

## चरण 8: दस्तावेज़ सहेजें

अंत में, हम अपने दस्तावेज़ को निर्दिष्ट निर्देशिका में सहेज लेंगे।

```csharp
doc.Save(dataDir + "WorkingWithShapes.LayoutInCell.docx");
```

## निष्कर्ष

और अब आपका काम हो गया! आपने .NET के लिए Aspose.Words का उपयोग करके अनुकूलित टेबल लेआउट के साथ सफलतापूर्वक एक Word दस्तावेज़ बनाया है और वॉटरमार्क जोड़ा है। इस ट्यूटोरियल का उद्देश्य प्रक्रिया के प्रत्येक भाग को समझने में आपकी सहायता करने के लिए एक स्पष्ट, चरण-दर-चरण मार्गदर्शिका प्रदान करना है। इन कौशलों के साथ, अब आप प्रोग्रामेटिक रूप से अधिक परिष्कृत और अनुकूलित Word दस्तावेज़ बना सकते हैं।

## अक्सर पूछे जाने वाले प्रश्न

### क्या मैं वॉटरमार्क टेक्स्ट के लिए अलग फ़ॉन्ट का उपयोग कर सकता हूँ?
 हां, आप फ़ॉन्ट सेट करके बदल सकते हैं`watermark.TextPath.FontFamily` प्रॉपर्टी को अपने इच्छित फ़ॉन्ट में बदलें।

### मैं वॉटरमार्क की स्थिति कैसे समायोजित करूं?
 आप संशोधित कर सकते हैं`RelativeHorizontalPosition`, `RelativeVerticalPosition`, `HorizontalAlignment` , और`VerticalAlignment` वॉटरमार्क की स्थिति को समायोजित करने के लिए गुण.

### क्या वॉटरमार्क के लिए पाठ के स्थान पर छवि का उपयोग करना संभव है?
 बिल्कुल! आप एक बना सकते हैं`Shape` प्रकार के साथ`ShapeType.Image` और इसका उपयोग करके अपनी छवि सेट करें`ImageData.SetImage` तरीका।

### क्या मैं अलग-अलग पंक्ति ऊंचाई वाली तालिकाएं बना सकता हूं?
हां, आप प्रत्येक पंक्ति के लिए अलग-अलग ऊंचाई निर्धारित कर सकते हैं`RowFormat.Height` उस पंक्ति में कक्षों को सम्मिलित करने से पहले संपत्ति का चयन करें।

### मैं दस्तावेज़ से वॉटरमार्क कैसे हटाऊं?
 आप दस्तावेज़ के आकार संग्रह में इसे ढूंढकर और कॉल करके वॉटरमार्क को हटा सकते हैं`Remove` तरीका।
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
