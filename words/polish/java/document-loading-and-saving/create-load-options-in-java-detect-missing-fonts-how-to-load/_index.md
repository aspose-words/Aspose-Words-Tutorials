---
category: general
date: 2026-02-18
description: Utwórz opcje ładowania w Javie, aby wykrywać brakujące czcionki i dowiedz
  się, jak ładować pliki DOCX z wywołaniem zwrotnym ostrzeżenia.
draft: false
keywords:
- create load options
- detect missing fonts
- how to load docx
- Aspose.Words warning callback
- Java document processing
language: pl
og_description: Utwórz opcje ładowania w Javie, aby wykrywać brakujące czcionki i
  dowiedz się, jak ładować pliki DOCX z wywołaniem zwrotnym ostrzeżenia.
og_title: Utwórz opcje ładowania w Javie – wykryj brakujące czcionki i jak załadować
  DOCX
tags:
- java
- aspose-words
- document-processing
title: Utwórz opcje ładowania w Javie – wykryj brakujące czcionki i jak załadować
  DOCX
url: /pl/java/document-loading-and-saving/create-load-options-in-java-detect-missing-fonts-how-to-load/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Utwórz opcje ładowania w Javie – wykrywanie brakujących czcionek i jak ładować DOCX

Zastanawiałeś się kiedyś, jak **utworzyć opcje ładowania**, które nie tylko odczytują plik DOCX, ale także informują, gdy brakuje czcionki? Nie jesteś jedyny. Brakujące czcionki mogą zamienić perfekcyjnie sformatowany dokument w nieczytelny bałagan, a ich wczesne wykrycie oszczędza godziny debugowania. W tym samouczku przejdziemy przez dokładne kroki, aby **wykrywać brakujące czcionki**, jednocześnie pokazując **jak ładować pliki DOCX** z własnym callbackiem ostrzeżeń.

## Czego się nauczysz

- Jak zainstancjonować `LoadOptions` i skonfigurować obsługę ostrzeżeń.  
- Dlaczego callback ostrzeżeń jest niezbędny do przechwytywania problemów z podstawianiem czcionek.  
- Dokładny kod potrzebny do **bezpiecznego ładowania pliku DOCX**, plus kilka praktycznych wskazówek dla projektów produkcyjnych.  
- Obsługa przypadków brzegowych, takich jak radzenie sobie z innymi typami ostrzeżeń lub ładowanie PDF‑ów tym samym podejściem.

Nie potrzebujesz żadnej zewnętrznej dokumentacji – wszystko, co potrzebne, znajduje się tutaj.

## Wymagania wstępne

- Java 17 lub nowsza (API działa także na starszych wersjach, ale 17 to optymalny wybór).  
- Biblioteka Aspose.Words for Java dodana do projektu (`aspose-words-x.x.jar`).  
- Podstawowa znajomość obsługi wyjątków w Javie.  

Jeśli masz te elementy, zaczynamy.

![Diagram przedstawiający przepływ tworzenia opcji ładowania, ustawiania callbacku ostrzeżeń i ładowania pliku DOCX](/images/create-load-options-diagram.png){: .center-image alt="Diagram przepływu tworzenia opcji ładowania, ustawiania callbacku ostrzeżeń i ładowania pliku DOCX"}

## Krok 1: Utwórz opcje ładowania (Jak ładować DOCX)

Pierwszą rzeczą, którą musisz zrobić, jest **utworzenie opcji ładowania**. Ten obiekt mówi Aspose.Words, jak zachowywać się przy otwieraniu pliku. Pomyśl o nim jako o zestawie instrukcji, które przekazujesz bibliotece, zanim jeszcze zobaczy ona DOCX.

```java
// Step 1: Instantiate LoadOptions
LoadOptions loadOptions = new LoadOptions();
```

Dlaczego nie po prostu wywołać `new Document("file.docx")`? Ponieważ bez `LoadOptions` tracisz możliwość reagowania na ostrzeżenia – takie jak brakujące czcionki – dopiero po załadowaniu dokumentu, co może być za późno w niektórych przepływach pracy.

## Krok 2: Skonfiguruj callback ostrzeżeń, aby wykrywać brakujące czcionki

Teraz podłączamy callback, który zostanie wywołany za każdym razem, gdy Aspose.Words napotka sytuację, o której chce Cię ostrzec. W naszym przypadku interesuje nas `WarningType.FONT_SUBSTITUTION`.

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

Kilka uwag:

- **Dlaczego callback?** Działa *w trakcie* procesu ładowania, dając Ci szansę zalogowania lub nawet przerwania operacji przed pełnym utworzeniem dokumentu.  
- **Dlaczego sprawdzać `WarningType.FONT_SUBSTITUTION`?** To dokładna wartość wyliczeniowa używana przez Aspose.Words w scenariuszach brakujących czcionek. Inne typy ostrzeżeń (np. `TABLE_STRUCTURE`) można filtrować w podobny sposób, jeśli są potrzebne.  
- **Wskazówka dotycząca wydajności:** Callback jest lekki; unikaj ciężkich operacji I/O wewnątrz niego. Jeśli musisz zapisywać do pliku, kolejkowanie komunikatów i ich zapis po zakończeniu ładowania jest lepszym rozwiązaniem.

