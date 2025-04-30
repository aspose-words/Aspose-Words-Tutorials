---
"description": "Java के लिए Aspose.Words का उपयोग करके DataTable से टेबल बनाने का तरीका जानें। आसानी से फ़ॉर्मेटेड टेबल के साथ पेशेवर Word दस्तावेज़ बनाएँ।"
"linktitle": "डेटाटेबल से टेबल बनाएं"
"second_title": "Aspose.Words जावा दस्तावेज़ प्रसंस्करण एपीआई"
"title": "डेटाटेबल से टेबल बनाएं"
"url": "/hi/java/table-processing/generate-table-from-datatable/"
"weight": 11
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# डेटाटेबल से टेबल बनाएं

## परिचय

डेटा स्रोतों से गतिशील रूप से तालिकाएँ बनाना कई अनुप्रयोगों में एक सामान्य कार्य है। चाहे आप रिपोर्ट, चालान या डेटा सारांश बना रहे हों, प्रोग्रामेटिक रूप से डेटा के साथ तालिका को पॉप्युलेट करने में सक्षम होने से आपका बहुत समय और प्रयास बच सकता है। इस ट्यूटोरियल में, हम जावा के लिए Aspose.Words का उपयोग करके DataTable से तालिका बनाने का तरीका जानेंगे। हम प्रक्रिया को प्रबंधनीय चरणों में विभाजित करेंगे, यह सुनिश्चित करते हुए कि आपको प्रत्येक भाग की स्पष्ट समझ है।

## आवश्यक शर्तें

कोड में गोता लगाने से पहले, आइए सुनिश्चित करें कि आपके पास आरंभ करने के लिए आवश्यक सभी चीजें मौजूद हैं:

1. जावा डेवलपमेंट किट (JDK): सुनिश्चित करें कि आपके मशीन पर JDK इंस्टॉल है। आप इसे यहाँ से डाउनलोड कर सकते हैं। [ओरेकल वेबसाइट](https://www.oracle.com/java/technologies/javase-jdk11-downloads.html).
   
2. जावा के लिए Aspose.Words: आपको Aspose.Words लाइब्रेरी की आवश्यकता होगी। आप नवीनतम संस्करण यहाँ से डाउनलोड कर सकते हैं [एस्पोज का रिलीज़ पृष्ठ](https://releases.aspose.com/words/java/).

3. आईडीई: इंटेलीज आईडिया या एक्लिप्स जैसे एकीकृत विकास वातावरण (आईडीई) से कोडिंग आसान हो जाएगी।

4. जावा का बुनियादी ज्ञान: जावा प्रोग्रामिंग अवधारणाओं से परिचित होने से आपको कोड स्निपेट को बेहतर ढंग से समझने में मदद मिलेगी।

5. नमूना डेटा: इस ट्यूटोरियल के लिए, हम डेटा स्रोत का अनुकरण करने के लिए "List of people.xml" नामक XML फ़ाइल का उपयोग करेंगे। आप परीक्षण के लिए नमूना डेटा के साथ यह फ़ाइल बना सकते हैं।

## चरण 1: नया दस्तावेज़ बनाएँ

सबसे पहले, हमें एक नया दस्तावेज़ बनाना होगा जहाँ हमारी तालिका रहेगी। यह हमारे काम के लिए कैनवास है।

```java
Document doc = new Document();
```

यहाँ, हम एक नया उदाहरण प्रस्तुत करते हैं `Document` यह हमारा कार्य दस्तावेज़ होगा, जहाँ हम अपनी तालिका बनाएंगे।

## चरण 2: डॉक्यूमेंटबिल्डर को आरंभ करें

आगे, हम इसका उपयोग करेंगे `DocumentBuilder` क्लास, जो हमें दस्तावेज़ को अधिक आसानी से हेरफेर करने की अनुमति देता है।

```java
DocumentBuilder builder = new DocumentBuilder(doc);
```

The `DocumentBuilder` ऑब्जेक्ट दस्तावेज़ में तालिकाओं, पाठ और अन्य तत्वों को सम्मिलित करने के लिए विधियाँ प्रदान करता है।

## चरण 3: पृष्ठ अभिविन्यास सेट करें

चूंकि हम चाहते हैं कि हमारी तालिका चौड़ी हो, इसलिए हम पृष्ठ का ओरिएंटेशन लैंडस्केप पर सेट करेंगे।

```java
doc.getFirstSection().getPageSetup().setOrientation(Orientation.LANDSCAPE);
```

यह चरण महत्वपूर्ण है क्योंकि यह सुनिश्चित करता है कि हमारी तालिका बिना कटे पृष्ठ पर अच्छी तरह से फिट हो जाए।

## चरण 4: XML से डेटा लोड करें

अब, हमें XML फ़ाइल से अपना डेटा लोड करना होगा `DataTable`. यहीं से हमारा डेटा आता है।

```java
DataSet ds = new DataSet();
ds.readXml(getMyDir() + "List of people.xml");
DataTable dataTable = ds.getTables().get(0);
```

यहाँ, हम XML फ़ाइल पढ़ते हैं और डेटासेट से पहली तालिका प्राप्त करते हैं। `DataTable` वह डेटा रखेगा जिसे हम अपने दस्तावेज़ में प्रदर्शित करना चाहते हैं।

## चरण 5: डेटाटेबल से तालिका आयात करें

अब आता है रोमांचक हिस्सा: हमारे डेटा को तालिका के रूप में दस्तावेज़ में आयात करना।

```java
Table table = importTableFromDataTable(builder, dataTable, true);
```

हम इस विधि को कहते हैं `importTableFromDataTable`, गुजर रहा है `DocumentBuilder`, हमारा `DataTable`, और एक बूलियन यह इंगित करने के लिए कि क्या स्तंभ शीर्षकों को शामिल करना है।

## चरण 6: टेबल को स्टाइल करें

एक बार जब हमारी टेबल तैयार हो जाए, तो हम इसे अच्छा दिखाने के लिए इसमें कुछ स्टाइलिंग कर सकते हैं।

```java
table.setStyleIdentifier(StyleIdentifier.MEDIUM_LIST_2_ACCENT_1);
table.setStyleOptions(TableStyleOptions.FIRST_ROW | TableStyleOptions.ROW_BANDS | TableStyleOptions.LAST_COLUMN);
```

यह कोड तालिका पर एक पूर्वनिर्धारित शैली लागू करता है, जिससे इसकी दृश्य अपील और पठनीयता बढ़ जाती है।

## चरण 7: अवांछित कोशिकाओं को हटाएँ

यदि आपके पास कोई ऐसा कॉलम है जिसे आप प्रदर्शित नहीं करना चाहते हैं, जैसे कि कोई छवि कॉलम, तो आप उसे आसानी से हटा सकते हैं।

```java
table.getFirstRow().getLastCell().removeAllChildren();
```

यह चरण सुनिश्चित करता है कि हमारी तालिका केवल प्रासंगिक जानकारी ही दिखाए।

## चरण 8: दस्तावेज़ सहेजें

अंत में, हम अपने दस्तावेज़ को उत्पन्न तालिका के साथ सहेजते हैं।

```java
doc.save(getArtifactsDir() + "WorkingWithTables.BuildTableFromDataTable.docx");
```

यह पंक्ति दस्तावेज़ को निर्दिष्ट निर्देशिका में सहेजती है, जिससे आप परिणामों की समीक्षा कर सकते हैं।

## importTableFromDataTable विधि

आइये इस पर करीब से नज़र डालें `importTableFromDataTable` विधि। यह विधि तालिका संरचना बनाने और इसे डेटा के साथ पॉप्युलेट करने के लिए जिम्मेदार है।

### चरण 1: टेबल शुरू करें

सबसे पहले, हमें दस्तावेज़ में एक नई तालिका शुरू करनी होगी।

```java
Table table = builder.startTable();
```

इससे हमारे दस्तावेज़ में एक नई तालिका आरंभ हो जाती है।

### चरण 2: कॉलम शीर्षक जोड़ें

यदि हम स्तंभ शीर्षकों को शामिल करना चाहते हैं, तो हम जाँच करते हैं `importColumnHeadings` झंडा।

```java
if (importColumnHeadings) {
    // मूल स्वरूपण संग्रहित करें
    boolean boldValue = builder.getFont().getBold();
    int paragraphAlignmentValue = builder.getParagraphFormat().getAlignment();

    // शीर्षक स्वरूपण सेट करें
    builder.getFont().setBold(true);
    builder.getParagraphFormat().setAlignment(ParagraphAlignment.CENTER);

    // स्तंभ नाम डालें
    for (DataColumn column : dataTable.getColumns()) {
        builder.insertCell();
        builder.writeln(column.getColumnName());
    }

    builder.endRow();

    // मूल स्वरूपण पुनर्स्थापित करें
    builder.getFont().setBold(boldValue);
    builder.getParagraphFormat().setAlignment(paragraphAlignmentValue);
}
```

कोड का यह ब्लॉक शीर्षक पंक्ति को प्रारूपित करता है और कॉलम के नामों को सम्मिलित करता है `DataTable`.

### चरण 3: तालिका को डेटा से भरें

अब, हम प्रत्येक पंक्ति के माध्यम से लूप करते हैं `DataTable` तालिका में डेटा सम्मिलित करने के लिए.

```java
for (DataRow dataRow : (Iterable<DataRow>) dataTable.getRows()) {
    for (Object item : dataRow.getItemArray()) {
        builder.insertCell();
        switch (item.getClass().getName()) {
            case "DateTime":
                Date dateTime = (Date) item;
                SimpleDateFormat simpleDateFormat = new SimpleDateFormat("MMMM d, yyyy");
                builder.write(simpleDateFormat.format(dateTime));
                break;
            default:
                builder.write(item.toString());
                break;
        }
    }
    builder.endRow();
}
```

इस अनुभाग में, हम विभिन्न डेटा प्रकारों को संभालते हैं, तिथियों को उचित रूप से प्रारूपित करते हैं जबकि अन्य डेटा को पाठ के रूप में सम्मिलित करते हैं।

### चरण 4: टेबल समाप्त करें

अंत में, जब सारा डेटा डाल दिया जाता है तो हम तालिका को पूरा कर लेते हैं।

```java
builder.endTable();
```

यह रेखा हमारी तालिका के अंत को चिह्नित करती है, जिससे `DocumentBuilder` यह जानने के लिए कि हमने यह अनुभाग पूरा कर लिया है।

## निष्कर्ष

और अब आप यह कर सकते हैं! आपने सफलतापूर्वक सीख लिया है कि Aspose.Words for Java का उपयोग करके DataTable से टेबल कैसे बनाई जाती है। इन चरणों का पालन करके, आप विभिन्न डेटा स्रोतों के आधार पर अपने दस्तावेज़ों में आसानी से गतिशील तालिकाएँ बना सकते हैं। चाहे आप रिपोर्ट बना रहे हों या चालान, यह विधि आपके वर्कफ़्लो को सुव्यवस्थित करेगी और आपके दस्तावेज़ निर्माण प्रक्रिया को बढ़ाएगी।

## अक्सर पूछे जाने वाले प्रश्न

### Java के लिए Aspose.Words क्या है?
जावा के लिए Aspose.Words, Word दस्तावेज़ों को प्रोग्रामेटिक रूप से बनाने, उनमें हेरफेर करने और परिवर्तित करने के लिए एक शक्तिशाली लाइब्रेरी है।

### क्या मैं Aspose.Words का निःशुल्क उपयोग कर सकता हूँ?
हां, Aspose एक निःशुल्क परीक्षण संस्करण प्रदान करता है। आप इसे यहां से डाउनलोड कर सकते हैं [यहाँ](https://releases.aspose.com/).

### मैं Aspose.Words में तालिकाओं को कैसे स्टाइल करूँ?
आप लाइब्रेरी द्वारा प्रदान किए गए पूर्वनिर्धारित शैली पहचानकर्ताओं और विकल्पों का उपयोग करके शैलियाँ लागू कर सकते हैं।

### मैं तालिकाओं में किस प्रकार का डेटा सम्मिलित कर सकता हूँ?
आप पाठ, संख्याएं और दिनांक सहित विभिन्न डेटा प्रकार सम्मिलित कर सकते हैं, जिन्हें तदनुसार स्वरूपित किया जा सकता है।

### मुझे Aspose.Words के लिए समर्थन कहां मिल सकता है?
आप सहायता पा सकते हैं और प्रश्न पूछ सकते हैं [एस्पोज फोरम](https://forum.aspose.com/c/words/8/).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}