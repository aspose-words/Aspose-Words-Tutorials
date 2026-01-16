---
date: 2026-01-16
description: تعلم كيفية تحويل البوصات إلى نقاط، قراءة بيانات تعريف المستند في جافا،
  إضافة خصائص مخصصة في جافا، وتعيين هوامش الصفحة في جافا باستخدام Aspose.Words للـ
  Java.
linktitle: Using Document Properties
second_title: Aspose.Words Java Document Processing API
title: تحويل البوصات إلى نقاط – باستخدام خصائص المستند في Aspose.Words للغة Java
url: /ar/java/document-manipulation/using-document-properties/
weight: 32
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# تحويل البوصات إلى نقاط – باستخدام خصائص المستند في Aspose.Words للـ Java

في هذا البرنامج التعليمي ستكتشف كيفية **تحويل البوصات إلى نقاط** عند ضبط هوامش الصفحة، قراءة بيانات تعريف المستند في Java، إضافة خصائص مخصصة في Java، والعمل مع خصائص المستند المدمجة باستخدام Aspose.Words للـ Java. سواءً كنت تُنشئ تقارير، فواتير، أو مستندات قانونية، فإن إتقان هذه التقنيات يمنحك تحكمًا دقيقًا في مظهر وبيانات التعريف لملفات Word الخاصة بك.

## إجابات سريعة
- **كيف أحول البوصات إلى نقاط؟** استخدم `ConvertUtil.inchToPoint(value)` من Aspose.Words.
- **هل يمكنني قراءة بيانات تعريف المستند في Java؟** نعم – استدعِ `doc.getBuiltInDocumentProperties()` أو `doc.getCustomDocumentProperties()`.
- **كيف أضيف خاصية مخصصة في Java؟** استخدم `doc.getCustomDocumentProperties().add(name, value)`.
- **ما الطريقة التي تضبط هوامش الصفحة بالنقاط؟** `PageSetup.setTopMargin`، `setBottomMargin`، إلخ، تقبل قيمًا بالنقاط.
- **هل يدعم الربط إلى إشارة مرجعية؟** نعم – استخدم `addLinkToContent` على مجموعة الخصائص المخصصة.

## مقدمة عن خصائص المستند

خصائص المستند هي جزء أساسي من أي ملف Word. فهي تخزن معلومات مثل العنوان، المؤلف، الموضوع، الكلمات المفتاحية، وأي بيانات تعريف مخصصة تحتاجها للمعالجة اللاحقة. في Aspose.Words للـ Java يمكنك التعامل مع كل من الخصائص المدمجة والمخصَّصة، ويمكنك أيضًا التحكم في تفاصيل التخطيط مثل الهوامش عن طريق تحويل وحدات القياس (مثال: **تحويل البوصات إلى نقاط**).

## ما هو “تحويل البوصات إلى نقاط”؟

في Word، تُعبَّر قياسات التخطيط بالنقاط (1 نقطة = 1/72 من البوصة). تحويل البوصات إلى نقاط يتيح لك تعريف الهوامش والمسافات والمسافات البادئة باستخدام الوحدات الإمبراطورية المألوفة بينما يتعامل الـ API مع النقاط داخليًا.

## لماذا ندير بيانات تعريف المستند في Java؟

إدراج بيانات التعريف يجعل البحث، التصنيف، وأتمتة سير العمل أسهل. على سبيل المثال، قد تُضيف علامة “مُصرَّح” إلى عقد أو تخزن رقم مراجعة لتتبع التدقيق. قراءة وكتابة هذه المعلومات برمجيًا يضمن الاتساق عبر دفعات كبيرة من المستندات.

## المتطلبات المسبقة
- Java 17+ (أو JDK متوافق)
- مكتبة Aspose.Words للـ Java مضافة إلى مشروعك (Maven/Gradle)
- ملف `.docx` تجريبي (مثلًا `Properties.docx`) موجود في دليل يمكن الوصول إليه

## دليل خطوة بخطوة

