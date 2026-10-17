---
category: general
date: 2026-03-04
description: Как настроить LLM для Document AI и заменить текст в DOCX с помощью ИИ —
  пошаговое руководство с полным кодом на Java.
draft: false
keywords:
- how to configure llm
- replace text in docx
- how to replace text
- how to use document ai
- replace phrase with ai
language: ru
og_description: Как настроить LLM для Document AI и заменить текст в DOCX с помощью
  ИИ — полное руководство с исполняемым кодом на Java.
og_title: Как настроить LLM – заменить текст в DOCX с помощью ИИ
tags:
- LLM
- Document AI
- Java
- DOCX
title: How to Configure LLM – Replace Text in DOCX with AI
url: /ru/java/ai-machine-learning-integration/how-to-configure-llm-replace-text-in-docx-with-ai/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Как настроить LLM – Замена текста в DOCX с помощью ИИ

Когда‑то задумывались **как настроить LLM**, чтобы он мог редактировать Word‑файл за вас? Вы не одиноки. Многие разработчики сталкиваются с проблемой, когда нужно программно заменить фразу внутри `.docx`, не открывая Microsoft Word. Хорошие новости? С локальным LLM и небольшим обёрткой Document AI вы можете заменить текст в файле DOCX всего в несколько строк Java.

В этом руководстве мы пройдём весь процесс: от настройки соединения с LLM, загрузки DOCX, до использования **Document AI** для замены целевой фразы. К концу вы получите самостоятельный, готовый к запуску пример, который можно добавить в любой проект Maven или Gradle. Без внешних API‑ключей, без облачных расходов — только ваша собственная модель, слушающая `http://localhost:8080/v1`.

> **Быстрый результат:** Если у вас уже есть локальный LLM (например, Llama 3 или Mistral), предоставляющий совместимый с OpenAI endpoint, код ниже работает сразу же.

---

![Схема настройки LLM для Document AI](/images/configure-llm-diagram.png){: .center-image alt="схема настройки llm"}

## Что понадобится

- **Java 17** (или любой современный JDK)  
- **Локальный LLM**, предоставляющий OpenAI‑подобный `/v1` endpoint (например, Ollama, LMStudio)  
- **Java‑библиотека Document AI** (предположим `com.example:document-ai:1.2.0` в Maven Central)  
- Пример файла DOCX (`input.docx`), размещённый в известной папке  

Если чего‑то не хватает, быстро запустите Ollama:

```bash
ollama serve &
ollama run llama3
```

Это запустит сервер на `http://localhost:8080/v1`, готовый принимать запросы.

---

## Как настроить LLM для Document AI

Первое, что мы делаем, — указываем клиенту `DocumentAi`, где находится модель и какую модель использовать. Это шаг **как настроить LLM**, который многие руководства упускают.

```java
// Step 1: Set up the LLM connection details
AiModelConfig modelConfig = new AiModelConfig();
modelConfig.setBaseUrl("http://localhost:8080/v1");   // Local server address
modelConfig.setApiKey("dummy");                       // Not needed for local models, but the client expects a value
modelConfig.setModelName("local-llm");                // Replace with your model's identifier
```

*Почему это важно:*  
Объект `AiModelConfig` абстрагирует детали HTTP, позволяя `DocumentAi` сосредоточиться на содержимом. Если вы когда‑нибудь переключитесь на облачного провайдера, нужно будет изменить только `baseUrl` и `apiKey` — остальной код останется без изменений.

---

## Загрузка и подготовка документа DOCX

Далее мы загружаем Word‑файл в память. Класс `Document` работает как с `.docx`, так и с `.pdf`, но здесь нас интересует только DOCX.

```java
// Step 2: Load the DOCX you want to edit
Path docPath = Paths.get("YOUR_DIRECTORY/input.docx");
Document inputDocument = new Document(docPath.toFile());
```

*Совет:* Используйте абсолютный путь во время отладки, чтобы избежать неожиданного «файл не найден». Когда убедитесь, что всё работает, переключитесь обратно на относительный путь для переносимости.

---

## Замена текста в DOCX с помощью ИИ

Теперь переходим к главному — **как заменить текст** в файле DOCX с помощью ИИ. Метод `replaceText` отправляет содержимое документа в LLM, просит выполнить замену и возвращает изменённый текст.

```java
// Step 3: Initialise the Document AI client
DocumentAi documentAi = new DocumentAi(modelConfig);

// Step 4: Ask the LLM to replace the target phrase
String oldPhrase = "old phrase";
String newPhrase = "new phrase";

String revisedText = documentAi.replaceText(
        inputDocument,
        oldPhrase,
        newPhrase
);
```

