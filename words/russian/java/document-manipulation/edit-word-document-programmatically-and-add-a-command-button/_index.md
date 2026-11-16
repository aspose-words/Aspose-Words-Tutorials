---
category: general
date: 2026-11-15
description: Редактировать документ Word программно, чтобы вставить кнопку управления.
  Узнайте, как добавить кнопку, задать её имя и создать кнопку формы в Word за несколько
  минут.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- edit word document programmatically
- how to add button
- insert command button word
- create form button word
- set command button name
language: ru
lastmod: 2026-11-15
og_description: Редактировать документ Word программно и вставить кнопку команды.
  Это руководство показывает, как добавить кнопку, задать имя кнопки команды и быстро
  создать кнопку формы в Word.
og_image_alt: Screenshot of a Word document edited programmatically with a command
  button
og_title: Редактировать документ Word программно — добавить кнопку команды
schemas:
- author: Aspose
  dateModified: '2026-11-15'
  description: Edit Word document programmatically to insert a command button. Learn
    how to add button, set command button name, and create form button Word in minutes.
  headline: Edit Word document programmatically and add a command button
  type: TechArticle
- description: Edit Word document programmatically to insert a command button. Learn
    how to add button, set command button name, and create form button Word in minutes.
  name: Edit Word document programmatically and add a command button
  steps:
  - name: Expected output
    text: 'When you open the saved file:'
  - name: How to add button to a specific paragraph?
    text: '```java builder.moveToParagraph(2, true); // moves to third paragraph (0‑based
      index) Forms2OleControl btn = builder.insertForms2OleControl(); btn.setName("btnThirdParagraph");
      btn.setCaption("Click Me"); ```'
  - name: How to insert a button inside a table cell?
    text: '```java Table table = builder.startTable(); builder.insertCell(); builder.insertCell();
      builder.endTable();'
  - name: What if I need a larger button?
    text: '```java cmdBtn.setWidth(100); // width in points cmdBtn.setHeight(30);
      // height in points ```'
  - name: How to **insert command button word** using a different language (e.g.,
      C#)?
    text: 'The same logic applies; replace Java syntax with C# equivalents:'
  type: HowTo
tags:
- Word automation
- Aspose.Words
- Java
title: Редактировать документ Word программно и добавить кнопку.
url: /ru/java/document-manipulation/edit-word-document-programmatically-and-add-a-command-button/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Редактировать документ Word программно и добавить command button

Если вам нужно **edit Word document programmatically**, самый быстрый способ — использовать Aspose.Words API. В этом руководстве показано, как **how to add button** элементы управления, настроить их подпись и **set command button name**, чтобы документ мог выступать в роли простой формы. В конце у вас будет полностью редактируемый *.docx*, содержащий рабочий command button, готовый к дальнейшей обработке.

Вы узнаете, как **insert command button word**, **create form button word**, и управлять свойствами кнопки без ручного открытия Word. Единственное требование — базовая среда разработки Java и библиотека Aspose.Words for Java.

## Предварительные требования

- Java 17 или новее (код также работает с Java 8+)
- Aspose.Words for Java (скачайте с [Aspose.Words for Java](https://products.aspose.com/words/java/))
- Существующий документ Word (`input.docx`), который вы хотите изменить
- Знание Maven или Gradle для добавления зависимости Aspose.Words

```xml
<!-- Maven dependency -->
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.12</version>
</dependency>
```

## Шаг 1: Загрузить документ Word

Первая операция при **edit Word document programmatically** — загрузить исходный файл в объект `Document`. Этот объект представляет весь файл Word в памяти, позволяя манипулировать его содержимым.

```java
import com.aspose.words.*;

public class WordButtonDemo {
    public static void main(String[] args) throws Exception {
        // Load the existing Word file
        Document doc = new Document("YOUR_DIRECTORY/input.docx");
```

> **Почему это важно:** Загрузка документа создает структуру, похожую на DOM, которую Aspose.Words может обходить и изменять. Пропуск этого шага оставит вас без цели для вставки кнопки.

## Шаг 2: Создать `DocumentBuilder` для редактирования документа

`DocumentBuilder` работает как курсор внутри файла Word. Он позволяет вставлять текст, изображения и элементы управления формой в текущей позиции.

```java
        // Initialize a builder positioned at the start of the document
        DocumentBuilder builder = new DocumentBuilder(doc);
```

> **Подсказка:** Если вам нужна кнопка в определённом абзаце, сначала переместите builder с помощью `builder.moveToParagraph(index, true);`.

## Шаг 3: Вставить Forms2OleControl (command button)

Теперь мы отвечаем на главный вопрос **how to add button** в файле Word. Метод `insertForms2OleControl()` создаёт устаревший *Forms2.0* command button, который является наиболее совместимым элементом управления во всех версиях Word.

```java
        // Insert the command button at the builder's current cursor location
        Forms2OleControl cmdBtn = builder.insertForms2OleControl();
```

> **Особый случай:** Элемент управления Forms2.0 виден только в *Design Mode* Word. Если нужна более новая ActiveX‑кнопка, рассмотрите `insertOleControl()`, но устаревший элемент работает в большинстве сценариев автоматизации.

## Шаг 4: Настроить свойства кнопки

После вставки элемента управления вы можете **set command button name** и **insert command button word** (caption), чтобы сделать его удобным для пользователя.

```java
        // Set the internal name used by automation scripts
        cmdBtn.setName("cmdSubmit");

        // Set the text that appears on the button
        cmdBtn.setCaption("Submit");
```

> **Зачем эти свойства?**  
> - `setName` задаёт кнопке идентификатор, который может использовать VBA или внешние инструменты.  
> - `setCaption` — видимая подпись, фактически **creating form button word**, по которой кликают конечные пользователи.

Вы также можете изменить размер, позицию или добавить макрос, получив доступ к базовому OLE‑объекту, но эти темы выходят за рамки данного краткого руководства.

## Шаг 5: Сохранить изменённый документ

Наконец, сохраните изменения в новый файл. Этот шаг **creates form button word** в выходном документе.

```java
        // Save the updated document
        doc.save("YOUR_DIRECTORY/output.docx");
    }
}
```

> **Результат:** Открыв `output.docx` в Microsoft Word, вы увидите кнопку с надписью «Submit». При переключении Word в *Design Mode* (Developer → Design Mode) вы можете двойным щелчком по кнопке добавить макрос или просто использовать её как заполнитель в форме.

### Ожидаемый результат

Когда вы откроете сохранённый файл:

- Точка вставки курсора заменяется кнопкой.
- Кнопка отображает подпись **Submit**.
- Внутреннее имя кнопки — **cmdSubmit**, которое можно использовать в VBA или внешних скриптах автоматизации.

## Часто задаваемые вопросы и варианты

### Как добавить кнопку в конкретный абзац?

```java
builder.moveToParagraph(2, true); // moves to third paragraph (0‑based index)
Forms2OleControl btn = builder.insertForms2OleControl();
btn.setName("btnThirdParagraph");
btn.setCaption("Click Me");
```

### Как вставить кнопку в ячейку таблицы?

```java
Table table = builder.startTable();
builder.insertCell();
builder.insertCell();
builder.endTable();

builder.moveToCell(0, 0, 0, 0, true); // first row, first cell
Forms2OleControl cellBtn = builder.insertForms2OleControl();
cellBtn.setCaption("Cell Button");
```

### Что делать, если нужна более крупная кнопка?

```java
cmdBtn.setWidth(100);   // width in points
cmdBtn.setHeight(30);   // height in points
```

### Как **insert command button word** с использованием другого языка (например, C#)?

Тот же принцип применяется; замените синтаксис Java эквивалентами C#:

```csharp
Document doc = new Document("input.docx");
DocumentBuilder builder = new DocumentBuilder(doc);
Forms2OleControl btn = builder.InsertForms2OleControl();
btn.Name = "cmdSubmit";
btn.Caption = "Submit";
doc.Save("output.docx");
```

## Профессиональные советы и подводные камни

- **Pro tip:** Всегда вызывайте `builder.moveToDocumentEnd()` перед вставкой кнопки, если хотите разместить её в самом конце документа.  
- **Watch out for:** Сохранение в тот же файл, из которого вы открыли, может повредить документ при возникновении исключения. Используйте отдельный путь вывода, как показано.  
- **Compatibility:** Устаревшая кнопка Forms2.0 работает в Word 2007‑2021. Для Word в вебе рассмотрите использование элементов управления содержимым.  
- **Performance:** Загрузка очень больших документов (>100 MB) может потреблять значительную память. Используйте `Document.load(InputStream, LoadOptions)` с `LoadOptions.setLoadFormat(LoadFormat.DOCX)`, чтобы ограничить использование ресурсов.

## Полный рабочий пример

Ниже приведена полная, готовая к запуску Java‑программа. Скопируйте её в класс с именем `WordButtonDemo.java`, скорректируйте пути к файлам и запустите `mvn compile exec:java`.

```java
import com.aspose.words.*;

public class WordButtonDemo {
    public static void main(String[] args) throws Exception {
        // 1. Load the source document
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // 2. Create a builder positioned at the start
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 3. Insert a command button (Forms2OleControl)
        Forms2OleControl cmdBtn = builder.insertForms2OleControl();

        // 4. Set button properties – this is where we **set command button name**
        cmdBtn.setName("cmdSubmit");   // internal identifier
        cmdBtn.setCaption("Submit");   // visible text (creates form button word)

        // 5. Save the edited document
        doc.save("YOUR_DIRECTORY/output.docx");
    }
}
```

Запустите программу и откройте `output.docx`, чтобы убедиться, что кнопка отображается как ожидалось.

## Заключение

Теперь вы знаете, как **edit Word document programmatically**, чтобы **insert command button word**, **create form button word** и **set command button name** с помощью Aspose.Words for Java. Этот подход устраняет ручное редактирование, позволяет пакетную обработку форм и бесшовно интегрируется в автоматизированные рабочие процессы.

Далее вы можете изучить:

- Добавление VBA‑макросов к кнопке (`cmdBtn.getOleFormat().setMacroName("MyMacro")`)  
- Использование **content controls** для более богатых форм (`builder.insertCheckBox()` и т.д.)  
- Автоматизацию массовой вставки в нескольких документах с помощью цикла  

Не стесняйтесь экспериментировать с размером, позицией кнопки и обработкой событий, чтобы подобрать решение под ваш сценарий. Приятного кодинга!

## Что изучать дальше?

Следующие руководства охватывают тесно связанные темы, которые развивают техники, продемонстрированные в этом руководстве. Каждый ресурс включает полные рабочие примеры кода с пошаговыми объяснениями, помогающими освоить дополнительные возможности API и исследовать альтернативные подходы к реализации в ваших проектах.

- [How to add a command button programmatically in a Word document](/words/english/net/working-with-oleobjects-and-activex/how-to-add-a-command-button-programmatically-in-a-word-docum/)
- [Create word document programmatically and add ActiveX button](/words/english/net/working-with-oleobjects-and-activex/create-word-document-programmatically-and-add-activex-button/)
- [Add Command Button to Word Document with Aspose.Words – Complete Guide](/words/english/net/working-with-oleobjects-and-activex/add-command-button-to-word-document-with-aspose-words-comple/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}