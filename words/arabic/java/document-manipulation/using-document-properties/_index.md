---
title: استخدام خصائص المستند في Aspose.Words لـ Java
linktitle: استخدام خصائص المستند
second_title: واجهة برمجة تطبيقات معالجة المستندات في Java Aspose.Words
description: قم بتحسين إدارة المستندات باستخدام Aspose.Words for Java. تعلم كيفية العمل مع خصائص المستندات وإضافة بيانات تعريفية مخصصة والمزيد في هذا البرنامج التعليمي الشامل.
weight: 32
url: /ar/java/document-manipulation/using-document-properties/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# استخدام خصائص المستند في Aspose.Words لـ Java


## مقدمة حول خصائص المستند

تُعد خصائص المستند جزءًا حيويًا من أي مستند. فهي توفر معلومات إضافية حول المستند نفسه، مثل عنوانه ومؤلفه وموضوعه وكلماته الرئيسية والمزيد. في Aspose.Words for Java، يمكنك معالجة خصائص المستند المضمنة والمخصصة.

## تعداد خصائص المستند

### الخصائص المضمنة

لاسترجاع خصائص المستند المضمنة والعمل بها، يمكنك استخدام مقتطف التعليمات البرمجية التالي:

```java
@Test
public void enumerateProperties() throws Exception
{
    Document doc = new Document("Your Directory Path" + "Properties.docx");
    System.out.println(MessageFormat.format("1. Document name: {0}", doc.getOriginalFileName()));
    System.out.println("2. Built-in Properties");
    for (DocumentProperty prop : doc.getBuiltInDocumentProperties())
        System.out.println(MessageFormat.format("{0} : {1}", prop.getName(), prop.getValue()));
}
```

سيعرض هذا الكود اسم المستند والخصائص المضمنة، بما في ذلك خصائص مثل "العنوان" و"المؤلف" و"الكلمات الرئيسية".

### خصائص مخصصة

للعمل مع خصائص المستند المخصصة، يمكنك استخدام مقتطف التعليمات البرمجية التالي:

```java
@Test
public void addCustomDocumentProperties() throws Exception
{
    Document doc = new Document("Your Directory Path" + "Properties.docx");
    CustomDocumentProperties customDocumentProperties = doc.getCustomDocumentProperties();

    if (customDocumentProperties.get("Authorized") != null) return;

    customDocumentProperties.add("Authorized", true);
    customDocumentProperties.add("Authorized By", "John Smith");
    customDocumentProperties.add("Authorized Date", new Date());
    customDocumentProperties.add("Authorized Revision", doc.getBuiltInDocumentProperties().getRevisionNumber());
    customDocumentProperties.add("Authorized Amount", 123.45);
}
```

يوضح مقتطف التعليمات البرمجية هذا كيفية إضافة خصائص مستند مخصصة، بما في ذلك القيمة المنطقية، والسلسلة، والتاريخ، ورقم المراجعة، والقيمة الرقمية.

## إزالة خصائص المستند

لإزالة خصائص مستند معينة، يمكنك استخدام الكود التالي:

```java
@Test
public void removeCustomDocumentProperties() throws Exception
{
    Document doc = new Document("Your Directory Path" + "Properties.docx");
    doc.getCustomDocumentProperties().remove("Authorized Date");
}
```

يقوم هذا الكود بإزالة الخاصية المخصصة "التاريخ المعتمد" من المستند.

## تكوين رابط للمحتوى

في بعض الحالات، قد ترغب في إنشاء روابط داخل مستندك. إليك كيفية القيام بذلك:

```java
@Test
public void configuringLinkToContent() throws Exception
{
    Document doc = new Document();
    DocumentBuilder builder = new DocumentBuilder(doc);
    builder.startBookmark("MyBookmark");
    builder.writeln("Text inside a bookmark.");
    builder.endBookmark("MyBookmark");

    CustomDocumentProperties customProperties = doc.getCustomDocumentProperties();

    // إضافة مرتبط إلى خاصية المحتوى.
    DocumentProperty customProperty = customProperties.addLinkToContent("Bookmark", "MyBookmark");
    customProperty = customProperties.get("Bookmark");
    boolean isLinkedToContent = customProperty.isLinkToContent();
    String linkSource = customProperty.getLinkSource();
    String customPropertyValue = customProperty.getValue().toString();
}
```

