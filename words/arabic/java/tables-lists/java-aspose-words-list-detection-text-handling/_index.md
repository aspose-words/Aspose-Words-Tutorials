---
"date": "2025-03-28"
"description": "تعلّم كيفية إتقان اكتشاف القوائم، ومعالجة النصوص، والمزيد باستخدام Aspose.Words لجافا. يغطي هذا الدليل اكتشاف القوائم المفصولة بمسافات، وقص المسافات، وتحديد اتجاه المستند، وتعطيل الكشف التلقائي عن الترقيم، وإدارة الروابط التشعبية."
"title": "اكتشاف القائمة الرئيسية ومعالجة النصوص في جافا باستخدام Aspose.Words - دليل كامل"
"url": "/ar/java/tables-lists/java-aspose-words-list-detection-text-handling/"
"weight": 1
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}


# اكتشاف القائمة الرئيسية ومعالجة النصوص في جافا باستخدام Aspose.Words: دليل كامل

## مقدمة

غالبًا ما يُواجه العمل مع مستندات النص العادي تحديات في تحديد البيانات المُهيكلة، مثل القوائم، نظرًا لعدم تناسق الفواصل ومشاكل التنسيق. تُوفر مكتبة Aspose.Words لجافا ميزات فعّالة لمعالجة هذه المشاكل، بما في ذلك اكتشاف الترقيم باستخدام المسافات البيضاء، وقص المسافات، وتحديد اتجاه المستند، وتعطيل الكشف التلقائي عن الترقيم، وإدارة الروابط التشعبية في المستندات النصية. يُمكّنك هذا البرنامج التعليمي من التعامل بفعالية مع البيانات النصية باستخدام Aspose.Words.

**ما سوف تتعلمه:**
- تقنيات الكشف عن القوائم المفصولة بمسافات بيضاء
- طرق لقص المسافات غير المرغوب فيها من محتوى المستند
- طرق لتحديد اتجاه قراءة ملف نصي
- طرق تعطيل الكشف التلقائي عن الترقيم
- استراتيجيات لاكتشاف الروابط التشعبية وإدارتها في مستندات النص العادي

دعونا نراجع المتطلبات الأساسية اللازمة قبل تنفيذ هذه الميزات.

## المتطلبات الأساسية

قبل أن نبدأ، تأكد من أن لديك ما يلي:

### المكتبات المطلوبة:
- **كلمات Aspose لجافا**:الإصدار 25.3 أو أحدث.

### إعداد البيئة:
- تأكد من أن بيئة التطوير الخاصة بك تدعم Maven أو Gradle، حيث أنهما مطلوبان لإدارة التبعيات.

### المتطلبات المعرفية:
- فهم أساسي لبرمجة جافا
- المعرفة بأنظمة بناء Maven أو Gradle

## إعداد Aspose.Words

لبدء استخدام Aspose.Words لجافا في مشروعك، عليك تضمين التبعية اللازمة. إليك الطريقة:

**مافن:**
```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>25.3</version>
</dependency>
```

**جرادل:**
```gradle
implementation 'com.aspose:aspose-words:25.3'
```

### الحصول على الترخيص

للاستفادة الكاملة من Aspose.Words، فكر في الحصول على ترخيص:
- **نسخة تجريبية مجانية**:متوفرة لاختبار الميزات.
- **رخصة مؤقتة**:لأغراض التقييم دون قيود.
- **شراء**:ترخيص كامل للاستخدام المستمر.

بمجرد حصولك على الترخيص، قم بتشغيله في تطبيقك لفتح جميع وظائف المكتبة.

## دليل التنفيذ

دعونا نقوم بتحليل كل ميزة ونرى كيفية تنفيذها باستخدام Aspose.Words لـ Java.

### اكتشاف الترقيم باستخدام المسافات البيضاء

**ملخص:** تتيح لك هذه الميزة تحديد القوائم داخل مستندات النص العادي التي تستخدم المسافات البيضاء كفاصلات.

#### الخطوة 1: تحميل المستند
```java
import com.aspose.words.*;

final String TEXT_DOC = "Full stop delimiters:\n" +
    // ...
    "3 Fourth list item 3";

TxtLoadOptions loadOptions = new TxtLoadOptions();
loadOptions.setDetectNumberingWithWhitespaces(true);
Document doc = new Document(new ByteArrayInputStream(TEXT_DOC.getBytes()), loadOptions);
```

#### الخطوة 2: التحقق من صحة اكتشاف القائمة
```java
List<Paragraph> paragraphList = Arrays.stream(doc.getFirstSection().getBody().getParagraphs().toArray())
        .filter(Paragraph.class::isInstance)
        .map(Paragraph.class::cast)
        .collect(Collectors.toList());

boolean detectNumberingWithWhitespaces = true;
if (detectNumberingWithWhitespaces) {
    assert doc.getLists().getCount() == 4 : "Expected four lists.";
    boolean foundFourthList = paragraphList.stream()
        .anyMatch(p -> p.getText().contains("Fourth list") && p.isListItem());
    assert foundFourthList : "Expected to find a fourth list item detected as numbered.";
}
```

*المعاملات والطرق:*
- `setDetectNumberingWithWhitespaces(true)`:يقوم بتكوين المحلل للتعرف على القوائم التي تحتوي على فواصل المسافات البيضاء.
- `doc.getLists().getCount()`:استرجاع عدد القوائم المكتشفة في المستند.

### تقليم المسافات البادئة واللاحقة

