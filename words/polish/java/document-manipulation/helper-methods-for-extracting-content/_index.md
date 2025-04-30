---
"description": "Dowiedz się, jak wydajnie wyodrębniać zawartość z dokumentów Word za pomocą Aspose.Words for Java. Poznaj metody pomocnicze, niestandardowe formatowanie i wiele więcej w tym kompleksowym przewodniku."
"linktitle": "Metody pomocnicze do wyodrębniania treści"
"second_title": "Aspose.Words API przetwarzania dokumentów Java"
"title": "Metody pomocnicze do wyodrębniania zawartości w Aspose.Words dla Java"
"url": "/pl/java/document-manipulation/helper-methods-for-extracting-content/"
"weight": 14
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Metody pomocnicze do wyodrębniania zawartości w Aspose.Words dla Java


## Wprowadzenie do metod pomocniczych do wyodrębniania zawartości w Aspose.Words dla języka Java

Aspose.Words for Java to potężna biblioteka, która pozwala programistom programowo pracować z dokumentami Word. Jednym z typowych zadań podczas pracy z dokumentami Word jest wyodrębnianie z nich treści. W tym artykule przyjrzymy się kilku metodom pomocniczym do wydajnego wyodrębniania treści przy użyciu Aspose.Words for Java.

## Wymagania wstępne

