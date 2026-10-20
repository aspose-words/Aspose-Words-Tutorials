---
category: general
date: 2026-10-20
description: Aspose.Words का उपयोग करके प्रोग्रामेटिकली Word दस्तावेज़ बनाएं और एक
  कमांड बटन जोड़ें। ActiveX कंट्रोल डालना और बटन का कैप्शन सेट करना सीखें।
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document programmatically
- add command button
- add activex control
- insert activex button
- set button caption
language: hi
lastmod: 2026-10-20
og_description: प्रोग्रामेटिकली Word दस्तावेज़ बनाएं और एक ActiveX कमांड बटन एम्बेड
  करें। यह ट्यूटोरियल बताता है कि कैसे नियंत्रण को सम्मिलित किया जाए और Aspose.Words
  के साथ उसका कैप्शन सेट किया जाए।
og_image_alt: Word file showing an ActiveX command button inserted by Aspose.Words
og_title: प्रोग्रामेटिक रूप से वर्ड दस्तावेज़ बनाएं – एक्टिवएक्स बटन जोड़ें
schemas:
- author: Aspose
  dateModified: '2026-10-20'
  description: Create Word document programmatically and add a command button using
    Aspose.Words. Learn to insert an ActiveX control and set button caption.
  headline: Create Word document programmatically with an ActiveX button
  type: TechArticle
- description: Create Word document programmatically and add a command button using
    Aspose.Words. Learn to insert an ActiveX control and set button caption.
  name: Create Word document programmatically with an ActiveX button
  steps:
  - name: 'Open a terminal or Visual Studio and create a new console project:'
    text: 'Open a terminal or Visual Studio and create a new console project:'
  - name: 'Add the Aspose.Words package:'
    text: 'Add the Aspose.Words package:'
  - name: '(Optional) If you have a license file, place it in the project root and
      add the following line at the start of `Program.cs` to avoid evaluation watermarks:'
    text: '(Optional) If you have a license file, place it in the project root and
      add the following line at the start of `Program.cs` to avoid evaluation watermarks:'
  - name: Open `ActiveXCommandButton.docx` in Microsoft Word.
    text: Open `ActiveXCommandButton.docx` in Microsoft Word.
  - name: Switch to **Design Mode** (Developer tab → **Design Mode**) to see the button’s
      borders.
    text: Switch to **Design Mode** (Developer tab → **Design Mode**) to see the button’s
      borders.
  - name: If the button does not appear, check that the **Developer** tab is enabled
      and that your Word version supports ActiveX controls.
    text: If the button does not appear, check that the **Developer** tab is enabled
      and that your Word version supports ActiveX controls.
  - name: For macro‑enabled files (`.docm`), ensure the macro name in `OnClick` matches
      a VBA routine; otherwise Word will display a security warning.
    text: For macro‑enabled files (`.docm`), ensure the macro name in `OnClick` matches
      a VBA routine; otherwise Word will display a security warning.
  type: HowTo
tags:
- Aspose.Words
- C#
- ActiveX
- Word automation
title: एक ActiveX बटन के साथ प्रोग्रामेटिक रूप से Word दस्तावेज़ बनाएं
url: /hi/net/working-with-oleobjects-and-activex/create-word-document-programmatically-with-an-activex-button/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# ActiveX बटन के साथ प्रोग्रामेटिक रूप से Word दस्तावेज़ बनाएं

Aspose.Words का उपयोग करके प्रोग्रामेटिकली Word दस्तावेज़ बनाएं, फिर एक कमांड बटन जोड़ें जिसे उपयोगकर्ता क्लिक कर सकें। यह गाइड आपको ActiveX कंट्रोल डालने, उसकी प्रॉपर्टीज़ कॉन्फ़िगर करने, और परिणाम को **.docx** फ़ाइल के रूप में सहेजने की प्रक्रिया दिखाता है।

आप एक पूर्ण, चलाने योग्य उदाहरण देखेंगे जिसे आप कंसोल एप्लिकेशन में कॉपी कर सकते हैं। ट्यूटोरियल के अंत तक आप एक ऐसा Word फ़ाइल जेनरेट कर पाएंगे जिसमें पूरी तरह कार्यशील कमांड बटन हो, और आप समझेंगे कि **add command button**, **add activex control**, **insert activex button**, और **set button caption** को अपने C# कोड से बाहर निकले बिना कैसे लागू किया जाता है।

## आवश्यकताएँ

