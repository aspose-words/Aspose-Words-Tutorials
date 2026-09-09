---
category: general
date: 2026-01-11
description: Dowiedz się, jak przechwytywać ostrzeżenia o zastępowaniu czcionek przy
  użyciu Aspose.Words for Java. Ten krok po kroku poradnik obejmuje także LoadOptions
  i wywołania zwrotne ostrzeżeń.
draft: false
keywords:
- capture font substitution warnings
- Aspose.Words font substitution
- Java warning callback
- LoadOptions usage
- document loading warnings
language: pl
og_description: Rejestruj ostrzeżenia o podstawianiu czcionek za pomocą Aspose.Words
  for Java. Skorzystaj z tego przewodnika, aby skonfigurować LoadOptions i wywołanie
  zwrotne ostrzeżeń dla niezawodnego ładowania dokumentów.
og_title: Przechwyć ostrzeżenia o podstawianiu czcionek w Javie – pełny poradnik
tags:
- Aspose.Words
- Java
- Document Processing
title: Rejestrowanie ostrzeżeń o podstawianiu czcionek w Javie przy użyciu Aspose.Words
  – Kompletny przewodnik
url: /pl/java/document-loading-and-saving/capture-font-substitution-warnings-in-java-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Przechwytywanie ostrzeżeń o zastępowaniu czcionek – Pełny samouczek Java

Czy kiedykolwiek potrzebowałeś **przechwytywać ostrzeżenia o zastępowaniu czcionek** przy otwieraniu dokumentu Word z brakującymi czcionkami? To powszechny problem, szczególnie gdy generujesz PDF‑y lub drukujesz na serwerze, który nie ma zainstalowanych wszystkich krojów pisma. Dobra wiadomość? Aspose.Words for Java robi to bezproblemowo — wystarczy skonfigurować obiekt `LoadOptions` i podłączyć callback ostrzeżeń. W tym przewodniku pokażemy dokładnie, jak to zrobić, dlaczego ma to znaczenie i czego można się spodziewać, gdy ostrzeżenie zostanie wywołane.

Omówimy także powiązane tematy, takie jak **Aspose.Words font substitution**, użycie **Java warning callback** oraz najlepsze praktyki **LoadOptions usage**. Po zakończeniu będziesz mieć gotowy do uruchomienia fragment kodu, który loguje każde zdarzenie brakującej czcionki, dzięki czemu dalsze przetwarzanie nie zaskoczy Cię niespodziewanie.

## Prerequisites

Zanim przejdziemy dalej, upewnij się, że masz:

- Java 17 (lub dowolny nowszy JDK) zainstalowany i skonfigurowany.
- Aspose.Words for Java 23.10 (lub nowszy) na ścieżce klas.
- Dokument Word, który odwołuje się do czcionki nieposiadanej lokalnie (np. `DocWithMissingFont.docx`).
- Podstawową znajomość bloków try/catch w Javie — nic skomplikowanego.

Jeśli którykolwiek z tych punktów jest Ci nieznany, zatrzymaj się na chwilę i zainstaluj bibliotekę z Maven Central:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.10</version>
</dependency>
```

Teraz, gdy podłoże jest gotowe, przejdźmy do kodu.

## Krok 1: Skonfiguruj Callback Ostrzeżeń, aby **Przechwytywać Ostrzeżenia o Zastępowaniu Czcionek**

Pierwszą rzeczą, której potrzebujesz, jest callback, który Aspose.Words wywoła za każdym razem, gdy napotka brakującą czcionkę. To właśnie tutaj **przechwytywane są ostrzeżenia o zastępowaniu czcionek**. Callback implementuje interfejs `IWarningCallback` i sprawdza `WarningType`.

```java
import com.aspose.words.*;

public class FontSubstitutionInfo {

