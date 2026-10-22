---
category: general
date: 2026-09-18
description: Vytvořte prázdný dokument v Javě a přidejte tlačítko ActiveX. Naučte
  se, jak vložit příkazové tlačítko, vytvořit interaktivní formulář a uložit dokument
  Word.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank document
- create interactive form
- add activex button
- how to insert command button
- create word document
language: cs
lastmod: 2026-09-18
og_description: Vytvořte prázdný dokument v Javě a vložte ActiveX příkazové tlačítko.
  Postupujte podle tohoto krok za krokem návodu, abyste vytvořili interaktivní formulář
  a uložili soubor Word.
og_image_alt: Screenshot of a Word document showing a clickable ActiveX command button
og_title: Vytvořit prázdný dokument s interaktivním příkazovým tlačítkem ve Wordu
schemas:
- author: Aspose
  dateModified: '2026-09-18'
  description: Create blank document in Java and add an ActiveX button. Learn how
    to insert command button, build an interactive form, and save a Word document.
  headline: Create blank document with an interactive command button in Word using
    Java
  type: TechArticle
- description: Create blank document in Java and add an ActiveX button. Learn how
    to insert command button, build an interactive form, and save a Word document.
  name: Create blank document with an interactive command button in Word using Java
  steps:
  - name: 'Load the existing document: `Document doc = new Document("ExistingForm.docx");`'
    text: 'Load the existing document: `Document doc = new Document("ExistingForm.docx");`'
  - name: 'Move the builder to the desired location: `builder.moveToParagraph(5, 0);
      // 6th paragraph, first node`'
    text: 'Move the builder to the desired location: `builder.moveToParagraph(5, 0);
      // 6th paragraph, first node`'
  - name: Insert the button as shown in Step 3.
    text: Insert the button as shown in Step 3.
  - name: Adjust the button’s `Top`/`Left` based on the paragraph’s layout.
    text: Adjust the button’s `Top`/`Left` based on the paragraph’s layout.
  type: HowTo
tags:
- Aspose.Words
- Java
- ActiveX
- Word automation
title: Vytvořte prázdný dokument s interaktivním tlačítkem příkazu ve Wordu pomocí
  Javy
url: /cs/java/document-manipulation/create-blank-document-with-an-interactive-command-button-in/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Vytvořte prázdný dokument s interaktivním tlačítkem příkazu ve Wordu pomocí Javy

Pokud potřebujete **vytvořit prázdný dokument**, který obsahuje klikatelné tlačítko, tento průvodce vám přesně ukáže, jak to provést pomocí Aspose.Words for Java. Naučíte se vytvořit interaktivní formulář, přidat tlačítko ActiveX a nakonec uložit soubor Word – vše během několika stručných kroků.

Vložení tlačítka příkazu promění statický .docx na funkční formulář, se kterým mohou koncoví uživatelé přímo v Microsoft Wordu interagovat. Tento tutoriál také pokrývá **jak vložit tlačítko příkazu**, řešení běžných úskalí a rozšíření řešení pro složitější formuláře.

## Předpoklady

* Java 17 nebo novější (kód se kompiluje s JDK 17+)
* Aspose.Words for Java 23.9 nebo novější – knihovna poskytuje `Document`, `DocumentBuilder` a `Forms2OleControl`.
* IDE nebo nástroj pro sestavení (Maven/Gradle), který dokáže přidat závislost Aspose.Words.
* Základní znalost syntaxe Javy a konceptů Word dokumentů.

```xml
<!-- Maven dependency -->
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
</dependency>
```

## Krok 1: Vytvořte prázdný dokument

Prvním krokem je vytvořit novou instanci objektu `Document`. Tento objekt představuje prázdný soubor Word připravený k vložení obsahu.

```java
// Step 1: Create a new blank document
Document doc = new Document();
```

Vytvoření prázdného dokumentu vám poskytne čisté plátno, což je nezbytné, když chcete **vytvořit Word dokument** programově bez jakékoli předchozí šablony.

