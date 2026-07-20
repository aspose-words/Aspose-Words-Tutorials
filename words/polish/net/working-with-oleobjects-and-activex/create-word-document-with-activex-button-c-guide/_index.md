---
category: general
date: 2026-07-19
description: Utwórz dokument Word przy użyciu Aspose.Words w C# i dowiedz się, jak
  dodać przycisk polecenia ActiveX, ustawić jego rozmiar oraz wstawić przycisk programowo.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document
- how to add activex
- insert command button
- set button size
- how to insert button
language: pl
lastmod: 2026-07-19
og_description: Utwórz dokument Word przy użyciu Aspose.Words C# i w kilka sekund
  osadź przycisk polecenia ActiveX. Skorzystaj z przewodnika krok po kroku, aby łatwo
  ustawić rozmiar przycisku i wstawić go.
og_image_alt: Screenshot of a Word document showing an ActiveX command button inserted
  via C#
og_title: Utwórz dokument Word z przyciskiem ActiveX – samouczek C#
schemas:
- author: Aspose
  dateModified: '2026-07-19'
  description: Create Word Document using Aspose.Words C# and learn how to add ActiveX
    command button, set button size, and insert button programmatically.
  headline: Create Word Document with ActiveX Button – C# Guide
  type: TechArticle
- description: Create Word Document using Aspose.Words C# and learn how to add ActiveX
    command button, set button size, and insert button programmatically.
  name: Create Word Document with ActiveX Button – C# Guide
  steps:
  - name: Prerequisites
    text: '- .NET 6.0 or later (the code also works on .NET Framework 4.7+). - A valid
      Aspose.Words for .NET license (or a free evaluation key). - Visual Studio 2022
      (or any IDE you like). - Basic familiarity with C# and object‑oriented programming.'
  - name: Platform Limitations
    text: '- ActiveX controls only run on the Windows version of Word. If your audience
      includes macOS or Word Online users, the button will appear as a static image.
      - Some corporate environments disable ActiveX for security; you may need to
      sign the document or inform users to enable content.'
  - name: VBA Interaction (Optional)
    text: If you want the button to execute a macro, you’ll have to add a VBA project
      to the document after saving. Aspose.Words does not generate VBA code automatically,
      but you can use the `Document.VbaProject` API to inject it.
  - name: Naming Collisions
    text: Always give each control a unique `Name`. Re‑using the same name can cause
      runtime errors when Word tries to resolve the control.
  - name: Performance Tip
    text: When inserting many controls, reuse a single `DocumentBuilder` instance
      and avoid calling `doc.Save` inside a loop. Batch the inserts and save once
      at the end.
  - name: What’s Next?
    text: '- **Style the button** – change fonts, colors, or add an image background.
      - **Attach VBA macros** – make the button perform calculations or launch external
      programs. - **Combine with other controls** – checkboxes, list boxes, or even
      embedded Excel sheets.'
  type: HowTo
tags:
- Aspose.Words
- C#
- ActiveX
- Word automation
title: Utwórz dokument Word z przyciskiem ActiveX – przewodnik C#
url: /pl/net/working-with-oleobjects-and-activex/create-word-document-with-activex-button-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Tworzenie dokumentu Word z przyciskiem ActiveX – Kompletny przewodnik C#

Zastanawiałeś się kiedyś, jak **utworzyć dokument Word**, który zawiera działający przycisk ActiveX? Być może automatyzujesz raport i potrzebujesz klikalnej kontrolki „Zatwierdź” bezpośrednio w pliku. W tym samouczku przejdziemy krok po kroku przez to właśnie – używając Aspose.Words for .NET, aby dodać przycisk polecenia ActiveX, ustawić jego rozmiar i wstawić go w wybrane miejsce.  

Jeśli kiedykolwiek pytałeś się *jak dodać activex* bez ręcznego otwierania Worda, jesteś we właściwym miejscu. Po zakończeniu będziesz mieć działający przykład, jasne wyjaśnienie każdego kroku oraz wskazówki, jak radzić sobie z typowymi problemami.

## Co się nauczysz

- Jak skonfigurować Aspose.Words w projekcie C#  
- Dokładny kod do **utworzenia dokumentu Word** i osadzenia przycisku polecenia ActiveX  
- Sposoby na **ustawienie rozmiaru przycisku** oraz dostosowanie jego napisu i nazwy  
- Prawidłową metodę **wstawiania przycisku polecenia** oraz **jak wstawić przycisk** w dowolnym miejscu dokumentu  
- Rozważania dotyczące przypadków brzegowych (wersja Worda, ograniczenia platformy, ostrzeżenia bezpieczeństwa)

