---
"date": "2025-03-28"
"description": "Aspose.Words for Java का उपयोग करके दस्तावेज़ हस्ताक्षर को स्वचालित करने का तरीका जानें। यह ट्यूटोरियल आपके परिवेश को सेट करना, परीक्षण डेटा बनाना, हस्ताक्षर रेखाएँ जोड़ना और दस्तावेज़ों पर डिजिटल हस्ताक्षर करना शामिल करता है।"
"title": "Aspose.Words की सहायता से Java में दस्तावेज़ हस्ताक्षर को स्वचालित करें - एक व्यापक मार्गदर्शिका"
"url": "/hi/java/mail-merge-reporting/aspose-words-java-document-signing-tutorial/"
"weight": 1
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}


# Aspose.Words के साथ जावा में दस्तावेज़ हस्ताक्षर को स्वचालित करें: एक व्यापक गाइड

## परिचय

आज की तेज़-तर्रार कारोबारी दुनिया में, कुशल दस्तावेज़ प्रबंधन आवश्यक है। दस्तावेज़ों के निर्माण और डिजिटल हस्ताक्षर को स्वचालित करने से समय की बचत हो सकती है और त्रुटियाँ कम हो सकती हैं। यह ट्यूटोरियल आपको हस्ताक्षरकर्ताओं के लिए परीक्षण डेटा बनाने, हस्ताक्षर रेखाएँ जोड़ने और दस्तावेज़ों पर डिजिटल रूप से हस्ताक्षर करने के लिए Aspose.Words for Java का उपयोग करने के बारे में मार्गदर्शन करेगा।

**आप क्या सीखेंगे:**
- जावा प्रोजेक्ट में Aspose.Words सेट अप करना
- जावा के साथ परीक्षण हस्ताक्षरकर्ता डेटा बनाना
- वर्ड दस्तावेज़ों में हस्ताक्षर पंक्तियाँ जोड़ना
- डिजिटल प्रमाणपत्रों का उपयोग करके दस्तावेजों पर डिजिटल हस्ताक्षर करना

आइये अपने विकास परिवेश की तैयारी शुरू करें!

## आवश्यक शर्तें

ट्यूटोरियल में आगे बढ़ने से पहले, सुनिश्चित करें कि आपका सेटअप इन आवश्यकताओं को पूरा करता है:

- **जावा डेवलपमेंट किट (JDK):** संस्करण 8 या उच्चतर.
- **एकीकृत विकास वातावरण (आईडीई):** जैसे कि इंटेलीज आईडिया या एक्लिप्स।
- **जावा के लिए Aspose.Words:** इस लाइब्रेरी को मावेन या ग्रैडल के माध्यम से शामिल किया जा सकता है।

### ज्ञान पूर्वापेक्षाएँ

जावा प्रोग्रामिंग की बुनियादी समझ और फ़ाइलों और स्ट्रीम को संभालने की जानकारी फ़ायदेमंद होगी। अगर आप Aspose में नए हैं, तो चिंता न करें—हम ज़रूरी बातें बताएँगे।

## Aspose.Words की स्थापना

अपने प्रोजेक्ट में Java के लिए Aspose.Words का उपयोग करने के लिए, इन चरणों का पालन करें:

### मावेन निर्भरता

अपने में निम्नलिखित निर्भरता जोड़ें `pom.xml` फ़ाइल:

```xml
<dependency>
  <groupId>com.aspose</groupId>
  <artifactId>aspose-words</artifactId>
  <version>25.3</version>
</dependency>
```

### ग्रेडेल निर्भरता

Gradle प्रोजेक्ट्स के लिए, अपने में यह लाइन शामिल करें `build.gradle` फ़ाइल:

```gradle
implementation 'com.aspose:aspose-words:25.3'
```

### लाइसेंस अधिग्रहण

Aspose विभिन्न लाइसेंसिंग विकल्प प्रदान करता है:

- **मुफ्त परीक्षण:** सुविधाओं का परीक्षण करने के लिए निःशुल्क परीक्षण संस्करण डाउनलोड करें।
- **अस्थायी लाइसेंस:** मूल्यांकन प्रयोजनों के लिए एक अस्थायी लाइसेंस प्राप्त करें।
- **खरीदना:** पूर्ण पहुंच के लिए, Aspose की वेबसाइट से लाइसेंस खरीदें।

