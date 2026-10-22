---
category: general
date: 2026-09-11
description: Aspose.Words DocumentBuilder का उपयोग करके कोड में forms2olecontrol कैसे
  बनाएं, सीखें। यह चरण‑दर‑चरण गाइड ActiveX कमांड बटन सम्मिलित करना, setOleClassName
  का उपयोग, और आकार निर्धारण को कवर करता है।
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create forms2olecontrol in code
- ActiveX command button
- Aspose.Words DocumentBuilder
- setOleClassName method
- Forms2OleControl size
language: hi
lastmod: 2026-09-11
og_description: Aspose.Words के साथ कोड में forms2olecontrol बनाएं। ActiveX कमांड
  बटन डालने, उसका क्लास नाम सेट करने और आकार समायोजित करने के लिए इस गाइड का पालन
  करें।
og_image_alt: Screenshot of a Word document showing a newly created ActiveX command
  button inserted via code
og_title: कोड में forms2olecontrol बनाएं – पूर्ण Aspose.Words गाइड
schemas:
- author: Aspose
  dateModified: '2026-09-11'
  description: Learn how to create forms2olecontrol in code using Aspose.Words DocumentBuilder.
    This step‑by‑step guide covers ActiveX command button insertion, setOleClassName
    usage, and sizing.
  headline: How to create forms2olecontrol in code with Aspose.Words
  type: TechArticle
- description: Learn how to create forms2olecontrol in code using Aspose.Words DocumentBuilder.
    This step‑by‑step guide covers ActiveX command button insertion, setOleClassName
    usage, and sizing.
  name: How to create forms2olecontrol in code with Aspose.Words
  steps:
  - name: Initialise the DocumentBuilder
    text: The `DocumentBuilder` class is the entry point for most document‑generation
      tasks in Aspose.Words. It gives you methods to add text, images, tables, and,
      importantly for this tutorial, OLE controls.
  - name: Insert the Forms2OleControl
    text: The `insertForms2OleControl` method returns a `Forms2OleControl` object.
      This object represents the OLE control placeholder that Word will render as
      an ActiveX button.
  - name: Specify the ActiveX class with setOleClassName
    text: Word needs to know which type of ActiveX control to render. The class name
      for a standard command button is `"Forms.CommandButton.1"`.
  - name: Adjust the Forms2OleControl size
    text: A button that is too small or too large looks unprofessional. You can control
      its dimensions with `setWidth` and `setHeight`.
  - name: Save the document and test
    text: After configuring the control, save the document to a location of your choice.
  - name: When to use Forms2OleControl vs. Content Controls
    text: If you only need simple data entry (e.g., a plain text field), Word’s built‑in
      content controls are lighter weight. Use `Forms2OleControl` when you require
      full ActiveX functionality such as event handling or custom VBA interaction.
  type: HowTo
tags:
- Aspose.Words
- C#
- ActiveX
title: Aspose.Words के साथ कोड में forms2olecontrol कैसे बनाएं
url: /hi/java/using-document-elements/how-to-create-forms2olecontrol-in-code-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words के साथ कोड में forms2olecontrol कैसे बनाएं

यदि आपको **कोड में forms2olecontrol बनाना** है, तो यह गाइड Aspose.Words .NET API का उपयोग करके इसे कैसे किया जाए, दिखाता है। चाहे आप एक ActiveX कमांड बटन की आवश्यकता वाले टेम्पलेट को ऑटोमेट कर रहे हों या आप प्रोग्रामेटिक रूप से Word दस्तावेज़ को समृद्ध बनाना चाहते हों, नीचे दिए गए चरण नियंत्रण को सम्मिलित करने से लेकर उसकी उपस्थिति को कॉन्फ़िगर करने तक सब कुछ कवर करते हैं।

इस ट्यूटोरियल में आप सीखेंगे कि **Aspose.Words DocumentBuilder** का उपयोग करके **ActiveX कमांड बटन** कैसे डालें, **setOleClassName मेथड** से उसकी क्लास सेट करें, और **Forms2OleControl का आकार** कैसे समायोजित करें। कोई बाहरी टूल आवश्यक नहीं—सिर्फ एक .NET विकास वातावरण और Aspose.Words लाइब्रेरी चाहिए।

## पूर्वापेक्षाएँ

शुरू करने से पहले सुनिश्चित करें कि आपके पास है:

