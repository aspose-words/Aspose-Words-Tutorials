---
category: general
date: 2026-03-25
description: Utwórz własny model AI do edycji dokumentów Word – dowiedz się, jak uczynić
  tekst bardziej formalnym, zamienić tekst akapitu i przekształcić akapit w Wordzie
  przy użyciu Aspose.Words AI.
draft: false
keywords:
- create custom ai model
- make text more formal
- replace paragraph text
- edit paragraph with ai
- rewrite word paragraph
language: pl
og_description: Stwórz niestandardowy model AI do edycji dokumentów Word. Dowiedz
  się, jak uczynić tekst bardziej formalnym, zamienić tekst akapitu i przekształcić
  akapit w Wordzie przy użyciu Aspose.Words AI.
og_title: Utwórz własny model AI – edytuj akapity w Wordzie w Javie
tags:
- Aspose.Words
- Java
- AI integration
title: Utwórz własny model AI – edytuj akapity Word w Javie
url: /pl/java/ai-machine-learning-integration/create-custom-ai-model-edit-word-paragraphs-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Utwórz niestandardowy model AI – Edytuj akapity Word w Javie

Czy kiedykolwiek potrzebowałeś **create custom AI model**, który może dopracować akapit w pliku Word? Może masz zestaw umów, które brzmią nieco zbyt potocznie i chciałbyś uczynić tekst bardziej formalnym jedną linią kodu. Dobre wieści są takie, że możesz to zrobić dokładnie w ten sposób — bez zewnętrznych usług, bez ciężkich SDK, tylko Aspose.Words for Java i punkt końcowy kompatybilny z OpenAI.

W tym samouczku przeprowadzimy Cię przez każdy krok niezbędny do **create custom AI model**, podłączenia go do lokalnego serwera LLM i użycia go do *replace paragraph text* w bardziej formalną wersję. Po zakończeniu będziesz mieć uruchamialny program w Javie, który **edit paragraph with AI**, przepisuje akapit Word i zapisuje wynik z powrotem na dysku. Bez zbędnych dodatków, tylko praktyczne rozwiązanie, które możesz skopiować‑wkleić do własnego projektu.

> **Czego będziesz potrzebować**  
> • Java 17 lub nowsza (kod kompiluje się także w starszych wersjach, ale 17 to optymalny wybór)  
> • Aspose.Words for Java 23.9 (lub najnowsze wydanie)  
> • Działający serwer LLM kompatybilny z OpenAI (np. Ollama, LocalAI) nasłuchujący na `http://localhost:8000/v1`  
> • Dokument Word jako wejście (`input.docx`) umieszczony w folderze, którym zarządzasz  

Jeśli zastanawiasz się *why bother building a custom model* zamiast wywoływać OpenAI bezpośrednio, odpowiedź brzmi elastyczność: kontrolujesz punkt końcowy, możesz wymieniać modele bez zmian w kodzie i trzymasz klucze API poza repozytorium źródłowym. Zanurzmy się.

---

## Utwórz niestandardowy model AI – konfiguracja i ustawienia

Najpierw musimy poinformować Aspose.Words, gdzie znajduje się nasz LLM. Klasa `AiModelEndpoint` przechowuje URL i opcjonalny klucz API. Ponieważ używamy lokalnego serwera, klucz może być pustym ciągiem, ale parametr jest wymagany.

```java
import com.aspose.words.ai.*;

public class LlmDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Define the LLM endpoint (OpenAI‑compatible)
        AiModelEndpoint llmEndpoint = new AiModelEndpoint(
                "http://localhost:8000/v1",   // URL of your LLM server
                "my-api-key");                // API key if required
```

> **Pro tip:** Jeśli kiedykolwiek przełączysz się na model hostowany (np. Azure OpenAI), po prostu zmień URL i klucz — nie są potrzebne żadne inne zmiany w kodzie.

## Wczytaj dokument Word

Teraz wczytujemy plik źródłowy do pamięci. `Document` może odczytywać `.docx`, `.doc`, `.rtf` i wiele innych formatów, ale w tym przykładzie pozostajemy przy `.docx`.

```java
        // Step 2: Load the source Word document
        Document document = new Document("YOUR_DIRECTORY/input.docx");
```

Upewnij się, że `YOUR_DIRECTORY` wskazuje na rzeczywisty folder; w przeciwnym razie napotkasz `FileNotFoundException`. W rzeczywistej aplikacji możesz przekazać ścieżkę jako argument wiersza poleceń lub odczytać ją z pliku konfiguracyjnego.

## Zainicjuj niestandardowy model AI

Tworzymy `AiModel` typu `CUSTOM` i podajemy mu wcześniej zdefiniowany punkt końcowy. To informuje Aspose.Words, aby kierował wszystkie wywołania AI przez nasz własny serwer.

```java
        // Step 3: Create a custom AI model that uses the endpoint
        AiModel llmModel = new AiModel(AiModelType.CUSTOM, llmEndpoint);
```

Za kulisami Aspose.Words buduje małego klienta HTTP, który komunikuje się z LLM przy użyciu standardowego schematu czatu/kompletacji OpenAI. Dlatego punkt końcowy musi być *OpenAI‑compatible*.

## Pobierz i przepisz pierwszy akapit

Tutaj faktycznie **make text more formal**. Pobieramy pierwszy akapit, wysyłamy jego surowy tekst do modelu z podpowiedzią i otrzymujemy edytowaną wersję.

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

Drugi argument (`"Make it more formal"`) jest instrukcją, którą przekazujemy modelowi. Możesz go zamienić na dowolną dyrektywę — **replace paragraph text**, **summarize**, **translate** itd. Metoda zwraca zwykły ciąg znaków, który później wstawimy z powrotem do dokumentu.

