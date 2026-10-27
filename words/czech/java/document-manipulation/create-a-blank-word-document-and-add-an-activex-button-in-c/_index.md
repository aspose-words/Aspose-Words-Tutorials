---
category: general
date: 2026-10-23
description: Vytvořte prázdný dokument Word pomocí C# a naučte se, jak vložit ActiveX
  ovládací prvky, včetně tlačítka, pomocí Aspose.Words.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- how to insert activex
- create activex control
- word document activex button
language: cs
lastmod: 2026-10-23
og_description: Vytvořte prázdný dokument Word pomocí C# a naučte se, jak vložit ActiveX
  ovládací prvky, včetně tlačítka, pomocí Aspose.Words.
og_image_alt: Result of creating a blank Word document with an ActiveX Submit button
og_title: Vytvořte prázdný dokument Word a přidejte tlačítko ActiveX v C#
schemas:
- author: Aspose
  dateModified: '2026-10-23'
  description: Create blank Word document with C# and learn how to insert ActiveX
    controls, including a button, using Aspose.Words.
  headline: Create a blank Word document and add an ActiveX button in C#
  type: TechArticle
- description: Create blank Word document with C# and learn how to insert ActiveX
    controls, including a button, using Aspose.Words.
  name: Create a blank Word document and add an ActiveX button in C#
  steps:
  - name: Instantiate a `Document`.
    text: Instantiate a `Document`.
  - name: Use `DocumentBuilder` to work with the file.
    text: Use `DocumentBuilder` to work with the file.
  - name: Call `InsertForms2OleControl` to **how to insert activex** controls.
    text: Call `InsertForms2OleControl` to **how to insert activex** controls.
  - name: Configure the control’s properties (**create activex control**).
    text: Configure the control’s properties (**create activex control**).
  - name: Save the file, yielding a **word document activex button** ready for VBA
      integration.
    text: Save the file, yielding a **word document activex button** ready for VBA
      integration.
  type: HowTo
tags:
- Aspose.Words
- C#
- ActiveX
title: Vytvořte prázdný dokument Word a přidejte ActiveX tlačítko v C#
url: /cs/java/document-manipulation/create-a-blank-word-document-and-add-an-activex-button-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Vytvořte prázdný dokument Word a přidejte ActiveX tlačítko v C#

Pokud potřebujete **vytvořit prázdný dokument Word** programově, tento návod vám přesně ukáže, jak na to. Uvidíte kompletní, spustitelný příklad, který vytvoří nový dokument, vloží ActiveX CommandButton a uloží soubor — vše pomocí Aspose.Words pro .NET.

Přidání **ActiveX tlačítka** vám umožní vložit interaktivní funkčnost, kterou lze použít v šablonách s makry nebo řešeních pouze pro Windows. Na konci tohoto tutoriálu budete schopni vložit jakékoli ActiveX ovládací prvky, ale zaměříme se na nejčastější scénář: **tlačítko ActiveX v dokumentu Word**, které odesílá formulář.

## Požadavky

* .NET 6.0 nebo novější (kód také funguje s .NET Framework 4.7+)
* Visual Studio 2022 (nebo jakékoli C# IDE)
* **Aspose.Words for .NET** NuGet balíček  
  ```bash
  dotnet add package Aspose.Words
  ```
* Základní znalost syntaxe C#

> **Tip:** Aspose.Words je komerční knihovna, ale nabízí bezplatnou dočasnou licenci pro testování. Nainstalujte licenci co nejdříve, abyste se vyhnuli vodotisku z evaluační verze.

## Krok 1: Vytvořte prázdný dokument Word pomocí Aspose.Words

Prvním krokem je vytvořit instanci objektu `Document`. Ten představuje prázdný soubor `.docx` v paměti.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create a new blank document
Document document = new Document();
```

`Document` začíná bez sekcí, stránek ani obsahu. Je to čistý list, který potřebujete pro scénáře **vytvořit prázdný dokument Word**, jako je generování zpráv od nuly.

## Krok 2: Získejte DocumentBuilder pro úpravu dokumentu

`DocumentBuilder` poskytuje pohodlné API pro přidávání textu, obrázků a ovládacích prvků. Použijeme jej k umístění ActiveX ovládacího prvku.

```csharp
// Obtain a DocumentBuilder tied to the blank document
DocumentBuilder builder = new DocumentBuilder(document);
```

Builder automaticky přidá výchozí sekci a první stránku, takže můžete okamžitě začít vkládat objekty.

## Krok 3: Jak vložit ActiveX ovládací prvky do dokumentu

Aspose.Words poskytuje metodu `InsertForms2OleControl` pro vložení OLE/ActiveX objektů. Metoda vyžaduje typ ovládacího prvku, šířku a výšku (v bodech). Níže vložíme **CommandButton** — klasické tlačítko formuláře, které vidíte ve starších šablonách Word.

```csharp
// Insert an ActiveX CommandButton control (100 × 30 points)
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    Forms2OleControlType.COMMANDBUTTON, 100, 30);
```

> **Proč to funguje:** `Forms2OleControlType.COMMANDBUTTON` říká Wordu, aby vytvořil tlačítko, které může reagovat na události kliknutí, když je dokument otevřen ve Windows prostředí, které podporuje ActiveX.

## Krok 4: Vytvořte ActiveX ovládací prvek – nastavte jeho vlastnosti

Nyní přiřadíme tlačítku programový název a viditelný popisek. Toto je část **vytvořit ActiveX ovládací prvek**, kterou vývojáři často přehlížejí.

```csharp
// Set the button's name (used in VBA) and the text shown to users
commandButton.Name = "btnSubmit";
commandButton.Caption = "Submit";
```

* `Name` je identifikátor, na který budete odkazovat z VBA maker (`ActiveDocument.InlineShapes("btnSubmit")`).
* `Caption` je popisek zobrazený na samotném tlačítku.

## Krok 5: Uložte dokument Word s ActiveX tlačítkem

Nakonec zapíšete dokument na disk. Přípona souboru musí být `.docx` (nebo `.docm`, pokud plánujete později přidat makra). Příklad ukládá do složky placeholder — nahraďte ji vlastní cestou.

```csharp
// Save the document containing the ActiveX button
string outputPath = @"C:\Temp\ActiveXButton.docx";
document.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

