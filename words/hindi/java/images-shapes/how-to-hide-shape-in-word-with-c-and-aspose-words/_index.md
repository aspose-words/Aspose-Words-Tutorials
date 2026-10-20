---
category: general
date: 2026-09-11
description: C# का उपयोग करके Word में आकृति को छिपाना सीखें। यह गाइड यह भी दिखाता
  है कि कैसे आयताकार आकृति डालें और Aspose.Words के साथ Word दस्तावेज़ में आकृति डालें।
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to hide shape in word
- insert rectangle shape
- insert shape into word document
language: hi
lastmod: 2026-09-11
og_description: C# और Aspose.Words का उपयोग करके Word में आकृति को कैसे छिपाएँ। आयताकार
  आकृति डालने और Word दस्तावेज़ में आकृतियों को प्रबंधित करने के लिए चरण‑दर‑चरण ट्यूटोरियल
  का पालन करें।
og_image_alt: Screenshot showing how to hide shape in Word document using C#
og_title: Word में आकृति को कैसे छिपाएँ – पूर्ण C# गाइड
schemas:
- author: Aspose
  dateModified: '2026-09-11'
  description: Learn how to hide shape in Word using C#. This guide also shows how
    to insert rectangle shape and insert shape into Word document with Aspose.Words.
  headline: How to hide shape in Word with C# and Aspose.Words
  type: TechArticle
- description: Learn how to hide shape in Word using C#. This guide also shows how
    to insert rectangle shape and insert shape into Word document with Aspose.Words.
  name: How to hide shape in Word with C# and Aspose.Words
  steps:
  - name: Explanation of each step
    text: 1. **Create a new document** – `Document` represents the Word file in memory.
      `DocumentBuilder` provides a fluent API for inserting content. 2. **Insert rectangle
      shape** – `InsertShape` creates a drawing object of type `Rectangle`. The dimensions
      are expressed in points (1 pt ≈ 1/72 in). This satis
  - name: Expected result
    text: 'Open `output.docx` in Microsoft Word:'
  - name: Manually adding the hidden attribute (fallback)
    text: '```csharp // Fallback for Aspose.Words versions prior to 24.10 Shape shape
      = builder.InsertShape(ShapeType.Rectangle, 100, 50); shape.FillColor = System.Drawing.Color.LightGray;'
  type: HowTo
