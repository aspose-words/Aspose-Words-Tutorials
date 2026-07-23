---
category: general
date: 2026-07-23
description: tworzenie przycisku w dokumencie Word przy użyciu Aspose.Words – krok
  po kroku przewodnik, jak wstawić przycisk ActiveX CommandButton do pliku .docx.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document button
- ActiveX CommandButton
- DocumentBuilder
- InsertForms2OleControl
- Aspose.Words
language: pl
lastmod: 2026-07-23
og_description: 'Utwórz przycisk dokumentu Word przy użyciu Aspose.Words: dowiedz
  się, jak w ciągu kilku minut osadzić przycisk ActiveX CommandButton w pliku Word.'
og_image_alt: Screenshot of a Word document showing an inserted CommandButton control
og_title: Przycisk tworzenia dokumentu Word – Kompletny przewodnik Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-07-23'
  description: create word document button using Aspose.Words – step‑by‑step guide
    to insert an ActiveX CommandButton into a .docx file.
  headline: create word document button with Aspose.Words – Full Code Example
  type: TechArticle
- description: create word document button using Aspose.Words – step‑by‑step guide
    to insert an ActiveX CommandButton into a .docx file.
  name: create word document button with Aspose.Words – Full Code Example
  steps:
  - name: '**Creates** an OLE object inside the Word file.'
    text: '**Creates** an OLE object inside the Word file.'
  - name: '**Registers** it as an ActiveX CommandButton, which Word will render as
      a clickable UI element.'
    text: '**Registers** it as an ActiveX CommandButton, which Word will render as
      a clickable UI element.'
  - name: '**Positions** it according to the rectangle we supplied.'
    text: '**Positions** it according to the rectangle we supplied.'
  - name: Launch Microsoft Word.
    text: Launch Microsoft Word.
  - name: Navigate to **File → Open** and select `CommandButton.docx`.
    text: Navigate to **File → Open** and select `CommandButton.docx`.
  - name: You should see a rectangular button labeled “CommandButton1”.
    text: You should see a rectangular button labeled “CommandButton1”.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
- ActiveX
- CommandButton
title: przycisk tworzenia dokumentu Word przy użyciu Aspose.Words – pełny przykład
  kodu
url: /pl/net/working-with-oleobjects-and-activex/create-word-document-button-with-aspose-words-full-code-exam/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# przycisk tworzenia dokumentu Word z Aspose.Words – Kompletny przewodnik programistyczny

Kiedykolwiek potrzebowałeś **przycisku tworzenia dokumentu Word**, ale nie wiedziałeś, którego API użyć? Nie jesteś sam — większość programistów napotyka trudności, gdy próbują osadzić interaktywne kontrolki w pliku .docx. Dobra wiadomość? Dzięki Aspose.Words dla .NET możesz wstawić w pełni funkcjonalny przycisk ActiveX CommandButton do dokumentu Word w zaledwie kilku linijkach kodu.

W tym tutorialu przejdziemy przez cały proces: od konfiguracji projektu, inicjalizacji `DocumentBuilder`, wstawienia przycisku metodą `InsertForms2OleControl`, po zapisanie pliku tak, aby Word rozpoznał kontrolkę. Na koniec będziesz mieć gotowy plik Word zawierający klikalny przycisk — bez konieczności używania COM interop.

## Co będzie potrzebne

Zanim zaczniemy, upewnij się, że masz następujące elementy:

- **.NET 6.0** lub nowszy (kod działa także z .NET Framework 4.6+).  
- **Aspose.Words for .NET** pakiet NuGet (wersja 23.9 lub nowsza).  
- Podstawowa znajomość C# (postaramy się, aby składnia była przyjazna początkującym).  
- Visual Studio 2022 lub dowolne inne IDE, którego używasz.

To wszystko — bez dodatkowych odwołań do COM, bez interfejsu Office, tylko czysty kod zarządzany.

---

## Krok 1: Konfiguracja Aspose.Words do **create word document button**

Na początek dodaj pakiet Aspose.Words do swojego projektu:

```bash
dotnet add package Aspose.Words
```

