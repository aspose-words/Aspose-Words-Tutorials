---
title: Zachowaj numerację źródłową
linktitle: Zachowaj numerację źródłową
second_title: Aspose.Words API przetwarzania dokumentów
description: Dowiedz się, jak importować dokumenty, zachowując formatowanie, korzystając z Aspose.Words dla .NET. Przewodnik krok po kroku z przykładami kodu.
weight: 10
url: /pl/net/join-and-append-documents/keep-source-numbering/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Zachowaj numerację źródłową

## Wstęp

 Podczas pracy z Aspose.Words dla .NET można sprawnie importować dokumenty z jednego źródła do drugiego, zachowując przy tym formatowanie, korzystając z`NodeImporter` klasa. Ten samouczek przeprowadzi Cię przez proces krok po kroku.

## Wymagania wstępne

Przed rozpoczęciem upewnij się, że masz następujące rzeczy:
- Na Twoim komputerze zainstalowano program Visual Studio.
-  Aspose.Words dla .NET zainstalowany. Jeśli nie, pobierz go z[Tutaj](https://releases.aspose.com/words/net/).
- Podstawowa znajomość programowania w języku C# i .NET.

## Importuj przestrzenie nazw

Najpierw uwzględnij w swoim projekcie niezbędne przestrzenie nazw:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Tables;
```

## Krok 1: Skonfiguruj swój projekt

Zacznij od utworzenia nowego projektu C# w programie Visual Studio i zainstaluj Aspose.Words za pomocą Menedżera pakietów NuGet.

## Krok 2: Zainicjuj dokumenty
Utwórz wystąpienia źródła (`srcDoc`) i miejsce docelowe (`dstDoc`) dokumentów.

```csharp
// Ścieżka do katalogu dokumentów
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document srcDoc = new Document(dataDir + "Document source.docx");
Document dstDoc = new Document(dataDir + "Northwind traders.docx");
```

## Krok 3: Skonfiguruj opcje importu
Skonfiguruj opcje importu, aby zachować formatowanie źródłowe, łącznie z numerowanymi akapitami.

```csharp
ImportFormatOptions importFormatOptions = new ImportFormatOptions { KeepSourceNumbering = true };
NodeImporter importer = new NodeImporter(srcDoc, dstDoc, ImportFormatMode.KeepSourceFormatting,
	importFormatOptions);
```

## Krok 4: Importuj akapity
Przejrzyj akapity w dokumencie źródłowym i zaimportuj je do dokumentu docelowego.

```csharp
ParagraphCollection srcParas = srcDoc.FirstSection.Body.Paragraphs;
foreach (Paragraph srcPara in srcParas)
{
    Node importedNode = importer.ImportNode(srcPara, false);
    dstDoc.FirstSection.Body.AppendChild(importedNode);
}
```

## Krok 5: Zapisz dokument
Zapisz scalony dokument w wybranej lokalizacji.

```csharp
dstDoc.Save(dataDir + "JoinAndAppendDocuments.KeepSourceNumbering.docx");
```

## Wniosek

 Podsumowując, używanie Aspose.Words dla .NET do importowania dokumentów z zachowaniem formatowania jest proste dzięki`NodeImporter` Klasa. Ta metoda zapewnia, że Twoje dokumenty zachowają swój oryginalny wygląd i strukturę bezproblemowo.

## Najczęściej zadawane pytania

### Czy mogę importować dokumenty z różnymi stylami formatowania?
 Tak,`NodeImporter` Klasa obsługuje importowanie dokumentów o różnych stylach formatowania.

### Co zrobić, jeśli moje dokumenty zawierają skomplikowane tabele i obrazy?
Aspose.Words dla platformy .NET obsługuje złożone struktury, takie jak tabele i obrazy, podczas operacji importowania.

### Czy Aspose.Words jest kompatybilny ze wszystkimi wersjami .NET?
Aspose.Words obsługuje wersje .NET Framework i .NET Core, co umożliwia bezproblemową integrację.

### Jak poradzić sobie z błędami podczas importowania dokumentów?
Użyj bloków try-catch do obsługi wyjątków, które mogą wystąpić w trakcie procesu importowania.

### Gdzie mogę znaleźć bardziej szczegółową dokumentację dotyczącą Aspose.Words dla .NET?
 Odwiedź[dokumentacja](https://reference.aspose.com/words/net/) aby uzyskać kompleksowe przewodniki i odniesienia do API.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
