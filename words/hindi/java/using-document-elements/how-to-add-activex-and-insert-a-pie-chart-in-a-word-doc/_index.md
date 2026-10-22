---
category: general
date: 2026-08-17
description: Aspose.Words का उपयोग करके Word दस्तावेज़ में ActiveX नियंत्रण कैसे जोड़ें
  और पाई चार्ट डालें। एक स्लाइस को एक्सप्लोड करें और कुछ चरणों में DOCX के रूप में
  सहेजें।
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to add activex
- insert pie chart
- save as docx
- how to insert chart
- explode pie slice
language: hi
lastmod: 2026-08-17
og_description: ActiveX नियंत्रण जोड़ना, पाई चार्ट डालना, स्लाइस को फटाना, और Aspose.Words
  के साथ DOCX के रूप में सहेजना – पूर्ण चरण‑दर‑चरण गाइड।
og_image_alt: Screenshot of a Word document showing an ActiveX button and a pie chart
  with an exploded slice
og_title: Word दस्तावेज़ में ActiveX जोड़ने और पाई चार्ट सम्मिलित करने का तरीका
schemas:
- author: Aspose
  dateModified: '2026-08-17'
  description: How to add ActiveX controls and insert a pie chart in a Word doc using
    Aspose.Words. Explode a slice and save as DOCX in a few steps.
  headline: How to add ActiveX and insert a pie chart in a Word doc
  type: TechArticle
tags:
- Aspose.Words
- ActiveX
- Chart
- DOCX
title: Word दस्तावेज़ में ActiveX जोड़ने और पाई चार्ट सम्मिलित करने का तरीका
url: /hi/java/using-document-elements/how-to-add-activex-and-insert-a-pie-chart-in-a-word-doc/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word दस्तावेज़ में ActiveX जोड़ना और पाई चार्ट सम्मिलित करना

यदि आपको **ActiveX** कंट्रोल जोड़ने और Word दस्तावेज़ में चार्ट एम्बेड करने की आवश्यकता है, तो यह ट्यूटोरियल एक पूर्ण, चलाने योग्य समाधान दिखाता है। Aspose.Words का उपयोग करके आप एक ActiveX CommandButton रख सकते हैं, पाई चार्ट बना सकते हैं, ज़ोर देने के लिए एक स्लाइस को एक्सप्लोड कर सकते हैं, और अंत में **DOCX के रूप में सहेज सकते** हैं केवल कुछ ही C# लाइनों में।

नीचे के सेक्शन में आप सभी आवश्यक इम्पोर्ट, पूरा कोड लिस्टिंग, और प्रत्येक चरण के महत्व की व्याख्याएँ देखेंगे। अंत तक आप प्रोग्रामेटिक रूप से उत्पन्न किसी भी .docx फ़ाइल में इंटरैक्टिव कंट्रोल और विज़ुअल डेटा एकीकृत कर पाएँगे।

## आवश्यकताएँ

शुरू करने से पहले सुनिश्चित करें कि आपके पास है:

* .NET 6.0 या बाद का संस्करण (कोड .NET Framework 4.7+ के साथ भी काम करता है)
* Aspose.Words for .NET पैकेज (NuGet के माध्यम से उपलब्ध)
* Visual Studio 2022 या VS Code जैसा विकास वातावरण
* C# और Word ऑब्जेक्ट मॉडल का बुनियादी ज्ञान

कोई अतिरिक्त थर्ड‑पार्टी चार्ट लाइब्रेरी आवश्यक नहीं है—Aspose.Words में बिल्ट‑इन चार्ट निर्माण सुविधा है।

## Aspose.Words के साथ ActiveX कंट्रोल जोड़ना

ActiveX कंट्रोल आपको Word फ़ाइल में सीधे इंटरैक्टिव UI एलिमेंट एम्बेड करने की अनुमति देते हैं। इस गाइड में हम एक **CommandButton** जोड़ते हैं जिसे बाद में VBA कोड से जोड़ा जा सकता है।

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

// Step 1: Create a new document and a DocumentBuilder
Document document = new Document();
DocumentBuilder builder = new DocumentBuilder(document);

// Step 2: Insert a group shape to hold the ActiveX control
GroupShape groupShape = builder.InsertGroupShape();

// Step 3: Insert a rectangle shape, hide it, and attach it to the group
Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 100, 50);
groupShape.AppendChild(rectangleShape);
rectangleShape.SetHidden(true);

// Step 4: Insert a plain‑text StructuredDocumentTag (optional placeholder)
StructuredDocumentTag plainTextTag = builder.InsertStructuredDocumentTag(
    StructuredDocumentTagType.PlainText, "MyTag");

