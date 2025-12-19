---
date: 2025-12-19
description: تعرّف على كيفية تصدير HTML باستخدام Aspose.Words Java، مع تغطية الخيارات
  المتقدمة لحفظ مستند Word كـ HTML وتحويل Word إلى HTML بكفاءة.
linktitle: Saving HTML Documents with
second_title: Aspose.Words Java Document Processing API
title: 'كيفية تصدير HTML باستخدام Aspose.Words Java: خيارات متقدمة'
url: /ar/java/document-loading-and-saving/advance-html-documents-saving-options/
weight: 16
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# كيفية تصدير HTML باستخدام Aspose.Words Java: الخيارات المتقدمة

في هذا البرنامج التعليمي ستكتشف **كيفية تصدير HTML** من مستندات Word باستخدام Aspose.Words for Java. سواء كنت بحاجة إلى **حفظ Word كـ HTML** للنشر على الويب أو **تحويل Word إلى HTML** للمعالجة اللاحقة، فإن خيارات الحفظ المتقدمة تمنحك تحكمًا دقيقًا في الناتج. سنستعرض كل خيار خطوة بخطوة، نشرح متى يُستخدم، ونظهر سيناريوهات واقعية حيث تُحدث هذه الإعدادات فرقًا.

## إجابات سريعة
- **ما هو الصنف الأساسي لتصدير HTML؟** `HtmlSaveOptions`  
- **هل يمكن تضمين الخطوط مباشرة في HTML؟** نعم، اضبط `exportFontsAsBase64` على `true`.  
- **كيف أحافظ على بيانات الجولة‑العودة الخاصة بـ Word؟** فعّل `exportRoundtripInformation`.  
- **أي تنسيق هو الأفضل للرسومات المتجهة؟** استخدم `convertMetafilesToSvg` للحصول على مخرجات SVG.  
- **هل يمكن تجنب تصادم أسماء فئات CSS؟** نعم، استخدم `addCssClassNamePrefix`.

## 1. مقدمة
Aspose.Words for Java هو API قوي يتيح للمطورين معالجة مستندات Word برمجيًا. يركز هذا الدليل على خيارات حفظ مستند HTML المتقدمة التي تسمح لك بتخصيص عملية التحويل لتلبية متطلبات الويب أو التكامل المحددة.

## 2. تصدير معلومات الجولة‑العودة
الحفاظ على معلومات الجولة‑العودة يتيح لك تحويل HTML مرة أخرى إلى مستند Word دون فقدان تفاصيل التخطيط أو التنسيق.

```java
public void exportRoundtripInformation() throws Exception {
    Document doc = new Document("Your Directory Path" + "Rendering.docx");
    HtmlSaveOptions saveOptions = new HtmlSaveOptions();
    saveOptions.setExportRoundtripInformation(true);
    doc.save("Your Directory Path" + "WorkingWithHtmlSaveOptions.ExportRoundtripInformation.html", saveOptions);
}
```

### متى يُستخدم
- عندما تحتاج إلى خط أنابيب تحويل قابل للعكس (HTML → Word → HTML).  
- مثالي لسيناريوهات التحرير التعاوني حيث يجب الاحتفاظ بالبنية الأصلية لـ Word.

## 3. تصدير الخطوط كـ Base64
تضمين الخطوط مباشرة في HTML يلغي الاعتماد على خطوط خارجية ويضمن الحفاظ على المظهر عبر المتصفحات.

```java

public void exportFontsAsBase64() throws Exception {
    Document doc = new Document("Your Directory Path" + "Rendering.docx");
    HtmlSaveOptions saveOptions = new HtmlSaveOptions();
    saveOptions.setExportFontsAsBase64(true);
    doc.save("Your Directory Path" + "WorkingWithHtmlSaveOptions.ExportFontsAsBase64.html", saveOptions);
}
```

### نصيحة احترافية
استخدم هذا الخيار عندما يكون للبيئة المستهدفة وصول محدود إلى الموارد الخارجية (مثل النشرات البريدية).

## 4. تصدير الموارد
تحكم في كيفية إخراج موارد CSS والخطوط، وحدد مجلدًا مخصصًا أو اسمًا مستعارًا URL لتلك الأصول.

```java

public void exportResources() throws Exception {
    Document doc = new Document("Your Directory Path" + "Rendering.docx");
    HtmlSaveOptions saveOptions = new HtmlSaveOptions();
    saveOptions.setCssStyleSheetType(CssStyleSheetType.EXTERNAL);
    saveOptions.setExportFontResources(true);
    saveOptions.setResourceFolder("Your Directory Path" + "Resources");
    saveOptions.setResourceFolderAlias("http://example.com/resources");
    doc.save("Your Directory Path" + "WorkingWithHtmlSaveOptions.ExportResources.html", saveOptions);
}
```

