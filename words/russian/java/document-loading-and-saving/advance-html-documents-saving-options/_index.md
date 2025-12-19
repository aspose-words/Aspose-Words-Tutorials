---
date: 2025-12-19
description: Узнайте, как экспортировать HTML с помощью Aspose.Words Java, включая
  расширенные параметры сохранения Word в HTML и эффективного преобразования Word
  в HTML.
linktitle: Saving HTML Documents with
second_title: Aspose.Words Java Document Processing API
title: 'Как экспортировать HTML с помощью Aspose.Words Java: расширенные параметры'
url: /ru/java/document-loading-and-saving/advance-html-documents-saving-options/
weight: 16
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Как экспортировать HTML с помощью Aspose.Words Java: расширенные параметры

В этом руководстве вы узнаете **как экспортировать HTML** из документов Word, используя Aspose.Words for Java. Независимо от того, нужно ли вам **сохранить Word как HTML** для публикации в вебе или **конвертировать Word в HTML** для последующей обработки, расширенные параметры сохранения предоставляют точный контроль над результатом. Мы пошагово рассмотрим каждый параметр, объясним, когда его использовать, и покажем реальные сценарии, где эти настройки имеют значение.

## Быстрые ответы
- **Какой основной класс для экспорта HTML?** `HtmlSaveOptions`  
- **Можно ли встроить шрифты непосредственно в HTML?** Да, установите `exportFontsAsBase64` в `true`.  
- **Как сохранить данные обратного пути, специфичные для Word?** Включите `exportRoundtripInformation`.  
- **Какой формат лучше всего подходит для векторной графики?** Используйте `convertMetafilesToSvg` для вывода в SVG.  
- **Можно ли избежать конфликтов имён CSS‑классов?** Да, используйте `addCssClassNamePrefix`.

## 1. Введение
Aspose.Words for Java — мощный API, позволяющий разработчикам программно работать с документами Word. В этом руководстве рассматриваются расширенные параметры сохранения HTML‑документов, которые позволяют настроить процесс конвертации под конкретные требования веба или интеграции.

## 2. Экспорт информации обратного пути
Сохранение информации обратного пути позволяет конвертировать HTML обратно в документ Word без потери макета или деталей форматирования.

```java
public void exportRoundtripInformation() throws Exception {
    Document doc = new Document("Your Directory Path" + "Rendering.docx");
    HtmlSaveOptions saveOptions = new HtmlSaveOptions();
    saveOptions.setExportRoundtripInformation(true);
    doc.save("Your Directory Path" + "WorkingWithHtmlSaveOptions.ExportRoundtripInformation.html", saveOptions);
}
```

### Когда использовать
- Когда нужен обратимый конвейер преобразования (HTML → Word → HTML).  
- Идеально для сценариев совместного редактирования, где необходимо сохранить исходную структуру Word.

## 3. Экспорт шрифтов как Base64
Встраивание шрифтов непосредственно в HTML устраняет зависимости от внешних шрифтов и обеспечивает визуальную точность во всех браузерах.

```java

public void exportFontsAsBase64() throws Exception {
    Document doc = new Document("Your Directory Path" + "Rendering.docx");
    HtmlSaveOptions saveOptions = new HtmlSaveOptions();
    saveOptions.setExportFontsAsBase64(true);
    doc.save("Your Directory Path" + "WorkingWithHtmlSaveOptions.ExportFontsAsBase64.html", saveOptions);
}
```

### Профессиональный совет
Используйте эту опцию, когда целевая среда имеет ограниченный доступ к внешним ресурсам (например, рассылки по электронной почте).

## 4. Экспорт ресурсов
Управляйте тем, как генерируются CSS и шрифтовые ресурсы, и указывайте пользовательскую папку или URL‑псевдоним для этих активов.

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

### Почему это важно
Вынос CSS в отдельный файл уменьшает размер HTML и позволяет кэшировать его для более быстрой загрузки страниц.

## 5. Конвертация метафайлов в EMF или WMF
Метафайлы (например, EMF/WMF) конвертируются в формат, который браузеры могут надёжно отображать.

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

### Сценарий использования
Выбирайте EMF/WMF, когда целевые браузеры поддерживают эти векторные форматы и вам требуется масштабирование без потерь.

