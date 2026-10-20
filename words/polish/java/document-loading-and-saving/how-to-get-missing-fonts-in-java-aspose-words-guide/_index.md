---
category: general
date: 2026-02-15
description: Dowiedz się, jak uzyskać brakujące czcionki podczas ładowania dokumentu
  Word w Javie przy użyciu Aspose.Words. Zawiera wywołania zwrotne ostrzeżeń oraz
  obsługę podstawiania czcionek.
draft: false
keywords:
- how to get missing fonts
- Aspose.Words missing font
- font substitution warning
- Java LoadOptions warning callback
- document processing Java
language: pl
og_description: Jak uzyskać brakujące czcionki w Javie z Aspose.Words. Odkryj wywołania
  zwrotne ostrzeżeń, obsługę podstawiania czcionek oraz najlepsze praktyki przetwarzania
  dokumentów.
og_title: Jak uzyskać brakujące czcionki w Javie – przewodnik Aspose.Words
tags:
- Aspose.Words
- Java
- Font Management
title: Jak uzyskać brakujące czcionki w Javie – przewodnik Aspose.Words
url: /pl/java/document-loading-and-saving/how-to-get-missing-fonts-in-java-aspose-words-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak uzyskać brakujące czcionki w Javie – przewodnik Aspose.Words

Czy kiedykolwiek otworzyłeś dokument Word w Javie i zobaczyłeś dziwne zamiany czcionek, zastanawiając się **jak uzyskać brakujące czcionki**? Nie jesteś pierwszy, który spotkał takie zaskoczenie. W wielu aplikacjach korporacyjnych ostrzeżenia o brakujących czcionkach mogą zepsuć wizualną wierność raportów, umów czy materiałów marketingowych.

Dobre wieści? Aspose.Words zapewnia prosty sposób na przechwycenie tych ostrzeżeń za pomocą callbacku, dzięki czemu możesz logować, zamieniać lub nawet powiadamiać użytkowników przed renderowaniem dokumentu. W tym samouczku przeprowadzimy Cię przez kompletny, uruchamialny przykład, który pokazuje **jak uzyskać brakujące czcionki**, wyjaśnia, dlaczego callback ma znaczenie, oraz omawia kilka trików w sytuacjach brzegowych, które mogą być potrzebne w rzeczywistych projektach.

> **Wskazówka:** Jeśli już używasz Aspose.Words 22.12 lub nowszej, API pokazane poniżej działa od razu, bez dodatkowej konfiguracji.

---

![Diagram ilustrujący, jak uzyskać brakujące czcionki przy użyciu callbacku ostrzeżeń Aspose.Words](how-to-get-missing-fonts-diagram.png "diagram jak uzyskać brakujące czcionki")

## Co obejmuje ten samouczek

- Ustawienie **callbacku ostrzeżeń Java LoadOptions** w celu przechwycenia ostrzeżeń o zamianie czcionek.  
- Filtrowanie ostrzeżeń, aby wyświetlały się tylko te związane z brakującymi czcionkami.  
- Wydrukowanie czytelnego raportu, który pokazuje, które czcionki zostały zamienione i na co.  
- Wskazówki dotyczące obsługi dużych dokumentów, dostosowywania poziomu ostrzeżeń oraz integracji rozwiązania z większym potokiem przetwarzania.

Pod koniec tego przewodnika będziesz w stanie odpowiedzieć na pytanie „**jak uzyskać brakujące czcionki**?” przy użyciu gotowego fragmentu kodu oraz solidnego zrozumienia leżących u podstaw mechanizmów.

### Wymagania wstępne

- Zainstalowany Java 8 lub nowszy.  
- Biblioteka Aspose.Words for Java (pobierz ze strony oficjalnej lub dodaj przez Maven/Gradle).  
- Dokument Word, który odwołuje się do czcionki niezainstalowanej na Twoim komputerze (np. `MissingFont.docx`).  

Jeśli brakuje Ci któregoś z powyższych, pobierz bibliotekę już teraz — dodanie jej do Maven jest tak proste jak:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version> <!-- replace with the latest version -->
</dependency>
```

---

## Krok 1: Przygotuj kolekcję dla ostrzeżeń o zamianie czcionek

Przed załadowaniem dokumentu potrzebujemy miejsca do przechowywania wszelkich ostrzeżeń generowanych przez Aspose.Words. `ArrayList<WarningInfo>` sprawdza się doskonale, ponieważ zachowuje kolejność i pozwala na późniejsze iterowanie.

```java
import com.aspose.words.*;
import java.util.ArrayList;
import java.util.List;

