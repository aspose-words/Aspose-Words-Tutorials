---
title: वर्ड दस्तावेज़ में बुकमार्क बनाएँ
linktitle: वर्ड दस्तावेज़ में बुकमार्क बनाएँ
second_title: Aspose.Words दस्तावेज़ प्रसंस्करण API
description: इस विस्तृत, चरण-दर-चरण मार्गदर्शिका के साथ .NET के लिए Aspose.Words का उपयोग करके Word दस्तावेज़ों में बुकमार्क बनाना सीखें। दस्तावेज़ नेविगेशन और संगठन के लिए बिल्कुल सही।
weight: 10
url: /hi/net/programming-with-bookmarks/create-bookmark/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# वर्ड दस्तावेज़ में बुकमार्क बनाएँ

## परिचय

वर्ड डॉक्यूमेंट में बुकमार्क बनाना एक गेम-चेंजर हो सकता है, खासकर जब आप बड़े दस्तावेज़ों में आसानी से नेविगेट करना चाहते हैं। आज, हम .NET के लिए Aspose.Words का उपयोग करके बुकमार्क बनाने की प्रक्रिया से गुजरेंगे। यह ट्यूटोरियल आपको चरण दर चरण ले जाएगा, यह सुनिश्चित करते हुए कि आप प्रक्रिया के प्रत्येक भाग को समझते हैं। तो, चलिए सीधे शुरू करते हैं!

## आवश्यक शर्तें

शुरू करने से पहले, आपके पास निम्नलिखित चीजें होनी चाहिए:

1.  Aspose.Words for .NET लाइब्रेरी: डाउनलोड करें और इंस्टॉल करें[यहाँ](https://releases.aspose.com/words/net/).
2. विकास वातावरण: विजुअल स्टूडियो या कोई अन्य .NET विकास वातावरण।
3. C# का बुनियादी ज्ञान: बुनियादी C# प्रोग्रामिंग अवधारणाओं की समझ।

## नामस्थान आयात करें

.NET के लिए Aspose.Words के साथ काम करने के लिए, आपको आवश्यक नामस्थान आयात करने होंगे:

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

## चरण 1: दस्तावेज़ और दस्तावेज़बिल्डर सेटअप करें

दस्तावेज़ आरंभ करें

सबसे पहले, हमें एक नया दस्तावेज़ बनाना होगा और उसे आरंभ करना होगा`DocumentBuilder`यह आपके दस्तावेज़ में सामग्री और बुकमार्क जोड़ने का प्रारंभिक बिंदु है।

```csharp
// दस्तावेज़ निर्देशिका का पथ.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

 स्पष्टीकरण:`Document` वस्तु आपका कैनवास है।`DocumentBuilder` यह आपके पेन की तरह है, जो आपको दस्तावेज़ में सामग्री लिखने और बुकमार्क बनाने की अनुमति देता है।

## चरण 2: मुख्य बुकमार्क बनाएं

मुख्य बुकमार्क आरंभ और समाप्त करें

बुकमार्क बनाने के लिए, आपको आरंभ और समाप्ति बिंदु निर्दिष्ट करने होंगे। यहाँ, हम "मेरा बुकमार्क" नाम से एक बुकमार्क बनाएंगे।

```csharp
builder.StartBookmark("My Bookmark");
builder.Writeln("Text inside a bookmark.");
```

 स्पष्टीकरण:`StartBookmark` विधि बुकमार्क की शुरुआत को चिह्नित करती है, और`Writeln` बुकमार्क के भीतर पाठ जोड़ता है.

## चरण 3: नेस्टेड बुकमार्क बनाएं

मुख्य बुकमार्क के अंदर नेस्टेड बुकमार्क जोड़ें

आप बुकमार्क को अन्य बुकमार्क के अंदर नेस्ट कर सकते हैं। यहाँ, हम "मेरे बुकमार्क" के अंदर "नेस्टेड बुकमार्क" जोड़ते हैं।

```csharp
builder.StartBookmark("Nested Bookmark");
builder.Writeln("Text inside a NestedBookmark.");
builder.EndBookmark("Nested Bookmark");
```

 स्पष्टीकरण: बुकमार्क को नेस्ट करने से अधिक संरचित और पदानुक्रमित सामग्री संगठन की अनुमति मिलती है।`EndBookmark` विधि वर्तमान बुकमार्क को बंद कर देती है.

## चरण 4: नेस्टेड बुकमार्क के बाहर टेक्स्ट जोड़ें

सामग्री जोड़ना जारी रखें

नेस्टेड बुकमार्क के बाद, हम मुख्य बुकमार्क में और अधिक सामग्री जोड़ना जारी रख सकते हैं।

```csharp
builder.Writeln("Text after Nested Bookmark.");
builder.EndBookmark("My Bookmark");
```

स्पष्टीकरण: यह सुनिश्चित करता है कि मुख्य बुकमार्क में नेस्टेड बुकमार्क और अतिरिक्त पाठ दोनों शामिल हों।

## चरण 5: पीडीएफ सेव विकल्प कॉन्फ़िगर करें

बुकमार्क के लिए PDF सेव विकल्प सेट करें

दस्तावेज़ को पीडीएफ के रूप में सहेजते समय, हम बुकमार्क शामिल करने के लिए विकल्प कॉन्फ़िगर कर सकते हैं।

```csharp
PdfSaveOptions options = new PdfSaveOptions();
options.OutlineOptions.BookmarksOutlineLevels.Add("My Bookmark", 1);
options.OutlineOptions.BookmarksOutlineLevels.Add("Nested Bookmark", 2);
```

 स्पष्टीकरण:`PdfSaveOptions` क्लास आपको यह निर्दिष्ट करने की अनुमति देता है कि दस्तावेज़ को पीडीएफ के रूप में कैसे सहेजा जाना चाहिए।`BookmarksOutlineLevels` संपत्ति पीडीएफ में बुकमार्क्स के पदानुक्रम को परिभाषित करती है।

## चरण 6: दस्तावेज़ सहेजें

दस्तावेज़ को PDF के रूप में सहेजें

अंत में, निर्दिष्ट विकल्पों के साथ दस्तावेज़ को सहेजें।

```csharp
doc.Save(dataDir + "WorkingWithBookmarks.CreateBookmark.pdf", options);
```

 स्पष्टीकरण:`Save` विधि दस्तावेज़ को निर्दिष्ट प्रारूप और स्थान में सहेजती है। पीडीएफ में अब हमारे द्वारा बनाए गए बुकमार्क शामिल होंगे।

## निष्कर्ष

Aspose.Words for .NET का उपयोग करके Word दस्तावेज़ में बुकमार्क बनाना सरल है और दस्तावेज़ नेविगेशन और संगठन के लिए बेहद उपयोगी है। चाहे आप रिपोर्ट बना रहे हों, ईबुक बना रहे हों या बड़े दस्तावेज़ों का प्रबंधन कर रहे हों, बुकमार्क जीवन को आसान बनाते हैं। इस ट्यूटोरियल में बताए गए चरणों का पालन करें, और आपके पास कुछ ही समय में एक बुकमार्क किया हुआ PDF तैयार हो जाएगा।

## अक्सर पूछे जाने वाले प्रश्न

### क्या मैं विभिन्न स्तरों पर एकाधिक बुकमार्क बना सकता हूँ?

बिल्कुल! आप आवश्यकतानुसार जितने चाहें उतने बुकमार्क बना सकते हैं और दस्तावेज़ को PDF के रूप में सहेजते समय उनके पदानुक्रमिक स्तर को परिभाषित कर सकते हैं।

### मैं बुकमार्क का टेक्स्ट कैसे अपडेट करूं?

 आप बुकमार्क तक नेविगेट करने के लिए निम्न का उपयोग कर सकते हैं:`DocumentBuilder.MoveToBookmark` और फिर पाठ को अद्यतन करें.

### क्या बुकमार्क को हटाना संभव है?

 हां, आप इसका उपयोग करके बुकमार्क हटा सकते हैं`Bookmarks.Remove` बुकमार्क का नाम निर्दिष्ट करके विधि।

### क्या मैं पीडीएफ के अलावा अन्य प्रारूपों में बुकमार्क बना सकता हूं?

हां, Aspose.Words DOCX, HTML और EPUB सहित विभिन्न प्रारूपों में बुकमार्क का समर्थन करता है।

### मैं यह कैसे सुनिश्चित कर सकता हूं कि बुकमार्क पीडीएफ में सही ढंग से दिखाई दें?

 यह सुनिश्चित करें कि आप परिभाषित करें`BookmarksOutlineLevels` ठीक से`PdfSaveOptions`यह सुनिश्चित करता है कि बुकमार्क पीडीएफ की रूपरेखा में शामिल हैं।
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
