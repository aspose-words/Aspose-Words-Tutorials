---
date: 2026-02-14
description: Dowiedz się, jak wyświetlać równania w linii, wstawiać równania matematyczne
  i z łatwością manipulować obiektami Office Math przy użyciu Aspose.Words dla Javy.
linktitle: Using Office Math Objects
second_title: Aspose.Words Java Document Processing API
title: Wyświetlanie równań w linii przy użyciu Office Math w Aspose.Words dla Javy
url: /pl/java/document-conversion-and-export/using-office-math-objects/
weight: 13
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Wyświetlanie równań w linii przy użyciu Office Math w Aspose.Words for Java

W tym obszernej tutorialu dowiesz się, jak **wyświetlać równania w linii** przy użyciu obiektów Office Math w Aspose.Words for Java. Niezależnie od tego, czy potrzebujesz **wstawić równanie matematyczne** do raportu, czy dopracować formatowanie złożonych formuł, ten przewodnik poprowadzi Cię przez każdy krok — od załadowania dokumentu Word po zapisanie ostatecznego wyniku.

## Szybkie odpowiedzi
- **Co oznacza „display math inline”?** Równanie pojawia się w obrębie przepływu tekstu, a nie w osobnej linii.  
- **Która klasa reprezentuje obiekt matematyczny?** `OfficeMath` w API Aspose.Words.  
- **Czy mogę zmienić wyrównanie?** Tak, użyj `setJustification` z LEFT, CENTER lub RIGHT.  
- **Czy potrzebna jest licencja na tę funkcję?** Wymagana jest ważna licencja Aspose.Words for Java do użytku produkcyjnego.  
- **Jaką wersję prezentuje przykład?** Kod działa z najnowszą wersją Aspose.Words for Java (2026).

## Co to jest „display math inline”?
Wyświetlanie równań w linii oznacza, że równanie jest traktowane jako część tekstu akapitu, co pozwala mu naturalnie owijać się razem z otaczającymi słowami. Jest to przydatne przy krótkich formułach, które nie powinny przerywać płynności czytania.

## Dlaczego warto używać obiektów Office Math w Aspose.Words for Java?
- **Precyzyjna kontrola** nad układem równania (inline vs. display).  
- **Programowa manipulacja** równaniami bez ręcznego otwierania Worda.  
- **Spójne renderowanie** na różnych platformach, idealne do automatycznego generowania raportów.

## Wymagania wstępne
Przed rozpoczęciem upewnij się, że masz:

- Aspose.Words for Java zainstalowany i odwołany w projekcie.  
- Plik Word, który już zawiera równanie Office Math (np. `OfficeMath.docx`).  
- Ważną licencję, jeśli planujesz uruchomić kod poza trybem ewaluacyjnym.

## Przewodnik krok po kroku

### Załaduj dokument
Najpierw załaduj dokument, który zawiera równanie Office Math, z którym chcesz pracować:

```java
Document doc = new Document("Your Directory Path" + "OfficeMath.docx");
```

### Uzyskaj dostęp do obiektu Office Math
Pobierz pierwszy węzeł Office Math z dokumentu:

```java
OfficeMath officeMath = (OfficeMath) doc.getChild(NodeType.OFFICE_MATH, 0, true);
```

### Ustaw typ wyświetlania (Inline vs. Display)
Kontroluj, czy równanie ma pojawić się w linii z otaczającym tekstem, czy w osobnej linii. Dla **display math inline** użyj wyliczenia `INLINE`; dla osobnej linii użyj `DISPLAY`:

```java
officeMath.setDisplayType(OfficeMathDisplayType.DISPLAY);
```

*Jeśli chcesz, aby równanie pozostało w linii, zamień `DISPLAY` na `INLINE`.*

### Ustaw wyrównanie
Dostosuj wyrównanie równania. Poniżej wyrównujemy je do lewej, ale możesz także wybrać `CENTER` lub `RIGHT`:

```java
officeMath.setJustification(OfficeMathJustification.LEFT);
```

### Zapisz zmodyfikowany dokument
Na koniec zapisz zmiany do nowego pliku:

```java
doc.save("Your Directory Path" + "ModifiedOfficeMath.docx");
```

## Pełny kod źródłowy użycia obiektów Office Math w Aspose.Words for Java

```java
        Document doc = new Document("Your Directory Path" + "Office math.docx");
        OfficeMath officeMath = (OfficeMath) doc.getChild(NodeType.OFFICE_MATH, 0, true);
        // OfficeMath display type represents whether an equation is displayed inline with the text or displayed on its line.
        officeMath.setDisplayType(OfficeMathDisplayType.DISPLAY);
        officeMath.setJustification(OfficeMathJustification.LEFT);
        doc.save("Your Directory Path" + "WorkingWithOfficeMath.MathEquations.docx");
```

## Typowe problemy i rozwiązywanie
- **Równanie nie znalezione:** Upewnij się, że dokument rzeczywiście zawiera obiekt Office Math; w przeciwnym razie `doc.getChild` zwraca `null`.  
- **Typ wyświetlania nie ma efektu:** Sprawdź, czy używasz najnowszej wersji Aspose.Words; starsze wydania mogą mieć ograniczone wsparcie dla `OfficeMathDisplayType`.  
- **Wyjątek licencyjny:** Jeśli pojawi się błąd licencji, sprawdź ponownie, czy plik licencji jest poprawnie załadowany przed utworzeniem instancji `Document`.

## Najczęściej zadawane pytania

**Q: Jaki jest cel obiektów Office Math w Aspose.Words for Java?**  
A: Obiekty Office Math pozwalają reprezentować i manipulować równaniami matematycznymi programowo, dając pełną kontrolę nad ich wyświetlaniem i formatowaniem.

**Q: Czy mogę wyrównać równania Office Math w dokumencie w inny sposób?**  
A: Tak, użyj metody `setJustification`, aby wyrównać je do lewej, prawej lub środka.

**Q: Czy Aspose.Words for Java nadaje się do obsługi złożonych dokumentów matematycznych?**  
A: Absolutnie. Biblioteka w pełni obsługuje skomplikowane równania, zagnieżdżone ułamki, macierze i wiele innych.

**Q: Jak mogę dowiedzieć się więcej o Aspose.Words for Java?**  
A: Aby uzyskać pełną dokumentację i pobrać pliki, odwiedź [Dokumentacja Aspose.Words for Java](https://reference.aspose.com/words/java/).

**Q: Gdzie mogę pobrać Aspose.Words for Java?**  
A: Możesz pobrać Aspose.Words for Java ze strony: [Pobierz Aspose.Words for Java](https://releases.aspose.com/words/java/).

---

**Ostatnia aktualizacja:** 2026-02-14  
**Testowano z:** Aspose.Words for Java 24.12 (najnowsza wersja na luty 2026)  
**Autor:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}