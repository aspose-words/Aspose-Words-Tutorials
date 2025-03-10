---
title: Pro odsazení seznamu použijte mezeru na úroveň
linktitle: Pro odsazení seznamu použijte mezeru na úroveň
second_title: Aspose.Words API pro zpracování dokumentů
description: Zjistěte, jak v Aspose.Words for .NET vytvářet víceúrovňové seznamy s odsazením znaků mezery. Podrobný průvodce pro přesné formátování dokumentu.
weight: 10
url: /cs/net/programming-with-txtsaveoptions/use-space-character-per-level-for-list-indentation/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Pro odsazení seznamu použijte mezeru na úroveň

## Zavedení

Pokud jde o formátování dokumentů, zejména při práci se seznamy, je klíčová přesnost. Ve scénářích, kdy potřebujete vytvořit dokumenty s různými úrovněmi odsazení, nabízí Aspose.Words for .NET výkonné nástroje pro zvládnutí tohoto úkolu. Jedna konkrétní funkce, která se může hodit, je konfigurace odsazení seznamu v textových souborech. Tato příručka vás provede tím, jak používat mezery k odsazení seznamu, aby si dokument zachová požadovanou strukturu a čitelnost.

## Předpoklady

Než se pustíte do výukového programu, budete potřebovat následující:

-  Aspose.Words for .NET: Ujistěte se, že máte nainstalovanou knihovnu Aspose.Words. Pokud jej ještě nemáte, můžete si jej stáhnout z[Aspose webové stránky](https://releases.aspose.com/words/net/).
- Visual Studio: Vývojové prostředí pro psaní a testování kódu.
- Základní porozumění C#: Znalost C# a .NET frameworku vám pomůže hladce pokračovat.

## Importovat jmenné prostory

Chcete-li začít pracovat s Aspose.Words, budete muset importovat potřebné jmenné prostory. Zde je návod, jak je můžete zahrnout do svého projektu:

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

Pojďme si rozebrat proces vytváření dokumentu s víceúrovňovým seznamem a určení mezer pro odsazení. 

## Krok 1: Nastavte svůj dokument

 Nejprve budete muset vytvořit nový dokument a inicializovat jej`DocumentBuilder` objekt. Tento objekt vám umožní snadno přidávat obsah a formátovat jej podle potřeby.

```csharp
// Cesta k vašemu adresáři dokumentů
string dataDir = "YOUR DOCUMENTS DIRECTORY";

// Vytvořte dokument a přidejte obsah
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

 V tomto úryvku nahraďte`"YOUR DOCUMENTS DIRECTORY"` se skutečnou cestou, kam chcete dokument uložit.

## Krok 2: Vytvořte seznam s více úrovněmi odsazení

 s`DocumentBuilder` instance, nyní můžete vytvořit seznam s různými úrovněmi odsazení. Použijte`ListFormat` vlastnost použít číslování a odsadit položky seznamu podle potřeby.

```csharp
// Vytvořte seznam se třemi úrovněmi odsazení
builder.ListFormat.ApplyNumberDefault();
builder.Write("Element 1");
builder.ListFormat.ListIndent();
builder.Write("Element 2");
builder.ListFormat.ListIndent();
builder.Write("Element 3");
```

 V tomto kroku`ApplyNumberDefault` nastaví formát seznamu a`ListIndent` se používá ke zvýšení úrovně odsazení pro každou následující položku seznamu.

## Krok 3: Konfigurace mezerového znaku pro odsazení

Nyní, když máte svůj seznam nastavený, je dalším krokem konfigurace, jak se bude pracovat s odsazením seznamu při ukládání dokumentu do textového souboru. Budete používat`TxtSaveOptions` určit, že pro odsazení mají být použity mezery.

```csharp
// Pro odsazení seznamu použijte jednu mezeru na úroveň
TxtSaveOptions saveOptions = new TxtSaveOptions();
saveOptions.ListIndentation.Count = 3;
saveOptions.ListIndentation.Character = ' ';
```

 Zde,`ListIndentation.Count` určuje počet mezer na úrovni odsazení a`ListIndentation.Character` nastaví skutečný znak použitý pro odsazení.

## Krok 4: Uložte dokument se zadanými možnostmi

Nakonec uložte dokument pomocí nakonfigurovaných možností. Tím se použije nastavení odsazení a soubor se uloží v požadovaném formátu.

```csharp
// Uložte dokument se zadanými možnostmi
doc.Save(dataDir + "WorkingWithTxtSaveOptions.UseSpaceCharacterPerLevelForListIndentation.txt", saveOptions);
```

 Tento fragment kódu uloží dokument do cesty zadané v`dataDir` s názvem souboru`"WorkingWithTxtSaveOptions.UseSpaceCharacterPerLevelForListIndentation.txt"`. Uložený soubor bude mít seznam formátovaný podle vašeho nastavení odsazení.

## Závěr

Pomocí těchto kroků jste úspěšně vytvořili dokument s víceúrovňovým odsazením seznamu pomocí mezer pro formátování. Tento přístup zajišťuje, že vaše seznamy jsou dobře strukturované a snadno čitelné, i když jsou uloženy jako textové soubory. Aspose.Words for .NET poskytuje robustní nástroje pro manipulaci s dokumenty a zvládnutí těchto funkcí může výrazně zlepšit vaše pracovní postupy zpracování dokumentů.

## FAQ

### Mohu pro odsazení seznamu kromě mezer použít jiné znaky?
 Ano, můžete zadat různé znaky pro odsazení seznamu nastavením`Character` majetek v`TxtSaveOptions`.

### Jak mohu v seznamech použít odrážky místo čísel?
 Použití`ListFormat.ApplyBulletDefault()` místo`ApplyNumberDefault()` k vytvoření seznamu s odrážkami.

### Mohu dynamicky upravit počet mezer pro odsazení?
 Ano, můžete upravit`ListIndentation.Count` vlastnost nastavit počet míst na základě vašich požadavků.

### Je možné po vytvoření dokumentu změnit odsazení seznamu?
Ano, před uložením dokumentu můžete kdykoli upravit formátování seznamu a nastavení odsazení.

### Jaké další formáty dokumentů podporují nastavení odsazení seznamu?
Kromě textových souborů lze nastavení odsazení seznamu použít i na jiné formáty, jako je DOCX, PDF a HTML, když používáte Aspose.Words.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
