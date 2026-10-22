---
category: general
date: 2026-10-07
description: Создайте кнопку ActiveX в Java и программно добавьте её в документы Word.
  Узнайте, как установить левую и верхнюю позицию кнопки.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create activex command button
- programmatically add command button
- how to set button left top
language: ru
lastmod: 2026-10-07
og_description: Создайте кнопку команд ActiveX на Java, чтобы встраивать интерактивные
  элементы управления в ваши документы Word. Узнайте, как программно добавить кнопку
  команд, задать её позицию и настроить внешний вид.
og_image_alt: Screenshot showing a created ActiveX command button in a Java‑generated
  Word document
og_title: Создание кнопки команд ActiveX в Java — пошаговое руководство
schemas:
- author: Aspose
  dateModified: '2026-10-07'
  description: Create ActiveX command button in Java and programmatically add command
    button to Word docs. Learn how to set button left top positions.
  headline: How to create ActiveX command button in Java
  type: TechArticle
- description: Create ActiveX command button in Java and programmatically add command
    button to Word docs. Learn how to set button left top positions.
  name: How to create ActiveX command button in Java
  steps:
  - name: How to set button left top
    text: Positioning the button is where the secondary keyword **how to set button
      left top** becomes relevant. The `setLeft` and `setTop` methods accept values
      measured in points (1 point = 1/72 in).
  - name: Adding multiple buttons
    text: If you need several buttons, repeat **Step 2** and **Step 3** for each control.
      Remember to adjust `setLeft` and `setTop` so the buttons don’t overlap.
  - name: Changing button behavior
    text: 'ActiveX buttons can run VBA macros when clicked. To attach a macro, set
      the `setOnAction` property with the macro name:'
  - name: Compatibility notes
    text: '- The button works only in desktop versions of Word that support ActiveX
      (e.g., Word for Windows). It will appear as a static image in Word for Mac or
      online editors. - If you target a mixed environment, consider using a **content
      control** (`RichTextContentControl`) instead of an ActiveX control.'
  - name: Next steps
    text: '- Explore other ActiveX controls such as `Forms.TextBox.1` or `Forms.CheckBox.1`.
      - Combine multiple controls with a VBA module to implement full‑featured forms.
      - Replace ActiveX with content controls if you need cross‑platform compatibility.'
  type: HowTo
tags:
- ActiveX
- Java
- Aspose.Words
title: Как создать командную кнопку ActiveX в Java
url: /ru/java/using-document-elements/how-to-create-activex-command-button-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Как создать кнопку команд ActiveX в Java

Если вам нужно **create ActiveX command button** в документе Word с помощью Java, это руководство покажет вам точно как. Вы увидите полный, исполняемый пример, который **programmatically adds a command button**, позиционирует его с помощью `setLeft` и `setTop` и сохраняет результат в файл `.docx`.

Встраивание интерактивной кнопки позволяет создавать формы, автоматизировать рабочие процессы или собирать ввод пользователя непосредственно внутри файла Word. Ниже приведены все шаги от настройки проекта до окончательной проверки, чтобы вы могли скопировать код в свой проект без пропусков.

## Предварительные требования

Перед началом убедитесь, что у вас есть:

- JDK 17 или новее установлен  
- Maven 3.8+ (или ваш предпочтительный инструмент сборки)  
- Aspose.Words for Java 23.9 или новее – библиотека, предоставляющая `DocumentBuilder` и поддержку OLE‑контролей  
- Базовое знакомство с синтаксисом Java и объектно‑ориентированными концепциями  

Если вы используете Maven, добавьте зависимость в ваш `pom.xml`:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
    <classifier>jdk17</classifier>
</dependency>
```

> **Pro tip:** Используйте последнюю версию Aspose.Words, чтобы получить выгоду от исправлений ошибок и новых возможностей OLE.

## Шаг 1: Создать новый пустой документ и DocumentBuilder

Первый шаг к **create ActiveX command button** — создать пустой `Document` и `DocumentBuilder`. Builder предоставляет удобный API для вставки контента, включая OLE‑контролы.

```java
import com.aspose.words.*;

public class ActiveXButtonDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new empty document and a DocumentBuilder to work with it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

`Document` представляет файл Word в памяти, а `DocumentBuilder` выступает в роли курсора, позволяющего точно размещать элементы там, где это необходимо.

## Шаг 2: Вставить OLE‑контроль кнопки команд

ActiveX‑контролы вставляются как OLE‑объекты. Aspose.Words предоставляет класс `Forms2OleControl` для этой цели.

```java
        // Step 2: Insert an OLE command button control into the document
        Forms2OleControl commandButton = builder.insertForms2OleControl();
```

При вызове `insertForms2OleControl()` Aspose автоматически создаёт форму‑заполнитель, которая будет хостить кнопку ActiveX.

## Шаг 3: Настроить свойства кнопки

Теперь вы **programmatically add command button** детали, такие как ProgID, подпись и размер. Наиболее распространённый ProgID для кнопки команд — `"Forms.CommandButton.1"`.

```java
        // Step 3: Configure the button's properties (type, position, size, caption)
        commandButton.setProgId("Forms.CommandButton.1"); // ActiveX class identifier
        commandButton.setCaption("Click Me");            // Text shown on the button
        commandButton.setWidth(80);                      // Width in points
        commandButton.setHeight(30);                     // Height in points
```

