---
category: general
date: 2026-03-13
description: Jak przechwytywać ostrzeżenia podczas ładowania dokumentów przy użyciu
  Aspose.Words, plus wskazówki dotyczące obsługi brakujących czcionek i ustawiania
  własnych ustawień czcionek. Poznaj pełne rozwiązanie w C#.
draft: false
keywords:
- how to capture warnings
- handle missing fonts
- set custom font settings
language: pl
og_description: Jak przechwytywać ostrzeżenia przy ładowaniu plików Word w Aspose.Words,
  a także praktyczne sposoby radzenia sobie z brakującymi czcionkami i ustawiania
  własnych ustawień czcionek.
og_title: Jak przechwytywać ostrzeżenia w Aspose.Words – Kompletny przewodnik
tags:
- Aspose.Words
- C#
- Document Processing
title: Jak przechwycić ostrzeżenia w Aspose.Words – Kompletny przewodnik
url: /pl/net/working-with-fonts/how-to-capture-warnings-in-aspose-words-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak przechwycić ostrzeżenia w Aspose.Words – Kompletny przewodnik

Zastanawiałeś się kiedyś **jak przechwycić ostrzeżenia**, które pojawiają się, gdy Aspose.Words ładuje dokument? W wielu rzeczywistych projektach zobaczysz alerty o podstawianiu czcionek, notatki o przestarzałych funkcjach czy nawet komunikaty związane z bezpieczeństwem. Ignorowanie ich jest jak jazda z pękniętą szybą – możesz dotrzeć do celu, ale nigdy nie wiesz, kiedy coś się zepsuje.

Dobrą wiadomością jest to, że Aspose.Words oferuje czysty, oparty na callbackach sposób przechwytywania tych komunikatów. W tym samouczku przejdziemy przez **kompletny przykład w C#**, który nie tylko przechwytuje ostrzeżenia, ale także pokazuje, jak **obsługiwać brakujące czcionki** i **ustawiać własne ustawienia czcionek**, aby dokumenty renderowały się dokładnie tak, jak oczekujesz.

---

## Co się nauczysz

- Skonfiguruj `LoadOptions`, aby podłączyć własny obiekt `FontSettings`.  
- Zarejestruj callback ostrzeżeń, który filtruje zdarzenia `FontSubstitution`.  
- Wypisz szczegóły ostrzeżeń na konsolę (lub dowolny logger, którego używasz).  
- Rozszerz rozwiązanie, aby elegancko obsługiwać brakujące czcionki na różnych platformach.  

Po zakończeniu tego przewodnika będziesz mieć gotowy do uruchomienia fragment kodu, który możesz wkleić do dowolnego projektu .NET, oraz garść praktycznych wskazówek, jak unikać typowych pułapek.

---

## Wymagania wstępne

| Requirement | Why It Matters |
|-------------|----------------|
| **Aspose.Words for .NET** (v23.12 or later) | API, którego używamy (`LoadOptions`, `IWarningCallback`), znajduje się tutaj. |
| **.NET 6+** (or .NET Framework 4.7.2+) | Nowoczesne funkcje językowe sprawiają, że kod jest czystszy. |
| **A sample DOCX** (named `input.docx`) placed in a known folder | Potrzebujemy czegoś do załadowania i wywołania ostrzeżenia. |
| **A console or logging framework** (optional) | Aby zobaczyć przechwycone ostrzeżenia w działaniu. |

Nie są wymagane dodatkowe pakiety NuGet poza samym Aspose.Words.

---

## Krok 1: Skonfiguruj własne ustawienia czcionek  

Zanim załadujesz dokument, możesz poinformować Aspose.Words, gdzie szukać czcionek. To jest część **ustawiania własnych ustawień czcionek** układanki.

```csharp
using Aspose.Words;
using Aspose.Words.Loading;
using System;

// 1️⃣ Create a FontSettings instance and point it at your font folder.
FontSettings fontSettings = new FontSettings();
fontSettings.SetFontsFolder(@"C:\MyFonts", recursive: true);

// 2️⃣ Plug the FontSettings into LoadOptions.
LoadOptions loadOptions = new LoadOptions
{
    FontSettings = fontSettings
};
```

