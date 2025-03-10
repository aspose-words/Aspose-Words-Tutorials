---
title: Nastavte záložní nastavení písma
linktitle: Nastavte záložní nastavení písma
second_title: Aspose.Words API pro zpracování dokumentů
description: Přečtěte si, jak nastavit záložní nastavení písem v Aspose.Words pro .NET. Tento komplexní průvodce zajišťuje správné zobrazení všech znaků ve vašich dokumentech.
weight: 10
url: /cs/net/working-with-fonts/set-font-fallback-settings/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Nastavte záložní nastavení písma

## Zavedení

Při práci s dokumenty, které obsahují různé textové prvky, jako jsou různé jazyky nebo speciální znaky, je zásadní zajistit, aby se tyto prvky zobrazovaly správně. Aspose.Words for .NET nabízí výkonnou funkci nazvanou Font Fallback Settings, která pomáhá při definování pravidel pro nahrazování písem, když původní písmo nepodporuje určité znaky. V této příručce prozkoumáme, jak nastavit nastavení zálohování písem pomocí Aspose.Words pro .NET v podrobném tutoriálu.

## Předpoklady

Než se pustíte do výukového programu, ujistěte se, že máte splněny následující předpoklady:

- Základní znalost C#: Znalost programovacího jazyka C# a .NET frameworku.
-  Aspose.Words for .NET: Stáhněte a nainstalujte z[odkaz ke stažení](https://releases.aspose.com/words/net/).
- Vývojové prostředí: Nastavení jako Visual Studio pro psaní a spouštění kódu.
-  Vzorový dokument: Mějte vzorový dokument (např.`Rendering.docx`) připraven k testování.
- Pravidla pro záložní písma XML: Připravte soubor XML definující pravidla pro záložní písma.

## Importovat jmenné prostory

Chcete-li používat Aspose.Words, musíte importovat potřebné jmenné prostory. To umožňuje přístup k různým třídám a metodám potřebným pro zpracování dokumentů.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;
using System;
```

## Krok 1: Definujte adresář dokumentů

Nejprve definujte adresář, kde je dokument uložen. To je nezbytné pro vyhledání a zpracování vašeho dokumentu.

```csharp
// Cesta k adresáři dokumentů
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## Krok 2: Vložte dokument

 Vložte dokument do Aspose.Words`Document` objekt. Tento krok vám umožní pracovat s dokumentem programově.

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

## Krok 3: Nakonfigurujte nastavení písma

 Vytvořte nový`FontSettings` objekt a načtěte záložní nastavení písma ze souboru XML. Tento soubor XML obsahuje pravidla pro záložní písmo.

```csharp
FontSettings fontSettings = new FontSettings();
fontSettings.FallbackSettings.Load(dataDir + "Font fallback rules.xml");
```

## Krok 4: Použijte nastavení písma na dokument

 Přiřadit nakonfigurované`FontSettings` dokumentu. Tím je zajištěno, že se při vykreslování dokumentu použijí záložní pravidla pro písmo.

```csharp
doc.FontSettings = fontSettings;
```

## Krok 5: Uložte dokument

Nakonec dokument uložte. Záložní nastavení písem bude použito během operace ukládání, aby byla zajištěna správná náhrada písem.

```csharp
doc.Save(dataDir + "WorkingWithFonts.SetFontFallbackSettings.pdf");
```

## Soubor XML: Pravidla zálohování písem

Zde je příklad toho, jak by měl vypadat váš soubor XML definující pravidla pro záložní písma:

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

Pomocí následujících kroků můžete efektivně nastavit a používat nastavení Font Fallback v Aspose.Words for .NET. Tím zajistíte, že vaše dokumenty zobrazí všechny znaky správně, i když původní písmo určité znaky nepodporuje. Implementace těchto nastavení výrazně zvýší kvalitu a čitelnost vašich dokumentů.

## FAQ

### Q1: Co je to zálohování písem?

Font Fallback je funkce, která umožňuje nahrazování písem, když původní písmo nepodporuje určité znaky, a zajišťuje správné zobrazení všech textových prvků.

### Q2: Mohu zadat více záložních písem?

Ano, v pravidlech XML můžete zadat více záložních písem. Aspose.Words bude kontrolovat každé písmo v zadaném pořadí, dokud nenajde takové, které daný znak podporuje.

### Q3: Kde si mohu stáhnout Aspose.Words pro .NET?

 Můžete si jej stáhnout z[Aspose stránku ke stažení](https://releases.aspose.com/words/net/).

### Otázka 4: Jak vytvořím soubor XML pro pravidla záložních písem?

Soubor XML lze vytvořit pomocí libovolného textového editoru. Mělo by se řídit strukturou uvedenou v příkladu v tomto tutoriálu.

### Q5: Je k dispozici podpora pro Aspose.Words?

 Ano, podporu najdete na[Fórum podpory Aspose.Words](https://forum.aspose.com/c/words/8).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
