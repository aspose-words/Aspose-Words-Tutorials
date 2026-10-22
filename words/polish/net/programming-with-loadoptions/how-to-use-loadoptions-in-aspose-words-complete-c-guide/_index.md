---
category: general
date: 2026-04-10
description: Jak używać klasy LoadOptions w Aspose.Words, aby przechwytywać ostrzeżenia
  o podstawianiu czcionek podczas ładowania dokumentów. Poznaj krok po kroku rozwiązanie
  w C# z pełnym przykładem kodu.
draft: false
keywords:
- how to use loadoptions
- warningcallback
- font substitution warning
- aspose.words loadoptions example
- c# document loading
language: pl
og_description: Jak używać klasy LoadOptions w Aspose.Words, aby przechwytywać ostrzeżenia
  o podstawianiu czcionek podczas ładowania dokumentów. Ten przewodnik prowadzi Cię
  krok po kroku przez pełną implementację w C#.
og_title: Jak używać LoadOptions w Aspose.Words – Kompletny przewodnik C#
tags:
- Aspose.Words
- C#
- Document Processing
- Font Management
title: Jak używać LoadOptions w Aspose.Words – Kompletny przewodnik C#
url: /pl/net/programming-with-loadoptions/how-to-use-loadoptions-in-aspose-words-complete-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak używać LoadOptions w Aspose.Words – Kompletny przewodnik C#

Użycie LoadOptions w Aspose.Words jest powszechną przeszkodą, gdy potrzebna jest ścisła kontrola nad ładowaniem dokumentów. W tym samouczku pokażemy dokładnie **jak używać LoadOptions**, aby przechwycić ostrzeżenia o podstawianiu czcionek i zareagować na nie w C#.  

Jeśli kiedykolwiek otworzyłeś plik DOCX, który odwoływał się do brakującej czcionki i zastanawiałeś się, dlaczego wynik wygląda dziwnie, jesteś we właściwym miejscu. Przeprowadzimy Cię przez cały proces, od utworzenia instancji `LoadOptions` po wypisanie szczegółów ostrzeżeń w konsoli. Na koniec będziesz mieć gotowy fragment kodu, który możesz wkleić do dowolnego projektu .NET.

## Czego się nauczysz

- Dlaczego `LoadOptions` ma znaczenie dla niezawodnego importu dokumentów.  
- Jak podłączyć **WarningCallback**, który konkretnie monitoruje **ostrzeżenia o podstawianiu czcionek**.  
- Dokładny kod potrzebny do załadowania pliku Word z włączonymi tymi opcjami.  
- Wskazówki dotyczące obsługi przypadków brzegowych, takich jak dokumenty zawierające wiele brakujących czcionek.  

Nie potrzebujesz żadnej zewnętrznej dokumentacji — wszystko, czego potrzebujesz, znajduje się tutaj.

## Wymagania wstępne

| Wymaganie | Powód |
|-------------|--------|
| .NET 6.0 lub nowszy | Zapewnia środowisko uruchomieniowe dla składni C# 10 używanej w przykładach. |
| Aspose.Words for .NET (najnowsza wersja) | Biblioteka, która dostarcza `LoadOptions` oraz infrastrukturę ostrzeżeń. |
| Plik DOCX, który może odwoływać się do czcionek niezainstalowanych na komputerze | Aby zobaczyć działanie callbacku ostrzeżeń. |
| Visual Studio 2022 (lub dowolne inne IDE) | Ułatwia debugowanie i testowanie. |

Jeśli już masz te elementy, świetnie — zanurzmy się.

## Krok 1 – Utwórz obiekt LoadOptions i podłącz WarningCallback

Pierwszą rzeczą, którą robisz, gdy **jak używać LoadOptions**, jest jego zainicjowanie. Kluczowym elementem jest przypisanie delegata do `WarningCallback`. Delegat ten wywołuje się za każdym razem, gdy Aspose.Words napotka sytuację, o której chce Cię poinformować — najczęściej brakującą czcionkę.

```csharp
using System;
using Aspose.Words;

// Step 1: Build LoadOptions with a warning listener.
LoadOptions loadOptions = new LoadOptions
{
    // The lambda receives the sender (unused) and a WarningInfo object.
    WarningCallback = (sender, args) =>
    {
        // We'll filter for font‑substitution warnings later.
        if (args.WarningType == WarningType.FontSubstitution)
        {
            Console.WriteLine($"⚠️ Font substitution: {args.Description}");
        }
    }
};
```

