---
category: general
date: 2026-06-27
description: Poznaj sposób przechwytywania ostrzeżeń o podstawianiu czcionek w Javie
  przy użyciu Aspose.Words. Ten samouczek krok po kroku obejmuje również wywołania
  zwrotne ostrzeżeń i użycie klasy LoadOptions.
draft: false
keywords:
- capture font substitution warnings
- Aspose.Words warning callback
- Java LoadOptions example
- font substitution handling
- document processing with Aspose
language: pl
og_description: Rejestruj ostrzeżenia o zamianie czcionek w Javie przy użyciu Aspose.Words.
  Skorzystaj z tego przewodnika, aby skonfigurować wywołania zwrotne ostrzeżeń, używać
  LoadOptions i obsługiwać brakujące czcionki.
og_title: Przechwytywanie ostrzeżeń o zastępowaniu czcionek w Javie – Poradnik Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-06-27'
  description: Learn how to capture font substitution warnings in Java using Aspose.Words.
    This step‑by‑step tutorial also covers warning callbacks and LoadOptions usage.
  headline: Capture Font Substitution Warnings in Java with Aspose.Words – Complete
    Guide
  type: TechArticle
- questions:
  - answer: Yes. The warning callback is format‑agnostic; it fires for any document
      type that Aspose.Words loads (DOC, DOCX, RTF, HTML, etc.). The only difference
      is the set of warnings that may appear.
    question: Does this work with PDF or other formats?
  - answer: Absolutely. Inside the `warning` method, inspect `info.getWarningType()`
      for other enum values such as `WarningType.IMAGE_RESOLUTION`. Then handle them
      accordingly.
    question: Can I capture other warning types, like *image resolution* warnings?
  - answer: 'Store each `info.getDescription()` in a `List<String>` inside the callback.
      After loading, you’ll have a collection you can log, send to a monitoring service,
      or use to trigger a font‑download routine. ## Conclusion You now know **how
      to capture font substitution warnings** in Java using Aspose.Word'
    question: What if I need the list of substituted fonts after the document loads?
  type: FAQPage
tags:
- Aspose.Words
- Java
- Document Conversion
title: Zbieranie ostrzeżeń o zamianie czcionek w Javie przy użyciu Aspose.Words –
  Kompletny przewodnik
url: /pl/java/document-loading-and-saving/capture-font-substitution-warnings-in-java-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Rejestrowanie ostrzeżeń o podstawianiu czcionek w Javie z Aspose.Words – Kompletny przewodnik

Kiedykolwiek potrzebowałeś **zarejestrować ostrzeżenia o podstawianiu czcionek** podczas ładowania pliku DOCX, który używa egzotycznych krojów? Nie jesteś sam. W wielu rzeczywistych projektach — pomyśl o automatycznych generatorach raportów lub konwerterach wsadowych dokumentów — brakujące czcionki wywołują ciche podstawienia, które mogą zepsuć wierność układu.  

Na szczęście Aspose.Words oferuje czysty sposób nasłuchiwania tych ostrzeżeń. W tym samouczku przejdziemy przez konfigurowanie **LoadOptions**, podłączenie **callbacku ostrzeżeń Aspose.Words** oraz wypisywanie każdego powiadomienia o *podstawianiu czcionki* na konsolę. Po zakończeniu będziesz dokładnie wiedział, kiedy czcionka została zamieniona i jak zareagować programowo.

> **Co otrzymasz:** w pełni działający fragment kodu w Javie, wyjaśnienie *dlaczego* każdy element ma znaczenie oraz wskazówki dotyczące obsługi przypadków brzegowych, takich jak własne katalogi czcionek.

## Wymagania wstępne i co będzie potrzebne

Zanim zaczniemy, upewnij się, że masz:

- Java 8 lub nowszą (kod działa również z Java 11+).
- Najnowszy plik JAR Aspose.Words for Java (pobierz ze strony producenta lub z Maven Central).
- Plik DOCX, który odwołuje się do czcionek niezainstalowanych w Twoim systemie (np. *font‑rich.docx* dostępny w zestawie demo Aspose).
- Porządny IDE (IntelliJ IDEA, Eclipse lub nawet VS Code z rozszerzeniami Java).

Nie są wymagane żadne zewnętrzne biblioteki poza Aspose.Words, a przykład działa w zwykłej metodzie `main`.

## Krok 1: Konfiguracja LoadOptions – punkt wejścia dla własnego ładowania

`LoadOptions` to worek konfiguracyjny Aspose.Words, który mówi bibliotece *jak* odczytać dokument. Domyślnie cicho podstawia brakujące czcionki, ale możesz zmienić to zachowanie przy pomocy callbacku ostrzeżeń.

```java
import com.aspose.words.*;

public class FontWarningDemo {
    public static void main(String[] args) throws Exception {

        // Step 1: Create LoadOptions to customize loading behavior
        LoadOptions loadOptions = new LoadOptions();
```

