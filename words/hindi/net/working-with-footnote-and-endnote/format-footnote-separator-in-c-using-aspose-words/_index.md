---
category: general
date: 2026-08-10
description: C# में Aspose.Words का उपयोग करके फुटनोट सेपरेटर को फॉर्मेट करें और फुटनोट
  व एंडनोट लाइनों को कस्टमाइज़ करें। मिनटों में C# फुटनोट फॉर्मेटिंग सीखें।
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- format footnote separator
- Aspose.Words footnote separator
- C# footnote formatting
- modify footnote separator
- style footnote separator
- endnote separator formatting
language: hi
lastmod: 2026-08-10
og_description: Aspose.Words का उपयोग करके C# में फुटनोट सेपरेटर को फॉर्मेट करें।
  फुटनोट और एंडनोट सेपरेटर्स को तेज़ और भरोसेमंद तरीके से स्टाइल करने के लिए इस ट्यूटोरियल
  का पालन करें।
og_image_alt: Code editor showing C# snippet that styles a footnote separator
og_title: C# में फुटनोट सेपरेटर को फॉर्मेट करें – पूर्ण Aspose.Words गाइड
schemas:
- author: Aspose
  dateModified: '2026-08-10'
  description: Format footnote separator in C# with Aspose.Words to customize footnote
    and endnote lines. Learn C# footnote formatting in minutes.
  headline: Format footnote separator in C# using Aspose.Words
  type: TechArticle
- description: Format footnote separator in C# with Aspose.Words to customize footnote
    and endnote lines. Learn C# footnote formatting in minutes.
  name: Format footnote separator in C# using Aspose.Words
  steps:
  - name: Styling the continuation separator (optional)
    text: 'The continuation separator appears when a footnote spans multiple pages.
      You can style it similarly:'
  - name: Formatting the endnote separator
    text: 'If your document also uses endnotes, you can apply the same logic to the
      `Endnotes` collection:'
  - name: Using a custom string for the separator
    text: 'Sometimes you want the separator to be a series of asterisks (`***`). Replace
      the existing runs with a new run:'
  - name: Handling documents without a separator node
    text: 'A rare edge case is a document that omits the separator node (e.g., when
      the author deleted it). In that scenario `document.Footnotes.Separator` returns
      `null`. Guard against it:'
  type: HowTo
tags:
- Aspose.Words
- C#
- footnotes
- document‑processing
title: C# में Aspose.Words का उपयोग करके फुटनोट सेपरेटर को फ़ॉर्मेट करें
url: /hi/net/working-with-footnote-and-endnote/format-footnote-separator-in-c-using-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C# में Aspose.Words का उपयोग करके फुटनोट सेपरेटर को फॉर्मेट करें

यदि आपको Word दस्तावेज़ में **format footnote separator** करने की आवश्यकता है, तो यह गाइड आपको Aspose.Words for .NET के साथ यह कैसे करना है दिखाएगा। आप एक पूर्ण, चलाने योग्य उदाहरण देखेंगे जो सेपरेटर पैराग्राफ की संरेखण और रंग बदलता है, और आप सीखेंगे कि उसी तकनीक को endnote separators पर कैसे लागू किया जाए।

यह ट्यूटोरियल प्रत्येक चरण को कवर करता है—स्रोत फ़ाइल को लोड करने से लेकर संशोधित दस्तावेज़ को सहेजने तक—ताकि आप कोड को अपने प्रोजेक्ट में बिना अतिरिक्त शोध के कॉपी‑पेस्ट कर सकें।

## आपको क्या चाहिए

* .NET 6.0 या बाद का संस्करण (कोड .NET Framework 4.6+ पर भी काम करता है)
* एक वैध Aspose.Words for .NET लाइसेंस (मुफ़्त ट्रायल मूल्यांकन के लिए काम करता है)
* एक Word फ़ाइल जिसमें कम से कम एक footnote या endnote हो (उदाहरण के लिए `Footnotes.docx`)
* Visual Studio 2022 या कोई भी C# IDE जो आप पसंद करते हैं

