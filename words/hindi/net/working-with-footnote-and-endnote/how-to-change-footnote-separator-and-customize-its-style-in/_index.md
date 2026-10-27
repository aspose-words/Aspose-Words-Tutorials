---
category: general
date: 2026-10-13
description: Aspose.Words का उपयोग करके Word दस्तावेज़ में फुटनोट सेपरेटर कैसे बदलें।
  प्रोग्रामेटिकली Word दस्तावेज़ में फ़ॉन्ट का रंग बदलना सीखें।
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to change footnote separator
- change font color in word document
- style footnote separator programmatically
- Aspose.Words footnote formatting
- C# Word automation
language: hi
lastmod: 2026-10-13
og_description: Aspose.Words के साथ Word दस्तावेज़ में फुटनोट सेपरेटर कैसे बदलें।
  यह ट्यूटोरियल आपको C# का उपयोग करके Word दस्तावेज़ में फ़ॉन्ट रंग कैसे बदलें, दिखाता
  है।
og_image_alt: Screenshot of a Word document showing red footnote separator and blue
  endnote separator
og_title: वर्ड दस्तावेज़ में फुटनोट सेपरेटर कैसे बदलें – चरण‑दर‑चरण गाइड
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: How to change footnote separator in a Word document using Aspose.Words.
    Learn to change font color in Word document programmatically.
  headline: How to change footnote separator and customize its style in a Word document
  type: TechArticle
- description: How to change footnote separator in a Word document using Aspose.Words.
    Learn to change font color in Word document programmatically.
  name: How to change footnote separator and customize its style in a Word document
  steps:
  - name: Why each line matters
    text: '* **Loading the document** (`new Document`) gives you an in‑memory representation
      that Aspose.Words can manipulate. * **`GetChild` with `ParagraphNodeType.FootnoteSeparator`**
      returns the hidden paragraph that Word uses to draw the line separating footnotes
      from the main text. The same method works '
  - name: Expected output
    text: 'When you open `FootnoteSeparatorsStyled.docx` in Microsoft Word:'
  - name: 1. Install Aspose.Words
    text: 'Open a terminal in your project folder and run:'
  - name: 2. Prepare the input file
    text: Place `Footnotes.docx` in a known directory (e.g., `C:\Docs`). Ensure the
      file contains at least one footnote and one endnote so the separator nodes exist.
  - name: 3. Write the C# program
    text: Create a new console project (`dotnet new console -n FootnoteStyler`) and
      replace the generated `Program.cs` with the full code block from the **How to
      change footnote separator** section. Remember to adjust the file paths to match
      your environment.
  - name: 4. Run and verify
    text: 'Execute the program:'
  - name: 5. Extend the solution
    text: '* **Different colors:** Use any `System.Drawing.Color` value, e.g., `Color.FromArgb(255,
      128, 0)` for orange. * **Custom line style:** Instead of changing the color,
      you can modify `ParagraphFormat` properties such as `LineSpacing`, `Shading`,
      or even replace the separator character. * **Multiple do'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
- footnotes
- document styling
title: वर्ड दस्तावेज़ में फुटनोट सेपरेटर को बदलने और उसकी शैली को अनुकूलित करने का
  तरीका
url: /hi/net/working-with-footnote-and-endnote/how-to-change-footnote-separator-and-customize-its-style-in/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word दस्तावेज़ में फुटनोट विभाजक को बदलने और उसकी शैली को अनुकूलित करने का तरीका

यदि आपको Word दस्तावेज़ में **how to change footnote separator** की आवश्यकता है, तो यह गाइड आपको एक पूर्ण, तुरंत चलाने योग्य समाधान प्रदान करता है। Aspose.Words for .NET का उपयोग करके आप फुटनोट और एंडनोट विभाजकों जैसे तत्वों में **change font color in Word document** भी कर सकते हैं, जिससे अंतिम फ़ाइल आपके ब्रांडिंग या शैली गाइड से मेल खाती है।

Document authors often ask: *Why does the default footnote separator look plain, and how can I make it stand out?* The answer is to directly access the separator paragraph objects, adjust their font properties, and save the result. This tutorial walks you through every step, from loading a .docx file to persisting the styled output.

आप सीखेंगे कैसे:

* ऐसी Word फ़ाइल लोड करें जिसमें पहले से फुटनोट और एंडनोट मौजूद हों।  
* फुटनोट और एंडनोट विभाजक पैराग्राफ को खोजें।  
* प्रत्येक विभाजक का फ़ॉन्ट रंग बदलें (फुटनोट के लिए लाल, एंडनोट के लिए नीला)।  
* परिवर्तित दस्तावेज़ को किसी भी मौजूदा सामग्री को खोए बिना सहेजें।

Aspose.Words लाइब्रेरी और .NET विकास वातावरण के अलावा कोई बाहरी टूल आवश्यक नहीं है।

## आवश्यकताएँ

* .NET 6.0 SDK या बाद का संस्करण (कोड .NET Framework 4.7+ के साथ भी काम करता है)।  
* Visual Studio 2022, Rider, या आपका पसंदीदा कोई भी C# एडिटर।  
* Aspose.Words for .NET NuGet पैकेज (`Aspose.Words`)।  
* एक नमूना Word फ़ाइल (`Footnotes.docx`) जिसमें कम से कम एक फुटनोट और एक एंडनोट हो।

> **Pro tip:** यदि आपके पास नमूना फ़ाइल नहीं है, तो एक नया Word दस्तावेज़ बनाएं, एक फुटनोट (`References → Insert Footnote`) और एक एंडनोट (`References → Insert Endnote`) सम्मिलित करें। इसे `Footnotes.docx` के रूप में उस फ़ोल्डर में सहेजें जिसे आप कोड से संदर्भित कर सकते हैं।

## Aspose.Words के साथ फुटनोट विभाजक को बदलने का तरीका

कार्य का मूल भाग Aspose.Words द्वारा *separator* नोड्स के रूप में उजागर किए गए विशेष पैराग्राफ़ को प्राप्त करना है। ये नोड्स `Paragraph` प्रकार के होते हैं और किसी अन्य पैराग्राफ़ की तरह फ़ॉर्मेट किए जा सकते हैं।

```csharp
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Tables;

