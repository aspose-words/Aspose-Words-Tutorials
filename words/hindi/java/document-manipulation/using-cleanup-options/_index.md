---
"description": "Aspose.Words for Java क्लीनअप विकल्पों के साथ दस्तावेज़ स्पष्टता बढ़ाएँ। खाली पैराग्राफ़, अप्रयुक्त क्षेत्र और बहुत कुछ हटाने का तरीका जानें।"
"linktitle": "क्लीनअप विकल्पों का उपयोग करना"
"second_title": "Aspose.Words जावा दस्तावेज़ प्रसंस्करण एपीआई"
"title": "Java के लिए Aspose.Words में क्लीनअप विकल्पों का उपयोग करना"
"url": "/hi/java/document-manipulation/using-cleanup-options/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Java के लिए Aspose.Words में क्लीनअप विकल्पों का उपयोग करना


## जावा के लिए Aspose.Words में क्लीनअप विकल्पों का उपयोग करने का परिचय

इस ट्यूटोरियल में, हम यह पता लगाएंगे कि मेल मर्ज प्रक्रिया के दौरान दस्तावेज़ों में हेरफेर करने और उन्हें साफ़ करने के लिए Aspose.Words for Java में क्लीनअप विकल्पों का उपयोग कैसे करें। क्लीनअप विकल्प आपको दस्तावेज़ क्लीनअप के विभिन्न पहलुओं को नियंत्रित करने की अनुमति देते हैं, जैसे कि खाली पैराग्राफ़, अप्रयुक्त क्षेत्र और बहुत कुछ हटाना।

## आवश्यक शर्तें

