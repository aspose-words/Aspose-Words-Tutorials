---
"description": "Naučte se v tomto průvodci, jak změnit zdroj kultury aktualizace polí v Aspose.Words pro .NET. Snadno ovládejte formátování data na základě různých kultur."
"linktitle": "Změnit zdroj kultury aktualizace pole"
"second_title": "Rozhraní API pro zpracování dokumentů Aspose.Words"
"title": "Změnit zdroj kultury aktualizace pole"
"url": "/cs/net/working-with-fields/change-field-update-culture-source/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Změnit zdroj kultury aktualizace pole

## Zavedení

V tomto tutoriálu se ponoříme do světa Aspose.Words pro .NET a prozkoumáme, jak změnit zdroj kultury aktualizace polí. Pokud pracujete s dokumenty Word, které obsahují pole s datem, a potřebujete ovládat formátování těchto dat na základě různých kultur, je tento průvodce určen právě vám. Pojďme si celý proces krok za krokem projít, abyste pochopili každý koncept a dokázali jej efektivně aplikovat ve svých projektech.

## Předpoklady

Než se pustíme do kódu, ujistěte se, že máte následující:

- Aspose.Words pro .NET: Můžete si jej stáhnout z [zde](https://releases.aspose.com/words/net/).
- Vývojové prostředí: Jakékoli IDE kompatibilní s .NET (např. Visual Studio).
- Základní znalost C#: Tento tutoriál předpokládá, že máte základní znalosti programování v C#.

## Importovat jmenné prostory

Nejprve si importujme potřebné jmenné prostory pro náš projekt. Tím zajistíme přístup ke všem požadovaným třídám a metodám poskytovaným Aspose.Words.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fields;
```

Nyní si rozdělme příklad do několika kroků, abyste pochopili, jak změnit zdroj kultury aktualizace pole v Aspose.Words pro .NET.

## Krok 1: Inicializace dokumentu

Prvním krokem je vytvoření nové instance `Document` třída a `DocumentBuilder`Tím se položí základ pro vytváření a manipulaci s naším dokumentem Wordu.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Krok 2: Vložení polí se specifickým národním prostředím

Dále musíme do dokumentu vložit pole. V tomto příkladu vložíme dvě pole s datem. Nastavíme národní prostředí písma na němčinu (LocaleId = 1031), abychom ukázali, jak kultura ovlivňuje formát data.

```csharp
builder.Font.LocaleId = 1031; // Němec
builder.InsertField("MERGEFIELD Date1 \\@ \"dddd, d MMMM yyyy\"");
builder.Write(" - ");
builder.InsertField("MERGEFIELD Date2 \\@ \"dddd, d MMMM yyyy\"");
```

## Krok 3: Nastavení zdroje kultury aktualizace pole

Pro řízení kultury použité při aktualizaci polí nastavíme `FieldUpdateCultureSource` majetek `FieldOptions` třída. Tato vlastnost určuje, zda je kultura převzata z kódu pole nebo z dokumentu.

```csharp
doc.FieldOptions.FieldUpdateCultureSource = FieldUpdateCultureSource.FieldCode;
```

## Krok 4: Spuštění hromadné korespondence

Nyní musíme spustit hromadnou korespondenci, abychom naplnili pole skutečnými daty. V tomto příkladu nastavíme druhé pole s datem (`Date2`) do 1. ledna 2011.

```csharp
doc.MailMerge.Execute(new string[] { "Date2" }, new object[] { new DateTime(2011, 1, 1) });
```

## Krok 5: Uložte dokument

Nakonec dokument uložíme do zadaného adresáře. Tímto krokem dokončíme proces změny zdroje kultury aktualizace pole.

```csharp
doc.Save(dataDir + "WorkingWithFields.ChangeFieldUpdateCultureSource.docx");
```

## Závěr

je to! Úspěšně jste změnili zdroj kultury aktualizace polí v Aspose.Words pro .NET. Dodržením těchto kroků zajistíte, že vaše dokumenty Word zobrazují data a další hodnoty polí podle zadaného nastavení kultury. To může být obzvláště užitečné při generování dokumentů pro mezinárodní publikum.

## Často kladené otázky

### Jaký je účel nastavení `LocaleId`?
Ten/Ta/To `LocaleId` určuje nastavení kultury pro text, což ovlivňuje formátování dat a dalších dat citlivých na národní prostředí.

### Mohu použít jiné národní prostředí než němčinu?
Ano, můžete nastavit `LocaleId` na jakýkoli platný identifikátor národního prostředí. Například 1033 pro angličtinu (Spojené státy).

### Co se stane, když nenastavím `FieldUpdateCultureSource` vlastnictví?
Pokud tato vlastnost není nastavena, při aktualizaci polí se použije výchozí nastavení kultury dokumentu.

### Je možné aktualizovat pole na základě kultury dokumentu místo kódu pole?
Ano, můžete nastavit `FieldUpdateCultureSource` na `FieldUpdateCultureSource.Document` použít nastavení kultury dokumentu.

### Jak formátuji data v jiném vzoru?
Vzor formátu data můžete změnit v `InsertField` metodu úpravou `\\@` hodnota přepínače.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}