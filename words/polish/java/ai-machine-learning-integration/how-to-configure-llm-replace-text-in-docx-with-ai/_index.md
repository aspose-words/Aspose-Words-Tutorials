---
category: general
date: 2026-03-04
description: Jak skonfigurować LLM dla Document AI i zamienić tekst w pliku DOCX przy
  użyciu AI – przewodnik krok po kroku z pełnym kodem Java.
draft: false
keywords:
- how to configure llm
- replace text in docx
- how to replace text
- how to use document ai
- replace phrase with ai
language: pl
og_description: How to configure LLM for Document AI and replace text in DOCX using
  AI – complete guide with runnable Java code.
og_title: Jak skonfigurować LLM – zamień tekst w DOCX przy pomocy AI
tags:
- LLM
- Document AI
- Java
- DOCX
title: How to Configure LLM – Replace Text in DOCX with AI
url: /pl/java/ai-machine-learning-integration/how-to-configure-llm-replace-text-in-docx-with-ai/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak skonfigurować LLM – zamiana tekstu w DOCX przy użyciu AI

Zastanawiałeś się kiedyś **jak skonfigurować LLM**, aby mógł edytować plik Word za Ciebie? Nie jesteś jedyny. Wielu programistów napotyka problem, gdy muszą programowo zamienić frazę w pliku `.docx` bez otwierania Microsoft Word. Dobra wiadomość? Dzięki lokalnemu LLM i małej nakładce Document AI możesz wymienić tekst w pliku DOCX w zaledwie kilku linijkach Javy.

W tym tutorialu przeprowadzimy Cię przez cały proces: od podłączenia LLM, wczytania DOCX, po użycie **Document AI** do zamiany docelowej frazy. Po zakończeniu będziesz mieć samodzielny, gotowy do uruchomienia przykład, który możesz wkleić do dowolnego projektu Maven lub Gradle. Bez zewnętrznych kluczy API, bez opłat w chmurze — tylko Twój własny model nasłuchujący na `http://localhost:8080/v1`.

> **Szybka wygrana:** Jeśli już masz lokalny LLM (np. Llama 3 lub Mistral) udostępniający kompatybilny z OpenAI endpoint, poniższy kod działa od razu.

---

![Diagram jak skonfigurować LLM dla Document AI](/images/configure-llm-diagram.png){: .center-image alt="jak skonfigurować diagram llm"}

## Czego będziesz potrzebować

- **Java 17** (lub dowolny nowoczesny JDK)  
- **lokalny LLM** udostępniający endpoint w stylu OpenAI `/v1` (np. Ollama, LMStudio)  
- **Biblioteka Document AI Java** (zakładając `com.example:document-ai:1.2.0` w Maven Central)  
- Przykładowy plik DOCX (`input.docx`) umieszczony w znanym folderze  

Jeśli brakuje Ci któregoś z nich, szybko uruchom Ollama:

```bash
ollama serve &
ollama run llama3
```

To uruchomi serwer na `http://localhost:8080/v1` gotowy do przyjmowania żądań.

---

## Jak skonfigurować LLM dla Document AI

Pierwszą rzeczą, którą robimy, jest poinformowanie klienta `DocumentAi`, gdzie znaleźć model i którego modelu użyć. To jest krok **jak skonfigurować LLM**, który wiele tutoriali pomija.

```java
// Step 1: Set up the LLM connection details
AiModelConfig modelConfig = new AiModelConfig();
modelConfig.setBaseUrl("http://localhost:8080/v1");   // Local server address
modelConfig.setApiKey("dummy");                       // Not needed for local models, but the client expects a value
modelConfig.setModelName("local-llm");                // Replace with your model's identifier
```

*Dlaczego to ważne:*  
Obiekt `AiModelConfig` ukrywa szczegóły HTTP, pozwalając `DocumentAi` skupić się na treści. Jeśli kiedykolwiek przełączysz się na dostawcę w chmurze, zmienisz tylko `baseUrl` i `apiKey` — reszta kodu pozostaje niezmieniona.

---

## Wczytaj i przygotuj dokument DOCX

Następnie wczytujemy plik Word do pamięci. Klasa `Document` obsługuje zarówno `.docx`, jak i `.pdf` pod maską, ale tutaj interesuje nas tylko DOCX.

```java
// Step 2: Load the DOCX you want to edit
Path docPath = Paths.get("YOUR_DIRECTORY/input.docx");
Document inputDocument = new Document(docPath.toFile());
```

