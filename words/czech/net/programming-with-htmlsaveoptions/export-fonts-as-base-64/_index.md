---
title: Exportovat písma jako základ 64
linktitle: Exportovat písma jako základ 64
second_title: Aspose.Words API pro zpracování dokumentů
description: V tomto podrobném kurzu se dozvíte, jak exportovat písma jako Base64 pomocí Aspose.Words for .NET. Ujistěte se, že jsou písma vložena a správně zobrazena v souborech HTML.
weight: 10
url: /cs/net/programming-with-htmlsaveoptions/export-fonts-as-base-64/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Exportovat písma jako základ 64

## Zavedení

Pokud jde o programovou manipulaci s dokumenty Wordu, Aspose.Words for .NET je velmoc. Jednou z jeho šikovných funkcí je export písem jako Base64 do souborů HTML, což zajišťuje, že písma jsou vložena a správně zobrazena v různých prohlížečích a systémech. V tomto tutoriálu se ponoříme do toho, jak toho můžete dosáhnout. Jste připraveni upravit písma dokumentů aplikace Word na web? Začněme!

## Předpoklady

Než se pustíme do kódování, ujistěte se, že máte vše, co potřebujete:

-  Aspose.Words for .NET Library: Můžete si ji stáhnout z[Aspose Releases](https://releases.aspose.com/words/net/) strana.
- Vývojové prostředí .NET: Jakékoli IDE jako Visual Studio bude fungovat perfektně.
- Základní znalost C#: Nemusíte být profík, ale základní znalost vám pomůže.

## Importovat jmenné prostory

Chcete-li používat Aspose.Words pro .NET, budete muset do kódu C# importovat potřebné jmenné prostory. Tím jsou k dispozici všechny třídy a metody.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

## Krok 1: Nastavte svůj projekt

Za prvé, pojďme nastavit váš projekt a nainstalovat knihovnu Aspose.Words.

### 1.1 Vytvořte nový projekt

Otevřete Visual Studio a vytvořte nový projekt Console App. Pojmenujte to nějak smysluplně jako „ExportFontsBase64“.

### 1.2 Instalace Aspose.Words

Aspose.Words for .NET můžete nainstalovat přes NuGet Package Manager:

1. Klepněte pravým tlačítkem myši na svůj projekt v Průzkumníku řešení.
2. Vyberte „Spravovat balíčky NuGet“.
3. Vyhledejte "Aspose.Words" a nainstalujte jej.

Případně můžete spustit následující příkaz v konzole Správce balíčků:

```sh
Install-Package Aspose.Words
```

## Krok 2: Načtěte dokument aplikace Word

Nyní, když je váš projekt nastaven, načteme dokument aplikace Word, ze kterého chcete exportovat písma.

### 2.1 Definujte adresář dokumentů

Nejprve definujte adresář, kde se nachází váš dokument aplikace Word:

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

 Nahradit`"YOUR DOCUMENT DIRECTORY"` se skutečnou cestou k vašemu adresáři dokumentů.

### 2.2 Vložte dokument

 Dále načtěte dokument pomocí`Document` třída:

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

Ujistěte se, že "Rendering.docx" je ve vašem určeném adresáři.

## Krok 3: Nakonfigurujte možnosti uložení HTML

 Chcete-li exportovat písma jako Base64, musíme nakonfigurovat`HtmlSaveOptions`.


 Vytvořte instanci`HtmlSaveOptions` a nastavte`ExportFontsAsBase64`majetek do`true`:

```csharp
HtmlSaveOptions saveOptions = new HtmlSaveOptions { ExportFontsAsBase64 = true };
```

## Krok 4: Uložte dokument jako HTML

Nakonec uložíme dokument s nakonfigurovanými možnostmi.


 Použijte`Save` metoda`Document` třídy pro uložení dokumentu:

```csharp
doc.Save(dataDir + "WorkingWithHtmlSaveOptions.ExportFontsAsBase64.html", saveOptions);
```

Tento řádek uloží váš dokument jako soubor HTML s fonty exportovanými jako Base64, což zajistí, že budou vloženy do HTML.

## Závěr

Gratuluji! Úspěšně jste exportovali písma jako Base64 z dokumentu aplikace Word pomocí Aspose.Words for .NET. Tím zajistíte, že vaše písma budou zachována a správně zobrazena na různých platformách. Ať už připravujete dokumenty pro zobrazení na webu nebo jednoduše zajišťujete kompatibilitu, tato funkce je neuvěřitelně užitečná.

## FAQ

### Co je kódování Base64?
Base64 je metoda kódování binárních dat (jako jsou fonty) do textového formátu. To zajišťuje kompatibilitu s textovými formáty, jako je HTML.

### Proč bych měl používat Base64 pro písma v HTML?
Použití Base64 zajišťuje, že písma jsou vkládána přímo do HTML, čímž se vyhnete problémům s chybějícími soubory písem a zajistíte konzistentní zobrazení.

### Mohu tuto metodu použít pro jiné zdroje, jako jsou obrázky?
Absolutně! Aspose.Words for .NET vám umožňuje vkládat různé zdroje, včetně obrázků, jako Base64 do vašich HTML souborů.

### Co když můj dokument obsahuje více písem?
Žádný problém! Aspose.Words for .NET vloží všechna písma použitá ve vašem dokumentu jako Base64 do výsledného souboru HTML.

### Je Aspose.Words for .NET zdarma k použití?
 Aspose.Words for .NET je komerční knihovna. Můžete si však stáhnout bezplatnou zkušební verzi z[Aspose Releases](https://releases.aspose.com/) strana.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
