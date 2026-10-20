---
category: general
date: 2026-03-25
description: Создайте пользовательскую модель ИИ для редактирования документов Word
  — узнайте, как сделать текст более формальным, заменить текст абзаца и переписать
  абзац в Word с помощью Aspose.Words AI.
draft: false
keywords:
- create custom ai model
- make text more formal
- replace paragraph text
- edit paragraph with ai
- rewrite word paragraph
language: ru
og_description: Создайте пользовательскую модель ИИ для редактирования документов
  Word. Узнайте, как сделать текст более формальным, заменить текст абзаца и переписать
  абзац Word с помощью Aspose.Words AI.
og_title: Создайте пользовательскую модель ИИ – редактирование абзацев Word в Java
tags:
- Aspose.Words
- Java
- AI integration
title: Создать пользовательскую AI‑модель — редактировать абзацы Word в Java
url: /ru/java/ai-machine-learning-integration/create-custom-ai-model-edit-word-paragraphs-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Создать пользовательскую AI‑модель – редактировать абзацы Word в Java

Когда‑нибудь вам нужно было **create custom AI model**, который может отшлифовать абзац в файле Word? Возможно, у вас есть набор контрактов, звучащих слишком неформально, и вы хотите сделать текст более формальным одной строкой кода. Хорошая новость в том, что вы можете сделать именно это — без внешних сервисов, без тяжёлых SDK, только Aspose.Words for Java и совместимый с OpenAI endpoint.

В этом руководстве мы пройдём каждый шаг, необходимый для **create custom AI model**, подключим его к локальному LLM‑серверу и затем используем для *replace paragraph text* более формальной версией. К концу у вас будет исполняемая Java‑программа, которая **edit paragraph with AI**, переписывает абзац Word и сохраняет результат на диск. Без лишних деталей, только практическое решение, которое вы можете скопировать‑вставить в свой проект.

> **Что вам понадобится**  
> • Java 17 или новее (код компилируется и в более ранних версиях, но 17 — оптимальный вариант)  
> • Aspose.Words for Java 23.9 (или последняя версия)  
> • Запущенный OpenAI‑compatible LLM сервер (например, Ollama, LocalAI), прослушивающий `http://localhost:8000/v1`  
> • Входной документ Word (`input.docx`), размещённый в папке, которой вы управляете  

Если вам интересно *почему стоит создавать пользовательскую модель* вместо прямого вызова OpenAI, ответ — гибкость: вы контролируете endpoint, можете менять модели без изменения кода и держите любые API‑ключи вне репозитория исходного кода. Давайте начнём.

---

## Создать пользовательскую AI‑модель – настройка и конфигурация

Сначала нам нужно сообщить Aspose.Words, где находится наш LLM. Класс `AiModelEndpoint` хранит URL и необязательный API‑key. Поскольку мы используем локальный сервер, ключ может быть пустой строкой, но параметр обязателен.

```java
import com.aspose.words.ai.*;

public class LlmDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Define the LLM endpoint (OpenAI‑compatible)
        AiModelEndpoint llmEndpoint = new AiModelEndpoint(
                "http://localhost:8000/v1",   // URL of your LLM server
                "my-api-key");                // API key if required
```

> **Совет:** Если вы когда‑нибудь переключитесь на размещённую модель (например, Azure OpenAI), просто измените URL и ключ — никаких других изменений кода не требуется.

---

## Загрузить документ Word

Теперь мы загружаем исходный файл в память. `Document` может читать `.docx`, `.doc`, `.rtf` и многие другие форматы, но в этом примере мы используем `.docx`.

```java
        // Step 2: Load the source Word document
        Document document = new Document("YOUR_DIRECTORY/input.docx");
```

Убедитесь, что `YOUR_DIRECTORY` указывает на реальную папку; иначе вы получите `FileNotFoundException`. В реальном приложении путь можно передать как аргумент командной строки или прочитать из конфигурационного файла.

---

## Инициализировать пользовательскую AI‑модель

Мы создаём `AiModel` типа `CUSTOM` и передаём ему endpoint, определённый ранее. Это заставляет Aspose.Words направлять все AI‑вызовы через наш собственный сервер.

```java
        // Step 3: Create a custom AI model that uses the endpoint
        AiModel llmModel = new AiModel(AiModelType.CUSTOM, llmEndpoint);
```

Внутри Aspose.Words создаёт небольшой HTTP‑клиент, который общается с LLM по стандартной схеме OpenAI chat/completion. Поэтому endpoint должен быть *OpenAI‑compatible*.

---

## Получить и переписать первый абзац

Здесь мы действительно **make text more formal**. Мы получаем первый абзац, отправляем его исходный текст модели с подсказкой и получаем отредактированную версию.

```java
        // Step 4: Retrieve the first paragraph and ask the model to rewrite it
        Paragraph firstParagraph = document.getFirstSection()
                                            .getBody()
                                            .getParagraphs()
                                            .get(0);
        String rewrittenText = llmModel.editText(
                firstParagraph.getText(),
                "Make it more formal");
```

Второй аргумент (`"Make it more formal"`) — это инструкция, которую мы передаём модели. Вы можете заменить её любой директивой — **replace paragraph text**, **summarize**, **translate** и т.д. Метод возвращает обычную строку, которую мы позже вставим обратно в документ.

> **Почему это работает:** `editText` отправляет JSON‑payload вида `{ "model": "...", "messages": [{ "role":"user", "content":"<text>\nMake it more formal"}] }`. LLM видит оригинальный абзац и инструкцию, затем отвечает отредактированным текстом.

---

## Заменить оригинальное содержимое абзаца

