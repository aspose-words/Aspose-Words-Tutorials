---
category: general
date: 2026-09-11
description: Naučte se, jak v C# vytvořit dokument Word a programově přidat tlačítko
  příkazu pomocí Aspose.Words během několika jednoduchých kroků.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document c#
- programmatically add command button
language: cs
lastmod: 2026-09-11
og_description: Vytvořte Word dokument v C# a programově přidejte tlačítko příkazu
  pomocí Aspose.Words. Postupujte podle tohoto kompletního průvodce pro funkční řešení.
og_image_alt: Screenshot of a Word document containing a Submit command button created
  with C#
og_title: Vytvořte Word dokument v C# – přidejte příkazové tlačítko programově
schemas:
- author: Aspose
  dateModified: '2026-09-11'
  description: Learn how to create word document c# and programmatically add a command
    button using Aspose.Words in a few simple steps.
  headline: How to create word document c# and programmatically add a command button
  type: TechArticle
- description: Learn how to create word document c# and programmatically add a command
    button using Aspose.Words in a few simple steps.
  name: How to create word document c# and programmatically add a command button
  steps:
  - name: Launch Word and open `CommandButton.docx`.
    text: Launch Word and open `CommandButton.docx`.
  - name: You should see a button labeled **Submit** in the document body.
    text: You should see a button labeled **Submit** in the document body.
  - name: Hovering over the button reveals the name `btnSubmit` in the **Properties**
      pane (Developer tab → Properties).
    text: Hovering over the button reveals the name `btnSubmit` in the **Properties**
      pane (Developer tab → Properties).
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
- ActiveX
title: Jak v C# vytvořit Word dokument a programově přidat tlačítko příkazu
url: /cs/net/working-with-oleobjects-and-activex/how-to-create-word-document-c-and-programmatically-add-a-com/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak vytvořit Word dokument v C# a programově přidat tlačítko příkazu

Pokud potřebujete **create word document c#** a vložit interaktivní tlačítko, tento průvodce vám přesně ukáže, jak na to. Pomocí Aspose.Words můžete programově přidat tlačítko příkazu během několika řádků kódu, čímž se vyhnete ruční práci s UI ve Wordu.

V tomto tutoriálu se naučíte, jak:

* Inicializovat prázdný Word soubor v C#.
* Vložit ActiveX **CommandButton** ovládací prvek.
* Nastavit vlastnosti tlačítka, jako je název a popisek.
* Uložit dokument, aby se tlačítko zobrazilo při otevření souboru v Microsoft Word.

K provedení nejsou potřeba žádné externí nástroje kromě knihovny Aspose.Words pro .NET a kroky fungují s .NET 6+ nebo .NET Framework 4.6.2 a novějšími.

## Požadavky

Před začátkem se ujistěte, že máte:

| Requirement | Reason |
|------------|--------|
| .NET 6 SDK (or .NET Framework 4.6.2+) | Poskytuje runtime pro C# projekt. |
| Visual Studio 2022 (or any C# IDE) | Umožňuje snadno psát, sestavovat a spouštět kód. |
| Aspose.Words for .NET NuGet package | Zajišťuje třídy `Document`, `DocumentBuilder` a `Forms2OleControl` použité v příkladu. |
| Basic knowledge of C# syntax | Umožňuje vám sledovat kód bez dalších učebních křivek. |

Balíček Aspose.Words můžete přidat pomocí konzole NuGet:

```powershell
Install-Package Aspose.Words
```

## Krok 1: Nastavení nového C# konzolového projektu

Vytvořte konzolovou aplikaci, která vygeneruje Word soubor. Otevřete terminál a spusťte:

```bash
dotnet new console -n WordButtonDemo
cd WordButtonDemo
dotnet add package Aspose.Words
```

Vygenerovaný soubor `Program.cs` bude obsahovat kód ukázaný v následujících krocích.

## Krok 2: Vytvoření prázdného dokumentu a DocumentBuilderu

Prvním krokem je vytvořit objekt `Document`, který představuje prázdný soubor `.docx`, a `DocumentBuilder`, který vám umožní upravovat obsah dokumentu.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Forms;

class Program
{
    static void Main()
    {
        // Step 2: Create a new blank document and a DocumentBuilder to edit it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

**Proč je to důležité:**  
`Document` je kontejner pro všechny Word elementy (odstavce, tabulky, ovládací prvky). `DocumentBuilder` poskytuje plynulé API pro vkládání objektů na aktuální pozici kurzoru, aniž byste museli pracovat s nízkoúrovňovými kolekcemi uzlů.

## Krok 3: Vložení ActiveX CommandButton ovládacího prvku

Aspose.Words podporuje vkládání starších ActiveX ovládacích prvků pomocí metody `InsertForms2OleControl`. Metoda vyžaduje typ ovládacího prvku a požadovanou velikost v bodech.

```csharp
        // Step 3: Insert an ActiveX CommandButton control (size: 100x30 points)
        Forms2OleControl commandButton = builder.InsertForms2OleControl(
            ControlType.CommandButton, 100, 30);
```

**Co se děje pod kapotou:**  
Word považuje ActiveX ovládací prvek za OLE (Object Linking and Embedding) objekt. Třída `Forms2OleControl` obaluje OLE data a vystavuje vlastnosti jako `Name` a `Caption`.

## Krok 4: Nastavení názvu a popisku tlačítka

Po umístění ovládacího prvku můžete přizpůsobit jeho runtime vlastnosti. Nastavení smysluplného `Name` vám pomůže tlačítko později identifikovat, zatímco `Caption` určuje text zobrazený na tlačítku.

```csharp
        // Step 4: Set the button's name and displayed caption
        commandButton.Name = "btnSubmit";
        commandButton.Caption = "Submit";
```

**Tip:**  
Pokud plánujete zpracovávat událost kliknutí tlačítka pomocí VBA, `Name` se stane názvem makra, na který odkazujete, např. `Sub btnSubmit_Click()`.

## Krok 5: Uložení dokumentu na disk

Nakonec zapište dokument do souboru `.docx`. Vyberte složku, do které máte právo zápisu; příklad používá relativní cestu, která se rozřeší do výstupního adresáře projektu.

```csharp
        // Step 5: Save the document containing the button
        string outputPath = Path.Combine(Environment.CurrentDirectory, "CommandButton.docx");
        doc.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

Spuštěním programu vznikne `CommandButton.docx`. Otevřením souboru v Microsoft Word se zobrazí klikatelné tlačítko **Submit**:

![Word dokument s tlačítkem Submit](/images/command-button.png "Snímek obrazovky Word dokumentu obsahujícího tlačítko Submit vytvořené v C#")

*Text alternativního obrázku (og_image_alt):* `Snímek obrazovky Word dokumentu obsahujícího tlačítko Submit vytvořené v C#`

## Ověření výsledku

1. Spusťte Word a otevřete `CommandButton.docx`.  
2. Měli byste vidět tlačítko označené **Submit** v těle dokumentu.  
3. Při najetí myší na tlačítko se v panelu **Properties** (záložka Developer → Properties) zobrazí název `btnSubmit`.  

Pokud se tlačítko nezobrazí, ujistěte se, že je v Wordu povolena záložka **Developer** (Soubor → Možnosti → Přizpůsobit pás → zaškrtněte *Developer*). ActiveX ovládací prvky jsou skryté, když je záložka zakázána.

## Řešení běžných variant a okrajových případů

| Situation | Recommended adjustment |
|-----------|------------------------|
| **Různá velikost tlačítka** | Změňte argumenty šířky a výšky v `InsertForms2OleControl`. Například `150, 40` vytvoří větší tlačítko. |
| **Více tlačítek** | Volajte `InsertForms2OleControl` opakovaně a mezi voláními posouvejte kurzor builderu (`builder.Writeln();`). |
| **Tlačítko bez ActiveX** | Použijte `InsertFormField` k přidání staršího formulářového pole (např. zaškrtávacího políčka), pokud potřebujete kompatibilitu se staršími verzemi Wordu, které blokují ActiveX. |
| **Cross‑platform použití** | ActiveX ovládací prvky fungují jen ve Windows verzích Wordu. Pro Mac nebo webové prohlížeče zvažte vložení hypertextového odkazu stylovaného jako tlačítko. |
| **Bezpečnostní upozornění** | Word může při otevření dokumentu obsahujícího ActiveX ovládací prvky zobrazit bezpečnostní výzvu. Podepsání dokumentu důvěryhodným certifikátem snižuje tuto překážku. |

## Kompletní, spustitelný příklad

Níže je kompletní program, který můžete zkopírovat a vložit do `Program.cs`. Po přidání NuGet balíčku Aspose.Words se zkompiluje a spustí bez úprav.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing.Forms;

class Program
{
    static void Main()
    {
        // Create a new blank document and a DocumentBuilder to edit it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert an ActiveX CommandButton control (size: 100x30 points)
        Forms2OleControl commandButton = builder.InsertForms2OleControl(
            ControlType.CommandButton, 100, 30);

        // Set the button's name and displayed caption
        commandButton.Name = "btnSubmit";
        commandButton.Caption = "Submit";

        // Save the document containing the button
        string outputPath = Path.Combine(Environment.CurrentDirectory, "CommandButton.docx");
        doc.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

**Očekávaný výstup v konzoli:**

```
Document saved to C:\Path\To\WordButtonDemo\bin\Debug\net6.0\CommandButton.docx
```

Otevřením vygenerovaného souboru se zobrazí tlačítko **Submit** připravené k interakci.

## Závěr

Nyní víte, jak **create word document c#** a **programově přidat command button** ovládací prvky pomocí Aspose.Words. Proces se zjednoduší na inicializaci `Document`, vložení `Forms2OleControl`, nastavení jeho vlastností a uložení souboru. Odtud můžete:

* Přidat další ovládací prvky (např. zaškrtávací políčka, textová pole) změnou `ControlType`.
* Připojit VBA makra k tlačítku pro vlastní logiku.
* Kombinovat tuto techniku s dalšími funkcemi Aspose.Words, jako je hromadná korespondence nebo vyplňování šablon.

Experimentujte s různými velikostmi, popisky a více tlačítky, aby vyhovovaly vašemu automatizačnímu scénáři. Šťastné programování!

## Co byste se měli naučit dál?

Následující tutoriály pokrývají úzce související témata, která staví na technikách předvedených v tomto průvodci. Každý zdroj obsahuje kompletní funkční ukázky kódu s podrobnými vysvětleními, které vám pomohou zvládnout další funkce API a prozkoumat alternativní přístupy k implementaci ve vašich projektech.

- [Create Word Document with Header and Footer Using Aspose.Words](/words/english/net/header-footer-formatting/create-header-footer/)
- [Create Word Document with Aspose.Words for .NET](/words/english/net/add-content-using-document-builder/insert-paragraph/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}