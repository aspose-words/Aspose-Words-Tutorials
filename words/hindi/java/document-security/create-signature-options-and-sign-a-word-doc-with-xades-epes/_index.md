---
category: general
date: 2026-10-10
description: Java में XAdES EPES का उपयोग करके हस्ताक्षर विकल्प बनाएं और एक Word दस्तावेज़
  पर साइन करें। कुछ स्पष्ट चरणों में प्रमाणपत्र के साथ ऑफिस दस्तावेज़ पर हस्ताक्षर
  करना सीखें।
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create signature options
- sign word doc
- sign office document
- how to sign docx
language: hi
lastmod: 2026-10-10
og_description: Java में XAdES EPES का उपयोग करके सिग्नेचर विकल्प बनाएं और एक Word
  दस्तावेज़ पर हस्ताक्षर करें। यह गाइड आपको प्रमाणपत्र के साथ ऑफिस दस्तावेज़ को सुरक्षित
  रूप से साइन करने का तरीका दिखाता है।
og_image_alt: Screenshot of Java code that creates signature options and signs a DOCX
  file
og_title: हस्ताक्षर विकल्प बनाएं और XAdES EPES के साथ एक Word दस्तावेज़ पर हस्ताक्षर
  करें
schemas:
- author: GroupDocs
  dateModified: '2026-10-10'
  description: Create signature options and sign a Word doc using XAdES EPES in Java.
    Learn how to sign office document with a certificate in a few clear steps.
  headline: Create signature options and sign a Word doc with XAdES EPES
  type: TechArticle
- description: Create signature options and sign a Word doc using XAdES EPES in Java.
    Learn how to sign office document with a certificate in a few clear steps.
  name: Create signature options and sign a Word doc with XAdES EPES
  steps:
  - name: The library loads the `.pfx` file and extracts the private key using the
      supplied password.
    text: The library loads the `.pfx` file and extracts the private key using the
      supplied password.
  - name: It creates an XML‑DSig structure matching the XAdES‑EPES profile.
    text: It creates an XML‑DSig structure matching the XAdES‑EPES profile.
  - name: The signature is embedded into the DOCX package, preserving the original
      document layout.
    text: The signature is embedded into the DOCX package, preserving the original
      document layout.
  - name: Open `SignedXades.docx` in Word.
    text: Open `SignedXades.docx` in Word.
  - name: Click **File → Info → View signatures**.
    text: Click **File → Info → View signatures**.
  - name: Word should display a green checkmark indicating a valid digital signature.
    text: Word should display a green checkmark indicating a valid digital signature.
  type: HowTo
tags:
- digital signature
- Java
- XAdES
title: हस्ताक्षर विकल्प बनाएं और XAdES EPES के साथ एक Word दस्तावेज़ पर हस्ताक्षर
  करें
url: /hi/java/document-security/create-signature-options-and-sign-a-word-doc-with-xades-epes/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Create signature options and sign a Word doc with XAdES EPES

यदि आपको DOCX फ़ाइल के लिए **हस्ताक्षर विकल्प बनाने** की आवश्यकता है, तो यह गाइड आपको Java में XAdES‑EPES स्तर का उपयोग करके Word दस्तावेज़ पर हस्ताक्षर करने का तरीका दिखाता है। आपको एक पूर्ण, चलाने योग्य उदाहरण मिलेगा जो कुछ ही कोड लाइनों में PFX प्रमाणपत्र के साथ Office दस्तावेज़ पर हस्ताक्षर करता है।

ऑफ़िस दस्तावेज़ों पर हस्ताक्षर करना कानूनी कार्यप्रवाह, स्वचालित अनुबंध प्रोसेसिंग, और सुरक्षित दस्तावेज़ विनिमय के लिए एक सामान्य आवश्यकता है। इस ट्यूटोरियल में आप सीखेंगे:

* XAdES‑EPES के लिए `SignatureOptions` को कॉन्फ़िगर करना।
* `DigitalSignatureUtil.sign` को कॉल करके **Word दस्तावेज़ पर हस्ताक्षर** करना।
* प्रमाणपत्र लोडिंग और पासवर्ड त्रुटियों जैसी सामान्य समस्याओं को संभालना।

> **Prerequisite** – Java 17 या बाद का संस्करण, GroupDocs.Signature for Java लाइब्रेरी (या एक संगत XAdES लाइब्रेरी), और एक वैध `.pfx` प्रमाणपत्र फ़ाइल।

---

## आपको क्या चाहिए

