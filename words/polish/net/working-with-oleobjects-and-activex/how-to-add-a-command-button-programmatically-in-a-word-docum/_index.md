---
category: general
date: 2026-10-13
description: Dowiedz się, jak dodać przycisk polecenia programowo przy użyciu Aspose.Words.
  Ten przewodnik pokazuje również, jak utworzyć przycisk w dokumencie Word z pełnym
  kodem C#.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- add command button programmatically
- create word document button
language: pl
lastmod: 2026-10-13
og_description: Dodaj przycisk polecenia programowo do dokumentu Word przy użyciu
  Aspose.Words. Skorzystaj z tego pełnego samouczka, aby stworzyć przycisk w dokumencie
  Word w C#.
og_image_alt: Screenshot of a Word document with a command button inserted programmatically
og_title: Dodaj przycisk polecenia programowo do dokumentu Word – przewodnik krok
  po kroku
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Learn how to add a command button programmatically using Aspose.Words.
    This guide also shows how to create a Word document button with full C# code.
  headline: How to add a command button programmatically in a Word document
  type: TechArticle
- description: Learn how to add a command button programmatically using Aspose.Words.
    This guide also shows how to create a Word document button with full C# code.
  name: How to add a command button programmatically in a Word document
  steps:
  - name: 'Create a new console project:'
    text: 'Create a new console project:'
  - name: 'Add the Aspose.Words NuGet package:'
    text: 'Add the Aspose.Words NuGet package:'
  - name: Open **Program.cs** and replace its content with the scaffold shown in the
      next steps.
    text: Open **Program.cs** and replace its content with the scaffold shown in the
      next steps.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: Jak programowo dodać przycisk polecenia w dokumencie Word
url: /pl/net/working-with-oleobjects-and-activex/how-to-add-a-command-button-programmatically-in-a-word-docum/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak dodać przycisk polecenia programowo w dokumencie Word  

Jeśli potrzebujesz **dodać przycisk polecenia programowo**, Aspose.Words udostępnia czyste API, które pozwala osadzać kontrolki formularzy OLE bezpośrednio w pliku .docx. Ten samouczek przeprowadzi Cię przez każdy krok niezbędny do **utworzenia przycisku w dokumencie Word**, który zachowuje się jak zwykły przycisk formularza po otwarciu dokumentu w Microsoft Word.  

Nauczysz się, jak skonfigurować środowisko programistyczne, wstawić przycisk, skonfigurować jego właściwości i zweryfikować wynik. Nie są wymagane żadne zewnętrzne narzędzia — wystarczy projekt .NET oraz biblioteka Aspose.Words for .NET.  

## Wymagania wstępne  

Zanim rozpoczniesz, upewnij się, że masz:  

* .NET 6.0 SDK lub nowszy zainstalowany.  
* Aktualną wersję Aspose.Words for .NET (przykłady używają 23.12, ale działa każda wersja 22.x+).  
* IDE, takie jak Visual Studio 2022 lub Visual Studio Code.  

Kod działa na Windows, macOS i Linux, ponieważ Aspose.Words jest niezależny od platformy.  

## Krok 1: Skonfiguruj projekt i odwołanie do Aspose.Words  

1. Utwórz nowy projekt konsolowy:  

   ```bash
   dotnet new console -n WordButtonDemo
   cd WordButtonDemo
   ```  

2. Dodaj pakiet NuGet Aspose.Words:  

   ```bash
   dotnet add package Aspose.Words
   ```  

3. Otwórz **Program.cs** i zamień jego zawartość na szkielet pokazany w kolejnych krokach.  

Ustawienie projektu w ten sposób zapewnia, że kompilator może odnaleźć przestrzenie nazw `Aspose.Words` i `Aspose.Words.Drawing.Forms` wymagane dla kontrolek formularzy.  

## Krok 2: Zainicjuj pusty dokument i DocumentBuilder  

Klasa `Document` reprezentuje cały plik Word, natomiast `DocumentBuilder` udostępnia płynne API do dodawania treści.  

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Forms;
using System.Drawing;   // required for RectangleF

