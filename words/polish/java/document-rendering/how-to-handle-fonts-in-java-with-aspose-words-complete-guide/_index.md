---
category: general
date: 2026-02-10
description: Jak obsługiwać czcionki w Javie przy użyciu Aspose.Words. Dowiedz się
  o ostrzeżeniach dotyczących podstawiania czcionek, wywołaniach zwrotnych LoadOptions
  oraz obsłudze brakujących czcionek w kilku krokach.
draft: false
keywords:
- how to handle fonts
- font substitution warnings
- Aspose.Words Java
- LoadOptions warning callback
- MissingFont.docx handling
language: pl
og_description: Jak obsługiwać czcionki w Javie z Aspose.Words. Ten przewodnik pokazuje
  krok po kroku obsługę zamiany czcionek, wywołań zwrotnych ostrzeżeń oraz zarządzanie
  brakującymi czcionkami.
og_title: Jak obsługiwać czcionki w Javie – Pełny samouczek Aspose.Words
tags:
- Java
- Aspose.Words
- Document Processing
title: Jak obsługiwać czcionki w Javie z Aspose.Words – Kompletny przewodnik
url: /pl/java/document-rendering/how-to-handle-fonts-in-java-with-aspose-words-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak obsługiwać czcionki w Javie – Kompletny przewodnik

Zastanawiałeś się kiedyś **jak obsługiwać czcionki**, gdy dokument Word odwołuje się do kroju pisma, który nie jest zainstalowany na twoim serwerze? To sytuacja, która sprawia trudności wielu programistom, szczególnie gdy automatyzujesz generowanie lub konwersję dokumentów przy użyciu Aspose.Words. Dobra wiadomość? Możesz przechwycić każde zdarzenie podstawienia czcionki i zareagować na nie — bez domysłów.

W tym samouczku przeprowadzimy Cię przez rzeczywisty przykład, który pokazuje **jak obsługiwać czcionki** przy użyciu Aspose.Words for Java. Podłączymy callback ostrzeżeń, odfiltrujemy tylko ostrzeżenia o podstawieniu czcionki i wydrukujemy przyjazną wiadomość dla każdej brakującej czcionki. Po zakończeniu zrozumiesz, dlaczego to ważne, jak to czysto zaimplementować i czego się spodziewać, gdy kod zostanie uruchomiony.

> **Co otrzymasz:** kompletną, gotową do uruchomienia klasę Java, wyjaśnienie każdego wiersza, wskazówki do użycia w produkcji oraz szybki sposób na zweryfikowanie wyniku.

---

## Wymagania wstępne

- **Java 8** (lub nowsza) zainstalowana na twoim komputerze.  
- **Aspose.Words for Java** JAR (najnowsza wersja na dzień 2026‑02, np. `aspose-words-23.11.jar`).  
- Przykładowy dokument (`MissingFont.docx`), który odwołuje się do czcionki, której nie masz zainstalowanej.  
- Środowisko programistyczne (IntelliJ IDEA, Eclipse lub nawet prosty edytor tekstu + wiersz poleceń).

Nie są potrzebne dodatkowe frameworki — wystarczy czysta Java i JAR Aspose.Words.

