---
category: general
date: 2026-04-04
description: Złap ostrzeżenia o podstawianiu czcionek podczas ładowania dokumentów
  Word przy użyciu Aspose.Words for Java i automatycznie wykrywaj brakujące czcionki.
  Postępuj zgodnie z tym przewodnikiem krok po kroku.
draft: false
keywords:
- capture font substitution warnings
- detect missing fonts
language: pl
og_description: Rejestruj ostrzeżenia o podstawianiu czcionek podczas ładowania dokumentów
  Word za pomocą Aspose.Words for Java i wykrywaj brakujące czcionki w kilku prostych
  krokach.
og_title: Zbieraj ostrzeżenia o zamianie czcionek – wykrywaj brakujące czcionki
tags:
- Aspose.Words
- Java
- Document Processing
title: Zbieraj ostrzeżenia o zamianie czcionek – wykrywaj brakujące czcionki
url: /pl/java/document-loading-and-saving/capture-font-substitution-warnings-detect-missing-fonts/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Rejestrowanie ostrzeżeń o podstawianiu czcionek – Wykrywanie brakujących czcionek

Czy kiedykolwiek potrzebowałeś **rejestrować ostrzeżenia o podstawianiu czcionek** przy otwieraniu pliku Word, tylko po to, by odkryć, że kluczowa czcionka jest brakująca? Nie jesteś sam. W wielu procesach korporacyjnych brakująca czcionka może zamienić perfekcyjnie sformatowany raport w zniekształcony bałagan, a jedyną wskazówką jest ciche ostrzeżenie, którego większość programistów nigdy nie widzi.

Dobrą wiadomością jest to, że Aspose.Words for Java pozwala wstrzyknąć się w proces ładowania i **wykrywać brakujące czcionki** zanim sprawią problemy. W tym samouczku przeprowadzimy Cię przez kompletny, gotowy do uruchomienia przykład, który wypisuje każde ostrzeżenie o podstawianiu bezpośrednio w konsoli, dzięki czemu możesz zdecydować, czy osadzić właściwą czcionkę, zastąpić ją, czy powiadomić użytkownika.

Krótko mówiąc, po zakończeniu tego przewodnika będziesz wiedział, jak:

* Skonfigurować obiekt `LoadOptions` z własnym callbackiem ostrzeżeń.
* Przefiltrować callback tak, aby reagował tylko na zdarzenia podstawiania czcionek.
* Załadować dowolny plik `.docx` i natychmiast zobaczyć ostrzeżenia.
* Rozszerzyć rozwiązanie o logowanie ostrzeżeń, rzucanie wyjątków lub nawet automatyczną instalację brakujących czcionek.

Nie potrzebna jest żadna zewnętrzna dokumentacja — wystarczy kilka linii Java i plik JAR Aspose.Words.

## Wymagania wstępne

Before we dive in, make sure you have:

* Zainstalowaną Javę 8 lub nowszą (najlepiej najnowszą wersję LTS).
* Aspose.Words for Java 23.11 lub nowszą – możesz pobrać artefakt Maven lub zwykły JAR ze strony Aspose.
* Dokument Word, który odwołuje się do czcionki nieobecnej na Twoim komputerze deweloperskim (np. „MyFancyFont”).  
* IDE lub edytor tekstu według własnego wyboru – używam IntelliJ IDEA, ale Eclipse lub VS Code również się sprawdzą.

Jeśli którykolwiek z powyższych elementów jest Ci nieznany, zatrzymaj się i najpierw je zainstaluj; reszta samouczka zakłada, że są gotowe.

---

## Rejestrowanie ostrzeżeń o podstawianiu czcionek przy użyciu Aspose.Words

Główna część rozwiązania znajduje się w instancji `LoadOptions`. Przypisując `IWarningCallback`, możemy przechwycić każde ostrzeżenie generowane przez bibliotekę podczas fazy ładowania.