## Krok 2: Inicializujte DocumentBuilder

`DocumentBuilder` je hlavní třída pro přidávání textu, tabulek a ovládacích prvků formuláře. Pracuje s `Document`, který jste právě vytvořili.

```java
// Step 2: Initialize a DocumentBuilder to construct the document content
DocumentBuilder builder = new DocumentBuilder(doc);
```

Builder udržuje aktuální vkládací bod, takže následné příkazy ovlivní správné místo v souboru.

## Krok 3: Vložte ovládací prvek tlačítka příkazu Forms2Ole

Aspose.Words poskytuje třídu `Forms2OleControl` pro ActiveX ovládací prvky. Pro **přidání ActiveX tlačítka** požádáte builder o typ `COMMANDBUTTON`.

```java
// Step 3: Insert a Forms2Ole command button control
Forms2OleControl commandButton = builder.insertForms2OleControl(OleControlType.COMMANDBUTTON);
```

Metoda `insertForms2OleControl` vloží ovládací prvek na aktuální pozici kurzoru builderu. Protože se jedná o objekt ActiveX, funguje pouze v desktopové verzi Microsoft Word, ne ve Word Online.

## Krok 4: Nakonfigurujte vzhled a umístění tlačítka

Můžete nastavit popisek, velikost a umístění tlačítka pomocí setterů ovládacího prvku. Hodnoty polohy jsou měřeny v bodech (1 bod = 1/72 palce).

```java
// Step 4: Configure the button's appearance and position
commandButton.setCaption("Click Me");   // Text shown on the button
commandButton.setTop(100);              // Distance from the top edge of the page (points)
commandButton.setLeft(100);             // Distance from the left edge of the page (points)
commandButton.setWidth(120);            // Optional: set button width
commandButton.setHeight(30);            // Optional: set button height
```

*Proč konfigurovat tyto vlastnosti?* Nastavením `Top` a `Left` zajistíte, že se tlačítko objeví na očekávaném místě na stránce, zatímco `Caption` definuje popisek viditelný uživateli. Pokud vynecháte šířku/výšku, Word přiřadí výchozí rozměry, které nemusí odpovídat vašemu návrhu.

### Tip
Pokud plánujete přidat více ovládacích prvků, zavolejte `builder.moveToDocumentEnd()` před každým vložením, abyste předešli překrývání objektů.

## Krok 5: Uložte dokument s vloženým tlačítkem příkazu

Nakonec zapište dokument na disk. Přípona souboru musí být `.docx` (nebo `.doc` pro starší verze Wordu), aby byl zachován ActiveX ovládací prvek.

```java
// Step 5: Save the document with the embedded command button
String outputPath = "C:/temp/CommandButton.docx";
doc.save(outputPath);
System.out.println("Document saved to: " + outputPath);
```

Když otevřete `CommandButton.docx` v Microsoft Wordu, uvidíte tlačítko s popiskem **Click Me**. Kliknutím spustíte výchozí akci ActiveX (která ve výchozím nastavení nic nedělá). Později můžete připojit makro nebo VBA skript, který definuje vlastní chování.

## Jak vložit tlačítko příkazu do existujícího formuláře (volitelné)

Pokud již máte formulář s textovými poli a chcete **vytvořit interaktivní formulář**, který zahrnuje tlačítko, postupujte podle těchto doplňujících kroků:

1. Načtěte existující dokument: `Document doc = new Document("ExistingForm.docx");`
2. Přesuňte builder na požadované místo: `builder.moveToParagraph(5, 0); // 6. odstavec, první uzel`
3. Vložte tlačítko podle kroku 3.
4. Upravte `Top`/`Left` tlačítka podle rozvržení odstavce.

Tento přístup vám umožní obohatit libovolnou předem vytvořenou šablonu Wordu o ActiveX tlačítko, aniž byste museli znovu vytvářet celý soubor.

