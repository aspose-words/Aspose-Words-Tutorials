---
category: general
date: 2026-09-05
description: Naučte se, jak vytvořit skupinový tvar v docx, vložit ActiveX příkazové
  tlačítko a načíst Markdown do dokumentu Word s kompletním příkladem v C#.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create group shape docx
- insert activex command button
- load markdown into word document
language: cs
lastmod: 2026-09-05
og_description: Vytvořte skupinový tvar v souboru docx, vložte ActiveX tlačítko příkazu
  a načtěte Markdown do dokumentu Word pomocí C#. Postupujte podle tohoto návodu krok
  za krokem.
og_image_alt: Screenshot of a Word document showing a grouped shape and an ActiveX
  button
og_title: Vytvořte skupinový tvar v docx a vložte ActiveX ovládací prvky – průvodce
  C#
schemas:
- author: Aspose
  dateModified: '2026-09-05'
  description: Learn how to create group shape docx, insert ActiveX command button,
    and load Markdown into a Word document with a complete C# example.
  headline: How to create group shape docx and add interactive controls in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Document automation
title: Jak vytvořit skupinový tvar v docx a přidat interaktivní ovládací prvky v C#
url: /cs/java/images-shapes/how-to-create-group-shape-docx-and-add-interactive-controls/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak vytvořit skupinový tvar docx a přidat interaktivní ovládací prvky v C#

Pokud potřebujete programově **create group shape docx** soubory, tento průvodce vám přesně ukáže, jak na to. Také uvidíte, jak **insert ActiveX command button** ovládací prvky a **load Markdown into a Word document** bez ztráty podtržení. Na konci tutoriálu budete mít plně funkční `.docx`, který kombinuje vektorovou grafiku, interaktivní UI prvky a obsah založený na markdownu.

Tento tutoriál předpokládá, že máte základní vývojové prostředí C# a nainstalovanou knihovnu Aspose.Words pro .NET. Žádné externí nástroje nejsou potřeba – vše běží uvnitř standardní .NET konzole nebo desktopové aplikace.

## Požadavky

- .NET 6.0 SDK nebo novější (kód také funguje s .NET Framework 4.7+)
- Aspose.Words pro .NET (NuGet balíček `Aspose.Words`)
- Platný X.509 certifikát (`.pfx`), pokud chcete otestovat krok podepisování
- Soubor obrázku (např. `logo.png`) a markdown soubor (`sample.md`) umístěné ve známé složce

> **Tip:** Uchovávejte všechny vstupní soubory v jediné složce *resources*, aby byly relativní cesty jednodušší.

## Krok 1: Nastavte projekt a importujte jmenné prostory

Vytvořte nový konzolový projekt a přidejte požadované `using` direktivy. Tento blok také ukazuje, jak odkazovat na třídy Aspose.Words, které použijete později.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Loading;
using Aspose.Words.Saving;
using Aspose.Words.Saving.XpsSaveOptions; // only needed for signing example
using Aspose.Words.Saving.Signature;

// Ensure the license is applied if you have one
// Aspose.Words.License license = new Aspose.Words.License();
// license.SetLicense("Aspose.Words.lic");
```

`using` příkazy vám poskytují přímý přístup k `Document`, `DocumentBuilder`, `GroupShape`, `Forms2OleControl` a dalším typům používaným v celém tutoriálu.

## Krok 2: **Create group shape docx** – přidejte seskupený tvar s podřízenými elementy

*Group shape* vám umožňuje zacházet s více kreslenými objekty jako s jednou jednotkou. To je užitečné pro přesouvání nebo změnu velikosti související grafiky najednou.

```csharp
// Initialize a new empty document
Document document = new Document();
DocumentBuilder builder = new DocumentBuilder(document);

// Insert a group shape container
GroupShape group = builder.InsertGroupShape();

// Add a rectangle (100 × 50 points) as the first child
Shape rect = builder.InsertShape(ShapeType.Rectangle, 100, 50);
group.AppendChild(rect);

// Add an ellipse (80 × 40 points) as the second child
Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 80, 40);
group.AppendChild(ellipse);

// Optional: set a fill color for visual distinction
rect.FillColor = System.Drawing.Color.LightBlue;
ellipse.FillColor = System.Drawing.Color.LightCoral;

// Save the intermediate document so you can inspect the group
document.Save("Output/GroupShape.docx");
```

**Proč group shape?**  
Seskupení udržuje obdélník a elipsu zarovnané, když je uživatel v aplikaci Word přetahuje. Také zjednodušuje pozdější operace, jako je aplikace společného okraje nebo programatické přesunutí celé grafiky.

## Krok 3: Vložte plain‑text content control (placeholder pro vstup uživatele)

Content control poskytuje koncovým uživatelům strukturovanou oblast pro zadání textu. Placeholder text zmizí, jakmile uživatel začne psát.

```csharp
// Insert a plain‑text StructuredDocumentTag (SDT) after the group shape
StructuredDocumentTag sdt = builder.InsertStructuredDocumentTag(
    SdtType.PlainText, "MyTag");

