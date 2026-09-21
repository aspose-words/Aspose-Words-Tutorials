---
category: general
date: 2026-09-21
description: प्रोग्रामेटिकली वर्ड दस्तावेज़ बनाएं और सीखें कि कैसे वर्ड दस्तावेज़
  को सहेजने का बटन, कमांड बटन शब्द डालें, और DocumentBuilder का उपयोग करके कमांड बटन
  का कैप्शन सेट करें।
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document programmatically
- save word document button
- insert command button word
- set command button caption
- how to use documentbuilder
language: hi
lastmod: 2026-09-21
og_description: Aspose.Words के साथ प्रोग्रामेटिकली वर्ड दस्तावेज़ बनाएं। सीखें कैसे
  वर्ड दस्तावेज़ को सहेजने का बटन, कमांड बटन वर्ड डालें, कमांड बटन का कैप्शन सेट करें,
  और इंटरैक्टिव फ़ॉर्म्स के लिए DocumentBuilder का उपयोग करें।
og_image_alt: Screenshot of a Word file that contains an inserted CommandButton created
  programmatically
og_title: प्रोग्रामेटिक रूप से वर्ड दस्तावेज़ बनाएं और एक बटन जोड़ें
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: Create word document programmatically and learn how to save word document
    button, insert command button word, and set command button caption using DocumentBuilder.
  headline: Create word document programmatically and insert a button
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word Automation
title: प्रोग्रामेटिक रूप से वर्ड दस्तावेज़ बनाएं और एक बटन डालें
url: /hi/java/using-document-elements/create-word-document-programmatically-and-insert-a-button/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# प्रोग्रामेटिकली वर्ड डॉक्यूमेंट बनाएं और बटन डालें

यदि आपको **प्रोग्रामेटिकली वर्ड डॉक्यूमेंट बनाना** है, तो Aspose.Words एक फ्लुएंट API प्रदान करता है जो आपको CommandButton जैसे इंटरैक्टिव कंट्रोल जोड़ने की अनुमति देता है। यह ट्यूटोरियल यह भी समझाता है **DocumentBuilder का उपयोग कैसे करें**, **वर्ड डॉक्यूमेंट बटन कैसे सेव करें**, और **कमांड बटन कैप्शन कैसे सेट करें** ताकि बटन .docx फ़ाइल में ठीक वैसा ही दिखे जैसा आप चाहते हैं।

आप सीखेंगे:

* `Document` के साथ एक खाली डॉक्यूमेंट इनिशियलाइज़ करना।
* डॉक्यूमेंट को एडिट करने के लिए `DocumentBuilder` के साथ काम करना।
* **CommandButton** (`insert command button word`) डालना।
* बटन का नाम और विज़िबल कैप्शन (`set command button caption`) सेट करना।
* परिणाम को डिस्क पर सहेजना (`save word document button`)।

यह स्टेप्स .NET डेवलपर्स के लिए C# और नवीनतम Aspose.Words for .NET (v24.10) का उपयोग करके लिखे गए हैं। Aspose.Words के अलावा कोई अतिरिक्त NuGet पैकेज आवश्यक नहीं है।

---

## शुरू करने से पहले आपको क्या चाहिए

