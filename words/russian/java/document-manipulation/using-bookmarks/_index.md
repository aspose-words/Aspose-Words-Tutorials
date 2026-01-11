---
date: 2026-01-11
description: Узнайте, как показывать и скрывать закладки, а также создавать закладки
  в Java с помощью Aspose.Words for Java для эффективной навигации по документу и
  его манипуляций.
linktitle: Using Bookmarks
second_title: Aspose.Words Java Document Processing API
title: Показать/скрыть закладки с Aspose.Words для Java
url: /ru/java/document-manipulation/using-bookmarks/
weight: 17
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Показ/скрытие закладок с Aspose.Words for Java

## Введение в использование закладок в Aspose.Words for Java

Закладки — мощная функция в Aspose.Words for Java, позволяющая **create bookmark java**, перемещаться к определённому содержимому и даже **show hide bookmarks**, когда необходимо создавать разные версии документа. В этом пошаговом руководстве мы рассмотрим создание, доступ, обновление, копирование и переключение видимости закладок, предоставляя полный контроль над манипуляциями с документом.

## Быстрые ответы
- **What is the primary purpose of bookmarks?** To mark and later retrieve specific parts of a document. → **What is the primary purpose of bookmarks?** Отметить и позже извлечь определённые части документа.  
- **Can I hide bookmark markers in the final output?** Yes—use the show/hide API to toggle their visibility. → **Can I hide bookmark markers in the final output?** Да — используйте API show/hide для переключения их видимости.  
- **How do I create a bookmark inside a table cell?** Start and end the bookmark with `DocumentBuilder` while the cursor is inside the cell. → **How do I create a bookmark inside a table cell?** Начните и завершите закладку с помощью `DocumentBuilder`, когда курсор находится внутри ячейки.  
- **Is it possible to copy bookmarked text to another document?** Absolutely—use `NodeImporter` to preserve formatting. → **Is it possible to copy bookmarked text to another document?** Конечно — используйте `NodeImporter` для сохранения форматирования.  
- **What version of Aspose.Words is required?** Any recent release; the code works with the latest 2026 build. → **What version of Aspose.Words is required?** Любая недавняя версия; код работает с последней сборкой 2026 года.

## Что такое «show hide bookmarks»?

Функция **show hide bookmarks** позволяет программно отображать или скрывать разделители закладок в сохраняемом документе. Это полезно, когда нужно создать чистый вывод для конечных пользователей, одновременно сохраняя данные закладок для внутренней обработки.

## Зачем использовать закладки в автоматизации документов на Java?

- **Efficient navigation** – Переходите напрямую к разделам без сканирования всего файла.  
- **Dynamic content generation** – Вставляйте, заменяйте или удаляйте текст, связанный с закладкой.  
- **Conditional visibility** – Показывайте или скрывайте маркеры закладок в зависимости от предпочтений пользователя или формата вывода.  
- **Reusability** – Копируйте фрагменты с закладками между документами, сохраняя стили.

## Требования
- Java Development Kit (JDK) 8 или выше.  
- Библиотека Aspose.Words for Java, добавленная в ваш проект (Maven/Gradle или JAR).  
- Базовое знакомство с классами `Document` и `DocumentBuilder`.

## Пошаговое руководство

### Шаг 1: Создание закладки (create bookmark java)

Чтобы добавить закладку, её нужно начать, записать содержимое, затем завершить. В этом примере создаётся простая закладка с именем **My Bookmark**.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Start the bookmark
builder.startBookmark("My Bookmark");
builder.writeln("Text inside a bookmark.");

// End the bookmark
builder.endBookmark("My Bookmark");
```

### Шаг 2: Доступ к закладкам (access bookmarks java)

Закладки можно получить либо по их нулевому индексу, либо по имени. Приведённый ниже код демонстрирует оба подхода.

```java
Document doc = new Document("Your Directory Path" + "Bookmarks.docx");

// By index:
Bookmark bookmark1 = doc.getRange().getBookmarks().get(0);