// Step 1: Create a list that will hold warning information.
List<WarningInfo> fontWarnings = new ArrayList<>();
```

*Dlaczego to ważne:* Callback ostrzeżeń może wywołać się dziesiątki razy dla jednego pliku — pomyśl o każdym brakującym glifie, każdym problemie z osadzonym obrazem itp. Gromadząc je najpierw, utrzymujesz fazę ładowania szybką i odkładasz przetwarzanie na kontrolowaną pętlę.

---

## Krok 2: Skonfiguruj LoadOptions z callbackiem ostrzeżeń

Aspose.Words pozwala podłączyć `IWarningCallback`. Wewnątrz callbacku dodamy każde `WarningInfo` do naszej listy z Kroku 1.

```java
// Step 2: Set up LoadOptions with a custom warning callback.
LoadOptions loadOptions = new LoadOptions();
loadOptions.setWarningCallback(new IWarningCallback() {
    @Override
    public void warning(WarningInfo info) {
        // Capture every warning; we'll filter later.
        fontWarnings.add(info);
    }
});
```

*Wyjaśnienie:* Metoda `warning` jest wywoływana **synchronicznie** podczas ładowania dokumentu. Po prostu dodając `WarningInfo` do `fontWarnings`, unikamy ciężkiego I/O (np. logowania do pliku), które mogłoby spowolnić ładowanie. Ten wzorzec — zbierz‑a‑następnie‑przetwórz — jest zalecany do obsługi dużych partii ostrzeżeń.

---

## Krok 3: Załaduj dokument przy użyciu skonfigurowanych opcji

Teraz faktycznie odczytujemy plik Word. Jeśli dokument zawiera czcionki, które nie są zainstalowane, Aspose.Words automatycznie je zamieni i wywoła callback ostrzeżeń, który właśnie podłączyliśmy.

```java
// Step 3: Load the document with the warning‑aware LoadOptions.
String filePath = "YOUR_DIRECTORY/MissingFont.docx"; // adjust to your environment
Document doc = new Document(filePath, loadOptions);
```

*Co się dzieje w tle?* Aspose.Words analizuje tabelę czcionek w pliku, porównuje ją z czcionkami dostępnymi w systemie operacyjnym i dla każdego brakującego wpisu tworzy `WarningInfo` z `WarningSource.FontSubstitution`. To źródło będzie kluczem, którego użyjemy do wyodrębnienia ostrzeżeń o brakujących czcionkach.

---

## Krok 4: Filtruj i wyświetl tylko ostrzeżenia o zamianie czcionek

Po załadowaniu `fontWarnings` może zawierać mieszankę wiadomości (np. przestarzałe funkcje, problemy z obrazami). Interesują nas tylko brakujące czcionki, więc przechodzimy przez listę i drukujemy zwięzły raport.

```java
// Step 4: Output any font‑substitution warnings that were captured.
for (WarningInfo warning : fontWarnings) {
    if (warning.getSource() == WarningSource.FontSubstitution) {
        System.out.println("Substituted '" + warning.getDescription() + "' with '" +
                           warning.getAdditionalInfo() + "'");
    }
}
```

**Przykładowe wyjście**

```
Substituted 'Comic Sans MS' with 'Arial'
Substituted 'Times New Roman PS' with 'Times New Roman'
```

*Dlaczego to jest przydatne:* Pole `description` informuje, której czcionki dokument żądał, natomiast `additionalInfo` mówi, jaką czcionkę faktycznie użył Aspose.Words. Mając te dane, możesz:

- Poprosić użytkownika o zainstalowanie brakującej czcionki.  
- Programowo osadzić zamienną czcionkę w dokumencie (`doc.getFontInfos().add(...)`).  
- Zalogować zdarzenie dla audytów zgodności.

---

## Obsługa przypadków brzegowych i typowych wariacji

### 1. Tłumienie ostrzeżeń nie‑dotyczących czcionek

Jeśli chcesz tylko wiadomości związane z czcionkami, możesz ściślej dopasować callback:

```java
loadOptions.setWarningCallback(info -> {
    if (info.getSource() == WarningSource.FontSubstitution) {
        fontWarnings.add(info);
    }
});
```

To zmniejsza zużycie pamięci przy przetwarzaniu ogromnych partii.

### 2. Dostosowywanie poziomu istotności ostrzeżeń

Aspose.Words klasyfikuje ostrzeżenia według `WarningType`. Dla brakujących czcionek zazwyczaj zobaczysz `WarningType.FontSubstitution`. Jeśli potrzebujesz traktować je jako błędy (np. przerwać ładowanie), rzuć wyjątek wewnątrz callbacku:

```java
loadOptions.setWarningCallback(info -> {
    if (info.getSource() == WarningSource.FontSubstitution) {
        throw new RuntimeException("Missing font detected: " + info.getDescription());
    }
});
```

### 3. Praca ze strumieniami zamiast plików

Czasami dokumenty pochodzą z bazy danych lub żądania HTTP. To samo podejście działa ze `InputStream`:

```java
InputStream docStream = new ByteArrayInputStream(bytesFromDb);
Document doc = new Document(docStream, loadOptions);
```

Pamiętaj tylko, aby zamknąć strumień po załadowaniu.

### 4. Używanie własnego folderu czcionek

Jeśli masz zbiór firmowych czcionek przechowywanych na udostępnionym dysku, wskaż Aspose.Words ten folder:

```java
loadOptions.setFontSettings(new FontSettings());
loadOptions.getFontSettings().setFontsFolder("C:/CorporateFonts", true);
```

Teraz biblioteka będzie najpierw szukać w tym miejscu *zanim* przejdzie do czcionek systemowych, co znacząco zmniejszy liczbę ostrzeżeń o brakujących czcionkach.

---

## Pełny działający przykład

Łącząc wszystko razem, oto samodzielna klasa, którą możesz wkleić do dowolnego projektu Java:

```java
import com.aspose.words.*;
import java.util.ArrayList;
import java.util.List;

