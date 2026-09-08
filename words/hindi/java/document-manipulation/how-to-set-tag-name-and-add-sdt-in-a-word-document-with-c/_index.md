---
category: general
date: 2026-09-08
description: C# का उपयोग करके Word दस्तावेज़ में टैग नाम सेट करें और एक कंटेंट कंट्रोल
  (SDT) बनाएं। जानें कि कैसे SDT जोड़ें, टैग में टेक्स्ट लिखें, और दस्तावेज़ को संशोधित
  करें।
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- set tag name
- how to add sdt
- modify word document
- create content control
- write text to tag
language: hi
lastmod: 2026-09-08
og_description: C# का उपयोग करके वर्ड दस्तावेज़ में टैग नाम सेट करें और कंटेंट कंट्रोल
  (SDT) बनाएं। SDT जोड़ने, टैग में टेक्स्ट लिखने और दस्तावेज़ को संशोधित करने के लिए
  इस चरण‑दर‑चरण गाइड का पालन करें।
og_image_alt: Screenshot showing a Word document with a StructuredDocumentTag whose
  tag name is set
og_title: Word दस्तावेज़ में टैग नाम सेट करें और SDT जोड़ें – C# गाइड
schemas:
- author: Aspose
  dateModified: '2026-09-08'
  description: Set tag name and create a content control (SDT) in a Word document
    using C#. Learn how to add SDT, write text to tag, and modify the document.
  headline: How to set tag name and add SDT in a Word document with C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: C# का उपयोग करके Word दस्तावेज़ में टैग नाम सेट करना और SDT जोड़ना
url: /hi/java/document-manipulation/how-to-set-tag-name-and-add-sdt-in-a-word-document-with-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C# के साथ Word दस्तावेज़ में टैग नाम सेट करना और SDT जोड़ना

यदि आपको Word फ़ाइलों के साथ काम करते समय StructuredDocumentTag (SDT) के लिए **टैग नाम सेट** करना है, तो यह गाइड आपको बिल्कुल बताता है कि कैसे करना है। आप एक पूर्ण, चलाने योग्य उदाहरण देखेंगे जो **एक कंटेंट कंट्रोल बनाता है**, टैग में टेक्स्ट लिखता है, और **Word दस्तावेज़ को अंत‑से‑अंत संशोधित करता है**।

डेवलपर्स अक्सर पूछते हैं, *“एक मौजूदा .docx में sdt कैसे जोड़ें और फिर *टैग में टेक्स्ट लिखें*?”* – उत्तर Aspose.Words for .NET API का उपयोग करने में है। इस ट्यूटोरियल के अंत तक आप एक Word फ़ाइल खोल सकेंगे, एक plain‑text SDT डाल सकेंगे, उसका टैग नाम सेट कर सकेंगे, उसे सामग्री से भर सकेंगे, और बिना किसी लटके हुए संसाधन के बदलाव सहेज सकेंगे।

## आवश्यकताएँ

