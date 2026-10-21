---
category: general
date: 2026-09-18
description: Создайте пустой документ в Java и добавьте кнопку ActiveX. Узнайте, как
  вставить кнопку‑команду, построить интерактивную форму и сохранить документ Word.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank document
- create interactive form
- add activex button
- how to insert command button
- create word document
language: ru
lastmod: 2026-09-18
og_description: Создайте пустой документ в Java и внедрите кнопку команд ActiveX.
  Следуйте этому пошаговому руководству, чтобы создать интерактивную форму и сохранить
  файл Word.
og_image_alt: Screenshot of a Word document showing a clickable ActiveX command button
og_title: Создать пустой документ с интерактивной кнопкой команды в Word
schemas:
- author: Aspose
  dateModified: '2026-09-18'
  description: Create blank document in Java and add an ActiveX button. Learn how
    to insert command button, build an interactive form, and save a Word document.
  headline: Create blank document with an interactive command button in Word using
    Java
  type: TechArticle
- description: Create blank document in Java and add an ActiveX button. Learn how
    to insert command button, build an interactive form, and save a Word document.
  name: Create blank document with an interactive command button in Word using Java
  steps:
  - name: 'Load the existing document: `Document doc = new Document("ExistingForm.docx");`'
    text: 'Load the existing document: `Document doc = new Document("ExistingForm.docx");`'
  - name: 'Move the builder to the desired location: `builder.moveToParagraph(5, 0);
      // 6th paragraph, first node`'
    text: 'Move the builder to the desired location: `builder.moveToParagraph(5, 0);
      // 6th paragraph, first node`'
  - name: Insert the button as shown in Step 3.
    text: Insert the button as shown in Step 3.
  - name: Adjust the button’s `Top`/`Left` based on the paragraph’s layout.
    text: Adjust the button’s `Top`/`Left` based on the paragraph’s layout.
  type: HowTo
tags:
- Aspose.Words
- Java
- ActiveX
- Word automation
title: Создать пустой документ с интерактивной кнопкой команды в Word с помощью Java
url: /ru/java/document-manipulation/create-blank-document-with-an-interactive-command-button-in/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Создать пустой документ с интерактивной кнопкой команды в Word с помощью Java

Если вам нужно **создать пустой документ**, содержащий кликабельную кнопку, это руководство покажет, как сделать это с помощью Aspose.Words for Java. Вы научитесь создавать интерактивную форму, добавлять кнопку ActiveX и, наконец, сохранять файл Word — всё за несколько лаконичных шагов.

Встраивание кнопки команды превращает статический .docx в функциональную форму, с которой конечные пользователи могут взаимодействовать непосредственно в Microsoft Word. В этом руководстве также рассматривается **как вставить кнопку команды**, обработка распространённых проблем и расширение решения для более сложных форм.

## Предварительные требования

* Java 17 или новее (код компилируется с JDK 17+)
* Aspose.Words for Java 23.9 или новее — библиотека предоставляет `Document`, `DocumentBuilder` и `Forms2OleControl`.
* IDE или система сборки (Maven/Gradle), способная добавить зависимость Aspose.Words.
* Базовые знания синтаксиса Java и концепций документов Word.

```xml
<!-- Maven dependency -->
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
</dependency>
```

## Шаг 1: Создать пустой документ

Первая операция — создать новый объект `Document`. Этот объект представляет пустой файл Word, готовый к заполнению.

```java
// Step 1: Create a new blank document
Document doc = new Document();
```

Создание пустого документа дает вам чистый холст, что необходимо, когда вы хотите **создать документ Word** программно без какого‑либо предварительного шаблона.

## Шаг 2: Инициализировать DocumentBuilder

`DocumentBuilder` — основной класс для добавления текста, таблиц и элементов управления формой. Он работает с `Document`, который вы только что создали.

```java
// Step 2: Initialize a DocumentBuilder to construct the document content
DocumentBuilder builder = new DocumentBuilder(doc);
```

Builder сохраняет текущую точку вставки, поэтому последующие команды влияют на правильное место в файле.

## Шаг 3: Вставить элемент управления Forms2Ole command button

Aspose.Words предоставляет класс `Forms2OleControl` для ActiveX‑элементов управления. Чтобы **добавить кнопку ActiveX**, вы запрашиваете тип `COMMANDBUTTON` у builder.

```java
// Step 3: Insert a Forms2Ole command button control
Forms2OleControl commandButton = builder.insertForms2OleControl(OleControlType.COMMANDBUTTON);
```

Метод `insertForms2OleControl` вставляет элемент управления в текущую позицию курсора builder. Поскольку элемент является объектом ActiveX, он работает только в настольной версии Microsoft Word, а не в Word Online.

## Шаг 4: Настроить внешний вид и позицию кнопки

Вы можете задать подпись, размер и расположение кнопки с помощью сеттеров элемента управления. Значения позиции измеряются в пунктах (1 пункт = 1/72 дюйма).

```java
// Step 4: Configure the button's appearance and position
commandButton.setCaption("Click Me");   // Text shown on the button
commandButton.setTop(100);              // Distance from the top edge of the page (points)
commandButton.setLeft(100);             // Distance from the left edge of the page (points)
commandButton.setWidth(120);            // Optional: set button width
commandButton.setHeight(30);            // Optional: set button height
```

