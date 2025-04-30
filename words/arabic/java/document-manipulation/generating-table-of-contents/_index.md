---
"description": "تعلّم كيفية إنشاء جدول المحتويات (TOC) وتخصيصه باستخدام Aspose.Words لجافا. أنشئ مستندات منظمة واحترافية بكل سهولة."
"linktitle": "إنشاء جدول المحتويات"
"second_title": "واجهة برمجة تطبيقات معالجة مستندات Java Aspose.Words"
"title": "إنشاء جدول المحتويات في Aspose.Words لـ Java"
"url": "/ar/java/document-manipulation/generating-table-of-contents/"
"weight": 21
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# إنشاء جدول المحتويات في Aspose.Words لـ Java


## مقدمة لإنشاء جدول المحتويات في Aspose.Words لـ Java

في هذا البرنامج التعليمي، سنشرح لك عملية إنشاء جدول محتويات (TOC) باستخدام Aspose.Words لجافا. يُعد جدول المحتويات ميزة أساسية لإنشاء مستندات منظمة. سنغطي كيفية تخصيص مظهره وتخطيطه.

## المتطلبات الأساسية

قبل أن تبدأ، تأكد من تثبيت Aspose.Words for Java وإعداده في مشروع Java الخاص بك.

## الخطوة 1: إنشاء مستند جديد

أولاً، دعنا ننشئ مستندًا جديدًا للعمل عليه.

```java
Document doc = new Document();
```

## الخطوة 2: تخصيص أنماط جدول المحتويات

لتخصيص مظهر جدول المحتويات، يمكنك تعديل الأنماط المرتبطة به. في هذا المثال، سنجعل إدخالات جدول المحتويات من المستوى الأول بخط عريض.

```java
doc.getStyles().getByStyleIdentifier(StyleIdentifier.TOC_1).getFont().setBold(true);
```

## الخطوة 3: إضافة محتوى إلى مستندك

يمكنك إضافة محتوى إلى المستند. سيُستخدم هذا المحتوى لإنشاء جدول المحتويات.

## الخطوة 4: إنشاء جدول المحتويات

لإنشاء جدول المحتويات، أدخل حقل جدول المحتويات في المكان المطلوب في مستندك. سيتم ملء هذا الحقل تلقائيًا بناءً على العناوين والأنماط في مستندك.

```java
// قم بإدراج حقل جدول المحتويات في الموقع المطلوب في مستندك.
FieldToc fieldToc = new FieldToc();
doc.getFirstSection().getBody().getFirstParagraph().appendChild(fieldToc);
```

## الخطوة 5: حفظ المستند

وأخيرًا، احفظ المستند مع جدول المحتويات.

```java
doc.save("your_output_path_here");
```

## تخصيص علامات التبويب في جدول المحتويات

يمكنك أيضًا تخصيص علامات التبويب في جدول المحتويات للتحكم في تخطيط أرقام الصفحات. إليك كيفية تغيير علامات التبويب:

```java
Document doc = new Document("Table of contents.docx");

for (Paragraph para : (Iterable<Paragraph>) doc.getChildNodes(NodeType.PARAGRAPH, true))
{
    if (para.getParagraphFormat().getStyle().getStyleIdentifier() >= StyleIdentifier.TOC_1 &&
        para.getParagraphFormat().getStyle().getStyleIdentifier() <= StyleIdentifier.TOC_9)
    {
        // احصل على علامة التبويب الأولى المستخدمة في هذه الفقرة، والتي تقوم بمحاذاة أرقام الصفحات.
        TabStop tab = para.getParagraphFormat().getTabStops().get(0);
        
        // إزالة علامة التبويب القديمة.
        para.getParagraphFormat().getTabStops().removeByPosition(tab.getPosition());
        
        // قم بإدراج علامة تبويب جديدة في موضع معدّل (على سبيل المثال، 50 وحدة إلى اليسار).
        para.getParagraphFormat().getTabStops().add(tab.getPosition() - 50.0, tab.getAlignment(), tab.getLeader());
    }
}

doc.save("output.docx");
```

أصبح لديك الآن جدول محتويات مخصص في مستندك مع علامات تبويب معدلة لمحاذاة أرقام الصفحات.


## خاتمة

في هذا البرنامج التعليمي، استكشفنا كيفية إنشاء جدول محتويات (TOC) باستخدام Aspose.Words لجافا، وهي مكتبة فعّالة للعمل مع مستندات Word. يُعدّ وجود جدول محتويات مُنظّم جيدًا أمرًا أساسيًا لتنظيم المستندات الطويلة والتنقل بينها، ويوفر Aspose.Words الأدوات اللازمة لإنشاء جداول المحتويات وتخصيصها بسهولة.

## الأسئلة الشائعة

### كيف يمكنني تغيير تنسيق إدخالات جدول المحتويات؟

يمكنك تعديل الأنماط المرتبطة بمستويات جدول المحتويات باستخدام `doc.getStyles().getByStyleIdentifier(StyleIdentifier.TOC_X)`حيث X هو مستوى TOC.

### كيف يمكنني إضافة المزيد من المستويات إلى جدول المحتويات الخاص بي؟

لتضمين المزيد من المستويات في جدول المحتويات الخاص بك، يمكنك تعديل حقل جدول المحتويات وتحديد عدد المستويات المطلوب.

### هل يمكنني تغيير مواضع علامة التبويب لإدخالات جدول المحتويات المحددة؟

نعم، كما هو موضح في مثال الكود أعلاه، يمكنك تغيير مواضع علامات التبويب لإدخالات جدول المحتويات المحددة عن طريق التكرار عبر الفقرات وتعديل علامات التبويب وفقًا لذلك.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}