* .NET 6.0 SDK या बाद का संस्करण स्थापित हो  
* Visual Studio 2022 (या कोई भी C#‑compatible IDE)  
* Aspose.Words for .NET लाइसेंस फ़ाइल (इस उदाहरण के लिए फ्री ट्रायल काम करता है)  
* C# और .NET प्रोजेक्ट सिस्टम की बुनियादी समझ  

ActiveX सपोर्ट लाइब्रेरी में ही निर्मित होने के कारण **Aspose.Words** के अलावा कोई अतिरिक्त NuGet पैकेज आवश्यक नहीं है।

## चरण 1: प्रोजेक्ट सेट अप करें और Aspose.Words जोड़ें

1. टर्मिनल या Visual Studio खोलें और एक नया कंसोल प्रोजेक्ट बनाएं:

   ```bash
   dotnet new console -n WordActiveXDemo
   cd WordActiveXDemo
   ```

2. Aspose.Words पैकेज जोड़ें:

   ```bash
   dotnet add package Aspose.Words
   ```

3. (वैकल्पिक) यदि आपके पास लाइसेंस फ़ाइल है, तो उसे प्रोजेक्ट रूट में रखें और `Program.cs` की शुरुआत में नीचे दिया गया लाइन जोड़ें ताकि इवैल्यूएशन वॉटरमार्क न दिखें:

   ```csharp
   Aspose.Words.License license = new Aspose.Words.License();
   license.SetLicense("Aspose.Words.lic");
   ```

## चरण 2: प्रोग्रामेटिकली Word दस्तावेज़ बनाएं – दस्तावेज़ को इनिशियलाइज़ करें

पहला ऑपरेशन **प्रोग्रामेटिकली Word दस्तावेज़ बनाना** है। आप यह `Document` ऑब्जेक्ट और `DocumentBuilder` को इंस्टैंसिएट करके करते हैं, जो आपको दस्तावेज़ की सामग्री संपादित करने की अनुमति देता है।

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;   // Provides ActiveX control types
using System.Drawing;        // For Point and Size structs

// Initialize a new blank document
Document document = new Document();

// DocumentBuilder gives a cursor‑based API for inserting elements
DocumentBuilder builder = new DocumentBuilder(document);
```

`Document` पूरे फ़ाइल का प्रतिनिधित्व करता है, जबकि `DocumentBuilder` एक कर्सर रखता है जिसे आप दस्तावेज़ में किसी भी स्थान पर ले जा सकते हैं। यह विभाजन API को साफ़ रखता है और आपको बाद में **add activex control** करने की सुविधा देता है बिना लो‑लेवल स्ट्रक्चर को मैन्युअली मैनेज किए।

## चरण 3: कमांड बटन जोड़ें – ActiveX कंट्रोल डालना

अब आप `OleControlType.CommandButton` प्रकार के ActiveX कंट्रोल को डालकर **add command button** करेंगे। `InsertForms2OleControl` मेथड को कंट्रोल टाइप, लोकेशन (`Point`), और साइज (`Size`) की आवश्यकता होती है।

```csharp
// Define where the button will appear (X = 100 pt, Y = 150 pt)
Point buttonPosition = new Point(100, 150);

// Define the button dimensions (width = 120 pt, height = 30 pt)
Size buttonSize = new Size(120, 30);

// Insert the ActiveX command button at the current cursor location
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    OleControlType.CommandButton, // control type
    buttonPosition,              // position
    buttonSize);                 // size
```

ऊपर दिया गया कॉल आपके द्वारा निर्दिष्ट सटीक कॉर्डिनेट्स पर दस्तावेज़ में **insert activex button** करता है। कॉर्डिनेट्स पॉइंट्स में मापे जाते हैं (1 pt ≈ 1/72 in)। यदि आपको बटन किसी विशिष्ट पैराग्राफ़ में चाहिए, तो पहले बिल्डर का कर्सर मूव करें:

```csharp
builder.Writeln("Click the button below:");
builder.MoveToDocumentEnd(); // places the cursor after the paragraph
```

## चरण 4: बटन कैप्शन सेट करें – कमांड बटन टेक्स्ट को कस्टमाइज़ करना

बिना लेबल वाला बटन भ्रमित करता है, इसलिए आप **set button caption** करके इसे अर्थपूर्ण बनायेंगे। `Caption` प्रॉपर्टी बटन पर दिखने वाले टेक्स्ट को निर्धारित करती है, जबकि `Name` कंट्रोल को एक प्रोग्रामेटिक पहचानकर्ता देता है।

```csharp
// Give the button a unique name for later reference
commandButton.Name = "btnSubmit";

// Set the visible text on the button
commandButton.Caption = "Submit";

