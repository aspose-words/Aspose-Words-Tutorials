---
"description": "В этом уроке мы рассмотрели различные расширенные возможности сохранения HTML-документов с помощью Aspose.Words for Java. Эти возможности позволяют вам создавать высококачественные HTML-документы"
"linktitle": "Сохранение HTML-документов с помощью"
"second_title": "API обработки документов Java Aspose.Words"
"title": "Расширенные возможности сохранения HTML-документов с помощью Aspose.Words Java"
"url": "/ru/java/document-loading-and-saving/advance-html-documents-saving-options/"
"weight": 16
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Расширенные возможности сохранения HTML-документов с помощью Aspose.Words Java


В этом уроке мы рассмотрим расширенные возможности сохранения HTML-документов, предоставляемые Aspose.Words для Java. Aspose.Words — это мощный Java API для работы с документами Word, предлагающий широкий спектр функций для обработки и преобразования документов.

## 1. Введение
Aspose.Words for Java позволяет вам работать с документами Word программно. В этом руководстве мы сосредоточимся на расширенных параметрах сохранения документов HTML, которые позволяют вам контролировать, как документы Word преобразуются в HTML.

## 2. Экспорт информации о круговом маршруте
The `exportRoundtripInformation` Метод позволяет экспортировать документы Word в HTML, сохраняя информацию о передаче. Эта информация может быть полезна, когда вы хотите преобразовать HTML обратно в формат Word, не теряя никаких деталей, специфичных для документа.

```java
public void exportRoundtripInformation() throws Exception {
    Document doc = new Document("Your Directory Path" + "Rendering.docx");
    HtmlSaveOptions saveOptions = new HtmlSaveOptions();
    saveOptions.setExportRoundtripInformation(true);
    doc.save("Your Directory Path" + "WorkingWithHtmlSaveOptions.ExportRoundtripInformation.html", saveOptions);
}
```

## 3. Экспорт шрифтов в формате Base64
С `exportFontsAsBase64` Метод позволяет экспортировать шрифты, используемые в документе, в виде закодированных в Base64 данных в HTML. Это гарантирует, что представление HTML сохранит те же стили шрифтов, что и исходный документ Word.

```java

public void exportFontsAsBase64() throws Exception {
    Document doc = new Document("Your Directory Path" + "Rendering.docx");
    HtmlSaveOptions saveOptions = new HtmlSaveOptions();
    saveOptions.setExportFontsAsBase64(true);
    doc.save("Your Directory Path" + "WorkingWithHtmlSaveOptions.ExportFontsAsBase64.html", saveOptions);
}
```

## 4. Экспорт ресурсов
The `exportResources` Метод позволяет указать тип таблицы стилей CSS и экспортировать ресурсы шрифтов. Вы также можете задать папку ресурсов и псевдоним для ресурсов в HTML.

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

## 5. Конвертировать метафайлы в EMF или WMF
The `convertMetafilesToEmfOrWmf` Метод позволяет преобразовывать метафайлы в документе в формат EMF или WMF, обеспечивая совместимость и плавную визуализацию в HTML.

```java

public void convertMetafilesToEmfOrWmf() throws Exception {

	string dataDir = "Your Document Directory";
    Document doc = new Document();
	DocumentBuilder builder = new DocumentBuilder(doc);

	builder.write("Here is an image as is: ");
	builder.insertHtml(
		"<img src=\"data:image/png;base64,\r\n                    iVBORw0KGgoAAAANSUhEUgAAAAoAAAAKCAYAAACNMs+9AAAABGdBTUEAALGP\r\n                    C/xhBQAAAAlwSFlzAAALEwAACxMBAJqcGAAAAAd0SU1FB9YGARc5KB0XV+IA\r\n                    AAAddEVYdENvbW1lbnQAQ3JlYXRlZCB3aXRoIFRoZSBHSU1Q72QlbgAAAF1J\r\n                    REFUGNO9zL0NglAAxPEfdLTs4BZM4DIO4C7OwQg2JoQ9LE1exdlYvBBeZ7jq\r\n                    ch9//q1uH4TLzw4d6+ErXMMcXuHWxId3KOETnnXXV6MJpcq2MLaI97CER3N0\r\n vr4MkhoXe0rZigAAAABJRU5ErkJggg==\" alt=\"Красная точка\" />");

	HtmlSaveOptions saveOptions = new HtmlSaveOptions(); { saveOptions.setMetafileFormat(HtmlMetafileFormat.EMF_OR_WMF); }

	doc.save(dataDir + "WorkingWithHtmlSaveOptions.ConvertMetafilesToEmfOrWmf.html", saveOptions);
}
```

