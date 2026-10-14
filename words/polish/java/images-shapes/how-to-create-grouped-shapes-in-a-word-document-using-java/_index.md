---
category: general
date: 2026-10-13
description: Dowiedz się, jak tworzyć grupowane kształty w Wordzie przy użyciu Javy.
  Ten przewodnik pokazuje, jak wstawić grupę kształtów, dodać linię do grupy oraz
  grupować wiele kształtów w całym dokumencie Word.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create grouped shapes
- add line to group
- group multiple shapes word
- insert group shape
language: pl
lastmod: 2026-10-13
og_description: Twórz grupowane kształty w Wordzie przy użyciu Javy. Skorzystaj z
  tego pełnego poradnika, aby wstawić grupę kształtów, dodać linię do grupy oraz grupować
  wiele kształtów w dokumentach Word.
og_image_alt: Screenshot of a Word document showing created grouped shapes
og_title: Tworzenie grupowanych kształtów w Wordzie przy użyciu Javy – przewodnik
  krok po kroku
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Learn how to create grouped shapes in Word with Java. This guide shows
    you how to insert group shape, add line to group, and group multiple shapes word‑wide.
  headline: How to create grouped shapes in a Word document using Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word automation
title: Jak utworzyć grupowane kształty w dokumencie Word przy użyciu Javy
url: /pl/java/images-shapes/how-to-create-grouped-shapes-in-a-word-document-using-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak tworzyć grupowane kształty w dokumencie Word przy użyciu Javy

Jeśli potrzebujesz **create grouped shapes** w pliku Microsoft Word z Javy, ten tutorial przeprowadzi Cię przez cały proces. Zobaczysz, jak **insert group shape**, umieścić prostokąt i linię w tym samym kontenerze oraz ostatecznie zapisać dokument z grupowanymi grafikami.

Grupowanie kształtów ułatwia przenoszenie, zmianę rozmiaru lub stylizowanie kilku obiektów rysunkowych jako jednej jednostki — idealne do diagramów, schematów blokowych lub własnych dekoracji strony. Po zakończeniu tego przewodnika będziesz w stanie **add line to group**, **group multiple shapes word** dokumenty i ponownie używać tej samej techniki dla dowolnej liczby kształtów.

## Wymagania wstępne

- Java 17 lub nowszy zainstalowany na Twojej maszynie deweloperskiej.  
- Licencja Aspose.Words for Java (lub darmowa wersja ewaluacyjna).  
- Projekt Maven lub Gradle, w którym możesz dodać zależność Aspose.Words:

```xml
<!-- Maven example -->
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version>
</dependency>
```

Nie są wymagane dodatkowe biblioteki.

## Krok 1: Wstaw kontener grupy kształtów

Pierwszym krokiem jest **insert group shape** w dokumencie. Ten kontener będzie przechowywać wszystkie kolejne kształty.

```java
import com.aspose.words.*;

public class InsertGroupShapeDemo {
    public static void main(String[] args) throws Exception {
        // Create a blank document and a DocumentBuilder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a group shape container
        Shape groupShape = builder.insertGroupShape();

        // The rest of the code will add shapes to this group
```

`builder.insertGroupShape()` tworzy pusty obiekt `Shape` typu `GROUPSHAPE`. Pomyśl o nim jak o przezroczystym płótnie, które może zawierać inne obiekty rysunkowe.

## Krok 2: Dodaj prostokąt do grupy

Prostokąt często służy jako wizualne tło dla grupy kształtów.

```java
        // Create a rectangle shape
        Shape rectangleShape = new Shape(doc, ShapeType.RECTANGLE);
        rectangleShape.setWidth(100);   // width in points
        rectangleShape.setHeight(50);   // height in points
        rectangleShape.setLeft(0);      // X‑coordinate inside the group
        rectangleShape.setTop(0);       // Y‑coordinate inside the group

        // Append the rectangle to the group container
        groupShape.appendChild(rectangleShape);
```

Ustawienie `Left` i `Top` na `0` pozycjonuje prostokąt w lewym górnym rogu grupy. Możesz zmienić te wartości, aby przesunąć kształt w grupie.

## Krok 3: **Add line to group** – utwórz kształt linii

Teraz **add line to group**. Linia pojawi się pod prostokątem.

```java
        // Create a line shape
        Shape lineShape = new Shape(doc, ShapeType.LINE);
        lineShape.setWidth(100);   // length of the line
        lineShape.setTop(60);      // vertical position (60 points down)

        // Append the line to the same group
        groupShape.appendChild(lineShape);
```

Właściwość `Top` przesuwa linię o 60 punktów poniżej prostokąta, tworząc prosty układ warstwowy. Możesz także ustawić `Left`, jeśli potrzebny jest poziomy offset.

## Krok 4: Zapisz dokument z grupowanymi kształtami

```java
        // Save the document to a .docx file
        doc.save("YOUR_DIRECTORY/GroupShapeDemo.docx");
    }
}
```

Kiedy otworzysz `GroupShapeDemo.docx` w Microsoft Word, zobaczysz jedną grupę zawierającą zarówno prostokąt, jak i linię. Wybranie grupy pozwala przenieść oba kształty razem, co pokazuje, że pomyślnie **group multiple shapes word**.

## Pełny, działający przykład

