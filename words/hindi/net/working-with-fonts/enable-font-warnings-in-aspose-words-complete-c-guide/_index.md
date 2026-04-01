---
category: general
date: 2026-04-01
description: Aspose.Words के साथ Word दस्तावेज़ लोड करते समय फ़ॉन्ट चेतावनियों को
  सक्षम करें। C# LoadOptions और फ़ॉन्ट सेटिंग्स का उपयोग करके फ़ॉन्ट प्रतिस्थापन घटनाओं
  को कैसे पकड़ें, जानें।
draft: false
keywords:
- enable font warnings
- font substitution
- Aspose.Words
- LoadOptions
- C# document processing
- font settings
language: hi
og_description: Aspose.Words के साथ Word दस्तावेज़ लोड करते समय फ़ॉन्ट चेतावनियों
  को सक्षम करें। यह ट्यूटोरियल आपको C# में फ़ॉन्ट प्रतिस्थापन घटनाओं को कैप्चर करना
  दिखाता है।
og_title: Aspose.Words में फ़ॉन्ट चेतावनियों को सक्षम करें – पूर्ण C# गाइड
tags:
- Aspose.Words
- C#
- Font Management
title: Aspose.Words में फ़ॉन्ट चेतावनियों को सक्षम करें – पूर्ण C# गाइड
url: /hi/net/working-with-fonts/enable-font-warnings-in-aspose-words-complete-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words में फ़ॉन्ट चेतावनियाँ सक्षम करें – पूर्ण C# गाइड

क्या आपने कभी सोचा है कि प्रोग्रामेटिकली लोड करने के बाद Word दस्तावेज़ अचानक अलग क्यों दिखता है? **Enable Font Warnings** और आप तुरंत जान पाएँगे कि Aspose.Words कब किसी गायब फ़ॉन्ट को फ़ॉलबैक से बदलता है। इस ट्यूटोरियल में हम एक व्यावहारिक उदाहरण के माध्यम से चलेंगे जो न केवल उन प्रतिस्थापनों को पकड़ता है बल्कि यह भी समझाता है कि *क्यों* वे होते हैं।

हम वह सब कवर करेंगे जो आपको शुरू करने के लिए चाहिए: आवश्यक NuGet पैकेज, सटीक `LoadOptions` कॉन्फ़िगरेशन, और एक साफ़ कंसोल आउटपुट जो बताता है कि कौन से फ़ॉन्ट बदले गए। अंत तक आपके पास **C# document processing** के लिए एक ठोस, पुन: उपयोग योग्य पैटर्न होगा जो Aspose.Words के किसी भी संस्करण के साथ काम करता है।

## आप क्या सीखेंगे

- `LoadOptions` इंस्टेंस कैसे बनाएँ जो फ़ॉन्ट परिवर्तन को ट्रैक करे।  
- `SubstitutionWarning` इवेंट का उद्देश्य और इसे कैसे जोड़ें।  
- एक पूर्ण, चलाने योग्य कोड सैंपल जो कंसोल में स्पष्ट चेतावनियाँ प्रिंट करता है।  
- ऐसे किनारे के मामलों को संभालने के टिप्स जैसे दस्तावेज़ जिनमें केवल मानक फ़ॉन्ट होते हैं।  

Aspose.Words के साथ कोई पूर्व अनुभव आवश्यक नहीं है—सिर्फ C# और .NET की बुनियादी परिचितता चाहिए।

---

![फ़ॉन्ट चेतावनियाँ सक्षम करने का आरेख](placeholder-image.png "फ़ॉन्ट चेतावनियाँ सक्षम करने का आरेख")

*Alt text: गायब फ़ॉन्ट के प्रतिस्थापित होने पर इवेंट फ्लो दिखाता हुआ फ़ॉन्ट चेतावनियाँ सक्षम करने का आरेख.*

## चरण 1: LoadOptions सेट करें और फ़ॉन्ट चेतावनियाँ सक्षम करें

