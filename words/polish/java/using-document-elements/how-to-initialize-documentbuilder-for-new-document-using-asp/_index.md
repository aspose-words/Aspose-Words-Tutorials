---
category: general
date: 2026-10-04
description: Dowiedz się, jak zainicjować DocumentBuilder dla nowego dokumentu i dodać
  przycisk ActiveX przy użyciu Aspose.Words w Javie. Przewodnik krok po kroku z pełnym
  kodem.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- initialize DocumentBuilder for new document
- insert ActiveX button
- Forms2OleControl command button
- Aspose.Words DocumentBuilder example
- create Word document with ActiveX
language: pl
lastmod: 2026-10-04
og_description: Zainicjalizuj DocumentBuilder dla nowego dokumentu i osadź przycisk
  polecenia ActiveX przy użyciu Aspose.Words Java API. Zapoznaj się z tym zwięzłym
  samouczkiem.
og_image_alt: Screenshot showing DocumentBuilder initialized for a new document with
  an ActiveX button
og_title: Zainicjalizuj DocumentBuilder dla nowego dokumentu – kompletny przewodnik
  Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-10-04'
  description: Learn how to initialize DocumentBuilder for new document and add an
    ActiveX button with Aspose.Words in Java. Step‑by‑step guide with full code.
  headline: How to initialize DocumentBuilder for new document using Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- Java
- DocumentBuilder
- ActiveX
title: Jak zainicjować DocumentBuilder dla nowego dokumentu przy użyciu Aspose.Words
url: /pl/java/using-document-elements/how-to-initialize-documentbuilder-for-new-document-using-asp/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak zainicjować DocumentBuilder dla nowego dokumentu przy użyciu Aspose.Words

Jeśli potrzebujesz **zainicjować DocumentBuilder dla nowego dokumentu** w projekcie Java, ten tutorial pokaże Ci dokładne kroki. Zobaczysz, jak utworzyć pusty plik Word, dodać przycisk polecenia ActiveX i zapisać wynik — wszystko w jednym, samodzielnym przykładzie kodu.

Praca z dokumentami Word programowo często oznacza obsługę szczegółów niskiego poziomu, takich jak kontrolki formularzy. Po zakończeniu tego przewodnika będziesz w stanie osadzić przycisk ActiveX bez wychodzenia z IDE, co jest przydatne przy generowaniu szablonów, automatycznych raportów lub interaktywnych formularzy.

## Prerequisites

Before you start, make sure you have:

* Java 17 lub nowszy zainstalowany  
* Maven 3.8+ (lub Gradle, jeśli wolisz)  
* Licencja Aspose.Words for Java (bezpłatna wersja próbna działa do testów)  
* Podstawowa znajomość składni Java  

If you’re new to Aspose.Words, the library provides a high‑level API for creating, editing, and saving Word documents. The `DocumentBuilder` class is the primary entry point for constructing document content.

## Krok 1: Skonfiguruj projekt Maven

Create a new Maven project (or add to an existing one) and include the Aspose.Words dependency:

```xml
<!-- pom.xml -->
<project>
    <modelVersion>4.0.0</modelVersion>
    <groupId>com.example</groupId>
    <artifactId>activex-demo</artifactId>
    <version>1.0.0</version>
    <dependencies>
        <dependency>
            <groupId>com.aspose</groupId>
            <artifactId>aspose-words</artifactId>
            <version>24.9</version> <!-- Use the latest stable version -->
        </dependency>
    </dependencies>
</project>
```

> **Wskazówka:** Utrzymuj wersję biblioteki aktualną; nowsze wydania dodają obsługę dodatkowych kontrolek formularzy i poprawiają wydajność.

## Krok 2: Zainicjuj `DocumentBuilder` dla nowego dokumentu

The core of the tutorial is the **initialize DocumentBuilder for new document** operation. You first create an empty `Document` instance, then pass it to the `DocumentBuilder` constructor.

```java
import com.aspose.words.*;

public class ActiveXButtonDemo {
    public static void main(String[] args) throws Exception {
        // Step 2.1: Create a new empty document
        Document doc = new Document();

        // Step 2.2: Initialize DocumentBuilder for new document
        DocumentBuilder builder = new DocumentBuilder(doc);
```

*Dlaczego to ważne:* Inicjalizacja `DocumentBuilder` wiąże builder z konkretnym obiektem `Document`, co pozwala dodawać akapity, tabele lub kontrolki formularzy bezpośrednio do tego dokumentu. Bez tego kroku builder nie miałby docelowego dokumentu, na którym mógłby pracować.

## Krok 3: Wstaw kontrolkę przycisku polecenia ActiveX

Aspose.Words exposes the `Forms2OleControl` class to embed legacy ActiveX controls. The following code adds a **Forms2OleControl command button** to the current cursor position.

```java
        // Step 3.1: Insert an ActiveX command button control
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON);

        // Step 3.2: Set the button caption (the text displayed on the button)
        commandButton.setCaption("Click Me");
```

