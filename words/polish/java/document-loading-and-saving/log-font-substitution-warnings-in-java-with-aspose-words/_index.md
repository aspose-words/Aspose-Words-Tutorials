---
category: general
date: 2026-06-17
description: Rejestruj ostrzeżenia o podstawianiu czcionek w Javie przy użyciu Aspose.Words
  – przechwytuj brakujące czcionki podczas ładowania dokumentu i zachowaj spójność
  wyjścia.
draft: false
keywords:
- log font substitution warnings
- Aspose.Words Java
- font substitution
- warning callback
- LoadOptions
- document loading
language: pl
og_description: Rejestruj ostrzeżenia o podstawianiu czcionek w Javie przy użyciu
  Aspose.Words. Dowiedz się, jak przechwytywać alerty o brakujących czcionkach podczas
  ładowania dokumentu i zachować swoje pliki PDF w nienaruszonym stanie.
og_title: Rejestrowanie ostrzeżeń o podstawianiu czcionek w Javie – Kompletny przewodnik
schemas:
- author: Aspose
  dateModified: '2026-06-17'
  description: Log font substitution warnings in Java using Aspose.Words – capture
    missing fonts during document load and keep your output consistent.
  headline: Log Font Substitution Warnings in Java with Aspose.Words
  type: TechArticle
- description: Log font substitution warnings in Java using Aspose.Words – capture
    missing fonts during document load and keep your output consistent.
  name: Log Font Substitution Warnings in Java with Aspose.Words
  steps:
  - name: Prerequisites
    text: '- Java 8 or newer (the code works with Java 11+ as well). - Aspose.Words
      for Java library (version 23.10 or later is recommended). - A sample `.docx`
      that references a font not installed on your machine (e.g., `MissingFont.docx`).'
  - name: Logging to a File Instead of the Console
    text: 'If you prefer a persistent log, replace the `System.out.println` call with
      a `FileWriter`:'
  - name: Capturing Multiple Documents in a Loop
    text: 'When processing a folder of documents, you can reuse the same callback:'
  - name: Dealing with Embedded Fonts
    text: 'Aspose.Words can embed missing fonts if you enable it:'
  type: HowTo
tags:
- Java
- Aspose.Words
- Document Processing
title: Rejestrowanie ostrzeżeń o podstawianiu czcionek w Javie przy użyciu Aspose.Words
url: /pl/java/document-loading-and-saving/log-font-substitution-warnings-in-java-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Rejestrowanie ostrzeżeń o podstawianiu czcionek w Javie – Kompletny przewodnik

Zastanawiałeś się kiedyś, jak **rejestrować ostrzeżenia o podstawianiu czcionek**, gdy dokument Word pobiera czcionkę, której nie masz na serwerze? Nie jesteś jedynym, który drapie się po głowie z powodu brakujących czcionek, które cicho są zamieniane. Dobra wiadomość? Aspose.Words for Java oferuje prosty sposób na przechwycenie tych podstawień w momencie ładowania dokumentu.

W tym samouczku przeprowadzimy praktyczny przykład, który dokładnie pokazuje, jak zarejestrować callback ostrzeżeń, filtrować alerty o podstawianiu czcionek i zapisywać je do konsoli (lub dowolnego loggera, którego preferujesz). Po zakończeniu będziesz mieć wielokrotnego użytku fragment kodu, który możesz wstawić do dowolnego projektu Java używającego **Aspose.Words Java**.

## Co się nauczysz

- Jak skonfigurować **LoadOptions**, aby przechwytywać ostrzeżenia.
- Jak zaimplementować **IWarningCallback**, który reaguje wyłącznie na zdarzenia **font substitution**.
- Jak bezpiecznie załadować dokument, zachowując przejrzysty ślad audytu brakujących czcionek.
- Wskazówki dotyczące rozszerzenia rozwiązania o logi plikowe lub systemy monitoringu.

### Wymagania wstępne

- Java 8 lub nowsza (kod działa również z Java 11+).
- Biblioteka Aspose.Words for Java (zalecana wersja 23.10 lub nowsza).
- Przykładowy plik `.docx`, który odwołuje się do czcionki niezainstalowanej na twoim komputerze (np. `MissingFont.docx`).

Nie są wymagane dodatkowe frameworki — wystarczy czysta Java i pliki Aspose.JAR.

---

## Krok 1: Skonfiguruj LoadOptions dla Aspose.Words Java

Zanim będziesz mógł przechwycić jakiekolwiek ostrzeżenia, potrzebujesz instancji **LoadOptions**. Ten obiekt informuje Aspose.Words, jak ma się zachowywać podczas parsowania nadchodzącego pliku.

```java
// Step 1: Create LoadOptions to enable warning capture
LoadOptions loadOptions = new LoadOptions();
```

