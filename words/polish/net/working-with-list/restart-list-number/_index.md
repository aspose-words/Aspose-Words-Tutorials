---
"description": "Dowiedz się, jak ponownie uruchomić numery list w dokumentach Word za pomocą Aspose.Words dla .NET. Ten szczegółowy, 2000-wyrazowy przewodnik obejmuje wszystko, co musisz wiedzieć, od konfiguracji po zaawansowaną personalizację."
"linktitle": "Numer listy ponownego uruchomienia"
"second_title": "Aspose.Words API przetwarzania dokumentów"
"title": "Numer listy ponownego uruchomienia"
"url": "/pl/net/working-with-list/restart-list-number/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Numer listy ponownego uruchomienia

## Wstęp

Chcesz opanować sztukę manipulacji listami w dokumentach Worda przy użyciu Aspose.Words dla .NET? Cóż, jesteś we właściwym miejscu! W tym samouczku zagłębimy się w ponowne uruchamianie numerów list, sprytną funkcję, która przeniesie Twoje umiejętności automatyzacji dokumentów na wyższy poziom. Zapnij pasy i zaczynajmy!

## Wymagania wstępne

Zanim przejdziemy do kodu, upewnijmy się, że masz wszystko, czego potrzebujesz:

1. Aspose.Words dla .NET: Musisz mieć zainstalowany Aspose.Words dla .NET. Jeśli jeszcze go nie zainstalowałeś, możesz [pobierz tutaj](https://releases.aspose.com/words/net/).
2. Środowisko programistyczne: Upewnij się, że masz odpowiednie środowisko programistyczne, np. Visual Studio.
3. Podstawowa znajomość języka C#: Podstawowa znajomość języka C# ułatwi Ci korzystanie z samouczka.

## Importuj przestrzenie nazw

Po pierwsze, zaimportujmy niezbędne przestrzenie nazw. Są one kluczowe dla dostępu do funkcji Aspose.Words.

```csharp
using Aspose.Words;
using Aspose.Words.Lists;
using System.Drawing;
```

Teraz podzielmy proces na łatwe do naśladowania kroki. Omówimy wszystko, od tworzenia listy po ponowne jej numerowanie.

## Krok 1: Skonfiguruj swój dokument i kreator

Zanim zaczniesz manipulować listami, potrzebujesz dokumentu i DocumentBuildera. DocumentBuilder to narzędzie, którego używasz do dodawania treści do dokumentu.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Krok 2: Utwórz i dostosuj swoją pierwszą listę

Następnie utworzymy listę na podstawie szablonu i dostosujemy jej wygląd. W tym przykładzie używamy formatu liczb arabskich z nawiasami.

```csharp
List list1 = doc.Lists.Add(ListTemplate.NumberArabicParenthesis);
list1.ListLevels[0].Font.Color = Color.Red;
list1.ListLevels[0].Alignment = ListLevelAlignment.Right;
```

Tutaj ustawiliśmy kolor czcionki na czerwony i wyrównaliśmy tekst do prawej.

## Krok 3: Dodaj elementy do swojej pierwszej listy

Mając gotową listę, czas dodać kilka elementów. DocumentBuilder `ListFormat.List` Właściwość ta pomaga w zastosowaniu formatu listy do tekstu.

```csharp
builder.Writeln("List 1 starts below:");
builder.ListFormat.List = list1;
builder.Writeln("Item 1");
builder.Writeln("Item 2");
builder.ListFormat.RemoveNumbers();
```

## Krok 4: Uruchom ponownie numerację listy

Aby ponownie użyć listy i ponownie uruchomić jej numerację, musisz utworzyć kopię oryginalnej listy. Pozwala to na niezależną modyfikację nowej listy.

```csharp
List list2 = doc.Lists.AddCopy(list1);
list2.ListLevels[0].StartAt = 10;
```

W tym przykładzie nowa lista zaczyna się od numeru 10.

## Krok 5: Dodaj elementy do nowej listy

Tak jak poprzednio, dodaj elementy do swojej nowej listy. To pokazuje, że lista jest restartowana od określonej liczby.

```csharp
builder.Writeln("List 2 starts below:");
builder.ListFormat.List = list2;
builder.Writeln("Item 1");
builder.Writeln("Item 2");
builder.ListFormat.RemoveNumbers();
```

## Krok 6: Zapisz swój dokument

Na koniec zapisz dokument w wybranym katalogu.

```csharp
builder.Document.Save(dataDir + "WorkingWithList.RestartListNumber.docx");
```

## Wniosek

Ponowne uruchamianie numerów list w dokumentach Word przy użyciu Aspose.Words dla .NET jest proste i niezwykle przydatne. Niezależnie od tego, czy generujesz raporty, tworzysz ustrukturyzowane dokumenty, czy po prostu potrzebujesz lepszej kontroli nad listami, ta technika jest dla Ciebie.

## Najczęściej zadawane pytania

### Czy mogę używać innych szablonów list oprócz NumberArabicParenthesis?

Oczywiście! Aspose.Words oferuje różne szablony list, takie jak punkty, litery, cyfry rzymskie i inne. Możesz wybrać ten, który najlepiej odpowiada Twoim potrzebom.

### Jak zmienić poziom listy?

Poziom listy można zmienić, modyfikując `ListLevels` nieruchomość. Na przykład, `list1.ListLevels[1]` odnosiłoby się do drugiego poziomu listy.

### Czy mogę rozpocząć numerację od nowa od dowolnego numeru?

Tak, możesz ustawić liczbę początkową na dowolną wartość całkowitą za pomocą `StartAt` Właściwość poziomu listy.

### Czy możliwe jest zastosowanie różnego formatowania dla różnych poziomów listy?

Rzeczywiście! Każdy poziom listy może mieć własne ustawienia formatowania, takie jak czcionka, wyrównanie i styl numeracji.

### Co zrobić, jeśli chcę kontynuować numerację z poprzedniej listy, zamiast zaczynać ją od nowa?

Jeśli chcesz kontynuować numerowanie, nie musisz tworzyć kopii listy. Po prostu kontynuuj dodawanie elementów do oryginalnej listy.





{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}