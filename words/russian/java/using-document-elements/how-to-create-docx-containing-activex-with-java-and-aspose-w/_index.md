---
category: general
date: 2026-09-27
description: Создайте документ docx с элементами ActiveX на Java с использованием
  Aspose.Words. Узнайте, как пошагово вставить кнопку командного ActiveX.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create docx containing activex
- insert activex command button
- Aspose.Words Java
- ActiveX control in Word
- generate Word document programmatically
language: ru
lastmod: 2026-09-27
og_description: Создайте docx, содержащий ActiveX, на Java с помощью Aspose.Words.
  Следуйте этому руководству, чтобы вставить кнопку ActiveX и сохранить документ.
og_image_alt: Screenshot of a Word document that contains an ActiveX command button
og_title: Создайте docx, содержащий ActiveX в Java — полное руководство
schemas:
- author: Aspose
  dateModified: '2026-09-27'
  description: Create docx containing ActiveX in Java using Aspose.Words. Learn to
    insert an ActiveX command button step‑by‑step.
  headline: How to create docx containing ActiveX with Java and Aspose.Words
  type: TechArticle
- description: Create docx containing ActiveX in Java using Aspose.Words. Learn to
    insert an ActiveX command button step‑by‑step.
  name: How to create docx containing ActiveX with Java and Aspose.Words
  steps:
  - name: The document should show a single page with a button labeled **Click Me**
      positioned near the top‑left corner.
    text: The document should show a single page with a button labeled **Click Me**
      positioned near the top‑left corner.
  - name: If the button does not appear, check that **ActiveX controls are enabled**
      in Word’s Trust Center (File → Options → Trust Center → Trust Center Settings
      → ActiveX Settings).
    text: If the button does not appear, check that **ActiveX controls are enabled**
      in Word’s Trust Center (File → Options → Trust Center → Trust Center Settings
      → ActiveX Settings).
  - name: The button is functional only on Windows versions of Word that support ActiveX.
      On macOS or web‑based Word, the control will be displayed as a static image.
    text: The button is functional only on Windows versions of Word that support ActiveX.
      On macOS or web‑based Word, the control will be displayed as a static image.
  type: HowTo
tags:
- docx
- activex
- java
- aspose-words
title: Как создать docx, содержащий ActiveX, с помощью Java и Aspose.Words
url: /ru/java/using-document-elements/how-to-create-docx-containing-activex-with-java-and-aspose-w/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Как создать docx, содержащий ActiveX, с помощью Java и Aspose.Words

Если вам нужно **создать docx, содержащий ActiveX**, это руководство покажет полное решение. Вы узнаете, как **вставить кнопку командного управления ActiveX** в файл Word с помощью Aspose.Words for Java, а затем сохранить результат как .docx, который можно открыть в Microsoft Word.

Программное создание документа Word избавляет от ручного редактирования и гарантирует согласованность отчётов, контрактов или шаблонов форм. Ниже приведённые шаги охватывают всё — от настройки проекта до обработки типичных подводных камней, чтобы вы могли интегрировать эту технику в любое Java‑приложение.

## Предварительные требования

* Java Development Kit (JDK) 8 или новее установлен.
* Maven 3.6+ (или другой предпочитаемый инструмент сборки).
* Файл лицензии Aspose.Words for Java (бесплатная оценочная версия подходит для тестирования).
* Microsoft Word, установленный на целевой машине, если вы хотите визуально проверить элемент управления ActiveX.

Эти элементы необходимы, потому что Aspose.Words предоставляет API, создающее документ, а Word нужен для отображения элемента управления ActiveX.

## Шаг 1: Настройка Maven‑проекта

Создайте новый Maven‑проект или добавьте зависимость Aspose.Words в существующий `pom.xml`:

