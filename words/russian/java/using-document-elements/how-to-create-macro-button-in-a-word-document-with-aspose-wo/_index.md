---
category: general
date: 2026-11-22
description: Создайте кнопку макроса в документе Word с помощью Java. Узнайте, как
  вставить кнопку команды, задать текст кнопки и привязать макрос к кнопке для интерактивных
  документов.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create macro button
- insert command button
- set button text
- link macro to button
- add interactive button
language: ru
lastmod: 2026-11-22
og_description: Создайте кнопку макроса в документе Word с помощью Java. Этот учебник
  показывает, как вставить кнопку команды, задать текст кнопки и связать макрос с
  кнопкой для полной интерактивности.
og_image_alt: Screenshot of a Word document showing a macro button created with Java
  code
og_title: Создайте кнопку макроса в документе Word с помощью Java – пошаговое руководство
schemas:
- author: Aspose
  dateModified: '2026-11-22'
  description: Create macro button in a Word document using Java. Learn to insert
    command button, set button text, and link macro to button for interactive documents.
  headline: How to create macro button in a Word document with Aspose.Words for Java
  type: TechArticle
- description: Create macro button in a Word document using Java. Learn to insert
    command button, set button text, and link macro to button for interactive documents.
  name: How to create macro button in a Word document with Aspose.Words for Java
  steps:
  - name: Insert command button into the document
    text: '`DocumentBuilder.insertForms2OleControl` creates an OLE control of the
      specified type. The `Forms2OleControlType.COMMAND_BUTTON` constant tells Aspose.Words
      to generate a command button that can host a macro.'
  - name: Set button text (caption)
    text: The caption is the visible label on the button. Use `setCaption` to define
      what the user sees.
  - name: Link macro to button
    text: A macro is identified by its name, for example `MyMacro`. The `setOnClick`
      method stores this name in the button’s `OnClick` event handler.
  - name: Add interactive button to a Word document
    text: After configuring the OLE control, you may want to position it, resize it,
      or add surrounding text. The `DocumentBuilder` continues to operate on the document,
      so you can insert paragraphs before or after the button.
  - name: Expected output
    text: 'Running the program generates `MacroButtonDemo.docm`. Opening the file
      in Microsoft Word shows:'
  type: HowTo
tags:
- Aspose.Words
- Java
- OLE controls
- Automation
title: Как создать кнопку макроса в документе Word с помощью Aspose.Words для Java
url: /ru/java/using-document-elements/how-to-create-macro-button-in-a-word-document-with-aspose-wo/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Как создать кнопку макроса в документе Word с помощью Aspose.Words для Java

Если вам нужно **создать кнопку макроса** в файле Word, это руководство проведет вас через все необходимые шаги. Вы узнаете, как **вставить кнопку команды**, **установить текст кнопки** и **привязать макрос к кнопке**, чтобы документ стал полностью интерактивным.

Разработчики часто встраивают OLE‑элементы управления для запуска VBA‑макросов из документа. Это руководство охватывает полный процесс, от настройки проекта до исполняемого примера на Java, который добавляет **интерактивную кнопку** в файл .docx. Внешние скрипты не требуются — всё выполняется внутри процесса Java.

## Необходимые условия

Перед началом убедитесь, что у вас есть:

* JDK 17 или новее установлен.
* Maven 3.8+ (или Gradle) для управления зависимостями.
* Aspose.Words for Java 23.9 или новее — библиотека предоставляет `DocumentBuilder` и API OLE‑контролей.
* Базовые знания Java и VBA‑макросов.

Если чего‑то не хватает, установите это в первую очередь; остальные части руководства предполагают, что они доступны.

## Как создать кнопку макроса с помощью Aspose.Words для Java

Суть решения состоит из четырёх действий:

1. **Вставить кнопку команды** OLE‑контрол в документ.
2. **Установить текст кнопки** (подпись), который видит пользователь.
3. **Привязать макрос к кнопке**, чтобы при нажатии выполнялась нужная VBA‑процедура.
4. **Сохранить документ** с внедрённым макросом.

