---
category: general
date: 2026-01-10
description: Dowiedz się, jak używać LoadOptions do obsługi brakujących czcionek w
  Aspose.Words. Krok po kroku kod, wskazówki i najlepsze praktyki zapewniające solidne
  ładowanie dokumentów.
draft: false
keywords:
- how to use loadoptions
- handle missing fonts
- Aspose.Words warning callback
- font substitution handling
- document loading options
language: pl
og_description: Jak używać LoadOptions do obsługi brakujących czcionek w Aspose.Words.
  Uzyskaj pełny, działający przykład z wyjaśnieniami i praktycznymi wskazówkami.
og_title: Jak używać LoadOptions w Aspose.Words – kompletny przewodnik
tags:
- Aspose.Words
- C#
- .NET
title: Jak używać LoadOptions w Aspose.Words – Kompletny przewodnik
url: /pl/net/programming-with-loadoptions/how-to-use-loadoptions-in-aspose-words-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak używać LoadOptions w Aspose.Words – Kompletny przewodnik

Zastanawiałeś się kiedyś **jak używać LoadOptions** przy ładowaniu dokumentu Word, który może nie mieć niektórych czcionek? Nie jesteś jedynym, który się nad tym zastanawia. W wielu rzeczywistych projektach dokumenty przemieszczają się między maszynami, a docelowy system często nie posiada dokładnych krojów użytych przez autora. Efekt? Nieoczekiwane podstawienia czcionek, które mogą zepsuć układ, ukryć ważne znaki lub po prostu wyglądać niezgodnie z marką.  

Na szczęście Aspose.Words oferuje czysty sposób na *obsługę brakujących czcionek* poprzez udostępnienie obiektu `LoadOptions` z callbackiem ostrzeżeń. W tym samouczku dowiesz się dokładnie **jak używać LoadOptions**, aby przechwycić ostrzeżenia o podstawieniu czcionek, zalogować je i utrzymać solidność swojego potoku przetwarzania.

Omówimy:

* Ustawienie klasy callbacku ostrzeżeń
* Konfigurowanie `LoadOptions` z tym callbackiem
* Ładowanie dokumentu z monitorowaniem brakujących czcionek
* Wskazówki dotyczące rozwiązywania problemów i rozszerzania rozwiązania

Nie potrzebujesz zewnętrznej dokumentacji — wszystko, co potrzebne, znajduje się tutaj.

---

## Czego będziesz potrzebować

Zanim zaczniemy, upewnij się, że masz:

* **Aspose.Words for .NET** (najnowsza wersja na 2026) zainstalowana przez NuGet
* Środowisko programistyczne .NET (Visual Studio, Rider lub VS Code)
* Przykładowy plik DOCX, który odwołuje się do czcionki, której nie masz zainstalowanej (nazwijmy go `input.docx`)

To wszystko — nie są wymagane dodatkowe biblioteki.

---

## Krok 1 – Zdefiniuj callback ostrzeżeń, aby przechwycić podstawienie czcionki

Pierwszym elementem układanki jest klasa implementująca `IWarningCallback`. Aspose.Words wywoła jej metodę `Warning` za każdym razem, gdy napotka coś godnego uwagi — np. brakującą czcionkę.

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;

/// <summary>
/// Custom warning handler that prints font‑substitution messages to the console.
/// </summary>
class FontWarningCallback : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // We're only interested in font‑substitution warnings.
        if (info.WarningType == WarningType.FontSubstitution)
        {
            Console.WriteLine($"⚠️ Font substitution detected: {info.Description}");
        }
    }
}
```

**Dlaczego to jest ważne:**  
Filtrując po `WarningType.FontSubstitution` unikamy bałaganu spowodowanego niepowiązanymi ostrzeżeniami (np. przestarzałe funkcje). Callback daje pełną kontrolę — możesz logować do pliku, podnieść wyjątek lub nawet spróbować programowo osadzić czcionkę zapasową.

---

## Krok 2 – Skonfiguruj LoadOptions z callbackiem

Teraz, gdy mamy obsługę, musimy powiedzieć Aspose.Words, aby jej używał. To jest miejsce, w którym **jak używać LoadOptions** w praktyce.

```csharp
// Create a LoadOptions instance and attach our custom callback.
var loadOptions = new LoadOptions
{
    WarningCallback = new FontWarningCallback()
};
```

**Wskazówka:** `LoadOptions` oferuje wiele innych przełączników (np. `Password`, `LoadFormat`, `Encoding`). Możesz je łączyć, ale do obsługi brakujących czcionek `WarningCallback` jest gwiazdą tego rozwiązania.

---

## Krok 3 – Załaduj dokument używając skonfigurowanych opcji

Gdy `LoadOptions` jest gotowy, ładowanie dokumentu jest proste. Aspose.Words automatycznie wywoła callback dla każdej czcionki, której nie znajdzie.

```csharp
// Path to the DOCX that may reference unavailable fonts.
string docPath = Path.Combine(Environment.CurrentDirectory, "input.docx");

