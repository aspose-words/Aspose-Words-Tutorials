---
category: general
date: 2026-06-05
description: Wykryj brakujące podstawienie czcionki w Javie przy użyciu Aspose.Words.
  Dowiedz się, jak skonfigurować LoadOptions, FontSettings i wywołania zwrotne ostrzeżeń,
  aby zapewnić niezawodne przetwarzanie dokumentów.
draft: false
keywords:
- detect missing font substitution
- Java Aspose.Words
- LoadOptions configuration
- FontSettings warning callback
- document loading Java
language: pl
og_description: wykryj brakujące podstawienie czcionki w Javie z Aspose.Words. Ten
  przewodnik pokazuje krok po kroku, jak skonfigurować LoadOptions, FontSettings i
  wywołanie zwrotne ostrzeżenia, aby wychwycić brakujące czcionki.
og_title: Wykryj brakujące podstawienie czcionki w Javie – Pełny poradnik Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-06-05'
  description: detect missing font substitution in Java using Aspose.Words. Learn
    how to configure LoadOptions, FontSettings, and warning callbacks for reliable
    document processing.
  headline: detect missing font substitution in Java – Complete Aspose.Words Guide
  type: TechArticle
- description: detect missing font substitution in Java using Aspose.Words. Learn
    how to configure LoadOptions, FontSettings, and warning callbacks for reliable
    document processing.
  name: detect missing font substitution in Java – Complete Aspose.Words Guide
  steps:
  - name: 4.1 Quick verification
    text: Run the program from your IDE or via `java -cp .;aspose-words-23.12.jar
      MissingFontDetector`. If the document references a font you don’t have, you’ll
      see the warning message printed. If the console stays silent, either the font
      exists on your machine or the document doesn’t request any missing font
  - name: 4.2 Logging instead of `System.out`
    text: 'In production code you probably want a logger:'
  - name: 4.3 Handling other warning types
    text: 'The callback receives *all* warnings, not just font issues. If you’d like
      to keep an eye on other problems (e.g., `UNKNOWN_STYLE`), add extra `if` branches.
      Here’s a quick example:'
  type: HowTo
tags:
- Aspose.Words
- Java
- Font handling
title: Wykrywanie brakującej substytucji czcionki w Javie – Kompletny przewodnik Aspose.Words
url: /pl/java/document-loading-and-saving/detect-missing-font-substitution-in-java-complete-aspose-wor/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# wykrywanie brakującej podstawy czcionki w Javie – Kompletny przewodnik Aspose.Words

Zastanawiałeś się kiedyś, jak **wykrywać brakujące podstawianie czcionek** podczas ładowania dokumentu Word w Javie? Nie jesteś jedyny. Brakujące czcionki mogą cicho zepsuć Twoje pliki PDF lub renderowane strony, a ich wczesne wykrycie oszczędza godziny debugowania. W tym samouczku przeprowadzimy praktyczne rozwiązanie, które nie tylko ładuje dokument, ale także informuje dokładnie, kiedy następuje podstawienie czcionki.

Omówimy wszystko, od tworzenia `LoadOptions` po podłączenie `WarningCallback`, który wypisuje czytelny komunikat za każdym razem, gdy Aspose.Words zamienia brakującą czcionkę. Po zakończeniu będziesz mieć wielokrotnego użytku fragment kodu działający z każdym plikiem `.docx` i zrozumiesz *dlaczego* każdy element ma znaczenie. Bez dodatkowych bibliotek, tylko czysta Java i Aspose.Words.

## Czego się nauczysz

- Jak skonfigurować **LoadOptions**, aby używał niestandardowych **FontSettings**.  
- Jak zaimplementować **IWarningCallback**, który przechwytuje ostrzeżenia `FONT_SUBSTITUTION`.  
- Jak załadować dokument, jednocześnie bezpiecznie monitorując brakujące czcionki.  
- Oczekiwany output konsoli oraz jak dostosować kod do frameworków logowania.  

**Wymagania wstępne**: zainstalowana Java 8+, Aspose.Words for Java (v23.12 lub nowszy) w classpath oraz przykładowy plik `.docx`, który odwołuje się do czcionki niezainstalowanej w systemie. To wszystko — nie są potrzebne dodatkowe narzędzia budujące.

---

## Krok 1: Konfiguracja projektu i dodanie Aspose.Words