**Dlaczego to ważne:** Bez callbacku Aspose.Words cicho zamienia brakujące czcionki na domyślne, i możesz nigdy nie zauważyć zmiany wizualnej. Rejestrując `WarningCallback`, otrzymujesz log w czasie rzeczywistym każdego podstawienia, co jest niezbędne w pipeline’ach dokumentów zapewniających jakość.

## Krok 2 – Reaguj tylko na ostrzeżenia o podstawianiu czcionek

Możesz się zastanawiać, czy callback nie zasypie Cię niepowiązanymi ostrzeżeniami (np. o przestarzałych funkcjach). Odpowiedź brzmi *tak* — ale możemy je odfiltrować. W powyższym fragmencie już sprawdzamy `args.WarningType == WarningType.FontSubstitution`. Ten wiersz jest **ochroną przed ostrzeżeniami o podstawianiu czcionek**, dodatkowym słowem kluczowym, które utrzymuje wyjście skoncentrowane.

Jeśli kiedykolwiek będziesz musiał obsłużyć inne typy ostrzeżeń, po prostu rozbuduj blok `if`:

```csharp
if (args.WarningType == WarningType.FontSubstitution)
{
    // Existing handling…
}
else if (args.WarningType == WarningType.UnknownFileFormat)
{
    Console.WriteLine($"❓ Unknown format: {args.Description}");
}
```

Ten wzorzec pokazuje, jak elastyczny jest mechanizm **warningcallback**, pozwalając dostosować reakcje dokładnie do scenariuszy, które Cię interesują.

## Krok 3 – Załaduj dokument przy użyciu skonfigurowanego LoadOptions

Teraz, gdy nasłuchiwacz jest gotowy, ostatnim elementem jest przekazanie instancji `LoadOptions` do konstruktora `Document`. To moment, w którym **przykład Aspose.Words LoadOptions** naprawdę błyszczy.

```csharp
// Step 3: Load the DOCX while the warning callback is active.
try
{
    Document doc = new Document("YOUR_DIRECTORY/input.docx", loadOptions);
    Console.WriteLine("✅ Document loaded successfully.");
}
catch (Exception ex)
{
    Console.WriteLine($"🚨 Failed to load document: {ex.Message}");
}
```

**Co zobaczysz:** Jeśli DOCX odwołuje się do czcionki, której nie ma na maszynie, konsola wyświetli wiersz podobny do:

```
⚠️ Font substitution: Font 'Calibri Light' has been substituted with 'Arial'.
✅ Document loaded successfully.
```

Ten wynik potwierdza, że **jak używać LoadOptions** do monitorowania problemów z czcionkami zakończyło się sukcesem.

## Pełny działający przykład (gotowy do kopiowania i wklejania)

Poniżej znajduje się kompletny program, który możesz od razu skompilować i uruchomić. Łączy wszystkie trzy kroki, dodaje kilka udogodnień (np. przyjazny baner) i demonstruje obsługę błędów.

```csharp
using System;
using Aspose.Words;

class Program
{
    static void Main()
    {
        Console.WriteLine("=== Aspose.Words LoadOptions Demo ===");

        // 1️⃣ Create LoadOptions with a warning callback.
        LoadOptions loadOptions = new LoadOptions
        {
            WarningCallback = (sender, args) =>
            {
                if (args.WarningType == WarningType.FontSubstitution)
                {
                    Console.WriteLine($"⚠️ Font substitution: {args.Description}");
                }
            }
        };

        // 2️⃣ Attempt to load the document.
        try
        {
            // Replace the path with your own file that may contain missing fonts.
            Document doc = new Document("YOUR_DIRECTORY/input.docx", loadOptions);
            Console.WriteLine("✅ Document loaded without fatal errors.");

            // Optional: Do something with the document, e.g., save as PDF.
            // doc.Save("output.pdf");
        }
        catch (Exception e)
        {
            Console.WriteLine($"🚨 Error: {e.Message}");
        }

        Console.WriteLine("=== End of Demo ===");
    }
}
```

### Oczekiwany wynik

Uruchomienie programu na maszynie, której brakuje czcionki odwoływanej w `input.docx`, daje coś podobnego do:

```
=== Aspose.Words LoadOptions Demo ===
⚠️ Font substitution: Font 'Times New Roman' has been substituted with 'Arial'.
✅ Document loaded without fatal errors.
=== End of Demo ===
```