| आइटम | कारण |
|------|--------|
| Java 17+ | आधुनिक भाषा सुविधाएँ और बेहतर सुरक्षा API |
| GroupDocs.Signature for Java (or equivalent) | `SignatureOptions`, `XmlDsigLevel`, और `DigitalSignatureUtil` प्रदान करता है |
| एक PFX प्रमाणपत्र (`.pfx`) | डिजिटल हस्ताक्षर के लिए निजी कुंजी प्रदान करता है |
| प्रमाणपत्र का पासवर्ड | निजी कुंजी को अनलॉक करने के लिए आवश्यक |
| एक अनहस्ताक्षरित DOCX फ़ाइल (`Unsigned.docx`) | स्रोत दस्तावेज़ जिसे आप **ऑफ़िस दस्तावेज़ पर हस्ताक्षर** करना चाहते हैं |

सुनिश्चित करें कि लाइब्रेरी JAR आपके क्लासपाथ पर है:

```bash
# Example using Maven
mvn dependency:copy -Dartifact=com.groupdocs:groupdocs-signature:23.3
```

---

## चरण 1: आवश्यक क्लासेस इम्पोर्ट करें

हस्ताक्षर और फ़ाइल I/O को संभालने वाली क्लासेस को इम्पोर्ट करके शुरू करें।

```java
import com.groupdocs.signature.SignatureOptions;
import com.groupdocs.signature.XmlDsigLevel;
import com.groupdocs.signature.DigitalSignatureUtil;
import java.io.IOException;
```

ये इम्पोर्ट आपको **हस्ताक्षर विकल्प बनाने** के लिए उपयोग किए जाने वाले API तक पहुँच प्रदान करते हैं और वास्तविक हस्ताक्षर ऑपरेशन करने में मदद करते हैं।

---

## चरण 2: हस्ताक्षर विकल्प बनाएं

`SignatureOptions` ऑब्जेक्ट में हस्ताक्षर प्रक्रिया के लिए आवश्यक सभी कॉन्फ़िगरेशन होते हैं, जैसे हस्ताक्षर स्तर, दृश्य रूप, और टाइमस्टैम्प सेटिंग्स।

```java
// Step 2: Create signature options
SignatureOptions signatureOptions = new SignatureOptions();
```

एक नया `SignatureOptions` इंस्टेंस बनाना **docx फ़ाइलों पर हस्ताक्षर करने** का पहला कदम है क्योंकि यह प्रत्येक हस्ताक्षर अनुरोध को अलग करता है, जिससे दस्तावेज़ों के बीच साइड इफ़ेक्ट्स नहीं होते।

---

## चरण 3: XAdES EPES हस्ताक्षर स्तर निर्दिष्ट करें

XAdES‑EPES (Explicit Policy-based Electronic Signature) ऑफिस दस्तावेज़ हस्ताक्षरों के लिए व्यापक रूप से स्वीकृत नीति है। स्तर सेट करने से लाइब्रेरी को पता चलता है कि कौन सा क्रिप्टोग्राफ़िक प्रोफ़ाइल उपयोग करना है।

```java
// Step 3: Specify the XAdES EPES signature level
signatureOptions.setXmlDsigLevel(XmlDsigLevel.XAdES_EPES);
```

क्यों XAdES‑EPES? यह हस्ताक्षर नीति को सीधे हस्ताक्षर में एम्बेड करता है, जिससे हस्ताक्षरित दस्तावेज़ स्व-समाहित और कई e‑signature नियमों के अनुरूप बनता है।

---

## चरण 4: DOCX फ़ाइल पर हस्ताक्षर करें

अब `DigitalSignatureUtil.sign` को कॉल करें। यह मेथड स्रोत फ़ाइल को पढ़ता है, हस्ताक्षर लागू करता है, और हस्ताक्षरित आउटपुट लिखता है।

```java
// Step 4: Sign the document using the provided certificate
try {
    DigitalSignatureUtil.sign(
        "YOUR_DIRECTORY/Unsigned.docx",   // input file
        "YOUR_DIRECTORY/SignedXades.docx", // output file
        "YOUR_DIRECTORY/mycert.pfx",      // certificate file
        "password",                       // certificate password
        signatureOptions                  // options configured above
    );
    System.out.println("Document signed successfully: SignedXades.docx");
} catch (IOException e) {
    System.err.println("Failed to sign the document: " + e.getMessage());
}
```

**आंतरिक प्रक्रिया क्या है?**  
1. लाइब्रेरी `.pfx` फ़ाइल को लोड करती है और प्रदान किए गए पासवर्ड से निजी कुंजी निकालती है।  
2. यह XAdES‑EPES प्रोफ़ाइल से मेल खाने वाली XML‑DSig संरचना बनाती है।  
3. हस्ताक्षर को DOCX पैकेज में एम्बेड किया जाता है, मूल दस्तावेज़ लेआउट को संरक्षित रखते हुए।  

