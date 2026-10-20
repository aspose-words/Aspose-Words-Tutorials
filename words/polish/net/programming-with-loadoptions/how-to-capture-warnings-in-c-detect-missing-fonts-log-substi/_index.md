---
category: general
date: 2026-04-04
description: Dowiedz się, jak przechwytywać ostrzeżenia, wykrywać brakujące czcionki
  oraz rejestrować zdarzenia podstawiania przy użyciu Aspose.Words LoadOptions w języku
  C#.
draft: false
keywords:
- how to capture warnings
- detect missing fonts
- how to log substitution
- Aspose.Words warning handling
- font substitution monitoring
language: pl
og_description: Jak przechwytywać ostrzeżenia, wykrywać brakujące czcionki oraz rejestrować
  zdarzenia podstawiania przy użyciu Aspose.Words LoadOptions w języku C#.
og_title: Jak przechwytywać ostrzeżenia w C# – wykrywać brakujące czcionki i logować
  podstawienia
tags:
- C#
- Aspose.Words
- Document Loading
- Font Management
title: Jak przechwycić ostrzeżenia w C# – wykrywać brakujące czcionki i logować podstawienia
url: /pl/net/programming-with-loadoptions/how-to-capture-warnings-in-c-detect-missing-fonts-log-substi/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak przechwytywać ostrzeżenia w C# – wykrywać brakujące czcionki i rejestrować podstawienia

Zastanawiałeś się kiedyś **jak przechwytywać ostrzeżenia**, które pojawiają się podczas ładowania dokumentu Word z brakującymi czcionkami? Nie jesteś sam. W wielu rzeczywistych projektach czcionki gubią się podczas migracji, a ciche podstawienie może zepsuć układ. Dobra wiadomość? Aspose.Words oferuje czysty sposób na nasłuchiwanie tych ostrzeżeń, wykrywanie brakujących czcionek i nawet logowanie każdego podstawienia, aby później móc naprawić źródło.

W tym samouczku przeprowadzimy Cię przez kompletną, gotową do uruchomienia rozwiązanie, które pokazuje **jak przechwytywać ostrzeżenia**, demonstruje **wykrywanie brakujących czcionek** oraz wyjaśnia **jak rejestrować zdarzenia podstawień**. Po zakończeniu będziesz mieć wielokrotnego użytku handler ostrzeżeń, w pełni skonfigurowany obiekt `LoadOptions` oraz przykładowy wynik konsoli, który możesz zweryfikować.

> **Wymaganie wstępne:** Potrzebujesz Aspose.Words for .NET (v24.x lub nowszy) zainstalowanego przez NuGet oraz podstawowego środowiska programistycznego C# (Visual Studio 2022 lub VS Code będą w porządku).

---

## Jak przechwytywać ostrzeżenia podczas ładowania dokumentów

Sednem rozwiązania jest klasa implementująca `IWarningCallback`. Aspose.Words wywołuje ten callback automatycznie dla każdego ostrzeżenia wygenerowanego podczas ładowania dokumentu, w tym ostrzeżeń o podstawieniu czcionki.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Warning;

/// <summary>
/// Handles warning callbacks from Aspose.Words.
/// </summary>
class FontWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // We're only interested in font‑substitution warnings.
        if (info.Type == WarningType.FontSubstitution)
        {
            // This line prints the warning to the console.
            Console.WriteLine($"Font substitution detected: {info.Description}");
        }
    }
}
```

> **Dlaczego ten krok?**  
> Filtrując po `WarningType.FontSubstitution` unikamy bałaganu spowodowanego niepowiązanymi ostrzeżeniami (np. przestarzałe funkcje). Dzięki temu log jest skoncentrowany na dokładnym problemie, którym się interesujesz — brakujących czcionkach.

---

## Wykrywanie brakujących czcionek z Aspose.Words

Gdy dokument odwołuje się do czcionki, której nie ma zainstalowanej w systemie, Aspose.Words podstawia najbliższą pasującą czcionkę i podnosi ostrzeżenie. Nasz handler powyżej przechwyci każde wystąpienie, skutecznie **wykrywając brakujące czcionki**.

Aby zobaczyć to w praktyce, musimy skonfigurować `LoadOptions` i podłączyć handler:

```csharp
// Configure load options and attach the warning callback.
var loadOptions = new LoadOptions
{
    WarningCallback = new FontWarningHandler()
};
```

> **Wskazówka:** Jeśli wolisz zbierać ostrzeżenia do późniejszej obróbki (np. zapisać do pliku), zamień `Console.WriteLine` na kod, który doda wiadomość do `List<string>`.

---

## Jak rejestrować zdarzenia podstawień

Logowanie jest tak proste, jak skierowanie wyjścia ostrzeżenia do trwałego magazynu. Poniżej szybki przykład, który zapisuje każde ostrzeżenie o podstawieniu do pliku tekstowego o nazwie `font-warnings.log`.

```csharp
using System.IO;

class FileLoggingWarningHandler : IWarningCallback
{
    private readonly string _logPath = "font-warnings.log";

    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
        {
            string message = $"[{DateTime.Now}] Font substitution: {info.Description}";
            // Append the message to the log file.
            File.AppendAllText(_logPath, message + Environment.NewLine);
        }
    }
}