    // Custom callback that prints details of each font substitution warning
    private static class FontWarningCallback implements IWarningCallback {
        @Override
        public void warning(WarningInfo info) {
            // Only act on font‑substitution warnings
            if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                System.out.println("Font substitution warning:");
                System.out.println("  Original font: " + info.getSource());
                System.out.println("  Substituted by: " + info.getDescription());
            }
        }
    }

    public static void main(String[] args) throws Exception {
        // Code continues in the next steps...
    }
}
```

**Dlaczego to ważne:** Bez callbacku Aspose.Words cicho zamienia brakującą czcionkę na domyślną i nigdy nie dowiesz się, że wygląd wizualny uległ zmianie. Przechwycając ostrzeżenie, możesz logować, powiadamiać lub nawet przerwać ładowanie, jeśli brakująca czcionka jest krytyczna.

## Krok 2: Skonfiguruj **LoadOptions** i Zarejestruj Callback

Teraz tworzymy instancję `LoadOptions` i podłączamy nasz `FontWarningCallback`. Ten krok jest niezbędny dla **LoadOptions usage** i zapewnia, że każde ładowanie dokumentu przechodzi przez ten sam filtr ostrzeżeń.

```java
public static void main(String[] args) throws Exception {
    // Step 2: Prepare LoadOptions and hook the warning callback
    LoadOptions loadOptions = new LoadOptions();
    loadOptions.setWarningCallback(new FontWarningCallback());

    // Continue to load the document in the next step...
}
```

**Wskazówka:** Ten sam obiekt `LoadOptions` możesz ponownie używać dla wielu dokumentów, co oszczędza kilka linii kodu i gwarantuje spójne **document loading warnings** w całej aplikacji.

## Krok 3: Ładuj Dokument i Obserwuj Wynik

Z podłączonym callbackiem po prostu ładujesz plik Word. Jeśli dokument odwołuje się do czcionki, której nie ma zainstalowanej, callback zostanie wywołany i wypisze szczegóły na konsolę.

```java
    // Step 3: Load the document using the configured LoadOptions
    Document doc = new Document("YOUR_DIRECTORY/DocWithMissingFont.docx", loadOptions);

    // Step 4: Confirm that the load completed
    System.out.println("Document loaded; check console for any font‑substitution warnings.");
}
```

### Expected Console Output

Zakładając, że `DocWithMissingFont.docx` odwołuje się do brakującej czcionki *„Comic Sans MS”*, zobaczysz mniej więcej:

```
Font substitution warning:
  Original font: Comic Sans MS
  Substituted by: Arial
Document loaded; check console for any font‑substitution warnings.
```

Jeśli dokument nie zawiera **brakujących czcionek**, konsola wyświetli tylko ostatnią linię, potwierdzając, że Twój callback nie wygenerował fałszywych alarmów.

## Krok 4: Obsługa Przypadków Brzegowych i Typowych Pułapek

### Multiple Missing Fonts

Jeśli dokument używa kilku niedostępnych czcionek, callback uruchamia się raz dla każdej z nich. Otrzymasz serię komunikatów, każdy z własnym `source` i `description`. Nie wymaga to dodatkowego kodu — wystarczy, że Twój system logowania poradzi sobie z szybkim, kolejnym wywołaniami.

### Suppressing Warnings

W rzadkich przypadkach możesz chcieć zignorować niektóre zastąpienia (np. wiesz, że konkretny fallback jest akceptowalny). Rozszerz logikę callbacku:

```java
if (info.getWarningType() == WarningType.FONT_SUBSTITUTION &&
    !info.getSource().equalsIgnoreCase("SomeFontYouAccept")) {
    // Log or act on the warning
}
```

### Thread Safety

`LoadOptions` w Aspose.Words nie jest domyślnie bezpieczny wątkowo. Jeśli ładujesz dokumenty równolegle, utwórz osobną instancję `LoadOptions` dla każdego wątku lub zsynchronizuj callback, aby uniknąć wyścigów.

## Krok 5: Weryfikacja Zastąpionej Czcionki w Wynikowym Dokumencie

Po załadowaniu możesz chcieć potwierdzić, że zastąpienie faktycznie nastąpiło. API pozwala iterować po wszystkich `Run` i sprawdzić efektywną nazwę czcionki:

```java
for (Run run : (Iterable<Run>) doc.getFirstSection().getBody().getChildNodes(NodeType.RUN, true)) {
    System.out.println("Run text: \"" + run.getText() + "\" uses font: " + run.getFont().getName());
}
```

## Full Working Example

Łącząc wszystko razem, oto kompletny, gotowy do uruchomienia program:

```java
import com.aspose.words.*;

