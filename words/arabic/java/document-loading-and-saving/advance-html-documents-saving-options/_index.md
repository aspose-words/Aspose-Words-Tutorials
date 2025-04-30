---
"description": "في هذا البرنامج التعليمي، تناولنا خيارات متقدمة لحفظ مستندات HTML باستخدام Aspose.Words لجافا. تُمكّنك هذه الخيارات من إنشاء مستندات HTML عالية الجودة."
"linktitle": "حفظ مستندات HTML باستخدام"
"second_title": "واجهة برمجة تطبيقات معالجة مستندات Java Aspose.Words"
"title": "خيارات حفظ مستندات HTML المتقدمة باستخدام Aspose.Words Java"
"url": "/ar/java/document-loading-and-saving/advance-html-documents-saving-options/"
"weight": 16
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# خيارات حفظ مستندات HTML المتقدمة باستخدام Aspose.Words Java


في هذا البرنامج التعليمي، سنستكشف خيارات حفظ مستندات HTML المتقدمة التي يوفرها Aspose.Words لجافا. Aspose.Words هي واجهة برمجة تطبيقات Java فعّالة للعمل مع مستندات Word، وتوفر مجموعة واسعة من الميزات لمعالجة المستندات وتحويلها.

## 1. المقدمة
يتيح لك Aspose.Words for Java العمل مع مستندات Word برمجيًا. في هذا البرنامج التعليمي، سنركز على خيارات حفظ مستندات HTML المتقدمة، والتي تُمكّنك من التحكم في كيفية تحويل مستندات Word إلى HTML.

## 2. تصدير معلومات الرحلة ذهابًا وإيابًا
ال `exportRoundtripInformation` تتيح لك هذه الطريقة تصدير مستندات Word إلى HTML مع الحفاظ على معلومات النقل ذهابًا وإيابًا. يمكن أن تكون هذه المعلومات مفيدة عند تحويل HTML إلى تنسيق Word مرة أخرى دون فقدان أي تفاصيل خاصة بالمستند.

```java
public void exportRoundtripInformation() throws Exception {
    Document doc = new Document("Your Directory Path" + "Rendering.docx");
    HtmlSaveOptions saveOptions = new HtmlSaveOptions();
    saveOptions.setExportRoundtripInformation(true);
    doc.save("Your Directory Path" + "WorkingWithHtmlSaveOptions.ExportRoundtripInformation.html", saveOptions);
}
```

## 3. تصدير الخطوط بتنسيق Base64
مع `exportFontsAsBase64` باستخدام هذه الطريقة، يمكنك تصدير الخطوط المستخدمة في المستند كبيانات مُرمَّزة بتنسيق Base64 بتنسيق HTML. هذا يضمن احتفاظ تمثيل HTML بنفس أنماط الخطوط الموجودة في مستند Word الأصلي.

```java

public void exportFontsAsBase64() throws Exception {
    Document doc = new Document("Your Directory Path" + "Rendering.docx");
    HtmlSaveOptions saveOptions = new HtmlSaveOptions();
    saveOptions.setExportFontsAsBase64(true);
    doc.save("Your Directory Path" + "WorkingWithHtmlSaveOptions.ExportFontsAsBase64.html", saveOptions);
}
```

## 4. تصدير الموارد
ال `exportResources` تتيح لك هذه الطريقة تحديد نوع جدول أنماط CSS وتصدير موارد الخطوط. كما يمكنك تحديد مجلد موارد واسم مستعار للموارد في HTML.

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

## 5. تحويل ملفات التعريف إلى EMF أو WMF
ال `convertMetafilesToEmfOrWmf` تتيح لك الطريقة تحويل ملفات التعريف في المستند إلى تنسيق EMF أو WMF، مما يضمن التوافق والتقديم السلس في HTML.

```java

public void convertMetafilesToEmfOrWmf() throws Exception {

	string dataDir = "Your Document Directory";
    Document doc = new Document();
	DocumentBuilder builder = new DocumentBuilder(doc);

	builder.write("Here is an image as is: ");
	builder.insertHtml(
		"<img src=\"data:image/png;base64,\r\n                    iVBORw0KGgoAAAANSUhEUgAAAAoAAAAKCAYAAACNMs+9AAAABGdBTUEAALGP\r\n                    C/xhBQAAAAlwSFlzAAALEwAACxMBAJqcGAAAAAd0SU1FB9YGARc5KB0XV+IA\r\n                    AAAddEVYdENvbW1lbnQAQ3JlYXRlZCB3aXRoIFRoZSBHSU1Q72QlbgAAAF1J\r\n                    REFUGNO9zL0NglAAxPEfdLTs4BZM4DIO4C7OwQg2JoQ9LE1exdlYvBBeZ7jq\r\n                    ch9//q1uH4TLzw4d6+ErXMMcXuHWxId3KOETnnXXV6MJpcq2MLaI97CER3N0\r\n vr4MkhoXe0rZigAAAABJRU5ErkJggg==\" alt=\"Red dot\" />");

	HtmlSaveOptions saveOptions = new HtmlSaveOptions(); { saveOptions.setMetafileFormat(HtmlMetafileFormat.EMF_OR_WMF); }

	doc.save(dataDir + "WorkingWithHtmlSaveOptions.ConvertMetafilesToEmfOrWmf.html", saveOptions);
}
```

