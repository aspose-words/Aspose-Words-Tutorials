---
category: general
date: 2026-09-11
description: Dowiedz się, jak tworzyć forms2olecontrol w kodzie przy użyciu Aspose.Words
  DocumentBuilder. Ten przewodnik krok po kroku obejmuje wstawianie przycisku polecenia
  ActiveX, użycie setOleClassName oraz ustawianie rozmiaru.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create forms2olecontrol in code
- ActiveX command button
- Aspose.Words DocumentBuilder
- setOleClassName method
- Forms2OleControl size
language: pl
lastmod: 2026-09-11
og_description: Utwórz forms2olecontrol w kodzie przy użyciu Aspose.Words. Skorzystaj
  z tego przewodnika, aby wstawić przycisk polecenia ActiveX, ustawić jego nazwę klasy
  i dostosować rozmiar.
og_image_alt: Screenshot of a Word document showing a newly created ActiveX command
  button inserted via code
og_title: Utwórz forms2olecontrol w kodzie – kompletny przewodnik Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-09-11'
  description: Learn how to create forms2olecontrol in code using Aspose.Words DocumentBuilder.
    This step‑by‑step guide covers ActiveX command button insertion, setOleClassName
    usage, and sizing.
  headline: How to create forms2olecontrol in code with Aspose.Words
  type: TechArticle
- description: Learn how to create forms2olecontrol in code using Aspose.Words DocumentBuilder.
    This step‑by‑step guide covers ActiveX command button insertion, setOleClassName
    usage, and sizing.
  name: How to create forms2olecontrol in code with Aspose.Words
  steps:
  - name: Initialise the DocumentBuilder
    text: The `DocumentBuilder` class is the entry point for most document‑generation
      tasks in Aspose.Words. It gives you methods to add text, images, tables, and,
      importantly for this tutorial, OLE controls.
  - name: Insert the Forms2OleControl
    text: The `insertForms2OleControl` method returns a `Forms2OleControl` object.
      This object represents the OLE control placeholder that Word will render as
      an ActiveX button.
  - name: Specify the ActiveX class with setOleClassName
    text: Word needs to know which type of ActiveX control to render. The class name
      for a standard command button is `"Forms.CommandButton.1"`.
  - name: Adjust the Forms2OleControl size
    text: A button that is too small or too large looks unprofessional. You can control
      its dimensions with `setWidth` and `setHeight`.
  - name: Save the document and test
    text: After configuring the control, save the document to a location of your choice.
  - name: When to use Forms2OleControl vs. Content Controls
    text: If you only need simple data entry (e.g., a plain text field), Word’s built‑in
      content controls are lighter weight. Use `Forms2OleControl` when you require
      full ActiveX functionality such as event handling or custom VBA interaction.
  type: HowTo
tags:
- Aspose.Words
- C#
- ActiveX
title: Jak utworzyć forms2olecontrol w kodzie przy użyciu Aspose.Words
url: /pl/java/using-document-elements/how-to-create-forms2olecontrol-in-code-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak utworzyć forms2olecontrol w kodzie przy użyciu Aspose.Words

Jeśli potrzebujesz **utworzyć forms2olecontrol w kodzie**, ten przewodnik pokazuje dokładnie, jak to zrobić przy użyciu API Aspose.Words .NET. Niezależnie od tego, czy automatyzujesz szablon wymagający przycisku ActiveX, czy po prostu chcesz programowo wzbogacić dokument Word, poniższe kroki obejmują wszystko, od wstawienia kontrolki po skonfigurowanie jej wyglądu.

W tym samouczku nauczysz się, jak używać **Aspose.Words DocumentBuilder** do wstawienia **przycisku ActiveX**, ustawienia jego klasy metodą **setOleClassName**, oraz dostosowania **rozmiaru Forms2OleControl**. Nie są wymagane żadne zewnętrzne narzędzia — wystarczy środowisko programistyczne .NET oraz biblioteka Aspose.Words.

## Wymagania wstępne

* .NET 6.0 lub nowszy zainstalowany (kod działa również z .NET Framework 4.7+)
* Najnowsza wersja pakietu NuGet Aspose.Words dla .NET
* Podstawowa znajomość C# oraz koncepcji kontrolek ActiveX w dokumentach Word

Jeśli którekolwiek z powyższych brakuje, zainstaluj pakiet NuGet za pomocą:

```bash
dotnet add package Aspose.Words
```

## Co obejmuje ten samouczek

* Utworzenie instancji `DocumentBuilder`
* Wstawienie `Forms2OleControl` (obiekt bazowy dla przycisku ActiveX)
* Przypisanie prawidłowej nazwy klasy za pomocą `setOleClassName`
* Ustawienie wizualnej szerokości i wysokości przy użyciu właściwości **Forms2OleControl size**
* Zapisanie dokumentu i weryfikacja wyniku

Po zakończeniu przewodnika będziesz mieć w pełni funkcjonalny plik Word zawierający przycisk, który można dalej dostosowywać lub powiązać z makrami VBA.

---

