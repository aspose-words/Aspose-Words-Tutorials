---
category: general
date: 2026-06-20
description: كيفية تعيين رد الاتصال في Aspose.Words Java لاكتشاف الخطوط المفقودة وتخصيص
  تحميل المستند. تعلّم خطوة بخطوة كيفية التعامل مع تحذيرات استبدال الخطوط.
draft: false
keywords:
- how to set callback
- detect missing fonts
- handle missing fonts
- customize document loading
language: ar
og_description: كيفية تعيين رد النداء في Aspose.Words Java لاكتشاف الخطوط المفقودة،
  ومعالجة الاستبدالات، وتخصيص تحميل المستند. دليل كامل مع الشيفرة.
og_title: كيفية تعيين رد الاتصال – اكتشاف الخطوط المفقودة في Aspose.Words Java
schemas:
- author: Aspose
  dateModified: '2026-06-20'
  description: how to set callback in Aspose.Words Java to detect missing fonts and
    customize document loading. Learn step‑by‑step handling of font substitution warnings.
  headline: how to set callback in Aspose.Words Java – Detect and Handle Missing Fonts
  type: TechArticle
- description: how to set callback in Aspose.Words Java to detect missing fonts and
    customize document loading. Learn step‑by‑step handling of font substitution warnings.
  name: how to set callback in Aspose.Words Java – Detect and Handle Missing Fonts
  steps:
  - name: What if I want the program to stop loading when a font is missing?
    text: 'Throw an exception inside the `warning` method:'
  - name: Does this work for PDFs generated from DOCX?
    text: Absolutely. The callback fires during the **loading** phase, which is identical
      for all output formats (`save` to PDF, DOCX, HTML, etc.). As long as you load
      the source document with the same `LoadOptions`, you’ll catch missing fonts
      before they affect the final PDF.
  - name: Can I capture other warning types (e.g., image conversion)?
    text: Yes—`WarningInfo.getWarningType()` can be compared against other enums like
      `WarningType.IMAGE_CONVERSION`. Just add more `if` branches in the callback.
  - name: Is there a performance impact?
    text: Negligible. The callback runs synchronously during loading, and the extra
      checks are lightweight. If you’re loading thousands of documents, you might
      want to disable warnings in production by setting `loadOptions.setWarningCallback(null);`.
  - name: What’s Next?
    text: '- Explore **font substitution tables** for bulk mapping of many missing
      fonts. - Combine this callback with **document validation** to enforce style
      guides. - Try **custom warning callbacks** that write to a log file or a monitoring
      system instead of `System.out`.'
  type: HowTo
tags:
- Aspose.Words
- Java
- Document Processing
title: كيفية تعيين رد النداء في Aspose.Words Java – اكتشاف ومعالجة الخطوط المفقودة
url: /ar/java/document-loading-and-saving/how-to-set-callback-in-aspose-words-java-detect-and-handle-m/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# كيفية تعيين رد النداء (callback) في Aspose.Words Java – اكتشاف ومعالجة الخطوط المفقودة

هل تساءلت يوماً **كيف تُعيّن رد النداء** في Aspose.Words Java لتتمكن من اكتشاف الخطوط المفقودة قبل أن تُفسد ملف PDF أو DOCX الخاص بك؟ لست وحدك. تحذيرات الخطوط المفقودة قد تُفسد التخطيط بصمت، وبدون رد نداء تحذيري مناسب قد لا تلاحظ المشكلة إلا عندما يبدو المستند النهائي غير صحيح.  

في هذا الدرس سنستعرض مثالاً كاملاً جاهزاً للتنفيذ **يكتشف الخطوط المفقودة**، **يتعامل مع الخطوط المفقودة** بأناقة، ويُظهر لك كيفية **تخصيص تحميل المستند** باستخدام رد نداء تحذيري. في النهاية ستحصل على فئة Java مستقلة يمكنك إدراجها في أي مشروع—دون الحاجة للبحث في توثيق إضافي.

## ما الذي ستحتاجه

- Java 8 أو أحدث (الكود يعمل أيضاً مع Java 11+)  
- مكتبة Aspose.Words for Java (الإصدار 23.9 أو أحدث)  
- ملف DOCX يحتوي على إشارة إلى خط غير مثبت لديك (مثلاً خط شركة مخصص)  

