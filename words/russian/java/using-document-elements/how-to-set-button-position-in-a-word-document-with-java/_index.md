---
category: general
date: 2026-09-24
description: Установите позицию кнопки в документе Word с помощью Java и Aspose.Words.
  Узнайте, как вставить кнопку, добавить ActiveX‑элемент и создать документ Word в
  стиле Java.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- set button position
- how to insert button
- add activex control
- add button to word
- create word document java
language: ru
lastmod: 2026-09-24
og_description: Установите позицию кнопки в документе Word с помощью Java. В этом
  руководстве показано, как вставить кнопку, добавить элемент управления ActiveX и
  создать документ Word на Java с использованием Aspose.Words.
og_image_alt: Screenshot of a Word document showing a CommandButton positioned at
  100 px left and 150 px top
og_title: Установка положения кнопки в документе Word с помощью Java – полное руководство
schemas:
- author: Aspose
  dateModified: '2026-09-24'
  description: Set button position in a Word document using Java and Aspose.Words.
    Learn how to insert button, add ActiveX control, and create Word document Java
    style.
  headline: How to set button position in a Word document with Java
  type: TechArticle
- description: Set button position in a Word document using Java and Aspose.Words.
    Learn how to insert button, add ActiveX control, and create Word document Java
    style.
  name: How to set button position in a Word document with Java
  steps:
  - name: Expected output
    text: '* A `.docx` file named **CommandButtonDemo.docx**. * Inside the document,
      a **CommandButton** labeled “Click Me” appears 100 px from the left margin and
      150 px from the top margin. * The button responds to clicks when the document
      is opened in Word (it will display a default ActiveX message unless y'
  - name: Adding multiple buttons
    text: If you need to **add button to Word** more than once, repeat steps 3‑5 with
      a new `Forms2OleControl` instance each time. Remember to adjust the `setTop`
      value so buttons don’t overlap.
  - name: Working without a license
    text: 'Aspose.Words adds a watermark when used without a license. For production
      code, purchase a license and apply it at the start of `main`:'
  - name: Compatibility with older Office versions
    text: 'ActiveX controls are supported in the `.doc` (Word 97‑2003) format. To
      create a legacy file, change the save format:'
  - name: Next steps
    text: '* Explore other `Forms2OleControl.ControlType` values (e.g., `CHECKBOX`,
      `TEXTBOX`) to build richer forms. * Combine the button with VBA macros for custom
      click handling. * Use Aspose.Words’ mail‑merge feature to generate personalized
      documents that already contain interactive controls.'
  type: HowTo
- questions:
  - answer: Yes. Aspose.Words is pure Java and runs on any JDK 8+ implementation,
      including OpenJDK.
    question: Does this work with OpenJDK?
  - answer: ActiveX button appearance is controlled by the host application (Word).
      You can attach VBA code to modify properties at runtime, but the static appearance
      is limited to the default style.
    question: Can I change the button’s font or color?
  - answer: 'Move the `DocumentBuilder` cursor into the cell before calling `insertForms2OleControl`.
      The control will inherit the cell’s layout, and you can still use `setLeft`/`setTop`
      for fine‑tuning. ## Conclusion You now know how to **set button position** in
      a Word document using Java, how to **how to inse'
    question: What if I need to place the button inside a table cell?
  type: FAQPage
tags:
- Aspose.Words
- Java
- ActiveX
- Word automation
- CommandButton
title: Как задать позицию кнопки в документе Word с помощью Java
url: /ru/java/using-document-elements/how-to-set-button-position-in-a-word-document-with-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Как установить позицию кнопки в документе Word с помощью Java

Если вам нужно **установить позицию кнопки** внутри файла Word, это руководство покажет вам полное, исполняемое решение. Независимо от того, создаёте ли вы шаблон, требующий взаимодействия с пользователем, или автоматизируете форму, вы узнаете точно **как вставить кнопку** с помощью Aspose.Words for Java и управлять её размещением.

В этом руководстве рассматривается всё, что вам нужно для **добавления ActiveX‑контроля** в документ Word, объясняется, как **добавить кнопку в Word**, и демонстрируется полный процесс **создания Word‑документа Java**. Внешние ссылки не требуются — просто скопируйте, запустите и проверьте результат.

## Требования

* Java 17 (или любой runtime Java 8+) установлен.  
* Maven или Gradle для управления зависимостями.  
* Лицензия Aspose.Words for Java (бесплатная пробная версия подходит для оценки).  
* Базовое понимание синтаксиса Java.  

