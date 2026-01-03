---
date: 2026-01-03
description: Dowiedz się, jak dostosować numery stron podczas wstawiania spisu treści
  przy użyciu Aspose.Words for Java. Dostosuj style spisu treści i twórz dokumenty
  bez wysiłku.
linktitle: Generating Table of Contents
second_title: Aspose.Words Java Document Processing API
title: Dostosuj numery stron i wygeneruj spis treści przy użyciu Aspose.Words dla
  Javy
url: /pl/java/document-manipulation/generating-table-of-contents/
weight: 21
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Dostosowanie numeracji stron i generowanie spisu treści w Aspose.Words dla Javy

W tym samouczku dowiesz się, jak **dostosować numerację stron** oraz **wstawić spis treści** (TOC) przy użyciu Aspose.Words dla Javy. Dobrze skonstruowany spis treści ułatwia nawigację w długich dokumentach, a precyzyjne dopasowanie wyrównania numerów stron zapewnia czytelnikom profesjonalne wrażenie. Przejdziemy przez tworzenie dokumentu, dostosowywanie stylów TOC oraz modyfikację tabulatorów, aby numery stron znajdowały się dokładnie tam, gdzie chcesz.

## Szybkie odpowiedzi
- **Co oznacza „dostosowanie numeracji stron”?** Modyfikację tabulatorów, które wyrównują numery stron w spisie treści.  
- **Czy mogę automatycznie wstawić spis treści?** Tak – użyj klasy `FieldToc`.  
- **Czy potrzebna jest licencja do uruchomienia kodu?** Bezpłatna wersja próbna wystarczy do rozwoju; licencja jest wymagana w środowisku produkcyjnym.  
- **Jaką wersję Aspose obsługujemy?** Przykłady działają z najnowszą wersją Aspose.Words dla Javy.  
- **Czy można dostosować style TOC?** Oczywiście – możesz zmieniać czcionki, pogrubienie i wiele innych.

## Co to jest spis treści w Aspose.Words?
Spis treści to pole, które przeszukuje dokument w poszukiwaniu stylów nagłówków (np. Heading 1, Heading 2) i generuje listę wpisów z numerami stron. Aspose.Words umożliwia wstawienie tego pola programowo oraz pełną kontrolę nad jego wyglądem.

## Dlaczego warto dostosować numery stron w spisie treści?
Dostosowanie tabulatorów daje precyzyjną kontrolę nad położeniem numerów stron, co jest kluczowe dla:

- Utrzymania czystego, kolumnowo wyrównanego układu.  
- Zgodności ze stylami korporacyjnymi.  
- Poprawy czytelności w dokumentach drukowanych i cyfrowych.

## Wymagania wstępne
- Aspose.Words dla Javy dodany do projektu (Maven/Gradle).  
- Podstawowa znajomość składni Javy.  

## Przewodnik krok po kroku

### Krok 1: Utwórz nowy dokument
Najpierw zainicjuj pusty obiekt `Document`, który będzie zawierał treść i spis treści.

```java
Document doc = new Document();
```

### Krok 2: Dostosuj style TOC
Możesz zmienić wygląd każdego poziomu spisu treści. W tym przykładzie pierwszopoziomowe wpisy ustawiamy jako pogrubione – jest to częsta prośba o formatowanie.

```java
doc.getStyles().getByStyleIdentifier(StyleIdentifier.TOC_1).getFont().setBold(true);
```

### Krok 3: Dodaj treść do dokumentu
Wstaw nagłówki (np. `Heading1`, `Heading2`) oraz zwykłe akapity. Pole TOC później automatycznie wykryje te nagłówki. *(Kod pominięty dla zwięzłości – istotny jest sam proces generowania TOC.)*

### Krok 4: Wstaw pole spisu treści
Umieść spis treści w wybranym miejscu – zazwyczaj na początku dokumentu.

```java
// Insert a TOC field at the desired location in your document.
FieldToc fieldToc = new FieldToc();
doc.getFirstSection().getBody().getFirstParagraph().appendChild(fieldToc);
```