## 6. تحويل ملفات التعريف إلى SVG
استخدم `convertMetafilesToSvg` طريقة لتحويل ملفات التعريف إلى صيغة SVG. هذه الصيغة مثالية لعرض الرسومات المتجهة في مستندات HTML.

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

## 7. أضف بادئة اسم فئة CSS
مع `addCssClassNamePrefix` يمكنك إضافة بادئة لأسماء فئات CSS في ملف HTML المُصدَّر. هذا يُساعد على منع التعارضات مع الأنماط الحالية.

```java

public void addCssClassNamePrefix() throws Exception {
    Document doc = new Document("Your Directory Path" + "Rendering.docx");
    HtmlSaveOptions saveOptions = new HtmlSaveOptions();
    saveOptions.setCssStyleSheetType(CssStyleSheetType.EXTERNAL);
    saveOptions.setCssClassNamePrefix("pfx_");
    doc.save("Your Directory Path" + "WorkingWithHtmlSaveOptions.AddCssClassNamePrefix.html", saveOptions);
}
```

## 8. تصدير عناوين URL الخاصة بـ CID لموارد MHTML
ال `exportCidUrlsForMhtmlResources` تُستخدم هذه الطريقة لحفظ المستندات بتنسيق MHTML. تتيح هذه الطريقة تصدير عناوين URL لمعرف المحتوى للموارد.

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

## 9. حل أسماء الخطوط
ال `resolveFontNames` تساعد الطريقة على حل أسماء الخطوط عند حفظ المستندات بتنسيق HTML، مما يضمن عرضًا متسقًا عبر منصات مختلفة.

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

## 10. تصدير حقل نموذج إدخال النص كنص
ال `exportTextInputFormFieldAsText` تقوم الطريقة بتصدير حقول النموذج كنص عادي في HTML، مما يجعلها قابلة للقراءة والتحرير بسهولة.

```java

public void exportTextInputFormFieldAsText() throws Exception {
    
	string dataDir = "Your Document Directory";
	Document doc = new Document(dataDir + "Rendering.docx");

	String imagesDir = Path.combine(dataDir, "Images");

	// يجب أن يكون المجلد المحدد موجودًا ويجب أن يكون فارغًا.
	if (Directory.exists(imagesDir))
		Directory.delete(imagesDir, true);

	Directory.createDirectory(imagesDir);

	// تعيين خيار لتصدير حقول النموذج كنص عادي، وليس كعناصر إدخال HTML.
	HtmlSaveOptions saveOptions = new HtmlSaveOptions(SaveFormat.HTML);
	{
		saveOptions.setExportTextInputFormFieldAsText(true); saveOptions.setImagesFolder(imagesDir);
	}

	doc.save(dataDir + "WorkingWithHtmlSaveOptions.ExportTextInputFormFieldAsText.html", saveOptions);
}
```

## خاتمة
في هذا البرنامج التعليمي، استكشفنا خيارات حفظ مستندات HTML المتقدمة التي يوفرها Aspose.Words لجافا. تمنحك هذه الخيارات تحكمًا دقيقًا في عملية التحويل، مما يسمح لك بإنشاء مستندات HTML تشبه إلى حد كبير مستندات Word الأصلية.

## الأسئلة الشائعة
فيما يلي بعض الأسئلة الشائعة حول العمل مع Aspose.Words لخيارات حفظ مستندات Java وHTML:

### س1: كيف يمكنني تحويل HTML إلى تنسيق Word باستخدام Aspose.Words لـ Java؟
لتحويل HTML إلى تنسيق Word مرة أخرى، يمكنك استخدام واجهة برمجة التطبيقات Aspose.Words `load` طريقة تحميل مستند HTML ثم حفظه بتنسيق Word.

### س2: هل يمكنني تخصيص أنماط CSS عند التصدير إلى HTML؟
نعم، يمكنك تخصيص أنماط CSS عن طريق تعديل أوراق الأنماط المستخدمة في HTML أو باستخدام `addCssClassNamePrefix` طريقة لإضافة بادئة إلى أسماء فئات CSS.

### س3: هل هناك طريقة لتحسين مخرجات HTML لعرضها على الويب؟
نعم، يمكنك تحسين مخرجات HTML لعرض الويب من خلال تكوين خيارات مثل تصدير الخطوط بتنسيق Base64 وتحويل الملفات التعريفية إلى SVG.

### س4: هل هناك أية قيود عند تحويل مستندات Word المعقدة إلى HTML؟
على الرغم من أن Aspose.Words for Java يوفر إمكانيات تحويل قوية، إلا أن مستندات Word المعقدة ذات التخطيطات المعقدة قد تتطلب معالجة لاحقة إضافية لتحقيق الناتج HTML المطلوب.



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}