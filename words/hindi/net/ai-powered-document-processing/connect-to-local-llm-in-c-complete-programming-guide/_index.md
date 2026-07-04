---
category: general
date: 2026-04-28
description: C# से स्थानीय LLM से कनेक्ट करें और बड़े भाषा मॉडल को वर्ड दस्तावेज़
  लोड करने के लिए प्रॉम्प्ट करें, स्थानीय LLM को कॉल करें और टेक्स्ट को स्वचालित रूप
  से पुनः लिखें। चरण‑दर‑चरण कोड शामिल है।
draft: false
keywords:
- connect to local llm
- prompt large language model
- load word document
- call local llm
- rewrite text automatically
language: hi
og_description: C# से स्थानीय LLM से कनेक्ट करें और देखें कैसे बड़े भाषा मॉडल को प्रॉम्प्ट
  करें, वर्ड दस्तावेज़ लोड करें, स्थानीय LLM को कॉल करें और मिनटों में स्वचालित रूप
  से टेक्स्ट को पुनर्लेखित करें।
og_title: C# में स्थानीय LLM से कनेक्ट करें – पूर्ण प्रोग्रामिंग गाइड
tags:
- Aspose.Words
- C#
- LLM
- AI Automation
title: C# में स्थानीय LLM से कनेक्ट करें – पूर्ण प्रोग्रामिंग गाइड
url: /hi/net/ai-powered-document-processing/connect-to-local-llm-in-c-complete-programming-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C# में स्थानीय LLM से कनेक्ट करें – पूर्ण प्रोग्रामिंग गाइड

क्या आपको कभी .NET एप्लिकेशन से **स्थानीय llm** से कनेक्ट करने की ज़रूरत पड़ी और सोचा कि इसे Word फ़ाइल से कैसे बात करवाई जाए? आप अकेले नहीं हैं। इस गाइड में हम पूरी प्रक्रिया को समझेंगे—स्थानीय llm से कनेक्ट करना, **prompt large language model**, Word दस्तावेज़ लोड करना, **call local llm**, और अंत में **rewrite text automatically**। अंत तक आपके पास एक चलाने योग्य नमूना होगा जो किसी भी पैराग्राफ को शून्य बाहरी API कुंजियों के साथ औपचारिक स्वर में बदल देगा।

## इस ट्यूटोरियल में क्या कवर किया गया है

हम आवश्यक NuGet पैकेज स्थापित करके शुरू करेंगे, फिर एक सरल स्थानीय LLM एंडपॉइंट (जैसे Ollama पोर्ट 11434 पर) चलाएंगे। उसके बाद हम Aspose.Words का उपयोग करके एक `.docx` फ़ाइल लोड करेंगे, पैराग्राफ को LLM को भेजेंगे, पुनर्लिखित संस्करण प्राप्त करेंगे, और उसे उसी दस्तावेज़ में वापस लिखेंगे। आप सामान्य समस्याओं—null पैराग्राफ, async डिस्पोज़ल, और एन्कोडिंग क्विर्क्स—को कैसे संभालें, भी देखेंगे—ताकि कोड प्रोडक्शन में काम करे, सिर्फ डेमो नहीं।

### आवश्यकताएँ

- .NET 6.0 SDK या बाद का (आप .NET 8 भी उपयोग कर सकते हैं)
- Visual Studio 2022 या VS Code के साथ C# एक्सटेंशन
- **Aspose.Words for .NET** (फ्री ट्रायल ठीक काम करता है)
- `/api/generate` कॉन्ट्रैक्ट को सपोर्ट करने वाला स्थानीय रूप से होस्ट किया गया LLM (जैसे, Ollama, LMStudio)
- C# में async/await की बुनियादी समझ

> **Pro tip:** यदि आपने अभी तक Ollama स्थापित नहीं किया है, तो `ollama serve` चलाएँ और `ollama pull llama3` से मॉडल पुल करें। डिफ़ॉल्ट HTTP एंडपॉइंट `http://localhost:11434/api/generate` होगा।

---

## चरण 1: आवश्यक पैकेज स्थापित करें

सबसे पहले, अपने प्रोजेक्ट में Aspose.Words और Aspose.Words.AI NuGet पैकेज जोड़ें।

