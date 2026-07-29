---
category: general
date: 2026-07-29
description: 'Урок по установке размера кнопки в Java: узнайте, как вставить кнопку
  ActiveX в документ Word с помощью Java и Aspose.Words, а также как задать размер
  и создать пустой документ.'
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- set button size java
- how to insert activex
- how to set button
- java create blank word
- insert command button word
language: ru
lastmod: 2026-07-29
og_description: Руководство по установке размера кнопки в Java показывает, как вставить
  кнопку ActiveX в файл Word с помощью Java, изменить её размер и сохранить документ
  программно.
og_image_alt: set button size java example showing a Word document with an ActiveX
  command button
og_title: Установить размер кнопки в Java – Добавить кнопку ActiveX Command Button
  в Word с помощью Java
schemas:
- author: Aspose
  dateModified: '2026-07-29'
  description: 'set button size java tutorial: learn how to insert ActiveX command
    button in a Word document using Java and Aspose.Words, plus sizing and blank document
    creation.'
  headline: set button size java – Insert ActiveX Command Button in Word
  type: TechArticle
- description: 'set button size java tutorial: learn how to insert ActiveX command
    button in a Word document using Java and Aspose.Words, plus sizing and blank document
    creation.'
  name: set button size java – Insert ActiveX Command Button in Word
  steps:
  - name: 1. Set Up the Project and Import Aspose.Words
    text: 'First, create a new Maven (or Gradle) project and add the Aspose.Words
      dependency shown above. Then, import the required classes in your Java source
      file:'
  - name: 2. java create blank word Document
    text: Now we actually **java create blank word** document. This is the foundation
      on which we’ll later **insert command button word**.
  - name: 3. Initialize DocumentBuilder and Insert the ActiveX Control
    text: 'The `DocumentBuilder` is a helper that lets us add content, paragraphs,
      tables, and, yes, ActiveX controls. Here’s where we answer **how to insert activex**:'
  - name: 4. How to Set Button Size Java – Adjust Width and Height
    text: 'Now comes the heart of the tutorial: **how to set button size java**. The
      control exposes several layout properties—`Left`, `Top`, `Width`, and `Height`.
      Setting them directly controls the button’s appearance on the page.'
  - name: 5. Save the Document
    text: 'Finally, persist the document to disk:'
  - name: What if the button doesn’t appear in Word?
    text: '- **Check the Word version.** ActiveX controls require the desktop version
      of Word; Word Online strips them out. - **Make sure the Aspose.Words license
      is applied** (if you’re using a paid edition). An unlicensed evaluation version
      may embed a watermark but still shows the control.'
  - name: Can I change the button’s font or color?
    text: Yes. After inserting the control, you can access its underlying OLE object
      and manipulate the VBA properties. That’s a more advanced topic—look into `commandButton.getOleObject().setProperty("ForeColor",
      0xFF0000)` for a red caption, for example.
  - name: How do I handle the button’s click event?
    text: ActiveX command buttons fire a VBA `Click` event. To make the button functional,
      you’ll need to embed a macro in the same document. Aspose.Words can add a macro
      module via the `Document.getMacros()` API, but the macro code itself must be
      written in VBA.
  - name: What about different button types?
    text: 'Aspose.Words supports many `Forms2OleControlType` values: `CHECKBOX`, `OPTIONBUTTON`,
      `LISTBOX`, etc. Swap the enum constant in the `insertForms2OleControl` call
      to experiment.'
  type: HowTo
tags:
- Java
- Aspose.Words
- ActiveX
- Word Automation
title: Установить размер кнопки Java – Вставить кнопку ActiveX Command в Word
url: /ru/java/using-document-elements/set-button-size-java-insert-activex-command-button-in-word/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# установить размер кнопки java – Вставка ActiveX Command Button в Word

Когда‑нибудь задавались вопросом **how to set button size java**, когда автоматизируете документы Word? Возможно, вы создаёте инструмент отчётности, которому нужна кликабельная кнопка «Submit» прямо внутри файла .docx. В этом руководстве мы пройдём весь процесс — создание пустого документа Word, вставка ActiveX command button и явная установка его ширины и высоты — всё с помощью Java и Aspose.Words.

