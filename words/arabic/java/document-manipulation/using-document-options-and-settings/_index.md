---
date: 2026-01-16
description: تعلم كيفية تمييز الأخطاء الإملائية في Word باستخدام Aspose.Words for
  Java، واكتشف كيفية ضبط عدد الأحرف في السطر، وتخصيص خيارات العرض، وتنظيف الأنماط.
linktitle: Using Document Options and Settings
second_title: Aspose.Words Java Document Processing API
title: تمييز الأخطاء الإملائية في Word باستخدام Aspose.Words Java
url: /ar/java/document-manipulation/using-document-options-and-settings/
weight: 31
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# استخدام خيارات وإعدادات المستند في Aspose.Words for Java

## مقدمة حول استخدام خيارات وإعدادات المستند في Aspose.Words for Java

في هذا الدليل الشامل، ستتعلم **كيفية تمييز أخطاء الإملاء في Word** باستخدام Aspose.Words for Java مع إتقان الإعدادات ذات الصلة مثل خيارات العرض، وتخطيط الصفحة، وتنظيف الأنماط. سواء كنت مطورًا متمرسًا أو مبتدئًا، ستساعدك الأمثلة أدناه على إنشاء مستندات قوية تدرك الأخطاء وتعمل عبر إصدارات Word المختلفة.

## إجابات سريعة
- **كيف يمكنني تمييز أخطاء الإملاء في Word؟** استخدم `setShowSpellingErrors(true)` على كائن `Document`.  
- **هل يمكنني أيضًا إظهار الأخطاء النحوية؟** نعم—استدعِ `setShowGrammaticalErrors(true)`.  
- **ما الطريقة التي تحدد عدد الأحرف في السطر؟** `getPageSetup().setCharactersPerLine(int)`.  
- **أي API يُحسّن التوافق مع إصدار Word معين؟** `doc.getCompatibilityOptions().optimizeFor(MsWordVersion)`.  
- **هل هناك طريقة لتنظيف الأنماط غير المستخدمة؟** استخدم `CleanupOptions` مع `setUnusedStyles(true)` واستدعِ `doc.cleanup(options)`.

## كيفية تمييز أخطاء الإملاء في Word؟

تجعل Aspose.Words من السهل تشغيل تمييز أخطاء الإملاء. عندما يُفتح المستند في Microsoft Word، تظهر الكلمات المكتوبة بشكل غير صحيح بخط أحمر سفلي مألوف، مما يساعد المستخدمين النهائيين على اكتشاف المشكلات فورًا.

## كيفية تحديد عدد الأحرف في السطر

التحكم في عدد الأحرف في السطر أمر أساسي لتخطيطات العرض ذات العرض الثابت (مثل قوائم الشيفرات أو النماذج القديمة). توفر فئة `PageSetup` الطريقة `setCharactersPerLine(int)` التي تسمح لك بتحديد هذه القيمة بدقة.

## كيفية إظهار الأخطاء النحوية

إلى جانب الإملاء، يمكنك أيضًا تمكين عرض الأخطاء النحوية. هذا مفيد عند صياغة محتوى يجب أن يتبع أدلة الأسلوب أو عند بناء أدوات تدقيق إملائي.

## تحسين المستندات للتوافق

```java
Document doc = new Document("Your Directory Path" + "Document.docx");
doc.getCompatibilityOptions().optimizeFor(MsWordVersion.WORD_2016);
doc.save("Your Directory Path" + "WorkingWithDocumentOptionsAndSettings.OptimizeForMsWord.docx");
```

أحد الجوانب المهمة في إدارة المستندات هو ضمان التوافق مع إصدارات مختلفة من Microsoft Word. توفر Aspose.Words for Java طريقة مباشرة لتحسين المستندات لإصدارات Word محددة. في المثال أعلاه، نقوم بتحسين مستند لـ Word 2016 لضمان توافق سلس.

## تحديد الأخطاء النحوية والإملائية

```java
@Test
public void showGrammaticalAndSpellingErrors() throws Exception
{
    Document doc = new Document("Your Directory Path" + "Document.docx");
    doc.setShowGrammaticalErrors(true);
    doc.setShowSpellingErrors(true);
    doc.save("Your Directory Path" + "WorkingWithDocumentOptionsAndSettings.ShowGrammaticalAndSpellingErrors.docx");
}
```

