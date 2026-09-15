---
category: general
date: 2026-09-14
description: Vytvořte ActiveX ovládací prvek ve Word dokumentu pomocí C#. Naučte se,
  jak vložit ActiveX, přidat interaktivní tlačítko a programově vygenerovat soubor
  .docx.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create activex control
- how to insert activex
- add interactive button
- create word document
- create button with code
language: cs
lastmod: 2026-09-14
og_description: Vytvořte ActiveX ovládací prvek ve Word dokumentu pomocí C#. Podívejte
  se na tento kompletní příklad, jak vložit ActiveX, přidat interaktivní tlačítko
  a uložit soubor.
og_image_alt: Screenshot of a Word document containing a newly created ActiveX CommandButton
og_title: Vytvořte ActiveX ovládací prvek ve Wordu pomocí C# – krok za krokem průvodce
schemas:
- author: Aspose
  dateModified: '2026-09-14'
  description: Create ActiveX control in a Word document with C#. Learn how to insert
    ActiveX, add interactive button, and generate the .docx file programmatically.
  headline: How to create ActiveX control in a Word document with C#
  type: TechArticle
tags:
- ActiveX
- C#
- Word automation
title: Jak vytvořit ActiveX ovládací prvek ve Word dokumentu pomocí C#
url: /cs/net/working-with-oleobjects-and-activex/how-to-create-activex-control-in-a-word-document-with-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak vytvořit ActiveX ovládací prvek v dokumentu Word pomocí C#

Pokud potřebujete **vytvořit ActiveX ovládací prvek** uvnitř souboru Microsoft Word, tento průvodce vám ukáže kompletní, připravené řešení. Uvidíte přesně, jak vložit ActiveX CommandButton, nastavit jeho vlastnosti a uložit výsledný soubor `.docx` pomocí čistého C# kódu.

Přidání interaktivního tlačítka do dokumentu Word je častý požadavek, když chcete, aby koncoví uživatelé spouštěli makra nebo vlastní logiku přímo z uživatelského rozhraní dokumentu. Níže uvedený příklad ukazuje **jak vložit ActiveX** bez použití nástrojů třetích stran a také pokrývá **jak programově vytvořit Word dokument**.

Na konci tohoto tutoriálu budete schopni **vytvořit tlačítko pomocí kódu**, přizpůsobit jeho popisek a vytvořit přenosný soubor Word, který zachová ActiveX ovládací prvek.

## Požadavky

- .NET 6.0 nebo novější (knihovna Aspose.Words pro .NET funguje s .NET Core a .NET Framework)
- Odkaz na NuGet balíček `Aspose.Words`  
  ```bash
  dotnet add package Aspose.Words
  ```
- Základní znalost C# a objektově orientovaného programování

## Krok 1: Nastavení projektu a import jmenných prostorů

