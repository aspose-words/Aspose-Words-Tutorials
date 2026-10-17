---
category: general
date: 2026-03-17
description: Poznaj samouczek aspose warning callback, aby wykrywać brakujące czcionki
  i śledzić brakujące czcionki w dokumentach Java, z kompletnym, gotowym do uruchomienia
  przykładem.
draft: false
keywords:
- aspose warning callback tutorial
- detect missing fonts
- track missing fonts
language: pl
og_description: Opanuj samouczek dotyczący wywołań zwrotnych ostrzeżeń Aspose, aby
  wykrywać brakujące czcionki i śledzić je w swoim procesie przetwarzania dokumentów
  Word w Javie.
og_title: Samouczek wywołania zwrotnego ostrzeżeń Aspose – wykrywanie brakujących
  czcionek
tags:
- Aspose.Words
- Java
- Font Substitution
- Document Processing
title: Samouczek wywołania zwrotnego ostrzeżeń Aspose – wykrywanie i śledzenie brakujących
  czcionek
url: /pl/java/document-rendering/aspose-warning-callback-tutorial-detect-and-track-missing-fo/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# aspose warning callback tutorial – Wykrywanie i Śledzenie Brakujących Czcionek

Zastanawiałeś się kiedyś, jak **wykrywać brakujące czcionki** podczas konwersji lub edycji plików Word przy użyciu Aspose.Words? Nie jesteś sam. W wielu rzeczywistych projektach nieobecna czcionka może powodować problemy z układem, a Ty potrzebujesz niezawodnego sposobu na **śledzenie brakujących czcionek**, zanim sprawią kłopoty.  

Dobra wiadomość? **aspose warning callback tutorial** dostarcza czysty, programowy hook, który wypisuje dokładnie te ostrzeżenia o zamianie czcionek w momencie ich wystąpienia. W tym przewodniku przejdziemy przez konfigurację callbacku, załadowanie dokumentu i obserwację ostrzeżeń w akcji — wszystko w Javie.

Po przeczytaniu tego artykułu będziesz mógł automatycznie wykrywać brakujące czcionki, rejestrować je i decydować, czy wstawić zamiennik, czy dostosować pliki źródłowe. Nie potrzebujesz zewnętrznych narzędzi.

## Wymagania wstępne

- **Java 8+** (kod kompiluje się na dowolnym aktualnym JDK)
- **Aspose.Words for Java** w wersji 23.10 lub nowszej – pobierz z portalu Aspose lub dodaj zależność Maven.
- Przykładowy plik DOCX, który celowo odwołuje się do czcionki, której nie masz zainstalowanej (np. „Comic Sans MS” na systemie Linux).

To wszystko — bez dodatkowych bibliotek, bez skomplikowanych kroków budowania.

## Krok 1: Zarejestruj Warning Callback – Rdzeń aspose warning callback tutorial

Pierwsza rzecz, której uczy tutorial, to podłączenie listenera ostrzeżeń. Aspose.Words generuje obiekt `WarningInfo` dla każdego napotkanego problemu, a flaga `WarningSource.FONT_SUBSTITUTION` informuje nas dokładnie, kiedy czcionka jest zamieniana.

```java
import com.aspose.words.*;

public class FontDiagnostics {
    public static void main(String[] args) throws Exception {

        // Step 1: Register a warning callback to capture font substitution warnings.
        Document.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) {
                // We only care about font‑substitution events.
                if (info.getSource() == WarningSource.FONT_SUBSTITUTION) {
                    System.out.println("Font substitution warning:");
                    System.out.println("  Original:   " + info.getDescription());
                    System.out.println("  Substituted:" + info.getAdditionalInfo());
                }
            }
        });
```

**Dlaczego to ważne:** Bez callbacku Aspose cicho zamienia brakujące czcionki i nigdy nie dowiesz się, które glify mogą wyglądać niepoprawnie. Logując ostrzeżenie, możesz **wykrywać brakujące czcionki** wcześnie i zdecydować, czy wstawić właściwą czcionkę.

> **Wskazówka:** Jeśli potrzebujesz zebrać ostrzeżenia do późniejszego raportowania, przechowuj je w `List<WarningInfo>` zamiast od razu wypisywać.

## Krok 2: Załaduj dokument – Gdzie mogą ukrywać się brakujące czcionki

Teraz ładujemy DOCX, który może odwoływać się do czcionek nieobecnych w systemie. Sam proces ładowania wywołuje callback ostrzeżeń, jeśli jakiekolwiek czcionki są brakujące.

```java
        // Step 2: Load a document that may contain missing fonts.
        Document document = new Document("YOUR_DIRECTORY/input.docx");
```

**Co się dzieje w tle?** Aspose analizuje definicje stylów dokumentu, skanuje każdy fragment tekstu i sprawdza repozytorium czcionek systemu. Gdy nie znajdzie dokładnego dopasowania, przechodzi na zamiennik i wyzwala ostrzeżenie, które właśnie podłączyliśmy.

## Krok 3: Zapisz dokument – Wypuszczenie ostrzeżeń

Na koniec zapisujemy dokument. Operacja zapisu ponownie ocenia czcionki, więc wszelkie ostrzeżenia, które nie zostały wyemitowane podczas ładowania, pojawią się teraz.

```java
        // Step 3: Save the document; any font substitution warnings will be printed by the callback.
        document.save("YOUR_DIRECTORY/output.docx");
    }
}
```

Po uruchomieniu programu zobaczysz w konsoli coś podobnego do:

```
Font substitution warning:
  Original:   Font "Comic Sans MS" not found.
  Substituted: Using "Arial" as fallback.
```

