---
category: general
date: 2026-09-11
description: Aspose.Words के साथ चार्ट लेबल संपादन ट्यूटोरियल, जिसमें चार्ट लेबल की
  स्थिति बदलना, चार्ट डेटा लेबल को कस्टमाइज़ करना, चार्ट श्रेणी नाम को छिपाना और चार्ट
  लेबल मान दिखाना शामिल है।
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- edit chart label tutorial
- change chart label position
- customize chart data label
- hide chart category name
- show chart label value
language: hi
lastmod: 2026-09-11
og_description: Edit chart label tutorial आपको चार्ट लेबल की स्थिति बदलने, चार्ट डेटा
  लेबल को कस्टमाइज़ करने, चार्ट श्रेणी नाम को छिपाने और Aspose.Words for .NET का उपयोग
  करके चार्ट लेबल मान दिखाने के माध्यम से मार्गदर्शन करता है।
og_image_alt: Screenshot of a Word document displaying a chart with customized data
  labels
og_title: चार्ट लेबल संपादन ट्यूटोरियल – C# में Word चार्ट लेबल को कस्टमाइज़ करें
schemas:
- author: Aspose
  dateModified: '2026-09-11'
  description: Edit chart label tutorial showing how to change chart label position,
    customize chart data label, hide chart category name, and show chart label value
    with Aspose.Words.
  headline: Edit chart label tutorial – modify Word chart labels in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Chart manipulation
title: चार्ट लेबल संपादन ट्यूटोरियल – C# में Word चार्ट लेबल संशोधित करें
url: /hi/net/programming-with-charts/edit-chart-label-tutorial-modify-word-chart-labels-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# चार्ट लेबल ट्यूटोरियल संपादित करें – C# में Word चार्ट लेबल संशोधित करें

यदि आपको Word दस्तावेज़ के लिए **edit chart label tutorial** की आवश्यकता है, तो यह गाइड आपको दिखाएगा कि Aspose.Words for .NET का उपयोग करके चार्ट लेबल की स्थिति कैसे बदलें, चार्ट डेटा लेबल को कस्टमाइज़ करें, चार्ट श्रेणी नाम को छिपाएँ, और चार्ट लेबल मान को दिखाएँ। आप एक पूर्ण, चलाने योग्य उदाहरण देखेंगे जिसे आप किसी भी C# प्रोजेक्ट में डाल सकते हैं।

चार्ट लेबल के साथ काम करना रिपोर्ट, इनवॉइस या डैशबोर्ड को प्रोग्रामेटिक रूप से जेनरेट करते समय एक सामान्य आवश्यकता है। यह ट्यूटोरियल हर कदम को कवर करता है—डॉक्यूमेंट लोड करने से लेकर बदलावों को सहेजने तक—ताकि आप मैन्युअल एडिटिंग के बिना परिष्कृत चार्ट बना सकें।

## Prerequisites

शुरू करने से पहले सुनिश्चित करें कि आपके पास है:

* .NET 6.0 या बाद का संस्करण स्थापित हो  
* एक वैध Aspose.Words for .NET लाइसेंस (या एक अस्थायी इवैल्यूएशन कुंजी)  
* Visual Studio 2022 या कोई भी C#‑संगत IDE  
* एक Word फ़ाइल (`Chart.docx`) जिसमें कम से कम एक चार्ट हो  

`Aspose.Words` के अलावा कोई अतिरिक्त NuGet पैकेज आवश्यक नहीं है।

## Step 1: Set up the project and import namespaces

एक नया कंसोल एप्लिकेशन बनाएं और Aspose.Words NuGet पैकेज जोड़ें:

```bash
dotnet new console -n ChartLabelEditor
cd ChartLabelEditor
dotnet add package Aspose.Words
```