- questions:
  - answer: No. Hidden shapes are ignored by the layout engine, so they do not consume
      space. This is useful for placeholder content that should not affect page breaks.
    question: Does hiding a shape affect pagination?
  - answer: Yes. The same `Hidden` property works on shapes located anywhere in the
      document tree, including headers, footers, and even inside tables.
    question: Can I hide a shape that is part of a header or footer?
  - answer: Iterate over the `Document.GetChildNodes(NodeType.Shape, true)` collection
      and set `Hidden = true` for each target shape. ```csharp foreach (Shape s in
      doc.GetChildNodes(NodeType.Shape, true)) { if (s.ShapeType == ShapeType.Rectangle)
      s.Hidden = true; } ```
    question: What if I need to hide multiple shapes at once?
  - answer: 'When converting to PDF, hidden shapes are omitted by default, matching
      Word’s rendering behavior. If you need them in the PDF, you must unhide them
      before conversion. ## Tips and pitfalls * **Pro tip:** Set `shape.WrapType =
      WrapType.None` before hiding if you later plan to unhide the shape without '
    question: Is the hidden attribute preserved when converting to PDF?
  type: FAQPage
tags:
- Aspose.Words
- C#
- Word automation
title: C# और Aspose.Words के साथ Word में आकार को कैसे छुपाएँ
url: /hi/java/images-shapes/how-to-hide-shape-in-word-with-c-and-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C# और Aspose.Words के साथ Word में शैप को छिपाने का तरीका

यदि आपको Word में शैप को छिपाना है जबकि शैप दस्तावेज़ संरचना में बना रहे, यह ट्यूटोरियल आपको ठीक-ठीक दिखाता है। Aspose.Words for .NET का उपयोग करके आप एक rectangle शैप डाल सकते हैं, उसे छिपा सकते हैं, और बाद में प्रोसेसिंग के लिए उसकी स्थिति को बरकरार रख सकते हैं।

Word ऑटोमेशन अक्सर शैप्स पर सूक्ष्म नियंत्रण की आवश्यकता रखता है—चाहे आप टेम्प्लेट बना रहे हों, रिपोर्ट तैयार कर रहे हों, या दस्तावेज़-एडिटिंग सेवा बना रहे हों। इस गाइड के अंत तक आप सक्षम होंगे:

* Word दस्तावेज़ में एक rectangle शैप डालें (`insert rectangle shape`).
* किसी भी शैप को हटाए बिना छिपाएँ (`how to hide shape in word`).
* परिणाम को सहेजें और सत्यापित करें कि छिपा हुआ शैप रेंडर किए गए दृश्य में नहीं दिखता (`insert shape into word document`).

यह उदाहरण Aspose.Words 24.10 या बाद के संस्करणों के साथ काम करता है और .NET 6.0+ को लक्षित करता है, लेकिन अवधारणाएँ पहले के संस्करणों पर भी लागू होती हैं।

## आवश्यकताएँ

* **Aspose.Words for .NET** ≥ 24.10. आप Aspose वेबसाइट से एक मुफ्त अस्थायी लाइसेंस प्राप्त कर सकते हैं।
* **.NET SDK** 6.0 या उससे नया आपके मशीन पर स्थापित होना चाहिए।
* एक विकास वातावरण जैसे Visual Studio 2022, VS Code, या Rider।
* C# और Word Open XML अवधारणा की बुनियादी परिचितता (वैकल्पिक लेकिन उपयोगी)।

## Aspose.Words के साथ Word में शैप को छिपाने का तरीका

नीचे एक पूर्ण, चलाने योग्य प्रोग्राम दिया गया है जो पूरे वर्कफ़्लो को दर्शाता है—एक दस्तावेज़ बनाने से लेकर rectangle शैप डालने और अंत में उसे छिपाने तक।

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class HideShapeDemo
{
    static void Main()
    {
        // Step 1: Create a new blank document and a DocumentBuilder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Insert a rectangle shape (100 × 50 points) at the current cursor position.
        Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 100, 50);
        // Optional: give the shape a visible fill so you can see it before hiding.
        rectangle.FillColor = System.Drawing.Color.LightBlue;

        // Step 3: Hide the shape without removing it from the document.
        // The Hidden property is available starting with Aspose.Words 24.10.
        rectangle.Hidden = true;

        // Step 4: Save the document to disk.
        string outputPath = "output.docx";
        doc.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}. The rectangle shape is hidden.");
    }
}
```

### प्रत्येक चरण की व्याख्या

1. **Create a new document** – `Document` मेमोरी में Word फ़ाइल का प्रतिनिधित्व करता है। `DocumentBuilder` सामग्री डालने के लिए एक fluent API प्रदान करता है।
2. **Insert rectangle shape** – `InsertShape` `Rectangle` प्रकार का एक ड्रॉइंग ऑब्जेक्ट बनाता है। आयाम पॉइंट्स में व्यक्त किए जाते हैं (1 pt ≈ 1/72 in)। यह `insert rectangle shape` आवश्यकता को पूरा करता है।
3. **Hide the shape** – `Shape.Hidden = true` सेट करने से शैप Word मार्कअप (`<w:hidden/>`) में छिपा हुआ चिह्नित हो जाता है। शैप दस्तावेज़ ट्री का हिस्सा बना रहता है, इसलिए आप बाद में इसे अनहाइड कर सकते हैं या प्रोग्रामेटिकली रेफ़रेंस कर सकते हैं। यह `how to hide shape in word` का मूल है।
4. **Save the file** – दस्तावेज़ `output.docx` में लिखा जाता है। जब Microsoft Word में खोला जाता है, तो rectangle दिखाई नहीं देगा, लेकिन यह XML में मौजूद रहेगा और ZIP व्यूअर या Open XML SDK से निरीक्षण किया जा सकता है।

### अपेक्षित परिणाम

`output.docx` को Microsoft Word में खोलें:

* दस्तावेज़ खाली दिखाई देता है—कोई दृश्य शैप नहीं।
* यदि आप अंतर्निहित XML (`word/document.xml`) की जांच करते हैं तो आपको `<w:pict>` तत्व के साथ `<w:hidden/>` एट्रिब्यूट मिलेगा, जो पुष्टि करता है कि शैप मौजूद है लेकिन छिपा हुआ है।

```xml
<w:pict>
  <v:shape id="Shape0" style="position:absolute; ...">
    <v:fillcolor>#ADD8E6</v:fillcolor>
    <w:hidden/>
  </v:shape>
</w:pict>
```