```xml
<project>
    <modelVersion>4.0.0</modelVersion>
    <groupId>com.example</groupId>
    <artifactId>activex-docx-demo</artifactId>
    <version>1.0.0</version>
    <properties>
        <maven.compiler.source>1.8</maven.compiler.source>
        <maven.compiler.target>1.8</maven.compiler.target>
    </properties>

    <dependencies>
        <!-- Aspose.Words for Java -->
        <dependency>
            <groupId>com.aspose</groupId>
            <artifactId>aspose-words</artifactId>
            <version>24.10</version> <!-- use the latest stable version -->
        </dependency>
    </dependencies>
</project>
```

> **Pro tip:** Синхронизируйте версию Aspose.Words с официальными примечаниями к выпуску, чтобы получать исправления ошибок и новые возможности ActiveX.

## Шаг 2: Написать Java‑код, создающий документ

Создайте класс с именем `ActiveXDocxCreator`. Приведённый ниже код включает все необходимые импорты, метод `main` и подробные комментарии, объясняющие каждую операцию.

```java
package com.example.activex;

import com.aspose.words.*;
import java.io.File;

/**
 * Demonstrates how to create a DOCX file that contains an ActiveX command button.
 * The resulting file can be opened in Microsoft Word where the button appears
 * on the first page.
 */
public class ActiveXDocxCreator {

    public static void main(String[] args) {
        // 1. Initialize a new empty document and a DocumentBuilder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2. Insert an ActiveX Forms2OleControl at the current cursor position.
        Forms2OleControl commandButton = builder.insertForms2OleControl();

        // 3. Configure the control to be a CommandButton and set its caption.
        commandButton.setControlType(Forms2OleControlType.COMMANDBUTTON);
        commandButton.setCaption("Click Me");

        // 4. Position the button on the page.
        //    The coordinates are measured in points (1 point = 1/72 inch).
        commandButton.setLeft(100); // 100 points from the left margin
        commandButton.setTop(150);  // 150 points from the top margin

        // 5. (Optional) Set the size of the button for better visibility.
        commandButton.setWidth(120);
        commandButton.setHeight(30);

        // 6. Save the document to the desired location.
        String outputPath = "output/ActiveXCommandButton.docx";
        try {
            // Ensure the output directory exists.
            new File("output").mkdirs();
            doc.save(outputPath);
            System.out.println("Document saved successfully to " + outputPath);
        } catch (Exception e) {
            System.err.println("Error while saving the document: " + e.getMessage());
        }
    }
}
```

### Почему каждая строка важна

* `Document` — контейнер для всего содержимого Word. Создание нового экземпляра даёт чистый холст.
* `DocumentBuilder` предоставляет удобный API для вставки элементов; он автоматически отслеживает текущую позицию вставки.
* `insertForms2OleControl()` создаёт универсальный заполнитель OLE‑контрола. Aspose.Words рассматривает его как контейнер ActiveX.
* `setControlType(Forms2OleControlType.COMMANDBUTTON)` указывает Word, что заполнитель должен отображаться как CommandButton.
* `setCaption("Click Me")` задаёт текст, отображаемый на кнопке.
* `setLeft` и `setTop` размещают кнопку относительно полей страницы. Отрегулируйте эти значения под ваш макет.
* `setWidth` и `setHeight` необязательны, но улучшают внешний вид кнопки, особенно когда размер по умолчанию слишком мал.
* `doc.save` записывает структуру из памяти в физический файл .docx, который может открыть Word.

## Шаг 3: Проверка сгенерированного документа

Откройте `output/ActiveXCommandButton.docx` в Microsoft Word:

1. Документ должен отображать одну страницу с кнопкой, помеченной **Click Me**, расположенной в верхнем‑левом углу.
2. Если кнопка не появляется, проверьте, что **ActiveX controls are enabled** в Центре управления безопасностью Word (File → Options → Trust Center → Trust Center Settings → ActiveX Settings).
3. Кнопка работает только в версиях Word для Windows, поддерживающих ActiveX. В macOS или веб‑версии Word элемент будет отображён как статическое изображение.

