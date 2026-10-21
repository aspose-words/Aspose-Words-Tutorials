---
category: general
date: 2026-10-07
description: Vytvořte ActiveX příkazové tlačítko v Javě a programově přidejte příkazové
  tlačítko do dokumentů Word. Naučte se, jak nastavit levý horní pozici tlačítka.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create activex command button
- programmatically add command button
- how to set button left top
language: cs
lastmod: 2026-10-07
og_description: Vytvořte ActiveX příkazové tlačítko v Javě pro vložení interaktivních
  ovládacích prvků do vašich dokumentů Word. Naučte se, jak programově přidat příkazové
  tlačítko, nastavit jeho pozici a přizpůsobit jeho vzhled.
og_image_alt: Screenshot showing a created ActiveX command button in a Java‑generated
  Word document
og_title: Vytvořte tlačítko příkazu ActiveX v Javě – průvodce krok za krokem
schemas:
- author: Aspose
  dateModified: '2026-10-07'
  description: Create ActiveX command button in Java and programmatically add command
    button to Word docs. Learn how to set button left top positions.
  headline: How to create ActiveX command button in Java
  type: TechArticle
- description: Create ActiveX command button in Java and programmatically add command
    button to Word docs. Learn how to set button left top positions.
  name: How to create ActiveX command button in Java
  steps:
  - name: How to set button left top
    text: Positioning the button is where the secondary keyword **how to set button
      left top** becomes relevant. The `setLeft` and `setTop` methods accept values
      measured in points (1 point = 1/72 in).
  - name: Adding multiple buttons
    text: If you need several buttons, repeat **Step 2** and **Step 3** for each control.
      Remember to adjust `setLeft` and `setTop` so the buttons don’t overlap.
  - name: Changing button behavior
    text: 'ActiveX buttons can run VBA macros when clicked. To attach a macro, set
      the `setOnAction` property with the macro name:'
  - name: Compatibility notes
    text: '- The button works only in desktop versions of Word that support ActiveX
      (e.g., Word for Windows). It will appear as a static image in Word for Mac or
      online editors. - If you target a mixed environment, consider using a **content
      control** (`RichTextContentControl`) instead of an ActiveX control.'
  - name: Next steps
    text: '- Explore other ActiveX controls such as `Forms.TextBox.1` or `Forms.CheckBox.1`.
      - Combine multiple controls with a VBA module to implement full‑featured forms.
      - Replace ActiveX with content controls if you need cross‑platform compatibility.'
  type: HowTo
tags:
- ActiveX
- Java
- Aspose.Words
title: Jak vytvořit ActiveX příkazové tlačítko v Javě
url: /cs/java/using-document-elements/how-to-create-activex-command-button-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak vytvořit ActiveX tlačítko příkazu v Javě

Pokud potřebujete **vytvořit ActiveX tlačítko příkazu** v dokumentu Word pomocí Javy, tento návod vám přesně ukáže, jak na to. Uvidíte kompletní, spustitelný příklad, který **programově přidá tlačítko příkazu**, umístí jej pomocí `setLeft` a `setTop` a uloží výsledek jako soubor `.docx`.

Vložení interaktivního tlačítka vám umožní vytvářet formuláře, automatizovat pracovní postupy nebo sbírat vstupy uživatelů přímo v souboru Word. Níže uvedené kroky pokrývají vše od nastavení projektu až po finální ověření, takže můžete kód zkopírovat do svého projektu, aniž by vám něco uniklo.

## Požadavky

Před začátkem se ujistěte, že máte:

- JDK 17 nebo novější nainstalováno  
- Maven 3.8+ (nebo váš preferovaný nástroj pro sestavení)  
- Aspose.Words pro Java 23.9 nebo novější – knihovna, která poskytuje `DocumentBuilder` a podporu OLE ovládacích prvků  
- Základní znalost syntaxe Javy a objektově orientovaných konceptů  

