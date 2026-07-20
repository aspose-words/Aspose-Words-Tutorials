---
category: general
date: 2026-07-20
description: Aspose.Words for .NET के साथ पाई चार्ट लेबल जोड़ें। पाई चार्ट लेबल बदलना,
  प्रतिशत लेबल दिखाना, और चार्ट सीरीज़ लेबल को जल्दी अपडेट करना सीखें।
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- add pie chart labels
- change pie chart labels
- update chart series labels
- show percentage labels
- display pie chart percentages
language: hi
lastmod: 2026-07-20
og_description: Aspose.Words के साथ C# में पाई चार्ट लेबल जोड़ें। कुछ ही चरणों में
  पाई चार्ट लेबल बदलना, प्रतिशत लेबल दिखाना और चार्ट सीरीज़ लेबल अपडेट करना सीखें।
og_image_alt: Word document screenshot displaying a pie chart with custom percentage
  labels
og_title: C# में पाई चार्ट लेबल जोड़ें – Aspose.Words पूर्ण ट्यूटोरियल
schemas:
- author: Aspose
  dateModified: '2026-07-20'
  description: Add pie chart labels with Aspose.Words for .NET. Learn how to change
    pie chart labels, show percentage labels, and update chart series labels quickly.
  headline: Add pie chart labels in C# using Aspose.Words – Complete Guide
  type: TechArticle
tags:
- Aspose.Words
- C#
- Chart Manipulation
title: Aspose.Words का उपयोग करके C# में पाई चार्ट लेबल जोड़ें – पूर्ण गाइड
url: /hi/net/programming-with-charts/add-pie-chart-labels-in-c-using-aspose-words-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C# में Aspose.Words का उपयोग करके पाई चार्ट लेबल जोड़ें – पूर्ण गाइड

क्या आपको **पाई चार्ट लेबल** को Word दस्तावेज़ में C# के माध्यम से जोड़ना है? Aspose.Words के साथ आप आसानी से **पाई चार्ट लेबल** बदल सकते हैं और **पाई चार्ट प्रतिशत** को फ़ाइल के अंदर ही प्रदर्शित कर सकते हैं—Word में मैन्युअल ट्यूनिंग की ज़रूरत नहीं।  

इस ट्यूटोरियल में हम **प्रतिशत लेबल** दिखाने, उन्हें पुनः स्थित करने, और डायनामिक डेटा के लिए **चार्ट सीरीज़ लेबल** को अपडेट करने के सटीक चरणों को देखेंगे। अंत तक आपके पास एक पुन: उपयोग योग्य स्निपेट होगा जिसे आप किसी भी .NET प्रोजेक्ट में डाल सकते हैं।

> **त्वरित पूर्वावलोकन:** गाइड को पूरा करने के बाद, सहेजे गए `.docx` को खोलने पर आपको एक पाई चार्ट दिखेगा जहाँ प्रत्येक स्लाइस को उसके प्रतिशत के साथ लेबल किया गया है, और लेबल स्लाइस के बाहर स्थित है जिससे पढ़ने में अधिक सुविधा मिलती है।

---

## आपको क्या चाहिए

- **Aspose.Words for .NET** (2026 तक का नवीनतम संस्करण)। इसे NuGet से प्राप्त करें: `Install-Package Aspose.Words`।
- एक **Word दस्तावेज़** जिसमें पहले से ही पाई या डोनट चार्ट मौजूद हो (हम इसे `Chart.docx` कहेंगे)।
- **C#** और Visual Studio (या आपका पसंदीदा IDE) की बुनियादी जानकारी।

बस इतना ही—कोई अतिरिक्त लाइब्रेरी नहीं, कोई COM इंटरऑप नहीं, सिर्फ शुद्ध मैनेज्ड कोड।

---

## पाई चार्ट लेबल जोड़ें – पूर्ण कार्यान्वयन