Poniżej znajduje się kompletny program ze wszystkimi importami i obsługą błędów. Skopiuj go do swojego IDE, zamień `YOUR_DIRECTORY` na istniejącą ścieżkę folderu i uruchom.

```java
import com.aspose.words.*;

public class InsertGroupShapeDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a blank document and a DocumentBuilder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Insert a group shape container
        Shape groupShape = builder.insertGroupShape();

        // Step 3: Add a rectangle to the group
        Shape rectangleShape = new Shape(doc, ShapeType.RECTANGLE);
        rectangleShape.setWidth(100);
        rectangleShape.setHeight(50);
        rectangleShape.setLeft(0);
        rectangleShape.setTop(0);
        groupShape.appendChild(rectangleShape);

        // Step 4: Add a line to the group
        Shape lineShape = new Shape(doc, ShapeType.LINE);
        lineShape.setWidth(100);
        lineShape.setTop(60);
        groupShape.appendChild(lineShape);

        // Step 5: Save the document
        doc.save("YOUR_DIRECTORY/GroupShapeDemo.docx");
    }
}
```

### Oczekiwany wynik

- Plik o nazwie `GroupShapeDemo.docx` pojawia się w docelowym folderze.  
- Otwarcie pliku w Wordzie pokazuje pojedynczy grupowany obiekt zawierający prostokąt na górze i linię poniżej.  
- Przeciągnięcie grupy przesuwa oba kształty razem, potwierdzając, że **created grouped shapes** zostały pomyślnie utworzone.

## Wskazówki i typowe pułapki

- **Pro tip:** Jeśli potrzebujesz obrócić lub stylizować pojedyncze kształty wewnątrz grupy, wywołaj odpowiednie settery (`setRotation`, `getFill().setForeColor` itp.) przed dodaniem ich do grupy. Grupa zachowa te właściwości wizualne.  
- **Watch out for:** Zapomnienie o ustawieniu właściwości `Top` dla linii może spowodować nakładanie się na prostokąt, co sprawi, że grupa będzie wyglądać na zagracona.  
- **Edge case:** Gdy dodajesz więcej niż dwa kształty, pamiętaj, że współrzędne każdego dziecka są względem początku grupy (0,0). Zaplanuj układ odpowiednio.  
- **Performance note:** Grupowanie dużej liczby kształtów (setek) może nieco zwiększyć rozmiar pliku, ale upraszcza późniejszą edycję w Wordzie.

## Jak programowo **group multiple shapes word** dokumenty

Wzorzec przedstawiony powyżej — utworzyć kontener grupy, skonfigurować każdy kształt dziecka i dodać — działa dla dowolnej liczby kształtów: kół, obrazów, pól tekstowych itp. Po prostu powtórz kroki „create shape → set properties → append” przed wywołaniem `doc.save()`.

Jeśli potrzebujesz **add line to group** po tym, jak grupa już zawiera inne kształty, możesz pobrać istniejącą grupę za pomocą:

```java
Shape existingGroup = (Shape) doc.getChildNodes(NodeType.SHAPE, true)
                                 .stream()
                                 .filter(s -> ((Shape) s).getShapeType() == ShapeType.GROUPSHAPE)
                                 .findFirst()
                                 .orElseThrow(() -> new IllegalStateException("No group found"));
existingGroup.appendChild(lineShape);
```

To pokazuje, że możesz modyfikować grupę w dowolnym momencie cyklu życia dokumentu.

## Zakończenie

Teraz wiesz, jak **create grouped shapes** w dokumencie Word przy użyciu Javy i Aspose.Words. Dzięki **inserting group shape**, **adding line to group** i **group multiple shapes word**, możesz tworzyć złożone rysunki zachowujące się jak pojedynczy obiekt — idealne do diagramów, szablonów i automatycznego generowania raportów.

Następnie, zapoznaj się z następującymi powiązanymi tematami:

- **Applying styles to grouped shapes** – dowiedz się, jak ustawić kolory wypełnienia, obramowania i efekty dla wszystkich elementów jednocześnie.  
- **Exporting grouped shapes to PDF** – zobacz, jak ta sama grupa pozostaje po konwersji dokumentu do PDF.  
- **Animating shapes with VBA** – połącz grupy wygenerowane w Javie z makrami Worda, aby uzyskać interaktywne dokumenty.

Śmiało eksperymentuj z różnymi typami kształtów, rozmiarami i pozycjami. Grupowanie daje elastyczność traktowania wielu obiektów jako jednego, upraszczając zarówno kod, jak i interakcję użytkownika. Szczęśliwego kodowania!

## Co powinieneś nauczyć się dalej?

Poniższe tutoriale obejmują ściśle powiązane tematy, które rozwijają techniki przedstawione w tym przewodniku. Każde źródło zawiera kompletne działające przykłady kodu z wyjaśnieniami krok po kroku, aby pomóc Ci opanować dodatkowe funkcje API i odkrywać alternatywne podejścia implementacyjne w własnych projektach.

- [Utwórz dokument Word w Javie – Dodaj prostokątny kształt z efektem cienia](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Utwórz prostokątny kształt w Wordzie przy użyciu Javy – Pełny przewodnik](/words/english/java/images-shapes/create-rectangle-shape-in-word-with-java-full-guide/)
- [Utwórz grupowy kształt w dokumencie Word przy użyciu Aspose.Words dla .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}