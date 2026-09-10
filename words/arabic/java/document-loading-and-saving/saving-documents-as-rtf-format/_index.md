---
date: 2025-12-24
description: تعلم كيفية تحويل ملفات Word إلى RTF باستخدام Aspose.Words للغة Java.
  يوضح هذا الدليل خطوة بخطوة تحميل ملف DOCX، وتكوين خيارات حفظ RTF، وحفظه كنص غني.
linktitle: Saving Documents as RTF Format
second_title: Aspose.Words Java Document Processing API
title: تحويل Word إلى RTF باستخدام Aspose.Words للـ Java – دليل تعليمي
url: /ar/java/document-loading-and-saving/saving-documents-as-rtf-format/
weight: 23
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# تحويل Word إلى RTF باستخدام Aspose.Words for Java

في هذا البرنامج التعليمي ستتعلم **كيفية تحويل Word إلى RTF** بسرعة وموثوقية باستخدام Aspose.Words for Java. تحويل ملف DOCX إلى تنسيق النص الغني RTF هو طلب شائع عندما تحتاج إلى توافق واسع مع معالجات النصوص القديمة، عملاء البريد الإلكتروني، أو أنظمة أرشفة المستندات. سنستعرض خطوات تحميل مستند Word في Java، تعديل خيارات حفظ RTF (بما في ذلك حفظ الصور كـ WMF)، وأخيرًا كتابة ملف الإخراج.

## إجابات سريعة
- **ماذا يعني “convert word to rtf”؟** يحول ملف DOCX/Word إلى تنسيق Rich Text Format مع الحفاظ على النص، الأنماط، وربما الصور.  
- **هل أحتاج إلى ترخيص؟** نسخة التجربة المجانية تكفي للتطوير؛ الترخيص التجاري مطلوب للإنتاج.  
- **ما نسخة Java المدعومة؟** Aspose.Words for Java يدعم Java 8 وما فوق.  
- **هل يمكنني الاحتفاظ بالصور عند التحويل؟** نعم – استخدم خيار `saveImagesAsWmf` لتضمين الصور كـ WMF داخل ملف RTF.  
- **كم يستغرق التحويل من وقت؟** عادةً أقل من ثانية للمستندات القياسية؛ الملفات الكبيرة قد تستغرق بضع ثوانٍ.

## ما هو “convert word to rtf”؟
تحويل مستند Word إلى RTF ينتج ملفًا مستقلًا عن المنصة يخزن النص، التنسيق، وربما الصور في ترميز نصي بسيط. هذا يجعل المستند قابلًا للعرض في تقريبًا أي معالج نصوص دون فقدان التخطيط.

## لماذا نستخدم Aspose.Words for Java لحفظ النص الغني؟
- **دقة كاملة** – جميع ميزات Word (الأنماط، الجداول، رؤوس/تذييلات الصفحات) تُحافظ عليها.  
- **بدون الحاجة إلى Microsoft Office** – يعمل على أي خادم أو بيئة سحابية.  
- **تحكم دقيق** – خيارات الحفظ تسمح لك بتحديد كيفية تخزين الصور، الترميز المستخدم، وأكثر.

