---
category: general
date: 2026-10-13
description: Aspose.Words का उपयोग करके प्रोग्रामेटिकली कमांड बटन कैसे जोड़ें, सीखें।
  यह गाइड पूर्ण C# कोड के साथ वर्ड दस्तावेज़ बटन बनाने का तरीका भी दिखाता है।
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- add command button programmatically
- create word document button
language: hi
lastmod: 2026-10-13
og_description: Aspose.Words का उपयोग करके प्रोग्रामेटिकली एक कमांड बटन को Word दस्तावेज़
  में जोड़ें। C# के साथ Word दस्तावेज़ बटन बनाने के लिए इस पूर्ण ट्यूटोरियल का पालन
  करें।
og_image_alt: Screenshot of a Word document with a command button inserted programmatically
og_title: Word दस्तावेज़ में प्रोग्रामेटिक रूप से कमांड बटन जोड़ें – चरण‑दर‑चरण गाइड
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Learn how to add a command button programmatically using Aspose.Words.
    This guide also shows how to create a Word document button with full C# code.
  headline: How to add a command button programmatically in a Word document
  type: TechArticle
- description: Learn how to add a command button programmatically using Aspose.Words.
    This guide also shows how to create a Word document button with full C# code.
  name: How to add a command button programmatically in a Word document
  steps:
  - name: 'Create a new console project:'
    text: 'Create a new console project:'
  - name: 'Add the Aspose.Words NuGet package:'
    text: 'Add the Aspose.Words NuGet package:'
  - name: Open **Program.cs** and replace its content with the scaffold shown in the
      next steps.
    text: Open **Program.cs** and replace its content with the scaffold shown in the
      next steps.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: Word दस्तावेज़ में प्रोग्रामेटिक रूप से कमांड बटन कैसे जोड़ें
url: /hi/net/working-with-oleobjects-and-activex/how-to-add-a-command-button-programmatically-in-a-word-docum/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word दस्तावेज़ में प्रोग्रामेटिकली कमांड बटन कैसे जोड़ें  

यदि आपको **प्रोग्रामेटिकली कमांड बटन जोड़ना** है, तो Aspose.Words एक साफ़ API प्रदान करता है जो आपको OLE फ़ॉर्म कंट्रोल्स को सीधे .docx फ़ाइल में एम्बेड करने देता है। यह ट्यूटोरियल आपको हर चरण से ले जाता है जो **Word दस्तावेज़ बटन बनाने** के लिए आवश्यक है, जो Microsoft Word में दस्तावेज़ खोलने पर एक सामान्य फ़ॉर्म बटन की तरह व्यवहार करता है।  

आप सीखेंगे कि विकास पर्यावरण कैसे सेटअप करें, बटन कैसे डालें, उसकी प्रॉपर्टीज़ कैसे कॉन्फ़िगर करें, और परिणाम कैसे सत्यापित करें। कोई बाहरी यूटिलिटीज़ आवश्यक नहीं हैं—सिर्फ एक .NET प्रोजेक्ट और Aspose.Words for .NET लाइब्रेरी।  

## आवश्यकताएँ  

शुरू करने से पहले, सुनिश्चित करें कि आपके पास है:  

* .NET 6.0 SDK या बाद का संस्करण स्थापित हो।  
* Aspose.Words for .NET का नवीनतम संस्करण (उदाहरण में 23.12 उपयोग किया गया है, लेकिन कोई भी 22.x+ रिलीज़ काम करेगा)।  
* Visual Studio 2022 या Visual Studio Code जैसे IDE।  

कोड Windows, macOS, और Linux पर चलता है क्योंकि Aspose.Words प्लेटफ़ॉर्म‑इंडिपेंडेंट है।  

## चरण 1: प्रोजेक्ट सेटअप करें और Aspose.Words को रेफ़रेंस करें  

1. एक नया कंसोल प्रोजेक्ट बनाएं:  

   ```bash
   dotnet new console -n WordButtonDemo
   cd WordButtonDemo
   ```  

2. Aspose.Words NuGet पैकेज जोड़ें:  

   ```bash
   dotnet add package Aspose.Words
   ```  

3. **Program.cs** खोलें और उसकी सामग्री को अगले चरणों में दिखाए गए स्कैफ़ोल्ड से बदल दें।  

प्रोजेक्ट को इस तरह सेटअप करने से यह सुनिश्चित होता है कि कंपाइलर `Aspose.Words` और `Aspose.Words.Drawing.Forms` नेमस्पेस को ढूंढ सके, जो फ़ॉर्म कंट्रोल्स के लिए आवश्यक हैं।  

## चरण 2: एक खाली दस्तावेज़ और DocumentBuilder को इनिशियलाइज़ करें  

`Document` क्लास पूरे Word फ़ाइल का प्रतिनिधित्व करती है, जबकि `DocumentBuilder` कंटेंट जोड़ने के लिए एक फ्लुएंट API प्रदान करता है।  

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Forms;
using System.Drawing;   // required for RectangleF

// Create an empty document.
Document doc = new Document();

