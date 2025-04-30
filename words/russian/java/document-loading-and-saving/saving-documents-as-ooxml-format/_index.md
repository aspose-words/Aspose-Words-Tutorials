---
"description": "Узнайте, как сохранять документы в формате OOXML с помощью Aspose.Words для Java. Защищайте, оптимизируйте и настраивайте свои файлы без усилий."
"linktitle": "Сохранение документов в формате OOXML"
"second_title": "API обработки документов Java Aspose.Words"
"title": "Сохранение документов в формате OOXML в Aspose.Words для Java"
"url": "/ru/java/document-loading-and-saving/saving-documents-as-ooxml-format/"
"weight": 20
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Сохранение документов в формате OOXML в Aspose.Words для Java


## Введение в сохранение документов в формате OOXML в Aspose.Words для Java

В этом руководстве мы рассмотрим, как сохранять документы в формате OOXML с помощью Aspose.Words for Java. OOXML (Office Open XML) — это формат файла, используемый Microsoft Word и другими офисными приложениями. Мы рассмотрим различные параметры и настройки для сохранения документов в формате OOXML.

## Предпосылки

Прежде чем начать, убедитесь, что в вашем проекте настроена библиотека Aspose.Words for Java.

## Сохранение документа с шифрованием паролем

Вы можете зашифровать свой документ паролем, сохраняя его в формате OOXML. Вот как это можно сделать:

```java
import com.aspose.words.Document;
import com.aspose.words.OoxmlSaveOptions;

// Загрузить документ
Document doc = new Document("Document.docx");

// Создайте OoxmlSaveOptions и установите пароль
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions();
saveOptions.setPassword("password");

// Сохраните документ с шифрованием
doc.save("EncryptedDoc.docx", saveOptions);
```

## Настройка соответствия OOXML

Вы можете указать уровень соответствия OOXML при сохранении документа. Например, вы можете установить его на ISO 29500:2008 (Strict). Вот как это сделать:

```java
import com.aspose.words.Document;
import com.aspose.words.OoxmlSaveOptions;
import com.aspose.words.MsWordVersion;
import com.aspose.words.OoxmlCompliance;

// Загрузить документ
Document doc = new Document("Document.docx");

// Оптимизировать для Word 2016
doc.getCompatibilityOptions().optimizeFor(MsWordVersion.WORD_2016);

// Создайте OoxmlSaveOptions и установите уровень соответствия
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions();
saveOptions.setCompliance(OoxmlCompliance.ISO_29500_2008_STRICT);

// Сохраните документ с настройкой соответствия
doc.save("ComplianceDoc.docx", saveOptions);
```

## Обновление свойства последнего сохраненного времени

Вы можете выбрать обновление свойства "Время последнего сохранения" документа при его сохранении. Вот как это сделать:

```java
import com.aspose.words.Document;
import com.aspose.words.OoxmlSaveOptions;

// Загрузить документ
Document doc = new Document("Document.docx");

// Создайте OoxmlSaveOptions и включите обновление свойства «Время последнего сохранения».
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions();
saveOptions.setUpdateLastSavedTimeProperty(true);

// Сохраните документ с обновленным свойством.
doc.save("UpdatedLastSavedTime.docx", saveOptions);
```

## Сохранение старых управляющих персонажей

Если ваш документ содержит устаревшие управляющие символы, вы можете сохранить их при сохранении. Вот как:

```java
import com.aspose.words.Document;
import com.aspose.words.OoxmlSaveOptions;
import com.aspose.words.SaveFormat;

// Загрузите документ с устаревшими управляющими символами
Document doc = new Document("LegacyControlChars.doc");

// Создайте OoxmlSaveOptions с форматом FLAT_OPC и включите сохранение устаревших управляющих символов.
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions();
saveOptions.setKeepLegacyControlChars(true);

// Сохраните документ с использованием устаревших управляющих символов.
doc.save("LegacyControlCharsPreserved.docx", saveOptions);
```

## Установка уровня сжатия

Вы можете настроить уровень сжатия при сохранении документа. Например, вы можете установить его на SUPER_FAST для минимального сжатия. Вот как:

```java
import com.aspose.words.Document;
import com.aspose.words.OoxmlSaveOptions;
import com.aspose.words.CompressionLevel;

// Загрузить документ
Document doc = new Document("Document.docx");

// Создайте OoxmlSaveOptions и установите уровень сжатия
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions();
saveOptions.setCompressionLevel(CompressionLevel.SUPER_FAST);

// Сохраните документ с указанным уровнем сжатия.
doc.save("FastCompressionDoc.docx", saveOptions);
```

Вот некоторые из основных параметров и настроек, которые вы можете использовать при сохранении документов в формате OOXML с помощью Aspose.Words for Java. Не стесняйтесь изучать дополнительные параметры и настраивать процесс сохранения документов по мере необходимости.

## Полный исходный код для сохранения документов в формате OOXML в Aspose.Words для Java

```java
public void encryptDocxWithPassword() throws Exception
{
	Document doc = new Document("Your Directory Path" + "Document.docx");
	OoxmlSaveOptions saveOptions = new OoxmlSaveOptions(); { saveOptions.setPassword("password"); }
	doc.save("Your Directory Path" + "WorkingWithOoxmlSaveOptions.EncryptDocxWithPassword.docx", saveOptions);
}
@Test
public void ooxmlComplianceIso29500_2008_Strict() throws Exception
{
	Document doc = new Document("Your Directory Path" + "Document.docx");
	doc.getCompatibilityOptions().optimizeFor(MsWordVersion.WORD_2016);
	OoxmlSaveOptions saveOptions = new OoxmlSaveOptions(); { saveOptions.setCompliance(OoxmlCompliance.ISO_29500_2008_STRICT); }
	doc.save("Your Directory Path" + "WorkingWithOoxmlSaveOptions.OoxmlComplianceIso29500_2008_Strict.docx", saveOptions);
}
@Test
public void updateLastSavedTimeProperty() throws Exception
{
	Document doc = new Document("Your Directory Path" + "Document.docx");
	OoxmlSaveOptions saveOptions = new OoxmlSaveOptions(); { saveOptions.setUpdateLastSavedTimeProperty(true); }
	doc.save("Your Directory Path" + "WorkingWithOoxmlSaveOptions.UpdateLastSavedTimeProperty.docx", saveOptions);
}
@Test
public void keepLegacyControlChars() throws Exception
{
	Document doc = new Document("Your Directory Path" + "Legacy control character.doc");
	OoxmlSaveOptions saveOptions = new OoxmlSaveOptions(); { saveOptions.setKeepLegacyControlChars(true); }
	doc.save("Your Directory Path" + "WorkingWithOoxmlSaveOptions.KeepLegacyControlChars.docx", saveOptions);
}
@Test
public void setCompressionLevel() throws Exception
{
	Document doc = new Document("Your Directory Path" + "Document.docx");
	OoxmlSaveOptions saveOptions = new OoxmlSaveOptions(); { saveOptions.setCompressionLevel(CompressionLevel.SUPER_FAST); }
	doc.save("Your Directory Path" + "WorkingWithOoxmlSaveOptions.SetCompressionLevel.docx", saveOptions);
}
```

## Заключение

В этом подробном руководстве мы рассмотрели, как сохранять документы в формате OOXML с помощью Aspose.Words для Java. Если вам нужно зашифровать документы с помощью паролей, обеспечить соответствие определенным стандартам OOXML, обновить свойства документа, сохранить устаревшие управляющие символы или настроить уровни сжатия, Aspose.Words предоставляет универсальный набор инструментов для удовлетворения ваших требований.

## Часто задаваемые вопросы

### Как снять защиту паролем с защищенного паролем документа?

Чтобы снять защиту паролем с документа, защищенного паролем, вы можете открыть документ с правильным паролем, а затем сохранить его, не указывая пароль в параметрах сохранения. Это сохранит документ без защиты паролем.

### Можно ли задать пользовательские свойства при сохранении документа в формате OOXML?

Да, вы можете задать пользовательские свойства для документа перед сохранением его в формате OOXML. Используйте `BuiltInDocumentProperties` и `CustomDocumentProperties` классы для установки различных свойств, таких как автор, заголовок, ключевые слова и пользовательские свойства.

### Какой уровень сжатия используется по умолчанию при сохранении документа в формате OOXML?

Уровень сжатия по умолчанию при сохранении документа в формате OOXML с помощью Aspose.Words для Java составляет `NORMAL`. Вы можете изменить уровень сжатия на `SUPER_FAST` или `MAXIMUM` по мере необходимости.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}