*Зачем настраивать эти свойства?* Установка `Top` и `Left` гарантирует, что кнопка появится в нужном месте на странице, а `Caption` определяет видимую пользователю подпись. Если пропустить ширину/высоту, Word назначит размеры по умолчанию, которые могут не соответствовать вашему дизайну.

### Совет профессионала
Если вы планируете добавить несколько элементов управления, вызывайте `builder.moveToDocumentEnd()` перед каждой вставкой, чтобы избежать наложения объектов.

## Шаг 5: Сохранить документ с встроенной кнопкой команды

Наконец, запишите документ на диск. Расширение файла должно быть `.docx` (или `.doc` для более старых версий Word), чтобы сохранить элемент управления ActiveX.

```java
// Step 5: Save the document with the embedded command button
String outputPath = "C:/temp/CommandButton.docx";
doc.save(outputPath);
System.out.println("Document saved to: " + outputPath);
```

Когда вы откроете `CommandButton.docx` в Microsoft Word, вы увидите кнопку с надписью **Click Me**. При нажатии она вызовет действие ActiveX по умолчанию (по умолчанию ничего не делает). Позже вы можете прикрепить макрос или скрипт VBA, чтобы определить пользовательское поведение.

## Как вставить кнопку команды в существующую форму (необязательно)

Если у вас уже есть форма с текстовыми полями и вы хотите **создать интерактивную форму**, включающую кнопку, выполните следующие дополнительные шаги:

1. Загрузите существующий документ: `Document doc = new Document("ExistingForm.docx");`
2. Переместите builder в нужное место: `builder.moveToParagraph(5, 0); // 6‑й абзац, первый узел`
3. Вставьте кнопку, как показано в Шаге 3.
4. Скорректируйте `Top`/`Left` кнопки в соответствии с разметкой абзаца.

## Пограничные случаи и устранение неполадок

| Ситуация | Что проверить | Рекомендуемое решение |
|-----------|---------------|-----------------------|
| Кнопка не отображается в Word | Убедитесь, что файл открыт в настольной версии Word (Word Online удаляет ActiveX). | Откройте файл в Word 2016+ настольной версии. |
| Подпись обрезана | Проверьте, что ширина кнопки достаточна для размещения текста. | Увеличьте `setWidth`, пока подпись не поместится. |
| При сохранении возникает `IOException` | Убедитесь, что каталог вывода существует и у вас есть права записи. | Создайте каталог или запустите программу с повышенными правами. |
| Несколько кнопок перекрываются | Курсор builder мог не переместиться после предыдущей вставки. | Вызовите `builder.moveToDocumentEnd()` перед вставкой каждого нового элемента. |

## Полный исполняемый пример

Ниже представлен полный, автономный Java‑программ, который вы можете скопировать, скомпилировать и запустить. Он демонстрирует **создать пустой документ**, **добавить кнопку ActiveX** и **сохранить документ Word** в одном процессе.

```java
import com.aspose.words.*;

public class CommandButtonDemo {
    public static void main(String[] args) {
        try {
            // 1. Create a new blank document
            Document doc = new Document();

            // 2. Initialize DocumentBuilder
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 3. Insert an ActiveX command button
            Forms2OleControl commandButton = builder.insertForms2OleControl(OleControlType.COMMANDBUTTON);

            // 4. Configure button properties
            commandButton.setCaption("Click Me");
            commandButton.setTop(100);   // points from top
            commandButton.setLeft(100);  // points from left
            commandButton.setWidth(120);
            commandButton.setHeight(30);

            // 5. Save the document
            String outPath = "CommandButton.docx";
            doc.save(outPath);
            System.out.println("Document created: " + outPath);
        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}
```

**Ожидаемый вывод**

```
Document created: CommandButton.docx
```

Открывая `CommandButton.docx`, вы видите одну страницу с кнопкой, подписью **Click Me**, расположенной на расстоянии 100 pt от верхнего и левого краёв.

## Заключение

Теперь вы знаете, как **создать пустой документ**, встроить **кнопку ActiveX** и превратить обычный файл Word в **интерактивную форму**. Овладев **как вставить кнопку команды**, вы можете расширить этот шаблон, добавив флажки, комбобоксы или даже пользовательскую логику на VBA.

Далее рассмотрите следующие связанные темы:

* **Создать интерактивную форму** с текстовыми полями (`builder.insertField`)  
* **Добавить кнопку ActiveX**, запускающую макрос VBA (`builder.insertOleObject`)  
* **Создать документ Word** из шаблона с помощью `Document(docTemplatePath)`  
* Преобразование полученного .docx в PDF с сохранением кнопки (примечание: в PDF кнопка будет отображаться как статическое изображение).

Не бойтесь экспериментировать с размером, позицией и подписью кнопки, чтобы они соответствовали вашему UI‑дизайну. Приятного кодинга!

## Что вам следует изучить дальше?

Следующие учебники охватывают тесно связанные темы, построенные на техниках, продемонстрированных в этом руководстве. Каждый ресурс включает полные рабочие примеры кода с пошаговыми объяснениями, помогающими вам освоить дополнительные возможности API и исследовать альтернативные подходы к реализации в собственных проектах.

- [Как создавать поля формы и добавлять контент с помощью DocumentBuilder в Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Создание проекта VBA в документе Word](/words/english/net/working-with-vba-macros/create-vba-project/)
- [Создание нового документа Word](/words/english/net/add-content-using-documentbuilder/create-new-document/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}