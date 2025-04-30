---
"description": "Java के लिए Aspose.Words का उपयोग करके दस्तावेज़ों को प्रिंट करना सीखें। अपने Java अनुप्रयोगों में निर्बाध प्रिंटिंग के लिए चरण-दर-चरण मार्गदर्शिका।"
"linktitle": "दस्तावेज़ मुद्रण"
"second_title": "Aspose.Words जावा दस्तावेज़ प्रसंस्करण एपीआई"
"title": "Java के लिए Aspose.Words में दस्तावेज़ प्रिंट करना"
"url": "/hi/java/printing-documents/printing-documents/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Java के लिए Aspose.Words में दस्तावेज़ प्रिंट करना


यदि आप Aspose.Words for Java का उपयोग करके दस्तावेज़ प्रिंट करना चाहते हैं, तो आप सही जगह पर हैं। इस चरण-दर-चरण मार्गदर्शिका में, हम आपको दिए गए स्रोत कोड का उपयोग करके Aspose.Words for Java के साथ दस्तावेज़ प्रिंट करने की प्रक्रिया के बारे में बताएँगे।

## परिचय

कई अनुप्रयोगों में दस्तावेज़ों को प्रिंट करना एक सामान्य कार्य है। Java के लिए Aspose.Words Word दस्तावेज़ों के साथ काम करने के लिए एक शक्तिशाली API प्रदान करता है, जिसमें उन्हें प्रिंट करने की क्षमता भी शामिल है। इस ट्यूटोरियल में, हम आपको Word दस्तावेज़ को चरण दर चरण प्रिंट करने की प्रक्रिया के बारे में बताएँगे।

## अपना परिवेश स्थापित करना

इससे पहले कि हम कोड में उतरें, सुनिश्चित करें कि आपके पास निम्नलिखित पूर्वापेक्षाएँ मौजूद हैं:

- जावा डेवलपमेंट किट (JDK) स्थापित
- Aspose.Words for Java लाइब्रेरी डाउनलोड की गई और आपके प्रोजेक्ट में जोड़ी गई

## दस्तावेज़ लोड करना

आरंभ करने के लिए, आपको वह Word दस्तावेज़ लोड करना होगा जिसे आप प्रिंट करना चाहते हैं। `"Your Document Directory"` आपके दस्तावेज़ के पथ के साथ और `"Your Output Directory"` वांछित आउटपुट निर्देशिका के साथ.

```java
string dataDir = "Your Document Directory";
string outPath = "Your Output Directory";
Document doc = new Document(dataDir + "Rendering.docx");
```

## प्रिंट जॉब बनाना

इसके बाद, हम अपने लोड किए गए दस्तावेज़ को प्रिंट करने के लिए एक प्रिंट जॉब बनाएंगे। नीचे दिया गया कोड स्निपेट एक प्रिंट जॉब आरंभ करता है और वांछित प्रिंटर सेटिंग्स सेट करता है।

```java
// हमारे दस्तावेज़ को प्रिंट करने के लिए एक प्रिंट कार्य बनाएँ।
PrinterJob pj = PrinterJob.getPrinterJob();
// दस्तावेज़ में पृष्ठों की संख्या के साथ एक विशेषता सेट आरंभ करें।
PrintRequestAttributeSet attributes = new HashPrintRequestAttributeSet();
attributes.add(new PageRanges(1, doc.getPageCount()));
// प्रिंटर सेटिंग्स को अन्य पैरामीटरों के साथ प्रिंट दस्तावेज़ में पास करें।
MultipagePrintDocument awPrintDoc = new MultipagePrintDocument(doc, 4, true, attributes);
```

## दस्तावेज़ का मुद्रण

अब जब हमने अपना प्रिंट जॉब सेट कर लिया है, तो अब दस्तावेज़ को प्रिंट करने का समय आ गया है। निम्न कोड स्निपेट दस्तावेज़ को प्रिंट जॉब से जोड़ता है और प्रिंटिंग प्रक्रिया आरंभ करता है।

