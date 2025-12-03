---
"date": "2025-03-29"
"description": "पायथन के साथ Aspose.Words लाइब्रेरी का उपयोग करके Word दस्तावेज़ों में टिप्पणियों और उत्तरों को प्रोग्रामेटिक रूप से जोड़ने, प्रबंधित करने और पुनर्प्राप्त करने का तरीका जानें।"
"title": "पायथन के लिए Aspose.Words का उपयोग करके Word दस्तावेज़ों में टिप्पणियाँ और उत्तर कैसे लागू करें"
"url": "/hi/python-net/annotations-comments/aspose-words-python-comments-replies/"
"weight": 1
---

# पायथन के लिए Aspose.Words का उपयोग करके Word दस्तावेज़ों में टिप्पणियाँ और उत्तर कैसे लागू करें

## परिचय

दस्तावेजों पर सहयोगात्मक रूप से काम करने के लिए अक्सर टीम के सदस्यों को सीधे दस्तावेज़ में टिप्पणियाँ और सुझाव जोड़ने की आवश्यकता होती है। जटिल वर्कफ़्लो या बड़ी टीमों को संभालते समय यह चुनौतीपूर्ण हो सकता है। पायथन के लिए Aspose.Words के साथ, आप Word दस्तावेज़ों में प्रोग्रामेटिक रूप से टिप्पणियाँ और उत्तर जोड़कर इन कार्यों को कुशलतापूर्वक प्रबंधित कर सकते हैं। इस ट्यूटोरियल में, हम पायथन में Aspose.Words लाइब्रेरी का उपयोग करके इन सुविधाओं को लागू करने का तरीका जानेंगे।

### आप क्या सीखेंगे
- किसी दस्तावेज़ में टिप्पणी और उत्तर कैसे जोड़ें
- किसी दस्तावेज़ से सभी टिप्पणियाँ और उनके उत्तर कैसे प्रिंट करें
- किसी टिप्पणी से व्यक्तिगत या सभी उत्तर कैसे हटाएँ
- सुझाए गए परिवर्तन लागू करने के बाद किसी टिप्पणी को पूर्ण के रूप में कैसे चिह्नित करें
- किसी टिप्पणी की UTC तिथि और समय कैसे प्राप्त करें

क्या आप इसमें शामिल होने के लिए तैयार हैं? आइये सबसे पहले अपना परिवेश तैयार करें।

## आवश्यक शर्तें

आरंभ करने से पहले, सुनिश्चित करें कि आपके पास निम्नलिखित हैं:
- आपके सिस्टम पर पायथन 3.6 या उच्चतर संस्करण स्थापित होना चाहिए।
- Aspose.Words को स्थापित करने के लिए Pip पैकेज प्रबंधक.
- पायथन प्रोग्रामिंग और दस्तावेज़ हेरफेर की बुनियादी समझ।

## पायथन के लिए Aspose.Words सेट अप करना

अपने पायथन प्रोजेक्ट्स में Aspose.Words का उपयोग शुरू करने के लिए, इसे स्थापित करने हेतु इन चरणों का पालन करें:

**पिप स्थापना:**

```bash
pip install aspose-words
```

### लाइसेंस प्राप्ति चरण

