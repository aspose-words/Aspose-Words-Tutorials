---
category: general
date: 2026-10-13
description: C# का उपयोग करके वर्ड में चार्ट को कस्टम नंबर फ़ॉर्मेट (जैसे मुद्रा)
  लागू करके चार्ट एक्सिस को कैसे फ़ॉर्मेट करें। चरण‑दर‑चरण कोड उदाहरण शामिल है।
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to format chart
- apply custom number format
- custom number format word
- how to set chart
- change chart axis format
language: hi
lastmod: 2026-10-13
og_description: C# के साथ Word में चार्ट को फॉर्मेट करने से आप चार्ट एक्सिस पर कस्टम
  नंबर फॉर्मेट लागू कर सकते हैं, जिससे मान मुद्रा, प्रतिशत या किसी भी पैटर्न में दिखाए
  जा सकें। चरण‑दर‑चरण गाइड का पालन करें।
og_image_alt: Word chart showing axis values formatted as currency after applying
  custom number format
og_title: C# के साथ Word में चार्ट को कैसे फ़ॉर्मेट करें – कस्टम नंबर फ़ॉर्मेट
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: How to format chart in Word with C# by applying a custom number format,
    such as currency, to chart axes. Step‑by‑step code example included.
  headline: How to format chart in Word with C# and custom number formats
  type: TechArticle
tags:
- Aspose.Words
- C#
- chart formatting
title: C# और कस्टम नंबर फ़ॉर्मैट्स के साथ Word में चार्ट को कैसे फ़ॉर्मेट करें
url: /hi/net/programming-with-charts/how-to-format-chart-in-word-with-c-and-custom-number-formats/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C# के साथ Word में चार्ट को कस्टम नंबर फ़ॉर्मेट के साथ कैसे फ़ॉर्मेट करें

C# के साथ Word में चार्ट को फ़ॉर्मेट करना एक सामान्य आवश्यकता है जब आपको डेटा को पेशेवर ढंग से प्रस्तुत करना हो। यह गाइड आपको **Aspose.Words for .NET** का उपयोग करके चार्ट की एक्सिस पर कस्टम नंबर फ़ॉर्मेट लागू करने का तरीका दिखाता है, ताकि मान बिल्कुल वही दिखें जैसा आप चाहते हैं।

आप सीखेंगे कि DOCX फ़ाइल को कैसे लोड करें, पहला चार्ट कैसे खोजें, वर्तमान फ़ॉर्मेट को पढ़ें, और फिर दो दशमलव के साथ मुद्रा जैसे नए पैटर्न को सेट करें। ट्यूटोरियल अतिरिक्त सीरीज़ के लिए चार्ट एक्सिस फ़ॉर्मेट बदलने और आवश्यकता पड़ने पर फ़ॉर्मेट रीसेट करने के बारे में भी बताता है।

## आवश्यकताएँ

* .NET 6.0 या बाद का संस्करण स्थापित हो  
* Visual Studio 2022 (या कोई भी IDE जो .NET को सपोर्ट करता हो) प्रोजेक्ट  
* **Aspose.Words for .NET** NuGet पैकेज (`Aspose.Words`)  
* एक Word दस्तावेज़ (`input.docx`) जिसमें कम से कम एक चार्ट हो  

आप निम्नलिखित कमांड के साथ पैकेज जोड़ सकते हैं:

```bash
dotnet add package Aspose.Words
```

## Aspose.Words का उपयोग करके Word में चार्ट को कैसे फ़ॉर्मेट करें

