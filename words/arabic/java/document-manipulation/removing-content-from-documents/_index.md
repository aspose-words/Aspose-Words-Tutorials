---
date: 2026-01-06
description: تعلم كيفية إزالة التذييلات من مستندات Word باستخدام Aspose.Words for
  Java، بالإضافة إلى كيفية حذف فواصل الأقسام، وفواصل الصفحات، وأكثر من ذلك.
linktitle: Removing Content from Documents
second_title: Aspose.Words Java Document Processing API
title: كيفية إزالة التذييلات من مستندات Word باستخدام Aspose.Words لجافا
url: /ar/java/document-manipulation/removing-content-from-documents/
weight: 16
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# كيفية إزالة التذييلات من مستندات Word باستخدام Aspose.Words for Java

## مقدمة عن Aspose.Words for Java

في هذا البرنامج التعليمي ستكتشف **كيفية إزالة التذييلات من ملفات Word** برمجياً باستخدام Aspose.Words for Java. سواءً كنت بحاجة إلى تنظيف التقارير المُولَّدة، أو حذف المعلومات السرية، أو مجرد ترتيب قالب، فإن هذا الدليل يشرح لك أكثر سيناريوهات إزالة المحتوى شيوعًا — فواصل الصفحات، فواصل الأقسام، التذييلات، وجداول المحتويات. لنبدأ!

## إجابات سريعة
- **هل يمكنني إزالة التذييلات دون التأثير على المحتوى الآخر؟** نعم، تتيح لك الـ API استهداف عقد التذييل فقط.
- **هل أحتاج إلى ترخيص لتشغيل هذه الأمثلة؟** النسخة التجريبية المجانية تكفي للتطوير؛ الترخيص مطلوب للإنتاج.
- **ما صيغ Word المدعومة؟** DOC، DOCX، DOCM، والصيغ المستندة إلى OOXML.
- **هل الكود متوافق مع Java 8 وما بعدها؟** بالتأكيد، المكتبة متوافقة مع Java بدءًا من الإصدار 8.
- **كيف أحذف فواصل الأقسام؟** راجع قسم “كيفية حذف فواصل الأقسام” أدناه.

## ما هو “إزالة التذييلات من Word”؟

إزالة التذييلات من مستند Word تعني حذف عقد `HeaderFooter` التي تظهر في أسفل كل صفحة. هذه العملية شائعة عندما تريد إنتاج تخطيط نظيف يحتوي على رأس فقط أو عندما تحتوي التذييلات على بيانات حساسة لا يجب مشاركتها.

## لماذا نستخدم Aspose.Words for Java لهذه المهمة؟

توفر Aspose.Words نموذج كائن عالي المستوى يُبسط تعقيد صيغة ملف DOCX. يمكنك تعديل الفقرات، والـ runs، والأقسام، والتذييلات ببضع أسطر من كود Java، دون الحاجة إلى تثبيت Microsoft Word على الخادم.

## المتطلبات المسبقة
- مجموعة تطوير Java (JDK) 8 أو أحدث.
- مكتبة Aspose.Words for Java (قم بتنزيلها من موقع Aspose).
- مستند Word تجريبي (`Document.docx`) موجود في مسار معروف.

## إزالة فواصل الصفحات

تتحكم فواصل الصفحات في ترقيم الصفحات لكن أحيانًا تحتاج إلى إزالتها. المقتطف التالي يفحص كل فقرة، يزيل علامة `PageBreakBefore`، ويحذف أي أحرف فاصل صفحة صريحة.

```java
Document doc = new Document("Your Directory Path" + "Document.docx");
NodeCollection paragraphs = doc.getChildNodes(NodeType.PARAGRAPH, true);
for (Paragraph para : (Iterable<Paragraph>) paragraphs) {
    if (para.getParagraphFormat().getPageBreakBefore()) {
        para.getParagraphFormat().setPageBreakBefore(false);
    }
    for (Run run : para.getRuns()) {
        if (run.getText().contains(ControlChar.PAGE_BREAK)) {
            run.setText(run.getText().replace(ControlChar.PAGE_BREAK, ""));
        }
    }
}
doc.save("Your Directory Path" + "RemoveContent.RemovePageBreaks.docx");
```

*نصيحة:* نفّذ هذا قبل إزالة التذييلات إذا كنت تريد تخطيط صفحة واحدة.

## كيفية حذف فواصل الأقسام

فواصل الأقسام تقسم المستند إلى أقسام مستقلة، كل منها يمتلك رؤوسًا، تذييلات، وإعدادات صفحة خاصة. لدمج الأقسام وحذف فواصل الأقسام **فعليًا**، قم بالتكرار بترتيب عكسي، أضف محتوى كل قسم سابق إلى الأخير، ثم احذف القسم الفارغ الآن.

```java
for (int i = doc.getSections().getCount() - 2; i >= 0; i--) {
    doc.getLastSection().prependContent(doc.getSections().get(i));
    doc.getSections().get(i).remove();
}
```