## Jak utworzyć forms2olecontrol w kodzie – krok po kroku

### Krok 1: Inicjalizacja DocumentBuilder

Klasa `DocumentBuilder` jest punktem wejścia dla większości zadań generowania dokumentów w Aspose.Words. Udostępnia metody dodawania tekstu, obrazów, tabel oraz, co istotne w tym samouczku, kontrolek OLE.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create a new empty document
Document doc = new Document();

// Initialise the builder for the document
DocumentBuilder builder = new DocumentBuilder(doc);
```

**Dlaczego to ważne:**  
`DocumentBuilder` utrzymuje bieżącą pozycję kursora w dokumencie. Tworząc go na początku, zapewniasz, że każde późniejsze wstawienie — takie jak **przycisk ActiveX** — pojawi się dokładnie tam, gdzie tego oczekujesz.

### Krok 2: Wstawienie Forms2OleControl

Metoda `insertForms2OleControl` zwraca obiekt `Forms2OleControl`. Obiekt ten reprezentuje miejsce kontrolki OLE, które Word wyświetli jako przycisk ActiveX.

```csharp
// Insert the Forms2OleControl at the current cursor location
Forms2OleControl commandButton = builder.InsertForms2OleControl();
```

**Dlaczego to ważne:**  
Bez tego wywołania nie możesz manipulować właściwościami kontrolki. Zwrócony `Forms2OleControl` zapewnia pełny dostęp do **metody setOleClassName**, atrybutów rozmiaru oraz innych ustawień specyficznych dla OLE.

### Krok 3: Określenie klasy ActiveX za pomocą setOleClassName

Word musi wiedzieć, jaki typ kontrolki ActiveX ma wyświetlić. Nazwa klasy dla standardowego przycisku to `"Forms.CommandButton.1"`.

```csharp
// Tell Word that this OLE control is a CommandButton
commandButton.SetOleClassName("Forms.CommandButton.1");
```

**Dlaczego to ważne:**  
Metoda `setOleClassName` jest mostem pomiędzy ogólnym miejscem OLE a konkretnym **przyciskiem ActiveX**. Użycie nieprawidłowej nazwy klasy skutkuje pustym obiektem lub błędem w czasie wykonywania po otwarciu dokumentu.

### Krok 4: Dostosowanie rozmiaru Forms2OleControl

Przycisk, który jest zbyt mały lub zbyt duży, wygląda nieprofesjonalnie. Możesz kontrolować jego wymiary za pomocą `setWidth` i `setHeight`.

```csharp
// Set the visual dimensions (points) of the button
commandButton.SetWidth(80);   // width in points
commandButton.SetHeight(30);  // height in points
```

**Dlaczego to ważne:**  
Te właściwości tworzą **rozmiar Forms2OleControl**. Wpływają na to, jak przycisk wygląda w interfejsie Word i zapewniają, że podłączone makro ma wystarczający obszar do kliknięcia.

### Krok 5: Zapisz dokument i przetestuj

Po skonfigurowaniu kontrolki zapisz dokument w wybranej lokalizacji.

```csharp
// Save the document as a .docx file
doc.Save("ActiveXButton.docx");
```

Otwórz `ActiveXButton.docx` w programie Microsoft Word. Powinieneś zobaczyć przycisk oznaczony „CommandButton1” (domyślny podpis). Kliknięcie go nie zrobi nic, chyba że dodasz makro VBA, ale sama kontrolka jest w pełni funkcjonalna.

**Oczekiwany wynik:**  

![Dokument Word z wstawionym przyciskiem ActiveX](/images/activeX-button.png "Zrzut ekranu dokumentu Word pokazujący nowo utworzony przycisk ActiveX wstawiony przy pomocy kodu")

*Tekst alternatywny obrazu zawiera główne słowo kluczowe dla dostępności i SEO.*

---

## Zrozumienie klasy ActiveX Forms2OleControl

Klasa `Forms2OleControl` otacza niskopoziomową infrastrukturę OLE, której Word używa do elementów ActiveX. Dziedziczy po `Shape`, co oznacza, że możesz również stosować typowe formatowanie kształtów (np. obramowania, obrót), jeśli jest to potrzebne.

* **ActiveX command button** – Najczęstszy przypadek użycia; możesz powiązać go z makrem za pomocą narzędzi deweloperskich Word.
* **setOleClassName method** – Określa, którą klasę COM Word ładuje; inne prawidłowe wartości to `"Forms.TextBox.1"` i `"Forms.ComboBox.1"`.
* **Forms2OleControl size** – Kontrolowane przez `SetWidth`/`SetHeight`. Metody te przyjmują jednostkę punktów (1 pt = 1/72 in).

### Kiedy używać Forms2OleControl vs. Content Controls

Jeśli potrzebujesz jedynie prostego wprowadzania danych (np. zwykłe pole tekstowe), wbudowane kontrolki treści Worda są lżejsze. Użyj `Forms2OleControl`, gdy wymagana jest pełna funkcjonalność ActiveX, taka jak obsługa zdarzeń lub niestandardowa interakcja z VBA.

---

## Ustawianie dodatkowych właściwości (opcjonalnie)

Chociaż podstawowe kroki wystarczają do **utworzenia forms2olecontrol w kodzie**, często chcesz dopracować wygląd lub zachowanie przycisku.

```csharp
// Change the button caption (requires a VBA macro to read it)
commandButton.SetOleData("Caption", "Submit");

