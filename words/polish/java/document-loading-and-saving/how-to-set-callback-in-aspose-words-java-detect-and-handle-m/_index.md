---
category: general
date: 2026-06-20
description: jak ustawić callback w Aspose.Words Java, aby wykrywać brakujące czcionki
  i dostosować ładowanie dokumentu. Dowiedz się krok po kroku, jak obsługiwać ostrzeżenia
  o podstawianiu czcionek.
draft: false
keywords:
- how to set callback
- detect missing fonts
- handle missing fonts
- customize document loading
language: pl
og_description: jak ustawić callback w Aspose.Words Java, aby wykrywać brakujące czcionki,
  obsługiwać ich zamiany i dostosowywać ładowanie dokumentu. Kompletny przewodnik
  z kodem.
og_title: jak ustawić callback – wykrywanie brakujących czcionek w Aspose.Words Java
schemas:
- author: Aspose
  dateModified: '2026-06-20'
  description: how to set callback in Aspose.Words Java to detect missing fonts and
    customize document loading. Learn step‑by‑step handling of font substitution warnings.
  headline: how to set callback in Aspose.Words Java – Detect and Handle Missing Fonts
  type: TechArticle
- description: how to set callback in Aspose.Words Java to detect missing fonts and
    customize document loading. Learn step‑by‑step handling of font substitution warnings.
  name: how to set callback in Aspose.Words Java – Detect and Handle Missing Fonts
  steps:
  - name: What if I want the program to stop loading when a font is missing?
    text: 'Throw an exception inside the `warning` method:'
  - name: Does this work for PDFs generated from DOCX?
    text: Absolutely. The callback fires during the **loading** phase, which is identical
      for all output formats (`save` to PDF, DOCX, HTML, etc.). As long as you load
      the source document with the same `LoadOptions`, you’ll catch missing fonts
      before they affect the final PDF.
  - name: Can I capture other warning types (e.g., image conversion)?
    text: Yes—`WarningInfo.getWarningType()` can be compared against other enums like
      `WarningType.IMAGE_CONVERSION`. Just add more `if` branches in the callback.
  - name: Is there a performance impact?
    text: Negligible. The callback runs synchronously during loading, and the extra
      checks are lightweight. If you’re loading thousands of documents, you might
      want to disable warnings in production by setting `loadOptions.setWarningCallback(null);`.
  - name: What’s Next?
    text: '- Explore **font substitution tables** for bulk mapping of many missing
      fonts. - Combine this callback with **document validation** to enforce style
      guides. - Try **custom warning callbacks** that write to a log file or a monitoring
      system instead of `System.out`.'
  type: HowTo
tags:
- Aspose.Words
- Java
- Document Processing
title: jak ustawić callback w Aspose.Words Java – wykrywanie i obsługa brakujących
  czcionek
url: /pl/java/document-loading-and-saving/how-to-set-callback-in-aspose-words-java-detect-and-handle-m/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# jak ustawić callback w Aspose.Words Java – wykrywanie i obsługa brakujących czcionek

Zastanawiałeś się kiedyś **jak ustawić callback** w Aspose.Words Java, aby wykrywać brakujące czcionki zanim zepsują Twój PDF lub DOCX? Nie jesteś jedyny. Ostrzeżenia o brakujących czcionkach mogą cicho zepsuć układ, a bez odpowiedniego callbacku ostrzeżeń możesz nigdy nie zauważyć, dopóki końcowy dokument nie będzie wyglądał nieprawidłowo.

W tym samouczku przeprowadzimy Cię przez kompletny, gotowy do uruchomienia przykład, który **wykrywa brakujące czcionki**, **elegancko obsługuje brakujące czcionki**, oraz pokazuje, jak **dostosować ładowanie dokumentu** przy użyciu callbacku ostrzeżeń. Po zakończeniu będziesz mieć samodzielną klasę Java, którą możesz wkleić do dowolnego projektu — bez konieczności dodatkowego szukania dokumentacji.

## Czego będziesz potrzebować

- Java 8 lub nowszy (kod działa również z Java 11+)  
- Biblioteka Aspose.Words for Java (wersja 23.9 lub późniejsza)  
- Plik DOCX, który odwołuje się do czcionki, której nie masz zainstalowanej (np. własna czcionka firmowa)  