> **Dlaczego to działa:** `editText` wysyła ładunek JSON taki jak `{ \"model\": \"...\", \"messages\": [{ \"role\":\"user\", \"content\":\"<text>\\nMake it more formal\"}] }`. LLM widzi oryginalny akapit i instrukcję, a następnie odpowiada zmodyfikowanym tekstem.

## Zastąp oryginalną treść akapitu

Teraz **replace paragraph text** w modelu obiektowym Word. Czyścimy wszystkie istniejące runy (niskopoziomowe fragmenty tekstu) i wstawiamy nowy `Run` zawierający wygenerowany przez AI ciąg znaków.

```java
        // Step 5: Replace the original paragraph content with the rewritten text
        firstParagraph.removeAllChildren();
        firstParagraph.appendChild(new Run(document, rewrittenText));
```

Uważaj, aby nie wywołać `firstParagraph.setText()` — ta metoda usunęłaby całe formatowanie. Użycie `Run` zachowuje styl akapitu (nagłówek, wypunktowanie itp.) przy zamianie rzeczywistych znaków.

## Zapisz zmodyfikowany dokument

Na koniec zapisujemy zmodyfikowany dokument z powrotem na dysku. Możesz nadpisać oryginalny plik lub, tak jak tutaj, utworzyć nową kopię.

```java
        // Step 6: Save the edited document
        document.save("YOUR_DIRECTORY/output.docx");
    }
}
```

Gdy otworzysz `output.docx`, powinieneś zobaczyć, że pierwszy akapit brzmi teraz znacznie bardziej formalnie. Jeśli LLM nie zastosował instrukcji idealnie, możesz dostosować podpowiedź lub spróbować innej wersji modelu.

## Pełny działający przykład

Poniżej znajduje się kompletny program — skopiuj go do `LlmDemo.java`, dostosuj ścieżki i uruchom przy użyciu `javac` + `java`.

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

**Expected output:** Otwórz `output.docx` i zobaczysz przekształcony oryginalny akapit. Na przykład, potoczna fraza „We’ll get the thing done soon.” może stać się „We shall complete the task promptly.” Dokładne sformułowanie zależy od używanego modelu.

## Częste pytania i przypadki brzegowe

### Co jeśli mój dokument ma wiele sekcji?

Powyższy kod dotyka tylko *pierwszego* akapitu *pierwszej* sekcji. Aby **edit paragraph with AI** w całym pliku, przeiteruj `document.getSections()` a następnie każdy `section.getBody().getParagraphs()`. Pamiętaj, aby pomijać puste akapity, w przeciwnym razie LLM otrzyma pusty ciąg i nie zwróci nic.

### Jak obsłużyć długie akapity przekraczające limity tokenów?

Większość LLM-ów ogranicza wejście do około 4 000 tokenów. Jeśli akapit jest wyjątkowo długi, podziel go na mniejsze fragmenty przed wywołaniem `editText`. Możesz ponownie używać tej samej instancji `AiModel`; po prostu pamiętaj o limitach szybkości na swoim lokalnym serwerze.

### Czy mogę użyć innej instrukcji, np. „summarize” lub „translate to French”?

Oczywiście. Drugi argument do `editText` jest wolnym tekstem. Dla streszczenia możesz przekazać `"Summarize in one sentence"`. Dla tłumaczenia, `"Translate to French, keep the tone formal"` działa równie dobrze. Ta elastyczność pozwala **replace paragraph text** w wielu scenariuszach bez zmiany kodu.

### Czy model zachowuje styl akapitu (czcionki, kolory)?

Ponieważ zamieniamy tylko `Run` wewnątrz tego samego obiektu `Paragraph`, istniejące style (poziom nagłówka, lista wypunktowana, wcięcie) pozostają nienaruszone. Jeśli potrzebujesz zmienić sam styl, możesz manipulować `Paragraph.getParagraphFormat()` po zamianie.

### Co jeśli mój serwer LLM wymaga HTTPS z certyfikatem samopodpisanym?

`AiModelEndpoint` akceptuje URL z `https://`. Jeśli certyfikat nie jest zaufany, musisz skonfigurować kontekst SSL Javy, aby go ufał, lub uruchomić serwer z ważnym certyfikatem. To ustawienie wykracza poza zakres tego samouczka, ale jest dobrze udokumentowane w przewodnikach Java SSL.

## Wskazówki dla integracji gotowej do produkcji

| Tip | Why it matters |
|-----|----------------|
| **Buforuj punkt końcowy** | Ponowne tworzenie `AiModelEndpoint` przy każdym żądaniu zwiększa narzut. |
| **Edytuj partiami** | Jeśli masz wiele akapitów, wyślij je w jednym żądaniu (np. tablica JSON), aby zmniejszyć opóźnienie. |
| **Waliduj wynik LLM** | Zawsze sprawdzaj zwrócony ciąg pod kątem wartości null lub pustych przed wstawieniem. |
| **Loguj podpowiedzi i odpowiedzi** | Przydatne przy debugowaniu i zapewnieniu zgodności, gdy przepisujesz tekst prawny. |
| **Łagodny fallback** | Jeśli LLM jest niedostępny, przejdź do oryginalnego akapitu lub prostej heurystycznej modyfikacji. |

## Podsumowanie

Pokazaliśmy, jak **create custom AI model** z Aspose.Words, połączyć go z punktem końcowym kompatybilnym z OpenAI i następnie **edit paragraph with AI**, aby **make text more formal**. Postępując zgodnie z sześcioma krokami — zdefiniuj punkt końcowy, wczytaj dokument, zainicjuj model,

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}