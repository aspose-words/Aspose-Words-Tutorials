---
category: general
date: 2026-09-24
description: Nastavte pozici tlačítka ve Word dokumentu pomocí Javy a Aspose.Words.
  Naučte se, jak vložit tlačítko, přidat ActiveX ovládací prvek a vytvořit Word dokument
  ve stylu Javy.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- set button position
- how to insert button
- add activex control
- add button to word
- create word document java
language: cs
lastmod: 2026-09-24
og_description: Nastavte pozici tlačítka ve Word dokumentu pomocí Javy. Tento průvodce
  ukazuje, jak vložit tlačítko, přidat ActiveX ovládací prvek a vytvořit Word dokument
  v Javě s Aspose.Words.
og_image_alt: Screenshot of a Word document showing a CommandButton positioned at
  100 px left and 150 px top
og_title: Nastavení pozice tlačítka v dokumentu Word pomocí Javy – kompletní průvodce
schemas:
- author: Aspose
  dateModified: '2026-09-24'
  description: Set button position in a Word document using Java and Aspose.Words.
    Learn how to insert button, add ActiveX control, and create Word document Java
    style.
  headline: How to set button position in a Word document with Java
  type: TechArticle
- description: Set button position in a Word document using Java and Aspose.Words.
    Learn how to insert button, add ActiveX control, and create Word document Java
    style.
  name: How to set button position in a Word document with Java
  steps:
  - name: Expected output
    text: '* A `.docx` file named **CommandButtonDemo.docx**. * Inside the document,
      a **CommandButton** labeled “Click Me” appears 100 px from the left margin and
      150 px from the top margin. * The button responds to clicks when the document
      is opened in Word (it will display a default ActiveX message unless y'
  - name: Adding multiple buttons
    text: If you need to **add button to Word** more than once, repeat steps 3‑5 with
      a new `Forms2OleControl` instance each time. Remember to adjust the `setTop`
      value so buttons don’t overlap.
  - name: Working without a license
    text: 'Aspose.Words adds a watermark when used without a license. For production
      code, purchase a license and apply it at the start of `main`:'
  - name: Compatibility with older Office versions
    text: 'ActiveX controls are supported in the `.doc` (Word 97‑2003) format. To
      create a legacy file, change the save format:'
  - name: Next steps
    text: '* Explore other `Forms2OleControl.ControlType` values (e.g., `CHECKBOX`,
      `TEXTBOX`) to build richer forms. * Combine the button with VBA macros for custom
      click handling. * Use Aspose.Words’ mail‑merge feature to generate personalized
      documents that already contain interactive controls.'
  type: HowTo
- questions:
  - answer: Yes. Aspose.Words is pure Java and runs on any JDK 8+ implementation,
      including OpenJDK.
    question: Does this work with OpenJDK?
  - answer: ActiveX button appearance is controlled by the host application (Word).
      You can attach VBA code to modify properties at runtime, but the static appearance
      is limited to the default style.
    question: Can I change the button’s font or color?
  - answer: 'Move the `DocumentBuilder` cursor into the cell before calling `insertForms2OleControl`.
      The control will inherit the cell’s layout, and you can still use `setLeft`/`setTop`
      for fine‑tuning. ## Conclusion You now know how to **set button position** in
      a Word document using Java, how to **how to inse'
    question: What if I need to place the button inside a table cell?
  type: FAQPage
tags:
- Aspose.Words
- Java
- ActiveX
- Word automation
- CommandButton
title: Jak nastavit pozici tlačítka v dokumentu Word pomocí Javy
url: /cs/java/using-document-elements/how-to-set-button-position-in-a-word-document-with-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak nastavit pozici tlačítka ve Word dokumentu pomocí Javy

Pokud potřebujete **nastavit pozici tlačítka** uvnitř souboru Word, tento průvodce vám ukáže kompletní, spustitelné řešení. Ať už vytváříte šablonu, která vyžaduje interakci uživatele, nebo automatizujete formulář, přesně se naučíte **jak vložit tlačítko** pomocí Aspose.Words for Java a ovládat jeho umístění.

Tutoriál pokrývá vše, co potřebujete k **přidání ActiveX ovládacího prvku** do Word dokumentu, vysvětluje, jak **přidat tlačítko do Wordu**, a demonstruje celý proces **vytvoření Word dokumentu v Javě**. Nejsou vyžadovány žádné externí odkazy – stačí zkopírovat, spustit a ověřit výsledek.

## Požadavky

* Nainstalovaný Java 17 (nebo jakékoli prostředí Java 8+).
* Maven nebo Gradle pro správu závislostí.
* Licence Aspose.Words for Java (bezplatná zkušební verze funguje pro hodnocení).
* Základní znalost syntaxe Javy.

