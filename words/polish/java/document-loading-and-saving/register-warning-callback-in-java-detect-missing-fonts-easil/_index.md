---
category: general
date: 2026-07-03
description: Zarejestruj wywołanie zwrotne ostrzeżeń w Javie, aby wykrywać brakujące
  czcionki podczas przetwarzania dokumentów Word. Dowiedz się, jak obsługiwać ostrzeżenia
  w Aspose.Words i wykrywać podstawianie czcionek.
draft: false
keywords:
- register warning callback
- detect missing fonts
- font substitution warning
- Aspose.Words warning callback
- Java missing font detection
- document font handling
language: pl
og_description: Zarejestruj callback ostrzeżeń w Javie, aby wykrywać brakujące czcionki.
  Ten przewodnik pokazuje, jak przechwycić ostrzeżenia o podstawianiu czcionek przy
  użyciu Aspose.Words.
og_title: Zarejestruj wywołanie zwrotne ostrzeżenia w Javie – Wykryj brakujące czcionki
schemas:
- author: Aspose
  dateModified: '2026-07-03'
  description: Register warning callback in Java to detect missing fonts while processing
    Word docs. Learn Aspose.Words warning handling and font substitution detection.
  headline: Register warning callback in Java – Detect missing fonts easily
  type: TechArticle
