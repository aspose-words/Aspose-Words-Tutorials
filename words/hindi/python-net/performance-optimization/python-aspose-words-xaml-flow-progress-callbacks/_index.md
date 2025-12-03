{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}
---
"date": "2025-03-29"
"description": "जानें कि XAML फ़्लो फ़ॉर्मेट और प्रोग्रेस कॉलबैक का उपयोग करके Python के लिए Aspose.Words के साथ दस्तावेज़ सहेजने का अनुकूलन कैसे करें। दस्तावेज़ों के प्रबंधन में दक्षता बढ़ाएँ।"
"title": "पायथन के Aspose.Words XAML प्रवाह और प्रगति कॉलबैक में दस्तावेज़ सहेजने का अनुकूलन"
"url": "/hi/python-net/performance-optimization/python-aspose-words-xaml-flow-progress-callbacks/"
"weight": 1
---

# Aspose.Words का उपयोग करके पायथन में दस्तावेज़ सहेजने का अनुकूलन कैसे करें: XAML प्रवाह और प्रगति कॉलबैक

## परिचय

क्या आप Python का उपयोग करके दस्तावेज़ रूपांतरणों को कुशलतापूर्वक प्रबंधित करना चाहते हैं? दस्तावेज़ सहेजने के दौरान छवियों को संभालने और प्रगति को ट्रैक करने में संघर्ष कर रहे हैं? यह ट्यूटोरियल आपको Python के लिए Aspose.Words के साथ दस्तावेज़ सहेजने के अनुकूलन के बारे में मार्गदर्शन करता है, जिसमें दो शक्तिशाली विशेषताओं पर ध्यान केंद्रित किया गया है: `XamlFlowSaveOptions` छवि फ़ोल्डर और दस्तावेज़ सहेजने की प्रगति कॉलबैक के साथ।

यह व्यापक मार्गदर्शिका उन डेवलपर्स के लिए एकदम सही है जो Aspose.Words लाइब्रेरी का उपयोग करके अपने दस्तावेज़ प्रसंस्करण वर्कफ़्लो को बढ़ाना चाहते हैं।

**आप क्या सीखेंगे:**
- छवि संसाधनों का प्रबंधन करते हुए दस्तावेज़ को XAML प्रवाह प्रारूप में कैसे सहेजें।
- लंबे परिचालन को रोकने के लिए दस्तावेज़ सहेजने के दौरान प्रगति कॉलबैक को कार्यान्वित करना।
- अपने विकास परिवेश में Python के लिए Aspose.Words को सेट अप और कॉन्फ़िगर करना।
- दस्तावेज़ प्रबंधन प्रणालियों में इन सुविधाओं का वास्तविक अनुप्रयोग।

आइए कोडिंग शुरू करने से पहले आवश्यक शर्तों पर गौर करें!

## आवश्यक शर्तें

आरंभ करने से पहले, सुनिश्चित करें कि आपके पास निम्नलिखित हैं:

### आवश्यक लाइब्रेरी और संस्करण
- **पायथन के लिए Aspose.Words**सुनिश्चित करें कि आपके पास संस्करण 23.3 या बाद का संस्करण है।
- **पायथन**: संस्करण 3.6 या उच्चतर अनुशंसित है।

### पर्यावरण सेटअप आवश्यकताएँ
- VSCode या PyCharm जैसा कोड संपादक.
- पायथन प्रोग्रामिंग का बुनियादी ज्ञान.

### ज्ञान पूर्वापेक्षाएँ
- दस्तावेज़ प्रसंस्करण अवधारणाओं से परिचित होना।
- पायथन में फ़ाइल हैंडलिंग और निर्देशिका प्रबंधन की समझ।

## पायथन के लिए Aspose.Words सेट अप करना

Aspose.Words का उपयोग शुरू करने के लिए, आपको इसे pip के माध्यम से इंस्टॉल करना होगा। अपना टर्मिनल या कमांड प्रॉम्प्ट खोलें और चलाएँ:

```bash
pip install aspose-words
```

