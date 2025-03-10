---
title: Aspose.Words पायथन का उपयोग करके दस्तावेज़ तालिका शैलियाँ और स्वरूपण
linktitle: दस्तावेज़ तालिका शैलियाँ और स्वरूपण
second_title: Aspose.Words पायथन दस्तावेज़ प्रबंधन API
description: Python के लिए Aspose.Words का उपयोग करके दस्तावेज़ तालिकाओं को स्टाइल और फ़ॉर्मेट करना सीखें। चरण-दर-चरण मार्गदर्शिकाओं और कोड उदाहरणों के साथ तालिकाएँ बनाएँ, कस्टमाइज़ करें और निर्यात करें। आज ही अपने दस्तावेज़ प्रस्तुतियों को बेहतर बनाएँ!
weight: 12
url: /hi/python-net/tables-and-formatting/document-table-styles-formatting/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words पायथन का उपयोग करके दस्तावेज़ तालिका शैलियाँ और स्वरूपण


दस्तावेज़ तालिकाएँ सूचना को व्यवस्थित और आकर्षक तरीके से प्रस्तुत करने में महत्वपूर्ण भूमिका निभाती हैं। Aspose.Words for Python टूल का एक शक्तिशाली सेट प्रदान करता है जो डेवलपर्स को तालिकाओं के साथ कुशलतापूर्वक काम करने और उनकी शैलियों और स्वरूपण को अनुकूलित करने की अनुमति देता है। इस लेख में, हम Aspose.Words for Python API का उपयोग करके दस्तावेज़ तालिकाओं में हेरफेर और सुधार करने का तरीका जानेंगे। आइए शुरू करते हैं!

## पायथन के लिए Aspose.Words के साथ आरंभ करना

इससे पहले कि हम दस्तावेज़ तालिका शैलियों और स्वरूपण की बारीकियों में उतरें, आइए सुनिश्चित करें कि आपके पास आवश्यक उपकरण सेट अप हैं:

1. पायथन के लिए Aspose.Words स्थापित करें: pip का उपयोग करके Aspose.Words लाइब्रेरी स्थापित करके शुरू करें। यह निम्न कमांड के साथ किया जा सकता है:
   
    ```bash
    pip install aspose-words
    ```

2. लाइब्रेरी आयात करें: निम्नलिखित आयात कथन का उपयोग करके Aspose.Words लाइब्रेरी को अपनी पायथन स्क्रिप्ट में आयात करें:

    ```python
    import aspose.words as aw
    ```

3. दस्तावेज़ लोड करें: Aspose.Words API का उपयोग करके कोई मौजूदा दस्तावेज़ लोड करें या नया दस्तावेज़ बनाएँ।

## दस्तावेज़ों में तालिकाएँ बनाना और सम्मिलित करना

पायथन के लिए Aspose.Words का उपयोग करके दस्तावेज़ों में तालिकाएँ बनाने और सम्मिलित करने के लिए, इन चरणों का पालन करें:

1.  एक तालिका बनाएं: का उपयोग करें`DocumentBuilder` क्लास का उपयोग करके एक नई तालिका बनाएं और पंक्तियों और स्तंभों की संख्या निर्दिष्ट करें।

    ```python
    builder = aw.DocumentBuilder(doc)
    table = builder.start_table()
    ```

2.  डेटा सम्मिलित करें: बिल्डर का उपयोग करके तालिका में डेटा जोड़ें`insert_cell` और`write` तरीके.

    ```python
    builder.insert_cell()
    builder.write("Header 1")
    builder.insert_cell()
    builder.write("Header 2")
    builder.end_row()
    ```

3. पंक्तियों को दोहराएँ: समान पैटर्न का अनुसरण करते हुए आवश्यकतानुसार पंक्तियाँ और कक्ष जोड़ें।

4.  दस्तावेज़ में तालिका डालें: अंत में, दस्तावेज़ में तालिका डालें`end_table` तरीका।

    ```python
    builder.end_table()
    ```

## मूल तालिका स्वरूपण लागू करना

 बुनियादी तालिका स्वरूपण को द्वारा प्रदान की गई विधियों का उपयोग करके प्राप्त किया जा सकता है`Table` और`Cell` कक्षाएं। यहां बताया गया है कि आप अपनी टेबल की उपस्थिति को कैसे बढ़ा सकते हैं:

1. स्तंभ की चौड़ाई निर्धारित करें: उचित संरेखण और दृश्य अपील सुनिश्चित करने के लिए स्तंभों की चौड़ाई समायोजित करें।

    ```python
    for cell in table.first_row.cells:
        cell.cell_format.preferred_width = aw.PreferredWidth.from_points(100)
    ```

2. सेल पैडिंग: बेहतर स्पेसिंग के लिए सेल में पैडिंग जोड़ें।

    ```python
    for row in table.rows:
        for cell in row.cells:
            cell.cell_format.set_paddings(10, 10, 10, 10)
    ```

3. पंक्ति की ऊंचाई: आवश्यकतानुसार पंक्ति की ऊंचाई को अनुकूलित करें।

    ```python
    for row in table.rows:
        row.row_format.height_rule = aw.HeightRule.AT_LEAST
        row.row_format.height = aw.ConvertUtil.inch_to_points(1)
    ```

## जटिल लेआउट के लिए कोशिकाओं को मर्ज करना और विभाजित करना

जटिल तालिका लेआउट बनाने के लिए अक्सर कक्षों को विलय और विभाजित करने की आवश्यकता होती है:

1. कोशिकाओं को मर्ज करें: एकाधिक कोशिकाओं को मर्ज करके एक बड़ी एकल कोशिका बनाएं।

    ```python
    table.rows[0].cells[0].cell_format.horizontal_merge = aw.CellMerge.FIRST
    table.rows[0].cells[1].cell_format.horizontal_merge = aw.CellMerge.PREVIOUS
    ```

2. विभाजित कोशिकाएँ: कोशिकाओं को उनके अलग-अलग घटकों में विभाजित करें।

    ```python
    cell.cell_format.horizontal_merge = aw.CellMerge.NONE
    ```

## तालिकाओं में बॉर्डर और छायांकन जोड़ना

बॉर्डर और छायांकन जोड़कर तालिका का स्वरूप बढ़ाएं:

1. बॉर्डर: तालिकाओं और कक्षों के लिए बॉर्डर अनुकूलित करें.

    ```python
    table.set_borders(0.5, aw.LineStyle.SINGLE, aw.Color.from_rgb(0, 0, 0))
    ```

2. छायांकन: दृश्य रूप से आकर्षक प्रभाव के लिए कोशिकाओं पर छायांकन लागू करें।

    ```python
    cell.cell_format.shading.background_pattern_color = aw.Color.from_rgb(230, 230, 230)
    ```

## सेल सामग्री और संरेखण के साथ कार्य करना

बेहतर पठनीयता के लिए सेल सामग्री और संरेखण को कुशलतापूर्वक प्रबंधित करें:

1. कक्ष सामग्री: कक्षों में सामग्री, जैसे पाठ और छवियाँ, डालें।

    ```python
    builder.insert_cell()
    builder.write("Hello, Aspose!")
    ```

2. पाठ संरेखण: सेल पाठ को आवश्यकतानुसार संरेखित करें।

    ```python
    cell.paragraphs[0].paragraph_format.alignment = aw.ParagraphAlignment.CENTER
    ```

## तालिका शीर्षलेख और पादलेख को संभालना

बेहतर संदर्भ के लिए अपनी तालिकाओं में शीर्षलेख और पादलेख शामिल करें:

1. तालिका शीर्षलेख: पहली पंक्ति को शीर्षलेख पंक्ति के रूप में सेट करें।

    ```python
    table.rows[0].row_format.is_header = True
    ```

2. तालिका पादलेख: अतिरिक्त जानकारी के लिए पादलेख पंक्ति बनाएँ

    ```python
    footer_row = table.append_row()
    footer_row.cells[0].cell_format.horizontal_merge = aw.CellMerge.NONE
    footer_row.cells[0].paragraphs[0].runs[0].text = "Total"
    ```
	
## तालिकाओं को विभिन्न प्रारूपों में निर्यात करना

एक बार आपकी तालिका तैयार हो जाए, तो आप इसे विभिन्न प्रारूपों में निर्यात कर सकते हैं, जैसे PDF या DOCX:

1. PDF के रूप में सहेजें: तालिका के साथ दस्तावेज़ को PDF फ़ाइल के रूप में सहेजें.

    ```python
    doc.save("table_document.pdf", aw.SaveFormat.PDF)
    ```

2. DOCX के रूप में सहेजें: दस्तावेज़ को DOCX फ़ाइल के रूप में सहेजें.

    ```python
    doc.save("table_document.docx", aw.SaveFormat.DOCX)
    ```
	
## निष्कर्ष

Aspose.Words for Python दस्तावेज़ तालिकाएँ बनाने, स्टाइल करने और फ़ॉर्मेट करने के लिए एक व्यापक टूलकिट प्रदान करता है। इस लेख में बताए गए चरणों का पालन करके, आप अपने दस्तावेज़ों में तालिकाओं को प्रभावी ढंग से प्रबंधित कर सकते हैं, उनकी उपस्थिति को अनुकूलित कर सकते हैं और उन्हें विभिन्न प्रारूपों में निर्यात कर सकते हैं। अपने दस्तावेज़ प्रस्तुतियों को बेहतर बनाने और अपने पाठकों को स्पष्ट, आकर्षक जानकारी प्रदान करने के लिए Aspose.Words की शक्ति का उपयोग करें।

## अक्सर पूछे जाने वाले प्रश्न

### मैं Python के लिए Aspose.Words कैसे स्थापित करूं?

Python के लिए Aspose.Words को स्थापित करने के लिए, निम्नलिखित कमांड का उपयोग करें: 

```bash
pip install aspose-words
```

### क्या मैं अपनी तालिकाओं पर कस्टम शैलियाँ लागू कर सकता हूँ?

हां, आप Aspose.Words का उपयोग करके फ़ॉन्ट, रंग और बॉर्डर जैसे विभिन्न गुणों को संशोधित करके अपनी तालिकाओं पर कस्टम शैलियाँ लागू कर सकते हैं।

### क्या किसी तालिका में कोशिकाओं को मर्ज करना संभव है?

 हां, आप किसी तालिका में कक्षों को मर्ज कर सकते हैं`CellMerge` Aspose.Words द्वारा प्रदान की गई संपत्ति.

### मैं अपनी तालिकाओं को विभिन्न प्रारूपों में कैसे निर्यात करूं?

 आप अपनी तालिकाओं को PDF या DOCX जैसे विभिन्न प्रारूपों में निर्यात कर सकते हैं`save` विधि और वांछित प्रारूप निर्दिष्ट करना।

### मैं Python के लिए Aspose.Words के बारे में और अधिक कहां से सीख सकता हूं?

 विस्तृत दस्तावेज़ीकरण और संदर्भ के लिए, यहां जाएं[पायथन API संदर्भ के लिए Aspose.Words](https://reference.aspose.com/words/python-net/).

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