**Dlaczego to ważne:** Bez `LoadOptions` dokument ładuje się po cichu i tracisz widoczność brakujących czcionek. Tworząc instancję, uzyskujesz hak do systemu ostrzeżeń.

## Krok 2: Definiowanie callbacku ostrzeżeń w celu *złapania ostrzeżeń o podstawianiu czcionek*

Aspose.Words wysyła zdarzenia ostrzeżeń przez interfejs `IWarningCallback`. Zaimplementuj go w miejscu (lub jako osobną klasę) i filtruj pod kątem `WarningType.FONT_SUBSTITUTION`.

```java
        // Step 2: Define a warning callback to capture font substitution warnings
        loadOptions.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) {
                // Only react to font substitution warnings
                if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                    System.out.println("Font substituted: " + info.getDescription());
                }
            }
        });
```

**Wyjaśnienie:**  
- `info.getWarningType()` podaje kategorię ostrzeżenia.  
- `WarningType.FONT_SUBSTITUTION` to wartość wyliczeniowa, którą nas interesuje.  
- `info.getDescription()` zawiera czytelną wiadomość, np. *„Font 'Comic Sans MS' not found, substituted with 'Arial'.”*  

Wypisując opis, **rejestrujesz ostrzeżenia o podstawianiu czcionek** w czasie rzeczywistym.

## Krok 3: Ładowanie dokumentu przy użyciu skonfigurowanego LoadOptions

Teraz, gdy callback jest gotowy, załaduj swój DOCX. Callback ostrzeżeń uruchamia się automatycznie podczas parsowania.

```java
        // Step 3: Load the document using the configured LoadOptions
        Document document = new Document("YOUR_DIRECTORY/font-rich.docx", loadOptions);
```

Zastąp `YOUR_DIRECTORY` rzeczywistą ścieżką do pliku testowego. Gdy konstruktor `Document` zostanie wywołany, każde brakujące fonty wywołają wcześniej zdefiniowany callback i zobaczysz komunikaty o podstawieniach na konsoli.

## Krok 4: Weryfikacja załadowanego dokumentu (opcjonalnie, ale przydatna)

Po załadowaniu możesz chcieć potwierdzić integralność dokumentu — liczbę stron, wyodrębniony tekst itp. Ten krok nie jest wymagany do rejestrowania ostrzeżeń, ale pomaga zobaczyć wpływ podstawień.

```java
        // Optional: Output basic document info
        System.out.println("Document loaded successfully.");
        System.out.println("Page count: " + document.getPageCount());
```

Jeśli czcionka została podstawiona, układ może nieco się przesunąć; sprawdzenie liczby stron może ujawnić takie zmiany.

## Krok 5: Zaawansowane – programowa obsługa podstawionych czcionek

Czasami nie chcesz jedynie logować ostrzeżenia — możesz potrzebować osadzić czcionkę zapasową lub dostosować styl. Poniżej szybki wzorzec, który możesz przyjąć.

```java
        // Advanced: Register a fallback font folder to reduce substitutions
        FontSettings fontSettings = new FontSettings();
        // Point to a folder that contains the missing fonts
        fontSettings.setFontsFolder("YOUR_DIRECTORY/custom-fonts", true);
        loadOptions.setFontSettings(fontSettings);
```

Wskazując Aspose.Words na folder zawierający oryginalne czcionki, możesz *zapobiec* podstawieniu całkowicie. Jeśli folderu brak, callback ostrzeżeń nadal przechwytuje zdarzenie, dając Ci strategię awaryjną.

## Pełny działający przykład

Łącząc wszystko, oto kompletny, gotowy do uruchomienia program:

```java
import com.aspose.words.*;

public class FontWarningDemo {
    public static void main(String[] args) throws Exception {

        // Initialize LoadOptions
        LoadOptions loadOptions = new LoadOptions();

        // Set up warning callback to capture font substitution warnings
        loadOptions.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) {
                if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                    System.out.println("Font substituted: " + info.getDescription());
                }
            }
        });

        // OPTIONAL: Register a custom fonts folder to avoid substitution
        FontSettings fontSettings = new FontSettings();
        fontSettings.setFontsFolder("YOUR_DIRECTORY/custom-fonts", true);
        loadOptions.setFontSettings(fontSettings);

        // Load the document – warnings will be printed automatically
        Document doc = new Document("YOUR_DIRECTORY/font-rich.docx", loadOptions);

        // Verify basic info
        System.out.println("Document loaded successfully.");
        System.out.println("Page count: " + doc.getPageCount());
    }
}
```

**Oczekiwany wynik w konsoli** (gdy napotkano brakującą czcionkę):

```
Font substituted: Font 'Pacifico' not found, substituted with 'Arial'.
Document loaded successfully.
Page count: 3
```

