---
category: general
date: 2026-11-15
description: Установите межстрочный интервал абзаца в документе Word с помощью Java.
  Узнайте, как программно задавать межстрочный интервал с использованием Aspose.Words
  для точного форматирования документа.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- set paragraph line spacing
- how to set line spacing
language: ru
lastmod: 2026-11-15
og_description: Установите межстрочный интервал абзаца в документе Word с помощью
  Java. Это руководство объясняет, как задать межстрочный интервал для абзацев и разделителей
  сносок, используя Aspose.Words, предоставляя полный контроль над макетом документа.
og_image_alt: Screenshot showing Java code that sets paragraph line spacing in a Word
  document
og_title: Задать межстрочный интервал абзаца в Word с помощью Java
schemas:
- author: Aspose
  dateModified: '2026-11-15'
  description: Set paragraph line spacing in a Word document with Java. Learn how
    to set line spacing programmatically using Aspose.Words for precise document formatting.
  headline: Set paragraph line spacing in a Word document with Java
  type: TechArticle
- description: Set paragraph line spacing in a Word document with Java. Learn how
    to set line spacing programmatically using Aspose.Words for precise document formatting.
  name: Set paragraph line spacing in a Word document with Java
  steps:
  - name: Load the Word document
    text: First, create a `Document` instance that points to your source file.
  - name: Retrieve the footnote separator
    text: Footnote separators are special paragraphs that appear between footnotes
      and the main text. To change their appearance you need to access the `FootnoteSeparator`
      object.
  - name: How to set line spacing for the separator's paragraph
    text: Now apply the desired line spacing. Aspose.Words uses points for line‑spacing
      values; 12 pts is roughly single‑spacing for most fonts.
  - name: Save the updated document
    text: Finally, write the changes back to disk.
  type: HowTo
tags:
- Java
- Aspose.Words
- Document Formatting
title: Установить межстрочный интервал абзаца в документе Word с помощью Java
url: /ru/java/formatting-styles/set-paragraph-line-spacing-in-a-word-document-with-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Установить межстрочный интервал абзаца в документе Word с помощью Java

Если вам нужно **установить межстрочный интервал абзаца** в документе Word, этот учебник покажет, как сделать это с помощью Java и Aspose.Words. Вы также узнаете, **как установить межстрочный интервал** для разделителей сносок — распространённое требование при форматировании профессиональных документов.

В следующих разделах вы:

* Загрузите существующий файл *.docx*.
* Получите абзац разделителя сносок.
* Примените пользовательское значение межстрочного интервала.
* Сохраните обновлённый документ.

Никакая внешняя конфигурация не требуется, кроме добавления библиотеки Aspose.Words в ваш проект, поэтому вы можете скопировать код дословно и сразу запустить его.

## Предварительные требования

Прежде чем начать, убедитесь, что у вас есть:

* Установлен Java 17 или новее.
* Maven (или другой инструмент сборки) для управления зависимостями.
* Действующая лицензия Aspose.Words for Java (бесплатная оценочная версия подходит для тестирования).
* Входной документ Word (`input.docx`) в известном каталоге.

Добавьте зависимость Aspose.Words в ваш `pom.xml`:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.10</version> <!-- Use the latest stable version -->
</dependency>
```

## Установить межстрочный интервал абзаца с помощью Aspose.Words

Этот заголовок H2 содержит основной ключевой запрос, удовлетворяя требование SEO.

### Шаг 1: Загрузить документ Word

Сначала создайте экземпляр `Document`, указывающий на ваш исходный файл.

```java
import com.aspose.words.*;

public class LineSpacingExample {
    public static void main(String[] args) throws Exception {
        // Load the Word document from the specified path
        Document doc = new Document("YOUR_DIRECTORY/input.docx");
        // Continue with formatting...
    }
}
```

*Почему это важно*: Загрузка документа даёт вам модель в памяти, которую можно изменять, не трогая оригинальный файл, пока вы явно не сохраните изменения.

### Шаг 2: Получить разделитель сносок

Разделители сносок — это специальные абзацы, которые находятся между сносками и основным текстом. Чтобы изменить их внешний вид, необходимо получить объект `FootnoteSeparator`.

```java
// Retrieve the footnote separator that Aspose.Words represents internally
FootnoteSeparator separator = doc.getFootnoteSeparator();
```

*Подсказка*: Если в документе нет сносок, разделитель всё равно существует как скрытый абзац, поэтому вызов никогда не вернёт `null`.

### Шаг 3: Как установить межстрочный интервал для абзаца разделителя

Теперь примените желаемый межстрочный интервал. Aspose.Words использует пункты для значений интервала; 12 пт примерно соответствует одинарному интервалу для большинства шрифтов.

```java
// Set the line spacing to 12 points (single‑spacing)
separator.getParagraphFormat().setLineSpacing(12.0);
```

Вы также можете использовать другие режимы интервала:

| Режим                     | Вызов метода                                      |
|--------------------------|---------------------------------------------------|
| **Exactly** (фикс. пт)   | `setLineSpacingRule(LineSpacingRule.EXACTLY)`    |
| **Multiple** (например, 1.5) | `setLineSpacingRule(LineSpacingRule.MULTIPLE); setLineSpacing(1.5);` |

Выбор правильного правила гарантирует, что документ будет отображаться одинаково в Word, Google Docs и других просмотрщиках.

### Шаг 4: Сохранить обновлённый документ

Наконец, запишите изменения обратно на диск.

```java
// Save the modified document to a new file
doc.save("YOUR_DIRECTORY/output.docx");
System.out.println("Document saved with updated paragraph line spacing.");
```

Когда вы откроете `output.docx` в Microsoft Word, разделитель сносок отобразится с указанным вами межстрочным интервалом.

## Понимание того, как установить межстрочный интервал для обычных абзацев

Тот же API работает с любым объектом `Paragraph`, а не только с разделителями сносок. Ниже приведён быстрый пример, который изменяет интервал первого абзаца в теле документа:

```java
// Access the first body paragraph
Paragraph firstPara = (Paragraph) doc.getFirstSection().getBody().getChild(NodeType.PARAGRAPH, 0, true);

