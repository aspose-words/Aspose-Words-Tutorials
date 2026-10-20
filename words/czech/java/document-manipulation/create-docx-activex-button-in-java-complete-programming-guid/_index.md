---
category: general
date: 2026-08-14
description: Vytvořte ActiveX tlačítko v souboru docx v Javě pomocí Aspose.Words.
  Naučte se, jak programově přidat tlačítko formuláře do Wordu a uložit dokument.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create docx ActiveX button
- add form button word
language: cs
lastmod: 2026-08-14
og_description: Vytvořte ActiveX tlačítko v souboru DOCX v Javě pomocí Aspose.Words.
  Tento průvodce vám ukáže, jak přidat tlačítko formuláře ve Wordu, nakonfigurovat
  jej a uložit soubor.
og_image_alt: Screenshot of a Word document containing an ActiveX CommandButton created
  with Java
og_title: Vytvořte ActiveX tlačítko pro docx v Javě – krok za krokem tutoriál
schemas:
- author: Aspose
  dateModified: '2026-08-14'
  description: Create docx ActiveX button in Java with Aspose.Words. Learn how to
    add a form button in Word programmatically and save the document.
  headline: Create docx ActiveX button in Java – complete programming guide
  type: TechArticle
- description: Create docx ActiveX button in Java with Aspose.Words. Learn how to
    add a form button in Word programmatically and save the document.
  name: Create docx ActiveX button in Java – complete programming guide
  steps:
  - name: Set up the project and import Aspose.Words
    text: 'Add the Aspose.Words dependency to your `pom.xml` if you use Maven:'
  - name: Create a new blank document
    text: Instantiate a `Document` object, which represents an empty Word file ready
      to receive content.
  - name: Initialize a DocumentBuilder
    text: '`DocumentBuilder` provides a fluent interface for inserting text, images,
      and controls. Attach it to the document you just created.'
  - name: Insert an ActiveX CommandButton control
    text: Use the `insertForms2OleControl` method to embed an ActiveX `CommandButton`.
      This method returns a `Forms2OleControl` instance that you can further configure.
  - name: Configure the button’s properties
    text: Set the control’s name, caption, and layout attributes. These values determine
      how the button appears in Word and how you can reference it later via VBA or
      automation scripts.
  - name: Save the document
    text: Finally, write the document to disk. Use the `.docx` extension to keep the
      file in the modern Office Open XML format.
  type: HowTo
tags:
- ActiveX
- Java
- Aspose.Words
- Word automation
title: Vytvořte ActiveX tlačítko v docx v Javě – kompletní programovací průvodce
url: /cs/java/document-manipulation/create-docx-activex-button-in-java-complete-programming-guid/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Vytvoření ActiveX tlačítka v docx v Javě – kompletní programovací průvodce

Pokud potřebujete **vytvořit ActiveX tlačítko v docx** v Javě, tento průvodce vás provede celým procesem. Uvidíte, jak přidat formulářové tlačítko ve Wordu, nakonfigurovat jeho vlastnosti a vytvořit připravený .docx soubor.

Práce s ActiveX ovládacími prvky je běžnou požadavkem při automatizaci starších Word formulářů. V tomto tutoriálu se naučíte **přidávat formulářová tlačítka do Word** dokumentů pomocí knihovny Aspose.Words pro Java, takže můžete vložit interaktivní ovládací prvky bez ruční úpravy.

## Co budete potřebovat

* Java 17 nebo novější (kód se kompiluje i s dřívějšími verzemi, ale doporučujeme Java 17).
* Aspose.Words pro Java 23.10 nebo novější – stáhněte JAR z webu Aspose nebo přidejte Maven závislost.
* IDE (IntelliJ IDEA, Eclipse nebo VS Code) nebo jednoduchý textový editor a nástroje pro sestavování z příkazové řádky.
* Základní znalost syntaxe Javy a objektově orientovaného programování.

## Jak vytvořit ActiveX tlačítko v docx pomocí Aspose.Words

Následující kroky ukazují přesné pořadí potřebné k **vytvoření ActiveX tlačítka v docx** objektů a jejich vložení do Word dokumentu.

