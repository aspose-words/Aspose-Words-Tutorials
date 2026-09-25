---
category: general
date: 2026-02-26
description: Obsłuż brakujące czcionki w C# przy użyciu Aspose.Words. Dowiedz się,
  jak przechwytywać ostrzeżenia o substytucji czcionek, zaimplementować IWarningCallback
  i utrzymać dokumenty w odpowiednim wyglądzie.
draft: false
keywords:
- handle missing fonts
- Aspose.Words font warning
- C# LoadOptions
- IWarningCallback implementation
- document loading with missing fonts
- font substitution handling
language: pl
og_description: Szybko obsłuż brakujące czcionki w C#. Ten przewodnik pokazuje, jak
  przechwycić ostrzeżenia o zamianie czcionek przy użyciu Aspose.Words, zaimplementować
  IWarningCallback i zweryfikować wyniki.
og_title: Obsługa brakujących czcionek w C# – krok po kroku poradnik Aspose.Words
tags:
- Aspose.Words
- C#
- Document Processing
title: Obsługa brakujących czcionek w C# z Aspose.Words – Kompletny przewodnik
url: /pl/net/working-with-fonts/handle-missing-fonts-in-c-with-aspose-words-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Obsługa brakujących czcionek w C# przy użyciu Aspose.Words – Kompletny przewodnik

Czy kiedykolwiek musiałeś **obsługiwać brakujące czcionki** podczas ładowania dokumentu Word w C# i zastanawiałeś się, dlaczego wynik wygląda dziwnie? Nie jesteś jedyny. Gdy plik źródłowy odwołuje się do czcionki, która nie jest zainstalowana na komputerze, Aspose.Words cicho podmienia inną, co może zepsuć układ lub identyfikację wizualną.  

Dobre wieści? Dzięki podłączeniu **callbacku ostrzeżeń** możesz przechwycić każde zdarzenie podmiany czcionki, zalogować je i zdecydować, czy dostarczyć zamiennik. W tym samouczku przeprowadzimy Cię przez cały proces — od konfiguracji projektu po weryfikację wyjścia w konsoli — abyś nigdy nie został zaskoczony niewidzialną czcionką.

> **Co otrzymasz**: Gotowa do uruchomienia aplikacja konsolowa C#, która raportuje każdą brakującą czcionkę, wyjaśnia, dlaczego pojawia się ostrzeżenie, i pokazuje, jak rozszerzyć obsługę o własną logikę.

---

## Wymagania wstępne