> **Tip:** Uchovávejte své Aspose.Words JAR soubory ve složce `libs/` a přidejte je do classpath vašeho projektu, abyste se vyhnuli konfliktům verzí.

## Krok 1: Nastavení Maven projektu

Vytvořte jednoduchý Maven projekt (nebo použijte Gradle) a přidejte závislost Aspose.Words:

```xml
<!-- pom.xml -->
<project>
    <modelVersion>4.0.0</modelVersion>
    <groupId>com.example</groupId>
    <artifactId>word-button-demo</artifactId>
    <version>1.0.0</version>
    <dependencies>
        <dependency>
            <groupId>com.aspose</groupId>
            <artifactId>aspose-words</artifactId>
            <version>24.9</version> <!-- latest at time of writing -->
        </dependency>
    </dependencies>
</project>
```

Spuštěním `mvn clean compile` se stáhne knihovna a připraví se cesta pro sestavení.

## Krok 2: Vytvoření nového Word dokumentu

Prvním krokem je **vytvořit Word dokument v Javě**. Vytvoříte objekt `Document` a `DocumentBuilder`, který vám umožní soubor upravovat.

```java
import com.aspose.words.*;

public class CommandButtonDemo {
    public static void main(String[] args) throws Exception {
        // Initialize a blank document
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

Třída `Document` představuje celý soubor .docx, zatímco `DocumentBuilder` poskytuje plynulé API pro vkládání obsahu.

## Krok 3: Jak vložit tlačítko – přidání ActiveX ovládacího prvku

Aspose.Words poskytuje třídu `Forms2OleControl` pro vkládání starších ActiveX ovládacích prvků, jako je CommandButton. Tento krok ukazuje přesný způsob, jak **vložit tlačítko** do dokumentu.

```java
        // Insert a CommandButton ActiveX control
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControl.ControlType.COMMANDBUTTON);
```

Metoda `insertForms2OleControl` vrací instanci `Forms2OleControl`, kterou můžete konfigurovat. Toto je jádro procesu **přidání ActiveX ovládacího prvku**.

## Krok 4: Nastavení pozice tlačítka

Nyní skutečně **nastavujeme pozici tlačítka**. Metody `setLeft` a `setTop` ovládacího prvku přijímají hodnoty v bodech (1 pt = 1/72 palce). Pro zarovnání tlačítka s typickými souřadnicemi obrazovky můžete převést pixely na body (1 px ≈ 0,75 pt). V příkladu umístíme tlačítko 100 px od levého okraje a 150 px od horního okraje.

```java
        // Position the button on the page
        commandButton.setLeft(100 * 0.75);   // 75 pt ≈ 100 px
        commandButton.setTop(150 * 0.75);    // 112.5 pt ≈ 150 px
```

Protože logika **nastavení pozice tlačítka** je zde zabalena, můžete tyto řádky znovu použít kdykoli potřebujete přesunout ovládací prvek. Upravit čísla podle požadavků na rozvržení.

## Krok 5: Definování velikosti a popisku

Tlačítko bez popisku je matoucí. Použijte `setWidth`, `setHeight` a `setCaption`, aby mělo viditelný vzhled.

```java
        // Define size and caption
        commandButton.setWidth(120 * 0.75);   // 90 pt width
        commandButton.setHeight(30 * 0.75);   // 22.5 pt height
        commandButton.setCaption("Click Me");
```

Velikost je také vyjádřena v bodech, takže pro konzistenci převádíme z pixelů.

## Krok 6: Uložení dokumentu – dokončení toku vytvoření Word dokumentu v Javě

Nakonec soubor uložte na disk. Cesta může být absolutní nebo relativní k kořeni projektu.

```java
        // Save the document containing the CommandButton
        doc.save("output/CommandButtonDemo.docx");
    }
}
```

Spuštěním programu se vytvoří `CommandButtonDemo.docx` ve složce `output`. Otevřením souboru v Microsoft Word se zobrazí klikatelné tlačítko umístěné přesně tam, kde jste jej nastavili.

### Očekávaný výstup

* Soubor `.docx` s názvem **CommandButtonDemo.docx**.
* V dokumentu se objeví **CommandButton** s popiskem „Click Me“ umístěný 100 px od levého okraje a 150 px od horního okraje.
* Tlačítko reaguje na kliknutí, když je dokument otevřen ve Wordu (zobrazí výchozí zprávu ActiveX, pokud nepřipojíte vlastní VBA kód).

## Krok 7: Běžné varianty a okrajové případy

### Přidání více tlačítek

Pokud potřebujete **přidat tlačítko do Wordu** více než jednou, opakujte kroky 3‑5 s novou instancí `Forms2OleControl` pokaždé. Nezapomeňte upravit hodnotu `setTop`, aby se tlačítka nepřekrývala.

```java
        Forms2OleControl secondButton = builder.insertForms2OleControl(
                Forms2OleControl.ControlType.COMMANDBUTTON);
        secondButton.setLeft(200 * 0.75);
        secondButton.setTop(250 * 0.75);
        secondButton.setWidth(120 * 0.75);
        secondButton.setHeight(30 * 0.75);
        secondButton.setCaption("Second");