* .NET 6.0 या बाद का संस्करण स्थापित (कोड .NET Framework 4.7+ के साथ भी काम करता है)
* Aspose.Words for .NET का नवीनतम NuGet पैकेज
* C# की बुनियादी समझ और Word दस्तावेज़ों में ActiveX नियंत्रणों का概念

यदि इनमें से कोई भी अनुपलब्ध है, तो NuGet पैकेज इस प्रकार स्थापित करें:

```bash
dotnet add package Aspose.Words
```

## इस ट्यूटोरियल में क्या कवर किया गया है

* `DocumentBuilder` इंस्टेंस बनाना
* `Forms2OleControl` सम्मिलित करना (ActiveX कमांड बटन का मूल ऑब्जेक्ट)
* `setOleClassName` के साथ सही क्लास नाम असाइन करना
* **Forms2OleControl आकार** प्रॉपर्टीज़ के माध्यम से दृश्य चौड़ाई और ऊँचाई सेट करना
* दस्तावेज़ को सहेजना और परिणाम की पुष्टि करना

गाइड के अंत तक आपके पास एक पूरी तरह कार्यशील Word फ़ाइल होगी, जिसमें एक क्लिक करने योग्य बटन होगा जिसे आप आगे कस्टमाइज़ या VBA मैक्रो से बाइंड कर सकते हैं।

---

## कोड में forms2olecontrol बनाने के चरण‑दर‑चरण

### चरण 1: DocumentBuilder को प्रारंभ करें

`DocumentBuilder` क्लास Aspose.Words में अधिकांश दस्तावेज़‑जनरेशन कार्यों का प्रवेश बिंदु है। यह आपको टेक्स्ट, इमेज, टेबल, और इस ट्यूटोरियल के लिए महत्वपूर्ण OLE नियंत्रण जोड़ने के मेथड प्रदान करता है।

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create a new empty document
Document doc = new Document();

