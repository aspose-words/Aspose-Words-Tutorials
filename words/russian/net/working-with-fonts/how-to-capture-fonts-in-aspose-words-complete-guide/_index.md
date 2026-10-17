---
category: general
date: 2026-01-05
description: Как быстро захватывать шрифты и обрабатывать отсутствующие шрифты с помощью
  Aspose.Words. Узнайте пошаговое решение с полным кодом на C#.
draft: false
keywords:
- how to capture fonts
- handle missing fonts
- Aspose.Words warnings
- font substitution callback
- missing font detection
language: ru
og_description: Как захватить шрифты в Aspose.Words и обработать отсутствующие шрифты.
  Следуйте этому подробному руководству для надёжной реализации на C#.
og_title: Как захватить шрифты в Aspose.Words – Полный учебник
tags:
- Aspose.Words
- C#
- Document Processing
title: Как захватить шрифты в Aspose.Words – Полное руководство
url: /ru/net/working-with-fonts/how-to-capture-fonts-in-aspose-words-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Как захватывать шрифты в Aspose.Words – Полное руководство

Когда‑то задавались вопросом **как захватывать шрифты** при загрузке Word‑документа с помощью Aspose.Words? Вы не одиноки. Отсутствующие шрифты могут вызвать тонкие сбои вёрстки, и без соответствующего предупреждения вы можете не заметить их, пока финальный PDF не выглядит некорректно. В этом руководстве мы покажем, как **захватывать шрифты** и обрабатывать их отсутствие, чтобы ваш вывод оставался пиксельно‑идеальным.

Мы пройдём через реальный сценарий, настроим обратный вызов предупреждений и предоставим готовый пример на C#. К концу вы поймёте, почему это важно, как реализовать решение и на что обратить внимание, когда шрифты исчезают из вашей среды.

## Что вы узнаете

- Как настроить **LoadOptions** для прослушивания предупреждений, связанных со шрифтами.  
- Роль **IWarningCallback** и **WarningInfo** в Aspose.Words.  
- Практические советы по отладке и журналированию отсутствующих шрифтов.  
- Полный, автономный пример кода, который можно скопировать в Visual Studio и запустить сразу.

**Предварительные требования:** .NET 6+ (или .NET Framework 4.7.2+), Aspose.Words for .NET, установленный через NuGet, и базовое знакомство с C#. Другие библиотеки не требуются.

---

## Шаг 1: Настройте LoadOptions для захвата шрифтов

Первое, что нам нужно, — это экземпляр **LoadOptions**. Этот объект указывает Aspose.Words, как вести себя при чтении документа. Присвоив пользовательский **IWarningCallback**, мы можем перехватывать любые предупреждения о подстановке шрифтов, возникающие во время загрузки.

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Loading;

// Prepare load options and attach a warning callback
LoadOptions loadOptions = new LoadOptions
{
    // The callback will be invoked for every warning Aspose.Words raises
    WarningCallback = new FontWarningCollector()
};
```

**Почему это важно:**  
Aspose.Words безмолвно заменяет отсутствующие шрифты на шрифт по умолчанию, если вы не попросите его сообщить об этом. Подключив обратный вызов, мы **захватываем информацию о шрифтах** сразу при загрузке, получая возможность вести журнал, заменять шрифты или даже прерывать операцию.

> **Совет:** Храните `loadOptions` как переиспользуемую переменную, если обрабатываете множество документов пакетно. Это избавит от повторного создания одного и того же обратного вызова.

---

## Шаг 2: Загрузите документ с настроенными параметрами

Теперь, когда обратный вызов установлен, загружаем документ. Конструктор **Document** принимает путь к файлу и **LoadOptions**, которые мы только что сконфигурировали.

```csharp
// Replace with the actual path to your .docx file
string inputPath = @"C:\Docs\input.docx";

