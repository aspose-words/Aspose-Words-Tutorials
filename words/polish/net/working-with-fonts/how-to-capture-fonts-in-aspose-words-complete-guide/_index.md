---
category: general
date: 2026-01-05
description: Jak szybko przechwytywać czcionki i obsługiwać brakujące czcionki przy
  użyciu Aspose.Words. Poznaj rozwiązanie krok po kroku z pełnym kodem C#.
draft: false
keywords:
- how to capture fonts
- handle missing fonts
- Aspose.Words warnings
- font substitution callback
- missing font detection
language: pl
og_description: Jak przechwytywać czcionki w Aspose.Words i obsługiwać brakujące czcionki.
  Postępuj zgodnie z tym szczegółowym przewodnikiem, aby uzyskać niezawodną implementację
  w C#.
og_title: Jak przechwycić czcionki w Aspose.Words – pełny poradnik
tags:
- Aspose.Words
- C#
- Document Processing
title: Jak przechwycić czcionki w Aspose.Words – Kompletny przewodnik
url: /pl/net/working-with-fonts/how-to-capture-fonts-in-aspose-words-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak przechwycić czcionki w Aspose.Words – Kompletny przewodnik

Zastanawiałeś się kiedyś **jak przechwycić czcionki** podczas ładowania dokumentu Word przy użyciu Aspose.Words? Nie jesteś jedyny. Brakujące czcionki mogą powodować subtelne problemy z układem, a bez odpowiedniego ostrzeżenia możesz ich nie zauważyć, dopóki finalny PDF nie będzie wyglądał niepoprawnie. W tym tutorialu pokażemy dokładnie, jak **przechwycić czcionki** oraz obsłużyć brakujące czcionki, aby wynik pozostawał pixel‑perfect.

Przejdziemy przez realistyczny scenariusz, skonfigurujemy callback ostrzeżeń i podamy gotowy przykład w C#. Po zakończeniu będziesz wiedział, dlaczego to ważne, jak to zaimplementować i na co zwrócić uwagę, gdy czcionki znikają z Twojego środowiska.

## Czego się nauczysz

- Jak skonfigurować **LoadOptions**, aby nasłuchiwać ostrzeżeń związanych z czcionkami.  
- Rolę **IWarningCallback** i **WarningInfo** w Aspose.Words.  
- Praktyczne wskazówki dotyczące rozwiązywania problemów i logowania brakujących czcionek.  
- Kompletny, samodzielny fragment kodu, który możesz wkleić do Visual Studio i uruchomić od razu.

**Wymagania wstępne:** .NET 6+ (lub .NET Framework 4.7.2+), Aspose.Words for .NET zainstalowany przez NuGet oraz podstawowa znajomość C#. Nie są potrzebne inne biblioteki.

---

## Krok 1: Skonfiguruj LoadOptions, aby przechwycić czcionki

Pierwszą rzeczą, której potrzebujemy, jest instancja **LoadOptions**. Ten obiekt mówi Aspose.Words, jak zachowywać się podczas odczytu dokumentu. Przypisując własny **IWarningCallback**, możemy przechwycić wszelkie ostrzeżenia o podmianie czcionek, które wystąpią w trakcie ładowania.

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Loading;

// Prepare load options and attach a warning callback
LoadOptions loadOptions = new LoadOptions
{
    // The callback will be invoked for every warning Aspose.Words raises
    WarningCallback = new FontWarningCollector()
};
```

**Dlaczego to ważne:**  
Aspose.Words cicho podmienia brakujące czcionki na domyślną, chyba że poprosisz o informację. Podłączając callback, **przechwycisz informacje o czcionkach** już w momencie ładowania, co daje możliwość logowania, zamiany lub nawet przerwania operacji.

> **Pro tip:** Trzymaj `loadOptions` jako zmienną wielokrotnego użytku, jeśli przetwarzasz wiele dokumentów w partii. Unikniesz w ten sposób wielokrotnego tworzenia tego samego callbacku.

---

## Krok 2: Załaduj dokument z skonfigurowanymi opcjami

Gdy callback jest już gotowy, ładujemy dokument. Konstruktor **Document** przyjmuje ścieżkę oraz **LoadOptions**, które właśnie skonfigurowaliśmy.

```csharp
// Replace with the actual path to your .docx file
string inputPath = @"C:\Docs\input.docx";