Каждое действие подробно объясняется в отдельном разделе ниже.

### Шаг 1: Вставить кнопку команды в документ

`DocumentBuilder.insertForms2OleControl` создаёт OLE‑контрол указанного типа. Константа `Forms2OleControlType.COMMAND_BUTTON` указывает Aspose.Words сгенерировать кнопку команды, которая может содержать макрос.

```java
import com.aspose.words.*;

public class MacroButtonDemo {
    public static void main(String[] args) throws Exception {
        // Load a blank document or create a new one
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a command button OLE control
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMAND_BUTTON);
```

**Почему это важно:** OLE‑контрол служит контейнером для макроса. Если его не вставить, пользователь не увидит визуального элемента для клика.

### Шаг 2: Установить текст кнопки (подпись)

Подпись — это видимая метка на кнопке. Используйте `setCaption`, чтобы задать то, что видит пользователь.

```java
        // Set the button's caption – this is the text displayed on the button
        commandButton.setCaption("Run Report");
```

**Почему это важно:** Чёткий текст кнопки повышает удобство использования. Метод `setCaption` обновляет свойство `Caption` OLE‑контрола, которое Word отображает как подпись кнопки.

### Шаг 3: Привязать макрос к кнопке

Макрос идентифицируется по своему имени, например `MyMacro`. Метод `setOnClick` сохраняет это имя в обработчике события `OnClick` кнопки.

```java
        // Assign a macro to run when the button is clicked
        commandButton.setOnClick("MyMacro");
```

**Почему это важно:** Привязка макроса создаёт интерактивное поведение. Когда пользователь нажимает кнопку в Word, выполняется связанная VBA‑процедура.

### Шаг 4: Добавить интерактивную кнопку в документ Word

После настройки OLE‑контрола вы можете позиционировать его, менять размер или добавлять окружающий текст. `DocumentBuilder` продолжает работать с документом, поэтому можно вставлять абзацы до или после кнопки.

```java
        // Add a descriptive paragraph before the button
        builder.moveToDocumentStart();
        builder.writeln("Click the button below to generate the report:");

        // Move the cursor back to the button location (optional)
        builder.moveTo(commandButton.getNode());

        // Optionally, resize the button (width and height in points)
        commandButton.setWidth(120);
        commandButton.setHeight(30);

        // Save the document with the macro-enabled format
        doc.save("MacroButtonDemo.docm", SaveFormat.DOCM);
    }
}
```

**Почему это важно:** Сохранение в формате `.docm` сохраняет код макроса. При сохранении как `.docx` ссылка на макрос теряется.

## Полный исполняемый пример

Ниже приведена полная Java‑программа, включая импорты, обработку исключений и комментарии, объясняющие каждый шаг. Скопируйте код в Maven‑проект с зависимостью Aspose.Words и запустите его.

```java
// Maven dependency (add to pom.xml):
// <dependency>
//   <groupId>com.aspose</groupId>
//   <artifactId>aspose-words</artifactId>
//   <version>23.9</version>
// </dependency>

import com.aspose.words.*;

public class MacroButtonDemo {
    public static void main(String[] args) throws Exception {
        // 1. Create a new empty document
        Document doc = new Document();

        // 2. Initialize DocumentBuilder to edit the document
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 3. Write an introductory paragraph
        builder.writeln("Press the button to execute the macro:");

        // 4. Insert the command button OLE control
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMAND_BUTTON);

        // 5. Set the visual caption of the button
        commandButton.setCaption("Run Report");

        // 6. Link the button to a VBA macro named MyMacro
        commandButton.setOnClick("MyMacro");

        // 7. Resize the button for better appearance
        commandButton.setWidth(120);   // points
        commandButton.setHeight(30);   // points

        // 8. Save the document as a macro‑enabled file
        doc.save("MacroButtonDemo.docm", SaveFormat.DOCM);
    }
}
```