Zanim przejdziemy do kodu, upewnij się, że Aspose.Words jest dostępny. Jeśli używasz Maven, dodaj następującą zależność do swojego `pom.xml`:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.12</version>
</dependency>
```

Jeśli wolisz Gradle, odpowiednik wygląda tak:

```gradle
implementation 'com.aspose:aspose-words:23.12'
```

Gdy biblioteka znajduje się w classpath, jesteś gotowy, aby **wykrywać brakujące podstawianie czcionek** w jednym wywołaniu metody.

---

## Krok 2: Utwórz LoadOptions i podłącz FontSettings

Sednem rozwiązania jest przygotowanie instancji `LoadOptions`, która potrafi monitorować problemy z czcionkami. Oto kod podzielony linia po linii.

```java
import com.aspose.words.*;

public class MissingFontDetector {

    public static void main(String[] args) throws Exception {
        // 1️⃣ Prepare load options – this object controls how the document is read.
        LoadOptions loadOptions = new LoadOptions();

        // 2️⃣ Create FontSettings – it holds font‑related configuration.
        FontSettings fontSettings = new FontSettings();

        // 3️⃣ Register a warning callback that will be invoked on font substitution.
        fontSettings.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) {
                // We only care about FONT_SUBSTITUTION warnings.
                if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                    System.out.println("⚠️ Font substitution detected: " + info.getMessage());
                }
            }
        });

        // 4️⃣ Attach the FontSettings to the LoadOptions.
        loadOptions.setFontSettings(fontSettings);
```

**Dlaczego to ważne**: `LoadOptions` informuje Aspose.Words *jak* interpretować wczytywany plik. Podłączając spersonalizowane `FontSettings`, dajemy ładowarce hak (`IWarningCallback`), który wywołuje się **dokładnie w momencie, gdy brakująca czcionka zostaje podstawiona**. Bez tego callbacku Aspose.Words cicho zamieni czcionkę i nigdy się o tym nie dowiesz.

---

## Krok 3: Załaduj dokument z skonfigurowanymi opcjami

Gdy system ostrzeżeń jest już gotowy, ładowanie dokumentu staje się proste.

```java
        // 5️⃣ Load the document using the prepared options.
        // Replace the path with the location of your test file.
        String docPath = "YOUR_DIRECTORY/docWithMissingFont.docx";
        Document doc = new Document(docPath, loadOptions);

        // Optional: do something with the document (e.g., save as PDF).
        // doc.save("output.pdf");
    }
}
```

Gdy wywołanie `new Document(...)` zostanie wykonane, Aspose.Words odczytuje plik, sprawdza każde odwołanie do czcionki i jeśli nie znajdzie pasującej czcionki w systemie, wywołuje metodę `warning`, którą zdefiniowaliśmy wcześniej. Konsola natychmiast wyświetli wiersz podobny do:

```
⚠️ Font substitution detected: Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
```

Ten wiersz jest wynikiem **wykrywania brakującej podstawy czcionki**, którego szukałeś.

---

## Krok 4: Zweryfikuj wynik i dostosuj callback (zaawansowane)

### 4.1 Szybka weryfikacja

Uruchom program z IDE lub za pomocą `java -cp .;aspose-words-23.12.jar MissingFontDetector`. Jeśli dokument odwołuje się do czcionki, której nie masz, zobaczysz wypisane ostrzeżenie. Jeśli konsola pozostaje cicha, to znaczy, że czcionka istnieje w systemie lub dokument nie wymaga żadnych brakujących czcionek.

### 4.2 Logowanie zamiast `System.out`

W kodzie produkcyjnym prawdopodobnie będziesz chciał używać loggera:

```java
import java.util.logging.Logger;

private static final Logger logger = Logger.getLogger(MissingFontDetector.class.getName());

