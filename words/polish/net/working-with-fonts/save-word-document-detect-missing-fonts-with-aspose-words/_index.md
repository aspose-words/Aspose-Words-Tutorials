---
category: general
date: 2026-03-22
description: Zapisz dokument Word i wykryj brakujące czcionki przy użyciu Aspose.Words.
  Dowiedz się, jak śledzić brakujące czcionki i przechwytywać błędy czcionek w C#.
draft: false
keywords:
- save word document
- detect missing fonts
- track missing fonts
- capture font errors
language: pl
og_description: Zapisz dokument Word i wykryj brakujące czcionki w C#. Ten przewodnik
  pokazuje, jak śledzić brakujące czcionki i przechwytywać błędy czcionek za pomocą
  wywołania zwrotnego ostrzeżenia.
og_title: Zapisz dokument Word – wykryj brakujące czcionki za pomocą Aspose.Words
tags:
- Aspose.Words
- C#
- Document Processing
title: Zapisz dokument Word – wykryj brakujące czcionki za pomocą Aspose.Words
url: /pl/net/working-with-fonts/save-word-document-detect-missing-fonts-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Zapisz dokument Word – wykryj brakujące czcionki przy użyciu Aspose.Words

Czy kiedykolwiek potrzebowałeś **zapisz dokument Word**, ale nie byłeś pewien, czy niektóre czcionki w środku przetrwają tę podróż? Dzieje się to częściej niż myślisz, szczególnie gdy dokumenty przemieszczają się między maszynami z różnymi bibliotekami czcionek. Dobra wiadomość? Aspose.Words zapewnia wbudowany sposób na **wykrywanie brakujących czcionek** podczas **zapisywania dokumentu Word**, dzięki czemu możesz logować, ostrzegać lub nawet zamienić je przed wyświetleniem pliku u użytkownika.

W tym samouczku przeprowadzimy Cię przez kompletny, gotowy do uruchomienia przykład, który nie tylko zapisuje dokument Word, ale także **śledzi brakujące czcionki** i **rejestruje błędy czcionek** przy użyciu własnego obsługiwacza ostrzeżeń. Po zakończeniu dokładnie zrozumiesz, dlaczego wywołanie zwrotne ostrzeżeń ma znaczenie, jak je podłączyć i jak wygląda wyjście konsoli, gdy następuje zamiana czcionki. Bez zbędnych dodatków — po prostu kod, który możesz od razu wkleić do projektu .NET.

> **Wymagania wstępne**  
> • .NET 6 (lub dowolna nowsza wersja .NET Framework) zainstalowana  
> • Visual Studio 2022 lub ulubione IDE  
> • Licencjonowana kopia **Aspose.Words for .NET** (darmowa wersja próbna wystarczy do testów)  

Jeśli masz to wszystko, zaczynamy.

---

## Zapisz dokument Word i wykryj brakujące czcionki

Idea jest prosta: przed wywołaniem `Document.Save` przypisz obiekt implementujący `IWarningCallback` do `Document.WarningCallback`. Aspose.Words wywoła ten obiekt dla każdego ostrzeżenia, które napotka, w tym ostrzeżeń o **zamianie czcionki**, które pojawiają się, gdy dokument źródłowy odwołuje się do czcionki, której system nie może znaleźć.

```csharp
using Aspose.Words;
using Aspose.Words.Warning;

// Step 1: Create a warning handler that prints font substitution messages
class FontWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // Only react to font‑substitution warnings
        if (info.Type == WarningType.FontSubstitution)
        {
            Console.WriteLine($"Font substitution: {info.Description}");
        }
    }
}

// Step 2: Load a document that may contain missing fonts
Document document = new Document("YOUR_DIRECTORY/input.docx");

// Step 3: Register the warning handler with the document
document.WarningCallback = new FontWarningHandler();

// Step 4: Save the document; any font substitution warnings will be output to the console
document.Save("YOUR_DIRECTORY/output.docx");
```

**Co zobaczysz:**  
Jeśli `input.docx` odwołuje się do czcionki, której nie ma zainstalowanej, konsola wypisze coś w rodzaju:

```
Font substitution: Font "Comic Sans MS" was substituted with "Arial".
```