Теперь мы **replace paragraph text** внутри модели объектов Word. Мы очищаем любые существующие `Run` (низкоуровневые куски текста) и вставляем новый `Run`, содержащий строку, сгенерированную AI.

```java
        // Step 5: Replace the original paragraph content with the rewritten text
        firstParagraph.removeAllChildren();
        firstParagraph.appendChild(new Run(document, rewrittenText));
```

Будьте осторожны и не вызывайте `firstParagraph.setText()` — этот метод удалит всё форматирование. Использование `Run` сохраняет стиль абзаца (заголовок, маркер и т.д.), заменяя только сами символы.

---

## Сохранить отредактированный документ

Наконец, мы записываем изменённый документ обратно на диск. Вы можете перезаписать оригинальный файл или, как в этом примере, создать новую копию.

```java
        // Step 6: Save the edited document
        document.save("YOUR_DIRECTORY/output.docx");
    }
}
```

Когда вы откроете `output.docx`, первый абзац будет звучать значительно более формально. Если LLM не выполнил инструкцию точно, вы можете скорректировать подсказку или попробовать другую версию модели.

---

## Полный рабочий пример

Ниже приведена полная программа — скопируйте её в `LlmDemo.java`, скорректируйте пути и запустите с помощью `javac` + `java`.

```java
import com.aspose.words.*;
import com.aspose.words.ai.*;

public class LlmDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Define the LLM endpoint (OpenAI‑compatible)
        AiModelEndpoint llmEndpoint = new AiModelEndpoint(
                "http://localhost:8000/v1",   // URL of your LLM server
                "my-api-key");                // API key if required

        // Step 2: Load the source Word document
        Document document = new Document("YOUR_DIRECTORY/input.docx");

        // Step 3: Create a custom AI model that uses the endpoint
        AiModel llmModel = new AiModel(AiModelType.CUSTOM, llmEndpoint);

        // Step 4: Retrieve the first paragraph and ask the model to rewrite it
        Paragraph firstParagraph = document.getFirstSection()
                                            .getBody()
                                            .getParagraphs()
                                            .get(0);
        String rewrittenText = llmModel.editText(
                firstParagraph.getText(),
                "Make it more formal");

        // Step 5: Replace the original paragraph content with the rewritten text
        firstParagraph.removeAllChildren();
        firstParagraph.appendChild(new Run(document, rewrittenText));

        // Step 6: Save the edited document
        document.save("YOUR_DIRECTORY/output.docx");
    }
}
```

**Ожидаемый результат:** Откройте `output.docx`, и вы увидите преобразованный оригинальный абзац. Например, неформальное предложение «We’ll get the thing done soon.» может стать «We shall complete the task promptly.» Точная формулировка зависит от используемой модели.

---

## Часто задаваемые вопросы и особые случаи

### Что если в документе несколько разделов?

Приведённый код изменяет только *первый* абзац *первого* раздела. Чтобы **edit paragraph with AI** по всему файлу, пройдитесь в цикле по `document.getSections()` и затем по каждому `section.getBody().getParagraphs()`. Не забудьте пропускать пустые абзацы, иначе LLM получит пустую строку и ничего не вернёт.

### Как обработать большие абзацы, превышающие лимит токенов?

Большинство LLM ограничивают ввод примерно 4 000 токенами. Если абзац необычно длинный, разбейте его на более мелкие части перед вызовом `editText`. Вы можете переиспользовать тот же экземпляр `AiModel`; просто учитывайте ограничения по скорости запросов на вашем локальном сервере.

### Можно ли использовать другую инструкцию, например “summarize” или “translate to French”?

Конечно. Второй аргумент `editText` свободный. Для резюме можно передать `"Summarize in one sentence"`. Для перевода — `"Translate to French, keep the tone formal"` тоже подойдёт. Такая гибкость позволяет **replace paragraph text** в разных сценариях без изменения кода.

### Сохраняет ли модель стили абзаца (шрифты, цвета)?

Поскольку мы заменяем только `Run` внутри того же объекта `Paragraph`, существующие стили (уровень заголовка, маркированный список, отступ) остаются неизменными. Если нужно изменить сам стиль, можно манипулировать `Paragraph.getParagraphFormat()` после замены.

### Что если мой LLM‑сервер требует HTTPS с самоподписанным сертификатом?

`AiModelEndpoint` принимает URL с `https://`. Если сертификат не доверенный, необходимо настроить SSL‑контекст Java, чтобы доверять ему, или запустить сервер с действительным сертификатом. Эта настройка выходит за рамки данного руководства, но хорошо описана в руководствах по Java SSL.

---

## Советы по интеграции в продакшн

| Совет | Почему это важно |
|-----|----------------|
| **Кешировать endpoint** | Создание `AiModelEndpoint` при каждом запросе добавляет накладные расходы. |
| **Пакетные правки** | Если у вас много абзацев, отправляйте их одним запросом (например, JSON‑массив) для снижения задержки. |
| **Проверять вывод LLM** | Всегда проверяйте возвращённую строку на null или пустое значение перед вставкой. |
| **Логировать подсказки и ответы** | Полезно для отладки и соответствия требованиям, когда вы переписываете юридический текст. |
| **Корректный откат** | Если LLM недоступен, откатывайтесь к оригинальному абзацу или простой эвристической правке. |

---

## Заключение

Мы показали, как **create custom AI model** с помощью Aspose.Words, подключить её к OpenAI‑compatible endpoint и затем **edit paragraph with AI**, чтобы **make text more formal**. Следуя шести шагам — определить endpoint, загрузить документ, инициализировать модель,

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}