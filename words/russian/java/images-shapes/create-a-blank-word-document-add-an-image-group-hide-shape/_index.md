---
category: general
date: 2026-10-10
description: Создайте пустой документ Word, вставьте изображение в Word, добавьте
  группу изображений и скройте фигуру в сохранённом файле. Следуйте этому пошаговому
  руководству.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- insert image into word
- add image group
- hide shape word document
language: ru
lastmod: 2026-10-10
og_description: Создайте пустой документ Word, вставьте изображение в Word, добавьте
  группу изображений и скройте форму. Это руководство показывает полный код на C#.
og_image_alt: Screenshot of a blank Word document with a hidden image group
og_title: Создайте пустой документ Word, добавьте группу изображений, скройте фигуру
schemas:
- author: Aspose
  dateModified: '2026-10-10'
  description: Create a blank Word document, insert image into Word, add an image
    group, and hide shape in the saved file. Follow this step‑by‑step guide.
  headline: Create a blank Word document, add an image group, hide shape
  type: TechArticle
tags:
- Word automation
- Aspose.Words
- C#
- Document processing
title: Создайте пустой документ Word, добавьте группу изображений, скройте форму
url: /ru/java/images-shapes/create-a-blank-word-document-add-an-image-group-hide-shape/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Создать пустой документ Word, добавить группу изображений, скрыть форму

Если вам нужно **создать пустой документ Word** и позже скрыть визуальные элементы, этот учебник покажет вам, как это сделать. Вы научитесь вставлять изображение в Word, добавлять группу изображений и скрывать форму в документе Word в единой переиспользуемой C#‑рутине.

Мы будем использовать библиотеку Aspose.Words for .NET, которая позволяет манипулировать файлами .docx без установленного Microsoft Word. К концу этого руководства у вас будет исполняемая программа, создающая файл Word, содержащий скрытую группу изображений, готовый к дальнейшей обработке или условному отображению.

## Необходимые условия

- .NET 6.0 или новее (код также работает с .NET Framework 4.6+)
- NuGet‑пакет Aspose.Words for .NET (`Install-Package Aspose.Words`)
- Папка на диске, из которой можно читать файл изображения и записывать выходной документ
- Базовые знания C# и Visual Studio (или любой другой предпочитаемой IDE)

## Создать пустой документ Word с помощью Aspose.Words

Первый шаг — **создать пустой документ Word**. Aspose.Words предоставляет класс `Document`, который представляет Word‑файл в памяти. Создание экземпляра без аргументов дает вам пустой документ, готовый к заполнению.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1: Create a new blank document and a builder to edit it
        Document doc = new Document();                 // blank .docx container
        DocumentBuilder builder = new DocumentBuilder(doc);
```

*Почему это важно:* Начало с пустого документа гарантирует отсутствие скрытого форматирования или оставшихся разделов, которые могут мешать форме, которую вы добавите позже.

## Вставить изображение в Word с помощью DocumentBuilder

Далее мы **вставляем изображение в Word**, сначала создавая групповую форму, которая будет удерживать картинку. Групповые формы позволяют рассматривать несколько графических объектов как единое целое, что удобно, когда позже нужно скрыть или переместить их вместе.

```csharp
        // Step 2: Insert a group shape with the desired size (width: 300, height: 200)
        GroupShape group = builder.InsertGroupShape(300, 200);
```

Метод `InsertGroupShape` создаёт пустой контейнер. Размеры задаются в пунктах (1 пункт = 1/72 дюйма). Подгоните размер под разрешение изображения, которое планируете встроить.

## Добавить группу изображений в документ

Теперь мы **добавляем группу изображений**, перемещая курсор builder‑а внутрь только что созданной группы и вставляя картинку. Все последующие вставки будут частью этой группы.

```csharp
        // Step 3: Position the builder inside the group so subsequent inserts go into it
        builder.MoveTo(group);

        // Step 4: Add an image to the group shape
        // Replace the path with the actual location of your PNG/JPEG file
        builder.InsertImage(@"YOUR_DIRECTORY\photo1.png");
