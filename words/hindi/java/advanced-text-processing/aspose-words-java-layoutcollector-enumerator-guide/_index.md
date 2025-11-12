---
date: '2025-11-12'
description: Aspose.Words for Java के LayoutCollector और LayoutEnumerator का उपयोग
  करके पृष्ठांकन का विश्लेषण करना, दस्तावेज़ लेआउट को पार करना, लेआउट कॉलबैक लागू
  करना, और निरंतर अनुभागों में पृष्ठ क्रमांक को पुनः शुरू करना सीखें।
keywords:
- Aspose.Words Java LayoutCollector
- Java document layout management
- LayoutEnumerator traversal
- analyze pagination java
- use layoutcollector page span
- traverse document layout
- restart page numbering sections
- implement layout callback
language: hi
title: Aspose.Words लेआउट टूल्स के साथ जावा पेजिनेशन विश्लेषण
url: /java/advanced-text-processing/aspose-words-java-layoutcollector-enumerator-guide/
weight: 1
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Java पेजिनेशन विश्लेषण Aspose.Words लेआउट टूल्स के साथ

## परिचय  

यदि आपको Java एप्लिकेशन में **पेजिनेशन का विश्लेषण** करना है या **दस्तावेज़ के लेआउट को पार करना** है, तो Aspose.Words for Java दो शक्तिशाली APIs प्रदान करता है: **`LayoutCollector`** और **`LayoutEnumerator`**। ये क्लासेज़ आपको यह पता लगाने देती हैं कि कोई नोड कितने पृष्ठों पर फैला है, प्रत्येक लेआउट इकाई के माध्यम से चलें, लेआउट इवेंट्स पर प्रतिक्रिया दें, और यहाँ तक कि निरंतर सेक्शन में पेज नंबरिंग को पुनः शुरू कर सकें। इस गाइड में हम प्रत्येक फीचर को चरण‑बद्ध तरीके से देखेंगे, वास्तविक कोड स्निपेट्स दिखाएंगे, और अपेक्षित परिणाम समझाएंगे ताकि आप इन्हें तुरंत लागू कर सकें।

आप सीखेंगे:

* **LayoutCollector** का उपयोग करके किसी भी नोड का प्रारंभ और समाप्ति पृष्ठ प्राप्त करना (use layoutcollector page span)  
* **LayoutEnumerator** के साथ दस्तावेज़ लेआउट को पार करना (traverse document layout)  
* पेजिनेशन इवेंट्स पर प्रतिक्रिया देने के लिए **लेआउट कॉलबैक** लागू करना (implement layout callback)  
* निरंतर सेक्शन में **पेज नंबरिंग को पुनः शुरू** करना (restart page numbering sections)  

आइए शुरू करते हैं।

## पूर्वापेक्षाएँ  

### आवश्यक लाइब्रेरीज़  

| निर्माण उपकरण | निर्भरता |
|------------|------------|
| **Maven** | ```xml<br><dependency><groupId>com.aspose</groupId><artifactId>aspose-words</artifactId><version>25.3</version></dependency>``` |
| **Gradle** | ```gradle<br>implementation 'com.aspose:aspose-words:25.3'``` |

> **नोट:** संस्करण संख्या संगतता के लिए रखी गई है; कोड किसी भी हालिया Aspose.Words for Java रिलीज़ के साथ काम करता है।

### पर्यावरण  

* JDK 8 या उससे नया  
* IntelliJ IDEA या Eclipse जैसे IDE  

### ज्ञान  

बुनियादी Java प्रोग्रामिंग और Maven/Gradle की परिचितता उदाहरणों को समझने के लिए पर्याप्त है।

## Aspose.Words की सेटअप  

कोई भी लेआउट API कॉल करने से पहले लाइब्रेरी को लाइसेंस (या ट्रायल मोड) में होना आवश्यक है। नीचे दिया गया स्निपेट न्यूनतम इनिशियलाइज़ेशन दिखाता है:

```java
import com.aspose.words.*;

public class SetupAsposeWords {
    public static void main(String[] args) throws Exception {
        // Load your license file – skip this line for a trial evaluation
        License license = new License();
        license.setLicense("path/to/your/license.lic");

        System.out.println("Aspose.Words is ready to use!");
    }
}
```

*यह कोड किसी दस्तावेज़ को संशोधित नहीं करता; यह केवल Aspose वातावरण तैयार करता है।*  

अब हम मुख्य फीचर्स में डुबकी लगाते हैं।

## फीचर 1: **LayoutCollector** का उपयोग करके पेजिनेशन का विश्लेषण  

`LayoutCollector` प्रत्येक नोड को उस पृष्ठ(पृष्ठों) से मैप करता है जिस पर वह स्थित है। यह **layoutcollector page span** का उपयोग करके पेजिनेशन विश्लेषण करने का सबसे भरोसेमंद तरीका है।

### चरण‑बद्ध कार्यान्वयन  

