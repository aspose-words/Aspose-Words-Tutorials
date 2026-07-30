---
date: 2025-12-27
description: Узнайте, как задать LoadOptions в Aspose.Words для Java, включая указание
  временной папки, установку версии Word, преобразование метафайлов в PNG и преобразование
  фигур в математические формулы для гибкой обработки документов.
linktitle: Using Load Options
second_title: Aspose.Words Java Document Processing API
title: Как установить LoadOptions в Aspose.Words для Java
url: /ru/java/document-loading-and-saving/using-load-options/
weight: 11
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Как установить LoadOptions в Aspose.Words для Java

В этом руководстве мы рассмотрим **как установить LoadOptions** для различных реальных сценариев работы с Aspose.Words для Java. LoadOptions предоставляют тонкую настройку того, как открывается документ — будь то необходимость обновить «грязные» поля, работать с зашифрованными файлами, конвертировать фигуры в Office Math или указать библиотеке, где хранить временные данные. К концу вы сможете настроить поведение загрузки в соответствии с точными требованиями вашего приложения.

## Быстрые ответы
- **Что такое LoadOptions?** Объект конфигурации, влияющий на то, как Aspose.Words загружает документ.  
- **Можно ли обновлять поля при загрузке?** Да — установите `setUpdateDirtyFields(true)`.  
- **Как открыть файл, защищённый паролем?** Передайте пароль конструктору `LoadOptions`.  
- **Можно ли изменить временную папку?** Используйте `setTempFolder("path")`.  
- **Какой метод конвертирует фигуры в Office Math?** `setConvertShapeToOfficeMath(true)`.

## Зачем использовать LoadOptions?
LoadOptions позволяют избежать дополнительных шагов после загрузки, снизить использование памяти и гарантировать, что документ интерпретируется точно так, как вам нужно. Например, конвертация метафайлов в PNG во время загрузки предотвращает проблемы с последующей растеризацией, а указание версии MS Word помогает сохранять точность макета при работе со старыми файлами.

## Предварительные требования
- Java 17 или новее  
- Aspose.Words for Java (последняя версия)  
- Действительная лицензия Aspose для использования в продакшене  

## Пошаговое руководство

### Обновление грязных полей

Если документ содержит поля, которые были изменены, но не обновлены, вы можете указать Aspose.Words автоматически обновлять их при загрузке.

```java
LoadOptions loadOptions = new LoadOptions();
loadOptions.setUpdateDirtyFields(true);

Document doc = new Document("Your Directory Path" + "Dirty field.docx", loadOptions);
doc.save("Your Directory Path" + "WorkingWithLoadOptions.UpdateDirtyFields.docx");
```

*Вызов `setUpdateDirtyFields(true)` гарантирует, что любые «грязные» поля будут пересчитаны сразу после открытия документа.*

### Загрузка зашифрованного документа

Если ваш исходный файл защищён паролем, укажите пароль при создании экземпляра `LoadOptions`. Вы также можете задать новый пароль при сохранении в другой формат.

```java
@Test
public void loadEncryptedDocument() throws Exception {
    Document doc = new Document("Your Directory Path" + "Encrypted.docx", new LoadOptions("docPassword"));
    doc.save("Your Directory Path" + "WorkingWithLoadOptions.LoadAndSaveEncryptedOdt.odt", new OdtSaveOptions("newPassword"));
}
```

### Конвертация фигур в Office Math

Некоторые старые документы хранят уравнения в виде графических фигур. Включение этой опции преобразует такие фигуры в нативные объекты Office Math, которые позже легче редактировать.

```java
LoadOptions loadOptions = new LoadOptions();
loadOptions.setConvertShapeToOfficeMath(true);

Document doc = new Document("Your Directory Path" + "Office math.docx", loadOptions);
doc.save("Your Directory Path" + "WorkingWithLoadOptions.ConvertShapeToOfficeMath.docx");
```

### Установка версии MS Word

Указание целевой версии Word помогает библиотеке выбрать правильные правила рендеринга, особенно при работе со старыми форматами файлов.

