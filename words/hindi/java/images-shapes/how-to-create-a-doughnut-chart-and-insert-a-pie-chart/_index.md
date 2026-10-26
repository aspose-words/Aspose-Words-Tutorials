---
category: general
date: 2026-10-26
description: जावा में चरण-दर-चरण कोड के साथ डोनट चार्ट बनाएं और पाई चार्ट सम्मिलित
  करें। लचीले चार्ट विज़ुअलाइज़ेशन के लिए पूर्ण कार्यप्रवाह सीखें।
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create doughnut chart
- insert pie chart
- Java chart library
- chart customization Java
- data visualization Java
language: hi
lastmod: 2026-10-26
og_description: जावा में डोनट चार्ट बनाने के लिए इस गाइड का उपयोग करें, जो लचीले विज़ुअलाइज़ेशन
  के लिए पाई चार्ट कैसे डालें, यह भी दिखाता है।
og_image_alt: Java code snippet creating a doughnut chart and inserting a pie chart
og_title: डोनट चार्ट बनाएं और पाई चार्ट सम्मिलित करें – जावा गाइड
schemas:
- author: Aspose
  dateModified: '2026-10-26'
  description: Create doughnut chart and insert pie chart in Java with step‑by‑step
    code. Learn the full workflow for flexible chart visualizations.
  headline: How to create a doughnut chart and insert a pie chart
  type: TechArticle
tags:
- chart
- Java
- data‑visualization
title: डोनट चार्ट कैसे बनाएं और पाई चार्ट डालें
url: /hi/java/images-shapes/how-to-create-a-doughnut-chart-and-insert-a-pie-chart/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# डोनट चार्ट कैसे बनाएं और पाई चार्ट सम्मिलित करें

यदि आपको Java में **डोनट चार्ट बनाना** है, तो यह ट्यूटोरियल आपको सटीक चरणों के माध्यम से ले जाएगा। हम यह भी दिखाएंगे कि कैसे **पाई चार्ट सम्मिलित करें** उसी बिल्डर API का उपयोग करके, ताकि आप दृश्य शैलियों के बीच आसानी से स्विच कर सकें। गाइड के अंत तक आपके पास एक पूर्ण, चलाने योग्य प्रोग्राम होगा जो दोनों चार्ट प्रकार बनाता है और सामान्य अनुकूलन दिखाता है।

इस ट्यूटोरियल में शामिल हैं:

* चुनी गई लाइब्रेरी द्वारा प्रदान किए गए चार्ट बिल्डर को प्रारंभ करना।  
* डोनट चार्ट बनाना और होल साइज कॉन्फ़िगर करना।  
* पाई चार्ट सम्मिलित करना और ज़ोर देने के लिए एक स्लाइस को एक्सप्लोड करना।  
* गुम सीरीज़ या असमर्थित चार्ट प्रकार जैसी किनारी स्थितियों को संभालने के टिप्स।  

आपको केवल एक नवीनतम JDK (8 या बाद का) और क्लासपाथ पर चार्ट लाइब्रेरी JAR की आवश्यकता है। कोई बाहरी सेवाएँ आवश्यक नहीं हैं।

---

## पूर्वापेक्षाएँ

| आइटम | कारण |
|------|--------|
| Java Development Kit (JDK) 8+ | उदाहरण को संकलित और चलाने के लिए आवश्यक। |
| Chart library (e.g., **Aspose.Cells for Java** or **JFreeChart**) | कोड में उपयोग किए गए `ChartBuilder`, `ChartType`, और सीरीज़ हेरफेर मेथड्स प्रदान करता है। |
| An IDE or a text editor | Java स्रोत फ़ाइल लिखने और निष्पादित करने के लिए। |

सुनिश्चित करें कि लाइब्रेरी JAR आपके प्रोजेक्ट के बिल्ड पाथ में जोड़ी गई है। यदि आप Maven का उपयोग करते हैं, तो उपयुक्त डिपेंडेंसी जोड़ें; अन्यथा, JAR को `libs` फ़ोल्डर में रखें और संकलन के दौरान इसका संदर्भ दें।

## चरण 1: चार्ट बिल्डर सेट अप करें

पहला चरण `ChartBuilder` (या समकक्ष) का एक इंस्टेंस बनाना है जो चार्ट ऑब्जेक्ट्स उत्पन्न करेगा। यह ऑब्जेक्ट एक फ़ैक्टरी के रूप में कार्य करता है और उस वर्कशीट या कैनवास को रखता है जहाँ चार्ट रखा जाएगा।

