---
title: Porównywanie dokumentów pod kątem różnic
linktitle: Porównywanie dokumentów pod kątem różnic
second_title: Aspose.Words API przetwarzania dokumentów Java
description: Dowiedz się, jak porównywać dokumenty pod kątem różnic, używając Aspose.Words w Javie. Nasz przewodnik krok po kroku zapewnia dokładne zarządzanie dokumentami.
weight: 12
url: /pl/java/document-merging/comparing-documents-for-differences/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Porównywanie dokumentów pod kątem różnic

## Wstęp

Czy kiedykolwiek zastanawiałeś się, jak dostrzec każdą pojedynczą różnicę między dwoma dokumentami Worda? Może rewidujesz dokument lub próbujesz znaleźć zmiany wprowadzone przez współpracownika. Ręczne porównania mogą być żmudne i podatne na błędy, ale z Aspose.Words dla Java to pestka! Ta biblioteka umożliwia automatyzację porównywania dokumentów, wyróżnianie rewizji i scalanie zmian bez wysiłku.

## Wymagania wstępne

Zanim zaczniesz pisać kod, upewnij się, że masz przygotowane następujące elementy:  
1. Java Development Kit (JDK) zainstalowany w Twoim systemie.  
2.  Aspose.Words dla biblioteki Java. Możesz[pobierz tutaj](https://releases.aspose.com/words/java/).  
3. Środowisko programistyczne, takie jak IntelliJ IDEA lub Eclipse.  
4. Podstawowa znajomość programowania w Javie.  
5.  Ważna licencja Aspose. Jeśli jej nie masz, zdobądź[tymczasowa licencja tutaj](https://purchase.aspose.com/temporary-license/).

## Importuj pakiety

Aby użyć Aspose.Words, musisz zaimportować niezbędne klasy. Poniżej przedstawiono wymagane importy:

```java
import com.aspose.words.*;
import java.util.Date;
```

Upewnij się, że te pakiety zostały prawidłowo dodane do zależności projektu.


W tej sekcji podzielimy ten proces na proste kroki.


## Krok 1: Skonfiguruj swoje dokumenty

Na początek potrzebujesz dwóch dokumentów: jednego reprezentującego oryginał i drugiego reprezentującego edytowaną wersję. Oto jak je utworzyć:

```java
Document doc1 = new Document();
DocumentBuilder builder = new DocumentBuilder(doc1);
builder.writeln("This is the original document.");

Document doc2 = new Document();
builder = new DocumentBuilder(doc2);
builder.writeln("This is the edited document.");
```

 Tworzy dwa dokumenty w pamięci z podstawową zawartością. Możesz również załadować istniejące dokumenty Word za pomocą`new Document("path/to/document.docx")`.


## Krok 2: Sprawdź istniejące wersje

Rewizje w dokumentach Worda oznaczają śledzone zmiany. Przed porównaniem upewnij się, że żaden dokument nie zawiera wcześniejszych rewizji:

```java
if (doc1.getRevisions().getCount() == 0 && doc2.getRevisions().getCount() == 0) {
    System.out.println("No revisions found. Proceeding with comparison...");
}
```

Jeśli istnieją jakieś zmiany, możesz je zaakceptować lub odrzucić przed kontynuowaniem.


## Krok 3: Porównaj dokumenty

 Użyj`compare` metoda znajdowania różnic. Ta metoda porównuje dokument docelowy (`doc2`) z dokumentem źródłowym (`doc1`):

```java
doc1.compare(doc2, "AuthorName", new Date());
```

Tutaj:
- AuthorName to imię i nazwisko osoby dokonującej zmian.
- Data jest znacznikiem czasu porównania.


## Krok 4: Rewizje procesu

Po porównaniu Aspose.Words wygeneruje wersje w dokumencie źródłowym (`doc1`). Przeanalizujmy te rewizje:

```java
for (Revision r : doc1.getRevisions()) {
    System.out.println("Revision type: " + r.getRevisionType());
    System.out.println("Node type: " + r.getParentNode().getNodeType());
    System.out.println("Changed text: " + r.getParentNode().getText());
}
```

Pętla ta dostarcza szczegółowych informacji o każdej rewizji, takich jak rodzaj zmiany i tekst, którego ona dotyczy.


## Krok 5: Zaakceptuj wszystkie poprawki

Jeśli chcesz dokument źródłowy (`doc1`) aby dopasować dokument docelowy (`doc2`), zaakceptuj wszystkie poprawki:

```java
doc1.getRevisions().acceptAll();
```

 To aktualizuje`doc1` aby odzwierciedlić wszystkie zmiany wprowadzone w`doc2`.


## Krok 6: Zapisz zaktualizowany dokument

Na koniec zapisz zaktualizowany dokument na dysku:

```java
doc1.save("Document.Compare.docx");
```

Aby potwierdzić zmiany, ponownie załaduj dokument i sprawdź, czy nie ma w nim żadnych innych wersji:

```java
doc1 = new Document("Document.Compare.docx");
if (doc1.getRevisions().getCount() == 0) {
    System.out.println("Documents are now identical.");
}
```


## Krok 7: Sprawdź równość dokumentów

Aby mieć pewność, że dokumenty są identyczne, porównaj ich tekst:

```java
if (doc1.getText().trim().equals(doc2.getText().trim())) {
    System.out.println("Documents are equal.");
}
```

Jeśli teksty się zgadzają, gratulacje — udało Ci się porównać i zsynchronizować dokumenty!


## Wniosek

Porównywanie dokumentów nie jest już uciążliwe dzięki Aspose.Words for Java. Za pomocą zaledwie kilku linijek kodu możesz wskazać różnice, przetworzyć poprawki i zapewnić spójność dokumentów. Niezależnie od tego, czy zarządzasz wspólnym projektem pisarskim, czy audytujesz dokumenty prawne, ta funkcja zmienia zasady gry.

## Najczęściej zadawane pytania

### Czy mogę porównywać dokumenty zawierające obrazy i tabele?  
Tak, Aspose.Words obsługuje porównywanie złożonych dokumentów, w tym dokumentów zawierających obrazy, tabele i formatowanie.

### Czy potrzebuję licencji, aby korzystać z tej funkcji?  
 Tak, licencja jest wymagana do pełnej funkcjonalności. Uzyskaj[tymczasowa licencja tutaj](https://purchase.aspose.com/temporary-license/).

### Co się stanie, jeśli istnieją już wcześniejsze wersje?  
Aby uniknąć konfliktów, przed porównaniem dokumentów należy je zaakceptować lub odrzucić.

### Czy mogę zaznaczyć zmiany w dokumencie?  
Tak, Aspose.Words pozwala dostosować sposób wyświetlania zmian, np. wyróżniać je.

### Czy ta funkcja jest dostępna w innych językach programowania?  
Tak, Aspose.Words obsługuje wiele języków, w tym .NET i Python.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
