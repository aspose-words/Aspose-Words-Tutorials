---
category: general
date: 2026-10-20
description: Vytvořte programově dokument Word a přidejte příkazové tlačítko pomocí
  Aspose.Words. Naučte se vložit ActiveX ovládací prvek a nastavit popisek tlačítka.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document programmatically
- add command button
- add activex control
- insert activex button
- set button caption
language: cs
lastmod: 2026-10-20
og_description: Vytvořte programově dokument Word a vložte do něj ovládací prvek ActiveX
  Command Button. Tento tutoriál vysvětluje, jak vložit ovládací prvek a nastavit
  jeho popisek pomocí Aspose.Words.
og_image_alt: Word file showing an ActiveX command button inserted by Aspose.Words
og_title: Vytvořte dokument Word programově – přidejte tlačítko ActiveX
schemas:
- author: Aspose
  dateModified: '2026-10-20'
  description: Create Word document programmatically and add a command button using
    Aspose.Words. Learn to insert an ActiveX control and set button caption.
  headline: Create Word document programmatically with an ActiveX button
  type: TechArticle
- description: Create Word document programmatically and add a command button using
    Aspose.Words. Learn to insert an ActiveX control and set button caption.
  name: Create Word document programmatically with an ActiveX button
  steps:
  - name: 'Open a terminal or Visual Studio and create a new console project:'
    text: 'Open a terminal or Visual Studio and create a new console project:'
  - name: 'Add the Aspose.Words package:'
    text: 'Add the Aspose.Words package:'
  - name: '(Optional) If you have a license file, place it in the project root and
      add the following line at the start of `Program.cs` to avoid evaluation watermarks:'
    text: '(Optional) If you have a license file, place it in the project root and
      add the following line at the start of `Program.cs` to avoid evaluation watermarks:'
  - name: Open `ActiveXCommandButton.docx` in Microsoft Word.
    text: Open `ActiveXCommandButton.docx` in Microsoft Word.
  - name: Switch to **Design Mode** (Developer tab → **Design Mode**) to see the button’s
      borders.
    text: Switch to **Design Mode** (Developer tab → **Design Mode**) to see the button’s
      borders.
  - name: If the button does not appear, check that the **Developer** tab is enabled
      and that your Word version supports ActiveX controls.
    text: If the button does not appear, check that the **Developer** tab is enabled
      and that your Word version supports ActiveX controls.
  - name: For macro‑enabled files (`.docm`), ensure the macro name in `OnClick` matches
      a VBA routine; otherwise Word will display a security warning.
    text: For macro‑enabled files (`.docm`), ensure the macro name in `OnClick` matches
      a VBA routine; otherwise Word will display a security warning.
  type: HowTo
tags:
- Aspose.Words
- C#
- ActiveX
- Word automation
title: Vytvořit dokument Word programově pomocí tlačítka ActiveX
url: /cs/net/working-with-oleobjects-and-activex/create-word-document-programmatically-with-an-activex-button/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Vytvoření dokumentu Word programově s tlačítkem ActiveX

Vytvořte dokument Word programově pomocí Aspose.Words a poté přidejte tlačítko příkazu, na které mohou uživatelé kliknout. Tento návod vás provede vložením ActiveX ovládacího prvku, nastavením jeho vlastností a uložením výsledku jako soubor **.docx**.

Uvidíte kompletní, spustitelný příklad, který můžete zkopírovat do konzolové aplikace. Na konci tutoriálu budete schopni vygenerovat soubor Word, který obsahuje plně funkční tlačítko příkazu, a pochopíte, jak **add command button**, **add activex control**, **insert activex button** a **set button caption** provádět přímo v C# kódu.

## Požadavky

* .NET 6.0 SDK nebo novější nainstalovaný  
* Visual Studio 2022 (nebo jakékoli C#‑kompatibilní IDE)  
* Licenční soubor Aspose.Words pro .NET (bezplatná zkušební verze funguje pro tento příklad)  
* Základní znalost C# a systému projektů .NET  

Žádné další NuGet balíčky nejsou vyžadovány kromě **Aspose.Words**, protože podpora ActiveX je součástí knihovny.

## Krok 1: Nastavení projektu a přidání Aspose.Words

1. Otevřete terminál nebo Visual Studio a vytvořte nový konzolový projekt:

   ```bash
   dotnet new console -n WordActiveXDemo
   cd WordActiveXDemo
   ```

2. Přidejte balíček Aspose.Words:

   ```bash
   dotnet add package Aspose.Words
   ```

3. (Volitelné) Pokud máte licenční soubor, umístěte jej do kořenového adresáře projektu a přidejte následující řádek na začátek `Program.cs`, aby se odstranily vodotisky z hodnocení:

   ```csharp
   Aspose.Words.License license = new Aspose.Words.License();
   license.SetLicense("Aspose.Words.lic");
   ```

## Krok 2: Vytvoření dokumentu Word programově – inicializace dokumentu

Prvním krokem je **create Word document programmatically**. To provedete vytvořením instance objektu `Document` a `DocumentBuilder`, který vám umožní upravovat obsah dokumentu.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;   // Provides ActiveX control types
using System.Drawing;        // For Point and Size structs

// Initialize a new blank document
Document document = new Document();

// DocumentBuilder gives a cursor‑based API for inserting elements
DocumentBuilder builder = new DocumentBuilder(document);
```

`Document` představuje celý soubor, zatímco `DocumentBuilder` udržuje kurzor, který můžete přesunout na libovolné místo v dokumentu. Toto oddělení udržuje API čisté a umožňuje vám později **add activex control** bez ručního spravování nízkoúrovňových struktur.

## Krok 3: Přidání tlačítka příkazu – vložení ActiveX ovládacího prvku

Nyní **add command button** vložením ActiveX ovládacího prvku typu `OleControlType.CommandButton`. Metoda `InsertForms2OleControl` vyžaduje typ ovládacího prvku, umístění (`Point`) a velikost (`Size`).

```csharp
// Define where the button will appear (X = 100 pt, Y = 150 pt)
Point buttonPosition = new Point(100, 150);

// Define the button dimensions (width = 120 pt, height = 30 pt)
Size buttonSize = new Size(120, 30);

// Insert the ActiveX command button at the current cursor location
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    OleControlType.CommandButton, // control type
    buttonPosition,              // position
    buttonSize);                 // size
