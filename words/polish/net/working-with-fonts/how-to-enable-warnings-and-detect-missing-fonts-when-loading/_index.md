---
category: general
date: 2026-02-21
description: Dowiedz się, jak włączyć ostrzeżenia, wykrywać brakujące czcionki oraz
  jak bezpiecznie ładować pliki docx przy użyciu Aspose.Words w C#. Postępuj zgodnie
  z przewodnikiem krok po kroku.
draft: false
keywords:
- how to enable warnings
- detect missing fonts
- how to load docx
- font substitution handling
- Aspose.Words warnings
language: pl
og_description: Jak włączyć ostrzeżenia, wykrywać brakujące czcionki i prawidłowo
  ładować pliki docx przy użyciu Aspose.Words. Pełny przykład kodu dołączony.
og_title: Jak włączyć ostrzeżenia i wykrywać brakujące czcionki podczas ładowania
  pliku DOCX
tags:
- C#
- Aspose.Words
- Document processing
title: Jak włączyć ostrzeżenia i wykrywać brakujące czcionki przy ładowaniu plików
  DOCX
url: /pl/net/working-with-fonts/how-to-enable-warnings-and-detect-missing-fonts-when-loading/
---

as is.

Now produce final content.

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak włączyć ostrzeżenia i wykrywać brakujące czcionki przy ładowaniu plików DOCX

Zastanawiałeś się kiedyś **jak włączyć ostrzeżenia** o brakujących czcionkach, zanim cicho zepsują renderowanie dokumentu? Nie jesteś sam — większość programistów zakłada, że biblioteka po prostu „zrobi to, co trzeba”, a potem odkrywają, że czcionka została zamieniona bez żadnej wskazówki.  

W tym poradniku pokażemy Ci dokładnie **jak włączyć ostrzeżenia**, jak **wykrywać brakujące czcionki** oraz właściwy sposób **jak ładować docx** przy użyciu Aspose.Words dla .NET. Na koniec będziesz mieć gotowy przykład, który wypisuje każde ostrzeżenie o zamianie czcionki na konsolę, więc nigdy nie będziesz musiał zgadywać, co stało się w pliku.

## Wymagania wstępne

- .NET 6.0 lub nowszy (kod działa także na .NET Framework 4.7+)  
- Visual Studio 2022 lub dowolne IDE C#, które preferujesz  
- Pakiet NuGet **Aspose.Words** (`Install-Package Aspose.Words`)  
- Plik DOCX, który może zawierać czcionki niezainstalowane na Twoim komputerze (nazwijmy go `input.docx`)

> **Pro tip:** Jeśli nie masz pliku testowego, po prostu otwórz dokument Word używający niestandardowej czcionki firmowej i zapisz go jako `input.docx`. To wywoła ostrzeżenie, które chcemy przechwycić.

## Przegląd rozwiązania

1. **Utwórz** obiekt `LoadOptions` z włączonym `FontSubstitutionWarnings`.  
2. **Załaduj** plik DOCX przy użyciu tych opcji.  
3. **Sprawdź** kolekcję `WarningCallback` pod kątem wpisów `FontSubstitution`.  
4. **Zareaguj** – możesz zalogować, wyświetlić lub nawet programowo zamienić brakującą czcionkę.

Poniżej rozbijamy każdy krok, wyjaśniamy *dlaczego* jest ważny i podajemy kompletny, gotowy do uruchomienia fragment kodu.

---

## Krok 1: Zainstaluj Aspose.Words i skonfiguruj projekt

Zanim będziemy mogli **jak włączyć ostrzeżenia**, potrzebujemy biblioteki, która je obsługuje.

```bash
# Using the .NET CLI
dotnet add package Aspose.Words
```

Lub w konsoli Menedżera Pakietów Visual Studio:

```powershell
Install-Package Aspose.Words
```

> **Dlaczego ten krok?**  
> Bez pakietu klasy `LoadOptions`, `Document` i infrastruktura ostrzeżeń po prostu nie istnieją. Dodanie odwołania NuGet zapewnia, że pobierasz najnowszą stabilną wersję (na dzień dzisiejszy 24.5).

