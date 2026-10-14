---
category: general
date: 2026-10-13
description: Создайте кнопку поля формы в Word, используя Aspose.Words для Java. Узнайте,
  как вставить кнопку‑команду в поля формы Word и задать её подпись за несколько простых
  шагов.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create form field button
- insert command button word
- set command button caption
language: ru
lastmod: 2026-10-13
og_description: Создайте кнопку поля формы в Word с помощью Aspose.Words для Java.
  Этот учебник показывает, как быстро вставить поля командных кнопок Word и задать
  подпись кнопки.
og_image_alt: Screenshot of a Word document containing an inserted command button
  form field created with Aspose.Words Java
og_title: Создание кнопки поля формы в Word – руководство Aspose.Words Java
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Create form field button in Word using Aspose.Words for Java. Learn
    how to insert command button word form fields and set command button caption in
    a few easy steps.
  headline: Create form field button in Word with Aspose.Words Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word automation
title: Создать кнопку поля формы в Word с помощью Aspose.Words Java
url: /ru/java/using-document-elements/create-form-field-button-in-word-with-aspose-words-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Создание кнопки поля формы в Word с Aspose.Words для Java

Если вам нужно **create form field button** в документе Word, это руководство проведет вас через весь процесс с использованием Aspose.Words for Java. Независимо от того, создаете ли вы шаблон формы для заполнения или добавляете интерактивные элементы управления в отчет, вы узнаете, как **insert command button word** form fields и **set command button caption** с минимальным количеством кода.

В этом руководстве рассматривается всё — от настройки Maven до полностью исполняемого примера, так что вы можете скопировать‑вставить код, запустить его и увидеть файл `.docx`, содержащий кликабельную кнопку, готовую к дальнейшей настройке.

## Предварительные требования

- Java 17 (или новее), установленный и настроенный на вашем компьютере.
- Maven 3.6+ для управления зависимостями.
- IDE или текстовый редактор по вашему выбору (например, IntelliJ IDEA, VS Code).
- Действительная лицензия Aspose.Words for Java (бесплатная пробная версия подходит для оценки).

## Шаг 1: Добавьте Aspose.Words в ваш Maven‑проект

Создайте `pom.xml` (или отредактируйте существующий) и включите зависимость Aspose.Words:

```xml
<dependencies>
    <dependency>
        <groupId>com.aspose</groupId>
        <artifactId>aspose-words</artifactId>
        <version>24.9</version> <!-- Use the latest version available -->
    </dependency>
</dependencies>
```

> **Совет:** Держите номер версии актуальным. Новые релизы добавляют поддержку последних функций Word и повышают производительность.

## Шаг 2: Инициализируйте пустой документ и `DocumentBuilder`

Класс `DocumentBuilder` предоставляет удобный API для редактирования документа Word. На этом шаге мы создаём пустой `Document` и привязываем к нему builder.

```java
import com.aspose.words.*;

public class InsertCommandButtonDemo {
    public static void main(String[] args) throws Exception {
        // Create a new blank document
        Document doc = new Document();

        // DocumentBuilder lets us add content programmatically
        DocumentBuilder builder = new DocumentBuilder(doc);
```

Создание документа является основой для **create form field button** объектов, которые будут использоваться позже в руководстве.

## Шаг 3: Вставьте поле формы командной кнопки

Aspose.Words предоставляет класс `Forms2OleControl` для OLE‑элементов управления формой. Чтобы **insert command button word** form fields, вызовите `insertForms2OleControl` с значением перечисления `COMMANDBUTTON`.

```java
        // Insert a Command Button form field at the current cursor position
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON);
```

Метод возвращает экземпляр `Forms2OleControl`, который мы можем настроить перед сохранением.

## Шаг 4: Определите размер и позицию кнопки

Командной кнопке требуются явные размеры и размещение на странице. Настройте ширину, высоту и координаты в соответствии с вашим макетом.

```java
        // Set the button's visual size (in points)
        commandButton.setWidth(120);   // 120 points ≈ 1.67 inches
        commandButton.setHeight(30);   // 30 points ≈ 0.42 inches

        // Position the button relative to the page margins
        commandButton.setLeft(50);   // 50 points from the left margin
        commandButton.setTop(100);   // 100 points from the top margin
```