```bash
dotnet add package Aspose.Words
dotnet add package Aspose.Words.AI
```

ये लाइब्रेरी हमें **load word document** क्षमता देती हैं और **call local llm** के लिए एक हल्का रैपर प्रदान करती हैं, बिना हाथ से HTTP अनुरोध लिखे।

---

## चरण 2: स्थानीय LLM एंडपॉइंट से कनेक्ट करें

स्थानीय रूप से होस्ट किए गए मॉडल से कनेक्ट करना उतना ही सरल है जितना `LocalLargeLanguageModel` को इंस्टैंशिएट करना। कंस्ट्रक्टर को जेनरेशन एंडपॉइंट का पूरा URL चाहिए।

```csharp
using Aspose.Words.AI;
using Aspose.Words;
using System.Threading.Tasks;

// Create a client that talks to the LLM running on localhost
var localLlm = new LocalLargeLanguageModel("http://localhost:11434/api/generate");
```

हम एंडपॉइंट को क्लास में क्यों रैप करते हैं? `LocalLargeLanguageModel` आपके लिए JSON सीरियलाइज़ेशन, रीट्राईज़, और स्ट्रीमिंग रिस्पॉन्स को संभालता है—ताकि आप `HttpClient` के साथ झंझट किए बिना प्रॉम्प्ट लॉजिक पर ध्यान दे सकें।

---

## चरण 3: स्रोत Word दस्तावेज़ लोड करें

अब हम दस्तावेज़ को मेमोरी में लाते हैं। Aspose.Words लगभग सभी Word फ़ॉर्मेट को सपोर्ट करता है, इसलिए `Document` `input.docx` को बिना Office इंस्टॉल किए पार्स कर लेगा।

```csharp
// Path to the source file – adjust as needed
string inputPath = Path.Combine(Environment.CurrentDirectory, "input.docx");

// Load the document; throws if the file is missing or corrupted
Document sourceDocument = new Document(inputPath);
```

यदि आपको स्ट्रीम के साथ काम करना है (जैसे, ASP.NET के माध्यम से अपलोड की गई फ़ाइल), तो फ़ाइल पाथ को `MemoryStream` से बदलें और उसे `Document` कंस्ट्रक्टर में पास करें।

---

## चरण 4: वर्तमान पैराग्राफ टेक्स्ट निकालें

हम दस्तावेज़ को नेविगेट करने के लिए `DocumentBuilder` का उपयोग करेंगे। इस उदाहरण में हम **पहले पैराग्राफ** को पुनर्लिखते हैं, लेकिन आप कई पैराग्राफ प्रोसेस करने के लिए `sourceDocument.GetChildNodes(NodeType.Paragraph, true)` पर इटरेट कर सकते हैं।

```csharp
// Builder gives us a cursor inside the document
DocumentBuilder docBuilder = new DocumentBuilder(sourceDocument);

// Grab the text of the paragraph where the builder is currently positioned
string originalParagraph = docBuilder.CurrentParagraph?.GetText() ?? string.Empty;

// Safety check – avoid sending empty strings to the LLM
if (string.IsNullOrWhiteSpace(originalParagraph))
{
    Console.WriteLine("No paragraph found at the current cursor position.");
    return;
}
```

`?.` ऑपरेटर `NullReferenceException` को रोकता है यदि दस्तावेज़ खाली हो। यह उन **edge cases** में से एक है जो शुरुआती लोगों को फँसाते हैं।

---

## चरण 5: पैराग्राफ को पुनर्लिखने के लिए LLM को प्रॉम्प्ट करें

अब हम वास्तव में **prompt large language model** करते हैं। प्रॉम्प्ट साधारण अंग्रेज़ी में है; रैपर इसे JSON के रूप में स्थानीय एंडपॉइंट पर भेजेगा।

```csharp
// Build a friendly instruction for the model
string prompt = $"Rewrite the following sentence in a more formal tone:\n{originalParagraph}";

// Await the model's response – this is an async call
string rewrittenParagraph = await localLlm.PromptAsync(prompt);
```

इस तरह अनुरोध को क्यों लिखते हैं? LLM स्पष्ट, एक‑कार्य निर्देशों पर सबसे अच्छा जवाब देते हैं। कॉलन के बाद नई लाइन जोड़ने से निर्देश और सामग्री अलग हो जाती है, जिससे मॉडल के प्रॉम्प्ट को दोहराने की संभावना कम हो जाती है।

