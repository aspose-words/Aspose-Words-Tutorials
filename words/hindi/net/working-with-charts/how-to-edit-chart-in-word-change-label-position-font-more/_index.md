---
category: general
date: 2026-07-29
description: Word दस्तावेज़ में चार्ट को कैसे संपादित करें—चार्ट लेबल की स्थिति बदलना,
  बार चार्ट लेबल को समायोजित करना, चार्ट डेटा लेबल को संशोधित करना, और चार्ट लेबल
  फ़ॉन्ट बदलना सीखें।
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to edit chart
- change chart label position
- adjust bar chart labels
- modify chart data labels
- change chart label font
language: hi
lastmod: 2026-07-29
og_description: Word में चार्ट को जल्दी कैसे संपादित करें। चार्ट लेबल की स्थिति बदलना,
  बार चार्ट लेबल को समायोजित करना, चार्ट डेटा लेबल को संशोधित करना, और चार्ट लेबल
  फ़ॉन्ट बदलना में निपुण बनें।
og_image_alt: Screenshot of a Word bar chart with custom label positions and larger
  font size
og_title: वर्ड में चार्ट को कैसे संपादित करें – लेबल और फ़ॉन्ट बदलें
schemas:
- author: Aspose
  dateModified: '2026-07-29'
  description: How to edit chart in a Word document—learn to change chart label position,
    adjust bar chart labels, modify chart data labels, and change chart label font.
  headline: 'How to Edit Chart in Word: Change Label Position, Font & More'
  type: TechArticle
- description: How to edit chart in a Word document—learn to change chart label position,
    adjust bar chart labels, modify chart data labels, and change chart label font.
  name: 'How to Edit Chart in Word: Change Label Position, Font & More'
  steps:
  - name: What if the document contains multiple charts?
    text: 'The code above grabs the *first* chart (`GetChild(NodeType.Shape, 0, true)`).
      To edit all charts, replace the single retrieval with a loop:'
  - name: How to **change chart label font** for a specific series only?
    text: 'Each `ChartSeries` has its own `DataLabelCollection`. Target a series by
      index:'
  - name: Does this work with pie or line charts?
    text: Yes—`ChartDataLabelPosition` supports values like `InsideEnd`, `OutsideEnd`,
      and `BestFit`. For a pie chart you might prefer `OutsideEnd` to keep labels
      readable.
  - name: What about localization (e.g., different decimal separators)?
    text: Aspose.Words respects the document’s locale settings. If you need to enforce
      a specific format, adjust `label.NumberFormat` before saving.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word Automation
title: 'वर्ड में चार्ट को कैसे संपादित करें: लेबल की स्थिति, फ़ॉन्ट और अधिक बदलें'
url: /hi/net/working-with-charts/how-to-edit-chart-in-word-change-label-position-font-more/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word में चार्ट को कैसे संपादित करें: लेबल की स्थिति, फ़ॉन्ट और अधिक बदलें

Word दस्तावेज़ में चार्ट को संपादित करना एक सामान्य आवश्यकता है जब आप चाहते हैं कि आपकी रिपोर्ट्स पेशेवर दिखें। क्या आपने कभी **चार्ट लेबल की स्थिति बदलने** या लेबल्स को पढ़ने योग्य बनाने के लिए अनगिनत मेन्यूज़ में खो जाने से जूझा है? आप अकेले नहीं हैं—बहुत से डेवलपर्स रिपोर्ट जेनरेशन को ऑटोमेट करते समय इस समस्या का सामना करते हैं। इस गाइड में हम एक पूर्ण, रन करने योग्य उदाहरण के माध्यम से दिखाएंगे कि कैसे **बार चार्ट लेबल्स को समायोजित करें**, **चार्ट डेटा लेबल्स को संशोधित करें**, और **C# और Aspose.Words लाइब्रेरी** का उपयोग करके **चार्ट लेबल फ़ॉन्ट बदलें**।

## आप क्या सीखेंगे

