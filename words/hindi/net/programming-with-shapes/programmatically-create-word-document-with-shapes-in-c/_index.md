---
category: general
date: 2026-11-22
description: C# में प्रोग्रामेटिक रूप से Word दस्तावेज़ बनाएं, आयताकार आकार डालें,
  कई आकार डालें, और Aspose.Words का उपयोग करके आकारों को Word में लिखें।
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- programmatically create word document
- insert rectangle shape
- insert multiple shapes
- write shapes to word
language: hi
lastmod: 2026-11-22
og_description: C# में प्रोग्रामेटिकली Word दस्तावेज़ बनाएं, आयताकार आकार डालें, कई
  आकार जोड़ें, और Aspose.Words का उपयोग करके आकारों को Word में लिखें।
og_image_alt: Screenshot of a Word document showing a rectangle and an ellipse grouped
  together
og_title: C# में प्रोग्रामेटिक रूप से आकारों के साथ Word दस्तावेज़ बनाना
schemas:
- author: Aspose
  dateModified: '2026-11-22'
  description: Programmatically create Word document in C# and insert rectangle shape,
    insert multiple shapes, and write shapes to Word using Aspose.Words.
  headline: Programmatically create Word document with shapes in C#
  type: TechArticle
- description: Programmatically create Word document in C# and insert rectangle shape,
    insert multiple shapes, and write shapes to Word using Aspose.Words.
  name: Programmatically create Word document with shapes in C#
  steps:
  - name: '**Initialize** a new `Document` and a `DocumentBuilder`.'
    text: '**Initialize** a new `Document` and a `DocumentBuilder`.'
  - name: '**Insert multiple shapes** (a rectangle and an ellipse) and place them
      inside a `GroupShape`.'
    text: '**Insert multiple shapes** (a rectangle and an ellipse) and place them
      inside a `GroupShape`.'
  - name: '**Write shapes to Word** by saving the `Document` to a `.docx` file.'
    text: '**Write shapes to Word** by saving the `Document` to a `.docx` file.'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
- shapes
title: C# में प्रोग्रामेटिक रूप से शैप्स के साथ Word दस्तावेज़ बनाएं
url: /hi/net/programming-with-shapes/programmatically-create-word-document-with-shapes-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C# में आकारों के साथ Word दस्तावेज़ को प्रोग्रामेटिकली बनाना

यदि आपको कस्टम ग्राफिक्स वाला **Word दस्तावेज़ को प्रोग्रामेटिकली बनाना** है, तो यह गाइड आपको Aspose.Words for .NET के साथ यह करने का तरीका दिखाएगा। आप एक आयत आकार डालना, अतिरिक्त आकार जोड़ना, उन्हें समूहित करना, और अंत में आकारों को Word में लिखना सीखेंगे—सभी कुछ ही C# लाइनों में।

ग्राफिक्स के साथ Word फ़ाइल बनाना अब मैन्युअल एडिटिंग या मैक्रो स्क्रिप्ट्स की आवश्यकता नहीं रखता। इस ट्यूटोरियल के अंत तक आपके पास एक पुन: उपयोग योग्य मेथड होगा जो एक `.docx` फ़ाइल उत्पन्न करता है जिसमें एक आयत और एक दीर्घवृत्त समूहित रूप में होते हैं, जो आगे की प्रोसेसिंग या रिपोर्टिंग के लिए तैयार है।

## आपको क्या चाहिए

