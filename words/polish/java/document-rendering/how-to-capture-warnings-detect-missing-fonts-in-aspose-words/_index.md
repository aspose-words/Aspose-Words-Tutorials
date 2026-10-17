---
category: general
date: 2026-03-19
description: Dowiedz się, jak przechwytywać ostrzeżenia w Aspose.Words for Java i
  wykrywać brakujące czcionki. Ten przewodnik krok po kroku pokazuje również, jak
  elegancko obsługiwać brakujące czcionki.
draft: false
keywords:
- how to capture warnings
- detect missing fonts
- how to detect missing fonts
- handle missing fonts
language: pl
og_description: Jak przechwytywać ostrzeżenia w Aspose.Words for Java, wykrywać brakujące
  czcionki i obsługiwać brakujące czcionki przy użyciu pełnego przykładu kodu.
og_title: Jak przechwytywać ostrzeżenia – wykrywać brakujące czcionki w Aspose.Words
tags:
- Aspose.Words
- Java
- Font Substitution
- Document Processing
title: Jak przechwytywać ostrzeżenia – wykrywać brakujące czcionki w Aspose.Words
url: /pl/java/document-rendering/how-to-capture-warnings-detect-missing-fonts-in-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak przechwycić ostrzeżenia – wykrywać brakujące czcionki w Aspose.Words

Zastanawiałeś się kiedyś **jak przechwycić ostrzeżenia**, gdy dokument Word jest ładowany i niektóre czcionki nie są dostępne na komputerze? Nie jesteś sam. W wielu rzeczywistych projektach brakujące czcionki powodują ciche przesunięcia układu, a jedynym sposobem, aby dowiedzieć się, co się stało, jest nasłuchiwanie strumienia ostrzeżeń emitowanego przez Aspose.Words.  

W tym tutorialu przeprowadzimy Cię przez kompletny, gotowy do uruchomienia przykład, który **wykrywa brakujące czcionki**, pokazuje **jak wykrywać brakujące czcionki** programowo, a także daje szybką wskazówkę dotyczącą **obsługi brakujących czcionek**, aby Twoje wyjście było przewidywalne.

> **Szybka uwaga:** Kod działa z Aspose.Words 23.9 (lub nowszym) i wymaga Java 8+.

---

## Czego będziesz potrzebować

- **Aspose.Words for Java** (zależność Maven/Gradle lub JAR na ścieżce klas)  
- Plik Word (`input.docx`), który odwołuje się do czcionki niezainstalowanej w systemie (np. „Comic Sans MS”)  
- Środowisko IDE Java lub prosta konfiguracja linii poleceń `javac`/`java`  

Nie są wymagane żadne inne biblioteki — wszystko inne znajduje się wewnątrz pakietu Aspose.Words.

---

## Krok 1 – Skonfiguruj LoadOptions, aby przechwytywać ostrzeżenia  

Aby rozpocząć nasłuchiwanie ostrzeżeń, musisz utworzyć instancję `LoadOptions`. Ten obiekt instruuje loader, aby śledził wszelkie napotkane problemy, takie jak brakujące czcionki.

```java
import com.aspose.words.*;

public class FontWarningDemo {
    public static void main(String[] args) throws Exception {

        // Step 1: Create LoadOptions that will store warning information
        LoadOptions loadOptions = new LoadOptions();

        // ... the rest of the code follows
```

**Dlaczego to ważne:** Bez `LoadOptions` loader cicho zastępuje brakujące czcionki domyślną czcionką systemową i nigdy nie dowiesz się, że doszło do podstawienia. Włączenie ostrzeżeń daje pełną widoczność.

---

## Krok 2 – Załaduj dokument przy użyciu LoadOptions  

Teraz faktycznie ładujemy dokument. `LoadOptions`, które właśnie utworzyliśmy, jest przekazywany do konstruktora, więc wszelkie ostrzeżenia wygenerowane podczas parsowania są przechwytywane.