Pokud používáte Maven, přidejte závislost do vašeho `pom.xml`:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
    <classifier>jdk17</classifier>
</dependency>
```

> **Tip:** Použijte nejnovější verzi Aspose.Words, abyste získali opravy chyb a nové OLE funkce.

## Krok 1: Vytvořte nový prázdný dokument a DocumentBuilder

Prvním krokem k **vytvoření ActiveX tlačítka příkazu** je vytvořit prázdný `Document` a `DocumentBuilder`. Builder vám poskytuje plynulé API pro vkládání obsahu, včetně OLE ovládacích prvků.

```java
import com.aspose.words.*;

public class ActiveXButtonDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new empty document and a DocumentBuilder to work with it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

`Document` představuje soubor Word v paměti, zatímco `DocumentBuilder` funguje jako kurzor, který vám umožní umístit prvky přesně tam, kde je potřebujete.

## Krok 2: Vložte OLE tlačítko příkazu

ActiveX ovládací prvky se vkládají jako OLE objekty. Aspose.Words poskytuje třídu `Forms2OleControl` pro tento účel.

```java
        // Step 2: Insert an OLE command button control into the document
        Forms2OleControl commandButton = builder.insertForms2OleControl();
```

Když zavoláte `insertForms2OleControl()`, Aspose automaticky vytvoří placeholder tvar, který bude hostit ActiveX tlačítko.

## Krok 3: Nakonfigurujte vlastnosti tlačítka

Nyní **programově přidáte podrobnosti tlačítka příkazu**, jako je jeho ProgID, popisek a velikost. Nejčastější ProgID pro tlačítko příkazu je `"Forms.CommandButton.1"`.

```java
        // Step 3: Configure the button's properties (type, position, size, caption)
        commandButton.setProgId("Forms.CommandButton.1"); // ActiveX class identifier
        commandButton.setCaption("Click Me");            // Text shown on the button
        commandButton.setWidth(80);                      // Width in points
        commandButton.setHeight(30);                     // Height in points
```

### Jak nastavit levý horní roh tlačítka

Umístění tlačítka je místo, kde se stává relevantním sekundární klíčové slovo **how to set button left top**. Metody `setLeft` a `setTop` přijímají hodnoty měřené v bodech (1 bod = 1/72 palce).

```java
        // Position the button 100 points from the left margin and 150 points from the top
        commandButton.setLeft(100);   // Horizontal offset
        commandButton.setTop(150);    // Vertical offset
```

Upravte tato čísla tak, aby odpovídala vašemu rozvržení. Například pro zarovnání tlačítka s buňkou tabulky vypočítejte souřadnice buňky a předáte je metodám `setLeft`/`setTop`.

## Krok 4: Uložte dokument

Nakonec zapište dokument na disk. Soubor bude obsahovat ActiveX tlačítko připravené k interakci po otevření v Microsoft Word.

```java
        // Step 4: Save the document containing the button
        doc.save("CommandButton.docx");
        System.out.println("Document saved successfully.");
    }
}
```

Spuštěním metody `main` se vytvoří `CommandButton.docx`. Otevřete soubor ve Wordu, povolte obsah, pokud budete vyzváni, a uvidíte klikatelné tlačítko s popiskem **Click Me**, umístěné na souřadnicích, které jste zadali.

![Vytvořit ActiveX tlačítko příkazu v Javě](/images/activex-button-screenshot.png){.center width=600 alt="Snímek obrazovky vytvoření ActiveX tlačítka příkazu v Javě, zobrazující tlačítko uvnitř dokumentu Word"}

## Běžné varianty a okrajové případy

### Přidání více tlačítek

Pokud potřebujete několik tlačítek, opakujte **Krok 2** a **Krok 3** pro každý ovládací prvek. Nezapomeňte upravit `setLeft` a `setTop`, aby se tlačítka nepřekrývala.

### Změna chování tlačítka