Albo, jeśli używasz interfejsu NuGet w Visual Studio, wyszukaj „Aspose.Words” i kliknij **Install**. Ten jeden wiersz zapewnia dostęp do klas `Document`, `DocumentBuilder` oraz metody `InsertForms2OleControl`, której użyjemy później.

> **Pro tip:** Aktualizuj pakiety NuGet na bieżąco; nowsze wersje często zawierają poprawki błędów związanych z obsługą ActiveX.

---

## Krok 2: Inicjalizacja **DocumentBuilder** dla **ActiveX CommandButton**

Teraz tworzymy nowy dokument Word i uruchamiamy `DocumentBuilder`. Pomyśl o `DocumentBuilder` jako o pędzlu, którym rysujesz zawartość na płótnie.

```csharp
using System;
using System.Drawing;               // For Rectangle
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 2.1: Create a new empty document
        Document document = new Document();

        // Step 2.2: Initialize DocumentBuilder to edit the document
        DocumentBuilder builder = new DocumentBuilder(document);
```

Zauważ, że importujemy `System.Drawing` — struktura `Rectangle` definiuje położenie i rozmiar przycisku. To właśnie tutaj będzie mieszkał **ActiveX CommandButton**.

---

## Krok 3: Użycie **InsertForms2OleControl** do **add a CommandButton**

Oto serce tutorialu: wstawienie samego przycisku. Metoda `InsertForms2OleControl` przyjmuje trzy argumenty — typ kontrolki, `Rectangle` oraz opcjonalnie nazwę. Użyjemy `OleControlType.CommandButton`, aby określić dokładnie tę kontrolkę, której potrzebujemy.

```csharp
        // Step 3: Insert an ActiveX CommandButton at (0,0) with width=100, height=30
        builder.InsertForms2OleControl(
            OleControlType.CommandButton,
            new Rectangle(0, 0, 100, 30));
```

To jedno wywołanie robi wiele:

1. **Tworzy** obiekt OLE wewnątrz pliku Word.  
2. **Rejestruje** go jako ActiveX CommandButton, który Word wyświetli jako klikalny element UI.  
3. **Pozycjonuje** go zgodnie z podanym prostokątem.

Jeśli potrzebujesz zmienić podpis przycisku lub inne właściwości, możesz to zrobić po wstawieniu, odwołując się do podstawowego `OleFormat`. W większości przypadków domyślny podpis („CommandButton1”) jest wystarczający.

---

## Krok 4: Zapis dokumentu Word zawierającego **CommandButton**

Zapisywanie jest proste — wskaż folder, do którego masz prawo zapisu. Rozszerzenie pliku musi być `.docx`, aby przycisk przetrwał cały proces.

