---
category: general
date: 2026-02-13
description: C# में PNG को जल्दी से Base64 में बदलें – सीखें कि कैसे इमेज को Base64
  एन्कोड करें, HTML में इमेज को Base64 के रूप में एम्बेड करें, और वेब प्रोजेक्ट्स
  के लिए स्ट्रीम को मेमोरी में कॉपी करें।
draft: false
keywords:
- convert png to base64
- base64 encode image
- embed image html base64
- image stream to base64
- copy stream to memory
language: hi
og_description: C# में PNG को जल्दी से Base64 में बदलें। यह ट्यूटोरियल दिखाता है कि
  कैसे इमेज को Base64 एन्कोड करें, इमेज को HTML Base64 में एम्बेड करें, और स्ट्रीम
  को मेमोरी में कॉपी करें।
og_title: C# में PNG को Base64 में बदलें – पूर्ण गाइड
tags:
- C#
- image-processing
- data-uri
title: C# में PNG को Base64 में बदलें – पूर्ण गाइड
url: /hi/net/basic-conversions/convert-png-to-base64-in-c-complete-guide/
---

translated alt text and title.

Now produce final content.{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# PNG को Base64 में बदलें C# में – पूर्ण गाइड

क्या आपको कभी **convert PNG to Base64** करने की ज़रूरत पड़ी लेकिन शुरुआत नहीं पता थी? आप अकेले नहीं हैं; कई डेवलपर्स इस समस्या का सामना करते हैं जब वे इमेजेज़ को सीधे HTML या CSS में एम्बेड करने की कोशिश करते हैं। अच्छी खबर यह है कि सही कदम जानने पर समाधान काफी सरल है।

इस ट्यूटोरियल में हम एक पूर्ण, चलाने योग्य उदाहरण के माध्यम से चलेंगे जो **base64 encode image** डेटा को दिखाता है, आपको **embed image html base64** को डेटा‑URI के माध्यम से एम्बेड करना सिखाता है, और यहाँ तक कि **copy stream to memory** को बिना संसाधन लीक किए करने का सबसे अच्छा तरीका भी समझाता है। अंत तक आपके पास एक पुन: उपयोग योग्य स्निपेट होगा जिसे आप किसी भी .NET प्रोजेक्ट में डाल सकते हैं।

## आप क्या सीखेंगे

- फ़ाइल की एक्सटेंशन को केस‑इंसेंसिटिव तरीके से सत्यापित करने का तरीका।  
- `MemoryStream` का उपयोग करके **image stream to base64** को बदलने का सबसे सुरक्षित पैटर्न।  
- ब्राउज़र द्वारा समझे जाने वाला उचित डेटा‑URI बनाना।  
- मूल स्ट्रीम को साफ़ करना ताकि आपका ऐप हल्का रहे।  

कोई बाहरी लाइब्रेरी आवश्यक नहीं है—सिर्फ .NET के साथ आने वाले BCL क्लासेस। यदि आप C# की बुनियादी बातों में सहज हैं और आपका प्रोजेक्ट पहले से फ़ाइल अपलोड को संभालता है, तो आप तैयार हैं।

---

![PNG फ़ाइल से Base64 डेटा‑URI तक के प्रवाह को दर्शाता आरेख – convert png to base64](https://example.com/convert-png-to-base64-diagram.png "convert png to base64 उदाहरण")

## PNG को Base64 में बदलें – चरण‑दर‑चरण

नीचे हम प्रक्रिया को पाँच तार्किक चरणों में विभाजित करते हैं। प्रत्येक हेडर पहेली के एक टुकड़े को दर्शाता है, जिससे आपके (और AI सहायक) लिए आवश्यक भाग को ढूँढना आसान हो जाता है।

### चरण 1: संसाधन PNG है या नहीं सत्यापित करें (केस‑इंसेंसिटिव)

मेमोरी बर्बाद करने से पहले, हम पुष्टि करते हैं कि आने वाली फ़ाइल वास्तव में PNG है। `StringComparison.OrdinalIgnoreCase` फ़्लैग अपर‑ या लोअर‑केस एक्सटेंशन के किसी भी मिश्रण को संभालता है।

```csharp
// Step 1: Verify that the resource is a PNG image (case‑insensitive)
if (args.ResourceFileExtension.Equals(".png", StringComparison.OrdinalIgnoreCase))
{
    // Continue with conversion...
}
else
{
    // Not a PNG – you might log or throw here
    throw new InvalidOperationException("Only PNG files are supported.");
}
```

*क्यों यह महत्वपूर्ण है:* Trying to encode a non‑image (or a JPEG) as PNG could corrupt the output and break the data‑URI you later embed.

### चरण 2: स्ट्रीम को मेमोरी में कॉपी करें

आने वाला `Stream` (शायद एक अपलोड हैंडलर से) पूरी तरह पढ़ा जाना चाहिए। `using var` स्टेटमेंट का उपयोग करने से बफ़र स्वचालित रूप से डिस्पोज़ हो जाता है, जिससे **copy stream to memory** साफ़ रहता है।

```csharp
using var memory = new MemoryStream();
args.Stream.CopyTo(memory);
```

*Pro tip:* यदि आप बहुत बड़ी फ़ाइलों से निपट रहे हैं, तो थ्रेड ब्लॉकिंग से बचने के लिए उचित बफ़र आकार के साथ `CopyToAsync` पर विचार करें।

### चरण 3: इमेज को Base64 एन्कोड करें

अब जब इमेज बाइट्स `memory` में हैं, हम उन्हें Base64 स्ट्रिंग में बदल सकते हैं। यह **base64 encode image** का मूल है।

```csharp
// Step 3: Encode the buffered bytes as a Base64 string
string base64Data = Convert.ToBase64String(memory.ToArray());
```

*क्या हो रहा है?* `Convert.ToBase64String` एक बाइट एरे लेता है और टेक्स्टुअल प्रतिनिधित्व लौटाता है जिसे ब्राउज़र बाइनरी डेटा में वापस डिकोड कर सकते हैं।

### चरण 4: HTML/CSS के लिए डेटा‑URI बनाएं

डेटा‑URI आपको इमेज को सीधे मार्कअप में एम्बेड करने देता है, अतिरिक्त HTTP अनुरोधों को समाप्त करता है। फ़ॉर्मेट है `data:[<mediatype>][;base64],<data>`।

```csharp
// Step 4: Build a data‑URI that embeds the PNG directly in HTML/CSS
args.ResourceFilePath = $"data:image/png;base64,{base64Data}";
```

जब आप बाद में `<img src="...">` टैग के अंदर `args.ResourceFilePath` रेंडर करेंगे, तो ब्राउज़र तुरंत PNG दिखाएगा।

### चरण 5: मूल स्ट्रीम को रिलीज़ करें

चूंकि इमेज अब डेटा‑URI द्वारा प्रतिनिधित्व किया गया है, मूल `Stream` अब आवश्यक नहीं है। इसे `null` सेट करने से गार्बेज कलेक्टर अंतर्निहित सॉकेट या फ़ाइल हैंडल को पुनः प्राप्त करने में मदद करता है।

```csharp
// Step 5: Release the original stream because the resource is now embedded
args.Stream = null;
```

*Edge case:* यदि आपको बाद में मूल फ़ाइल चाहिए (जैसे डिस्क पर स्टोर करने के लिए), तो इस चरण को छोड़ दें और कहीं और रेफ़रेंस रखें।

---

## पूर्ण कार्यशील उदाहरण

सभी हिस्सों को मिलाकर एक कॉम्पैक्ट मेथड बनता है जिसे आप किसी भी क्लास में पेस्ट कर सकते हैं जो अपलोडेड रिसोर्सेज़ को प्रोसेस करता है।

```csharp
using System;
using System.IO;

public class ResourceProcessor
{
    public void ProcessPng(ResourceArgs args)
    {
        // Verify extension (primary check)
        if (!args.ResourceFileExtension.Equals(".png", StringComparison.OrdinalIgnoreCase))
        {
            throw new InvalidOperationException("Only PNG files can be converted to Base64.");
        }

        // Copy the incoming stream into a memory buffer (copy stream to memory)
        using var memory = new MemoryStream();
        args.Stream.CopyTo(memory);

        // Encode the buffered bytes as a Base64 string (base64 encode image)
        string base64Data = Convert.ToBase64String(memory.ToArray());

        // Build a data‑URI that embeds the PNG directly in HTML/CSS (embed image html base64)
        args.ResourceFilePath = $"data:image/png;base64,{base64Data}";

        // Release the original stream because the resource is now embedded (image stream to base64)
        args.Stream = null;
    }
}

// Helper class to mimic incoming arguments
public class ResourceArgs
{
    public string ResourceFileExtension { get; set; }   // e.g., ".png"
    public Stream Stream { get; set; }                 // original file stream
    public string ResourceFilePath { get; set; }       // will hold the data‑URI
}
```

**Expected output:** `ProcessPng` चलने के बाद, `args.ResourceFilePath` में एक स्ट्रिंग होगी जो इस प्रकार दिखती है:

```
data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAA...
```

अब आप उस स्ट्रिंग को सीधे `<img>` टैग में डाल सकते हैं:

```html
<img src="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAA..." alt="Converted PNG">
```

इमेज तुरंत दिखाई देती है, बिना किसी अतिरिक्त नेटवर्क ट्रैफ़िक के।

---

## सामान्य प्रश्न और किनारे के मामलों

### अगर PNG बहुत बड़ा हो तो क्या?

बड़ी इमेजेज़ मेमोरी उपयोग को बढ़ा सकती हैं क्योंकि पूरी फ़ाइल `MemoryStream` में रहती है। कुछ मेगाबाइट से बड़ी फ़ाइलों के लिए, बेस64 कन्वर्ज़न को चंक्स में स्ट्रीम करने या एन्कोड करने से पहले इमेज को रिसाइज़ करने पर विचार करें।

### क्या मैं इसे async बना सकता हूँ?

बिल्कुल। `CopyTo` को `CopyToAsync` से बदलें और मेथड को `async Task` के रूप में मार्क करें। इससे आपका ASP.NET अनुरोध थ्रेड I/O पूरा होने तक मुक्त रहता है।

```csharp
await args.Stream.CopyToAsync(memory);
```

### क्या यह अन्य इमेज फ़ॉर्मेट्स के साथ काम करता है?

कोड स्वयं फ़ॉर्मेट‑अज्ञेय है; आपको केवल डेटा‑URI में MIME टाइप (`image/jpeg`, `image/gif`, आदि) को समायोजित करना है और एक्सटेंशन चेक को उसी अनुसार बदलना है।

### मैं त्रुटियों को सुगमता से कैसे संभालूँ?

पूरे ब्लॉक को `try/catch` में रैप करें और एक्सेप्शन को लॉग करें। यदि आप वेब API में हैं, तो एक सहायक संदेश के साथ 400 Bad Request लौटाएँ।

---

## निष्कर्ष

अब आप जानते हैं कि C# में **convert PNG to Base64** कैसे किया जाता है, शुरुआत से अंत तक। ट्यूटोरियल ने फ़ाइल प्रकार की पुष्टि, स्ट्रीम को सुरक्षित रूप से मेमोरी में कॉपी करना, **base64 encode image** करना, उचित **embed image html base64** डेटा‑URI बनाना, और संसाधनों को साफ़ करना कवर किया।  

अब आप ऑन‑द‑फ्लाई इमेज रिसाइज़िंग, जेनरेटेड डेटा‑URIs को कैश करने, या यहां तक कि SVG प्लेसहोल्डर बनाने का अन्वेषण कर सकते हैं। जो भी आप चुनें, ऊपर दिखाया गया पैटर्न किसी भी स्थिति में जहाँ आपको **image stream to base64** को बदलना और सीधे मार्कअप में एम्बेड करना हो, एक ठोस आधार प्रदान करेगा।

क्या आपके पास इस वर्कफ़्लो में कोई नया मोड़ है? शायद आप WebAssembly या Blazor के साथ काम कर रहे हैं—कमेंट्स में अपने प्रयोग साझा करने में संकोच न करें। कोडिंग का आनंद लें!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}