class FootnoteSeparatorStyler
{
    static void Main()
    {
        // Step 1: Load the source document that already contains footnotes/endnotes.
        Document doc = new Document(@"C:\Docs\Footnotes.docx");

        // Step 2: Get the footnote separator paragraph.
        Paragraph footnoteSeparator = (Paragraph)doc.GetChild(
            NodeType.Paragraph, (int)ParagraphNodeType.FootnoteSeparator, true);

        // Step 3: Get the endnote separator paragraph.
        Paragraph endnoteSeparator = (Paragraph)doc.GetChild(
            NodeType.Paragraph, (int)ParagraphNodeType.EndnoteSeparator, true);

        // Step 4: Change the font color of the footnote separator to red.
        footnoteSeparator.Font.Color = Color.Red;

        // Step 5: Change the font color of the endnote separator to blue.
        endnoteSeparator.Font.Color = Color.Blue;

        // Step 6: Save the modified document.
        doc.Save(@"C:\Docs\FootnoteSeparatorsStyled.docx");
    }
}
```

### प्रत्येक पंक्ति का महत्व क्यों है

* **Loading the document** (`new Document`) आपको एक इन‑मेमोरी प्रतिनिधित्व देता है जिसे Aspose.Words हेरफेर कर सकता है।  
* **`GetChild` with `ParagraphNodeType.FootnoteSeparator`** वह छिपा पैराग्राफ़ लौटाता है जिसे Word फुटनोट को मुख्य टेक्स्ट से अलग करने वाली रेखा खींचने के लिए उपयोग करता है। वही मेथड एंडनोट विभाजक के लिए भी काम करता है।  
* **Changing `Font.Color`** सीधे रेखा की उपस्थिति को प्रभावित करता है क्योंकि Word विभाजक को एक पैराग्राफ़ के रूप में एकल “‑” अक्षर के साथ रेंडर करता है। रंग को `Color.Red` (या किसी भी `System.Drawing.Color`) पर सेट करने से दृश्य शैली अपडेट होती है।  
* **Saving** परिवर्तन को एक .docx फ़ाइल में लिखता है जिसे कोई भी Word प्रोसेसर खोल सकता है।

### अपेक्षित आउटपुट

जब आप Microsoft Word में `FootnoteSeparatorsStyled.docx` खोलते हैं:

* फुटनोट विभाजक रेखा **लाल** दिखाई देती है।  
* एंडनोट विभाजक रेखा **नीली** दिखाई देती है।  

सभी मूल फुटनोट और एंडनोट सामग्री अपरिवर्तित रहती है।

## C# का उपयोग करके Word दस्तावेज़ में फ़ॉन्ट रंग बदलें

ऊपर दर्शाया गया ऑपरेशन व्यापक क्षमता का एक विशिष्ट मामला है: प्रोग्रामेटिक रूप से **change font color in Word document**। एक बार जब आपके पास `Paragraph`, `Run`, या कोई भी `Node` हो जिसमें टेक्स्ट हो, आप उसके `Font.Color` प्रॉपर्टी को समायोजित कर सकते हैं।

```csharp
// Example: Change the color of all headings (style "Heading 1") to dark green.
foreach (Paragraph para in doc.GetChildNodes(NodeType.Paragraph, true))
{
    if (para.ParagraphFormat.StyleIdentifier == StyleIdentifier.Heading1)
        para.Font.Color = Color.DarkGreen;
}
```

* यह स्निपेट प्रत्येक पैराग्राफ़ पर इटररेट करता है, जांचता है कि क्या वह `Heading 1` शैली का उपयोग करता है, और उसका फ़ॉन्ट रंग सेट करता है।  
* आप इस शर्त को बदलकर फुटनोट, टेबल या किसी अन्य नोड प्रकार को लक्षित कर सकते हैं।

## चरण‑दर‑चरण विवरण

### 1. Aspose.Words स्थापित करें

अपने प्रोजेक्ट फ़ोल्डर में एक टर्मिनल खोलें और चलाएँ:

```bash
dotnet add package Aspose.Words
```

### 2. इनपुट फ़ाइल तैयार करें

`Footnotes.docx` को एक ज्ञात डायरेक्टरी (जैसे, `C:\Docs`) में रखें। सुनिश्चित करें कि फ़ाइल में कम से कम एक फुटनोट और एक एंडनोट हो ताकि विभाजक नोड्स मौजूद हों।

### 3. C# प्रोग्राम लिखें

एक नया कंसोल प्रोजेक्ट बनाएं (`dotnet new console -n FootnoteStyler`) और जेनरेटेड `Program.cs` को **How to change footnote separator** सेक्शन के पूर्ण कोड ब्लॉक से बदलें। फ़ाइल पाथ को अपने पर्यावरण के अनुसार समायोजित करना याद रखें।

### 4. चलाएँ और सत्यापित करें

प्रोग्राम चलाएँ:

```bash
dotnet run
```

रन पूरा होने के बाद, `FootnoteSeparatorsStyled.docx` खोलें। आपको वर्णित अनुसार लाल और नीली विभाजक रेखाएँ दिखनी चाहिए।

### 5. समाधान का विस्तार करें

* **Different colors:** कोई भी `System.Drawing.Color` मान उपयोग करें, उदाहरण के लिए नारंगी के लिए `Color.FromArgb(255, 128, 0)`।  
* **Custom line style:** रंग बदलने के बजाय, आप `ParagraphFormat` प्रॉपर्टीज़ जैसे `LineSpacing`, `Shading`, या यहां तक कि विभाजक अक्षर को बदल सकते हैं।  
* **Multiple documents:** लॉजिक को एक मेथड में रैप करें जो इनपुट और आउटपुट पाथ लेता है, फिर बैच प्रोसेसिंग के लिए लूप में इसे कॉल करें।

## सामान्य समस्याएँ और उन्हें कैसे टालें

| लक्षण | कारण | समाधान |
|---------|-------|-----|
| `GetChild` returns `null` | स्रोत दस्तावेज़ में फुटनोट/एंडनोट विभाजक नहीं है (जैसे, कोई फुटनोट नहीं)। | कम से कम एक फुटनोट या एंडनोट जोड़ें, या `Font` तक पहुँचने से पहले `null` की जाँच करें। |
| रंग परिवर्तन दिखाई नहीं दे रहा | कुछ Word संस्करणों में विभाजक को एक अक्षर की बजाय रेखा के रूप में रेंडर किया जाता है। | `ParagraphFormat.LineSpacingRule = LineSpacingRule.Exactly` और `ParagraphFormat.LineSpacing = 1` सेट करें ताकि एक दृश्यमान अक्षर बाध्य हो। |
| रनटाइम एक्सेप्शन `FileNotFoundException` | गलत फ़ाइल पाथ। | एब्सोल्यूट पाथ का उपयोग करें या `Path.Combine` को `Environment.CurrentDirectory` के साथ प्रयोग करें। |

## पूर्ण, चलाने योग्य उदाहरण

नीचे पूर्ण प्रोग्राम दिया गया है जिसे आप कॉपी‑पेस्ट करके एक कंसोल ऐप में उपयोग कर सकते हैं। इसमें एरर हैंडलिंग और टिप्पणियाँ शामिल हैं जो प्रत्येक ऑपरेशन को समझाती हैं।

```csharp
using System;
using System.Drawing;
using Aspose.Words;