## Okrajové případy a řešení problémů

| Situace | Co zkontrolovat | Doporučené řešení |
|-----------|---------------|-----------------|
| Tlačítko se ve Wordu nezobrazuje | Ujistěte se, že soubor otevřete v desktopové verzi Wordu (Word Online odstraňuje ActiveX). | Otevřete soubor v desktopové verzi Word 2016+ |
| Popisek je oříznutý | Zkontrolujte, že šířka tlačítka je dostatečná pro text. | Zvyšte `setWidth`, dokud popisek nebude pasovat |
| Ukládání vyvolá `IOException` | Ověřte, že výstupní adresář existuje a máte oprávnění k zápisu. | Vytvořte adresář nebo spusťte program s vyššími právy |
| Více tlačítek se překrývá | Kurzor builderu se po předchozím vložení možná nepřesunul. | Zavolejte `builder.moveToDocumentEnd()` před vložením každého nového ovládacího prvku |

## Kompletní spustitelný příklad

Níže je kompletní, samostatný Java program, který můžete zkopírovat, zkompilovat a spustit. Ukazuje **vytvoření prázdného dokumentu**, **přidání ActiveX tlačítka** a **uložení Word dokumentu** v jednom postupu.

```java
import com.aspose.words.*;

public class CommandButtonDemo {
    public static void main(String[] args) {
        try {
            // 1. Create a new blank document
            Document doc = new Document();

            // 2. Initialize DocumentBuilder
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 3. Insert an ActiveX command button
            Forms2OleControl commandButton = builder.insertForms2OleControl(OleControlType.COMMANDBUTTON);

            // 4. Configure button properties
            commandButton.setCaption("Click Me");
            commandButton.setTop(100);   // points from top
            commandButton.setLeft(100);  // points from left
            commandButton.setWidth(120);
            commandButton.setHeight(30);

            // 5. Save the document
            String outPath = "CommandButton.docx";
            doc.save(outPath);
            System.out.println("Document created: " + outPath);
        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}
```

**Očekávaný výstup**

```
Document created: CommandButton.docx
```

Otevření `CommandButton.docx` zobrazí jedinou stránku s tlačítkem označeným **Click Me**, umístěným 100 pt od horního a levého okraje.

## Závěr

Nyní víte, jak **vytvořit prázdný dokument**, vložit **ActiveX tlačítko** a proměnit obyčejný Word soubor na **interaktivní formulář**. Ovládnutím **jak vložit tlačítko příkazu** můžete tento vzor rozšířit o zaškrtávací políčka, rozbalovací seznamy nebo dokonce vlastní logiku řízenou VBA.

Dále zvažte prozkoumání těchto souvisejících témat:

* **Vytvořit interaktivní formulář** s textovými poli (`builder.insertField`)  
* **Přidat ActiveX tlačítko**, které spouští VBA makro (`builder.insertOleObject`)  
* **Vytvořit Word dokument** ze šablony pomocí `Document(docTemplatePath)`  
* Převod výsledného .docx na PDF při zachování tlačítka (poznámka: PDF zobrazí tlačítko jako statický obrázek).

Neváhejte experimentovat s velikostí, umístěním a popiskem tlačítka, aby odpovídaly vašemu UI designu. Šťastné programování!

## Co byste se měli naučit dál?

Následující tutoriály pokrývají úzce související témata, která staví na technikách předvedených v tomto průvodci. Každý zdroj obsahuje kompletní funkční ukázky kódu s podrobnými vysvětleními, které vám pomohou zvládnout další funkce API a prozkoumat alternativní přístupy k implementaci ve vašich projektech.

- [Jak vytvořit formulářová pole a přidat obsah pomocí DocumentBuilder v Aspose.Words pro Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Vytvořit VBA projekt ve Word dokumentu](/words/english/net/working-with-vba-macros/create-vba-project/)
- [Vytvořit nový Word dokument](/words/english/net/add-content-using-documentbuilder/create-new-document/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}