---
category: general
date: 2026-09-27
description: Vytvořte soubor docx obsahující ActiveX v Javě pomocí Aspose.Words. Naučte
  se krok za krokem vložit tlačítko příkazu ActiveX.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create docx containing activex
- insert activex command button
- Aspose.Words Java
- ActiveX control in Word
- generate Word document programmatically
language: cs
lastmod: 2026-09-27
og_description: Vytvořte soubor docx obsahující ActiveX v Javě pomocí Aspose.Words.
  Postupujte podle tohoto návodu, jak vložit příkazové tlačítko ActiveX a uložit dokument.
og_image_alt: Screenshot of a Word document that contains an ActiveX command button
og_title: Vytvořte docx obsahující ActiveX v Javě – kompletní průvodce
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
title: Jak vytvořit docx obsahující ActiveX pomocí Javy a Aspose.Words
url: /cs/java/using-document-elements/how-to-create-docx-containing-activex-with-java-and-aspose-w/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak vytvořit docx obsahující ActiveX pomocí Javy a Aspose.Words

Pokud potřebujete **vytvořit docx obsahující ActiveX**, tento průvodce vám ukáže kompletní řešení. Naučíte se, jak **vložit ActiveX tlačítko příkazu** do souboru Word pomocí Aspose.Words for Java a poté výsledek uložit jako .docx, který lze otevřít v Microsoft Word.

Programatické generování dokumentu Word vás ušetří ruční úpravy a zaručuje konzistenci napříč zprávami, smlouvami nebo šablonami formulářů. Níže uvedené kroky pokrývají vše od nastavení projektu až po řešení běžných úskalí, takže můžete tuto techniku začlenit do jakékoli Java aplikace.

## Požadavky

* Java Development Kit (JDK) 8 nebo novější nainstalovaný.
* Maven 3.6+ (nebo jiný build nástroj, který preferujete).
* Licenční soubor Aspose.Words for Java (bezplatná zkušební verze funguje pro testování).
* Microsoft Word nainstalovaný na cílovém počítači, pokud chcete vizuálně ověřit ActiveX ovládací prvek.

Tyto položky jsou vyžadovány, protože Aspose.Words poskytuje API, které vytváří dokument, zatímco Word je potřeba k vykreslení ActiveX ovládacího prvku.

## Krok 1: Nastavení Maven projektu

Create a new Maven project or add the Aspose.Words dependency to an existing `pom.xml`:

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

> **Tip:** Udržujte verzi Aspose.Words v souladu s oficiálními poznámkami k vydání, abyste získali opravy chyb a nové funkce ActiveX.

## Krok 2: Napsat Java kód, který vytváří dokument

Vytvořte třídu pojmenovanou `ActiveXDocxCreator`. Níže uvedený kód obsahuje všechny potřebné importy, metodu `main` a podrobné komentáře, které vysvětlují každou operaci.

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

### Proč je každý řádek důležitý

* `Document` je kontejner pro veškerý obsah Wordu. Vytvoření nové instance vám poskytne čisté plátno.
* `DocumentBuilder` poskytuje plynulé API pro vkládání prvků; automaticky sleduje vkládací bod.
* `insertForms2OleControl()` vytváří obecný zástupný OLE ovládací prvek. Aspose.Words jej považuje za ActiveX kontejner.
* `setControlType(Forms2OleControlType.COMMANDBUTTON)` říká Wordu, že zástupný prvek má být vykreslen jako CommandButton.
* `setCaption("Click Me")` definuje text zobrazený na tlačítku.
* `setLeft` a `setTop` umisťují tlačítko relativně k okrajům stránky. Přizpůsobte tyto hodnoty podle svého rozvržení.
* `setWidth` a `setHeight` jsou volitelné, ale zlepšují vzhled tlačítka, zejména když je výchozí velikost příliš malá.
* `doc.save` zapíše strukturu v paměti do fyzického .docx souboru, který může Word otevřít.

## Krok 3: Ověření vygenerovaného dokumentu

Open `output/ActiveXCommandButton.docx` in Microsoft Word:

1. Dokument by měl zobrazovat jedinou stránku s tlačítkem označeným **Click Me**, umístěným blízko levého horního rohu.
2. Pokud se tlačítko nezobrazí, zkontrolujte, že **ActiveX ovládací prvky jsou povoleny** v Trust Center Wordu (Soubor → Možnosti → Trust Center → Nastavení Trust Center → Nastavení ActiveX).
3. Tlačítko je funkční pouze ve Windows verzích Wordu, které podporují ActiveX. Na macOS nebo webové verzi Wordu bude ovládací prvek zobrazen jako statický obrázek.

## Krok 4: Řešení běžných okrajových případů

| Situace | Důvod | Doporučená akce |
|-----------|--------|--------------------|
| Tlačítko chybí po otevření souboru | Bezpečnostní nastavení Wordu blokují ActiveX | Povolte „Spouštět všechny ovládací prvky bez omezení“ pro důvěryhodná umístění. |
| Vygenerovaný .docx nelze otevřít | Nekompatibilní verze Aspose.Words | Aktualizujte na nejnovější verzi Aspose.Words; starší verze nemusí správně vložit požadované OLE části. |
| Potřebujete, aby tlačítko spouštělo makro | ActiveX samotné neobsahuje kód makra | Kombinujte ActiveX ovládací prvek s VBA makrem, které zpracovává událost `Click`. Použijte metodu `DocumentBuilder.insertOleObject` k vložení šablony s povoleným makrem. |
| Rozvržení je špatné při různých velikostech stránky | Souřadnice jsou absolutní body | Použijte `builder.getPageSetup().setPageWidth` a `setPageHeight` k standardizaci velikosti stránky před umístěním ovládacího prvku. |

## Krok 5: Rozšíření řešení

Můžete vložit jiné ActiveX ovládací prvky změnou výčtu `ControlType`:

```java
commandButton.setControlType(Forms2OleControlType.CHECKBOX); // inserts a checkbox
```

Aspose.Words také podporuje vkládání **ActiveX textových polí**, **listových polí** a **kombinovaných polí**. Stejné metody pro umístění (`setLeft`, `setTop`, `setWidth`, `setHeight`) platí.

Pokud potřebujete umístit více ovládacích prvků, opakovaně volejte `builder.insertForms2OleControl()` a podle toho upravte souřadnice každého ovládacího prvku.

## Kompletní zdrojový soubor

Níže je celý soubor `ActiveXDocxCreator.java` připravený ke zkopírování a vložení:

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

Spuštěním tohoto programu vytvoříte **docx obsahující ActiveX**, který můžete distribuovat koncovým uživatelům, kteří potřebují interaktivní formuláře.

## Závěr

Nyní víte, jak **vytvořit docx obsahující ActiveX** pomocí Javy a Aspose.Words a jak **programově vložit ActiveX tlačítko příkazu**. Tutoriál pokryl nastavení projektu, kompletní zdrojový kód, kroky ověření a strategie pro řešení typických problémů.

Odtud můžete zkoumat:

* Přidání VBA makrů pro reakci na kliknutí tlačítka.
* Vkládání dalších ActiveX ovládacích prvků, jako jsou zaškrtávací políčka nebo komboboxy.
* Automatizaci generování více‑stránkových formulářů s dynamickými daty.

Experimentujte s různými souřadnicemi, velikostmi a typy ovládacích prvků, aby vyhovovaly vašemu konkrétnímu rozvržení dokumentu. Šťastné programování!

## Co byste se měli naučit dál?

Následující tutoriály pokrývají úzce související témata, která staví na technikách předvedených v tomto průvodci. Každý zdroj obsahuje kompletní funkční příklady kódu s podrobnými vysvětleními, které vám pomohou zvládnout další funkce API a prozkoumat alternativní přístupy k implementaci ve vašich projektech.

- [Používání OLE objektů a ActiveX ovládacích prvků v Aspose.Words pro Java](/words/english/java/using-document-elements/using-ole-objects-and-activex/)
- [Jak vytvořit formulářová pole a přidat obsah pomocí DocumentBuilder v Aspose.Words pro Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Vytvoření obdélníkového tvaru ve Wordu s Aspose.Words – krok za krokem průvodce](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}