नीचे एक **पूरा, चलाने योग्य** C# कंसोल प्रोग्राम है जो दस्तावेज़ को लोड करता है, पहले पाई चार्ट को संशोधित करता है, और परिणाम सहेजता है। हर लाइन पर टिप्पणी है ताकि आप समझ सकें **क्यों** हम यह कर रहे हैं, न कि सिर्फ **क्या** कर रहे हैं।

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

namespace PieChartLabelDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Load the Word document that already contains a pie chart.
            //    Change the path to where your Chart.docx lives.
            Document doc = new Document(@"YOUR_DIRECTORY\Chart.docx");

            // 2️⃣ Retrieve the first chart node in the document.
            //    The GetChild method walks the document tree and returns the first Node of type Chart.
            Chart chart = (Chart)doc.GetChild(NodeType.Chart, 0, true);
            if (chart == null)
            {
                Console.WriteLine("No chart found in the document.");
                return;
            }

            // 3️⃣ Access the data label collection of the first series.
            //    In a pie chart each series represents the whole pie; the collection holds the labels for each slice.
            ChartDataLabelCollection dataLabels = chart.Series[0].DataLabelCollection;

            // 4️⃣ Position the data labels **outside** the slices.
            //    This is the most readable layout for pie/doughnut charts.
            dataLabels.Position = ChartDataLabelPosition.OutsideEnd;

            // 5️⃣ Turn on the percentage display.
            //    ShowPercentage automatically calculates and shows each slice’s contribution.
            dataLabels.ShowPercentage = true;

            // 6️⃣ (Optional) If you also want the actual values, enable ShowValue.
            //    dataLabels.ShowValue = true; // uncomment to display raw numbers.

            // 7️⃣ Save the modified document.
            //    The new file will contain the pie chart with custom labels.
            doc.Save(@"YOUR_DIRECTORY\ChartWithCustomLabels.docx");

            Console.WriteLine("Pie chart labels added successfully!");
        }
    }
}
```

### अपेक्षित परिणाम

`ChartWithCustomLabels.docx` को Microsoft Word में खोलें। आपको पाई चार्ट **प्रत्येक स्लाइस के बाहर स्थित प्रतिशत लेबल** के साथ दिखेगा। लेबल कुछ इस तरह दिखेंगे “35 %”, “20 %” आदि, जिससे चार्ट तुरंत समझ में आ जाता है।

---

## पाई चार्ट लेबल बदलें: स्थिति और स्वरूपण

यदि आपको केवल **पाई चार्ट लेबल** बदलने की आवश्यकता है और प्रतिशत नहीं दिखाना है, तो आप `Position` प्रॉपर्टी को नीचे दिए गए विकल्पों में से किसी एक पर सेट कर सकते हैं:

| पोजीशन एन्‍युम | दृश्य प्रभाव |
|---------------|---------------|
| `InsideEnd`   | लेबल स्लाइस के अंदर, किनारे पर स्थित होते हैं। |
| `Center`      | लेबल स्लाइस के मध्य में दिखाई देते हैं (छोटे पाई के लिए उपयुक्त)। |
| `OutsideEnd`  | लेबल स्लाइस के बाहर होते हैं, लीडर लाइन से जुड़े होते हैं (हमारा डिफ़ॉल्ट)। |

```csharp
dataLabels.Position = ChartDataLabelPosition.Center; // example switch
```

**प्रो टिप:** `OutsideEnd` तब सबसे अच्छा काम करता है जब चार्ट में कई स्लाइस हों; यह ओवरलैपिंग टेक्स्ट को रोकता है।

---

## पाई चार्ट पर प्रतिशत लेबल दिखाएँ

`ShowPercentage` प्रॉपर्टी एक **बूलियन फ़्लैग** है। इसे `true` सेट करने से Aspose.Words प्रत्येक स्लाइस के डेटा स्रोत के आधार पर उसका योगदान गणना करता है।

```csharp
dataLabels.ShowPercentage = true; // Turns on the % display
```

यदि आपको दोनों, कच्चे नंबर **और** प्रतिशत चाहिए, तो आप इसे `ShowValue` के साथ भी जोड़ सकते हैं:

```csharp
dataLabels.ShowValue = true; // Shows the actual cell value next to the %
```

जब दोनों फ़्लैग सक्षम होते हैं, तो लेबल कुछ इस तरह दिखता है “45 % (120)”.

---

## डायनामिक डेटा के लिए चार्ट सीरीज़ लेबल अपडेट करें

अक्सर आप चार्ट को रन‑टाइम पर जेनरेट करते हैं—जैसे मासिक बिक्री या सर्वे परिणाम। प्रोग्रामेटिक रूप से **चार्ट सीरीज़ लेबल** अपडेट करने के लिए, डेटा लेबल्स को बदलने से पहले `Series` कलेक्शन को संशोधित करें:

```csharp
// Assume you have a second series you want to rename
chart.Series[1].Name = "Projected Growth";