यदि प्रमाणपत्र पासवर्ड गलत है या फ़ाइल पढ़ी नहीं जा सकती, तो `IOException` फेंका जाता है, जिसे आपको दिखाए अनुसार संभालना चाहिए।

---

## चरण 5: हस्ताक्षरित दस्तावेज़ की जाँच करें (वैकल्पिक)

हस्ताक्षर करने के बाद, आप यह पुष्टि करना चाह सकते हैं कि हस्ताक्षर मौजूद है और वैध है। GroupDocs एक वेरिफिकेशन API प्रदान करता है, लेकिन एक त्वरित मैनुअल जाँच Microsoft Word के साथ की जा सकती है:

1. `SignedXades.docx` को Word में खोलें।  
2. **File → Info → View signatures** पर क्लिक करें।  
3. Word को एक हरा टिक दिखाना चाहिए जो वैध डिजिटल हस्ताक्षर दर्शाता है।

लाइब्रेरी के साथ स्वचालित जाँच इस प्रकार दिखती है:

```java
import com.groupdocs.signature.VerificationResult;

VerificationResult result = DigitalSignatureUtil.verify(
    "YOUR_DIRECTORY/SignedXades.docx",
    signatureOptions
);

if (result.isSuccessful()) {
    System.out.println("Signature verification succeeded.");
} else {
    System.out.println("Signature verification failed: " + result.getErrorMessage());
}
```

वेरिफिकेशन स्टेप चलाने से आपको प्रोग्रामेटिक भरोसा मिलता है कि **ऑफ़िस दस्तावेज़ पर हस्ताक्षर** सफल रहा।

---

## पूर्ण, चलाने योग्य उदाहरण

सभी भागों को एक साथ जोड़ते हुए, यहाँ एक स्व-समाहित Java क्लास है जिसे आप कॉपी, पेस्ट और चलाकर उपयोग कर सकते हैं।

```java
import com.groupdocs.signature.SignatureOptions;
import com.groupdocs.signature.XmlDsigLevel;
import com.groupdocs.signature.DigitalSignatureUtil;
import com.groupdocs.signature.VerificationResult;
import java.io.IOException;

/**
 * Demonstrates how to create signature options and sign a DOCX file with XAdES EPES.
 */
public class XadesSignatureDemo {

    public static void main(String[] args) {
        // Paths – update these to match your environment
        String inputPath = "YOUR_DIRECTORY/Unsigned.docx";
        String outputPath = "YOUR_DIRECTORY/SignedXades.docx";
        String certPath = "YOUR_DIRECTORY/mycert.pfx";
        String certPassword = "password";

        // 1️⃣ Create signature options
        SignatureOptions signatureOptions = new SignatureOptions();

        // 2️⃣ Set XAdES EPES level
        signatureOptions.setXmlDsigLevel(XmlDsigLevel.XAdES_EPES);

        // 3️⃣ Sign the document
        try {
            DigitalSignatureUtil.sign(inputPath, outputPath, certPath, certPassword, signatureOptions);
            System.out.println("Document signed successfully: " + outputPath);
        } catch (IOException e) {
            System.err.println("Signing failed: " + e.getMessage());
            return;
        }

        // 4️⃣ (Optional) Verify the signature
        VerificationResult verification = DigitalSignatureUtil.verify(outputPath, signatureOptions);
        if (verification.isSuccessful()) {
            System.out.println("Signature verification succeeded.");
        } else {
            System.out.println("Signature verification failed: " + verification.getErrorMessage());
        }
    }
}
```

**अपेक्षित आउटपुट**

```
Document signed successfully: YOUR_DIRECTORY/SignedXades.docx
Signature verification succeeded.
```

यदि कुछ भी गलत होता है, तो कंसोल एक स्पष्ट त्रुटि संदेश दिखाएगा, जिससे आप प्रमाणपत्र या फ़ाइल‑पाथ समस्याओं का समाधान कर सकेंगे।

---

## सामान्य प्रश्न और किनारे‑के‑केस हैंडलिंग

