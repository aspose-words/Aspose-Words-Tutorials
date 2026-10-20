---
category: general
date: 2026-07-16
description: Установите размер кнопки программно в документе Word с помощью Aspose.Words
  for Java. Узнайте, как вставить кнопку ActiveX, задать её расположение и многое
  другое.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- set button size
- insert activex button
- programmatically add button
- set button location
- create word document button
language: ru
lastmod: 2026-07-16
og_description: Установите размер кнопки в документе Word с помощью Java. Это пошаговое
  руководство показывает, как вставить кнопку ActiveX, задать её положение и программно
  добавить кнопку.
og_image_alt: Screenshot of a Word document where the button size has been set using
  Aspose.Words for Java
og_title: Установите размер кнопки в Word с помощью Java – Полный учебник Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-07-16'
  description: Set button size programmatically in a Word document using Aspose.Words
    for Java. Learn how to insert ActiveX button, set button location and more.
  headline: Set Button Size in Word with Java – Complete Aspose.Words Guide
  type: TechArticle
- description: Set button size programmatically in a Word document using Aspose.Words
    for Java. Learn how to insert ActiveX button, set button location and more.
  name: Set Button Size in Word with Java – Complete Aspose.Words Guide
  steps:
  - name: Expected Output Screenshot
    text: '![Word document showing the inserted button with the set button size](https://example.com/images/set-button-size.png
      "Screenshot of a Word file where the button size has been set using Aspose.Words
      for Java")'
  - name: “Can I set the button size using centimeters instead of points?”
    text: Word’s API only accepts points, but you can convert centimeters to points
      (`points = cm * 28.3465`). Write a small helper method if you prefer metric
      units.
  - name: “What if I need the button to appear on a specific page?”
    text: After inserting the button, you can move the cursor to a particular page
      using `builder.moveToPage(pageNumber)`. Insert the control right after the move,
      then set its location as shown above.
  - name: “Does this work with .doc (Word 97‑2003) files?”
    text: Yes—Aspose.Words automatically handles older formats. Just change the file
      extension in `doc.save("Demo.doc")`.
  type: HowTo
tags:
- Aspose.Words
- Java
- ActiveX
- Word automation
title: Установка размера кнопки в Word с помощью Java – Полное руководство по Aspose.Words
url: /ru/java/using-document-elements/set-button-size-in-word-with-java-complete-aspose-words-guid/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Установить размер кнопки в Word с помощью Java – Полное руководство Aspose.Words

Задумывались ли вы когда‑нибудь, как **установить размер кнопки** внутри файла Word без открытия пользовательского интерфейса? Вы не одиноки. Когда нужно быстро сгенерировать документ с заполненной формой — например, пакет приветствия с кнопкой «Submit» — выполнение этого программно экономит часы ручной работы.

В этом руководстве мы пройдём точные шаги по **вставке ActiveX‑кнопки**, настройке её размеров, правильному позиционированию и окончательному сохранению файла. К концу вы сможете **программно добавлять кнопку** в любой документ Word, используя Aspose.Words for Java.

## Предварительные требования – Что вам нужно перед началом

- **Java Development Kit (JDK) 8+** – код работает на любой современной JDK.  
- **Aspose.Words for Java** library (download the latest JAR from the official site).  
- **IDE** of your choice—IntelliJ IDEA, Eclipse, or even a simple text editor works.  
- Basic familiarity with Java syntax; no deep Word‑automation knowledge required.

> *Совет:* Keep the Aspose.Words JAR on your project’s classpath, otherwise you’ll hit `ClassNotFoundException` the moment you try to import `com.aspose.words.*`.

## Шаг 1: Создать новый документ Word

The first thing we do is spin up a blank document and a `DocumentBuilder`. Think of the builder as a pen that lets us draw anything inside the file.

```java
import com.aspose.words.*;

public class InsertCommandButtonDemo {
    public static void main(String[] args) throws Exception {
        // Create an empty document.
        Document doc = new Document();

        // DocumentBuilder gives us a fluent API to add content.
        DocumentBuilder builder = new DocumentBuilder(doc);
```

> **Почему это важно:** The `Document` object represents the entire .docx file, while the `DocumentBuilder` is the workhorse that lets us insert paragraphs, tables, and—yes—ActiveX controls.

## Шаг 2: Вставить ActiveX‑кнопку – Момент «Insert ActiveX Button»

Now we actually **insert activex button** into the document. Aspose.Words exposes a convenient method `insertForms2OleControl` that returns a `Forms2OleControl` object.

```java
        // Insert an ActiveX CommandButton control.
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMAND_BUTTON);
        commandButton.setName("cmdSubmit");   // Programmatic name.
        commandButton.setCaption("Submit");   // Text shown on the button.
```

> *Что происходит под капотом?* `Forms2OleControlType.COMMAND_BUTTON` tells Word we want a classic CommandButton, the same kind you’d drop from the Developer tab in the UI.

## Шаг 3: Установить размер и позицию кнопки – Основная логика «Set Button Size»

Here’s where the primary keyword shines. We’ll **set button size** and also **set button location** so the control appears exactly where we want it on the page.

```java
        // Position the button (distance from the left/top edges in points).
        commandButton.setLeft(100);   // 100 points from the left margin.
        commandButton.setTop(150);    // 150 points from the top margin.

        // Set the button's dimensions.
        commandButton.setWidth(80);   // Width = 80 points.
        commandButton.setHeight(30);  // Height = 30 points.
```

