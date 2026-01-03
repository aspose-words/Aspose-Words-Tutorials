---
date: 2026-01-03
description: Узнайте, как заменять текст на HTML в документах Word с помощью Aspose.Words
  для Java. Пошаговое руководство с примерами кода, советами по замене текста с помощью
  regex в Java и многим другим.
linktitle: Finding and Replacing Text
second_title: Aspose.Words Java Document Processing API
title: заменить текст на HTML с помощью Aspose.Words для Java
url: /ru/java/document-manipulation/finding-and-replacing-text/
weight: 15
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# заменить текст на html в Aspose.Words for Java

## Введение в поиск и замену текста в Aspose.Words for Java

Aspose.Words for Java — это мощный Java API, позволяющий программно работать с документами Word. Одна из самых распространённых задач — **заменить текст на html**, будь то обновление заполнителей в шаблоне, вставка стилизованного контента или массовые преобразования текста. В этом руководстве мы рассмотрим, как заменять текст, как использовать regex replace text java, а также как заменять текст в заголовках — всё это при чистом и эффективном коде.

## Быстрые ответы
- **Каков основной метод для замены текста на html?** Используйте `FindReplaceOptions` с пользовательским обратным вызовом, например `ReplaceWithHtmlEvaluator`.  
- **Можно ли игнорировать поля при замене?** Да — установите `options.setIgnoreFields(true)`.  
- **Нужна ли лицензия для продакшн‑использования?** Для коммерческих развертываний требуется действующая лицензия Aspose.Words.  
- **Какая версия Java поддерживается?** Aspose.Words for Java работает с Java 8 и выше.  
- **Поддерживается ли regex replace text java?** Абсолютно — передайте объект `Pattern` в метод `replace`.

## Что такое «заменить текст на html»?

Замена текста на HTML означает замену простого текстового заполнителя на богатую разметку HTML (таблицы, списки, стили) при сохранении структуры окружающего документа Word. Aspose.Words разбирает HTML и вставляет соответствующие объекты Word, предоставляя полный контроль над окончательным макетом.

## Почему стоит использовать Aspose.Words для этой задачи?

- **Полная точность Word** — библиотека сохраняет всё форматирование, заголовки, колонтитулы и отслеживаемые изменения.  
- **Встроенная поддержка regex** — идеально подходит для сложных поисковых шаблонов (`regex replace text java`).  
- **Тонкий контроль** — такие параметры, как `IgnoreFields`, `IgnoreDeleted` и `UseLegacyOrder`, позволяют точно настроить операцию под ваши требования.  
- **Кросс‑платформенный** — работает на любой ОС, где запускается Java.

## Предварительные требования

