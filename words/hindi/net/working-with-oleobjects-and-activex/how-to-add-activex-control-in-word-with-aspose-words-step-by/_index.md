---
category: general
date: 2026-08-07
description: C# का उपयोग करके Word दस्तावेज़ में ActiveX नियंत्रण कैसे जोड़ें, सीखें।
  इसमें बटन के साथ मैक्रो को जोड़ना और क्लिक करने योग्य बटन वाले Word उदाहरण शामिल
  हैं।
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to add activex control
- associate macro with button
- add clickable button word
- add command button word
language: hi
lastmod: 2026-08-07
og_description: Aspose.Words का उपयोग करके Word दस्तावेज़ में ActiveX नियंत्रण कैसे
  जोड़ें। इस गाइड का पालन करके बटन डालें, बटन के साथ मैक्रो जोड़ें, और क्लिक करने
  योग्य बटन शब्द जोड़ें।
og_image_alt: Screenshot showing a Word document with an ActiveX command button inserted
  via Aspose.Words
og_title: Word में ActiveX कंट्रोल कैसे जोड़ें – पूर्ण C# ट्यूटोरियल
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: Learn how to add activex control in a Word document using C#. Includes
    associate macro with button and add clickable button word examples.
  headline: how to add activex control in Word with Aspose.Words – step‑by‑step guide
  type: TechArticle
- description: Learn how to add activex control in a Word document using C#. Includes
    associate macro with button and add clickable button word examples.
  name: how to add activex control in Word with Aspose.Words – step‑by‑step guide
  steps:
  - name: Why each line matters
    text: '| Line | Purpose | |------|---------| | `Document doc = new Document();`
      | Instantiates a fresh Word package in memory. | | `DocumentBuilder builder
      = new DocumentBuilder(doc);` | Provides a fluent API for inserting content,
      including ActiveX controls. | | `InsertForms2OleControl` | The only Aspose.'
  - name: Common pitfalls when associating a macro
    text: '* **Macro security settings** – If the document is opened on a machine
      with strict security policies, the macro may be blocked. Provide instructions
      to lower the security level or sign the macro. * **Naming conflicts** – The
      macro name must be unique within the document’s VBA project; otherwise Word'
  - name: 'Edge case: Long captions'
    text: Word truncates captions that exceed the button’s width. To avoid clipping,
      either increase the width argument in `InsertForms2OleControl` or shorten the
      text. Testing with different languages (e.g., German or Japanese) is advisable
      because character width varies.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: Aspose.Words के साथ Word में ActiveX कंट्रोल कैसे जोड़ें – चरण‑दर‑चरण मार्गदर्शिका
url: /hi/net/working-with-oleobjects-and-activex/how-to-add-activex-control-in-word-with-aspose-words-step-by/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word में Aspose.Words के साथ ActiveX कंट्रोल कैसे जोड़ें

यदि आपको प्रोग्रामेटिक रूप से Microsoft Word फ़ाइल में **how to add activex control** जोड़ने की आवश्यकता है, तो यह ट्यूटोरियल Aspose.Words for .NET का उपयोग करके सटीक चरण दिखाता है। आप देखेंगे कि कैसे एक कमांड बटन डालें, उसका कैप्शन सेट करें, और **associate macro with button** ताकि उपयोगकर्ता क्लिक करने पर कंट्रोल प्रतिक्रिया दे। अंत तक आपके पास एक macro‑enabled `.docm` फ़ाइल होगी जिसमें पूरी तरह कार्यात्मक बटन होगा।

इंटरैक्टिव टेम्पलेट जैसे लोन एप्लिकेशन, कर्मचारी ऑनबोर्डिंग फ़ॉर्म, या ऑटोमेटेड रिपोर्ट बनाते समय ActiveX बटन जोड़ना एक सामान्य आवश्यकता है। यह गाइड कोड की प्रत्येक पंक्ति को समझाता है, **why** प्रत्येक चरण क्यों महत्वपूर्ण है, और संभावित सामान्य समस्याओं को कवर करता है।

## आवश्यकताएँ