`Program.cs` खोलें और आवश्यक नेमस्पेस इम्पोर्ट करें:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;
```

ये नेमस्पेस आपको `Document` क्लास के माध्यम से Word फ़ाइलों को संभालने और चार्ट तत्वों को मैनीपुलेट करने के लिए `Chart` क्लासेज़ तक पहुंच प्रदान करते हैं।

## Step 2: Load the Word document that contains a chart

पहली कार्यशील पंक्ति स्रोत दस्तावेज़ को लोड करती है। `YOUR_DIRECTORY` को उस वास्तविक पथ से बदलें जहाँ `Chart.docx` स्थित है।

```csharp
// Load the Word document containing the chart
Document doc = new Document(@"YOUR_DIRECTORY\Chart.docx");
```

डॉक्यूमेंट को लोड करने से एक इन‑मेमोरी प्रतिनिधित्व बनता है जिसे आप ट्रैवर्स और मॉडिफाई कर सकते हैं।

## Step 3: Retrieve the first chart in the document

चार्ट `NodeType.Chart` प्रकार के चाइल्ड नोड्स के रूप में संग्रहीत होते हैं। `GetChild` मेथड डॉक्यूमेंट ट्री को सर्च करता है और वह चार्ट रिटर्न करता है जिसे आप एडिट करना चाहते हैं।

```csharp
// Retrieve the first chart object (index 0)
Chart chart = (Chart)doc.GetChild(NodeType.Chart, 0, true);
```

यदि दस्तावेज़ में कई चार्ट हैं, तो आप इंडेक्स बदलकर किसी अन्य चार्ट को टारगेट कर सकते हैं।

## Step 4: Access and customize the data label of the first series

हर चार्ट सीरीज़ का एक `DataLabel` ऑब्जेक्ट होता है जो लेबल के दिखने के तरीके को नियंत्रित करता है। नीचे दिया गया कोड ट्यूटोरियल के द्वितीयक कीवर्ड्स द्वारा आवश्यक चार प्रमुख कस्टमाइज़ेशन को दर्शाता है।

```csharp
// Access the data label of the first series (index 0)
ChartDataLabel label = chart.Series[0].DataLabel;

// Change chart label position – place the label in the center of each data point
label.Position = DataLabelPosition.Center;

// Customize chart data label – use a custom separator between label parts
label.Separator = "; ";

// Hide chart category name – the category text will not be shown
label.ShowCategoryName = false;

// Show chart label value – the numeric value of the point will be displayed
label.ShowValue = true;
```

**इन सेटिंग्स का महत्व क्यों है**

* `DataLabelPosition.Center` लेबल को डिफ़ॉल्ट बाहर‑ऑफ़‑पॉइंट स्थान से डेटा पॉइंट के मध्य में ले जाता है, जिससे बिंदु घने होने पर चार्ट पढ़ना आसान हो जाता है।  
* एक कस्टम `Separator` सेट करने से आप नियंत्रित कर सकते हैं कि सीरीज़ नाम, वैल्यू और अन्य भाग कैसे जोड़ें।  
* श्रेणी नाम को छिपाना (`ShowCategoryName = false`) दृश्य अव्यवस्था को कम करता है जब श्रेणी पहले से ही एक्सिस से स्पष्ट हो।  
* `ShowValue` को सक्षम करने से वास्तविक डेटा वैल्यू दिखती है, जो अक्सर वित्तीय या सांख्यिकीय रिपोर्टों में आवश्यक होती है।

## Step 5: Save the modified document

लेबल प्रॉपर्टीज़ को समायोजित करने के बाद, बदलावों को नई फ़ाइल में सहेजें:

```csharp
// Save the updated document with customized chart labels
doc.Save(@"YOUR_DIRECTORY\CustomLabelChart.docx");
```

नई फ़ाइल (`CustomLabelChart.docx`) में वही चार्ट लेआउट रहेगा, लेकिन लेबल का स्वरूप आपने परिभाषित किया हुआ होगा।

## Full source code

नीचे पूरा, तैयार‑से‑चलाने वाला प्रोग्राम दिया गया है। इसे `Program.cs` में कॉपी करें, फ़ाइल पाथ समायोजित करें, और प्रोजेक्ट चलाएँ।

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

namespace ChartLabelEditor
{
    class Program
    {
        static void Main(string[] args)
        {
            // 1️⃣ Load the Word document that contains a chart
            Document doc = new Document(@"YOUR_DIRECTORY\Chart.docx");

            // 2️⃣ Retrieve the first chart in the document
            Chart chart = (Chart)doc.GetChild(NodeType.Chart, 0, true);
            if (chart == null)
            {
                Console.WriteLine("No chart found in the document.");
                return;
            }

            // 3️⃣ Access the data label of the first series
            ChartDataLabel label = chart.Series[0].DataLabel;

            // 4️⃣ Customize the label appearance
            label.Position = DataLabelPosition.Center;   // change chart label position
            label.Separator = "; ";                      // customize chart data label
            label.ShowValue = true;                      // show chart label value
            label.ShowCategoryName = false;              // hide chart category name

            // 5️⃣ Save the modified document
            doc.Save(@"YOUR_DIRECTORY\CustomLabelChart.docx");

            Console.WriteLine("Chart label customization complete.");
        }
    }
}
```

### Expected result

