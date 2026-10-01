---
category: general
date: 2026-09-30
description: Přidejte ActiveX ovládací prvek do dokumentu Word pomocí C#. Naučte se,
  jak vložit ActiveX tlačítko, přidat příkazové tlačítko a učinit jej kliknutelným.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- activex control word
- how to insert activex
- how to add command button
- insert activex button
- add clickable button word
language: cs
lastmod: 2026-09-30
og_description: Přidejte ActiveX kontrolu do dokumentu Word pomocí C#. Postupujte
  podle tohoto kompletního návodu, jak vložit ActiveX tlačítko, přidat příkazové tlačítko
  a učinit jej kliknutelným.
og_image_alt: Word document displaying an inserted ActiveX command button
og_title: Přidejte ActiveX ovládací prvek do dokumentů Word – krok za krokem průvodce
  C#
schemas:
- author: Aspose
  dateModified: '2026-09-30'
  description: Add an ActiveX control word to a Word document using C#. Learn how
    to insert an ActiveX button, add a command button, and make it clickable.
  headline: How to add an ActiveX control word in Word with C#
  type: TechArticle
tags:
- ActiveX
- Aspose.Words
- C#
- Word automation
title: Jak přidat ActiveX ovládací prvek do Wordu pomocí C#
url: /cs/net/working-with-oleobjects-and-activex/how-to-add-an-activex-control-word-in-word-with-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak přidat ActiveX control word do Wordu pomocí C#

Pokud potřebujete vložit **ActiveX control word** do souboru Microsoft Word, tento průvodce vám přesně ukáže, jak na to. Uvidíte kompletní, spustitelný příklad, který vloží klikací tlačítko, uloží dokument a funguje s nejnovější verzí Aspose.Words pro .NET.

Přidání ActiveX control word vám umožní vytvářet interaktivní formuláře, vlastní dialogy nebo jednoduché UI prvky, které se chovají jako nativní ovládací prvky Wordu. Ať už vytváříte šablonu smlouvy vyžadující interakci uživatele nebo zprávu, která potřebuje tlačítko „Run“, níže uvedené kroky pokrývají vše, co potřebujete.

## Požadavky

