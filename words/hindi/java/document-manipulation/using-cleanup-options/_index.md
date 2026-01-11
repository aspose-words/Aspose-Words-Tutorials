---
date: 2026-01-11
description: Aspose.Words for Java की सफ़ाई विकल्पों का उपयोग करके Word दस्तावेज़
  को कैसे साफ़ करें, सीखें, जिसमें खाली पैराग्राफ़, खाली तालिका पंक्तियों और अप्रयुक्त
  फ़ील्ड्स को हटाना शामिल है।
linktitle: Using Cleanup Options
second_title: Aspose.Words Java Document Processing API
title: Aspose.Words क्लीनअप विकल्प (Java) का उपयोग करके Word दस्तावेज़ को साफ़ करें
url: /hi/java/document-manipulation/using-cleanup-options/
weight: 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words क्लीनअप विकल्पों (Java) का उपयोग करके Word दस्तावेज़ को साफ़ करें

इस ट्यूटोरियल में आप सीखेंगे कि Aspose.Words for Java के साथ **Word दस्तावेज़** फ़ाइलों को कैसे साफ़ किया जाए। चाहे आप इनवॉइस, कॉन्ट्रैक्ट, या बड़े पैमाने पर मेल‑मर्ज रिपोर्ट बना रहे हों, अनचाहे खाली पैराग्राफ, अप्रयुक्त फ़ील्ड, या खाली टेबल पंक्तियाँ अंतिम आउटपुट को अनप्रोफेशनल बना सकती हैं। हम प्रत्येक क्लीनअप विकल्प को चरण‑दर‑चरण समझाएंगे, आपको आवश्यक सटीक कोड दिखाएंगे, और *क्यों* प्रत्येक सेटिंग महत्वपूर्ण है, यह समझाएंगे ताकि आप हर बार परिष्कृत दस्तावेज़ बना सकें।

## त्वरित उत्तर
- **“clean up Word दस्तावेज़” का क्या अर्थ है?** मेल‑मर्ज ऑपरेशन के बाद खाली पैराग्राफ, अप्रयुक्त मर्ज रीजन, खाली टेबल पंक्तियों और अन्य अनावश्यक तत्वों को हटाना।  
- **कौन सा क्लीनअप विकल्प खाली पैराग्राफ हटाता है?** `MailMergeCleanupOptions.REMOVE_EMPTY_PARAGRAPHS`।  
- **मैं खाली टेबल पंक्तियों को कैसे हटाऊँ?** `MailMergeCleanupOptions.REMOVE_EMPTY_TABLE_ROWS` का उपयोग करें।  
- **क्या मैं उन फ़ील्ड्स को हटा सकता हूँ जो कभी भरे नहीं गए?** हाँ – `MailMergeCleanupOptions.REMOVE_UNUSED_FIELDS` या `REMOVE_EMPTY_FIELDS`।  
- **क्या इन उदाहरणों को चलाने के लिए लाइसेंस आवश्यक है?** मूल्यांकन के लिए एक फ्री ट्रायल काम करता है; उत्पादन उपयोग के लिए एक व्यावसायिक लाइसेंस आवश्यक है।

## मेल‑मर्ज के संदर्भ में “Clean Up Word Document” क्या है?
जब आप मेल‑मर्ज करते हैं, तो Aspose.Words डेटा को मर्ज फ़ील्ड्स और रीजन में डालता है। यदि कुछ फ़ील्ड को `null` या खाली स्ट्रिंग मिलती है, तो दस्तावेज़ में बिखरे हुए पैराग्राफ, खाली टेबल, या प्लेसहोल्डर रीजन रह सकते हैं। **क्लीनअप विकल्प** इन अवशेषों को स्वचालित रूप से हटाते हैं, जिससे एक साफ़, प्रिंट‑तैयार दस्तावेज़ मिल जाता है।

## क्लीनअप विकल्पों का उपयोग क्यों करें?
- **पेशेवर दिखावट:** कोई खाली लाइन या अनाथ टेबल नहीं।  
- **छोटा फ़ाइल आकार:** अप्रयुक्त तत्वों को हटाने से दस्तावेज़ का वजन कम होता है।  
- **सरल डाउनस्ट्रीम प्रोसेसिंग:** साफ़ दस्तावेज़ को PDF, HTML, या अन्य फ़ॉर्मेट में बदलना आसान होता है।  
- **समय बचत:** एक‑लाइन सेटिंग्स मैन्युअल पोस्ट‑प्रोसेसिंग स्क्रिप्ट्स को बदल देती हैं।