**Expected output** – यदि `originalParagraph` `"Hey, what's up?"` था, तो LLM इस तरह उत्तर दे सकता है:

> “Good day, how may I assist you?”

आप परिणाम को प्रिंट करके सत्यापित कर सकते हैं:

```csharp
Console.WriteLine("Original:  " + originalParagraph);
Console.WriteLine("Rewritten: " + rewrittenParagraph);
```

---

## चरण 6: पुनर्लिखित टेक्स्ट को दस्तावेज़ में वापस डालें

नया टेक्स्ट हाथ में होने पर, हम पुराने पैराग्राफ को बदलते हैं। `DocumentBuilder.Writeln` नई लाइन लिखता है और कर्सर को आगे ले जाता है, जो जोड़ने के लिए उपयुक्त है। यदि आपको बिल्कुल वही पैराग्राफ *बदलना* है, तो लिखने से पहले `docBuilder.CurrentParagraph.RemoveAllChildren()` उपयोग कर सकते हैं।

```csharp
// Option A – Append a new paragraph (keeps the original)
docBuilder.Writeln(rewrittenParagraph);

// Option B – Replace the existing paragraph (uncomment to use)
// docBuilder.CurrentParagraph.RemoveAllChildren();
// docBuilder.CurrentParagraph.AppendChild(new Run(docBuilder.Document, rewrittenParagraph));
```

दोनों तरीकों को दिखाया गया है ताकि आप अपने वर्कफ़्लो के अनुसार चुन सकें।

---

## चरण 7: अपडेटेड दस्तावेज़ को सेव करें

अंत में, हम बदलावों को नई फ़ाइल में सहेजते हैं। Aspose.Words फ़ाइल एक्सटेंशन के आधार पर फ़ॉर्मेट स्वचालित रूप से चुन लेता है।

```csharp
string outputPath = Path.Combine(Environment.CurrentDirectory, "output.docx");
sourceDocument.Save(outputPath);

Console.WriteLine($"Document saved to {outputPath}");
```

`output.docx` को Word में खोलें, और आप देखेंगे कि पैराग्राफ अब औपचारिक स्वर में पढ़ा जाता है।

---

## पूर्ण कार्यशील उदाहरण

नीचे **पूर्ण, स्व-निहित प्रोग्राम** है। इसे कॉपी‑पेस्ट करके एक कंसोल प्रोजेक्ट में रखें, NuGet पैकेज रिस्टोर करें, और चलाएँ—स्थानीय LLM चल रहा हो तो अतिरिक्त कॉन्फ़िगरेशन की ज़रूरत नहीं।

```csharp
using Aspose.Words.AI;
using Aspose.Words;
using System;
using System.IO;
using System.Threading.Tasks;

class Program
{
    static async Task Main()
    {
        // -------------------------------------------------
        // Step 1: Connect to the locally hosted LLM endpoint
        // -------------------------------------------------
        var localLlm = new LocalLargeLanguageModel("http://localhost:11434/api/generate");

        // -------------------------------------------------
        // Step 2: Load the source Word document
        // -------------------------------------------------
        string inputPath = Path.Combine(Environment.CurrentDirectory, "input.docx");
        Document sourceDocument = new Document(inputPath);

        // -------------------------------------------------
        // Step 3: Retrieve the text of the current paragraph
        // -------------------------------------------------
        DocumentBuilder docBuilder = new DocumentBuilder(sourceDocument);
        string originalParagraph = docBuilder.CurrentParagraph?.GetText() ?? string.Empty;

        if (string.IsNullOrWhiteSpace(originalParagraph))
        {
            Console.WriteLine("No paragraph found at the current cursor position.");
            return;
        }

        // -------------------------------------------------
        // Step 4: Ask the LLM to rewrite the paragraph in a formal tone
        // -------------------------------------------------
        string prompt = $"Rewrite the following sentence in a more formal tone:\n{originalParagraph}";
        string rewrittenParagraph = await localLlm.PromptAsync(prompt);

        // -------------------------------------------------
        // Step 5: Insert the rewritten text back into the document
        // -------------------------------------------------
        docBuilder.Writeln(rewrittenParagraph);

        // -------------------------------------------------
        // Step 6: Save the updated document
        // -------------------------------------------------
        string outputPath = Path.Combine(Environment.CurrentDirectory, "output.docx");
        sourceDocument.Save(outputPath);

        Console.WriteLine("Original paragraph:");
        Console.WriteLine(originalParagraph);
        Console.WriteLine("\nRewritten paragraph:");
        Console.WriteLine(rewrittenParagraph);
        Console.WriteLine($"\nDocument saved to {outputPath}");
    }
}
```