Aspose अपने उत्पादों का निःशुल्क परीक्षण प्रदान करता है। आप अस्थायी लाइसेंस का अनुरोध कर सकते हैं [यहाँ](https://purchase.aspose.com/temporary-license/)उत्पादन उपयोग के लिए, आपको Aspose वेबसाइट से पूर्ण लाइसेंस खरीदना होगा।

### बुनियादी आरंभीकरण और सेटअप

एक बार इंस्टॉल हो जाने पर, लाइब्रेरी को अपनी स्क्रिप्ट में आयात करें:

```python
import aspose.words as aw
```

## कार्यान्वयन मार्गदर्शिका

आइए Aspose.Words का उपयोग करके टिप्पणियाँ और उत्तर जोड़ने की प्रत्येक सुविधा का विश्लेषण करें।

### उत्तर के साथ टिप्पणी जोड़ें

यह अनुभाग दर्शाता है कि किसी दस्तावेज़ में टिप्पणी और उत्तर कैसे जोड़ें।

#### अवलोकन

आप एक नया वर्ड दस्तावेज़ बनाएंगे, एक टिप्पणी जोड़ेंगे, और फिर उस टिप्पणी पर प्रोग्रामेटिक रूप से एक उत्तर जोड़ेंगे।

```python
import aspose.words as aw
import datetime

# एक नया दस्तावेज़ ऑब्जेक्ट बनाएँ.
doc = aw.Document()
builder = aw.DocumentBuilder(doc=doc)

# लेखक की जानकारी और वर्तमान दिनांक/समय के साथ एक टिप्पणी जोड़ें।
comment = aw.Comment(doc, 'John Doe', 'J.D.', datetime.datetime.now())
comment.set_text('My comment.')

# दस्तावेज़ में वर्तमान पैराग्राफ़ में टिप्पणी जोड़ें.
builder.current_paragraph.append_child(comment)

# प्रारंभिक टिप्पणी पर उत्तर जोड़ें.
comment.add_reply('Joe Bloggs', 'J.B.', datetime.datetime.now(), 'New reply')

# दस्तावेज़ को टिप्पणियों और उत्तरों के साथ सहेजें.
doc.save(file_name="YOUR_OUTPUT_DIRECTORY/Comment.AddCommentWithReply.docx")
```

**पैरामीटर और विधियाँ:**
- `aw.Comment`: एक नया टिप्पणी ऑब्जेक्ट आरंभ करता है। पैरामीटर में दस्तावेज़, लेखक का नाम, आद्याक्षर और दिनांक/समय शामिल हैं।
- `set_text()`: टिप्पणी की पाठ्य सामग्री निर्धारित करता है।
- `add_reply()`: किसी मौजूदा टिप्पणी पर उत्तर जोड़ता है.

### सभी टिप्पणियाँ प्रिंट करें

यह सुविधा दिखाती है कि किसी दस्तावेज़ से सभी टिप्पणियाँ कैसे निकालें और प्रिंट करें।

#### अवलोकन

हम एक मौजूदा वर्ड फाइल खोलेंगे, उसकी सभी टिप्पणियाँ निकालेंगे, तथा उनके उत्तरों के साथ उन्हें प्रिंट करेंगे।

```python
import aspose.words as aw

# टिप्पणियाँ युक्त दस्तावेज़ लोड करें.
doc = aw.Document(file_name='YOUR_DOCUMENT_DIRECTORY/Comments.docx')

# दस्तावेज़ से सभी टिप्पणी नोड्स प्राप्त करें.
comments = doc.get_child_nodes(aw.NodeType.COMMENT, True)

for comment in comments:
    if comment.ancestor is None:  # शीर्ष-स्तरीय टिप्पणियों की जाँच करें
        print('Top-level comment:')
        comment = comment.as_comment()
        print(f'\t"{comment.get_text().strip()}", by {comment.author}')
        print(f'Has {len(comment.replies)} replies')
        
        # टिप्पणी के प्रत्येक उत्तर को प्रिंट करें।
        for reply in comment.replies:
            reply = reply.as_comment()
            print(f'\t"{reply.get_text().strip()}", by {reply.author}')
```

**पैरामीटर और विधियाँ:**
- `get_child_nodes()`: निर्दिष्ट प्रकार के सभी नोड्स (इस मामले में टिप्पणियाँ) को पुनः प्राप्त करता है।
- `as_comment()`: आगे के हेरफेर के लिए एक नोड को टिप्पणी ऑब्जेक्ट में डालता है।

### टिप्पणी उत्तर हटाएं

यह अनुभाग दर्शाता है कि टिप्पणियों से उत्तरों को अलग-अलग या पूरी तरह से कैसे हटाया जाए।

#### अवलोकन

आप सीखेंगे कि जब उत्तरों की आवश्यकता न हो तो उन्हें हटाकर उन्हें कुशलतापूर्वक कैसे प्रबंधित किया जाए।

```python
import aspose.words as aw
import datetime

# एक नया दस्तावेज़ ऑब्जेक्ट आरंभ करें.
doc = aw.Document()
comment = aw.Comment(doc, 'John Doe', 'J.D.', datetime.datetime.now())
comment.set_text('My comment.')

# टिप्पणी को दस्तावेज़ के प्रथम पैराग्राफ में जोड़ें।
doc.first_section.body.first_paragraph.append_child(comment)

# मौजूदा टिप्पणी में उत्तर जोड़ें.
comment.add_reply('Joe Bloggs', 'J.B.', datetime.datetime.now(), 'New reply')
comment.add_reply('Joe Bloggs', 'J.B.', datetime.datetime.now(), 'Another reply')

# किसी विशिष्ट उत्तर को हटाएँ (इस मामले में पहला उत्तर)।
comment.remove_reply(comment.replies[0])

# वैकल्पिक रूप से, टिप्पणी से सभी उत्तर हटा दें।
comment.remove_all_replies()

# दस्तावेज़ में परिवर्तन सहेजें.
doc.save(file_name="YOUR_OUTPUT_DIRECTORY/Comment.RemoveReplies.docx")
```

**पैरामीटर और विधियाँ:**
- `remove_reply()`: किसी टिप्पणी से विशिष्ट उत्तर को हटाता है.
- `remove_all_replies()`: टिप्पणी से संबद्ध सभी उत्तरों को साफ़ करता है.

### टिप्पणी को पूर्ण के रूप में चिह्नित करें

यह सुविधा आपको सुझाए गए परिवर्तनों के लागू हो जाने के बाद टिप्पणियों को हल किया गया के रूप में चिह्नित करने की अनुमति देती है।

#### अवलोकन

किसी टिप्पणी को 'पूर्ण' के रूप में चिह्नित करने से यह संकेत मिलता है कि उस पर विचार किया गया है, जो दस्तावेज़ संशोधनों पर नज़र रखने के लिए महत्वपूर्ण है।

```python
import aspose.words as aw
import datetime

# एक नया दस्तावेज़ बनाएँ और बनाएँ.
doc = aw.Document()
builder = aw.DocumentBuilder(doc=doc)

# दस्तावेज़ में कुछ पाठ जोड़ें.
builder.writeln('Helo world!')

# वर्तनी सुधार का सुझाव देते हुए एक टिप्पणी डालें.
comment = aw.Comment(doc, 'John Doe', 'J.D.', datetime.datetime.now())
comment.set_text('Fix the spelling error!')
doc.first_section.body.first_paragraph.append_child(comment)

# टाइपिंग त्रुटि को सुधारें और टिप्पणी को पूर्ण चिह्नित करें।
doc.first_section.body.first_paragraph.runs[0].text = 'Hello world!'
comment.done = True

# दस्तावेज़ को चिह्नित टिप्पणियों के साथ सहेजें.
doc.save(file_name="YOUR_OUTPUT_DIRECTORY/Comment.Done.docx")
```

**पैरामीटर और विधियाँ:**
- `done`: किसी टिप्पणी को हल किया गया चिह्नित करने के लिए एक गुण.

### टिप्पणी के लिए UTC दिनांक और समय प्राप्त करें

टिप्पणी जोड़े जाने का सार्वभौमिक समन्वित समय (UTC) प्राप्त करें, जो वैश्विक सहयोग में टाइमस्टैम्पिंग के लिए उपयोगी है।

#### अवलोकन

यह उदाहरण दिखाता है कि किसी टिप्पणी की UTC तिथि और समय तक कैसे पहुंचा जाए और उसे कैसे प्रदर्शित किया जाए।

```python
import aspose.words as aw
import datetime
from datetime import timezone

# एक नया दस्तावेज़ ऑब्जेक्ट आरंभ करें.
doc = aw.Document()
builder = aw.DocumentBuilder(doc)
date = datetime.datetime.now()

# वर्तमान दिनांक/समय के साथ एक टिप्पणी जोड़ें.
comment = aw.Comment(doc, 'John Doe', 'J.D.', date)
comment.set_text('My comment.')

# दस्तावेज़ में वर्तमान पैराग्राफ़ में टिप्पणी जोड़ें.
builder.current_paragraph.append_child(comment)

# UTC पुनर्प्राप्ति को प्रदर्शित करने के लिए दस्तावेज़ को सहेजें और पुनः लोड करें।
doc.save(file_name="YOUR_OUTPUT_DIRECTORY/Comment.UtcDateTime.docx")
doc = aw.Document("YOUR_OUTPUT_DIRECTORY/Comment.UtcDateTime.docx")

# पहली टिप्पणी और उसकी UTC दिनांक/समय तक पहुँचें.
comment = doc.get_child(aw.NodeType.COMMENT, 0, True).as_comment()
utc_date_time = comment.date_time_utc.strftime('%Y-%m-%d %H:%M:%S')
print(f'UTC Date and Time: {utc_date_time}')
```

**पैरामीटर और विधियाँ:**
- `date_time_utc`: टिप्पणी जोड़े जाने का UTC दिनांक/समय पुनर्प्राप्त करता है.

## व्यावहारिक अनुप्रयोगों

पायथन के लिए Aspose.Words को विभिन्न दस्तावेज़ वर्कफ़्लो में एकीकृत किया जा सकता है। यहाँ कुछ उपयोग के मामले दिए गए हैं:
1. **दस्तावेज़ समीक्षा प्रणाली**: सहकर्मी समीक्षा के दौरान टिप्पणियां और उत्तर जोड़ना स्वचालित करें.
2. **कानूनी दस्तावेज़ प्रबंधन**कानूनी दस्तावेजों में परिवर्तनों और टिप्पणियों को कुशलतापूर्वक ट्रैक करें।
3. **शैक्षणिक सहयोग**: शैक्षणिक पत्रों में लेखकों और समीक्षकों के बीच फीडबैक लूप को सुगम बनाना।

यह व्यापक मार्गदर्शिका आपको पायथन के लिए Aspose.Words का उपयोग करके अपने Word दस्तावेज़ों में टिप्पणी और उत्तर प्रबंधन को प्रभावी ढंग से लागू करने में मदद करेगी।