### Krok 5: Zapisz dokument
Zachowaj dokument na dysku. Możesz wybrać dowolny obsługiwany format, taki jak DOCX, PDF lub HTML.

```java
doc.save("your_output_path_here");
```

## Dostosowywanie tabulatorów w TOC (Dostosowanie numeracji stron)
Jeśli domyślny tabulator nie wyrównuje numerów stron tak, jak potrzebujesz, możesz przeiterować wszystkie akapity TOC i zmodyfikować pozycje ich tabulatorów.

```java
Document doc = new Document("Table of contents.docx");

for (Paragraph para : (Iterable<Paragraph>) doc.getChildNodes(NodeType.PARAGRAPH, true))
{
    if (para.getParagraphFormat().getStyle().getStyleIdentifier() >= StyleIdentifier.TOC_1 &&
        para.getParagraphFormat().getStyle().getStyleIdentifier() <= StyleIdentifier.TOC_9)
    {
        // Get the first tab used in this paragraph, which aligns the page numbers.
        TabStop tab = para.getParagraphFormat().getTabStops().get(0);
        
        // Remove the old tab.
        para.getParagraphFormat().getTabStops().removeByPosition(tab.getPosition());
        
        // Insert a new tab at a modified position (e.g., 50 units to the left).
        para.getParagraphFormat().getTabStops().add(tab.getPosition() - 50.0, tab.getAlignment(), tab.getLeader());
    }
}

doc.save("output.docx");
```

Teraz wpisy w spisie treści wyświetlają numery stron dokładnie tam, gdzie chcesz, nadając dokumentowi wykończony wygląd.

## Częste problemy i wskazówki
- **Brak nagłówków w TOC:** Upewnij się, że Twoje nagłówki używają wbudowanych stylów (`Heading1`, `Heading2` itp.) lub mapuj style niestandardowe na poziomy TOC.  
- **Tabulator nie zastosowany:** Sprawdź, czy akapit rzeczywiście należy do stylu TOC (`TOC_1`‑`TOC_9`).  
- **Wydajność przy dużych dokumentach:** Wywołaj `doc.updateFields()` po wstawieniu TOC, aby odświeżyć wpisy jednorazowo.

## Najczęściej zadawane pytania

**P: Jak zmienić formatowanie wpisów TOC?**  
O: Użyj `doc.getStyles().getByStyleIdentifier(StyleIdentifier.TOC_X)`, gdzie *X* to poziom (1‑9), i zmodyfikuj czcionkę, kolor lub ustawienia akapitu.

**P: Jak dodać więcej poziomów do mojego TOC?**  
O: Zmodyfikuj przełącznik `FieldToc` `\o "1-3"` (na przykład), aby uwzględnić dodatkowe poziomy nagłówków, a następnie zaktualizuj odpowiadające style `TOC_X`.

**P: Czy mogę zmienić pozycje tabulatorów dla konkretnych wpisów TOC?**  
O: Tak – przeiteruj akapity, jak pokazano w sekcji „Dostosowywanie tabulatorów”, i zmień każdy tabulator indywidualnie.

**P: Czy można wygenerować TOC w wyjściu PDF?**  
O: Oczywiście. Zapisz dokument jako PDF (`doc.save("output.pdf")`) po wygenerowaniu spisu treści; pole zostanie automatycznie wyrenderowane.

**P: Czy muszę ręcznie wywoływać `updateFields()`?**  
O: Po wstawieniu `FieldToc` Aspose.Words aktualizuje go przy zapisie, ale wywołanie `doc.updateFields()` daje natychmiastowy wynik, przydatny podczas debugowania.

## Podsumowanie
Nauczyłeś się, jak **dostosować numery stron**, **wstawić spis treści** oraz **dostosować style TOC** przy użyciu Aspose.Words dla Javy. Te techniki pozwalają tworzyć czyste, nawigowalne i profesjonalnie sformatowane dokumenty spełniające wszelkie standardy wydawnicze.

---  

**Ostatnia aktualizacja:** 2026-01-03  
**Testowano z Aspose.Words dla Javy (najnowsza wersja)  
**Autor:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}