**ملخص:** تعمل هذه الميزة على إزالة المسافات غير الضرورية في بداية أو نهاية الأسطر في المستندات النصية العادية، مما يضمن تنسيق النص بشكل نظيف.

#### الخطوة 1: تكوين خيارات التحميل
```java
import java.nio.charset.StandardCharsets;
import java.io.ByteArrayInputStream;

String textDoc = "      Line 1 \n" +
    // ...
    " Line 3       ";

TxtLoadOptions loadOptions = new TxtLoadOptions();
loadOptions.setLeadingSpacesOptions(TxtLeadingSpacesOptions.TRIM);
loadOptions.setTrailingSpacesOptions(TxtTrailingSpacesOptions.TRIM);

Document doc = new Document(new ByteArrayInputStream(textDoc.getBytes(StandardCharsets.US_ASCII)), loadOptions);
```

#### الخطوة 2: التحقق من التقليم
```java
ParagraphCollection paragraphs = doc.getFirstSection().getBody().getParagraphs();
for (int i = 0; i < paragraphs.getCount(); i++) {
    Paragraph paragraph = paragraphs.get(i);
    String text = paragraph.getText();
    assert !text.startsWith(" ") : "Expected no leading spaces.";
    assert !text.endsWith(" ") : "Expected no trailing spaces.";
}
```

*التكوينات الرئيسية:*
- `setLeadingSpacesOptions(TxtLeadingSpacesOptions.TRIM)`:يقوم بقص المسافات من بداية الأسطر.
- `setTrailingSpacesOptions(TxtTrailingSpacesOptions.TRIM)`:يزيل المسافات الموجودة في نهايات الأسطر.

### اكتشاف اتجاه المستند

**ملخص:** تحديد ما إذا كان ينبغي قراءة المستند من اليمين إلى اليسار (RTL)، مثل النص العبري أو العربي.

#### الخطوة 1: ضبط الاكتشاف التلقائي
```java
TxtLoadOptions loadOptions = new TxtLoadOptions();
loadOptions.setDocumentDirection(DocumentDirection.AUTO);
Document doc = new Document("YOUR_DOCUMENT_DIRECTORY/Hebrew text.txt", loadOptions);

boolean isBidi = doc.getFirstSection().getBody().getFirstParagraph().getParagraphFormat().isBidi();
assert isBidi : "Expected Hebrew text to be right-to-left.";
```

### تعطيل الكشف التلقائي عن الترقيم

**ملخص:** منع المكتبة من اكتشاف عناصر القائمة وتنسيقها تلقائيًا.

#### الخطوة 1: تكوين خيارات التحميل
```java
TxtLoadOptions options = new TxtLoadOptions();
options.setAutoNumberingDetection(false);
Document doc = new Document("YOUR_DOCUMENT_DIRECTORY/Number detection.txt", options);

int listItemsCount = 0;
for (Paragraph paragraph : (Iterable<Paragraph>) doc.getChildNodes(NodeType.PARAGRAPH, true)) {
    if (paragraph.isListItem())
        listItemsCount++;
}
assert listItemsCount == 0 : "Expected no detected list items.";
```

### اكتشاف الارتباطات التشعبية في النص

**ملخص:** تحديد وإدارة الروابط التشعبية داخل المستندات النصية العادية.

#### الخطوة 1: تعيين خيارات الكشف
```java
import java.nio.charset.StandardCharsets;
import java.io.ByteArrayInputStream;

final String INPUT_TEXT = "Some links in TXT:\n" +
    // ...
    "https://docs.aspose.com/words/net/";

try (ByteArrayInputStream stream = new ByteArrayInputStream(INPUT_TEXT.getBytes(StandardCharsets.US_ASCII))) {
    TxtLoadOptions loadOptions = new TxtLoadOptions();
    loadOptions.setDetectHyperlinks(true);
    Document doc = new Document(stream, loadOptions);

    String[] expectedLinks = {"https://www.aspose.com/"، "https://docs.aspose.com/words/net/"};
    for (int i = 0; i < doc.getRange().getFields().getCount(); i++) {
        String result = doc.getRange().getFields().get(i).getResult().trim();
        assert result.equals(expectedLinks[i]) : "Expected hyperlink does not match.";
    }
}
```

## التطبيقات العملية

1. **أنظمة إدارة المحتوى (CMS):** تنسيق المحتوى الذي ينشئه المستخدم تلقائيًا في قوائم منظمة.
2. **أدوات استخراج البيانات:** استخدم اكتشاف القائمة لتنظيم البيانات غير المنظمة للتحليل.
3. **خطوط أنابيب معالجة النصوص:** قم بتعزيز معالجة المستندات مسبقًا عن طريق تقليم المسافات واكتشاف اتجاه النص.

## اعتبارات الأداء

لتحسين الأداء:
- قم بتحميل المستندات بأقل قدر من العمليات، مع التركيز على الميزات الضرورية.
- قم بإدارة استخدام الذاكرة عن طريق معالجة المستندات الكبيرة في أجزاء حيثما كان ذلك ممكنًا.

## خاتمة

باستخدام Aspose.Words لجافا، يمكنك إدارة البيانات النصية بكفاءة في مستندات النص العادي. من اكتشاف القوائم المفصولة بمسافات بيضاء إلى معالجة اتجاه النص والروابط التشعبية، تتيح لك هذه الأدوات القوية معالجة المستندات بكفاءة. لمزيد من الاستكشاف، راجع [توثيق Aspose.Words](https://reference.aspose.com/words/java/) أو جرب النسخة التجريبية المجانية.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}