- .NET 6.0 lub nowszy (kod działa zarówno na .NET Core, jak i .NET Framework)
- Visual Studio 2022 (lub dowolnym IDE C#, które preferujesz)
- **Licencja** na Aspose.Words for .NET (bezpłatna wersja próbna wystarczy do testów)
- Dokument Word, który odwołuje się do czcionki niezainstalowanej na Twoim komputerze (np. *Comic Sans MS* na Linuxie)

Jeśli masz to wszystko, zanurzmy się.

---

## Krok 1: Utwórz nowy projekt konsolowy i dodaj Aspose.Words

Aby zachować porządek, rozpocznij od nowego projektu konsolowego.

```bash
dotnet new console -n FontWarningDemo
cd FontWarningDemo
dotnet add package Aspose.Words
```

> **Wskazówka**: Użyj flagi `--framework net6.0`, jeśli chcesz celować w konkretny runtime.

To pobiera najnowszy pakiet NuGet Aspose.Words, który zawiera typy `LoadOptions` i `IWarningCallback`, których będziemy potrzebować.

---

## Krok 2: Zaimplementuj obsługę ostrzeżeń (IWarningCallback)

Aspose.Words generuje obiekt `WarningInfo` dla każdego niekrytycznego problemu napotkanego podczas ładowania dokumentu. Implementując `IWarningCallback`, decydujesz, co zrobić z tymi ostrzeżeniami.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.LoadOptions;

public class FontWarningHandler : IWarningCallback
{
    // This method is called automatically by Aspose.Words whenever a warning occurs.
    public void Warning(WarningInfo info)
    {
        // We’re only interested in font‑substitution warnings.
        if (info.Type == WarningType.FontSubstitution)
        {
            // The Description property contains the name of the missing font and the substitute used.
            Console.WriteLine($"⚠️ Missing font detected: {info.Description}");
        }
        // You could also log other warning types here if you wish.
    }
}
```

**Dlaczego to ważne**: Bez obsługi ostrzeżeń o podmianie czcionki są cicho ignorowane. Wyświetlając je, uzyskasz natychmiastowy wgląd, które czcionki są brakujące i jaką czcionkę Aspose.Words użyło zamiast niej.

---

## Krok 3: Skonfiguruj LoadOptions z callbackiem ostrzeżeń

Teraz łączymy obsługę z procesem ładowania dokumentu. `LoadOptions` pozwala podłączyć callback przed parsowaniem pliku.

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;

class Program
{
    static void Main()
    {
        // 1️⃣ Tell Aspose.Words to use our FontWarningHandler.
        LoadOptions loadOptions = new LoadOptions
        {
            WarningCallback = new FontWarningHandler()
        };

        // 2️⃣ Path to the Word file that contains missing fonts.
        string docPath = @"YOUR_DIRECTORY\DocumentWithMissingFont.docx";

        // 3️⃣ Load the document with the custom options.
        Document doc = new Document(docPath, loadOptions);

        // At this point, any font‑substitution warning has already been printed.
        Console.WriteLine("✅ Document loaded successfully.");
    }
}
```

> **Uwaga**: Zastąp `YOUR_DIRECTORY` rzeczywistym folderem zawierającym Twój testowy plik `.docx`. Instancja `LoadOptions` musi być przekazana do konstruktora `Document`; w przeciwnym razie włączone zostanie domyślne ciche zachowanie.

---

## Krok 4: Uruchom aplikację i zweryfikuj wyjście

Skompiluj i uruchom:

```bash
dotnet run
```

Jeśli dokument odwołuje się do czcionki, której nie masz na komputerze (np. *Papyrus*), zobaczysz coś takiego:

```
⚠️ Missing font detected: The font 'Papyrus' was not found. Using 'Times New Roman' as a substitute.
✅ Document loaded successfully.
```

Ta pojedyncza linia dokładnie informuje, której czcionki brakuje i jaką czcionkę zastępczą wybrało Aspose.Words. Teraz możesz zdecydować, czy osadzić brakującą czcionkę, zmienić dokument źródłowy, czy zaakceptować podmianę.

---

## Krok 5: Zaawansowane – Zbieranie ostrzeżeń do późniejszego użycia

Czasami chcesz przechowywać ostrzeżenia zamiast od razu je wyświetlać. Poniżej szybka modyfikacja obsługi, która zbiera komunikaty w liście.

```csharp
using System.Collections.Generic;

public class FontWarningCollector : IWarningCallback
{
    public List<string> Messages { get; } = new();

    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
        {
            string msg = $"Missing font: {info.Description}";
            Messages.Add(msg);
        }
    }
}
```

I zaktualizuj `Main` odpowiednio:

```csharp
static void Main()
{
    var collector = new FontWarningCollector();

    LoadOptions lo = new LoadOptions { WarningCallback = collector };
    Document doc = new Document(@"YOUR_DIRECTORY\DocumentWithMissingFont.docx", lo);

    Console.WriteLine("✅ Document loaded.");
    if (collector.Messages.Count > 0)
    {
        Console.WriteLine("\n--- Font Substitution Report ---");
        foreach (var m in collector.Messages)
            Console.WriteLine(m);
    }
}
```

Teraz masz wielokrotnego użytku listę, którą możesz zapisać do pliku logu, wysłać do usługi monitorującej lub wyświetlić w interfejsie użytkownika.

---

## Krok 6: Typowe pułapki i jak ich unikać

| Problem | Dlaczego się pojawia | Rozwiązanie |
|-------|----------------|-----|
| **Brak ostrzeżeń** | Callback nie został podłączony lub dokument został załadowany bez `LoadOptions`. | Upewnij się, że `LoadOptions.WarningCallback` jest ustawiony **przed** wywołaniem konstruktora `Document`. |
| **Nieprawidłowa nazwa czcionki w komunikacie** | Niektóre czcionki są osadzone w dokumencie; Aspose.Words raportuje *oryginalną* nazwę, a nie osadzoną. | Zweryfikuj odwołania do czcionek w pliku źródłowym; osadzenie czcionek eliminuje ostrzeżenie całkowicie. |
| **Wpływ na wydajność** | Zbieranie ostrzeżeń dla tysięcy dokumentów może zwiększyć obciążenie. | Używaj prostego `Console.WriteLine` do szybkiego debugowania; przełącz się na kolektor tylko wtedy, gdy potrzebujesz danych. |

---

## Podsumowanie wizualne

![Ilustracja obsługi brakujących czcionek pokazująca przepływ callbacku ostrzeżeń](/images/handle-missing-fonts.png "Diagram obsługi brakujących czcionek przy użyciu Aspose.Words")

*Diagram (tekst alternatywny zawiera główne słowo kluczowe) wizualizuje, jak callback ostrzeżeń przechwytuje zdarzenia podmiany czcionki podczas ładowania dokumentu.*

---

## Zakończenie

Teraz wiesz **jak obsługiwać brakujące czcionki** w C# przy użyciu Aspose.Words. Podłączając `IWarningCallback` do `LoadOptions`, uzyskasz pełną widoczność każdego zdarzenia podmiany czcionki, możesz je logować lub reagować na nie, i ostatecznie zapewnić, że generowane dokumenty zachowają zamierzony wygląd i styl.

> **Szybkie podsumowanie**:  
> 1. Dodaj Aspose.Words do aplikacji konsolowej.  
> 2. Zaimplementuj `FontWarningHandler` (lub kolektor).  
> 3. Przekaż go przez `LoadOptions` podczas ładowania dokumentu.  
> 4. Zweryfikuj wyjście w konsoli lub zapisane ostrzeżenia.  

Od tego momentu możesz zbadać **osadzanie brakujących czcionek** (`FontSettings.SubstitutionSettings`) lub **automatyczne pobieranie ich z firmowego serwera czcionek** — oba są naturalnymi rozszerzeniami wzorca, który właśnie zbudowaliśmy.

Masz więcej pytań dotyczących **ostrzeżeń czcionek Aspose.Words**, **C# LoadOptions** lub **ładowania dokumentów z brakującymi czcionkami**? Zostaw komentarz i powodzenia w kodowaniu!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}