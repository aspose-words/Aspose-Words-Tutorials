---
category: general
date: 2026-09-21
description: Aspose.Words का उपयोग करके C# में Word दस्तावेज़ बनाना, कॉलम चार्ट सम्मिलित
  करना, लेबल की स्थिति सेट करना और मान प्रदर्शित करना सीखें, एक चरण‑दर‑चरण गाइड में।
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document c#
- how to insert chart
- how to set label
- how to display values
- insert column chart word
language: hi
lastmod: 2026-09-21
og_description: Aspose.Words के साथ C# में Word दस्तावेज़ बनाएं। यह ट्यूटोरियल दिखाता
  है कि कॉलम चार्ट कैसे डालें, लेबल की स्थिति सेट करें, और मान प्रदर्शित करें।
og_image_alt: Screenshot of a Word document created with C# that contains a column
  chart and data labels
og_title: C# में Word दस्तावेज़ बनाएं – कॉलम चार्ट डालें, लेबल सेट करें, मान दिखाएँ
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: Learn how to create Word document C# and insert a column chart, set
    label position, and display values using Aspose.Words in a step‑by‑step guide.
  headline: How to create Word document C# with a column chart and formatted labels
  type: TechArticle
- description: Learn how to create Word document C# and insert a column chart, set
    label position, and display values using Aspose.Words in a step‑by‑step guide.
  name: How to create Word document C# with a column chart and formatted labels
  steps:
  - name: Expected result
    text: When you open `output.docx`, you should see a single column chart similar
      to the image below. Each column has a numeric label at its top, inside the column,
      displaying the series value.
  - name: Adding custom data to the chart
    text: 'If you need to replace the placeholder data, you can modify the chart’s
      `Series` collection:'
  - name: Changing label font and color
    text: 'You can further customize the label appearance:'
  - name: Inserting multiple charts
    text: The `DocumentBuilder` can insert as many charts as you need. Just call `InsertChart`
      again after moving the cursor with `builder.Writeln()` or `builder.InsertParagraph()`.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
- Charts
title: C# में कॉलम चार्ट और स्वरूपित लेबल के साथ Word दस्तावेज़ कैसे बनाएं
url: /hi/net/programming-with-charts/how-to-create-word-document-c-with-a-column-chart-and-format/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C# के साथ कॉलम चार्ट और फ़ॉर्मेटेड लेबल्स वाला Word दस्तावेज़ कैसे बनाएं

यदि आपको **create Word document C#** चाहिए जिसमें चार्ट शामिल हो, तो यह गाइड आपको बिल्कुल बताता है कि इसे कैसे करें। आप सीखेंगे कि कॉलम चार्ट कैसे डालें, उसके डेटा लेबल को कैसे स्थित करें, और लेबल के मान कैसे दिखाएं—सब Aspose.Words for .NET के साथ।

चार्ट‑सक्षम Word फ़ाइल बनाना पहले Microsoft Word में मैन्युअल काम की आवश्यकता होती थी। यहाँ वर्णित **how to insert chart** चरणों के साथ, आप कोड से पूरी प्रक्रिया को स्वचालित कर सकते हैं, जिससे रिपोर्ट जनरेशन तेज़ और दोहराने योग्य बनता है। ट्यूटोरियल में **how to set label** प्रॉपर्टीज़ और **how to display values** भी कवर किए गए हैं ताकि चार्ट अंतिम उपयोगकर्ताओं के लिए तैयार हो।

इस लेख के अंत तक आपके पास एक पूर्ण, चलाने योग्य C# प्रोग्राम होगा जो एक `.docx` फ़ाइल बनाता है जिसमें एक कॉलम चार्ट होता है, जिसके डेटा लेबल प्रत्येक कॉलम के अंदर दिखाई देते हैं और उनके संख्यात्मक मान दिखाते हैं।

## आवश्यकताएँ

* .NET 6.0 SDK या बाद का संस्करण स्थापित हो  
* **Aspose.Words for .NET** की लाइसेंस प्राप्त कॉपी (टेस्टिंग के लिए फ्री ट्रायल काम करता है)  
* Visual Studio 2022 या Visual Studio Code जैसे IDE  