```java
@Test
public void setMsWordVersion() throws Exception {
    LoadOptions loadOptions = new LoadOptions();
    loadOptions.setMswVersion(MsWordVersion.WORD_2010);

    Document doc = new Document("Your Directory Path" + "Document.docx", loadOptions);
    doc.save("Your Directory Path" + "WorkingWithLoadOptions.SetMsWordVersion.docx");
}
```

### Использование временной папки

Большие документы могут создавать временные файлы (например, при извлечении изображений). Вы можете направить эти файлы в выбранную вами папку, что полезно в изолированных средах.

```java
@Test
public void useTempFolder() throws Exception {
    LoadOptions loadOptions = new LoadOptions();
    loadOptions.setTempFolder("Your Directory Path");

    Document doc = new Document("Your Directory Path" + "Document.docx", loadOptions);
}
```

### Обратный вызов предупреждений

Во время загрузки Aspose.Words может генерировать предупреждения (например, о неподдерживаемых функциях). Реализация обратного вызова позволяет регистрировать или реагировать на эти события.

```java
@Test
public void warningCallback() throws Exception {
    LoadOptions loadOptions = new LoadOptions();
    loadOptions.setWarningCallback(new DocumentLoadingWarningCallback());

    Document doc = new Document("Your Directory Path" + "Document.docx", loadOptions);
}

public static class DocumentLoadingWarningCallback implements IWarningCallback {
    public void warning(WarningInfo info) {
        // Handle warnings as they arise during document loading.
        System.out.println(MessageFormat.format("WARNING: {0}, source: {1}", info.getWarningType(), info.getSource()));
        System.out.println(MessageFormat.format("\tDescription: {0}", info.getDescription()));
    }
}
```

### Конвертация метафайлов в PNG

Метафайлы, такие как WMF, могут быть растеризованы в PNG при загрузке, обеспечивая согласованное отображение на разных платформах.

```java
@Test
public void convertMetafilesToPng() throws Exception {
    LoadOptions loadOptions = new LoadOptions();
    loadOptions.setConvertMetafilesToPng(true);

    Document doc = new Document("Your Directory Path" + "WMF with image.docx", loadOptions);
}
```

## Полный исходный код для работы с Load Options в Aspose.Words для Java

```java
public void updateDirtyFields() throws Exception {
	LoadOptions loadOptions = new LoadOptions();
	{
		loadOptions.setUpdateDirtyFields(true);
	}
	Document doc = new Document("Your Directory Path" + "Dirty field.docx", loadOptions);
	doc.save("Your Directory Path" + "WorkingWithLoadOptions.UpdateDirtyFields.docx");
}
@Test
public void loadEncryptedDocument() throws Exception {
	Document doc = new Document("Your Directory Path" + "Encrypted.docx", new LoadOptions("docPassword"));
	doc.save("Your Directory Path" + "WorkingWithLoadOptions.LoadAndSaveEncryptedOdt.odt", new OdtSaveOptions("newPassword"));
}
@Test
public void convertShapeToOfficeMath() throws Exception {
	LoadOptions loadOptions = new LoadOptions();
	{
		loadOptions.setConvertShapeToOfficeMath(true);
	}
	Document doc = new Document("Your Directory Path" + "Office math.docx", loadOptions);
	doc.save("Your Directory Path" + "WorkingWithLoadOptions.ConvertShapeToOfficeMath.docx");
}
@Test
public void setMsWordVersion() throws Exception {
	// Create a new LoadOptions object, which will load documents according to MS Word 2019 specification by default
	// and change the loading version to Microsoft Word 2010.
	LoadOptions loadOptions = new LoadOptions();
	{
		loadOptions.setMswVersion(MsWordVersion.WORD_2010);
	}
	Document doc = new Document("Your Directory Path" + "Document.docx", loadOptions);
	doc.save("Your Directory Path" + "WorkingWithLoadOptions.SetMsWordVersion.docx");
}
@Test
public void useTempFolder() throws Exception {
	LoadOptions loadOptions = new LoadOptions();
	{
		loadOptions.setTempFolder("Your Directory Path");
	}
	Document doc = new Document("Your Directory Path" + "Document.docx", loadOptions);
}
@Test
public void warningCallback() throws Exception {
	LoadOptions loadOptions = new LoadOptions();
	{
		loadOptions.setWarningCallback(new DocumentLoadingWarningCallback());
	}
	Document doc = new Document("Your Directory Path" + "Document.docx", loadOptions);
}
public static class DocumentLoadingWarningCallback implements IWarningCallback {
	public void warning(WarningInfo info) {
		// Prints warnings and their details as they arise during document loading.
		System.out.println(MessageFormat.format("WARNING: {0}, source: {1}", info.getWarningType(), info.getSource()));
		System.out.println(MessageFormat.format("\tDescription: {0}", info.getDescription()));
	}
}
@Test
public void convertMetafilesToPng() throws Exception {
	LoadOptions loadOptions = new LoadOptions();
	{
		loadOptions.setConvertMetafilesToPng(true);
	}
	Document doc = new Document("Your Directory Path" + "WMF with image.docx", loadOptions);
}
@Test
public void loadChm() throws Exception {
	LoadOptions loadOptions = new LoadOptions();
	{
		loadOptions.setEncoding(Charset.forName("windows-1251"));
	}
	Document doc = new Document("Your Directory Path" + "HTML help.chm", loadOptions);
}
```