```java
        // Step 2: Load the document that may contain missing fonts
        Document document = new Document("YOUR_DIRECTORY/input.docx", loadOptions);
```

**Wskazówka:** Jeśli przetwarzasz wiele plików w partii, ponownie użyj tej samej instancji `LoadOptions`, aby uniknąć niepotrzebnego tworzenia obiektów.

---

## Krok 3 – Iteruj po przechwyconych ostrzeżeniach  

Aspose.Words przechowuje każde ostrzeżenie jako obiekt `WarningInfo`. Interesują nas tylko ostrzeżenia związane z czcionkami, więc filtrujemy je pod kątem `FontSubstitutionWarningInfo`.

```java
        // Step 3: Loop through all warnings generated while loading
        for (WarningInfo warning : document.getWarnings()) {
            // Step 3a: Keep only font substitution warnings
            if (warning instanceof FontSubstitutionWarningInfo) {
                FontSubstitutionWarningInfo fontWarning = (FontSubstitutionWarningInfo) warning;

                // Step 4: Output the requested and actual font names
                System.out.println("Requested: " + fontWarning.getRequestedFontName()
                        + " → Substituted: " + fontWarning.getActualFontName());
            }
        }
    }
}
```

**Explanation:**  
- `document.getWarnings()` zwraca listę wszystkich ostrzeżeń, które wystąpiły podczas ładowania.  
- `FontSubstitutionWarningInfo` zawiera dwie kluczowe informacje: **żądana czcionka** (ta, o którą prosił DOCX) oraz **rzeczywista czcionka**, do której Aspose.Words sięgnął.  
- Wypisując oba, natychmiast widzisz, które czcionki są brakujące i jakie podstawienie miało miejsce.

---

## Krok 4 – (Opcjonalnie) Obsłuż brakujące czcionki programowo  

Przechwytywanie ostrzeżeń to tylko połowa historii. Gdy już wiesz, że czcionka jest brakująca, możesz chcieć **obsłużyć brakujące czcionki** poprzez dostarczenie własnego podstawienia lub zalogowanie problemu do późniejszej analizy.

```java
                // Optional: Replace the missing font with a known fallback
                FontSettings fontSettings = new FontSettings();
                fontSettings.getSubstitutionSettings().getTableSubstitution()
                    .addSubstitutes(fontWarning.getRequestedFontName(), "Arial");
                document.setFontSettings(fontSettings);
```

**Why do this?**  
- Gwarantuje spójne renderowanie na różnych maszynach.  
- Zapobiega nieoczekiwanym zmianom układu w PDF‑ach lub obrazach generowanych później.  

Możesz także zapisać szczegóły ostrzeżenia w bazie danych, wysłać e‑mail do zespołu treści lub nawet przerwać proces, jeśli brakująca czcionka jest krytyczna.

---

## Pełny działający przykład  

Poniżej znajduje się kompletny, uruchamialny program. Wystarczy zamienić `YOUR_DIRECTORY/input.docx` na ścieżkę do swojego pliku testowego, dodać plik JAR Aspose.Words do classpath i uruchomić.

```java
import com.aspose.words.*;

public class FontWarningDemo {
    public static void main(String[] args) throws Exception {

        // 1️⃣ Create LoadOptions to capture warnings
        LoadOptions loadOptions = new LoadOptions();

        // 2️⃣ Load the document that may contain missing fonts
        Document document = new Document("YOUR_DIRECTORY/input.docx", loadOptions);

        // 3️⃣ Iterate through all warnings
        for (WarningInfo warning : document.getWarnings()) {
            // 3a️⃣ Filter only font substitution warnings
            if (warning instanceof FontSubstitutionWarningInfo) {
                FontSubstitutionWarningInfo fontWarning = (FontSubstitutionWarningInfo) warning;

                // 4️⃣ Display the requested and actual font names
                System.out.println("Requested: " + fontWarning.getRequestedFontName()
                        + " → Substituted: " + fontWarning.getActualFontName());

                // 5️⃣ (Optional) Provide a custom fallback
                FontSettings fontSettings = new FontSettings();
                fontSettings.getSubstitutionSettings().getTableSubstitution()
                    .addSubstitutes(fontWarning.getRequestedFontName(), "Arial");
                document.setFontSettings(fontSettings);
            }
        }

        // 6️⃣ Save the document if you need to see the result with the fallback applied
        document.save("output.docx");
    }
}
```

