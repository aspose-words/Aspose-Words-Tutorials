---
"description": "Naučte se, jak uzamknout poměr stran tvarů v dokumentech Wordu pomocí Aspose.Words pro .NET. Postupujte podle tohoto podrobného návodu, abyste zachovali proporce obrázků a tvarů."
"linktitle": "Poměr stran uzamčen"
"second_title": "Rozhraní API pro zpracování dokumentů Aspose.Words"
"title": "Poměr stran uzamčen"
"url": "/cs/net/programming-with-shapes/aspect-ratio-locked/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Poměr stran uzamčen

## Zavedení

Přemýšleli jste někdy, jak zachovat perfektní proporce obrázků a tvarů ve vašich dokumentech Word? Někdy potřebujete zajistit, aby se vaše obrázky a tvary při změně velikosti nezkreslily. A právě zde se hodí uzamčení poměru stran. V tomto tutoriálu se podíváme na to, jak nastavit poměr stran tvarů v dokumentech Word pomocí Aspose.Words pro .NET. Rozdělíme to do snadno sledovatelných kroků, abyste tyto dovednosti mohli s jistotou aplikovat ve svých projektech.

## Předpoklady

Než se pustíme do kódu, pojďme si projít, co k začátku potřebujete:

- Knihovna Aspose.Words pro .NET: Musíte mít nainstalovanou Aspose.Words pro .NET. Pokud ji ještě nemáte, můžete [stáhněte si to zde](https://releases.aspose.com/words/net/).
- Vývojové prostředí: Ujistěte se, že máte nastavené vývojové prostředí .NET. Visual Studio je oblíbenou volbou.
- Základní znalost C#: Určitá znalost programování v C# bude užitečná.

## Importovat jmenné prostory

Nejdříve si importujme potřebné jmenné prostory. Tyto jmenné prostory nám poskytnou přístup ke třídám a metodám, které potřebujeme pro práci s dokumenty a tvary aplikace Word.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
```

## Krok 1: Nastavení adresáře dokumentů

Než začneme manipulovat s tvary, musíme si nastavit adresář, kam budou naše dokumenty uloženy. Pro jednoduchost použijeme zástupný symbol. `YOUR DOCUMENT DIRECTORY`Nahraďte to skutečnou cestou k adresáři s dokumenty.

```csharp
// Cesta k adresáři s dokumenty
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## Krok 2: Vytvořte nový dokument

Dále vytvoříme nový dokument Wordu pomocí Aspose.Words. Tento dokument bude sloužit jako plátno pro přidávání tvarů a obrázků.

```csharp
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

Zde vytvoříme instanci `Document` třídu a použijte `DocumentBuilder` aby nám pomohly sestavit obsah dokumentu.

## Krok 3: Vložení obrázku

Nyní vložíme do našeho dokumentu obrázek. Použijeme `InsertImage` metoda `DocumentBuilder` třída. Ujistěte se, že máte v zadaném adresáři obrázek.

```csharp
Shape shape = builder.InsertImage(dataDir + "Transparent background logo.png");
```

Nahradit `dataDir + "Transparent background logo.png"` s cestou k souboru s obrázkem.

## Krok 4: Zamkněte poměr stran

Jakmile je obrázek vložen, můžeme jeho poměr stran uzamknout. Uzamčení poměru stran zajistí, že proporce obrázku zůstanou při změně velikosti konstantní.

```csharp
shape.AspectRatioLocked = true;
```

Prostředí `AspectRatioLocked` na `true` zajišťuje, že si obrázek zachová původní poměr stran.

## Krok 5: Uložte dokument

Nakonec dokument uložíme do zadaného adresáře. V tomto kroku se zapíší všechny provedené změny v souboru dokumentu.

```csharp
doc.Save(dataDir + "WorkingWithShapes.AspectRatioLocked.docx");
```

## Závěr

Gratulujeme! Úspěšně jste se naučili, jak nastavit poměr stran tvarů v dokumentech Word pomocí Aspose.Words pro .NET. Dodržováním těchto kroků zajistíte, že si vaše obrázky a tvary zachovají své proporce, a vaše dokumenty tak budou vypadat profesionálně a elegantně. Nebojte se experimentovat s různými obrázky a tvary a zjistit, jak funkce uzamčení poměru stran funguje v různých scénářích.

## Často kladené otázky

### Mohu po uzamčení poměr stran odemknout?
Ano, poměr stran můžete odemknout nastavením `shape.AspectRatioLocked = false`.

### Co se stane, když změním velikost obrázku s uzamčeným poměrem stran?
Velikost obrázku se proporcionálně změní a zachová se původní poměr šířky a výšky.

### Mohu to použít i na jiné tvary než obrázky?
Rozhodně! Funkci uzamčení poměru stran lze použít na jakýkoli tvar, včetně obdélníků, kruhů a dalších.

### Je Aspose.Words pro .NET kompatibilní s .NET Core?
Ano, Aspose.Words pro .NET podporuje .NET Framework i .NET Core.

### Kde najdu další dokumentaci k Aspose.Words pro .NET?
Najdete zde komplexní dokumentaci [zde](https://reference.aspose.com/words/net/).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}