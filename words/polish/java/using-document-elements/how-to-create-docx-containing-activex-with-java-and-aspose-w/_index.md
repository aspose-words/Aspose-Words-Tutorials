---
category: general
date: 2026-09-27
description: Utwórz plik docx zawierający ActiveX w Javie przy użyciu Aspose.Words.
  Dowiedz się, jak krok po kroku wstawić przycisk polecenia ActiveX.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create docx containing activex
- insert activex command button
- Aspose.Words Java
- ActiveX control in Word
- generate Word document programmatically
language: pl
lastmod: 2026-09-27
og_description: Utwórz plik docx zawierający ActiveX w Javie przy użyciu Aspose.Words.
  Postępuj zgodnie z tym przewodnikiem, aby wstawić przycisk polecenia ActiveX i zapisać
  dokument.
og_image_alt: Screenshot of a Word document that contains an ActiveX command button
og_title: Utwórz plik docx zawierający ActiveX w Javie – kompletny przewodnik
schemas:
- author: Aspose
  dateModified: '2026-09-27'
  description: Create docx containing ActiveX in Java using Aspose.Words. Learn to
    insert an ActiveX command button step‑by‑step.
  headline: How to create docx containing ActiveX with Java and Aspose.Words
  type: TechArticle
- description: Create docx containing ActiveX in Java using Aspose.Words. Learn to
    insert an ActiveX command button step‑by‑step.
  name: How to create docx containing ActiveX with Java and Aspose.Words
  steps:
  - name: The document should show a single page with a button labeled **Click Me**
      positioned near the top‑left corner.
    text: The document should show a single page with a button labeled **Click Me**
      positioned near the top‑left corner.
  - name: If the button does not appear, check that **ActiveX controls are enabled**
      in Word’s Trust Center (File → Options → Trust Center → Trust Center Settings
      → ActiveX Settings).
    text: If the button does not appear, check that **ActiveX controls are enabled**
      in Word’s Trust Center (File → Options → Trust Center → Trust Center Settings
      → ActiveX Settings).
  - name: The button is functional only on Windows versions of Word that support ActiveX.
      On macOS or web‑based Word, the control will be displayed as a static image.
    text: The button is functional only on Windows versions of Word that support ActiveX.
      On macOS or web‑based Word, the control will be displayed as a static image.
  type: HowTo
tags:
- docx
- activex
- java
- aspose-words
title: Jak utworzyć plik docx zawierający ActiveX przy użyciu Javy i Aspose.Words
url: /pl/java/using-document-elements/how-to-create-docx-containing-activex-with-java-and-aspose-w/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak utworzyć docx zawierający ActiveX przy użyciu Javy i Aspose.Words

Jeśli potrzebujesz **utworzyć docx zawierający ActiveX**, ten przewodnik pokaże Ci kompletne rozwiązanie. Nauczysz się, jak **wstawić przycisk polecenia ActiveX** do pliku Word przy użyciu Aspose.Words for Java, a następnie zapisać wynik jako .docx, który można otworzyć w Microsoft Word.

Programowe generowanie dokumentu Word oszczędza ręcznej edycji i zapewnia spójność raportów, umów czy szablonów formularzy. Poniższe kroki obejmują wszystko – od konfiguracji projektu po obsługę typowych problemów, dzięki czemu możesz zintegrować tę technikę z dowolną aplikacją Java.

## Wymagania wstępne

Zanim rozpoczniesz, upewnij się, że masz:

* Zainstalowany Java Development Kit (JDK) 8 lub nowszy.
* Maven 3.6+ (lub inny preferowany system budowania).
* Plik licencyjny Aspose.Words for Java (darmowa wersja ewaluacyjna wystarczy do testów).
* Zainstalowany Microsoft Word na docelowym komputerze, jeśli chcesz wizualnie zweryfikować kontrolkę ActiveX.

Te elementy są niezbędne, ponieważ Aspose.Words udostępnia API tworzące dokument, a Word jest potrzebny do renderowania kontrolki ActiveX.

## Krok 1: Konfiguracja projektu Maven

Utwórz nowy projekt Maven lub dodaj zależność Aspose.Words do istniejącego pliku `pom.xml`:

```xml
<project>
    <modelVersion>4.0.0</modelVersion>
    <groupId>com.example</groupId>
    <artifactId>activex-docx-demo</artifactId>
    <version>1.0.0</version>
    <properties>
        <maven.compiler.source>1.8</maven.compiler.source>
        <maven.compiler.target>1.8</maven.compiler.target>
    </properties>

    <dependencies>
        <!-- Aspose.Words for Java -->
        <dependency>
            <groupId>com.aspose</groupId>
            <artifactId>aspose-words</artifactId>
            <version>24.10</version> <!-- use the latest stable version -->
        </dependency>
    </dependencies>
</project>
```

> **Porada:** Utrzymuj wersję Aspose.Words zgodną z oficjalnymi notatkami wydania, aby korzystać z poprawek błędów i nowych funkcji ActiveX.

## Krok 2: Napisz kod Java tworzący dokument

Utwórz klasę o nazwie `ActiveXDocxCreator`. Poniższy kod zawiera wszystkie wymagane importy, metodę `main` oraz szczegółowe komentarze wyjaśniające każde działanie.

```java
package com.example.activex;

import com.aspose.words.*;
import java.io.File;

/**
 * Demonstrates how to create a DOCX file that contains an ActiveX command button.
 * The resulting file can be opened in Microsoft Word where the button appears
 * on the first page.
 */
public class ActiveXDocxCreator {

    public static void main(String[] args) {
        // 1. Initialize a new empty document and a DocumentBuilder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2. Insert an ActiveX Forms2OleControl at the current cursor position.
        Forms2OleControl commandButton = builder.insertForms2OleControl();

        // 3. Configure the control to be a CommandButton and set its caption.
        commandButton.setControlType(Forms2OleControlType.COMMANDBUTTON);
        commandButton.setCaption("Click Me");

        // 4. Position the button on the page.
        //    The coordinates are measured in points (1 point = 1/72 inch).
        commandButton.setLeft(100); // 100 points from the left margin
        commandButton.setTop(150);  // 150 points from the top margin

        // 5. (Optional) Set the size of the button for better visibility.
        commandButton.setWidth(120);
        commandButton.setHeight(30);

        // 6. Save the document to the desired location.
        String outputPath = "output/ActiveXCommandButton.docx";
        try {
            // Ensure the output directory exists.
            new File("output").mkdirs();
            doc.save(outputPath);
            System.out.println("Document saved successfully to " + outputPath);
        } catch (Exception e) {
            System.err.println("Error while saving the document: " + e.getMessage());
        }
    }
}
```

### Dlaczego każda linia ma znaczenie

* `Document` jest kontenerem dla całej zawartości Word. Utworzenie nowej instancji daje czyste płótno.
* `DocumentBuilder` zapewnia płynne API do wstawiania elementów; automatycznie śledzi punkt wstawiania.
* `insertForms2OleControl()` tworzy ogólny placeholder kontrolki OLE. Aspose.Words traktuje go jako kontener ActiveX.
* `setControlType(Forms2OleControlType.COMMANDBUTTON)` informuje Word, że placeholder ma być renderowany jako przycisk CommandButton.
* `setCaption("Click Me")` definiuje tekst wyświetlany na przycisku.
* `setLeft` i `setTop` umieszczają przycisk względem marginesów strony. Dostosuj te wartości do swojego układu.
* `setWidth` i `setHeight` są opcjonalne, ale poprawiają wygląd przycisku, szczególnie gdy domyślny rozmiar jest zbyt mały.
* `doc.save` zapisuje strukturę w pamięci do fizycznego pliku .docx, który Word może otworzyć.

## Krok 3: Zweryfikuj wygenerowany dokument

Otwórz `output/ActiveXCommandButton.docx` w Microsoft Word:

1. Dokument powinien wyświetlać jedną stronę z przyciskiem oznaczonym **Click Me** umieszczonym w pobliżu lewego górnego rogu.
2. Jeśli przycisk się nie pojawia, sprawdź, czy **kontrolki ActiveX są włączone** w Centrum zaufania Worda (Plik → Opcje → Centrum zaufania → Ustawienia Centrum zaufania → Ustawienia ActiveX).
3. Przycisk działa tylko w wersjach Worda na Windows, które obsługują ActiveX. Na macOS lub w wersji web‑owej Worda kontrolka zostanie wyświetlona jako statyczny obraz.

## Krok 4: Obsługa typowych przypadków brzegowych

