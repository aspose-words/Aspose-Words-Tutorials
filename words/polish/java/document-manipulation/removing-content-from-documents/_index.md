---
date: 2026-01-06
description: Dowiedz się, jak usuwać stopki z dokumentów Word przy użyciu Aspose.Words
  for Java, a także jak usuwać podziały sekcji, podziały stron i inne.
linktitle: Removing Content from Documents
second_title: Aspose.Words Java Document Processing API
title: Jak usunąć stopki z dokumentów Word przy użyciu Aspose.Words dla Javy
url: /pl/java/document-manipulation/removing-content-from-documents/
weight: 16
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Jak usunąć stopki z dokumentów Word przy użyciu Aspose.Words for Java

## Wprowadzenie do Aspose.Words for Java

W tym samouczku odkryjesz **jak usunąć stopki z Word** programowo przy użyciu Aspose.Words for Java. Niezależnie od tego, czy musisz oczyścić wygenerowane raporty, usunąć poufne informacje, czy po prostu uporządkować szablon, ten przewodnik przeprowadzi Cię przez najczęstsze scenariusze usuwania treści — podziały stron, podziały sekcji, stopki i spisy treści. Zaczynajmy!

## Szybkie odpowiedzi
- **Czy mogę usunąć stopki bez wpływu na inną treść?** Tak, API pozwala celować wyłącznie w węzły stopki.
- **Czy potrzebna jest licencja do uruchomienia tych przykładów?** Darmowa wersja próbna działa w środowisku deweloperskim; licencja jest wymagana w produkcji.
- **Jakie formaty Word są obsługiwane?** DOC, DOCX, DOCM oraz formaty oparte na OOXML.
- **Czy kod jest kompatybilny z Java 8 i nowszymi?** Absolutnie, biblioteka jest kompatybilna z Java od wersji 8.
- **Jak usunąć podziały sekcji?** Zobacz sekcję „Jak usunąć podziały sekcji” poniżej.

## Co oznacza „usunięcie stopek z Word”?

Usunięcie stopek z dokumentu Word oznacza usunięcie węzłów `HeaderFooter`, które pojawiają się na dole każdej strony. Ta operacja jest powszechna, gdy chcesz uzyskać czysty układ z jedynie nagłówkiem lub gdy stopki zawierają wrażliwe dane, które nie powinny być udostępniane.

## Dlaczego używać Aspose.Words for Java do tego zadania?

Aspose.Words udostępnia wysokopoziomowy model obiektowy, który abstrahuje złożoność formatu pliku DOCX. Możesz manipulować akapitami, fragmentami tekstu, sekcjami i stopkami przy użyciu kilku linii kodu Java, bez konieczności instalacji Microsoft Word na serwerze.

## Wymagania wstępne
- Java Development Kit (JDK) 8 lub nowszy.
- Biblioteka Aspose.Words for Java (pobierz ze strony Aspose).
- Przykładowy dokument Word (`Document.docx`) umieszczony w znanym katalogu.

## Usuwanie podziałów stron

Podziały stron kontrolują paginację, ale czasami trzeba je usunąć. Poniższy fragment skanuje każdy akapit, usuwa flagę `PageBreakBefore` i eliminuje wszelkie wyraźne znaki podziału strony.

```java
Document doc = new Document("Your Directory Path" + "Document.docx");
NodeCollection paragraphs = doc.getChildNodes(NodeType.PARAGRAPH, true);
for (Paragraph para : (Iterable<Paragraph>) paragraphs) {
    if (para.getParagraphFormat().getPageBreakBefore()) {
        para.getParagraphFormat().setPageBreakBefore(false);
    }
    for (Run run : para.getRuns()) {
        if (run.getText().contains(ControlChar.PAGE_BREAK)) {
            run.setText(run.getText().replace(ControlChar.PAGE_BREAK, ""));
        }
    }
}
doc.save("Your Directory Path" + "RemoveContent.RemovePageBreaks.docx");
```

*Wskazówka:* Uruchom to przed usunięciem stopek, jeśli chcesz uzyskać układ jednokolumnowy.

## Jak usunąć podziały sekcji

Podziały sekcji dzielą dokument na niezależne sekcje, z własnymi nagłówkami, stopkami i ustawieniami strony. Aby scalić sekcje i skutecznie **usunąć podziały sekcji**, iteruj w kolejności odwrotnej, dołącz zawartość każdej wcześniejszej sekcji na początek ostatniej, a następnie usuń teraz pustą sekcję.

```java
for (int i = doc.getSections().getCount() - 2; i >= 0; i--) {
    doc.getLastSection().prependContent(doc.getSections().get(i));
    doc.getSections().get(i).remove();
}
```