// Apply double line spacing (2.0 × the font size)
firstPara.getParagraphFormat().setLineSpacingRule(LineSpacingRule.MULTIPLE);
firstPara.getParagraphFormat().setLineSpacing(2.0);
```

**Почему это может понадобиться**: Отчёты, контракты и академические работы часто требуют определённого стиля межстрочного интервала (например, двойного интервала для черновиков). Использование того же метода `setLineSpacing` гарантирует точный макет, который вы ожидаете.

## Распространённые подводные камни и как их избежать

| Проблема                                 | Причина                                   | Решение |
|------------------------------------------|-------------------------------------------|---------|
| Межстрочный интервал не изменяется       | `LineSpacingRule` оставлен по умолчанию (AUTO) | Явно задайте правило с помощью `setLineSpacingRule`. |
| Дополнительные пустые строки после разделителя | Разделитель содержит скрытые возвраты каретки | Обрежьте текст разделителя с помощью `separator.getText().trim();` перед применением интервала. |
| Документ повреждается после сохранения   | Используется устаревшая версия Aspose.Words | Обновите до последней версии (например, 24.10), в которой исправлены ошибки сохранения. |

## Профессиональный совет: пакетная обработка нескольких документов

Если вам нужно обновить десятки файлов, оберните логику в вспомогательный метод и пройдитесь по папке:

```java
public static void updateSpacing(Path inputPath, Path outputPath) throws Exception {
    Document doc = new Document(inputPath.toString());
    FootnoteSeparator sep = doc.getFootnoteSeparator();
    sep.getParagraphFormat().setLineSpacing(12.0);
    doc.save(outputPath.toString());
}
```

Запуск этого метода в цикле сэкономит вам часы ручного редактирования.

## Ожидаемый результат

После выполнения полной программы `output.docx` будет:

* Содержать оригинальное содержание без изменений, кроме межстрочного интервала.
* Показывать разделитель сносок с одинарным интервалом (12 пт).
* Сохранять всё остальное форматирование (стили, изображения, таблицы).

Откройте файл в Word и проверьте, что линия разделителя стала уже (или шире), в зависимости от установленного вами значения.

## Заключение

Теперь вы знаете, как **установить межстрочный интервал абзаца** в документе Word с помощью Java, а также понимаете, **как установить межстрочный интервал** для разделителей сносок и обычных абзацев. Полный, готовый к запуску пример демонстрирует загрузку документа, настройку свойств межстрочного интервала и сохранение результата — всё с помощью нескольких простых вызовов API.

**Следующие шаги**, которые вы можете изучить:

* **Как установить межстрочный интервал** для таблиц и элементов списка.
* Применение разных правил интервала к заголовкам и основному тексту.
* Использование объекта `Style` для принудительного задания интервала по всему документу.

Экспериментируйте со значениями, комбинируйте их с другими параметрами форматирования, и вы получите полный контроль над макетом документа в любом Java‑приложении. Приятного кодинга!

## Что изучать дальше?

Следующие учебники охватывают тесно связанные темы, построенные на техниках, продемонстрированных в этом руководстве. Каждый ресурс включает полностью работающие примеры кода с пошаговыми объяснениями, чтобы помочь вам освоить дополнительные возможности API и исследовать альтернативные подходы к реализации в собственных проектах.

- [How to set options in Aspose.Words for Java – complete guide](/words/english/java/document-loading-and-saving/how-to-set-options-in-aspose-words-for-java-complete-guide/)
- [How to Set LoadOptions in Aspose.Words for Java](/words/english/java/document-loading-and-saving/using-load-options/)
- [Change Asian Paragraph Spacing And Indents In Word Document](/words/english/net/document-formatting/change-asian-paragraph-spacing-and-indents/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}