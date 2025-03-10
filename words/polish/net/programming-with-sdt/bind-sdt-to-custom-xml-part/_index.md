---
title: Powiąż SDT z niestandardową częścią XML
linktitle: Powiąż SDT z niestandardową częścią XML
second_title: Aspose.Words API przetwarzania dokumentów
description: Dowiedz się, jak powiązać strukturalne znaczniki dokumentu (SDT) z niestandardowymi elementami XML w dokumentach programu Word za pomocą Aspose.Words dla platformy .NET, korzystając z tego samouczka krok po kroku.
weight: 10
url: /pl/net/programming-with-sdt/bind-sdt-to-custom-xml-part/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Powiąż SDT z niestandardową częścią XML

## Wstęp

Tworzenie dynamicznych dokumentów Word, które wchodzą w interakcję z niestandardowymi danymi XML, może znacznie zwiększyć elastyczność i funkcjonalność Twoich aplikacji. Aspose.Words for .NET zapewnia solidne funkcje wiązania znaczników dokumentu strukturalnego (SDT) z niestandardowymi częściami XML, umożliwiając tworzenie dokumentów, które dynamicznie wyświetlają dane. W tym samouczku przeprowadzimy Cię przez proces wiązania SDT z niestandardową częścią XML krok po kroku. Zanurzmy się!

## Wymagania wstępne

Zanim zaczniemy, upewnij się, że spełnione są następujące wymagania wstępne:

-  Aspose.Words dla .NET: Najnowszą wersję można pobrać ze strony[Aspose.Words dla wydań .NET](https://releases.aspose.com/words/net/).
- Środowisko programistyczne: Visual Studio lub inne zgodne środowisko IDE .NET.
- Podstawowa znajomość języka C#: Znajomość języka programowania C# i platformy .NET.

## Importuj przestrzenie nazw

Aby skutecznie używać Aspose.Words dla .NET, musisz zaimportować niezbędne przestrzenie nazw do swojego projektu. Dodaj następujące dyrektywy using na górze pliku kodu:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Markup;
using Aspose.Words.Saving;
```

Podzielmy proces na łatwe do opanowania kroki, aby łatwiej było go śledzić. Każdy krok obejmie określoną część zadania.

## Krok 1: Zainicjuj dokument

Najpierw musisz utworzyć nowy dokument i skonfigurować środowisko.

```csharp
// Ścieżka do katalogu dokumentów
string dataDir = "YOUR DOCUMENT DIRECTORY";

// Zainicjuj nowy dokument
Document doc = new Document();
```

W tym kroku inicjujemy nowy dokument, który będzie zawierał nasze niestandardowe dane XML i SDT.

## Krok 2: Dodaj niestandardową część XML

Następnie dodajemy do dokumentu niestandardową część XML. Ta część będzie zawierać dane XML, które chcemy powiązać z SDT.

```csharp
// Dodaj niestandardową część XML do dokumentu
CustomXmlPart xmlPart = doc.CustomXmlParts.Add(Guid.NewGuid().ToString("B"), "<root><text>Hello, World!</text></root>");
```

Tutaj tworzymy nową niestandardową część XML z unikalnym identyfikatorem i dodajemy przykładowe dane XML.

## Krok 3: Utwórz znacznik dokumentu strukturalnego (SDT)

Po dodaniu niestandardowej części XML tworzymy SDT w celu wyświetlenia danych XML.

```csharp
//Utwórz znacznik dokumentu strukturalnego (SDT)
StructuredDocumentTag sdt = new StructuredDocumentTag(doc, SdtType.PlainText, MarkupLevel.Block);
doc.FirstSection.Body.AppendChild(sdt);
```

Tworzymy SDT typu PlainText i dołączamy go do pierwszej sekcji treści dokumentu.

## Krok 4: Powiąż SDT z niestandardową częścią XML

Teraz powiążemy SDT z częścią XML niestandardową za pomocą wyrażenia XPath.

```csharp
// Powiąż SDT z niestandardową częścią XML
sdt.XmlMapping.SetMapping(xmlPart, "/root[1]/text[1]", "");
```

 Ten krok mapuje SDT na`<text>` element w`<root>` węzeł naszej niestandardowej części XML.

## Krok 5: Zapisz dokument

Na koniec zapisujemy dokument w podanym katalogu.

```csharp
// Zapisz dokument
doc.Save(dataDir + "WorkingWithSdt.BindSDTtoCustomXmlPart.doc");
```

To polecenie zapisuje dokument z powiązanym SDT w wyznaczonym katalogu.

## Wniosek

Gratulacje! Udało Ci się powiązać SDT z niestandardową częścią XML przy użyciu Aspose.Words dla .NET. Ta potężna funkcja umożliwia tworzenie dynamicznych dokumentów, które można łatwo aktualizować nowymi danymi, po prostu modyfikując zawartość XML. Niezależnie od tego, czy generujesz raporty, tworzysz szablony, czy automatyzujesz przepływy pracy dokumentów, Aspose.Words dla .NET oferuje narzędzia, których potrzebujesz, aby ułatwić i usprawnić swoje zadania.

## Najczęściej zadawane pytania

### Czym jest strukturalny znacznik dokumentu (SDT)?
Strukturalny znacznik dokumentu (SDT) to element kontroli treści w dokumentach programu Word, który można wykorzystać do wiązania dynamicznych danych, dzięki czemu dokumenty stają się interaktywne i oparte na danych.

### Czy mogę powiązać wiele SDT z różnymi częściami XML w jednym dokumencie?
Tak, można powiązać wiele SDT z różnymi częściami XML w tym samym dokumencie, co umożliwia tworzenie złożonych szablonów opartych na danych.

### Jak zaktualizować dane XML w części Custom XML?
 Dane XML można aktualizować, uzyskując dostęp do`CustomXmlPart` obiektu i bezpośrednio modyfikować jego zawartość XML.

### Czy możliwe jest powiązanie SDT z atrybutami XML zamiast z elementami?
Tak, można powiązać SDT z atrybutami XML, określając odpowiednie wyrażenie XPath, które odnosi się do żądanego atrybutu.

### Gdzie mogę znaleźć więcej dokumentacji na temat Aspose.Words dla .NET?
 Pełną dokumentację Aspose.Words dla .NET można znaleźć pod adresem[Dokumentacja Aspose.Words](https://reference.aspose.com/words/net/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
