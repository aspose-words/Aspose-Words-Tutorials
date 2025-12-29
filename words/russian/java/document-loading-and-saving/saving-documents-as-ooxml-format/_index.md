---
date: 2025-12-29
description: Узнайте, как зашифровать DOCX паролем с помощью параметров сохранения
  Aspose.Words для Java. Обеспечьте безопасность, оптимизируйте и настраивайте свои
  файлы OOXML без усилий.
linktitle: Saving Documents as OOXML Format
second_title: Aspose.Words Java Document Processing API
title: Как зашифровать DOCX с паролем с помощью Aspose.Words для Java
url: /ru/java/document-loading-and-saving/saving-documents-as-ooxml-format/
weight: 20
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Как зашифровать DOCX с паролем с помощью Aspose.Words for Java

В этом руководстве вы узнаете **как зашифровать docx с паролем** при сохранении документов в формате OOXML с помощью Aspose.Words for Java. Защищая конфиденциальные отчёты или обеспечивая безопасность черновиков контрактов, ниже приведённые шаги покажут, как точно применить защиту паролем и тонко настроить другие параметры сохранения OOXML.

## Быстрые ответы
- **Can I encrypt a DOCX file with a password?** Да, используйте `OoxmlSaveOptions.setPassword()` перед сохранением.  
- **Which class controls OOXML save settings?** `OoxmlSaveOptions` (часть Aspose.Words).  
- **Do I need a license for password protection?** Для использования в продакшене требуется действующая лицензия Aspose.Words.  
- **Can I combine encryption with compliance settings?** Конечно – задайте одновременно `setPassword` и `setCompliance` в одном экземпляре `OoxmlSaveOptions`.  
- **What compression levels are available?** `NORMAL`, `SUPER_FAST` и `MAXIMUM` через `CompressionLevel`.

## Что означает “encrypt docx with password”?
Шифрование файла DOCX означает, что содержимое файла хранится в зашифрованном виде и может быть открыто только после ввода правильного пароля. Это защищает конфиденциальную информацию от неавторизованного доступа, при этом стандартные инструменты Word могут открыть файл, как только пароль будет предоставлен.

## Почему использовать параметры сохранения Aspose.Words для шифрования?
Aspose.Words предоставляет обширный набор **aspose words save options**, позволяющий управлять не только шифрованием, но и уровнями соответствия, сжатием и обработкой устаревших управляющих символов — всё из Java‑кода. Это устраняет необходимость в ручной пост‑обработке или сторонних инструментах.

## Требования
- Java Development Kit (JDK 8 или выше)  
- Библиотека Aspose.Words for Java, добавленная в ваш проект (Maven/Gradle или JAR)  
- Действительная лицензия Aspose.Words для продакшена (необязательно для оценки)

## Сохранение документа с шифрованием паролем

Вы можете зашифровать документ паролем при сохранении его в формате OOXML. Вот как это сделать:

```java
import com.aspose.words.Document;
import com.aspose.words.OoxmlSaveOptions;

// Load the document
Document doc = new Document("Document.docx");

// Create OoxmlSaveOptions and set the password
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions();
saveOptions.setPassword("password");

// Save the document with encryption
doc.save("EncryptedDoc.docx", saveOptions);
```

## Установка соответствия OOXML

Можно указать уровень соответствия OOXML при сохранении документа. Например, можно установить ISO 29500:2008 (Strict). Вот как:

```java
import com.aspose.words.Document;
import com.aspose.words.OoxmlSaveOptions;
import com.aspose.words.MsWordVersion;
import com.aspose.words.OoxmlCompliance;

// Load the document
Document doc = new Document("Document.docx");

// Optimize for Word 2016
doc.getCompatibilityOptions().optimizeFor(MsWordVersion.WORD_2016);

// Create OoxmlSaveOptions and set the compliance level
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions();
saveOptions.setCompliance(OoxmlCompliance.ISO_29500_2008_STRICT);

// Save the document with compliance setting
doc.save("ComplianceDoc.docx", saveOptions);
```