### चलाने पर क्या उम्मीद रखें

1. कंसोल मूल और पुनर्लिखित पैराग्राफ प्रिंट करता है।  
2. `output.docx` `input.docx` के बगल में दिखाई देता है।  
3. फ़ाइल खोलने पर नया औपचारिक पैराग्राफ मूल के बाद (या यदि आप वैकल्पिक कोड पर स्विच किए हैं तो बदला हुआ) दिखता है।

---

## सामान्य Edge Cases को संभालना

| Situation | Solution |
|-----------|----------|
| **खाली या केवल व्हाइटस्पेस वाला पैराग्राफ** | `Prompt` करने से पहले `string.IsNullOrWhiteSpace` जांचें (Step 3 देखें)। |
| **LLM त्रुटि या खाली स्ट्रिंग लौटाता है** | `PromptAsync` को `try/catch` में रैप करें और मूल टेक्स्ट पर वापस जाएँ। |
| **कई पैराग्राफ को पुनर्लिखने की आवश्यकता** | `sourceDocument.GetChildNodes(NodeType.Paragraph, true)` पर लूप करें और वही प्रॉम्प्ट लॉजिक लागू करें। |
| **बड़े दस्तावेज़ लेटेंसी पैदा करते हैं** | पैराग्राफ को बैच करें और एक ही अनुरोध में भेजें (प्रॉम्प्ट प्रति कॉल अधिकतम 4 KB)। |
| **Non‑ASCII अक्षर गड़बड़ हो जाते हैं** | सुनिश्चित करें कि LLM एंडपॉइंट UTF‑8 उपयोग करता है (अधिकांश आधुनिक मॉडल ऐसा करते हैं)। |

---

## अगले कदम और संबंधित विषय

- **Prompt large language model** को अधिक विस्तृत निर्देशों के साथ उपयोग करें (जैसे, स्टाइल गाइड, लंबाई सीमा)।
- **call local llm** को वेब API में उपयोग करके दस्तावेज़‑ऑटोमेशन को सर्विस के रूप में एक्सपोज़ करें।
- **load word document** को समानांतर स्ट्रीम में एक्सप्लोर करें उच्च‑थ्रूपुट परिदृश्यों के लिए।
- इस दृष्टिकोण को **rewrite text automatically** के साथ मिलाकर बल्क ईमेल जेनरेशन या रिपोर्ट मानकीकरण के लिए उपयोग करें।

यदि आप और गहराई में जाना चाहते हैं, तो Aspose की **document merging** दस्तावेज़ीकरण और कस्टम सैंपलिंग पैरामीटर के लिए Ollama API रेफ़रेंस देखें।

---

## निष्कर्ष

हमने अभी दिखाया कि कैसे **connect to local llm** को C# से, **prompt large language model**, **load word document**, **call local llm**, और **rewrite text automatically**—एक ही चलाने योग्य कंसोल ऐप में किया जाए। यह पैटर्न स्केलेबल है: प्रॉम्प्ट बदलें, पैराग्राफ पर इटरेट करें, या लॉजिक को ASP.NET एंडपॉइंट के माध्यम से एक्सपोज़ करें। मुख्य बात यह है कि स्थानीय AI मॉडल क्लासिक दस्तावेज़‑प्रोसेसिंग लाइब्रेरी के साथ कसकर इंटीग्रेट किए जा सकते हैं, जिससे आप भरोसेमंद ऑन‑प्रेम वातावरण से बाहर निकले बिना शक्तिशाली ऑटोमेशन प्राप्त कर सकते हैं।

थ्रेडिंग के बारे में प्रश्न हैं,

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}