## पूर्वापेक्षाएँ
- Java विकास वातावरण (JDK 8+).  
- Aspose.Words for Java लाइब्रेरी – इसे [here](https://releases.aspose.com/words/java/) से डाउनलोड करें।  
- मेल‑मर्ज अवधारणाओं की बुनियादी समझ।

## चरण‑दर‑चरण मार्गदर्शिका

### चरण 1: खाली पैराग्राफ कैसे हटाएँ (Java)
पहले, हम दिखाएंगे कि कैसे उन पैराग्राफ़ को हटाया जाए जिनमें कोई दृश्यमान टेक्स्ट नहीं है। यह विशेष रूप से उपयोगी है जब एक मर्ज फ़ील्ड `null` में बदल जाता है।

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert merge fields
FieldMergeField mergeFieldOption1 = (FieldMergeField) builder.insertField("MERGEFIELD", "Option_1");
mergeFieldOption1.setFieldName("Option_1");
builder.write(" ? ");
FieldMergeField mergeFieldOption2 = (FieldMergeField) builder.insertField("MERGEFIELD", "Option_2");
mergeFieldOption2.setFieldName("Option_2");

// Set cleanup options
doc.getMailMerge().setCleanupOptions(MailMergeCleanupOptions.REMOVE_EMPTY_PARAGRAPHS);

// Enable cleanup of paragraphs that contain only punctuation marks
doc.getMailMerge().setCleanupParagraphsWithPunctuationMarks(true);

// Execute mail merge (both fields are null, so they become empty)
doc.getMailMerge().execute(new String[] { "Option_1", "Option_2" }, new Object[] { null, null });

// Save the cleaned document
doc.save("WorkingWithCleanupOptions.CleanupParagraphsWithPunctuationMarks.docx");
```

**यहाँ क्या होता है?**  
- `REMOVE_EMPTY_PARAGRAPHS` Aspose.Words को बताता है कि मर्ज के बाद जो भी पैराग्राफ खाली रह जाता है, उसे हटाया जाए।  
- `cleanupParagraphsWithPunctuationMarks` को सक्षम करने से वे पैराग्राफ भी हट जाते हैं जो केवल विराम चिह्नों से बने होते हैं (जैसे, “?”)।

### चरण 2: अनमर्ज्ड रीजन कैसे हटाएँ
यदि किसी मेल‑मर्ज रीजन के लिए कोई डेटा नहीं है, तो आप उसे पूरी तरह से हटा सकते हैं।

```java
Document doc = new Document("Your Directory Path" + "Mail merge destination - Northwind suppliers.docx");
DataSet data = new DataSet();

// Set cleanup options to remove unused regions
doc.getMailMerge().setCleanupOptions(MailMergeCleanupOptions.REMOVE_UNUSED_REGIONS);

// Execute mail merge with regions (the DataSet is empty)
doc.getMailMerge().executeWithRegions(data);

// Save the cleaned document
doc.save("WorkingWithCleanupOptions.RemoveUnmergedRegions.docx");
```

**यह क्यों महत्वपूर्ण है:**  
- अप्रयुक्त रीजन अक्सर खाली सेक्शन या बिखरे हुए हेडिंग छोड़ते हैं। `REMOVE_UNUSED_REGIONS` फ़्लैग इन्हें स्वचालित रूप से साफ़ करता है।

### चरण 3: खाली फ़ील्ड कैसे हटाएँ
जब किसी फ़ील्ड को खाली स्ट्रिंग मिलती है, तो आप पूरे फ़ील्ड को हटाना चाहेंगे बजाय एक खाली प्लेसहोल्डर छोड़ने के।

```java
Document doc = new Document("Your Directory Path" + "Table with fields.docx");

// Set cleanup options to remove empty fields
doc.getMailMerge().setCleanupOptions(MailMergeCleanupOptions.REMOVE_EMPTY_FIELDS);

// Execute mail merge with a mix of populated and empty values
doc.getMailMerge().execute(new String[] { "FullName", "Company", "Address", "Address2", "City" },
    new Object[] { "James Bond", "MI5 Headquarters", "Milbank", "", "London" });

// Save the cleaned document
doc.save("WorkingWithCleanupOptions.RemoveEmptyFields.docx");
```

### चरण 4: अप्रयुक्त फ़ील्ड कैसे हटाएँ
यदि कुछ फ़ील्ड मर्ज के दौरान कभी संदर्भित नहीं होते, तो आप उन्हें पूरी तरह से हटा सकते हैं।

```java
Document doc = new Document("Your Directory Path" + "Table with fields.docx");

// Set cleanup options to remove unused fields
doc.getMailMerge().setCleanupOptions(MailMergeCleanupOptions.REMOVE_UNUSED_FIELDS);

// Execute mail merge
doc.getMailMerge().execute(new String[] { "FullName", "Company", "Address", "Address2", "City" },
    new Object[] { "James Bond", "MI5 Headquarters", "Milbank", "", "London" });

// Save the cleaned document
doc.save("WorkingWithCleanupOptions.RemoveUnusedFields.docx");
```

### चरण 5: कंटेनिंग फ़ील्ड कैसे हटाएँ
कभी‑कभी एक मर्ज फ़ील्ड एक पैराग्राफ के अंदर रहता है जिसे आप भी हटाना चाहते हैं।

```java
Document doc = new Document("Your Directory Path" + "Table with fields.docx");

// Set cleanup options to remove containing fields
doc.getMailMerge().setCleanupOptions(MailMergeCleanupOptions.REMOVE_CONTAINING_FIELDS);

// Execute mail merge
doc.getMailMerge().execute(new String[] { "FullName", "Company", "Address", "Address2", "City" },
    new Object[] { "James Bond", "MI5 Headquarters", "Milbank", "", "London" });

// Save the cleaned document
doc.save("WorkingWithCleanupOptions.RemoveContainingFields.docx");
```

### चरण 6: खाली टेबल पंक्तियों को कैसे हटाएँ
टेबल अक्सर ऐसी पंक्तियों के साथ समाप्त होते हैं जिनमें केवल खाली फ़ील्ड होते हैं। यह विकल्प उन पंक्तियों को हटाता है।

```java
Document doc = new Document("Your Directory Path" + "Table with fields.docx");

// Set cleanup options to remove empty table rows
doc.getMailMerge().setCleanupOptions(MailMergeCleanupOptions.REMOVE_EMPTY_TABLE_ROWS);

// Execute mail merge
doc.getMailMerge().execute(new String[] { "FullName", "Company", "Address", "Address2", "City" },
    new Object[] { "James Bond", "MI5 Headquarters", "Milbank", "", "London" });

// Save the cleaned document
doc.save("WorkingWithCleanupOptions.RemoveEmptyTableRows.docx");
```

## सामान्य समस्याएँ और ट्रबलशूटिंग
- **पैराग्राफ नहीं हट रहे:** सुनिश्चित करें कि `setCleanupParagraphsWithPunctuationMarks(true)` को क्लीनअप विकल्प सेट करने के *बाद* कॉल किया गया है।  
- **खाली टेबल पंक्तियाँ बनी रहती हैं:** जाँचें कि टेबल सेल वास्तव में खाली स्ट्रिंग्स (न कि व्हाइटस्पेस) रखती हैं।  
- **अप्रयुक्त फ़ील्ड रह गए:** दोबारा जाँचें कि आप सही एनोम (`REMOVE_UNUSED_FIELDS`) का उपयोग कर रहे हैं और मर्ज फ़ील्ड कहीं और गलती से नहीं भरे गए हैं।

## अक्सर पूछे जाने वाले प्रश्न

**प्रश्न: `REMOVE_EMPTY_FIELDS` और `REMOVE_UNUSED_FIELDS` में क्या अंतर है?**  
**उत्तर:** `REMOVE_EMPTY_FIELDS` उन फ़ील्ड को हटाता है जो मर्ज के दौरान खाली स्ट्रिंग या `null` प्राप्त करते हैं, जबकि `REMOVE_UNUSED_FIELDS` उन फ़ील्ड को हटाता है जिन्हें मर्ज ऑपरेशन ने कभी संदर्भित नहीं किया।

**प्रश्न: क्या मैं कई क्लीनअप विकल्पों को संयोजित कर सकता हूँ?**  
**उत्तर:** हाँ। `setCleanupOptions` मेथड एनोम मानों के बिटवाइज़ OR को स्वीकार करता है, जिससे आप एक ही कॉल में पैराग्राफ, टेबल और रीजन को साफ़ कर सकते हैं।

**प्रश्न: क्या `cleanupParagraphsWithPunctuationMarks` को सक्षम करने से सामान्य टेक्स्ट प्रभावित होता है?**  
**उत्तर:** यह केवल उन पैराग्राफ़ को हटाता है जो केवल विराम चिह्नों से बने होते हैं (जैसे, “?” या “---”)। सामान्य वाक्य अपरिवर्तित रहते हैं।

**प्रश्न: क्या यह संभव है कि किन विराम चिह्नों को माना जाए, इसे कस्टमाइज़ किया जा सके?**  
**उत्तर:** वर्तमान API एक पूर्वनिर्धारित विराम चिह्न सेट का उपयोग करता है। कस्टम व्यवहार के लिए, आपको मर्ज के बाद दस्तावेज़ को पोस्ट‑प्रोसेस करना होगा।

**प्रश्न: क्या ये क्लीनअप विकल्प PDF रूपांतरण के साथ काम करते हैं?**  
**उत्तर:** बिल्कुल। एक बार Word दस्तावेज़ साफ़ हो जाने के बाद, आप इसे PDF, HTML, या किसी भी समर्थित फ़ॉर्मेट में बिना अनचाहे तत्वों के परिवर्तित कर सकते हैं।

## निष्कर्ष
अब आपके पास Aspose.Words for Java के साथ मेल‑मर्ज के दौरान **Word दस्तावेज़** फ़ाइलों को साफ़ करने के लिए एक पूर्ण टूलबॉक्स है। उपयुक्त `MailMergeCleanupOptions` चुनकर, आप स्वचालित रूप से खाली पैराग्राफ, खाली टेबल पंक्तियाँ, अप्रयुक्त फ़ील्ड और अधिक हटा सकते हैं—जिससे हर बार आपको एक सुगठित, उत्पादन‑तैयार दस्तावेज़ मिलता है।

---

**अंतिम अपडेट:** 2026-01-11  
**परीक्षित संस्करण:** Aspose.Words for Java 24.11  
**लेखक:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}