---
category: general
date: 2026-08-10
description: C# का उपयोग करके Word में आयताकार आकार डालें। सीखें कि कैसे आकार को छुपाएँ,
  Word में आकार को छुपाएँ, और Aspose.Words के साथ छुपा हुआ आकार बनाएँ।
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert rectangle shape
- how to hide shape
- hide shape in word
- create hidden shape
language: hi
lastmod: 2026-08-10
og_description: C# का उपयोग करके Word में आयताकार आकार डालें। यह ट्यूटोरियल बताता
  है कि आकार को कैसे छुपाएँ, Word में आकार को कैसे छुपाएँ, और पूर्ण कोड उदाहरणों के
  साथ छुपा हुआ आकार कैसे बनाएँ।
og_image_alt: Screenshot showing a hidden rectangle shape inserted into a Word document
  using C#
og_title: C# के साथ Word में आयताकार आकार डालें – चरण‑दर‑चरण गाइड
schemas:
- author: Aspose
  dateModified: '2026-08-10'
  description: Insert rectangle shape in Word using C#. Learn how to hide shape, hide
    shape in Word, and create hidden shape with Aspose.Words.
  headline: Insert rectangle shape in Word with C# – complete guide
  type: TechArticle
- description: Insert rectangle shape in Word using C#. Learn how to hide shape, hide
    shape in Word, and create hidden shape with Aspose.Words.
  name: Insert rectangle shape in Word with C# – complete guide
  steps:
  - name: Can I hide only the outline but keep the fill visible?
    text: Yes. Instead of setting `Hidden = true`, you can set `rectangle.LineFormat.Visible
      = false` to hide the border while keeping the fill color. This is a variation
      of **how to hide shape** that preserves part of the visual appearance.
  - name: Does the hidden flag work in older Word versions (2003, 2007)?
    text: The hidden attribute is part of the Open XML specification introduced with
      Word 2007. Documents saved in the older binary `.doc` format will not preserve
      the flag. To support legacy formats, save the document as `.docx` and, if needed,
      convert it later using Aspose.Words’ `SaveFormat.Doc`.
  - name: What if I need to hide multiple shapes at once?
    text: Iterate over the `Document.GetChildNodes(NodeType.Shape, true)` collection
      and set `Hidden = true` on each shape that meets your criteria (e.g., a specific
      `ShapeType` or a custom `AlternativeText` value).
  - name: Is there a performance impact when hiding shapes?
    text: The hidden flag adds a tiny XML attribute; it does not affect rendering
      speed. However, a very large number of hidden objects can increase file size
      marginally. Remove shapes you never need to keep the document lean.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: C# के साथ Word में आयताकार आकार डालें – पूर्ण गाइड
url: /hi/net/programming-with-shapes/insert-rectangle-shape-in-word-with-c-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C# के साथ Word में आयताकार आकार डालें – पूर्ण गाइड

यदि आपको C# का उपयोग करके Word दस्तावेज़ में **आयताकार आकार डालना** है, तो यह गाइड आपको सटीक चरण दिखाता है। आप यह भी सीखेंगे **आकार को कैसे छुपाएँ** ताकि वह अंतिम फ़ाइल में न दिखे, जो सामान्य प्रश्न **hide shape in Word** का उत्तर देता है और प्रोग्रामेटिक रूप से **create hidden shape** कैसे बनाएं, यह दर्शाता है।

यह ट्यूटोरियल Aspose.Words SDK को सेटअप करने से लेकर यह सत्यापित करने तक सब कुछ कवर करता है कि आकार छुपा हुआ है। लेख के अंत तक आपके पास एक पुन: उपयोग योग्य कोड स्निपेट होगा जिसे आप किसी भी .NET प्रोजेक्ट में डाल सकते हैं।

## आवश्यकताएँ

