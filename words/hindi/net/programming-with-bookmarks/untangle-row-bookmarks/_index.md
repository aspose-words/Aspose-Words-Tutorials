---
title: वर्ड डॉक्यूमेंट में पंक्ति बुकमार्क्स को सुलझाएँ
linktitle: वर्ड डॉक्यूमेंट में पंक्ति बुकमार्क्स को सुलझाएँ
second_title: Aspose.Words दस्तावेज़ प्रसंस्करण API
description: Aspose.Words for .NET का उपयोग करके अपने Word दस्तावेज़ों में उलझे हुए पंक्ति बुकमार्क को आसानी से सुलझाएँ। यह मार्गदर्शिका आपको स्वच्छ और सुरक्षित बुकमार्क प्रबंधन की प्रक्रिया से गुज़ारती है।
weight: 10
url: /hi/net/programming-with-bookmarks/untangle-row-bookmarks/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# वर्ड डॉक्यूमेंट में पंक्ति बुकमार्क्स को सुलझाएँ

## परिचय

क्या आपने कभी ऐसी स्थिति का सामना किया है जहाँ बुकमार्क द्वारा Word दस्तावेज़ में एक पंक्ति को हटाने से आस-पास की पंक्तियों में अन्य बुकमार्क गड़बड़ हो जाते हैं? यह अविश्वसनीय रूप से निराशाजनक हो सकता है, खासकर जब जटिल तालिकाओं से निपटना हो। शुक्र है, Aspose.Words for .NET एक शक्तिशाली समाधान प्रदान करता है: पंक्ति बुकमार्क को सुलझाना। 

यह मार्गदर्शिका आपको Aspose.Words for .NET का उपयोग करके अपने Word दस्तावेज़ों में पंक्ति बुकमार्क को सुलझाने की प्रक्रिया से परिचित कराएगी। हम कोड को समझने में आसान चरणों में विभाजित करेंगे और प्रत्येक फ़ंक्शन के उद्देश्य को समझाएँगे, जिससे आप उन कष्टप्रद बुकमार्क समस्याओं से आत्मविश्वास के साथ निपटने में सक्षम होंगे।

## आवश्यक शर्तें

इसमें गोता लगाने से पहले, आपको कुछ चीजों की आवश्यकता होगी:

1.  Aspose.Words for .NET: यह व्यावसायिक लाइब्रेरी Word दस्तावेज़ों के साथ प्रोग्रामेटिक रूप से काम करने के लिए कार्यक्षमता प्रदान करती है। 2. आप यहाँ से निःशुल्क परीक्षण डाउनलोड कर सकते हैं[लिंक को डाउनलोड करें](https://releases.aspose.com/words/net/) या लाइसेंस खरीदें[खरीदना](https://purchase.aspose.com/buy).
3. AC# विकास वातावरण: विजुअल स्टूडियो या कोई अन्य C# IDE पूरी तरह से काम करेगा।
4. पंक्ति बुकमार्क्स वाला एक वर्ड दस्तावेज़: हम प्रदर्शन के उद्देश्य से "Table column bookmarks.docx" नामक एक नमूना दस्तावेज़ का उपयोग करेंगे।

## नामस्थान आयात करें

पहले चरण में आपके C# प्रोजेक्ट में आवश्यक नामस्थानों को आयात करना शामिल है। ये नामस्थान उन कक्षाओं और कार्यात्मकताओं तक पहुँच प्रदान करते हैं जिनका उपयोग हम .NET के लिए Aspose.Words से करेंगे:

```csharp
using Aspose.Words;
using System;
```

## चरण 1: वर्ड दस्तावेज़ लोड करें

 हम उलझन वाली पंक्ति बुकमार्क वाले वर्ड दस्तावेज़ को लोड करके शुरू करते हैं।`Document` क्लास Aspose.Words में दस्तावेज़ हेरफेर को संभालता है। दस्तावेज़ को लोड करने का तरीका यहां बताया गया है:

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY"; // अपने दस्तावेज़ स्थान से बदलें
Document doc = new Document(dataDir + "Table column bookmarks.docx");
```

 प्रतिस्थापित करना याद रखें`"YOUR DOCUMENT DIRECTORY"` आपकी "Table column bookmarks.docx" फ़ाइल के वास्तविक पथ के साथ.

## चरण 2: पंक्ति बुकमार्क्स को सुलझाएँ

 यहीं पर जादू घटित होता है!`Untangle` फ़ंक्शन पंक्ति बुकमार्क को सुलझाने का काम करता है। आइए इसकी कार्यक्षमता को समझें:

```csharp
private void Untangle(Document doc)
{
   foreach (Bookmark bookmark in doc.Range.Bookmarks)
   {
	   // बुकमार्क और बुकमार्क अंत दोनों की मूल पंक्ति प्राप्त करें
	   Row row1 = (Row)bookmark.BookmarkStart.GetAncestor(typeof(Row));
	   Row row2 = (Row)bookmark.BookmarkEnd.GetAncestor(typeof(Row));

	   // जांचें कि क्या पंक्तियाँ वैध और आसन्न हैं
	   if (row1 != null && row2 != null && row1.NextSibling == row2)
		   //बुकमार्क के अंत को शीर्ष पंक्ति के अंतिम सेल के अंतिम पैराग्राफ़ पर ले जाएं
		   row1.LastCell.LastParagraph.AppendChild(bookmark.BookmarkEnd);
   }
}
```

कोड क्या करता है, इसका चरण-दर-चरण विवरण यहां दिया गया है:

 हम दस्तावेज़ में सभी बुकमार्क्स को एक का उपयोग करके पुनरावृत्त करते हैं`foreach` कुंडली।
प्रत्येक बुकमार्क के लिए, हम बुकमार्क प्रारंभ (`bookmark.BookmarkStart`) और बुकमार्क अंत (`bookmark.BookmarkEnd` ) का उपयोग`GetAncestor` तरीका।
फिर हम जाँचते हैं कि क्या दोनों पंक्तियाँ पाई जाती हैं (`row1 != null`और`row2 != null`) और यदि वे आसन्न पंक्तियाँ हैं (`row1.NextSibling == row2`) यह सुनिश्चित करता है कि हम केवल उन बुकमार्क को संशोधित करें जो आसन्न पंक्तियों में फैले हों।
यदि शर्तें पूरी होती हैं, तो हम बुकमार्क अंत नोड को शीर्ष पंक्ति के अंतिम सेल में अंतिम पैराग्राफ के अंत में ले जाते हैं (`row1.LastCell.LastParagraph.AppendChild(bookmark.BookmarkEnd)`) उन्हें प्रभावी ढंग से सुलझाना।

## चरण 3: बुकमार्क द्वारा पंक्ति हटाएं

 अब जब बुकमार्क उलझे हुए नहीं हैं, तो हम उनके बुकमार्क नामों का उपयोग करके पंक्तियों को सुरक्षित रूप से हटा सकते हैं।`DeleteRowByBookmark` फ़ंक्शन इस कार्य को संभालता है:

```csharp
private void DeleteRowByBookmark(Document doc, string bookmarkName)
{
   Bookmark bookmark = doc.Range.Bookmarks[bookmarkName];

   Row row = (Row)bookmark?.BookmarkStart.GetAncestor(typeof(Row));
   row?.Remove();
}
```

इस फ़ंक्शन का विवरण इस प्रकार है:

हम बुकमार्क का नाम लेते हैं (`bookmarkName`) को इनपुट के रूप में उपयोग करें।
 हम संबंधित बुकमार्क ऑब्जेक्ट को पुनः प्राप्त करते हैं`doc.Range.Bookmarks[bookmarkName]`.
फिर हम बुकमार्क की मूल पंक्ति का उपयोग शुरू करते हैं`GetAncestor` (के समान`Untangle` समारोह)।
अंत में, हम जाँचते हैं कि बुकमार्क और पंक्ति मौजूद है या नहीं (`bookmark != null` और

## चरण 4: उलझन को सत्यापित करें

 जब`Untangle` फ़ंक्शन को अन्य बुकमार्क की सुरक्षा सुनिश्चित करनी चाहिए, इसे सत्यापित करना हमेशा अच्छा अभ्यास है। यहां बताया गया है कि हम कैसे जांच सकते हैं कि अनटैंगलिंग प्रक्रिया ने गलती से किसी अन्य बुकमार्क के अंत को नहीं हटाया है:

```csharp
if (doc.Range.Bookmarks["ROW1"].BookmarkEnd == null)
   throw new Exception("Wrong, the end of the bookmark was deleted.");
```

यह कोड स्निपेट जाँचता है कि "ROW1" नामक बुकमार्क का अंत "ROW2" बुकमार्क वाली पंक्ति को हटाने के बाद भी मौजूद है या नहीं। यदि यह शून्य है, तो एक अपवाद फेंका जाता है, जो अनटैंगलिंग प्रक्रिया में किसी समस्या का संकेत देता है। 

## चरण 5: दस्तावेज़ सहेजें

 अंत में, बुकमार्क्स को सुलझाने और संभावित रूप से पंक्तियों को हटाने के बाद, संशोधित दस्तावेज़ को सहेजें`Save` तरीका:

```csharp
doc.Save(dataDir + "WorkingWithBookmarks.UntangleRowBookmarks.docx");
```

यह दस्तावेज़ को अनटैंगल्ड बुकमार्क्स और किसी भी हटाई गई पंक्तियों के साथ एक नए फ़ाइल नाम "WorkingWithBookmarks.UntangleRowBookmarks.docx" के अंतर्गत सहेजता है। 

## निष्कर्ष

 इन चरणों का पालन करके और उपयोग करके`Untangle`फ़ंक्शन का उपयोग करके, आप Aspose.Words for .NET के साथ अपने Word दस्तावेज़ों में पंक्ति बुकमार्क को प्रभावी ढंग से सुलझा सकते हैं। यह सुनिश्चित करता है कि बुकमार्क द्वारा पंक्तियों को हटाने से आसन्न पंक्तियों में अन्य बुकमार्क के साथ अनपेक्षित परिणाम नहीं होते हैं। प्लेसहोल्डर्स को इस तरह से बदलना याद रखें`"YOUR DOCUMENT DIRECTORY"` अपने वास्तविक पथ और फ़ाइल नाम के साथ.

## अक्सर पूछे जाने वाले प्रश्न

### क्या Aspose.Words for .NET निःशुल्क है?

 Aspose.Words for .NET एक व्यावसायिक लाइब्रेरी है जिसका निःशुल्क परीक्षण उपलब्ध है। आप इसे यहाँ से डाउनलोड कर सकते हैं[लिंक को डाउनलोड करें](https://releases.aspose.com/words/net/).

### क्या मैं वर्ड में मैन्युअल रूप से पंक्ति बुकमार्क्स को सुलझा सकता हूँ?

तकनीकी रूप से संभव होने पर भी, Word में बुकमार्क को मैन्युअल रूप से खोलना थकाऊ और त्रुटि-प्रवण हो सकता है। Aspose.Words for .NET इस प्रक्रिया को स्वचालित करता है, जिससे आपका समय और प्रयास बचता है।

###  क्या होगा यदि`Untangle` function encounters an error?

कोड में एक अपवाद हैंडलर शामिल है जो एक अपवाद को फेंकता है यदि अनटैंगलिंग प्रक्रिया गलती से किसी अन्य बुकमार्क के अंत को हटा देती है। आप अपनी विशिष्ट आवश्यकताओं के अनुरूप इस त्रुटि हैंडलिंग को अनुकूलित कर सकते हैं।

### क्या मैं इस कोड का उपयोग असम्बद्ध पंक्तियों में बुकमार्क्स को सुलझाने के लिए कर सकता हूँ?

वर्तमान में, कोड उन बुकमार्क को सुलझाने पर केंद्रित है जो आसन्न पंक्तियों में फैले हुए हैं। गैर-आसन्न पंक्तियों को संभालने के लिए कोड को संशोधित करने के लिए उन परिदृश्यों को पहचानने और संभालने के लिए अतिरिक्त तर्क की आवश्यकता होगी।

### क्या इस दृष्टिकोण का उपयोग करने में कोई सीमाएं हैं?

यह दृष्टिकोण मानता है कि बुकमार्क तालिका कक्षों के भीतर अच्छी तरह से परिभाषित हैं। यदि बुकमार्क कक्षों के बाहर या अप्रत्याशित स्थानों पर रखे जाते हैं, तो अनटैंगलिंग प्रक्रिया इच्छित तरीके से काम नहीं कर सकती है।
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
