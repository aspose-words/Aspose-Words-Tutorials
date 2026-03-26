---
category: general
date: 2026-03-25
description: कस्टम AI मॉडल बनाकर Word दस्तावेज़ों को संपादित करें – सीखें कि टेक्स्ट
  को अधिक औपचारिक कैसे बनाएं, पैराग्राफ का टेक्स्ट बदलें, और Aspose.Words AI का उपयोग
  करके Word पैराग्राफ को पुनर्लेखन करें।
draft: false
keywords:
- create custom ai model
- make text more formal
- replace paragraph text
- edit paragraph with ai
- rewrite word paragraph
language: hi
og_description: Word दस्तावेज़ों को संपादित करने के लिए कस्टम AI मॉडल बनाएं। जानिए
  कैसे टेक्स्ट को अधिक औपचारिक बनाएं, पैराग्राफ़ टेक्स्ट को बदलें, और Aspose.Words
  AI का उपयोग करके Word पैराग्राफ़ को पुनर्लेखित करें।
og_title: कस्टम एआई मॉडल बनाएं – जावा में शब्द पैराग्राफ संपादित करें
tags:
- Aspose.Words
- Java
- AI integration
title: कस्टम एआई मॉडल बनाएं – जावा में वर्ड पैराग्राफ संपादित करें
url: /hi/java/ai-machine-learning-integration/create-custom-ai-model-edit-word-paragraphs-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# कस्टम AI मॉडल बनाएं – जावा में Word पैराग्राफ संपादित करें

क्या आपको कभी **create custom AI model** की आवश्यकता पड़ी है जो Word फ़ाइल के भीतर किसी पैराग्राफ को निखार सके? शायद आपके पास कई अनुबंध हैं जो थोड़ा बहुत अनौपचारिक लगते हैं, और आप एक ही कोड लाइन से टेक्स्ट को अधिक औपचारिक बनाना चाहते हैं। अच्छी खबर यह है कि आप बिल्कुल वही कर सकते हैं—कोई बाहरी सेवा नहीं, कोई भारी SDK नहीं, सिर्फ Aspose.Words for Java और एक OpenAI‑compatible एंडपॉइंट।

इस ट्यूटोरियल में हम **create custom AI model** बनाने, उसे स्थानीय LLM सर्वर से जोड़ने, और फिर उसे *पैराग्राफ टेक्स्ट* को अधिक औपचारिक संस्करण से बदलने के लिए उपयोग करने के सभी चरणों से गुजरेंगे। अंत तक आपके पास एक चलाने योग्य जावा प्रोग्राम होगा जो **edit paragraph with AI** करता है, Word पैराग्राफ को पुनर्लेखित करता है, और परिणाम को डिस्क पर वापस सहेजता है। कोई फालतू बात नहीं, सिर्फ एक व्यावहारिक समाधान जिसे आप अपने प्रोजेक्ट में कॉपी‑पेस्ट कर सकते हैं।

> **आपको क्या चाहिए**  
> • Java 17 या उससे नया (कोड पहले के संस्करणों के साथ भी कम्पाइल हो सकता है, लेकिन 17 सबसे उपयुक्त है)  
> • Aspose.Words for Java 23.9 (या नवीनतम रिलीज)  
> • एक चल रहा OpenAI‑compatible LLM सर्वर (जैसे, Ollama, LocalAI) जो `http://localhost:8000/v1` पर सुन रहा हो  
> • एक इनपुट Word दस्तावेज़ (`input.docx`) जिसे आप नियंत्रित फ़ोल्डर में रखें  

यदि आप सोच रहे हैं *सीधे OpenAI को कॉल करने के बजाय कस्टम मॉडल बनाना क्यों*?, तो उत्तर लचीलापन है: आप एंडपॉइंट को नियंत्रित करते हैं, बिना कोड बदलें मॉडल बदल सकते हैं, और आप अपने स्रोत रिपॉज़िटरी से सभी API कुंजियों को बाहर रख सकते हैं। चलिए शुरू करते हैं।