**Dlaczego to jest ważne:**  
Jeśli DOCX odwołuje się do czcionki, która nie jest zainstalowana na komputerze, Aspose.Words cicho podstawi czcionkę zapasową *chyba że* skonfigurowałeś folder z wymaganymi czcionkami. Ustawiając własny folder, zmniejszasz ryzyko ostrzeżeń o „podstawianiu czcionek” już na początku.

> **Wskazówka:** Na Linuksie może być konieczne dodanie pakietu `fonts-dejavu-core` lub dowolnej kolekcji TrueType, od której zależą Twoje dokumenty.

---

## Krok 2: Zarejestruj callback ostrzeżeń  

Aspose.Words implementuje `IWarningCallback`. Stworzymy mały handler, który wypisuje tylko ostrzeżenia, które nas interesują: brakujące lub podstawione czcionki.

```csharp
// 3️⃣ Register the callback.
loadOptions.WarningCallback = new FontWarningHandler();
```

```csharp
public class FontWarningHandler : IWarningCallback
{
    public void Warn(IWarningInfo info)
    {
        // Filter for font‑substitution warnings only.
        if (info.WarningType == WarningType.FontSubstitution)
        {
            // You could log to a file, send to telemetry, etc.
            Console.WriteLine($"[Font Substitution] {info.Description}");
        }
        // Optionally handle other warning types here.
    }
}
```

**Dlaczego to jest ważne:**  
Scenariusz **obsługi brakujących czcionek** jest teraz widoczny. Zamiast zgadywać, która czcionka została zamieniona, otrzymujesz jasny opis, np. „Font 'Calibri' was substituted with 'Arial'”. To nieocenione przy debugowaniu problemów z układem w generowanych PDF‑ach lub raportach drukowanych.

---

## Krok 3: Załaduj dokument z skonfigurowanymi opcjami  

Teraz w końcu wczytujemy dokument do pamięci, używając `LoadOptions`, które właśnie przygotowaliśmy.

```csharp
// 4️⃣ Load the DOCX. Any warnings will flow through FontWarningHandler.
Document doc = new Document(@"C:\Docs\input.docx", loadOptions);

// Quick sanity check – render the first page to PDF (optional).
doc.Save(@"C:\Docs\output.pdf");
Console.WriteLine("Document loaded and saved successfully.");
```

Jeśli plik źródłowy używa czcionki, której nie ma w `C:\MyFonts`, zobaczysz wyjście podobne do:

```
[Font Substitution] Font 'OpenSans-Regular' was substituted with 'Arial'.
Document loaded and saved successfully.
```

Ta linia to wynik **jak przechwycić ostrzeżenia**, którego szukałeś.

---

## Krok 4: Pełny działający przykład (gotowy do kopiowania i wklejenia)

Poniżej znajduje się cały program, gotowy do kompilacji. Wklej go do nowego projektu konsolowego i uruchom — upewnij się tylko, że ścieżki wskazują na rzeczywiste lokalizacje w Twoim systemie.

```csharp
using Aspose.Words;
using Aspose.Words.Loading;
using System;

namespace AsposeWarningDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // -------------------------------------------------
            // Step 1: Prepare LoadOptions with custom FontSettings.
            // -------------------------------------------------
            FontSettings fontSettings = new FontSettings();
            fontSettings.SetFontsFolder(@"C:\MyFonts", recursive: true);

            LoadOptions loadOptions = new LoadOptions
            {
                FontSettings = fontSettings,
                // Step 2: Attach the warning callback.
                WarningCallback = new FontWarningHandler()
            };

            // -------------------------------------------------
            // Step 3: Load the document – warnings flow to handler.
            // -------------------------------------------------
            string inputPath = @"C:\Docs\input.docx";
            Document doc = new Document(inputPath, loadOptions);

            // Optional: Save as PDF to verify rendering.
            string outputPath = @"C:\Docs\output.pdf";
            doc.Save(outputPath);

            Console.WriteLine("Document processed. Check console for any warning messages.");
        }
    }

    // -------------------------------------------------
    // Warning handler that focuses on missing‑font events.
    // -------------------------------------------------
    public class FontWarningHandler : IWarningCallback
    {
        public void Warn(IWarningInfo info)
        {
            if (info.WarningType == WarningType.FontSubstitution)
            {
                Console.WriteLine($"[Font Substitution] {info.Description}");
            }
            // You could add more branches for other warning types.
        }
    }
}
```