Vytvořte nový konzolový projekt (nebo integrujte kód do jakékoli existující C# aplikace). Naimportujte požadované jmenné prostory, aby kompilátor mohl najít třídy pro zpracování Wordu.

```csharp
using System;
using System.Drawing;               // Provides RectangleF
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Ole;
```

> **Proč je tento krok důležitý** – API `Aspose.Words` poskytuje třídy `Document`, `DocumentBuilder` a `Forms2OleControl`, které vám umožňují manipulovat se soubory Word na úrovni objektů. Bez těchto odkazů by zbytek kódu nekompiloval.

## Krok 2: Vytvoření nového Word dokumentu a DocumentBuilderu

Objekt `Document` představuje celý balíček `.docx`, zatímco `DocumentBuilder` nabízí plynulé API pro vkládání obsahu.

```csharp
// Step 2: Initialize a fresh Word document
Document document = new Document();

// Attach a builder to the document – the builder knows where to write next
DocumentBuilder builder = new DocumentBuilder(document);
```

> **Vysvětlení** – Vytvořením nového `Document` získáte čisté plátno. Kurzorem builderu se nachází na začátku první sekce, připravený na další vložení.

## Krok 3: Vložení ActiveX CommandButton

Použijte `InsertForms2OleControl` k umístění ActiveX ovládacího prvku na konkrétní místo. Metoda vyžaduje typ ovládacího prvku a `RectangleF`, který určuje souřadnice X/Y a velikost (v bodech).

```csharp
// Step 3: Add an ActiveX CommandButton at (100,100) with width 120 and height 30
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    OleControlType.CommandButton,
    new RectangleF(100, 100, 120, 30));
```

> **Proč to funguje** – `OleControlType.CommandButton` říká API, aby vytvořilo standardní Windows CommandButton. Obdélník umístí tlačítko relativně k levému hornímu rohu stránky, což vám umožní **přidat interaktivní tlačítko** přesně tam, kde jej potřebujete.

## Krok 4: Nastavení vlastností tlačítka

Nyní nastavte viditelný text tlačítka (`Caption`) a jeho interní název (`Name`). Tyto vlastnosti jsou to, co uživatelé vidí a na co může VBA kód později odkazovat.

```csharp
// Step 4: Define the button’s caption and programmatic name
commandButton.Caption = "Click Me";
commandButton.Name = "btnClick";
```

> **Praktický tip** – `Name` musí být v dokumentu jedinečný; jinak mohou VBA makra odkazovat na nesprávný ovládací prvek.

## Krok 5: Uložení dokumentu

Nakonec zapište soubor na disk. ActiveX ovládací prvek je uložen uvnitř balíčku Word, takže uložený soubor si zachová plnou funkčnost při otevření v Microsoft Word.

```csharp
// Step 5: Persist the document – the ActiveX control stays embedded
string outputPath = @"C:\Temp\CommandButton.docx";
document.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

> **Výsledek** – Otevřením `CommandButton.docx` ve Wordu se zobrazí klikatelné CommandButton s popiskem „Click Me“. Ovládací prvek lze propojit s makrem pomocí uživatelského rozhraní Wordu (`Developer → Design Mode → Properties`).

## Kompletní výpis zdrojového kódu

Spojením všech kroků dohromady získáte jeden samostatný program, který můžete zkopírovat, vložit a spustit.

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Ole;

class Program
{
    static void Main()
    {
        // Create a new document and a builder
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Insert an ActiveX CommandButton at the desired location
        Forms2OleControl commandButton = builder.InsertForms2OleControl(
            OleControlType.CommandButton,
            new RectangleF(100, 100, 120, 30));

        // Set the button's caption and internal name
        commandButton.Caption = "Click Me";
        commandButton.Name = "btnClick";

        // Save the document – the control is preserved
        string outputPath = @"C:\Temp\CommandButton.docx";
        document.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

### Očekávaný výstup

Spuštěním programu se vypíše potvrzovací řádek:

```
Document saved to C:\Temp\CommandButton.docx
```

Když otevřete vygenerovaný soubor v Microsoft Word, uvidíte **CommandButton** umístěný na zadaných souřadnicích. Kliknutí na tlačítko v režimu návrhu jej zvýrazní; v režimu spuštění se chová jako jakékoli standardní ActiveX tlačítko.

## Běžné varianty a okrajové případy

| Scénář | Úprava |
|----------|------------|
| **Různý typ ovládacího prvku** | Nahraďte `OleControlType.CommandButton` za `OleControlType.CheckBox`, `OleControlType.OptionButton` atd. |
| **Více tlačítek** | Opakovaně volajte `InsertForms2OleControl` a aktualizujte souřadnice `RectangleF` pro každé nové tlačítko. |
| **Dynamické velikosti** | Vypočítejte rozměry obdélníku na základě velikosti stránky (`builder.PageSetup.PageWidth`). |
| **Ukládání do proudu** | Použijte `document.Save(stream, SaveFormat.Docx)`, když potřebujete vrátit soubor z webového API. |
| **Formát Word 97‑2003** | Změňte formát ukládání na `SaveFormat.Doc`, aby se vytvořil soubor `.doc`, který stále obsahuje ActiveX ovládací prvek. |

> **Pro tip:** Vždy testujte vygenerovaný dokument na cílové verzi Wordu, protože starší verze mohou vynutit bezpečnostní nastavení, která ve výchozím nastavení zakazují ActiveX ovládací prvky.

## Často kladené otázky

**Funguje to s .NET Core?**  
Ano. Knihovna Aspose.Words je multiplatformní a plně kompatibilní s .NET Core a .NET 5/6+.

**Mohu přiřadit makro k tlačítku programově?**  
API nepřidává VBA kód přímo. Po vygenerování dokumentu jej otevřete ve Wordu, povolte kartu Developer a zaznamenejte nebo napište makro, které odkazuje na `btnClick`.

**Co když se tlačítko nezobrazí?**  
Zkontrolujte, že je v Wordu povolena karta `Developer` a že dokument není otevřen v **Protected View**. Také ověřte, že souřadnice obdélníku jsou v mezích okrajů stránky.

## Závěr

Nyní víte, jak **vytvořit ActiveX ovládací prvek** uvnitř souboru Word pomocí C#. Tutoriál pokryl **jak vložit ActiveX**, ukázal **přidání interaktivního tlačítka**, předvedl **vytvoření Word dokumentu** od nuly a ilustroval **vytvoření tlačítka pomocí kódu**, které po uložení přetrvává.

Odtud můžete zkoumat další typy ActiveX, propojit tlačítko s VBA makry nebo vložit logiku do větší služby pro generování dokumentů. Experimentujte s různými velikostmi, pozicemi a vlastnostmi ovládacích prvků, aby vyhovovaly přesně požadovanému uživatelskému zážitku.

---

## Co byste se měli naučit dál?

Následující tutoriály pokrývají úzce související témata, která staví na technikách předvedených v tomto průvodci. Každý zdroj obsahuje kompletní funkční ukázky kódu s podrobnými vysvětleními, které vám pomohou zvládnout další funkce API a prozkoumat alternativní přístupy k implementaci ve vašich projektech.

- [Vytvořit nový Word dokument](/words/english/net/add-content-using-documentbuilder/create-new-document/)
- [Vytvořit VBA projekt v Word dokumentu](/words/english/net/working-with-vba-macros/create-vba-project/)
- [Vytvořit a stylovat Word dokument v Aspose.Words pro .NET](/words/english/net/document-styling/apply-paragraph-style/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}