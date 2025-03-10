---
title: Export Cid URL pro zdroje Mhtml
linktitle: Export Cid URL pro zdroje Mhtml
second_title: Aspose.Words API pro zpracování dokumentů
description: V tomto podrobném kurzu se dozvíte, jak exportovat adresy URL Cid pro zdroje MHTML pomocí Aspose.Words for .NET. Ideální pro vývojáře všech úrovní.
weight: 10
url: /cs/net/programming-with-htmlsaveoptions/export-cid-urls-for-mhtml-resources/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Export Cid URL pro zdroje Mhtml

## Zavedení

Jste připraveni zvládnout umění exportu Cid URL pro zdroje MHTML pomocí Aspose.Words pro .NET? Ať už jste zkušený vývojář nebo teprve začínáte, tento komplexní průvodce vás provede každým krokem. Na konci tohoto článku budete mít křišťálově jasnou představu o tom, jak efektivně zacházet s prostředky MHTML v dokumentech aplikace Word. Pojďme se ponořit!

## Předpoklady

Než začneme, ujistěte se, že máte vše, co potřebujete:

-  Aspose.Words for .NET: Ujistěte se, že máte nainstalovanou nejnovější verzi Aspose.Words pro .NET. Pokud ne, můžete si jej stáhnout z[zde](https://releases.aspose.com/words/net/).
- Vývojové prostředí: Vývojové prostředí, jako je Visual Studio.
- Základní znalost C#: I když vás provedu každým krokem, základní znalost C# bude prospěšná.

## Importovat jmenné prostory

Nejprve importujme potřebné jmenné prostory. Tento krok připraví půdu pro náš tutoriál:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;
```

Nyní si tento proces rozdělíme do jednoduchých, zvládnutelných kroků. Každý krok bude obsahovat podrobné vysvětlení, abyste mohli bez námahy pokračovat.

## Krok 1: Nastavení vašeho projektu

### Krok 1.1: Vytvořte nový projekt
Otevřete Visual Studio a vytvořte nový projekt C#. Chcete-li, aby byly věci jednoduché, vyberte šablonu aplikace konzoly.

### Krok 1.2: Přidejte Aspose.Words pro .NET Reference
Chcete-li používat Aspose.Words pro .NET, musíte přidat odkaz na knihovnu Aspose.Words. Můžete to udělat pomocí Správce balíčků NuGet:

1. Klepněte pravým tlačítkem myši na svůj projekt v Průzkumníku řešení.
2. Vyberte „Spravovat balíčky NuGet“.
3. Vyhledejte "Aspose.Words" a nainstalujte jej.

## Krok 2: Načtení dokumentu aplikace Word

### Krok 2.1: Zadejte adresář dokumentů
Definujte cestu k adresáři dokumentů. Zde se nachází váš dokument aplikace Word.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

 Nahradit`"YOUR DOCUMENT DIRECTORY"` se skutečnou cestou k vašemu adresáři.

### Krok 2.2: Vložte dokument
Načtěte dokument aplikace Word do projektu.

```csharp
Document doc = new Document(dataDir + "Content-ID.docx");
```

## Krok 3: Konfigurace možností uložení HTML

 Vytvořte instanci`HtmlSaveOptions` upravit, jak bude váš dokument uložen jako MHTML.

```csharp
HtmlSaveOptions saveOptions = new HtmlSaveOptions(SaveFormat.Mhtml)
{
    PrettyFormat = true,
    ExportCidUrlsForMhtmlResources = true
};
```

- `SaveFormat.Mhtml` určuje, že výstupní formát je MHTML.
- `PrettyFormat = true` zajišťuje, že výstup je úhledně naformátován.
- `ExportCidUrlsForMhtmlResources = true` umožňuje export Cid URL pro zdroje MHTML.

### Krok 4: Uložení dokumentu jako MHTML

Krok 4.1: Uložte dokument
Uložte dokument jako soubor MHTML pomocí nakonfigurovaných možností.

```csharp
doc.Save(dataDir + "WorkingWithHtmlSaveOptions.ExportCidUrlsForMhtmlResources.mhtml", saveOptions);
```

## Závěr

Gratuluji! Úspěšně jste exportovali adresy URL Cid pro zdroje MHTML pomocí Aspose.Words for .NET. Tento výukový program vás provede nastavením projektu, načtením dokumentu aplikace Word, konfigurací možností uložení HTML a uložením dokumentu jako MHTML. Nyní můžete tyto kroky použít na své vlastní projekty a vylepšit úkoly správy dokumentů.

## FAQ

### Jaký je účel exportu adres URL Cid pro zdroje MHTML?
Export Cid URL pro zdroje MHTML zajistí, že vložené zdroje ve vašem souboru MHTML budou správně odkazovány, což zlepší přenositelnost a integritu dokumentu.

### Mohu si výstupní formát dále přizpůsobit?
 Ano, Aspose.Words for .NET nabízí rozsáhlé možnosti přizpůsobení pro ukládání dokumentů. Viz[dokumentace](https://reference.aspose.com/words/net/) pro více podrobností.

### Potřebuji licenci k používání Aspose.Words pro .NET?
 Ano, k používání Aspose.Words pro .NET potřebujete licenci. Můžete získat bezplatnou zkušební verzi[zde](https://releases.aspose.com/) nebo zakoupit licenci[zde](https://purchase.aspose.com/buy).

### Mohu tento proces automatizovat pro více dokumentů?
Absolutně! Můžete vytvořit skript pro automatizaci procesu pro více dokumentů s využitím síly Aspose.Words pro .NET pro efektivní zpracování dávkových operací.

### Kde mohu získat podporu, pokud narazím na problémy?
Pokud potřebujete podporu, navštivte fórum podpory Aspose[zde](https://forum.aspose.com/c/words/8) za pomoc od komunity a vývojářů Aspose.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