Jeśli jeszcze nie dodałeś Aspose.Words do swojego projektu Maven, po prostu dodaj:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
</dependency>
```

To wszystko — bez dodatkowych wtyczek, bez natywnych zależności.

---

## Krok 1: Zrozum mechanizm WarningCallback

**Callback ostrzeżeń** to sposób Aspose.Words na poinformowanie Cię, gdy coś nieoczekiwanego dzieje się podczas ładowania lub zapisywania dokumentu. Implementując `IWarningCallback` zyskujesz pełną kontrolę nad tym, co jest logowane, ignorowane lub nawet przekształcane w wyjątek.

> **Dlaczego to ważne:**  
> Gdy brakuje czcionki, Aspose podmienia ją na czcionkę zapasową. Efekt wizualny może być diametralnie inny, szczególnie w PDF‑ach o silnym brandingu. Przechwytując `WarningType.FONT_SUBSTITUTION`, możesz zalogować dokładną nazwę czcionki, zdecydować, czy przerwać proces, lub programowo podmienić własną czcionkę.

## Krok 2: Utwórz instancję LoadOptions

`LoadOptions` jest punktem wejścia do dostosowywania ładowania dokumentu. Do tego obiektu podłączysz callback przed faktycznym załadowaniem pliku.

```java
// Step 2: Prepare LoadOptions
LoadOptions loadOptions = new LoadOptions();
```

W tym momencie `loadOptions` jest po prostu pustym kontenerem — nic się jeszcze nie dzieje. Prawdziwa magia zaczyna się, gdy podłączymy callback.

## Krok 3: Zaimplementuj i podłącz callback

Poniżej znajduje się kompaktowa anonimowa klasa implementująca `IWarningCallback`. Wypisuje przyjazny komunikat na konsolę za każdym razem, gdy zachodzi podmiana czcionki.

```java
// Step 3: Attach a warning callback to capture font substitution warnings
loadOptions.setWarningCallback(new IWarningCallback() {
    @Override
    public void warning(WarningInfo info) {
        // Detect missing fonts
        if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
            System.out.println("[Missing Font] " + info.getDescription());
            // Optional: you could throw an exception here to abort loading
            // throw new RuntimeException("Font missing: " + info.getDescription());
        }
    }
});
```

> **Pro tip:** Jeśli chcesz **obsłużyć brakujące czcionki** poprzez podanie zamiennika, możesz również ustawić `FontSettings` w `LoadOptions` i mapować brakujące czcionki na znany zamiennik.

## Krok 4: Załaduj dokument z własnymi opcjami

Teraz, gdy callback jest podłączony, załaduj dokument. Jeśli plik odwołuje się do czcionki, której nie masz, zobaczysz wypisane ostrzeżenie.

```java
// Step 4: Load the document using the configured LoadOptions
String docPath = "YOUR_DIRECTORY/doc-with-missing-font.docx";
Document document = new Document(docPath, loadOptions);
```

Po uruchomieniu programu, konsola może wyświetlić:

```
[Missing Font] Font substitution: The font "MyCustomFont" was not found. Substituted with "Arial".
```

Ten wiersz dowodzi, że pomyślnie **wykryłeś brakujące czcionki** i jesteś teraz w stanie **obsłużyć brakujące czcionki** w dowolny sposób.

## Krok 5: Opcjonalnie – zamień brakujące czcionki na znaną czcionkę

Jeśli wolisz automatycznie zamieniać każdą brakującą czcionkę, powiedzmy, na `Times New Roman`, możesz dodać obiekt `FontSettings`:

```java
// Optional Step 5: Map missing fonts to a fallback
FontSettings fontSettings = new FontSettings();
fontSettings.setMissingFontNotification(new IWarningCallback() {
    @Override
    public void warning(WarningInfo info) {
        // This will be called for each missing font
        if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
            System.out.println("[Auto‑Replace] " + info.getDescription());
        }
    }
});
// Force substitution to Times New Roman
fontSettings.getSubstitutionSettings().getTableSubstitution().addSubstitutes("MyCustomFont", new String[]{"Times New Roman"});
loadOptions.setFontSettings(fontSettings);
```

Teraz dokument ładuje się, a każde odwołanie do `MyCustomFont` jest cicho zamieniane na `Times New Roman`. Konsola nadal będzie informować, co zostało zamienione, utrzymując Cię w pętli.

## Pełny działający przykład

Poniżej znajduje się pojedyncza klasa Java, która zawiera wszystkie powyższe kroki. Skopiuj‑wklej ją do swojego IDE, dostosuj `docPath` i uruchom.

```java
import com.aspose.words.*;

