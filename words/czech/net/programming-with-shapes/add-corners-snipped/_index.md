---
title: Přidat rohy ustřižené
linktitle: Přidat rohy ustřižené
second_title: Aspose.Words API pro zpracování dokumentů
description: Naučte se, jak přidat tvar s odříznutými rohy do dokumentů aplikace Word pomocí Aspose.Words for .NET. Tento podrobný průvodce vám zajistí snadné vylepšení vašich dokumentů.
weight: 10
url: /cs/net/programming-with-shapes/add-corners-snipped/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Přidat rohy ustřižené

## Zavedení

Přidání vlastních tvarů do dokumentů aplikace Word může být zábavným a vizuálně přitažlivým způsobem, jak zvýraznit důležité informace nebo dodat svému obsahu trochu šmrncu. V tomto tutoriálu se ponoříme do toho, jak můžete vložit tvary „Vystřižené rohy“ do dokumentů aplikace Word pomocí Aspose.Words for .NET. Tato příručka vás provede každým krokem a zajistí, že můžete bez námahy přidávat tyto tvary a upravovat své dokumenty jako profesionál.

## Předpoklady

Než se pustíme do kódu, ujistěte se, že máte vše, co potřebujete, abyste mohli začít:

1.  Aspose.Words for .NET: Pokud jste tak ještě neučinili, stáhněte si nejnovější verzi z webu[Aspose stránku vydání](https://releases.aspose.com/words/net/).
2. Vývojové prostředí: Nastavte své vývojové prostředí. Visual Studio je oblíbená volba, ale můžete použít jakékoli IDE, které podporuje .NET.
3.  Licence: Pokud právě experimentujete, můžete použít a[zkušební verze zdarma](https://releases.aspose.com/) nebo získat a[dočasná licence](https://purchase.aspose.com/temporary-license/) pro odemknutí plné funkčnosti.
4. Základní porozumění C#: Znalost programování C# vám pomůže postupovat podle příkladů.

## Importovat jmenné prostory

Než začneme pracovat s Aspose.Words pro .NET, musíme naimportovat potřebné jmenné prostory. Přidejte je do horní části souboru C#:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
```

Nyní si rozdělme proces přidávání tvaru „Vystřižené rohy“ do několika kroků. Postupujte přesně podle těchto kroků, aby vše fungovalo hladce.

## Krok 1: Inicializujte Document a DocumentBuilder

 První věc, kterou musíme udělat, je vytvořit nový dokument a inicializovat a`DocumentBuilder` objekt. Tento stavitel nám pomůže přidat obsah do našeho dokumentu.

```csharp
// Cesta k vašemu adresáři dokumentů
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

 V tomto kroku jsme nastavili náš dokument a tvůrce. Myslete na`DocumentBuilder` jako vaše digitální pero, připravené k psaní a kreslení v dokumentu aplikace Word.

## Krok 2: Vložte tvar s odříznutými rohy

 Dále použijeme`DocumentBuilder` pro vložení tvaru "Uříznuté rohy". Tento typ tvaru je předdefinován v Aspose.Words a lze jej snadno vložit pomocí jediného řádku kódu.

```csharp
builder.InsertShape(ShapeType.TopCornersSnipped, 50, 50);
```

Zde specifikujeme typ tvaru a jeho rozměry (50x50). Představte si, že na dokument umístíte malý, dokonale ustřižený rohový štítek. 

## Krok 3: Definujte možnosti uložení s dodržováním předpisů

Před uložením našeho dokumentu musíme definovat možnosti uložení, abychom zajistili, že náš dokument vyhovuje konkrétním standardům. Použijeme`OoxmlSaveOptions` třídy za to.

```csharp
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions(SaveFormat.Docx)
{
    Compliance = OoxmlCompliance.Iso29500_2008_Transitional
};
```

Tyto možnosti uložení zajišťují, že náš dokument splňuje normu ISO/IEC 29500:2008, která je zásadní pro kompatibilitu a životnost dokumentu.

## Krok 4: Uložte dokument

Nakonec uložíme náš dokument do určeného adresáře pomocí možností uložení, které jsme definovali dříve.

```csharp
doc.Save(dataDir + "WorkingWithShapes.AddCornersSnipped.docx", saveOptions);
```

A stejně tak váš dokument nyní obsahuje vlastní tvar "Rohy Snipped" uložený s nezbytnými možnostmi souladu.

## Závěr

Tady to máš! Přidávání vlastních tvarů do dokumentů aplikace Word pomocí Aspose.Words for .NET je jednoduché a může výrazně zlepšit vizuální přitažlivost vašich dokumentů. Podle těchto kroků můžete snadno vložit tvar "Rohy Snipped" a zajistit, aby váš dokument splňoval požadované standardy. Šťastné kódování!

## FAQ

### Mohu přizpůsobit velikost tvaru „Uříznuté rohy“?
Ano, velikost můžete upravit změnou rozměrů v`InsertShape` metoda.

### Je možné přidat další typy tvarů?
 Absolutně! Aspose.Words podporuje různé tvary. Stačí změnit`ShapeType` do požadovaného tvaru.

### Potřebuji licenci k používání Aspose.Words?
I když můžete použít bezplatnou zkušební nebo dočasnou licenci, pro neomezené použití je vyžadována plná licence.

### Jak mohu tvary dále upravovat?
K přizpůsobení vzhledu a chování tvarů můžete použít další vlastnosti a metody poskytované Aspose.Words.

### Je Aspose.Words kompatibilní s jinými formáty?
Ano, Aspose.Words podporuje více formátů dokumentů včetně DOCX, PDF, HTML a dalších.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
