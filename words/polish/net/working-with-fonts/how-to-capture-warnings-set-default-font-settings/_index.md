---
category: general
date: 2026-03-19
description: Dowiedz się, jak przechwytywać ostrzeżenia w Aspose.Words, ustawiać domyślne
  ustawienia czcionek oraz wykrywać brakujące czcionki podczas ładowania dokumentu
  Word.
draft: false
keywords:
- how to capture warnings
- set default font settings
- load word document
- detect missing fonts
- Aspose.Words warning callback
- font substitution handling
language: pl
og_description: Jak przechwycić ostrzeżenia w Aspose.Words, ustawić domyślne ustawienia
  czcionek i wykrywać brakujące czcionki podczas ładowania dokumentu Word.
og_title: Jak przechwytywać ostrzeżenia – Ustaw domyślne ustawienia czcionki
tags:
- Aspose.Words
- C#
- Document Processing
title: Jak przechwytywać ostrzeżenia – Ustaw domyślne ustawienia czcionki
url: /pl/net/working-with-fonts/how-to-capture-warnings-set-default-font-settings/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak przechwytywać ostrzeżenia – Ustaw domyślne ustawienia czcionki

**Jak przechwytywać ostrzeżenia** jest powszechną potrzebą podczas pracy z Aspose.Words, szczególnie jeśli Twoje dokumenty zależą od konkretnych czcionek, które mogą nie być dostępne na docelowym komputerze. Czy kiedykolwiek otworzyłeś plik DOCX i zastanawiałeś się, dlaczego układ wygląda nieprawidłowo? Odpowiedź często ukryta jest w ostrzeżeniu o brakującej czcionce.  

W tym przewodniku przeprowadzimy Cię przez **jak przechwytywać ostrzeżenia** podczas **ładowania dokumentu Word**, skonfigurujemy **ustaw domyślne ustawienia czcionki**, a na koniec **wykryjemy brakujące czcionki**, abyś mógł reagować programowo. Bez zbędnych wstępów — tylko kompletny, działający przykład oraz wyjaśnienie każdej linii.

> *Pro tip:* Wczesne przechwytywanie ostrzeżeń chroni Cię przed późniejszym debugowaniem tajemniczych problemów z układem.

---

## Czego będziesz potrzebować

- **Aspose.Words for .NET** (najnowsza wersja na 2026).  
- Środowisko programistyczne .NET (Visual Studio, Rider lub VS Code).  
- Przykładowy plik DOCX, który odwołuje się do czcionki, której *nie* masz zainstalowanej (np. *Comic Sans MS* na systemie Linux).  

To wszystko. Nie są wymagane dodatkowe pakiety NuGet poza Aspose.Words.

---

## Krok 1 – Zrozum, dlaczego musisz przechwytywać ostrzeżenia

Gdy Aspose.Words analizuje dokument, może napotkać czcionki, które nie są dostępne na hoście. Domyślnie biblioteka cicho zastępuje brakującą czcionkę czcionką awaryjną, co może zmienić podziały linii, odstępy i nawet spowodować zniknięcie tekstu.  

Użycie **WarningCallback** razem z obiektem **FontSettings** daje dwie korzyści:

1. **Widoczność** – otrzymujesz wpis `WarningInfo` dla każdej substytucji.  
2. **Kontrola** – możesz wstępnie skonfigurować domyślną czcionkę, aby zminimalizować nieprzewidziane zmiany wizualne.  

Pomyśl o tym jak o zainstalowaniu „strażnika”, który krzyczy za każdym razem, gdy silnik wymienia część pod maską.

---

## Krok 2 – Ustaw domyślne ustawienia czcionki

Pierwsze drugorzędne słowo kluczowe, **set default font settings**, pojawia się właśnie tutaj. Tworzysz instancję `FontSettings` i opcjonalnie wskazujesz folder zawierający Twoje czcionki awaryjne.

```csharp
using System;
using System.Collections.Generic;
using Aspose.Words;
using Aspose.Words.Fonts;

// Create a FontSettings object and point it to a folder with fallback fonts (optional)
var fontSettings = new FontSettings();
// Example: fontSettings.SetFontsFolder(@"C:\MyFallbackFonts", true);
```

> **Dlaczego?**  
> Jeśli nie określisz czcionki awaryjnej, Aspose.Words wybiera pierwszą czcionkę systemową pasującą do stylu, co może być zupełnie inne. Ustawiając znany domyślny font, zapewniasz spójne renderowanie na różnych maszynach.

---

## Krok 3 – Przygotuj Callback ostrzeżeń, aby przechwytywać ostrzeżenia

Teraz pokażemy **jak przechwytywać ostrzeżenia** poprzez dołączenie `WarningInfoCollection` do opcji ładowania. Ta kolekcja będzie przechowywać każde ostrzeżenie wygenerowane podczas procesu ładowania.