// Set a friendly placeholder that appears in the UI
sdt.PlaceholderName = "Enter text here";

// Optionally, lock the content control to prevent deletion
sdt.LockContents = false;
sdt.LockContentControl = false;
```

Vlastnost `PlaceholderName` je to, co Word zobrazuje jako světle šedou nápovědu. Uživatelé ji mohou nahradit svým vlastním textem a podkladové XML zůstane dobře formátované.

## Krok 4: **Insert ActiveX command button** – přidejte interaktivní UI do dokumentu

ActiveX ovládací prvky jsou stále podporovány v moderních Word souborech a mohou spouštět makra nebo externí automatizaci. Níže přidáme *command button* a nastavíme jeho popisek.

```csharp
// Insert an ActiveX Forms2OleControl at the current cursor position
Forms2OleControl commandBtn = builder.InsertForms2OleControl();

// Define the control type as a command button
commandBtn.ControlType = Forms2OleControl.ControlType.CommandButton;

// Set the visible caption
commandBtn.Caption = "Click Me";

// Position the button relative to the page (optional)
commandBtn.Left = 150;   // points from the left margin
commandBtn.Top = 300;    // points from the top margin
```

**Kdy použít ActiveX tlačítko?**  
Pokud distribuujete dokument v korporátním prostředí, které spoléhá na VBA makra, ActiveX tlačítko může spustit makro nebo externí aplikaci. Pro čistě HTML‑založenou interaktivitu zvažte místo toho použití *content controls* s *Office.js*.

## Krok 5: Vložte skrytý obrázek (např. logo) pro branding nebo pozdější přístup skriptem

Skryté tvary nejsou zobrazeny v tištěném dokumentu, ale zůstávají v XML, což vám umožní je později programaticky načíst.

```csharp
// Insert an image from disk
Shape logo = builder.InsertImage("Resources/logo.png");

// Hide the image from the view/layout
logo.Hidden = true;

// You can still reference the image via its ShapeId if needed
string logoId = logo.Name;
```

## Krok 6: **Load markdown into a Word document** při zachování podtržení

Aspose.Words může importovat Markdown přímo. Povolení `ImportUnderlineFormatting` zajišťuje, že markdown podtržení (`<u>` nebo `__text__`) se převede na Word podtržení místo obyčejného textu.

```csharp
// Configure markdown load options
MarkdownLoadOptions mdOptions = new MarkdownLoadOptions
{
    ImportUnderlineFormatting = true
};

// Load the markdown file into a new Document instance
Document markdownDoc = new Document("Resources/sample.md", mdOptions);

// Append the markdown content to the main document after the previous elements
builder.MoveToDocumentEnd();
builder.InsertDocument(markdownDoc, ImportFormatMode.KeepSourceFormatting);
```

**Speciální případ:** Pokud markdown soubor obsahuje tabulky, jsou automaticky převedeny na Word tabulky. Pokud potřebujete vlastní stylování tabulek, použijte `DocumentBuilder` po vložení.

## Krok 7: Podepište dokument pomocí XAdES‑EPES (volitelný bezpečnostní krok)

Digitální podpisy garantují integritu dokumentu. Následující kód podepisuje soubor **create group shape docx** pomocí profilu XAdES‑EPES.

```csharp
// Initialize the signature object for the current document
Signature signature = new Signature(document);

// Choose the XAdES‑EPES level
signature.XmlDsigLevel = XmlDsigLevel.XAdES_EPES;

// Sign using a .pfx certificate (replace path and password)
signature.Sign("Resources/cert.pfx", "password");