### Wymagania wstępne

- .NET 6.0 lub nowszy (kod działa również na .NET Framework 4.7+).  
- Ważna licencja Aspose.Words for .NET (lub darmowy klucz ewaluacyjny).  
- Visual Studio 2022 (lub dowolne inne IDE).  
- Podstawowa znajomość C# i programowania obiektowego.

Innych bibliotek firm trzecich nie potrzebujesz.

---

## Krok 1: Utwórz dokument Word – konfiguracja projektu

Zanim będziemy mogli **wstawić przycisk polecenia**, potrzebny jest pusty plik Word, na którym będziemy pracować. Ten krok pokazuje klasyczny wzorzec „utworzenia dokumentu Word” przy użyciu Aspose.Words.

```csharp
// Add the Aspose.Words NuGet package first:
//   dotnet add package Aspose.Words
using Aspose.Words;
using Aspose.Words.Drawing.Ole;

// 1️⃣  Initialize a new blank document.
Document doc = new Document();

// 1️⃣  Create a DocumentBuilder – it lets us place content.
DocumentBuilder builder = new DocumentBuilder(doc);
```

> **Dlaczego to ważne:** `Document` reprezentuje cały plik .docx, natomiast `DocumentBuilder` śledzi bieżącą pozycję kursora. Wszystkie kolejne wstawienia (w tym nasz kontroler ActiveX) odbywają się względem tego buildera.

---

## Krok 2: Jak dodać ActiveX – budowanie kontrolki CommandButton

Teraz, gdy dokument istnieje, zajmiemy się częścią **jak dodać activex**. Aspose.Words udostępnia klasę `Forms2OleControl` dla obiektów ActiveX. Tutaj utworzymy przycisk polecenia i skonfigurujemy jego właściwości, w tym wymóg **ustawienia rozmiaru przycisku**.

```csharp
// 2️⃣  Create the ActiveX command button.
Forms2OleControl commandButton = new Forms2OleControl(
    doc,                     // Parent document
    Forms2OleControlType.CommandButton); // Control type

// Configure appearance – this is where we **set button size**.
commandButton.Width = 120;          // Width in points (≈1.67 inches)
commandButton.Height = 30;          // Height in points (≈0.42 inches)

// Set the text the user sees.
commandButton.Caption = "Click Me";

// Give the control a unique name for later reference.
commandButton.Name = "cmdButton1";
```

> **Pro tip:** Rozmiar jest podawany w punktach (1 punkt = 1/72 cala). Dostosuj wartości do swojego układu; typowy przycisk na pasku narzędzi ma wymiary 120 × 30 i wygląda dobrze.

---

## Krok 3: Wstaw przycisk polecenia – serce **Insert Command Button**

Gdy kontrolka jest gotowa, **wstawiamy przycisk polecenia** do dokumentu w bieżącej lokalizacji buildera. Możesz przenieść builder w dowolne miejsce (np. po akapicie) przed wywołaniem tej metody.

```csharp
// 3️⃣  Insert the prepared ActiveX control into the document.
builder.InsertForms2OleControl(commandButton);
```

Jeśli potrzebujesz **jak wstawić przycisk** w określonym zakładce, najpierw przesuń builder:

```csharp
builder.MoveToBookmark("MyPlace"); // Ensure a bookmark named 'MyPlace' exists
builder.InsertForms2OleControl(commandButton);
```

> **Co się dzieje w tle?** Aspose.Words zapisuje niezbędne strumienie obiektów OLE w pakiecie .docx, dzięki czemu Word może wyświetlić przycisk bez dodatkowych makr.

---

## Krok 4: Zapisz dokument – zakończenie cyklu **Create Word Document**

Ostatni krok jest prosty: zapisz plik na dysku. To kończy pełny cykl **utworzenia dokumentu Word**, osadzenia ActiveX i zapisu.

```csharp
// 4️⃣  Save the document where you want it.
string outputPath = @"C:\Temp\CommandButton.docx";
doc.Save(outputPath);
```

Otwórz wynikowy plik w Microsoft Word (tylko Windows). Powinieneś zobaczyć klikalny przycisk oznaczony „Click Me”. Kliknięcie wywoła domyślną akcję dla CommandButton – nic się nie stanie, dopóki nie podłączysz kodu VBA, ale kontrolka jest w pełni funkcjonalna.