## Распространённые сценарии использования и советы
- **Конвейеры пакетного конвертирования** — Сочетайте `setTempFolder` с запланированным заданием, чтобы обрабатывать сотни файлов, не заполняя системный временный каталог.  
- **Миграция устаревших документов** — Используйте `setMswVersion` вместе с `setConvertShapeToOfficeMath`, чтобы перенести старые инженерные документы в современный формат, сохранив уравнения.  
- **Безопасная работа с документами** — Сочетайте `loadEncryptedDocument` с `OdtSaveOptions`, чтобы повторно зашифровать файлы новым паролем в другом формате.  

## Часто задаваемые вопросы

**В: Как обрабатывать предупреждения во время загрузки документа?**  
О: Реализуйте пользовательский `IWarningCallback` (как показано в примере *Обратный вызов предупреждений*) и зарегистрируйте его через `loadOptions.setWarningCallback(...)`. Это позволяет вести журнал, игнорировать или прерывать процесс в зависимости от уровня серьезности предупреждения.

**В: Можно ли конвертировать фигуры в объекты Office Math при загрузке документа?**  
О: Да — вызовите `loadOptions.setConvertShapeToOfficeMath(true)` перед созданием `Document`. Библиотека автоматически заменит совместимые фигуры на нативные объекты Office Math.

**В: Как указать версию MS Word при загрузке документа?**  
О: Используйте `loadOptions.setMswVersion(MsWordVersion.WORD_2010)` (или любое другое значение перечисления), чтобы сообщить Aspose.Words, какие правила рендеринга версии Word применять.

**В: Какова цель метода `setTempFolder` в LoadOptions?**  
О: Он направляет все временные файлы, создаваемые во время загрузки (например, извлечённые изображения), в указанную вами папку, что важно для сред с ограниченными системными временными каталогами.

**В: Можно ли конвертировать метафайлы, такие как WMF, в PNG при загрузке?**  
О: Конечно — включите это с помощью `loadOptions.setConvertMetafilesToPng(true)`. Это гарантирует, что растровые изображения сохраняются в формате PNG, улучшая совместимость с современными просмотрщиками.

## Заключение

Мы рассмотрели основные методы **как установить LoadOptions** в Aspose.Words для Java, от обновления грязных полей до работы с зашифрованными файлами, конвертации фигур, указания версии Word, направления временного хранилища и многого другого. Используя эти параметры, вы можете создавать надёжные, высокопроизводительные конвейеры обработки документов, адаптирующиеся к широкому спектру входных сценариев.

---

**Последнее обновление:** 2025-12-27  
**Тестировано с:** Aspose.Words for Java 24.11  
**Автор:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}