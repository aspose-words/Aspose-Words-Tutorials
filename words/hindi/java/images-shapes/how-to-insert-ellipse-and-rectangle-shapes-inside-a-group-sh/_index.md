---
category: general
date: 2026-10-23
description: Aspose.Words का उपयोग करके Word में एलिप्स कैसे डालें और आयताकार आकार
  कैसे जोड़ें, सीखें। इसमें कर्सर को आकार पर ले जाना और समूह आकार कैसे बनाएं, शामिल
  है।
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to insert ellipse
- how to add rectangle
- move cursor to shape
- insert rectangle shape word
- how to create group shape
language: hi
lastmod: 2026-10-23
og_description: Aspose.Words के साथ Word में अण्डाकार (ellipse) कैसे डालें और आयताकार
  (rectangle) आकार कैसे जोड़ें। कर्सर को आकार पर ले जाने और समूह आकार बनाने के लिए
  चरण‑दर‑चरण मार्गदर्शिका का पालन करें।
og_image_alt: Screenshot of a Word document showing a group shape containing a rectangle
  and an ellipse
og_title: Word समूह आकार में अंडाकार और आयताकार आकृतियों को कैसे डालें
schemas:
- author: Aspose
  dateModified: '2026-10-23'
  description: Learn how to insert ellipse and how to add rectangle shape in Word
    using Aspose.Words. Includes move cursor to shape and how to create group shape.
  headline: How to insert ellipse and rectangle shapes inside a group shape with Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: Aspose.Words के साथ समूह आकार के भीतर दीर्घवृत्त और आयताकार आकृतियों को कैसे
  सम्मिलित करें
url: /hi/java/images-shapes/how-to-insert-ellipse-and-rectangle-shapes-inside-a-group-sh/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words के साथ समूह आकार के भीतर दीर्घवृत्त और आयत आकार कैसे डालें

यदि आपको प्रोग्रामेटिक रूप से Word दस्तावेज़ में **दीर्घवृत्त कैसे डालें** पता करना है, तो यह गाइड पूरी प्रक्रिया दिखाता है। आप **आयत आकार कैसे जोड़ें**, **आकार पर कर्सर कैसे ले जाएँ**, और **समूह आकार कैसे बनाएं** जो कई ड्राइंग ऑब्जेक्ट्स को रखता है, यह भी देखेंगे।

Word ऑटोमेशन अक्सर ड्राइंग ऑब्जेक्ट्स की सटीक स्थिति की आवश्यकता रखता है। इस ट्यूटोरियल के अंत तक आप एक `.docx` फ़ाइल बना पाएँगे जिसमें समूहित आयत और दीर्घवृत्त होगा, जिसे आगे स्टाइल या एक्सपोर्ट किया जा सकता है। Aspose.Words for .NET लाइब्रेरी और .NET विकास वातावरण के अलावा कोई बाहरी टूल आवश्यक नहीं है।

## Prerequisites

शुरू करने से पहले सुनिश्चित करें कि आपके पास है:

* .NET 6.0 या बाद का संस्करण स्थापित हो।
* Aspose.Words for .NET (NuGet पैकेज `Aspose.Words`) आपके प्रोजेक्ट में जोड़ा गया हो।
* C# सिंटैक्स और Visual Studio (या किसी भी IDE) का बुनियादी ज्ञान।

ये आवश्यकताएँ कोड को अतिरिक्त कॉन्फ़िगरेशन के बिना कम्पाइल करने में मदद करती हैं।

## Word में समूह आकार कैसे बनाएं