> **Совет:** Храните JAR‑файлы Aspose.Words в папке `libs/` и добавляйте их в classpath вашего проекта, чтобы избежать конфликтов версий.

## Шаг 1: Настройка Maven‑проекта

Создайте простой Maven‑проект (или используйте Gradle) и добавьте зависимость Aspose.Words:

```xml
<!-- pom.xml -->
<project>
    <modelVersion>4.0.0</modelVersion>
    <groupId>com.example</groupId>
    <artifactId>word-button-demo</artifactId>
    <version>1.0.0</version>
    <dependencies>
        <dependency>
            <groupId>com.aspose</groupId>
            <artifactId>aspose-words</artifactId>
            <version>24.9</version> <!-- latest at time of writing -->
        </dependency>
    </dependencies>
</project>
```

Выполнение `mvn clean compile` загружает библиотеку и подготавливает путь сборки.

## Шаг 2: Создание нового Word‑документа

Первая операция — **создать Word‑документ java**. Вы создаёте объект `Document` и `DocumentBuilder`, который позволяет редактировать файл.

```java
import com.aspose.words.*;

public class CommandButtonDemo {
    public static void main(String[] args) throws Exception {
        // Initialize a blank document
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

Класс `Document` представляет весь файл .docx, а `DocumentBuilder` предоставляет удобный API для вставки содержимого.

## Шаг 3: Как вставить кнопку — добавить ActiveX‑контроль

Aspose.Words предоставляет класс `Forms2OleControl` для вставки устаревших ActiveX‑контролей, таких как CommandButton. Этот шаг показывает точный способ **как вставить кнопку** в документ.

```java
        // Insert a CommandButton ActiveX control
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControl.ControlType.COMMANDBUTTON);
```

Метод `insertForms2OleControl` возвращает экземпляр `Forms2OleControl`, который можно настроить. Это ядро процесса **добавления ActiveX‑контроля**.

## Шаг 4: Установка позиции кнопки

Теперь мы действительно **устанавливаем позицию кнопки**. Методы `setLeft` и `setTop` у контроля принимают значения в пунктах (1 pt = 1/72 in). Чтобы согласовать кнопку с типичными координатами экрана, можно преобразовать пиксели в пункты (1 px ≈ 0.75 pt). В примере мы размещаем кнопку на расстоянии 100 px от левого края и 150 px от верхнего края.

```java
        // Position the button on the page
        commandButton.setLeft(100 * 0.75);   // 75 pt ≈ 100 px
        commandButton.setTop(150 * 0.75);    // 112.5 pt ≈ 150 px
```

Поскольку логика **установки позиции кнопки** инкапсулирована здесь, вы можете переиспользовать эти строки каждый раз, когда нужно переместить контроль. Отрегулируйте числа под требования вашего макета.

## Шаг 5: Определение размера и подписи

Кнопка без подписи сбивает с толку. Используйте `setWidth`, `setHeight` и `setCaption`, чтобы придать ей видимый вид.

```java
        // Define size and caption
        commandButton.setWidth(120 * 0.75);   // 90 pt width
        commandButton.setHeight(30 * 0.75);   // 22.5 pt height
        commandButton.setCaption("Click Me");
```

Размер также задаётся в пунктах, поэтому мы конвертируем из пикселей для согласованности.

## Шаг 6: Сохранение документа — завершение процесса **create Word document java**

Наконец, сохраняем файл на диск. Путь может быть абсолютным или относительным к корню проекта.

```java
        // Save the document containing the CommandButton
        doc.save("output/CommandButtonDemo.docx");
    }
}
```

Запуск программы создаёт `CommandButtonDemo.docx` в папке `output`. Открытие файла в Microsoft Word показывает кликабельную кнопку, расположенную точно там, где вы её задали.

### Ожидаемый результат

* Файл `.docx` с именем **CommandButtonDemo.docx**.  
* Внутри документа появляется **CommandButton** с подписью «Click Me», расположенный на 100 px от левого поля и 150 px от верхнего поля.  
* Кнопка реагирует на клики при открытии документа в Word (будет отображать стандартное сообщение ActiveX, если не добавить пользовательский VBA‑код).

## Шаг 7: Общие варианты и граничные случаи

### Добавление нескольких кнопок

Если вам нужно **добавить кнопку в Word** более одного раза, повторите шаги 3‑5 с новым экземпляром `Forms2OleControl` каждый раз. Не забудьте скорректировать значение `setTop`, чтобы кнопки не перекрывались.

```java
        Forms2OleControl secondButton = builder.insertForms2OleControl(
                Forms2OleControl.ControlType.COMMANDBUTTON);
        secondButton.setLeft(200 * 0.75);
        secondButton.setTop(250 * 0.75);
        secondButton.setWidth(120 * 0.75);
        secondButton.setHeight(30 * 0.75);
        secondButton.setCaption("Second");
