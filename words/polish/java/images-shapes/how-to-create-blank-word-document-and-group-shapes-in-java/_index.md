---
category: general
date: 2026-09-27
description: Utwórz pusty dokument Word w Javie i grupuj kształty przy użyciu Aspose.Words.
  Dowiedz się, jak ustawić rozmiar kształtu, ustawić kolor wypełnienia kształtu oraz
  dodać element podrzędny do grupy.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- group shapes in word
- set shape size
- set shape fill color
- append child to group
language: pl
lastmod: 2026-09-27
og_description: Utwórz pusty dokument Word w Javie przy użyciu Aspose.Words. Ten samouczek
  pokazuje, jak grupować kształty w Wordzie, ustawiać rozmiar kształtu, ustawiać kolor
  wypełnienia kształtu oraz dodawać element podrzędny do grupy.
og_image_alt: Screenshot of a blank Word document with grouped shapes created using
  Java
og_title: Utwórz pusty dokument Word i grupuj kształty w Javie – przewodnik krok po
  kroku
schemas:
- author: Aspose
  dateModified: '2026-09-27'
  description: Create a blank Word document in Java and group shapes using Aspose.Words.
    Learn to set shape size, set shape fill color, and append child to group.
  headline: How to create blank word document and group shapes in Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word automation
title: Jak utworzyć pusty dokument Word i grupować kształty w Javie
url: /pl/java/images-shapes/how-to-create-blank-word-document-and-group-shapes-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak utworzyć pusty dokument Word i grupować kształty w Javie

Jeśli potrzebujesz **utworzyć pusty dokument Word** programowo, ten przewodnik pokaże Ci dokładnie, jak to zrobić przy użyciu Aspose.Words for Java. Dowiesz się także, jak **grupować kształty w Wordzie**, ustawić rozmiar każdego kształtu, zastosować kolor wypełnienia oraz **dołączyć element potomny do grupy**, aby obiekty zachowywały się jako jedna jednostka.

Praca z plikami Word z poziomu kodu oszczędza ręcznego formatowania i umożliwia automatyczne generowanie raportów, umów czy broszur marketingowych. Po zakończeniu tego samouczka będziesz mieć działający program w Javie, który tworzy plik `.docx` zawierający niebieski prostokąt i obraz, oba zgrupowane razem.

## Wymagania wstępne

Zanim rozpoczniesz, upewnij się, że masz:

- Java 17 (lub nowszy JDK) zainstalowany.
- Maven lub Gradle do zarządzania zależnościami.
- Licencję Aspose.Words for Java (darmowa wersja ewaluacyjna wystarczy do testów).
- Przykładowy plik obrazu (np. `sample.jpg`) umieszczony w folderze, do którego możesz odwołać się w kodzie.

> **Pro tip:** Trzymaj pliki obrazów w katalogu `resources` i wczytuj je za pomocą `ClassLoader.getResourceAsStream`, aby uniknąć twardo zakodowanych ścieżek bezwzględnych.

## Krok 1: Utwórz pusty dokument Word i dodaj GroupShape

Pierwszym krokiem jest utworzenie nowego obiektu `Document`, który reprezentuje pusty plik Word, a następnie wstawienie `GroupShape`. Grupa będzie pełnić rolę kontenera dla wszystkich kształtów dodawanych później.

```java
import com.aspose.words.*;

public class GroupShapesDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document
        Document doc = new Document();                     // create blank word document
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a GroupShape that will act as a container for other shapes
        GroupShape group = builder.insertGroupShape();     // group shapes in word
```

*Dlaczego to ważne:* `GroupShape` pozwala na przemieszczanie, obracanie lub formatowanie wielu kształtów jednocześnie, co jest niezbędne przy złożonych układach, takich jak diagramy czy znaki wodne.

## Krok 2: Wstaw prostokąt i **ustaw rozmiar kształtu**

Następnie tworzysz prostokąt, definiujesz jego wymiary i dodajesz go do grupy. To demonstruje operację **ustaw rozmiar kształtu**.

```java
        // Step 2: Create a rectangle shape, configure its size, and add it to the group
        Shape rectangle = new Shape(doc, ShapeType.RECTANGLE);
        rectangle.setWidth(100.0);                         // set shape size – width 100 points
        rectangle.setHeight(50.0);                         // set shape size – height 50 points
        rectangle.setFillColor(java.awt.Color.BLUE);      // set shape fill color to blue
        group.appendChild(rectangle);                     // append child to group
```

*Wyjaśnienie:* `setWidth` i `setHeight` kontrolują dokładny rozmiar kształtu w punktach (1 punkt = 1/72 cala). Dostosuj te wartości, aby spełniały wymagania Twojego układu.