// Refresh the data label collection after changes
ChartDataLabelCollection secondSeriesLabels = chart.Series[1].DataLabelCollection;
secondSeriesLabels.ShowPercentage = true;
secondSeriesLabels.Position = ChartDataLabelPosition.OutsideEnd;
```

यह स्निपेट दिखाता है कि कैसे **किसी भी सीरीज़ के लिए** चार्ट सीरीज़ लेबल अपडेट किए जा सकते हैं, न कि केवल पहली के लिए। यह उन रिपोर्टों में उपयोगी है जहाँ आप वास्तविक बनाम अनुमानित डेटा को मिलाते हैं।

---

## एज केस और सामान्य समस्याएँ

| स्थिति | ध्यान रखने योग्य बातें | समाधान |
|-----------|-------------------|-----|
| **चार्ट पाई/डोनट नहीं है** | `Position` का कोई दृश्य प्रभाव नहीं हो सकता। | सुनिश्चित करें `chart.Type` `ChartType.Pie` या `ChartType.Doughnut` है। |
| **कोई चार्ट नहीं मिला** | `GetChild` `null` लौटाता है। | एक गार्ड क्लॉज़ जोड़ें (कोड देखें) और उपयोगी संदेश लॉग करें। |
| **पुराना Word संस्करण** | कुछ लेबल सुविधाएँ अनदेखी रह जाती हैं। | पूर्ण समर्थन के लिए `.docx` (आधुनिक फ़ॉर्मेट) के रूप में सहेजें। |
| **स्लाइस की बड़ी संख्या** | `OutsideEnd` के साथ भी लेबल ओवरलैप हो सकते हैं। | स्लाइस संख्या कम करें या चार्ट का आकार बढ़ाएँ। |

---

## पूर्ण कार्यशील उदाहरण (कॉपी‑पेस्ट)

नीचे वह **पूरा प्रोग्राम** है जिसे आप नई कंसोल प्रोजेक्ट में कॉपी कर सकते हैं। केवल `YOUR_DIRECTORY` को उस फ़ोल्डर से बदलें जहाँ `Chart.docx` स्थित है।



## आगे क्या सीखें?

निम्नलिखित ट्यूटोरियल्स उन विषयों को कवर करते हैं जो इस गाइड में दिखाए गए तकनीकों पर आधारित हैं। प्रत्येक संसाधन में पूर्ण कार्यशील कोड उदाहरण और चरण‑दर‑चरण व्याख्याएँ शामिल हैं, जिससे आप अतिरिक्त API सुविधाओं में महारत हासिल कर सकें और अपने प्रोजेक्ट्स में वैकल्पिक कार्यान्वयन तरीकों का अन्वेषण कर सकें।

- [Set Default Options For Data Labels In A Chart](/words/english/net/programming-with-charts/default-options-for-data-labels/)
- [Customize Single Chart Series In A Chart](/words/english/net/programming-with-charts/single-chart-series/)
- [Insert Column Chart in Word Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-column-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}