निम्नलिखित पूर्ण प्रोग्राम हर चरण को दर्शाता है जो **चार्ट को फ़ॉर्मेट** करने के लिए आवश्यक है। फ़ाइल को `Program.cs` के रूप में सहेजें और कमांड लाइन या अपने IDE से चलाएँ।

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // Step 1: Load the Word document that contains the chart
        Document doc = new Document("input.docx");

        // Step 2: Retrieve the first chart shape from the document
        Chart chart = (Chart)doc.GetChild(NodeType.Shape, 0, true);
        if (chart == null)
        {
            Console.WriteLine("No chart found in the document.");
            return;
        }

        // Step 3: Access the X‑value collection of the first data series
        ChartXValueCollection xValues = chart.ChartData.Series[0].XValues;

        // Optional: Show the current number format code
        Console.WriteLine($"Current format code: {xValues.FormatCode}");

        // Step 4: Apply a custom number format (currency with two decimals)
        // The format string follows Excel/Word conventions.
        xValues.FormatCode = "\"$\"#,##0.00";

        // Step 5: Save the modified document
        doc.Save("output_formatted.docx");
        Console.WriteLine("Chart axis format applied and document saved as output_formatted.docx");
    }
}
```

### प्रत्येक चरण की व्याख्या

| चरण | क्यों महत्वपूर्ण है | मुख्य कोड |
|------|-------------------|----------|
| **Load the document** | आपको Word फ़ाइल के साथ काम करने के लिए एक `Document` ऑब्जेक्ट चाहिए। | `new Document("input.docx")` |
| **Retrieve the chart** | `Chart` ऑब्जेक्ट्स `Shape` नोड्स के रूप में संग्रहीत होते हैं; कास्टिंग करने से आप चार्ट‑विशिष्ट API का उपयोग कर सकते हैं। | `(Chart)doc.GetChild(NodeType.Shape, 0, true)` |
| **Access X‑values** | एक्सिस फ़ॉर्मेटिंग डेटा सीरीज़ के वैल्यू कलेक्शन पर लागू होती है। | `chart.ChartData.Series[0].XValues` |
| **Read current format** | मौजूदा `FormatCode` को जानना आपको यह तय करने में मदद करता है कि इसे बदलना है या बढ़ाना है। | `xValues.FormatCode` |
| **Set custom format** | `FormatCode` प्रॉपर्टी किसी भी Excel‑संगत पैटर्न को स्वीकार करती है, जिससे आप मुद्रा, प्रतिशत, तिथियों आदि को सक्षम कर सकते हैं। | `xValues.FormatCode = "\"$\"#,##0.00"` |
| **Save the document** | परिवर्तनों को सहेजने से नया एक्सिस फ़ॉर्मेट DOCX फ़ाइल में वापस लिखा जाता है। | `doc.Save("output_formatted.docx")` |

प्रोग्राम चलाने पर `output_formatted.docx` बनता है। इसे Word में खोलें और आप देखेंगे कि चार्ट की X‑axis मान **$1,234.00**, **$2,345.00**, … के रूप में दिख रहे हैं, साधारण संख्याओं के बजाय।

## चार्ट एक्सिस पर कस्टम नंबर फ़ॉर्मेट लागू करें

यदि आपको Y‑axis या अतिरिक्त सीरीज़ पर **कस्टम नंबर फ़ॉर्मेट** लागू करना हो, तो प्रक्रिया समान है—सिर्फ एक अलग कलेक्शन को टार्गेट करें:

```csharp
// Apply format to Y‑values of the second series
ChartYValueCollection yValues = chart.ChartData.Series[1].YValues;
yValues.FormatCode = "0%"; // percentage format
```

> **प्रो टिप:** फ़ॉर्मेट स्ट्रिंग के अंदर डबल कोट्स का उपयोग करके लिटरल कैरेक्टर्स एम्बेड करें (जैसे, मुद्रा के लिए `"$"`). ऊपर दिखाए अनुसार कोट्स को एस्केप करें।

## कस्टम नंबर फ़ॉर्मेट शब्द – Word के लोकेल को संभालना

Word दस्तावेज़ के लोकेल का सम्मान करता है जब वह नंबर फ़ॉर्मेट को इंटरप्रेट करता है। यदि दस्तावेज़ गैर‑US लोकेल का उपयोग करता है, तो आपको फ़ॉर्मेट स्ट्रिंग को समायोजित करने की आवश्यकता हो सकती है:

```csharp
// German locale – uses comma as decimal separator
xValues.FormatCode = "\"€\" #.##0,00";
```

जर्मन भाषा सेटिंग्स वाले दस्तावेज़ पर फ़ॉर्मेट का परीक्षण करने से पुष्टि होती है कि मान **€ 1.234,00** के रूप में दिखते हैं।

## प्रोग्रामेटिक रूप से चार्ट प्रॉपर्टीज़ सेट करना

एक्सिस फ़ॉर्मेटिंग के अलावा, आप अक्सर **चार्ट** शीर्षक, लेजेंड या डेटा लेबल सेट करना चाहते हैं। यहाँ एक छोटा स्निपेट है जो दिखाता है कि एक्सिस फ़ॉर्मेट करने के बाद चार्ट शीर्षक कैसे सेट करें:

```csharp
chart.Title.Text = "Sales by Quarter";
chart.Title.IsVisible = true;
```

कस्टम नंबर फ़ॉर्मेट के साथ इसे मिलाने से आपको एक पूरी तरह से पॉलिश्ड चार्ट मिलता है जो रिपोर्टिंग के लिए तैयार है।

## उपयोगकर्ता इनपुट के आधार पर चार्ट एक्सिस फ़ॉर्मेट को डायनामिक रूप से बदलना

वास्तविक दुनिया के अनुप्रयोगों में आप उपयोगकर्ताओं को रन‑टाइम पर फ़ॉर्मेट चुनने की अनुमति दे सकते हैं। निम्नलिखित मेथड फ़ॉर्मेटिंग लॉजिक को एन्कैप्सुलेट करता है:

```csharp
static void SetAxisFormat(Chart chart, int seriesIndex, string formatCode)
{
    var xVals = chart.ChartData.Series[seriesIndex].XValues;
    xVals.FormatCode = formatCode;
}
```

आप मुद्रा के लिए `SetAxisFormat(chart, 0, "\"$\"#,##0.00")` या प्रतिशत के लिए `SetAxisFormat(chart, 0, "0%")` कॉल कर सकते हैं। यह तरीका आपके मुख्य कोड को साफ़ रखता है और भविष्य के विस्तारों का समर्थन करता है।

## किनारे के मामलों और सामान्य समस्याएँ

| स्थिति | ध्यान रखने योग्य बातें | सुझावित समाधान |
|-----------|-------------------|---------------|
| दस्तावेज़ में **कोई चार्ट नहीं** | `GetChild` `null` लौटाता है, जिससे कास्ट एक्सेप्शन होता है। | कास्ट करने से पहले `null` की जाँच करें (उदाहरण देखें)। |
| एक ही दस्तावेज़ में कई चार्ट | कोड हमेशा पहला चार्ट (`index 0`) ले लेता है। | `doc.GetChildNodes(NodeType.Shape, true)` पर लूप करें और `ShapeType.Chart` द्वारा फ़िल्टर करें। |
| सीरीज़ **बिना X‑values** (जैसे, पाई चार्ट) | `XValues` तक पहुँचने से `ArgumentOutOfRangeException` हो सकता है। | फ़ॉर्मेट करने से पहले सुनिश्चित करें कि `Series[i].XValues` खाली नहीं है। |
| लोकेल मिसमैच | मुद्रा प्रतीक गलत दिख सकता है। | `xValues.FormatCode` को उपयुक्त लोकेल प्रतीकों के साथ स्पष्ट रूप से सेट करें। |

## अपेक्षित आउटपुट

नमूना प्रोग्राम चलाने के बाद, **output_formatted.docx** खोलें। चार्ट की X‑axis को चुने हुए कस्टम फ़ॉर्मेट में संख्याएँ दिखानी चाहिए। मुद्रा उदाहरण के लिए, एक्सिस लेबल इस प्रकार दिखेंगे:

```
$1,000.00
$2,000.00
$3,000.00
```

यदि आपने Y‑values पर प्रतिशत फ़ॉर्मेट लागू किया है, तो Y‑axis लेबल इस प्रकार दिखेंगे:

```
10%
20%
30%
```

## निष्कर्ष

इस ट्यूटोरियल ने आपको C# के साथ Word में **चार्ट को फ़ॉर्मेट** करने का तरीका दिखाया, जहाँ आप एक्सिस मानों पर **कस्टम नंबर फ़ॉर्मेट** लागू करते हैं। अब आपके पास मुद्रा, प्रतिशत या किसी भी अन्य संख्यात्मक पैटर्न को सेट करने के लिए पुन: उपयोग योग्य पैटर्न है, साथ ही लोकेल, कई सीरीज़ और डायनामिक उपयोगकर्ता इनपुट को संभालने के लिए मार्गदर्शन भी।

अगले चरण में आप **चार्ट** शीर्षक, डेटा लेबल सेट करना या `ChartRenderer` का उपयोग करके चार्ट को इमेज के रूप में एक्सपोर्ट करना देख सकते हैं। ये विषय यहाँ कवर किए गए अवधारणाओं पर सीधे आधारित हैं और आपको पूरी तरह से स्वचालित रिपोर्टिंग समाधान बनाने में मदद करेंगे।

---

## आगे आप क्या सीखें?

निम्नलिखित ट्यूटोरियल उन विषयों को कवर करते हैं जो इस गाइड में प्रदर्शित तकनीकों पर आधारित हैं। प्रत्येक संसाधन में पूर्ण कार्यशील कोड उदाहरण और चरण‑दर‑चरण व्याख्याएँ शामिल हैं, जो आपको अतिरिक्त API फीचर्स में निपुण बनने और अपने प्रोजेक्ट में वैकल्पिक कार्यान्वयन दृष्टिकोणों का अन्वेषण करने में मदद करेंगे।

- [चार्ट में एक्सिस के लिए नंबर फ़ॉर्मेट](/words/english/net/programming-with-charts/number-format-for-axis/)
- [चार्ट में डेटा लेबल की संख्या फ़ॉर्मेट करें](/words/english/net/programming-with-charts/format-number-of-data-label/)
- [Aspose.Words for .NET का उपयोग करके Word लाइन चार्ट में सेकेंडरी X‑Axis को फ़ॉर्मेट करें और डिस्प्ले यूनिट्स को थाउज़ेंड्स पर सेट करें](/words/english/net/programming-with-charts/format-secondary-axis/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}