*Wskazówka:* Używaj ścieżki bezwzględnej podczas debugowania, aby uniknąć niespodzianki „plik nie znaleziony”. Gdy będziesz pewny, przełącz się z powrotem na ścieżkę względną dla przenośności.

---

## Zamień tekst w DOCX przy użyciu AI

Nadszedł najważniejszy fragment tutorialu — **jak zamienić tekst** w pliku DOCX przy pomocy AI. Metoda `replaceText` wysyła zawartość dokumentu do LLM, prosi o wykonanie zamiany i zwraca zmodyfikowany tekst.

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

*Co się dzieje w tle?*  
`DocumentAi` serializuje DOCX do zwykłego tekstu, tworzy prompt taki jak:

> “W następującym dokumencie zamień każde wystąpienie ‘starej frazy’ na ‘nową frazę’ i zwróć tylko zaktualizowany tekst.”

LLM przetwarza żądanie i odsyła zmodyfikowaną treść. To podejście działa nawet gdy fraza rozciąga się na wiele segmentów lub akapitów — coś, czego zwykła zamiana ciągów znaków często nie łapie.

---

## Zweryfikuj i wyświetl zmodyfikowany tekst

Na koniec wypisujemy tekst zmodyfikowany przez AI na konsolę. W rzeczywistej aplikacji prawdopodobnie zapiszesz wynik do nowego DOCX, ale wypisanie pozwala szybko zweryfikować.

```java
// Step 5: Show the AI‑revised output
System.out.println("AI‑revised text:");
System.out.println("-----------------------------------");
System.out.println(revisedText);
```

**Oczekiwany wynik** (zakładając, że oryginalny DOCX zawierał „This is the old phrase we want to change.”):

```
AI‑revised text:
-----------------------------------
This is the new phrase we want to change.
```

Jeśli widzisz nową frazę, gratulacje — **właśnie nauczyłeś się używać Document AI do zamiany frazy przy pomocy AI**.

---

## Pełny działający przykład

Łącząc wszystko razem, oto kompletny, gotowy do uruchomienia klas Java. Śmiało skopiuj‑wklej do `src/main/java/com/example/ReplaceInDocx.java`.

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

### Jak uruchomić

```bash
# Compile
mvn clean compile

# Execute
mvn exec:java -Dexec.mainClass="com.example.ReplaceInDocx"
```

Upewnij się, że serwer LLM jest uruchomiony przed uruchomieniem programu; w przeciwnym razie otrzymasz błąd timeout połączenia.

---

## Przypadki brzegowe i typowe pułapki

| Sytuacja | Na co zwrócić uwagę | Sugestia naprawy |
|-----------|-------------------|---------------|
| **Fraza nie znaleziona** | LLM zwraca oryginalny tekst bez zmian. | Sprawdź pisownię i wrażliwość na wielkość liter; możesz dodać `ignoreCase:true` do promptu, jeśli Twoja nakładka to obsługuje. |
| **Duże dokumenty (>5 MB)** | Rozmiar promptu może przekroczyć limit tokenów modelu. | Podziel DOCX na sekcje, przetwarzaj każdą osobno, a następnie połącz wyniki. |
| **Lokalny LLM zwraca błędy** | Często spowodowane niezgodną nazwą modelu. | Sprawdź, czy nazwa modelu w UI LLM (`ollama list`) odpowiada `modelConfig.setModelName`. |
| **Znaki Unicode są zniekształcone** | Problemy z kodowaniem przy odczycie DOCX. | Upewnij się, że środowisko Java używa UTF‑8 (dodaj `-Dfile.encoding=UTF-8` do argumentów JVM). |

---

## Kolejne kroki

Teraz, gdy wiesz **jak zamienić tekst w DOCX** przy użyciu AI, możesz chcieć zbadać:

- **Jak używać Document AI** do bardziej złożonych zadań, takich jak ekstrakcja tabel lub zachowanie stylu.  
- **Zamień frazę przy użyciu AI** w PDF-ach, zamieniając argument konstruktora `Document`.  
- **Przetwarzanie wsadowe**: iteruj po katalogu plików DOCX i zastosuj tę samą zamianę.  

Każdy z nich opiera się na tej samej podstawie `AiModelConfig` i `DocumentAi`, więc nie będziesz musiał zaczynać od zera.

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}