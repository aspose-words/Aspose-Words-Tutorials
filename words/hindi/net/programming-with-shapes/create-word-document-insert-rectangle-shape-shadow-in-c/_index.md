---
category: general
date: 2026-05-26
description: C# में Aspose.Words का उपयोग करके Word दस्तावेज़ बनाएं, आयताकार आकार
  डालें, भराव रंग सेट करें, और शैडो इफ़ेक्ट जोड़ें – चरण‑दर‑चरण गाइड।
draft: false
keywords:
- create word document
- insert rectangle shape
- how to add shadow
- how to insert shape
- how to set fill
language: hi
og_description: Aspose.Words का उपयोग करके C# में Word दस्तावेज़ बनाएं। सीखें कि कैसे
  एक आयताकार आकार डालें, उसका भराव रंग सेट करें, और एक छाया प्रभाव जोड़ें।
og_title: Word दस्तावेज़ बनाएं – C# में आयताकार आकार और छाया सम्मिलित करें
schemas:
- author: Aspose
  dateModified: '2026-05-26'
  description: Create Word document in C# with Aspose.Words, insert rectangle shape,
    set fill color, and add shadow effect – step‑by‑step guide.
  headline: Create Word Document – Insert Rectangle Shape & Shadow in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: वर्ड दस्तावेज़ बनाएं – C# में आयताकार आकार और छाया डालें
url: /hi/net/programming-with-shapes/create-word-document-insert-rectangle-shape-shadow-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word दस्तावेज़ बनाएं – C# में आयताकार आकार & छाया डालें

क्या आपने कभी सोचा है कि **create Word document** को प्रोग्रामेटिकली बिना Microsoft Word खोले कैसे बनाया जाए? आप अकेले नहीं हैं। कई ऑटोमेशन परिदृश्यों में—जैसे इनवॉइस, कॉन्ट्रैक्ट, या बड़े पैमाने पर रिपोर्ट जनरेशन—आपको एक भरोसेमंद तरीका चाहिए जिससे .docx फ़ाइल बनाई जा सके, उसमें एक आकार डाला जा सके, उसे रंग दिया जा सके, और शायद एक छाया भी जोड़े जाए ताकि वह प्रोफ़ेशनल दिखे।

इस ट्यूटोरियल में हम ठीक वही करेंगे: Aspose.Words for .NET का उपयोग करके **create Word document**, **insert rectangle shape**, फ़िल लागू करना, और **add shadow**। अंत तक आपके पास एक तैयार‑से‑सेव फ़ाइल होगी जिसे आप किसी भी डाउनस्ट्रीम वर्कफ़्लो में पाइप कर सकते हैं।  

हम **how to insert shape** को लचीले तरीके से करने और **how to set fill** के महत्व को भी छूएँगे ताकि विज़ुअल कंसिस्टेंसी बनी रहे। कोई फालतू बात नहीं, सिर्फ वह कोड जो आप कॉपी‑पेस्ट करके चला सकते हैं।

## आवश्यकताएँ

- .NET 6+ (या .NET Framework 4.7+) स्थापित हो।
- एक वैध Aspose.Words for .NET लाइसेंस (या अस्थायी इवैल्यूएशन की)।
- Visual Studio, Rider, या कोई भी C# IDE जो आपको पसंद हो।
- C# सिंटैक्स की बुनियादी समझ—कोई विशेष ज्ञान आवश्यक नहीं।

ये सब हैं? बढ़िया, चलिए शुरू करते हैं।

## चरण 1 – Word दस्तावेज़ बनाएं

