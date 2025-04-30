---
"description": "Узнайте, как клонировать и объединять документы в Aspose.Words для Java. Пошаговое руководство с примерами исходного кода."
"linktitle": "Клонирование и объединение документов"
"second_title": "API обработки документов Java Aspose.Words"
"title": "Клонирование и объединение документов в Aspose.Words для Java"
"url": "/ru/java/document-manipulation/cloning-and-combining-documents/"
"weight": 27
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Клонирование и объединение документов в Aspose.Words для Java


## Введение в клонирование и объединение документов в Aspose.Words для Java

В этом уроке мы рассмотрим, как клонировать и объединять документы с помощью Aspose.Words для Java. Мы рассмотрим различные сценарии, включая клонирование документа, вставку документов в точки замены, закладки и во время операций слияния почты.

## Шаг 1: Клонирование документа

Чтобы клонировать документ в Aspose.Words для Java, вы можете использовать `deepClone()` метод. Вот простой пример:

```java
Document doc = new Document("Your Directory Path" + "Document.docx");
Document clone = doc.deepClone();
clone.save("Your Directory Path" + "CloneAndCombineDocuments.CloningDocument.docx");
```

Этот код создаст глубокую копию исходного документа и сохранит ее как новый файл.

## Шаг 2: Вставка документов в точки замены

Вы можете вставлять документы в определенные точки замены в другом документе. Вот как это можно сделать:

```java
Document mainDoc = new Document("Your Directory Path" + "Document insertion 1.docx");
FindReplaceOptions options = new FindReplaceOptions();
options.setDirection(FindReplaceDirection.BACKWARD);
options.setReplacingCallback(new InsertDocumentAtReplaceHandler());
mainDoc.getRange().replace(Pattern.compile("\\[MY_DOCUMENT\\]"), "", options);
mainDoc.save("Your Directory Path" + "CloneAndCombineDocuments.InsertDocumentAtReplace.docx");
```

В этом примере мы используем `FindReplaceOptions` объект для указания обработчика обратного вызова для замены. `InsertDocumentAtReplaceHandler` класс обрабатывает логику вставки.

## Шаг 3: Вставка документов в закладки

Чтобы вставить документ в определенную закладку в другом документе, можно использовать следующий код:

```java
Document mainDoc = new Document("Your Directory Path" + "Document insertion 1.docx");
Document subDoc = new Document("Your Directory Path" + "Document insertion 2.docx");
Bookmark bookmark = mainDoc.getRange().getBookmarks().get("insertionPlace");
insertDocument(bookmark.getBookmarkStart().getParentNode(), subDoc);
mainDoc.save("Your Directory Path" + "CloneAndCombineDocuments.InsertDocumentAtBookmark.docx");
```

Здесь мы находим закладку по имени и используем `insertDocument` метод вставки содержимого `subDoc` документ в месте закладки.

## Шаг 4: Вставка документов во время слияния почты

Вы можете вставлять документы во время операции слияния почты в Aspose.Words for Java. Вот как:

```java
Document mainDoc = new Document("Your Directory Path" + "Document insertion 1.docx");
mainDoc.getMailMerge().setFieldMergingCallback(new InsertDocumentAtMailMergeHandler());
mainDoc.getMailMerge().execute(new String[] { "Document_1" }, new Object[] { "Your Directory Path" + "Document insertion 2.docx" });
mainDoc.save("Your Directory Path" + "CloneAndCombineDocuments.InsertDocumentAtMailMerge.doc");
```

В этом примере мы устанавливаем обратный вызов для слияния полей с помощью `InsertDocumentAtMailMergeHandler` класс для обработки вставки документа, указанного в поле «Document_1».

## Заключение

Клонирование и объединение документов в Aspose.Words для Java можно выполнить с помощью различных методов. Если вам нужно клонировать документ, вставить содержимое в точки замены, закладки или во время слияния почты, Aspose.Words предоставляет мощные функции для беспрепятственного управления документами.

## Часто задаваемые вопросы

### Как клонировать документ в Aspose.Words для Java?

Вы можете клонировать документ в Aspose.Words для Java, используя `deepClone()` метод. Вот пример:

```java
Document doc = new Document("Your Directory Path" + "Document.docx");
Document clone = doc.deepClone();
clone.save("Your Directory Path" + "ClonedDocument.docx");
```

### Как вставить документ в закладку?

Чтобы вставить документ в закладку в Aspose.Words для Java, вы можете найти закладку по имени, а затем использовать `insertDocument` метод вставки контента. Вот пример:

```java
Document mainDoc = new Document("Your Directory Path" + "MainDocument.docx");
Document subDoc = new Document("Your Directory Path" + "SubDocument.docx");
Bookmark bookmark = mainDoc.getRange().getBookmarks().get("MyBookmark");
insertDocument(bookmark.getBookmarkStart().getParentNode(), subDoc);
mainDoc.save("Your Directory Path" + "CombinedDocument.docx");
```

### Как вставить документы во время слияния почты в Aspose.Words для Java?

Вы можете вставлять документы во время слияния почты в Aspose.Words для Java, установив обратный вызов слияния полей и указав документ для вставки. Вот пример:

```java
Document mainDoc = new Document("Your Directory Path" + "MainDocument.docx");
mainDoc.getMailMerge().setFieldMergingCallback(new InsertDocumentAtMailMergeHandler());
mainDoc.getMailMerge().execute(new String[] { "DocumentField" }, new Object[] { "Your Directory Path" + "DocumentToInsert.docx" });
mainDoc.save("Your Directory Path" + "MergedDocument.docx");
```

В этом примере `InsertDocumentAtMailMergeHandler` класс обрабатывает логику вставки для «DocumentField» во время слияния почты.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}