// Disable the button initially
commandButton.SetOleData("Enabled", false);

// Add a tooltip
commandButton.SetOleData("ToolTipText", "Click to submit the form");
```

**Dlaczego to ważne:**  
`SetOleData` pozwala zapisać dowolne wartości właściwości bezpośrednio do strumienia OLE. To najelastyczniejszy sposób dostosowania **przycisku ActiveX** bez użycia VBA.

## Typowe problemy i rozwiązywanie

| Objaw | Prawdopodobna przyczyna | Rozwiązanie |
|--------|--------------|-----|
| Przycisk pojawia się jako szara ramka | Nieprawidłowa nazwa klasy przekazana do `setOleClassName` | Sprawdź, czy ciąg jest dokładnie `"Forms.CommandButton.1"` (uwzględniając wielkość liter) |
| Rozmiar się nie zmienia | Szerokość/Wysokość ustawiono przed wstawieniem kontrolki | Zawsze wywołuj `SetWidth`/`SetHeight` **po** `InsertForms2OleControl` |
| Dokument zgłasza błąd „OLE object not found” przy otwieraniu | Brak licencji Aspose.Words (wersja ewaluacyjna może ograniczać OLE) | Zastosuj ważną licencję lub użyj wersji próbnej z pełnym wsparciem OLE |
| Etykieta przycisku pozostaje „CommandButton1” | `SetOleData` nie użyto lub makro nie odczytuje właściwości | Użyj makra VBA, aby odczytać właściwość `"Caption"` lub ustaw etykietę przez interfejs Word |

## Pełny, gotowy do uruchomienia przykład

Poniżej znajduje się kompletny program konsolowy, który możesz skopiować, wkleić i uruchomić. Demonstruje wszystkie zagadnienia omówione w tym samouczku.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace Forms2OleControlDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // 1. Create a new document and a DocumentBuilder
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 2. Insert the Forms2OleControl (ActiveX placeholder)
            Forms2OleControl commandButton = builder.InsertForms2OleControl();

            // 3. Set the ActiveX class to CommandButton
            commandButton.SetOleClassName("Forms.CommandButton.1");

            // 4. Define the visual size of the button
            commandButton.SetWidth(80);   // 80 points = ~1.11 inches
            commandButton.SetHeight(30);  // 30 points = ~0.42 inches

            // Optional: set a custom caption via OLE data (requires VBA to read)
            commandButton.SetOleData("Caption", "Submit");

            // 5. Save the document
            string outputPath = "ActiveXButton.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

**Wyjaśnienie każdej sekcji**

* **Using directives** – Importuje przestrzeń nazw Aspose.Words wymaganą dla `Document`, `DocumentBuilder` i `Forms2OleControl`.
* **Document creation** – Tworzy pusty plik Word.
* **InsertForms2OleControl** – Umieszcza kontrolkę OLE w bieżącej pozycji kursora buildera.
* **SetOleClassName** – Informuje Word, że kontrolka jest **przyciskiem ActiveX**.
* **SetWidth / SetHeight** – Dostosowuje **rozmiar Forms2OleControl** dla profesjonalnego wyglądu.
* **SetOleData (optional)** – Pokazuje, jak zapisać dodatkowe właściwości, takie jak podpis.
* **Save** – Zapisuje finalny plik `.docx` na dysku.

Uruchom program (`dotnet run`) i otwórz `ActiveXButton.docx`. Powinieneś zobaczyć przycisk, który później możesz połączyć z makrem.

---

## Podsumowanie

Teraz wiesz, jak **utworzyć forms2olecontrol w kodzie** przy użyciu Aspose.Words, od inicjalizacji `DocumentBuilder` po skonfigurowanie **przycisku ActiveX** metodą `setOleClassName` oraz kontrolowanie jego **rozmiaru Forms2OleControl**. To podejście pozwala automatyzować złożone dokumenty Word, osadzać interaktywne elementy UI i utrzymywać całą logikę wewnątrz

## Co powinieneś się nauczyć dalej?

Poniższe samouczki obejmują ściśle powiązane tematy, które rozwijają techniki przedstawione w tym przewodniku. Każdy zasób zawiera kompletne działające przykłady kodu z wyjaśnieniami krok po kroku, aby pomóc Ci opanować dodatkowe funkcje API i odkrywać alternatywne podejścia implementacyjne w własnych projektach.

- [Jak tworzyć pola formularzy i dodawać treść przy użyciu DocumentBuilder w Aspose.Words dla Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Tworzenie grupy kształtów w dokumencie Word przy użyciu Aspose.Words dla .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Tworzenie prostokątnego kształtu w Word przy użyciu Aspose.Words – przewodnik krok po kroku](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}