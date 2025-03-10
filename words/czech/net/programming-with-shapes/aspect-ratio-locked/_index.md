---
title: Poměr stran uzamčen
linktitle: Poměr stran uzamčen
second_title: Aspose.Words API pro zpracování dokumentů
description: Naučte se, jak uzamknout poměr stran tvarů v dokumentech aplikace Word pomocí Aspose.Words for .NET. Postupujte podle tohoto podrobného průvodce, aby byly obrázky a tvary proporcionální.
weight: 10
url: /cs/net/programming-with-shapes/aspect-ratio-locked/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Poměr stran uzamčen

## Zavedení

Přemýšleli jste někdy, jak zachovat dokonalé proporce obrázků a tvarů v dokumentech aplikace Word? Někdy je potřeba zajistit, aby se vaše obrázky a tvary při změně velikosti nezkreslily. Zde se hodí uzamčení poměru stran. V tomto tutoriálu prozkoumáme, jak nastavit poměr stran tvarů v dokumentech aplikace Word pomocí Aspose.Words for .NET. Rozdělíme to do snadno pochopitelných kroků, abychom zajistili, že tyto dovednosti můžete s důvěrou aplikovat na své projekty.

## Předpoklady

Než se ponoříme do kódu, pojďme si projít, co potřebujete, abyste mohli začít:

- Aspose.Words for .NET Library: Musíte mít nainstalovanou Aspose.Words for .NET. Pokud jste to ještě neudělali, můžete[stáhněte si to zde](https://releases.aspose.com/words/net/).
- Vývojové prostředí: Ujistěte se, že máte nastavené vývojové prostředí .NET. Visual Studio je oblíbenou volbou.
- Základní znalost C#: Určitá znalost programování v C# bude užitečná.

## Importovat jmenné prostory

Nejprve importujme potřebné jmenné prostory. Tyto jmenné prostory nám umožní přístup ke třídám a metodám, které potřebujeme pro práci s dokumenty a tvary aplikace Word.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
```

## Krok 1: Nastavte adresář dokumentů

 Než začneme s tvary manipulovat, musíme si nastavit adresář, kam se budou naše dokumenty ukládat. Pro jednoduchost použijeme zástupný symbol`YOUR DOCUMENT DIRECTORY`. Nahraďte to skutečnou cestou k adresáři dokumentů.

```csharp
// Cesta k vašemu adresáři dokumentů
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## Krok 2: Vytvořte nový dokument

Dále vytvoříme nový dokument Word pomocí Aspose.Words. Tento dokument bude sloužit jako naše plátno pro přidávání tvarů a obrázků.

```csharp
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

 Zde vytvoříme instanci`Document` třídy a použití a`DocumentBuilder` které nám pomohou vytvořit obsah dokumentu.

## Krok 3: Vložte obrázek

 Nyní vložíme obrázek do našeho dokumentu. Použijeme`InsertImage` metoda`DocumentBuilder`třída. Ujistěte se, že máte obrázek v zadaném adresáři.

```csharp
Shape shape = builder.InsertImage(dataDir + "Transparent background logo.png");
```

 Nahradit`dataDir + "Transparent background logo.png"` s cestou k souboru obrázku.

## Krok 4: Uzamkněte poměr stran

Jakmile je obrázek vložen, můžeme uzamknout jeho poměr stran. Uzamčení poměru stran zajišťuje, že proporce obrazu zůstanou při změně velikosti konstantní.

```csharp
shape.AspectRatioLocked = true;
```

 Nastavení`AspectRatioLocked` na`true` zajišťuje, že si obraz zachová svůj původní poměr stran.

## Krok 5: Uložte dokument

Nakonec dokument uložíme do zadaného adresáře. Tento krok zapíše všechny změny, které jsme provedli v souboru dokumentu.

```csharp
doc.Save(dataDir + "WorkingWithShapes.AspectRatioLocked.docx");
```

## Závěr

Gratuluji! Úspěšně jste se naučili, jak nastavit poměr stran tvarů v dokumentech aplikace Word pomocí Aspose.Words for .NET. Dodržením těchto kroků zajistíte, že si vaše obrázky a tvary zachovají své proporce a vaše dokumenty budou vypadat profesionálně a vyleštěně. Nebojte se experimentovat s různými obrázky a tvary, abyste viděli, jak funkce uzamčení poměru stran funguje v různých scénářích.

## FAQ

### Mohu po zamknutí odemknout poměr stran?
Ano, poměr stran můžete odemknout nastavením`shape.AspectRatioLocked = false`.

### Co se stane, když změním velikost obrázku se zamčeným poměrem stran?
Velikost obrázku se proporcionálně změní, přičemž se zachová původní poměr šířky k výšce.

### Mohu to použít na jiné tvary kromě obrázků?
Absolutně! Funkci uzamčení poměru stran lze použít na jakýkoli tvar, včetně obdélníků, kruhů a dalších.

### Je Aspose.Words for .NET kompatibilní s .NET Core?
Ano, Aspose.Words for .NET podporuje .NET Framework i .NET Core.

### Kde najdu další dokumentaci k Aspose.Words pro .NET?
 Můžete najít komplexní dokumentaci[zde](https://reference.aspose.com/words/net/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
