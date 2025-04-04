---
title: Работа с параметрами резюмирования
linktitle: Работа с параметрами резюмирования
second_title: API обработки документов Aspose.Words
description: Научитесь эффективно резюмировать документы Word с помощью Aspose.Words для .NET с помощью нашего пошагового руководства по интеграции моделей ИИ для быстрого получения аналитических данных.
weight: 10
url: /ru/net/ai-powered-document-processing/working-with-summarize-options/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Работа с параметрами резюмирования

## Введение

Когда дело доходит до обработки документов, особенно больших, резюмирование ключевых моментов может быть благословением. Если вы когда-либо обнаруживали себя просеивающим страницы текста в поисках иголки в стоге сена, вы оцените эффективность, которую предлагает резюмирование. В этом руководстве мы подробно рассмотрим, как использовать Aspose.Words для .NET для эффективного резюмирования ваших документов. Будь то для личного использования, презентаций на рабочем месте или академических начинаний, это руководство проведет вас шаг за шагом через весь процесс.

## Предпосылки

Прежде чем приступить к обобщению документов, убедитесь, что выполнены следующие предварительные условия:

1.  Библиотека Aspose.Words for .NET: Убедитесь, что вы загрузили библиотеку Aspose.Words. Вы можете взять ее здесь[здесь](https://releases.aspose.com/words/net/).
2. Среда .NET: В вашей системе должна быть настроена среда .NET (например, Visual Studio). Если вы новичок в .NET, не волнуйтесь; это довольно удобно для пользователя!
3. Базовые знания C#: Знакомство с программированием на C# будет полезным. Мы пройдем несколько шагов в коде, и понимание основ сделает это более плавным.
4. Ключ API для модели ИИ: поскольку мы используем генеративные языковые модели для резюмирования, вам понадобится ключ API, который вы можете установить в своей среде.

Выполнив эти предварительные условия, мы готовы приступить к работе!

## Импортные пакеты

Для начала давайте возьмем необходимые пакеты для нашего проекта. Нам понадобится Aspose.Words и любой пакет AI, который вы хотите использовать для реферирования. Вот как это можно сделать:

```csharp
using System.Text;
using Aspose.Words;
using System;
using Aspose.Words.AI;
```

Обязательно установите все необходимые пакеты NuGet с помощью диспетчера пакетов NuGet в Visual Studio.

Теперь, когда наша среда готова, давайте рассмотрим шаги по обобщению ваших документов с помощью Aspose.Words для .NET.

## Шаг 1: Настройка каталогов документов 

Прежде чем приступить к обработке документов, неплохо настроить каталоги. Такая организация поможет вам эффективно управлять входными и выходными файлами.

```csharp
// Ваш каталог документов
string MyDir = "YOUR_DOCUMENT_DIRECTORY"; 
// Ваш каталог ArtifactsDir
string ArtifactsDir = "YOUR_ARTIFACTS_DIRECTORY"; 
```

 Обязательно замените`"YOUR_DOCUMENT_DIRECTORY"` и`"YOUR_ARTIFACTS_DIRECTORY"` с реальными путями в вашей системе, где хранятся ваши документы и где вы хотите сохранить обобщенные файлы.

## Шаг 2: Загрузка документов 

Далее нам нужно загрузить документы, которые мы хотим резюмировать. Здесь мы переносим ваш текст в программу.

```csharp
Document firstDoc = new Document(MyDir + "Big document.docx");
Document secondDoc = new Document(MyDir + "Document.docx");
```

Здесь мы загружаем два документа —`Big document.docx` и`Document.docx`. Убедитесь, что эти файлы существуют в указанном вами каталоге.

## Шаг 3: Настройка модели ИИ 

Теперь пришло время поработать с нашей моделью ИИ, которая поможет нам обобщить документы. Сначала вам нужно будет установить свой ключ API. 

```csharp
string apiKey = Environment.GetEnvironmentVariable("API_KEY");
IAiModelText model = (IAiModelText)AiModel.Create(AiModelType.Gpt4OMini).WithApiKey(apiKey);
```

В этом примере мы используем OpenAI GPT-4 Mini. Убедитесь, что ваш ключ API правильно установлен в переменных среды, чтобы это работало правильно.

## Шаг 4: Подведение итогов по отдельному документу

А вот и самое интересное — подведение итогов! Для начала давайте подведем итоги по одному документу. 

```csharp
Document oneDocumentSummary = model.Summarize(firstDoc, new SummarizeOptions() { SummaryLength = SummaryLength.Short });
oneDocumentSummary.Save(ArtifactsDir + "AI.AiSummarize.One.docx");
```

Здесь мы просим модель ИИ подвести итог`firstDoc` с короткой длиной резюме. Резюмированный документ будет сохранен в указанном каталоге артефактов.

## Шаг 5: Обобщение нескольких документов

А что, если вам нужно обобщить несколько документов? Не беспокойтесь! Следующий шаг покажет вам, как с этим справиться.

```csharp
Document multiDocumentSummary = model.Summarize(new Document[] { firstDoc, secondDoc }, new SummarizeOptions() { SummaryLength = SummaryLength.Long });
multiDocumentSummary.Save(ArtifactsDir + "AI.AiSummarize.Multi.docx");
```

 В этом случае мы суммируем оба`firstDoc` и`secondDoc` и мы указали более длинную длину резюме. Ваш обобщенный вывод поможет вам уловить основные идеи без прочтения каждой детали.

## Заключение

И вот оно! Вы успешно резюмировали один или два документа с помощью Aspose.Words for .NET. Шаги, которые мы прошли, можно адаптировать для более крупных проектов или даже автоматизировать для различных задач по обработке документов. Помните, резюмирование может значительно сэкономить вам время и усилия, сохраняя при этом суть ваших документов. 

Хотите поиграться с кодом? Вперед! Прелесть этой технологии в том, что вы можете настроить ее под свои нужды. Не забывайте, что вы можете найти больше ресурсов и документации на[Документация Aspose.Words для .NET](https://reference.aspose.com/words/net/) и если у вас возникнут какие-либо проблемы,[Форум поддержки Aspose](https://forum.aspose.com/c/words/8/) всего в одном клике.

## Часто задаваемые вопросы

### Что такое Aspose.Words?
Aspose.Words — мощная библиотека, которая позволяет разработчикам выполнять операции с документами Word без необходимости установки Microsoft Word.

### Можно ли резюмировать PDF-файлы с помощью Aspose?
Aspose.Words в основном работает с документами Word. Для обобщения PDF-файлов вам может пригодиться Aspose.PDF.

### Нужно ли мне подключение к Интернету для запуска модели ИИ?
Да, поскольку модель ИИ требует вызова API, который зависит от активного подключения к Интернету.

### Существует ли пробная версия Aspose.Words?
 Конечно! Вы можете загрузить бесплатную пробную версию с сайта[здесь](https://releases.aspose.com/).

### Что делать, если у меня возникнут проблемы?
 Если у вас возникли какие-либо проблемы или есть вопросы, посетите[форум поддержки](https://forum.aspose.com/c/words/8/) для руководства.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
