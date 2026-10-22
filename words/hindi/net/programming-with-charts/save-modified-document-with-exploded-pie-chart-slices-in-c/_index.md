---
category: general
date: 2026-10-13
description: 'पाई चार्ट को कस्टमाइज़ करने के बाद संशोधित दस्तावेज़ को सहेजें: स्लाइस
  को एक्सप्लोड करें, पहले स्लाइस का कोण बदलें, और C# में प्रतिशत लेबल दिखाएँ।'
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- save modified document
- show percentage labels
- explode pie chart slices
- display percentages pie
- change first slice
language: hi
lastmod: 2026-10-13
og_description: C# में पाई चार्ट को कस्टमाइज़ करने के बाद संशोधित दस्तावेज़ को सहेजें।
  पाई चार्ट के स्लाइस को एक्सप्लोड करना, पहले स्लाइस का कोण बदलना, और प्रतिशत लेबल
  दिखाना सीखें।
og_image_alt: Screenshot of a Word document where the pie chart slices are exploded
  and percentage labels are displayed after saving the modified document
og_title: विस्फोटित पाई चार्ट स्लाइस के साथ संशोधित दस्तावेज़ सहेजें – C# गाइड
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: 'Save modified document after customizing a pie chart: explode slices,
    change first slice angle, and show percentage labels in C#.'
  headline: Save modified document with exploded pie chart slices in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word chart
- pie chart
- document manipulation
title: C# में विस्फोटित पाई चार्ट स्लाइस के साथ संशोधित दस्तावेज़ को सहेजें
url: /hi/net/programming-with-charts/save-modified-document-with-exploded-pie-chart-slices-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C# में विस्फोटित पाई चार्ट स्लाइस के साथ संशोधित दस्तावेज़ सहेजें

यदि आपको Word पाई चार्ट को समायोजित करने के बाद **save modified document** करने की आवश्यकता है, तो यह गाइड आपको बिल्कुल बताता है कि कैसे करना है। आप पाई चार्ट स्लाइस को विस्फोटित करना, पहले स्लाइस का कोण बदलना, और प्रतिशत लेबल दिखाना सीखेंगे—सभी कुछ C# कोड की लाइनों से।

चार्ट को अनुकूलित करना रिपोर्ट, इनवॉइस, या डैशबोर्ड को प्रोग्रामेटिक रूप से जनरेट करते समय एक सामान्य आवश्यकता है। इस ट्यूटोरियल के अंत तक आप DOCX फ़ाइल लोड कर सकेंगे, चार्ट की उपस्थिति को संशोधित कर सकेंगे, और **save modified document** को वितरण के लिए तैयार कर सकेंगे।

## आवश्यकताएँ

- .NET 6.0 या बाद का (कोड .NET Framework 4.6+ के साथ भी काम करता है)
- Aspose.Words for .NET 23.10 या नया (फ्री ट्रायल या लाइसेंस्ड कॉपी)
- एक Word फ़ाइल (`input.docx`) जिसमें एकल पाई चार्ट हो
- Visual Studio 2022 या कोई भी C# IDE

> **Tip:** Aspose.Words NuGet पैकेज `dotnet add package Aspose.Words` के साथ जोड़ा जाता है।

## चरण 1: चार्ट वाली Word दस्तावेज़ को लोड करें

पहला कदम स्रोत DOCX फ़ाइल को खोलना है। `Document` क्लास मेमोरी में पूरे Word फ़ाइल का प्रतिनिधित्व करती है।

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // Load the Word document that contains the chart
        Document doc = new Document(@"YOUR_DIRECTORY\input.docx");
```

दस्तावेज़ को लोड करने से आपको प्रत्येक नोड तक पूरी पहुँच मिलती है, जिसमें चार्ट रखने वाले शैप्स भी शामिल हैं।

## चरण 2: दस्तावेज़ से पहला चार्ट शैप प्राप्त करें

चार्ट `Shape` नोड्स के अंदर संग्रहीत होते हैं। आप `GetChild` के साथ पहला चार्ट ढूँढ़ सकते हैं।

```csharp
        // Retrieve the first chart shape from the document
        Chart chart = (Chart)doc.GetChild(NodeType.Shape, 0, true);