**Oczekiwany wynik** (gdy „Comic Sans MS” jest brakująca):

```
Requested: Comic Sans MS → Substituted: Arial
```

Po uruchomieniu opcjonalnego kodu podstawienia, zapisany `output.docx` będzie renderowany przy użyciu **Arial**, wszędzie tam, gdzie pierwotnie odwoływano się do „Comic Sans MS”.

---

## Częste pytania i przypadki brzegowe  

| Pytanie | Odpowiedź |
|----------|-----------|
| *Co jeśli dokument ma wiele brakujących czcionek?* | Pętla wyemituje ostrzeżenie dla każdej z nich. Możesz zebrać je w `Map<String, String>` do przetwarzania wsadowego. |
| *Czy to działa dla PDF‑ów generowanych z dokumentu?* | Zdecydowanie tak. Podstawianie czcionek odbywa się w fazie ładowania, więc każde późniejsze eksportowanie (PDF, HTML, obraz) używa rozpoznanych czcionek. |
| *Czy mogę wyciszyć ostrzeżenia zamiast je przechwytywać?* | Tak — ustaw `loadOptions.setWarningCallback(null);`, ale utracisz widoczność brakujących czcionek. |
| *Czy lista ostrzeżeń jest czyszczona po zapisaniu?* | Kolekcja ostrzeżeń należy do instancji `Document`. Po wywołaniu `document.save()` lista pozostaje niezmieniona, chyba że utworzysz nowy `Document`. |
| *A co z niestandardowymi czcionkami osadzonymi w DOCX?* | Osadzone czcionki są traktowane jako dostępne; Aspose.Words użyje ich, nawet jeśli nie są zainstalowane w systemie hosta. |

---

## Wskazówki dla produkcji  

- **Cache FontSettings:** Jeśli przetwarzasz setki plików, utwórz jedną `FontSettings` z preferowanymi podstawieniami i używaj jej ponownie, aby uniknąć dodatkowego obciążenia.  
- **Log Structured Data:** Zamiast zwykłego `System.out`, zapisz ostrzeżenia do logu JSON — to ułatwia analizę downstream (np. „najczęściej brakujące czcionki”).  
- **Validate Early:** Uruchom szybkie „dry‑load” z `LoadOptions` przed intensywnym przetwarzaniem; przerwij wczesnie, jeśli brakują krytyczne czcionki.  
- **Thread Safety:** Obiekty `Document` nie są bezpieczne wątkowo. Przetwarzaj każdy plik w osobnym wątku lub użyj `LoadOptions` lokalnego dla wątku.  

---

## Zakończenie  

Teraz wiesz **jak przechwycić ostrzeżenia** w Aspose.Words dla Javy, **wykrywać brakujące czcionki** oraz **obsługiwać brakujące czcionki** przy użyciu czystej strategii podstawień. Korzystając z `LoadOptions` i iterując po `document.getWarnings()`, uzyskasz pełny wgląd w zdarzenia podstawiania czcionek, zapewniając, że generowane dokumenty wyglądają dokładnie tak, jak zamierzone, we wszystkich środowiskach.

Gotowy na kolejny krok? Spróbuj rozszerzyć ten wzorzec, aby **wykrywać brakujące obrazy**, **śledzić nieobsługiwane funkcje**, a nawet **automatycznie osadzać brakujące czcionki** w pliku wyjściowym. To samo podejście do przechwytywania ostrzeżeń działa w wielu innych scenariuszach przetwarzania dokumentów, czyniąc Twój kod odpornym i przyszłościowym.

Szczęśliwego kodowania i niech Twoje dokumenty zawsze renderują się pięknie!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}