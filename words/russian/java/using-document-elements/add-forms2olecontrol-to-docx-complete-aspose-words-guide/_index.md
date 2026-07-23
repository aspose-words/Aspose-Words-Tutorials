---
category: general
date: 2026-07-23
description: Узнайте, как добавить Forms2OleControl в DOCX с помощью Aspose.Words.
  Это пошаговое руководство показывает, как вставить элемент управления ActiveX CommandButton
  в Java.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- add forms2olecontrol to docx
- insert ActiveX control in DOCX
- Aspose.Words Forms2OleControl example
- embed CommandButton in Word document
- Java DocumentBuilder ActiveX
language: ru
lastmod: 2026-07-23
og_description: Добавьте Forms2OleControl в DOCX мгновенно. Следуйте этому практическому
  руководству, чтобы встроить ActiveX CommandButton с помощью Aspose.Words для Java.
og_image_alt: Screenshot of Java code that adds Forms2OleControl to DOCX using Aspose.Words
og_title: Добавьте Forms2OleControl в DOCX – Полное руководство по Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-07-23'
  description: Learn how to add Forms2OleControl to DOCX using Aspose.Words. This
    step‑by‑step guide shows inserting an ActiveX CommandButton control in Java.
  headline: Add Forms2OleControl to DOCX – Complete Aspose.Words Guide
  type: TechArticle
- description: Learn how to add Forms2OleControl to DOCX using Aspose.Words. This
    step‑by‑step guide shows inserting an ActiveX CommandButton control in Java.
  name: Add Forms2OleControl to DOCX – Complete Aspose.Words Guide
  steps:
  - name: Using a Different ActiveX Control
    text: 'If you want a checkbox instead of a button, just change the control type:'
  - name: Embedding Multiple Controls
    text: Call `builder.insertForms2OleControl()` multiple times, moving the cursor
      with `builder.moveTo()` or inserting text between calls. Each call adds a new
      OLE container, so you can build complex forms inside a single DOCX.
  - name: Working with .NET
    text: The same logic applies to C#—the method names are identical (`DocumentBuilder.InsertForms2OleControl()`).
      If you’re on .NET, replace the Java syntax with its C# counterpart, but the
      **embed CommandButton in Word document** concept stays unchanged.
  type: HowTo
tags:
- Aspose.Words
- ActiveX
- Java
- DOCX
title: Добавление Forms2OleControl в DOCX – Полное руководство по Aspose.Words
url: /ru/java/using-document-elements/add-forms2olecontrol-to-docx-complete-aspose-words-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Добавление Forms2OleControl в DOCX – Полное руководство по Aspose.Words

Вы когда‑нибудь задумывались, как **add Forms2OleControl to DOCX** без лишних усилий? Вы не одиноки. Независимо от того, создаёте ли вы отчёт на основе шаблона или вам нужна кликабельная кнопка внутри файла Word, внедрение ActiveX‑контрола — это секретный ингредиент.

В этом руководстве мы пройдём конкретный пример, который **adds Forms2OleControl to DOCX** с помощью Aspose.Words for Java. Вы увидите полный код, поймёте, почему каждая строка важна, и получите советы по работе с особенностями, которые часто ставят разработчиков в тупик.

## Что вы узнаете

- Как настроить Aspose.Words в Java‑проекте  
- Точные шаги для **insert an ActiveX control in DOCX** (да, основной ключевой запрос снова)  
- Настройка свойств CommandButton, чтобы он вел себя как реальный элемент UI  
- Сохранение документа и проверка, что контрол действительно встроен  

Предварительный опыт работы с ActiveX не требуется, но базовое понимание Java и Maven/Gradle сделает процесс проще. Готовы? Погружаемся.

---

## Шаг 1: Настройка Aspose.Words в вашем проекте

Прежде чем вы сможете **add Forms2OleControl to DOCX**, вам нужна библиотека Aspose.Words в classpath. Самый простой способ — через Maven:

```xml
<!-- pom.xml -->
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version> <!-- Use the latest stable version -->
</dependency>
```

> **Pro tip:** Если вы используете Gradle, эквивалент будет `implementation 'com.aspose:aspose-words:24.9'`.  

Почему это важно: Aspose.Words предоставляет метод `DocumentBuilder.insertForms2OleControl()`, которым мы будем пользоваться для **insert an ActiveX control in DOCX**. Без библиотеки компилятор не будет знать, что такое `Forms2OleControl`.

## Шаг 2: Добавление Forms2OleControl в DOCX

Теперь начинается основная часть руководства — здесь мы действительно **add Forms2OleControl to DOCX**. Мы создадим новый документ, инициализируем `DocumentBuilder` и вызовем метод вставки.

```java
import com.aspose.words.*;

public class ActiveXExample {
    public static void main(String[] args) throws Exception {
        // Step 2.1: Create a new blank document
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Step 2.2: Insert an ActiveX Forms2OleControl (CommandButton)
        Forms2OleControl commandButton = builder.insertForms2OleControl();

        // Step 2.3: Configure the CommandButton properties
        commandButton.setOleControlType(OleControlType.COMMANDBUTTON);
        commandButton.setName("MyButton");
        commandButton.setCaption("Click Me");

        // Step 2.4: Save the document with the embedded control
        String outPath = "output/ActiveXButton.docx";
        document.save(outPath);
        System.out.println("Document saved to " + outPath);
    }
}
```