सुनिश्चित करें कि आपकी परियोजना आवश्यक निर्भरताओं और किसी भी आवश्यक लाइसेंस के साथ कॉन्फ़िगर की गई है। यह सेटअप आपको Aspose की शक्तिशाली दस्तावेज़ हेरफेर क्षमताओं का सहजता से लाभ उठाने की अनुमति देगा।

## कार्यान्वयन मार्गदर्शिका

हम प्रत्येक सुविधा को चरण-दर-चरण देखेंगे, जिसकी शुरुआत परीक्षण हस्ताक्षरकर्ता डेटा बनाने से होगी।

### फ़ीचर 1: हस्ताक्षरकर्ताओं के लिए परीक्षण डेटा बनाएँ

#### अवलोकन

यह सुविधा अद्वितीय आईडी, नाम, स्थिति और छवियों के साथ हस्ताक्षरकर्ताओं की एक सूची तैयार करती है। वास्तविक डेटा का उपयोग किए बिना दस्तावेज़ हस्ताक्षर परिदृश्यों का परीक्षण करने के लिए यह आवश्यक है।

##### चरण 1: अपना जावा क्लास सेट करें

नाम से एक क्लास बनाएं `SignPersonCreator` और आवश्यक लाइब्रेरीज़ आयात करें:

```java
import java.io.ByteArrayOutputStream;
import java.io.FileInputStream;
import java.io.IOException;
import java.io.InputStream;
import java.util.ArrayList;
import java.util.UUID;

class DocumentHelper {
    public static byte[] getBytesFromStream(InputStream inputStream) throws IOException {
        int numRead; 
        byte[] buffer = new byte[1024]; 
        ByteArrayOutputStream baos = new ByteArrayOutputStream();

        while ((numRead = inputStream.read(buffer)) != -1) {
            baos.write(buffer, 0, numRead);
        }
        return baos.toByteArray();
    }
}

public class SignPersonCreator {
    private static ArrayList<SignPersonTestClass> gSignPersonList;

    public static void main(String[] args) throws IOException {
        createSignPersonData();
        System.out.println("Test data successfully added!");
    }

    private static void createSignPersonData() throws IOException {
        InputStream inputStream = new FileInputStream(YOUR_DOCUMENT_DIRECTORY + "Logo.jpg");

        gSignPersonList = new ArrayList<>();
        gSignPersonList.add(new SignPersonTestClass(UUID.randomUUID(), "Ron Williams", "Chief Executive Officer",
                DocumentHelper.getBytesFromStream(inputStream)));
        gSignPersonList.add(new SignPersonTestClass(UUID.randomUUID(), "Stephen Morse", "Head of Compliance",
                DocumentHelper.getBytesFromStream(inputStream)));
    }
}
```

##### स्पष्टीकरण

- **यूयूआईडी:** प्रत्येक हस्ताक्षरकर्ता के लिए एक अद्वितीय पहचानकर्ता उत्पन्न करता है।
- **getBytesFromStream:** भंडारण के लिए एक छवि फ़ाइल को बाइट सरणी में परिवर्तित करता है।

### फ़ीचर 2: दस्तावेज़ में हस्ताक्षर लाइन जोड़ें

#### अवलोकन

यह सुविधा आपके दस्तावेज़ में एक हस्ताक्षर पंक्ति जोड़ती है, तथा उसे हस्ताक्षरकर्ता के विवरण के साथ जोड़ती है।

##### चरण 1: SignatureLineAdder क्लास बनाएँ

कार्यान्वयन `SignatureLineAdder` वर्ग इस प्रकार है:

```java
import com.aspose.words.*;

class SignatureLineAdder {
    public static void main(String[] args) throws Exception {
        String srcDocumentPath = YOUR_DOCUMENT_DIRECTORY + "Document.docx";
        String dstDocumentPath = YOUR_OUTPUT_DIRECTORY + "SignDocumentCustom.Sign.docx";
        
        SignPersonTestClass signPersonInfo = gSignPersonList.stream()
                .filter(x -> x.getName().equals("Ron Williams")).findFirst().orElse(null);

        if (signPersonInfo != null) {
            addSignatureLine(srcDocumentPath, dstDocumentPath, signPersonInfo);
            System.out.println("Signature line added successfully!");
        } else {
            System.out.println("Sign person does not exist, please check your parameters.");
        }
    }

    private static void addSignatureLine(final String srcDocumentPath, final String dstDocumentPath,
                                         final SignPersonTestClass signPersonInfo) throws Exception {
        Document document = new Document(srcDocumentPath);
        DocumentBuilder builder = new DocumentBuilder(document);

        SignatureLineOptions signatureLineOptions = new SignatureLineOptions();
        signatureLineOptions.setSigner(signPersonInfo.getName());
        signatureLineOptions.setSignerTitle(signPersonInfo.getPosition());

        SignatureLine signatureLine = builder.insertSignatureLine(signatureLineOptions).getSignatureLine();
        signatureLine.setId(String.valueOf(signPersonInfo.getPersonId()));

        builder.getDocument().save(dstDocumentPath);
    }
}
```