इन वस्तुओं को तैयार रखने से आप **C# footnote formatting** लॉजिक पर ध्यान केंद्रित कर सकते हैं, न कि पर्यावरण सेटअप पर।

## चरण 1: फुटनोट और एंडनोट वाले दस्तावेज़ को लोड करें

पहला कार्य यह है कि आप एक `Document` ऑब्जेक्ट बनाएं जो आपके स्रोत फ़ाइल की ओर इशारा करता हो। Aspose.Words पूरे DOCX पैकेज को मेमोरी में पढ़ता है, जिससे आपको फुटनोट और एंडनोट नोड्स तक पूरी पहुँच मिलती है।

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
using System.Drawing;

// Load the source DOCX file
Document document = new Document(@"C:\Docs\Footnotes.docx");
```

*Why this matters*: दस्तावेज़ को लोड करना किसी भी परिवर्तन का पूर्वापेक्षित शर्त है। यदि फ़ाइल पथ गलत है, तो Aspose.Words `FileNotFoundException` फेंकेगा, इसलिए आगे बढ़ने से पहले पथ की जाँच कर लें।

## चरण 2: सेपरेटर और continuation‑separator नोड्स को प्राप्त करें

Footnote और endnote सेपरेटर `Footnotes` और `Endnotes` कलेक्शन्स के अंदर विशेष नोड्स के रूप में संग्रहीत होते हैं। प्रत्येक कलेक्शन `Separator` और `ContinuationSeparator` प्रॉपर्टीज़ प्रदान करता है जो एक `Node` रेफ़रेंस लौटाती हैं।

```csharp
// Footnote separator nodes
Node footnoteSeparator          = document.Footnotes.Separator;
Node footnoteContinuationSep    = document.Footnotes.ContinuationSeparator;