### Krok 1: Nastavení projektu a import Aspose.Words

Přidejte závislost Aspose.Words do souboru `pom.xml`, pokud používáte Maven:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.10</version>
    <classifier>jdk17</classifier>
</dependency>
```

Nebo, pokud dáváte přednost Gradlu:

```gradle
implementation 'com.aspose:aspose-words:23.10:jdk17'
```

Po vyřešení závislosti importujte požadované třídy ve vašem Java zdrojovém souboru:

```java
import com.aspose.words.Document;
import com.aspose.words.DocumentBuilder;
import com.aspose.words.forms.Forms2OleControl;
import com.aspose.words.forms.Forms2OleControlType;
```

Tyto importy vám poskytují přístup k `Document`, `DocumentBuilder` a API `Forms2OleControl`, které se používá k vložení ActiveX ovládacích prvků.

### Krok 2: Vytvoření nového prázdného dokumentu

Vytvořte instanci objektu `Document`, který představuje prázdný Word soubor připravený přijímat obsah.

```java
// Step 2: Create a new blank document
Document document = new Document();
```

Vytvoření dokumentu jako první zajišťuje, že následný builder pracuje na čistém plátně.

### Krok 3: Inicializace DocumentBuilderu

`DocumentBuilder` poskytuje plynulé rozhraní pro vkládání textu, obrázků a ovládacích prvků. Připojte jej k dokumentu, který jste právě vytvořili.

```java
// Step 3: Initialize a DocumentBuilder to construct the document content
DocumentBuilder builder = new DocumentBuilder(document);
```

Builder sleduje aktuální pozici kurzoru v dokumentu, takže další vložení proběhne přesně tam, kde potřebujete.

### Krok 4: Vložení ActiveX CommandButton ovládacího prvku

Použijte metodu `insertForms2OleControl` k vložení ActiveX `CommandButton`. Tato metoda vrací instanci `Forms2OleControl`, kterou můžete dále konfigurovat.

```java
// Step 4: Insert an ActiveX CommandButton control into the document
Forms2OleControl commandButton = builder.insertForms2OleControl(
        Forms2OleControlType.COMMAND_BUTTON);
```

V tomto okamžiku .docx soubor obsahuje zástupný znak pro tlačítko, ale zatím nemá žádný vizuální popisek ani velikost.

### Krok 5: Konfigurace vlastností tlačítka

Nastavte název ovládacího prvku, popisek a atributy rozvržení. Tyto hodnoty určují, jak tlačítko vypadá ve Wordu a jak na něj můžete později odkazovat pomocí VBA nebo automatizačních skriptů.

```java
// Step 5: Configure the button's properties (name, caption, size, and position)
commandButton.setName("btnSubmit");          // internal name used by VBA
commandButton.setCaption("Submit");          // text shown on the button
commandButton.setTop(100);                  // distance from the top of the page (points)
commandButton.setLeft(150);                 // distance from the left margin (points)
commandButton.setWidth(80);                 // button width (points)
commandButton.setHeight(30);                // button height (points)
```

> **Tip:** Word měří pozice v bodech (1 pt ≈ 1/72 in). Upravit `setTop` a `setLeft` pro zarovnání tlačítka s okolním obsahem.

### Krok 6: Uložení dokumentu

Nakonec zapište dokument na disk. Použijte příponu `.docx`, aby soubor zůstal v moderním formátu Office Open XML.

```java
// Step 6: Save the document containing the ActiveX button
String outputPath = "C:/temp/ActiveXButton.docx";
document.save(outputPath);
System.out.println("Document saved to " + outputPath);
```

Když otevřete výsledný soubor v Microsoft Word, uvidíte **Submit** tlačítko umístěné na souřadnicích, které jste zadali. Kliknutí na tlačítko ve Wordu nespustí žádnou akci, pokud nepřipojíte VBA kód, ale ovládací prvek je plně funkční pro workflow založené na formulářích.

## Časté otázky a okrajové případy

| Otázka | Odpověď |
|----------|--------|
| **Potřebuji speciální verzi Wordu?** | ActiveX ovládací prvky jsou podporovány v desktopové verzi Microsoft Word na Windows. V Wordu pro Mac ani ve Word Online nejsou k dispozici. |
| **Mohu to použít s `.doc` soubory?** | Ano. Uložte dokument s příponou `.doc` (`document.save("ActiveXButton.doc")`). Stejné API funguje i pro starší binární formát. |
| **Co když se tlačítko nezobrazí?** | Ujistěte se, že **File → Options → Trust Center → Trust Center Settings → ActiveX Settings** povoluje ActiveX ovládací prvky. Také ověřte, že dokument není otevřen v režimu „Protected View“. |
| **Mohu přidat další ActiveX ovládací prvky?** | Určitě. Nahraďte `Forms2OleControlType.COMMAND_BUTTON` za `Forms2OleControlType.CHECK_BOX`, `RADIO_BUTTON` atd. |
| **Existuje limit velikosti?** | Velikost ovládacího prvku je omezena jen rozvržením stránky. Velmi velké rozměry mohou způsobit přetečení rozvržení. |

## Kompletní, spustitelný příklad

Níže je kompletní Java třída, kterou můžete zkopírovat, zkompilovat a spustit. Obsahuje všechny importy, metodu main a vložené komentáře pro přehlednost.

```java
package com.example.wordactive;