##### स्पष्टीकरण

- **हस्ताक्षर लाइन विकल्प:** हस्ताक्षरकर्ता का नाम और पदवी कॉन्फ़िगर करता है.
- **हस्ताक्षर पंक्ति डालें:** दस्तावेज़ में वर्तमान कर्सर स्थिति पर एक हस्ताक्षर पंक्ति सम्मिलित करता है।

### विशेषता 3: डिजिटल प्रमाणपत्र के साथ दस्तावेज़ पर हस्ताक्षर करें

#### अवलोकन

यह सुविधा डिजिटल प्रमाणपत्र का उपयोग करके दस्तावेज़ पर डिजिटल हस्ताक्षर करती है, जिससे प्रामाणिकता और अखंडता सुनिश्चित होती है।

##### चरण 1: दस्तावेज़ हस्ताक्षरकर्ता वर्ग बनाएँ

कार्यान्वयन `DocumentSigner` कक्षा:

```java
import com.aspose.words.*;

class DocumentSigner {
    public static void main(String[] args) throws Exception {
        String srcDocumentPath = YOUR_DOCUMENT_DIRECTORY + "Document.docx";
        String dstDocumentPath = YOUR_OUTPUT_DIRECTORY + "SignDocumentCustom.Sign.docx";
        String certificatePath = YOUR_DOCUMENT_DIRECTORY + "morzal.pfx";
        String certificatePassword = "aw";

        SignPersonTestClass signPersonInfo = gSignPersonList.stream()
                .filter(x -> x.getName().equals("Ron Williams")).findFirst().orElse(null);

        if (signPersonInfo != null) {
            signDocument(srcDocumentPath, dstDocumentPath, signPersonInfo, certificatePath, certificatePassword);
            System.out.println("Document successfully signed!");
        } else {
            System.out.println("Sign person does not exist, please check your parameters.");
        }
    }

    private static void signDocument(final String srcDocumentPath, final String dstDocumentPath,
                                     final SignPersonTestClass signPersonInfo, final String certificatePath,
                                     final String certificatePassword) throws Exception {
        Document document = new Document(dstDocumentPath);

        CertificateHolder certificateHolder = CertificateHolder.create(certificatePath, certificatePassword);

        SignOptions signOptions = new SignOptions();
        signOptions.setSignatureLineId(String.valueOf(
            signPersonInfo.getPersonId()));

        document.sign(signOptions, certificateHolder);
    }
}
```

##### स्पष्टीकरण

- **प्रमाणपत्रधारक:** हस्ताक्षर के लिए प्रयुक्त डिजिटल प्रमाणपत्र को दर्शाता है।
- **संकेत:** वह विधि जो निर्दिष्ट विकल्पों और प्रमाणपत्र के साथ दस्तावेज़ पर हस्ताक्षर करती है।

## निष्कर्ष

इस ट्यूटोरियल में, आपने Aspose.Words का उपयोग करके Java में दस्तावेज़ निर्माण और हस्ताक्षर को स्वचालित करने का तरीका सीखा है। इन चरणों का पालन करके, आप अपने दस्तावेज़ प्रबंधन प्रक्रियाओं को सुव्यवस्थित कर सकते हैं, सुरक्षा बढ़ा सकते हैं और डेटा अखंडता सुनिश्चित कर सकते हैं। आगे की खोज के लिए, Aspose.Words की अधिक उन्नत सुविधाओं में गोता लगाने पर विचार करें।

**अगले कदम:**
- मेल मर्ज या रिपोर्ट जनरेशन जैसी अतिरिक्त Aspose.Words सुविधाओं का अन्वेषण करें।
- विस्तृत मार्गदर्शिका और API संदर्भों के लिए Aspose दस्तावेज़ देखें।
- Aspose.Words द्वारा समर्थित विभिन्न दस्तावेज़ प्रारूपों के साथ प्रयोग करें।

{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}