// Endnote separator nodes
Node endnoteSeparator           = document.Endnotes.Separator;
Node endnoteContinuationSep     = document.Endnotes.ContinuationSeparator;
```

*Why this matters*: `Separator` नोड वह रेखा दर्शाता है जो दृश्य रूप से मुख्य टेक्स्ट को फुटनोट ब्लॉक से अलग करती है। रेफ़रेंस प्राप्त करके आप उसके पैराग्राफ फ़ॉर्मेट, फ़ॉन्ट, या यहाँ तक कि पूरे नोड को बदल सकते हैं।

## चरण 3: फुटनोट सेपरेटर की दृश्य शैली बदलें

अधिकांश Word दस्तावेज़ों में सेपरेटर एक एकल पैराग्राफ होता है जिसमें डैश या एस्टरिस्क होता है। नीचे दिया गया कोड जाँचता है कि सेपरेटर `Paragraph` है या नहीं और यदि है तो उसे केंद्रित करता है और टेक्स्ट का रंग ग्रे कर देता है।

```csharp
// Ensure the separator is a Paragraph before casting
if (footnoteSeparator is Paragraph separatorParagraph)
{
    // Center the separator paragraph
    separatorParagraph.ParagraphFormat.Alignment = ParagraphAlignment.Center;

    // Set the separator text color to gray
    if (separatorParagraph.Runs.Count > 0)
    {
        separatorParagraph.Runs[0].Font.Color = Color.Gray;
    }
}
```

### continuation separator को स्टाइल करना (वैकल्पिक)

जब फुटनोट कई पृष्ठों में फैला हो तो continuation separator दिखाई देता है। आप इसे समान रूप से स्टाइल कर सकते हैं:

```csharp
if (footnoteContinuationSep is Paragraph contParagraph)
{
    contParagraph.ParagraphFormat.Alignment = ParagraphAlignment.Center;
    if (contParagraph.Runs.Count > 0)
        contParagraph.Runs[0].Font.Color = Color.DarkGray;
}
```

*Why this matters*: सेपरेटर को संरेखित करने से पठनीयता बढ़ती है, और रंग बदलने से यह सामान्य पैराग्राफ टेक्स्ट से अलग दिखता है। आप `ParagraphAlignment.Center` को `Left` या `Right` से बदलकर अपने दस्तावेज़ के डिज़ाइन गाइडलाइन के अनुसार सेट कर सकते हैं।

## चरण 4: संशोधित दस्तावेज़ को सहेजें

इच्छित शैली लागू करने के बाद, दस्तावेज़ को डिस्क पर वापस लिखें। आप मूल फ़ाइल को ओवरराइट कर सकते हैं या नई संस्करण बना सकते हैं।

```csharp
// Save the document with the modified separator
document.Save(@"C:\Docs\Footnotes_Styled.docx");
```

जब आप `Footnotes_Styled.docx` को Microsoft Word में खोलते हैं, तो फुटनोट सेपरेटर केंद्रित और ग्रे दिखेगा, बिल्कुल उसी तरह जैसा कोड ने निर्दिष्ट किया था।

## उन्नत विविधताएँ

### endnote separator को फॉर्मेट करना

यदि आपके दस्तावेज़ में endnotes भी हैं, तो आप वही लॉजिक `Endnotes` कलेक्शन पर लागू कर सकते हैं:

```csharp
if (endnoteSeparator is Paragraph endSepParagraph)
{
    endSepParagraph.ParagraphFormat.Alignment = ParagraphAlignment.Center;
    if (endSepParagraph.Runs.Count > 0)
        endSepParagraph.Runs[0].Font.Color = Color.SlateGray;
}
```

### सेपरेटर के लिए कस्टम स्ट्रिंग का उपयोग करना

कभी‑कभी आप चाहते हैं कि सेपरेटर कई एस्टरिस्क (`***`) की श्रृंखला हो। मौजूदा रन को एक नए रन से बदलें:

```csharp
if (footnoteSeparator is Paragraph sepPara)
{
    // Clear existing content
    sepPara.Runs.Clear();

    // Add a custom separator string
    Run newRun = new Run(document, "***");
    newRun.Font.Color = Color.Gray;
    sepPara.Runs.Add(newRun);
}
```

### सेपरेटर नोड के बिना दस्तावेज़ को संभालना

एक दुर्लभ किनारा मामला वह है जहाँ दस्तावेज़ सेपरेटर नोड को छोड़ देता है (उदाहरण के लिए जब लेखक ने इसे हटा दिया)। ऐसे परिदृश्य में `document.Footnotes.Separator` `null` लौटाता है। इसके खिलाफ सुरक्षा करें:

```csharp
if (footnoteSeparator != null && footnoteSeparator is Paragraph sepPara)
{
    // Apply styling as shown earlier
}
else
{
    // Optionally create a new separator paragraph
    Paragraph newSep = new Paragraph(document);
    newSep.ParagraphFormat.Alignment = ParagraphAlignment.Center;
    Run run = new Run(document, "-");
    run.Font.Color = Color.Gray;
    newSep.Runs.Add(run);
    document.Footnotes.InsertAfter(newSep, document.Footnotes.LastParagraph);
}
```

## सामान्य समस्याएँ और उन्हें कैसे टालें

| समस्या | क्यों होता है | समाधान |
|---------|----------------|-----|
| **Separator is not a `Paragraph`** | कुछ Word टेम्प्लेट सेपरेटर के रूप में `Table` या `Shape` का उपयोग करते हैं। | कास्ट करने से पहले `is Paragraph` से नोड प्रकार जाँचें। |
| **`Runs` collection is empty** | सेपरेटर एक खाली पैराग्राफ हो सकता है। | `Runs[0]` तक पहुँचने से पहले `Runs.Count > 0` सत्यापित करें। |
| **License not applied** | लाइसेंस न होने पर Aspose.Words वॉटरमार्क डालता है और API उपयोग को सीमित कर सकता है। | प्रोग्राम की शुरुआत में `License license = new License(); license.SetLicense("Aspose.Words.lic");` कॉल करें। |
| **Saving to a read‑only folder** | `Save` मेथड `UnauthorizedAccessException` फेंकता है। | लक्ष्य डायरेक्टरी में लिखने की अनुमति सुनिश्चित करें। |

इन समस्याओं को शुरुआती चरण में हल करने से रन‑टाइम एक्सेप्शन से बचा जा सकता है और **modify footnote separator** का अनुभव सुगम बनता है।

## पूर्ण, चलाने योग्य उदाहरण

नीचे एक स्व-निहित कंसोल एप्लिकेशन है जो ऊपर चर्चा किए गए प्रत्येक चरण को प्रदर्शित करता है। कोड को नई .NET कंसोल प्रोजेक्ट में कॉपी करें, फ़ाइल पथ बदलें, और चलाएँ।

```csharp
using Aspose.Words;
using System;
using System.Drawing;