### لماذا يهم
فصل CSS في ملف خارجي يقلل من حجم HTML ويسمح بالتخزين المؤقت لتسريع تحميل الصفحات.

## 5. تحويل ملفات الميتا إلى EMF أو WMF
يتم تحويل ملفات الميتا (مثل EMF/WMF) إلى تنسيق يمكن للمتصفحات عرضه بثقة.

```java

public void convertMetafilesToEmfOrWmf() throws Exception {

	string dataDir = "Your Document Directory";
    Document doc = new Document();
	DocumentBuilder builder = new DocumentBuilder(doc);

	builder.write("Here is an image as is: ");
	builder.insertHtml(
		"<img src=\"data:image/png;base64,\r\n                    iVBORw0KGgoAAAANSUhEUgAAAAoAAAAKCAYAAACNMs+9AAAABGdBTUEAALGP\r\n                    C/xhBQAAAAlwSFlzAAALEwAACxMBAJqcGAAAAAd0SU1FB9YGARc5KB0XV+IA\r\n                    AAAddEVYdENvbW1lbnQAQ3JlYXRlZCB3aXRoIFRoZSBHSU1Q72QlbgAAAF1J\r\n                    REFUGNO9zL0NglAAxPEfdLTs4BZM4DIO4C7OwQg2JoQ9LE1exdlYvBBeZ7jq\r\n                    ch9//q1uH4TLzw4d6+ErXMMcXuHWxId3KOETnnXXV6MJpcq2MLaI97CER3N0\r\n                    vr4MkhoXe0rZigAAAABJRU5ErkJggg==\" alt=\"Red dot\" />");

	HtmlSaveOptions saveOptions = new HtmlSaveOptions(); { saveOptions.setMetafileFormat(HtmlMetafileFormat.EMF_OR_WMF); }

	doc.save(dataDir + "WorkingWithHtmlSaveOptions.ConvertMetafilesToEmfOrWmf.html", saveOptions);
}
```

### حالة الاستخدام
اختر EMF/WMF عندما تدعم المتصفحات المستهدفة هذه الصيغ المتجهة وتحتاج إلى توسع بدون فقدان الجودة.

## 6. تحويل ملفات الميتا إلى SVG
يوفر SVG أفضل قابلية للتوسع وهو مدعوم على نطاق واسع في المتصفحات الحديثة.

```java

public void convertMetafilesToSvg() throws Exception {
	string dataDir = "Your Document Directory";
    Document doc = new Document();
	DocumentBuilder builder = new DocumentBuilder(doc);
	
	builder.write("Here is an SVG image: ");
	builder.insertHtml(
		"<svg height='210' width='500'>\r\n                <polygon points='100,10 40,198 190,78 10,78 160,198' \r\n                    style='fill:lime;stroke:purple;stroke-width:5;fill-rule:evenodd;' />\r\n            </svg> ");

	HtmlSaveOptions saveOptions = new HtmlSaveOptions(); { saveOptions.setMetafileFormat(HtmlMetafileFormat.SVG); }

	doc.save(dataDir + "WorkingWithHtmlSaveOptions.ConvertMetafilesToSvg.html", saveOptions);
}
```

### الفائدة
ملفات SVG خفيفة الوزن وتبقى مستقلة عن الدقة، مما يجعلها مثالية لتصميم ويب متجاوب.

## 7. إضافة بادئة لاسم فئة CSS
تجنب تعارض الأنماط عن طريق إضافة بادئة لجميع أسماء فئات CSS التي يتم إنشاؤها.

```java

public void addCssClassNamePrefix() throws Exception {
    Document doc = new Document("Your Directory Path" + "Rendering.docx");
    HtmlSaveOptions saveOptions = new HtmlSaveOptions();
    saveOptions.setCssStyleSheetType(CssStyleSheetType.EXTERNAL);
    saveOptions.setCssClassNamePrefix("pfx_");
    doc.save("Your Directory Path" + "WorkingWithHtmlSaveOptions.AddCssClassNamePrefix.html", saveOptions);
}
```

### نصيحة عملية
استخدم بادئة فريدة (مثل اسم مشروعك) عند دمج HTML في صفحات موجودة لتفادي تضارب CSS.

## 8. تصدير عناوين CID لموارد MHTML
عند الحفظ كـ MHTML، يمكنك تصدير الموارد باستخدام عناوين Content‑ID لتحسين توافق البريد الإلكتروني.

```java

public void exportCidUrlsForMhtmlResources() throws Exception {
	string dataDir = "Your Document Directory";
    Document doc = new Document(dataDir + "Content-ID.docx");

	HtmlSaveOptions saveOptions = new HtmlSaveOptions(SaveFormat.MHTML);
	{
		saveOptions.setPrettyFormat(true); saveOptions.setExportCidUrlsForMhtmlResources(true);
	}

	doc.save(dataDir + "WorkingWithHtmlSaveOptions.ExportCidUrlsForMhtmlResources.mhtml", saveOptions);
}
```