Dlaczego ten krok jest kluczowy? Bez obiektu `LoadOptions` biblioteka cicho podstawia brakujące czcionki i nigdy nie zobaczysz śladu. Tworząc go jawnie, otwierasz drzwi do własnego **callbacka ostrzeżeń**, który może rejestrować dokładnie to, co Cię interesuje.

> **Wskazówka:** Jeśli ładujesz wiele dokumentów w partii, użyj ponownie jednej instancji `LoadOptions`, aby uniknąć niepotrzebnego tworzenia obiektów.

---

## Krok 2: Zaimplementuj callback ostrzeżeń dla podstawiania czcionek

Aspose.Words dostarcza interfejs `IWarningCallback`. Implementacja pozwala zdecydować, co zrobić, gdy silnik zgłosi `WarningInfo`. W naszym przypadku chcemy reagować tylko na `WarningType.FONT_SUBSTITUTION`.

```java
// Step 2: Register a warning callback that logs only font‑substitution warnings
loadOptions.setWarningCallback(new IWarningCallback() {
    @Override
    public void warning(WarningInfo info) {
        // Filter for font‑substitution warnings only
        if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
            // Simple console output – replace with a logger if you prefer
            System.out.println("Font substitution: " + info.getMessage());
        }
    }
});
```

Kilka rzeczy do zauważenia:

1. **Filtrowanie** – Instrukcja `if` zapewnia, że ignorujemy niepowiązane ostrzeżenia (np. problemy z układem) i utrzymujemy log w porządku.
2. **Bezpieczeństwo wątków** – Callback działa w tym samym wątku, który ładuje dokument, więc nie potrzebujesz dodatkowej synchronizacji dla prostego wyjścia do konsoli. Jeśli zapisujesz do współdzielonego loggera, upewnij się, że jest on bezpieczny wątkowo.
3. **Rozszerzalność** – Chcesz zapisywać do pliku? Zamień `System.out.println` na `java.util.logging.Logger` lub inny framework logowania.

## Krok 3: Załaduj dokument używając skonfigurowanych opcji

Teraz, gdy callback jest gotowy, załaduj swój plik Word. W momencie, gdy Aspose.Words przetworzy dokument, każda brakująca czcionka wywoła wcześniej zdefiniowany callback.

```java
// Step 3: Load the document with the warning‑aware LoadOptions
Document doc = new Document("YOUR_DIRECTORY/MissingFont.docx", loadOptions);
```

Jeśli plik źródłowy odwołuje się do czcionki, która nie jest zainstalowana, zobaczysz wyjście podobne do:

```
Font substitution: Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
```

Ta linia to **rejestrowane ostrzeżenia o podstawianiu czcionek**, których szukałeś. Teraz możesz na nią zareagować — np. powiadomić użytkownika, przełączyć się na zapasowy arkusz stylów lub po prostu zachować zapis dla zgodności.

## Krok 4: Kontynuuj normalne przetwarzanie

Po załadowaniu dokument zachowuje się jak każdy inny obiekt `Document`. Śmiało przeglądaj sekcje, wyodrębniaj tekst lub konwertuj do PDF. Logowanie ostrzeżeń odbywa się automatycznie podczas kroku ładowania, więc nie potrzebujesz dodatkowego kodu.

```java
// Example: Print the number of sections – just to prove the doc is usable
System.out.println("Document has " + doc.getSections().getCount() + " sections.");
```

Konsola pokaże teraz zarówno ostrzeżenie o podstawianiu czcionek (jeśli wystąpi) **jak i** liczbę sekcji, potwierdzając, że dokument jest w pełni funkcjonalny.

## Zaawansowane wskazówki i przypadki brzegowe

### Logowanie do pliku zamiast konsoli

Jeśli wolisz trwały log, zamień wywołanie `System.out.println` na `FileWriter`:

```java
private static final String LOG_PATH = "logs/font_substitutions.txt";

loadOptions.setWarningCallback(new IWarningCallback() {
    @Override
    public void warning(WarningInfo info) {
        if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
            try (FileWriter fw = new FileWriter(LOG_PATH, true)) {
                fw.write("Font substitution: " + info.getMessage() + System.lineSeparator());
            } catch (IOException e) {
                e.printStackTrace();
            }
        }
    }
});
```

Pamiętaj, aby w kodzie produkcyjnym prawidłowo obsługiwać `IOException`.

### Przechwytywanie wielu dokumentów w pętli

Podczas przetwarzania folderu dokumentów możesz ponownie użyć tego samego callbacka:

```java
File[] files = new File("input").listFiles((dir, name) -> name.endsWith(".docx"));
for (File f : files) {
    Document d = new Document(f.getAbsolutePath(), loadOptions);
    // Additional processing...
}
```

