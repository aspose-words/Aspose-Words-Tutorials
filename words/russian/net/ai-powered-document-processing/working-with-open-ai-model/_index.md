---
title: Работа с открытой моделью ИИ
linktitle: Работа с открытой моделью ИИ
second_title: API обработки документов Aspose.Words
description: Откройте для себя эффективное реферирование документов с помощью Aspose.Words для .NET с мощными моделями OpenAI. Погрузитесь в это всеобъемлющее руководство прямо сейчас.
weight: 10
url: /ru/net/ai-powered-document-processing/working-with-open-ai-model/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Работа с открытой моделью ИИ

## Введение

В современном цифровом мире контент — король. Независимо от того, являетесь ли вы студентом, бизнес-профессионалом или заядлым писателем, способность эффективно обрабатывать, резюмировать и генерировать документы бесценна. Вот где в игру вступает библиотека Aspose.Words для .NET, позволяющая вам управлять документами как профессионал. В этом всеобъемлющем руководстве мы углубимся в то, как использовать Aspose.Words в сочетании с моделями OpenAI для эффективного резюмирования документов. Готовы раскрыть свой потенциал управления документами? Давайте начнем!

## Предпосылки

Прежде чем мы засучим рукава и погрузимся в код, вам необходимо иметь под рукой несколько основных вещей:

### .NET Framework
Убедитесь, что вы работаете на версии .NET Framework, совместимой с Aspose.Words. Обычно .NET 5.0 и выше должны работать отлично.

