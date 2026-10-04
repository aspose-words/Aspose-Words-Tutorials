---
category: general
date: 2026-10-04
description: Узнайте, как инициализировать DocumentBuilder для нового документа и
  добавить кнопку ActiveX с помощью Aspose.Words в Java. Пошаговое руководство с полным
  кодом.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- initialize DocumentBuilder for new document
- insert ActiveX button
- Forms2OleControl command button
- Aspose.Words DocumentBuilder example
- create Word document with ActiveX
language: ru
lastmod: 2026-10-04
og_description: Инициализируйте DocumentBuilder для нового документа и внедрите кнопку
  ActiveX с помощью Aspose.Words Java API. Следуйте этому краткому руководству.
og_image_alt: Screenshot showing DocumentBuilder initialized for a new document with
  an ActiveX button
og_title: Инициализация DocumentBuilder для нового документа – полное руководство
  по Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-10-04'
  description: Learn how to initialize DocumentBuilder for new document and add an
    ActiveX button with Aspose.Words in Java. Step‑by‑step guide with full code.
  headline: How to initialize DocumentBuilder for new document using Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- Java
- DocumentBuilder
- ActiveX
title: Как инициализировать DocumentBuilder для нового документа с помощью Aspose.Words
url: /ru/java/using-document-elements/how-to-initialize-documentbuilder-for-new-document-using-asp/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Как инициализировать DocumentBuilder для нового документа с помощью Aspose.Words

Если вам нужно **initialize DocumentBuilder for new document** в Java‑проекте, этот учебник покажет точные шаги. Вы увидите, как создать пустой файл Word, добавить кнопку ActiveX command button и сохранить результат — всё в одном автономном примере кода.

Работа с документами Word программно часто подразумевает работу с низкоуровневыми деталями, такими как элементы управления формами. К концу этого руководства вы сможете внедрять кнопку ActiveX, не покидая IDE, что полезно для создания шаблонов, автоматических отчетов или интерактивных форм.

## Требования

* Java 17 или новее установлен  
* Maven 3.8+ (или Gradle, если предпочитаете)  
* Лицензия Aspose.Words for Java (бесплатная пробная версия подходит для тестирования)  
* Базовое знакомство с синтаксисом Java  

Если вы новичок в Aspose.Words, библиотека предоставляет высокоуровневый API для создания, редактирования и сохранения документов Word. Класс `DocumentBuilder` является основным входом для построения содержимого документа.

## Шаг 1: Настройка проекта Maven

Создайте новый проект Maven (или добавьте в существующий) и включите зависимость Aspose.Words:

```xml
<!-- pom.xml -->
<project>
    <modelVersion>4.0.0</modelVersion>
    <groupId>com.example</groupId>
    <artifactId>activex-demo</artifactId>
    <version>1.0.0</version>
    <dependencies>
        <dependency>
            <groupId>com.aspose</groupId>
            <artifactId>aspose-words</artifactId>
            <version>24.9</version> <!-- Use the latest stable version -->
        </dependency>
    </dependencies>
</project>
```

> **Совет:** Держите версию библиотеки актуальной; новые релизы добавляют поддержку дополнительных элементов управления формами и повышают производительность.

## Шаг 2: Инициализация `DocumentBuilder` для нового документа

Суть учебника — операция **initialize DocumentBuilder for new document**. Сначала вы создаёте пустой экземпляр `Document`, затем передаёте его конструктору `DocumentBuilder`.

```java
import com.aspose.words.*;

public class ActiveXButtonDemo {
    public static void main(String[] args) throws Exception {
        // Step 2.1: Create a new empty document
        Document doc = new Document();

        // Step 2.2: Initialize DocumentBuilder for new document
        DocumentBuilder builder = new DocumentBuilder(doc);
```

*Почему это важно:* Инициализация `DocumentBuilder` привязывает построитель к конкретному объекту `Document`, позволяя добавлять абзацы, таблицы или элементы управления формами непосредственно в этот документ. Без этого шага у построителя не будет цели для работы.

## Шаг 3: Вставка элемента управления ActiveX command button

Aspose.Words предоставляет класс `Forms2OleControl` для встраивания устаревших ActiveX‑элементов управления. Следующий код добавляет **Forms2OleControl command button** в текущую позицию курсора.

```java
        // Step 3.1: Insert an ActiveX command button control
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON);

        // Step 3.2: Set the button caption (the text displayed on the button)
        commandButton.setCaption("Click Me");
```

### Что такое ActiveX command button?

ActiveX command button — это устаревший элемент пользовательского интерфейса, который может выполнять макросы или вызывать события при щелчке пользователя внутри документа Word. Хотя современные версии Office предпочитают Content Controls, многие корпоративные шаблоны всё ещё используют ActiveX для обратной совместимости.

## Шаг 4: Сохранение документа

После вставки элемента управления просто вызовите `save`. Файл будет содержать кнопку ActiveX и его можно открыть в Microsoft Word.