- .NET 6.0 या बाद का संस्करण स्थापित हो (कोड .NET Framework 4.6+ के साथ भी काम करता है)
- Aspose.Words for .NET का वैध लाइसेंस या एक अस्थायी इवैल्यूएशन कुंजी
- Visual Studio 2022 (या कोई भी IDE जो C# को सपोर्ट करता हो)
- C# सिंटैक्स और Word फ़ाइलों के Document Object Model (DOM) की बुनियादी समझ

`Aspose.Words` के अलावा कोई अतिरिक्त NuGet पैकेज आवश्यक नहीं है।

## चरण 1: एक नया खाली दस्तावेज़ और DocumentBuilder बनाएं

पहला ऑपरेशन `Document` ऑब्जेक्ट को इंस्टैंशिएट करना है। `DocumentBuilder` आकार, पैराग्राफ और टेबल जैसी सामग्री डालने के लिए एक सुविधाजनक API प्रदान करता है।

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create an empty Word document.
Document document = new Document();

// DocumentBuilder lets you add elements to the document.
DocumentBuilder builder = new DocumentBuilder(document);
```

**Why this matters:** `Document` पूरे .docx फ़ाइल का प्रतिनिधित्व करता है, जबकि `DocumentBuilder` एक कर्सर बनाए रखता है जो ट्रैक करता है कि अगला तत्व कहाँ रखा जाएगा। दोनों ऑब्जेक्ट्स को इनिशियलाइज़ करना किसी भी Word ऑटोमेशन टास्क की नींव है।

## चरण 2: आयताकार आकार डालें

अब आप आयताकार आकार डालते हैं। `InsertShape` मेथड को आकार का प्रकार और उसके आयाम पॉइंट्स में चाहिए (1 पॉइंट ≈ 1/72 इंच)। **200 × 100 पॉइंट्स** का आकार लगभग 2.78 × 1.39 इंच का आयत बनाता है।

```csharp
// Insert a rectangle of 200x100 points.
Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 200, 100);
```

**Why this matters:** आपको प्राप्त `Shape` ऑब्जेक्ट पूरी तरह कॉन्फ़िगर करने योग्य है—रंग, बॉर्डर, टेक्स्ट और विज़िबिलिटी सभी को दस्तावेज़ सहेजने से पहले बदला जा सकता है।

## चरण 3: आकार को छुपाएँ

आयत को प्रदर्शित या प्रिंट होने से रोकने के लिए, उसकी `Hidden` प्रॉपर्टी को `true` सेट करें। यह प्रॉपर्टी सीधे Word के “Hidden” एट्रिब्यूट से मैप होती है, जिसे Word व्यू और प्रिंट मोड दोनों में सम्मानित करता है।

```csharp
// Hide the shape so it never appears.
rectangle.Hidden = true;
```

**Why this matters:** `Hidden` सेट करना **hide shape in Word** का मानक तरीका है, बिना उसे दस्तावेज़ संरचना से हटाए। आकार कोड के लिए उपलब्ध रहता है, जिससे बाद में कंडीशनल फ़ॉर्मेटिंग या डेटा‑ड्रिवेन विज़िबिलिटी टॉगल जैसी मैनिपुलेशन संभव होती है।

## चरण 4: दस्तावेज़ सहेजें

अंत में, दस्तावेज़ को डिस्क पर सहेजें। कोई भी फ़ोल्डर चुनें; उदाहरण में एक प्लेसहोल्डर पाथ उपयोग किया गया है जिसे आपको वास्तविक पाथ से बदलना चाहिए।

```csharp
// Save the document with the hidden rectangle.
document.Save(@"C:\Temp\HiddenShape.docx");
```

**Why this matters:** सहेजने से फ़ाइल अंतिम रूप लेती है और छुपे हुए फ़्लैग को अंतर्निहित Open XML में लिखा जाता है। जब आप Microsoft Word में दस्तावेज़ खोलते हैं, तो आयत अदृश्य रहेगा, जिससे पुष्टि होती है कि आपने सफलतापूर्वक **created hidden shape** बना लिया है।

## चरण 5: छुपे हुए आकार की पुष्टि करें

जनरेट किए गए `HiddenShape.docx` को Microsoft Word में खोलें:

1. **File → Options → Display** पर जाएँ और सुनिश्चित करें कि *“Show hidden text”* **अनचेक्ड** है।  
2. आयत किसी भी पेज पर दिखाई नहीं देनी चाहिए।  
3. दोबारा जांचने के लिए *“Show hidden text”* को एनेबल करें; आयत हल्की डॉटेड आउटलाइन के साथ दिखाई देगी, जिससे पता चलता है कि आकार मौजूद है लेकिन छुपा हुआ है।

यदि आयत अभी भी दिखाई दे रही है, तो यह सत्यापित करें कि आपने `Hidden = true` सेट करने के बाद फ़ाइल सहेजी है और आप सही फ़ाइल खोल रहे हैं।

## पूर्ण चलाने योग्य उदाहरण

नीचे पूरा प्रोग्राम दिया गया है जिसे आप कॉपी, पेस्ट और सीधे चला सकते हैं।

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1: Create a new blank document and a DocumentBuilder.
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Step 2: Insert a rectangle shape of 200x100 points.
        Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 200, 100);

        // Step 3: Hide the shape so it does not appear when viewed or printed.
        rectangle.Hidden = true;

        // Step 4: Save the document with the hidden shape.
        string outputPath = @"C:\Temp\HiddenShape.docx";
        document.Save(outputPath);

        Console.WriteLine($"Document saved to {outputPath}");
        Console.WriteLine("Open the file in Word to verify that the rectangle is hidden.");
    }
}
```

**Expected output:** कंसोल फ़ाइल पाथ और एक छोटा रिमाइंडर प्रिंट करेगा। जब फ़ाइल Word में खोली जाएगी, तो आयत अदृश्य रहेगा जब तक कि हिडन टेक्स्ट एनेबल न किया गया हो।

## सामान्य प्रश्न और किनारे के मामले

### क्या मैं केवल आउटलाइन को छुपा सकता हूँ जबकि फ़िल दिखा सकता हूँ?

हाँ। `Hidden = true` सेट करने के बजाय, आप `rectangle.LineFormat.Visible = false` सेट कर सकते हैं ताकि बॉर्डर छुपे लेकिन फ़िल रंग बना रहे। यह **how to hide shape** का एक वैरिएशन है जो दृश्य का कुछ हिस्सा बनाए रखता है।