*Что происходит «за кулисами»?*  
`DocumentAi` сериализует DOCX в обычный текст, формирует запрос вида:

> “В следующем документе замените каждое вхождение ‘old phrase’ на ‘new phrase’ и верните только обновлённый текст.”

LLM обрабатывает запрос и возвращает модифицированное содержимое. Такой подход работает даже когда фраза разбита на несколько ранов или абзацев — то, что часто упускает простая замена строк.

---

## Проверка и вывод изменённого текста

Наконец, выводим ИИ‑изменённый текст в консоль. В реальном приложении, скорее всего, вы запишете результат обратно в новый DOCX, но вывод в консоль позволяет быстро проверить результат.

```java
// Step 5: Show the AI‑revised output
System.out.println("AI‑revised text:");
System.out.println("-----------------------------------");
System.out.println(revisedText);
```

**Ожидаемый вывод** (при условии, что исходный DOCX содержал «This is the old phrase we want to change.»):

```
AI‑revised text:
-----------------------------------
This is the new phrase we want to change.
```

Если вы видите новую фразу, поздравляем — **вы только что научились использовать Document AI для замены фразы с помощью ИИ**.

---

## Полный рабочий пример

Объединив всё вместе, получаем полностью готовый к запуску Java‑класс. Скопируйте‑вставьте его в `src/main/java/com/example/ReplaceInDocx.java`.

```java
package com.example;

import com.example.documentai.AiModelConfig;
import com.example.documentai.DocumentAi;
import com.example.documentai.Document;

import java.nio.file.Path;
import java.nio.file.Paths;

/**
 * Demonstrates how to configure LLM, load a DOCX, and replace a phrase using Document AI.
 */
public class ReplaceInDocx {

    public static void main(String[] args) {
        // 1️⃣ Configure the local LLM connection
        AiModelConfig modelConfig = new AiModelConfig();
        modelConfig.setBaseUrl("http://localhost:8080/v1");
        modelConfig.setApiKey("dummy");               // Not required for local models
        modelConfig.setModelName("local-llm");        // Change if needed

        // 2️⃣ Load the DOCX you want to modify
        Path docPath = Paths.get("YOUR_DIRECTORY/input.docx");
        Document inputDocument = new Document(docPath.toFile());

        // 3️⃣ Create the Document AI client using the configuration
        DocumentAi documentAi = new DocumentAi(modelConfig);

        // 4️⃣ Replace the target phrase with the new phrase using the AI model
        String oldPhrase = "old phrase";
        String newPhrase = "new phrase";

        String revisedText = documentAi.replaceText(
                inputDocument,
                oldPhrase,
                newPhrase
        );

        // 5️⃣ Output the AI‑revised text
        System.out.println("AI‑revised text:");
        System.out.println("-----------------------------------");
        System.out.println(revisedText);
    }
}
```

### Как запустить

```bash
# Compile
mvn clean compile

# Execute
mvn exec:java -Dexec.mainClass="com.example.ReplaceInDocx"
```

Убедитесь, что сервер LLM запущен перед запуском программы; иначе вы получите ошибку тайм‑аута соединения.

---

## Крайние случаи и распространённые подводные камни

| Ситуация | На что обратить внимание | Предлагаемое решение |
|----------|--------------------------|----------------------|
| **Фраза не найдена** | LLM возвращает оригинальный текст без изменений. | Проверьте орфографию и регистр; при необходимости добавьте `ignoreCase:true` в запрос, если ваш обёртка поддерживает это. |
| **Большие документы (>5 МБ)** | Размер запроса может превысить лимит токенов модели. | Разбейте DOCX на секции, обработайте каждую отдельно, затем объедините результаты. |
| **Локальный LLM возвращает ошибки** | Часто из‑за несоответствия имени модели. | Убедитесь, что имя модели в UI LLM (`ollama list`) совпадает с тем, что указано в `modelConfig.setModelName`. |
| **Unicode‑символы искажаются** | Проблемы кодировки при чтении DOCX. | Убедитесь, что ваша JVM использует UTF‑8 (добавьте `-Dfile.encoding=UTF-8` в параметры JVM). |

---

## Следующие шаги

Теперь, когда вы знаете **как заменить текст в DOCX** с помощью ИИ, можете изучить:

- **Как использовать Document AI** для более сложных задач, таких как извлечение таблиц или сохранение стилей.  
- **Замена фразы с ИИ** в PDF, просто заменив аргумент конструктора `Document`.  
- **Пакетная обработка**: перебрать каталог DOCX‑файлов и применить ту же замену.  

Все эти сценарии опираются на одну и ту же основу `AiModelConfig` и `DocumentAi`, так что начинать с нуля не придётся.

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}