## المتطلبات المسبقة
1. **Aspose.Words for Java Library** – قم بتحميل وإضافة ملف JAR إلى مشروعك من [هنا](https://releases.aspose.com/words/java/).  
2. **ملف Word مصدر** – على سبيل المثال، `Document.docx` الذي تريد حفظه كـ RTF.  
3. **بيئة تطوير Java** – JDK 8+ وIDE المفضلة لديك.

## الخطوة 1: تحميل مستند Word (load word document java)
أولاً، قم بتحميل ملف DOCX الحالي إلى كائن `Document`. هذا هو الأساس لأي تحويل.

```java
import com.aspose.words.Document;

// Load the source document (e.g., Document.docx)
Document doc = new Document("path/to/Document.docx");
```

> **نصيحة احترافية:** استخدم المسارات المطلقة أو موارد class‑path لتجنب `FileNotFoundException`.

## الخطوة 2: تكوين خيارات حفظ RTF (save images as wmf)
توفر Aspose.Words الفئة `RtfSaveOptions` لضبط الإخراج بدقة. في هذا المثال نقوم بتمكين **حفظ الصور كـ WMF**، وهو التنسيق المفضل لملفات RTF.

```java
import com.aspose.words.RtfSaveOptions;

// Create an instance of RtfSaveOptions
RtfSaveOptions saveOptions = new RtfSaveOptions();

// Set the option to save images as WMF
saveOptions.setSaveImagesAsWmf(true);
```

يمكنك أيضًا تعديل إعدادات أخرى، مثل `saveOptions.setEncoding(Charset.forName("UTF-8"))` إذا كنت تحتاج إلى ترميز حرفي محدد.

## الخطوة 3: حفظ المستند كـ RTF (save docx as rtf)
الآن قم بكتابة المستند باستخدام الخيارات المكوَّنة. هذه الخطوة **تحفظ DOCX كـ RTF**، منتجًا ملف نص غني جاهز للتوزيع.

```java
// Save the document in RTF format

doc.save("path/to/output.rtf", saveOptions);
```

## الكود الكامل لتحويل Word إلى RTF
فيما يلي النسخة المختصرة التي يمكنك نسخها ولصقها في فئة Java. تُظهر **حفظ النص الغني** مع خيار صورة WMF في كتلة واحدة.

```java
Document doc = new Document("Your Directory Path" + "Document.docx");
RtfSaveOptions saveOptions = new RtfSaveOptions(); { saveOptions.setSaveImagesAsWmf(true); }
doc.save("Your Directory Path" + "WorkingWithRtfSaveOptions.SavingImagesAsWmf.rtf", saveOptions);
```

## المشكلات الشائعة واستكشاف الأخطاء
| المشكلة | السبب | الحل |
|---------|--------|------|
| ملف RTF الناتج فارغ | الملف المصدر غير موجود أو لم يتم تحميله | تحقق من المسار في `new Document(...)` |
| الصور مفقودة | تم تعيين `saveImagesAsWmf` إلى `false` | فعّل `saveOptions.setSaveImagesAsWmf(true)` |
| أحرف مشوشة | ترميز خاطئ | عيّن `saveOptions.setEncoding(Charset.forName("UTF-8"))` |

## الأسئلة المتكررة

**س: كيف يمكنني تغيير خيارات حفظ RTF الأخرى؟**  
ج: استخدم الفئة `RtfSaveOptions` – توفر خصائص للضغط، الخطوط، وأكثر. راجع وثائق Aspose.Words Java API للقائمة الكاملة.

**س: هل يمكنني حفظ مستند RTF بترميز مختلف؟**  
ج: نعم. استدعِ `saveOptions.setEncoding(Charset.forName("UTF-8"))` (أو أي ترميز مدعوم) قبل الحفظ.

**س: هل يمكن حفظ مستند RTF بدون صور؟**  
ج: بالتأكيد. عيّن `saveOptions.setSaveImagesAsWmf(false)` لاستبعاد الصور من الإخراج.

**س: كيف يجب أن أتعامل مع الاستثناءات أثناء التحويل؟**  
ج: غلف عمليات التحميل والحفظ بكتلة try‑catch تُلتقط `Exception`. سجِّل الخطأ وربما أعد رمي استثناء مخصص لتطبيقك.

**س: هل يعمل هذا مع ملفات Word محمية بكلمة مرور؟**  
ج: حمّل المستند باستخدام كائن `LoadOptions` يتضمن كلمة المرور، ثم تابع بنفس خطوات الحفظ.

## الخلاصة
الآن لديك طريقة كاملة وجاهزة للإنتاج **لتحويل Word إلى RTF** باستخدام Aspose.Words for Java. من خلال تحميل DOCX، تكوين `RtfSaveOptions` (بما في ذلك **حفظ الصور كـ WMF**)، واستدعاء `doc.save(...)`، يمكنك توليد ملفات نص غني عالية الجودة تعمل في كل مكان. لا تتردد في استكشاف خيارات حفظ إضافية لتخصيص الإخراج وفقًا لاحتياجاتك الدقيقة.

---

**Last Updated:** 2025-12-24  
**Tested With:** Aspose.Words for Java 24.12  
**Author:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}