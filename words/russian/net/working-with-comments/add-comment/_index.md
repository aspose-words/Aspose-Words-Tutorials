---
title: Вставьте Comment в определённый абзац Word‑документа с помощью Aspose.Words for .NET
weight: 210
limit:
description: Пошаговое руководство по добавлению комментария автора в выбранный абзац Word‑документа и сохранению его как DOCX с использованием Aspose.Words for .NET.
keywords: [add comment Aspose.Words for .NET, insert comment Word document, comment author Aspose.Words, c# add comment to Word, save DOCX with comment]
url: /net/working-with-comments/add-comment/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Пошаговое руководство по добавлению комментария автора в выбранный
    абзац Word‑документа и сохранению его как DOCX с использованием Aspose.Words for
    .NET.
  headline: Вставьте Comment в определённый абзац Word‑документа с помощью Aspose.Words
    for .NET
  type: TechArticle
- description: Пошаговое руководство по добавлению комментария автора в выбранный
    абзац Word‑документа и сохранению его как DOCX с использованием Aspose.Words for
    .NET.
  name: Вставьте Comment в определённый абзац Word‑документа с помощью Aspose.Words
    for .NET
  steps:
  - name: Создайте новый объект Document и DocumentBuilder, чтобы начать построение
      файла Word.
    text: Создайте новый объект Document и DocumentBuilder, чтобы начать построение
      файла Word.
  - name: Используйте DocumentBuilder.Writeln, чтобы добавить в документ три отдельных
      абзаца текста.
    text: Используйте DocumentBuilder.Writeln, чтобы добавить в документ три отдельных
      абзаца текста.
  - name: Безопасно получайте второй абзац, переходя к первому, если в документе менее
      двух абзацев.
    text: Безопасно получайте второй абзац, переходя к первому, если в документе менее
      двух абзацев.
  - name: Создайте объект Comment с данными автора, задайте его текст и прикрепите
      к выбранному абзацу.
    text: Создайте объект Comment с данными автора, задайте его текст и прикрепите
      к выбранному абзацу.
  - name: Сохраните изменённый документ как файл DOCX с именем 'sample.docx' в текущей
      папке.
    text: Сохраните изменённый документ как файл DOCX с именем 'sample.docx' в текущей
      папке.
  type: HowTo
- questions:
  - answer: '`if`‑блок переходит к первому абзацу (`paraList[0]`), когда `paraList.Count`
      меньше 2, поэтому комментарий будет прикреплён к этому единственному абзацу,
      а не к отсутствующему второму.'
    question: Что делает код, если документ содержит только один абзац?
  - answer: Они передаются в конструктор `Comment` вторым и третьим аргументами –
      `new Comment(wordDoc, \"Jordan\", \"JH\", DateTime.Now)` – где \"Jordan\" —
      имя автора, а \"JH\" — инициалы.
    question: Как в этом примере задаются имя автора комментария и его инициалы?
  - answer: В этом фрагменте комментарий привязан к всему `Paragraph` через `AppendChild`,
      но чтобы комментировать диапазон текста, необходимо создать `CommentRangeStart`
      и `CommentRangeEnd` вокруг нужных узлов `Run`, а затем добавить узел `Comment`
      между ними.
    question: Можно ли прикрепить комментарий к конкретному фрагменту текста, а не
      ко всему абзацу?
  - answer: '`AppendChild` добавляет узел `Comment` в коллекцию дочерних элементов
      абзаца, а Aspose.Words автоматически генерирует необходимые маркеры начала/конца
      комментария при сохранении документа.'
    question: Нужно ли вручную вставлять маркеры комментариев, или этим занимается
      `AppendChild`?
  type: FAQPage
images:
- /net/working-with-comments/add-comment/og-image.png
og_title: Вставить комментарий в абзац Word
og_description: Добавьте комментарий автора в определённый абзац и экспортируйте файл как DOCX с помощью Aspose.Words.
og_image_alt: Руководство, показывающее, как добавить комментарий к абзацу в документе Word с использованием Aspose.Words for .NET
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Вставьте Comment в определённый абзац Word‑документа с помощью Aspose.Words
С помощью Aspose.Words for .NET вы можете программно добавлять комментарии в файлы Word. Этот учебник пошагово показывает создание нового документа, вставку трёх абзацев, поиск второго абзаца и прикрепление комментария, содержащего информацию об авторе и дате. В конце документ сохраняется как файл DOCX с сохранённым комментарием.

---

{{< tutorial-widget sourcePath="words/net/working-with-comments/add-comment" >}}


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

**Q: Что делает код, если документ содержит только один абзац?**  
A: `if`‑блок переходит к первому абзацу (`paraList[0]`), когда `paraList.Count` меньше 2, поэтому комментарий будет прикреплён к этому единственному абзацу, а не к отсутствующему второму.

**Q: Как в этом примере задаются имя автора комментария и его инициалы?**  
A: Они передаются в конструктор `Comment` вторым и третьим аргументами – `new Comment(wordDoc, \"Jordan\", \"JH\", DateTime.Now)` – где \"Jordan\" — имя автора, а \"JH\" — инициалы.

**Q: Можно ли прикрепить комментарий к конкретному фрагменту текста, а не ко всему абзацу?**  
A: В этом фрагменте комментарий привязан к всему `Paragraph` через `AppendChild`, но чтобы комментировать диапазон текста, необходимо создать `CommentRangeStart` и `CommentRangeEnd` вокруг нужных узлов `Run`, а затем добавить узел `Comment` между ними.

**Q: Нужно ли вручную вставлять маркеры комментариев, или этим занимается `AppendChild`?**  
A: `AppendChild` добавляет узел `Comment` в коллекцию дочерних элементов абзаца, а Aspose.Words автоматически генерирует необходимые маркеры начала/конца комментария при сохранении документа.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}