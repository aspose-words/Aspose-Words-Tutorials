---
date: 2026-01-03
description: تعلم كيفية تعديل أرقام الصفحات أثناء إدراج جدول المحتويات باستخدام Aspose.Words
  for Java. خصّص أنماط جدول المحتويات وأنشئ المستندات بسهولة.
linktitle: Generating Table of Contents
second_title: Aspose.Words Java Document Processing API
title: ضبط أرقام الصفحات وإنشاء جدول المحتويات باستخدام Aspose.Words للغة Java
url: /ar/java/document-manipulation/generating-table-of-contents/
weight: 21
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# ضبط أرقام الصفحات وإنشاء جدول محتويات في Aspose.Words for Java

## إجابات سريعة
- **ماذا يعني “ضبط أرقام الصفحات”؟** تعديل مواضع علامات التبويب التي تُحاذى أرقام الصفحات في جدول المحتويات.  
- **هل يمكنني إدراج جدول محتويات تلقائيًا؟** نعم – استخدم الفئة `FieldToc`.  
- **هل أحتاج إلى ترخيص لتشغيل الكود؟** النسخة التجريبية المجانية تكفي للتطوير؛ الترخيص مطلوب للإنتاج.  
- **ما هو إصدار Aspose المدعوم؟** الأمثلة تعمل مع أحدث إصدار من Aspose.Words for Java.  
- **هل يمكن تخصيص أنماط جدول المحتويات؟** بالتأكيد – يمكنك تغيير الخطوط، الوزن، والمزيد.

## ما هو جدول المحتويات في Aspose.Words؟
جدول المحتويات هو حقل يقوم بمسح المستند للبحث عن أنماط العناوين (مثل Heading 1، Heading 2) ويولد قائمة بالمدخلات مع أرقام الصفحات. يتيح لك Aspose.Words إدراج هذا الحقل برمجيًا والتحكم الكامل في مظهره.

## لماذا نضبط أرقام الصفحات في جدول المحتويات؟
ضبط علامات التبويب يمنحك تحكمًا دقيقًا في موضع أرقام الصفحات، وهو أمر أساسي لـ:

- الحفاظ على تخطيط نظيف ومحاذى على الأعمدة.  
- مطابقة دليل الأنماط المؤسسية.  
- تحسين قابلية القراءة في المستندات المطبوعة والرقمية.

## المتطلبات المسبقة
- إضافة Aspose.Words for Java إلى مشروعك (Maven/Gradle).  
- إلمام أساسي بصياغة Java.

## دليل خطوة بخطوة

### الخطوة 1: إنشاء مستند جديد
أولاً، أنشئ كائن `Document` فارغ سيحمل المحتوى وجدول المحتويات.

```java
Document doc = new Document();
```

### الخطوة 2: تخصيص أنماط جدول المحتويات
يمكنك تغيير مظهر كل مستوى في جدول المحتويات. في هذا المثال نجعل مدخلات المستوى الأول غامقة، وهو طلب تنسيق شائع.

```java
doc.getStyles().getByStyleIdentifier(StyleIdentifier.TOC_1).getFont().setBold(true);
```

### الخطوة 3: إضافة محتوى إلى المستند
أدرج عناوين (مثل `Heading1`، `Heading2`) وفقرة عادية. سيقوم حقل جدول المحتويات لاحقًا بالتقاط هذه العناوين تلقائيًا. *(تم حذف الكود للتركيز على توليد جدول المحتويات.)*

### الخطوة 4: إدراج حقل جدول المحتويات
ضع جدول المحتويات في المكان الذي تريده—عادةً في بداية المستند.

```java
// Insert a TOC field at the desired location in your document.
FieldToc fieldToc = new FieldToc();
doc.getFirstSection().getBody().getFirstParagraph().appendChild(fieldToc);
```

### الخطوة 5: حفظ المستند
احفظ المستند على القرص. يمكنك اختيار أي تنسيق مدعوم مثل DOCX أو PDF أو HTML.

```java
doc.save("your_output_path_here");
```