---

## Krok 2: Utwórz opcje ładowania, które włączają ostrzeżenia o zamianie czcionek

Serce **jak włączyć ostrzeżenia** znajduje się w klasie `LoadOptions`. Ustawienie `FontSubstitutionWarnings` na `true` mówi silnikowi, aby rejestrował każdy przypadek, gdy musi zamienić brakującą czcionkę.

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Warnings;

// Step 2: Build the options object
LoadOptions loadOptions = new LoadOptions
{
    // This flag makes the library emit warnings for any font it cannot find.
    FontSubstitutionWarnings = true
};
```

> **Dlaczego włączać tę flagę?**  
> Domyślnie Aspose.Words cicho zamienia brakujące czcionki na domyślną (zwykle Arial). Może to prowadzić do przesunięć układu, niewidocznych znaków lub naruszeń identyfikacji wizualnej. Włączenie flagi daje pełną przejrzystość.

---

## Krok 3: Załaduj plik DOCX przy użyciu skonfigurowanych opcji

Teraz, gdy wiemy **jak ładować docx** z włączonymi ostrzeżeniami, faktycznie wykonujemy ładowanie.

```csharp
// Step 3: Load the document – replace the path with your own file location.
string docPath = @"YOUR_DIRECTORY\input.docx";
Document document = new Document(docPath, loadOptions);
```

> **Co się dzieje w tle?**  
> Podczas parsowania DOCX, Aspose.Words sprawdza każdy element `<w:rFonts>`. Jeśli określona czcionka nie jest zainstalowana, rejestruje ostrzeżenie `FontSubstitution` i przechodzi na czcionkę domyślną. Ponieważ włączyliśmy ostrzeżenia, te wpisy trafiają do `document.WarningCallback.Warnings`.

---

## Krok 4: Pobierz i wyświetl ostrzeżenia o zamianie czcionek

Właściwość `WarningCallback` zawiera `WarningInfoCollection`. Przejdź przez nią, odfiltruj `WarningType.FontSubstitution` i wypisz komunikaty.

```csharp
// Step 4: Iterate over warnings and print font‑substitution details.
foreach (WarningInfo warning in document.WarningCallback.Warnings)
{
    if (warning.Type == WarningType.FontSubstitution)
    {
        Console.WriteLine($"⚠️ Font substituted: {warning.Message}");
    }
}
```

**Oczekiwany wynik** (przykład):

```
⚠️ Font substituted: Font 'MyCustomFont' was not found. Substituted with 'Arial'.
⚠️ Font substituted: Font 'CorporateLogo' was not found. Substituted with 'Times New Roman'.
```

> **Co zrobić z tymi komunikatami?**  
> Możesz je zalogować do pliku, wyświetlić w interfejsie użytkownika lub nawet uruchomić własną procedurę zamiany czcionek. Kluczowe jest to, że teraz *wykrywasz brakujące czcionki* zamiast zgadywać później.

---

## Krok 5: (Opcjonalnie) Zamień brakujące czcionki na określony zamiennik

Jeśli masz firmową czcionkę, którą chcesz wymusić, możesz obsłużyć ostrzeżenia i zamienić je w locie.

```csharp
// Optional: Custom fallback font
string fallbackFont = "Calibri";

foreach (WarningInfo warning in document.WarningCallback.Warnings)
{
    if (warning.Type == WarningType.FontSubstitution)
    {
        // Extract the missing font name from the warning message
        string missingFont = warning.Message.Split('\'')[1];
        Console.WriteLine($"Replacing missing font '{missingFont}' with '{fallbackFont}'");
        document.FontInfos[missingFont].SubstitutedFont = fallbackFont;
    }
}
```

> **Dlaczego warto to rozważyć?**  
> Gwarantuje to spójność wizualną we wszystkich generowanych dokumentach, co jest kluczowe dla zgodności z marką.

---

## Pełny, uruchamialny przykład

Poniżej znajduje się pojedynczy plik C#, który możesz skopiować i wkleić do aplikacji konsolowej. Zawiera wszystko — od instalacji pakietu po wypisywanie ostrzeżeń.

```csharp
// Program.cs
using System;
using Aspose.Words;
using Aspose.Words.Warnings;

