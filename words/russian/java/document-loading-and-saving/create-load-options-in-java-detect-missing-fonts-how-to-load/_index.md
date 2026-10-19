---
category: general
date: 2026-02-18
description: Создайте параметры загрузки в Java для обнаружения отсутствующих шрифтов
  и узнайте, как загружать файлы DOCX с обратным вызовом предупреждения.
draft: false
keywords:
- create load options
- detect missing fonts
- how to load docx
- Aspose.Words warning callback
- Java document processing
language: ru
og_description: Создайте параметры загрузки в Java для обнаружения отсутствующих шрифтов
  и узнайте, как загружать файлы DOCX с обратным вызовом предупреждения.
og_title: Создание параметров загрузки в Java – обнаружение недостающих шрифтов и
  как загрузить DOCX
tags:
- java
- aspose-words
- document-processing
title: Создание параметров загрузки в Java – обнаружение отсутствующих шрифтов и как
  загрузить DOCX
url: /ru/java/document-loading-and-saving/create-load-options-in-java-detect-missing-fonts-how-to-load/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Создание Load Options в Java – Обнаружение отсутствующих шрифтов и загрузка DOCX

Когда‑то задавались вопросом, как **создать параметры загрузки**, которые не только читают DOCX, но и сообщают о недостающих шрифтах? Вы не одиноки. Отсутствующие шрифты могут превратить идеально оформленный документ в неразборчивый беспорядок, а их раннее обнаружение экономит часы отладки. В этом руководстве мы пройдём пошагово процесс **обнаружения отсутствующих шрифтов**, показывая при этом **как загрузить DOCX** с пользовательским обработчиком предупреждений.

## Что вы узнаете

- Как создать `LoadOptions` и настроить обработчик предупреждений.  
- Почему обратный вызов предупреждения необходим для отлова проблем замены шрифтов.  
- Точный код, необходимый для **безопасной загрузки DOCX** файла, плюс несколько практических советов для реальных проектов.  
- Обработку крайних случаев, например работу с другими типами предупреждений или загрузку PDF тем же способом.

Никакой внешней документации не требуется — всё, что нужно, находится здесь.

## Требования

- Java 17 или новее (API работает и в более старых версиях, но 17 — оптимальный вариант).  
- Библиотека Aspose.Words for Java, добавленная в ваш проект (`aspose-words-x.x.jar`).  
- Базовое понимание обработки исключений в Java.  

Если всё это у вас есть, приступаем.

![Diagram showing the flow of creating load options, setting a warning callback, and loading a DOCX file](/images/create-load-options-diagram.png){: .center-image alt="Диаграмма потока создания параметров загрузки"}

## Шаг 1: Создание Load Options (Как загрузить DOCX)

Первое, что нужно сделать, — **создать параметры загрузки**. Этот объект указывает Aspose.Words, как вести себя при открытии файла. Считайте его набором инструкций, которые вы передаёте библиотеке ещё до того, как она увидит DOCX.

```java
// Step 1: Instantiate LoadOptions
LoadOptions loadOptions = new LoadOptions();
```

Почему нельзя просто вызвать `new Document("file.docx")`? Потому что без `LoadOptions` вы теряете возможность реагировать на предупреждения — такие как отсутствие шрифтов — до того, как документ уже загружен, а это может быть слишком поздно для некоторых рабочих процессов.

## Шаг 2: Настройка обратного вызова предупреждения для обнаружения отсутствующих шрифтов

Теперь мы привязываем обратный вызов, который будет вызываться каждый раз, когда Aspose.Words сталкивается с ситуацией, о которой хочет вас предупредить. В нашем случае нас интересует `WarningType.FONT_SUBSTITUTION`.

```java
// Step 2: Register a warning callback
loadOptions.setWarningCallback(new IWarningCallback() {
    @Override
    public void warning(WarningInfo info) {
        // React only to font substitution warnings
        if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
            System.out.println("Missing font detected: " + info.getDescription());
        }
    }
});
```

Несколько замечаний:

- **Зачем нужен обратный вызов?** Он работает *во время* процесса загрузки, давая возможность записать лог или даже прервать операцию до полной материализации документа.  
- **Почему проверять `WarningType.FONT_SUBSTITUTION`?** Это точное значение enum, которое Aspose.Words использует для сценариев с отсутствующими шрифтами. Другие типы предупреждений (например, `TABLE_STRUCTURE`) можно фильтровать аналогично, если они нужны.  
- **Совет по производительности:** Обратный вызов лёгкий; избегайте тяжёлого ввода‑вывода внутри него. Если нужно писать в файл, собирайте сообщения в очередь и сбрасывайте их после загрузки.

## Шаг 3: Загрузка DOCX файла с настроенными параметрами