### क्या हिडन फ़्लैग पुराने Word संस्करणों (2003, 2007) में काम करता है?

हिडन एट्रिब्यूट Open XML स्पेसिफिकेशन का हिस्सा है जो Word 2007 के साथ पेश किया गया था। पुराने बाइनरी `.doc` फ़ॉर्मेट में सहेजी गई फ़ाइलें इस फ़्लैग को नहीं रखतीं। लेगेसी फ़ॉर्मेट को सपोर्ट करने के लिए, दस्तावेज़ को `.docx` के रूप में सहेजें और यदि आवश्यक हो तो बाद में Aspose.Words के `SaveFormat.Doc` का उपयोग करके कनवर्ट करें।

### अगर मुझे एक साथ कई आकार छुपाने हों तो क्या करें?

`Document.GetChildNodes(NodeType.Shape, true)` कलेक्शन पर इटरेट करें और प्रत्येक ऐसे आकार पर `Hidden = true` सेट करें जो आपके मानदंडों को पूरा करता हो (जैसे, विशिष्ट `ShapeType` या कस्टम `AlternativeText` मान)।

```csharp
foreach (Shape shp in document.GetChildNodes(NodeType.Shape, true))
{
    if (shp.AlternativeText == "HideMe")
        shp.Hidden = true;
}
```

### आकार छुपाने से प्रदर्शन पर कोई असर पड़ता है क्या?

हिडन फ़्लैग एक छोटा XML एट्रिब्यूट जोड़ता है; यह रेंडरिंग स्पीड को प्रभावित नहीं करता। हालांकि, बहुत बड़ी संख्या में छुपे हुए ऑब्जेक्ट्स फ़ाइल साइज को थोड़ा बढ़ा सकते हैं। अनावश्यक आकारों को हटाएँ ताकि दस्तावेज़ हल्का रहे।

## टिप्स और सर्वोत्तम प्रैक्टिसेज

- **Give the shape a meaningful name** `rectangle.Name = "MyHiddenRectangle"` का उपयोग करके सेट करें; यह बाद में DOM में आकार खोजते समय मदद करता है।  
- **Set `AlternativeText`** को एक कस्टम टैग (जैसे, `"HiddenShape"`) पर सेट करें। इससे आप आकार को उसके इंडेक्स पर निर्भर हुए बिना ढूँढ सकते हैं।  
- **Wrap the code in a try‑catch block** ताकि लाइसेंसिंग एरर या I/O एक्सेप्शन को सुगमता से हैंडल किया जा सके।  
- **Dispose of the Document** सहेजने के बाद यदि आप लूप में कई फ़ाइलें प्रोसेस कर रहे हैं तो अनमैनेज्ड रिसोर्सेज़ को फ्री करने के लिए: `document.Dispose();`।

## निष्कर्ष

अब आप जानते हैं कि **C# के साथ Word दस्तावेज़ में आयताकार आकार कैसे डालें**, **Word में आकार कैसे छुपाएँ**, और **छुपा हुआ आकार कैसे बनाएं** जो दस्तावेज़ संरचना का हिस्सा बना रहता है लेकिन अंतिम उपयोगकर्ता को अदृश्य रहता है। पूर्ण, चलाने योग्य उदाहरण पूरे वर्कफ़्लो को दर्शाता है, दस्तावेज़ निर्माण से लेकर सत्यापन तक।

आगे आप **how to hide shape** को यूज़र इनपुट के आधार पर एक्सप्लोर कर सकते हैं, या डायनामिक डॉक्यूमेंट जेनरेशन के लिए हिडन शैप्स को कंटेंट कंट्रोल्स के साथ संयोजित कर सकते हैं। आप इसी तकनीक को अन्य शैप टाइप्स जैसे एलिप्स, एरो या कस्टम ड्रॉइंग्स पर भी लागू कर सकते हैं।

विभिन्न आयाम, रंग और विज़िबिलिटी सेटिंग्स के साथ प्रयोग करने में संकोच न करें। यदि कोई समस्या आती है, तो ऊपर दिए गए चरणों को दोबारा देखें या गहरी API जानकारी के लिए Aspose.Words दस्तावेज़ देखें। Happy coding!

## अगला आप क्या सीखें?

निम्नलिखित ट्यूटोरियल्स उन विषयों को कवर करते हैं जो इस गाइड में दिखाए गए तकनीकों पर आधारित हैं। प्रत्येक संसाधन में पूर्ण कार्यशील कोड उदाहरण और चरण‑दर‑चरण व्याख्याएँ शामिल हैं, जिससे आप अतिरिक्त API फीचर्स में महारत हासिल कर सकें और अपने प्रोजेक्ट्स में वैकल्पिक इम्प्लीमेंटेशन अप्रोचेज़ का अन्वेषण कर सकें।

- [C# का उपयोग करके Word में आयताकार आकार बनाएं – चरण‑दर‑चरण गाइड](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Aspose.Words के साथ Word में आयताकार आकार बनाएं – चरण‑दर‑चरण गाइड](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)
- [Aspose.Words Shape Shadow ट्यूटोरियल – C# में Word Shape में शैडो जोड़ें](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}