// Create a builder linked to the document.
DocumentBuilder builder = new DocumentBuilder(doc);
```  

*यह चरण क्यों महत्वपूर्ण है* – `DocumentBuilder` के बिना आप बटन को पेज पर सटीक रूप से पोज़िशन नहीं कर सकते। बिल्डर वर्तमान कर्सर लोकेशन का सम्मान करता है, जिससे बाद में कई कंट्रोल्स डालना आसान हो जाता है।  

## चरण 3: कमांड बटन OLE कंट्रोल डालें  

Aspose.Words कमांड बटन को `ControlType.CommandButton` प्रकार के OLE कंट्रोल के रूप में मानता है। आप उसकी लोकेशन और आकार को `RectangleF` से परिभाषित करते हैं, जो पॉइंट्स में मापा जाता है (1 पॉइंट = 1/72 इंच)।  

```csharp
// Define the button rectangle: X=100, Y=150, Width=120, Height=30 (points)
RectangleF buttonRect = new RectangleF(100, 150, 120, 30);

// Insert the command button at the current cursor position.
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    ControlType.CommandButton,
    buttonRect);
```  

**मुख्य बिंदु**  

* आयत का मूल बिंदु (X, Y) पेज के टॉप‑लेफ़्ट कोने के सापेक्ष होता है।  
* `Width` या `Height` बदलने से बटन का दृश्य आकार बदलता है।  
* `InsertForms2OleControl` एक `Forms2OleControl` ऑब्जेक्ट लौटाता है जिसे आप आगे कॉन्फ़िगर कर सकते हैं।  

## चरण 4: बटन का नाम और कैप्शन कॉन्फ़िगर करें  

**नाम** Word के मैक्रो इंजन द्वारा कंट्रोल को पहचानने के लिए उपयोग किया जाता है, जबकि **कैप्शन** वह टेक्स्ट है जो उपयोगकर्ता देखता है।  

```csharp
// Set a unique identifier for the button.
commandButton.Name = "cmdSubmit";

// Set the text displayed on the button.
commandButton.Caption = "Submit";
```  

यदि आप बाद में VBA मैक्रो जोड़ने की योजना बनाते हैं, तो वर्णनात्मक नाम उपयोग करें क्योंकि Word का मैक्रो रिकॉर्डर इस प्रॉपर्टी को रेफ़र करता है।  

## चरण 5: (वैकल्पिक) दस्तावेज़ सहेजें और परिणाम सत्यापित करें  

फ़ाइल सहेजने से आप इसे Microsoft Word में खोल सकते हैं ताकि पुष्टि हो सके कि बटन दिखाई देता है और काम करता है।  

```csharp
// Save the document to the output folder.
string outputPath = Path.Combine(Environment.CurrentDirectory, "CommandButtonDemo.docx");
doc.Save(outputPath);

Console.WriteLine($"Document saved to: {outputPath}");
```  

जब आप Word में *CommandButtonDemo.docx* खोलते हैं, तो आपको **Submit** लेबल वाला बटन दिखाई देगा, जो बाएँ मार्जिन से लगभग 1.4 इंच और पेज के शीर्ष से 2.1 इंच पर स्थित है। बटन पर क्लिक करने से डिफ़ॉल्ट रूप से कुछ नहीं होता क्योंकि कोई मैक्रो संलग्न नहीं है, लेकिन विज़ुअल कंट्रोल पूरी तरह कार्यात्मक है।  

## चरण 6: किनारे के मामले और सामान्य जाल  

| स्थिति | ध्यान रखने योग्य बात | सुझाया गया समाधान |
|-----------|-------------------|-----------------|
| **बटन मौजूदा टेक्स्ट के साथ ओवरलैप करता है** | आयत पैराग्राफ़ के साथ इंटरसेक्ट कर सकती है, जिससे लेआउट समस्याएँ उत्पन्न हो सकती हैं। | बटन डालने से पहले `builder.Writeln()` कॉल करके कर्सर को नई लाइन पर ले जाएँ, या `Y` कॉर्डिनेट को समायोजित करें। |
| **दस्तावेज़ चेतावनी के साथ खुलता है** | कुछ Word संस्करण उन OLE कंट्रोल्स को फ्लैग करते हैं जिनका कोई लिंक्ड प्रोग्राम नहीं होता। | सुनिश्चित करें कि कंट्रोल टाइप `CommandButton` है; Word इसे एक स्टैंडर्ड फ़ॉर्म एलिमेंट मानता है और बाहरी प्रोग्राम की आवश्यकता नहीं होती। |
| **Linux पर हेडलेस वातावरण में चलाना** | UI टेस्ट करने के लिए Word लॉन्च नहीं किया जा सकता, लेकिन फ़ाइल वैध रहती है। | एक यूनिट टेस्ट उपयोग करें जो कंट्रोल की प्रॉपर्टीज़ (`commandButton.Name`, `commandButton.Caption`) पढ़े और सत्यापित करे कि वे सही सेट हुई हैं। |
| **कई बटनों की आवश्यकता** | कर्सर को मूव किए बिना वही `DocumentBuilder` दोबारा उपयोग करने से बटन पिछले बटन के ऊपर जोड़ दिया जाता है। | प्रत्येक इन्सर्शन से पहले `builder.MoveToDocumentEnd()` कॉल करें या आयत के `Y` मान को समायोजित करें। |

इन किनारे के मामलों को शुरुआती चरण में संबोधित करने से सैकड़ों कंट्रोल्स वाले पूर्ण फ़ॉर्म्स में समाधान को स्केल करने पर समय बचता है।  

## चरण 7: पूर्ण, चलाने योग्य उदाहरण  

नीचे एक स्व-निहित प्रोग्राम है जिसे आप कॉपी, पेस्ट और बिना किसी संशोधन के चला सकते हैं (NuGet रिस्टोर को छोड़कर)।  

```csharp
using System;
using System.IO;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing.Forms;