```java
// प्रिंट कार्य का उपयोग करके मुद्रित किए जाने वाले दस्तावेज़ को पास करें।
pj.setPrintable(awPrintDoc);
pj.print();
```
## संपूर्ण स्रोत कोड
```java
string dataDir = "Your Document Directory";
Document doc = new Document(dataDir + "Rendering.docx");
// हमारे दस्तावेज़ को प्रिंट करने के लिए एक प्रिंट कार्य बनाएँ।
PrinterJob pj = PrinterJob.getPrinterJob();
// दस्तावेज़ में पृष्ठों की संख्या के साथ एक विशेषता सेट आरंभ करें।
PrintRequestAttributeSet attributes = new HashPrintRequestAttributeSet();
attributes.add(new PageRanges(1, doc.getPageCount()));
// प्रिंटर सेटिंग्स को अन्य पैरामीटरों के साथ प्रिंट दस्तावेज़ में पास करें।
MultipagePrintDocument awPrintDoc = new MultipagePrintDocument(doc, 4, true, attributes);
// प्रिंट कार्य का उपयोग करके मुद्रित किए जाने वाले दस्तावेज़ को पास करें।
pj.setPrintable(awPrintDoc);
pj.print();
```
MultipagePrintDocument का स्रोत कोड
```java
class MultipagePrintDocument implements Printable
{
    private final Document mDocument;
    private final int mPagesPerSheet;
    private final boolean mPrintPageBorders;
    private final AttributeSet mAttributeSet;
    /// <सारांश>
    /// कस्टम PrintDocument वर्ग का निर्माता.
    /// </सारांश> 
    public MultipagePrintDocument(Document document, int pagesPerSheet, boolean printPageBorders,
                                  AttributeSet attributes) {
        if (document == null)
            throw new IllegalArgumentException("document");
        mDocument = document;
        mPagesPerSheet = pagesPerSheet;
        mPrintPageBorders = printPageBorders;
        mAttributeSet = attributes;
    }
    public int print(Graphics g, PageFormat pf, int page) {
        // विशेषता सेट में परिभाषित पृष्ठ प्रारंभ और समाप्ति सूचकांक।
        int[][] pageRanges = ((PageRanges) mAttributeSet.get(PageRanges.class)).getMembers();
        int fromPage = pageRanges[0][0] - 1;
        int toPage = pageRanges[0][1] - 1;
        Dimension thumbCount = getThumbCount(mPagesPerSheet, pf);
        // उस पृष्ठ अनुक्रमणिका की गणना करें जिसे आगे प्रस्तुत किया जाना है।
        int pagesOnCurrentSheet = (int) (page * (thumbCount.getWidth() * thumbCount.getHeight()));
        // यदि पृष्ठ अनुक्रमणिका कुल पृष्ठ श्रेणी से अधिक है तो कोई समस्या नहीं है
        // और अधिक प्रस्तुत करना है।
        if (pagesOnCurrentSheet > (toPage - fromPage))
            return Printable.NO_SUCH_PAGE;
        // प्रत्येक थम्बनेल प्लेसहोल्डर का आकार पॉइंट्स में परिकलित करें।
        Point2D.Float thumbSize = new Point2D.Float((float) (pf.getImageableWidth() / thumbCount.getWidth()),
                (float) (pf.getImageableHeight() / thumbCount.getHeight()));
        // इस कागज़ के पन्ने पर मुद्रित होने वाले पहले पृष्ठ की संख्या की गणना करें।
        int startPage = pagesOnCurrentSheet + fromPage;
        // इस कागज़ के शीट पर मुद्रित होने वाले अंतिम पृष्ठ की संख्या का चयन करें।
        int pageTo = Math.max(startPage + mPagesPerSheet - 1, toPage);
        // संग्रहीत वर्तमान पृष्ठ से परिकलित पृष्ठ तक चयनित पृष्ठों के माध्यम से लूप करें
        // अंतिम पृष्ठ.
        for (int pageIndex = startPage; pageIndex <= pageTo; pageIndex++) {
            // स्तंभ और पंक्ति सूचकांक की गणना करें.
            int rowIdx = (int) Math.floor((pageIndex - startPage) / thumbCount.getWidth());
            int columnIdx = (int) Math.floor((pageIndex - startPage) % thumbCount.getWidth());
            // विश्व निर्देशांक में थम्बनेल स्थान को परिभाषित करें (इस मामले में बिंदु)।
            float thumbLeft = columnIdx * thumbSize.x;
            float thumbTop = rowIdx * thumbSize.y;
            try {
                // बायीं और ऊपरी प्रारंभिक स्थिति की गणना करें।
                int leftPos = (int) (thumbLeft + pf.getImageableX());
                int topPos = (int) (thumbTop + pf.getImageableY());
                // गणना किए गए निर्देशांकों का उपयोग करके दस्तावेज़ पृष्ठ को ग्राफ़िक्स ऑब्जेक्ट में प्रस्तुत करें
                // और थंबनेल प्लेसहोल्डर आकार.
                // उपयोगी वापसी मान वह पैमाना है जिस पर पृष्ठ को प्रस्तुत किया गया था।
                float scale = mDocument.renderToSize(pageIndex, (Graphics2D) g, leftPos, topPos, (int) thumbSize.x,
                        (int) thumbSize.y);
                // पृष्ठ की सीमाएँ बनाएँ (पृष्ठ का थंबनेल, थंबनेल से छोटा हो सकता है)
                // प्लेसहोल्डर आकार).
                if (mPrintPageBorders) {
                    // पेज का वास्तविक 100% आकार पॉइंट्स में प्राप्त करें।
                    Point2D.Float pageSize = mDocument.getPageInfo(pageIndex).getSizeInPoints();
                    // ज्ञात स्केल फैक्टर का उपयोग करके स्केल किए गए पृष्ठ के चारों ओर बॉर्डर बनाएं।
                    g.setColor(Color.black);
                    g.drawRect(leftPos, topPos, (int) (pageSize.x * scale), (int) (pageSize.y * scale));
                    // थम्बनेल प्लेसहोल्डर के चारों ओर बॉर्डर बनाएं.
                    g.setColor(Color.red);
                    g.drawRect(leftPos, topPos, (int) thumbSize.x, (int) thumbSize.y);
                }
            } catch (Exception e) {
                // यदि रेंडरिंग के दौरान कोई त्रुटि हो तो कुछ न करें।
                // यदि रेंडरिंग के दौरान कोई त्रुटि होती है तो यह एक रिक्त पृष्ठ प्रदर्शित करेगा।
            }
        }
        return Printable.PAGE_EXISTS;
    }
    private Dimension getThumbCount(int pagesPerSheet, PageFormat pf) {
        Dimension size;
        // शीट पर कॉलम और पंक्तियों की संख्या निर्धारित करें
        // परिदृश्य-उन्मुख कागज.
        switch (pagesPerSheet) {
            case 16:
                size = new Dimension(4, 4);
                break;
            case 9:
                size = new Dimension(3, 3);
                break;
            case 8:
                size = new Dimension(4, 2);
                break;
            case 6:
                size = new Dimension(3, 2);
                break;
            case 4:
                size = new Dimension(2, 2);
                break;
            case 2:
                size = new Dimension(2, 1);
                break;
            default:
                size = new Dimension(1, 1);
                break;
        }
        // यदि कागज पोर्ट्रेट अभिविन्यास में है तो चौड़ाई और ऊंचाई को बदलें।
        if ((pf.getWidth() - pf.getImageableX()) < (pf.getHeight() - pf.getImageableY()))
            return new Dimension((int) size.getHeight(), (int) size.getWidth());
        return size;
	}
}
```

