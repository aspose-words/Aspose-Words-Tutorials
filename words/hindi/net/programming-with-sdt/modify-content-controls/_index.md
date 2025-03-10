---
title: सामग्री नियंत्रण संशोधित करें
linktitle: सामग्री नियंत्रण संशोधित करें
second_title: Aspose.Words दस्तावेज़ प्रसंस्करण API
description: .NET के लिए Aspose.Words का उपयोग करके Word में संरचित दस्तावेज़ टैग को संशोधित करना सीखें। चरण-दर-चरण टेक्स्ट, ड्रॉपडाउन और छवियों को अपडेट करें।
weight: 10
url: /hi/net/programming-with-sdt/modify-content-controls/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# सामग्री नियंत्रण संशोधित करें

## परिचय

यदि आपने कभी Word दस्तावेज़ों के साथ काम किया है और आपको संरचित सामग्री नियंत्रणों को संशोधित करने की आवश्यकता है - जैसे कि सादा पाठ, ड्रॉपडाउन सूचियाँ, या चित्र - .NET के लिए Aspose.Words का उपयोग करके, तो आप सही जगह पर हैं! संरचित दस्तावेज़ टैग (SDT) शक्तिशाली उपकरण हैं जो दस्तावेज़ स्वचालन को आसान और अधिक लचीला बनाते हैं। इस ट्यूटोरियल में, हम इस बात पर गहराई से विचार करेंगे कि आप अपनी ज़रूरतों के हिसाब से इन SDT को कैसे संशोधित कर सकते हैं। चाहे आप टेक्स्ट अपडेट कर रहे हों, ड्रॉपडाउन चयन बदल रहे हों, या छवियों को बदल रहे हों, यह गाइड आपको चरण-दर-चरण प्रक्रिया से गुज़ारेगा।

## आवश्यक शर्तें

इससे पहले कि हम सामग्री नियंत्रण को संशोधित करने की बारीकियों में उतरें, सुनिश्चित करें कि आपके पास निम्नलिखित हैं:

