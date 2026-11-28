---
category: general
date: 2026-10-10
description: पैराग्राफ को फ़्रेंच में अनुवाद करें और चार्ट डेटा लेबल को बदलना, चार्ट
  डेटा लेबल को अनुकूलित करना, तथा Aspose.Words AI का उपयोग करके संपादित docx फ़ाइल
  को सहेजना सीखें।
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- translate paragraph to french
- how to change chart data label
- how to translate word document with ai
- customize chart data label
- how to save edited docx file
language: hi
lastmod: 2026-10-10
og_description: पैराग्राफ को फ्रेंच में अनुवाद करें और चार्ट डेटा लेबल को बदलना, चार्ट
  डेटा लेबल को अनुकूलित करना, तथा Aspose.Words AI का उपयोग करके संपादित docx फ़ाइल
  को सहेजना सीखें।
og_image_alt: Screenshot of a Word document showing a French paragraph and a chart
  with a customized data label
og_title: पैराग्राफ को फ्रेंच में अनुवाद करें और वर्ड में चार्ट लेबल बदलें
schemas:
- author: Aspose
  dateModified: '2026-10-10'
  description: Translate paragraph to French and learn how to change chart data label,
    customize chart data label, and save edited docx file using Aspose.Words AI.
  headline: Translate paragraph to French and change chart label in Word
  type: TechArticle
tags:
- Aspose.Words
- C#
- AI translation
- chart customization
title: पैराग्राफ को फ्रेंच में अनुवाद करें और वर्ड में चार्ट लेबल बदलें
url: /hi/net/ai-powered-document-processing/translate-paragraph-to-french-and-change-chart-label-in-word/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# पैराग्राफ को फ्रेंच में अनुवाद करें और Word में चार्ट लेबल बदलें

यदि आपको **पैराग्राफ को फ्रेंच में अनुवाद** करना है और साथ ही उसी Word दस्तावेज़ में एक चार्ट को अपडेट करना है, तो यह गाइड आपको बिल्कुल बताता है कि कैसे करना है। Aspose.Words AI का उपयोग करके आप टेक्स्ट को स्वचालित रूप से अनुवाद कर सकते हैं, फिर चार्ट के डेटा लेबल को संशोधित कर सकते हैं और अंत में संपादित `.docx` फ़ाइल को सहेज सकते हैं—सभी कुछ सरल चरणों में।

यह ट्यूटोरियल स्रोत फ़ाइल को लोड करने से लेकर बदलावों को स्थायी बनाने तक सब कुछ कवर करता है। अंत तक आप किसी भी पैराग्राफ को अनुवाद कर सकेंगे, चार्ट डेटा लेबल को कस्टमाइज़ कर सकेंगे, और वितरण के लिए तैयार एक नया Word फ़ाइल बना सकेंगे। कोई बाहरी स्क्रिप्ट आवश्यक नहीं है; पूरा वर्कफ़्लो एक ही C# प्रोग्राम में रहता है।

## आवश्यकताएँ

- .NET 6.0 या बाद का संस्करण (कोड .NET Framework 4.7+ के साथ भी काम करता है)
- Aspose.Words for .NET लाइसेंस (या एक मुफ्त इवैल्यूएशन कुंजी)
- Google AI ट्रांसलेटर के लिए इंटरनेट एक्सेस (`Translator` क्लास Google की API का उपयोग करता है)
- एक Word दस्तावेज़ (`input.docx`) जिसमें कम से कम एक पैराग्राफ और एक चार्ट हो

## चरण 1: प्रोजेक्ट सेट अप करें और नेमस्पेस इम्पोर्ट करें

एक नया कंसोल एप्लिकेशन बनाएं और Aspose.Words NuGet पैकेज जोड़ें:

```bash
dotnet new console -n WordAiDemo
cd WordAiDemo
dotnet add package Aspose.Words
dotnet add package Aspose.Words.AI
```

अब `Program.cs` के शीर्ष पर आवश्यक नेमस्पेस शामिल करें:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.AI;          // AI translation helpers
using Aspose.Words.Drawing;    // Chart manipulation classes
using Aspose.Words.Tables;     // For accessing chart series and labels
```

ये इम्पोर्ट्स आपको दस्तावेज़ लोडिंग, AI अनुवाद, और चार्ट एडिटिंग कार्यक्षमता तक पहुँच प्रदान करते हैं।

## चरण 2: स्रोत Word दस्तावेज़ लोड करें

```csharp
// Path to the original file – adjust as needed
string inputPath = @"YOUR_DIRECTORY/input.docx";

// Load the document into memory
Document document = new Document(inputPath);
Console.WriteLine("Document loaded successfully.");
```

फ़ाइल को लोड करने से एक इन‑मेमोरी प्रतिनिधित्व बनता है जिसे आप डिस्क पर मूल फ़ाइल को छुए बिना क्वेरी और संशोधित कर सकते हैं।

## चरण 3: पहले पैराग्राफ को फ्रेंच में अनुवाद करें

पहला पैराग्राफ अक्सर एक शीर्षक या परिचयात्मक वाक्य होता है, जिससे यह अनुवाद के लिए एक अच्छा उम्मीदवार बनता है। `Translator` क्लास Google की AI मॉडल को कॉल करने को एब्स्ट्रैक्ट करती है।

```csharp
// Retrieve the first paragraph in the first section
Paragraph paragraph = document.FirstSection.Body.FirstParagraph;

// Extract the raw text (including trailing paragraph mark)
string originalText = paragraph.GetText();

// Translate the text to French
string translatedText = Translator.Translate(originalText, Language.French);
Console.WriteLine($"Original: {originalText.Trim()}");
Console.WriteLine($"Translated: {translatedText.Trim()}");

