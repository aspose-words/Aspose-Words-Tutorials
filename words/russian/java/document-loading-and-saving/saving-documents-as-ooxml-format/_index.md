---
date: 2026-01-09
description: Узнайте, как зашифровать DOCX с паролем и изменить уровень сжатия при
  сохранении документов в формате OOXML с помощью Aspose.Words for Java.
linktitle: Saving Documents as OOXML Format
second_title: Aspose.Words Java Document Processing API
title: Шифрование docx с паролем – сохранение OOXML с помощью Aspose.Words Java
url: /ru/java/document-loading-and-saving/saving-documents-as-ooxml-format/
weight: 20
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Шифрование docx с паролем – сохранение OOXML с Aspose.Words Java

## Введение в сохранение документов в формате OOXML в Aspose.Words for Java

В этом руководстве вы узнаете, как **зашифровать docx с паролем** и сохранять документы в формате OOXML с помощью Aspose.Words for Java. OOXML (Office Open XML) — современный файловый формат, используемый Microsoft Word и многими другими офисными приложениями. Мы рассмотрим самые распространённые параметры — защиту паролем, уровни соответствия, обновление свойств, обработку устаревших управляющих символов и **изменение уровня сжатия** — чтобы вы могли настроить вывод точно под свои нужды.

## Быстрые ответы
- **Как защитить файл Word?** Используйте `OoxmlSaveOptions.setPassword("yourPassword")` перед сохранением.  
- **Какой уровень соответствия OOXML выбрать?** ISO 29500 2008 Strict для максимальной совместимости с современными версиями Office.  
- **Можно ли сохранить устаревшие управляющие символы?** Да, включите `setKeepLegacyControlChars(true)`.  
- **Как изменить уровень сжатия?** Установите `setCompressionLevel(CompressionLevel.SUPER_FAST)` или `MAXIMUM` в зависимости от необходимости.  
- **Влияют ли эти параметры на размер файла?** Уровень сжатия и обработка устаревших символов могут заметно изменить окончательный размер .docx.

## Что такое «encrypt docx with password»?
Шифрование файла DOCX означает, что документ сохраняется с шифрованием AES‑256, требующим пароля для открытия в Word или любом совместимом просмотрщике. Это необходимо для защиты конфиденциальной информации при передаче файлов по электронной почте, облачному хранилищу или внутренним порталам.

## Почему стоит использовать параметры сохранения OOXML?
- **Безопасность:** Защита паролем предотвращает несанкционированный доступ.  
- **Совместимость:** Параметры соответствия гарантируют работу файла в разных версиях Word.  
- **Производительность:** Настройка сжатия может ускорить процесс сохранения или уменьшить размер файла.  
- **Сохранность:** Сохранение устаревших управляющих символов поддерживает точность при конвертации старых документов.

## Предварительные требования
- Библиотека Aspose.Words for Java, добавленная в ваш проект (Maven/Gradle или вручную JAR).  
- Java 8 или выше.  
- Исходный документ (`.docx` или `.doc`), который вы хотите обработать.

## Сохранение документа с шифрованием паролем

Вы можете зашифровать документ паролем при сохранении его в формате OOXML. Как это сделать:

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

> **Pro tip:** Выберите надёжный пароль и храните его в безопасном месте; пароль нельзя восстановить из зашифрованного файла.

## Установка соответствия OOXML

Можно задать уровень соответствия OOXML при сохранении документа. Например, установить ISO 29500:2008 (Strict). Как это сделать:

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

## Обновление свойства «Время последнего сохранения»

Можно указать, чтобы свойство «Last Saved Time» обновлялось при сохранении документа. Как это сделать:

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

Если ваш документ содержит устаревшие управляющие символы, их можно сохранить при сохранении. Как это сделать:

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

## Как изменить уровень сжатия при сохранении OOXML

Можно настроить уровень сжатия при сохранении документа. Например, установить `SUPER_FAST` для минимального сжатия или `MAXIMUM` для наименьшего размера файла. Как это сделать:

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

Это некоторые из ключевых параметров и настроек, которые вы можете использовать при сохранении документов в формате OOXML с помощью Aspose.Words for Java. Не стесняйтесь исследовать дополнительные возможности и настраивать процесс сохранения документов под свои требования.

## Полный исходный код для сохранения документов в формате OOXML в Aspose.Words for Java

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

В этом полном руководстве мы рассмотрели, как **зашифровать docx с паролем** и сохранять документы в формате OOXML с помощью Aspose.Words for Java. Независимо от того, нужно ли вам защитить файлы, обеспечить строгую совместимость OOXML, обновить свойства документа, сохранить устаревшие управляющие символы или **изменить уровень сжатия**, Aspose.Words предоставляет универсальный набор инструментов для выполнения ваших задач.

## Часто задаваемые вопросы

**В: Как удалить защиту паролем из защищённого документа?**  
О: Откройте документ, указав правильный пароль, затем сохраните его без указания пароля в `OoxmlSaveOptions`. Это создаст незащищённую копию.

**В: Можно ли задать пользовательские свойства при сохранении документа в формате OOXML?**  
О: Да. Используйте `BuiltInDocumentProperties` и `CustomDocumentProperties` объекта `Document` перед вызовом `save()`.

**В: Какой уровень сжатия используется по умолчанию при сохранении документа в формате OOXML?**  
О: По умолчанию — `CompressionLevel.NORMAL`. Вы можете переключиться на `SUPER_FAST` для скорости или `MAXIMUM` для минимального размера файла.

**В: Повлияет ли включение `keepLegacyControlChars` на совместимость с современными версиями Word?**  
О: Современный Word может открывать файлы с устаревшими управляющими символами, но некоторые старые функции могут отображаться иначе. Используйте эту опцию только тогда, когда необходимо сохранить точное оригинальное содержимое.

**В: Можно ли комбинировать несколько параметров сохранения (например, пароль + сжатие) в одном вызове?**  
О: Абсолютно. Настройте все нужные свойства в одном экземпляре `OoxmlSaveOptions` перед передачей его в `doc.save()`.

---

**Последнее обновление:** 2026-01-09  
**Тестировано с:** Aspose.Words for Java 24.12  
**Автор:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}