```java
import com.aspose.cells.*;

public class DoughnutAndPieDemo {
    public static void main(String[] args) throws Exception {
        // Create a new workbook to host the charts
        Workbook workbook = new Workbook();
        Worksheet sheet = workbook.getWorksheets().get(0);

        // Initialize the chart builder with the worksheet
        ChartBuilder builder = new ChartBuilder(sheet);
```

**यह क्यों महत्वपूर्ण है:**  
बिल्डर चार्ट को एक विशिष्ट वर्कशीट से जोड़ता है, जिससे सभी बाद के चार्ट ऑब्जेक्ट्स समान ड्राइंग सतह साझा करते हैं। इस चरण को छोड़ने से विज़ुअल तत्वों के लिए लक्ष्य स्थान नहीं रहेगा।

## चरण 2: **डोनट चार्ट बनाएं**

अब हम एक निर्धारित आकार के साथ डोनट चार्ट बनाते हैं। होल साइज निर्धारित करता है कि चार्ट के केंद्र में कितना हिस्सा खाली रहेगा, जिससे सामान्य पाई को डोनट में बदला जाता है।

```java
        // Insert a doughnut chart with a width of 500 and height of 350
        Chart doughnutChart = builder.insertChart(ChartType.DOUGHNUT, 500, 350);

        // Set the hole size to 30% of the chart radius
        doughnutChart.getDoughnutChart().setHoleSize(30);

        // Add sample data series
        doughnutChart.getNSeries().add("{10, 20, 30, 40}", true);
```

**व्याख्या:**  

* `insertChart(ChartType.DOUGHNUT, 500, 350)` चार्ट ऑब्जेक्ट बनाता है और वर्कशीट पर स्थान आरक्षित करता है।  
* `setHoleSize(30)` पाई को 30 % खाली केंद्र के साथ डोनट में बदलता है।  
* `add("{10, 20, 30, 40}", true)` चार डेटा पॉइंट प्रदान करता है; `true` फ़्लैग लाइब्रेरी को बताता है कि मानों को एकल सीरीज़ के रूप में माना जाए।  

**किनारी स्थिति:** यदि चयनित चार्ट प्रकार में होल का समर्थन नहीं है (जैसे बार चार्ट), तो `getDoughnutChart()` को कॉल करने पर अपवाद उत्पन्न होता है। होल साइज समायोजित करने से पहले हमेशा चार्ट प्रकार की पुष्टि करें।

## चरण 3: **पाई चार्ट सम्मिलित करें**

डोनट तैयार होने के बाद, हम वही बिल्डर का उपयोग करके **पाई चार्ट सम्मिलित करना** दिखाते हैं। यह चरण दोनों चार्ट प्रकारों के बीच समानता को उजागर करता है और दिखाता है कि स्लाइस को कैसे ज़ोर दिया जाए।

```java
        // Insert a pie chart next to the doughnut
        Chart pieChart = builder.insertChart(ChartType.PIE, 400, 300);

        // Add the same data series for consistency
        pieChart.getNSeries().add("{10, 20, 30, 40}", true);

        // Explode the first slice by 10% to draw attention
        pieChart.getSeries().get(0).setExplode(10);
```

**व्याख्या:**  

* `ChartType.PIE` बिल्डर को क्लासिक पाई चार्ट बनाने के लिए बताता है।  
* `setExplode(10)` पहले स्लाइस को त्रिज्या के 10 % से ऑफ़सेट करता है, जो मुख्य डेटा पॉइंट को उजागर करने की एक सामान्य तकनीक है।  

**टिप:** `setExplode` मेथड केवल पाई चार्ट की पहली सीरीज़ पर काम करता है। यदि आपके पास कई सीरीज़ हैं, तो आपको सही इंडेक्स को लक्षित करना होगा।

## चरण 4: वर्कबुक सहेजें

अंत में, वर्कबुक को फ़ाइल में लिखें ताकि आप चार्ट को Excel या किसी भी संगत व्यूअर में देख सकें।

```java
        // Save the workbook to a file
        workbook.save("DoughnutAndPieChart.xlsx");
        System.out.println("Workbook created with doughnut and pie charts.");
    }
}
```

**अब सहेजना क्यों आवश्यक है:**  
वर्कबुक को स्थायी बनाना सभी ड्राइंग ऑपरेशन्स को अंतिम रूप देता है। सहेजने से पहले फ़ाइल को देखने का प्रयास करने पर एक खाली या अधूरी दस्तावेज़ प्राप्त होता है।

