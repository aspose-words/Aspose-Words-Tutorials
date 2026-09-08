---
category: general
date: 2026-09-08
description: Jak uložit docx při vkládání ActiveX ovládacího prvku v C#. Postupujte
  podle tohoto návodu krok po kroku pro programové přidání tlačítka příkazu.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to save docx
- insert activex control
- add activex button
- create word document programmatically
- how to add command button
language: cs
lastmod: 2026-09-08
og_description: Jak uložit soubor docx při vkládání ActiveX ovládacího prvku v C#.
  Tento tutoriál vás provede vytvořením Word dokumentu programově, přidáním příkazového
  tlačítka a uložením souboru.
og_image_alt: How to save docx with an ActiveX command button displayed in the document
og_title: Jak uložit docx a vložit ActiveX tlačítko v C#
schemas:
- author: Aspose
  dateModified: '2026-09-08'
  description: How to save docx while inserting an ActiveX control in C#. Follow this
    step‑by‑step guide to add a command button programmatically.
  headline: How to save docx and insert an ActiveX button with C#
  type: TechArticle
tags:
- C#
- Word automation
- ActiveX
- Docx
title: Jak uložit docx a vložit ActiveX tlačítko pomocí C#
url: /cs/net/working-with-oleobjects-and-activex/how-to-save-docx-and-insert-an-activex-button-with-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak uložit docx a vložit ActiveX tlačítko pomocí C#

Pokud potřebujete programově vytvořit dokument Word a poté uložit docx s interaktivním tlačítkem, tento průvodce vám ukáže, jak na to. Naučíte se vložit ActiveX ovládací prvek, přidat ActiveX tlačítko a uložit výsledný .docx soubor pomocí C# a knihovny Aspose.Words.

Tutoriál pokrývá každý krok potřebný k **create word document programmatically**, vložení **command button** a uložení souboru na disk. Předchozí zkušenost s COM objekty není vyžadována, ale měli byste mít základní znalosti C# a nainstalovaný Visual Studio.

## Předpoklady

* .NET 6.0 SDK nebo novější  
* Visual Studio 2022 (nebo jakékoli C# IDE)  
* Aspose.Words for .NET NuGet balíček (`Install-Package Aspose.Words`)  
* Porozumění struktuře projektu C#  

Tyto položky zajišťují, že kód se zkompiluje a spustí bez další konfigurace.

## Krok 1: Nastavení nového C# konzolového projektu

Vytvořte konzolovou aplikaci, která bude hostovat logiku automatizace Wordu.

```bash
dotnet new console -n WordActiveXDemo
cd WordActiveXDemo
dotnet add package Aspose.Words
```

Výše uvedený příkaz vytvoří složku s názvem **WordActiveXDemo**, přidá referenci na Aspose.Words a připraví projekt ke kompilaci.

## Krok 2: Programové vytvoření Word dokumentu

Otevřete vygenerovaný soubor `Program.cs` a přidejte požadované `using` direktivy.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;   // not used directly but required for some overloads
```

Nyní vytvořte instanci prázdného objektu `Document`. Tento objekt představuje celý Word soubor v paměti.

```csharp
// Step 2: Create a new blank document
Document document = new Document();
```

`Document` třída je vstupním bodem pro všechny operace zpracování Wordu. V tomto okamžiku dokument neobsahuje žádné stránky, ale Aspose.Words automaticky vytvoří výchozí sekci, když přidáte obsah.

## Krok 3: Vložení ActiveX ovládacího prvku – přidání activex tlačítka

Objekt **Forms2OleControl** vám umožní vložit ActiveX ovládací prvek do odstavce Wordu. Následující kód vloží **CommandButton** s šířkou 150 pt a výškou 30 pt.

```csharp
// Step 3: Initialize a DocumentBuilder to edit the document
DocumentBuilder builder = new DocumentBuilder(document);

// Insert an ActiveX CommandButton control with the desired size
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    Forms2OleControlType.CommandButton, 150, 30);
```

`InsertForms2OleControl` vytvoří ovládací prvek a vrátí silně typovanou instanci `Forms2OleControl`, kterou můžete dále konfigurovat. Metoda automaticky přidá nový odstavec pro hostování ovládacího prvku, takže nemusíte ručně spravovat objekty odstavců.

## Krok 4: Konfigurace tlačítka příkazu – jak přidat vlastnosti tlačítka příkazu

Nastavte vlastnosti **Name** a **Caption** tlačítka, aby bylo rozpoznatelné za běhu a uživatelsky přívětivé v UI.

```csharp
// Step 4: Set the control's name and caption
commandButton.Name = "cmdSubmit";
commandButton.Caption = "Submit";
```

Atribut `Name` je užitečný, když později budete zpracovávat událost kliknutí tlačítka pomocí VBA nebo Word makra. `Caption` je text, který koncový uživatel vidí na povrchu tlačítka.

### Pro tip
Pokud plánujete automatizovat zpracování kliknutí z C#, vložte VBA makro, které odkazuje na `cmdSubmit`. Word při otevření dokumentu vyzve uživatele k povolení maker, což je standardní bezpečnostní chování pro ActiveX ovládací prvky.

## Krok 5: Jak uložit docx

Po umístění ovládacího prvku uložte dokument do souboru .docx. Metoda `Save` automaticky vybere vhodný formát na základě přípony souboru.

```csharp
// Step 5: Save the document containing the CommandButton
string outputPath = @"C:\Temp\CommandButton.docx";
document.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