समूह आकार एक कंटेनर की तरह काम करता है जिससे आप कई आकारों को एक इकाई के रूप में ले, घुमा या फॉर्मेट कर सकते हैं। नीचे दिया गया कोड एक विशिष्ट आकार (300 × 200 पॉइंट) के साथ समूह बनाता है और आगे की ड्राइंग ऑपरेशन्स के लिए दस्तावेज़ तैयार करता है।

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class GroupShapeDemo
{
    static void Main()
    {
        // Create a new blank document and a DocumentBuilder.
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Insert a group shape that will act as a container for other shapes.
        GroupShape group = builder.InsertGroupShape(300, 200);
        
        // The group shape is now part of the document.
        // Subsequent shape insertions will be placed inside this group.
```

*Why this step matters*: समूह आकार एक स्थानीय कॉर्डिनेट सिस्टम परिभाषित करता है। समूह में कर्सर ले जाने के बाद जो भी आकार जोड़े जाएंगे, वे समूह के मूल बिंदु के सापेक्ष स्थित होंगे, जिससे लेआउट गणनाएँ सरल हो जाती हैं।

## Word में आयत आकार कैसे जोड़ें

अब जब समूह मौजूद है, आप उसके भीतर **आयत आकार डाल सकते** हैं। आयत पृष्ठभूमि या अन्य सामग्री के लिए एक दृश्य प्लेसहोल्डर के रूप में काम करेगा।

```csharp
        // Move the cursor into the group so that the next shape is added to it.
        builder.MoveTo(group);
        
        // Insert a rectangle of width 100 points and height 50 points.
        builder.InsertShape(ShapeType.Rectangle, 100, 50);
```

*Explanation*: `MoveTo(group)` बिल्डर को बताता है कि सक्रिय इंसर्शन पॉइंट समूह आकार है। कर्सर को समूह में नहीं ले जाने पर, `InsertShape` आयत को मुख्य दस्तावेज़ बॉडी में जोड़ देगा, न कि समूह में।

## दीर्घवृत्त कैसे डालें

आयत स्थापित हो जाने के बाद, अब आप **दीर्घवृत्त कैसे डालें** दिखा सकते हैं। दीर्घवृत्त उसी समूह के भीतर केंद्रित होगा और आवश्यकता अनुसार आयत के ऊपर ओवरलैप करेगा।

```csharp
        // Keep the cursor inside the same group.
        builder.MoveTo(group);
        
        // Insert an ellipse of width 80 points and height 80 points.
        builder.InsertShape(ShapeType.Ellipse, 80, 80);
```

*Why the cursor must be moved*: प्रत्येक `InsertShape` कॉल वर्तमान कर्सर स्थान का सम्मान करती है। `MoveTo(group)` को फिर से कॉल करने से यह सुनिश्चित होता है कि दीर्घवृत्त भी समूह का बच्चा है, जिससे वांछित पदानुक्रम बना रहता है।

## अतिरिक्त ऑब्जेक्ट्स डालने से पहले आकार पर कर्सर ले जाएँ

यदि बाद में आप और आकार जोड़ना चाहते हैं, तो प्रत्येक इंसर्शन से पहले **आकार पर कर्सर ले जाएँ**। यह पैटर्न समूह के बाहर आकस्मिक प्लेसमेंट से बचाता है।

```csharp
        // Example: add a third shape, such as a line.
        builder.MoveTo(group);
        builder.InsertShape(ShapeType.Line, 150, 0);
```

*Tip*: `MoveTo(group)` को पुनः उपयोग करना हल्का होता है और कोड की पठनीयता बढ़ाता है। यह भविष्य में रखरखाव को भी आसान बनाता है क्योंकि इंसर्शन संदर्भ स्पष्ट रहता है।

## दस्तावेज़ को सहेजें

अंत में, दस्तावेज़ को डिस्क पर सहेजें। उदाहरण फ़ाइल को `GroupShape.docx` नाम से आप द्वारा निर्दिष्ट फ़ोल्डर में सहेजता है।

```csharp
        // Save the document to the desired location.
        document.Save(@"C:\Temp\GroupShape.docx");
    }
}
```

जब आप सहेजी गई फ़ाइल को Microsoft Word में खोलेंगे, तो आपको एकल समूह दिखाई देगा जिसमें आयत और दीर्घवृत्त दोनों सही ढंग से स्थित होंगे।

### Expected output

* `GroupShape.docx` नाम की एक `.docx` फ़ाइल।
* दस्तावेज़ के भीतर 300 × 200 पॉइंट आकार का एक समूहित ड्राइंग ऑब्जेक्ट।
* समूह के अंदर:
  * समूह के मूल बिंदु पर स्थित आयत (100 × 50 पॉइंट)।
  * आयत के ऊपर ओवरलैप करने वाला दीर्घवृत्त (80 × 80 पॉइंट)।
  * कर्सर ले जाने के बाद आप द्वारा जोड़े गए कोई भी अतिरिक्त आकार।

## सामान्य विविधताएँ और किनारी स्थितियाँ

| Situation | Recommended approach |
|-----------|----------------------|
| **विभिन्न इकाई आकार** | Aspose.Words पॉइंट्स (1 pt = 1/72 in) का उपयोग करता है। `InsertShape` कॉल करने से पहले सेंटीमीटर या इंच को पॉइंट्स में बदलें। |
| **समूह के भीतर आकार घुमाना** | आकार डालने के बाद उसका `ShapeBase` ऑब्जेक्ट प्राप्त करें और `ShapeBase.RotationAngle` सेट करें। |
| **आकार के भीतर टेक्स्ट जोड़ना** | `ShapeBase.AppendChild(new Paragraph(document))` का उपयोग करें और फिर इच्छित टेक्स्ट के साथ एक `Run` जोड़ें। |
| **DOCX के बजाय PDF में सहेजना** | `document.Save("GroupShape.pdf", SaveFormat.Pdf);` कॉल करें – समूह पदानुक्रम PDF आउटपुट में संरक्षित रहता है। |

इन विविधताओं से स्पष्ट होता है कि वही **दीर्घवृत्त कैसे डालें** तर्क कई वास्तविक‑दुनिया परिदृश्यों में अनुकूलित किया जा सकता है।

## Pro tips

* **एक ही `DocumentBuilder` इंस्टेंस को पुनः उपयोग करें** – यह मेमोरी ओवरहेड कम करता है और दस्तावेज़ की स्थिति को सुसंगत रखता है।
* **आकार के आयामों को वैध करें** – अत्यधिक बड़ी चौड़ाई या ऊँचाई पुराने Word संस्करणों में रेंडरिंग समस्याएँ पैदा कर सकती है।
* **स्टाइलिंग से पहले समूह बनाएं** – सभी चाइल्ड जोड़ने के बाद समूह पर फ़िल रंग या लाइन स्टाइल लागू करने से समान रूप प्राप्त होता है।

## निष्कर्ष

आप अब समझते हैं **दीर्घवृत्त कैसे डालें** और **आयत आकार कैसे जोड़ें** समूहित कंटेनर के भीतर Word दस्तावेज़ में Aspose.Words का उपयोग करके। प्रत्येक इंसर्शन से पहले **आकार पर कर्सर ले जाएँ** करके आप साफ़ पदानुक्रम बनाए रखते हैं और आकस्मिक प्लेसमेंट से बचते हैं। पूरा उदाहरण कम्पाइल, रन होता है और एक समूहित आकार उत्पन्न करता है जिसे आगे कस्टमाइज़ या एक्सपोर्ट किया जा सकता है।

और अधिक खोजने के लिए तैयार हैं? इस तकनीक को **समूह आकार कैसे बनाएं** के साथ मिलाकर जटिल आरेख बनाएं, या **आयत आकार Word में डालें** को टेक्स्ट बॉक्स के साथ प्रयोग करके समृद्ध रिपोर्ट जेनरेट करें। Happy coding!

## What Should You Learn Next?

नीचे दिए गए ट्यूटोरियल्स उन विषयों को कवर करते हैं जो इस गाइड में प्रदर्शित तकनीकों पर आधारित हैं। प्रत्येक संसाधन में पूर्ण कार्यशील कोड उदाहरण और चरण‑दर‑चरण व्याख्याएँ शामिल हैं, जिससे आप अतिरिक्त API सुविधाओं में महारत हासिल कर सकें और अपने प्रोजेक्ट्स में वैकल्पिक कार्यान्वयन दृष्टिकोणों का अन्वेषण कर सकें।

- [Word में आयत आकार और समूह आकार कैसे बनाएं Aspose.Words के साथ](/words/english/net/programming-with-shapes/how-to-create-rectangle-shape-and-group-shapes-in-word-with/)
- [खाली Word दस्तावेज़ बनाएं और C# में छिपा दीर्घवृत्त आकार जोड़ें](/words/english/java/images-shapes/how-to-create-blank-word-document-and-add-a-hidden-ellipse-s/)
- [C# में समूह आकार docx बनाएं और इंटरैक्टिव कंट्रोल्स जोड़ें](/words/english/java/images-shapes/how-to-create-group-shape-docx-and-add-interactive-controls/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}