ActiveX tlačítka mohou spouštět VBA makra po kliknutí. Pro připojení makra nastavte vlastnost `setOnAction` na název makra:

```java
commandButton.setOnAction("MyMacro");
```

Ujistěte se, že cílový dokument obsahuje odpovídající VBA modul; jinak Word zobrazí chybu.

### Poznámky o kompatibilitě

- Tlačítko funguje pouze v desktopových verzích Wordu, které podporují ActiveX (např. Word pro Windows). V Wordu pro Mac nebo online editorech se zobrazí jako statický obrázek.  
- Pokud cílíte na smíšené prostředí, zvažte použití **content control** (`RichTextContentControl`) místo ActiveX ovládacího prvku.

## Kompletní zdrojový kód pro referenci

Níže je kompletní, samostatný příklad, který můžete zkopírovat do nového Maven projektu a okamžitě spustit.

```java
import com.aspose.words.*;

public class ActiveXButtonDemo {
    public static void main(String[] args) throws Exception {
        // Create a new empty document and a DocumentBuilder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert an OLE command button control
        Forms2OleControl commandButton = builder.insertForms2OleControl();

        // Configure the button
        commandButton.setProgId("Forms.CommandButton.1");
        commandButton.setCaption("Click Me");
        commandButton.setWidth(80);
        commandButton.setHeight(30);

        // How to set button left top – position the control
        commandButton.setLeft(100);   // Horizontal offset in points
        commandButton.setTop(150);    // Vertical offset in points

        // Save the resulting document
        doc.save("CommandButton.docx");
        System.out.println("Document saved successfully.");
    }
}
```

**Očekávaný výstup:** Po spuštění najdete `CommandButton.docx` v pracovním adresáři vašeho projektu. Otevřením souboru v Microsoft Word se zobrazí tlačítko na určeném místě s popiskem „Click Me“.

## Závěr

Nyní víte, jak **vytvořit ActiveX tlačítko příkazu** v Javě, **programově přidat tlačítko příkazu** do dokumentu Word a přesně ovládat jeho rozvržení pomocí metod **how to set button left top**. Tato technika otevírá dveře k bohatým, interaktivním formulářům ve Wordu, které mohou spouštět makra, spouštět externí aplikace nebo sbírat vstupy uživatelů přímo v dokumentu.

### Další kroky

- Prozkoumejte další ActiveX ovládací prvky, jako jsou `Forms.TextBox.1` nebo `Forms.CheckBox.1`.  
- Kombinujte více ovládacích prvků s VBA modulem pro implementaci plnohodnotných formulářů.  
- Nahraďte ActiveX content controly, pokud potřebujete multiplatformní kompatibilitu.  

Neváhejte experimentovat s velikostí, popiskem a umístěním, aby odpovídaly vašemu UI designu. Pokud narazíte na problémy, dvakrát zkontrolujte, že verze Aspose.Words, kterou používáte, podporuje OLE ovládací prvky, a ověřte, že nastavení zabezpečení Wordu umožňuje spouštění ActiveX. Šťastné programování!

## Co byste se měli naučit dál?

Následující tutoriály pokrývají úzce související témata, která staví na technikách předvedených v tomto návodu. Každý zdroj obsahuje kompletní funkční ukázky kódu s podrobnými vysvětleními, které vám pomohou zvládnout další funkce API a prozkoumat alternativní přístupy k implementaci ve vašich projektech.

- [Vkládání OLE objektů a ActiveX ovládacích prvků do dokumentů Word](/words/english/python-net/document-structure-and-content-manipulation/document-ole-objects-active-x/)
- [Jak vytvořit formulářová pole a přidat obsah pomocí DocumentBuilder v Aspose.Words pro Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Vytvoření obdélníkového tvaru ve Wordu pomocí Javy – Kompletní průvodce](/words/english/java/images-shapes/create-rectangle-shape-in-word-with-java-full-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}