---

## Create Custom AI Model – Setup and Configuration

सबसे पहले हमें Aspose.Words को यह बताना होगा कि हमारा LLM कहाँ स्थित है। `AiModelEndpoint` क्लास URL और वैकल्पिक API कुंजी को रखती है। क्योंकि हम स्थानीय सर्वर उपयोग कर रहे हैं, कुंजी खाली स्ट्रिंग हो सकती है, लेकिन पैरामीटर आवश्यक है।

```java
import com.aspose.words.ai.*;

public class LlmDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Define the LLM endpoint (OpenAI‑compatible)
        AiModelEndpoint llmEndpoint = new AiModelEndpoint(
                "http://localhost:8000/v1",   // URL of your LLM server
                "my-api-key");                // API key if required
```

> **Pro tip:** यदि आप कभी होस्टेड मॉडल (जैसे, Azure OpenAI) पर स्विच करते हैं, तो केवल URL और कुंजी बदलें—कोई अन्य कोड परिवर्तन आवश्यक नहीं।

---

## Load the Word Document

अब हम स्रोत फ़ाइल को मेमोरी में लाते हैं। `Document` `.docx`, `.doc`, `.rtf` और कई अन्य फ़ॉर्मेट पढ़ सकता है, लेकिन इस उदाहरण में हम `.docx` ही उपयोग करेंगे।

```java
        // Step 2: Load the source Word document
        Document document = new Document("YOUR_DIRECTORY/input.docx");
```

सुनिश्चित करें कि `YOUR_DIRECTORY` वास्तविक फ़ोल्डर की ओर इशारा कर रहा है; अन्यथा आपको `FileNotFoundException` मिलेगा। वास्तविक‑दुनिया के एप्लिकेशन में आप पाथ को कमांड‑लाइन आर्गुमेंट के रूप में पास कर सकते हैं या कॉन्फ़िग फ़ाइल से पढ़ सकते हैं।

---

## Initialize the Custom AI Model

हम `CUSTOM` प्रकार का `AiModel` बनाते हैं और उसे पहले परिभाषित एंडपॉइंट देते हैं। यह Aspose.Words को बताता है कि सभी AI कॉल हमारे अपने सर्वर के माध्यम से रूट हों।

```java
        // Step 3: Create a custom AI model that uses the endpoint
        AiModel llmModel = new AiModel(AiModelType.CUSTOM, llmEndpoint);
```

पर्दे के पीछे Aspose.Words एक छोटा HTTP क्लाइंट बनाता है जो मानक OpenAI चैट/कम्प्लीशन स्कीमा का उपयोग करके LLM से बात करता है। इसलिए एंडपॉइंट *OpenAI‑compatible* होना आवश्यक है।

---

## Retrieve and Rewrite the First Paragraph

यहीं पर हम वास्तव में **टेक्स्ट को अधिक औपचारिक** बनाते हैं। हम पहला पैराग्राफ लेते हैं, उसका कच्चा टेक्स्ट मॉडल को प्रॉम्प्ट के साथ भेजते हैं, और संपादित संस्करण प्राप्त करते हैं।

```java
        // Step 4: Retrieve the first paragraph and ask the model to rewrite it
        Paragraph firstParagraph = document.getFirstSection()
                                            .getBody()
                                            .getParagraphs()
                                            .get(0);
        String rewrittenText = llmModel.editText(
                firstParagraph.getText(),
                "Make it more formal");
```

दूसरा आर्गुमेंट (`"Make it more formal"`) वह निर्देश है जो हम मॉडल को देते हैं। आप इसे किसी भी निर्देश से बदल सकते हैं—**replace paragraph text**, **summarize**, **translate**, आदि। यह मेथड एक साधारण स्ट्रिंग लौटाता है, जिसे हम बाद में दस्तावेज़ में वापस डालेंगे।