Document doc = new Document(inputPath, loadOptions);
```

Jeśli jakaś czcionka będzie brakować, Aspose.Words wyemituje ostrzeżenie, które otrzyma nasz `FontWarningCollector`. Sam dokument i tak zostanie załadowany, ale będziesz mieć wyraźny zapis, które czcionki zostały podmienione.

---

## Krok 3: Implementacja FontWarningCollector – obsługa brakujących czcionek

Sednem **jak przechwycić czcionki** jest klasa `FontWarningCollector`. Implementuje ona `IWarningCallback` i filtruje wyłącznie zdarzenia `WarningType.FontSubstitution`.

```csharp
// Helper class that receives warning callbacks from Aspose.Words
class FontWarningCollector : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // We care exclusively about font substitution warnings
        if (info.Type == WarningType.FontSubstitution)
        {
            // Log the warning – you could also write to a file or database
            Console.WriteLine($"Font substitution detected: {info.Description}");
        }
    }
}
```

**Wyjaśnienie:**  
- `info.Type` informuje nas o kategorii ostrzeżenia. Sprawdzając, czy jest to `FontSubstitution`, **obsługujemy brakujące czcionki** bez zapełniania logu niepowiązanymi komunikatami (np. o przestarzałych funkcjach).  
- `info.Description` zawiera czytelną wiadomość, np. „Font 'Comic Sans MS' was substituted with 'Arial'.” – to dokładnie te dane, które potrzebujesz do audytu swojego zestawu czcionek.

> **Uwaga:** Jeśli chcesz przerwać przetwarzanie, gdy krytyczna czcionka jest nieobecna, wyrzuć wyjątek wewnątrz bloku `if` zamiast jedynie wypisywać komunikat.

---

## Krok 4: Zweryfikuj wynik – czego się spodziewać

Uruchom program z konsoli lub IDE. Dla każdej brakującej czcionki zobaczysz linię podobną do:

```
Font substitution detected: Font 'Times New Roman' was substituted with 'Arial'.
```

Jeśli wszystkie czcionki są dostępne, callback pozostaje cichy i dokument ładuje się bez incydentów. Teraz możesz bezpiecznie kontynuować zapisywanie, konwertowanie lub drukowanie dokumentu, mając pewność, że **przechwyciłeś informacje o czcionkach**.

---

## Krok 5: Pełny działający przykład (wszystkie elementy razem)

Poniżej kompletny, gotowy do skopiowania program. Zawiera dyrektywy `using`, implementację callbacku oraz krótką demonstrację zapisu załadowanego dokumentu jako PDF.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Loading;

namespace FontCaptureDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // 1️⃣ Configure load options with our warning collector
            LoadOptions loadOptions = new LoadOptions
            {
                WarningCallback = new FontWarningCollector()
            };

            // 2️⃣ Path to the source DOCX (adjust as needed)
            string inputPath = @"C:\Docs\input.docx";

            // 3️⃣ Load the document – any missing fonts trigger our callback
            Document doc = new Document(inputPath, loadOptions);

            // 4️⃣ Optional: Save as PDF to see the final result
            string outputPdf = @"C:\Docs\output.pdf";
            doc.Save(outputPdf);

            Console.WriteLine("Document processed successfully.");
        }
    }

    // 5️⃣ Our custom warning collector – handles missing fonts
    class FontWarningCollector : IWarningCallback
    {
        public void Warning(WarningInfo info)
        {
            if (info.Type == WarningType.FontSubstitution)
            {
                // You could log to a file, raise an event, or collect into a list
                Console.WriteLine($"Font substitution detected: {info.Description}");
            }
        }
    }
}
```

**Uruchamianie kodu:**  
1. Utwórz nowy projekt konsolowy (`dotnet new console -n FontCaptureDemo`).  
2. Dodaj pakiet Aspose.Words (`dotnet add package Aspose.Words`).  
3. Zamień wygenerowany `Program.cs` na powyższy fragment.  
4. Umieść DOCX, który celowo odwołuje się do czcionki, której nie masz (np. „Papyrus”).  
5. Uruchom (`dotnet run`). Obserwuj konsolę pod kątem komunikatów o podmianie, a następnie otwórz `output.pdf`, aby zweryfikować układ.

---

## Często zadawane pytania i przypadki brzegowe

### Co zrobić, jeśli później potrzebuję listy brakujących czcionek?

Przechowuj komunikaty w `List<string>` wewnątrz `FontWarningCollector` i udostępnij je przez właściwość. Dzięki temu możesz zapisać listę do pliku logu po przetworzeniu wielu dokumentów.

### Czy to działa z zaszyfrowanymi lub chronionymi hasłem plikami?

Tak, ale musisz również podać hasło poprzez `LoadOptions.Password`. Callback ostrzeżeń działa tak samo po odszyfrowaniu dokumentu.

### Czy mogę podmienić brakującą czcionkę własnym zamiennikiem?

Oczywiście. W metodzie `Warning` możesz wywołać `doc.FontSettings.SubstitutionSettings.FontSubstitutes.AddMissing("MissingFont", "MyFallback")`. Dzięki temu podmiana będzie deterministyczna.

### Czy to wpływa na wydajność?

Obciążenie jest minimalne – zasadniczo wywołanie metody przy każdym ostrzeżeniu. W partii tysięcy dokumentów wpływ jest pomijalny w porównaniu z kosztami I/O ładowania każdego pliku.

---

## Podsumowanie

Omówiliśmy **jak przechwycić czcionki** w Aspose.Words, pokazaliśmy, jak **obsługiwać brakujące czcionki** przy użyciu czystego callbacku ostrzeżeń oraz dostarczyliśmy pełny, gotowy do uruchomienia przykład. Wprowadzając ten wzorzec do swojego potoku przetwarzania dokumentów, nigdy nie zostaniesz zaskoczony cichą podmianą czcionek.

Gotowy na kolejny krok? Spróbuj rozbudować collector, aby zapisywał logi w formacie JSON, integrował się z panelem monitoringu lub automatycznie osadzał brakujące czcionki w wyjściowym PDF. Możliwości są nieograniczone, a Ty masz solidne podstawy.

Miłego kodowania! 🚀

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}