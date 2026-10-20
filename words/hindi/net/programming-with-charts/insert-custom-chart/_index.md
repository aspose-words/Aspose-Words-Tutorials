---
title: Aspose.Words for .NET का उपयोग करके Word दस्तावेज़ में कस्टम कॉलम चार्ट डालें
weight: 310
limit:
description: एक Word फ़ाइल बनाएं, कॉलम चार्ट डालें, उसकी डेटा को कस्टम एरे से बदलें, एक शीर्षक जोड़ें, और सभी Aspose.Words for .NET के साथ सहेजें।
keywords: [Aspose.Words for .NET, custom chart, column chart, Word document chart, populate chart from array, insert chart Aspose.Words]
url: /net/programming-with-charts/insert-custom-chart/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: एक Word फ़ाइल बनाएं, कॉलम चार्ट डालें, उसकी डेटा को कस्टम एरे से बदलें,
    एक शीर्षक जोड़ें, और सभी Aspose.Words for .NET के साथ सहेजें।
  headline: Aspose.Words for .NET का उपयोग करके Word दस्तावेज़ में कस्टम कॉलम चार्ट
    डालें
  type: TechArticle
- description: एक Word फ़ाइल बनाएं, कॉलम चार्ट डालें, उसकी डेटा को कस्टम एरे से बदलें,
    एक शीर्षक जोड़ें, और सभी Aspose.Words for .NET के साथ सहेजें।
  name: Aspose.Words for .NET का उपयोग करके Word दस्तावेज़ में कस्टम कॉलम चार्ट डालें
  steps:
  - name: एक नया Document बनाएं और उससे जुड़ा एक DocumentBuilder बनाएं।
    text: एक नया Document बनाएं और उससे जुड़ा एक DocumentBuilder बनाएं।
  - name: डॉक्यूमेंट में 432x252 पॉइंट आकार का एक कॉलम चार्ट डालें और उसका Chart ऑब्जेक्ट
      प्राप्त करें।
    text: डॉक्यूमेंट में 432x252 पॉइंट आकार का एक कॉलम चार्ट डालें और उसका Chart ऑब्जेक्ट
      प्राप्त करें।
  - name: चार्ट से स्वचालित रूप से उत्पन्न नमूना सीरीज़ को हटा दें।
    text: चार्ट से स्वचालित रूप से उत्पन्न नमूना सीरीज़ को हटा दें।
  - name: X‑axis श्रेणी लेबल और प्रत्येक सीरीज़ के लिए लेजेंड एंट्रीज़ को परिभाषित
      करें।
    text: X‑axis श्रेणी लेबल और प्रत्येक सीरीज़ के लिए लेजेंड एंट्रीज़ को परिभाषित
      करें।
  - name: एक दो‑आयामी एरे बनाएं जहाँ प्रत्येक पंक्ति एक सीरीज़ के मान रखती है।
    text: एक दो‑आयामी एरे बनाएं जहाँ प्रत्येक पंक्ति एक सीरीज़ के मान रखती है।
  - name: प्रत्येक सीरीज़ पर इटररेट करें, मैट्रिक्स से उसकी पंक्ति के मान निकालें,
      और संबंधित लेजेंड एंट्री तथा X‑axis लेबल के साथ सीरीज़ को चार्ट में जोड़ें।
    text: प्रत्येक सीरीज़ पर इटररेट करें, मैट्रिक्स से उसकी पंक्ति के मान निकालें,
      और संबंधित लेजेंड एंट्री तथा X‑axis लेबल के साथ सीरीज़ को चार्ट में जोड़ें।
  - name: चार्ट शीर्षक टेक्स्ट को 'Half‑Yearly Revenue' सेट करें और इसे दृश्यमान बनाएं।
    text: चार्ट शीर्षक टेक्स्ट को 'Half‑Yearly Revenue' सेट करें और इसे दृश्यमान बनाएं।
  - name: कस्टम चार्ट वाले दस्तावेज़ को .docx फ़ाइल के रूप में सहेजें।
    text: कस्टम चार्ट वाले दस्तावेज़ को .docx फ़ाइल के रूप में सहेजें।
  type: HowTo
- questions:
  - answer: '`Chart.Series.Add` मान एरे की लंबाई को X‑axis लेबल की संख्या के बराबर
      होने की अपेक्षा करता है, और आपको प्रत्येक लेजेंड एंट्री के लिए ठीक एक सीरीज़
      जोड़नी चाहिए; असंगति होने पर रनटाइम पर `ArgumentException` फेंका जाएगा।'
    question: '`dataMatrix` में पंक्तियों या कॉलम की लंबाई `legendEntries` या `xLabels`
      की लंबाई से मेल नहीं खाती तो क्या होगा?'
  - answer: हाँ—`docBuilder.InsertChart` में `ChartType.Column` को किसी अन्य `ChartType`
      (जैसे `ChartType.Line`) से बदलें और बाद के `Series.Add` कॉल्स नए चार्ट को उसी
      तरह भर देंगे।
    question: क्या मैं समान डेटा‑पॉपुलेशन लॉजिक के साथ किसी अलग चार्ट प्रकार, जैसे
      लाइन चार्ट, का उपयोग कर सकता हूँ?
  - answer: '`InsertChart` द्वारा लौटाए गए `Shape` की `Width` और `Height` प्रॉपर्टीज़
      को समायोजित करें (उदाहरण: `chartContainer.Width = 500; chartContainer.Height
      = 300;`)।'
    question: चार्ट को डालने के बाद उसका आकार कैसे बदलें?
  - answer: प्रत्येक सीरीज़ को जोड़ने के बाद `chartObj.Series[i].HasDataLabel = true;`
      सेट करें, या `chartObj.Series` पर लूप करके `HasDataLabel` को सक्षम करें ताकि
      चार्ट पर मान दिखें।
    question: क्या चार्ट के प्रत्येक कॉलम पर डेटा लेबल जल्दी से दिखाने का कोई तरीका
      है?
  type: FAQPage
