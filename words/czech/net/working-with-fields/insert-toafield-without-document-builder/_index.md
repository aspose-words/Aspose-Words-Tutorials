---
"description": "Naučte se, jak vložit pole TOA bez použití nástroje pro tvorbu dokumentů v Aspose.Words pro .NET. Postupujte podle našeho podrobného návodu, jak efektivně spravovat citace právních textů."
"linktitle": "Vložit pole TOA bez nástroje pro tvorbu dokumentů"
"second_title": "Rozhraní API pro zpracování dokumentů Aspose.Words"
"title": "Vložit pole TOA bez nástroje pro tvorbu dokumentů"
"url": "/cs/net/working-with-fields/insert-toafield-without-document-builder/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Vložit pole TOA bez nástroje pro tvorbu dokumentů

## Zavedení

Vytvoření pole Tabulka zdrojů (TOA) v dokumentu Word se může zdát jako skládání složité skládačky. S pomocí Aspose.Words pro .NET se však celý proces stává hladkým a přímočarým. V tomto článku vás provedeme kroky pro vložení pole TOA bez použití nástroje pro tvorbu dokumentů, což vám usnadní správu citací a právních odkazů v dokumentech Word.

## Předpoklady

Než se pustíme do tutoriálu, pojďme si probrat základní informace, které budete potřebovat:

- Aspose.Words pro .NET: Ujistěte se, že máte nainstalovanou nejnovější verzi. Můžete si ji stáhnout z [Webové stránky Aspose](https://releases.aspose.com/words/net/).
- Vývojové prostředí: IDE kompatibilní s .NET, jako je Visual Studio.
- Základní znalost C#: Pochopení základní syntaxe a konceptů C# bude užitečné.
- Ukázkový dokument aplikace Word: Vytvořte nebo si připravte ukázkový dokument tam, kam chcete vložit pole TOA.

## Importovat jmenné prostory

Pro začátek budete muset importovat potřebné jmenné prostory z knihovny Aspose.Words. Toto nastavení vám zajistí přístup ke všem třídám a metodám potřebným pro manipulaci s dokumenty.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fields;
```

Rozdělme si celý proces na jednoduché a snadno sledovatelné kroky. Provedeme vás každou fází a vysvětlíme, co každý kus kódu dělá a jak přispívá k vytvoření pole TOA.

## Krok 1: Inicializace dokumentu

Nejprve je třeba vytvořit instanci `Document` třída. Tento objekt představuje dokument aplikace Word, na kterém pracujete.

```csharp
// Cesta k adresáři s dokumenty.
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
```

Tento kód inicializuje nový dokument aplikace Word. Můžete si to představit jako vytvoření prázdného plátna, na které budete přidávat svůj obsah.

## Krok 2: Vytvoření a konfigurace pole TA

Dále přidáme pole TA (Tabulka autorit). Toto pole označuje položky, které se objeví v TOA.

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
- Paragraph para = new Paragraph(doc);: Vytvoří nový odstavec v dokumentu.
- FieldTA fieldTA = (FieldTA) para.AppendField(FieldType.FieldTOAEntry, false);: Přidá do odstavce pole TA. The `FieldType.FieldTOAEntry` určuje, že se jedná o vstupní pole TOA.
- fieldTA.EntryCategory = "1";: Nastavuje kategorii položky. To je užitečné pro kategorizaci různých typů položek.
- fieldTA.LongCitation = "Hodnota 0";: Určuje dlouhý citační text. Toto je text, který se zobrazí v TOA.
- doc.FirstSection.Body.AppendChild(para);: Připojí odstavec s polem TA do těla dokumentu.

## Krok 3: Přidání pole TOA

Nyní vložíme skutečné pole TOA, které shrne všechny položky TA do tabulky.

```csharp
para = new Paragraph(doc);

FieldToa fieldToa = (FieldToa) para.AppendField(FieldType.FieldTOA, false);
fieldToa.EntryCategory = "1";
doc.FirstSection.Body.AppendChild(para);
```

V tomto kroku:
- FieldToa fieldToa = (FieldToa) para.AppendField(FieldType.FieldTOA, false);: Přidá do odstavce pole TOA.
- fieldToa.EntryCategory = "1";: Filtruje položky tak, aby zahrnovaly pouze ty označené kategorií "1".

## Krok 4: Aktualizace pole TOA

Po vložení pole TOA je nutné jej aktualizovat, aby odráželo nejnovější položky.

```csharp
fieldToa.Update();
```

Tento příkaz aktualizuje pole TOA a zajišťuje, že všechny označené položky jsou v tabulce správně zobrazeny.

## Krok 5: Uložte dokument

Nakonec uložte dokument s nově přidaným polem TOA.

```csharp
doc.Save(dataDir + "WorkingWithFields.InsertTOAFieldWithoutDocumentBuilder.docx");
```

Tento řádek kódu uloží dokument do zadaného adresáře. Nezapomeňte nahradit `"YOUR DOCUMENT DIRECTORY"` se skutečnou cestou, kam chcete soubor uložit.

## Závěr

A tady to máte! Úspěšně jste přidali pole TOA do dokumentu Word bez použití nástroje pro tvorbu dokumentů. Dodržováním těchto kroků můžete efektivně spravovat citace a vytvářet komplexní seznamy zdrojů ve svých právních dokumentech. Aspose.Words pro .NET tento proces usnadňuje a zefektivňuje a poskytuje vám nástroje pro snadné zvládání složitých úkolů s dokumenty.

## Často kladené otázky

### Mohu přidat více polí TA s různými kategoriemi?
Ano, můžete přidat více polí TA s různými kategoriemi nastavením `EntryCategory` majetek odpovídajícím způsobem.

### Jak si mohu přizpůsobit vzhled TOA?
Vzhled pole TOA si můžete přizpůsobit úpravou vlastností pole TOA, jako je formátování položek a popisky kategorií.

### Je možné automaticky aktualizovat pole TOA?
když můžete pole TOA aktualizovat ručně pomocí `Update` Metoda Aspose.Words v současné době nepodporuje automatické aktualizace změn v dokumentu.

### Mohu programově přidat pole TA do konkrétních částí dokumentu?
Ano, pole TA můžete přidat na konkrétní místa vložením do požadovaných odstavců nebo sekcí.

### Jak mohu zpracovat více polí TOA v jednom dokumentu?
Více polí TOA můžete spravovat přiřazením různých `EntryCategory` hodnoty a zajištění toho, aby každé pole TOA filtrovalo položky na základě své kategorie.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}