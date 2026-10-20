---
category: general
date: 2026-04-01
description: Włącz ostrzeżenia o czcionkach podczas ładowania dokumentów Word przy
  użyciu Aspose.Words. Dowiedz się, jak przechwytywać zdarzenia podstawiania czcionek
  za pomocą C# LoadOptions i ustawień czcionek.
draft: false
keywords:
- enable font warnings
- font substitution
- Aspose.Words
- LoadOptions
- C# document processing
- font settings
language: pl
og_description: Włącz ostrzeżenia o czcionkach podczas ładowania dokumentów Word przy
  użyciu Aspose.Words. Ten samouczek pokazuje, jak przechwycić zdarzenia podstawiania
  czcionek w C#.
og_title: Włącz ostrzeżenia o czcionkach w Aspose.Words – Kompletny przewodnik C#
tags:
- Aspose.Words
- C#
- Font Management
title: Włącz ostrzeżenia dotyczące czcionek w Aspose.Words – Kompletny przewodnik
  C#
url: /pl/net/working-with-fonts/enable-font-warnings-in-aspose-words-complete-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Włącz ostrzeżenia o czcionkach w Aspose.Words – Kompletny przewodnik C#  

Zastanawiałeś się kiedyś, dlaczego dokument Word nagle wygląda inaczej po załadowaniu go programowo? **Włącz ostrzeżenia o czcionkach** i od razu dowiesz się, kiedy Aspose.Words zamienia brakującą czcionkę na zastępczą. W tym samouczku przeprowadzimy praktyczny przykład, który nie tylko przechwytuje te zamiany, ale także wyjaśnia *dlaczego* się odbywają.  

Omówimy wszystko, co potrzebne, aby rozpocząć: wymaganą paczkę NuGet, dokładną konfigurację `LoadOptions` oraz przejrzysty wynik w konsoli, który informuje, które czcionki zostały zastąpione. Po zakończeniu będziesz mieć solidny, wielokrotnego użytku wzorzec dla **przetwarzania dokumentów w C#**, który działa z dowolną wersją Aspose.Words.  

## Czego się nauczysz

- Jak utworzyć instancję `LoadOptions`, która śledzi zmiany czcionek.  
- Cel zdarzenia `SubstitutionWarning` i jak je podłączyć.  
- Pełny, uruchamialny przykład kodu, który wypisuje czytelne ostrzeżenia w konsoli.  
- Wskazówki dotyczące obsługi przypadków brzegowych, takich jak dokumenty zawierające wyłącznie standardowe czcionki.  

Nie wymagana jest wcześniejsza znajomość Aspose.Words — wystarczy podstawowa znajomość C# i .NET.  

---  

![diagram włączania ostrzeżeń o czcionkach pokazujący przepływ zdarzeń, gdy brakująca czcionka jest zastępowana](placeholder-image.png "Diagram włączania ostrzeżeń o czcionkach")  

## Krok 1: Skonfiguruj LoadOptions i włącz ostrzeżenia o czcionkach

Pierwszą rzeczą, której potrzebujesz, jest obiekt `LoadOptions`. Ten kontener informuje Aspose.Words, jak traktować plik, który zamierzasz załadować. Przypisując nową instancję `FontSettings`, otwierasz drzwi do zdarzeń związanych z czcionkami.  

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// Step 1: Prepare load options and enable font substitution warnings
LoadOptions loadOptions = new LoadOptions
{
    // Attach a new FontSettings object – this is where warnings are emitted.
    FontSettings = new FontSettings()
};
```  

**Dlaczego to ważne:**  
Jeśli pominiesz przypisanie `FontSettings`, Aspose.Words nadal będzie zastępował brakujące czcionki, ale nie otrzymasz żadnego powiadomienia. Mechanizm ostrzeżeń znajduje się wewnątrz `FontSettings`, więc jego inicjalizacja jest *kluczowa* dla naszego celu.  

> **Porada:** Możesz także skierować `FontSettings` na własny folder czcionek za pomocą `SetFontsFolder`. Zmniejszy to liczbę wyświetlanych ostrzeżeń, ponieważ Aspose.Words będzie w stanie znaleźć brakujące kroje.  

## Krok 2: Subskrybuj zdarzenie SubstitutionWarning (zastąpienie czcionki)

Teraz, gdy obiekt `FontSettings` istnieje, podłączamy się do jego zdarzenia `SubstitutionWarning`. To zdarzenie wyzwala się **za każdym razem**, gdy Aspose.Words zamienia żądaną czcionkę na inną.  

```csharp
// Step 2: Subscribe to the SubstitutionWarning event to be notified when a font is replaced
loadOptions.FontSettings.SubstitutionWarning += (sender, e) =>
{
    // e.FontName – the name that the document asked for
    // e.SubstitutedFontName – the font that Aspose.Words actually used
    Console.WriteLine($"[Warning] Font \"{e.FontName}\" was substituted with \"{e.SubstitutedFontName}\".");
};
```  

**Dlaczego to ważne:**  
Bez tego nasłuchiwacza nie będziesz mieć wglądu w proces zamiany. Linia w konsoli zapewnia szybki ślad audytu, co jest szczególnie przydatne podczas automatycznych kompilacji lub generowania PDF-ów dla branż o wysokich wymaganiach zgodności.  

> **Częste pytanie:** *Co jeśli chcę wyłączyć ostrzeżenia?*  
> Możesz po prostu odłączyć obsługę lub ustawić `FontSettings.SubstitutionWarning += null;`. Jednak zachowanie ostrzeżeń jest zazwyczaj najbezpieczniejszą drogą, ponieważ ciche zamiany mogą prowadzić do problemów z układem.  

## Krok 3: Załaduj dokument z skonfigurowanymi opcjami (przetwarzanie dokumentów w C#)

Gdy system ostrzeżeń jest gotowy, ładowanie dokumentu jest proste. Przekaż instancję `LoadOptions` do konstruktora `Document`, a Aspose.Words zajmie się resztą.  

```csharp
// Step 3: Load the document using the configured options
string filePath = @"C:\Docs\DocumentWithMissingFont.docx";