### Как задать кнопку left top

Позиционирование кнопки — это место, где вторичное ключевое слово **how to set button left top** становится актуальным. Методы `setLeft` и `setTop` принимают значения в пунктах (1 пункт = 1/72 дюйма).

```java
        // Position the button 100 points from the left margin and 150 points from the top
        commandButton.setLeft(100);   // Horizontal offset
        commandButton.setTop(150);    // Vertical offset
```

Отрегулируйте эти числа под ваш макет. Например, чтобы выровнять кнопку по ячейке таблицы, вычислите координаты ячейки и передайте их в `setLeft`/`setTop`.

## Шаг 4: Сохранить документ

Наконец, запишите документ на диск. Файл будет содержать кнопку ActiveX, готовую к взаимодействию при открытии в Microsoft Word.

```java
        // Step 4: Save the document containing the button
        doc.save("CommandButton.docx");
        System.out.println("Document saved successfully.");
    }
}
```

Запуск метода `main` создаёт `CommandButton.docx`. Откройте файл в Word, при необходимости включите содержимое, и вы увидите кликабельную кнопку с подписью **Click Me**, расположенную в указанных координатах.

![Create ActiveX command button in Java](/images/activex-button-screenshot.png){.center width=600 alt="Скриншот создания кнопки команд ActiveX в Java, показывающий кнопку внутри документа Word"}

## Общие варианты и особые случаи

### Добавление нескольких кнопок

Если вам нужно несколько кнопок, повторите **Step 2** и **Step 3** для каждого контроля. Не забудьте скорректировать `setLeft` и `setTop`, чтобы кнопки не перекрывались.

### Изменение поведения кнопки

ActiveX‑кнопки могут запускать VBA‑макросы при нажатии. Чтобы привязать макрос, установите свойство `setOnAction` с именем макроса:

```java
commandButton.setOnAction("MyMacro");
```

Убедитесь, что целевой документ содержит соответствующий VBA‑модуль; иначе Word выдаст ошибку.

### Примечания о совместимости

- Кнопка работает только в настольных версиях Word, поддерживающих ActiveX (например, Word для Windows). В Word для Mac или онлайн‑редакторах она будет отображаться как статическое изображение.  
- Если вы нацелены на смешанную среду, рассмотрите возможность использования **content control** (`RichTextContentControl`) вместо ActiveX‑контроля.

## Полный исходный код для справки

Ниже приведён полностью самостоятельный пример, который вы можете скопировать в новый Maven‑проект и сразу запустить.

```java
import com.aspose.words.*;

public class ActiveXButtonDemo {
    public static void main(String[] args) throws Exception {
        // Create a new empty document and a DocumentBuilder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert an OLE command button control
        Forms2OleControl commandButton = builder.insertForms2OleControl();

        // Configure the button
        commandButton.setProgId("Forms.CommandButton.1");
        commandButton.setCaption("Click Me");
        commandButton.setWidth(80);
        commandButton.setHeight(30);

        // How to set button left top – position the control
        commandButton.setLeft(100);   // Horizontal offset in points
        commandButton.setTop(150);    // Vertical offset in points

        // Save the resulting document
        doc.save("CommandButton.docx");
        System.out.println("Document saved successfully.");
    }
}
```

**Expected output:** После выполнения вы найдёте `CommandButton.docx` в рабочем каталоге вашего проекта. Открытие файла в Microsoft Word покажет кнопку в указанном месте с подписью “Click Me”.

## Заключение

Теперь вы знаете, как **create ActiveX command button** в Java, **programmatically add command button** в документ Word и точно управлять её расположением с помощью методов **how to set button left top**. Эта техника открывает возможности создания богатых интерактивных форм Word, которые могут запускать макросы, открывать внешние приложения или собирать ввод пользователя непосредственно внутри документа.

### Следующие шаги

- Исследуйте другие ActiveX‑контролы, такие как `Forms.TextBox.1` или `Forms.CheckBox.1`.  
- Скомбинируйте несколько контролей с VBA‑модулем для реализации полнофункциональных форм.  
- Замените ActiveX на content controls, если нужна кроссплатформенная совместимость.  

Экспериментируйте с размером, подписью и позиционированием, чтобы соответствовать вашему UI‑дизайну. Если возникнут проблемы, дважды проверьте, что используемая версия Aspose.Words поддерживает OLE‑контролы, и убедитесь, что настройки безопасности Word позволяют выполнение ActiveX. Happy coding!

## Что следует изучить дальше?

Следующие руководства охватывают тесно связанные темы, построенные на техниках, продемонстрированных в этом руководстве. Каждый ресурс включает полные рабочие примеры кода с пошаговыми объяснениями, помогающими освоить дополнительные возможности API и исследовать альтернативные подходы к реализации в ваших проектах.

- [Встраивание OLE‑объектов и ActiveX‑контролей в документы Word](/words/english/python-net/document-structure-and-content-manipulation/document-ole-objects-active-x/)
- [Как создавать поля формы и добавлять содержимое с помощью DocumentBuilder в Aspose.Words для Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Создание прямоугольной фигуры в Word с помощью Java – Полное руководство](/words/english/java/images-shapes/create-rectangle-shape-in-word-with-java-full-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}