public class DetectMissingFontsDemo {
    public static void main(String[] args) {
        try {
            // 1️⃣ Create LoadOptions
            LoadOptions loadOptions = new LoadOptions();

            // 2️⃣ Attach warning callback (detect missing fonts)
            loadOptions.setWarningCallback(new IWarningCallback() {
                @Override
                public void warning(WarningInfo info) {
                    if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                        System.out.println("[Missing Font] " + info.getDescription());
                    }
                }
            });

            // 3️⃣ (Optional) Set up automatic font substitution
            FontSettings fontSettings = new FontSettings();
            fontSettings.getSubstitutionSettings()
                        .getTableSubstitution()
                        .addSubstitutes("MyCustomFont", new String[]{"Times New Roman"});
            loadOptions.setFontSettings(fontSettings);

            // 4️⃣ Load the document with custom loading behavior
            String docPath = "YOUR_DIRECTORY/doc-with-missing-font.docx";
            Document doc = new Document(docPath, loadOptions);

            // 5️⃣ Save to PDF to see the final result (optional)
            doc.save("output.pdf");
            System.out.println("Document loaded and saved successfully.");

        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}
```

**Oczekiwany wynik**

```
[Missing Font] Font substitution: The font "MyCustomFont" was not found. Substituted with "Times New Roman".
Document loaded and saved successfully.
```

Masz teraz odtwarzalny sposób na **wykrywanie brakujących czcionek**, **obsługę brakujących czcionek** oraz **dostosowanie ładowania dokumentu** — wszystko dzięki poznaniu, jak poprawnie **ustawić callback**.

---

## Najczęściej zadawane pytania

### Co zrobić, jeśli chcę, aby program przestał ładować, gdy brakuje czcionki?

Rzuć wyjątek wewnątrz metody `warning`:

```java
throw new RuntimeException("Critical: Missing font - " + info.getDescription());
```

Blok catch na końcu przechwyci go, i możesz zdecydować, jak logować lub powiadomić użytkownika.

### Czy to działa dla PDF‑ów generowanych z DOCX?

Zdecydowanie tak. Callback wywoływany jest w fazie **ładowania**, która jest identyczna dla wszystkich formatów wyjściowych (`save` do PDF, DOCX, HTML, itp.). Pod warunkiem, że załadujesz dokument źródłowy z tymi samymi `LoadOptions`, wykryjesz brakujące czcionki zanim wpłyną na końcowy PDF.

### Czy mogę przechwycić inne typy ostrzeżeń (np. konwersję obrazów)?

Tak — `WarningInfo.getWarningType()` może być porównywane z innymi enumami, takimi jak `WarningType.IMAGE_CONVERSION`. Po prostu dodaj więcej gałęzi `if` w callbacku.

### Czy to ma wpływ na wydajność?

Znikomy. Callback działa synchronicznie podczas ładowania, a dodatkowe sprawdzenia są lekkie. Jeśli ładujesz tysiące dokumentów, możesz wyłączyć ostrzeżenia w produkcji, ustawiając `loadOptions.setWarningCallback(null);`.

---

## Przegląd wizualny

![jak ustawić callback przykład w Aspose.Words Java](https://example.com/images/callback-diagram.png "jak ustawić callback")

*Diagram ilustruje przepływ: `LoadOptions` → `IWarningCallback` → Ładowanie dokumentu → Obsługa podmiany czcionek.*

---

## Podsumowanie

Omówiliśmy **jak ustawić callback** w Aspose.Words Java, zademonstrowaliśmy **wykrywanie brakujących czcionek**, pokazaliśmy praktyczne sposoby **obsługi brakujących czcionek** oraz wyjaśniliśmy, jak **dostosować ładowanie dokumentu** przy użyciu `LoadOptions`.  

Uzbrojony w tę wiedzę, możesz teraz zabezpieczyć swoje pipeline’y dokumentów przed cichymi podmianami czcionek, utrzymać spójność marki i zapewnić użytkownikom jasną informację zwrotną, gdy coś pójdzie nie tak.

### Co dalej?

- Zbadaj **tabele podmiany czcionek** do masowego mapowania wielu brakujących czcionek.  
- Połącz ten callback z **walidacją dokumentu**, aby wymusić wytyczne stylu.  
- Wypróbuj **niestandardowe callbacki ostrzeżeń**, które zapisują do pliku logu lub systemu monitorowania zamiast `System.out`.  

Śmiało eksperymentuj i daj nam znać, jak dostosowałeś callback do własnych projektów. Szczęśliwego kodowania!

---

## Co powinieneś nauczyć się dalej?

Poniższe samouczki obejmują ściśle powiązane tematy, które rozwijają techniki przedstawione w tym przewodniku. Każdy zasób zawiera kompletne działające przykłady kodu z krok po kroku wyjaśnieniami, aby pomóc Ci opanować dodatkowe funkcje API i odkrywać alternatywne podejścia implementacyjne w własnych projektach.

- [Jak ustawić LoadOptions w Aspose.Words dla Java](/words/english/java/document-loading-and-saving/using-load-options/)
- [Jak wykrywać czcionki w Aspose.Words – obsługa ostrzeżeń i ustawień](/words/english/net/working-with-fonts/how-to-detect-fonts-in-aspose-words-handle-warnings-settings/)
- [Jak przechwytywać czcionki w Aspose.Words – kompletny przewodnik](/words/english/net/working-with-fonts/how-to-capture-fonts-in-aspose-words-complete-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}