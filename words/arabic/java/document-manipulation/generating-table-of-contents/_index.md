---
title: إنشاء جدول المحتويات في Aspose.Words للغة Java
linktitle: إنشاء جدول المحتويات
second_title: واجهة برمجة تطبيقات معالجة المستندات في Java Aspose.Words
description: تعرف على كيفية إنشاء جدول المحتويات (TOC) وتخصيصه باستخدام Aspose.Words for Java. أنشئ مستندات منظمة واحترافية دون عناء.
weight: 21
url: /ar/java/document-manipulation/generating-table-of-contents/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# إنشاء جدول المحتويات في Aspose.Words للغة Java


## مقدمة حول إنشاء جدول المحتويات في Aspose.Words للغة Java

في هذا البرنامج التعليمي، سنوضح لك عملية إنشاء جدول المحتويات (TOC) باستخدام Aspose.Words for Java. يُعد جدول المحتويات ميزة أساسية لإنشاء مستندات منظمة. وسنتناول كيفية تخصيص مظهر جدول المحتويات وتخطيطه.

## المتطلبات الأساسية

قبل أن تبدأ، تأكد من تثبيت Aspose.Words for Java وإعداده في مشروع Java الخاص بك.

## الخطوة 1: إنشاء مستند جديد

أولاً، دعنا ننشئ مستندًا جديدًا للعمل عليه.

```java
Document doc = new Document();
```

## الخطوة 2: تخصيص أنماط جدول المحتويات

لتخصيص مظهر جدول المحتويات الخاص بك، يمكنك تعديل الأنماط المرتبطة به. في هذا المثال، سنجعل إدخالات جدول المحتويات من المستوى الأول بخط غامق.

```java
doc.getStyles().getByStyleIdentifier(StyleIdentifier.TOC_1).getFont().setBold(true);
```

## الخطوة 3: إضافة المحتوى إلى مستندك

يمكنك إضافة المحتوى الخاص بك إلى المستند. سيتم استخدام هذا المحتوى لإنشاء جدول المحتويات.

## الخطوة 4: إنشاء جدول المحتويات

لتوليد جدول المحتويات، أدخل حقل جدول المحتويات في الموقع المطلوب في مستندك. سيتم ملء هذا الحقل تلقائيًا استنادًا إلى العناوين والأنماط في مستندك.

```java
// قم بإدراج حقل جدول المحتويات في الموقع المطلوب في مستندك.
FieldToc fieldToc = new FieldToc();
doc.getFirstSection().getBody().getFirstParagraph().appendChild(fieldToc);
```

## الخطوة 5: احفظ المستند

وأخيرًا، احفظ المستند باستخدام جدول المحتويات.

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
        
        //قم بإدراج علامة تبويب جديدة في موضع معدّل (على سبيل المثال، 50 وحدة إلى اليسار).
        para.getParagraphFormat().getTabStops().add(tab.getPosition() - 50.0, tab.getAlignment(), tab.getLeader());
    }
}

doc.save("output.docx");
```

أصبح لديك الآن جدول محتويات مخصص في مستندك مع علامات تبويب معدلة لمحاذاة أرقام الصفحات.


## خاتمة

في هذا البرنامج التعليمي، استكشفنا كيفية إنشاء جدول محتويات (TOC) باستخدام Aspose.Words for Java، وهي مكتبة قوية للعمل مع مستندات Word. يعد جدول المحتويات المنظم جيدًا أمرًا ضروريًا لتنظيم المستندات الطويلة والتنقل بينها، ويوفر Aspose.Words الأدوات اللازمة لإنشاء جداول المحتويات وتخصيصها دون عناء.

## الأسئلة الشائعة

### كيف يمكنني تغيير تنسيق إدخالات جدول المحتويات؟

 يمكنك تعديل الأنماط المرتبطة بمستويات جدول المحتويات باستخدام`doc.getStyles().getByStyleIdentifier(StyleIdentifier.TOC_X)`حيث X هو مستوى TOC.

### كيف يمكنني إضافة المزيد من المستويات إلى جدول المحتويات الخاص بي؟

لتضمين المزيد من المستويات في جدول المحتويات الخاص بك، يمكنك تعديل حقل جدول المحتويات وتحديد عدد المستويات المطلوب.

### هل يمكنني تغيير مواضع علامة التبويب لإدخالات جدول المحتويات المحددة؟

نعم، كما هو موضح في مثال الكود أعلاه، يمكنك تغيير مواضع علامات التبويب لإدخالات جدول المحتويات المحددة عن طريق التكرار عبر الفقرات وتعديل علامات التبويب وفقًا لذلك.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