إذا لم تقم بعد بإضافة Aspose.Words إلى مشروع Maven الخاص بك، فقط أضف:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
</dependency>
```

هذا كل شيء—بدون إضافات أخرى، بدون تبعيات أصلية.

---

## الخطوة 1: فهم آلية WarningCallback

**رد النداء التحذيري** هو طريقة Aspose.Words لتنبيهك عندما يحدث شيء غير متوقع أثناء تحميل أو حفظ المستند. من خلال تنفيذ `IWarningCallback` ستحصل على التحكم الكامل فيما يتم تسجيله، أو تجاهله، أو حتى تحويله إلى استثناء.

> **لماذا هذا مهم:**  
> عندما يكون الخط مفقوداً، تقوم Aspose باستبداله بخط احتياطي. النتيجة البصرية قد تكون مختلفة تماماً، خاصةً في ملفات PDF التي تعتمد على هوية العلامة التجارية. من خلال التقاط `WarningType.FONT_SUBSTITUTION` يمكنك تسجيل اسم الخط بدقة، وتحديد ما إذا كنت تريد إيقاف العملية، أو استبداله بخط مخصص برمجياً.

---

## الخطوة 2: إنشاء كائن LoadOptions

`LoadOptions` هو نقطة الدخول لتخصيص تحميل المستند. ستربط رد النداء بهذا الكائن قبل أن تقوم بتحميل الملف فعلياً.

```java
// Step 2: Prepare LoadOptions
LoadOptions loadOptions = new LoadOptions();
```

في هذه المرحلة `loadOptions` مجرد حاوية فارغة—لم يحدث شيء بعد. السحر الحقيقي يبدأ عندما نُدخل رد النداء.

---

## الخطوة 3: تنفيذ وربط رد النداء

فيما يلي فئة مجهولة مختصرة تُنفّذ `IWarningCallback`. تقوم بطباعة سطر ودود إلى وحدة التحكم كلما حدث استبدال للخط.

```java
// Step 3: Attach a warning callback to capture font substitution warnings
loadOptions.setWarningCallback(new IWarningCallback() {
    @Override
    public void warning(WarningInfo info) {
        // Detect missing fonts
        if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
            System.out.println("[Missing Font] " + info.getDescription());
            // Optional: you could throw an exception here to abort loading
            // throw new RuntimeException("Font missing: " + info.getDescription());
        }
    }
});
```

> **نصيحة احترافية:** إذا أردت **معالجة الخطوط المفقودة** عن طريق توفير بديل، يمكنك أيضاً ضبط `FontSettings` على `LoadOptions` وربط الخطوط المفقودة بخط احتياطي معروف.

---

## الخطوة 4: تحميل المستند باستخدام الخيارات المخصصة

الآن بعد أن تم ربط رد النداء، قم بتحميل المستند. إذا كان الملف يشير إلى خط غير موجود لديك، سيظهر التحذير في وحدة التحكم.

```java
// Step 4: Load the document using the configured LoadOptions
String docPath = "YOUR_DIRECTORY/doc-with-missing-font.docx";
Document document = new Document(docPath, loadOptions);
```

عند تشغيل البرنامج، قد تظهر في وحدة التحكم:

```
[Missing Font] Font substitution: The font "MyCustomFont" was not found. Substituted with "Arial".
```

هذا السطر يثبت أنك نجحت في **اكتشاف الخطوط المفقودة** وأنك الآن في موقع يمكنك من **معالجة الخطوط المفقودة** كما تشاء.

---

## الخطوة 5: اختياري – استبدال الخطوط المفقودة بخط معروف

إذا كنت تفضّل استبدال أي خط مفقود تلقائياً، مثلاً بـ `Times New Roman`، يمكنك إضافة كائن `FontSettings`:

```java
// Optional Step 5: Map missing fonts to a fallback
FontSettings fontSettings = new FontSettings();
fontSettings.setMissingFontNotification(new IWarningCallback() {
    @Override
    public void warning(WarningInfo info) {
        // This will be called for each missing font
        if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
            System.out.println("[Auto‑Replace] " + info.getDescription());
        }
    }
});
// Force substitution to Times New Roman
fontSettings.getSubstitutionSettings().getTableSubstitution().addSubstitutes("MyCustomFont", new String[]{"Times New Roman"});
loadOptions.setFontSettings(fontSettings);
```

الآن يُحمَّل المستند، وأي إشارة إلى `MyCustomFont` تُستبدل صامتاً بـ `Times New Roman`. ستظل وحدة التحكم تُظهر لك ما تم استبداله، لتبقى على اطلاع.

---

## مثال كامل يعمل

فيما يلي فئة Java واحدة تضم جميع الخطوات السابقة. انسخ‑الصقها في بيئتك التطويرية، عدّل `docPath`، ثم شغّلها.

```java
import com.aspose.words.*;

