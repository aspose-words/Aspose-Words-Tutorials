---
title: Изменить элементы управления содержимым
linktitle: Изменить элементы управления содержимым
second_title: API обработки документов Aspose.Words
description: Узнайте, как изменять структурированные теги документов в Word с помощью Aspose.Words для .NET. Обновляйте текст, раскрывающиеся списки и изображения шаг за шагом.
weight: 10
url: /ru/net/programming-with-sdt/modify-content-controls/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Изменить элементы управления содержимым

## Введение

Если вы когда-либо работали с документами Word и вам нужно было изменить элементы управления структурированным содержимым — например, обычный текст, раскрывающиеся списки или изображения — с помощью Aspose.Words for .NET, вы попали по адресу! Структурированные теги документов (SDT) — это мощные инструменты, которые делают автоматизацию документов проще и гибче. В этом руководстве мы рассмотрим, как можно изменить эти SDT в соответствии с вашими потребностями. Независимо от того, обновляете ли вы текст, меняете ли вы раскрывающиеся списки или меняете изображения, это руководство проведет вас через этот процесс шаг за шагом.

## Предпосылки

Прежде чем мы перейдем к тонкостям изменения элементов управления содержимым, убедитесь, что у вас есть следующее:

1.  Aspose.Words for .NET Installed: Убедитесь, что у вас установлена библиотека Aspose.Words. Если нет, вы можете[скачать здесь](https://releases.aspose.com/words/net/).

2. Базовые знания C#: в этом руководстве предполагается, что вы знакомы с основными концепциями программирования на C#.

3. Среда разработки .NET: для запуска приложений .NET у вас должна быть настроена среда IDE, например Visual Studio.

4. Образец документа: Мы будем использовать образец документа Word с различными типами SDT. Вы можете использовать тот, что в примере, или создать свой собственный.

5.  Доступ к документации Aspose: для получения более подробной информации ознакомьтесь с[Документация Aspose.Words](https://reference.aspose.com/words/net/).

## Импорт пространств имен

Чтобы начать работать с Aspose.Words, вам нужно импортировать соответствующие пространства имен в ваш проект C#. Вот как это сделать:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Tables;
```

Эти пространства имен предоставят вам доступ к классам и методам, необходимым для управления структурированными тегами документов в документах Word.

## Шаг 1: Настройте путь к документу

 Перед внесением любых изменений вам необходимо указать путь к вашему документу. Заменить`"YOUR DOCUMENT DIRECTORY"` с фактическим путем хранения вашего документа.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Structured document tags.docx");
```

## Шаг 2: Перебор структурированных тегов документа

 Чтобы изменить SDT, вам сначала нужно пройтись по всем SDT в документе. Это делается с помощью`GetChildNodes` метод получения всех узлов типа`StructuredDocumentTag`.

```csharp
foreach (StructuredDocumentTag sdt in doc.GetChildNodes(NodeType.StructuredDocumentTag, true))
{
    // Изменить SDT в зависимости от их типа
}
```

## Шаг 3: Измените простые текстовые SDT

Если SDT — это простой текстовый тип, вы можете заменить его содержимое. Сначала очистите существующее содержимое, затем добавьте новый текст.

```csharp
if (sdt.SdtType == SdtType.PlainText)
{
    sdt.RemoveAllChildren();
    Paragraph para = sdt.AppendChild(new Paragraph(doc)) as Paragraph;
    Run run = new Run(doc, "new text goes here");
    para.AppendChild(run);
}
```

 Пояснение: Здесь,`RemoveAllChildren()`очищает существующее содержимое SDT. Затем мы создаем новый`Paragraph` и`Run` объект для вставки нового текста.

## Шаг 4: Измените SDT раскрывающегося списка

 Для выпадающего списка SDT вы можете изменить выбранный элемент, перейдя к`ListItems` коллекция. Здесь мы выбираем третий элемент в списке.

```csharp
if (sdt.SdtType == SdtType.DropDownList)
{
    SdtListItem secondItem = sdt.ListItems[2];
    sdt.ListItems.SelectedValue = secondItem;
}
```

Объяснение: Этот фрагмент кода выбирает элемент с индексом 2 (третий элемент) из выпадающего списка. Настройте индекс в соответствии с вашими потребностями.

## Шаг 5: Измените SDT изображения

Чтобы обновить изображение в SDT-файле изображений, вы можете заменить существующее изображение новым.

```csharp
if (sdt.SdtType == SdtType.Picture)
{
    Shape shape = (Shape) sdt.GetChild(NodeType.Shape, 0, true);
    if (shape.HasImage)
    {
        shape.ImageData.SetImage(ImagesDir + "Watermark.png");
    }
}
```

 Пояснение: Этот код проверяет, содержит ли фигура изображение, а затем заменяет его новым изображением, расположенным по адресу`ImagesDir`.

## Шаг 6: Сохраните измененный документ.

После внесения всех необходимых изменений сохраните измененный документ под новым именем, чтобы сохранить исходный документ нетронутым.

```csharp
doc.Save(dataDir + "WorkingWithSdt.ModifyContentControls.docx");
```

Пояснение: Это сохранит документ с новым именем файла, чтобы вы могли легко отличить его от оригинала.

## Заключение

Изменение элементов управления содержимым в документе Word с помощью Aspose.Words для .NET становится простым, как только вы понимаете необходимые шаги. Независимо от того, обновляете ли вы текст, меняете ли вы выпадающие списки или меняете изображения, Aspose.Words предоставляет надежный API для этих задач. Следуя этому руководству, вы сможете эффективно управлять и настраивать элементы управления структурированным содержимым вашего документа, делая ваши документы более динамичными и адаптированными к вашим потребностям.

## Часто задаваемые вопросы

1. Что такое структурированный тег документа (SDT)?

SDT — это элементы в документах Word, которые помогают управлять содержимым документа и форматировать его, например текстовые поля, раскрывающиеся списки или изображения.

2. Как добавить новый раскрывающийся элемент в SDT?

 Чтобы добавить новый элемент, используйте`ListItems` свойство и добавить новый`SdtListItem` в коллекцию.

3. Можно ли использовать Aspose.Words для удаления SDT из документа?

Да, вы можете удалить SDT, открыв узлы документа и удалив нужный SDT.

4. Как обрабатывать SDT, вложенные в другие элементы?

 Используйте`GetChildNodes` метод с соответствующими параметрами для доступа к вложенным SDT.

5. Что делать, если SDT, который мне нужно изменить, не отображается в документе?

Убедитесь, что SDT не скрыт и не защищен. Проверьте настройки документа и убедитесь, что ваш код правильно нацелен на тип SDT.


### Пример исходного кода для изменения элементов управления содержимым с помощью Aspose.Words для .NET 

```csharp
// Путь к каталогу ваших документов
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document(dataDir + "Structured document tags.docx");
foreach (StructuredDocumentTag sdt in doc.GetChildNodes(NodeType.StructuredDocumentTag, true))
{
	switch (sdt.SdtType)
	{
		case SdtType.PlainText:
		{
			sdt.RemoveAllChildren();
			Paragraph para = sdt.AppendChild(new Paragraph(doc)) as Paragraph;
			Run run = new Run(doc, "new text goes here");
			para.AppendChild(run);
			break;
		}
		case SdtType.DropDownList:
		{
			SdtListItem secondItem = sdt.ListItems[2];
			sdt.ListItems.SelectedValue = secondItem;
			break;
		}
		case SdtType.Picture:
		{
			Shape shape = (Shape) sdt.GetChild(NodeType.Shape, 0, true);
			if (shape.HasImage)
			{
				shape.ImageData.SetImage(ImagesDir + "Watermark.png");
			}
			break;
		}
	}
}
doc.Save(dataDir + "WorkingWithSdt.ModifyContentControls.docx");

```

Вот и все! Вы успешно изменили различные типы элементов управления содержимым в документе Word с помощью Aspose.Words для .NET.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