```java
import com.aspose.words.*;

public class FontDiagnosticsTutorial {
    public static void main(String[] args) throws Exception {

        // Step 1️⃣: Create LoadOptions and set a warning callback.
        LoadOptions loadOptions = new LoadOptions();
        loadOptions.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) {
                // Capture only font substitution warnings.
                if (info.getWarningType() == WarningType.SUBSTITUTED_FONT) {
                    System.out.println("Font substitution: " + info.getDescription());
                }
            }
        });

        // Step 2️⃣: Load the document. The callback runs automatically.
        Document doc = new Document("YOUR_DIRECTORY/document-with-missing-font.docx", loadOptions);

        // Step 3️⃣: If you reach this line, the document is loaded.
        // Any missing‑font warnings have already been printed to the console.
        System.out.println("Document loaded successfully.");
    }
}
```

**Dlaczego to działa:**  
`LoadOptions` informuje Aspose.Words, jak traktować wczytywany plik. Interfejs `IWarningCallback` jest hakiem, który otrzymuje obiekt `WarningInfo` dla *każdego* ostrzeżenia. Sprawdzając `info.getWarningType()`, filtrujemy wszystko oprócz `SUBSTITUTED_FONT`. Właściwość `description` zawiera czytelną dla człowieka wiadomość, np. “Font 'MyFancyFont' was substituted with 'Arial'”.

### Oczekiwany wynik w konsoli

Jeśli dokument źródłowy odwołuje się do czcionki, która nie jest zainstalowana, zobaczysz coś podobnego do:

```
Font substitution: Font 'MyFancyFont' was substituted with 'Arial'.
Document loaded successfully.
```

Jeśli dokument używa wyłącznie czcionek dostępnych na maszynie, callback pozostaje cichy i otrzymasz jedynie końcowy wiersz “Document loaded successfully.” line.

## Wykrywanie brakujących czcionek w dokumencie

Możesz się zastanawiać, *„Czy ostrzeżenie o podstawianiu jest tym samym co brakująca czcionka?”* W większości przypadków tak — Aspose.Words zastępuje brakującą czcionkę zapasową i zgłasza to poprzez `SUBSTITUTED_FONT`. Jednak istnieją sytuacje brzegowe, w których czcionka jest obecna, ale dokładny styl (pogrubienie‑pochylenie, konkretne funkcje OpenType) nie jest dostępny, co prowadzi do subtelnego podstawienia.

Aby mieć całkowitą pewność, że wykryto wszystkie luki, możesz połączyć callback ostrzeżeń z inspekcją po załadowaniu:

```java
// After loading the document, iterate through all runs.
for (Paragraph para : (Iterable<Paragraph>) doc.getFirstSection().getBody().getChildNodes(NodeType.PARAGRAPH, true)) {
    for (Run run : (Iterable<Run>) para.getChildNodes(NodeType.RUN, true)) {
        Font font = run.getFont();
        if (font.getName().equalsIgnoreCase("MyFancyFont")) {
            System.out.println("Run still uses the missing font: " + font.getName());
        }
    }
}
```

**Wskazówka:** Jeśli znajdziesz fragmenty (runs) nadal odwołujące się do brakującej czcionki, możesz je zamienić w locie:

```java
font.setName("Arial"); // fallback
```

W ten sposób zapewniasz spójny wizualny rezultat, nawet jeśli pierwotne ostrzeżenie zostało zignorowane.

## Częste pułapki i jak ich unikać