// By name:
Bookmark bookmark2 = doc.getRange().getBookmarks().get("MyBookmark3");
```

### Шаг 3: Обновление данных закладки (update bookmark text)

Вы можете переименовать закладку или заменить её текстовое содержимое. Это удобно, когда исходный документ изменяется.

```java
Document doc = new Document("Your Directory Path" + "Bookmarks.docx");
Bookmark bookmark = doc.getRange().getBookmarks().get("MyBookmark1");
String name = bookmark.getName();
String text = bookmark.getText();
bookmark.setName("RenamedBookmark");
bookmark.setText("This is new bookmarked text.");
```

### Шаг 4: Работа с текстом закладки (copy bookmarked text)

Копирование фрагмента с закладкой в другой документ с сохранением оригинального форматирования просто с помощью `NodeImporter`.

```java
Document srcDoc = new Document("Your Directory Path" + "Bookmarks.docx");
Bookmark srcBookmark = srcDoc.getRange().getBookmarks().get("MyBookmark1");
Document dstDoc = new Document();
NodeImporter importer = new NodeImporter(srcDoc, dstDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING);
appendBookmarkedText(importer, srcBookmark, dstDoc.getLastSection().getBody());
dstDoc.save("Your Directory Path" + "WorkingWithBookmarks.CopyBookmarkedText.docx");
```

### Шаг 5: Показ и скрытие закладок (show hide bookmarks)

Следующий фрагмент кода демонстрирует, как скрыть маркеры закладки в сохраняемом файле. Передайте `false` для скрытия, `true` для отображения.

```java
Document doc = new Document("Your Directory Path" + "Bookmarks.docx");
showHideBookmarkedContent(doc, "MyBookmark1", false);
doc.save("Your Directory Path" + "WorkingWithBookmarks.ShowHideBookmarks.docx");
```

### Шаг 6: Развязывание закладок строк (bookmark table cell)

Когда закладки охватывают строки таблицы, они могут запутаться. Нижеуказанные вспомогательные методы развязывают их и позволяют удалить конкретную строку по её закладке.

```java
Document doc = new Document("Your Directory Path" + "Table column bookmarks.docx");
untangle(doc);
deleteRowByBookmark(doc, "ROW2");
doc.save("Your Directory Path" + "WorkingWithBookmarks.UntangleRowBookmarks.docx");
```

## Распространённые проблемы и решения

| Issue | Solution |
|-------|----------|
| **Bookmark not found** | Убедитесь, что имя закладки точно совпадает (с учётом регистра) и документ был сохранён после создания. |
| **Copied text loses formatting** | Используйте `ImportFormatMode.KEEP_SOURCE_FORMATTING` с `NodeImporter`, как показано в Шаге 4. |
| **Show/hide does not affect output** | Убедитесь, что вызываете `showHideBookmarkedContent` **до** сохранения документа. |
| **Bookmark inside a table cell is ignored** | Выполняйте вызовы start/end, пока курсор builder находится внутри целевой ячейки. |

## Часто задаваемые вопросы

**Q: Как создать закладку в ячейке таблицы?**  
A: Используйте `DocumentBuilder`, чтобы переместить курсор в нужную ячейку, затем вызовите `startBookmark` и `endBookmark` вокруг содержимого ячейки.

**Q: Можно ли скопировать закладку в другой документ?**  
A: Да — используйте класс `NodeImporter` (см. Шаг 4) для импорта узла с закладкой, сохраняя его оригинальное форматирование.

**Q: Как удалить строку по её закладке?**  
A: Сначала найдите строку, содержащую закладку, затем вызовите `remove` у узла строки (как показано в Шаге 6).

**Q: Какие типичные сценарии использования закладок?**  
A: Генерация оглавления, извлечение конкретных разделов для отчётов и автоматизация сборки документов на основе выбора пользователя.

**Q: Где можно найти более подробную информацию о Aspose.Words for Java?**  
A: Для подробной документации и загрузок посетите [Aspose.Words for Java Documentation](https://reference.aspose.com/words/java/).

---

**Последнее обновление:** 2026-01-11  
**Тестировано с:** Aspose.Words for Java 24.11 (2026)  
**Автор:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}