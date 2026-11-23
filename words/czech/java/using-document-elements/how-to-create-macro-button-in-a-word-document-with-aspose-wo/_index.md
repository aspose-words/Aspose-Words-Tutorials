---
category: general
date: 2026-11-22
description: Vytvořte makro tlačítko ve Word dokumentu pomocí Javy. Naučte se vložit
  příkazové tlačítko, nastavit text tlačítka a propojit makro s tlačítkem pro interaktivní
  dokumenty.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create macro button
- insert command button
- set button text
- link macro to button
- add interactive button
language: cs
lastmod: 2026-11-22
og_description: Vytvořte makro tlačítko ve Word dokumentu pomocí Javy. Tento tutoriál
  ukazuje, jak vložit příkazové tlačítko, nastavit text tlačítka a propojit makro
  s tlačítkem pro plnou interaktivitu.
og_image_alt: Screenshot of a Word document showing a macro button created with Java
  code
og_title: Vytvořte tlačítko makra ve Word dokumentu pomocí Javy – krok za krokem průvodce
schemas:
- author: Aspose
  dateModified: '2026-11-22'
  description: Create macro button in a Word document using Java. Learn to insert
    command button, set button text, and link macro to button for interactive documents.
  headline: How to create macro button in a Word document with Aspose.Words for Java
  type: TechArticle
- description: Create macro button in a Word document using Java. Learn to insert
    command button, set button text, and link macro to button for interactive documents.
  name: How to create macro button in a Word document with Aspose.Words for Java
  steps:
  - name: Insert command button into the document
    text: '`DocumentBuilder.insertForms2OleControl` creates an OLE control of the
      specified type. The `Forms2OleControlType.COMMAND_BUTTON` constant tells Aspose.Words
      to generate a command button that can host a macro.'
  - name: Set button text (caption)
    text: The caption is the visible label on the button. Use `setCaption` to define
      what the user sees.
  - name: Link macro to button
    text: A macro is identified by its name, for example `MyMacro`. The `setOnClick`
      method stores this name in the button’s `OnClick` event handler.
  - name: Add interactive button to a Word document
    text: After configuring the OLE control, you may want to position it, resize it,
      or add surrounding text. The `DocumentBuilder` continues to operate on the document,
      so you can insert paragraphs before or after the button.
  - name: Expected output
    text: 'Running the program generates `MacroButtonDemo.docm`. Opening the file
      in Microsoft Word shows:'
  type: HowTo
tags:
- Aspose.Words
- Java
- OLE controls
- Automation
title: Jak vytvořit makro tlačítko v dokumentu Word pomocí Aspose.Words pro Javu
url: /cs/java/using-document-elements/how-to-create-macro-button-in-a-word-document-with-aspose-wo/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak vytvořit makro tlačítko v dokumentu Word pomocí Aspose.Words pro Java

Pokud potřebujete **vytvořit makro tlačítko** v souboru Word, tento průvodce vás provede přesně potřebnými kroky. Naučíte se, jak **vložit příkazové tlačítko**, **nastavit text tlačítka** a **propojit makro s tlačítkem**, aby se dokument stal plně interaktivním.

Vývojáři často vkládají OLE ovládací prvky pro spuštění VBA makr z dokumentu. Tento tutoriál pokrývá kompletní workflow, od nastavení projektu až po spustitelný Java příklad, který přidá **interaktivní tlačítko** do souboru .docx. Žádné externí skripty nejsou potřeba – vše běží uvnitř Java procesu.

## Požadavky

* Nainstalovaný JDK 17 nebo novější.
* Maven 3.8+ (nebo Gradle) pro správu závislostí.
* Aspose.Words for Java 23.9 nebo novější – knihovna poskytuje `DocumentBuilder` a OLE control API.
* Základní znalost Javy a VBA makr.

Pokud některá z těchto položek chybí, nejprve je nainstalujte; zbytek tutoriálu předpokládá, že jsou k dispozici.

## Jak vytvořit makro tlačítko pomocí Aspose.Words pro Java

Jádro řešení se skládá ze čtyř akcí:

