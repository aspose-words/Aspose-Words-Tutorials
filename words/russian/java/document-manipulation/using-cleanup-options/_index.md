---
date: 2026-01-11
description: Узнайте, как очищать документ Word с помощью параметров очистки Aspose.Words
  for Java, включая удаление пустых абзацев, пустых строк таблицы и неиспользуемых
  полей.
linktitle: Using Cleanup Options
second_title: Aspose.Words Java Document Processing API
title: Очистка документа Word с помощью параметров очистки Aspose.Words (Java)
url: /ru/java/document-manipulation/using-cleanup-options/
weight: 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Очистка Word-документа с помощью параметров очистки Aspose.Words (Java)

В этом руководстве вы узнаете, как **очистить Word‑документ** с помощью Aspose.Words for Java. Независимо от того, генерируете ли вы счета‑фактуры, контракты или массовые отчёты слияния почты, нежелательные пустые абзацы, неиспользуемые поля или пустые строки таблиц могут сделать окончательный результат непрофессиональным. Мы пройдём каждый параметр очистки шаг за шагом, покажем вам точный код, который нужен, и объясним *почему* каждый параметр важен, чтобы вы могли каждый раз получать отшлифованные документы.

## Быстрые ответы
- **Что означает «очистить Word‑документ»?** Удаление пустых абзацев, неиспользуемых регионов слияния, пустых строк таблиц и других избыточных элементов после операции слияния почты.  
- **Какой параметр очистки удаляет пустые абзацы?** `MailMergeCleanupOptions.REMOVE_EMPTY_PARAGRAPHS`.  
- **Как удалить пустые строки таблицы?** Используйте `MailMergeCleanupOptions.REMOVE_EMPTY_TABLE_ROWS`.  
- **Можно ли избавиться от полей, которые никогда не заполнялись?** Да — `MailMergeCleanupOptions.REMOVE_UNUSED_FIELDS` или `REMOVE_EMPTY_FIELDS`.  
- **Нужна ли лицензия для запуска этих примеров?** Бесплатная пробная версия подходит для оценки; коммерческая лицензия требуется для использования в продакшене.

## Что означает «очистить Word‑документ» в контексте слияния почты?
Когда вы выполняете слияние почты, Aspose.Words вставляет данные в поля и регионы слияния. Если некоторые поля получают `null` или пустые строки, документ может оказаться с лишними абзацами, пустыми таблицами или областями‑заполнителями. **Параметры очистки** автоматически удаляют эти артефакты, оставляя чистый документ, готовый к печати.

## Зачем использовать параметры очистки?
- **Профессиональный вид:** Нет пустых строк или «осиротевших» таблиц.  
- **Меньший размер файла:** Удаление неиспользуемых элементов уменьшает вес документа.  
- **Упрощённая последующая обработка:** Чистые документы легче конвертировать в PDF, HTML или другие форматы.  
- **Экономия времени:** Однострочные настройки заменяют ручные скрипты пост‑обработки.