शुरू करने से पहले, सुनिश्चित करें कि आपके प्रोजेक्ट में Aspose.Words for Java लाइब्रेरी एकीकृत है। आप इसे यहाँ से डाउनलोड कर सकते हैं [यहाँ](https://releases.aspose.com/words/java/).

## चरण 1: खाली पैराग्राफ हटाना

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// मर्ज फ़ील्ड डालें
FieldMergeField mergeFieldOption1 = (FieldMergeField) builder.insertField("MERGEFIELD", "Option_1");
mergeFieldOption1.setFieldName("Option_1");
builder.write(" ? ");
FieldMergeField mergeFieldOption2 = (FieldMergeField) builder.insertField("MERGEFIELD", "Option_2");
mergeFieldOption2.setFieldName("Option_2");

// सफ़ाई विकल्प सेट करें
doc.getMailMerge().setCleanupOptions(MailMergeCleanupOptions.REMOVE_EMPTY_PARAGRAPHS);

// विराम चिह्नों के साथ पैराग्राफ़ को साफ़ करने की सुविधा सक्षम करें
doc.getMailMerge().setCleanupParagraphsWithPunctuationMarks(true);

// मेल मर्ज निष्पादित करें
doc.getMailMerge().execute(new String[] { "Option_1", "Option_2" }, new Object[] { null, null });

// दस्तावेज़ सहेजें
doc.save("WorkingWithCleanupOptions.CleanupParagraphsWithPunctuationMarks.docx");
```

इस उदाहरण में, हम एक नया दस्तावेज़ बनाते हैं, मर्ज फ़ील्ड डालते हैं, और खाली पैराग्राफ़ हटाने के लिए क्लीनअप विकल्प सेट करते हैं। इसके अतिरिक्त, हम विराम चिह्नों वाले पैराग्राफ़ को हटाने को सक्षम करते हैं। मेल मर्ज निष्पादित करने के बाद, दस्तावेज़ को निर्दिष्ट क्लीनअप लागू करके सहेजा जाता है।

## चरण 2: असंयुक्त क्षेत्रों को हटाना

```java
Document doc = new Document("Your Directory Path" + "Mail merge destination - Northwind suppliers.docx");
DataSet data = new DataSet();

// अप्रयुक्त क्षेत्रों को हटाने के लिए क्लीनअप विकल्प सेट करें
doc.getMailMerge().setCleanupOptions(MailMergeCleanupOptions.REMOVE_UNUSED_REGIONS);

// क्षेत्रों के साथ मेल मर्ज निष्पादित करें
doc.getMailMerge().executeWithRegions(data);

// दस्तावेज़ सहेजें
doc.save("WorkingWithCleanupOptions.RemoveUnmergedRegions.docx");
```

इस उदाहरण में, हम मर्ज क्षेत्रों के साथ एक मौजूदा दस्तावेज़ खोलते हैं, अप्रयुक्त क्षेत्रों को हटाने के लिए क्लीनअप विकल्प सेट करते हैं, और फिर खाली डेटा के साथ मेल मर्ज निष्पादित करते हैं। यह प्रक्रिया दस्तावेज़ से अप्रयुक्त क्षेत्रों को स्वचालित रूप से हटा देती है।

## चरण 3: खाली फ़ील्ड हटाना

```java
Document doc = new Document("Your Directory Path" + "Table with fields.docx");

// रिक्त फ़ील्ड हटाने के लिए क्लीनअप विकल्प सेट करें
doc.getMailMerge().setCleanupOptions(MailMergeCleanupOptions.REMOVE_EMPTY_FIELDS);

// मेल मर्ज निष्पादित करें
doc.getMailMerge().execute(new String[] { "FullName", "Company", "Address", "Address2", "City" },
    new Object[] { "James Bond", "MI5 Headquarters", "Milbank", "", "London" });

// दस्तावेज़ सहेजें
doc.save("WorkingWithCleanupOptions.RemoveEmptyFields.docx");
```

इस उदाहरण में, हम मर्ज फ़ील्ड वाला एक दस्तावेज़ खोलते हैं, खाली फ़ील्ड हटाने के लिए क्लीनअप विकल्प सेट करते हैं, और डेटा के साथ मेल मर्ज निष्पादित करते हैं। मर्ज के बाद, दस्तावेज़ से कोई भी खाली फ़ील्ड हटा दी जाएगी।

## चरण 4: अप्रयुक्त फ़ील्ड हटाना

```java
Document doc = new Document("Your Directory Path" + "Table with fields.docx");

// अप्रयुक्त फ़ील्ड हटाने के लिए क्लीनअप विकल्प सेट करें
doc.getMailMerge().setCleanupOptions(MailMergeCleanupOptions.REMOVE_UNUSED_FIELDS);

// मेल मर्ज निष्पादित करें
doc.getMailMerge().execute(new String[] { "FullName", "Company", "Address", "Address2", "City" },
    new Object[] { "James Bond", "MI5 Headquarters", "Milbank", "", "London" });

// दस्तावेज़ सहेजें
doc.save("WorkingWithCleanupOptions.RemoveUnusedFields.docx");
```

इस उदाहरण में, हम मर्ज फ़ील्ड वाला एक दस्तावेज़ खोलते हैं, अप्रयुक्त फ़ील्ड को हटाने के लिए क्लीनअप विकल्प सेट करते हैं, और डेटा के साथ मेल मर्ज निष्पादित करते हैं। मर्ज के बाद, दस्तावेज़ से कोई भी अप्रयुक्त फ़ील्ड हटा दी जाएगी।

## चरण 5: सम्मिलित फ़ील्ड हटाना

```java
Document doc = new Document("Your Directory Path" + "Table with fields.docx");

// सम्मिलित फ़ील्ड को हटाने के लिए क्लीनअप विकल्प सेट करें
doc.getMailMerge().setCleanupOptions(MailMergeCleanupOptions.REMOVE_CONTAINING_FIELDS);

// मेल मर्ज निष्पादित करें
doc.getMailMerge().execute(new String[] { "FullName", "Company", "Address", "Address2", "City" },
    new Object[] { "James Bond", "MI5 Headquarters", "Milbank", "", "London" });

// दस्तावेज़ सहेजें
doc.save("WorkingWithCleanupOptions.RemoveContainingFields.docx");
```

इस उदाहरण में, हम मर्ज फ़ील्ड वाले दस्तावेज़ को खोलते हैं, फ़ील्ड को हटाने के लिए क्लीनअप विकल्प सेट करते हैं, और डेटा के साथ मेल मर्ज निष्पादित करते हैं। मर्ज के बाद, फ़ील्ड स्वयं दस्तावेज़ से हटा दिए जाएँगे।

## चरण 6: खाली तालिका पंक्तियाँ हटाना

```java
Document doc = new Document("Your Directory Path" + "Table with fields.docx");

// खाली तालिका पंक्तियों को हटाने के लिए क्लीनअप विकल्प सेट करें
doc.getMailMerge().setCleanupOptions(MailMergeCleanupOptions.REMOVE_EMPTY_TABLE_ROWS);

// मेल मर्ज निष्पादित करें
doc.getMailMerge().execute(new String[] { "FullName", "Company", "Address", "Address2", "City" },
    new Object[] { "James Bond", "MI5 Headquarters", "Milbank", "", "London" });

// दस्तावेज़ सहेजें
doc.save("WorkingWithCleanupOptions.RemoveEmptyTableRows.docx");
```

इस उदाहरण में, हम एक टेबल और मर्ज फ़ील्ड वाला दस्तावेज़ खोलते हैं, खाली टेबल पंक्तियों को हटाने के लिए क्लीनअप विकल्प सेट करते हैं, और डेटा के साथ मेल मर्ज निष्पादित करते हैं। मर्ज के बाद, दस्तावेज़ से कोई भी खाली टेबल पंक्तियाँ हटा दी जाएँगी।

## निष्कर्ष

इस ट्यूटोरियल में, आपने सीखा है कि मेल मर्ज प्रक्रिया के दौरान दस्तावेज़ों में हेरफेर करने और उन्हें साफ़ करने के लिए Aspose.Words for Java में क्लीनअप विकल्पों का उपयोग कैसे करें। ये विकल्प दस्तावेज़ क्लीनअप पर बारीक नियंत्रण प्रदान करते हैं, जिससे आप आसानी से पॉलिश और अनुकूलित दस्तावेज़ बना सकते हैं।

## अक्सर पूछे जाने वाले प्रश्न

### Aspose.Words for Java में क्लीनअप विकल्प क्या हैं?

Aspose.Words for Java में क्लीनअप विकल्प ऐसी सेटिंग्स हैं जो आपको मेल मर्ज प्रक्रिया के दौरान दस्तावेज़ क्लीनअप के विभिन्न पहलुओं को नियंत्रित करने की अनुमति देती हैं। वे आपको खाली पैराग्राफ, अप्रयुक्त क्षेत्रों और अधिक जैसे अनावश्यक तत्वों को हटाने में सक्षम बनाते हैं, जिससे यह सुनिश्चित होता है कि आपका अंतिम दस्तावेज़ अच्छी तरह से संरचित और पॉलिश है।

### मैं अपने दस्तावेज़ से खाली पैराग्राफ़ कैसे हटा सकता हूँ?

Aspose.Words for Java का उपयोग करके अपने दस्तावेज़ से खाली पैराग्राफ़ हटाने के लिए, आप सेट कर सकते हैं `MailMergeCleanupOptions.REMOVE_EMPTY_PARAGRAPHS` विकल्प को true पर सेट करें। इससे वे पैराग्राफ़ अपने आप हट जाएँगे जिनमें कोई विषय-वस्तु नहीं है, जिसके परिणामस्वरूप दस्तावेज़ साफ़-सुथरा हो जाएगा।

### इसका उद्देश्य क्या है? `REMOVE_UNUSED_REGIONS` सफाई विकल्प?

The `MailMergeCleanupOptions.REMOVE_UNUSED_REGIONS` विकल्प का उपयोग मेल मर्ज प्रक्रिया के दौरान दस्तावेज़ में उन क्षेत्रों को हटाने के लिए किया जाता है जिनमें कोई संगत डेटा नहीं होता है। यह अप्रयुक्त प्लेसहोल्डर्स से छुटकारा पाकर आपके दस्तावेज़ को साफ-सुथरा रखने में मदद करता है।

### क्या मैं Java के लिए Aspose.Words का उपयोग करके किसी दस्तावेज़ से खाली तालिका पंक्तियों को हटा सकता हूँ?

हां, आप किसी दस्तावेज़ से खाली तालिका पंक्तियों को सेट करके हटा सकते हैं `MailMergeCleanupOptions.REMOVE_EMPTY_TABLE_ROWS` क्लीनअप विकल्प को सही पर सेट करें। यह स्वचालित रूप से उन सभी तालिका पंक्तियों को हटा देगा जिनमें डेटा नहीं है, जिससे आपके दस्तावेज़ में एक अच्छी तरह से संरचित तालिका सुनिश्चित होगी।

### जब मैं सेट करता हूँ तो क्या होता है? `REMOVE_CONTAINING_FIELDS` विकल्प?

सेटिंग `MailMergeCleanupOptions.REMOVE_CONTAINING_FIELDS` विकल्प मेल मर्ज प्रक्रिया के दौरान दस्तावेज़ से संपूर्ण मर्ज फ़ील्ड को हटा देगा, जिसमें उसका पैराग्राफ़ भी शामिल है। यह तब उपयोगी होता है जब आप मर्ज फ़ील्ड और उनके संबंधित टेक्स्ट को हटाना चाहते हैं।

### मैं अपने दस्तावेज़ से अप्रयुक्त मर्ज फ़ील्ड कैसे हटा सकता हूँ?

किसी दस्तावेज़ से अप्रयुक्त मर्ज फ़ील्ड को हटाने के लिए, आप सेट कर सकते हैं `MailMergeCleanupOptions.REMOVE_UNUSED_FIELDS` विकल्प को true पर सेट करें। इससे मेल मर्ज के दौरान पॉप्युलेट न होने वाले मर्ज फ़ील्ड अपने आप हट जाएँगे, जिससे दस्तावेज़ साफ़ हो जाएगा।

### के बीच क्या अंतर है `REMOVE_EMPTY_FIELDS` और `REMOVE_UNUSED_FIELDS` सफाई विकल्प?

The `REMOVE_EMPTY_FIELDS` विकल्प उन मर्ज फ़ील्ड को हटा देता है जिनमें कोई डेटा नहीं है या जो मेल मर्ज प्रक्रिया के दौरान खाली हैं। दूसरी ओर, `REMOVE_UNUSED_FIELDS` विकल्प मर्ज के दौरान डेटा से पॉप्युलेट न किए गए मर्ज फ़ील्ड को हटाता है। उनके बीच का चुनाव इस बात पर निर्भर करता है कि आप बिना कंटेंट वाले फ़ील्ड को हटाना चाहते हैं या फिर वे फ़ील्ड जो विशिष्ट मर्ज ऑपरेशन में उपयोग नहीं किए गए हैं।

### मैं विराम चिह्नों वाले पैराग्राफ़ को हटाने की सुविधा कैसे सक्षम कर सकता हूँ?

विराम चिह्नों वाले पैराग्राफ़ को हटाने के लिए, आप सेट कर सकते हैं `cleanupParagraphsWithPunctuationMarks` विकल्प को सही पर सेट करें और सफाई के लिए विचार किए जाने वाले विराम चिह्नों को निर्दिष्ट करें। यह आपको अनावश्यक विराम चिह्न-केवल पैराग्राफ़ को हटाकर अधिक परिष्कृत दस्तावेज़ बनाने की अनुमति देता है।

### क्या मैं Aspose.Words for Java में क्लीनअप विकल्पों को अनुकूलित कर सकता हूँ?

हां, आप अपनी विशिष्ट आवश्यकताओं के अनुसार क्लीनअप विकल्पों को कस्टमाइज़ कर सकते हैं। आप चुन सकते हैं कि कौन से क्लीनअप विकल्प लागू करने हैं और उन्हें अपने दस्तावेज़ क्लीनअप आवश्यकताओं के अनुसार कॉन्फ़िगर करें, यह सुनिश्चित करते हुए कि आपका अंतिम दस्तावेज़ आपके वांछित मानकों को पूरा करता है।


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}