### تعداد خصائص المستند المدمجة
فيما يلي اختبار بسيط يفتح مستندًا ويطبع جميع الخصائص المدمجة مثل العنوان، المؤلف، والكلمات المفتاحية.

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

> **نصيحة احترافية:** استخدم هذا المقتطف للتحقق من أن بيانات التعريف قد كُتبت بشكل صحيح خلال الخطوات السابقة.

### إضافة خصائص مستند مخصصة (add custom properties java)
الخصائص المخصصة تسمح لك بتخزين أي نوع بيانات تحتاجه—منطقية، نصية، تاريخ، رقم، إلخ.

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

> **لماذا هذا مهم:** إضافة علامة مثل **Authorized** يمكن أن تُشغِّل سير عمل موافقة لاحق دون تعديل محتوى المستند.

### إزالة خاصية مخصصة
إذا لم تعد خاصية ما ضرورية، يمكنك حذفها بشكل نظيف.

```java
@Test
public void removeCustomDocumentProperties() throws Exception
{
    Document doc = new Document("Your Directory Path" + "Properties.docx");
    doc.getCustomDocumentProperties().remove("Authorized Date");
}
```

### تكوين رابط إلى محتوى (bookmark linking)
يمكنك إنشاء إشارة مرجعية ثم إضافة خاصية مخصصة تشير إلى تلك الإشارة، مما يتيح مراجع متقاطعة ديناميكية.

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

    // Add linked to content property.
    DocumentProperty customProperty = customProperties.addLinkToContent("Bookmark", "MyBookmark");
    customProperty = customProperties.get("Bookmark");
    boolean isLinkedToContent = customProperty.isLinkToContent();
    String linkSource = customProperty.getLinkSource();
    String customPropertyValue = customProperty.getValue().toString();
}
```

### التحويل بين وحدات القياس (set page margins java)
هنا يبرز الكلمة المفتاحية الأساسية. نضبط الهوامش بالبوصة، ثم **نحوِّل البوصات إلى نقاط** باستخدام `ConvertUtil`.

```java
@Test
public void convertBetweenMeasurementUnits() throws Exception
{
    Document doc = new Document();
    DocumentBuilder builder = new DocumentBuilder(doc);
    PageSetup pageSetup = builder.getPageSetup();

    // Set margins in inches.
    pageSetup.setTopMargin(ConvertUtil.inchToPoint(1.0));
    pageSetup.setBottomMargin(ConvertUtil.inchToPoint(1.0));
    pageSetup.setLeftMargin(ConvertUtil.inchToPoint(1.5));
    pageSetup.setRightMargin(ConvertUtil.inchToPoint(1.5));
    pageSetup.setHeaderDistance(ConvertUtil.inchToPoint(0.2));
    pageSetup.setFooterDistance(ConvertUtil.inchToPoint(0.2));
}
```

> **ملاحظة:** `ConvertUtil` يوفر أيضًا `pointToInch`، `mmToPoint`، وغيرها لتسهيل التعامل مع التخطيط.

### استخدام أحرف التحكم (read document metadata java)
أحرف التحكم تساعدك على تنظيف تدفقات النص. هذا المثال يستبدل عودة السطر (`\r`) بتسلسل فاصل سطر Windows (`\r\n`).

```java
@Test
public void useControlCharacters()
{
    final String TEXT = "test\r";

    // Replace "\r" control character with "\r\n".
    String replace = TEXT.replace(ControlChar.CR, ControlChar.CR_LF);
}
```

## المشكلات الشائعة والحلول
| المشكلة | السبب | الحل |
|---------|--------|------|
| الهوامش تبدو غير صحيحة بعد التحويل | استخدام وحدة خاطئة (مثلًا سم بدلًا من البوصة) | تأكد من استدعاء `ConvertUtil.inchToPoint` للقيم بالبوصة |
| الخاصية المخصصة لا تظهر | تم إضافة الخاصية بعد حفظ المستند | استدعِ `doc.save(...)` بعد إضافة الخصائص |
| رابط الإشارة المرجعية مكسور | خطأ إملائي في اسم الإشارة | تأكد من تطابق اسم الإشارة تمامًا في `addLinkToContent` |

## الأسئلة المتكررة

### كيف يمكنني الوصول إلى خصائص المستند المدمجة؟

للوصول إلى خصائص المستند المدمجة في Aspose.Words للـ Java، يمكنك استخدام طريقة `getBuiltInDocumentProperties` على كائن `Document`. تُعيد هذه الطريقة مجموعة من الخصائص المدمجة التي يمكنك التنقل خلالها.

### هل يمكنني إضافة خصائص مستند مخصصة إلى مستند؟

نعم، يمكنك إضافة خصائص مستند مخصصة إلى مستند باستخدام مجموعة `CustomDocumentProperties`. يمكنك تعريف خصائص مخصصة بأنواع بيانات مختلفة، بما في ذلك السلاسل، القيم المنطقية، التواريخ، والقيم الرقمية.

### كيف يمكنني إزالة خاصية مستند مخصصة معينة؟

لإزالة خاصية مستند مخصصة معينة، استخدم طريقة `remove` على مجموعة `CustomDocumentProperties`، مع تمرير اسم الخاصية التي تريد إزالتها كمعامل.

### ما هو هدف الربط إلى محتوى داخل المستند؟

الربط إلى محتوى داخل المستند يتيح لك إنشاء مراجع ديناميكية لأجزاء محددة من المستند. هذا مفيد لإنشاء مستندات تفاعلية أو مراجع متقاطعة بين الأقسام.

### كيف يمكنني التحويل بين وحدات قياس مختلفة في Aspose.Words للـ Java؟

يمكنك التحويل بين وحدات قياس مختلفة في Aspose.Words للـ Java باستخدام فئة `ConvertUtil`. توفر هذه الفئة طرقًا لتحويل الوحدات مثل البوصة إلى نقاط، النقاط إلى سنتيمترات، وأكثر.

## أسئلة شائعة أخرى

**س: كيف أقرأ بيانات تعريف المستند في Java دون تحميل الملف بالكامل؟**  
ج: استخدم `DocumentInfo` لاسترجاع الخصائص الأساسية دون تحميل محتوى المستند بالكامل.

**س: هل يمكنني ضبط هوامش الصفحة برمجيًا في Java للمستندات الموجودة؟**  
ج: نعم—افتح المستند، عدل هوامش `PageSetup` (حوّل البوصات إلى نقاط إذا لزم)، ثم احفظه.

**س: هل يمكن تصدير الخصائص المخصصة إلى بيانات تعريف PDF؟**  
ج: عند الحفظ إلى PDF، يقوم Aspose.Words تلقائيًا بربط الخصائص المخصصة ببيانات تعريف PDF المخصصة.

**س: هل تؤثر أحرف التحكم على تحويل PDF؟**  
ج: تُحافظ عليها أثناء التحويل؛ ومع ذلك قد ترغب في توحيد نهايات الأسطر للاتساق.

**س: أي نسخة من Aspose.Words مطلوبة لـ `ConvertUtil`؟**  
ج: `ConvertUtil` متوفرة منذ Aspose.Words 16.5؛ أي نسخة حديثة تدعمها.

## الخلاصة

من خلال إتقان **تحويل البوصات إلى نقاط**، قراءة بيانات تعريف المستند في Java، وإضافة الخصائص المخصصة في Java، تحصل على سيطرة كاملة على كل من التخطيط البصري والبيانات المخفية لملفات Word الخاصة بك. هذه القدرات تمكّنك من بناء خطوط أنابيب مستندات مؤتمتة، فرض الامتثال، وإنشاء تقارير منسقة غنيًا—كل ذلك باستخدام Aspose.Words للـ Java.

---

**آخر تحديث:** 2026-01-16  
**تم الاختبار مع:** Aspose.Words للـ Java 24.11  
**المؤلف:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}