## تخصيص علامات التبويب في جدول المحتويات (ضبط أرقام الصفحات)
إذا لم تكن علامة التبويب الافتراضية تُحاذى أرقام الصفحات كما تريد، يمكنك المرور على جميع فقرات جدول المحتويات وتعديل مواضع علامات التبويب الخاصة بها.

```java
Document doc = new Document("Table of contents.docx");

for (Paragraph para : (Iterable<Paragraph>) doc.getChildNodes(NodeType.PARAGRAPH, true))
{
    if (para.getParagraphFormat().getStyle().getStyleIdentifier() >= StyleIdentifier.TOC_1 &&
        para.getParagraphFormat().getStyle().getStyleIdentifier() <= StyleIdentifier.TOC_9)
    {
        // Get the first tab used in this paragraph, which aligns the page numbers.
        TabStop tab = para.getParagraphFormat().getTabStops().get(0);
        
        // Remove the old tab.
        para.getParagraphFormat().getTabStops().removeByPosition(tab.getPosition());
        
        // Insert a new tab at a modified position (e.g., 50 units to the left).
        para.getParagraphFormat().getTabStops().add(tab.getPosition() - 50.0, tab.getAlignment(), tab.getLeader());
    }
}

doc.save("output.docx");
```

الآن تُظهر مدخلات جدول المحتويات أرقام الصفحات بالضبط في الموضع المطلوب، مما يمنح مستندك مظهرًا مصقولًا.

## المشكلات الشائعة والنصائح
- **عدم ظهور العناوين في جدول المحتويات:** تأكد من أن عناوينك تستخدم الأنماط المدمجة (`Heading1`، `Heading2`، إلخ) أو قم بربط الأنماط المخصصة بمستويات جدول المحتويات.  
- **عدم تطبيق علامة التبويب:** تحقق من أن الفقرة تنتمي فعليًا إلى نمط جدول المحتويات (`TOC_1`‑`TOC_9`).  
- **الأداء في المستندات الكبيرة:** استدعِ `doc.updateFields()` بعد إدراج جدول المحتويات لتحديث المدخلات مرة واحدة.

## الأسئلة المتكررة

**س: كيف أغيّر تنسيق مدخلات جدول المحتويات؟**  
ج: استخدم `doc.getStyles().getByStyleIdentifier(StyleIdentifier.TOC_X)` حيث *X* هو المستوى (1‑9) وعدّل الخط أو اللون أو إعدادات الفقرة.

**س: كيف يمكنني إضافة مستويات إضافية إلى جدول المحتويات؟**  
ج: عدّل مفتاح `FieldToc` `\o "1-3"` (على سبيل المثال) لتضمين مستويات العناوين الإضافية، ثم حدّث الأنماط المقابلة `TOC_X`.

**س: هل يمكنني تغيير مواضع علامات التبويب لمدخلات معينة في جدول المحتويات؟**  
ج: نعم – مرّ على الفقرات كما هو موضح في قسم “تخصيص علامات التبويب” وعدّل كل علامة تبويب على حدة.

**س: هل يمكن توليد جدول محتويات في مخرجات PDF؟**  
ج: بالتأكيد. احفظ المستند كملف PDF (`doc.save("output.pdf")`) بعد توليد جدول المحتويات؛ يتم عرض الحقل تلقائيًا.

**س: هل يجب استدعاء `updateFields()` يدويًا؟**  
ج: عند إدراج `FieldToc`، يقوم Aspose.Words بتحديثه عند الحفظ، لكن استدعاء `doc.updateFields()` يمنحك نتائج فورية أثناء التصحيح.

## الخلاصة
لقد تعلمت كيفية **ضبط أرقام الصفحات**، **إدراج جدول محتويات**، و**تخصيص أنماط جدول المحتويات** باستخدام Aspose.Words for Java. تتيح لك هذه التقنيات إنشاء مستندات نظيفة، قابلة للتنقل، ومصممة باحترافية لتلبية أي معيار نشر.

---  

**آخر تحديث:** 2026-01-03  
**تم الاختبار مع:** Aspose.Words for Java (أحدث إصدار)  
**المؤلف:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}