public class FontSubstitutionInfo {

    private static class FontWarningCallback implements IWarningCallback {
        @Override
        public void warning(WarningInfo info) {
            if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                System.out.println("Font substitution warning:");
                System.out.println("  Original font: " + info.getSource());
                System.out.println("  Substituted by: " + info.getDescription());
            }
        }
    }

    public static void main(String[] args) throws Exception {
        // Prepare LoadOptions and register the warning callback
        LoadOptions loadOptions = new LoadOptions();
        loadOptions.setWarningCallback(new FontWarningCallback());

        // Load the document (replace with your actual path)
        Document doc = new Document("YOUR_DIRECTORY/DocWithMissingFont.docx", loadOptions);

        // Optional: verify effective fonts in the document
        for (Run run : (Iterable<Run>) doc.getFirstSection().getBody().getChildNodes(NodeType.RUN, true)) {
            System.out.println("Run text: \"" + run.getText() + "\" uses font: " + run.getFont().getName());
        }

        System.out.println("Document loaded; check console for any font‑substitution warnings.");
    }
}
```

Zapisz go jako `FontSubstitutionInfo.java`, skompiluj przy pomocy `javac` i uruchom `java FontSubstitutionInfo`. Powinieneś zobaczyć komunikaty ostrzegawcze (jeśli wystąpią), a następnie listę `Run` i ich ostatecznych czcionek.

## Visual Aid

![Zrzut ekranu wyjścia konsoli pokazujący ostrzeżenia o zastępowaniu czcionek](/images/font-substitution-warning.png "przykład przechwytywania ostrzeżeń o zastępowaniu czcionek")

*Alt text:* **przechwytywanie ostrzeżeń o zastępowaniu czcionek** – wyjście konsoli po załadowaniu dokumentu z brakującymi czcionkami.

## Conclusion

Teraz wiesz, jak **przechwytywać ostrzeżenia o zastępowaniu czcionek** przy użyciu Aspose.Words for Java. Konfigurując obiekt `LoadOptions` i dostarczając własny `IWarningCallback`, uzyskujesz pełną widoczność wszelkich zdarzeń brakujących czcionek, które w innym wypadku mogłyby cicho wpłynąć na wygląd dokumentu. Technika ta łączy się bezpośrednio z obsługą **Aspose.Words font substitution**, zapewnia niezawodne **document loading warnings** i daje elastyczność logowania, powiadamiania lub przerywania działania zgodnie z regułami biznesowymi.

### Co dalej?

- Zbadaj wzorce **Java warning callback** dla innych typów ostrzeżeń (np. `DEPRECATED_FEATURE`).
- Połącz to podejście z **PDF conversion**, aby mieć pewność, że zastąpione czcionki nie zepsują układu.
- Zagłęb się w **LoadOptions usage** — eksperymentuj z `Password`, `Encoding` i `ResourceLoadingCallback` w bardziej zaawansowanych scenariuszach.

Śmiało modyfikuj callback, kieruj ostrzeżenia do frameworka logowania lub nawet rzucaj własny wyjątek, jeśli krytyczna czcionka jest nieobecna. Niebo jest granicą, a Ty masz solidne podstawy, na których możesz budować.

Miłego kodowania i niech Twoje dokumenty zawsze renderują się dokładnie tak, jak tego oczekujesz!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}