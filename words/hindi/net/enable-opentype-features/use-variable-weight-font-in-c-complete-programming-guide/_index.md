---
category: general
date: 2026-06-02
description: C# में वैरिएबल वेट फ़ॉन्ट का उपयोग करना सीखें और प्रोग्रामेटिकली फ़ॉन्ट
  वेट सेट करें, साथ ही डायनामिक टाइपोग्राफी के लिए फ़ॉन्ट स्ट्रेच कोड बदलें।
draft: false
keywords:
- use variable weight font
- set font weight programmatically
- change font stretch code
- variable font Aspose.Words
- dynamic typography C#
language: hi
og_description: C# में वैरिएबल वेट फ़ॉन्ट का उपयोग करके प्रोग्रामेटिक रूप से फ़ॉन्ट
  वज़न सेट करें और फ़ॉन्ट स्ट्रेच कोड बदलें, जिससे आपके दस्तावेज़ों में डायनेमिक टाइपोग्राफी
  सक्षम हो सके।
og_title: C# में वैरिएबल वेट फ़ॉन्ट का उपयोग – पूर्ण गाइड
schemas:
- author: Aspose
  dateModified: '2026-06-02'
  description: Learn how to use variable weight font in C# and set font weight programmatically
    while change font stretch code for dynamic typography.
  headline: Use Variable Weight Font in C# – Complete Programming Guide
  type: TechArticle
- description: Learn how to use variable weight font in C# and set font weight programmatically
    while change font stretch code for dynamic typography.
  name: Use Variable Weight Font in C# – Complete Programming Guide
  steps:
  - name: What if the font doesn’t appear at all?
    text: '- **Missing FontSettings**: Double‑check that `doc.FontSettings = fontSettings;`
      is executed **before** any text is added. - **Incorrect family name**: Use `fontSettings.GetFonts()`
      to list all discovered families; copy the exact string. - **Unsupported weight/stretch**:
      Some variable fonts only sup'
  - name: Can I change the weight after the document is saved?
    text: Yes. The `Run` object is mutable, so you can adjust `FontWeight` or `FontStretch`
      at any point before the final `Save`. If you need to toggle weights dynamically
      (e.g., based on user interaction), consider generating separate runs for each
      state.
  - name: Does this work with DOCX output?
    text: Absolutely. The variable‑weight metadata is stored in the underlying OpenXML,
      and modern versions of Word can interpret it. However, older Word versions may
      ignore the stretch setting.
  type: HowTo
tags:
- C#
- Aspose.Words
- Variable Fonts
title: C# में वैरिएबल वेट फ़ॉन्ट का उपयोग करें – पूर्ण प्रोग्रामिंग गाइड
url: /hi/net/enable-opentype-features/use-variable-weight-font-in-c-complete-programming-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C# में Variable Weight Font का उपयोग – पूर्ण प्रोग्रामिंग गाइड

क्या आपको कभी **variable weight font** को .NET प्रोजेक्ट में उपयोग करना पड़ा लेकिन यह नहीं पता था कि वजन (weight) और स्ट्रेच (stretch) को उपयोगकर्ता इनपुट के अनुसार कैसे बदलें? आप अकेले नहीं हैं। कई UI या रिपोर्टिंग परिदृश्यों में आप चाहते हैं कि टेक्स्ट अनुकूलित हो—शायद एक हल्का हेडलाइन जो होवर पर बोल्ड हो जाए, या एक पैराग्राफ जो ज़ोर देने के लिए अपनी चौड़ाई बढ़ा ले। अच्छी खबर यह है कि Aspose.Words के साथ आप **फ़ॉन्ट वेट को प्रोग्रामेटिकली सेट** कर सकते हैं और यहाँ तक कि **फ़ॉन्ट स्ट्रेच कोड** को भी रीयल‑टाइम में बदल सकते हैं।

इस ट्यूटोरियल में हम एक हैंड‑ऑन उदाहरण के माध्यम से दिखाएंगे कि कैसे एक variable‑weight फ़ॉन्ट लोड करें, कस्टम वेट लागू करें, और स्ट्रेच सेटिंग को ट्यून करें—सभी स्पष्ट C# कोड के साथ जिसे आप कॉपी‑पेस्ट कर सकते हैं। अंत तक आपके पास एक चलाने योग्य कंसोल एप्लिकेशन होगा जो प्रभाव को दर्शाते हुए एक PDF उत्पन्न करेगा।

---

## आपको क्या चाहिए