```

### Práce bez licence

Aspose.Words přidá vodoznak, pokud je používán bez licence. Pro produkční kód zakupte licenci a aplikujte ji na začátku `main`:

```java
        License license = new License();
        license.setLicense("Aspose.Words.lic");
```

### Kompatibilita se staršími verzemi Office

ActiveX ovládací prvky jsou podporovány ve formátu `.doc` (Word 97‑2003). Pro vytvoření staršího souboru změňte formát ukládání:

```java
        doc.save("CommandButtonDemo.doc", SaveFormat.DOC);
```

## Kompletní zdrojový kód (spustitelný)

```java
import com.aspose.words.*;

public class CommandButtonDemo {
    public static void main(String[] args) throws Exception {
        // Optional: apply a license if you have one
        // License license = new License();
        // license.setLicense("Aspose.Words.lic");

        // Step 1: Create a new blank document and a DocumentBuilder to edit it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Insert a CommandButton ActiveX control (how to insert button)
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControl.ControlType.COMMANDBUTTON);

        // Step 3: Position the button on the page (set button position)
        commandButton.setLeft(100 * 0.75);   // distance from the left edge (points)
        commandButton.setTop(150 * 0.75);    // distance from the top edge (points)

        // Step 4: Define the button's size and caption
        commandButton.setWidth(120 * 0.75);   // width in points
        commandButton.setHeight(30 * 0.75);   // height in points
        commandButton.setCaption("Click Me");

        // Step 5: Save the document containing the CommandButton (create word document java)
        doc.save("output/CommandButtonDemo.docx");
    }
}
```

Uložte soubor jako `src/main/java/CommandButtonDemo.java`, spusťte `mvn exec:java -Dexec.mainClass=CommandButtonDemo` a otevřete vygenerovaný dokument, abyste viděli výsledek.

## Často kladené otázky

**Q: Funguje to s OpenJDK?**  
A: Ano. Aspose.Words je čistě Java a běží na jakékoli implementaci JDK 8+, včetně OpenJDK.

**Q: Můžu změnit font nebo barvu tlačítka?**  
A: Vzhled ActiveX tlačítka řídí hostitelská aplikace (Word). Můžete připojit VBA kód pro úpravu vlastností za běhu, ale statický vzhled je omezen na výchozí styl.

**Q: Co když potřebuji umístit tlačítko do buňky tabulky?**  
A: Přesuňte kurzor `DocumentBuilder` do buňky před voláním `insertForms2OleControl`. Ovládací prvek zdědí rozvržení buňky a stále můžete použít `setLeft`/`setTop` pro jemné doladění.

## Závěr

Nyní víte, jak **nastavit pozici tlačítka** ve Word dokumentu pomocí Javy, jak **vložit tlačítko**, jak **přidat ActiveX ovládací prvek** a jak **přidat tlačítko do Wordu**, přičemž dodržujete osvědčené postupy pro **vytvoření Word dokumentu v Javě** projekty. Kompletní příklad demonstruje celý pracovní postup – od nastavení projektu až po uložený soubor `.docx` obsahující funkční CommandButton.

### Další kroky

* Prozkoumejte další hodnoty `Forms2OleControl.ControlType` (např. `CHECKBOX`, `TEXTBOX`) pro tvorbu bohatších formulářů.
* Kombinujte tlačítko s VBA makry pro vlastní zpracování kliknutí.
* Využijte funkci hromadné korespondence Aspose.Words k vytvoření personalizovaných dokumentů, které již obsahují interaktivní ovládací prvky.

Šťastné programování a užívejte si automatizaci Word dokumentů pomocí Javy!

## Co byste se měli naučit dál?

Následující tutoriály pokrývají úzce související témata, která staví na technikách předvedených v tomto průvodci. Každý zdroj obsahuje kompletní funkční ukázky kódu s podrobnými vysvětleními, které vám pomohou zvládnout další funkce API a prozkoumat alternativní přístupy k implementaci ve vašich projektech.

- [Jak vytvořit formulářová pole a přidat obsah pomocí DocumentBuilder v Aspose.Words pro Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Přidání pole Combo Box do Word dokumentu pomocí Aspose.Words pro .NET](/words/english/net/add-content-using-documentbuilder/insert-combo-box/)
- [Jak načíst Word dokumenty pomocí Aspose.Words Java: komplexní průvodce](/words/english/java/document-operations/aspose-words-java-master-word-processing/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}