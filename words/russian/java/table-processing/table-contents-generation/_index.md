---
title: Генерация содержания
linktitle: Генерация содержания
second_title: API обработки документов Java Aspose.Words
description: Узнайте, как создать динамическое оглавление с помощью Aspose.Words для Java. Освойте генерацию TOC с пошаговыми инструкциями и примерами исходного кода.
weight: 14
url: /ru/java/table-processing/table-contents-generation/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Генерация содержания

## Введение

Вы когда-нибудь испытывали трудности с созданием динамичного и профессионально выглядящего оглавления (TOC) в документах Word? Не ищите дальше! С Aspose.Words для Java вы можете автоматизировать весь процесс, экономя время и гарантируя точность. Независимо от того, создаете ли вы комплексный отчет или научную работу, это руководство проведет вас через программную генерацию TOC с помощью Java. Готовы погрузиться? Давайте начнем!

## Предпосылки

Прежде чем приступить к кодированию, убедитесь, что у вас есть следующее:

1.  Java Development Kit (JDK): установлен в вашей системе. Вы можете загрузить его с[Веб-сайт Oracle](https://www.oracle.com/java/technologies/javase-downloads.html).
2.  Библиотека Aspose.Words для Java: загрузите последнюю версию с сайта[страница релиза](https://releases.aspose.com/words/java/).
3. Интегрированная среда разработки (IDE): например, IntelliJ IDEA, Eclipse или NetBeans.
4.  Временная лицензия Aspose: чтобы избежать ограничений оценки, получите[временная лицензия](https://purchase.aspose.com/temporary-license/).

## Импортные пакеты

Для эффективного использования Aspose.Words for Java убедитесь, что вы импортируете требуемые классы. Вот импорты:

```java
import com.aspose.words.*;
```

Чтобы создать динамическое оглавление в документе Word, выполните следующие действия.

## Шаг 1: Инициализация документа и DocumentBuilder

 Первый шаг — создать новый документ и использовать`DocumentBuilder` класс для манипулирования им.


```java
string dataDir = "Your Document Directory";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

- `Document`: Представляет документ Word.
- `DocumentBuilder`: Вспомогательный класс, позволяющий легко манипулировать документом.

## Шаг 2: Вставьте оглавление

Теперь давайте вставим оглавление в начало документа.


```java
builder.insertTableOfContents("\\o \"1-3\" \\h \\z \\u");
builder.insertBreak(BreakType.PAGE_BREAK);
```

- `insertTableOfContents`: Вставляет поле TOC. Параметры указывают:
  - `\o "1-3"`: Включить заголовки уровней 1–3.
  - `\h`: Сделать записи гиперссылками.
  - `\z`: Подавить нумерацию страниц для веб-документов.
  - `\u`: Сохранять стили для гиперссылок.
- `insertBreak`: Добавляет разрыв страницы после оглавления.

## Шаг 3: Добавьте заголовки для заполнения оглавления

ЧТОБЫ заполнить оглавление, вам необходимо добавить абзацы со стилями заголовков.


```java
builder.getParagraphFormat().setStyleIdentifier(StyleIdentifier.HEADING_1);
builder.writeln("Heading 1");

builder.getParagraphFormat().setStyleIdentifier(StyleIdentifier.HEADING_2);
builder.writeln("Heading 1.1");
builder.writeln("Heading 1.2");

builder.getParagraphFormat().setStyleIdentifier(StyleIdentifier.HEADING_1);
builder.writeln("Heading 2");
```

- `setStyleIdentifier` : Устанавливает стиль абзаца на определенный уровень заголовка (например,`HEADING_1`, `HEADING_2`).
- `writeln`: Добавляет текст в документ с указанным стилем.

## Шаг 4: Добавьте вложенные заголовки

Чтобы продемонстрировать уровни оглавления, включите вложенные заголовки.


```java
builder.getParagraphFormat().setStyleIdentifier(StyleIdentifier.HEADING_3);
builder.writeln("Heading 3.1.1");
builder.writeln("Heading 3.1.2");
builder.writeln("Heading 3.1.3");

builder.getParagraphFormat().setStyleIdentifier(StyleIdentifier.HEADING_4);
builder.writeln("Heading 3.1.3.1");
builder.writeln("Heading 3.1.3.2");
```

- Добавьте заголовки более глубоких уровней, чтобы отобразить иерархию в оглавлении.

## Шаг 5: Обновите поля TOC

Поле TOC необходимо обновить для отображения последних заголовков.


```java
doc.updateFields();
```

- `updateFields`: Обновляет все поля в документе, гарантируя, что оглавление отражает добавленные заголовки.

## Шаг 6: Сохраните документ

Наконец, сохраните документ в желаемом формате.


```java
doc.save(dataDir + "DocumentBuilder.InsertToc.docx");
```

- `save` : Экспортирует документ в`.docx` файл. Вы можете указать другие форматы, такие как`.pdf` или`.txt` если необходимо.

## Заключение

Поздравляем! Вы успешно создали динамическое оглавление в документе Word с помощью Aspose.Words для Java. Всего несколькими строками кода вы автоматизировали задачу, которая в противном случае могла бы занять часы. Итак, что дальше? Попробуйте поэкспериментировать с различными стилями и форматами заголовков, чтобы адаптировать TOC к конкретным потребностям.

## Часто задаваемые вопросы

### Могу ли я дополнительно настроить формат TOC?
Конечно! Вы можете настроить параметры TOC, такие как включение номеров страниц, выравнивание текста или использование пользовательских стилей заголовков.

### Обязательно ли наличие лицензии для Aspose.Words для Java?
 Да, для полной функциональности требуется лицензия. Вы можете начать с[временная лицензия](https://purchase.aspose.com/temporary-license/).

### Могу ли я создать оглавление для существующего документа?
 Да! Загрузите документ в`Document` объект и выполните те же шаги для вставки и обновления оглавления.

### Работает ли это для экспорта в PDF?
 Да, оглавление появится в PDF-файле, если вы сохраните документ в формате`.pdf` формат.

### Где я могу найти дополнительную документацию?
 Проверьте[Документация Aspose.Words для Java](https://reference.aspose.com/words/java/) для получения дополнительных примеров и подробностей.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