* .NET 6 (या .NET Core 3.1 / .NET Framework 4.8) स्थापित हो।
* एक वैध Aspose.Words for .NET लाइसेंस या अस्थायी इवैल्यूएशन कुंजी।
* Visual Studio 2022 (या कोई भी IDE जो C# को सपोर्ट करता हो)।
* Word मैक्रो (VBA) की बुनियादी समझ, यदि आप वह मैक्रो लिखने वाले हैं जो बटन ट्रिगर करेगा।

> **Pro tip:** जब आप सैंपल चलाते हैं, तो आउटपुट को ऐसी फ़ोल्डर में सेव करें जहाँ आपके पास लिखने की अनुमति हो, अन्यथा `doc.Save` एक अपवाद फेंकेगा।

## Aspose.Words का उपयोग करके Word दस्तावेज़ में ActiveX कंट्रोल कैसे जोड़ें

समाधान का मूल एक छोटा C# प्रोग्राम है जो नया दस्तावेज़ बनाता है, ActiveX **CommandButton** कंट्रोल डालता है, और फ़ाइल को macro‑enabled दस्तावेज़ (`.docm`) के रूप में सहेजता है। कोड पूर्ण है और कॉपी‑पेस्ट के लिए तैयार है।

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1: Create a new blank document and a builder to edit it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Insert an ActiveX CommandButton control (Forms2OleControl)
        // Parameters: control type, left, top, width, height (in points)
        Forms2OleControl commandButton = builder.InsertForms2OleControl(
            OleControlType.CommandButton,
            0,   // left position (points)
            0,   // top position (points)
            150, // width (points)
            30   // height (points)
        );

        // Step 3: Set the button's visible caption – this is the add clickable button word
        commandButton.Caption = "Click Me";

        // Step 4 (optional): Associate a macro with the button's click action
        // This demonstrates how to associate macro with button
        commandButton.OnAction = "MyMacro";

        // Step 5: Save the document as a macro‑enabled file to preserve the button reference
        // The file extension .docm tells Word to keep ActiveX controls and macros
        doc.Save("CommandButton.docm");
    }
}
```

### प्रत्येक पंक्ति क्यों महत्वपूर्ण है

| पंक्ति | उद्देश्य |
|--------|----------|
| `Document doc = new Document();` | मेमोरी में एक नया Word पैकेज बनाता है। |
| `DocumentBuilder builder = new DocumentBuilder(doc);` | सामग्री डालने के लिए, जिसमें ActiveX कंट्रोल शामिल हैं, एक सहज API प्रदान करता है। |
| `InsertForms2OleControl` | वह एकमात्र Aspose.Words मेथड है जो ActiveX कंट्रोल बनाता है; आप कंट्रोल प्रकार (`CommandButton`) और उसकी ज्यामिति निर्दिष्ट करते हैं। |
| `commandButton.Caption = "Click Me";` | **add clickable button word** सेट करता है जो अंतिम‑उपयोगकर्ता देखता है। बिना कैप्शन के बटन खाली दिखेगा। |
| `commandButton.OnAction = "MyMacro";` | **associate macro with button** – बताता है कि कंट्रोल क्लिक होने पर कौन सा VBA मैक्रो चलाना है। |
| `doc.Save("CommandButton.docm");` | दस्तावेज़ को macro‑enabled फ़ाइल के रूप में सहेजता है; सामान्य `.docx` कंट्रोल और मैक्रो को हटा देगा। |

> **Note:** निर्देशांक (बाएँ, ऊपर) पॉइंट्स में मापे जाते हैं (1 pt ≈ 1/72 in)। बटन को पृष्ठ पर जहाँ चाहिए वहाँ रखने के लिए इन्हें समायोजित करें।

## बटन के साथ मैक्रो कैसे जोड़ें

`OnAction` प्रॉपर्टी बटन को `MyMacro` नामक VBA मैक्रो से लिंक करती है। आपको अभी भी वह मैक्रो Word फ़ाइल के भीतर बनाना होगा, या तो मैन्युअल रूप से या प्रोग्रामेटिक रूप से VBA कोड इंजेक्ट करके (Aspose.Words VBA कोड नहीं लिखता)। यहाँ एक न्यूनतम मैक्रो है जिसे आप Word के **Developer → Visual Basic** एडिटर से जोड़ सकते हैं:

```vba
Sub MyMacro()
    MsgBox "Button clicked!", vbInformation, "ActiveX Demo"
