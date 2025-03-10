---
title: वर्ड दस्तावेज़ों में हेडर और फ़ुटर में हेरफेर करना
linktitle: वर्ड दस्तावेज़ों में हेडर और फ़ुटर में हेरफेर करना
second_title: Aspose.Words पायथन दस्तावेज़ प्रबंधन API
description: पायथन के लिए Aspose.Words का उपयोग करके Word दस्तावेज़ों में हेडर और फ़ुटर को बदलना सीखें। कस्टमाइज़ करने, जोड़ने, हटाने और बहुत कुछ के लिए स्रोत कोड के साथ चरण-दर-चरण मार्गदर्शिका। अपने दस्तावेज़ स्वरूपण को अभी बेहतर बनाएँ!
weight: 16
url: /hi/python-net/document-structure-and-content-manipulation/document-headers-footers/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# वर्ड दस्तावेज़ों में हेडर और फ़ुटर में हेरफेर करना

Word दस्तावेज़ों में हेडर और फ़ुटर आपके कंटेंट को संदर्भ, ब्रांडिंग और अतिरिक्त जानकारी प्रदान करने में महत्वपूर्ण भूमिका निभाते हैं। Aspose.Words for Python API का उपयोग करके इन तत्वों में हेरफेर करने से आपके दस्तावेज़ों की उपस्थिति और कार्यक्षमता में उल्लेखनीय वृद्धि हो सकती है। इस चरण-दर-चरण मार्गदर्शिका में, हम Aspose.Words for Python का उपयोग करके हेडर और फ़ुटर के साथ काम करने का तरीका जानेंगे।


## पायथन के लिए Aspose.Words के साथ आरंभ करना

हेडर और फ़ुटर में हेरफेर करने से पहले, आपको Python के लिए Aspose.Words सेट अप करना होगा। इन चरणों का पालन करें:

1. स्थापना: pip का उपयोग करके Python के लिए Aspose.Words स्थापित करें।

```python
pip install aspose-words
```

2. मॉड्यूल आयात करना: अपनी पायथन स्क्रिप्ट में आवश्यक मॉड्यूल आयात करें।

```python
import aspose.words as aw
```

## एक सरल शीर्षलेख और पादलेख जोड़ना

अपने Word दस्तावेज़ में मूल शीर्षलेख और पादलेख जोड़ने के लिए, इन चरणों का पालन करें:

1. दस्तावेज़ बनाना: Aspose.Words का उपयोग करके एक नया Word दस्तावेज़ बनाएँ।

```python
doc = aw.Document()
```

2.  शीर्षलेख और पादलेख जोड़ना: का उपयोग करें`sections` दस्तावेज़ की प्रॉपर्टी का उपयोग करके अनुभागों तक पहुँचें। फिर, इसका उपयोग करें`headers_footers` शीर्षलेख और पादलेख जोड़ने के लिए संपत्ति।

```python
section = doc.sections[0]
header = section.headers_footers[aw.HeaderFooterType.HEADER_PRIMARY]
footer = section.headers_footers[aw.HeaderFooterType.FOOTER_PRIMARY]
```

3. दस्तावेज़ को सहेजना: दस्तावेज़ को शीर्षलेख और पादलेख के साथ सहेजें।

```python
doc.save("document_with_header_footer.docx")
```

## शीर्षलेख और पादलेख सामग्री को अनुकूलित करना

आप चित्र, तालिकाएँ और गतिशील फ़ील्ड जोड़कर हेडर और फ़ुटर सामग्री को कस्टमाइज़ कर सकते हैं। उदाहरण के लिए:

1. छवियाँ जोड़ना: शीर्षलेख या पादलेख में छवियाँ डालें।

```python
image_path = "path_to_your_image.png"
header_run.add_picture(image_path)
```

2. गतिशील फ़ील्ड: स्वचालित डेटा प्रविष्टि के लिए गतिशील फ़ील्ड का उपयोग करें।

```python
footer_run.text = "Page number: {PAGE} of {NUMPAGES} - Document created on {DATE}"
```

## विषम और सम पृष्ठों के लिए अलग-अलग शीर्षलेख और पादलेख

विषम और सम पृष्ठों के लिए अलग-अलग हेडर और फ़ुटर बनाना आपके दस्तावेज़ों में एक पेशेवर स्पर्श जोड़ सकता है। यहाँ बताया गया है कि कैसे:

1. विषम और सम पृष्ठ लेआउट सेट करना: विषम और सम पृष्ठों के लिए अलग-अलग शीर्षलेख और पादलेख की अनुमति देने के लिए लेआउट को परिभाषित करें।

```python
section = doc.sections[0]
section.page_setup.different_first_page_header_footer = True
section.page_setup.odd_and_even_pages_header_footer = True
```

2. शीर्षलेख और पादलेख जोड़ना: प्रथम पृष्ठ, विषम पृष्ठों और सम पृष्ठों के लिए शीर्षलेख और पादलेख जोड़ें।

```python
header_first = section.headers_footers[aspose.words.HeaderFooterType.HEADER_FIRST]
footer_first = section.headers_footers[aspose.words.HeaderFooterType.FOOTER_FIRST]
header_odd = section.headers_footers[aspose.words.HeaderFooterType.HEADER_EVEN]
footer_odd = section.headers_footers[aspose.words.HeaderFooterType.FOOTER_EVEN]
header_even = section.headers_footers[aspose.words.HeaderFooterType.HEADER_ODD]
footer_even = section.headers_footers[aspose.words.HeaderFooterType.FOOTER_ODD]
```

## हेडर और फ़ुटर हटाना

किसी Word दस्तावेज़ से शीर्षलेख और पादलेख हटाने के लिए:

1. शीर्षलेख और पादलेख हटाना: शीर्षलेख और पादलेख की सामग्री साफ़ करें।

```python
header.clear_content()
footer.clear_content()
```

2. विभिन्न शीर्षलेख/पादलेख अक्षम करना: यदि आवश्यक हो तो विषम और सम पृष्ठों के लिए विभिन्न शीर्षलेख और पादलेख अक्षम करें।

```python
section.page_setup.different_first_page_header_footer = False
section.page_setup.odd_and_even_pages_header_footer = False
```

## अक्सर पूछे जाने वाले प्रश्न

### मैं हेडर और फ़ुटर सामग्री तक कैसे पहुँच सकता हूँ?

 शीर्षलेख और पादलेख सामग्री तक पहुंचने के लिए, का उपयोग करें`headers_footers` दस्तावेज़ के अनुभाग की संपत्ति.

### क्या मैं हेडर और फ़ुटर में छवियाँ जोड़ सकता हूँ?

 हां, आप हेडर और फ़ुटर में चित्र जोड़ सकते हैं`add_picture` तरीका।

### क्या विषम और सम पृष्ठों के लिए अलग-अलग शीर्षक रखना संभव है?

बिल्कुल, आप उपयुक्त सेटिंग्स सक्षम करके विषम और सम पृष्ठों के लिए अलग-अलग शीर्षलेख और पादलेख बना सकते हैं।

### क्या मैं विशिष्ट पृष्ठों से शीर्षलेख और पादलेख हटा सकता हूँ?

हां, आप हेडर और फुटर की सामग्री को प्रभावी ढंग से हटाने के लिए उसे साफ़ कर सकते हैं।

### मैं Python के लिए Aspose.Words के बारे में और अधिक कहां से सीख सकता हूं?

 अधिक विस्तृत दस्तावेज़ीकरण और उदाहरणों के लिए, यहां जाएं[पायथन API संदर्भ के लिए Aspose.Words](https://reference.aspose.com/words/python-net/).

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