// Initialise the builder for the document
DocumentBuilder builder = new DocumentBuilder(doc);
```

**यह क्यों महत्वपूर्ण है:**  
`DocumentBuilder` दस्तावेज़ के भीतर वर्तमान कर्सर स्थिति को बनाए रखता है। इसे जल्दी बनाकर आप सुनिश्चित करते हैं कि बाद में किया गया कोई भी सम्मिलन—जैसे **ActiveX कमांड बटन**—बिल्कुल वहीँ दिखाई दे जहाँ आप चाहते हैं।

### चरण 2: Forms2OleControl सम्मिलित करें

`insertForms2OleControl` मेथड एक `Forms2OleControl` ऑब्जेक्ट लौटाता है। यह ऑब्जेक्ट OLE नियंत्रण प्लेसहोल्डर को दर्शाता है जिसे Word एक ActiveX बटन के रूप में रेंडर करेगा।

```csharp
// Insert the Forms2OleControl at the current cursor location
Forms2OleControl commandButton = builder.InsertForms2OleControl();
```

**यह क्यों महत्वपूर्ण है:**  
इस कॉल के बिना आप नियंत्रण की प्रॉपर्टीज़ को नहीं बदल सकते। लौटाया गया `Forms2OleControl` आपको **setOleClassName मेथड**, आकार एट्रिब्यूट्स, और अन्य OLE‑विशिष्ट सेटिंग्स तक पूरी पहुँच देता है।

### चरण 3: setOleClassName से ActiveX क्लास निर्दिष्ट करें

Word को यह जानना आवश्यक है कि कौन सा ActiveX नियंत्रण रेंडर करना है। एक मानक कमांड बटन के लिए क्लास नाम `"Forms.CommandButton.1"` है।

```csharp
// Tell Word that this OLE control is a CommandButton
commandButton.SetOleClassName("Forms.CommandButton.1");
```

**यह क्यों महत्वपूर्ण है:**  
`setOleClassName` मेथड सामान्य OLE प्लेसहोल्डर और विशिष्ट **ActiveX कमांड बटन** के बीच पुल का काम करता है। गलत क्लास नाम देने पर खाली ऑब्जेक्ट या दस्तावेज़ खोलते समय रन‑टाइम त्रुटि आती है।

### चरण 4: Forms2OleControl का आकार समायोजित करें

बहुत छोटा या बहुत बड़ा बटन अनप्रोफेशनल दिखता है। आप `setWidth` और `setHeight` के माध्यम से इसके आयाम नियंत्रित कर सकते हैं।

```csharp
// Set the visual dimensions (points) of the button
commandButton.SetWidth(80);   // width in points
commandButton.SetHeight(30);  // height in points
```

**यह क्यों महत्वपूर्ण है:**  
ये प्रॉपर्टीज़ **Forms2OleControl आकार** बनाती हैं। यह निर्धारित करती हैं कि बटन Word UI में कैसे दिखेगा और यह सुनिश्चित करती हैं कि जुड़ा हुआ मैक्रो पर्याप्त क्लिकेबल एरिया रखे।

### चरण 5: दस्तावेज़ सहेजें और परीक्षण करें

नियंत्रण को कॉन्फ़िगर करने के बाद, दस्तावेज़ को अपनी इच्छित जगह पर सहेजें।

```csharp
// Save the document as a .docx file
doc.Save("ActiveXButton.docx");
```

`ActiveXButton.docx` को Microsoft Word में खोलें। आपको “CommandButton1” (डिफ़ॉल्ट कैप्शन) लेबल वाला बटन दिखेगा। इसे क्लिक करने से कुछ नहीं होगा जब तक आप VBA मैक्रो न जोड़ें, लेकिन नियंत्रण स्वयं पूरी तरह कार्यशील है।

**अपेक्षित आउटपुट:**  

![Word दस्तावेज़ जिसमें सम्मिलित ActiveX कमांड बटन है](/images/activeX-button.png "कोड द्वारा निर्मित नया ActiveX कमांड बटन दिखाते हुए Word दस्तावेज़ का स्क्रीनशॉट")

*छवि का alt टेक्स्ट एक्सेसिबिलिटी और SEO के लिए मुख्य कीवर्ड शामिल करता है।*

---

## ActiveX Forms2OleControl क्लास को समझना

`Forms2OleControl` क्लास Word द्वारा ActiveX तत्वों के लिए उपयोग की जाने वाली लो‑लेवल OLE इन्फ्रास्ट्रक्चर को रैप करती है। यह `Shape` से विरासत में मिलती है, इसलिए आवश्यकता पड़ने पर आप सामान्य शेप फ़ॉर्मेटिंग (जैसे बॉर्डर, रोटेशन) भी लागू कर सकते हैं।

* **ActiveX कमांड बटन** – सबसे सामान्य उपयोग केस; आप इसे Word के डेवलपर टूल्स से मैक्रो से बाइंड कर सकते हैं।
* **setOleClassName मेथड** – निर्धारित करता है कि Word कौन सा COM क्लास लोड करे; अन्य वैध मानों में `"Forms.TextBox.1"` और `"Forms.ComboBox.1"` शामिल हैं।
* **Forms2OleControl आकार** – `SetWidth`/`SetHeight` द्वारा नियंत्रित। ये मेथड पॉइंट्स (1 pt = 1/72 in) स्वीकार करते हैं।

### Forms2OleControl बनाम Content Controls कब उपयोग करें

यदि आपको केवल साधारण डेटा एंट्री (जैसे साधारण टेक्स्ट फ़ील्ड) चाहिए, तो Word के बिल्ट‑इन कंटेंट कंट्रोल हल्के होते हैं। जब आपको इवेंट हैंडलिंग या कस्टम VBA इंटरैक्शन जैसी पूरी ActiveX कार्यक्षमता चाहिए, तब `Forms2OleControl` का उपयोग करें।

---

## अतिरिक्त प्रॉपर्टीज़ सेट करना (वैकल्पिक)

कोर चरणों से **कोड में forms2olecontrol बनाना** संभव है, लेकिन अक्सर आप बटन की उपस्थिति या व्यवहार को फाइन‑ट्यून करना चाहते हैं।

```csharp
// Change the button caption (requires a VBA macro to read it)
commandButton.SetOleData("Caption", "Submit");

// Disable the button initially
commandButton.SetOleData("Enabled", false);

