---
category: general
date: 2026-07-19
description: Aspose.Words for C# का उपयोग करके पाई चार्ट स्लाइस को एक्सप्लोड करें।
  जानें कैसे पाई स्लाइस को एक्सप्लोड करें, डोनट होल का आकार समायोजित करें, और चार्ट
  डेटा पॉइंट्स को जल्दी बदलें।
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- explode pie chart slice
- how to explode pie slice
- adjust doughnut hole size
- change chart data points
language: hi
lastmod: 2026-07-19
og_description: Aspose.Words for C# के साथ पाई चार्ट स्लाइस को एक्सप्लोड करें। यह
  गाइड आपको दिखाता है कि पाई स्लाइस को कैसे एक्सप्लोड करें, डोनट होल का आकार कैसे
  समायोजित करें, और चार्ट डेटा पॉइंट्स को प्रभावी ढंग से कैसे बदलें।
og_image_alt: Screenshot showing an exploded pie chart slice created with Aspose.Words
  in C#
og_title: C# में पाई चार्ट स्लाइस को बाहर निकालें – Aspose.Words ट्यूटोरियल
schemas:
- author: Aspose
  dateModified: '2026-07-19'
  description: Explode pie chart slice using Aspose.Words for C#. Learn how to explode
    pie slice, adjust doughnut hole size, and change chart data points quickly.
  headline: Explode Pie Chart Slice in C# with Aspose.Words – Full Guide
  type: TechArticle
- description: Explode pie chart slice using Aspose.Words for C#. Learn how to explode
    pie slice, adjust doughnut hole size, and change chart data points quickly.
  name: Explode Pie Chart Slice in C# with Aspose.Words – Full Guide
  steps:
  - name: Install and Reference Aspose.Words
    text: 'First things first, add the Aspose.Words package to your project. In the
      Package Manager Console:'
  - name: Load the Word Document Containing the Chart
    text: We need a `Document` object that points at the `.docx` with the chart you
      want to modify.
  - name: Retrieve the First Chart Node
    text: Most examples assume a single chart, so we’ll grab the first one. If you
      have multiple charts, adjust the index accordingly.
  - name: Explode the First Slice of a Pie Chart
    text: Now the star of the show—**how to explode pie slice**. We’ll set the `Exploded`
      property of the first data point.
  - name: Adjust Doughnut Hole Size (If It’s a Doughnut Chart)
    text: If your chart happens to be a doughnut, you might want to **adjust doughnut
      hole size**. The hole size is a percentage of the chart’s radius.
  - name: Change Chart Data Points (Optional)
    text: Sometimes you need to **change chart data points**—maybe you’ve updated
      the underlying numbers and want the visual to reflect that.
  - name: Save the Modified Document
    text: Finally, write the changes back to disk. You can overwrite the original
      or create a new file—up to you.
  - name: What’s Next?
    text: '- **Style the exploded slice** (change fill color, border, or add a data
      label). Search for “Aspose.Words chart formatting”. - **Automate batch processing**
      of multiple documents—loop through a folder, explode slices, and save new versions.
      - **Combine with Aspose.Slides** if you need the same chart'
  type: HowTo
tags:
- Aspose.Words
- C#
- Chart Manipulation
title: C# में Aspose.Words के साथ पाई चार्ट स्लाइस को बाहर निकालें – पूर्ण गाइड
url: /hi/net/programming-with-charts/explode-pie-chart-slice-in-c-with-aspose-words-full-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C# में Aspose.Words के साथ पाई चार्ट स्लाइस को एक्सप्लोड करें – पूर्ण गाइड

क्या आपने कभी सोचा है कि **explode pie chart slice** को C# का उपयोग करके Word दस्तावेज़ में कैसे किया जाए? आप अकेले नहीं हैं। चाहे आप एक सेल्स डेक तैयार कर रहे हों या सर्वे परिणामों को विज़ुअलाइज़ कर रहे हों, एक एक्सप्लोडेड स्लाइस ठीक वही जगह ध्यान आकर्षित कर सकता है जहाँ आप चाहते हैं। इस ट्यूटोरियल में हम पूरी प्रक्रिया को कवर करेंगे—दस्तावेज़ लोड करना, चार्ट निकालना, पहली स्लाइस को एक्सप्लोड करना, डोनट होल को समायोजित करना, और यहाँ तक कि चार्ट डेटा पॉइंट्स को बदलना।