Мы также ответим на назойливый вопрос «**how to insert activex**», который возникает у многих разработчиков. К концу вы получите исполняемую программу, генерирующую файл Word с идеально‑размерной кнопкой, готовой к дальнейшей настройке.

---

## Что понадобится

- **Java Development Kit (JDK) 8 или новее** – код компилируется любой современной JDK.  
- **Aspose.Words for Java** (последняя версия на июль 2026). Скачайте JAR с [веб‑сайта Aspose](https://products.aspose.com/words/java) или через Maven:  
  ```xml
  <dependency>
      <groupId>com.aspose</groupId>
      <artifactId>aspose-words</artifactId>
      <version>23.10</version>
  </dependency>
  ```  
- IDE или простой текстовый редактор — подойдут IntelliJ IDEA, Eclipse или VS Code.  
- Папка, в которой вы хотите разместить сгенерированный **CommandButton.docx**.

Это всё. Никаких дополнительных библиотек Office interop, без COM‑трюков, только чистый Java.

---

## Пошаговая реализация

Мы разобьём решение на пять логических шагов. Каждый шаг имеет собственный заголовок H2; один из них содержит наш **primary keyword** для SEO.

### 1. Настройка проекта и импорт Aspose.Words

Сначала создайте новый проект Maven (или Gradle) и добавьте зависимость Aspose.Words, показанную выше. Затем импортируйте необходимые классы в ваш Java‑файл:

```java
import com.aspose.words.*;
```

> **Pro tip:** Если вы используете IDE, позвольте ей автоматически импортировать классы. Это экономит массу ввода и предотвращает опечатки.

### 2. java create blank word Document

Теперь мы действительно **java create blank word** документ. Это основа, на которой позже **insert command button word**.

```java
// Step 2: Create a new blank document
Document document = new Document();          // Starts with a clean, empty .docx
```

### 3. Инициализация DocumentBuilder и вставка ActiveX‑контроля

`DocumentBuilder` — вспомогательный класс, позволяющий добавлять контент, абзацы, таблицы и, да, ActiveX‑контролы. Здесь мы отвечаем на **how to insert activex**:

```java
// Step 3: Initialize a DocumentBuilder to work with the document
DocumentBuilder builder = new DocumentBuilder(document);

// Insert an ActiveX command button (COMMANDBUTTON is a built‑in type)
Forms2OleControl commandButton = builder.insertForms2OleControl(
        Forms2OleControlType.COMMANDBUTTON);
```

### 4. How to Set Button Size Java – Регулировка ширины и высоты

Теперь наступает сердце руководства: **how to set button size java**. Управление раскрывает несколько свойств расположения — `Left`, `Top`, `Width` и `Height`. Прямое задание этих свойств контролирует внешний вид кнопки на странице.

```java
// Step 4: Set button properties, including size
commandButton.setCaption("Click Me"); // Text shown on the button
commandButton.setLeft(100);           // Distance from the left margin (points)
commandButton.setTop(200);            // Distance from the top margin (points)
commandButton.setWidth(120);          // Width in points (≈1.67 inches)
commandButton.setHeight(30);          // Height in points (≈0.42 inches)
```

Почему именно такие числа? В Word один пункт равен 1/72 дюйма. Поэтому ширина `120` пунктов примерно 1,67 дюйма — достаточно для читаемой подписи, но не слишком громоздко. Корректируйте значения под ваш макет; те же свойства отвечают и на запрос **how to set button**.

> **Note:** Если нужен другой тип кнопки (например, флажок), замените `Forms2OleControlType.COMMANDBUTTON` на соответствующее значение enum.

### 5. Сохранение документа

Наконец, сохраняем документ на диск:

```java
// Step 5: Save the document with the embedded ActiveX control
document.save("YOUR_DIRECTORY/CommandButton.docx");
```

Замените `YOUR_DIRECTORY` абсолютным или относительным путём на вашей машине. После запуска программы откройте полученный файл в Microsoft Word. Вы увидите кнопку с надписью «Click Me», расположенную на 100 пт от левого края и 200 пт от верхнего, точно с теми размерами, которые мы задали.

---

## Полный рабочий пример

Ниже приведён полностью готовый к запуску Java‑класс. Скопируйте его в `CommandButtonActiveX.java`, скорректируйте путь вывода и нажмите **Run**.

```java
import com.aspose.words.*;

public class CommandButtonActiveX {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document (java create blank word)
        Document document = new Document();

        // Step 2: Initialize a DocumentBuilder to work with the document
        DocumentBuilder builder = new DocumentBuilder(document);

        // Step 3: Insert an ActiveX command button (how to insert activex)
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON);

        // Step 4: Set button properties – this is how to set button size java
        commandButton.setCaption("Click Me"); // Button text
        commandButton.setLeft(100);           // Left position (points)
        commandButton.setTop(200);            // Top position (points)
        commandButton.setWidth(120);          // Width (points)
        commandButton.setHeight(30);          // Height (points)

        // Step 5: Save the document (insert command button word)
        document.save("YOUR_DIRECTORY/CommandButton.docx");
    }
}
```

**Expected output:** Открывая `CommandButton.docx` в Word, вы увидите одну страницу с кликабельной кнопкой «Click Me», размещённой примерно по центру. Размеры кнопки соответствуют указанным значениям, подтверждая, что **set button size java** работает как задумано.

---

## Часто задаваемые вопросы и особые случаи

### Что делать, если кнопка не появляется в Word?

- **Проверьте версию Word.** ActiveX‑контролы требуют настольной версии Word; Word Online их удаляет.  
- **Убедитесь, что лицензия Aspose.Words применена** (если используете платную редакцию). Не лицензированная оценочная версия может добавить водяной знак, но всё равно покажет контрол.

### Можно ли изменить шрифт или цвет кнопки?

Да. После вставки контрола вы можете получить доступ к его внутреннему OLE‑объекту и менять свойства VBA. Это более продвинутая тема — посмотрите `commandButton.getOleObject().setProperty("ForeColor", 0xFF0000)` для красной подписи, например.

### Как обработать событие Click кнопки?

ActiveX‑кнопки генерируют событие VBA `Click`. Чтобы кнопка стала функциональной, необходимо встроить макрос в тот же документ. Aspose.Words может добавить модуль макроса через API `Document.getMacros()`, но сам код макроса должен быть написан на VBA.

### Что насчёт разных типов кнопок?

Aspose.Words поддерживает множество значений `Forms2OleControlType`: `CHECKBOX`, `OPTIONBUTTON`, `LISTBOX` и др. Просто замените константу enum в вызове `insertForms2OleControl`, чтобы поэкспериментировать.

---

## Профессиональные советы для production‑ready кода

1. **Используйте константы для значений расположения** — упростит будущие изменения.  
2. **Оборачивайте путь сохранения в объект `Path`**, чтобы избежать проблем с разделителями платформ.  
3. **Освобождайте объект Document** (или применяйте try‑with‑resources), если обрабатываете множество файлов в цикле.  
4. **Проверяйте существование папки вывода** перед вызовом `save`, чтобы избежать `FileNotFoundException`.

---

## Заключение

Вы только что освоили **set button size java**, создав пустой файл Word, вставив ActiveX command button и точно настроив его размеры — всё несколькими строками кода на Java. Это покрывает основные запросы **how to insert activex**, **how to set button**, **java create blank word** и **insert command button word** в одном самостоятельном примере.

Что дальше? Попробуйте изменить подпись кнопки, добавить макрос для обработки кликов или разместить несколько контролов на одной странице. Можно также исследовать конвертацию полученного .docx в PDF с помощью Aspose.Words, сохраняя кнопку как статическое изображение.

Экспериментируйте, а если возникнут сложности, оставляйте комментарий ниже. Приятного кодинга!

## Что стоит изучить дальше?

Следующие руководства охватывают тесно связанные темы, расширяющие техники, продемонстрированные в этом пособии. Каждый ресурс включает полностью работающие примеры кода с пошаговыми объяснениями, помогая вам освоить дополнительные возможности API и исследовать альтернативные подходы в собственных проектах.

- [Как создавать поля формы и добавлять контент с помощью DocumentBuilder в Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Как загружать документы Word с помощью Aspose.Words Java: Полное руководство](/words/english/java/document-operations/aspose-words-java-master-word-processing/)
- [Как сохранить документ как PDF с помощью Aspose.Words for Java](/words/english/java/document-loading-and-saving/saving-documents-as-pdf/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}