namespace FootnoteSeparatorStyler
{
    class Program
    {
        static void Main()
        {
            // OPTIONAL: Apply your Aspose.Words license
            // var license = new License();
            // license.SetLicense("Aspose.Words.lic");

            // 1. Load the source document
            string inputPath = @"C:\Docs\Footnotes.docx";
            Document doc = new Document(inputPath);

            // 2. Retrieve separator nodes
            Node footnoteSeparator = doc.Footnotes.Separator;
            Node footnoteContinuationSep = doc.Footnotes.ContinuationSeparator;
            Node endnoteSeparator = doc.Endnotes.Separator;
            Node endnoteContinuationSep = doc.Endnotes.ContinuationSeparator;

            // 3. Style footnote separator
            if (footnoteSeparator is Paragraph footSepPara)
            {
                footSepPara.ParagraphFormat.Alignment = ParagraphAlignment.Center;
                if (footSepPara.Runs.Count > 0)
                    footSepPara.Runs[0].Font.Color = Color.Gray;
            }

            // 3a. (Optional) Style footnote continuation separator
            if (footnoteContinuationSep is Paragraph footContPara)
            {
                footContPara.ParagraphFormat.Alignment = ParagraphAlignment.Center;
                if (footContPara.Runs.Count > 0)
                    footContPara.Runs[0].Font.Color = Color.DarkGray;
            }

            // 4. Style endnote separator (optional)
            if (endnoteSeparator is Paragraph endSepPara)
            {
                endSepPara.ParagraphFormat.Alignment = ParagraphAlignment.Center;
                if (endSepPara.Runs.Count > 0)
                    endSepPara.Runs[0].Font.Color = Color.SlateGray;
            }

            // 5. Save the modified document
            string outputPath = @"C:\Docs\Footnotes_Styled.docx";
            doc.Save(outputPath);

            Console.WriteLine("Footnote separator formatted successfully.");
            Console.WriteLine($"Saved to: {outputPath}");
        }
    }
}
```

**Expected result**  

जब आप `Footnotes_Styled.docx` खोलते हैं:

* फुटनोट सेपरेटर लाइन मुख्य टेक्स्ट के नीचे केंद्रित होती है।
* इसका रंग हल्का ग्रे दिखता है, जिससे यह दृश्य रूप से अलग दिखता है।
* यदि दस्तावेज़ में endnotes हैं, तो उनके सेपरेटर भी केंद्रित और ग्रे (या स्लेट) रंग के होते हैं

## आगे आप क्या सीखें?

यह गाइड में प्रदर्शित तकनीकों पर आधारित निकट-संबंधित विषयों को कवर करने वाले निम्नलिखित ट्यूटोरियल्स हैं। प्रत्येक संसाधन में पूर्ण कार्यशील कोड उदाहरण और चरण‑दर‑चरण व्याख्याएँ शामिल हैं, जो आपको अतिरिक्त API फीचर्स में निपुण बनने और अपने प्रोजेक्ट में वैकल्पिक कार्यान्वयन दृष्टिकोणों का अन्वेषण करने में मदद करेंगे।

- [Words Processing with Footnote and Endnote](/words/english/net/working-with-footnote-and-endnote/)
- [Set Footnote And Endnote Position](/words/english/net/working-with-footnote-and-endnote/set-footnote-and-end-note-position/)
- [Working With Footnote And Endnote](/words/german/net/working-with-footnote-and-endnote/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}