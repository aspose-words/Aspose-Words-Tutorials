---
title: दस्तावेज़ सौंदर्य के लिए वॉटरमार्क बनाना और प्रारूपित करना
linktitle: दस्तावेज़ सौंदर्य के लिए वॉटरमार्क बनाना और प्रारूपित करना
second_title: Aspose.Words पायथन दस्तावेज़ प्रबंधन API
description: पायथन के लिए Aspose.Words का उपयोग करके दस्तावेज़ों में वॉटरमार्क बनाना और फ़ॉर्मेट करना सीखें। टेक्स्ट और इमेज वॉटरमार्क जोड़ने के लिए स्रोत कोड के साथ चरण-दर-चरण मार्गदर्शिका। इस ट्यूटोरियल के साथ अपने दस्तावेज़ की खूबसूरती बढ़ाएँ।
weight: 10
url: /hi/python-net/tables-and-formatting/manage-document-watermarks/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# दस्तावेज़ सौंदर्य के लिए वॉटरमार्क बनाना और प्रारूपित करना


वॉटरमार्क दस्तावेजों में एक सूक्ष्म लेकिन प्रभावशाली तत्व के रूप में काम करते हैं, जो व्यावसायिकता और सौंदर्यशास्त्र की एक परत जोड़ते हैं। Aspose.Words for Python के साथ, आप अपने दस्तावेज़ों की दृश्य अपील को बढ़ाने के लिए आसानी से वॉटरमार्क बना और प्रारूपित कर सकते हैं। यह ट्यूटोरियल आपको Aspose.Words for Python API का उपयोग करके अपने दस्तावेज़ों में वॉटरमार्क जोड़ने की चरण-दर-चरण प्रक्रिया के माध्यम से मार्गदर्शन करेगा।

## दस्तावेज़ों में वॉटरमार्क का परिचय

वॉटरमार्क ऐसे डिज़ाइन तत्व हैं जिन्हें दस्तावेज़ों की पृष्ठभूमि में रखा जाता है ताकि मुख्य सामग्री को बाधित किए बिना अतिरिक्त जानकारी या ब्रांडिंग दी जा सके। दस्तावेज़ की अखंडता बनाए रखने और दृश्य अपील को बढ़ाने के लिए इनका उपयोग आमतौर पर व्यावसायिक दस्तावेज़ों, कानूनी कागजात और रचनात्मक कार्यों में किया जाता है।