> **यह क्यों काम करता है:** `editText` एक JSON पेलोड जैसे `{ "model": "...", "messages": [{ "role":"user", "content":"<text>\nMake it more formal"}] }` भेजता है। LLM मूल पैराग्राफ और निर्देश देखता है, फिर संशोधित टेक्स्ट के साथ जवाब देता है।

---

## Replace the Original Paragraph Content

अब हम Word ऑब्जेक्ट मॉडल के भीतर **paragraph text** को बदलते हैं। हम मौजूदा सभी रन (टेक्स्ट के लो‑लेवल टुकड़े) को साफ़ करते हैं और AI‑जनरेटेड स्ट्रिंग वाले नए `Run` को डालते हैं।

```java
        // Step 5: Replace the original paragraph content with the rewritten text
        firstParagraph.removeAllChildren();
        firstParagraph.appendChild(new Run(document, rewrittenText));
```

ध्यान रखें कि `firstParagraph.setText()` को कॉल न करें—यह मेथड सभी फ़ॉर्मेटिंग हटा देगा। `Run` का उपयोग करने से पैराग्राफ की शैली (हेडिंग, बुलेट आदि) बनी रहती है जबकि वास्तविक अक्षर बदल जाते हैं।

---

## Save the Edited Document

अंत में, हम संशोधित दस्तावेज़ को डिस्क पर वापस लिखते हैं। आप मूल फ़ाइल को ओवरराइट कर सकते हैं या, जैसा कि यहाँ किया गया है, एक नई कॉपी बना सकते हैं।

```java
        // Step 6: Save the edited document
        document.save("YOUR_DIRECTORY/output.docx");
    }
}
```

जब आप `output.docx` खोलेंगे तो आपको पहला पैराग्राफ अब काफी अधिक औपचारिक सुनाई देगा। यदि LLM ने निर्देश को पूरी तरह नहीं माना, तो आप प्रॉम्प्ट को समायोजित कर सकते हैं या अलग मॉडल संस्करण आज़मा सकते हैं।

---

## Full Working Example

नीचे पूरा प्रोग्राम दिया गया है—इसे `LlmDemo.java` में कॉपी करें, पाथ को समायोजित करें, और `javac` + `java` के साथ चलाएँ।

```java
import com.aspose.words.*;
import com.aspose.words.ai.*;

public class LlmDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Define the LLM endpoint (OpenAI‑compatible)
        AiModelEndpoint llmEndpoint = new AiModelEndpoint(
                "http://localhost:8000/v1",   // URL of your LLM server
                "my-api-key");                // API key if required

        // Step 2: Load the source Word document
        Document document = new Document("YOUR_DIRECTORY/input.docx");

        // Step 3: Create a custom AI model that uses the endpoint
        AiModel llmModel = new AiModel(AiModelType.CUSTOM, llmEndpoint);

        // Step 4: Retrieve the first paragraph and ask the model to rewrite it
        Paragraph firstParagraph = document.getFirstSection()
                                            .getBody()
                                            .getParagraphs()
                                            .get(0);
        String rewrittenText = llmModel.editText(
                firstParagraph.getText(),
                "Make it more formal");

        // Step 5: Replace the original paragraph content with the rewritten text
        firstParagraph.removeAllChildren();
        firstParagraph.appendChild(new Run(document, rewrittenText));

        // Step 6: Save the edited document
        document.save("YOUR_DIRECTORY/output.docx");
    }
}
```

**अपेक्षित आउटपुट:** `output.docx` खोलें और आप देखेंगे कि मूल पैराग्राफ बदल गया है। उदाहरण के लिए, “We’ll get the thing done soon.” जैसी अनौपचारिक वाक्य “We shall complete the task promptly.” में बदल सकती है। सटीक शब्दावली आपके द्वारा उपयोग किए जा रहे मॉडल पर निर्भर करेगी।

---

## Common Questions & Edge Cases

### What if my document has multiple sections?

