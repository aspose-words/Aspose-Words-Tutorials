---
"description": "Aspose.Words for Java में OLE ऑब्जेक्ट और ActiveX नियंत्रण का उपयोग करना सीखें। आसानी से इंटरैक्टिव दस्तावेज़ बनाएँ। अभी शुरू करें!"
"linktitle": "OLE ऑब्जेक्ट्स और ActiveX नियंत्रणों का उपयोग करना"
"second_title": "Aspose.Words जावा दस्तावेज़ प्रसंस्करण एपीआई"
"title": "जावा के लिए Aspose.Words में OLE ऑब्जेक्ट्स और ActiveX नियंत्रणों का उपयोग करना"
"url": "/hi/java/using-document-elements/using-ole-objects-and-activex/"
"weight": 21
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# जावा के लिए Aspose.Words में OLE ऑब्जेक्ट्स और ActiveX नियंत्रणों का उपयोग करना

इस ट्यूटोरियल में, हम Aspose.Words for Java में OLE (ऑब्जेक्ट लिंकिंग और एम्बेडिंग) ऑब्जेक्ट्स और ActiveX कंट्रोल्स के साथ काम करने का तरीका जानेंगे। OLE ऑब्जेक्ट्स और ActiveX कंट्रोल्स शक्तिशाली उपकरण हैं जो आपको स्प्रेडशीट, मल्टीमीडिया फ़ाइलें या इंटरैक्टिव कंट्रोल्स जैसी बाहरी सामग्री को एम्बेड या लिंक करके अपने दस्तावेज़ों को बेहतर बनाने की अनुमति देते हैं। कोड उदाहरणों में गहराई से जाने और इन सुविधाओं का प्रभावी ढंग से उपयोग करने का तरीका जानने के लिए हमारे साथ बने रहें।

### आवश्यक शर्तें

आरंभ करने से पहले, सुनिश्चित करें कि आपके पास निम्नलिखित पूर्वापेक्षाएँ मौजूद हैं:

1. Aspose.Words for Java : सुनिश्चित करें कि आपके Java प्रोजेक्ट में Aspose.Words लाइब्रेरी स्थापित है। आप इसे यहाँ से डाउनलोड कर सकते हैं [यहाँ](https://releases.aspose.com/words/java/).

2. जावा विकास वातावरण: आपके सिस्टम पर एक कार्यशील जावा विकास वातावरण स्थापित होना चाहिए।

### OLE ऑब्जेक्ट सम्मिलित करना

आइए एक Word दस्तावेज़ में OLE ऑब्जेक्ट डालने से शुरू करें। हम एक सरल Word दस्तावेज़ बनाएंगे और फिर एक वेब पेज का प्रतिनिधित्व करने वाला OLE ऑब्जेक्ट डालेंगे।

```java
string outPath = "Your Output Directory";
public void insertOleObject() throws Exception
{
    Document doc = new Document();
    DocumentBuilder builder = new DocumentBuilder(doc);
    builder.insertOleObject("http://www.aspose.com", "htmlfile", सच, सच, शून्य);
    doc.save("Your Directory Path" + "WorkingWithOleObjectsAndActiveX.InsertOleObject.docx");
}
```

इस कोड में, हम एक नया दस्तावेज़ बनाते हैं और एक OLE ऑब्जेक्ट डालते हैं जो Aspose वेबसाइट प्रदर्शित करता है। आप URL को वांछित सामग्री से बदल सकते हैं।

### OlePackage के साथ OLE ऑब्जेक्ट सम्मिलित करना

आगे, आइए जानें कि OlePackage का उपयोग करके OLE ऑब्जेक्ट कैसे डालें। यह आपको अपने दस्तावेज़ में बाहरी फ़ाइलों को OLE ऑब्जेक्ट के रूप में एम्बेड करने की अनुमति देता है।

```java
@Test
public void insertOleObjectWithOlePackage() throws Exception
{
    Document doc = new Document();
    DocumentBuilder builder = new DocumentBuilder(doc);
    byte[] bs = FileUtils.readFileToByteArray(new File("Your Directory Path" + "Zip file.zip"));
    try (ByteArrayInputStream stream = new ByteArrayInputStream(bs))
    {
        Shape shape = builder.insertOleObject(stream, "Package", true, null);
        OlePackage olePackage = shape.getOleFormat().getOlePackage();
        olePackage.setFileName("filename.zip");
        olePackage.setDisplayName("displayname.zip");
        doc.save(outPath + "WorkingWithOleObjectsAndActiveX.InsertOleObjectWithOlePackage.docx");
    }
}
```

इस उदाहरण में, हम OlePackage का उपयोग करके एक OLE ऑब्जेक्ट सम्मिलित करते हैं, जिससे आप बाहरी फ़ाइलों को एम्बेडेड ऑब्जेक्ट के रूप में शामिल कर सकते हैं।

### OLE ऑब्जेक्ट को आइकन के रूप में सम्मिलित करना

अब, आइए देखें कि किसी OLE ऑब्जेक्ट को आइकन के रूप में कैसे डाला जाता है। यह तब उपयोगी होता है जब आप किसी एम्बेडेड फ़ाइल का प्रतिनिधित्व करने वाला आइकन प्रदर्शित करना चाहते हैं।

```java
@Test
public void insertOleObjectAsIcon() throws Exception
{
    Document doc = new Document();
    DocumentBuilder builder = new DocumentBuilder(doc);
    builder.insertOleObjectAsIcon("Your Directory Path" + "Presentation.pptx", false, getImagesDir() + "Logo icon.ico", "My embedded file");
    doc.save(outPath + "WorkingWithOleObjectsAndActiveX.InsertOleObjectAsIcon.docx");
}
```

इस कोड में, हम एक OLE ऑब्जेक्ट को एक आइकन के रूप में सम्मिलित करते हैं, जो एम्बेडेड सामग्री का अधिक आकर्षक दृश्य प्रतिनिधित्व प्रदान करता है।

### ActiveX नियंत्रण गुण पढ़ना

अब, आइए अपना ध्यान ActiveX नियंत्रणों पर केंद्रित करें। हम सीखेंगे कि Word दस्तावेज़ में ActiveX नियंत्रणों के गुणों को कैसे पढ़ा जाए।

```java
@Test
public void readActiveXControlProperties() throws Exception
{
    Document doc = new Document("Your Directory Path" + "ActiveX controls.docx");
    String properties = "";
    for (Shape shape : (Iterable<Shape>) doc.getChildNodes(NodeType.SHAPE, true))
    {
        if (shape.getOleFormat() == null) break;
        OleControl oleControl = shape.getOleFormat().getOleControl();
        if (oleControl.isForms2OleControl())
        {
            Forms2OleControl checkBox = (Forms2OleControl) oleControl;
            properties = properties + "\nCaption: " + checkBox.getCaption();
            properties = properties + "\nValue: " + checkBox.getValue();
            properties = properties + "\nEnabled: " + checkBox.getEnabled();
            properties = properties + "\nType: " + checkBox.getType();
            if (checkBox.getChildNodes() != null)
            {
                properties = properties + "\nChildNodes: " + checkBox.getChildNodes();
            }
            properties += "\n";
        }
    }
    properties = properties + "\nTotal ActiveX Controls found: " + doc.getChildNodes(NodeType.SHAPE, true).getCount();
    System.out.println("\n" + properties);
}
```

इस कोड में, हम Word दस्तावेज़ में आकृतियों को दोहराते हैं, ActiveX नियंत्रणों की पहचान करते हैं, और उनके गुणों को पुनः प्राप्त करते हैं।

### निष्कर्ष

बधाई हो! आपने Aspose.Words for Java में OLE ऑब्जेक्ट्स और ActiveX नियंत्रणों के साथ काम करना सीख लिया है। ये सुविधाएँ गतिशील और इंटरैक्टिव दस्तावेज़ बनाने के लिए संभावनाओं की दुनिया खोलती हैं।

### पूछे जाने वाले प्रश्न

### वर्ड दस्तावेज़ में OLE ऑब्जेक्ट्स का उद्देश्य क्या है? 
   - OLE ऑब्जेक्ट्स आपको किसी Word दस्तावेज़ में बाह्य सामग्री, जैसे फ़ाइलें या वेब पेज, को एम्बेड या लिंक करने की अनुमति देते हैं।

### क्या मैं अपने दस्तावेज़ में OLE ऑब्जेक्ट्स के स्वरूप को अनुकूलित कर सकता हूँ? 
   - हां, आप आइकन और फ़ाइल नाम सेट करने सहित OLE ऑब्जेक्ट्स की उपस्थिति को अनुकूलित कर सकते हैं।

### ActiveX नियंत्रण क्या हैं, और वे मेरे दस्तावेज़ों को कैसे बेहतर बना सकते हैं? 
   - ActiveX नियंत्रण इंटरैक्टिव तत्व हैं जो आपके Word दस्तावेज़ों में कार्यक्षमता जोड़ सकते हैं, जैसे प्रपत्र नियंत्रण या मल्टीमीडिया प्लेयर।

### क्या Aspose.Words for Java एंटरप्राइज़-स्तरीय दस्तावेज़ स्वचालन के लिए उपयुक्त है? 
   - हां, Java के लिए Aspose.Words, Java अनुप्रयोगों में दस्तावेज़ निर्माण और हेरफेर को स्वचालित करने के लिए एक शक्तिशाली लाइब्रेरी है।

### मैं Java के लिए Aspose.Words तक पहुंच कहां से प्राप्त कर सकता हूं? 
   - आप Java के लिए Aspose.Words को यहां से डाउनलोड कर सकते हैं [यहाँ](https://releases.aspose.com/words/java/).

आज ही Aspose.Words for Java के साथ शुरुआत करें और दस्तावेज़ स्वचालन और अनुकूलन की पूरी क्षमता को अनलॉक करें!



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}