`CustomLabelChart.docx` को Microsoft Word में खोलें। आपको चार्ट की पहली सीरीज़ का लेबल प्रत्येक डेटा पॉइंट पर केंद्रित दिखेगा, केवल संख्यात्मक वैल्यू प्रदर्शित करेगा, और “; ” को सेपरेटर के रूप में उपयोग करेगा। श्रेणी नाम अब वैल्यू के बगल में नहीं दिखेंगे।

## Common questions and edge cases

| प्रश्न | उत्तर |
|----------|--------|
| **यदि दस्तावेज़ में कोई चार्ट नहीं है तो क्या होगा?** | उदाहरण `null` चार्ट की जाँच करता है और कंसोल संदेश के साथ सुगमता से बाहर निकलता है। |
| **क्या मैं कई श्रृंखलाओं के लिए लेबल संपादित कर सकता हूँ?** | हाँ। `chart.Series` पर लूप करें और प्रत्येक `Series[i].DataLabel` पर समान `DataLabel` सेटिंग्स लागू करें। |
| **लेबल की फ़ॉन्ट शैली कैसे बदलूँ?** | `label.Font` का उपयोग करें (उदा., `label.Font.Size = 10; label.Font.Color = Color.Blue;`)। |
| **क्या `DataLabelPosition.Center` सभी चार्ट प्रकारों के लिए समर्थित है?** | अधिकांश 2‑D चार्ट प्रकार इसे सपोर्ट करते हैं। 3‑D चार्ट में कुछ स्थितियों को Word द्वारा अनदेखा किया जा सकता है। |
| **क्या मुझे Aspose.Words के लिए लाइसेंस चाहिए?** | इवैल्यूएशन मोड काम करता है लेकिन वॉटरमार्क जोड़ता है। लाइसेंस वॉटरमार्क हटाता है और पूरी कार्यक्षमता अनलॉक करता है। |

## Pro tips

* **Batch processing:** लोडिंग और सेविंग लॉजिक को एक मेथड में रैप करें जो इनपुट और आउटपुट पाथ स्वीकार करता है। इससे लूप में दर्जनों दस्तावेज़ प्रोसेस करना आसान हो जाता है।  
* **Performance:** एक ही फ़ाइल में कई चार्ट संशोधित करते समय एकल `Document` इंस्टेंस को पुन: उपयोग करें ताकि बार‑बार I/O से बचा जा सके।  
* **Testing:** यदि आपको CI पाइपलाइन में आउटपुट की पुष्टि करनी है, तो विज़ुअल डिफ़ (जैसे हेडलेस Word व्यूअर) को ऑटोमेट करके लेबल परिवर्तन की जाँच करें।  

## Next steps

अब जब आप **edit chart label tutorial** की बुनियादी बातें समझ गए हैं, तो निम्नलिखित विषयों पर विचार करें:

* **Change chart label position** अन्य सीरीज़ या विभिन्न चार्ट प्रकारों के लिए  
* **Customize chart data label** फ़ॉर्मेटिंग जैसे नंबर फ़ॉर्मेट, फ़ॉन्ट रंग, या बैकग्राउंड फ़िल्स  
* **Hide chart category name** जबकि मल्टी‑सीरीज़ चार्ट में सीरीज़ नाम दिखाया जाए  
* **Show chart label value** पाई चार्ट के लिए प्रतिशत मानों के साथ  

ये विषय Word चार्ट की सौंदर्यशास्त्र पर आपका नियंत्रण गहरा करेंगे और उन्नत रिपोर्टिंग परिदृश्यों के लिए तैयार करेंगे।

---

*हैप्पी कोडिंग! यदि आपको यह ट्यूटोरियल उपयोगी लगा, तो इसे टीम के साथ शेयर करें या GitHub पर सुधार योगदान दें।*


## What Should You Learn Next?

नीचे दिए गए ट्यूटोरियल्स निकट-संबंधित विषयों को कवर करते हैं जो इस गाइड में प्रदर्शित तकनीकों पर आधारित हैं। प्रत्येक संसाधन में पूर्ण कार्यशील कोड उदाहरण और चरण‑दर‑चरण व्याख्याएँ शामिल हैं, जिससे आप अतिरिक्त API फीचर्स में महारत हासिल कर सकें और अपने प्रोजेक्ट्स में वैकल्पिक इम्प्लीमेंटेशन एप्रोच का अन्वेषण कर सकें।

- [Customize Chart Data Label](/words/english/net/programming-with-charts/chart-data-label/)
- [Chart Data Label](/words/german/net/programming-with-charts/chart-data-label/)
- [Chart Data Label](/words/french/net/programming-with-charts/chart-data-label/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}