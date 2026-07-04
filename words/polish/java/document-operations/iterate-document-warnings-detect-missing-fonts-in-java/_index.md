---
category: general
date: 2026-04-28
description: Iteruj ostrzeżenia dokumentu w pliku Word, aby wykryć brakujące czcionki,
  pobierz ich nazwy i wyświetl szczegóły brakujących czcionek przy użyciu Aspose.Words
  dla Javy.
draft: false
keywords:
- iterate document warnings
- detect missing fonts
- load word document
- retrieve missing font
- print missing font
language: pl
og_description: Iteruj ostrzeżenia dokumentu, aby znaleźć brakujące czcionki, pobierz
  ich nazwy i wyświetl szczegóły brakujących czcionek w pełnym przykładzie w Javie.
og_title: 'Iteruj ostrzeżenia dokumentu: wykryj brakujące czcionki w Javie'
tags:
- Aspose.Words
- Java
- Document Processing
title: 'Iteruj ostrzeżenia dokumentu: wykryj brakujące czcionki w Javie'
url: /pl/java/document-operations/iterate-document-warnings-detect-missing-fonts-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Iterowanie ostrzeżeń dokumentu – wykrywanie brakujących czcionek w Javie

Czy kiedykolwiek musiałeś **iterować ostrzeżenia dokumentu** przy otwieraniu pliku Word i zastanawiałeś się, które czcionki są brakujące? Nie jesteś sam. Brakujące czcionki mogą zepsuć wygląd raportu, a bez możliwości ich wykrycia możesz wydać dokument, który nie przypomina oryginału.  

W tym tutorialu pokażemy, jak **wykrywać brakujące czcionki** poprzez załadowanie dokumentu Word, iterowanie jego ostrzeżeń, pobranie nazw brakujących czcionek i w końcu wypisanie informacji o brakujących czcionkach — wszystko przy użyciu Aspose.Words for Java.  

Omówimy wszystko od pierwszej linii kodu po oczekiwany wynik w konsoli, abyś mógł od razu skopiować‑wkleić działające rozwiązanie do swojego projektu. Żadne dodatkowe dokumenty nie są potrzebne.

## Wymagania wstępne

- Zainstalowany Java 8 lub nowsza.
- Biblioteka Aspose.Words for Java (najświeższa wersja z dnia 2026‑04‑28).
- Plik Word, który potencjalnie zawiera czcionki niezainstalowane na Twoim komputerze (np. `doc-with-missing-font.docx`).

Jeśli już masz te elementy, świetnie — jesteś gotowy, aby **załadować dokument Word** i rozpocząć iterowanie.

## Krok 1 – Załaduj dokument Word z domyślnymi opcjami

Zanim będziemy mogli **iterować ostrzeżenia dokumentu**, plik musi zostać wczytany do pamięci. Aspose.Words umożliwia to za pomocą jednego wywołania konstruktora. Użycie domyślnych `LoadOptions` zazwyczaj wystarcza, ale dla przejrzystości pokażemy explicite tworzenie obiektu.

```java
import com.aspose.words.*;

public class MissingFontDetector {
    public static void main(String[] args) throws Exception {

        // Step 1: Prepare load options (default settings are fine for this example)
        LoadOptions loadOptions = new LoadOptions();

        // Step 2: Load the document that may contain missing fonts
        Document document = new Document("YOUR_DIRECTORY/doc-with-missing-font.docx", loadOptions);
```

> **Dlaczego to ważne:**  
> Ładowanie dokumentu powoduje, że Aspose.Words skanuje plik w poszukiwaniu zasobów, których nie może rozwiązać, takich jak czcionki niezainstalowane lokalnie. Te problemy są przechowywane jako **ostrzeżenia**, które **iterujemy ostrzeżenia dokumentu** w następnym kroku.

## Krok 2 – Iteruj ostrzeżenia dokumentu, aby znaleźć problemy z czcionkami

Teraz przechodzi do serca rozwiązania: przechodzimy przez każde ostrzeżenie, które biblioteka zebrała podczas ładowania. Obiekty `WarningInfo` informują nas, co poszło nie tak, a my możemy odfiltrować `FontSubstitutionWarning`, aby **wykrywać brakujące czcionki**.

```java
        // Step 3: Iterate over all warnings generated during loading
        for (WarningInfo warningInfo : document.getWarnings()) {
            // Step 4: Identify font substitution warnings
            if (warningInfo instanceof FontSubstitutionWarning) {
                FontSubstitutionWarning fontWarning = (FontSubstitutionWarning) warningInfo;

                // Step 5: Output the missing font name and the font that was used as a substitute
                System.out.println("Missing font: " + fontWarning.getMissingFontName());
                System.out.println("Substituted with: " + fontWarning.getSubstitutedFontName());
            }
        }
    }
}
```

