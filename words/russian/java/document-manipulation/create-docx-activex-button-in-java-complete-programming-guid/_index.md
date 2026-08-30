---
category: general
date: 2026-08-14
description: Создайте кнопку ActiveX в docx с помощью Java и Aspose.Words. Узнайте,
  как программно добавить кнопку формы в Word и сохранить документ.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create docx ActiveX button
- add form button word
language: ru
lastmod: 2026-08-14
og_description: Создайте кнопку ActiveX в docx с помощью Java и Aspose.Words. Это
  руководство покажет, как добавить кнопку формы в Word, настроить её и сохранить
  файл.
og_image_alt: Screenshot of a Word document containing an ActiveX CommandButton created
  with Java
og_title: Создание кнопки ActiveX в docx на Java – пошаговое руководство
schemas:
- author: Aspose
  dateModified: '2026-08-14'
  description: Create docx ActiveX button in Java with Aspose.Words. Learn how to
    add a form button in Word programmatically and save the document.
  headline: Create docx ActiveX button in Java – complete programming guide
  type: TechArticle
- description: Create docx ActiveX button in Java with Aspose.Words. Learn how to
    add a form button in Word programmatically and save the document.
  name: Create docx ActiveX button in Java – complete programming guide
  steps:
  - name: Set up the project and import Aspose.Words
    text: 'Add the Aspose.Words dependency to your `pom.xml` if you use Maven:'
  - name: Create a new blank document
    text: Instantiate a `Document` object, which represents an empty Word file ready
      to receive content.
  - name: Initialize a DocumentBuilder
    text: '`DocumentBuilder` provides a fluent interface for inserting text, images,
      and controls. Attach it to the document you just created.'
  - name: Insert an ActiveX CommandButton control
    text: Use the `insertForms2OleControl` method to embed an ActiveX `CommandButton`.
      This method returns a `Forms2OleControl` instance that you can further configure.
  - name: Configure the button’s properties
    text: Set the control’s name, caption, and layout attributes. These values determine
      how the button appears in Word and how you can reference it later via VBA or
      automation scripts.
  - name: Save the document
    text: Finally, write the document to disk. Use the `.docx` extension to keep the
      file in the modern Office Open XML format.
  type: HowTo
tags:
- ActiveX
- Java
- Aspose.Words
- Word automation
title: Создание кнопки ActiveX в docx на Java — полное руководство по программированию
url: /ru/java/document-manipulation/create-docx-activex-button-in-java-complete-programming-guid/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Создание кнопки ActiveX в docx на Java – полное руководство по программированию

Если вам нужно **создать кнопку ActiveX в docx** на Java, это руководство проведёт вас через весь процесс. Вы увидите, как добавить кнопку формы в Word, настроить её свойства и получить готовый к использованию .docx‑файл.

Работа с элементами управления ActiveX часто требуется при автоматизации устаревших форм Word. В этом учебнике вы научитесь **добавлять кнопку формы в документы Word** с помощью библиотеки Aspose.Words for Java, чтобы внедрять интерактивные элементы без ручного редактирования.

## Что понадобится

Прежде чем начать, убедитесь, что у вас есть:

* Java 17 или новее (код компилируется и в более ранних версиях, но рекомендуется Java 17).
* Aspose.Words for Java 23.10 или новее — скачайте JAR с сайта Aspose или добавьте зависимость Maven.
* IDE (IntelliJ IDEA, Eclipse или VS Code) или простой текстовый редактор и инструменты сборки командной строки.
* Базовые знания синтаксиса Java и объектно‑ориентированного программирования.

## Как создать кнопку ActiveX в docx с помощью Aspose.Words

Ниже перечислены точные шаги, необходимые для **создания объектов кнопки ActiveX в docx** и их внедрения в документ Word.

### Шаг 1: Настройка проекта и импорт Aspose.Words

Добавьте зависимость Aspose.Words в ваш `pom.xml`, если используете Maven:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.10</version>
    <classifier>jdk17</classifier>
</dependency>
```

Или, если предпочитаете Gradle:

```gradle
implementation 'com.aspose:aspose-words:23.10:jdk17'
```

После того как зависимость будет разрешена, импортируйте необходимые классы в ваш Java‑файл:

```java
import com.aspose.words.Document;
import com.aspose.words.DocumentBuilder;
import com.aspose.words.forms.Forms2OleControl;
import com.aspose.words.forms.Forms2OleControlType;
```

Эти импорты дают доступ к `Document`, `DocumentBuilder` и API `Forms2OleControl`, используемому для вставки элементов управления ActiveX.

### Шаг 2: Создание нового пустого документа

Создайте объект `Document`, который представляет пустой файл Word, готовый к заполнению содержимым.

```java
// Step 2: Create a new blank document
Document document = new Document();
```

Создание документа вначале гарантирует, что последующий builder будет работать на чистом холсте.

### Шаг 3: Инициализация DocumentBuilder

`DocumentBuilder` предоставляет удобный интерфейс для вставки текста, изображений и элементов управления. Привяжите его к только что созданному документу.

```java
// Step 3: Initialize a DocumentBuilder to construct the document content
DocumentBuilder builder = new DocumentBuilder(document);
```

Builder отслеживает текущую позицию курсора внутри документа, поэтому следующая вставка произойдёт точно там, где вам нужно.

### Шаг 4: Вставка элемента управления ActiveX CommandButton

Используйте метод `insertForms2OleControl` для внедрения ActiveX `CommandButton`. Этот метод возвращает экземпляр `Forms2OleControl`, который можно дополнительно настроить.

```java
// Step 4: Insert an ActiveX CommandButton control into the document
Forms2OleControl commandButton = builder.insertForms2OleControl(
        Forms2OleControlType.COMMAND_BUTTON);
