---
"description": "Naučte se, jak do dokumentů Wordu přidat tvar se zkrácenými rohy pomocí nástroje Aspose.Words pro .NET. Tento podrobný návod vám zajistí, že své dokumenty snadno vylepšíte."
"linktitle": "Přidat zkrácené rohy"
"second_title": "Rozhraní API pro zpracování dokumentů Aspose.Words"
"title": "Přidat zkrácené rohy"
"url": "/cs/net/programming-with-shapes/add-corners-snipped/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Přidat zkrácené rohy

## Zavedení

Přidávání vlastních tvarů do dokumentů Wordu může být zábavným a vizuálně atraktivním způsobem, jak zvýraznit důležité informace nebo dodat obsahu trochu šmrncu. V tomto tutoriálu se ponoříme do toho, jak můžete do dokumentů Wordu vkládat tvary „Corners Snipped“ (zkrácené rohy) pomocí Aspose.Words pro .NET. Tato příručka vás provede každým krokem a zajistí, že tyto tvary budete moci bez námahy přidávat a upravovat dokumenty jako profesionál.

## Předpoklady

Než se pustíme do kódu, ujistěte se, že máte vše, co potřebujete k zahájení:

1. Aspose.Words pro .NET: Pokud jste tak ještě neučinili, stáhněte si nejnovější verzi z [Stránka s vydáním Aspose](https://releases.aspose.com/words/net/).
2. Vývojové prostředí: Nastavte si vývojové prostředí. Visual Studio je oblíbenou volbou, ale můžete použít jakékoli IDE, které podporuje .NET.
3. Licence: Pokud jen experimentujete, můžete použít [bezplatná zkušební verze](https://releases.aspose.com/) nebo si pořiďte [dočasná licence](https://purchase.aspose.com/temporary-license/) pro odemknutí plné funkčnosti.
4. Základní znalost C#: Znalost programování v C# vám pomůže sledovat příklady.

## Importovat jmenné prostory

Než začneme pracovat s Aspose.Words pro .NET, musíme importovat potřebné jmenné prostory. Přidejte je na začátek vašeho C# souboru:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
```

Nyní si rozeberme proces přidání tvaru „Rohy zkrácené“ do několika kroků. Pečlivě dodržujte tyto kroky, abyste zajistili, že vše bude fungovat hladce.

## Krok 1: Inicializace dokumentu a nástroje DocumentBuilder

První věc, kterou musíme udělat, je vytvořit nový dokument a inicializovat jej. `DocumentBuilder` objekt. Tento nástroj pro tvorbu nám pomůže přidat obsah do našeho dokumentu.

```csharp
// Cesta k adresáři s dokumenty
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

V tomto kroku jsme nastavili náš dokument a nástroj pro tvorbu. Zamyslete se nad `DocumentBuilder` jako vaše digitální pero, připravené k psaní a kreslení v dokumentu Word.

## Krok 2: Vložení tvaru zkrácených rohů

Dále použijeme `DocumentBuilder` vložit tvar „Zkrácené rohy“. Tento typ tvaru je předdefinovaný v Aspose.Words a lze jej snadno vložit jediným řádkem kódu.

```csharp
builder.InsertShape(ShapeType.TopCornersSnipped, 50, 50);
```

Zde určujeme typ tvaru a jeho rozměry (50x50). Představte si, že na dokument umisťujete malou samolepku s dokonale oříznutým rohem. 

## Krok 3: Definování možností ukládání s ohledem na dodržování předpisů

Před uložením dokumentu musíme definovat možnosti ukládání, abychom zajistili, že náš dokument splňuje specifické standardy. Použijeme `OoxmlSaveOptions` třída pro toto.

```csharp
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions(SaveFormat.Docx)
{
    Compliance = OoxmlCompliance.Iso29500_2008_Transitional
};
```

Tyto možnosti ukládání zajišťují, že náš dokument splňuje normu ISO/IEC 29500:2008, což je klíčové pro kompatibilitu a dlouhou životnost dokumentu.

## Krok 4: Uložte dokument

Nakonec uložíme náš dokument do zadaného adresáře pomocí voleb ukládání, které jsme definovali dříve.

```csharp
doc.Save(dataDir + "WorkingWithShapes.AddCornersSnipped.docx", saveOptions);
```

A váš dokument nyní obsahuje vlastní tvar „Zkrácené rohy“, uložený s potřebnými možnostmi dodržování předpisů.

## Závěr

A máte to! Přidávání vlastních tvarů do dokumentů Wordu pomocí Aspose.Words pro .NET je jednoduché a může výrazně vylepšit vizuální atraktivitu vašich dokumentů. Dodržováním těchto kroků můžete snadno vložit tvar „Zkrácené rohy“ a zajistit, aby váš dokument splňoval požadované standardy. Přeji vám příjemné programování!

## Často kladené otázky

### Mohu si přizpůsobit velikost tvaru „Zkrácené rohy“?
Ano, velikost můžete upravit změnou rozměrů v `InsertShape` metoda.

### Je možné přidat i jiné typy tvarů?
Rozhodně! Aspose.Words podporuje různé tvary. Stačí změnit `ShapeType` do vámi požadovaného tvaru.

### Potřebuji licenci k používání Aspose.Words?
I když můžete použít bezplatnou zkušební verzi nebo dočasnou licenci, pro neomezené používání je vyžadována plná licence.

### Jak mohu dále upravovat tvary?
Vzhled a chování tvarů můžete přizpůsobit pomocí dalších vlastností a metod poskytovaných Aspose.Words.

### Je Aspose.Words kompatibilní s jinými formáty?
Ano, Aspose.Words podporuje více formátů dokumentů včetně DOCX, PDF, HTML a dalších.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}