// Later, when creating LoadOptions:
var loadOptions = new LoadOptions
{
    WarningCallback = new FileLoggingWarningHandler()
};
```

> **Dlaczego logować do pliku?**  
> Trwałe logi pozwalają audytować problemy z czcionkami w wielu uruchomieniach, automatyzować alerty lub przekazywać dane do kontroli w pipeline’ie budowania.

---

## Pełny działający przykład

Łącząc wszystko razem, oto samodzielna aplikacja konsolowa, którą możesz skopiować, wkleić i uruchomić. Demonstracja **przechwytywania ostrzeżeń**, **wykrywania brakujących czcionek** oraz **logowania podstawień** w jednym miejscu.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Warning;

class FontWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
        {
            Console.WriteLine($"Font substitution: {info.Description}");
        }
    }
}

class FileLoggingWarningHandler : IWarningCallback
{
    private readonly string _logPath = "font-warnings.log";

    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
        {
            string message = $"[{DateTime.Now}] Font substitution: {info.Description}";
            File.AppendAllText(_logPath, message + Environment.NewLine);
        }
    }
}

class Program
{
    static void Main()
    {
        // Choose which handler you want:
        // var handler = new FontWarningHandler();          // console output
        var handler = new FileLoggingWarningHandler();    // file logging

        var loadOptions = new LoadOptions
        {
            WarningCallback = handler
        };

        // Path to the document that may contain missing fonts.
        string docPath = Path.Combine(Environment.CurrentDirectory, "input.docx");

        try
        {
            // Load the document – warnings are raised automatically.
            Document doc = new Document(docPath, loadOptions);
            Console.WriteLine("Document loaded successfully.");
        }
        catch (Exception ex)
        {
            Console.WriteLine($"Failed to load document: {ex.Message}");
        }

        // If you used the file logger, show where the log lives.
        if (handler is FileLoggingWarningHandler)
        {
            Console.WriteLine($"Font warnings have been written to 'font-warnings.log'.");
        }
    }
}
```

### Oczekiwany wynik w konsoli

Jeśli `input.docx` odwołuje się do czcionki, której nie ma zainstalowanej, zobaczysz coś w stylu:

```
Font substitution: Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
Document loaded successfully.
```

Jeśli przełączysz się na `FileLoggingWarningHandler`, te same linie pojawią się w pliku `font-warnings.log` wraz ze znacznikami czasu.

![how to capture warnings console output](image-placeholder.png)

---

## Częste pytania i przypadki brzegowe

### Co zrobić, jeśli chcę przechwytywać *wszystkie* ostrzeżenia, a nie tylko podstawienia czcionek?

Po prostu usuń warunek `if (info.Type == WarningType.FontSubstitution)`. Callback otrzyma każdy typ ostrzeżenia (`WarningType.DegradedDocument`, `WarningType.UnexpectedContent` itd.). Następnie możesz rozgałęziać się na podstawie `info.Type`, aby obsłużyć każdy przypadek osobno.

### Czy to działa z PDF‑ami, czy tylko z dokumentami Word?

`LoadOptions` i `IWarningCallback` są częścią Aspose.Words, więc dotyczą formatów kompatybilnych z Wordem (`.docx`, `.doc`, `.rtf`, `.html`). Dla PDF‑ów używa się własnych mechanizmów ostrzeżeń Aspose.PDF.

### Jak mogę zamiast logowania po prostu wyciszyć ostrzeżenia?

Ustaw `LoadOptions.WarningCallback = null` lub zaimplementuj callback, ale pozostaw ciało metody puste. Biblioteka nadal wykona podstawienie, ale nie wyświetli ostrzeżeń.

### A co z bezpieczeństwem wątkowym?

Instancja callbacku jest wywoływana w tym samym wątku, w którym ładowany jest dokument, więc nie potrzebujesz dodatkowej synchronizacji, chyba że współdzielisz handler pomiędzy równoległymi ładowaniami. W takim wypadku zabezpiecz współdzielone zasoby (np. plik logu) przy pomocy locka lub użyj kolekcji współbieżnych.

---

## Zakończenie

Omówiliśmy **jak przechwytywać ostrzeżenia** z Aspose.Words, pokazaliśmy **wykrywanie brakujących czcionek** oraz wyjaśniliśmy **logowanie zdarzeń podstawień** do późniejszej analizy. Podłączając prostą implementację `IWarningCallback` do `LoadOptions`, zyskujesz pełną widoczność problemów związanych z czcionkami, nie zaśmiecając kodu.

Co dalej? Spróbuj rozbudować logger, aby wysyłał e‑maile, integrował się z Azure Monitor lub automatycznie instalował brakujące czcionki na serwerze buildów. Możesz także zbadać inne typy ostrzeżeń — `WarningType.DegradedDocument` może ostrzegać o funkcjach, które nie przetrwały konwersji.

Masz więcej pytań o obsługę czcionek lub Aspose.Words? Zostaw komentarz lub otwórz nowe zgłoszenie na forum Aspose. Miłego kodowania i niech Twoje dokumenty zawsze renderują się z właściwą czcionką!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}