## Предварительные требования
- Среда разработки Java (JDK 8+).  
- Библиотека Aspose.Words for Java — скачайте её [здесь](https://releases.aspose.com/words/java/).  
- Базовое знакомство с концепциями слияния почты.

## Пошаговое руководство

### Шаг 1: Как удалить пустые абзацы (Java)
Сначала мы покажем, как удалить абзацы, не содержащие видимого текста. Это особенно полезно, когда поле слияния получает значение `null`.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert merge fields
FieldMergeField mergeFieldOption1 = (FieldMergeField) builder.insertField("MERGEFIELD", "Option_1");
mergeFieldOption1.setFieldName("Option_1");
builder.write(" ? ");
FieldMergeField mergeFieldOption2 = (FieldMergeField) builder.insertField("MERGEFIELD", "Option_2");
mergeFieldOption2.setFieldName("Option_2");

// Set cleanup options
doc.getMailMerge().setCleanupOptions(MailMergeCleanupOptions.REMOVE_EMPTY_PARAGRAPHS);

// Enable cleanup of paragraphs that contain only punctuation marks
doc.getMailMerge().setCleanupParagraphsWithPunctuationMarks(true);

// Execute mail merge (both fields are null, so they become empty)
doc.getMailMerge().execute(new String[] { "Option_1", "Option_2" }, new Object[] { null, null });

// Save the cleaned document
doc.save("WorkingWithCleanupOptions.CleanupParagraphsWithPunctuationMarks.docx");
```

**Что происходит здесь?**  
- `REMOVE_EMPTY_PARAGRAPHS` указывает Aspose.Words удалить любой абзац, который после слияния оказывается пустым.  
- Включение `cleanupParagraphsWithPunctuationMarks` также удаляет абзацы, состоящие только из знаков пунктуации (например, “?”).

### Шаг 2: Как удалить неслитые регионы
Если у региона слияния нет соответствующих данных, вы можете полностью удалить его.

```java
Document doc = new Document("Your Directory Path" + "Mail merge destination - Northwind suppliers.docx");
DataSet data = new DataSet();

// Set cleanup options to remove unused regions
doc.getMailMerge().setCleanupOptions(MailMergeCleanupOptions.REMOVE_UNUSED_REGIONS);

// Execute mail merge with regions (the DataSet is empty)
doc.getMailMerge().executeWithRegions(data);

// Save the cleaned document
doc.save("WorkingWithCleanupOptions.RemoveUnmergedRegions.docx");
```

**Почему это важно:**  
- Неиспользуемые регионы часто оставляют пустые разделы или лишние заголовки. Флаг `REMOVE_UNUSED_REGIONS` автоматически их удаляет.

### Шаг 3: Как удалить пустые поля

```java
Document doc = new Document("Your Directory Path" + "Table with fields.docx");

// Set cleanup options to remove empty fields
doc.getMailMerge().setCleanupOptions(MailMergeCleanupOptions.REMOVE_EMPTY_FIELDS);

// Execute mail merge with a mix of populated and empty values
doc.getMailMerge().execute(new String[] { "FullName", "Company", "Address", "Address2", "City" },
    new Object[] { "James Bond", "MI5 Headquarters", "Milbank", "", "London" });

// Save the cleaned document
doc.save("WorkingWithCleanupOptions.RemoveEmptyFields.docx");
```

### Шаг 4: Как удалить неиспользуемые поля

```java
Document doc = new Document("Your Directory Path" + "Table with fields.docx");

// Set cleanup options to remove unused fields
doc.getMailMerge().setCleanupOptions(MailMergeCleanupOptions.REMOVE_UNUSED_FIELDS);

// Execute mail merge
doc.getMailMerge().execute(new String[] { "FullName", "Company", "Address", "Address2", "City" },
    new Object[] { "James Bond", "MI5 Headquarters", "Milbank", "", "London" });

// Save the cleaned document
doc.save("WorkingWithCleanupOptions.RemoveUnusedFields.docx");
```

### Шаг 5: Как удалить содержащие поля

```java
Document doc = new Document("Your Directory Path" + "Table with fields.docx");

// Set cleanup options to remove containing fields
doc.getMailMerge().setCleanupOptions(MailMergeCleanupOptions.REMOVE_CONTAINING_FIELDS);

// Execute mail merge
doc.getMailMerge().execute(new String[] { "FullName", "Company", "Address", "Address2", "City" },
    new Object[] { "James Bond", "MI5 Headquarters", "Milbank", "", "London" });

// Save the cleaned document
doc.save("WorkingWithCleanupOptions.RemoveContainingFields.docx");
```

### Шаг 6: Как удалить пустые строки таблицы

```java
Document doc = new Document("Your Directory Path" + "Table with fields.docx");

// Set cleanup options to remove empty table rows
doc.getMailMerge().setCleanupOptions(MailMergeCleanupOptions.REMOVE_EMPTY_TABLE_ROWS);

// Execute mail merge
doc.getMailMerge().execute(new String[] { "FullName", "Company", "Address", "Address2", "City" },
    new Object[] { "James Bond", "MI5 Headquarters", "Milbank", "", "London" });

// Save the cleaned document
doc.save("WorkingWithCleanupOptions.RemoveEmptyTableRows.docx");
```

## Распространённые проблемы и их устранение
- **Абзацы не удаляются:** Убедитесь, что `setCleanupParagraphsWithPunctuationMarks(true)` вызывается *после* установки параметра очистки.  
- **Пустые строки таблицы остаются:** Проверьте, что ячейки таблицы действительно содержат пустые строки (а не пробелы).  
- **Неиспользуемые поля остаются:** Дважды проверьте, что вы используете правильный enum (`REMOVE_UNUSED_FIELDS`) и что поля слияния не заполняются случайно в другом месте.

## Часто задаваемые вопросы

**Q: В чём разница между `REMOVE_EMPTY_FIELDS` и `REMOVE_UNUSED_FIELDS`?**  
A: `REMOVE_EMPTY_FIELDS` удаляет поля, получившие пустую строку или `null` во время слияния, тогда как `REMOVE_UNUSED_FIELDS` удаляет поля, которые никогда не были упомянуты в операции слияния.

**Q: Можно ли комбинировать несколько параметров очистки?**  
A: Да. Метод `setCleanupOptions` принимает побитовое ИЛИ значений enum, позволяя очистить абзацы, таблицы и регионы одним вызовом.

**Q: Влияет ли включение `cleanupParagraphsWithPunctuationMarks` на обычный текст?**  
A: Оно удаляет только абзацы, состоящие исключительно из знаков пунктуации (например, “?” или “---”). Обычные предложения остаются нетронутыми.

**Q: Можно ли настроить, какие знаки пунктуации учитываются?**  
A: Текущий API использует предопределённый набор знаков пунктуации. Для пользовательского поведения вам придётся выполнить пост‑обработку документа после слияния.

**Q: Работают ли эти параметры очистки при конвертации в PDF?**  
A: Конечно. После очистки Word‑документа вы можете конвертировать его в PDF, HTML или любой другой поддерживаемый формат без переноса нежелательных элементов.

## Заключение
Теперь у вас есть полный набор инструментов для **очистки Word‑документов** во время слияния почты с помощью Aspose.Words for Java. Выбирая соответствующие `MailMergeCleanupOptions`, вы можете автоматически удалять пустые абзацы, пустые строки таблиц, неиспользуемые поля и многое другое — получая каждый раз аккуратный документ, готовый к продакшену.

---

**Последнее обновление:** 2026-01-11  
**Тестировано с:** Aspose.Words for Java 24.11  
**Автор:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}