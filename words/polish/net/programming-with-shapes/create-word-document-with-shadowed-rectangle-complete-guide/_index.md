---
category: general
date: 2026-04-21
description: Utwórz dokument Word ze stylizowanym prostokątem i cieniem. Dowiedz się,
  jak dodać cień, wstawić kształt prostokąta, ustawić kolor cienia i wiele więcej
  w C#.
draft: false
keywords:
- create word document
- how to add shadow
- insert rectangle shape
- create rectangle in word
- set shadow color
language: pl
og_description: Utwórz dokument Word i dodaj prostokątny kształt z cieniem w C#. Skorzystaj
  z tego przewodnika, aby łatwo ustawić kolor cienia, rozmycie i przesunięcia.
og_title: Utwórz dokument Word z prostokątem w cieniu – krok po kroku
tags:
- Aspose.Words
- C#
- Document Automation
title: Tworzenie dokumentu Word z prostokątem z cieniem – kompletny przewodnik
url: /pl/net/programming-with-shapes/create-word-document-with-shadowed-rectangle-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Utwórz dokument Word z prostokątem z cieniem – Kompletny przewodnik

Kiedykolwiek potrzebowałeś **utworzyć dokument Word**, który wygląda nieco bardziej dopracowanie niż zwykła strona tekstu? Może tworzysz szablon raportu lub ulotkę i prosty prostokąt z subtelnym cieniem będzie idealnym rozwiązaniem. W tym samouczku przeprowadzimy Cię krok po kroku przez to, jak wstawić kształt prostokąta, włączyć cień i dostosować jego kolor, rozmycie oraz przesunięcia — wszystko przy użyciu C# i Aspose.Words.

Omówimy także **jak dodać cień** w sposób działający zarówno w Word 2016, 2019, jak i najnowszej wersji Office 365. Na koniec będziesz mieć gotowy do zapisania plik *.docx* prezentujący ładnie zacieniony prostokąt oraz zrozumiesz „dlaczego” każdej ustawionej właściwości.

## Wymagania wstępne

- .NET 6 (lub dowolna nowsza wersja .NET Framework)  
- Pakiet NuGet Aspose.Words for .NET (`Install-Package Aspose.Words`)  
- Podstawowa znajomość składni C#  
- IDE, takie jak Visual Studio (ale wystarczy dowolny edytor)

Nie są potrzebne dodatkowe biblioteki; wszystko, czego potrzebujesz, znajduje się w Aspose.Words.

## Krok 1 – Inicjalizacja dokumentu i buildera (Utwórz dokument Word)

Aby **utworzyć dokument Word** programowo, zaczynasz od klasy `Document`. `DocumentBuilder` jest Twoim pędzlem; pozwala dodawać tekst, kształty i inne elementy.

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

class ShadowRectangleDemo
{
    static void Main()
    {
        // Step 1: Create a new blank document and a builder to edit it
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);
```

*Dlaczego to ważne:* Obiekt `Document` reprezentuje cały plik .docx. Bez niego nie masz gdzie podłączyć prostokąta ani jego cienia.

## Krok 2 – Wstawienie kształtu prostokąta (Wstaw kształt prostokąta)

Teraz faktycznie **wstawiamy kształt prostokąta**. Metoda `InsertShape` przyjmuje wyliczenie `ShapeType` oraz szerokość i wysokość w punktach.

```csharp
        // Step 2: Insert a rectangle shape of the desired size (200x100 points)
        Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 200, 100);
```

*Wskazówka:* 1 punkt ≈ 1/72 cala, więc 200 pt to w przybliżeniu 2,78 cala szerokości. Dostosuj te liczby do swojego układu.

## Krok 3 – Włączenie cienia (Jak dodać cień)

Cienie są domyślnie wyłączone. Przełącz flagę `Visible`, aby go włączyć.

```csharp
        // Step 3: Turn on the shadow for the shape
        rectangle.ShadowFormat.Visible = true;
```

*Co się dzieje?* Gdy `Visible` jest ustawione na `true`, Word renderuje cień oparty na pozostałych właściwościach, które ustawisz później.

## Krok 4 – Dostosowanie wyglądu cienia (Ustaw kolor cienia, rozmycie, przesunięcia)

Tutaj **ustawiamy kolor cienia**, promień rozmycia oraz przesunięcia X/Y. Śmiało eksperymentuj — różne wartości dają miękkie poświaty, głębokie cienie lub nawet efekt „unoszenia się”.

```csharp
        // Step 4: Define the shadow appearance – colour, blur radius and offsets
        rectangle.ShadowFormat.Color = Color.Gray;   // shadow colour
        rectangle.ShadowFormat.Blur = 5.0;           // blur radius (points)
        rectangle.ShadowFormat.OffsetX = 4.0;        // horizontal offset (points)
        rectangle.ShadowFormat.OffsetY = 4.0;        // vertical offset (points)
