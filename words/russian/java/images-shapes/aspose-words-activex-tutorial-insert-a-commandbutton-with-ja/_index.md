---
category: general
date: 2026-08-07
description: Учебник Aspose.Words ActiveX показывает, как добавить элемент управления
  CommandButton в документ Word с помощью Java. Узнайте полный код, конфигурацию и
  шаги сохранения.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- aspose words activex tutorial
- aspose.words java
- activeX control java
- documentbuilder insert control
- forms2olecontrol usage
language: ru
lastmod: 2026-08-07
og_description: Учебник Aspose.Words ActiveX объясняет, как встроить элемент управления
  CommandButton ActiveX в документ Word с использованием Java. Следуйте полному примеру,
  чтобы создать, настроить и сохранить документ.
og_image_alt: Screenshot of a Word document with a CommandButton added via Aspose.Words
  ActiveX tutorial
og_title: Учебник Aspose.Words ActiveX – пошаговое руководство по Java
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: Aspose.Words ActiveX tutorial shows how to add a CommandButton control
    to a Word document using Java. Learn the full code, configuration, and saving
    steps.
  headline: Aspose.Words ActiveX tutorial – insert a CommandButton with Java
  type: TechArticle
- description: Aspose.Words ActiveX tutorial shows how to add a CommandButton control
    to a Word document using Java. Learn the full code, configuration, and saving
    steps.
  name: Aspose.Words ActiveX tutorial – insert a CommandButton with Java
  steps:
  - name: Initialize a `Document` and `DocumentBuilder`.
    text: Initialize a `Document` and `DocumentBuilder`.
  - name: Insert a `Forms2OleControl` of type `COMMAND_BUTTON`.
    text: Insert a `Forms2OleControl` of type `COMMAND_BUTTON`.
  - name: Set the button’s name, caption, size, and position.
    text: Set the button’s name, caption, size, and position.
  - name: Save the document as a .docx file that contains the ActiveX control.
    text: Save the document as a .docx file that contains the ActiveX control.
  type: HowTo
tags:
- Aspose.Words
- Java
- ActiveX
title: Учебник Aspose.Words ActiveX – вставка CommandButton с помощью Java
url: /ru/java/images-shapes/aspose-words-activex-tutorial-insert-a-commandbutton-with-ja/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words ActiveX tutorial – вставка CommandButton с Java

Если вам нужно встроить ActiveX‑элемент в файл Word, этот **Aspose.Words ActiveX tutorial** проведёт вас через весь процесс. Вы увидите, как создать пустой документ, вставить CommandButton, задать его свойства и сохранить результат — всё с помощью обычного кода Java.

Пример использует Aspose.Words for Java API, что исключает необходимость установки Microsoft Office на сервере сборки. К концу этого руководства вы сможете генерировать файлы .docx, содержащие полностью функциональные элементы CommandButton, готовые к использованию в Windows‑средах.

## Prerequisites

- Установлен Java Development Kit (JDK) 8 или новее.
- Maven или другой инструмент сборки для управления зависимостями.
- Лицензия Aspose.Words for Java (или временный оценочный ключ), чтобы избежать водяных знаков оценки.
- Базовое знакомство с синтаксисом Java и объектно‑ориентированным программированием.

> **Pro tip:** Добавьте зависимость Aspose.Words Maven в ваш `pom.xml`, чтобы IDE автоматически разрешала классы автоматически:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.10</version> <!-- Use the latest version -->
</dependency>
```

## Шаг 1: Создать новый пустой документ и `DocumentBuilder`

Класс `Document` представляет файл Word в памяти, а `DocumentBuilder` предоставляет fluent‑API для редактирования документа. Инициализация обоих объектов подготавливает документ к дальнейшим изменениям.

```java
import com.aspose.words.*;

public class ActiveXDemo {
    public static void main(String[] args) throws Exception {
        // Create an empty Word document
        Document document = new Document();

        // DocumentBuilder lets you add text, tables, and controls
        DocumentBuilder builder = new DocumentBuilder(document);
```

**Почему это важно:**  
`DocumentBuilder` отслеживает текущую позицию курсора, поэтому любая последующая операция вставки — например, добавление элемента управления — появляется точно там, где вы задумали.

## Шаг 2: Insert a CommandButton ActiveX control

Aspose.Words раскрывает `Forms2OleControl` для ActiveX‑объектов. Метод `insertForms2OleControl` требует указать тип элемента управления, который задаётся через перечисление `Forms2OleControlType`.

```java
        // Insert a CommandButton ActiveX control at the current cursor location
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMAND_BUTTON);
```

**Объяснение:**  
Вставленный элемент — объект на основе COM, который Word отобразит как кликабельную кнопку при открытии документа в Windows‑среде.

## Шаг 3: Configure the button’s properties

После вставки вы можете настроить имя, подпись, размер и позицию кнопки. Эти свойства влияют на внешний вид и поведение элемента внутри Word.

```java
        // Set the logical name used by VBA or external scripts
        commandButton.setName("cmdSubmit");

        // Text displayed on the button face
        commandButton.setCaption("Submit");

        // Position the button 100 points from the left margin and 150 points from the top
        commandButton.setLeft(100);
        commandButton.setTop(150);