## पायथन के लिए Aspose.Words के साथ आरंभ करना

 शुरू करने के लिए, सुनिश्चित करें कि आपके पास Python के लिए Aspose.Words इंस्टॉल है। आप इसे Aspose रिलीज़ से डाउनलोड कर सकते हैं:[पायथन के लिए Aspose.Words डाउनलोड करें](https://releases.aspose.com/words/python/).

स्थापना के बाद, आप आवश्यक मॉड्यूल आयात कर सकते हैं और दस्तावेज़ ऑब्जेक्ट सेट कर सकते हैं।

```python
import aspose.words as aw

# Load or create a document
doc = aw.Document()

# Your code continues here
```

## टेक्स्ट वॉटरमार्क जोड़ना

टेक्स्ट वॉटरमार्क जोड़ने के लिए, इन चरणों का पालन करें:

1. वॉटरमार्क ऑब्जेक्ट बनाएं.
2. वॉटरमार्क के लिए पाठ निर्दिष्ट करें.
3. दस्तावेज़ में वॉटरमार्क जोड़ें.

```python
# Create a watermark object
watermark = aw.drawing.Watermark()

# Set text for the watermark
watermark.text = "Confidential"

# Add the watermark to the document
doc.watermark = watermark
```

## टेक्स्ट वॉटरमार्क उपस्थिति को अनुकूलित करना

आप विभिन्न गुणों को समायोजित करके टेक्स्ट वॉटरमार्क के स्वरूप को अनुकूलित कर सकते हैं:

```python
# Customize text watermark appearance
watermark.font.size = 36
watermark.font.bold = True
watermark.color = aw.drawing.Color.GRAY
```

## छवि वॉटरमार्क जोड़ना

छवि वॉटरमार्क जोड़ने में भी ऐसी ही प्रक्रिया शामिल है:

1. वॉटरमार्क के लिए छवि लोड करें.
2. एक छवि वॉटरमार्क ऑब्जेक्ट बनाएँ.
3. दस्तावेज़ में छवि वॉटरमार्क जोड़ें.

```python
# Load the image for the watermark
image_path = "path/to/watermark.png"
watermark_image = aw.drawing.Image(image_path)

# Create an image watermark object
image_watermark = aw.drawing.ImageWatermark(watermark_image)

# Add the image watermark to the document
doc.watermark = image_watermark
```

## छवि वॉटरमार्क गुण समायोजित करना

आप छवि वॉटरमार्क का आकार और स्थिति नियंत्रित कर सकते हैं:

```python
# Adjust image watermark properties
image_watermark.size = aw.drawing.SizeF(200, 100)
image_watermark.relative_horizontal_position = aw.drawing.RelativeHorizontalPosition.CENTER
image_watermark.relative_vertical_position = aw.drawing.RelativeVerticalPosition.MIDDLE
```

## दस्तावेज़ के विशिष्ट अनुभागों पर वॉटरमार्क लगाना

यदि आप दस्तावेज़ के विशिष्ट अनुभागों पर वॉटरमार्क लागू करना चाहते हैं, तो आप निम्नलिखित तरीका अपना सकते हैं:

```python
# Apply watermark to a specific section
section = doc.sections[0]
section.watermark = watermark
```

## पारदर्शी वॉटरमार्क बनाना

पारदर्शी वॉटरमार्क बनाने के लिए, पारदर्शिता स्तर समायोजित करें:

```python
# Create a transparent watermark
watermark.transparency = 0.5  # Range: 0 (opaque) to 1 (fully transparent)
```

## वॉटरमार्क के साथ दस्तावेज़ को सहेजना

एक बार वॉटरमार्क जोड़ लेने के बाद, दस्तावेज़ को लागू वॉटरमार्क के साथ सहेजें:

```python
# Save the document with watermarks
output_path = "path/to/output/document_with_watermark.docx"
doc.save(output_path)
```

## निष्कर्ष

Aspose.Words for Python का उपयोग करके अपने दस्तावेज़ों में वॉटरमार्क जोड़ना एक सीधी प्रक्रिया है जो आपकी सामग्री की दृश्य अपील और ब्रांडिंग को बढ़ाती है। चाहे वह टेक्स्ट हो या इमेज वॉटरमार्क, आपके पास अपनी पसंद के अनुसार उनकी उपस्थिति और प्लेसमेंट को अनुकूलित करने की सुविधा है।

## पूछे जाने वाले प्रश्न

### मैं किसी दस्तावेज़ से वॉटरमार्क कैसे हटा सकता हूँ?

 वॉटरमार्क हटाने के लिए, दस्तावेज़ के वॉटरमार्क गुण को इस पर सेट करें`None`.

### क्या मैं अलग-अलग पृष्ठों पर अलग-अलग वॉटरमार्क लगा सकता हूँ?

हां, आप किसी दस्तावेज़ के विभिन्न अनुभागों या पृष्ठों पर अलग-अलग वॉटरमार्क लागू कर सकते हैं।

### क्या घुमाए गए टेक्स्ट वॉटरमार्क का उपयोग करना संभव है?

बिल्कुल! आप रोटेशन एंगल प्रॉपर्टी सेट करके टेक्स्ट वॉटरमार्क को घुमा सकते हैं।

### क्या मैं वॉटरमार्क को संपादित या हटाए जाने से बचा सकता हूँ?

यद्यपि वॉटरमार्क को पूरी तरह से संरक्षित नहीं किया जा सकता, फिर भी आप उनकी पारदर्शिता और स्थान को समायोजित करके उन्हें छेड़छाड़ के प्रति अधिक प्रतिरोधी बना सकते हैं।

### क्या Aspose.Words for Python विंडोज और लिनक्स दोनों के लिए उपयुक्त है?

हां, Python के लिए Aspose.Words विंडोज और लिनक्स दोनों वातावरणों के साथ संगत है।

 अधिक जानकारी और व्यापक API संदर्भों के लिए, Aspose.Words दस्तावेज़ देखें:[पायथन API संदर्भ के लिए Aspose.Words](https://reference.aspose.com/words/python-net/)
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