छिपे हुए शैप को `Hidden = false` सेट करके और दस्तावेज़ को पुनः सहेजकर फिर से दृश्यमान बनाया जा सकता है।

## Word दस्तावेज़ में rectangle शैप डालें

हालांकि मुख्य लक्ष्य शैप को छिपाना है, कई परिस्थितियों में पहले शैप डालना शुरू किया जाता है। `InsertShape` मेथड कई `ShapeType` मानों को सपोर्ट करता है, जिसमें `Rectangle`, `Ellipse`, `Line`, और कस्टम इमेजेज़ शामिल हैं।

```csharp
// Example: Insert an ellipse shape and keep it visible.
Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 80, 80);
ellipse.FillColor = System.Drawing.Color.Pink;
```

**Rectangle का उपयोग क्यों करें?**  
एक rectangle एक साफ, अक्ष‑समान कंटेनर प्रदान करता है जो टेक्स्ट, इमेजेज़ या अन्य नेस्टेड शैप्स रख सकता है। इसे अक्सर टेबल या चार्ट जैसे डायनामिक कंटेंट के प्लेसहोल्डर के रूप में उपयोग किया जाता है। पहले rectangle डालने से, आप लेआउट स्थिरता को बनाए रखते हैं, भले ही बाद में उसे छिपा दें।

## Word दस्तावेज़ में शैप डालें – सर्वोत्तम प्रथाएँ

जब आप `insert shape into word document` करते हैं, तो निम्नलिखित पर विचार करें:

* **Set explicit dimensions** – स्वचालित आकार पर निर्भरता से बचें; प्लेटफ़ॉर्म्स के बीच सुसंगत लेआउट सुनिश्चित करने के लिए चौड़ाई और ऊँचाई पॉइंट्स में निर्दिष्ट करें।
* **Define positioning** – डिफ़ॉल्ट रूप से शैप वर्तमान पैराग्राफ से जुड़ा होता है। इसे सटीक रूप से रखने के लिए `builder.MoveTo` या `builder.StartBookmark` का उपयोग करें।
* **Apply styling early** – Fill color, line style, और टेक्स्ट रैपिंग अंतिम रूप को प्रभावित करते हैं। यहाँ तक कि छिपे हुए शैप्स भी उचित स्टाइलिंग से लाभान्वित होते हैं क्योंकि मार्कअप अपरिवर्तित रहता है।
* **Version compatibility** – `Hidden` प्रॉपर्टी केवल Aspose.Words 24.10 और उसके बाद के संस्करणों में उपलब्ध है। यदि आप पुराने संस्करण को लक्षित कर रहे हैं, तो आप `Node` API का उपयोग करके मैन्युअली `<w:hidden/>` एट्रिब्यूट जोड़ सकते हैं।

### हिडन एट्रिब्यूट को मैन्युअली जोड़ना (फ़ॉलबैक)

```csharp
// Fallback for Aspose.Words versions prior to 24.10
Shape shape = builder.InsertShape(ShapeType.Rectangle, 100, 50);
shape.FillColor = System.Drawing.Color.LightGray;

// Access the underlying OpenXml node.
var shapeNode = shape.GetChildNodes(NodeType.Any, true)[0];
shapeNode.GetAttributes().Add("w:hidden", "true");
```

## पूर्ण अंत‑से‑अंत उदाहरण

सब कुछ मिलाकर, यहाँ एक एकल प्रोग्राम है जो:

1. एक rectangle शैप डालता है।
2. शैप को छिपाता है।
3. कंट्रास्ट के लिए एक दृश्यमान ellipse डालता है।
4. दस्तावेज़ को सहेजता है।

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class FullDemo
{
    static void Main()
    {
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert and hide a rectangle.
        Shape rect = builder.InsertShape(ShapeType.Rectangle, 120, 60);
        rect.FillColor = System.Drawing.Color.LightGreen;
        rect.Hidden = true; // core of how to hide shape in word

        // Insert a visible ellipse to show the difference.
        Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 80, 80);
        ellipse.FillColor = System.Drawing.Color.Coral;

        // Save the output.
        string filePath = "demo_output.docx";
        doc.Save(filePath);
        Console.WriteLine($"Demo document saved to {filePath}");
    }
}
```

प्रोग्राम चलाने से `demo_output.docx` बनता है। जब इसे खोला जाता है, तो आपको केवल कोरल ellipse दिखेगा; हरा rectangle XML में मौजूद है लेकिन दृश्य से छिपा हुआ है।

## आम प्रश्न और किनारे के मामलों

**Q: क्या शैप को छिपाने से पेजिनेशन पर असर पड़ता है?**  
A: नहीं। छिपे हुए शैप्स को लेआउट इंजन द्वारा अनदेखा किया जाता है, इसलिए वे स्थान नहीं लेते। यह उन प्लेसहोल्डर कंटेंट के लिए उपयोगी है जो पेज ब्रेक्स को प्रभावित नहीं करना चाहिए।

**Q: क्या मैं हेडर या फुटर का हिस्सा होने वाले शैप को छिपा सकता हूँ?**  
A: हाँ। वही `Hidden` प्रॉपर्टी दस्तावेज़ ट्री में कहीं भी स्थित शैप्स पर काम करती है, जिसमें हेडर, फुटर, और टेबल के अंदर भी शामिल हैं।

**Q: यदि मुझे एक साथ कई शैप्स को छिपाना हो तो क्या करें?**  
A: `Document.GetChildNodes(NodeType.Shape, true)` संग्रह पर इटररेट करें और प्रत्येक लक्ष्य शैप के लिए `Hidden = true` सेट करें।

```csharp
foreach (Shape s in doc.GetChildNodes(NodeType.Shape, true))
{
    if (s.ShapeType == ShapeType.Rectangle)
        s.Hidden = true;
}
```

**Q: क्या PDF में कन्वर्ट करने पर हिडन एट्रिब्यूट बना रहता है?**  
A: PDF में कन्वर्ट करते समय, छिपे हुए शैप्स डिफ़ॉल्ट रूप से बाहर रखे जाते हैं, जो Word की रेंडरिंग व्यवहार से मेल खाता है। यदि आपको PDF में चाहिए, तो कन्वर्ज़न से पहले उन्हें अनहाइड करना होगा।

## टिप्स और संभावित समस्याएँ

* **Pro tip:** यदि आप बाद में शैप को अनहाइड करना चाहते हैं बिना आसपास के टेक्स्ट को प्रभावित किए, तो छिपाने से पहले `shape.WrapType = WrapType.None` सेट करें।
* **Watch out for older Aspose.Words versions:** `Hidden` प्रॉपर्टी 24.10 से पहले `NotSupportedException` फेंकती है। ऐसे में मैन्युअल XML तरीका उपयोग करें।
* **Testing:** हमेशा उत्पन्न `.docx` को Word में खोलें और “Show XML markup” (Developer टैब) का उपयोग करके पुष्टि करें कि `<w:hidden/>` एट्रिब्यूट मौजूद है।

## निष्कर्ष

अब आप जानते हैं कि C# और Aspose.Words का उपयोग करके Word में शैप को कैसे छिपाएँ, साथ ही rectangle शैप कैसे डालें और Word दस्तावेज़ में शैप डालें, दृश्यता पर पूर्ण नियंत्रण के साथ। `Hidden` प्रॉपर्टी का उपयोग करके आप शैप्स को दस्तावेज़ मॉडल में रख सकते हैं बाद में प्रोसेसिंग के लिए, जबकि अंतिम उपयोगकर्ताओं को एक साफ़ दृश्य प्रस्तुत कर सकते हैं।

अगला, संबंधित विषयों का अन्वेषण करें जैसे **रनटाइम पर शैप प्रॉपर्टीज़ अपडेट करना**, **छिपे हुए शैप्स को इमेजेज़ में बदलना**, या **Open XML SDK का उपयोग करके हिडन एलिमेंट्स को सीधे मैनिपुलेट करना**। ये एक्सटेंशन आपके ज्ञान को गहरा करेंगे

## आप को अगला क्या सीखना चाहिए?

निम्नलिखित ट्यूटोरियल्स उन निकट-संबंधित विषयों को कवर करते हैं जो इस गाइड में प्रदर्शित तकनीकों पर आधारित हैं। प्रत्येक संसाधन में पूर्ण कार्यशील कोड उदाहरण और चरण-दर-चरण व्याख्याएँ शामिल हैं जो आपको अतिरिक्त API फीचर्स में महारत हासिल करने और अपने प्रोजेक्ट्स में वैकल्पिक इम्प्लीमेंटेशन अप्रोचेज़ का अन्वेषण करने में मदद करेंगे।

- [Insert Shapes in Word Documents Using Aspose.Words for .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}