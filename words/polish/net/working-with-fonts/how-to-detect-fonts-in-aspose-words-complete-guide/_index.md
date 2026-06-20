---
category: general
date: 2026-04-21
description: Dowiedz się, jak wykrywać czcionki, przechwytywać ostrzeżenia, konfigurować
  wywołanie zwrotne i wyliczać ostrzeżenia przy użyciu Aspose.Words w C#. Przewodnik
  krok po kroku zapewniający niezawodne zarządzanie czcionkami.
draft: false
keywords:
- how to detect fonts
- how to capture warnings
- how to configure callback
- how to enumerate warnings
- Aspose.Words font handling
language: pl
og_description: Jak wykrywać czcionki w Aspose.Words? Ten samouczek pokazuje, jak
  przechwycić ostrzeżenia, skonfigurować wywołanie zwrotne i wyliczyć ostrzeżenia
  w C#.
og_title: Jak wykrywać czcionki w Aspose.Words – Kompletny przewodnik
tags:
- Aspose.Words
- C#
- Document Processing
title: Jak wykrywać czcionki w Aspose.Words – kompletny przewodnik
url: /pl/net/working-with-fonts/how-to-detect-fonts-in-aspose-words-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak wykrywać czcionki w Aspose.Words – kompletny przewodnik

Zastanawiałeś się kiedyś **jak wykrywać czcionki**, które brakuje podczas ładowania dokumentu Word? To sytuacja, która pojawia się częściej niż by się chciało, szczególnie przy pracy z starszymi plikami lub wdrożeniami wieloplatformowymi. W tym tutorialu przeprowadzimy Cię przez kompletny, gotowy do uruchomienia przykład, który **przechwytuje ostrzeżenia**, **konfiguruje callback** i **enumeruje ostrzeżenia**, abyś zawsze wiedział, które czcionki zostały zastąpione.

Użyjemy Aspose.Words for .NET (v24.9 w momencie pisania) oraz czystego C#. Bez zewnętrznych usług, bez magii — tylko API i kilka linijek kodu. Po zakończeniu będziesz mógł wykrywać każdą zamianę czcionki, logować ją i nawet zdecydować, czy przerwać ładowanie, jeśli brakująca czcionka jest krytyczna.  

### Czego potrzebujesz
- **Aspose.Words for .NET** (instalacja przez NuGet: `Install-Package Aspose.Words`)
- .NET 6.0 lub nowszy (kod działa także na .NET Framework)
- Przykładowy plik DOCX, który odwołuje się do czcionki nieobecnej w systemie (np. „MyCustomFont.ttf”)
- Visual Studio, Rider lub dowolny edytor C#, którego używasz

> **Pro tip:** Jeśli nie masz dokumentu z brakującymi czcionkami, po prostu zmień nazwę pliku czcionki w systemie lub edytuj XML w DOCX, aby odwoływał się do nieistniejącej rodziny czcionek.

---

## Jak wykrywać czcionki z Aspose.Words

Kluczowa idea polega na podłączeniu się do systemu ostrzeżeń Aspose.Words. Gdy biblioteka nie może znaleźć żądanej czcionki, generuje ostrzeżenie `WarningType.FontSubstitution`. Dostarczając własną implementację `IWarningCallback`, możesz **wykrywać czcionki**, które zostały zamienione podczas procesu ładowania.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// 1️⃣ Create a collector that implements IWarningCallback
public class FontWarningCollector : IWarningCallback
{
    public List<WarningInfo> Warnings { get; } = new();

    public void Warning(WarningInfo info)
    {
        // Store every warning – we’ll filter later
        Warnings.Add(info);
    }
}
```

> **Dlaczego to działa:** Aspose.Words wywołuje metodę `Warning` dla każdego niekrytycznego problemu. Przechowując obiekty `WarningInfo`, uzyskujesz pełny dostęp do typu, wiadomości i kontekstu, co jest dokładnie tym, czego potrzebujesz, aby **wykrywać czcionki** zamieniane w trakcie ładowania.

---

## Jak przechwytywać ostrzeżenia podczas ładowania dokumentu

Mając już kolektor, musimy poinstruować `LoadOptions`, aby go używał. To jest część **jak przechwytywać ostrzeżenia** w całej układance.

```csharp
// 2️⃣ Prepare LoadOptions with our warning collector
var warningCollector = new FontWarningCollector();
var loadOptions = new LoadOptions
{
    // Assign the callback – this is where warnings are captured
    WarningCallback = warningCollector
};

// 3️⃣ Load the document (replace the path with your own file)
Document doc = new Document("YOUR_DIRECTORY/DocumentWithMissingFont.docx", loadOptions);
```

> **Przypadek brzegowy:** Jeśli ładujesz dokument ze strumienia (`new Document(stream, loadOptions)`), ten sam callback działa — po prostu przekaż strumień zamiast ścieżki do pliku.

W tym momencie dokument jest w pełni załadowany, ale wszystkie ostrzeżenia o zamianie czcionek są bezpiecznie przechowywane w `warningCollector.Warnings`.

---

## Jak enumerować ostrzeżenia i raportować zamiany czcionek

Na koniec przeglądamy zebrane ostrzeżenia i **enumerujemy ostrzeżenia**, które dotyczą konkretnie zamiany czcionek. Ten krok przekształca surowe dane w czytelny raport.

```csharp
// 4️⃣ Iterate over the collected warnings
foreach (var warning in warningCollector.Warnings)
{
    // We're only interested in font substitution warnings
    if (warning.Type == WarningType.FontSubstitution)
    {
        Console.WriteLine($"Substituted font: {warning.Message}");
    }
}
```

**Oczekiwany wynik** (przykład):

```
Substituted font: Font 'Calibri' not found. Substituted with 'Arial'.
Substituted font: Font 'MyCustomFont' not found. Substituted with 'Times New Roman'.
```

Jeśli dokument nie zawiera brakujących czcionek, pętla po prostu nie wypisze nic — nie ma o czym się martwić.

---

## Pełny działający przykład (wszystkie kroki w jednym pliku)

Poniżej znajduje się kompletny program, który możesz skopiować i wkleić do projektu konsolowego. Łączy on **jak wykrywać czcionki**, **jak przechwytywać ostrzeżenia**, **jak konfigurować callback** oraz **jak enumerować ostrzeżenia** w jednej spójnej całości.

```csharp
using System;
using System.Collections.Generic;
using Aspose.Words;
using Aspose.Words.Fonts;