## Шаг 4: Обработка распространённых граничных случаев

| Situation | Reason | Recommended action |
|-----------|--------|--------------------|
| The button is missing after opening the file | Word’s security settings block ActiveX | Enable “Run all controls without restrictions” for trusted locations. |
| The generated .docx cannot be opened | Incompatible Aspose.Words version | Upgrade to the latest Aspose.Words release; older versions may not embed the required OLE parts correctly. |
| You need the button to execute a macro | ActiveX alone does not contain macro code | Combine the ActiveX control with a VBA macro that handles the `Click` event. Use the `DocumentBuilder.insertOleObject` method to embed a macro‑enabled template. |
| The layout is off on different page sizes | Coordinates are absolute points | Use `builder.getPageSetup().setPageWidth` and `setPageHeight` to standardize the page size before positioning the control. |

## Шаг 5: Расширение решения

Вы можете вставлять другие элементы управления ActiveX, изменив перечисление `ControlType`:

```java
commandButton.setControlType(Forms2OleControlType.CHECKBOX); // inserts a checkbox
```

Aspose.Words также поддерживает вставку **ActiveX text boxes**, **list boxes** и **combo boxes**. Те же методы позиционирования (`setLeft`, `setTop`, `setWidth`, `setHeight`) применимы.

Если необходимо разместить несколько элементов управления, вызывайте `builder.insertForms2OleControl()` последовательно и корректируйте координаты каждого контрола соответственно.

## Полный исходный файл

Ниже представлен весь файл `ActiveXDocxCreator.java`, готовый для копирования и вставки:

```java
package com.example.activex;

import com.aspose.words.*;
import java.io.File;

public class ActiveXDocxCreator {
    public static void main(String[] args) {
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        Forms2OleControl commandButton = builder.insertForms2OleControl();
        commandButton.setControlType(Forms2OleControlType.COMMANDBUTTON);
        commandButton.setCaption("Click Me");
        commandButton.setLeft(100);
        commandButton.setTop(150);
        commandButton.setWidth(120);
        commandButton.setHeight(30);

        String outputPath = "output/ActiveXCommandButton.docx";
        try {
            new File("output").mkdirs();
            doc.save(outputPath);
            System.out.println("Document saved successfully to " + outputPath);
        } catch (Exception e) {
            System.err.println("Error while saving the document: " + e.getMessage());
        }
    }
}
```

Запуск этой программы создаёт **docx, содержащий ActiveX**, который вы можете распространять среди конечных пользователей, нуждающихся в интерактивных формах.

## Заключение

Теперь вы знаете, как **создать docx, содержащий ActiveX**, используя Java и Aspose.Words, и как **программно вставить кнопку командного управления ActiveX**. В руководстве рассмотрены настройка проекта, полный исходный код, шаги проверки и стратегии решения типичных проблем.

Отсюда вы можете изучить:

* Добавление VBA‑макросов для обработки нажатия кнопки.
* Встраивание других элементов управления ActiveX, таких как флажки или комбобоксы.
* Автоматизацию генерации многостраничных форм с динамическими данными.

Экспериментируйте с различными координатами, размерами и типами контролов, чтобы они соответствовали вашему конкретному макету документа. Приятного кодирования!

## Что изучать дальше?

Следующие руководства охватывают тесно связанные темы, построенные на техниках, продемонстрированных в этом руководстве. Каждый ресурс включает полностью работающие примеры кода с пошаговыми объяснениями, помогающими освоить дополнительные возможности API и исследовать альтернативные подходы к реализации в ваших проектах.

- [Using OLE Objects and ActiveX Controls in Aspose.Words for Java](/words/english/java/using-document-elements/using-ole-objects-and-activex/)
- [How to create form fields and add content using DocumentBuilder in Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Create rectangle shape in Word with Aspose.Words – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}