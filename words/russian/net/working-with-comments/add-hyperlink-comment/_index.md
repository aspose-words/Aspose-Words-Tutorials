---
title: Добавьте гиперссылочный комментарий и экспортируйте его как аннотацию PDF с помощью Aspose.Words for .NET
weight: 110
limit:
description: Научитесь добавлять гиперссылочный комментарий в файл Word и экспортировать его как аннотацию PDF с помощью Aspose.Words for .NET.
keywords: [Aspose.Words for .NET, add hyperlink comment, PDF annotation, export Word to PDF, comment with hyperlink, verify PDF output]
url: /net/working-with-comments/add-hyperlink-comment/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Научитесь добавлять гиперссылочный комментарий в файл Word и экспортировать
    его как аннотацию PDF с помощью Aspose.Words for .NET.
  headline: Добавьте гиперссылочный комментарий и экспортируйте его как аннотацию
    PDF с помощью Aspose.Words for .NET
  type: TechArticle
- description: Научитесь добавлять гиперссылочный комментарий в файл Word и экспортировать
    его как аннотацию PDF с помощью Aspose.Words for .NET.
  name: Добавьте гиперссылочный комментарий и экспортируйте его как аннотацию PDF
    с помощью Aspose.Words for .NET
  steps:
  - name: Создайте новый пустой объект Document и DocumentBuilder для работы с ним.
    text: Создайте новый пустой объект Document и DocumentBuilder для работы с ним.
  - name: Запишите строку видимого текста, которая будет содержать предстоящий комментарий.
    text: Запишите строку видимого текста, которая будет содержать предстоящий комментарий.
  - name: Создайте объект Comment, автором которого будет Jane Doe, и прикрепите его
      к первому абзацу документа.
    text: Создайте объект Comment, автором которого будет Jane Doe, и прикрепите его
      к первому абзацу документа.
  - name: Внутри комментария добавьте абзац и вставьте синюю подчёркнутую гиперссылку
      на сайт Aspose.Words Library.
    text: Внутри комментария добавьте абзац и вставьте синюю подчёркнутую гиперссылку
      на сайт Aspose.Words Library.
  - name: Настройте документ так, чтобы комментарии отображались как аннотации PDF,
      и обновите макет.
    text: Настройте документ так, чтобы комментарии отображались как аннотации PDF,
      и обновите макет.
  - name: Создайте папку "Output" в текущем каталоге для сохранения сгенерированного
      PDF.
    text: Создайте папку "Output" в текущем каталоге для сохранения сгенерированного
      PDF.
  - name: Сохраните подготовленный документ в виде PDF‑файла, используя PdfSaveOptions.
    text: Сохраните подготовленный документ в виде PDF‑файла, используя PdfSaveOptions.
  - name: Проверьте, что PDF‑файл существует и содержит данные, затем выведите результат
      в консоль.
    text: Проверьте, что PDF‑файл существует и содержит данные, затем выведите результат
      в консоль.
  type: HowTo
- questions:
  - answer: Третий параметр `InsertHyperlink` указывает, следует ли рассматривать
      ссылку как поле; установка значения `false` вставляет обычную гиперссылку, которая
      работает в аннотации PDF без необходимости кода поля.
    question: Что контролирует третий аргумент (`false`) в `InsertHyperlink`?
  - answer: Установите `myDocument.LayoutOptions.CommentDisplayMode` в `CommentDisplayMode.ShowInBalloons`
      перед вызовом `Save`; тогда PDF будет содержать комментарий как обычный комментарий
      Word, а не как аннотацию.
    question: Как сделать так, чтобы комментарий отображался в виде балуна в документе
      Word, а не как аннотация PDF?
  - answer: Да — каждый `Comment`, который вы добавляете к абзацу, может содержать
      собственный вызов `InsertHyperlink`, и все гиперссылки будут сохранены как отдельные
      аннотации PDF при сохранении документа.
    question: Если я добавлю более одного комментария, будет ли каждая гиперссылка
      работать в экспортированном PDF?
  - answer: Откройте сгенерированный PDF, найдите аннотацию комментария (обычно отображаемую
      в виде значка заметки), щёлкните её, чтобы раскрыть текст комментария, а затем
      нажмите синюю подчёркнутую ссылку; она должна открыть целевой URL в веб‑браузере.
    question: Как проверить, что гиперссылка внутри комментария действительно работает
      после генерации PDF?
  type: FAQPage