fontSettings.setWarningCallback(info -> {
    if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
        logger.warning("Font substitution: " + info.getMessage());
    }
});
```

Ta mała zmiana sprawia, że mechanizm **wykrywania brakującej podstawy czcionki** współpracuje płynnie z istniejącymi potokami logowania.

### 4.3 Obsługa innych typów ostrzeżeń

Callback otrzymuje *wszystkie* ostrzeżenia, nie tylko te związane z czcionkami. Jeśli chcesz monitorować inne problemy (np. `UNKNOWN_STYLE`), dodaj dodatkowe gałęzie `if`. Oto szybki przykład:

```java
if (info.getWarningType() == WarningType.UNKNOWN_STYLE) {
    logger.info("Unknown style encountered: " + info.getMessage());
}
```

---

## Krok 5: Typowe pułapki i wskazówki profesjonalne

| Pułapka | Dlaczego się dzieje | Rozwiązanie |
|--------|----------------------|-------------|
| **Brak ostrzeżenia** | Czcionka faktycznie istnieje w systemie operacyjnym, lub dokument używa zastępczej czcionki, którą Aspose.Words traktuje jako „znalezioną”. | Usuń czcionkę z systemu tymczasowo lub użyj naprawdę nieistniejącej nazwy czcionki w dokumencie źródłowym. |
| **Callback nigdy nie wywoływany** | `setWarningCallback` został wywołany na *innym* obiekcie `FontSettings` niż ten podłączony do `LoadOptions`. | Upewnij się, że wywołujesz `loadOptions.setFontSettings(fontSettings)` **po** skonfigurowaniu callbacku. |
| **Spowolnienie wydajności** | Ładowanie wielu dużych dokumentów z callbackami może wprowadzać dodatkowy narzut. | Zachowaj jedną instancję `FontSettings` w pamięci podręcznej i używaj jej przy kolejnych ładowaniach, jeśli przetwarzasz partie dokumentów. |
| **Wiele wątków** | `FontSettings` nie jest domyślnie bezpieczny wątkowo. | Utwórz osobny `FontSettings` dla każdego wątku lub synchronizuj dostęp. |

**Wskazówka profesjonalna**: Jeśli generujesz PDF-y dla usługi webowej, możesz chcieć zbierać wszystkie ostrzeżenia o podstawianiu czcionek w liście i zwracać je w odpowiedzi API, zamiast wypisywać je na konsolę.

---

## Pełny działający przykład (gotowy do kopiowania i wklejenia)

```java
import com.aspose.words.*;

public class MissingFontDetector {
    public static void main(String[] args) throws Exception {
        // Prepare load options
        LoadOptions loadOptions = new LoadOptions();

        // Configure font settings with a warning callback
        FontSettings fontSettings = new FontSettings();
        fontSettings.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) {
                if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                    System.out.println("⚠️ Font substitution detected: " + info.getMessage());
                }
            }
        });

        // Attach font settings to load options
        loadOptions.setFontSettings(fontSettings);

        // Path to the document that contains a missing font
        String docPath = "YOUR_DIRECTORY/docWithMissingFont.docx";

        // Load the document – this triggers the callback if needed
        Document doc = new Document(docPath, loadOptions);

        // Optional: save as PDF to verify visual output
        // doc.save("output.pdf");

        System.out.println("Document loaded successfully.");
    }
}
```

**Oczekiwany output konsoli** (zakładając, że plik odwołuje się do brakującej czcionki):

```
⚠️ Font substitution detected: Font 'Papyrus' was not found. Substituted with 'Times New Roman'.
Document loaded successfully.
```

Jeśli brak brakujących czcionek, zobaczysz tylko ostatni wiersz „Document loaded successfully.”

---

## Podsumowanie

Właśnie pokazaliśmy, jak **wykrywać brakujące podstawianie czcionek** w Javie przy użyciu Aspose.Words. Konfigurując `LoadOptions`, tworząc instancję `FontSettings` i podłączając `IWarningCallback`, uzyskujesz pełną widoczność każdego zamienianego przez bibliotekę fontu. To podejście nie tylko zapobiega cichym błędom renderowania, ale także daje możliwość logowania, powiadamiania lub nawet automatycznego osadzania czcionek zastępczych.

Od tego momentu możesz:

- Rozszerzyć callback, aby zbierał ostrzeżenia w listę dla odpowiedzi API.  
- Połączyć tę technikę z **konfiguracją LoadOptions** w innych scenariuszach (np. własne ładowanie zasobów).  
- Poznać szerszy ekosystem **Java Aspose.Words**: konwertowanie do PDF, wyodrębnianie tekstu lub wykonywanie scalania korespondencji.

Wypróbuj to, dostosuj logger, i pozwól swoim aplikacjom zgłaszać, gdy czcionka zniknie. Szczęśliwego kodowania!

## Co warto nauczyć się dalej?

Poniższe samouczki obejmują ściśle powiązane tematy, które rozwijają techniki przedstawione w tym przewodniku. Każde źródło zawiera kompletne działające przykłady kodu z wyjaśnieniami krok po kroku, aby pomóc Ci opanować dodatkowe funkcje API i odkrywać alternatywne podejścia implementacyjne w własnych projektach.

- [Przechwytywanie ostrzeżeń o podstawianiu czcionek w Javie z Aspose.Words – Kompletny przewodnik](/words/english/java/document-loading-and-saving/capture-font-substitution-warnings-in-java-with-aspose-words/)
- [Używanie opcji i ustawień dokumentu w Aspose.Words dla Javy](/words/english/java/document-manipulation/using-document-options-and-settings/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}