```java
        // Step 4: Save the document containing the ActiveX button
        String outputPath = "output/ActiveXButton.docx";
        doc.save(outputPath);
        System.out.println("Document saved to " + outputPath);
    }
}
```

Когда вы откроете `ActiveXButton.docx` в Word, вы увидите кнопку с надписью **Click Me**. Нажатие на кнопку ничего не сделает, если вы не привяжете макрос, но сам элемент управления полностью функционирует.

## Полный, исполняемый пример

Ниже приведена полная программа, которую вы можете скопировать и вставить в `src/main/java/com/example/ActiveXButtonDemo.java`. Она включает все импорты и обработку ошибок, необходимые для быстрого теста.

```java
package com.example;

import com.aspose.words.*;

public class ActiveXButtonDemo {
    public static void main(String[] args) {
        try {
            // Step 1: Create a new empty document
            Document doc = new Document();

            // Step 2: Initialize DocumentBuilder for new document
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Step 3: Insert an ActiveX command button control
            Forms2OleControl commandButton = builder.insertForms2OleControl(
                    Forms2OleControlType.COMMANDBUTTON);
            commandButton.setCaption("Click Me");

            // Step 4: Save the document
            String outputPath = "output/ActiveXButton.docx";
            doc.save(outputPath);
            System.out.println("Document saved to " + outputPath);
        } catch (Exception e) {
            System.err.println("Error creating document: " + e.getMessage());
            e.printStackTrace();
        }
    }
}
```

**Ожидаемый вывод**

```
Document saved to output/ActiveXButton.docx
```

Откройте сгенерированный файл в Microsoft Word 2016 или более новой версии; вы должны увидеть кнопку с надписью *Click Me*, размещённую в верхней части первой страницы.

## Распространённые варианты и граничные случаи

| Scenario | Adjustment |
|----------|------------|
| **Добавить кнопку в конкретный абзац** | Переместите курсор построителя с помощью `builder.moveToParagraph(index, NodeType.PARAGRAPH);` перед вызовом `insertForms2OleControl`. |
| **Установить размер кнопки** | Используйте `commandButton.setWidth(100);` и `commandButton.setHeight(30);` для задания размеров в пунктах. |
| **Добавить макрос к кнопке** | После сохранения документа откройте его в Word, включите вкладку Developer и вручную привяжите к кнопке макрос VBA (элементы управления ActiveX нельзя скриптовать напрямую из Aspose.Words). |
| **Целевой формат .doc (бинарный)** | Измените `doc.save(outputPath, SaveFormat.DOC);`, чтобы создать файл в старом формате Word 97‑2003. |
| **Запуск на Android** | Используйте Aspose.Words for Android через его Java API; тот же код будет работать, пока библиотека включена в APK. |

## Советы по устранению неполадок

* **`java.lang.NoClassDefFoundError`** – Убедитесь, что JAR‑файл Aspose.Words находится в classpath. Maven добавляет его автоматически; для ручных сборок разместите JAR в `libs/` и добавьте его в библиотеки вашей IDE.  
* **Button does not appear in Word** – Проверьте, включена ли опция *Show legacy forms* в Центре управления безопасностью Word (`File → Options → Trust Center → Trust Center Settings → Macro Settings`).  
* **License exception** – Если вы запускаете код без действующей лицензии, Aspose.Words вставит водяной знак. Зарегистрируйте бесплатную пробную версию или приобретите лицензию, чтобы удалить его.

## Заключение

Теперь вы знаете, как **initialize DocumentBuilder for new document**, вставить кнопку ActiveX command button и сохранить результат с помощью Aspose.Words for Java. Этот шаблон позволяет программно генерировать интерактивные шаблоны Word, что особенно удобно для автоматической генерации отчетов или форм‑ориентированных рабочих процессов.

Отсюда вы можете изучать дополнительные элементы управления формами (`Forms2OleControlType.CHECKBOX`, `COMBOBOX` и т.д.), комбинировать кнопку с пользовательскими макросами VBA или генерировать полнофункциональные документы, включающие таблицы, изображения и стили — всё с использованием того же рабочего процесса `DocumentBuilder`.

---

*Готовы создавать более сложную автоматизацию Word? Ознакомьтесь с нашими руководствами по **insert table with DocumentBuilder**, **apply styles programmatically**, и **export to PDF with Aspose.Words**.*

## Что следует изучить дальше?

Следующие учебники охватывают тесно связанные темы, построенные на техниках, продемонстрированных в этом руководстве. Каждый ресурс включает полные рабочие примеры кода с пошаговыми объяснениями, чтобы помочь вам освоить дополнительные возможности API и исследовать альтернативные подходы к реализации в ваших проектах.

- [Как создать поля формы и добавить содержимое с помощью DocumentBuilder в Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Как сохранить документ как PDF с помощью Aspose.Words for Java](/words/english/java/document-loading-and-saving/saving-documents-as-pdf/)
- [Как добавить водяной знак в документ с помощью Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-watermarks-to-documents/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}