Document doc = new Document(filePath, loadOptions);

// Optional: Save to PDF to see the visual impact of the substitution
doc.Save(@"C:\Docs\Output.pdf");
```  

**Dlaczego to ważne:**  
Obiekt `LoadOptions` jest mostem między surowym plikiem a infrastrukturą ostrzeżeń. Jeśli go pominiesz, dokument zostanie załadowany cicho, a wszystkie brakujące czcionki zostaną zamienione bez śladu.  

> **Przypadek brzegowy:** Niektóre dokumenty zawierają wbudowane dokładne pliki czcionek, których potrzebują. W takim scenariuszu nie pojawi się żadne ostrzeżenie, ponieważ Aspose.Words znajdzie wbudowaną czcionkę. Powyższy kod nadal działa; po prostu zobaczysz pusty wynik w konsoli.  

## Krok 4: Zweryfikuj wynik i typowe pułapki

Uruchom program z wiersza poleceń lub debuggera w IDE. Jeśli dokument źródłowy zawiera czcionkę, która nie jest zainstalowana na komputerze (lub nie jest dostępna w niestandardowym folderze czcionek), zobaczysz linie takie jak:  

```
[Warning] Font "Comic Sans MS" was substituted with "Arial".
[Warning] Font "MyCustomFont" was substituted with "Times New Roman".
```  

Jeśli nic nie zostanie wypisane, to albo:  

1. Wszystkie czcionki zostały znalezione, **lub**  
2. Obsługa `SubstitutionWarning` nie została poprawnie podłączona (sprawdź ponownie Krok 2).  

### Dlaczego dochodzi do zamiany czcionek?

- **Brak systemowej czcionki:** System operacyjny nie posiada żądanego kroju.  
- **Nieobsługiwany format czcionki:** Aspose.Words potrafi odczytać TrueType i OpenType, ale nie każdy własnościowy format.  
- **Ograniczenia licencyjne:** Niektóre komercyjne czcionki blokują osadzanie, wymuszając użycie zastępczej.  

Zrozumienie *dlaczego* pomaga zdecydować, czy dostarczyć brakujące czcionki wraz z aplikacją, czy dostosować styl dokumentu.  

## Bonus: Kontrolowanie czcionki zastępczej

Jeśli chcesz, aby każda brakująca czcionka była zastępowana określoną rodziną (np. „Calibri”), możesz ustawić globalną regułę zamiany:  

```csharp
loadOptions.FontSettings.SubstitutionSettings.FontSubstitutes.AddSubstitutes(
    "AnyMissingFont", // wildcard – applies to any font not found
    new[] { "Calibri" } // the preferred substitute
);
```  

Teraz konsola nadal będzie Cię ostrzegać, ale efekt wizualny będzie spójny we wszystkich brakujących czcionkach.  

---  

## Podsumowanie

- **Włącz ostrzeżenia o czcionkach** tworząc `LoadOptions` z nowym `FontSettings`.  
- Podłącz zdarzenie `SubstitutionWarning`, aby otrzymywać alerty w czasie rzeczywistym, gdy czcionka zostanie zamieniona.  
- Załaduj dokument przy użyciu skonfigurowanych opcji i opcjonalnie zapisz jako PDF, aby zobaczyć efekt wizualny.  
- Zdiagnozuj, dlaczego doszło do zamiany i w razie potrzeby wymuś określoną czcionkę zastępczą.  

Właśnie dodałeś zabezpieczenie do swojego przepływu pracy **Aspose.Words**, które zapobiega cichym zmianom układu. Następnie możesz zbadać **ustawienia czcionek** takie jak `DefaultFontName` lub zagłębić się w opcje **renderowania dokumentu**, aby dopracować wyjście PDF.  

---  

### Co wypróbować dalej?

- **Zbadaj inne funkcje FontSettings**: `SetFontsFolder`, `LoadFontSources` i `DefaultFontName`.  
- **Połącz ostrzeżenia z frameworkami logowania** (Serilog, NLog) w celu uzyskania diagnostyki na poziomie produkcyjnym.  
- **Eksperymentuj z różnymi formatami dokumentów** (`.doc`, `.rtf`, `.html`), aby zobaczyć, jak każdy radzi sobie z brakującymi czcionkami.  

Masz pytania lub nietypowy scenariusz? zostaw komentarz poniżej i powodzenia w kodowaniu!  

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}