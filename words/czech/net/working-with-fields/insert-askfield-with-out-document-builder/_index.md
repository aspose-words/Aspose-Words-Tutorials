---
title: Vložit ASKField bez Tvůrce dokumentů
linktitle: Vložit ASKField bez Tvůrce dokumentů
second_title: Aspose.Words API pro zpracování dokumentů
description: Přečtěte si, jak vložit pole ASK bez použití Tvůrce dokumentů v Aspose.Words pro .NET. Chcete-li dynamicky vylepšit své dokumenty Word, postupujte podle tohoto průvodce.
weight: 10
url: /cs/net/working-with-fields/insert-askfield-with-out-document-builder/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Vložit ASKField bez Tvůrce dokumentů

## Zavedení

Chcete zvládnout automatizaci dokumentů pomocí Aspose.Words pro .NET? Jste na správném místě! Dnes vás provedeme tím, jak vložit pole ASK bez použití Tvůrce dokumentů. Toto je šikovná funkce, když chcete, aby váš dokument vyzval uživatele ke konkrétnímu vstupu, díky čemuž budou vaše dokumenty Word interaktivnější a dynamičtější. Pojďme se tedy ponořit a udělat vaše dokumenty chytřejšími!

## Předpoklady

Než si ušpiníme ruce nějakým kódem, ujistěte se, že máme vše nastaveno:

1.  Aspose.Words for .NET: Ujistěte se, že máte nainstalovanou tuto knihovnu. Pokud ne, můžete si jej stáhnout z[zde](https://releases.aspose.com/words/net/).
2. Vývojové prostředí: Vhodné IDE jako Visual Studio.
3. .NET Framework: Ujistěte se, že máte nainstalované rozhraní .NET Framework.

Velký! Nyní, když jsme vše připraveni, začněme importem potřebných jmenných prostorů.

## Importovat jmenné prostory

Nejprve musíme importovat jmenný prostor Aspose.Words, abychom získali přístup ke všem funkcím Aspose.Words pro .NET. Postup je následující:

```csharp
using Aspose.Words;
using Aspose.Words.Fields;
```

## Krok 1: Vytvořte nový dokument

Než budeme moci vložit pole ASK, potřebujeme dokument, se kterým budeme pracovat. Zde je návod, jak vytvořit nový dokument:

```csharp
// Cesta k adresáři dokumentů.
string dataDir = "YOUR DOCUMENTS DIRECTORY";

// Vytvoření dokumentu.
Document doc = new Document();
```

Tento fragment kódu nastaví nový dokument aplikace Word, kam přidáme pole ASK.

## Krok 2: Otevřete uzel odstavce

V dokumentu aplikace Word je obsah uspořádán do uzlů. Potřebujeme přístup k prvnímu bodu odstavce, kam vložíme pole ASK:

```csharp
Paragraph para = (Paragraph)doc.GetChild(NodeType.Paragraph, 0, true);
```

Tento řádek kódu načte první odstavec v dokumentu, připravený pro vložení pole ASK.

## Krok 3: Vložte pole ASK

Nyní přejdeme k hlavní události – vložení pole ASK. Toto pole vyzve uživatele k zadání při otevření dokumentu.

```csharp
// Vložte pole ASK.
FieldAsk field = (FieldAsk)para.AppendField(FieldType.FieldAsk, false);
```

Zde k odstavci připojíme pole ASK. Jednoduché, že?

## Krok 4: Nakonfigurujte pole ASK

Musíme nastavit některé vlastnosti, abychom definovali, jak se pole ASK chová. Pojďme nakonfigurovat název záložky, text výzvy, výchozí odpověď a chování hromadné korespondence:

```csharp
field.BookmarkName = "Test1";
field.PromptText = "Please enter your response:";
field.DefaultResponse = "Default response";
field.PromptOnceOnMailMerge = true;
```

- BookmarkName: Jedinečný identifikátor pro pole ASK.
- PromptText: Text, který uživatele vyzve k zadání.
- DefaultResponse: Předvyplněná odpověď, kterou může uživatel změnit.
- PromptOnceOnMailMerge: Určuje, zda se výzva během hromadné korespondence zobrazí pouze jednou.

## Krok 5: Aktualizujte pole

Po konfiguraci pole ASK jej musíme aktualizovat, abychom zajistili správnost použití všech nastavení:

```csharp
field.Update();
```

Tento příkaz zajistí, že naše pole ASK je připraveno a správně nastaveno v dokumentu.

## Krok 6: Uložte dokument

Nakonec uložíme dokument do našeho zadaného adresáře:

```csharp
doc.Save(dataDir + "InsertionChampASKSansDocumentBuilder.docx");
```

Tento řádek uloží dokument s vloženým polem ASK. A tady to máte – váš dokument je nyní vybaven dynamickým polem ASK!

## Závěr

Gratuluji! Právě jste přidali pole ASK do dokumentu aplikace Word pomocí Aspose.Words for .NET bez Tvůrce dokumentů. Tato funkce může výrazně zlepšit interakci uživatele s vašimi dokumenty, díky čemuž jsou flexibilnější a uživatelsky přívětivější. Pokračujte v experimentování s různými poli a vlastnostmi, abyste odemkli plný potenciál Aspose.Words. Šťastné kódování!

## FAQ

### Co je pole ASK v Aspose.Words?
Pole ASK v Aspose.Words je pole, které uživatele vyzve k zadání konkrétního vstupu při otevření dokumentu, což umožňuje dynamické zadávání dat.

### Mohu použít více polí ASK v jednom dokumentu?
Ano, do dokumentu můžete vložit více polí ASK, každé s jedinečnými výzvami a odpověďmi.

###  Jaký je účel`PromptOnceOnMailMerge` property?
 The`PromptOnceOnMailMerge` vlastnost určuje, zda se výzva ASK zobrazí pouze jednou během operace hromadné korespondence nebo pokaždé.

### Musím aktualizovat pole ASK po nastavení jeho vlastností?
Ano, aktualizace pole ASK zajistí, že všechny vlastnosti budou správně použity a pole bude fungovat podle očekávání.

### Mohu upravit text výzvy a výchozí odpověď?
Absolutně! Můžete nastavit vlastní text výzvy a výchozí odpovědi, abyste pole ASK přizpůsobili svým konkrétním potřebám.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