Точная настройка этих значений гарантирует, что кнопка появится точно там, где вы хотите, в окончательном документе.

## Шаг 5: **Set command button caption**

Отображаемый текст на кнопке управляется методом `setCaption`. Здесь мы **set command button caption**, чтобы направить пользователя.

```java
        // Define the text that appears on the button
        commandButton.setCaption("Click Me");
```

Вы можете заменить `"Click Me"` на любой ярлык, соответствующий назначению вашей формы, например `"Submit"` или `"Approve"`.

## Шаг 6: Сохраните документ

Наконец, запишите документ на диск. Полученный файл содержит интерактивную кнопку и может быть открыт в Microsoft Word или LibreOffice.

```java
        // Save the document with the embedded command button
        doc.save("CommandButtonDemo.docx");
    }
}
```

Запуск программы создаёт `CommandButtonDemo.docx`. Открывая его в Word, вы увидите кнопку с надписью **Click Me**, расположенную на 50 pt от левого края и 100 pt от верхнего края страницы.

### Ожидаемый результат

- Файл `.docx` с именем `CommandButtonDemo.docx`.
- Документ содержит одну страницу с полем формы командной кнопки.
- Кнопка отображает установленную вами подпись (например, **Click Me**).

## Распространённые варианты и крайние случаи

| Ситуация | Как адаптировать |
|-----------|--------------|
| **Multiple buttons** | Вызовите `insertForms2OleControl` несколько раз, корректируя `setLeft`/`setTop` для каждой новой кнопки. |
| **Different caption per button** | Используйте `setCaption` с уникальной строкой после каждой вставки. |
| **Button inside a table cell** | Переместите курсор в нужную ячейку с помощью `builder.moveTo(cell.getFirstParagraph())` перед вставкой элемента управления. |
| **Legacy Word formats (.doc)** | Сохраните с помощью `doc.save("Demo.doc", SaveFormat.DOC);` — командная кнопка сохраняется. |
| **Read‑only forms** | После вставки установите `commandButton.setEnabled(false);`, чтобы предотвратить взаимодействие пользователя. |

## Советы для надёжной реализации

- **Validate dimensions**: Чрезмерно большие ширины могут привести к выходу кнопки за пределы полей страницы.
- **License enforcement**: Без действительной лицензии Aspose.Words добавляет водяной знак в сгенерированный документ. Примените лицензию заранее с помощью `License license = new License(); license.setLicense("Aspose.Words.lic");`.
- **Testing**: Откройте сгенерированный файл в Word и переключите **Design Mode** (Developer → Design Mode), чтобы увидеть свойства кнопки.

## Полный обзор исходного кода

```java
import com.aspose.words.*;

public class InsertCommandButtonDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document and a builder to edit it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Insert a Command Button form field
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON);

        // Step 3: Define the button's size and position on the page
        commandButton.setWidth(120);
        commandButton.setHeight(30);
        commandButton.setLeft(50);
        commandButton.setTop(100);

        // Step 4: Set the text that appears on the button
        commandButton.setCaption("Click Me");

        // Step 5: Save the document with the embedded command button
        doc.save("CommandButtonDemo.docx");
    }
}
```

Скопируйте код в файл с именем `InsertCommandButtonDemo.java`, скомпилируйте с помощью Maven (`mvn compile`) и запустите (`mvn exec:java -Dexec.mainClass=InsertCommandButtonDemo`). Сгенерированный документ появится в корневой папке вашего проекта.

## Заключение

Теперь вы знаете, как **create form field button** в Word с помощью Aspose.Words for Java, как **insert command button word** form fields и как программно **set command button caption**. Этот сквозной пример даёт прочную основу для создания более сложных интерактивных документов Word — независимо от того, нужна ли вам одна кнопка отправки или полный набор элементов управления формой.

### Что дальше?

- [Как создавать поля формы и добавлять контент с помощью DocumentBuilder в Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Добавить поле формы выпадающего списка в документ Word с Aspose.Words for .NET](/words/english/net/add-content-using-documentbuilder/insert-combo-box/)
- [Добавить поле формы флажка в документ Word с Aspose.Words for .NET](/words/english/net/add-content-using-documentbuilder/insert-check-box/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}