| Pułapka | Dlaczego się pojawia | Rozwiązanie |
|---------|----------------------|-------------|
| **Zapomnienie o ustawieniu callbacka** | `LoadOptions` domyślnie ma callback typu no‑op, więc ostrzeżenia znikają. | Zawsze wywołaj `loadOptions.setWarningCallback(...)` przed ładowaniem. |
| **Użycie niewłaściwego typu ostrzeżenia** | `WarningType.SUBSTITUTED_FONT` jest jedynym enumem sygnalizującym brakujące czcionki. | Filtruj dokładnie na `WarningType.SUBSTITUTED_FONT`; inne typy (np. `UNKNOWN_FILE_FORMAT`) nie są powiązane. |
| **Hard‑kodowanie ścieżek plików** | Działa lokalnie, ale psuje się w pipeline’ach CI/CD. | Użyj ścieżki względnej lub przekaż lokalizację pliku jako argument wiersza poleceń. |
| **Ignorowanie czcionek Unicode** | Niektóre brakujące czcionki są problemem tylko dla określonych znaków. | Testuj dokument zawierający pełny zestaw znaków, który zamierzasz obsługiwać. |
| **Uruchamianie na serwerze bez interfejsu graficznego bez konfiguracji czcionek** | Serwer może nie mieć żadnych czcionek zapasowych, co powoduje nieoczekiwane podstawienia. | Zainstaluj minimalny zestaw popularnych czcionek (Arial, Times New Roman) na serwerze. |

## Rozszerzanie rozwiązania

Teraz, gdy możesz **rejestrować ostrzeżenia o podstawianiu czcionek**, możesz chcieć:

* **Logować ostrzeżenia do pliku** – zamień `System.out.println` na logger, np. SLF4J.
* **Rzucić wyjątek** – przydatne w zautomatyzowanych pipeline’ach, gdzie brakująca czcionka powinna spowodować niepowodzenie budowania:

```java
if (info.getWarningType() == WarningType.SUBSTITUTED_FONT) {
    throw new RuntimeException("Missing font detected: " + info.getDescription());
}
```

* **Automatyczna instalacja brakujących czcionek** – pobierz wymagany plik TTF/OTF w czasie działania i dodaj go do `GraphicsEnvironment` Javy. To bardziej zaawansowany scenariusz, ale w pełni możliwy.

## Diagram (opcjonalnie)

![Diagram przepływu rejestrowania ostrzeżeń o podstawianiu czcionek pokazujący LoadOptions → WarningCallback → wyjście w konsoli](capture-font-substitution-warnings-diagram.png)

*Alt text:* “Diagram przepływu rejestrowania ostrzeżeń o podstawianiu czcionek ilustrujący, jak Aspose.Words kieruje ostrzeżenia o brakujących czcionkach do niestandardowego callbacka.”

## Podsumowanie

Właśnie omówiliśmy, jak **rejestrować ostrzeżenia o podstawianiu czcionek** i **wykrywać brakujące czcionki** podczas ładowania dokumentów Word przy użyciu Aspose.Words for Java. Konfigurując obiekt `LoadOptions` i implementując mały `IWarningCallback`, uzyskujesz pełną widoczność procesu podstawiania czcionek, co umożliwia logowanie, zamianę lub przerwanie w przypadku brakujących krojów.

Krótko mówiąc: ustaw callback, filtruj na `SUBSTITUTED_FONT`, załaduj dokument i obsłuż wynik w dowolny sposób, jaki potrzebuje Twoja aplikacja. Stąd możesz rozbudować rozwiązanie o frameworki logowania, kontrole CI lub nawet automatyczną dostawę czcionek.

Chcesz iść dalej? Spróbuj:

* **Osadzanie czcionek** bezpośrednio w zapisywanym dokumencie (`doc.save(..., SaveOptions.createSaveOptions(SaveFormat.DOCX))` z `FontEmbeddingMode.EMBED_ALL`).
* **Generowanie PDF** po naprawie czcionek, zapewniając, że końcowy wynik wygląda dokładnie tak, jak zamierzono.
* **Skanowanie całego folderu** dokumentów w poszukiwaniu brakujących czcionek i tworzenie podsumowującego raportu.

To wszystko na teraz — miłego kodowania i niech Twoje dokumenty zawsze renderują się z odpowiednią czcionką!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}