> **Почему это важно:** Points are the native measurement unit in Word (1 point = 1/72 inch). By tweaking `setLeft`, `setTop`, `setWidth`, and `setHeight` you gain pixel‑perfect control—no more “it looks right on my screen but not on the printer”.

> *Распространённая ошибка:* Forgetting to set either width or height will leave the button at the default size, which can be too small to click. Always specify both.

## Шаг 4: Сохранить документ – «Create Word Document Button» завершён

Finally, we write the file to disk. The name suggests we’re **creating a Word document button** inside a .docx.

```java
        // Persist the document to the file system.
        doc.save("CommandButtonDemo.docx");
    }
}
```

When you open `CommandButtonDemo.docx` in Microsoft Word, you’ll see a **Submit** button placed 100 pt from the left edge and 150 pt from the top, sized at 80 × 30 pt. Clicking it in the UI will trigger the default ActiveX behavior (which you can later wire up with VBA if needed).

### Ожидаемый скриншот результата

![установить размер кнопки в документе Word с помощью Java](https://example.com/images/set-button-size.png "Скриншот файла Word, где размер кнопки установлен с помощью Aspose.Words for Java")

*Alt text:* установить размер кнопки в документе Word с помощью Java

## Шаг 5 (Опционально): Добавить больше элементов управления или стилизовать кнопку

If you need to **programmatically add button** controls beyond a single Submit button, just repeat the insertion block with new names and captions. You can also adjust font, background color, or even bind VBA macros later.

```java
        // Example: Adding a Cancel button next to Submit.
        Forms2OleControl cancelBtn = builder.insertForms2OleControl(
                Forms2OleControlType.COMMAND_BUTTON);
        cancelBtn.setName("cmdCancel");
        cancelBtn.setCaption("Cancel");
        cancelBtn.setLeft(190);   // Position it 90 points to the right of Submit.
        cancelBtn.setTop(150);
        cancelBtn.setWidth(80);
        cancelBtn.setHeight(30);
```

> *Подсказка:* Keep all button dimensions consistent for a professional look. A quick way is to store width/height in constants.

## Часто задаваемые вопросы и особые случаи

### «Можно ли установить размер кнопки в сантиметрах вместо пунктов?»

Word’s API only accepts points, but you can convert centimeters to points (`points = cm * 28.3465`). Write a small helper method if you prefer metric units.

### «Что если мне нужно, чтобы кнопка появлялась на определённой странице?»

After inserting the button, you can move the cursor to a particular page using `builder.moveToPage(pageNumber)`. Insert the control right after the move, then set its location as shown above.

### «Работает ли это с файлами .doc (Word 97‑2003)?»

Yes—Aspose.Words automatically handles older formats. Just change the file extension in `doc.save("Demo.doc")`.

## Полный, исполняемый пример

Below is the entire program you can copy‑paste into a Java class and run immediately (assuming the Aspose.Words JAR is on the classpath).

```java
import com.aspose.words.*;

public class InsertCommandButtonDemo {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Create a blank document.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Insert the first ActiveX CommandButton.
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMAND_BUTTON);
        commandButton.setName("cmdSubmit");
        commandButton.setCaption("Submit");

        // 3️⃣ Set button location and size – the core set button size logic.
        commandButton.setLeft(100);
        commandButton.setTop(150);
        commandButton.setWidth(80);
        commandButton.setHeight(30);

        // 4️⃣ (Optional) Add a second button for illustration.
        Forms2OleControl cancelBtn = builder.insertForms2OleControl(
                Forms2OleControlType.COMMAND_BUTTON);
        cancelBtn.setName("cmdCancel");
        cancelBtn.setCaption("Cancel");
        cancelBtn.setLeft(190);
        cancelBtn.setTop(150);
        cancelBtn.setWidth(80);
        cancelBtn.setHeight(30);

        // 5️⃣ Save the document – you’ve now created a Word document button.
        doc.save("CommandButtonDemo.docx");
    }
}
```

Run the program, open the generated `CommandButtonDemo.docx`, and you’ll see two neatly sized buttons ready for interaction.

## Заключение – Вы освоили установку размера кнопки в Word

We just walked through a complete, end‑to‑end solution for **set button size** and **set button location** using Aspose.Words for Java. By following the steps you can **insert activex button**, **programmatically add button** controls, and ultimately **create word document button** elements that behave exactly as you need.

What’s next? Try embedding the button inside a table cell, or attach a VBA macro that validates form fields before submission. The same pattern works for other ActiveX controls like check boxes or combo boxes—just swap `Forms2OleControlType.COMMAND_BUTTON` for the appropriate enum value.

If you hit any snags, drop a comment below. Happy coding, and enjoy the power of automated Word document creation!

## Что изучать дальше?

The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [Как установить LoadOptions в Aspose.Words для Java](/words/english/java/document-loading-and-saving/using-load-options/)
- [Как удалить нижние колонтитулы из документов Word с помощью Aspose.Words для Java](/words/english/java/document-manipulation/removing-content-from-documents/)
- [Aspose.Words Java&#58; Полное руководство по обработке документов Word](/words/english/java/document-operations/aspose-words-java-master-word-processing/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}