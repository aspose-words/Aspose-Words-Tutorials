---
"description": "Naučte se, jak nastavit záložní písma v Aspose.Words pro .NET. Tato komplexní příručka zajistí, že se všechny znaky ve vašich dokumentech zobrazí správně."
"linktitle": "Nastavení záložního písma"
"second_title": "Rozhraní API pro zpracování dokumentů Aspose.Words"
"title": "Nastavení záložního písma"
"url": "/cs/net/working-with-fonts/set-font-fallback-settings/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Nastavení záložního písma

## Zavedení

Při práci s dokumenty, které obsahují rozmanité textové prvky, jako jsou různé jazyky nebo speciální znaky, je zásadní zajistit, aby se tyto prvky zobrazovaly správně. Aspose.Words pro .NET nabízí výkonnou funkci s názvem Nastavení záložního písma, která pomáhá definovat pravidla pro nahrazování písem, když původní písmo určité znaky nepodporuje. V této příručce se v podrobném návodu podíváme na to, jak nastavit záložní písmo pomocí Aspose.Words pro .NET.

## Předpoklady

Než se pustíte do tutoriálu, ujistěte se, že máte splněny následující předpoklady:

- Základní znalost C#: Znalost programovacího jazyka C# a frameworku .NET.
- Aspose.Words pro .NET: Stáhněte a nainstalujte z [odkaz ke stažení](https://releases.aspose.com/words/net/).
- Vývojové prostředí: Nastavení, jako je Visual Studio, pro psaní a spouštění kódu.
- Vzorový dokument: Mějte k dispozici vzorový dokument (např. `Rendering.docx`) připraveno k testování.
- Pravidla pro záložní písma v XML: Připravte soubor XML definující pravidla pro záložní písma.

## Importovat jmenné prostory

Pro použití Aspose.Words je nutné importovat potřebné jmenné prostory. To umožňuje přístup k různým třídám a metodám potřebným pro zpracování dokumentů.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;
using System;
```

## Krok 1: Definování adresáře dokumentů

Nejprve definujte adresář, kde je váš dokument uložen. To je nezbytné pro nalezení a zpracování dokumentu.

```csharp
// Cesta k adresáři s dokumenty
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## Krok 2: Vložení dokumentu

Vložte dokument do Aspose.Words `Document` objekt. Tento krok vám umožňuje pracovat s dokumentem programově.

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

## Krok 3: Konfigurace nastavení písma

Vytvořit nový `FontSettings` objekt a načíst nastavení záložního písma ze souboru XML. Tento soubor XML obsahuje pravidla pro záložní písma.

```csharp
FontSettings fontSettings = new FontSettings();
fontSettings.FallbackSettings.Load(dataDir + "Font fallback rules.xml");
```

## Krok 4: Použití nastavení písma v dokumentu

Přiřaďte nakonfigurované `FontSettings` do dokumentu. Tím se zajistí, že se při vykreslování dokumentu použijí pravidla pro záložní písma.

```csharp
doc.FontSettings = fontSettings;
```

## Krok 5: Uložte dokument

Nakonec dokument uložte. Nastavení záložního písma bude použito během operace ukládání, aby se zajistila správná náhrada písma.

```csharp
doc.Save(dataDir + "WorkingWithFonts.SetFontFallbackSettings.pdf");
```

## Soubor XML: Pravidla pro záložní písma

Zde je příklad, jak by měl vypadat váš XML soubor definující pravidla pro záložní písma:

```xml
<?xml version="1.0" encoding="UTF-8" standalone="yes"?>
<FontFallbackSettings xmlns="Aspose.Words">
    <FallbackTable>
        <Rule Ranges="0B80-0BFF" FallbackFonts="Vijaya"/>
        <Rule Ranges="1F300-1F64F" FallbackFonts="Segoe UI Emoji, Segoe UI Symbol"/>
        <Rule Ranges="2000-206F, 2070-209F, 20B9" FallbackFonts="Arial" />
        <Rule Ranges="3040-309F" FallbackFonts="MS Gothic" BaseFonts="Times New Roman"/>
        <Rule Ranges="3040-309F" FallbackFonts="MS Mincho"/>
        <Rule FallbackFonts="Arial Unicode MS"/>
    </FallbackTable>
</FontFallbackSettings>
```

## Závěr

Dodržováním těchto kroků můžete efektivně nastavit a používat záložní nastavení písma v Aspose.Words pro .NET. Tím zajistíte, že se ve vašich dokumentech budou všechny znaky zobrazovat správně, i když původní písmo určité znaky nepodporuje. Implementace těchto nastavení výrazně zlepší kvalitu a čitelnost vašich dokumentů.

## Často kladené otázky

### Q1: Co je záložní písmo?

Funkce Font Font Fallback umožňuje nahrazení písem, pokud původní písmo nepodporuje určité znaky, a zajišťuje tak správné zobrazení všech textových prvků.

### Q2: Mohu zadat více záložních písem?

Ano, v pravidlech XML můžete zadat více záložních fontů. Aspose.Words bude kontrolovat každý font v zadaném pořadí, dokud nenajde takový, který daný znak podporuje.

### Q3: Kde si mohu stáhnout Aspose.Words pro .NET?

Můžete si ho stáhnout z [Stránka ke stažení Aspose](https://releases.aspose.com/words/net/).

### Q4: Jak vytvořím soubor XML pro pravidla pro záložní písma?

Soubor XML lze vytvořit pomocí libovolného textového editoru. Měl by mít strukturu uvedenou v příkladu v tomto tutoriálu.

### Q5: Je k dispozici podpora pro Aspose.Words?

Ano, podporu můžete najít na [Fórum podpory Aspose.Words](https://forum.aspose.com/c/words/8).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}