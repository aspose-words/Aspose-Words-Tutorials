---
category: general
date: 2026-09-24
description: Dowiedz się, jak w Javie utworzyć pusty dokument Word i grupować kształty,
  takie jak prostokąty i linie, przy użyciu Aspose.Words. Zawiera kod krok po kroku.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- how to group shapes
- add rectangle shape
- group shapes in word
- set shape size
language: pl
lastmod: 2026-09-24
og_description: Utwórz pusty dokument Word w Javie i dowiedz się, jak grupować kształty,
  dodać kształt prostokąta oraz ustawić rozmiar kształtu za pomocą Aspose.Words.
og_image_alt: Screenshot of a blank Word document with grouped shapes created using
  Java
og_title: Utwórz pusty dokument Word i grupuj kształty w Javie – przewodnik krok po
  kroku
schemas:
- author: Aspose
  dateModified: '2026-09-24'
  description: Learn how to create a blank Word document in Java and group shapes
    like rectangles and lines using Aspose.Words. Includes step‑by‑step code.
  headline: How to create a blank Word document and group shapes in Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word automation
title: Jak utworzyć pusty dokument Word i grupować kształty w Javie
url: /pl/java/images-shapes/how-to-create-a-blank-word-document-and-group-shapes-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak utworzyć pusty dokument Word i grupować kształty w Javie

Jeśli potrzebujesz **utworzyć pusty dokument Word** i następnie uporządkować wiele obiektów rysunkowych, ten przewodnik pokaże Ci dokładnie, jak to zrobić. Korzystając z Aspose.Words for Java możesz wstawić grupowy kształt, dodać prostokątny kształt, narysować linię i kontrolować rozmiar oraz położenie każdego kształtu — wszystko w jednym, uruchamialnym programie.

Przejdziesz przez każdy krok, od inicjalizacji dokumentu po zapisanie finalnego pliku `.docx`. Na końcu zrozumiesz **jak grupować kształty**, **dodać prostokątny kształt** oraz **ustawić rozmiar kształtu**, aby Twoje pliki Word wyglądały dokładnie tak, jak zamierzasz.

## Wymagania wstępne