### Ожидаемый результат

Запуск программы создаёт `MacroButtonDemo.docm`. При открытии файла в Microsoft Word отображается:

* Абзац с текстом *«Press the button to execute the macro:»*.
* Кнопка с подписью **Run Report** сразу под абзацем.
* При нажатии на кнопку Word пытается выполнить макрос `MyMacro`. (Необходимо добавить реальный VBA‑код в документ вручную или с помощью другого шага автоматизации.)

Если макрос отсутствует, Word выводит предупреждение о безопасности — это стандартное поведение для документов с поддержкой макросов.

## Общие варианты и граничные случаи

| Сценарий | Как адаптировать код |
|----------|-----------------------|
| **Different button caption** | Измените строку, передаваемую в `setCaption`. |
| **Multiple buttons** | Вызывайте `insertForms2OleControl` многократно, для каждой задавая собственные `setCaption` и `setOnClick`. |
| **Custom macro names** | Замените `"MyMacro"` на любое допустимое имя VBA‑процедуры, например `"ExportToExcel"`. |
| **Button size constraints** | Отрегулируйте значения `setWidth` и `setHeight`; Word учитывает указанные точки. |
| **Embedding the macro programmatically** | Используйте `Document.getBuiltInDocumentProperties().add("Macros", …)` или отдельный шаг внедрения VBA; Aspose.Words сам не записывает VBA‑код. |

**Pro tip:** Всегда тестируйте сгенерированный `.docm` на машине, где безопасность макросов установлена в *Enable all macros* (разрешить все макросы) для разработки. В продакшене подпишите макрос доверенным сертификатом, чтобы избежать запросов безопасности.

## Список проверки при устранении неполадок

* **Кнопка не отображается** — Убедитесь, что документ сохранён как `.docm` и открыт в версии Word, поддерживающей OLE‑контролы.
* **Макрос не запускается** — Проверьте, что имя макроса точно совпадает, включая регистр, и что макрос существует в VBA‑проекте документа.
* **Подпись кнопки обрезана** — Увеличьте ширину кнопки с помощью `setWidth`, чтобы разместить более длинный текст.
* **Неожиданное смещение макета** — Используйте `builder.moveTo` для точного позиционирования курсора перед вставкой элемента.

## Заключение

Теперь вы знаете, как **создать кнопку макроса** в документе Word с помощью Java, **вставить кнопку команды**, **установить текст кнопки** и **привязать макрос к кнопке** для полной интерактивности. Полный пример демонстрирует каждый необходимый вызов API, объясняет, почему каждый шаг важен, и даёт рекомендации по распространённым вариантам.

Далее вы можете изучить:

* **Добавление интерактивной кнопки** в существующие шаблоны вместо создания нового документа.
* **Программное внедрение VBA‑кода** с использованием Open XML SDK или вторичного инструмента автоматизации.
* **Комбинирование нескольких OLE‑контролов** (чекбоксы, списковые поля) для создания сложных форм.

Экспериментируйте с различными подписями, именами макросов и размерами кнопок, чтобы подобрать оптимальное решение для вашего случая. Приятного кодинга!

## Что изучать дальше?

Следующие руководства охватывают тесно связанные темы, опираясь на техники, продемонстрированные в этом руководстве. Каждый ресурс включает полностью работающие примеры кода с пошаговыми объяснениями, помогая вам освоить дополнительные возможности API и исследовать альтернативные подходы к реализации в своих проектах.

- [Как вставить кнопку команды в документ Word с помощью Java](/words/english/java/using-document-elements/how-to-insert-command-button-in-a-word-document-using-java/)
- [Как установить позицию кнопки в документе Word с помощью Java](/words/english/java/using-document-elements/how-to-set-button-position-in-a-word-document-with-java/)
- [Как вставить кнопку ActiveX в Word – задать подпись кнопки](/words/english/java/using-document-elements/how-to-insert-activex-button-in-word-set-button-caption/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}