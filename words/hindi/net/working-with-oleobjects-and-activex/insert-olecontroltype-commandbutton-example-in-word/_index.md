---
category: general
date: 2026-08-17
description: Aspose.Words का उपयोग करके Word में OleControlType.CommandButton का उदाहरण
  डालें। जानें कि प्रोग्रामेटिक रूप से Word दस्तावेज़ में फ़ॉर्म कंट्रोल कैसे जोड़ें।
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert olecontroltype.commandbutton example
- how to add form controls to word document
- Aspose.Words ActiveX button
- C# Word automation
- programmatic form controls
language: hi
lastmod: 2026-08-17
og_description: Aspose.Words के साथ Word में OleControlType.CommandButton का उदाहरण
  डालें। Word दस्तावेज़ में फ़ॉर्म कंट्रोल जोड़ने के लिए इस गाइड का पालन करें।
og_image_alt: Screenshot showing an ActiveX CommandButton inserted into a Word document
  using Aspose.Words
og_title: Word में OleControlType.CommandButton उदाहरण सम्मिलित करें
schemas:
- author: Aspose
  dateModified: '2026-08-17'
  description: Insert OleControlType.CommandButton example in Word using Aspose.Words.
    Learn how to add form controls to a Word document programmatically.
  headline: Insert OleControlType.CommandButton example in Word
  type: TechArticle
tags:
- Aspose.Words
- C#
- ActiveX
- Word automation
title: Word में OleControlType.CommandButton उदाहरण सम्मिलित करें
url: /hi/net/working-with-oleobjects-and-activex/insert-olecontroltype-commandbutton-example-in-word/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word में OleControlType.CommandButton उदाहरण सम्मिलित करें

यदि आपको Word फ़ाइल में **insert OleControlType.CommandButton example** सम्मिलित करने की आवश्यकता है, तो यह गाइड आपको दिखाएगा कि कैसे। आप Aspose.Words का उपयोग करके **how to add form controls to a Word document** सीखेंगे, एक पूर्ण, चलाने योग्य C# प्रोग्राम के साथ।

ActiveX बटन जैसे फ़ॉर्म कंट्रोल आपको इंटरैक्टिव Word टेम्पलेट बनाने की अनुमति देते हैं—जो अनुबंधों, प्रश्नावली, या आंतरिक टूल्स के लिए उपयोगी हैं। नीचे दिए गए चरण प्रोजेक्ट सेटअप से लेकर सहेजी गई `.docx` फ़ाइल में बटन सही ढंग से दिख रहा है, यह सत्यापित करने तक सब कुछ कवर करते हैं।

## आवश्यकताएँ