| Sytuacja | Powód | Zalecane działanie |
|-----------|--------|--------------------|
| Przycisk nie jest widoczny po otwarciu pliku | Ustawienia zabezpieczeń Worda blokują ActiveX | Włącz „Uruchamiaj wszystkie kontrolki bez ograniczeń” dla zaufanych lokalizacji. |
| Wygenerowany plik .docx nie może zostać otwarty | Niekompatybilna wersja Aspose.Words | Uaktualnij do najnowszej wersji Aspose.Words; starsze wersje mogą nie osadzać wymaganych części OLE prawidłowo. |
| Potrzebujesz, aby przycisk uruchamiał makro | ActiveX sam w sobie nie zawiera kodu makra | Połącz kontrolkę ActiveX z makrem VBA obsługującym zdarzenie `Click`. Użyj metody `DocumentBuilder.insertOleObject`, aby osadzić szablon z włączonym makrem. |
| Układ jest nieprawidłowy przy różnych rozmiarach stron | Współrzędne są w punktach bezwzględnych | Użyj `builder.getPageSetup().setPageWidth` i `setPageHeight`, aby ustandaryzować rozmiar strony przed pozycjonowaniem kontrolki. |

## Krok 5: Rozszerzanie rozwiązania

Możesz wstawiać inne kontrolki ActiveX, zmieniając wartość wyliczenia `ControlType`:

```java
commandButton.setControlType(Forms2OleControlType.CHECKBOX); // inserts a checkbox
```

Aspose.Words obsługuje także wstawianie **ActiveX text boxów**, **list boxów** i **combo boxów**. Te same metody pozycjonowania (`setLeft`, `setTop`, `setWidth`, `setHeight`) mają zastosowanie.

Jeśli potrzebujesz umieścić wiele kontrolek, wywołuj `builder.insertForms2OleControl()` wielokrotnie i odpowiednio dostosowuj współrzędne każdej z nich.

## Pełny plik źródłowy

Poniżej znajduje się cały plik `ActiveXDocxCreator.java` gotowy do skopiowania i wklejenia:

```java
package com.example.activex;

import com.aspose.words.*;
import java.io.File;

public class ActiveXDocxCreator {
    public static void main(String[] args) {
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        Forms2OleControl commandButton = builder.insertForms2OleControl();
        commandButton.setControlType(Forms2OleControlType.COMMANDBUTTON);
        commandButton.setCaption("Click Me");
        commandButton.setLeft(100);
        commandButton.setTop(150);
        commandButton.setWidth(120);
        commandButton.setHeight(30);

        String outputPath = "output/ActiveXCommandButton.docx";
        try {
            new File("output").mkdirs();
            doc.save(outputPath);
            System.out.println("Document saved successfully to " + outputPath);
        } catch (Exception e) {
            System.err.println("Error while saving the document: " + e.getMessage());
        }
    }
}
```

Uruchomienie tego programu generuje **docx zawierający ActiveX**, który możesz dystrybuować do użytkowników potrzebujących interaktywnych formularzy.

## Podsumowanie

Wiesz już, jak **utworzyć docx zawierający ActiveX** przy użyciu Javy i Aspose.Words oraz jak **programowo wstawić przycisk polecenia ActiveX**. Tutorial obejmował konfigurację projektu, pełny kod źródłowy, kroki weryfikacji oraz strategie radzenia sobie z typowymi problemami.

Od tego momentu możesz rozważyć:

* Dodanie makr VBA reagujących na kliknięcie przycisku.
* Osadzenie innych kontrolek ActiveX, takich jak pola wyboru czy combo boxy.
* Automatyzację generowania formularzy wielostronicowych z dynamicznymi danymi.

Eksperymentuj z różnymi współrzędnymi, rozmiarami i typami kontrolek, aby dopasować je do konkretnego układu dokumentu. Powodzenia w kodowaniu!


## Co powinieneś nauczyć się dalej?


Poniższe samouczki dotyczą ściśle powiązanych tematów, które rozwijają techniki przedstawione w tym przewodniku. Każdy zasób zawiera kompletny, działający kod oraz wyczerpujące wyjaśnienia krok po kroku, aby pomóc Ci opanować dodatkowe funkcje API i odkrywać alternatywne podejścia w własnych projektach.

- [Using OLE Objects and ActiveX Controls in Aspose.Words for Java](/words/english/java/using-document-elements/using-ole-objects-and-activex/)
- [How to create form fields and add content using DocumentBuilder in Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Create rectangle shape in Word with Aspose.Words – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}