الدقة أمر حاسم عند التعامل مع المستندات. تتيح لك Aspose.Words for Java تمييز الأخطاء النحوية والإملائية داخل مستنداتك، مما يجعل عملية التدقيق والتحرير أكثر كفاءة.

## تنظيف الأنماط والقوائم غير المستخدمة

```java
@Test
public void cleanupUnusedStylesAndLists() throws Exception
{
    Document doc = new Document("Your Directory Path" + "Unused styles.docx");
    // Define cleanup options
    CleanupOptions cleanupOptions = new CleanupOptions();
    cleanupOptions.setUnusedLists(false);
    cleanupOptions.setUnusedStyles(true);
    doc.cleanup(cleanupOptions);
    doc.save("Your Directory Path" + "WorkingWithDocumentOptionsAndSettings.CleanupUnusedStylesAndLists.docx");
}
```

إدارة أنماط المستند والقوائم بفعالية أمر ضروري للحفاظ على اتساق المستند. تسمح لك Aspose.Words for Java بتنظيف الأنماط والقوائم غير المستخدمة، مما يضمن بنية مستند منظمة ومبسطة.

## إزالة الأنماط المكررة

```java
@Test
public void cleanupDuplicateStyle() throws Exception
{
    Document doc = new Document("Your Directory Path" + "Document.docx");
    // Clean duplicate styles
    CleanupOptions options = new CleanupOptions();
    options.setDuplicateStyle(true);
    doc.cleanup(options);
    doc.save("Your Directory Path" + "WorkingWithDocumentOptionsAndSettings.CleanupDuplicateStyle.docx");
}
```

يمكن أن تؤدي الأنماط المكررة إلى ارتباك وعدم اتساق في مستنداتك. باستخدام Aspose.Words for Java، يمكنك بسهولة إزالة الأنماط المكررة، مما يحافظ على وضوح وتماسك المستند.

## تخصيص خيارات عرض المستند

```java
@Test
public void viewOptions() throws Exception
{
    Document doc = new Document("Your Directory Path" + "Document.docx");
    // Customize viewing options
    doc.getViewOptions().setViewType(ViewType.PAGE_LAYOUT);
    doc.getViewOptions().setZoomPercent(50);
    doc.save("Your Directory Path" + "WorkingWithDocumentOptionsAndSettings.ViewOptions.docx");
}
```

تخصيص تجربة عرض المستندات أمر حيوي. تتيح لك Aspose.Words for Java ضبط خيارات عرض متعددة، مثل تخطيط الصفحة ونسبة التكبير، لتحسين قابلية القراءة.

## تكوين إعدادات صفحة المستند

```java
@Test
public void documentPageSetup() throws Exception
{
    Document doc = new Document("Your Directory Path" + "Document.docx");
    // Configure page setup options
    doc.getFirstSection().getPageSetup().setLayoutMode(SectionLayoutMode.GRID);
    doc.getFirstSection().getPageSetup().setCharactersPerLine(30);
    doc.getFirstSection().getPageSetup().setLinesPerPage(10);
    doc.save("Your Directory Path" + "WorkingWithDocumentOptionsAndSettings.DocumentPageSetup.docx");
}
```

إعداد الصفحة بدقة أمر أساسي لتنسيق المستند. تمكّنك Aspose.Words for Java من ضبط أوضاع التخطيط، **الأحرف في السطر**، والأسطر في الصفحة، لضمان مظهر جذاب لمستنداتك.

## تحديد لغات التحرير

```java
@Test
public void addJapaneseAsEditingLanguages() throws Exception
{
    LoadOptions loadOptions = new LoadOptions();
    // Set language preferences for editing
    loadOptions.getLanguagePreferences().addEditingLanguage(EditingLanguage.JAPANESE);
    Document doc = new Document("Your Directory Path" + "No default editing language.docx", loadOptions);
    // Check the overridden editing language
    int localeIdFarEast = doc.getStyles().getDefaultFont().getLocaleIdFarEast();
    System.out.println(localeIdFarEast == (int) EditingLanguage.JAPANESE
            ? "The document either has no any FarEast language set in defaults or it was set to Japanese originally."
            : "The document default FarEast language was set to another than Japanese language originally, so it is not overridden.");
}
```