- .NET 6.0 SDK या बाद का संस्करण स्थापित हो  
- Visual Studio 2022 (या कोई भी C# IDE)  
- Aspose.Words for .NET लाइसेंस या एक मुफ्त अस्थायी लाइसेंस  
- C# और Word फ़ाइल अवधारणाओं की बुनियादी परिचितता  

> **Pro tip:** यदि आप मुफ्त ट्रायल का उपयोग कर रहे हैं, तो लाइसेंस फ़ाइल को executable के समान फ़ोल्डर में रखें और इसे `Main` की शुरुआत में लोड करें।

## चरण 1: एक नया कंसोल प्रोजेक्ट बनाएं और Aspose.Words जोड़ें

एक टर्मिनल खोलें और चलाएँ:

```bash
dotnet new console -n OleCommandButtonDemo
cd OleCommandButtonDemo
dotnet add package Aspose.Words
```

यह एक साफ़ प्रोजेक्ट बनाता है और नवीनतम Aspose.Words पैकेज को लाता है, जो `Document`, `DocumentBuilder`, और `InsertForms2OleControl` APIs प्रदान करता है, जो **insert OleControlType.CommandButton example** के लिए आवश्यक हैं।

## चरण 2: पूर्ण प्रोग्राम लिखें

`Program.cs` को निम्नलिखित कोड से बनाएं या बदलें। इसमें सभी आवश्यक `using` निर्देश, लाइसेंस लोडिंग, और मूल स्निपेट में दिखाए गए चार‑चरणीय वर्कफ़्लो शामिल हैं।

```csharp
using System;
using System.Drawing;               // For Rectangle
using Aspose.Words;
using Aspose.Words.Drawing;          // For OleControlType

class Program
{
    static void Main()
    {
        // -------------------------------------------------
        // Optional: load a trial or commercial license.
        // -------------------------------------------------
        // var license = new Aspose.Words.License();
        // license.SetLicense("Aspose.Words.lic");

        // -------------------------------------------------
        // Step 1: Create a new blank document
        // -------------------------------------------------
        Document doc = new Document();

        // -------------------------------------------------
        // Step 2: Initialize a DocumentBuilder to work with the document
        // -------------------------------------------------
        DocumentBuilder builder = new DocumentBuilder(doc);

        // -------------------------------------------------
        // Step 3: Insert an ActiveX CommandButton control
        // -------------------------------------------------
        // OleControlType.CommandButton creates a CommandButton.
        // "ClickMe" is the control's name.
        // The Rectangle defines the button's position (x, y) and size (width, height).
        builder.InsertForms2OleControl(
            OleControlType.CommandButton,
            "ClickMe",
            new Rectangle(100, 100, 80, 30));

        // -------------------------------------------------
        // Step 4: Save the document containing the ActiveX button
        // -------------------------------------------------
        string outputPath = "ActiveXButton.docx";
        doc.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

### प्रत्येक पंक्ति क्यों महत्वपूर्ण है

* **License loading** – यह सुनिश्चित करता है कि आप मूल्यांकन प्रतिबंधों से सीमित न हों।  
* **`Document doc = new Document();`** – सभी Word सामग्री के लिए कंटेनर बनाता है; यह **insert OleControlType.CommandButton example** की नींव है।  
* **`DocumentBuilder builder = new DocumentBuilder(doc);`** – टेक्स्ट, इमेज और कंट्रोल जोड़ने के लिए एक फ़्लुएंट API प्रदान करता है।  
* **`InsertForms2OleControl`** – वह मुख्य मेथड जो **how to add form controls to a Word document** को लागू करता है। `OleControlType.CommandButton` enum मान Aspose.Words को एक ActiveX बटन बनाने के लिए बताता है।  
* **`new Rectangle(100, 100, 80, 30)`** – बटन को बाएँ और ऊपर के मार्जिन से 100 pts की दूरी पर रखता है, जिसकी चौड़ाई 80 pts और ऊँचाई 30 pts है। अपने लेआउट के अनुसार इन संख्याओं को समायोजित करें।  
* **`doc.Save`** – .docx फ़ाइल को डिस्क पर लिखता है; अब फ़ाइल में एम्बेडेड बटन शामिल है।  

## चरण 3: प्रोग्राम बनाएं और चलाएँ

प्रोजेक्ट फ़ोल्डर से, निष्पादित करें:

```bash
dotnet run
```

आपको कंसोल संदेश दिखना चाहिए:

```
Document saved to ActiveXButton.docx
```

`ActiveXButton.docx` को Microsoft Word में खोलें। आपको पृष्ठ के मध्य में लगभग स्थित **ClickMe** लेबल वाला बटन दिखाई देगा। बटन पर क्लिक करने से डिफ़ॉल्ट ActiveX व्यवहार ट्रिगर होता है (जो आमतौर पर कोई ऑपरेशन नहीं करता जब तक आप कोई मैक्रो संलग्न न करें)।

![insert olecontroltype.commandbutton example](/images/activex-button.png "Word दस्तावेज़ में सम्मिलित ActiveX CommandButton")

*Image alt text:* insert olecontroltype.commandbutton example – एक ActiveX CommandButton जो Word दस्तावेज़ में प्रदर्शित है।

## चरण 4: बटन को अनुकूलित करना (वैकल्पिक)

बुनियादी **insert OleControlType.CommandButton example** एक डिफ़ॉल्ट बटन बनाता है। आप उसके कैप्शन, फ़ॉन्ट को बदल सकते हैं, या नीचे OLE ऑब्जेक्ट को संपादित करके मैक्रो भी संलग्न कर सकते हैं। नीचे सम्मिलन के बाद बटन के कैप्शन को बदलने का संक्षिप्त तरीका दिया गया है:

```csharp
// Retrieve the first shape (our button) from the document
Shape buttonShape = (Shape)doc.GetChild(NodeType.Shape, 0, true);

// Access the OLE format and set the caption
buttonShape.OleFormat.GetControl().SetProperty("Caption", "Submit");
```

> **Note:** OLE प्रॉपर्टीज़ का प्रत्यक्ष हेरफेर करने के लिए अंतर्निहित COM इंटरफ़ेस की समझ आवश्यक है। अधिकांश मामलों में, डिफ़ॉल्ट कैप्शन पर्याप्त है।

## चरण 5: सामान्य समस्याएँ और उन्हें कैसे टालें

| समस्या | क्यों होता है | समाधान |
|-------|----------------|-----|
| बटन Word में नहीं दिख रहा है | दस्तावेज़ को `.docx` के रूप में सहेजा गया था लेकिन ऐसे व्यूअर में खोला गया जो OLE कंट्रोल्स को हटाता है (जैसे, Google Docs)। | फ़ाइल को Microsoft Word या Word Online में संपादन अधिकारों के साथ खोलें। |
| `ArgumentOutOfRangeException` रनटाइम त्रुटि | `Rectangle` निर्देशांक पृष्ठ मार्जिन के बाहर हैं। | पृष्ठ आकार के भीतर मान उपयोग करें (उदाहरण के लिए, A4 के लिए 0‑500)। |
| लाइसेंस अपवाद | ट्रायल लाइसेंस 30 दिनों के बाद समाप्त हो जाता है। | एक वैध लाइसेंस फ़ाइल लोड करें या Aspose से विस्तारित ट्रायल का अनुरोध करें। |

## चरण 6: यह उदाहरण बड़े ऑटोमेशन प्रोजेक्ट्स में कैसे फिट होता है

जब आपको **how to add form controls to Word document** बड़े पैमाने पर चाहिए—जैसे सैकड़ों अनुबंध टेम्पलेट बनाना—तो सम्मिलन लॉजिक को एक पुन: उपयोग योग्य मेथड में लपेटें:

```csharp
static void AddCommandButton(DocumentBuilder builder, string name, Rectangle bounds)
{
    builder.InsertForms2OleControl(OleControlType.CommandButton, name, bounds);
}
```

आप फिर `AddCommandButton` को लूप्स के भीतर कॉल कर सकते हैं जो डेटा पंक्तियों को प्रोसेस करते हैं, यह सुनिश्चित करते हुए कि प्रत्येक उत्पन्न दस्तावेज़ में एक अनोखा बटन नाम हो (जैसे, `Approve_001`, `Approve_002`)।

## निष्कर्ष

अब आपके पास एक पूर्ण **insert OleControlType.CommandButton example** है जो Aspose.Words for .NET का उपयोग करके **how to add form controls to a Word document** को दर्शाता है। ट्यूटोरियल ने प्रोजेक्ट सेटअप, पूर्ण स्रोत कोड, अनुकूलन टिप्स, और सामान्य समस्या निवारण चरणों को कवर किया।

अब आप आगे खोज सकते हैं:

- अन्य कंट्रोल प्रकार जोड़ना जैसे **CheckBox** या **ComboBox** (`OleControlType.CheckBox`, `OleControlType.ComboBox`)।  
- बटन को VBA मैक्रो से बाइंड करना ताकि अधिक इंटरैक्टिविटी मिल सके।  
- फ़ॉर्म फ़ील्ड्स को संरक्षित रखते हुए समान दस्तावेज़ से PDFs जनरेट करना।

विभिन्न आकार, स्थितियों, और कंट्रोल नामों के साथ प्रयोग करें ताकि आपका विशिष्ट उपयोग केस फिट हो सके। कोडिंग का आनंद लें!

## आगे आप क्या सीखें?

निम्नलिखित ट्यूटोरियल्स उन निकट संबंधित विषयों को कवर करते हैं जो इस गाइड में प्रदर्शित तकनीकों पर आधारित हैं। प्रत्येक संसाधन में पूर्ण कार्यशील कोड उदाहरण और चरण-दर-चरण व्याख्याएँ शामिल हैं जो आपको अतिरिक्त API सुविधाओं में महारत हासिल करने और अपने प्रोजेक्ट्स में वैकल्पिक कार्यान्वयन दृष्टिकोणों का अन्वेषण करने में मदद करती हैं।

- [Word दस्तावेज़ में कॉम्बो बॉक्स फ़ॉर्म फ़ील्ड सम्मिलित करें](/words/english/net/add-content-using-documentbuilder/insert-combo-box-form-field/)
- [Word दस्तावेज़ में चेक बॉक्स फ़ॉर्म फ़ील्ड सम्मिलित करें](/words/english/net/add-content-using-documentbuilder/insert-check-box-form-field/)
- [Word दस्तावेज़ में टेक्स्ट इनपुट फ़ॉर्म फ़ील्ड सम्मिलित करें](/words/english/net/add-content-using-documentbuilder/insert-text-input-form-field/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}