`Aspose.Words` के अलावा कोई अतिरिक्त NuGet पैकेज आवश्यक नहीं है।

## चरण 1: प्रोजेक्ट सेट अप करें और Aspose.Words जोड़ें

एक नया कंसोल प्रोजेक्ट बनाएं और Aspose.Words पैकेज जोड़ें:

```bash
dotnet new console -n WordChartDemo
cd WordChartDemo
dotnet add package Aspose.Words
```

`dotnet add package` कमांड **Aspose.Words** का नवीनतम स्थिर संस्करण लाता है, जिसमें **insert column chart word** उदाहरण में उपयोग किया गया चार्ट API शामिल है।

## चरण 2: नया खाली Word दस्तावेज़ बनाएं

पहला कोड टुकड़ा एक खाली दस्तावेज़ और एक `DocumentBuilder` बनाता है जो आपको सामग्री डालने देता है। यह **create word document C#** का आधार है।

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // Step 2: Initialize a new blank document.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

`Document` पूरे `.docx` फ़ाइल का प्रतिनिधित्व करता है, जबकि `DocumentBuilder` ऐसे मेथड्स प्रदान करता है जैसे `InsertParagraph`, `InsertImage`, और इस ट्यूटोरियल के लिए महत्वपूर्ण `InsertChart`।

## चरण 3: कॉलम चार्ट डालें (how to insert chart)

अब हम एक **column chart** डालते हैं। `InsertChart` मेथड चार्ट प्रकार, चौड़ाई, और ऊँचाई को पॉइंट्स में लेता है।

```csharp
        // Step 3: Insert a column chart with a width of 400 pt and height of 300 pt.
        Chart chart = builder.InsertChart(ChartType.Column, 400, 300);
```

इस चरण पर चार्ट में डिफ़ॉल्ट डेटा सीरीज़ प्लेसहोल्डर मानों के साथ होती है। यदि आपको कस्टम नंबर चाहिए तो आप सीरीज़ डेटा बदल सकते हैं, लेकिन **how to set label** और **how to display values** दिखाने के लिए डिफ़ॉल्ट डेटा पर्याप्त है।

## चरण 4: डेटा लेबल को प्रत्येक कॉलम के अंदर स्थित करें (how to set label)

डेटा लेबल वह टेक्स्ट है जो प्रत्येक कॉलम पर दिखाई देता है। चार्ट को पढ़ने में आसान बनाने के लिए, हम लेबल को कॉलम के अंदर ले जाते हैं और उसका संख्यात्मक मान सक्षम करते हैं।

```csharp
        // Step 4: Access the first data label of the first series.
        ChartDataLabel label = chart.DataLabels[0];

        // Position the label at the inside end of the column.
        label.Position = ChartDataLabelPosition.InsideEnd;

        // Show the numeric value of each data point.
        label.ShowValue = true;
```

`ChartDataLabelPosition.InsideEnd` लेबल को कॉलम के शीर्ष पर रखता है लेकिन फिर भी कॉलम के आकार के भीतर, जो रिपोर्ट्स के लिए सामान्य दृश्य शैली है। `ShowValue` को `true` सेट करने से **how to display values** की आवश्यकता पूरी होती है।

## चरण 5: दस्तावेज़ सहेजें

अंत में, दस्तावेज़ को डिस्क पर लिखें। फ़ाइल को Microsoft Word, LibreOffice, या किसी भी व्यूअर से खोला जा सकता है जो Open XML फ़ॉर्मेट का समर्थन करता है।