```

Výše uvedené volání **insert activex button** do dokumentu na přesně zadaných souřadnicích. Souřadnice jsou měřeny v bodech (1 pt ≈ 1/72 in). Pokud potřebujete tlačítko v konkrétním odstavci, nejprve přesuňte kurzor builderu:

```csharp
builder.Writeln("Click the button below:");
builder.MoveToDocumentEnd(); // places the cursor after the paragraph
```

## Krok 4: Nastavení popisku tlačítka – úprava textu tlačítka příkazu

Tlačítko bez popisku je matoucí, proto **set button caption** na něco smysluplného. Vlastnost `Caption` určuje text zobrazený na tlačítku, zatímco `Name` dává ovládacímu prvku programový identifikátor.

```csharp
// Give the button a unique name for later reference
commandButton.Name = "btnSubmit";

// Set the visible text on the button
commandButton.Caption = "Submit";

// Optional: assign a macro name that Word will call when the button is clicked
commandButton.OnClick = "SubmitForm()";
```

Pokud později exportujete dokument do formátu podporujícího makra (`.docm`), hodnota `OnClick` musí odpovídat názvu VBA makra. Pro běžný `.docx` je vlastnost uložena, ale neprovádí se, což je v pořádku pro většinu automatizačních scénářů.

## Krok 5: Uložení dokumentu obsahujícího ActiveX tlačítko

Po nastavení ovládacího prvku můžete **save the document**. Vyberte adresář, do kterého máte právo zapisovat, a použijte příponu `.docx` pro maximální kompatibilitu.

```csharp
// Replace with your desired output folder
string outputPath = Path.Combine(Environment.CurrentDirectory, "ActiveXCommandButton.docx");

// Save the document to disk
document.Save(outputPath);
```

Když otevřete vygenerovaný soubor v Microsoft Word, uvidíte tlačítko označené **Submit** na zadaných souřadnicích. Kliknutí na tlačítko v desktopovém klientu se pokusí spustit makro `SubmitForm` (pokud existuje).

## Krok 6: Ověření výsledku a řešení běžných problémů

1. Otevřete `ActiveXCommandButton.docx` v Microsoft Word.  
2. Přepněte do **Design Mode** (karta Developer → **Design Mode**) a zobrazte okraje tlačítka.  
3. Pokud se tlačítko nezobrazí, zkontrolujte, že je karta **Developer** povolena a že vaše verze Wordu podporuje ActiveX ovládací prvky.  
4. Pro soubory podporující makra (`.docm`) se ujistěte, že název makra v `OnClick` odpovídá VBA rutině; jinak Word zobrazí bezpečnostní varování.

### Tip

ActiveX ovládací prvky jsou pouze pro Windows. Pokud potřebujete multiplatformní interaktivitu, zvažte použití **Content Controls** (`RichTextContentControl`) místo ActiveX tlačítka.

## Kompletní zdrojový kód

Níže je kompletní, připravený ke spuštění program. Zkopírujte jej do `Program.cs` a spusťte `dotnet run`.



## Co byste se měli naučit dál?

Následující tutoriály pokrývají úzce související témata, která staví na technikách předvedených v tomto návodu. Každý zdroj obsahuje kompletní funkční ukázky kódu s podrobnými vysvětleními, které vám pomohou zvládnout další funkce API a prozkoumat alternativní přístupy k implementaci ve vašich projektech.

- [Create Word Document with ActiveX Button – C# Guide](/words/english/net/working-with-oleobjects-and-activex/create-word-document-with-activex-button-c-guide/)
- [Add Command Button to Word Document with Aspose.Words – Complete Guide](/words/english/net/working-with-oleobjects-and-activex/add-command-button-to-word-document-with-aspose-words-comple/)
- [create word document button with Aspose.Words – Full Code Example](/words/english/net/working-with-oleobjects-and-activex/create-word-document-button-with-aspose-words-full-code-exam/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}