## Обновление свойства «Last Saved Time»

Можно выбрать обновление свойства «Last Saved Time» документа при сохранении. Вот как:

```java
import com.aspose.words.Document;
import com.aspose.words.OoxmlSaveOptions;

// Load the document
Document doc = new Document("Document.docx");

// Create OoxmlSaveOptions and enable updating the Last Saved Time property
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions();
saveOptions.setUpdateLastSavedTimeProperty(true);

// Save the document with the updated property
doc.save("UpdatedLastSavedTime.docx", saveOptions);
```

## Сохранение устаревших управляющих символов

Если ваш документ содержит устаревшие управляющие символы, вы можете сохранить их при сохранении. Вот как:

```java
import com.aspose.words.Document;
import com.aspose.words.OoxmlSaveOptions;
import com.aspose.words.SaveFormat;

// Load a document with legacy control characters
Document doc = new Document("LegacyControlChars.doc");

// Create OoxmlSaveOptions with the FLAT_OPC format and enable keeping legacy control characters
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions();
saveOptions.setKeepLegacyControlChars(true);

// Save the document with legacy control characters
doc.save("LegacyControlCharsPreserved.docx", saveOptions);
```

## Установка уровня сжатия

Можно регулировать уровень сжатия при сохранении документа. Например, можно установить **SUPER_FAST** для минимального сжатия. Вот как:

```java
import com.aspose.words.Document;
import com.aspose.words.OoxmlSaveOptions;
import com.aspose.words.CompressionLevel;

// Load the document
Document doc = new Document("Document.docx");

// Create OoxmlSaveOptions and set the compression level
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions();
saveOptions.setCompressionLevel(CompressionLevel.SUPER_FAST);

// Save the document with the specified compression level
doc.save("FastCompressionDoc.docx", saveOptions);
```

Это некоторые из ключевых параметров и настроек, которые вы можете использовать при сохранении документов в формате OOXML с помощью Aspose.Words for Java. Не стесняйтесь исследовать дополнительные возможности и настраивать процесс сохранения документов по мере необходимости.

## Полный исходный код для сохранения документов в формате OOXML с помощью Aspose.Words for Java

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

В этом полном руководстве мы рассмотрели, как **encrypt docx with password** и тонко настроить набор параметров сохранения OOXML с помощью Aspose.Words for Java. Независимо от того, нужно ли вам защитить конфиденциальное содержание, соответствовать строгим требованиям ISO, сохранить устаревшие символы или управлять сжатием, библиотека предоставляет детальный контроль через один и тот же API `OoxmlSaveOptions`.

## Часто задаваемые вопросы

**Q: Как удалить защиту паролем из документа, защищённого паролем?**  
A: Откройте документ, указав правильный пароль, затем сохраните его снова без вызова `setPassword`. Новый файл будет незащищённым.

**Q: Можно ли задать пользовательские свойства при сохранении документа в формате OOXML?**  
A: Да. Используйте `BuiltInDocumentProperties` или `CustomDocumentProperties` у объекта `Document` перед вызовом `save`.

**Q: Какой уровень сжатия используется по умолчанию при сохранении документа в формате OOXML?**  
A: По умолчанию — `NORMAL`. Вы можете переключиться на `SUPER_FAST` для скорости или `MAXIMUM` для меньшего размера файла.

**Q: Работают ли параметры сохранения aspose words с более старыми версиями Word?**  
A: Да. Настраивая `MsWordVersion` и параметры соответствия, можно целиться в Word 2007‑2019 и обеспечить совместимость.

**Q: Можно ли объединить несколько параметров сохранения в одной операции?**  
A: Абсолютно. Создайте один экземпляр `OoxmlSaveOptions`, задайте все нужные свойства (пароль, соответствие, сжатие и т.д.) и передайте его в `doc.save()`.

---

**Последнее обновление:** 2025-12-29  
**Тестировано с:** Aspose.Words for Java 24.12  
**Автор:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}