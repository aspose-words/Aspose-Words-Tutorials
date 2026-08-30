---
category: general
date: 2026-08-07
description: Tutoriál Aspose.Words ActiveX ukazuje, jak pomocí Javy přidat ovládací
  prvek CommandButton do dokumentu Word. Naučte se kompletní kód, konfiguraci a kroky
  ukládání.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- aspose words activex tutorial
- aspose.words java
- activeX control java
- documentbuilder insert control
- forms2olecontrol usage
language: cs
lastmod: 2026-08-07
og_description: Tutoriál Aspose.Words ActiveX vysvětluje, jak vložit ovládací prvek
  CommandButton ActiveX do dokumentu Word pomocí Javy. Postupujte podle kompletního
  příkladu, abyste vytvořili, nakonfigurovali a uložili dokument.
og_image_alt: Screenshot of a Word document with a CommandButton added via Aspose.Words
  ActiveX tutorial
og_title: Tutoriál Aspose.Words ActiveX – krok za krokem pro Javu
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: Aspose.Words ActiveX tutorial shows how to add a CommandButton control
    to a Word document using Java. Learn the full code, configuration, and saving
    steps.
  headline: Aspose.Words ActiveX tutorial – insert a CommandButton with Java
  type: TechArticle
- description: Aspose.Words ActiveX tutorial shows how to add a CommandButton control
    to a Word document using Java. Learn the full code, configuration, and saving
    steps.
  name: Aspose.Words ActiveX tutorial – insert a CommandButton with Java
  steps:
  - name: Initialize a `Document` and `DocumentBuilder`.
    text: Initialize a `Document` and `DocumentBuilder`.
  - name: Insert a `Forms2OleControl` of type `COMMAND_BUTTON`.
    text: Insert a `Forms2OleControl` of type `COMMAND_BUTTON`.
  - name: Set the button’s name, caption, size, and position.
    text: Set the button’s name, caption, size, and position.
  - name: Save the document as a .docx file that contains the ActiveX control.
    text: Save the document as a .docx file that contains the ActiveX control.
  type: HowTo
tags:
- Aspose.Words
- Java
- ActiveX
title: Tutoriál Aspose.Words ActiveX – vložení CommandButtonu pomocí Javy
url: /cs/java/images-shapes/aspose-words-activex-tutorial-insert-a-commandbutton-with-ja/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words ActiveX tutoriál – vložení CommandButton pomocí Javy

Pokud potřebujete vložit ActiveX ovládací prvek do souboru Word, tento **Aspose.Words ActiveX tutoriál** vás provede celým procesem. Uvidíte, jak vytvořit prázdný dokument, vložit CommandButton, nastavit jeho vlastnosti a uložit výsledek – vše pomocí čistého Java kódu.

Příklad používá Aspose.Words for Java API, které eliminuje potřebu Microsoft Office na serveru pro sestavování. Na konci tohoto průvodce budete schopni generovat soubory .docx, které obsahují plně funkční ovládací prvky CommandButton připravené k použití ve Windows prostředí.

## Požadavky

- Java Development Kit (JDK) 8 nebo novější nainstalovaný.
- Maven nebo jiný nástroj pro sestavování pro správu závislostí.
- Licence Aspose.Words for Java (nebo dočasný evaluační klíč) k odstranění evaluačních vodoznaků.
- Základní znalost syntaxe Javy a objektově orientovaného programování.

> **Tip:** Přidejte závislost Aspose.Words Maven do souboru `pom.xml`, aby IDE automaticky řešilo třídy:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.10</version> <!-- Use the latest version -->
</dependency>
```

## Krok 1: Vytvořte nový prázdný dokument a `DocumentBuilder`

`Document` třída představuje soubor Word v paměti, zatímco `DocumentBuilder` poskytuje plynulé API pro úpravu dokumentu. Inicializace obou objektů připraví dokument na další úpravy.

```java
import com.aspose.words.*;

public class ActiveXDemo {
    public static void main(String[] args) throws Exception {
        // Create an empty Word document
        Document document = new Document();

        // DocumentBuilder lets you add text, tables, and controls
        DocumentBuilder builder = new DocumentBuilder(document);
```

**Proč je to důležité:**  
`DocumentBuilder` sleduje aktuální pozici kurzoru, takže jakákoli následná operace vložení – například přidání ovládacího prvku – se objeví přesně tam, kde zamýšlíte.

## Krok 2: Vložte ActiveX ovládací prvek CommandButton

Aspose.Words poskytuje `Forms2OleControl` pro ActiveX objekty. Metoda `insertForms2OleControl` vyžaduje typ ovládacího prvku, který určujete pomocí výčtu `Forms2OleControlType`.

```java
        // Insert a CommandButton ActiveX control at the current cursor location
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMAND_BUTTON);
```

**Vysvětlení:**  
Vložený ovládací prvek je objekt založený na COM, který Word vykreslí jako klikací tlačítko, když je dokument otevřen ve Windows prostředí.

## Krok 3: Nakonfigurujte vlastnosti tlačítka

Po vložení můžete upravit název tlačítka, popisek, velikost a pozici. Tyto vlastnosti ovlivňují, jak ovládací prvek vypadá a chová se uvnitř Wordu.

```java
        // Set the logical name used by VBA or external scripts
        commandButton.setName("cmdSubmit");

        // Text displayed on the button face
        commandButton.setCaption("Submit");

        // Position the button 100 points from the left margin and 150 points from the top
        commandButton.setLeft(100);
        commandButton.setTop(150);