Uložení souboru dokončuje workflow **how to save docx**. Výsledný soubor lze otevřít v Microsoft Word, kde se na první stránce objeví ActiveX tlačítko. Po kliknutí na tlačítko Word zobrazí zástupnou zprávu, pokud není připojeno makro.

## Krok 6: Spuštění programu a ověření výsledku

Zkompilujte a spusťte konzolovou aplikaci:

```bash
dotnet run
```

Po dokončení programu otevřete `C:\Temp\CommandButton.docx` v Microsoft Word:

* Dokument obsahuje jednu stránku s tlačítkem **Submit** poblíž horní části.  
* Přechod myší nad tlačítkem zobrazí tooltip s názvem `cmdSubmit`.  
* Žádný obsah není ztracen a velikost souboru je srovnatelná se standardním prázdným .docx.

Pokud se tlačítko nezobrazí, ověřte, že:

1. Nastavení **Trust Center** ve Wordu povolují ActiveX ovládací prvky.  
2. Soubor byl uložen s příponou `.docx` (ne `.doc`).  

## Okrajové případy a běžné varianty

| Situace | Doporučené úpravy |
|-----------|------------------------|
| Potřebujete jinou velikost tlačítka | Změňte argumenty šířky a výšky v `InsertForms2OleControl`. |
| Chcete tlačítko na konkrétní stránce | Použijte `builder.MoveToDocumentEnd();` po přidání stránek, nebo vložte zalomení stránky před ovládací prvek. |
| Musíte podporovat prostředí bez Aspose.Words | Použijte Open XML SDK k vložení elementu `w:object`, ale kód se stane podstatně složitějším. |
| Je vyžadován dokument s povolenými makry | Uložte s příponou `.docm` (`document.Save("MyDoc.docm");`) a vložte VBA modul, který zpracovává `cmdSubmit_Click`. |

## Kompletní zdrojový kód

Níže je kompletní, samostatný program, který můžete zkopírovat do `Program.cs` a spustit bez úprav (kromě výstupní cesty).

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace WordActiveXDemo
{
    class Program
    {
        static void Main()
        {
            // Create a new blank document
            Document document = new Document();

            // Initialize a DocumentBuilder to edit the document
            DocumentBuilder builder = new DocumentBuilder(document);

            // Insert an ActiveX CommandButton control with the desired size
            Forms2OleControl commandButton = builder.InsertForms2OleControl(
                Forms2OleControlType.CommandButton, 150, 30);

            // Set the control's name and caption
            commandButton.Name = "cmdSubmit";
            commandButton.Caption = "Submit";

            // Save the document containing the CommandButton
            string outputPath = @"C:\Temp\CommandButton.docx";
            document.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

### Očekávaný výstup v konzoli

```
Document saved to C:\Temp\CommandButton.docx
```

Otevření souboru ve Wordu zobrazí tlačítko označené **Submit**. Kliknutí na tlačítko spustí výchozí chování ActiveX (dialogové okno s informací, že není připojeno žádné makro).

## Závěr

Tento tutoriál ukázal **how to save docx** při vkládání **ActiveX control**, konkrétně **add activex button**, který funguje jako tlačítko příkazu. Nyní víte, jak **create word document programmatically**, nakonfigurovat vlastnosti tlačítka a uložit soubor pro interakci koncového uživatele.

Odtud můžete dále zkoumat:

* Přidání VBA maker pro zpracování `cmdSubmit_Click`.  
* Vkládání dalších ActiveX ovládacích prvků, jako jsou zaškrtávací políčka nebo rozbalovací seznamy.  
* Generování vícestránkových dokumentů s více interaktivními prvky.  

Experimentujte s různými typy ovládacích prvků a možnostmi rozvržení, abyste vytvořili bohaté, interaktivní Word šablony, které zjednoduší vaše obchodní procesy.

## Co byste se měli naučit dál?

Následující tutoriály pokrývají úzce související témata, která staví na technikách předvedených v tomto průvodci. Každý zdroj obsahuje kompletní funkční příklady kódu s podrobnými vysvětleními, které vám pomohou zvládnout další funkce API a prozkoumat alternativní přístupy k implementaci ve vašich projektech.

- [Aspose.Words – Save docx as txt and Export Word Equations as LaTeX – Complete Guide](/words/english/net/basic-conversions/save-docx-as-txt-complete-guide-to-export-word-equations-as/)
- [how to recover docx – C# guide for corrupted Word files](/words/english/net/programming-with-loadoptions/how-to-recover-docx-c-guide-for-corrupted-word-files/)
- [How to Save Word as Markdown – Complete C# Guide](/words/english/net/programming-with-markdownsaveoptions/how-to-save-word-as-markdown-complete-c-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}