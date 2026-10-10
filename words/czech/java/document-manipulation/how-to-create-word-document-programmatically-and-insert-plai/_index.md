---
category: general
date: 2026-10-10
description: Vytvořte programově dokument Word pomocí Aspose.Words a vložte ovládací
  prvek prostého textu – krok za krokem průvodce pro vývojáře .NET.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document programmatically
- insert plain text content control
language: cs
lastmod: 2026-10-10
og_description: Programově vytvořte dokument Word pomocí Aspose.Words a přidejte ovládací
  prvek prostého textu, který zobrazuje zástupný text, což umožňuje dynamická formulářová
  pole v souborech .docx.
og_image_alt: Screenshot of a Word document displaying a plain text content control
  placeholder
og_title: Vytvořte Word dokument programově a přidejte ovládací prvek prostého textu
schemas:
- author: Aspose
  dateModified: '2026-10-10'
  description: Create word document programmatically with Aspose.Words and insert
    plain text content control – a step‑by‑step guide for .NET developers.
  headline: How to create word document programmatically and insert plain text content
    control
  type: TechArticle
tags:
- word
- document automation
- content control
- Aspose.Words
- C#
title: Jak programově vytvořit dokument Word a vložit ovládací prvek prostého textu
url: /cs/java/document-manipulation/how-to-create-word-document-programmatically-and-insert-plai/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak programově vytvořit dokument Word a vložit ovládací prvek prostého textu

Pokud potřebujete **programově vytvořit dokument Word**, tento průvodce vám přesně ukáže, jak to provést pomocí Aspose.Words pro .NET. V několika řádcích kódu se také naučíte **vložit ovládací prvek prostého textu** (také nazývaný Structured Document Tag), aby dokument mohl fungovat jako vyplnitelný formulář.

Provedete kompletní workflow—od inicializace nového objektu `Document` až po uložení finálního souboru .docx. Žádné externí nástroje nejsou potřeba a příklad funguje s .NET 6, .NET 7 nebo jakýmkoli aktuálním .NET runtime.

## Požadavky

* Platná licence Aspose.Words pro .NET (nebo použijte režim bezplatného hodnocení).  
* .NET 6+ SDK nainstalováno.  
* IDE, například Visual Studio 2022, Rider nebo VS Code.  

Pokud jste ještě nenainstalovali NuGet balíček Aspose.Words, spusťte:

```bash
dotnet add package Aspose.Words
```

## Krok 1: Programově vytvořit dokument Word

Prvním krokem je vytvořit prázdný objekt `Document` a `DocumentBuilder`. Builder vám poskytuje pohodlné API pro přidávání obsahu, stránek a Structured Document Tags (SDT).

```csharp
using Aspose.Words;
using Aspose.Words.BuildingBlocks;
using Aspose.Words.Markup;

// Create an empty document and a builder attached to it
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

**Proč je to důležité** – `Document` představuje celý soubor .docx v paměti. Vytvořením programově se vyhnete režii otevírání šablonového souboru, což je užitečné pro generování zpráv, faktur nebo jakéhokoli dokumentu za běhu.

## Krok 2: Vložit ovládací prvek prostého textu

**Ovládací prvek prostého textu** (SDT) umožňuje uživatelům zadávat text do předdefinované oblasti. Také podporuje zástupný text, který se zobrazí, když je ovládací prvek prázdný.

```csharp
// Insert a plain‑text Structured Document Tag (SDT) with an identifier "MyTag"
StructuredDocumentTag plainTextTag = builder.InsertStructuredDocumentTag(
    StructuredDocumentTagType.PlainText, "MyTag");

// Set placeholder text that shows inside the control when it is empty
plainTextTag.PlaceholderName = "Enter name";
```

**Vysvětlení** – `InsertStructuredDocumentTag` vytvoří SDT na aktuální pozici kurzoru `DocumentBuilder`. Hodnota výčtu `StructuredDocumentTagType.PlainText` říká Aspose.Words, aby vykreslil pole prostého textu místo rozbalovacího seznamu nebo výběru data. Vlastnost `PlaceholderName` poskytuje vizuální nápovědu uživateli, podobně jako šedý nápovědní text, který vidíte v moderních formulářích Wordu.

### Běžné varianty

| Varianta | Jak dosáhnout |
|-----------|-------------------|
| **Ovládací prvek bohatého textu** | Použijte `StructuredDocumentTagType.RichText` místo `PlainText`. |
| **Opakující se sekce** | Použijte `StructuredDocumentTagType.Group` a vnořte do něj další značky. |
| **Vlastní mapování XML** | Zavolejte `plainTextTag.SetXmlMapping(xmlPart, xpath, false)` po vytvoření `XmlPart`. |

## Krok 3: Přidat další obsah dokumentu (volitelné)

Můžete přidat běžné odstavce, tabulky nebo obrázky před nebo po ovládacím prvku. Zde je rychlý příklad, který přidá nadpis a odstavec:

```csharp
// Add a heading above the content control
builder.Font.Size = 16;
builder.Font.Bold = true;
builder.Writeln("Employee Information");

