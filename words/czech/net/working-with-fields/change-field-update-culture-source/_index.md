---
title: Změnit pole Aktualizovat zdroj kultury
linktitle: Změnit pole Aktualizovat zdroj kultury
second_title: Aspose.Words API pro zpracování dokumentů
description: V této příručce se dozvíte, jak změnit zdroj kultury aktualizace pole v Aspose.Words pro .NET. Snadno ovládejte formátování data na základě různých kultur.
weight: 10
url: /cs/net/working-with-fields/change-field-update-culture-source/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Změnit pole Aktualizovat zdroj kultury

## Zavedení

V tomto tutoriálu se ponoříme do světa Aspose.Words pro .NET a prozkoumáme, jak změnit zdroj kultury aktualizace pole. Pokud máte co do činění s dokumenty Wordu, které obsahují pole data, a potřebujete ovládat, jak jsou tato data formátována na základě různých kultur, je tato příručka určena právě vám. Pojďme si projít procesem krok za krokem a ujistěte se, že pochopíte každý koncept a dokážete jej efektivně aplikovat ve svých projektech.

## Předpoklady

Než skočíme do kódu, ujistěte se, že máte následující:

-  Aspose.Words for .NET: Můžete si jej stáhnout z[zde](https://releases.aspose.com/words/net/).
- Vývojové prostředí: Jakékoli .NET kompatibilní IDE (např. Visual Studio).
- Základní znalost C#: Tento tutoriál předpokládá, že máte základní znalosti o programování v C#.

## Importovat jmenné prostory

Nejprve importujme potřebné jmenné prostory pro náš projekt. To zajistí, že budeme mít přístup ke všem požadovaným třídám a metodám poskytovaným Aspose.Words.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fields;
```

Nyní si tento příklad rozdělíme do několika kroků, které vám pomohou pochopit, jak změnit zdroj kultury aktualizace pole v Aspose.Words pro .NET.

## Krok 1: Inicializujte dokument

 Prvním krokem je vytvoření nové instance souboru`Document` třída a a`DocumentBuilder`. To vytváří základ pro vytváření a manipulaci s naším dokumentem Word.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Krok 2: Vložte pole se specifickým národním prostředím

Dále musíme do dokumentu vložit pole. V tomto příkladu vložíme dvě pole data. Nastavíme národní prostředí písma na němčinu (LocaleId = 1031), abychom ukázali, jak kultura ovlivňuje formát data.

```csharp
builder.Font.LocaleId = 1031; // Němec
builder.InsertField("MERGEFIELD Date1 \\@ \"dddd, d MMMM yyyy\"");
builder.Write(" - ");
builder.InsertField("MERGEFIELD Date2 \\@ \"dddd, d MMMM yyyy\"");
```

## Krok 3: Nastavte zdroj kultury aktualizace pole

 Pro kontrolu kultury používané při aktualizaci polí jsme nastavili`FieldUpdateCultureSource` vlastnictvím`FieldOptions`třída. Tato vlastnost určuje, zda je kultura převzata z kódu pole nebo dokumentu.

```csharp
doc.FieldOptions.FieldUpdateCultureSource = FieldUpdateCultureSource.FieldCode;
```

## Krok 4: Proveďte hromadnou korespondenci

Nyní musíme provést hromadnou korespondenci, abychom naplnili pole skutečnými daty. V tomto příkladu nastavíme druhé pole data (`Date2`) do 1. ledna 2011.

```csharp
doc.MailMerge.Execute(new string[] { "Date2" }, new object[] { new DateTime(2011, 1, 1) });
```

## Krok 5: Uložte dokument

Nakonec dokument uložíme do zadaného adresáře. Tento krok dokončí proces změny zdroje kultury aktualizace pole.

```csharp
doc.Save(dataDir + "WorkingWithFields.ChangeFieldUpdateCultureSource.docx");
```

## Závěr

A tady to máte! Úspěšně jste změnili zdroj kultury aktualizace pole v Aspose.Words pro .NET. Pomocí těchto kroků můžete zajistit, že vaše dokumenty Word zobrazí data a další hodnoty polí podle zadaného nastavení jazykové verze. To může být užitečné zejména při generování dokumentů pro mezinárodní publikum.

## FAQ

###  Jaký je účel nastavení`LocaleId`?
 The`LocaleId` určuje nastavení kultury pro text, které ovlivňuje, jak jsou formátována data a další data citlivá na národní prostředí.

### Mohu použít jiné národní prostředí než němčinu?
 Ano, můžete nastavit`LocaleId`na jakýkoli platný identifikátor národního prostředí. Například 1033 pro angličtinu (Spojené státy americké).

###  Co se stane, když nenastavím`FieldUpdateCultureSource` property?
Pokud tato vlastnost není nastavena, použije se při aktualizaci polí výchozí nastavení kultury dokumentu.

### Je možné aktualizovat pole na základě kultury dokumentu namísto kódu pole?
 Ano, můžete nastavit`FieldUpdateCultureSource` na`FieldUpdateCultureSource.Document` použít nastavení kultury dokumentu.

### Jak mohu formátovat data v jiném vzoru?
 Vzor formátu data můžete změnit v`InsertField` metodou úpravou`\\@` hodnotu spínače.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