![Diagram przedstawiający, jak obsługiwać czcionki w Javie przy użyciu Aspose.Words](https://example.com/handle-fonts-diagram.png "diagram jak obsługiwać czcionki")

*Tekst alternatywny obrazu: diagram jak obsługiwać czcionki*

## Krok 1 – Konfiguracja callbacku ostrzeżeń (rdzeń **jak obsługiwać czcionki**)

Gdy Aspose.Words ładuje dokument, generuje szereg obiektów `WarningInfo` dla wszystkiego, co nie jest idealne. Dołączając `IWarningCallback`, możesz przechwycić te ostrzeżenia w czasie rzeczywistym.

```java
import com.aspose.words.*;

public class FontSubstitutionDemo {

    public static void main(String[] args) throws Exception {

        // 1️⃣ Create LoadOptions and register a warning callback.
        LoadOptions loadOptions = new LoadOptions();

        // The callback will be invoked for every warning Aspose.Words emits.
        loadOptions.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) {
                // 2️⃣ Filter for FONT_SUBSTITUTION warnings only.
                if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                    System.out.println("Substituted font: " + info.getDescription());
                }
                // Other warning types are ignored – you could log them here if you wish.
            }
        });
```

**Dlaczego to jest ważne:**  
Jeśli pominiesz callback, Aspose.Words cicho zamieni brakujące czcionki na domyślną, i nigdy nie dowiesz się, które czcionki były brakujące. Obsługując ostrzeżenie, zyskujesz przejrzystość i możesz zdecydować, czy osadzić czcionkę zapasową, zalogować problem, czy nawet przerwać operację.

## Krok 2 – Ładowanie dokumentu przy użyciu skonfigurowanego `LoadOptions`

Teraz, gdy callback jest gotowy, po prostu ładujemy dokument. Instancja `LoadOptions`, którą utworzyliśmy powyżej, jest przekazywana bezpośrednio do konstruktora `Document`.

```java
        // 3️⃣ Load a document that may contain missing fonts.
        // Replace the path with the actual location of your test file.
        Document document = new Document("YOUR_DIRECTORY/MissingFont.docx", loadOptions);

        // At this point the warning callback runs automatically.
        // Any font substitution will be printed to the console.
```

**Czego się spodziewać:**  
Gdy `MissingFont.docx` odwołuje się, powiedzmy, do *Comic Sans MS*, a na serwerze jest tylko *Arial*, callback wypisze coś w rodzaju:

```
Substituted font: Font 'Comic Sans MS' was substituted with 'Arial'.
```

Jeśli dokument zostanie załadowany bez brakujących czcionek, nic nie zostanie wydrukowane — dokładnie to, czego chcesz, gdy **jak obsługiwać czcionki** odbywa się płynnie.

## Krok 3 – (Opcjonalnie) Weryfikacja tabeli czcionek dokumentu

Czasami trzeba sprawdzić, które czcionki dokument faktycznie używa po załadowaniu. Aspose.Words ułatwia to zadanie.

```java
        // Optional: List all fonts the document thinks it has.
        FontInfoCollection fonts = document.getFontInfos();
        System.out.println("\n--- Fonts used in the document ---");
        for (FontInfo font : fonts) {
            System.out.println(font.getFullName());
        }
    }
}
```

**Kiedy to używać:**  
Jeśli tworzysz przetwarzacz wsadowy, który musi zgłaszać brakujące czcionki przed publikacją PDF, wydrukowanie tabeli czcionek daje ostateczną kontrolę poprawności.

## Pełny, gotowy do uruchomienia przykład

Łącząc wszystko razem, oto pełna klasa, którą możesz skopiować‑wkleić do `FontSubstitutionDemo.java` i uruchomić:

```java
import com.aspose.words.*;

public class FontSubstitutionDemo {
    public static void main(String[] args) throws Exception {

        // Step 1 – Create LoadOptions with a warning callback.
        LoadOptions loadOptions = new LoadOptions();
        loadOptions.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) {
                // Handle only font‑substitution warnings.
                if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                    System.out.println("Substituted font: " + info.getDescription());
                }
            }
        });

        // Step 2 – Load the document that may contain missing fonts.
        Document document = new Document("YOUR_DIRECTORY/MissingFont.docx", loadOptions);

        // Step 3 – (Optional) List the fonts the document finally uses.
        FontInfoCollection fonts = document.getFontInfos();
        System.out.println("\n--- Fonts used in the document ---");
        for (FontInfo font : fonts) {
            System.out.println(font.getFullName());
        }
    }
}
```

**Uruchamianie kodu:**  

```bash
javac -cp "aspose-words-23.11.jar" FontSubstitutionDemo.java
java -cp ".:aspose-words-23.11.jar" FontSubstitutionDemo
```

Powinieneś zobaczyć komunikaty o podstawieniach, a następnie ostateczną listę czcionek.

## Częste pytania i przypadki brzegowe

### Co zrobić, jeśli muszę samodzielnie podstawić czcionkę?

Callback ostrzeżeń informuje tylko *co* zostało podstawione. Jeśli chcesz wymusić konkretną czcionkę zapasową, możesz użyć `FontSettings`:

```java
FontSettings fontSettings = new FontSettings();
fontSettings.setSubstitutionSettings(new FontSubstitutionSettings() {{
    getTableSubstitution().addSubstitutes("MissingFont", "Arial");
}});
loadOptions.setFontSettings(fontSettings);
```

Teraz każde wystąpienie „MissingFont” zostanie zastąpione „Arial” przed załadowaniem dokumentu.

### Czy to działa przy zapisywaniu do PDF?

Zdecydowanie tak. Ten sam callback wywołuje się podczas `document.save("out.pdf")`, jeśli renderer PDF również musi podstawić czcionki. Wystarczy zachować te same `LoadOptions` lub podłączyć nowy callback do `PdfSaveOptions`.

### Jak to zachowuje się w środowisku wielowątkowym?

`LoadOptions` **nie** jest bezpieczne wątkowo, więc twórz nową instancję dla każdego wątku. Sam callback może być bezstanowy (jak pokazano) lub możesz wstrzyknąć logger, który jest świadomy wątków.

### Co zrobić, jeśli brakująca czcionka jest niestandardową czcionką firmową?

Zazwyczaj osadzisz tę czcionkę w folderze czcionek serwera i wskażesz Aspose.Words na nią za pomocą `FontSettings.setFontsFolder("path/to/fonts", true)`. Callback przestanie się wywoływać dla tej czcionki, ponieważ nie będzie już brakować.

## Profesjonalne wskazówki dla gotowego do produkcji zarządzania czcionkami

- **Loguj, a nie tylko `System.out.println`** – używaj odpowiedniego frameworka logowania (SLF4J, Log4j), aby móc przechwytywać ostrzeżenia w systemie monitoringu.  
- **Cache'uj wyszukiwania czcionek** – jeśli przetwarzasz tysiące dokumentów, unikaj wielokrotnego skanowania katalogu czcionek systemu. Załaduj czcionki raz do instancji `FontSettings` i używaj jej ponownie.  
- **Fail fast, gdy krytyczne czcionki są brakujące** – możesz wyrzucić wyjątek wewnątrz callbacku, jeśli konkretna czcionka jest wymagana do zgodności z identyfikacją marki.  
- **Testuj różnorodne dokumenty** – uwzględnij PDF‑y, DOCX‑y i DOC‑y; każdy format może wywołać inne typy ostrzeżeń.  

## Podsumowanie

Omówiliśmy **jak obsługiwać czcionki** w Javie przy użyciu Aspose.Words od początku do końca:

1. Dołącz `IWarningCallback`, aby przechwycić ostrzeżenia o podstawieniu czcionki.  
2. Załaduj dokument z `LoadOptions`, aby callback działał automatycznie.  
3. (Opcjonalnie) Sprawdź ostateczną listę czcionek, aby potwierdzić wynik.  

Stosując te kroki, zyskujesz pełną przejrzystość brakujących czcionek, możesz egzekwować firmowe zasady dotyczące czcionek i uniknąć cichych podstawień, które mogłyby zepsuć wygląd generowanych PDF‑ów lub plików Word.

Gotowy na kolejne wyzwanie? Spróbuj zamienić callback, aby logował *wszystkie* ostrzeżenia, poeksperymentuj z `FontSettings` w celu stworzenia własnych reguł podstawień lub zintegrować tę logikę z mikrousługą Spring‑Boot, która przetwarza dokumenty w locie.

Miłego kodowania i niech twoje dokumenty zawsze renderują się z odpowiednią czcionką!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}