**परिणाम:** *DoughnutAndPieChart.xlsx* खोलने पर बाएँ तरफ 30 % होल वाला डोनट चार्ट और दाएँ तरफ एक्सप्लोडेड पहली स्लाइस वाला पाई चार्ट दिखता है।

## चरण 5: सामान्य विविधताएँ और समस्या निवारण

| स्थिति | समायोजन |
|-----------|------------|
| **विभिन्न चार्ट आयाम** | `insertChart` में चौड़ाई और ऊँचाई के तर्क बदलें। |
| **एकाधिक डेटा सीरीज़** | `add` को कई बार कॉल करें या 2‑D एरे स्ट्रिंग पास करें। |
| **डायनामिक होल साइज** | डेटा रेंज के आधार पर होल साइज गणना करें, फिर `setHoleSize` को कॉल करें। |
| **कई स्लाइस एक्सप्लोड करें** | प्रत्येक स्लाइस को ऑफ़सेट करने के लिए `chart.getSeries().get(i).setExplode(percent)` के माध्यम से लूप करें। |
| **लाइब्रेरी डोनट का समर्थन नहीं करती** | पाई चार्ट का उपयोग करें और मैन्युअली एक सफ़ेद सर्कल ओवरले ड्रॉ करें, हालांकि यह कम सटीक है। |

**प्रो टिप:** बड़े वर्कबुक के साथ काम करते समय चार्ट सम्मिलित करने के बाद हमेशा `builder.flush()` (यदि उपलब्ध हो) को कॉल करें। यह आंतरिक बफ़र्स को रिलीज़ करता है और मेमोरी लीक को रोकता है।

![डोनट चार्ट बनाते और पाई चार्ट सम्मिलित करते हुए Java कोड](https://example.com/images/doughnut-pie-java.png "Java में डोनट चार्ट बनाने का उदाहरण")

*छवि अंतिम वर्कबुक लेआउट को दोनों चार्टों के साथ साइड बाय साइड दर्शाती है।*

## निष्कर्ष

अब आप Java में एक फ्लुएंट बिल्डर API का उपयोग करके **डोनट चार्ट बनाना** और **पाई चार्ट सम्मिलित करना** जानते हैं। पूरा उदाहरण प्रारंभिककरण, आकार कॉन्फ़िगरेशन, होल साइजिंग, स्लाइस एक्सप्लोजन, और फ़ाइल आउटपुट को कवर करता है। अब आप रंग, लेजेंड, और डेटा लेबल जैसी अतिरिक्त अनुकूलन का अन्वेषण कर सकते हैं ताकि आपकी रिपोर्टिंग आवश्यकताओं के अनुरूप हो।

**अगले कदम**

* **chart customization Java** जैसी विशेषताओं जैसे ग्रेडिएंट फ़िल्स और डेटा लेबल के साथ प्रयोग करें।  
* चार्ट जनरेशन को एक वेब सर्विस में एकीकृत करें जो मांग पर वर्कबुक लौटाए।  
* अपने प्रोजेक्ट के लिए सबसे उपयुक्त विकल्प चुनने हेतु बिल्डर अप्रोच की तुलना अन्य लाइब्रेरी (जैसे JFreeChart) से करें।

शुभ चार्टिंग!

## आपको आगे क्या सीखना चाहिए?

निम्नलिखित ट्यूटोरियल्स इस गाइड में प्रदर्शित तकनीकों पर आधारित निकटतम संबंधित विषयों को कवर करते हैं। प्रत्येक संसाधन में पूर्ण कार्यशील कोड उदाहरण और चरण-दर-चरण व्याख्याएँ शामिल हैं जो आपको अतिरिक्त API सुविधाओं में निपुण बनने और अपने प्रोजेक्ट में वैकल्पिक कार्यान्वयन दृष्टिकोणों का अन्वेषण करने में मदद करती हैं।

- [Java के साथ Word दस्तावेज़ में डोनट चार्ट कैसे बनाएं](/words/english/java/images-shapes/how-to-create-doughnut-chart-in-a-word-document-with-java/)
- [Java में डोनट चार्ट संपादित करने के बाद Word दस्तावेज़ सहेजें](/words/english/java/using-document-elements/save-word-document-after-editing-doughnut-chart-in-java/)
- [Java में पाई चार्ट सम्मिलित करें – एक्सप्लोड, रोटेट और स्लाइस को हाइलाइट करें](/words/english/java/images-shapes/insert-pie-chart-in-java-explode-rotate-highlight-slices/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}