पहली चीज़ जो आपको चाहिए वह एक `LoadOptions` ऑब्जेक्ट है। यह कंटेनर Aspose.Words को बताता है कि आप जिस फ़ाइल को लोड करने वाले हैं, उसे कैसे संभालना है। एक नया `FontSettings` इंस्टेंस असाइन करके आप फ़ॉन्ट‑संबंधित इवेंट्स के लिए दरवाज़ा खोलते हैं।

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// Step 1: Prepare load options and enable font substitution warnings
LoadOptions loadOptions = new LoadOptions
{
    // Attach a new FontSettings object – this is where warnings are emitted.
    FontSettings = new FontSettings()
};
```

**यह क्यों महत्वपूर्ण है:**  
यदि आप `FontSettings` असाइनमेंट को छोड़ देते हैं, तो Aspose.Words अभी भी गायब फ़ॉन्ट को प्रतिस्थापित करेगा, लेकिन आपको कोई सूचना नहीं मिलेगी। चेतावनी तंत्र `FontSettings` के भीतर रहता है, इसलिए इसे इनिशियलाइज़ करना हमारे लक्ष्य के लिए *अत्यावश्यक* है।

> **प्रो टिप:** आप `SetFontsFolder` का उपयोग करके `FontSettings` को एक कस्टम फ़ॉन्ट्स फ़ोल्डर की ओर भी इंगित कर सकते हैं। इससे आपको मिलने वाली चेतावनियों की संख्या कम हो जाती है, क्योंकि Aspose.Words वास्तव में गायब टाइपफ़ेस को खोज सकता है।

## चरण 2: SubstitutionWarning इवेंट (फ़ॉन्ट प्रतिस्थापन) के लिए सब्सक्राइब करें

अब जब `FontSettings` ऑब्जेक्ट मौजूद है, हम इसके `SubstitutionWarning` इवेंट में हुक करते हैं। यह इवेंट **हर बार** फायर होता है जब Aspose.Words अनुरोधित फ़ॉन्ट को किसी अन्य चीज़ से बदलता है।

```csharp
// Step 2: Subscribe to the SubstitutionWarning event to be notified when a font is replaced
loadOptions.FontSettings.SubstitutionWarning += (sender, e) =>
{
    // e.FontName – the name that the document asked for
    // e.SubstitutedFontName – the font that Aspose.Words actually used
    Console.WriteLine($"[Warning] Font \"{e.FontName}\" was substituted with \"{e.SubstitutedFontName}\".");
};
```

**यह क्यों महत्वपूर्ण है:**  
इस लिस्नर के बिना आपको प्रतिस्थापन प्रक्रिया में कोई दृश्यता नहीं होगी। कंसोल लाइन आपको एक त्वरित ऑडिट ट्रेल देती है, जो स्वचालित बिल्ड्स के दौरान या अनुपालन‑भारी उद्योगों के लिए PDF जनरेट करते समय विशेष रूप से उपयोगी है।

> **सामान्य प्रश्न:** *यदि मैं चेतावनियों को दबाना चाहूँ?*  
> आप सरलता से हैंडलर को डिटैच कर सकते हैं या `FontSettings.SubstitutionWarning += null;` सेट कर सकते हैं। हालांकि, चेतावनियों को रखना आमतौर पर सबसे सुरक्षित रास्ता है क्योंकि चुपचाप होने वाले प्रतिस्थापन लेआउट गड़बड़ियों का कारण बन सकते हैं।

## चरण 3: कॉन्फ़िगर किए गए विकल्पों के साथ अपना दस्तावेज़ लोड करें (C# document processing)

चेतावनी प्रणाली तैयार होने के साथ, दस्तावेज़ लोड करना सीधा है। `LoadOptions` इंस्टेंस को `Document` कंस्ट्रक्टर में पास करें, और Aspose.Words बाकी काम करेगा।

```csharp
// Step 3: Load the document using the configured options
string filePath = @"C:\Docs\DocumentWithMissingFont.docx";

Document doc = new Document(filePath, loadOptions);