يوضح مقتطف التعليمات البرمجية هذا كيفية إنشاء إشارة مرجعية في مستندك وإضافة خاصية مستند مخصصة ترتبط بهذه الإشارة المرجعية.

## التحويل بين وحدات القياس

في Aspose.Words for Java، يمكنك تحويل وحدات القياس بسهولة. فيما يلي مثال لكيفية القيام بذلك:

```java
@Test
public void convertBetweenMeasurementUnits() throws Exception
{
    Document doc = new Document();
    DocumentBuilder builder = new DocumentBuilder(doc);
    PageSetup pageSetup = builder.getPageSetup();

    // تعيين الهوامش بالبوصة.
    pageSetup.setTopMargin(ConvertUtil.inchToPoint(1.0));
    pageSetup.setBottomMargin(ConvertUtil.inchToPoint(1.0));
    pageSetup.setLeftMargin(ConvertUtil.inchToPoint(1.5));
    pageSetup.setRightMargin(ConvertUtil.inchToPoint(1.5));
    pageSetup.setHeaderDistance(ConvertUtil.inchToPoint(0.2));
    pageSetup.setFooterDistance(ConvertUtil.inchToPoint(0.2));
}
```

يقوم مقتطف التعليمات البرمجية هذا بتعيين هوامش ومسافات مختلفة بالبوصات عن طريق تحويلها إلى نقاط.

## استخدام أحرف التحكم

يمكن أن تكون أحرف التحكم مفيدة عند التعامل مع النص. إليك كيفية استبدال حرف تحكم في النص:

```java
@Test
public void useControlCharacters()
{
    final String TEXT = "test\r";

    // استبدل حرف التحكم "\r" بـ "\r\n".
    String replace = TEXT.replace(ControlChar.CR, ControlChar.CR_LF);
}
```

في هذا المثال، نقوم باستبدال علامة الإرجاع (`\r`) مع إرجاع العربة متبوعًا بتغذية السطر (`\r\n`).

## خاتمة

تلعب خصائص المستندات دورًا مهمًا في إدارة وتنظيم مستنداتك بفعالية في Aspose.Words for Java. سواء كنت تعمل باستخدام خصائص مضمنة أو خصائص مخصصة أو تستخدم أحرف التحكم، فلديك مجموعة من الأدوات تحت تصرفك لتحسين قدرات إدارة المستندات.

## الأسئلة الشائعة

### كيف يمكنني الوصول إلى خصائص المستند المضمنة؟

 للوصول إلى خصائص المستند المضمنة في Aspose.Words for Java، يمكنك استخدام`getBuiltInDocumentProperties` الطريقة على`Document` تقوم هذه الطريقة بإرجاع مجموعة من الخصائص المضمنة التي يمكنك تكرارها.

### هل يمكنني إضافة خصائص مستند مخصصة إلى مستند؟

 نعم، يمكنك إضافة خصائص مستند مخصصة إلى مستند باستخدام`CustomDocumentProperties` المجموعة. يمكنك تعريف خصائص مخصصة بأنواع بيانات مختلفة، بما في ذلك السلاسل والقيم المنطقية والتاريخ والقيم الرقمية.

### كيف يمكنني إزالة خاصية مستند مخصصة محددة؟

 لإزالة خاصية مستند مخصصة معينة، يمكنك استخدام`remove` الطريقة على`CustomDocumentProperties`مجموعة، تمرير اسم الخاصية التي تريد إزالتها كمعلمة.

### ما هو الغرض من الربط بالمحتوى داخل المستند؟

يتيح لك الربط بالمحتوى داخل المستند إنشاء مراجع ديناميكية لأجزاء معينة من المستند. يمكن أن يكون هذا مفيدًا لإنشاء مستندات تفاعلية أو مراجع متبادلة بين الأقسام.

### كيف يمكنني التحويل بين وحدات القياس المختلفة في Aspose.Words لـ Java؟

 يمكنك التحويل بين وحدات قياس مختلفة في Aspose.Words for Java باستخدام`ConvertUtil` يوفر طرقًا لتحويل الوحدات مثل البوصات إلى نقاط، والنقط إلى سنتيمترات، والمزيد.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