images:
- /net/programming-with-charts/insert-custom-chart/og-image.png
og_title: Word दस्तावेज़ में कस्टम कॉलम चार्ट जोड़ें
og_description: चार्ट की डिफ़ॉल्ट डेटा को अपनी एरे से बदलें और सेकंडों में एक शीर्षक सेट करें।
og_image_alt: Aspose.Words for .NET का उपयोग करके बनाए गए कस्टम कॉलम चार्ट के साथ Word दस्तावेज़ का स्क्रीनशॉट
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for .NET का उपयोग करके Word दस्तावेज़ में कस्टम कॉलम चार्ट डालें
यह ट्यूटोरियल आपको Word दस्तावेज़ बनाने, कॉलम चार्ट डालने, उसकी डिफ़ॉल्ट डेटा साफ़ करने, और दो‑आयामी एरे से कस्टम मानों से चार्ट को भरने की प्रक्रिया दिखाता है—प्रत्येक पंक्ति को एक सीरीज़ और प्रत्येक कॉलम को एक श्रेणी के रूप में मैप करते हुए। आप फ़ाइल सहेजने से पहले चार्ट शीर्षक कैसे जोड़ें, यह भी देखेंगे। पूरी तरह कस्टमाइज़्ड चार्ट बनाने के लिए चरणों का पालन करें।

---

{{< tutorial-widget sourcePath="words/net/programming-with-charts/insert-custom-chart" >}}


{{< /blocks/products/pf/tutorial-page-section >}}

{{< blocks/products/pf/tutorial-page-section >}}
## Installation Instructions
1. Download Aspose.Words for .NET:
   Get the latest version from the [Aspose Downloads page](https://releases.aspose.com/words/net/).

2. Install via NuGet:
   - Open your Visual Studio project.
   - Navigate to the NuGet Package Manager (Tools > NuGet Package Manager > Manage NuGet Packages for Solution).
   - Search for "Aspose.Words" and click Install.

3. Add Namespace References:
   Add the following namespace at the top of your code file:
   ```csharp
   using Aspose.Words;
   using Aspose.Words.Saving;
   using Aspose.Words.Drawing;
   using Aspose.Words.Fields;
   using System.Drawing;
   ```

4. Apply License (Optional):
   To use the full version, [apply a license](https://purchase.aspose.com/temporary-license/) or use a [free trial](https://releases.aspose.com/).

## Also See
[Aspose.Words for .NET Documentation](https://docs.aspose.com/words/net/)
[Aspose.Words for .NET References](https://reference.aspose.com/words/net/)

## Frequently asked questions

**Q: `dataMatrix` में पंक्तियों या कॉलम की लंबाई `legendEntries` या `xLabels` की लंबाई से मेल नहीं खाती तो क्या होगा?**  
A: `Chart.Series.Add` मान एरे की लंबाई को X‑axis लेबल की संख्या के बराबर होने की अपेक्षा करता है, और आपको प्रत्येक लेजेंड एंट्री के लिए ठीक एक सीरीज़ जोड़नी चाहिए; असंगति होने पर रनटाइम पर `ArgumentException` फेंका जाएगा।

**Q: क्या मैं समान डेटा‑पॉपुलेशन लॉजिक के साथ किसी अलग चार्ट प्रकार, जैसे लाइन चार्ट, का उपयोग कर सकता हूँ?**  
A: हाँ—`docBuilder.InsertChart` में `ChartType.Column` को किसी अन्य `ChartType` (जैसे `ChartType.Line`) से बदलें और बाद के `Series.Add` कॉल्स नए चार्ट को उसी तरह भर देंगे।

**Q: चार्ट को डालने के बाद उसका आकार कैसे बदलें?**  
A: `InsertChart` द्वारा लौटाए गए `Shape` की `Width` और `Height` प्रॉपर्टीज़ को समायोजित करें (उदाहरण: `chartContainer.Width = 500; chartContainer.Height = 300;`)।

**Q: क्या चार्ट के प्रत्येक कॉलम पर डेटा लेबल जल्दी से दिखाने का कोई तरीका है?**  
A: प्रत्येक सीरीज़ को जोड़ने के बाद `chartObj.Series[i].HasDataLabel = true;` सेट करें, या `chartObj.Series` पर लूप करके `HasDataLabel` को सक्षम करें ताकि चार्ट पर मान दिखें।

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}