// Add a tooltip
commandButton.SetOleData("ToolTipText", "Click to submit the form");
```

**यह क्यों महत्वपूर्ण है:**  
`SetOleData` आपको OLE स्ट्रीम में सीधे मनमाने प्रॉपर्टी वैल्यू लिखने की अनुमति देता है। यह **ActiveX कमांड बटन** को VBA के बिना कस्टमाइज़ करने का सबसे लचीला तरीका है।

---

## सामान्य समस्याएँ और ट्रबलशूटिंग

| लक्षण | संभावित कारण | समाधान |
|--------|--------------|-----|
| बटन ग्रे बॉक्स के रूप में दिखता है | `setOleClassName` में गलत क्लास नाम पास किया गया | स्ट्रिंग बिल्कुल `"Forms.CommandButton.1"` (केस‑सेंसिटिव) है, यह सुनिश्चित करें |
| आकार नहीं बदल रहा | नियंत्रण सम्मिलित करने से पहले Width/Height सेट किया गया | हमेशा `InsertForms2OleControl` के **बाद** `SetWidth`/`SetHeight` कॉल करें |
| दस्तावेज़ खोलते समय “OLE object not found” त्रुटि | Aspose.Words लाइसेंस अनुपलब्ध (evaluation संस्करण OLE को सीमित कर सकता है) | वैध लाइसेंस लागू करें या पूर्ण OLE समर्थन वाले फ्री ट्रायल का उपयोग करें |
| बटन का कैप्शन “CommandButton1” ही रहता है | `SetOleData` नहीं उपयोग किया गया या मैक्रो प्रॉपर्टी नहीं पढ़ रहा | VBA मैक्रो से `"Caption"` प्रॉपर्टी पढ़ें या Word UI से कैप्शन सेट करें |

---

## पूर्ण, चलाने योग्य उदाहरण

नीचे एक पूर्ण कंसोल एप्लिकेशन दिया गया है जिसे आप कॉपी‑पेस्ट करके चला सकते हैं। यह ट्यूटोरियल में कवर किए गए सभी चरणों को प्रदर्शित करता है।

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace Forms2OleControlDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // 1. Create a new document and a DocumentBuilder
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 2. Insert the Forms2OleControl (ActiveX placeholder)
            Forms2OleControl commandButton = builder.InsertForms2OleControl();

            // 3. Set the ActiveX class to CommandButton
            commandButton.SetOleClassName("Forms.CommandButton.1");

            // 4. Define the visual size of the button
            commandButton.SetWidth(80);   // 80 points = ~1.11 inches
            commandButton.SetHeight(30);  // 30 points = ~0.42 inches

            // Optional: set a custom caption via OLE data (requires VBA to read)
            commandButton.SetOleData("Caption", "Submit");

            // 5. Save the document
            string outputPath = "ActiveXButton.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

**प्रत्येक सेक्शन की व्याख्या**

* **Using निर्देश** – `Document`, `DocumentBuilder`, और `Forms2OleControl` के लिए आवश्यक Aspose.Words नेमस्पेस लाता है।
* **Document निर्माण** – एक खाली Word फ़ाइल बनाता है।
* **InsertForms2OleControl** – बिल्डर के वर्तमान कर्सर पर OLE नियंत्रण रखता है।
* **SetOleClassName** – Word को बताता है कि नियंत्रण एक **ActiveX कमांड बटन** है।
* **SetWidth / SetHeight** – पेशेवर लुक के लिए **Forms2OleControl आकार** समायोजित करता है।
* **SetOleData (वैकल्पिक)** – कैप्शन जैसी अतिरिक्त प्रॉपर्टीज़ लिखने का उदाहरण देता है।
* **Save** – अंतिम `.docx` फ़ाइल को डिस्क पर लिखता है।

प्रोग्राम चलाएँ (`dotnet run`) और `ActiveXButton.docx` खोलें। आपको एक बटन दिखाई देगा जिसे बाद में मैक्रो से लिंक किया जा सकता है।

---

## निष्कर्ष

आप अब Aspose.Words का उपयोग करके **कोड में forms2olecontrol बनाना** जानते हैं, `DocumentBuilder` को इनिशियलाइज़ करने से लेकर `setOleClassName` के साथ **ActiveX कमांड बटन** कॉन्फ़िगर करने और **Forms2OleControl आकार** नियंत्रित करने तक। यह तरीका आपको जटिल Word दस्तावेज़ों को ऑटोमेट करने, इंटरैक्टिव UI तत्व एम्बेड करने, और सभी लॉजिक को कोड में रखने की अनुमति देता है।

## आगे आप क्या सीखें?

नीचे दिए गए ट्यूटोरियल्स इस गाइड में दिखाए गए तकनीकों पर आधारित हैं और अतिरिक्त API फीचर्स को मास्टर करने तथा वैकल्पिक इम्प्लीमेंटेशन एप्रोच को एक्सप्लोर करने में मदद करेंगे।

- [How to create form fields and add content using DocumentBuilder in Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create rectangle shape in Word with Aspose.Words – Step‑by‑step guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}