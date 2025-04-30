---
"description": "تعلّم كيفية تقسيم المستندات إلى صفحات HTML باستخدام Aspose.Words لجافا. اتبع دليلنا خطوة بخطوة لتحويل المستندات بسلاسة."
"linktitle": "تقسيم المستندات إلى صفحات HTML"
"second_title": "واجهة برمجة تطبيقات معالجة مستندات Java Aspose.Words"
"title": "تقسيم المستندات إلى صفحات HTML في Aspose.Words لـ Java"
"url": "/ar/java/document-manipulation/splitting-documents-into-html-pages/"
"weight": 25
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# تقسيم المستندات إلى صفحات HTML في Aspose.Words لـ Java


## مقدمة لتقسيم المستندات إلى صفحات HTML في Aspose.Words لـ Java

في هذا الدليل التفصيلي، سنستكشف كيفية تقسيم المستندات إلى صفحات HTML باستخدام Aspose.Words لجافا. Aspose.Words هي واجهة برمجة تطبيقات Java فعّالة للعمل مع مستندات مايكروسوفت وورد، وتوفر ميزات شاملة لمعالجة المستندات، بما في ذلك إمكانية تحويلها إلى صيغ مختلفة، بما في ذلك HTML.

## المتطلبات الأساسية

قبل أن نبدأ، تأكد من توفر المتطلبات الأساسية التالية:

- تم تثبيت Java Development Kit (JDK) على نظامك.
- مكتبة Aspose.Words لجافا. يمكنك تنزيلها من [هنا](https://releases.aspose.com/words/java/).

## الخطوة 1: استيراد الحزم الضرورية

```java
import com.aspose.words.*;
import java.io.*;
import java.util.ArrayList;
```

## الخطوة 2: إنشاء طريقة لتحويل Word إلى HTML

```java
class WordToHtmlConverter
{
    // تفاصيل التنفيذ لتحويل Word إلى HTML.
    // ...
}
```

## الخطوة 3: حدد فقرات العناوين كبداية للموضوع

```java
private ArrayList<Paragraph> selectTopicStarts()
{
    NodeCollection paras = mDoc.getChildNodes(NodeType.PARAGRAPH, true);
    ArrayList<Paragraph> topicStartParas = new ArrayList<Paragraph>();
    for (Paragraph para : (Iterable<Paragraph>) paras)
    {
        int style = para.getParagraphFormat().getStyleIdentifier();
        if (style == StyleIdentifier.HEADING_1)
            topicStartParas.add(para);
    }
    return topicStartParas;
}
```

## الخطوة 4: إدراج فواصل الأقسام قبل عناوين الفقرات

```java
private void insertSectionBreaks(ArrayList<Paragraph> topicStartParas)
{
    DocumentBuilder builder = new DocumentBuilder(mDoc);
    for (Paragraph para : topicStartParas)
    {
        Section section = para.getParentSection();
        if (para != section.getBody().getFirstParagraph())
        {
            builder.moveTo(para.getFirstChild());
            builder.insertBreak(BreakType.SECTION_BREAK_NEW_PAGE);
            section.getBody().getLastParagraph().remove();
        }
    }
}
```

## الخطوة 5: تقسيم المستند إلى مواضيع

```java
private ArrayList<Topic> saveHtmlTopics() throws Exception
{
    ArrayList<Topic> topics = new ArrayList<Topic>();
    for (int sectionIdx = 0; sectionIdx < mDoc.getSections().getCount(); sectionIdx++)
    {
        Section section = mDoc.getSections().get(sectionIdx);
        String paraText = section.getBody().getFirstParagraph().getText();
        String fileName = makeTopicFileName(paraText);
        if ("".equals(fileName))
            fileName = "UNTITLED SECTION " + sectionIdx;
        fileName = mDstDir + fileName + ".html";
        String title = makeTopicTitle(paraText);
        if ("".equals(title))
            title = "UNTITLED SECTION " + sectionIdx;
        Topic topic = new Topic(title, fileName);
        topics.add(topic);
        saveHtmlTopic(section, topic);
    }
    return topics;
}
```

## الخطوة 6: احفظ كل موضوع كملف HTML

```java
private void saveHtmlTopic(Section section, Topic topic) throws Exception
{
    Document dummyDoc = new Document();
    dummyDoc.removeAllChildren();
    dummyDoc.appendChild(dummyDoc.importNode(section, true, ImportFormatMode.KEEP_SOURCE_FORMATTING));
    dummyDoc.getBuiltInDocumentProperties().setTitle(topic.getTitle());
    HtmlSaveOptions saveOptions = new HtmlSaveOptions();
    {
        saveOptions.setPrettyFormat(true);
        saveOptions.setAllowNegativeIndent(true);
        saveOptions.setExportHeadersFootersMode(ExportHeadersFootersMode.NONE);
    }
    dummyDoc.save(topic.getFileName(), saveOptions);
}
```

## الخطوة 7: إنشاء جدول محتويات للموضوعات

```java
private void saveTableOfContents(ArrayList<Topic> topics) throws Exception
{
    Document tocDoc = new Document(mTocTemplate);
    tocDoc.getMailMerge().setFieldMergingCallback(new HandleTocMergeField());
    tocDoc.getMailMerge().executeWithRegions(new TocMailMergeDataSource(topics));
    tocDoc.save(mDstDir + "contents.html");
}
```

بعد أن شرحنا الخطوات، يمكنك تطبيق كل خطوة في مشروع جافا لتقسيم المستندات إلى صفحات HTML باستخدام Aspose.Words for Java. ستتيح لك هذه العملية إنشاء تمثيل HTML منظم لمستنداتك، مما يجعلها أكثر سهولة في الوصول إليها واستخدامها.

## خاتمة

في هذا الدليل الشامل، تناولنا عملية تقسيم المستندات إلى صفحات HTML باستخدام Aspose.Words لجافا. باتباع الخطوات الموضحة، يمكنك تحويل مستندات Word إلى صيغة HTML بكفاءة، مما يجعل محتواك أكثر سهولة في الوصول إليه على الويب.

## الأسئلة الشائعة

### كيف أقوم بتثبيت Aspose.Words لـ Java؟

لتثبيت Aspose.Words لـ Java، يمكنك تنزيل المكتبة من [هنا](https://releases.aspose.com/words/java/) واتبع تعليمات التثبيت الواردة في الوثائق.

### هل يمكنني تخصيص مخرجات HTML؟

نعم، يمكنك تخصيص مخرجات HTML عن طريق ضبط خيارات الحفظ في `HtmlSaveOptions` يسمح لك هذا بالتحكم في تنسيق ومظهر ملفات HTML المُولَّدة.

### ما هي إصدارات Microsoft Word التي يدعمها Aspose.Words لـ Java؟

يدعم Aspose.Words لجافا مجموعة واسعة من تنسيقات مستندات مايكروسوفت وورد، بما في ذلك DOC وDOCX وRTF وغيرها. وهو متوافق مع مختلف إصدارات مايكروسوفت وورد.

### كيف يمكنني التعامل مع الصور في HTML المحول؟

يستطيع Aspose.Words for Java التعامل مع الصور في HTML المُحوّلة بحفظها كملفات منفصلة في نفس مجلد ملف HTML. هذا يضمن عرض الصور بشكل صحيح في مُخرَج HTML.

### هل هناك نسخة تجريبية من Aspose.Words لـ Java متاحة؟

نعم، يمكنك طلب نسخة تجريبية مجانية من Aspose.Words for Java من موقع Aspose على الويب لتقييم ميزاته وقدراته قبل شراء الترخيص.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}