        // Define the button’s dimensions (width × height) in points
        commandButton.setWidth(80);
        commandButton.setHeight(30);
```

**Proč jsou tato nastavení důležitá:**  

- **Name** – Umožňuje VBA makrům odkazovat na ovládací prvek (`ActiveDocument.Forms("cmdSubmit")`).
- **Caption** – Určuje viditelný popisek, na který uživatelé klikají.
- **Left / Top** – Řídí umístění vzhledem k okrajům stránky.
- **Width / Height** – Zajišťuje konzistentní vizuální velikost napříč různými rozlišeními obrazovky.

## Krok 4: Uložte dokument

Volání `save` zapíše reprezentaci v paměti do fyzického souboru. Můžete zvolit libovolný podporovaný formát (`.docx`, `.doc`, `.pdf`, atd.). Pro tento tutoriál zachováme nativní Word formát.

```java
        // Persist the document with the embedded ActiveX control
        document.save("output/ActiveXDemo.docx");
    }
}
```

**Výsledek:**  
Otevření `ActiveXDemo.docx` v Microsoft Word zobrazí CommandButton označený **Submit** umístěný na zadaných souřadnicích. Kliknutí na tlačítko spustí výchozí chování (žádný VBA kód není připojen ve výchozím nastavení).

## Kompletní zdrojový kód

Sestavením všech částí dohromady vypadá kompletní spustitelný program takto:

```java
import com.aspose.words.*;
import com.aspose.words.forms.*;

public class ActiveXDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document and a DocumentBuilder
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Step 2: Insert a CommandButton ActiveX control
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMAND_BUTTON);

        // Step 3: Configure the button's properties
        commandButton.setName("cmdSubmit");
        commandButton.setCaption("Submit");
        commandButton.setLeft(100);
        commandButton.setTop(150);
        commandButton.setWidth(80);
        commandButton.setHeight(30);

        // Step 4: Save the document with the ActiveX control
        document.save("output/ActiveXDemo.docx");
    }
}
```

### Očekávaný výstup

- Soubor pojmenovaný **ActiveXDemo.docx** umístěný ve složce `output`.
- Po otevření v Microsoft Word (Windows) dokument zobrazí klikací tlačítko **Submit** na definované pozici.
- Tlačítko lze vybrat, přesunout nebo propojit s VBA kódem přes uživatelské rozhraní Wordu (Developer → Properties).

## Řešení běžných variant

| Scenario | Adjustment |
|----------|------------|
| **Uložit jako .doc** (starší formát) | `document.save("ActiveXDemo.doc", SaveFormat.DOC);` |
| **Přidat obslužnou rutinu události** | Word neexponuje události ActiveX prostřednictvím Aspose.Words. Musíte přidat VBA kód ručně po vygenerování dokumentu. |
| **Více ovládacích prvků** | Opakujte blok vložení/konfigurace s různými hodnotami `setName` a `setCaption`. |
| **Jiný typ ovládacího prvku (např. CheckBox)** | Použijte `Forms2OleControlType.CHECKBOX` ve volání `insertForms2OleControl`. |
| **Platformy mimo Windows** | ActiveX ovládací prvky se vykreslují pouze ve Wordu pro Windows. Pro multiplatformní řešení zvažte obsahové ovládací prvky (`StructuredDocumentTag`). |

## Nejlepší postupy a úskalí

- **License early** – Zaregistrujte svou licenci Aspose.Words před vytvořením objektu `Document`, aby se předešlo výzvám k evaluaci.
- **Coordinate system** – Pozice jsou měřeny v bodech (1 pt = 1/72 palce). Převádějte z pixelů nebo centimetrů, pokud váš UI design používá tyto jednotky.
- **File paths** – Používejte absolutní cesty nebo Java `Paths` API, aby nedošlo k `FileNotFoundException`, když výstupní adresář neexistuje.
- **Thread safety** – `Document` a `DocumentBuilder` nejsou thread‑safe. Vytvářejte samostatné instance pro každý vlákno, pokud generujete dokumenty paralelně.
- **Testing** – Ověřte vygenerovaný dokument na cílové verzi Wordu (např. Word 2016, Word 365), protože starší verze mohou zobrazovat ActiveX ovládací prvky odlišně.

## Závěr

Tento **Aspose.Words ActiveX tutoriál** ukazuje, jak programově přidat ovládací prvek CommandButton do dokumentu Word pomocí Javy. Naučili jste se:

1. Inicializovat `Document` a `DocumentBuilder`.
2. Vložit `Forms2OleControl` typu `COMMAND_BUTTON`.
3. Nastavit název, popisek, velikost a pozici tlačítka.
4. Uložit dokument jako soubor .docx, který obsahuje ActiveX ovládací prvek.

Odtud můžete zkoumat další typy ovládacích prvků, automatizovat injekci VBA maker nebo kombinovat ActiveX ovládací prvky s dalšími funkcemi Aspose.Words, jako je hromadná korespondence a obsahové ovládací prvky. Experimentujte s různými rozvrženími a integrujte vygenerované dokumenty do vašeho většího Java‑založeného reportingového pipeline.

---

## Co byste se měli naučit dál?

Následující tutoriály pokrývají úzce související témata, která navazují na techniky předvedené v tomto průvodci. Každý zdroj obsahuje kompletní funkční ukázky kódu s podrobnými vysvětleními, které vám pomohou zvládnout další funkce API a prozkoumat alternativní přístupy k implementaci ve vašich projektech.

- [Používání OLE objektů a ActiveX ovládacích prvků v Aspose.Words pro Java](/words/english/java/using-document-elements/using-ole-objects-and-activex/)
- [Jak vytvořit formulářová pole a přidat obsah pomocí DocumentBuilder v Aspose.Words pro Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Převod Wordu na RTF s tutoriálem Aspose.Words pro Java](/words/english/java/document-loading-and-saving/saving-documents-as-rtf-format/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}