// Move the cursor back to the placeholder location (already set by InsertStructuredDocumentTag)
builder.Font.Size = 12;
builder.Font.Bold = false;
builder.Writeln(); // Adds a line break after the control
```

**Tip** – Kurzoru builderu se automaticky přesune na konec vloženého SDT, takže všechny následující volání `Writeln` se objeví za ovládacím prvkem.

## Krok 4: Uložit dokument obsahující ovládací prvek

Nakonec zapište dokument na disk. Můžete zvolit libovolný podporovaný formát (`.docx`, `.pdf`, `.html` atd.). Pro tento tutoriál ukládáme jako soubor Word.

```csharp
// Save the document to the specified path
string outputPath = Path.Combine(Environment.CurrentDirectory, "SdtExample.docx");
doc.Save(outputPath);
Console.WriteLine($"Document saved to: {outputPath}");
```

### Očekávaný výstup

Když otevřete *SdtExample.docx* v Microsoft Word, uvidíte:

1. Nadpis **Employee Information**.  
2. Ovládací prvek prostého textu se šedým zástupným textem **Enter name**.  

Pokud kliknete do ovládacího prvku, zástupný text zmizí a můžete zadat libovolný text. Identifikátor značky ovládacího prvku (`MyTag`) lze později programově získat pro extrakci dat nebo validaci.

## Kompletní, spustitelný příklad

Níže je samostatná konzolová aplikace, která spojuje všechny kroky. Zkopírujte kód do nového .NET konzolového projektu a spusťte jej.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Markup;

namespace WordContentControlDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Create an empty document and a DocumentBuilder
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 2️⃣ Insert a plain‑text content control (SDT) with a tag identifier
            StructuredDocumentTag sdt = builder.InsertStructuredDocumentTag(
                StructuredDocumentTagType.PlainText, "MyTag");

            // 3️⃣ Set placeholder text that appears when the control is empty
            sdt.PlaceholderName = "Enter name";

            // Optional: add a heading above the control
            builder.MoveToDocumentStart(); // Ensure heading appears before the control
            builder.Font.Size = 16;
            builder.Font.Bold = true;
            builder.Writeln("Employee Information");

            // Move back to the end of the control to continue writing
            builder.MoveToDocumentEnd();
            builder.Font.Size = 12;
            builder.Font.Bold = false;
            builder.Writeln(); // Adds a line break after the control

            // 4️⃣ Save the document
            string outputPath = Path.Combine(Environment.CurrentDirectory, "SdtExample.docx");
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to: {outputPath}");
        }
    }
}
```

Spuštěním programu se vypíše úplná cesta k vygenerovanému souboru. Otevřete soubor ve Wordu a ověřte, že **ovládací prvek prostého textu** se zobrazí se svým zástupným textem.

## Řešení problémů a okrajové případy

| Problém | Příčina | Řešení |
|-------|-------|-----|
| Zástupný text se nezobrazuje | Ovládací prvek je již vyplněn textem nebo je dokument otevřen v režimu, který skryje zástupné texty. | Ujistěte se, že je SDT prázdný před uložením, nebo nastavte `sdt.IsShowingPlaceholder = true` (k dispozici v novějších verzích Aspose.Words). |
| Ovládací prvek zmizí po uložení jako PDF | Export do PDF ve výchozím nastavení neuchovává interaktivní formulářová pole. | Použijte `PdfSaveOptions` s `SaveFormat.Pdf` a nastavte `ExportDocumentStructure = true`. |
| Identifikátor značky nebyl nalezen při pozdějším zpracování | Název značky byl překlep nebo přepsán. | Ověřte, že identifikátor předaný do `InsertStructuredDocumentTag` odpovídá názvu, který později dotazujete (`MyTag`). |

## Nejlepší postupy pro programové vytváření dokumentů Word

* **Znovu použijte jediný `DocumentBuilder`** na dokument, abyste se vyhnuli zbytečným alokacím paměti.  
* **Nastavte písma a styly před zápisem textu**; změna po přidání obsahu může způsobit nekonzistentní formátování.  
* **Uvolněte velké objekty** (např. `MemoryStream`, pokud dokument streamujete) pomocí `using` bloků.  
* **Ověřte dokument** pomocí `doc.UpdateFields()` a `doc.UpdatePageLayout()` před uložením, zejména když přidáváte tabulky nebo obrázky.  

## Závěr

Nyní víte, jak **programově vytvořit dokument Word** a **vložit ovládací prvek prostého textu** pomocí Aspose.Words pro .NET. Kompletní příklad ukazuje inicializaci dokumentu, vložení SDT se zástupným textem, volitelný další obsah a uložení do souboru .docx.

Zde můžete:

* Nahradit ovládací prvek prostého textu **bohatým textem** nebo **výběrem data**.  
* Naplnit dokument daty z databáze a později získat zadané hodnoty pomocí `StructuredDocumentTag.GetText()`.  
* Exportovat stejný dokument do PDF, HTML nebo OpenXML formátů při zachování formulářových polí.

Experimentujte s různými typy značek a prozkoumejte API Aspose.Words k vytvoření sofistikovaných, vyplnitelných šablon Word, které se hladce integrují do vašich .NET aplikací. Šťastné programování!

## Co byste se měli naučit dál?

Následující tutoriály pokrývají úzce související témata, která staví na technikách předvedených v tomto průvodci. Každý zdroj obsahuje kompletní funkční ukázky kódu s podrobnými vysvětleními, které vám pomohou zvládnout další funkce API a prozkoumat alternativní přístupy k implementaci ve vašich projektech.

- [Přidat rozbalovací seznam (Combo Box) jako formulářové pole do dokumentu Word s Aspose.Words pro .NET](/words/english/net/add-content-using-documentbuilder/insert-combo-box/)
- [Vložit textové vstupní formulářové pole do dokumentu Word](/words/english/net/add-content-using-documentbuilder/insert-text-input-form-field/)
- [Přidat zaškrtávací políčko jako formulářové pole do dokumentu Word s Aspose.Words pro .NET](/words/english/net/add-content-using-documentbuilder/insert-check-box/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}