* .NET 6.0 या बाद का संस्करण स्थापित हो।
* एक वैध Aspose.Words for .NET लाइसेंस (या आप मूल्यांकन संस्करण के साथ काम कर सकते हैं)।
* Visual Studio 2022 (या कोई भी IDE जो C# को सपोर्ट करता हो)।
* `input.docx` नामक इनपुट Word दस्तावेज़ को उस फ़ोल्डर में रखें जिसे आप कोड से संदर्भित कर सकते हैं।

## चरण 1: प्रोजेक्ट सेट अप करें और नेमस्पेस इम्पोर्ट करें

एक नया Console App प्रोजेक्ट बनाएं और Aspose.Words NuGet पैकेज जोड़ें:

```bash
dotnet new console -n WordSdtDemo
cd WordSdtDemo
dotnet add package Aspose.Words
```

फिर, `Program.cs` के शीर्ष पर आवश्यक `using` निर्देश जोड़ें:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Markup;
```

ये नेमस्पेस आपको `Document`, `DocumentBuilder`, और `StructuredDocumentTag` क्लास तक पहुँच देते हैं, जो **Word दस्तावेज़ को संशोधित करने** के लिए आवश्यक हैं।

## चरण 2: मौजूदा Word दस्तावेज़ लोड करें

पहला कार्य वह फ़ाइल लोड करना है जिसे आप संपादित करना चाहते हैं। यह चरण हर उस स्थिति में आवश्यक है जहाँ आप **Word दस्तावेज़** की सामग्री **संशोधित** करते हैं।

```csharp
// Load an existing Word document from disk
string inputPath = @"YOUR_DIRECTORY\input.docx";
Document doc = new Document(inputPath);
Console.WriteLine($"Loaded document: {inputPath}");
```

> **हम पहले दस्तावेज़ क्यों लोड करते हैं** – `Document` ऑब्जेक्ट मेमोरी में पूरे .docx पैकेज का प्रतिनिधित्व करता है। केवल लोड करने के बाद ही आप सुरक्षित रूप से नए नोड्स जैसे SDT डाल सकते हैं।

## चरण 3: StructuredDocumentTag (SDT) डालें और उसका टैग नाम सेट करें

अब हम मुख्य प्रश्न का उत्तर देते हैं: **sdt कैसे जोड़ें** और **टैग नाम कैसे सेट करें**। हम `DocumentBuilder.InsertStructuredDocumentTag` को `SdtType.PlainText` के साथ उपयोग करते हैं। दूसरा तर्क टैग नाम है, जिसे आप बाद में प्रोग्रामेटिक रूप से या Word के UI के माध्यम से संदर्भित कर सकते हैं।

```csharp
// Create a DocumentBuilder attached to the loaded document
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a plain‑text StructuredDocumentTag (content control) at the cursor position
// The second parameter ("MyTag") is the tag name we are setting.
StructuredDocumentTag sdt = builder.InsertStructuredDocumentTag(
    SdtType.PlainText, "MyTag");

// Confirm that the tag name has been set
Console.WriteLine($"Inserted SDT with tag name: {sdt.Tag}");
```

> **व्याख्या** – `InsertStructuredDocumentTag` एक `StructuredDocumentTag` इंस्टेंस लौटाता है। `"MyTag"` पास करके हम निर्माण के समय ही **टैग नाम सेट** करते हैं। यदि बाद में इसे बदलने की आवश्यकता हो, तो आप `sdt.Tag` को नया मान असाइन कर सकते हैं।

## चरण 4: नए बनाए गए टैग में टेक्स्ट लिखें

SDT बनने के बाद, आप आमतौर पर **टैग में टेक्स्ट लिखना** चाहते हैं ताकि अंतिम उपयोगकर्ता प्लेसहोल्डर या डिफ़ॉल्ट सामग्री देख सकें। `SetText` मेथड ठीक यही करता है।

```csharp
// Populate the SDT with sample content
sdt.SetText("Sample content");

// Optionally, you can also set the placeholder text that appears when the tag is empty
sdt.PlaceholderName = "Enter your text here";
Console.WriteLine("Text written to the SDT.");
```

> **SetText क्यों उपयोग करें** – सीधे `Text` प्रॉपर्टी को असाइन करने से पूरी नोड हाइरार्की बदल जाएगी। `SetText` कंटेंट कंट्रोल के अंदरूनी टेक्स्ट को सुरक्षित रूप से अपडेट करता है जबकि उसकी संरचना बनी रहती है।

## चरण 5: संशोधित दस्तावेज़ सहेजें

अंत में, बदलावों को नई फ़ाइल में सहेजें। यह **Word दस्तावेज़ संशोधित** करने की प्रक्रिया को पूरा करता है।

```csharp
// Define the output path
string outputPath = @"YOUR_DIRECTORY\output.docx";

// Save the document with the inserted content control
doc.Save(outputPath);
Console.WriteLine($"Document saved to: {outputPath}");
```

जब आप Microsoft Word में `output.docx` खोलेंगे, तो आपको **MyTag** लेबल वाला एक plain‑text कंटेंट कंट्रोल दिखेगा जिसमें “Sample content” टेक्स्ट होगा। इस कंट्रोल को मैन्युअल रूप से संपादित किया जा सकता है, और टैग नाम Word के डेवलपर टूल्स के माध्यम से उपलब्ध रहता है।

## पूर्ण स्रोत कोड

नीचे पूरा, स्व-निहित प्रोग्राम दिया गया है। इसे `Program.cs` में कॉपी करें और चलाएँ; कोई अतिरिक्त स्निपेट्स आवश्यक नहीं हैं।

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Markup;

namespace WordSdtDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // 1️⃣ Load the existing Word document
            string inputPath = @"YOUR_DIRECTORY\input.docx";
            Document doc = new Document(inputPath);
            Console.WriteLine($"Loaded document: {inputPath}");

            // 2️⃣ Create a DocumentBuilder to work with the document
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 3️⃣ Insert a plain‑text StructuredDocumentTag (SDT) and set its tag name
            StructuredDocumentTag sdt = builder.InsertStructuredDocumentTag(
                SdtType.PlainText, "MyTag");
            Console.WriteLine($"Inserted SDT with tag name: {sdt.Tag}");

            // 4️⃣ Write text to the tag (and optionally set a placeholder)
            sdt.SetText("Sample content");
            sdt.PlaceholderName = "Enter your text here";
            Console.WriteLine("Text written to the SDT.");

            // 5️⃣ Save the modified document
            string outputPath = @"YOUR_DIRECTORY\output.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to: {outputPath}");
        }
    }
}
```

### कंसोल में अपेक्षित आउटपुट

```
Loaded document: YOUR_DIRECTORY\input.docx
Inserted SDT with tag name: MyTag
Text written to the SDT.
Document saved to: YOUR_DIRECTORY\output.docx
```

### परिणामी Word फ़ाइल कैसी दिखती है

![Word दस्तावेज़ जिसमें MyTag नामक कंटेंट कंट्रोल और “Sample content” टेक्स्ट दिख रहा है](/images/word-sdt-example.png){: .img-fluid alt="Word दस्तावेज़ में टैग नाम सेट करने का उदाहरण"}

*यह स्क्रीनशॉट SDT को **टैग नाम** **MyTag** के साथ सेट दिखाता है और एम्बेडेड टेक्स्ट दिखाई देता है।*

## सामान्य विविधताएँ और किनारे के मामलों

| स्थिति | कैसे निपटें |
|-----------|------------------|
| **रिच‑टेक्स्ट SDT बनाएं** | `SdtType.RichText` का उपयोग `PlainText` के बजाय करें। |
| **इन्सर्शन के बाद अलग टैग नाम सेट करें** | `sdt.Tag = "NewTag";` – आप कभी भी टैग नाम को पुनः असाइन कर सकते हैं। |
| **एक विशिष्ट पैराग्राफ के अंदर SDT जोड़ें** | `InsertStructuredDocumentTag` कॉल करने से पहले बिल्डर का कर्सर (`builder.MoveToParagraph(index)`) ले जाएँ। |
| **एक ही दस्तावेज़ में कई SDTs** | प्रत्येक कंट्रोल के लिए चरण 3‑4 दोहराएँ; प्रत्येक का एक अनूठा टैग नाम हो सकता है। |
| **सुरक्षित दस्तावेज़ों के साथ काम करना** | SDT डालने से पहले सुनिश्चित करें कि दस्तावेज़ अनप्रोटेक्टेड है (`doc.Unprotect()`)। |

## मजबूत Word ऑटोमेशन के लिए प्रो टिप्स

* **जल्दी लाइसेंस प्राप्त करें** – `Main` की शुरुआत में `Aspose.Words.License license = new Aspose.Words.License(); license.SetLicense("Aspose.Words.lic");` कॉल करें ताकि मूल्यांकन वॉटरमार्क न दिखें।
* **ऑब्जेक्ट्स को डिस्पोज़ करें** – यदि आप .NET Framework टार्गेट कर रहे हैं तो `Document` को `using` ब्लॉक में रखें ताकि फ़ाइल हैंडल रिलीज़ हो सके।
* **टैग की मौजूदगी सत्यापित करें** – बाद में दस्तावेज़ पढ़ते समय, टैग को `Tag` प्रॉपर्टी से खोजने के लिए `doc.GetChildNodes(NodeType.StructuredDocumentTag, true)` उपयोग करें।
* **परफॉर्मेंस** – बड़े दस्तावेज़ों के लिए, केवल आवश्यक सेक्शन `LoadOptions` के साथ `LoadFormat.Docx` और `LoadFormat.Auto` का उपयोग करके लोड करें।

## निष्कर्ष

अब आप जानते हैं कि C# का उपयोग करके **टैग नाम कैसे सेट करें**, **कंटेंट कंट्रोल कैसे बनाएं**, **टैग में टेक्स्ट कैसे लिखें**, और **Word दस्तावेज़ को कैसे संशोधित करें**। पूरा उदाहरण **sdt कैसे जोड़ें** और बदलावों को सुरक्षित रूप से सहेजने का मानक पैटर्न दर्शाता है।

अब आगे

## अब आपको आगे क्या सीखना चाहिए?

निम्नलिखित ट्यूटोरियल्स उन निकट संबंधी विषयों को कवर करते हैं जो इस गाइड में दिखाए गए तकनीकों पर आधारित हैं। प्रत्येक संसाधन में पूर्ण कार्यशील कोड उदाहरण और चरण‑दर‑चरण व्याख्याएँ शामिल हैं, जो आपको अतिरिक्त API फीचर्स में महारत हासिल करने और अपने प्रोजेक्ट्स में वैकल्पिक कार्यान्वयन दृष्टिकोणों का पता लगाने में मदद करेंगे।

- [Aspose.Words for .NET में Document Builder का उपयोग करके कंटेंट जोड़ें](/words/english/net/add-content-using-document-builder/)
- [Word दस्तावेज़ - कंटेंट कैसे हटाएँ](/words/english/net/remove-content/)
- [Aspose.Words के साथ Word दस्तावेज़ बनाएं – चरण‑दर‑चरण गाइड](/words/english/net/enable-opentype-features/create-word-document-with-aspose-words-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}