**Oczekiwany wynik:**  

- Jeśli wszystkie czcionki są dostępne:  
  `Document processed. Check console for any warning messages.`  

- Jeśli brakuje czcionki:  
  ```
  [Font Substitution] Font 'Times New Roman' was substituted with 'Arial'.
  Document processed. Check console for any warning messages.
  ```

---

## Krok 5: Częste warianty i przypadki brzegowe  

| Situation | What to Adjust |
|-----------|----------------|
| **Multiple font folders** | Wywołaj `fontSettings.AddFontFolder(@"C:\MoreFonts", true);` dla każdej dodatkowej lokalizacji. |
| **Suppress all warnings** | Zaimplementuj `Warn`, ale pozostaw ciało pustym, lub ustaw `loadOptions.WarningCallback = null;`. |
| **Capture other warning types** | Sprawdź `info.WarningType` pod kątem `WarningType.DeprecatedFeature`, `WarningType.UnexpectedContent` itp. |
| **Running on Linux/macOS** | Upewnij się, że folder czcionek zawiera pliki `.ttf`/`.otf` kompatybilne z Linuksem; może być konieczne zainstalowanie `libfontconfig`. |
| **Large documents** | Rozważ strumieniowe wczytywanie dokumentu (`LoadOptions.LoadFormat = LoadFormat.Docx;`), aby zmniejszyć obciążenie pamięci. |

Przewidując te scenariusze, unikniesz niespodzianek przy przechodzeniu z maszyny deweloperskiej do potoku CI lub maszyny w chmurze.

---

## Krok 6: Wizualne potwierdzenie (opcjonalnie)

Jeśli wolisz szybki wizualny sygnał, możesz zrzucić przechwycone ostrzeżenia do małego raportu HTML. Oto mały fragment, który zapisuje komunikaty do `warnings.html`:

```csharp
using System.IO;
using System.Text;

public class HtmlWarningHandler : IWarningCallback
{
    private readonly StringBuilder _sb = new StringBuilder();

    public void Warn(IWarningInfo info)
    {
        if (info.WarningType == WarningType.FontSubstitution)
        {
            _sb.AppendLine($"<li>{info.Description}</li>");
        }
    }

    public void WriteReport(string path)
    {
        string html = $"<html><body><h2>Font Substitution Warnings</h2><ul>{_sb}</ul></body></html>";
        File.WriteAllText(path, html);
    }
}
```

Po załadowaniu dokumentu wywołaj `handler.WriteReport(@"C:\Docs\warnings.html");` i otwórz go w przeglądarce. Poniższy obrazek pokazuje, jak może wyglądać raport:

![Jak przechwycić ostrzeżenia – zrzut ekranu](/images/capture-warnings.png)

*Alt text:* **jak przechwycić ostrzeżenia** – zrzut ekranu wyjścia konsoli i raportu HTML.

---

## Zakończenie  

Omówiliśmy **jak przechwycić ostrzeżenia** w Aspose.Words, przedstawiliśmy niezawodny sposób **obsługi brakujących czcionek** oraz pokazaliśmy, jak **ustawiać własne ustawienia czcionek** dla deterministycznego renderowania. Pełny przykład jest gotowy do wstawienia w dowolnym rozwiązaniu .NET, a modułowy `FontWarningHandler` można rozszerzyć, aby dopasować go do Twojej strategii logowania lub telemetrii.

Następne kroki? Spróbuj zamienić wywołania `Console.WriteLine` na strukturalny logger, np. Serilog, lub przesłać ostrzeżenia do Application Insights w celu monitorowania w czasie rzeczywistym. Możesz także zbadać wzorzec `DocumentVisitor`, jeśli potrzebujesz przeglądać zawartość dokumentu po jego załadowaniu.

Masz pytania o inne typy ostrzeżeń lub strategie osadzania czcionek? zostaw komentarz poniżej — miłego kodowania!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}