namespace WordButtonDemo
{
    class Program
    {
        static void Main()
        {
            // 1. Create a new empty document.
            Document doc = new Document();

            // 2. Create a DocumentBuilder to work with the document.
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 3. Define the button rectangle (position + size).
            RectangleF buttonRect = new RectangleF(100, 150, 120, 30);

            // 4. Insert the command button OLE control.
            Forms2OleControl commandButton = builder.InsertForms2OleControl(
                ControlType.CommandButton,
                buttonRect);

            // 5. Set identifying properties.
            commandButton.Name = "cmdSubmit";
            commandButton.Caption = "Submit";

            // 6. Save the document.
            string outputPath = Path.Combine(
                Environment.CurrentDirectory,
                "CommandButtonDemo.docx");
            doc.Save(outputPath);

            Console.WriteLine($"Document saved to: {outputPath}");
        }
    }
}
```

**अपेक्षित आउटपुट**  

प्रोग्राम चलाने पर एक पाथ प्रिंट होता है जो इस प्रकार है:  

```
Document saved to: C:\Path\To\WordButtonDemo\CommandButtonDemo.docx
```  

जेनरेटेड *CommandButtonDemo.docx* खोलने पर एक ही **Submit** बटन दिखता है जो कोड में परिभाषित कॉर्डिनेट्स पर रखा गया है। कोई अतिरिक्त UI एलिमेंट नहीं दिखता, जिससे पुष्टि होती है कि **प्रोग्रामेटिकली कमांड बटन जोड़ने** वर्कफ़्लो सफल रहा।  

## निष्कर्ष  

अब आप जानते हैं कि Aspose.Words का उपयोग करके Word दस्तावेज़ में **प्रोग्रामेटिकली कमांड बटन कैसे जोड़ें**, और यह भी समझते हैं कि **Word दस्तावेज़ बटन कैसे बनाएं** जिसे बाद में VBA मैक्रो या बाहरी ऑटोमेशन टूल्स से जोड़ा जा सकता है। प्रक्रिया में दस्तावेज़ को इनिशियलाइज़ करना, OLE `CommandButton` कंट्रोल डालना, उसकी प्रॉपर्टीज़ कॉन्फ़िगर करना, और फ़ाइल सहेजना शामिल है।  

अब आप आगे कर सकते हैं:  

* विभिन्न `ControlType` मानों के साथ चरण 3 दोहराकर अधिक कंट्रोल्स (चेकबॉक्स, टेक्स्ट फ़ील्ड) जोड़ें।  
* बटन से VBA मैक्रो संलग्न करें ताकि फ़ॉर्म सहेजना या ईमेल भेजना जैसी क्रियाएँ की जा सकें।  
* फ़ील्ड परिभाषाओं के डेटा‑ड्रिवन कलेक्शन पर लूप करके पूरे फ़ॉर्म को डायनामिकली जेनरेट करें।  

आयत के कॉर्डिनेट्स और बटन के कैप्शन को अपने UI डिज़ाइन के अनुसार प्रयोग करें। कोडिंग का आनंद लें!  


## अब आप आगे क्या सीखें?  


निम्नलिखित ट्यूटोरियल्स उन संबंधित विषयों को कवर करते हैं जो इस गाइड में दिखाए गए तकनीकों पर आधारित हैं। प्रत्येक संसाधन में पूर्ण कार्यशील कोड उदाहरण और चरण‑दर‑चरण व्याख्याएँ शामिल हैं, जो आपको अतिरिक्त API फीचर्स में महारत हासिल करने और अपने प्रोजेक्ट्स में वैकल्पिक इम्प्लीमेंटेशन अप्रोचेज़ को एक्सप्लोर करने में मदद करेंगे।  

- [Aspose.Words for .NET के साथ Word दस्तावेज़ में कॉम्बो बॉक्स फ़ॉर्म फ़ील्ड जोड़ें](/words/english/net/add-content-using-documentbuilder/insert-combo-box/)
- [Aspose.Words for .NET के साथ Word दस्तावेज़ में चेक बॉक्स फ़ॉर्म फ़ील्ड जोड़ें](/words/english/net/add-content-using-documentbuilder/insert-check-box/)
- [Aspose.Words के साथ खाली Word दस्तावेज़ बनाएं – चरण‑दर‑चरण गाइड](/words/english/net/programming-with-shapes/create-blank-word-document-with-aspose-words-step-by-step-gu/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}