- description: Register warning callback in Java to detect missing fonts while processing
    Word docs. Learn Aspose.Words warning handling and font substitution detection.
  name: Register warning callback in Java – Detect missing fonts easily
  steps:
  - name: Why this matters
    text: '* **Visibility:** Without a callback, the substitution happens silently,
      and you might ship a document with the wrong appearance. * **Automation:** In
      batch pipelines you can log every missing‑font incident and later feed the list
      to a font‑installation script. * **Compliance:** Some industries (e.g'
  - name: Expected console output
    text: 'Assuming `input.docx` references the font *“Comic Sans MS”* which isn’t
      installed, you’ll see something like:'
  - name: Multiple missing fonts
    text: If a document references several unavailable fonts, the callback will fire
      once per font. You can aggregate the messages into a list if you need a summary
      report later.
  - name: Controlling substitution behavior
    text: 'Sometimes you *do* want to force a particular fallback font. Use `FontSettings`
      before loading the document:'
  - name: Performance considerations
    text: 'Registering a warning callback introduces a tiny overhead—only a few nanoseconds
      per warning. In high‑throughput services (e.g., converting thousands of docs
      per hour) the impact is negligible. However, if you’re processing millions,
      consider disabling warnings after you’ve verified the font set is '
  - name: Cross‑platform notes
    text: The callback works identically on Windows, macOS, and Linux. The only difference
      is the set of fonts available on each OS. If you run the same job on multiple
      agents, you might see different substitution messages. To keep results deterministic,
      ship a **custom font folder** and point Aspose.Words to
  type: HowTo
tags:
- Aspose.Words
- Java
- Fonts
title: Zarejestruj wywołanie zwrotne ostrzeżenia w Javie – Łatwo wykrywaj brakujące
  czcionki
url: /pl/java/document-loading-and-saving/register-warning-callback-in-java-detect-missing-fonts-easil/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Zarejestruj callback ostrzeżenia w Javie – Łatwo wykrywać brakujące czcionki

Zastanawiałeś się kiedyś, jak **zarejestrować callback ostrzeżenia**, aby **wykrywać brakujące czcionki** podczas konwertowania lub edytowania dokumentów Word? Nie jesteś jedyny. Brakujące czcionki mogą po cichu psuć układy, zamienić elegancki raport w zniekształcony bałagan, a większość programistów nie zdaje sobie sprawy, dopóki ostateczny PDF nie wygląda niepoprawnie.  

W tym samouczku przeprowadzimy Cię przez kompletny, gotowy do uruchomienia przykład, który pokaże dokładnie, jak podłączyć się do systemu ostrzeżeń Aspose.Words for Java, przechwycić te uciążliwe alerty o podstawianiu czcionek i zalogować je lub zareagować w dowolny sposób. Bez niejasnych „zobacz dokumentację” skrótów — tylko czysty kod do kopiowania i wklejania oraz wyjaśnienie każdej linii.

## Wymagania wstępne

* **Java 17** (lub dowolny nowszy JDK) zainstalowany i ustawiony `JAVA_HOME`.  
* **Aspose.Words for Java** JAR (pobierz z oficjalnej strony lub pobierz przez Maven).  
* Przykładowy plik `.docx`, który odwołuje się do czcionki **nie**zainstalowanej na twoim komputerze — to wywoła ostrzeżenie.  
* Twoje ulubione IDE lub prosty edytor tekstu oraz narzędzia budowania w wierszu poleceń.

To wszystko. Bez dodatkowych frameworków, bez zewnętrznych usług. Gotowy? Zaczynamy.

## Krok 1: Skonfiguruj projekt i dodaj Aspose.Words

Jeśli używasz Maven, dodaj następującą zależność do swojego `pom.xml`:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.10</version> <!-- use the latest stable version -->
</dependency>
```

Dla Gradle, wstaw to do `build.gradle`:

```groovy
implementation 'com.aspose:aspose-words:24.10'
```

Jeśli wolisz ręczną metodę, po prostu umieść `aspose-words-24.10.jar` na swojej ścieżce klas.  
**Pro tip:** trzymaj JAR obok folderu `src`; ułatwi to późniejsze polecenie `javac`.

## Krok 2: Załaduj dokument, który może zawierać brakujące czcionki

Pierwszą rzeczą, którą robisz, jest stworzenie obiektu `Document` wskazującego na plik źródłowy. Ten krok jest prosty, ale to także moment, w którym biblioteka skanuje plik i *potencjalnie* wykrywa brakujące czcionki.

```java
import com.aspose.words.*;

public class FontWarningDemo {
    public static void main(String[] args) throws Exception {
        // Adjust the path to point at your test document
        String inputPath = "YOUR_DIRECTORY/input.docx";

        // Load the document – Aspose.Words will start parsing it now
        Document doc = new Document(inputPath);
```

Tutaj `Document` jest punktem wejścia dla wszystkich operacji Aspose.Words. Gdy uruchamia się konstruktor, biblioteka parsuje XML dokumentu, rozwiązuje czcionki i, jeśli jakieś czcionki są niedostępne, *kolejkuje* ostrzeżenie, które później możemy przechwycić.

## Krok 3: Zarejestruj callback ostrzeżenia, aby przechwycić alerty o podstawianiu czcionek

Teraz gwiazda programu: **register warning callback**. Aspose.Words pozwala podłączyć implementację interfejsu `IWarningCallback`. Za każdym razem, gdy silnik napotka sytuację wartą oznaczenia — np. brakującą czcionkę — wywołuje twoją metodę `warning`.

```java
        // Register the warning callback
        doc.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) {
                // We’re only interested in font substitution warnings
                if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                    System.out.println("⚠️ Font substituted: " + info.getDescription());
                }
            }
        });
