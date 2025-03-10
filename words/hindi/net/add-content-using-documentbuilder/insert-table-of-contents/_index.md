---
title: वर्ड दस्तावेज़ में विषय सूची डालें
linktitle: वर्ड दस्तावेज़ में विषय सूची डालें
second_title: Aspose.Words दस्तावेज़ प्रसंस्करण API
description: .NET के लिए Aspose.Words का उपयोग करके Word में विषय-सूची सम्मिलित करना सीखें। दस्तावेज़ों में सहज नेविगेशन के लिए हमारे चरण-दर-चरण मार्गदर्शिका का पालन करें।
weight: 10
url: /hi/net/add-content-using-documentbuilder/insert-table-of-contents/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# वर्ड दस्तावेज़ में विषय सूची डालें

## परिचय
इस ट्यूटोरियल में, आप सीखेंगे कि Aspose.Words for .NET का उपयोग करके अपने Word दस्तावेज़ों में कुशलतापूर्वक सामग्री की तालिका (TOC) कैसे जोड़ें। यह सुविधा लंबे दस्तावेज़ों को व्यवस्थित करने और नेविगेट करने, पठनीयता बढ़ाने और दस्तावेज़ अनुभागों का त्वरित अवलोकन प्रदान करने के लिए आवश्यक है।

## आवश्यक शर्तें

आरंभ करने से पहले, सुनिश्चित करें कि आपके पास निम्नलिखित हैं:

- C# और .NET फ्रेमवर्क की बुनियादी समझ।
- आपके मशीन पर Visual Studio स्थापित है.
-  Aspose.Words for .NET लाइब्रेरी। यदि आपने इसे अभी तक इंस्टॉल नहीं किया है, तो आप इसे यहाँ से डाउनलोड कर सकते हैं[यहाँ](https://releases.aspose.com/words/net/).

## नामस्थान आयात करें

आरंभ करने के लिए, अपने C# प्रोजेक्ट में आवश्यक नामस्थान आयात करें:

```csharp
using Aspose.Words;
using Aspose.Words.Builder;
using Aspose.Words.Fields;
using Aspose.Words.Tables;
```

आइये इस प्रक्रिया को स्पष्ट चरणों में विभाजित करें:

## चरण 1: Aspose.Words दस्तावेज़ और DocumentBuilder को आरंभ करें

 सबसे पहले, एक नया Aspose.Words आरंभ करें`Document` वस्तु और एक`DocumentBuilder` इसके साथ कार्य करने के लिए:

```csharp
// दस्तावेज़ और दस्तावेज़बिल्डर आरंभ करें
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## चरण 2: विषय-सूची डालें

 अब, का उपयोग कर सामग्री की तालिका डालें`InsertTableOfContents` तरीका:

```csharp
// विषय सूची डालें
builder.InsertTableOfContents("\\o \"1-3\" \\h \\z \\u");
```

## चरण 3: दस्तावेज़ सामग्री को नए पृष्ठ पर प्रारंभ करें

उचित स्वरूपण सुनिश्चित करने के लिए, वास्तविक दस्तावेज़ सामग्री को नए पृष्ठ पर प्रारंभ करें:

```csharp
// पृष्ठ विराम डालें
builder.InsertBreak(BreakType.PageBreak);
```

## चरण 4: शीर्षकों के साथ अपने दस्तावेज़ की संरचना करें

उपयुक्त शीर्षक शैलियों का उपयोग करके अपने दस्तावेज़ की सामग्री को व्यवस्थित करें:

```csharp
// शीर्षक शैलियाँ सेट करें
builder.ParagraphFormat.StyleIdentifier = StyleIdentifier.Heading1;
builder.Writeln("Heading 1");

builder.ParagraphFormat.StyleIdentifier = StyleIdentifier.Heading2;
builder.Writeln("Heading 1.1");
builder.Writeln("Heading 1.2");

builder.ParagraphFormat.StyleIdentifier = StyleIdentifier.Heading1;
builder.Writeln("Heading 2");
builder.Writeln("Heading 3");

builder.ParagraphFormat.StyleIdentifier = StyleIdentifier.Heading2;
builder.Writeln("Heading 3.1");

builder.ParagraphFormat.StyleIdentifier = StyleIdentifier.Heading3;
builder.Writeln("Heading 3.1.1");
builder.Writeln("Heading 3.1.2");
builder.Writeln("Heading 3.1.3");

builder.ParagraphFormat.StyleIdentifier = StyleIdentifier.Heading2;
builder.Writeln("Heading 3.2");
builder.Writeln("Heading 3.3");
```

## चरण 5: विषय-सूची को अपडेट और भरें

दस्तावेज़ संरचना को प्रतिबिंबित करने के लिए विषय-सूची को अद्यतन करें:

```csharp
// विषय-सूची फ़ील्ड को अपडेट करें
doc.UpdateFields();
```

## चरण 6: दस्तावेज़ सहेजें

अंत में, अपने दस्तावेज़ को निर्दिष्ट निर्देशिका में सहेजें:

```csharp
// दस्तावेज़ सहेजें
string dataDir = "YOUR_DOCUMENT_DIRECTORY_PATH";
doc.Save(dataDir + "InsertTableOfContentsUsingAsposeWords.docx");
```

## निष्कर्ष

.NET के लिए Aspose.Words का उपयोग करके सामग्री की तालिका जोड़ना सरल है और आपके दस्तावेज़ों की उपयोगिता को काफी हद तक बढ़ाता है। इन चरणों का पालन करके, आप जटिल दस्तावेज़ों को कुशलतापूर्वक व्यवस्थित और नेविगेट कर सकते हैं।

## अक्सर पूछे जाने वाले प्रश्न

### क्या मैं विषय-सूची के स्वरूप को अनुकूलित कर सकता हूँ?
हां, आप .NET API के लिए Aspose.Words का उपयोग करके सामग्री तालिका की उपस्थिति और व्यवहार को अनुकूलित कर सकते हैं।

### क्या Aspose.Words स्वचालित रूप से फ़ील्ड अपडेट करने का समर्थन करता है?
हां, Aspose.Words आपको दस्तावेज़ परिवर्तनों के आधार पर सामग्री तालिका जैसे फ़ील्ड को गतिशील रूप से अपडेट करने की अनुमति देता है।

### क्या मैं एक ही दस्तावेज़ में एकाधिक विषय-सूची तैयार कर सकता हूँ?
Aspose.Words एक ही दस्तावेज़ में विभिन्न सेटिंग्स के साथ कई विषय-सूची बनाने का समर्थन करता है।

### क्या Aspose.Words माइक्रोसॉफ्ट वर्ड के विभिन्न संस्करणों के साथ संगत है?
हां, Aspose.Words माइक्रोसॉफ्ट वर्ड प्रारूपों के विभिन्न संस्करणों के साथ संगतता सुनिश्चित करता है।

### मैं Aspose.Words के लिए और अधिक सहायता और समर्थन कहां पा सकता हूं?
 अधिक सहायता के लिए, कृपया यहां जाएं[Aspose.Words फ़ोरम](https://forum.aspose.com/c/words/8) या जाँच करें[आधिकारिक दस्तावेज](https://reference.aspose.com/words/net/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