## Krok 3: Załaduj plik DOCX z skonfigurowanymi opcjami

Gdy opcje i callback są gotowe, możesz w końcu załadować DOCX. To część, która odpowiada na pytanie **jak ładować docx**, jednocześnie respektując ustawione ostrzeżenia.

```java
// Step 3: Load the document using the configured LoadOptions
try {
    Document document = new Document("YOUR_DIRECTORY/input.docx", loadOptions);
    System.out.println("Document loaded successfully.");
} catch (Exception e) {
    System.err.println("Failed to load document: " + e.getMessage());
}
```

**Co się dzieje „pod maską”?** Podczas strumieniowego odczytu pliku Aspose.Words sprawdza każdy odwołanie do czcionki. Jeśli wymagana czcionka nie jest zainstalowana, wywołuje zdefiniowany wcześniej callback ostrzeżeń. Zobaczysz wyjście podobne do:

```
Missing font detected: Font 'Calibri' is not installed. Substituted with 'Arial'.
Document loaded successfully.
```

Ta natychmiastowa informacja zwrotna jest bezcenna, gdy przetwarzasz partie plików na serwerze.

## Pełny działający przykład

Łącząc wszystko razem, oto samodzielny program, który możesz skopiować i wkleić do swojego IDE.

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

**Oczekiwany wynik**

```
Missing font: Font 'Times New Roman' is not installed. Substituted with 'Arial'.
DOCX loaded – you can now work with it.
```

Jeśli plik nie zawiera brakujących czcionek, callback pozostaje cichy, a linijka „DOCX loaded” pojawia się w konsoli.

## Porady profesjonalne i przypadki brzegowe

| Sytuacja | Co zrobić |
|-----------|------------|
| **Wiele brakujących czcionek** | Callback wywołuje się dla każdej z nich, więc otrzymasz osobną linię dla każdej czcionki. Zbierz je w `List<String>`, jeśli potrzebujesz podsumowania później. |
| **Chcesz przechwytywać także inne ostrzeżenia** | Dodaj gałęzie `else if` dla `WarningType.TABLE_STRUCTURE`, `WarningType.UNKNOWN_FILE_FORMAT` itp. |
| **Ładowanie dużych plików DOCX** | Użyj `LoadOptions.setLoadFormat(LoadFormat.DOCX)`, aby podpowiedzieć format i przyspieszyć wykrywanie. |
| **Uruchamianie w usłudze webowej** | Unikaj `System.out.println`; zamiast tego wstrzyknij logger (`SLF4J`, `Log4j`) wewnątrz callbacku. |
| **Czcionki instalowane w czasie działania** | Po wykryciu brakującej czcionki możesz programowo załadować ją za pomocą `GraphicsEnvironment.registerFont(...)` i ponownie załadować dokument. |

## Dlaczego to podejście przewyższa metodę „Tylko try‑catch”

Wielu programistów po prostu otacza `new Document(...)` blokiem try‑catch, licząc, że wyjątek poinformuje ich o brakujących czcionkach. Niestety Aspose.Words traktuje podstawianie czcionek jako *ostrzeżenie*, a nie błąd, więc żaden wyjątek nie jest rzucany. Dzięki **utworzeniu opcji ładowania** i podłączeniu callbacku ostrzeżeń zyskujesz deterministyczny wgląd w problemy z czcionkami bez utraty wydajności.

## Kolejne kroki

- **Wykrywanie brakujących czcionek w PDF‑ach** – ten sam wzorzec `LoadOptions` działa również dla PDF‑ów, wystarczy zmienić ścieżkę pliku i format ładowania.  
- **Automatyzacja instalacji czcionek** – połącz callback z skryptem, który pobiera brakujące czcionki z udostępnionego repozytorium.  
- **Eksploracja innych typów ostrzeżeń** – Aspose.Words może ostrzegać o przestarzałych tagach, skomplikowanych tabelach i nie tylko.  

Śmiało eksperymentuj: zamień konstruktor `Document` na strumień (`new Document(InputStream, loadOptions)`), jeśli pracujesz z danymi w pamięci, lub łańcuchuj wiele callbacków przy użyciu wzorca kompozytu dla dużych pipeline’ów przetwarzania.

---

### TL;DR

Pokazaliśmy, jak **utworzyć opcje ładowania** w Javie, skonfigurować callback, który **wykrywa brakujące czcionki**, oraz jak **bezpiecznie załadować plik DOCX**. W trzech zwięzłych krokach masz teraz wzorzec, który można wstawić do dowolnego projektu Aspose.Words.

Masz pytania dotyczące innych formatów plików lub potrzebujesz pomocy w dostosowaniu callbacku do swojego środowiska? Zostaw komentarz poniżej i powodzenia w kodowaniu!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}