---
"description": "Dowiedz się, jak czytać właściwości kontrolki ActiveX z plików Word za pomocą Aspose.Words dla .NET w przewodniku krok po kroku. Udoskonal swoje umiejętności automatyzacji dokumentów."
"linktitle": "Odczyt właściwości Active XControl z pliku Word"
"second_title": "Aspose.Words API przetwarzania dokumentów"
"title": "Odczyt właściwości Active XControl z pliku Word"
"url": "/pl/net/working-with-oleobjects-and-activex/read-active-xcontrol-properties/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Odczyt właściwości Active XControl z pliku Word

## Wstęp

dzisiejszej erze cyfrowej automatyzacja jest kluczem do zwiększenia produktywności. Jeśli pracujesz z dokumentami Word, które zawierają kontrolki ActiveX, możesz potrzebować odczytać ich właściwości w różnych celach. Kontrolki ActiveX, takie jak pola wyboru i przyciski, mogą przechowywać ważne dane. Używając Aspose.Words dla .NET, możesz wydajnie wyodrębniać i manipulować tymi danymi programowo.

## Wymagania wstępne

Zanim zaczniemy, upewnij się, że masz następujące rzeczy:

1. Biblioteka Aspose.Words dla .NET: Można ją pobrać ze strony [Tutaj](https://releases.aspose.com/words/net/).
2. Visual Studio lub dowolne środowisko IDE języka C#: do pisania i wykonywania kodu.
3. Dokument programu Word zawierający kontrolki ActiveX, na przykład „Kontrolki ActiveX.docx”.
4. Podstawowa znajomość języka C#: Znajomość programowania w języku C# jest konieczna, aby móc uczestniczyć w zajęciach.

## Importuj przestrzenie nazw

Najpierw zaimportujmy niezbędne przestrzenie nazw do pracy z Aspose.Words dla .NET.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Ole;
using System;
```

## Krok 1: Załaduj dokument Word

Na początek musisz załadować dokument Word zawierający kontrolki ActiveX.

```csharp
// Ścieżka do katalogu dokumentów
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "ActiveX controls.docx");
```

## Krok 2: Zainicjuj ciąg, aby zachować właściwości

Następnie zainicjuj pusty ciąg, aby zapisać właściwości kontrolek ActiveX.

```csharp
string properties = "";
```

## Krok 3: Przejrzyj kształty w dokumencie

Musimy przejść przez wszystkie kształty w dokumencie, aby znaleźć kontrolki ActiveX.

```csharp
foreach (Shape shape in doc.GetChildNodes(NodeType.Shape, true))
{
    if (shape.OleFormat is null) continue;
    
    OleControl oleControl = shape.OleFormat.OleControl;
    if (oleControl.IsForms2OleControl)
    {
        // Przetwórz kontrolkę ActiveX
    }
}
```

## Krok 4: Wyodrębnij właściwości z kontrolek ActiveX

W pętli sprawdź, czy kontrolka jest Forms2OleControl. Jeśli tak, rzuć ją i wyodrębnij właściwości.

```csharp
Forms2OleControl checkBox = (Forms2OleControl) oleControl;
properties += "\nCaption: " + checkBox.Caption;
properties += "\nValue: " + checkBox.Value;
properties += "\nEnabled: " + checkBox.Enabled;
properties += "\nType: " + checkBox.Type;

if (checkBox.ChildNodes != null)
{
    properties += "\nChildNodes: " + checkBox.ChildNodes;
}

properties += "\n";
```

## Krok 5: Zlicz całkowitą liczbę kontrolek ActiveX

Po przejrzeniu wszystkich kształtów należy policzyć całkowitą liczbę znalezionych kontrolek ActiveX.

```csharp
properties += "\nTotal ActiveX Controls found: " + doc.GetChildNodes(NodeType.Shape, true).Count;
```

## Krok 6: Wyświetl właściwości

Na koniec wydrukuj wyodrębnione właściwości na konsoli.

```csharp
Console.WriteLine("\n" + properties);
```

## Wniosek

masz to! Udało Ci się nauczyć, jak odczytywać właściwości kontrolki ActiveX z dokumentu Word przy użyciu Aspose.Words dla .NET. Ten samouczek obejmował ładowanie dokumentu, iterowanie po kształtach i wyodrębnianie właściwości z kontrolek ActiveX. Wykonując te kroki, możesz zautomatyzować wyodrębnianie ważnych danych z dokumentów Word, zwiększając wydajność przepływu pracy.

## Najczęściej zadawane pytania

### Czym są kontrolki ActiveX w dokumentach Word?
Kontrolki ActiveX to interaktywne obiekty osadzone w dokumentach programu Word, takie jak pola wyboru, przyciski i pola tekstowe, służące do tworzenia formularzy i automatyzowania zadań.

### Czy mogę modyfikować właściwości kontrolek ActiveX za pomocą Aspose.Words dla .NET?
Tak, Aspose.Words dla .NET umożliwia programową modyfikację właściwości kontrolek ActiveX.

### Czy korzystanie z Aspose.Words dla .NET jest bezpłatne?
Aspose.Words for .NET oferuje bezpłatną wersję próbną, ale musisz kupić licencję, aby móc dalej korzystać z programu. Możesz otrzymać bezpłatną wersję próbną [Tutaj](https://releases.aspose.com/).

### Czy mogę używać Aspose.Words dla .NET z innymi językami .NET poza C#?
Tak, Aspose.Words dla .NET można używać z dowolnym językiem .NET, w tym VB.NET i F#.

### Gdzie mogę znaleźć więcej dokumentacji na temat Aspose.Words dla .NET?
Szczegółową dokumentację można znaleźć [Tutaj](https://reference.aspose.com/words/net/).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}