```

### Dlaczego to ważne

* **Widoczność:** Bez callbacku podstawienie odbywa się cicho i możesz dostarczyć dokument z niewłaściwym wyglądem.  
* **Automatyzacja:** W potokach wsadowych możesz logować każde zdarzenie brakującej czcionki i później przekazać listę do skryptu instalującego czcionki.  
* **Zgodność:** Niektóre branże (np. prawnicza) wymagają dowodu, że użyto oryginalnych czcionek lub że zostały one prawidłowo podstawione.

Zauważ, że filtrujemy na `WarningType.FONT_SUBSTITUTION`. Aspose.Words generuje wiele typów ostrzeżeń — przepełnienie układu, przestarzałe funkcje itp. — ale nas interesują tylko te, które informują o brakującej czcionce. Dzięki temu konsola pozostaje czysta, a my skupiamy się na celu **detect missing fonts**.

## Krok 4: Zapisz dokument i pozwól wywołać callback

Gdy w końcu wywołasz `save`, silnik kończy wszelkie leniwe ładowanie i uruchamia callback ostrzeżenia dla każdej brakującej czcionki, którą wykrył podczas operacji zapisu.

```java
        // Save the document – this is where the warning callback gets invoked
        String outputPath = "YOUR_DIRECTORY/output.docx";
        doc.save(outputPath);

        System.out.println("✅ Document saved to " + outputPath);
    }
}
```

### Oczekiwany output w konsoli

Zakładając, że `input.docx` odwołuje się do czcionki *„Comic Sans MS”*, której nie ma zainstalowanej, zobaczysz coś w stylu:

```
⚠️ Font substituted: Font 'Comic Sans MS' is not available. Substituted with 'Arial'.
✅ Document saved to YOUR_DIRECTORY/output.docx
```

Jeśli dokument źródłowy zawiera już wyłącznie zainstalowane czcionki, linia ostrzeżenia po prostu się nie pojawi — co oznacza, że **detect missing fonts** zakończyło się cicho sukcesem.

![Console output showing register warning callback in action and detect missing fonts](register-warning-callback-output.png)

*Tekst alternatywny obrazu: register warning callback output showing detect missing fonts*

## Krok 5: Obsługa przypadków brzegowych i wskazówki najlepszych praktyk

### Wiele brakujących czcionek

Jeśli dokument odwołuje się do kilku niedostępnych czcionek, callback wywoła się raz dla każdej z nich. Możesz zagregować komunikaty w listę, jeśli potrzebujesz później podsumowania.

```java
List<String> missingFonts = new ArrayList<>();
doc.setWarningCallback(info -> {
    if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
        missingFonts.add(info.getDescription());
    }
});
// After saving
if (!missingFonts.isEmpty()) {
    System.out.println("Missing fonts detected:");
    missingFonts.forEach(System.out::println);
}
```

### Kontrolowanie zachowania podstawiania

Czasami *naprawdę* chcesz wymusić konkretną czcionkę zapasową. Użyj `FontSettings` przed załadowaniem dokumentu:

```java
FontSettings settings = new FontSettings();
settings.setSubstitutionSettings(new FontSubstitutionSettings()
        .addSubstitutes("Comic Sans MS", "Times New Roman"));
doc.setFontSettings(settings);
```

Callback nadal będzie się wywoływał, ale będziesz dokładnie wiedział, której czcionki użyto.

### Rozważania dotyczące wydajności

Rejestrowanie callbacku ostrzeżenia wprowadza niewielki narzut — tylko kilka nanosekund na ostrzeżenie. W usługach o wysokiej przepustowości (np. konwertowanie tysięcy dokumentów na godzinę) wpływ jest znikomy. Jednak przy przetwarzaniu milionów warto rozważyć wyłączenie ostrzeżeń po zweryfikowaniu, że zestaw czcionek jest kompletny:

```java
doc.setWarningCallback(null); // turn off after initial scan
```

### Uwagi dotyczące różnych platform

Callback działa identycznie na Windows, macOS i Linux. Jedyna różnica to zestaw czcionek dostępnych w danym systemie operacyjnym. Jeśli uruchamiasz to samo zadanie na wielu agentach, możesz zobaczyć różne komunikaty o podstawianiu. Aby wyniki były deterministyczne, dostarcz **własny folder czcionek** i wskaż go Aspose.Words za pomocą `FontSettings.setFontsFolder("path/to/fonts", true);`.

## Pełny, gotowy do uruchomienia przykład

Poniżej znajduje się cała klasa Java, którą możesz skopiować‑wkleić do `src/main/java/FontWarningDemo.java`. Zawiera wszystkie importy, obsługę błędów i komentarze potrzebne do natychmiastowego uruchomienia.

```java
import com.aspose.words.*;
import java.util.ArrayList;
import java.util.List;