```

### Работа без лицензии

Aspose.Words добавляет водяной знак при использовании без лицензии. Для продакшн‑кода приобретите лицензию и примените её в начале `main`:

```java
        License license = new License();
        license.setLicense("Aspose.Words.lic");
```

### Совместимость со старыми версиями Office

ActiveX‑контролы поддерживаются в формате `.doc` (Word 97‑2003). Чтобы создать файл старого формата, измените формат сохранения:

```java
        doc.save("CommandButtonDemo.doc", SaveFormat.DOC);
```

## Полный исходный код (исполняемый)

```java
import com.aspose.words.*;

public class CommandButtonDemo {
    public static void main(String[] args) throws Exception {
        // Optional: apply a license if you have one
        // License license = new License();
        // license.setLicense("Aspose.Words.lic");

        // Step 1: Create a new blank document and a DocumentBuilder to edit it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Insert a CommandButton ActiveX control (how to insert button)
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControl.ControlType.COMMANDBUTTON);

        // Step 3: Position the button on the page (set button position)
        commandButton.setLeft(100 * 0.75);   // distance from the left edge (points)
        commandButton.setTop(150 * 0.75);    // distance from the top edge (points)

        // Step 4: Define the button's size and caption
        commandButton.setWidth(120 * 0.75);   // width in points
        commandButton.setHeight(30 * 0.75);   // height in points
        commandButton.setCaption("Click Me");

        // Step 5: Save the document containing the CommandButton (create word document java)
        doc.save("output/CommandButtonDemo.docx");
    }
}
```

Сохраните файл как `src/main/java/CommandButtonDemo.java`, запустите `mvn exec:java -Dexec.mainClass=CommandButtonDemo` и откройте сгенерированный документ, чтобы увидеть результат.

## Часто задаваемые вопросы

**В: Работает ли это с OpenJDK?**  
О: Да. Aspose.Words — чистый Java и работает на любой реализации JDK 8+, включая OpenJDK.

**В: Можно ли изменить шрифт или цвет кнопки?**  
О: Внешний вид ActiveX‑кнопки контролируется приложением‑хостом (Word). Вы можете прикрепить VBA‑код для изменения свойств во время выполнения, но статический вид ограничен стилем по умолчанию.

**В: Что если нужно разместить кнопку внутри ячейки таблицы?**  
О: Переместите курсор `DocumentBuilder` в ячейку перед вызовом `insertForms2OleControl`. Контроль унаследует макет ячейки, и вы всё равно можете использовать `setLeft`/`setTop` для точной настройки.

## Заключение

Теперь вы знаете, как **установить позицию кнопки** в документе Word с помощью Java, как **вставить кнопку**, как **добавить ActiveX‑контроль**, и как **добавить кнопку в Word**, следуя лучшим практикам для проектов **create Word document java**. Полный пример демонстрирует весь рабочий процесс — от настройки проекта до сохранённого файла `.docx`, содержащего рабочий CommandButton.

### Следующие шаги

* Исследуйте другие значения `Forms2OleControl.ControlType` (например, `CHECKBOX`, `TEXTBOX`), чтобы создавать более сложные формы.  
* Сочетайте кнопку с VBA‑макросами для пользовательской обработки кликов.  
* Используйте функцию слияния писем Aspose.Words для генерации персонализированных документов, уже содержащих интерактивные элементы управления.

Удачной разработки и приятного автоматизирования документов Word с помощью Java!

## Что стоит изучить дальше?

Следующие руководства охватывают тесно связанные темы, которые развивают техники, продемонстрированные в этом руководстве. Каждый ресурс включает полные работающие примеры кода с пошаговыми объяснениями, чтобы помочь вам освоить дополнительные возможности API и исследовать альтернативные подходы к реализации в ваших проектах.

- [Как создать поля формы и добавить содержимое с помощью DocumentBuilder в Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Добавить поле формы выпадающего списка в документ Word с помощью Aspose.Words for .NET](/words/english/net/add-content-using-documentbuilder/insert-combo-box/)
- [Как загрузить документы Word с Aspose.Words Java: Полное руководство](/words/english/java/document-operations/aspose-words-java-master-word-processing/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}