## निष्कर्ष

बधाई हो! आपने Aspose.Words for Java का उपयोग करके सफलतापूर्वक एक Word दस्तावेज़ प्रिंट किया है। यह चरण-दर-चरण मार्गदर्शिका आपको अपने Java अनुप्रयोगों में दस्तावेज़ प्रिंटिंग को सहजता से एकीकृत करने में मदद करेगी।

## पूछे जाने वाले प्रश्न

### प्रश्न 1: क्या मैं Java के लिए Aspose.Words का उपयोग करके किसी दस्तावेज़ के विशिष्ट पृष्ठों को प्रिंट कर सकता हूँ?

हां, आप दस्तावेज़ प्रिंट करते समय पृष्ठ सीमा निर्दिष्ट कर सकते हैं। कोड उदाहरण में, हमने उपयोग किया `attributes.add(new PageRanges(1, doc.getPageCount()))` सभी पेज प्रिंट करने के लिए। आप आवश्यकतानुसार पेज रेंज समायोजित कर सकते हैं।

### प्रश्न 2: क्या Aspose.Words for Java बैच प्रिंटिंग के लिए उपयुक्त है?

बिलकुल! जावा के लिए Aspose.Words बैच प्रिंटिंग कार्यों के लिए उपयुक्त है। आप दस्तावेजों की एक सूची के माध्यम से पुनरावृति कर सकते हैं और समान कोड का उपयोग करके उन्हें एक-एक करके प्रिंट कर सकते हैं।

### प्रश्न 3: मैं मुद्रण त्रुटियों या अपवादों को कैसे संभाल सकता हूँ?

आपको मुद्रण प्रक्रिया के दौरान होने वाले किसी भी संभावित अपवाद को संभालना चाहिए। अपवादों को संभालने के बारे में जानकारी के लिए Aspose.Words for Java दस्तावेज़ देखें।

### प्रश्न 4: क्या मैं प्रिंट सेटिंग को और अधिक अनुकूलित कर सकता हूँ?

हां, आप अपनी विशिष्ट आवश्यकताओं को पूरा करने के लिए प्रिंट सेटिंग को कस्टमाइज़ कर सकते हैं। उपलब्ध प्रिंट विकल्पों के बारे में अधिक जानने के लिए Aspose.Words for Java दस्तावेज़ देखें।

### प्रश्न 5: मैं Aspose.Words for Java के लिए अधिक सहायता और समर्थन कहां से प्राप्त कर सकता हूं?

अतिरिक्त समर्थन और सहायता के लिए, आप यहां जा सकते हैं [Aspose.Words जावा मंच के लिए](https://forum.aspose.com/).

---

अब जब आपने सफलतापूर्वक सीख लिया है कि Aspose.Words for Java का उपयोग करके दस्तावेज़ों को कैसे प्रिंट किया जाए, तो आप अपने Java अनुप्रयोगों में इस कार्यक्षमता को लागू करना शुरू कर सकते हैं। हैप्पी कोडिंग!


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}