public class MissingFontDetector {

    public static void main(String[] args) {
        // 1️⃣ Prepare a collection for warnings.
        List<WarningInfo> fontWarnings = new ArrayList<>();

        // 2️⃣ Create LoadOptions with a warning callback.
        LoadOptions loadOptions = new LoadOptions();
        loadOptions.setWarningCallback(info -> fontWarnings.add(info));

        // (Optional) Point to a custom font folder.
        // FontSettings fontSettings = new FontSettings();
        // fontSettings.setFontsFolder("C:/CorporateFonts", true);
        // loadOptions.setFontSettings(fontSettings);

        // 3️⃣ Load the document.
        String docPath = "YOUR_DIRECTORY/MissingFont.docx";
        Document doc;
        try {
            doc = new Document(docPath, loadOptions);
        } catch (Exception e) {
            System.err.println("Failed to load document: " + e.getMessage());
            return;
        }

        // 4️⃣ Print missing‑font warnings.
        System.out.println("=== Missing Font Report ===");
        for (WarningInfo warning : fontWarnings) {
            if (warning.getSource() == WarningSource.FontSubstitution) {
                System.out.println("Substituted '" + warning.getDescription() + "' with '" +
                                   warning.getAdditionalInfo() + "'");
            }
        }
        System.out.println("=== End of Report ===");
    }
}
```

Uruchom ten program, a zobaczysz schludną listę każdej czcionki, którą Aspose.Words musiał zastąpić. Bez dodatkowych bibliotek, bez ukrytej magii — tylko czysta Java i moc API **Aspose.Words missing font**.

---

## Zakończenie

Odpowiedzieliśmy na podstawowe pytanie **jak uzyskać brakujące czcionki** w środowisku Java przy użyciu Aspose.Words. Poprzez podłączenie callbacku ostrzeżeń `LoadOptions`, zbieranie obiektów `WarningInfo` i filtrowanie źródeł `FontSubstitution`, uzyskasz pełną widoczność problemów związanych z czcionkami przed jakimkolwiek renderowaniem. Podejście skaluje się od narzędzi jednoplikowych po masowe przetwarzanie partii i jest na tyle elastyczne, aby obsłużyć własne foldery czcionek, obsługę poziomu istotności czy wejścia oparte na strumieniach.

Kolejne kroki? Spróbuj osadzić zamienione czcionki bezpośrednio w dokumencie (`doc.getFontInfos().add(...)`), aby ostateczny plik był naprawdę samodzielny, lub zintegrować raport ostrzeżeń z panelem monitorującym. Możesz także zgłębić powiązane tematy, takie jak **document processing Java**, **Aspose.Words font substitution warning** i **Java LoadOptions warning callback**, aby pogłębić swoją wiedzę.

Miłego kodowania i niech Twoje dokumenty zawsze renderują się z oczekiwanymi czcionkami!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}