namespace FontDetectionDemo
{
    // Custom warning collector (captures all warnings)
    public class FontWarningCollector : IWarningCallback
    {
        public List<WarningInfo> Warnings { get; } = new();

        public void Warning(WarningInfo info)
        {
            Warnings.Add(info);
        }
    }

    class Program
    {
        static void Main(string[] args)
        {
            // -------------------------------------------------
            // Step 1: Set up the warning collector (how to configure callback)
            var collector = new FontWarningCollector();
            var loadOptions = new LoadOptions
            {
                WarningCallback = collector
            };

            // -------------------------------------------------
            // Step 2: Load the document (how to detect fonts)
            string filePath = "YOUR_DIRECTORY/DocumentWithMissingFont.docx";
            Document doc;
            try
            {
                doc = new Document(filePath, loadOptions);
            }
            catch (Exception ex)
            {
                Console.WriteLine($"Failed to load document: {ex.Message}");
                return;
            }

            // -------------------------------------------------
            // Step 3: Enumerate warnings (how to enumerate warnings)
            bool anySubstitutions = false;
            foreach (var warning in collector.Warnings)
            {
                if (warning.Type == WarningType.FontSubstitution)
                {
                    anySubstitutions = true;
                    Console.WriteLine($"Substituted font: {warning.Message}");
                }
            }

            if (!anySubstitutions)
            {
                Console.WriteLine("No font substitutions detected – all fonts are available.");
            }

            // Optional: Continue processing the document...
        }
    }
}
```

**Uruchomienie tego programu** wypisze każdą czcionkę, którą Aspose.Words musiało zastąpić. Możesz przekierować wyjście do pliku logu, wywołać alarm lub nawet przerwać ładowanie, jeśli brakująca czcionka jest krytyczna.

---

## Częste pytania i pułapki

### Co zrobić, gdy trzeba zatrzymać ładowanie przy brakującej czcionce?
Możesz sprawdzić obiekty `WarningInfo` w callbacku i rzucić wyjątek, gdy pojawi się konkretna nazwa czcionki. Wyjątek przerwie ładowanie, dając pełną kontrolę.

```csharp
public void Warning(WarningInfo info)
{
    if (info.Type == WarningType.FontSubstitution &&
        info.Message.Contains("MyCriticalFont"))
    {
        throw new InvalidOperationException("Critical font missing – aborting load.");
    }
    Warnings.Add(info);
}
```

### Czy to działa z PDF‑ami lub innymi formatami?
Tak. Aspose.Words używa tej samej infrastruktury ostrzeżeń dla PDF, RTF i HTML. Wystarczy zmienić rozszerzenie pliku, a reszta kodu pozostaje identyczna.

### Jak mogę logować ostrzeżenia do pliku zamiast na konsolę?
Zamień `Console.WriteLine` na dowolny framework logujący, którego używasz (`Serilog`, `NLog` itp.). Klasa `WarningInfo` udostępnia `Message`, `Source` i `Exception` do szczegółowych logów.

### Czy to wpłynie na wydajność?
Obciążenie jest znikome — Aspose.Words i tak generuje ostrzeżenia wewnętrznie. Dodanie callbacku po prostu zapisuje je w liście, co jest O(n) względem liczby ostrzeżeń. Dla typowych dokumentów wpływ jest znacznie poniżej 1 % całkowitego czasu ładowania.

---

## Podsumowanie wizualne

![Jak wykrywać czcionki w Aspose.Words – diagram przepływu ostrzeżeń](https://example.com/images/font-detection-diagram.png "jak wykrywać czcionki")

*Tekst alternatywny:* **jak wykrywać czcionki** – diagram pokazujący callback ostrzeżeń, kolekcję i kroki enumeracji.

---

## Zakończenie

Omówiliśmy **jak wykrywać czcionki** w Aspose.Words poprzez **przechwytywanie ostrzeżeń**, **konfigurowanie callbacku** i **enumerowanie ostrzeżeń**. Pełny przykład kodu prezentuje gotowy do produkcji wzorzec, który możesz wstawić do dowolnej aplikacji .NET.  

Następnie możesz rozważyć:

- **Jak przechwytywać ostrzeżenia** dla innych problemów (np. problemy z konwersją obrazów)
- **Jak konfigurować callback** dla własnych frameworków logujących
- **Jak enumerować ostrzeżenia** w wielu dokumentach w ramach zadania wsadowego
- Użycie **Aspose.Words.Fonts.FontSettings** do podania folderów z czcionkami zapasowymi, co może zmniejszyć liczbę zamian już na etapie ładowania.

Wypróbuj, dostosuj kolektor do swojego stylu logowania i nigdy nie daj się zaskoczyć nieoczekiwaną zamianą czcionki. Jeśli napotkasz jakiekolwiek problemy, zostaw komentarz poniżej — miłego kodowania!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}