- **Aspose.Words for .NET** (v23.12 या बाद का)। यह लाइब्रेरी variable‑weight फ़ॉन्ट्स के लिए पूर्ण समर्थन के साथ आती है।
- एक फ़ोल्डर जिसमें कम से कम एक variable‑weight फ़ॉन्ट फ़ाइल हो, उदाहरण के लिए *RobotoFlex‑Variable.ttf*। इसे आप Google Fonts से डाउनलोड कर सकते हैं।
- .NET 6 SDK (या कोई भी हालिया .NET संस्करण) और आपका पसंदीदा IDE।
- बेसिक C# ज्ञान—कोई जटिल चीज़ नहीं, सिर्फ़ कुछ पंक्तियों का कोड।

बस इतना ही। Aspose.Words के अलावा कोई अतिरिक्त NuGet पैकेज नहीं, और कोई अजीब कॉन्फ़िगरेशन फ़ाइल नहीं।

---

![Use variable weight font example](https://example.com/variable-weight-sample.png "Use variable weight font demonstration")

*Alt text: उत्पन्न PDF दस्तावेज़ में variable weight फ़ॉन्ट के उपयोग को दिखाते हुए स्क्रीनशॉट।*

---

## चरण 1: FontSettings सेट करें और अपने फ़ॉन्ट फ़ोल्डर की ओर इशारा करें  

सबसे पहले—Aspose.Words को यह बताना होता है कि आपके variable‑weight फ़ॉन्ट्स कहाँ स्थित हैं। आप यह `FontSettings` ऑब्जेक्ट बनाकर और एक `FolderFontSource` संलग्न करके करते हैं। `true` फ़्लैग इंजन को सब‑फ़ोल्डर्स में भी खोज करने के लिए कहता है, जो तब उपयोगी होता है जब आप कई फ़ॉन्ट फ़ैमिलीज़ को एक साथ रखते हैं।

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// Step 1: Create FontSettings and point to the folder containing variable‑weight fonts
var fontSettings = new FontSettings();
fontSettings.SetFontSources(new FontSourceBase[]
{
    new FolderFontSource(@"C:\MyProject\Fonts\", true) // Adjust path to your own directory
});
```

**क्यों महत्वपूर्ण है:** फ़ोल्डर को रजिस्टर किए बिना, Aspose.Words सिस्टम फ़ॉन्ट्स पर फ़ॉल्बैक कर देगा और आपके कस्टम फ़ॉन्ट फ़ाइल में एम्बेडेड variable‑weight डेटा को नजरअंदाज़ करेगा। यह कदम आगे आने वाले सभी कार्यों की नींव है।

---

## चरण 2: FontSettings को Document से जोड़ें  

अब हम एक नया `Document` बनाते हैं (या मौजूदा को लोड करते हैं) और उसे अभी तैयार किए गए `FontSettings` का उपयोग करने के लिए कहते हैं। यह बाइंडिंग वह है जो बाद में जोड़े जाने वाले प्रत्येक `Run` को variable‑weight डेटा उपलब्ध कराती है।

```csharp
// Step 2: Attach the FontSettings to the document
var doc = new Document();          // Starts with a blank document
doc.FontSettings = fontSettings;   // Connects our custom fonts
```

यदि आपके पास पहले से एक टेम्पलेट है—जैसे प्लेसहोल्डर्स वाला Word फ़ाइल—तो `new Document()` को `new Document("Template.docx")` से बदल सकते हैं। वही `FontSettings` लागू होगा।

---

## चरण 3: वह टेक्स्ट Run जोड़ें जो Variable‑Weight फ़ॉन्ट का उपयोग करेगा  

एक **Run** Aspose.Words में टेक्स्ट फ़ॉर्मेटिंग की सबसे छोटी इकाई है। हम एक बनाएँगे, उसे एक नए पैराग्राफ में डालेंगे, और बाद में उसके फ़ॉन्ट एट्रिब्यूट्स को बदलेंगे।

```csharp
// Step 3: Add a run of text that will use the variable‑weight font
var paragraph = new Paragraph(doc);
doc.FirstSection.Body.AppendChild(paragraph);

var run = new Run(doc, "Variable‑weight text demo");
paragraph.AppendChild(run);
```

इस चरण पर टेक्स्ट डिफ़ॉल्ट फ़ॉन्ट (आमतौर पर Times New Roman) में रेंडर होगा। असली जादू तब होगा जब हम variable‑weight फ़ैमिली असाइन करेंगे।

---

## चरण 4: Variable‑Weight फ़ॉन्ट फ़ैमिली चुनें  

यहीं पर हम **variable weight font** का वास्तविक उपयोग करेंगे। `Font.Name` को उस सटीक फ़ैमिली नाम पर सेट करें जो फ़ॉन्ट फ़ाइल के अंदर परिभाषित है। Roboto Flex के लिए, नाम `"Roboto Flex"` है।

```csharp
// Step 4: Choose the variable‑weight font family
run.Font.Name = "Roboto Flex";
```

यदि फ़ैमिली नाम के बारे में अनिश्चित हैं, तो `.ttf` फ़ाइल को फ़ॉन्ट व्यूअर में खोलें या `fontSettings.GetFonts()` मेथड का उपयोग करके उपलब्ध फ़ैमिलीज़ की सूची प्राप्त करें।

---

## चरण 5: फ़ॉन्ट वेट और स्ट्रेच को प्रोग्रामेटिकली सेट करें  

अब ट्यूटोरियल का मुख्य भाग: हम **फ़ॉन्ट वेट को प्रोग्रामेटिकली सेट** करेंगे और **फ़ॉन्ट स्ट्रेच कोड** को बदलेंगे। दोनों प्रॉपर्टीज़ पूर्णांक मान लेती हैं जो OpenType स्पेसिफिकेशन से मैप होते हैं।

```csharp
// Step 5: Specify the desired weight and stretch for the run
run.Font.FontWeight = 300;   // Light weight (300)
run.Font.FontStretch = 125; // Expanded stretch (125% of normal width)
```

- **FontWeight**: 100 (Thin) → 900 (Black)। वह कोई भी मान चुनें जो variable फ़ॉन्ट सपोर्ट करता हो।
- **FontStretch**: 50 (Ultra‑Condensed) → 200 (Ultra‑Expanded)। डिफ़ॉल्ट 100 (Normal) है।

> **प्रो टिप:** हर variable फ़ॉन्ट पूरी रेंज नहीं देता। यदि आप ऐसा मान सेट करते हैं जो सपोर्ट नहीं करता, तो इंजन निकटतम उपलब्ध वेट या स्ट्रेच पर क्लैंप कर देगा।

---

## चरण 6: डॉक्यूमेंट को सेव करें और परिणाम सत्यापित करें  

अंत में, डॉक्यूमेंट को PDF (या DOCX) में लिखें और खोलें ताकि प्रभाव देख सकें। PDF विज़ुअल वैरिफिकेशन के लिए अच्छा फॉर्मेट है क्योंकि रेंडरिंग प्लेटफ़ॉर्म‑क्रॉस सुसंगत रहती है।

```csharp
// Step 6: Save the document as PDF
doc.Save(@"C:\MyProject\Output\VariableWeightDemo.pdf", SaveFormat.Pdf);
```

जब आप *VariableWeightDemo.pdf* खोलेंगे, तो आपको “Variable‑weight text demo” वाक्यांश को Roboto Flex के हल्के, थोड़ा विस्तारित संस्करण में रेंडर होते हुए दिखेगा। `FontWeight` को `700` और `FontStretch` को `80` पर बदलें और फिर चलाएँ—टेक्स्ट बोल्ड और अधिक कंडेंस्ड हो जाएगा।

---

## सामान्य प्रश्न एवं किनारे के मामलों  

### फ़ॉन्ट बिल्कुल नहीं दिख रहा है तो क्या करें?  

- **Missing FontSettings**: सुनिश्चित करें कि `doc.FontSettings = fontSettings;` **किसी भी टेक्स्ट को जोड़ने से पहले** निष्पादित हो रहा है।
- **गलत फ़ैमिली नाम**: `fontSettings.GetFonts()` से सभी खोजे गए फ़ैमिलीज़ की सूची देखें; सटीक स्ट्रिंग कॉपी करें।
- **Unsupported weight/stretch**: कुछ variable फ़ॉन्ट्स केवल 100‑900 वेट रेंज का एक उपसमुच्चय सपोर्ट करते हैं। सुरक्षित फ़ॉलबैक के लिए `run.Font.FontWeight = 400;` उपयोग करें।

### क्या डॉक्यूमेंट सेव होने के बाद वेट बदल सकते हैं?  

हाँ। `Run` ऑब्जेक्ट mutable है, इसलिए आप अंतिम `Save` से पहले कभी भी `FontWeight` या `FontStretch` को समायोजित कर सकते हैं। यदि आप वेट को डायनामिकली टॉगल करना चाहते हैं (उदा. उपयोगकर्ता इंटरैक्शन के आधार पर), तो प्रत्येक स्थिति के लिए अलग‑अलग रन जेनरेट करने पर विचार करें।

### क्या यह DOCX आउटपुट के साथ काम करता है?  

बिल्कुल। variable‑weight मेटाडेटा मूल OpenXML में संग्रहीत होता है, और आधुनिक Word संस्करण इसे इंटरप्रेट कर सकते हैं। हालांकि, पुराने Word संस्करण स्ट्रेच सेटिंग को नजरअंदाज़ कर सकते हैं।

---

## पूर्ण कार्यशील उदाहरण  

नीचे एक पूरा कंसोल प्रोग्राम दिया गया है जिसे आप तुरंत कंपाइल और रन कर सकते हैं। इसमें सभी आवश्यक `using` निर्देश, एरर हैंडलिंग, और टिप्पणी शामिल हैं।

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

namespace VariableWeightDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Configure FontSettings
            var fontSettings = new FontSettings();
            fontSettings.SetFontSources(new FontSourceBase[]
            {
                // 👉 Point to your local folder containing the variable‑weight font files
                new FolderFontSource(@"C:\MyProject\Fonts\", true)
            });

            // 2️⃣ Create the document and attach FontSettings
            var doc = new Document();
            doc.FontSettings = fontSettings;

            // 3️⃣ Build a paragraph with a run of text
            var paragraph = new Paragraph(doc);
            doc.FirstSection.Body.AppendChild(paragraph);
            var run = new Run(doc, "Variable‑weight text demo");
            paragraph.AppendChild(run);

            // 4️⃣ Apply the variable‑weight font family
            run.Font.Name = "Roboto Flex";

            // 5️⃣ Set weight (300 = Light) and stretch (125 = Expanded)
            run.Font.FontWeight = 300;   // set font weight programmatically
            run.Font.FontStretch = 125; // change font stretch code

            // 6️⃣ Save as PDF to verify the rendering
            string outputPath = @"C:\MyProject\Output\VariableWeightDemo.pdf";
            doc.Save(outputPath, SaveFormat.Pdf);

            Console.WriteLine($"Document saved to {outputPath}");
            Console.WriteLine("Open the PDF to see the light, expanded Roboto Flex text.");
        }
    }
}
```

**अपेक्षित आउटपुट:** कंसोल सेव पाथ प्रिंट करेगा, और जेनरेट किया गया PDF टेक्स्ट को हल्के, विस्तारित स्टाइल में दिखाएगा—बिल्कुल वही जो हमने कॉन्फ़िगर किया था।

---

## पुनरावलोकन  

हमने C# में Aspose.Words के साथ **variable weight font** का उपयोग कैसे करें, **फ़ॉन्ट वेट को प्रोग्रामेटिकली सेट** करना, और **फ़ॉन्ट स्ट्रेच कोड** को बदलना दिखाया। चरण सरल थे: `FontSettings` को कॉन्फ़िगर करें, उसे `Document` से जोड़ें, एक `Run` बनाएं, variable‑weight फ़ैमिली चुनें, और अंत में `FontWeight` तथा `FontStretch` को ट्यून करें।

---

## आगे क्या करें?  

- **डायनामिक UI इंटीग्रेशन**: वही लॉजिक WinForms या WPF ऐप में जोड़ें ताकि उपयोगकर्ता स्लाइडर के माध्यम से वेट/स्ट्रेच चुन सकें।
- **एकाधिक रन**: एक ही पैराग्राफ में विभिन्न वेट वाले कई रन जोड़ें और टाइपोग्राफिक हाइरार्की बनाएं।
- **एडवांस्ड एक्सिस**: कुछ variable फ़ॉन्ट्स अतिरिक्त एक्सिस (जैसे slant, optical size) प्रदान करते हैं। `run.Font.FontStyle` या `FontVariationSettings` का उपयोग करके और भी सूक्ष्म नियंत्रण प्राप्त करें।
- **परफ़ॉर्मेंस टिप्स**: कई डॉक्यूमेंट प्रोसेस करते समय `FontSettings` इंस्टेंस को कैश करें ताकि फ़ोल्डर स्कैन दोहराने से बचा जा सके।

बिना हिचकिचाहट प्रयोग करें—*Roboto Flex* को *Inter Variable* या किसी अन्य OpenType variable फ़ॉन्ट से बदलें, और अपने डॉक्यूमेंट्स को नई दृश्य लचीलापन दें। कोडिंग का आनंद लें!

## अगला क्या सीखें?  

नीचे दिए गए ट्यूटोरियल्स उन विषयों को कवर करते हैं जो इस गाइड में दिखाए गए तकनीकों पर आधारित हैं। प्रत्येक संसाधन में पूर्ण कार्यशील कोड उदाहरण और चरण‑दर‑चरण व्याख्याएँ हैं, जिससे आप अतिरिक्त API फीचर्स में महारत हासिल कर सकें और अपने प्रोजेक्ट्स में वैकल्पिक इम्प्लीमेंटेशन एप्रोच का अन्वेषण कर सकें।

- [Use Font From Target Machine](/words/english/net/programming-with-htmlfixedsaveoptions/use-font-from-target-machine/)
- [Use Font From Target Machine](/words/german/net/programming-with-htmlfixedsaveoptions/use-font-from-target-machine/)
- [Use Font From Target Machine](/words/french/net/programming-with-htmlfixedsaveoptions/use-font-from-target-machine/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}