### Co to jest przycisk polecenia ActiveX?

An ActiveX command button is a legacy UI element that can run macros or trigger events when a user clicks it inside a Word document. Although modern Office versions favor Content Controls, many enterprise templates still rely on ActiveX for backward compatibility.

## Krok 4: Zapisz dokument

After inserting the control, you simply call `save`. The file will contain the ActiveX button and can be opened in Microsoft Word.

```java
        // Step 4: Save the document containing the ActiveX button
        String outputPath = "output/ActiveXButton.docx";
        doc.save(outputPath);
        System.out.println("Document saved to " + outputPath);
    }
}
```

When you open `ActiveXButton.docx` in Word, you’ll see a button labeled **Click Me**. Clicking the button will do nothing unless you attach a macro, but the control itself is fully functional.

## Pełny, gotowy do uruchomienia przykład

Below is the complete program you can copy‑paste into `src/main/java/com/example/ActiveXButtonDemo.java`. It includes all imports and error handling needed for a quick test.

```java
package com.example;

import com.aspose.words.*;

public class ActiveXButtonDemo {
    public static void main(String[] args) {
        try {
            // Step 1: Create a new empty document
            Document doc = new Document();

            // Step 2: Initialize DocumentBuilder for new document
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Step 3: Insert an ActiveX command button control
            Forms2OleControl commandButton = builder.insertForms2OleControl(
                    Forms2OleControlType.COMMANDBUTTON);
            commandButton.setCaption("Click Me");

            // Step 4: Save the document
            String outputPath = "output/ActiveXButton.docx";
            doc.save(outputPath);
            System.out.println("Document saved to " + outputPath);
        } catch (Exception e) {
            System.err.println("Error creating document: " + e.getMessage());
            e.printStackTrace();
        }
    }
}
```

**Oczekiwany wynik**

```
Document saved to output/ActiveXButton.docx
```

Open the generated file in Microsoft Word 2016 or later; you should see a button labeled *Click Me* placed at the top of the first page.

## Typowe warianty i przypadki brzegowe

| Scenariusz | Dostosowanie |
|----------|------------|
| **Dodaj przycisk do konkretnego akapitu** | Przesuń kursor buildera za pomocą `builder.moveToParagraph(index, NodeType.PARAGRAPH);` przed wywołaniem `insertForms2OleControl`. |
| **Ustaw rozmiar przycisku** | Użyj `commandButton.setWidth(100);` i `commandButton.setHeight(30);`, aby określić wymiary w punktach. |
| **Dodaj makro do przycisku** | Po zapisaniu dokumentu otwórz go w Wordzie, włącz kartę Deweloper i ręcznie dołącz makro VBA do przycisku (kontrolki ActiveX nie mogą być skryptowane bezpośrednio z Aspose.Words). |
| **Docelowy format .doc (binarny)** | Zmień `doc.save(outputPath, SaveFormat.DOC);`, aby wygenerować starszy plik Word 97‑2003. |
| **Uruchom na Androidzie** | Użyj Aspose.Words for Android poprzez jego API Java; ten sam kod działa, o ile biblioteka jest dołączona do APK. |

## Wskazówki rozwiązywania problemów

* **`java.lang.NoClassDefFoundError`** – Ensure the Aspose.Words JAR is on the classpath. Maven automatically adds it; for manual builds, place the JAR in `libs/` and add it to your IDE’s libraries.  
* **Button does not appear in Word** – Verify that the *Show legacy forms* option is enabled in Word’s Trust Center (`File → Options → Trust Center → Trust Center Settings → Macro Settings`).  
* **License exception** – If you run the code without a valid license, Aspose.Words will insert a watermark. Register a free trial or purchase a license to remove it.

## Zakończenie

You now know how to **initialize DocumentBuilder for new document**, insert an ActiveX command button, and save the result with Aspose.Words for Java. This pattern lets you generate interactive Word templates programmatically, which is especially handy for automated reporting or form‑driven workflows.

From here you can explore additional form controls (`Forms2OleControlType.CHECKBOX`, `COMBOBOX`, etc.), combine the button with custom VBA macros, or generate full‑featured documents that include tables, images, and styling—all using the same `DocumentBuilder` workflow.

---

*Gotowy do tworzenia bardziej złożonej automatyzacji Word? Sprawdź nasze przewodniki o **wstawianiu tabeli przy użyciu DocumentBuilder**, **stosowaniu stylów programowo** oraz **eksportowaniu do PDF przy użyciu Aspose.Words**.*

## What Should You Learn Next?

The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [Jak tworzyć pola formularzy i dodawać zawartość przy użyciu DocumentBuilder w Aspose.Words dla Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Jak zapisać dokument jako PDF przy użyciu Aspose.Words dla Java](/words/english/java/document-loading-and-saving/saving-documents-as-pdf/)
- [Dodaj znak wodny do dokumentu przy użyciu Aspose.Words dla Java](/words/english/java/document-conversion-and-export/using-watermarks-to-documents/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}