// Load the document while the warning callback monitors font issues.
Document doc = new Document(docPath, loadOptions);

// At this point you can continue processing the document—saving, editing, etc.
Console.WriteLine("✅ Document loaded successfully.");
```

**Oczekiwany wynik:**  

Jeśli `input.docx` używa czcionki o nazwie *„GothicBold”*, której nie ma zainstalowanej, zobaczysz coś takiego:

```
⚠️ Font substitution detected: Font substitution applied. Original font: GothicBold, Substituted font: Arial.
✅ Document loaded successfully.
```

Linia ostrzeżenia pojawia się **dokładnie w momencie napotkania brakującej czcionki**, dając natychmiastową informację zwrotną.

---

## Krok 4 – (Opcjonalnie) Kontynuuj przetwarzanie dokumentu

Zazwyczaj będziesz chciał zrobić więcej niż tylko załadować plik. Poniżej kilka typowych działań po załadowaniu, które działają płynnie z naszą konfiguracją ostrzeżeń.

### 4.1 Zapisz dokument jako PDF

```csharp
// Convert to PDF – the substituted fonts are already baked into the layout.
doc.Save("output.pdf", SaveFormat.Pdf);
Console.WriteLine("📄 PDF saved as output.pdf");
```

### 4.2 Zastąp brakujące czcionki znanym zapasem

Jeśli wolisz konkretny zapas (np. *„Calibri”*), możesz dostosować `FontSettings` przed zapisem:

```csharp
var fontSettings = new FontSettings();
fontSettings.SubstitutionSettings.FontSubstitutionRules.AddSubstitutes(
    "GothicBold", new[] { "Calibri", "Arial" });

doc.FontSettings = fontSettings;
doc.Save("output-with-fallback.pdf", SaveFormat.Pdf);
Console.WriteLine("🔄 PDF saved with explicit fallback fonts.");
```

### 4.3 Zaloguj wszystkie ostrzeżenia do pliku

```csharp
class FileLoggingWarningCallback : IWarningCallback
{
    private readonly string _logPath = "load-warnings.log";

    public void Warning(WarningInfo info)
    {
        File.AppendAllText(_logPath,
            $"{DateTime.Now:u} - {info.WarningType}: {info.Description}{Environment.NewLine}");
    }
}

// Use it:
var loadOptionsWithFileLog = new LoadOptions
{
    WarningCallback = new FileLoggingWarningCallback()
};
```

Te fragmenty ilustrują **jak używać LoadOptions** poza podstawowym przypadkiem, dając elastyczność dla rozwiązań klasy produkcyjnej.

---

## Częste pułapki i jak **obsługiwać brakujące czcionki** elegancko

| Pułapka | Dlaczego się pojawia | Jak naprawić / złagodzić |
|---------|----------------------|--------------------------|
| **Brak podłączonego callbacku** | Zapomniałeś ustawić `WarningCallback`. | Zawsze twórz instancję `LoadOptions` i przypisz swój handler przed ładowaniem. |
| **Callback tylko wypisuje, nigdy nie zapisuje** | W usłudze webowej wyjście konsoli znika. | Zastąp `Console.WriteLine` loggerem (Serilog, NLog) lub zapisz do trwałego magazynu. |
| **Wiele brakujących czcionek, zgłoszona tylko pierwsza** | Twój callback rzuca wyjątek przy pierwszym ostrzeżeniu. | Utrzymuj callback lekki; unikaj rzucania wyjątków, chyba że naprawdę chcesz przerwać. |
| **Podstawiona czcionka wygląda nieprawidłowo** | Domyślna substytucja może wybrać wizualnie niepodobną czcionkę. | Użyj `FontSettings.SubstitutionSettings.FontSubstitutionRules`, aby priorytetyzować preferowany zapas. |
| **Spadek wydajności przy dużych dokumentach** | Callback ostrzeżeń wywoływany tysiące razy. | Grupuj ostrzeżenia: zbieraj je w liście i przetwarzaj po załadowaniu, lub filtruj tylko unikalne nazwy czcionek. |

Świadomość tych scenariuszy pomaga **obsługiwać brakujące czcionki** bez niespodzianek.

---

## Pełny działający przykład – wszystkie elementy razem

Poniżej znajduje się kompletny, gotowy do uruchomienia program, który demonstruje cały przepływ. Skopiuj i wklej do projektu konsolowego, dodaj pakiet NuGet Aspose.Words i będzie działał od razu.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.LoadOptions;

class FontWarningCallback : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        if (info.WarningType == WarningType.FontSubstitution)
        {
            Console.WriteLine($"⚠️ Font substitution: {info.Description}");
        }
    }
}

class Program
{
    static void Main()
    {
        // 1️⃣ Configure LoadOptions with our warning handler.
        var loadOptions = new LoadOptions
        {
            WarningCallback = new FontWarningCallback()
        };

        // 2️⃣ Path to the source DOCX.
        string sourcePath = Path.Combine(Environment.CurrentDirectory, "input.docx");

        // 3️⃣ Load the document – any missing fonts trigger our callback.
        Document doc = new Document(sourcePath, loadOptions);
        Console.WriteLine("✅ Document loaded.");

        // 4️⃣ Optional: Save as PDF to see the final appearance.
        string pdfPath = Path.Combine(Environment.CurrentDirectory, "output.pdf");
        doc.Save(pdfPath, SaveFormat.Pdf);
        Console.WriteLine($"📄 PDF saved to {pdfPath}");

        // 5️⃣ (Bonus) Set explicit fallback font for a known missing font.
        var fontSettings = new FontSettings();
        fontSettings.SubstitutionSettings.FontSubstitutionRules.AddSubstitutes(
            "GothicBold", new[] { "Calibri", "Arial" });
        doc.FontSettings = fontSettings;
        doc.Save("output-with-fallback.pdf", SaveFormat.Pdf);
        Console.WriteLine("🔄 PDF with explicit fallback saved.");
    }
}
```