// Optional: Save to PDF to see the visual impact of the substitution
doc.Save(@"C:\Docs\Output.pdf");
```

**यह क्यों महत्वपूर्ण है:**  
`LoadOptions` ऑब्जेक्ट कच्ची फ़ाइल और चेतावनी इन्फ्रास्ट्रक्चर के बीच पुल है। यदि आप इसे छोड़ देते हैं, तो दस्तावेज़ चुपचाप लोड हो जाएगा, और कोई भी गायब फ़ॉन्ट बिना किसी निशान के बदल दिया जाएगा।

> **एज केस:** कुछ दस्तावेज़ आवश्यक फ़ॉन्ट फ़ाइलें एम्बेड करते हैं। उस स्थिति में कोई चेतावनी नहीं दिखेगी क्योंकि Aspose.Words एम्बेडेड फ़ॉन्ट को खोज लेता है। ऊपर का कोड अभी भी काम करता है; आपको केवल एक खाली कंसोल आउटपुट दिखेगा।

## चरण 4: आउटपुट सत्यापित करें और सामान्य pitfalls

प्रोग्राम को कमांड‑प्रॉम्प्ट या अपने IDE के डिबगर से चलाएँ। यदि स्रोत दस्तावेज़ में ऐसा फ़ॉन्ट है जो मशीन पर इंस्टॉल नहीं है (या कस्टम फ़ॉन्ट्स फ़ोल्डर में उपलब्ध नहीं है), तो आपको इस तरह की लाइन्स दिखेंगी:

```
[Warning] Font "Comic Sans MS" was substituted with "Arial".
[Warning] Font "MyCustomFont" was substituted with "Times New Roman".
```

यदि कुछ भी प्रिंट नहीं होता, तो या तो:

1. सभी फ़ॉन्ट मिल गए, **या**  
2. `SubstitutionWarning` हैंडलर सही तरीके से अटैच नहीं हुआ था (स्टेप 2 को दोबारा जांचें)।

### फ़ॉन्ट प्रतिस्थापन क्यों होते हैं?

- **Missing system font:** ऑपरेटिंग सिस्टम में अनुरोधित टाइपफ़ेस नहीं है।  
- **Unsupported font format:** Aspose.Words TrueType और OpenType पढ़ सकता है, लेकिन हर प्रोपायटरी फ़ॉर्मेट नहीं।  
- **License restrictions:** कुछ व्यावसायिक फ़ॉन्ट एम्बेडिंग को ब्लॉक करते हैं, जिससे फ़ॉलबैक लागू होता है।

*क्यों* को समझना आपको यह तय करने में मदद करता है कि क्या आप अपने ऐप के साथ गायब फ़ॉन्ट्स को शिप करें या दस्तावेज़ की स्टाइलिंग को समायोजित करें।

## बोनस: फ़ॉलबैक फ़ॉन्ट को नियंत्रित करना

यदि आप चाहते हैं कि हर गायब फ़ॉन्ट किसी विशिष्ट फ़ैमिली (जैसे, “Calibri”) पर फ़ॉलबैक हो, तो आप एक ग्लोबल सब्स्टिट्यूशन नियम सेट कर सकते हैं:

```csharp
loadOptions.FontSettings.SubstitutionSettings.FontSubstitutes.AddSubstitutes(
    "AnyMissingFont", // wildcard – applies to any font not found
    new[] { "Calibri" } // the preferred substitute
);
```

अब कंसोल फिर भी आपको चेतावनी देगा, लेकिन दृश्य परिणाम सभी गायब फ़ॉन्ट्स में सुसंगत रहेगा।

---

## पुनरावलोकन

- **Enable Font Warnings** एक नया `FontSettings` के साथ `LoadOptions` बनाकर सक्षम करें।  
- `SubstitutionWarning` इवेंट को हुक करें ताकि जब भी फ़ॉन्ट बदला जाए, वास्तविक‑समय अलर्ट मिलें।  
- कॉन्फ़िगर किए गए विकल्पों का उपयोग करके अपना दस्तावेज़ लोड करें, और वैकल्पिक रूप से PDF में सेव करके दृश्य प्रभाव देखें।  
- पता लगाएँ कि प्रतिस्थापन क्यों हुआ और, यदि आवश्यक हो, एक विशिष्ट फ़ॉलबैक फ़ॉन्ट को मजबूर करें।  

आपने अभी अपने **Aspose.Words** वर्कफ़्लो में एक सुरक्षा जाल जोड़ दिया है जो चुपचाप लेआउट परिवर्तन को रोकता है। अगला, आप `DefaultFontName` जैसे **फ़ॉन्ट सेटिंग्स** का अन्वेषण कर सकते हैं या PDF आउटपुट को फाइन‑ट्यून करने के लिए **डॉक्यूमेंट रेंडरिंग** विकल्पों में गहराई से जा सकते हैं।

---

### आगे क्या आज़माएँ?

- **अन्य FontSettings सुविधाओं** का अन्वेषण करें: `SetFontsFolder`, `LoadFontSources`, और `DefaultFontName`.  
- **चेतावनियों को लॉगिंग फ्रेमवर्क** (Serilog, NLog) के साथ मिलाएँ ताकि प्रोडक्शन‑ग्रेड डायग्नॉस्टिक्स मिलें।  
- **विभिन्न दस्तावेज़ फ़ॉर्मैट्स** (`.doc`, `.rtf`, `.html`) के साथ प्रयोग करें यह देखने के लिए कि प्रत्येक कैसे गायब फ़ॉन्ट्स को संभालता है।  

कोई प्रश्न या अजीब स्थिति है? नीचे टिप्पणी छोड़ें, और कोडिंग का आनंद लें!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}