تلعب لغات التحرير دورًا مهمًا في معالجة المستندات. باستخدام Aspose.Words for Java، يمكنك ضبط وتخصيص لغات التحرير لتلبية احتياجات المستند اللغوية.

## الخلاصة

في هذا الدليل، استعرضنا مختلف خيارات وإعدادات المستند المتاحة في Aspose.Words for Java. من التحسين وعرض الأخطاء إلى تنظيف الأنماط وخيارات العرض، توفر هذه المكتبة القوية إمكانات واسعة لإدارة وتخصيص مستنداتك.

## الأسئلة المتكررة

### كيف أقوم بتحسين مستند لإصدار Word معين؟

لتحسين مستند لإصدار Word معين، استخدم طريقة `optimizeFor` وحدد الإصدار المطلوب. على سبيل المثال، لتحسين مستند لـ Word 2016:

```java
Document doc = new Document("Your Directory Path" + "Document.docx");
doc.getCompatibilityOptions().optimizeFor(MsWordVersion.WORD_2016);
doc.save("Your Directory Path" + "OptimizedForWord2016.docx");
```

### كيف يمكنني تمييز الأخطاء النحوية والإملائية في مستند؟

يمكنك تمكين عرض الأخطاء النحوية والإملائية في المستند باستخدام الشيفرة التالية:

```java
Document doc = new Document("Your Directory Path" + "Document.docx");
doc.setShowGrammaticalErrors(true);
doc.setShowSpellingErrors(true);
doc.save("Your Directory Path" + "ShowErrors.docx");
```

### ما هدف تنظيف الأنماط والقوائم غير المستخدمة؟

يساعد تنظيف الأنماط والقوائم غير المستخدمة على الحفاظ على بنية مستند نظيفة ومنظمة. فهو يزيل الفوضى غير الضرورية، مما يحسن قابلية القراءة والاتساق.

### كيف يمكنني إزالة الأنماط المكررة من مستند؟

لإزالة الأنماط المكررة من مستند، استخدم طريقة `cleanup` مع تعيين خيار `duplicateStyle` إلى `true`. إليك مثالًا:

```java
Document doc = new Document("Your Directory Path" + "Document.docx");
CleanupOptions options = new CleanupOptions();
options.setDuplicateStyle(true);
doc.cleanup(options);
doc.save("Your Directory Path" + "CleanedDocument.docx");
```

### كيف أقوم بتخصيص خيارات عرض المستند؟

يمكنك تخصيص خيارات عرض المستند باستخدام فئة `ViewOptions`. على سبيل المثال، لتعيين نوع العرض إلى تخطيط الصفحة وتكبيره إلى 50%:

```java
Document doc = new Document("Your Directory Path" + "Document.docx");
doc.getViewOptions().setViewType(ViewType.PAGE_LAYOUT);
doc.getViewOptions().setZoomPercent(50);
doc.save("Your Directory Path" + "CustomView.docx");
```

## نصائح إضافية ومخاطر شائعة

- **فعّل كلًا من فحص الإملاء والنحو** عندما تحتاج إلى تدقيق شامل. نسيان أحد العلامتين (`setShowGrammaticalErrors` أو `setShowSpellingErrors`) قد يترك الأخطاء غير ملحوظة.  
- **عند ضبط عدد الأحرف في السطر**، تذكر أن القيمة تتفاعل مع الخط المختار وهوامش الصفحة. اختبر التخطيط الفعلي للمستند لتجنب الانقطاعات غير المتوقعة.  
- **عمليات التنظيف لا يمكن التراجع عنها** على الملف الأصلي. اعمل دائمًا على نسخة أو استخدم نظام تحكم بالإصدارات للحفاظ على النمط الأصلي.  
- **تفضيلات لغة التحرير** تؤثر على سلوك التدقيق الإملائي. إذا كنت تستهدف مستندات متعددة اللغات، أضف جميع اللغات ذات الصلة إلى `LanguagePreferences`.

---

**آخر تحديث:** 2026-01-16  
**تم الاختبار مع:** Aspose.Words for Java 24.12  
**المؤلف:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}