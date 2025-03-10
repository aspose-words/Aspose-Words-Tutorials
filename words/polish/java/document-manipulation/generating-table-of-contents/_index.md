---
title: Generowanie spisu treści w Aspose.Words dla Java
linktitle: Generowanie spisu treści
second_title: Aspose.Words API przetwarzania dokumentów Java
description: Dowiedz się, jak generować i dostosowywać spis treści (TOC) za pomocą Aspose.Words dla Java. Twórz uporządkowane i profesjonalne dokumenty bez wysiłku.
weight: 21
url: /pl/java/document-manipulation/generating-table-of-contents/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Generowanie spisu treści w Aspose.Words dla Java


## Wprowadzenie do generowania spisu treści w Aspose.Words dla Java

W tym samouczku przeprowadzimy Cię przez proces generowania spisu treści (TOC) przy użyciu Aspose.Words dla Java. TOC jest kluczową funkcją tworzenia uporządkowanych dokumentów. Omówimy, jak dostosować wygląd i układ spisu treści.

## Wymagania wstępne

Zanim zaczniesz, upewnij się, że masz zainstalowany i skonfigurowany pakiet Aspose.Words for Java w swoim projekcie Java.

## Krok 1: Utwórz nowy dokument

Najpierw utwórzmy nowy dokument, z którym będziemy pracować.

```java
Document doc = new Document();
```

## Krok 2: Dostosuj style spisu treści

Aby dostosować wygląd spisu treści, możesz zmodyfikować style z nim powiązane. W tym przykładzie pogrubimy wpisy spisu treści pierwszego poziomu.

```java
doc.getStyles().getByStyleIdentifier(StyleIdentifier.TOC_1).getFont().setBold(true);
```

## Krok 3: Dodaj zawartość do dokumentu

Możesz dodać swoją treść do dokumentu. Ta treść zostanie użyta do wygenerowania spisu treści.

## Krok 4: Wygeneruj spis treści

Aby wygenerować spis treści, wstaw pole spisu treści w żądanym miejscu w dokumencie. To pole zostanie automatycznie wypełnione na podstawie nagłówków i stylów w dokumencie.

```java
// Wstaw pole spisu treści w wybranym miejscu dokumentu.
FieldToc fieldToc = new FieldToc();
doc.getFirstSection().getBody().getFirstParagraph().appendChild(fieldToc);
```

## Krok 5: Zapisz dokument

Na koniec zapisz dokument ze spisem treści.

```java
doc.save("your_output_path_here");
```

## Dostosowywanie tabulatorów w spisie treści

Możesz również dostosować tabulatory w spisie treści, aby kontrolować układ numerów stron. Oto, jak możesz zmienić tabulatory:

```java
Document doc = new Document("Table of contents.docx");

for (Paragraph para : (Iterable<Paragraph>) doc.getChildNodes(NodeType.PARAGRAPH, true))
{
    if (para.getParagraphFormat().getStyle().getStyleIdentifier() >= StyleIdentifier.TOC_1 &&
        para.getParagraphFormat().getStyle().getStyleIdentifier() <= StyleIdentifier.TOC_9)
    {
        // Wybierz pierwszą kartę użytą w tym akapicie, która wyrównuje numery stron.
        TabStop tab = para.getParagraphFormat().getTabStops().get(0);
        
        // Usuń starą zakładkę.
        para.getParagraphFormat().getTabStops().removeByPosition(tab.getPosition());
        
        //Wstaw nową zakładkę w zmienionej pozycji (np. 50 jednostek na lewo).
        para.getParagraphFormat().getTabStops().add(tab.getPosition() - 50.0, tab.getAlignment(), tab.getLeader());
    }
}

doc.save("output.docx");
```

Teraz masz w swoim dokumencie dostosowany spis treści z dostosowanymi tabulatorami do wyrównania numerów stron.


## Wniosek

W tym samouczku sprawdziliśmy, jak wygenerować spis treści (TOC) za pomocą Aspose.Words for Java, potężnej biblioteki do pracy z dokumentami Word. Dobrze ustrukturyzowany spis treści jest niezbędny do organizowania i nawigacji po długich dokumentach, a Aspose.Words zapewnia narzędzia do łatwego tworzenia i dostosowywania spisów treści.

## Najczęściej zadawane pytania

### Jak zmienić formatowanie wpisów w spisie treści?

 Możesz modyfikować style powiązane z poziomami spisu treści za pomocą`doc.getStyles().getByStyleIdentifier(StyleIdentifier.TOC_X)`, gdzie X jest poziomem spisu treści.

### Jak mogę dodać więcej poziomów do spisu treści?

Aby dodać więcej poziomów do spisu treści, możesz zmodyfikować pole spisu treści i określić żądaną liczbę poziomów.

### Czy mogę zmienić położenie tabulatorów dla konkretnych wpisów spisu treści?

Tak, jak pokazano w przykładzie kodu powyżej, można zmienić położenie tabulatorów dla konkretnych wpisów spisu treści, przechodząc przez akapity i odpowiednio modyfikując położenia tabulatorów.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