```csharp
// Step 3: Prepare a list that will collect warning information
var warningInfos = new List<WarningInfo>();

// Create a WarningInfoCollection that forwards warnings to our list
var warningCallback = new WarningInfoCollection(warningInfos);
```

`WarningInfoCollection` implementuje `IWarningCallback`, więc Aspose.Words automatycznie przekazuje każde ostrzeżenie do `warningInfos`. Nie ma potrzeby odpytywania.

---

## Krok 4 – Ładuj dokument Word z skonfigurowanymi opcjami

Tutaj drugie drugorzędne słowo kluczowe, **load word document**, wchodzi w grę. Przekazujemy zarówno `FontSettings`, jak i `WarningCallback` poprzez instancję `LoadOptions`.

```csharp
// Step 4: Build LoadOptions with our font settings and warning callback
var loadOptions = new LoadOptions
{
    FontSettings = fontSettings,
    WarningCallback = warningCallback
};

// Load the DOCX – this is the moment we actually **load word document**
Document doc = new Document("YOUR_DIRECTORY/MissingFont.docx", loadOptions);
```

Jeśli dokument odwołuje się do czcionki, która nie jest zainstalowana, callback ostrzeżeń przechwyci wpis `WarningType.FontSubstitution`.

---

## Krok 5 – Wykryj brakujące czcionki z zebranych ostrzeżeń

Na koniec odpowiadamy na trzecie drugorzędne słowo kluczowe, **detect missing fonts**, iterując po zebranych ostrzeżeniach.

```csharp
// Step 5: Examine the collected warnings for any font substitution events
foreach (var warning in warningInfos)
{
    if (warning.WarningType == WarningType.FontSubstitution)
    {
        Console.WriteLine($"⚠️ Font substitution detected: {warning.Description}");
    }
}
```

Typowy wynik wygląda tak:

```
⚠️ Font substitution detected: Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
```

Ten wiersz informuje dokładnie, której czcionki brakuje i jaka czcionka awaryjna została użyta — informacje, które możesz zalogować, wyświetlić użytkownikowi lub nawet uruchomić własną procedurę instalacji czcionki.

---

## Pełny, działający przykład

Poniżej znajduje się pełny program, który możesz skopiować i wkleić do aplikacji konsolowej. Demonstruje **jak przechwytywać ostrzeżenia**, **ustawić domyślne ustawienia czcionki**, **ładować dokument Word** oraz **wykrywać brakujące czcionki** w jednym przepływie.

```csharp
using System;
using System.Collections.Generic;
using Aspose.Words;
using Aspose.Words.Fonts;

namespace CaptureWarningsDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Prepare a list to collect warning information during loading
            var warningInfos = new List<WarningInfo>();

            // 2️⃣ Configure load options – this is where we **set default font settings**
            var fontSettings = new FontSettings();
            // Uncomment and adjust the line below if you have a fallback folder:
            // fontSettings.SetFontsFolder(@"C:\MyFallbackFonts", true);

            var loadOptions = new LoadOptions
            {
                FontSettings = fontSettings,
                WarningCallback = new WarningInfoCollection(warningInfos)
            };

            // 3️⃣ **Load word document** with the configured options
            string docPath = @"YOUR_DIRECTORY/MissingFont.docx";
            Document document = new Document(docPath, loadOptions);

            // 4️⃣ **Detect missing fonts** by scanning the collected warnings
            Console.WriteLine("Scanning for font substitution warnings...");
            foreach (var warning in warningInfos)
            {
                if (warning.WarningType == WarningType.FontSubstitution)
                {
                    Console.WriteLine($"⚠️ {warning.Description}");
                }
            }

            // Optional: keep console window open
            Console.WriteLine("Done. Press any key to exit.");
            Console.ReadKey();
        }
    }
}
```

**Oczekiwany wynik:** Gdy wskazany DOCX odwołuje się do czcionki, której nie ma zainstalowanej, konsola wypisuje ostrzeżenie dla każdej substytucji. Jeśli wszystkie czcionki są dostępne, pętla nie generuje żadnego wyjścia.

---

## Częste pułapki i przypadki brzegowe

| Sytuacja | Dlaczego się dzieje | Jak sobie radzić |
|-----------|----------------|------------------|
| **Brak ostrzeżeń** mimo że układ wygląda nieprawidłowo | Dokument może używać czcionek *osadzonych*, które Aspose.Words renderuje bez substytucji. | Sprawdź `Document.HasEmbeddedFonts` i rozważ wyodrębnienie osadzonych czcionek, jeśli potrzebujesz ich na innym komputerze. |
| **Wiele ostrzeżeń dla |  |  |

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}