| प्रश्न | उत्तर |
|----------|--------|
| **क्या मैं एक अलग हस्ताक्षर स्तर उपयोग कर सकता हूँ?** | हां। `XmlDsigLevel.XAdES_EPES` को `XAdES_BES`, `XAdES_T` आदि से बदलें, जो अनुपालन आवश्यकताओं पर निर्भर करता है। |
| **अगर मेरा प्रमाणपत्र .pfx फ़ाइल के बजाय keystore में संग्रहीत है तो क्या करें?** | `KeyStore` को मैन्युअल रूप से लोड करें, `PrivateKey` और `Certificate` निकालें, फिर उन्हें `sign` के उस ओवरलोड को पास करें जो `KeyStore` ऑब्जेक्ट स्वीकार करता है। |
| **मैं एक दृश्यमान हस्ताक्षर छवि कैसे जोड़ूँ?** | `sign` को कॉल करने से पहले `signatureOptions.setSignatureImage("path/to/image.png")` का उपयोग करें। |
| **क्या हस्ताक्षर प्रक्रिया थ्रेड‑सेफ है?** | `DigitalSignatureUtil.sign` मेथड स्टेटलेस है; आप इसे कई थ्रेड्स से सुरक्षित रूप से कॉल कर सकते हैं बशर्ते प्रत्येक थ्रेड अपना `SignatureOptions` इंस्टेंस उपयोग करे। |
| **अगर DOCX में पहले से मौजूद हस्ताक्षर हैं तो क्या होगा?** | लाइब्रेरी एक नया हस्ताक्षर पैकेज एंट्री जोड़ देगा, पहले के हस्ताक्षरों को संरक्षित रखते हुए। यदि आवश्यक हो तो जाँचें कि हस्ताक्षर नीति कई हस्ताक्षरों की अनुमति देती है या नहीं। |

---

## टिप्स और सर्वोत्तम प्रथाएँ (E‑E‑A‑T)

* **Pro tip:** अपने प्रमाणपत्र पासवर्ड को हार्ड‑कोड करने के बजाय एक सुरक्षित वॉल्ट (जैसे Azure Key Vault) में संग्रहित करें।  
* **Watch out for:** Windows (`\`) और Unix (`/`) पर फ़ाइल पाथ सेपरेटर। प्लेटफ़ॉर्म‑स्वतंत्र पाथ बनाने के लिए `Paths.get(...)` का उपयोग करें।  
* **Performance:** बड़े DOCX फ़ाइलों पर हस्ताक्षर I/O‑बाउंड हो सकता है; यदि आप बैच में कई दस्तावेज़ प्रोसेस करते हैं तो इनपुट फ़ाइल को स्ट्रीम करने पर विचार करें।  
* **Compliance:** XAdES‑EPES EU eIDAS नियमावली के अनुरूप है; हस्ताक्षर स्तर चुनने से पहले अपने स्थानीय कानूनी आवश्यकताओं की जाँच करें।

---

## निष्कर्ष

इस ट्यूटोरियल में आपने Java का उपयोग करके XAdES‑EPES स्तर के साथ **हस्ताक्षर विकल्प बनाने** और **Word दस्तावेज़ पर हस्ताक्षर करने** का तरीका सीखा। पूर्ण उदाहरण में प्रमाणपत्र लोडिंग, विकल्प कॉन्फ़िगरेशन, हस्ताक्षर कॉल, और वैकल्पिक वेरिफिकेशन शामिल है, जो आपको प्रोडक्शन में **docx फ़ाइलों पर हस्ताक्षर करने** के लिए एक तैयार समाधान प्रदान करता है।

## आगे आप क्या सीखें?

निम्नलिखित ट्यूटोरियल्स उन निकट संबंधित विषयों को कवर करते हैं जो इस गाइड में दिखाए गए तकनीकों पर आधारित हैं। प्रत्येक संसाधन में पूर्ण कार्यशील कोड उदाहरण और चरण‑दर‑चरण व्याख्याएँ शामिल हैं, जो आपको अतिरिक्त API फीचर्स में महारत हासिल करने और अपने प्रोजेक्ट्स में वैकल्पिक कार्यान्वयन दृष्टिकोणों का अन्वेषण करने में मदद करेंगे।

- [Java में लोड विकल्प बनाएं – गायब फ़ॉन्ट्स का पता लगाएँ और DOCX कैसे लोड करें](/words/english/java/document-loading-and-saving/create-load-options-in-java-detect-missing-fonts-how-to-load/)
- [Aspose.Words for Java में दस्तावेज़ विकल्प और सेटिंग्स का उपयोग](/words/english/java/document-manipulation/using-document-options-and-settings/)
- [Aspose.Words for Java का उपयोग करके रीड‑ओनली दस्तावेज़ों में संपादन योग्य रेंज कैसे बनाएं](/words/english/java/security-protection/editable-ranges-aspose-words-java/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}