Jeśli wszystkie czcionki są dostępne, zobaczysz jedynie komunikaty o sukcesie — żadne linie ostrzeżeń się nie pojawią.

## Częste pułapki i wskazówki profesjonalne

- **Pułapka:** Zapomnienie o ustawieniu `WarningCallback`. Kod i tak się załaduje, ale przegapisz szczegóły podstawień.  
  **Wskazówka:** Zawsze przypisuj callback od razu po utworzeniu `LoadOptions`; jest to tanie i zwraca się później.

- **Pułapka:** Użycie względnej ścieżki, która wskazuje na niewłaściwy folder.  
  **Wskazówka:** Użyj `Path.Combine(Environment.CurrentDirectory, "input.docx")` dla bardziej odpornego wyszukiwania pliku.

- **Pułapka:** Zakładanie, że ostrzeżenie zatrzyma ładowanie.  
  **Wskazówka:** Ostrzeżenia o podstawianiu czcionek są *informacyjne*; nie przerywają ładowania. Jeśli potrzebujesz surowszej walidacji, rzuć wyjątek wewnątrz callbacku, gdy wystąpi podstawienie.

- **Pułapka:** Uruchamianie na serwerze bez żadnych czcionek (np. minimalny obraz Docker).  
  **Wskazówka:** Wstępnie zainstaluj wymagane czcionki lub dołącz je do aplikacji, a następnie zweryfikuj za pomocą callbacku, że w produkcji nie dochodzi do podstawień.

## Kiedy używać LoadOptions vs. inspekcji po załadowaniu

Możesz zapytać: „Dlaczego nie po prostu sprawdzić dokument po jego załadowaniu?” Odpowiedź leży w wydajności i poprawności. Obsługując ostrzeżenia **podczas** ładowania, łapiesz problemy wcześnie — zanim nastąpią jakiekolwiek obliczenia układu czy konwersje do PDF. Jest to szczególnie cenne w potokach przetwarzania wsadowego, gdzie każdy dodatkowy krok kosztuje czas.

## Rozszerzenie przykładu: zapisywanie raportu wszystkich podstawionych czcionek

Jeśli potrzebujesz trwałego zapisu (być może ze względu na zgodność), zmodyfikuj callback, aby zbierał komunikaty w liście i zapisywał je do pliku po załadowaniu:

```csharp
var substitutions = new List<string>();

loadOptions.WarningCallback = (s, a) =>
{
    if (a.WarningType == WarningType.FontSubstitution)
    {
        substitutions.Add(a.Description);
        Console.WriteLine($"⚠️ {a.Description}");
    }
};

// After loading:
File.WriteAllLines("font-substitutions.txt", substitutions);
```

Teraz masz zarówno informacje zwrotne w konsoli, jak i trwały log.

## Powiązane tematy, które możesz zbadać dalej

- **Jak osadzić własne czcionki w Aspose.Words** – eliminuje całkowicie podstawianie.  
- **Używanie LoadOptions do ograniczenia rozmiaru dokumentu** – pomaga chronić przed złośliwie dużymi plikami.  
- **Konwertowanie Word do PDF z zachowaną typografią** – dobrze współgra z podejściem warning‑callback.  

Każdy z tych tematów buduje na fundamencie, który właśnie stworzyłeś przy pomocy `LoadOptions`.

## Podsumowanie

Omówiliśmy **jak używać LoadOptions** w Aspose.Words od początku do końca: tworzymy opcje, podłączamy `WarningCallback`, który koncentruje się na **ostrzeżeniach o podstawianiu czcionek**, i ładujemy dokument z pewnością. Pełny przykład działa od razu, a dodatkowe wskazówki pomagają uniknąć typowych pułapek.  

Śmiało eksperymentuj — zamień callback na inne typy ostrzeżeń, loguj do bazy danych lub włącz logikę do usługi sieciowej, która waliduje przesyłane pliki Word. Wzorzec jest elastyczny, niezawodny i, co najważniejsze, daje wgląd w ukryty proces podstawiania czcionek, który w przeciwnym razie mógłby popsuć renderowanie Twoich dokumentów.

Powodzenia w kodowaniu i niech Twoje dokumenty zawsze renderują się dokładnie tak, jak zamierzasz! 

![Diagram pokazujący przepływ użycia LoadOptions z callbackiem ostrzeżeń w Aspose.Words](https://example.com/images/loadoptions-flow.png "Diagram użycia LoadOptions")

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}