1.  Aspose.Words for .NET स्थापित: सुनिश्चित करें कि आपके पास Aspose.Words लाइब्रेरी स्थापित है। यदि नहीं, तो आप कर सकते हैं[यहाँ पर डाउनलोड करो](https://releases.aspose.com/words/net/).

2. C# का बुनियादी ज्ञान: यह ट्यूटोरियल मानता है कि आप बुनियादी C# प्रोग्रामिंग अवधारणाओं से परिचित हैं।

3. .NET विकास वातावरण: .NET अनुप्रयोगों को चलाने के लिए आपके पास Visual Studio जैसा IDE होना चाहिए।

4. एक नमूना दस्तावेज़: हम विभिन्न प्रकार के SDTs के साथ एक नमूना Word दस्तावेज़ का उपयोग करेंगे। आप उदाहरण से एक का उपयोग कर सकते हैं या अपना खुद का बना सकते हैं।

5.  Aspose दस्तावेज़ तक पहुंच: अधिक विस्तृत जानकारी के लिए, देखें[Aspose.Words दस्तावेज़ीकरण](https://reference.aspose.com/words/net/).

## नामस्थान आयात करें

Aspose.Words के साथ काम करना शुरू करने के लिए, आपको अपने C# प्रोजेक्ट में संबंधित नेमस्पेस को आयात करना होगा। यहाँ बताया गया है कि आप इसे कैसे करते हैं:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Tables;
```

ये नामस्थान आपको अपने वर्ड दस्तावेज़ों में संरचित दस्तावेज़ टैग में हेरफेर करने के लिए आवश्यक वर्गों और विधियों तक पहुंच प्रदान करेंगे।

## चरण 1: अपना दस्तावेज़ पथ सेट करें

 कोई भी परिवर्तन करने से पहले, आपको अपने दस्तावेज़ का पथ निर्दिष्ट करना होगा।`"YOUR DOCUMENT DIRECTORY"` उस वास्तविक पथ के साथ जहां आपका दस्तावेज़ संग्रहीत है.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Structured document tags.docx");
```

## चरण 2: संरचित दस्तावेज़ टैग के माध्यम से लूप करें

 SDTs को संशोधित करने के लिए, आपको सबसे पहले दस्तावेज़ में सभी SDTs को लूप करना होगा। यह का उपयोग करके किया जाता है`GetChildNodes` प्रकार के सभी नोड्स प्राप्त करने की विधि`StructuredDocumentTag`.

```csharp
foreach (StructuredDocumentTag sdt in doc.GetChildNodes(NodeType.StructuredDocumentTag, true))
{
    // एसडीटी को उनके प्रकार के आधार पर संशोधित करें
}
```

## चरण 3: सादा पाठ SDTs संशोधित करें

यदि SDT सादा टेक्स्ट प्रकार का है, तो आप इसकी सामग्री को बदल सकते हैं। सबसे पहले, मौजूदा सामग्री को साफ़ करें, फिर नया टेक्स्ट जोड़ें।

```csharp
if (sdt.SdtType == SdtType.PlainText)
{
    sdt.RemoveAllChildren();
    Paragraph para = sdt.AppendChild(new Paragraph(doc)) as Paragraph;
    Run run = new Run(doc, "new text goes here");
    para.AppendChild(run);
}
```

 स्पष्टीकरण: यहाँ,`RemoveAllChildren()`SDT की मौजूदा सामग्री को साफ़ करता है। फिर हम एक नया बनाते हैं`Paragraph` और`Run` नया टेक्स्ट डालने के लिए ऑब्जेक्ट का चयन करें.

## चरण 4: ड्रॉपडाउन सूची SDTs को संशोधित करें

 ड्रॉपडाउन सूची SDTs के लिए, आप एक्सेस करके चयनित आइटम को बदल सकते हैं`ListItems` यहां, हम सूची में तीसरे आइटम का चयन करते हैं।

```csharp
if (sdt.SdtType == SdtType.DropDownList)
{
    SdtListItem secondItem = sdt.ListItems[2];
    sdt.ListItems.SelectedValue = secondItem;
}
```

स्पष्टीकरण: यह कोड स्निपेट ड्रॉपडाउन सूची से इंडेक्स 2 (तीसरा आइटम) पर आइटम का चयन करता है। अपनी ज़रूरतों के आधार पर इंडेक्स को समायोजित करें।

## चरण 5: चित्र SDTs संशोधित करें

किसी चित्र SDT के भीतर किसी छवि को अद्यतन करने के लिए, आप मौजूदा छवि को नई छवि से बदल सकते हैं।

```csharp
if (sdt.SdtType == SdtType.Picture)
{
    Shape shape = (Shape) sdt.GetChild(NodeType.Shape, 0, true);
    if (shape.HasImage)
    {
        shape.ImageData.SetImage(ImagesDir + "Watermark.png");
    }
}
```

 स्पष्टीकरण: यह कोड जाँचता है कि क्या आकृति में कोई छवि है और फिर उसे एक नई छवि से बदल देता है जो कि स्थित है`ImagesDir`.

## चरण 6: अपना संशोधित दस्तावेज़ सहेजें

सभी आवश्यक परिवर्तन करने के बाद, अपने मूल दस्तावेज़ को बरकरार रखने के लिए संशोधित दस्तावेज़ को नए नाम से सहेजें।

```csharp
doc.Save(dataDir + "WorkingWithSdt.ModifyContentControls.docx");
```

स्पष्टीकरण: यह दस्तावेज़ को एक नए फ़ाइल नाम के साथ सहेजता है ताकि आप इसे मूल से आसानी से अलग कर सकें।

## निष्कर्ष

.NET के लिए Aspose.Words का उपयोग करके Word दस्तावेज़ में सामग्री नियंत्रणों को संशोधित करना एक बार जब आप इसमें शामिल चरणों को समझ लेते हैं, तो यह सरल हो जाता है। चाहे आप टेक्स्ट अपडेट कर रहे हों, ड्रॉपडाउन चयन बदल रहे हों, या छवियों को स्वैप कर रहे हों, Aspose.Words इन कार्यों के लिए एक मजबूत API प्रदान करता है। इस ट्यूटोरियल का पालन करके, आप अपने दस्तावेज़ के संरचित सामग्री नियंत्रणों को प्रभावी ढंग से प्रबंधित और अनुकूलित कर सकते हैं, जिससे आपके दस्तावेज़ अधिक गतिशील और आपकी आवश्यकताओं के अनुरूप बनेंगे।

## पूछे जाने वाले प्रश्न

1. संरचित दस्तावेज़ टैग (एसडीटी) क्या है?

एसडीटी वर्ड दस्तावेजों में ऐसे तत्व होते हैं जो दस्तावेज़ सामग्री, जैसे टेक्स्ट बॉक्स, ड्रॉपडाउन सूची या चित्र, को प्रबंधित और प्रारूपित करने में मदद करते हैं।

2. मैं SDT में नया ड्रॉपडाउन आइटम कैसे जोड़ सकता हूँ?

 नया आइटम जोड़ने के लिए, का उपयोग करें`ListItems` संपत्ति और एक नया जोड़ें`SdtListItem` संग्रह के लिए.

3. क्या मैं किसी दस्तावेज़ से SDTs हटाने के लिए Aspose.Words का उपयोग कर सकता हूँ?

हां, आप दस्तावेज़ के नोड्स तक पहुंचकर और वांछित SDT को हटाकर SDT को हटा सकते हैं।

4. मैं उन SDTs को कैसे संभालूँ जो अन्य तत्वों के भीतर स्थित हैं?

 उपयोग`GetChildNodes` नेस्टेड एसडीटी तक पहुंचने के लिए उपयुक्त पैरामीटर के साथ विधि।

5. यदि जिस SDT को मुझे संशोधित करना है वह दस्तावेज़ में दिखाई नहीं दे रहा है तो मुझे क्या करना चाहिए?

सुनिश्चित करें कि SDT छिपा हुआ या सुरक्षित नहीं है। दस्तावेज़ सेटिंग जांचें और सुनिश्चित करें कि आपका कोड SDT प्रकार को सही ढंग से लक्षित कर रहा है।


### .NET के लिए Aspose.Words का उपयोग करके सामग्री नियंत्रण संशोधित करने के लिए उदाहरण स्रोत कोड 

```csharp
// आपके दस्तावेज़ निर्देशिका का पथ
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document(dataDir + "Structured document tags.docx");
foreach (StructuredDocumentTag sdt in doc.GetChildNodes(NodeType.StructuredDocumentTag, true))
{
	switch (sdt.SdtType)
	{
		case SdtType.PlainText:
		{
			sdt.RemoveAllChildren();
			Paragraph para = sdt.AppendChild(new Paragraph(doc)) as Paragraph;
			Run run = new Run(doc, "new text goes here");
			para.AppendChild(run);
			break;
		}
		case SdtType.DropDownList:
		{
			SdtListItem secondItem = sdt.ListItems[2];
			sdt.ListItems.SelectedValue = secondItem;
			break;
		}
		case SdtType.Picture:
		{
			Shape shape = (Shape) sdt.GetChild(NodeType.Shape, 0, true);
			if (shape.HasImage)
			{
				shape.ImageData.SetImage(ImagesDir + "Watermark.png");
			}
			break;
		}
	}
}
doc.Save(dataDir + "WorkingWithSdt.ModifyContentControls.docx");

```

बस! आपने .NET के लिए Aspose.Words का उपयोग करके अपने Word दस्तावेज़ में विभिन्न प्रकार के सामग्री नियंत्रणों को सफलतापूर्वक संशोधित किया है।
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