```

На данном этапе файл .docx содержит заполнитель для кнопки, но у неё ещё нет визуального заголовка или размеров.

### Шаг 5: Настройка свойств кнопки

Установите имя элемента, подпись и атрибуты расположения. Эти значения определяют, как кнопка будет выглядеть в Word и как к ней можно будет обратиться позже через VBA или скрипты автоматизации.

```java
// Step 5: Configure the button's properties (name, caption, size, and position)
commandButton.setName("btnSubmit");          // internal name used by VBA
commandButton.setCaption("Submit");          // text shown on the button
commandButton.setTop(100);                  // distance from the top of the page (points)
commandButton.setLeft(150);                 // distance from the left margin (points)
commandButton.setWidth(80);                 // button width (points)
commandButton.setHeight(30);                // button height (points)
```

> **Pro tip:** Word измеряет позиции в пунктах (1 pt ≈ 1/72 in). Отрегулируйте `setTop` и `setLeft`, чтобы выровнять кнопку относительно окружающего контента.

### Шаг 6: Сохранение документа

Наконец, запишите документ на диск. Используйте расширение `.docx`, чтобы файл оставался в современном формате Office Open XML.

```java
// Step 6: Save the document containing the ActiveX button
String outputPath = "C:/temp/ActiveXButton.docx";
document.save(outputPath);
System.out.println("Document saved to " + outputPath);
```

Когда вы откроете полученный файл в Microsoft Word, вы увидите кнопку **Submit**, расположенную в указанных координатах. Нажатие кнопки в Word не вызовет действие, если не привязать VBA‑код, но элемент полностью функционирует для форм‑ориентированных рабочих процессов.

## Часто задаваемые вопросы и особые случаи

| Вопрос | Ответ |
|----------|--------|
| **Нужна ли специальная версия Word?** | Элементы управления ActiveX поддерживаются в настольной версии Microsoft Word на Windows. Они недоступны в Word для Mac или Word Online. |
| **Можно ли использовать это с файлами `.doc`?** | Да. Сохраните документ с расширением `.doc` (`document.save("ActiveXButton.doc")`). Тот же API работает и для старого бинарного формата. |
| **Что делать, если кнопка не появляется?** | Убедитесь, что **File → Options → Trust Center → Trust Center Settings → ActiveX Settings** разрешает элементы управления ActiveX. Также проверьте, что документ не открыт в режиме «Protected View». |
| **Можно ли добавить другие элементы управления ActiveX?** | Конечно. Замените `Forms2OleControlType.COMMAND_BUTTON` на `Forms2OleControlType.CHECK_BOX`, `RADIO_BUTTON` и т.д. |
| **Есть ли ограничение по размеру?** | Размер элемента ограничен только макетом страницы. Очень большие размеры могут вызвать переполнение макета. |

## Полный, готовый к запуску пример

Ниже представлен полностью готовый Java‑класс, который вы можете скопировать, скомпилировать и запустить. Он включает все импорты, метод `main` и встроенные комментарии для ясности.

```java
package com.example.wordactive;

import com.aspose.words.Document;
import com.aspose.words.DocumentBuilder;
import com.aspose.words.forms.Forms2OleControl;
import com.aspose.words.forms.Forms2OleControlType;

public class ActiveXButtonDemo {
    public static void main(String[] args) {
        try {
            // Create a new blank document
            Document document = new Document();

            // Initialize DocumentBuilder
            DocumentBuilder builder = new DocumentBuilder(document);

            // Insert an ActiveX CommandButton control
            Forms2OleControl commandButton = builder.insertForms2OleControl(
                    Forms2OleControlType.COMMAND_BUTTON);

            // Configure button properties
            commandButton.setName("btnSubmit");
            commandButton.setCaption("Submit");
            commandButton.setTop(100);   // points from top
            commandButton.setLeft(150);  // points from left
            commandButton.setWidth(80);  // width in points
            commandButton.setHeight(30); // height in points

            // Save the document
            String outputPath = "ActiveXButton.docx";
            document.save(outputPath);
            System.out.println("Document saved successfully to " + outputPath);
        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}
```

**Ожидаемый результат:** После выполнения программы в рабочем каталоге появится `ActiveXButton.docx`. Открыв его в Microsoft Word, вы увидите кликабельную кнопку **Submit**, расположенную в верхнем‑левом углу первой страницы.

## Заключение

Теперь вы знаете, как **создавать объекты кнопки ActiveX в docx** на Java с помощью Aspose.Words, и как **добавлять кнопку формы в документы Word** программно. Шаги — настройка проекта, создание документа, вставка элемента управления, конфигурация его свойств и сохранение — охватывают весь рабочий процесс от начала до конца.

Дальше вы можете изучить:

* Добавление VBA‑макросов, реагирующих на нажатие кнопки.
* Внедрение других элементов управления ActiveX, таких как флажки или списковые поля.
* Автоматизацию генерации многостраничных форм с несколькими интерактивными элементами.

Не бойтесь экспериментировать с размерами, позициями и подписями, чтобы они соответствовали требованиям вашего дизайна формы. Приятного кодинга!

## Что изучать дальше?

Следующие учебники охватывают тесно связанные темы, расширяющие техники, продемонстрированные в этом руководстве. Каждый ресурс включает полностью работающие примеры кода с пошаговыми объяснениями, чтобы помочь вам освоить дополнительные возможности API и исследовать альтернативные подходы в ваших проектах.

- [How to create form fields and add content using DocumentBuilder in Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [How to Load HTML and Save as DOCX using Aspose.Words for Java](/words/english/java/document-loading-and-saving/loading-and-saving-html-documents/)
- [How to Create PDF Documents with Aspose.Words for Java | Document Processing API](/words/english/java/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}