// Step 5: Insert the CommandButton ActiveX control
Forms2OleControl commandButton = builder.InsertForms2OleControl();
commandButton.SetActiveXControlType(Forms2OleControlType.CommandButton);
commandButton.SetCaption("Click Me");

// The CommandButton now appears in the document and can be used in VBA macros.
```

**यह क्यों काम करता है:**  
`InsertForms2OleControl` एक OLE कंटेनर बनाता है जिसे Word UI ActiveX कंट्रोल के रूप में पहचानता है। कंट्रोल प्रकार को `CommandButton` सेट करके और कैप्शन देने से यह एक सामान्य बटन की तरह व्यवहार करता है जब उपयोगकर्ता फ़ाइल को Word में खोलता है।

## पाई चार्ट सम्मिलित करना और स्लाइस को एक्सप्लोड करना

चार्ट दस्तावेज़ के भीतर डेटा को विज़ुअलाइज़ करने में उपयोगी होते हैं। नीचे दिए गए चरण **चार्ट सम्मिलित करने** और विशेष रूप से **पाई चार्ट** जिसमें पहला स्लाइस एक्सप्लोड किया गया है, को दर्शाते हैं।

```csharp
// Step 6: Insert a pie chart (400 × 300 points)
Chart pieChart = (Chart)builder.InsertChart(ChartType.Pie, 400, 300);

// Populate the chart with sample data
pieChart.Series.Clear();
ChartSeries series = pieChart.Series.Add("Sales", new[] { "Q1", "Q2", "Q3", "Q4" },
                                          new[] { 12000, 15000, 9000, 13000 });

// Step 7: Explode the first slice for emphasis
series.SetExplode(0, true);

// Optional: Customize colors or labels here if needed
```

**स्लाइस को एक्सप्लोड करने का कारण:**  
`SetExplode(0, true)` कॉल करने से Aspose.Words पहले डेटा पॉइंट को ऑफसेट करता है, जिससे दर्शक की नजर उस सेगमेंट की ओर आकर्षित होती है। यह प्रस्तुतियों में प्रमुख मान को उजागर करने की सामान्य तकनीक है।

## DOCX के रूप में सहेजें

ActiveX बटन और चार्ट जोड़ने के बाद, दस्तावेज़ को डिस्क पर सहेजें। यह चरण **DOCX के रूप में सहेजने** को मानक मेथड से दर्शाता है।

```csharp
// Step 8: Save the document in DOCX format
document.Save("Output.docx", SaveFormat.Docx);
```

फ़ाइल `Output.docx` अब एक इंटरैक्टिव बटन, एक्सप्लोडेड स्लाइस वाला पाई चार्ट, और अतिरिक्त प्लगइन्स के बिना Microsoft Word में खुलने योग्य है।

## पूर्ण चलाने योग्य उदाहरण

सब कुछ मिलाकर, यहाँ एक स्व-निहित प्रोग्राम है जिसे आप कॉन्सोल एप्लिकेशन में कॉपी करके तुरंत चला सकते हैं।

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // Create document and builder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert group shape and hidden rectangle (required for ActiveX positioning)
        GroupShape group = builder.InsertGroupShape();
        Shape rect = builder.InsertShape(ShapeType.Rectangle, 100, 50);
        group.AppendChild(rect);
        rect.SetHidden(true);

        // Optional placeholder tag
        builder.InsertStructuredDocumentTag(StructuredDocumentTagType.PlainText, "MyTag");

        // Insert CommandButton ActiveX control
        Forms2OleControl button = builder.InsertForms2OleControl();
        button.SetActiveXControlType(Forms2OleControlType.CommandButton);
        button.SetCaption("Click Me");

        // Insert pie chart and explode first slice
        Chart chart = (Chart)builder.InsertChart(ChartType.Pie, 400, 300);
        chart.Series.Clear();
        ChartSeries series = chart.Series.Add("Revenue", new[] { "Jan", "Feb", "Mar" },
                                               new[] { 5000, 7000, 3000 });
        series.SetExplode(0, true); // explode pie slice

        // Save the document
        doc.Save("Output.docx", SaveFormat.Docx);

        Console.WriteLine("Document created successfully: Output.docx");
    }
}
```

**अपेक्षित परिणाम:**  
`Output.docx` को Word में खोलने पर *Click Me* लेबल वाला बटन और पहला स्लाइस (January) बाकी से ऑफसेट किया हुआ पाई चार्ट दिखेगा। बटन VBA इवेंट हैंडलिंग के लिए तैयार है, और चार्ट को Word के बिल्ट‑इन चार्ट टूल्स से संपादित किया जा सकता है।

