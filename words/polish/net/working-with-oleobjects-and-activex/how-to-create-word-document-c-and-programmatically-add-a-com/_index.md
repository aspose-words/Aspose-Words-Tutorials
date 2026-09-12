---
category: general
date: 2026-09-11
description: Dowiedz się, jak w C# utworzyć dokument Word i programowo dodać przycisk
  polecenia przy użyciu Aspose.Words w kilku prostych krokach.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document c#
- programmatically add command button
language: pl
lastmod: 2026-09-11
og_description: Utwórz dokument Word w C# i programowo dodaj przycisk polecenia za
  pomocą Aspose.Words. Przejrzyj ten kompletny przewodnik, aby uzyskać działające
  rozwiązanie.
og_image_alt: Screenshot of a Word document containing a Submit command button created
  with C#
og_title: Utwórz dokument Word w C# – dodaj przycisk polecenia programowo
schemas:
- author: Aspose
  dateModified: '2026-09-11'
  description: Learn how to create word document c# and programmatically add a command
    button using Aspose.Words in a few simple steps.
  headline: How to create word document c# and programmatically add a command button
  type: TechArticle
- description: Learn how to create word document c# and programmatically add a command
    button using Aspose.Words in a few simple steps.
  name: How to create word document c# and programmatically add a command button
  steps:
  - name: Launch Word and open `CommandButton.docx`.
    text: Launch Word and open `CommandButton.docx`.
  - name: You should see a button labeled **Submit** in the document body.
    text: You should see a button labeled **Submit** in the document body.
  - name: Hovering over the button reveals the name `btnSubmit` in the **Properties**
      pane (Developer tab → Properties).
    text: Hovering over the button reveals the name `btnSubmit` in the **Properties**
      pane (Developer tab → Properties).
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
- ActiveX
title: Jak utworzyć dokument Word w C# i programowo dodać przycisk polecenia
url: /pl/net/working-with-oleobjects-and-activex/how-to-create-word-document-c-and-programmatically-add-a-com/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak utworzyć dokument Word w C# i programowo dodać przycisk poleceń

Jeśli potrzebujesz **utworzyć dokument Word w C#** i osadzić interaktywny przycisk, ten przewodnik pokaże Ci dokładnie, jak to zrobić. Korzystając z Aspose.Words możesz programowo dodać przycisk **CommandButton** w zaledwie kilku linijkach kodu, eliminując potrzebę ręcznej pracy z interfejsem w Wordzie.

W tym tutorialu dowiesz się, jak:

* Zainicjować pusty plik Word przy użyciu C#.
* Wstawić kontrolkę ActiveX **CommandButton**.
* Ustawić właściwości przycisku, takie jak nazwa i podpis.
* Zapisać dokument, aby przycisk był widoczny po otwarciu pliku w Microsoft Word.

Nie są wymagane żadne zewnętrzne narzędzia poza biblioteką Aspose.Words for .NET, a kroki działają z .NET 6+ lub .NET Framework 4.6.2 i nowszymi.

## Wymagania wstępne

Zanim rozpoczniesz, upewnij się, że masz:

| Wymaganie | Powód |
|------------|--------|
| .NET 6 SDK (lub .NET Framework 4.6.2+) | Dostarcza środowisko uruchomieniowe dla projektu C#. |
| Visual Studio 2022 (lub dowolne IDE C#) | Ułatwia pisanie, budowanie i uruchamianie kodu. |
| Pakiet NuGet Aspose.Words for .NET | Dostarcza klasy `Document`, `DocumentBuilder` i `Forms2OleControl` używane w przykładzie. |
| Podstawowa znajomość składni C# | Pozwala śledzić kod bez dodatkowych krzywych uczenia się. |

Pakiet Aspose.Words możesz dodać za pomocą konsoli NuGet:

```powershell
Install-Package Aspose.Words
```

## Krok 1: Utwórz nowy projekt konsolowy C#

Utwórz aplikację konsolową, która wygeneruje plik Word. Otwórz terminal i uruchom:

```bash
dotnet new console -n WordButtonDemo
cd WordButtonDemo
dotnet add package Aspose.Words
```

Wygenerowany plik `Program.cs` będzie zawierał kod przedstawiony w kolejnych krokach.

## Krok 2: Utwórz pusty dokument i DocumentBuilder

Pierwszą operacją jest stworzenie obiektu `Document`, który reprezentuje pusty plik `.docx`, oraz `DocumentBuilder`, który umożliwia edycję zawartości dokumentu.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Forms;

class Program
{
    static void Main()
    {
        // Step 2: Create a new blank document and a DocumentBuilder to edit it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

**Dlaczego to ważne:**  
`Document` jest kontenerem dla wszystkich elementów Worda (akapity, tabele, kontrolki). `DocumentBuilder` zapewnia płynne API do wstawiania obiektów w bieżącej pozycji kursora bez konieczności pracy z niskopoziomowymi kolekcjami węzłów.

## Krok 3: Wstaw kontrolkę ActiveX CommandButton

Aspose.Words obsługuje wstawianie starszych kontrolek ActiveX poprzez metodę `InsertForms2OleControl`. Metoda wymaga typu kontrolki oraz żądanych wymiarów w punktach.

```csharp
        // Step 3: Insert an ActiveX CommandButton control (size: 100x30 points)
        Forms2OleControl commandButton = builder.InsertForms2OleControl(
            ControlType.CommandButton, 100, 30);
```

**Co się dzieje „pod maską”:**  
Word traktuje kontrolkę ActiveX jako obiekt OLE (Object Linking and Embedding). Klasa `Forms2OleControl` opakowuje dane OLE i udostępnia właściwości takie jak `Name` i `Caption`.

## Krok 4: Skonfiguruj nazwę i podpis przycisku

Po umieszczeniu kontrolki możesz dostosować jej właściwości w czasie wykonywania. Ustawienie znaczącej `Name` pomaga później zidentyfikować przycisk, natomiast `Caption` definiuje tekst wyświetlany na przycisku.

```csharp
        // Step 4: Set the button's name and displayed caption
        commandButton.Name = "btnSubmit";
        commandButton.Caption = "Submit";
```

**Wskazówka dla profesjonalistów:**  
Jeśli planujesz obsłużyć zdarzenie kliknięcia przycisku w VBA, `Name` staje się nazwą makra, które wywołujesz, np. `Sub btnSubmit_Click()`.

## Krok 5: Zapisz dokument na dysku

Na koniec zapisz dokument do pliku `.docx`. Wybierz folder, do którego masz prawo zapisu; w przykładzie użyto ścieżki względnej, która rozwiązuje się do katalogu wyjściowego projektu.

```csharp
        // Step 5: Save the document containing the button
        string outputPath = Path.Combine(Environment.CurrentDirectory, "CommandButton.docx");
        doc.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

Uruchomienie programu tworzy plik `CommandButton.docx`. Otwarcie go w Microsoft Word wyświetla klikalny przycisk **Submit**:

![Word document with a Submit command button](/images/command-button.png "Zrzut ekranu dokumentu Word zawierającego przycisk Submit utworzony w C#")

*Tekst alternatywny obrazu (og_image_alt):* `Zrzut ekranu dokumentu Word zawierającego przycisk Submit utworzony w C#`

## Weryfikacja wyniku

1. Uruchom Word i otwórz `CommandButton.docx`.  
2. Powinieneś zobaczyć przycisk oznaczony **Submit** w treści dokumentu.  
3. Najazd kursorem na przycisk wyświetli nazwę `btnSubmit` w panelu **Properties** (zakładka Developer → Properties).  

Jeśli przycisk się nie pojawi, upewnij się, że zakładka **Developer** jest włączona w Wordzie (Plik → Opcje → Dostosuj wstążkę → zaznacz *Developer*). Kontrolki ActiveX są ukryte, gdy zakładka jest wyłączona.

## Obsługa typowych wariantów i przypadków brzegowych

| Sytuacja | Zalecana modyfikacja |
|-----------|------------------------|
| **Inny rozmiar przycisku** | Zmień argumenty szerokości i wysokości w `InsertForms2OleControl`. Na przykład `150, 40` tworzy większy przycisk. |
| **Wiele przycisków** | Wywołuj `InsertForms2OleControl` wielokrotnie, przemieszczając kursor buildera pomiędzy wywołaniami (`builder.Writeln();`). |
| **Przycisk bez ActiveX** | Użyj `InsertFormField`, aby dodać starsze pole formularza (np. pole wyboru), jeśli potrzebna jest kompatybilność ze starszymi wersjami Worda, które blokują ActiveX. |
| **Użycie wieloplatformowe** | Kontrolki ActiveX działają tylko w wersjach Worda na Windows. Dla Maca lub przeglądarek internetowych rozważ wstawienie hiperłącza stylizowanego jako przycisk. |
| **Ostrzeżenia bezpieczeństwa** | Word może wyświetlić komunikat bezpieczeństwa przy otwieraniu dokumentu zawierającego kontrolki ActiveX. Podpisanie dokumentu zaufanym certyfikatem zmniejsza tę niedogodność. |

## Pełny, gotowy do uruchomienia przykład

Poniżej znajduje się kompletny program, który możesz skopiować i wkleić do `Program.cs`. Kompiluje się i uruchamia bez modyfikacji po dodaniu pakietu NuGet Aspose.Words.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing.Forms;

class Program
{
    static void Main()
    {
        // Create a new blank document and a DocumentBuilder to edit it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert an ActiveX CommandButton control (size: 100x30 points)
        Forms2OleControl commandButton = builder.InsertForms2OleControl(
            ControlType.CommandButton, 100, 30);

        // Set the button's name and displayed caption
        commandButton.Name = "btnSubmit";
        commandButton.Caption = "Submit";

        // Save the document containing the button
        string outputPath = Path.Combine(Environment.CurrentDirectory, "CommandButton.docx");
        doc.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

**Oczekiwany wynik w konsoli:**

```
Document saved to C:\Path\To\WordButtonDemo\bin\Debug\net6.0\CommandButton.docx
```

Otwarcie wygenerowanego pliku pokazuje przycisk **Submit** gotowy do interakcji.

## Podsumowanie

Teraz wiesz, jak **utworzyć dokument Word w C#** i **programowo dodać kontrolki przycisków poleceń** przy użyciu Aspose.Words. Proces sprowadza się do zainicjowania `Document`, wstawienia `Forms2OleControl`, skonfigurowania jego właściwości i zapisania pliku. Od tego momentu możesz:

* Dodawać kolejne kontrolki (np. pola wyboru, pola tekstowe) zmieniając `ControlType`.
* Dołączać makra VBA do przycisku w celu własnej logiki.
* Łączyć tę technikę z innymi funkcjami Aspose.Words, takimi jak scalanie korespondencji czy wypełnianie szablonów.

Eksperymentuj z różnymi rozmiarami, podpisami i wieloma przyciskami, aby dopasować rozwiązanie do swojego scenariusza automatyzacji. Powodzenia w kodowaniu!

## Co powinieneś nauczyć się dalej?

Poniższe tutoriale obejmują ściśle powiązane tematy, które rozwijają techniki przedstawione w tym przewodniku. Każdy zasób zawiera kompletne działające przykłady kodu oraz szczegółowe wyjaśnienia, aby pomóc Ci opanować dodatkowe funkcje API i odkrywać alternatywne podejścia w własnych projektach.

- [Create Word Document with Header and Footer Using Aspose.Words](/words/english/net/header-footer-formatting/create-header-footer/)
- [Create Word Document with Aspose.Words for .NET](/words/english/net/add-content-using-document-builder/insert-paragraph/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}