namespace FootnoteSeparatorStyler
{
    class Program
    {
        static void Main()
        {
            // Paths – update these to match your environment.
            const string inputPath = @"C:\Docs\Footnotes.docx";
            const string outputPath = @"C:\Docs\FootnoteSeparatorsStyled.docx";

            // Load the document.
            Document doc = new Document(inputPath);

            // Retrieve footnote separator.
            Paragraph footnoteSeparator = (Paragraph)doc.GetChild(
                NodeType.Paragraph, (int)ParagraphNodeType.FootnoteSeparator, true);

            // Retrieve endnote separator.
            Paragraph endnoteSeparator = (Paragraph)doc.GetChild(
                NodeType.Paragraph, (int)ParagraphNodeType.EndnoteSeparator, true);

            // Guard against missing separators.
            if (footnoteSeparator == null || endnoteSeparator == null)
            {
                Console.WriteLine("The document does not contain footnote or endnote separators.");
                return;
            }

            // Change colors – this is the core of “change font color in word document”.
            footnoteSeparator.Font.Color = Color.Red;   // Footnote separator → red
            endnoteSeparator.Font.Color = Color.Blue; // Endnote separator → blue

            // Save the result.
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

इस प्रोग्राम को चलाने से एक Word फ़ाइल बनती है जहाँ फुटनोट विभाजक रेखा लाल और एंडनोट विभाजक रेखा नीली होती है, जिससे **how to change footnote separator** की आवश्यकता पूरी होती है और साथ ही **change font color in word document** का प्रदर्शन भी होता है।

## निष्कर्ष

आप अब जानते हैं कि Aspose.Words for .NET का उपयोग करके Word दस्तावेज़ में **how to change footnote separator** कैसे किया जाता है और प्रोग्रामेटिक रूप से **change font color in Word document** कैसे किया जाता है। प्रक्रिया इस प्रकार है:

1. दस्तावेज़ लोड करें।  
2. छिपे हुए विभाजक पैराग्राफ़ प्राप्त करें।  
3. उनके `Font.Color` प्रॉपर्टीज़ सेट करें।  
4. संशोधित फ़ाइल सहेजें।

यहाँ से आप अधिक उन्नत स्टाइलिंग का अन्वेषण कर सकते हैं—लाइन की मोटाई समायोजित करना, विभिन्न फ़ॉन्ट लागू करना, या कई फ़ाइलों में प्रक्रिया को स्वचालित करना। इन तकनीकों में महारत हासिल करने से आपको C# कोड से सीधे Word दस्तावेज़ की उपस्थिति पर सूक्ष्म नियंत्रण मिलता है।

---


## अगला आप क्या सीखें?

निम्नलिखित ट्यूटोरियल्स उन विषयों को कवर करते हैं जो इस गाइड में प्रदर्शित तकनीकों पर आधारित हैं। प्रत्येक संसाधन में पूर्ण कार्यशील कोड उदाहरण और चरण‑दर‑चरण व्याख्याएँ शामिल हैं जो आपको अतिरिक्त API फीचर्स में महारत हासिल करने और अपने प्रोजेक्ट्स में वैकल्पिक कार्यान्वयन दृष्टिकोणों का अन्वेषण करने में मदद करती हैं।

- [Word दस्तावेज़ में पैराग्राफ़ शैली विभाजक प्राप्त करें](/words/english/net/document-formatting/get-paragraph-style-separator/)
- [Aspose.Words का उपयोग करके हेडर और फुटर के साथ Word दस्तावेज़ बनाएं](/words/english/net/header-footer-formatting/create-header-footer/)
- [Aspose.Words for .NET का उपयोग करके Word दस्तावेज़ के फुटर में पेज नंबर जोड़ें](/words/english/net/working-with-headers-and-footers/add-page-numbers/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}