```

*Dlaczego te liczby?* Rozmycie 5 pt daje delikatnie piórkowany brzeg, a przesunięcie 4 pt przesuwa cień w dół i w prawo, imitując źródło światła z górnego lewego rogu. Zmien `Color` na `Color.Black`, aby uzyskać mocniejszy kontrast, lub użyj `Color.FromArgb(128, 0, 0, 0)` dla półprzezroczystej czerni.

### Przypadki brzegowe i wariacje

- **Brak rozmycia:** Ustaw `Blur = 0`, aby uzyskać ostry, wyraźny cień.  
- **Ujemne przesunięcia:** Użyj `OffsetX = -4`, aby przesunąć cień w lewo.  
- **Różne kształty:** Te same właściwości cienia działają dla kół, trójkątów czy nawet kształtów rysowanych odręcznie — po prostu zmień `ShapeType` w Kroku 2.  
- **Kompatybilność:** Aspose.Words zapisuje dane cienia w formacie Office Open XML, który działa w Word 2010‑2021 oraz Office 365.

## Krok 5 – Zapisanie dokumentu (Utwórz dokument Word)

Na koniec zapisz plik na dysku. Możesz wybrać dowolny obsługiwany format (`.docx`, `.pdf`, `.odt`, …), ale w tym przewodniku pozostaniemy przy klasycznym formacie Word.

```csharp
        // Step 5: Save the document with the shaped shadow
        document.Save("ShadowRectangle.docx");
    }
}
```

Gdy otworzysz **ShadowRectangle.docx** w Microsoft Word, zobaczysz szary prostokąt z subtelnym, rozmytym cieniem przesuniętym w dół i w prawo — dokładnie tak, jak zaprogramowaliśmy.

### Oczekiwany rezultat

- Plik *.docx* jednosktronicowy.  
- Prostokąt 200 pt × 100 pt wyśrodkowany w miejscu, w którym znajdował się kursor w momencie wywołania `InsertShape`.  
- Szary cień, który pojawia się 4 pt w prawo i 4 pt w dół, z rozmyciem 5 pt.

Jeśli kształt wydaje się nie wyśrodkowany, możesz przesunąć kursor za pomocą `builder.MoveTo` przed wstawieniem lub dostosować właściwości `Left` i `Top` prostokąta po jego utworzeniu.

## Często zadawane pytania i rozwiązywanie problemów

**P: Cień nie pojawia się w Wordzie.**  
O: Upewnij się, że `ShadowFormat.Visible` jest ustawione na `true`. Sprawdź także, czy używasz aktualnej wersji Aspose.Words (funkcja cienia została dodana w wersji 20.3).

**P: Czy mogę zastosować gradient do cienia?**  
O: Nie bezpośrednio przez `ShadowFormat`. Interfejs Worda obsługuje gradientowe cienie, ale schemat Open XML (na którym opiera się Aspose.Words) udostępnia tylko cienie jednokolorowe. Aby uzyskać gradient, trzeba ręcznie edytować XML — to bardziej zaawansowany scenariusz.

**P: Co zrobić, jeśli potrzebuję przezroczystego prostokąta tylko z cieniem?**  
O: Po wstawieniu ustaw `rectangle.FillColor = Color.Transparent;`. Cień nadal będzie renderowany, ponieważ jest niezależny od wypełnienia.

## Wskazówki dla kodu produkcyjnego

- **Ponowne użycie buildera:** Jeśli dodajesz wiele kształtów, trzymaj tę samą instancję `DocumentBuilder` — tworzenie nowego obiektu dla każdego kształtu generuje niepotrzebne obciążenie.  
- **Zbiorcze zapisy:** Zapisz raz po wszystkich modyfikacjach; częste operacje I/O spowalniają generowanie dużych dokumentów.  
- **Obsługa błędów:** Owiń cały blok w `try / catch` i loguj wyjątki `Aspose.Words`; często zawierają przydatne numery linii, jeśli szablon dokumentu jest uszkodzony.

## Kolejne kroki (tematy powiązane)

- **Jak dodać cień** do obrazów lub pól tekstowych (podobne użycie `ShadowFormat`).  
- **Wstaw kształt prostokąta** wewnątrz komórki tabeli dla niestandardowego stylu komórki.  
- **Utwórz prostokąt w Wordzie** przy użyciu natywnego XML Worda (dla tych, którzy wolą surowy Open XML).  
- **Ustaw kolor cienia** dynamicznie w zależności od danych wejściowych użytkownika lub kolorów motywu.

Eksperymentuj z różnymi kolorami, promieniami rozmycia i przesunięciami — może delikatna niebieska poświata dla raportu korporacyjnego, albo głęboki czarny cień dla dramatycznej ulotki. Możliwości są nieograniczone, a zmiany w kodzie minimalne.

---

### Szybkie podsumowanie

- **Utworzyliśmy dokument Word** od podstaw.  
- **Wstawiliśmy kształt prostokąta** i włączyliśmy jego cień.  
- **Ustawiliśmy kolor cienia**, rozmycie i przesunięcia, aby uzyskać profesjonalny wygląd.  
- **Zapisaliśmy plik**, gotowy do dystrybucji.

Teraz masz solidną bazę do dodawania wizualnych akcentów w każdym projekcie automatyzacji Worda. Masz więcej pomysłów? Dodaj komentarz i kontynuujmy dyskusję. Szczęśliwego kodowania!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}