        // Define the button’s dimensions (width × height) in points
        commandButton.setWidth(80);
        commandButton.setHeight(30);
```

**Почему эти настройки важны:**  

- **Name** – Позволяет VBA‑макросам ссылаться на элемент (`ActiveDocument.Forms("cmdSubmit")`).
- **Caption** – Определяет видимую надпись, по которой кликают пользователи.
- **Left / Top** – Управляет размещением относительно полей страницы.
- **Width / Height** – Обеспечивает одинаковый визуальный размер на разных разрешениях экрана.

## Шаг 4: Save the document

Вызов `save` записывает представление в памяти в физический файл. Вы можете выбрать любой поддерживаемый формат (`.docx`, `.doc`, `.pdf` и т.д.). Для этого руководства мы сохраняем в нативном формате Word.

```java
        // Persist the document with the embedded ActiveX control
        document.save("output/ActiveXDemo.docx");
    }
}
```

**Результат:**  
Открытие `ActiveXDemo.docx` в Microsoft Word отображает кнопку CommandButton с подписью **Submit**, расположенную в указанных координатах. Нажатие кнопки вызывает поведение по умолчанию (по умолчанию VBA‑кода нет).

## Full source code

Объединив все части, получаем полностью рабочую программу:

```java
import com.aspose.words.*;
import com.aspose.words.forms.*;

public class ActiveXDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document and a DocumentBuilder
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Step 2: Insert a CommandButton ActiveX control
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMAND_BUTTON);

        // Step 3: Configure the button's properties
        commandButton.setName("cmdSubmit");
        commandButton.setCaption("Submit");
        commandButton.setLeft(100);
        commandButton.setTop(150);
        commandButton.setWidth(80);
        commandButton.setHeight(30);

        // Step 4: Save the document with the ActiveX control
        document.save("output/ActiveXDemo.docx");
    }
}
```

### Ожидаемый результат

- Файл с именем **ActiveXDemo.docx**, расположенный в папке `output`.
- При открытии в Microsoft Word (Windows) документ отображает кликабельную кнопку **Submit** в заданном положении.
- Кнопку можно выделять, перемещать или привязывать к VBA‑коду через пользовательский интерфейс Word (Developer → Properties).

## Handling common variations

| Сценарий | Корректировка |
|----------|----------------|
| **Сохранить как .doc** (устаревший формат) | `document.save("ActiveXDemo.doc", SaveFormat.DOC);` |
| **Добавить обработчик события** | Word не предоставляет события ActiveX через Aspose.Words. Вам необходимо добавить VBA‑код вручную после генерации документа. |
| **Несколько элементов управления** | Повторите блок вставки/настройки с разными значениями `setName` и `setCaption`. |
| **Другой тип элемента управления (например, CheckBox)** | Используйте `Forms2OleControlType.CHECKBOX` в вызове `insertForms2OleControl`. |
| **Платформы, отличные от Windows** | Элементы ActiveX отображаются только в Word для Windows. Для кросс‑платформенных решений рассмотрите элементы управления содержимым (`StructuredDocumentTag`). |

## Best practices and pitfalls

- **License early** – Зарегистрируйте лицензию Aspose.Words до создания `Document`, чтобы избежать запросов оценки.
- **Coordinate system** – Позиции измеряются в пунктах (1 pt = 1/72 in). При необходимости преобразуйте из пикселей или сантиметров, если ваш дизайн UI использует эти единицы.
- **File paths** – Используйте абсолютные пути или API Java `Paths`, чтобы избежать `FileNotFoundException`, если каталог вывода не существует.
- **Thread safety** – `Document` и `DocumentBuilder` не являются потокобезопасными. Создавайте отдельные экземпляры для каждого потока, если генерируете документы параллельно.
- **Testing** – Проверьте сгенерированный документ в целевой версии Word (например, Word 2016, Word 365), так как старые версии могут отображать элементы ActiveX иначе.

## Conclusion

Этот **Aspose.Words ActiveX tutorial** демонстрирует, как программно добавить элемент CommandButton в документ Word с помощью Java. Вы научились:

1. Инициализировать `Document` и `DocumentBuilder`.
2. Вставить `Forms2OleControl` типа `COMMAND_BUTTON`.
3. Задать имя, подпись, размер и позицию кнопки.
4. Сохранить документ как файл .docx, содержащий элемент ActiveX.

Далее вы можете исследовать дополнительные типы элементов управления, автоматизировать внедрение VBA‑макросов или комбинировать ActiveX‑элементы с другими возможностями Aspose.Words, такими как слияние писем и элементы управления содержимым. Экспериментируйте с разными макетами и интегрируйте сгенерированные документы в ваш более крупный Java‑ориентированный конвейер отчетности.

---


## What Should You Learn Next?

Следующие руководства охватывают тесно связанные темы, которые расширяют техники, продемонстрированные в этом руководстве. Каждый ресурс включает полностью работающие примеры кода с пошаговыми объяснениями, чтобы помочь вам освоить дополнительные возможности API и исследовать альтернативные подходы в ваших проектах.

- [Использование OLE‑объектов и ActiveX‑элементов в Aspose.Words for Java](/words/english/java/using-document-elements/using-ole-objects-and-activex/)
- [Как создавать поля формы и добавлять контент с помощью DocumentBuilder в Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Конвертация Word в RTF с помощью Aspose.Words for Java Tutorial](/words/english/java/document-loading-and-saving/saving-documents-as-rtf-format/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}