- एक .docx फ़ाइल लोड करना जिसमें पहले से एक बार चार्ट मौजूद है।  
- पहले चार्ट शेप को प्राप्त करना और उसके डेटा‑लेबल कलेक्शन तक पहुंचना।  
- **चार्ट लेबल की स्थिति बदलना** ताकि बार्स साफ़ दिखें।  
- बेहतर पठनीयता के लिए **बार चार्ट लेबल्स** का फ़ॉन्ट आकार समायोजित करना।  
- संशोधित दस्तावेज़ को डिस्क पर सहेजना।  

कोई बाहरी टूल नहीं, कोई मैन्युअल UI कदम नहीं—सिर्फ वह कोड जिसे आप किसी भी .NET प्रोजेक्ट में डाल सकते हैं। अंत तक आपके पास एक स्व-निहित समाधान होगा जिसे आप दर्जनों दस्तावेज़ों में पुन: उपयोग कर सकते हैं।

> **Prerequisites**  
> - .NET 6.0 या बाद का संस्करण (कोड .NET Framework 4.7+ पर भी काम करता है)।  
> - Aspose.Words for .NET (NuGet के माध्यम से उपलब्ध)।  
> - एक Word फ़ाइल (`BarChart.docx`) जिसमें पहले से एक बार चार्ट मौजूद है।  

यदि आपके पास इनमें से कोई भी नहीं है, तो अभी नवीनतम Aspose.Words पैकेज प्राप्त करें:

```bash
dotnet add package Aspose.Words
```

---

## चार्ट को संपादित करने का तरीका: Word दस्तावेज़ से चार्ट प्राप्त करें

**how to edit chart** ऑब्जेक्ट्स का पहला कदम दस्तावेज़ को लोड करना और चार्ट शेप को ढूँढ़ना है। Aspose.Words चार्ट्स को `Shape` नोड्स के रूप में मानता है, इसलिए हम `GetChild` को `NodeType.Shape` के साथ उपयोग करके पहला चार्ट प्राप्त कर सकते हैं।

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

// Load the Word document that contains a chart
Document document = new Document(@"C:\Temp\BarChart.docx");