## 6. Конвертировать метафайлы в SVG
Используйте `convertMetafilesToSvg` метод преобразования метафайлов в формат SVG. Этот формат идеально подходит для отображения векторной графики в HTML-документах.

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

## 7. Добавьте префикс имени класса CSS
С `addCssClassNamePrefix` Метод позволяет добавлять префикс к именам классов CSS в экспортированном HTML. Это помогает предотвратить конфликты с существующими стилями.

```java

public void addCssClassNamePrefix() throws Exception {
    Document doc = new Document("Your Directory Path" + "Rendering.docx");
    HtmlSaveOptions saveOptions = new HtmlSaveOptions();
    saveOptions.setCssStyleSheetType(CssStyleSheetType.EXTERNAL);
    saveOptions.setCssClassNamePrefix("pfx_");
    doc.save("Your Directory Path" + "WorkingWithHtmlSaveOptions.AddCssClassNamePrefix.html", saveOptions);
}
```

## 8. Экспортируйте URL-адреса CID для ресурсов MHTML
The `exportCidUrlsForMhtmlResources` Метод используется при сохранении документов в формате MHTML. Позволяет экспортировать URL Content-ID для ресурсов.

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

## 9. Разрешите названия шрифтов
The `resolveFontNames` Метод помогает разрешать названия шрифтов при сохранении документов в формате HTML, обеспечивая единообразную визуализацию на разных платформах.

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

## 10. Экспорт поля формы ввода текста как текста
The `exportTextInputFormFieldAsText` метод экспортирует поля формы как обычный текст в HTML, что делает их легко читаемыми и редактируемыми.

```java

public void exportTextInputFormFieldAsText() throws Exception {
    
	string dataDir = "Your Document Directory";
	Document doc = new Document(dataDir + "Rendering.docx");

	String imagesDir = Path.combine(dataDir, "Images");

	// Указанная папка должна существовать и быть пустой.
	if (Directory.exists(imagesDir))
		Directory.delete(imagesDir, true);

	Directory.createDirectory(imagesDir);

	// Установите опцию экспорта полей формы как обычного текста, а не как элементов ввода HTML.
	HtmlSaveOptions saveOptions = new HtmlSaveOptions(SaveFormat.HTML);
	{
		saveOptions.setExportTextInputFormFieldAsText(true); saveOptions.setImagesFolder(imagesDir);
	}

	doc.save(dataDir + "WorkingWithHtmlSaveOptions.ExportTextInputFormFieldAsText.html", saveOptions);
}
```

## Заключение
В этом уроке мы изучили расширенные возможности сохранения HTML-документов, предоставляемые Aspose.Words for Java. Эти возможности дают вам детальный контроль над процессом преобразования, позволяя создавать HTML-документы, которые очень похожи на исходные документы Word.

## Часто задаваемые вопросы
Вот некоторые часто задаваемые вопросы о работе с Aspose.Words для Java и параметрах сохранения документов HTML:

### В1: Как преобразовать HTML обратно в формат Word с помощью Aspose.Words для Java?
Чтобы преобразовать HTML обратно в формат Word, вы можете использовать API Aspose.Words `load` метод загрузки HTML-документа и последующего сохранения его в формате Word.

### В2: Могу ли я настраивать стили CSS при экспорте в HTML?
Да, вы можете настраивать стили CSS, изменяя таблицы стилей, используемые в HTML, или используя `addCssClassNamePrefix` метод добавления префикса к именам классов CSS.

### В3: Есть ли способ оптимизировать вывод HTML для отображения в Интернете?
Да, вы можете оптимизировать вывод HTML для отображения на веб-сайтах, настроив такие параметры, как экспорт шрифтов в формате Base64 и преобразование метафайлов в SVG.

### В4: Существуют ли какие-либо ограничения при конвертации сложных документов Word в HTML?
Хотя Aspose.Words для Java предоставляет мощные возможности конвертации, для получения желаемого результата в формате HTML сложным документам Word со сложной структурой может потребоваться дополнительная постобработка.



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}