Zanim przejdziemy do przykładów kodu, upewnij się, że masz zainstalowany i skonfigurowany Aspose.Words for Java w swoim projekcie Java. Możesz go pobrać ze strony [Tutaj](https://releases.aspose.com/words/java/).

## Metoda pomocnicza 1: Wyodrębnianie akapitów według stylu

```java
public static ArrayList<Paragraph> paragraphsByStyleName(Document doc, String styleName) {
    // Utwórz tablicę, aby zebrać akapity o określonym stylu.
    ArrayList<Paragraph> paragraphsWithStyle = new ArrayList<Paragraph>();
    NodeCollection paragraphs = doc.getChildNodes(NodeType.PARAGRAPH, true);

    // Przejrzyj wszystkie akapity, aby znaleźć te, które odpowiadają określonemu stylowi.
    for (Paragraph paragraph : (Iterable<Paragraph>) paragraphs) {
        if (paragraph.getParagraphFormat().getStyle().getName().equals(styleName))
            paragraphsWithStyle.add(paragraph);
    }
    return paragraphsWithStyle;
}
```

Możesz użyć tej metody, aby wyodrębnić akapity, które mają określony styl w dokumencie Word. Jest to przydatne, gdy chcesz wyodrębnić zawartość z określonym formatowaniem, takim jak nagłówki lub cytaty blokowe.

## Metoda pomocnicza 2: Wyodrębnianie zawartości według węzłów

```java
public static ArrayList<Node> extractContentBetweenNodes(Node startNode, Node endNode, boolean isInclusive) {
    // Najpierw sprawdź, czy węzły przekazane tej metodzie nadają się do użycia.
    verifyParameterNodes(startNode, endNode);
    
    // Utwórz listę, na której będą przechowywane wyodrębnione węzły.
    ArrayList<Node> nodes = new ArrayList<Node>();

    // Jeśli którykolwiek ze znaczników jest częścią komentarza, łącznie z samym komentarzem, musimy przesunąć wskaźnik
    // przejdź do węzła komentarza znalezionego po węźle CommentRangeEnd.
    if (endNode.getNodeType() == NodeType.COMMENT_RANGE_END && isInclusive) {
        Node node = findNextNode(NodeType.COMMENT, endNode.getNextSibling());
        if (node != null)
            endNode = node;
    }
    
    // Zachowaj zapis oryginalnych węzłów przekazanych tej metodzie, aby w razie potrzeby rozdzielić węzły znaczników.
    Node originalStartNode = startNode;
    Node originalEndNode = endNode;

    // Wyodrębnij zawartość na podstawie węzłów na poziomie bloku (akapity i tabele). Przejdź przez węzły nadrzędne, aby je znaleźć.
    // Podzielimy zawartość pierwszego i ostatniego węzła w zależności od tego, czy węzły znaczników są inline.
    startNode = getAncestorInBody(startNode);
    endNode = getAncestorInBody(endNode);
    boolean isExtracting = true;
    boolean isStartingNode = true;
    // Aktualny węzeł, który wyodrębniamy z dokumentu.
    Node currNode = startNode;

    // Rozpocznij wyodrębnianie treści. Przetwórz wszystkie węzły na poziomie bloku i podziel konkretnie pierwszy
    // i ostatnie węzły, gdy jest to potrzebne, aby zachować formatowanie akapitu.
    // Ta metoda jest nieco bardziej skomplikowana niż zwykły ekstraktor, ponieważ musimy wziąć pod uwagę
    // w wyodrębnianiu za pomocą węzłów inline, pól, zakładek itp., aby uczynić je użytecznymi.
    while (isExtracting) {
        // Sklonuj bieżący węzeł i jego elementy podrzędne, aby uzyskać kopię.
        Node cloneNode = currNode.deepClone(true);
        boolean isEndingNode = currNode.equals(endNode);
        if (isStartingNode || isEndingNode) {
            // Musimy przetworzyć każdy znacznik osobno, dlatego przekazujemy go do osobnej metody.
            // Aby zachować indeksy węzłów, najpierw należy przetworzyć zakończenie.
            if (isEndingNode) {
                // !isStartingNode: nie dodawaj węzła dwa razy, jeśli znaczniki wskazują ten sam węzeł.
                processMarker(cloneNode, nodes, originalEndNode, currNode, isInclusive,
                        false, !isStartingNode, false);
                isExtracting = false;
            }
            // Warunki muszą być oddzielne, ponieważ znaczniki początku i końca bloku mogą znajdować się w tym samym węźle.
            if (isStartingNode) {
                processMarker(cloneNode, nodes, originalStartNode, currNode, isInclusive,
                        true, true, false);
                isStartingNode = false;
            }
        } else
            // Węzeł nie jest znacznikiem początku ani końca, po prostu dodaj kopię do listy.
            nodes.add(cloneNode);

        // Przejdź do następnego węzła i wyodrębnij go. Jeśli następny węzeł jest nullem,
        // resztę treści znajdziesz w innej sekcji.
        if (currNode.getNextSibling() == null && isExtracting) {
            // Przejdź do następnej sekcji.
            Section nextSection = (Section) currNode.getAncestor(NodeType.SECTION).getNextSibling();
            currNode = nextSection.getBody().getFirstChild();
        } else {
            // Przejdź do następnego węzła w treści.
            currNode = currNode.getNextSibling();
        }
    }

    // Aby zachować zgodność z trybem z zakładkami wbudowanymi, dodaj następny akapit (pusty).
    if (isInclusive && originalEndNode == endNode && !originalEndNode.isComposite())
        includeNextParagraph(endNode, nodes);

    // Zwróć węzły znajdujące się pomiędzy znacznikami węzłów.
    return nodes;
}
```

Ta metoda pozwala wyodrębnić zawartość między dwoma określonymi węzłami, niezależnie od tego, czy są to akapity, tabele czy inne elementy blokowe. Obsługuje różne scenariusze, w tym znaczniki inline, pola i zakładki.

## Metoda pomocnicza 3: Generowanie nowego dokumentu

```java
public static Document generateDocument(Document srcDoc, ArrayList<Node> nodes) throws Exception {
    Document dstDoc = new Document();
    
    // Usuń pierwszy akapit z pustego dokumentu.
    dstDoc.getFirstSection().getBody().removeAllChildren();
    
    // Importuj każdy węzeł z listy do nowego dokumentu. Zachowaj oryginalne formatowanie węzła.
    NodeImporter importer = new NodeImporter(srcDoc, dstDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING);
    for (Node node : nodes) {
        Node importNode = importer.importNode(node, true);
        dstDoc.getFirstSection().getBody().appendChild(importNode);
    }
    
    return dstDoc;
}
```

Ta metoda pozwala na wygenerowanie nowego dokumentu poprzez zaimportowanie listy węzłów z dokumentu źródłowego. Zachowuje oryginalne formatowanie węzłów, co czyni ją przydatną do tworzenia nowych dokumentów o określonej zawartości.

## Wniosek

Wyodrębnianie treści z dokumentów Word może być kluczową częścią wielu zadań przetwarzania dokumentów. Aspose.Words for Java zapewnia potężne metody pomocnicze, które upraszczają ten proces. Niezależnie od tego, czy musisz wyodrębnić akapity według stylu, treści między węzłami, czy wygenerować nowe dokumenty, te metody pomogą Ci wydajnie pracować z dokumentami Word w aplikacjach Java.

## Najczęściej zadawane pytania

### Jak zainstalować Aspose.Words dla Java?

Aby zainstalować Aspose.Words dla Javy, możesz pobrać go ze strony internetowej Aspose. Odwiedź [Tutaj](https://releases.aspose.com/words/java/) aby pobrać najnowszą wersję.

### Czy mogę wyodrębnić treść z określonych sekcji dokumentu Word?

Tak, możesz wyodrębnić zawartość z określonych sekcji dokumentu Word, korzystając z metod wymienionych w tym artykule. Wystarczy określić węzły początkowe i końcowe, które definiują sekcję, którą chcesz wyodrębnić.

### Czy Aspose.Words dla Java jest kompatybilny z Java 11?

Tak, Aspose.Words for Java jest kompatybilny z Java 11 i nowszymi wersjami. Możesz go używać w swoich aplikacjach Java bez żadnych problemów.

### Czy mogę dostosować formatowanie wyodrębnionej treści?

Tak, możesz dostosować formatowanie wyodrębnionej zawartości, modyfikując importowane węzły w wygenerowanym dokumencie. Aspose.Words for Java zapewnia rozbudowane opcje formatowania, aby spełnić Twoje potrzeby.

### Gdzie mogę znaleźć więcej dokumentacji i przykładów dla Aspose.Words dla Java?

Pełną dokumentację i przykłady dla Aspose.Words dla Java można znaleźć na stronie internetowej Aspose. Odwiedź [https://reference.aspose.com/words/java/](https://reference.aspose.com/words/java/) aby uzyskać szczegółową dokumentację i zasoby.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}