> **Oczekiwany wynik:** Plik .docx z jedną stroną, przyciskiem wyśrodkowanym w miejscu wstawienia, o wymiarach 120 × 30 pt, z napisem „Click Me”.  
> ![Przycisk ActiveX wstawiony do dokumentu Word](placeholder-image.png)  
> *Tekst alternatywny obrazu:* **Przycisk ActiveX wstawiony do dokumentu Word przy użyciu C#** (matches `og_image_alt`).

---

## Krok 5: Przypadki brzegowe, bezpieczeństwo i dobre praktyki

### Ograniczenia platformy
- Kontrolki ActiveX działają wyłącznie w wersji Worda na Windows. Jeśli Twoi odbiorcy korzystają z macOS lub Word Online, przycisk zostanie wyświetlony jako statyczny obraz.
- W niektórych środowiskach korporacyjnych ActiveX jest wyłączone ze względów bezpieczeństwa; może być konieczne podpisanie dokumentu lub poinformowanie użytkowników o włączeniu zawartości.

### Interakcja z VBA (opcjonalnie)
Jeśli chcesz, aby przycisk wykonywał makro, musisz dodać projekt VBA do dokumentu po zapisaniu. Aspose.Words nie generuje kodu VBA automatycznie, ale możesz użyć API `Document.VbaProject`, aby go wstrzyknąć.

### Kolizje nazw
Zawsze nadaj każdej kontrolce unikalną właściwość `Name`. Ponowne użycie tej samej nazwy może spowodować błędy w czasie działania, gdy Word będzie próbował rozwiązać kontrolkę.

### Wskazówka dotycząca wydajności
Podczas wstawiania wielu kontrolek, używaj jednego egzemplarza `DocumentBuilder` i unikaj wywoływania `doc.Save` w pętli. Grupuj wstawienia i zapisz raz na końcu.

---

## Pełny działający przykład

Łącząc wszystko razem, oto kompletny, gotowy do skopiowania i wklejenia program:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing.Ole;

class Program
{
    static void Main()
    {
        // Initialize a new blank document.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Create and configure the ActiveX command button.
        Forms2OleControl commandButton = new Forms2OleControl(
            doc, Forms2OleControlType.CommandButton);
        commandButton.Width = 120;          // Set button size – width
        commandButton.Height = 30;          // Set button size – height
        commandButton.Caption = "Click Me";
        commandButton.Name = "cmdButton1";

        // Insert the button at the current cursor position.
        builder.InsertForms2OleControl(commandButton);

        // Save the document.
        string outputPath = @"C:\Temp\CommandButton.docx";
        doc.Save(outputPath);

        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

Uruchom program, otwórz zapisany plik i zobacz przycisk dokładnie w miejscu, w którym znajdował się builder.

---

## Podsumowanie

Właśnie **utworzyliśmy dokument Word** od podstaw, nauczyliśmy się **jak dodać activex** poprzez skonfigurowanie `Forms2OleControl`, opanowaliśmy właściwości **ustawienia rozmiaru przycisku** oraz zademonstrowaliśmy prawidłowy sposób **wstawiania przycisku polecenia** i **jak wstawić przycisk** w dowolnym miejscu pliku.  

Z jednego przykładu kodu masz teraz solidną bazę do bardziej zaawansowanej automatyzacji Worda – czy to budujesz szablony z interaktywnymi formularzami, generujesz kontrakty wymagające potwierdzenia użytkownika, czy po prostu dodajesz kilka przydatnych kontrolek do raportu.

### Co dalej?

- **Stylizuj przycisk** – zmień czcionki, kolory lub dodaj tło graficzne.  
- **Dołącz makra VBA** – spraw, by przycisk wykonywał obliczenia lub uruchamiał zewnętrzne programy.  
- **Połącz z innymi kontrolkami** – pola wyboru, listy rozwijane czy nawet osadzone arkusze Excel.  

Eksperymentuj, a jeśli napotkasz problem, zostaw komentarz poniżej. Miłego kodowania i udanej automatyzacji Worda z Aspose.Words!

## Co powinieneś nauczyć się dalej?

Poniższe samouczki obejmują tematy ściśle powiązane, które rozwijają techniki przedstawione w tym przewodniku. Każdy zasób zawiera kompletne przykłady kodu oraz szczegółowe wyjaśnienia, aby pomóc Ci opanować dodatkowe funkcje API i odkrywać alternatywne podejścia w własnych projektach.

- [Create Word Document with Aspose.Words for .NET](/words/english/net/add-content-using-document-builder/insert-paragraph/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Insert Inline Image in Word Document using Aspose.Words](/words/english/net/add-content-using-document-builder/insert-inline-image/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}