// Optional: assign a macro name that Word will call when the button is clicked
commandButton.OnClick = "SubmitForm()";
```

यदि आप बाद में दस्तावेज़ को मैक्रो‑सक्षम फॉर्मेट (`.docm`) में एक्सपोर्ट करते हैं, तो `OnClick` वैल्यू को VBA मैक्रो नाम से मेल खाना चाहिए। साधारण `.docx` के लिए, यह प्रॉपर्टी संग्रहीत रहती है लेकिन निष्पादित नहीं होती, जो अधिकांश ऑटोमेशन परिदृश्यों के लिए ठीक है।

## चरण 5: ActiveX बटन वाले दस्तावेज़ को सहेजें

कंट्रोल को कॉन्फ़िगर करने के बाद, आप **save the document** कर सकते हैं। ऐसी डायरेक्टरी चुनें जहाँ आपके पास लिखने की अनुमति हो, और अधिकतम संगतता के लिए `.docx` एक्सटेंशन का उपयोग करें।

```csharp
// Replace with your desired output folder
string outputPath = Path.Combine(Environment.CurrentDirectory, "ActiveXCommandButton.docx");

// Save the document to disk
document.Save(outputPath);
```

जब आप उत्पन्न फ़ाइल को Microsoft Word में खोलेंगे, तो आप निर्दिष्ट कॉर्डिनेट्स पर **Submit** लेबल वाला बटन देखेंगे। डेस्कटॉप क्लाइंट में बटन पर क्लिक करने से `SubmitForm` मैक्रो चलाने की कोशिश होगी (यदि वह मौजूद है)।

## चरण 6: परिणाम सत्यापित करें और सामान्य समस्याओं का समाधान करें

1. `ActiveXCommandButton.docx` को Microsoft Word में खोलें।  
2. **Design Mode** (Developer टैब → **Design Mode**) पर स्विच करें ताकि बटन की बॉर्डर दिखे।  
3. यदि बटन नहीं दिख रहा है, तो जांचें कि **Developer** टैब सक्षम है और आपका Word संस्करण ActiveX कंट्रोल्स को सपोर्ट करता है।  
4. मैक्रो‑सक्षम फ़ाइलों (`.docm`) के लिए, `OnClick` में मैक्रो नाम को VBA रूटीन से मिलाएँ; अन्यथा Word एक सुरक्षा चेतावनी दिखाएगा।

### प्रो टिप

ActiveX कंट्रोल्स केवल Windows पर ही काम करते हैं। यदि आपको क्रॉस‑प्लेटफ़ॉर्म इंटरैक्टिविटी चाहिए, तो ActiveX बटन के बजाय **Content Controls** (`RichTextContentControl`) का उपयोग करने पर विचार करें।

## पूर्ण स्रोत कोड

नीचे पूर्ण, तैयार‑से‑चलाने वाला प्रोग्राम दिया गया है। इसे `Program.cs` में कॉपी करें और `dotnet run` चलाएँ।

```csharp
using System;
using System.IO;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Optional: apply a license to remove evaluation watermarks
        // var license = new Aspose.Words.License();
        // license.SetLicense("Aspose.Words.lic");

        // Step 2: Create a new blank document
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Insert a paragraph to give context
        builder.Writeln("Please click the button below to submit the form:");
        builder.MoveToDocumentEnd();

        // Step 3: Add command button – insert ActiveX control
        Point position = new Point(100, 150);
        Size size = new Size(120, 30);
        Forms2OleControl commandButton = builder.InsertForms2OleControl(


## अब आप आगे क्या सीखें?

निम्नलिखित ट्यूटोरियल्स इस गाइड में दिखाए गए तकनीकों पर आधारित निकट संबंधित विषयों को कवर करते हैं। प्रत्येक संसाधन में पूर्ण कार्यशील कोड उदाहरण और चरण‑दर‑चरण व्याख्याएँ शामिल हैं, जो आपको अतिरिक्त API फीचर्स में महारत हासिल करने और अपने प्रोजेक्ट्स में वैकल्पिक इम्प्लीमेंटेशन अप्रोचेज़ को एक्सप्लोर करने में मदद करती हैं।

- [ActiveX बटन के साथ Word दस्तावेज़ बनाएं – C# गाइड](/words/english/net/working-with-oleobjects-and-activex/create-word-document-with-activex-button-c-guide/)
- [Aspose.Words के साथ Word दस्तावेज़ में कमांड बटन जोड़ें – पूर्ण गाइड](/words/english/net/working-with-oleobjects-and-activex/add-command-button-to-word-document-with-aspose-words-comple/)
- [Aspose.Words के साथ Word दस्तावेज़ बटन बनाएं – पूर्ण कोड उदाहरण](/words/english/net/working-with-oleobjects-and-activex/create-word-document-button-with-aspose-words-full-code-exam/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}