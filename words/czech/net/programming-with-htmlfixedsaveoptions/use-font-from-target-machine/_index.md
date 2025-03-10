---
title: Použít písmo z cílového stroje
linktitle: Použít písmo z cílového stroje
second_title: Aspose.Words API pro zpracování dokumentů
description: Naučte se používat písma z cílového počítače v dokumentech aplikace Word pomocí Aspose.Words for .NET. Postupujte podle našeho podrobného průvodce pro bezproblémovou integraci písem.
weight: 10
url: /cs/net/programming-with-htmlfixedsaveoptions/use-font-from-target-machine/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Použít písmo z cílového stroje

## Zavedení

Jste připraveni ponořit se do fascinujícího světa Aspose.Words pro .NET? Připoutejte se, protože se vás chystáme vzít na cestu magickou říší písem. Dnes se zaměříme na to, jak používat písma z cílového počítače při práci s dokumenty aplikace Word. Tato šikovná funkce zajišťuje, že váš dokument bude vypadat přesně tak, jak zamýšlíte, bez ohledu na to, kde je zobrazen. Začněme!

## Předpoklady

Než se pustíme do podrobností, ujistěte se, že máte vše, co potřebujete:

1.  Aspose.Words for .NET: Ujistěte se, že máte nainstalovanou knihovnu Aspose.Words for .NET. Pokud jste to ještě neudělali, můžete si ji stáhnout[zde](https://releases.aspose.com/words/net/).
2. Vývojové prostředí: Měli byste mít nastavené vývojové prostředí .NET, jako je Visual Studio.
3. Dokument, se kterým budete pracovat: Připravte si dokument aplikace Word k testování. Budeme používat dokument s názvem "Odrážky s alternativním fontem.docx".

Nyní, když jsme probrali základy, pojďme se ponořit do kódu!

## Importovat jmenné prostory

Nejprve musíme importovat potřebné jmenné prostory. Toto je páteř našeho projektu, spojující všechny body.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;
```

## Krok 1: Načtěte dokument aplikace Word

 Prvním krokem v našem tutoriálu je načtení dokumentu aplikace Word. Tady to všechno začíná. Použijeme`Document` třídy z knihovny Aspose.Words, abyste toho dosáhli.

### Krok 1.1: Definujte cestu dokumentu

Začněme definováním cesty k adresáři dokumentů. Zde se nachází váš dokument aplikace Word.

```csharp
// Cesta k adresáři vašich dokumentů
string dataDir = "YOUR DOCUMENTS DIRECTORY";
```

### Krok 1.2: Vložte dokument

 Nyní načteme dokument pomocí`Document` třída.

```csharp
// Načtěte dokument aplikace Word
Document doc = new Document(dataDir + "Bullet points with alternative font.docx");
```

## Krok 2: Nakonfigurujte možnosti uložení

Dále musíme nakonfigurovat možnosti ukládání. Tento krok je zásadní, protože zajišťuje, že písma použitá ve vašem dokumentu jsou písma z cílového počítače.

 Vytvoříme instanci`HtmlFixedSaveOptions` a nastavte`UseTargetMachineFonts`majetek do`true`.

```csharp
// Nakonfigurujte možnosti zálohování pomocí funkce „Použít písma z cílového počítače“.
HtmlFixedSaveOptions saveOptions = new HtmlFixedSaveOptions
{
    UseTargetMachineFonts = true
};
```

## Krok 3: Uložte dokument

Nakonec dokument uložíme jako pevný HTML soubor. Tady se děje kouzlo!

 Použijeme`Save` způsob uložení dokumentu s nakonfigurovanými možnostmi uložení.

```csharp
// Převést dokument do pevného HTML
doc.Save(dataDir + "WorkingWithHtmlFixedSaveOptions.UseFontFromTargetMachine.html", saveOptions);
```

## Krok 4: Ověřte výstup

neposlední řadě je vždy dobré výstup ověřit. Otevřete uložený soubor HTML a zkontrolujte, zda jsou písma správně použita z cílového počítače.

Přejděte do adresáře, do kterého jste uložili soubor HTML, a otevřete jej ve webovém prohlížeči.

```csharp
// Ověřte výstup otevřením souboru HTML
System.Diagnostics.Process.Start(dataDir + "WorkingWithHtmlFixedSaveOptions.UseFontFromTargetMachine.html");
```

A tady to máte! Úspěšně jste použili písma z cílového počítače v dokumentu aplikace Word pomocí Aspose.Words for .NET.

## Závěr

Použití písem z cílového počítače zajišťuje, že vaše dokumenty aplikace Word budou vypadat konzistentně a profesionálně, bez ohledu na to, kde jsou zobrazeny. Aspose.Words for .NET činí tento proces přímočarým a efektivním. Podle tohoto kurzu jste se naučili, jak načíst dokument, nakonfigurovat možnosti uložení a uložit dokument s požadovaným nastavením písma. Šťastné kódování!

## FAQ

### Mohu tuto metodu použít s jinými formáty dokumentů?
Ano, Aspose.Words for .NET podporuje různé formáty dokumentů a můžete nakonfigurovat podobné možnosti ukládání pro různé formáty.

### Co když cílový počítač nemá požadovaná písma?
Pokud cílový počítač nemá požadovaná písma, dokument se nemusí vykreslit podle očekávání. V případě potřeby je vždy dobré vkládat písma.

### Jak vložím písma do dokumentu?
 Vkládání písem lze provést pomocí`FontSettings` třídy v Aspose.Words pro .NET. Viz[dokumentace](https://reference.aspose.com/words/net/) pro více podrobností.

### Existuje způsob, jak zobrazit náhled dokumentu před uložením?
 Ano, můžete použít`DocumentRenderer` třídy pro zobrazení náhledu dokumentu před uložením. Podívejte se na Aspose.Words pro .NET[dokumentace](https://reference.aspose.com/words/net/) pro více informací.

### Mohu dále upravit výstup HTML?
 Absolutně! The`HtmlFixedSaveOptions` class poskytuje různé vlastnosti pro přizpůsobení výstupu HTML. Prozkoumat[dokumentace](https://reference.aspose.com/words/net/) pro všechny dostupné možnosti.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