- Java 17 lub nowsza (kod kompiluje się na dowolnym aktualnym JDK)
- Biblioteka Aspose.Words for Java (pobierz ze [strony Aspose](https://products.aspose.com/words/java))
- IDE lub narzędzie budujące (Maven/Gradle), które umożliwi dodanie pliku JAR Aspose.Words do classpath
- Podstawowa znajomość składni Javy

> **Pro tip:** Użyj Maven do zarządzania zależnościami; dodaj `com.aspose:aspose-words:23.12` (lub najnowszą wersję) do swojego `pom.xml`.

## Krok 1: Utwórz pusty dokument Word

Pierwszym zadaniem jest **utworzyć pusty dokument Word**. Daje to czyste płótno, na którym później możesz wstawiać kształty.

```java
import com.aspose.words.*;

public class GroupShapeDemo {
    public static void main(String[] args) throws Exception {
        // Initialize a new empty document
        Document document = new Document();

        // DocumentBuilder provides convenient methods for inserting content
        DocumentBuilder builder = new DocumentBuilder(document);
```

*Dlaczego to ważne:* Obiekt `Document` reprezentuje cały plik `.docx`. Rozpoczęcie od pustego dokumentu zapewnia, że żadne ukryte formatowanie nie będzie kolidować z dodawanymi kształtami.

## Krok 2: Wstaw grupowy kształt – kontener dla wielu obiektów

**Grupowy kształt** działa jak kontener, który pozwala przenosić, zmieniać rozmiar lub obracać kilka kształtów jednocześnie. To jest sedno **jak grupować kształty** w Wordzie.

```java
        // Insert a group shape of width 300 points and height 200 points
        GroupShape group = builder.insertGroupShape(300.0, 200.0);
```

*Wyjaśnienie:* Metoda `insertGroupShape` tworzy obiekt `GroupShape` i umieszcza go w bieżącej pozycji kursora. Wszystkie kolejne kształty, które `appendChild` do tej grupy, będą traktowane jako jedna jednostka.

## Krok 3: Dodaj prostokątny kształt i ustaw jego rozmiar

Teraz **dodajemy prostokątny kształt** do grupy i **precyzyjnie ustawiamy rozmiar kształtu**.

```java
        // Create a rectangle shape
        Shape rectangle = new Shape(document, ShapeType.RECTANGLE);
        rectangle.setWidth(150.0);   // set shape width
        rectangle.setHeight(100.0);  // set shape height
        rectangle.setLeft(20.0);     // horizontal offset inside the group
        rectangle.setTop(20.0);      // vertical offset inside the group

        // Add the rectangle to the group
        group.appendChild(rectangle);
```

*Dlaczego musisz ustawić rozmiar kształtu:* Szerokość i wysokość kontrolują, jak prostokąt będzie wyglądał na stronie. Metody `setLeft` i `setTop` pozycjonują prostokąt względem początku grupy, dając pełną kontrolę nad układem piksel po pikselu.

## Krok 4: Dodaj linię i skonfiguruj jej wymiary

Linia to kolejny powszechny obiekt rysunkowy. Zastosujemy **logikę podobną do dodawania prostokątnego kształtu** do linii, pokazując, że te same zasady wymiarowania mają zastosowanie.

```java
        // Create a line shape
        Shape line = new Shape(document, ShapeType.LINE);
        line.setWidth(200.0);   // line length
        line.setHeight(0.0);    // height is zero for a horizontal line
        line.setLeft(20.0);
        line.setTop(130.0);

        // Add the line to the same group
        group.appendChild(line);
```

*Kluczowy punkt:* Mimo że linia nie ma wysokości, nadal używasz `setWidth`, aby określić jej długość. Pozycjonowanie (`setLeft`, `setTop`) odbywa się w tym samym układzie współrzędnych co inne kształty.

## Krok 5: Zapisz dokument z grupowanymi kształtami

Na koniec utrwal zmiany, zapisując dokument. Powstanie plik `.docx`, który możesz otworzyć w Microsoft Word, aby zweryfikować rezultat.

```java
        // Save the document to disk
        document.save("GroupShapeDemo.docx");
    }
}
```

**Oczekiwany wynik:** Otwarcie `GroupShapeDemo.docx` pokazuje pustą stronę zawierającą grupowany prostokąt i linię. Wybranie dowolnego kształtu zaznacza całą grupę, umożliwiając ich jednoczesne przemieszczanie.

## Częste pytania i obsługa przypadków brzegowych

| Pytanie | Odpowiedź |
|----------|--------|
| *Czy mogę dodać więcej niż dwa kształty do grupy?* | Tak. Wywołaj `group.appendChild(yourShape)` dla każdego dodatkowego kształtu. |
| *Co zrobić, jeśli potrzebuję innej jednostki (np. centymetry) do określenia rozmiaru?* | Aspose.Words używa punktów (1 punkt = 1/72 cala). Konwertuj przy pomocy `Points = centimeters * 28.3465`. |
| *Czy grupa zachowa układ po otwarciu dokumentu na innym komputerze?* | Absolutnie. Wszystkie dane o rozmiarze i położeniu są zapisane w pliku `.docx`, co czyni układ przenośnym. |
| *Jak później rozgrupować kształty?* | Pobierz obiekt `GroupShape`, a następnie iteruj po `group.getChildNodes(NodeType.SHAPE, true)` i przenieś każde dziecko poza grupę. |
| *Co zrobić, jeśli trzeba obrócić całą grupę?* | Użyj `group.setRotationAngle(double angleInDegrees)` przed zapisem. |

## Pełny, uruchamialny przykład

Poniżej znajduje się kompletny program, który możesz skopiować i wkleić do swojego IDE. Zawiera wszystkie niezbędne importy oraz komentarze.

```java
import com.aspose.words.*;

public class GroupShapeDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank Word document
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Step 2: Insert a group shape (container)
        GroupShape group = builder.insertGroupShape(300.0, 200.0);

        // Step 3: Add a rectangle shape and set its size
        Shape rectangle = new Shape(document, ShapeType.RECTANGLE);
        rectangle.setWidth(150.0);
        rectangle.setHeight(100.0);
        rectangle.setLeft(20.0);
        rectangle.setTop(20.0);
        group.appendChild(rectangle);

        // Step 4: Add a line shape and configure its dimensions
        Shape line = new Shape(document, ShapeType.LINE);
        line.setWidth(200.0);
        line.setHeight(0.0);
        line.setLeft(20.0);
        line.setTop(130.0);
        group.appendChild(line);

        // Step 5: Save the document with the grouped shapes
        document.save("GroupShapeDemo.docx");
    }
}
```

Uruchom program, otwórz `GroupShapeDemo.docx` w Microsoft Word i zobaczysz grupowane kształty dokładnie tak, jak opisano.

## Zakończenie

Teraz wiesz, jak **utworzyć pusty dokument Word**, **grupować kształty w Wordzie**, **dodać prostokątny kształt** oraz **ustawić rozmiar kształtu** przy użyciu Aspose.Words for Java. Umieszczając kształty wewnątrz `GroupShape`, zyskujesz pełną kontrolę nad wspólnym pozycjonowaniem, skalowaniem i rotacją — idealne do diagramów, schematów blokowych lub własnych grafik osadzonych w automatycznych raportach.

**Kolejne kroki:**  
- Zbadaj **jak grupować kształty** z bardziej złożonymi obiektami, takimi jak obrazy czy pola tekstowe.  
- Eksperymentuj z `setRotationAngle`, aby obrócić całą grupę.  
- Połącz tę technikę z funkcją korespondencji seryjnej, aby generować spersonalizowane dokumenty zawierające markowe grafiki.

Śmiało dostosowuj kod do własnych projektów i podziel się wynikami w komentarzach!

## Co powinieneś nauczyć się dalej?

Poniższe samouczki obejmują tematy ściśle powiązane, które rozwijają techniki przedstawione w tym przewodniku. Każde źródło zawiera kompletne działające przykłady kodu z krok po kroku wyjaśnieniami, pomagając Ci opanować dodatkowe funkcje API i odkrywać alternatywne podejścia implementacyjne w własnych projektach.

- [Create rectangle shape in Word with Java – Full Guide](/words/english/java/images-shapes/create-rectangle-shape-in-word-with-java-full-guide/)
- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}