Jeśli wszystkie czcionki są dostępne, callback pozostaje cichy — nic nie zostanie wypisane, co jest dokładnie tym, czego się spodziewasz.

## Typowe pułapki i wskazówki profesjonalne

| Pułapka | Dlaczego się pojawia | Rozwiązanie |
|---------|----------------------|-------------|
| **Callback nigdy się nie wywołuje** | Zapomniałeś podłączyć callback do `LoadOptions` **lub** użyłeś domyślnego konstruktora `Document` bez przekazania `loadOptions`. | Zawsze wywołuj `loadOptions.setWarningCallback(...)` **i** używaj przeciążenia `new Document(path, loadOptions)`. |
| **Zbyt wiele ostrzeżeń zapełnia log** | Duże dokumenty z wieloma brakującymi czcionkami generują ostrzeżenie dla każdego podstawienia. | Dodatkowo filtruj po `info.getDescription()` pod kątem konkretnych nazw czcionek lub agreguj ostrzeżenia w liście do późniejszego przetworzenia. |
| **Podstawione czcionki wpływają na układ** | Czcionka zapasowa może mieć inne metryki (rozmiar, odstępy). | Udostępnij własny folder czcionek (patrz Krok 5) lub po załadowaniu dostosuj style dokumentu. |
| **Uruchamianie na serwerze bez interfejsu graficznego** | Domyślne podstawienie może polegać na systemowych czcionkach, które nie są zainstalowane na serwerze. | Dołącz wymagane czcionki do aplikacji i wskaż `FontSettings` na ten folder. |

## Najczęściej zadawane pytania

**P: Czy to działa z PDF‑ami lub innymi formatami?**  
O: Tak. Callback ostrzeżeń jest niezależny od formatu; uruchamia się dla każdego typu dokumentu, który Aspose.Words ładuje (DOC, DOCX, RTF, HTML itp.). Jedyną różnicą jest zestaw ostrzeżeń, które mogą się pojawić.

**P: Czy mogę przechwycić inne typy ostrzeżeń, np. ostrzeżenia o rozdzielczości obrazów?**  
O: Oczywiście. W metodzie `warning` sprawdzaj `info.getWarningType()` pod kątem innych wartości wyliczeniowych, takich jak `WarningType.IMAGE_RESOLUTION`. Następnie obsłuż je zgodnie z potrzebami.

**P: Co zrobić, jeśli potrzebuję listy podstawionych czcionek po załadowaniu dokumentu?**  
O: Przechowuj każdy `info.getDescription()` w `List<String>` wewnątrz callbacku. Po załadowaniu będziesz mieć kolekcję, którą możesz logować, wysłać do usługi monitorującej lub użyć do uruchomienia procedury pobierania czcionek.

## Podsumowanie

Wiesz już **jak przechwycić ostrzeżenia o podstawianiu czcionek** w Javie przy użyciu Aspose.Words, dlaczego każdy element układanki ma znaczenie oraz jak rozszerzyć rozwiązanie na scenariusze produkcyjne. Dzięki `LoadOptions`, callbackowi ostrzeżeń Aspose.Words oraz opcjonalnemu `FontSettings` zyskujesz pełną widoczność brakujących czcionek i możesz utrzymać niezawodność swoich potoków konwersji dokumentów.

Gotowy na kolejny krok? Spróbuj zamienić `System.out.println` na logger, np. SLF4J, lub zintegrować listę ostrzeżeń z interfejsem UI, który ostrzeże użytkowników przed finalizacją konwersji wsadowej. Możesz także zbadać **callback ostrzeżeń Aspose.Words** pod kątem innych typów ostrzeżeń, takich jak *nieobsługiwane funkcje* czy alerty o *wysokiej rozdzielczości obrazów*.  

Miłego kodowania i niech Twoje PDF‑y nigdy nie cierpią z powodu nieoczekiwanych podstawień czcionek! 

![Zrzut ekranu pokazujący wyjście konsoli z przechwyconymi ostrzeżeniami o podstawianiu czcionek](image-placeholder.png "przechwytywanie ostrzeżeń o podstawianiu czcionek")


## Co warto nauczyć się dalej?


Poniższe samouczki dotyczą ściśle powiązanych tematów, które rozwijają techniki przedstawione w tym przewodniku. Każdy zasób zawiera kompletne przykłady kodu oraz szczegółowe wyjaśnienia, aby pomóc Ci opanować dodatkowe funkcje API i odkrywać alternatywne podejścia w własnych projektach.

- [Włącz ostrzeżenia o podstawianiu czcionek w Aspose.Words – Kompletny przewodnik](/words/english/net/working-with-fonts/enable-font-substitution-warnings-in-aspose-words-complete-g/)
- [Jak ustawić LoadOptions w Aspose.Words for Java](/words/english/java/document-loading-and-saving/using-load-options/)
- [Jak tworzyć dokumenty PDF przy użyciu Aspose.Words for Java | Document Processing API](/words/english/java/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}