End Sub
```

जब उपयोगकर्ता `CommandButton.docm` खोलता है और बटन पर क्लिक करता है, तो Word `MyMacro` चलाता है और एक संदेश बॉक्स दिखाता है। यदि मैक्रो सुरक्षा **Disable all macros without notification** पर सेट है, तो बटन निष्क्रिय दिखेगा। उपयोगकर्ताओं को दस्तावेज़ के लिए मैक्रो सक्षम करने या विश्वसनीय प्रमाणपत्र से मैक्रो साइन करने की सलाह दें।

### मैक्रो जोड़ते समय सामान्य समस्याएँ

* **मैक्रो सुरक्षा सेटिंग्स** – यदि दस्तावेज़ ऐसी मशीन पर खुलता है जहाँ सुरक्षा नीतियां कड़ी हैं, तो मैक्रो ब्लॉक हो सकता है। सुरक्षा स्तर कम करने या मैक्रो साइन करने के निर्देश प्रदान करें।
* **नामकरण टकराव** – मैक्रो नाम दस्तावेज़ के VBA प्रोजेक्ट में अद्वितीय होना चाहिए; अन्यथा Word “duplicate procedure name” त्रुटि देगा।
* **64‑bit बनाम 32‑bit Word** – ActiveX कंट्रोल समान रूप से काम करते हैं, लेकिन VBA एडिटर Office संस्करण के आधार पर अलग चेतावनी संदेश दिखा सकता है।

## Word फ़ॉर्म में क्लिक करने योग्य बटन शब्द कैसे जोड़ें

`Caption` प्रॉपर्टी वह टेक्स्ट है जो उपयोगकर्ता बटन पर देखते हैं। आप इसे आगे कस्टमाइज़ कर सकते हैं:

```csharp
commandButton.Caption = "Submit Form";
commandButton.Font.Size = 10;      // Adjust font size
commandButton.Font.Name = "Arial"; // Choose a readable font
```

यदि आपको कैप्शन को उपयोगकर्ता इनपुट के आधार पर गतिशील रूप से बदलना है, तो आप बाद में Word के ऑब्जेक्ट मॉडल के माध्यम से कंट्रोल तक पहुँच सकते हैं:

```vba
Sub UpdateButtonCaption()
    Dim btn As InlineShape
    Set btn = ActiveDocument.InlineShapes(1).OLEFormat.Object
    btn.Caption = "Updated Text"
End Sub
```

### किनारा मामला: लंबी कैप्शन

Word उन कैप्शन को ट्रंकेट कर देता है जो बटन की चौड़ाई से अधिक होते हैं। क्लिपिंग से बचने के लिए, `InsertForms2OleControl` में चौड़ाई तर्क बढ़ाएँ या टेक्स्ट को छोटा करें। विभिन्न भाषाओं (जैसे जर्मन या जापानी) के साथ परीक्षण करना सलाहनीय है क्योंकि अक्षर चौड़ाई भिन्न होती है।

## फ़ॉर्म ऑटोमेशन के लिए कमांड बटन शब्द कैसे जोड़ें

दृश्य कैप्शन के अलावा, **add command button word** अवधारणा कंट्रोल के प्रोग्रामेटिक नाम को दर्शाती है। Aspose.Words ActiveX कंट्रोल के लिए सीधे `Name` प्रॉपर्टी नहीं देता, लेकिन आप `AltText` फ़ील्ड सेट कर सकते हैं, जिसे Word कंट्रोल के पहचानकर्ता के रूप में मानता है:

```csharp
commandButton.AltText = "SubmitButton";
```

बाद में VBA में आप बटन को उसके `AltText` मान से रेफ़र कर सकते हैं:

```vba
Sub FindButton()
    Dim shp As Shape
    For Each shp In ActiveDocument.Shapes
        If shp.AlternativeText = "SubmitButton" Then
            MsgBox "Found the Submit button!"
        End If
    Next shp
