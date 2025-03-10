---
title: Vložit pole TOA bez Tvůrce dokumentů
linktitle: Vložit pole TOA bez Tvůrce dokumentů
second_title: Aspose.Words API pro zpracování dokumentů
description: Naučte se, jak vložit pole TOA bez použití nástroje pro tvorbu dokumentů v Aspose.Words pro .NET. Postupujte podle našeho podrobného průvodce pro efektivní správu právních citací.
weight: 10
url: /cs/net/working-with-fields/insert-toafield-without-document-builder/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Vložit pole TOA bez Tvůrce dokumentů

## Zavedení

Vytvoření pole tabulky oprávnění (TOA) v dokumentu aplikace Word může připadat jako poskládání složitého puzzle. S pomocí Aspose.Words pro .NET se však proces stává hladkým a přímočarým. V tomto článku vás provedeme kroky k vložení pole TOA bez použití nástroje pro tvorbu dokumentů, což vám usnadní správu citací a právních odkazů v dokumentech aplikace Word.

## Předpoklady

Než se pustíte do výukového programu, proberme si základy, které budete potřebovat:

-  Aspose.Words for .NET: Ujistěte se, že máte nainstalovanou nejnovější verzi. Můžete si jej stáhnout z[Aspose webové stránky](https://releases.aspose.com/words/net/).
- Vývojové prostředí: IDE kompatibilní s .NET jako Visual Studio.
- Základní znalosti C#: Porozumění základní syntaxi a konceptům C# bude užitečné.
- Vzorový dokument Word: Vytvořte nebo mějte připravený vzorový dokument, kam chcete vložit pole TOA.

## Importovat jmenné prostory

Chcete-li začít, budete muset importovat potřebné jmenné prostory z knihovny Aspose.Words. Toto nastavení zajišťuje, že máte přístup ke všem třídám a metodám potřebným pro manipulaci s dokumenty.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fields;
```

Pojďme si tento proces rozdělit do jednoduchých, snadno pochopitelných kroků. Provedeme vás každou fází a vysvětlíme, co každá část kódu dělá a jak přispívá k vytvoření pole TOA.

## Krok 1: Inicializujte dokument

 Nejprve musíte vytvořit instanci souboru`Document` třída. Tento objekt představuje dokument aplikace Word, na kterém pracujete.

```csharp
// Cesta k adresáři dokumentů.
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
```

Tento kód inicializuje nový dokument aplikace Word. Můžete si to představit jako vytvoření prázdného plátna, na které přidáte svůj obsah.

## Krok 2: Vytvořte a nakonfigurujte pole TA

Dále přidáme pole TA (Tabulka pravomocí). Toto pole označuje položky, které se objeví v TOA.

```csharp
Paragraph para = new Paragraph(doc);

// Chceme vložit pole TA a TOA takto:
// { TA \c 1 \l "Hodnota 0" }
FieldTA fieldTA = (FieldTA) para.AppendField(FieldType.FieldTOAEntry, false);
fieldTA.EntryCategory = "1";
fieldTA.LongCitation = "Value 0";

doc.FirstSection.Body.AppendChild(para);
```

Zde je rozpis:
- Odstavec para = nový Odstavec(doc);: Vytvoří nový odstavec v dokumentu.
-  FieldTA fieldTA = (FieldTA) para.AppendField(FieldType.FieldTOAEntry, false);: Přidá do odstavce pole TA. The`FieldType.FieldTOAEntry` určuje, že se jedná o vstupní pole TOA.
- fieldTA.EntryCategory = "1";: Nastaví kategorii záznamu. To je užitečné pro kategorizaci různých typů záznamů.
- fieldTA.LongCitation = "Value 0";: Určuje dlouhý text citace. Toto je text, který se objeví v TOA.
- doc.FirstSection.Body.AppendChild(para);: Připojí odstavec s polem TA k tělu dokumentu.

## Krok 3: Přidejte pole TOA

Nyní vložíme skutečné pole TOA, které zkompiluje všechny položky TA do tabulky.

```csharp
para = new Paragraph(doc);

FieldToa fieldToa = (FieldToa) para.AppendField(FieldType.FieldTOA, false);
fieldToa.EntryCategory = "1";
doc.FirstSection.Body.AppendChild(para);
```

V tomto kroku:
- FieldToa fieldToa = (FieldToa) para.AppendField(FieldType.FieldTOA, false);: Přidá do odstavce pole TOA.
- fieldToa.EntryCategory = "1";: Filtruje položky tak, aby zahrnovaly pouze položky označené kategorií "1".

## Krok 4: Aktualizujte pole TOA

Po vložení pole TOA je třeba jej aktualizovat, aby odpovídalo nejnovějším záznamům.

```csharp
fieldToa.Update();
```

Tento příkaz obnoví pole TOA a zajistí, že všechny označené položky jsou v tabulce správně zobrazeny.

## Krok 5: Uložte dokument

Nakonec uložte dokument s nově přidaným polem TOA.

```csharp
doc.Save(dataDir + "WorkingWithFields.InsertTOAFieldWithoutDocumentBuilder.docx");
```

 Tento řádek kódu uloží dokument do zadaného adresáře. Nezapomeňte vyměnit`"YOUR DOCUMENT DIRECTORY"` se skutečnou cestou, kam chcete soubor uložit.

## Závěr

A tady to máte! Úspěšně jste přidali pole TOA do dokumentu aplikace Word bez použití nástroje pro tvorbu dokumentů. Pomocí těchto kroků můžete efektivně spravovat citace a vytvářet komplexní tabulky oprávnění ve vašich právních dokumentech. Aspose.Words for .NET činí tento proces plynulým a efektivním a poskytuje vám nástroje pro snadné zpracování složitých dokumentů.

## FAQ

### Mohu přidat více polí TA s různými kategoriemi?
 Ano, můžete přidat více polí TA s různými kategoriemi nastavením`EntryCategory`majetek podle toho.

### Jak mohu přizpůsobit vzhled TOA?
Vzhled TOA můžete upravit úpravou vlastností pole TOA, jako je formátování položek a štítky kategorií.

### Je možné automaticky aktualizovat pole TOA?
 I když můžete ručně aktualizovat pole TOA pomocí`Update` Aspose.Words v současné době nepodporuje automatické aktualizace změn dokumentu.

### Mohu přidat pole TA programově do konkrétních částí dokumentu?
Ano, pole TA můžete přidat na konkrétní místa tak, že je vložíte do požadovaných odstavců nebo sekcí.

### Jak mohu zpracovat více polí TOA v jednom dokumentu?
 Můžete spravovat více polí TOA přiřazením různých`EntryCategory` hodnoty a zajistit, aby každé pole TOA filtruje položky na základě své kategorie.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
