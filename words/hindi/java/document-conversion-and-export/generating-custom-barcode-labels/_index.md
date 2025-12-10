---
date: 2025-12-10
description: Aspose.Words for Java का उपयोग करके कस्टम बारकोड लेबल कैसे बनाएं, सीखें।
  यह चरण-दर-चरण गाइड आपको दिखाता है कि वर्ड दस्तावेज़ों में बारकोड कैसे एम्बेड करें।
linktitle: Generating Custom Barcode Labels
second_title: Aspose.Words Java Document Processing API
title: Aspose.Words for Java में कस्टम बारकोड लेबल बनाएं
url: /hi/java/document-conversion-and-export/generating-custom-barcode-labels/
weight: 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for Java में कस्टम बारकोड लेबल जनरेट करें

## Aspose.Words for Java में कस्टम बारकोड जनरेट करने का परिचय

बारकोड आधुनिक अनुप्रयोगों में अनिवार्य हैं—चाहे आप इन्वेंट्री प्रबंधित कर रहे हों, टिकट प्रिंट कर रहे हों, या आईडी कार्ड बना रहे हों। इस ट्यूटोरियल में आप **कस्टम बारकोड** लेबल जनरेट करेंगे और उन्हें सीधे `IBarcodeGenerator` इंटरफ़ेस का उपयोग करके Word दस्तावेज़ में एम्बेड करेंगे। हम पर्यावरण सेटअप से लेकर बारकोड इमेज डालने तक हर कदम को विस्तार से बताएँगे, ताकि आप तुरंत अपने Java प्रोजेक्ट्स में बारकोड का उपयोग शुरू कर सकें।

## त्वरित उत्तर
- **यह ट्यूटोरियल क्या सिखाता है?** Aspose.Words for Java के साथ कस्टम बारकोड लेबल जनरेट करना और उन्हें Word फ़ाइल में एम्बेड करना।  
- **उदाहरण में कौन सा बारकोड प्रकार उपयोग किया गया है?** QR कोड (आप इसे किसी भी समर्थित प्रकार से बदल सकते हैं)।  
- **क्या लाइसेंस की आवश्यकता है?** विकास के दौरान अनलिमिटेड एक्सेस के लिए एक टेम्पररी लाइसेंस आवश्यक है।  
- **कौन सा Java संस्करण आवश्यक है?** JDK 8 या उससे ऊपर।  
- **क्या मैं बारकोड का आकार या रंग बदल सकता हूँ?** हाँ—`BarcodeParameters` और `BarcodeGenerator` सेटिंग्स को संशोधित करें।

## पूर्वापेक्षाएँ

कोडिंग शुरू करने से पहले सुनिश्चित करें कि आपके पास निम्नलिखित हैं:

- Java Development Kit (JDK): संस्करण 8 या उससे ऊपर।  
- Aspose.Words for Java लाइब्रेरी: [Download here](https://releases.aspose.com/words/java/)।  
- Aspose.BarCode for Java लाइब्रेरी: [Download here](https://releases.aspose.com/)।  
- इंटीग्रेटेड डेवलपमेंट एनवायरनमेंट (IDE): IntelliJ IDEA, Eclipse, या कोई भी पसंदीदा IDE।  
- टेम्पररी लाइसेंस: अनलिमिटेड एक्सेस के लिए एक [temporary license](https://purchase.aspose.com/temporary-license/) प्राप्त करें।

## पैकेज इम्पोर्ट करें

हम Aspose.Words और Aspose.BarCode लाइब्रेरी का उपयोग करेंगे। अपने प्रोजेक्ट में निम्नलिखित पैकेज इम्पोर्ट करें:

```java
import com.aspose.barcode.generation.*;
import com.aspose.words.BarcodeParameters;
import com.aspose.words.IBarcodeGenerator;
import java.awt.*;
import java.awt.image.BufferedImage;
```

इन इम्पोर्ट्स से हमें बारकोड जनरेशन API और Word दस्तावेज़ क्लासेज़ तक पहुँच मिलती है।

## चरण 1: बारकोड ऑपरेशन्स के लिए एक यूटिलिटी क्लास बनाएं

मुख्य कोड को साफ़ रखने के लिए हम सामान्य हेल्पर्स—जैसे **twips को pixels में बदलना** और **hex‑color रूपांतरण**—को एक यूटिलिटी क्लास में एन्कैप्सुलेट करेंगे।

### कोड

```java
class CustomBarcodeGeneratorUtils {
    public static double twipsToPixels(String heightInTwips, double defVal) {
        try {
            int lVal = Integer.parseInt(heightInTwips);
            return (lVal / 1440.0) * 96.0; // Assuming default DPI is 96
        } catch (Exception e) {
            return defVal;
        }
    }

    public static Color convertColor(String inputColor, Color defVal) {
        if (inputColor == null || inputColor.isEmpty()) return defVal;
        try {
            int color = Integer.parseInt(inputColor, 16);
            return new Color((color & 0xFF), ((color >> 8) & 0xFF), ((color >> 16) & 0xFF));
        } catch (Exception e) {
            return defVal;
        }
    }
}
```

**व्याख्या**

- `twipsToPixels` – Word आयामों को **twips** में मापता है; यह मेथड उन्हें स्क्रीन पिक्सेल में बदलता है, जो बारकोड इमेज का सटीक आकार निर्धारित करने में उपयोगी है।  
- `convertColor` – हेक्साडेसिमल स्ट्रिंग (जैसे `"FF0000"` लाल के लिए) को `java.awt.Color` ऑब्जेक्ट में बदलता है, जिससे आप **बारकोड को कस्टम फोरग्राउंड और बैकग्राउंड रंगों** के साथ इन्सर्ट कर सकते हैं।

## चरण 2: कस्टम बारकोड जनरेटर लागू करें

अब हम `IBarcodeGenerator` इंटरफ़ेस को इम्प्लीमेंट करेंगे। यह क्लास **generate qr code java**‑स्टाइल इमेजेज़** बनाकर Aspose.Words में एम्बेड करने के लिए जिम्मेदार होगी।

### कोड

```java
class CustomBarcodeGenerator implements IBarcodeGenerator {
    public BufferedImage getBarcodeImage(BarcodeParameters parameters) {
        try {
            BarcodeGenerator gen = new BarcodeGenerator(
                CustomBarcodeGeneratorUtils.getBarcodeEncodeType(parameters.getBarcodeType()),
                parameters.getBarcodeValue()
            );

            gen.getParameters().getBarcode().setBarColor(
                CustomBarcodeGeneratorUtils.convertColor(parameters.getForegroundColor(), Color.BLACK)
            );
            gen.getParameters().setBackColor(
                CustomBarcodeGeneratorUtils.convertColor(parameters.getBackgroundColor(), Color.WHITE)
            );

            return gen.generateBarCodeImage();
        } catch (Exception e) {
            return new BufferedImage(100, 100, BufferedImage.TYPE_INT_ARGB);
        }
    }

    public BufferedImage getOldBarcodeImage(BarcodeParameters parameters) {
        throw new UnsupportedOperationException();
    }
}
```

**व्याख्या**

- `getBarcodeImage` `BarcodeGenerator` का एक इंस्टेंस बनाता है, `BarcodeParameters` द्वारा प्रदान किए गए रंग लागू करता है, और अंत में एक `BufferedImage` रिटर्न करता है।  
- यह मेथड त्रुटियों को सुगमता से हैंडल करता है और एक प्लेसहोल्डर इमेज रिटर्न करता है, जिससे Word दस्तावेज़ निर्माण कभी क्रैश नहीं होता।

## चरण 3: बारकोड जनरेट करें और **बारकोड को Word में एम्बेड करें**

जनरेटर तैयार होने के बाद, हम अब एक बारकोड इमेज बनाकर **इसे Word दस्तावेज़ में इन्सर्ट** करेंगे।

### कोड

```java
import com.aspose.words.*;

public class GenerateCustomBarcodeLabels {
    public static void main(String[] args) throws Exception {
        // Load or create a Word document
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Set up custom barcode generator
        CustomBarcodeGenerator barcodeGenerator = new CustomBarcodeGenerator();
        BarcodeParameters barcodeParameters = new BarcodeParameters();
        barcodeParameters.setBarcodeType("QR");
        barcodeParameters.setBarcodeValue("https://example.com");
        barcodeParameters.setForegroundColor("000000");
        barcodeParameters.setBackgroundColor("FFFFFF");

        // Generate barcode image
        BufferedImage barcodeImage = barcodeGenerator.getBarcodeImage(barcodeParameters);

        // Insert barcode image into Word document
        builder.insertImage(barcodeImage, 200, 200);

        // Save the document
        doc.save("CustomBarcodeLabels.docx");

        System.out.println("Barcode labels generated successfully!");
    }
}
```

**व्याख्या**

1. **डॉक्यूमेंट इनिशियलाइज़ेशन** – एक नया `Document` बनाता है (या आप मौजूदा टेम्पलेट लोड कर सकते हैं)।  
2. **बारकोड पैरामीटर्स** – बारकोड प्रकार (`QR`), एन्कोड करने वाला वैल्यू, और फोरग्राउंड/बैकग्राउंड रंग निर्धारित करता है।  
3. **इमेज इन्सर्शन** – `builder.insertImage` जनरेटेड बारकोड को इच्छित आकार (200 × 200 पिक्सेल) पर रखता है। यह **how to insert barcode** को Word फ़ाइल में डालने का मुख्य भाग है।  
4. **सेविंग** – अंतिम दस्तावेज़, `CustomBarcodeLabels.docx`, में एम्बेडेड बारकोड होता है, जिसे प्रिंट या वितरण के लिए तैयार किया जा सकता है।

## Aspose.Words के साथ कस्टम बारकोड लेबल क्यों जनरेट करें?

- **पूर्ण नियंत्रण** बारकोड की उपस्थिति (प्रकार, आकार, रंग) पर।  
- **सीमलेस इंटीग्रेशन** – मध्यवर्ती इमेज फ़ाइलों की आवश्यकता नहीं; बारकोड मेमोरी में जनरेट होकर सीधे एम्बेड होता है।  
- **क्रॉस‑प्लेटफ़ॉर्म** – किसी भी OS पर काम करता है जो Java सपोर्ट करता है, जिससे यह सर्वर‑साइड डॉक्यूमेंट जनरेशन के लिए आदर्श है।  
- **स्केलेबल** – आप डेटा स्रोत पर लूप करके एक ही रन में सैकड़ों पर्सनलाइज़्ड लेबल बना सकते हैं।

## सामान्य समस्याएँ और ट्रबलशूटिंग

| लक्षण | संभावित कारण | समाधान |
|-------|--------------|--------|
| बारकोड खाली दिख रहा है | `BarcodeParameters` के रंग एक जैसे हैं (जैसे काला पर काला) | `foregroundColor` और `backgroundColor` मानों की जाँच करें। |
| इमेज विकृत है | `insertImage` को गलत पिक्सेल डाइमेंशन पास किए गए हैं | चौड़ाई/ऊँचाई आर्ग्यूमेंट को समायोजित करें या सटीक आकार के लिए `twipsToPixels` रूपांतरण का उपयोग करें। |
| असमर्थित बारकोड प्रकार त्रुटि | `CustomBarcodeGeneratorUtils.getBarcodeEncodeType` द्वारा न पहचाना गया प्रकार उपयोग किया गया | सुनिश्चित करें कि बारकोड प्रकार स्ट्रिंग समर्थित `EncodeTypes` (जैसे `"QR"`, `"CODE128"`) में से एक है। |

## अक्सर पूछे जाने वाले प्रश्न

**प्रश्न: क्या मैं Aspose.Words for Java को बिना लाइसेंस के उपयोग कर सकता हूँ?**  
उत्तर: हाँ, लेकिन कुछ सीमाएँ होंगी। पूर्ण कार्यक्षमता के लिए एक [temporary license](https://purchase.aspose.com/temporary-license/) प्राप्त करें।

**प्रश्न: मैं कौन‑से प्रकार के बारकोड जनरेट कर सकता हूँ?**  
उत्तर: Aspose.BarCode QR, Code 128, EAN‑13 और कई अन्य फॉर्मेट्स को सपोर्ट करता है। पूरी सूची के लिए [documentation](https://reference.aspose.com/words/java/) देखें।

**प्रश्न: मैं बारकोड का आकार कैसे बदल सकता हूँ?**  
उत्तर: `builder.insertImage` में चौड़ाई और ऊँचाई आर्ग्यूमेंट को समायोजित करें, या Word माप इकाइयों को पिक्सेल में बदलने के लिए `twipsToPixels` का उपयोग करें।

**प्रश्न: क्या बारकोड टेक्स्ट के लिए कस्टम फ़ॉन्ट उपयोग कर सकता हूँ?**  
उत्तर: हाँ, आप `BarcodeGenerator` की `CodeTextParameters` प्रॉपर्टी के माध्यम से टेक्स्ट फ़ॉन्ट को कस्टमाइज़ कर सकते हैं।

**प्रश्न: यदि मुझे समस्याएँ आती हैं तो मदद कहाँ से मिल सकती है?**  
उत्तर: सहायता के लिए [support forum](https://forum.aspose.com/c/words/8/) पर जाएँ, जहाँ Aspose समुदाय और इंजीनियर्स मदद करेंगे।

## निष्कर्ष

ऊपर बताए गए चरणों को अपनाकर आप अब **कस्टम बारकोड** इमेजेज़ जनरेट करना और Aspose.Words for Java के साथ **बारकोड को Word** दस्तावेज़ में एम्बेड करना जानते हैं। यह तकनीक इन्वेंट्री टैग, इवेंट टिकट या किसी भी स्थिति में जहाँ बारकोड जनरेटेड दस्तावेज़ का हिस्सा हो, के लिए लचीली है। विभिन्न बारकोड प्रकारों और स्टाइलिंग विकल्पों के साथ प्रयोग करें ताकि आपके व्यवसाय की विशिष्ट आवश्यकताओं को पूरा किया जा सके।

---

**अंतिम अपडेट:** 2025-12-10  
**टेस्टेड विथ:** Aspose.Words for Java 24.12, Aspose.BarCode for Java 24.12  
**लेखक:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}