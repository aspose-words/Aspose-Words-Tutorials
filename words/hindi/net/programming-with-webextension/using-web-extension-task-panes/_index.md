---
"description": "इस विस्तृत, चरण-दर-चरण ट्यूटोरियल में .NET के लिए Aspose.Words का उपयोग करके Word दस्तावेज़ों में वेब एक्सटेंशन टास्क पैन को जोड़ने और कॉन्फ़िगर करने का तरीका जानें।"
"linktitle": "वेब एक्सटेंशन टास्क पैन का उपयोग करना"
"second_title": "Aspose.Words दस्तावेज़ प्रसंस्करण API"
"title": "वेब एक्सटेंशन टास्क पैन का उपयोग करना"
"url": "/hi/net/programming-with-webextension/using-web-extension-task-panes/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# वेब एक्सटेंशन टास्क पैन का उपयोग करना

## परिचय

Aspose.Words for .NET का उपयोग करके Word दस्तावेज़ में वेब एक्सटेंशन टास्क पैन का उपयोग करने पर इस गहन ट्यूटोरियल में आपका स्वागत है। यदि आप कभी भी अपने Word दस्तावेज़ों को इंटरैक्टिव टास्क पैन के साथ बेहतर बनाना चाहते हैं, तो आप सही जगह पर हैं। यह मार्गदर्शिका आपको इसे सहजता से प्राप्त करने के लिए हर चरण से गुजारेगी।

## आवश्यक शर्तें

इससे पहले कि हम आगे बढ़ें, आइए सुनिश्चित करें कि आपके पास वह सब कुछ है जो आपको चाहिए:

- .NET के लिए Aspose.Words: आप इसे डाउनलोड कर सकते हैं [यहाँ](https://releases.aspose.com/words/net/).
- .NET विकास वातावरण: विजुअल स्टूडियो या कोई अन्य IDE जिसे आप पसंद करते हैं।
- C# का बुनियादी ज्ञान: इससे आपको कोड उदाहरणों को समझने में मदद मिलेगी।
- Aspose.Words के लिए लाइसेंस: आप एक खरीद सकते हैं [यहाँ](https://purchase.aspose.com/buy) या अस्थायी लाइसेंस प्राप्त करें [यहाँ](https://purchase.aspose.com/temporary-license/).

## नामस्थान आयात करें

कोडिंग शुरू करने से पहले, सुनिश्चित करें कि आपके प्रोजेक्ट में निम्नलिखित नेमस्पेस आयातित हैं:

```csharp
using Aspose.Words;
using Aspose.Words.WebExtensions;
```

## चरण-दर-चरण मार्गदर्शिका

अब, आइये इस प्रक्रिया को आसान चरणों में विभाजित करें।

### चरण 1: अपनी दस्तावेज़ निर्देशिका सेट करना

सबसे पहले, हमें आपके डॉक्यूमेंट डायरेक्टरी का पथ सेट करना होगा। यहीं पर आपका वर्ड डॉक्यूमेंट सेव होगा।

```csharp
// दस्तावेज़ निर्देशिका का पथ.
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

प्रतिस्थापित करें `"YOUR DOCUMENT DIRECTORY"` अपने दस्तावेज़ फ़ोल्डर के वास्तविक पथ के साथ.

### चरण 2: नया दस्तावेज़ बनाना

इसके बाद, हम Aspose.Words का उपयोग करके एक नया Word दस्तावेज़ बनाएंगे।

```csharp
Document doc = new Document();
```

यह पंक्ति एक नए उदाहरण को आरंभ करती है `Document` क्लास, जो एक वर्ड दस्तावेज़ का प्रतिनिधित्व करता है.

### चरण 3: कार्य फलक जोड़ना

अब, हम अपने दस्तावेज़ में एक टास्क पेन जोड़ेंगे। टास्क पेन एक वर्ड दस्तावेज़ के भीतर अतिरिक्त कार्यक्षमता और उपकरण प्रदान करने के लिए उपयोगी होते हैं।

```csharp
TaskPane taskPane = new TaskPane();
doc.WebExtensionTaskPanes.Add(taskPane);
```

यहाँ, हम एक नया निर्माण करते हैं `TaskPane` ऑब्जेक्ट और इसे दस्तावेज़ में जोड़ें `WebExtensionTaskPanes` संग्रह।

### चरण 4: कार्य फलक को कॉन्फ़िगर करना

अपने कार्य फलक को दृश्यमान बनाने और उसके गुणधर्म निर्धारित करने के लिए, हम निम्नलिखित कोड का उपयोग करते हैं:

```csharp
taskPane.DockState = TaskPaneDockState.Right;
taskPane.IsVisible = true;
taskPane.Width = 300;
```

- `DockState` टास्क पेन कहां दिखाई देगा यह सेट करता है। इस मामले में, यह दाईं ओर है।
- `IsVisible` यह सुनिश्चित करता है कि कार्य फलक दृश्यमान हो.
- `Width` कार्य फलक की चौड़ाई निर्धारित करता है.

### चरण 5: वेब एक्सटेंशन संदर्भ सेट अप करना

इसके बाद, हम वेब एक्सटेंशन संदर्भ सेट करते हैं जिसमें आईडी, संस्करण, स्टोर प्रकार और स्टोर शामिल होते हैं।

```csharp
taskPane.WebExtension.Reference.Id = "wa102923726";
taskPane.WebExtension.Reference.Version = "1.0.0.0";
taskPane.WebExtension.Reference.StoreType = WebExtensionStoreType.OMEX;
taskPane.WebExtension.Reference.Store = "th-TH";
```

- `Id` वेब एक्सटेंशन के लिए एक अद्वितीय पहचानकर्ता है।
- `Version` एक्सटेंशन का संस्करण निर्दिष्ट करता है.
- `StoreType` स्टोर के प्रकार को इंगित करता है (इस मामले में, OMEX)।
- `Store` स्टोर का भाषा/संस्कृति कोड निर्दिष्ट करता है.

### चरण 6: वेब एक्सटेंशन में गुण जोड़ना

आप अपने वेब एक्सटेंशन के व्यवहार या सामग्री को परिभाषित करने के लिए उसमें गुण जोड़ सकते हैं।

```csharp
taskPane.WebExtension.Properties.Add(new WebExtensionProperty("mailchimpCampaign", "mailchimpCampaign"));
```

यहाँ, हम नाम की एक संपत्ति जोड़ते हैं `mailchimpCampaign`.

### चरण 7: वेब एक्सटेंशन को बाइंड करना

अंत में, हम अपने वेब एक्सटेंशन में बाइंडिंग जोड़ते हैं। बाइंडिंग आपको एक्सटेंशन को दस्तावेज़ के विशिष्ट भागों से लिंक करने की अनुमति देती है।

```csharp
taskPane.WebExtension.Bindings.Add(new WebExtensionBinding("UnnamedBinding_0_1506535429545", WebExtensionBindingType.Text, "194740422"));
```

- `UnnamedBinding_0_1506535429545` बंधन का नाम है.
- `WebExtensionBindingType.Text` यह इंगित करता है कि बाइंडिंग टेक्स्ट प्रकार की है।
- `194740422` दस्तावेज़ के उस भाग की आईडी है जिससे एक्सटेंशन जुड़ा हुआ है।

### चरण 8: दस्तावेज़ को सहेजना

सब कुछ सेट करने के बाद, अपना दस्तावेज़ सेव करें।

```csharp
doc.Save(dataDir + "WorkingWithWebExtension.UsingWebExtensionTaskPanes.docx");
```

यह पंक्ति दस्तावेज़ को दिए गए फ़ाइल नाम के साथ निर्दिष्ट निर्देशिका में सहेजती है।

### चरण 9: कार्य फलक जानकारी लोड करना और प्रदर्शित करना

कार्य फलक की जानकारी को सत्यापित करने और प्रदर्शित करने के लिए, हम दस्तावेज़ को लोड करते हैं और कार्य फलकों के माध्यम से पुनरावृति करते हैं।

```csharp
doc = new Document(dataDir + "WorkingWithWebExtension.UsingWebExtensionTaskPanes.docx");

Console.WriteLine("Task panes sources:\n");

foreach (TaskPane taskPaneInfo in doc.WebExtensionTaskPanes)
{
    WebExtensionReference reference = taskPaneInfo.WebExtension.Reference;
    Console.WriteLine($"Provider: \"{reference.Store}\", version: \"{reference.Version}\", catalog identifier: \"{reference.Id}\";");
}
```

यह कोड दस्तावेज़ को लोड करता है और कंसोल में प्रत्येक कार्य फलक के प्रदाता, संस्करण और कैटलॉग पहचानकर्ता को प्रिंट करता है।

## निष्कर्ष

और बस! आपने Aspose.Words for .NET का उपयोग करके Word दस्तावेज़ में वेब एक्सटेंशन टास्क पेन को सफलतापूर्वक जोड़ा और कॉन्फ़िगर किया है। यह शक्तिशाली सुविधा सीधे दस्तावेज़ के भीतर अतिरिक्त कार्यक्षमता प्रदान करके आपके Word दस्तावेज़ों को महत्वपूर्ण रूप से बढ़ा सकती है। 

## अक्सर पूछे जाने वाले प्रश्न

### वर्ड में टास्क पेन क्या है?
टास्क पेन एक इंटरफ़ेस तत्व है जो वर्ड दस्तावेज़ के भीतर अतिरिक्त उपकरण और कार्यात्मकताएं प्रदान करता है, जिससे उपयोगकर्ता की सहभागिता और उत्पादकता बढ़ती है।

### क्या मैं कार्य फलक के स्वरूप को अनुकूलित कर सकता हूँ?
हां, आप निम्न जैसे गुण सेट करके टास्क पेन के स्वरूप को अनुकूलित कर सकते हैं `DockState`, `IsVisible`, और `Width`.

### वेब एक्सटेंशन गुण क्या हैं?
वेब एक्सटेंशन गुण वे कस्टम गुण हैं जिन्हें आप किसी वेब एक्सटेंशन में उसके व्यवहार या सामग्री को परिभाषित करने के लिए जोड़ सकते हैं।

### मैं वेब एक्सटेंशन को दस्तावेज़ के किसी भाग से कैसे जोड़ूं?
आप वेब एक्सटेंशन को दस्तावेज़ के किसी भाग से इस प्रकार जोड़ सकते हैं: `WebExtensionBinding` क्लास, बाइंडिंग प्रकार और लक्ष्य आईडी निर्दिष्ट करना।

### मैं Aspose.Words for .NET के बारे में अधिक जानकारी कहां पा सकता हूं?
आप विस्तृत दस्तावेज पा सकते हैं [यहाँ](https://reference.aspose.com/words/net/).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}