End Sub
```

यह तकनीक तब उपयोगी होती है जब आपके पास कई बटन हों और आपको उन्हें प्रोग्रामेटिक रूप से अलग‑अलग पहचानना हो।

## पूर्ण कार्यशील उदाहरण

नीचे पूरा प्रोग्राम है जिसे आप कंसोल एप्लिकेशन के रूप में कंपाइल और रन कर सकते हैं। इसमें वैकल्पिक स्टाइलिंग, मैक्रो एसोसिएशन, और प्रत्येक चरण का विवरण देने वाला टिप्पणी ब्लॉक शामिल है।

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class AddActiveXButton
{
    static void Main()
    {
        // 1️⃣ Create a new document and a builder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Insert an ActiveX CommandButton.
        //    left=50pt, top=100pt places the button away from the margin.
        Forms2OleControl btn = builder.InsertForms2OleControl(
            OleControlType.CommandButton,
            50,   // left
            100,  // top
            200,  // width
            40    // height
        );

        // 3️⃣ Add clickable button word (caption) and style it.
        btn.Caption = "Submit Form";
        btn.Font.Size = 11;
        btn.Font.Name = "Calibri";

        // 4️⃣ Associate macro with button – this is how to associate macro with button.
        btn.OnAction = "SubmitMacro";

        // 5️⃣ Give the control a friendly identifier (add command button word).
        btn.AltText = "SubmitButton";

        // 6️⃣ Save as macro‑enabled document.
        doc.Save("SubmitForm.docm");
    }
}
```

**Expected result:** `SubmitForm.docm` को Microsoft Word में खोलने पर एक नीले‑बॉर्डर वाला बटन *Submit Form* लेबल के साथ दिखेगा। बटन पर क्लिक करने से VBA मैक्रो `SubmitMacro` चलेगा (यदि आपने दस्तावेज़ में मैक्रो जोड़ा है)। बटन को उसी `Forms2OleControl` ऑब्जेक्ट का उपयोग करके आगे मूव, रिसाइज़ या स्टाइल किया जा सकता है।

## समाधान का परीक्षण

1. C# कंसोल ऐप को बिल्ड और रन करें।  
2. उत्पन्न `SubmitForm.docm` को Word में खोलें।  
3. यदि पूछा जाए, तो मैक्रो सक्षम करें।  
4. *Submit Form* बटन पर क्लिक करें – आपको `SubmitMacro` में परिभाषित संदेश बॉक्स दिखना चाहिए।

यदि बटन दिखता है लेकिन कुछ नहीं करता, तो दोबारा जांचें कि मैक्रो नाम बिल्कुल मेल खाता है (`SubmitMacro`) और मैक्रो सुरक्षा निष्पादन को ब्लॉक नहीं कर रही है।

## अक्सर पूछे जाने वाले प्रश्न

| प्रश्न | उत्तर |
|--------|-------|
| *क्या मैं एक से अधिक ActiveX बटन जोड़ सकता हूँ?* | हाँ। `InsertForms2OleControl` को विभिन्न निर्देशांक के साथ कई बार कॉल करें। अलग‑अलग `OnAction` और `AltText` मानों का उपयोग करके उन्हें पहचानें। |
| *क्या ActiveX कंट्रोल Word Online में दिखाई देता है?* | नहीं। |

## अब आपको क्या सीखना चाहिए?

निम्नलिखित ट्यूटोरियल्स उन विषयों को कवर करते हैं जो इस गाइड में दर्शाए गए तकनीकों पर आधारित हैं। प्रत्येक संसाधन में पूर्ण कार्यशील कोड उदाहरण और चरण‑दर‑चरण व्याख्याएँ शामिल हैं, जिससे आप अतिरिक्त API सुविधाओं में महारत हासिल कर सकें और अपने प्रोजेक्ट्स में वैकल्पिक कार्यान्वयन दृष्टिकोणों का अन्वेषण कर सकें।

- [Aspose.Words for .NET में Document Builder का उपयोग करके सामग्री जोड़ें](/words/english/net/add-content-using-document-builder/)
- [Aspose.Words Shape Shadow ट्यूटोरियल – C# में Word Shape में शैडो जोड़ें](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)
- [Word दस्तावेज़ में नया सेक्शन जोड़ें | Aspose.Words for .NET](/words/english/net/document-sections/add-section/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}