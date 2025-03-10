---
title: जावा के लिए Aspose.Words में टेक्स्ट ढूँढना और बदलना
linktitle: पाठ ढूँढना और बदलना
second_title: Aspose.Words जावा दस्तावेज़ प्रसंस्करण एपीआई
description: Aspose.Words for Java के साथ Word दस्तावेज़ों में टेक्स्ट ढूँढ़ना और बदलना सीखें। कोड उदाहरणों के साथ चरण-दर-चरण मार्गदर्शिका। अपने Java दस्तावेज़ हेरफेर कौशल को बढ़ाएँ।
weight: 15
url: /hi/java/document-manipulation/finding-and-replacing-text/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# जावा के लिए Aspose.Words में टेक्स्ट ढूँढना और बदलना


## जावा के लिए Aspose.Words में टेक्स्ट ढूँढने और बदलने का परिचय

Aspose.Words for Java एक शक्तिशाली Java API है जो आपको Word दस्तावेज़ों के साथ प्रोग्रामेटिक रूप से काम करने की अनुमति देता है। Word दस्तावेज़ों से निपटने के दौरान सबसे आम काम टेक्स्ट को ढूँढना और बदलना है। चाहे आपको टेम्प्लेट में प्लेसहोल्डर अपडेट करने की ज़रूरत हो या ज़्यादा जटिल टेक्स्ट मैनिपुलेशन करने की, Aspose.Words for Java आपके लक्ष्यों को कुशलतापूर्वक हासिल करने में आपकी मदद कर सकता है।

## आवश्यक शर्तें

इससे पहले कि हम टेक्स्ट ढूंढने और बदलने के विवरण में उतरें, सुनिश्चित करें कि आपके पास निम्नलिखित पूर्वापेक्षाएँ मौजूद हैं:

- जावा विकास पर्यावरण
- Aspose.Words जावा लाइब्रेरी के लिए
- काम करने के लिए एक नमूना Word दस्तावेज़

 आप Aspose.Words for Java लाइब्रेरी को यहां से डाउनलोड कर सकते हैं[यहाँ](https://releases.aspose.com/words/java/).

## सरल पाठ ढूँढना और प्रतिस्थापित करना

```java
// दस्तावेज़ लोड करें
Document doc = new Document("your-document.docx");

// एक दस्तावेज़ बिल्डर बनाएँ
DocumentBuilder builder = new DocumentBuilder(doc);

// पाठ ढूंढें और बदलें
builder.getRange().replace("old-text", "new-text", new FindReplaceOptions());

// संशोधित दस्तावेज़ सहेजें
doc.save("modified-document.docx");
```

 इस उदाहरण में, हम एक वर्ड दस्तावेज़ लोड करते हैं, एक बनाते हैं`DocumentBuilder` , और का उपयोग करें`replace` दस्तावेज़ के भीतर "पुराने-पाठ" को "नए-पाठ" के साथ खोजने और बदलने की विधि।

## नियमित अभिव्यक्तियों का उपयोग करना

नियमित अभिव्यक्तियाँ पाठ खोज और प्रतिस्थापन के लिए शक्तिशाली पैटर्न मिलान क्षमताएँ प्रदान करती हैं। Aspose.Words for Java अधिक उन्नत खोज और प्रतिस्थापन संचालन के लिए नियमित अभिव्यक्तियों का समर्थन करता है।

```java
// दस्तावेज़ लोड करें
Document doc = new Document("your-document.docx");

// एक दस्तावेज़ बिल्डर बनाएँ
DocumentBuilder builder = new DocumentBuilder(doc);

// टेक्स्ट ढूंढने और बदलने के लिए नियमित अभिव्यक्तियों का उपयोग करें
Pattern regex = Pattern.compile("your-pattern");
builder.getRange().replace(regex, "replacement-text", new FindReplaceOptions());

// संशोधित दस्तावेज़ सहेजें
doc.save("modified-document.docx");
```

इस उदाहरण में, हम दस्तावेज़ के भीतर पाठ खोजने और बदलने के लिए नियमित अभिव्यक्ति पैटर्न का उपयोग करते हैं।

## फ़ील्ड के अंदर पाठ को अनदेखा करना

आप खोज और प्रतिस्थापन संचालन करते समय फ़ील्ड के अंदर के पाठ को अनदेखा करने के लिए Aspose.Words को कॉन्फ़िगर कर सकते हैं।

```java
// दस्तावेज़ लोड करें
Document doc = new Document("your-document.docx");

// FindReplaceOptions इंस्टेंस बनाएं और IgnoreFields को true पर सेट करें
FindReplaceOptions options = new FindReplaceOptions();
options.setIgnoreFields(true);

// टेक्स्ट बदलते समय विकल्पों का उपयोग करें
doc.getRange().replace("text-to-replace", "new-text", options);

// संशोधित दस्तावेज़ सहेजें
doc.save("modified-document.docx");
```

यह तब उपयोगी होता है जब आप फ़ील्ड के अंदर के टेक्स्ट को, जैसे मर्ज फ़ील्ड, प्रतिस्थापित होने से बचाना चाहते हैं।

## संशोधन हटाएँ के अंदर पाठ को अनदेखा करना

आप खोज और प्रतिस्थापन कार्यों के दौरान हटाए गए संशोधनों के अंदर पाठ को अनदेखा करने के लिए Aspose.Words को कॉन्फ़िगर कर सकते हैं।

```java
// दस्तावेज़ लोड करें
Document doc = new Document("your-document.docx");

// FindReplaceOptions इंस्टेंस बनाएं और IgnoreDeleted को true पर सेट करें
FindReplaceOptions options = new FindReplaceOptions();
options.setIgnoreDeleted(true);

// टेक्स्ट बदलते समय विकल्पों का उपयोग करें
doc.getRange().replace("text-to-replace", "new-text", options);

// संशोधित दस्तावेज़ सहेजें
doc.save("modified-document.docx");
```

यह आपको ट्रैक किए गए परिवर्तनों में हटाए जाने के लिए चिह्नित पाठ को प्रतिस्थापित किए जाने से बाहर रखने की अनुमति देता है।

## सम्मिलित संशोधनों के अंदर पाठ को अनदेखा करना

आप खोज और प्रतिस्थापन कार्यों के दौरान सम्मिलित संशोधनों के अंदर पाठ को अनदेखा करने के लिए Aspose.Words को कॉन्फ़िगर कर सकते हैं।

```java
// दस्तावेज़ लोड करें
Document doc = new Document("your-document.docx");

// FindReplaceOptions इंस्टेंस बनाएं और IgnoreInserted को true पर सेट करें
FindReplaceOptions options = new FindReplaceOptions();
options.setIgnoreInserted(true);

// टेक्स्ट बदलते समय विकल्पों का उपयोग करें
doc.getRange().replace("text-to-replace", "new-text", options);

// संशोधित दस्तावेज़ सहेजें
doc.save("modified-document.docx");
```

यह आपको ट्रैक किए गए परिवर्तनों में सम्मिलित के रूप में चिह्नित पाठ को प्रतिस्थापित होने से बाहर करने की अनुमति देता है।

## टेक्स्ट को HTML से बदलना

आप टेक्स्ट को HTML सामग्री से बदलने के लिए Java के लिए Aspose.Words का उपयोग कर सकते हैं।

```java
// दस्तावेज़ लोड करें
Document doc = new Document("your-document.docx");

// कस्टम रिप्लेसिंग कॉलबैक के साथ FindReplaceOptions इंस्टेंस बनाएं
FindReplaceOptions options = new FindReplaceOptions();
options.setReplacingCallback(new ReplaceWithHtmlEvaluator(options));

// टेक्स्ट बदलते समय विकल्पों का उपयोग करें
doc.getRange().replace("text-to-replace", "new-html-content", options);

// संशोधित दस्तावेज़ सहेजें
doc.save("modified-document.docx");
```

 इस उदाहरण में, हम एक कस्टम का उपयोग करते हैं`ReplaceWithHtmlEvaluator` पाठ को HTML सामग्री से बदलने के लिए.

## हेडर और फूटर में टेक्स्ट बदलना

आप अपने वर्ड दस्तावेज़ के शीर्षलेखों और पादलेखों में पाठ ढूंढ और बदल सकते हैं।

```java
// दस्तावेज़ लोड करें
Document doc = new Document("your-document.docx");

// शीर्षलेखों और पादलेखों का संग्रह प्राप्त करें
HeaderFooterCollection headersFooters = doc.getFirstSection().getHeadersFooters();

// वह शीर्षलेख या पादलेख प्रकार चुनें जिसमें आप पाठ बदलना चाहते हैं (उदाहरण के लिए, HeaderFooterType.FOOTER_PRIMARY)
HeaderFooter footer = headersFooters.getByHeaderFooterType(HeaderFooterType.FOOTER_PRIMARY);

// FindReplaceOptions इंस्टैंस बनाएं और उसे फ़ुटर की रेंज पर लागू करें
FindReplaceOptions options = new FindReplaceOptions();
footer.getRange().replace("text-to-replace", "new-text", options);

// संशोधित दस्तावेज़ सहेजें
doc.save("modified-document.docx");
```

यह आपको विशेष रूप से शीर्षलेखों और पादलेखों में पाठ प्रतिस्थापन करने की अनुमति देता है।

## हेडर और फ़ुटर ऑर्डर के लिए परिवर्तन दिखाना

आप अपने दस्तावेज़ में शीर्षलेख और पादलेख क्रम में परिवर्तन दिखाने के लिए Aspose.Words का उपयोग कर सकते हैं।

```java
// दस्तावेज़ लोड करें
Document doc = new Document("your-document.docx");

// पहला भाग प्राप्त करें
Section firstPageSection = doc.getFirstSection();

//FindReplaceOptions इंस्टैंस बनाएं और उसे दस्तावेज़ की श्रेणी पर लागू करें
FindReplaceOptions options = new FindReplaceOptions();
options.setReplacingCallback(new ReplaceLog());

// शीर्षलेख और पादलेख क्रम को प्रभावित करने वाले पाठ को बदलें
doc.getRange().replace(Pattern.compile("(header|footer)"), "", options);

// संशोधित दस्तावेज़ सहेजें
doc.save("modified-document.docx");
```

यह आपको अपने दस्तावेज़ में शीर्षलेख और पादलेख क्रम से संबंधित परिवर्तनों को देखने की अनुमति देता है।

## टेक्स्ट को फ़ील्ड से बदलना

आप Java के लिए Aspose.Words का उपयोग करके टेक्स्ट को फ़ील्ड से बदल सकते हैं।

```java
// दस्तावेज़ लोड करें
Document doc = new Document("your-document.docx");

// FindReplaceOptions इंस्टेंस बनाएं और फ़ील्ड के लिए कस्टम रिप्लेसिंग कॉलबैक सेट करें
FindReplaceOptions options = new FindReplaceOptions();
options.setReplacingCallback(new ReplaceTextWithFieldHandler(FieldType.FIELD_MERGE_FIELD));

// टेक्स्ट बदलते समय विकल्पों का उपयोग करें
doc.getRange().replace(Pattern.compile("PlaceHolder(\\d+)"), "", options);

// संशोधित दस्तावेज़ सहेजें
doc.save("modified-document.docx");
```

 इस उदाहरण में, हम टेक्स्ट को फ़ील्ड से बदलते हैं और फ़ील्ड प्रकार निर्दिष्ट करते हैं (उदाहरण के लिए,`FieldType.FIELD_MERGE_FIELD`).

## मूल्यांकनकर्ता के साथ प्रतिस्थापित करना

आप प्रतिस्थापन पाठ को गतिशील रूप से निर्धारित करने के लिए कस्टम मूल्यांकनकर्ता का उपयोग कर सकते हैं।

```java
// दस्तावेज़ लोड करें
Document doc = new Document("your-document.docx");

// FindReplaceOptions इंस्टेंस बनाएं और कस्टम रिप्लेसिंग कॉलबैक सेट करें
FindReplaceOptions options = new FindReplaceOptions();
options.setReplacingCallback(new MyReplaceEvaluator());

// टेक्स्ट बदलते समय विकल्पों का उपयोग करें
doc.getRange().replace(Pattern.compile("[s|m]ad"), "", options);

// संशोधित दस्तावेज़ सहेजें
doc.save("modified-document.docx");
```

इस उदाहरण में, हम एक कस्टम मूल्यांकनकर्ता (`MyReplaceEvaluator`) का प्रयोग करें.

## रेगेक्स से प्रतिस्थापित करना

Java के लिए Aspose.Words आपको नियमित अभिव्यक्तियों का उपयोग करके पाठ को प्रतिस्थापित करने की अनुमति देता है।

```java
// दस्तावेज़ लोड करें
Document doc = new Document("your-document.docx");

// टेक्स्ट ढूंढने और बदलने के लिए नियमित अभिव्यक्तियों का उपयोग करें
doc.getRange().replace(Pattern.compile("[s|m]ad"), "bad", new FindReplaceOptions());

// संशोधित दस्तावेज़ सहेजें
doc.save("modified-document.docx");
```

इस उदाहरण में, हम दस्तावेज़ के भीतर पाठ खोजने और बदलने के लिए नियमित अभिव्यक्ति पैटर्न का उपयोग करते हैं।

## प्रतिस्थापन पैटर्न के भीतर प्रतिस्थापन को पहचानना

आप Java के लिए Aspose.Words का उपयोग करके प्रतिस्थापन पैटर्न को पहचान सकते हैं और उनमें प्रतिस्थापन कर सकते हैं।

```java
// दस्तावेज़ लोड करें
Document doc = new Document("your-document.docx");

// UseSubstitutions को true पर सेट करके FindReplaceOptions इंस्टेंस बनाएं
FindReplaceOptions options = new FindReplaceOptions();
options.setUseSubstitutions(true);

// टेक्स्ट को पैटर्न से बदलते समय विकल्पों का उपयोग करें
doc.getRange().replace(Pattern.compile("([A-z]+) give money to ([A-z]+)"), "$2 take money from $1", options);

// संशोधित दस्तावेज़ सहेजें
doc.save("modified-document.docx");
```

यह आपको अधिक उन्नत प्रतिस्थापन के लिए प्रतिस्थापन पैटर्न के भीतर प्रतिस्थापन करने की अनुमति देता है।

## स्ट्रिंग से प्रतिस्थापित करना

आप Java के लिए Aspose.Words का उपयोग करके टेक्स्ट को सरल स्ट्रिंग से बदल सकते हैं।

```java
// दस्तावेज़ लोड करें
Document doc = new Document("your-document.docx");

// टेक्स्ट को स्ट्रिंग से बदलें
doc.getRange().replace("text-to-replace", "new-string", new FindReplaceOptions());

// संशोधित दस्तावेज़ सहेजें
doc.save("modified-document.docx");
```

इस उदाहरण में, हम दस्तावेज़ के भीतर "text-to-replace" को "new-string" से प्रतिस्थापित करते हैं।

## लीगेसी ऑर्डर का उपयोग करना

आप खोज और प्रतिस्थापन संक्रियाएँ करते समय विरासत क्रम का उपयोग कर सकते हैं।

```java
// दस्तावेज़ लोड करें
Document doc = new Document("your-document.docx");

// FindReplaceOptions इंस्टेंस बनाएं और UseLegacyOrder को true पर सेट करें
FindReplaceOptions options = new FindReplaceOptions();
options.setUseLegacyOrder(true);

// टेक्स्ट बदलते समय विकल्पों का उपयोग करें
doc.getRange().replace(Pattern.compile("\\[(.*?)\\]"), "", options);

// संशोधित दस्तावेज़ सहेजें
doc.save("modified-document.docx");
```

यह आपको खोजने और बदलने के कार्यों के लिए विरासत क्रम का उपयोग करने की अनुमति देता है।

## तालिका में पाठ बदलना

आप अपने वर्ड दस्तावेज़ में तालिकाओं के भीतर पाठ ढूंढ और प्रतिस्थापित कर सकते हैं।

```java
// दस्तावेज़ लोड करें
Document doc = new Document("your-document.docx");

// एक विशिष्ट तालिका प्राप्त करें (उदाहरणार्थ, पहली तालिका)
Table table = (Table) doc.getChild(NodeType.TABLE, 0, true);

//तालिका में पाठ बदलने के लिए FindReplaceOptions का उपयोग करें
table.getRange().replace("old-text", "new-text", new FindReplaceOptions());

// संशोधित दस्तावेज़ सहेजें
doc.save("modified-document.docx");
```

यह आपको विशेष रूप से तालिकाओं के भीतर पाठ प्रतिस्थापन करने की अनुमति देता है।

## निष्कर्ष

Aspose.Words for Java, Word दस्तावेज़ों में टेक्स्ट ढूँढ़ने और बदलने के लिए व्यापक क्षमताएँ प्रदान करता है। चाहे आपको साधारण टेक्स्ट प्रतिस्थापन करने की आवश्यकता हो या नियमित अभिव्यक्तियों, फ़ील्ड मैनिपुलेशन या कस्टम मूल्यांकनकर्ताओं का उपयोग करके अधिक उन्नत संचालन करने की आवश्यकता हो, Aspose.Words for Java आपके लिए है। इस शक्तिशाली Java लाइब्रेरी की पूरी क्षमता का दोहन करने के लिए Aspose द्वारा प्रदान किए गए व्यापक दस्तावेज़ों और उदाहरणों का पता लगाना सुनिश्चित करें।

## अक्सर पूछे जाने वाले प्रश्न

### मैं Java के लिए Aspose.Words कैसे डाउनलोड करूं?

 आप वेबसाइट पर जाकर Java के लिए Aspose.Words डाउनलोड कर सकते हैं[इस लिंक](https://releases.aspose.com/words/java/).

### क्या मैं पाठ प्रतिस्थापन के लिए नियमित अभिव्यक्ति का उपयोग कर सकता हूँ?

हां, आप Aspose.Words for Java में टेक्स्ट प्रतिस्थापन के लिए नियमित अभिव्यक्तियों का उपयोग कर सकते हैं। यह आपको अधिक उन्नत और लचीले खोज और प्रतिस्थापन संचालन करने की अनुमति देता है।

### प्रतिस्थापन के दौरान मैं फ़ील्ड के अंदर पाठ को कैसे अनदेखा कर सकता हूं?

प्रतिस्थापन के दौरान फ़ील्ड के अंदर पाठ को अनदेखा करने के लिए, आप सेट कर सकते हैं`IgnoreFields` की संपत्ति`FindReplaceOptions` को`true`यह सुनिश्चित करता है कि फ़ील्ड के भीतर का पाठ, जैसे मर्ज फ़ील्ड, प्रतिस्थापन से बाहर रखा गया है।

### क्या मैं हेडर और फ़ुटर के अंदर पाठ बदल सकता हूँ?

 हां, आप अपने वर्ड डॉक्यूमेंट के हेडर और फूटर के अंदर टेक्स्ट को बदल सकते हैं। बस उचित हेडर या फूटर तक पहुंचें और इसका उपयोग करें`replace` वांछित विधि के साथ`FindReplaceOptions`.

### UseLegacyOrder विकल्प किसके लिए है?

`UseLegacyOrder` विकल्प में`FindReplaceOptions` आपको खोज और प्रतिस्थापन संचालन करते समय विरासत क्रम का उपयोग करने की अनुमति देता है। यह कुछ परिदृश्यों में उपयोगी हो सकता है जहां विरासत क्रम व्यवहार वांछित है।
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