public class DetectMissingFontsDemo {
    public static void main(String[] args) {
        try {
            // 1️⃣ Create LoadOptions
            LoadOptions loadOptions = new LoadOptions();

            // 2️⃣ Attach warning callback (detect missing fonts)
            loadOptions.setWarningCallback(new IWarningCallback() {
                @Override
                public void warning(WarningInfo info) {
                    if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                        System.out.println("[Missing Font] " + info.getDescription());
                    }
                }
            });

            // 3️⃣ (Optional) Set up automatic font substitution
            FontSettings fontSettings = new FontSettings();
            fontSettings.getSubstitutionSettings()
                        .getTableSubstitution()
                        .addSubstitutes("MyCustomFont", new String[]{"Times New Roman"});
            loadOptions.setFontSettings(fontSettings);

            // 4️⃣ Load the document with custom loading behavior
            String docPath = "YOUR_DIRECTORY/doc-with-missing-font.docx";
            Document doc = new Document(docPath, loadOptions);

            // 5️⃣ Save to PDF to see the final result (optional)
            doc.save("output.pdf");
            System.out.println("Document loaded and saved successfully.");

        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}
```

**الناتج المتوقع**

```
[Missing Font] Font substitution: The font "MyCustomFont" was not found. Substituted with "Times New Roman".
Document loaded and saved successfully.
```

الآن لديك طريقة قابلة لإعادة الإنتاج **لاكتشاف الخطوط المفقودة**، **معالجة الخطوط المفقودة**، و**تخصيص تحميل المستند**—كل ذلك عبر تعلم **كيفية تعيين رد النداء** بشكل صحيح.

---

## الأسئلة المتكررة

### ماذا لو أردت إيقاف تحميل البرنامج عندما يكون الخط مفقوداً؟

ارمِ استثناءً داخل طريقة `warning`:

```java
throw new RuntimeException("Critical: Missing font - " + info.getDescription());
```

سيتم التقاط الاستثناء في كتلة `catch` في الأسفل، ويمكنك تحديد كيفية تسجيله أو تنبيه المستخدم.

### هل يعمل هذا مع ملفات PDF التي تُنشأ من DOCX؟

بالتأكيد. رد النداء يُستدعى أثناء مرحلة **التحميل**، وهي نفسها لجميع صيغ الإخراج (`save` إلى PDF، DOCX، HTML، إلخ). طالما أنك تُحمِّل المستند الأصلي باستخدام نفس `LoadOptions`، ستلتقط الخطوط المفقودة قبل أن تؤثر على ملف PDF النهائي.

### هل يمكنني التقاط أنواع تحذير أخرى (مثل تحويل الصور)؟

نعم—`WarningInfo.getWarningType()` يمكن مقارنته مع تعداد آخر مثل `WarningType.IMAGE_CONVERSION`. ما عليك سوى إضافة فروع `if` إضافية داخل رد النداء.

### هل هناك تأثير على الأداء؟

ضئيل. رد النداء يُنفَّذ بشكل متزامن أثناء التحميل، والفحوصات الإضافية خفيفة. إذا كنت تُحمِّل آلاف المستندات، قد ترغب في تعطيل التحذيرات في بيئة الإنتاج عبر `loadOptions.setWarningCallback(null);`.

---

## نظرة بصرية عامة

![مثال على تعيين رد النداء في Aspose.Words Java](https://example.com/images/callback-diagram.png "مثال على تعيين رد النداء في Aspose.Words Java")

*يوضح المخطط التدفق: `LoadOptions` → `IWarningCallback` → تحميل المستند → معالجة استبدال الخط.*

---

## الخاتمة

غطّينا **كيفية تعيين رد النداء** في Aspose.Words Java، عرضنا **اكتشاف الخطوط المفقودة**، قدمنا طرقاً عملية **للتعامل مع الخطوط المفقودة**، وشرحنا كيف **تخصّص تحميل المستند** باستخدام `LoadOptions`.  

مع هذه المعرفة، يمكنك الآن حماية خطوط أنابيب المستندات الخاصة بك من استبدالات الخطوط الصامتة، الحفاظ على هوية العلامة التجارية، وتزويد المستخدمين بتغذية راجعة واضحة عندما يحدث أي خلل.

### ما الخطوة التالية؟

- استكشف **جداول استبدال الخطوط** لتعيين مجموعة كبيرة من الخطوط المفقودة.  
- اجمع هذا الرد مع **تحقق المستند** لفرض دليل الأنماط.  
- جرّب **ردود نداء تحذيرية مخصصة** تكتب إلى ملف سجل أو نظام مراقبة بدلاً من `System.out`.  

لا تتردد في التجربة، وأخبرنا كيف عدّلت رد النداء لمشاريعك الخاصة. برمجة سعيدة!

---


## ما الذي يجب أن تتعلمه بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات التي تم توضيحها في هذا الدليل. كل مصدر يتضمن أمثلة كود كاملة مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف أساليب تنفيذ بديلة في مشاريعك.

- [How to Set LoadOptions in Aspose.Words for Java](/words/english/java/document-loading-and-saving/using-load-options/)
- [How to Detect Fonts in Aspose.Words – Handle Warnings & Settings](/words/english/net/working-with-fonts/how-to-detect-fonts-in-aspose-words-handle-warnings-settings/)
- [How to Capture Fonts in Aspose.Words – Complete Guide](/words/english/net/working-with-fonts/how-to-capture-fonts-in-aspose-words-complete-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}