// Retrieve the first chart shape from the document
Chart chart = (Chart)document.GetChild(NodeType.Shape, 0, true);
```

> **Why this matters:**  
> `Chart` ऑब्जेक्ट तक सीधे पहुंचकर आप Word में फ़ाइल खोलने और प्रत्येक लेबल को मैन्युअल रूप से समायोजित करने की ओवरहेड से बचते हैं। यह किसी भी **modify chart data labels** ऑटोमेशन का मूल आधार है।

## बार चार्ट लेबल्स समायोजित करें: चार्ट लेबल की स्थिति बदलें

अब जब हमारे पास `Chart` इंस्टेंस है, चलिए उसके `DataLabelCollection` पर इटररेट करते हैं। लक्ष्य है **चार्ट लेबल की स्थिति बदलना** ताकि प्रत्येक लेबल अपने बार के बेस के अंदर सुगमता से बैठे, बजाय इसके कि वह ऊपर लटकता रहे।

```csharp
// Loop through each data label in the chart
foreach (ChartDataLabel dataLabel in chart.DataLabelCollection)
{
    // Place label inside the base of the bar
    dataLabel.Position = ChartDataLabelPosition.InsideBase;
}
```

> **Pro tip:**  
> `InsideBase` वर्टिकल बार चार्ट्स के लिए अच्छा काम करता है। यदि आप हॉरिज़ॉन्टल बार चार्ट के साथ काम कर रहे हैं, तो `InsideEnd` आज़माएँ। पोजीशन के साथ प्रयोग करना सस्ता है—सिर्फ कोड को फिर से चलाएँ और सहेजे गए दस्तावेज़ को खोलें।

## चार्ट लेबल फ़ॉन्ट बदलें: पठनीयता के लिए फ़ॉन्ट आकार समायोजित करें

छोटा फ़ॉन्ट रिपोर्ट की स्पष्टता का मौन हत्यारा है। **चार्ट लेबल फ़ॉन्ट बदलने** के लिए, प्रत्येक `ChartDataLabel` पर `Font.Size` प्रॉपर्टी सेट करें। हम इसे 9 pt पर ले जाएंगे, जो अधिकांश प्रिंटेड रिपोर्ट्स के लिए एक आदर्श आकार है।

```csharp
foreach (ChartDataLabel dataLabel in chart.DataLabelCollection)
{
    // Set a readable font size (9 points)
    dataLabel.Font.Size = 9;
}
```

> **Why we do this:**  
> फ़ॉन्ट आकार समायोजित करना **modify chart data labels** की सर्वश्रेष्ठ प्रैक्टिस का हिस्सा है। बड़े फ़ॉन्ट एक्सेसिबिलिटी बढ़ाते हैं और मैन्युअल पोस्ट‑प्रोसेसिंग की आवश्यकता को कम करते हैं।

## अपडेटेड दस्तावेज़ सहेजें

पोजीशन और फ़ॉन्ट को ट्यून करने के बाद, **how to edit chart** का अंतिम कदम बदलावों को स्थायी बनाना है। Aspose.Words इसे एक लाइन में कर देता है।

```csharp
// Save the modified document with new label settings
document.Save(@"C:\Temp\BarChartCustomLabels.docx");
```

`BarChartCustomLabels.docx` को Word में खोलें और आप देखेंगे कि लेबल्स बार्स के अंदर कसकर फिट हैं, स्पष्ट 9 pt फ़ॉन्ट के साथ। अब छोटे नंबरों को पढ़ने के लिए आँखें नहीं मारनी पड़ेंगी।

---

## पूर्ण कार्यशील उदाहरण (सभी चरण एक फ़ाइल में)

नीचे एक पूर्ण, तैयार‑चलाने योग्य कंसोल प्रोग्राम है जो पूरी प्रक्रिया को दर्शाता है—दस्तावेज़ लोड करने से लेकर अपडेटेड संस्करण को सहेजने तक। इसे नई .NET कंसोल प्रोजेक्ट में कॉपी‑पेस्ट करें और **F5** दबाएँ।

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

namespace ChartLabelEditor
{
    class Program
    {
        static void Main(string[] args)
        {
            // Path to the source document (must contain a bar chart)
            string sourcePath = @"C:\Temp\BarChart.docx";

            // Path where the edited document will be saved
            string destPath = @"C:\Temp\BarChartCustomLabels.docx";

            // Load the Word document
            Document doc = new Document(sourcePath);

            // Retrieve the first chart shape
            Chart chart = (Chart)doc.GetChild(NodeType.Shape, 0, true);
            if (chart == null)
            {
                Console.WriteLine("No chart found in the document.");
                return;
            }

            // Iterate over each data label
            foreach (ChartDataLabel label in chart.DataLabelCollection)
            {
                // Change chart label position
                label.Position = ChartDataLabelPosition.InsideBase;

                // Change chart label font size
                label.Font.Size = 9;
            }

            // Save the updated document
            doc.Save(destPath);
            Console.WriteLine($"Chart labels updated and saved to: {destPath}");
        }
    }
}
```

**Expected output** जब आप प्रोग्राम चलाएँगे:

```
Chart labels updated and saved to: C:\Temp\BarChartCustomLabels.docx
```

परिणामी फ़ाइल खोलें और आप देखेंगे कि **adjust bar chart labels** बार्स के अंदर स्थित हैं, एक आरामदायक फ़ॉन्ट आकार के साथ।

---

## सामान्य प्रश्न और किनारे के मामले

### यदि दस्तावेज़ में कई चार्ट हों तो क्या करें?

ऊपर दिया गया कोड *पहला* चार्ट (`GetChild(NodeType.Shape, 0, true)`) लेता है। सभी चार्ट्स को संपादित करने के लिए, एकल रिट्रीवल को लूप से बदलें:

```csharp
NodeCollection shapes = doc.GetChildNodes(NodeType.Shape, true);
foreach (Shape shape in shapes)
{
    if (shape.HasChart)
    {
        Chart chart = shape.GetChart();
        // Apply label changes as shown earlier
    }
}
```

### केवल एक विशिष्ट सीरीज़ के लिए **चार्ट लेबल फ़ॉन्ट बदलें** कैसे करें?

प्रत्येक `ChartSeries` की अपनी `DataLabelCollection` होती है। इंडेक्स द्वारा एक सीरीज़ को टार्गेट करें:

```csharp
ChartSeries series = chart.Series[1]; // second series (zero‑based)
foreach (ChartDataLabel label in series.DataLabelCollection)
{
    label.Font.Size = 10; // larger for this series only
}
```

### क्या यह पाई या लाइन चार्ट्स के साथ काम करता है?

हां—`ChartDataLabelPosition` में `InsideEnd`, `OutsideEnd`, और `BestFit` जैसे मान शामिल हैं। पाई चार्ट के लिए आप `OutsideEnd` पसंद कर सकते हैं ताकि लेबल्स पढ़ने योग्य रहें।

### लोकलाइज़ेशन (जैसे विभिन्न दशमलव विभाजक) के बारे में क्या?

Aspose.Words दस्तावेज़ की लोकेल सेटिंग्स का सम्मान करता है। यदि आपको कोई विशिष्ट फॉर्मेट लागू करना है, तो सहेजने से पहले `label.NumberFormat` को समायोजित करें।

---

## सारांश और अगले कदम

हमने **how to edit chart** ऑब्जेक्ट्स को Word दस्तावेज़ में शुरू से अंत तक कवर किया: फ़ाइल लोड करना, चार्ट प्राप्त करना, **चार्ट लेबल की स्थिति बदलना**, **बार चार्ट लेबल्स समायोजित करना**, **चार्ट डेटा लेबल्स संशोधित करना**, और अंत में **चार्ट लेबल फ़ॉन्ट बदलना** और सहेजना। पूरा उदाहरण प्रोडक्शन‑रेडी है और किसी भी ऑटोमेशन पाइपलाइन में डाला जा सकता है।

अगले स्तर पर जाने के लिए विचार करें:

- **डेटा लेबल रंग जोड़ें** (`dataLabel.Font.Color = Color.Blue;`)।  
- **मानों को प्रतिशत में दिखाएँ** (`dataLabel.NumberFormat = "0%";`)।  
- **चार्ट्स को प्रोग्रामेटिकली बनाएं** बजाय मौजूदा चार्ट लोड करने के।  

इन सभी को हमने आज इस्तेमाल किए गए समान API सतह पर आधारित किया है, इसलिए आप सहज महसूस करेंगे।

यदि आपको कोई समस्या आती है, तो नीचे टिप्पणी छोड़ें या अधिक गहन चार्ट‑कस्टमाइज़ेशन विकल्पों के लिए Aspose.Words दस्तावेज़ देखें। Happy coding, और सुंदर लेबल वाले चार्ट्स का आनंद लें!

## आगे आप क्या सीखें?

निम्नलिखित ट्यूटोरियल्स उन विषयों को कवर करते हैं जो इस गाइड में दिखाए गए तकनीकों पर आधारित हैं। प्रत्येक संसाधन में पूर्ण कार्यशील कोड उदाहरण और चरण‑दर‑चरण व्याख्याएँ शामिल हैं, जिससे आप अतिरिक्त API फीचर्स में महारत हासिल कर सकें और अपने प्रोजेक्ट्स में वैकल्पिक इम्प्लीमेंटेशन अप्रोचेज़ को एक्सप्लोर कर सकें।

- [Customize Chart Data Label](/words/english/net/programming-with-charts/chart-data-label/)
- [Format Number Of Data Label In A Chart](/words/english/net/programming-with-charts/format-number-of-data-label/)
- [Chart Data Label](/words/german/net/programming-with-charts/chart-data-label/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}