Ten wiersz informuje dokładnie, której czcionki brakowało i jaką czcionkę Aspose.Words użyło zamiast niej — idealne do **rejestrowania błędów czcionek** przed udostępnieniem pliku.

---

## Śledź brakujące czcionki przy użyciu wywołania zwrotnego ostrzeżeń (krok po kroku)

### 1️⃣ Zainstaluj Aspose.Words

Otwórz konsolę NuGet w swoim projekcie i uruchom:

```bash
dotnet add package Aspose.Words
```

Spowoduje to pobranie najnowszej stabilnej wersji (obecnie 24.10). Aktualizowanie biblioteki zapewnia dostęp do najnowszych możliwości **wykrywania brakujących czcionek** oraz poprawek błędów.

### 2️⃣ Zdefiniuj obsługiwacz ostrzeżeń

Dlaczego potrzebujemy osobnej klasy? Implementacja `IWarningCallback` pozwala scentralizować całą logikę ostrzeżeń w jednym miejscu. Możesz także logować do pliku, wysyłać telemetrykę lub rzucać wyjątek, jeśli brakująca czcionka jest krytycznym błędem w Twoim procesie.

```csharp
class FontWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // Filter only the warnings we care about
        if (info.Type == WarningType.FontSubstitution)
        {
            // Here we simply write to the console,
            // but you could replace this with any logging framework.
            Console.WriteLine($"Font substitution: {info.Description}");
        }
    }
}
```

> **Porada:** Jeśli musisz **śledzić brakujące czcionki** w wielu dokumentach, przechowuj komunikaty w `List<string>` wewnątrz obsługiwacza i udostępnij je później do raportowania.

### 3️⃣ Załaduj dokument źródłowy

Konstruktor `Document` może przyjąć ścieżkę do pliku, strumień lub nawet surowe bajty. W większości przypadków wskażesz na plik `.docx`, który otrzymałeś od użytkownika lub innego systemu.

```csharp
Document doc = new Document("YOUR_DIRECTORY/input.docx");
```

Jeśli plik jest duży, rozważ użycie `LoadOptions` z włączonym leniwym ładowaniem, co zmniejszy obciążenie pamięci.

### 4️⃣ Podłącz wywołanie zwrotne

Przypisz instancję do `doc.WarningCallback`. Od tego momentu każde ostrzeżenie (w tym zamiany czcionek) będzie przekazywane do Twojego obsługiwacza.

```csharp
doc.WarningCallback = new FontWarningHandler();
```

### 5️⃣ Zapisz dokument

Teraz możesz bezpiecznie wywołać `Save`. Obsługiwacz ostrzeżeń działa **synchronicznie** podczas operacji zapisu, więc wynik pojawi się od razu.

```csharp
doc.Save("YOUR_DIRECTORY/output.docx");
```

Jeśli wolisz zapisać do innego formatu (PDF, HTML itp.), ten sam mechanizm ostrzeżeń działa — Aspose.Words nadal zgłosi brakujące czcionki przed konwersją.

---

## Rejestruj błędy czcionek – typowe przypadki brzegowe

Podstawowy przepływ obejmuje większość scenariuszy, ale w rzeczywistych projektach można napotkać kilka trudności. Poniżej znajdziesz niektóre warianty i sposoby ich obsługi.

### Brakująca czcionka w nagłówku/stopce

Nagłówki i stopki są oddzielnymi węzłami, ale system ostrzeżeń traktuje je tak samo jak tekst w treści. Nie wymaga dodatkowego kodu; wywołanie zwrotne zostanie uruchomione także dla tych czcionek. Upewnij się tylko, że ładowany jest pełny dokument (domyślne zachowanie tak robi).

### Wielokrotne zamiany w jednym dokumencie

Jeśli dokument używa kilku nieznanych czcionek, obsługiwacz zostanie wywołany raz dla każdej zamiany. Aby nie zasypać konsoli, możesz odfiltrować duplikaty:

```csharp
class FontWarningHandler : IWarningCallback
{
    private readonly HashSet<string> _seen = new();

    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution && _seen.Add(info.Description))
        {
            Console.WriteLine($"Font substitution: {info.Description}");
        }
    }
}
```