| पूर्वापेक्षा | कारण |
|--------------|--------|
| Visual Studio 2022 (या कोई भी C# IDE) | सैंपल कोड को कंपाइल और रन करने के लिए। |
| .NET 6.0 SDK या बाद का संस्करण | उदाहरण के लिए रनटाइम प्रदान करता है। |
| Aspose.Words for .NET (v24.10 या नया) | वह लाइब्रेरी जो आपको **प्रोग्रामेटिकली वर्ड डॉक्यूमेंट बनाने** और फॉर्म कंट्रोल्स को मैनीपुलेट करने देती है। |
| C# और OOP कॉन्सेप्ट्स की बेसिक समझ | कोड फ्लो को समझने के लिए आवश्यक। |

आप NuGet के माध्यम से Aspose.Words इंस्टॉल कर सकते हैं:

```bash
dotnet add package Aspose.Words
```

---

## प्रोग्रामेटिकली वर्ड डॉक्यूमेंट बनाएं

पहला कदम एक खाली `Document` को इंस्टैंशिएट करना है। यह ऑब्जेक्ट मेमोरी में पूरे Word फ़ाइल का प्रतिनिधित्व करता है।

```csharp
// Step 1: Create a new blank document
Document doc = new Document();
```

प्रोग्रामेटिकली डॉक्यूमेंट बनाना आपको एक साफ़ कैनवास देता है जिस पर आप पैराग्राफ, टेबल या इंटरैक्टिव कंट्रोल्स जोड़ सकते हैं।  

---

## DocumentBuilder का उपयोग कैसे करें

`DocumentBuilder` वह प्रमुख क्लास है जो `Document` को एडिट करती है। यह टेक्स्ट, इमेज और फॉर्म फील्ड्स डालने के मेथड्स प्रदान करती है। इस ट्यूटोरियल में हम इसका उपयोग CommandButton रखने के लिए करेंगे।

```csharp
// Step 2: Initialize a DocumentBuilder to edit the document
DocumentBuilder builder = new DocumentBuilder(doc);
```

बिल्डर एक इंटरनल कर्सर रखती है जो वर्तमान इंसर्शन लोकेशन की ओर इशारा करता है। डिफॉल्ट रूप से यह पहले सेक्शन की शुरुआत में शुरू होता है, जो हमारे उदाहरण के लिए आदर्श है।

---

## कमांड बटन वर्ड में डालें

Aspose.Words CommandButton को एक ActiveX कंट्रोल के रूप में ट्रीट करता है। `InsertForms2OleControl` मेथड एक जनरिक OLE कंट्रोल बनाता है जिसे हम बाद में बटन के रूप में कॉन्फ़िगर करते हैं।

```csharp
// Step 3: Insert an ActiveX Forms2OleControl (a CommandButton)
Forms2OleControl commandButton = builder.InsertForms2OleControl();
```

इस बिंदु पर कंट्रोल डॉक्यूमेंट में मौजूद है लेकिन इसका कोई विज़ुअल रिप्रेजेंटेशन नहीं है जब तक हम इसका टाइप परिभाषित नहीं करते।

---

## कमांड बटन कैप्शन सेट करें

अब हम OLE कंट्रोल को बताते हैं कि उसे CommandButton की तरह व्यवहार करना चाहिए और उसे एक फ्रेंडली लेबल देते हैं।

```csharp
// Step 4: Define the control as a CommandButton
commandButton.SetControlType(Forms2OleControlType.COMMANDBUTTON);

// Step 5: Set a unique name for the button (used for identification)
commandButton.SetName("btnSubmit");

// Step 6: Set the visible caption that appears on the button
commandButton.SetCaption("Submit");
```

**कमांड बटन कैप्शन** सेट करना आवश्यक है क्योंकि Word इस टेक्स्ट को बटन की सतह पर दिखाता है। यदि आप `SetCaption` को छोड़ देते हैं, तो बटन एक जनरिक लेबल के साथ दिखाई देगा।

---

## वर्ड डॉक्यूमेंट बटन सेव करें

अंत में, डॉक्यूमेंट को डिस्क पर पर्सिस्ट करें। `Save` मेथड पूरे Word पैकेज को, जिसमें नया बटन भी शामिल है, एक .docx फ़ाइल में लिखता है।

```csharp
// Step 7: Save the document containing the CommandButton
doc.Save("YOUR_DIRECTORY/CommandButton.docx");
```

फ़ाइल `CommandButton.docx` अब एक पूरी तरह कार्यात्मक बटन **Submit** लेबल के साथ रखती है। जब उपयोगकर्ता Microsoft Word में फ़ाइल खोलता है और बटन पर क्लिक करता है, तो डिफ़ॉल्ट एक्शन (जिसे आप बाद में VBA के माध्यम से बाइंड कर सकते हैं) ट्रिगर हो जाएगा।

---

## पूर्ण कार्यशील उदाहरण

नीचे पूरा प्रोग्राम दिया गया है जिसे आप कॉपी, पेस्ट और रन कर सकते हैं। यह डॉक्यूमेंट निर्माण से लेकर बटन को सेव करने तक का पूरा वर्कफ़्लो दर्शाता है।

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1. Create a new blank document
        Document doc = new Document();

        // 2. Initialize DocumentBuilder (how to use DocumentBuilder)
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 3. Insert a CommandButton (insert command button word)
        Forms2OleControl commandButton = builder.InsertForms2OleControl();

        // 4. Define the control type as CommandButton
        commandButton.SetControlType(Forms2OleControlType.COMMANDBUTTON);

        // 5. Give the button a unique name (optional but useful)
        commandButton.SetName("btnSubmit");

        // 6. Set the visible caption (set command button caption)
        commandButton.SetCaption("Submit");

        // 7. Save the document (save word document button)
        string outputPath = @"C:\Temp\CommandButton.docx";
        doc.Save(outputPath);

        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

**अपेक्षित परिणाम**

* एक फ़ाइल जिसका नाम `CommandButton.docx` है, वह पाथ पर स्थित है जिसे आपने निर्दिष्ट किया है।
* Microsoft Word में फ़ाइल खोलने पर पहले पेज पर एकल **Submit** बटन दिखेगा।
* बटन को सेलेक्ट, रिसाइज़ या Word के **Developer** टैब से मैक्रो से लिंक किया जा सकता है।

---

## सामान्य प्रश्न और एज‑केस हैंडलिंग

| प्रश्न | उत्तर |
|----------|--------|
| *अगर मुझे एक से अधिक बटन चाहिए तो?* | विभिन्न नामों और कैप्शन के साथ स्टेप्स 3–6 दोहराएँ। प्रत्येक बटन का `SetName` वैल्यू यूनिक होना चाहिए। |
| *क्या मैं बटन का आकार सेट कर सकता हूँ?* | हाँ। कंट्रोल डालने के बाद आप `OleFormat` ऑब्जेक्ट के माध्यम से उसकी `Width` और `Height` प्रॉपर्टीज़ को मॉडिफ़ाई कर सकते हैं। |
| *क्या बटन सभी Word वर्ज़न पर काम करेगा?* | ActiveX कंट्रोल्स डेस्कटॉप संस्करण (Windows) के Word में सपोर्टेड हैं। वे Word Online या macOS पर रेंडर नहीं होते। |
| *क्लिक हैंडलर कैसे जोड़ें?* | आपको VBA कोड लिखना होगा जो बटन के नाम (`btnSubmit`) को रेफ़र करे। VBA मैक्रो को `doc.VbaProject` के ज़रिए एम्बेड किया जा सकता है। |
| *अगर बटन को टेबल सेल के अंदर डालना हो तो?* | `builder.MoveTo(cell.FirstParagraph)` के साथ बिल्डर का कर्सर इच्छित सेल में ले जाएँ, फिर `InsertForms2OleControl` कॉल करें। |

---

## प्रो टिप्स

* **प्रो टिप:** हमेशा `SetName` के साथ एक अर्थपूर्ण नाम सेट करें। यह VBA ऑटोमेशन को सरल बनाता है और डिबगिंग आसान करता है।
* **ध्यान रखें:** `SetControlType` को कॉल करना न भूलें। इस कॉल के बिना OLE ऑब्जेक्ट एक जनरिक प्लेसहोल्डर के रूप में दिखेगा, न कि क्लिकेबल बटन के रूप में।
* **परफ़ॉर्मेंस टिप:** यदि आप लूप में कई डॉक्यूमेंट जनरेट कर रहे हैं, तो एक ही `DocumentBuilder` इंस्टेंस को री‑यूज़ करें और प्रत्येक इंसर्शन से पहले `builder.MoveToDocumentEnd()` कॉल करें ताकि अनावश्यक कर्सर रीसेट से बचा जा सके।

---

## अगले कदम

अब जब आप **प्रोग्रामेटिकली वर्ड डॉक्यूमेंट बनाना**, **कमांड बटन वर्ड में डालना**, **कमांड बटन कैप्शन सेट करना**, और **वर्ड डॉक्यूमेंट बटन सेव करना** जानते हैं, तो आप अधिक एडवांस्ड सीनारियो एक्सप्लोर कर सकते हैं:

* यूज़र इनपुट के लिए **TextFormField** कंट्रोल्स जोड़ें।
* बटन को **MacroButton** फील्ड्स के साथ कॉम्बाइन करें ताकि सीधे VBA एक्सीक्यूट हो सके।
* बटन पर आइकन रखने के लिए **DocumentBuilder.InsertImage** का उपयोग करें।
* ASP.NET के साथ इंटीग्रेट करके Word फॉर्म्स जेनरेट करें


## आप अगला क्या सीखें?

निम्नलिखित ट्यूटोरियल्स उन विषयों को कवर करते हैं जो इस गाइड में दिखाए गए तकनीकों पर आधारित हैं। प्रत्येक रिसोर्स में पूर्ण कार्यशील कोड उदाहरण और स्टेप‑बाय‑स्टेप एक्सप्लेनैशन शामिल हैं, जिससे आप अतिरिक्त API फीचर्स में महारत हासिल कर सकें और अपने प्रोजेक्ट्स में वैकल्पिक इम्प्लीमेंटेशन अप्रोचेज़ को एक्सप्लोर कर सकें।

- [Create New Word Document](/words/english/net/add-content-using-documentbuilder/create-new-document/)
- [Create Word Document with Aspose.Words for .NET](/words/english/net/add-content-using-document-builder/insert-paragraph/)
- [Insert Inline Image in Word Document using Aspose.Words](/words/english/net/add-content-using-document-builder/insert-inline-image/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}