namespace FontWarningDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // 1️⃣ Create LoadOptions with warnings enabled
            LoadOptions loadOptions = new LoadOptions
            {
                FontSubstitutionWarnings = true
            };

            // 2️⃣ Load the DOCX (adjust the path as needed)
            string docPath = @"YOUR_DIRECTORY\input.docx";
            Document doc = new Document(docPath, loadOptions);

            // 3️⃣ Show all font‑substitution warnings
            Console.WriteLine("=== Font Substitution Warnings ===");
            foreach (WarningInfo warning in doc.WarningCallback.Warnings)
            {
                if (warning.Type == WarningType.FontSubstitution)
                {
                    Console.WriteLine($"⚠️ {warning.Message}");
                }
            }

            // 4️⃣ (Optional) Replace missing fonts with Calibri
            string fallback = "Calibri";
            foreach (WarningInfo warning in doc.WarningCallback.Warnings)
            {
                if (warning.Type == WarningType.FontSubstitution)
                {
                    string missingFont = warning.Message.Split('\'')[1];
                    Console.WriteLine($"Replacing '{missingFont}' with '{fallback}'");
                    doc.FontInfos[missingFont].SubstitutedFont = fallback;
                }
            }

            // 5️⃣ Save the corrected document (optional)
            string outPath = @"YOUR_DIRECTORY\output.docx";
            doc.Save(outPath);
            Console.WriteLine($"Document saved to {outPath}");
        }
    }
}
```

**Uruchom:** `dotnet run` z folderu projektu. Jeśli jakiekolwiek czcionki będą brakować, zobaczysz wypisane ostrzeżenia, a opcjonalna zamiana zostanie zastosowana przed zapisaniem pliku.

---

## Najczęściej zadawane pytania

### Czy to działa także przy konwersji do PDF?

Tak. Po obsłużeniu ostrzeżeń możesz wywołać `doc.Save("output.pdf")` i zamienione czcionki pojawią się w PDF tak, jak w DOCX.

### Co zrobić, jeśli chcę wyciszyć ostrzeżenia dla konkretnej czcionki?

Możesz odfiltrować je w pętli — po prostu pomiń `WarningInfo`, którego `Message` zawiera nazwę czcionki, którą chcesz zignorować.

### Czy `FontSubstitutionWarnings` jest dostępny w starszych wersjach Aspose.Words?

Został wprowadzony w wersji 20.5. Jeśli używasz starszej wersji, zaktualizuj ją przez NuGet; zmiana API jest wstecznie kompatybilna.

---

## Podsumowanie

Przeprowadziliśmy Cię przez **jak włączyć ostrzeżenia**, pokazaliśmy **jak wykrywać brakujące czcionki** i zademonstrowaliśmy właściwy sposób **jak ładować docx** przy użyciu Aspose.Words, zachowując pełną przejrzystość zamian czcionek. Analizując `document.WarningCallback.Warnings`, otrzymujesz wiarygodny ślad audytu — koniec z cichymi zamianami.

Co dalej? Spróbuj podłączyć logikę ostrzeżeń do frameworka logowania, takiego jak Serilog, lub zbuduj interfejs, który podświetla brakujące czcionki przed udostępnieniem dokumentu użytkownikom. Możesz także przyjrzeć się klasie `FontSettings` w celu uzyskania bardziej szczegółowej kontroli nad politykami zamiany czcionek.

Miłego kodowania i niech Twoje dokumenty zawsze renderują się dokładnie tak, jak tego oczekujesz! 

![Diagram ilustrujący przepływ od ładowania pliku DOCX do przechwytywania ostrzeżeń o zamianie czcionek – jak włączyć ostrzeżenia w Aspose.Words](/images/font-warning-flow.png)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}