## Krok 3: **Ustaw kolor wypełnienia kształtu** dla prostokąta

Tło prostokąta jest ustawione na niebieskie przy użyciu `setFillColor`. Możesz użyć dowolnej stałej `java.awt.Color` lub stworzyć własny kolor RGB.

```java
        // The fill color was already applied in the previous step.
        // If you need a different color later, just call setFillColor again:
        // rectangle.setFillColor(new java.awt.Color(255, 165, 0)); // orange
```

*Dlaczego jest to przydatne:* Kolory wypełnienia pomagają wizualnie odróżnić obiekty, szczególnie gdy później eksportujesz dokument do PDF lub drukujesz go.

## Krok 4: Wstaw obraz i **dołącz element potomny do grupy**

Teraz dodaj obraz do tego samego `GroupShape`. Obraz jest wstawiany za pomocą `DocumentBuilder.insertImage`, a następnie dołączany do grupy, aby poruszał się razem z prostokątem.

```java
        // Step 4: Insert an image and add it to the same group
        Shape picture = builder.insertImage("YOUR_DIRECTORY/sample.jpg");
        group.appendChild(picture);                       // append child to group
```

*Przypadek brzegowy:* Jeśli ścieżka do obrazu jest nieprawidłowa, Aspose.Words zgłosi `FileNotFoundException`. Użyj ścieżki względnej lub wczytaj obraz z zasobów, aby uniknąć tego problemu.

## Krok 5: **Zapisz dokument z zgrupowanymi kształtami**

Na koniec zapisz dokument na dysku. Powstały plik będzie zawierał prostokąt i obraz zgrupowane razem.

```java
        // Step 5: Save the document with the grouped shapes
        doc.save("YOUR_DIRECTORY/GroupShape.docx");       // creates the blank word document with grouped shapes
    }
}
```

### Oczekiwany wynik

- Plik o nazwie `GroupShape.docx` pojawia się w określonym katalogu.
- Otwierając go w Microsoft Word, zobaczysz pustą stronę z niebieskim prostokątem i wybranym obrazem, oba zaznaczone jako pojedynczy obiekt (można je razem przesuwać lub zmieniać ich rozmiar).

![create blank word document with grouped shapes](/images/grouped-shapes.png "create blank word document with grouped shapes")

*Zrzut ekranu powyżej pokazuje ostateczne zgrupowane kształty w nowo utworzonym dokumencie Word.*

## Typowe warianty i dodatkowe wskazówki

| Sytuacja | Jak sobie radzić |
|-----------|-----------------|
| **Wiele obrazów** | Wstaw każdy obraz przy pomocy `builder.insertImage` i wywołaj `group.appendChild(picture)` dla każdego z nich. |
| **Różne typy kształtów** | Użyj `ShapeType.OVAL`, `ShapeType.LINE` itp., przy tworzeniu obiektu `Shape`. |
| **Zmiana pozycji grupy** | Po dodaniu wszystkich elementów potomnych, ustaw `group.setLeft(x)` i `group.setTop(y)`, aby przesunąć całą grupę. |
| **Eksport do PDF** | Wywołaj `doc.save("output.pdf")` po zgrupowaniu; PDF zachowa grupowanie. |
| **Wymuszanie licencji** | Jeśli używasz wersji ewaluacyjnej, pojawi się znak wodny. Zainstaluj ważną licencję, aby go usunąć. |

## Podsumowanie

Teraz wiesz, jak **utworzyć pusty dokument Word**, wstawić **GroupShape**, **ustawić rozmiar kształtu**, **ustawić kolor wypełnienia kształtu** oraz **dołączyć element potomny do grupy** przy użyciu Aspose.Words for Java. Ten wzorzec pozwala budować złożone, programowe układy, które później można edytować w Wordzie lub eksportować do innych formatów.

Następnie wypróbuj, jak **grupować kształty w Wordzie** z polami tekstowymi, dodać hiperłącza do kształtów lub zautomatyzować generowanie raportów wielostronicowych. Te same zasady mają zastosowanie — po prostu twórz dodatkowe kształty, konfigurować ich właściwości i dołączaj je do tej samej grupy.

Powodzenia w kodowaniu!

## Co powinieneś nauczyć się dalej?

Poniższe samouczki obejmują ściśle powiązane tematy, które rozwijają techniki przedstawione w tym przewodniku. Każdy zasób zawiera kompletne, działające przykłady kodu z wyjaśnieniami krok po kroku, aby pomóc Ci opanować dodatkowe funkcje API i odkrywać alternatywne podejścia implementacyjne w własnych projektach.

- [Create rectangle shape in Word with Java – Full Guide](/words/english/java/images-shapes/create-rectangle-shape-in-word-with-java-full-guide/)
- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}