// Replace the paragraph's runs with the translated text
paragraph.Runs.Clear();                     // Remove existing runs
paragraph.AppendChild(new Run(document, translatedText)); // Insert new run
```

**यह क्यों काम करता है:**  
`paragraph.Runs.Clear()` सभी मौजूदा टेक्स्ट रन को हटा देता है, जिससे नई अनुवादित सामग्री पुराने कंटेंट के साथ जुड़ नहीं पाती। `new Run(document, translatedText)` एक नया रन बनाता है जो पैराग्राफ की फ़ॉर्मेटिंग को इनहेरिट करता है।

## चरण 4: पहला चार्ट खोजें और उसके डेटा लेबल को कस्टमाइज़ करें

चार्ट `Shape` नोड्स के रूप में `NodeType.Shape` प्रकार के होते हैं। पहला चार्ट `GetChild` के साथ प्राप्त किया जा सकता है।

```csharp
// Find the first chart in the document (deep search)
Chart chart = (Chart)document.GetChild(NodeType.Shape, 0, true);
if (chart == null)
{
    Console.WriteLine("No chart found in the document.");
    return;
}

// Access the first series and its first data label
ChartSeries series = chart.Series[0];
ChartDataLabel dataLabel = series.DataLabels[0];

// Change the label's position and text
dataLabel.Position = ChartDataLabelPosition.OutsideEnd; // Move label outside the bar
dataLabel.Text = "Ventes T1"; // French for "Sales Q1"
Console.WriteLine("Chart data label customized.");
```

**मुख्य चरणों की व्याख्या:**  

- `GetChild(NodeType.Shape, 0, true)` एक डेप्थ‑फ़र्स्ट सर्च करता है और पहला शेप रिटर्न करता है, जो हमारे केस में एक चार्ट है।
- `ChartSeries` डेटा पॉइंट्स का संग्रह दर्शाता है; पहला सीरीज़ (`Series[0]`) आमतौर पर प्राथमिक डेटा सेट से मेल खाता है।
- `ChartDataLabelPosition.OutsideEnd` लेबल को बार के अंत के बाहर ले जाता है, जिससे पठनीयता बढ़ती है।
- `dataLabel.Text` को फ्रेंच स्ट्रिंग सेट करने से लेबल अनुवादित पैराग्राफ के साथ संरेखित हो जाता है।

## चरण 5: अनुवादित पैराग्राफ के साथ दस्तावेज़ सहेजें

```csharp
string translatedDocPath = @"YOUR_DIRECTORY/translated.docx";
document.Save(translatedDocPath);
Console.WriteLine($"Translated document saved to {translatedDocPath}");
```

इस चरण पर दस्तावेज़ में फ्रेंच पैराग्राफ मौजूद है लेकिन अभी भी मूल चार्ट कॉन्फ़िगरेशन रखता है।

## चरण 6: अपडेटेड चार्ट के साथ दस्तावेज़ सहेजें

आप वही `Document` इंस्टेंस फिर से उपयोग कर सकते हैं—इसे पुनः लोड करने की जरूरत नहीं—क्योंकि चार्ट में किए गए बदलाव पहले से ही मेमोरी में हैं।

```csharp
string chartUpdatedPath = @"YOUR_DIRECTORY/chart-updated.docx";
document.Save(chartUpdatedPath);
Console.WriteLine($"Chart‑updated document saved to {chartUpdatedPath}");
```

दोनों फ़ाइलें अब वितरण के लिए तैयार हैं:

- **`translated.docx`** – फ्रेंच पैराग्राफ शामिल है।
- **`chart-updated.docx`** – फ्रेंच पैराग्राफ *और* कस्टमाइज़्ड चार्ट लेबल शामिल है।

## पूर्ण, चलाने योग्य उदाहरण

नीचे पूरा प्रोग्राम दिया गया है जिसे आप `Program.cs` में कॉपी‑पेस्ट कर सकते हैं। यह जैसा है वैसा ही कंपाइल और रन करता है, बशर्ते आपने `YOUR_DIRECTORY` को वास्तविक फ़ोल्डर पाथ से बदल दिया हो।

```csharp
using System;
using Aspose.Words;
using Aspose.Words.AI;
using Aspose.Words.Drawing;
using Aspose.Words.Tables;

namespace WordAiDemo
{
    class Program
    {
        static void Main()
        {
            // ---------- Load the source document ----------
            string inputPath = @"YOUR_DIRECTORY/input.docx";
            Document document = new Document(inputPath);
            Console.WriteLine("Document loaded.");

            // ---------- Translate the first paragraph ----------
            Paragraph paragraph = document.FirstSection.Body.FirstParagraph;
            string original = paragraph.GetText();
            string translated = Translator.Translate(original, Language.French);
            Console.WriteLine


## आगे आप क्या सीखें?

निम्नलिखित ट्यूटोरियल्स उन विषयों को कवर करते हैं जो इस गाइड में प्रदर्शित तकनीकों पर आधारित हैं। प्रत्येक संसाधन में पूर्ण कार्यशील कोड उदाहरण और चरण‑दर‑चरण व्याख्याएँ शामिल हैं, जो आपको अतिरिक्त API फीचर्स में महारत हासिल करने और अपने प्रोजेक्ट्स में वैकल्पिक इम्प्लीमेंटेशन अप्रोचेज़ को एक्सप्लोर करने में मदद करेंगे।

- [चार्ट डेटा लेबल को कस्टमाइज़ करें](/words/english/net/programming-with-charts/chart-data-label/)
- [चार्ट में डेटा लेबल की संख्या का फ़ॉर्मेट](/words/english/net/programming-with-charts/format-number-of-data-label/)
- [चार्ट डेटा लेबल](/words/french/net/programming-with-charts/chart-data-label/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}