हम उन द्वितीयक अवधारणाओं को भी शामिल करेंगे जिनकी आप तलाश कर रहे हो सकते हैं: **how to explode pie slice**, **adjust doughnut hole size**, और **change chart data points**। कोई फालतू बात नहीं, सिर्फ एक पूर्ण, कॉपी‑पेस्ट‑रेडी समाधान।

---

## आपको क्या चाहिए

- **Aspose.Words for .NET** (2026‑07‑19 तक का नवीनतम संस्करण)। आप इसे NuGet से `Install-Package Aspose.Words` कमांड से प्राप्त कर सकते हैं।
- एक **.NET 6+** प्रोजेक्ट (या यदि आप लेगेसी पर हैं तो .NET Framework 4.7.2+)।
- एक Word फ़ाइल (`Chart.docx`) जिसमें पहले से ही पाई या डोनट चार्ट हो। यदि आपके पास नहीं है, तो Word में जल्दी से एक चार्ट बनाकर सहेज लें।

बस इतना ही—कोई अतिरिक्त लाइब्रेरी नहीं, कोई COM इंटरऑप नहीं, सिर्फ शुद्ध मैनेज्ड कोड।

## पाई चार्ट स्लाइस को एक्सप्लोड करें – चरण‑दर‑चरण कार्यान्वयन

नीचे हम कार्य को छोटे‑छोटे चरणों में विभाजित करते हैं। प्रत्येक सेक्शन में स्पष्ट हेडिंग, कोड स्निपेट, और *क्यों* हम यह कर रहे हैं, इसका छोटा विवरण होता है।

### चरण 1: Aspose.Words स्थापित और संदर्भित करें

सबसे पहले, Aspose.Words पैकेज को अपने प्रोजेक्ट में जोड़ें। पैकेज मैनेजर कंसोल में:

```powershell
Install-Package Aspose.Words
```

> **Pro tip:** यदि आप Visual Studio के बिल्ट‑इन NuGet UI का उपयोग कर रहे हैं, तो “Aspose.Words” खोजें और Install पर क्लिक करें। यह सुनिश्चित करता है कि आपको नवीनतम बग फिक्स और चार्ट के साथ बॉक्स से बाहर काम करने की क्षमता मिले।

### चरण 2: चार्ट वाले Word दस्तावेज़ को लोड करें

हमें एक `Document` ऑब्जेक्ट चाहिए जो उस `.docx` की ओर इशारा करता हो जिसमें वह चार्ट हो जिसे आप संशोधित करना चाहते हैं।

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

// Load the source document
Document doc = new Document(@"C:\Charts\Chart.docx");

