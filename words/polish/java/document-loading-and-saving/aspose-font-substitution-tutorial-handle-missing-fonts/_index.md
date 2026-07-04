---
category: general
date: 2026-05-04
description: Samouczek podstawiania czcionek Aspose pokazuje, jak obsługiwać brakujące
  czcionki w Javie, używając wywołań zwrotnych ostrzeżeń i LoadOptions, aby zapewnić
  niezawodne ładowanie dokumentów.
draft: false
keywords:
- aspose font substitution tutorial
- handle missing fonts
- Aspose.Words font warning callback
- Java LoadOptions warning handling
- missing font detection Aspose
language: pl
og_description: Samouczek zamiany czcionek Aspose wyjaśnia, jak radzić sobie z brakującymi
  czcionkami w Javie, przechwytywać zdarzenia zamiany i zapewnić prawidłowy wygląd
  dokumentów.
og_title: Poradnik zamiany czcionek Aspose – Obsługa brakujących czcionek
tags:
- Aspose.Words
- Java
- Font Management
title: Samouczek wymiany czcionek Aspose – Obsługa brakujących czcionek
url: /pl/java/document-loading-and-saving/aspose-font-substitution-tutorial-handle-missing-fonts/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose Font Substitution Tutorial – Obsługa brakujących czcionek

Kiedykolwiek potrzebowałeś **aspose font substitution tutorial**, ponieważ załadowany DOCX wygląda nagle niepoprawnie? Nie jesteś sam — brakujące czcionki to podstępne źródło błędów, które mogą zamienić perfekcyjnie sformatowany raport w nieczytelny bałagan. Dobrą wiadomością jest to, że Aspose.Words zapewnia czysty sposób **obsługi brakujących czcionek** zanim zepsują one układ.

W tym przewodniku przejdziemy przez kompletny, gotowy do uruchomienia przykład w Javie, który przechwytuje ostrzeżenia o zamianie czcionek, wyjaśnia, dlaczego każdy element ma znaczenie, i pokazuje, jak zweryfikować wynik. Po zakończeniu będziesz dokładnie wiedział, jak utrzymać dokumenty w ostrej formie, nawet gdy oryginalne kroje nie są zainstalowane na maszynie.

## Czego się nauczysz

- Jak zarejestrować własny `IWarningCallback`, który nasłuchuje zdarzeń `FONT_SUBSTITUTION`.  
- Dlaczego użycie `LoadOptions` jest zalecaną metodą dla niezawodnej obsługi czcionek.  
- Sposoby testowania rozwiązania na celowo uszkodzonym dokumencie.  
- Typowe pułapki (np. zapomnienie o ustawieniu callbacku) i szybkie poprawki.  

**Wymagania wstępne**: Java 8+ zainstalowana, ważna licencja Aspose.Words for Java (lub darmowa wersja ewaluacyjna) oraz podstawowe IDE, takie jak IntelliJ lub Eclipse. Nie są potrzebne żadne dodatkowe biblioteki.

---