### लाइसेंस प्राप्ति चरण
1. **मुफ्त परीक्षण**: अस्थायी लाइसेंस तक पहुंचें [यहाँ](https://purchase.aspose.com/temporary-license/) परीक्षण प्रयोजनों के लिए.
2. **खरीदना**: दीर्घकालिक उपयोग के लिए, लाइसेंस खरीदें [यहाँ](https://purchase.aspose.com/buy).
3. **बुनियादी आरंभीकरण और सेटअप**:
   - अपना दस्तावेज़ लोड करें `aw.Document()`.
   - आवश्यकतानुसार सहेजने के विकल्प कॉन्फ़िगर करें.

## कार्यान्वयन मार्गदर्शिका

यह अनुभाग आपको इस ट्यूटोरियल की दो मुख्य विशेषताओं को लागू करने में मदद करेगा: इमेज फ़ोल्डर के साथ XamlFlowSaveOptions, और डॉक्यूमेंट सेविंग प्रोग्रेस कॉलबैक।

### सुविधा 1: छवि फ़ोल्डर के साथ XamlFlowSaveOptions

#### अवलोकन
यह सुविधा आपको छवि फ़ोल्डर और उपनाम निर्दिष्ट करते समय दस्तावेज़ को XAML प्रवाह प्रारूप में सहेजने की अनुमति देती है। यह एम्बेडेड छवियों के साथ बड़े दस्तावेज़ों को कुशलतापूर्वक प्रबंधित करने के लिए आदर्श है।

#### कार्यान्वयन चरण

##### चरण 1: आवश्यक लाइब्रेरीज़ आयात करें
```python
import os
from datetime import datetime
import aspose.words as aw
```

##### चरण 2: ImageUriPrinter कॉलबैक क्लास को परिभाषित करें
यह वर्ग रूपांतरण के दौरान छवि स्ट्रीम की गणना करता है और उन्हें निर्दिष्ट उपनाम फ़ोल्डर में पुनर्निर्देशित करता है।

```python
class ExXamlFlowSaveOptionsImageFolder:
    class ImageUriPrinter(aw.saving.IImageSavingCallback):
        """Counts and prints filenames of images while their parent document is converted to flow-form .xaml."""
        
        def __init__(self, images_folder_alias: str):
            self.images_folder_alias = images_folder_alias
            self.resources = []  # प्रकार: सूची[स्ट्र]

        def image_saving(self, args: aw.saving.ImageSavingArgs):
            self.resources.append(args.image_file_name)
            with open(f"{self.images_folder_alias}/{args.image_file_name}", "wb") as image_stream:
                args.image_stream = image_stream
            args.keep_image_stream_open = False

    def test_image_folder(self):
        YOUR_DOCUMENT_DIRECTORY = 'YOUR_DOCUMENT_DIRECTORY'
        YOUR_OUTPUT_DIRECTORY = 'YOUR_OUTPUT_DIRECTORY'

        doc = aw.Document(f"{YOUR_DOCUMENT_DIRECTORY}/Rendering.docx")
        callback = self.ImageUriPrinter(YOUR_OUTPUT_DIRECTORY + "XamlFlowImageFolderAlias")

        options = aw.saving.XamlFlowSaveOptions()
        options.images_folder = YOUR_OUTPUT_DIRECTORY + "XamlFlowImageFolder"
        options.images_folder_alias = YOUR_OUTPUT_DIRECTORY + "XamlFlowImageFolderAlias"
        options.image_saving_callback = callback

        os.makedirs(options.images_folder_alias, exist_ok=True)
        
        doc.save(f"{YOUR_OUTPUT_DIRECTORY}/XamlFlowSaveOptions.image_folder.xaml", options)

        for resource in callback.resources:
            print(f"{callback.images_folder_alias}/{resource}")
```
**मुख्य कॉन्फ़िगरेशन विकल्प:**
- `images_folder`: वह निर्देशिका निर्दिष्ट करता है जहाँ छवियाँ सहेजी जाती हैं।
- `images_folder_alias`: दस्तावेज़ रूपांतरण के दौरान उपयोग किए जाने वाले उपनाम पथ को सेट करता है।

##### समस्या निवारण युक्तियों
- फ़ाइल नहीं मिली त्रुटि से बचने के लिए कोड चलाने से पहले सुनिश्चित करें कि सभी निर्देशिकाएं मौजूद हैं।
- अपनी आउटपुट निर्देशिका में लेखन अनुमतियों की जाँच करें।

### सुविधा 2: दस्तावेज़ सहेजने की प्रगति कॉलबैक

#### अवलोकन
यह सुविधा प्रगति कॉलबैक का उपयोग करके बचत प्रक्रिया का प्रबंधन करती है, जिससे आप लंबे समय से चल रहे बचत कार्यों को रद्द कर सकते हैं।

#### कार्यान्वयन चरण

##### चरण 1: SavingProgressCallback क्लास को परिभाषित करें
यह वर्ग दस्तावेज़-सहेजने की अवधि पर नज़र रखता है और यदि यह निर्दिष्ट समय सीमा से अधिक हो जाती है तो उसे रद्द कर देता है।

```python
class ExXamlFlowSaveOptionsProgressCallback:
    class SavingProgressCallback(aw.saving.IDocumentSavingCallback):
        """Saving progress callback. Cancel document saving after the 'max_duration' seconds."""
        
        def __init__(self):
            self.saving_started_at = datetime.now()
            self.max_duration = 0.01  # अधिकतम स्वीकृत अवधि (सेकंड में).

        def notify(self, args: aw.saving.DocumentSavingArgs):
            canceled_at = datetime.now()
            elapsed_seconds = (canceled_at - self.saving_started_at).total_seconds()
            if elapsed_seconds > self.max_duration:
                raise OperationCanceledException(f"estimated_progress = {args.estimated_progress}; canceled_at = {canceled_at}")

    def test_progress_callback(self):
        YOUR_DOCUMENT_DIRECTORY = 'YOUR_DOCUMENT_DIRECTORY'
        YOUR_OUTPUT_DIRECTORY = 'YOUR_OUTPUT_DIRECTORY'

        parameters = [
            (aw.SaveFormat.XAML_FLOW, "xamlflow"),
            (aw.SaveFormat.XAML_FLOW_PACK, "xamlflowpack"),
        ]

        for save_format, ext in parameters:
            doc = aw.Document(f"{YOUR_DOCUMENT_DIRECTORY}/Big document.docx")
            save_options = aw.saving.XamlFlowSaveOptions(save_format)
            save_options.progress_callback = self.SavingProgressCallback()

            try:
                doc.save(f"{YOUR_OUTPUT_DIRECTORY}/XamlFlowSaveOptions.progress_callback.{ext}", save_options)
            except OperationCanceledException as e:
                print(e)
```
**मुख्य कॉन्फ़िगरेशन विकल्प:**
- `save_format`: XAML_FLOW और XAML_FLOW_PACK के बीच चुनें.
- `progress_callback`: लंबे ऑपरेशन को संभालने के लिए प्रगति को सहेजने पर नज़र रखता है।

##### समस्या निवारण युक्तियों
- समायोजित करना `max_duration` दस्तावेज़ के आकार और जटिलता के आधार पर।
- सूचनाप्रद त्रुटि संदेश प्रदान करने के लिए अपवादों को शालीनतापूर्वक संभालें।

## व्यावहारिक अनुप्रयोगों

इन सुविधाओं के कुछ वास्तविक उपयोग के मामले यहां दिए गए हैं:
1. **दस्तावेज़ प्रबंधन प्रणालियाँ**छवि फ़ोल्डर्स निर्दिष्ट करके एम्बेडेड छवियों वाले बड़े दस्तावेज़ों को कुशलतापूर्वक प्रबंधित करें, प्रदर्शन और संगठन को बढ़ाएं।
2. **स्वचालित रिपोर्टिंग उपकरण**: प्रगति कॉलबैक का उपयोग करके यह सुनिश्चित करें कि रिपोर्ट स्वीकार्य समय सीमा के भीतर तैयार हो, जिससे उपयोगकर्ता अनुभव में सुधार हो।
3. **सामग्री वितरण नेटवर्क**: संसाधनों का प्रभावी प्रबंधन करते हुए वेब वितरण के लिए दस्तावेजों के रूपांतरण को सरल बनाना।

## प्रदर्शन संबंधी विचार

पायथन के साथ Aspose.Words का उपयोग करते समय प्रदर्शन को अनुकूलित करने के लिए:
- **स्मृति प्रबंधन**: संसाधन उपयोग की निगरानी करें और उपयोग के बाद वस्तुओं का निपटान करके मेमोरी को कुशलतापूर्वक प्रबंधित करें।
- **फ़ाइल I/O संचालन**: गति में सुधार के लिए फ़ाइल पढ़ने/लिखने के कार्यों को न्यूनतम करें।
- **प्रचय संसाधन**जहां तक संभव हो, ओवरहेड को कम करने के लिए दस्तावेजों को बैचों में संसाधित करें।

## निष्कर्ष

इस ट्यूटोरियल में, हमने XAML Flow और प्रोग्रेस कॉलबैक का उपयोग करके Python के लिए Aspose.Words के साथ दस्तावेज़ सहेजने का अनुकूलन करने का तरीका खोजा। इन सुविधाओं को लागू करके, आप अपने दस्तावेज़ प्रसंस्करण वर्कफ़्लो की दक्षता बढ़ा सकते हैं, संसाधनों को प्रभावी ढंग से प्रबंधित कर सकते हैं और समय पर संचालन सुनिश्चित कर सकते हैं।
{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}