images:
- /net/working-with-comments/add-hyperlink-comment/og-image.png
og_title: Вставить гиперссылочный комментарий и экспортировать в PDF
og_description: Научитесь встраивать кликабельную ссылку в комментарий Word и превращать её в аннотацию PDF.
og_image_alt: Руководство, показывающее, как добавить комментарий с кликабельной гиперссылкой в документ Word и экспортировать его как аннотацию PDF с использованием Aspose.Words for .NET
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Добавьте гиперссылочный комментарий и экспортируйте его как аннотацию PDF с помощью Aspose.Words
В этом учебнике вы увидите, как создать документ Word, вставить комментарий, содержащий кликабельную гиперссылку на внешний веб‑сайт, настроить отображение этого комментария как аннотации PDF, экспортировать документ в PDF и проверить полученный PDF‑файл. Пошаговый код позволяет добавлять насыщенные, поддерживающие ссылки комментарии и сохранять их при конвертации в PDF, что упрощает обмен интерактивными заметками с читателями.

---

{{< tutorial-widget sourcePath="words/net/working-with-comments/add-hyperlink-comment" >}}


{{< /blocks/products/pf/tutorial-page-section >}}

{{< blocks/products/pf/tutorial-page-section >}}
## Installation Instructions
1. Download Aspose.Words for .NET:
   Get the latest version from the [Aspose Downloads page](https://releases.aspose.com/words/net/).

2. Install via NuGet:
   - Open your Visual Studio project.
   - Navigate to the NuGet Package Manager (Tools > NuGet Package Manager > Manage NuGet Packages for Solution).
   - Search for "Aspose.Words" and click Install.

3. Add Namespace References:
   Add the following namespace at the top of your code file:
   ```csharp
   using Aspose.Words;
   using Aspose.Words.Saving;
   using Aspose.Words.Drawing;
   using Aspose.Words.Fields;
   using System.Drawing;
   ```

4. Apply License (Optional):
   To use the full version, [apply a license](https://purchase.aspose.com/temporary-license/) or use a [free trial](https://releases.aspose.com/).

## Also See
[Aspose.Words for .NET Documentation](https://docs.aspose.com/words/net/)
[Aspose.Words for .NET References](https://reference.aspose.com/words/net/)

## Frequently asked questions

**Q: Что контролирует третий аргумент (`false`) в `InsertHyperlink`?**  
A: Третий параметр `InsertHyperlink` указывает, следует ли рассматривать ссылку как поле; установка значения `false` вставляет обычную гиперссылку, которая работает в аннотации PDF без необходимости кода поля.

**Q: Как сделать так, чтобы комментарий отображался в виде балуна в документе Word, а не как аннотация PDF?**  
A: Установите `myDocument.LayoutOptions.CommentDisplayMode` в `CommentDisplayMode.ShowInBalloons` перед вызовом `Save`; тогда PDF будет содержать комментарий как обычный комментарий Word, а не как аннотацию.

**Q: Если я добавлю более одного комментария, будет ли каждая гиперссылка работать в экспортированном PDF?**  
A: Да — каждый `Comment`, который вы добавляете к абзацу, может содержать собственный вызов `InsertHyperlink`, и все гиперссылки будут сохранены как отдельные аннотации PDF при сохранении документа.

**Q: Как проверить, что гиперссылка внутри комментария действительно работает после генерации PDF?**  
A: Откройте сгенерированный PDF, найдите аннотацию комментария (обычно отображаемую в виде значка заметки), щёлкните её, чтобы раскрыть текст комментария, а затем нажмите синюю подчёркнутую ссылку; она должна открыть целевой URL в веб‑браузере.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}