## सामान्य प्रश्न और किनारे के मामले

* **क्या मैं अन्य ActiveX प्रकार जोड़ सकता हूँ?**  
  हाँ। `Forms2OleControlType.CommandButton` को `Forms2OleControlType` enum के किसी भी मान (जैसे `CheckBox`, `OptionButton`) से बदलें। वही इंसर्शन पैटर्न लागू होता है।

* **यदि मुझे अलग चार्ट प्रकार चाहिए तो?**  
  `InsertChart` कॉल में `ChartType.Bar`, `ChartType.Line` आदि का उपयोग करें। **चार्ट सम्मिलित करने** चरण समान रहता है; केवल enum मान बदलता है।

* **एक्सप्लोडेड स्लाइस का आकार कैसे नियंत्रित करें?**  
  Aspose.Words वर्तमान में बाइनरी एक्सप्लोड फ़्लैग (true/false) का समर्थन करता है। अधिक सूक्ष्म नियंत्रण (जैसे ऑफसेट दूरी) के लिए सहेजने के बाद मूल OOXML को संपादित करना पड़ेगा।

* **क्या दस्तावेज़ पुराने Word संस्करणों के साथ संगत है?**  
  DOCX के रूप में सहेजने से Word 2007 और बाद के संस्करणों के साथ संगतता सुनिश्चित होती है। Word 2003 के लिए आप `SaveFormat.Doc` में बदल सकते हैं, लेकिन उस फॉर्मेट में ActiveX समर्थन सीमित है।

* **क्या मुझे `System.Drawing` का रेफ़रेंस चाहिए?**  
  नहीं। सभी ड्रॉइंग ऑब्जेक्ट Aspose.Words द्वारा प्रदान किए जाते हैं, इसलिए आवश्यक NuGet पैकेज केवल `Aspose.Words` है।

## निष्कर्ष

आप अब जानते हैं **ActiveX कैसे जोड़ें**, **पाई चार्ट कैसे सम्मिलित करें**, **पाई स्लाइस को एक्सप्लोड करें**, और **DOCX के रूप में सहेजें** Aspose.Words for .NET का उपयोग करके। पूरा उदाहरण दस्तावेज़ निर्माण से लेकर अंतिम सहेजने तक प्रत्येक चरण को कवर करता है, और प्रत्येक API कॉल के पीछे की तर्कशक्ति को समझाता है।

आगे आप खोज सकते हैं:

* CommandButton क्लिक पर प्रतिक्रिया देने वाले VBA मैक्रो जोड़ना (**चार्ट सम्मिलित करने** और डेटा अपडेट को ऑटोमेट करना)
* चार्ट की उपस्थिति (रंग, डेटा लेबल) को कॉर्पोरेट ब्रांडिंग के अनुसार कस्टमाइज़ करना
* अतिरिक्त ActiveX कंट्रोल जैसे **ComboBox** या **ListBox** एम्बेड करके फ़ॉर्म को अधिक समृद्ध बनाना

कोड के साथ प्रयोग करने, नमूना डेटा बदलने, और अपने दस्तावेज़‑जनरेशन पाइपलाइन में समाधान को एकीकृत करने में स्वतंत्र महसूस करें। कोडिंग का आनंद लें!

## आगे क्या सीखें?

निम्नलिखित ट्यूटोरियल्स उन विषयों को कवर करते हैं जो इस गाइड में प्रदर्शित तकनीकों पर आधारित हैं। प्रत्येक संसाधन में पूर्ण कार्यशील कोड उदाहरण और चरण‑दर‑चरण व्याख्याएँ शामिल हैं, जिससे आप अतिरिक्त API फीचर्स में महारत हासिल कर सकें और अपने प्रोजेक्ट्स में वैकल्पिक इम्प्लीमेंटेशन अप्रोच का अन्वेषण कर सकें।

- [Aspose.Words for .NET का उपयोग करके Word में कॉलम चार्ट सम्मिलित करें](/words/english/net/working-with-charts/insert-column-chart/)
- [Aspose.Words for .NET का उपयोग करके Word में सरल कॉलम चार्ट सम्मिलित करें](/words/english/net/working-with-charts/insert-simple-column-chart/)
- [Aspose.Words for .NET का उपयोग करके Word में बबल चार्ट सम्मिलित करें](/words/english/net/working-with-charts/insert-bubble-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}