// Create an empty document.
Document doc = new Document();

// Create a builder linked to the document.
DocumentBuilder builder = new DocumentBuilder(doc);
```  

*Dlaczego ten krok ma znaczenie* – Bez `DocumentBuilder` nie możesz precyzyjnie umieścić przycisku na stronie. Builder respektuje bieżącą pozycję kursora, co ułatwia późniejsze wstawianie wielu kontrolek.  

## Krok 3: Wstaw kontrolkę OLE przycisku polecenia  

Aspose.Words traktuje przycisk polecenia jako kontrolkę OLE typu `ControlType.CommandButton`. Określasz jego położenie i rozmiar za pomocą `RectangleF` mierzonego w punktach (1 punkt = 1/72 cala).  

```csharp
// Define the button rectangle: X=100, Y=150, Width=120, Height=30 (points)
RectangleF buttonRect = new RectangleF(100, 150, 120, 30);

// Insert the command button at the current cursor position.
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    ControlType.CommandButton,
    buttonRect);
```  

**Kluczowe punkty**  

* Początek prostokąta (X, Y) jest względem lewego górnego rogu strony.  
* Zmiana `Width` lub `Height` modyfikuje wizualny rozmiar przycisku.  
* `InsertForms2OleControl` zwraca obiekt `Forms2OleControl`, który możesz dalej konfigurować.  

## Krok 4: Skonfiguruj nazwę i etykietę przycisku  

**Nazwa** jest używana przez silnik makr Worda do identyfikacji kontrolki, natomiast **etykieta** (caption) to tekst widziany przez użytkownika.  

```csharp
// Set a unique identifier for the button.
commandButton.Name = "cmdSubmit";

// Set the text displayed on the button.
commandButton.Caption = "Submit";
```  

Jeśli planujesz później dodać makra VBA, użyj opisowej nazwy, ponieważ rejestrator makr Worda odwołuje się do tej właściwości.  

## Krok 5: (Opcjonalnie) Zapisz dokument i zweryfikuj wynik  

Zapisanie pliku pozwala otworzyć go w Microsoft Word, aby potwierdzić, że przycisk się pojawia i działa.  

```csharp
// Save the document to the output folder.
string outputPath = Path.Combine(Environment.CurrentDirectory, "CommandButtonDemo.docx");
doc.Save(outputPath);

Console.WriteLine($"Document saved to: {outputPath}");
```  

Po otwarciu *CommandButtonDemo.docx* w Wordzie powinieneś zobaczyć przycisk oznaczony **Submit** umieszczony w przybliżeniu 1,4 cala od lewego marginesu i 2,1 cala od górnej krawędzi strony. Kliknięcie przycisku nie robi nic domyślnie, ponieważ nie jest dołączone żadne makro, ale kontrolka wizualna jest w pełni funkcjonalna.  

## Krok 6: Przypadki brzegowe i typowe pułapki  

| Situation | What to watch for | Recommended fix |
|-----------|-------------------|-----------------|
| **Przycisk zachodzi na istniejący tekst** | Prostokąt może przecinać akapit, powodując problemy z układem. | Wstaw przycisk po wywołaniu `builder.Writeln()`, aby przenieść kursor do nowej linii, lub dostosuj współrzędną `Y`. |
| **Dokument otwiera się z ostrzeżeniem** | Niektóre wersje Worda oznaczają kontrolki OLE, które nie mają powiązanego programu. | Upewnij się, że typ kontrolki to `CommandButton`; Word traktuje ją jako standardowy element formularza i nie wymaga zewnętrznego programu. |
| **Uruchamianie na Linuksie w środowisku bez interfejsu graficznego** | Word nie może być uruchomiony do testowania interfejsu, ale plik pozostaje prawidłowy. | Użyj testu jednostkowego, który odczytuje właściwości kontrolki (`commandButton.Name`, `commandButton.Caption`), aby zweryfikować ich poprawne ustawienie. |
| **Wymagane wiele przycisków** | Ponowne użycie tego samego `DocumentBuilder` bez przesuwania kursora dodaje przycisk na wierzchu poprzedniego. | Wywołaj `builder.MoveToDocumentEnd()` lub dostosuj wartość `Y` prostokąta przed każdym wstawieniem. |

Rozwiązywanie tych przypadków brzegowych na wczesnym etapie oszczędza czas przy skalowaniu rozwiązania do pełnych formularzy z dziesiątkami kontrolek.  

## Krok 7: Pełny, gotowy do uruchomienia przykład  

Poniżej znajduje się samodzielny program, który możesz skopiować, wkleić i uruchomić bez modyfikacji (poza przywróceniem pakietów NuGet).  

```csharp
using System;
using System.IO;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing.Forms;