![Aspose font substitution tutorial diagram](https://example.com/images/font-substitution-diagram.png "Aspose font substitution tutorial diagram")

## Krok 1 – Zdefiniuj Warning Callback, aby przechwycić zamiany  

Pierwszą rzeczą, którą robi Aspose.Words, gdy nie może znaleźć żądanej czcionki, jest wywołanie zdarzenia `WarningInfo`. Implementując `IWarningCallback` możesz logować, wyświetlać lub nawet przerwać ładowanie, jeśli tego potrzebujesz.

```java
// Step 1: Create a callback that prints font‑substitution warnings
class FontWarningCollector implements IWarningCallback {
    @Override
    public void warning(WarningInfo info) {
        // Only react to font substitution warnings
        if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
            System.out.println("Font substitution detected: " + info.getDescription());
        }
    }
}
```

**Dlaczego to ważne** – Bez callbacku nigdy nie dowiesz się, że Aspose zamienił *Arial* na *Liberation Sans* (lub inny wybrany zamiennik). Ta cicha zamiana może powodować przesunięcia układu, szczególnie w tabelach lub układach wielokolumnowych.

---

## Krok 2 – Podłącz callback do `LoadOptions`

`LoadOptions` jest centralnym miejscem dla wszystkiego, co wpływa na sposób odczytu dokumentu. Podłączając callback w tym miejscu, zapewniasz, że **każdy** dokument ładowany z tymi opcjami wywoła Twoją logikę ostrzeżeń.

```java
// Step 2: Wire the callback into LoadOptions
LoadOptions loadOptions = new LoadOptions();
loadOptions.setWarningCallback(new FontWarningCollector());
```

**Wskazówka** – Jeśli planujesz ładować kilka dokumentów w partii, użyj tego samego obiektu `LoadOptions`. Oszczędza to koszt tworzenia obiektów i utrzymuje spójność logowania.

---

## Krok 3 – Załaduj dokument, który może wymagać zamiany czcionek  

Teraz faktycznie odczytujemy plik, o którym wiemy, że brakuje w nim czcionki. Zamień `YOUR_DIRECTORY` na folder zawierający Twoje pliki testowe.

```java
// Step 3: Load a document that deliberately references a missing font
String inputPath = "YOUR_DIRECTORY/missing-font.docx";
Document doc = new Document(inputPath, loadOptions);
```

Gdy loader natrafi na glif, którego nie da się wyrenderować, callback z **Kroku 1** wypisze przyjazny komunikat w konsoli. Przykład:

```
Font substitution detected: Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
```

**Przypadek brzegowy** – Jeśli dokument zawiera *osadzone* czcionki, Aspose użyje ich najpierw i pominie ostrzeżenie. To oczekiwane zachowanie; ostrzeżenia pojawiają się tylko dla naprawdę brakujących czcionek.

---

## Krok 4 – Zapisz dokument (już z zamienionymi czcionkami)

Po zakończeniu ładowania Aspose już wewnętrznie zamienił brakujące czcionki. Zapisanie dokumentu zachowuje tę zamianę, więc wynik wygląda dokładnie tak, jak widziałeś w konsoli.

```java
// Step 4: Persist the document – the fonts are already substituted if needed
String outputPath = "YOUR_DIRECTORY/loaded.docx";
doc.save(outputPath);
System.out.println("Document saved to " + outputPath);
```

Otwórz `loaded.docx` w Wordzie lub LibreOffice i zobaczysz niezmieniony układ, mimo że oryginalna czcionka nie jest zainstalowana na Twoim komputerze.

---

## Krok 5 – Zweryfikuj wynik programowo (opcjonalnie)

Jeśli chcesz mieć pewność, że żadne nieoczekiwane zamiany nie przeszły niezauważone, możesz po załadowaniu zapytać tabelę czcionek dokumentu.

```java
// Optional: List all fonts actually used in the saved document
for (FontInfo fontInfo : doc.getFontInfos()) {
    System.out.println("Used font: " + fontInfo.getFontName());
}
```

Wynik powinien zawierać czcionkę zastępczą (np. *Arial*) zamiast brakującej. Jest to przydatne w zautomatyzowanych pipeline'ach, gdzie potrzebne jest zapewnienie, że końcowy PDF lub DOCX spełnia wymogi brandingu.

---

## Pro Tips & Common Pitfalls

- **Pro tip:** Ustaw `loadOptions.setFontSettings(new FontSettings())`, jeśli musisz skierować Aspose do własnego folderu czcionek przed ładowaniem. To zmniejsza liczbę zamian.
- **Uwaga:** Zapomnienie o wywołaniu `setWarningCallback`. Kod nadal będzie działał, ale przegapisz kluczowe komunikaty diagnostyczne.
- **Uwaga dotycząca wydajności:** Ładowanie dużych dokumentów z wieloma brakującymi czcionkami może generować dużo ostrzeżeń. Rozważ ograniczenie wyjścia lub zapisywanie ich do pliku logu zamiast `System.out`.
- **Co zrobić, aby przerwać przy zamianie?** Zamień wywołanie `System.out.println` na `throw new RuntimeException(info.getDescription())` wewnątrz callbacku. To wymusi niepowodzenie ładowania, co jest przydatne w scenariuszach wymagających ścisłej zgodności.

---

## Frequently Asked Questions

**Q: Czy to działa z formatami PDF lub obrazami?**  
A: Callback ostrzeżeń jest specyficzny dla fazy ładowania formatów przetwarzania Word (`.docx`, `.doc`, `.rtf` itp.). Renderowanie PDF używa innego pipeline'u, ale nadal możesz przechwycić ostrzeżenia związane z czcionkami za pomocą `PdfLoadOptions`.

**Q: Czy mogę zamienić konkretną czcionkę na inną wybraną przeze mnie?**  
A: Tak. Utwórz obiekt `FontSettings`, wywołaj `fontSettings.getSubstitutionSettings().getTableSubstitutes().addSubstitutes("MissingFont", "MyPreferredFont")` i przypisz go do `loadOptions.setFontSettings(fontSettings)`.

**Q: Czy callback jest bezpieczny wątkowo?**  
A: Domyślna implementacja nie jest zsynchronizowana. Jeśli ładujesz dokumenty równolegle, upewnij się, że Twoja implementacja callbacku obsługuje dostęp współbieżny (np. używając `ConcurrentLinkedQueue` do logowania).

---

## Conclusion

Masz teraz kompletny **aspose font substitution tutorial**, który pokazuje, jak **obsługiwać brakujące czcionki** w Java w sposób elegancki. Definiując własny `IWarningCallback`, podłączając go do `LoadOptions` i zapisując dokument, zapewniasz spójność wyjścia niezależnie od tego, jakie czcionki są zainstalowane na maszynie hosta.  

Od tego momentu możesz eksplorować:

- Niestandardowe tabele zamiany czcionek dla zgodności z marką.  
- Integrację loggera ostrzeżeń z SLF4J lub Log4j dla diagnostyki produkcyjnej.  
- Rozszerzenie callbacku w celu zbierania statystyk w partii dokumentów.

Wypróbuj, dostosuj czcionki zastępcze i pozwól swoim dokumentom pozostać pięknymi, nawet gdy oryginalne kroje znikną. Szczęśliwego kodowania!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}