पहली चीज़ जो आपको चाहिए वह एक खाली दस्तावेज़ ऑब्जेक्ट है। यह वह कैनवास है जहाँ बाकी सब कुछ रखा जाता है।

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Step 1: Create a new blank document and a DocumentBuilder.
Document doc = new Document();                 // The document itself.
DocumentBuilder builder = new DocumentBuilder(doc); // Helper to add content.
```

`Document` मेमोरी में .docx फ़ाइल का प्रतिनिधित्व करता है, जबकि `DocumentBuilder` हमें टेक्स्ट, टेबल और आकार डालने के लिए एक सुविधाजनक API देता है। इस तरह **Creating the Word document** तुरंत होता है—कोई UI नहीं, कोई COM इंटरऑप नहीं, सिर्फ शुद्ध .NET।

## चरण 2 – आयताकार आकार डालें

अब जब हमारे पास दस्तावेज़ है, चलिए **insert rectangle shape** करते हैं। `InsertShape` मेथड एक `ShapeType` एन्नुम, चौड़ाई और ऊँचाई (पॉइंट्स में) लेता है। हम 150 × 80 पॉइंट्स आकार का आयताकार उपयोग करेंगे, जो लगभग 2 × 1 इंच के बराबर है।

```csharp
// Step 2: Insert a rectangle shape of the desired size.
Shape shape = builder.InsertShape(ShapeType.Rectangle, 150, 80);
```

पर्दे के पीछे, Aspose एक `Shape` ऑब्जेक्ट बनाता है, उसे वर्तमान पैराग्राफ में जोड़ता है, और एक रेफ़रेंस लौटाता है जिसे आप स्टाइल कर सकते हैं। यह **how to insert shape** का मूल है—सिर्फ एक लाइन का कोड, फिर भी अत्यंत शक्तिशाली।

## चरण 3 – Fill कैसे सेट करें

बिना फ़िल वाले आकार सफ़ेद पेज पर अदृश्य होते हैं। चलिए इसे एक सुखद हल्के‑नीले बैकग्राउंड देते हैं।

```csharp
// Step 3: Apply a fill color to make the shape visible.
shape.FillColor = System.Drawing.Color.LightBlue; // Any System.Drawing.Color works.
```

आप ग्रेडिएंट, टेक्सचर, या यहाँ तक कि पिक्चर फ़िल भी उपयोग कर सकते हैं, लेकिन एक सॉलिड रंग उदाहरण को सरल रखता है। यह **how to set fill** को किसी भी आकार पर दिखाता है जो आप बनाते हैं, जिससे आपके पाठकों को अपेक्षित विज़ुअल संकेत मिलता है।

## चरण 4 – Shadow कैसे जोड़ें

छायाएँ गहराई जोड़ती हैं और आकार को उभारा बनाती हैं। Aspose.Words एक `ShadowFormat` ऑब्जेक्ट प्रदान करता है जहाँ आप दृश्यता टॉगल कर सकते हैं, रंग चुन सकते हैं, और ब्लर, दूरी, तथा कोण को सूक्ष्म‑समायोजित कर सकते हैं।

```csharp
// Step 4: Configure the shadow effect – enable it, set color, blur, distance and angle.
shape.ShadowFormat.Visible = true;                     // Turn the shadow on.
shape.ShadowFormat.Color = System.Drawing.Color.Gray; // Shadow color.
shape.ShadowFormat.BlurRadius = 4.0;                  // Softness in pixels.
shape.ShadowFormat.Distance = 3.0;                    // How far the shadow is offset.
shape.ShadowFormat.Angle = 45;                        // Direction of the offset (degrees).
```

इन विशेष मानों का चयन क्यों? 45° का कोण एक प्राकृतिक टॉप‑राइट लाइट सोर्स देता है, हल्का ब्लर छाया को सूक्ष्म रखता है, और छोटी दूरी आकार को अलग‑थलग दिखने से रोकती है। आप प्रयोग करने के लिए स्वतंत्र हैं—कोण को 135° करने से छाया नीचे‑बाएँ गिरेगी, उदाहरण के तौर पर।

## चरण 5 – दस्तावेज़ सहेजें

सारा काम हो गया; अब हम फ़ाइल को डिस्क पर लिखते हैं। कोई भी पाथ चुनें जो आपको पसंद हो; बस यह सुनिश्चित करें कि फ़ोल्डर मौजूद हो।

```csharp
// Step 5: Save the document with the shaped shadow.
doc.Save("YOUR_DIRECTORY/ShadowShape.docx");
```

जब आप Microsoft Word में `ShadowShape.docx` खोलेंगे, तो आपको एक हल्के‑नीले आयताकार के साथ एक नरम ग्रे छाया दिखेगी—बिल्कुल वही जो हमने स्क्रिप्ट किया था।

## पूर्ण कार्यशील उदाहरण

सब कुछ एक साथ मिलाकर, यहाँ पूरा, कॉपी‑पेस्ट‑तैयार प्रोग्राम है:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a new blank document.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Insert a rectangle shape (150 × 80 points).
        Shape shape = builder.InsertShape(ShapeType.Rectangle, 150, 80);

        // 3️⃣ Set a solid fill color so the shape is visible.
        shape.FillColor = System.Drawing.Color.LightBlue;

        // 4️⃣ Add a subtle shadow for depth.
        shape.ShadowFormat.Visible = true;
        shape.ShadowFormat.Color = System.Drawing.Color.Gray;
        shape.ShadowFormat.BlurRadius = 4.0;   // pixels
        shape.ShadowFormat.Distance = 3.0;     // pixels
        shape.ShadowFormat.Angle = 45;        // degrees

        // 5️⃣ Persist the document.
        doc.Save("ShadowShape.docx");
    }
}
```