- Среда разработки Java (JDK 8+)  
- Библиотека Aspose.Words for Java — скачайте её по ссылке [here](https://releases.aspose.com/words/java/).  
- Пример документа Word (`.docx`) для экспериментов.

## Поиск и замена простого текста

```java
// Load the document
Document doc = new Document("your-document.docx");

// Create a DocumentBuilder
DocumentBuilder builder = new DocumentBuilder(doc);

// Find and replace text
builder.getRange().replace("old-text", "new-text", new FindReplaceOptions());

// Save the modified document
doc.save("modified-document.docx");
```

Этот простой пример демонстрирует **как заменить текст** с помощью метода `replace`. Это основа для более сложных сценариев.

## Использование регулярных выражений (regex replace text java)

```java
// Load the document
Document doc = new Document("your-document.docx");

// Create a DocumentBuilder
DocumentBuilder builder = new DocumentBuilder(doc);

// Use regular expressions for finding and replacing text
Pattern regex = Pattern.compile("your-pattern");
builder.getRange().replace(regex, "replacement-text", new FindReplaceOptions());

// Save the modified document
doc.save("modified-document.docx");
```

Регулярные выражения предоставляют мощное сопоставление шаблонов, идеально подходящее для динамических заполнителей или сложных границ слов.

## Игнорирование текста внутри полей (aspose words replace text)

```java
// Load the document
Document doc = new Document("your-document.docx");

// Create a FindReplaceOptions instance and set IgnoreFields to true
FindReplaceOptions options = new FindReplaceOptions();
options.setIgnoreFields(true);

// Use options when replacing text
doc.getRange().replace("text-to-replace", "new-text", options);

// Save the modified document
doc.save("modified-document.docx");
```

Установите `IgnoreFields`, чтобы оставить поля слияния, номера страниц или другие коды полей нетронутыми, пока вы заменяете окружающий контент.

## Игнорирование текста внутри удалённых правок

```java
// Load the document
Document doc = new Document("your-document.docx");

// Create a FindReplaceOptions instance and set IgnoreDeleted to true
FindReplaceOptions options = new FindReplaceOptions();
options.setIgnoreDeleted(true);

// Use options when replacing text
doc.getRange().replace("text-to-replace", "new-text", options);

// Save the modified document
doc.save("modified-document.docx");
```

Это предотвращает изменение текста, помеченного как удалённый (отслеживаемые изменения).

## Игнорирование текста внутри вставленных правок

```java
// Load the document
Document doc = new Document("your-document.docx");

// Create a FindReplaceOptions instance and set IgnoreInserted to true
FindReplaceOptions options = new FindReplaceOptions();
options.setIgnoreInserted(true);

// Use options when replacing text
doc.getRange().replace("text-to-replace", "new-text", options);

// Save the modified document
doc.save("modified-document.docx");
```

Полезно, когда нужно сохранить вновь вставленный текст неизменным во время массовой замены.

## Замена текста на HTML

```java
// Load the document
Document doc = new Document("your-document.docx");

// Create a FindReplaceOptions instance with a custom replacing callback
FindReplaceOptions options = new FindReplaceOptions();
options.setReplacingCallback(new ReplaceWithHtmlEvaluator(options));

// Use options when replacing text
doc.getRange().replace("text-to-replace", "new-html-content", options);

// Save the modified document
doc.save("modified-document.docx");
```

Здесь мы **заменяем текст на html**, предоставляя пользовательский оценщик, который разбирает строку HTML и вставляет соответствующие узлы Word.

## Замена текста в заголовках и колонтитулах (replace text in headers)

```java
// Load the document
Document doc = new Document("your-document.docx");

// Get the collection of headers and footers
HeaderFooterCollection headersFooters = doc.getFirstSection().getHeadersFooters();

// Choose the header or footer type you want to replace text in (e.g., HeaderFooterType.FOOTER_PRIMARY)
HeaderFooter footer = headersFooters.getByHeaderFooterType(HeaderFooterType.FOOTER_PRIMARY);

// Create a FindReplaceOptions instance and apply it to the footer's range
FindReplaceOptions options = new FindReplaceOptions();
footer.getRange().replace("text-to-replace", "new-text", options);

// Save the modified document
doc.save("modified-document.docx");
```

Точная замена в заголовках или колонтитулах обеспечивает согласованность брендинга документа.

## Показ изменений порядка заголовков и колонтитулов

```java
// Load the document
Document doc = new Document("your-document.docx");

// Get the first section
Section firstPageSection = doc.getFirstSection();

// Create a FindReplaceOptions instance and apply it to the document's range
FindReplaceOptions options = new FindReplaceOptions();
options.setReplacingCallback(new ReplaceLog());

// Replace text that affects header and footer orders
doc.getRange().replace(Pattern.compile("(header|footer)"), "", options);

// Save the modified document
doc.save("modified-document.docx");
```

Этот пример регистрирует изменения, помогая вам проводить аудит модификаций порядка заголовков/колонтитулов.

## Замена текста полями

```java
// Load the document
Document doc = new Document("your-document.docx");

// Create a FindReplaceOptions instance and set a custom replacing callback for fields
FindReplaceOptions options = new FindReplaceOptions();
options.setReplacingCallback(new ReplaceTextWithFieldHandler(FieldType.FIELD_MERGE_FIELD));

// Use options when replacing text
doc.getRange().replace(Pattern.compile("PlaceHolder(\\d+)"), "", options);

// Save the modified document
doc.save("modified-document.docx");
```

Вставка полей (например, полей слияния) позволяет создавать динамические документы, которые можно заполнить позже.

## Замена с помощью оценщика

```java
// Load the document
Document doc = new Document("your-document.docx");

// Create a FindReplaceOptions instance and set a custom replacing callback
FindReplaceOptions options = new FindReplaceOptions();
options.setReplacingCallback(new MyReplaceEvaluator());

// Use options when replacing text
doc.getRange().replace(Pattern.compile("[s|m]ad"), "", options);

// Save the modified document
doc.save("modified-document.docx");
```

Пользовательские оценщики дают вам полный программный контроль над заменяемым текстом.

## Замена с помощью Regex (regex replace text java)

```java
// Load the document
Document doc = new Document("your-document.docx");

// Use regular expressions for finding and replacing text
doc.getRange().replace(Pattern.compile("[s|m]ad"), "bad", new FindReplaceOptions());

// Save the modified document
doc.save("modified-document.docx");
```

Краткий способ выполнить замену на основе шаблонов по всему документу.

## Распознавание и подстановки в шаблонах замены

```java
// Load the document
Document doc = new Document("your-document.docx");

// Create a FindReplaceOptions instance with UseSubstitutions set to true
FindReplaceOptions options = new FindReplaceOptions();
options.setUseSubstitutions(true);

// Use options when replacing text with a pattern
doc.getRange().replace(Pattern.compile("([A-z]+) give money to ([A-z]+)"), "$2 take money from $1", options);

// Save the modified document
doc.save("modified-document.docx");
```

Включите `UseSubstitutions`, чтобы ссылаться на группы захвата непосредственно в строке замены.

## Замена строкой (replace text word java)

```java
// Load the document
Document doc = new Document("your-document.docx");

// Replace text with a string
doc.getRange().replace("text-to-replace", "new-string", new FindReplaceOptions());

// Save the modified document
doc.save("modified-document.docx");
```

Самая простая форма замены — идеально подходит для статических заполнителей.

## Использование Legacy Order

```java
// Load the document
Document doc = new Document("your-document.docx");

// Create a FindReplaceOptions instance and set UseLegacyOrder to true
FindReplaceOptions options = new FindReplaceOptions();
options.setUseLegacyOrder(true);

// Use options when replacing text
doc.getRange().replace(Pattern.compile("\\[(.*?)\\]"), "", options);

// Save the modified document
doc.save("modified-document.docx");
```

Legacy order может потребоваться при работе со старыми документами, которые зависят от оригинальной последовательности обхода.

## Замена текста в таблице

```java
// Load the document
Document doc = new Document("your-document.docx");

// Get a specific table (e.g., the first table)
Table table = (Table) doc.getChild(NodeType.TABLE, 0, true);

// Use FindReplaceOptions for replacing text in the table
table.getRange().replace("old-text", "new-text", new FindReplaceOptions());

// Save the modified document
doc.save("modified-document.docx");
```

Точная замена внутри таблиц предотвращает нежелательные изменения в других частях документа.

## Распространённые проблемы и решения

- **HTML отображается некорректно** — убедитесь, что ваш HTML правильно сформирован и содержит обязательные теги (например, `<p>`, `<table>`).  
- **Regex не совпадает** — не забудьте экранировать специальные символы и при необходимости использовать `Pattern.CASE_INSENSITIVE`.  
- **Поля заменяются непреднамеренно** — установите `options.setIgnoreFields(true)`, чтобы защитить их.  
- **Производительность на больших документах** — используйте `UseLegacyOrder` или обрабатывайте секции по отдельности, чтобы уменьшить потребление памяти.

## Часто задаваемые вопросы

**В: Как скачать Aspose.Words for Java?**  
О: Вы можете скачать Aspose.Words for Java с сайта, перейдя по [this link](https://releases.aspose.com/words/java/).

**В: Можно ли использовать регулярные выражения для замены текста?**  
О: Да, вы можете использовать регулярные выражения для замены текста в Aspose.Words for Java. Это позволяет выполнять более продвинутые и гибкие операции поиска и замены.

**В: Как игнорировать текст внутри полей при замене?**  
О: Установите свойство `IgnoreFields` объекта `FindReplaceOptions` в `true`. Это исключит содержимое полей, например поля слияния, из замены.

**В: Можно ли заменить текст внутри заголовков и колонтитулов?**  
О: Абсолютно. Получите нужный заголовок или колонтитул через `HeaderFooterCollection` и примените метод `replace` с соответствующими параметрами.

**В: Что делает параметр `UseLegacyOrder`?**  
О: `UseLegacyOrder` заставляет движок поиска/замены обходить узлы в оригинальном порядке, используемом в более старых версиях Aspose.Words, что может быть полезно для совместимости со старыми документами.

---

**Последнее обновление:** 2026-01-03  
**Тестировано с:** Aspose.Words for Java 24.12  
**Автор:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}