Když otevřete výsledný soubor v Microsoft Word (pouze Windows), uvidíte funkční **tlačítko ActiveX v dokumentu Word**, které lze propojit s VBA kódem.

## Kompletní funkční příklad

Níže je kompletní program, který můžete zkopírovat a vložit do nového konzolového projektu.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace ActiveXButtonDemo
{
    class Program
    {
        static void Main()
        {
            // 1. Create a blank Word document
            Document document = new Document();

            // 2. Get a builder to edit the document
            DocumentBuilder builder = new DocumentBuilder(document);

            // 3. Insert an ActiveX CommandButton (100 × 30 points)
            Forms2OleControl commandButton = builder.InsertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON, 100, 30);

            // 4. Configure the button
            commandButton.Name = "btnSubmit";
            commandButton.Caption = "Submit";

            // 5. Save the file
            string outputPath = @"C:\Temp\ActiveXButton.docx";
            document.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

**Očekávaný výstup po spuštění programu**

```
Document saved to C:\Temp\ActiveXButton.docx
```

Otevřete vygenerovaný soubor `ActiveXButton.docx` ve Wordu a uvidíte tlačítko s popiskem **Submit** umístěné v horní části první stránky.

## Okrajové případy a běžné úskalí

| Situace | Na co si dát pozor | Doporučení |
|-----------|-------------------|----------------|
| Běh na macOS nebo Linuxu | ActiveX je technologie pouze pro Windows, takže tlačítko se zobrazí jako placeholder. | Používejte tutoriál jen pro šablony cílené na Windows. |
| Dokument otevřený ve Word Online | ActiveX ovládací prvky nejsou podporovány v prohlížečovém zobrazení. | Poskytněte náhradní UI nebo uživatele instruujte, aby soubor otevřeli v desktopovém klientu. |
| Potřeba souboru s makry | `.docx` soubory nemohou ukládat VBA kód. | Uložte jako `.docm` (`document.Save("MyFile.docm", SaveFormat.Docm)`) a makro přidejte samostatně. |
| Nesoulad velikosti ovládacího prvku | Hodnoty šířky/výšky jsou v bodech (1 pt ≈ 1/72 in). | Upravit číselné hodnoty tak, aby dosáhly požadované vizuální velikosti. |

## Často kladené otázky

**Jak vložit ActiveX ovládací prvky jinak než tlačítko?**  
Použijte stejnou metodu `InsertForms2OleControl`, ale předávejte jinou hodnotu výčtu `Forms2OleControlType`, například `COMBOBOX` nebo `LISTBOX`.

**Mohu změnit font nebo barvu tlačítka?**  
Vzhled ActiveX tlačítka řídí hostitelská aplikace (Word) a podkladové téma Windows. Vlastnosti jako `ForeColor` a `BackColor` můžete po otevření dokumentu upravit pomocí VBA.

**Existuje způsob, jak přidat obslužnou rutinu kliknutí přímo z C#?**  
Ne. Událost kliknutí musí být zpracována ve VBA nebo v doplňku pro Word, protože tlačítko běží uvnitř procesu Wordu, ne ve vaší .NET aplikaci.

## Závěr

Nyní víte, jak programově **vytvořit prázdný dokument Word** a vložit **ActiveX tlačítko** pomocí Aspose.Words pro .NET. Pokryté kroky:

1. Vytvořte instanci `Document`.
2. Použijte `DocumentBuilder` k práci se souborem.
3. Zavolejte `InsertForms2OleControl` pro **jak vložit activex** ovládací prvky.
4. Nakonfigurujte vlastnosti ovládacího prvku (**vytvořit activex ovládací prvek**).
5. Uložte soubor, čímž získáte **tlačítko ActiveX v dokumentu Word** připravené pro integraci VBA.

Odtud můžete zkoumat přidávání dalších typů ovládacích prvků, propojení VBA maker nebo převod dokumentu do PDF při zachování tlačítka (jako statického obrázku). Experimentujte s různými velikostmi, popisky a názvy.

## Co byste se měli naučit dál?

Následující tutoriály pokrývají úzce související témata, která staví na technikách předvedených v tomto návodu. Každý zdroj obsahuje kompletní funkční ukázky kódu s podrobnými vysvětleními, které vám pomohou zvládnout další funkce API a prozkoumat alternativní přístupy k implementaci ve vašich projektech.

- [Jak přidat ActiveX tlačítko do dokumentu Word pomocí Aspose.Words](/words/english/net/working-with-oleobjects-and-activex/how-to-add-activex-button-in-a-word-document-with-aspose-wor/)
- [Vytvořit dokument Word s ActiveX tlačítkem – průvodce pro C#](/words/english/net/working-with-oleobjects-and-activex/create-word-document-with-activex-button-c-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}