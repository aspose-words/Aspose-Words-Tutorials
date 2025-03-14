---
title: Работа с моделью Google AI
linktitle: Работа с моделью Google AI
second_title: API обработки документов Aspose.Words
description: Повысьте эффективность обработки документов с помощью Aspose.Words для .NET и Google AI, чтобы легко создавать краткие резюме.
weight: 10
url: /ru/net/ai-powered-document-processing/working-with-google-ai-model/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Работа с моделью Google AI

## Введение

В этой статье мы рассмотрим, как пошагово суммировать документы с помощью Aspose.Words и моделей ИИ Google. Хотите ли вы сжать длинный отчет или извлечь информацию из нескольких источников, мы вам поможем.

## Предпосылки

Прежде чем погрузиться в практическую часть, давайте убедимся, что вы настроены на успех. Вот что вам понадобится:

1. Базовые знания C# и .NET: знакомство с концепциями программирования поможет вам лучше понять примеры.
   
2.  Библиотека Aspose.Words for .NET: Эта мощная библиотека позволяет вам легко создавать и обрабатывать документы Word. Вы можете[скачать здесь](https://releases.aspose.com/words/net/).

3. API-ключ для Google AI Model: Чтобы использовать AI-модели, вам нужен API-ключ для аутентификации. Сохраните его в безопасности в переменных среды.

4. Среда разработки: убедитесь, что у вас настроена рабочая среда .NET (Visual Studio или любая другая IDE).

5. Образец документа: для проверки реферирования вам понадобятся образцы документов Word (например, «Большой документ.docx», «Документ.docx»).

Теперь, когда мы рассмотрели основы, давайте погрузимся в код!

## Импортные пакеты

Для работы с Aspose.Words и интеграции моделей Google AI вам необходимо импортировать необходимые пространства имен. Вот как это можно сделать:

```csharp
using System.Text;
using Aspose.Words;
using System;
using Aspose.Words.AI;
```

Теперь, когда вы импортировали необходимые пакеты, давайте разберем процесс обобщения документов пошагово.

## Шаг 1: Настройка каталога документов

Прежде чем мы сможем обрабатывать документы, нам нужно указать, где находятся наши файлы. Этот шаг имеет решающее значение для обеспечения того, чтобы Aspose.Words мог получить доступ к документам.

```csharp
// Ваш каталог документов
string MyDir = "YOUR_DOCUMENT_DIRECTORY";
// Ваш каталог ArtifactsDir
string ArtifactsDir = "YOUR_ARTIFACTS_DIRECTORY";
```

 Заменять`"YOUR_DOCUMENT_DIRECTORY"` и`"YOUR_ARTIFACTS_DIRECTORY"` с реальными путями в вашей системе, где хранятся ваши документы. Это будет служить основой для чтения и сохранения документов.

## Шаг 2: Загрузка документов

Далее нам нужно загрузить документы, которые мы хотим суммировать. В этом случае вы загрузите два документа, которые мы указали ранее.

```csharp
Document firstDoc = new Document(MyDir + "Big document.docx");
Document secondDoc = new Document(MyDir + "Document.docx");
```

 The`Document` класс из Aspose.Words позволяет загружать файлы Word в память. Убедитесь, что имена файлов соответствуют реальным документам в вашем каталоге, иначе вы столкнетесь с ошибками «файл не найден»!

## Шаг 3: Получение ключа API

Чтобы использовать модель AI, вам нужно будет получить свой API Key. Он служит пропуском для доступа к службам Google AI.

```csharp
string apiKey = Environment.GetEnvironmentVariable("API_KEY");
```

Эта строка кода извлекает ключ API, который вы сохранили в переменных среды. Хорошей практикой является хранение конфиденциальной информации, такой как ключи API, вне вашего кода по соображениям безопасности.

## Шаг 4: Создание экземпляра модели ИИ

Теперь пришло время создать экземпляр модели ИИ. Здесь вы можете выбрать, какую модель использовать — в этом примере мы выбираем модель GPT-4 Mini.

```csharp
IAiModelText model = (IAiModelText)AiModel.Create(AiModelType.Gpt4OMini).WithApiKey(apiKey);
```

 Эта строка устанавливает модель ИИ, которую вы будете использовать для резюмирования документов. Обязательно проконсультируйтесь[документация](https://reference.aspose.com/words/net/) для получения подробной информации о различных моделях и их возможностях.

## Шаг 5: Подведение итогов по отдельному документу

Давайте сосредоточимся на подведении итогов первого документа. Мы можем выбрать здесь краткое резюме.

```csharp
Document oneDocumentSummary = model.Summarize(firstDoc, new SummarizeOptions() { SummaryLength = SummaryLength.Short });
oneDocumentSummary.Save(ArtifactsDir + "AI.AiSummarize.One.docx");
```

 На этом этапе мы используем`Summarize`метод из экземпляра модели AI для получения сгущения первого документа. Длина резюме установлена на короткую, но вы можете настроить ее в зависимости от ваших потребностей. Наконец, сжатый документ сохраняется в вашем каталоге артефактов.

## Шаг 6: Обобщение нескольких документов

Хотите резюмировать несколько документов одновременно? Aspose.Words тоже делает это легко!

```csharp
Document multiDocumentSummary = model.Summarize(new Document[] { firstDoc, secondDoc }, new SummarizeOptions() { SummaryLength = SummaryLength.Long });
multiDocumentSummary.Save(ArtifactsDir + "AI.AiSummarize.Multi.docx");
```

 Здесь мы звоним`Summarize` метод снова, но на этот раз с массивом документов. Это даст вам длинное резюме, которое инкапсулирует суть обоих файлов. Как и прежде, результат сохраняется в указанном каталоге артефактов.

## Заключение

И вот оно! Вы успешно настроили среду для резюмирования документов с помощью Aspose.Words for .NET и моделей ИИ Google. От загрузки документов до создания кратких резюмирований эти шаги обеспечивают оптимизированный подход к эффективному управлению большими объемами текста.

## Часто задаваемые вопросы

### Что такое Aspose.Words?
Aspose.Words — мощная библиотека для создания, изменения и преобразования документов Word с использованием .NET.

### Как получить ключ API для Google AI?
Обычно ключ API можно получить, зарегистрировавшись в Google Cloud и включив необходимые службы API.

### Могу ли я резюмировать несколько документов одновременно?
Да! Как было показано, вы можете передать массив документов в метод реферирования.

### Какие типы резюме я могу создавать?
В зависимости от ваших потребностей вы можете выбрать краткий, средний или длинный вариант резюме.

### Где я могу найти больше ресурсов Aspose.Words?
 Проверьте[документация](https://reference.aspose.com/words/net/) для получения дополнительных примеров и рекомендаций.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