* .NET 6.0 SDK nebo novější (kód také funguje s .NET Framework 4.8)
* Visual Studio 2022 (nebo jakékoli IDE podporující C#)
* Aspose.Words pro .NET nainstalováno (`dotnet add package Aspose.Words`)
* Základní znalost C# a struktury Word dokumentu

> **Pro tip:** Metoda `InsertForms2OleControl` funguje jen s legacy ovládacími prvky „Forms 2.0“, což jsou ActiveX ovládací prvky, které Word používá pro formulářová pole. Pokud cílíte na novější verze Office, ovládací prvek se stále správně vykreslí v desktopovém klientovi.

## Krok 1: Nastavení projektu a import jmenných prostorů

Vytvořte nový konzolový projekt a přidejte požadované `using` direktivy. Tím zajistíte, že kompilátor najde třídy `Document`, `DocumentBuilder` a `OleControlType`.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
```

Jmenný prostor `Aspose.Words` poskytuje vysoce‑úrovňová API pro zpracování Wordu, zatímco `Aspose.Words.Drawing` obsahuje výčtový typ `OleControlType`, potřebný k určení typu ActiveX ovládacího prvku.

## Krok 2: Načtení zdrojového Word dokumentu

Musíte začít se souborem Word, který chcete upravit. Následující kód načte `input.docx` ze složky, kterou určíte.

```csharp
// Step 2: Load the Word document you want to modify
string inputPath = @"C:\Docs\input.docx";
Document doc = new Document(inputPath);
```

Pokud soubor neexistuje, Aspose.Words vyhodí `FileNotFoundException`. Zabalte volání do `try/catch` bloku, pokud potřebujete elegantní zpracování chyb.

## Krok 3: Vytvoření DocumentBuilder pro úpravu dokumentu

`DocumentBuilder` je hlavní nástroj pro vkládání textu, obrázků a ovládacích prvků. Udržuje kurzor, který ukazuje na místo, kam bude umístěn další prvek.

```csharp
// Step 3: Create a DocumentBuilder to work with the document's content
DocumentBuilder builder = new DocumentBuilder(doc);
```

Ve výchozím nastavení je kurzor builderu umístěn na začátku první sekce. Můžete jej přesunout pomocí metod jako `MoveToDocumentEnd()` nebo `MoveToParagraph(index)`, pokud chcete tlačítko umístit jinam.

## Krok 4: Vložení ActiveX CommandButton ovládacího prvku

Nyní přichází jádro tutoriálu: vložení **ActiveX control word**, který se zobrazí jako klikací tlačítko. Metoda `InsertForms2OleControl` přijímá dva argumenty – typ ovládacího prvku a popisek (nebo název) ovládacího prvku.

```csharp
// Step 4: Insert an ActiveX CommandButton control with the caption "ClickMe"
builder.InsertForms2OleControl(OleControlType.CommandButton, "ClickMe");
```

* **Proč použít `OleControlType.CommandButton`?**  
  Říká Wordu, aby vytvořil klasické tlačítko Forms 2.0, které zobrazuje popisek a může být později propojeno s makrem nebo VBA skriptem.

* **Co dělá popisek?**  
  Řetězec `"ClickMe"` se stane viditelným textem tlačítka. Můžete jej změnit na cokoli, co odpovídá vašemu UI.

### Vložení tlačítka na konkrétní místo

Pokud potřebujete tlačítko po konkrétním odstavci, nejprve přesuňte builder:

```csharp
builder.MoveToParagraph(2); // moves to the third paragraph (zero‑based index)
builder.InsertParagraph(); // optional: add a blank line before the button
builder.InsertForms2OleControl(OleControlType.CommandButton, "Submit");
```

## Krok 5: Uložení upraveného dokumentu

Po vložení ovládacího prvku uložte změny do nového souboru (nebo přepište originál).

```csharp
// Step 5: Save the modified document
string outputPath = @"C:\Docs\output.docx";
doc.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

Když otevřete `output.docx` v desktopové verzi Wordu, uvidíte tlačítko označené **ClickMe** (nebo **Submit**, podle použitého popisku). Kliknutí na tlačítko v režimu návrhu nic neprovedne; můžete mu později přiřadit makro přes kartu „Developer“ ve Wordu.

## Kompletní, spustitelný příklad

Níže je samostatný program, který demonstruje celý postup. Zkopírujte jej do `Program.cs` nového konzolového aplikace a spusťte.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace ActiveXControlWordDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // Paths – adjust to your environment
            string inputPath = @"C:\Docs\input.docx";
            string outputPath = @"C:\Docs\output.docx";

            // 1️⃣ Load the source document
            Document doc = new Document(inputPath);

            // 2️⃣ Create a builder to edit the document
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Optional: move to the end of the document
            builder.MoveToDocumentEnd();
            builder.Writeln(); // add a blank line before the button

            // 3️⃣ Insert the ActiveX CommandButton (the core of the activex control word)
            builder.InsertForms2OleControl(OleControlType.CommandButton, "ClickMe");

            // 4️⃣ Save the result
            doc.Save(outputPath);
            Console.WriteLine($"Successfully saved the document with an ActiveX button to: {outputPath}");
        }
    }
}
```

### Očekávaný výstup

* Konzole vypíše zprávu o úspěchu s cestou k výstupu.
* Otevření `output.docx` zobrazí tlačítko **ClickMe** na místě, kde jej builder vložil.
* Tlačítko lze vybrat, změnit jeho velikost nebo mu přiřadit makro přes **Developer → Design Mode** ve Wordu.

## Časté otázky a řešení okrajových případů

| Question | Answer |
|----------|--------|
| **Jak vložit ActiveX tlačítko do záhlaví/pati?** | Přesuňte builder do záhlaví/pati pomocí `builder.MoveToHeaderFooter(HeaderFooterType.HeaderPrimary)` před voláním `InsertForms2OleControl`. |
| **Co když potřebuji zaškrtávací políčko místo tlačítka?** | Použijte `OleControlType.CheckBox` a jako popisek zadejte například `"Agree"`. |
| **Bude tlačítko fungovat ve Word Online?** | Ne. Word Online nepodporuje legacy Forms 2.0 ActiveX ovládací prvky. Tlačítko se vykreslí jen v desktopovém klientovi. |
| **Mohu nastavit velikost tlačítka programově?** | Po vložení získáte objekt `Shape` pomocí `builder.CurrentParagraph.Runs[0].GetShape()` a upravíte `Width`/`Height`. |
| **Existuje způsob, jak přiřadit makro z kódu?** | Aspose.Words neposkytuje úpravu maker. Musíte dokument otevřít ve Wordu a makro přiřadit ručně nebo použít Office Interop API. |

## Tipy pro produkční použití

* **Vyhněte se pevně zakódovaným cestám** – použijte `Path.Combine` a konfigurační soubory.
* **Uvolněte `Document`** – zabalte jej do `using` bloku, pokud pracujete s velkými soubory, aby se paměť rychle uvolnila.
* **Ověřte výstup** – programově zkontrolujte, že dokument obsahuje tvar typu `OleControl` iterací `doc.GetChildNodes(NodeType.Shape, true)`.
* **Bezpečnostní poznámka** – ActiveX ovládací prvky mohou spouštět kód na klientském počítači. Dokumenty distribuujte jen důvěryhodným uživatelům a zvažte digitální podpisy.

## Závěr

Nyní víte, jak přidat **ActiveX control word** do Word dokumentu pomocí C#. Načtením dokumentu, vytvořením `DocumentBuilder`, vložením tlačítka příkazu pomocí `InsertForms2OleControl` a uložením souboru můžete automatizovat tvorbu interaktivních Word formulářů. Experimentujte s dalšími hodnotami `OleControlType`, umisťujte ovládací prvky do záhlaví nebo tabulek a kombinujte je s makry pro bohatší uživatelský zážitek.

---

*Další kroky*: prozkoumejte **jak vložit ActiveX** ovládací prvky jiných typů, naučte se **jak přidat obslužné rutiny pro command button** pomocí VBA a přečtěte si **nejlepší postupy pro vkládání ActiveX tlačítka** pro multiplatformní kompatibilitu.

## Co byste se měli naučit dál?

Následující tutoriály pokrývají úzce související témata, která staví na technikách předvedených v tomto průvodci. Každý zdroj obsahuje kompletní funkční ukázky kódu s podrobným vysvětlením, které vám pomohou zvládnout další funkce API a prozkoumat alternativní přístupy k implementaci ve vašich projektech.

- [Vkládání OLE objektů a ActiveX ovládacích prvků do Word dokumentů](/words/english/python-net/document-structure-and-content-manipulation/document-ole-objects-active-x/)
- [Přidání Combo Box formulářového pole do Word dokumentu pomocí Aspose.Words pro .NET](/words/english/net/add-content-using-documentbuilder/insert-combo-box/)
- [Přidání Check Box formulářového pole do Word dokumentu pomocí Aspose.Words pro .NET](/words/english/net/add-content-using-documentbuilder/insert-check-box/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}