// Save the signed document
document.Save("Output/SignedGroupShape.docx");
```

> **Bezpečnostní poznámka:** Uchovávejte heslo certifikátu mimo zdrojový kód. V produkci používejte proměnné prostředí nebo zabezpečený trezor.

## Kompletní spustitelný příklad

Spojením všech kroků dohromady získáte jeden samostatný program. Uložte soubor jako `Program.cs` a spusťte jej z příkazové řádky.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Loading;
using Aspose.Words.Saving.Signature;

class Program
{
    static void Main()
    {
        // 1️⃣ Create the document and group shape
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
        GroupShape group = builder.InsertGroupShape();
        group.AppendChild(builder.InsertShape(ShapeType.Rectangle, 100, 50));
        group.AppendChild(builder.InsertShape(ShapeType.Ellipse, 80, 40));

        // 2️⃣ Add a plain‑text content control
        StructuredDocumentTag sdt = builder.InsertStructuredDocumentTag(
            SdtType.PlainText, "MyTag");
        sdt.PlaceholderName = "Enter text here";

        // 3️⃣ Insert an ActiveX command button
        Forms2OleControl btn = builder.InsertForms2OleControl();
        btn.ControlType = Forms2OleControl.ControlType.CommandButton;
        btn.Caption = "Click Me";

        // 4️⃣ Insert a hidden logo image
        Shape logo = builder.InsertImage("Resources/logo.png");
        logo.Hidden = true;

        // 5️⃣ Load markdown while keeping underline formatting
        MarkdownLoadOptions mdOpts = new MarkdownLoadOptions
        {
            ImportUnderlineFormatting = true
        };
        Document mdDoc = new Document("Resources/sample.md", mdOpts);
        builder.MoveToDocumentEnd();
        builder.InsertDocument(mdDoc, ImportFormatMode.KeepSourceFormatting);

        // 6️⃣ Sign the document (optional)
        Signature sig = new Signature(doc);
        sig.XmlDsigLevel = XmlDsigLevel.XAdES_EPES;
        sig.Sign("Resources/cert.pfx", "password");

        // Save the final file
        doc.Save("Output/CompleteGroupShape.docx");
        Console.WriteLine("Document created successfully.");
    }
}
```

Spuštěním programu se vygeneruje `CompleteGroupShape.docx`, který obsahuje:

- Seskupený obdélník + elipsu (jádro **create group shape docx**)
- Plain‑text content control s placeholder textem
- **insert ActiveX command button** označené „Click Me“
- Skrytý obrázek loga
- Markdown obsah se zachovaným podtržením
- Digitální podpis XAdES‑EPES (pokud je certifikát poskytnut)

## Časté otázky a řešení problémů

| Otázka | Odpověď |
|---|---|
| **Bude ActiveX tlačítko fungovat v macOS Word?** | macOS Word nepodporuje ActiveX ovládací prvky. Tlačítko se zobrazí jako statický obrázek. Pro multiplatformní interaktivitu použijte content controls s Office.js. |
| **Co když markdown soubor obsahuje vlastní CSS?** | Aspose.Words ignoruje CSS; zpracovává se pouze standardní markdown syntaxe. Po importu převádějte elementy stylované pomocí CSS ručně na Word styly. |
| **Mohu později přidat další tvary do stejné skupiny?** | Ano. Získejte `GroupShape` podle jeho názvu nebo indexu a poté zavolejte `AppendChild(newShape)`. Nezapomeňte po úpravách dokument znovu uložit. |
| **Jak změním algoritmus podpisu?** | Nastavte `signature.SignatureAlgorithm` před voláním `Sign`. Výchozí je SHA‑256, který splňuje většinu požadavků na shodu. |
| **Je skrytý obrázek viditelný v uživatelském rozhraní Wordu?** | Ne, ale lze jej zobrazit zapnutím *Show hidden text* v nastavení Wordu. To je užitečné pro uložení metadat bez znečištění rozvržení. |

## Další kroky

Nyní, když můžete **create group shape docx**, **insert ActiveX command button** a **load markdown into a Word document**, můžete zkoumat:

- **Embedding VBA macros**, které reagují na kliknutí ActiveX tlačítka.
- **Applying custom styles** na odstavce vygenerované z markdownu.
- **Generating PDFs** ze stejného dokumentu pomocí `doc.Save("output.pdf", SaveFormat.Pdf)`.
- **Automating batch processing** více markdown souborů do jednoho sestaveného reportu.

Tyto rozšíření vám umožní vytvořit plně automatizované dokumentové pipeline, které kombinují bohatou grafiku, interaktivní ovládací prvky a autorství založené na markdownu – vše z C#.

---

*Šťastné programování! Pokud jste tento tutoriál našli

## Co byste se měli naučit dál?

Následující tutoriály pokrývají úzce související témata, která staví na technikách předvedených v tomto průvodci. Každý zdroj obsahuje kompletní funkční ukázky kódu s podrobnými vysvětleními, které vám pomohou zvládnout další funkce API a prozkoumat alternativní přístupy k implementaci ve vašich projektech.

- [Vytvořit Group Shape v dokumentu Word pomocí Aspose.Words pro .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Vytvořit obdélníkový tvar ve Wordu pomocí C# – krok za krokem](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Vytvořit markdown z Wordu – kompletní C# průvodce](/words/english/java/document-conversion-and-export/create-markdown-from-word-complete-c-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}