**Что происходит здесь?**  

- `new Document()` дает нам чистый холст. Представьте его как чистый лист бумаги, готовый для **insert ActiveX control in DOCX**.  
- `builder.insertForms2OleControl()` создаёт низкоуровневый OLE‑контейнер, который Aspose.Words называет *Forms2OleControl*. Это единственный вызов API, который действительно **adds Forms2OleControl to DOCX**.  
- Установка `OleControlType.COMMANDBUTTON` сообщает Word, что OLE‑объект должен вести себя как классический CommandButton — точно так же, как кнопку, которую вы размещаете на форме в конструкторе UI.  
- Наконец, `document.save(...)` записывает файл .docx, сохраняющий встроенный ActiveX.

## Шаг 3: Настройка свойств CommandButton (Почему это важно)

Простая вставка контрола даёт вам пустой заполнитель. Чтобы он стал полезным, необходимо задать несколько свойств:

| Property | Purpose | Typical Value |
|----------|---------|---------------|
| `setOleControlType` | Определяет тип ActiveX‑контрола (Button, CheckBox и т.д.) | `OleControlType.COMMANDBUTTON` |
| `setName` | Внутренний идентификатор, используемый макросами Word или скриптами VBA | `"MyButton"` |
| `setCaption` | Текст, отображаемый на поверхности кнопки | `"Click Me"` |

Если вы пропустите эти настройки, кнопка будет отображаться с общим именем и без подписи — ничего, что пользователь захотел бы нажать. Кроме того, помните, что ActiveX‑контролы являются **platform‑specific**; они работают только на Windows‑машинах с установленными соответствующими COM‑библиотеками.

> **Watch out:** При открытии сгенерированного DOCX на платформе, отличной от Windows (например, macOS), Word покажет изображение‑заполнитель вместо реальной кнопки. Это нормальное ограничение ActiveX, а не ошибка в вашем коде.

## Шаг 4: Сохранение и проверка документа

Вызов `document.save(...)` записывает стандартный DOCX‑файл, который может открыть любая современная версия Microsoft Word. После выполнения программы откройте `ActiveXButton.docx`:

1. Найдите кнопку “Click Me” в месте её вставки.  
2. Щёлкните правой кнопкой мыши по кнопке → **Properties**, чтобы подтвердить имя и подпись.  
3. Нажмите кнопку; Word отобразит простое окно сообщения, если вы прикрепили макрос (это выходит за рамки данного руководства).

Если кнопка отсутствует, дважды проверьте, что вы правильно использовали **Aspose.Words Forms2OleControl example** и что папка вывода существует.  

> **Edge case:** Если вам нужно, чтобы кнопка запускала макрос, вам придётся добавить VBA‑код в документ после его сохранения. Aspose.Words может внедрять VBA с помощью API `Document.getBuiltInDocumentProperties()`, но это уже отдельное руководство.

## Распространённые варианты и подводные камни

### Использование другого ActiveX‑контрола

Если вам нужен флажок вместо кнопки, просто измените тип контрола:

```java
commandButton.setOleControlType(OleControlType.CHECKBOX);
commandButton.setCaption("Accept Terms");
```

### Встраивание нескольких контролов

Вызовите `builder.insertForms2OleControl()` несколько раз, перемещая курсор с помощью `builder.moveTo()` или вставляя текст между вызовами. Каждый вызов добавляет новый OLE‑контейнер, поэтому вы можете создавать сложные формы в одном DOCX.

### Работа с .NET

Тот же принцип применим к C# — имена методов идентичны (`DocumentBuilder.InsertForms2OleControl()`). Если вы работаете в .NET, замените синтаксис Java на его аналог в C#, но концепция **embed CommandButton in Word document** остаётся неизменной.

## Заключение

Теперь у вас есть рабочий, сквозной пример, который **adds Forms2OleControl to DOCX** с помощью Aspose.Words for Java. Создав пустой документ, вставив ActiveX‑контрол, настроив его свойства и сохранив файл, вы освоили основные шаги для **insert ActiveX control in DOCX** и можете расширять этот шаблон на другие типы контролов.

Что дальше? Попробуйте сочетать эту технику с слиянием почты Aspose.Words (mail‑merge) для создания персонализированных форм, или изучите добавление VBA‑макросов, чтобы кнопка действительно что‑то делала. Возможности безграничны, когда вы комбинируете код **Aspose.Words Forms2OleControl example** со своей бизнес‑логикой.

Удачной разработки, и не стесняйтесь оставлять комментарий, если столкнётесь с проблемами!

## Что вам стоит изучить дальше?

Следующие руководства охватывают тесно связанные темы, которые развивают техники, продемонстрированные в этом руководстве. Каждый ресурс включает полные рабочие примеры кода с пошаговыми объяснениями, чтобы помочь вам освоить дополнительные возможности API и исследовать альтернативные подходы к реализации в ваших проектах.

- [Как создавать поля формы и добавлять контент с помощью DocumentBuilder в Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Добавление закладок в Word с Aspose.Words for Java – вставка, обновление, удаление](/words/english/java/content-management/aspose-words-java-manage-bookmarks/)
- [Как добавить водяной знак в документы с помощью Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-watermarks-to-documents/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}