// Verify that the document actually contains a chart
if (doc.GetChildNodes(NodeType.Chart, true).Count == 0)
{
    throw new InvalidOperationException("No chart found in the specified document.");
}
```

> **Why this matters:** `Document` Aspose.Words में हर ऑपरेशन का एंट्री पॉइंट है। चार्ट की जाँच पहले ही करके, हम बाद में स्लाइस को एक्सप्लोड करने की कोशिश में null रेफ़रेंस से बचते हैं।

### चरण 3: पहला चार्ट नोड प्राप्त करें

अधिकांश उदाहरण एक ही चार्ट मानते हैं, इसलिए हम पहला चार्ट ले लेंगे। यदि आपके पास कई चार्ट हैं, तो इंडेक्स को उसी अनुसार समायोजित करें।

```csharp
// Grab the first chart in the document (index 0)
Chart chart = (Chart)doc.GetChild(NodeType.Chart, 0, true);
```

> **Note:** `Chart` में कास्ट करना सुरक्षित है क्योंकि हमने पहले ही पुष्टि कर ली है कि चार्ट मौजूद है। यह ऑब्जेक्ट हमें सीरीज़, डेटा पॉइंट्स, और चार्ट‑टाइप‑स्पेसिफिक सेटिंग्स तक पहुंच देता है।

### चरण 4: पाई चार्ट की पहली स्लाइस को एक्सप्लोड करें

अब मुख्य भाग—**how to explode pie slice**। हम पहले डेटा पॉइंट की `Exploded` प्रॉपर्टी सेट करेंगे।

```csharp
// Ensure the chart is a Pie (or Pie3D) before exploding
if (chart.ChartType == ChartType.Pie || chart.ChartType == ChartType.Pie3D)
{
    // Explode the first slice (index 0)
    chart.PieChartData.Series[0].DataPoints[0].Exploded = true;
}
else
{
    Console.WriteLine("The chart is not a pie chart; skipping explode operation.");
}
```

> **Why this works:** `Exploded` Word को बताता है कि वह स्लाइस को केंद्र से बाहर खींचे, जिससे क्लासिक “exploded pie” इफ़ेक्ट बनता है। यह प्रॉपर्टी बूलियन है, इसलिए `true` सेट करने से काम हो जाता है।

### चरण 5: डोनट चार्ट के होल साइज को समायोजित करें (यदि यह डोनट चार्ट है)

यदि आपका चार्ट डोनट है, तो आप **adjust doughnut hole size** करना चाह सकते हैं। होल साइज चार्ट के रेडियस का प्रतिशत होता है।

```csharp
// Check for Doughnut chart type and modify the hole size
if (chart.ChartType == ChartType.Doughnut)
{
    // Set the hole size to 30% (range: 0–100)
    chart.DoughnutChartData.HoleSize = 30;
}
```

> **What the number means:** `30` का मान मतलब है कि अंदर का सर्कल कुल रेडियस का 30 % लेगा, जिससे बाहरी रिंग मोटी हो जाएगी।

### चरण 6: चार्ट डेटा पॉइंट्स बदलें (वैकल्पिक)

कभी‑कभी आपको **change chart data points** करने की ज़रूरत पड़ती है—शायद आपने मूल संख्याएँ अपडेट कर दी हों और विज़ुअल को भी उसी अनुसार बदलना चाहते हों।

```csharp
// Example: Update the second data point's value to 75
if (chart.PieChartData?.Series?.Count > 0 && chart.PieChartData.Series[0].DataPoints.Count > 1)
{
    chart.PieChartData.Series[0].DataPoints[1].Value = 75;
}
```

> **Why you’d do this:** डेटा पॉइंट का मान बदलने से स्लाइस प्रतिशत स्वचालित रूप से पुनः गणना हो जाता है, जिससे चार्ट सटीक रहता है बिना Word में मैन्युअल एडिट किए।

### चरण 7: संशोधित दस्तावेज़ को सहेजें

अंत में, बदलावों को डिस्क पर लिखें। आप मूल फ़ाइल को ओवरराइट कर सकते हैं या नई फ़ाइल बना सकते हैं—आपकी पसंद।

```csharp
// Save the document with the exploded slice and adjusted doughnut hole
doc.Save(@"C:\Charts\FormattedChart.docx");