> **Pro tip:** Sprawdzenie `instanceof` zapewnia, że obsługujemy tylko ostrzeżenia związane z czcionkami, pomijając inne, np. problemy z ładowaniem obrazów. Dzięki temu pętla jest wydajna, a wyjście skoncentrowane na czcionkach, dla których naprawdę potrzebujesz **pobrać informacje o brakującej czcionce**.

### Oczekiwany wynik w konsoli

```
Missing font: Arial Black
Substituted with: Liberation Sans
Missing font: Calibri
Substituted with: Liberation Sans
```

Jeśli dokument nie zawiera brakujących czcionek, pętla po prostu zakończy się cicho — nic do **wypisania brakującej czcionki**.

## Krok 3 – Dlaczego nie po prostu przechwycić wyjątek?

Możesz się zastanawiać: „Dlaczego nie otoczyć wywołania `new Document(...)` blokiem try‑catch i szukać wyjątku?” Odpowiedź jest dwu‑aspektowa:

1. **Szczegółowe informacje:** Wyjątki mówią tylko, że coś się nie powiodło. Ostrzeżenia podają dokładną nazwę czcionki i zamiennik, który wybrało Aspose.Words.
2. **Problemy niekrytyczne:** Brakujące czcionki zwykle nie są krytyczne; dokument i tak się ładuje, ale jego wizualna integralność jest naruszona. **Iterując ostrzeżenia dokumentu**, zachowujesz możliwość przetworzenia reszty pliku.

## Krok 4 – Rozszerzenie przykładu: zbieranie brakujących czcionek do listy

Czasami potrzebujesz listy brakujących czcionek do dalszego przetwarzania — np. aby je osadzić lub powiadomić użytkownika w interfejsie. Oto szybka modyfikacja, która gromadzi nazwy w `Set<String>`.

```java
        // Collect missing fonts for later use
        Set<String> missingFonts = new HashSet<>();

        for (WarningInfo warningInfo : document.getWarnings()) {
            if (warningInfo instanceof FontSubstitutionWarning) {
                FontSubstitutionWarning fontWarning = (FontSubstitutionWarning) warningInfo;
                missingFonts.add(fontWarning.getMissingFontName());

                // Still print for immediate feedback
                System.out.println("Missing font: " + fontWarning.getMissingFontName());
                System.out.println("Substituted with: " + fontWarning.getSubstitutedFontName());
            }
        }

        // Example of using the collected data
        System.out.println("Total missing fonts: " + missingFonts.size());
```

Teraz masz czysty sposób na **pobranie brakujących czcionek** programistycznie, który możesz przekazać do modułu raportowania lub kreatora instalacji czcionek.

## Krok 5 – Rozważania praktyczne

- **Wiele zamienników:** Jedna brakująca czcionka może być zastąpiona różnymi czcionkami w różnych częściach dokumentu. Lista ostrzeżeń będzie zawierać każde wystąpienie, więc możesz zobaczyć duplikaty.
- **Wydajność:** Ładowanie bardzo dużych dokumentów może wygenerować tysiące ostrzeżeń. Jeśli interesują Cię tylko czcionki, filtruj je od razu, jak pokazano, aby pętla była szybka.
- **Czcionki wieloplatformowe:** Na Linuksie domyślnym zamiennikiem jest często *Liberation Sans*. Na Windows może to być *Arial*. Znajomość zamiennika pomaga zdecydować, czy musisz dostarczyć własne czcionki wraz z aplikacją.

## Krok 6 – Pomoc wizualna

Poniżej zrzut ekranu z wynikiem w konsoli (tekst alternatywny zawiera główne słowo kluczowe dla SEO).

![Iterate document warnings console output showing missing fonts and their substitutes](/images/iterate-document-warnings.png)

*Alt text:* *przykład iterowania ostrzeżeń dokumentu wyświetlający nazwy brakujących czcionek i szczegóły zamienników.*

## Podsumowanie

Właśnie nauczyłeś się, jak **iterować ostrzeżenia dokumentu** w Aspose.Words for Java, **wykrywać brakujące czcionki**, **bezpiecznie załadować dokument Word**, **pobrać informacje o brakującej czcionce** oraz **wypisać szczegóły brakujących czcionek** w konsoli. Pełny fragment kodu działa od razu, a Ty możesz go dostosować, aby logował do pliku, wyświetlał dialog UI lub automatycznie osadzał brakujące czcionki.

Następnie możesz zbadać, jak **załadować dokument Word** z własnymi źródłami czcionek (np. dodając folder z firmowymi czcionkami) lub jak osadzić brakujące czcionki bezpośrednio w pliku, aby zachować układ na wszystkich maszynach. Oba tematy naturalnie rozwijają to, co tutaj omówiliśmy.

Miłego kodowania i niech Twoje PDF‑y zawsze wyglądają dokładnie tak, jak tego oczekujesz!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}