```csharp
        // Step 4: Save the document with the embedded button
        string outputPath = @"C:\Temp\CommandButton.docx";
        document.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

Po otwarciu `CommandButton.docx` w Microsoft Word zobaczysz mały przycisk w lewym górnym rogu pierwszej strony. Kliknięcie go nie robi nic (wymagałoby to VBA), ale kontrolka jest w pełni funkcjonalna i może być podłączona później.

> **Dlaczego to działa:** Aspose.Words zapisuje strumień OLE bezpośrednio w pakiecie DOCX, omijając potrzebę generowania kontrolki w czasie działania przez Word. Dzięki temu przycisk pojawia się dokładnie tam, gdzie go umieściliśmy.

---

## Krok 5: Weryfikacja przycisku w Wordzie

Otwórz wygenerowany plik:

1. Uruchom Microsoft Word.  
2. Przejdź do **Plik → Otwórz** i wybierz `CommandButton.docx`.  
3. Powinieneś zobaczyć prostokątny przycisk oznaczony „CommandButton1”.  

Jeśli przycisku nie widać, upewnij się, że **Tryb projektowania** jest włączony (Developer → Design Mode). To przełącza wizualną reprezentację kontrolek ActiveX.

---

## Krok 6: Zaawansowane opcje – Dostosowywanie **ActiveX CommandButton**

Poniżej kilka szybkich poprawek, które mogą się przydać:

| Cel | Fragment kodu |
|------|--------------|
| Zmień podpis | ```csharp<br/>OleFormat ole = builder.CurrentParagraph.Runs[0].OleFormat;<br/>ole.OleControlCaption = "Submit";``` |
| Ustaw nazwę makra (wymaga obsługi makr w Wordzie) | ```csharp<br/>ole.OleControlMacroName = "MyMacro";``` |
| Zmień rozmiar po wstawieniu | ```csharp<br/>builder.MoveToDocumentEnd();<br/>builder.InsertForms2OleControl(OleControlType.CommandButton, new Rectangle(0,0,150,40));``` |

Te fragmenty pokazują elastyczność `InsertForms2OleControl`. Możesz nawet osadzić inne kontrolki ActiveX, takie jak `CheckBox` czy `ListBox`, zamieniając wartość wyliczenia `OleControlType`.

---

## Pełny działający przykład

Poniżej znajduje się kompletny, gotowy do skopiowania program, który **creates a word document button** od podstaw:

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

class CreateWordDocumentButton
{
    static void Main()
    {
        // 1️⃣ Create a new empty document
        Document document = new Document();

        // 2️⃣ Initialize DocumentBuilder – the tool that lets us edit the document
        DocumentBuilder builder = new DocumentBuilder(document);

        // 3️⃣ Insert an ActiveX CommandButton at position (0,0) with size 100x30
        builder.InsertForms2OleControl(
            OleControlType.CommandButton,
            new Rectangle(0, 0, 100, 30));

        // 4️⃣ Save the .docx file – this is where the button lives
        string outputPath = @"C:\Temp\CommandButton.docx";
        document.Save(outputPath);

        Console.WriteLine($"✅ Document with button saved to: {outputPath}");
    }
}
```

**Oczekiwany wynik po uruchomieniu programu:**

```
✅ Document with button saved to: C:\Temp\CommandButton.docx
```

Otwórz powstały plik i zobacz przycisk dokładnie tam, gdzie kod go umieścił.

---

## Częste pułapki i jak ich uniknąć

- **Brak odwołania do `System.Drawing`** – struktura `Rectangle` znajduje się w tej przestrzeni nazw; bez niej kompilator zgłosi błąd.  
- **Używanie starszej wersji Aspose.Words** – wczesne wydania nie obsługiwały w pełni `InsertForms2OleControl`. Zaktualizuj do najnowszej stabilnej wersji.  
- **Zapisywanie jako `.doc` zamiast `.docx`** – strumień OLE jest usuwany w starszym formacie binarnym, co powoduje zniknięcie przycisku.  
- **Uruchamianie na serwerze bez interfejsu graficznego i bez zainstalowanego Worda** – przycisk nadal będzie w pliku, ale nie będziesz mógł go podglądnąć bez Worda. To nie jest problem w automatycznych pipeline’ach generujących dokumenty.

---

## Kolejne kroki – Rozszerzanie przepływu **create word document button**

Teraz, gdy opanowałeś podstawy, rozważ następujące pomysły na wyższy poziom:

- **Dołącz makra VBA** do przycisku, aby realizować własną logikę biznesową.  
- **Generuj wiele przycisków** w pętli, tworząc dynamiczne formularze.  
- **Połącz z Aspose.PDF**, aby wyeksportować ten sam dokument do PDF, zachowując układ wizualny (przycisk stanie się statycznym obrazem w PDF).  
- **


## Co warto nauczyć się dalej?


Poniższe tutoriale obejmują tematy blisko powiązane, które rozwijają techniki przedstawione w tym przewodniku. Każdy zasób zawiera kompletne przykłady kodu oraz szczegółowe wyjaśnienia, aby pomóc Ci opanować dodatkowe funkcje API i odkrywać alternatywne podejścia w własnych projektach.

- [Utwórz dokument Word przy użyciu Aspose.Words dla .NET](/words/english/net/add-content-using-document-builder/insert-paragraph/)
- [Utwórz prostokątny kształt w Wordzie z Aspose.Words – przewodnik krok po kroku](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)
- [Wstaw obraz inline do dokumentu Word przy użyciu Aspose.Words](/words/english/net/add-content-using-document-builder/insert-inline-image/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}