namespace WordButtonDemo
{
    class Program
    {
        static void Main()
        {
            // 1. Create a new empty document.
            Document doc = new Document();

            // 2. Create a DocumentBuilder to work with the document.
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 3. Define the button rectangle (position + size).
            RectangleF buttonRect = new RectangleF(100, 150, 120, 30);

            // 4. Insert the command button OLE control.
            Forms2OleControl commandButton = builder.InsertForms2OleControl(
                ControlType.CommandButton,
                buttonRect);

            // 5. Set identifying properties.
            commandButton.Name = "cmdSubmit";
            commandButton.Caption = "Submit";

            // 6. Save the document.
            string outputPath = Path.Combine(
                Environment.CurrentDirectory,
                "CommandButtonDemo.docx");
            doc.Save(outputPath);

            Console.WriteLine($"Document saved to: {outputPath}");
        }
    }
}
```

**Oczekiwany wynik**  

Uruchomienie programu wypisuje ścieżkę podobną do:  

```
Document saved to: C:\Path\To\WordButtonDemo\CommandButtonDemo.docx
```  

Otwarcie wygenerowanego *CommandButtonDemo.docx* pokazuje pojedynczy przycisk **Submit** umieszczony w współrzędnych określonych w kodzie. Nie pojawiają się dodatkowe elementy UI, co potwierdza, że proces **add command button programmatically** zakończył się sukcesem.  

## Zakończenie  

Teraz wiesz, jak **dodać przycisk polecenia programowo** do dokumentu Word przy użyciu Aspose.Words, a także rozumiesz, jak **utworzyć przycisk w dokumencie Word**, który później można podłączyć do makr VBA lub zewnętrznych narzędzi automatyzacji. Proces polega na zainicjowaniu dokumentu, wstawieniu kontrolki OLE `CommandButton`, skonfigurowaniu jej właściwości i zapisaniu pliku.  

Od tego momentu możesz:  

* Dodać więcej kontrolek (pola wyboru, pola tekstowe) powtarzając krok 3 z różnymi wartościami `ControlType`.  
* Dołączyć makra VBA do przycisku, aby wykonywać akcje takie jak zapisywanie formularza lub wysyłanie e‑maila.  
* Generować całe formularze dynamicznie, iterując po kolekcji definicji pól opartych na danych.  

Eksperymentuj z współrzędnymi prostokąta i etykietą przycisku, aby dopasować je do projektu UI. Powodzenia w kodowaniu!  

## Co powinieneś nauczyć się dalej?

Poniższe samouczki obejmują ściśle powiązane tematy, które rozwijają techniki przedstawione w tym przewodniku. Każdy zasób zawiera kompletne działające przykłady kodu z wyjaśnieniami krok po kroku, aby pomóc Ci opanować dodatkowe funkcje API i odkrywać alternatywne podejścia implementacyjne w własnych projektach.

- [Dodaj pole formularza Combo Box do dokumentu Word przy użyciu Aspose.Words for .NET](/words/english/net/add-content-using-documentbuilder/insert-combo-box/)
- [Dodaj pole formularza Check Box do dokumentu Word przy użyciu Aspose.Words for .NET](/words/english/net/add-content-using-documentbuilder/insert-check-box/)
- [Utwórz pusty dokument Word przy użyciu Aspose.Words – przewodnik krok po kroku](/words/english/net/programming-with-shapes/create-blank-word-document-with-aspose-words-step-by-step-gu/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}