```

यदि दस्तावेज़ में कई चार्ट हैं, तो इंडेक्स (`0`) को समायोजित करें या संग्रह के माध्यम से इटररेट करें। यह लाइन सुनिश्चित करती है कि आपके पास वह `Chart` ऑब्जेक्ट रेफ़रेंस है जिसे आप संशोधित करेंगे।

## चरण 3: पाई चार्ट स्लाइस को विस्फोटित करें

एक स्लाइस को विस्फोटित करने से वह पाई के बाकी हिस्सों से अलग हो जाता है, जिससे चार्ट पढ़ना आसान हो जाता है। `Explode` प्रॉपर्टी पूरे सीरीज़ पर काम करती है।

```csharp
        // Enable slice explosion so each slice is separated from the pie
        chart.PieChart.Explode = true;
```

`Explode` को `true` सेट करने से पूरे सीरीज़ के लिए **explodes pie chart slices** हो जाता है, जो तब उपयोगी होता है जब आप चाहते हैं कि प्रत्येक स्लाइस अलग दिखे।

## चरण 4: पहले स्लाइस का कोण बदलें

कभी-कभी आपको पहला स्लाइस एक कस्टम कोण से शुरू करना पड़ता है, उदाहरण के लिए डिज़ाइन गाइडलाइन के साथ संरेखित करने के लिए।

```csharp
        // Set a custom start angle for the first slice (30 degrees)
        chart.PieChart.FirstSliceAngle = 30;
```

`FirstSliceAngle` प्रॉपर्टी **changes first slice** की दिशा बदलती है, जिससे पूरी पाई घुम जाती है और पहला स्लाइस 30 डिग्री पर शुरू होता है।

## चरण 5: पाई स्लाइस पर प्रतिशत लेबल दिखाएँ

प्रत्येक स्लाइस के संख्यात्मक योगदान को दिखाना अक्सर रिपोर्ट में आवश्यक होता है। `DataLabel.ShowPercentage` फ़्लैग प्रतिशत मानों को सक्रिय करता है।

```csharp
        // Display percentage values on the data labels of the pie slices
        chart.PieChart.DataLabel.ShowPercentage = true;
```

यह चरण **show percentage labels** को सीधे चार्ट पर दिखाता है, जो **display percentages pie** आवश्यकता को भी पूरा करता है।

## चरण 6: संशोधित दस्तावेज़ सहेजें

सभी कस्टमाइज़ेशन लागू होने के बाद, बदलावों को नई फ़ाइल में सहेजें। `Save` मेथड अपडेटेड DOCX को डिस्क पर लिखता है।

```csharp
        // Save the modified document
        doc.Save(@"YOUR_DIRECTORY\output.docx");
    }
}
```

अब आपके पास एक **save modified document** है जिसमें विस्फोटित पाई चार्ट, घुमाया हुआ पहला स्लाइस, और दृश्यमान प्रतिशत लेबल हैं।

![Save modified document showing exploded pie chart](/images/pie-chart-exploded.png "Save modified document with exploded pie chart slices and percentage labels")

*स्क्रीनशॉट दर्शाता है कि दस्तावेज़ सहेजने के बाद अंतिम आउटपुट कैसा दिखता है।*

## पूर्ण, चलाने योग्य उदाहरण

सभी भागों को मिलाकर, यहाँ पूरा प्रोग्राम है जिसे आप कॉपी‑पेस्ट करके एक कंसोल प्रोजेक्ट में उपयोग कर सकते हैं:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

namespace PieChartCustomizer
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Load the source DOCX
            Document doc = new Document(@"YOUR_DIRECTORY\input.docx");

            // 2️⃣ Get the first chart shape
            Chart chart = (Chart)doc.GetChild(NodeType.Shape, 0, true);
            if (chart == null)
            {
                Console.WriteLine("No chart found in the document.");
                return;
            }

            // 3️⃣ Explode all slices
            chart.PieChart.Explode = true;

            // 4️⃣ Rotate the first slice to 30°
            chart.PieChart.FirstSliceAngle = 30;

            // 5️⃣ Show percentages on each slice
            chart.PieChart.DataLabel.ShowPercentage = true;

            // 6️⃣ Persist the changes
            string outPath = @"YOUR_DIRECTORY\output.docx";
            doc.Save(outPath);
            Console.WriteLine($"Document saved to {outPath}");
        }
    }
}
```

### अपेक्षित परिणाम

`output.docx` खोलने पर एक पाई चार्ट दिखेगा जहाँ:

- प्रत्येक स्लाइस थोड़ा अलग हो जाता है (**exploded pie chart slices**)
- पहला स्लाइस 30‑डिग्री ऑफ़सेट पर शुरू होता है (**change first slice**)
- प्रत्येक स्लाइस अपना योगदान प्रतिशत के रूप में दिखाता है (**show percentage labels**, **display percentages pie**)
- फ़ाइल को मूल को बदले बिना **save modified document** किया गया है।

## सामान्य प्रश्न और किनारे के मामलों

| प्रश्न | उत्तर |
|----------|--------|
| **यदि दस्तावेज़ में कोई चार्ट नहीं है तो क्या होगा?** | कोड `GetChild` के बाद `null` की जाँच करता है। यदि कोई चार्ट नहीं है, तो आप प्रोग्रामेटिक रूप से एक जोड़ सकते हैं या स्पष्ट संदेश के साथ प्रक्रिया रोक सकते हैं। |
| **क्या मैं केवल एक ही स्लाइस को विस्फोटित कर सकता हूँ?** | हाँ। `chart.PieChart.Series[0].DataPoints[i].Explosion = true;` का उपयोग करें जहाँ `i` स्लाइस का इंडेक्स है। |
| **मैं लेबल फ़ॉर्मेट कैसे बदलूँ (जैसे, मान + % दिखाएँ)?** | `chart.PieChart.DataLabel.ShowValue = true;` सेट करें और वैकल्पिक रूप से `chart.PieChart.DataLabel.ShowPercentage = true;` सेट करके दोनों को मिलाएँ। |
| **क्या सहेजने के बाद चार्ट शैली बनी रहती है?** | Aspose.Words सभी स्टाइलिंग, जिसमें रंग और फ़ॉन्ट शामिल हैं, को **save modified document** करने पर बरकरार रखता है। |
| **क्या मैं एक ही फ़ाइल में कई चार्ट प्रोसेस कर सकता हूँ?** | `NodeType.Shape` के साथ सभी `Shape` नोड्स को लूप करें और `shape.HasChart` द्वारा फ़िल्टर करें। प्रत्येक चार्ट पर वही कदम लागू करें। |

## निष्कर्ष

अब आप जानते हैं कि Word में प्रोग्रामेटिक रूप से पाई चार्ट को कस्टमाइज़ करने के बाद **save modified document** कैसे करें। गाइड ने पाई चार्ट स्लाइस को विस्फोटित करना, पहले स्लाइस का कोण बदलना, और प्रतिशत लेबल दिखाना शामिल किया—जो **show percentage labels**, **explode pie chart slices**, **display percentages pie**, और **change first slice** आवश्यकताओं को पूरा करता है।

अगले, आप निम्नलिखित का अन्वेषण कर सकते हैं:

- डेटा सीरीज़ को डायनामिक रूप से जोड़ना (`chart.Series.Add(...)`)
- लेजेंड प्लेसमेंट और चार्ट शीर्षकों को कस्टमाइज़ करना
- चार्ट स्टाइलिंग को बरकरार रखते हुए DOCX को PDF में बदलना

विभिन्न कोणों, विस्फोट सेटिंग्स, या लेबल फ़ॉर्मेट के साथ प्रयोग करने में संकोच न करें ताकि आपकी रिपोर्टिंग आवश्यकताओं के अनुरूप हो। कोडिंग का आनंद लें!

## अगला आप क्या सीखें?

निम्नलिखित ट्यूटोरियल्स निकट संबंधित विषयों को कवर करते हैं जो इस गाइड में दिखाए गए तकनीकों पर आधारित हैं। प्रत्येक संसाधन में पूर्ण कार्यशील कोड उदाहरण और चरण‑दर‑चरण व्याख्याएँ शामिल हैं जो आपको अतिरिक्त API फीचर्स में महारत हासिल करने और अपने प्रोजेक्ट्स में वैकल्पिक कार्यान्वयन दृष्टिकोणों का अन्वेषण करने में मदद करती हैं।

- [C# में Aspose.Words के साथ संपादित दस्तावेज़ कैसे सहेजें – चरण‑दर‑चरण गाइड](/words/english/net/programming-with-docsaveoptions/how-to-save-edited-document-in-c-with-aspose-words-step-by-s/)
- [Aspose.Words for .NET का उपयोग करके Word दस्तावेज़ में चार्ट सीरीज़ डेटा अपडेट करें](/words/english/net/programming-with-charts/modify-chart-series/)
- [Word दस्तावेज़ में कॉलम चार्ट डालें](/words/english/net/programming-with-charts/insert-column-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}