```

*Подсказка:* Используйте абсолютный путь или правильно экранированный относительный путь; иначе `InsertImage` выбросит `FileNotFoundException`.

## Скрыть форму в документе Word

Наконец, мы **скрываем форму в документе Word**, установив свойство `Hidden` группы в `true`. Скрытые формы не отображаются при открытии документа в Word, но остаются в файле и могут быть раскрыты программно позже.

```csharp
        // Step 5: Hide the entire group (the image will not be visible in the saved document)
        group.Hidden = true;

        // Step 6: Save the document with the hidden group
        doc.Save(@"YOUR_DIRECTORY\GroupHidden.docx");
    }
}
```

Когда вы откроете *GroupHidden.docx* в Microsoft Word, вы увидите полностью пустую страницу, потому что группа изображений скрыта. Файл всё равно содержит данные изображения, которые можно раскрыть позже, установив `group.Hidden = false`, если понадобится.

## Полный, исполняемый пример

Ниже приведена полная программа, которую можно скопировать и вставить в новый консольный проект:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace WordShapeDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Create a blank Word document
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 2️⃣ Insert a group shape (300 pt × 200 pt)
            GroupShape group = builder.InsertGroupShape(300, 200);

            // 3️⃣ Move inside the group so inserts become part of it
            builder.MoveTo(group);

            // 4️⃣ Insert the image (replace with your own file)
            builder.InsertImage(@"YOUR_DIRECTORY\photo1.png");

            // 5️⃣ Hide the group so the image is not shown
            group.Hidden = true;

            // 6️⃣ Save the result
            doc.Save(@"YOUR_DIRECTORY\GroupHidden.docx");

            Console.WriteLine("Document created successfully.");
        }
    }
}
```

**Ожидаемый результат**

- Файл с именем `GroupHidden.docx` появляется в `YOUR_DIRECTORY`.
- При открытии файла в Word отображается пустая страница.
- Скрытое изображение можно раскрыть, изменив `group.Hidden = false` и сохранив файл заново.

## Распространённые варианты и особые случаи

| Situation | How to adapt the code |
|-----------|----------------------|
| **Несколько изображений** | Вставьте дополнительные вызовы `InsertImage` после `builder.MoveTo(group)`. Все изображения останутся внутри той же группы и будут использовать тот же флаг скрытия. |
| **Разные форматы изображений** | Aspose.Words поддерживает PNG, JPEG, BMP, GIF, TIFF. Просто измените расширение файла; код менять не требуется. |
| **Условная видимость** | Сохраните пользовательскую переменную документа (`doc.Variables.Add("ShowImages", "true")`) и переключайте `group.Hidden` в зависимости от её значения во время выполнения. |
| **Большие документы** | Создайте группу на определённой странице (`builder.InsertBreak(BreakType.PageBreak)`) перед вставкой группы, чтобы избежать сдвигов разметки. |
| **Совместимость со старыми версиями Word** | Сохраните как `doc.Save("output.doc", SaveFormat.Doc)`, если нужен устаревший формат `.doc`; скрытые формы ведут себя так же. |

**Совет:** Всегда устанавливайте `group.Hidden = true` *после* вставки всех дочерних элементов. Изменение флага до добавления контента может привести к неожиданному отображению некоторых элементов в старых версиях Word.

## Заключение

Теперь вы знаете, как **создать пустой документ Word**, **вставить изображение в Word**, **добавить группу изображений** и **скрыть форму в документе Word** с помощью Aspose.Words for .NET. Полный пример демонстрирует каждый шаг от инициализации документа до сохранения файла, содержащего скрытую группу изображений.

Далее вы можете изучить:

- Добавление текстовых полей или диаграмм в ту же группу
- Использование `DocumentBuilder.StartBookmark` / `EndBookmark` для пометки скрытых секций
- Программное переключение видимости на основе ввода пользователя или переменных документа

Не стесняйтесь экспериментировать с различными формами, размерами и правилами видимости, чтобы подобрать оптимальное решение для вашего сценария автоматизации. Happy coding!

## Что стоит изучить дальше?

Следующие учебники охватывают тесно связанные темы, которые развивают техники, продемонстрированные в этом руководстве. Каждый ресурс включает полностью работающие примеры кода с пошаговыми объяснениями, помогающими освоить дополнительные возможности API и исследовать альтернативные подходы к реализации в ваших проектах.

- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create Word Document with Floating Image in .NET](/words/english/net/add-content-using-documentbuilder/insert-floating-image/)
- [Insert Inline Image in Word Document using Aspose.Words](/words/english/net/add-content-using-document-builder/insert-inline-image/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}