## 6. Конвертация метафайлов в SVG
SVG обеспечивает лучшую масштабируемость и широко поддерживается современными браузерами.

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

### Преимущество
Файлы SVG лёгкие и сохраняют независимость от разрешения документа, что идеально для адаптивного веб‑дизайна.

## 7. Добавление префикса к именам CSS‑классов
Предотвратите конфликты стилей, добавив префикс ко всем сгенерированным именам CSS‑классов.

```java

public void addCssClassNamePrefix() throws Exception {
    Document doc = new Document("Your Directory Path" + "Rendering.docx");
    HtmlSaveOptions saveOptions = new HtmlSaveOptions();
    saveOptions.setCssStyleSheetType(CssStyleSheetType.EXTERNAL);
    saveOptions.setCssClassNamePrefix("pfx_");
    doc.save("Your Directory Path" + "WorkingWithHtmlSaveOptions.AddCssClassNamePrefix.html", saveOptions);
}
```

### Практический совет
Используйте уникальный префикс (например, название вашего проекта) при внедрении HTML в существующие страницы, чтобы избежать конфликтов CSS.

## 8. Экспорт CID‑URL для ресурсов MHTML
При сохранении в формате MHTML можно экспортировать ресурсы, используя URL‑адреса Content‑ID для лучшей совместимости с электронной почтой.

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

### Когда использовать
Идеально для создания единого, автономного HTML‑файла, который можно прикреплять к письмам.

## 9. Разрешение имён шрифтов
Обеспечивает, что HTML ссылается на правильные семейства шрифтов, улучшая кроссплатформенную согласованность.

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

### Почему это полезно
Если оригинальный документ использует шрифты, не установленные на клиентском компьютере, эта опция заменит их веб‑безопасными альтернативами.

## 10. Экспорт текстового поля формы как текста
Отображайте поля формы как обычный текст вместо интерактивных HTML‑элементов ввода.

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

### Сценарий использования
Когда требуется только чтение формы для архивирования или печати.

## Распространённые ошибки и их устранение
| Проблема | Типичная причина | Решение |
|----------|------------------|---------|
| Отсутствуют шрифты в выводе | `exportFontsAsBase64` не включён | Установите `setExportFontsAsBase64(true)` |
| CSS ломается после встраивания | Используется `EXTERNAL` без указания CSS‑файла | Убедитесь, что CSS‑файл размещён по указанному `resourceFolderAlias` |
| Большой размер HTML | Встраивание множества изображений в Base64 | Перейдите на внешние ресурсы изображений через `setExportFontResources(true)` и настройте `resourceFolder` |
| SVG не отображается в старых браузерах | Браузер не поддерживает SVG | Предоставьте резервный PNG, также экспортируя в EMF/WMF |

## Часто задаваемые вопросы

**В: Можно ли одновременно встраивать шрифты как Base64 и сохранять внешний CSS?**  
О: Да. Установите `exportFontsAsBase64(true)`, оставив `CssStyleSheetType.EXTERNAL` для отделения данных шрифтов от правил стилей.

**В: Как конвертировать существующий HTML обратно в документ Word?**  
О: Загрузите HTML с помощью `Document doc = new Document("input.html");`, затем `doc.save("output.docx");`. Сохраните данные обратного пути, используя `exportRoundtripInformation` при первоначальном экспорте.

**В: Влияет ли использование конвертации в SVG на производительность?**  
О: Конвертация больших метафайлов в SVG может увеличить время обработки, но полученный HTML обычно меньше и быстрее рендерится в браузерах.

**В: Работают ли эти параметры с Aspose.Words для .NET?**  
О: Те же концепции присутствуют в .NET API, хотя имена методов могут немного отличаться (например, `HtmlSaveOptions` используется в обеих платформах).

**В: Какой вариант выбрать для HTML, пригодного для электронной почты?**  
О: Используйте `SaveFormat.MHTML` с `exportCidUrlsForMhtmlResources`, чтобы встроить все ресурсы непосредственно в тело письма.

---

**Последнее обновление:** 2025-12-19  
**Тестировано с:** Aspose.Words for Java 24.12  
**Автор:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}