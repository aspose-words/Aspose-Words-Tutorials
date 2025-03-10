---
title: Zmiana kształtu
linktitle: Zmiana kształtu
second_title: Aspose.Words API przetwarzania dokumentów
description: Dowiedz się, jak obsługiwać zmiany kształtów w dokumentach Word za pomocą Aspose.Words dla .NET dzięki temu kompleksowemu przewodnikowi. Opanuj śledzenie zmian, wstawianie kształtów i wiele więcej.
weight: 10
url: /pl/net/working-with-revisions/shape-revision/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Zmiana kształtu

## Wstęp

Edytowanie dokumentów Word programowo może być zniechęcającym zadaniem, szczególnie jeśli chodzi o obsługę kształtów. Niezależnie od tego, czy tworzysz raporty, projektujesz szablony, czy po prostu automatyzujesz tworzenie dokumentów, możliwość śledzenia i zarządzania rewizjami kształtów jest kluczowa. Aspose.Words dla .NET oferuje potężne API, aby uczynić ten proces płynnym i wydajnym. W tym samouczku zagłębimy się w szczegóły rewizji kształtów w dokumentach Word, zapewniając, że masz narzędzia i wiedzę, aby z łatwością zarządzać swoimi dokumentami.

## Wymagania wstępne

Zanim zagłębimy się w kod, upewnijmy się, że masz wszystko, czego potrzebujesz:

-  Aspose.Words dla .NET: Upewnij się, że masz zainstalowaną bibliotekę Aspose.Words. Możesz[pobierz tutaj](https://releases.aspose.com/words/net/).
- Środowisko programistyczne: Należy skonfigurować środowisko programistyczne, np. Visual Studio.
- Podstawowa znajomość języka C#: Znajomość języka programowania C# i podstawowych koncepcji programowania obiektowego.
- Dokument Word: Dokument Word, z którym możesz pracować, lub możesz go utworzyć podczas kursu.

## Importuj przestrzenie nazw

Najpierw zaimportujmy niezbędne przestrzenie nazw. Zapewnią nam one dostęp do klas i metod wymaganych do obsługi dokumentów i kształtów Worda.

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using Aspose.Words;
using Aspose.Words.Drawing;
```

## Krok 1: Konfigurowanie katalogu dokumentów

Zanim zaczniemy pracować z kształtami, musimy zdefiniować ścieżkę do naszego katalogu dokumentów. To tutaj zapiszemy nasze zmodyfikowane dokumenty.

```csharp
// Ścieżka do katalogu dokumentów.
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## Krok 2: Tworzenie nowego dokumentu

Utwórzmy nowy dokument Word, w którym będziemy wstawiać i modyfikować kształty.

```csharp
Document doc = new Document();
```

## Krok 3: Wstawianie kształtu osadzonego

Zaczniemy od wstawienia kształtu inline do naszego dokumentu bez śledzenia rewizji. Kształt inline to taki, który płynie z tekstem.

```csharp
Shape shape = new Shape(doc, ShapeType.Cube);
shape.WrapType = WrapType.Inline;
shape.Width = 100.0;
shape.Height = 100.0;
doc.FirstSection.Body.FirstParagraph.AppendChild(shape);
```

## Krok 4: Rozpoczęcie śledzenia wersji

Aby śledzić zmiany w naszym dokumencie, musimy włączyć śledzenie rewizji. Jest to niezbędne do identyfikacji modyfikacji wprowadzonych do kształtów.

```csharp
doc.StartTrackRevisions("John Doe");
```

## Krok 5: Wstawianie innego kształtu z poprawkami

Teraz, gdy śledzenie rewizji jest włączone, wstawmy inny kształt. Tym razem wszelkie zmiany będą śledzone.

```csharp
shape = new Shape(doc, ShapeType.Sun);
shape.WrapType = WrapType.Inline;
shape.Width = 100.0;
shape.Height = 100.0;
doc.FirstSection.Body.FirstParagraph.AppendChild(shape);
```

## Krok 6: Pobieranie i modyfikowanie kształtów

Możemy pobrać wszystkie kształty w dokumencie i zmodyfikować je według potrzeb. Tutaj pobierzemy kształty i usuniemy pierwszy.

```csharp
List<Shape> shapes = doc.GetChildNodes(NodeType.Shape, true).Cast<Shape>().ToList();
shapes[0].Remove();
```

## Krok 7: Zapisywanie dokumentu

Po wprowadzeniu zmian musimy zapisać dokument. Dzięki temu wszystkie poprawki i modyfikacje zostaną zapisane.

```csharp
doc.Save(dataDir + "Revision shape.docx");
```

## Krok 8: Obsługa zmian w przesunięciach kształtu

Gdy kształt jest przenoszony, Aspose.Words śledzi to jako rewizję. Oznacza to, że będą dwa wystąpienia kształtu: jedno w oryginalnej lokalizacji i jedno w nowej lokalizacji.

```csharp
doc = new Document(dataDir + "Revision shape.docx");
shapes = doc.GetChildNodes(NodeType.Shape, true).Cast<Shape>().ToList();
```

## Wniosek

I masz to! Udało Ci się nauczyć, jak obsługiwać zmiany kształtu w dokumentach Worda przy użyciu Aspose.Words dla .NET. Niezależnie od tego, czy zarządzasz szablonami dokumentów, automatyzujesz raporty, czy po prostu śledzisz zmiany, te umiejętności są bezcenne. Postępując zgodnie z tym przewodnikiem krok po kroku, nie tylko opanowałeś podstawy, ale także uzyskałeś wgląd w bardziej zaawansowane techniki obsługi dokumentów.

## Najczęściej zadawane pytania

### Czym jest Aspose.Words dla .NET?
Aspose.Words for .NET to zaawansowana biblioteka umożliwiająca programistom tworzenie, modyfikowanie i konwertowanie dokumentów Word programowo przy użyciu języka C#.

### Czy mogę śledzić zmiany wprowadzane w innych elementach dokumentu Word?
Tak, Aspose.Words dla platformy .NET obsługuje śledzenie zmian w różnych elementach, w tym tekście, tabelach i innych.

### Jak mogę otrzymać bezpłatną wersję próbną Aspose.Words dla .NET?
 Możesz otrzymać bezpłatną wersję próbną Aspose.Words dla .NET[Tutaj](https://releases.aspose.com/).

### Czy możliwe jest akceptowanie lub odrzucanie poprawek programowo?
Tak, Aspose.Words dla .NET udostępnia metody umożliwiające programowe akceptowanie lub odrzucanie poprawek.

### Czy mogę używać Aspose.Words dla .NET z innymi językami .NET poza C#?
Oczywiście! Aspose.Words dla .NET można używać z dowolnym językiem .NET, w tym VB.NET i F#.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