Ten wynik dowodzi, że **aspose warning callback tutorial** działa, a Ty skutecznie **wykryłeś brakujące czcionki** i **śledzisz brakujące czcionki** w logu.

## Jak wykrywać brakujące czcionki w dokumencie Word – Poza podstawami

Podejście z callbackiem świetnie sprawdza się przy jednorazowych uruchomieniach, ale czasem potrzebne jest narzędzie wielokrotnego użytku. Oto szybki wrapper, który możesz włożyć do dowolnego projektu:

```java
public class FontMissingChecker {
    private final List<String> missingFonts = new ArrayList<>();

    public FontMissingChecker() {
        Document.setWarningCallback((WarningInfo info) -> {
            if (info.getSource() == WarningSource.FONT_SUBSTITUTION) {
                missingFonts.add(info.getDescription());
            }
        });
    }

    public List<String> check(String path) throws Exception {
        new Document(path); // triggers warnings
        return missingFonts;
    }
}
```

Użyj go tak:

```java
FontMissingChecker checker = new FontMissingChecker();
List<String> fonts = checker.check("input.docx");
if (!fonts.isEmpty()) {
    System.out.println("Missing fonts detected:");
    fonts.forEach(System.out::println);
}
```

Teraz masz wielokrotnego użytku **detect missing fonts** metodę, która zwraca listę, którą możesz podać do potoku CI lub interfejsu UI.

## Śledzenie brakujących czcionek z Aspose.Words – Raportowanie dla zespołów

W większym zespole możesz chcieć wygenerować raport CSV ze wszystkimi brakującymi czcionkami w wielu dokumentach. Połącz poprzednie narzędzie z prostą iteracją plików:

```java
import java.nio.file.*;
import java.io.*;

public class BulkFontReporter {
    public static void main(String[] args) throws Exception {
        Path folder = Paths.get("YOUR_DIRECTORY");
        try (BufferedWriter writer = Files.newBufferedWriter(folder.resolve("missing-fonts-report.csv"))) {
            writer.write("Document,Missing Font\n");
            Files.list(folder)
                 .filter(p -> p.toString().endsWith(".docx"))
                 .forEach(p -> {
                     try {
                         FontMissingChecker checker = new FontMissingChecker();
                         List<String> missing = checker.check(p.toString());
                         for (String msg : missing) {
                             // Extract font name from description
                             String font = msg.replaceAll("Font \"(.*?)\".*", "$1");
                             writer.write(p.getFileName() + "," + font + "\n");
                         }
                     } catch (Exception e) {
                         // In a real app, log the error
                     }
                 });
        }
        System.out.println("Report generated at missing-fonts-report.csv");
    }
}
```

Uruchomienie tego skryptu da Ci **track missing fonts** CSV, które każdy deweloper może szybko przejrzeć przed zatwierdzeniem dokumentu do produkcji.

## Typowe pułapki i jak ich unikać

| Pułapka | Dlaczego się pojawia | Rozwiązanie |
|---------|----------------------|-------------|
| **Callback nie wywołuje się** | Zapomniałeś ustawić callback **przed** załadowaniem dokumentu. | Umieść `Document.setWarningCallback` na samym początku `main`. |
| **Pojawia się tylko pierwsze ostrzeżenie** | Aspose buforuje ostrzeżenia per instancja `Document`. | Używaj nowego obiektu `Document` dla każdego pliku lub resetuj callback między uruchomieniami. |
| **Nieprawidłowa nazwa czcionki w logu** | Opis zawiera dodatkowy tekst („Font … not found”). | Usuń go przy pomocy regex, jak pokazano w przykładzie CSV. |
| **Spadek wydajności przy dużych partiach** | Callback działa na każdym fragmencie tekstu, co może być kosztowne. | Ogranicz sprawdzanie do kroku wstępnego; pomiń zapisywanie, jeśli potrzebujesz tylko detekcji. |

## Oczekiwane wyniki i weryfikacja

1. **Wyjście konsoli** – Powinieneś zobaczyć przynajmniej jedną linię „Font substitution warning” dla każdej brakującej czcionki.  
2. **Raport CSV** – Po zakończeniu skryptu wsadowego otwórz `missing-fonts-report.csv` i sprawdź, czy każdy wiersz zawiera nazwę dokumentu oraz dokładną brakującą czcionkę.  
3. **Zapisany dokument** – Wyjściowy DOCX zostanie wyrenderowany przy użyciu czcionek zastępczych, ale układ wizualny może różnić się od oryginału.

Jeśli którykolwiek z tych kroków nie zachowuje się tak, jak opisano, sprawdź, czy plik JAR Aspose.Words znajduje się na classpath oraz czy `input.docx` naprawdę odwołuje się do czcionki nieobecnej w Twoim systemie operacyjnym.

## Podsumowanie

Właśnie ukończyłeś **aspose warning callback tutorial**, który pokazuje, jak **wykrywać brakujące czcionki** i **śledzić brakujące czcionki** w aplikacjach Java. Rejestrując listener ostrzeżeń, ładując dokument i opcjonalnie eksportując wyniki, zyskasz pełną widoczność problemów związanych z czcionkami, zanim pojawią się w produkcji.

Następne kroki, które możesz rozważyć:

- Osadzenie brakującej czcionki bezpośrednio przy użyciu `LoadOptions.setFontSubstitution`.
- Użycie klasy `FontSettings` do mapowania brakujących czcionek na konkretne zamienniki.
- Integracja raportu CSV z potokiem CI/CD, aby przerywać buildy przy wykryciu nieudokumentowanych czcionek.

Wypróbuj to, dostosuj callbacki do swojego frameworka logowania i zobacz, jak Twój przepływ pracy z dokumentami staje się znacznie bardziej odporny. Szczęśliwego kodowania!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}