### Zamiana ostrzeżeń w wyjątki

Czasami brakująca czcionka jest krytyczna. Rzuć wyjątek wewnątrz obsługiwacza, aby przerwać zapisywanie:

```csharp
if (info.Type == WarningType.FontSubstitution)
{
    throw new InvalidOperationException($"Missing font detected: {info.Description}");
}
```

Pamiętaj, aby otoczyć `doc.Save` blokiem `try/catch`, aby obsłużyć wyjątek w sposób kontrolowany.

---

## Zweryfikuj wynik – czego się spodziewać

Po zakończeniu zapisu otwórz `output.docx` w Microsoft Word (lub innym kompatybilnym przeglądarce). Powinieneś zobaczyć taką samą wizualną układkę jak w oryginale, ale zamienione czcionki będą widoczne jako zastępcze, które zaobserwowałeś w konsoli. Aby dodatkowo sprawdzić, możesz:

1. Otworzyć **Plik → Opcje → Zaawansowane → Pokaż zawartość dokumentu → Użyj jakości roboczej** – wymusi to wyświetlenie ukrytych zamian czcionek.
2. Skorzystać z dialogu **Zamień czcionki** w Wordzie (`Ctrl+Shift+F`), aby zobaczyć, które czcionki są faktycznie osadzone.

Jeśli wszystko się zgadza, udało Ci się **zapisz dokument Word** jednocześnie **wykrywając brakujące czcionki** i **rejestrując błędy czcionek**. 🎉

---

## Pełny działający przykład (gotowy do skopiowania)

Poniżej znajduje się cały program, który możesz wkleić do nowego projektu aplikacji konsolowej. Wystarczy podmienić `YOUR_DIRECTORY` na rzeczywistą ścieżkę folderu na Twoim komputerze.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Warning;

namespace FontWarningDemo
{
    // Step 1: Create a warning handler that prints font substitution messages
    class FontWarningHandler : IWarningCallback
    {
        public void Warning(WarningInfo info)
        {
            // Only handle font‑substitution warnings
            if (info.Type == WarningType.FontSubstitution)
            {
                Console.WriteLine($"Font substitution: {info.Description}");
            }
        }
    }

    class Program
    {
        static void Main(string[] args)
        {
            // Step 2: Load a document that may contain missing fonts
            Document document = new Document("YOUR_DIRECTORY/input.docx");

            // Step 3: Register the warning handler with the document
            document.WarningCallback = new FontWarningHandler();

            // Step 4: Save the document; any font substitution warnings will be output to the console
            document.Save("YOUR_DIRECTORY/output.docx");

            Console.WriteLine("Document saved successfully.");
        }
    }
}
```

**Oczekiwany wynik w konsoli** (przykład):

```
Font substitution: Font "Times New Roman" was substituted with "Arial".
Document saved successfully.
```

To cała historia — żadnych ukrytych kroków, żadnych zewnętrznych dokumentów, które trzeba ścigać.

---

## Podsumowanie

Właśnie pokazaliśmy, jak **zapisz dokument Word** jednocześnie aktywnie **wykrywać brakujące czcionki**, **śledzić brakujące czcionki** i **rejestrować błędy czcionek** przy użyciu wywołania zwrotnego ostrzeżeń Aspose.Words. Dzięki podłączeniu małej implementacji `IWarningCallback` zyskujesz pełną widoczność zamian czcionek w czasie zapisu, co daje możliwość logowania, zamiany lub przerwania procesu w razie potrzeby.  

Gotowy na kolejne wyzwanie? Spróbuj rozbudować obsługiwacz, aby zapisywał ostrzeżenia w ustrukturyzowanym formacie JSON, lub połącz go z Aspose.PDF, aby konwertować ten sam dokument przy zachowaniu informacji o czcionkach. Możesz także zbadać możliwość osadzania brakujących czcionek bezpośrednio w pliku wyjściowym — Aspose.Words obsługuje osadzanie czcionek poprzez `LoadOptions.FontSettings`.  

Wypróbuj, dostosuj kod do swojego pipeline’u i daj nam znać, jak to działa w Twoim środowisku. Szczęśliwego kodowania!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}