هذه الطريقة تحافظ على جميع المحتويات مع القضاء على الفاصل البنيوي.

## إزالة التذييلات (الهدف الأساسي: إزالة التذييلات من Word)

غالبًا ما تحتوي التذييلات على أرقام الصفحات، تواريخ، أو ملاحظات سرية. الكود أدناه يزيل **جميع أنواع التذييلات** — التذييل للصفحة الأولى، الأساسي، وحتى الصفحات الفردية — من كل قسم.

```java
Document doc = new Document("Your Directory Path" + "Header and footer types.docx");
for (Section section : doc.getSections()) {
    HeaderFooter footer = section.getHeadersFooters().getByHeaderFooterType(HeaderFooterType.FOOTER_FIRST);
    footer.remove();
    footer = section.getHeadersFooters().getByHeaderFooterType(HeaderFooterType.FOOTER_PRIMARY);
    footer.remove();
    footer = section.getHeadersFooters().getByHeaderFooterType(HeaderFooterType.FOOTER_EVEN);
    footer.remove();
}
doc.save("Your Directory Path" + "RemoveContent.RemoveFooters.docx");
```

بعد تشغيل هذا المقتطف، سيكون للمستند الناتج **بدون أي تذييلات**، محققًا الهدف الأساسي “إزالة التذييلات من Word”.

## إزالة جدول المحتويات

يُخزن جدول المحتويات (TOC) كحقل. لحذفه، ابحث عن حقل TOC حسب فهرسه وأزل العقدة المرتبطة به.

```java
Document doc = new Document("Your Directory Path" + "Table of contents.docx");
removeTableOfContents(doc, 0);
doc.save("Your Directory Path" + "RemoveContent.RemoveToc.doc");
```

*(طريقة `removeTableOfContents` هي جزء من أمثلة Aspose.Words وتزيل عقدة TOC المحددة.)*

## المشكلات الشائعة & استكشاف الأخطاء وإصلاحها

| العَرَض | السبب المحتمل | الحل |
|---------|--------------|-----|
| التذييلات لا تزال تظهر بعد تشغيل الكود | المستند يحتوي على أزواج **header/footer** غير مُعالجة (مثل `FOOTER_FIRST` المفقود) | كرّر الحلقة عبر جميع قيم `HeaderFooterType` أو تحقق من `null` قبل استدعاء `remove()`. |
| تغيّر تخطيط الصفحة بشكل غير متوقع بعد حذف فواصل الأقسام | فقدت إعدادات الصفحة الخاصة بالقسم (الهوامش، الاتجاه) | انسخ إعدادات القسم إلى القسم المستهدف قبل الإزالة. |
| `ControlChar.PAGE_BREAK` لم يُحذف | المستند يستخدم **section breaks** بدلاً من أحرف فاصل الصفحة | استخدم طريقة “كيفية حذف فواصل الأقسام” أولاً. |

## الأسئلة المتكررة

**س: هل يمكنني إزالة تذييلات محددة فقط (مثل تذييل الصفحة الأولى فقط)؟**  
ج: نعم. استرجع التذييل بنوعه (`FOOTER_FIRST`) واستدعِ `remove()` فقط على تلك الحالة.

**س: كيف أحذف فواصل الأقسام دون دمج المحتوى؟**  
ج: يمكنك حذف عقدة `Section` مباشرة إذا لم تكن بحاجة إلى الحفاظ على محتواها، لكن لاحظ أن أي رؤوس/تذييلات مرتبطة بهذا القسم ستُفقد أيضًا.

**س: هل يمكن اكتشاف وجود جدول محتويات في المستند برمجيًا قبل محاولة حذفه؟**  
ج: استخدم `doc.getRange().getFields()` وتحقق من الحقول من النوع `FieldType.FIELD_TABLE_OF_CONTENTS`.

**س: هل تدعم Aspose.Words إزالة التذييلات من ملفات Word المشفرة؟**  
ج: نعم، فقط افتح المستند باستخدام كلمة المرور: `new Document(path, new LoadOptions(password))`.

**س: هل سيؤثر إزالة التذييلات على ترقيم الصفحات في المستند؟**  
ج: إزالة التذييلات لا تغير أرقام الصفحات إلا إذا كان التذييل نفسه يحتوي على حقل رقم الصفحة. إذا كنت بحاجة إلى إعادة ترقيم الصفحات، حدّث حقول أرقام الصفحات وفقًا لذلك.

## الخلاصة

لقد غطينا كل ما تحتاجه **لإزالة التذييلات من مستندات Word** باستخدام Aspose.Words for Java، بالإضافة إلى المهام المرتبطة مثل حذف فواصل الصفحات، **كيفية حذف فواصل الأقسام**، وإزالة جداول المحتويات. من خلال الاستفادة من هذه المقتطفات، يمكنك إنتاج مستندات نظيفة ومهنية تتناسب مع متطلبات تطبيقك.

---

**آخر تحديث:** 2026-01-06  
**تم الاختبار مع:** Aspose.Words for Java 24.12  
**المؤلف:** Aspose  


{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