// Quick confirmation
Console.WriteLine("Document saved successfully with exploded pie chart slice.");
```

> **Tip:** यदि आपको स्पष्ट रूप से फॉर्मेट बताना है तो `SaveFormat.Docx` उपयोग करें, लेकिन `Save(string)` फ़ाइल एक्सटेंशन से फॉर्मेट को स्वचालित रूप से पहचान लेता है।

## अपेक्षित परिणाम

जब आप `FormattedChart.docx` को Microsoft Word में खोलेंगे, तो आपको दिखना चाहिए:

- पाई चार्ट की पहली स्लाइस **exploded** होकर बाहर की ओर निकली हुई।
- यदि चार्ट डोनट है, तो केंद्रीय होल अब रेडियस का **30 %** ले रहा है।
- सभी संशोधित डेटा पॉइंट्स आपके द्वारा सेट किए गए नए मानों को दर्शाते हैं।

नीचे एक मॉक‑अप दिया गया है कि एक्सप्लोडेड स्लाइस कैसी दिखती है (केवल चित्रण हेतु)।

![Aspose.Words के साथ C# में बनाया गया एक्सप्लोडेड पाई चार्ट स्लाइस](exploded-pie-slice.png)

*Alt text:* **एक्सप्लोडेड पाई चार्ट स्लाइस** जो Word दस्तावेज़ में एक निकली हुई सेगमेंट को दर्शाता है।

## सामान्य प्रश्न और किनारे के मामलों

**यदि चार्ट पाई या डोनट नहीं है तो क्या होगा?**  
कोड `ChartType` की जाँच करता है इससे पहले कि `Exploded` या `HoleSize` लागू किया जाए। बार, लाइन, या एरिया चार्ट्स में ये प्रॉपर्टी मौजूद नहीं होतीं, इसलिए लॉजिक उन्हें सुरक्षित रूप से स्किप कर देता है।

**क्या मैं कई स्लाइस को एक्सप्लोड कर सकता हूँ?**  
बिल्कुल। `chart.PieChartData.Series[0].DataPoints` पर लूप लगाएँ और इच्छित किसी भी इंडेक्स पर `Exploded = true` सेट करें।

**क्या मुझे संस्कृति‑विशिष्ट नंबर फ़ॉर्मेट की चिंता करनी चाहिए?**  
Aspose.Words संख्यात्मक मानों को डबल के रूप में स्टोर करता है, लोकेल से स्वतंत्र, इसलिए कॉमा बनाम डॉट की समस्या नहीं होगी।

**हेडर/फ़ूटर में एम्बेडेड चार्ट्स के बारे में क्या?**  
`doc.GetChildNodes(NodeType.Chart, true)` का उपयोग करके सभी चार्ट प्राप्त करें, फिर प्रत्येक नोड के `ParentNode` को जांचें कि वह कहाँ स्थित है। वही एक्सप्लोड लॉजिक लागू होता है।

## निष्कर्ष

अब आपके पास Aspose.Words का उपयोग करके C# में **explode pie chart slice** करने का एक ठोस, कॉपी‑पेस्ट‑रेडी समाधान है। हमने पूरे वर्कफ़्लो को कवर किया—दस्तावेज़ लोड करना, चार्ट प्राप्त करना, स्लाइस को एक्सप्लोड करना, **adjusting doughnut hole size**, **changing chart data points**, और अंत में फ़ाइल को सहेजना।

बिना झिझक प्रयोग करें: कोई अलग स्लाइस एक्सप्लोड करें, होल साइज को 45 % तक बढ़ाएँ, या एक साथ कई डेटा पॉइंट्स अपडेट करें। Aspose.Words API इन बदलावों को आसान बनाता है, और Word फ़ाइल खोलते ही परिवर्तन तुरंत दिखते हैं।

### आगे क्या?

- **Style the exploded slice** (fill color बदलें, बॉर्डर जोड़ें, या डेटा लेबल जोड़ें)। “Aspose.Words chart formatting” खोजें।
- **Automate batch processing** कई दस्तावेज़ों के लिए—फ़ोल्डर में लूप करें, स्लाइस एक्सप्लोड करें, और नई संस्करण सहेजें।
- **Combine with Aspose.Slides** यदि आपको वही चार्ट PowerPoint डेक में चाहिए।

यदि आपके पास चार्ट मैनिपुलेशन के बारे में और प्रश्न हैं, या अन्य चार्ट प्रकारों में गहराई से जाना चाहते हैं, तो नीचे टिप्पणी करें, और कोडिंग का आनंद लें!

## अब आपको क्या सीखना चाहिए?

निम्नलिखित ट्यूटोरियल्स उन विषयों को कवर करते हैं जो इस गाइड में दिखाए गए तकनीकों पर आधारित हैं। प्रत्येक संसाधन में पूर्ण कार्यशील कोड उदाहरण और चरण‑दर‑चरण व्याख्याएँ शामिल हैं, जिससे आप अतिरिक्त API फीचर्स को मास्टर कर सकें और अपने प्रोजेक्ट्स में वैकल्पिक इम्प्लीमेंटेशन एप्रोच को एक्सप्लोर कर सकें।

- [Insert Column Chart in Word Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-column-chart/)
- [Insert a Simple Column Chart in Word Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-simple-column-chart/)
- [Insert Area Chart in Word Document | Aspose.Words for .NET](/words/english/net/working-with-charts/insert-area-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}