### متى يُستخدم
مثالي لإنشاء ملف HTML واحد متكامل يمكن إرفاقه بالبريد الإلكتروني.

## 9. حل أسماء الخطوط
يضمن أن يشير HTML إلى عائلات الخطوط الصحيحة، مما يحسن التناسق عبر الأنظمة.

```java

public void resolveFontNames() throws Exception {
    
	string dataDir = "Your Document Directory";
	Document doc = new Document(dataDir + "Missing font.docx");

	HtmlSaveOptions saveOptions = new HtmlSaveOptions(SaveFormat.HTML);
	{
		saveOptions.setPrettyFormat(true); saveOptions.setResolveFontNames(true);
	}

	doc.save(dataDir + "WorkingWithHtmlSaveOptions.ResolveFontNames.html", saveOptions);
}
```

### لماذا يساعد
إذا كان المستند الأصلي يستخدم خطوطًا غير مثبتة على جهاز العميل، فإن هذا الخيار يستبدلها ببدائل آمنة للويب.

## 10. تصدير حقل نموذج النص كـ Text
يعرض حقول النماذج كنص عادي بدلاً من عناصر إدخال HTML التفاعلية.

```java

public void exportTextInputFormFieldAsText() throws Exception {
    
	string dataDir = "Your Document Directory";
	Document doc = new Document(dataDir + "Rendering.docx");

	String imagesDir = Path.combine(dataDir, "Images");

	// The folder specified needs to exist and should be empty.
	if (Directory.exists(imagesDir))
		Directory.delete(imagesDir, true);

	Directory.createDirectory(imagesDir);

	// Set an option to export form fields as plain text, not as HTML input elements.
	HtmlSaveOptions saveOptions = new HtmlSaveOptions(SaveFormat.HTML);
	{
		saveOptions.setExportTextInputFormFieldAsText(true); saveOptions.setImagesFolder(imagesDir);
	}

	doc.save(dataDir + "WorkingWithHtmlSaveOptions.ExportTextInputFormFieldAsText.html", saveOptions);
}
```

### حالة الاستخدام
عند الحاجة إلى تمثيل للقراءة فقط لنموذج لأغراض الأرشفة أو الطباعة.

## المشكلات الشائعة & استكشاف الأخطاء
| المشكلة | السبب الشائع | الحل |
|-------|---------------|-----|
| فقدان الخطوط في الناتج | عدم تفعيل `exportFontsAsBase64` | اضبط `setExportFontsAsBase64(true)` |
| تعطل CSS بعد الدمج | استخدام `EXTERNAL` دون توفير ملف CSS | تأكد من نشر ملف CSS في `resourceFolderAlias` المحدد |
| حجم HTML كبير | تضمين العديد من الصور كـ Base64 | انتقل إلى موارد صور خارجية عبر `setExportFontResources(true)` وتهيئة `resourceFolder` |
| عدم عرض SVG في المتصفحات القديمة | المتصفح لا يدعم SVG | قدم صورة PNG بديلة عن طريق تصديرها أيضًا كـ EMF/WMF |

## الأسئلة المتكررة

**س: هل يمكنني تضمين الخطوط كـ Base64 مع الحفاظ على CSS خارجي؟**  
ج: نعم. اضبط `exportFontsAsBase64(true)` مع إبقاء `CssStyleSheetType.EXTERNAL` لفصل بيانات الخط عن قواعد الأنماط.

**س: كيف أحول HTML موجود إلى مستند Word؟**  
ج: استخدم `Document doc = new Document("input.html");` ثم `doc.save("output.docx");`. حافظ على بيانات الجولة‑العودة باستخدام `exportRoundtripInformation` أثناء التصدير الأولي.

**س: هل هناك تأثير على الأداء عند استخدام تحويل SVG؟**  
ج: تحويل ملفات ميتا الكبيرة إلى SVG قد يزيد من زمن المعالجة، لكن HTML الناتج يكون أصغر عادةً ويُعرض أسرع في المتصفحات.

**س: هل تعمل هذه الخيارات مع Aspose.Words لـ .NET أيضًا؟**  
ج: المفاهيم نفسها موجودة في API .NET، رغم أن أسماء الطرق قد تختلف قليلًا (مثل `HtmlSaveOptions` مشتركة بين المنصات).

**س: أي خيار يجب اختياره للحصول على HTML مناسب للبريد الإلكتروني؟**  
ج: استخدم `SaveFormat.MHTML` مع `exportCidUrlsForMhtmlResources` لتضمين جميع الموارد مباشرة في جسم البريد.

---

**آخر تحديث:** 2025-12-19  
**تم الاختبار مع:** Aspose.Words for Java 24.12  
**المؤلف:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}