### अपेक्षित परिणाम

- लक्ष्य फ़ोल्डर में **ShadowShape.docx** नाम की फ़ाइल दिखाई देती है।
- इसे Word में खोलने पर पहले पृष्ठ के केंद्र में हल्का‑नीला आयताकार दिखता है।
- आयताकार 45° कोण पर ग्रे छाया डालता है, जिससे एक सूक्ष्म 3‑D प्रभाव मिलता है।

## सामान्य प्रश्न और किनारे के मामलों

**अगर मुझे कोई अलग आकार चाहिए?**  
`ShapeType.Rectangle` को किसी भी अन्य एन्नुम वैल्यू (`Ellipse`, `Star`, `Arrow`, आदि) से बदलें। बाकी कोड वही रहता है।

**क्या मैं आकार के अंदर टेक्स्ट जोड़ सकता हूँ?**  
हाँ—आकार बनाने के बाद, `shape.AppendChild(new Paragraph(doc))` कॉल करें और फिर अपने टेक्स्ट के साथ एक `Run` डालें। यदि आप रैपिंग चाहते हैं तो `shape.TextBox` प्रॉपर्टीज़ सेट करना याद रखें।

**DPI या माप इकाइयों के बारे में क्या?**  
Aspose पॉइंट्स में काम करता है (1 pt = 1/72 इंच)। यदि आप सेंटीमीटर पसंद करते हैं, तो 28.35 से गुणा करें (क्योंकि 1 cm ≈ 28.35 pt)।

**क्या इसे काम करने के लिए लाइसेंस चाहिए?**  
इवैल्यूएशन संस्करण पहली पेज पर वॉटरमार्क जोड़ता है। एक उचित लाइसेंस इसे हटाता है और पूरी API अनलॉक करता है।

## टिप्स और सावधानियाँ

- **Pro tip:** यदि आप आकार को दस्तावेज़ के अंत में चाहते हैं तो उसे डालने से पहले `builder.MoveToDocumentEnd()` कॉल करें।
- **ध्यान रखें:** रीड‑ओनली फ़ोल्डर में सहेजने से `UnauthorizedAccessException` फेंका जाएगा। सुनिश्चित करें कि आपके एप्लिकेशन के पास लिखने की अनुमति है।
- **Performance note:** बड़े पैमाने पर जनरेशन (सैकड़ों दस्तावेज़) के लिए, एक ही `Document` इंस्टेंस को टेम्पलेट के रूप में पुन: उपयोग करें और `doc.Clone(true)` से क्लोन करें ताकि बार‑बार इनिशियलाइज़ेशन ओवरहेड से बचा जा सके।

## निष्कर्ष

अब आप जानते हैं कि Aspose.Words for .NET का उपयोग करके **create Word document**, **insert rectangle shape**, **set fill**, और **add shadow** कैसे किया जाता है। ऊपर दिया गया स्निपेट एक स्व-निहित समाधान है जिसे आप किसी भी C# प्रोजेक्ट में डाल सकते हैं, चाहे वह कंसोल ऐप, वेब API, या बैकग्राउंड सर्विस हो।

अब आप आगे खोज सकते हैं:

- विभिन्न रंगों के साथ कई आकार जोड़ना।
- ग्रेडिएंट या पिक्चर फ़िल्स का उपयोग (`shape.FillColor = ...` → `shape.FillPattern`)।
- जटिल रिपोर्ट लेआउट के लिए आकारों को टेबल्स के साथ मिलाना।

इसे आज़माएँ, पैरामीटर बदलें, और देखें कि आपका ऑटोमेटेड Word फ़ाइल कुछ ही लाइनों के कोड से अधिक प्रोफ़ेशनल दिखे। कोडिंग का आनंद लें!

## संबंधित ट्यूटोरियल

- [C# में Word में आयताकार आकार बनाएं – चरण‑दर‑चरण गाइड](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Aspose.Words Shape Shadow Tutorial – C# में Word Shape में छाया जोड़ें](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)
- [Aspose.Words for .NET का उपयोग करके Word दस्तावेज़ में समूह आकार बनाएं](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}