Ponieważ callback jest podłączony do `loadOptions`, każda iteracja automatycznie loguje wszelkie zdarzenia podstawiania czcionek.

### Radzenie sobie z czcionkami osadzonymi

Aspose.Words może osadzać brakujące czcionki, jeśli to włączysz:

```java
loadOptions.setLoadFormat(LoadFormat.DOCX);
loadOptions.setEnableFontSubstitution(true); // default is true
```

Nawet przy włączonym osadzaniu, callback ostrzeżeń nadal się wywołuje, dając wgląd w to, co zostało podstawione.

## Pełny działający przykład

Poniżej znajduje się kompletny, gotowy do uruchomienia program. Skopiuj go do klasy o nazwie `FontSubstitutionDiagnostics.java`, dostosuj ścieżkę do pliku i uruchom.

```java
import com.aspose.words.*;

import java.io.FileWriter;
import java.io.IOException;

/**
 * Demonstrates how to log font substitution warnings using Aspose.Words for Java.
 */
public class FontSubstitutionDiagnostics {

    // Optional: path to a persistent log file
    private static final String LOG_FILE = "font_substitution_log.txt";

    public static void main(String[] args) throws Exception {
        // 1️⃣ Create LoadOptions to capture warnings
        LoadOptions loadOptions = new LoadOptions();

        // 2️⃣ Register a warning callback that logs only font‑substitution warnings
        loadOptions.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) {
                if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                    String message = "Font substitution: " + info.getMessage();
                    // Log to console
                    System.out.println(message);
                    // Also append to a file (optional)
                    try (FileWriter fw = new FileWriter(LOG_FILE, true)) {
                        fw.write(message + System.lineSeparator());
                    } catch (IOException e) {
                        // In a real app, use a proper logging framework
                        e.printStackTrace();
                    }
                }
            }
        });

        // 3️⃣ Load the document with the configured LoadOptions
        Document doc = new Document("YOUR_DIRECTORY/MissingFont.docx", loadOptions);

        // 4️⃣ Continue normal processing – e.g., print section count
        System.out.println("Document has " + doc.getSections().getCount() + " sections.");
    }
}
```

**Oczekiwane wyjście** (zakładając, że dokument źródłowy odwołuje się do brakującej czcionki):

```
Font substitution: Font 'Times New Roman' was not found. Substituted with 'Arial'.
Document has 3 sections.
```

Zarówno konsola, jak i `font_substitution_log.txt` będą zawierały ostrzeżenie, zapewniając wiarygodny ślad audytu.

## Podsumowanie

Pokazaliśmy właśnie, jak **rejestrować ostrzeżenia o podstawianiu czcionek** w Javie przy użyciu Aspose.Words. Konfigurując `LoadOptions`, podłączając `IWarningCallback` i ładując dokument, uzyskasz pełną widoczność wszelkich zdarzeń brakujących czcionek, które w innym wypadku mogłyby pozostać niezauważone. Od tego momentu możesz:

- Przekierować ostrzeżenia do centralnej usługi logowania.
- Wywoływać alerty w pipeline'ach kontroli jakości.
- Połączyć tę technikę z innymi strategiami **document loading**, takimi jak konwersja do PDF lub scalanie korespondencji (mail‑merge).

Śmiało eksperymentuj — zamień logger konsoli na SLF4J, dodaj znaczniki czasu lub nawet wyślij alerty do panelu monitoringu. Podstawowy wzorzec pozostaje taki sam, a teraz masz solidną bazę do niezawodnego zarządzania czcionkami w dowolnym przepływie pracy dokumentów opartym na Javie.

Masz własny pomysł, którym chciałbyś się podzielić? Może zintegrowałeś to ze Spring Boot lub funkcją w chmurze. Dodaj komentarz poniżej i kontynuujmy dyskusję. Szczęśliwego kodowania!

## Co powinieneś nauczyć się dalej?

Poniższe samouczki obejmują ściśle powiązane tematy, które rozwijają techniki przedstawione w tym przewodniku. Każdy zasób zawiera kompletne działające przykłady kodu z wyjaśnieniami krok po kroku, aby pomóc Ci opanować dodatkowe funkcje API i odkrywać alternatywne podejścia implementacyjne w własnych projektach.

- [Rejestrowanie ostrzeżeń o podstawianiu czcionek w Javie z Aspose.Words – Kompletny przewodnik](/words/english/java/document-loading-and-saving/capture-font-substitution-warnings-in-java-with-aspose-words/)
- [Używanie opcji i ustawień dokumentu w Aspose.Words for Java](/words/english/java/document-manipulation/using-document-options-and-settings/)
- [Włączanie ostrzeżeń o podstawianiu czcionek w Aspose.Words – Kompletny przewodnik](/words/english/net/working-with-fonts/enable-font-substitution-warnings-in-aspose-words-complete-g/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}