import com.aspose.words.Document;
import com.aspose.words.DocumentBuilder;
import com.aspose.words.forms.Forms2OleControl;
import com.aspose.words.forms.Forms2OleControlType;

public class ActiveXButtonDemo {
    public static void main(String[] args) {
        try {
            // Create a new blank document
            Document document = new Document();

            // Initialize DocumentBuilder
            DocumentBuilder builder = new DocumentBuilder(document);

            // Insert an ActiveX CommandButton control
            Forms2OleControl commandButton = builder.insertForms2OleControl(
                    Forms2OleControlType.COMMAND_BUTTON);

            // Configure button properties
            commandButton.setName("btnSubmit");
            commandButton.setCaption("Submit");
            commandButton.setTop(100);   // points from top
            commandButton.setLeft(150);  // points from left
            commandButton.setWidth(80);  // width in points
            commandButton.setHeight(30); // height in points

            // Save the document
            String outputPath = "ActiveXButton.docx";
            document.save(outputPath);
            System.out.println("Document saved successfully to " + outputPath);
        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}
```

**Očekávaný výsledek:** Po spuštění programu se v pracovním adresáři objeví `ActiveXButton.docx`. Otevřením v Microsoft Word se zobrazí klikatelné **Submit** tlačítko umístěné blízko levého horního rohu první stránky.

## Závěr

Nyní víte, jak **vytvořit ActiveX tlačítko v docx** objekty v Javě pomocí Aspose.Words, a viděli jste, jak **přidávat formulářová tlačítka do Word** dokumentů programově. Kroky – nastavení projektu, vytvoření dokumentu, vložení ovládacího prvku, konfigurace jeho vlastností a uložení – pokrývají celý pracovní postup od začátku až do konce.

Dále můžete zkoumat:

* Přidání VBA maker, která reagují na kliknutí tlačítka.
* Vkládání dalších ActiveX ovládacích prvků, jako jsou zaškrtávací políčka nebo seznamové boxy.
* Automatizaci generování více‑stránkových formulářů s několika interaktivními prvky.

Neváhejte experimentovat s velikostmi, pozicemi a popisky, aby odpovídaly vašim konkrétním požadavkům na návrh formuláře. Šťastné programování!

## Co byste se měli naučit dál?

Následující tutoriály pokrývají úzce související témata, která staví na technikách předvedených v tomto průvodci. Každý zdroj obsahuje kompletní funkční ukázky kódu s podrobnými vysvětleními, které vám pomohou zvládnout další funkce API a prozkoumat alternativní přístupy k implementaci ve vašich projektech.

- [Jak vytvořit formulářová pole a přidat obsah pomocí DocumentBuilder v Aspose.Words pro Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Jak načíst HTML a uložit jako DOCX pomocí Aspose.Words pro Java](/words/english/java/document-loading-and-saving/loading-and-saving-html-documents/)
- [Jak vytvořit PDF dokumenty s Aspose.Words pro Java | Document Processing API](/words/english/java/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}