Когда параметры и обратный вызов готовы, можно наконец загрузить DOCX. Это часть, отвечающая на вопрос **как загрузить docx**, учитывая заданные предупреждения.

```java
// Step 3: Load the document using the configured LoadOptions
try {
    Document document = new Document("YOUR_DIRECTORY/input.docx", loadOptions);
    System.out.println("Document loaded successfully.");
} catch (Exception e) {
    System.err.println("Failed to load document: " + e.getMessage());
}
```

**Что происходит под капотом?** По мере чтения файла Aspose.Words проверяет каждую ссылку на шрифт. Если требуемый шрифт не установлен, вызывается наш ранее определённый обратный вызов предупреждения. Вы увидите вывод вроде:

```
Missing font detected: Font 'Calibri' is not installed. Substituted with 'Arial'.
Document loaded successfully.
```

Такой мгновенный отклик бесценен, когда вы обрабатываете партии файлов на сервере.

## Полный рабочий пример

Объединив всё вместе, получаем автономную программу, которую можно скопировать и вставить в свою IDE.

```java
import com.aspose.words.*;

public class DetectMissingFonts {
    public static void main(String[] args) {
        // 1️⃣ Create LoadOptions
        LoadOptions loadOptions = new LoadOptions();

        // 2️⃣ Register warning callback to detect missing fonts
        loadOptions.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) {
                if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                    System.out.println("Missing font: " + info.getDescription());
                }
            }
        });

        // 3️⃣ Load the DOCX using the configured options
        try {
            Document doc = new Document("YOUR_DIRECTORY/input.docx", loadOptions);
            System.out.println("DOCX loaded – you can now work with it.");
        } catch (Exception ex) {
            System.err.println("Error loading DOCX: " + ex.getMessage());
        }
    }
}
```

**Ожидаемый вывод**

```
Missing font: Font 'Times New Roman' is not installed. Substituted with 'Arial'.
DOCX loaded – you can now work with it.
```

Если в файле нет отсутствующих шрифтов, обратный вызов просто молчит, и появляется строка «DOCX loaded».

## Профессиональные советы и крайние случаи

| Ситуация | Что делать |
|-----------|------------|
| **Несколько отсутствующих шрифтов** | Обратный вызов срабатывает для каждого, поэтому вы получите строку на каждый шрифт. При необходимости соберите их в `List<String>` для последующего резюме. |
| **Нужно отлавливать и другие предупреждения** | Добавьте ветви `else if` для `WarningType.TABLE_STRUCTURE`, `WarningType.UNKNOWN_FILE_FORMAT` и т.д. |
| **Загрузка больших DOCX файлов** | Используйте `LoadOptions.setLoadFormat(LoadFormat.DOCX)`, чтобы подсказать формат и ускорить обнаружение. |
| **Запуск в веб‑сервисе** | Избегайте `System.out.println`; вместо этого внедрите логгер (`SLF4J`, `Log4j`) внутри обратного вызова. |
| **Шрифты устанавливаются во время выполнения** | После обнаружения отсутствующего шрифта можно программно загрузить его через `GraphicsEnvironment.registerFont(...)` и перезагрузить документ. |

## Почему этот подход лучше, чем только «try‑catch»

Многие разработчики просто оборачивают `new Document(...)` в блок try‑catch, надеясь, что исключение сообщит об отсутствующих шрифтах. К сожалению, Aspose.Words рассматривает замену шрифта как *предупреждение*, а не как ошибку, поэтому исключение не бросается. Создавая `LoadOptions` и привязывая обратный вызов предупреждения, вы получаете детальную информацию о проблемах со шрифтами без потери производительности.

## Следующие шаги

- **Обнаружение отсутствующих шрифтов в PDF** — тот же шаблон `LoadOptions` работает и для PDF, просто измените путь к файлу и формат загрузки.  
- **Автоматическая установка шрифтов** — соедините обратный вызов со скриптом, который скачивает недостающие шрифты из общего репозитория.  
- **Изучение других типов предупреждений** — Aspose.Words может предупреждать о устаревших тегах, сложных таблицах и многом другом.  

Экспериментируйте: замените конструктор `Document` на поток (`new Document(InputStream, loadOptions)`), если работаете с данными в памяти, или объединяйте несколько обратных вызовов с помощью композитного шаблона для масштабных конвейеров обработки.

---

### TL;DR

Мы показали, как **создать load options** в Java, настроить обратный вызов, **обнаруживающий отсутствующие шрифты**, и, наконец, **безопасно загрузить DOCX** файл. Всего за три лаконичных шага у вас есть переиспользуемый шаблон, который можно внедрить в любой проект Aspose.Words.

Есть вопросы о других форматах файлов или нужна помощь с настройкой обратного вызова под вашу среду? Оставляйте комментарий ниже, и счастливого кодинга!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}