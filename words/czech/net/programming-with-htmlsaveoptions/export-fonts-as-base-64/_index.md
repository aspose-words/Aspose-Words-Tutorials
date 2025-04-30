---
"description": "V tomto podrobném návodu se naučte, jak exportovat fonty ve formátu Base64 pomocí Aspose.Words pro .NET. Zajistěte, aby byly fonty vloženy a správně zobrazeny v souborech HTML."
"linktitle": "Exportovat fonty jako Base 64"
"second_title": "Rozhraní API pro zpracování dokumentů Aspose.Words"
"title": "Exportovat fonty jako Base 64"
"url": "/cs/net/programming-with-htmlsaveoptions/export-fonts-as-base-64/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Exportovat fonty jako Base 64

## Zavedení

Pokud jde o programovou manipulaci s dokumenty Wordu, Aspose.Words pro .NET je skvělou volbou. Jednou z jeho šikovných funkcí je export písem ve formátu Base64 v rámci souborů HTML, což zajišťuje, že jsou písma vložena a správně zobrazena v různých prohlížečích a systémech. V tomto tutoriálu se ponoříme do toho, jak toho dosáhnout. Jste připraveni upravit písma ve vašich dokumentech Word pro web? Pojďme na to!

## Předpoklady

Než se pustíme do kódování, ujistěte se, že máte vše, co potřebujete:

- Knihovna Aspose.Words pro .NET: Můžete si ji stáhnout z [Aspose Releases](https://releases.aspose.com/words/net/) strana.
- Vývojové prostředí .NET: Jakékoli IDE, jako je Visual Studio, bude fungovat perfektně.
- Základní znalost C#: Nemusíte být profesionál, ale základní znalost vám pomůže.

## Importovat jmenné prostory

Chcete-li používat Aspose.Words pro .NET, budete muset importovat potřebné jmenné prostory do kódu C#. Tím se zpřístupní všechny třídy a metody pro použití.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

## Krok 1: Nastavení projektu

Nejdříve si nastavíme váš projekt a nainstalujeme knihovnu Aspose.Words.

### 1.1 Vytvoření nového projektu

Otevřete Visual Studio a vytvořte nový projekt konzolové aplikace. Pojmenujte ho nějak smysluplně, například „ExportFontsBase64“.

### 1.2 Instalace Aspose.Words

Aspose.Words pro .NET můžete nainstalovat pomocí Správce balíčků NuGet:

1. Klikněte pravým tlačítkem myši na svůj projekt v Průzkumníku řešení.
2. Vyberte možnost „Spravovat balíčky NuGet“.
3. Vyhledejte „Aspose.Words“ a nainstalujte jej.

Případně můžete v konzoli Správce balíčků spustit následující příkaz:

```sh
Install-Package Aspose.Words
```

## Krok 2: Načtěte dokument aplikace Word

Nyní, když je váš projekt nastavený, načtěme dokument Wordu, ze kterého chcete exportovat písma.

### 2.1 Definování adresáře dokumentů

Nejprve definujte adresář, kde se nachází váš dokument Wordu:

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

Nahradit `"YOUR DOCUMENT DIRECTORY"` se skutečnou cestou k adresáři dokumentů.

### 2.2 Vložení dokumentu

Dále vložte dokument pomocí `Document` třída:

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

Ujistěte se, že soubor „Rendering.docx“ se nachází ve vámi zadaném adresáři.

## Krok 3: Konfigurace možností ukládání HTML

Pro export fontů jako Base64 je potřeba nakonfigurovat `HtmlSaveOptions`.


Vytvořte instanci `HtmlSaveOptions` a nastavte `ExportFontsAsBase64` majetek `true`:

```csharp
HtmlSaveOptions saveOptions = new HtmlSaveOptions { ExportFontsAsBase64 = true };
```

## Krok 4: Uložte dokument jako HTML

Nakonec uložte dokument s nakonfigurovanými možnostmi.


Použijte `Save` metoda `Document` třída pro uložení dokumentu:

```csharp
doc.Save(dataDir + "WorkingWithHtmlSaveOptions.ExportFontsAsBase64.html", saveOptions);
```

Tento řádek uloží váš dokument jako soubor HTML s fonty exportovanými ve formátu Base64, čímž zajistí, že budou vloženy do HTML.

## Závěr

Gratulujeme! Úspěšně jste exportovali písma ve formátu Base64 z dokumentu Word pomocí nástroje Aspose.Words pro .NET. Tím je zajištěno, že se vaše písma zachovají a zobrazí správně na různých platformách. Ať už připravujete dokumenty pro zobrazení na webu, nebo jednoduše zajišťujete kompatibilitu, tato funkce je neuvěřitelně užitečná.

## Často kladené otázky

### Co je kódování Base64?
Base64 je metoda kódování binárních dat (například písem) do textového formátu. To zajišťuje kompatibilitu s textovými formáty, jako je HTML.

### Proč bych měl/a používat Base64 pro fonty v HTML?
Použití Base64 zajišťuje, že fonty jsou vloženy přímo do HTML, čímž se předejde problémům s chybějícími soubory fontů a zajistí se konzistentní zobrazení.

### Mohu tuto metodu použít i pro jiné zdroje, jako jsou obrázky?
Rozhodně! Aspose.Words pro .NET umožňuje vkládat různé zdroje, včetně obrázků, ve formátu Base64 do vašich HTML souborů.

### Co když můj dokument obsahuje více písem?
Žádný problém! Aspose.Words pro .NET vloží všechna písma použitá ve vašem dokumentu jako Base64 do výsledného HTML souboru.

### Je Aspose.Words pro .NET zdarma k použití?
Aspose.Words pro .NET je komerční knihovna. Můžete si však stáhnout bezplatnou zkušební verzi z [Aspose Releases](https://releases.aspose.com/) strana.



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}