Document doc = new Document(inputPath, loadOptions);
```

Если какой‑либо шрифт отсутствует, Aspose.Words сгенерирует предупреждение, которое получит наш `FontWarningCollector`. Сам документ всё равно загрузится, но у вас будет чёткая запись о том, какие шрифты были заменены.

---

## Шаг 3: Реализуйте FontWarningCollector — Обработка отсутствующих шрифтов

Суть **как захватывать шрифты** лежит в классе `FontWarningCollector`. Он реализует `IWarningCallback` и фильтрует только события `WarningType.FontSubstitution`.

```csharp
// Helper class that receives warning callbacks from Aspose.Words
class FontWarningCollector : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // We care exclusively about font substitution warnings
        if (info.Type == WarningType.FontSubstitution)
        {
            // Log the warning – you could also write to a file or database
            Console.WriteLine($"Font substitution detected: {info.Description}");
        }
    }
}
```

**Пояснение:**  
- `info.Type` сообщает нам категорию предупреждения. Проверяя `FontSubstitution`, мы **обрабатываем отсутствующие шрифты**, не засоряя вывод нерелевантными сообщениями (например, о устаревших функциях).  
- `info.Description` содержит человекочитаемое сообщение вроде “Font 'Comic Sans MS' was substituted with 'Arial'.” — это именно те данные, которые нужны для аудита вашего набора шрифтов.

> **Осторожно:** Если необходимо остановить обработку при отсутствии критически важного шрифта, бросьте исключение внутри блока `if` вместо простого вывода.

---

## Шаг 4: Проверьте вывод — Что ожидать

Запустите программу из консоли или IDE. Для каждого отсутствующего шрифта вы увидите строку вроде:

```
Font substitution detected: Font 'Times New Roman' was substituted with 'Arial'.
```

Если все шрифты присутствуют, обратный вызов молчит, и документ загружается без происшествий. Теперь можно безопасно продолжать сохранение, конвертацию или печать документа, будучи уверенным, что вы **захватили информацию о шрифтах**.

---

## Шаг 5: Полный рабочий пример (все части вместе)

Ниже полностью готовая к копированию и вставке программа. В ней присутствуют директивы `using`, реализация обратного вызова и небольшая демонстрация сохранения загруженного документа в PDF.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Loading;

namespace FontCaptureDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // 1️⃣ Configure load options with our warning collector
            LoadOptions loadOptions = new LoadOptions
            {
                WarningCallback = new FontWarningCollector()
            };

            // 2️⃣ Path to the source DOCX (adjust as needed)
            string inputPath = @"C:\Docs\input.docx";

            // 3️⃣ Load the document – any missing fonts trigger our callback
            Document doc = new Document(inputPath, loadOptions);

            // 4️⃣ Optional: Save as PDF to see the final result
            string outputPdf = @"C:\Docs\output.pdf";
            doc.Save(outputPdf);

            Console.WriteLine("Document processed successfully.");
        }
    }

    // 5️⃣ Our custom warning collector – handles missing fonts
    class FontWarningCollector : IWarningCallback
    {
        public void Warning(WarningInfo info)
        {
            if (info.Type == WarningType.FontSubstitution)
            {
                // You could log to a file, raise an event, or collect into a list
                Console.WriteLine($"Font substitution detected: {info.Description}");
            }
        }
    }
}
```

**Запуск кода:**  
1. Создайте новый консольный проект (`dotnet new console -n FontCaptureDemo`).  
2. Добавьте пакет Aspose.Words (`dotnet add package Aspose.Words`).  
3. Замените сгенерированный `Program.cs` на приведённый выше фрагмент.  
4. Поместите DOCX, который намеренно ссылается на шрифт, которого у вас нет (например, “Papyrus”).  
5. Выполните (`dotnet run`). Смотрите консоль на сообщения о подстановке, затем откройте `output.pdf`, чтобы проверить вёрстку.

---

## Часто задаваемые вопросы и особые случаи

### Как получить список отсутствующих шрифтов позже?

Сохраните сообщения в `List<string>` внутри `FontWarningCollector` и откройте их через свойство. Так вы сможете записать список в лог‑файл после обработки множества документов.

### Работает ли это с зашифрованными или защищёнными паролем файлами?

Да, но необходимо также передать пароль через `LoadOptions.Password`. Обратный вызов предупреждений работает так же после расшифровки документа.

### Можно ли заменить отсутствующий шрифт собственным fallback‑ом?

Безусловно. Внутри метода `Warning` можно вызвать `doc.FontSettings.SubstitutionSettings.FontSubstitutes.AddMissing("MissingFont", "MyFallback")`. Это делает подстановку детерминированной.

### Влияет ли это на производительность?

Накладные расходы минимальны — по сути, один вызов метода на каждое предупреждение. При обработке тысяч документов влияние пренебрежимо мало по сравнению с затратами ввода‑вывода при загрузке каждого файла.

---

## Заключение

Мы рассмотрели **как захватывать шрифты** в Aspose.Words, показали, как **обрабатывать отсутствующие шрифты** с помощью чистого обратного вызова предупреждений, и предоставили полностью готовый пример. Подключив этот шаблон к вашему конвейеру обработки документов, вы больше никогда не будете удивлены тихой подстановкой шрифтов.

Готовы к следующему шагу? Попробуйте расширить коллектор для записи JSON‑логов, интеграции с панелью мониторинга или автоматического внедрения недостающих шрифтов в итоговый PDF. Возможностей бесконечно много, а теперь у вас есть надёжная основа.

Счастливого кодинга! 🚀

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}