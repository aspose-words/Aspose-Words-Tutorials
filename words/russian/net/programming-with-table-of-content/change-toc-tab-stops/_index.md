---
title: Изменение позиций табуляции оглавления в документе Word
linktitle: Изменение позиций табуляции оглавления в документе Word
second_title: API обработки документов Aspose.Words
description: Узнайте, как изменить позиции табуляции TOC в документах Word с помощью Aspose.Words для .NET. Это пошаговое руководство поможет вам создать профессионально выглядящее оглавление.
weight: 10
url: /ru/net/programming-with-table-of-content/change-toc-tab-stops/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Изменение позиций табуляции оглавления в документе Word

## Введение

Вы когда-нибудь задумывались, как оживить оглавление (TOC) в документах Word? Может быть, вы хотите, чтобы эти табуляции были идеально выровнены для этого профессионального штриха. Вы в правильном месте! Сегодня мы подробно рассмотрим, как можно изменить табуляции TOC с помощью Aspose.Words для .NET. Оставайтесь, и я обещаю, что вы уйдете со всеми знаниями, чтобы ваше TOC выглядело стильно и аккуратно.

## Предпосылки

Прежде чем начать, давайте убедимся, что у вас есть все необходимое:

1.  Aspose.Words для .NET: Вы можете[скачать здесь](https://releases.aspose.com/words/net/).
2. Среда разработки: Visual Studio или любая совместимая с C# IDE.
3. Документ Word: в частности, содержащий оглавление.

Все понял? Отлично! Поехали.

## Импорт пространств имен

Прежде всего, вам нужно импортировать необходимые пространства имен. Это похоже на упаковку инструментов перед началом проекта.

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
```

Давайте разобьем этот процесс на простые, удобоваримые шаги. Мы загрузим документ, изменим позиции табуляции оглавления и сохраним обновленный документ.

## Шаг 1: Загрузите документ

Зачем? Нам нужно получить доступ к документу Word, содержащему оглавление, которое мы хотим изменить.

Как? Вот простой фрагмент кода, с которого можно начать:

```csharp
// Путь к каталогу ваших документов
string dataDir = "YOUR DOCUMENTS DIRECTORY";

// Загрузите документ, содержащий оглавление
Document doc = new Document(dataDir + "Table of contents.docx");
```

Представьте, что ваш документ — это торт, и мы собираемся добавить немного глазури. Первый шаг — достать этот торт из коробки.

## Шаг 2: Определите параграфы оглавления

Зачем? Нам нужно точно определить параграфы, составляющие оглавление. 

Как? Пройдитесь по абзацам и проверьте их стили:

```csharp
foreach(Paragraph para in doc.GetChildNodes(NodeType.Paragraph, true))
{
    if (para.ParagraphFormat.Style.StyleIdentifier >= StyleIdentifier.Toc1 &&
        para.ParagraphFormat.Style.StyleIdentifier <= StyleIdentifier.Toc9)
    {
        // Найден абзац оглавления
    }
}
```

Думайте об этом как о сканировании толпы, чтобы найти своих друзей. Здесь мы ищем абзацы, стилизованные под записи TOC.

## Шаг 3: Измените позиции табуляции

Почему? Вот где происходит магия. Изменение позиций табуляции придает вашему TOC более чистый вид.

Как? Удалить существующую позицию табуляции и добавить новую в измененной позиции:

```csharp
foreach(Paragraph para in doc.GetChildNodes(NodeType.Paragraph, true))
{
    if (para.ParagraphFormat.Style.StyleIdentifier >= StyleIdentifier.Toc1 &&
        para.ParagraphFormat.Style.StyleIdentifier <= StyleIdentifier.Toc9)
    {
        TabStop tab = para.ParagraphFormat.TabStops[0];
        para.ParagraphFormat.TabStops.RemoveByPosition(tab.Position);
        para.ParagraphFormat.TabStops.Add(tab.Position - 50, tab.Alignment, tab.Leader);
    }
}
```

Это как переставлять мебель в гостиной, пока она не станет идеальной. Мы доводим эти табуляторы до совершенства.

## Шаг 4: Сохраните измененный документ.

Зачем? Чтобы гарантировать, что все ваши труды будут сохранены и их можно будет просмотреть или поделиться.

Как? Сохраните документ под новым именем, чтобы сохранить оригинал нетронутым:

```csharp
// Сохраните измененный документ.
doc.Save(dataDir + "WorkingWithTableOfContent.ChangeTocTabStops.docx");
```

И вуаля! Теперь в вашем оглавлении позиции табуляции расположены именно там, где вам нужно.

## Заключение

Изменение позиций табуляции TOC в документе Word с помощью Aspose.Words for .NET становится простым, как только вы разбиваете его на части. Загрузив документ, определив абзацы TOC, изменив позиции табуляции и сохранив документ, вы можете добиться безупречного и профессионального вида. Помните, практика ведет к совершенству, поэтому продолжайте экспериментировать с различными позициями позиций табуляции, чтобы получить именно тот макет, который вам нужен.

## Часто задаваемые вопросы

### Можно ли изменять позиции табуляции для разных уровней оглавления по отдельности?
Да, можно! Просто проверьте каждый конкретный уровень TOC (Toc1, Toc2 и т. д.) и отрегулируйте соответствующим образом.

### Что делать, если в моем документе несколько оглавлений?
Код сканирует все абзацы, оформленные в стиле TOC, поэтому он изменит все TOC, присутствующие в документе.

### Можно ли добавить несколько позиций табуляции в запись оглавления?
 Конечно! Вы можете добавить столько позиций табуляции, сколько необходимо, отрегулировав`para.ParagraphFormat.TabStops` коллекция.

### Можно ли изменить выравнивание позиции табуляции и стиль заполнителя?
Да, при добавлении новой позиции табуляции можно указать различные выравнивания и стили отступов.

### Нужна ли мне лицензия для использования Aspose.Words для .NET?
 Да, вам нужна действующая лицензия для использования Aspose.Words for .NET после пробного периода. Вы можете получить[временная лицензия](https://purchase.aspose.com/temporary-license/) или[купить один](https://purchase.aspose.com/buy).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