**Uruchomienie tego programu** spowoduje:

1. Wypisanie wszelkich ostrzeżeń o podstawieniu czcionek na konsolę.  
2. Zapisanie oryginalnego układu jako `output.pdf`.  
3. Zapisanie drugiego PDF (`output-with-fallback.pdf`), który wymusza zapas na *Calibri* lub *Arial*.

---

## Najczęściej zadawane pytania (FAQ)

**P: Czy to działa dla plików DOC, RTF lub HTML?**  
O: Tak. `LoadOptions` jest niezależny od formatu; pod warunkiem podania prawidłowej ścieżki pliku, callback ostrzeżeń zostanie wywołany dla brakujących czcionek we wszystkich obsługiwanych formatach.

**P: Czy mogę całkowicie wyciszyć ostrzeżenia?**  
O: Możesz przypisać pusty callback (`new IWarningCallback { Warning = _ => {} }`) lub ustawić `LoadOptions.WarningCallback = null`. Jednak utrata widoczności może spowodować, że przegapisz krytyczne problemy z czcionkami.

**P: Co zrobić, jeśli muszę zastąpić brakujące czcionki osadzonymi?**  
O: Użyj `FontSettings`, aby osadzić plik czcionki zastępczej (`AddFontSource`). Połącz to z regułami substytucji, aby uzyskać płynne doświadczenie.

**P: Czy callback jest bezpieczny wątkowo?**  
O: Callback może być wywoływany z wielu wątków przy równoległym ładowaniu dużych dokumentów. Upewnij się, że wszelkie współdzielone zasoby (np. pliki logów) są synchronizowane.

---

## Podsumowanie

Przeszliśmy przez **jak używać LoadOptions** w Aspose.Words, aby **elegancko obsługiwać brakujące czcionki**. Definiując własny `IWarningCallback`, podłączając go do obiektu `LoadOptions` i ładując dokument z tą konfiguracją, uzyskasz podgląd w czasie rzeczywistym na wszystkie zdarzenia podstawienia czcionek. Następnie możesz logować, zastępować lub osadzać czcionki zapasowe, aby wynik wyglądał dokładnie tak, jak zamierzasz.

Pamiętaj, że kluczowe kroki to:

1. Zaimplementuj callback ostrzeżeń, który koncentruje się na `WarningType.FontSubstitution`.
2. Podłącz callback do obiektu `LoadOptions`.
3. Załaduj dokument z tymi opcjami.
4. (Opcjonalnie) Zastosuj dodatkowe reguły substytucji czcionek lub logowanie w razie potrzeby.

Śmiało eksperymentuj — zamień logger konsoli na logger strukturalny, dodaj powiadomienia e‑mailowe o krytycznych brakujących czcionkach lub zintegrować ten wzorzec z większym potokiem przetwarzania dokumentów. Podejście skaluje się dobrze, niezależnie od tego, czy obsługujesz pojedynczy plik, czy przetwarzasz tysiące w trybie wsadowym.

Miłego kodowania i niech Twoje dokumenty zawsze renderują się z odpowiednimi krojami!

![przykład użycia loadoptions]

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}