1. **Vložit příkazové tlačítko** OLE ovládací prvek do dokumentu.
2. **Nastavit text tlačítka** (popisek), který uživatel vidí.
3. **Propojit makro s tlačítkem**, aby kliknutí spustilo požadovanou VBA rutinu.
4. **Uložit dokument** s vloženým makrem.

Každá akce je podrobně vysvětlena v následujících sekcích.

### Krok 1: Vložit příkazové tlačítko do dokumentu

```java
import com.aspose.words.*;

public class MacroButtonDemo {
    public static void main(String[] args) throws Exception {
        // Load a blank document or create a new one
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a command button OLE control
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMAND_BUTTON);
```

**Proč je to důležité:** OLE ovládací prvek funguje jako kontejner pro makro. Bez jeho vložení neexistuje žádný vizuální prvek, na který by uživatel mohl kliknout.

### Krok 2: Nastavit text tlačítka (popisek)

```java
        // Set the button's caption – this is the text displayed on the button
        commandButton.setCaption("Run Report");
```

**Proč je to důležité:** Jasný text tlačítka zlepšuje použitelnost. Metoda `setCaption` aktualizuje vlastnost `Caption` OLE ovládacího prvku, kterou Word vykresluje jako popisek tlačítka.

### Krok 3: Propojit makro s tlačítkem

```java
        // Assign a macro to run when the button is clicked
        commandButton.setOnClick("MyMacro");
```

**Proč je to důležité:** Propojení makra vytváří interaktivní chování. Když uživatel klikne na tlačítko ve Wordu, spustí se přiřazená VBA rutina.

### Krok 4: Přidat interaktivní tlačítko do dokumentu Word

Po nastavení OLE ovládacího prvku můžete chtít určit jeho pozici, změnit velikost nebo přidat okolní text. `DocumentBuilder` nadále pracuje s dokumentem, takže můžete vložit odstavce před nebo za tlačítko.

```java
        // Add a descriptive paragraph before the button
        builder.moveToDocumentStart();
        builder.writeln("Click the button below to generate the report:");

        // Move the cursor back to the button location (optional)
        builder.moveTo(commandButton.getNode());

        // Optionally, resize the button (width and height in points)
        commandButton.setWidth(120);
        commandButton.setHeight(30);

        // Save the document with the macro-enabled format
        doc.save("MacroButtonDemo.docm", SaveFormat.DOCM);
    }
}
```

**Proč je to důležité:** Uložení jako `.docm` zachová kód makra. Pokud uložíte jako `.docx`, odkaz na makro se ztratí.

## Kompletní spustitelný příklad

Níže je kompletní Java program, včetně importů, ošetření výjimek a komentářů, které vysvětlují každý krok. Zkopírujte kód do Maven projektu s Aspose.Words závislostí a spusťte jej.

```java
// Maven dependency (add to pom.xml):
// <dependency>
//   <groupId>com.aspose</groupId>
//   <artifactId>aspose-words</artifactId>
//   <version>23.9</version>
// </dependency>

import com.aspose.words.*;

public class MacroButtonDemo {
    public static void main(String[] args) throws Exception {
        // 1. Create a new empty document
        Document doc = new Document();

        // 2. Initialize DocumentBuilder to edit the document
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 3. Write an introductory paragraph
        builder.writeln("Press the button to execute the macro:");

        // 4. Insert the command button OLE control
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMAND_BUTTON);

        // 5. Set the visual caption of the button
        commandButton.setCaption("Run Report");

        // 6. Link the button to a VBA macro named MyMacro
        commandButton.setOnClick("MyMacro");

        // 7. Resize the button for better appearance
        commandButton.setWidth(120);   // points
        commandButton.setHeight(30);   // points

        // 8. Save the document as a macro‑enabled file
        doc.save("MacroButtonDemo.docm", SaveFormat.DOCM);
    }
}
```

### Očekávaný výstup

Spuštěním programu se vygeneruje `MacroButtonDemo.docm`. Otevřením souboru v Microsoft Wordu se zobrazí:

* Odstavec, který obsahuje text *„Stiskněte tlačítko pro spuštění makra:“*.
* Tlačítko s popiskem **Run Report** přímo pod odstavcem.
* Po kliknutí na tlačítko se Word pokusí spustit makro `MyMacro`. (Skutečný VBA kód musíte do dokumentu přidat ručně nebo pomocí jiného automatizačního kroku.)

Pokud makro neexistuje, Word zobrazí bezpečnostní varování, což je standardní chování pro dokumenty s povolenými makry.

## Běžné varianty a okrajové případy

| Scénář | Jak upravit kód |
|----------|-----------------------|
| **Jiný popisek tlačítka** | Změňte řetězec předávaný metodě `setCaption`. |
| **Více tlačítek** | Opakovaně zavolejte `insertForms2OleControl`, každé s vlastním `setCaption` a `setOnClick`. |
| **Vlastní názvy makr** | Nahraďte `"MyMacro"` libovolným platným názvem VBA procedury, např. `"ExportToExcel"`. |
| **Omezení velikosti tlačítka** | Upravte hodnoty `setWidth` a `setHeight`; Word respektuje zadané body. |
| **Vkládání makra programově** | Použijte `Document.getBuiltInDocumentProperties().add("Macros", …)` nebo samostatný krok injekce VBA; Aspose.Words sám VBA kód nezapisuje. |

**Tip:** Vždy testujte vygenerovaný `.docm` na počítači, kde je zabezpečení makr nastaveno na *Enable all macros* pro vývoj. V produkci podepište makro důvěryhodným certifikátem, aby se předešlo bezpečnostním výzvám.

## Kontrolní seznam řešení problémů

* **Tlačítko se nezobrazuje** – Ověřte, že dokument je uložen jako `.docm` a otevřen ve verzi Wordu, která podporuje OLE ovládací prvky.
* **Makro se nespouští** – Ujistěte se, že název makra přesně odpovídá, včetně velikosti písmen, a že makro existuje v VBA projektu dokumentu.
* **Popisek tlačítka je oříznutý** – Zvětšete šířku tlačítka pomocí `setWidth`, aby se vešel delší text.
* **Neočekávaný posun rozvržení** – Použijte `builder.moveTo` k přesnému umístění kurzoru před vložením ovládacího prvku.

## Závěr

Nyní víte, jak **vytvořit makro tlačítko** v dokumentu Word pomocí Javy, **vložit příkazové tlačítko**, **nastavit text tlačítka** a **propojit makro s tlačítkem** pro plnou interaktivitu. Kompletní příklad ukazuje všechny potřebné volání API, vysvětluje, proč je každý krok důležitý, a poskytuje návod pro běžné varianty.

Dále můžete zkoumat:

* **Přidat interaktivní tlačítko** do existujících šablon místo nového dokumentu.
* **Programově vložit VBA kód** pomocí Open XML SDK nebo sekundárního automatizačního nástroje.
* **Kombinovat více OLE ovládacích prvků** (zaškrtávací políčka, seznamy) pro vytvoření bohatých formulářů.

Experimentujte s různými popisky, názvy makr a velikostmi tlačítek, aby vyhovovaly vašemu konkrétnímu případu použití. Šťastné programování!

## Co byste se měli naučit dál?

Následující tutoriály pokrývají úzce související témata, která staví na technikách předvedených v tomto průvodci. Každý zdroj obsahuje kompletní funkční ukázky kódu s podrobnými vysvětleními, které vám pomohou zvládnout další funkce API a prozkoumat alternativní přístupy k implementaci ve vašich projektech.

- [Jak vložit příkazové tlačítko do dokumentu Word pomocí Javy](/words/english/java/using-document-elements/how-to-insert-command-button-in-a-word-document-using-java/)
- [Jak nastavit pozici tlačítka v dokumentu Word pomocí Javy](/words/english/java/using-document-elements/how-to-set-button-position-in-a-word-document-with-java/)
- [Jak vložit ActiveX tlačítko do Wordu – nastavit popisek tlačítka](/words/english/java/using-document-elements/how-to-insert-activex-button-in-word-set-button-caption/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}