ऊपर दिया गया कोड केवल *पहले* सेक्शन के *पहले* पैराग्राफ को छूता है। पूरे फ़ाइल में **edit paragraph with AI** करने के लिए `document.getSections()` पर लूप करें और फिर प्रत्येक `section.getBody().getParagraphs()` पर इटररेट करें। खाली पैराग्राफ को स्किप करना याद रखें, नहीं तो LLM को खाली स्ट्रिंग मिलेगी और वह कुछ नहीं लौटाएगा।

### How do I handle large paragraphs that exceed token limits?

अधिकतर LLM इनपुट को लगभग 4 000 टोकन तक सीमित रखते हैं। यदि कोई पैराग्राफ असामान्य रूप से लंबा है, तो उसे छोटे हिस्सों में विभाजित करके `editText` को कॉल करें। आप वही `AiModel` इंस्टेंस पुनः उपयोग कर सकते हैं; बस अपने स्थानीय सर्वर पर रेट लिमिट्स का ध्यान रखें।

### Can I use a different instruction, like “summarize” or “translate to French”?

बिल्कुल। `editText` का दूसरा आर्गुमेंट फ्री‑फ़ॉर्म है। सारांश के लिए आप `"Summarize in one sentence"` पास कर सकते हैं। अनुवाद के लिए `"Translate to French, keep the tone formal"` भी ठीक रहेगा। यह लचीलापन आपको कई परिदृश्यों में **replace paragraph text** करने देता है बिना कोड बदले।

### Does the model preserve paragraph styling (fonts, colors)?

क्योंकि हम केवल उसी `Paragraph` ऑब्जेक्ट के भीतर `Run` को बदलते हैं, मौजूदा शैलियाँ (हेडिंग लेवल, बुलेट लिस्ट, इंडेंटेशन) अपरिवर्तित रहती हैं। यदि आपको शैली स्वयं बदलनी है, तो प्रतिस्थापन के बाद `Paragraph.getParagraphFormat()` को मैनीपुलेट कर सकते हैं।

### What if my LLM server requires HTTPS with a self‑signed certificate?

`AiModelEndpoint` `https://` वाले URL को स्वीकार करता है। यदि प्रमाणपत्र विश्वसनीय नहीं है, तो आपको Java के SSL कॉन्टेक्स्ट को भरोसा करने के लिए कॉन्फ़िगर करना होगा, या सर्वर को वैध प्रमाणपत्र के साथ चलाना होगा। यह सेटअप इस ट्यूटोरियल के दायरे से बाहर है लेकिन Java SSL गाइड्स में अच्छी तरह से दस्तावेज़ित है।

---

## Tips for Production‑Ready Integration

| Tip | Why it matters |
|-----|----------------|
| **Cache the endpoint** | हर अनुरोध पर `AiModelEndpoint` को पुनः बनाना ओवरहेड जोड़ता है। |
| **Batch edits** | यदि कई पैराग्राफ हैं, तो उन्हें एक ही अनुरोध (जैसे, JSON एरे) में भेजें ताकि लेटेंसी कम हो। |
| **Validate LLM output** | `null` या खाली स्ट्रिंग मिलने पर हमेशा जांचें, फिर ही इन्सर्ट करें। |
| **Log prompts and responses** | डिबगिंग और अनुपालन के लिए उपयोगी जब आप कानूनी टेक्स्ट को पुनर्लेखित कर रहे हों। |
| **Graceful fallback** | यदि LLM डाउन हो, तो मूल पैराग्राफ या कोई साधारण री‑राइट एल्गोरिद्म उपयोग करें। |

---

## Conclusion

हमने दिखाया कि कैसे Aspose.Words के साथ **create custom AI model** बनाकर उसे OpenAI‑compatible एंडपॉइंट से जोड़ा जाए, और फिर **edit paragraph with AI** करके **टेक्स्ट को अधिक औपचारिक** बनाया जाए। इन छह चरणों—एंडपॉइंट परिभाषित करना, दस्तावेज़ लोड करना, मॉडल इनिशियलाइज़ करना, पैराग्राफ प्राप्त करना, उसे बदलना, और फ़ाइल सहेजना—को फॉलो करके आप अपना समाधान तुरंत लागू कर सकते हैं।

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}