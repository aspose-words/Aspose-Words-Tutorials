---
title: Pro odsazení seznamu použijte znak tabulátoru na úroveň
linktitle: Pro odsazení seznamu použijte znak tabulátoru na úroveň
second_title: Aspose.Words API pro zpracování dokumentů
description: Naučte se vytvářet víceúrovňové seznamy s odsazením s kartami pomocí Aspose.Words for .NET. Postupujte podle tohoto průvodce pro přesné formátování seznamu ve vašich dokumentech.
weight: 10
url: /cs/net/programming-with-txtsaveoptions/use-tab-character-per-level-for-list-indentation/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Pro odsazení seznamu použijte znak tabulátoru na úroveň

## Zavedení

Seznamy jsou zásadní při organizování obsahu, ať už připravujete zprávu, píšete výzkumnou práci nebo připravujete prezentaci. Pokud však jde o prezentaci seznamů s více úrovněmi odsazení, může být dosažení požadovaného formátu trochu složité. Pomocí Aspose.Words for .NET můžete snadno spravovat odsazení seznamu a přizpůsobit, jak je každá úroveň zastoupena. V tomto tutoriálu se zaměříme na vytvoření seznamu s více úrovněmi odsazení s použitím znaků tabulátoru pro přesné formátování. Na konci této příručky budete mít jasno v tom, jak nastavit a uložit dokument se správným stylem odsazení.

## Předpoklady

Než se pustíme do kroků, ujistěte se, že máte připraveno následující:

1.  Instalováno Aspose.Words for .NET: Potřebujete knihovnu Aspose.Words. Pokud jste jej ještě nenainstalovali, můžete si jej stáhnout z[Aspose ke stažení](https://releases.aspose.com/words/net/).

2. Základní porozumění C# a .NET: Pro sledování tohoto kurzu je nezbytná znalost programování v C# a .NET frameworku.

3. Vývojové prostředí: Ujistěte se, že máte IDE nebo textový editor pro psaní a spouštění kódu C# (např. Visual Studio).

4. Vzorový adresář dokumentů: Nastavte adresář, do kterého budete dokument ukládat a testovat. 

## Importovat jmenné prostory

Nejprve musíte importovat potřebné jmenné prostory, abyste mohli používat Aspose.Words ve vaší aplikaci .NET. Přidejte následující pomocí direktiv na začátek souboru C#:

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

V této části vytvoříme víceúrovňový seznam s odsazením s kartami pomocí Aspose.Words for .NET. Postupujte takto:

## Krok 1: Nastavte svůj dokument

Vytvořte nový dokument a DocumentBuilder

```csharp
// Cesta k adresáři vašich dokumentů
string dataDir = "YOUR DOCUMENT DIRECTORY";

// Vytvořte nový dokument
Document doc = new Document();

// Inicializujte DocumentBuilder
DocumentBuilder builder = new DocumentBuilder(doc);
```

 Zde jsme založili nový`Document` objekt a a`DocumentBuilder` začít vytvářet obsah v dokumentu.

## Krok 2: Použijte výchozí formátování seznamu

Vytvořte a naformátujte seznam

```csharp
// Použít výchozí styl číslování na seznam
builder.ListFormat.ApplyNumberDefault();
```

V tomto kroku použijeme na náš seznam výchozí formát číslování. To nám pomůže při vytváření číslovaného seznamu, který pak můžeme upravit.

## Krok 3: Přidejte položky seznamu s různými úrovněmi

Vložit položky seznamu a odsadit

```csharp
//Přidejte první položku seznamu
builder.Write("Element 1");

// Odsazením vytvoříte druhou úroveň
builder.ListFormat.ListIndent();
builder.Write("Element 2");

// Dalším odsazením vytvoříte třetí úroveň
builder.ListFormat.ListIndent();
builder.Write("Element 3");
```

 Zde do našeho seznamu přidáváme tři prvky, každý s rostoucí úrovní odsazení. The`ListIndent` metoda se používá ke zvýšení úrovně odsazení pro každou následující položku.

## Krok 4: Nakonfigurujte možnosti uložení

Nastavte Odsazení na Použít znaky tabulátoru

```csharp
// Nakonfigurujte možnosti uložení tak, aby byly k odsazení použity znaky tabulátoru
TxtSaveOptions saveOptions = new TxtSaveOptions();
saveOptions.ListIndentation.Count = 1;
saveOptions.ListIndentation.Character = '\t';
```

 Nakonfigurujeme`TxtSaveOptions` pro použití tabulátorů pro odsazení v uloženém textovém souboru. The`ListIndentation.Character` vlastnost je nastavena na`'\t'`, což představuje znak tabulátoru.

## Krok 5: Uložte dokument

Uložte dokument se zadanými možnostmi

```csharp
// Uložte dokument se zadanými možnostmi
doc.Save(dataDir + "WorkingWithTxtSaveOptions.UseTabCharacterPerLevelForListIndentation.txt", saveOptions);
```

 Nakonec dokument uložíme pomocí`Save` metodou s naším zvykem`TxtSaveOptions`. Tím je zajištěno, že se seznam uloží se znaky tabulátoru pro úrovně odsazení.

## Závěr

tomto tutoriálu jsme prošli vytvořením víceúrovňového seznamu s odsazením pomocí karet pomocí Aspose.Words pro .NET. Pomocí těchto kroků můžete snadno spravovat a formátovat seznamy v dokumentech a zajistit, aby byly prezentovány jasně a profesionálně. Ať už pracujete na sestavách, prezentacích nebo jakémkoli jiném typu dokumentu, tyto techniky vám pomohou dosáhnout přesné kontroly nad formátováním seznamu.

## FAQ

### Jak mohu změnit znak odsazení z tabulátoru na mezeru?
 Můžete upravit`saveOptions.ListIndentation.Character` vlastnost použít znak mezery místo tabulátoru.

### Mohu použít různé styly seznamů na různé úrovně?
Ano, Aspose.Words umožňuje přizpůsobení stylů seznamů na různých úrovních. Chcete-li dosáhnout různých stylů, můžete upravit možnosti formátování seznamu.

### Co když potřebuji použít odrážky místo čísel?
 Použijte`ListFormat.ApplyBulletDefault()` metoda místo toho`ApplyNumberDefault()` k vytvoření seznamu s odrážkami.

### Jak mohu upravit velikost znaku tabulátoru použitého pro odsazení?
 Bohužel velikost karty v`TxtSaveOptions`je pevná. Chcete-li upravit velikost odsazení, možná budete muset použít mezery nebo přímo přizpůsobit formátování seznamu.

### Mohu tato nastavení použít při exportu do jiných formátů, jako je PDF nebo DOCX?
Konkrétní nastavení znaků tabulátoru platí pro textové soubory. U formátů jako PDF nebo DOCX budete muset upravit možnosti formátování v rámci těchto formátů.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