- .NET 6.0 या बाद का (कोड .NET Framework 4.6+ के साथ भी काम करता है)
- Aspose.Words for .NET (NuGet पैकेज `Aspose.Words`)
- Visual Studio 2022 जैसे IDE (कोई भी एडिटर जो C# को कंपाइल कर सके, ठीक है)

> **Pro tip:** कोडिंग शुरू करने से पहले पैकेज को CLI कमांड `dotnet add package Aspose.Words` से इंस्टॉल करें।

## Word दस्तावेज़ को प्रोग्रामेटिकली बनाना – अवलोकन

समग्र प्रवाह तीन तार्किक चरणों में विभाजित है:

1. **Initialize** एक नया `Document` और एक `DocumentBuilder` बनाएं।  
2. **Insert multiple shapes** (एक आयत और एक दीर्घवृत्त) को `GroupShape` के अंदर रखें।  
3. **Write shapes to Word** `Document` को `.docx` फ़ाइल में सेव करके।

प्रत्येक चरण नीचे एक समर्पित स्टेप में संलग्न है, ताकि आप कोड को सीधे अपने प्रोजेक्ट में कॉपी‑पेस्ट कर सकें।

![Programmatically create Word document with grouped shapes](grouped-shapes.png){: .align-center alt="Programmatically create Word document with grouped shapes"}

## चरण 1: दस्तावेज़ और बिल्डर को इनिशियलाइज़ करें

`Document` क्लास पूरे Word फ़ाइल का प्रतिनिधित्व करती है, जबकि `DocumentBuilder` सामग्री जोड़ने के लिए एक फ्लुएंट API प्रदान करता है।

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create a new empty document
Document document = new Document();

// Initialize a DocumentBuilder for the document
DocumentBuilder builder = new DocumentBuilder(document);
```

*Why this matters:* `Document` को पहले बनाने से आपको एक साफ़ कैनवास मिलता है। `DocumentBuilder` वर्तमान इंसर्शन पॉइंट को ट्रैक करता है, जो बाद में आकारों को पैराग्राफ हायरार्की से जोड़ते समय आवश्यक होता है।

## चरण 2: ग्रुप शेप कंटेनर डालें

`GroupShape` आपको कई व्यक्तिगत आकारों को एक इकाई के रूप में ट्रीट करने देता है। यह तब उपयोगी होता है जब आप उन्हें साथ में मूव या रिसाइज़ करना चाहते हैं।

```csharp
// Insert a group shape container at the current cursor position
GroupShape groupShape = builder.InsertGroupShape();
```

*Explanation:* `InsertGroupShape` एक खाली कंटेनर डालता है और स्वचालित रूप से इसे वर्तमान आकार बना देता है। सभी बाद के आकार इंसर्शन इस कंटेनर में जोड़ दिए जाएंगे जब तक आप समूह को बंद नहीं करते।

## आयत आकार डालें

अब हम पहला ग्राफिक—एक आयत—जोड़ते हैं। यह **insert rectangle shape** आवश्यकता को पूरा करता है।

```csharp
// Insert a rectangle shape (width: 100 pt, height: 50 pt)
builder.InsertShape(ShapeType.Rectangle, 100, 50);
```

आयत समूह के फ़ॉर्मेटिंग कॉन्टेक्स्ट को इनहेरिट करती है, इसलिए यह `GroupShape` के अंदर दिखाई देती है। आप बाद में लाइन रंग, फ़िल या टेक्स्ट भी सेट कर सकते हैं यदि आवश्यक हो।

## कई आकार डालें

**insert multiple shapes** क्षमता दिखाने के लिए, हम आयत के बाद एक दीर्घवृत्त जोड़ते हैं। आप समूह को बंद करने से पहले किसी भी संख्या में आकार (जैसे, त्रिकोण, सितारे) जोड़ते रह सकते हैं।

```csharp
// Insert an ellipse shape (width: 80 pt, height: 40 pt)
builder.InsertShape(ShapeType.Ellipse, 80, 40);
```

इस बिंदु पर समूह में दो अलग-अलग आकार हैं: एक आयत और एक दीर्घवृत्त। क्योंकि वे एक ही पैरेंट साझा करते हैं, आप उन्हें एक इकाई के रूप में मूव कर सकते हैं।

## चरण 3: ग्रुप शेप को पैराग्राफ हायरार्की से जोड़ें

Word दस्तावेज़ सामग्री को पैराग्राफ ट्री में स्टोर करते हैं। अंतिम फ़ाइल में समूह को दिखाने के लिए, हमें इसे वर्तमान पैराग्राफ से जोड़ना होगा।

```csharp
// Append the group shape to the current paragraph so it becomes part of the document flow
groupShape.AppendChild(builder.CurrentParagraph);
```

*Why this step is required:* यदि समूह को पैराग्राफ में जोड़ नहींते, तो आकार केवल मेमोरी में रहते हैं और दस्तावेज़ सेव करते समय बाहर हो जाते हैं।

## चरण 4: दस्तावेज़ को सेव करें – आकारों को Word में लिखें

अंत में, हम इन‑मेमोरी `Document` को डिस्क पर सहेजते हैं। यह **write shapes to word** लक्ष्य को पूरा करता है।

```csharp
// Define the output path (adjust the folder as needed)
string outputPath = Path.Combine(Environment.CurrentDirectory, "GroupShape.docx");

// Save the document in DOCX format
document.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

जब आप Microsoft Word में `GroupShape.docx` खोलेंगे, तो आपको एक आयत और एक दीर्घवृत्त समूहित रूप में दिखेंगे, बिल्कुल उसी तरह जैसा कोड ने डाला था।

### अपेक्षित आउटपुट

- एक फ़ाइल जिसका नाम **GroupShape.docx** है, जो प्रोजेक्ट के आउटपुट फ़ोल्डर में स्थित है।
- Word फ़ाइल के अंदर: एक एकल पैराग्राफ जिसमें एक समूहित आयत (100 pt × 50 pt) और एक दीर्घवृत्त (80 pt × 40 pt) शामिल है। किसी भी आकार का चयन करने पर पूरी समूह चयनित हो जाएगी।

## सामान्य किनारे के मामलों को संभालना

| **स्थिति** | **सिफारिश** |
|-----------|----------------|
| **विभिन्न DPI या पेज आकार** | `builder.PageSetup.PaperSize` को आकार डालने से पहले स्पष्ट रूप से सेट करें ताकि अप्रत्याशित स्केलिंग से बचा जा सके। |
| **आकारों को सटीक रूप से पोजिशन करने की आवश्यकता** | इंसर्शन पॉइंट को मूव करने के लिए `builder.MoveTo` का उपयोग करें, फिर `groupShape.Left` और `groupShape.Top` प्रॉपर्टीज़ सेट करें (मान पॉइंट्स में होते हैं)। |

## अब आप क्या सीखें?

निम्नलिखित ट्यूटोरियल्स उन निकट संबंधित विषयों को कवर करते हैं जो इस गाइड में दिखाए गए तकनीकों पर आधारित हैं। प्रत्येक संसाधन में पूर्ण कार्यशील कोड उदाहरण और चरण-दर-चरण व्याख्याएँ शामिल हैं जो आपको अतिरिक्त API फीचर्स में महारत हासिल करने और अपने प्रोजेक्ट में वैकल्पिक इम्प्लीमेंटेशन एप्रोच को एक्सप्लोर करने में मदद करेंगे।

- [Word दस्तावेज़ बनाएं – आयत आकार और शैडो डालें C# में](/words/english/net/programming-with-shapes/create-word-document-insert-rectangle-shape-shadow-in-c/)
- [Word दस्तावेज़ को प्रोग्रामेटिकली बनाएं और C# में आकारों को समूहित करें](/words/english/net/programming-with-shapes/create-word-document-programmatically-and-group-shapes-in-c/)
- [C# में ग्रुप शेप के साथ Word दस्तावेज़ को प्रोग्रामेटिकली बनाएं](/words/english/net/programming-with-shapes/programmatically-create-a-word-document-with-a-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}