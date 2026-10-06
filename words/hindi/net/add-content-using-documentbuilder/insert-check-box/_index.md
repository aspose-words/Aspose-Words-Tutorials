---
title: Aspose.Words for .NET के साथ Word दस्तावेज़ में एक Check Box Form Field जोड़ें
weight: 210
limit:
description: Aspose.Words for .NET का उपयोग करके एक नए Word दस्तावेज़ में प्रोग्रामेटिक रूप से चेक बॉक्स फ़ॉर्म फ़ील्ड कैसे जोड़ें और फ़ाइल को सहेजें, सीखें।
keywords: [Aspose.Words for .NET, insert check box, check box form field, .NET DocumentBuilder, Word document automation, add form field programmatically]
url: /net/add-content-using-documentbuilder/insert-check-box/
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for .NET के साथ Word दस्तावेज़ में एक Check Box Form Field जोड़ें
यह ट्यूटोरियल दिखाता है कि कैसे एक नया Word दस्तावेज़ बनाया जाए और Aspose.Words for .NET के DocumentBuilder का उपयोग करके एक चेक बॉक्स फ़ॉर्म फ़ील्ड डाला जाए। चरणों का पालन करके आप इंटरैक्टिव एलिमेंट जोड़ने के लिए आवश्यक सटीक कोड देखेंगे और फिर दस्तावेज़ को फ़ाइल में सहेजेंगे। यह प्रोग्रामेटिक रूप से सरल फ़ॉर्म-सक्षम Word फ़ाइलें बनाने का एक तेज़ तरीका है।

---

{{< tutorial-widget sourcePath="words/net/add-content-using-documentbuilder/insert-check-box" >}}


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
   ```

4. Apply License (Optional):
   To use the full version, [apply a license](https://purchase.aspose.com/temporary-license/) or use a [free trial](https://releases.aspose.com/).

## Also See
[Aspose.Words for .NET Documentation](https://docs.aspose.com/words/net/)
[Aspose.Words for .NET References](https://reference.aspose.com/words/net/)

## Frequently asked questions

**Q: InsertCheckBox में चौथा आर्गुमेंट (0) क्या दर्शाता है?**
A: यह चेक बॉक्स के दृश्य आकार को पॉइंट्स में निर्दिष्ट करता है; 0 मान Aspose.Words को डिफ़ॉल्ट आकार उपयोग करने के लिए बताता है।

**Q: क्या मैं एक ही नाम के साथ एक से अधिक चेक बॉक्स डाल सकता हूँ?**
A: नहीं – प्रत्येक फ़ॉर्म फ़ील्ड का नाम अद्वितीय होना चाहिए; "CheckBox" नाम के साथ दूसरा चेक बॉक्स डालने का प्रयास करने पर ArgumentException फेंका जाएगा।

**Q: मैं एक नई दस्तावेज़ के बजाय मौजूदा दस्तावेज़ में चेक बॉक्स कैसे जोड़ूँ?**
A: पहले दस्तावेज़ लोड करें (उदा., `Document doc = new Document("Existing.docx");`) फिर उस दस्तावेज़ के लिए DocumentBuilder बनाएं और इच्छित कर्सर पोजीशन पर `InsertCheckBox` को कॉल करें।

**Q: दस्तावेज़ सहेजने के बाद डाले गए चेक बॉक्स की स्थिति कैसे पढ़ूँ?**
A: `doc.Range.FormFields["CheckBox"]` के माध्यम से फ़ॉर्म फ़ील्ड प्राप्त करें और उसकी `Checked` प्रॉपर्टी को जांचें कि वह चेक किया गया है या नहीं।

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}