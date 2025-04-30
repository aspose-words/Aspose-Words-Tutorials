---
"description": "Освоение параметров загрузки в Aspose.Words для Java. Настройте загрузку документов, управляйте шифрованием, преобразуйте фигуры, устанавливайте версии Word и многое другое для эффективной обработки документов Java."
"linktitle": "Использование параметров загрузки"
"second_title": "API обработки документов Java Aspose.Words"
"title": "Использование параметров загрузки в Aspose.Words для Java"
"url": "/ru/java/document-loading-and-saving/using-load-options/"
"weight": 11
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Использование параметров загрузки в Aspose.Words для Java


## Введение в работу с параметрами загрузки в Aspose.Words для Java

В этом уроке мы рассмотрим, как работать с параметрами загрузки в Aspose.Words для Java. Параметры загрузки позволяют настраивать загрузку и обработку документов. Мы рассмотрим различные сценарии, включая обновление грязных полей, загрузку зашифрованных документов, преобразование фигур в Office Math, установку версии MS Word, указание временной папки, обработку предупреждений и преобразование метафайлов в PNG. Давайте разберемся шаг за шагом.

## Обновить грязные поля

```java
LoadOptions loadOptions = new LoadOptions();
loadOptions.setUpdateDirtyFields(true);

Document doc = new Document("Your Directory Path" + "Dirty field.docx", loadOptions);
doc.save("Your Directory Path" + "WorkingWithLoadOptions.UpdateDirtyFields.docx");
```

Этот фрагмент кода демонстрирует, как обновить грязные поля в документе. `setUpdateDirtyFields(true)` метод используется для обеспечения обновления грязных полей во время загрузки документа.

## Загрузить зашифрованный документ

```java
@Test
public void loadEncryptedDocument() throws Exception {
    Document doc = new Document("Your Directory Path" + "Encrypted.docx", new LoadOptions("docPassword"));
    doc.save("Your Directory Path" + "WorkingWithLoadOptions.LoadAndSaveEncryptedOdt.odt", new OdtSaveOptions("newPassword"));
}
```

Здесь мы загружаем зашифрованный документ с использованием пароля. `LoadOptions` конструктор принимает пароль документа, и вы также можете указать новый пароль при сохранении документа, используя `OdtSaveOptions`.

## Преобразовать форму в офисную математику

```java
LoadOptions loadOptions = new LoadOptions();
loadOptions.setConvertShapeToOfficeMath(true);

Document doc = new Document("Your Directory Path" + "Office math.docx", loadOptions);
doc.save("Your Directory Path" + "WorkingWithLoadOptions.ConvertShapeToOfficeMath.docx");
```

Этот код демонстрирует, как преобразовывать фигуры в объекты Office Math во время загрузки документа. `setConvertShapeToOfficeMath(true)` метод позволяет осуществить это преобразование.

## Установить версию MS Word

```java
@Test
public void setMsWordVersion() throws Exception {
    LoadOptions loadOptions = new LoadOptions();
    loadOptions.setMswVersion(MsWordVersion.WORD_2010);

    Document doc = new Document("Your Directory Path" + "Document.docx", loadOptions);
    doc.save("Your Directory Path" + "WorkingWithLoadOptions.SetMsWordVersion.docx");
}
```

Вы можете указать версию MS Word для загрузки документа. В этом примере мы устанавливаем версию Microsoft Word 2010 с помощью `setMswVersion`.

## Использовать временную папку

```java
@Test
public void useTempFolder() throws Exception {
    LoadOptions loadOptions = new LoadOptions();
    loadOptions.setTempFolder("Your Directory Path");

    Document doc = new Document("Your Directory Path" + "Document.docx", loadOptions);
}
```

Установив временную папку с помощью `setTempFolder`, вы можете контролировать, где будут храниться временные файлы во время обработки документа.

## Предупреждение Обратный звонок

```java
@Test
public void warningCallback() throws Exception {
    LoadOptions loadOptions = new LoadOptions();
    loadOptions.setWarningCallback(new DocumentLoadingWarningCallback());

    Document doc = new Document("Your Directory Path" + "Document.docx", loadOptions);
}

public static class DocumentLoadingWarningCallback implements IWarningCallback {
    public void warning(WarningInfo info) {
        // Обрабатывайте предупреждения по мере их возникновения во время загрузки документа.
        System.out.println(MessageFormat.format("WARNING: {0}, source: {1}", info.getWarningType(), info.getSource()));
        System.out.println(MessageFormat.format("\tDescription: {0}", info.getDescription()));
    }
}
```

Этот код демонстрирует, как настроить обратный вызов предупреждения для обработки предупреждений во время загрузки документа. Вы можете настроить поведение вашего приложения при возникновении предупреждений.

## Конвертировать метафайлы в PNG

```java
@Test
public void convertMetafilesToPng() throws Exception {
    LoadOptions loadOptions = new LoadOptions();
    loadOptions.setConvertMetafilesToPng(true);

    Document doc = new Document("Your Directory Path" + "WMF with image.docx", loadOptions);
}
```

Чтобы преобразовать метафайлы (например, WMF) в изображения PNG во время загрузки документа, можно использовать `setConvertMetafilesToPng(true)` метод.

## Полный исходный код для работы с параметрами загрузки в Aspose.Words для Java

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
	// Создайте новый объект LoadOptions, который по умолчанию будет загружать документы в соответствии со спецификацией MS Word 2019.
	// и измените версию загрузки на Microsoft Word 2010.
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
		// Печатает предупреждения и их подробности по мере их появления во время загрузки документа.
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

## Заключение

В этом руководстве мы углубились в различные аспекты работы с параметрами загрузки в Aspose.Words для Java. Параметры загрузки играют важную роль в настройке загрузки и обработки документов, позволяя вам адаптировать обработку документов к вашим конкретным потребностям. Давайте повторим основные моменты, рассмотренные в этом руководстве:

## Часто задаваемые вопросы

### Как обрабатывать предупреждения во время загрузки документа?

Вы можете настроить обратный вызов предупреждения, как показано на рисунке. `warningCallback()` Метод выше. Настройте `DocumentLoadingWarningCallback` класс для обработки предупреждений в соответствии с требованиями вашего приложения.

### Можно ли преобразовывать фигуры в объекты Office Math при загрузке документа?

Да, вы можете преобразовывать фигуры в объекты Office Math с помощью `loadOptions.setConvertShapeToOfficeMath(true)`.

### Как указать версию MS Word для загрузки документа?

Использовать `loadOptions.setMswVersion(MsWordVersion.WORD_2010)` указать версию MS Word для загрузки документа.

### Какова цель `setTempFolder` метод в параметрах загрузки?

The `setTempFolder` Метод позволяет указать папку, в которой будут храниться временные файлы во время обработки документа.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}