1. **एक नया दस्तावेज़ बनाएं और LayoutCollector संलग्न करें।**  
2. **ऐसी सामग्री जोड़ें जो पेजिनेशन को मजबूर करे** (जैसे पेज ब्रेक, सेक्शन ब्रेक)।  
3. **`updatePageLayout()`** के साथ लेआउट को रीफ़्रेश करें।  
4. **कलेक्टर** से प्रारंभ पृष्ठ, समाप्ति पृष्ठ, और कुल पृष्ठों की जानकारी प्राप्त करें।

#### 1️⃣ Document और LayoutCollector को इनिशियलाइज़ करें  

```java
Document doc = new Document();                 // Empty document
LayoutCollector layoutCollector = new LayoutCollector(doc);
```

#### 2️⃣ दस्तावेज़ को भरें  

```java
DocumentBuilder builder = new DocumentBuilder(doc);
builder.write("Section 1");
builder.insertBreak(BreakType.PAGE_BREAK);
builder.insertBreak(BreakType.SECTION_BREAK_EVEN_PAGE);
builder.write("Section 2");
builder.insertBreak(BreakType.PAGE_BREAK);
```

#### 3️⃣ लेआउट अपडेट करें और मेट्रिक्स प्राप्त करें  

```java
layoutCollector.clear();          // Reset any previous mappings
doc.updatePageLayout();           // Force pagination calculation

int pagesSpanned = layoutCollector.getNumPagesSpanned(doc);
assert pagesSpanned == 5;         // Expected: the document occupies 5 pages
System.out.println("Document spans " + pagesSpanned + " pages.");
```

**अपेक्षित आउटपुट**

```
Document spans 5 pages.
```

> **यह क्यों काम करता है:** `updatePageLayout()` Aspose.Words को लेआउट पुनः गणना करने के लिए मजबूर करता है, जिसके बाद `LayoutCollector` सटीक पेज स्पैन रिपोर्ट कर सकता है।

## फीचर 2: **LayoutEnumerator** के साथ दस्तावेज़ लेआउट को पार करना  

जब आपको **दस्तावेज़ लेआउट को पार** करना हो (जैसे कस्टम रेंडरिंग या विश्लेषण के लिए), `LayoutEnumerator` पृष्ठों, पैराग्राफ़, लाइनों और शब्दों का ट्री‑समान दृश्य प्रदान करता है।

### चरण‑बद्ध कार्यान्वयन  

1. लेआउट इकाइयों वाले मौजूदा दस्तावेज़ को लोड करें।  
2. `LayoutEnumerator` का एक इंस्टेंस बनाएं।  
3. रूट `PAGE` इकाई पर जाएँ।  
4. पुनरावर्ती हेल्पर मेथड्स का उपयोग करके लेआउट को आगे और पीछे चलें।

#### 1️⃣ दस्तावेज़ लोड करें और Enumerator बनाएं  

```java
Document doc = new Document("YOUR_DOCUMENT_DIRECTORY/Layout entities.docx");
LayoutEnumerator layoutEnumerator = new LayoutEnumerator(doc);
```

#### 2️⃣ पेज लेवल पर पोज़िशन करें  

```java
layoutEnumerator.moveParent(LayoutEntityType.PAGE);
```

#### 3️⃣ आगे की यात्रा (Depth‑First)  

```java
traverseLayoutForward(layoutEnumerator, 1);
```

#### 4️⃣ पीछे की यात्रा  

```java
traverseLayoutBackward(layoutEnumerator, 1);
```

> **हेल्पर मेथड्स** (`traverseLayoutForward` / `traverseLayoutBackward`) को पुनरावर्ती रूप से लागू किया गया है ताकि प्रत्येक चाइल्ड इकाई का प्रकार और पेज इंडेक्स प्रिंट किया जा सके। आप इन्हें आँकड़े एकत्र करने, ग्राफ़िक्स रेंडर करने, या लेआउट प्रॉपर्टीज़ बदलने के लिए अनुकूलित कर सकते हैं।

## फीचर 3: **Layout Callbacks** को लागू करना  

कभी‑कभी आपको तब प्रतिक्रिया देनी होती है जब Aspose.Words दस्तावेज़ के किसी भाग का लेआउट समाप्त हो जाता है। `IPageLayoutCallback` को लागू करके आप **layout callback** लॉजिक बना सकते हैं, जैसे प्रत्येक पृष्ठ को इमेज के रूप में सेव करना।

### चरण‑बद्ध कार्यान्वयन  

1. दस्तावेज़ के `LayoutOptions` में एक कॉलबैक इंस्टेंस असाइन करें।  
2. कॉलबैक के भीतर `PART_REFLOW_FINISHED` और `CONVERSION_FINISHED` इवेंट्स को हैंडल करें।  
3. `ImageSaveOptions` का उपयोग करके वर्तमान पृष्ठ को PNG में रेंडर करें।

#### 1️⃣ कॉलबैक रजिस्टर करें  

```java
doc.getLayoutOptions().setCallback(new RenderPageLayoutCallback());
doc.updatePageLayout();                     // Triggers the callback events
```

#### 2️⃣ कॉलबैक क्लास  