### Библиотека Aspose.Words для .NET
 Вам нужно будет скачать и установить библиотеку Aspose.Words. Вы можете взять ее здесь[эта ссылка](https://releases.aspose.com/words/net/).

### API-ключ OpenAI
Для интеграции языковых моделей OpenAI для реферирования документов вам понадобится API Key. Вы можете получить его, зарегистрировавшись на платформе OpenAI и получив свой ключ из настроек учетной записи.

### IDE для разработки
Наличие интегрированной среды разработки (IDE), такой как Visual Studio, идеально подходит для разработки приложений .NET.

### Базовые знания программирования
Базовые знания C# и объектно-ориентированного программирования помогут вам легче усвоить концепции.

## Импортные пакеты

Теперь, когда у нас все готово, давайте импортируем наши пакеты. Откройте ваш проект Visual Studio и добавьте необходимые библиотеки. Вот как это можно сделать:

### Добавить пакет Aspose.Words

Вы можете добавить пакет Aspose.Words через NuGet Package Manager. Вот как это сделать:
- Перейдите в Инструменты -> Диспетчер пакетов NuGet -> Управление пакетами NuGet для решения.
- Найдите «Aspose.Words» и нажмите «Установить».

### Добавить системную среду

 Обязательно включите`System`Пространство имен для обработки переменных среды:
```csharp
using System.Text;
using Aspose.Words;
using System;
using Aspose.Words.AI;
```

### Добавить Aspose.Words

Затем включите пространство имен Aspose.Words в свой файл C#:
```csharp
using Aspose.Words;
```

### Добавить библиотеку OpenAI

Если вы используете библиотеку для взаимодействия с OpenAI (например, клиент REST), убедитесь, что вы также включили ее. Возможно, вам придется добавить ее через NuGet так же, как мы добавили Aspose.Words.

Теперь, когда мы подготовили нашу среду и импортировали необходимые пакеты, давайте разберем процесс реферирования документа пошагово.

## Шаг 1: Определите каталоги документов

Прежде чем начать работать с документами, вам необходимо настроить каталоги, в которых будут храниться ваши документы и артефакты:

```csharp
// Ваш каталог документов
string MyDir = "YOUR_DOCUMENT_DIRECTORY";
// Ваш каталог артефактов
string ArtifactsDir = "YOUR_ARTIFACTS_DIRECTORY";
```
 Это делает ваш код более управляемым, так как вы можете легко изменить пути при необходимости.`MyDir` где хранятся ваши входные документы, в то время как`ArtifactsDir` здесь вы будете сохранять сгенерированные резюме.

## Шаг 2: Загрузите документы

Далее вы загрузите документы, которые хотите резюмировать. Это просто с Aspose.Words:

```csharp
Document firstDoc = new Document(MyDir + "Big document.docx");
Document secondDoc = new Document(MyDir + "Document.docx");
```
Убедитесь, что названия ваших документов соответствуют тем, которые вы собираетесь использовать, в противном случае вы столкнетесь с ошибками!

## Шаг 3: Получите свой ключ API

Теперь, когда ваши документы загружены, пришло время получить ваш ключ API OpenAI. Вы получите его из переменных среды, чтобы сохранить его в безопасности:
```csharp
string apiKey = Environment.GetEnvironmentVariable("API_KEY");
```
Крайне важно безопасно управлять своим ключом API, чтобы защититься от несанкционированного доступа.

## Шаг 4: Создание экземпляра модели OpenAI

Имея готовый ключ API, вы можете создать экземпляр модели OpenAI. Для резюмирования документов мы будем использовать модель Gpt4OMini:

```csharp
IAiModelText model = (IAiModelText)AiModel.Create(AiModelType.Gpt4OMini).WithApiKey(apiKey);
```
Этот шаг по сути настраивает мозговой аппарат, необходимый для резюмирования ваших документов, предоставляя вам доступ к резюмированию на основе искусственного интеллекта.

## Шаг 5: Подведите итог отдельного документа

Давайте сначала подведем итоги первого документа. Вот тут-то и происходит волшебство:

```csharp
Document oneDocumentSummary = model.Summarize(firstDoc, new SummarizeOptions() { SummaryLength = SummaryLength.Short });
oneDocumentSummary.Save(ArtifactsDir + "AI.AiSummarize.One.docx");
```
 Здесь мы используем`Summarize` Метод модели.`SummaryLength.Short`параметр указывает, что нам нужна краткая сводка — идеально для быстрого обзора!

## Шаг 6: Обобщение нескольких документов

Чувствуете амбициозность? Вы можете резюмировать несколько документов одновременно. Посмотрите, как это просто:

```csharp
Document multiDocumentSummary = model.Summarize(new Document[] { firstDoc, secondDoc }, new SummarizeOptions() { SummaryLength = SummaryLength.Long });
multiDocumentSummary.Save(ArtifactsDir + "AI.AiSummarize.Multi.docx");
```
Эта функция особенно удобна для сравнения нескольких файлов. Возможно, вы готовитесь к встрече и вам нужны краткие заметки из нескольких длинных отчетов. Это ваш новый лучший друг!

## Заключение

Резюмирование документов с помощью Aspose.Words для .NET и OpenAI — это не просто полезный навык; это весьма расширяет возможности. Следуя этому руководству, вы превратили длинный, сложный текст в краткие резюме, сэкономив себе время и усилия. Независимо от того, обеспечиваете ли вы ясность для клиентов или готовитесь к важной презентации, теперь у вас есть инструменты, чтобы сделать это эффективно.

Так чего же вы ждете? С уверенностью погружайтесь в свои документы и позвольте технологиям сделать всю тяжелую работу!

## Часто задаваемые вопросы

### Что такое Aspose.Words для .NET?  
Aspose.Words для .NET — это мощная библиотека, которая позволяет разработчикам создавать, обрабатывать и преобразовывать документы программным способом.

### Нужен ли мне ключ API для OpenAI?  
Да, для доступа к возможностям резюмирования с использованием моделей вам необходим действительный ключ API OpenAI.

### Могу ли я резюмировать несколько документов одновременно?  
Конечно! Вы можете обобщить несколько документов за один вызов, что идеально подходит для расширенных отчетов.

### Как установить Aspose.Words?  
Вы можете установить его через диспетчер пакетов NuGet в Visual Studio, выполнив поиск по запросу «Aspose.Words».

### Существует ли бесплатная пробная версия Aspose.Words?  
 Да, вы можете получить доступ к бесплатной пробной версии Aspose.Words через их[веб-сайт](https://releases.aspose.com/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
