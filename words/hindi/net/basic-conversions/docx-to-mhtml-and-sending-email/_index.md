---
"description": "इस चरण-दर-चरण मार्गदर्शिका में जानें कि DOCX को MHTML में कैसे बदलें और .NET के लिए Aspose.Words का उपयोग करके ईमेल कैसे भेजें। आसान स्वचालन के साथ अपनी उत्पादकता बढ़ाएँ।"
"linktitle": "Docx को Mhtml में बदलें और ईमेल भेजें"
"second_title": "Aspose.Words दस्तावेज़ प्रसंस्करण API"
"title": "Docx को Mhtml में बदलें और ईमेल भेजें"
"url": "/hi/net/basic-conversions/docx-to-mhtml-and-sending-email/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Docx को Mhtml में बदलें और ईमेल भेजें

## परिचय

आज के डिजिटल युग में, दस्तावेज़ों को एक फ़ॉर्मेट से दूसरे फ़ॉर्मेट में बदलना और उन्हें ईमेल के ज़रिए भेजना एक आम काम है। यह लेख आपको DOCX फ़ाइल को MHTML फ़ॉर्मेट में बदलने और फिर Aspose.Words for .NET का उपयोग करके उसे ईमेल के रूप में भेजने की प्रक्रिया से परिचित कराएगा। हम प्रत्येक चरण को विस्तृत, आसानी से समझने योग्य गाइड में विभाजित करेंगे, ताकि आप प्रक्रिया को शुरू से अंत तक समझ सकें। आइए शुरू करते हैं!

## आवश्यक शर्तें

शुरू करने से पहले, सुनिश्चित करें कि आपके पास निम्नलिखित पूर्वापेक्षाएँ मौजूद हैं:

1. Aspose.Words for .NET: Aspose.Words for .NET लाइब्रेरी को डाउनलोड करें और इंस्टॉल करें [Aspose रिलीज़ पेज](https://releases.aspose.com/words/net/).
2. .NET के लिए Aspose.Email: .NET लाइब्रेरी के लिए Aspose.Email को डाउनलोड करें और इंस्टॉल करें। [Aspose रिलीज़ पेज](https://releases.aspose.com/email/net/).
3. .NET फ्रेमवर्क: सुनिश्चित करें कि आपके मशीन पर .NET फ्रेमवर्क स्थापित है।
4. एसएमटीपी सर्वर: ईमेल भेजने के लिए आपको एसएमटीपी सर्वर तक पहुंच की आवश्यकता होती है।

## नामस्थान आयात करें

अपने प्रोजेक्ट में Aspose.Words और Aspose.Email का उपयोग करने के लिए, आपको आवश्यक नामस्थान आयात करने होंगे। अपनी C# फ़ाइल के शीर्ष पर निम्नलिखित using निर्देश जोड़ें:

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using Aspose.Email;
using Aspose.Email.Mime;
using Aspose.Email.Clients.Smtp;
```

आइए इस प्रक्रिया को कई चरणों में विभाजित करें ताकि आप प्रत्येक भाग को स्पष्ट रूप से समझ सकें।

## चरण 1: DOCX दस्तावेज़ लोड करें

सबसे पहले, आपको वह DOCX दस्तावेज़ लोड करना होगा जिसे आप कनवर्ट करना चाहते हैं। `Document` अपनी DOCX फ़ाइल लोड करने के लिए Aspose.Words से क्लास का उपयोग करें।

```csharp
// दस्तावेज़ निर्देशिका का पथ.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Document.docx");
```

## चरण 2: दस्तावेज़ को MHTML के रूप में सहेजें

इसके बाद, लोड किए गए दस्तावेज़ को MHTML फ़ाइल के रूप में सेव करें। यह कार्य MHTML फ़ाइल के रूप में किया जाता है। `Save` की विधि `Document` कक्षा।

```csharp
Stream stream = new MemoryStream();
doc.Save(stream, SaveFormat.Mhtml);

// स्ट्रीम को आरंभ में वापस ले जाएं ताकि Aspose.Email इसे पढ़ सके।
stream.Position = 0;
```

## चरण 3: एक ईमेल संदेश बनाएँ

अब, Aspose.Email का उपयोग करके MHTML स्ट्रीम से एक ईमेल संदेश बनाएँ। आप इसका उपयोग करेंगे `MailMessage` इस उद्देश्य के लिए कक्षा.

```csharp
// स्ट्रीम से एक Aspose.Email MIME ईमेल संदेश बनाएँ।
MailMessage message = MailMessage.Load(stream, new MhtmlLoadOptions());
message.From = "your_from@email.com";
message.To = "your_to@email.com";
message.Subject = "Aspose.Words + Aspose.Email MHTML Test Message";
```

## चरण 4: ईमेल भेजें

अंत में, SMTP क्लाइंट का उपयोग करके ईमेल भेजें। अपने SMTP सर्वर विवरण के साथ SMTP क्लाइंट को कॉन्फ़िगर करें और इसका उपयोग करें `Send` संदेश भेजने की विधि.

```csharp
// Aspose.Email का उपयोग करके संदेश भेजें.
SmtpClient client = new SmtpClient();
client.Host = "your_smtp.com";
client.Send(message);
```

## निष्कर्ष

बधाई हो! आपने सफलतापूर्वक एक DOCX दस्तावेज़ को MHTML में परिवर्तित कर लिया है और इसे Aspose.Words for .NET का उपयोग करके ईमेल के माध्यम से भेज दिया है। इस प्रक्रिया में दस्तावेज़ को लोड करना, इसे MHTML में परिवर्तित करना, एक ईमेल संदेश बनाना और इसे SMTP क्लाइंट का उपयोग करके भेजना शामिल है। इन चरणों के साथ, आप अपने अनुप्रयोगों में दस्तावेज़ों के रूपांतरण और ईमेलिंग को आसानी से स्वचालित कर सकते हैं।

## अक्सर पूछे जाने वाले प्रश्न

### क्या मैं अन्य दस्तावेज़ प्रारूपों को परिवर्तित करने के लिए इस विधि का उपयोग कर सकता हूँ?
हां, Aspose.Words विभिन्न प्रारूपों का समर्थन करता है, और आप DOC, DOCX, RTF, और अधिक जैसे दस्तावेजों को MHTML में परिवर्तित कर सकते हैं।

### मैं ईमेल में अनुलग्नक कैसे जोड़ सकता हूँ?
आप इसका उपयोग कर सकते हैं `Attachments` की संपत्ति `MailMessage` अपने ईमेल में अनुलग्नक जोड़ने के लिए क्लास का उपयोग करें।

### क्या Aspose.Words .NET कोर के साथ संगत है?
हां, Aspose.Words .NET Core के साथ संगत है। आप इसे .NET Core एप्लीकेशन में भी इस्तेमाल कर सकते हैं।

### क्या मुझे Aspose.Words और Aspose.Email के लिए लाइसेंस की आवश्यकता है?
हां, दोनों पुस्तकालयों को लाइसेंस की आवश्यकता है। आप अस्थायी लाइसेंस प्राप्त कर सकते हैं [Aspose खरीद पृष्ठ](https://purchase.aspose.com/temporary-license/) मूल्यांकन प्रयोजनों के लिए।

### मैं अधिक दस्तावेज कहां पा सकता हूं?
आप Aspose.Words के लिए विस्तृत दस्तावेज़ पा सकते हैं [यहाँ](https://reference.aspose.com/words/net/) और Aspose.Email के लिए [यहाँ](https://reference.aspose.com/email/net/).



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}