```java
private static class RenderPageLayoutCallback implements IPageLayoutCallback {
    public void notify(PageLayoutCallbackArgs a) throws Exception {
        if (a.getEvent() == PageLayoutEvent.PART_REFLOW_FINISHED) {
            notifyPartFinished(a);
        } else if (a.getEvent() == PageLayoutEvent.CONVERSION_FINISHED) {
            notifyConversionFinished(a);
        }
    }

    private void renderPage(PageLayoutCallbackArgs a, int pageIndex) throws Exception {
        ImageSaveOptions saveOptions = new ImageSaveOptions(SaveFormat.PNG);
        saveOptions.setPageSet(new PageSet(pageIndex));

        try (FileOutputStream stream = new FileOutputStream(
                "YOUR_ARTIFACTS_DIR/PageLayoutCallback.page-" + (pageIndex + 1) + ".png")) {
            a.getDocument().save(stream, saveOptions);
        }
    }

    // You can add custom logic here for partFinished / conversionFinished
}
```

**क्या होता है:** हर बार जब कोई लेआउट भाग रीफ़्लो समाप्त करता है, कॉलबैक उस पृष्ठ को PNG फ़ाइल में रेंडर करता है, जिससे आपको पेजिनेशन प्रक्रिया का दृश्य ट्रेस मिलता है।

## फीचर 4: निरंतर सेक्शन में **पेज नंबरिंग को पुनः शुरू** करना  

जब दस्तावेज़ में निरंतर सेक्शन होते हैं, आप चाह सकते हैं कि पेज नंबर केवल नई भौतिक पृष्ठ पर ही रीसेट हों। यह `ContinuousSectionRestart` सेटिंग से प्राप्त किया जाता है।

### चरण‑बद्ध कार्यान्वयन  

1. लक्ष्य दस्तावेज़ लोड करें।  
2. `ContinuousSectionPageNumberingRestart` विकल्प बदलें।  
3. परिवर्तन लागू करने के लिए `updatePageLayout()` फिर से चलाएँ।

#### 1️⃣ दस्तावेज़ लोड करें  

```java
Document doc = new Document("YOUR_DOCUMENT_DIRECTORY/Continuous section page numbering.docx");
```

#### 2️⃣ रीस्टार्ट व्यवहार कॉन्फ़िगर करें  

```java
doc.getLayoutOptions()
   .setContinuousSectionPageNumberingRestart(ContinuousSectionRestart.FROM_NEW_PAGE_ONLY);
doc.updatePageLayout();            // Apply the new numbering rule
```

**परिणाम:** अब पेज नंबर केवल नई भौतिक पृष्ठ शुरू होने पर रीसेट होंगे, जिससे रिपोर्ट या पुस्तकों में एक साफ़, पेशेवर लुक बना रहेगा।

## व्यावहारिक अनुप्रयोग  

| परिदृश्य | कौन सा API मदद करता है | लाभ |
|----------|------------------------|------|
| **लंबे अनुबंधों का ऑडिट** | `LayoutCollector` | जल्दी पता लगाएँ कि कौन से क्लॉज़ कई पृष्ठों पर फैले हैं। |
| **कस्टम PDF रेंडरिंग** | `LayoutEnumerator` | लेआउट ट्री को चलाकर प्रत्येक लाइन को वेक्टर ग्राफ़िक्स के रूप में एक्सपोर्ट करें। |
| **लाइव दस्तावेज़ प्रीव्यू** | Layout callbacks | उपयोगकर्ता द्वारा सामग्री संपादित करने पर पेज इमेज ऑन‑द‑फ्लाई जेनरेट करें। |
| **बहु‑सेक्शन रिपोर्ट** | Continuous section restart | मैन्युअल समायोजन के बिना पेज नंबर लॉजिकल रखें। |

## प्रदर्शन टिप्स  

* **`updatePageLayout()`** कॉल करने से पहले अनावश्यक नोड्स को ट्रिम करें – कम तत्वों से पेजिनेशन तेज़ होता है।  
* कई क्वेरीज़ के लिए **एक ही LayoutCollector** को पुनः उपयोग करें, हर बार नया न बनाएं।  
* यदि आपको केवल पेज‑लेवल डेटा चाहिए तो **LayoutEnumerator** के साथ ट्रैवर्सल डेप्थ को सीमित रखें।  
* कॉलबैक उदाहरण में दिखाए अनुसार **स्ट्रीम्स को डिस्पोज़** करें ताकि बड़े दस्तावेज़ों पर मेमोरी लीक न हो।

## निष्कर्ष  

`LayoutCollector`, `LayoutEnumerator`, लेआउट कॉलबैक्स, और निरंतर‑सेक्शन नंबरिंग को महारत हासिल करके आप अब **analyze pagination java**, **traverse document layout**, और **restart page numbering sections** के लिए एक पूर्ण टूलबॉक्स रखते हैं। ये APIs आपको मजबूत, उच्च‑प्रदर्शन टेक्स्ट‑प्रोसेसिंग पाइपलाइन बनाने की अनुमति देती हैं जो हर