To podejście zachowuje całą zawartość, jednocześnie eliminując przerwanie strukturalne.

## Usuwanie stopek (Główny cel: usunięcie stopek z Word)

Stopki często zawierają numery stron, daty lub poufne notatki. Poniższy kod usuwa **wszystkie typy stopek** — pierwszą stronę, podstawową i nawet strony — z każdej sekcji.

```java
Document doc = new Document("Your Directory Path" + "Header and footer types.docx");
for (Section section : doc.getSections()) {
    HeaderFooter footer = section.getHeadersFooters().getByHeaderFooterType(HeaderFooterType.FOOTER_FIRST);
    footer.remove();
    footer = section.getHeadersFooters().getByHeaderFooterType(HeaderFooterType.FOOTER_PRIMARY);
    footer.remove();
    footer = section.getHeadersFooters().getByHeaderFooterType(HeaderFooterType.FOOTER_EVEN);
    footer.remove();
}
doc.save("Your Directory Path" + "RemoveContent.RemoveFooters.docx");
```

Po uruchomieniu tego fragmentu wynikowy dokument nie będzie miał **stopek**, spełniając główny cel „usunięcia stopek z Word”.

## Usuwanie spisu treści

Spis treści (TOC) jest przechowywany jako pole. Aby go usunąć, znajdź pole TOC po jego indeksie i usuń powiązany węzeł.

```java
Document doc = new Document("Your Directory Path" + "Table of contents.docx");
removeTableOfContents(doc, 0);
doc.save("Your Directory Path" + "RemoveContent.RemoveToc.doc");
```

*(Metoda `removeTableOfContents` jest częścią przykładów Aspose.Words i usuwa określony węzeł TOC.)*

## Typowe problemy i rozwiązywanie

| Symptom | Likely Cause | Fix |
|---------|--------------|-----|
| Stopki nadal się pojawiają po uruchomieniu kodu | Dokument zawiera pary **header/footer**, które nie są dostępne (np. brak `FOOTER_FIRST`) | Iteruj po wszystkich wartościach `HeaderFooterType` lub sprawdź `null` przed wywołaniem `remove()`. |
| Układ strony zmienia się nieoczekiwanie po usunięciu podziałów sekcji | Ustawienia strony specyficzne dla sekcji (marginesy, orientacja) zostały utracone | Skopiuj ustawienia sekcji do docelowej sekcji przed usunięciem. |
| `ControlChar.PAGE_BREAK` nie został usunięty | Dokument używa **section breaks** zamiast znaków podziału strony | Użyj najpierw metody „Jak usunąć podziały sekcji”. |

## Najczęściej zadawane pytania

**Q: Czy mogę usunąć tylko określone stopki (np. tylko stopkę pierwszej strony)?**  
A: Tak. Pobierz stopkę według jej typu (`FOOTER_FIRST`) i wywołaj `remove()` tylko na tej instancji.

**Q: Jak usunąć podziały sekcji bez łączenia zawartości?**  
A: Możesz usunąć węzeł `Section` bezpośrednio, jeśli nie musisz zachować jego zawartości, ale pamiętaj, że wszystkie nagłówki/stopki przypisane do tej sekcji również zostaną utracone.

**Q: Czy można programowo wykryć, czy dokument zawiera TOC przed próbą jego usunięcia?**  
A: Użyj `doc.getRange().getFields()` i sprawdź pola typu `FieldType.FIELD_TABLE_OF_CONTENTS`.

**Q: Czy Aspose.Words obsługuje usuwanie stopek z zaszyfrowanych plików Word?**  
A: Tak, wystarczy otworzyć dokument z hasłem: `new Document(path, new LoadOptions(password))`.

**Q: Czy usunięcie stopek wpłynie na paginację dokumentu?**  
A: Usunięcie stopek nie zmienia numeracji stron, chyba że stopka sama zawiera pole numeru strony. Jeśli potrzebujesz ponownej numeracji, zaktualizuj odpowiednio pola numeru strony.

## Zakończenie

Omówiliśmy wszystko, co potrzebne, aby **usunąć stopki z dokumentów Word** przy użyciu Aspose.Words for Java, wraz z powiązanymi zadaniami, takimi jak usuwanie podziałów stron, **jak usunąć podziały sekcji** oraz usuwanie spisów treści. Korzystając z tych fragmentów, możesz tworzyć czyste, profesjonalne dokumenty dopasowane do wymagań Twojej aplikacji.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}

---

**Last Updated:** 2026-01-06  
**Tested With:** Aspose.Words for Java 24.12  
**Author:** Aspose  

---