/**
 * Demonstrates how to register a warning callback in Aspose.Words for Java
 * to detect missing fonts during document processing.
 */
public class FontWarningDemo {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Paths – adjust to your environment
        String inputPath = "YOUR_DIRECTORY/input.docx";
        String outputPath = "YOUR_DIRECTORY/output.docx";

        // 2️⃣ Load the document (parsing begins here)
        Document doc = new Document(inputPath);

        // 3️⃣ Optional: set a custom font folder if you ship fonts with your app
        // FontSettings fs = new FontSettings();
        // fs.setFontsFolder("fonts", true);
        // doc.setFontSettings(fs);

        // 4️⃣ Register the warning callback to catch missing‑font warnings
        List<String> missingFonts = new ArrayList<>();
        doc.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) {
                if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                    // Log to console
                    System.out.println("⚠️ Font substituted: " + info.getDescription());
                    // Collect for later reporting
                    missingFonts.add(info.getDescription());
                }
            }
        });

        // 5️⃣ Save the document – triggers the callback
        doc.save(outputPath);
        System.out.println("✅ Document saved to " + outputPath);

        // 6️⃣ Post‑save reporting (if any fonts were missing)
        if (!missingFonts.isEmpty()) {
            System.out.println("\nSummary of missing fonts:");
            missingFonts.forEach(System.out::println);
        } else {
            System.out.println("\nNo missing fonts detected.");
        }
    }
}
```

Skompiluj i uruchom:

```bash
javac -cp "aspose-words-24.10.jar" FontWarningDemo.java
java -cp ".:aspose-words-24.10.jar" FontWarningDemo
```

Powinieneś zobaczyć linie ostrzeżeń (jeśli wystąpią), a następnie komunikat o sukcesie.

## Zakończenie

Właśnie nauczyłeś się **jak zarejestrować callback ostrzeżenia** w Javie, aby **wykrywać brakujące czcionki** przy pracy z Aspose.Words. Podłączając się do systemu ostrzeżeń biblioteki, uzyskujesz pełną widoczność zdarzeń podstawiania czcionek, możesz je logować dla zgodności, a nawet programowo zamieniać czcionki w razie potrzeby.  

Od tego momentu możesz rozważyć:

* **Detect missing fonts** w partii plików przy użyciu pętli lub strumieni równoległych.  
* Integrację callbacku z frameworkiem logowania (SLF4J, Log4j) w celu uzyskania raportów klasy produkcyjnej.  
* Użycie `FontSettings` do wymuszenia firmowego zestawu czcionek i uniknięcia niechcianych podstawień.

Spróbuj — zamień dokument wejściowy, wypróbuj różne scenariusze brakujących czcionek i zobacz, jak zachowuje się callback. Jeśli napotkasz problemy, zostaw komentarz poniżej; happy coding!

## Co warto nauczyć się dalej?

Poniższe samouczki obejmują tematy ściśle powiązane, które rozwijają techniki przedstawione w tym przewodniku. Każdy zasób zawiera kompletne działające przykłady kodu z wyjaśnieniami krok po kroku, aby pomóc Ci opanować dodatkowe funkcje API i odkrywać alternatywne podejścia implementacyjne w własnych projektach.

- [Przechwytywanie ostrzeżeń o podstawianiu czcionek w Javie z Aspose.Words – Kompletny przewodnik](/words/english/java/document-loading-and-saving/capture-font-substitution-warnings-in-java-with-aspose-words/)
- [Callback ostrzeżenia w dokumencie Word](/words/english/net/programming-with-loadoptions/warning-callback/)
- [Aspose Words Java Callback Niestandardowe oszczędności](/words/hindi/java/images-shapes/aspose-words-java-callback-custom-savings/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}