```csharp
        // Step 5: Save the document to the output folder.
        string outputPath = Path.Combine(Environment.CurrentDirectory, "output.docx");
        doc.Save(outputPath);

        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

प्रोग्राम चलाने पर `output.docx` बनता है जिसमें एक कॉलम चार्ट होता है, जिसके डेटा लेबल प्रत्येक कॉलम के अंदर स्थित होते हैं और उनके मान दिखाते हैं।

### अपेक्षित परिणाम

जब आप `output.docx` खोलेंगे, तो आपको नीचे दी गई छवि के समान एक एकल कॉलम चार्ट दिखना चाहिए। प्रत्येक कॉलम के शीर्ष पर, कॉलम के अंदर, एक संख्यात्मक लेबल होता है जो सीरीज़ मान प्रदर्शित करता है।

![Chart in a Word document created with C#](/images/word-chart-example.png "Chart in a Word document created with C# – create word document C#")

*Alt text:* *C# के साथ बनाए गए Word दस्तावेज़ में चार्ट जो दिखाता है कि कैसे column chart word डालें और मान प्रदर्शित करें।*

## सामान्य विविधताएँ और किनारी मामलों

### चार्ट में कस्टम डेटा जोड़ना

यदि आपको प्लेसहोल्डर डेटा बदलना है, तो आप चार्ट के `Series` संग्रह को संशोधित कर सकते हैं:

```csharp
// Replace the default series with custom values.
chart.Series.Clear();
ChartSeries series = chart.Series.Add(ChartType.Column);
series.Name = "Sales Q1";
series.AddCategory("Jan", 120);
series.AddCategory("Feb", 150);
series.AddCategory("Mar", 180);
```

### लेबल फ़ॉन्ट और रंग बदलना

आप लेबल की उपस्थिति को और कस्टमाइज़ कर सकते हैं:

```csharp
label.Font.Name = "Arial";
label.Font.Size = 10;
label.Font.Color = System.Drawing.Color.DarkBlue;
```

### कई चार्ट डालना

`DocumentBuilder` जितने भी चार्ट चाहिए उतने डाल सकता है। बस `builder.Writeln()` या `builder.InsertParagraph()` से कर्सर को स्थानांतरित करने के बाद `InsertChart` फिर से कॉल करें।

## प्रो टिप्स

* **Pro tip:** `chart.HasTitle = true` सेट करें और `chart.Title.Text` असाइन करें ताकि चार्ट को एक वर्णनात्मक शीर्षक मिले। यह स्क्रीन रीडर्स के लिए एक्सेसिबिलिटी को सुधारता है।
* **Watch out for:** नेटवर्क शेयर पर सहेजते समय सुनिश्चित करें कि एप्लिकेशन के पास लिखने की अनुमति है; अन्यथा `doc.Save` `UnauthorizedAccessException` फेंकेगा।
* **Performance tip:** कई इन्सर्शन के लिए एक ही `DocumentBuilder` इंस्टेंस को पुन: उपयोग करें; प्रत्येक ऑपरेशन के लिए नया बिल्डर बनाना अनावश्यक ओवरहेड जोड़ता है।

## निष्कर्ष

अब आप जानते हैं कि **create Word document C#** जिसमें कॉलम चार्ट हो, कैसे **insert chart** तत्व डालें, **set label** स्थितियों को सेट करें, और प्रत्येक कॉलम के अंदर **display values** दिखाएँ। ऊपर दिया गया पूर्ण कोड उदाहरण चलाने के लिए तैयार है, और आप इसे कस्टम डेटा, स्टाइलिंग, या अतिरिक्त चार्ट्स के साथ विस्तारित कर सकते हैं।

अगला, संबंधित विषयों जैसे **how to insert picture**, **how to generate tables**, या **how to apply document themes** को एक्सप्लोर करें ताकि आपके ऑटोमेटेड रिपोर्ट्स और भी समृद्ध बनें। कोडिंग का आनंद लें!

## अब आपको क्या सीखना चाहिए?

निम्नलिखित ट्यूटोरियल्स उन निकट संबंधित विषयों को कवर करते हैं जो इस गाइड में दिखाए गए तकनीकों पर आधारित हैं। प्रत्येक संसाधन में पूर्ण कार्यशील कोड उदाहरण और चरण-दर-चरण व्याख्याएँ शामिल हैं जो आपको अतिरिक्त API फीचर्स में निपुण बनने और अपने प्रोजेक्ट्स में वैकल्पिक कार्यान्वयन दृष्टिकोणों का पता लगाने में मदद करती हैं।

- [Insert Column Chart in Word Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-column-chart/)
- [Insert a Simple Column Chart in Word Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-simple-column-chart/)
- [Insert Area Chart in Word Document | Aspose.Words for .NET](/words/english/net/working-with-charts/insert-area-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}